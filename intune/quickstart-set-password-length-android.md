---
title: Snabbstart – Skapa en efterlevnadsprincip för lösenord för Android-enheter
titleSuffix: Microsoft Intune
description: I den här snabbstarten använder du Microsoft Intune till att ange den lösenordslängd som krävs för Android-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4a16272f32b8546e7e9bb12a22f16235ab49aed
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799666"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Snabbstart: Skapa en efterlevnadsprincip för lösenord för Android-enheter

I den här snabbstarten använder du Microsoft Intune för att ange att Android-användare på företaget måste ange ett lösenord med en viss längd innan åtkomst beviljas till information i deras Android-enheter. 

En Intune-enhetsefterlevnadsprincip anger de regler och inställningar som enheter måste uppfylla för att anses vara kompatibla. Du kan använda efterlevnadsprinciper med villkorsstyrd åtkomst för att tillåta eller blockera åtkomst till företagsresurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet.

> [!IMPORTANT]
> Förutom lösenordsinställningarna kan du också ange andra systemsäkerhetsinställningar som skyddar dina anställda. Mer information finns i [Inställningar för systemsäkerhet](compliance-policy-create-android-for-work.md#system-security-settings).

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör. 

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip

För den här snabbstarten använder du Intune för att kräva att Android-användare bland personalen anger ett lösenord med en viss längd innan åtkomst beviljas till information i deras Android-enheter.

1. Välj **Enhetsefterlevnad** > **Principer** > **Skapa princip** i Intune.
2. Lägg till **Android-efterlevnad** som **Namn**. Ange även en **Beskrivning**.
3. För **Plattform**, välj **Android**. 
4. Välj **Inställningar** > **Systemsäkerhet** för att visa Android-bladet **Systemsäkerhet**.
5. Klicka på **Kräv** intill **Kräv ett lösenord för att låsa upp mobila enheter**.
6. Ange **Minst numeriskt** bredvid **Krav på lösenordstyp**.
7. Ange **6** intill **Minsta längd på lösenord**. 

    ![Skärmbild som visar hur en grupp skapas i Microsoft Intune](media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. När du är klar klickar du på **OK** > **OK** > **Skapa** för att skapa principen.

När du har skapat principen visas den i listan över enhetsefterlevnadsprinciper. 

## <a name="clean-up-resources"></a>Rensa resurser

Ta bort principen när du inte längre behöver den. Gör det genom att välja efterlevnadsprincipen och klicka på **Ta bort**.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten använde du Intune till att skapa en efterlevnadsprincip för personalens Android-enheter som kräver ett lösenord på minst sex tecken. Mer information om att skapa efterlevnadsprinciper finns i [Kom igång med efterlevnadsprinciper för enheter i Intune](device-compliance-get-started.md).

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Skicka meddelanden till icke-kompatibla enheter](quickstart-send-notification.md)
