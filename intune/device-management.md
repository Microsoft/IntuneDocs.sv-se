---
title: Hantera enheter med Intune
titleSuffix: Intune on Azure
description: "Läs hur du visar de enheter som du hanterar med Intune och utför olika åtgärder på dem.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0fc5337b92ac604a448038f685b27623b6153f9
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/09/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Vad är enhetshantering i Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Arbetsbelastningen **Enheter** ger dig insikter om de enheter du hanterar och låter dig utföra fjärråtgärder på dessa enheter. För att få åtkomst till arbetsbelastningen:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. Du kan nu utföra de fjärrenhetsåtgärder som anges. Vilka åtgärder som är tillgängliga beror på enhetsplattformen och enhetens konfiguration:

## <a name="available-device-actions"></a>Tillgängliga enhetsåtgärder

- [Visa enhetsinventeringen](device-inventory.md)
- Utför åtgärder för fjärransluten enhet:
    - [Ta bort företagsdata](device-company-data-remove.md) 
    - [Fabriksåterställning](device-factory-reset.md)
    - [Fjärrlåsning](device-remote-lock.md)
    - [Återställ lösenord](device-passcode-reset.md)
    - [Kringgå aktiveringslås](device-activation-lock-bypass.md)
    - [Fresh Start](device-fresh-start.md)
    - [Borttappat läge](device-lost-mode.md)
    - [Hitta enhet](device-locate.md)
    - [Starta om](device-restart.md)
    - [PIN-återställning av Windows 10](device-windows-pin-reset.md)
    - [Fjärrstyrning för Android](device-profile-android-teamviewer.md)
    - [Synkronisera enhet](device-sync.md)


## <a name="next-steps"></a>Nästa steg

- Välj **Enhetsåtgärder** om du vill visa status för åtgärder som vidtas på enheter som du hanterar. 
![Övervaka enhetsåtgärder](./media/monitor-device-actions.png)
