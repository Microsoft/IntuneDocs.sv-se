---
title: Användarenhetsassociation – Intune-informationslager
titlesuffix: Microsoft Intune
description: En lista över ändringar i Intunes informationslager-API.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0829bbcb661822c5d00ba4ca1e5d31ece301ef02
ms.sourcegitcommit: 445a54dc6826a549d770a9953549ae2191d391c2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2018
ms.locfileid: "45727432"
---
# <a name="user-device-association"></a>Användarenhetsassociation

Entiteten **Användarenhetsassociation** innehåller användarenhetsassociationer i din organisation.


|        Namn        |                                           Beskrivning                                            |        Exempel         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              Unikt id för användaren i informationslagret. (Surrogatnyckel).               |          123           |
|     DeviceKey      |                      Unikt id för enheten i informationslagret.                      |          123           |
| CreatedDateTimeUTC |           Datum och tid när användarenhetsassociationen skapades. Använder UTC-formatet.           | 2016-11-23 12:00:00 |
|     IsDeleted      | Anger att användaren har avregistrerat enheten och att associationen inte är aktuell längre. |       Sant/falskt       |
|  EndedDateTimeUTC  |              Datum och tid i UTC när IsDeleted ändrades till <strong>True</strong>.               | 2017-06-23 12:00:00 |

