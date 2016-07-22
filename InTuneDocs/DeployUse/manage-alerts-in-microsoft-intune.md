---
title: Hantera aviseringar | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74dc4ce4-21da-4f40-a07f-3eea34561eee
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: bfea7213f67b55807045bfd8b29fdb083b841a56


---

# Hantera aviseringar i Microsoft Intune
Använd arbetsytan **Aviseringar** i administratörskonsolen för Intune när du ska utvärdera den övergripande hälsan för enheter i din organisation och för att identifiera problem.

#### Visa aktiva aviseringar

1.  Gör något av följande i administratörskonsolen för Intune:

    -   **Om du vill visa allmän information om aviseringar**, inklusive de tre viktigaste aviseringarna och det totala antalet aktiva aviseringar, klickar du på **Systemöversikt**. Du kan klicka på länkarna i aviseringarna om du vill se mer detaljerad information.

    -   **För att visa sammanfattningar för avisering**, klicka på **Aviseringar &gt; Översikt**. Området **Aviseringstypssammanfattning** visar en sammanfattning över olika aviseringar på sidan **Aviseringsöversikt**. Viktiga aviseringar visas först. Du kan klicka på länkarna i aviseringarna om du vill se mer detaljerad information.

        > [!NOTE]
        > I vissa fall kan en varningstyp visas mer än en gång i listan **Aviseringstypssammanfattning**.
        > 
        > Följande instanser av aviseringstypen för ledigt logiskt diskutrymme kan t.ex. förekomma i listan:
        > 
        > -   3 Ledigt logiskt diskutrymme
        > -   2 Ledigt logiskt diskutrymme
        > 
        > Detta inträffar när samma aviseringstyp genereras för enheter som körs under olika operativsystem. I det här exemplet kan den första instansen av aviseringen, 3 Ledigt logiskt diskutrymme, ha genererats av datorer som kör Windows® 7. Den andra förekomsten av aviseringstypen kan ha genererats av datorer som kör Windows Vista®.

    -   **Visa alla aktiva aviseringar**, klicka på **Aviseringar &gt; Alla aviseringar**. En lista över alla aktiva aviseringar visas med följande kolumner på sidan **Aviseringar**:

        1.  **Namn** – namnet på den aviseringstyp som skapade aviseringen.

        2.  **Källa** – en länk till aviseringens källa. Om tröskelvärdet för visning av aviseringstypen har satts till **Visa alla** visar den här länken en enskild enhet. Om tröskelvärdet för visning av aviseringstypen har satts till ett värde visar länken en lista över alla enheter som påverkas av aviseringen.

        3.  **Senast uppdaterad**– detta anger den tidpunkt då aviseringen senast ändrades. Om en avisering är stängd visas den tid då aviseringen stängdes.

        4.  **Allvarlighetsgrad**– anger aviseringens allvarlighetsgrad

## Visa anslagstavleaviseringar
Anslagstavleaviseringar tillhandahåller viktig tjänstinformation om t.ex. kommande tjänstuppgraderingar, underhåll eller avbrott. Visa och hantera anslagstavleaviseringar på följande sätt.

#### Visa och hantera anslagstavleaviseringar

1.  I administratörskonsolen för Intune klickar du på **Systemöversikt**.

2.  Om det finns några viktiga tjänstmeddelanden visas de i området **Anslagstavla**.

3.  Om du vill exportera en anslagstavleavisering till en CSV- eller HTML-fil klickar du på **Aviseringar &gt; Alla aviseringar &gt; Meddelanden**. Markera ett meddelande, klicka på listexporteringsikonen och följ anvisningarna.

## Granska Intune-status
Visa systemstatussammanfattningar för Endpoint Protection, uppdateringar, agenthälsa, principer och program på arbetsytan **Systemöversikt**, så kan du lättare identifiera och prioritera problem som kräver din omedelbara uppmärksamhet. En länk till sammanfattningen **Tjänststatus** ges också i felmeddelanden vid systemavbrott. Sammanfattningen **Tjänststatus** innehåller information om problemen vid respektive plats och visar tidpunkten för senaste uppdatering.

#### Visa status för din prenumeration

1.  I administratörskonsolen för Intune klickar du på **Systemöversikt**.

2.  Du kan undersöka statusen för de olika Microsoft Intune-komponenterna i området **Systemstatus**. Många av objekten innehåller länkar genom vilka du kan få ytterligare information. Under **Endpoint Protection** kan du t.ex. välja det antal instanser som ska visas på arbetsytan **Endpoint Protection** med en lista över skadlig kod som har identifierats. När du väljer antal enheter visas arbetsytan **Grupper** med en lista över enheter där skadlig kod har påträffats.

## Stänga och återaktivera aviseringar
Intune-aviseringar förblir aktiva tills någon av följande typer av händelser inträffar:

-   Det problem som orsakade aviseringen har lösts.

-   Aviseringen har stängts manuellt.

-   Fem dagar har passerat sedan varningen genererades. Aviseringen upphör att gälla efter 45 dagar och stängs automatiskt.

Aviseringar som har markerats som stängda tas bort permanent efter 90 dagar.

#### Stänga en varning manuellt

1.  Gör något av följande i administratörskonsolen för Intune:

    1.  **För att stänga en avisering från aviseringslistan** – Klicka på **Aviseringar &gt; Alla aviseringar**. Välj en avisering och klicka sedan på **Stäng avisering**.

    2.  **För att stänga en avisering för en specifik enhet** – Klicka på **Grupper &gt; Alla enheter**. Välj en enhet och klicka på **Visa egenskaper**. Klicka sedan på fliken **Aviseringar**, markera en varning och klicka sedan på **Stäng avisering**.

    3.  **Stänga en anslagstavleavisering** – Klicka på **Systemöversikt**. Klicka på **X** bredvid anslagstavleaviseringen.

#### Visa och återaktivera stängda aviseringar

1.  I administratörskonsolen för Intune klickar du på **Aviseringar &gt; Alla aviseringar**.

2.  Klicka på **Stängd** i listan **Filter**.

    Aviseringarnas namn och ytterligare information visas i listhanteringsfönstret. Information om de markerade varningarna visas i förhandsgranskningsfönstret.

3.  Om du vill återaktivera den markerade aviseringen klickar du på **Återaktivera avisering**.

### Se även
[Håll dig informerad med aviseringar från Microsoft Intune](get-notified-by-alerts.md)




<!--HONumber=Jun16_HO4-->


