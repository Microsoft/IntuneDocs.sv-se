---
title: "Tilldela webbappar till Intune | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Lär dig hur du lägger till webbappar i Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 8b14b9dfef7100a86c338c362ba56be329a8639c

---

# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Lägga till webbappar i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på bladet **Intune**.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. Välj **Appinformation** på bladet **Lägg till app**.
7. Konfigurera följande information på bladet **Redigera app**. När du är klar klickar du på **Lägg till**:
    - **App-URL** – Ange webbadressen till webbplatsen där den app som du vill distribuera finns.
    - **Appnamn** – Ange namnet på appen så som det ska visas på företagsportalen.
    - **Appbeskrivning** – Ange en beskrivning för appen. Detta visas för slutanvändare i företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Kräv en hanterad webbläsare för att öppna den här länken** – När du distribuerar en länk till en webbplats eller en webbapp till användare kan de bara öppna den i Intune Managed Browser. Den här webbläsaren måste installeras på enheterna.
    - **Ladda upp ikon** – Ladda upp en ikon som ska associeras med appen. Den här ikonen visas med appen när användare söker i företagsportalen.
8. När du är klar väljer du **Spara** på bladet **Lägg till app**.

Den app som du har skapat visas i listan över appar där du kan välja att tilldela den till olika grupper. Mer information finns i [Tilldela appar till grupper](/intune-azure/manage-apps/deploy-apps).


<!--HONumber=Feb17_HO3-->


