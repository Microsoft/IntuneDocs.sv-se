---
title: "Lägg till IMEI-identifierare i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs mer om hur du kan lägga till företagsidentifierare (IMEI-nummer) till Microsoft Intune. "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: d8cb15d1b8c1c100f15084e43d2c3c4633fd64b5
ms.openlocfilehash: f12d538b1f4cd327b893d234f2b558185cdd9d85
ms.lasthandoff: 03/09/2017

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

> [!IMPORTANT]
> Vissa Android-enheter har flera IMEI-nummer. Intune inventerar ett IMEI-nummer per enhet. Om du importerar ett IMEI-nummer men det inte är det IMEI-nummer som är inventerat i Intune så kommer enheten att klassificeras som en personlig enhet i stället för en enhet som ägs av företaget. Om du importerar flera IMEI-nummer för en enhet så visas registreringsstatus för icke-inventerade nummer som **Okänt**.

**Ta bort en CSV-lista över företagets identifierare**

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Id:n för företagsenheter**.

3. Välj **Ta bort**.

