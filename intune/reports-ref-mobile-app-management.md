---
title: Hantering av mobila appar (MAM)
titleSuffix: Microsoft Intune
description: Referensavsnitt för kategorin Mobilappshantering för entitetssamlingar i API:et för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 456abbf849120675b6a7c108ca65c6f9967ae64a
ms.sourcegitcommit: 601327125ac8ae912d8159422de8aac7dbdc25f6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59429207"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Referens för MAM-entiteter (hantering av mobilappshantering)

Kategorin **Mobilappshantering** innehåller entiteter för mobilappar som:

  -  Appar
  -  Instanser
  -  Incheckningsstatus
  -  Hälsostatus
  -  Principstatus
  -  Registreringsstatus
  -  Plattformstyper

## <a name="mamapplication"></a>MamApplication

Entiteten **MamApplication** innehåller en lista över verksamhetsspecifika appar som hanteras via mobilappshantering (MAM) utan registrering i företaget.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| mamApplicationKey |Unikt ID för MAM-programmet. | 432 |
| mamApplicationName |Namn på MAM-programmet. |MAM exempel programnamn |
| mamApplicationId |Program-id för MAM-appen. | 123 |
| IsDeleted |Visar huruvida posten för MAM-appen har uppdaterats. <br>Sant: MAM-appen innehåller en ny post med uppdaterade fält i den här tabellen. <br>Falskt: den senaste posten för den här MAM-appen. |Sant/falskt |
| StartDateInclusiveUTC |Datum och tid i UTC när MAM-appen skapades i informationslagret. |2016-11-23 12:00:00 |
| DeletedDateUTC |Datum och tid i UTC när IsDeleted ändrades till True. |2016-11-23 12:00:00 |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC för senaste ändring av MAM-appen i informationslagret. |2016-11-23 12:00:00 |


## <a name="mamapplicationinstance"></a>MamApplicationInstance

Entiteten **MamApplicationInstance** innehåller en lista över appar som hanteras via mobilappshantering (MAM) som enskilda instanser per användare och enhet. Alla användare och enheter i listan är skyddade, vilket betyder att det finns minst en princip för mobilappshantering kopplad till dem.


|          Egenskap          |                                                                                                  Beskrivning                                                                                                  |               Exempel                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               Unikt id för MAM-appinstansen i informationslagret – surrogatnyckel.                                                                |                 123                  |
|           UserId           |                                                                              Användar-ID för den användare som har den här MAM-appen installerad.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              Unikt id för MAM-appinstansen, liknar ApplicationInstanceKey,men id:t är en naturlig nyckel.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | Program-Id för Mam-programmet som den här Mam-programinstans har skapats.   | 2016-11-23 12:00:00   |
|     ApplicationVersion     |                                                                                     Programversion för MAM-appen.                                                                                      |                  2                   |
|        CreatedDate         |                                                                 Datum då MAM-appinstansposten skapades. Värdet kan vara null.                                                                 |        2016-11-23 12:00:00        |
|          Plattform          |                                                                          Plattform för den enhet där MAM-appen är installerad.                                                                           |                  2                   |
|      PlatformVersion       |                                                                      Plattformsversion för enheten där MAM-appen är installerad.                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            SDK-version där MAM-appen är paketerad.                                                                            |                 3.2                  |
| mamDeviceId | Enhets-Id för enheten där MAM-programinstans som är associerad med.   | 2016-11-23 12:00:00   |
| mamDeviceType | Enhetstyp för enheten där MAM-programinstans som är associerad med.   | 2016-11-23 12:00:00   |
| mamDeviceName | Enhetsnamn för enheten där MAM-programinstans som är associerad med.   | 2016-11-23 12:00:00   |
|         IsDeleted          | Visar huruvida posten för MAM-appinstansen har uppdaterats. <br>Sant: MAM-appinstansen innehåller en ny post med uppdaterade fält i den här tabellen. <br>Falskt: den senaste posten för den här MAM-appinstansen. |              Sant/falskt              |
|   StartDateInclusiveUtc    |                                                              Datum och tid i UTC när MAM-appinstansen skapades i informationslagret.                                                               |        2016-11-23 12:00:00        |
|       DeletedDateUtc       |                                                                             Datum och tid i UTC när IsDeleted ändrades till True.                                                                              |        2016-11-23 12:00:00        |
| RowLastModifiedDateTimeUtc |                                                           Datum och tid i UTC för senaste ändring av MAM-appinstansen i informationslagret.                                                            |        2016-11-23 12:00:00        |


## <a name="mamcheckin"></a>MamCheckin

Entiteten **MamCheckin** visar data som samlas in när en hanterad mobilappinstans har checkat in på Intune-tjänsten. 

