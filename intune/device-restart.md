---
title: Starta om enheter med Microsoft Intune – Azure | Microsoft Docs
description: Starta om Windows- och iOS-enheter med Microsoft Intune i Azure-portalen med fjärråtgärden Starta om.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 98b3403e3f45e1aa7169937a05692686d97d7362
ms.sourcegitcommit: 390a4be5aa36007c36fb6a5abcfe8d20bc862a4b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="remotely-restart-devices-with-intune"></a>Starta om enheter med Intune med en fjärråtgärd


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Åtgärden **Starta om** innebär att enheten som du väljer startas om. Enhetens ägare meddelas inte automatiskt om omstarten, och kan förlora arbete.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds på Windows 8.1 och senare
- Windows Phone – stöds på Windows Phone 8.1 och senare
- iOS – stöds

    > [!Note]  
    > Det här kommandot kräver en övervakad enhet och behörighet till **Enhetslås**. Enheten startas om direkt. iOS-enheter som är låsta med lösenord ansluter inte till ett Wi-Fi-nätverk igen efter omstart. Det kan hända att enheten inte kan kommunicera med servern efter omstart.
- macOS – stöds inte
- Android – stöds inte

## <a name="restart-a-device"></a>Starta om en enhet

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enheter** > **Alla enheter**.
4. I listan över enheter som du hanterar väljer du en enhet, väljer **Mer** och väljer sedan fjärråtgärden **Starta om**.

## <a name="next-steps"></a>Nästa steg

- Om du vill se status för åtgärden **Starta om** väljer du **Enheter** > **Enhetsåtgärder**.
