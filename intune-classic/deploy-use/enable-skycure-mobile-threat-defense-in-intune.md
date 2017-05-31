---
title: Aktivera Skycure Mobile Threat Defense i Intune | Microsoft Docs
description: Aktivera Skycure Mobile Threat Defense i den klassiska Intune-konsolen.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 9be25144ce8c556e890668979e674dd56370f8cd
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Aktivera Skycure Mobile Threat Defense i Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Aktivera Skycure Mobile Threat Defense /intune-classic/deploy-use/setup-the-skycure-integration-with-Intune).

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Så här aktiverar du Skycure MTD-anslutningen i Intune

1.  Gå till den [klassiska Intune-konsolen](https://manage.microsoft.com/) och ange sedan dina autentiseringsuppgifter.

2.  Välj **Administratör** &gt; **Integrering med tredjepartstjänst** och välj sedan **Skycure-status**. Aktivera **Synkronisering med MTD** med hjälp av växlingsknappen.

    ![Aktivera Skycure-växling i den klassiska Intune-konsolen](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> Du måste konfigurera Skycure-apparna innan du skapar reglerna för efterlevnadsprincipen och konfigurerar villkorlig åtkomst. Detta ser till att appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post eller andra företagsresurser.

Nu är du klar med installationen av Skycure och Intune-integreringen i Intune-administratörskonsolen. De efterföljande stegen för att implementera den här lösningen består i att distribuera Skycure for Work-appar och konfigurera efterlevnadsprincipen.

## <a name="next-steps"></a>Nästa steg

[Skapa efterlevnadsprincip för Skycure Mobile Threat Defense](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)

