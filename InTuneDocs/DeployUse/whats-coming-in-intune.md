---
title: Kommande nyheter | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0d70a46d9c13aad1bc0a940836d83a99b93bb95e
ms.openlocfilehash: 7f84ad1566431a7a72897750fadbc90cb56ec5ce


---

# Kommande nyheter i Microsoft Intune – augusti
Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka då och då för nytillkommet innehåll.

Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Apphantering
### Dolda och visade appar för iOS 9.3
För övervakade enheter som kör iOS 9.3 eller senare kan du använda listan över dolda och visade appar i den allmänna konfigurationsprincipen för iOS för att:
- Ange en lista över appar som ska vara dolda från användare. Användare kan inte visa eller starta dessa appar.
- Ange en lista över appar som användare kan visa och starta. Inga andra appar kan visas eller startas.

Appar som du kan ange omfattar både appar som du har distribuerat och inbyggda iOS-appar som Meddelanden och Anteckningar.
<!---TFS 1279009--->

### Princip för tillåtna och blockerade appar för Samsung KNOX-enheter

Nu kan du konfigurera en anpassad princip för Samsung KNOX-enheter som gör att du kan skapa något av följande:
- En lista över appar som blockeras från att köras på enheten. Även om den har installerats kan en app som definierats i listan över blockerade appar inte aktiveras på enheten.
- En lista över appar som enhetens användare tillåts att installera från Google Play Store. Inga andra appar kan installeras från butiken.

De här inställningarna kan endast användas av enheter som kör Samsung KNOX.
<!--- For details, see [Use custom policies to allow and block apps for Samsung KNOX devices]( custom-policy-to-allow-and-block-samsung-knox-apps.md)--->
<!---TFS 1311629 --->

### Nya appar är kompatibla med hanteringsprinciper för mobilappar (MAM)
Yammer-appen för [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) och [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) är kompatibel med [hanteringsprinciper för mobilappar (MAM) i Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), oavsett om enheten har registrerats.

