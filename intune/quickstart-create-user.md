---
title: Snabbstart – Skapa en användare i Intune
description: Snabbstart – Skapa en användare i Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/25/2019
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: b49595493b5db3e5735e0a4717c27e91f058b8d8
ms.sourcegitcommit: d38ca1bf44e17211097aea481e00b6c1e87effae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514271"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>Snabbstart: Skapa en användare i Intune och tilldela dem en licens

I den här snabbstarten får du skapa en användare och tilldela dem en Intune. När du använder Intune måste varje person som du vill ge åtkomst till företagets data ha sitt eget användarkonto. Intune-administratörer kan konfigurera användare senare för att hantera åtkomstkontroll.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in på [Intune](https://aka.ms/intuneportal) som [global administratör eller Intune-tjänstadministratör](users-add.md#types-of-administrators). Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-a-user"></a>Skapa en användare

Användare måste ha ett användarkonto för att registrera sig för Intune-enhetshantering. Så här skapar du en ny användare:

1. Välj **Användare** > **Alla användare** > **Ny användare** i Intune.
![Webbläsare](media/quickstart-create-user/create-user.png)
2. I rutan **Namn** anger du ett namn, t.ex. *Dewey Kellum*.
3. I rutan **Användarnamn** anger du ett användar-ID, t.ex. Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Om du inte har konfigurerat ditt kunddomännamn så använder du det verifierade domännamnet som du använde för att skapa Intune-prenumerationen (eller den [kostnadsfria utvärderingsversionen](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Välj **Visa lösenord** och anteckna det automatiskt genererade lösenordet så att du kan logga in på en testenhet.
5. Välj **Skapa**.

## <a name="assign-a-license-to-the-user"></a>Tilldela användaren en licens

När du har skapat en användare måste du använda [Administrationscenter för Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) för att tilldela en Intune-licens till dem. Om du inte tilldelar användaren en licens, kommer de inte att kunna registrera sin enhet i Intune. 

Så här tilldelar du en Intune-licens till en användare:

1. Logga in på [Administrationscenter för Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) med samma autentiseringsuppgifter du använde för att logga in på Intune.
2. Välj **Användare** > **Aktiva användare** > och välj den användare som du just skapade.
3. Välj sedan **Redigera** bredvid **Produktlicenser**.
4. Välj en plats för användaren under **Plats**.
5. Klicka på **På** bredvid Intune-licensen (eller en annan licens som du har som omfattar Intune). [Produktnamnet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** som visas används som tjänstplan i Azure-hanteringen 

   > [!NOTE]
   > Den här inställningen använder en av dina licenser för den här användaren. Om du använder en utvärderingsmiljö skulle du senare omtilldela den här licensen till en verklig användare i en livemiljö.
6. Välj **Spara** > **Stäng**.

Den nya aktiva Intune-användaren visas nu som en användare med en **Intune**-licens.

## <a name="clean-up-resources"></a>Rensa resurser

Om du inte längre behöver den här användaren kan du ta bort användaren genom att navigera till [Administrationscenter för Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) och välja **Användare** > **Aktiva användare** > *välja användaren i listan* > **Ta bort användare** > **Ta bort användare** > **Bekräfta ändringar** > **Stäng**.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten har du skapat en användare som du sedan tilldelat en Intune-licens. Mer information om hur du lägger till användare i Intune finns i [Lägga till användare och ge administrativ behörighet till Intune](users-add.md).

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Skapa en grupp för att hantera användare](quickstart-create-group.md)
