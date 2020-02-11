---
title: Snabbstart – Lägga till och tilldela en klientapp
titleSuffix: Microsoft Intune
description: I den här snabbstarten använder du Microsoft Intune för att lägga till och tilldela en klientapp.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40337b3c45885dacf486173814044a27b7f3f6cc
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755076"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Snabbstart: Lägg till och tilldela en klientapp

I den här snabbstarten använder du Intune för att lägga till och tilldela en klientapp till företagets personal. En av en administratörs prioriteringar är att säkerställa att användarna har åtkomst till appar som de behöver för att utföra sitt arbete. 

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav

- För att slutföra den här snabbstarten måste du [skapa en användare](../fundamentals/quickstart-create-user.md), [skapa en grupp](../fundamentals/quickstart-create-group.md) och [registrera en enhet](../quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in på [Intune](https://aka.ms/intuneportal) som [global administratör eller Intune-tjänstadministratör](../fundamentals/users-add.md#types-of-administrators). Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="add-the-client-app-to-intune"></a>Lägga till klientappen i Intune

En app kan inkluderas så att Intune kan hantera aspekter av appen. 

Använd följande steg för att lägga till en app i Intune:
1. Välj **Appar** > **Alla appar** > **Lägg till** i [Intune](https://aka.ms/intuneportal). 
2. Välj **Windows 10** i avsnittet **Office 365-paket** på fönstret **Välj apptyp**.
3. Klicka på **Välj**. Stegen **Lägg till app** visas.
4. Bekräfta standardinformationen på sidan **Information om appsvit**.
5. Klicka på **Nästa** för att visa sidan **Konfigurera appsviten**.
6. Bredvid **Uppdatera kanal** väljer du **Varje månad** i listrutan.
7. Bekräfta de återstående standardvärdena på sidan ***Konfigurera appsvit**.
8. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.
9. Klicka på **Välj omfångstaggar** om du vill lägga till omfångstaggar för appen. Mer information finns i [Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT](~/fundamentals/scope-tags.md).
10. Klicka på **Nästa** för att visa sidan **Tilldelningar**.
11. Välj grupptilldelningar för appen. Mer information finns i [Lägga till grupper för att organisera användare och enheter](~/fundamentals/groups-add.md). 
12. Visa sidan **Granska och skapa** genom att klicka på **Nästa**. Granska värdena och inställningarna som du har angett för appen.
13. När du är färdig klickar du på **Skapa** för att lägga till appen i Intune.

## <a name="assign-the-app-to-a-group"></a>Tilldela appen till en grupp

När du har lagt till en app till Microsoft Intune kan du tilldela appen till grupper med användare eller enheter.

> [!NOTE]
> Den här snabbstarten bygger på tidigare snabbstarter i den här serien. Information finns i [förutsättningarna](quickstart-add-assign-app.md#prerequisites) i den här snabbstarten.

Använd följande steg för att tilldela en app till en grupp:
1. Välj **Appar** > **Alla appar** i [Intune](https://aka.ms/intuneportal). 
2. Välj den app som du vill tilldela till en grupp.
3. Klicka på **Tilldelningar** > **Lägg till grupp** så att fönstret **Lägg till grupp** visas.
4. Välj **Tillgänglig för registrerade enheter** i listrutan **Tilldelningstyp**. 
5. Klicka på **Inkluderade grupper** > **Välj grupper som ska inkluderas** > **Contoso-testare**.
6. Klicka på **Välj** > **OK** > **OK** > **Spara** för att tilldela gruppen.

Du har nu tilldelat appen till gruppen **Contoso-testare**.

## <a name="install-the-app-on-the-enrolled-device"></a>Installera appen på den registrerade enheten

Du måste installera och använda företagsportalappen för att installera den **Contoso-att-göra-app** som gjorts tillgänglig av Intune. Använd följande steg för att kontrollera att appen är tillgänglig för användaren av den registrerade enheten.

1. Logga in på den registrerade Windows 10 Desktop-enheten.

    > [!IMPORTANT]
    > Enheten måste vara [registrerad med Intune](../quickstart-enroll-windows-device.md). Dessutom måste du logga in på enheten med ett konto som ingår i den grupp som du tilldelade till appen.

2. Från **Start-menyn** öppnar du **Microsoft Store**. Leta sedan upp **företagsportalappen** och installera den.
3. Starta **företagsportalappen**.
4. Klicka på den app som du lade till med hjälp av Intune. I den här snabbstarten lade du till appen **Microsoft Office 365-appaket**.

    > [!NOTE]
    > Om du inte kunde tilldela några appar till Intune-användaren visas följande meddelande: *Din IT-administratör har inte gjort några appar tillgängliga för dig.*

5. Klicka på **Installera**.

Om företaget kräver att du i stället tilldelar företagsportalappen till personalen kan manuellt tilldela företagsportalappen för Windows 10 manuellt direkt från Intune. Mer information finns i [Lägga till företagsportalappen för Windows 10 manuellt med hjälp av Microsoft Intune](../company-portal-app.md)

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten lade du till appar i Intune, tilldelade apparna till en grupp och installerade apparna på den registrerade Windows 10 Desktop-enheten. Mer information om hur du hanterar appar i Intune finns i [Vad är apphantering i Microsoft Intune?](app-management.md)

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Skapa och tilldela en appskyddsprincip](quickstart-create-assign-app-policy.md)
