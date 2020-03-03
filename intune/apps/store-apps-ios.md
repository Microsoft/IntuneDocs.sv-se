---
title: Lägg till iOS Store-appar i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till iOS Store-appar i Microsoft Intune. Du kan tilldela appar med den här metoden om de är gratis i App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f2baf60fed2c6010e5ae0784cda166ac4fabfd57
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511743"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Lägg till iOS Store-appar i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Informationen i den här artikeln visar hur du lägger till iOS Store-appar i Microsoft Intune. iOS Store-appar är appar som Intune installerar på dina användares enheter. En användare är en del av ditt företags arbetsstyrka. iOS Store-appar uppdateras automatiskt.

>[!NOTE]
>Även om användare av iOS/iPadOS-enheter kan ta bort några av de inbyggda iOS/iPadOS-apparna som Aktier och Kartor, kan du inte använda Intune för att distribuera dessa appar igen. Om dina användarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.

## <a name="before-you-start"></a>Innan du börjar

Du kan endast tilldela appar med den här metoden om de är gratis i App Store. Om du vill tilldela betalappar med hjälp av Intune bör du använda [volyminköpsprogrammet för iOS/iPadOS](vpp-apps-ios.md).

>[!NOTE]
>När du arbetar med Microsoft Intune, rekommenderar vi att du använder antingen webbläsaren Google Chrome eller Microsoft Edge.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj **iOS Store-app** i rutan **Välj apptyp** bland de tillgängliga typerna av **Store-appar**.
4. Klicka på **Välj**.<br>
   Stegen **Lägg till app** visas.
5. Välj **Sök i App Store**.
6. Välj nationella/regionala inställningar för App Store i rutan **Sök i App Store**.
7. Ange namnet (eller en del av namnet) i fönstret **Sök**.  
    Intune söker i butiken och returnerar en lista över relevanta resultat.
8. I resultatlistan väljer du den app du önskar och klickar sedan på **Välj**.<br>

   Sidan **Appinformation** visas i fönstret **Lägg till app**. När det är möjligt läggs appinformation till utifrån den app som du valde i butiken.

9. Lägg till information om appen i fönstret **Appinformation**. Beroende på vilken app du har valt kan det hända att några av värdena i det här fönstret har fyllts i automatiskt:
    - **Namn**: Ange namnet på appen så som den ska visas i företagsportalen. Se till att alla appnamn du använder är unika. Om ett appnamn dupliceras visas endast ett namn för användare i företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Webbadress till appbutik**: Skriv App Stores URL för den app som du vill skapa.
    - **Lägsta operativsystemversion**: Välj den tidigaste operativsystemsversion i listan som appen kan installeras i. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Tillämplig enhetstyp**: I listan väljer du de enheter som används av appen.
    - **Kategori**: Du kan även välja en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Välj det här alternativet för att tydligt visa appsviten på företagsportalens huvudsida när användarna söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn. Det här fältet visas bara för administratörer och är inte synligt för användarna.
    - **Ägare**: Alternativt kan du ange ett namn på appens ägare, t.ex. *Personalavdelningen*. Det här fältet visas bara för administratörer och är inte synligt för användarna.
    - **Kommentarer**: Alternativt kanske du vill ange kommentarer till appen. Det här fältet visas bara för en administratör och kommer inte att visas för slutanvändarna.
    - **Logotyp**: Om du vill kan du ladda upp en ikon som ska kopplas till appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
10. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.
11. Klicka på **Välj omfångstaggar** om du vill lägga till omfångstaggar för appen. Mer information finns i [Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT](~/fundamentals/scope-tags.md).
12. Klicka på **Nästa** för att visa sidan **Tilldelningar**.
13. Välj grupptilldelningar för appen. Mer information finns i [Lägga till grupper för att organisera användare och enheter](~/fundamentals/groups-add.md). 
14. Visa sidan **Granska och skapa** genom att klicka på **Nästa**. Granska värdena och inställningarna som du har angett för appen.
15. När du är färdig klickar du på **Skapa** för att lägga till appen i Intune.

**Översiktsbladet** för appen som du har skapat visas i applistan.

## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md)
