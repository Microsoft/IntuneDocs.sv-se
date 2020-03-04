---
title: Konfigurera Wandera Mobile Security med Intune
titleSuffix: Intune on Azure
description: Konfigurera Wandera Mobile Security med Microsoft Intune för att styra mobil enhetsåtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f82a64cdb66528e3e1d3a81fd6119c4a99dff504
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782260"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Wandera Mobile Threat Defense-anslutning i Intune  

Styr åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst baserat på riskbedömningar som utförs av Wandera. Wandera är en MTD-lösning (Mobile Threat Defense) som integreras med Microsoft Intune.  Risken bedöms utifrån telemetri som samlas in från enheter som använder Wandera-tjänsten och inkluderar:
- Säkerhetsproblem med operativsystemversion
- Installerade skadliga program
- Skadliga nätverksprofiler
- Cryptojacking

Du kan konfigurera principer för *villkorlig åtkomst* baserat på Wanderas riskbedömning som aktiveras via Intunes principer för enhetsefterlevnad. Riskbedömningspolicyn kan tillåta eller blockera inkompatibla enheters åtkomst till företagets resurser utifrån identifierade hot.  

> [!NOTE]
> Den här Mobile Threat Defense-leverantören stöds inte för oregistrerade enheter.

## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Hur skyddar Intune och Wandera Mobile Threat Defense företagets resurser?  

Wanderas mobilapp installeras sömlöst med Microsoft Intune. Den här appen hämtar information från filsystem, nätverksstackar samt telemetri för enheter och program (i förekommande fall). Den här informationen synkroniseras till Molntjänsten Wandera för att utvärdera enhetens risk för mobila hot. Dessa risknivåklassificeringen kan konfigureras efter dina behov i Wanderas konsol, RADAR.

Efterlevnadsprincipen i Intune innehåller en regel för MTD baserat på Wanderas riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat.

För enheter som är inkompatibla kan åtkomst till resurser som Office 365 blockeras. Användarna av blockerade enheter får anvisningar i Wandera-appen för att lösa problemet och återfå åtkomsten.

## <a name="supported-platforms"></a>Plattformar som stöds  

Följande plattformar har stöd för Wandera efter att ha registrerats i Intune:

- Android 5.0 och senare  
- iOS 10.2 och senare  

Mer information om plattformar och enheter finns på [Wanderas webbplats](https://www.wandera.com/mobile-threat-defense/).

## <a name="prerequisites"></a>Krav  

- Microsoft Intune-prenumeration  
- Azure Active Directory  
- Wandera Mobile Threat Defense (tidigare Wandera Secure)  

Mer information finns i [mobilsäkerhet med Wandera](https://www.wandera.com/mobile-security/).
 
## <a name="sample-scenarios"></a>Exempelscenarier

Här visas vanliga scenarier för användning av Wandera MTD med Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program  

När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna från vanliga verktyg tills hotet har åtgärdats. Vanliga blockeringar är:  
- Ansluta till företagets e-post  
- Synkronisera företagets filer med appen OneDrive för arbetet  
- Åtkomst till företagsappar  

**Blockera när skadliga appar identifieras**:

![Konceptbild av skadliga appar som har identifierats](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**Åtkomst beviljad när problemet är löst**: 

![Konceptbild av beviljad åtkomst när problemet är löst](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket  

Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och skydda åtkomsten till WiFi-nätverk baserat på enhetens risk.  

**Blockera nätverksåtkomst via Wi-Fi**:  

![Blockera nätverksåtkomst via Wi-Fi](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**Åtkomst beviljad när problemet är löst**:  

![Åtkomst beviljad när problemet är löst](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket

Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och förhindra synkronisering av företagsfiler baserat på enhetens risk för angrepp.

**Blockera SharePoint Online när hot identifieras på nätverket**:  

![Blockera SharePoint Online när hot identifieras på nätverket](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**Åtkomst beviljad när problemet är löst**:  

![Åtkomst beviljas när problemet är löst för Sharepoint-exempel](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>Nästa steg

- [Integrera Wandera med Intune](wandera-mtd-connector-integration.md)
- [Konfigurera Wandera-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Skapa en efterlevnadsprincip för Wandera-enheter](mtd-device-compliance-policy-create.md)
- [Aktivera Wandera MTD-anslutningsprogram](mtd-connector-enable.md)
