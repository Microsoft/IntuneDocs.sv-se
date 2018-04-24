---
title: Aktivera Skycure Mobile Threat Defense i Intune
description: Aktivera Skycure Mobile Threat Defense i den klassiska Intune-portalen.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: da4197a41798f4e47ff35d2dfab36c5317f92e21
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Aktivera Skycure Mobile Threat Defense i Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Om du vill aktivera Skycures skydd mot mobilhot bör du redan ha konfigurerat [Intune Connector i Skycure-konsolen](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune).

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Så här aktiverar du Skycure MTD-anslutningen i Intune

1.  Gå till den [klassiska Intune-portalen](https://manage.microsoft.com/) och ange sedan dina autentiseringsuppgifter.

2.  Välj **Administratör** &gt; **Integrering med tredjepartstjänst** och välj sedan **Skycure-status**. Aktivera **Synkronisering med MTD** med hjälp av växlingsknappen.

    ![Aktivera Skycure-växling i den klassiska Intune-portalen](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> Du måste konfigurera Skycure-apparna innan du skapar reglerna för efterlevnadsprincipen och konfigurerar villkorlig åtkomst. Detta ser till att appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post eller andra företagsresurser.

Nu är du klar med installationen av Skycure och Intune-integreringen i Intune-administratörskonsolen. De efterföljande stegen för att implementera den här lösningen består i att distribuera Skycure for Work-appar och konfigurera efterlevnadsprincipen.

## <a name="next-steps"></a>Nästa steg

[Skapa efterlevnadsprincip för Skycure Mobile Threat Defense](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
