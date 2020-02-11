---
title: Snabbstart – Skapa en användare i Intune
description: Snabbstart – Skapa en användare i Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6aa57b71e052e3fc8566fcdff8bdd9ef5d1c39e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754498"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-the-user-a-license"></a>Snabbstart: Skapa en användare i Intune och tilldela hen en licens

I den här snabbstarten skapar du en användare och tilldelar hen en Intune-licens. När du använder Intune måste varje person som du vill ge åtkomst till företagets data ha sitt eget användarkonto. Intune-administratörer kan konfigurera användare senare för att hantera åtkomstkontroll.

## <a name="prerequisites"></a>Krav

- En Microsoft Intune-prenumeration. [Registrera dig för ett kostnadsfri utvärderingskonto](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune-in-microsoft-endpoint-manager"></a>Logga in på Intune i Microsoft Endpoint Manager

Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) som global administratör eller [Intune-tjänstadministratör](users-add.md#types-of-administrators). Om du har skapat en prenumeration för Intune-utvärdering är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-a-user"></a>Skapa en användare

En användare måste ha ett användarkonto för att registrera sig för Intune-enhetshantering. Så här skapar du en ny användare:

1. Välj **Användare** > **Alla användare** > **Ny användare** i Microsoft Endpoint Manager:  ![Välj Ny användare i Microsoft Endpoint Manager](./media/quickstart-create-user/create-user.png)
2. Skriv ett namn, t.ex. *Dewey Kellum* i rutan **Namn**:  ![Lägg till användarinformation](./media/quickstart-create-user/create-user-02.png)
3. Ange ett användar-ID, t.ex. Dewey@contoso.onmicrosoft.com i rutan **Användarnamn**.

    > [!NOTE]
    > Om du inte har konfigurerat ditt kunddomännamn så använder du det verifierade domännamnet som du använde för att skapa Intune-prenumerationen (eller den [kostnadsfria utvärderingsversionen](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Välj **Visa lösenord** och var noga med att komma ihåg det automatiskt genererade lösenordet så att du kan logga in på en testenhet.
5. Välj **Skapa**.

## <a name="assign-a-license-to-the-user"></a>Tilldela användaren en licens

När du har skapat en användare måste du använda [Administrationscenter för Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) så att du kan tilldela användaren en Intune-licens. Om du inte tilldelar användaren en licens kommer den inte att kunna registrera sin enhet i Intune.

Så här tilldelar du en Intune-licens till en användare:

1. Logga in på [Administrationscenter för Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) med samma autentiseringsuppgifter du använde för att logga in på Intune.
2. Välj **Användare** > **Aktiva användare** och välj sedan den användare du just har skapat.
3. Välj fliken **Licenser och appar**.
4. Välj en plats för användaren under **Välj plats**, såvida den inte redan har angetts.
2. Markera kryssrutan **Intune** i avsnittet **Licenser**. Om en annan licens inkluderar Intune, så kan du välja den licensen. [Produktnamnet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) som visas används som tjänstplan i Azure-hanteringen.

    ![Välj plats och Intune-licens](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > Den här inställningen använder en av dina licenser för användaren. Om du använder en utvärderingsmiljö kommer du senare att omtilldela den här licensen till en verklig användare i en livemiljö.

6. Välj **Spara ändringar**.

Den nya aktiva Intune-användaren visas nu som en användare med en **Intune**-licens.

## <a name="clean-up-resources"></a>Rensa resurser

Om du inte behöver den här användaren längre, så kan du ta bort användaren genom att gå till [Administrationscenter för Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) och välja **Användare** > *användaren* > *ikonen Ta bort användare* > **Ta bort användare** > **Stäng**.

   ![Välj ikonen Ta bort](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten har du skapat en användare som du sedan tilldelat en Intune-licens. Mer information om hur du lägger till användare i Intune finns i [Lägga till användare och ge administrativ behörighet till Intune](users-add.md).

Om du vill fortsätta den här serien med Intune-snabbstarter, så gå till nästa snabbstart:

> [!div class="nextstepaction"]
> [Snabbstart: Skapa en grupp för att hantera användare](../quickstart-create-group.md)
