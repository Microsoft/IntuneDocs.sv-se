---
title: Användarenhetsassociation – Intune-informationslager
titlesuffix: Microsoft Intune
description: Entiteten UserDeviceAssociation innehåller användarenhetsassociationer i din organisation.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.openlocfilehash: 02c579a7371a59a46cfb0017e6aa1a17af92bd03
ms.sourcegitcommit: 1c9ef5cfac2fc024528d2cfc9d590fa68dd58080
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429567"
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