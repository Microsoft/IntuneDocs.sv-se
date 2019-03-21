---
title: Datamodellen informationslager
titlesuffix: Microsoft Intune
description: Microsoft Intune-informationslagret samlar in data dagligen för att kunna ge en historisk bild över den ständigt föränderliga mobilmiljön.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2cbf6e1bde3f8853f2e5c6c1919089bf0dc10126
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565528"
---
# <a name="microsoft-intune-data-warehouse-data-model"></a>Datamodell för Microsoft Intune-informationslager

Intune-informationslagret samplar dagligen data för att ge en historik över den ständigt föränderliga miljön med mobila enheter. Vyn består av relaterade entiteter i tid.

## <a name="entities-entity-sets"></a>Entiteter: Entitetsuppsättningar

Informationslagret visas data i följande övergripande områden:

  -  Appskyddsaktiverade appar och användning
  -  Registrerade enheter, egenskaper och inventering
  -  Inventering av appar och programvara
  -  Efterlevnadsprinciper och enhetskonfigurering

Dessa områden innehåller entiteterna som är viktiga för din Intune-miljö. Du hittar information entitetsuppsättningarna i följande avsnitt:

  -  [Program](reports-ref-application.md)
  -  [Datum](reports-ref-date.md)
  -  [Enheter](reports-ref-devices.md)
  -  [Tillägg för Intune-hantering](reports-ref-intunemanagementextension.md)
  -  [Princip](reports-ref-policy.md)
  -  [Mobilapphantering (MAM)](reports-ref-mobile-app-management.md)
  -  [Användare](reports-ref-user.md)
  -  [Aktuell användare](reports-ref-current-user.md)
  -  [Användarenhetsassociation](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>Relationer: Star-schemamodellen

Lagret organiserar entiteterna i relationer som är meningsfulla för den typ av frågor du vill ställa. Du kan till exempel granska antalet installationer av ett internt utvecklat Android-program. Informationslagrets struktur ger dig en lättöverskådlig bild av den mobila miljön. Analysverktyg, exempelvis Microsoft Power BI, kan i sin tur använda informationslagerdatamodellen för att skapa visualiseringar och dynamiska instrumentpaneler.

Enheter och relationer använder en star-schemamodell. Ett star-schema visar fakta över en tidsdimension. *Fakta* i det här sammanhanget är ett kvantitativt mått, till exempel antal enheter, antal appar eller registreringstid. Faktatabeller lagrar stora mängder data. De kan bli mycket stora så de begränsar vanligtvis informationen till 30 dagar. En *dimension* ger kontext till fakta. Faktumet mäter vad som händer och dimensionen visar för vem det hände. Dimensionstabeller som **användare**-tabellen är mindre och kan kvarhålla data längre tidsperioder = än faktatabeller. 

Ett stjärnschema är utformat för maximal flexibilitet och dataanalys så att du kan skapade de rapporter som behövs för att förstå din föränderliga mobilmiljö.

## <a name="time-daily-snapshots"></a>Tid: dagliga ögonblicksbilder

Lagret är nedströms från dina Intune-data. Intune tar en daglig ögonblicksbild vid midnatt UTC-tid och lagrar den i lagret. Varaktigheten för kvarhållna ögonblicksbilder varierar mellan faktatabeller. Vissa kan kvarhållas sju dagar, andra 30 dagar och vissa till och med längre.

## <a name="next-steps"></a>Nästa steg

 - Mer information om hur informationslagret spårar en användares livstid i Intune finns i [Representation av användarens livstid i Intunes informationslager](reports-ref-user-timeline.md).
 - Mer information om hur du arbetar med informationslager finns i [Skapa första informationslagret](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse).
 - Mer information om hur du arbetar med Power BI och ett informationslager finns i [skapa en ny Power BI-rapport genom att importera en datauppsättning](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/). 
