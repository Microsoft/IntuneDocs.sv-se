---
title: "API-slutpunkt för Intune-informationslager | Microsoft Docs"
description: Referensavsnitt om API-webbadresstrukturen.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f6aec4741e5be788f4c1fbab929afd38e2fe07e7
ms.sourcegitcommit: 1978a30ab1af0f43aa5f447690d0bbcdcb9b563b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="intune-data-warehouse-api-endpoint"></a>API-slutpunkt för Intune-informationslager

Du kan använda API:et för Intune-informationslager med ett konto som har särskilda rollbaserade åtkomstkontroller och Azure AD-autentiseringsuppgifter. Sedan kan du godkänna REST-klienten med hjälp av OAuth 2.0. Utforma slutligen en beskrivande webbadress för att anropa en informationslagerresurs.

[!INCLUDE[reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Auktorisering

I Azure Active Directory (Azure AD) används OAuth 2.0 för att du ska kunna bevilja åtkomst till webbprogram och webb-API:er i din klientorganisation. Den här vägledningen är språkoberoende och beskriver hur du skickar och tar emot HTTP-meddelanden utan att använda några av våra bibliotek med öppen källkod. OAuth 2.0-auktoriseringskodflödet beskrivs i [avsnitt 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) i OAuth 2.0-specifikationen.

Mer information finns i [Bevilja åtkomst till webbprogram med hjälp av OAuth 2.0 och Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>API-webbadresstruktur

Informationslagrets API-slutpunkter läser entiteterna för varje uppsättning. API:et har stöd för HTTP-verbet **GET** och en deluppsättning frågealternativ.

Följande format används för webbadressen för Intune:  
https://fef.{***position***}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{***entitetssamling***}?api-version={***api-version***}

Webbadressen innehåller följande element:

| Element | Exempel | Description |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| position | msua06 | Grundwebbadressen hittar du på bladet för informationslager-API på Azure Portal. |
| entitetssamling | datum | Namnet på OData-entitetssamlingen. Mer information om samlingar och entiteter i datamodellen finns i [Datamodell](reports-ref-data-model.md). |
| api-version | beta | Version är den API-version som ska kommas åt. Mer information finns i [Version](#API-version-information). |


## <a name="api-version-information"></a>API-versionsinformation

Den aktuella API-versionen är: `beta`. 

## <a name="odata-query-options"></a>OData-frågealternativ

Den aktuella versionen har stöd för följande OData-frågeparametrar: `$filter, $orderby, $select, $skip,` och `$top`.