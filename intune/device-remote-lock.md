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
ms.openlocfilehash: ecd7fa03b35e91b5a77906858fb251348796704d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
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
|Windows 10|Ja|
|Windows 10 Mobil|Ja|
|Windows Phone|Ja, för Windows Phone 8.1 och senare|

> [!NOTE]  
> För macOS-enheter anger du en 6-siffrig PIN-kod för återställning. När enheten är låst visar bladet **Enhetsöversikt** PIN-koden tills en annan enhetsåtgärd skickas.

## <a name="how-to-remote-lock-a-device"></a>Fjärrlåsa en enhet

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Fjärrlås**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
