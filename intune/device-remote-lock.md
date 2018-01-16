---
title: "Fjärrlåsa hanterade enheter med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du använder Intune för att fjärrlåsa enheter som du hanterar.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45d27b709ba8d4ff1d8fb4417a217ad008c19c36
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/12/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Fjärrlåsa hanterade enheter med Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med **Fjärrlås** låses den valda enheten. Enhetens ägare måste använda sitt lösenord för att låsa upp den. Du kan endast fjärrlåsa en enhet som har en PIN-kod eller angett lösenord.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds på Windows Phone 8.1 och senare
- iOS – stöds
- macOS – stöds

    > [!Note]  
    > Ange en PIN-kod för återställning på 6 siffror. När enheten är låst visar bladet **Enhetsöversikt** PIN-koden tills en annan enhetsåtgärd skickas.
- Android – stöds

## <a name="how-to-remote-lock-a-device"></a>Fjärrlåsa en enhet

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Fjärrlås**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
