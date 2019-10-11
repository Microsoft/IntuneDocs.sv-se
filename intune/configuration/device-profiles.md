---
title: Funktioner och inställningar för enheter i Microsoft Intune – Azure | Microsoft Docs
description: Översikt över de olika enhetsprofilerna i Microsoft Intune. Få information om funktioner, begränsningar, e-post, Wi-Fi, VPN, utbildning, certifikat, uppgradering av Windows 10, BitLocker och Windows Defender, Windows Information Protection, administrativa mallar och anpassade inställningar för enhetskonfiguration i Azure-portalen. Använd dessa profiler för att hantera och skydda data och enheter i företaget.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3afdb365d0ed88a58028287cc7010bb334e9001e
ms.sourcegitcommit: fca2670142c083d7562c0a36547a6a451863e315
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/08/2019
ms.locfileid: "72036441"
---
# <a name="apply-features-and-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Tillämpa funktioner och inställningar på dina enheter med enhetsprofiler i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune innehåller inställningar och funktioner som du kan aktivera eller inaktivera på olika enheter i din organisation. Dessa inställningar och funktioner läggs till i ”konfigurationsprofiler”. Du kan skapa profiler för olika enheter och plattformar, till exempel iOS, Android och Windows. Använd sedan Intune för att tillämpa eller ”tilldela” profilen till enheterna.

Använd dessa konfigurationsprofiler som en del av din lösning för hantering av mobilenheter till att utföra olika uppgifter. Några profilexempel:

- På Windows 10-enheter använder du en profilmall som blockerar ActiveX-kontroller i Internet Explorer.
- Tillåt användare på iOS- och macOS-enheter att använda AirPrint-skrivare i organisationen.
- Tillåt eller förhindra åtkomst till Bluetooth på enheten.
- Skapa en WiFi- eller VPN-profil som ger olika enheter åtkomst till företagsnätverket.
- Hantera programuppdateringar, till exempel när de installeras.
- Kör en Android-enhet som en dedikerad kioskenhet som kan köra en eller flera appar.

I den här artikeln ges en översikt över de olika profiltyper som du kan skapa. Med de här profilerna kan du tillåta eller förhindra vissa funktioner på enheterna.

## <a name="administrative-templates"></a>Administrativa mallar

[Administrativa mallar](administrative-templates-windows.md) innehåller hundratals inställningar som du kan konfigurera för Internet Explorer, OneDrive, fjärrskrivbord, Word, Excel och andra Office-program.

Dessa mallar ger administratörer en förenklad vy över inställningar som liknar grupprinciper, men de är helt molnbaserade.

Den här funktionen stöder:

- Windows 10 och senare

## <a name="certificates"></a>Certifikat

[Certifikat](../protect/certificates-configure.md) konfigurerar betrodda certifikat, SCEP- och PKCS-certifikat som har tilldelats till enheter. De här certifikaten autentiserar Wi-Fi-, VPN- och e-postprofiler.

Den här funktionen stöder: 

- Android
- Android enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8,1
- Windows 10 och senare

## <a name="custom-profile"></a>Anpassad profil

Med [Anpassade inställningar](../custom-settings-configure.md) kan administratörer tilldela enhetsinställningar som inte är inbyggda i Intune. Du kan ange OMA-URI-värden på Android-enheter. På iOS-enheter kan du importera en konfigurationsfil som du har skapat i Apple Configurator.

Den här funktionen stöder:

- Android
- Android enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1

## <a name="delivery-optimization"></a>Leveransoptimering

[Leveransoptimering](../delivery-optimization-windows.md) ger en bättre upplevelse vid leverans av programuppdateringar. De här inställningarna ersätter inställningarna i **Programuppdateringar** > **Windows 10-uppdateringsring**.

Använd inställningarna för att styra hur programuppdateringar laddas ned till enheter i din organisation. Du kan exempelvis låta användarna hämta sina egna uppdateringar, eller hämta uppdateringar med hjälp av leveransoptimeringens molntjänster i en enhetsprofil.

Den här funktionen stöder:

- Windows 10 och senare

## <a name="device-features"></a>Enhetsfunktioner

[Enhetsfunktioner](../device-features-configure.md) styr funktioner på iOS- och macOS-enheter, t.ex. AirPrint, meddelanden och låsskärmsmeddelanden.

Den här funktionen stöder:

- iOS/iPadOS
- macOS

## <a name="device-restrictions"></a>Enhetsbegränsningar

[Enhetsbegränsningar](device-restrictions-configure.md) styr säkerhet, maskinvara, delning av data och fler inställningar på enheter. Du kan till exempel skapa en profil för enhetsbegränsningar som förhindrar användare av iOS-enheter från att använda kameran på enheten. 

