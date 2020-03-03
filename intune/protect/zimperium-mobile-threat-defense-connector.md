---
title: Zimperium MTD-anslutningsprogram med Intune
titleSuffix: Intune on Azure
description: Läs mer om hur du integrerar Intune med Zimperium Mobile Threat Defense för att styra mobil enhetsåtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d0fe5634e5af6ef4c6f19e067131f151733c0b5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515245"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Zimperium Mobile Threat Defense-anslutning med Intune

Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst, baserat på riskbedömning som utförs av Zimperium, en Mobile Threat Defense-lösning (MTD) som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som kör Zimperium-appen.

Du kan konfigurera principer för villkorlig åtkomst baserat på Zimperiums riskbedömning som aktiveras via Intunes principer för enhetsefterlevnad. Riskbedömningspolicyn kan tillåta eller blockera inkompatibla enheters åtkomst till företagets resurser utifrån identifierade hot.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Hur skyddar Intune och Zimperium företagets resurser?

Zimperium-appen för Android och iOS/iPadOS samlar in tillgängliga telemetridata om filsystem, nätverksstackar, enheter och program. Dessa data skickas sedan till Zimperium-molntjänsten för bedömning av risken för mobila hot på enheten.

Intune-enhetens efterlevnadsprincip innehåller en regel för Zimperium Mobile Threat Defense, som är baserad på Zimperiums riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat. Om enheten inte bedöms uppfylla efterlevnadskraven nekas användarna åtkomst till företagsresurser som Exchange Online och SharePoint Online. Användarna får också instruktioner från Zimperium-appen som är installerad på deras enheter, som hjälper dem att åtgärda problemet så att de kan komma åt företagets resurser igen.

## <a name="sample-scenarios"></a>Exempelscenarier

Nedan följer några scenarier vid integrering av Zimperium med Intune:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program

När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna till dess att hotet har åtgärdats:

- Ansluta till företagets e-post

- Synkronisera företagets filer med appen OneDrive för arbetet

- Åtkomst till företagsappar

**Blockera när skadliga appar identifieras:**

![Konceptbild av skadliga appar som har identifierats](./media/zimperium-mobile-threat-defense-connector/Maliciousapps_blocked_Zimperium.png)

**Åtkomst beviljad när problemet är löst:**

![Konceptbild av beviljad åtkomst när problemet är löst](./media/zimperium-mobile-threat-defense-connector/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket

Identifiera hot, till exempel **Man-in-the-middle**-angrepp i nätverket, samt skydda åtkomsten till WiFi-nätverk baserat på enhetsrisken.

**Blockera nätverksåtkomst via Wi-Fi:**

![Blockera nätverksåtkomst via Wi-Fi](./media/zimperium-mobile-threat-defense-connector/network_wifi_blocked_Zimperium.png)

**Åtkomst beviljad när problemet är löst:**

![Åtkomst beviljad när problemet är löst](./media/zimperium-mobile-threat-defense-connector/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket

Identifiera hot, till exempel **Man-in-the-middle**-angrepp i nätverket och förhindra synkronisering av företagsfiler baserat på enhetsrisken.

**Blockera SharePoint Online när hot identifieras på nätverket:**

![Blockera SharePoint Online när hot identifieras på nätverket](./media/zimperium-mobile-threat-defense-connector/network_spo_blocked_Zimperium.png)

**Åtkomst beviljad när problemet är löst:**

![Åtkomst beviljad när problemet är löst för Sharepoint-exempel](./media/zimperium-mobile-threat-defense-connector/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>Plattformar som stöds

- **Android 4.1 och senare**

- **iOS 8 och senare**

## <a name="prerequisites"></a>Krav

- Azure Active Directory Premium

- Microsoft Intune-prenumeration

- Prenumeration på Zimperium Mobile Threat Defense

  - Mer information finns på [Zimperiums webbplats](https://www.zimperium.com/zips-mobile-ips).

## <a name="next-steps"></a>Nästa steg

- [Integrera Zimperium med Intune](zimperium-mtd-connector-integration.md)

- [Konfigurera Zimperium-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Skapa en Zimperium-princip för enhetsefterlevnad](mtd-device-compliance-policy-create.md)

- [Aktivera Zimperium MTD-anslutningsprogram](mtd-connector-enable.md)
