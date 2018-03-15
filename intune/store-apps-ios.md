---
title: "Så här lägger du till iOS Store-appar i Microsoft Intune"
titlesuffix: 
description: "Läs mer om att lägga till iOS Store-appar i Microsoft Intune."
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b5315d683abfc38a7f42d2f322cc77c625270e3c
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Så här lägger du till iOS Store-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Informationen i den här artikeln visar hur du lägger till iOS Store-appar i Microsoft Intune. iOS Store-appar är appar som Intune installerar på en användarenhet. Användaren ingår i ditt företags personal. iOS Store-appar uppdateras automatiskt. 

>[!NOTE]
>Användare av iOS-enheter kan ta bort några av de inbyggda iOS-apparna som Aktier och Kartor, men du kan inte använda Intune för att distribuera dessa appar igen. Om slutanvändarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.

## <a name="before-you-start"></a>Innan du börjar

Du kan endast tilldela appar med den här metoden om de är gratis i App Store. Om du vill tilldela betalappar med hjälp av Intune bör du använda [volyminköpsprogrammet för iOS](vpp-apps-ios.md).

>[!NOTE]
>Webbläsarna Chrome och Microsoft Edge rekommenderas när du arbetar med Microsoft Intune.

## <a name="step-1---search-for-the-app-in-the-store"></a>Steg 1 – Sök efter appen i butiken

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Mobilappar** på **Intune**-bladet.
4. Välj **Appar** under avsnittet **Hantera** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** till höger i fönstret **Appar**.
6. I listan **Apptyp** väljer du **iOS** under tillgängliga typer i **Store-app**.
6. Välj **Search the App Store** (Sök i App Store).
7. Välj nationella inställningar för App Store på bladet **Search the App Store** (Sök i App Store).
8. Ange namn (eller en del av namnet) i sökrutan. Intune söker i butiken och returnerar en lista över relevanta resultat.
9. Välj önskad app i listan och klicka sedan på **Välj**.

## <a name="step-2---configure-app-information"></a>Steg 2 – Konfigurera information om appen

1. På bladet **Lägg till app** väljer du **Appinformation** för att konfigurera appen.
2. Lägg till appinformationen på bladet **Appinformation**. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
- **Namn** – Ange namnet på appen som ska visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
- **Beskrivning** – Ange en beskrivning av appen som ska visas för användare på företagsportalen.
- **Utgivare** – Ange namnet på appens utgivare.
- **Webbadress till appbutik** – Ange App Store-URL:en för den app som du vill skapa.
- **Lägsta operativsystemversion** – Välj den minsta operativsystemversion som appen kan installeras på. Appen installeras inte på en enhet med ett äldre operativsystem.
- **Tillämplig enhetstyp** – Från listan väljer du de enheter som används av appen.
- **Kategori** (valfritt). Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Kategorier gör det enklare för användarna att hitta appen när de söker i företagsportalen.
- **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
- **Webbadress till information** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
- **Sekretesswebbadress** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen (valfritt). Webbadressen visas för användarna på företagsportalen.
- **Utvecklare (valfritt)** – Ange apputvecklarens namn. Det här fältet visas bara för en administratör och kommer inte att visas för slutanvändarna.
- **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.  Det här fältet visas bara för en administratör och kommer inte att visas för slutanvändarna.
- **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen. Det här fältet visas bara för en administratör och kommer inte att visas för slutanvändarna.
- **Logotyp** – Ladda upp en ikon som är associerad med appen. Ikonen visas tillsammans med appen när användarna söker på företagsportalen.
3. När du är klar klickar du på **OK** på bladet **Lägg till information**.
4. Klicka på **Lägg till** på bladet **Lägg till app**. 

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. 

## <a name="next-steps"></a>Nästa steg

- [Så här tilldelar du appar till grupper](apps-deploy.md)
