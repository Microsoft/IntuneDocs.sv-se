---
title: "Vad händer om du avregistrerar din Windows-enhet från Intune? Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08f31db90f324ef5f93076c4e13bfa5328a15adc
ms.openlocfilehash: ebd1300c490f3d69110a5f1920fd25d1dc5cb850


---


# Vad händer om du avregistrerar din Windows-enhet från Intune?

Använd länkarna under "I den här artikeln" till höger på den här sidan för att hitta information om vilken typ av enhet som du använder.


## Windows 10, Windows 8.1, Windows 8, Windows 7, Vista

-   Enheten visas inte längre på företagsportalen och du kan inte längre installera appar från företagsportalen.

-   Om klientprogrammet för Intune är installerat tas det bort från datorn.

-   Endpoint Protection-programmet för Intune tas bort från datorn. Om det finns annan antivirusprogramvara installerad på datorn och den har inaktiverats kan det hända att den återaktiveras när Intune Endpoint Protection tas bort. Kontrollera datorn när du har tagit bort den från företagsportalen.

    > [!IMPORTANT]
    > Om det andra virusskyddsprogrammet inte återaktiveras och det inte finns något annat virusskyddsprogram kan datorn vara utsatt för virus och skadlig kod.

-   Inställningar som ändrades på enheten när du lade till den, exempelvis inaktivering av kameran, gäller inte längre.

-   Datorn får inte längre några automatiska programuppdateringar eller antivirusuppdateringar från Intune. Beroende på datorns konfiguration kan den dock eventuellt fortfarande ta emot uppdateringar via Windows Server Update Services, Windows Update eller Microsoft Update.

För Windows 8.1 gäller även följande:

-   Det går inte att använda företagsappar eller företagsdata på enheten längre.

-   Vissa e-postappar, till exempel Windows Mail, har inte längre åtkomst till företagsrelaterad e-post som lagras på din enhet.

-   Eventuellt går det inte att ansluta till företagets nätverk via Wi-Fi eller VPN.

-   Eventuellt har du inte åtkomst till vissa företagsresurser från din enhet längre, exempelvis fildelningar eller interna webbplatser.

## Windows 10 Mobile och Windows Phone 8.1

-   Företagsportalappen avinstalleras från enheten. Det innebär att din enhet inte längre visas på företagsportalen och du kan inte längre installera appar från företagsportalappen eller företagsportalens webbplats.

-   Det går inte att använda företagsappar eller företagsdata på enheten längre.

-   Inställningar som ändrades på enheten när du lade till den, exempelvis inaktivering av kameran eller att en viss längd på lösenorden krävdes, gäller inte längre.

    > [!IMPORTANT]
    > Det enda undantaget är krypteringsprinciper, som fortfarande gäller. Om företagsprinciperna anger att din Windows Phone ska vara krypterad kan telefonen bara dekrypteras genom att den återställs via **Inställningar**-menyn i Windows Phone.

## Windows RT som kör Windows 8.1

-   Företagsportalappen avinstalleras från enheten. Det innebär att din enhet inte längre visas på företagsportalen och att du inte längre kan installera appar från företagsportalen.

-   Det går inte att använda företagsappar eller företagsdata på enheten längre.

-   Inställningar som ändrades på enheten när du lade till den, exempelvis inaktivering av kameran eller att en viss längd på lösenorden krävdes, gäller inte längre.

-   Eventuellt går det inte längre att ansluta till företagets nätverk via Wi-Fi eller VPN.

-   Eventuellt har du inte åtkomst till vissa företagsresurser från din enhet längre, exempelvis fildelningar eller interna webbplatser.

-   Vissa e-postappar, till exempel Windows Mail, har inte längre åtkomst till företagsrelaterad e-post som lagras på din enhet.

När du tar bort en Windows RT-enhet händer följande:

-   Företagsportalappen avinstalleras från enheten. Det innebär att din enhet inte längre visas på företagsportalen och att du inte längre kan installera appar från företagsportalen.

-   Det går inte att använda företagsappar eller företagsdata på enheten längre.

-   Inställningar som ändrades på enheten när du lade till den, exempelvis inaktivering av kameran eller att en viss längd på lösenorden krävdes, gäller inte längre.

Kontakta IT-administratören om du har frågor. Titta efter kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).




<!--HONumber=Oct16_HO2-->


