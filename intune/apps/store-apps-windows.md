---
title: Lägga till Microsoft Store-appar i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till appar från Microsoft Store (Windows Store) i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c19d14b2f2cfa838d79af1c6fbb3c3500004e56e
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74548027"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Lägga till Microsoft Store-appar i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Innan du kan tilldela, övervaka, konfigurera eller skydda appar måste du lägga till dem till Intune. 

## <a name="add-an-app-to-intune"></a>Lägga till en app i Intune
Du kan lägga till en Microsoft-Store-app i Intune genom att göra följande:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Klientappar** i **Intune**-fönstret.
4. I arbetsbelastningsfönstret **Klientappar** väljer du **Appar** under **Hantera**.
5. Välj **Lägg till** i fönsterrutan **Appar**.
6. I fönsterrutan **Lägg till app** väljer du **Windows Phone 8.1** som **Apptyp** och väljer sedan **Appinformation**.
7. Lägg till appinformationen i fönstret **Appinformation**. Beroende på vilken app du har valt kan det hända att några av värdena i det här fönstret har fyllts i automatiskt:
    - **Namn**: Ange namnet på appen så som den ska visas i företagsportalen. Se till att alla appnamn du använder är unika. Om ett appnamn dupliceras visas endast ett namn för användare i företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Webbadress till appbutik**: Skriv webbadressen till App Store för den app som du vill skapa. Du hittar webbadressen genom att söka i [Microsoft Store](https://store.microsoft.com) efter det önskade programmet. Använd webbadressen från webbläsarens adressfält.
    - **Kategori**: Du kan även välja en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Välj det här alternativet för att tydligt visa appsviten på företagsportalens huvudsida när användarna söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appens ägare, t.ex. *Personalavdelningen*.
    - **Kommentarer**: Alternativt kanske du vill ange kommentarer till appen.
    - **Logotyp**: Om du vill kan du ladda upp en ikon som ska kopplas till appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
8. Välj **OK**.
9. Välj **Lägg till**.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Microsoft Store-appar kan endast tilldelas till grupper med tilldelningstypen **Tillgängligt för registrerade enheter** (användarna installerar appen från företagsportalappen eller webbplatsen för företagsportalen).

## <a name="next-steps"></a>Nästa steg
- [Tilldela appar till grupper](apps-deploy.md)
