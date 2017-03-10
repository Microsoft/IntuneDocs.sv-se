---
title: Intune Mobile Threat Defense | Microsoft Docs
description: "Skydda åtkomsten till företagets resurser baserat på enhetsrisk."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08d87906-8158-4d5e-a49d-ad919efef3d1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b7ab3041a38bd394195a67690d245d1ad9fd0566
ms.openlocfilehash: fd54a1c94c9a4a279710d6be9f7cfe3b48468cb7
ms.lasthandoff: 03/03/2017


---

# <a name="intune-mobile-threat-defense-connectors"></a>Intune Mobile Threat Defense-anslutningsprogram

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune Mobile Threat Defense-anslutningsprogram låter dig använda din leverantör av skydd mot mobila hot som informationskälla för efterlevnadsprinciper och regler för villkorlig åtkomst. Det här låter IT-administratörer lägga till ytterligare en skyddsnivå till sina företagsresurser som till exempel Exchange och Sharepoint, särskilt från komprometterade mobila enheter.

## <a name="what-problem-does-this-solve"></a>Vilka problem kan du lösa så här?

Företag behöver skydda känsliga data från nya hot som inkluderar fysiska, app-baserade och nätverksbaserade hot, samt säkerhetsproblem med operativsystem.
Tidigare har företag varit förutseende med att skydda datorer mot angrepp, medan mobila enheter har fått vara oövervakade och oskyddade. Mobila plattformar har ett inbyggt skydd med appisolering och kontrollerade appbutiker för kunder, men dessa plattformar är fortfarande sårbara för sofistikerade attacker. Idag använder många anställda den här typen av enheter för arbete och behöver ha åtkomst till känslig information. Enheter måste skyddas från allt mer sofistikerade attacker.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Hur fungerar Intune Mobile Threat Defense-anslutningsprogram?

Anslutningsprogrammet skyddar företagsresurser genom att skapa en kanal för kommunikation mellan Intune och din valda leverantör av skydd mot mobila hot. Intune Mobile Threat Defense-partner erbjuder intuitiva program som är enkla att distribuera för mobila enheter och som aktivt skannar och analyserar hotbilden mot enheten för information som de sedan delar med Intune i syfte att rapportera eller orsaka åtgärder. Om en ansluten app för skydd mot mobila hot rapporterar till leverantören av skydd mot mobila hot att en telefon i nätverket är ansluten till ett nätverk som är sårbart för man in the middle-angrepp så delas den här informationen och kategoriseras på en lämplig risknivå (låg/medium/hög). Den här risknivån kan sedan jämföras med din konfigurerade tillåtna risknivå i Intune för att avgöra om åtkomst till vissa resurser bör återkallas medan enheten är komprometterad.

## <a name="sample-scenarios"></a>Exempelscenarier

När en enhet betraktas som infekterad av Mobile Threat Defense-lösningen:

![](http://i.imgur.com/kF8tI42.png)

Åtkomst beviljas när enheten åtgärdats:

![](http://i.imgur.com/zG4ZrzX.png)

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense-partner

Lär dig hur du skyddar åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk med:

- [Lookout](https://docs.microsoft.com/intune/deploy-use/lookout-mobile-threat-defense-connector)