En fullständig lista över MAM-kompatibla appar finns på webbplatsen för [Microsoft Intune-programpartner](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336--->

## Enhetshantering
### Stöd för Android 7.0
I augusti kommer Intune att stödja "day 0" för det kommande Android 7.0-operativsystemet för mobila enheter.
<!---TFS 1262053--->
### Googles borttagning av funktionen för fjärråterställning av lösenord på Android 7.0-enheter
Google tar bort möjligheten för IT-administratörer och slutanvändare att fjärråterställa lösenordet på Android 7.0-enheter. Tidigare kunde IT-administratörer fjärråterställa en användares lösenord, och slutanvändarna kunde återställa sina lösenord från företagsportalens webbplats.

## Hantering av grupper
### Intune-grupper övergår till Azure Active Directory-grupper i början av september 2016
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

## Företagsportal

### Feedbacklänk från företagsportalen till Microsoft
På företagsportalens webbplats kan slutanvändare trycka på en ny "Feedback"-länk, längst ned på sidan, för att skicka feedback till Microsoft om sina erfarenheter av webbplatsen. Den insamlade, avidentifierade feedbacken hjälper Microsoft att förbättra företagsportalens webbplats för användare.
<!--- TFS 1313657--->

### Tillägg av Meddelanden på företagsportalen för Android
Vi publicerar en uppdatering av företagsportalen för Android i september där vi lägger till en ny **Meddelanden**-ikon på startsidan. När användaren trycker på ikonen visas sidan **Meddelanden**. På sidan visas alla objekt som kräver åtgärder i företagsportalappen, till exempel inkompatibla enheter, registreringsuppdatering och aktivering av registreringar. Om du också använder företagsportalappen för iOS kan du redan se dessa meddelanden. När sidan **Meddelanden** läggs till kommer sidan **Konfiguration av företagsåtkomst** inte att visas varje gång du startar eller återupptar företagsportalen för Android, förutsatt att enheten redan är registrerad. Vi vet att många av er har skapat instruktioner till användarna och uppskattar att få veta på förhand när era instruktioner/skärmbilder behöver uppdateras. Uppdatera din dokumentation med de kommande ändringarna. Om du behöver nya skärmbilder kan du gå till https://aka.ms/androidcpupdate.  

### Förbättringar i hur iOS-slutanvändare får sina appar
Följande ändringar av app-panelerna i företagsportalsappen för iOS görs i september så att användarna ska kunna få flera vyer på en och samma plats, nämligen företagsportalens webbplats för alla deras appar. Apples begränsningar förhindrar för närvarande att verksamhetsspecifika appar och hanterade App Store-appar listas i företagsportalsappen, och kräver att besöker olika vyer om de vill hitta alla sina appar.

- Panelen **Företagsappar** pekar för närvarande på en lista över alla program på fliken ALLA på företagsportalens webbplats, och den kommer att fortsätta fungera på samma sätt. Namnet på panelen ändras till **Alla appar**.
- Panelen **Andra appar** pekar för tillfället pekar på en vy i företagsportalsappen som visar alla appar som Apple tillåter att företagsportalsappen visar. Namnet på panelen ändras till **Aktuella appar**, och om du trycker på panelen öppnas fliken AKTUELLT på företagsportalens webbplats.
-  Panelen **Kategorier** pekar för tillfället på en vy i företagsportalsappen som listar appkategorier. Panelens namn kommer inte att ändras, men den kommer nu att peka på fliken KATEGORIER på företagsportalens webbplats.
Du kan söka efter uppdaterade skärmbilder [här](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

### Uppmanar till installation av appen iOS Managed Browser om IT Pro anger detta krav för en app
I den version av iOS-företagsportalsappen som släpptes i september uppmanar enhetens företagsportalsapp dig till att installera den hanterade webbläsaren innan ett webbklipp kan installeras, om du har konfigurerat detta webbpklipp så att det bara kan öppnas i den hanterade webbläsaren och om du ännu inte har installerat den hanterade webbläsaren. 
<!---TFS 1228570--->

## Tjänstens utfasning
### Företagsportalappar för Windows 8 och Windows Phone 8 blir inaktuella med början i september 2016
Med början i september 2016 upphör Microsoft Intunes stöd för Microsoft Intune-företagsportalappar för Windows Phone 8- och Windows 8-plattformarna. Uppdatera enheter till Windows 8.1 och Windows Phone 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1 om du vill fortsätta att distribuera appar till dessa enheter.
<!---TFS 1255391--->

### Borttagning av anpassade meddelanderegler för specifika grupper
Intune-meddelanderegler används för att definiera vem en e-postavisering ska skickas till från Intune. För närvarande kan du konfigurera meddelanderegler för att skicka e-post till alla användare av enheter i en Intune-enhetsgrupp som du har skapat. Med början i juni 2016 kommer det inte längre att finnas stöd för att rikta sig till användarskapade grupper.

Den preliminära tidslinjen för den här ändringen ser ut som följer:
- Från och med september 2016 kan nya klienter inte se steg två i guiden Skapa meddelanderegel. Befintliga klienter påverkas inte.
- Omkring oktober 2016 kommer vissa befintliga klienter inte att se kommandot för att välja enhetsgrupper i guiden.
- Längre fram planerar vi för att samtliga klienter inte kommer att se kommandot för att välja enhetsgrupper i guiden.

<!---   TFS 1278864--->
### Ändringar i stödet för iOS-företagsportalappen
I september krävs det av alla användare att de använder den senaste versionen av Microsoft Intune-företagsportalappen för iOS. Nya användare kommer bara att kunna hämta den senaste versionen och aktuella användare kommer att behöva uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.

<!---TFS 1283165--->


### Intune Viewer-appar
Med versionen av den nya RMS-delningsappen kommer vi att ta bort följande Intune Viewer-appar i augusti 2016:
- Intune AV Viewer
- Intune PDF Viewer
- Intune Image Viewer för Android från Google Play

I stället för att använda Intune Viewer-appar bör du använda den nya Rights Management-appen (RMS-delning) för Android, där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. Läs mer om [RMS-delningsappen](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app).
<!--- goes in 1608 What's New--->


### Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Aug16_HO4-->


