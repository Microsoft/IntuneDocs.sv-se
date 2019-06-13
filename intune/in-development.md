---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc5ea7076e77e5071724168fab58fa78f59601c4
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744314"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>Under utveckling för Microsoft Intune – juni 2019

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
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- ***********************************************-->
### <a name="app-management"></a>Apphantering

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Enhetsanvändare kan visa alla hanterade appar som de har installerat eller försökt att installera <!-- 2352913 -->
Företagsportalen för Windows visar alla hanterade appar, både nödvändiga och tillgängliga, som är installerade på en användares enhet. Användare kommer att kunna visa installationsförsök och väntande installationer, och deras aktuella status. Om din organisation inte gör appar obligatoriska eller tillgängliga ser användarna ett meddelande som förklarar att inga företagsappar har installerats. Användarna kommer också att kunna sortera eller filtrera appar baserat på installationsstatus.

#### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956---"></a>Tillgänglig Google Play-apprapportering för Android-arbetsprofiler <!-- 3041956 -->
För tillgängliga appinstallationer på Androids arbetsprofilenheter kan du visa appens installationsstatus samt den installerade versionen av hanterade Google Play-appar. Mer information finns i [Så här övervakar du appskyddsprinciper](app-protection-policies-monitor.md), [Hantera Android-arbetsprofilenheter med Intune](android-enterprise-overview.md) och [Hanterade Google Play-apptyper](apps-add-android-for-work.md#managed-google-play-app-type).

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Konfigurera vilken webbläsare som ska ha tillåtelse att länka till organisationsdata <!-- 3145939 -->
Principer för Intune-appskydd (APP) på enheter med Android och iOS gör att du kan överföra organisationswebblänkar till en viss webbläsare utöver Intune Managed Browser eller Microsoft Edge.  Mer information om APP finns i [Vad är appskyddsprinciper?](app-protection-policy.md).

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>Sidan Installerade appar på företagsportalens webbplats  <!-- 4224326 -->
[Företagsportalwebbplatsen](https://portal.manage.microsoft.com/) innehåller en ny sida för att visa användare alla appar som har installerats på enheten. Den här listan innehåller både tillgängliga appar och de appar som krävs av deras organisation. Användare kommer att kunna se status för installationen och krav för appar på sina enheter från den här sidan. Mer information om företagsportens webbplats finns i [Använda Intune-företagsportalens webbplats](/intune-user-help/using-the-intune-company-portal-website.md) och [Så här konfigurerar du Microsoft Intune-företagsportalappen](company-portal-app.md).

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>Anropa Graph API-läsåtgärder från ett program utan användarens autentiseringsuppgifter <!-- 4655885 -->
Program kan anropa Intune Graph API-läsåtgärder med appidentitet utan användarens autentiseringsuppgifter. Mer information finns i [Get access without a user](https://docs.microsoft.com/graph/auth-v2-service) (Få åtkomst utan användare).

<!-- ***********************************************-->
### <a name="device-configuration"></a>Enhetskonfiguration


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Stöd för IKEv2 VPN-profiler för iOS <!-- 1943438 -->
Du kommer att kunna skapa VPN-profiler för den iOS-inbyggda VPN-klienten med hjälp av IKEv2-protokoll. IKEv2 är en ny anslutningstyp i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **VPN** för profiltyp > **Inställningar**.

De här VPN-profilerna konfigurerar den inbyggda VPN-klienten. Därför installeras eller skickas inga VPN-klientappar till hanterade enheter. Den här funktionen kräver att enheter registreras i Intune (MDM-registrering).

Om du vill se de aktuella VPN-inställningarna som du kan konfigurera går du till [Konfigurera VPN-inställningar på iOS-enheter i Microsoft Intune](vpn-settings-ios.md).

Gäller för: iOS

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>Konfigurera inställningar för kerneltillägg på macOS-enheter <!-- 20430240 -->
På macOS-enheter kan du skapa en enhetskonfigurationsprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **macOS** som plattform). I en kommande uppdatering ingår en ny grupp med inställningar som gör att du kan konfigurera och använda kerneltillägg på dina enheter.

Gäller för: macOS 10.13.2 och senare

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Baslinjestöd för nyckelordssökning  <!-- 3082036         -->
När du skapar eller redigerar en profil för säkerhetsbaslinjen kommer du snart att kunna använda *sökfunktionen* för att filtrera inställningarna som visas i konsolen.   

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Använd ”tillämplighetsregler” när du skapar konfigurationsprofiler för Windows 10-enheter <!-- 2549910 -->
Du skapar konfigurationsprofiler för Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10** som plattform). Du kommer att kunna skapa en **tillämpningsregel** så att profilen endast gäller för en viss utgåva eller en specifik version. Exempelvis kan du skapa en profil som aktiverar vissa BitLocker-inställningar. När du lägger till profilen använder du en tillämpningsregel så att profilen endast gäller för enheter som kör Windows 10 Enterprise.

Gäller för: 
- Windows 10 och senare

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>Appar från inställningen Endast Store för Windows 10-enheter innehåller fler konfigurationsalternativ <!-- 2697002  -->

När du skapar en enhetsbegränsningsprofil för Windows-enheter kan du använda inställningen **Appar endast från Store**. Det gör att användare endast installerar appar från Windows App Store (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp). Den här inställningen kommer att expanderas för att stödja fler alternativ i en kommande uppdatering. 

Gå till [Enhetsinställningar för Windows 10 (och senare) för att tillåta eller begränsa funktioner med hjälp av Intune](device-restrictions-windows-10.md#app-store) för att se de aktuella inställningarna.

Gäller: Windows 10 och senare

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Distribuera flera Zebra Mobility Extensions-enhetsprofiler till en enhet, samma användargrupp eller samma grupp av enheter <!-- 4089955 -->
I Intune kan du använda Zebra Mobility Extensions (MX) i en profil för enhetskonfiguration för att anpassa inställningar eller lägga till inställningar som inte är fördefinierade i Intune. För närvarande kan du distribuera en profil till en enskild enhet. I en kommande uppdatering kommer du att kunna distribuera flera profiler till:

- Samma användargrupp
- Samma enhetsgrupp
- En enskild enhet

[Använda och hantera Zebra-enheter med Zebra Mobility Extensions i Microsoft Intune](android-zebra-mx-overview.md) visar hur du använder MX i Intune.

Gäller: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Vissa inställningar för helskärmsläge på iOS-enheter är angivna till ”Blockera”, vilket ersätter ”Tillåt” <!-- 4404075  -->
När du skapar en enhetsbegränsningsprofil på iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Helskärmsläge**) ställer du in **Autolås**, **Ringsignalsknapp**, **Skärmrotation**, **Viloläge för skärm-knapp** och **Volymknappar**. 

För närvarande kan dessa inställningar konfigureras med hjälp av **Blockera** (blockerar funktionen) eller **Inte konfigurerat** (tillåter funktionen). I en kommande uppdatering blir värdena **Blockera** (blockerar funktionen) eller **Inte konfigurerat** (tillåter funktionen).

Om du vill se de aktuella inställningarna går du till [iOS-enhetsinställningar för att tillåta eller begränsa funktioner](device-restrictions-ios.md). 

Gäller för: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>Använd Face ID för lösenordsautentisering på iOS-enheter <!-- 4490704  -->
När du skapar en enhetsbegränsningsprofil för iOS-enheter kan du använda ett fingeravtryck som lösenord. Inställningarna för lösenord med fingeravtryck kommer även att tillåta ansiktsigenkänning i en kommande uppdatering (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Lösenord**). Därför ändrar du följande inställningar:

- **Upplåsning med fingeravtryck** är nu **Upplåsning av Touch ID och Face ID**.
- **Ändring av fingeravtryck (endast övervakat)** är nu **Ändring av Touch ID och Face ID (endast övervakat)** .

Face ID är tillgängligt i iOS 11.0 och senare. Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](device-restrictions-ios.md#password) för att se de aktuella inställningarna.

Gäller för: iOS

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>Funktionen Appar är beroende av klassificeringsregion för begränsning av spel och App Store-funktioner på iOS-enheter <!-- 4593948  -->
På iOS-enheter kan du tillåta eller begränsa funktioner för spel, App Store och dokumentvisning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel**). Du kan också välja klassificeringsregion, till exempel USA. I en kommande uppdatering blir funktionen **Appar** en underordnad **klassificeringsregion** och blir beroende av **klassificeringsregion**.

Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming) för att se de aktuella inställningarna.

