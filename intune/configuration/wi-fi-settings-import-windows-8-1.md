---
title: Importera Wi-Fi-inställningar för Windows-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Exportera Wi-Fi-inställningar från en Windows-enhet som en XML-fil med hjälp av netsh wlan. Sedan importerar du den här filen i Intune för att skapa en Wi-Fi-profil för enheter som kör Windows 8.1, Windows 10 och Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207017"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importera Wi-Fi-inställningar för Windows-enheter i Intune

För enheter som kör Windows kan du importera en Wi-Fi-konfigurationsprofil som tidigare exporterats till en fil. **För Windows 10 och senare enheter kan du även [skapa en Wi-Fi-profil](wi-fi-settings-windows.md) direkt i Intune**.

Gäller för:  
- Windows 8.1 och senare
- Windows 10 och senare
- Windows 10 Desktop eller Mobile
- Windows 10 Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportera trådlösa inställningar från en Windows-enhet

I Windows kan du använda `netsh wlan` för att exportera en befintlig Wi-Fi-profil till en XML-fil som kan läsas av Intune. Nyckeln måste exporteras i oformaterad text för att profilen ska kunna användas.

På en Windows-dator som redan har rätt WiFi-profil installerad, gör du följande:

1. Skapa en lokal mapp för de exporterade trådlösa profilerna, till exempel **c:\WiFi**.
2. Öppna en kommandotolk som administratör.
3. Kör kommandot `netsh wlan show profiles`. Notera namnet på profilen som du vill exportera. I det här exemplet är profilnamnet **WiFiName**.
4. Kör kommandot `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Detta kommando skapar en fil för Wi-Fi-profilen med namnet **Wi-Fi-WiFiName.xml** i målmappen.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importera trådlösa inställningar till Intune

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett beskrivande namn på profilen. Namnet **måste** vara samma namn som namnattributet i den trådlösa nätverksprofilens xml-fil. Annars misslyckas det.
    - **Beskrivning**: Ange en beskrivning som ger en översikt över inställningen, samt annan viktig information.
    - **Plattform**: Välj **Windows 8.1 och senare**.
    - **Profiltyp**: Välj **Wi-Fi-import**.

    > [!IMPORTANT]
    > - Om du exporterar en profil för trådlöst nätverk som innehåller en i förväg delad nyckel, **måste** du lägga till `key=clear` i kommandot. Ange till exempel: `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - En i förväg delad nyckel med Windows 10 visar ett reparationsfel i Intune. När detta sker tilldelas den trådlösa nätverksprofilen till enheten och profilen fungerar som förväntat.
    > - Om du exporterar en trådlös nätverksprofil som innehåller en i förväg delad nyckel, måste filen vara skyddad. Nyckeln är i oformaterad text, så det är ditt ansvar att skydda den.

4. Ange följande inställningar:

    - **Anslutningens namn**: Ange ett namn på Wi-Fi-anslutningen. Det här namnet visas för användarna när de söker efter tillgängliga Wi-Fi-nätverk.
    - **Profil-XML**: Använd bläddringsknappen och välj XML-filen som innehåller de Wi-Fi-profilinställningar som du vill importera.
    - **Filinnehåll**: Visar XML-koden för den konfigurationsprofil du har valt.

5. Klicka på **OK** för att spara ändringarna.
6. När du är klar väljer du **OK** > **Skapa** för att skapa Intune-profilen. När du är klar visas din profil i listan **Enhetskonfiguration – profiler**.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Se [Översikt över Wi-Fi-inställningar](wi-fi-settings-configure.md), inklusive andra tillgängliga plattformar.
