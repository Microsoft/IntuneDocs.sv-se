---
title: Skapa en Intune-rapport från OData-feeden med Power BI
titleSuffix: Microsoft Intune
description: Skapa en trädkartevisualisering med Power BI Desktop med ett interaktivt filter från API:t för Intune-informationslager.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4494d5f75336f7152668cfa1bb6fa1cd1a94305c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167857"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Skapa en Intune-rapport från OData-feeden med Power BI

Den här artikeln beskriver hur du skapar en TreeMap-visualisering av dina Intune-data med hjälp av Power BI Desktop som användare ett interaktivt filter. CHEFEN kan till exempel vilja veta hur den övergripande distributionen av enheter jämförs mellan företagsägda enheter och personliga enheter. Trädkartan ger insikt i det totala antalet enhetstyper. Du kan granska antalet iOS-, Android- och Windows-enheter som är företagsägda eller privatägda.

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

Du kanske blir förvirrad av användningen av termerna *entitet* och *tabell*. Data modellen kan nås via ett OData-flöde (Open data Protocol). I OData kallas containrarna som i Power BI heter tabeller istället entiteter. Båda termerna avser samma sak som innehåller dina data. Mer information om OData finns i OData- [översikten](/odata/overview).

## <a name="install-power-bi-desktop"></a>Installera Power BI Desktop

Installera den senaste versionen av Power BI Desktop. Du kan ladda ned Power BI Desktop från: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Anslut till OData-feeden för klientens Intune-informationslager

> [!Note]  
> Du måste ha behörighet för **Rapporter** i Intune. Mer information finns i [Auktorisering](reports-api-url.md).

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Öppna fönstret **Intune Data Warehouse** genom att välja Data Warehouse-länken under **Övriga uppgifter** på höger sida om bladet **Microsoft Intune – översikt**.
3. Kopiera den anpassade feed-URL:en. Exempelvis: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Öppna Power BI Desktop.
5. Välj **Arkiv** > **Hämta data** > **OData-feed**från meny raden.
6. Klistra in den anpassade feed-URL: en som du kopierade från föregående steg i URL-rutan i **OData-matnings** fönstret.
7. Välj **Grundläggande**.

    ![OData-feeden för klientens Intune Data Warehouse](media/reports-create-01-odatafeed.png)

8. Välj **OK**.
9. Välj **Organisationskonto** och logga in med dina autentiseringsuppgifter för Intune.

    ![Autentisering av organisationskonto](media/reports-create-02-org-account.png)

10. Välj **Anslut**. Navigatören öppnas och visar listan över tabeller i Intune-informationslagret.

    ![Skärmbild av Navigator – listan över Data Warehouse-tabeller](media/reports-create-02-loadentities.png)

11. Markera tabellerna **enheter** och **ownerTypes**.  Välj **Läs in**. Power BI läser in data i modellen.

## <a name="create-a-relationship"></a>Skapa en relation

Du kan importera flera tabeller för att inte endast analysera data i en enda tabell utan även relaterade data i flera tabeller. Power BI har en funktion som heter **Identifiera automatiskt** som försöker hitta och skapa relationer åt dig. Tabellerna i informationslagret har skapats för att fungera med Power BI:s funktion Identifiera automatiskt. Men även om Power BI inte hittar relationerna automatiskt hanterar du fortfarande relationerna.

![Hantera relationer för relaterade data i tabeller](media/reports-create-03-managerelationships.png)

1. Välj **Hantera relationer**.
2. Välj **Identifiera automatiskt...** om inte Power BI redan har identifierat relationerna.

Relationerna visas i en Från-kolumn till en Till-kolumn. I det här exemplen länkar datafältet **ownerTypeKey** i tabellen **enheter** till datafältet **ownerTypeKey** i tabellen **ownerTypes**. Du använder relationen för att leta upp vanliga namn för enhetstypkoden i tabellen **enheter**.

## <a name="create-a-treemap-visualization"></a>Skapa en trädkarta-visualisering

Ett trädkarta-diagram visar hierarkiska data som rutor i rutor. Varje gren i hierarkin är en ruta som innehåller mindre rutor som visar undergrenar. Du kan använda Power BI Desktop för att skapa en träd karta över dina Intunes klient data som visar relativa mängder av enhets tillverkare.

![Trädkartevisualiseringar med Power BI](media/reports-create-03-treemap.png)

1. I fönstret **visualiseringar** letar du upp och väljer **TreeMap**. **TreeMap** -diagrammet kommer att läggas till i rapport arbets ytan.
2. Leta upp `devices` tabellen i **fönstret** fält.
3. Expandera tabellen och `manufacturer` Välj data fältet. `devices`
4. Dra data fältet till rapport arbets ytan och släpp det **i TreeMap**-diagrammet.`manufacturer`
5. `devices` Dra data fältet från tabellen till fönstret **visualiseringar** och släpp det under avsnittet **värden** i rutan med etiketten **Lägg till data fält här**. `deviceKey`  

Nu har du ett visuellt objekt som visar din organisations distribution av enheternas tillverkare.

![Trädkarta med data – distribution av tillverkare av enheter](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Lägga till ett filter

Du kan lägga till ett filter till din trädkarta så att du kan svara på fler frågor med programmet.

1. Lägg till ett filter genom att välja rapportarbetsytan och sedan **Utsnittsikonen** (![trädkarta med datamodell och relationer som stöds](media/reports-create-slicer.png)) under **Visualiseringar**. Den tomma visualiseringen av **utsnitt** kommer att visas på arbets ytan.
2. Leta upp `ownerTypes` tabellen i **fönstret** fält.
3. Expandera tabellen och `ownerTypeName` Välj data fältet. `ownerTypes`
4. Dra datafältet `onwerTypeName` från tabellen `ownerTypes` till rutan **Filter** och släpp det under avsnittet **Filter på den här sidan** i rutan med namnet **Lägg till datafält här**.  

   Under tabellen finns ett data fält med namnet `OwnerTypeKey`som innehåller data om huruvida en enhet är företagsägda eller personliga. `OwnerTypes` Eftersom du vill visa egna namn i det här filtret håller du utkik efter tabellen `ownerTypes` och drar **ownerTypeName**. Detta exempel visar hur datamodellen stöder relationer mellan tabeller.

![Trädkarta med filter – stöder relationer mellan tabeller](media/reports-create-08_ownertype.png)

Nu har du ett interaktivt filter som du kan använda för att växla mellan företagsägda och privatägda enheter. Använd det här filtret om du vill se hur distributionen ändras.

1. Välj **företag** i utsnittet för att se att företagets ägda enhets distribution.
2. Välj **personligt** i utsnittet för att se de personligt ägda enheterna.

## <a name="next-steps"></a>Nästa steg

- Läs mer om att [skapa och hantera relationer](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) i Power BI Desktop i Power BI-dokumentationen.
- Läs informationen om [Intune-informationslagermodellen](reports-ref-data-model.md).
