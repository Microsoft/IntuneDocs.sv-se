---
title: Lookout MTD-anslutningsprogram med Microsoft Intune
titleSuffix: Microsoft Intune
description: Läs mer om hur du integrerar Intune med Lookout Mobile Threat Defense (MTD) för att styra mobil enhetsåtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0123647fb1e8a1d52506ad0753906f974103aad
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502205"
---
# <a name="lookout-mobile-endpoint-security-connector-with-intune"></a>Lookout Mobile Endpoint Security-anslutningsprogram med Intune

Du kan styra åtkomsten från mobila enheter till företagsresurser baserat på den riskbedömning som utförs av Lookout, en Mobile Threat Defense-lösning som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som använder Lookout-tjänsten och inkluderar:
- Säkerhetsproblem med operativsystemversion
- Installerade skadliga program
- Skadliga nätverksprofiler

Du kan konfigurera principer för villkorlig åtkomst baserat på Lookouts riskbedömning som aktiveras med Intunes efterlevnadsprinciper. Med hjälp av inställningarna kan du tillåta eller blockera inkompatibla enheter baserat på de hot som har identifierats.

## <a name="how-do-intune-and-lookout-mobile-endpoint-security-help-protect-company-resources"></a>Hur skyddar Intune och Lookout Mobile Endpoint Security företagets resurser?
Lookouts mobilapp, **Lookout for work**, är installerat och körs på mobila enheter. Den här appen avbildar filsystem, nätverksstackar samt telemetri för enheter och program där det är tillgängligt och skickar det sedan till Lookouts molntjänst för att utvärdera enhetens risk för mobila hot. Du kan ändra risknivåklassificeringen för hot i Lookout-konsolen så som den passar dig.  

Efterlevnadsprincipen i Intune innehåller en regel för Lookout Mobile Threat Defense som baseras på Lookouts riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat.

Om enheten utvärderats som inkompatibel, kan åtkomst till resurser som Exchange Online och SharePoint Online blockeras. Användarna på blockerade enheter får information om de steg som de måste vidta för att lösa problemet och återfå åtkomsten. Den här vägledningen startas via Lookout for work-appen.

## <a name="supported-platforms"></a>Plattformar som stöds  
Följande plattformar har stöd för Lookout efter att ha registrerats i Intune:
* **Android 4.1 och senare**  
* **iOS 8 och senare**  

Mer information om stöd för plattformar och språk finns på [Lookout-webbplatsen](https://personal.support.lookout.com/hc/articles/114094140253).  

## <a name="prerequisites"></a>Krav
* Enterprise-prenumeration för Lookout Mobile EndPoint Security  
* Microsoft Intune-prenumeration
* Azure Active Directory Premium
* Enterprise Mobility och Security (EMS) E3 eller E5, med licenser som tilldelas användare.  

Se [Lookout Mobile EndPoint Security](https://www.lookout.com/products/mobile-endpoint-security) för mer information

## <a name="sample-scenarios"></a>Exempelscenarier

Här visas vanliga scenarier för användning av Mobile Endpoint Security med Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program
När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna från följande till dess att hotet har åtgärdats:
* Ansluta till företagets e-post
* Synkronisera företagets filer med appen OneDrive för arbetet
* Åtkomst till företagsappar

**Blockera när skadliga appar identifieras:**

![Konceptbild av hur principen blockerar åtkomst på grund av skadliga appar](./media/lookout-mobile-threat-defense-connector/malicious-apps-blocked.png)

**Åtkomst beviljad när problemet är löst:**

![Konceptbild som visar när åtkomst beviljas till enheter efter åtgärd](./media/lookout-mobile-threat-defense-connector/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket
Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och skydda åtkomsten till WiFi-nätverk baserat på enhetens risk.

**Blockera nätverksåtkomst via Wi-Fi:**

![Bild som visar blockering av WiFi-åtkomst baserat på nätverkshot](./media/lookout-mobile-threat-defense-connector/network-wifi-blocked.png)

**Åtkomst beviljad när problemet är löst:**

![Konceptbild av Villkorlig åtkomst som beviljar åtkomst efter åtgärd](./media/lookout-mobile-threat-defense-connector/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket

Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och förhindra synkronisering av företagsfiler baserat på enhetens risk för angrepp.

**Blockera SharePoint Online när hot identifieras på nätverket:**

![Konceptbild som visar blockerad åtkomst till SharePoint Online](./media/lookout-mobile-threat-defense-connector/network-spo-blocked.png)


**Åtkomst beviljad när problemet är löst:**

![Konceptbild som visar beviljad åtkomst efter att nätverkshot har åtgärdats](./media/lookout-mobile-threat-defense-connector/network-spo-unblocked.png)

## <a name="next-steps"></a>Nästa steg
Här följer de åtgärder du måste utföra för att implementera den här lösningen:
1. [Ställa in Lookout-integrering](lookout-mtd-connector-integration.md)
2. [Aktivera Mobile Endpoint Security i Intune](mtd-connector-enable.md)
3. [Lägga till och tilldela appen Lookout for Work](mtd-apps-ios-app-configuration-policy-add-assign.md)
4. [Konfigurera Lookout-enhetens efterlevnadsprincip](mtd-device-compliance-policy-create.md)
