---
title: Snabbstart – Registrera din Windows 10 Desktop-enhet i Microsoft Intune
description: Snabbstart – Använda företagsportalen för att registrera din Windows 10 Desktop-enhet i Microsoft Intune.
services: microsoft-intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/30/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 658a7655-a6df-4dbe-b56c-22c7fc60e706
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91f20411f668428c8bf3af8b0bd4ae6f4b0b545f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73713513"
---
# <a name="quickstart-enroll-your-windows-10-device"></a>Snabbstart: Registrera din Windows 10-enhet

I den här snabbstarten antar du först rollen som Intune-användare och registrerar din Windows 10-enhet i Microsoft Intune. Går därefter tillbaka till Intune och bekräftar den registrerade enheten.

Om du registrerar dina enheter i Microsoft Intune kan dina Windows 10-enheter få åtkomst till organisationens skyddade data, t.ex. e-post, filer och andra resurser. Detta gäller för både Windows 10 Desktop- och Windows 10 Mobile-enheter. Genom att registrera dina enheter kan du skydda både din och organisationens åtkomst och dessutom hålla arbetsdata åtskilda från personliga data.

> [!TIP]
> Ta reda på vad som händer när du [registrerar din enhet i Intune](/intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows) och hur [informationen på enheten](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) påverkas.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav

- Microsoft Intune-prenumeration – [registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md)
- För att slutföra den här snabbstarten måste du genomföra stegen för att [konfigurera automatisk registrering i Intune](quickstart-setup-auto-enrollment.md).

## <a name="confirm-your-windows-10-desktop-version"></a>Bekräfta din Windows 10 Desktop-version

Innan du registrerar ditt Windows 10 Desktop måste du bekräfta den version av Windows som du har installerat.

1. Högerklicka på **startikonen** i Windows och välj **Inställningar** för att visa alternativ för Windows-inställningar.

   ![Skärmbild av Windows-inställningar – System](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-01.png)

2. Välj **System** > **Om**. 

   ![Skärmbild av dina systeminställningar](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-02.png)

    > [!TIP]
    > Du kan även skriva frasen ”Om din dator” i **sökfältet** och sedan välja **Om din dator**.

3. I fönstret **Inställningar** visas en lista över **Windows-specifikationer** för datorn. Leta upp **versionen** i den här listan.

4. Bekräfta att **versionen** av Windows 10 är **1607 eller senare**.

    > [!IMPORTANT]
    > De steg som visas i den här snabbstarten gäller för Windows 10-version **1607 eller senare**. Om du har version **1511 eller äldre** fortsätter du med [de här stegen](/intune-user-help/enroll-windows-10-device).  

## <a name="enroll-windows-10-desktop"></a>Registrera Windows 10 Desktop

1. Gå tillbaka till Windows-inställningar och välj **Konton**.

   ![Skärmbild av dina systeminställningar – Konton](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-03.png)

2. Välj **Åtkomst till arbete eller skola** > **Anslut**.

    ![Välj kontot för arbete eller skola](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-04.png)

3. Logga in på Intune med ditt arbetskonto eller skolkonto och välj sedan **Nästa**. Om du följde snabbstarten [skapa en användare och tilldela en licens](../fundamentals/quickstart-create-user.md), kan du logga in med det användarkonto som du skapade.

    > [!NOTE]
    > Om du konfigurerar ett ”. onmicrosoft.com” får användarkontot **.onmicrosoft.com** som en del av kontoadressen. 

   ![Ange ditt arbets- eller skolkonto](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-05.png)

    Ett meddelande visas som anger att ditt företag eller din skola registrerar din enhet.

4. När sidan **Allt är klart!** visas väljer du **Klar**. Klart.

5. Nu visas det tillagda kontot som en del av inställningarna för **Åtkomst till arbete eller skola** på Windows Desktop-enheten.

   ![Skärmbild av nyligen tillagt konto](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-06.png)

    Om du har följt de föregående stegen, men ändå inte kan komma åt din e-post eller dina filer på arbetet eller i skolan, kan du följa anvisningarna i [Felsökningssteg att följa för Åtkomst för arbete eller skola](/intune-user-help/troubleshoot-your-windows-10-device-windows#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).

## <a name="confirm-your-device-enrollment-in-intune"></a>Bekräfta din enhetsregistrering i Intune

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) som global administratör eller Intune-tjänstadministratör.
2. Välj **Enheter** > **Samtliga enheter** för att visa de registrerade enheterna i Intune.
3. Kontrollera att du har ytterligare en enhet registrerad i Intune.

   ![Skärmbild av Intune-registrerade enheter](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-07.png)

## <a name="clean-up-resources"></a>Rensa resurser

Om du vill avregistrera din Windows-enhet läser du [Ta bort din Windows-enhet från hanteringen](/intune-user-help/unenroll-your-device-from-intune-windows).

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten lärde du dig att registrera en Windows 10-enhet i Intune. Du kan lära dig andra sätt att registrera enheter på alla plattformar. Mer information om hur du använder enheter med Intune finns i [Använda hanterade enheter för att få arbetet gjort](/intune-user-help/use-managed-devices-to-get-work-done).

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Ange en obligatorisk lösenordslängd för Android-enheter](../quickstart-set-password-length-android.md)
