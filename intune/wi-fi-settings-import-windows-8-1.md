---
title: Importera Wi-Fi-inställningar för Windows-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Exportera Wi-Fi-inställningar från en Windows-enhet som en XML-fil med hjälp av netsh wlan. Sedan importerar du den här filen i Intune för att skapa en Wi-Fi-profil för enheter som kör Windows 8.1, Windows 10 och Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ce5cdd9509ed3407491714ccfa853613eb43973
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321143"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importera Wi-Fi-inställningar för Windows-enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

För enheter som kör Windows kan du importera en Wi-Fi-konfigurationsprofil som tidigare exporterats till en fil. **För Windows 10 och senare enheter kan du [skapa en Wi-Fi-profil](wi-fi-settings-windows.md) direkt i Intune**.

Gäller för:  
- Windows 8.1 och senare
- Windows 10 och senare
- Windows 10 Desktop eller Mobile
- Windows 10 Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportera trådlösa inställningar från en Windows-enhet

I Windows kan du använda **netsh wlan** för att exportera en befintlig trådlös profil till en XML-fil som kan läsas av Intune. Nyckeln måste exporteras i oformaterad text för att profilen ska kunna användas.

På en Windows-dator som redan har rätt WiFi-profil installerad, gör du följande:

1. Skapa en lokal mapp för de exporterade trådlösa profilerna, till exempel **c:\WiFi**.
2. Öppna en kommandotolk som administratör.
3. Kör kommandot `netsh wlan show profiles` och anteckna namnet på den profil som du vill exportera. I det här exemplet är profilnamnet **WiFiName**.
4. Kör kommandot `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Detta skapar en Wi-Fi-profil med namnet **Wi-Fi-WiFiName.xml** i målmappen.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importera trådlösa inställningar till Intune

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
4. Ange ett **Namn** och en **Beskrivning** för enhetsbegränsningsprofilen.

    > [!IMPORTANT]
    > - Namnet **måste** vara samma namn som namnattributet i den trådlösa nätverksprofilens xml-fil. Annars misslyckas det.
    > - Om du exporterar en profil för trådlöst nätverk som innehåller en i förväg delad nyckel, **måste** du lägga till `key=clear` i kommandot. Ange till exempel: `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - En i förväg delad nyckel med Windows 10 visar ett reparationsfel i Intune. När detta sker tilldelas den trådlösa nätverksprofilen till enheten och profilen fungerar som förväntat.
    > - Om du exporterar en trådlös nätverksprofil som innehåller en i förväg delad nyckel, måste filen vara skyddad. Nyckeln är i oformaterad text, så det är ditt ansvar att skydda den.

5. I **Plattform** väljer di **Windows 8.1 och senare**.
6. I **Profiltyp** väljer du **Trådlöst (import)**.
7. Konfigurera följande inställningar:
  - **Anslutningsnamn**: Ange ett namn på den trådlösa nätverksanslutningen. Det här namnet visas för slutanvändarna när de bläddrar bland tillgängliga trådlösa nätverk.
  - **XML-profil**: Välj bläddringsknappen för att välja XML-filen som innehåller inställningarna för den trådlösa nätverksprofilen som du vill importera till Intune.
  - **Filinnehåll**: Visar XML-koden för den konfigurationsprofil du har valt.
8. När du är klar väljer du **OK** och sedan **Skapa** för att skapa profilen.

Profilen skapas och visas i profillistan.
