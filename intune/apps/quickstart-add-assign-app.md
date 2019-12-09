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
ms.openlocfilehash: d09857c4e5b63947a6e3b3140f673f0887f7f920
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563415"
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
2. Välj **Windows 10** i avsnittet **Office 365-paket** i listrutan **Apptyp**.
3. Välj **Konfigurera appaket** och välj de Office-appar som ska tilldelas till Intune-användaren.
4. Klicka på **OK** för att godkänna de appar som valts som standard.
5. Välj **Information om appsvit**.
6. Ange **Microsoft Office 365-appaket** som **Paketnamn**.
7. Ange **Microsoft Office 365-appaket** som **Beskrivning av svit**.
8. Klicka på **Ja** intill **Visa den som aktuell app i företagsportalen**.
9. Klicka på **OK**.

    ![Skärmbild av tillägg av appinformation](./media/quickstart-add-assign-app/quickstart-add-assign-app-01.png)

10. Välj **Inställningar för appaket**.
11. I listrutan **Uppdateringskanal** väljer du **Varje månad**.
12. Klicka på **OK** > **Lägg till**.

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
