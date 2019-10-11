---
title: Så här övervakar du appskyddsprinciper
titleSuffix: Microsoft Intune
description: I det här ämnet beskrivs hur du övervakar mobilappars efterlevnadsstatus för hanteringsprinciper i Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fad554ace3b7c8c279161f149bc06854dfaca93d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725523"
---
# <a name="how-to-monitor-app-protection-policies"></a>Så här övervakar du appskyddsprinciper
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Du kan övervaka efterlevnadsstatusen i de hanteringsprinciper för mobilappar som du har tillämpat på användare i fönstret för Intunes appskydd i [Azure-portalen](https://portal.azure.com). Där hittar du dessutom information om de användare som påverkas av principerna, dess efterlevnadsstatus och eventuella problem som användarna kan råka ut för.

Det finns tre olika platser där du kan övervaka efterlevnadsstatusen i hanteringsprinciper för mobilappar:
- Sammanfattningsvy
- Detaljerad vy
- Rapporteringsvy

> [!NOTE]
> Information om att skapa appskyddsprinciper finns i [Skapa och tilldela appskyddsprinciper](app-protection-policies.md).

Kvarhållningsperioden för appskyddsdata är 90 dagar. Alla appinstanser som har checkat in på MAM-tjänsten under de senaste 90 dagarna kommer att ingå i appskyddsstatusrapporten. En appinstans är en unik användare + app + enhet. 

## <a name="summary-view"></a>Sammanfattningsvy

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Klientappar** i **Intune**-fönstret.
4. Visa sammanfattningsvyn genom att välja **Appskyddsstatus** i avsnittet **Övervaka** i arbetsbelastningen **Klientappar**:

![Panelen Sammanfattning i fönstret Hantering av mobilprogram i Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Tilldelade användare**: Det totala antalet tilldelade användare i företaget som använder en app som är associerad med en princip i en arbetskontext och är skyddade och licensierade, samt de tilldelade användare som är oskyddade och olicensierade.
- **Flaggade användare**: Antalet användare som har problem. Upplåsta (iOS) och rotade (Android) enheter rapporteras under **Flaggade användare**. Användare med enheter som är flaggade av Googles SafetyNet-kontroll för enhetsattestering (om det är aktiverat av IT-administratören) rapporteras här. 
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
- **Senaste synkronisering**: När enheten senast synkroniserades.

>[!NOTE]
> Om MAM-principen inte har distribuerats till de användare som du sökte efter, visas ett meddelande om att inga MAM-principer tillämpas på användaren.

Visa rapporter för en användare genom att följa anvisningarna:

1. Välj sammanfattningspanelen **Användarstatus** för att välja en användare.

    ![Skärmbild av panelen Sammanfattning i hantering av mobilprogram i Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. I fönstret **Apprapportering** som öppnas väljer du **Välj användare** för att söka efter en Azure Active Directory-användare.

    ![Skärmbild som visar alternativet Välj användare i fönstret Apprapportering](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Välj användaren i listan. Du kan se information om användarens kompatibilitetsstatus.

### <a name="flagged-users"></a>Flaggade användare
I den detaljerade vyn visas felmeddelandet, appen som användes när felet inträffade, enhetens operativsystem och en tidsstämpel. Användare med enheter som är flaggade av den villkorliga startkontrollen ”SafetyNet-kontroll för enhetsattestering” rapporteras här med de orsaker som har rapporterats av Google.

### <a name="users-with-potentially-harmful-apps"></a>Användare med potentiellt skadliga appar
I den detaljerade vyn visas användaren, programpaket-ID:t, om appen är MAM aktiverad, hotkategori, e-post, enhetsnamn och en tidstämpel. Användare med enheter som är flaggade av den villkorliga startkontrollen ”Kräv hotgenomsökning på appar” rapporteras här med hotkategorin som har rapporterats av Google. Om det finns appar i den här rapporten som distribueras via Intune kontaktar du appens utvecklare för appen och/eller tar bort appen från att tilldelas till slutanvändarna. 

## <a name="reporting-view"></a>Rapporteringsvy

Du hittar samma rapporter överst på bladet **Appskyddsstatus**.

> [!NOTE]
> Intune ger ytterligare fält för enhetsrapportering inklusive appregistrerings-ID, Android-tillverkare, modell och version av säkerhetsuppdatering samt iOS-modell. I Intune är dessa fält tillgängliga genom att välja **Klientappar** > **Appskyddsstatus** och sedan välja **Appskyddsrapport: iOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodell (Android och iOS) och lägsta inställning för version av Android-säkerhetsuppdatering. 

Det finns ytterligare rapporter som hjälper dig med efterlevnadsstatusen för MAM-principer. Du visar de rapporterna genom att välja **Klientappar** > **Appskyddsstatus** > **Rapporter**. 

På bladet **Rapporter** finns flera rapporter baserade på användare och app, bland annat följande:


- **Användarrapport**: Den här rapporten visar en översikt över samma information som du hittar i rapporten **Användarstatus** under avsnittet [Detaljerad vy](app-protection-policies-monitor.md#detailed-view) ovan.

- **Apprapport**: Förutom att välja plattform och app, visar rapporten två olika appskyddsstatusar som du kan välja innan du skapar rapporten. Statusen kan vara **Skyddad** eller **Oskyddad**.

  - Användarstatus för hanterad MAM-aktivitet (**Skyddad**): Den här rapporten ger en översikt över hur alla hanterade MAM-appar opererar, per användare. Den visar alla appar som är mål för MAM-principer för varje användare. Den visar även status för varje app, som incheckade med MAM-principer eller som mål för MAM-principer men inte incheckade.
  - Användarstatus för icke-hanterad MAM-aktivitet (**Oskyddad**): Den här rapporten ger en översikt över hur MAM-aktiverade appar som är icke-hanterade opererar, per användare. Detta kan inträffa på grund av följande anledningar:
    - De här apparna används antingen av en användare eller en app som för närvarande inte är mål för en MAM-princip.
    - Alla appar är incheckade men kommer inte åt MAM-principer.

    ![Skärmbild av en användares blad för apprapportering med information för 3 appar](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Användarkonfigurationsrapport**: Rapporten baseras på en vald användare och innehåller information om de appkonfigurationer som användaren har tagit emot.
- **Appkonfigurationsrapport**: Rapporten baseras på den valda plattformen och appen och innehåller information om vilka användare som har tagit emot konfigurationer av den valda appen.
- **Appinlärningsrapport för Windows informationsskydd**: Rapporten visar vilka appar försöker korsa principgränser.
- **Webbplatsinlärning för Windows informationsskydd**: Rapporten visar vilka webbplatser som försöker korsa principgränser.

## <a name="table-grouping"></a>Tabellgruppering

När datan i **Användarrapport från appskydd** visas kan du sammanställa informationen enligt följande:

- **Valideringsresultat:** Informationen visas grupperad efter appskyddsstatus, vilken kan vara fel, varning eller klar.
- **Appnamn:** Informationen visas grupperad efter appar (det faktiska appnamnet) som fel, varning eller klar.

## <a name="export-app-protection-activities-to-csv"></a>Exportera appskyddsaktiviteter till CSV

Du kan exportera alla dina principaktiviteter för appskyddet till en enda *.csv*-fil. Detta kan du ha nytta av om du vill analysera alla de appskyddsstatusar som rapporteras från användarna.

Generera appskyddsrapporten genom att följa dessa anvisningar:

1. Välj **Appskyddsrapport** i fönstret Hantering av mobilprogram i Intune.

    ![Skärmbild av nedladdningslänken för appskydd](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Välj först **Ja** för att spara rapporten och välj sedan **Spara som**. Välj den mapp som du vill spara rapporten i.

    ![Skärmbild av bekräftelserutan Spara rapport](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>Se även
- [Hantera dataöverföring mellan iOS-appar](data-transfer-between-apps-manage-ios.md)
- [Vad som händer när din Android-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-android.md)
- [Vad som händer när din iOS-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-ios.md)
