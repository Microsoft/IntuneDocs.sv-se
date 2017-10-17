---
title: Aktivera Lookout MTP i Intune
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
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f34697140a287d41203d1bad5df59250f07d08ce
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="enable-lookout-mtd-connection-in-the-intune-classic-portal"></a>Aktivera Lookout MTD-anslutningen i den klassiska Intune-portalen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Om du vill aktivera Lookout MTD-anslutningen i Intune måste du redan ha konfigurerat Intune Connector i Lookout-konsolen.  Om du inte redan har gjort det bör du [Konfigurera din Lookout Mobile Threat Defense-prenumeration](setup-your-lookout-mtd-subscription.md).

På sidan **Administration** i [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com), välj **Integrering med tjänst från tredje part** för att aktivera Lookout MTP-anslutningen i Intune. Välj **Status för Lookout** och aktivera **Synkronisering med MTP** med växlingsknappen.

![skärmbild av sidan Lookout-synkronisering med växelknappen för att aktivera markerad](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> Du **måste** konfigurera Lookout for Work-appen innan du skapar policyn för efterlevnad och konfigurerar villkorlig åtkomst. Detta ser till att appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post eller andra företagsresurser.

Nu är du klar med installationen av Lookout och Intune-integration i Intune-administratörskonsolen.  I de få återstående stegen för att implementera lösningen ska du distribuera principen [Lookout for Works-apparna](/intune-classic/deploy-use/device-threat-protection-policy).


## <a name="next-steps"></a>Nästa steg
[Konfigurera Lookout for Work-appen](/intune-classic/deploy-use/device-threat-protection-apps)
