---
title: "Användarenhetsassociation | Microsoft Docs"
description: "Referensavsnitt för kategorin Användarenhetsassociation i API:et för Intune-informationslager."
keywords: Intune-informationslager
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: BCDBABCB-A7B1-42F2-BDD1-D055E33F2239
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 490e29f87c65875a385472e6abe9400363383f9b
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-device-association-entity"></a>Referens för entiteten för användarenhetsassociationer

Kategorin **Användarenhetsassociation** innehåller entiteten **Användarenhetsassociation** som användes för att definiera enhetsassociationer i organisationen.

**Användarenhetsassociation**

Entiteten **Användarenhetsassociation** representerar organisationens enhetsassociationer.

| Namn               | Beskrivning                                                                                      | Exempel                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Unikt id för användaren i informationslagret – surrogatnyckel.                             | 123                    |
| DeviceKey          | Unikt id för enheten i informationslagret.                                           | 123                    |
| CreatedDateTimeUTC | Datum och tid i UTC när användarenhetsassociationen skapades.                               | 2016-11-23 12:00:00 |
| IsDeleted          | Anger att användaren har avregistrerat enheten och att associationen inte är aktuell längre. | Sant                   |
| EndedDateTimeUTC   | Datum och tid i UTC när IsDeleted ändrades till **True**.                                         | 2017-06-23 12:00:00 |