---
title: Skapa en Intune-rapport från OData-feeden med Power BI
titleSuffix: Microsoft Intune
description: Skapa en trädkartevisualisering med Power BI Desktop med ett interaktivt filter från API:t för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fbbffb187fc9e9537bf647bc33e3d98879369c3
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576058"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Skapa en Intune-rapport från OData-feeden med Power BI

I den här artikeln beskrivs hur du skapar en trädkartevisualisering med ett interaktivt filter av dina Intune-data med Power BI Desktop. Din ekonomichef kanske exempelvis vill veta hur fördelningen mellan företagsägda och privata enheter ser ut. Trädkartan ger insikt i det totala antalet enhetstyper. Du kan granska antalet iOS/iPadOS-, Android- och Windows-enheter som är företagsägda eller privatägda.

## <a name="overview-of-creating-the-chart"></a>Översikt över att skapa diagrammet

För att skapa det här diagrammet ska du:
1. Installera Power BI Desktop om det inte redan har det.
2. Anslut till datamodellen Intune-informationslager och hämta aktuella data för modellen.
3. Skapa eller hantera datamodellrelationerna.
4. Skapa ett diagram med data från tabellen **enheter**.
5. Skapa ett interaktivt filter.
6. Visa det färdiga diagrammet.

### <a name="a-note-about-tables-and-entities"></a>En anteckning om tabeller och enheter

Du arbetar med tabeller i Power BI. En tabell innehåller datafält. Varje fält har en datatyp. Fältet får bara innehålla data för datatypen. Datatyper är siffror, text, datum och så vidare. Tabellerna i Power BI fylls med de senaste historiska data från din klient när du läser in modellen. Även om specifika data ändras med tiden ändras inte tabellstrukturen om inte den underliggande datamodellen uppdateras.

Du kanske blir förvirrad av användningen av termerna *entitet* och *tabell*. Datamodellen är åtkomlig via en OData-feed (Open Data Protocol). I OData kallas containrarna som i Power BI heter tabeller istället entiteter. Båda termerna avser samma sak som innehåller dina data. Om du vill veta mer om OData kan du läsa [OData-översikten](/odata/overview).

## <a name="install-power-bi-desktop"></a>Installera Power BI Desktop

Installera den senaste versionen av Power BI Desktop. Du kan ladda ned Power BI Desktop från: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Anslut till OData-feeden för klientens Intune-informationslager

> [!Note]  
> Du måste ha behörighet för **Rapporter** i Intune. Mer information finns i [Auktorisering](../reports-api-url.md).

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Öppna fönstret **Intune Data Warehouse** genom att välja Data Warehouse-länken under **Övriga uppgifter** på höger sida om bladet **Microsoft Intune – översikt**.
3. Kopiera den anpassade feed-URL:en. Exempelvis: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Öppna Power BI Desktop.
5. Välj **Arkiv** > **Hämta data** > **Odata-feed** från menyfältet.
6. Klistra in den anpassade feedadressen du kopierade från föregående steg i adressfältet i fönstret **OData-feed**.
7. Välj **Grundläggande**.

    ![OData-feeden för klientens Intune Data Warehouse](./media/reports-proc-create-with-odata/reports-create-01-odatafeed.png)

8. Välj **OK**.
9. Välj **Organisationskonto** och logga in med dina autentiseringsuppgifter för Intune.

    ![Autentisering av organisationskonto](./media/reports-proc-create-with-odata/reports-create-02-org-account.png)

10. Välj **Anslut**. Navigatören öppnas och visar listan över tabeller i Intune-informationslagret.

    ![Skärmbild av Navigator – listan över Data Warehouse-tabeller](./media/reports-proc-create-with-odata/reports-create-02-loadentities.png)

11. Markera tabellerna **enheter** och **ownerTypes**.  Välj **Läs in**. Power BI läser in data i modellen.

## <a name="create-a-relationship"></a>Skapa en relation

