---
title: "Lägga till webbappar i Microsoft Intune"
titleSuffix: 
description: "Läs mer om att lägga till webbappar i Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ecb44f8b98501f6c82f91994cd8a06b8177208d7
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Lägga till webbappar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune stöder en mängd olika apptyper som bland annat Web Apps. En webbapp är ett klientserverprogram. Servern tillhandahåller webbappen, som inkluderar användargränssnitt, innehåll och funktioner. Dessutom erbjuder moderna webbtjänstplattformar dessutom vanligen säkerhet, belastningsutjämning och andra förmåner. En webbapp underhålls separat på webben. Du använder Microsoft Intune till att peka på den här apptypen. Du tilldelar också vilka användargrupper som ska kunna få åtkomst till den här appen. 

Innan du kan hantera och tilldela appar för dina användare, lägger du till appen i Intune. Intune skapar en genväg till webbappen på användarenhetens startskärm.

> [!Note]
> Webbappar stöds inte på Android for Work-enheter eller i macOS.

Utför följande steg om du vill lägga till en app i Intune som en genväg till en app på webben:

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Microsoft Intune** väljer du **Mobilappar**.
4. I fönstret **Mobilappar** väljer du **Appar**.
5. Välj **Lägg till** ovanför listan över appar. Fönstret **Lägg till app** visas.
6. I fönstret **Lägg till app** väljer du typ av **Webblänk** i listrutan **Apptyp**.
7. Välj alternativet **Konfigurera** för att visa fönstret **Appinformation**.
8. Lägg till följande information i fönstret **Appinformation**:
    - **Namn** – Ange namnet på appen så som det ska visas i företagsportalen.
    - **Beskrivning** – Ange en beskrivning för appen. Detta visas för slutanvändare i företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **App-URL** – Ange webbadressen till webbplatsen där den app som du vill tilldela finns.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det här avsnittet gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Kräv en hanterad webbläsare för att öppna den här länken** – När du tilldelar en länk till en webbplats eller en webbapp till användare kan de öppna den i Intune Managed Browser. Den här webbläsaren måste installeras på enheterna.
    - **Logotyp** – Ladda upp en logotyp som är associerad med appen. Den här logotypen visas med appen när användare söker på företagsportalen.
9. När du är klar väljer du **OK** i fönstret **Lägg till information**.
10. I fönstret **Lägg till app** väljer du sedan **Lägg till**.

> [!Note]
> Användarna måste lägga till Intune-widgeten på startsidan för att kunna se vilka webbappar som har tilldelats till Android-enheter.

## <a name="next-steps"></a>Nästa steg

- Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).