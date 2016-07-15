---
title: Konceptbevis | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f3c97380-23ca-40da-acbc-78108507cad7
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d82d0ae4820d2e2141848235b8741abccaec3bc6
ms.openlocfilehash: 4c01b7cec6474153fcea465fc050ac419ca2eec5


---

# Konceptbevis
Konceptbevisfasen bör fokusera på att fastställa distributionens möjligheter att uppfylla företagets krav. Den här fasen innehåller en enkel topologi som designats för att verifiera specifika tekniska scenarier.  Distributionen bör vara i en testmiljö och bör inte vara värd för några produktionsanvändare.

## Varför är detta viktigt?
Ett konceptbevis är viktigt för att förstå distributionens genomförbarhet innan du går vidare till pilotanvändare. Det bör ses som ett experiment i liten skala där du får lära dig hur Microsoft Intune fungerar i din miljö. Det bör också verifiera specifika scenarier innan du investerar i de resurser som krävs för en pilot. Erfarenheterna från konceptbeviset bör påverka pilot- och produktionsdesignen.
Börja med att gå igenom identifieringsfrågorna, som hjälper dig att fastställa omfånget och definiera konceptbeviset.

## Identifieringsfrågor
Diskutera dessa frågor med projektgruppen för att fastställa omfånget av projektinformationen, avslöja möjliga risker och definiera aktiviteter som går att utföra.

-   Vilka centrala scenarier måste Intune uppfylla för att tillgodose organisationens behov inom enhetshantering?

-   Vilka funktioner vill du undersöka och verifiera?

-   Vilka resurser måste du ha i testmiljön för att slutföra verifieringen av dessa scenarier?

## Mål för fokusområde
Gå igenom det här avsnittet för att få vägledning om fokusområdesaktiviteter för den här fasen av distributionen.

### Planering
Du måste känna till de scenarier som du behöver verifiera, och vad du behöver för att slutföra den här verifieringen, innan du distribuerar konceptbevisinfrastrukturen.

### Supportavdelningen
Supportavdelningen behöver inte förberedelser inför den här fasen i projektet eftersom den inte omfattar några produktionsanvändare eller enheter. Det är dock en möjlighet för supportavdelningen att lära sig mer om distributionen och hanteringen av Intune.

### Medvetenhet
Det tekniska teamet och finansiären från ledningen bör ha inblick i förloppet för scenariotestning. Designteamet måste vara medvetna om erfarenheterna som ska tas med i designen.

### Utbildning
Administratörer som kommer att hantera användare, enheter, principer och program bör utnyttja konceptbeviset som en möjlighet att lära sig mer om Intune-konsolen och -funktionerna.

### Åtgärder
Konceptbeviset kräver inte kontinuerliga åtgärder. Det kan dock finnas specifika scenarier som åtgärdspersonal bör förstå eller verifiera i konceptbeviset.

## Checklista för att komma igång
Följande är en lista över steg som hjälper dig att komma igång med **konceptbevis**fasen.

-   Definiera framgångskriterierna för konceptbeviset. Dessa bör vara baserade på verifiering av affärsmässiga och tekniska krav.

-   Identifiera de resurser som krävs för att verifiera testscenarier.

-   Identifiera lämpliga testmiljöer som efterliknar produktionsmiljön, till exempel det antal enheter med olika operativsystem som krävs.

## Vanliga utmaningar
Följande är några utmaningar som du kan stöta på i **konceptbevis**fasen.

-   **Utmaning:** Få tekniska resurser och personal för att verifiera produktionsliknande scenarier.

    **Lösning:** Förklara tydligt att erfarenheterna i PoC-miljön underlättar den tekniska designen och förbättrar kvaliteten på de efterföljande faserna. Brist på resurser för konceptbeviset kräver att dessa erfarenheter fås efter att den tekniska designen har slutförts – vilket kan kräva ändrad design av vissa element.

-   **Utmaning:** Definiera de testscenarier som krävs i produktion.

    **Lösning:** Arbeta med finansiären från ledningen, nätverket och användarteamen för att förstå kraven på en klienthanteringslösning.

### Nästa steg
[Pilot](pilot.md)



<!--HONumber=Jun16_HO4-->


