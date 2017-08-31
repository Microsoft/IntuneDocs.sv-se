---
title: Hantera enheter med Intune
titleSuffix: Intune on Azure
description: "Läs hur du visar de enheter som du hanterar med Intune och utför olika åtgärder på dem.”"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5d78b4a87eaa366b7bb00356c4b98d609620dcf3
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Vad är enhetshantering i Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Arbetsbelastningen **Enheter** ger dig insikter om de enheter du hanterar och låter dig utföra fjärråtgärder på dessa enheter. För att få åtkomst till arbetsbelastningen:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. Du kan se information om enheter och utföra de fjärrenhetsåtgärder som anges.

## <a name="available-device-actions"></a>Tillgängliga enhetsåtgärder
Vilka åtgärder som är tillgängliga beror på enhetsplattformen och enhetens konfiguration.

- [Visa enhetsinventeringen](device-inventory.md)
- Utför åtgärder för fjärransluten enhet:
    - [Ta bort företagsdata](devices-wipe.md#remove-company-data)
    - [Fabriksåterställning](devices-wipe.md#factory-reset)
    - [Fjärrlåsning](device-remote-lock.md) 
    - [Återställ lösenord](device-passcode-reset.md)
    - [Kringgå aktiveringslås](device-activation-lock-bypass.md) (Endast iOS)
    - [Börja om på nytt](device-fresh-start.md) (Endast Windows)
    - [Borttappat läge](device-lost-mode.md) (Endast iOS)
    - [Hitta enhet](device-locate.md) (Endast iOS)
    - [Starta om](device-restart.md) (Endast Windows)
    - [Återställning av Windows 10-PIN](device-windows-pin-reset.md)
    - [Fjärrstyrning för Android](device-profile-android-teamviewer.md)
    - [Synkronisera enhet](device-sync.md)


## <a name="next-steps"></a>Nästa steg

- Välj **Enhetsåtgärder** om du vill visa status för åtgärder som vidtas på enheter som du hanterar.
![Övervaka enhetsåtgärder](./media/monitor-device-actions.png)
