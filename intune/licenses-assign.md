---
title: Tilldela licenser för Microsoft Intune
description: Tilldela licenser till användare så att de kan registrera sig i Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 797ea27103144423d1b43434612999631a4a243d
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834501"
---
# <a name="assign-licenses-to-users-so-they-can-enroll-devices-in-intune"></a>Tilldela licenser till användare så att de kan registrera enheter i Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Oavsett om du lägger till användare manuellt eller synkroniserar från din lokala Active Directory, så måste du först tilldela varje användare en Intune-licens innan de kan registrera sina enheter i Intune. En lista över licenser finns i [Licenser som inkluderar Intune](licenses.md).

## <a name="assign-an-intune-license-in-the-office-365-admin-center"></a>Tilldela en Intune-licens i administrationscentret för Office 365

Du kan använda [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) för att manuellt lägga till molnbaserade användare och tilldela licenser till både molnbaserade användarkonton och konton som synkroniseras från din lokala Active Directory till Azure AD.

1. Logga in på [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) med dina klientadministratörsuppgifter och välj sedan **Användare** > **Aktiva användare**.

2. Markera det användarkonto som du vill tilldela en Intune-användarlicens och välj sedan **Produktlicenser** > **Redigera**.

3. Växla **Intune** eller **Enterprise Mobility + säkerhet** till **På** och Välj **Spara**.

   ![Skärmbild av avsnittet Produktlicenser på Office 365-portalen.](./media/office-assign-license.png)

4. Användarkontot har nu de behörigheter som krävs för att använda tjänsten och registrera enheter för hantering.

> [!NOTE]
> Användarna visas i administratörskonsolen när de har registrerat en enhet. Du kan också välja en grupp användare som redigeras samtidigt, genom att välja att lägga till eller ersätta en licens för alla markerade användare.

## <a name="assign-an-intune-license-by-using-azure-active-directory"></a>Tilldela en Intune-licens genom att använda Azure Active Directory

Du kan också tilldela Intune-licenser till användare med hjälp av Azure Active Directory. Mer information finns i [artikeln Licensiera användare i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal). 

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>Använd synkronisering av skolinformation för att tilldela användare licenser till Intune for Education
Om du representerar en utbildningsorganisation kan du använda synkronisering av skolinformation (SDS) för att tilldela Intune for Education-licenser till synkroniserade användare. Markera bara kryssrutan Intune for Education när du konfigurerar din SDS-profil.  

![Skärmbild av SDS-profilinställningen](./media/i4e-sds-profile-setup-setting.png)

Kontrollera att Intune A Direct-licensen också tilldelas när du tilldelar en Intune for Education-licens.

![Skärmbild av konfiguration av produktlicens](./media/i4e-set-licenses.png)

Se den här [översikten över synkronisering av skolinformation](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91) om du vill veta mer om SDS.

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>Hur användar- och enhetslicenser påverkar åtkomsten till tjänster
* Varje **användare** som du tilldelar en programanvändarlicens kan få åtkomst till och använda onlinetjänster och relaterade program (t.ex. System Center-program) och hantera program och upp till 15 enheter.
* Du kan köpa licenser för enheter separat från användarlicenser. Enhetslicenser behöver inte tilldelas till enheterna. Varje enhet som har åtkomst till och använder onlinetjänster och relaterad programvara (som System Center-program) måste ha en enhetslicens.
* Om en enhet används av mer än en användare så krävs det en programvarulicens för var och en, eller så krävs det en programlicens för varje användare.

## <a name="understanding-the-type-of-licenses-you-have-purchased"></a>Förstå vilken typ av licenser som du har köpt

Hur du har köpt Intune avgör vilken prenumerationsinformation som visas:

- Om du har köpt Intune med ett Enterprise-avtal, hittar du din prenumerationsinformation i volymlicensportalen under **Prenumerationer**.
- Kontakta din återförsäljare om du har köpt Intune från en leverantör av molnlösningar.
- Om du har köpt Intune med en CC# eller faktura är dina licenser användarbaserade.




## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>Använda PowerShell för att hantera EMS-användarlicenser selektivt
Organisationer som använder Microsoft Enterprise Mobility + Security (tidigare Enterprise Mobility Suite) kanske har användare som bara behöver Azure Active Directory Premium eller Intune-tjänster i EMS-paketet. Du kan tilldela en tjänst eller en delmängd tjänster med hjälp av [Azure Active Directory PowerShell-cmdlets](https://msdn.microsoft.com/library/jj151815.aspx).

Om du vill tilldela användarlicenser för EMS-tjänster öppnar du PowerShell som administratör på en dator där [Azure Active Directory-modulen för Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) är installerad. Du kan installera PowerShell på en lokal dator eller på en AD FS-server.

Du måste skapa en ny definition av licens-SKU:n som bara gäller önskade tjänstplaner. Det gör du genom att inaktivera planer som du inte vill använda. Du kan till exempel skapa en definition av licens-SKU:n som inte tilldelar en Intune-licens. Om du vill visa en lista över tjänster som är tillgängliga skriver du:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

Du kan köra följande kommando om du vill undanta Intune-tjänstplanen. Du kan använda samma metod om du vill utöka till en hel säkerhetsgrupp eller använda mer detaljerade filter.

**Exempel 1**<br>
Skapa en ny användare på kommandoraden och tilldela en EMS-licens utan att aktivera Intune-delen av licensen:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Kontrollera med:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Exempel 2**<br>
Inaktivera Intune-delen av EMS-licensen för en användare som redan har tilldelats en licens:

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

Kontrollera med:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)
