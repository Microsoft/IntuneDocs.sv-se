---
title: "Hur du konfigurerar Wi-Fi-inställningar i Intune"
titleSuffix: Azure portal
description: "Läs om hur använder Intune för att konfigurera WiFi-anslutningar på enheter som du hanterar.”"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1fadb488-9c6c-43c1-ba23-8c69db633b96
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 161b0de7d697a4ed2d8f80dffdef71296eb6ced2
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Så här konfigurerar du Wi-Fi-inställningar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd Wi-Fi-profiler i Microsoft Intune om du vill tilldela trådlösa nätverksinställningar till användare och enheter i din organisation. När du tilldelar en Wi-Fi-profil får användarna åtkomst till ditt företags Wi-Fi-nätverk utan att de behöver göra några inställningar själva.

Anta till exempel att du installerar ett nytt Wi-Fi-nätverk med namnet Contoso Wi-Fi och att du vill konfigurera alla iOS-enheter så att de ansluter till det här nätverket. Så här ser processen ut:

1. Skapa en Wi-Fi-profil som innehåller alla inställningar som behövs för att ansluta till det trådlösa nätverket Contoso Wi-Fi.
2. Tilldela profilen till en grupp som innehåller alla användare av iOS-enheter.
3. Det nya nätverket Contoso Wi-Fi visas i listan över trådlösa nätverk på användarnas enheter och de kan enkelt ansluta till det.

Wi-Fi-profiler stöder följande enhetsplattformar:

- Android 4 och senare
- Android for Work
- iOS 8.0 och senare
- macOS (Mac OS X 10.9 och senare)

För enheter som kör Windows 8.1, Windows 10 och Windows 10 Mobile, kan du importera en Wi-Fi-konfiguration som tidigare har exporterats från en annan enhet.

Använd informationen i det här avsnittet om du vill lära dig grunderna för hur du konfigurerar en Wi-Fi-profil. Läs sedan de specifika avsnitten om respektive plattform om du vill ha mer detaljerad information.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Skapa en enhetsprofil som innehåller Wi-Fi-inställningar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. Ange **Namn** och **Beskrivning** för Wi-Fi-profilen på bladet **Skapa profil**.
5. Välj den enhetsplattform på vilken du vill tillämpa Wi-Fi-inställningarna från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för Wi-Fi-inställningar:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows 8.1 och senare (importera en profil)**
6. I listrutan **Profil** väljer du **Trådlöst basnätverk** eller **Trådlöst företagsnätverk**. Du kan använda **Trådlöst basnätverk** för att tillhandahålla basfunktioner som nätverksnamn och SSID. Med **Trådlöst företagsnätverk** kan du ange mer avancerad information som det utökningsbara autentiseringsprotokollet EAP om ditt Wi-Fi-nätverk använder detta. **Wi-Fi-import** (för Windows 8.1 och Windows 10) gör det möjligt att importera Wi-Fi-inställningar som en XML-fil som du tidigare har exporterat från en annan enhet.
7. Beroende på vilken plattform du har valt så varierar de inställningar som du kan konfigurera. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
    - [Inställningar för Android och Android for Work](wi-fi-settings-android.md)
    - [Inställningar för iOS](wi-fi-settings-ios.md)
    - [Inställningar för macOS](wi-fi-settings-macos.md)
    - [Inställningar för Windows Phone 8.1](wi-fi-settings-import-windows-8-1.md)
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).
