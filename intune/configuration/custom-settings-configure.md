---
title: Använd anpassade enhetsinställningar i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa en profil för att använda anpassade inställningar på enheter som kör Windows Phone, Windows 8.1, Windows 10 och senare, Android, Android Enterprise, macOS eller iOS med Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 87c35fdaddec591b57b9b7c28f94560ff52a93b0
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506933"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Skapa en profil med anpassade inställningar i Intune

## <a name="what-are-custom-profiles"></a>Vad är anpassade profiler

Microsoft Intune innehåller många inbyggda inställningar för att styra olika funktioner på en enhet. Du kan också skapa anpassade profiler. Anpassade profiler är användbara om du vill använda enhetsinställningar och funktioner som inte är inbyggda i Intune. Dessa profiler innehåller funktioner och inställningar som du kan styra på enheter i din organisation. Du kan till exempel skapa en anpassad profil som anger samma funktioner för alla iOS-enheter.

Mer information om konfigurationsprofiler finns i [Vad är Microsoft Intune-enhetsprofiler?](device-profiles.md) 

Den här artikeln innehåller länkar med anvisningar för att skapa anpassade profiler för Android, Android Enterprise, iOS, macOS och Windows.

## <a name="available-platforms"></a>Tillgängliga plattformar

Anpassade inställningar konfigureras på olika sätt för respektive plattform. För att styra funktioner på Android- och Windows-enheter kan du till exempel ange OMA-URI-värden (Open Mobile Alliance Uniform Resource Identifier). För Apple-enheter kan du importera en fil som du skapat med [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) eller [Apple profilhanterare](https://support.apple.com/profile-manager).

Anpassade profiler skapas på liknande sätt som inbyggda profiler och är tillgängliga på följande plattformar:

- [Android](../custom-settings-android.md)
- [Android enterprise](../custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>Nästa steg

Välj din plattform och sätt igång:

- [Android](../custom-settings-android.md)
- [Android enterprise](../custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
