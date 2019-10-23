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
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 030d455c366a9c447444c247e9690e5d31613982
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508605"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Ta bort en användare från en delad iOS-enhet


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Med åtgärden **Ta bort användare** tar du bort en vald användare från den lokala cachen på en delad iPad-enhet. iPad-enheten måste konfigureras för att hantera iOS-klassrumsappen med hjälp av en [iOS-utbildningsprofil](../fundamentals/education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS – stöds på iOS 9.3 och senare (endast delade iPad-enheter)
- macOS – stöds inte
- Android – stöds inte

## <a name="remove-a-user"></a>Ta bort en användare

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Enheter** i **Intune**-fönstret.
4. Välj **Alla enheter** i fönstret **Enheter**.
5. Välj en iOS-enhet i listan över de enheter du hanterar.
6. Välj **Användare** i fönstret för enheten.
7. Högerklicka på den användare du vill ta bort i listan och välj sedan **Ta bort användare**.

## <a name="next-steps"></a>Nästa steg

- Om du vill se status för åtgärden **Ta bort användare** väljer du **Enheter** > **Enhetsåtgärder**.
