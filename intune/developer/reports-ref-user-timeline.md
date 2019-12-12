---
title: Användarentitetens tidslinje i informationslagret
titleSuffix: Microsoft Intune
description: Läs om hur Microsoft Intune-informationslagret visar användare på en tidslinje.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b94be3e1454c60f16ff40e73ce37f8c4e349126d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813351"
---
# <a name="user-lifetime-representation-in-the-microsoft-intune-data-warehouse"></a>Visning av användarlivstiden i Microsoft Intunes informationslager

Du kan använda månaden för ögonblicksbilder som lagras i Intunes informationslager för att besvara frågor om tidsbaserade trender. Exempelvis kan du titta på hur många användare som lagts till under en månad. Du kan också fråga om antalet användare som har tagits bort från systemet.

Informationslagret lagrar historisk information för att kunna tillhandahålla den här insiktstypen. Informationslagret kan spåra livslängden för en entitet. Lagret registrerar när en entitet skapades, när entitetens status ändras och när en entitet tas bort. Med historiken som fångats i de dagliga ögonblicksbilderna av kvantitativa mått, kan du jämföra en dag mot föregående dag och så vidare.

Det kan vara förvirrande att arbeta med entitetslivslängder eftersom entiteterna ändrar tillstånd. Det innebär att om du tittar på en ögonblicksbild av dag 30, kanske en användarpost inte finns i aktivt tillstånd i data. På dag 29-28 finns dock entitetsposten som aktiv. Och innan dag 28, fanns inte användaren alls.

Scenariot blir tydligare om du går igenom livslängden för en entitet.

Anta att en användare **John Smith**, blir tilldelad en licens 2017-06-01, då skulle tabellen **användare** innehålla följande post: 
 
| Visningsnamn | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 12/31/9999 | TRUE
 
John Smith säger upp sin licens 2017-07-25. Tabellen **användare** har följande poster. Ändringar i befintliga poster är `marked`. 

| Visningsnamn | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | `07/26/2017` | `FALSE` 
| John Smith | TRUE | 07/26/2017 | 12/31/9999 | TRUE 

Den första raden anger att John Smith fanns i Intune från 2017-06-01 till 2017-07-25. Den andra posten anger att användaren har tagits bort 2017-07-25 och inte längre finns i Intune.

Anta att en användare John Smith, får en ny licens tilldelad 2017-08-31, då skulle tabellen användare innehålla följande poster:
 
| Visningsnamn | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 07/26/2017 | FALSE 
| John Smith | TRUE | 07/26/2017 | `08/31/2017` | `FALSE` 
| John Smith | FALSE | 08/31/2017 | 12/31/9999 | TRUE 
 
En person som vill se aktuell status för alla användare, behöver använda ett filter där `IsCurrent = TRUE`. 
 
En person som enbart vill se aktuella användare, behöver använda ett filter där `IsCurrent = TRUE AND IsDeleted = FALSE`.

## <a name="dimension-tables-in-the-entity-lifetime"></a>Dimensionstabeller i entitetens livslängd

För att kunna lagra historiken över tillståndsändringar, tar Intune inte bort poster. Istället markeras posten som borttagen. Det kallas en mjuk borttagning. Dimensionstabellerna använder olika metadatakolumner för att spåra livslängden för poster. 

De vanligaste metadatakolumnerna är: 

| Namn på metadataegenskap  | Tolkning av värden |
|--|--|
| IsDeleted | Anger om entiteten har tagits bort i Intune. |
| StartDateInclusiveUTC  | UTC-datum då entiteten lästes in i Intune-informationslagret. Entiteten kan ha skapats innan den importerades till Intune-informationslagret. |
| DeletedDateUTC  | UTC-datumet då entiteten togs bort i Intune. |  

En metadatakolumn som börjar med prefixet **Row**, som **RowLastModifiedDateTimeUTC**, anger när en post skapades eller ändrades i Intune-informationslagret. Lagret är nedströms från data i Intune. Det här värdet har ingen relation till livslängden för entiteten i Intune.  
 
En person som enbart vill se de dimensionsentiteter som finns för tillfället, behöver använda ett filter där **IsDeleted = FALSE**.

## <a name="next-steps"></a>Nästa steg

- Mer information om entiteten **Aktuell användare** finns i [Referens för den aktuella användarentiteten](../reports-ref-current-user.md).
- Information om entiteten **Användare** finns i [Referens för användarentiteten](../reports-ref-user.md).
