---
title: "Övervaka appdistributioner | Microsoft Docs"
description: "Läs om hur du övervakar appar som du har distribuerat med Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5daad56d-71c8-455b-8a55-f8b33e279a8a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: ee0d10f9b86b1122d0f16568b71b087c341e88df
ms.lasthandoff: 12/10/2016


---


# <a name="monitor-app-deployments-in-microsoft-intune"></a>Övervaka appdistributioner i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="monitor-an-app-deployment"></a>Övervaka en appdistribution
Du kan se de appar som du hanterar och status för distributioner i Intune-administratörskonsolen. <!---App status is displayed in real-time. You don't have to wait for the device to check-in before you can see this.--->

### <a name="to-view-apps-that-you-manage-and-their-status"></a>Visa de appar som du hanterar och deras status
Välj noden **Appar** på arbetsytan **Appar** och välj sedan **Appar**.

Listan med appar som du hanterar visas. När du väljer en app visas installationsstatus i rutan längst ned i konsolfönstret. Välj denna status för att se ytterligare information. Om statusen exempelvis visar **1 användare har tillgång till programvaran** kan du välja meddelandet för att se användarens namn.

> [!TIP]
> Du kan använda listrutan **Filter** för att endast visa appar som uppfyller de kriterier du anger, t.ex. appar som inte installerades eller appar som har distribuerats.
>
> ![Exempel på appfilter](./media/app-filters.png)

Dessutom visar arbetsytan **Instrumentpanel** en översikt över apparnas status. Om du klickar någonstans i översikten vidarebefordras du till listan över appar.

## <a name="to-view-more-detailed-information-about-an-app"></a>Visa mer detaljerad information om en app
Välj en app i listan över appar och välj sedan **Visa egenskaper**.

På sidan **Programvaruegenskaper** för appen väljer du någon av dessa flikar: **Allmänt** (visar allmän information om appen och dess installationsstatus), **Enheter** (visar de enheter som har installerat en riktad distribution av appen) och **Användare** (visar de användare vars enheter har installerat en riktad distribution av appen).

Som tidigare kan du använda listrutan **Filter** för att konfigurera de värden som visas på var och en av flikarna.