Du kan importera flera tabeller för att inte endast analysera data i en enda tabell utan även relaterade data i flera tabeller. Power BI har en funktion som heter **Identifiera automatiskt** som försöker hitta och skapa relationer åt dig. Tabellerna i informationslagret har skapats för att fungera med Power BI:s funktion Identifiera automatiskt. Men även om Power BI inte hittar relationerna automatiskt hanterar du fortfarande relationerna.

![Hantera relationer för relaterade data i tabeller](./media/reports-proc-create-with-odata/reports-create-03-managerelationships.png)

1. Välj **Hantera relationer**.
2. Välj **Identifiera automatiskt...** om inte Power BI redan har identifierat relationerna.

Relationerna visas i en Från-kolumn till en Till-kolumn. I det här exemplen länkar datafältet **ownerTypeKey** i tabellen **enheter** till datafältet **ownerTypeKey** i tabellen **ownerTypes**. Du använder relationen för att leta upp vanliga namn för enhetstypkoden i tabellen **enheter**.

## <a name="create-a-treemap-visualization"></a>Skapa en trädkarta-visualisering

Ett trädkarta-diagram visar hierarkiska data som rutor i rutor. Varje gren i hierarkin är en ruta som innehåller mindre rutor som visar undergrenar. Du kan använda Power BI Desktop till att skapa en trädkarta över dina Intune-klientdata som visar relativa antal enheter från olika tillverkare.

![Trädkartevisualiseringar med Power BI](./media/reports-proc-create-with-odata/reports-create-03-treemap.png)

1. Leta upp och välj **Trädkarta** i fönstret **Visualiseringar**. **Trädkartan** läggs till på rapportarbetsytan.
2. Leta upp `devices` tabellen i **fönstret** fält.
3. Expandera tabellen `devices` och välj datafältet `manufacturer`.
4. Dra data fältet till rapport arbets ytan och släpp det **i TreeMap**-diagrammet.`manufacturer`
5. `devices` Dra data fältet från tabellen till fönstret **visualiseringar** och släpp det under avsnittet **värden** i rutan med etiketten **Lägg till data fält här**. `deviceKey`  

Nu har du ett visuellt objekt som visar din organisations distribution av enheternas tillverkare.

![Trädkarta med data – distribution av tillverkare av enheter](./media/reports-proc-create-with-odata/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Lägga till ett filter

Du kan lägga till ett filter till din trädkarta så att du kan svara på fler frågor med programmet.

1. Lägg till ett filter genom att välja rapportarbetsytan och sedan **Utsnittsikonen** (![trädkarta med datamodell och relationer som stöds](./media/reports-proc-create-with-odata/reports-create-slicer.png)) under **Visualiseringar**. Den tomma **utsnittsvisualiseringen** visas på arbetsytan.
2. Leta upp `ownerTypes` tabellen i **fönstret** fält.
3. Expandera tabellen `ownerTypes` och välj datafältet `ownerTypeName`.
4. Dra datafältet `onwerTypeName` från tabellen `ownerTypes` till rutan **Filter** och släpp det under avsnittet **Filter på den här sidan** i rutan med namnet **Lägg till datafält här**.  

   Under tabellen `OwnerTypes` finns det ett datafält som heter `OwnerTypeKey` där det står om enheten är företagsägd eller privatägd. Eftersom du vill visa egna namn i det här filtret håller du utkik efter tabellen `ownerTypes` och drar **ownerTypeName**. Detta exempel visar hur datamodellen stöder relationer mellan tabeller.

![Trädkarta med filter – stöder relationer mellan tabeller](./media/reports-proc-create-with-odata/reports-create-08_ownertype.png)

Nu har du ett interaktivt filter som du kan använda för att växla mellan företagsägda och privatägda enheter. Använd det här filtret om du vill se hur distributionen ändras.

1. Välj **Företag** i utsnittet för att se fördelningen av företagsägda enheter.
2. Välj **Personlig** i utsnittet för att se de privatägda enheterna.

## <a name="next-steps"></a>Nästa steg

- Läs mer om att [skapa och hantera relationer](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) i Power BI Desktop i Power BI-dokumentationen.
- Läs informationen om [Intune-informationslagermodellen](reports-ref-data-model.md).
