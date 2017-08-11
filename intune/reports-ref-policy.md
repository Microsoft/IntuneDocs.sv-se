---
title: Princip | Microsoft Docs
description: "Referensavsnitt för kategorin Princip för entitetssamlingar i API:et för Intune-informationslager."
keywords: Intune-informationslager
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D5ADB9D8-D46A-43BD-AB0F-D6927508E3F4
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6af0ff1f463c153e62f6df63ce811076c5f692f2
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-policy-entities"></a>Referens för principentiteter

Kategorin **Princip** innehåller entiteter för mobilenheter som spårar information, till exempel:

  -  Inventering av enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper  
  -  Antal enheter med tillståndet lyckades, väntar, misslyckades eller fel per dag  
  -  Antal användare med status lyckat väntande, misslyckat eller fel per dag  
  -  Sammanlagt antal enheter med status lyckat, väntande, misslyckat eller fel per dag  

## <a name="policy"></a>Princip

Entiteten **Princip** innehåller en lista över enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper. Principerna med hantering av mobilenheter (MDM) kan tilldelas en grupp i företaget.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| PolicyKey |Unik nyckel för principen i informationslagret |123 |
| PolicyId |Unikt id för principen i informationslagret |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |Namnet på principen |"Windows 10 Baseline" |
| PolicyVersion |Principversion. Varje gång principen redigeras eller ändras skapas en ny version. |1, 2, 3 |
| IsDeleted |Visar huruvida principposten har uppdaterats.  Sant: principen innehåller en ny post med uppdaterade fält. Falskt: den senaste posten för den här principen. |Sant/falskt |
| StartDateInclusiveUTC |Datum och tid i UTC när den här principen skapades i informationslagret |2016-11-23 12:00:00 |
| DeletedDateUTC |Datum och tid i UTC när IsDeleted ändrades till True |2016-11-23 12:00:00 |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC när den här principen senast ändrades i informationslagret |2016-11-23 12:00:00 |

## <a name="policytype"></a>PolicyType

Entiteten **PolicyType** innehåller en lista över typer av enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper. Principerna med hantering av mobilenheter (MDM) kan tilldelas en grupp i företaget.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| PolicyTypeId |Unikt id för principen i källsystemet |123 |
| PolicyTypeKey |Unikt id för principen i informationslagret |1 |
| PolicyTypeName |Namn på principtypen. |Windows 10-efterlevnadsprincip |

## <a name="deviceconfiguration"></a>DeviceConfiguration

Entiteten **DeviceConfigurationProfileDeviceActivity** innehåller en lista över antalet enheter med tillståndet lyckades, väntar, misslyckades eller fel per dag. Antalet visar de enhetskonfigurationsprofiler som har tilldelats entiteten. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer, ökar antalet lyckade med ett för den dagen. Om det finns två tilldelade principer för en enhet, en med tillståndet lyckades och en med tillståndet fel, ökar antalet lyckade och enheten försätts i feltillstånd. Entiteten visar hur många enheter som har en viss status vid en viss dag under de senaste 30 dagarna.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| DateKey |Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret |20160703 |
| Väntar |Antalet unika enheter i väntande läge |123 |
| Lyckades |Antalet unika enheter i väntande läge |12 |
| Fel |Antalet unika enheter med feltillstånd |10 |
| Misslyckades |Antalet unika enheter med tillståndet misslyckades |2 |

## <a name="userconfiguration"></a>UserConfiguration

Entiteten **UserConfigurationProfileDeviceActivity** innehåller en lista över antalet användare med tillståndet lyckades, väntar, misslyckades eller fel per dag. Antalet visar de enhetskonfigurationsprofiler som har tilldelats entiteten. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer ökar antalet lyckade med ett för den dagen. Om en användare har tilldelats två profiler, en med tillståndet lyckades och den andra med tillståndet fel, räknas användaren som med feltillstånd.  Entiteten **UserConfigurationProfileDeviceActivity** visar hur många användare i ett visst tillstånd en viss dag under de senaste 30 dagarna.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| DateKey |Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret |20160703 |
| Väntar |Antalet unika användare i väntande läge |123 |
| Lyckades |Antalet unika användare med tillståndet lyckades |12 |
| Fel |Antalet unika användare med feltillstånd |10 |
| Misslyckades |Antalet unika användare med tillståndet misslyckades |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

Entiteten **PolicyTypeActivity** visat det sammanlagda antalet enheter med tillståndet lyckades, väntar misslyckades eller fel. Tillståndet visas avseende enhetskonfigurationsprofil, appkonfigurationsprofil eller efterlevnadsprincip per dag.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| DateKey |Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret |20160703 |
| PolicyKey |Principnyckel, kan kopplas till princip gör att få namn på princip |Windows 10-baslinje |
| PolicyTypeKey |Typ av principnyckel, kan kopplas till principtyp gör att få namnet på principtyp |Windows10Compliance Policy |
| Väntar |Antalet unika enheter i väntande läge |123 |
| Lyckades |Antalet unika enheter med tillståndet lyckades |12 |
| Fel |Antalet unika enheter med feltillstånd |10 |
| Fail- |Antalet unika enheter med tillståndet misslyckades |2 |