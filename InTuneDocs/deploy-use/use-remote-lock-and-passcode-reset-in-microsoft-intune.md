---
title: "Fjärrlåsning och lösenordsåterställning | Microsoft Docs"
description: "Intune tillhandahåller funktioner för både fjärrlåsning och lösenordsåterställning."
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 01/06/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: b3504cc1aab8bbe553581d822af63363668a8ef7

---
# <a name="help-protect-your-devices-with-remote-lock-and-passcode-reset"></a>Skydda dina enheter med fjärrlåsning och lösenordsåterställning

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune tillhandahåller både funktioner för fjärrlåsning och lösenordsåterställning.

## <a name="lock-a-device-remotely"></a>Fjärrlåsa en enhet
Om en användare förlorar en enhet kan du fjärrlåsa enheten. Enheten måste redan ha en PIN-kod eller lösenord konfigurerat för den innan du kan använda fjärrlåsning. 

Följande tabell visar hur fjärrlåsning fungerar på olika mobilplattformar.

|Plattform|Fjärrlåsning|
|------------|---------------|
|macOS|Stöds inte|
|iOS|Stöds|
|Android|Stöds|
|Windows 10 och Windows 10 Mobile|Stöds|
|Windows Phone 8 och Windows Phone 8.1|Stöds|
|Windows RT 8.1 och Windows RT|Stöds om enhetens aktuella användare är samma användare som registrerat enheten.|
|Windows 8,1|Stöds om enhetens aktuella användare är samma användare som registrerat enheten.|

Fjärrlås stöds inte för Windows-datorer som registrerats i Intune-programklienten.

### <a name="lock-a-mobile-device-remotely-through-the-intune-console"></a>Fjärrlåsa en mobil enhet via Intune-konsolen

1.  I [Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** &gt; **Alla mobila enheter**.

2.  Välj **Alla direkthanterade enheter** för enheter som registrerats i Intune eller **Alla hanterade enheter i Exchange ActiveSync**.

    > [!TIP]
    > Du kan också navigera till en enhet efter användare. Välj **Alla användare**. Öppna sidan med egenskaper för användaren, välj **Enheter** och välj sedan namnet på den mobila enhet som du vill låsa.

3.  Välj den eller de enheter i listan som du vill låsa. I verktygsfältet väljer du **Fjärruppgifter** och sedan **Fjärrlås**.

## <a name="reset-the-passcode-on-a-device"></a>Återställa lösenordet på en enhet
Om användare glömmer ett lösenord kan du hjälpa dem genom att ta bort lösenordet från enheten eller genom att framtvinga användningen av ett nytt tillfälligt lösenord på en enhet. Följande tabell visar hur lösenordsåterställning fungerar på olika mobilplattformar.

|Plattform|Återställning av lösenord|
|------------|------------------|
|macOS|Stöds inte|
|iOS|Stöd för att rensa lösenord från en enhet. Skapar inte ett nytt tillfälligt lösenord.|
|Android|Stöds på versioner tidigare än Android 7.0. Skapar ett tillfälligt lösenord.|
|Windows 10 Mobil|Stöds|
|Windows Phone 8 och Windows Phone 8.1|Stöds|
|Windows RT 8.1|Stöds inte|
|Windows 8,1|Stöds inte|
|Windows 10 desktop|Stöds inte|

Lösenordsåterställning stöds inte för Windows-datorer som registrerats i Intune-programklienten.

### <a name="reset-a-passcode"></a>Återställa ett lösenord

1.  I [Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** &gt; **Alla mobila enheter**.

2.  Välj **Alla direkthanterade enheter** för enheter som registrerats i Intune eller **Alla hanterade enheter i Exchange ActiveSync**.

    > [!TIP]
    > Du kan också navigera till en enhet efter användare. Klicka på **Alla användare**. Öppna sidan med egenskaper för användaren, klicka på **Enheter** och sedan på namnet på den mobila enhet som du vill rensa.

3.  Välj den eller de enheter i listan som du vill låsa. I verktygsfältet väljer du **Fjärruppgifter** och sedan **Återställ lösenord**.


### <a name="see-also"></a>Se även
[Ta enheter ur bruk](retire-devices-from-microsoft-intune-management.md) och [Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx) (Selektiv Windows-rensning för datahantering på enheter)



<!--HONumber=Jan17_HO2-->


