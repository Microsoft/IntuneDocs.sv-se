---
title: Inställningar för Windows informationsskydd i Microsoft Intune
titleSuffix: ''
description: Lär dig mer om Microsoft Intune-inställningar som du kan använda för att hantera Windows informationsskydd.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 1/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5bb668c3c9dd1325a34a71c7a61b2efab8e52feb
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231157"
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Hur du konfigurerar inställningar för Windows informationsskydd i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Allt fler anställda använder egna enheter i företaget. Detta innebär en ökad risk för oavsiktliga dataläckage via appar och tjänster, till exempel e-post, sociala media och offentliga moln, som företaget inte har någon kontroll över. En medarbetare kan till exempel skicka de senaste ritningarna via sitt personliga e-postkonto, kopiera och klistra in produktinformation i en tweet eller spara en försäljningsrapport på en offentlig molnlagringsplats.

**Windows informationsskydd** bidrar till att skydda mot potentiella dataläckage utan att störa användarupplevelsen för de anställda. Informationsskyddet skyddar även företagsappar och företagsdata mot oavsiktliga dataläckage i företagsägda enheter och personliga enheter som medarbetarna tar med sig till jobbet utan att det behövs några ändringar i miljön eller andra appar.

Den här Intune-principen hanterar listan över appar som skyddas av Windows informationsskydd, företagsnätverksplatser, skyddsnivå och krypteringsinställningar.

>[!NOTE]
> Om du vill använda företagsportalappen för Windows 10 med Windows informationsskydd, måste du lägga till företagsportalappen i Windows informationsskyddsläget som **Undantag**. 

### <a name="next-steps"></a>Nästa steg
Mer information finns i:
-  [Skydda företagsdata med hjälp av Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
- [Skapa en princip för Windows Information Protection (WIP) med den klassiska konsolen för Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune)
- [Skapa en princip för Windows Information Protection (WIP) med MDM med hjälp av Azure Portal för Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune-azure)
- [Skapa en princip för Windows Information Protection (WIP) med MAM med hjälp av Azure Portal för Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure)
