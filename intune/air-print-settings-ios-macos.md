---
title: AirPrint-inställningar i Intune för iOS- och macOS-enheter
titlesuffix: Microsoft Intune
description: Läs om hur du kan använda Microsoft Intune för att ansluta iOS- och macOS-enheter automatiskt till AirPrint-kompatibla skrivare.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9e2781743618c213fc57e21026480f7f30535c67
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="airprint-settings-for-ios-and-macos-devices"></a>AirPrint-inställningar för iOS- och macOS-enheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Använd de här inställningarna för att konfigurera att iOS- eller macOS-enheter automatiskt ska ansluta till AirPrint-kompatibla skrivare i nätverket. Du måste ha IP-adressen och resurssökvägen till skrivarna för att kunna fortsätta.

## <a name="find-airprint-printer-information"></a>Hitta information om AirPrint-skrivare

Använd den här metoden för att lägga till AirPrint-information till AirPrint-nyttolasten, så att användarna av iOS-enheter kan skriva ut till kända AirPrint-skrivare.

1. Öppna Terminal på en Mac som är ansluten till samma lokala nätverk (undernät) som AirPrint-skrivarna (från **/Program/Verktyg**)
2. I Terminal skriver du **ippfind** och trycker sedan på returtangenten.
3. Anteckna eventuell skrivarinformation som kommandot returnerar, t.ex.: **ipp://myprinter.local.:631/ipp/port1**. Den första delen av informationen är namnet på skrivaren och den sista delen resurssökvägen.
4. I Terminal skriver du **ping myprinter.local** och trycker sedan på returtangenten.
5. Anteckna den IP-adressinformation som returneras av kommandot, till exempel **PING myprinter.local (10.50.25.21)**.
6. Slutligen använder du IP-adress och resurssökvägen i inställningarna för AirPrint-nyttolasten. Ett exempel på en IP-adress kan vara **10.50.25.21** och ett exempel på en resurssökväg kan vara **/ipp/port1**.

## <a name="configure-an-airprint-profile"></a>Konfigurera en AirPrint-profil

1. Från [Intune i Azure Portal](https://portal.azure.com) går du till [**Enhetsfunktioner** i enhetens konfigurationsområde](device-features-configure.md). 
1. I fönstret **Enhetsfunktioner** väljer du **AirPrint**.
2. Lägg till ett AirPrint-mål genom att i fönstret **AirPrint** ange dess **IP-adress** och **resurssökväg**. Klicka sedan på **Lägg till**.
3. Fortsätt lägga till så många mål som du behöver. Välj **OK** när du är klar.

Du kan också importera en lista med skrivare från en fil med kommaavgränsade värden (.csv) eller exportera listan.


## <a name="next-steps"></a>Nästa steg

Du kan nu tilldela enhetsprofilen till de grupper som du väljer. Mer information finns i [Hur du tilldelar enhetsprofiler](device-profile-assign.md).