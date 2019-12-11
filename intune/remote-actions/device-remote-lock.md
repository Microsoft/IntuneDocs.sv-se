---
title: Låsa enheter med Microsoft Intune – Azure | Microsoft Docs
description: Använd åtgärden för fjärrlåsning i Microsoft Intune för att låsa en enhet som skyddas av en PIN-kod eller ett lösenord.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bce5a89ecc49952f5c21536c429e9cd3309b13c3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712271"
---
# <a name="remotely-lock-devices-with-intune"></a>Fjärrlåsa enheter med Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Åtgärden **Fjärrlås** låser enheten. Enhetens ägare måste ange sitt lösenord för att låsa upp den. Du kan fjärrlåsa enheter som har en PIN-kod eller ett lösenord. Enheter som saknar PIN-kod eller lösenord går inte att fjärrlåsa.

## <a name="supported-platforms"></a>Plattformar som stöds

**Fjärrlås** stöds på följande plattformar:

- Android
- Android enterprise-kioskenheter
- Android enterprise-arbetsprofilenheter
- iOS
- macOS
- Windows 10 Mobil
- Windows Phone 8.1 och senare

**Fjärrlås** stöds inte för:
- Windows 10 desktop

> [!NOTE]
> För macOS-enheter anger du en 6-siffrig PIN-kod för återställning. När enheten är låst visar **Enhetsöversikt** PIN-koden tills en annan enhetsåtgärd skickas.

## <a name="remote-lock-a-device"></a>Fjärrlås på en enhet

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Välj **Enheter** > **Alla enheter**.
4. Välj en enhet i listan över enheter och välj sedan åtgärden **Fjärrlås**.

## <a name="next-steps"></a>Nästa steg

- Om du vill se status för den här åtgärden väljer du **Microsoft Intune** > **Enheter** > **Enhetsåtgärder**. 
- Se [Tillgängliga åtgärder](device-management.md) för fler åtgärder som kan hjälpa dig att hantera enheter.
