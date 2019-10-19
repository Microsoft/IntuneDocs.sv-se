---
title: Referens för programentiteter
titleSuffix: Microsoft Intune
description: Referensavsnitt för kategorin Program för entitetssamlingar i API:et för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ac40be5cf3d0a0a217340b3c745daf740a24e8e7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490376"
---
# <a name="reference-for-application-entities"></a>Referens för programenheter

Kategorin **Program** innehåller entiteter för mobilenheter som spårar information, till exempel:

- Versioner av en app
- Installationskälla för en app
- Typ av utvecklare som har skapat en app
- Hanterade typer av programvara för en app, till exempel **sidecar** eller **desktop**
- VPP-status (volymköpsprogram) för en app

## <a name="apprevisions"></a>appRevisions

I entiteten **AppRevision** visas en lista över alla appversioner.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| appKey |Appens unika id. |123 |
| applicationId |Unikt id för appen, liknar AppKey men den här nyckeln är naturlig. |b66bc706-ffff-7437-0340-032819502773 |
| revision |Versionen som anges av administratören under uppladdningen av binärfilen. |2 |
| title |Appens titel. |Excel |
| utgivare |Appens utgivare. |Microsoft |
| uploadState |Appens uppladdningsstatus. |1 |
| appTypeKey |Referens till AppType som beskrivs i följande avsnitt. | |
| vppProgramTypeKey |Referens till VppProgramType som beskrivs nedan. | |
| creationTime |Tidpunkt då versionen skapades. |2016-11-23 12:00:00 |
| modifiedTime |Senaste ändring av något relaterat till den här versionen. |2016-11-23 12:00:00 |
| ikoner |Storlek på binärfilen. | |
| startDateInclusiveUTC |Datum och tid i UTC när appversionen skapades i informationslagret. |2016-11-23 12:00:00 |
| endDateExclusiveUTC |Datum och tid i UTC när appversionen blev inaktuell. |2016-11-23 12:00:00 |
| isCurrent |Visar om appversionen i informationslagret är aktuell eller inte. |Sant/falskt |
| rowLastModifiedDateTimeUTC |Datum och tid i UTC för senaste ändring av appversionen i informationslagret. |2016-11-23 12:00:00 |

## <a name="apptypes"></a>appTypes

Entiteten **AppType** visar en lista över installationskällan för en app.

| Egenskap  | Beskrivning |
|---------|------------|
| appTypeID |Id för typen |
| appTypeKey |Surrogatnyckel för nyckeln |
| appTypeName |Typ av app |

### <a name="example"></a>Exempel

| AppTypeID  | Namn | Beskrivning |
|---------|------------|--------|
| 0 |Android Store-app | En Android Store-app. |
| 1 |Verksamhetsspecifik Android-app | En verksamhetsspecifik app för Android. |
| 2 |Hanterad Android Store-app (MAM) | En Android-app med aktiverad hantering. |
| 3 |iOS Store-app | En iOS Store-app. |
| 4 |Verksamhetsspecifik iOS-app | Verksamhetsspecifik app för iOS. |
| 5 |Hanterad iOS Store-app (MAM?) | En iOS Store-app med aktiverad hantering. |
| 6 |O365 Pro Plus Suite | Office 365 Pro Plus Suite för Windows 10. |
| 7 |Webbapp | En webbapp. |
| 8 |Windows Phone 8.1 Store-app | En Windows Phone 8.1 Store-app. |
| 9 |Windows Store-app | En Windows Store-app. |
| 10 |Verksamhetsspecifika Windows-appar | En verksamhetsspecifik Windows AppX-app. |
| 11 |Windows Mobile MSI | En verksamhetsspecifik app för MSI. |
| 12 |Verksamhetsspecifik Windows Phone-app | Verksamhetsspecifik app för Windows Phone. |


## <a name="vppprogramtypes"></a>vppProgramTypes

Entiteten **vppProgramType** innehåller en lista över möjliga typer av volymköpsprogram för en app.

| Egenskap  | Beskrivning |
|---------|------------|
| vppProgramTypeID | Id för typen. |
| vppProgramTypeKey | Surrogatnyckel för nyckeln. |
| vppProgramTypeName | Typ av volymköpsprogram. |

### <a name="example"></a>Exempel

| VppProgramID  | Namn | Beskrivning |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsofts volymköpsprogram. |
| 00000000-0000-0000-0000-000000000000 | Inte tillgängligt än | Standardvärde, inget volymköpsprogram. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apples volymköpsprogram. |



## <a name="applicationinventories"></a>applicationInventories

Entiteten **applicationInventory** innehåller en lista över program som hittats på enheten under inventeringen.

| Egenskap  | Beskrivning |
|---------|------------|
| deviceKey | Det här är en referens till enhetstabellen som innehåller Intune-enhetens ID. |
| dateKey | Referens till datumtabellen som visar dagen för inventeringen. |
| applicationName | Programnamnet. |
| applicationVersion | Programmets version. |
| bundleSize | Appens storlek i byte. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

Entiteten **mobileAppInstallState** representerar installationstillståndet för ett mobilprogram efter det att det har tilldelats till en grupp som innehåller enheter och/eller användare.

| Egenskap | Beskrivning |
|---|---|
| appInstallStateKey | Unikt ID för appens installationstillstånd för ditt konto. |
| appInstallState | Uppräkningsvärde för appens installationstillstånd. |
| appInstallStateName | Namn på appens installationstillstånd. |



