---
title: Snabbstart – Efterlevnadsprincip för lösenord för Android-enheter
titleSuffix: Microsoft Intune
description: I den här snabbstarten använder du Microsoft Intune för att ange den lösenordslängd som krävs för Android-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61fdf91d57ce5d187a0c43153f317b0b42c6b46c
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409761"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Snabbstart: Skapa en efterlevnadsprincip för lösenord för Android-enheter

I den här snabbstarten använder du Microsoft Intune för att ange att Android-användare på företaget måste ange ett lösenord med en viss längd innan åtkomst beviljas till information i deras Android-enheter.

En Intune-enhetsefterlevnadsprincip anger de regler och inställningar som enheter måste uppfylla för att anses vara kompatibla. Du kan använda efterlevnadsprinciper med villkorlig åtkomst för att tillåta eller blockera åtkomst till företagsresurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet.

> [!IMPORTANT]
> Förutom lösenordsinställningarna kan du också ange andra systemsäkerhetsinställningar som skyddar dina anställda. Mer information finns i [Inställningar för systemsäkerhet](compliance-policy-create-android-for-work.md).

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) som [global administratör](../fundamentals/users-add.md#types-of-administrators) eller [tjänstadministratör](../fundamentals/users-add.md#types-of-administrators) för Intune.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip

Skapa en enhetsefterlevnadsprincip som kräver att Android-användare anger ett lösenord med en viss längd innan åtkomst beviljas till information på deras Android-enheter.

1. I Intune väljer du **Enheter** > **Efterlevnadsprinciper** > **Skapa princip**.

2. Lägg till **Android-efterlevnad** som **Namn**. Ange även en **Beskrivning**.

3. Välj **Android Enterprise** för **Plattform**.

4. I **Profiltyp** väljer du **Arbetsprofil**.

5. Välj **Inställningar** > **Systemsäkerhet** för att visa Android-bladet **Systemsäkerhet**.

6. I **Kräv ett lösenord för att låsa upp mobila enheter** väljer du **Kräv**.

7. I **Krav på lösenordstyp** väljer du **Minst numeriskt**.

8. I **Minsta lösenordslängd** anger du **6**.

    ![Skärmbild som visar hur en grupp skapas i Microsoft Intune](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

9. När du är klar väljer du **OK** > **OK** > **Skapa** för att skapa principen.

När du har skapat principen visas den i listan över enhetsefterlevnadsprinciper.

## <a name="clean-up-resources"></a>Rensa resurser

Ta bort principen när du inte längre behöver den. Gör det genom att välja efterlevnadsprincipen och klicka på **Ta bort**.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten använde du Intune till att skapa en efterlevnadsprincip för personalens Android-enheter som kräver ett lösenord på minst sex tecken. Mer information om att skapa efterlevnadsprinciper finns i [Kom igång med efterlevnadsprinciper för enheter i Intune](device-compliance-get-started.md).

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Skicka meddelanden till icke-kompatibla enheter](../quickstart-send-notification.md)
