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
ms.openlocfilehash: 934742108effda0a88f4bcc42e06daa12c55288c
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648844"
---
# <a name="reference-for-intune-management-extension"></a>Referens för tillägg för Intune-hantering

Kategorin **IntuneManagementExtension** innehåller entiteter för mobila enheter som spårar information, till exempel:

  - Versioner av IntuneManagementExtension
  - Installationsstatus för IntuneManagementExtension

## <a name="intunemanagementextensionversion"></a>IntuneManagementExtensionVersion

Entiteten **IntuneManagementExtensionVersion** visar alla versioner som används av IntuneManagementExtension.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| ExtensionVersionKey |Unik identifierare för IntuneManagementExtension-versionen. | 1 |
| ExtensionVersion |Det fyrsiffriga versionsnumret. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstate"></a>IntuneManagementExtensionHealthState

**IntuneManagementExtensionHealthState** visar en lista över alla möjliga hälsotillstånd för IntuneManagementExtension.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| ExtensionStateKey |Unikt id för hälsotillstånd. | 2 |
| ExtensionState |Hälsotillståndet för en IntuneManagementExtension. | Felfri |

## <a name="intunemanagementextension"></a>IntuneManagementExtension

**IntuneManagementExtension** visar en lista över hälsa för IntuneManagementExtension för varje Windows 10-enhet per dag.
Data bevaras under de senaste 60 dagarna. 


|      Egenskap       |                         Beskrivning                         | Exempel |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               Datumets unika id.                |   123   |
|      TenantKey      |              Klientens unika id.               |   456   |
|      DeviceKey      |              Unikt id för enheten.               |   789   |
| ExtensionVersionKey | Unik identifierare för IntuneManagementExtension-versionen. |    1    |
|  ExtensionStateKey  |             Unikt id för hälsotillstånd.              |    2    |

