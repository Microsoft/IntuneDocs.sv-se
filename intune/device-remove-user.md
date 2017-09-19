---
title: "Ta bort en användare från en iOS-enhet med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du tar bort en användare från en delad iOS-enhet med Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f16d42406fa7961cc165adcbd1e7c4c7ab5d78b4
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="remove-a-user-from-a-shared-ios-device-with-intune"></a>Ta bort en användare från en delad iOS-enhet med Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Åtgärden **Ta bort användare** tar bort den aktuella användaren på en delad iPad-enhet som har konfigurerats för hantering av Classroom-appen för iOS med hjälp av en [utbildningsprofil för iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS – stöds på iOS 9.3 och senare (endast delade iPad-enheter)
- macOS – stöds inte
- Android – stöds inte

## <a name="how-to-remove-a-user"></a>Ta bort en användare

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. Välj **Alla enheter** på bladet **Enheter**.
5. Välj en iOS-enhet i listan över de enheter du hanterar.
6. Välj **Användare** på bladet för den enheten.
7. Högerklicka på den användare du vill ta bort i listan och välj sedan **Ta bort användare**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
