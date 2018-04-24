---
title: Så här övervakar du appskyddsprinciper
titleSuffix: Microsoft Intune
description: Övervaka kompatibilitetsstatusen för hanteringsprinciper för mobilappar i Intune.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7db5a9dfe7a7da21a9b59dafb4f95cdb54a59735
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-monitor-app-protection-policies"></a>Så här övervakar du appskyddsprinciper
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**Om du inte är i Azure-portalen** beskriver det här ämnet [hur du skapar programskyddsprinciper](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) i den klassiska Intune-portalen.


Övervaka efterlevnadsstatusen för principer för hantering av mobila appar (MAM) som du tillämpat på användare i fönstret för Intune-appskydd i [Azure Portal](https://portal.azure.com). Hitta information om de användare som påverkas av MAM-principerna, efterlevnadsstatus och eventuella problem som användarna kan råka ut för.

Det finns tre olika platser för att övervaka efterlevnadsstatus:

-   Sammanfattningsvy

-   Detaljerad vy

-   Rapporteringsvy

## <a name="summary-view"></a>Sammanfattningsvy

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
4. Visa sammanfattningsvyn genom att välja **Övervaka** > **Status för appskydd** i arbetsbelastningen **Mobile Apps**:

![Panelen Sammanfattning i fönstret Hantering av mobilprogram i Intune](./media/app-protection-user-status-summary.png)

-   **Användare:** Totalt antal användare på företaget som använder en app som är associerad med principen i ett arbetssammanhang.

-   **HANTERAS AV PRINCIP**: Antal användare som har använt en app som har en princip tilldelad till dem i ett arbetssammanhang.

-   **INGEN PRINCIP**: Antal användare som använder en app som ingen princip i ett arbetssammanhang inriktar sig på. Du kan välja att lägga till dessa användare i principen.
    > [!NOTE]
    > Om du har flera principer per plattform anses en användare vara hanterad av en princip när användaren har minst en tilldelad princip.

- **Flaggade användare**: Antalet användare som har problem. För närvarande rapporteras endast användare med upplåsta enheter under **Flaggade användare**.


## <a name="detailed-view"></a>Detaljerad vy
Du kommer till den detaljerade vyn av sammanfattningen genom att välja panelen **Användarstatus** (beroende på enhetens operativsystem) och panelen **Flaggade användare**.

### <a name="user-status"></a>Användarstatus
Du kan söka efter en enskild användare och kontrollera efterlevnadsstatusen för användaren. I fönstret **Apprapportering** visas följande information för en vald användare:
- Enheter som är associerade med användarkontot

- Appar med en MAM-princip på enheten

- Status:

  - **Incheckad**: Principen har distribuerats till användaren och appen användes i arbetskontexten minst en gång.

  - **Inte incheckad:** Principen har distribuerats till användaren, men appen har inte använts i arbetskontexten sedan dess.

>[!NOTE]
> Om MAM-principen inte har distribuerats till de användare som du sökte efter, visas ett meddelande om att inga MAM-principer tillämpas på användaren.

Visa rapporter för en användare genom att följa anvisningarna:

1.  Välj panelen **Sammanfattning** för att välja en användare.

    ![Skärmbild som visar panelen Sammanfattning på bladet Inställningar i Hantering av mobilprogram i Intune](./media/MAM-reporting-6.png)

2. I fönstret **Apprapportering** som öppnas väljer du **Välj användare** för att söka efter en Azure Active Directory-användare.

    ![Skärmbild som visar alternativet Välj användare i fönstret Apprapportering](./media/MAM-reporting-2.png)

3. Välj användaren i listan. Du kan se information om användarens kompatibilitetsstatus.

### <a name="flagged-users"></a>Flaggade användare
I den detaljerade vyn visas felmeddelandet, appen som användes när felet inträffade, enhetens operativsystem och en tidsstämpel.

## <a name="reporting-view"></a>Rapporteringsvy

Du kan hitta samma rapporter från den detaljerade vyn och ytterligare rapporter som hjälper dig med efterlevnadsstatusen för MAM-principer:

![Skärmbild som visar två rapporter som är tillgängliga i fönstret Inställningar](./media/MAM-reporting-7.png)

-   **Rapport om appskyddsanvändare:** Visar en översikt över samma information som du hittar i rapporten **Användarstatus** under avsnittet Detaljerad vy ovan.

-   **Rapport om appskyddsappar:** Tillhandahåller två olika statusar om appskydd som administratörer kan välja innan de skapar rapporten. Statusen kan vara skyddad eller oskyddad.

    -   Användarstatus för hanterad MAM-aktivitet (Skyddad): Den här rapporten ger en översikt över hur alla hanterade MAM-appar opererar, per användare.

        -   Den visar alla appar som är mål för MAM-principer för varje användare. Den visar även status för varje app, som incheckade med MAM-principer eller som mål för MAM-principer men inte incheckade.
<br></br>
    -   Användarstatus för icke-hanterad MAM-aktivitet (Oskyddad): Den här rapporten ger en översikt över hur MAM-aktiverade appar som är icke-hanterade opererar, per användare. Detta kan inträffa på grund av följande anledningar:

        -   De här apparna används antingen av en användare eller en app som för närvarande inte är mål för en MAM-princip.

        -   Alla appar är incheckade men kommer inte åt MAM-principer.

![Skärmbild som visar bladet Apprapportering för en användare med en tabell med information för tre registrerade appar](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Tabellgruppering

När data för **användarrapporten för appskydd** visas kan du sammanställa informationen enligt följande:

- **Verifieringsresultat:** Informationen visas grupperad efter appskyddsstatus, vilken kan vara fel, varning eller klar.
- **Appnamn:** Informationen visas grupperad efter appar (det faktiska appnamnet) som fel, varning eller klar.

## <a name="export-app-protection-activities-to-csv"></a>Exportera appskyddsaktiviteter till CSV

Du kan exportera alla dina appskyddsprincipsaktiviteter till en enda CSV-fil. Detta kan du ha nytta av om du vill analysera alla de appskyddsstatusar som rapporteras från användarna.

Generera appskyddsrapporten genom att följa dessa anvisningar:

1. Välj **Appskyddsrapport** i fönstret Hantering av mobilprogram i Intune.

    ![Skärmbild som visar nedladdningslänken Appskydd i fönstret Hantering av mobilprogram i Intune](./media/app-protection-report-csv-2.png)

2. Välj först Ja om du vill spara rapporten, välj sedan Spara som och ange den mapp som du vill spara rapporten i.

    ![Skärmbild av bekräftelserutan Spara rapport](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Se även
[Hantera dataöverföring mellan iOS-appar](data-transfer-between-apps-manage-ios.md)

* [Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-apps-android.md)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-apps-ios.md)
