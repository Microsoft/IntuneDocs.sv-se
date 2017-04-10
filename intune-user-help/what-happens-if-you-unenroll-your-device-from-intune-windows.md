---
title: "Vad händer om du avregistrerar din Windows-enhet? | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: a87fe0cf9591040f1455d71b1f40cd0705ba8abf
ms.openlocfilehash: 7d41dc09c36684bd30263cfc0519cdacb3ab321b
ms.lasthandoff: 01/24/2017


---


# <a name="what-happens-if-you-unenroll-your-windows-device-from-intune"></a>Vad händer om du avregistrerar din Windows-enhet från Intune?

Använd länkarna under **I den här artikeln** till höger på den här sidan för att hitta information om vilken typ av enhet som du använder.


## <a name="windows-10-windows-81-windows-8-windows-7-windows-vista"></a>Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista

-   Enheten visas inte längre på företagsportalen och du kan inte längre installera appar från företagsportalen.

-   Om klientprogrammet för Intune är installerat tas det bort från datorn.

-   Endpoint Protection-programmet för Intune tas bort från datorn. Om det finns annan antivirusprogramvara installerad på datorn och den har inaktiverats kan det hända att den återaktiveras när Intune Endpoint Protection tas bort. Kontrollera datorn när du har tagit bort den från företagsportalen.

    > [!IMPORTANT]
    > Om det andra virusskyddsprogrammet inte återaktiveras och det inte finns något annat virusskyddsprogram kan datorn vara utsatt för virus och skadlig kod.

-   Inställningar som ändrades på enheten när du lade till den (t.ex. inaktivering av kameran) gäller inte längre.

-   Datorn får inte längre några automatiska programuppdateringar eller antivirusuppdateringar från Intune. Men, beroende på datorns konfiguration, kan den kanske fortfarande ta emot uppdateringar via Windows Server Update Services, Windows Update eller Microsoft Update.

För Windows 8.1 gäller även följande:

-   Det går inte att använda företagsappar eller företagsdata på enheten längre.

-   Vissa e-postappar, t.ex Windows Mail, kan inte komma åt företags-e-post som lagras på din enhet.

-   Du kanske inte kan ansluta till företagets nätverk via Wi-Fi eller VPN.

-   Du kanske inte längre har åtkomst till vissa företagsresurser från din enhet, t.ex. filresurser eller interna webbplatser.

## <a name="windows-10-mobile-and-windows-phone-81"></a>Windows 10 Mobile och Windows Phone 8.1

-   Företagsportalappen avinstalleras från enheten. Det innebär att enheten inte längre visas på företagsportalen, och du kan inte installera appar från företagsportalappen eller från företagsportalens webbplats.

-   Det går inte att använda företagsappar eller företagsdata på enheten längre.

-   Inställningar som ändrades på enheten när du lade till den (t.ex. inaktivering av kameran eller krav på en viss lösenordslängd) gäller inte längre.

    > [!IMPORTANT]
    > Det enda undantaget är krypteringsprinciper, som fortfarande gäller. Om företagets policy krävde att du krypterade din Windows Phone är det enda sättet att dekryptera telefonen att återställa den med hjälp **Inställningar**-menyn.

## <a name="windows-rt-running-windows-81"></a>Windows RT som kör Windows 8.1

-   Företagsportalappen avinstalleras från enheten. Det betyder att enheten inte längre visas på företagsportalen och du kan inte installera appar från företagsportalen.

-   Det går inte att använda företagsappar eller företagsdata på enheten längre.

-   Inställningar som ändrades på enheten när du lade till den (t.ex. inaktivering av kameran eller krav på en viss lösenordslängd) gäller inte längre.

-   Du kanske inte längre kan ansluta till företagets nätverk via Wi-Fi eller VPN.

-   Du kanske inte längre har åtkomst till vissa företagsresurser från din enhet, t.ex. filresurser eller interna webbplatser.

-   Vissa e-postappar, t.ex Windows Mail, kan inte komma åt företags-e-post som lagras på din enhet.

När du tar bort en Windows RT-enhet händer följande:

-   Företagsportalappen avinstalleras från enheten. Det betyder att enheten inte längre visas på företagsportalen, och du kan inte installera appar från företagsportalen.

-   Det går inte att använda företagsappar eller företagsdata på enheten längre.

-   Inställningar som ändrades på enheten när du lade till den (t.ex. inaktivering av kameran eller krav på en viss lösenordslängd) gäller inte längre.

Kontakta IT-administratören om du har frågor. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).

