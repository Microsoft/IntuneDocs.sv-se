---
title: Mobile Threat Defense med Microsoft Intune
titleSuffix: Microsoft Intune
description: Använd Intune Mobile Threat Defense (MTD) med din Mobile Threat Defense-partner för att skydda åtkomsten till företagsresurser baserat på enhetsrisken.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5329e23ee6307f86c7b1fcaead0cb24b8271443c
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041627"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Vad är Mobile Threat Defense-integrering med Intune?
Intune kan integrera data från en Mobile Threat Defense-leverantör som informationskälla för efterlevnadsprinciper och regler för villkorsstyrd åtkomst. Du kan använda den här informationen för att skydda företagsresurser som Exchange och SharePoint genom att blockera åtkomst från komprometterade mobila enheter.  

## <a name="what-problem-does-this-solve"></a>Vilka problem kan du lösa så här?
Integrering av information från en Mobile Threat Defense-leverantör kan hjälpa dig att skydda företagets resurser från hot som påverkar mobila plattformar.  

Vanligtvis är företag förutseende med att skydda datorer mot sårbarheter och angrepp, medan mobila enheter ofta är oövervakade och oskyddade. I då fall då mobila plattformar har ett inbyggt skydd med appisolering och kontrollerade appbutiker för kunder är dessa plattformar fortfarande sårbara för sofistikerade attacker. Allt eftersom fler anställda använder arbetsenheter och kommer åt känslig information kan information från en Mobile Threat Defense-leverantör hjälpa dig att skydda enheter och resurser från allt mer sofistikerade attacker.  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Hur fungerar Intune Mobile Threat Defense-anslutningsprogram?

Intune använder ett Mobile Threat Defense-anslutningsprogram för att skapa en kanal för kommunikation mellan Intune och din valda Mobile Threat Defense-leverantör. Intune Mobile Threat Defense-partner erbjuder intuitiva program som är enkla att distribuera för mobila enheter. De här programmen skannar och analyserar aktivt information om hot som kan delas med Intune. Intune kan använda data antingen för rapporter eller i syfte att framtvinga principer.  

Exempel: En ansluten Mobile Threat Defense-app rapporterar till Mobile Threat Defense-leverantören att en telefon i nätverket för närvarande är ansluten till ett nätverk som är sårbart för man-i-mitten-attacker. Den här informationen kategoriseras till en lämplig risknivå som låg, medel eller hög. Den här risknivån jämförs sedan med de regler för risknivåer som du anger i Intune. Baserat på den här jämförelsen kan åtkomst till vissa resurser som du väljer återkallas medan enheten är komprometterad.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Vilka data samlar Intune in för skydd mot mobilhot?

Om Intune är aktiverat samlar det in information om appinventering från både personliga och företagsägda enheter och gör den tillgänglig för leverantörer av skydd mot mobilhot (MTD) att hämta, till exempel Lookout for Work. Du kan samla in en appinventering från användare av iOS-enheter.

Den här tjänsten kräver anmälan; som standard delas ingen information om appinventering. En Intune-administratör måste aktivera appsynkronisering för iOS-enheter i tjänstinställningarna innan någon information om appinventering delas.

**Appinventering**  
Om du aktiverar appsynkronisering för iOS-enheter skickas inventeringar från både företagsägda och personligt ägda iOS-enheter till din MTD-tjänstleverantör. Data i appinventeringen omfattar:

 - App-ID
 - Appversion
 - Kort appversion
 - Appnamn
 - Storlek på appsamling
 - Dynamisk appstorlek
 - Oavsett om appen har verifierats eller inte
 - Oavsett om appen hanteras eller inte

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
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- Wandera (information kommer snart)
