---
title: Konfigurera inställningar för enhetsbegränsningar i Microsoft Intune – Azure | Microsoft Docs
description: Lägga till en enhetsprofil för att begränsa funktioner i Android-, macOS-, iOS-, Windows Phone- och Windows 10-enheter i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 56ddf28bb9e81417b4b91bb18baaba14f07fbdd9
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905061"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Konfigurera inställningar för enhetsbegränsningar i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Med enhetsbegränsningar kan du kontrollera en mängd olika inställningar och funktioner som du hanterar i flera kategorier, bland annat:
- Säkerhet
- Webbläsare
- Maskinvara
- Inställningar för delade data

Du kan till exempel skapa en profil för enhetsbegränsningar som förhindrar användare av iOS-enheter från att komma åt kameran på enheten.

Lär dig grunderna för enhetsbegränsningsprofiler och läs sedan ytterligare artiklar för varje plattform för att få veta mer om enhetsegenskaperna.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Skapa en enhetsprofil med inställningar för enhetsbegränsningar

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
4. Ange ett **Namn** och en **Beskrivning** för enhetsbegränsningsprofilen.
5. Välj den enhetsplattform på vilken du vill tillämpa anpassade inställningar från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för inställning av enhetsbegränsningar:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**
6. I listrutan **Profil** väljer du **Enhetsbegränsningar**. Om du vill skapa en enhetsbegränsningsprofil för Windows 10 Team-enheter, som en Surface Hub, väljer du **Enhetsbegränsningar (Windows 10 Team)**.
7. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
    - [Inställningar för Android](device-restrictions-android.md)
    - [Inställningar för iOS](device-restrictions-ios.md)
    - [Inställningar för macOS](device-restrictions-macos.md)
    - [Inställningar för Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Inställningar för Windows 10](device-restrictions-windows-10.md)
    - [Inställningar för Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Inställningar för Windows Holographic for Business](device-restrictions-windows-holographic.md)
    - [Inställningar för Android-arbetsprofil](device-restrictions-android-for-work.md)
8. När du är klar går du tillbaka till sidan **Skapa profil** och klickar på **Skapa**.

Profilen skapas och visas på sidan med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
