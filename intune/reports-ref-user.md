---
title: Användare – Intune-informationslager
titlesuffix: Microsoft Intune
description: Referensavsnitt för kategorin Användare för entitetssamlingar i API:t för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: efeaacffe996701f560af4cf077ee9fd23041545
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="reference-for-user-entity"></a>Referens för användarentitet

Kategorin **Användare** innehåller entiteten **Användare** som definierar användaregenskaper i datamodellen.

## <a name="user"></a>Användare

Entiteten **Användare** visar alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i ditt företag.

Entitetssamlingen **Användare** innehåller användardata. De här posterna innehåller användarens tillstånd vid datainsamlingsperioden, även om användaren har tagits bort. En användare kan till exempel läggas till i Intune och sedan tas bort under den senaste månaden. Användaren är då inte tillgänglig vid tidpunkten för rapporten, men användaren och tillståndet finns i data från föregående månad. Du kan skapa en rapport som visar varaktigheten för användarens historiska förekomst i dina data.

| Egenskap  | Description | Exempel |
|---------|------------|--------|
| UserKey |Unikt id för användaren i informationslagret – surrogatnyckel. |123 |
| UserId |Unikt id för användaren, liknar UserKey men är en naturlig nyckel. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Användarens e-postadress. |John@constoso.com |
| UPN | Användarens huvudnamn. | John@constoso.com |
| DisplayName |Användarens visningsnamn. |John |
| IntuneLicensed |Anger om användaren är Intune-licensierad eller inte. |Sant/falskt |
| IsDeleted | Anger om alla användarens licenser har gått ut och om användaren därför har tagits bort från Intune. Den här flaggan ändras inte för en enskild post. Istället skapas en ny post för ett nytt användartillstånd. |Sant/falskt |
| StartDateInclusiveUTC |Om IsDeleted = falskt, DateTime i UTC när användaren har tilldelats en licens och börjat vara med i Intune. Om IsDeleted = sant, DateTime i UTC när användarens licenser gick ut och den togs bort från Intune. |2016-11-23 12:00:00 |
| EndDateExclusiveUTC |Om IsDeleted = falskt, DateTime i UTC när användarens licenser gick ut och den togs bort från Intune. Licensen gick ut någon gång under föregående dag. Om IsDeleted = sant, DateTime i UTC när användaren fick en ny licens och återskapades i Intune.  |2016-11-23 12:00:00 |
| IsCurrent |Anger om den här posten representerar användarens senaste tillstånd. Flera poster kan finnas för en enskild användare, men endast en av dem representerar det aktuella tillståndet.  |Sant/falskt |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC när posten senast ändrades i informationslagret  |2016-11-23 12:00:00 |

## <a name="next-steps"></a>Nästa steg
 - Du kan använda entitetssamlingen **aktuell användare** för att begränsa användardata till användare som för närvarande är aktiva. Mer information finns i [referens för den aktuella användarentiteten](reports-ref-current-user.md).
 - Läs mer om hur informationslagret spårar en användares livstid i Intune i [representation av användarlivstid Intune-informationslagret](reports-ref-user-timeline.md).
