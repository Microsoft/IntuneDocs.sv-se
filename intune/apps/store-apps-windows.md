---
title: Lägga till Microsoft Store-appar i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till appar från Microsoft Store (Windows Store) i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
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
ms.openlocfilehash: 8743af2a05f6daebca5e1394ba5b7b8f13fcf7e3
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754923"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Lägga till Microsoft Store-appar i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Innan du kan tilldela, övervaka, konfigurera eller skydda appar måste du lägga till dem till Intune. 

## <a name="add-an-app-to-intune"></a>Lägga till en app i Intune
Du kan lägga till en Microsoft-Store-app i Intune genom att göra följande:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj **Windows Store-app** i rutan **Välj apptyp** bland de tillgängliga typerna av **Store-appar**.
4. Klicka på **Välj**. Stegen **Lägg till app** visas.
5. Om du vill konfigurera **Appinformation** för Windows Store-appar, så gå till [Microsoft Store](https://www.microsoft.com/store/apps) och sök efter den app som du vill distribuera. Visa appsidan och notera appinformationen. 
6. Lägg till information om appen i fönstret **Appinformation**:
    - **Namn**: Ange namnet på appen så som den ska visas i företagsportalen. Se till att alla appnamn du använder är unika. Om ett appnamn dupliceras visas endast ett namn för användare i företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Webbadress till appbutik**: Skriv webbadressen till App Store för den app som du vill skapa. Du hittar webbadressen genom att söka i [Microsoft Store](https://www.microsoft.com/store/apps) efter det önskade programmet. Använd webbadressen från webbläsarens adressfält.
    - **Kategori**: Du kan även välja en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Välj det här alternativet för att tydligt visa appsviten på företagsportalens huvudsida när användarna söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appens ägare, t.ex. *Personalavdelningen*.
    - **Kommentarer**: Alternativt kanske du vill ange kommentarer till appen.
    - **Logotyp**: Om du vill kan du ladda upp en ikon som ska kopplas till appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
7. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.
8. Klicka på **Välj omfångstaggar** om du vill lägga till omfångstaggar för appen. Mer information finns i [Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT](~/fundamentals/scope-tags.md).
9. Klicka på **Nästa** för att visa sidan **Tilldelningar**.
10. Välj grupptilldelningar för appen. Mer information finns i [Lägga till grupper för att organisera användare och enheter](~/fundamentals/groups-add.md). 
11. Visa sidan **Granska och skapa** genom att klicka på **Nästa**. Granska värdena och inställningarna som du har angett för appen.
12. När du är färdig klickar du på **Skapa** för att lägga till appen i Intune.

**Översiktsbladet** för appen som du har skapat visas i applistan.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer.

> [!IMPORTANT]
> Microsoft Store-appar kan endast tilldelas till grupper med tilldelningstypen **Tillgängligt för registrerade enheter** (användarna installerar appen från företagsportalappen eller webbplatsen för företagsportalen).

## <a name="next-steps"></a>Nästa steg
- [Tilldela appar till grupper](apps-deploy.md)
