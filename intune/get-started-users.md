---
title: Komma igång med att hantera användare
titlesuffix: Microsoft Intune
description: Lägg till en användare i Intune och tilldela dem en licens så att de kan få åtkomst till företagsresurser på mobila enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fc5d2a6f17bdac8711348c136ee390a400fc21bd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182507"
---
# <a name="get-started-managing-users"></a>Komma igång med att hantera användare

Tänk på alla olika personer i din organisation. Alla som använder företagsinformation behöver en användare som hanterar åtkomst till informationen i Intune.

## <a name="how-do-i-create-a-user"></a>Hur skapar jag en användare?

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. När du har öppnat fönstret **Microsoft Intune** väljer du **Användare**. På sidan **Alla användare** väljer du **+ Ny användare**.
4. Ange information om användaren, t.ex. **namn** och **användarnamn**. Delen av användarnamnet som är domännamnet måste vara något av följande domän:
    - Det initiala standarddomännamnet ”contoso.onmicrosoft.com” eller
    - en verifierad, ofedererad domän som till exempel ”contoso.com”
5. Välj [en grupp](get-started-groups.md) du vill lägga till användaren i under **Grupper**.
6. Spara det automatiskt genererade användarlösenordet så att du kan använda det till att logga in på en testenhet. Du måste ge det här lösenordet till användare så att de kan ändra det till ett normalt lösenord som de kan komma ihåg.
7. Välj **Skapa** i fönstret **Användare**.

## <a name="assigning-licenses-to-users"></a>Tilldela licenser till användare

När du har skapat en användare måste du använda [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) för att tilldela den användaren en Intune-licens. Användare kan inte registrera sina enheter för hantering innan du har tilldelat dem en licens.

1. Logga in på [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) med samma autentiseringsuppgifter du använde för att logga in på Intune.
2. Välj **Användare** > **Aktiva användare** och välj sedan den användare du skapade tidigare.
3. Du kan behöva vänta en stund tills all information om användaren har lästs in. När informationen har lästs in väljer du **Redigera** för användarens **produktlicenser**.
4. Tilldela användaren en **plats** och växla sedan Intune till **På**.

   > [!NOTE]
   > En av de tillgängliga licenserna används nu för den här användaren. Om du använder livemiljön kan du inaktivera användningen av den här licens om du senare vill tilldela den till riktig användare.

5. Välj **Spara**.

## <a name="next-steps"></a>Nästa steg

[Kom igång med grupper](get-started-groups.md) – Dela upp användare i grupper för att göra det lättare att hantera principer och appar som de har åtkomst till.
