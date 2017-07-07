---
title: "Migreringsguide för hantering av mobila enheter"
description: "Syftet med den här handboken är att guida användarna steg för steg genom processen att migrera från en MDM-tredjepartsleverantör till Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9e86f342413a0f31c51d7a56f862986c433309eb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="intune-migration-guide"></a>Migreringsguide för Intune

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

![MDM-migreringsguide för Intune](./media/MDM-migration-guide-art.PNG)

En lyckad migrering till Intune inleds enligt en bestämd plan som omfattar aktuell miljö för hantering av mobilenheter, affärsmål och tekniska krav. Du måste dessutom ha viktiga intressenter som stöder och samarbetar kring din migreringsplan.

Syftet med den här handboken är att guida dig steg för steg genom processen att migrera från en MDM-tredjepartsleverantör till Intune.

## <a name="whats-included-in-this-guide"></a>Vad ingår i den här guiden?

Den här handboken omfattar två faser, som båda innehåller uppgifter, strategier och taktiska riktlinjer som hjälper dig att ta dig igenom alla steg i processen med att migrera till Intune MDM.

-   [Fas 1: Förbered Intune för hantering av mobila enheter] (migration-guide-prepare.md)

    -   [Utvärdera dina MDM-migreringskrav](migration-guide-prepare.md#assess-mdm-requirements)

    -   [Grundläggande konfiguration](migration-guide-setup.md)

    -   [Konfigurera principer för enhets- och apphantering](migration-guide-configure-policies.md)

    -   [Konfigurera appskyddsprinciper] (migration-guide-app-protection-policies.md)

    -   [Särskilda överväganden vid migrering](migration-guide-considerations.md)

-   [Fas 2: Migreringskampanj](migration-guide-campaign.md)

    -   [Kommunikationsplan](migration-guide-communication-plan.md)

    -   [Genomför slutanvändarinförande med villkorlig åtkomst](migration-guide-drive-adoption.md)
    
    -   [Normal migreringscykel](migration-guide-cycle.md)
        -   [Övervaka migrering](migration-guide-cycle.md#monitoring-migration)
        -   [Efter migreringen](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>Antaganden

-   Du har redan utvärderat Intune i en proof of concept-miljö (PoC) och har valt att använda det som MDM-lösning i din organisation.

-   Du är redan bekant med Intune och dess funktioner. 

> [!NOTE]
> Läs [Utvärderingsguide för Intune](/intune-classic/understand-explore/sign-up-for-30-day-trial-microsoft-intune) om du vill lära dig mer om Intune innan du migrerar.

## <a name="before-you-begin"></a>Innan du börjar

Det är viktigt att du är medveten om att den nya Intune-distributionen kan skilja sig från din gamla MDM-distribution. Till skillnad från vanliga MDM-tjänster så fokuserar Intune på identitetsdriven åtkomstkontroll, och kräver därför inte någon nätverksproxy för att kontrollera åtkomsten till företagsdata från mobila enheter utanför företagets nätverksperimeter. Microsoft erbjuder lösningar som skyddar datatjänsterna i molnet genom en uppsättning väl integrerade molntjänster, som tillsammans går under namnet och samlingsnamnet Enterprise Client + Security.

-   Läs avsnittet [Vanliga sätt att använda Intune](migration-guide-prepare.md#assess-mdm-requirements).

## <a name="next-steps"></a>Nästa steg

[Fas 1: Förbered Intune för hantering av mobila enheter] (migration-guide-prepare.md)
