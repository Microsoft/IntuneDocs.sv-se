---
title: "Logga ut användaren av en iOS-enhet med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du kan logga ut den aktuella användaren av en iOS-enhet med Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 07/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 839815417a6b7ad54ea974fac3e885a0cd862fc8
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Logga ut den aktuella användaren på Intune-hanterade iOS-enheter


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Åtgärden **Logga ut aktuell användare** loggar ut den aktuella användaren på en delad iPad-enhet som har konfigurerats för hantering av Classroom-appen för iOS med en [utbildningsprofil för iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS – stöds på iOS 9.3 och senare (endast delade iPad-enheter)
- macOS – stöds inte
- Android – stöds inte

## <a name="how-to-logout-the-current-user"></a>Logga ut den aktuella användaren

1.  Logga in på Azure-portalen.
2.  Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3.  Välj **Enheter** på bladet **Intune**.
4.  På bladet **Enheter och grupper** väljer du **Alla enheter**.
5.  Välj en iOS-enhet i listan med de enheter du hanterar och välj sedan fjärråtgärden **Logga ut aktuell användare**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
