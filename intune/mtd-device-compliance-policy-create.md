---
title: Skapa en princip för MTD-enhetsefterlevnad med Microsoft Intune
titleSuffix: Microsoft Intune
description: Skapa en Intune-princip för enhetsefterlevnad som använder din MTD-partners hotnivåer för att bestämma om en mobil enhet ska få åtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d1215d463c89dfa3e740099f7582d61359a4669
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044562"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Skapa en princip för Mobile Threat Defense-enhetsefterlevnad med Intune

> [!NOTE] 
> Denna information gäller alla partners för skydd mot mobilhot.

Intune med MTD hjälper dig att identifiera hot och bedöma risker på mobila enheter. Du kan skapa en Intune-principregel för enhetsefterlevnad som bedömer risken och avgör om enheten uppfyller efterlevnadskraven. Du kan sedan använda en [princip för villkorlig åtkomst](create-conditional-access-intune.md) för att blockera åtkomst till tjänster utifrån enhetens efterlevnad.

## <a name="before-you-begin"></a>Innan du börjar

Som en del av MTD-installationen skapade du i MTD-partnerkonsolen en princip som klassificerar olika hot i kategorierna Hög, Medel och Låg. Du måste nu ange MTD-nivå i Intune-principen för enhetsefterlevnad.

Förutsättningar för principen för enhetsefterlevnad med MTD:

-   Ställ in MTD-integrering med Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>Skapa en MTD-enhetsefterlevnadsprincip

1.  Gå till [Azure Portal](https://portal.azure.com/) och logga in med dina Intune-autentiseringsuppgifter.

2.  Välj **Alla tjänster** i den vänstra menyn på **Azure-instrumentpanelen** och skriv sedan **Intune** i textrutefiltret.

3.  Välj **Intune**. **Intune-instrumentpanelen** öppnas.

4. Välj **Enhetsefterlevnad** på **Intunes instrumentpanel** och välj sedan **Principer** under avsnittet **Hantera**.

5.  Välj **Skapa princip**, ange ett **namn** på och en **beskrivning** av principen för enhetsefterlevnad, välj **plattform** och välj sedan **Konfigurera** under avsnittet **Inställningar**.

6.  Välj **Enhetens hälsotillstånd** i fönstret för **efterlevnadsprincip**.

7.  I fönstret **Enhetens hälsotillstånd** väljer du mobilhotnivå i listrutan under **Kräv att enheten ska hållas vid eller under hotnivån för enheten**.

    a.  **Skyddad**: Den här nivån är säkrast. Enheten får inte ha några förekommande hot och ska ha tillgång till företagsresurser. Om något hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.

    b.  **Låg**: Enheten följer standard om det enbart finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.

    c.  **Medel**: Enheten följer standard om hoten som hittas på enheten är låga eller medelhöga. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.

    d.  **Hög**: Det här är den minst säkra nivån. Detta tillåter alla hotnivåer och använder endast Mobile Threat Defense i rapporteringssyfte. Enheterna måste ha MTD-appen aktiverad med den här inställningen.

8.  Klicka på **OK** två gånger och välj sedan **Skapa**.

> [!IMPORTANT]
> Om du skapar principer för villkorlig åtkomst till Office 365 eller andra tjänster kommer utvärderingen av efterlevnad att bedömas och icke-kompatibla enheter kommer inte att få åtkomst till företagsresurser förrän hotet har lösts i enheten.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>Tilldela en MTD-enhetsefterlevnadsprincip

Om du vill tilldela en princip för enhetsefterlevnad till användare, väljer du en princip som du tidigare har konfigurerat. Du hittar befintliga principer i fönstret **Enhetsefterlevnad – Principer**.

1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Åtgärden öppnar ett fönster där du kan välja **Azure Active Directory-säkerhetsgrupper** och tilldela dem till principen.

2. Öppna sidan som visar säkerhetsgrupper för Azure AD genom att välja **Välj grupper att ta med**.  När du väljer **Välj** distribueras principen till användarna.

    > [!NOTE] 
    > Du har tillämpat principen på användarna. Enheterna som används av de användare som principen är inriktad på kommer att utvärderas för att se om de följer standard.

## <a name="next-steps"></a>Nästa steg

- [Aktivera MTD med Intune](mtd-connector-enable.md)
