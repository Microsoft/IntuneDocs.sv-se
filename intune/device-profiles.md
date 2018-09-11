---
title: Enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Översikt över olika Microsoft Intune-enhetsprofiler, bland annat funktioner, begräsningar, e-post, Wi-Fi, VPN, utbildning, certifikat, uppgradering av Windows 10, BitLocker och Windows Defender, Windows Information Protection och anpassade inställningar för enhetskonfiguration i Azure Portal. Använd dessa profiler för att hantera och skydda data och enheter i företaget.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: da220e1f82c59f3181d64dc01d071867d62df397
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313980"
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Vad är enhetsprofiler i Microsoft Intune?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune innehåller inställningar och funktioner som du kan aktivera eller inaktivera på olika enheter i din organisation. Dessa inställningar och funktioner hanteras med hjälp av profiler. Några profilexempel: 

- En WiFi-profil som ger olika enheter åtkomst till företagets trådlösa nätverk
- En VPN-profil som ger olika enheter åtkomst till VPN-servern i företagsnätverket

I den här artikeln ges en översikt över de olika profiler du kan skapa för dina enheter. Med de här profilerna kan du tillåta eller förhindra vissa funktioner på enheterna.

## <a name="before-you-begin"></a>Innan du börjar
Om du vill se tillgängliga funktioner öppnar du [Azure Portal](https://portal.azure.com) och din Intune-resurs. 

**Enhetskonfiguration** omfattar följande alternativ:

- **Översikt**: Visar status för dina profiler och ytterligare information om de profiler som du har tilldelat till användare och enheter
- **Hantera**: Skapa enhetsprofiler och överför anpassade [PowerShell-skript](intune-management-extension.md) som ska köras i profilen
- **Övervaka**: Kontrollera status för en profil och visa loggar för dina profiler
- **Installation**: Lägg till en certifikatutfärdare (SCEP eller PFX) eller aktivera kostnadsuppföljning av telekommunikation i profilen

## <a name="create-the-profile"></a>Skapa profilen

[Skapa enhetsprofiler](device-profile-create.md) innehåller stegvisa anvisningar för att skapa en profil. 

## <a name="device-features---ios-and-macos"></a>Enheten har funktioner för – iOS och macOS

[Enhetsfunktioner](device-features-configure.md) styr funktioner på iOS- och macOS-enheter, t.ex. AirPrint, meddelanden och delade enhetskonfigurationer.

Den här funktionen stöder:
- iOS 
- macOS


## <a name="device-restrictions"></a>Enhetsbegränsningar
[Enhetsbegränsningar](device-restrictions-configure.md) styr säkerhet, maskinvara, delning av data och fler inställningar på enheter. Du kan till exempel skapa en profil för enhetsbegränsningar som förhindrar användare av iOS-enheter från att använda kameran på enheten. 

Den här funktionen stöder:

- Android
- iOS
- macOS
- Windows 10
- Windows 10-teamet

## <a name="endpoint-protection"></a>Endpoint Protection
Med [inställningarna för slutpunktsskydd för Windows 10](endpoint-protection-windows-10.md) kan du konfigurera BitLocker- och Windows Defender-inställningar för Windows 10-enheter.

Om du vill publicera Windows Defender Avancerat skydd (WDATP) med Microsoft Intune kan du läsa informationen om att [konfigurera slutpunkter med verktyg för hantering av mobilenheter (MDM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection).

Den här funktionen stöder:
- Windows 10 och senare

## <a name="identity-protection"></a>Identity Protection
[Identity protection](identity-protection-configure.md) styr upplevelsen av Windows Hello for Business på Windows 10- och Windows 10 Mobile-enheter. Konfigurera dessa inställningar för att göra Windows Hello for Business tillgängligt för användare och enheter, samt för att ange krav på PIN-koder för enheter och gester.  

Den här funktionen stöder:  
- Windows 10 och senare
- Windows 10 Holographic for Business  

## <a name="kiosk"></a>Helskärmsläge

Profilen [Inställningar för helskärmsläge](kiosk-settings.md) konfigurerar en enhet för att köra en eller flera appar. Du kan också anpassa andra funktioner i helskärmsläget, som en startmeny och en webbläsare.

Den här funktionen stöder:
- Windows 10 och senare

## <a name="email"></a>E-post
Med profilen för [e-postinställningar](email-settings-configure.md) kan du skapa, tilldela och övervaka Exchange ActiveSync-e-postinställningar på enheter. Med e-postprofiler uppnår du konsekvens, minskar supportsamtalen och ger slutanvändarna åtkomst till företagets e-post på sina personliga enheter utan de behöver konfigurera något själva. 

Den här funktionen stöder: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="vpn"></a>VPN
Med [VPN-inställningar](vpn-settings-configure.md) kan du tilldela VPN-profiler till användare och enheter i din organisation, så att de enkelt och säkert kan ansluta till nätverket. 

Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. Enheter använder en VPN-anslutningsprofil för att initiera en anslutning till VPN-servern. 

Den här funktionen stöder: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8,1
- Windows 10

## <a name="wi-fi"></a>Wi-Fi
Med [Wi-Fi-inställningar](wi-fi-settings-configure.md) kan du tilldela trådlösa nätverksinställningar till användare och enheter. När du tilldelar en Wi-Fi-profil får användarna åtkomst till ditt företags trådlösa nätverk utan att de behöver göra några inställningar själva. 

Den här funktionen stöder: 

- Android
- iOS
- macOS
- Windows 8.1 (endast import)

## <a name="esim-cellular---public-preview"></a>eSIM-mobilnät – offentlig förhandsversion

[Profiler för eSIM-mobilnät](esim-device-configuration.md) ger möjligheten att konfigurera mobildataabonnemang på dina hanterade enheter för åtkomst till Internet och data.  När du har fått aktiveringskoder från mobiloperatören kan du använda Intune för att importera dessa aktiveringskoder och sedan tilldela till dina eSIM-kompatibla enheter.

Den här funktionen stöder:
- Windows 10 Fall Creators Update och senare

## <a name="education"></a>Utbildning
Konfigurationsalternativen [Utbildningsinställningar – Windows 10](education-settings-configure.md) för [appen Windows Take a Test](https://education.microsoft.com/gettrained/win10takeatest). När du konfigurerar dessa alternativ kan inga andra appar köras på enheten förrän provet har slutförts.

I [Utbildningsinställningar – iOS](education-settings-configure-ios-shared.md) används iOS-appen Classroom som hjälp för och stöd till elevernas enheter i klassrummet. Du kan konfigurera iPad-enheter så att flera elever kan dela en enda enhet.

## <a name="edition-upgrade"></a>Versionsuppgradering
Med [Windows 10-versionsuppgraderingar](edition-upgrade-configure-windows-10.md) kan du automatiskt uppgradera enheter som kör vissa versioner av Windows 10 till en senare version.

Den här funktionen stöder: 
- Windows 10 och senare

## <a name="update-policies"></a>Uppdateringsprinciper
I [Uppdateringsprinciper för iOS](software-updates-ios.md) visas hur du skapar och tilldelar iOS-principer för installering av programuppdateringar på iOS-enheterna. Du kan också granska installationsstatusen.

Den här funktionen stöder:
- iOS

## <a name="certificates"></a>Certifikat
Med [certifikat](certificates-configure.md) kan du konfigurera betrodda, SCEP- och PKCS-certifikat som kan tilldelas till enheter och användas för att autentisera trådlösa profiler, VPN- och e-postprofiler.

Den här funktionen stöder: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8,1
- Windows 10

## <a name="windows-information-protection-profile"></a>Profil för Windows informationsskydd
[Windows informationsskydd](windows-information-protection-configure.md) skyddar mot dataläckage utan att störa medarbetarnas användning. Det skyddar även företagsappar och företagsdata mot oavsiktliga dataläckage i företagsägda enheter och personliga enheter som medarbetarna använder på jobbet. Detta sker utan det krävs några ändringar i din miljö eller andra appar.

Den här funktionen stöder:
- Windows 10 och senare

## <a name="custom-profile"></a>Anpassad profil
Med [anpassade inställningar](custom-settings-configure.md) kan du tilldela enhetsinställningar som inte är inbyggda i Intune. Du kan till exempel ange OMA-URI-värden på Android-enheter. På iOS-enheter kan du importera en konfigurationsfil som du har skapat i Apple Configurator. 

Den här funktionen stöder:

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Hantering och felsökning

[Hantera dina profiler](device-profile-monitor.md) för att kontrollera statusen för enheter och tilldelade profiler. Hjälp även till att lösa konflikter genom att se inställningarna som orsakar en konflikt och de profiler som innehåller dessa inställningar. [Vanliga problem och lösningar](device-profile-troubleshoot.md) ger en lista med frågor och svar för att hjälpa till att arbeta med profiler, bland annat vad som händer när en profil tas bort, vad som orsakar att meddelanden skickas till enheter med mera.