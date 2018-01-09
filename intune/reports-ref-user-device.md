---
title: "Användarenhetsassociation – Intune-informationslagret | Microsoft Docs"
description: "En lista över ändringar i Intunes informationslager-API."
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
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
ms.openlocfilehash: 45c3e14631fdfe74cafea4a0965efac51386524a
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2018
---
# <a name="user-device-association"></a>Användarenhetsassociation

Entiteten **Användarenhetsassociation** innehåller användarenhetsassociationer i din organisation.

| Namn               | Description                                                                                      | Exempel                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Unikt id för användaren i informationslagret. (Surrogatnyckel).                              | 123                    |
| DeviceKey          | Unikt id för enheten i informationslagret.                                            | 123                    |
| CreatedDateTimeUTC | Datum och tid när användarenhetsassociationen skapades. Använder UTC-formatet.                                | 2016-11-23 12:00:00 |
| IsDeleted          | Anger att användaren har avregistrerat enheten och att associationen inte är aktuell längre. | Sant/falskt             |
| EndedDateTimeUTC   | Datum och tid i UTC när IsDeleted ändrades till **True**.                                              | 2017-06-23 12:00:00 |
