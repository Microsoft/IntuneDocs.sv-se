---
# required metadata

title: Ange företagsägda enheter med IMEI-nummer (International Mobile Equipment Identity) | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ange enheter som ägs av företaget med IMEI-nummer (International Mobile Equipment Identity)
Med Microsoft Intune kan administratörer importera IMEI-nummer för mobilplattformar för att identifiera de mobila enheter som företaget äger. När enheterna är registrerade i Intune märks de enheter som har importerade IMEI-nummer som företagsenheter. Det gör att det går att använda andra principer för dessa enheten än för personalens privata enheter.

1. I [Microsoft Intune Administrationskonsol](http://manage.microsoft.com) går du till **Grupper** &gt; **Alla enheter** &gt; **Alla företagets förregistrerade enheter** &gt; **Efter IMEI (alla plattformar)** och klickar sedan på **Lägg till enheter**. Du kan lägga till enheter på två sätt:

    -   **Överför en CSV-fil som innehåller serienummer** – Skapa en kommaavgränsad lista med två kolumner utan rubrik som är begränsad till 5 000 enheter eller 5 MB per CSV-fil.

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;Information om enhet nr 1&gt;|
        |&lt;IMEI #2&gt;|&lt;Information om enhet nr 2&gt;|
        CSV-filen när den visas i en textredigerare:

        ```
        AA-BBBBBB-CCCCCC-D,PO 1234
        AA-BBBBBB-CCCCCC-E,PO 1234
        ```

    -   **Information om manuellt tillagd enhet** – Ange IMEI-nummer och enhetsinformation om upp till fem enheter

   *Informationen* är avsedd för administrativt bruk för att identifiera vilket IMEI-nummer som är associerat med en viss enhet. Informationen skickas inte till enheten, men den visas i Intune-konsolen.

2.   Klicka på **Nästa**
3.  På sidan **Granska enheter** kan du granska vilka IMEI-nummer som har importerats. Du kan också bestämma om du vill skriva över **informationen** för IMEI-nummer som importeras på nytt. Du kan avmarkera kryssrutan **Skriv över** om du vill bevara den aktuella informationen. Klicka på **Slutför** om du vill importera IMEI-numren.
4.  IMEI-numren och beskrivningarna läggs till i listan **Efter IMEI (alla plattformar)**.

När en enhet som har ett sådant IMEI-nummer registreras (vanligtvis när en användare installerar företagsportalappen och gör registreringen) märks enheten som en företagsägd enhet och visas som registrerad i gruppen **IMEI-enheter**.


<!--HONumber=May16_HO2-->


