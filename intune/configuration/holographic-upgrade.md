---
title: Uppgradera till Windows Holographic for Business
titleSuffix: Microsoft Intune
description: Lär dig hur du uppgraderar enheter som kör Windows Holographic till Windows Holographic for Business
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6342ed23f67c37c2f5084e58594294d826a28e40
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506711"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Uppgradera enheter som kör Windows Holographic till Windows Holographic for Business

Microsoft Intune innehåller många inställningar som hanterar och skyddar dina enheter. I den här artikeln visas och beskrivs inställningarna för att uppgradera Windows Holographic-enheter till Windows Holographic for Business. De här inställningarna skapas i uppgraderingens konfigurationsprofil i Intune som sedan skickas eller distribueras till enheter.

I din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar när du uppgraderar dina Windows Holographic-enheter. Du kan köpa Commercial Suite om du behöver licensen som krävs vid uppgraderingen av Microsoft HoloLens. Mer information finns i [Unlock Windows Holographic for Business features](https://docs.microsoft.com/hololens/hololens1-upgrade-enterprise) (Lås upp funktioner i Windows Holographic for Business).

Mer information om den här funktionen finns i [Uppgradera Windows 10-utgåvor eller aktivera S-läget](../edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Versionsuppgradering

- **Version att uppgradera till**: **Windows 10 Holographic for Business**.
- **Licensfil**: Bläddra till och välj den XML-licensfil som du har fått.

  ![Ange XML-filnamnet som innehåller licensinformationen för Holographic for Business](./media/holographic-upgrade/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>Nästa steg

Profilen skapas, men den kanske inte gör något än. Kom ihåg att [tilldela profilen](device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

Du kan också skapa uppgraderingsprofiler för utgåvan till enheter som har [Windows 10 och senare](edition-upgrade-windows-settings.md).
