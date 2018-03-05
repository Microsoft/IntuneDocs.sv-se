---
title: Skycure Mobile Threat Defense-anslutningsprogram
description: "Skydda åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk med Skycure Mobile Threat Defense-anslutningsprogrammet och Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7a004e6c-604a-448c-bfb8-cfda63749f5b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 096cd7f2f7895531b00d77c5d26413471fb9bbcf
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2018
---
# <a name="skycure-mobile-threat-defense-connector"></a>Skycure Mobile Threat Defense-anslutningsprogram

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Skycure, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som kör Skycure och inkluderar:

-   Fysiskt skydd

-   Nätverksskydd

-   Programskydd

-   Skydd mot säkerhetsrisker

Du kan konfigurera principer för villkorlig åtkomst baserat på Skycures riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera icke-kompatibla enheter för företagets resurser baserat på de hot som har identifierats.

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>Hur skyddar Intune och Skycure företagets resurser?

Skycures mobilapp för Android eller iOS avbildar filsystem, nätverksstackar samt telemetri för enheter och program där det är tillgängligt. Detta skickas sedan till Skycures molntjänst som utvärderar enhetens risk för mobila hot.

Intune-enhetens efterlevnadsprincip innehåller en regel för Skycure Mobile Threat Defense, som är baserad på Skycures riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat.

Om enheten utvärderats som inkompatibel blockeras åtkomst till resurser som Exchange Online och SharePoint Online. Användarna av blockerade enheter får anvisningar i Skycures mobilapp för att lösa problemet och återfå åtkomsten till företagets resurser.

Intune stöder två lägen för integrering med Skycure:

-   **Grundinställning** är ett skrivskyddat läge som gör Skycure synligt för enheter i Intune.

-   **Fullständig integrering** tillåter att Skycure rapporterar information om enhetsrisker och säkerhetsincidenter till Intune.

## <a name="sample-scenarios"></a>Exempelscenarier

Nedan visas några vanliga scenarier:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program

När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna till dess att hotet har åtgärdats:

-   Ansluta till företagets e-post

-   Synkronisera företagets filer med appen OneDrive för arbetet

-   Åtkomst till företagsappar

**Blockera när skadliga appar identifieras:**

![Skadliga appar har identifierats](../media/mtp/skycure-arch-1.png)

**Åtkomst beviljad när problemet är löst:**

![Beviljad åtkomst till skadliga appar upptäcktes](../media/mtp/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket

Identifiera hot, till exempel **Man-in-the-middle**-angrepp i nätverket, samt skydda åtkomsten till WiFi-nätverk baserat på enhetsrisken.

**Blockera nätverksåtkomst via Wi-Fi:**

![Blockera nätverksåtkomst via Wi-Fi](../media/mtp/skycure-arch-3.png)

**Åtkomst beviljad när problemet är löst:**

![Åtkomst beviljad när problemet är löst](../media/mtp/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket

Identifiera hot, till exempel **Man-in-the-middle**-angrepp i nätverket och förhindra synkronisering av företagsfiler baserat på enhetsrisken.

**Blockera SharePoint Online när hot identifieras på nätverket:**

![Blockera SharePoint Online när hot identifieras på nätverket](../media/mtp/skycure-arch-5.png)

**Åtkomst beviljad när problemet är löst:**

![Åtkomst beviljad när problemet är löst för Sharepoint-exempel](../media/mtp/skycure-arch-6.png)

## <a name="supported-platforms"></a>Plattformar som stöds

-   **Android 4.1 och senare**

-   **iOS 8 och senare**

## <a name="pre-requisites"></a>Förutsättningar

-   Azure Active Directory Premium

-   Microsoft Intune-prenumeration

-   Prenumeration på Skycure Mobile Threat Defense

Mer information hittar du på [Skycures webbplats](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Nästa steg

Här är de steg som du måste utföra om du vill integrera Intune med Skycure:

1.  [Konfigurera Skycure till att använda enkel inloggning (SS) med Azure Active Directory](/intune-classic/deploy-use/configure-skycure-to-use-azure-active-directory-single-sign-on)

2.  [Hämta konfigurationsprincip för Skycures iOS-app](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)

3.  [Lägg till Skycure-appar, Microsoft Authenticator och konfigurationsprincipen för iOS-appar](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)

4.  [Distribuera Skycure-appar, Microsoft Authenticator och konfigurationsprincip för iOS-app](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)

5.  [Konfigurera Skycure-integrering med Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

6.  [Aktivera Skycure Mobile Threat Defense i Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

7.  [Skapa efterlevnadsprincip för Skycure Mobile Threat Defense i Intune](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