Gäller för: iOS

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>Administrativa mallar för grupprincip     <!--  3510695 -->
För att förbättra säkerheten för enheter i molnet släpper vi administrativa mallar. Med dem kan du använda Intune för att konfigurera val av grupprincipinställningar för Windows-datorer.  Mallarna använder Policy Configuration Service Provider (CSP) för att erbjuda upp till 2 500 ytterligare inställningar från Office, Windows och OneDrive.

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>Nya inställningar för Windows-säkerhetsbaslinjer  <!-- 3534649, 4217151          -->
Vi lägger till nya inställningar för Windows-säkerhetsbaslinjen. Den första inställningen avser virtualiseringsbaserad säkerhet, som kräver säker start. Med den andra inställningen kan du hantera röstaktivering av Windows-appar när skärmen låses.

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>Funktionen Säkerhetsbaslinjer blir nu allmänt tillgänglig  <!--  3785395       -->
Funktionen Säkerhetsbaslinjer lämnar snart förhandsversionen och blir allmänt tillgänglig. 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>Mallen för Windows-säkerhetsbaslinjer blir allmänt tillgänglig   <!--  3794072       -->
Mallen för Windows-säkerhetsbaslinjer lämnar snart förhandsversionen och blir allmänt tillgänglig. Förhandsversionen av mallen kommer att dras tillbaka och en ny mall blir tillgänglig.

<!-- ***********************************************-->
### <a name="device-management"></a>Enhetshantering

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Tilldela omfångstaggar till alla hanterade enheter i en säkerhetsgrupp <!-- 3173810 -->
För närvarande kan du kan tilldela en omfångstagg till en enhet genom att gå till varje enskild enhets **egenskapssida** och välja omfångstaggar. Du kommer att kunna tilldela omfångstaggar till en säkerhetsgrupp, och alla enheter i säkerhetsgruppen kommer också att associeras med omfångstaggarna i en kommande uppdatering. Gör det här genom att välja **Intune** > **Roller** > **Omfång (taggar)**  > **Skapa**  >  **Omfång (taggar)** > välj de grupper som du vill tilldela omfångstaggen till. Alla enheter i grupperna kommer också att tilldelas omfångstaggen. Omfångstaggar med den här funktionen skriver över omfångstaggar med det aktuella flödet för enhetens omfångstaggar. (Det aktuella flödet för att tilldela omfångstaggar till enheter blir skrivskyddat i en kommande uppdatering.)

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>Se säkerhetskorrigeringsnivå för Android-enheter <!-- 4461911  -->
Du kommer att kunna se säkerhetskorrigeringsnivå för Android-enheter. Det gör du genom att välja **Intune** > **Enheter** > **Alla enheter** > välj en enhet > **Övervaka** > **Maskinvara**.


<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


