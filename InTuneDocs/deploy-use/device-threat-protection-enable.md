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
ms.sourcegitcommit: 6f687a1db84b49bc173d2067ab95598b4485daa8
ms.openlocfilehash: 618819ff8dded925bc4745160dde8c9e75694faf


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Aktivera Lookout MTP-anslutning i Intune-administratörskonsolen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Om du vill aktivera Lookout MTP-anslutning (malicious threat protection) i Intune bör du redan ha konfigurerat Intune Connector i Lookout-konsolen.  Om du inte redan har gjort det bör du [Konfigurera din prenumeration med Lookout mobilt skydd](set-up-your-subscription-with-lookout-mtp.md).

På sidan **Administration** i [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com), välj **Integrering med tjänst från tredje part** för att aktivera Lookout MTP-anslutningen i Intune. Välj **Status för Lookout** och aktivera **Synkronisering med MTP** med växlingsknappen.

![skärmbild av sidan Lookout-synkronisering med växelknappen för att aktivera markerad](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> Du **måste** konfigurera Lookout for Work-appen innan du skapar policyn för efterlevnad och konfigurerar villkorlig åtkomst. Detta ser till att appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post eller andra företagsresurser.

Nu är du klar med installationen av Lookout och Intune-integration i Intune-administratörskonsolen.  De efterföljande stegen för att implementera den här lösningen består av att distribuera [Lookout for Work apps](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-apps) (Lookout for Work-appar) och konfigurera [efterlevnads](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-policy)-principen.


## <a name="next-steps"></a>Nästa steg
[Konfigurera Lookout for Work-appen](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-apps)



<!--HONumber=Feb17_HO4-->


