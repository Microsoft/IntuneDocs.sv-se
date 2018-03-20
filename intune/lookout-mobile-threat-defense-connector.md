---
title: Lookout MTD-anslutningsprogram med Microsoft Intune
titlesuffix: 
description: "Läs mer om hur du integrerar Intune med Lookout Mobile Threat Defense (MTD) för att styra mobil enhetsåtkomst till företagets resurser."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 31369b0bc3c9798f2322233e9d9a7907444c2274
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Lookout Mobile Threat Defense-anslutningsprogram med Intune

Du kan styra åtkomsten från mobila enheter till företagsresurser baserat på den riskbedömning som utförs av Lookout, en Mobile Threat Defense-lösning som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som använder Lookout-tjänsten och inkluderar:
- Säkerhetsproblem med operativsystemversion
- Installerade skadliga program
- Skadliga nätverksprofiler

Du kan konfigurera principer för villkorlig åtkomst baserat på Lookouts riskbedömning som aktiveras med Intunes efterlevnadsprinciper. Med hjälp av inställningarna kan du tillåta eller blockera inkompatibla enheter baserat på de hot som har identifierats.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>Hur skyddar Intune och Lookout Mobile Threat Defense företagets resurser?
Lookouts mobilapp, **Lookout for work**, är installerat och körs på mobila enheter. Den här appen avbildar filsystem, nätverksstackar samt telemetri för enheter och program där det är tillgängligt och skickar det sedan till Lookouts molntjänst för att utvärdera enhetens risk för mobila hot. Du kan ändra risknivåklassificeringen för hot i Lookout-konsolen så som den passar dig.  

Efterlevnadsprincipen i Intune innehåller en regel för Lookout Mobile Threat Defense som baseras på Lookouts riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat.

Om enheten utvärderats som inkompatibel kan åtkomst till resurser som Exchange Online och SharePoint Online blockeras. Användarna på blockerade enheter får information om de steg som de måste vidta för att lösa problemet och återfå åtkomst. Den här vägledningen startas via Lookout for work-appen.

## <a name="supported-platforms"></a>Plattformar som stöds
Följande plattformar har stöd för Lookout efter att ha registrerats i Intune:
* **Android 4.1 och senare**
* **iOS 8 och senare** Mer information om stöd för plattformar och språk finns på [Lookout-webbplatsen](https://personal.support.lookout.com/hc/articles/114094140253).

## <a name="prerequisites"></a>Krav
* Microsoft Intune-prenumeration
* Azure Active Directory
* Enterprise-prenumeration för Lookout Mobile EndPoint Security  

Se [Lookout Mobile EndPoint Security](https://www.lookout.com/products/mobile-endpoint-security) för mer information

## <a name="sample-scenarios"></a>Exempelscenarier

Här visas vanliga scenarier för när Lookout Mobile Threat Defense används med Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program
När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna från följande till dess att hotet har åtgärdats:
* Ansluta till företagets e-post
* Synkronisera företagets filer med appen OneDrive för arbetet
* Åtkomst till företagsappar

**Blockera när skadliga appar identifieras:**

![diagram som visar en princip för villkorlig åtkomst som blockerar åtkomsten när en enhet bedöms vara icke-kompatibel på grund av skadliga appar på enheten](./media/malicious-apps-blocked.png)

**Åtkomst beviljad när problemet är löst:**

![diagram som visar hur en princip för villkorlig åtkomst beviljar åtkomst när en enhet bedöms vara kompatibel efter problemet åtgärdats](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket
Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och skydda åtkomsten till WiFi-nätverk baserat på enhetens risk.

**Blockera nätverksåtkomst via Wi-Fi:**

![diagram som visar hur villkorlig åtkomst blockerar WiFi-åtkomst baserat på nätverkshot](./media/network-wifi-blocked.png)

**Åtkomst beviljad när problemet är löst:**

![diagram som visar hur villkorlig åtkomst beviljar åtkomst efter att hotet har oskadliggjorts](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket

Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och förhindra synkronisering av företagsfiler baserat på enhetens risk för angrepp.

**Blockera SharePoint Online när hot identifieras på nätverket:**

![Diagram som visar hur villkorlig åtkomst blockerar enheter från att få åtkomst till SharePoint Online baserat på identifiering av hot](./media/network-spo-blocked.png)


**Åtkomst beviljad när problemet är löst:**

![Diagram som visar hur villkorlig åtkomst beviljar åtkomst efter att hotet har oskadliggjorts](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>Nästa steg
Här följer de åtgärder du måste utföra för att implementera den här lösningen:
1.  [Ställa in Lookout-integrering](lookout-mtd-connector-integration.md)
2.  [Aktivera Lookout Mobile Threat Defense i Intune](mtd-connector-enable.md)
3.  [Lägga till och tilldela appen Lookout for Work](mtd-apps-ios-app-configuration-policy-add-assign.md)
4.  [Konfigurera Lookout-enhetens efterlevnadsprincip](mtd-device-compliance-policy-create.md)
