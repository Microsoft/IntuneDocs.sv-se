---
title: "Så här lägger du till iOS Store-appar i Intune"
titlesuffix: Azure portal
description: "Läs mer om att lägga till iOS-butiksappar i Intune.”"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 53ff149b28a2f75a3b30c59fa5f30edcf4879fae
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Så här lägger du till iOS Store-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Informationen i det här avsnittet beskriver hur du lägger till iOS-appar från App Store i Intune.

>[!NOTE]
>Användare av iOS-enheter kan ta bort några av de inbyggda iOS-apparna som Aktier och Kartor, men du kan inte använda Intune för att distribuera dessa appar igen. Om slutanvändarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.

## <a name="before-you-start"></a>Innan du börjar

Du kan endast tilldela appar med den här metoden om de är gratis i App Store. Om du vill tilldela betalappar med hjälp av Intune bör du använda [volyminköpsprogrammet för iOS](vpp-apps-ios.md).


## <a name="step-1---search-for-the-app-in-the-store"></a>Steg 1 – Sök efter appen i butiken

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
4. Välj **Hantera** > Appar i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. Välj **Sök i App Store** på bladet **Lägg till app**.
7. På bladet **Apple App Store** anger du namnet (eller en del av namnet) i sökrutan. Intune söker i butiken och returnerar en lista över relevanta resultat.
8. Välj önskad app i listan och klicka sedan på **OK**.

## <a name="step-2---configure-app-information"></a>Steg 2 – Konfigurera information om appen

1. Välj **Appinformation** på bladet **Lägg till app**.
2. Konfigurera följande information på bladet **Redigera app**. När du är klar klickar du på **Lägg till**. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
- **Appnamn** – Ange namnet på appen så som det ska visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Appbeskrivning** – Ange en beskrivning för appen. Detta visas för användare i företagsportalen.
- **Utgivare** – Ange namnet på appens utgivare.
- **App Store-URL** – Ange App Store-URL:en för den app som du vill skapa.
- **Minsta operativsystem** – Välj den minsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
- **Kategori** (valfritt). Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
- **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
- **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
- **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
- **Utvecklare (valfritt)** – Ange apputvecklarens namn.
- **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
- **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
- **Ladda upp ikon** – Överför en ikon som ska kopplas till appen. Den här ikonen visas med appen när användare söker i företagsportalen.
3. När du är klar väljer du **Spara** på bladet **Lägg till app**.

Den app som du har skapat visas i listan över appar där du kan välja att tilldela den till olika grupper. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).
