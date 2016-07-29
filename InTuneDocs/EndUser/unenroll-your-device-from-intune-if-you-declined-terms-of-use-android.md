---
title: "Avregistrera enheten från Intune om du avvisade användningsvillkoren | Microsoft Intune"
description: "Beskriver hur du avregistrerar en Android-enhet från Intune om du avvisade användningsvillkoren och inte kan logga in på företagsportalappen"
keywords: 
author: staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 618e2abda642c3b9b2e813824dfd4235c9309faa
ms.openlocfilehash: 82cc94eb37b11251343706d60a45fb78458cab7e


---


# Avregistrera enheten från Intune om du avvisade användningsvillkoren

Det bästa sättet att avregistrera en Android-enhet är att acceptera användningsvillkoren, logga in i företagsportalappen och sedan följa dessa [anvisningar](unenroll-your-device-from-intune-android.md) för att avregistrera enheten. Om du avböjer användningsvillkoren när du försöker logga in i företagsportalappen hindras du från att logga in i företagsportalappen vid framtida försök. Därför måste du följa särskilda anvisningar för att avregistrera enheten.

När du installerar företagsportalappen avregistrerar du också enheten från Intune, vilket innebär att din enhet inte längre har åtkomst till företagets resurser.  Mer information om vad som händer när du avregistrerar din enhet finns i [Vad händer om jag avregistrerar min enhet från Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Innan du kan avinstallera företagsportalappen måste du välja inställningen **Enhetsadministratörer** och inaktivera **Företagsportalen**. Anvisningarna kan skilja sig en aning beroende på vilken Android-enhet du har.

Avregistrera enheten från Intune och avinstallera företagsportalappen

1.  Gå till **Inställningar** &gt; **Säkerhet &amp; Skärmlås** &gt; **Enhetsadministratörer**.

    Om du slutför det här steget avregistreras enheten helt.

2.  Avmarkera kryssrutan bredvid eller inaktivera **Företagsportalen**.

    Nu kan du installera företagsportalappen.

Behöver du fortfarande hjälp? Kontakta IT-administratören (kontaktinformation finns på [företagsportalens webbplats](http://portal.manage.microsoft.com)) eller skriv till Microsoft Android-teamet på wintunedroidfbk@microsoft.com.


### Se även
[Med hjälp av en Android-enhet med Intune](using-your-android-device-with-intune.md)



<!--HONumber=Jul16_HO4-->


