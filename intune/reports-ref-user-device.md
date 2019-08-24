---
title: Användarenhetsassociation – Intune-informationslager
titleSuffix: Microsoft Intune
description: Entiteten UserDeviceAssociation innehåller användarenhetsassociationer i din organisation.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
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
ms.openlocfilehash: 4593fd5e76bf51b11ef9796bacc8c562241eaca2
ms.sourcegitcommit: c8cb314256c4896e838918f015ffaefb8f00ace5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2019
ms.locfileid: "70001749"
---
# <a name="reference-for-user-device-association-entity"></a>Referens för entiteten för användarenhetsassociationer

Entiteten **userDeviceAssociation** innehåller användarenhetsassociationer i din organisation.

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        Namn        |                                           Beskrivning                                            |        Exempel         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      userKey       |              Unikt id för användaren i informationslagret. (Surrogatnyckel).               |          123           |
|     deviceKey      |                      Unikt id för enheten i informationslagret.                      |          123           |
| createdDateTimeUTC |           Datum och tid när användarenhetsassociationen skapades. Använder UTC-formatet.           | 2016-11-23 12:00:00 |
|     isDeleted      | Anger att användaren har avregistrerat enheten och att associationen inte är aktuell längre. |       Sant/falskt       |
|  endedDateTimeUTC  |              Datum och tid i UTC när IsDeleted ändrades till <strong>True</strong>.               | 2017-06-23 12:00:00 |

## <a name="next-steps"></a>Nästa steg

- Mer information om [Intune-informationslagret](reports-nav-create-intune-reports.md).
