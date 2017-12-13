---
title: "Lås enheten från företagsportalen | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b
searchScope: User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: f5c2536e4566baa2661b77f5574085410784a787
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2017
---
# <a name="remotely-lock-your-device-from-the-company-portal-website"></a>Fjärrlås din enhet från företagsportalens webbplats

Olyckor händer och ibland kan enheter tappas bort. Om du har tappat bort din enhet, eller blivit bestulen, är kanske det första problemet du oroar dig för att vem som helst kan komma åt informationen på den, oavsett var enheten är.

[!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

För att vara säker kan du låsa den med hjälp av fjärrlåsningsalternativet på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog). Fjärrlåset fungerar på:

* Android
* iOS
* macOS
* Windows 10 Mobile (om enheten redan har ett angivet lösenord)
* Windows Phone 8.1 (om enheten redan har ett angivet lösenord)

## <a name="to-use-remote-lock-to-lock-your-device"></a>Använda Fjärrlås för att låsa enheten

1.  På [webbplatsen för företagsportalen](https://portal.manage.microsoft.com#HelpDeskDialog) trycker du på __menyknappen__ ![En liten bild på menyknappen (tre vågräta streck)](/Intune/whats-new/media/CP_hamburger_menu.png) och väljer __Mina enheter__.

  ![En bild av webbplatsen för företagsportalen med en utökad sidomeny till vänster på skärmen med knapparna Start, Alla appar, Mina enheter, Support och Logga ut.](/media/iwp-expanded-sidebar.png)

2. På sidan __Mina enheter__ väljer du namnet på den enhet som du vill låsa.

  ![En skärmbild på sidan Min enhet med ett par oidentifierade enheter ovanför popup-meddelandet om att registrera enheter som inte finns i listan eller identifiera oidentifierade enheter.](./media/macOS_enroll_002_tap_here_banner.png)

3.  Enheten öppnas i ett popup-fönster. Tryck på knappen **Fjärrlås**.

    ![Alla alternativ för den valda enheten på webbplatsen för företagsportalen, inklusive Byt namn, Ta bort, Återställ enhet, Återställ lösenord och Fjärrlås. ](./media/iwp-screen-with-all-options.png)

4.  Ett meddelande visas så att du vet att du håller på att låsa enheten. Tryck på **Fjärrlåsning** så kommer företagsportalens webbplats att försöka låsa enheten.

    När du väljer **Fjärrlås** visas meddelandet ”Fjärrlås väntar”.  När fjärrlåsningen lyckas ändras statusen till ”Enheten har fjärrlåsts”.

    Fjärrlåsningens status visas på tre platser:

    * Meddelandefältet på webbplatsen.
    * Sidan **Information** för enheten.
    * Panelen som visar namnet på enheten i avsnittet **Mina enheter** på sidan.

> [!Note]
> Om meddelandet ”Det gick inte att fjärrlåsa” visas väntar du några minuter och provar sedan att låsa enheten igen. När du försöker igen ändras statusen till ”Fjärrlås väntar” igen. Om åtgärden inte fungerar måste du kontakta företagets support.

Om du hittar din enhet och vill låsa upp den efter att du har använt Fjärrlås anger du bara ditt lösenord.

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
