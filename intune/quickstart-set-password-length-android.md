---
title: Snabbstart – Ange en obligatorisk lösenordslängd för Android-enheter
titlesuffix: Microsoft Intune
description: I den här snabbstarten använder du Microsoft Intune till att ange en lösenordslängd som krävs för Android-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395303"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>Snabbstart: Ange en obligatorisk lösenordslängd för Android-enheter

I den här snabbstarten använder du Microsoft Intune för att ange att Android-användare på företaget måste ange ett lösenord med en viss längd innan åtkomst beviljas till information i deras Android-enheter. 

> [!IMPORTANT]
> Förutom lösenordsinställningarna kan du också ange andra systemsäkerhetsinställningar som skyddar dina anställda. Mer information finns i [Inställningar för systemsäkerhet](compliance-policy-create-android-for-work.md#system-security-settings).

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör. Du hittar Intune i Azure Portal genom att välja **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip
1. När du har öppnat bladet **Microsoft Intune** väljer du **Enhetsefterlevnad** > **Principer** > **Skapa princip**.
2. Lägg till **Android-efterlevnad** som **Namn**. Ange även en **Beskrivning**.
3. För **Plattform**, välj **Android**. 
4. Välj **Inställningar** > **Systemsäkerhet** för att visa Android-bladet **Systemsäkerhet**.
5. I **Lösenord**, bredvid **Kräv ett lösenord för att låsa upp mobila enheter**, klickar du på **Kräv**.
6. Bredvid **Minsta längd på lösenord** anger du **6**.  

    ![Skärmbild som visar hur en grupp skapas i Microsoft Intune](./media/quickstart-set-password-length-android-01.png)

7. När du är klar klickar du på **OK** för att stänga bladet **Systemsäkerhet**. 
8. Klicka på **OK** för att stänga bladet **Kompatibilitetsprincip för Android**. 
9. Klicka på **Skapa** för att skapa principen.

När du har skapat principen visas den i listan **Enhetsefterlevnad – Principer**. 

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten använde du Intune till att skapa en efterlevnadsprincip för personalens Android-enheter som kräver ett lösenord på minst sex tecken.

> [!div class="nextstepaction"]
> [Konfigurera automatisk registrering](quickstart-setup-auto-enrollment.md)
