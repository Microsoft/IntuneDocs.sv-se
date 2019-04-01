---
title: iOS-enhetsinställningar i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till, konfigurera eller skapa inställningar på iOS-enheter när du vill begränsa funktioner, till exempel lösenordskrav, kontrollera låst skärm, använda inbyggda appar, lägga till begränsade eller godkända appar, hantera bluetooth-enheter, ansluta till molnet för säkerhetskopiering och lagring, aktivera helskärmsläge, lägga till domäner och kontrollera hur användarna samverkar med Safari-webbläsaren i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a92d18615f6be7c1e0ce931d443d2ac986db991e
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566717"
---
# <a name="ios-device-settings-to-allow-or-restrict-features-using-intune"></a>Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln beskriver de olika inställningar som du kan styra på iOS-enheter. Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar för att tillåta eller inaktivera funktioner, ange lösenordsregler, tillåta eller begränsa specifika appar med mera.

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina iOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en profil för enhetskonfiguration begränsningar](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Allmänt

- **Dela användningsdata**: Välj **Blockera** för att förhindra enheten från att skicka diagnostik- och användningsdata till Apple. **Inte konfigurerad** (standard) tillåter att dessa data skickas.
  - **Inställningar för ändring av skicka diagnostik (endast övervakat)**: **blockera** hindrar användaren från att ändra skicka analytics diagnostikinställningarna i **diagnostik- och användningsdata**(enhetens inställningar). **Inte konfigurerad** (standard) tillåter att användaren ändrar dessa enhetsinställningar.

    Den här funktionen gäller för:  
    - iOS 9.3.2 och senare

- **Skärmdump**: Välj **Blockera** för att förhindra skärmbilder eller skärmdumpar på enheten. **Inte konfigurerat** (standard) tillåter användaren att spara skärminnehållet som en bild.
  - **Fjärrskärmsvisning i appen Klassrum (endast övervakat)**: Välj **Blockera** om du vill förhindra appen Klassrum från att visa skärmarna på fjärranslutna enheter. **Inte konfigurerad** (standard) tillåter appen Apple Klassrum att visa skärmen.

    Den här funktionen gäller för:  
    - iOS 9.3 och senare

  - **Skärmvisning utan uppmaning i appen Klassrum (endast övervakat)**: Om det här ställs in på **Tillåt** kan lärarna tyst övervaka skärmarna på elevernas iOS-enheter med hjälp av appen Klassrum utan att eleverna vet om det. Elevenheter som registrerats i en klass som använder appen Klassrum ger automatiskt behörighet till den kursens lärare. **Inte konfigurerad** (standard) förhindrar att den här funktionen.
- **Ej betrodda TLS-certifikat**: Välj**Blockera** om du vill stoppa ej betrodda TLS-certifikat på enheten. **Inte konfigurerad** (standard) kan TLS-certifikat.
- **Företagsappförtroende**: Välj **Blockera** om du vill ta bort knappen **Lita på företagsutvecklare** i Inställningar > Allmänt > Profiler och enhetshantering på enheten. **Inte konfigurerad** (standard) tillåter att användaren väljer att lita på appar som inte laddats ned från App Store.
- **Kontoändring (endast övervakat)**: När den är inställd på **Blockera** kan användaren inte uppdatera enhetsspecifika inställningar från iOS-appens inställningar. Användaren kan t.ex. skapa nya enhetskonton eller ändra användarnamn eller lösenord. **Inte konfigurerad** (standard) tillåter användare att ändra dessa inställningar.

  Den här funktionen gäller även för inställningar som kan nås från appen för iOS-inställningar, som E-post, Kontakter, Kalender, Facebook, Twitter med flera. Den här funktionen gäller inte för appar med kontoinställningar som inte konfigureras från appen för iOS-inställningar, som Microsoft Outlook-appen.
- **Skärmen tid (endast övervakat)**: Välj **blockera** att hindra användare från att ange sina egna begränsningar i skärmen tidsinställningar (enhet). **Inte konfigurerad** tillåter att användaren konfigurerar enhetsbegränsningar (till exempel kontrollfunktioner för föräldrar eller innehåll och sekretessbegränsningar) på enheten.

  Den här inställningen har bytt namn från **aktivera begränsningar i enhetsinställningarna**. Effekten av ändringen:  
  
  - iOS 11.4.1 och tidigare: **Blockera** förhindrar slutanvändare från att ange egna begränsningar i enhetsinställningarna. Är detta samma; och det finns inga ändringar för slutanvändare.
  - iOS 12,0 och senare: **blockera** hindrar slutanvändare från att ange sina egna **skärmen tid** i enhetsinställningarna (Inställningar > Allmänt > skärmen tid), inklusive innehåll och sekretess begränsningar. Enheter som har uppgraderats till iOS 12.0 ser fliken begränsningar i enhetsinställningarna längre (Inställningar > Allmänt > enhetshantering > Hanteringsprofil > begränsningar). Dessa inställningar finns i **Skärmtid**.
  
- **Användning av alternativet Radera allt innehåll och inställningar på enheten (endast övervakat)**: Välj **Blockera** så att användarna inte kan använda alternativet att radera allt innehåll och alla inställningar på enheten (endast övervakat). **Inte konfigurerad** (standard) ger användarna åtkomst till de här inställningarna.
- **Namnbyte för enhet (endast övervakat)**: Välj **Blockera** så att enhetens namn inte kan ändras. **Inte konfigurerad** (standard) tillåter användaren att ändra enhetens namn.
- **Ändring av aviseringsinställningar (endast övervakat)**: Välj **Blockera** så att aviseringsinställningarna inte kan ändras. **Inte konfigurerad** (standard) tillåter användaren att ändra enhetens meddelandeinställningar.
- **Ändring av bakgrundsbild (endast övervakat)**: **Blockera** förhindrar att bakgrundsbilden ändras. **Inte konfigurerad** (standard) tillåter användaren att ändra enhetens bakgrundsbild.
- **Ändringar av inställningar för företagsappsförtroende (endast övervakat)**: **Blockera** förhindrar användaren från att ändra inställningarna för företagsappsförtroende på kontrollerade enheter. **Inte konfigurerad** (standard) tillåter användaren att lita på appar som inte laddats ned från App Store.
- **Ändra konfigurationsprofil (endast övervakat)**: **Blockera** förhindrar ändringar av enhetens konfigurationsprofil. **Inte konfigurerad** (standard) tillåter användaren att installera konfigurationsprofiler.
- **Aktiveringslås (endast övervakat)**: Välj **Tillåt** om du vill aktivera aktiveringslåset på övervakade iOS-enheter. Aktiveringslåset gör det svårare att återaktivera en förlorad eller stulen enhet.
- **Blockera borttagning av appar (endast övervakat)**: Välj **Blockera** om du vill förhindra användare från att ta bort appar. **Inte konfigurerad** (standard) tillåter användaren att ta bort appar från enheten.
- **Blockera USB-begränsat läge (endast övervakat)**: Välj **Blockera** om du vill inaktivera USB-begränsat läge på övervakade enheter. USB-begränsat läge blockerar USB-tillbehör från att utbyta data med en enhet som har varit låst i över en timma. **Inte konfigurerad** (standard) kan USB begränsat läge.
- **Framtvinga automatisk datum och tid (endast övervakat)**: **Kräv** tvingar övervakade enheter att konfigurera datum och tid automatiskt. Enhetens tidszon uppdateras när enheten har mobila anslutningar eller har aktiverats för Wi-Fi med platstjänster.
- **Kräv att elever begär tillstånd att lämna Classroom-kurs (endast övervakat)**: **Kräv** tvingar elever som har registrerats i en ohanterad kurs med appen Classroom att begära tillstånd från läraren om att lämna kursen. **Inte konfigurerad** (standard) tvingar inte eleven att be om behörighet.

  Den här funktionen gäller för:  
  - iOS 11.3 och senare

- **Tillåt klassrummet för att låsa till en app och låsa enheten utan att fråga (endast övervakat)**: **aktivera** låter lärare att låsa appar eller låsa enheten med hjälp av appen klassrum utan att fråga elevens. Låsning appar innebär att kan enheten bara åtkomst lärare angivna appar. **Inte konfigurerad** (standard) som förhindrar att lärare låsning appar eller enheter som använder appen klassrum utan att fråga elevens. 

  Den här funktionen gäller för:  
  - iOS 11.0 and later

- **Ansluta automatiskt till Classroom-klasser utan att fråga (endast övervakat)**: **aktivera** automatiskt tillåter studenter att ansluta till en klass som är i appen klassrum utan att fråga Lärarens. **Inte konfigurerad** (standard) uppmanar lärare som studenter som vill ansluta till en klass som är i appen klassrum.

  Den här funktionen gäller för:  
  - iOS 11.0 and later

- **Tillåt trådlösa PKI-uppdateringar**: **Tillåt** låter dina användare ta emot programuppdateringar utan att ansluta sina enheter till en dator.
- **Begränsa reklamspårning**: Välj **Begränsa** om du vill inaktivera enhetens reklamidentifierare. **Inte konfigurerad** (standard) behåller den aktiverad.
- **Blockera VPN-skapande (endast övervakat)**: **Blockera** förhindrar användare från att skapa VPN-konfigurationsinställningar. **Inte konfigurerad** (standard) tillåter användare att skapa virtuella privata nätverk på enheten.
- **Ändra eSIM-inställningar (endast övervakat)**: **blockera** förhindrar användare från att ta bort eller lägga till en mobil plan till eSIM på enheten. **Inte konfigurerad** (standard) tillåter användare att ändra dessa inställningar.

  Den här funktionen gäller för:  
  - iOS 12.1 och senare

- **Skjuta upp programuppdateringar (endast övervakat)**: när **inte konfigurerad** (standard), programuppdateringar visas på enheten som Apple släpper dem. Till exempel om en iOS-uppdatering hämtar släpps av Apple på ett specifikt datum, visas sedan uppdateringen naturligt på enheten runt lanseringsdatumet.

  **Aktivera** gör att du kan fördröja när programuppdateringar visas på enheter, från 0 – 90 dagar. Den här inställningen styr inte när uppdateringar är eller inte är installerade. 

  - **Fördröjning synligheten för programuppdateringar**: Ange ett värde mellan 0 – 90 dagar. När fördröjningen upphör får användarna ett meddelande om att uppdatera till den tidigaste versionen av OS som var tillgänglig när fördröjningen utlöstes.

    Till exempel om iOS 12.a finns på **1 januari**, och **fördröjning synlighet** är inställd på **5 dagar**, sedan iOS 12.a visas inte som en tillgänglig uppdatering på slutanvändarenheter. På den **sjätte dagen** efter utgivningen att uppdateringen är tillgänglig och slutanvändare kan installera den.

    Den här inställningen gäller för:  
    - iOS 11.3 och senare

## <a name="password"></a>Lösenord

- **Lösenord**: **Kräv** att slutanvändaren måste ange ett lösenord för att få åtkomst till enheten. **Inte konfigurerad** låter användare komma åt enheten utan att ange ett lösenord.
  - **Enkla lösenord**: Välj **Blockera** om du vill kräva mer avancerade lösenord. **Inte konfigurerad** tillåter enkla lösenord som `0000` och `1234`.
  - **Krav på lösenordstyp**: Välj den typ av lösenord som din organisation kräver. Alternativen är:
    - **Standard för enheten**
    - **Numerisk**
    - **Alfanumerisk**
  - **Antal icke-alfanumeriska tecken i lösenord**: Ange det antal symboltecken i lösenordet (t.ex. `#` eller `@`) som måste ingå i lösenordet.
  - **Minsta längd på lösenord**: Ange den minsta längd som en användare måste ange (mellan 4 och 14 tecken).
  - **Antal felaktiga inloggningar innan enheten rensas**: Ange antalet felaktiga inloggningar som tillåts innan enheten rensas (mellan 1–11).
  - **Maximalt antal minuter efter skärmlås innan ett lösenord krävs**<sup>1</sup>: Ange hur länge enheten kan vara inaktiv innan användaren måste ange sitt lösenord på nytt. Om den tid som du anger är längre än vad som är angivet i enhetens inställningar, så ignorerar enheten den tid som du anger. Stöds på enheter med iOS 8.0 och senare.
  - **Maximalt antal minuter av inaktivitet innan skärmen låses**<sup>1</sup>: Ange det maximala antal minuter av inaktivitet som ska tillåtas på enheten innan skärmen låses. Om den tid som du anger är längre än vad som är angivet i enhetens inställningar, så ignorerar enheten den tid som du anger.
  - **Lösenordets giltighetstid (dagar)**: Ange antal dagar innan lösenordet för enheten måste ändras.
  - **Förhindra återanvändning av tidigare lösenord**: Ange hur många nya lösenord som måste ha använts innan ett gammalt kan återanvändas.
  - **Upplåsning med fingeravtryck**: Välj **Blockera** om du vill förhindra att fingeravtryck används för att låsa upp enheten. **Inte konfigurerad** låter användare låsa upp enheten med ett fingeravtryck.
- **Ändring av lösenkod (endast övervakat)**: Välj **Blockera** om du vill förhindra att lösenkoden ändras, läggs till eller tas bort. Ändringar av lösenkodsbegränsningar ignoreras på övervakade enheter när den här funktionen har blockerats. **Inte konfigurerad** (standard) tillåter att lösenord läggs till, ändras eller tas bort.

  - **Ändring av fingeravtryck (endast övervakat)**: **Blockera** stoppar användaren från att ändra, lägga till eller ta bort TouchID-fingeravtryck. **Inte konfigurerad** (standard) tillåter att användaren uppdaterar TouchID-fingeravtryck på enheten.

- **Blockera automatisk ifyllning av lösenord (endast övervakat)**: Välj **Blockera** om du vill förhindra att funktionen för automatisk ifyllning av lösenord används i iOS. När du väljer **Blockera** sker även följande:

  - Användarna ombeds inte att använda ett sparat lösenord i Safari eller i någon app.
  - Automatisk starka lösenord inaktiveras och starka lösenord föreslås inte för användare.

  **Inte konfigurerat** (standard) tillåter dessa funktioner.

- **Blockera förfrågningar om lösenordsnärhet (endast övervakat)**: Välj **Blockera** så att användarens enhet inte begär lösenord från enheter i närheten. **Inte konfigurerad** (standard) tillåter dessa lösenordsbegäranden.
- **Blockera lösenordsdelning (endast övervakat)**: **Blockera** förhindrar att lösenord delas mellan enheter med hjälp av AirDrop. **Inte konfigurerad** (standard) tillåter att lösenord delas.
- **Kräv Touch ID eller Face ID-autentisering för lösenord eller kreditkort information Autofyll (endast övervakat)**: när **kräver**, användare måste autentisera med hjälp av TouchID eller FaceID innan lösenord eller kreditkort informationen kan vara automatiskt ifylld Safari och andra appar. **Inte konfigurerad** (standard) kan du styra den här funktionen i enhetsinställningarna.

  Den här funktionen gäller för:  
  - iOS 11.0 and later

<sup>1</sup> När du konfigurerar **Maximalt antal minuter av inaktivitet innan skärmen låses** och **Maximalt antal minuter efter skärmlås innan ett lösenord krävs** tillämpas de i följd. Om du t.ex. ställer in värdet för båda inställningarna till **5** minuter så stängs skärmen av automatiskt efter fem minuter. Enheten låses efter ytterligare fem minuter. Om användaren däremot stänger av skärmen manuellt så tillämpas den andra inställningen omedelbart. När användaren i det här exemplet har stängt av skärmen låses enheten fem minuter senare.

## <a name="locked-screen-experience"></a>Låsskärm

- **Åtkomst till Kontrollcenter när enheten är låst**: Välj **Blockera** om du vill förhindra åtkomst till kontrollcenterappen när enheten är låst. **Inte konfigurerad** låter användare få åtkomst till kontrollcenterappen när enheten är låst.
- **Meddelanden när enheten är låst**: **Blockera** förhindrar åtkomst till meddelanden när enheten är låst. **Inte konfigurerad** tillåter användaren att få åtkomst till aviseringsvyn utan att låsa upp enheten.
- **Plånboksmeddelanden när enheten är låst**: **Blockera** förhindrar åtkomst till appen Plånbok när enheten är låst. **Inte konfigurerad** tillåter användare åtkomst till appen Plånbok när enheten är låst.
- **Dagsvyn när enheten är låst**: **Block** förhindrar åtkomst till vyn Idag när enheten är låst. **Inte konfigurerad** tillåter användaren att se vyn Idag när enheten är låst.

## <a name="app-store-doc-viewing-gaming"></a>App Store, dokumentvisning, spel

- **App Store**: **Blockera** förhindrar åtkomst till App Store på övervakade enheter. **Inte konfigurerad** tillåter åtkomst.
  - **Installera appar från App Store (endast övervakat)**: Välj **Blockera** om du vill blockera App Store från enhetens startskärm. Användarna kan fortsätta att använda iTunes eller Apple Configurator-verktyget för att installera appar. **Inte konfigurerad** tillåter att App Store visas på hemskärmen.
  - **Automatisk nedladdning av appar (endast övervakat)**: Välj **Blockera** om du vill förhindra automatisk nedladdning av appar som har köpts på andra enheter. Det påverkar inte uppdateringar av befintliga appar. **Inte konfigurerad** tillåter att appar som har köpts på andra iOS-enheter laddas ned på enheten.
- **Lösenord till App Store**: **Kräv** innebär att användaren måste ange ett lösenord innan hen kan besöka App Store. **Inte konfigurerad** möjliggör åtkomst till App Store utan användning av lösenord.
- **Köp i appar**: Välj **Blockera** om du vill förhindra att köp från butiken görs i appen. **Inte konfigurerad** tillåter köp i butiken från en app som körs.
- **Stötande musik, podcaster eller nyhetsinnehåll i iTunes (endast övervakat)**: Välj **Blockera** om du vill stoppa explicit iTunes-musik, podcaster eller nyhetsinnehåll. **Inte konfigurerad** tillåter att enheten får åtkomst till sådant som är klassificerat som vuxet innehåll i butiken.
- **Ladda ned innehåll från iBook-butiken flaggat som ”erotik”**: Välj **Blockera** om du vill förhindra användare från att ladda ned mediainnehåll som klassificeras som erotik från iBook-butiken. **Inte konfigurerad** tillåter att användare laddar ned böcker i kategorin Erotik.
- **Visa företagsdokument i ohanterade appar**: **Blockera** förhindrar visning av icke-företagsdokument i ohanterade appar. **Inte konfigurerad** tillåter visning av företagsdokument i vilken app som helst. Exempelvis vill du kanske förhindra användare från att spara filer från OneDrive-appen till Dropbox. Konfigurera den här inställningen som **Blockera**. När enheten har hämtat principen (t.ex. efter en omstart) kommer det inte längre att vara tillåtet att spara.
  - **Tillåt att hanterade appar att skriva kontakter till ohanterade kontakter konton**: när **Tillåt**, användarna kan lägga till och synkronisera en person Outlook kontaktinformation, inklusive företag och företagets kontakter till den inbyggda appen kontakter på enheten. När det är inställt på **Inte konfigurerad** kan användarna inte lägga till Outlook-kontakter i den inbyggda appen Kontakter på enheten.
  
    Om du vill använda inställningen ställer du in **Visa företagsdokument i ohanterade appar** på **Blockera**.
  
- **Visa icke-företagsdokument i ohanterade appar**: **Blockera** förhindrar visning av icke-företagsdokument i företagsappar. **Inte konfigurerad** tillåter visning av valfria dokument i företagshanterade appar.
  - **Tillåt ohanterade appar att läsa från hanterade kontakter konton**: när **Tillåt**, användare kan lägga till en person iContacts appen kontaktinformation till Outlook. **Inte konfigurerad** förhindrar läsning, inklusive ta bort dubbletter, från den inbyggda appen Kontakter på enheter.
  
    Om du vill använda inställningen ställer du in **Visa dokument som inte gäller företag i företagsappar** på **Blockera**.
  
- **Behandla AirDrop som ohanterat mål**: **Kräv** tvingar fram att AirDrop betraktas som ett ohanterat släppmål. Det förhindrar hanterade appar från att skicka data med hjälp av Airdrop. 
- **Lägga till Game Center-vänner (endast övervakat)**: **Blockera** förhindrar användare från att lägga till Game Center-vänner. **Inte konfigurerad** tillåter användaren att lägga till vänner i Game Center.
- **Game Center (endast övervakat)**: **Blockera** förhindrar användning av Game Center-appen. **Inte konfigurerad** tillåter användning av Game Center-appen på enheten.
- **Spel för flera personer (endast övervakat)**: Välj **Blockera** om du vill förhindra spel för flera personer. **Inte konfigurerad** tillåter användaren att spela spel för flera personer på enheten.
- **Klassificeringsregion**: Välj den klassificeringsregion som du vill använda för tillåtna hämtningsbara filer. Och välj sedan tillåtna klassificeringar för **filmer** och **TV-program**.
- **Appar**: Välj åldersklassificering för de appar som användarna kan ladda ned eller välj **Tillåt alla appar**.

## <a name="built-in-apps"></a>Inbyggda appar

- **Kamera**: Välj **Blockera** om du vill förhindra åtkomst till enhetens kamera. **Inte konfigurerad** ger åtkomst till enhetens kamera.
  - **FaceTime**: **Blockera** förhindrar åtkomst till FaceTime-appen. **Inte konfigurerad** tillåter åtkomst till FaceTime-appen på enheten.
- **Siri**: **Blockera** förhindrar åtkomst till Siri. **Inte konfigurerad** tillåter att röstassistenten Siri används på enheten.
  - **Siri när enheten är låst**: Välj **Blockera** om du vill förhindra åtkomst till Siri när enheten är låst. **Inte konfigurerad** tillåter att röstassistenten Siri används på enheten när den när låst.
  - **Filtrering av grovt språk i Siri (endast övervakat)**: **Kräv** förhindrar att Siri från dikterar eller talar ett olämpligt språk.
  - **Siri skickar frågor om innehåll som skapats av användare från Internet (endast övervakat)**: **Blockera** förhindrar Siri från att få åtkomst till webbplatser för att kunna besvara frågor. **Inte konfigurerad** tillåter Siri att få åtkomst till användargenererat innehåll på Internet.
- **Apple News (endast övervakat)**: Välj **Blockera** om du vill förhindra åtkomst till Apple News-appen på enheten. **Inte konfigurerad** tillåter att Apple News-appen används.
- **iBooks store (endast övervakat)**: **Blockera** förhindrar åtkomst till iBooks Store. **Inte konfigurerad** tillåter användare att söka efter och köpa böcker i iBooks Store.
- **Appen Meddelanden på enheten (endast övervakat)**: Välj **Blockera** så att användare inte kan använda appen Meddelanden på enheten. **Inte konfigurerad** tillåter att appen Meddelanden skickar och läser textmeddelanden.
- **Podcaster (endast övervakat)**: **Blockera** förhindrar användare från att använda appen Podcaster. **Inte konfigurerad** tillåter att Podcaster-appen används.
- **Tjänsten Musik (endast övervakat)**: **Blockera** återställer appen Apple Music till klassiskt läge och inaktiverar tjänsten Musik. **Inte konfigurerad** tillåter att Apple Music-appen används.
- **iTunes Radio-tjänsten (endast övervakat)**: **Blockera** förhindrar användare från att använda appen iTunes Radio. **Inte konfigurerad** tillåter att iTunes Radio-appen används.
- **Ändringar av inställningarna för appen Find My Friends (endast övervakat)**: **Blockera** förhindrar att inställningarna för appen Find My Friends ändras. **Inte konfigurerad** tillåter att användaren ändrar inställningarna för appen Find My Friends.
- **Spotlight-sökning som returnerar resultat från Internet (endast övervakat)**: **Blockera** förhindrar Spotlight från att returnera resultat från sökningar på Internet. **Inte konfigurerad** tillåter att Spotlight-sökningar ansluter till Internet för att kunna visa ytterligare sökresultat.
- **Blockera borttagning av systemappar från enheten (endast övervakat)**: Om du väljer **Blockera** inaktiverar du möjligheten att ta bort systemappar från enheten. **Inte konfigurerad** tillåter användarna att ta bort systemappar från enheten.

#### <a name="safari"></a>Safari

- **Safari**: **Blockera** webbläsaren Safari från att användas på enheten. **Inte konfigurerad** tillåter användarna att använda webbläsaren Safari.
- **Autofyll**: **Blockera** inaktiverar funktionen Autofyll i Safari på enheten. **Inte konfigurerad** tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren.
- **Cookies**: Välj hur cookies ska hanteras på enheten. Alternativen är:
  - Tillåt
  - Blockera alla cookies
  - Tillåt cookies från besökta webbplatser
  - Tillåt cookies från aktuell webbplats
- **JavaScript**: **Blockera** förhindrar att Java-skript i webbläsaren körs på enheten. **Inte konfigurerad** tillåter Java-skript.
- **Bedrägerivarningar**: **Kräv** att bedrägerivarningar ska visas i webbläsaren på enheten. **Inte konfigurerad** inaktiverar den här funktionen.
- **Popup-fönster**: **Blockera** så att blockering av popup-fönster inaktivas i webbläsaren. **Inte konfigurerad** tillåter popup-blockeraren.

## <a name="restricted-apps"></a>Begränsade appar

Du kan konfigurera en av följande listor i listan med begränsade appar:

- **Otillåtna appar**: En lista över appar som inte hanteras av Intune som du inte vill ha installerade på enheten. Om en användare installerar en app från den här listan kommer Intune att meddela dig.
- **Godkända appar**: En lista över de appar som användare tillåts att installera. Om användarna vill fortsätta följa standard får de inte installera andra appar. Appar som hanteras av Intune tillåts automatiskt. Om en användare installerar en app från den här listan kommer Intune att meddela dig.

Om du vill lägga till appar i listorna kan du:

- **Lägga till** iTunes App Store-webbadressen för den önskade appen. Om du t.ex. vill lägga till appen Microsoft Work Folders anger du `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Du hittar webbadressen till en app genom att öppna iTunes App Store och söka efter appen. Du kan t.ex. söka efter `Microsoft Remote Desktop` eller `Microsoft Word`. Välj appen och kopiera webbadressen.

  Du kan även använda iTunes för att hitta appen och sedan använda uppgiften **Kopiera länk** för att hämta appens webbadress.

- Importera en CSV-fil med information om appen, inklusive webbadressen. Använd formatet `<app url>, <app name>, <app publisher>`. Eller exportera en befintlig lista som innehåller listan över begränsade appar i samma format.

> [!IMPORTANT]
> Enhetsprofiler som använder inställningar för begränsade appar måste tilldelas grupper av användare.

## <a name="show-or-hide-apps-supervised-only"></a>Visa eller dölj appar (endast övervakat)

I listan för att visa eller dölja appar kan du konfigurera en av följande listor på övervakade enheter som kör iOS 9.3 eller senare.

- **Dolda appar**: Ange en lista med appar som är dolda för användarna. Användarna kan varken visa eller öppna de här apparna.
- **Synliga appar**: Ange en lista med appar som användarna ska kunna se och starta. Inga andra appar kan visas eller startas.

Om du vill lägga till appar i listorna kan du:

- **Lägga till** iTunes App Store-webbadressen för den önskade appen. Om du t.ex. vill lägga till appen Microsoft Work Folders anger du `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Du hittar webbadressen till en app genom att öppna iTunes App Store och söka efter appen. Du kan t.ex. söka efter `Microsoft Remote Desktop` eller `Microsoft Word`. Välj appen och kopiera webbadressen.

  Du kan även använda iTunes för att hitta appen och sedan använda uppgiften **Kopiera länk** för att hämta appens webbadress.

- Importera en CSV-fil med information om appen, inklusive webbadressen. Använd formatet `<app url>, <app name>, <app publisher>`. Eller exportera en befintlig lista som innehåller listan över begränsade appar i samma format.

## <a name="wireless"></a>Trådlöst

- **Dataroaming**: Välj **Blockera** om du vill förhindra dataroaming över det mobila nätverket. **Inte konfigurerad** (standard) tillåter dataroaming när enheten är i ett mobilnät.
- **Global bakgrundssamling under nätverksväxling**: **Blockera** förhindrar att funktionen för global bakgrundssamling används under nätverksväxling i mobilnätverket. **Inte konfigurerad** (standard) tillåter att enheten hämtar data, till exempel e-post, när den nätverksväxlar i ett mobilnät.
- **Röstsamtal**: Välj **Blockera** om du vil förhindra användare från att använda enhetens röstsamtalsfunktion. **Inte konfigurerad** (standard) tillåter röstsamtal på enheten.
- **Röstroaming**: Välj **Blockera** om du vill förhindra röstroaming över det mobila nätverket. **Inte konfigurerad** (standard) tillåter röstroaming när enheten är i ett mobilnät.
- **Ändringar i inställningarna för användning av appmobildata (endast övervakat)**: Välj **Blockera** om du vill förhindra att inställningarna för användning av appmobildata ska kunna ändras. **Inte konfigurerad** (standard) tillåter att användaren bestämmer vilka appar som ska få använda mobildata.
- **Ändringar i mobila schemainställningar (endast övervakat)**: **blockera** förhindrar att användare ändrar inställningar i mobila planen. **Inte konfigurerad** (standard) kan du göra ändringar.

  Den här funktionen gäller för:  
  - iOS 11.0 and later

- **Internetdelning**: **Blockera** förhindrar att enheten används för Internetdelning. Den här inställningen kanske inte är kompatibel med vissa operatörer. **Inte konfigurerad** (standard) kan den här funktionen.
- **Anslut till trådlösa nätverk med endast konfigurationsprofiler (endast övervakat)**: **Kräv** tvingar enheten att endast använda trådlösa nätverk som har konfigurerats med Intunes konfigurationsprofiler. **Inte konfigurerad** (standard) tillåter enheten att använda andra trådlösa nätverk.
- **Regler för mobilanvändning (endast hanterade appar)**: Definiera de datatyper som hanterade appar kan använda i mobilnät. Alternativen är:
  - **Blockera användning av mobildata**: Blockera användningen av mobildata för **Alla hanterade appar** eller **Välj särskilda appar**.
  - **Blockera användning av mobildata vid nätverksväxling**: Blockera användningen av mobildata vid nätverksväxling för **Alla hanterade appar** eller **Välj särskilda appar**.

## <a name="connected-devices"></a>Anslutna enheter

- **AirDrop (endast övervakat)**: **Blockera** förhindrar att du använder AirDrop på enheten. **Inte konfigurerad** (standard) tillåter att funktionen AirDrop används för att utbyta innehåll med enheter i närheten.
- **Apple Watch-parkoppling (endast övervakat)**: **Blockera** förhindrar att enheten parkopplas med en Apple Watch. **Inte konfigurerad** (standard) tillåter att enheten parkopplas med en Apple Watch.
- **Handledsavkänning för parkopplad Apple Watch**: **Kräv** tvingar en parkopplad Apple Watch att använda handledsavkänning. När så krävs visar inte Apple Watch meddelanden när den inte bärs runt handleden. 
- **Ändring av Bluetooth (endast övervakat)**: **Blockera** förhindrar att slutanvändaren från att ändra enhetens Bluetooth-inställningar. **Inte konfigurerad** (standard) tillåter att användaren ändrar dessa inställningar.
- **Parkoppling av värd för att styra de enheter som en iOS-enhet kan parkopplas till (endast övervakat)**: **Inte konfigurerad** (standard) tillåter parkoppling så att administratören kan kontrollera vilka enheter som en iOS-enhet kan kopplas med. **Blockera** förhindrar parkoppling av värd.
- **Kräv parkopplingslösenord för utgående AirPlay-förfrågningar**: **Kräv** ett parkopplingslösenord när användaren använder AirPlay för att strömma innehåll till andra Apple-enheter. **Inte konfigurerad** (standard) tillåter att användaren strömmar innehåll med AirPlay utan att behöva ange något lösenord.
- **Blockera AirPrint (endast övervakat)**: Välj **Blockera** om du vill förhindra att AirPrint-funktionen används på enheten. **Inte konfigurerat** (standard) tillåter användaren att använda AirPrint.
  - **Blockera lagring av AirPrint-autentiseringsuppgifter i nyckelringen (endast övervakat)**: **Blockera** förhindrar användning av nyckelring vid lagring av användarnamn och lösenord på enheten. **Inte konfigurerad** (standard) tillåter att AirPrint-användarnamnet och lösenordet lagras i nyckelringsappen.
  - **Kräv ett betrott TLS-certifikat för AirPrint (endast övervakat)**: **Kräv** tvingar enheten att använda betrodda certifikat för TLS-utskriftskommunikation.
  - **Blockera iBeacon-identifiering av AirPrint-skrivare (endast övervakat)**: **Blockera** förhindrar skadliga AirPrint Bluetooth-sändare från att nätfiska nätverkstrafik. **Inte konfigurerad** (standard) tillåter reklam för AirPrint-skrivare på enheten.
- **Blockerar inställningen upp nya Närliggande enheter (endast övervakat)**: **blockera** inaktiverar uppmaningen om att konfigurera nya enheter som är i närheten. **Inte konfigurerad** (standard) gör att anvisningarna för användare att ansluta till andra Apple-enheter i närheten.

  Den här funktionen gäller för:  
  - iOS 11.0 and later

## <a name="keyboard-and-dictionary"></a>Tangentbord och ordlista

- **Orddefinitionssökning (endast övervakat)**: **Blockera** förhindrar användare från att markera ett ord och sedan söka upp dess definition på enheten. **Inte konfigurerad** ger åtkomst till definitionssökningsfunktionen.
- **Tangentbord med förslag (endast övervakat)**: **Inte konfigurerad** tillåter tangentbord med förslag på ord som användaren kan ha nytta av. **Blockera** förhindrar den här funktionen.
- **Autokorrigering (endast övervakat)**: **Inte konfigurerad** låter enheten automatiskt korrigera felstavade ord. **Blockera** förhindrar att autokorrigering används.
- **Tangentbord med stavningskontroll (endast övervakat)**: **Inte konfigurerad** tillåter att stavningskontroll används på enheten. **Blockera** tillåter stavningskontroll.
- **Kortkommandon (endast övervakat)**: **Inte konfigurerad** tillåter att kortkommandon används på enheten. **Blockera** hindrar användaren från att använda kortkommandon.
- **Diktering (endast övervakat)**: **Blockera** hindrar användaren från att använda röstindata för att ange text. **Inte konfigurerat** tillåter användaren att använda röstindata.

## <a name="cloud-and-storage"></a>Moln och lagring

- **Säkerhetskopiera till iCloud**: **Inte konfigurerad** tillåter användaren att säkerhetskopiera enheten till iCloud. **Blockera** hindrar användaren från att säkerhetskopiera enheten till iCloud.
- **Blockera iCloud-dokumentsynkronisering**: **Inte konfigurerad** tillåter synkronisering av dokument och nyckelvärden till ditt lagringsutrymme i iCloud. **Blockera** förhindrar iCloud från att synkronisera dokument och data.
- **Synkronisering av bildström till iCloud**: **Inte konfigurerad** låter användarna aktivera **My Photo Stream** på sina enheter och synkroniseras med iCloud och låta foton vara tillgängliga på användarens alla enheter. **Blockera** förhindrar bildströmssynkronisering till iCloud.
- **Krypterad säkerhetskopiering**: **Kräv** att säkerhetskopior av enheter måste vara krypterade.
- **iCloud-bildbiblioteket**: Ställ in på **Blockera** om du vill inaktivera användning av iCloud-bildbiblioteket för att lagra foton och videoklipp i molnet. Alla bilder som inte har laddats ned till fullo från iCloud-bildbiblioteket till enheten tas bort från enheten. **Inte konfigurerad** tillåter att iCloud-bildbiblioteket används.
- **Synkronisering av hanterade appar till molnet**: **Inte konfigurerad** tillåter att appar som du hanterar med Intune synkroniserar data till användarens iCloud-konton. **Blockera** förhindrar denna datasynkronisering till iCloud.
- **Delad bildström**: Välj **Blockera** om du vill inaktivera **iCloud-bilddelning** på enheten. **Inte konfigurerad** tillåter delad bildström.
- **Aktivitetsfortsättning**: **Inte konfigurerad** tillåter användare att återuppta det arbete som de påbörjat på en iOS-enhet på en annan iOS- eller macOS-enhet (överlämning). **Blockera** förhindrar den här överlämningen.
- **Blockera synkronisering av iCloud-nyckelring**: Välj **Blockera** om du vill inaktivera synkronisering av autentiseringsuppgifter som lagras i nyckelringen till iCloud. **Inte konfigurerad** tillåter användare att ändra dessa autentiseringsuppgifter.
- **Blockera säkerhetskopiering av företagsbok**: Välj **Blockera** om du vill förhindra användarna från att säkerhetskopiera företagsböcker. **Inte konfigurerad** tillåter användarna att säkerhetskopiera dessa böcker.
- **Blockera synkronisering av företagsboksmetadata (anteckningar och markeringar)**: **Blockera** förhindrar synkronising av anteckningar och markeringar i företagsböcker. **Inte konfigurerad** tillåter synkroniseringen.

## <a name="autonomous-single-app-mode-supervised-only"></a>Autonomt enkelt appläge (endast övervakat)

Använd inställningarna för att konfigurera iOS-enheter så att de kör specifika appar i autonomt enkelappsläge. När det här läget har konfigurerats och appen körs låses enheten. Bara den appen kan köras. Lägg t.ex. till en app som låter användarna göra ett prov på enheten. När appens åtgärder har slutförts, eller om du tar bort principen, återgår enheten till sitt normala tillstånd.

Om du vill lägga till appar kan du:

- Ange **appnamn** och **appsamlings-ID** och välj **Lägg till**. [Samlings-ID:n för inbyggda iOS-appar](#bundle-ids-for-built-in-ios-apps) (i den här artikeln) inkluderar några appar och deras ID:n.
- **Importera** en CSV-fil med listan över appnamn och deras samlings-ID:n. Eller **exportera** en befintlig lista som innehåller dessa appar.

## <a name="kiosk-supervised-only"></a>Helskärm (endast övervakat)

- **App för att köra i helskärmsläge**: Välj den apptyp som du vill köra i helskärmsläge. Alternativen är:
  - **Inte konfigurerad**: inställningar för helskärmsläge tillämpas inte. Enheten körs inte i helskärmsläge.
  - **Store App**: Ange webbadressen till en app i iTunes App Store.
  - **Hanterad app**: Välj en app som du lagt till i Intune.
  - **Inbyggd App**: Ange den [appsamlings-ID](#bundle-ids-for-built-in-ios-apps) (i den här artikeln) på den inbyggda appen.

- **AssistiveTouch**: **Kräv** att hjälpmedelsinställningen för AssistiveTouch ska finnas på enheten. Den här funktionen hjälper användarna med skärmgester som de behöver hjälp med. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Invertera färger**: **Kräv** att hjälpmedelsinställningen Invertera färger ska användas, så att användare med synsvårigheter kan anpassa skärmen. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Monoljud**: **Kräv** att hjälpmedelsinställningen för Monoljud ska finnas på enheten. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **VoiceOver**: **Kräv** att hjälpmedelsinställningen VoiceOver ska finnas på enheten så att text på skärmen kan läsas upp. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Zooma**: **Kräv** att zoominställningen ska finnas på enheten så att användarna kan använda pekskärmen för att zooma in på skärmen. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Autolås**: **Tillåt** automatisk låsning av enheten. **Inte konfigurerad** inaktiverar den här funktionen.
- **Ringsignalsknapp**: **Tillåt** att ringsignalsknappen används på enheten. **Inte konfigurerad** inaktiverar den här funktionen.
- **Skärmrotation**: **Tillåt** att skärmrotationen ändras när användaren roterar enheten. **Inte konfigurerad** inaktiverar den här funktionen.
- **Viloläge för skärm-knapp**: Välj **Tillåt** om du vill inaktivera enhetens knapp för viloläge. **Inte konfigurerad** aktiverar den här funktionen.
- **Touch**: **Blockera** inaktiverar enhetens pekskärm. **Inte konfigurerad** tillåter användaren att använda pekskärmen.
- **Inte konfigurerad**: **Tillåt** att enhetens volymknappar används. **Inte konfigurerad** inaktiverar volymknapparna.
- **Assistivetouch-knapp**: **Tillåt** låter användarna använda funktionen AssistiveTouch. **Inte konfigurerad** inaktiverar den här funktionen.
- **Invertera färger**: **Tillåt** ändringar av färginvertering så att användarna kan justera funktionen för färginvertering. **Inte konfigurerad** inaktiverar den här funktionen.
- **Läs upp markerad text**: **Tillåt** att hjälpmedelsinställningen Läs upp markering finns på enheten. Den här funktionen läser upp text som användaren väljer. **Inte konfigurerad** inaktiverar den här funktionen.
- **VoiceOver-knapp**: **Tillåt** VoiceOver-ändringar så att användarna kan uppdatera VoiceOver-funktionen, t.ex. när det gäller hur snabbt texten ska läsas upp. **Inte konfigurerad** förhindrar VoiceOver-ändringar.
- **Zoomkontroll**: **Tillåt** att användaren kan ändra zoominställningarna. **Inte konfigurerad** förhindrar zoominställningar.

> [!NOTE]
> Innan du kan konfigurera en iOS-enhet för helskärmsläge måste du använda Apple Configurator-verktyget eller Apples enhetsregistreringsprogram för att placera enheten i övervakat läge. Information om hur du använder Apple Configurator-verktyget finns i Apples guide.
> Om den iOS-appen som du anger har installerats efter det att du har tilldelat profilen så går inte enheten över i helskärmsläge förrän den startas om.

## <a name="domains"></a>Domains

- **Omarkerade e-postdomäner** > **e-Domänwebbadress**: lägga till en eller flera webbadresser i listan. När slutanvändarna får ett e-postmeddelande från en annan domän än någon av de du har angett, så markeras e-postmeddelandet som ej betrott i iOS-e-postappen.

- **Hanterade webbdomäner** > **webbadress till Webbdomän**; Lägg till en eller flera webbadresser i listan. Dokument som laddas ned från de domäner du anger här anses vara hanterade. Den här inställningen gäller enbart för dokument som hämtas i Safari-webbläsaren.

- **Autofyll lösenord Safari-domäner** > **Domänwebbadress**: lägga till en eller flera webbadresser i listan. Användarna kan bara spara webblösenord från webbadresser i den här listan. Den här inställningen gäller enbart för Safari-webbläsaren, samt för iOS 9.3 och senare enheter i övervakat läge. Om du inte anger någon webbadress, kan lösenorden sparas från alla webbplatser.

## <a name="bundle-ids-for-built-in-ios-apps"></a>Samlings-ID för inbyggda iOS-appar

I följande lista visas appsamlings-ID:n för några vanliga inbyggda iOS-appar. Kontakta programvaruleverantören för att hitta appsamlings-ID:n för andra appar.

| Samlings-ID                   | Appnamn     | Utgivare |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | Appbutik    | Apple     |
| com.apple.calculator        | Kalkylator   | Apple     |
| com.apple.mobilecal         | Kalender     | Apple     |
| com.apple.camera            | Kamera       | Apple     |
| com.apple.mobiletimer       | Klocka        | Apple     |
| com.apple.compass           | Kompass      | Apple     |
| com.apple.MobileAddressBook | Kontakter     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Filer        | Apple     |
| com.apple.mobileme.fmf1     | Hitta vänner | Apple     |
| com.apple.mobileme.fmip1    | Hitta iPhone  | Apple     |
| com.apple.gamecenter        | Spelcenter  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Hälsa       | Apple     |
| com.apple.Home              | Hem         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | E-post         | Apple     |
| com.apple.Maps              | Kartor         | Apple     |
| com.apple.MobileSMS         | Meddelanden     | Apple     |
| com.apple.Music             | Musik        | Apple     |
| com.apple.news              | Nyheter         | Apple     |
| com.apple.mobilenotes       | Obs!        | Apple     |
| com.apple.Numbers           | Siffror      | Apple     |
| com.apple.Pages             | Sidor        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Foton       | Apple     |
| com.apple.podcasts          | Poddsändningar     | Apple     |
| com.apple.reminders         | Påminnelser    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Inställningar     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Aktier       | Apple     |
| com.apple.tips              | Tips         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | Videor       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Plånbok       | Apple     |
| com.apple.Bridge            | Titta på        | Apple     |
| com.apple.weather           | Väder      | Apple     |

## <a name="settings-that-require-supervised-mode"></a>Inställningar som kräver övervakat läge

Övervakat läge för iOS kan bara aktiveras under den inledande enhetsinställningen via Apples program för enhetsregistrering eller med hjälp av Apple Configurator. När du har aktiverat övervakat läge kan Intune konfigurera en enhet med följande funktioner:

- Applås (enkelt appläge) 
- Global HTTP-proxy 
- Kringgå aktiveringslås 
- Autonomt enkelt appläge 
- Webbinnehållsfilter 
- Ange bakgrund och låsskärm 
- Tyst app-push 
- VPN alltid på 
- Tillåt exklusiv installation av hanterad app 
- iBookstore 
- iMessages 
- Spelcenter 
- Airdrop 
- AirPlay 
- Värdkoppling 
- Molnsynkronisering 
- Spotlight-sökning 
- Handoff 
- Radera enhet 
- Begränsningar för gränssnitt 
- Installation av konfigurationsprofiler genom gränssnittet 
- Nyheter 
- Kortkommandon 
- Ändringar av lösenord 
- Ändringar av enhetsnamn 
- Automatisk nedladdning av appar 
- Ändringar till förtroende för företagsapp 
- Apple Music 
- Mail Drop 
- Koppla med Apple Watch 

> [!NOTE]
> Apple har bekräftat att vissa inställningar flyttas till endast övervakat läge under 2019. Vi rekommenderar att du tänker på detta när du använder de här inställningarna i stället för att vänta på att Apple ska migrera dem till endast övervakat läge:
> - Appinstallation av slutanvändare
> - Borttagning av app
> - FaceTime
> - Safari
> - iTunes
> - Barnförbjudet innehåll
> - Dokument och data i iCloud
> - Spel för flera personer
> - Lägg till spelcentervänner
> - Siri

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också begränsa enhetens funktioner och inställningar på [macOS](device-restrictions-macos.md) enheter.