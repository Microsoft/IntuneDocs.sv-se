---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: Intune tillhandahåller specifika rapporttyper med fokuserade vyer som innehåller konsekventa och relevanta data.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3ae06ae3f9f76d86a792721d45f8319bfe6491fd
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654234"
---
# <a name="intune-reports"></a>Intune-rapporter
Microsoft Intune-rapporter gör det möjligt för dig att övervaka hälsotillståndet och aktiviteten hos punkter i din organisation på ett mer effektivt sätt och ger även andra rapporteringsdata i Intune. Du kan till exempel se rapporter om enhetens efterlevnad, enhetens hälsotillstånd och enhetstrender. Dessutom kan du skapa anpassade rapporter för att få mer information. 

> [!NOTE]
> Ändringarna i Intune-rapporteringen distribueras gradvis över en tidsperiod för att hjälpa dig att förbereda och anpassa till den nya strukturen.

Rapport typerna är ordnade i följande fokusområden:
- **Drift** – tillhandahåller tidsbegränsade måldata som hjälper dig att fokusera och vidta åtgärder. Administratörer, ämnesexperter och supportavdelningen kommer att ha stor nytta av dessa rapporter.
- **Organisatorisk** – innehåller en bred översikt över en sammanställning, till exempel enhetshanteringstillstånd. Chefer och administratörer har stor nytta av dessa rapporter.
- **Historisk** – visar mönster och trender under en viss tidsperiod. Chefer och administratörer har stor nytta av dessa rapporter.
- **Specialist** – låter dig använda rådata för att skapa dina egna anpassade rapporter. Dessa rapporter är mycket användbara för administratörer.

Rapporteringsramverket ger en konsekvent och mer omfattande rapporteringsupplevelse. Tillgängliga rapporter innehåller följande funktioner:
- **Sök och sortera** – du kan söka efter och sortera i alla kolumner, oavsett hur stor datauppsättningen är.
- **Datasidor** – du kan söka av dina data baserat på sidor, antingen sida-vid-sida eller genom att hoppa till en speciell sida.
- **Prestanda** – du kan snabbt skapa och visa rapporter som skapats från stora klienter.
- **Exportera** – du kan snabbt exportera rapporteringsdata som skapats från stora klienter.

### <a name="who-can-access-the-data"></a>Vem som kan komma åt data?

Användare med följande behörigheter kan gå igenom loggar:

- Global administratör
- Intune Service-administratör
- Administratörer som har tilldelats en roll för Intune med behörighet **Läs**

## <a name="non-compliant-devices-report-operational"></a>Rapport över icke-kompatibla enheter (drift)
Rapporten över icke-kompatibla enheter lyfter fram data som vanligtvis används av support- eller administratörsroller för att identifiera problem och hjälpa till att åtgärda dem. De data som finns i dessa rapporter kommer i rätt tid, belyser oväntade beteenden och är underlag för åtgärder. Rapporten är tillgänglig vid sidan av arbetsbelastningen, vilket gör att rapporten över icke-kompatibla enheter kan nås utan att du behöver bläddra bort från aktiva arbetsflöden. Den här rapporten innehåller funktioner för filtrering, sökning, sidor och sortering. Du kan också öka detaljnivån för att felsöka.

Du kan visa rapporten över **icke-kompatibla enheter** med följande steg:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Övervaka** > **icke-kompatibla enheter**.

    ![Rapport över icke-kompatibla enheter](./media/intune-reports/intune-reports-02.png)

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i Azure-portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Enhetsefterlevnad** > **Inte kompatibla enheter**.

## <a name="device-compliance-report-organizational"></a>Rapport om enhetsefterlevnad (organisatorisk)
Rapporter om enhetsefterlevnad är avsedda att vara breda och ger en mer traditionell rapporteringsvy över data för att identifiera aggregerade mått. Den här rapporten är utformad för att fungera med stora datauppsättningar för att ge en helhetsbild av enhetsefterlevnaden. Till exempel visar kompatibilitetsrapport för enhetskompatibilitet alla efterlevnadsprinciper för enheter för att ge en bredare vy över dina data, oavsett hur stor datauppsättningen är. I den här rapporten visas en fullständig analys av poster utöver en praktisk visualisering av sammansatta mått. Den här rapporten kan skapas genom att använda filter och välja knappen ”Skapa rapport”. Detta uppdaterar data för att visa det senaste läget med möjlighet att visa de enskilda poster som utgör aggregerade data. Precis som de flesta rapporter i det nya ramverket kan dessa poster sorteras och genomsökas för att fokusera på den information du behöver. 

