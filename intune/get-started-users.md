---
title: "Kom igång med användare"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e711f32ebd77a83b17e6db468f8cb23a409c8d31
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="get-started-with-users"></a>Kom igång med användare

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Azure Active Directory hanterar organisationens objektgrupper, t.ex. enheter och appar, och även organisationens användargrupper. Du kan gruppera användare eller enheter tillsammans i stället för att hantera varje enhet individuellt. På så sätt kan du enkelt tilldela appar och inställningar till ett stort antal användare och enheter.

## <a name="how-do-i-create-a-user"></a>Hur skapar jag en användare?

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Sök efter **användare och grupper** med hjälp av **Sök resurser**.
3. När du har öppnat bladet **Användare och grupper** väljer du **Alla användare** och väljer sedan **+ Ny användare**.
4. Ange information om användaren, t.ex. **namn** och **användarnamn**. Domännamndelen av användarnamnet måste antingen vara det inledande standarddomännamnet, t.ex. contoso.onmicrosoft.com, eller ett verifierat, ofedererat domännamn, t.ex. contoso.com.
5. Välj den testgrupp du vill lägga till användaren i under **Grupper**.
6. Spara det automatiskt genererade användarlösenordet så att du kan använda det till att logga in på en testenhet. Du måste ge det här lösenordet till användare så att de kan ändra det till ett normalt lösenord som de kan komma ihåg.
7. Välj **Skapa** på bladet **Användare**.

## <a name="assigning-licenses-to-users"></a>Tilldela licenser till användare

När du har skapat en användare måste du använda [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) för att tilldela den användaren en Intune-licens. Användare kan inte registrera sina enheter för hantering innan du har tilldelat dem en licens.

1. Logga in på [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) med samma autentiseringsuppgifter du använde för att logga in på Intune.
2. Välj **Användare** > **Aktiva användare** och välj sedan den användare du skapade tidigare.
3. Du kan behöva vänta en stund tills all information om användaren har lästs in. När informationen har lästs in väljer du **Redigera** för användarens **produktlicenser**.
4. Tilldela användaren en **plats** och växla sedan Intune till **På**.

 > [!NOTE]
 > En av de tillgängliga licenserna används nu för den här användaren. Om du använder livemiljön kan du inaktivera användningen av den här licens om du senare vill tilldela den till riktig användare.

5. Välj **Spara**.
