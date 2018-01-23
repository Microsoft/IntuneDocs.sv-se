---
title: "Använda Intune-informationslagret | Microsoft Docs"
description: "Använd Intune-informationslagret för att skapa rapporter som ger inblick i ditt företags mobilmiljö."
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 910d279b57c885040d2ad092e460d3e7ca71090e
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/16/2018
---
# <a name="use-the-intune-data-warehouse"></a>Använda Intune-informationslagret

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd Intune-informationslagret för att skapa rapporter som ger inblick i företagets mobilmiljö. Några rapporter innehåller exempelvis:
-   Trend för användarnas registrering i Intune så att du kan optimera licensinköpen
-   Information på detaljnivå om app- och operativsystemversioner så att du kan granska status för mobila enheter
-   Trender för registrering och regelefterlevnad för enheter så att du smidigt kan rulla ut principuppdateringar

Informationslagret ger dig tillgång till mer information om din mobila miljö än Azure Portal. Med Intune-informationslagret får du tillgång till:

  -  Tidigare Intune-data
  -  Dagsaktuella data
  -  En datamodell som använder OData-standarden

> [!Note]
> Om du använder hantering av mobila hybridenheter (MDM) med System Center Configuration Manager och Microsoft Intune kan du hämta data från SCCM. Intune-informationslagret innehåller endast Intune-data. Du kan använda en SCCM Power BI-instrumentpanel för anpassade rapporter. Mer information finns i ”[Announcing the Power BI solution template for System Center Configuration Manager]( https://powerbi.microsoft.com/blog/sccm-solution-template)” (Meddelande om Power BI-lösningsmallen för System Center Configuration Manager). och ”[Create a Power BI report and dashboard](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/create-powerbi-report-dashboard)” (Skapa en Power BI-rapport och -instrumentpanel).


> [!Important]  
> Du kan testa de nya funktionerna i betaversionen av informationslagret. För att kunna använda betaversionen måste din webbadress innehålla frågeparametern `api-version=beta`. Betaversionen innehåller funktioner som ännu inte är allmänt tillgängliga som tjänst som stöds. Allt eftersom nya funktioner läggs till i Intune kan betaversionen ändra funktionssätt och datakontrakt. Eventuell anpassad kod eller rapportverktyg som är beroende av betaversionen kan sluta att fungera på grund av pågående uppdateringar.

**Nästa steg**

- Få en länk och använd Power BI för att få mer information. Mer information finns i [Ansluta till Intune-informationslagret med Power BI](reports-proc-get-a-link-powerbi.md).
- Med länken skapar du en anpassad rapport med Power BI. Det finns anvisningar i [Skapa en rapport från OData-feeden med Power BI](reports-proc-create-with-odata.md).
- Mer information om API för Intune-informationslagret, datamodellen och relationerna mellan enheter<!-- , and an example of creating a custom client to retrieve data,--> finns i [API för Intune-datalagret](reports-nav-intune-data-warehouse.md).