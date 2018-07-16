---
title: Hur du konfigurerar Wi-Fi-inställningar i Intune
titleSuffix: Microsoft Intune
description: Läs om hur du använder Microsoft Intune för att konfigurera WiFi-anslutningar på enheter som du hanterar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e2dba6e0d1c50790c8c2c2bf287695ab67fdb972
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905347"
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Så här konfigurerar du Wi-Fi-inställningar i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Använd Wi-Fi-profiler i Microsoft Intune om du vill tilldela trådlösa nätverksinställningar till användare och enheter i din organisation. När du tilldelar en Wi-Fi-profil får användarna åtkomst till ditt företags Wi-Fi-nätverk utan att de behöver göra några inställningar själva.

Anta till exempel att du installerar ett nytt Wi-Fi-nätverk med namnet Contoso Wi-Fi och att du vill konfigurera alla iOS-enheter så att de ansluter till det här nätverket. Så här ser processen ut:

1. Skapa en Wi-Fi-profil som innehåller alla inställningar som behövs för att ansluta till det trådlösa nätverket Contoso Wi-Fi.
2. Tilldela profilen till en grupp som innehåller alla användare av iOS-enheter.
3. Det nya nätverket Contoso Wi-Fi visas i listan över trådlösa nätverk på användarnas enheter och de kan enkelt ansluta till det.

## <a name="supported-device-platforms"></a>Enhetsplattformar som stöds

Wi-Fi-profiler stöder följande enhetsplattformar:

- Android 4 och senare
- Android-arbetsprofiler
- iOS 8.0 och senare
- macOS (Mac OS X 10.11 och senare)

För enheter som kör Windows 8.1, Windows 10, Windows 10 Mobile och Windows Holographic for Business kan du importera en Wi-Fi-konfiguration som tidigare har exporterats från en annan enhet.

Använd informationen i det här avsnittet om du vill lära dig grunderna för hur du konfigurerar en Wi-Fi-profil. Läs sedan de specifika avsnitten om respektive plattform om du vill ha mer detaljerad information.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Skapa en enhetsprofil som innehåller Wi-Fi-inställningar

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
2. I fönstret **Enhetskonfiguration** under avsnittet **Hantera** väljer du **Profiler**.
3. I fönstret Profiler väljer du **Skapa profil**.
4. Ange **Namn** och **Beskrivning** för Wi-Fi-profilen i fönstret **Skapa profil**.
5. Välj den enhetsplattform på vilken du vill tillämpa Wi-Fi-inställningarna från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för Wi-Fi-inställningar:
    - **Android**
    - **Android enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**

   > [!IMPORTANT]
   > Om du skapar en profil för enheter som kör Windows 10, inklusive Windows Holographic for Business, så måste du välja plattformen **Windows 8.1 och senare**. Plattformen **Windows 10 och senare** innehåller inte någon WiFi-profiltyp. 

6. I listrutan **WiFi-typ** väljer du **Grundläggande** eller **Företag** på Apple- eller Android-enheter. Du kan använda **Grundläggande** för att tillhandahålla basfunktioner som nätverksnamn och SSID. Med **Enterprise** kan du ange mer avancerad information, som t.ex. det utökningsbara autentiseringsprotokollet (EAP), om ditt WiFi-nätverk använder detta protokoll. 

   Profilen **Wi-Fi-import** (för Windows 8.1 och senare) gör det möjligt att importera Wi-Fi-inställningar som en XML-fil som du tidigare har exporterat från en annan enhet.
1. Beroende på vilken plattform du väljer så varierar de inställningar som du kan konfigurera. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
    - [Inställningar för Android och Android-arbetsprofiler](wi-fi-settings-android.md)
    - [Inställningar för iOS](wi-fi-settings-ios.md)
    - [Inställningar för macOS](wi-fi-settings-macos.md)
    - [Inställningar för Windows 8.1 och senare](wi-fi-settings-import-windows-8-1.md) (inklusive Windows Holographic for Business)
1. När du är klar går du tillbaka till fönstret **Skapa profil** och väljer **Skapa**.

Profilen skapas och visas i fönstret med profillistan.

## <a name="next-steps"></a>Nästa steg

Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).
