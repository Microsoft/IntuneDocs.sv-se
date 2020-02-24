---
title: Logga ut användaren från en iOS/iPadOS-enhet
titleSuffix: Microsoft Intune
description: Lär dig hur du kan logga ut den aktuella användaren från en iOS/iPadOS-enhet med Intune."
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
ms.openlocfilehash: 6e23f95d169a95244abc8669eb9a19150cff8138
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413696"
---
# <a name="logout-the-current-user-on-intune-managed-iosipados-devices"></a>Logga ut den aktuella användaren från Intune-hanterade iOS/iPadOS-enheter


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Åtgärden **Logga ut aktuell användare** loggar ut den aktuella användaren på en delad iPad-enhet. 

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS/iPadOS – stöds på iOS/iPadOS 9.3 och senare (endast delade iPad-enheter)
- macOS – stöds inte
- Android – stöds inte

## <a name="how-to-log-out-the-current-user"></a>Så här loggar du ut den aktuella användaren

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Enheter**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. Välj en iOS/iPadOS-enhet i listan med de enheter du hanterar och välj sedan fjärråtgärden **Logga ut aktuell användare**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
