---
title: Snabbstart – Skapa och tilldela en appskyddsprincip
titleSuffix: Microsoft Intune
description: I den här snabbstarten använder du Microsoft Intune för att skapa och tilldela en appskyddsprincip.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ec42d122bf3da3fbacef513d6af2dbe124b196c
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530771"
---
# <a name="quickstart-create-and-assign-an-app-protection-policy"></a>Snabbstart: Skapa och tilldela en skyddsprincip för ett program

I den här snabbstarten använder du Intune för att skapa och tilldela en appskyddsprincip till en klientapp på en slutanvändares enhet. Intune använder appskyddsprinciper för att bekräfta att dina appar uppfyller organisationens dataskyddskrav.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav

- För att slutföra den här snabbstarten måste du [skapa en användare](quickstart-create-user.md), [skapa en grupp](quickstart-create-group.md), [registrera en enhet](quickstart-setup-auto-enrollment.md) och [lägga till och tilldela en app](quickstart-add-assign-app.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in i [Intune](https://aka.ms/intuneportal) som [global administratör eller Intune-tjänstadministratör](users-add.md#types-of-administrators). Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-an-app-protection-policy"></a>Skapa en appskyddsprincip

Använd följande steg om du vill skapa en appskyddsprincip:

1. I [Intune](https://aka.ms/intuneportal) väljer du **Klientappar** > **Appskyddsprinciper** > **Skapa princip**. 
2. Ange följande information: 

    - **Namn**: *Windows 10-innehållsskydd*
    - **Beskrivning**: *Användare som är associerade med den här principen kommer inte att kunna klippa ut, kopiera eller klistra in innehåll mellan den tilldelade appen och andra icke-hanterade appar på enheten.*
    - **Plattform**: *Windows 10*
    - **Registreringsstatus**: *Med registrering*

3. Välj **Skyddade appar** för att välja de appar som måste följa den här principen.
4. Klicka på **Lägg till appar**.
5. Under **Rekommenderade appar** väljer du **Word Mobile**.
5. Klicka på **OK** > **OK**. 
6. Välj **Nödvändiga inställningar** för att konfigurera appen.
7. Klicka på **Tillåt åsidosättningar** för att ställa in Windows informationsskyddsläge. Om du väljer det här alternativet blockeras företagsdata från att lämna den skyddade appen.
8. Klicka på **OK** > **Skapa**.

Appskyddsprincipen visas nu i Intune.

### <a name="assign-the-app-protection-policy"></a>Tilldela appskyddsprincipen

När du har skapat en appskyddsprincip i Intune kan du tilldela till grupper. 

Använd följande steg för att tilldela appskyddsprincipen:

1. I [Intune](https://aka.ms/intuneportal) väljer du **Intune** > **Klientappar** > **Appskyddsprinciper**. 
2. Välj den appskyddsprincip som du skapade tidigare. I den här snabbstarten är principen **Windows 10-innehållsskydd**.
3. Välj **Tilldelningar**.
4. Klicka på **Välj grupper som ska inkluderas** på fliken **Inkludera**.
5. Välj **Contoso-testare** som den grupp som ska inkluderas.
6. Klicka på **Välj** > **Spara**. 

Du har nu tilldelat appskyddsprincipen.

> [!NOTE]
> Appskyddsprinciper kan endast tillämpas på grupper som innehåller användare, inte grupper som innehåller enheter.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten skapade och tilldelade du en appskyddsprincip. Användare av den app som har den här principen tilldelad kommer inte att kunna klippa ut, kopiera eller klistra in innehåll mellan den tilldelade appen och andra icke-hanterade appar på enheten. Den här typen av skydd hjälper till att skydda din organisations data. Mer information om appskyddsprinciper i Intune finns i [Vad är appskyddsprinciper?](app-protection-policy.md)

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Skapa och tilldela en anpassad roll](quickstart-create-custom-role.md)
