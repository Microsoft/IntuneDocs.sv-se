---
title: Funktionsinställningar för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se alla inställningar som används vid konfiguration av macOS-enheter för AirPrint i Microsoft Intune. Se även anvisningar för att hämta IP-adress, sökväg och portinställningar för en AirPrint-server i nätverket. Använd dessa inställningar i en enhetskonfigurationsprofil när du konfigurerar macOS-enheter till att använda AirPrint-servrar i nätverket.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db89dd2cce679597533d2861a43a7a2fd82abd14
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850581"
---
# <a name="macos-device-feature-settings-in-intune"></a>Funktionsinställningar för macOS-enheter i Intune

Intune innehåller vissa inbyggda inställningar som tillåter att macOS-användare skriver ut på AirPrint-skrivare i nätverket. I den här artikeln visas inställningarna, tillsammans med en beskrivning av vad varje inställning gör. Här visas även anvisningar för att hämta IP-adress, sökväg och port för AirPrint-skrivare som använder Terminal-appen (emulator).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en macOS-enhetskonfigurationsprofil](device-features-configure.md).

## <a name="airprint-settings"></a>AirPrint-inställningar

1. I **Inställningar** väljer du **AirPrint**. Ange följande egenskaper för AirPrint-servern:

    - **IP-adress**: Ange skrivarens IPv4- eller IPv6-adress. Om du använder värdnamn till att identifiera skrivare, kan du hämta IP-adressen genom att pinga skrivaren i Terminal-appen. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
    - **Sökväg**: Ange sökvägen till skrivaren. Sökvägen är vanligtvis `ipp/print` för skrivare i nätverket. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
    - **Port**: Ange lyssningsporten för AirPrint-målet. Om du lämnar den här egenskapen tom, kommer AirPrint att använda standardporten. Tillgängligt i iOS 11.0 och senare.
    - **TLS**: Välj **Aktivera** för att skydda AirPrint-anslutningar med TLS (Transport Layer Security). Tillgängligt i iOS 11.0 och senare.

2. Välj **Lägg till**. AirPrint-servern läggs till i listan. Du kan lägga till flera AirPrint-servrar.

    Du kan också **Importera** en kommaavgränsad fil (.csv) med en lista över AirPrint-skrivare. När du har lagt till AirPrint-skrivarna i Intune, kan du också **Exportera** listan.

3. När du är klar väljer du **OK** för att spara listan.

## <a name="get-the-ip-address-and-path"></a>Hämta IP-adress och sökväg

Om du vill lägga till AirPrinter-servrar, behöver du ha skrivarens IP-adress, resurssökväg och port. Följande steg visar hur du hämtar den här informationen.

1. Öppna **Terminal** (från **/Program/Verktyg**) på en Mac som är ansluten till samma lokala nätverk (undernät) som AirPrint-skrivarna.
2. I Terminal-appen skriver du `ippfind` och väljer Retur.

    Observera skrivarinformationen. Du kan exempelvis ange något i stil med `ipp://myprinter.local.:631/ipp/port1`. Den första delen är namnet på skrivaren. Den sista delen (`ipp/port1`) är resurssökvägen.

3. I Terminal skriver du `ping myprinter.local` och väljer Retur.

   Observera IP-adressen. Den visar något i stil med `PING myprinter.local (10.50.25.21)`.

4. Använd värdena för IP-adressen och resurssökvägen. I det här exemplet är IP-adressen `10.50.25.21` och resurssökvägen är `/ipp/port1`.

## <a name="next-steps"></a>Nästa steg

- Visa alla inställningar för [iOS](ios-device-features-settings.md)-enheter.
- Om du vill tilldela profilen till grupper kan du läsa om att [tilldela enhetsprofiler](device-profile-assign.md).
