---
title: Lägga till webbappar i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till webbappar i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0d62341e35bf851bb429b15a582183bec62a9d4a
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="add-web-apps-to-microsoft-intune"></a>Lägga till webbappar i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune stöder en mängd olika apptyper som bland annat webbappar. En webbapp är ett klientserverprogram. Servern tillhandahåller webbappen, som inkluderar användargränssnitt, innehåll och funktioner. Dessutom erbjuder moderna webbtjänstplattformar ofta säkerhet, belastningsutjämning och andra förmåner. En webbapp underhålls separat på webben. Du använder Microsoft Intune till att peka på den här apptypen. Du anger också vilka användargrupper som får åtkomst till den här appen. 

Innan du kan hantera och tilldela appar för dina användare, lägger du till appen i Intune. Intune skapar en genväg till webbappen på användarenhetens startskärm.

> [!Note]
> Webbappar stöds inte på Android for Work-enheter eller i macOS.

## <a name="add-a-web-app-to-intune"></a>Lägg till en webbapp i Intune
Om du vill lägga till en app i Intune som en genväg till en app på webben gör du så här:

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**.  
    Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enheter** i **Mobilappar**-fönstret.
4. I arbetsbelastningsfönstret **Mobilappar** under **Hantera**, väljer du **Appar**.
5. Välj **Lägg till** i fönsterrutan **Appar**.
6. Välj typen **Webblänk** i listrutan **Typ av app** i fönsterrutan **Lägg till app**.
7. Välj **Konfigurera**.
8. Lägg till följande information i fönstret **Appinformation**:
    - **Namn**: Ange namnet på appen så som det ska visas i företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **App-URL**: Ange webbadressen till den webbplats där den app som du vill tilldela finns.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen**: Välj det här alternativet för att visa appsviten på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Kräv en hanterad webbläsare för att öppna den här länken**: Välj det här alternativet om du vill tilldela användarna en länk till en webbplats eller en webbapp som du kan de öppna i Intune Managed Browser. Den här webbläsaren måste installeras på enheterna.
    - **Logotyp**: Ladda upp en ikon som ska associeras med appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
9. Välj **OK**.
10. I fönstret **Lägg till app** väljer du **Lägg till**.

> [!Note]
> Användarna måste lägga till Intune-widgeten på startsidan för att kunna se vilka webbappar som har tilldelats till Android-enheter.

## <a name="next-steps"></a>Nästa steg

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md). 
