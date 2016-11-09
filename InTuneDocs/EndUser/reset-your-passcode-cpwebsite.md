---
title: "Återställa enhetens lösenord från företagsportalens webbplats | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2aea845bc00c153f070e04abb67582a5d5a726ca
ms.openlocfilehash: 47b36616f7a8ee23d4d47b41a1db2c41c185c6f5


---


# Återställa enhetens lösenord från företagsportalens webbplats

Om du har tappat bort PIN-koden eller lösenordet för en enhet som du har registrerat i Intune kan du återställa det på [företagsportalens webbplats](http://portal.manage.microsoft.com). Du kan använda webbplatsen för företagsportalen för att hantera datorer och enheter som du har registrerat i Intune och för att utföra de flesta av de uppgifter som du kan utföra när du använder företagsportalappen.

> [!NOTE]
> Knappen **Återställ lösenord** kanske inte visas på webbplatsen för företagsportalen beroende på hur IT-administratören har konfigurerat Intune. Återställning av lösenord stöds inte för Windows 8.1-enheter.

Så här återställer du lösenordet:

1.  Öppna [företagsportalens webbplats](http://portal.manage.microsoft.com) och välj den enhet vars lösenord du vill återställa.

2.  Välj **Återställ lösenord**.

    ![Enhetsinformation med knappen Återställ lösenord](./media/iwp-screen-with-all-options.png)

3.  Välj **Logga ut** och logga sedan in igen med dina autentiseringsuppgifter för arbetet eller skolan. Du måste logga in igen inom fem minuter.

    ![Återställningsmeddelande med utloggningsknapp](./media/iwp-2-sign-out.png)

4.  Välj **Återställ lösenord**.

    ![Meddelande som beskriver vad som händer när du återställer lösenordet](./media/iwp-3-tap-reset-passcode-after-signin.png)

    I tabellen ser du hur **lösenordsåterställning** fungerar på din enhet.

    |Plattform|Stöd|
    |------------|-----------|
    |Android|Skapar ett tillfälligt, alfanumeriskt lösenord.|
    |iOS|Tar bort lösenordet från enheten och skapar inte ett tillfälligt lösenord. Om du använder Touch ID måste du konfigurera det igen på enheten eftersom det tas bort om du återställer lösenordet.|
    |Windows 10 (endast mobila enheter)|Skapar ett tillfälligt, alfanumeriskt lösenord. Windows Hello stöds.|
    |Windows Phone 8.1|Skapar ett tillfälligt, numeriskt lösenord.|
    När du har låst upp enheten kan du ange ett nytt lösenord genom att gå till **Inställningar** på enheten.

5.  Lås upp enheten och ange sedan ett nytt lösenord eller ändra det tillfälliga lösenordet genom att gå till **Inställningar** på enheten.

    Om du vill visa ett meddelande som bekräftar att lösenordet har återställts klickar du på meddelandeflaggan längst upp till höger på företagsportalens webbplats.

Behöver du fortfarande hjälp? Kontakta IT-administratören. Titta efter kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).



<!--HONumber=Oct16_HO3-->


