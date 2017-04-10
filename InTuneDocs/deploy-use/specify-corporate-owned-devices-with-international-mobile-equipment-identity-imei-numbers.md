---
title: Ange IMEI-nummer | Microsoft Docs
description: "Med Microsoft Intune kan administratörer importera IMEI-nummer för mobilenhetsplattformar för att identifiera företagsägda mobila enheter"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: 02743ee216ce09c74a9d0ab2455e826b36e8aa4a
ms.lasthandoff: 03/22/2017


---

# <a name="specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>Ange enheter som ägs av företaget med IMEI-nummer (International Mobile Equipment Identity)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Med Microsoft Intune kan administratörer importera och använda IMEI-nummer (International Mobile Equipment Identity) för mobilenhetsplattformar för att identifiera företagsägda mobila enheter. När enheterna har registrerats i Intune kan du se enheter som har importerade IMEI-nummer under **Grupper** > **Översikt** > **Alla enheter**. **Enhetsgrupp** visar en lista över enheter som har importerade IMEI-nummer med **Företag** i kolumnen **Ägarskap**.

1. Gå till [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) och välj **Grupper** &gt; **Alla enheter** &gt; **Företagets förregistrerade enheter** &gt; **Efter IMEI (alla plattformar)** och välj sedan **Lägg till enheter**. Du kan lägga till enheter på två sätt:

    -   **Överför en CSV-fil med serienummer** – Skapa en lista med två kolumner och kommaavgränsade värden (CSV-fil) utan sidhuvud och begränsa listan till 5 000 enheter eller 5 MB per CSV-fil. Informationsfältet får inte innehålla fler än 128 tecken.

        |||
        |-|-|
        |&lt;IMEI-nummer 1&gt;|&lt;Information om enhet nr 1&gt;|
        |&lt;IMEI-nummer 2&gt;|&lt;Information om enhet nr 2&gt;|
        CSV-filen när den visas i en textredigerare:

        ```
        01 234567 890123,device details
        02 234567 890123,device details
        ```

    -   **Lägg till enhetsinformation manuellt** – Ange IMEI-nummer och enhetsinformation för upp till 15 enheter.

   Fältet *Information* är för administrativ användning. Du kan ange information för att identifiera enheten i listan över företagsägda enheter som visas efter maskinvaru-ID. Informationen skickas inte till enheten, men den visas i Intune-konsolen.

2.   Välj **Nästa**.
3.  I rutan **Granska enheter** kan du kontrollera IMEI-numren för importerade enheter. Du kan också bestämma om du vill skriva över **informationen** för IMEI-nummer som importeras igen. Du kan avmarkera rutan **Skriv över** om du vill bevara den aktuella informationen. Importera IMEI-numren genom att klicka på **Slutför**.
4.  De importerade IMEI-numren och beskrivningarna läggs till i listan **Efter IMEI (alla plattformar)**.

> [!IMPORTANT]
> Om du importerar IMEI-nummer för Android-enheter bör du vara medveten om att vissa Android-enheter kan ha flera IMEI-nummer. Om du importerar ett IMEI-nummer men det inte är det IMEI-nummer som rapporterats till Intune av enheten så kommer enheten att klassificeras som en personlig enhet i stället för en enhet som ägs av företaget.

När en enhet som har ett IMEI-nummer registreras i Intune (vanligtvis när en användare installerar företagsportalappen och slutför registreringen) märks enheten som företagsägd och visas som registrerad i gruppen **IMEI-enheter**.

>[!NOTE]
> När din organisation migreras till den nya Azure-portalen ser du en ändring av den här funktionen. I den befintliga Intune-administratörskonsolen kan administratörer godkänna tillhörande information från en överförd CSV och skriva över befintlig information för enskilda maskinvaruidentifierare. I den nya Azure-portalen kan du automatiskt skriva över informationen för alla maskinvaruidentifierare eller ignorera all ny information för befintliga identifierare.

Detaljerade specifikationer om IMEI (International Mobile Equipment Identifiers) finns i [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

