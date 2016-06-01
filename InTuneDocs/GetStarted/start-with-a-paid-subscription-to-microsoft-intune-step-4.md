---
# required metadata

title: Hantera Intune-licenser | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Hantera Intune-licenser
En användare måste ha en licens för din Intune-prenumeration för att kunna logga in och använda tjänsten eller registrera sina enheter för hantering. När användarna har en licens är de medlemmar i användargruppen [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)]. Den här gruppen innehåller alla användare som har licens att använda prenumerationen. Varje användarlicens stöder registrering av upp till fem enheter

## Så här tilldelas Intune-licenser
När användarkonton synkroniseras från din lokala Active Directory eller läggs till manuellt i din molntjänstprenumeration via kontoportalen så tilldelas de inte en Intune-licens automatiskt. I stället måste en Intune-klientadministratör senare redigera användarkontot och tilldela en licens till användaren från kontoportalen.

Om din prenumeration delar Azure AD med andra molntjänster som är associerade med din prenumeration har du också tillgång till användare som har lagts till i dessa tjänster. Dessa användare har ingen licens till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] förrän du tilldelar licenser till var och en av dem.

> [!TIP]
> Om alternativet för att tilldela eller återkalla en licens till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] är inaktiverat kan din prenumeration inkludera alternativ för volymlicensiering, t.ex. alternativen som är tillgängliga när du använder [Enterprise Mobility Suite](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx). Information om hur du tilldelar eller återkallar licenser finns i dokumentationen för dina licensalternativ.

## Tilldela en Intune-användarlicens

Du använder **[!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]** för att manuellt lägga till molnbaserade användare och tilldela licenser till både molnbaserade användarkonton och konton som synkroniseras från din lokala Active Directory till Azure AD.

1.  Logga in på Intune-kontoportalen med dina klientadministratörsuppgifter.

2.  Välj det användarkonto som du vill tilldela Intune-användarlicensen till och aktivera kryssrutan **Microsoft Intune** i egenskaperna för användarkontot.

3.  Nu läggs användarkontot till i Microsoft Intune-användargruppen som beviljar användaren behörighet att använda tjänsten och registrera sina enheter för hantering.

### Använda PowerShell för att hantera EMS-användarlicenser selektivt
Organisationer som använder Microsoft EMS (Enterprise Mobility Suite) kanske har användare som bara behöver Azure Active Directory Premium eller Intune-tjänster i EMS-paketet. Du kan tilldela det eller en delmängd tjänster med hjälp av [Azure Active Directory PowerShell-cmdlets](https://msdn.microsoft.com/library/jj151815.aspx) 

Om du vill tilldela användarlicenser för EMS-tjänster öppnar du PowerShell som administratör på en dator där [Azure Active Directory-modulen för Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) är installerad. Du kan installera PowerShell på en lokal dator eller på en AD FS-server.

Du måste skapa en ny definition av licens-SKU:n som bara gäller önskade tjänstplaner. Det gör du genom att inaktivera planer som du inte vill använda. Du kan till exempel skapa en definition av licens-SKU:n som inte tilldelar en Intune-licens. Om du vill visa en lista över tjänster som är tillgängliga skriver du:
 
    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus 

Du kan köra följande kommando om du vill undanta Intune-tjänstplanen. Du kan använda samma metod om du vill utöka till en hel säkerhetsgrupp eller använda mer detaljerade filter. 

Exempel 1

    Connect-MsolService 
        
    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS 
    

Skapa en ny användare på kommandoraden och tilldela en EMS-licens utan att aktivera Intune-delen av licensen:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

Kontrollera med:

    Connect-MsolService 
    
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS
 
Exempel 2
 
    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![Inaktivera Intune-delen av EMS-licensen för en användare som redan har tilldelats en licens:](./media/posh-addlic-verify.png)

### Kontrollera med:
PoSH-AddLic-Verify Nästa steg
>Grattis!

>Du är klar med steg 4 i *snabbstartsguiden för Intune*  


<!--HONumber=May16_HO2-->


