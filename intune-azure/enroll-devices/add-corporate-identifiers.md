---
title: "Lägg till IMEI-identifierare till Intune | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs mer om hur du kan lägga till företagsidentifierare (IMEI-nummer) till Microsoft Intune. "
keywords: 
author: staciebarker
ms.author: stabark
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: e134a6e3ff143dacce1d70ef0ab44ade0722ed57

---

# <a name="add-corporate-identifiers"></a>Lägg till företagsidentifierare

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Du kan skapa en lista med IMEI-nummer (International Mobile Equipment Identity) för att identifiera dina företagsenheter. Enheterna behöver inte vara registrerade och har antingen statusen ”Registrerad” eller ”Ej kontaktad”. ”Ej kontaktad” innebär att enheten aldrig checkar in med Intune-tjänsten.

För att skapa listan, skapar du en lista med kommateckenavgränsade fält (.csv) i två kolumner men utan rubrik. Lägg till IMEI-identifieraren i den vänstra kolumnen och informationen i den högra kolumnen. Det maximala antalet rader i kolumnen är för närvarande 500.

Om du öppnar CSV-listan i en textredigerare ser den ut ungefär så här:

01 234567 890123, enhetsinformation</br>
02 234567 890123, enhetsinformation

**Lägga till en CSV-lista över företagets identifierare**

1. Välj **Fler tjänster** i Azure-portalen, skriv **Intune** i textrutan och välj sedan **Övrigt** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Id:n för företagsenheter**.

3. Om du importerar en fil med ny information som kommer att skriva över befintlig information, så välj **Skriv över information för befintliga identifierare**. Då ersätts den befintliga informationen av den nya.

4. Navigera till IMEI CSV-filen och markera **Lägg till**.

**Ta bort en CSV-lista över företagets identifierare**

1. Välj **Registrera enheter** på Intune-bladet och välj sedan **Id:n för företagsenheter**.

2. Välj **Ta bort**.



<!--HONumber=Feb17_HO1-->


