---
title: Om Android for Work | Microsoft Intune
description: "Intune har stöd för Android for Work och ger tillgång till ytterligare hanteringsfunktioner och sekretess när Android-enheter används i arbetet."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
translationtype: Human Translation
ms.sourcegitcommit: 83914246bde673b188ca3f7d9cf50b4d0de2edd4
ms.openlocfilehash: 127db326fc96625c719b8136964bae014a904b3d


---

# <a name="manage-android-for-work-devices-with-intune"></a>Hantera Android for Work-enheter med Intune

Android for Work är en samling funktioner och tjänster för Android-enheter. Dessa funktioner och tjänster tillhandahåller ytterligare hanteringsfunktioner och sekretess när Android-enheter används i arbetet. Intune kan hjälpa dig att distribuera appar och företagsresurser till Android for Work-enheter så att arbetsrelaterad och personlig information hålls isär. När de har distribuerats finns apparna och de data som de har åtkomst till helt och hållet i Android for Work-miljön på enheten.

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

## <a name="supported-devices"></a>Enheter som stöds

Android for Work kräver nyare Android-maskinvara eftersom många hanteringsfunktioner använder funktioner som ingår i nyare Android-operativsystem. Android for Work stöds för närvarande på enheter som kör Android 5.0 Lollipop och senare, och som har stöd för arbetsprofiler. För enheter som inte har inbyggt stöd för Android for Work är traditionell Android-hantering fortfarande tillgängligt. Läs mer om [kraven för Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Onboarding

Innan du registrerar Android for Work-enheter måste du slutföra några onboarding-steg. Dessa steg upprättar en anslutning mellan din Intune-klient och Googles Play for Work-tjänst, som är en viktig del i distributionen och hanteringen av Android for Work-appen. Läs mer om hur du [aktiverar registrering av Android for Work-enheter](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-android-for-work).

## <a name="work-profile-management"></a>Hantering av arbetsprofiler

När du hanterar en Android for Work-enhet med Intune hanterar du inte hela enheten. Hanteringsfunktionerna påverkar bara en arbetsprofil som skapas under registreringen. Appar som distribueras till enheten med Intune är en del av arbetsprofilen. Ikonerna för appar i arbetsprofilen visas med en orange portfölj. Den här ikonen gör det lätt att skilja mellan företagsappar och personliga appar på enheten. Alla Android-appar och data utanför Android for Work-delen av enheten förblir personliga och kontrolleras av slutanvändaren. Användare kan installera valfria appar i den personliga delen av enheten, medan administratörer kan hantera och övervaka åtgärder som hör till arbetsprofilen.

## <a name="app-publishing-and-distribution"></a>Publicering och distribution av appar

Google Play for Work-tjänsten är en viktig del av distributionen och hanteringen av appar. Alla appar som har distribuerats till Android for Work-enheter i arbetsprofilen kommer från Play for Work. Om du vill hantera och distribuera appar i Play Store loggar du in som Intune-administratör på webbplatsen för Play for Work och godkänner appar för din Intune-klientorganisation. De här apparna synkroniseras med Intune-konsolen där de sedan kan distribueras och hanteras med hjälp av Intune. Affärsappar (LOB) som utvecklats av din organisation måste publiceras till Play for Work med hjälp av Googles publiceringskonsol för Android-appar. Affärsappar måste konfigureras i publiceringskonsolen för Android-appar för att begränsa åtkomsten till din organisation.

Appar installeras utan användarinteraktion och utan att användaren måste tillåta **installation från okända källor**. Användarna kan bläddra igenom och installera valfria eller tillgängliga appar genom att använda den arbetsmärkta Play Store-appen på deras enheter. Lär dig mer om hur du [distribuerar appar för Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/android-for-work-apps).

## <a name="app-configuration"></a>Appkonfiguration

Android for Work tillhandahåller infrastruktur för distribution av appkonfigurationsvärden till appar som stöder dem. Genom att ange konfigurationsvärden för arbetsappar kan du vara säker på att de konfigureras korrekt första gången användarna startar appen. Stöd för appkonfiguration kräver att apputvecklarna skapar sina Android-appar specifikt för att ge stöd för hanterade konfigurationsvärden. Om de gör det kan du använda Intune för att ange och tillämpa dessa konfigurationsinställningar. Lär dig mer om [konfigurationsinställningarna för Android for Work-appen](afw-app-configuration-policy.md).

## <a name="email-configuration"></a>E-postkonfiguration

Android for Work tillhandahåller inte en standardapp för e-post eller ett internt objekt för e-postprofiler som iOS gör. I stället kan du ange e-postkonfigurationer genom att använda appkonfigurationsinställningar för e-postappar som stöder dem. Gmail och Nine Work är två EAS-klientappar (Exchange ActiveSync) i Play Store som stöder konfiguration med en Android for Work-appkonfiguration.

Intune tillhandahåller konfigurationsmallar för Gmail- och Nine Work-appar. Andra e-postappar som stöder appkonfigurationsprofiler kan konfigureras med konfigurationsprinciper för mobilappar.

Om du använder villkorlig EAS-åtkomst för Android for Work-enheter måste du antingen använda Gmail- eller Nine Work-e-postappen. Microsoft Outlook för Android-appen, eller andra e-postappar som använder modern autentisering via ADAL, stöds också. Lär dig mer om [e-postprofiler för företags-e-post](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="mobile-app-management-policies"></a>Hanteringsprinciper för mobilappar

Begränsningsprinciper som tillämpas på appar som har aktiverats för hantering av mobila program (MAM) stöds helt och hållet i arbetsprofilen och i den personliga profilen. Du kan publicera affärsappar i publiceringskonsolen för Android-appar på https://play.google.com/apps/publish. Den här konsolen innehåller ett alternativ för att göra appar privata i din organisation. Lär dig mer om [inställningar för efterlevnadsprinciper](afw-compliance-policy-settings-in-microsoft-intune.md). Mer information finns i [Hanteringsprinciper för mobilappar](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

## <a name="vpn-profiles"></a>VPN-profiler

VPN-stöd påminner om Android VPN-profiler. Samma VPN-providers och grundläggande konfigurationsalternativ är tillgängliga. Det finns två viktiga skillnader:

1.  **VPN begränsat till arbetsprofiler** – VPN-anslutningarna begränsas till appar som distribuerats till arbetsprofilen. Android for Work-hanterade appar kan använda VPN-anslutningen. Personliga appar på enheten kan inte använda en hanterad VPN-anslutning.

2.  **Appspecifik VPN** – Om en VPN-provider stöder konfiguration av appspecifik VPN och konfiguration av ”Per app-VPN” via konfigurationsprofilen för Android for Work-appar så kan appspecifik VPN konfigureras i Intune. Kontakta VPN-providern och fråga om den här funktionen stöds. Lär dig mer om [VPN-anslutningsprofiler](vpn-connections-in-microsoft-intune.md).

## <a name="certificate-profiles"></a>Certifikatprofiler

Samma konfigurationsalternativ för certifikatprofiler som är tillgängliga för traditionell Android-hantering är tillgängliga på Android for Work-enheter. Android for Work tillhandahåller förbättrade API:er för certifikathantering. Denna förbättrade certifikathantering tillhandahåller följande funktioner:

1.  Säkerställer en tyst och sömlös certifikatdistribution för användaren.

2.  Säkerställer att distribuerade certifikat tas bort helt när en enhet dras tillbaka från Intune och arbetsprofilen tas bort.

3.  Tillhandahåller förbättrade meddelandefunktioner som meddelar användarna att certifikatet har distribuerats och konfigurerats av deras IT-avdelning via hanteringstjänsten.

Lär dig mer om [certifikatprofiler](secure-resource-access-with-certificate-profiles.md).

## <a name="wi-fi-profiles"></a>Wi-Fi-profiler

Wi-Fi-profiler som hanteras av Android for Work tas bort när enheten dras tillbaka från Intune och arbetsprofilen tas bort. Lär dig mer om [Wi-Fi-profiler](wi-fi-connections-in-microsoft-intune.md).

## <a name="next-steps"></a>Nästa steg
[Aktivera registrering av Android for Work-enheter](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-android-for-work)
[Distribuera appar för Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/android-for-work-apps)



<!--HONumber=Nov16_HO5-->


