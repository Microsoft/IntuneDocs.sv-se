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

## Intune-kommunikation
- **Hälsoinformation för Intune-tjänsten.** för Intune har nu flyttats till en central plats med andra Microsoft-tjänster. Nu hittar du den här informationen i [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx) under Tjänstens hälsa. Mer information finns i [det här blogginlägget](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

- **Introduktion till gränssnittet i Meddelandecenter** Som en del av migreringen av Intune till [hanteringsportalen för Office 365](https://portal.office.com/) kommer vi att börja utnyttja Meddelandecenter för att informera om nya funktioner och annan kommunikation. Genom att installera den medföljande mobilappen för Office 365-administratör kan du också ta emot meddelanden på din mobiltelefon och enkelt vidarebefordra meddelanden till användare eller ett distributionsalias.
Från och med majutgåvan kommer vi att börja använda Meddelandecenter för att meddela dig när uppdateringar är färdiga och för att publicera information om nya och förbättrade Intune-funktioner. Ta en titt på Meddelandecenter redan nu genom att logga in till [hanteringsportalen för Office 365](https://portal.office.com/) och välja alternativet **Meddelandecenter** i det vänstra navigeringsfönstret.

## Apphantering
- **Nya appar tillgängliga för hantering med MAM-principer.** Microsoft Word-, Excel- och PowerPoint-appar för Android kan nu associeras med MAM-principer på enheter som inte har registrerats med Intune. Om du vill se en fullständig lista över appar som stöds kan du gå till Microsoft Intune-galleriet för mobilprogram på [sidan för Microsoft Intune-programpartner](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


- **Villkorlig åtkomst för webbläsare.** Du kan skapa en princip för villkorlig åtkomst för Exchange Online och SharePoint Online så att programmen bara kan användas av hanterade och godkända iOS- och Android-enheter. Användare som försöker logga in till Outlook Web Access (OWA) och SharePoint-webbplatser med iOS- och Android-enheter uppmanas att registrera sina enheter med Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS 1175844--->

- **MAM SDK: Stöd för konfiguration av PIN-kodens längd.** Du kan ange längden på PIN-koden för MAM-appar på samma sätt som PIN-koden för en enhet. Detta innebär att slutanvändaren måste uppfylla de nya begränsningar som du anger. Användaren ser en lite annorlunda PIN-skärm som är anpassad till den längre inmatningen.
<!--- TFS 1104753--->

- **Skype för företag för Android.** Intune-administratörer kan nu välja att rikta MAM mot Skype för företag utan registreringsprinciper.  När användarna har loggat in tillämpas MAM-principerna.
<!--- TFS item 1248444 --->

- **Skype för företag för iOS.** Intune-administratörer kan nu välja att rikta MAM mot Skype för företag utan registreringsprinciper.  När användarna har loggat in tillämpas MAM-principerna.
<!--- TFS item 1248443 --->

### Stöd för Xamarin
Nu har Microsoft Intune App SDK stöd för Xamarin-appar i följande scenarier:

- När du skriver nya appar eller ändrar koden i befintliga affärsappar med hjälp av Intune SDK. Du kan hämta plugin-programmet på [Microsoft Intune-sidan på Github](https://github.com/msintuneappsdk).
- Lägga till stöd för MAM till befintliga affärsappar med hjälp av Intunes programhanteringsverktyg

Om du behöver hjälp med att välja metod läser du [Förbereda appar för hantering av mobilprogram med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->


## Enhetshantering
- **Fjärrhjälpsessioner för Windows-datorer.** TeamViewer-integration för agenthanterade Windows-datorer innebär att du kan underlätta supportavdelningens arbete genom att upprätta fjärrhjälpsessioner med agenthanterade Windows-datorer. Detta gäller Windows 7, 8, 8.1 och Windows 10.
<!--- TFS 1284856--->



## Företagsportal

- **Popup-meddelanden för slutanvändare.** Slutanvändarna ser nu popup-meddelanden från Android-företagsportalappen när de registrerar enheter eller tar bort enheter från företagsportalen.
- **En banderoll för enhetsidentifikation ger mer information till slutanvändaren.** Slutanvändarna kan enkelt identifiera den enhet de valt när de använder företagsportalens webbplats. Om fel enhet har valts kan de välja rätt enhet genom att trycka på länken ”Tryck här” på banderollens startsida.
<!--- TFS 1231157--->

- **Ändringar i kontona för Enhetsregistreringshanterare i Android-företagsportalappen.** I syfte att förbättra prestanda och skalning visar Intune inte längre alla enheter i Enhetsregistreringshanteraren (DEM, Device Enrollment Manager) i fönstret **Mina enheter** i Android-företagsportalappen. Endast den lokala enhet som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen.

- **Ändringar av konton för enhetsregistreringshanterare i iOS-företagsportalappen.** I syfte att förbättra prestanda och skalning visar Intune inte längre alla enheter i enhetsregistreringshanterarna (DEM, Device Enrollment Managers) i fönstret Mina enheter i iOS-företagsportalappen. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen.  Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter.  Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt.



## Tjänstens utfasning
**Borttagning av anpassade meddelanderegler för specifika grupper.**
Intune-meddelanderegler används för att definiera vem en e-postavisering ska skickas till från Intune. För närvarande kan du konfigurera meddelanderegler för att skicka e-post till alla användare av enheter i en Intune-enhetsgrupp som du har skapat. Från och med den 1 juni 2016 eller däromkring kommer det inte längre att finnas stöd för att rikta sig till användarskapade grupper.

Om du vill rikta en meddelanderegel till en grupp som du har skapat via Microsoft Intune-administrationskonsolen skulle du i dag utföra följande steg:

Gå till **Admin**-arbetsytan och klicka på **Meddelanderegler** > **Skapa ny regel**

Välj de enhetsgrupper som regeln ska gälla för i steg två i guiden Skapa meddelanderegel. Det här steget, Välj enhetsgrupper, håller på att fasas ut från Intune-konsolen.

Den preliminära tidslinjen för den här ändringen ser ut som följer:
- Från och med juni 2016 kan nya klienter inte se steg två i guiden Skapa meddelanderegel. Befintliga klienter påverkas inte.
- Runt augusti 2016 kommer vissa befintliga klienter inte att se kommandot för att välja enhetsgrupper i guiden.
- Runt oktober 2016 planerar vi för att samtliga klienter inte kommer att se kommandot för att välja enhetsgrupper i guiden.

<!---   TFS 1278864--->
**Ändringar i stödet för iOS-företagsportalappen.**
Under de kommande månaderna kommer det en uppdatering för Microsoft Intune-företagsportalappen för iOS som bara har stöd för enheter som kör iOS 8.0 eller senare. Användarna kan inte registrera nya enheter som kör versioner under iOS 8.0. Registrerade enheter som kör versioner under iOS 8.0 fortsätter att hanteras och kommer under en begränsad tid att kunna fortsätta använda företagsportalappen. Enheterna måste dock har version iOS 8.0 eller senare installerad för att få åtkomst till den senaste versionen av företagsportalappen. Vi rekommenderar att du att meddelar användarna om att de bör uppdatera till iOS 8.0 eller senare för att kunna dra full nytta av nya funktioner i Intune.  

- **Intune Viewer-appar.** Med versionen av den nya RMS-delningsappen tar vi bort följande Intune Viewer-appar, med början från augusti 2016:
    - Intune AV Viewer
    - Intune PDF Viewer
    - Intune Image Viewer för Android från Google Play

  I stället för att använda Intune Viewer-appar bör du använda den nya Rights Management-appen (RMS-delning) för Android, där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. Läs mer om RMS-delningsappen (med länk till dokumentationen).






### Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).


<!--HONumber=May16_HO5-->


