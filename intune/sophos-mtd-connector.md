---
title: Konfigurera Sophos Mobile-integrering med Intune
titleSuffix: Intune on Azure
description: Konfigurera Sophos Mobile-lösningen med Microsoft Intune för att styra mobil enhetsåtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94af7600ddfc5612c666bc38cb871d84c8c4baa5
ms.sourcegitcommit: b1ad73f5c9fd0ad8026c572aef8d15e258951c8f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64880749"
---
# <a name="sophos-mobile-threat-defense-connector-with-intune"></a>Sophos Mobile Threat Defense-anslutning i Intune
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Sophos Mobile, en MTD-lösning (Mobile Threat Defense) som är integrerad i Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som kör Sophos Mobile-appen.
Du kan konfigurera principer för villkorlig åtkomst baserat på Sophos Mobiles riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera åtkomst för icke-kompatibla enheter till företagets resurser baserat på de hot som har identifierats.

## <a name="how-do-intune-and-sophos-mobile-help-protect-your-company-resources"></a>Hur skyddar Intune och Sophos Mobile företagets resurser?
Sophos Mobile-appen för Android och iOS samlar in tillgängliga telemetridata om filsystem, nätverksstackar, enheter och program. Dessa data skickas sedan till Sophos Mobile-molntjänsten för bedömning av risken för mobila hot på enheten.
Intune-enhetens efterlevnadsprincip innehåller en regel för Sophos Mobile Threat Defense som är baserad på Sophos Mobiles riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat. Om enheten inte bedöms uppfylla efterlevnadskraven nekas användarna åtkomst till företagsresurser som Exchange Online och SharePoint Online. Användarna får också instruktioner från Sophos Mobile-appen som är installerad på deras enheter, som hjälper dem att åtgärda problemet så att de kan komma åt företagets resurser igen.  

## <a name="sample-scenarios"></a>Exempelscenarier
Nedan visas några vanliga scenarier.  
### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program
När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna från följande åtgärder tills hotet har åtgärdats:
- Ansluta till företagets e-post
- Synkronisera företagets filer med appen OneDrive för arbetet
- Åtkomst till företagsappar

**Blockera när skadliga appar identifieras**:
 
![Konceptbild av skadliga appar som har identifierats](./media/sophos-mtd-connector/sophos_malicious_apps_blocked.png)  

**Åtkomst beviljad när problemet är löst**:  
![Konceptbild av beviljad åtkomst när problemet är löst](./media/sophos-mtd-connector/sophos_malicious_apps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket  
Identifiera hot mot ditt nätverk såsom man-in-the-middle-angrepp, och skydda åtkomsten till Wi-Fi-nätverk baserat på enhetens risk.  

**Blockera nätverksåtkomst via Wi-Fi**:  
![Blockera nätverksåtkomst via Wi-Fi](./media/sophos-mtd-connector/sophos_network_wifi_blocked.png)

**Åtkomst beviljad när problemet är löst**:   
![Åtkomst beviljad när problemet är löst](./media/sophos-mtd-connector/sophos_network_wifi_unblocked.png)  

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket  
Identifiera hot mot ditt nätverk såsom man-in-the-middle-angrepp, och förhindra synkronisering av företagsfiler baserat på enhetens risk för angrepp.  

**Blockera SharePoint Online när hot identifieras på nätverket**:   
![Blockera SharePoint Online när hot identifieras på nätverket](./media/sophos-mtd-connector/sophos_network_spo_blocked.png)  

**Åtkomst beviljad när problemet är löst**:  
![Åtkomst beviljad när problemet är löst för Sharepoint-exempel](./media/sophos-mtd-connector/sophos_network_spo_unblocked.png)  

## <a name="supported-platforms"></a>Plattformar som stöds  
- Android 5.0 och senare
- iOS 11.0 and later

## <a name="prerequisites"></a>Krav  
- Azure Active Directory Premium
- Microsoft Intune-prenumeration 
- Prenumeration på Sophos Mobile Threat Defense

Mer information finns på [Sophos webbplats](https://www.sophos.com/products/mobile-control).  

## <a name="next-steps"></a>Nästa steg  
- [Integrera Sophos med Intune](sophos-mtd-connector-integration.md)
- [Konfigurera Sophos-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Skapa en efterlevnadsprincip för enheter för Sophos](mtd-device-compliance-policy-create.md)
- [Aktivera Sophos MTD-anslutningsapp](mtd-connector-enable.md)
