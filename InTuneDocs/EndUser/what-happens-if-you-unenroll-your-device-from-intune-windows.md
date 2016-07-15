---
title: "Vad händer om du avregistrerar din enhet från Intune? | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1244d931d1bd3db012fbcfe0bd055d1fd4f2d88a
ms.openlocfilehash: f0108b884439aac9661c9f36f85b47d80209d155


---


# Vad händer om du avregistrerar din enhet från Intune?

Mer information om vad som händer får du via länken som matchar den typ av enhet du använder och som visas i avsnittet ”I den här artikeln” ovan.

- [Windows 10 Mobile, 8.1, Windows 8, Windows 7, Vista](#windows-10-mobile--8-1,-windows-8,-windows-7,-vista)
- [Windows 10, Windows 8.1 eller Windows Phone 8](#windows-10--windows-8-1-or-windows-phone-8)
- [Windows RT som kör Windows 8.1 eller Windows RT](#windows-rt-running-windows-8-1-or-windows-rt)


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

## Windows 10 mobile, Windows Phone 8.1 eller Windows Phone 8

-   Företagsportalappen avinstalleras från enheten. Det innebär att din enhet inte längre visas på företagsportalen och du kan inte längre installera appar från företagsportalappen eller företagsportalens webbplats.

-   Det går inte att använda företagsappar eller företagsdata på enheten längre.

-   Inställningar som ändrades på enheten när du lade till den, exempelvis inaktivering av kameran eller att en viss längd på lösenorden krävdes, gäller inte längre.

    > [!IMPORTANT]
    > Det enda undantaget är krypteringsprinciper, som fortfarande gäller. Om företagsprinciperna anger att din Windows Phone ska vara krypterad kan telefonen bara dekrypteras genom att den återställs via **Inställningar**-menyn i Windows Phone.

## Windows RT som kör Windows 8.1 eller Windows RT

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

### Se även
[Att använda din Windowsenhet med Intune](using-your-windows-device-with-intune.md)


<!--HONumber=Jun16_HO4-->


