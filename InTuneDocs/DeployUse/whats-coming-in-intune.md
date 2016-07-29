---
title: Kommande nyheter | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 9b536372623632b609433c49991a8bdc70e6da49


---

# Kommande nyheter i Microsoft Intune – juli
Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka då och då för nytillkommet innehåll.

Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Apphantering
### Förbättra uppdateringsupplevelsen för appetableringsprofiler
Verksamhetsspecifika Apple iOS-appar skapas med en inbyggd etableringsprofil och kod som signeras med ett certifikat. När appen körs på en iOS-enhet bekräftar iOS appens integritet och tillämpar de principer som definierats av etableringsprofilen.

Signeringscertifikatet du använder för att signera appar gäller normalt i 3 år. Däremot upphör etableringsprofilen att gälla efter ett år. Med den här uppdateringen tillhandahåller Intune verktyg för att distribuera en ny etableringsprofilprincip till enheter som har appar som snart slutar att gälla medan certifikatet fortfarande är giltigt.
<!--- TFS 1280247--->

### Stöd för Xamarin
Microsoft Intune App SDK har stöd för Xamarin-appar i följande scenarier:

- När du skriver nya appar eller ändrar koden i befintliga affärsappar med hjälp av Intune SDK. Du kommer att kunna hämta plugin-programmet på [Microsoft Intune-sidan på Github](https://github.com/msintuneappsdk).
- Lägga till stöd för MAM till befintliga affärsappar med hjälp av Intunes programhanteringsverktyg

Om du behöver hjälp med att välja metod läser du [Förbereda appar för hantering av mobilprogram med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).

<!--- TFS 1061478 & TFS 1152340--->

## Enhetshantering
### Höjd gräns för enhetsregistrering
Intune kommer att öka maxgränsen för enhetsregistrering från 5 till 15 enheter per användare.
<!---TFS 1289896 --->

## Hantering av grupper
### Intune-grupper övergår till Azure Active Directory-grupper i början av augusti 2016
Intune får en ny grupphanteringsupplevelse. ADD-säkerhetsgrupper (Azure Active Directory) kommer att användas som användargrupper och enhetsgrupper i Intune. Dessa grupper kommer att användas för all grupphantering, principdistribution och profildistribution **när vi introducerar den nya Azure-baserade Intune-administratörsportalen**.

Med den nya upplevelsen behöver du inte duplicera grupper i olika tjänster och **du får tillgång till nya AADP-gruppfunktioner (Azure Active Directory Premium)**. Dessutom får du möjlighet till utökning med PowerShell och Graph. Du får även en mer enhetlig grupphantering för mobilitetshanteringen i företaget.

Det kommer att göras en del ändringar i den **aktuella administratörskonsolen** i samband med övergången till säkerhetsgrupper. **Dessa ändringar, och användning av AAD-säkerhetsgrupper, kommer att läggas till i Intune-dokumentationen**.

Nya Intune-användare kommer att se **några av ändringarna före befintliga klienter**.

Förutom ändringarna i grupphantering kommer **följande funktion att bli inaktuell**:
- Exkludera medlemmar eller grupper när du skapar en ny grupp
- Hantera grupper i rollen tjänstadministratör
- Anpassade gruppbaserade aviseringar för aviseringsregler
- Pivotering med grupper i rapporter


## Företagsportal

### Tillägg av Meddelanden på företagsportalen för Android
Vi publicerar en uppdatering av företagsportalen för Android i augusti där vi lägger till en ny **Meddelanden**-ikon på startsidan. När användaren trycker på ikonen visas sidan **Meddelanden**. På sidan visas alla objekt som kräver åtgärder i företagsportalappen, till exempel inkompatibla enheter, registreringsuppdatering och aktivering av registreringar. Om du också använder företagsportalappen för iOS kan du redan se dessa meddelanden. När sidan **Meddelanden** läggs till kommer sidan **Konfiguration av företagsåtkomst** inte att visas varje gång du startar eller återupptar företagsportalen för Android, förutsatt att enheten redan är registrerad. Vi vet att många av er har skapat instruktioner till användarna och uppskattar att få veta på förhand när era instruktioner/skärmbilder behöver uppdateras. Uppdatera din dokumentation med de kommande ändringarna. Om du behöver nya skärmbilder kan du gå till https://aka.ms/androidcpupdate  

### Hjälp användarna att lösa registreringsproblem när det inte går att ansluta till arbetsplatsen
Om du använder villkorlig åtkomst: Registreringsanvisningarna för Windows 8.1, Windows 10 Desktop och Windows 10 Mobile har förenklats på företagsportalens webbplats för slutanvändare som inte kunde ansluta till arbetsplatsen (Workplace Join, WPJ). När slutanvändarna försökte registrera och ansluta till arbetsplatsen och registreringen lyckades men inte anslutningen till arbetsplatsen, visades inte den registrerade enheten i listan med enheter som användarna skulle identifiera, vilket orsakade förvirring för användarna. Nu visas separata steg för ”enhetsregistrering” och ”anslutning till arbetsplatsen”, vilket gör det lättare att se status för enheterna och slutföra processen om användarna inte lyckas ansluta till arbetsplatsen. De separata stegen förväntas också underlätta felsökningen för IT-administratörer.

### Ändringar av konton för enhetsregistreringshanterare i iOS-företagsportalappen
För att förbättra prestanda och skalning visar Intune inte längre alla enheter i Enhetsregistreringshanteraren (DEM) i fönstret Mina enheter i företagsportalappen för iOS. Endast den lokala enhet som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kommer endast att utföras från Intune-administrationskonsolen.  Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter. Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt.
<!---TFS 1233681--->
### Begränsa appinstallation med separat inläsning till registrerade Android-enheter
Det går inte längre att installera program på Android-enheter via företagsportalens webbplats om de inte har registrerats i Intune via Intune-företagsportalappen för Android.
<!---TFS 1299082--->

## Tjänstens utfasning
**Företagsportalsappar för Windows 8 och Windows Phone 8 bör inte längre användas från september 2016.** Med början i september 2016 upphör Microsoft Intunes stöd för appar i Microsoft Intune-företagsportalappen för Windows Phone 8- och Windows 8-plattformarna. Uppdatera enheter till Windows 8.1 och Windows Phone 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1 om du vill fortsätta att distribuera appar till dessa enheter.
<!---TFS 1255391--->

**Borttagning av anpassade meddelanderegler för specifika grupper.**
Intune-meddelanderegler används för att definiera vem en e-postavisering ska skickas till från Intune. För närvarande kan du konfigurera meddelanderegler för att skicka e-post till alla användare av enheter i en Intune-enhetsgrupp som du har skapat. Från och med den 1 juni 2016 eller däromkring kommer det inte längre att finnas stöd för att rikta sig till användarskapade grupper.

Den preliminära tidslinjen för den här ändringen ser ut som följer:
- Från och med augusti 2016 kan nya klienter inte se steg två i guiden Skapa meddelanderegel. Befintliga klienter påverkas inte.
- Omkring september 2016 kommer vissa befintliga klienter inte att se kommandot för att välja enhetsgrupper i guiden.
- Omkring november 2016 planerar vi för att samtliga klienter inte kommer att se kommandot för att välja enhetsgrupper i guiden.

<!---   TFS 1278864--->

**Ändringar i stödet för iOS-företagsportalappen.**
I juli krävs det av alla användare att de använder den senaste versionen av Microsoft Intune-företagsportalappen för iOS . Nya användare kommer bara att kunna hämta den senaste versionen och aktuella användare kommer att behöva uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.  

**Intune Viewer-appar.** Med versionen av den nya RMS-delningsappen tar vi bort följande Intune Viewer-appar, med början från augusti 2016:
- Intune AV Viewer
- Intune PDF Viewer
- Intune Image Viewer för Android från Google Play

I stället för att använda Intune Viewer-appar bör du använda den nya Rights Management-appen (RMS-delning) för Android, där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. Läs mer om RMS-delningsappen (med länk till dokumentationen).



### Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Jul16_HO4-->


