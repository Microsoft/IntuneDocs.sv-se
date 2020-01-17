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
ms.openlocfilehash: 01ea2f75d166e5cc6aef4b890dba5722a74c1f61
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827827"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>Under utveckling för Microsoft Intune – januari 2020

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Förutom informationen på den här sidan: 

- Om vi tror att du behöver vidta åtgärder innan en ändring genomförs, publicerar vi ett extra inlägg i meddelandecentret för Office.
- När en funktion går in i produktion, oavsett om det är en för hands version eller är allmänt tillgänglig, kommer funktions beskrivningen att flyttas från den här sidan till [vad som är nytt](whats-new.md).
- Den här sidan och sidan [Nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Information om planerade produktlanseringar och tidslinjer finns i [Microsoft 365-översikten](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS).

> [!NOTE]
> Den här sidan visar våra aktuella förväntningar om Intune-funktioner i en framtida version. Datum och enskilda funktioner kan ändras. Den här sidan beskriver inte alla funktioner som utvecklas.

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Visa meddelanden för Företagsportal-appen i Windows<!-- 1808082  -->
Vi uppdaterar Företagsportal-appen på Windows-enheter för att visa popup-meddelanden till användare, även när programmet stängs. Uppdateringen visar endast meddelanden för tillgängliga appar när installations statusen är slutförd eller inte fungerar. Företagsportal appen visar inte meddelanden för nödvändiga program. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Visa installations status meddelanden för appen Företagsportal<!-- 2514416  -->
Företagsportal-appen visar ytterligare status meddelanden för Programinstallation för slutanvändare. Följande villkor gäller för nya Win32-beroende funktioner:
- Appen gick inte att installera. Beroenden som definierats av administratören uppfylldes inte.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276-idready---"></a>Anpassa webb klipp till Microsoft Edge på iOS-enheter<!-- 5455276 idready -->
Webb klipp, som fungerar som fästa webb program på iOS-enheter, måste uppdateras. Nyligen distribuerade webb klipp öppnas i Microsoft Edge i stället för Intune Managed Browser om det behövs för att öppna i en skyddad webbläsare. Du måste rikta in dig på befintliga webb klipp för att se till att de öppnas i Microsoft Edge i stället för Managed Browser. 

### <a name="user-experience-change-when-adding-apps-to-intune---4705829-idready---"></a>Ändring av användar upplevelse vid tillägg av appar i Intune<!-- 4705829 idready -->
En ny användar upplevelse visas när du lägger till appar via Intune. Den här upplevelsen ger samma inställningar och information som du har använt tidigare, men den nya upplevelsen följer en guide-liknande process innan du lägger till en app i Intune. Den här nya upplevelsen innehåller också en gransknings sida innan appen läggs till. Välj **Appar** > **Alla appar** > **Lägg till** i [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Du hittar mer information i [Lägg till appar i Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----3136567--"></a>Kräv att Win32-appar startas om <!-- 3136567-->
Du kan kräva att en Win32-app måste startas om efter en lyckad installation. Du kan också välja hur lång tid (Grace-perioden) som ska ske innan omstarten måste ske.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Lägg till automatiska proxyinställningar i Wi-Fi-profiler för Android Enterprise Work-profiler<!-- 4490822 idready -->
På Android Enterprise Work Profile-enheter kan du skapa Wi-Fi-profiler. När du väljer företags typen Wi-Fi kan du också ange den EAP-typ (Extensible Authentication Protocol) som används i ditt Wi-Fi-nätverk.

När du väljer företags typ i en framtida uppdatering kan du ange inställningar för automatisk proxy, inklusive en proxyserver-URL, till exempel `proxy.contoso.com`.

Om du vill se de aktuella Wi-Fi-inställningar som du kan konfigurera går du till [Lägg till Wi-Fi-inställningar för enheter som kör Android Enterprise och Android i Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Gäller för:
- Android Enterprise-arbetsprofil

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Konfigurations profiler för enheter med kabelanslutna nätverk för macOS-enheter<!-- 3508686  -->
En ny macOS-enhets konfigurations profil är tillgänglig som konfigurerar kabelanslutna nätverk (**enhets konfiguration** > **profiler** > **Skapa profil** > **MacOS** för plattformen > **kabelanslutet nätverk** för profil typ). Använd den här funktionen för att skapa 802.1 x-profiler för att hantera kabelanslutna nätverk och distribuera dessa kabelanslutna nätverk till dina macOS-enheter.

Gäller för:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>VPN-profiler med IKEv2 VPN-anslutningar kan använda Always on med iOS-enheter <!-- 1947932 idready -->
På iOS-enheter kan du skapa en VPN-profil som använder en IKEv2-anslutning (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS/iPad** för Platform > **VPN** för profil typ). I en framtida uppdatering kan du konfigurera Always on med IKEv2. När IKEv2 har kon figurer ATS ansluter IKEv2 VPN-profiler automatiskt och håller på att ansluta (eller snabbt återansluta) till VPN-anslutningen. Den förblir ansluten även när du flyttar mellan nätverk eller startar om enheter.

I iOS är Always on VPN begränsat till IKEv2-profiler.

Om du vill se de aktuella IKEv2-inställningarna som du kan konfigurera går du till [Lägg till VPN-inställningar på iOS-enheter i Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Gäller för:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Förbättrad användar gränssnitts upplevelse när du skapar konfigurations profiler på iOS-och macOS-enheter<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
När du skapar en profil för iOS-eller macOS-enheter uppdateras upplevelsen i administrations centret för slut punkts hantering. Den här ändringen påverkar följande enhets konfigurations profiler (**enheter** > **konfigurations profiler** > **Skapa profil** > **iOS** eller **MacOS** för plattform):

- Anpassad: iOS, macOS
- Enhets funktioner: iOS, macOS
- Enhets begränsningar: iOS, macOS
- Slutpunktsskydd: macOS
- Tillägg: macOS
- Inställnings fil: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Förbättrad användar gränssnitts upplevelse vid skapande av konfigurations profiler för OEMConfig på Android Enterprise-enheter<!-- 5568645 idready  -->
När du skapar eller redigerar en OEMConfig-profil för Android Enterprise-enheter uppdateras upplevelsen i administrations centret för slut punkts hantering. Den uppdaterade upplevelsen ger en översikt över inställningar som du har konfigurerat på ett snabbt sätt. Den här ändringen påverkar enhetens konfigurations profil för OEMConfig (**enheter** > **konfigurations profiler** > **Skapa profil** > **Android Enterprise** for Platform > **OEMConfig** för profil typ).

Den här funktionen gäller för:
- Android enterprise 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Enhetsregistrering

### <a name="block-android-enrollments-by-device-manufacturer--5197392-idready--"></a>Blockera Android-registreringar per enhets tillverkare<!--5197392 idready-->
Du kan blockera enheter från att registreras baserat på enhetens tillverkare. Detta gäller för Android-enhetens administratör och arbets profil enheter för Android Enterprise. Om du vill se registrerings begränsningarna går du till [administrations Center för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)> **enheter** > **registrerings begränsningar**.



<!-- ***********************************************-->
## <a name="device-management"></a>Enhetshantering


### <a name="new-information-in-device-details---4471759-5604099----"></a>Ny information i enhets information<!-- 4471759 5604099  -->
Följande information kommer att läggas till på sidan **Översikt** för enheter:
- Minnes kapacitet (mängden fysiskt minne på enheten)
- Lagrings kapacitet (mängden fysiskt lagrings utrymme på enheten) 
- Processortyp och hastighet
- RAM-och processor data

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-idready--"></a>Ny säkerhets hanterare för inbyggd roll slut punkt för Intune<!--4253397 idready-->
En ny inbyggd Intune-roll är tillgänglig: slut punkts säkerhets hanteraren. Den här nya rollen ger administratörer fullständig åtkomst till Endpoint Manager-noden i Intune och endast redo att komma åt andra områden. Rollen är en utökning av rollen "säkerhets administratör" från Azure AD. Om du för närvarande bara har globala administratörer som roller behövs inga ändringar. Om du använder roller och du vill ha den granularitet som säkerhets hanteraren i Endpoint tillhandahåller, tilldelar du sedan rollen när den är tillgänglig. Mer information om inbyggda roller finns i [rollbaserad åtkomst kontroll](role-based-access-control.md).

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Användar gränssnitts ändringar i Intune-roller kommer<!--5801612 idready-->
Användar gränssnittet för administrations [Center för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **klient administration** > **roller** ändras till en mer användarvänlig och intuitiv design. Den här upplevelsen ger samma inställningar och information som du använder nu, men den nya upplevelsen använder en guide som liknar processen.


<!-- ***********************************************-->
## <a name="security"></a>Säkerhet

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Stöd för härledda autentiseringsuppgifter på Android COBO-enheter<!--4839592-->
Du kommer att kunna använda härledda autentiseringsuppgifter på fullständigt hanterade Android-enheter. Support kommer att tas med för att hämta en härledd autentiseringsuppgift för Entrust Datacard, överföra och DISA purebred. Du kan använda en härledd autentiseringsuppgift för app-autentisering, Wi-Fi, VPN eller S/MIME-signering och/eller kryptering med appar som stöder det. 

<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


