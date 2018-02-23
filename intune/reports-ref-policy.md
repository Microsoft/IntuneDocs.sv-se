---
title: Princip | Microsoft Docs
description: "Referensavsnitt för kategorin Princip för entitetssamlingar i API:et för Intune-informationslager."
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/12/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab8393f3792611001d15fe4eb031225587126251
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/15/2018
---
# <a name="reference-for-policy-entities"></a>Referens för principentiteter

Kategorin **Princip** innehåller entiteter för mobilenheter som spårar information, till exempel:

  -  Inventering av enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper  
  -  Antal enheter med tillståndet lyckades, väntar, misslyckades eller fel per dag  
  -  Antal användare med status lyckat väntande, misslyckat eller fel per dag  
  -  Sammanlagt antal enheter med status lyckat, väntande, misslyckat eller fel per dag  

## <a name="policy"></a>Princip

Entiteten **Princip** innehåller en lista över enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper. Principerna med hantering av mobilenheter (MDM) kan tilldelas en grupp i företaget.

| Egenskap  | Description | Exempel |
|---------|------------|--------|
| PolicyKey |Unik nyckel för principen i informationslagret. |123 |
| PolicyId |Unikt id för principen i informationslagret. |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |Namnet på principen. |"Windows 10 Baseline" |
| PolicyVersion |Principversion. Varje gång principen redigeras eller ändras skapas en ny version. |1, 2, 3 |
| IsDeleted |Visar huruvida principposten har uppdaterats.  <br>Sant: principen innehåller en ny post med uppdaterade fält. <br>Falskt: den senaste posten för den här principen. |Sant/falskt |
| StartDateInclusiveUTC |Datum och tid i UTC när den här principen skapades i informationslagret. |2016-11-23 12:00:00 |
| DeletedDateUTC |Datum och tid i UTC när IsDeleted ändrades till True. |2016-11-23 12:00:00 |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC när den här principen senast ändrades i informationslagret. |2016-11-23 12:00:00 |

## <a name="policytype"></a>PolicyType

Entiteten **PolicyType** innehåller en lista över typer av enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper. Principerna med hantering av mobilenheter (MDM) kan tilldelas en grupp i företaget.

| Egenskap  | Description | Exempel |
|---------|------------|--------|
| PolicyTypeId |Unikt id för principen i källsystemet. |123 |
| PolicyTypeKey |Unikt id för principen i informationslagret. |1 |
| PolicyTypeName |Namn på principtypen. |Windows 10-efterlevnadsprincip. |

## <a name="deviceconfiguration"></a>DeviceConfiguration

Entiteten **DeviceConfigurationProfileDeviceActivity** innehåller en lista över antalet enheter med tillståndet lyckades, väntar, misslyckades eller fel per dag. Antalet visar de enhetskonfigurationsprofiler som har tilldelats entiteten. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer, ökar antalet lyckade med ett för den dagen. Om det finns två tilldelade principer för en enhet, en med tillståndet lyckades och en med tillståndet fel, ökar antalet lyckade och enheten försätts i feltillstånd. Entiteten visar hur många enheter som har en viss status vid en viss dag under de senaste 30 dagarna.

| Egenskap  | Description | Exempel |
|---------|------------|--------|
| DateKey |Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. |20160703 |
| Väntar |Antalet unika enheter i väntande läge. |123 |
| Lyckades |Antalet unika enheter med tillståndet lyckades. |12 |
| Fel |Antalet unika enheter med feltillstånd. |10 |
| Misslyckades |Antalet unika enheter med tillståndet misslyckades. |2 |



Entiteten **DeviceConfigurationProfileUserActivity** innehåller en lista över antalet användare med tillståndet lyckades, väntar, misslyckades eller fel per dag. Antalet visar de enhetskonfigurationsprofiler som har tilldelats entiteten. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer ökar antalet lyckade med ett för den dagen. Om en användare har tilldelats två profiler, en med tillståndet lyckades och den andra med tillståndet fel, räknas användaren i feltillståndet.  Entiteten **DeviceConfigurationProfileUserActivity** visar hur många användare som varit i ett visst tillstånd en viss dag under de senaste 30 dagarna.

| Egenskap  | Description | Exempel |
|---------|------------|--------|
| DateKey |Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. |20160703 |
| Väntar |Antalet unika användare i väntande läge. |123 |
| Lyckades |Antalet unika användare med tillståndet lyckades. |12 |
| Fel |Antalet unika användare med feltillstånd. |10 |
| Misslyckades |Antalet unika användare med tillståndet misslyckades. |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

Entiteten **PolicyTypeActivity** visat det sammanlagda antalet enheter med tillståndet lyckades, väntar misslyckades eller fel. Tillståndet visas avseende enhetskonfigurationsprofil, appkonfigurationsprofil eller efterlevnadsprincip per dag.

| Egenskap  | Description | Exempel |
|---------|------------|--------|
| DateKey |Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. |20160703 |
| PolicyKey |Principnyckel, kan kopplas till princip gör att få namn på princip. |Windows 10-baslinje |
| PolicyTypeKey |Typ av principnyckel, kan kopplas till principtyp gör att få namnet på principtyp. |Windows 10-efterlevnadsprincip |
| Väntar |Antalet unika enheter i väntande läge. |123 |
| Lyckades |Antalet unika enheter med tillståndet lyckades. |12 |
| Fel |Antalet unika enheter med feltillstånd. |10 |
| Misslyckades |Antalet unika enheter med tillståndet misslyckades. |2 |

## <a name="compliance-policy"></a>Efterlevnadsprincip

