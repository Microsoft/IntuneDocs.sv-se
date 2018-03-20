---
title: "Identifiera scenarion för användningsfall"
titlesuffix: Microsoft Intune
description: "Den här artikeln hjälper till att identifiera krav för Intune-användningsfall och underanvändningsfall för en Microsoft Intune-molnimplementering."
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ef2030ba36e7a2c5f1a9566a2fcb94ecca465149
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/17/2018
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>Identifiera hantering av mobila enheter för användningsscenarier

Att identifiera användningsfallen är en viktig del av planeringsprocessen för att lyckas med Intune-distributionen. Användningsscenarier är användbara eftersom de hjälper dig att segmentera dina användare i hanterbara grupper efter användartyp eller roll, eller ägarskapet för användarens enhet (om den t.ex. tillhör företaget eller personen).

Vi ska nu ta upp några exempel som hjälper din organisation att identifiera användningsfall för Intune, samt organisationsgrupper och mobila enhetsplattformar som är kopplade till varje användningsfall.

## <a name="device-ownership"></a>Äganderätt till enhet
Du kan börja med att titta på organisationens mål och delmål för Intune-distributionen för att få hjälp att identifiera de främsta användningsfallen för distributionen. Inom omfattningen för Intune-distributionsplanen måste du besvara följande frågor:

-   Planerar du att ha stöd för företagsägda enheter?

-   Planerar du att ha stöd för personligt ägda enheter (BYOD)?

Dessa är inte antingen/eller-alternativ. Du kanske inser att du behöver stödja båda typerna av ägarskap för att organisationens mål ska kunna uppfyllas. Med underanvändningsfall kan du tydliggöra var de olika principerna för enhetshantering ska tillämpas.

### <a name="user-type-or-device-role"></a>Användartyp eller enhetsroll

Fastställ om varje användningsfallsscenario omfattar underanvändningsfall. En organisation kan t.ex. ha identifierat krav för att stödja ett företagsanvändningsfall som också omfattar ytterligare underanvändningsfall baserade på användartyp eller enhetsroll, t.ex.:

-   Informationsarbetare

-   Chef

-   Helskärmsläge

Här följer några exempel på användningsfall och underanvändningsfall:

| **Användningsfall** | **Underanvändningsfall** |
|:---:|:---:|
| Företag | Informationsarbetare |              
| Företag | Chefer |           
| Företag | Helskärmsläge |
| BYOD | Informationsarbetare |           
| BYOD | Chefer |

Du kan [ladda ned en mall för ovanstående tabell](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) där du kan ange din organisations scenarier för användningsfall och underanvändningsfall.

## <a name="organizational-groups-for-your-scenarios"></a>Organisationsgrupper för dina scenarier

Du måste nu identifiera de organisationsgrupper som är kopplade till varje användningsfall och underanvändningsfall. Exempel:

| **Användningsfall** | **Underanvändningsfall** | **Organisationsgrupper** |
|:---:|:---:|:---:|
| Företag | Informationsarbetare | Personalavdelning, ekonomi |               
| Företag | Chef | Personalavdelning, ekonomi |            
| Företag | Helskärmsläge | Återförsäljning |
| BYOD | Informationsarbetare | Marknadsföring, försäljning |            
| BYOD | Chef | Marknadsföring, försäljning |


## <a name="mobile-device-platforms-for-your-scenarios"></a>Mobila enhetsplattformar för dina scenarier

Nästa steg är att identifiera de mobila enhetsplattformar som är kopplade till respektive användningsfall. Det kan finnas mer än en.

Ditt fallscenario för företagsanvändning stöder kanske iOS- och Android Samsung Knox-enhetsplattformar. Din BYOD-princip kan innehålla stöd för ytterligare plattformar för mobila enheter, t.ex. Android (inte Samsung Knox) och Windows 10 Mobile. Utifrån föregående exempel har vi kopplat plattformar för mobila enheter till respektive användningsfallsscenario.

| **Användningsfall** | **Underanvändningsfall** | **Grupper** | **Enhetsplattformar** |   
|:---:|:---:|:---:|:---:|
| Företag | Informationsarbetare | Personalavdelning, ekonomi | iOS |                                                           
| Företag | Chefer | Personalavdelning, ekonomi | iOS |                                                           
| Företag | Helskärmsläge | Återförsäljning | Android |
| BYOD | Informationsarbetare | Marknadsföring, försäljning | iOS |                                                           
| BYOD | Chefer | Marknadsföring, försäljning | iOS |

## <a name="next-steps"></a>Nästa steg

Nästa avsnitt innehåller råd om att [identifiera Intune-kraven för varje användningsfall](planning-guide-requirements.md).
