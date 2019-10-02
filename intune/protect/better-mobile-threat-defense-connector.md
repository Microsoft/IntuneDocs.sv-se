---
title: Better Mobile Threat Defense-anslutning i Intune
titleSuffix: Intune on Azure
description: Ställ in Better Mobile Threat Defense-anslutningen i Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd7401469d6fdc9d8380e27425ad797554e5f243
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723027"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>Better Mobile Threat Defense-anslutning i Intune

Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst baserat på riskbedömning som utförs av Better Mobile, en MTD-lösning (Mobile Threat Defense) som är integrerad i Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som kör Better Mobile-appen.

Du kan konfigurera principer för villkorlig åtkomst baserat på Better Mobiles riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera åtkomst för icke-kompatibla enheter till företagets resurser baserat på de hot som har identifierats.

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>Hur skyddar Intune och Better Mobile företagets resurser?

Better Mobile-appen installeras och körs på mobila enheter. Den här appen avbildar filsystem, nätverksstackar, enheter och programtelemetri där det är tillgängligt, och skickar sedan data till Better Mobiles molntjänst för att utvärdera enhetens risk för mobila hot.

Intune-enhetens efterlevnadsprincip innehåller en regel för Mobile Threat Defense som är baserad på Better Mobiles riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat. Om enheten inte bedöms uppfylla efterlevnadskraven nekas användarna åtkomst till företagsresurser som Exchange Online och SharePoint Online. Användarna får också instruktioner från Better Mobile-appen som är installerad på deras enheter, som hjälper dem att åtgärda problemet så att de kan komma åt företagets resurser igen.

## <a name="sample-scenarios"></a>Exempelscenarier

Nedan visas några vanliga scenarier.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program

När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna från följande åtgärder tills hotet har åtgärdats:

- Ansluta till företagets e-post

- Synkronisera företagets filer med appen OneDrive för arbetet

- Åtkomst till företagsappar

**Blockera när skadliga appar identifieras:**

![Bild som visar att skadliga appar har identifierats](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_blocked.png)

**Åtkomst beviljad när problemet är löst:**

![Beviljad åtkomst till skadliga appar upptäcktes](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket

Identifiera hot mot ditt nätverk såsom **man-in-the-middle**-angrepp, och skydda åtkomsten till Wi-Fi-nätverk baserat på enhetens risk.

**Blockera nätverksåtkomst via Wi-Fi:**

![Blockera nätverksåtkomst via Wi-Fi](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_blocked.png)

**Åtkomst beviljad när problemet är löst:**

![Bild av beviljad åtkomst när problemet är löst](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket

Identifiera hot mot ditt nätverk såsom **man-in-the-middle**-angrepp, och förhindra synkronisering av företagsfiler baserat på enhetens risk för angrepp.

**Blockera SharePoint Online när hot identifieras på nätverket:**

![Blockera SharePoint Online när hot identifieras på nätverket](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_blocked.png)

**Åtkomst beviljad när problemet är löst:**

![Åtkomst beviljad när problemet är löst för Sharepoint-exempel](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Plattformar som stöds

- **Android 4.1 och senare**

- **iOS 8.0 och senare**

## <a name="prerequisites"></a>Krav

- Azure Active Directory Premium

- Microsoft Intune-prenumeration

- Prenumeration på Better Mobile Threat Defense

  - Mer information finns på [Better Mobiles webbplats](https://www.better.mobi/).

## <a name="next-steps"></a>Nästa steg

- [Integrera Better Mobile med Intune](better-mobile-mtd-connector-integration.md)

- [Konfigurera Better Mobile-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Skapa en efterlevnadsprincip för enheter med Better Mobile](mtd-device-compliance-policy-create.md)

- [Aktivera Better Mobile MTD-anslutningen](mtd-connector-enable.md)
