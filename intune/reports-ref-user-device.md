---
title: "Användarenhetsassociation – Intune-informationslagret | Microsoft Docs"
description: "En lista över ändringar i Intunes informationslager-API."
keywords: Intune-informationslager
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c47455b0139f7451796257a77859cbd9899a7dd
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/02/2017
---
# <a name="user-device-association"></a>Användarenhetsassociation

Entiteten **Användarenhetsassociation** innehåller användarenhetsassociationer i din organisation.

| Namn               | Beskrivning                                                                                      | Exempel                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Unikt id för användaren i informationslagret. (Surrogatnyckel).                              | 123                    |
| DeviceKey          | Unikt id för enheten i informationslagret.                                            | 123                    |
| CreatedDateTimeUTC | Datum och tid när användarenhetsassociationen skapades. Använder UTC-formatet.                                | 2016-11-23 12:00:00 |
| IsDeleted          | Anger att användaren har avregistrerat enheten och att associationen inte är aktuell längre. | Sant/falskt             |
| EndedDateTimeUTC   | Datum och tid i UTC när IsDeleted ändrades till **True**.                                              | 2017-06-23 12:00:00 |
