---
title: "Åtgärder för inkompatibilitet"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig hur du skapar åtgärder för ej kompatibla enheter"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 16da087e741e335144266c838c0a91050bd7d520
ms.lasthandoff: 03/15/2017


---

# <a name="create-actions-for-non-compliance"></a>Skapa åtgärder för inkompatibilitet

Med **Åtgärder för inkompatibilitet** kan du konfigurera en tidsordnad sekvens med åtgärder som tillämpas på enheter som är inkompatibla. Du kan t.ex. meddela användare via e-post om inkompatibla enheter eller genom villkorlig åtkomst blockera enheterna från att komma åt företagets resurser.

## <a name="use-case-scenario"></a>Användningsfallsscenario

När en enhet rapporteras som inkompatibel av en efterlevnadsprincip för en Intune-enhet, blockeras den som standard omedelbart genom villkorlig åtkomst, och användaren får ett e-postmeddelande med anvisningar om hur inkompatibiliteten kan åtgärdas. Med **Åtgärder för inkompatibilitet** har du större flexibilitet när du ska bestämma dig för vad du vill göra när en enhet är inkompatibel. Du kan t.ex. bestämma dig för att inte blockera enheten omedelbart, för att sedan ge användaren en respitperiod att åtgärda problemet.

Det finns två typer av åtgärder:

-   Meddela användaren via e-post

-   Blockera åtkomst till företagets resurser via villkorlig åtkomst

## <a name="notify-the-user-via-email"></a>Meddela användaren via e-post

Du kan välja bland standardmallarna för e-post eller skapa en helt anpassade e-postmeddelanden. Vi tillhandahåller anpassning av ämne, brödtext, företagslogotyp, kontaktuppgifter och ytterligare mottagare.

## <a name="block-corporate-resource-access-through-conditional-access"></a>Blockera åtkomst till företagets resurser via villkorlig åtkomst

Du kan ange ett schema med det antal dagar som enhetens åtkomst till företagets resurser ska blockeras. Detta kan verkställas direkt, eller så kan du ge användaren en respitperiod under vilken hen kan åtgärda inkompatibiliteten.

## <a name="before-you-begin"></a>Innan du börjar

Du måste ha skapat minst en princip för enhetsefterlevnad för att kunna vidta åtgärder mot inkompatibilitet.

-   Läs om hur du skapar en princip för enhetsefterlevnad för Windows:

    -   [Android](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android)

    -   [Android for Work](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android-for-work)

    -   [iOS](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-ios)

    -   [Windows](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-windows)

Du måste ha konfigurerat villkorlig EMS-åtkomst om du planerar att använda principer för enhetsefterlevnad för att blockera enheter från att använda företagets resurser.

- Läs om [hur du konfigurerar villkorlig EMS-åtkomst](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).

Du måste dessutom ha skapat en mall för aviseringsmeddelanden. Mallen för aviseringsmeddelanden används senare under processen när du skapar åtgärder mot inkompatibilitet som ska skickas med e-post till dina användare.

### <a name="to-add-a-notification-message-template"></a>Lägga till en mall för aviseringsmeddelanden

Gå till bladet **Principer för enhetsefterlevnad**:

1.  Välj **Meddelanden** under **Hantera**. Bladet för mallar för aviseringsmeddelanden visas.

    ![Lägga till en meddelandemall](../media/afnc-1.png)

2.  Välj **Lägg till** och definiera sedan följande:

    a.  Beskrivning

    b.  Från

    c.  Ärende

    d.  Meddelande

    e.  E-postrubrik – Infoga företagslogotyp

    f.  E-postrubrik – Infoga företagsnamn

    g.  E-postsidfot – Inkludera kontaktinformation

     ![Mallen för aviseringsmeddelanden](../media/afnc-2.png)

När du har lagt till informationen klickar du på **Skapa**. Mallen för aviseringsmeddelanden är tillgänglig att användas.

> [!NOTE] 
> Du kan också redigera en meddelandemall som du skapat tidigare.

## <a name="to-create-actions-for-non-compliance"></a>Skapa åtgärder avseende inkompatibilitet

Du kan lägga till en åtgärd när du skapar en ny princip för enhetsefterlevnad eller genom att redigera en befintlig princip för enhetsefterlevnad.

1.  Välj **Principer** under **Hantera** på bladet **Principer för enhetsefterlevnad**.

2.  Välj en princip för enhetsefterlevnad genom att klicka på den.

    ![Efterlevnadsprinciper](../media/afnc-3.png)

3.  Bladet **Principegenskaper för enhetsefterlevnad** öppnas. Välj **Åtgärder för inkompatibilitet**.

4.  Bladet Åtgärder för inkompatibilitet öppnas. Ange åtgärdsparametrar genom att välja **Lägg till**.

    ![Bladet Åtgärder för inkompatibilitet](../media/afnc-4.png)

Åtgärderna för inkompatibilitet är:

-   **Framtvinga princip för villkorlig åtkomst**

-   **Skicka e-post till slutanvändare**

### <a name="enforce-conditional-access-policy"></a>Framtvinga princip för villkorlig åtkomst

Lägga till den här åtgärden för inkompatibilitet:

1.  Välj **Lägg till** på bladet **Åtgärder för inkompatibilitet**.

2.  Välj **Framtvinga princip för villkorlig åtkomst** i listrutan Åtgärd på bladet **Åtgärdsparametrar**.

3.  Under **Schema** kan du ange i hur många dagar (0 till 255) som principen för villkorlig åtkomst ska tillämpas. Om du anger **0** dagar innebär det att villkorlig åtkomst **genast** måste blockera åtkomsten till företagets resurser när enheterna är inte uppfyller principerna för enhetsefterlevnad.

    ![Schemalägga åtgärder för inkompatibilitet](../media/afnc-5.png)

4.  Välj **Lägg till** och välj sedan **OK** på bladet **Åtgärder**.

5.  Välj **Spara** på bladet **Principegenskaper för enhetsefterlevnad**.

### <a name="send-e-mail-to-end-user"></a>Skicka e-post till slutanvändare

Du kan skicka e-post med hjälp av en e-postmall till användare som inte uppfyller efterlevnadskraven. De här e-postmeddelandena bidrar till att genomdriva enhetsefterlevnad i hela organisationen.

Lägga till den här åtgärden för inkompatibilitet:

1.  Välj **Lägg till** på bladet **Åtgärder för inkompatibilitet**.

2.  Välj **Skicka e-post till slutanvändare** i listrutan Åtgärd på bladet **Åtgärdsparametrar**.

3.  Välj en redan skapad meddelandemall genom att klicka på **Meddelandemall**. Du kan visa meddelandemallens innehåll och sedan klicka på **Välj**.

    ![Meddelandemall](../media/afnc-6.png)

> [!NOTE] 
> Du kan visa meddelandemallen, men du kan inte redigera den. Om du vill redigera meddelandemallen måste du gå tillbaka till bladet **Aviseringar**.

1.  Ange under **Schema** det antal dagar efter det att inkompatibiliteten konstaterats som e-postmeddelandet bör skickas till användarna. Om du anger **0** dagar innebär det att e-postmeddelandet skickas **Omedelbart**.

2.  Välj **Lägg till** och välj sedan **OK** på bladet **Åtgärder**.

3.  Välj **Spara** på bladet **Principegenskaper för enhetsefterlevnad**.

