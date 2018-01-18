---
title: Skicka iOS-loggar till Microsoft-utvecklare | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 733a590e-836f-4941-bfd9-6ae53ba25e06
searchScope: User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 28c83baeea59f1722744ea63ac19c21599fccebf
ms.sourcegitcommit: 5004b9564915712b41860df20324f39fac3dc27d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/03/2018
---
# <a name="send-logs-to-the-company-portal-developers-for-ios-devices"></a>Skicka loggar till företagsportalens utvecklare för iOS-enheter

Företagsportalappen kan ibland avslutas oväntat. Det här är ett problem som apputvecklarna vill ha mer information om, eftersom det hjälper oss att förbättra funktionaliteten och förhindra att liknande saker händer igen i framtiden. Den här informationen sparas på din enhet i ett specialdokument som kallas _diagnostiklogg_.

Om du råkar ut för detta, så behöver företagsportalsteamet viss information som hjälper dem att diagnostisera orsaken. Gör så här:

1.  Försök att få problemet att uppstå igen. Om du inte kan så är det ingen fara, men det skulle kunna underlätta nästa steg.
2.  Gå till __Inställningar__ > __Sekretess__ > __Analys__ > __Analysdata__. Detta är en lista med över inträffade appaktiviteter, med allt från krascher till allmänna användningsmönster, och den innehåller ingen som helst personlig information. Den här listan sträcker sig från det senaste till det äldsta. Om du har kunnat återskapa problemet så bör detta bör vara det första objektet som visas i listan över appaktiviteter på den här sidan. Om du inte kunde återskapa problemet så bläddra nedåt tills du hittar det första objektet som börjar med "företagsportal". Öppna det genom att trycka på det.
3.  Tryck och håll ned, och dra sedan de små blå punkterna uppåt och nedåt tills all text i rapporten har markerats. Tryck på __Kopiera__ på snabbmenyn.
4.  Öppna din e-postapp och klistra in innehållet i brödtexten i e-postmeddelandets brödtext. Skicka e-postmeddelandet till <a href="mailto:IntuneCPiOSfeedback@microsoft.com?subject=My Company Portal App Closed Unexpectedly&body=Press and hold, then paste your copied Company Portal app logs here.">IntuneCPiOSfeedback@microsoft.com</a>.

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