Den här funktionen stöder:

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 10 och senare
- Windows 10-teamet

## <a name="edition-upgrade"></a>Versionsuppgradering

Med [Windows 10-versionsuppgraderingar](edition-upgrade-configure-windows-10.md) kan du automatiskt uppgradera enheter som kör vissa versioner av Windows 10 till en senare version.

Den här funktionen stöder:

- Windows 10 och senare

## <a name="education"></a>Utbildning

Konfigurationsalternativen [Utbildningsinställningar – Windows 10](education-settings-configure.md) för [appen Windows Take a Test](https://education.microsoft.com/gettrained/win10takeatest). När du konfigurerar dessa alternativ kan inga andra appar köras på enheten förrän provet har slutförts.

I [Utbildningsinställningar – iOS](../fundamentals/education-settings-configure-ios-shared.md) används iOS-appen Classroom som hjälp för och stöd till elevernas enheter i klassrummet. Du kan konfigurera iPad-enheter så att många elever kan dela en enda enhet.

## <a name="email"></a>E-post

I [E-postinställningar](email-settings-configure.md) skapas, tilldelas och övervakas Exchange ActiveSyncs e-postinställningar för enheterna. Med e-postprofiler uppnår du konsekvens, minskar supportsamtalen och ger slutanvändarna åtkomst till företagets e-post på sina personliga enheter, utan de behöver konfigurera något själva. 

Den här funktionen stöder: 

- Android
- Android enterprise
- iOS/iPadOS
- Windows Phone 8.1
- Windows 10 och senare

## <a name="endpoint-protection"></a>Endpoint Protection

Med [inställningarna för slutpunktsskydd för Windows 10](../protect/endpoint-protection-windows-10.md) kan du konfigurera BitLocker- och Windows Defender-inställningar för Windows 10-enheter.

Om du vill publicera Microsoft Defender Avancerat skydd (WDATP) med Microsoft Intune kan du läsa informationen om att [konfigurera slutpunkter med verktyg för hantering av mobilenheter (MDM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-mdm).

Den här funktionen stöder:

- Windows 10 och senare

## <a name="esim-cellular---public-preview"></a>eSIM-mobilnät – offentlig förhandsversion

Med [Profiler för eSIM-mobilnät](esim-device-configuration.md) kan administratörer konfigurera mobildataabonnemang på dina hanterade enheter för åtkomst till Internet och data. När du har fått aktiveringskoder från mobiloperatören kan du använda Intune för att importera dessa aktiveringskoder och sedan tilldela dem till dina eSIM-kompatibla enheter.

Den här funktionen stöder:

- Windows 10 Fall Creators Update och senare

## <a name="extensions"></a>Tillägg

[Kernel-tillägg](kernel-extensions-overview-macos.md) låter administratörer lägga till ytterligare funktioner eller program på kernelnivå på macOS-enheter. Konfigurera dessa inställningar för att lita på alla tillägg från en specifik utvecklare eller partner eller tillåt vissa kerneltillägg.

Den här funktionen stöder:

- macOS

## <a name="identity-protection"></a>Identity Protection

[Identity protection](../protect/identity-protection-configure.md) styr upplevelsen av Windows Hello for Business på Windows 10- och Windows 10 Mobile-enheter. Konfigurera dessa inställningar för att göra Windows Hello for Business tillgängligt för användare och enheter, samt för att ange krav på PIN-koder för enheter och gester.  

Den här funktionen stöder:  

- Windows 10 och senare
- Windows 10 Holographic for Business  

## <a name="kiosk"></a>Helskärmsläge

Profilen [Inställningar för helskärmsläge](kiosk-settings.md) konfigurerar en enhet till att köra en eller flera appar. Du kan också anpassa andra funktioner i helskärmsläget, som en startmeny och en webbläsare.

Den här funktionen stöder:

- Windows 10 och senare

Inställningar för helskärmsläge finns också som enhetsbegränsningar för [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) och [iOS](device-restrictions-ios.md#kiosk).

## <a name="oemconfig"></a>OEMConfig

[OEMConfig](android-oem-configuration-overview.md) är en standard som gör det möjligt för OEM-tillverkare (originalutrustningstillverkare) och EMM:er (Enterprise Mobility Management) att bygga och stödja OEM-specifika funktioner på ett standardiserat sätt på Android Enterprise-enheter. Med OEMConfig skapar en OEM ett schema som definierar OEM-/regionsspecifika hanteringsfunktioner och bäddar in dem i en app som laddats upp till Google Play. Intune läser in schemat från appen så att Intune-administratörer kan konfigurera inställningarna i schemat.

Den här funktionen stöder:

- Android Enterprise (OEMConfig)

## <a name="powershell-scripts"></a>PowerShell-skript

[PowerShell-skript på Windows 10-enheter](../apps/intune-management-extension.md) använder Intune Management-tillägget för att ladda upp dina PowerShell-skript i Intune och sedan köra dessa skript på dina enheter. Se även vad som krävs för att använda tillägget, hur du lägger till dem i Intune och annan viktig information.


Den här funktionen stöder:

- Windows 10 och senare
- Windows 10 Holographic for Business

## <a name="shared-multi-user-device"></a>Delad enhet för flera användare

[Windows 10](shared-user-device-settings-windows.md) och [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) innehåller inställningar för att hantera enheter med flera användare, som också kallas för delade enheter eller delade datorer. När en användare loggar in på enheten väljer du om användaren kan ändra strömsparalternativen eller spara filer på enheten. I ett annat exempel kan du för att spara utrymme skapa en princip som tar bort inaktiva autentiseringsuppgifter från Windows HoloLens-enheter.

Med dessa inställningar för delade enheter för flera användare kan en administratör kontrollera några av enhetens funktioner och hantera dessa delade enheter med Intune.

Den här funktionen stöder:

- Windows 10 och senare
- Windows 10 Holographic for Business

## <a name="update-policies"></a>Uppdateringsprinciper

I [Uppdateringsprinciper för iOS](../software-updates-ios.md) visas hur du skapar och tilldelar iOS-principer för installering av programuppdateringar på iOS-enheterna. Du kan också granska installationsstatusen.

Se [Leveransoptimering](../delivery-optimization-windows.md) för uppdateringsprinciper på Windows-enheter. 

Den här funktionen stöder:

- iOS/iPadOS

## <a name="vpn"></a>VPN

Med [VPN-inställningar](vpn-settings-configure.md) kan du tilldela VPN-profiler till användare och enheter i din organisation, så att de enkelt och säkert kan ansluta till nätverket. 

Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. Enheter använder en VPN-anslutningsprofil för att initiera en anslutning till VPN-servern. 

Den här funktionen stöder: 

- Android
- Android enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8,1
- Windows 10 och senare

## <a name="wi-fi"></a>Wi-Fi

Med [Wi-Fi-inställningar](wi-fi-settings-configure.md) kan du tilldela trådlösa nätverksinställningar till användare och enheter. När du tilldelar en Wi-Fi-profil får användarna åtkomst till ditt företags trådlösa nätverk utan att de behöver göra några inställningar själva. 

Den här funktionen stöder: 

- Android
- Android enterprise
- iOS/iPadOS
- macOS
- Windows 8.1 (endast import)
- Windows 10 och senare

## <a name="windows-information-protection-profile"></a>Profil för Windows informationsskydd

[Windows informationsskydd](../protect/windows-information-protection-configure.md) skyddar mot dataläckage utan att störa medarbetarnas användning. Det skyddar även företagsappar och företagsdata mot oavsiktliga dataläckage i företagsägda enheter och personliga enheter som medarbetarna använder på jobbet. Windows informationsskydd kräver inte några ändringar i din miljö eller i andra appar.

Den här funktionen stöder:

- Windows 10 och senare

## <a name="zebra-mobility-extensions-mx"></a>Zebra Mobility Extensions (MX)

Med [Zebra Mobility Extensions (MX)](android-zebra-mx-overview.md) kan administratörer använda och hantera Zebra-enheter i Intune. Du skapar StageNow-profiler med dina inställningar och använder sedan Intune för att tilldela och distribuera profilerna till dina Zebra-enheter. [StageNow-loggar och vanliga problem](android-zebra-mx-logs-troubleshoot.md) är en bra resurs om du vill felsöka profiler och se vissa potentiella problem som kan uppstå när du använder StageNow.

Den här funktionen stöder:

- Android (mobilitetstillägg)

## <a name="manage-and-troubleshoot"></a>Hantering och felsökning

[Hantera dina profiler](../device-profile-monitor.md) för att kontrollera statusen för enheter och tilldelade profiler. Du får även hjälp med att lösa konflikter genom att se inställningarna som orsakar en konflikt och de profiler som innehåller dessa inställningar. I [Vanliga problem och lösningar](device-profile-troubleshoot.md) får administratörer hjälp med att arbeta med profiler. Där beskrivs vad som händer när en profil tas bort, vad som orsakar att meddelanden skickas till enheter och mycket mer.

## <a name="next-steps"></a>Nästa steg

Välj din plattform och sätt igång.
