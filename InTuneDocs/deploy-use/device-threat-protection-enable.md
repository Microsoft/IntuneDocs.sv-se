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
ms.sourcegitcommit: 53862e49c922b75b414fd5aceec3bba2b10299a6
ms.openlocfilehash: 1297522d0f7b52ebe14eb7b938f3458e7308ae27


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Aktivera Lookout MTP-anslutning i Intune-administratörskonsolen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Om du vill aktivera Lookout MTP-anslutning (malicious threat protection) i Intune bör du redan ha konfigurerat Intune Connector i Lookout-konsolen.  Om du inte redan har gjort det bör du [Konfigurera din prenumeration med Lookout mobilt skydd](set-up-your-subscription-with-lookout-mtp.md).

På sidan **Administration** i [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com), välj **Integrering med tjänst från tredje part** för att aktivera Lookout MTP-anslutningen i Intune. Välj **Status för Lookout** och aktivera **Synkronisering med MTP** med växlingsknappen.

![skärmbild av sidan Lookout-synkronisering med växelknappen för att aktivera markerad](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> Du **måste** konfigurera Lookout for Work-appen innan du skapar policyn för efterlevnad och konfigurerar villkorlig åtkomst. Detta ser till att appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post eller andra företagsresurser.

Nu är du klar med installationen av Lookout och Intune-integration i Intune-administratörskonsolen.  De efterföljande stegen för att implementera den här lösningen består av att distribuera [Lookout for Work apps](configure-and-deploy-lookout-for-work-apps.md) (Lookout for Work-appar) och konfigurera [efterlevnads](enable-device-threat-protection-rule-in-compliance-policy.md)-principen.


## <a name="next-steps"></a>Nästa steg
[Konfigurera Lookout for Work-appen](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Jan17_HO2-->


