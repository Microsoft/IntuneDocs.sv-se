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
ms.openlocfilehash: 2b52265bb9b3df800c0e13450a2154e46098a933
ms.sourcegitcommit: 9d08545727543b434dd270371fa50233470f2bce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410828"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Snabbstart: Skapa en grupp för att hantera användare

I den här snabbstarten använder du Intune för att skapa en grupp baserad på en befintlig användare. Grupper används för att hantera användare och styra de anställdas åtkomst till företagets resurser. Resurserna kan tillhöra ditt företags intranät eller kan vara externa resurser, t.ex. SharePoint-webbplatser, SaaS-appar eller webbappar.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

>[!NOTE]
>Intune tillhandahåller de i förväg skapade grupperna **Alla användare** och **Alla enheter** i konsolen med inbyggda optimeringar för att förenkla för dig.

## <a name="prerequisites"></a>Krav

- För att kunna slutföra den här snabbstarten måste du först [skapa en användare](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in i [Intune](https://aka.ms/intuneportal) som [global administratör eller Intune-tjänstadministratör](users-add.md#types-of-administrators). Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-a-group"></a>Skapa en grupp

Du ska skapa en grupp som ska användas senare i den här snabbstarten.

1. När du har öppnat fönstret **Microsoft Intune** väljer du **Grupper** > **Ny grupp**.
2. Välj **Säkerhet** i listrutan **Grupptyp**.
3. Ange ”Contoso-testare” som **Namn** och lägg till en **Beskrivning** för gruppen.
4. Ange **Typ av medlemskap** till **Tilldelad**. 
5. Klicka på **Medlemmar** och välj en eller flera medlemmar för gruppen från den befintliga listan.

    ![Skärmbild som visar hur en grupp skapas i Microsoft Intune](./media/quickstart-use-groups-01.png)

6. Klicka på **Välj** > **Skapa**.

När du har skapat gruppen visas den i listan **Alla grupper**. 

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten har du använt Intune för att skapa en grupp baserad på en befintlig användare.

> [!div class="nextstepaction"]
> [Skapa en enhetsefterlevnadsprincip](quickstart-create-policy.md)
