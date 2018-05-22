---
title: Lägga till Android Store-appar i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till Android Store-appar i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f62cb3a99a9cfd328cc041f095b0980eacc99852
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Lägga till Android Store-appar i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Innan du tilldelar en app till en enhet eller en grupp av användare måste du först lägga till appen i Microsoft Intune. Du kan lägga till en Android Store-app till Intune från Azure Portal genom att göra så här:

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**.  
    Intune finns i avsnittet **Övervakning och hantering**.
1. Välj **Enheter** i **Mobilappar**-fönstret.
2. I arbetsbelastningsfönstret **Mobilappar** under **Hantera**, väljer du **Appar**.
3. Välj **Lägg till**.
4. I fönstret **Lägg till App** väljer du **Android** under de tillgängliga **Store-app**-typerna.
5. Om du vill konfigurera information om appen väljer **Konfigurera** och ange följande information.  
    Beroende på vilken app du har valt kan det hända att några av värdena har fyllts i automatiskt.
    - **Namn**: Ange namnet på appen så som det ska visas i företagsportalen. Se till att alla appnamn du använder är unika. Om ett appnamn dupliceras visas endast ett namn för användare i företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Webbadress till appbutik**: Ange webbadressen till appbutiken för den app som du vill skapa.
    - **Lägsta operativsystemversion**: Välj på listan den tidigaste operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen**: Välj det här alternativet för att visa appsviten på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL**: Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL**: Alternativt kan du ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appägaren, t.ex. *Personalavdelningen*.
    - **Anteckningar**: Alternativt kanske du vill ge kommentarer som du vill koppla till den här appen.
    - **Logo**: Om du vill kan du ladda upp en ikon som ska kopplas till appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
1. Välj **OK**.
2. Välj **Lägg till**.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. 

## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md)