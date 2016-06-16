---
# required metadata

title: Kommande nyheter | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/17/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Kommande nyheter i Microsoft Intune
Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka då och då för nytillkommet innehåll.

Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Apphantering
- **Ändringar i företagsdatapolicy för Windows 10.** Till följd av förbättringar av app-principer i företagsdatapolicyn för Windows 10 raderas eventuella befintliga regler som du har konfigurerat när du sparar en princip som har konfigurerats med appregler (tidigare skyddade appar). För att fortsätta måste du konfigurera om dessa appregler.

- **Villkorlig åtkomst för webbläsare.** Du kan skapa en princip för villkorlig åtkomst för Exchange Online och SharePoint Online så att programmen bara kan användas av hanterade och godkända iOS- och Android-enheter. Användare som försöker logga in till Outlook Web Access (OWA) och SharePoint-webbplatser med iOS- och Android-enheter uppmanas att registrera sina enheter med Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS 1175844--->

- **Dynamics CRM Online stöder villkorlig åtkomst.** Kunder kan skapa en princip för villkorlig åtkomst för Dynamics CRM Online så att det bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Slutanvändare som försöker logga in i mobilappen för Dynamics CRM på iOS och Android uppmanas att registrera sig i Intune samt åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS1295358--->

### Stöd för Xamarin
Nu har Microsoft Intune App SDK stöd för Xamarin-appar i följande scenarier:

- När du skriver nya appar eller ändrar koden i befintliga affärsappar med hjälp av Intune SDK. Du kan hämta plugin-programmet på [Microsoft Intune-sidan på Github](https://github.com/msintuneappsdk).
- Lägga till stöd för MAM till befintliga affärsappar med hjälp av Intunes programhanteringsverktyg

Om du behöver hjälp med att välja metod läser du [Förbereda appar för hantering av mobilprogram med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->


## Företagsportal
**Ändringar av konton för enhetsregistreringshanterare i iOS-företagsportalappen.** I syfte att förbättra prestanda och skalning visar Intune inte längre alla enheter i enhetsregistreringshanterarna (DEM, Device Enrollment Managers) i fönstret Mina enheter i iOS-företagsportalappen. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen.  Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter.  Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt.
<!---TFS 1233681--->

## Tjänstens utfasning
**Företagsportalsappar för Windows 8 och Windows Phone 8 bör inte längre användas från september 2016.** Med början i september 2016 upphör Microsoft Intunes stöd för appar i Microsoft Intune-företagsportalappen för Windows Phone 8- och Windows 8-plattformarna. Uppdatera enheter till Windows 8.1 och Windows Phone 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1 om du vill fortsätta att distribuera appar till dessa enheter.
<!---TFS 1255391--->

**Borttagning av anpassade meddelanderegler för specifika grupper.**
Intune-meddelanderegler används för att definiera vem en e-postavisering ska skickas till från Intune. För närvarande kan du konfigurera meddelanderegler för att skicka e-post till alla användare av enheter i en Intune-enhetsgrupp som du har skapat. Från och med den 1 juni 2016 eller däromkring kommer det inte längre att finnas stöd för att rikta sig till användarskapade grupper.

Den preliminära tidslinjen för den här ändringen ser ut som följer:
- Från och med juni 2016 kan nya klienter inte se steg två i guiden Skapa meddelanderegel. Befintliga klienter påverkas inte.
- Runt augusti 2016 kommer vissa befintliga klienter inte att se kommandot för att välja enhetsgrupper i guiden.
- Runt oktober 2016 planerar vi för att samtliga klienter inte kommer att se kommandot för att välja enhetsgrupper i guiden.

<!---   TFS 1278864--->
**Ändringar i stödet för iOS-företagsportalappen.**
Användarna måste uppdatera till den senaste iOS-företagsportalappen. Under de kommande månaderna krävs att alla användare av Microsoft Intune-företagsportalappen för iOS använder den senaste versionen. Nya användare kommer bara att kunna hämta den senaste versionen och aktuella användare kommer att behöva uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.  

**Intune Viewer-appar.** Med versionen av den nya RMS-delningsappen tar vi bort följande Intune Viewer-appar, med början från augusti 2016:
- Intune AV Viewer
- Intune PDF Viewer
- Intune Image Viewer för Android från Google Play

I stället för att använda Intune Viewer-appar bör du använda den nya Rights Management-appen (RMS-delning) för Android, där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. Läs mer om RMS-delningsappen (med länk till dokumentationen).


### Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).


<!--HONumber=Jun16_HO2-->


