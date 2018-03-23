---
title: Hantering av mobila appar (MAM)
titlesuffix: Microsoft Intune
description: Referensavsnitt för kategorin Mobilappshantering för entitetssamlingar i API:et för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: eb9f63199063db34361c7d463b8cef37bb8bfa1f
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2018
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

| Egenskap | Description | Exempel |
|---------|------------|--------|
| ApplicationKey |Unikt id för MAM-appen i informationslagret. |123 |
| ApplicationName |Namn på MAM-appen. |”Word” |
| ApplicationId |Program-id för MAM-appen. |b66bc706-ffff-7437-0340-032819502773 |
| IsDeleted |Visar huruvida posten för MAM-appen har uppdaterats. <br>Sant: MAM-appen innehåller en ny post med uppdaterade fält i den här tabellen. <br>Falskt: den senaste posten för den här MAM-appen. |Sant/falskt |
| StartDateInclusiveUTC |Datum och tid i UTC när MAM-appen skapades i informationslagret. |2016-11-23 12:00:00 |
| DeletedDateUTC |Datum och tid i UTC när IsDeleted ändrades till True. |2016-11-23 12:00:00 |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC för senaste ändring av MAM-appen i informationslagret. |2016-11-23 12:00:00 |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

Entiteten **MamApplicationInstance** innehåller en lista över appar som hanteras via mobilappshantering (MAM) som enskilda instanser per användare och enhet. Alla användare och enheter i listan är skyddade, vilket betyder att det finns minst en princip för mobilappshantering kopplad till dem.

| Egenskap | Description | Exempel |
|---------|------------|--------|
| ApplicationInstanceKey |Unikt id för MAM-appinstansen i informationslagret – surrogatnyckel. |123 |
| UserId |Användar-id för den användare som har installerat den här MAM-appen. |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationInstanceId |Unikt id för MAM-appinstansen, liknar ApplicationInstanceKey,men id:t är en naturlig nyckel. |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationId |Program-id för MAM-appen |com.microsoft.groupies-daily.<IOS> |
| ApplicationVersion |Programversion för MAM-appen. |2 |
| CreatedDate |Datum då MAM-appinstansposten skapades. Värdet kan vara null. |2016-11-23 12:00:00 |
| Plattform |Plattform för den enhet där MAM-appen är installerad. |2 |
| PlatformVersion |Plattformsversion för enheten där MAM-appen är installerad. |2.2 |
| SdkVersion |SDK-version där MAM-appen är paketerad. |3.2 |
| DeviceId |Enhets-id för enheten där MAM-appen är installerad. |b66bc706-ffff-7437-0340-032819502773 |
| DeviceName |Enhetsnamn för enheten där MAM-appen är installerad. |”MyDevice” |
| IsDeleted |Visar huruvida posten för MAM-appinstansen har uppdaterats. <br>Sant: MAM-appinstansen innehåller en ny post med uppdaterade fält i den här tabellen. <br>Falskt: den senaste posten för den här MAM-appinstansen. |Sant/falskt |
| StartDateInclusiveUtc |Datum och tid i UTC när MAM-appinstansen skapades i informationslagret. |2016-11-23 12:00:00 |
| DeletedDateUtc |Datum och tid i UTC när IsDeleted ändrades till True. |2016-11-23 12:00:00 |
| RowLastModifiedDateTimeUtc |Datum och tid i UTC för senaste ändring av MAM-appinstansen i informationslagret. |2016-11-23 12:00:00 |

## <a name="mamcheckin"></a>MamCheckin

Entiteten **MamCheckin** visar data som samlas in när en hanterad mobilappinstans har checkat in på Intune-tjänsten. 

> [!Note]  
> När en appinstans checkar in flera gånger per dag lagras den i informationslagret som en enda incheckning.

