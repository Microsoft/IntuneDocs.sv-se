---
title: Snabbstart – Skapa en grupp för att hantera användare
titleSuffix: Microsoft Intune
description: I den här snabbstarten använder du Microsoft Intune för att skapa en grupp baserad på befintliga användare.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/25/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a9cf1b610830928a753be176de2643fa1826bd0
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050312"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Snabbstart: Skapa en grupp för att hantera användare

I den här snabbstarten använder du Intune för att skapa en grupp baserad på en befintlig användare. Grupper används för att hantera användare och styra de anställdas åtkomst till företagets resurser. Resurserna kan tillhöra ditt företags intranät eller kan vara externa resurser, t.ex. SharePoint-webbplatser, SaaS-appar eller webbappar.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

>[!NOTE]
>Intune tillhandahåller de i förväg skapade grupperna **Alla användare** och **Alla enheter** i konsolen med inbyggda optimeringar för att förenkla för dig.

## <a name="prerequisites"></a>Krav

- För att kunna slutföra den här snabbstarten måste du först [skapa en användare](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in i [Intune-portalen](https://aka.ms/intuneportal) som [global administratör eller Intune-tjänstadministratör](users-add.md#types-of-administrators). Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-a-group"></a>Skapa en grupp

Du ska skapa en grupp som ska användas senare i den här snabbstarten. Så här skapar du en grupp:

1. När du har öppnat fönstret **Microsoft Intune** väljer du **Grupper** > **Ny grupp**.
2. Välj **Säkerhet** i listrutan **Grupptyp**.
3. I fältet **Gruppnamn** anger du namnet för den nya gruppen (exempelvis **Contoso-testare**).
4. Fyll i en **Beskrivning** av gruppen
5. Ange **Typ av medlemskap** till **Tilldelad**. 
6. Klicka på **Medlemmar** och välj en eller flera medlemmar för gruppen från listan.

    ![Skärmbild som visar hur en grupp skapas i Microsoft Intune](./media/quickstart-use-groups-01.png)

7. Klicka på **Välj** > **Skapa**.

När du har skapat gruppen visas den i listan **Alla grupper**. 

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten har du använt Intune för att skapa en grupp baserad på en befintlig användare. Mer information om att lägga till grupper i Intune finns i [Lägga till grupper för att organisera användare och enheter](groups-add.md).

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Konfigurera automatisk registrering för Windows 10-enheter](quickstart-setup-auto-enrollment.md)
