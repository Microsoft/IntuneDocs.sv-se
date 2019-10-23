---
title: Så här övervakar du appskyddsprinciper
titleSuffix: Microsoft Intune
description: Det här avsnittet beskriver hur du övervakar appskyddsprinciper i Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d82813f1292c99cf248c56a102503413d2cb8fb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507449"
---
# <a name="how-to-monitor-app-protection-policies"></a>Så här övervakar du appskyddsprinciper
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Du kan övervaka efterlevnadsstatusen i de hanteringsprinciper för mobilappar som du har tillämpat på användare i fönstret för Intunes appskydd i [Azure-portalen](https://portal.azure.com). Där hittar du dessutom information om de användare som påverkas av principerna, dess efterlevnadsstatus och eventuella problem som användarna kan råka ut för.

Det finns tre olika platser för att övervaka appskyddsprinciper:
- Sammanfattningsvy
- Detaljerad vy
- Rapporteringsvy

> [!NOTE]
> Mer information finns i [Hur du skapar och tilldelar skyddsprinciper för appar](app-protection-policies.md).

Kvarhållningsperioden för appskyddsdata är 90 dagar. Alla appinstanser som har checkat in på MAM-tjänsten under de senaste 90 dagarna kommer att ingå i appskyddsstatusrapporten. En *appinstans* är en unik användare + app + enhet. 

## <a name="summary-view"></a>Sammanfattningsvy

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Klientappar** i **Intune**-fönstret.
4. Visa sammanfattningsvyn genom att i **Övervaka** välja **Status för appskydd** i arbetsbelastningen **Klientappar**.

   ![Skärmbild av panelen Sammanfattning i fönstret för hantering av mobilprogram i Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Tilldelade användare**: Det totala antalet tilldelade användare i företaget som använder en app som är associerad med en princip i en arbetskontext och är skyddade och licensierade, samt de tilldelade användare som är oskyddade och olicensierade.
- **Flaggade användare**: Antalet användare som har problem med sina enheter. Upplåsta (iOS) och rotade (Android) enheter rapporteras under **Flaggade användare**. Även användare med enheter som är flaggade av Googles SafetyNet-kontroll för enhetsattestering (om det är aktiverat av IT-administratören) rapporteras här. 
- **Användare med potentiellt skadliga appar**: Antalet användare som kan ha en skadlig app på en Android-enhet som identifieras av Google Play Protect. 
- **Användarstatus för iOS** och **Användarstatus för Android**: Antal användare som har använt en app som har en princip tilldelad till dem i en arbetskontext för den relaterade plattformen. Den här informationen visar antalet användare som hanteras av principen, samt antalet användare som använder en app som ingen princip i en arbetskontext inriktar sig på. Du kan välja att lägga till dessa användare i principen.
- **De viktigaste skyddade iOS-apparna**: Den här informationen, som baseras på de mest använda iOS-apparna, visar antalet skyddade och oskyddade iOS-appar.
- **De viktigaste skyddade Android-apparna**: Den här informationen, som baseras på de mest använda Android-apparna, visar antalet skyddade och oskyddade Android-appar.
- **Populära konfigurerade iOS-appar utan registrering**: Den här informationen, som baseras på de mest använda iOS-apparna för oregistrerade enheter, visar antalet konfigurerade iOS-appar.
- **Populära konfigurerade Android-appar utan registrering**: Den här informationen, som baseras på de mest använda Android-apparna för oregistrerade enheter, visar antalet konfigurerade Android-appar.

    > [!NOTE]
    > Om du har flera principer per plattform anses en användare vara hanterad av en princip när användaren har minst en tilldelad princip.

## <a name="detailed-view"></a>Detaljerad vy
Du kommer till den detaljerade vyn av sammanfattningen genom att välja panelen **Användarstatus** (beroende på enhetens operativsystem), **Användare med potentiellt skadliga appar** och panelen **Flaggade användare**.

### <a name="user-status"></a>Användarstatus
Du kan söka efter en enskild användare och kontrollera efterlevnadsstatusen för användaren. I fönstret **Apprapportering** visas följande information för en vald användare:
- **Ikon**: Visar om appstatusen är uppdaterad.
- **Appnamn**: Namnet på appen.
- **Enhetsnamn**: Enheter som är associerade med användarkontot.
- **Enhetstyp**: Typ av enhet eller operativsystem som enheten kör.
- **Principer**: De principer som associeras med appen.
- **Status**:
  - **Incheckad**: Principen har distribuerats till användaren och appen användes i arbetskontexten minst en gång.
  - **Inte incheckad**: Principen har distribuerats till användaren, men appen har inte använts i arbetskontexten sedan dess.
- **Senaste synkronisering**: När appen senast synkroniserades med Intune. 

>[!NOTE]
> Kolumnen **Senaste synkronisering** visar samma värde i både konsolens användarstatusrapport och appskyddsprincipens [exporteringsbara .csv-rapport](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities-to-csv). Skillnaden är en liten fördröjning i synkroniseringen mellan värdet i de två rapporterna. 
>
> Tiden som anges i Senaste synkronisering är när Intune senast såg appinstansen. När en användare startar en app kan den meddela starttiden till Intunes appskyddstjänst, beroende på när den senast checkades in. Se [återförsöksintervallets tider för incheckning till appskyddsprincipen](https://docs.microsoft.com/en-us/intune/app-protection-policy-delivery). Om en användare inte har använt den specifika appen under det senaste incheckningsintervallet (som vanligtvis är 30 minuter vid aktiv användning) och de startar appen, händer följande:
>
> - Appskyddsprincipens exporteringsbara .csv-rapport har den nyaste tidsangivelsen, inom 1 minut (minst) till 30 minuter (högst).
> - Användarens statusrapport har den nyaste tidsangivelsen omedelbart.
>
> Anta till exempel att du har en riktad och en licensierad användare som startar en skyddad app kl. 12:00:
> - Om inloggningen sker för första gången innebär det att användaren har loggats ut tidigare och inte har någon appinstansregistrering i Intune. Efter inloggningen får användaren en ny registrering av appinstansen och kan checkas in omedelbart (med samma tidsfördröjning som tidigare vid framtida incheckningar). Den senaste synkroniseringstiden är alltså 12:00 i användarstatusrapporten och 12:01 (eller senast 12:30) i rapporten för appskyddsprincipen. 
> - Om användaren bara startar appen, kommer den senaste synkroniseringstiden som rapporteras att bero på när användaren senast checkade in.


Visa rapporter för en användare genom att följa anvisningarna:

1. Välj sammanfattningspanelen **Användarstatus** för att välja en användare.

    ![Skärmbild av panelen Sammanfattning i hantering av mobilprogram i Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. I fönstret **Apprapportering** väljer du **Välj användare** för att söka efter en Azure Active Directory-användare.

    ![Skärmbild som visar alternativet Välj användare i fönstret Apprapportering](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Välj användaren i listan. Du kan se information om användarens kompatibilitetsstatus.

>[!NOTE]
> Om MAM-principen inte har distribuerats till de användare som du sökte efter, visas ett meddelande om att inga MAM-principer tillämpas på användaren.

### <a name="flagged-users"></a>Flaggade användare
I den detaljerade vyn visas felmeddelandet, appen som användes när felet inträffade, enhetens operativsystem och en tidsstämpel. Felet är vanligt i jailbrokade (iOS) eller rotade (Android) enheter. Användare med enheter som har flaggats av den villkorsstyrda startkontrollen ”SafetyNet-enhetsbestyrkande” visas här med den orsak som rapporterades av Google. För att en användare ska kunna tas bort från rapporten måste status för själva enheten ha ändrats, vilket inträffar efter nästa kontroll av rotidentifiering (eller kontroll av jailbreak/SafetyNet) som rapporterar ett positivt resultat. Om enheten är helt åtgärdad sker uppdateringen av rapporten Flaggade användare när bladet läses in på nytt.

### <a name="users-with-potentially-harmful-apps"></a>Användare med potentiellt skadliga appar
I den detaljerade vyn visas:

- Användaren.
- Appaketets ID.
- Om appen är MAM-aktiverad.
- Hotkategorin.
- E-postmeddelandet.
- Enhetens namn.
- En tidsstämpel.

Användare med enheter som är flaggade av den villkorsstyrda startkontrollen **Kräv genomsökning efter hot i appar** visas här med den hotkategori som rapporterades av Google. Om det finns appar i den här rapporten som distribueras via Intune, kontaktar du appens utvecklare eller slutar tilldela appen till användarna. 

## <a name="reporting-view"></a>Rapporteringsvy

Du hittar samma rapporter överst på bladet **Appskyddsstatus**.

> [!NOTE]
> Intune ger ytterligare fält för enhetsrapportering inklusive appregistrerings-ID, Android-tillverkare, modell och version av säkerhetsuppdatering samt iOS-modell. I Intune når du dessa fält genom att välja **Klientappar** > **Appskyddsstatus** > **Appskyddsrapport: iOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodellen (Android och iOS) och lägsta tillåtna version för Android-säkerhetsuppdateringar. 

Det finns ytterligare rapporter som hjälper dig med efterlevnadsstatusen för MAM-principer. Du visar de rapporterna genom att välja **Klientappar** > **Appskyddsstatus** > **Rapporter**. 

På bladet **Rapporter** finns flera rapporter baserade på användare och app, bland annat följande:

- **Användarrapport**: Den här rapporten visar en översikt över samma information som du hittar i rapporten **Användarstatus** under avsnittet [Detaljerad vy](app-protection-policies-monitor.md#detailed-view) ovan.

- **Apprapport**: Förutom att välja plattform och app, visar rapporten två olika appskyddsstatusar som du kan välja innan du skapar rapporten. Statusen kan vara **Skyddad** eller **Oskyddad**.

  - Användarstatus för hanterad MAM-aktivitet (**Skyddad**): Den här rapporten ger en översikt över aktiviteten i alla hanterade MAM-appar per användare. Den visar alla appar som omfattas av MAM-principer för varje användare, samt status för varje app som checkas in med MAM-principer. Rapporten innehåller också status för varje app som omfattas av en MAM-princip, men som aldrig har checkats in.
  - Användarstatus för icke-hanterad MAM-aktivitet (**Oskyddad**): Den här rapporten ger en översikt per användare över aktiviteten i MAM-aktiverade appar som för närvarande inte hanteras. Detta kan inträffa på grund av följande:
    - Apparna används antingen av en användare eller en app som för närvarande inte omfattas av någon MAM-princip.
    - Alla appar är incheckade men kommer inte åt MAM-principer.

    ![Skärmbild av en användares blad för apprapportering med information om tre appar](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Användarkonfigurationsrapport**: Rapporten baseras på en vald användare och innehåller information om de appkonfigurationer som användaren har tagit emot.
- **Appkonfigurationsrapport**: Rapporten baseras på den valda plattformen och appen och innehåller information om vilka användare som har tagit emot konfigurationer av den valda appen.
- **Appinlärningsrapport för Windows informationsskydd**: Rapporten visar vilka appar försöker korsa principgränser.
- **Webbplatsinlärning för Windows informationsskydd**: Rapporten visar vilka webbplatser som försöker korsa principgränser.

## <a name="table-grouping"></a>Tabellgruppering

När datan i **Användarrapport från appskydd** visas kan du sammanställa informationen enligt följande:

- **Valideringsresultat**: Datan grupperas efter appskyddsstatus, vilken kan vara ”fel”, ”varning” eller ”klart”.
- **Appnamn**: Datan grupperas efter det faktiska namnet på appen. Även här kan statusen vara ”fel”, ”varning” eller ”klart”.

## <a name="export-app-protection-activities"></a>Exportera appskyddsaktiviteter

Du kan exportera alla dina appskyddsprincipsaktiviteter till en enda CSV-fil. Detta kan du ha nytta av om du vill analysera alla de appskyddsstatusar som rapporteras från användarna.

Generera appskyddsrapporten genom att följa dessa anvisningar:

1. Välj **Appskyddsrapport** i fönstret Hantering av mobilprogram i Intune.

    ![Skärmbild av nedladdningslänken för appskydd](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Välj **Ja** om du vill spara rapporten och välj sedan **Spara som**. Välj den mapp som du vill spara rapporten i.

    ![Skärmbild av bekräftelserutan Spara rapport](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>Se även
- [Hantera dataöverföring mellan iOS-appar](data-transfer-between-apps-manage-ios.md)
- [Vad som händer när din Android-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-android.md)
- [Vad som händer när din iOS-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-ios.md)
