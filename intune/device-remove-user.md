---
title: Ta bort en användare från en iOS-enhet med Microsoft Intune
titleSuffix: ''
description: Läs om hur du tar bort en användare från en delad iOS-enhet med Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53c4e02f32fa421c745f5bfa15e97023f47ece88
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568589"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Ta bort en användare från en delad iOS-enhet


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Med åtgärden **Ta bort användare** tar du bort en vald användare från den lokala cachen på en delad iPad-enhet. iPad-enheten måste konfigureras för att hantera iOS-klassrumsappen med hjälp av en [iOS-utbildningsprofil](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS – stöds på iOS 9.3 och senare (endast delade iPad-enheter)
- macOS – stöds inte
- Android – stöds inte

## <a name="remove-a-user"></a>Ta bort en användare

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enheter** i **Intune**-fönstret.
4. Välj **Alla enheter** i fönstret **Enheter**.
5. Välj en iOS-enhet i listan över de enheter du hanterar.
6. Välj **Användare** i fönstret för enheten.
7. Högerklicka på den användare du vill ta bort i listan och välj sedan **Ta bort användare**.

## <a name="next-steps"></a>Nästa steg

- Om du vill se status för åtgärden **Ta bort användare** väljer du **Enheter** > **Enhetsåtgärder**.
