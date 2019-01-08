---
title: Lägg till iOS Store-appar i Microsoft Intune
titlesuffix: ''
description: Läs mer om att lägga till iOS Store-appar i Microsoft Intune. Du kan tilldela appar med den här metoden om de är gratis i App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5f1423b0f2f216f65026d2b1a7bf52dda39c9f88
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642514"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Lägg till iOS Store-appar i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Informationen i den här artikeln visar hur du lägger till iOS Store-appar i Microsoft Intune. iOS Store-appar är appar som Intune installerar på dina användares enheter. En användare är en del av ditt företags arbetsstyrka. iOS Store-appar uppdateras automatiskt.

>[!NOTE]
>Även om användare av iOS-enheter kan ta bort några av de inbyggda iOS-apparna som Aktier och Kartor, kan du inte använda Intune för att distribuera dessa appar igen. Om dina användarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.

## <a name="before-you-start"></a>Innan du börjar

Du kan endast tilldela appar med den här metoden om de är gratis i App Store. Om du vill tilldela betalappar med hjälp av Intune bör du använda [volyminköpsprogrammet för iOS](vpp-apps-ios.md).

>[!NOTE]
>När du arbetar med Microsoft Intune, rekommenderar vi att du använder antingen webbläsaren Google Chrome eller Microsoft Edge.

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**.  
    Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** i **Intune**-fönstret.
4. I arbetsbelastningsfönstret **Klientappar** väljer du **Appar** under **Hantera**.
5. Välj **Lägg till** i fönsterrutan **Appar**.
6. I listan **Apptyp** under den **Store-app**, välj **iOS**.
7. Välj **Sök i App Store**.
8. Välj nationella inställningar för App Store i rutan **Sök i App Store**.
9. Ange namnet (eller en del av namnet) i fönstret **Sök**.  
    Intune söker i butiken och returnerar en lista över relevanta resultat.
10. I resultatlistan väljer du den app du önskar och klickar sedan på **Välj**.
11. I fönstret **Lägg till app** väljer du **Appinformation** för att konfigurera appen.
12. Lägg till appinformationen i fönstret **Appinformation**. Beroende på vilken app du har valt kan det hända att några av värdena i det här fönstret har fyllts i automatiskt:
    - **Namn**: Ange namnet på appen så som det ska visas i företagsportalen. Se till att alla appnamn du använder är unika. Om ett appnamn dupliceras visas endast ett namn för användare i företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Webbadress till appbutik**: Skriv App Stores URL för den app som du vill skapa.
    - **Lägsta operativsystemsversion**: Välj den tidigaste operativsystemsversion i listan som appen kan installeras i. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Tillämplig enhetstyp**: I listan väljer du de enheter som används av appen.
    - **Kategori**: Du kan även välja en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa den som en aktuell app i företagsportalen**: Välj det här alternativet för att tydligt visa appsviten på företagsportalens huvudsida när användare söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn. Det här fältet visas bara för administratörer och är inte synligt för användarna.
    - **Ägare**: Alternativt kan du ange ett namn på appens ägare, t.ex. *Personalavdelningen*. Det här fältet visas bara för administratörer och är inte synligt för användarna.
    - **Kommentarer**: Alternativt kanske du vill ange kommentarer till appen. Det här fältet visas bara för en administratör och kommer inte att visas för slutanvändarna.
    - **Logotyp**: Om du vill kan du ladda upp en ikon som ska kopplas till appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
13. Välj **OK**.
14. Välj **Lägg till**.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer.

## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md)
