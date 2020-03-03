---
title: Så här övervakar du appskyddsprinciper
titleSuffix: Microsoft Intune
description: Det här avsnittet beskriver hur du övervakar appskyddsprinciper i Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2019
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
ms.openlocfilehash: 317f39b28909196d03ef5e7c68c7980f5fdfea3f
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512219"
---
# <a name="how-to-monitor-app-protection-policies"></a>Så här övervakar du appskyddsprinciper
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Du kan övervaka statusen i de appskyddsprinciper som du har tillämpat på användare i fönstret för Intunes appskydd i [Azure-portalen](https://portal.azure.com). Där hittar du dessutom information om de användare som påverkas av appskyddsprinciperna, dess efterlevnadsstatus och eventuella problem som användarna kan råka ut för.

Det finns tre olika platser för att övervaka appskyddsprinciper:
- Sammanfattningsvy
- Detaljerad vy
- Rapporteringsvy

Kvarhållningsperioden för appskyddsdata är 90 dagar. Alla appinstanser som har checkat in på Intune-tjänsten under de senaste 90 dagarna kommer att ingå i appskyddsstatusrapporten. En *appinstans* är en unik användare + app + enhet. 

> [!NOTE]
> Mer information finns i [Hur du skapar och tilldelar skyddsprinciper för appar](app-protection-policies.md).

## <a name="summary-view"></a>Sammanfattningsvy

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Välj **Appar** > **Övervaka** > **Appskyddsstatus**.

   ![Skärmbild av panelen Sammanfattning i fönstret för hantering av mobilprogram i Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Tilldelade användare**: Det totala antalet tilldelade användare i företaget som använder en app som är associerad med en princip i en arbetskontext och är skyddade och licensierade, samt de tilldelade användare som är oskyddade och olicensierade.
- **Flaggade användare**: Antalet användare som har problem med sina enheter. Upplåsta (iOS/iPadOS) och rotade (Android) enheter rapporteras under **Flaggade användare**. Även användare med enheter som är flaggade av Googles SafetyNet-kontroll för enhetsattestering (om det är aktiverat av IT-administratören) rapporteras här. 
- **Användare med potentiellt skadliga appar**: Antalet användare som kan ha en skadlig app på en Android-enhet som identifieras av Google Play Protect. 
- **Användarstatus för iOS** och **Användarstatus för Android**: Antal användare som har använt en app som har en princip tilldelad till dem i en arbetskontext för den relaterade plattformen. Den här informationen visar antalet användare som hanteras av principen, samt antalet användare som använder en app som ingen princip i en arbetskontext inriktar sig på. Du kan välja att lägga till dessa användare i principen.
- **De viktigaste skyddade iOS/iPadOS-apparna** och **De viktigaste skyddade Android-apparna**: Den här informationen, som baseras på de mest använda iOS/iPadOS- och Android-apparna, visar antalet skyddade och oskyddade appar efter plattform.
- **Populära konfigurerade iOS/iPadOS-appar utan registrering** och **Populära konfigurerade Android-appar utan registrering**: Den här informationen, som baseras på de mest använda iOS/iPadOS- och Android-apparna för oregistrerade enheter, visar antalet konfigurerade appar efter plattform (som använder en appkonfigureringspolicy).

    > [!NOTE]
    > Om du har flera principer per plattform anses en användare vara hanterad av en princip när användaren har minst en tilldelad princip.

## <a name="detailed-view"></a>Detaljerad vy
Du kommer till den detaljerade vyn av sammanfattningen genom att välja panelen **Flaggade användare** och panelen **Användare med potentiellt skadliga appar**.

### <a name="flagged-users"></a>Flaggade användare
I den detaljerade vyn visas felmeddelandet, appen som användes när felet inträffade, enhetens operativsystem och en tidsstämpel. Felet är vanligt i jailbrokade (iOS/iPadOS) eller rotade (Android) enheter. Användare med enheter som har flaggats av den villkorsstyrda startkontrollen ”SafetyNet-enhetsbestyrkande” visas här med den orsak som rapporterades av Google. För att en användare ska kunna tas bort från rapporten måste status för själva enheten ha ändrats, vilket inträffar efter nästa kontroll av rotidentifiering (eller kontroll av jailbreak/SafetyNet) som rapporterar ett positivt resultat. Om enheten är helt åtgärdad sker uppdateringen av rapporten Flaggade användare när fönstret läses in på nytt.

### <a name="users-with-potentially-harmful-apps"></a>Användare med potentiellt skadliga appar
Användare med enheter som är flaggade av den villkorsstyrda startkontrollen **Kräv genomsökning efter hot i appar** visas här med den hotkategori som rapporterades av Google. Om det finns appar i den här rapporten som distribueras via Intune, kontaktar du appens utvecklare eller slutar tilldela appen till användarna. I den detaljerade vyn visas:

- **Användare**: Användarens namn.
- **Appaket-ID**: Detta är hur Android-operativsystemet unikt identifierar en app.
- **Om appen är MAM-aktiverad**: Om appen distribueras via Microsoft Intune eller inte. 
- **Hotkategorin**: Vilken av Googles hotkategorier som denna app hör till. 
- **E-post**: Användarens e-postadress.
- **Enhetsnamn**: Namn på enheter som är associerade med användarkontot.
- **En tidsstämpel**: Datumet för den senaste synkroniseringen som Google gjorde med Microsoft Intune vad gäller potentiellt skadliga appar.

## <a name="reporting-view"></a>Rapporteringsvy

Du hittar samma rapporter högst upp i fönstret **Appskyddsstatus**. Du visar de rapporterna genom att välja **Appar** > **Appskyddsstatus** > **Rapporter**. Fönstret **Rapporter** tillhandahåller flera rapporter som baseras på användare och appar, däribland följande:

### <a name="user-report"></a>Användarrapport
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
> Kolumnen **Senaste synkronisering** visar samma värde i både konsolens användarstatusrapport och appskyddsprincipens [exporteringsbara .csv-rapport](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities). Skillnaden är en liten fördröjning i synkroniseringen mellan värdet i de två rapporterna. 
>
> Tiden som anges i Senaste synkronisering är när Intune senast såg appinstansen. När en användare startar en app kan den meddela starttiden till Intunes appskyddstjänst, beroende på när den senast checkades in. Se [återförsöksintervallets tider för incheckning till appskyddsprincipen](~/apps/app-protection-policy-delivery.md). Om en användare inte har använt den specifika appen under det senaste incheckningsintervallet (som vanligtvis är 30 minuter vid aktiv användning) och de startar appen, händer följande:
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

### <a name="app-report"></a>Apprapport
Du kan söka efter plattform och app, sedan visar rapporten två olika appskyddsstatusar som du kan välja innan du skapar rapporten. Statusen kan vara **Skyddad** eller **Oskyddad**.

  - Användarstatus för hanterad MAM-aktivitet (**Skyddad**): Den här rapporten ger en översikt över aktiviteten i alla hanterade MAM-appar per användare. Den visar alla appar som omfattas av MAM-principer för varje användare, samt status för varje app som checkas in med MAM-principer. Rapporten innehåller också status för varje app som omfattas av en MAM-princip, men som aldrig har checkats in.
  - Användarstatus för icke-hanterad MAM-aktivitet (**Oskyddad**): Den här rapporten ger en översikt per användare över aktiviteten i MAM-aktiverade appar som för närvarande inte hanteras. Detta kan inträffa på grund av följande:
    - Apparna används antingen av en användare eller en app som för närvarande inte omfattas av någon MAM-princip.
    - Alla appar är incheckade men kommer inte åt MAM-principer.

    ![Skärmbild av en användares apprapporteringsfönster med information om tre appar](./media/app-protection-policies-monitor/MAM-reporting-4.png)

### <a name="user-configuration-report"></a>**Användarkonfigurationsrapport**
Rapporten baseras på en vald användare och innehåller information om de appkonfigurationer som användaren har tagit emot.

### <a name="app-configuration-report"></a>**Appkonfigurationsrapport**
Rapporten baseras på den valda plattformen och appen och innehåller information om vilka användare som har tagit emot konfigurationer av den valda appen.

### <a name="app-learning-report-for-windows-information-protection"></a>Appinlärningsrapport för Windows informationsskydd
Rapporten visar vilka appar försöker korsa principgränser.

### <a name="website-learning-for-windows-information-protection"></a>Webbplatsinlärning för Windows informationsskydd
Rapporten visar vilka webbplatser som försöker korsa principgränser.

## <a name="export-app-protection-activities"></a>Exportera appskyddsaktiviteter
Du kan exportera alla dina appskyddsprincipsaktiviteter till en enda CSV-fil. Detta kan du ha nytta av om du vill analysera alla de appskyddsstatusar som rapporteras från användarna. **Appskyddsfilen i .csv -format visar**:
- **Användare**: Användarens namn.
- **E-post**: Användarens e-postadress.
- **App**: Namnet på appen.
- **Appversion**: Appens version.
- **Enhetsnamn**: Namn på enheter som är associerade med användarkontot.
- **Enhetstillverkare**: Denna lista visar enhetens tillverkare (endast Android). 
- **Enhetsmodell**: Denna lista visar enhetens tillverkare (endast Android). 
- **Korrigeringsversion för Android**: Datum för senaste säkerhetskorrigering för Android.
- **AAD-enhets-ID**: Den här kolumnen fylls i om enheten är AAD-ansluten.
- **ID för hanterad mobilenhet**: Den här kolumnen fylls i om enheten har registrerats Microsoft Intune MDM.
- **Plattform**: Operativsystemet.
- **Plattformsversion**: Operativsystemversionen.
- **Hanteringstyp**: Typ av hantering på enheten. Till exempel Android Enterprise, ohanterad eller MDM.  
- **Appskyddsstatus**: Oskyddad eller skyddad.
- **Princip**: De appskyddsprinciper som associeras med appen.
- **Senaste synkronisering**: När appen senast synkroniserades med Microsoft Intune. 
- **Kompatibilitetstillstånd**: Om appen på användarens enhet är kompatibel med alla appbaserade principer för villkorlig åtkomst.  

Följ de här stegen om du vill skapa en appskyddsfil i . csv-format eller en appkonfigurationsfil i . csv-format:

1. Välj **Appskyddsrapport** i fönstret Hantering av mobilprogram i Intune.

    ![Skärmbild av nedladdningslänken för appskydd](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Välj **Ja** om du vill spara rapporten och välj sedan **Spara som**. Välj den mapp som du vill spara rapporten i.

    ![Skärmbild av bekräftelserutan Spara rapport](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)
   
> [!NOTE]
> Intune ger ytterligare fält för enhetsrapportering inklusive appregistrerings-ID, Android-tillverkare, modell och version av säkerhetsuppdatering samt iOS/iPadOS-modell. I Intune når du dessa fält genom att välja **Appar** > **Appskyddsstatus** > **Appskyddsrapport: iOS/iPadOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodellen (Android och iOS/iPadOS) och **lägsta tillåtna version för Android-säkerhetsuppdateringar**.   
 
## <a name="see-also"></a>Se även
- [Hantera dataöverföring mellan iOS/iPadOS-appar](data-transfer-between-apps-manage-ios.md)
- [Vad som händer när din Android-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-android.md)
- [Vad som händer när din iOS/iPadOS-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-ios.md)
