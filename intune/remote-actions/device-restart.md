---
title: Starta om enheter med Microsoft Intune – Azure | Microsoft Docs
description: Starta om Windows- och iOS-enheter med Microsoft Intune i Azure-portalen med fjärråtgärden Starta om.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b7b77c4f0127c9ee16b255d0e0e28622b85c323b
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907261"
---
# <a name="remotely-restart-devices-with-intune"></a>Starta om enheter med Intune med en fjärråtgärd


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Åtgärden **Starta om** innebär att enheten som du väljer startas om. Enhetens ägare meddelas inte automatiskt om omstarten, och kan förlora arbete.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds på Windows 8.1 och senare
- Windows Phone – stöds på Windows Phone 8.1 och senare
- Android-kioskenheter – stöds på Android 7.0 och senare
- iOS – stöds

    > [!Note]  
    > Det här kommandot kräver en övervakad enhet och behörighet till **Enhetslås**. Enheten startas om direkt. iOS-enheter som är låsta med lösenord ansluter inte till ett Wi-Fi-nätverk igen efter omstart. Det kan hända att enheten inte kan kommunicera med servern efter omstart.
- macOS – stöds inte
- Android- och Android-arbetsprofilenheter – stöds inte

## <a name="restart-a-device"></a>Starta om en enhet

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Välj **Enheter** > **Alla enheter**.
4. I listan med enheter som du hanterar väljer du en enhet > **Starta om** > **Ja**.

## <a name="next-steps"></a>Nästa steg

- Om du vill se status för åtgärden **Starta om** väljer du **Enheter** > **Enhetsåtgärder**.
