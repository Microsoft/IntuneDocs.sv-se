---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4bd5392abba3ea22127cb9bcbbb53ec4929f2d5e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166351"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>Under utveckling för Microsoft Intune – September 2019

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Dessutom:

- Om vi tror att du behöver vidta åtgärder innan en ändring genomförs, publicerar vi ett extra inlägg i meddelandecentret för Office.
- När en funktion distribueras i produktionsmiljön, antingen som en förhandsversion eller som en allmänt tillgänglig version, flyttas funktionsbeskrivningen från den här sida till [sidan Nyheter](whats-new.md).
- Den här sidan och [sidan Nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Information om planerade produktlanseringar och tidslinjer finns i [M365-översikten](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS).

> [!Note]
> Den här informationen återspeglar Microsofts planer gällande Intune-funktioner i kommande versioner. Datum och enskilda funktioner kan ändras. Alla komponenter som är under utveckling har inte en funktionsbeskrivning på den här sidan.

**RSS-feed**: Håll dig informerad när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Apphantering

### <a name="managed-google-play-private-lob-apps----1464182----"></a>Hanterade Google Play-privata LOB-appar <!-- 1464182  -->
Intune gör det möjligt för IT-administratörer att publicera privata Android LOB-appar till hanterad Google Play via en iframe som är inbäddad i Intune-konsolen.  IT-administratörer måste för närvarande publicera LOB-appar direkt till Googles Play-publicerings konsol, som kräver många steg och som är mycket tids krävande.  Den här nya funktionen möjliggör enkel publicering av LOB-appar med en minimal uppsättning steg utan att du behöver lämna Intune-konsolen.  Alla scenarier för hantering av Android-företag som använder hanterad Google Play kan dra nytta av den här funktionen (arbets profil, dedikerade, fullständigt hanterade och icke-registrerade enheter).  I Intune väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **hanterad Google Play** från listan **typ av app** . Mer information om hanterade Google Play-appar finns i [lägga till hanterade Google Play-appar i Android Enterprise-enheter med Intune](apps-add-android-for-work.md).

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Företagsportal program installations status meddelanden <!-- 2514416  -->
Företagsportal-appen visar ytterligare status meddelanden för Programinstallation för slutanvändare. Följande villkor gäller för nya Win32-beroende funktioner:
- Appen gick inte att installera. Beroenden som definierats av administratören uppfylldes inte.
- Appen har installerats men kräver en omstart.
- Appen håller på att installeras, men kräver en omstart för att fortsätta.

### <a name="managed-google-play-iframe-support----2871756----"></a>Stöd för hanterad Google Play-iframe <!-- 2871756  -->
Intune tillhandahåller stöd för att lägga till och hantera webb länkar direkt i Intune-konsolen via den hanterade Google Play-iframe.  Detta gör det möjligt för IT-administratörer att skicka en URL och ikon och sedan distribuera länkarna till enheter precis som vanliga Android-appar. Alla scenarier för hantering av Android-företag som använder hanterad Google Play kan dra nytta av den här funktionen (arbets profil, dedikerade, fullständigt hanterade och icke-registrerade enheter).  I Intune väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **hanterad Google Play** från listan **typ av app** . Mer information om hanterade Google Play-appar finns i [lägga till hanterade Google Play-appar i Android Enterprise-enheter med Intune](apps-add-android-for-work.md).

### <a name="macos-support-for-vpp-apps----3173501----"></a>macOS-stöd för VPP-appar <!-- 3173501  -->
macOS-appar som du har köpt med hjälp av Apple Business Manager visas i-konsolen när Apple VPP-token synkroniseras i Intune. Du kan tilldela, återkalla och omtilldela enhets-och användarbaserade licenser för grupper med hjälp av-konsolen. Microsoft Intune hjälper dig att hantera VPP-appar som köpts för användning i företaget av:
- Rapportera licensinformation från App Store.
- Spåra antalet använda licenser.
- Hjälpa dig att inte installera fler exemplar av en app än du äger.
Mer information om Intune och VPP, finns i [Hantera volyminköpta appar och böcker med Microsoft Intune](vpp-apps.md).

### <a name="macos-support-for-web-apps----3174427----"></a>macOS-stöd för webbappar <!-- 3174427  -->
Du kommer att kunna installera webbappar, som gör att du kan lägga till en genväg till en webb adress på webben, till dockan med hjälp av macOS-Företagsportal. Slutanvändare kan komma åt **installations** åtgärden från sidan information om appar för en webbapp i macOS-företagsportal. Mer information om typen **webbapp** finns i [lägga till appar i Microsoft Intune](apps-add.md).

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Tilldela Microsoft Edge beta för macOS <!-- 4678761  -->
Du kan lägga till och tilldela den senaste versionen av Microsoft Edge beta till Intune för macOS-enheter. Från Intune väljer du**appar** > för **klient program** > **Lägg till app** > **Microsoft Edge – MacOS**. Tilldela sedan Microsoft Edge beta till de avsedda grupperna. Microsoft AutoUpdate (MAU) håller Microsoft Edge uppdaterat. Mer information om Microsoft Edge finns i [Hantera webb åtkomst med hjälp av Microsoft Edge med Microsoft Intune](manage-microsoft-edge.md).

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Läs-och skriv Graph API åtgärder för Intune-appar <!-- 5031704  -->
Program kan anropa Intune-Graph API med både Läs-och skriv åtgärder med hjälp av app-identitet utan användarautentiseringsuppgifter. Mer information om hur du kommer åt Microsoft Graph API för Intune finns i [Arbeta med Intune i Microsoft Graph.](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurera program meddelande innehåll för organisations konton <!-- 2576686 -->
Med Intune App Protection-principer (APP) på Android-och iOS-enheter kan du styra appens meddelande innehåll för org-konton. Den här funktionen kommer att kräva stöd från program och är kanske inte tillgänglig för alla APP-aktiverade program. Mer information om APP finns i [Vad är appskyddsprinciper?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Tillgänglig Google Play-apprapportering för Android-arbetsprofiler <!-- 3041956  -->
Om du vill se tillgängliga appinstallationer på Androids arbetsprofilenheter, kan du visa appens installationsstatus samt den installerade versionen av hanterade Google Play-appar. Mer information finns i [Så här övervakar du appskyddsprinciper](app-protection-policies-monitor.md), [Hantera Android-arbetsprofilenheter med Intune](android-enterprise-overview.md) och [Hanterade Google Play-apptyper](apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>Enhets funktioner, enhets begränsningar och tilläggs profiler för iOS-och macOS-inställningar visas av registrerings typ <!-- 4886161  -->

I Intune skapar du profiler för iOS-och MacOS-enheter (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS** eller **MacOS** för plattform > **enhets funktioner** , **Enhets begränsningar**eller **tillägg** för profil typ). För närvarande visas de tillgängliga inställningarna i de här profilerna. 

I en framtida uppdatering kommer de tillgängliga inställningarna i Intune-portalen att kategoriseras av den registrerings typ som de gäller för:

- iOS
  - Alla registrerings typer
  - Enhets registrering och automatisk enhets registrering
  - Automatisk enhets registrering

- macOS
  - Alla registrerings typer
  - Enhetsregistrering
  - Användare godkänd och automatisk enhets registrering
  - Automatisk enhets registrering

Gäller för:

- iOS
  - [Enhetsfunktioner](ios-device-features-settings.md)
  - [Enhetsbegränsningar](device-restrictions-ios.md)

- macOS
  - [Enhetsfunktioner](macos-device-features-settings.md)
  - [Enhetsbegränsningar](device-restrictions-macos.md)
  - [Tillägg](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>Nya inställningar för röst kontroll för övervakade iOS-enheter som körs i hel skärms läge <!-- 4892835  -->

I Intune kan du skapa principer för att köra övervakade iOS-enheter som en kiosk eller dedikerad enhet (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS** för plattform >  **Enhets begränsningar** för profil typ > **kiosk (endast övervakat)** ). 

I en framtida uppdatering kommer det att finnas nya inställningar som du kan styra:

- **Röst kontroll**: aktiverar röst kontroll på enheten i hel skärms läge.
- **Ändring av röst kontroll**: Tillåt att användare ändrar inställningen röst kontroll på enheten i hel skärms läge.

Om du vill se de aktuella inställningarna går du till [iOS kiosk (endast övervakat) inställningar](device-restrictions-ios.md#kiosk).

Gäller för:

- iOS 13.0 och senare

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>Använd enkel inloggning för appar och webbplatser på dina iOS-och macOS-enheter <!-- 4893175  -->
I en framtida uppdatering kommer det att finnas några nya inställningar för enkel inloggning för iOS-och MacOS-enheter **(enhets konfigurations** > **profiler** > **Skapa profil** > **iOS** eller **MacOS** för plattforms > **enhets funktioner** för profil typ).

Använd de här inställningarna om du vill konfigurera en enkel inloggnings upplevelse, särskilt för appar och webbplatser som använder Kerberos-autentisering. Du kan välja mellan ett allmänt autentiserings tillägg för enkel inloggning och Apples inbyggda Kerberos-tillägg.

Om du vill se de aktuella enhets funktioner som du kan konfigurera går du till [iOS-enhetens funktioner](ios-device-features-settings.md) och [MacOS-enhets funktioner](macos-device-features-settings.md).

Gäller för:

- iOS 13.0 och senare
- macOS 10.15 och senare

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>Associera domäner till appar på macOS 10.15 + enheter <!-- 4898079  -->
På MacOS-enheter kan du konfigurera olika funktioner och skicka dessa funktioner till dina enheter med en princip (**enhets konfiguration** > **profiler** > **Skapa profil** > **MacOS** för plattforms > **enhets funktioner** för profil typ). I en framtida uppdatering kan du koppla domäner till dina appar. Den här funktionen hjälper till att dela autentiseringsuppgifter med webbplatser som är relaterade till din app och kan användas med Apples tillägg för enkel inloggning, Universal Links och Autofyll. 

Om du vill se de aktuella funktioner som du kan konfigurera går du till [Inställningar för MacOS-enhetens funktioner i Intune](macos-device-features-settings.md).

Gäller för:

- macOS 10.15 och senare

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>Använd "iTunes" och "Apps" i URL: en för iTunes App Store när du visar eller döljer appar på iOS-övervakade enheter <!-- 4928474  --> 
I Intune kan du skapa principer för att visa eller dölja appar på dina övervakade iOS-enheter (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS** för plattform > **enhet begränsningar** för profil typ > **Visa eller Dölj appar (endast övervakat)** ). 

Du kan ange URL: en för iTunes App Store, `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`till exempel. I en framtida uppdatering kan du använda både `apps` och `itunes` i URL: en, till exempel:

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Mer information om de här inställningarna finns i [Visa eller Dölj appar](device-restrictions-ios.md#show-or-hide-apps).

Gäller för:

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Stöd för IKEv2 VPN-profiler för iOS <!-- 1943438 -->
Du kommer att kunna skapa VPN-profiler för den iOS-inbyggda VPN-klienten med hjälp av IKEv2-protokoll. IKEv2 är en ny anslutningstyp i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **VPN** för profiltyp > **Inställningar**.

De här VPN-profilerna konfigurerar den inbyggda VPN-klienten. Därför installeras eller skickas inga VPN-klientappar till hanterade enheter. Den här funktionen kräver att enheter registreras i Intune (MDM-registrering).

Om du vill se de aktuella VPN-inställningarna som du kan konfigurera går du till [Konfigurera VPN-inställningar på iOS-enheter i Microsoft Intune](vpn-settings-ios.md).

Gäller för: iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>Enhetsregistrering

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>Nya klienter kommer som standard bort från Android-enhetens administratörs hantering <!-- 4869790  -->
Android: s enhets administratörs funktioner har ersatts av Android Enterprise. Därför rekommenderar vi att du använder Android Enterprise för nya registreringar i stället. I en framtida uppdatering måste nya klienter utföra följande nödvändiga steg i Android-registreringen för **att kunna använda** > enhets administratörs hantering: gå till**enhets registrering** > **Android-registrering** Personliga och >  **företagsägda enheter med behörighet för enhets administration** **Använd enhets administratören för att hantera enheter.**  > 

Befintliga klienter får ingen ändring i sina miljöer. 

Mer information om Android-enhetens administratör i Intune finns i [registrering av Android-enhetens administratör](android-enroll-device-administrator.md).

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>För iOS-enheter anpassar du registrerings processens sekretess sida på Företagsportal <!-- 4394993  -->
Med hjälp av markdown kan du anpassa Företagsportalens sekretess skärm som slutanvändarna ser under iOS-registreringen. Mer specifikt kan du anpassa listan över saker som din organisation inte kan se eller göra på enheten.

<!-- ***********************************************-->
## <a name="device-management"></a>Enhetshantering

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Distribuera program uppdateringar till macOS-enheter <!-- 3194876 -->
Du kan distribuera program uppdateringar till grupper av macOS-enheter. Den här funktionen inkluderar kritisk, inbyggd program vara, konfigurations fil och andra uppdateringar. Du kommer att kunna skicka uppdateringar på nästa enhet checka in eller välja ett vecko schema för att distribuera uppdateringar i eller från tidsfönster som du har angett. Detta hjälper dig när du vill uppdatera enheter utanför standard arbets tiden eller när supportavdelningen är helt bemannad. Du får också en detaljerad rapport om alla macOS-enheter med distribuerade uppdateringar. Du kan öka detalj nivån för rapporten per enhet för att se status för särskilda uppdateringar.

### <a name="send-custom-notifications-to-a-device----4928910----"></a>Skicka anpassade meddelanden till en enhet <!-- 4928910  -->
Du kan skicka anpassade meddelanden till vissa enheter som har Företagsportal-eller Intune-appen installerad. Det gör du genom att gå **till Intune** > -**enheter** > **alla enheter** > välja en enhet > **mer** > **Skicka anpassat meddelande**. 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Uppdateringar av fullständigt hanterade funktioner i Android Enterprise <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

Vi lägger till följande stöd för fullständigt hanterade Android-enheter:

- SCEP-certifikat för fullständigt hanterad Android är tillgängligt för cert-autentisering på enheter som hanteras som enhets ägare. SCEP-certifikat stöds redan på arbets profil enheter.  Med SCEP-certifikat för enhets ägare kommer du att kunna: <!-- 5227935 -->
    - Skapa SCEP-profil under göra-avsnittet i Android Enterprise
    - länka SCEP-certifikat till Wi-Fi-profil för autentisering
    - länka SCEP-certifikat till VPN-profiler för autentisering
    - länka SCEP-certifikat till e-postprofiler för autentisering (via app-konfiguration)
- Systemappar kommer att stödjas på Android Enterprise-enheter. I Intune ska du lägga till en Android Enterprise-systemappen genom att välja**appar** > för **klient program** > **Lägg till**. Välj **Android Enterprise system app**i listan **typ av app** . Mer information om hur du lägger till appar i Intune finns i [Lägga till appar i Microsoft Intune](apps-add.md). <!-- 4062195 -->
- I **enhetens kompatibilitet** > **Android Enterprise** > **Device Owner**kan du skapa en efterlevnadsprincip som anger nivån för Google SafetyNET-attestering.   <!-- 4631425 -->
- I fullständigt hanterade Android-enheter kommer leverantörer av skydd mot mobila hot att stödjas. I **enhetens kompatibilitet** > **Android Enterprise** > **Device Owner**kan du välja en acceptabel hotnivå. <!-- 4631440 --> [Android Enterprise-inställningar för att markera enheter som kompatibla eller icke-kompatibla med Intune](compliance-policy-create-android-for-work.md#device-owner) listar de aktuella inställningarna.


Gäller för: 
- Fullständigt hanterade Android Enterprise-enheter

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

### <a name="updated-support-experience-------5012398------"></a>Uppdaterad support upplevelse   <!--  5012398    -->
Som en del av fortsatta förbättringar kommer vi att uppdatera support upplevelsen i konsolen för Intune.  Vi kommer att förbättra sökningen och feedbacken i konsolen för vanliga problem och effektivisera arbets flödet för att kontakta supporten.     

<!-- ***********************************************-->
## <a name="security"></a>Säkerhet

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Manipulering av skydd för Windows Defender Antivirus  <!-- 4705448       -->
Vi kommer att lägga till *manipulations skydd* i de inställningar som Intune kan hantera för Windows Defender Antivirus. Du kan använda en enhets konfigurations profil för Windows 10 Endpoint Protection för att aktivera eller inaktivera skydd mot manipulering.  Mer information om skydd mot manipulering finns i [förhindra säkerhets inställnings ändringar med Manipulerings skydd](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) i Windows-dokumentationen. 


<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).




