---
title: Konfigurera inställningar för enhetsbegränsningar i Microsoft Intune – Azure | Microsoft Docs
description: Lägga till en enhetsprofil för att begränsa funktioner i Android-, macOS-, iOS-, Windows Phone- och Windows 10-enheter i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 11b241a14ed70a2e999fa505449cd12cdd1e025e
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728794"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Konfigurera inställningar för enhetsbegränsningar i Microsoft Intune

Med enhetsbegränsningar kan du kontrollera en mängd olika inställningar och funktioner som du hanterar i flera kategorier, bland annat:
- Säkerhet
- Webbläsare
- Maskinvara
- Inställningar för delade data

Du kan till exempel skapa en profil för enhetsbegränsningar som förhindrar användare av iOS-enheter från att komma åt kameran på enheten.

Lär dig grunderna för enhetsbegränsningsprofiler och läs sedan ytterligare artiklar för varje plattform för att få veta mer om enhetsegenskaperna.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Skapa en enhetsprofil med inställningar för enhetsbegränsningar

1. I [Azure Portal](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange ett **Namn** och en **Beskrivning** för enhetsbegränsningsprofilen.
4. Välj den enhetsplattform på vilken du vill tillämpa anpassade inställningar från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för inställning av enhetsbegränsningar:

    - **Android**
    - **Android enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**

5. I listrutan **Profil** väljer du **Enhetsbegränsningar**. För att skapa en enhetsbegränsningsprofil för Windows 10 Team-enheter, som en Surface Hub, väljer du sedan **Enhetsbegränsningar (Windows 10 Team)**.
6. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Välj din plattforms detaljerade inställningar:

    - [Inställningar för Android](device-restrictions-android.md)
    - [Inställningar för Android Enterprise](device-restrictions-android-for-work.md)
    - [Inställningar för iOS](device-restrictions-ios.md)
    - [Inställningar för macOS](device-restrictions-macos.md)
    - [Inställningar för Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Inställningar för Windows 10](device-restrictions-windows-10.md)
    - [Inställningar för Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Inställningar för Windows Holographic for Business](device-restrictions-windows-holographic.md)

7. När du är klar går du tillbaka till sidan **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas på sidan med profillistan. 

## <a name="next-step"></a>Nästa steg

När profilen har skapats är den klar att tilldelas. Se [tilldela enhetsprofiler](device-profile-assign.md) för anvisningar. 

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
