---
title: "Användarenhetsassociation – Intune-informationslagret | Microsoft Docs"
description: "En lista över ändringar i Intunes informationslager-API."
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9032ffa547daeb19e694a0245dfec676d85a5793
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
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
