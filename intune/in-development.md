---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7dd6f62cb53dd0cc373fb3f2ffa7d9434b135cd
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494248"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>Under utveckling för Microsoft Intune – juli 2019

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Dessutom:

- Om vi tror att du måste vidta åtgärder innan en ändring genomförs publicerar vi ett extra inlägg i Meddelandecenter för Office.
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


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>Anpassade meddelanden för användare och grupper    <!-- 16766574   -->
Du kommer snart att kunna skicka anpassade adhoc-push-meddelanden från Företagsportalen-program till användare på iOS och Android-enheter du hanterar med Intune. Dessa anpassade meddelanden som inte är knutna till specifika Intune-funktioner och kan användas i något syfte som du behöver, inklusive allmänna meddelanden som du vill skicka till vissa eller alla dina anställda.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurera appen meddelandeinnehåll för organisationskonton <!-- 2576686 -->
Intunes appskyddsprinciper (APP) på Android och iOS-enheter gör att du kan kontroll appinnehåll meddelande för Org konton. Den här funktionen kräver support från program och kanske inte tillgänglig för alla APP aktiverade program. Mer information om APP finns i [Vad är appskyddsprinciper?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Tillgänglig Google Play-apprapportering för Android-arbetsprofiler <!-- 3041956  -->
För tillgängliga appinstallationer på Androids arbetsprofilenheter kan du visa appens installationsstatus samt den installerade versionen av hanterade Google Play-appar. Mer information finns i [Så här övervakar du appskyddsprinciper](app-protection-policies-monitor.md), [Hantera Android-arbetsprofilenheter med Intune](android-enterprise-overview.md) och [Hanterade Google Play-apptyper](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Stöd för IKEv2 VPN-profiler för iOS <!-- 1943438 -->
Du kommer att kunna skapa VPN-profiler för den iOS-inbyggda VPN-klienten med hjälp av IKEv2-protokoll. IKEv2 är en ny anslutningstyp i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **VPN** för profiltyp > **Inställningar**.

De här VPN-profilerna konfigurerar den inbyggda VPN-klienten. Därför installeras eller skickas inga VPN-klientappar till hanterade enheter. Den här funktionen kräver att enheter registreras i Intune (MDM-registrering).

Om du vill se de aktuella VPN-inställningarna som du kan konfigurera går du till [Konfigurera VPN-inställningar på iOS-enheter i Microsoft Intune](vpn-settings-ios.md).

Gäller för: iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Använd ”tillämplighetsregler” när du skapar konfigurationsprofiler för Windows 10-enheter <!-- 2549910 -->
Du skapar konfigurationsprofiler för Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10** som plattform). Du kommer att kunna skapa en **tillämpningsregel** så att profilen endast gäller för en viss utgåva eller en specifik version. Exempelvis kan du skapa en profil som aktiverar vissa BitLocker-inställningar. När du lägger till profilen använder du en tillämpningsregel så att profilen endast gäller för enheter som kör Windows 10 Enterprise.

Gäller för: 
- Windows 10 och senare

### <a name="administrative-templates-for-group-policy---------3510695---"></a>Administrativa mallar för grupprincip     <!--  3510695 -->
För att förbättra säkerheten för enheter i molnet släpper vi administrativa mallar. Med dem kan du använda Intune för att konfigurera val av grupprincipinställningar för Windows-datorer.  Mallarna använder Policy Configuration Service Provider (CSP) för att erbjuda upp till 2 500 ytterligare inställningar från Office, Windows och OneDrive.

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>Hantera FileVault för macOS   <!--  3858502 + 1210104   -->
Du kommer att kunna använda en Intune endpoint protection enhetskonfigurationsprofil för att hantera FileVault krypteringsnyckel för macOS-enheter. Detta inkluderar escrow för visning av och rotera krypteringsnycklar av företagets enheter. Användarna kommer att kunna hämta dessa nycklar via Företagsportalens webbplats.

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Avancerade inställningar för Windows Defender-brandväggen   <!--  1311949     -->
Snart kommer du att kunna använda Intune som offentlig förhandsversion för att hantera anpassade brandväggsregler på klienter för Windows Defender.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Nya configuration designer när du skapar en OEMConfig-profil för Android-företag <!-- 3712769  -->
I Intune kan du skapa en profil för enhetskonfiguration som använder en app som OEMConfig (enhetskonfiguration > profiler > Skapa profil > Android enterprise för plattform > OEMConfig för Profiltyp). När du gör det öppnas en JSON-redigerare med en mall och värden som du kan ändra. Den här uppdateringen innehåller en Konfigurationsdesigner med ett förbättrat användargränssnitt som visar information som är inbäddad i appen, inklusive titlar och beskrivningar. JSON-redigerare finns kvar och visar alla ändringar du gör i Configuration Designer.

Om du vill visa de aktuella inställningarna går du till [Använd och hantera Android-företagsenheter med OEMConfig](android-oem-configuration-overview.md).

Gäller: Android Enterprise


<!-- ***********************************************-->
## <a name="device-management"></a>Enhetshantering

### <a name="improve-device-location---3855417---"></a>Förbättra enhetsplats<!-- 3855417 -->
Du kommer att kunna Zooma in på de exakta koordinaterna för en enhet med den **hitta enhet** åtgärd. Mer information om att hitta försvunna iOS-enheter finns i [hitta borttappade iOS-enheter](device-locate.md).

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Konfigurera automatisk Rensa tidsgränsen till 30 dagar <!--4231059  -->
Du kommer att kunna ställa in automatisk Rensa tidsgränsen så kort som 30 dagar (i stället för aktuella högst 90 dagar) efter den senaste inloggningen. Du gör detta genom att gå till **Intune** > **enheter** > **installationsprogrammet** > **Rensa upp Enhetsregler**.


<!-- ***********************************************-->
## <a name="security"></a>Säkerhet

### <a name="import-and-export-security-baselines------3408610------------"></a>Importera och exportera baslinjer för säkerhet    <!--3408610          -->  
Vi lägger till möjligheten att exportera och importera säkerheten så att du kan ta dina anpassningar med dig och dela filer mellan Intune-miljöer.



<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


