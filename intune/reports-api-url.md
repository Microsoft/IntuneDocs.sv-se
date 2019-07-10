---
title: API-slutpunkt för Intune-informationslager
titleSuffix: Microsoft Intune
description: Referensavsnittet beskriver API-webbadresstrukturen för Microsoft Intune-informationslagret. Filterexempel finns.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d2e6c99d9493d935f4a8f87c6525af19796b5f6
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648788"
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

| Element | Exempel | Beskrivning |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| position | msua06 | Grundwebbadressen hittar du på bladet för informationslager-API på Azure Portal. |
| entitetssamling | datum | Namnet på OData-entitetssamlingen. Mer information om samlingar och entiteter i datamodellen finns i [Datamodell](reports-ref-data-model.md). |
| api-version | beta | Version är den API-version som ska kommas åt. Mer information finns i [Version](reports-api-url.md#api-version-information). |
| maxhistorydays | 7 | (Valfritt) Det maximala antalet dagar av historik som ska hämtas. Den här parametern kan anges till valfri samling men börjar bara gälla för samlingar som inkluderar `dateKey` som en del av sin nyckelegenskap. Mer information finns i [DateKey-intervallfilter](reports-api-url.md#datekey-range-filters). |

## <a name="api-version-information"></a>API-versionsinformation

Det går nu att använda v1.0-versionen av Intune-informationslagret genom att ange frågeparametern `api-version=v1.0`. Uppdateringar av samlingar i datalagret är additiva och avbryter inte befintliga scenarier.

Du kan testa de nya funktionerna i betaversionen av informationslagret. För att kunna använda betaversionen måste webbadressen innehålla frågeparametern `api-version=beta`. Betaversionen innehåller funktioner som ännu inte är allmänt tillgängliga som en tjänst som stöds. Allt eftersom nya funktioner läggs till i Intune kan betaversionen ändra funktionssätt och datakontrakt. Eventuell anpassad kod eller rapportverktyg som är beroende av betaversionen kan sluta att fungera på grund av pågående uppdateringar.

## <a name="odata-query-options"></a>OData-frågealternativ

Den aktuella versionen har stöd för följande OData-frågeparametrar: `$filter`, `$select`, `$skip,` och `$top`. I `$filter` kanske endast `DateKey` eller `RowLastModifiedDateTimeUTC` stöds när kolumnerna kan användas, och andra egenskaper skulle utlösa en felaktig begäran.

## <a name="datekey-range-filters"></a>DateKey-intervallfilter

`DateKey`-intervallfilter kan användas för att begränsa den mängd data som laddas ned för några av samlingarna med `dateKey` som en nyckelegenskap. `DateKey`-filtret kan användas för att optimera tjänstprestanda genom att tillhandahålla följande `$filter`-frågeparameter:

1. Enbart `DateKey` i `$filter`, som stöder operatorerna `lt/le/eq/ge/gt` och sammankopplas med logikoperatorn `and`, där de kan mappas till ett startdatum och/eller slutdatum.
2. `maxhistorydays` anges som ett anpassat frågealternativ.<br>

## <a name="filter-examples"></a>Filterexempel

> [!NOTE]
> I filterexemplen antas att dagens datum är 2019-02-21.

|                             Filter                             |           Prestandaoptimering           |                                          Beskrivning                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Fullständig                                      |    Returnera data med `DateKey` mellan 20180214 och 20180221.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Fullständig                                      |    Returnera data med `DateKey` lika med 20180214.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Fullständig                                      |    Returnera data med `DateKey` mellan 20180214 och 20180220.                                     |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Fullständig                                      |    Returnera data med `DateKey` lika med 20180214. `maxhistorydays` ignoreras.                            |
|    `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z`                                |    Fullständig                                       |    Returnera data med `RowLastModifiedDateTimeUTC` är större än eller lika med `2018-02-21T23:18:51.3277273Z`                             |
