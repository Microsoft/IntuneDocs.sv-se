---
title: "Återställa enhetens lösenord från företagsportalens webbplats | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e52ebdd62ca68f1d9226def654961075400184a8
ms.openlocfilehash: 31023a2d51d4dd4cb854c1fa077f5a9910232bb4


---


# Återställa enhetens lösenord från företagsportalens webbplats

Om du har tappat bort PIN-koden eller lösenordet för en enhet som du har registrerat i Intune kan du återställa det på [företagsportalens webbplats](http://portal.manage.microsoft.com). Företagsportalens webbplats är en webbsida som du kan använda för att hantera datorer och enheter som registrerats i Intune och för att utföra de flesta av de aktiviteter som du kan göra när du använder företagsportalappen.

> [!NOTE] 
> Knappen Återställ lösenordskod kanske inte visas på webbplatsen för företagsportalen beroende på hur IT-administratören har konfigurerat Intune. Återställning av lösenord stöds inte för Windows 8.1- och Windows RT-enheter.

Så här återställer du lösenordet:

1.  Öppna [företagsportalens webbplats](http://portal.manage.microsoft.com) och tryck på den enhet vars lösenord du vill återställa.

2.  Tryck på **Återställ lösenord**.

    ![tap-passcode-to-reset](./media/iwp-1-tap-reset-passcode.png)

3.  Tryck på **Logga ut** och logga sedan in igen med dina autentiseringsuppgifter för arbetet eller skolan. Du måste logga in igen inom fem minuter.

    ![sign-out-sign-back-in](./media/iwp-2-sign-out.png)

4.  Tryck på **Återställ lösenord**.

    ![tap-reset-passcode](./media/iwp-3-tap-reset-passcode-after-signin.png)

    I tabellen ser du hur lösenordsåterställning fungerar på din enhet.

    |Plattform|Stöd|
    |------------|-----------|
    |Android|Skapar ett nytt, tillfälligt, alfanumeriskt lösenord.|
    |iOS|Tar bort lösenordet från enheten och skapar inte ett nytt tillfälligt lösenord. Om du använder Touch ID måste du konfigurera det igen på enheten eftersom det tas bort om du återställer lösenordet.|
    |Windows 10 (endast mobila enheter)|Skapar ett nytt, tillfälligt, alfanumeriskt lösenord. Windows Hello stöds.|
    |Windows Phone 8.1|Skapar ett nytt, tillfälligt, numeriskt lösenord.|
    När du har låst upp enheten kan du ange ett nytt lösenord genom att gå till **Inställningar** på enheten.

5.  Lås upp enheten och ange sedan ett nytt lösenord eller ändra det tillfälliga lösenordet genom att gå till **Inställningar** på enheten.

    Om du vill visa ett meddelande som bekräftar att lösenordet har återställts klickar du på meddelandeflaggan längst upp till höger på företagsportalens webbplats.

Behöver du fortfarande hjälp? Kontakta IT-administratören. Titta efter kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).

### Se även
[Använda Intune-företagsportalens webbplats](using-the-intune-company-portal-website.md)


<!--HONumber=Jun16_HO4-->


