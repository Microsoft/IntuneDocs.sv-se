---
title: Registrera Windows-enheter
titlesuffix: Azure portal
description: "Aktivera hantering av mobila enheter (MDM) för Windows-enheter."
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0c4c245829a7819c9427a8ebe8ad9e166b58da97
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2017
---
# <a name="enroll-windows-devices"></a>Registrera Windows-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Det här avsnittet hjälper IT-administratörer att förenkla Windows-registrering för sina användare. När du har [konfigurerat Intune](setup-steps.md) kan användarna registrera Windows-enheter genom att [logga in](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) med sina arbets- eller skolkonton.  

I egenskap av Intune-administratör kan du förenkla registreringen på följande sätt:
- [Aktivera automatisk registrering](#enable-windows-10-automatic-enrollment) (Azure AD Premium krävs)
- [CNAME-registrering](#simplify-windows-enrollment-without-azure-ad-premium)
- [Aktivera massregistrering](windows-bulk-enroll.md) (Azure AD Premium och Windows Configuration Designer krävs)
- [Lägg till ett anpassat meddelande](windows-enrollment-status.md) som möter användarna när de registrerar sig, och så att de kan se förloppet för principinställningar som verkställs

Två saker som innebär att du kan förenkla Windows-enhetsregistreringen:

- **Använder du Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) ingår i Enterprise Mobility + Security och andra licensieringsplaner.
- **Vilka versioner av Windows-klienterna kommer användarna att registrera?** <br>Windows 10-enheter kan registreras automatiskt genom att lägga till ett arbets- eller skolkonto. Tidigare versioner måste registreras via företagsportalappen.

||**Azure AD Premium**|**Övriga AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatisk registrering](#enable-windows-10-automatic-enrollment) |[Användarregistrering](#enable-windows-enrollment-without-azure-ad-premium)|
|**Tidigare Windows-versioner**|[Användarregistrering](#enable-windows-enrollment-without-azure-ad-premium)|[Användarregistrering](#enable-windows-enrollment-without-azure-ad-premium)|

Organisationer som använder automatisk registrering kan också konfigurera [massregistrering av enheter](windows-bulk-enroll.md) med hjälp av Windows Configuration Designer-appen.

**Stöd för flera användare**<br>
Enheter som kör Windows 10 Creator-uppdateringen och är domänanslutna till Azure Active Directory, har nu stöd för fleranvändarhantering med Intune. När vanliga användare loggar in med sina autentiseringsuppgifter för Azure AD får de tillgång till de appar och principer som har tilldelats deras användarnamn. Användare kan för närvarande inte använda Företagsportalen för självbetjäningsscenarier som att installera appar.

[!INCLUDE[AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Förenkla Windows-registreringen utan Azure AD Premium
Du kan förenkla registreringen för dina användare genom att skapa ett DNS-alias (CNAME-posttyp) som automatiskt omdirigerar registreringsbegäranden till Intune-servrarna. Om du inte skapar en DNS CNAME-resurspost måste alla användare som försöker ansluta till Intune ange Intune-servernamnet under registreringen.

**Steg 1: Skapa CNAME-poster** (valfritt)<br>
Skapa CNAME-DNS-resursposter för företagsdomänen. Om ditt företags webbplats till exempel är contoso.com så skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment-s.manage.microsoft.com.

Det är valfritt att skapa CNAME DNS-poster, men det blir enklare för användarna om du gör det. Om ingen CNAME-post hittas, uppmanas användarna att manuellt ange MDM-servernamnet, enrollment.manage.microsoft.com.

|Typ|Värdnamn|Pekar på|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 timme|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

Om du har fler än ett UPN-suffix måste du skapa en CNAME-post för varje domännamn och leda var och en till EnterpriseEnrollment-s.manage.microsoft.com. Om användare på Contoso använder name@contoso.com, men även använder name@us.contoso.com och name@eu.constoso.com som e-post/UPN måste Contosos DNS-administratör skapa följande CNAME-poster:

|Typ|Värdnamn|Pekar på|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 timme|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 timme|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 timme|

`EnterpriseEnrollment-s.manage.microsoft.com` – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postens domännamn

Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

**Steg 2: Verifiera CNAME** (valfritt)<br>
På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. Välj **Registrera enheter** > **Windows-registrering** på Intune-bladet. Ange webbadressen till företagswebbplatsen i rutan **Ange ett verifierat domännamn** och välj sedan **Testa automatisk identifiering**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Berätta för användare hur de ska registrera Windows-enheter
Berätta för användarna hur de ska registrera sina Windows-enheter och vad de kan förvänta sig när de har registrerat sig för hantering.

> [!NOTE]
> Slutanvändare måste ansluta till webbplatsen för företagsportalen via Microsoft Edge för att se Windows-appar som du tilldelat för specifika Windows-versioner. Andra webbläsare, inklusive Google Chrome, Mozilla Firefox och Internet Explorer har inte stöd för den här typen av filtrering.

Registreringsinstruktioner för slutanvändare finns i [Registrera din Windows-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Du kan även be användarna granska [vad IT-administratören kan se på enheten](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Mer information om slutanvändarnas aktiviteter finns i [Resurser om slutanvändarens upplevelse med Microsoft Intune](end-user-educate.md).

## <a name="next-steps"></a>Nästa steg

- [Tänk på detta när du hanterar Windows-enheter med Intune i Azure](/intune-classic/deploy-use/intune-on-azure.md).
