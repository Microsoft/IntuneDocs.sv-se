---
title: Aktivera Skycure Mobile Threat Defense i Intune
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
ms.openlocfilehash: 4dad45d15fec7189fdcf184839040b9e3f9a3a48
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Aktivera Skycure Mobile Threat Defense i Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Om du vill aktivera Skycure Mobile Threat Defense så ska du redan ha konfigurerat [Intune-anslutningsappen i Skycure-konsolen] (/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune).

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Så här aktiverar du Skycure MTD-anslutningen i Intune

1.  Gå till den [klassiska Intune-konsolen](https://manage.microsoft.com/) och ange sedan dina autentiseringsuppgifter.

2.  Välj **Administratör** &gt; **Integrering med tredjepartstjänst** och välj sedan **Skycure-status**. Aktivera **Synkronisering med MTD** med hjälp av växlingsknappen.

    ![Aktivera Skycure-växling i den klassiska Intune-konsolen](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> Du måste konfigurera Skycure-apparna innan du skapar reglerna för efterlevnadsprincipen och konfigurerar villkorlig åtkomst. Detta ser till att appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post eller andra företagsresurser.

Nu är du klar med installationen av Skycure och Intune-integreringen i Intune-administratörskonsolen. De efterföljande stegen för att implementera den här lösningen består i att distribuera Skycure for Work-appar och konfigurera efterlevnadsprincipen.

## <a name="next-steps"></a>Nästa steg

[Skapa efterlevnadsprincip för Skycure Mobile Threat Defense](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
