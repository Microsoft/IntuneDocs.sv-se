---
title: IntuneManagementExtension-entitet
titleSuffix: Microsoft Intune
description: Referensavsnitt för kategorin IntuneManagementExtension-entitet för entitetssamlingar i API för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70802626c79f11748e81c39afdd8bc8c5d0622b3
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313779"
---
# <a name="reference-for-intune-management-extensions"></a>Referens för tillägg för Intune-hantering

Kategorin **intuneManagementExtensions** innehåller entiteter för mobila enheter som spårar information, till exempel:

- Versioner av IntuneManagementExtension
- Installationsstatus för IntuneManagementExtension

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

Entiteten **intuneManagementExtensionVersion** visar en lista över alla versioner som används av intuneManagementExtensions.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| extensionVersionKey |Unik identifierare för intuneManagementExtensions-versionen. | 1 |
| extensionVersion |Det fyrsiffriga versionsnumret. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

**intuneManagementExtensionHealthState** visar en lista över alla möjliga hälsotillstånd för intuneManagementExtensions.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| extensionStateKey |Unikt id för hälsotillstånd. | 2 |
| extensionState |Hälsotillståndet för en IntuneManagementExtension. | Felfri |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

**intuneManagementExtension** visar en lista över intuneManagementExtensions-hälsan på varje Windows 10-enhet per dag.
Data bevaras under de senaste 60 dagarna. 


|      Egenskap       |                         Beskrivning                         | Exempel |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               Datumets unika id.                |   123   |
|      tenantKey      |              Klientens unika id.               |   456   |
|      deviceKey      |              Unikt id för enheten.               |   789   |
| extensionVersionKey | Unik identifierare för intuneManagementExtension-versionen. |    1    |
|  extensionStateKey  |             Unikt id för hälsotillstånd.              |    2    |

