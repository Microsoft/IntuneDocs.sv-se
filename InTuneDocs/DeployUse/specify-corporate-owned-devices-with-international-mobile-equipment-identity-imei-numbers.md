---
title: "Ange företagsägda enheter med IMEI-nummer (International Mobile Equipment Identity) | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 398d93d4e2317d00a2f9d5f89966aaec3b942504
ms.openlocfilehash: af4b87eb8082ee5ff11cd2d42b788ad17b334bcb


---

# Ange enheter som ägs av företaget med IMEI-nummer (International Mobile Equipment Identity)
Med Microsoft Intune kan administratörer importera IMEI-nummer för mobilplattformar för att identifiera de mobila enheter som företaget äger. När de har registrerats i Intune kan enheter med importerade IMEI-tal kan visas under **Grupper** > **Översikt** > **Alla enheter** > **Förregistrerade företagsenheter** > **Av IMEI (alla plattformar)**.

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



<!--HONumber=Jun16_HO3-->


