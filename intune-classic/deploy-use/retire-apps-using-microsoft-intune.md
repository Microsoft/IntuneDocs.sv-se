---
title: Dra tillbaka appar | Microsoft Docs
description: "Läs om hur du återställer eller avinstallerar appar med Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: d0c24549c4805da87c74247253905a96d6290969
ms.lasthandoff: 12/30/2016


---

# <a name="retire-apps-using-microsoft-intune"></a>Ta bort appar med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Om du vill dra tillbaka en app avinstallerar du den bara. När du distribuerar och hanterar appar med Intune ser processen för att avinstallera appen likadan ut för både mobila enheter och Windows-datorer. Appen måste ha stöd för avinstallationsprocessen för att den här proceduren ska lyckas.

## <a name="uninstall-an-app"></a>Avinstallera en app

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Appar** &gt; **Appar**.

2.  Markera den app som du vill avinstallera (en app som du har distribuerat tidigare) och klicka sedan på **Hantera distribution**.

3.  På sidan **Distributionsåtgärd** väljer du **Avinstallera** i kolumnen **Godkännande** :

När enheten eller datorn söker efter  appar nästa gång avinstalleras appen.

### <a name="see-also"></a>Se även
[Lägga till appar i Microsoft Intune](add-apps.md)

