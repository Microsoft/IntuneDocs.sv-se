---
title: "Begränsa åtkomst med enhetsskydd | Microsoft Intune"
description: "Begränsa åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: d529bd1c2a281c06f70593e73b71d09962a3c714


---

# <a name="restrict-access-to-company-resource-based-on-device-network-and-application-risk"></a>Begränsa åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk
Du kan styra åtkomst från mobila enheter till företagsresurser baserat på riskbedömning som utförs av Lookout, en lösning för enhetsskydd som är integrerad med Microsoft Intune. Risken är baserad på telemetri som Lookout-tjänsten samlar in från enheter för säkerhetsproblem med operativsystem (OS), installerade skadliga appar och skadliga nätverksprofiler. Du kan konfigurera principer för villkorlig åtkomst i Intune baserat på Lookouts rapporterade riskbedömning som aktiveras genom policyer för efterlevnad och tillåta eller blockera enheter som har visats vara inkompatibla på grund av hot som identifieras på enheterna.  

## <a name="what-problem-does-this-solve"></a>Vilka problem kan du lösa så här?
Företag och organisationer behöver skydda känsliga data från nya hot som inkluderar fysiska, app-baserade och nätverksbaserade hot, samt säkerhetsproblem med operativsystem.

Företag och organisationer har tidigare tagit en aktiv roll för att skydda datorer mot skadliga angrepp. Mobila tjänster är ett nytt område som ofta förblir oskyddade. Även om de mobila plattformarna har ett inbyggt skydd för operativsystemet med tekniker som appisolering och kontrollerade appbutiker för kunder är dessa plattformar fortfarande sårbara för sofistikerade attacker. Eftersom mobila enheter används mer och mer av anställda för att utföra arbete och de behöver åtkomst till information som kan vara känslig och värdefull måste dessa enheter skyddas från en mängd olika sofistikerade attacker.

Intune gör det möjligt att kontrollera åtkomst till företagets resurser och data baserat på riskbedömning som lösningar för enhetsskydd som Lookout tillhandahåller.

## <a name="how-do-intune-and-lookout-device-threat-protection-help-protect-company-resources"></a>Hur skyddar Intune och Lookout enhetsskydd företagets resurser?
Lookouts mobilapp (Lookout for work), körs på mobila enheter, avbildar filsystem, nätverksstackar samt telemetri för enheter och program (där det är tillgängligt) och skickar det till molntjänsten Lookout enhetsskydd för att beräkna enhetens sammanställda risk för mobila hot. Du kan även ändra risknivåklassificeringen för hot i Lookout-konsolen så som den passar dig.  

Efterlevnadsprincipen i Intune innehåller nu en ny regel för Lookout mobilt skydd som baseras på riskbedömningen av hot mot enheten som utförts av Lookout. När den här regeln är aktiverad utvärderar Microsoft Intune enhetens efterlevnad med principen som du har aktiverat.

Om enheten utvärderats som inkompatibel med efterlevnadsprincipen kan åtkomst till resurser som Exchange Online och SharePoint Online blockeras med hjälp av principer för villkorlig åtkomst. När åtkomst blockerats får slutanvändare tillgång till en genomgång för att lösa problemet och få tillgång till företagets resurser. Den här genomgången startas via Lookout for work-appen.
## <a name="supported-platforms"></a>Plattformar som stöds:
* **Android 4.1 och senare** och är registrerade i Microsoft Intune.
* **iOS 8 och senare** och är registrerade i Microsoft Intune.
Information om plattformar och språk som har stöd i Lookout finns i denna [artikel](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

## <a name="prerequisites"></a>Krav:
* En prenumeration på Microsoft Intune och Azure Active Directory.
* En Enterprise-prenumeration till Lookout Mobile EndPoint Security.  Se [Lookout Mobile EndPoint Security](https://www.lookout.com/products/mobile-endpoint-security) för mer information

## <a name="example-scenarios"></a>Exempelscenarier
Nedan följer några vanliga scenarier:
### <a name="control-access-based-on-threat-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program:
När skadliga program, till exempel skadlig kod har upptäckts på enheten, kan du blockera sådana enheter från:
* Att ansluta till företagets e-post innan du oskadliggjort hotet.
* Att synkronisera företagets filer med OneDrive för arbetet.
* Att få åtkomst till verksamhetskritiska program.

**Åtkomst som är blockerad när skadliga program upptäcks:**
![diagram som visar en villkorlig åtkomstprincip som blockerar åtkomst när en enhet bedöms vara icke-kompatibel på grund av skadliga appar på enheten](../media/mtp/malicious-apps-blocked.png)

**Enheten avblockeras och kan få tillgång till företagets resurser när hotet är oskadliggjort:**

![diagram som visar hur en princip för villkorlig åtkomst beviljar åtkomst när en enhet bedöms vara kompatibel efter problemet åtgärdats](../media/mtp/malicious-apps-unblocked.png)
### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket:
Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och begränsa åtkomsten till WiFi-nätverk baserat på enhetens risk för angrepp.

**Åtkomst till nätverket via WiFi blockeras:**
![diagram som visar hur villkorlig åtkomst blockerar WiFi-åtkomst baserat på nätverkshot](../media/mtp/network-wifi-blocked.png)

**Åtkomst beviljad när problemet är löst:**

![diagram som visar hur villkorlig åtkomst beviljar åtkomst efter att hotet har oskadliggjorts](../media/mtp/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket:

Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och förhindra synkronisering av företagsfiler baserat på enhetens risk för angrepp.

**Åtkomst till SharePoint Online blockerat baserat på att ett hot mot nätverket har upptäckts på enheten:**

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



<!--HONumber=Dec16_HO2-->


