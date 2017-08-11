---
title: "Använda Intune-informationslagret | Microsoft Docs"
description: "Använd Intune-informationslagret för att skapa rapporter som ger inblick i ditt företags mobilmiljö."
keywords: Intune-informationslager
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: db6661dd92b890d711f655a60eb883b417a30d8a
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2017
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

> [!Important]  
> Du kan testa de nya funktionerna i betaversionen av informationslagret. För att kunna använda betaversionen måste din webbadress innehålla frågeparametern `api-version=beta`. Betaversionen innehåller funktioner som ännu inte är allmänt tillgängliga som tjänst som stöds. Allt eftersom nya funktioner läggs till i Intune kan betaversionen ändra funktionssätt och datakontrakt. Eventuell anpassad kod eller rapportverktyg som är beroende av betaversionen kan sluta att fungera på grund av pågående uppdateringar. <!-- If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

**Nästa steg**

- Få en länk och använd Power BI för att få mer information. Mer information finns i [Ansluta till Intune-informationslagret med Power BI](reports-proc-get-a-link-powerbi.md).
- Mer information om API för Intune-informationslagret, datamodellen och relationerna mellan enheter<!-- , and an example of creating a custom client to retrieve data,--> finns i [API för Intune-datalagret](reports-nav-intune-date-warehouse.md).