---
title: Användarenhetsassociation – Intune-informationslager
titleSuffix: Microsoft Intune
description: Entiteten UserDeviceAssociation innehåller användarenhetsassociationer i din organisation.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7401b5da7629addf03498afd44033a59839d39e
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66045319"
---
# <a name="reference-for-user-device-association-entity"></a>Referens för entiteten för användarenhetsassociationer

Entiteten **Användarenhetsassociation** innehåller användarenhetsassociationer i din organisation.

## <a name="userdeviceassociation"></a>UserDeviceAssociation


|        Namn        |                                           Beskrivning                                            |        Exempel         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              Unikt id för användaren i informationslagret. (Surrogatnyckel).               |          123           |
|     DeviceKey      |                      Unikt id för enheten i informationslagret.                      |          123           |
| CreatedDateTimeUTC |           Datum och tid när användarenhetsassociationen skapades. Använder UTC-formatet.           | 2016-11-23 12:00:00 |
|     IsDeleted      | Anger att användaren har avregistrerat enheten och att associationen inte är aktuell längre. |       Sant/falskt       |
|  EndedDateTimeUTC  |              Datum och tid i UTC när IsDeleted ändrades till <strong>True</strong>.               | 2017-06-23 12:00:00 |

## <a name="next-steps"></a>Nästa steg

- Mer information om [Intune-informationslagret](reports-nav-create-intune-reports.md).
