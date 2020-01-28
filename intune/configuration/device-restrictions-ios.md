---
title: iOS-enhetsinställningar i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till, konfigurera eller skapa inställningar på iOS-enheter när du vill begränsa funktioner, till exempel lösenordskrav, kontrollera låst skärm, använda inbyggda appar, lägga till begränsade eller godkända appar, hantera bluetooth-enheter, ansluta till molnet för säkerhetskopiering och lagring, aktivera helskärmsläge, lägga till domäner och kontrollera hur användarna samverkar med Safari-webbläsaren i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/13/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39978043428f6ad912832007f60628815d6549a6
ms.sourcegitcommit: fb72b19986f34907d228c856d2e6949751ec02a1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75920081"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>Enhetsinställningarna för iOS och iPadOS tillåter eller begränsar funktioner med hjälp av Intune

Den här artikeln beskriver de olika inställningar som du kan styra på iOS- och iPadOS-enheter. Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar för att tillåta eller inaktivera funktioner, ange lösenordsregler, tillåta eller begränsa specifika appar med mera.

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina iOS-enheter.

> [!TIP]
> De här inställningarna använder Apples MDM-inställningar. Mer information om de här inställningarna finns i [Apples inställningar för hantering av mobilenheter](https://support.apple.com/guide/mdm/welcome/web) (öppnar Apples webbplats).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en konfigurationsprofil för enhetsbegränsningar](../device-restrictions-configure.md).

> [!NOTE]
> Dessa inställningar gäller för olika registreringstyper. Vissa inställningar gäller för alla registreringsalternativ. Mer information om de olika registreringstyperna finns i [iOS-registrering](../ios-enroll.md).

## <a name="general"></a>Allmänt

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registreringstyper

- **Dela användningsdata**: Välj **Blockera** för att förhindra enheten från att skicka diagnostik- och användningsdata till Apple. **Inte konfigurerad** (standard) tillåter att dessa data skickas.

- **Skärmdump**: Välj **Blockera** för att förhindra skärmbilder eller skärmdumpar på enheten. I iOS 9.0 och senare blockeras även skärminspelningar. **Inte konfigurerad** (standard) låter användaren spara skärminnehållet som en bild eller video.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

- **Ej betrodda TLS-certifikat**: Välj**Blockera** om du vill stoppa ej betrodda TLS-certifikat på enheten. **Inte konfigurerad** (standard) tillåter TLS-certifikat.
- **Blockera trådlösa PKI-uppdateringar**: **Blockera** hindrar användarna från att ta emot programuppdateringar om inte enheten är ansluten till en dator. **Inte konfigurerad** (standard): tillåter att en enhet tar emot programuppdateringar utan att vara ansluten till en dator.
- **Begränsa reklamspårning**: Välj **Begränsa** om du vill inaktivera enhetens reklamidentifierare. **Inte konfigurerad** (standard) gör att den förblir aktiverad.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **Ändring av inställningar för att skicka diagnostik**: **Blockera** hindrar användaren från att ändra inställningarna för diagnostiköverföring och appanalys i **Diagnostik och användning** (enhetsinställningar). **Inte konfigurerad** (standard) tillåter att användaren ändrar dessa enhetsinställningar.

  Om du vill använda den här inställningen anger du inställningen **Dela användningsdata** till **Blockera**.

  Den här funktionen gäller för:  
  - iOS 9.3.2 och senare

- **Fjärrskärmsvisning via appen Klassrum**: Välj **Blockera** om du vill förhindra appen Klassrum från att visa skärmarna på fjärranslutna enheter. **Inte konfigurerad** (standard) tillåter appen Apple Klassrum att visa skärmen.

  Om du vill använda den här inställningen anger du inställningen **Skärmdump** till **Blockera**.

  Den här funktionen gäller för:  
  - iOS 9.3 och senare

- **Skärmvisning utan uppmaning via appen Klassrum**: Om det är inställt på **Tillåt** kan lärarna tyst övervaka skärmarna på elevernas iOS-enheter med hjälp av appen Klassrum utan att eleverna vet om det. Elevenheter som registrerats i en klass som använder appen Klassrum ger automatiskt behörighet till den kursens lärare. **Inte konfigurerad** (standard) förhindrar den här funktionen.

  Om du vill använda den här inställningen anger du inställningen **Skärmdump** till **Blockera**.

- **Företagsappförtroende**: Välj **Blockera** om du vill ta bort knappen **Lita på företagsutvecklare** i Inställningar > Allmänt > Profiler och enhetshantering på enheten. **Inte konfigurerad** (standard) tillåter att användaren väljer att lita på appar som inte laddats ned från App Store.
- **Kontoändring**: När det är inställt på **Blockera** kan användaren inte uppdatera enhetsspecifika inställningar från iOS-appens inställningar. Användaren kan t.ex. skapa nya enhetskonton eller ändra användarnamn eller lösenord. **Inte konfigurerad** (standard) tillåter användare att ändra dessa inställningar.

  Den här funktionen gäller även för inställningar som kan nås från appen för iOS-inställningar, som E-post, Kontakter, Kalender, Facebook, Twitter med flera. Den här funktionen gäller inte för appar med kontoinställningar som inte konfigureras från appen för iOS-inställningar, som Microsoft Outlook-appen.

- **Skärmtid**: Välj **Blockera** om du vill hindra användare från att ange sina egna begränsningar i Skärmtid (enhetsinställningar). **Inte konfigurerad** tillåter att användaren konfigurerar enhetsbegränsningar (till exempel kontrollfunktioner för föräldrar eller innehålls- och sekretessbegränsningar) på enheten.

  Den här inställningen har bytt namn från **Aktivera begränsningar i enhetsinställningarna**. Effekten av ändringen:  
  
  - iOS 11.4.1 och tidigare: **Blockera** förhindrar slutanvändare att ange egna begränsningar i enhetsinställningarna. Beteendet är detsamma. Ingenting har ändrats för slutanvändarna.
  - iOS 12.0 och senare: **Blockera** hindrar slutanvändarna från att ange sin egen **skärmtid** i enhetsinställningarna (Inställningar > Allmänt > Skärmtid), inklusive innehålls- och sekretessbegränsningar. På enheter som har uppgraderats till iOS 12.0 visas inte längre fliken Begränsningar i enhetsinställningarna (Inställningar > Allmänt > Enhetshantering > Hanteringsprofil > Begränsningar). Dessa inställningar finns i **Skärmtid**.
  
- **Användning av alternativet Radera allt innehåll och inställningar på enheten**: Välj **Blockera** så att användarna inte kan alternativet att radera allt innehåll och inställningar på enheten. **Inte konfigurerad** (standard) ger användarna åtkomst till de här inställningarna.
- **Ändra enhetsnamn**: Välj **Blockera** så att enhetsnamnet inte kan ändras. **Inte konfigurerad** (standard) tillåter användaren att ändra enhetens namn.
- **Ändring av notisinställningar**: Välj **Blockera** så att meddelandeinställningarna inte kan ändras. **Inte konfigurerad** (standard) tillåter användaren att ändra enhetens meddelandeinställningar.
- **Ändring av bakgrundsbild**: **Blockera** förhindrar att bakgrundsbilden ändras. **Inte konfigurerad** (standard) tillåter användaren att ändra enhetens bakgrundsbild.
- **Ändringar av inställningar för att lita på företagsappar**: **Blockera** förhindrar användaren att ändra behörighetsinställningar i företagsappen på övervakade enheter. **Inte konfigurerad** (standard) tillåter användaren att lita på appar som inte laddats ned från App Store.
- **Ändra konfigurationsprofil**: **Blockera** förhindrar ändringar av konfigurationsprofilen på enheten. **Inte konfigurerad** (standard) tillåter användaren att installera konfigurationsprofiler.
- **Aktiveringslås**: Välj **Tillåt** för att aktivera aktiveringslåset på övervakade iOS-enheter. Aktiveringslåset gör det svårare att återaktivera en förlorad eller stulen enhet.
- **Blockera borttagning av app**: Välj **Blockera** för att förhindra att användarna tar bort appar. **Inte konfigurerad** (standard) tillåter användaren att ta bort appar från enheten.
- **Tillåt USB-tillbehör när enheten är låst**: **Tillåt** låter USB-tillbehör utbyta data med en enhet som har varit låst i över en timme. **Inte konfigurerad** (standard) uppdaterar inte USB-begränsat läge på enheten och USB-tillbehören kommer att blockeras från att överföra data från enheten om den är låst i mer än en timme.
- **Tvinga automatiskt datum och tid**: **Kräv** tvingar övervakade enheter att ange datum och tid automatiskt. Enhetens tidszon uppdateras när enheten har mobila anslutningar eller har aktiverats för Wi-Fi med platstjänster.
- **Kräv att deltagarna begär tillstånd för att lämna Klassrumskursen**: **Kräv** tvingar elever som har registrerats i en ohanterad kurs med appen Klassrum att begära tillstånd från läraren om att lämna kursen. **Inte konfigurerad** (standard) tvingar inte eleven att be om behörighet.

  Den här funktionen gäller för:  
  - iOS 11.3 och senare

- **Tillåt Klassrum att låsa en app och låsa enheten utan att fråga**: **Aktivera** tillåter att lärare låser appar eller låser enheten med hjälp av Classroom-appen utan att fråga eleven. Applåsning innebär att enheten endast kan komma åt de appar som anges av läraren. **Inte konfigurerad** (standard) förhindrar att lärare låser appar eller enheter med hjälp av Classroom-appen utan att fråga eleven.

  Den här funktionen gäller för:  
  - iOS 11.0 och senare

- **Delta automatiskt i klassrumsklasser utan att fråga**: **Aktivera** tillåter automatiskt elever att ansluta till en klass i Classroom-appen utan att fråga läraren. **Inte konfigurerad** (standard) uppmärksammar lärare på att elever vill ansluta till en klass i Classroom-appen.

  Den här funktionen gäller för:  
  - iOS 11.0 och senare

- **Blockera möjlighet att skapa VPN**: **Blockera** förhindrar användare från att skapa VPN-konfigurationsinställningar. **Inte konfigurerad** (standard) tillåter användare att skapa virtuella privata nätverk på enheten.
- **Ändrar eSIM-inställningar**: **Blockera** hindrar användarna från att ta bort eller lägga till ett mobilabonnemang till eSIM på enheten. **Inte konfigurerad** (standard) tillåter användare att ändra dessa inställningar.

  Den här funktionen gäller för:  
  - iOS 12.1 och senare

- **Skjut upp programuppdateringar**: När **Inte konfigurerad** (standard) används visas programuppdateringar på enheten när de ges ut av Apple. Om en iOS-uppdatering exempelvis släpps av Apple på ett specifikt datum, visas uppdateringen på enheten runt utgivningsdatumet.

  **Aktivera** gör att du kan skjuta upp visningen av programuppdateringar på enheter i 0–90 dagar. Den här inställningen styr inte när uppdateringar installeras eller inte. 

  - **Fördröj visning av programuppdateringar**: Ange ett värde mellan 0–90 dagar. När fördröjningen upphör får användarna ett meddelande om att uppdatera till den tidigaste versionen av OS som var tillgänglig när fördröjningen utlöstes.

    Om iOS 12.a exempelvis blir tillgänglig **den 1 januari** och **Fördröj synlighet** är inställt på **5 dagar**, visas inte iOS 12.som en tillgänglig uppdatering på slutanvändarnas enheter. På **den sjätte dagen** efter utgivningen är uppdateringen tillgänglig och slutanvändarna kan installera den.

    Den här inställningen gäller för:  
    - iOS 11.3 och senare

## <a name="password"></a>lösenordsinställning

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registreringstyper

- **Lösenord**: Slutanvändaren **måste** ange ett lösenord för att få åtkomst till enheten. **Inte konfigurerad** (standard) låter användare komma åt enheten utan att ange ett lösenord.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

> [!IMPORTANT]
> Om du konfigurerar en lösenordsinställning på en enhet som registreras via Användarregisterring används automatiskt inställningen **Blockera** för **Enkla lösenord**, och en 6-siffrig PIN-kod krävs.
>
> Du kan till exempel konfigurera inställningen **Lösenordets giltighetstid** och skicka den här principen till användarregistrerade enheter. Följande händer på enheterna:
>
> - Inställningen **Lösenordets giltighetstid** ignoreras.
> - Enkla lösenord, till exempel `1111` eller `1234`, tillåts inte.
> - En 6-siffrig PIN-kod krävs.

- **Enkla lösenord**: Välj **Blockera** om du vill kräva mer avancerade lösenord. **Inte konfigurerad** tillåter enkla lösenord som `0000` och `1234`.

- **Lösenordstyp som krävs**: Välj den typ av lösenord som din organisation kräver. Alternativen är:
  - **Standard för enheten**
  - **Numerisk**
  - **Alfanumerisk**
- **Antal icke-alfanumeriska tecken i lösenord**: Ange antalet symboltecken (till exempel `#` eller `@`) som måste tas med i lösenordet.

- **Minsta lösenordslängd**: Ange den minsta längden som en användare måste ange, mellan 4 och 14 tecken. På användarregistrerade enheter anger du en längd på mellan 4 och 6 tecken.
  
  > [!NOTE]
  > För enheter som är användarregistrerade kan användare ange en PIN-kod med fler än 6 siffror. Dock tillämpas högst 6 siffror på enheten. Till exempel anger en administratör minimilängden till `8`. På användarregistrerade enheter behöver användarna bara ange en 6-siffrig PIN-kod. Intune framtvingar inte en PIN-kod som har fler än 6 siffror på användarregistrerade enheter.

- **Antal felaktiga inloggningar innan enheten rensas**: Anger antalet tillåtna felinloggningar innan enheten rensas (mellan 4 och 11).
  
  iOS har inbyggd säkerhet som kan påverka den här inställningen. Till exempel kan iOS fördröja utlösandet av principen beroende på antalet inloggningsförsök. Det kan även betrakta upprepade angivelser av samma lösenord som ett försök. Apples [säkerhetsguide för iOS](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) (öppnar Apples webbplats) är en bra resurs och innehåller mer detaljerad information om lösenord.
  
- **Maximalt antal minuter efter skärmlås innan ett lösenord krävs**<sup>1</sup>: Ange hur länge enheten kan vara inaktiv innan användaren måste ange sitt lösenord på nytt. Om den tid som du anger är längre än vad som är angivet i enhetens inställningar, så ignorerar enheten den tid som du anger. Stöds på enheter med iOS 8.0 och senare.

- **Maximalt antal minuter av inaktivitet innan skärmen låses**<sup>1</sup>: Ange det maximala antal minuter av inaktivitet som ska tillåtas på enheten innan skärmen låses.

  **iOS-alternativ**:  

  - **Inte konfigurerad** (standard): Intune rör inte den här inställningen.
  - **Omedelbart**: Skärmen låses efter 30 sekunders inaktivitet.
  - **1**: Skärmen låses efter 1 minuts inaktivitet.
  - **2**: Skärmen låses efter 2 minuters inaktivitet.
  - **3**: Skärmen låses efter 3 minuters inaktivitet.
  - **4**: Skärmen låses efter 4 minuters inaktivitet.
  - **5**: Skärmen låses efter 5 minuters inaktivitet.
    
  **iPad-alternativ**:  

  - **Inte konfigurerad** (standard): Intune rör inte den här inställningen.
  - **Omedelbart**: Skärmen låses efter 2 minuters inaktivitet.
  - **2**: Skärmen låses efter 2 minuters inaktivitet.
  - **5**: Skärmen låses efter 5 minuters inaktivitet.
  - **10**: Skärmen låses efter 10 minuters inaktivitet.
  - **15**: Skärmen låses efter 15 minuters inaktivitet.

  Om ett värde inte gäller för iOS eller iPad använder Apple närmaste *lägsta* värde. Om du till exempel anger `4` minuter använder iPad-enheter `2` minuter. Om du anger `10` minuter använder iOS-enheter `5` minuter. Detta är en Apple-begränsning.
  
  > [!NOTE]
  > Intune-användargränssnittet för den här inställningen skiljer inte de värden som stöds för iOS och iPad. Användargränssnittet kan komma att uppdateras i en framtida version.

- **Lösenordets giltighetstid (dagar)** : Ange antalet dagar innan lösenordet måste ändras.
- **Förhindra återanvändning av tidigare lösenord**: Ange hur många nya lösenord som måste ha använts innan ett gammalt kan återanvändas.
- **Upplåsning av Touch ID och Face ID**: Välj **Blockera** om du vill förhindra att fingeravtryck eller ansikte används för att låsa upp enheten. **Inte konfigurerad** låter användare låsa upp enheten med dessa metoder.

  Om den här inställningen blockeras förhindrar det även användning av FaceID-autentisering för att låsa upp enheten.

  Face ID gäller för:  
  - iOS 11.0 och senare

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **Ändring av lösenord**: Välj **Blockera** om du vill förhindra att lösenkoden ändras, läggs till eller tas bort. Ändringar av lösenkodsbegränsningar ignoreras på övervakade enheter när den här funktionen har blockerats. **Inte konfigurerad** (standard) tillåter att lösenord läggs till, ändras eller tas bort.

  - **Ändring av Touch ID och Face ID**: **Blockera** hindrar användaren från att ändra, lägga till eller ta bort TouchID-fingeravtryck och Face ID. **Inte konfigurerad** (standard) tillåter att användaren uppdaterar TouchID-fingeravtryck och Face ID på enheten.

    Om den här inställningen blockeras hindras användaren även från att ändra, lägga till eller ta bort FaceID-autentisering.

    Face ID gäller för:  
    - iOS 11.0 och senare

- **Blockera automatisk ifyllning av lösenord**: Förhindra användningen av funktionen för automatisk ifyllning av lösenord i iOS genom att välja **Blockera**. Inställningen **Blockera** har också följande effekt:

  - Användarna ombeds inte att använda ett sparat lösenord i Safari eller i någon app.
  - Automatisk starka lösenord inaktiveras och starka lösenord föreslås inte för användare.

  **Inte konfigurerat** (standard) tillåter dessa funktioner.

- **Blockera förfrågningar om lösenordsnärhet**: Välj **Blockera** så att användarens enhet inte begär lösenord från enheter i närheten. **Inte konfigurerad** (standard) tillåter dessa lösenordsbegäranden.
- **Blockera lösenordsdelning**: **Blockera** förhindrar att lösenord delas mellan enheter med hjälp av AirDrop. **Inte konfigurerad** (standard) tillåter att lösenord delas.
- **Kräv autentisering via Touch ID eller Face ID för automatisk ifyllning av lösenord eller bankkortsuppgifter**: När inställningen **Kräv** används måste användare autentisera med hjälp av TouchID eller FaceID innan lösenord eller kreditkortsinformationen kan fyllas i automatiskt i Safari och andra appar. **Inte konfigurerad** (standard) gör att användarna kan styra den här funktionen i enhetsinställningarna.

  Den här funktionen gäller för:  
  - iOS 11.0 och senare
  
<sup>1</sup> När du konfigurerar **Maximalt antal minuter av inaktivitet innan skärmen låses** och **Maximalt antal minuter efter skärmlås innan ett lösenord krävs** tillämpas de i följd. Om du t.ex. ställer in värdet för båda inställningarna till **5** minuter så stängs skärmen av automatiskt efter fem minuter. Enheten låses efter ytterligare fem minuter. Om användaren däremot stänger av skärmen manuellt så tillämpas den andra inställningen omedelbart. När användaren i det här exemplet har stängt av skärmen låses enheten fem minuter senare.

## <a name="locked-screen-experience"></a>Låsskärm

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registreringstyper

- **Åtkomst till Kontrollcenter när enheten är låst**: Välj **Blockera** om du vill förhindra åtkomst till kontrollcenterappen när enheten är låst. **Inte konfigurerad** (standard) låter användare få åtkomst till kontrollcenterappen när enheten är låst.
- **Meddelanden när enheten är låst**: **Blockera** förhindrar åtkomst till meddelanden när enheten är låst. **Inte konfigurerad** (standard) tillåter användaren att få åtkomst till aviseringsvyn utan att låsa upp enheten.
- **Dagsvyn när enheten är låst**: **Blockera** förhindrar åtkomst till dagsvyn när enheten är låst. **Inte konfigurerad** (standard) tillåter användaren att se vyn Idag när enheten är låst.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

- **Wallet-notiser när enheten är låst**: **Blockera** förhindrar åtkomst till Wallet-appen när enheten är låst. **Inte konfigurerad** (standard) tillåter användare åtkomst till appen Plånbok när enheten är låst.

## <a name="app-store-doc-viewing-gaming"></a>App Store, dokumentvisning, spel

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registreringstyper

- **Visa företagsdokument i ohanterade appar**: **Blockera** förhindrar visning av företagsdokument i ohanterade appar. **Inte konfigurerad** (standard) tillåter visning av företagsdokument i vilken app som helst. Exempelvis vill du kanske förhindra användare från att spara filer från OneDrive-appen till Dropbox. Konfigurera den här inställningen som **Blockera**. När enheten har hämtat principen (t.ex. efter en omstart) kommer det inte längre att vara tillåtet att spara.


  > [!NOTE]
  > När den här inställningen blockeras så blockeras även tangentbord från tredje part som är installerade från App Store.

  - **Tillåt ohanterade appar att läsa från hanterade kontaktkonton**: När detta anges till **Tillåt** kan ohanterade appar, till exempel den inbyggda appen för iOS-kontakter, läsa och få åtkomst till kontaktinformation från hanterade appar, däribland Outlook-mobilappen. **Inte konfigurerad** (standard) förhindrar läsning, inklusive ta bort dubbletter, från den inbyggda appen Kontakter på enheter.  
  
    Den här inställningen tillåter eller förhindrar läsning av kontaktinformation. Den styr inte synkronisering av kontakter mellan apparna.
  
    Om du vill använda inställningen ställer du in **Visa företagsdokument i ohanterade appar** på **Blockera**.

  Mer information om de här två inställningarna och deras inverkan på Outlook för synkronisering av iOS-kontaktexport finns i [Supporttips: Använd anpassade Intune-profilinställningar med den inbyggda appen för iOS-kontakter](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **Behandla AirDrop som ohanterat mål**: **Kräv** tvingar fram att AirDrop betraktas som ett ohanterat släppmål. Det förhindrar hanterade appar från att skicka data med hjälp av Airdrop. 
- **Visa dokument som inte gäller företag i företagsappar**: **Blockera** förhindrar visning av icke-företagsdokument i företagsappar. **Inte konfigurerad** (standard) tillåter visning av valfria dokument i företagshanterade appar.

  Om detta anges till **Blockera** förhindrar det även synkroniseringen av kontaktexport i Outlook för iOS. Mer information finns i [Supporttips: Aktivera synkronisering av Outlook iOS-kontakter med iOS12 MDM-kontroller](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

- **Kräv iTunes Store-lösenord för alla köp**: **Kräv** att användaren anger Apple ID-lösenordet för varje köp i app eller iTunes. **Inte konfigurerad** (standard) tillåter köp utan att ett lösenord begärs varje gång.
- **Köp i app**: Välj **Blockera** om du vill förhindra att köp från butiken görs i appen. **Inte konfigurerad** (standard) tillåter köp i butiken från en app som körs.
- **Ladda ned innehåll från iBook-butiken flaggat som ”erotik”** : Välj **Blockera** om du vill förhindra användare från att ladda ned mediainnehåll som klassificeras som erotik från iBook-butiken. **Inte konfigurerad** (standard) tillåter att användare laddar ned böcker i kategorin Erotik.
- **Tillåt hanterade appar att skriva kontakter till ohanterade kontaktkonton**: När detta anges till **Tillåt** kan hanterade appar, till exempel Outlook-mobilappen, spara eller synkronisera kontaktinformation såsom affärs- och företagskontakter till den inbyggda appen för iOS-kontakter. När detta anges till **Inte konfigurerad** (standard) kan hanterade appar inte spara eller synkronisera kontaktinformation till den inbyggda appen för iOS-kontakter på enheten.
  
  Om du vill använda inställningen ställer du in **Visa företagsdokument i ohanterade appar** på **Blockera**.

- **Klassificeringsregion**: Välj den klassificeringsregion som du vill använda för tillåtna hämtningsbara filer. Och välj sedan tillåtna klassificeringar för **filmer**, **TV-program** och **appar**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **App Store**: **Blockera** förhindrar åtkomst till App Store på övervakade enheter. **Inte konfigurerat** (standard) tillåter åtkomst.

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

  - **Installerar appar från App Store**: Välj **Blockera** för att blockera App Store från enhetens startskärm. Användarna kan fortsätta att använda iTunes eller Apple Configurator-verktyget för att installera appar. **Inte konfigurerad** (standard) tillåter att App Store visas på hemskärmen.
  - **Automatisk nedladdning av appar**: Välj **Blockera** om du vill förhindra automatisk nedladdning av appar som har köpts på andra enheter. Det påverkar inte uppdateringar av befintliga appar. **Inte konfigurerad** (standard) tillåter att appar som har köpts på andra iOS-enheter laddas ned på enheten.

- **Stötande innehåll i iTunes-musik, podcast eller nyheter**: Välj **Blockera** om du vill stoppa explicit iTunes-musik, podcaster eller nyhetsinnehåll. **Inte konfigurerad** (standard) tillåter att enheten får åtkomst till sådant som är klassificerat som vuxet innehåll i butiken. iOS 13 och senare kan kräva endast övervakade enheter. 

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

- **Lägga till Game Center-vänner**: **Blockera** förhindrar användare från att lägga till Game Center-vänner. **Inte konfigurerad** (standard) tillåter användaren att lägga till vänner i Game Center.

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

- **Spelcenter**: **Blockera** förhindrar användning av Game Center-appen. **Inte konfigurerad** (standard) tillåter användning av Game Center-appen på enheten.
- **Spel för flera personer**: Välj **Blockera** om du vill förhindra spel för flera personer. **Inte konfigurerad** (standard) tillåter användaren att spela spel för flera personer på enheten.

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

- **Åtkomst till nätverksenhet i Files-appen**: Med hjälp av SMB-protokollet (Server Message Block) har enheter åtkomst till filer eller andra resurser på en nätverksserver. **Inaktivera** förhindrar åtkomst till filer på en SMB-nätverksenhet. **Inte konfigurerat** (standard) tillåter åtkomst.

  Den här funktionen gäller för:  
  - iOS och iPadOS 13.0 och senare

## <a name="built-in-apps"></a>Inbyggda appar

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registreringstyper

- **Siri**: **Blockera** förhindrar åtkomst till Siri. **Inte konfigurerad** (standard) tillåter att röstassistenten Siri används på enheten.
  - **Siri när enheten är låst**: Välj **Blockera** om du vill förhindra åtkomst till Siri när enheten är låst. **Inte konfigurerad** (standard) tillåter att röstassistenten Siri används på enheten när den när låst.

- **Bedrägerivarningar i Safari**: **Kräv** att bedrägerivarningar ska visas i webbläsaren på enheten. **Inte konfigurerad** (standard) inaktiverar den här funktionen.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

- **Spotlight-sökning för att returnera resultat från Internet**: **Blockera** förhindrar Spotlight från att returnera resultat från sökningar på Internet. **Inte konfigurerad** (standard) tillåter att Spotlight-sökningar ansluter till Internet för att visa sökresultat.

- **Cookies i Safari**: Välj hur cookies ska hanteras på enheten. Alternativen är:
  - Tillåt
  - Blockera alla cookies
  - Tillåt cookies från besökta webbplatser
  - Tillåt cookies från aktuell webbplats

- **Safari JavaScript**: **Blockera** förhindrar att Java-skript i webbläsaren körs på enheten. **Inte konfigurerad** (standard) tillåter JavaScript.

- **Popupfönster i Safari**: **Blockera** så att blockering av popup-fönster inaktiveras i webbläsaren. **Inte konfigurerad** (standard) tillåter popup-blockeraren.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **Kamera**: Välj **Blockera** om du vill förhindra åtkomst till enhetens kamera. **Inte konfigurerad** (standard) ger åtkomst till enhetens kamera.

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

  - **FaceTime**: **Blockera** förhindrar åtkomst till FaceTime-appen. **Inte konfigurerad** (standard) tillåter åtkomst till FaceTime-appen på enheten.

    Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

- **Siris filter mot olämpligt språk**: **Kräv** förhindrar att Siri från dikterar eller talar ett olämpligt språk.

  Om du vill använda den här inställningen anger du inställningen **Siri** till **Blockera**.

- **Siri för att söka användargenererat innehåll från Internet**: **Blockera** förhindrar Siri att komma åt webbplatser för att besvara frågor. **Inte konfigurerad** (standard) tillåter Siri att få åtkomst till användargenererat innehåll på Internet.

  Om du vill använda den här inställningen anger du inställningen **Siri** till **Blockera**.

- **Apple News**: Välj **Blockera** om du vill förhindra åtkomst till Apple News-appen på enheten. **Inte konfigurerad** (standard) tillåter att Apple News-appen används.
- **iBooks store**: **Blockera** förhindrar åtkomst till iBooks-butiken. **Inte konfigurerad** (standard) tillåter användare att söka efter och köpa böcker i iBooks Store.
- **Appen Meddelanden på enheten**: **Blockera** förhindrar att användare använder appen Meddelanden för iMessage. Om enheten har stöd för SMS kan användaren fortfarande skicka och ta emot textmeddelanden via SMS. **Inte konfigurerad** (standard) tillåter användning av appen Meddelanden för att skicka och läsa meddelanden via Internet.
- **Poddsändningar**: **Blockera** förhindrar användare från att använda appen Podcaster. **Inte konfigurerad** (standard) tillåter att Podcaster-appen används.
- **Musiktjänst**: **Blockera** återställer appen Apple Music till klassiskt läge och inaktiverar tjänsten Musik. **Inte konfigurerad** (standard) tillåter att Apple Music-appen används.
- **iTunes Radio-tjänst**: **Blockera** förhindrar användare från att använda appen iTunes Radio. **Inte konfigurerad** (standard) tillåter att iTunes Radio-appen används.
- **iTunes Store**: **Inte konfigurerad** (standard) tillåter iTunes på enheterna. **Blockera** förhindrar användare från att använda iTunes på enheten. 

  Den här funktionen gäller för:  
  - iOS 4.0 och senare

- **Hitta min iPhone**: **Inte konfigurerad** (standard) tillåter att den här Hitta min-funktionen används för att hämta enhetens ungefärliga plats. **Blockera** förhindrar den här funktionen i Hitta min-appen. 

  Den här funktionen gäller för:  
  - iOS 13.0 och iPadOS 13.0 och senare

- **Hitta mina vänner**: **Inte konfigurerad** (standard) tillåter att den här Hitta min-appen används för att hitta släkt och vänner från en Apple-enhet eller iCloud.com. **Blockera** förhindrar den här funktionen i Hitta min-appen.

  Den här funktionen gäller för:  
  - iOS 13.0 och iPadOS 13.0 och senare

- **Ändringar av inställningarna för appen Hitta mina vänner**: **Blockera** förhindrar ändringar i Find My Friends-appinställningar. **Inte konfigurerad** (standard) tillåter att användaren ändrar inställningarna för appen Find My Friends.

- **Spotlight-sökning för att returnera resultat från Internet**: **Blockera** förhindrar Spotlight från att returnera resultat från sökningar på Internet. **Inte konfigurerad** (standard) tillåter att Spotlight-sökningar ansluter till Internet för att visa sökresultat.

- **Blockera borttagning av systemappar från enheten**: Om du väljer **Blockera** inaktiverar du möjligheten att ta bort systemappar från enheten. **Inte konfigurerad** (standard) tillåter användarna att ta bort systemappar från enheten.

- **Safari**: **Blockera** att webbläsaren Safari används på enheten. **Inte konfigurerad** (standard) tillåter användarna att använda webbläsaren Safari.

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

- **Autofyll i Safari**: **Blockera** inaktiverar funktionen Autofyll i Safari på enheten. **Inte konfigurerad** (standard) tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren.

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

## <a name="restricted-apps"></a>Begränsade appar

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

- **Lista över typer av begränsade appar**: Skapa en lista över appar som användarna inte får installera eller använda. Alternativen är:

  - **Inte konfigurerad** (standard): Det finns inga begränsningar från Intune. Användare har åtkomst till appar som du tilldelar samt inbyggda appar.
  - **Otillåtna appar**: Appar som inte hanteras av Intune som du inte vill ha installerade på enheten. Användare hindras inte från att installera en förbjuden app. Men om en användare installerar en app från den här listan rapporteras det i Intune.
  - **Godkända appar**: Appar som användare tillåts att installera. Användarna får inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt. Användarna hindras inte från att installera en app som inte finns med i listan över godkända appar. Men om de gör det rapporteras det i Intune.

Om du vill lägga till appar i listorna kan du:

- **Lägga till** iTunes App Store-webbadressen för den önskade appen. Om du t.ex. vill lägga till appen Microsoft Work Folders anger du `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` eller `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  Du hittar webbadressen till en app genom att öppna iTunes App Store och söka efter appen. Du kan t.ex. söka efter `Microsoft Remote Desktop` eller `Microsoft Word`. Välj appen och kopiera webbadressen.

  Du kan även använda iTunes för att hitta appen och sedan använda uppgiften **Kopiera länk** för att hämta appens webbadress.

- **Importera** en CSV-fil med information om appen, inklusive webbadressen. Använd formatet `<app url>, <app name>, <app publisher>`. Eller, **Exportera** en befintlig lista som innehåller listan över begränsade appar i samma format.

> [!IMPORTANT]
> Enhetsprofiler som använder inställningar för begränsade appar måste tilldelas grupper av användare.

## <a name="show-or-hide-apps"></a>Visa eller dölja appar

Gäller enheter som kör iOS 9.3 eller senare.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **Lista över typer av appar**: Skapa en lista över appar som ska visas eller döljas. Du kan visa eller dölja inbyggda appar och verksamhetsspecifika appar. På Apple-webbplatsen finns en lista med [inbyggda Apple-appar](https://support.apple.com/HT208094). Alternativen är:

  - **Dolda appar**: Ange en lista med appar som är dolda för användarna. Användarna kan varken visa eller öppna de här apparna.
  
    Apple förhindrar att vissa inbyggda appar döljs. Du kan till exempel inte dölja appen **Inställningar** eller **Plånbok** på enheten. [Ta bort inbyggda Apple-appar](https://support.apple.com/HT208094) visar en lista över appar som kan döljas.
  
  - **Synliga appar**: Ange en lista med appar som användarna ska kunna se och starta. Inga andra appar kan visas eller startas.

- **App-URL**: Ange butiks-URL:en för den app som du vill visa eller dölja. Exempel:

  - Om du vill lägga till appen Microsoft Work Folders anger du `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` eller `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - Om du vill lägga till appen Microsoft Word anger du `https://itunes.apple.com/de/app/microsoft-word/id586447913` eller `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  Du hittar webbadressen till en app genom att öppna iTunes App Store och söka efter appen. Du kan t.ex. söka efter `Microsoft Remote Desktop` eller `Microsoft Word`. Välj appen och kopiera webbadressen.

  Du kan även använda iTunes för att hitta appen och sedan använda uppgiften **Kopiera länk** för att hämta appens webbadress.
  
  Mer information om hur du hittar ett samlings-ID finns i [Hitta samlings-ID för en iOS-app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- **Appsamlings-ID**: Ange [appsamlings-ID](bundle-ids-built-in-ios-apps.md) för den app som du vill lägga till. Du kan visa eller dölja inbyggda appar och verksamhetsspecifika appar. På Apple-webbplatsen finns en lista med [inbyggda Apple-appar](https://support.apple.com/HT208094).
- **Appnamn**: Ange namnet på den app som du vill lägga till. Du kan visa eller dölja inbyggda appar och verksamhetsspecifika appar. På Apple-webbplatsen finns en lista med [inbyggda Apple-appar](https://support.apple.com/HT208094).
- **Utgivare**: Ange namnet på den utgivare som du vill lägga till.

Om du vill lägga till appar kan du:

- **Lägg till**: Välj om du vill skapa din lista över appar.
- **Importera** en CSV-fil med information om appen, inklusive webbadressen. Använd formatet `<app url>, <app name>, <app publisher>`. Eller välj **Exportera** om du vill skapa en lista över begränsade appar som du har lagt till, i samma format.

## <a name="wireless"></a>Trådlöst

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

Anteckning behövs för dataroaming (tips eller viktig anteckning som vägleder kunder): Den här inställningen visas inte i avsedd profil för enhetshantering. Det beror på att den här inställningen behandlas som en fjärrenhetsåtgärd, och varje gång tillståndet för dataroaming ändras på enheten blockeras den igen av Intune-tjänsten. Även om den inte finns i hanteringsprofilen fungerar den om den visas som lyckad från rapporteringen i administratörskonsolen. 
- **Datanätverksväxling**: Välj **Blockera** om du vill förhindra dataroaming över det mobila nätverket. **Inte konfigurerad** (standard) tillåter dataroaming när enheten är i ett mobilnät.

  > [!IMPORTANT]
  > Den här inställningen behandlas som en fjärrenhetsåtgärd. Därför visas inte den här inställningen i hanteringsprofilen på enheten. Varje gång statusen för dataroaming ändras på enheten blockeras **Dataroaming** av Intune-tjänsten. Om rapporteringsstatusen i Intune visar att den lyckades vet du att den fungerar, även om inställningen inte visas i hanteringsprofilen på enheten.

- **Hämtning av global bakgrund under nätverksväxling**: **Blockera** förhindrar att funktionen för global bakgrundssamling används under nätverksväxling i mobilnätverket. **Inte konfigurerad** (standard) tillåter att enheten hämtar data, till exempel e-post, när den nätverksväxlar i ett mobilnät.
- **Röstsamtal**: Välj **Blockera** om du vil förhindra användare från att använda enhetens röstsamtalsfunktion. **Inte konfigurerad** (standard) tillåter röstsamtal på enheten.
- **Röstnätverksväxling**: Välj **Blockera** om du vill förhindra röstroaming över det mobila nätverket. **Inte konfigurerad** (standard) tillåter röstroaming när enheten är i ett mobilnät.
- **Internetdelning**: **Blockera** inaktiverar Internetdelning på användarnas enheter vid varje enhetssynkronisering. Den här inställningen kanske inte är kompatibel med vissa operatörer. **Inte konfigurerad** (standard) behåller användarens standardinställning för Internetdelning.

  > [!IMPORTANT]
  > Den här inställningen behandlas som en fjärrenhetsåtgärd. Därför visas inte den här inställningen i hanteringsprofilen på enheten. Varje gång statusen för personlig hotspot ändras på enheten blockeras **Personlig hotspot** av Intune-tjänsten. Om rapporteringsstatusen i Intune visar att den lyckades vet du att den fungerar, även om inställningen inte visas i hanteringsprofilen på enheten.

- **Regler för mobilanvändning (endast hanterade appar)** : Definiera de datatyper som hanterade appar kan använda i mobilnät. Alternativen är:
  - **Blockera användning av mobildata**: Blockera användningen av mobildata för **Alla hanterade appar** eller **Välj särskilda appar**.
  - **Blockera användning av mobildata vid nätverksväxling**: Blockera användningen av mobildata vid nätverksväxling för **Alla hanterade appar** eller **Välj särskilda appar**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **Ändringar av inställningar för mobildataanvändning**: Välj **Blockera** om du vill förhindra att inställningarna för användning av appmobildata ska kunna ändras. **Inte konfigurerad** (standard) tillåter att användaren bestämmer vilka appar som ska få använda mobildata.
- **Ändringar av mobilabonnemangsinställningar**: **Blockera** hindrar användarna från att ändra inställningar i mobilabonnemanget. **Inte konfigurerad** (standard) tillåter att användarna gör ändringar.

  Den här funktionen gäller för:  
  - iOS 11.0 och senare

- **Användarändring av personlig hotspot**: När detta anges till **Blockera** kan användaren inte ändra inställningen för personlig hotspot. **Inte konfigurerad** (standard) tillåter slutanvändare att aktivera eller inaktivera sin personliga hotspot.

  Om du blockerar den här inställningen och blockerar inställningen **Personlig hotspot** stängs personlig hotspot av.

  Den här funktionen gäller för:  
  - iOS 12.2 och senare

- **Anslut till trådlösa nätverk med endast konfigurationsprofiler**: **Kräv** tvingar enheten att endast använda trådlösa nätverk som har konfigurerats med Intunes konfigurationsprofiler. **Inte konfigurerad** (standard) tillåter enheten att använda andra trådlösa nätverk.

  När detta anges till **Kräv** bör du se till att enheten har en Wi-Fi-profil. Om du inte tilldelar en Wi-Fi-profil kan den här inställningen hindra enheten från att ansluta till Internet. Om den här profilen för enhetsbegränsningar tilldelas före en Wi-Fi-profil kan enheten alltså blockeras från att ansluta till Internet.
  
  Om den inte kan ansluta avregistrerar du enheten och registrerar den igen med en Wi-Fi-profil. Ange sedan den här inställningen till **Kräv** i en profil för enhetsbegränsningar och tilldela profilen till enheten.

- **Wi-Fi är alltid aktiverat**: När detta anges till **Kräv** förblir Wi-Fi aktiverat i appen Inställningar. Den kan inte inaktiveras i Inställningar eller i Kontrollcenter, även när enheten är i flygplansläge. **Inte konfigurerad** (standard) tillåter att användaren kontrollerar aktivering eller inaktivering av Wi-Fi.

  Konfiguration av den här inställningen hindrar inte användare från att välja ett Wi-Fi-nätverk.

  Den här funktionen gäller för:  
  - iOS och iPadOS 13.0 och senare

## <a name="connected-devices"></a>Anslutna enheter

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registreringstyper

- **Handledsavkänning för parkopplad Apple Watch**: **Kräv** tvingar en parkopplad Apple Watch att använda handledsavkänning. När så krävs visar inte Apple Watch meddelanden när den inte bärs runt handleden. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

- **Kräv parkopplingslösenord för utgående AirPlay-förfrågningar**: **Kräv** ett parkopplingslösenord när användaren använder AirPlay för att strömma innehåll till andra Apple-enheter. **Inte konfigurerad** (standard) tillåter att användaren strömmar innehåll med AirPlay utan att behöva ange något lösenord.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **AirDrop**: **Blockera** förhindrar att du använder AirDrop på enheten. **Inte konfigurerad** (standard) tillåter att funktionen AirDrop används för att utbyta innehåll med enheter i närheten.
- **Apple Watch-parkoppling**: **Blockera** förhindrar parkoppling med en Apple Watch. **Inte konfigurerad** (standard) tillåter att enheten parkopplas med en Apple Watch.
- **Bluetooth-ändring**: **Blockera** förhindrar att slutanvändaren från att ändra enhetens Bluetooth-inställningar. **Inte konfigurerad** (standard) tillåter att användaren ändrar dessa inställningar.
- **Parkoppling av värd för att styra de enheter som en iOS-enhet kan parkopplas till**: **Inte konfigurerad** (standard) tillåter parkoppling så att administratören kan kontrollera vilka enheter som en iOS-enhet kan kopplas med. **Blockera** förhindrar parkoppling av värd.
- **Blockera AirPrint**: Välj **Blockera** om du vill förhindra att AirPrint-funktionen används på enheten. **Inte konfigurerat** (standard) tillåter användaren att använda AirPrint.
  - **Blockera lagring av AirPrint-autentiseringsuppgifter i nyckelringen**: **Blockera** förhindrar användning av nyckelring vid lagring av användarnamn och lösenord på enheten. **Inte konfigurerad** (standard) tillåter att AirPrint-användarnamnet och lösenordet lagras i nyckelringsappen.
  - **Kräv ett betrott TLS-certifikat för AirPrint**: **Kräv** tvingar enheten att använda betrodda certifikat för TLS-utskriftskommunikation.
  - **Blockera iBeacon-identifiering av AirPrint-skrivare**: **Blockera** förhindrar skadliga AirPrint Bluetooth-sändare från att nätfiska nätverkstrafik. **Inte konfigurerad** (standard) tillåter reklam för AirPrint-skrivare på enheten.
- **Blockera inställning av nya enheter i närheten**: **Blockera** inaktiverar uppmaningen om att konfigurera nya enheter som finns i närheten. **Inte konfigurerad** (standard) tillåter uppmaningar om att ansluta till andra Apple-enheter i närheten.

  Den här funktionen gäller för:  
  - iOS 11.0 och senare

- **Åtkomst till filer på USB-enhet**: Enheter kan ansluta till och öppna filer på en USB-enhet. **Inaktivera** förhindrar enhetsåtkomst till USB-enheten i Files-appen när en USB-enhet är ansluten till enheten. Om den här funktionen inaktiveras blockeras även slutanvändare från att överföra filer till en USB-enhet som är ansluten till en iPad. **Inte konfigurerad** (standard) tillåter åtkomst till en USB-enhet i Files-appen.

  Den här funktionen gäller för:  
  - iOS och iPadOS 13.0 och senare

## <a name="keyboard-and-dictionary"></a>Tangentbord och ordlista

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **Slå upp definition av ord**: **Blockera** förhindrar användare från att markera ett ord och sedan söka upp dess definition på enheten. **Inte konfigurerad** (standard) ger åtkomst till definitionssökningsfunktionen.
- **Tangentbord med förslag**: **Inte konfigurerad** (standard) tillåter tangentbord med förslag på ord som användaren kan ha nytta av. **Blockera** förhindrar den här funktionen.
- **Automatisk korrigering**: **Inte konfigurerad** (standard) låter enheten automatiskt korrigera felstavade ord. **Blockera** förhindrar att autokorrigering används.
- **Tangentbord med stavningskontroll**: **Inte konfigurerad** (standard) tillåter att stavningskontroll används på enheten. **Blockera** tillåter stavningskontroll.
- **Kortkommandon**: **Inte konfigurerad** (standard) tillåter att kortkommandon används på enheten. **Blockera** hindrar användaren från att använda kortkommandon.
- **Diktering**: **Blockera** hindrar användaren från att använda röstindata för att ange text. **Inte konfigurerat** (standard) tillåter användaren att använda röstindata.
- **QuickPath**: **Inte konfigurerad** (standard) gör att användare kan använda QuickPath, som möjliggör kontinuerlig inmatning på enhetens tangentbord. Användare kan skriva genom att svepa över tangenterna för att skapa ord. **Blockera** förhindrar användare från att använda QuickPath. 

  Den här funktionen gäller för:  
  - iOS 13.0 och iPadOS 13.0 och senare

## <a name="cloud-and-storage"></a>Moln och lagring

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registreringstyper

- **Krypterad säkerhetskopiering**: **Kräv** att säkerhetskopior av enheter måste vara krypterade.
- **Synkronisering av hanterade appar till molnet**: **Inte konfigurerad** (standard) tillåter att appar som du hanterar med Intune synkroniserar data till användarens iCloud-konton. **Blockera** förhindrar denna datasynkronisering till iCloud.
- **Blockera säkerhetskopiering av företagsbok**: Välj **Blockera** om du vill förhindra användarna från att säkerhetskopiera företagsböcker. **Inte konfigurerad** (standard) tillåter användarna att säkerhetskopiera dessa böcker.
- **Blockera synkronisering av företagsboksmetadata (anteckningar och markeringar)** : **Blockera** förhindrar synkronising av anteckningar och markeringar i företagsböcker. **Inte konfigurerat** (standard) tillåter synkronisering.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

- **Synkronisering av bildström till iCloud**: **Inte konfigurerad** (standard) låter användarna aktivera **My Photo Stream** på sina enheter och synkroniseras med iCloud och låta foton vara tillgängliga på användarens alla enheter. **Blockera** förhindrar bildströmssynkronisering till iCloud. Om den här funktionen blockeras kan det leda till dataförlust. 
- **iCloud-bildbiblioteket**: Ställ in på **Blockera** om du vill inaktivera användning av iCloud-bildbiblioteket för att lagra foton och videoklipp i molnet. Alla bilder som inte har laddats ned till fullo från iCloud-bildbiblioteket till enheten tas bort från enheten. **Inte konfigurerad** (standard) tillåter att iCloud-bildbiblioteket används.
- **Delad bildström**: Välj **Blockera** om du vill inaktivera **iCloud-bilddelning** på enheten. **Inte konfigurerad** (standard) tillåter delad bildström.
- **Handoff**: **Inte konfigurerad** (standard) tillåter användare att påbörja arbete på en iOS-enhet och sedan fortsätta det arbete som de inledde på en annan iOS- eller macOS-enhet. **Blockera** förhindrar den här överlämningen.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **Säkerhetskopiera till iCloud**: **Inte konfigurerad** (standard) tillåter användaren att säkerhetskopiera enheten till iCloud. **Blockera** hindrar användaren från att säkerhetskopiera enheten till iCloud.

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

- **Blockera synkronisering av iCloud-dokument**: **Inte konfigurerad** (standard) tillåter synkronisering av dokument och nyckelvärden till ditt iCloud-lagringsutrymme. **Blockera** förhindrar iCloud från att synkronisera dokument och data.

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

- **Blockera synkronisering av iCloud-nyckelring**: Välj **Blockera** om du vill inaktivera synkronisering av autentiseringsuppgifter som lagras i nyckelringen till iCloud. **Inte konfigurerad** (standard) tillåter användare att synkronisera dessa autentiseringsuppgifter.

  Från och med iOS 13.0 kräver den här inställningen övervakade enheter.

## <a name="autonomous-single-app-mode"></a>Autonomt enkelt appläge

Använd inställningarna för att konfigurera iOS-enheter så att de kör specifika appar i autonomt enkelappsläge. När det här läget har konfigurerats och appen körs låses enheten. Bara den appen kan köras. Lägg t.ex. till en app som låter användarna göra ett prov på enheten. När appens åtgärder har slutförts, eller om du tar bort principen, återgår enheten till sitt normala tillstånd.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **Appnamn**: Ange namnet på appen som du vill ha.
- **Appsamlings-ID**: Ange [samlings-ID](bundle-ids-built-in-ios-apps.md) för den önskade appen.
- **Lägg till**: Välj om du vill skapa din lista över appar.

Du kan även **Importera** en CSV-fil med listan över appnamn och deras samlings-ID:n. Eller **exportera** en befintlig lista som innehåller dessa appar.

## <a name="kiosk"></a>Helskärmsläge

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **App som ska köras i helskärmsläge**: Välj den apptyp som du vill köra i helskärmsläge. Alternativen är:
  - **Inte konfigurerat** (standard): Inställningar för helskärmsläge tillämpas inte. Enheten körs inte i helskärmsläge.
  - **Store App**: Ange webbadressen till en app i iTunes App Store.
  - **Hanterad app**: Välj en app som du lagt till i Intune.
  - **Inbyggd app**: Ange den inbyggda appens [samlings-ID](bundle-ids-built-in-ios-apps.md).

- **AssistiveTouch**: **Kräv** att hjälpmedelsinställningen för AssistiveTouch ska finnas på enheten. Den här funktionen hjälper användarna med skärmgester som de behöver hjälp med. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Invertera färger**: **Kräv** att hjälpmedelsinställningen Invertera färger ska användas, så att användare med synsvårigheter kan anpassa skärmen. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Monoljud**: **Kräv** att hjälpmedelsinställningen för Monoljud ska finnas på enheten. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Röstkontroll**: **Kräv** aktiverar röstkontroll på enheten och gör det möjligt för användare att fullständigt styra operativsystemet med hjälp av Siri-kommandon. **Inte konfigurerad** inaktiverar röstkontroll på enheten.

  Den här inställningen gäller för:  
  - iOS 13.0 och senare
  - iPadOS 13.0 och senare
  
  > [!TIP]
  > Om du har LOB-appar tillgängliga för din organisation och de inte är redo för **Röstkontroll** på dag 0 när iOS 13.0 lanseras rekommenderar vi att du låter den här inställningen vara **Inte konfigurerad**.

- **VoiceOver**: **Kräv** att hjälpmedelsinställningen VoiceOver ska finnas på enheten så att text på skärmen kan läsas upp. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Zooma**: **Kräv** att zoominställningen ska finnas på enheten så att användarna kan använda pekskärmen för att zooma in på skärmen. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Autolås**: **Blockera** förhindrar automatisk låsning av enheten. **Inte konfigurerad** tillåter denna funktion.
- **Ringsignalsknapp**: **Blockera** inaktiverar tyst läge på enheten. **Inte konfigurerad** tillåter denna funktion.
- **Skärmrotation**: **Blockera** hindrar att skärmrotationen ändras när användaren roterar enheten. **Inte konfigurerad** tillåter denna funktion.
- **Viloläge för skärm-knapp**: Välj **Blockera** om du vill inaktivera enhetens knapp för viloläge. **Inte konfigurerad** tillåter denna funktion.
- **Touch**: **Blockera** inaktiverar enhetens pekskärm. **Inte konfigurerad** tillåter användaren att använda pekskärmen.
- **Volymknappar**: **Blockera** förhindrar att enhetens volymknappar används. **Inte konfigurerad** tillåter volymknapparna.
- **AssistiveTouch-knapp**: **Tillåt** låter användarna använda funktionen AssistiveTouch. **Inte konfigurerad** inaktiverar den här funktionen.
- **Invertera färger-knapp**: **Tillåt** att inställningarna för att invertera färger kan justeras. **Inte konfigurerad** inaktiverar den här funktionen.
- **Läs upp markerad text**: **Tillåt** att hjälpmedelsinställningen Läs upp markering finns på enheten. Den här funktionen läser upp text som användaren väljer. **Inte konfigurerad** inaktiverar den här funktionen.
- **Ändring av röstkontroll**: **Tillåt** användare att ändra tillståndet för röstkontroll på sina enheter. **Inte konfigurerad** blockerar användare från att ändra tillståndet för röstkontroll på sina enheter.

  Den här inställningen gäller för:  
  - iOS 13.0 och senare
  - iPadOS 13.0 och senare

- **VoiceOver-knapp**: **Tillåt** VoiceOver-ändringar så att användarna kan uppdatera VoiceOver-funktionen, t.ex. när det gäller hur snabbt texten ska läsas upp. **Inte konfigurerad** förhindrar VoiceOver-ändringar.
- **Zoomkontroll**: **Tillåt** att användaren kan ändra zoominställningarna. **Inte konfigurerad** förhindrar zoominställningar.

> [!NOTE]
> Innan du kan konfigurera en iOS-enhet för helskärmsläge måste du använda Apple Configurator-verktyget eller Apples enhetsregistreringsprogram för att placera enheten i övervakat läge. Information om hur du använder Apple Configurator-verktyget finns i Apples guide.
> Om den iOS-appen som du anger har installerats efter det att du har tilldelat profilen så går inte enheten över i helskärmsläge förrän den startas om.

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhetsregistrering, automatisk enhetsregistrering (övervakad)

- **Omarkerade e-postdomäner** > **Webbadress till e-postdomän**: Lägg till en eller flera webbadresser i listan. När slutanvändarna får ett e-postmeddelande från en annan domän än någon av de du har angett, så markeras e-postmeddelandet som ej betrott i iOS-e-postappen.

- **Hanterade webbdomäner** > **Webbadress till webbdomän**: Lägg till en eller flera webbadresser i listan. Dokument som laddas ned från de domäner du anger här anses vara hanterade. Den här inställningen gäller enbart för dokument som hämtas i Safari-webbläsaren.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhetsregistrering (övervakad)

- **Fyll i lösenord automatiskt på Safari-domäner** > **Domänwebbadress**: Lägg till en eller flera webbadresser i listan. Användarna kan bara spara webblösenord från webbadresser i den här listan. Den här inställningen gäller enbart för Safari-webbläsaren och enheter i övervakat läge. Om du inte anger någon webbadress, kan lösenorden sparas från alla webbplatser.

  Den här inställningen gäller för:  
  - iOS 9.3 och senare

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
>
> - Appinstallation av slutanvändare
> - Borttagning av app
> - FaceTime
> - Safari
> - iTunes
> - Barnförbjudet innehåll
> - Dokument och data i iCloud
> - Spel för flera personer
> - Lägg till Game Center-vänner
> - Siri

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

Du kan också begränsa enhetens funktioner och inställningar på [macOS](device-restrictions-macos.md)-enheter.
