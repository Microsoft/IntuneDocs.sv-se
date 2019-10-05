---
title: Hantering av mobila appar (MAM)
titleSuffix: Microsoft Intune
description: Referensavsnitt för kategorin Mobilappshantering för entitetssamlingar i API:et för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f06d2b4b61d522dced12e5d08cd1e854aefd9de8
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71939949"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Referens för MAM-entiteter (hantering av mobilappshantering)

Kategorin **Mobilappshantering** innehåller entiteter för mobilappar som:

- Appar
- Instanser
- Incheckningsstatus
- Hälsostatus
- Principstatus
- Registreringsstatus
- Plattformstyper

## <a name="mamapplications"></a>mamApplications

Entiteten **mamApplication** innehåller en lista över verksamhetsspecifika appar som hanteras via mobilappshantering (MAM) utan registrering i företaget.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| mamApplicationKey |Unik identifierare för MAM-programmet. | 432 |
| mamApplicationName |Namn på MAM-programmet. |Exempelnamn på MAM-program |
| mamApplicationId |Program-ID för MAM-programmet. | 123 |
| isDeleted |Visar huruvida posten för MAM-appen har uppdaterats. <br>Sant: MAM-appen innehåller en ny post med uppdaterade fält i den här tabellen. <br>Falskt: den senaste posten för den här MAM-appen. |Sant/falskt |
| startDateInclusiveUTC |Datum och tid i UTC när MAM-appen skapades i informationslagret. |2016-11-23 12:00:00 |
| deletedDateUTC |Datum och tid i UTC när IsDeleted ändrades till True. |2016-11-23 12:00:00 |
| rowLastModifiedDateTimeUTC |Datum och tid i UTC för senaste ändring av MAM-appen i informationslagret. |2016-11-23 12:00:00 |


## <a name="mamapplicationinstances"></a>mamApplicationInstances

Entiteten **mamApplicationInstance** innehåller en lista över appar som hanteras via mobilappshantering (MAM) som enskilda instanser per användare och enhet. Alla användare och enheter i listan är skyddade, vilket betyder att det finns minst en princip för mobilappshantering kopplad till dem.


|          Egenskap          |                                                                                                  Beskrivning                                                                                                  |               Exempel                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               Unikt id för MAM-appinstansen i informationslagret – surrogatnyckel.                                                                |                 123                  |
|           userId           |                                                                              Användar-ID för den användare som har den här MAM-appen installerad.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              Unikt id för MAM-appinstansen, liknar ApplicationInstanceKey,men id:t är en naturlig nyckel.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | Program-ID för det Mam-program som Mam-programinstansen skapades för.   | 2016-11-23 12:00:00   |
|     applicationVersion     |                                                                                     Programversion för MAM-appen.                                                                                      |                  2                   |
|        createdDate         |                                                                 Datum då MAM-appinstansposten skapades. Värdet kan vara null.                                                                 |        2016-11-23 12:00:00        |
|          plattform          |                                                                          Plattform för den enhet där MAM-appen är installerad.                                                                           |                  2                   |
|      platformVersion       |                                                                      Plattformsversion för enheten där MAM-appen är installerad.                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            SDK-version där MAM-appen är paketerad.                                                                            |                 3.2                  |
| mamDeviceId | Enhets-ID för den enhet som MAM-programinstansen är associerad med.   | 2016-11-23 12:00:00   |
| mamDeviceType | Enhetstyp för enheten som MAM-programinstansen är associerad med.   | 2016-11-23 12:00:00   |
| mamDeviceName | Enhetsnamn för enheten som MAM-programinstansen är associerad med.   | 2016-11-23 12:00:00   |
|         isDeleted          | Visar huruvida posten för MAM-appinstansen har uppdaterats. <br>Sant: MAM-appinstansen innehåller en ny post med uppdaterade fält i den här tabellen. <br>Falskt: den senaste posten för den här MAM-appinstansen. |              Sant/falskt              |
|   startDateInclusiveUtc    |                                                              Datum och tid i UTC när MAM-appinstansen skapades i informationslagret.                                                               |        2016-11-23 12:00:00        |
|       deletedDateUtc       |                                                                             Datum och tid i UTC när IsDeleted ändrades till True.                                                                              |        2016-11-23 12:00:00        |
| rowLastModifiedDateTimeUtc |                                                           Datum och tid i UTC för senaste ändring av MAM-appinstansen i informationslagret.                                                            |        2016-11-23 12:00:00        |


