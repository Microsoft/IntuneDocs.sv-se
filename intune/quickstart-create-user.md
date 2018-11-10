---
title: Snabbstart – Skapa en användare i Intune
description: Snabbstart – Skapa en användare i Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 10/30/2018
ms.author: erikje
ms.openlocfilehash: fb88f703048eaa122bb406d8adb1fc9face764c4
ms.sourcegitcommit: 9d08545727543b434dd270371fa50233470f2bce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410760"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Snabbstart: Skapa en användare och tilldela användaren en licens

I den här snabbstarten ska du skapa en användare som du sedan tilldelar en licens. När du använder Intune måste varje person som du vill ska ha åtkomst till företagets data ha ett användarkonto. Intune-administratörer kan sedan konfigurera sådana användare för att hantera åtkomstkontroll.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in i [Intune](https://aka.ms/intuneportal) som [global administratör eller Intune-tjänstadministratör](users-add.md#types-of-administrators). Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-a-user"></a>Skapar en användare

Användare måste ha ett användarkonto för att kunna registrera sig för hantering av Intune-enheter.

1. Välj **Användare** > **Alla användare** > **Ny användare** i Intune.
![Webbläsare](media/quickstart-create-user/create-user.png)
2. I rutan **Namn** anger du ett namn, t.ex. *Dewey Kellum*.
3. I rutan **Användarnamn** anger du ett användar-ID, t.ex. Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Om du inte har konfigurerat ditt kunddomännamn använder du det verifierade domännamnet som du använde för att skapa Intune-prenumerationen (eller den [kostnadsfria utvärderingsversionen](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Välj **Visa lösenord** och anteckna det automatiskt genererade lösenordet så att du kan logga in på en testenhet.
5. Välj **Skapa**.

## <a name="assign-a-license-to-the-user"></a>Tilldela användaren en licens

När du har skapat en användare måste du använda [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) för att tilldela användaren en Intune-licens. Användare kan inte registrera sina enheter i Intune förrän du har tilldelat dem en licens. 

1. Logga in på [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) med samma autentiseringsuppgifter du använde för att logga in på Intune.
2. Välj **Användare** > **Aktiva användare** > och välj den användare som du just har skapat.
3. Välj sedan **Redigera** bredvid **Produktlicenser**.
4. Välj en plats för användaren under **Plats**.
5. Klicka på **På** bredvid Intune-licensen (eller en annan licens som du har som omfattar Intune). [Produktnamnet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** som visas används som tjänstplan i Azure-hanteringen 

   > [!NOTE]
   > Den här inställningen använder en av dina licenser för den här användaren. Om du använder en utvärderingsmiljö skulle du senare omtilldela den här licensen till en verklig användare i en livemiljö.
6. Välj **Spara** > **Stäng**.

Den nya aktiva Intune-användaren visas nu som en användare med en **Intune**-licens.

## <a name="clean-up-resources"></a>Rensa resurser

Om du inte längre behöver den här användaren kan du ta bort användaren genom att navigera till [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) och välja **Användare** > **Aktiva användare** > *välja användaren i listan* > **Ta bort användare** > **Ta bort användare** > **Bekräfta ändringar** > **Stäng**.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten har du skapat en användare som du sedan tilldelat en licens. Du kan nu tilldela en grupp denna användare.

> [!div class="nextstepaction"]
> [Skapa en grupp](quickstart-create-group.md)
