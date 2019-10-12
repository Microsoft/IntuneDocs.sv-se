---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7c4e5ed45455dda941fb0c61c989c12c57135d
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999318"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Under utveckling för Microsoft Intune – oktober 2019

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

### <a name="additional-app-configuration-variable-available----4969237----"></a>Ytterligare variabel för app-konfiguration är tillgänglig <!-- 4969237  -->
När du skapar en konfigurations princip för appar kan du inkludera konfigurations variabeln `AAD Device ID` som en del av dina konfigurations inställningar. Gå till Intune och välj **Klientappar** > **Appkonfigurationsprinciper** > **Lägg till**. Ange konfigurations princip informationen och välj **konfigurations inställningar** för att Visa bladet **konfigurations inställningar** .

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>Mörkt läge för iOS Företagsportal <!-- 4911422  -->
Mörkt läge är planerat för iOS-Företagsportal. Hämta företags program, hantera enheter och få IT-support i valfritt färg schema. Mer information om hur du IOS-företagsportalen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](../apps/company-portal-app.md).

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Förhindra installation av appar från okända källor på Android Enterprise-enheter <!-- 4760025  -->
För en Android Enterprise-arbetsprofils enhet är det aldrig möjligt för slutanvändare att installera appar från okända källor i arbets profilen. Du kan också utöka den här begränsningen till den personliga profilen. Om du aktiverar den här begränsningen kommer slutanvändare på arbets profil enheter för Android även att förhindras från inläsning av appar från okända källor till den personliga delen av enheten. 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>Uppdatera till app Protection-gränssnittet och etablerings gränssnittet för iOS-appen <!-- 4102027, 4102029  -->
Användar gränssnittet för att skapa och redigera skydds principer för appar och etablerings profiler för iOS-appar i Intune kommer att uppdateras. Gränssnittsändringarna omfattar:
- En förenklad upplevelse genom att använda ett format format med en guide som är komprimerat på ett blad. 
- En uppdatering av Create-flödet för att inkludera tilldelningar.
- En sammanfattnings sida för alla saker som anges när du visar egenskaper, innan du skapar en ny princip eller när du redigerar en egenskap. När du redigerar egenskaper visas dessutom bara en lista med objekt från kategorin med egenskaper som redige ras i sammanfattningen.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Skapa grupper av hanterings objekt som kallas princip uppsättningar <!-- 3762880  -->
Med princip uppsättningar kan du skapa ett paket med referenser till redan befintliga hanterings enheter som behöver identifieras, riktas och övervakas som en enda konceptuell enhet. Princip uppsättningar ersätter inte befintliga begrepp eller objekt. En administratör kan fortsätta att tilldela enskilda objekt som de gör i dag. Enskilda objekt refereras till av en princip uppsättning. Det innebär att alla ändringar av de enskilda objekten avspeglas i princip uppsättningen.  I Intune väljer du **princip uppsättningar** > **skapa** för att skapa en ny princip uppsättning. 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Win32-appar på Windows 10 S-läge enheter <!-- 3747604  --> 
Du kommer att kunna installera och köra Win32-appar på Windows 10 S-läge-hanterade enheter. Du kan skapa en eller flera kompletterande principer för S-läge med hjälp av PowerShell-verktygen för Windows Defender-WDAC (program kontroll). Signera tilläggs principerna med Device Guard-signing Portal och ladda sedan upp och distribuera principerna via Intune. I Intune hittar du den här funktionen genom att välja **klient program** > **Windows 10 S kompletterande principer**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Ange appens tillgänglighet baserat på datum och tid <!-- 3510685  -->
Som administratör kan du konfigurera start tid och tids gräns tid för en obligatorisk app. Vid start tillfället startar Intune Management-tillägget appens innehåll hämtas och cachelagrar det. Appen kommer att installeras vid tids gränsen. För tillgängliga appar kommer start tiden att diktera när appen visas i Företagsportal. I Intune väljer du **Klientappar** > **Appar**. Välj sedan en annan app i listan eller Välj **Lägg** till för att lägga till en ny app. Från bladet app väljer du **tilldelningar** > **Lägg till grupp**. Ange **tilldelnings typen** till **obligatorisk** och välj sedan **inkluderade grupper**. Ange **gör att den här appen krävs för att alla användare** ska **Ja** och välj **Redigera** för att ändra alternativ för **slutanvändare** . På bladet **slut användar upplevelse** anger du den **tillgängliga tiden för program vara** efter behov. Mer information om hur du lägger till appar finns i [Lägga till appar i Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Kräv att Win32-appar startas om <!-- 3136567  -->
Du kan kräva att en Win32-app måste startas om efter en lyckad installation. Du kan också välja tids period (respitperioden) innan omstarten måste ske.

### <a name="company-portal-app-on-windows----1808082----"></a>Företagsportal app i Windows <!-- 1808082  -->
Företagsportal-appen på Windows-enheter kommer att uppdateras för att visa popup-meddelanden till användare, även när programmet stängs. Uppdateringen visar endast meddelanden för tillgängliga appar när installations statusen är slutförd eller misslyckades. Företagsportal appen visar inte meddelanden för nödvändiga program.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Företagsportal program installations status meddelanden <!-- 2514416  -->
Företagsportal-appen visar ytterligare status meddelanden för Programinstallation för slutanvändare. Följande villkor gäller för nya Win32-beroende funktioner:
- Appen gick inte att installera. Beroenden som definierats av administratören uppfylldes inte.
- Appen har installerats men kräver en omstart.
- Appen håller på att installeras, men kräver en omstart för att fortsätta.

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Tilldela Microsoft Edge beta för macOS <!-- 4678761  -->
Du kan lägga till och tilldela den senaste versionen av Microsoft Edge beta till Intune för macOS-enheter. Från Intune väljer du **klient program** > **appar** > **Lägg till app** > **Microsoft Edge – MacOS**. Tilldela sedan Microsoft Edge beta till de avsedda grupperna. Microsoft AutoUpdate (MAU) håller Microsoft Edge uppdaterat. Mer information om Microsoft Edge finns i [Hantera webb åtkomst med hjälp av Microsoft Edge med Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurera program meddelande innehåll för organisations konton <!-- 2576686 -->
Med Intune App Protection-principer (APP) på Android-och iOS-enheter kan du styra appens meddelande innehåll för org-konton. Den här funktionen kommer att kräva stöd från program och är kanske inte tillgänglig för alla APP-aktiverade program. Mer information om APP finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Tillgänglig Google Play-apprapportering för Android-arbetsprofiler <!-- 3041956  -->
Om du vill se tillgängliga appinstallationer på Androids arbetsprofilenheter, kan du visa appens installationsstatus samt den installerade versionen av hanterade Google Play-appar. Mer information finns i [Så här övervakar du appskyddsprinciper](../apps/app-protection-policies-monitor.md), [Hantera Android-arbetsprofilenheter med Intune](../enrollment/android-enterprise-overview.md) och [Hanterade Google Play-apptyper](../apps/apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>Nya enhets konfigurations inställningar för övervakade iOS-och iPad-enheter <!-- 5199328  -->
På iOS-och iPad-enheter kan du skapa en profil för att begränsa funktioner och inställningar på enheter (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS/iPad** för plattforms > **enhet begränsningar** för profil typ). Det kommer att finnas nya inställningar som du kan styra: 
- Åtkomst till nätverks enheten i filer-appen  
- Åtkomst till USB-enhet i filer-appen 
- Wi-Fi är alltid aktiverat 

Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md) för att se de aktuella inställningarna.

Gäller för:
- iOS 13.0 och senare
- iPadOS 13.0 och senare

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>Inställningen Anslut automatiskt tas bort i Wi-Fi-profiler på Android och Android Enterprise <!-- 5021055  -->
På Android-och Android Enterprise-enheter kan du skapa en Wi-Fi-profil för att konfigurera olika inställningar (**enhets konfiguration** > **profiler** > **Skapa profil** > **Android** eller **Android Enterprise** för plattforms > **Wi-Fi** för profil typ). Inställningen **Anslut automatiskt** tas bort eftersom den [inte stöds av Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Om du använder den här inställningen i en Wi-Fi-profil kanske du märker att **Anslut automatiskt** inte fungerar. Du behöver inte vidta några åtgärder, men tänk på att den här inställningen tas bort i användar gränssnittet i Intune.

Om du vill se de aktuella inställningarna går du till inställningar för [Android Wi-Fi](../configuration/wi-fi-settings-android.md) eller [Android Enterprise Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md).

Gäller för:
- Android
- Android enterprise

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>Skapa en global HTTP-proxy på Android Enterprise-enhet ägare enheter <!-- 4816339  -->
På Android Enterprise-enheter kan du konfigurera en global HTTP-proxy som uppfyller organisationens webb läsar standarder (**enhets konfiguration** > **profiler** > **Skapa profil** > **Android Enterprise** för plattforms > **enhets ägare > enhets begränsningar** för profil typ > **anslutning**). När den har kon figurer ATS kommer all HTTP-trafik att använda denna proxy.

Gäller för:
- Ägare av Android Enterprise-enhet

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>Ny enhets profil för konfigurations gränssnitt för enheter för enheter med Windows 10 och senare <!-- 2266073  -->
På Windows 10 och senare kan du skapa en enhets konfigurations profil för att kontrol lera inställningar och funktioner (**enhets konfiguration** > **profiler** > **Skapa profil** > **Windows 10 och senare** för plattform). Det kommer att finnas en ny profil typ för konfigurations gränssnitt för inbyggd enhet som tillåter Intune att hantera UEFI-inställningar (BIOS).

Om du vill se en översikt över alla aktuella inställningar som du kan konfigurera, se [tillämpa funktioner och inställningar på dina enheter med hjälp av enhets profiler i Microsoft Intune](../configuration/device-profiles.md).

Gäller för:
- Windows 10-RS5 (1809) och senare på utvalda enheter

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>PKCS-certifikat för macOS  <!-- 1333650                -->
Vi lägger till fullständigt stöd för PKCS-certifikat på enheter som kör macOS. Användare kommer att kunna distribuera användar-och enhets certifikat med fälten anpassnings ämne och alternativt namn för certifikat mottagare. Vi kommer också att ha en ny inställning som tillåter all åtkomst till appar, vilket genom att aktivera ger alla associerade appar åtkomst till den privata nyckeln. Mer information om den här inställningen finns i följande Apple-dokumentation: https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>Härledda autentiseringsuppgifter för att etablera mobila enheter med certifikat      <!--  1736036, 1736037, 1772050      --> 
Vi kommer att lägga till stöd för härledda autentiseringsuppgifter som stöder *National Institute of Standards and Technology (NIST) 800-157* standard för att distribuera certifikat till enheter.  Härledda autentiseringsuppgifter är beroende av att ett PIV-kort (personal Identity Verification) eller ett Common Access Card-kort (KOMPATIBILITETSSTATUS) används, till exempel ett smartkort. Användare autentiseras med smartkortet på en dator och skickar sedan en begäran om ett certifikat för den hanterade enheten enligt den process som krävs av providern för härledd autentisering.   

Processen att använda härledda autentiseringsuppgifter för att hämta ett certifikat skiljer sig från att använda SCEP-eller PKCS-certifikat profiler, men slut resultatet är samma – mobila enheter med certifikat för autentisering som kan användas för app-autentisering, VPN, Wi-Fi eller e-post filer.   

Mer information finns i [härledda PIV-autentiseringsuppgifter](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) på www.nccoe.nist.gov.

Den första versionen av härledda autentiseringsuppgifter stöder Entrust Datacard, överDISAa och purebred på iOS. Ytterligare plattformar och härledda Credential-leverantörer kommer att stödjas i senare versioner.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Enhetsregistrering

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>Ange vilka operativ Systems versioner för Android-enheter som registreras med arbets profil eller enhets administratörs registrering <!-- 4350697 -->
Med begränsningar för enhets typ i Intune kan du använda enhetens operativ system version för att ange vilka användar enheter som ska använda Android företags arbets profil registrering eller registrering av Android-enhets administratörer. Det gör du genom att gå **till Intune** > **enhets registrering** > **registrerings begränsningar** > **skapa begränsning** > **enhets typ begränsning** > **plattforms inställningar**.

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>Redigera enhets namn värde för autopilot-enheter <!-- 4816775 -->
Du kan redigera enhets namn svärdet för Azure AD-anslutna autopilot-enheter. Det gör du genom att gå till **Intune** >  **enhets registrering** > **Windows-registrering** > **windows autopilot** > **enheter** > Välj enhet > ändra värdet för enhets namn i den högra rutan > **Spara** .

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>För iOS-enheter anpassar du registreringsprocessens sekretessida i Företagsportal <!-- 4394993  -->
Med Markdown kan du anpassa sekretessidan i Företagsportal som slutanvändare ser vid iOS-registrering. Mer specifikt kan du anpassa listan med saker som organisationen inte kan se eller göra på enheten.

<!-- ***********************************************-->
## <a name="device-management"></a>Enhetshantering


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>Redigera grupp märkes värde för autopilot-enheter<!-- 4816775 -->
Du kan redigera grupp märkes värdet för autopilot-enheter. Det gör du genom att gå till **Intune** >  **enhets registrering** > **Windows-registrering** > **windows autopilot** > **enheter** > Välj enhet > ändra värdet för grupp tag gen i den högra rutan > **Spara** .

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Användar gränssnitts uppdatering för att skapa och redigera Windows 10-uppdaterings ringar  <!-- 4099089          -->   
Vi kommer att lansera en uppdaterad användar gränssnitts upplevelse för att skapa och redigera för Windows 10 uppdaterings ringar för Intune.  Ändringar i användar gränssnittet kommer att innehålla:  
- Förenkla den befintliga upplevelsen genom att använda ett format format med en guide som är komprimerat på ett blad. Den här användar gränssnitts uppdateringen kommer att utföras med blad tillväxten som kräver IT-proffs för att öka detalj nivån i djupgående blad.   
- Ändra Create-flödet för att inkludera tilldelningar.  
- Att lägga till en sammanfattnings sida för alla saker som anges när du visar egenskaper, innan du skapar en ny uppdaterings ring och när du redigerar en egenskap. Vid redigering visar sammanfattningen bara listan över objekt som har angetts i kategorin med egenskaper som redigeras.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>Användar gränssnitts uppdatering för att skapa och redigera iOS-programuppdateringar  <!-- 4099090        -->   
Vi kommer att lansera en uppdaterad GRÄNSSNITTs upplevelse för att skapa och redigera för iOS-programuppdateringar till Intune. Ändringar i användar gränssnittet kommer att innehålla:
- Förenkla den befintliga upplevelsen genom att använda ett format format med en guide som är komprimerat på ett blad. Den här användar gränssnitts uppdateringen kommer att utföras med blad tillväxten som kräver IT-proffs för att öka detalj nivån i djupgående blad.  
- Det skapa flödet för iOS-programuppdaterings policyn kommer att uppdateras för att inkludera tilldelningar 
- IOS-programuppdaterings principen innehåller en sammanfattnings sida för alla saker som anges när du visar egenskaper, innan du skapar en ny princip och när du redigerar en egenskap. Vid redigering visar sammanfattningen bara listan över objekt som har angetts i kategorin med egenskaper som redigeras.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Mål användar grupper för macOS för att kräva JAMF-hantering <!-- 4061739 -->
Du kan rikta in dig på specifika grupper av användare för att kräva att deras macOS-enheter hanteras av JAMF. Den här anpassningen gör att du kan använda JAMF-kompatibilitet för en delmängd av macOS-enheter medan andra enheter fortsätter att hanteras av Intune. Du kan också gradvis migrera användarnas enheter från en MDM till en annan.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Nya begränsningar för namnbyte av Windows-enheter <!-- 3478938 -->
Enhets namn måste följa dessa regler:
- 15 tecken eller mindre (måste vara mindre än eller lika med 63 byte, inte inklusive avslutande NULL)
- Inte null eller en tom sträng
- Tillåten ASCII: bokstäver (a-z, A-Z), siffror (0-9) och bindestreck
- Tillåtet Unicode: tecken > = 0x80, måste vara en giltig UTF8, måste vara IDN-mappnings Bart (RtlIdnToNameprepUnicode lyckades, se RFC 3492)
- Namn får inte innehålla siffror eller börja med ett tal
- Inga blank steg i namnet
- Otillåtna tecken: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Distribuera program uppdateringar till macOS-enheter <!-- 3194876 -->
Du kan distribuera program uppdateringar till grupper av macOS-enheter. Den här funktionen inkluderar kritisk, inbyggd program vara, konfigurations fil och andra uppdateringar. Du kommer att kunna skicka uppdateringar på nästa enhet checka in eller välja ett vecko schema för att distribuera uppdateringar i eller från tidsfönster som du har angett. Den här funktionen hjälper dig när du vill uppdatera enheter utanför standard arbets tiden eller när supportavdelningen är helt bemannad. Du får också en detaljerad rapport om alla macOS-enheter med distribuerade uppdateringar. Du kan öka detalj nivån för rapporten per enhet för att se status för särskilda uppdateringar.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>Sidan översikt över nya Android-rapporter på enheter <!-- 2984353  -->
Vi kommer att lägga till en ny rapport på sidan enhets översikt som visar hur många Android-enheter som har registrerats i varje enhets hanterings lösning. Det här diagrammet visar arbets profil, fullständigt hanterade, dedikerade och enhets administratör registrerade enheter. Om du vill se rapporten väljer du **Intune** > **enheter** > -**Översikt**.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Windows Autopilot-distributionsrapporter <!-- 3856172  -->
En ny rapport visar varje enhet som distribueras via Windows autopilot. Dessa data är tillgängliga i 30 dagar efter distributionen. Om du vill se rapporten går du till **Intune** > **enhets registrering** > **övervaka** > **autopilot-distributioner**.

### <a name="updated-support-experience-------5012398------"></a>Uppdaterad support upplevelse   <!--  5012398    -->
Som en del av fortsatta förbättringar kommer vi att uppdatera support upplevelsen i konsolen för Intune.  Vi kommer att förbättra sökningen och feedbacken i konsolen för vanliga problem och effektivisera arbets flödet för att kontakta supporten.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).




