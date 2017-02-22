---
title: "Övervaka MAM-principer med Microsoft Intune | Microsoft Docs"
description: "Se hur många användare som principen tillämpas på och öka detaljnivån om du vill ha mer information."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 22c30f51bf83219053f97310ed1830ad9e01acd8
ms.openlocfilehash: bd270cd4b04894d4824487d36ea4f0c1929dd568


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>Övervaka hanteringsprinciper för mobilappar med Microsoft Intune
Du kan övervaka efterlevnadsstatusen för de hanteringsprinciper för mobilappar (MAM) som du har tillämpat på användare. Du kan hitta information om de användare som påverkas av MAM-principerna, efterlevnadsstatus och eventuella problem som användarna kan råka ut för.

Det finns tre olika platser för att övervaka efterlevnadsstatus:

-   Sammanfattningsvy

-   Detaljerad vy

-   Rapporteringsvy

## <a name="summary-view"></a>Sammanfattningsvy

Följ de tre stegen nedan för att öppna sammanfattningsvyn:

1. Gå till [Azure Portal](https://portal.azure.com) och logga in med dina autentiseringsuppgifter.
2. Välj **Fler tjänster** och skriv **Intune** i filtrets textruta.
3. Välj **Intune App Protection**.

På bladet **Hantering av mobilprogram i Intune** visas en sammanfattning av efterlevnadsstatusen:

![Panelen Sammanfattning på bladet Hantering av mobilprogram i Intune](../media/mam-azure-portal-user-status-summary.png)

-   **Användare:** Totalt antal användare på företaget som använder de appar som är associerade med principen.

-   **HANTERAS AV PRINCIP:** Antalet användare som har använt minst en av apparna i arbetskontexten.

-   **INGEN PRINCIP**: Antalet användare som använder de appar som är associerade med principen, men som inte omfattas av principen. Du kan välja att lägga till dessa användare i principen.

- **Flaggade användare**: Antalet användare som har problem. För närvarande rapporteras endast användare med upplåsta enheter under **Flaggade användare**.


## <a name="detailed-view"></a>Detaljerad vy
Du kommer till den detaljerade vyn av sammanfattningen genom att välja panelen **Användarstatus** (beroende på enhetens operativsystem) och panelen **Flaggade användare**.

### <a name="user-status"></a>Användarstatus
Du kan söka efter en enskild användare och kontrollera efterlevnadsstatusen för användaren. På bladet **Apprapportering** visas följande information för en vald användare:
- Enheter som är associerade med användarkontot

- Appar med en MAM-princip på enheten

- Status:

  - **Incheckad**: Principen har distribuerats till användaren och appen användes i arbetskontexten minst en gång.

  - **Inte incheckad:** Principen har distribuerats till användaren, men appen har inte använts i arbetskontexten sedan dess.

>[!NOTE]
> Om MAM-principen inte har distribuerats till de användare som du sökte efter visas ett meddelande om att inga MAM-principer tillämpas på användaren.

Visa rapporter för en användare genom att följa anvisningarna:

1.  Välj panelen **Sammanfattning** för att välja en användare.

    ![Skärmbild 3](../media/MAM-reporting-6.png)

2. På bladet **Apprapportering** som öppnas väljer du **Välj användare** för att söka efter en Azure Active Directory-användare.

    ![Alternativet Välj användare på bladet Apprapportering](../media/MAM-reporting-2.png)

3. Välj användaren i listan. Du kan se informationen om användarens kompatibilitetsstatus.

### <a name="flagged-users"></a>Flaggade användare
I den detaljerade vyn visas felmeddelandet, appen som användes när felet inträffade, enhetens operativsystem och en tidsstämpel.

## <a name="reporting-view"></a>Rapporteringsvy

Du kan hitta samma rapporter från den detaljerade vyn och ytterligare rapporter som hjälper dig med efterlevnadsstatusen för MAM-principer:

![Skärmbild-4](../media/MAM-reporting-7.png)

-   **Rapport om appskyddsanvändare:** Visar en översikt över samma information som du hittar i rapporten **Användarstatus** under avsnittet Detaljerad vy ovan.

-   **Rapport om appskyddsappar:** Tillhandahåller två olika statusar om appskydd som administratörer kan välja innan de skapar rapporten. Statusen kan vara skyddad eller oskyddad.

    -   Användarstatus för hanterad MAM-aktivitet (Skyddad): Den här rapporten ger en översikt över hur alla hanterade MAM-appar opererar, per användare.

        -   Den visar alla appar som är mål för MAM-principer för varje användare. Den visar även status för varje app, som incheckade med MAM-principer eller som mål för MAM-principer men inte incheckade.
<br></br>
    -   Användarstatus för icke-hanterad MAM-aktivitet (Oskyddad): Den här rapporten ger en översikt över hur MAM-aktiverade appar som är icke-hanterade opererar, per användare. Detta kan inträffa på grund av följande anledningar:

        -   De här apparna används antingen av en användare eller en app som för närvarande inte är mål för en MAM-princip.

        -   Alla appar är incheckade men kommer inte åt MAM-principer.

![Skärmbild-2](../media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Tabellgruppering

När data för **användarrapporten för appskydd** visas kan du sammanställa informationen enligt följande:

- **Verifieringsresultat:** Informationen visas grupperad efter appskyddsstatus, vilken kan vara fel, varning eller klar.
- **Appnamn:** Informationen visas grupperad efter appar (det faktiska appnamnet) som fel, varning eller klar.

## <a name="export-app-protection-activities-to-csv"></a>Exportera appskyddsaktiviteter till CSV

Du kan exportera alla dina appskyddsprincipsaktiviteter till en enda CSV-fil. Detta kan du ha nytta av om du vill analysera alla de appskyddsstatusar som rapporteras från användarna.

Generera appskyddsrapporten genom att följa dessa anvisningar:

1. Välj Appskyddsrapport på bladet Hantering av mobilappar i Intune.

    ![Skärmbild&6;](../media/app-protection-report-csv-2.png)

2. Välj först Ja om du vill spara rapporten, välj sedan Spara som och ange den mapp som du vill spara rapporten i.

    ![Skärmbild&7;](../media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Se även
[Hantera dataöverföring mellan iOS-appar](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Vad som händer när din Android-app hanteras med MAM-principer](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [Vad som händer när din iOS-app hanteras med MAM-principer](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Feb17_HO2-->