## <a name="mamcheckins"></a>mamCheckins

Entiteten **mamCheckin** visar data som samlas in när en hanterad mobilappinstans har checkat in på Intune-tjänsten. 

> [!Note]  
> När en appinstans checkar in flera gånger per dag lagras den i informationslagret som en enda incheckning.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| dateKey |Datumnyckel när incheckningen av MAM-appen registrerades i informationslagret. | 20160703 |
| applicationInstanceKey |Nyckel för appinstansen som är kopplad till incheckningen av den mobilappshanterade appen. | 123 |
| userKey |Nyckel för användaren som är kopplad till incheckningen av MAM-appen. | 4323 |
| mamApplicationKey |Programnyckel för programmet som är associerat med MAM-programincheckningen. | 432 |
| deviceHealthKey |Nyckel för DeviceHealth som är koppla till den här incheckningen av MAM-appen. | 321 |
| platformKey |Visar plattformen för enheten som är kopplad till den här incheckningen av MAM-appen. |123 |
| effectiveAppliedPolicyKey |Visar gällande tillämpad princip som är kopplad till den här incheckade MAM-appen. En gällande tillämpad princip är en sammansättning av alla principer som är relevanta för en viss app och användare. | 322 |
| pastCheckInDate |Datum och tid för den senaste incheckningen av MAM-appen. Värdet kan vara null. |2016-11-23 12:00:00 |


## <a name="mamdevicehealth"></a>mamDeviceHealth

Entiteten **mamDeviceHealth** motsvarar de enheter där principer för mobilappshantering (MAM) har distribuerats även om de är jailbrokade.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| deviceHealthKey |Unikt id för enheten med tillhörande hälsostatus i informationslagret – surrogatnyckel. |123 |
| deviceHealth |Unikt id för enheten och dess tillhörande hälsostatus, liknar DeviceHealthKey men id:t är en naturlig nyckel. |b66bc706-ffff-7777-0340-032819502773 |
| deviceHealthName |Visar enhetens status. <br>Inte tillgänglig: det finns ingen information om enheten. <br>Felfri: enheten är inte jailbrokad. <br>Ej felfri: enheten är jailbrokad. |Inte tillgänglig Felfri Ej felfri |
| rowLastModifiedDateTimeUtc |Datum och tid i UTC för senaste ändring av hälsotillståndet för mobilappshanterad enhet i informationslagret. |2016-11-23 12:00:00 |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

Entiteten **mamEffectivePolicy** innehåller en lista över gällande principer för mobilappshantering (MAM) som tillämpas i din organisation. En gällande tillämpad princip är en sammansättning av alla principer som är relevanta för en viss app och användare.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| effectivePolicyKey |Unikt id för gällande mobilappshanteringsprincip informationslagret. |2 |
| realPolicyKey |Unikt id för den mobilappshanteringsprincip som utfärdats av it-avdelningen. |1 |
| rowCreatedDateTimeUtc |Datum och tid i UTC när mobilappshanteringsprincipen skapades i informationslagret. |2016-11-23 12:00:00 |

## <a name="mamplatforms"></a>mamPlatforms

Entiteten **mamPlatform** innehåller en lista över namn på plattformar och typer där en mobilappshanterad app (MAM) har installerats.


|          Egenskap          |                                    Beskrivning                                    |                         Exempel                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     Unikt id för plattformen i informationslagret – surrogatnyckel.      |                           123                           |
|          plattform          | Unikt id för plattformen, liknar PlatformKey men är en naturlig nyckel. |                           123                           |
|        platformName        |                                   Namn på plattform                                   | Inte tillgängligt <br>Inga <br>Windows <br>iOS <br>Android. |
| rowLastModifiedDateTimeUtc | Datum och tid i UTC för senaste ändring av plattformen i informationslagret.  |                 2016-11-23 12:00:00                  |

