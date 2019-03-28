---
title: Självstudie – Använda Autopilot till att registrera enheter i Intune
titleSuffix: Microsoft Intune
description: I den här självstudien ska du ställa in Windows Autopilot för att registrera enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36aa9ad733e2ae5e0f4a292b073fbebd5f5f5f8f
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57395986"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>Självstudie: Använda Autopilot till att registrera Windows-enheter i Intune
Med Windows Autopilot blir det enklare att registrera enheter. Med Microsoft Intune och Autopilot kan du ge dina slutanvändare nya enheter utan att behöva skapa, underhålla och tillämpa anpassade operativsystemavbildningar. 

I den här självstudien får du lära dig att:
> [!div class="checklist"]
> * Lägga till enheter i Intune
> * Skapa en Autopilot-enhetsgrupp
> * Skapa en Autopilot-distributionsprofil
> * Tilldela Autopilot-distributionsprofilen till enhetsgruppen
> * Distribuera Windows-enheter till användare

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

I [översikten över Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot) visas fördelar, scenarier och förutsättningar.


## <a name="prerequisites"></a>Krav
- [Konfigurera automatisk registrering i Windows](quickstart-setup-auto-enrollment.md)
- [Azure Active Directory Premium-prenumeration](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Lägg till enheter

Det första steget i att konfigurera Windows Autopilot är att lägga till Windows-enheter i Intune. Allt du behöver göra är att skapa en CSV-fil och importera den till Intune.

1. I en textredigerare skapar du en lista med kommaavgränsade värden (CSV) som identifierar Windows-enheterna. Använd följande format:
    
    *serial-number*, *windows-product-id*, *hardware-hash*, *optional-order-id*
    
    De första tre objekten krävs, men order-ID är valfritt.

2. Spara CSV-filen.

3. I [Intune på Microsoft Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter** > **Importera**.

    ![Skärmbild av Windows Autopilot-enheter](media/enrollment-autopilot/autopilot-import-device.png)

4. Under **Lägg till Windows Autopilot-enheter** bläddrar du till den CSV-fil som du sparade.

    ![Skärmbild av Lägg till Windows Autopilot-enheter](media/enrollment-autopilot/autopilot-import-device2.png)

5. Välj **Importera** för att börja importera enhetsinformationen. Det kan ta flera minuter att importera.

4. När importen är klar väljer du **Enhetsregistrering** > **Windows-registrering** > **Windows Autopilot** > **Enheter** > **Synkronisera**. Ett meddelande visar att synkroniseringen pågår. Processen kan ta några minuter att slutföra, beroende på hur många enheter du synkroniserar.

5. Uppdatera vyn för att se de nya enheterna.

## <a name="create-an-autopilot-device-group"></a>Skapa en Autopilot-enhetsgrupp

Nu ska du skapa en enhetsgrupp där du placerar de Autopilot-enheter som du nyss läste in.

1. I [Intune på Azure-portalen](https://aka.ms/intuneportal) väljer du **Grupper** > **Ny grupp**.
2. På bladet **Grupp**:
    1. Välj **Säkerhet** för **Grupptyp**.
    2. I **Gruppnamn** anger du *Autopilot-grupp*. I **Gruppbeskrivning** anger du *Testgrupp för Autopilot-enheter*.
    3. I **Medlemskapstyp** väljer du **Tilldelad**.
3. På bladet **Grupp** väljer du **Medlemmar** och lägger till Autopilot-enheterna i gruppen. Autopilot-enheter som ännu inte har registrerats är enheter där namnet är samma som enhetens serienummer.
4. Välj **Skapa**.  

## <a name="create-an-autopilot-deployment-profile"></a>Skapa en Autopilot-distributionsprofil

När du har skapat en enhetsgrupp, måste du skapa en distributionsprofil så att du kan konfigurera Autopilot-enheterna.

1. I [Intune på Microsoft Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil**.
2. I **Namn** anger du *Autopilot-profil*. I **Beskrivning** anger du *Testprofil för Autopilot-enheter*.
3. Ange **Omvandla alla målenheter till Autopilot** som **Ja**. Den här inställningen ser till att alla enheter i listan blir registrerade med Autopilots distributionstjänst. Det kan ta upp till 48 timmar för registreringen att bearbetas.
4. I **Distributionsläge** väljer du **Användarstyrd**. Enheter med den här profilen är associerade med användaren som registrerar enheten. Autentiseringsuppgifter krävs för att registrera enheten.
5. Välj **Azure AD-ansluten** i **Anslut till Azure AD som**.
6. Välj **Välkomstprogram**, konfigurera följande alternativ, låt de andra ha standardinställningarna och välj sedan **Spara**:
    - **Licensavtal för slutanvändare (EULA)**: **Dölj**
    - **Sekretessinställningar**: **Visa**
    - **Användarkontotyp**: **Standard**

6. Välj **Skapa** när du vill skapa profilen. Autopilot-distributionsprofilen kan nu tilldelas till enheterna.

## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Tilldela en Autopilot-distributionsprofil till en enhetsgrupp

Nu när distributionsprofilen har skapats kan du tilldela den till enhetsgruppen.
1. I [Intune på Microsoft Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > välj en profil.
2. Välj **Tilldelningar** på det specifika profilbladet. 
3. Välj **Välj grupper**. På bladet **Välj grupper** väljer du **Autopilot-grupp** och sedan **Välj**.

## <a name="distribute-devices-to-users"></a>Distribuera enheter till användare

Du kan nu distribuera Windows-enheterna till dina användare. När de loggar in för första gången kommer Autopilot-systemet automatiskt registrera och konfigurera enheterna. 

## <a name="clean-up-resources"></a>Rensa resurser

Om du inte vill använda Autopilot-enheter mer kan du ta bort dem.

1. Om enheterna har registrerats i Intune måste du först [ta bort dem från Azure Active Directory-portalen](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. I [Intune på Azure Portal](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter**.

3. Under **Windows Autopilot-enheter** markerar du de enheter som du vill ta bort. Välj sedan **Ta bort**.

4. Bekräfta borttagningen genom att välja **Ja**. Det kan ta några minuter att ta bort.

## <a name="next-steps"></a>Nästa steg

Det finns mer information om andra alternativ som är tillgängliga för Windows Autopilot.

> [!div class="nextstepaction"]
> [Fördjupande artikel om Autopilot-registrering](enrollment-autopilot.md)


