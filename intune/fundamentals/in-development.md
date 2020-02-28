---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7113552e09a7c7fa145a452e56575bfaf5297c3e
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514580"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>Under utveckling för Microsoft Intune – februari 2020

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

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Omdirigera webbklipp till Microsoft Edge på iOS/iPadOS-enheter<!-- 5455276 -->
Webbklipp, som fungerar som fästa webbappar på iOS/iPadOS-enheter, måste uppdateras. Nyligen distribuerade webbklipp öppnas i Microsoft Edge i stället för Intune Managed Browser om det behövs för att öppna i en skyddad webbläsare. Du måste omdirigera befintliga webbklipp för att se till att de öppnas i Microsoft Edge i stället för Managed Browser.

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>Förbättringar av användarupplevelsen i företagsportalen för macOS<!-- 5568987 -->
Vi håller på att förbättra registreringsupplevelsen för macOS-enheter och företagsportalappen för Mac. Du kan förvänta dig följande:
- En bättre Microsoft **AutoUpdate**-upplevelse under registreringen som ser till att användarna har den senaste versionen av företagsportalen.
- En bättre kompatibilitetskontroll under registreringen.
- Stöd för kopierade incident-ID:n så att användarna snabbare kan skicka fel från sina enheter till företagets supportteam.

Mer information om registrering och företagsportalappen för Mac finns i Registrera din macOS-enhet med hjälp av företagsportalappen (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp). 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>En skärm kommer att tas bort från registreringen av Android-arbetsprofiler i företagsportalen<!--6103987 -->
Skärmen **Vad händer nu?** kommer att tas bort från registreringsflödet för Android-arbetsprofiler i företagsportalen för att effektivisera användarupplevelsen. Gå till [Registrera med Android-arbetsprofilen]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile) om du vill se det aktuella registreringsflödet för Android-arbetsprofiler.

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>Appen Microsoft Defender Avancerat skydd (ATP) för macOS<!-- 5424518 idready -->
Intune kommer att tillhandahålla ett enkelt sätt att distribuera appen Microsoft Defender Avancerat skydd (ATP) för macOS till hanterade Mac-enheter. Mer information finns i [Microsoft Defender Avancerat skydd för Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac). 

<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Enhetskonfigurationsprofiler för fast nätverk för macOS-enheter<!-- 3508686  -->
En ny konfigurationsprofil för macOS-enheter kommer att bli tillgänglig, som konfigurerar kabelanslutna nätverk (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattformen > **Kabelanslutet nätverk** för profiltypen). Använd den här funktionen för att skapa 802.1 x-profiler för att hantera kabelanslutna nätverk och distribuera dessa kabelanslutna nätverk till dina macOS-enheter.

Gäller för:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932-idready---"></a>VPN-profiler med IKEv2 VPN-anslutningar kan använda Alltid på med iOS/iPadOS-enheter <!-- 1947932 idready -->
På iOS/iPadOS-enheter kan du skapa en VPN-profil som använder en IKEv2-anslutning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPadOS** för plattformen > **VPN** för profiltypen). I en framtida uppdatering kan du konfigurera Alltid på med IKEv2. När IKEv2 VPN-profiler har konfigurerats ansluter de automatiskt och förblir anslutna (eller återansluter snabbt) till VPN-anslutningen. Den förblir ansluten även när du flyttar mellan nätverk eller startar om enheter.

På iOS/iPadOS är Alltid på för VPN begränsat till IKEv2-profiler.

