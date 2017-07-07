---
title: "Importera Wi-Fi-inställningar för Windows 8.1- och senare"
titleSuffix: Intune on Azure
description: "Så här importerar du trådlösa inställningar från Windows till en trådlös Intune-profil.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c4e9b19-b268-4f6d-9663-7cdbe4e4a8dd
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c4ef9bf6ed3f731afada55d2af71d56367f4638d
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Så här importerar du trådlösa inställningar för enheter med Windows 8.1 och senare i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

För enheter som kör Windows 8.1 och Windows 10 (Desktop eller Mobile) kan du importera en Wi-Fi-konfigurationsprofil som tidigare exporterades till en fil.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportera trådlösa inställningar från en Windows-enhet

I Windows kan du använda verktyget **netsh wlan** för att exportera en befintlig trådlös profil till en XML-fil som kan läsas av Intune. Följ stegen nedan på en Windows-dator som redan har nödvändig WiFi-profil installerad.
1. Skapa en lokal mapp för de exporterade trådlösa profilerna, till exempel **c:\WiFi**.
1. Öppna en kommandotolk som administratör.
1. Kör kommandot **netsh wlan show profiles** och anteckna namnet på den profil som du vill exportera. I det här exemplet är profilnamnet **WiFiName**.
1. Kör det här kommandot: **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. När du gör det skapas en trådlös profilfil med namnet **Wi-Fi-WiFiName.xml** i målmappen.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importera trådlösa inställningar till Intune

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för enhetsbegränsningsprofilen.
5. I listrutan **Plattform** väljer du **Windows 8.1 och senare**.
6. I listrutan **Profiltyp** väljer du **Trådlöst (import)**.
7. På bladet **Trådlöst basnätverk** konfigurerar du följande:
    - **Anslutningsnamn** Ange namnet på den trådlösa anslutningen. Det här namnet visas för slutanvändarna när de bläddrar bland tillgängliga trådlösa nätverk.
    - **XML-profil** Klicka på bläddringsknappen för att välja XML-filen som innehåller de trådlösa profilinställningar som du vill importera till Intune.
    - **Filinnehåll** Visar XML-koden för den konfigurationsprofil du har valt.
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.