| Egenskap | Description | Exempel |
|---------|------------|--------|
| DateKey |Datumnyckel när incheckningen av MAM-appen registrerades i informationslagret. | 20160703 |
| ApplicationInstanceKey |Nyckel för appinstansen som är kopplad till incheckningen av den mobilappshanterade appen. |1900-05-02 12:00:00 |
| UserKey |Nyckel för användaren som är kopplad till incheckningen av MAM-appen. |1900-01-12 12:00:00 |
| ApplicationKey |Nyckeln för den incheckade MAM-appen. |1900-01-10 12:00:00 |
| DeviceHealthKey |Nyckel för DeviceHealth som är koppla till den här incheckningen av MAM-appen. |1900-01-02 12:00:00 |
| PlatformKey |Visar plattformen för enheten som är kopplad till den här incheckningen av MAM-appen. |1900-01-01 12:00:00 |
| EffectiveAppliedPolicyKey |Visar gällande tillämpad princip som är kopplad till den här incheckade MAM-appen. En gällande tillämpad princip är en sammansättning av alla principer som är relevanta för en viss app och användare. |1900-05-02 12:00:00 |
| LastCheckInDate |Datum och tid för den senaste incheckningen av MAM-appen. Värdet kan vara null. |2016-11-23 12:00:00 |

## <a name="mamdevicehealth"></a>MamDeviceHealth

Entiteten **MamDeviceHealth** motsvarar de enheter där principer för mobilappshantering (MAM) har distribuerats även om de är jailbrokade.

| Egenskap | Description | Exempel |
|---------|------------|--------|
| DeviceHealthKey |Unikt id för enheten med tillhörande hälsostatus i informationslagret – surrogatnyckel. |1900-01-01 12:00:00 |
| DeviceHealth |Unikt id för enheten och dess tillhörande hälsostatus, liknar DeviceHealthKey men id:t är en naturlig nyckel. |1900-01-01 12:00:00 |
| DeviceHealthName |Visar enhetens status. <br>Inte tillgänglig: det finns ingen information om enheten. <br>Felfri: enheten är inte jailbrokad. <br>Ej felfri: enheten är jailbrokad. |Inte tillgänglig Felfri Ej felfri |
| RowLastModifiedDateTimeUtc |Datum och tid i UTC för senaste ändring av hälsotillståndet för mobilappshanterad enhet i informationslagret. |2016-11-23 12:00:00 |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

Entiteten **MamEffectivePolicy** innehåller en lista över gällande principer för mobilappshantering som tillämpas i din organisation. En gällande tillämpad princip är en sammansättning av alla principer som är relevanta för en viss app och användare.

| Egenskap | Description | Exempel |
|---------|------------|--------|
| EffectivePolicyKey |Unikt id för gällande mobilappshanteringsprincip informationslagret. |2 |
| RealPolicyKey |Unikt id för den mobilappshanteringsprincip som utfärdats av it-avdelningen. |1 |
| RowCreatedDateTimeUtc |Datum och tid i UTC när mobilappshanteringsprincipen skapades i informationslagret. |2016-11-23 12:00:00 |

## <a name="mamglobalapplication"></a>MamGlobalApplication

Entiteten **MamGlobalApplication** innehåller en lista över Store-appar som hanteras via mobilappshantering (MAM) utan registrering i företaget.

| Egenskap | Description | Exempel |
|---------|------------|--------|
| ApplicationKey |Unikt id för Store-appen i informationslagret, kallas även surrogatnyckeln. |123 |
| ApplicationId |Store-appens unika id. Id:t liknar ApplicationKey men är en naturlig nyckel. |com.microsoft.skydrive.<ios> |
| ApplicationName |Namn på globalt mobilappshanteringsprogram. |Skydrive |
| RowLastModifiedDateTimeUtc |Datum och tid i UTC för senaste ändring av globalt mobilappshanteringsprogram i informationslagret. |2016-11-23 12:00:00 |

## <a name="mamplatform"></a>MamPlatform

Entiteten **MamPlatform** innehåller en lista över namn på plattformar och typer där en mobilappshanterad app (MAM) har installerats.

| Egenskap | Description | Exempel |
|---------|------------|--------|
| PlatformKey |Unikt id för plattformen i informationslagret – surrogatnyckel. |123 |
| Plattform |Unikt id för plattformen, liknar PlatformKey men är en naturlig nyckel. |123 |
| PlatformName |Namn på plattform |Inte tillgängligt <br>Inga <br>Windows <br>iOS <br>Android. |
| RowLastModifiedDateTimeUtc |Datum och tid i UTC för senaste ändring av plattformen i informationslagret. |2016-11-23 12:00:00 |
