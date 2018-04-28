---
title: Mobile Threat Defense med Microsoft Intune
titleSuffix: ''
description: Använd Intune Mobile Threat Defense (MTD) med din Mobile Threat Defense-partner för att skydda åtkomsten till företagsresurser baserat på enhetsrisken.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 11/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d840bf62682621e4ec3848538a96066c0fd228fe
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2018
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Vad är Mobile Threat Defense-integrering med Intune?


Intune Mobile Threat Defense-anslutningsprogram låter dig använda din leverantör av skydd mot mobila hot som informationskälla för efterlevnadsprinciper och regler för villkorlig åtkomst. Det här gör det möjligt för IT-administratörer att lägga till ytterligare en skyddsnivå i sina företagsresurser, till exempel Exchange och Sharepoint, särskilt från komprometterade mobila enheter.

## <a name="what-problem-does-this-solve"></a>Vilka problem kan du lösa så här?

Företag behöver skydda känsliga data från nya hot som inkluderar fysiska, app-baserade och nätverksbaserade hot, samt säkerhetsproblem med operativsystem.

Tidigare har företag varit förutseende med att skydda datorer mot angrepp, medan mobila enheter har fått vara oövervakade och oskyddade. Mobila plattformar har ett inbyggt skydd med appisolering och kontrollerade appbutiker för kunder, men dessa plattformar är fortfarande sårbara för sofistikerade attacker. Idag använder många anställda den här typen av enheter för arbete och behöver ha åtkomst till känslig information. Enheter måste skyddas från allt mer sofistikerade attacker.

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Hur fungerar Intune Mobile Threat Defense-anslutningsprogram?

Anslutningsprogrammet skyddar företagsresurser genom att skapa en kanal för kommunikation mellan Intune och din valda leverantör av skydd mot mobila hot. Intune Mobile Threat Defense-partner erbjuder intuitiva program som är enkla att distribuera för mobila enheter och som aktivt skannar och analyserar hotbilden mot enheten för information som de sedan delar med Intune i syfte att rapportera eller orsaka åtgärder. 

Om en ansluten app för skydd mot mobila hot rapporterar till leverantören av skydd mot mobila hot att en telefon i nätverket är ansluten till ett nätverk som är sårbart för man in the middle-angrepp så delas den här informationen och kategoriseras på en lämplig risknivå (låg/medium/hög). Den här risknivån kan sedan jämföras med din konfigurerade tillåtna risknivå i Intune för att avgöra om åtkomst till vissa resurser bör återkallas medan enheten är komprometterad.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Vilka data samlar Intune in för skydd mot mobilhot?

Intune samlar in information om appinventering från både personliga och företagsägda enheter och gör den tillgänglig för leverantörer av skydd mot mobilhot (MTD) att hämta, till exempel Lookout for Work. Du kan samla in en appinventering från användare av enheter med iOS 11+.

**Appinventering**  
Inventeringar från både företagsägda iOS 11+ och personligt ägda enheter skickas till MTD-leverantören. Data i appinventeringen omfattar:

 - App-ID
 - Appversion
 - Kort appversion
 - Appnamn
 - Storlek på appsamling
 - Dynamisk appstorlek
 - Om appen har verifierats eller inte
 - Om appen är hanterad eller inte

## <a name="sample-scenarios"></a>Exempelscenarier

När en enhet betraktas som infekterad av Mobile Threat Defense-lösningen:

![Bild på en infekterad enhet enligt Mobile Threat Defense](./media/MTD-image-1.png)

Åtkomst beviljas när enheten åtgärdats:

![Bild på åtkomst beviljad av Mobile Threat Defense](./media/MTD-image-2.png)

> [!NOTE] 
> Användning av flera leverantörer för Mobile Threat Defense med Intune stöds inte. Om flera MTD-verktyg är aktiverade måste alla MTD-appar installeras och genomsöka enheterna beträffande hot.

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense-partner

Lär dig hur du skyddar åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk med:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
