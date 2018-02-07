---
title: "Migreringsguide för hantering av mobila enheter"
description: "Den här guiden leder dig genom de olika stegen för att migrera från en MDM-leverantör från tredje part till Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 888624530fe77f22ea9391b688fa9f9b92f0ac75
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="intune-migration-guide"></a>Migreringsguide för Intune

![MDM-migreringsguide för Intune](./media/MDM-migration-guide-art.PNG)

En lyckad migrering till Intune börjar med en bestämd plan som omfattar aktuell miljö för hantering av mobilenheter, affärsmål och tekniska krav. Du måste dessutom ha viktiga intressenter som stöder och samarbetar kring din migreringsplan.

Den här guiden leder dig genom de olika stegen för att migrera från en MDM-leverantör från tredje part till Intune.

## <a name="whats-included-in-this-guide"></a>Vad ingår i den här guiden?

Den här guiden delar in migreringen i två faser, som båda innehåller uppgifter, strategier och taktiska riktlinjer som hjälper dig att ta dig igenom alla steg i processen med att migrera till Intune MDM.

-   [Fas 1: Förbereda Intune för hantering av mobila enheter](migration-guide-prepare.md)

    -   [Utvärdera dina MDM-migreringskrav](migration-guide-prepare.md#assess-mdm-requirements)

    -   [Grundläggande konfiguration](migration-guide-setup.md)

    -   [Konfigurera principer för enhets- och apphantering](migration-guide-configure-policies.md)

    -   [Konfigurera appskyddsprinciper](migration-guide-app-protection-policies.md)

    -   [Särskilda överväganden vid migrering](migration-guide-considerations.md)

-   [Steg 2: Migreringskampanjen](migration-guide-campaign.md)

    -   [Kommunikationsplan](migration-guide-communication-plan.md)

    -   [Genomför slutanvändarinförande med villkorlig åtkomst](migration-guide-drive-adoption.md)

    -   [Typisk migreringscykel](migration-guide-cycle.md)
        -   [Övervaka migrering](migration-guide-cycle.md#monitoring-migration)
        -   [Efter migreringen](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>Antaganden

-   Du har redan utvärderat Intune i en proof of concept-miljö (PoC) och har valt att använda det som MDM-lösning i din organisation.

-   Du är redan bekant med Intune och dess funktioner.

## <a name="before-you-begin"></a>Innan du börjar

Det är viktigt att du är medveten om att den nya Intune-distributionen kan skilja sig från din gamla MDM-distribution. Till skillnad från vanliga MDM-tjänster så fokuserar Intune på identitetsdriven åtkomstkontroll, och kräver därför inte någon nätverksproxy för att kontrollera åtkomsten till företagsdata från mobila enheter utanför företagets nätverksperimeter. Microsoft erbjuder lösningar som skyddar datatjänster i molnet genom en uppsättning väl integrerade molntjänster, som tillsammans kallas Enterprise Client + Security.

-   Läs avsnittet [Vanliga sätt att använda Intune](common-scenarios.md).

## <a name="next-steps"></a>Nästa steg

[Fas 1: Förbereda Intune för hantering av mobila enheter](migration-guide-prepare.md)
