---
# required metadata

title: Skicka loggar med diagnostikdata till IT-administratören via e-post | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 85c868e7-8d63-480c-9770-4e99614a5c94

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Skicka loggar med diagnostikdata till IT-administratören via e-post

Om det uppstår ett fel på din Android-enhet när du arbetar med dina skol- eller företagsappar eller när du använder företagsportalappen kan du skicka loggar med diagnostikdata som hjälper IT-administratören att identifiera och åtgärda felet. Om du vill inkludera alla detaljer i loggarna, vilket gör det lättare för IT-administratören att lösa problemet, aktiverar du Utförlig loggning. Läs mer om [utförlig loggning](use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android.md).

Så här aktiverar du utförlig loggning:

1.  Öppna företagsportalappen.

2.  Tryck på **Meny** &gt; **Inställningar**.

    > [!NOTE] 
    > **Meny** kan vara en program- eller maskinvaruknapp, beroende på vilken Android-enhet du har.

3.  Under **Diagnostikdata** trycker du på **Skicka Data**.

    > [!NOTE]
    > **Endast om du använder enheter med Android 6.0 eller senare:** När du trycker på **Skicka data** visas meddelandet **Tillåt att företagsportalen kommer åt foton, media och filer på enheten?**. 

    Det här meddelandet är vilseledande eftersom **Microsoft aldrig kommer åt foton, media eller filer på din enhet!** Google styr meddelandetexten, så Microsoft kan inte ändra den.  När du tillåter åtkomst är allt du gör att tillåta att enheten skriver dataloggar till enhetens SD-kort, vilket gör att du kan flytta dessa loggar med hjälp av en USB-kabel.

    Om du nekar åtkomst visas meddelandet igen nästa gång du trycker på **Skicka data**, men du kan inaktivera framtida meddelanden genom att trycka i kryssrutan **Fråga inte igen**.  Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** &gt; **Appar** &gt; **Företagsportal** &gt; **Behörigheter** &gt; **Lagring** och sedan aktivera behörigheten.

4.  Följ anvisningarna för att välja en e-post-app som ska användas för att skicka loggar till IT-administratören. Appen skapar ett föradresserat e-postmeddelande med alla loggar bifogade.


### Se även
[Med hjälp av en Android-enhet med Intune](using-your-android-device-with-intune.md)

<!--HONumber=Jun16_HO2-->


