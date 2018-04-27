---
title: Låsa enheter med Microsoft Intune – Azure | Microsoft Docs
description: Använd åtgärden för fjärrlåsning i Microsoft Intune för att låsa en enhet som skyddas av en PIN-kod eller ett lösenord.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45ab6434245c0dd412b2e9d23e394f72871a459a
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="remotely-lock-devices-with-intune"></a>Fjärrlåsa enheter med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Åtgärden **Fjärrlås** låser enheten. Enhetens ägare måste ange sitt lösenord för att låsa upp den. Du kan fjärrlåsa enheter som har en PIN-kod eller ett lösenord. Enheter som saknar PIN-kod eller lösenord går inte att fjärrlåsa.

## <a name="supported-platforms"></a>Plattformar som stöds

**Fjärrlås** stöds på följande plattformar:

- Android
- iOS
- macOS
- Windows 10 Mobil
- Windows Phone 8.1 och senare

**Fjärrlås** stöds *inte* för:
- Windows 10 desktop

> [!NOTE]
> För macOS-enheter anger du en 6-siffrig PIN-kod för återställning. När enheten är låst visar **Enhetsöversikt** PIN-koden tills en annan enhetsåtgärd skickas.

## <a name="remote-lock-a-device"></a>Fjärrlås på en enhet

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj sedan **Microsoft Intune**.
3. Välj **Enheter** > **Alla enheter**.
4. Välj en enhet i listan över enheter och välj sedan åtgärden **Fjärrlås**.

## <a name="next-steps"></a>Nästa steg

- Om du vill se status för den här åtgärden väljer du **Microsoft Intune** > **Enheter** > **Enhetsåtgärder**. 
- Se [Tillgängliga åtgärder](device-management.md) för fler åtgärder som kan hjälpa dig att hantera enheter.
