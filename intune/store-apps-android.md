---
title: "Lägga till Android Store-appar i Intune"
titleSuffix: Azure portal
description: "Läs mer om att lägga till Android Store-appar i Intune.”"
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 09b5cf4bc97aa6a4d21068e96ab16f4a8f1a549f
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-add-android-store-apps-to-microsoft-intune"></a>Så här lägger du till Android Store-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på Intune-bladet.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. Välj **Appinformation** på bladet **Lägg till app**.
7. Konfigurera följande information på bladet **Redigera app**. När du är klar klickar du på **Lägg till**. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
    - **Appnamn** – Ange namnet på appen så som det ska visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Appbeskrivning** – Ange en beskrivning för appen. Detta visas för användare i företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **App Store-URL** – Ange App Store-URL:en för den app som du vill skapa.
    - **Minsta operativsystem** – Välj den minsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Ladda upp ikon** – Överför en ikon som ska kopplas till appen. Den här ikonen visas med appen när användare söker i företagsportalen.
8. När du är klar väljer du **Spara** på bladet **Lägg till app**.

Den app som du har skapat visas i listan över appar där du kan välja att tilldela den till olika grupper. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).