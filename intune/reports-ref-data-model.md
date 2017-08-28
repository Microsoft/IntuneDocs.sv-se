---
title: Datamodellen informationslager | Microsoft Docs
description: "Intune-informationslagret samplar data dagligen och visar historik över den ständigt föränderliga mobilmiljön."
keywords: Intune-informationslager
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9257af29c65dbe27667738abc8ee06203177124f
ms.sourcegitcommit: b8ef9d8387b4d9b2ea4e6ce937635304771e6532
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/11/2017
---
# <a name="data-warehouse-data-model"></a>Datamodellen informationslager

Intune-informationslagret samplar data dagligen och visar historik över den ständigt föränderliga mobilmiljön.

De data som hämtas från klientorganisationen läggs till i informationslagret. Lagret är en uppsättning entiteter och samband som behövs för den typ av frågor du ställer. Du kan exempelvis titta på antalet installationer av ett internutvecklat Android-program per dag under den senaste veckan för att se om det visar på en ökande trend. Informationslagrets struktur ger dig en lättöverskådlig bild av den mobila miljön. Analysverktyg, exempelvis Microsoft Power BI, kan i sin tur använda informationslagerdatamodellen för att skapa visualiseringar och dynamiska instrumentpaneler.

En schemamodell av stjärntyp används i Intune-informationslagerstrukturen. I ett stjärnschema visas fakta sorterade över en tidsdimension. *Fakta* i det här sammanhanget är ett kvantitativt mått, till exempel antal enheter, antal appar eller registreringstid. En *dimension* i det här sammanhanget är en uppsättning kategorier och deras hierarkiska samband. Dagar grupperas exempelvis i månader och månader grupperas i år. Ett stjärnschema är utformat för maximal flexibilitet och dataanalys så att du kan skapade de rapporter som behövs för att förstå din föränderliga mobilmiljö.

I informationslagret visas data i följande övergripande kategorier:
  -  Appskyddsaktiverade appar och användning
  -  Registrerade enheter, egenskaper och inventering
  -  Inventering av appar och programvara
  -  Efterlevnadsprinciper och enhetskonfigurering

**Datamodellens entitetsuppsättningar**

Entitetsuppsättningar är namngivna samlingar entiteter i datamodellen. Uppsättningarna innehåller entiteter som definierar de data som samlas in av modellen. Varje entitetsuppsättning ger en åtkomstpunkt till informationslagerdatamodellen. Du hittar information om följande entitetskategorier:

  -  [Datum](reports-ref-date.md)
  -  [Användare](reports-ref-user.md)
  -  [Mobilapphantering (MAM)](reports-ref-mobile-app-management.md)
  -  [Enheter](reports-ref-devices.md)
  -  [Program](reports-ref-application.md)
  -  [Princip](reports-ref-policy.md)

<!-- ## Data Model relationships

For more information on the relationships in the data model, see [Relationships of Entities](reports-api-entity-relationships.md). -->