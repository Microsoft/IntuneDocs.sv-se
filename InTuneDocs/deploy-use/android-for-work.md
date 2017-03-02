---
title: Om Android for Work | Microsoft Docs
description: "Intune har stöd för Android for Work och ger tillgång till ytterligare hanteringsfunktioner och sekretess när Android-enheter används i arbetet."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a5c024c2139536f004799b18a0f6d1d1eb4875b2
ms.openlocfilehash: bdacb61d1713bf24b2f33f144afa0db356e10ee0
ms.lasthandoff: 02/23/2017


---

# <a name="manage-android-for-work-devices-with-intune"></a>Hantera Android for Work-enheter med Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Android for Work är en uppsättning funktioner och tjänster för Android-enheter som avgränsar personliga appar och data från en arbetsprofil som innehåller arbetsappar och data. Android for Work ger tillgång till ytterligare hanteringsfunktioner och sekretess när Android-enheter används i arbetet. Intune hjälper dig att distribuera appar och företagsresurser till Android for Work-enheter så att arbetsrelaterad och personlig information hålls isär. När de har distribuerats finns apparna och de data som de har åtkomst till helt och hållet i Android for Work-miljön på enheten.

## <a name="supported-devices"></a>Enheter som stöds

Hanteringsfunktioner i Android for Work använder funktioner som ingår i nyare Android-operativsystem. Android for Work stöds för närvarande på enheter som kör Android 5.0 Lollipop och senare, som har stöd för arbetsprofiler. För enheter som inte har stöd för Android for Work är traditionell Android-hantering fortfarande tillgängligt. Läs mer om [kraven för Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Onboarding

Innan du registrerar Android for Work-enheter måste du slutföra några onboarding-steg. Dessa steg upprättar en anslutning mellan din Intune-klient och Googles Play for Work-tjänst, som är en viktig del i distributionen och hanteringen av Android for Work-appen. Läs mer om hur du [aktiverar registrering av Android for Work-enheter](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work).

## <a name="work-profile-management"></a>Hantering av arbetsprofiler

När du hanterar en Android for Work-enhet med Intune hanterar du inte hela enheten. Hanteringsfunktionerna påverkar bara arbetsprofilen som skapas på enheten under registreringen. Appar som distribueras till enheten med Intune installeras i arbetsprofilen. Ikoner för appar i arbetsprofilen visar en orange portfölj för att skilja arbetsappar från personliga appar på enheten. Alla Android-appar och data utanför Android for Work-delen av enheten förblir personliga och kontrolleras av slutanvändaren. Användare kan installera valfria appar i den personliga delen av enheten, medan administratörer kan hantera och övervaka appar och åtgärder som hör till arbetsprofilen.

I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i Android for Work-enheter. Läs mer om [Principinställningar för Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="app-publishing-and-distribution"></a>Publicering och distribution av appar

Google Play for Work-tjänsten är en viktig del av distributionen och hanteringen av Android for Work-appar. Alla appar som har distribuerats till Android for Work-enheter i arbetsprofilen kommer från Play for Work-tjänsten. Om du vill hantera och distribuera appar i Play Store loggar du in som Intune-administratör på webbplatsen för Play for Work och godkänner appar för din Intune-klientorganisation. De här apparna synkroniseras med Intune-konsolen där de sedan kan distribueras och hanteras med hjälp av Intune. Affärsappar (LOB) som utvecklats av din organisation måste publiceras till Play for Work med hjälp av Googles publiceringskonsol för Android-appar. Affärsappar måste konfigureras i publiceringskonsolen för Android-appar för att begränsa åtkomsten till din organisation.

Appar kan installeras utan användarinteraktion och utan att användaren måste tillåta **installation från okända källor**. Användarna kan bläddra igenom och installera valfria eller tillgängliga appar genom att bläddra igenom Play Store på sin enhet. Lär dig mer om hur du [distribuerar appar för Android for Work](https://docs.microsoft.com/intune/deploy-use/android-for-work-apps).

## <a name="app-configuration"></a>Appkonfiguration

Android for Work tillhandahåller infrastruktur för distribution av appkonfigurationsvärden till appar som stöder dem. Genom att ange konfigurationsvärden för arbetsappar kan du vara säker på att de konfigureras korrekt första gången användarna startar appen. Stöd för appkonfiguration kräver att apputvecklarna skapar sina Android-appar specifikt för att ge stöd för hanterade konfigurationsvärden. Om de gör det kan du använda Intune för att ange och tillämpa dessa konfigurationsinställningar. Lär dig mer om [konfigurationsinställningarna för Android for Work-appen](afw-app-configuration-policy.md).

## <a name="email-configuration"></a>E-postkonfiguration

Android for Work tillhandahåller inte en standardapp för e-post eller ett internt objekt för e-postprofiler som iOS gör. I stället kan du ange e-postkonfigurationer genom att använda appkonfigurationsinställningar för e-postappar som stöder dem. Gmail och Nine Work är två EAS-klientappar (Exchange ActiveSync) i Play Store som stöder konfiguration med en Android for Work-appkonfiguration.

Intune tillhandahåller konfigurationsmallar för Gmail- och Nine Work-appar. Andra e-postappar som stöder appkonfigurationsprofiler kan konfigureras med konfigurationsprinciper för mobilappar.

Om du använder villkorlig Exchange ActiveSync-åtkomst för Android for Work-enheter måste du antingen använda Gmail- eller Nine Work-e-postappen. Microsoft Outlook för Android-appen, eller andra e-postappar som använder modern autentisering via ADAL, stöds också. Lär dig mer om [e-postprofiler för företags-e-post](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="mobile-app-management-policies"></a>Hanteringsprinciper för mobilappar

Begränsningsprinciper som tillämpas på appar som har aktiverats för hantering av mobila program (MAM) stöds helt och hållet i arbetsprofilen och i den personliga profilen. Du kan publicera affärsappar i publiceringskonsolen för Android-appar på https://play.google.com/apps/publish. Den här konsolen innehåller ett alternativ för att göra appar privata i din organisation. Lär dig mer om [Inställningar för efterlevnadsprinciper för Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md). Allmän information om MAM-principer finns i [Hanteringsprinciper för mobilappar](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

## <a name="vpn-profiles"></a>VPN-profiler

VPN-stöd påminner om Android VPN-profiler. Samma VPN-providrar och grundläggande konfigurationsalternativ är tillgängliga för Android for Work-hantering, med två skillnader:

-  **VPN begränsat till arbetsprofiler** – VPN-anslutningarna är begränsade till appar som distribuerats till arbetsprofilen. Endast Android for Work-hanterade appar kan använda VPN-anslutningen. Personliga appar på enheten kan inte använda en hanterad VPN-anslutning.

-  **Appspecifik VPN** – Om en VPN-provider stöder konfiguration av appspecifik VPN och konfiguration av ”Per app-VPN” via konfigurationsprofilen för Android for Work-appar så kan en appspecifik VPN konfigureras i Intune. Kontakta VPN-providern och fråga om den här funktionen stöds. Lär dig mer om [VPN-anslutningsprofiler](vpn-connections-in-microsoft-intune.md).

## <a name="certificate-profiles"></a>Certifikatprofiler

Samma konfigurationsalternativ för certifikatprofiler som är tillgängliga för Android-hantering är tillgängliga på Android for Work-enheter. Android for Work tillhandahåller förbättrade API:er för certifikathantering. Denna förbättrade certifikathantering tillhandahåller följande funktioner:

- Säkerställer en tyst och sömlös certifikatdistribution för användaren.
-  Säkerställer att distribuerade certifikat tas bort helt när en enhet dras tillbaka från Intune och arbetsprofilen tas bort.
-  Tillhandahåller förbättrade meddelandefunktioner som meddelar användarna att certifikatet har distribuerats och konfigurerats av deras IT-avdelning via hanteringstjänsten.

Lär dig mer om [certifikatprofiler](secure-resource-access-with-certificate-profiles.md).

## <a name="wi-fi-profiles"></a>Wi-Fi-profiler

Wi-Fi-profiler som hanteras av Android for Work tas bort när enheten dras tillbaka från Intune och arbetsprofilen tas bort. Lär dig mer om [Wi-Fi-profiler](wi-fi-connections-in-microsoft-intune.md).

## <a name="next-steps"></a>Nästa steg
[Aktivera registrering för Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-android-for-work)

[Distribuera appar för Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/android-for-work-apps)

