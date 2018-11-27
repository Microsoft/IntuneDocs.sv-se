---
title: Hantera Android-arbetsprofilenheter i Microsoft Intune
titlesuffix: ''
description: Microsoft Intune har stöd för Android-arbetsprofilenheter och ger tillgång till ytterligare hanteringsfunktioner och sekretess när Android-enheter används i arbetet.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4082b845643aae47464e4df14ac6621fcf8f39cf
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180259"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Hantera Android-arbetsprofilenheter med Intune

Android enterprise är en uppsättning funktioner och tjänster som separerar personliga appar och data från arbetsappar och -data. Android enterprise ger tillgång till ytterligare hanteringsfunktioner och sekretess när Android-enheter används i arbetet. 

## <a name="supported-devices"></a>Enheter som stöds

Android enterprise-hanteringsfunktioner använder funktioner som är en del nyare Android-operativsystem. För enheter som inte har stöd för Android enterprise är traditionell Android-hantering fortfarande tillgängligt. Mer information finns i [Krav för Android enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Onboarding

Innan du registrerar Android-arbetsprofilenheter måste du slutföra några onboarding-steg. Dessa steg upprättar en anslutning mellan Intune-klientorganisationen och Googles Play for Work-tjänst. Mer information finns i [Aktivera registrering av Android-arbetsprofilenheter](android-work-profile-enroll.md).

## <a name="work-profile-management"></a>Hantering av arbetsprofiler

När du hanterar en Android-arbetsprofilenhet med Intune hanterar du inte hela enheten. Hanteringsfunktionerna påverkar bara arbetsprofilen som skapas på enheten under registreringen. Appar som distribueras till enheten med Intune installeras i arbetsprofilen. Appikoner i arbetsprofilen skiljs från personliga appar på enheten. Alla Android-appar och data utanför Android enterprise-delen av enheten förblir personliga och kontrolleras av slutanvändaren. Användarna kan installera vilka appar som helst på den personliga sidan av enheten. Administratörer kan hantera och övervaka appar och åtgärder som arbetsprofilen omfattas av.

I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i Android-arbetsprofilenheter. Mer information finns i [Principinställningar för Android-arbetsprofilenheter](compliance-policy-create-android-for-work.md).

## <a name="app-publishing-and-distribution"></a>Publicering och distribution av appar

Google Play for Work-tjänsten är en viktig del av distributionen och hanteringen av Android enterprise-appar. Alla appar som distribuerats på Android-arbetsprofilenheter i arbetsprofilen kommer från Managed Google Play-tjänsten. För att hantera och distribuera appar i Play Store måste du logga in på Google Plays webbplats med ditt företags administratörsautentiseringsuppgifter för Google-hantering. Du kan godkänna appar för Android enterprise-distribution så att de visas i enheternas arbetsprofiler. De här apparna synkroniseras sedan med Intune-konsolen där de sedan kan distribueras och hanteras med hjälp av Intune. Verksamhetsspecifika appar (LOB) som utvecklats av din organisation måste publiceras till Managed Google Play med hjälp av Googles publiceringskonsol för Android-appar. Verksamhetsspecifika appar måste konfigureras i publiceringskonsolen för Android-appar för att begränsa åtkomsten till din organisation.

Appar kan installeras utan användarinteraktion och utan att användaren måste tillåta **installation från okända källor**. Användarna kan söka och installera valfria eller tillgängliga appar i Play for Work-butiken på sin enhet. Mer information finns i [Tilldela appar till Android-arbetsprofilenheter med Intune](apps-add-android-for-work.md).

## <a name="app-configuration"></a>Appkonfiguration

Android enterprise tillhandahåller infrastruktur för distribution av appkonfigurationsvärden till appar som stöder dem. Genom att ange konfigurationsvärden för arbetsappar kan du vara säker på att de konfigureras korrekt första gången användarna startar appen. Stöd för appkonfiguration kräver att apputvecklarna skapar sina Android-appar specifikt för att ge stöd för hanterade konfigurationsvärden. Om de gör det kan du använda Intune för att ange och tillämpa dessa konfigurationsinställningar. Mer information finns i [Lägg till appkonfigurationsprinciper för hanterade Android-enheter](app-configuration-policies-use-android.md).

## <a name="email-configuration"></a>E-postkonfiguration

Android enterprise tillhandahåller inte en standardapp för e-post eller ett internt objekt för e-postprofiler som iOS gör. I stället kan du ange e-postkonfigurationer genom att använda appkonfigurationsinställningar för e-postappar som stöder dem. Gmail och Nine Work är två EAS-klientappar (Exchange ActiveSync) i Play Store som stöder konfiguration med en Android enterprise-appkonfiguration.

Intune tillhandahåller konfigurationsmallar för Gmail- och Nine Work-appar när de hanteras som arbetsappar. Andra e-postappar som stöder appkonfigurationsprofiler kan konfigureras med konfigurationsprinciper för mobilappar.

Om du använder villkorlig Exchange ActiveSync-åtkomst för Android enterprise-enheter kan du använda Gmail- eller Nine Work-e-postappen. Microsoft Outlook för Android-appen, eller andra e-postappar som använder modern autentisering via ADAL, stöds också. Mer information finns i [Konfigurera e-postinställningar i Microsoft Intune](email-settings-configure.md).

## <a name="app-protection-policies"></a>Appskyddsprinciper

Skyddsprinciperna för appar som tillämpas stöds helt och hållet i arbetsprofilen och i den personliga profilen. Du kan publicera affärsappar i publiceringskonsolen för Android-appar på https://play.google.com/apps/publish. Den här konsolen innehåller ett alternativ för att göra appar privata i din organisation. Mer information finns i [Lägga till en efterlevnadsprincip för Android-arbetsprofilenheter i Intune](compliance-policy-create-android-for-work.md). Allmän information om appskyddsprinciper finns i [Vad är appskyddsprinciper?](app-protection-policy.md)

## <a name="vpn-profiles"></a>VPN-profiler

VPN-stöd påminner om Android VPN-profiler. Samma VPN-providrar och grundläggande konfigurationsalternativ är tillgängliga för Android enterprise-hantering, med två skillnader:

-  **VPN begränsat till arbetsprofiler** – VPN-anslutningarna är begränsade till appar som distribuerats till arbetsprofilen. Endast Android enterprise-hanterade appar kan använda VPN-anslutningen. Personliga appar på enheten kan inte använda en hanterad VPN-anslutning. Mer information finns i [VPN-inställningar för Android enterprise](vpn-settings-android.md#android-for-work-vpn-settings).

-  **Appspecifik VPN** – Appspecifik VPN kan konfigureras i Intune om VPN-providern stöder:
    - konfiguration av appspecifik VPN
    - funktionen att konfigurera per app-VPN via Android enterprise-appkonfigurationsprofilen.
    Mer information finns i [Använd en anpassad Microsoft Intune-profil för att skapa en VPN-profil per app för Android-enheter](android-pulse-secure-per-app-vpn.md).

## <a name="certificate-profiles"></a>Certifikatprofiler

Samma konfigurationsalternativ för certifikatprofiler som är tillgängliga för Android-hantering är tillgängliga på Android arbetsprofilenheter. Android enterprise tillhandahåller förbättrade API:er för certifikathantering. Denna förbättrade certifikathantering tillhandahåller följande funktioner:

-  Säkerställer en tyst och sömlös certifikatdistribution för användaren.
-  Säkerställer att distribuerade certifikat tas bort när en enhet dras tillbaka från Intune och arbetsprofilen tas bort.
-  Tillhandahåller förbättrade meddelandefunktioner som meddelar användarna att certifikatet har distribuerats och konfigurerats av deras IT-avdelning via hanteringstjänsten.

Mer information finns i [Konfigurera en certifikatprofil för dina enheter i Microsoft Intune](certificates-configure.md).

## <a name="wi-fi-profiles"></a>Wi-Fi-profiler

Wi-Fi-profiler som hanteras av Android enterprise tas bort när enheten dras tillbaka från Intune och arbetsprofilen tas bort. Mer information finns i [Konfigurera Wi-Fi-inställningar i Microsoft Intune](wi-fi-settings-configure.md).

## <a name="next-steps"></a>Nästa steg
- [Registrera Android-enheter](android-enroll.md)
- [Tilldela appar till Android-arbetsprofilenheter med Intune](apps-add-android-for-work.md)
