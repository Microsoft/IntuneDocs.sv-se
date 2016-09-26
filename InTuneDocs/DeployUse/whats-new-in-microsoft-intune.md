---
title: "Vad är nytt | Microsoft Intune"
description: "Ta reda på vad är nytt den här månaden och i tidigare versioner av Microsoft Intune"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 03a5dd14b854fedf7e2cb5b949580960a0eab9de
ms.openlocfilehash: 1d09e5a0adb3ecfa8f2d64f668ea7ff16bdf31fa


---

# Nyheter i Microsoft Intune -- September
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

>[!IMPORTANT]
>Blogginlägg – Se till att mobila enheter uppdateras med Microsoft Intune<br>
>Mot bakgrund av de nyligen inträffade "Trident"-attackerna med skadlig kod på iOS-enheter har vi publicerat ett nytt blogginlägg, [Ensuring mobile devices are up to date using Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) (Kontrollera att mobila enheter är uppdaterade med Microsoft Intune).

## Stöd för iOS 10
Befintliga Intune MDM- och MAM-scenarier är kompatibla med iOS 10. Om du vill få tips kan du läsa [Intune-supportteamets blogg](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

## Programhanteringsverktyget stöder MAM utan enhetsregistrering för Android och iOS
Intunes programhanteringsverktyg är ett kommandoradsverktyg som används för att aktivera Intune MAM på verksamhetsspecifika appar för iOS och Android. Det är det enklaste sättet att införliva SDK:n för Intune MAM i appen, så att appen kan verkställa MAM-principer som distribueras genom Intune. Med MAM-principer kan du:

1. Kryptera appens data.
2. Kräva att informationsanställda anger en PIN-kod när appen startas.
3. Tillåta att appen överför data endast till andra hanterade appar.
4. Förhindra att appen säkerhetskopierar data till Android, iTunes och iCloud.
5. Endast tillåta åtgärderna att klippa ut, kopiera och klistra in för andra hanterade appar.

Förhandsversion av den uppdaterade versionen av Intunes programhanteringsverktyg stöder nu MAM utan enhetsregistrering på interna verksamhetsspecifika appar för iOS och Android. Det innebär att slutanvändarna inte behöver registrera sina enheter med Intune för att kunna använda MAM-aktiverade verksamhetsspecifika appar.

Alla kan testa den allmänna förhandsversionen av programvaran och läsa användbar dokumentation som finns i GitHub för msintuneappsdk:

http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Innan du installerar och använder förhandsversionen av Microsoft Intune-programhanteringsverktyget för Android och iOS måste du:

* Granska Microsofts licensvillkor för förhandsversionen av Microsoft Intune-programhanteringsverktyget för Android och iOS
* Skriv ut och behåll en kopia av licensvillkoren för framtida referens. Genom att ladda ned och använda förhandsversionen av Microsoft Intune-programhanteringsverktyget för Android godkänner du licensvillkoren. Om du inte accepterar villkoren har du inte rätt att använda programvaran.
<!---TFS 1235607--->

## Intune-grupper påbörjar övergången till Azure Active Directory i september
Vissa nya Intune-konton kommer att använda Azure Active Directory-säkerhetsgrupper i stället för Intune-användargrupper. Du kommer att veta att du arbetar med säkerhetsgrupper, eftersom sidan för Intune-portalgrupper har en länk som dirigerar dig till Azure-hanteringsportalen.

## Lookout-integrering för att skydda Android-enheter
Microsoft integrerar med Lookouts lösning för mobilhotsskydd för att skydda mobila Android-enheter genom att identifiera skadlig kod, riskfyllda appar med mera, på enheter. Lookouts lösning hjälper dig att bestämma hotnivån, vilken kan konfigureras. Du kan skapa en regel för policy för efterlevnad i Intune för att fastställa enhetens efterlevnad baserat på riskbedömningen av Lookout. Genom att använda åtkomstprinciper kan du tillåta eller blockera åtkomst till företagsresurser utifrån enhetens efterlevnadsstatus.

Slutanvändare med icke-kompatibla enheter kommer att uppmanas att registrera och måste installera Lookout for Work-appen på Android-enheter, aktivera appen och åtgärda hot som rapporteras i Lookout for Work-appen för att få åtkomst. Mer information finns i [Begränsa åtkomsten baserat på enhet, nätverk och programrisk](restrict-access-based-on-device-network-app-risk.md).


## Uppdateringar av företagsportalen

### Android

**Tillägg av "Meddelanden" på företagsportalen för Android**<br/>
En ny ikon för meddelanden har lagts till på företagsportalen för Android på startsidan. När användaren trycker på ikonen visas sidan Meddelanden. På sidan visas alla objekt som kräver åtgärder i företagsportalappen, till exempel inkompatibla enheter, registreringsuppdatering och aktivering av registreringar. Om du använder företagsportalappen för iOS kan du redan se dessa meddelanden. Den nya sidan Meddelanden innebär att användarna inte kommer att se sidan Konfiguration av företagsåtkomst varje gång de startar eller återupptar företagsportalen, förutsatt att enheten redan är registrerad. Om du skapar din egen vägledning för slutanvändare kanske du vill uppdatera din dokumentation för den här ändringen. Sök efter uppdaterade skärmbilder [här](https://aka.ms/androidcpupdate).  
<!---TFS 1095560--->


### iOS
**Ändringar i stödet för iOS-företagsportalappen**<br/>
Alla användare av Microsoft Intune-företagsportalappen för iOS måste nu använda den senaste versionen. Nya användare kan endast ladda ned den senaste versionen och aktuella användare måste uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalsappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.
<!---TFS 1283165--->

**Förbättringar i hur iOS-slutanvändare får sina appar**<br/>
Följande ändringar har gjorts av appanelerna i företagsportalsappen för iOS så att användarna ska kunna få flera vyer på en och samma plats, nämligen företagsportalens webbplats för alla deras appar. Apples begränsningar förhindrar att verksamhetsspecifika appar och hanterade App Store-appar listas i företagsportalsappen, och kräver att användarna besöker olika vyer om de vill hitta alla sina appar.

- Panelen **Företagsappar** visade tidigare en lista över alla program under fliken ALLA på företagsportalens webbplats, och den kommer att fortsätta fungera på samma sätt. Namnet på panelen har ändrats till **Alla appar**.
- Panelen **Andra appar** visade tidigare en vy i företagsportalsappen som visar alla appar som Apple tillåter att företagsportalsappen visar. Namnet på panelen har ändrats till **Aktuella appar**, och om du trycker på panelen öppnas fliken AKTUELLT på företagsportalens webbplats.
-  Panelen **Kategorier** visade tidigare en vy i företagsportalsappen som listar appkategorier. Panelens namn har inte ändrats, men den pekar nu på fliken KATEGORIER på företagsportalens webbplats.
Du kan söka efter uppdaterade skärmbilder [här](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

**Uppmanar till installation av appen iOS Managed Browser om IT Pro anger detta krav för en app**<br/>
Enhetens företagsportalsapp uppmanar dig till att installera den hanterade webbläsaren innan ett webbklipp kan installeras, om du har konfigurerat detta webbklipp så att det bara kan öppnas i den hanterade webbläsaren och om du ännu inte har installerat den hanterade webbläsaren. 
<!---TFS 1228570--->

### Windows
**En feedback-knapp har lagts till i Windows Phone 8.1-företagsportalappen**<br/>
I företagsportalappen för Windows Phone 8.1 kan slutanvändarna skicka feedback om appen med hjälp av en ny "skicka feedback"-knapp. För att hitta knappen trycker användare på "trepunkts"-menyn längst ned till höger på skärmen Företagsportalapp och sedan på **skicka feedback**. Den insamlade, avidentifierade feedbacken hjälper Microsoft att förbättra företagsportalappen för användare.
<!---TFS 1317806--->


## Kommande nyheter

### Intune-grupper övergår till Azure Active Directory-grupper
Intune får en ny grupphanteringsupplevelse. ADD-säkerhetsgrupper (Azure Active Directory) kommer att användas som användargrupper och enhetsgrupper i Intune. Dessa grupper kommer att användas för all grupphantering, principdistribution och profildistribution **när vi introducerar den nya Azure-baserade Intune-administratörsportalen**.

Med den nya upplevelsen behöver du inte duplicera grupper i olika tjänster och **du får tillgång till nya AADP-gruppfunktioner (Azure Active Directory Premium)**. Dessutom får du möjlighet till utökning med PowerShell och Graph. Du får även en mer enhetlig grupphantering för mobilitetshanteringen i företaget.

Det kommer att göras en del ändringar i den **aktuella administratörskonsolen** i samband med övergången till säkerhetsgrupper. **Dessa ändringar, och användning av AAD-säkerhetsgrupper, kommer att läggas till i Intune-dokumentationen**.

Nya Intune-användare kommer att se **några av ändringarna före befintliga klienter**.

Förutom ändringarna i grupphantering kommer **följande funktion att bli inaktuell**:
- Exkludera medlemmar eller grupper när du skapar en ny grupp
- Grupperna **Användare utan grupp** och **Enheter utan grupp**
- **Hantera grupper** i rollen tjänstadministratör
- Anpassade gruppbaserade aviseringar för aviseringsregler
- Pivotering med grupper i rapporter
<!--- TFS 1295329--->

### Nya apprinciper för villkorlig åtkomst till Exchange Online och SharePoint Online
Du kommer att kunna begränsa åtkomsten till Exchange Online och SharePoint Online så att åtkomst endast kan komma från mobila Office-appar som Outlook, Word, Excel och OneDrive. Den här nya funktionen passar perfekt ihop med Intune MAM-principer (mobile app management) eftersom du kan blockera åtkomst till inbyggda e-postklienter eller andra appar som inte har konfigurerats med Intune MAM-principerna. Detta garanterar att dina användare har åtkomst till din organisations data med appar som kan skyddas med Intune MAM. Du kan komma igång med hantering av mobilappar i Intune via Azure Portal. Leta efter det nya avsnittet om villkorlig åtkomst i bladet ”Inställningar”.



### Tjänstens utfasning

- **Företagsportalappar för Windows 8 och Windows Phone 8 blir inaktuella** <br/>
Från och med oktober 2016 kommer Microsoft Intune inte längre stödja företagsportalappar för Windows 8 och Windows Phone 8. Microsoft Intunes stöd för Windows Phone 8-plattformen kommer också att upphöra. Följaktligen kommer du inte att kunna registrera eller uppdatera Windows Phone 8-enheter. Men du kan fortsätta att hantera Windows Phone 8- och Windows 8-enheter som redan har registrerats. Uppdatera enheter med Windows Phone 8 och Windows 8 till Windows Phone 8.1 respektive Windows 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1. På så sätt kan du fortsätta att distribuera appar till dessa enheter utan avbrott.



### Moln-översikt
Håll dig informerad om Intunes utveckling i [översikten över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).


## Tidigare versioner av Intune
Information om det senaste halvårets nyheter i Intune finns i artikeln [Tidigare Intune-versioner](previous-intune-releases.md).

### Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Sep16_HO3-->


