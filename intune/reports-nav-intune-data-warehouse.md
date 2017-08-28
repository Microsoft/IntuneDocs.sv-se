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
ms.openlocfilehash: 52b498beb024b86282c93be7aa5a248800db6609
ms.sourcegitcommit: 294de4d4058de2c625abb8143e90880d27da9284
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/15/2017
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

## <a name="odata-custom-client"></a>OData anpassad klient

Du kan öppna datamodellen Intune-informationslager via RESTful-slutpunkter. För att få åtkomst till dina data måste klienten auktorisera med Microsoft Azure Active Directory (Azure AD) med hjälp av OAuth 2.0. Först måste du ställa in en webbapp och en klientapp i Azure och bevilja klienten åtkomst. Din lokala klient auktoriseras och kan sedan kommunicera med informationslagrets slutpunkter.

Mer information finns i [Hämta data från API för informationslager med en REST-klient](reports-proc-data-rest.md)

## <a name="interacting-with-the-api"></a>Interagera med API:et

API:et måste auktoriserad med Azure AD. Azure AD använder OAuth 2.0. När det har auktoriserats kan du hämta data från API:et med ett HTTP GET-verb och genom att kontakta de visade entitetssamlingarna. Mer information finns i:

 -  [Auktorisering](reports-api-url.md)
 -  [API-webbadresstruktur](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Datamodellen Intune-informationslager

OData definierar en abstrakt datamodell och ett protokoll som ger alla klienter åtkomst till information som visas av alla datakällor. I dokumentationen om datamodellen förklaras namnområden, entiteter och returobjekt i datamodellen Intune-informationslager. Mer information finns i [Datamodellen informationslager](reports-ref-data-model.md).

## <a name="next-steps"></a>Nästa steg

[Autentiseringsscenarier i Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)  
[odata.org](http://www.odata.org)  
[OData version 4.0](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  
