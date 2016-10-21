---
title: "Begränsa åtkomst med mobilt skydd | Microsoft Intune"
description: "Begränsa åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c3cf5e6b32ad24d4972fd147331dda7d2d43e8c6
ms.openlocfilehash: d4eadb73aac14a375f41c434a4303a885bfbae64


---

# Begränsa åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk
Du kan styra åtkomst från mobila enheter till företagsresurser baserat på riskbedömning som utförs av Lookout, en lösning för skydd mot mobila hot (MTP) som är integrerad med Microsoft Intune. Risken är baserad på telemetri som Lookouts MTP-tjänst samlar in från enheter för säkerhetsproblem med operativsystem (OS), installerade skadliga appar och nätverksprofiler. Du kan konfigurera principer för villkorlig åtkomst i Intune baserat på riskbedömning och tillåta eller blockera enheter som har visats vara inkompatibla på grund av hot som identifieras på enheterna.  För tillfället stöds detta endast för **Android**-enheter som kör **4.1 och senare** och som är registrerade i Microsoft Intune.  
## Vilka problem kan du lösa så här?
Företag och organisationer behöver skydda känsliga data från nya hot som inkluderar fysiska, app-baserade och nätverksbaserade hot, samt säkerhetsproblem med operativsystem.

Företag och organisationer har tidigare tagit en aktiv roll för att skydda datorer mot skadliga angrepp. Mobila tjänster är ett nytt område som ofta förblir oskyddade. Även om de mobila plattformarna har ett inbyggt skydd för operativsystemet med tekniker som appisolering och kontrollerade appbutiker för kunder är dessa plattformar fortfarande sårbara för sofistikerade attacker. Eftersom mobila enheter används mer och mer av anställda för att utföra arbete och de behöver åtkomst till information som kan vara känslig och värdefull måste dessa enheter skyddas från en mängd olika sofistikerade attacker.

Intune gör det möjligt att kontrollera åtkomst till företagets resurser och data baserat på riskbedömning som MTP-lösningar som Lookout tillhandahåller.

## Hur skyddar Intune och Lookout mobilt skydd företagets resurser?
Lookouts mobilapp (Lookout for work), körs på mobila enheter, avbildar filsystem, nätverksstackar samt telemetri för enheter och program (där det är tillgängligt) och skickar det till (MTP)-molntjänsten Lookout mobilt skydd för att beräkna enhetens sammanställda risk för mobila hot. Du kan även ändra risknivåklassificeringen för hot i MTP-konsolen så som den passar dig.  
Efterlevnadsprincipen i Intune innehåller nu en ny regel för Lookout mobilt skydd som baseras på riskbedömningen som utförts av Lookout MTP. När den här regeln är aktiverad utvärderar Microsoft Intune enhetens efterlevnad med principen som du har aktiverat.

Om enheten utvärderats som inkompatibel med efterlevnadsprincipen kan åtkomst till resurser som Exchange Online och SharePoint Online blockeras med hjälp av principer för villkorlig åtkomst. När åtkomst blockerats får slutanvändare tillgång till en genomgång för att lösa problemet och få tillgång till företagets resurser. Den här genomgången startas via Lookout for work-appen.

## Exempelscenarier
Nedan följer några vanliga scenarier:
### Hot från skadliga program:
När skadliga program, till exempel skadlig kod har upptäckts på enheten, kan du blockera sådana enheter från:
* Att ansluta till företagets e-post innan du oskadliggjort hotet.
* Att synkronisera företagets filer med OneDrive för arbetet.
* Att få åtkomst till verksamhetskritiska program.

**Åtkomst som är blockerad när skadliga program upptäcks:**
![diagram som visar en villkorlig åtkomstprincip som blockerar åtkomst när en enhet bedöms vara icke-kompatibel på grund av skadliga appar på enheten](../media/mtp/malicious-apps-blocked.png)

**Enheten avblockeras och kan få tillgång till företagets resurser när hotet är oskadliggjort:**

![diagram som visar hur en princip för villkorlig åtkomst beviljar åtkomst när en enhet bedöms vara kompatibel efter problemet åtgärdats](../media/mtp/malicious-apps-unblocked.png)
### Hot mot nätverket:
Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och begränsa åtkomsten till WiFi-nätverk baserat på enhetens risk för angrepp.

**Åtkomst till nätverket via WiFi blockeras:**
![diagram som visar hur villkorlig åtkomst blockerar WiFi-åtkomst baserat på nätverkshot](../media/mtp/network-wifi-blocked.png)

**Åtkomst beviljad efter problemet är löst:**

![diagram som visar hur villkorlig åtkomst beviljar åtkomst efter att hotet har oskadliggjorts](../media/mtp/network-wifi-unblocked.png)
### Hot mot nätverket (förhindra åtkomst till SharePoint Online):

Identifiera hot mot ditt nätverk, till exempel man-in-the-middle-angrepp, och förhindra synkronisering av företagsfiler baserat på enhetens risk för angrepp.

**Åtkomst till SharePoint Online blockerat baserat på att ett hot mot nätverket har upptäckts på enheten:**

![Diagram som visar hur villkorlig åtkomst blockerar enheter från att få åtkomst till SharePoint Online baserat på identifiering av hot](../media/mtp/network-spo-blocked.png)


**Åtkomst beviljad efter problemet är löst:**

![Diagram som visar hur villkorlig åtkomst beviljar åtkomst efter att hotet har oskadliggjorts](../media/mtp/network-spo-unblocked.png)

## Nästa steg
Här följer de åtgärder du måste utföra för att implementera den här lösningen:
1.  [Konfigurera din prenumeration med Lookout mobilt skydd](set-up-your-subscription-with-lookout-mtp.md)
2.  [Aktivera anslutning till Lookout MTP i Intune](enable-lookout-mtp-connection-in-intune.md)
3.  [Konfigurera och distribuera Lookout for work-appen](configure-and-deploy-lookout-for-work-apps.md)
4.  [Konfigurera efterlevnadsprincipen](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Felsöka Lookout-integrering](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)



<!--HONumber=Sep16_HO3-->


