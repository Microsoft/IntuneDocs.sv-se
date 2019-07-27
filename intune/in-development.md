---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9b02deb529bd6a9bca882fecb3d55d9db513191
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427175"
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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurera program meddelande innehåll för organisations konton <!-- 2576686 -->
Med Intune App Protection-principer (APP) på Android-och iOS-enheter kan du styra appens meddelande innehåll för org-konton. Den här funktionen kommer att kräva stöd från program och är kanske inte tillgänglig för alla APP-aktiverade program. Mer information om APP finns i [Vad är appskyddsprinciper?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Tillgänglig Google Play-apprapportering för Android-arbetsprofiler <!-- 3041956  -->
För tillgängliga appinstallationer på Androids arbetsprofilenheter kan du visa appens installationsstatus samt den installerade versionen av hanterade Google Play-appar. Mer information finns i [Så här övervakar du appskyddsprinciper](app-protection-policies-monitor.md), [Hantera Android-arbetsprofilenheter med Intune](android-enterprise-overview.md) och [Hanterade Google Play-apptyper](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Stöd för IKEv2 VPN-profiler för iOS <!-- 1943438 -->
Du kommer att kunna skapa VPN-profiler för den iOS-inbyggda VPN-klienten med hjälp av IKEv2-protokoll. IKEv2 är en ny anslutningstyp i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **VPN** för profiltyp > **Inställningar**.

De här VPN-profilerna konfigurerar den inbyggda VPN-klienten. Därför installeras eller skickas inga VPN-klientappar till hanterade enheter. Den här funktionen kräver att enheter registreras i Intune (MDM-registrering).

Om du vill se de aktuella VPN-inställningarna som du kan konfigurera går du till [Konfigurera VPN-inställningar på iOS-enheter i Microsoft Intune](vpn-settings-ios.md).

Gäller för: iOS


<!-- ***********************************************-->
## <a name="device-management"></a>Enhetshantering

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Konfigurera automatisk rensning av enhetens tids gräns till 30 dagar <!--4231059  -->
Du kan ställa in den automatiska tids gränsen för enhets rensning så kort som 30 dagar (i stället för den aktuella gränsen på 90 dagar) efter den senaste inloggningen. Det gör du genom att gå till **Intune** > -**enheter** > **Konfigurera** > **enhet rensa regler**.

<!-- ***********************************************-->
## <a name="security"></a>Säkerhet

### <a name="import-and-export-security-baselines------3408610------------"></a>Importera och exportera säkerhets bas linjer    <!--3408610          -->  
Vi lägger till möjligheten att exportera och importera säkerhets bas linjer så att du kan ta dina anpassningar med dig och dela dem mellan Intune-miljöer.


<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


