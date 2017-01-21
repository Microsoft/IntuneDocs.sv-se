---
title: "Begränsa åtkomst med enhetsskydd | Microsoft Docs"
description: "Begränsa åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6b83d06ecbe6e202bf022444c288e0866b3507c6
ms.openlocfilehash: 1dd2c4a46857aef1ba273904d58d5eacae99c7bc


---

# <a name="restrict-access-to-company-resource-based-on-device-network-and-application-risk"></a>Begränsa åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk
Du kan styra åtkomst från mobila enheter till företagsresurser baserat på riskbedömning som utförs av Lookout, en lösning för enhetsskydd som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som använder Lookout-tjänsten och inkluderar:
- Säkerhetsproblem med operativsystemversion
- Installerade skadliga program
- Skadliga nätverksprofiler

Du kan konfigurera principer för villkorlig åtkomst baserat på Lookouts riskbedömning som aktiveras via Intunes efterlevnadsprinciper. Med hjälp av inställningarna kan du tillåta eller blockera inkompatibla enheter baserat på de hot som har identifierats.  

## <a name="what-problem-does-this-solve"></a>Vilka problem kan du lösa så här?
Företag behöver skydda känsliga data från nya hot som inkluderar fysiska, app-baserade och nätverksbaserade hot, samt säkerhetsproblem med operativsystem.

Tidigare har företag varit förutseende med att skydda datorer mot angrepp, medan mobila enheter har fått vara oövervakade och oskyddade. Mobila plattformar har ett inbyggt skydd med appisolering och kontrollerade appbutiker för kunder, men dessa plattformar är fortfarande sårbara för sofistikerade attacker. Idag använder många anställda den här typen av enheter för arbete och behöver ha åtkomst till känslig information. Enheter måste skyddas från allt mer sofistikerade attacker.

Intune låter dig kontrollera åtkomst till företagets resurser baserat på riskbedömning som lösningar för enhetsskydd som Lookout tillhandahåller.

## <a name="how-do-intune-and-lookout-device-threat-protection-help-protect-company-resources"></a>Hur skyddar Intune och Lookout enhetsskydd företagets resurser?
Lookouts mobilapp, **Lookout for work**, är installerat och körs på mobila enheter. Den här appen avbildar filsystem, nätverksstackar samt telemetri för enheter och program där det är tillgängligt och skickar det sedan till Lookouts molntjänst för att utvärdera enhetens risk för mobila hot. Du kan ändra risknivåklassificeringen för hot i Lookout-konsolen så som den passar dig.  

Efterlevnadsprincipen i Intune innehåller en regel för Lookout mobilt skydd som baseras på riskbedömningen som utförts av Lookout. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat.

Om enheten utvärderats som inkompatibel kan åtkomst till resurser som Exchange Online och SharePoint Online blockeras. Användarna på blockerade enheter får information om de steg som de måste vidta för att lösa problemet och återfå åtkomst. Den här vägledningen startas via Lookout for work-appen.

## <a name="supported-platforms"></a>Plattformar som stöds:
Följande plattformar har stöd för Lookout efter att ha registrerats i Intune:
* **Android 4.1 och senare**
* **iOS 8 och senare** Mer information om stöd för plattformar och språk finns på [Lookout-webbplatsen](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

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
Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och begränsa åtkomsten till WiFi-nätverk baserat på enhetens risk för angrepp.

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
1.  [Konfigurera din prenumeration med Lookout mobilt skydd](set-up-your-subscription-with-lookout-mtp.md)
2.  [Aktivera anslutning till Lookout MTP i Intune](enable-lookout-mtp-connection-in-intune.md)
3.  [Konfigurera och distribuera Lookout for Work-appen](configure-and-deploy-lookout-for-work-apps.md)
4.  [Konfigurera efterlevnadsprincipen](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Felsöka Lookout-integrering](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)



<!--HONumber=Dec16_HO4-->


