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
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 095395be4c86780ad65ba1e24b856f6eef8d41ae
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/16/2018
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
