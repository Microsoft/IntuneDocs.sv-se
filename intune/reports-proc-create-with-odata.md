---
title: Skapa en rapport från OData-feeden med Power BI
titlesuffix: Microsoft Intune
description: Skapa en trädkartevisualisering med Power BI Desktop med ett interaktivt filter från API:t för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 9c93554fd6750459aacc154165e7a58e160534fb
ms.sourcegitcommit: 1c9ef5cfac2fc024528d2cfc9d590fa68dd58080
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429720"
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>Skapa en rapport från OData-feeden med Power BI

I artikeln beskrivs hur man skapar en trädkartevisualisering med Power BI Desktop och ett interaktivt filter. Din ekonomichef kanske exempelvis vill veta den övergripande distributionen av enheter ser ut – företagsägda jämfört med privata enheter. Trädkartan ger insikt i det totala antalet enhetstyper. Du kan granska antalet iOS-, Android- och Windows-enheter som är företagsägda eller privatägda.

### <a name="overview-of-creating-the-chart"></a>Översikt över att skapa diagrammet

För att kunna skapa det här diagrammet måste du:
1. Installera Power BI Desktop om det inte redan har det.
2. Anslut till datamodellen Intune-informationslager och hämta aktuella data för modellen.
3. Skapa eller hantera datamodellrelationerna.
4. Skapa ett diagram med data från tabellen **enheter**.
5. Skapa ett interaktivt filter.
6. Visa det färdiga diagrammet.

### <a name="a-note-about-tables-and-entities"></a>En anteckning om tabeller och enheter

Du arbetar med tabeller i Power BI. En tabell innehåller datafält. Varje fält har en datatyp. Fältet får bara innehålla data för datatypen. Datatyper är siffror, text, datum och så vidare. Tabellerna i Power BI fylls med de senaste historiska data från din klient när du läser in modellen. Även om specifika data ändras med tiden ändras inte tabellstrukturen om inte den underliggande datamodellen uppdateras.

Du kanske blir förvirrad av användningen av termerna _entitet_ och _tabell_. Datamodellen är åtkomlig via en OData-feed. I OData kallas containrarna som i Power BI heter tabeller istället entiteter. Båda termerna avser samma sak som innehåller dina data.

## <a name="install-power-bi-desktop"></a>Installera Power BI Desktop

Installera den senaste versionen av Power BI Desktop. Du kan ladda ned Power BI Desktop från: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Anslut till OData-feeden för klientens Intune-informationslager

> [!Note]  
> Du måste ha behörighet för **Rapporter** i Intune. Mer information finns i [Auktorisering](reports-api-url.md).

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Öppna fönstret **Intune-informationslager**.
4. Kopiera den anpassade feed-URL:en. Exempelvis: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
5. Öppna Power BI Desktop.
6. Välj **Hämta data** > **Odata-feed**.
7. Klistra in den anpassade feed-URL:en i URL-rutan i fönstret **OData feed** (OData-feed).
8. Välj **Grundläggande**.

    ![OData-feed](media/reports-create-01-odatafeed.png)

9. Välj **OK**.
10. Välj **Organisationskonto** och logga in med dina autentiseringsuppgifter för Intune.

    ![Autentisering av organisationskonto](media/reports-create-02-org-account.png)

11. Välj **Anslut**. Navigatören öppnas och visar listan över tabeller i Intune-informationslagret.

    ![Navigatör](media/reports-create-02-loadentities.png)

12. Markera tabellerna **enheter** och **ownerTypes**.  Välj **Läs in**. Power BI läser in data i modellen.

## <a name="create-a-relationship"></a>Skapa en relation

Du kan importera flera tabeller för att inte endast analysera data i en enda tabell utan även relaterade data i flera tabeller.  PowerBI har en funktion som heter **Identifiera automatiskt** som försöker hitta och skapa relationer åt dig. Tabellerna i informationslagret har skapats för att fungera med PowerBI:s funktion Identifiera automatiskt. Men även om PowerBI inte hittar relationerna automatiskt hanterar du fortfarande relationerna.

![Hantera relationer](media/reports-create-03-managerelationships.png)

1. Välj **Hantera relationer**.
2. Välj **Identifiera automatiskt...** om inte PowerBI redan har identifierat relationerna.

Relationerna visas i en Från-kolumn till en Till-kolumn. I det här exemplen länkar datafältet **ownerTypeKey** i tabellen **enheter** till datafältet **ownerTypeKey** i tabellen **ownerTypes**. Du använder relationen för att leta upp vanliga namn för enhetstypkoden i tabellen **enheter**.

## <a name="create-a-treemap-visualization"></a>Skapa en trädkarta-visualisering

Ett trädkarta-diagram visar hierarkiska data som rutor i rutor. Varje gren i hierarkin är en ruta som innehåller mindre rutor som visar undergrenar. Du kan använda Power BI Desktop för att skapa en trädkarta över dina Intune-data.

![Visualiseringar > trädkarta](media/reports-create-03-treemap.png)

1. Välj en diagramtyp. Välj **Trädkarta**.
2. Leta reda på tabellen **enheter** i datamodellen.
3. Expandera **enhetstabellen** och välj datafältet för **tillverkare** i fönstret **Fält**.
4. Dra **tillverkardatafältet** till trädkartediagrammet på rapportarbetsytan.
5. Dra datafältet **deviceKey** från **enhetstabellen** till avsnittet **Värden** i fönstret **Visualiseringar** och släpp det i rutan **Dra datafält hit**.  

Nu har du ett visuellt objekt som visar din organisations distribution av enheternas tillverkare.

![Trädkarta med data](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Lägga till ett filter

Du kan lägga till ett filter till din trädkarta så att du kan svara på fler frågor med programmet.


1. Lägg till ett filter genom att välja rapportarbetsytan och sedan **Utsnittsikonen** (![trädkarta med datamodell och relationer som stöds](media/reports-create-slicer.png)) under **Visualiseringar**.
2. Leta reda på tabellen **ownerTypes** och dra datafältet **ownerTypeName** under avsnittet **Filter** i panelen **Visualiseringar**.  

   Under enhetstabellen finns det ett datafält som heter **OwnerTypeKey** som innehåller en kod som anger om enhet är företagsägd eller privatägd. Eftersom du vill visa egna namn i det här filtret håller du utkik efter tabellen **ownerTypes** och drar **ownerTypeName**. Detta exempel visar hur datamodellen stöder relationer mellan tabeller.

![Trädkarta med filter](media/reports-create-08_ownertype.png)

Nu har du ett interaktivt filter som du kan använda för att växla mellan företagsägda och privatägda enheter. Använd det här filtret om du vill se hur distributionen ändras.

1. Välj **Företag** för att se den företagsägda enhetens distribution.
2. Välj **Personlig** för att se de privatägda enheterna.

## <a name="next-steps"></a>Nästa steg

 - Läs mer om att [skapa och hantera relationer](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) i Power BI Desktop i Power BI-dokumentationen.
 - Läs informationen om [Intune-informationslagermodellen](https://docs.microsoft.com/intune/reports-ref-data-model).
