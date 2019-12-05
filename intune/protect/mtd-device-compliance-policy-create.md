---
title: Skapa en princip för MTD-enhetsefterlevnad med Microsoft Intune
titleSuffix: Microsoft Intune
description: Skapa en Intune-princip för enhetsefterlevnad som använder din MTD-partners hotnivåer för att bestämma om en mobil enhet ska få åtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 504c77fb56918cf97312e70f50b38356f9f7efef
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409704"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Skapa en princip för Mobile Threat Defense-enhetsefterlevnad med Intune

Intune med MTD hjälper dig att identifiera hot och bedöma risker på mobila enheter. Du kan skapa en Intune-principregel för enhetsefterlevnad som bedömer risken och avgör om enheten uppfyller efterlevnadskraven. Du kan sedan använda en [princip för villkorlig åtkomst](create-conditional-access-intune.md) för att blockera åtkomst till tjänster utifrån enhetens efterlevnad.

> [!NOTE]
> Denna information gäller alla partners för skydd mot mobilhot.

## <a name="before-you-begin"></a>Innan du börjar

Som en del av MTD-installationen skapade du i MTD-partnerkonsolen en princip som klassificerar olika hot i kategorierna Hög, Medel och Låg. Du måste nu ange MTD-nivå i Intune-principen för enhetsefterlevnad.

Förutsättningar för principen för enhetsefterlevnad med MTD:

- Ställ in MTD-integrering med Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>Skapa en MTD-enhetsefterlevnadsprincip

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enhet** > **Efterlevnadsprinciper** > **Skapa princip**.

3. Ange en efterlevnadsprincip för enheter i **Namn**, **Beskrivning**, välj **Plattform**, **Konfigurera** under avsnittet **Inställningar**.

4. Välj **Enhetens hälsotillstånd** i fönstret för **efterlevnadsprincip**.

5. I fönstret **Enhetens hälsotillstånd** väljer du mobilhotnivå i listrutan under **Kräv att enheten ska hållas vid eller under hotnivån för enheten**.

   - **Skyddad**: Den här nivån är säkrast. Enheten får inte ha några förekommande hot och ska ha tillgång till företagsresurser. Om något hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.

   - **Låg**: Enheten följer standard om det enbart finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.

   - **Medel**: Enheten följer standard om hoten som hittas på enheten är låga eller medelhöga. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.

   - **Hög**: Det här är den minst säkra nivån. Detta tillåter alla hotnivåer och använder endast Mobile Threat Defense i rapporteringssyfte. Enheterna måste ha MTD-appen aktiverad med den här inställningen.

6. Välj **OK** två gånger och sedan **Skapa** för att skapa principen.

> [!IMPORTANT]
> Om du skapar principer för villkorlig åtkomst till Office 365 eller andra tjänster kommer utvärderingen av efterlevnad att bedömas och icke-kompatibla enheter kommer inte att få åtkomst till företagsresurser förrän hotet har lösts i enheten.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>Tilldela en MTD-enhetsefterlevnadsprincip

Tilldela en efterlevnadsprincip för enheter till användare:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enhet** > **Efterlevnadsprinciper**.

3. Välj den princip som du vill tilldela till användarna och välj sedan **Tilldelningar**. Använd de tillgängliga alternativen för att *inkludera* och *exkludera* grupper som ska ta emot principen.  

4. Välj Spara för att slutföra tilldelningen. När du sparar tilldelningen, distribueras principen till de valda användarna och efterlevnaden utvärderas i deras enheter.

## <a name="next-steps"></a>Nästa steg

[Aktivera MTD med Intune](mtd-connector-enable.md)
