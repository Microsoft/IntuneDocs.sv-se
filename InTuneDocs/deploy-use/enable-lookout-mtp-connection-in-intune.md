---
title: Aktivera Lookout MTP i Intune | Microsoft Intune
description: "Aktivera Lookout mobilt skydd i Intune-administratörskonsolen."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 1bef6c15387309e1b36bc85758ca699acd54fdd0


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Aktivera Lookout MTP-anslutning i Intune-administratörskonsolen
Det här avsnittet visar hur du aktiverar Lookout MTP-anslutning i Intune. Du borde redan ha konfigurerat Intune Connector i Lookout-konsolen innan du utför det här steget.  Om du inte redan har gjort det, gör stegen som beskrivs i  [Set up your subscription with Lookout mobile threat protection](set-up-your-subscription-with-lookout-mtp.md) (Konfigurera din prenumeration med Lookout mobila skydd).

På sidan **Administration** i [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com), välj **Integrering med tjänst från tredje part** för att aktivera Lookout MTP-anslutningen i Intune. Välj **Status för Lookout** och aktivera **Synkronisering med MTP** med växlingsknappen.

![skärmbild av sidan Lookout-synkronisering med växelknappen för att aktivera markerad](../media/mtp/lookout-intune-synchronization.png)

Nu är du klar med installationen av Lookout och Intune-integration i Intune-administratörskonsolen.  De efterföljande stegen för att implementera den här lösningen består av att distribuera [Lookout for Work apps](configure-and-deploy-lookout-for-work-apps.md) (Lookout for Work-appar) och konfigurera [efterlevnads](enable-device-threat-protection-rule-in-compliance-policy.md)-principen.

>[!IMPORTANT]
> Du **måste** konfigurera Lookout for Work-appen innan du skapar policyn för efterlevnad och konfigurerar villkorlig åtkomst. Detta ser till att appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post eller andra företagsresurser.
## <a name="next-steps"></a>Nästa steg
[Konfigurera Lookout for Work-appen](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Dec16_HO2-->


