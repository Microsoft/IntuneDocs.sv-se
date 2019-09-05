---
title: Dirigera loggar till Azure Monitor med hjälp av Microsoft Intune – Azure | Microsoft Docs
description: Använd diagnostikinställningar för att skicka gransknings- och driftloggar i Microsoft Intune till Azure storage-konto, händelsehubbar eller logganalys. Välj hur länge du vill behålla data och se några beräknade kostnader för olika storlek på klienter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ed32ad564f850c06b37b15e1994ac066a929ffaa
ms.sourcegitcommit: cf40f641af4746a1e34edd980dc6ec96fd040126
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122419"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Skicka data till lagring, händelsehubbar eller logganalys i Intune (förhandsversion)

Microsoft Intune innehåller inbyggda loggar med information om din miljö:

- **Granskningsloggar** visar information om olika händelser eller aktiviteter som sker i Intune.
- **Arbetsloggar (förhandsversion)** visar information om användare och enheter som har registrerats korrekt (eller misslyckats) samt information om icke-kompatibla enheter.
- **Organisationsloggar för enhetsefterlevnad (förhandsversion)** visar en organisationsrapport för enhetsefterlevnad i Intune samt information om icke-kompatibla enheter.

Dessa loggar kan också skickas till Azure Monitor-tjänster, inklusive lagringskonton, händelsehubbar och logganalyser. Mer specifikt kan du:

* Arkivera Intune-loggarna till ett Azure storage-konto för att behålla data eller arkivera under en viss tid.
* Strömma Intune-loggar till en Azure-händelsehubb för analys med hjälp av populära verktyg för säkerhetsinformation och händelsehantering (SIEM), till exempel Splunk och QRadar.
* Integrera Intune-loggarna med dina egna anpassade logglösningar genom att strömma dem till en händelsehubb.
* Skicka Intune-loggarna till Log Analytics för att aktivera kraftfulla visualiseringar, övervakning och avisering för anslutna data.

Dessa funktioner är en del av **diagnostikinställningarna** i Intune.

Den här artikeln visar hur du använder **diagnostikinställningar** för att skicka data till olika tjänster, ger exempel och uppskattade kostnader och innehåller några vanliga frågor och svar. När du aktiverar den här funktionen dirigeras dina loggar till den Azure Monitor-tjänst som du väljer.

## <a name="prerequisites"></a>Krav

För att använda funktionen behöver du:

