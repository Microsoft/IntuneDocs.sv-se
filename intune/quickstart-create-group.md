---
title: Snabbstart – Skapa en grupp för att hantera användare
titlesuffix: Microsoft Intune
description: I den här snabbstarten använder du Microsoft Intune för att skapa en grupp baserad på befintliga användare.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a4468f2e6919349095d934790740afc8c347282
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581798"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Snabbstart: Skapa en grupp för att hantera användare

I den här snabbstarten använder du Intune för att skapa en grupp baserad på en befintlig användare. Grupper används för att hantera användare och styra de anställdas åtkomst till företagets resurser. Resurserna kan tillhöra ditt företags intranät eller kan vara externa resurser, t.ex. SharePoint-webbplatser, SaaS-appar eller webbappar.

Om du inte har en Intune-prenumeration [så registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

>[!NOTE]
>Intune tillhandahåller de i förväg skapade grupperna **Alla användare** och **Alla enheter** i konsolen med inbyggda optimeringar för att förenkla för dig.

## <a name="prerequisites"></a>Krav

- För att kunna slutföra den här snabbstarten måste du först [skapa en användare](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör. Du hittar Intune i Azure Portal genom att välja **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.

## <a name="create-a-group"></a>Skapa en grupp
1. När du har öppnat fönstret **Microsoft Intune** väljer du **Grupper** > **Ny grupp**.
2. Välj **Grupptyp** > **Säkerhet** i fönstret **Grupp**.
3. Ange ”Contoso-testare” som **Namn** och lägg till en **Beskrivning** för gruppen.
4. Ange **Tilldelad** som **medlemskapstyp**. 
5. Klicka på **Medlemmar** och välj **Medlemmar** till gruppen i den befintliga listan.

    ![Skärmbild som visar hur en grupp skapas i Microsoft Intune](./media/quickstart-use-groups-01.png)

6. Klicka på **Välj**.
7. Klicka på **Skapa**.

Om du lyckas skapa gruppen visas den i listan **Alla grupper**. 

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten har du använt Intune för att skapa en grupp baserad på en befintlig användare.

> [!div class="nextstepaction"]
> [Skapa en enhetsefterlevnadsprincip](quickstart-create-policy.md)
