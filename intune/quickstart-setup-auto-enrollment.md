---
title: Snabbstart – Konfigurera automatisk registrering i Intune
description: Snabbstart – Konfigurera automatisk registrering för Windows 10-enheter i Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581777"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Snabbstart: Konfigurera automatisk registrering för Windows 10-enheter

I den här snabbstarten får du konfigurera Microsoft Intune till att automatiskt registrera enheter när specifika användare loggar in på Windows 10-enheter.

Om du inte har en Intune-prenumeration [så registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav

- För att kunna slutföra den här snabbstarten måste du först [skapa en användare](quickstart-create-user.md) och [skapa en grupp](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör.

## <a name="set-up-windows-10-automatic-enrollment"></a>Konfigurera automatisk registrering i Windows 10

I det här exemplet kommer du att använda MDM-registrering så att både företagets enheter BYOD-enheter kan registreras automatiskt.

1. Välj **Azure Active Directory** > **Mobilitet (MDM och MAM)** > **Microsoft Intune** >  **Vissa**.
![Webbläsare](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. Välj **Välj grupper** > **Contoso Testare** > **Välj**.
3. Använd standardvärdena för följande URL:er:
    - Webbadress till MDM-användarvillkor
    - Webbadress till MDM-identifiering
    - Webbadress till MDM-kompatibilitet
4. Välj **Spara**.
5. Logga in som en användare i gruppen på en Windows 10-enhet och följ anvisningarna.

## <a name="clean-up-resources"></a>Rensa resurser

Om du vill konfigurera om automatisk registrering i Intune, så läs [Konfigurera registrering för Windows-enheter](windows-enroll.md).

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten har du lärt dig hur du ställer in automatisk registrering för Windows 10-enheter. Du kan lära dig andra sätt att registrera enheter på alla plattformar.

> [!div class="nextstepaction"]
> Artikeln [Vad är enhetsregistrering?](device-enrollment.md)