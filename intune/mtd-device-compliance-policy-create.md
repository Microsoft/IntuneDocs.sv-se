---
title: "Skapa en princip för Mobile Threat Defense-enhetsefterlevnad med Intune"
titleSuffix: Intune on Azure
description: "Skapa en princip för Mobile Threat Defense-enhetsefterlevnad i Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6b05522c7390acb3974e088ecd60d13db46ef5a
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2017
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Skapa en princip för Mobile Threat Defense-enhetsefterlevnad med Intune

> [!NOTE] 
> Detta avsnitt gäller alla Mobile Threat Defense-partner.

Intune med MTD hjälper dig att identifiera hot och bedöma risker på mobila enheter. Du kan skapa en Intune-principregel för enhetsefterlevnad som bedömer risken och avgör om enheten uppfyller efterlevnadskraven. Du kan sedan använda principen för villkorlig åtkomst för att blockera åtkomst till tjänster utifrån enhetens efterlevnad.

## <a name="before-you-begin"></a>Innan du börjar

Som en del av MTD-installationen skapade du i MTD-partnerkonsolen en princip som klassificerar olika hot i kategorierna Hög, Medel och Låg. Du måste nu ange MTD-nivå i Intune-principen för enhetsefterlevnad.

Förutsättningar för principen för enhetsefterlevnad med MTD:

-   Ställ in MTD-integrering med Intune

-   Aktivera MTD-anslutningen i Intune

## <a name="to-create-a-mtd-device-compliance-policy"></a>Så här skapar du en princip för enhetsefterlevnad

1.  Gå till [Azure Portal](https://portal.azure.com/) och logga in med dina Intune-autentiseringsuppgifter.

2.  Välj **Fler tjänster** på den vänstra menyn på **Azure-instrumentpanelen** och skriv sedan **Intune** i textrutefiltret.

3.  Välj **Intune**. **Intune-instrumentpanelen** öppnas.

4. Välj **Enhetsefterlevnad** på **Intunes instrumentpanel** och välj sedan **Principer** under avsnittet **Hantera**.

5.  Välj **Skapa princip**, ange ett **namn** på och en **beskrivning** av principen för enhetsefterlevnad, välj **plattform** och välj sedan **Konfigurera** under avsnittet **Inställningar**.

6.  Välj **Enhetens hälsotillstånd** på bladet för **efterlevnadsprincip**.

7.  På bladet **Enhetens hälsotillstånd** väljer du mobilhotnivå i listrutan under **Kräv att enheten ska hållas på eller under mobilhotnivån**.

    a.  **Skyddad**: Det här är det säkraste alternativet. Enheten får inte ha några förekommande hot och ska ha tillgång till företagsresurser. Om något hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.

    b.  **Låg**: Enheten är kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.

    c.  **Medel**: Enheten är kompatibel om hoten som hittas på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.

    d.  **Hög**: Det här alternativet är minst säkert. Detta tillåter alla hotnivåer och använder endast Mobile Threat Defense i rapporteringssyfte. Enheterna måste ha MTD-appen aktiverad med den här inställningen.

8.  Klicka på **OK** två gånger och välj sedan **Skapa**.

> [!IMPORTANT]
> Om du skapar principer för villkorlig åtkomst till Office 365 eller andra tjänster kommer utvärderingen av efterlevnad att bedömas och icke-kompatibla enheter kommer inte att få åtkomst till företagsresurser förrän hotet har lösts i enheten.

## <a name="to-assign-a-mtd-device-compliance-policy"></a>Så här tilldelar du en policy för MTD-enhetsefterlevnad

Om du vill tilldela en princip för enhetsefterlevnad till användare, väljer du en princip som du tidigare har konfigurerat. Du hittar befintliga principer på bladet **Principer för enhetsefterlevnad**.

1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas det blad där du kan välja **Azure Active Directory-säkerhetsgrupper** och tilldela dem till principen.

2. Öppna bladet som visar säkerhetsgrupper för Azure AD genom att välja **Välj grupper**.  När du väljer **Välj** distribueras principen till användarna.

    > [!NOTE] 
    > Du har tillämpat principen på användarna. Efterlevnaden hos de enheter som används av de användare som principen är inriktad på kommer att utvärderas.