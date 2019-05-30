---
title: Skapa en Wi-Fi-profil för enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se stegen för att skapa en konfigurationsprofil för Wi-Fi-enheter i Microsoft Intune. Skapa profiler för Android, Android Enterprise, Android Kiosk, iOS, macOS, Windows 10 och senare, samt Windows Holographic for Business. Använd de här profilerna till att skapa en Wi-Fi-anslutning som ska använda certifikat, välja en EAP-typ, välja en autentiseringsmetod, aktivera en proxy och mycket mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 73d6aab271e6c065dbdaac2359974457d8fae607
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050562"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Lägga till och använda Wi-Fi-inställningar på dina enheter i Microsoft Intune

Wi-Fi är ett trådlöst nätverk som används av många mobila enheter för att få åtkomst till nätverket. Microsoft Intune innehåller inbyggda Wi-Fi-inställningar som kan distribueras till användare och enheter i din organisation. Den här gruppen med inställningar kallas en ”profil” och kan tilldelas till olika användare och grupper. När den har tilldelats får användare tillgång till organisationens Wi-Fi-nätverk, utan att de behöver konfigurera något själva.

Anta till exempel att du installerar ett nytt Wi-Fi-nätverk som heter Contoso Wi-Fi. Du vill sedan konfigurera att alla iOS-enheter kan ansluta till nätverket. Så här ser processen ut:

1. Skapa en Wi-Fi-profil som innehåller inställningar som ansluter till det trådlösa nätverket Contoso Wi-Fi.
2. Tilldela profilen till en grupp som innehåller alla användare av iOS-enheter.
3. Det nya nätverket Contoso Wi-Fi visas i listan med trådlösa nätverk på användarnas enheter. De kan sedan ansluta till nätverket med hjälp av den autentiseringsmetod som du har valt.

Den här artikeln visar stegen för att skapa en Wi-Fi-profil. Den innehåller även länkar som beskriver de olika inställningarna för varje plattform.

## <a name="supported-device-platforms"></a>Enhetsplattformar som stöds

Wi-Fi-profiler stöder följande enhetsplattformar:

- Android 4 och senare
- Android Enterprise och Kiosk
- iOS 8.0 och senare
- macOS (Mac OS X 10.11 och senare)
- Windows 10 och senare, Windows 10 Mobile och Windows Holographic for Business

> [!NOTE]
> För enheter som kör Windows 8.1 kan du importera en Wi-Fi-konfiguration som tidigare har exporterats från en annan enhet.

## <a name="create-a-device-profile"></a>Skapa en enhetsprofil

1. I [Azure Portal](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** och väljer **Microsoft Intune**. 
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange **Namn** och **Beskrivning** för Wi-Fi-profilen.
4. I listrutan **Plattform** väljer du den enhetsplattform där Wi-Fi-inställningarna ska tillämpas. Alternativen är:

    - **Android**
    - **Android enterprise**
    - **iOS**
    - **macOS**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**

5. I **Profiltyp** väljer du **Wi-Fi**.

    - För **Android Enterprise**-enheter som körs i helskärmsläge kan du välja **Endast enhetsägare** > **Wi-Fi**.
    - För **Windows 8.1 och senare** kan du välja **Wi-Fi-import**. Med det alternativet kan du importera en XML-fil med Wi-Fi-inställningarna, som du tidigare har exporterat från en annan enhet.

6. Några av Wi-Fi-inställningarna skiljer sig åt för de olika plattformarna. Om du vill se inställningarna för en viss plattform väljer du:

    - [Android](wi-fi-settings-android.md)
    - [Android Enterprise och Kiosk](wi-fi-settings-android-enterprise.md)
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 och senare](wi-fi-settings-windows.md)
    - [Windows 8.1 och senare](wi-fi-settings-import-windows-8-1.md), inklusive Windows Holographic for Business

    De flesta plattformar har **grundläggande** inställningar och **företagsinställningar**. De **grundläggande** inställningarna innehåller funktioner som nätverksnamn och SSID. I **företagsinställningarna** kan du ange mer avancerad information, som exempelvis EAP (Extensible Authentication Protocol).

7. När du är klar med Wi-Fi-inställningarna väljer du **Skapa profil** > **Skapa** för att lägga till konfigurationsprofilen. Profilen skapas och visas i profillistan (**Enhetskonfiguration** > **Profiler**).

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Därefter [tilldelar du profilen](device-profile-assign.md) och [övervakar dess status.](device-profile-monitor.md)
