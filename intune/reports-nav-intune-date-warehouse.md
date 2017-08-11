---
title: "API för Intune-informationslager  | Microsoft Docs"
description: "Du kan använda API:et för att skapa rapporter som ger information om företagets mobilmiljö."
keywords: Intune-informationslager
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5f03fd3a1557ef5d013fe695016ed0e3b119ee62
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2017
---
#  <a name="intune-data-warehouse-api"></a>API för Intune-informationslager

Med API:t för Intune-informationslagret får du tillgång till Intune-data i ett maskinläsligt format som kan användas i valfritt analysverktyg. Du kan använda API:et för att skapa rapporter som ger information om företagets mobilmiljö. API:t använder OData-protokollet som följer standardmönstret för:

  -   Sidhuvuden för begäran och svar
  -   Statuskoder
  -   HTTP-metoder
  -   Webbadresskonventioner
  -   Medietyper
  -   Nyttolastformat
  -   Frågealternativ

OData (Open Data Protocol) är en OASIS-standard (Organization for the Advancement of Structured Information Standards) som definierar bästa metod för att bygga och använda RESTful-API:er. I Intune-informationslagret används OData version 4.0.

Det här referensavsnittet innehåller en översikt över slutpunkter, HTTP-metoder som stöds, retur av nyttolastformat och dokumentation om datamodellen Intune-informationslager.

> [!Important]  
> Du kan testa de nya funktionerna i betaversionen av informationslagret. För att kunna använda betaversionen måste din webbadress innehålla frågeparametern `api-version=beta`. Betaversionen innehåller funktioner som ännu inte är allmänt tillgängliga som tjänst som stöds. Allt eftersom nya funktioner läggs till i Intune kan betaversionen ändra funktionssätt och datakontrakt. Eventuell anpassad kod eller rapportverktyg som är beroende av betaversionen kan sluta att fungera på grund av pågående uppdateringar. <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

<!-- ## OData custom client

You can access the Intune Data Warehouse data model through RESTful endpoints. To gain access to your data, your client must authorize with Microsoft Azure Active Directory (Azure AD) using OAuth 2.0. You first set up a web app and a client app in Azure, grant permissions to the client. Your local client will get authorization, can then communicate with the Data Warehouse endpoints.

For more information, see [Get data from the Data Warehouse API with a REST client](Get-data-REST.md) -->

## <a name="interacting-with-the-api"></a>Interagera med API:et

API:et måste auktoriserad med Azure AD. Azure AD använder OAuth 2.0. När det har auktoriserats kan du hämta data från API:et med ett HTTP GET-verb och genom att kontakta de visade entitetssamlingarna. Mer information finns i:

 -  [Auktorisering](reports-api-url.md)
 -  [API-webbadresstruktur](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Datamodellen Intune-informationslager

OData definierar en abstrakt datamodell och ett protokoll som ger alla klienter åtkomst till information som visas av alla datakällor. I dokumentationen om datamodellen förklaras namnområden, entiteter och returobjekt i datamodellen Intune-informationslager. Mer information finns i [Datamodellen informationslager](reports-ref-data-model.md).

## <a name="for-more-information"></a>Mer information

[Autentiseringsscenarier i Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)  
[odata.org](http://www.odata.org)  
[OData version 4.0](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  
