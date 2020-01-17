---
title: Använda Intune-informationslagret
titleSuffix: Microsoft Intune
description: Använd Intune-informationslagret för att skapa rapporter som ger inblick i företagets mobilmiljö.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 58c4db1f4c778050bc91bde79494742e018f5329
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547907"
---
# <a name="use-the-microsoft-intune-data-warehouse"></a>Använda Microsoft Intune-informationslager

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Använd Intune-informationslagret för att skapa rapporter som ger inblick i företagets mobilmiljö. Några rapporter innehåller exempelvis:
- Trend för användarnas registrering i Intune så att du kan optimera licensinköpen
- Information på detaljnivå om app- och operativsystemversioner så att du kan granska status för mobila enheter
- Trender för registrering och regelefterlevnad för enheter så att du smidigt kan rulla ut principuppdateringar

## <a name="data-warehouse-benefits"></a>Fördelar med informationslager

Informationslagret ger dig tillgång till mer information om din mobila miljö än Azure Portal. Med Intune-informationslagret får du tillgång till:

- Tidigare Intune-data
- Dagsaktuella data
- En datamodell som använder OData-standarden

> [!Note]
> Om du använder samhanterad hantering av mobilenheter (MDM) med Microsoft Endpoint Configuration Manager och Microsoft Intune behöver du hämta data från Configuration Manager. Intune-informationslagret innehåller endast Intune-data. Du kan använda en Power BI-instrumentpanel med Configuration Manager för anpassade rapporter. Mer information finns i ”[Meddelande om Power BI-lösningsmallen för Configuration Manager](https://powerbi.microsoft.com/blog/sccm-solution-template)” och ”[Power BI-innehåll för Dynamics 365](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/power-bi-home-page)”.

> [!Important]  
> Det går nu att använda v1.0-versionen av Intune-informationslagret genom att ange frågeparametern `api-version=v1.0`. Uppdateringar av samlingar i datalagret är additiva och avbryter inte befintliga scenarier.<br><br>
> Du kan testa de nya funktionerna i betaversionen av informationslagret. För att kunna använda betaversionen måste webbadressen innehålla frågeparametern `api-version=beta`. Betaversionen innehåller funktioner som ännu inte är allmänt tillgängliga som en tjänst som stöds. Allt eftersom nya funktioner läggs till i Intune kan betaversionen ändra funktionssätt och datakontrakt. Eventuell anpassad kod eller rapportverktyg som är beroende av betaversionen kan sluta att fungera på grund av pågående uppdateringar.

## <a name="next-steps"></a>Nästa steg

- Få en länk och använd Power BI för att få mer information. Mer information finns i [Ansluta till Intune-informationslagret med Power BI](reports-proc-get-a-link-powerbi.md).
- Med länken skapar du en anpassad rapport med Power BI. Det finns anvisningar i [Skapa en rapport från OData-feeden med Power BI](reports-proc-create-with-odata.md).
- Mer information om API:et för Intune-informationslagret, datamodellen och relationerna mellan enheter<!-- , and an example of creating a custom client to retrieve data,--> finns i [API för Intune-informationslager](reports-nav-intune-data-warehouse.md).
