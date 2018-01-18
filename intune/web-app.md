---
title: "Så här lägger du till webbappar till Intune"
titleSuffix: Azure portal
description: "Lär dig hur du lägger till webbappar i Intune.”"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6da1441b16a43b5e22bedd9e87970f3388b11b9e
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/30/2017
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Lägga till webbappar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Innan du kan hantera och tilldela appar för dina användare, lägger du till appen i Intune. Intune stöder en mängd olika apptyper som bland annat Web Apps.

> [!Note]
> Webb Apps stöds inte på Android för arbetsenheter.

Utför följande steg om du vill lägga till en app i Intune som en genväg till en app på webben:

1. Logga in på Azure-portalen.
2. Med hjälp av **Fler resurser**, söker du efter och väljer **Intune**.
3. På bladet **Microsoft Intune** väljer du **mobilappar**.
4. På bladet **Mobilappar** väljer du **Appar**.
5. Välj **Lägg till** ovanför listan över appar. Bladet **Lägg till app** visas.
6. På bladet **Lägg till app** väljer du typ av **Web App** från listrutan **Typ av app**.
7. Välj alternativet **Konfigurera** för att visa bladet **Appinformation**.
8. Lägg till följande information på bladet **Appinformation**:
    - **Namn** – Ange namnet på appen så som det ska visas i företagsportalen.
    - **Beskrivning** – Ange en beskrivning för appen. Detta visas för slutanvändare i företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **App-URL** – Ange webbadressen till webbplatsen där den app som du vill tilldela finns.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det här avsnittet gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Kräv en hanterad webbläsare för att öppna den här länken** – När du tilldelar en länk till en webbplats eller en webbapp till användare kan de öppna den i Intune Managed Browser. Den här webbläsaren måste installeras på enheterna.
    - **Logotyp** – Ladda upp en logotyp som är associerad med appen. Den här logotypen visas med appen när användare söker på företagsportalen.
9. När du är klar väljer du **OK** på bladet **Lägg till information**.
10. Från bladet **Lägg till app** väljer du**Lägg till**.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).