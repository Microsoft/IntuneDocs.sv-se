---
title: Aktivera Lookout MTP i Intune | Microsoft Intune
description: "Aktivera Lookout mobilt skydd i Intune-administratörskonsolen."
keywords: 
author: karthikaraman
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
ms.sourcegitcommit: 1334500471d2aea5e8c58a3219c755bfd9953424
ms.openlocfilehash: 4ae7d6c571f69c0cc51dc15355e50325afb88694


---

# Aktivera Lookout MTP-anslutning i Intune-administratörskonsolen
Det här avsnittet visar hur du aktiverar Lookout MTP-anslutning i Intune. Du borde redan ha konfigurerat Intune Connector i Lookout MTP-konsolen innan du gör det här steget.  Om du inte redan har gjort det, gör stegen som beskrivs i  [Set up your subscription with Lookout mobile threat protection](set-up-your-subscription-with-lookout-mtp.md) (Konfigurera din prenumeration med Lookout mobila skydd).

På sidan **Administration** i [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com), välj **Integrering med tjänst från tredje part** för att aktivera Lookout MTP-anslutningen i Intune. Välj **Status för Lookout** och aktivera **Synkronisering med MTP** med växlingsknappen.

![skärmbild av sidan Lookout-synkronisering med växelknappen för att aktivera markerad](../media/mtp/lookout-intune-synchronization.png)

Nu är du klar med installationen av Lookout och Intune-integration i Intune-administratörskonsolen.  De efterföljande stegen för att implementera den här lösningen består av att distribuera [Lookout for Work apps](configure-and-deploy-lookout-for-work-apps.md) (Lookout for Work-appar) och konfigurera [efterlevnads](enable-device-threat-protection-rule-in-compliance-policy.md)-principen.

>[!IMPORTANT]
> Du **måste** konfigurera Lookout for Work-appen innan du skapar policyn för efterlevnad och konfigurerar villkorlig åtkomst. Detta ser till att appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post eller andra företagsresurser.
## Nästa steg
[Konfigurera Lookout for Work-appen ](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Sep16_HO2-->