Om du vill se de aktuella IKEv2-inställningarna som du kan konfigurera går du till [Lägg till VPN-inställningar på iOS/iPadOS-enheter i Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Gäller för:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Förbättrat användargränssnitt när du skapar konfigurationsprofiler på iOS/iPadOS- och macOS-enheter<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
När du skapar en profil för iOS/iPadOS- eller macOS-enheter uppdateras funktionen i administrationscentret för slutpunktshantering. Den här ändringen påverkar följande enhetskonfigurationsprofiler (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** > **iOS** eller **macOS** för plattformen):

- Anpassad: iOS/iPadOS, macOS
- Enhetsfunktioner: iOS/iPadOS, macOS
- Enhetsbegränsningar: iOS/iPadOS, macOS
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
## <a name="device-management"></a>Enhetshantering

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Ändra primär användare för Windows-enheter <!-- 3794742 -->
Du kommer att kunna ändra den primära användaren för Windows-hybridanslutna och Azure AD-anslutna enheter. Om du vill göra det går du till **Intune** > - **Enheter** > **Alla enheter** > väljer en enhet > **Egenskaper** > **Primär användare**. 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>Serienummer på sidan för Apple MDM-pushcertifikat<!--5947765 -->
Serienumret visas på sidan för Apple MDM-pushcertifikat. Serienumret behövs för att få åtkomst till Apple MDM-pushcertifikatet om åtkomsten till det Apple-ID som skapade certifikatet skulle förloras. Om du vill visa serienumret går du till **Devices (Enheter)**  > **iOS** > **iOS enrollment (iOS-registrering)**  > **Apple MDM Push certificate (Apple MDM-pushcertifikat)** .

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>Välja vilka iOS/iPadOS-uppdateringar som ska skickas till registrerade enheter<!--5879689 -->
Du kommer att kunna välja en specifik iOS/iPadOS-uppdatering som ska skickas till enheter som har registrerats med hjälp av antingen Apple Business Manager eller Apple School Manager. För dessa enheter måste en enhetskonfigurationsprincip anges för att fördröja programuppdateringens synlighet ett antal dagar. Om du vill se den här funktionen går du till MEM > **Devices (Enheter)**  > **iOS** > **Update policies for iOS/iPadOS (Uppdateringsprinciper för iOS/iPadOS)**  > **Create profile (Skapa profil)** .

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>Nya alternativ för uppdateringsschemat för att skicka OS-uppdateringar till registrerade iOS/iPadOS-enheter<!--5879689-->
Du kommer att kunna använda följande alternativ när du schemalägger operativsystemsuppdateringar för iOS/iPadOS-enheter. Detta gäller för enheter som använde registreringstypen Apple Business Manager eller Apple School Manager.
- Uppdatera vid nästa incheckning
- Uppdatera under schemalagd tid
- Uppdatera utanför schemalagd tid

För de två sista alternativen kan du skapa flera tidsperioder.

Om du vill se de nya alternativen går du till MEM > **Devices (Enheter)**  > **iOS** > **Update policies for iOS/iPadOS (Uppdateringsprinciper för iOS/iPadOS)**  > **Create profile (Skapa profil)** .


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Övervakning och felsökning

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>Förbättrad rapporteringsupplevelse i Intune<!-- 3791418 idready -->
Intune har nu en förbättrad rapporteringsupplevelse, inklusive nya rapporttyper, bättre rapportorganisation, mer fokuserade vyer, förbättrade rapportfunktioner samt mer konsekventa och tidsrelevanta data. Rapporteringsupplevelsen kommer att flyttas från allmänt tillgänglig förhandsversion till GA (allmän tillgänglighet). Dessutom tillhandahåller GA-versionen lokaliseringsstöd, felkorrigeringar, designförbättringar och aggregerade enhetsefterlevnadsdata på paneler i [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

De nya rapporttyperna fokuserar på följande:
- **Drift** – tillhandahåller färska poster med fokus på driftproblem. 
- **Organisation** – innehåller en bred sammanfattning av det övergripande läget.
- **Historisk** – visar mönster och trender under en viss tidsperiod.
- **Specialist** – låter dig använda rådata för att skapa dina egna anpassade rapporter.

Den första uppsättningen nya rapporter fokuserar på enhetsefterlevnad. Mer information finns i [Blogg – Rapporteringsramverk i Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) och [Intune-rapporter](~/fundamentals/reports.md).



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Användargränssnittsändringar i Intune-roller kommer<!--5801612 idready-->
Användargränssnittet för [Microsoft Endpoint Manager-administrationscenter](https://go.microsoft.com/fwlink/?linkid=2109431) > **Innehavaradministratör** > **Roller** ändras till en mer användarvänlig och intuitiv design. De här funktionerna tillhandahåller samma inställningar och information som du använder nu, men de nya funktionerna använder en guideliknande process.


<!-- ***********************************************-->
## <a name="security"></a>Säkerhet

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Stöd för härledda autentiseringsuppgifter på Android COBO-enheter<!--4839592-->
Du kommer att kunna använda härledda autentiseringsuppgifter på fullständigt hanterade Android Enterprise-enheter. Support kommer att inkluderas för att hämta en härledd autentiseringsuppgift för Entrust Datacard, Intercede och DISA Purebred. Du kan använda en härledd autentiseringsuppgift för appautentisering, Wi-Fi, VPN eller S/MIME-signering och/eller kryptering med appar som stöder det.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Använda antivirusprincipen för att hantera inställningar för Microsoft Defender Antivirus och Windows-säkerhetsupplevelsen<!--6131401 -->
Från noden *Slutpunktsskydd* kommer du att kunna konfigurera inställningar för **Antivirus**. När du konfigurerar en princip för Antivirus kommer du att definiera inställningar för dina Windows 10-enheter via två profiltyper:

- Microsoft Defender Antivirus: Hantera inställningar för molnskydd, antivirusundantag, reparation, genomsökningsalternativ och mycket annat.
- Windows-säkerhetsfunktion: Hantera hur användare upplever Windows säkerhetsinställningar på sina enheter. Du kommer att kunna konfigurera vad slutanvändare kan visa i Microsoft Defender Security Center och vilka meddelanden de får. 

<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


