---
title: Hantera enheter med Intune
titleSuffix: Intune on Azure
description: "Läs hur du visar de enheter som du hanterar med Intune och utför olika åtgärder på dem.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f066e62e323fffb7c6954d83b2b55ee63f4be46
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Vad är enhetshantering i Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Arbetsbelastningen **Enheter** ger dig insikter om de enheter du hanterar och låter dig utföra fjärråtgärder på dessa enheter. För att få åtkomst till arbetsbelastningen:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.

Nu kan du utföra följande åtgärder:

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


## <a name="support-for-each-device-action"></a>Stöd för varje enhetsåtgärd

Använd följande tabell för att förstå vilka enhetsplattformar som stöds av vilken åtgärd.

|||||||
|-|-|-|-|-|-|
|Enhetsåtgärd|Windows|Windows Phone|iOS|macOS|Android|
|**Ta bort företagsdata**|Ja|Ja|Ja|Ja|Ja|
|**Fabriksåterställning**|Windows 8.1 och senare (ej EAS-hanterade enheter)|Ja|Ja|Nej|Android for Work stöds inte|
|**Ta bort**|Ja|Ja|Ja|Ja|Ja|
|**Fjärrlåsning**|Nej|Windows Phone 8.1 och senare|Ja|Nej|Ja|
|**Återställ lösenord**|Nej|Windows Phone 8.1 till Windows 10 Creators Update som ej är ansluten till Azure AD, Windows 10 Creators Update och senare – alla|Ja|Nej|Android for Work tidigare än i Android 7 stöds inte|
|**Nytt lösenord** (för Windows 10-enheter)|Nej|Windows 10 Creators Update och senare (ansluten till Azure AD)|Nej|Nej|Android for Work stöds inte|
|**Kringgå aktiveringslås**|Nej|Nej|Endast företagsägda enheter|Nej|Nej|
|**Borttappat läge**|Nej|Nej|iOS 9.3 och senare, övervakade och företagsägda enheter|Nej|Nej|
|**Hitta enhet**|Nej|Nej|iOS 9.3 och senare, övervakade och företagsägda enheter i borttappat läge|Nej|Nej|
|**Logga ut aktuell användare**|Nej|Nej|iOS 9.3 och senare (endast delade iPad-enheter)|Nej|Nej|
|**Starta om**|Windows 8.1 och senare|Windows Phone 8.1 och senare|Nej|Nej|Nej|
|**Fresh Start**|Windows 10 Creators Update och senare|Nej|Nej|Nej|Nej|
|**Ny fjärrhjälpsession**|Nej|Nej|Nej|Nej|Ja|
|**Ta bort användare**|Nej|Nej|iOS 9.3 och senare (endast delade iPad-enheter)|Nej|Nej|

## <a name="next-steps"></a>Nästa steg

- Välj **Enhetsåtgärder** om du vill visa status för åtgärder som vidtas på enheter som du hanterar. 
![Övervaka enhetsåtgärder](./media/monitor-device-actions.png)