---
title: Referens för principentiteter
titleSuffix: Microsoft Intune
description: Referensavsnitt för kategorin Princip för entitetssamlingar i API:et för Intune-informationslager.
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
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64fc1bab596715be80fd3a91c003cac1176fe787
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490272"
---
# <a name="reference-for-policy-entities"></a>Referens för principentiteter

Kategorin **principer** innehåller entiteter för mobilenheter som spårar information, till exempel:

- Inventering av enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper  
- Antal enheter med tillståndet lyckades, väntar, misslyckades eller fel per dag  
- Antal användare med status lyckat väntande, misslyckat eller fel per dag  
- Sammanlagt antal enheter med status lyckat, väntande, misslyckat eller fel per dag  

## <a name="policies"></a>policies

Entiteten **princip** innehåller en lista över enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper. Principerna med hantering av mobilenheter (MDM) kan tilldelas en grupp i företaget.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| policyKey |Unik nyckel för principen i informationslagret. |123 |
| policyId |Unikt id för principen i informationslagret. |b66bc706-ffff-7437-0340-032819502773 |
| policyName |Namnet på principen. |"Windows 10 Baseline" |
| policyVersion |Principversion. Varje gång principen redigeras eller ändras skapas en ny version. |1, 2, 3 |
| isDeleted |Visar huruvida principposten har uppdaterats.  <br>Sant: principen innehåller en ny post med uppdaterade fält. <br>Falskt: den senaste posten för den här principen. |Sant/falskt |
| startDateInclusiveUTC |Datum och tid i UTC när den här principen skapades i informationslagret. |2016-11-23 12:00:00 |
| deletedDateUTC |Datum och tid i UTC när IsDeleted ändrades till True. |2016-11-23 12:00:00 |
| rowLastModifiedDateTimeUTC |Datum och tid i UTC när den här principen senast ändrades i informationslagret. |2016-11-23 12:00:00 |

## <a name="policytypes"></a>policyTypes

Entiteten **policyType** innehåller en lista över typer av enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper. Principerna med hantering av mobilenheter (MDM) kan tilldelas en grupp i företaget.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| policyTypeId |Unikt id för principen i källsystemet. |123 |
| policyTypeKey |Unikt id för principen i informationslagret. |1 |
| policyTypeName |Namn på principtypen. |Windows 10-efterlevnadsprincip. |

## <a name="device-configuration"></a>Enhetskonfiguration

Entiteten **deviceConfigurationProfileDeviceActivity** innehåller en lista över antalet **enheter** med tillståndet lyckades, väntar, misslyckades eller fel per dag. Antalet visar de enhetskonfigurationsprofiler som har tilldelats entiteten. Om en **enhet** exempelvis har tillståndet lyckades för alla tilldelade principer ökar antalet lyckade med ett för den dagen. Om det finns två tilldelade principer för en enhet, en med tillståndet lyckades och en med tillståndet fel, ökar antalet lyckade och enheten försätts i feltillstånd. Entiteten visar hur många enheter som har en viss status vid en viss dag under de senaste 30 dagarna.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| dateKey |Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. |20160703 |
| Väntar |Antalet unika enheter i väntande läge. |123 |
| lyckades |Antalet unika enheter med tillståndet lyckades. |12 |
| fel |Antalet unika enheter med feltillstånd. |10 |
| misslyckades |Antalet unika enheter med tillståndet misslyckades. |2 |

Entiteten **deviceConfigurationProfileUserActivity** innehåller en lista över antalet **användare** med tillståndet lyckades, väntar, misslyckades eller fel per dag. Antalet visar de enhetskonfigurationsprofiler som har tilldelats entiteten. Om en **användare** exempelvis har tillståndet lyckades för alla tilldelade principer ökar antalet lyckade med ett för den dagen. Om en användare har tilldelats två profiler, en med tillståndet lyckades och den andra med tillståndet fel, räknas användaren i feltillståndet.  Entiteten **deviceConfigurationProfileUserActivity** visar hur många användare som varit i ett visst tillstånd en viss dag under de senaste 30 dagarna.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| dateKey |Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. |20160703 |
| Väntar |Antalet unika användare i väntande läge. |123 |
| lyckades |Antalet unika användare med tillståndet lyckades. |12 |
| fel |Antalet unika användare med feltillstånd. |10 |
| misslyckades |Antalet unika användare med tillståndet misslyckades. |2 |

## <a name="policytypeactivities"></a>policyTypeActivities

Entiteten **policyTypeActivity** visat det sammanlagda antalet enheter med tillståndet lyckades, väntar misslyckades eller fel. Tillståndet visas avseende enhetskonfigurationsprofil, appkonfigurationsprofil eller efterlevnadsprincip per dag.

| Egenskap  | Beskrivning | Exempel |
|---------|------------|--------|
| dateKey |dateKey när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. |20160703 |
| policyKey |policyKey, kan kopplas till en princip för att hämta policyName. |Windows 10-baslinje |
| policyTypeKey |Typ av principnyckel, kan kopplas till principtyp gör att få namnet på principtyp. |Windows 10-efterlevnadsprincip |
| Väntar |Antalet unika enheter i väntande läge. |123 |
| lyckades |Antalet unika enheter med tillståndet lyckades. |12 |
| fel |Antalet unika enheter med feltillstånd. |10 |
| misslyckades |Antalet unika enheter med tillståndet misslyckades. |2 |

## <a name="compliance-policy"></a>Efterlevnadsprincip

API-referensen för efterlevnadsprinciper innehåller entiteter som tillhandahåller statusinformation om efterlevnadsprinciper som tilldelas till enheter.

