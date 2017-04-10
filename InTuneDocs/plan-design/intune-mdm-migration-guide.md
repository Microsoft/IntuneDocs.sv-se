---
title: "Migreringsguide för Intunes hantering av mobila enheter (MDM) | Microsoft Docs"
description: "Syftet med den här handboken är att guida användarna steg för steg genom processen att migrera från en MDM-tredjepartsleverantör till Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8da2695c4c6dc8b45559323b83a4bb77167303b7
ms.openlocfilehash: 444cb61ea57b92924a681c564a1a913f4204ea89
ms.lasthandoff: 03/28/2017


---

# <a name="intune-migration-guide"></a>Migreringsguide för Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

![MDM-migreringsguide för Intune](../media/MDM-migration-guide-art.PNG)

En lyckad migrering till Intune inleds enligt en bestämd plan som omfattar aktuell MDM-miljön, affärsmål och tekniska krav. Du måste dessutom ha viktiga intressenter som stöder och samarbetar kring din migreringsplan.

Syftet med den här handboken är att guida dig steg för steg genom processen att migrera från en MDM-tredjepartsleverantör till Intune.

## <a name="whats-included-in-this-guide"></a>Vad ingår i den här guiden?

Den här handboken omfattar två faser, som båda innehåller uppgifter, strategier och taktiska riktlinjer som hjälper dig att ta dig igenom alla steg i processen med att migrera till Intune MDM.

-   [Fas 1: Förbered Intune för hantering av mobila enheter (MDM)](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

    -   [Utvärdera dina MDM-migreringskrav](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)

    -   [Grundläggande konfiguration](https://docs.microsoft.com/intune/plan-design/migration-phase1-basic-setup)

    -   [Konfigurera principer för enhets- och apphantering](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-device-and-app-management-policies)

    -   [Konfigurera appskyddsprinciper (valfritt)](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-app-protection-policies)

    -   [Särskilda överväganden vid migrering](https://docs.microsoft.com/intune/plan-design/migration-phase1-special-migration-considerations)

-   [Fas 2: Migreringskampanj](https://docs.microsoft.com/intune/plan-design/migration-phase2-migration-campaign)

    -   [Kommunikationsplan](https://docs.microsoft.com/intune/plan-design/migration-phase2-communication-plan)

    -   [Genomför slutanvändarinförande med villkorlig åtkomst](https://docs.microsoft.com/intune/plan-design/migration-phase2-drive-end-user-adoption-with-conditional-access)
    
    -   [Normal migreringscykel](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle)
        -   [Övervaka migrering](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle#monitoring-migration)
        -   [Efter migreringen](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle#post-migration)

## <a name="assumptions"></a>Antaganden

-   Du har redan utvärderat Intune i en proof of concept-miljö (PoC) och har valt att använda det som MDM-lösning i din organisation.

-   Du är redan bekant med Intune och dess funktioner. 

> [!NOTE]
> Läs [Utvärderingsguide för Intune](https://docs.microsoft.com/intune/understand-explore/sign-up-for-30-day-trial-microsoft-intune) om du vill lära dig mer om Intune innan du migrerar.

## <a name="before-you-begin"></a>Innan du börjar

Det är viktigt att du är medveten om att den nya Intune-distributionen kan skilja sig från din gamla MDM-distribution. Till skillnad från vanliga MDM-tjänster så fokuserar Intune på identitetsdriven åtkomstkontroll, och kräver därför inte någon nätverksproxy för att kontrollera åtkomsten till företagsdata från mobila enheter utanför företagets nätverksperimeter. Microsoft erbjuder lösningar som skyddar datatjänsterna i molnet genom en uppsättning väl integrerade molntjänster, som tillsammans går under namnet och samlingsnamnet Enterprise Client + Security.

-   Läs om [olika sätt att använda Intune](https://docs.microsoft.com/intune/understand-explore/common-ways-to-use-intune) och börja sammanställa svar på frågorna under [Fas 1: Utvärdera MDM-krav](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements).

## <a name="next-steps"></a>Nästa steg

[Fas 1: Förbered Intune för hantering av mobila enheter (MDM)](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

