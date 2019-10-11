---
title: Lägga till Android Store-appar i Microsoft Intune
titleSuffix: ''
description: Lär dig att lägga till Android Store-appar från Google Play-butiken i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea7db3cb6839a466044f83b1849a7f91f7de1822
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724613"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Lägga till Android Store-appar i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Innan du tilldelar en app till en enhet eller en grupp av användare måste du först lägga till appen i Microsoft Intune. 

## <a name="add-an-app"></a>Lägga till en app

Du kan lägga till en Android Store-app till Intune från Azure Portal genom att göra så här:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Klientappar** i **Intune**-fönstret.
4. I arbetsbelastningsfönstret **Klientappar** väljer du **Appar** under **Hantera**.
5. Välj **Lägg till**.
6. I fönstret **Lägg till App** väljer du **Android** under de tillgängliga **Store-app**-typerna.
7. Om du vill konfigurera information om appen väljer **Konfigurera** och ange följande information. För Android-appar går du till [Google Play Butik](https://play.google.com/store) och söker efter den app du vill distribuera. Välj appen och notera appinformationen. Beroende på vilken app du har valt kan det hända att några av värdena har fyllts i automatiskt.
    - **Namn**: Ange namnet på appen så som den ska visas i företagsportalen. Se till att alla appnamn du använder är unika. Om ett appnamn dupliceras visas endast ett namn för användare i företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Webbadress till appbutik**: Ange webbadressen till appbutiken för den app som du vill skapa.
    - **Lägsta operativsystemsversion**: Välj den tidigaste operativsystemsversion i listan som appen kan installeras i. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Kategori**: Du kan även välja en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Välj det här alternativet för att tydligt visa appsviten på företagsportalens huvudsida när användarna söker efter appar. Gäller för appar som distribueras med tillgänglig avsikt.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appens ägare, t.ex. *Personalavdelningen*.
    - **Kommentarer**: Alternativt kanske du vill ange kommentarer till appen.
    - **Logotyp**: Om du vill kan du ladda upp en ikon som ska kopplas till appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
8. Välj **OK**.
9. Välj **Lägg till**.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. 

## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md)
