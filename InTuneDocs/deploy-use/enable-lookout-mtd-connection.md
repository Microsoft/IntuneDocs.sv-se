---
title: Aktivera Lookout MTP i Intune | Microsoft Docs
description: "Aktivera Lookout mobilt skydd i Intune-administratörskonsolen."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d42fa20a3bc6b6f4a74dd0872aae25cfb33067b9
ms.openlocfilehash: d2a10a0e14d9b0b4d2e3f8e2715b47d984e5aa66
ms.lasthandoff: 03/21/2017


---

# <a name="enable-lookout-mtd-connection-in-the-intune-classic-console"></a>Aktivera Lookout MTD-anslutningen i den klassiska Intune-konsolen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Om du vill aktivera Lookout MTD-anslutningen i Intune måste du redan ha konfigurerat Intune Connector i Lookout-konsolen.  Om du inte redan har gjort det bör du [Konfigurera din Lookout Mobile Threat Defense-prenumeration](set-up-your-subscription-with-lookout-mtp.md).

På sidan **Administration** i [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com), välj **Integrering med tjänst från tredje part** för att aktivera Lookout MTP-anslutningen i Intune. Välj **Status för Lookout** och aktivera **Synkronisering med MTP** med växlingsknappen.

![skärmbild av sidan Lookout-synkronisering med växelknappen för att aktivera markerad](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> Du **måste** konfigurera Lookout for Work-appen innan du skapar policyn för efterlevnad och konfigurerar villkorlig åtkomst. Detta ser till att appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post eller andra företagsresurser.

Nu är du klar med installationen av Lookout och Intune-integration i Intune-administratörskonsolen.  De efterföljande stegen för att implementera den här lösningen består av att distribuera [Lookout for Work apps](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-apps) (Lookout for Work-appar) och konfigurera [efterlevnads](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-policy)-principen.


## <a name="next-steps"></a>Nästa steg
[Konfigurera Lookout for Work-appen](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-apps)