API-referensen för efterlevnadsprinciper innehåller entiteter som tillhandahåller statusinformation om efterlevnadsprinciper som tilldelas till enheter.

### <a name="compliancepolicystatusdeviceactivities"></a>CompliancePolicyStatusDeviceActivities

I följande tabell sammanfattas tilldelningsstatusen för efterlevnadsprinciper för enheter. Den visar antalet enheter som finns i varje kompatibilitetstillstånd.


|Egenskap     |Description  |Exempel  |
|---------|---------|---------|
|DateKey  |Datumnyckel när sammanfattningen skapades för efterlevnadsprincipen.|20161204 |
|Okänt  |Antalet enheter som är offline eller inte kunde kommunicera med Intune eller Azure AD av andra orsaker. |5|
|NotApplicable      |Antalet enheter där principer för efterlevnad som tilldelats av administratören inte kan användas.|201 |
|Kompatibel      |Antalet enheter som har tillämpat en eller flera principer för enhetsefterlevnad som administratören har satt upp som mål. |4083 |
|InGracePeriod      |Antalet enheter som inte är kompatibla men som är i respitperioden som angetts av administratören. |57|
|NonCompliant      |Antalet enheter som inte har tillämpat en eller flera av principerna för enhetsefterlevnad som administratören har satt upp som mål, eller där användaren inte har uppfyllt de principer administratören har satt upp som mål.|43 |
|Fel      |Antalet enheter som inte kunde kommunicera med Intune eller Azure AD och returnerade ett felmeddelande. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>CompliancePolicyStatusDevicePerPolicyActivities 

I följande tabell sammanfattas tilldelningsstatus för efterlevnadsprinciper för enheter per princip och per principtyp. Den visar antalet enheter som finns efter kompatibilitetstillstånd för varje tilldelad efterlevnadsprincip.



|Egenskap  |Description  |Exempel  |
|---------|---------|---------|
|DateKey  |Datumnyckel när sammanfattningen skapades för efterlevnadsprincipen.|20161219|
|PolicyKey     |Nyckel för efterlevnadsprincipen som sammanfattningen skapades för. |10178 |
|PolicyPlatformKey      |Nyckel för plattformstypen för efterlevnadsprincipen som sammanfattningen skapades för.|5|
|Okänt     |Antalet enheter som är offline eller inte kunde kommunicera med Intune eller Azure AD av andra orsaker.|13|
|NotApplicable     |Antalet enheter där principer för efterlevnad som tilldelats av administratören inte kan användas.|3|
|Kompatibel      |Antalet enheter som har tillämpat en eller flera principer för enhetsefterlevnad som administratören har satt upp som mål. |45|
|InGracePeriod      |Antalet enheter som inte är kompatibla men som är i respitperioden som angetts av administratören. |3|
|NonCompliant      |Antalet enheter som inte har tillämpat en eller flera av principerna för enhetsefterlevnad som administratören har satt upp som mål, eller där användaren inte har uppfyllt de principer administratören har satt upp som mål.|7|
|Fel      |Antalet enheter som inte kunde kommunicera med Intune eller Azure AD och returnerade ett felmeddelande. |3|

### <a name="policyplatformtypes"></a>PolicyPlatformTypes

Följande tabell innehåller plattformstyper för alla tilldelade principer. Principer för plattformstyper som aldrig har tilldelats till några enheter visas inte i den här tabellen.


|Egenskap  |Description  |Exempel  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |Den unika nyckeln för principplattformstypen. |20170519 |
|PolicyPlatformTypeId      |Den unika identifieraren för principplattformstypen.|1|
|PolicyPlatformTypeName      |Namnet för principplattformstypen.|AndroidForWork |

### <a name="policydeviceactivity"></a>PolicyDeviceActivity

Följande tabell visar antalet enheter med tillståndet lyckades, väntar, misslyckades eller fel per dag. Siffran återger data per principtypprofil. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer, ökar antalet lyckade med ett för den dagen. Om det finns två tilldelade principer för en enhet, en med tillståndet lyckades och en med tillståndet fel, ökar antalet lyckade och enheten försätts i feltillstånd. Entiteten PolicyDeviceActivity visar hur många enheter som har en viss status vid en viss dag under de senaste 30 dagarna.

|Egenskap  |Description  |Exempel  |
|---------|---------|---------|
|DateKey|Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret.|20160703|
|Väntar|Antalet unika enheter i väntande läge.|123|
|Lyckades|Antalet unika enheter med tillståndet lyckades.|12|
PolicyKey|Principnyckel, kan kopplas till princip gör att få namn på princip.|Windows 10-baslinje|
|Fel|Antalet unika enheter med feltillstånd.|10|
|Misslyckades|Antalet unika enheter med tillståndet misslyckades.|2|

### <a name="policyuseractivity"></a>PolicyUserActivity 

Följande tabell visar antalet användare med tillståndet lyckades, väntar, misslyckades eller fel per dag. Siffran återger data per principtypprofil. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer ökar antalet lyckade med ett för den dagen. Om en användare har tilldelats två profiler, en med tillståndet lyckades och den andra med tillståndet fel, räknas användaren i feltillståndet. Entiteten PolicyUserActivity visar hur många användare som har en viss status vid en viss dag under de senaste 30 dagarna.

|Egenskap  |Description  |Exempel  |
|---------|---------|---------|
|DateKey|Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret.|20160703|
|Väntar|Antalet unika enheter i väntande läge.|123|
|Lyckades|Antalet unika enheter med tillståndet lyckades.|12|
PolicyKey|Principnyckel, kan kopplas till princip gör att få namn på princip.|Windows 10-baslinje|
|Fel|Antalet unika enheter med feltillstånd.|10|
