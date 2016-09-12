---
title: Ange IMEI-nummer | Microsoft Intune
description: "Med Microsoft Intune kan administratörer importera IMEI-nummer för plattformar för mobila enheter för att identifiera företagsägda mobila enheter"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: 4e2092182dbda4523c19afeabc34aa0166962c40


---

# Ange enheter som ägs av företaget med IMEI-nummer (International Mobile Equipment Identity)
Med Microsoft Intune kan administratörer importera IMEI-nummer för mobilplattformar för att identifiera de mobila enheter som företaget äger. När enheterna har registrerats i Intune visas enheter med importerade IMEI-nummer under **Grupper** > **Översikt** > **Alla enheter**. I **Enhetsgrupp** visas enheter med importerade IMEI-nummer som **Företag** i kolumnen **Ägarskap**.

1. Gå till [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) och välj **Grupper** &gt; **Alla enheter** &gt; **Alla förregistrerade företagsenheter** &gt; **Av IMEI (alla plattformar)** och välj sedan **Lägg till enheter…**. Du kan lägga till enheter på två sätt:

    -   **Överför en CSV-fil som innehåller serienummer** – Skapa en kommaavgränsad lista med två kolumner utan rubrik som är begränsad till 5 000 enheter eller 5 MB per CSV-fil.

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;Information om enhet nr 1&gt;|
        |&lt;IMEI #2&gt;|&lt;Information om enhet nr 2&gt;|
        CSV-filen när den visas i en textredigerare:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Information om manuellt tillagd enhet** – Ange IMEI-nummer och enhetsinformation om upp till fem enheter

   *Informationen* är avsedd för administrativt bruk för att identifiera vilket IMEI-nummer som är associerat med en viss enhet. Informationen skickas inte till enheten, men den visas i Intune-konsolen.

2.   Välj **Nästa**.
3.  På sidan **Granska enheter** kan du granska vilka IMEI-nummer som har importerats. Du kan också bestämma om du vill skriva över **informationen** för IMEI-nummer som importeras på nytt. Du kan avmarkera kryssrutan **Skriv över** om du vill bevara den aktuella informationen. Importera IMEI-numren genom att klicka på **Slutför**.
4.  IMEI-numren och beskrivningarna läggs till i listan **Efter IMEI (alla plattformar)**.

När en enhet som har ett sådant IMEI-nummer registreras (vanligtvis när en användare installerar företagsportalappen och gör registreringen) märks enheten som en företagsägd enhet och visas som registrerad i gruppen **IMEI-enheter**.



<!--HONumber=Jul16_HO4-->