> [!Note]  
> När en appinstans checkar in flera gånger per dag lagras den i informationslagret som en enda incheckning.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| DateKey |Datumnyckel när incheckningen av MAM-appen registrerades i informationslagret. | 20160703 |
| ApplicationInstanceKey |Nyckel för appinstansen som är kopplad till incheckningen av den mobilappshanterade appen. | 123 |
| UserKey |Nyckel för användaren som är kopplad till incheckningen av MAM-appen. | 4323 |
| mamApplicationKey |Nyckel för program som är associerade med MAM-programmet incheckning. | 432 |
| DeviceHealthKey |Nyckel för DeviceHealth som är koppla till den här incheckningen av MAM-appen. | 321 |
| PlatformKey |Visar plattformen för enheten som är kopplad till den här incheckningen av MAM-appen. |123 |
| EffectiveAppliedPolicyKey |Visar gällande tillämpad princip som är kopplad till den här incheckade MAM-appen. En gällande tillämpad princip är en sammansättning av alla principer som är relevanta för en viss app och användare. | 322 |
| LastCheckInDate |Datum och tid för den senaste incheckningen av MAM-appen. Värdet kan vara null. |2016-11-23 12:00:00 |


## <a name="mamdevicehealth"></a>MamDeviceHealth

Entiteten **MamDeviceHealth** motsvarar de enheter där principer för mobilappshantering (MAM) har distribuerats även om de är jailbrokade.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| DeviceHealthKey |Unikt id för enheten med tillhörande hälsostatus i informationslagret – surrogatnyckel. |123 |
| DeviceHealth |Unikt id för enheten och dess tillhörande hälsostatus, liknar DeviceHealthKey men id:t är en naturlig nyckel. |b66bc706-ffff-7777-0340-032819502773 |
| DeviceHealthName |Visar enhetens status. <br>Inte tillgänglig: det finns ingen information om enheten. <br>Felfri: enheten är inte jailbrokad. <br>Ej felfri: enheten är jailbrokad. |Inte tillgänglig Felfri Ej felfri |
| RowLastModifiedDateTimeUtc |Datum och tid i UTC för senaste ändring av hälsotillståndet för mobilappshanterad enhet i informationslagret. |2016-11-23 12:00:00 |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

Entiteten **MamEffectivePolicy** innehåller en lista över gällande principer för mobilappshantering som tillämpas i din organisation. En gällande tillämpad princip är en sammansättning av alla principer som är relevanta för en viss app och användare.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| EffectivePolicyKey |Unikt id för gällande mobilappshanteringsprincip informationslagret. |2 |
| RealPolicyKey |Unikt id för den mobilappshanteringsprincip som utfärdats av it-avdelningen. |1 |
| RowCreatedDateTimeUtc |Datum och tid i UTC när mobilappshanteringsprincipen skapades i informationslagret. |2016-11-23 12:00:00 |

## <a name="mamglobalapplication"></a>MamGlobalApplication

Entiteten **MamGlobalApplication** innehåller en lista över Store-appar som hanteras via mobilappshantering (MAM) utan registrering i företaget.


|          Egenskap          |                                               Beskrivning                                               |           Exempel            |
|----------------------------|---------------------------------------------------------------------------------------------------------|------------------------------|
|       ApplicationKey       |          Unikt id för Store-appen i informationslagret, kallas även surrogatnyckeln.          |             123              |
|       ApplicationId        | Store-appens unika id. Id:t liknar ApplicationKey men är en naturlig nyckel.  | com.microsoft.skydrive.<ios> |
|      ApplicationName       |                                      Namn på globalt mobilappshanteringsprogram.                                       |           Skydrive           |
| RowLastModifiedDateTimeUtc | Datum och tid i UTC för senaste ändring av globalt mobilappshanteringsprogram i informationslagret. |    2016-11-23 12:00:00    |

## <a name="mamplatform"></a>MamPlatform

Entiteten **MamPlatform** innehåller en lista över namn på plattformar och typer där en mobilappshanterad app (MAM) har installerats.


|          Egenskap          |                                    Beskrivning                                    |                         Exempel                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     Unikt id för plattformen i informationslagret – surrogatnyckel.      |                           123                           |
|          Plattform          | Unikt id för plattformen, liknar PlatformKey men är en naturlig nyckel. |                           123                           |
|        PlatformName        |                                   Namn på plattform                                   | Inte tillgängligt <br>Inga <br>Windows <br>iOS <br>Android. |
| RowLastModifiedDateTimeUtc | Datum och tid i UTC för senaste ändring av plattformen i informationslagret.  |                 2016-11-23 12:00:00                  |

