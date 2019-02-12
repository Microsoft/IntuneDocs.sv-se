---
title: Skapa enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Lägga till eller konfigurera en enhetsprofil i Microsoft Intune, till exempel välja plattformstyp och konfigurera inställningar i Azure-portalen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: befffd3f3ae43531d8a5f541e6f7cd4e43f4a2b0
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845805"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Skapa en enhetsprofil i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.

2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.

3. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på den nya profilen.
   - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
   - **Plattform**: Välj plattformstyp:  

       - **Android**
       - **Android enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 och senare**
       - **Windows 10 och senare**

   - **Profiltyp**: Välj den typ som du vill skapa. Listans innehåll beror på vilken plattform du väljer.
   - **Inställningar**: Läs en beskrivning av inställningarna för varje profiltyp i följande artiklar:

       -  [Enhetsfunktioner](device-features-configure.md)
       -  [Enhetsbegränsningar](device-restrictions-configure.md)
       -  [Slutpunktsskydd](endpoint-protection-configure.md)
       -  [Identity Protection](identity-protection-configure.md)  
       -  [Helskärmsläge](kiosk-settings.md)
       -  [E-post](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [Wi-Fi](wi-fi-settings-configure.md)
       -  Utbildning för [Windows 10](education-settings-configure.md) och [iOS](wi-fi-settings-ios.md)
       -  [Windows 10-utgåveuppgradering](edition-upgrade-configure-windows-10.md)
       -  [iOS-uppdateringsprinciper](software-updates-ios.md)
       -  [Certifikat](certificates-configure.md)
       -  [Windows informationsskydd](windows-information-protection-configure.md)
       -  [Anpassad](custom-settings-configure.md)

     ![Skärmbild av Skapa profil](./media/create-device-profile.png)

4. Välj **Skapa** när du är klar.

Profilen skapas och visas i listan.

## <a name="next-steps"></a>Nästa steg
[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
