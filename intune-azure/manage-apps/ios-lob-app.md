---
title: "Lägga till branschspecifika iOS-appar i Intune | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs mer om att lägga till branschspecifika iOS-appar i Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 424fae862592c1ab5b4221fb5ad40a52c39f6760
ms.openlocfilehash: d8615611eb715da66b1cf0972b885fbccb12fe6a

---

# <a name="how-to-add-ios-line-of-business-lob-apps-to-intune"></a>Så här lägger du till branschspecifika iOS-appar i Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Steg 1 – Ange platsen för programinstallationsfilen

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på Intune-bladet.
4. Välj Hantera > **Appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. Välj **Programinstallationsfil** på bladet **Lägg till app**.
7. Klicka på bläddringsknappen på bladet **Välj installationsfil**, bläddra fram till iOS-appinstallationsfilen (med filnamnstillägget .ipa) och klicka sedan på **OK**.

## <a name="step-2---configure-app-information"></a>Steg 2 – Konfigurera information om appen

1. Konfigurera följande information på bladet **Redigera app**. När du är klar klickar du på **Lägg till**. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
    - **Appnamn** – Ange namnet på appen så som det ska visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Appbeskrivning** – Ange en beskrivning för appen. Detta visas för användare i företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Tillämplig enhetstyp** – Ange om den här appen ska kunna installeras på iPad-, iPhone- eller kompatibla iPod-enheter.
    - **Minsta operativsystem** – Välj den minsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Ladda upp ikon** – Överför en ikon som ska kopplas till appen. Den här ikonen visas med appen när användare söker i företagsportalen.
2. När du är klar väljer du **Spara** på bladet **Lägg till App**.

Den app som du har skapat visas i listan över appar där du kan välja att tilldela den till olika grupper. Mer information finns i [Tilldela appar till grupper](/intune-azure/manage-apps/deploy-apps).


<!--HONumber=Feb17_HO1-->


