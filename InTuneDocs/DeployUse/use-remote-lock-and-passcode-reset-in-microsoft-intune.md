---
title: "Använda fjärrlåsning och lösenordsåterställning | Microsoft Intune"
description: "Intune tillhandahåller funktioner för både fjärrlåsning och lösenordsåterställning."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: c2b4b6308569e1e67a1c3da18c12d19bdeecf08e

---
# Skydda dina enheter med fjärrlåsning och lösenordsåterställning
Microsoft Intune tillhandahåller både funktioner för fjärrlåsning och lösenordsåterställning.

## Fjärrlåsa en enhet
Om en användare förlorar sin enhet kan du låsa enheten via fjärranslutning. Tabellen nedan visar hur fjärrlåsning fungerar på olika mobilplattformar.

|Plattform|Fjärrlåsning|
|------------|---------------|
|iOS|Stöds|
|Android|Stöds|
|Windows 10 och Windows 10 Mobile|Stöds|
|Windows Phone 8 och Windows Phone 8.1|Stöds|
|Windows RT 8.1 och Windows RT|Stöds om enhetens aktuella användare är samma användare som registrerat enheten.|
|Windows 8.1|Stöds om enhetens aktuella användare är samma användare som registrerat enheten.|


### Så här fjärrlåser du en mobil enhet via Intune-konsolen

1.  I [Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** &gt; **Alla mobila enheter**.

2.  Välj **Alla direkthanterade enheter** för enheter som registrerats i Intune eller **Alla hanterade enheter i Exchange ActiveSync**.

    > [!TIP]
    > Du kan också navigera till en enhet efter användare. Välj **Alla användare**. Öppna sidan med egenskaper för användaren, välj **Enheter** och välj sedan namnet på den mobila enhet som du vill rensa.

3.  Välj den eller de enheter i listan som du vill låsa. I verktygsfältet väljer du **Fjärruppgifter** och sedan **Fjärrlås**.

## Återställa lösenordet på en enhet
Om en användare glömmer sitt lösenord, kan du hjälpa dem genom att ta bort lösenordet från enheten eller genom att tvinga ett nytt tillfälligt lösenord till en enhet. Tabellen nedan visar hur lösenordsåterställning fungerar på olika mobilplattformar.

|Plattform|Återställning av lösenord|
|------------|------------------|
|iOS|Stöd för att rensa lösenord från en enhet. Skapar inte ett nytt tillfälligt lösenord.|
|Android|Stöds och ett tillfälligt lösenord skapas.|
|Windows 10 Mobil|Stöds|
|Windows Phone 8 och Windows Phone 8.1|Stöds|
|Windows RT 8.1 och Windows RT|Stöds inte|
|Windows 8.1|Stöds inte|

### Så här återställer du ett lösenord

1.  I [Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** &gt; **Alla mobila enheter**.

2.  Välj **Alla direkthanterade enheter** för enheter som registrerats i Intune eller **Alla hanterade enheter i Exchange ActiveSync**.

    > [!TIP]
    > Du kan också navigera till en enhet efter användare. Klicka på **Alla användare**. Öppna sidan med egenskaper för användaren, klicka på **Enheter** och sedan på namnet på den mobila enhet som du vill rensa.

3.  Välj den eller de enheter i listan som du vill låsa. I verktygsfältet väljer du **Fjärruppgifter** och sedan **Återställ lösenord**.


### Se även
[Ta enheter ur bruk](retire-devices-from-microsoft-intune-management.md)
[Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx)



<!--HONumber=Jul16_HO4-->


