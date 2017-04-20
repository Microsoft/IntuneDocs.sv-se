---
title: "Lägg till IMEI-identifierare i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs mer om hur du kan lägga till företagsidentifierare (IMEI-nummer) till Microsoft Intune. "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 4ebd74c77145464574a1fed878ec4dbc2eb3c271
ms.openlocfilehash: 7bb8168c442a3340e8c185f1908acd9be15cab05
ms.lasthandoff: 04/05/2017

---

# <a name="add-corporate-identifiers"></a>Lägg till företagsidentifierare

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Som IT-administratör kan du skapa och importera en fil med kommateckenavgränsade värden (CSV) som innehåller en lista med IMEI-nummer (International Mobile Equipment Identity) som identifierar företagsägda enheter. Varje IMEI-nummer kan innehålla information som anges i listan för administrativa ändamål.

När du överför serienummer för företagsägda iOS-enheter måste de kopplas till en profil för företagsregistrering. Enheter måste sedan registreras med antingen Apples enhetsregistreringsprogram (DEP) eller Apple Configurator om de ska visas som företagsägda. 

## <a name="create-a-csv-file"></a>Skapa en CSV-fil
För att skapa listan, skapar du en lista med kommateckenavgränsade fält (.csv) i två kolumner men utan rubrik. Lägg till IMEI-identifieraren i den vänstra kolumnen och informationen i den högra kolumnen. Informationen är begränsad till 128 tecken. Den aktuella gränsen är 500 rader per CSV-fil.

**Överför en CSV-fil med serienummer** – Skapa en lista med två kolumner och kommaavgränsade värden (CSV-fil) utan sidhuvud och begränsa listan till 5 000 enheter eller 5 MB per CSV-fil.

|||
|-|-|
|&lt;IMEI-nummer 1&gt;|&lt;Information om enhet nr 1&gt;|
|&lt;IMEI-nummer 2&gt;|&lt;Information om enhet nr 2&gt;|

    This .csv file when viewed in a text editor appears as:

    ```
    01 234567 890123,device details
    02 234567 890123,device details
    ```

**Lägga till en CSV-lista över företagets identifierare**

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Id:n för företagsenheter**.

3. Om du importerar en fil med ny information som kommer att skriva över befintlig information, så välj **Skriv över information för befintliga identifierare**. Då ersätts den befintliga informationen av den nya.

4. Navigera till IMEI CSV-filen och markera **Lägg till**.

> [!IMPORTANT]
> Vissa Android-enheter har flera IMEI-nummer. Intune inventerar ett IMEI-nummer per enhet. Om du importerar ett IMEI-nummer men det inte är det IMEI-nummer som är inventerat i Intune så kommer enheten att klassificeras som en personlig enhet i stället för en enhet som ägs av företaget. Om du importerar flera IMEI-nummer för en enhet så visas registreringsstatus för icke-inventerade nummer som **Okänt**.

Enheterna behöver inte vara registrerade när de har importerats och kan antingen ha statusen **Registrerad** eller **Ej kontaktad**. **Ej kontaktad** innebär att enheten aldrig har kommunicerat med Intune-tjänsten.

## <a name="delete-a-csv-list"></a>Ta bort en CSV-lista

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Id:n för företagsenheter**.

3. Välj **Ta bort**.

Detaljerade specifikationer om IMEI (International Mobile Equipment Identifiers) finns i [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

