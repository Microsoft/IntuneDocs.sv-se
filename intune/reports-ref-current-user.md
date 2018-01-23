---
title: "Aktuell användare – Intune-informationslagret | Microsoft Docs"
description: "Referensavsnitt för kategorin Användare för entitetssamlingar i API:t för Intune-informationslager."
keywords: Intune-informationslager
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 895855befe31e84b3dc472216afdf52d636bc27a
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/16/2018
---
# <a name="reference-for-current-user-entity"></a>Referens för aktuell användarentitet

Kategorin **aktuell användare** innehåller användaregenskaper i datamodellen. Entitetssamlingen **aktuell användare** begränsas till användare som är aktiva. Entiteten innehåller alla Azure Active Directory-användare är tilldelade en licens för tillfället. Licensen kan vara en Intune-licens, en Hybrid-licens eller en licens för Microsoft Office 365. Om en användare har tagits bort, kommer hen inte att representeras i kollektionen för aktuell användare. En samling som innehåller en historik över ändringar i användartillstånd finns i [referens för användarentiteten](reports-ref-user.md).


## <a name="current-user"></a>Aktuell användare

Entiteten **Aktuell användare** visar alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i ditt företag.

| Egenskap  | Description | Exempel |
|---------|------------|--------|
| UserKey |Unikt id för användaren i informationslagret – surrogatnyckel. |123 |
| UserId |Unikt id för användaren, liknar UserKey men är en naturlig nyckel. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Användarens e-postadress. |John@constoso.com |
| UPN | Användarens huvudnamn. | John@constoso.com |
| DisplayName |Användarens visningsnamn. |John |
| IntuneLicensed |Anger om användaren är Intune-licensierad eller inte. |Sant/falskt |
| StartDateInclusiveUTC |Datum och tid i UTC när den här användaren skapades i informationslagret. |2016-11-23 12:00:00 |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC när den här användaren senast ändrades i informationslagret. |2016-11-23 12:00:00 |

## <a name="next-steps"></a>Nästa steg
 - Du kan använda entitetssamlingen **användare** för att utöka användardata till användare som inte är aktiva. Mer information finns i [referens för användarentiteten](reports-ref-user.md).
 - Läs mer om hur informationslagret spårar en användares livstid i Intune i [representation av användarlivstid Intune-informationslagret](reports-ref-user-timeline.md).