* An Azure-prenumeration: Om du inte har en Azure-prenumeration [kan du registrera dig för en kostnadsfri utvärdering](https://azure.microsoft.com/free/).
* En Microsoft Intune-miljö (klient) i Azure
* En användare som är **Global administratör** eller **Intune-tjänstadministratör** för Intune-klienten.

Beroende på var du vill dirigera granskningsloggdata, behöver du någon av följande tjänster:

* Ett [Azure storage-konto](https://docs.microsoft.com/azure/storage/common/storage-account-overview) med behörigheter för *Listnycklar*. Vi rekommenderar att du använder ett allmänt lagringskonto och inte ett blob-lagringskonto. Information om lagringspriser hittar du i [Priskalkylatorn för Azure Storage](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* En [namnrymd för Azure-händelshubbar](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) för att integrera med lösningar från tredje part.
* En [arbetsyta för Azure-logganalyser](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) för att skicka loggar till Log Analytics.

## <a name="send-logs-to-azure-monitor"></a>Skicka loggar till Azure Monitor

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Under **Övervakning** väljer du **Diagnostikinställningar**. Första gången du öppnar den ska du aktivera den. Annars lägger du till en inställning.

    ![Aktivera diagnostikinställningar i Intune för att skicka loggar till Azure Monitor](media/diagnostics-settings-turn-on.png)

3. Ange följande egenskaper:

    - **Namn**: Ange ett namn för diagnostikinställningarna. Den här inställningen innehåller alla egenskaper som du anger. Ange till exempel `Route audit logs to storage account`.
    - **Arkivera till ett lagringskonto**: Sparar loggdata till ett Azure storage-konto. Använd det här alternativet om du vill spara eller arkivera data.

        1. Välj det här alternativet > **Konfigurera**. 
        2. Välj ett befintligt lagringskonto i listan > **OK**.

    - **Strömma till en händelsehubb**: Strömmar loggarna till en Azure-händelsehubb. Om du vill ha analyser av loggdata med hjälp av SIEM-verktyg, till exempel Splunk och QRadar, väljer du det här alternativet.

        1. Välj det här alternativet > **Konfigurera**. 
        2. Välj en befintlig namnrymd och en princip för händelsehubben i listan > **OK**.

    - **Skicka till Log Analytics**: Skickar data till Azure-logganalys. Om du vill använda visualiseringar, övervakning och avisering för dina loggar, väljer du det här alternativet.

        1. Välj det här alternativet > **Konfigurera**. 
        2. Skapa en ny arbetsyta och ange arbetsytans information. Eller välj en befintlig arbetsyta i listan > **OK**.

            [Azure-logganalysarbetsytan](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) innehåller mer information om de här inställningarna.

    - **LOG** > **AuditLogs**: Välj det här alternativet för att skicka [Intune-granskningsloggarna](monitor-audit-logs.md) till ditt lagringskonto, händelsehubb eller logganalys. Granskningsloggarna visar historiken för varje aktivitet som genererar en ändring i Intune, inklusive vem som gjorde den och när.

      Om du väljer att använda ett lagringskonto, ange då också hur många dagar som du vill behålla data (kvarhållning). Om du vill behålla data alltid ange **Kvarhållning (dagar)** till `0` (noll).

    - **LOG** > **OperationalLogs**: Arbetsloggar (förhandsversion) visar framgång eller misslyckande för användare och enheter som registreras i Intune samt information om inkompatibla enheter. Välj det här alternativet för att skicka registreringsloggarna till ditt lagringskonto, händelsehubb eller logganalys.

      Om du väljer att använda ett lagringskonto, ange då också hur många dagar som du vill behålla data (kvarhållning). Om du vill behålla data alltid ange **Kvarhållning (dagar)** till `0` (noll).

      > [!NOTE]
      > Driftloggarna finns i förhandsversion. Om du vill ge feedback, inklusive information i driftsloggarna, går du till [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    - **LOG** > **DeviceComplianceOrg**: Organisationsloggar för enhetsefterlevnad (förhandsversion) visar organisationsrapporten för enhetsefterlevnad i Intune samt information om icke-kompatibla enheter. Välj det här alternativet för att skicka efterlevnadsloggarna till ditt lagringskonto, din händelsehubb eller din logganalys.

      Om du väljer att använda ett lagringskonto, ange då också hur många dagar som du vill behålla data (kvarhållning). Om du vill behålla data alltid ange **Kvarhållning (dagar)** till `0` (noll).
 
      > [!NOTE]
      > Organisationsloggar för enhetsefterlevnad är i förhandsversion. Om du vill ge feedback, inklusive information i rapporten, går du till [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    När du är klar ser inställningarna ut ungefär som följande inställningar: 

    ![Exempelbild som skickar Intune-granskningsloggar till ett Azure storage-konto](media/diagnostics-settings-example.png)

4. **Spara** ändringarna. Inställningarna visas i listan. När den har skapats kan du ändra inställningarna genom att välja **Redigera inställning** > **Spara**.

## <a name="use-audit-logs-throughout-intune"></a>Använda spårningsloggar i Intune

Du kan även exportera spårningsloggar i andra delar av Intune, däribland registrering, efterlevnad, konfiguration, enheter, klientappar och mer.

Så här exporterar du till exempel spårningsloggarna vid användning av enhetsefterlevnad:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetsefterlevnad** > **Övervaka** > **Spårningsloggar**:

    ![Välj spårningslogg för att dirigera Intune-data till Azure Monitor-lagring, händelsehubbar eller analys](media/audit-logs-under-monitor-in-compliance.png)

3. Välj **Inställningar för exportera data**. Om det inte är aktiverat kan du aktivera **Diagnostikinställningar**. Du kan även välja att skicka loggarna enligt beskrivningen i [skicka loggar till Azure Monitor](#send-logs-to-azure-monitor) (i den här artikeln).

## <a name="cost-considerations"></a>Kostnadsöverväganden

Om du redan har en Microsoft Intune-licens behöver du en Azure-prenumeration för att installera lagringskontot och händelsehubben. Azure-prenumerationen är vanligtvis kostnadsfri. Men du måste betala för att använda Azure-resurser, inklusive lagringskontot för arkivering och händelsehubben för dataströmning. Mängden data och kostnaderna varierar beroende på storleken på klienten.

### <a name="storage-size-for-activity-logs"></a>Lagringsstorlek för aktivitetsloggar

Varje granskningslogghändelse använder cirka 2 KB datalagring. Du kanske har cirka 1,5 miljoner händelser per dag för en klient med 100 000 användare. Du kan behöva cirka 3 GB lagringsutrymme per dag. Eftersom skrivningar vanligtvis sker i femminutersomgångar, kan du förvänta dig cirka 9 000 skrivåtgärder per månad.

Följande tabeller visar en kostnadsuppskattning beroende på storleken på klienten. Den innehåller också ett gpv2-lagringskonto (allmänt syfte) i västra USA för minst ett års datakvarhållning. För att få en uppfattning om datavolymen som du förväntar dig för dina loggar, kan du använda [priskalkylatorn för Azure storage](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Granskningslogg med 100 000 användare**

| | |
|---|---|
|Händelser per dag| 1,5 miljon|
|Uppskattad mängd data per månad| 90 GB|
|Uppskattad kostnad per månad (USD)| 1,93 $|
|Uppskattad kostnad per år (USD)| 23,12 $|

**Granskningslogg med 1 000 användare**

| | |
|---|---|
|Händelser per dag| 15 000|
|Uppskattad mängd data per månad| 900 MB|
|Uppskattad kostnad per månad (USD)| 0,02 $|
|Uppskattad kostnad per år (USD)| 0,24 $|

### <a name="event-hub-messages-for-activity-logs"></a>Meddelanden från händelsehubbar för aktivitetsloggar

Händelser grupperas vanligtvis med fem minuters intervall och skickas som ett enda meddelande med alla händelser inom denna tidsram. Ett meddelande i en händelsehubb har en maximal storlek på 256 KB. Om den totala storleken på alla meddelanden under tidsperioden överstiger den volymen, skickas flera meddelanden.

Exempelvis inträffar cirka 18 händelser per sekund vanligtvis för en stor klient med fler än 100 000 användare. Detta motsvarar 5 400 händelser var femte minut (300 sekunder x 18 händelser). Granskningsloggarna är cirka 2 KB per händelse. Detta motsvarar 10,8 MB data. Därför skickas 43 meddelanden till händelsehubben i detta femminutersintervall.

Följande tabell innehåller beräknade kostnader per månad för en grundläggande händelsehubb i västra USA, beroende på mängden händelsedata. För att få en uppfattning om datavolymen som du förväntar dig för dina loggar, kan du använda [Priskalkylatorn för Event Hubs](https://azure.microsoft.com/pricing/details/event-hubs/).

**Granskningslogg med 100 000 användare**

| | |
|---|---|
|Händelser per sekund| 18|
|Händelser per femminutersintervall| 5 400|
|Volym per intervall| 10,8 MB|
|Meddelanden per intervall| 43|
|Meddelanden per månad| 371 520|
|Uppskattad kostnad per månad (USD)| 10,83 $|

**Granskningslogg med 1 000 användare**

| | |
|---|---|
|Händelser per sekund|0,1 |
|Händelser per femminutersintervall| 52|
|Volym per intervall|104 KB |
|Meddelanden per intervall|1 |
|Meddelanden per månad|8 640 |
|Uppskattad kostnad per månad (USD)|10,80 $ |

### <a name="log-analytics-cost-considerations"></a>Kostnadsöverväganden för Log Analytics

Du kan granska kostnaderna för att hantera Log Analytics-arbetsytan i [Hantera kostnader genom att kontrollera datavolymer och kvarhållning i Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).

## <a name="frequently-asked-questions"></a>Vanliga frågor och svar

Få svar på vanliga frågor och svar och läs om kända problem med Intune-loggarna i Azure Monitor.

### <a name="which-logs-are-included"></a>Vilka loggar ingår?

Granskningsloggar och operativa (förhandsversion) loggar är båda tillgängliga för dirigering med hjälp av den här funktionen.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>När visas motsvarande loggarna i händelsehubben efter en åtgärd?

Loggarna visas vanligtvis i din händelsehubb inom några minuter efter att åtgärden utförts. I [Vad är Azure Event Hubs? ](https://docs.microsoft.com/azure/event-hubs/) hittar du mer information.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>När visas motsvarande loggarna i lagringskontot efter en åtgärd ?

För Azure storage-konton är svarstiden någonstans mellan 5 till 15 minuter efter att åtgärden har körts.

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>Vad händer om en administratör ändrar kvarhållningsperioden för en diagnostikinställning?

Den nya kvarhållningsprincipen tillämpas på loggar som samlats in efter ändringen. Insamlade loggar innan principändringen påverkas inte.

### <a name="how-much-does-it-cost-to-store-my-data"></a>Hur mycket kostar det för att lagra mina data?

Kostnader för lagring beror på storleken på dina loggar och kvarhållningsperioden som du väljer. Du hittar en lista över de uppskattade kostnaderna för klienter som är beroende av loggvolymen som genererats i [Lagringsstorlek på aktivitetsloggar](#storage-size-for-activity-logs) (i den här artikeln).

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>Hur mycket kostar det för att strömma data till en händelsehubb?

Strömningskostnaderna beror på hur många meddelanden du får per minut. Mer information om hur kostnader beräknas och kostnadsuppskattningar baserat på antal meddelanden finns i [Meddelanden från händelsehubbar för aktivitetsloggar](#event-hub-messages-for-activity-logs) (i den här artikeln).

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Hur gör jag för att integrera granskningsloggar för Intune med mitt SIEM-system?

Använd Azure Monitor med Event Hubs för att strömma loggar till ditt SIEM-system. Först [strömma loggarna till en händelsehubb](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub). Sedan [konfigurera SIEM-verktyget](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) med den konfigurerade händelsehubben. 

### <a name="what-siem-tools-are-currently-supported"></a>Vilka SIEM-verktyg stöds för närvarande?

Azure Monitor stöds för närvarande av [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), QRadar och [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) (öppnar en ny webbplats). Mer information om hur anslutningsapparna fungerar finns i [Strömma Azure-övervakningsdata till en händelsehubb med ett externt verktyg](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs).

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>Kan jag komma åt data från en händelsehubb utan att använda något externt SIEM-verktyg?

Ja. Om du vill komma åt loggarna från ditt anpassade program måste du använda [Event Hubs API](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph).

### <a name="what-data-is-stored"></a>Vilka data lagras?

Intune lagrar inte alla data som skickas via pipelinen. Intune dirigerar data till Azure Monitor-pipelinen vid klientens medgivande. Mer information finns i [Översikt av Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview).

## <a name="next-steps"></a>Nästa steg

* [Arkivera aktivitetsloggar till ett lagringskonto](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Dirigera aktivitetsloggar till en händelsehubb](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Integrera aktivitetsloggar med Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
