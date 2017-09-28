---
title: Mobile Threat Defense med Intune
titleSuffix: Azure portal
description: "Skydda åtkomsten till företagets resurser baserat på enhetsrisk"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 52125f78ae8d0633f53002cb1507c615a327ee8b
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/19/2017
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Mobile Threat Defense-integrering med Intune


Intune Mobile Threat Defense-anslutningsprogram låter dig använda din leverantör av skydd mot mobila hot som informationskälla för efterlevnadsprinciper och regler för villkorlig åtkomst. Det här låter IT-administratörer lägga till ytterligare en skyddsnivå till sina företagsresurser som till exempel Exchange och Sharepoint, särskilt från komprometterade mobila enheter.

## <a name="what-problem-does-this-solve"></a>Vilka problem kan du lösa så här?

Företag behöver skydda känsliga data från nya hot som inkluderar fysiska, app-baserade och nätverksbaserade hot, samt säkerhetsproblem med operativsystem.
Tidigare har företag varit förutseende med att skydda datorer mot angrepp, medan mobila enheter har fått vara oövervakade och oskyddade. Mobila plattformar har ett inbyggt skydd med appisolering och kontrollerade appbutiker för kunder, men dessa plattformar är fortfarande sårbara för sofistikerade attacker. Idag använder många anställda den här typen av enheter för arbete och behöver ha åtkomst till känslig information. Enheter måste skyddas från allt mer sofistikerade attacker.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Hur fungerar Intune Mobile Threat Defense-anslutningsprogram?

Anslutningsprogrammet skyddar företagsresurser genom att skapa en kanal för kommunikation mellan Intune och din valda leverantör av skydd mot mobila hot. Intune Mobile Threat Defense-partner erbjuder intuitiva program som är enkla att distribuera för mobila enheter och som aktivt skannar och analyserar hotbilden mot enheten för information som de sedan delar med Intune i syfte att rapportera eller orsaka åtgärder. Om en ansluten app för skydd mot mobila hot rapporterar till leverantören av skydd mot mobila hot att en telefon i nätverket är ansluten till ett nätverk som är sårbart för man in the middle-angrepp så delas den här informationen och kategoriseras på en lämplig risknivå (låg/medium/hög). Den här risknivån kan sedan jämföras med din konfigurerade tillåtna risknivå i Intune för att avgöra om åtkomst till vissa resurser bör återkallas medan enheten är komprometterad.

## <a name="sample-scenarios"></a>Exempelscenarier

När en enhet betraktas som infekterad av Mobile Threat Defense-lösningen:

![Mobile Threat Defense-infekterad enhet](./media/MTD-image-1.png)

Åtkomst beviljas när enheten åtgärdats:

![Mobile Threat Defense-åtkomst har beviljats](./media/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense-partner

Lär dig hur du skyddar åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk med:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Skycure](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)