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
ms.sourcegitcommit: 15415f9f31d520d66257df3a7e134e4b1de8467c
ms.openlocfilehash: 8c9e6b39ee01697d993e5738ec35e8a64fc8e236
ms.lasthandoff: 04/07/2017

---

# <a name="add-corporate-identifiers"></a>Lägg till företagsidentifierare

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Som IT-administratör kan du skapa och importera en fil med kommateckenavgränsade värden (CSV) som innehåller en lista med IMEI-nummer (International Mobile Equipment Identity) som identifierar företagsägda enheter. Varje IMEI-nummer kan innehålla information som anges i listan för administrativa ändamål.

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

## <a name="add-corporate-identifiers"></a>Lägg till företagsidentifierare
För att skapa listan, skapar du en lista med kommateckenavgränsade fält (.csv) i två kolumner men utan rubrik. Lägg till IMEI-identifieraren i den vänstra kolumnen och informationen i den högra kolumnen. Informationen är begränsad till 128 tecken och används endast i administrationssyfte. Informationen visas inte på enheten. Den aktuella gränsen är 500 rader per CSV-fil.

**Överför en CSV-fil med serienummer** – Skapa en lista med två kolumner och kommaavgränsade värden (CSV-fil) utan sidhuvud och begränsa listan till 5 000 enheter eller 5 MB per CSV-fil.

|||
|-|-|
|&lt;IMEI-nummer 1&gt;|&lt;Information om enhet nr 1&gt;|
|&lt;IMEI-nummer 2&gt;|&lt;Information om enhet nr 2&gt;|

CSV-filen när den visas i en textredigerare:

```
01 234567 890123,device details
02 234567 890123,device details
```


> [!IMPORTANT]
> Vissa Android-enheter har flera IMEI-nummer. Intune inventerar ett IMEI-nummer per enhet. Om du importerar ett IMEI-nummer men det inte är det IMEI-nummer som är inventerat i Intune så kommer enheten att klassificeras som en personlig enhet i stället för en enhet som ägs av företaget. Om du importerar flera IMEI-nummer för en enhet så visas registreringsstatus för icke-inventerade nummer som **Okänt**.

**Lägga till en CSV-lista över företagets identifierare**

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. På bladet Intune väljer du **Enhetsregistrering** > **Registreringsbegränsningar**, **ID:n för företagsenheter** och klickar sedan på **Lägg till**.

3. På bladet **Lägg till identifierare** anger du ID-typ, **IMEI**. Du kan ange om tidigare importerade siffror ska **skriva över information för befintliga identifierare**.  

4. Klicka på mappikonen och ange sökvägen till listan du vill importera. Navigera till IMEI CSV-filen och markera **Lägg till**.

Enheterna behöver inte vara registrerade när de har importerats och kan antingen ha statusen **Registrerad** eller **Ej kontaktad**. **Ej kontaktad** innebär att enheten aldrig har kommunicerat med Intune-tjänsten.

## <a name="delete--corporate-identifiers"></a>Ta bort företagsidentifierare

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. På bladet Intune väljer du **Enhetsregistrering** > **Registreringsbegränsningar**, väljer **ID:n för företagsenheter** och **Ta bort**.

3. På bladet **Ta bort identifierare** bläddrar du till CSV-filen med enhets-ID:n att ta bort och klickar sedan på **Ta bort**.

## <a name="imei-specifications"></a>IMEI-specifikationer
Detaljerade specifikationer om IMEI (International Mobile Equipment Identifiers) finns i [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

