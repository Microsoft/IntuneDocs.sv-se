---
title: "Ta bort en användare från en iOS-enhet med Microsoft Intune"
titlesuffix: 
description: "Läs om hur du tar bort en användare från en delad iOS-enhet med Intune."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce1b6b439c287b67a7c9e776edf136e78e5ecf5b
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Ta bort en användare från en delad iOS-enhet


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Åtgärden **Ta bort användare** tar bort den aktuella användaren på en delad iPad-enhet som har konfigurerats för hantering av Classroom-appen för iOS med hjälp av en [utbildningsprofil för iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS – stöds på iOS 9.3 och senare (endast delade iPad-enheter)
- macOS – stöds inte
- Android – stöds inte

## <a name="how-to-remove-a-user"></a>Ta bort en användare

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enheter** på bladet **Intune**.
4. Välj **Alla enheter** på bladet **Enheter**.
5. Välj en iOS-enhet i listan över de enheter du hanterar.
6. Välj **Användare** på bladet för den enheten.
7. Högerklicka på den användare du vill ta bort i listan och välj sedan **Ta bort användare**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd du precis vidtagit väljer du **Enhetsåtgärder** på bladet **Enheter**.
