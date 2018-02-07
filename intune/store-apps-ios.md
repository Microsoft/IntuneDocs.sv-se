---
title: "Så här lägger du till iOS Store-appar i Intune | Microsoft Docs"
titlesuffix: Azure portal
description: "Läs mer om att lägga till iOS-butiksappar i Intune.”"
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e013b5c995274365978ee0c2ba2f45bfeef54baa
ms.sourcegitcommit: b982f9d50da4f958fb0c48c56ba46c8ef71500c4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Så här lägger du till iOS Store-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Informationen i det här avsnittet beskriver hur du lägger till iOS-appar från App Store i Intune.

>[!NOTE]
>Användare av iOS-enheter kan ta bort några av de inbyggda iOS-apparna som Aktier och Kartor, men du kan inte använda Intune för att distribuera dessa appar igen. Om slutanvändarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.

## <a name="before-you-start"></a>Innan du börjar

Du kan endast tilldela appar med den här metoden om de är gratis i App Store. Om du vill tilldela betalappar med hjälp av Intune bör du använda [volyminköpsprogrammet för iOS](vpp-apps-ios.md).

>[!NOTE]
>Webbläsarna Chrome och Microsoft Edge rekommenderas när du arbetar med Microsoft Intune.

## <a name="step-1---search-for-the-app-in-the-store"></a>Steg 1 – Sök efter appen i butiken

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
4. Välj **Hantera** > Appar i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. Välj **Sök i App Store** på bladet **Lägg till app**.
7. På bladet **Apple App Store** väljer du nationella inställningar.
8. Ange namn (eller en del av namnet) i sökrutan. Intune söker i butiken och returnerar en lista över relevanta resultat.
9. Välj önskad app i listan och klicka sedan på **OK**.

## <a name="step-2---configure-app-information"></a>Steg 2 – Konfigurera information om appen

1. Välj **Appinformation** på bladet **Lägg till app**.
2. Konfigurera följande appinformation på bladet **Redigera app**. När du är klar klickar du på **Lägg till**. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
- **Namn** – Ange namnet på appen som ska visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
- **Beskrivning** – Ange en beskrivning av appen som ska visas för användare på företagsportalen.
- **Utgivare** – Ange namnet på appens utgivare.
- **Webbadress till appbutik** – Ange App Store-URL:en för den app som du vill skapa.
- **Land/region för butik** – Välj land.
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
3. När du är klar väljer du **OK** på bladet **Lägg till app**.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).
