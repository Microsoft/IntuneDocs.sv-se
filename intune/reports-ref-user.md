---
title: Användare – Intune-informationslager
titlesuffix: Microsoft Intune
description: Referensavsnitt för kategorin Användare för entitetssamlingar i API:t för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/20/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ab0674304f1e74c8bf2ad1aeecd419575484e5f
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58358178"
---
# <a name="reference-for-user-entity"></a>Referens för användarentitet

Kategorin **Användare** innehåller entiteten **Användare** som definierar användaregenskaper i datamodellen.

## <a name="user"></a>Användare

Entiteten **Användare** visar alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i ditt företag.

Entitetssamlingen **Användare** innehåller användardata. De här posterna innehåller användarens tillstånd vid datainsamlingsperioden, även om användaren har tagits bort. En användare kan till exempel läggas till i Intune och sedan tas bort under den senaste månaden. Användaren är då inte tillgänglig vid tidpunkten för rapporten, men användaren och tillståndet finns i data från föregående månad. Du kan skapa en rapport som visar varaktigheten för användarens historiska förekomst i dina data.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| UserKey |Unikt id för användaren i informationslagret – surrogatnyckel. |123 |
| UserId |Unikt id för användaren, liknar UserKey men är en naturlig nyckel. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Användarens e-postadress. |John@constoso.com |
| userPrincipalName | Användarens huvudnamn. | John@constoso.com |
| DisplayName |Användarens visningsnamn. |John |
| IntuneLicensed |Anger om användaren är Intune-licensierad eller inte. |Sant/falskt |
| IsDeleted | Anger om alla användarens licenser har gått ut och om användaren därför har tagits bort från Intune. Den här flaggan ändras inte för en enskild post. Istället skapas en ny post för ett nytt användartillstånd. |Sant/falskt |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC när posten senast ändrades i informationslagret  |2016-11-23 12:00:00 |

## <a name="next-steps"></a>Nästa steg
 - Du kan använda entitetssamlingen **aktuell användare** för att begränsa användardata till användare som för närvarande är aktiva. Mer information finns i [referens för den aktuella användarentiteten](reports-ref-current-user.md).
 - Mer information om hur informationslagret spårar en användares livstid i Intune finns i [Representation av användarens livstid i Intunes informationslager](reports-ref-user-timeline.md).
