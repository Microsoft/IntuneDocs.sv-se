---
title: API-slutpunkt för Intune-informationslager
titlesuffix: Microsoft Intune
description: Referensavsnittet beskriver API-webbadresstrukturen för Intune-informationslagret.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/25/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 05251e3aeb0c290a51c378f8c67f3d55149b63dc
ms.sourcegitcommit: e6013abd9669ddd0d6449f5c129d5b8850ea88f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/25/2018
ms.locfileid: "39254509"
---
# <a name="intune-data-warehouse-api-endpoint"></a>API-slutpunkt för Intune-informationslager

Du kan använda API:et för Intune-informationslager med ett konto som har särskilda rollbaserade åtkomstkontroller och Azure AD-autentiseringsuppgifter. Sedan kan du godkänna REST-klienten med hjälp av OAuth 2.0. Utforma slutligen en beskrivande webbadress för att anropa en informationslagerresurs.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Auktorisering

I Azure Active Directory (Azure AD) används OAuth 2.0 för att du ska kunna bevilja åtkomst till webbprogram och webb-API:er i din klientorganisation. Den här vägledningen är språkoberoende och beskriver hur du skickar och tar emot HTTP-meddelanden utan att använda några bibliotek med öppen källkod. OAuth 2.0-auktoriseringskodflödet beskrivs i [avsnitt 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) i OAuth 2.0-specifikationen.

Mer information finns i [Bevilja åtkomst till webbprogram med hjälp av OAuth 2.0 och Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>API-webbadresstruktur

Informationslagrets API-slutpunkter läser entiteterna för varje uppsättning. API:et har stöd för HTTP-verbet **GET** och en deluppsättning frågealternativ.

Följande format används för webbadressen för Intune:  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> I ovanstående URL ersätter du `{location}`, `{entity-collection}`, och `{api-version}` baserat på informationen i tabellen nedan.

Webbadressen innehåller följande element:

| Element | Exempel | Description |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| position | msua06 | Grundwebbadressen hittar du på bladet för informationslager-API på Azure Portal. |
| entitetssamling | datum | Namnet på OData-entitetssamlingen. Mer information om samlingar och entiteter i datamodellen finns i [Datamodell](reports-ref-data-model.md). |
| api-version | beta | Version är den API-version som ska kommas åt. Mer information finns i [Version](#API-version-information). |
| maxhistorydays | 7 | (Valfritt) Det maximala antalet dagar av historik som ska hämtas. Den här parametern kan anges till valfri samling men börjar bara gälla för samlingar som inkluderar `dateKey` som en del av sin nyckelegenskap. Mer information finns i [DateKey-intervallfilter](reports-api-url.md#datekey-range-filters). |

## <a name="api-version-information"></a>API-versionsinformation

Den aktuella API-versionen är: `beta`. 

## <a name="odata-query-options"></a>OData-frågealternativ

Den aktuella versionen har stöd för följande OData-frågeparametrar: `$filter, $orderby, $select, $skip,` och `$top`.

## <a name="datekey-range-filters"></a>DateKey-intervallfilter

`DateKey`-intervallfilter kan användas för att begränsa den mängd data som laddas ned för några av samlingarna med `dateKey` som en nyckelegenskap. `DateKey`-filtret kan användas för att optimera tjänstprestanda genom att tillhandahålla följande `$filter`-frågeparameter:

1.  Enbart `DateKey` i `$filter`, som stöder operatorerna `lt/le/eq/ge/gt` och sammankopplas med logikoperatorn `and`, där de kan mappas till ett startdatum och/eller slutdatum.
2.  `maxhistorydays` anges som ett anpassat frågealternativ.<br>

## <a name="filter-examples"></a>Filterexempel

> [!NOTE]
> Filterexemplen antar att dagens datum är 2018-02-21.

|                             Filter                             |           Prestandaoptimering           |                                          Description                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Fullständig                                      |    Returnera data med `DateKey` mellan 20180214 och 20180221.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Fullständig                                      |    Returnera data med `DateKey` lika med 20180214.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Fullständig                                      |    Returnera data med `DateKey` mellan 20180214 och 20180220.                                     |
|    `maxhistorydays=7&$filter=Id gt 1`                            |    Delvis; Id gt 1 optimeras inte    |    Returnera data med `DateKey` mellan 20180214 och 20180221 och Id som är större än 1.             |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Fullständig                                      |    Returnera data med `DateKey` lika med 20180214. `maxhistorydays` ignoreras.                            |
|    `$filter=DateKey eq 20180214 and Id gt 1`                     |    Inga                                      |    Behandlas inte som `DateKey`-intervallfilter, och därför sker ingen prestandaökning.                              |
|    `$filter=DateKey ne 20180214`                                 |    Inga                                      |    Behandlas inte som `DateKey`-intervallfilter, och därför sker ingen prestandaökning.                              |
|    `maxhistorydays=7&$filter=DateKey eq 20180214 and Id gt 1`    |    Inga                                      |    Behandlas inte som `DateKey`-intervallfilter, och därför sker ingen prestandaökning. `maxhistorydays` ignoreras.    |
