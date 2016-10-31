---
title: Ange IMEI-nummer | Microsoft Intune
description: "Med Microsoft Intune kan administratörer importera IMEI-nummer för mobilenhetsplattformar för att identifiera företagsägda mobila enheter"
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: c6b01a5efc0f60622b95623fd91f192c267ff766
ms.openlocfilehash: 9bd2b4bb676e23712c0a668161b81c4e352bce87


---

# Ange enheter som ägs av företaget med IMEI-nummer (International Mobile Equipment Identity)
Med Microsoft Intune kan administratörer importera och använda IMEI-nummer (International Mobile Equipment Identity) för mobilenhetsplattformar för att identifiera företagsägda mobila enheter. När enheterna har registrerats i Intune kan du se enheter som har importerade IMEI-nummer under **Grupper** > **Översikt** > **Alla enheter**. **Enhetsgrupp** visar en lista över enheter som har importerade IMEI-nummer med **Företag** i kolumnen **Ägarskap**.

1. Gå till [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) och välj **Grupper** &gt; **Alla enheter** &gt; **Företagets förregistrerade enheter** &gt; **Efter IMEI (alla plattformar)** och välj sedan **Lägg till enheter**. Du kan lägga till enheter på två sätt:

    -   **Överför en CSV-fil med serienummer** – Skapa en lista med två kolumner och kommaavgränsade värden (CSV-fil) utan sidhuvud och begränsa listan till 5 000 enheter eller 5 MB per CSV-fil.

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;Information om enhet nr 1&gt;|
        |&lt;IMEI #2&gt;|&lt;Information om enhet nr 2&gt;|
        CSV-filen när den visas i en textredigerare:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Lägg till enhetsinformation manuellt** – Ange IMEI-nummer och enhetsinformation för upp till fem enheter.

   *Informationen* är avsedd för administrativ användning och hjälper dig att identifiera vilket IMEI-nummer som associeras med en viss enhet. Informationen skickas inte till enheten, men den visas i Intune-konsolen.

2.   Välj **Nästa**.
3.  I rutan **Granska enheter** kan du kontrollera IMEI-numren för importerade enheter. Du kan också bestämma om du vill skriva över **informationen** för IMEI-nummer som importeras igen. Du kan avmarkera rutan **Skriv över** om du vill bevara den aktuella informationen. Importera IMEI-numren genom att klicka på **Slutför**.
4.  De importerade IMEI-numren och beskrivningarna läggs till i listan **Efter IMEI (alla plattformar)**.

När en enhet som har ett IMEI-nummer registreras i Intune (vanligtvis när en användare installerar företagsportalappen och slutför registreringen) märks enheten som företagsägd och visas som registrerad i gruppen **IMEI-enheter**.



<!--HONumber=Oct16_HO3-->


