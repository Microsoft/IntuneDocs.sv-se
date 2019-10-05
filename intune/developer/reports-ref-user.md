---
title: Användare – Intune-informationslager
titleSuffix: Microsoft Intune
description: Referensavsnitt för kategorin Användare för entitetssamlingar i API:t för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 444ed3ad156e81a15eec0b86bb670eb63b5b04e7
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71939931"
---
# <a name="reference-for-user-entity"></a>Referens för användarentitet

Kategorin **Användare** innehåller entiteten **användare** som definierar användaregenskaper i datamodellen.

## <a name="users"></a>användare

Entiteten **user** visar en lista över alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i företaget.

Entitetssamlingen **user** innehåller användardata. De här posterna innehåller användarens tillstånd vid datainsamlingsperioden, även om användaren har tagits bort. En användare kan till exempel läggas till i Intune och sedan tas bort under den senaste månaden. Användaren är inte tillgänglig vid tidpunkten för rapporten, men användaren och tillståndet finns i data från föregående månad. Du kan skapa en rapport som visar varaktigheten för användarens historiska förekomst i dina data.

|          Egenskap          |                                                                                                           Beskrivning                                                                                                          |                Exempel               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| userKey                    | Unik identifierare för användaren i informationslagret – surrogatnyckel.                                                                                                                                                         | 123                                  |
| userId                     | Unik identifierare för användaren, liknar UserKey men är en naturlig nyckel.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| userEmail                  | Användarens e-postadress.                                                                                                                                                                                                     | John@constoso.com                    |
| userPrincipalName                        | Användarens huvudnamn.                                                                                                                                                                                               | John@constoso.com                    |
| visningsnamn                | Användarens visningsnamn.                                                                                                                                                                                                      | John                                 |
| intuneLicensed             | Anger om användaren är Intune-licensierad eller inte.                                                                                                                                                                              | Sant/falskt                           |
| isDeleted                  | Anger om alla användarens licenser har gått ut och om användaren därför har tagits bort från Intune. Den här flaggan ändras inte för en enskild post. I stället skapas en ny post för ett nytt användartillstånd. | Sant/falskt                           |
| RowLastModifiedDateTimeUTC | Datum och tid i UTC när posten senast ändrades i informationslagret                                                                                                                                                 | 11/23/2016 0:00                      |


## <a name="next-steps"></a>Nästa steg
- Du kan använda entitetssamlingen **aktuell användare** för att begränsa användardata till användare som för närvarande är aktiva. Mer information finns i [referens för den aktuella användarentiteten](../reports-ref-current-user.md).
- Mer information om hur informationslagret spårar en användares livstid i Intune finns i [Representation av användarens livstid i Intunes informationslager](reports-ref-user-timeline.md).
