---
title: Logga ut användaren av en iOS-enhet
titlesuffix: Microsoft Intune
description: Lär dig hur du kan logga ut den aktuella användaren av en iOS-enhet med Intune."
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 24b59e5b60f2a8dce0522c689463ac095617052c
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185669"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Logga ut den aktuella användaren på Intune-hanterade iOS-enheter


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Åtgärden **Logga ut aktuell användare** loggar ut den aktuella användaren på en delad iPad-enhet. 

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS – stöds på iOS 9.3 och senare (endast delade iPad-enheter)
- macOS – stöds inte
- Android – stöds inte

## <a name="how-to-log-out-the-current-user"></a>Så här loggar du ut den aktuella användaren

1.  Logga in på Azure-portalen.
2.  Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3.  Välj **Enheter** på bladet **Intune**.
4.  På bladet **Enheter och grupper** väljer du **Alla enheter**.
5.  Välj en iOS-enhet i listan med de enheter du hanterar och välj sedan fjärråtgärden **Logga ut aktuell användare**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
