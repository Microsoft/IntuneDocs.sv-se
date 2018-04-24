---
title: Lookout Mobile Threat Defense-anslutningsprogram
description: Skydda åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk med Lookout Mobile Threat Defense-anslutningsprogrammet och Intune.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 85a296c28658b8eb3db5e5e99dcd573b3b98e0ea
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Lookout Mobile Threat Defense-anslutningsprogram med Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Du kan styra åtkomsten från mobila enheter till företagsresurser baserat på den riskbedömning som utförs av Lookout, en Mobile Threat Defense-lösning som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som använder Lookout-tjänsten och inkluderar:
- Säkerhetsproblem med operativsystemversion
- Installerade skadliga program
- Skadliga nätverksprofiler

Du kan konfigurera principer för villkorlig åtkomst baserat på Lookouts riskbedömning som aktiveras via Intunes efterlevnadsprinciper. Med hjälp av inställningarna kan du tillåta eller blockera inkompatibla enheter baserat på de hot som har identifierats.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>Hur skyddar Intune och Lookout Mobile Threat Defense företagets resurser?
Lookouts mobilapp, **Lookout for work**, är installerat och körs på mobila enheter. Den här appen avbildar filsystem, nätverksstackar samt telemetri för enheter och program där det är tillgängligt och skickar det sedan till Lookouts molntjänst för att utvärdera enhetens risk för mobila hot. Du kan ändra risknivåklassificeringen för hot i Lookout-konsolen så som den passar dig.  

Efterlevnadsprincipen i Intune innehåller en regel för Lookout Mobile Threat Defense som baseras på Lookouts riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat.

Om enheten utvärderats som inkompatibel kan åtkomst till resurser som Exchange Online och SharePoint Online blockeras. Användarna på blockerade enheter får information om de steg som de måste vidta för att lösa problemet och återfå åtkomst. Den här vägledningen startas via Lookout for work-appen.

## <a name="supported-platforms"></a>Plattformar som stöds:
Följande plattformar har stöd för Lookout efter att ha registrerats i Intune:
* **Android 4.1 och senare**
* **iOS 8 och senare** Mer information om stöd för plattformar och språk finns på [Lookout-webbplatsen](https://personal.support.lookout.com/hc/articles/114094140253).

## <a name="prerequisites"></a>Krav:
* Microsoft Intune-prenumeration
* Azure Active Directory
* Enterprise-prenumeration för Lookout Mobile EndPoint Security  

Se [Lookout Mobile EndPoint Security](https://www.lookout.com/products/mobile-endpoint-security) för mer information

## <a name="sample-scenarios"></a>Exempelscenarier
Nedan följer några vanliga scenarier:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program
När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna från följande till dess att hotet har åtgärdats:
* Ansluta till företagets e-post
* Synkronisera företagets filer med appen OneDrive för arbetet
* Åtkomst till företagsappar

**Blockera när skadliga program upptäcks:**
![diagram som visar en villkorlig åtkomstprincip som blockerar åtkomst när en enhet bedöms vara icke-kompatibel på grund av skadliga appar på enheten](../media/mtp/malicious-apps-blocked.png)

**Åtkomst beviljad när problemet är löst:**

![diagram som visar hur en princip för villkorlig åtkomst beviljar åtkomst när en enhet bedöms vara kompatibel efter problemet åtgärdats](../media/mtp/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket
Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och skydda åtkomsten till WiFi-nätverk baserat på enhetens risk för angrepp.

**Blockera åtkomst till nätverket via WiFi:**
![diagram som visar hur villkorlig åtkomst blockerar WiFi-åtkomst baserat på nätverkshot](../media/mtp/network-wifi-blocked.png)

**Åtkomst beviljad när problemet är löst:**

![diagram som visar hur villkorlig åtkomst beviljar åtkomst efter att hotet har oskadliggjorts](../media/mtp/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket

Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och förhindra synkronisering av företagsfiler baserat på enhetens risk för angrepp.

**Blockera SharePoint Online när hot identifieras på nätverket:**

![Diagram som visar hur villkorlig åtkomst blockerar enheter från att få åtkomst till SharePoint Online baserat på identifiering av hot](../media/mtp/network-spo-blocked.png)


**Åtkomst beviljad när problemet är löst:**

![Diagram som visar hur villkorlig åtkomst beviljar åtkomst efter att hotet har oskadliggjorts](../media/mtp/network-spo-unblocked.png)

## <a name="next-steps"></a>Nästa steg
Här följer de åtgärder du måste utföra för att implementera den här lösningen:
1.  [Konfigurera prenumerationen av Lookout](setup-your-lookout-mtd-subscription.md)
2.  [Aktivera Lookout Mobile Threat Defense i Intune](enable-lookout-mtd-connection.md)
3.  [Konfigurera och distribuera Lookout Mobile Threat Defense-appen](configure-deploy-lookout-for-work-app.md)
4.  [Konfigurera Lookout-enhetens efterlevnadsprincip](create-lookout-device-compliance-policy.md)
5.  [Felsöka Lookout Mobile Threat Defense-integreringen](/intune-classic/troubleshoot/device-threat-protection-troubleshooting)
