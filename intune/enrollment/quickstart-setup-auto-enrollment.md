---
title: Snabbstart – Konfigurera automatisk registrering i Intune
description: Snabbstart – Konfigurera automatisk registrering för Windows 10-enheter i Intune.
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78620818bfd13f0292e159c6a3670b5e3af53dab
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709507"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Snabbstart: Konfigurera automatisk registrering för Windows 10-enheter

I den här snabbstarten får du konfigurera Microsoft Intune till att automatiskt registrera enheter när specifika användare loggar in på Windows 10-enheter.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav

- Microsoft Intune-prenumeration [registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md).
- För att kunna slutföra den här snabbstarten måste du först [skapa en användare](../fundamentals/quickstart-create-user.md) och [skapa en grupp](../fundamentals/quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) som global administratör eller Intune-tjänstadministratör. Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="set-up-windows-10-automatic-enrollment"></a>Konfigurera automatisk registrering i Windows 10

I det här exemplet kommer du att använda MDM-registrering så att både företagets enheter och BYOD-enheter kan registreras automatiskt. Du kommer att registrera dig för en kostnadsfri Azure Active Directory Premium-prenumeration.

1. I Azure väljer du **Azure Active Directory** > **Mobilitet (MDM och MAM)** .
2. Välj **Hämta en kostnadsfri utvärderingsversion för att använda den här funktionen**. Om du väljer det här alternativet tillåts automatisk registrering med hjälp av den kostnadsfria utvärderingsversionen av Azure Active Directory Premium. 

    ![Välja den kostnadsfria utvärderingsversionen av Azure Active Directory Premium](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    Välj alternativet för kostnadsfri utvärderingsversion av **Enterprise Mobility + Security E5**. Dessutom måste du välja att **Aktivera** den kostnadsfria utvärderingsversionen.

    ![Välja kostnadsfri utvärderingsversion av Enterprise Mobility + Security E5](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. Välj **Microsoft Intune**. 

    ![Välja Microsoft Intune i listan](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Välj **Vissa** på **MDM-användaromfång** för att använda MDM-autoregistrering för att hantera företagsdata på dina anställdas Windows-enheter. MDM-autoregistrering kommer att konfigureras för AAD-anslutna enheter och Bring Your Own Device-scenarier.

    ![Välj ”Vissa” i listan Konfigurera](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Välj **Välj grupper** > **Contoso-testare** > **Välj** som tilldelad grupp.

    ![Välj den grupp som ska registreras](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Välj **Vissa** i **MAM-användaromfång** för att hantera data på personalens enheter.
7. Välj **Välj grupper** > **Contoso-testare** > **Välj** som tilldelad grupp. 
8. Använd standardvärdena för de återstående konfigurationsvärdena.
9. Välj **Spara**.

## <a name="clean-up-resources"></a>Rensa resurser

Om du vill konfigurera om automatisk registrering i Intune, så läs [Konfigurera registrering för Windows-enheter](windows-enroll.md).

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten har du lärt dig hur du ställer in automatisk registrering för Windows 10-enheter. Mer information om enhetsregistrering finns i [Vad är enhetsregistrering?](device-enrollment.md)

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Registrera din Windows 10-enhet](../quickstart-enroll-windows-device.md)
