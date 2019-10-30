---
title: Skapa en Mobile Threat Defense-appskyddsprincip (MTD) med Intune
titleSuffix: Microsoft Intune
description: Skapa en Mobile Threat Defense-appskyddsprincip (MTD) med Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794426"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Skapa en Mobile Threat Defense-appskyddsprincip med Intune

> [!NOTE] 
> Den här artikeln gäller för alla Mobile Threat Defense-partner (MTD) som har stöd för appskyddsprinciper: Better Mobile (Android), Zimperium (iOS) samt Lookout for Work (Android/iOS).

Intune med MTD hjälper dig att identifiera hot och bedöma risker på mobila enheter. Du kan skapa en Intune-appskyddsprincip som bedömer risk för att avgöra huruvida enheten tillåts att få åtkomst till företagsdata. 

## <a name="before-you-begin"></a>Innan du börjar

Som en del av MTD-installationen skapade du i MTD-partnerkonsolen en princip som klassificerar olika hot i kategorierna Hög, Medel och Låg. Du måste nu ange Mobile Threat Defense-nivån i Intune-appskyddsprincipen.

Förutsättningar för appskyddsprincip med MTD:

- Konfigurera MTD-integrering med Intune. Utan den här integrationen har MTD-appskyddsprincipen ingen verkan.

## <a name="to-create-an-mtd-app-protection-policy"></a>Så här skapar du en MTD-appskyddsprincip

1. Gå till [Azure Portal](https://portal.azure.com/) och logga in med dina Intune-autentiseringsuppgifter.

2. Välj **Alla tjänster** i den vänstra menyn på **Azure-instrumentpanelen** och skriv sedan **Intune** i textrutefiltret.

3. Välj **Intune**. **Intune-instrumentpanelen** öppnas.

4. På **Intune-instrumentpanelen** väljer du **Klientappar** och sedan **Appskyddsprinciper** i avsnittet **Hantera**.

5. Välj **Skapa princip**, ange **Namn** och **Beskrivning** och välj önskad **Plattform**. 

6. I fönstret **Villkorsstyrd start** väljer du under tabellen **Enhetstillstånd** Mobile Threat Level i listrutan under **Högsta tillåtna hotnivå för enhet**.

    a.  **Skyddad**: Den här nivån är säkrast. Enheten får inte ha några förekommande hot och ska ha tillgång till företagsresurser. Om något hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.

    b.  **Låg**: Enheten följer standard om det enbart finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.

    c.  **Medel**: Enheten följer standard om hoten som hittas på enheten är låga eller medelhöga. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.

    d.  **Hög**: Det här är den minst säkra nivån. Detta tillåter alla hotnivåer och använder endast Mobile Threat Defense i rapporteringssyfte. Enheterna måste ha MTD-appen aktiverad med den här inställningen.

7. Klicka på **Spara** två gånger och välj sedan **Skapa**.

## <a name="to-assign-an-mtd-app-protection-policy"></a>Så här tilldelar du en MTD-appskyddsprincip

Om du vill tilldela en princip för enhetsefterlevnad till användare, väljer du en princip som du tidigare har konfigurerat. Du hittar befintliga principer i fönstret **Enhetsefterlevnad – Principer**.

1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Åtgärden öppnar ett fönster där du kan välja **Azure Active Directory-säkerhetsgrupper** och tilldela dem till principen.

2. Välj **Välj grupper som ska inkluderas** för att öppna det fönster som visar Azure AD-säkerhetsgrupperna. När du väljer **Välj** distribueras principen till användarna.

> [!NOTE] 
> Du har tillämpat principen på användarna. De enheter som används av de användare som är mål för principen utvärderas för åtkomst till företagsdata i riktade appar via Intune-appskydd.

## <a name="next-steps"></a>Nästa steg  

- Lär dig mer om [Mobile Threat Defense](~/protect/mobile-threat-defense.md) i Microsoft Intune.
