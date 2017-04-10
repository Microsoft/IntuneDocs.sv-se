---
title: "Så här lägger du till branschspecifika Android-appar i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs mer om att lägga branschspecifika Android-appar i Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: af0b2bd72ae262d10e1a18c0d242b1816819c677
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-add-android-line-of-business-lob-apps-to-microsoft-intune"></a>Så här lägger du till branschspecifika Android-appar i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Steg 1 – Ange platsen för programinstallationsfilen

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. Välj **Programinstallationsfil** på bladet **Lägg till app**.
Klicka på bläddringsknappen på bladet **Välj installationsfil**, bläddra fram till Android-appinstallationsfilen (med filnamnstillägget .apk) och klicka sedan på **OK**.

## <a name="step-2---configure-app-information"></a>Steg 2 – Konfigurera information om appen

1. Välj **Appinformation** på bladet **Lägg till app**.
2. Konfigurera följande information på bladet **Redigera app**. När du är klar klickar du på **Lägg till**. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
    - **Appnamn** – Ange namnet på appen så som det ska visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Appbeskrivning** – Ange en beskrivning för appen. Detta visas för användare i företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Minsta operativsystem** – Välj den minsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Ladda upp ikon** – Överför en ikon som ska kopplas till appen. Den här ikonen visas med appen när användare söker i företagsportalen.
3. När du är klar väljer du **Spara** på bladet **Lägg till app**.

Den app som du har skapat visas i listan över appar där du kan välja att tilldela den till olika grupper. Mer information finns i [Tilldela appar till grupper](/intune-azure/manage-apps/deploy-apps).

