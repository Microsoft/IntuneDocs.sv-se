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
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601526"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Under utveckling för Microsoft Intune – oktober 2019

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

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>Använd mörkt läge i iOS Företagsportal <!-- 4911422  -->
Mörkt läge är planerat för iOS-Företagsportal. Du kommer att kunna hämta företags program, hantera enheter och få IT-support i valfritt färg schema. Mer information om iOS-företagsportalen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](../apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Köra Win32-appar på Windows 10 S-mode-enheter <!-- 3747604  --> 
Du kan installera och köra Win32-appar på enheter som hanteras i Windows 10 S-läge. Skapa en eller flera kompletterande principer för S-läge med hjälp av PowerShell-verktygen för Windows Defender-WDAC (program kontroll). Använd Device Guard-signing Portal för att signera tilläggs principerna. Sedan laddar du upp och distribuerar principerna via Intune. 

I Intune hittar du den här funktionen genom att välja **klient program**  > **Windows 10 S kompletterande principer**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Ange appens tillgänglighet baserat på datum och tid <!-- 3510685  -->
Som administratör kan du konfigurera start tiden och tids gränsen för en obligatorisk app. Vid start tiden laddar Intune Management-tillägget ned appens innehåll och cachelagrar det. Appen kommer att installeras vid tids gränsen. För tillgängliga appar kommer start tiden att diktera när appen visas i Företagsportal. 

Ange appens tillgänglighet baserat på datum och tid:

1. I Intune väljer du **Klientappar** > **Appar**. 
1. Välj en app i listan eller Lägg till en ny genom att välja **Lägg till**. 
1. Från bladet app väljer du **tilldelningar** > **Lägg till grupp**. 
1. Ange **tilldelnings typen** till **obligatorisk** och välj sedan **inkluderade grupper**. 
1. Ställ in **gör den här appen obligatorisk för alla användare** till **Ja**. 
1. Välj **Redigera** för att ändra **slutanvändarens upplevelse** alternativ. 
1. På bladet **slut användar upplevelse** anger du den **tillgängliga tiden för program vara** efter behov. 

Du hittar mer information i [Lägg till appar i Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Kräv att Win32-appar startas om <!-- 3136567  -->
Du kan behöva en Win32-app för att starta om efter en lyckad installation. Du kan välja hur lång tid (Grace-perioden) som ska starta innan omstarten.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Visa meddelanden för Företagsportal-appen i Windows <!-- 1808082  -->
Vi uppdaterar Företagsportal-appen på Windows-enheter för att visa popup-meddelanden till användare, även när programmet stängs. Uppdateringen visar endast meddelanden för tillgängliga appar när installations statusen är slutförd eller inte fungerar. Företagsportal appen visar inte meddelanden för nödvändiga program.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>Visa installations status meddelanden för appen Företagsportal <!-- 2514416  -->
Företagsportal-appen visar ytterligare status meddelanden för Programinstallation för slutanvändare. Följande villkor gäller för nya Win32-beroende funktioner:
- Appen gick inte att installera. Beroenden som definierats av administratören uppfylldes inte.
- Appen har installerats men kräver en omstart.
- Appen håller på att installeras men kräver en omstart för att fortsätta.

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>Tilldela Microsoft Edge beta för macOS <!-- 4678761  -->
Du kan lägga till och tilldela den senaste versionen av Microsoft Edge beta till Intune för macOS-enheter. 

Så här tilldelar du Microsoft Edge beta för macOS-enheter:
1. I Intune väljer du **klient program**  > **appar**  > **Lägg till app**  > **Microsoft Edge – MacOS**. 
1. Tilldela Microsoft Edge beta till de avsedda grupperna. Microsoft AutoUpdate (MAU) håller Microsoft Edge uppdaterat. 
 
Mer information om Microsoft Edge finns i [Hantera webb åtkomst med hjälp av Microsoft Edge med Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurera program meddelande innehåll för organisations konton <!-- 2576686 -->
Med Intune-appen på Android-och iOS-enheter kan du styra appens meddelande innehåll för organisations konton. Den här funktionen kommer att kräva stöd från program och är kanske inte tillgänglig för alla APP-aktiverade program. Mer information om APP finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Ny enhets profil för konfiguration av inbyggd program vara för enheter som kör Windows 10 och senare <!-- 2266073  -->
I Windows 10 och senare kan du skapa en enhets konfigurations profil för att kontrol lera inställningar och funktioner: 

1. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
1. Välj **Windows 10 och senare** som Plattform. 
 
En ny enhets typ för konfigurations gränssnitt för inbyggd enhet gör att Intune kan hantera UEFI-inställningar (BIOS).

Information om de aktuella inställningar som du kan konfigurera finns i [använda funktioner och inställningar på dina enheter med hjälp av enhets profiler i Microsoft Intune](../configuration/device-profiles.md).

Den här funktionen gäller för Windows 10-RS5 (1809) och senare på utvalda enheter.
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Enhetsregistrering

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>För iOS-enheter anpassar du sekretess fönstret för registrering i Företagsportal <!-- 4394993  -->
Med Markdown kan du anpassa företagsportalens sekretessida, som slutanvändarna ser vid iOS-registreringen. Mer specifikt kan du anpassa listan med saker som din organisation inte kan se eller göra på enheten.

<!-- ***********************************************-->
## <a name="device-management"></a>Enhetshantering


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Redigera gruppens märkes värde för autopilot-enheter<!-- 4816775 -->
Du kan redigera **grupp märkes** värdet för autopilot-enheter:

1. Välj **Intune**  > **enhets registrering**  > **Windows-registrering**  > **Windows autopilot** - > **enheter**.
1. Välj enhet.
1. Ändra värdet för **grupp tag gen** i rutan till höger.
1. Välj **Spara**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Mål användar grupper för macOS för att kräva JAMF-hantering <!-- 4061739 -->
Du kan rikta in dig på specifika grupper av användare så att de kräver att deras macOS-enheter hanteras av JAMF. Den här anpassningen gör att du kan använda JAMF-kompatibilitet för en delmängd av macOS-enheter medan andra enheter fortsätter att hanteras av Intune. Med mål kan du också gradvis migrera användarnas enheter från ett MDM-system (Mobile Device Management) till en annan.

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Distribuera program uppdateringar till macOS-enheter <!-- 3194876 -->
Du kan distribuera program uppdateringar till grupper av macOS-enheter. Den här funktionen inkluderar kritisk, inbyggd program vara, konfigurations fil och andra uppdateringar. Du kan skicka uppdateringar vid nästa enhets incheckning. Alternativt kan du välja ett vecko schema för att distribuera uppdateringar i eller utanför perioder som du har angett. 

Den här funktionen hjälper dig när du vill uppdatera enheter utanför standard arbets tid eller utanför timmar när supportavdelningen är helt bemannad. Du får också en detaljerad rapport om alla macOS-enheter som har distribuerade uppdateringar. Du kan öka detalj nivån i rapporten efter enhet för att se status för en viss uppdatering.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Övervakning och fel sökning

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>Android-rapport på sidan enhets översikt <!-- 2984353  -->
Vi lägger till en ny rapport på sidan **enhets översikt** . Rapporten visar hur många Android-enheter som har registrerats i varje enhets hanterings lösning. Diagrammet visar enhets antal för arbets profil, fullständigt hanterad, dedikerad och enhets administratör registrerad. 

Om du vill se rapporten väljer du **Intune** > **enheter** > -**Översikt**.

### <a name="updated-support-experience-------5012398------"></a>Uppdaterad support upplevelse   <!--  5012398    -->
Som en del av fortsatta förbättringar kommer vi att uppdatera support upplevelsen i konsolen för Intune.  Vi förbättrar sökningen och feedbacken i konsolen för vanliga problem och vi effektiviserar arbets flödet för att kontakta supporten.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).