### <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities

I följande tabell sammanfattas tilldelningsstatusen för efterlevnadsprinciper för enheter. Den visar antalet enheter som finns i varje kompatibilitetstillstånd.


|Egenskap     |Beskrivning  |Exempel  |
|---------|---------|---------|
|dateKey  |Datumnyckel när sammanfattningen skapades för efterlevnadsprincipen.|20161204 |
|okänd  |Antalet enheter som är offline eller inte kunde kommunicera med Intune eller Azure AD av andra orsaker. |5|
|notApplicable      |Antalet enheter där principer för efterlevnad som tilldelats av administratören inte kan användas.|201 |
|kompatibel      |Antalet enheter som har tillämpat en eller flera principer för enhetsefterlevnad som administratören har satt upp som mål. |4083 |
|inGracePeriod      |Antalet enheter som inte är kompatibla men som är i respitperioden som angetts av administratören. |57|
|nonCompliant      |Antalet enheter som inte har tillämpat en eller flera av principerna för enhetsefterlevnad som administratören har satt upp som mål, eller där användaren inte har uppfyllt de principer administratören har satt upp som mål.|43 |
|fel      |Antalet enheter som inte kunde kommunicera med Intune eller Azure AD och returnerade ett felmeddelande. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities 

I följande tabell sammanfattas tilldelningsstatus för efterlevnadsprinciper för enheter per princip och per principtyp. Den visar antalet enheter som finns efter kompatibilitetstillstånd för varje tilldelad efterlevnadsprincip.



|Egenskap  |Beskrivning  |Exempel  |
|---------|---------|---------|
|dateKey  |Datumnyckel när sammanfattningen skapades för efterlevnadsprincipen.|20161219|
|policyKey     |Nyckel för efterlevnadsprincipen som sammanfattningen skapades för. |10178 |
|policyPlatformKey      |Nyckel för plattformstypen för efterlevnadsprincipen som sammanfattningen skapades för.|5|
|okänd     |Antalet enheter som är offline eller inte kunde kommunicera med Intune eller Azure AD av andra orsaker.|13|
|notApplicable     |Antalet enheter där principer för efterlevnad som tilldelats av administratören inte kan användas.|3|
|kompatibel      |Antalet enheter som har tillämpat en eller flera principer för enhetsefterlevnad som administratören har satt upp som mål. |45|
|inGracePeriod      |Antalet enheter som inte är kompatibla men som är i respitperioden som angetts av administratören. |3|
|nonCompliant      |Antalet enheter som inte har tillämpat en eller flera av principerna för enhetsefterlevnad som administratören har satt upp som mål, eller där användaren inte har uppfyllt de principer administratören har satt upp som mål.|7|
|fel      |Antalet enheter som inte kunde kommunicera med Intune eller Azure AD och returnerade ett felmeddelande. |3|

### <a name="policyplatformtypes"></a>policyPlatformTypes

Följande tabell innehåller plattformstyper för alla tilldelade principer. Principer för plattformstyper som aldrig har tilldelats till några enheter visas inte i den här tabellen.


|Egenskap  |Beskrivning  |Exempel  |
|---------|---------|---------|
|policyPlatformTypeKey      |Den unika nyckeln för principplattformstypen. |20170519 |
|policyPlatformTypeId      |Den unika identifieraren för principplattformstypen.|1|
|policyPlatformTypeName      |Namnet för principplattformstypen.|AndroidForWork |

### <a name="policydeviceactivities"></a>policyDeviceActivities

Följande tabell visar antalet enheter med tillståndet lyckades, väntar, misslyckades eller fel per dag. Siffran återger data per principtypprofil. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer, ökar antalet lyckade med ett för den dagen. Om det finns två tilldelade principer för en enhet, en med tillståndet lyckades och en med tillståndet fel, ökar antalet lyckade och enheten försätts i feltillstånd. Entiteten policyDeviceActivity visar en lista över hur många enheter som har ett visst tillstånd under en viss dag de senaste 30 dagarna.

|Egenskap  |Beskrivning  |Exempel  |
|---------|---------|---------|
|dateKey|Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret.|20160703|
|Väntar|Antalet unika enheter i väntande läge.|123|
|Lyckades|Antalet unika enheter med tillståndet lyckades.|12|
|policyKey|policyKey, kan kopplas till en princip för att hämta policyName.|Windows 10-baslinje|
|fel|Antalet unika enheter med feltillstånd.|10|
|misslyckades|Antalet unika enheter med tillståndet misslyckades.|2|

### <a name="policyuseractivities"></a>policyUserActivities

Följande tabell visar antalet användare med tillståndet lyckades, väntar, misslyckades eller fel per dag. Siffran återger data per principtypprofil. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer ökar antalet lyckade med ett för den dagen. Om en användare har tilldelats två profiler, en med tillståndet lyckades och den andra med tillståndet fel, räknas användaren i feltillståndet. Entiteten PolicyUserActivity visar hur många användare som har en viss status vid en viss dag under de senaste 30 dagarna.


| Egenskap  |                                         Beskrivning                                         |       Exempel       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  dateKey  | Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. |      20160703       |
|  Väntar  |                         Antalet unika enheter i väntande läge.                          |         123         |
| lyckades |                         Antalet unika enheter med tillståndet lyckades.                          |         12          |
| policyKey |                 policyKey, kan kopplas till en princip för att hämta policyName.                 | Windows 10-baslinje |
|   fel   |                          Antalet unika enheter med feltillstånd.                           |         10          |

