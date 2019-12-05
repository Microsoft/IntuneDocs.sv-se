---
title: Använda virtuella Windows 10-datorer med Microsoft Intune
titleSuffix: ''
description: Riktlinjer för att använda virtuella Windows 10-datorer med Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afaf2c8a63bfaed1fdb593baf42c8fa258d7893
ms.sourcegitcommit: 1a22b8b31424847d3c86590f00f56c5bc3de2eb5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74263123"
---
# <a name="using-windows-10-virtual-machines-with-intune"></a>Använda virtuella Windows 10-datorer med Intune

Intune stöder hanteringen av virtuella datorer som kör Windows 10 Enterprise med vissa begränsningar. Intune-hanteringen är inte beroende av eller stör inte hanteringen av Windows Virtual Desktop för samma virtuella dator.

Tänk på följande när du hanterar virtuella Windows 10-datorer med Intune:

## <a name="enrollment"></a>Registrering
- Vi rekommenderar inte att du hanterar virtuella datorer med sessionsvärdar vid behov med Intune. Varje virtuella dator måste registreras när den skapas. Genom att regelbundet ta bort virtuella datorer lämnar du också kvar överblivna enhetsposter i Intune tills de [rensas](../remote-actions/devices-wipe.md#automatically-delete-devices-with-cleanup-rules). 
- Läget för automatisk distribuering av Windows Autopilot stöds inte eftersom det kräver en Trusted Platform Module (TPM). 
- OOBE-registreringen (Out-of-Box Experience) stöds inte på virtuella datorer som bara kan nås med hjälp av RDP (till exempel virtuella datorer som har Azure som värd). Den här begränsningen innebär följande:
    - Windows Autopilot och kommersiell OOBE stöds inte.
    - Alternativen för registreringstatussidan för enhetssammanhangsprinciper stöds inte.

## <a name="configuration"></a>Konfiguration
Intune stöder inte någon konfiguration som använder en Trusted Platform Module eller maskinvaruhantering, inklusive:
- [BitLocker-inställningar](../configuration/device-profiles.md#endpoint-protection)
- [Konfigurationsgränssnittsinställningar för enhetens inbyggda programvara](../configuration/device-profiles.md#device-firmware-configuration-interface)

## <a name="reporting"></a>Rapportering
Intune identifierar automatiskt virtuella datorer och rapporterar dem som ”virtuell dator” i **Enheter** > **Alla enheter** > Välj en enhet > **Översikt** > **Modell**-fältet. 

Frigjorda virtuella datorer kan bidra till rapporter om inkompatibla enheter eftersom de inte kan [checka in med Intune-tjänsten](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

## <a name="retirement"></a>Dra in
Om du bara har RDP-åtkomst ska du inte använda åtgärden [Rensa](../remote-actions/devices-wipe.md#wipe). Åtgärden Rensa tar bort den virtuella datorns RDP-inställningar och hindrar dig från att någonsin ansluta igen.


