---
title: Skapa en appbaserad princip för villkorlig åtkomst för SharePoint Online
description: ''
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 05/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 5848fc18e0c288f8806f1fc93427d96c48317d64
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="set-up-app-based-conditional-access-ca-policies-for-sharepoint-online"></a>Konfigurera principer för appbaserad villkorlig åtkomst för SharePoint Online

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Det här avsnittet innehåller information om hur du ställer in en appbaserad villkorlig åtkomstprincip för SharePoint Online. Den appbaserade villkorliga åtkomsten hjälper administratörer att endast tillåta de mobilappar som Intunes appskyddsprinciper tillämpas på.

## <a name="to-create-the-app-based-ca-policy-for-sharepoint-online"></a>Skapa den appbaserade villkorliga åtkomstprincipen för SharePoint Online

1. Gå till [Azure-portalen](https://portal.azure.com) och logga in med dina autentiseringsuppgifter.

    > [!NOTE]
    > Om du inte har använt Azure-portalen tidigare, kan du läsa avsnittet [Azure-portal for appskyddsprinciper](azure-portal-for-microsoft-intune-mam-policies.md).

2. Välj **Fler tjänster** på den vänstra menyn och skriv sedan **Intune** i textrutefiltret.

3. Välj **Intune-appskydd** > **Hantering av mobilprogram i Intune** > **Alla inställningar**.

4. Välj panelen SharePoint Online på bladet Hantering av mobilprogram i Intune.

5. På bladet **Tillåtna appar** väljer du alternativet **Tillåt appar som stöder Intunes apprinciper** för att endast tillåta appar som stöds av Intunes appskyddsprinciper.

    > [!NOTE] 
    > När du väljer att endast tillåta appar som stöds av Intunes appskyddsprinciper, visar listan **enbart** de appar som stöds.

    ![Skärmbild av bladet med tillåtna appar som visar listan med appar](../media/mam-ca-spo-allowed-apps.png)

## <a name="to-assign-app-based-ca-policies-to-your-users"></a>Tilldela appbaserade villkorliga åtkomstprinciper till dina användare

1. Öppna bladet **Begränsade användargrupper** och välj sedan **Lägg till användargrupp**.

2. Välj en eller flera användargrupper som du vill tillämpa den här principen på.

    ![Skärmbild av bladet begränsade användargrupper med alternativet lägg till användargrupp markerat](../media/mam-ca-spo-restricted-groups.png)

    > [!IMPORTANT] 
    > Du kanske vill att vissa användare i den grupp du valde i föregående steg inte ska påverkas av den här principen. I sådana fall måste du lägga till dessa användare till listan över undantagna användare. 

3. På bladet **SharePoint Online** väljer du **Undantagna användargrupper** och sedan **Lägg till användargrupp** för att öppna listan med användargrupper.

4. Välj de grupper som du vill undanta från den här principen.  

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Ändra eller ta bort användargrupper från en befintlig appbaserad villkorlig åtkomstprincip

1. Öppna bladet **Begränsade användargrupper** och markera sedan den användargrupp du vill ta bort.
2. Klicka på ellipsen för att se borttagningsalternativen.
3. Välj **Ta bort** att ta bort användargruppen från listan.

> [!NOTE] 
> Du kan använda samma procedur för att ta bort en användargrupp från listan **Undantagna användargrupper**.

## <a name="next-steps"></a>Nästa steg

[Blockera appar som inte använder modern autentisering](block-apps-with-no-modern-authentication.md)

## <a name="see-also"></a>Se även

[Skydda appdata med appskyddsprinciper](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Konfigurera appbaserad villkorlig åtkomst för Exchange Online](mam-ca-for-exchange-online.md)
