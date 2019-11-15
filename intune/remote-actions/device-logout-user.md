---
title: Logga ut användaren av en iOS-enhet
titleSuffix: Microsoft Intune
description: Lär dig hur du kan logga ut den aktuella användaren av en iOS-enhet med Intune."
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fdb23916319b06fb4d85b913209d1ac9e007d551
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713167"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Logga ut den aktuella användaren på Intune-hanterade iOS-enheter


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Åtgärden **Logga ut aktuell användare** loggar ut den aktuella användaren på en delad iPad-enhet. 

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS – stöds på iOS 9.3 och senare (endast delade iPad-enheter)
- macOS – stöds inte
- Android – stöds inte

## <a name="how-to-log-out-the-current-user"></a>Så här loggar du ut den aktuella användaren

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Enheter**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. Välj en iOS-enhet i listan med de enheter du hanterar och välj sedan fjärråtgärden **Logga ut aktuell användare**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
