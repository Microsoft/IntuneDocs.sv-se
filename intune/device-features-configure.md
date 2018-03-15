---
title: "Konfigurera funktionsinställningar på enheter i Microsoft Intune"
titleSuffix: 
description: "Läs hur du använder Microsoft Intune till att konfigurera funktioner på enheter som du hanterar."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6cd646976deb1599c4cbc9154b6f2a487029dd79
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
#<a name="configure-device-feature-settings-in-microsoft-intune"></a>Konfigurera enhetens funktionsinställningar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med enhetsfunktioner kan du styra funktioner på iOS- och macOS-enheter, som t.ex. AirPrint, meddelanden och delade enhetskonfigurationer.

I den här artikeln får du lära dig grunderna för hur du konfigurerar profiler för enhetsfunktioner. Läs sedan andra artiklar om respektive plattform om du vill veta mer.

## <a name="create-a-device-profile-containing-device-feature-settings"></a>Skapa en enhetsprofil med inställningar för enhetsfunktioner

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning + hantering**.
3. Välj **Enhetskonfiguration** på **Intune**-sidan.
2. Välj **Profiler** under**Hantera** på sidan **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilsidan.
4. På sidan **Skapa profil** anger du ett **Namn** och en **Beskrivning** för enhetens funktionsprofil.
5. Välj den enhetsplattform som du vill tillämpa inställningarna på i listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för enhetsfunktioner:
    - **iOS**
    - **macOS**
6. I listrutan **Profiltyp** väljer du **Enhetsfunktioner**. 
7. Beroende på vilken plattform du väljer så varierar de inställningar som du kan konfigurera. Gå till någon av följande artiklar om du vill se detaljerade inställningar för respektive plattform:
    - [AirPrint-inställningar för iOS och MacOS](air-print-settings-ios-macos.md)
    - [AirPlay-inställningar för iOS](airplay-settings-ios.md)
    - [Layoutinställningar för iOS-startskärm](home-screen-settings-ios.md)
    - [Appaviseringsinställningar för iOS](app-notification-settings-ios.md)
    - [Konfigurationsinställningar för delade enheter för iOS](shared-device-settings-ios.md)
    - [Konfigurera enkel inloggning för Intune för iOS-enheter](sso-ios.md)
    - [Inställningar för webbinnehållsfilter för iOS](web-content-filter-settings-ios.md)

8. När du är klar väljer du **OK**, går tillbaka till sidan **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas på sidan med profillistan.
## <a name="next-steps"></a>Nästa steg

Om du vill tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).



