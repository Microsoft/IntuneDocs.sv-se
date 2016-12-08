---
title: "Vad händer om du installerar företagsportalappen och registrerar din Windows-enhet i Intune? Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9ddbcde20fac83289c4622f69538ff00fa0cb65b
ms.openlocfilehash: 2d56c2f23fd70ab0ca593d1ad5d60889e5855a7a


---


# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-windows-device-in-intune"></a>Vad händer om du installerar företagsportalappen och registrerar din Windows-enhet i Intune?

När du installerar företagsportalappen och sedan använder den för att registrera en Windows- eller Windows Phone-enhet låter du IT-administratören hantera din enhet för att skydda företags- eller skoldata. Det här avsnittet beskriver vad som händer med enheter som är äldre än Windows 10. För Windows 10-enheter läser du [motsvarande avsnitt](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md).

## <a name="what-happens-to-all-windows-devices-after-enrollment"></a>Vad händer med alla Windows-enheter efter registreringen?
Om du registrerar en Windows- eller Windows Phone-enhet i Intune kan du:

-   Komma åt företagets nätverk, samt dina e-post- och arbetsfiler.

-   Hämta företagsappar från webbplatsen för företagsportalen. (För Windows 7 och Windows Vista kan du bara hämta företagsappar från webbplatsen för företagsportalen.)

-   Konfigurera ditt företags eller din skolas e-postkonto automatiskt.

-   Återställa din telefon till fabriksinställningarna om den tappas bort eller blir stulen.

När du registrerar en enhet ger du IT-administratören tillstånd att till exempel:

-   Återställa enheten till tillverkarens standardinställningar. Det är bra om enheten tappas bort eller blir stulen.

-   Ta bara bort företagsrelaterade filer och företagsappar. *Dina personliga data och inställningar tas inte bort.*

-   IT-administratören kan se vilka program som är installerade på enheten, inklusive programvara som du har installerat själv.

-   Ange krav för enheten, till exempel för att kräva ett lösenord eller en PIN-kod för enheten för att skydda företagsdata. IT-administratören kan också begränsa hur många gånger du kan ange ett felaktigt lösenord, och kan låsa dig ute från enheten om du försöker för många gånger.

-   Kräva att du krypterar data på din enhet för att skydda företagsdata, om enheten förloras eller blir stulen.

-   Kräva att du accepterar villkoren.

-   Förhindra dig att ta bilder av företagsrelaterade data.

## <a name="what-happens-to-all-windows-pcs-after-enrollment"></a>Vad händer med alla Windows-datorer efter registreringen?

-  Programvara installeras på datorn så att IT-administratören kan hantera datorn och så att du kan komma åt företagsresurser som appar och kompletterande information. IT-administratören kan automatiskt uppdatera den här programvaran.

-  Intune Endpoint Protection kanske är installerat på datorn. Det här programmet söker efter virus och skadlig kod.

-  IT-administratören kan samla in eller radera data från datorns hårddisk.

-  IT-administratören kan installera appar och uppdateringar på datorn.

## <a name="what-happens-every-eight-hours-after-device-enrollment"></a>Vad händer var åttonde timme efter enhetsregistreringen?
Ungefär var åttonde timme kommer registrerade enheter att:

-   Hämta eventuella uppdateringar av principer eller appar som din IT-administratör har gjort tillgängliga.

-   Skicka eventuella uppdateringar av hårdvaruförteckningen.

-   Skicka eventuella uppdateringar av förteckningar över företagsappar.

Kontakta IT-administratören om du har frågor. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).



<!--HONumber=Nov16_HO1-->


