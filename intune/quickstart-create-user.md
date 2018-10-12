---
title: Snabbstart – Skapa en användare i Intune
description: Snabbstart – Skapa en användare i Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581810"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Snabbstart: Skapa en användare och tilldela användaren en licens

I den här snabbstarten får du skapa en användare som du sedan tilldelar en licens. När du använder Intune måste varje person som du vill ska ha åtkomst till företagets data ha ett användarkonto. Intune-administratörer kan sedan konfigurera sådana användare för att hantera åtkomstkontroll.

Om du inte har en Intune-prenumeration [så registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör.

## <a name="create-a-user"></a>Skapar en användare

Användare måste ha ett användarkonto för att kunna registrera sig för hantering av Intune-enheter.

1. Välj **Användare** > **Alla användare** > **Ny användare** i Intune.
![Webbläsare](media/quickstart-create-user/create-user.png)
2. Skriv *Dewey Kellum* i rutan **Namn**.
3. Skriv *Dewey@contoso.onmicrosoft.com* i rutan **Användarnamn**.
4. Välj **Grupper** > **Alla** > **Välj**.
5. Välj **Visa lösenord** och anteckna det automatiskt genererade lösenordet så att du kan logga in på en testenhet.
6. Välj **Skapa**.

## <a name="assign-a-license-to-the-user"></a>Tilldela användaren en licens

När du har skapat en användare måste du använda [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) för att tilldela användaren en Intune-licens. Användare kan inte registrera sina enheter i Intune förrän du har tilldelat dem en licens. 

1. Logga in på [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) med samma autentiseringsuppgifter du använde för att logga in på Intune.
2. Välj **Användare** > **Aktiva användare** > och välj den användare som du just har skapat.
3. Välj en plats för användaren under **Plats**.
3. Välj **Produktlicenser** och välj **På** för **Enterprise Mobility + Security E3** (eller någon annan licens som du har som inkluderar Intune).
   > [!NOTE]
   > En av de tillgängliga licenserna används nu för den här användaren. Om du använder livemiljön kan du inaktivera användningen av den här licens om du senare vill tilldela den till riktig användare.
5. Välj **Spara**.

## <a name="clean-up-resources"></a>Rensa resurser

Om du inte längre behöver den här användaren kan du ta bort den genom att välja **Användare** > **Alla användare** > välja användaren i listan > **Ta bort användare** > **Ja**.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten har du skapat en användare som du sedan tilldelat en licens. Du kan nu tilldela en grupp denna användare.

> [!div class="nextstepaction"]
> [Skapa en grupp](quickstart-create-group.md)
