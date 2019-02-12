---
title: Så här övervakar du appskyddsprinciper
titleSuffix: Microsoft Intune
description: Övervaka kompatibilitetsstatusen för hanteringsprinciper för mobilappar i Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7efa888344b91c74672563730bbdea6c7424214b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835103"
---
# <a name="how-to-monitor-app-protection-policies"></a>Så här övervakar du appskyddsprinciper
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Övervaka efterlevnadsstatusen för principer för hantering av mobila appar (MAM) som du tillämpat på användare i fönstret för Intune-appskydd i [Azure Portal](https://portal.azure.com). Hitta information om de användare som påverkas av MAM-principerna, efterlevnadsstatus och eventuella problem som användarna kan råka ut för.

Det finns tre olika platser för att övervaka efterlevnadsstatus:

-   Sammanfattningsvy

-   Detaljerad vy

-   Rapporteringsvy

> [!NOTE]
> Information om att skapa appskyddsprinciper finns i [Skapa och tilldela appskyddsprinciper](app-protection-policies.md).

## <a name="summary-view"></a>Sammanfattningsvy

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** i **Intune**-fönstret.
4. Visa sammanfattningsvyn genom att välja **Appskyddsstatus** i avsnittet **Övervaka** i arbetsbelastningen **Klientappar**:

![Panelen Sammanfattning i fönstret Hantering av mobilprogram i Intune](./media/app-protection-user-status-summary.png)

-   **Tilldelade användare**: Det totala antalet tilldelade användare i företaget som använder en app som är associerad med en princip i en arbetskontext och är skyddade och licensierade, samt de tilldelade användare som är oskyddade och olicensierade.
-   **Flaggade användare**: Antalet användare som har problem. Upplåsta enheter rapporteras under **Flaggade användare**.
-   **Användarstatus för iOS** och **Användarstatus för Android**: Antal användare som har använt en app som har en princip tilldelad till dem i en arbetskontext för den relaterade plattformen. Den här informationen visar antalet användare som hanteras av principen, samt antalet användare som använder en app som ingen princip i en arbetskontext inriktar sig på. Du kan välja att lägga till dessa användare i principen.

    > [!NOTE]
    > Om du har flera principer per plattform anses en användare vara hanterad av en princip när användaren har minst en tilldelad princip.

## <a name="detailed-view"></a>Detaljerad vy
Du kommer till den detaljerade vyn av sammanfattningen genom att välja panelen **Användarstatus** (beroende på enhetens operativsystem) och panelen **Flaggade användare**.

### <a name="user-status"></a>Användarstatus
Du kan söka efter en enskild användare och kontrollera efterlevnadsstatusen för användaren. I fönstret **Apprapportering** visas följande information för en vald användare:
- Enheter som är associerade med användarkontot

- Appar med en MAM-princip på enheten

- Status:

  - **Incheckad**: Principen har distribuerats till användaren och appen användes i arbetskontexten minst en gång.

  - **Inte incheckad**: Principen har distribuerats till användaren, men appen har inte använts i arbetskontexten sedan dess.

>[!NOTE]
> Om MAM-principen inte har distribuerats till de användare som du sökte efter, visas ett meddelande om att inga MAM-principer tillämpas på användaren.

Visa rapporter för en användare genom att följa anvisningarna:

1.  Välj sammanfattningspanelen **Användarstatus** för att välja en användare.

    ![Skärmbild av panelen Sammanfattning i hantering av mobilprogram i Intune](./media/MAM-reporting-6.png)

2. I fönstret **Apprapportering** som öppnas väljer du **Välj användare** för att söka efter en Azure Active Directory-användare.

    ![Skärmbild som visar alternativet Välj användare i fönstret Apprapportering](./media/MAM-reporting-2.png)

3. Välj användaren i listan. Du kan se information om användarens kompatibilitetsstatus.

### <a name="flagged-users"></a>Flaggade användare
I den detaljerade vyn visas felmeddelandet, appen som användes när felet inträffade, enhetens operativsystem och en tidsstämpel.

## <a name="reporting-view"></a>Rapporteringsvy

Du hittar samma rapporter på bladet **Appskyddsstatus**.

> [!NOTE]
> Intune ger ytterligare fält för enhetsrapportering inklusive appregistrerings-ID, Android-tillverkare, modell och version av säkerhetsuppdatering samt iOS-modell. I Intune är dessa fält tillgängliga genom att välja **Klientappar** > **Appskyddsstatus** och sedan välja **Appskyddsrapport: iOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodell (Android och iOS) och lägsta inställning för version av Android-säkerhetsuppdatering. 

Det finns ytterligare rapporter som hjälper dig med efterlevnadsstatusen för MAM-principer. Du visar de rapporterna genom att välja **Klientappar** > **Appskyddsstatus** > **Rapporter**. 

På bladet **Rapporter** finns flera rapporter baserade på användare och app, bland annat följande:


-   **Användarrapport**: Den här rapporten visar en översikt över samma information som du hittar i rapporten **Användarstatus** under avsnittet Detaljerad vy ovan.

-   **Apprapport**: Den här rapporten tillhandahåller två olika statusar om appskydd som administratörer kan välja innan de skapar rapporten. Statusen kan vara skyddad eller oskyddad.

    -   Användarstatus för hanterad MAM-aktivitet (Skyddad): Den här rapporten ger en översikt över hur alla hanterade MAM-appar opererar, per användare.

        -   Den visar alla appar som är mål för MAM-principer för varje användare. Den visar även status för varje app, som incheckade med MAM-principer eller som mål för MAM-principer men inte incheckade.
<br><br>
    -   Användarstatus för icke-hanterad MAM-aktivitet (Oskyddad): Den här rapporten ger en översikt över hur MAM-aktiverade appar som är icke-hanterade opererar, per användare. Detta kan inträffa på grund av följande anledningar:

        -   De här apparna används antingen av en användare eller en app som för närvarande inte är mål för en MAM-princip.

        -   Alla appar är incheckade men kommer inte åt MAM-principer.

![Skärmbild av en användares blad för apprapportering med information för 3 appar](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Tabellgruppering

När data för **användarrapporten för appskydd** visas kan du sammanställa informationen enligt följande:

- **Valideringsresultat:** Informationen visas grupperad efter appskyddsstatus, vilken kan vara fel, varning eller klar.
- **Appnamn:** Informationen visas grupperad efter appar (det faktiska appnamnet) som fel, varning eller klar.

## <a name="export-app-protection-activities-to-csv"></a>Exportera appskyddsaktiviteter till CSV

Du kan exportera alla dina appskyddsprincipsaktiviteter till en enda CSV-fil. Detta kan du ha nytta av om du vill analysera alla de appskyddsstatusar som rapporteras från användarna.

Generera appskyddsrapporten genom att följa dessa anvisningar:

1. Välj **Appskyddsrapport** i fönstret Hantering av mobilprogram i Intune.

    ![Skärmbild av nedladdningslänken för appskydd](./media/app-protection-report-csv-2.png)

2. Välj först Ja om du vill spara rapporten, välj sedan Spara som och ange den mapp som du vill spara rapporten i.

    ![Skärmbild av bekräftelserutan Spara rapport](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Se även
[Hantera dataöverföring mellan iOS-appar](data-transfer-between-apps-manage-ios.md)

* [Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-apps-android.md)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-apps-ios.md)
