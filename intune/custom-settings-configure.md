---
title: Använd anpassade enhetsinställningar i Microsoft Intune – Azure | Microsoft Docs
description: Lägga till eller skapa en profil för att använda anpassade inställningar för Windows-, Android- och iOS-enheter med Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce7c263435f92a041b93dc5d34ffa912c6fa87fb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Skapa en profil med anpassade inställningar i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune kanske inte har alla inbyggda inställningar du behöver eller vill ha. Eller så kanske du vill använda en inställning som är tillgänglig i andra enhetsprofiler. Om du vill lägga till dessa inställningar skapar du en enhetsprofil och konfigurerar profilen med anpassade enhetsinställningar.

Den här artikeln innehåller de grundläggande stegen för att skapa en profil med anpassade inställningar. Den innehåller även länkar för att gräva längre ned i skapandet av anpassade inställningar med de olika plattformarna.

## <a name="custom-settings-on-different-platforms"></a>Anpassade inställningar på olika plattformar
Anpassade inställningar konfigureras på olika sätt för respektive plattform. För att styra funktioner på Android- och Windows-enheter kan du till exempel ange OMA-URI-värden (Open Mobile Alliance Uniform Resource Identifier). På Apple-enheter kan du importera en fil som du har skapat med [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration**, **Profiler** och sedan **Skapa profil**.
4. Ange **namn** och **beskrivning** för den anpassade profilen.
5. Välj enhetsplattform för att tillämpa anpassade inställningar från listrutan **Plattform**. Du kan välja någon av följande plattformar:

    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**

6. I listrutan **Profil**typ väljer du **Anpassad**.
7. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Följande länkar ger mer information om de anpassade inställningarna för varje plattform:

    - [Inställningar för Android](custom-settings-android.md)
    - [Inställningar för iOS](custom-settings-ios.md)
    - [Inställningar för macOS](custom-settings-macos.md)
    - [Inställningar för Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
    - [Inställningar för Windows 10](custom-settings-windows-10.md)
    - [Inställningar för Windows Holographic for Business](custom-settings-windows-holographic.md)
    - [Inställningar för Android for Work](custom-settings-android-for-work.md)

8. När du är klar väljer du **Skapa**.

Profilen skapas och visas i profillistan. Information om hur du tilldelar den här profilen till grupper finns i [Tilldela enhetsprofiler](device-profile-assign.md).
