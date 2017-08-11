---
title: "Användare | Microsoft Docs"
description: "Referensavsnitt för kategorin Användare för entitetssamlingar i API:t för Intune-informationslager."
keywords: Intune-informationslager
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2b9739299c52c668117116f54c08715f1218d130
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-user-entity"></a>Referens för användarentitet

Kategorin **Användare** innehåller entiteten **Användare** som definierar använda- och agentegenskaper i datamodellen.

**Användare**

Entiteten **Användare** visar alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i ditt företag.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| UserKey |Unikt id för användaren i informationslagret – surrogatnyckel |123 |
| UserId |Unikt id för användaren, liknar UserKey men är en naturlig nyckel |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Användarens e-postadress |John@constoso.com |
| DisplayName |Användarens visningsnamn |John |
| IntuneLicensed |Anger om användaren är Intune-licensierad eller inte. |Sant/falskt |
| IsDeleted |Visar huruvida den här användarposten har uppdaterats.  Sant: användaren har en ny post med uppdaterade fält i den här tabellen. Falskt: den senaste posten för den här användaren. |Sant/falskt |
| StartDateInclusiveUTC |Datum och tid i UTC när den här användaren skapades i informationslagret |2016-11-23 12:00:00 |
| EndDateExclusiveUTC |Datum och tid i UTC när IsDeleted ändrades till True |2016-11-23 12:00:00 |
| IsCurrent |Visar om den här användarposten i informationslagret är aktuell eller inte |Sant/falskt |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC när den här användaren senast ändrades i informationslagret |2016-11-23 12:00:00 |

