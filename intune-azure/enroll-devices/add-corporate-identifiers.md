---
title: "Lägg till IMEI-identifierare i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs mer om hur du kan lägga till företagsidentifierare (IMEI-nummer) till Microsoft Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 0d7c8eedbdad917a43d43d2e79ead5663e8e2871
ms.lasthandoff: 02/18/2017

---

# <a name="add-corporate-identifiers"></a>Lägg till företagsidentifierare

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Du kan skapa en lista med IMEI-nummer (International Mobile Equipment Identity) för att identifiera dina företagsenheter. Enheterna behöver inte vara registrerade och har antingen statusen ”Registrerad” eller ”Ej kontaktad”. ”Ej kontaktad” innebär att enheten aldrig checkar in med Intune-tjänsten.

För att skapa listan, skapar du en lista med kommateckenavgränsade fält (.csv) i två kolumner men utan rubrik. Lägg till IMEI-identifieraren i den vänstra kolumnen och informationen i den högra kolumnen. Det maximala antalet rader i kolumnen är för närvarande 500.

Om du öppnar CSV-listan i en textredigerare ser den ut ungefär så här:

01 234567 890123, enhetsinformation</br>
02 234567 890123, enhetsinformation

**Lägga till en CSV-lista över företagets identifierare**

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Id:n för företagsenheter**.

3. Om du importerar en fil med ny information som kommer att skriva över befintlig information, så välj **Skriv över information för befintliga identifierare**. Då ersätts den befintliga informationen av den nya.

4. Navigera till IMEI CSV-filen och markera **Lägg till**.

**Ta bort en CSV-lista över företagets identifierare**

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Id:n för företagsenheter**.

3. Välj **Ta bort**.

