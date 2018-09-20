---
title: Lägga till webbappar i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till webbappar i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7e974a17506be36c725dddfa21329269c8fcebc8
ms.sourcegitcommit: 572287c3bb0020b6b75e4e2ac27019c20c699159
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44340277"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Lägga till webbappar i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune stöder en mängd olika apptyper som bland annat webbappar. En webbapp är ett klientserverprogram. Servern tillhandahåller webbappen, som inkluderar användargränssnitt, innehåll och funktioner. Dessutom erbjuder moderna webbtjänstplattformar ofta säkerhet, belastningsutjämning och andra förmåner. En webbapp underhålls separat på webben. Du använder Microsoft Intune till att peka på den här apptypen. Du anger också vilka användargrupper som får åtkomst till den här appen. 

Innan du kan hantera och tilldela appar för dina användare, lägger du till appen i Intune. Intune skapar en genväg till webbappen på användarenhetens startskärm.

> [!Note]
> Webbappar stöds inte på Android-arbetsprofilenheter eller i macOS.

## <a name="add-a-web-app-to-intune"></a>Lägg till en webbapp i Intune
Om du vill lägga till en app i Intune som en genväg till en app på webben gör du så här:

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**.  
    Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** i **Intune**-fönstret.
4. I arbetsbelastningsfönstret **Klientappar** väljer du **Appar** under **Hantera**.
5. Välj **Lägg till** i fönsterrutan **Appar**.
6. Välj typen **Webblänk** i listrutan **Typ av app** i fönsterrutan **Lägg till app**.
7. Välj **Konfigurera**.
8. Lägg till följande information i fönstret **Appinformation**:
    - **Namn**: Ange namnet på appen så som det ska visas i företagsportalen. 
    
        > [!NOTE]
        > Om du ändrar namnet på appen via Intune i Azure Portal när du har distribuerat och installerat den kan du inte längre använda appen som mål i dina kommandon.
    
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
>
> För närvarande associeras distribution av Intune-webappar till iOS-enheter med hanteringsprofilen och kan inte tas bort manuellt. Du kan ändra distributionstypen till **Avinstallera** i Intune-portalen, så att webbappen kan tas bort automatiskt. Om du tar bort distributionen innan du ändrar tilldelningsavsikt för appen till **Avinstallera**, kommer webbappen dock att förbli permanent på enheten tills enheten har avregistrerats från Intune.

## <a name="next-steps"></a>Nästa steg

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md). 
