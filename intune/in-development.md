---
title: Under utveckling - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c377a8558b1f318b4ddad735b6368a291e34516
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756827"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>Under utveckling för Microsoft Intune – mars 2019

För att hjälpa din beredskap och planering, den här sidan visar Intune UI-uppdateringar och funktioner som är under utveckling, men ännu inte släppts. Dessutom:

- Om vi tror att du måste vidta åtgärder innan en ändring, publicerar vi ett kostnadsfri meddelandecenter för Office-inlägg.
- När en funktion har startats i produktion, antingen som en förhandsversion eller allmänt tillgänglig, funktionsbeskrivningen och kommer att flyttas ut den här sidan till den [nyheter](whats-new.md).
- Den här sidan och [nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Referera till den [M365-översikt](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) för strategiska mål och tidslinjer.

> [!Note]
> Dessa objekt visas Microsofts aktuella förväntningar om Intune-funktioner som kommer i en framtida version. Datum och enskilda funktioner kan ändras. Inte alla objekt i utveckling har en funktionsbeskrivning på den här sidan.

**RSS-feed**: Håll dig informerad när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal


<!-- 1903 start-->

### <a name="encryption-report-----2351538---"></a>Kryptering rapport  <!-- 2351538 -->
Du kommer att kunna använda en ny rapport för kryptering för att visa information om krypteringsstatus för dina enheter. Tillgänglig information innehåller en enheter TPM-version, kryptering beredskap och status, felrapportering och mer.  

### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-----2351547----"></a>Åtkomstnycklar på BitLocker-återställning från Intune-portalen  <!-- 2351547  -->
Vi lägger till en ny startpunkt i enheter, där du kan visa information från Azure Active Directory (AAD) om BitLocker-nyckel-ID och BitLocker återställningsnycklar.

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>Omfångstaggar för appkonfigurationsprinciper <!--2371891 -->
Du kommer att kunna lägga till en omfångstagg till en appkonfigurationsprincip så att endast personer med roller som även är tilldelade den omfångstaggen har tillgång till appkonfigurationsprincipen. Appkonfigurationsprincipen kan endast avsedda för eller som är associerade med appar som har tilldelats samma omfattningstaggen.

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Tilldela Autopilot-profiler till den virtuella gruppen Alla enheter <!--2715522 -->
Du kommer att kunna tilldela Autopilot-profiler till den virtuella gruppen Alla enheter. Om du vill göra det väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > välj en profil >  **Tilldelningar** > under **Tilldela till** väljer du **Alla enheter**. Mer information om Autopilot-profiler finns i [Registrera Windows-enheter med hjälp av Windows Autopilot](enrollment-autopilot.md).

### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523----"></a>Installera tillgängliga appar med hjälp av företagsportalappen när massregistrering för Windows <!-- 2751523  -->
Windows-enheter som registrerats i Intune med [massregistrering för Windows](windows-bulk-enroll.md) (konfigurationspaket) kommer att kunna använda appen företagsportal för att installera tillgängliga appar. Läs mer om företagsportalappen, [manuellt lägga till Windows 10-Företagsportalen](store-apps-company-portal-app.md) och [så här konfigurerar du Microsoft Intune-företagsportalappen](company-portal-app.md).

### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430---"></a>Omfångstaggar för iOS-appetableringsprofiler <!--2934430 -->
Du kommer att kunna lägga till en omfångstagg en etableringsprofil för iOS-app så att endast personer med roller som även är tilldelade den omfångstaggen har tillgång till etableringsprofilen för iOS-appen. 

### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477----"></a>Office distribution Tool (ODT) XML för distribution av Office ProPlus <!-- 3192477  -->
Du kommer att kunna tillhandahålla Office distribution Tool (ODT) XML när du skapar en instans av Office Pro Plus i Intune-administratörskonsolen. Detta gör att större anpassningsbarhet om de befintliga Intune UI-alternativen inte uppfyller dina behov. 

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>Blockera användare från söker efter uppdateringar för Windows    <!-- 3316758    -->
Vi lägger till en ny Windows uppdateringsring inställning som du kan använda som blockerar användare från söker efter uppdateringar för Windows. Den här inställningen vara inte tillgänglig i portalen, men kan konfigureras med hjälp av Intune Graph API.

### <a name="windows-update-notifications-----3316782---"></a>Meddelanden om uppdateringar för Windows  <!-- 3316782 -->
Vi lägger till stöd för Windows Update ring konfigurationer så att du kan konfigurera Windows Update-meddelanden som användarna ser. Den här inställningen vara inte tillgänglig i portalen, men kan konfigureras med hjälp av Intune Graph API.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Ändringar i Företagsportalen registrering för iOS 12 enhetens användare <!--3448635 -->  
Företagsportalen för iOS kommer att uppdatera appskärmar registrering och stegen för att anpassas till MDM-registrering ändringar som introducerades i Apple iOS 12.2. Uppdaterade arbetsflödet kommer nu att uppmana användarna att:

- Tillåt Safari att öppna webbplatsen för Företagsportalen (via Safari) och ladda ned hanteringsprofilen innan det returneras till appen företagsportal. 
- Öppna inställningsappen för att installera hanteringsprofilen på sin enhet.
- Gå tillbaka till företagsportalappen att slutföra en registrering.  

Mer information om hur du kan förbereda för dessa ändringar finns i den [Microsoft Tech Community-post](https://techcommunity.microsoft.com/). Under tiden för att stödja nya iOS-registreringar i Företagsportalen, vi har uppdaterat stegen i [registrera iOS-enhet i Intune](https://docs.microsoft.com/en-us/intune/ios-enroll). Ändringarna docs är live när Apple släpper iOS version 12.2. 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>Stöd för ytterligare anslutningar på sidan Status för klient <!-- 3617202     -->
Status för klient-sidan visar statusinformation för ytterligare anslutningar, inklusive *Windows Defender Avancerat skydd* (ATP) och andra Mobile Threat Defense-anslutningsprogram.

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>Bevilja Intune skrivskyddad åtkomst till vissa Azure Active Directory-roller <!-- 3637917 -->
Vi kommer att bevilja Intune skrivskyddad åtkomst till följande Azure AD-roller. Behörigheter som beviljas med Azure AD-roller ersätter behörigheter som beviljas med Intune rollbaserad åtkomstkontroll (RBAC).

Skrivskyddad åtkomst till Intune-granskningsdata:

- Efterlevnadsadministratör
- Efterlevnadsadministratör för Data

Skrivskyddad åtkomst till alla Intune-data:

- Säkerhetsadministratör
- Säkerhetsansvarig
- Säkerhetsläsare
- Global läsare

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>Enklare åtkomst till diagnostikinställningar   <!-- 3804627   -->
Vi lägger till en ny möjlighet att den **granskningsloggar** -bladet i varje i varje granskningsloggen arbetsbelastning i Intune-konsolen som du kan använda för att öppna direkt i *diagnostikinställningar* sidan.

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>Skapa och använda profiler för enhetskonfiguration på Android Zebra enheter i Intune <!-- 3895244  -->
Intune stöder konfiguration Zebra Android-enheter. Mer specifikt kommer du att kunna: 

- Skapa en profil för enhetskonfiguration och Använd inställningar för Android Zebra enheter med hjälp av Mobility tillägg (MX)-profiler som genererats av StageNow (**enhetskonfiguration** > **profiler**  >  **Skapa profil** > **Android** för plattform).

Gäller för:  
- Android

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Distribution av online-licensierade Microsoft Store för företag-appar <!-- 1672660  -->
Du kommer att kunna tilldela nödvändiga online-licensierade Microsoft Store för företag-appar i kontexten för enheten. Genom att distribuera en Microsoft Store för företag-app på detta sätt, kan appen installeras för alla användare på enheten. Detta gäller endast för Windows 10 RS4+ desktop-enheter. Alternativet att installera i kontexten för enheten finns på sidan Tilldelning av klientappar för MSFB Online-licensierade appar.

## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).
