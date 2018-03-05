---
title: "Lägga till Android Store-appar i Intune"
titleSuffix: Azure portal
description: "Läs mer om att lägga till Android Store-appar i Intune.”"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cdf00d8adc5a854f90b59c6066d6f0ab7c6ae94a
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-add-android-store-apps-to-microsoft-intune"></a>Så här lägger du till Android Store-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Innan du tilldelar en app till en enhet eller en grupp av användare måste du först lägga till appen i Microsoft Intune. Med följande anvisningar kan du lägga till en Android Store-app till Intune från Azure Portal.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. På bladet **Microsoft Intune** väljer du **Mobilappar**.
4. Välj **Appar** under avsnittet **Hantera** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. På bladet **Lägg till App** väljer du **Android** under de tillgängliga **Store-app**-typerna.
7. Välj **Konfigurera** för att konfigurera appinformationen med följande information: Beroende på vilken app du har valt kan vissa av värdena på det här bladet ha fyllts i automatiskt:
    - **Namn** – Ange namnet på appen så som det ska visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Beskrivning** – Ange en beskrivning för appen. Den här beskrivningen visas för användare i företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Webbadress till appbutik** – Ange webbadressen till appbutiken för den app som du vill skapa.
    - **Lägsta operativsystemversion** – Välj den lägsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** (valfritt) – Ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
    - **Sekretess-URL** (valfritt) – Ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
    - **Utvecklare** (valfritt) – Ange apputvecklarens namn.
    - **Ägare** (valfritt) – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** (valfritt) – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Logo** – (valfritt) Ladda upp en ikon som ska kopplas till appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
8. Klicka på **OK** när du har slutfört inställningarna för appinformationen.
9. Klicka på **Lägg till** för att lägga till appen.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. 

##<a name="next-steps"></a>Nästa steg

- [Så här tilldelar du appar till grupper](apps-deploy.md)