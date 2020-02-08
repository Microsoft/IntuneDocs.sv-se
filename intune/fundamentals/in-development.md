---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d71ae3c15dddedd5d9ebfaf06fcae25af89f6b82
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912647"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>Under utveckling för Microsoft Intune – januari 2020

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Förutom informationen på den här sidan: 

- Om vi tror att du behöver vidta åtgärder innan en ändring genomförs, publicerar vi ett extra inlägg i meddelandecentret för Office.
- När en funktion går in i produktion, oavsett om det är en förhandsversion eller en allmänt tillgänglig version, flyttas funktionsbeskrivningen från den här sidan till [Nyheter](whats-new.md).
- Den här sidan och sidan [Nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Information om planerade produktlanseringar och tidslinjer finns i [Microsoft 365-översikten](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS).

> [!NOTE]
> Den här informationen återspeglar våra planer gällande Intune-funktioner i kommande versioner. Datum och enskilda funktioner kan ändras. Den här sidan beskriver inte alla funktioner som utvecklas.

**RSS-feed**: Få reda på när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Apphantering

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Visa meddelanden för Företagsportalappen i Windows<!-- 1808082  -->
Vi uppdaterar Företagsportalappen på Windows-enheter för att visa popup-meddelanden till användare, även när programmet är stängt. Uppdateringen visar endast meddelanden för tillgängliga appar när installationsstatusen är slutförd eller har misslyckats. Företagsportalappen visar inte meddelanden för nödvändiga program. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Visa installationsstatusmeddelanden för Företagsportalappen<!-- 2514416  -->
Företagsportalappen visar ytterligare statusmeddelanden för appinstallation för slutanvändare. Följande villkor gäller för nya Win32-beroende funktioner:
- Appen gick inte att installera. Beroenden som definierats av administratören uppfylldes inte.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>Omdirigera webbklipp till Microsoft Edge på iOS-enheter<!-- 5455276 -->
Webbklipp, som fungerar som fästa webbappar på iOS-enheter, måste uppdateras. Nyligen distribuerade webbklipp öppnas i Microsoft Edge i stället för Intune Managed Browser om det behövs för att öppna i en skyddad webbläsare. Du måste omdirigera befintliga webbklipp för att se till att de öppnas i Microsoft Edge i stället för Managed Browser. 


<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Enhetskonfigurationsprofiler för fast nätverk för macOS-enheter<!-- 3508686  -->
En ny konfigurationsprofil för macOS-enheter kommer att bli tillgänglig, som konfigurerar kabelanslutna nätverk (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattformen > **Kabelanslutet nätverk** för profiltypen). Använd den här funktionen för att skapa 802.1 x-profiler för att hantera kabelanslutna nätverk och distribuera dessa kabelanslutna nätverk till dina macOS-enheter.

Gäller för:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>VPN-profiler med IKEv2 VPN-anslutningar kan använda Alltid på med iOS-enheter <!-- 1947932 idready -->
På iOS-enheter kan du skapa en VPN-profil som använder en IKEv2-anslutning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPadOS** för plattformen > **VPN** för profiltypen). I en framtida uppdatering kan du konfigurera Alltid på med IKEv2. När IKEv2 VPN-profiler har konfigurerats ansluter de automatiskt och förblir anslutna (eller återansluter snabbt) till VPN-anslutningen. Den förblir ansluten även när du flyttar mellan nätverk eller startar om enheter.

På iOS är Alltid på för VPN begränsat till IKEv2-profiler.

Om du vill se de aktuella IKEv2-inställningarna som du kan konfigurera går du till [Lägg till VPN-inställningar på iOS-enheter i Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Gäller för:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Förbättrat användargränssnitt när du skapar konfigurationsprofiler på iOS- och macOS-enheter<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
När du skapar en profil för iOS- eller macOS-enheter uppdateras funktionen i administrationscentret för slutpunktshantering. Den här ändringen påverkar följande enhetskonfigurationsprofiler (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** > **iOS** eller **macOS** för plattformen):

- Anpassad: iOS, macOS
- Enhetsfunktioner: iOS, macOS
- Enhetsbegränsningar: iOS, macOS
- Slutpunktsskydd: macOS
- Tillägg: macOS
- Inställningsfil: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Förbättrat användargränssnitt när du skapar OEMConfig-konfigurationsprofiler på Android Enterprise-enheter<!-- 5568645 idready  -->
När du skapar eller redigerar en OEMConfig-profil för Android Enterprise-enheter uppdateras funktionen i administrationscentret för slutpunktshantering. Den uppdaterade funktionen ger en snabb översikt över inställningar som du har konfigurerat. Den här ändringen påverkar OEMConfig-profilen för enhetskonfigurationen (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** > **Android Enterprise** för plattformen > **OEMConfig** för profiltypen).

Den här funktionen gäller för:
- Android enterprise 

<!-- ***********************************************-->
<!--## Device enrollment-->



<!-- ***********************************************-->
<!--## Device management-->



<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Användargränssnittsändringar i Intune-roller kommer<!--5801612 idready-->
Användargränssnittet för [Microsoft Endpoint Manager-administrationscenter](https://go.microsoft.com/fwlink/?linkid=2109431) > **Innehavaradministratör** > **Roller** ändras till en mer användarvänlig och intuitiv design. De här funktionerna tillhandahåller samma inställningar och information som du använder nu, men de nya funktionerna använder en guideliknande process.


<!-- ***********************************************-->
## <a name="security"></a>Säkerhet

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Stöd för härledda autentiseringsuppgifter på Android COBO-enheter<!--4839592-->
Du kommer att kunna använda härledda autentiseringsuppgifter på fullständigt hanterade Android Enterprise-enheter. Support kommer att inkluderas för att hämta en härledd autentiseringsuppgift för Entrust Datacard, Intercede och DISA Purebred. Du kan använda en härledd autentiseringsuppgift för appautentisering, Wi-Fi, VPN eller S/MIME-signering och/eller kryptering med appar som stöder det. 

<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


