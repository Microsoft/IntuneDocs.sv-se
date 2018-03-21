---
title: "Så här lägger du till Windows Store-appar i Microsoft Intune"
titleSuffix: 
description: "Läs mer om att lägga till Windows Store-appar i Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e2280ad72bbd353d80af316cde436e8ffc79d1f
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>Så här lägger du till Windows Store-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Innan du kan tilldela, övervaka, konfigurera eller skydda appar måste du lägga till dem till Intune. Använd följande steg om du vill lägga till en Windows Store-app i Microsoft Intune.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning + hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. I fönstret **Lägg till app** väljer du en **Apptyp** för **Windows** och **Appinformation**.
7. Konfigurera följande information i fönstret **Appinformation**. När du är klar klickar du på **OK**. Beroende på vilken app du har valt kan det hända att några av värdena i det här fönstret har fyllts i automatiskt:
    - **Namn** – Ange namnet på appen så som det ska visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Beskrivning** – Ange en beskrivning av appen som ska visas för användare på företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Webbadress till appbutik** – Ange webbadressen till appbutiken för den app som du vill skapa.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna eller en kategori som du har skapat, vilket gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Logo** – Ladda upp en ikon som är associerad med appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
8. När du är klar väljer du **Lägg till** i fönstret **Lägg till app**.

Den app som du har skapat visas i listan över appar där du kan välja att tilldela den till olika grupper. 

## <a name="next-steps"></a>Nästa steg

- [Så här tilldelar du appar till grupper](apps-deploy.md)