---
title: "Importera Wi-Fi-inställningar för Windows 8.1- och senare"
titleSuffix: Microsoft Intune
description: "Så här importerar du trådlösa inställningar från Windows till en trådlös Intune-profil."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0113703cbdc58172edc9552146c7634aa1058e3b
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Importera trådlösa inställningar för enheter med Windows 8.1 och senare i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

För enheter som kör operativsystemen Windows 8.1, Windows 10 Desktop eller Mobile, eller Windows Holographic for Business, kan du importera en Wi-Fi-konfigurationsprofil som tidigare exporterades till en fil.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportera trådlösa inställningar från en Windows-enhet

I Windows kan du använda verktyget **netsh wlan** för att exportera en befintlig trådlös profil till en XML-fil som kan läsas av Intune. Följ stegen nedan på en Windows-dator som redan har nödvändig WiFi-profil installerad.
1. Skapa en lokal mapp för de exporterade trådlösa profilerna, till exempel **c:\WiFi**.
1. Öppna en kommandotolk som administratör.
1. Kör kommandot **netsh wlan show profiles** och anteckna namnet på den profil som du vill exportera. I det här exemplet är profilnamnet **WiFiName**.
1. Kör det här kommandot: **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. När du gör det skapas en trådlös profilfil med namnet **Wi-Fi-WiFiName.xml** i målmappen.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importera trådlösa inställningar till Intune

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-sidan.
2. Välj **Hantera** > **Profiler** på sidan **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilsidan.
4. På sidan **Skapa profil** anger du ett **Namn** och en **Beskrivning** för enhetsbegränsningsprofilen.

   > [!WARNING]
   > Namnet **måste** vara samma namn som namnattributet i Wi-Fi-profilens xml-fil, annars misslyckas det.

5. I listrutan **Plattform** väljer du **Windows 8.1 och senare**.
6. I listrutan **Profiltyp** väljer du **Trådlöst (import)**.
7. På sidan **Trådlöst basnätverk** konfigurerar du följande inställningar:
    - **Anslutningsnamn** Ange namnet på den trådlösa anslutningen. Det här namnet visas för slutanvändarna när de bläddrar bland tillgängliga trådlösa nätverk.
    - **XML-profil** Klicka på bläddringsknappen för att välja XML-filen som innehåller de trådlösa profilinställningar som du vill importera till Intune.
    - **Filinnehåll** Visar XML-koden för den konfigurationsprofil du har valt.
8. När du är klar går du tillbaka till sidan **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på sidan med profillistan.