Använd följande steg för att visa en rapport över enhetens status:
1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Rapporter** för att visa rapportsammanfattningen.
3. Välj **Enhetsefterlevnad**.
4. Select the **Efterlevnadsstatus**, **Operativsystem** och **Ownership** filter för att förfina din rapport.
5. Klicka på **Skapa rapport** (eller **Skapa igen**) för att hämta aktuella data.

    ![Enhetsefterlevnadsrapport](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > Den här **Enhetsefterlevnads**rapporten innehåller en tidsstämpel för när rapporten senast skapades. 

Mer information finns i [Tvinga fram kompatibilitet för Microsoft Defender ATP med villkorlig åtkomst i Intune](~/protect/advanced-threat-protection.md).

## <a name="reports-summary"></a>Sammanfattning av rapporter 

Enhetskompatibilitetsrapporten är tillgänglig som sammanfattningsrapport i arbetsbelastningen **Rapporter**. Använd följande steg för att visa enhetskompatibilitetsrapporten:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Rapporter** för att visa rapportsammanfattningen.

    ![Sammanfattning av Intune-rapporter](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>Trendrapport för enhetsefterlevnad (historisk)
Trendrapporter för enhetsefterlevnad används sannolikt av administratörer och arkitekter för att identifiera långsiktiga trender för enhetsefterlevnad. Aggregerade data visas under en viss tidsperiod och är användbara för att fatta framtida beslut om investeringar, köra processförbättringar eller att söka efter avvikelser. Filter kan också användas för att se vissa trender. De data som anges i den här rapporten är en ögonblicksbild av det aktuella klientorganisationsläget (nära realtid). 

En trendrapport för enhetsefterlevnad kan visa trenden för enheternas efterlevnadsprinciper under en viss tidsperiod. Du kan identifiera efterlevnadstoppar inträffade och fokusera din tid och dina ansträngningar.

Du kan visa rapporten över **Trender** med följande steg:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Rapporter** > **Trender** för att visa enhetsefterlevnad som en 60-dagarstrend.

    ![Intune-trendrapport](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Azure Monitor-integrationsrapporter (specialist)
Du kan anpassa dina egna rapporter för att hämta de data du behöver. Data i dina rapporter är också tillgängliga via [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) med [Log Analytics](reports.md#log-analytics) och [Azure Monitor-arbetsböcker](reports.md#workbooks). Med dessa lösningar kan du skapa anpassade frågor, konfigurera aviseringar och utforma instrumentpaneler för att visa enhetsefterlevnadsprinciper på det sätt som du vill. Dessutom kan du behålla aktivitetsloggarna på ditt Azure Storage-konto, integrera med de rapporter som använder [verktyg för säkerhetsinformations- och händelsehantering (SIEM)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration) och korrelera rapporterna med Azure AD-aktivitetsloggar. Azure Monitor-arbetsböcker kan dessutom användas för att importera instrumentpaneler för anpassade rapporteringsbehov.

> [!NOTE]
> För komplexa rapporteringsfunktioner krävs en Azure-prenumeration.

Ett exempel på en specialistrapport skulle korrelera enhetens ägarskapsdata med plattforms registreringsdata i en anpassad rapport. Den anpassade rapporten kan sedan visas på en befintlig instrumentpanel i Azure Active Directory-portalen.

Du kan skapa och visa anpassade rapporter med hjälp av följande steg:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **rapporter** > **Diagnostikinställningar** lägg till en [diagnostisk inställning](reports.md#diagnostic-settings).

    ![Sammanfattning av Intune-rapporter](./media/intune-reports/intune-reports-04.png)

3. Klicka på **Lägg till diagnostisk inställning** för att visa fönstret **Diagnostikinställningar**. 
4. Ange ett **Namn** för diagnostikinställningarna. 
5. Välj inställningarna **Skicka till Log Analytics** och **DeviceComplianceOrg**.

    ![Sammanfattning av Intune-rapporter](./media/intune-reports/intune-reports-04a.png)

6. Klicka på **Spara**.
7. Välj sedan **Log Analytics** för att skapa och köra en ny loggfråga med [Log Analytics](reports.md#log-analytics).

   ![Log Analytics – Logfråga](./media/intune-reports/intune-reports-05.png)

8. Välj **Arbetsböcker** för att skapa eller öppna en interaktiv rapport med hjälp av [Azure Monitor-arbetsböcker](reports.md#workbooks).

   ![Arbetsböcker – interaktiva rapporter](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>Diagnostikinställningar
Varje Azure-resurs kräver en egen diagnostiskinställning. Den diagnostiska inställningen definierar följande för en resurs:

- Kategorier av loggar och måttdata som skickas till de mål som definierats i inställningen. De tillgängliga kategorierna kan variera för olika resurstyper.
- En eller flera destinationer att skicka loggarna till. Aktuella destinationer är Log Analytics-arbetsyta, Event Hubs och Azure Storage.
- Bevarandeprincip för data som lagras i Azure Storage.

En enda diagnostisk inställning kan definiera en av varje typ av destination. Om du vill skicka data till fler än en av en viss typ av mål (till exempel två olika Log Analytics-arbetsytor) skapar du flera inställningar. Varje resurs kan ha upp till fem diagnostiska inställningar.

Mer information om diagnostikinställningar finns i [Skapa diagnostisk inställning för att samla in plattformsloggar och mått i Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings).

### <a name="log-analytics"></a>Log Analytics
Log Analytics är det primära verktyget i Azure Portal för att skriva loggfrågor och analysera resultaten från frågorna interaktivt. Även om en loggfråga används någon annanstans i Azure Monitor skriver du vanligtvis och testar frågan först med Log Analytics. Mer information om hur du använder Log Analytics och skapar loggfrågor finns [Översikt över loggfrågor i Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview). 

### <a name="workbooks"></a>Arbetsböcker
Arbetsböcker kombinerar text, analysfrågor, Azure-mått och parametrar i omfattande och interaktiva rapporter. Arbetsböcker kan redigeras av andra teammedlemmar som har åtkomst till samma Azure-resurser. Mer information om arbetsböcker finns i [Azure Monitor-arbetsböcker](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks). Du kan också arbeta med och bidra till mallar för arbetsböcker. Mer information finns i [Mallar för arbetsböcker i Azure Monitor](https://go.microsoft.com/fwlink/?linkid=867045).

## <a name="next-steps"></a>Nästa steg 

Läs mer om följande tekniker:
- [Blogg – Microsoft Intune-rapporteringsramverk](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [Vad är Log Analytics?](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [Loggfrågor](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Kom igång med Log Analytics i Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Azure Monitor-arbetsböcker](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [Säkerhetsinformations- och händelsehanteringsverktyg (SIEM)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
