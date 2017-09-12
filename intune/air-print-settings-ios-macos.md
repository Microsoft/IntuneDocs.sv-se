---
title: "AirPrint-inställningar i Intune för iOS- och macOS-enheter"
titlesuffix: Azure portal
description: "Lär dig hur du kan använda Intune för att ansluta iOS- och macOS-enheter automatiskt till AirPrint-kompatibla skrivare.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f0a0fde27f39873874669c2ea0b435f47ad763d5
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="airprint-settings-for-ios-and-macos-devices"></a>AirPrint-inställningar för iOS- och macOS-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

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

1. På bladet **Enhetsfunktioner** väljer du **AirPrint**.
2. Lägg till ett AirPrint-mål genom att på bladet **AirPrint** ange dess **IP-adress** och **resurssökväg**. Klicka sedan på **Lägg till**.
3. Fortsätt lägga till så många mål som du behöver. Välj **OK** när du är klar.

Du kan också importera en lista med skrivare från en fil med kommaavgränsade värden (.csv) eller exportera listan.


## <a name="next-steps"></a>Nästa steg

Du kan nu tilldela enhetsprofilen till de grupper som du väljer. Mer information finns i [Hur du tilldelar enhetsprofiler](device-profile-assign.md).