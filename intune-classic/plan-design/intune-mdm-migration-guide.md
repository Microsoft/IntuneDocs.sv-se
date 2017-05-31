---
title: "Migreringsguide för Intunes hantering av mobila enheter (MDM) | Microsoft Docs"
description: "Syftet med den här handboken är att guida användarna steg för steg genom processen att migrera från en MDM-tredjepartsleverantör till Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: cce6d997c1aad73819b8cfcf31a1505f0ce75923
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="intune-migration-guide"></a>Migreringsguide för Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

![MDM-migreringsguide för Intune](../media/MDM-migration-guide-art.PNG)

En lyckad migrering till Intune inleds enligt en bestämd plan som omfattar aktuell MDM-miljön, affärsmål och tekniska krav. Du måste dessutom ha viktiga intressenter som stöder och samarbetar kring din migreringsplan.

Syftet med den här handboken är att guida dig steg för steg genom processen att migrera från en MDM-tredjepartsleverantör till Intune.

## <a name="whats-included-in-this-guide"></a>Vad ingår i den här guiden?

Den här handboken omfattar två faser, som båda innehåller uppgifter, strategier och taktiska riktlinjer som hjälper dig att ta dig igenom alla steg i processen med att migrera till Intune MDM.

-   [Fas 1: Förbereda Intune för Hantering av mobila enheter] (/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

    -   [Utvärdera dina MDM-migreringskrav](/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)

    -   [Grundläggande konfiguration](/intune-classic/plan-design/migration-phase1-basic-setup)

    -   [Konfigurera principer för enhets- och apphantering](/intune-classic/plan-design/migration-phase1-configure-device-and-app-management-policies)

    -   [Konfigurera appskyddsprinciper] (/intune-classic/plan-design/migration-phase1-configure-app-protection-policies)

    -   [Särskilda överväganden vid migrering](/intune-classic/plan-design/migration-phase1-special-migration-considerations)

-   [Fas 2: Migreringskampanj](/intune-classic/plan-design/migration-phase2-migration-campaign)

    -   [Kommunikationsplan](/intune-classic/plan-design/migration-phase2-communication-plan)

    -   [Genomför slutanvändarinförande med villkorlig åtkomst](/intune-classic/plan-design/migration-phase2-drive-end-user-adoption-with-conditional-access)
    
    -   [Normal migreringscykel](/intune-classic/plan-design/migration-phase2-typical-migration-cycle)
        -   [Övervaka migrering](/intune-classic/plan-design/migration-phase2-typical-migration-cycle#monitoring-migration)
        -   [Efter migreringen](/intune-classic/plan-design/migration-phase2-typical-migration-cycle#post-migration)

## <a name="assumptions"></a>Antaganden

-   Du har redan utvärderat Intune i en proof of concept-miljö (PoC) och har valt att använda det som MDM-lösning i din organisation.

-   Du är redan bekant med Intune och dess funktioner. 

> [!NOTE]
> Läs [Utvärderingsguide för Intune](/intune-classic/understand-explore/sign-up-for-30-day-trial-microsoft-intune) om du vill lära dig mer om Intune innan du migrerar.

## <a name="before-you-begin"></a>Innan du börjar

Det är viktigt att du är medveten om att den nya Intune-distributionen kan skilja sig från din gamla MDM-distribution. Till skillnad från vanliga MDM-tjänster så fokuserar Intune på identitetsdriven åtkomstkontroll, och kräver därför inte någon nätverksproxy för att kontrollera åtkomsten till företagsdata från mobila enheter utanför företagets nätverksperimeter. Microsoft erbjuder lösningar som skyddar datatjänsterna i molnet genom en uppsättning väl integrerade molntjänster, som tillsammans går under namnet och samlingsnamnet Enterprise Client + Security.

-   Läs avsnittet [Vanliga sätt att använda Intune](/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements).

## <a name="next-steps"></a>Nästa steg

[Fas 1: Förbereda Intune för Hantering av mobila enheter] (/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

