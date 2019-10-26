---
title: Flytta Intune-kontodata för informationslager
titleSuffix: Microsoft Intune
description: Förstå hur du säkerhetskopierar Intune-data för informationslager när du flyttar ditt konto.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: bbf9944411776e5d6f47aa59116806a0a703ce4c
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813378"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Flytta Intune-kontodata för informationslager 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Genom att begära att ett konto flyttas begär du att datacentret ändras till en annan plats. Efter överflyttningen återställs ditt informationslager och börjar registrera data på den nya platsen baserat på den angivna dagen flytten börjar. Om du vill säkerhetskopiera dina tidigare informationslagerdata, gör du följande **innan** ditt konto flyttas. De flesta informationslagertabeller behåller data i 30 dagar, så att alla dataluckor i dessa tabeller inte längre är tillgängliga 30 dagar efter att ditt konto har flyttats. Läs mer om kvarhållningsintervall för specifika tabeller i [Datamodell för informationslager](reports-ref-data-model.md). 

## <a name="back-up-your-data-warehouse-data"></a>Säkerhetskopiera dina informationslagerdata 

Om du vill säkerhetskopiera informationslagerdata måste du spara dina informationslagerdata till en *.csv*-fil med hjälp av informationslager-API:  

1. Följ processen som anges i följande artikel om du använder informationslager-API för första gången, [Hämta data från Intune informationslager-API med en REST-klient](reports-proc-data-rest.md).
2. Använd PowerShell-exemplet som heter [Få åtkomst till Intune-informationslagret med PowerShell](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell) för att hämta alla data i CSV-filer. 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Säkerhetskopiera dina trenddiagram från Azure-portalen

Vissa trenddiagram i vyn för Azure-portalen kommer att återställas. Du kan säkerhetskopiera dessa diagram genom att köra följande skript i **Graph**:   

### <a name="terms--conditions-acceptance-reports"></a>Godkännanderapporter för villkor
1. I Azure-portalen går du till **Microsoft Intune** -> **Enhetsregistrering** -> **Villkor**.
2. För varje **Villkor**, välj **Godkännanderapport** följt av **Exportera**.
3. Spara rapporten lokalt.
 
### <a name="app-protection-reports"></a>Appskyddsrapporter  
1. I Azure-portalen går du till **Microsoft Intune** -> **Klientappar** -> **Appskyddsstatus**.
2. Klicka på ikonen hämta (⤓) för att spara varje rapport.

### <a name="device-configuration-charts"></a>Enhetskonfigurationsdiagram 
1. I Azure-portalen går du till **Microsoft Intune** -> **DeviceConfiguration**.
2. Med hjälp av Microsoft [Graph-testaren](https://developer.microsoft.com/graph/graph-explorer), laddar du ned data bakom diagrammen. 
    - För distributionsstatus för alla enhetskonfigurationsprofiler för alla enheter, se [Enhetsdistributionsstatus](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content).

    - För distributionsstatus för alla enhetskonfigurationsprofiler för alla användare, se [Användardistributionsstatus](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content).

    - För profildistributionsstatus se [Ange distributionsstatus](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview).
  
    > [!NOTE]
    > Du måste ha en giltig autentiseringstoken för åtkomst till enhetskonfiguration och information om distributionsstatus.

## <a name="device-enrollment-charts"></a>Enhetsregistreringsdiagram
1. I Azure-portalen går du till **Microsoft Intune** -> **DeviceEnrollment**.
2. Med hjälp av Microsoft [Graph-testaren](https://developer.microsoft.com/graph/graph-explorer), laddar du ned data bakom diagrammen.
    - För registreringsstatus, kopiera [frågan om registreringsstatus](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content) och klistra in den i [Graph-testaren](https://developer.microsoft.com/graph/graph-explorer).
    - För de främsta registreringsfelen denna vecka kopiera [frågan om registreringsfel](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content) och klistrar in den i [Graph-testaren](https://developer.microsoft.com/graph/graph-explorer).

    > [!NOTE]
    > Du måste ha en giltig autentiseringstoken för åtkomst till enhetens registreringsdata. 

## <a name="after-a-data-warehouse-account-move"></a>Efter att ha flyttat ett informationslagerkonto

När informationslagerkontot flyttas ser du i Intune att informationslagret har återställts och dina data nu lagras på den nya platsen. Diagram och exportalternativ återställs och du ser ett meddelande som när du klickar på det omdirigerar dig till en artikel som förklarar varför diagrammen har återställts.  

## <a name="data-warehouse-move-example"></a>Exempel på en flytt av informationslager 

Kunden X begär att ett konto flyttas med start 2018-01-06. Kunden får som svar en länk till dokumentationen om vad hen behöver göra om hen vill säkerhetskopiera sina tidigare informationslagerdata. 2018-01-06 kommer informationslagret och de diagram det stödjer att återställes och börja lagra data i det nya datacentret. 

## <a name="next-steps"></a>Nästa steg

- Läs mer om [vad som är nytt i Intune varje vecka](../fundamentals/whats-new.md). Du kan också läsa mer om kommande ändringar, viktiga meddelanden om tjänsten och information om tidigare versioner.
- Läs [Microsoft Intune-bloggen](https://go.microsoft.com/fwlink/?LinkID=273882).
