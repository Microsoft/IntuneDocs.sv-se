---
title: "Konfigurera begränsningar för Intune-enheter | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs mer om hur använder Intune för att konfigurera inställningar och funktioner på enheter som du hanterar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: c6293e9c669266203705a8fe06c323869dc7881f
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Så här konfigurerar du enhetsbegränsningar i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Med enhetsbegränsningar kan du kontrollera en mängd olika inställningar och funktioner som du hanterar i flera kategorier, bland annat säkerhet, webbläsare, maskinvara och datadelning. Du kan till exempel skapa en profil för enhetsbegränsningar som förhindrar användare av iOS-enheter från att komma åt kameran på enheten.

Använd informationen i det här avsnittet om du vill lära dig grunderna för hur du konfigurerar profiler för enhetsbegränsningar. Läs sedan de specifika avsnitten om respektive plattform om du vill ha mer detaljerad enhetsinformation.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Skapa en enhetsprofil med inställningar för enhetsbegränsningar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för enhetsbegränsningsprofilen.
5. Välj den enhetsplattform på vilken du vill tillämpa anpassade inställningar från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för inställning av enhetsbegränsningar:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**
6. I listrutan **Profil** väljer du **Enhetsbegränsningar**. Om du vill skapa en enhetsbegränsningsprofil för Windows 10 Team-enheter, som en Surface Hub, väljer du **Enhetsbegränsningar (Windows 10 Team)**.
7. Beroende på vilken plattform du har valt så varierar de inställningar som du kan konfigurera. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
    - [Inställningar för Android](device-restrictions-for-android.md)
    - [Inställningar för iOS](device-restrictions-for-ios.md)
    - [Inställningar för macOS](device-restrictions-for-macos.md)
    - [Inställningar för Windows Phone 8.1](device-restrictions-for-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-for-windows-8-1.md)
    - [Inställningar för Windows 10](device-restrictions-for-windows-10.md)
    - [Inställningar för Windows 10 Team](device-restrictions-for-windows-10-team.md)
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](how-to-assign-device-profiles.md).

## <a name="example-of-device-restriction-settings"></a>Exempel på inställningar för enhetsbegränsningar

I det här utförliga exemplet skapar du en enhetsbegränsningsprincip som blockerar användning av den inbyggda kameranappen på Android-enheter.

![Inaktivera kameran på Android-enheter](./media/disable-android-camera.png)


