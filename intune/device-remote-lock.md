---
title: "Fjärrlåsa hanterade enheter med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du använder Intune för att fjärrlåsa enheter som du hanterar.\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a8f3c93507cde4363570a9a39f8b3b1f69c07df
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Fjärrlåsa hanterade enheter med Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med **Fjärrlås** låses den valda enheten. Enhetens ägare måste använda sitt lösenord för att låsa upp den. Du kan endast fjärrlåsa en enhet som har en PIN-kod eller angett lösenord.

## <a name="supported-platforms"></a>Plattformar som stöds

Fjärrlåsning stöds på följande plattformar:

|Plattform|Supportstatus|
|---|---|
|Android|Ja|
|iOS|Ja|
|macOS|Ja|
|Windows 10 desktop|Nej|
|Windows 10 Mobil|Ja|
|Windows Phone|Ja, för Windows Phone 8.1 och senare|

> [!NOTE]  
> För macOS-enheter anger du en 6-siffrig PIN-kod för återställning. När enheten är låst visar bladet **Enhetsöversikt** PIN-koden tills en annan enhetsåtgärd skickas.

## <a name="how-to-remote-lock-a-device"></a>Fjärrlåsa en enhet

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning + hantering**.
3. Välj **Enheter** på bladet **Intune**.
4. Välj **Alla enheter** på bladet **Enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Fjärrlås**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd du precis vidtagit väljer du **Enhetsåtgärder** på bladet **Enheter**.
