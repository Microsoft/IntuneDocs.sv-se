---
title: "Identifiera användningsfall i Intune | Microsoft Docs"
description: "Den här artikeln hjälper till att identifiera krav för Intune-användningsfall och underfall för en Microsoft Intune-molnimplementering."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 3c5744e7c1290bf9016bc03dcb2db9a1bd9f43dd
ms.openlocfilehash: 031820d505e0e9cb007e47a5397934d0e505aed4
ms.lasthandoff: 04/10/2017


---

# <a name="identify-intune-use-case-scenarios"></a>Identifiera användningsfall i Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Användningsfall för hantering av mobila enheter beskriver användartypen eller rollen och enhetens ägande (t.ex. företagsägd eller personlig). Användningsfall är till hjälp eftersom de gör det möjligt att dela upp användarna i hanterbara grupper. Att identifiera användningsfallen är en viktig del av planeringsprocessen för att lyckas med Intune-distributionen.

Vi ska nu ta upp några exempel som hjälper din organisation att identifiera användningsfall för Intune, samt organisationsgrupper och mobila enhetsplattformar som är kopplade till varje användningsfall.

## <a name="use-case-scenarios"></a>Användningsfall

Du kan börja med att titta på organisationens mål och delmål för Intune-distributionen för att få hjälp att identifiera de främsta användningsfallen för distributionen. Inom omfattningen för Intune-distributionsplanen måste du besvara följande frågor:

-   Planerar du att ha stöd för företagsägda enheter?

-   Planerar du att ha stöd för personligt ägda enheter (BYOD)?

### <a name="sub-use-case-scenarios"></a>Underanvändningsfall

När du har identifierat de viktigaste användningsfallen måste du fastställa om varje användningsfall även omfattar underfall. En organisation kan till exempel ha identifierat krav för att stödja ett företagsanvändningsfall som också omfattar ytterligare underanvändningsfall:

-   Informationsarbetare

-   Chefer

-   Helskärmsläge

Följande är några exempel på användningsfall och underanvändningsfall. Du kan använda tabellen nedan för att ange din organisations användningsfall och underanvändningsfall:

| **Användningsfall** | **Underanvändningsfall** |
|:---:|:---:|
| Företag | Informationsarbetare |              
| Företag | Chefer |           
| Företag | Helskärmsläge |
| BYOD | Informationsarbetare |           
| BYOD | Chefer |

## <a name="identify-organizational-groups-associated-with-use-case-scenarios"></a>Identifiera organisationsgrupper som är kopplade till användningsfall

Du måste nu identifiera de organisationsgrupper som är kopplade till varje användningsfall och underanvändningsfall. Följande är några exempel på organisationsgrupper som är kopplade till användningsfall och underanvändningsfall som kan användas som mall för att ange organisationens information:

| **Användningsfall** | **Underanvändningsfall** | **Organisationsgrupper** |
|:---:|:---:|:---:|
| Företag | Informationsarbetare | Personalavdelning, ekonomi |               
| Företag | Chef | Personalavdelning, ekonomi |            
| Företag | Helskärmsläge | Återförsäljning |
| BYOD | Informationsarbetare | Marknadsföring, försäljning |            
| BYOD | Chef | Marknadsföring, försäljning |

## <a name="identify-mobile-device-platforms-for-use-case-scenarios"></a>Identifiera mobila enhetsplattformar för användningsfall

Här identifierar du de mobila enhetsplattformar som är kopplade till varje användningsfall. Företagsanvändningsfallet kan till exempel ha stöd för enhetsplattformarna iOS och Android Samsung KNOX, och BYOD-principen kan omfatta stöd för ytterligare mobila enhetsplattformar som Android (inte Samsung KNOX) och Windows 10 Mobile. Följande är ett exempel på mobila enhetsplattformar som är kopplade till varje användningsfall. Du kan använda tabellen nedan för att ange organisationens enhetsplattformar som är kopplade till dess användningsfall:

| **Användningsfall** | **Underanvändningsfall** | **Grupper** | **Enhetsplattformar** |   
|:---:|:---:|:---:|:---:|
| Företag | Informationsarbetare | Personalavdelning, ekonomi | iOS |                                                           
| Företag | Chefer | Personalavdelning, ekonomi | iOS |                                                           
| Företag | Helskärmsläge | Återförsäljning | Android |
| BYOD | Informationsarbetare | Marknadsföring, försäljning | iOS |                                                           
| BYOD | Chefer | Marknadsföring, försäljning | iOS |

## <a name="next-steps"></a>Nästa steg

Nästa avsnitt innehåller råd om att [identifiera Intune-kraven för varje användningsfall](section-3-determine-use-case-requirements.md).

