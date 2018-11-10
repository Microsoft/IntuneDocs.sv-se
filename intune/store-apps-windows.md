---
title: Lägga till Microsoft Store-appar i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till appar från Microsoft Store (Windows Store) i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: da10455cd6dc3cfbda23726832c539c206aea18c
ms.sourcegitcommit: 814d1d473de2de2e735efab826b1091de2b093f5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025159"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Lägga till Microsoft Store-appar i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Innan du kan tilldela, övervaka, konfigurera eller skydda appar måste du lägga till dem till Intune. 

## <a name="add-an-app-to-intune"></a>Lägga till en app i Intune
Du kan lägga till en Microsoft-Store-app i Intune genom att göra följande:

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**.  
    Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** i **Intune**-fönstret.
4. I arbetsbelastningsfönstret **Klientappar** väljer du **Appar** under **Hantera**.
5. Välj **Lägg till** i fönsterrutan **Appar**.
6. I fönsterrutan **Lägg till app** väljer du **Windows Phone 8.1** som **Apptyp** och väljer sedan **Appinformation**.
7. Lägg till appinformationen i fönstret **Appinformation**. Beroende på vilken app du har valt kan det hända att några av värdena i det här fönstret har fyllts i automatiskt:
    - **Namn**: Ange namnet på appen så som det ska visas i företagsportalen. Se till att alla appnamn du använder är unika. Om ett appnamn dupliceras visas endast ett namn för användare i företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Webbadress till appbutik**: Ange App Store-URL:en för den app som du vill skapa.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen**: Välj det här alternativet för att visa appsviten på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL**: Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL**: Alternativt kan du ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appägaren, t.ex. *Personalavdelningen*.
    - **Anteckningar**: Alternativt kanske du vill ge kommentarer som du vill koppla till den här appen.
    - **Logo**: Om du vill kan du ladda upp en ikon som ska kopplas till appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
8. Välj **OK**.
9. Välj **Lägg till**.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Microsoft Store-appar kan endast tilldelas till grupper med tilldelningstypen **Tillgängligt för registrerade enheter** (användarna installerar appen från företagsportalappen eller webbplatsen för företagsportalen).

## <a name="next-steps"></a>Nästa steg
- [Tilldela appar till grupper](apps-deploy.md)
