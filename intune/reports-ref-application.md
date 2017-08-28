---
title: Program | Microsoft Docs
description: "Referensavsnitt för kategorin Program för entitetssamlingar i API:et för Intune-informationslager."
keywords: Intune-informationslager
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6107059888c8d2fb6227277202a5906491ac9092
ms.sourcegitcommit: b8ef9d8387b4d9b2ea4e6ce937635304771e6532
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/11/2017
---
# <a name="reference-for-application-entities"></a>Referens för programenheter

Kategorin **Program** innehåller entiteter för mobilenheter som spårar information, till exempel:

  -  Versioner av en app
  -  Installationskälla för en app
  -  Typ av utvecklare som har skapat en app
  -  Hanterade typer av programvara för en app, till exempel **sidecar** eller **desktop**
  -  VPP-status (volymköpsprogram) för en app

## <a name="apprevision"></a>AppRevision

I entiteten **AppRevision** visas en lista över alla versioner av appen.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| AppKey |Appens unika id |123 |
| ApplicationId |Unikt id för appen, liknar AppKey men den här nyckeln är naturlig. |b66bc706-ffff-7437-0340-032819502773 |
| Revision |Versionen som anges av administratören under uppladdningen av binärfilen |2 |
| Titel |Appens titel |Excel |
| Utgivare |Appens utgivare |Microsoft |
| UploadState |Appens uppladdningsstatus |1 |
| AppTypeKey |Referens till AppType som beskrivs i följande avsnitt. | |
| VppProgramTypeKey |Referens till VppProgramType som beskrivs nedan | |
| SkapadTid |Tidpunkt då versionen skapades |2016-11-23 12:00:00 |
| ModifiedTime |Senaste ändring av något relaterat till den här versionen |2016-11-23 12:00:00 |
| Storlek |Storlek på binärfilen | |
| StartDateInclusiveUTC |Datum och tid i UTC när appversionen skapades i informationslagret |2016-11-23 12:00:00 |
| EndDateExclusiveUTC |Datum och tid i UTC när appversionen blev inaktuell |2016-11-23 12:00:00 |
| IsCurrent |Visar om appversionen i informationslagret är aktuell eller inte |Sant/falskt |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC för senaste ändring av appversionen i informationslagret |2016-11-23 12:00:00 |

## <a name="apptypes"></a>AppTypes

Entiteten **AppTypes** visar en lista över installationskällan för en app.

| Egenskap  | Beskrivning |
|---------|------------|
| AppTypeID |Id för typen |
| AppTypeKey |Surrogatnyckel för nyckeln |
| AppTypeName |Typ av app |

## <a name="example"></a>Exempel

| AppTypeID  | Namn | Beskrivning |
|---------|------------|--------|
| 0 |Android Store-app |En Android Store-app |
| 1 |Verksamhetsspecifik Android-app |En verksamhetsspecifik app för Android |
| 2 |Hanterad Android Store-app (MAM) |En Android-app med aktiverad hantering |
| 3 |iOS Store-app |En iOS Store-app |
| 4 |Verksamhetsspecifik iOS-app |Verksamhetsspecifik app för iOS |
| 5 |Hanterad iOS Store-app (MAM?) |En iOS Store-app med aktiverad hantering |
| 6 |O365 Pro Plus Suite |Office 365 Pro Plus Suite för Windows 10 |
| 7 |Webbapp |En webbapp |
| 8 |Windows Phone 8.1 Store-app |En Windows Phone 8.1 Store-app |
| 9 |Windows Store-app |En Windows Store-app |
| 10 |Verksamhetsspecifika Windows-appar |En verksamhetsspecifik Windows AppX-app |
| 11 |Windows Mobile MSI |En Verksamhetsspecifik app för MSI |
| 12 |Verksamhetsspecifik Windows Phone-app |Verksamhetsspecifik app för Windows Phone |


## <a name="vppprogramtypes"></a>VppProgramTypes

Entiteten **VppProgramTypes** innehåller en lista över möjliga typer av volymköpsprogram för en app.

| Egenskap  | Beskrivning |
|---------|------------|
| VppProgramTypeID |Id för typen |
| VppProgramTypeKey |Surrogatnyckel för nyckeln |
| VppProgramTypeName |Typ av volymköpsprogram |

## <a name="example"></a>Exempel

| VppProgramID  | Namn | Beskrivning |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 |Microsoft |Microsofts volymköpsprogram |
| 00000000-0000-0000-0000-000000000000 |Inte tillgängligt än |Standardvärde, inget volymköpsprogram |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B |Apple |Apples volymköpsprogram |
