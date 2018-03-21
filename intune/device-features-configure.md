---
title: "Skapa iOS- eller macOS-enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs"
description: "Lägg till eller skapa en iOS- eller macOS-enhetsprofil och konfigurera inställningarna för AirPrint, AirPlay, layout för startsidan, appmeddelanden, delad enhet, enkel inloggning och webbinnehållsfilter i Microsoft Intune"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e3de7d1bccd57da1290987a714416373cbdd2b0d
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/09/2018
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Lägga till funktionsinställningar för iOS- eller macOS-enheter i Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med enhetsfunktioner kan du kontrollera en rad inställningar och funktioner på iOS- och macOS-enheter, som:

- Inställningar för AirPrint och AirPlay
- Startsideslayout
- Meddelanden från appar
- Konfiguration av delad enhet
- Konfigurera enkel inloggning
- Filtrera webbinnehåll

I den här artikeln finns det information om grunderna i hur du konfigurerar profiler för iOS-enhetsfunktioner. Efter det kan du läsa flera artiklar för att konfigurera plattformsspecifika inställningar för dina enheter.

## <a name="create-a-device-profile"></a>Skapa en enhetsprofil

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj sedan **Microsoft Intune**.
3. Välj **Enhetskonfiguration**, **Profiler** och sedan **Skapa profil**.
4. Ange följande egenskaper:

  - **Namn**: Ange ett beskrivande namn på den nya profilen
  - **Beskrivning**: (Valfritt men rekommenderas) Ange en beskrivning för profilen
  - **Plattform**: Välj din plattformstyp:
    - **iOS**
    - **macOS**
  - **Profiltyp**: Välj **Enhetsfunktioner**
  - **Inställningar**: Inställningarna beror på vilken plattform du väljer. Läs en beskrivning av inställningarna för varje profiltyp i följande artiklar:

    - [AirPrint-inställningar för iOS och MacOS](air-print-settings-ios-macos.md)
    - [AirPlay-inställningar för iOS](airplay-settings-ios.md)
    - [Layoutinställningar för iOS-startskärm](home-screen-settings-ios.md)
    - [Appaviseringsinställningar för iOS](app-notification-settings-ios.md)
    - [Konfigurationsinställningar för delade enheter för iOS](shared-device-settings-ios.md)
    - [Konfigurera enkel inloggning för Intune för iOS-enheter](sso-ios.md)
    - [Inställningar för webbinnehållsfilter för iOS](web-content-filter-settings-ios.md)

5. När du är klar väljer du **OK** och sedan **Skapa** för att spara dina ändringar.

Profilen skapas och visas i listan.

## <a name="next-step"></a>Nästa steg

Information om hur du tilldelar den här profilen till grupper finns i [Tilldela enhetsprofiler](device-profile-assign.md).