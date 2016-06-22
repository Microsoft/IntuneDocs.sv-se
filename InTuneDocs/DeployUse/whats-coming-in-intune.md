---
# required metadata

title: Kommande nyheter | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 06/10/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: mamoriss
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Kommande nyheter i Microsoft Intune
Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka då och då för nytillkommet innehåll.

Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Apphantering
- **Förbättrad konfigurationsupplevelse för Windows 10-företagsdatapolicy.** Vi har gjort förbättringar i konfigurationsupplevelsen för Windows 10- företagsdatapolicyn vad gäller att skapa regler för program, specificera nätverksgränsdefinitioner och andra inställningar för företagsdataskydd.
<!---TFS 1303011--->

- **Villkorlig åtkomst för webbläsare.** Du kan skapa en princip för villkorlig åtkomst för Exchange Online och SharePoint Online så att programmen bara kan användas av hanterade och godkända iOS- och Android-enheter. Användare som försöker logga in till Outlook Web Access (OWA) och SharePoint-webbplatser med iOS- och Android-enheter uppmanas att registrera sina enheter med Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS 1175844--->

- **Dynamics CRM Online stöder villkorlig åtkomst.** Kunder kan skapa en princip för villkorlig åtkomst för Dynamics CRM Online så att det bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Slutanvändare som försöker logga in i mobilappen för Dynamics CRM på iOS och Android uppmanas att registrera sig i Intune samt åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS1295358--->

### Stöd för Xamarin
Microsoft Intune App SDK har stöd för Xamarin-appar i följande scenarier:

- När du skriver nya appar eller ändrar koden i befintliga affärsappar med hjälp av Intune SDK. Du kommer att kunna hämta plugin-programmet på [Microsoft Intune-sidan på Github](https://github.com/msintuneappsdk).
- Lägga till stöd för MAM till befintliga affärsappar med hjälp av Intunes programhanteringsverktyg

Om du behöver hjälp med att välja metod läser du [Förbereda appar för hantering av mobilprogram med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->

## Enhetshantering
- **Windows Defender-principinställning för att skydda mot potentiellt oönskade appar.** En ny Windows Defender-inställning som kallas **identifiering av potentiellt oönskade program** har lagts till i den allmänna konfigurationsprincipen för Windows 10 Desktop och Mobile. Du kan använda den här inställningen för att skydda registrerade stationära Windows-datorer från att köra program som Windows Defender har klassificerat som potentiellt oönskade. Du kan skydda dig mot att dessa program körs eller använda granskningsläget för att rapportera att ett potentiellt oönskat program har installerats.
<!---TFS 1244478--->

## Villkorlig åtkomst
**Cisco ISE-kontrollprinciper för nätverksåtkomst för Intune.**  Kunder som använder Cisco Identity Service Engine (ISE) 2.1 och även använder Microsoft Intune kan ange en princip för nätverksåtkomst i ISE.

Med den här principen måste enheter som ansluter till nätverket med hjälp av Wi-Fi eller VPN uppfylla följande villkor innan de tillåts åtkomst:

* Måste hanteras av Intune
* Måste vara kompatibla med alla distribuerade efterlevnadsprinciper för Intune

Användare med icke kompatibla enheter uppmanas att registrera sig och åtgärda eventuella efterlevnadsproblem för att få åtkomst.
<!---TFS 1299144--->

## Företagsportal
**Ändringar av konton för enhetsregistreringshanterare i iOS-företagsportalappen.** För att förbättra prestanda och skalning visar Intune inte längre alla enheter i Enhetsregistreringshanteraren (DEM) i fönstret Mina enheter i företagsportalappen för iOS. Endast den lokala enhet som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kommer endast att utföras från Intune-administrationskonsolen.  Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter. Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt.
<!---TFS 1233681--->

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


<!--HONumber=Jun16_HO3-->


