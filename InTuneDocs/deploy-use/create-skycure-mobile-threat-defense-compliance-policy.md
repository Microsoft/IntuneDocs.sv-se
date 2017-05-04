---
title: "Skapa efterlevnadsprincip för Skycure Mobile Threat Defense | Microsoft Docs"
description: "Skapa efterlevnadsprincip för Skycure Mobile Threat Defense i den klassiska Intune-konsolen."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 56ff1728-1119-4e8a-aae6-ed5c7fafa052
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: c28ba63136c1037c8c8191e9a7f46fa9a4823b4e
ms.lasthandoff: 04/25/2017


---

# <a name="create-skycure-mobile-threat-defense-compliance-policy"></a>Skapa efterlevnadsprincip för Skycure Mobile Threat Defense

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Tack vare Intune med Skycure Mobile Threat Defense kan du identifiera hot på mobila enheter och utvärdera risken på dessa enheter. Du kan skapa en Intune-regel för efterlevnadsprinciper som bedömer risken och avgör om enheten är kompatibel. Du kan sedan använda den villkorliga åtkomstprincipen för att blockera åtkomst till tjänster utifrån enhetens efterlevnad.

## <a name="before-you-begin"></a>Innan du börjar

Krav för efterlevnadsprincip med Skycures enhetsskydd:

-   [Konfigurera Skycure-integrering med Intune](https://docs.microsoft.com/intune/deploy-use/setup-the-skycure-integration-with-Intune)

-   [Aktivera anslutning till Skycure i Intune](https://docs.microsoft.com/intune/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

Som en del av installationen av Skycure Mobile Threat Defense har du skapat en princip i Skycure-konsolen som klassificerar olika hot som hög, medel och låg. Du måste nu ange den maximalt tillåtna hotnivån i Intunes efterlevnadsprincip.

## <a name="to-create-skycure-compliance-policy"></a>Så här skapar du en efterlevnadsprincip i Skycure

1.  Gå till den [klassiska Intune-konsolen](https://manage.microsoft.com/) och ange sedan dina autentiseringsuppgifter.

2.  Välj **Princip** &gt; **Efterlevnadsprinciper**. Du kan antingen använda en befintlig efterlevnadsprincip eller skapa en ny.

3.  Välj **Lägg till** &gt; **Enhetens hälsotillstånd** och aktivera sedan **Enhetsskydd**.

4.  Välj **Högsta tillåtna hotnivå**:

    a.  **Ingen (skyddad)**: Det här är det säkraste alternativet. Enheten får inte ha några förekommande hot och ska ha tillgång till företagsresurser. Om något hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.

    b.  **Låg**: Enheten är kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.

    c.  **Medel**: Enheten är kompatibel om hoten som hittas på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.

    d.  **Hög**: Det här alternativet är minst säkert. Detta tillåter alla hotnivåer och använder endast Skycure Mobile Threat Defense för rapportering.

> [!IMPORTANT]
> Om du skapar principer för villkorlig åtkomst till Office 365 eller andra tjänster kommer denna utvärdering av efterlevnad att bedömas och icke-kompatibla enheter kommer inte att få åtkomst till dessa tjänster förrän hotet har lösts.

## <a name="span-idmonitor-device-threats-classanchorspan-idnext-steps-classanchorspan-idtoc477360344-classanchorspanspanspannext-steps"></a><span id="monitor-device-threats" class="anchor"><span id="next-steps" class="anchor"><span id="_Toc477360344" class="anchor"></span></span></span>Nästa steg

-   Skapa en princip för villkorlig åtkomst för:

    -   [Exchange Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
    -   [Exchange On-premises](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
    -   [SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)
    -   [Skype för företag – Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)
    -   [Dynamics CRM](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

