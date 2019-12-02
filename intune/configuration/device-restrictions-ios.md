---
title: iOS-enhetsinställningar i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till, konfigurera eller skapa inställningar på iOS-enheter när du vill begränsa funktioner, till exempel lösenordskrav, kontrollera låst skärm, använda inbyggda appar, lägga till begränsade eller godkända appar, hantera bluetooth-enheter, ansluta till molnet för säkerhetskopiering och lagring, aktivera helskärmsläge, lägga till domäner och kontrollera hur användarna samverkar med Safari-webbläsaren i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6fde277e16043662420864adcc0458e3dccad308
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465650"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>Enhetsinställningarna för iOS och iPadOS tillåter eller begränsar funktioner med hjälp av Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Den här artikeln beskriver de olika inställningar som du kan styra på iOS- och iPadOS-enheter. Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar för att tillåta eller inaktivera funktioner, ange lösenordsregler, tillåta eller begränsa specifika appar med mera.

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina iOS-enheter.

> [!TIP]
> Inställningarna använder Apples MDM-inställningar. Mer information om de här inställningarna finns i [Apples hanterings inställningar för mobila enheter](https://support.apple.com/guide/mdm/welcome/web) (öppnar Apples webbplats).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en konfigurationsprofil för enhetsbegränsningar](../device-restrictions-configure.md).

> [!NOTE]
> Dessa inställningar gäller för olika registrerings typer, med vissa inställningar som gäller för alla registrerings alternativ. Mer information om de olika registrerings typerna finns i [iOS-registrering](../ios-enroll.md).

## <a name="general"></a>Allmänt

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **Dela användningsdata**: Välj **Blockera** för att förhindra enheten från att skicka diagnostik- och användningsdata till Apple. **Inte konfigurerad** (standard) tillåter att dessa data skickas.

- **Skärmdump**: Välj **Blockera** för att förhindra skärmbilder eller skärmdumpar på enheten. I iOS 9,0 och senare blockeras även skärm inspelningar. **Inte konfigurerad** (standard) låter användaren spara skärminnehållet som en bild eller video.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

- **Ej betrodda TLS-certifikat**: Välj**Blockera** om du vill stoppa ej betrodda TLS-certifikat på enheten. **Inte konfigurerad** (standard) tillåter TLS-certifikat.
- **Tillåt trådlösa PKI-uppdateringar**: **Tillåt** låter dina användare ta emot programuppdateringar utan att ansluta sina enheter till en dator.
- **Begränsa reklamspårning**: Välj **Begränsa** om du vill inaktivera enhetens reklamidentifierare. **Inte konfigurerad** (standard) gör att den förblir aktiverad.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Ändring av inställningar för att skicka diagnostik**: **Blockera** hindrar användaren från att ändra diagnostiköverförings- och appanalysinställningar i **Diagnostik och användning** (enhetsinställningar). **Inte konfigurerad** (standard) tillåter att användaren ändrar dessa enhetsinställningar.

  Om du vill använda den här inställningen anger du inställningen **dela användnings data** som ska **blockeras**.

  Den här funktionen gäller för:  
  - iOS 9.3.2 och senare

- **Fjärrskärmsvisning i appen Klassrum**: Välj **Blockera** om du vill förhindra appen Klassrum från att visa skärmarna på fjärranslutna enheter. **Inte konfigurerad** (standard) tillåter appen Apple Klassrum att visa skärmen.

  Om du vill använda den här inställningen ställer du in inställningen för **skärmdump** på **blockera**.

  Den här funktionen gäller för:  
  - iOS 9.3 och senare

- **Skärmvisning utan uppmaning i appen Klassrum**: Om det här ställs in på **Tillåt** kan lärarna tyst övervaka skärmarna på elevernas iOS-enheter med hjälp av appen Klassrum utan att eleverna vet om det. Elevenheter som registrerats i en klass som använder appen Klassrum ger automatiskt behörighet till den kursens lärare. **Inte konfigurerad** (standard) förhindrar den här funktionen.

  Om du vill använda den här inställningen ställer du in inställningen för **skärmdump** på **blockera**.

- **Företagsappförtroende**: Välj **Blockera** om du vill ta bort knappen **Lita på företagsutvecklare** i Inställningar > Allmänt > Profiler och enhetshantering på enheten. **Inte konfigurerad** (standard) tillåter att användaren väljer att lita på appar som inte laddats ned från App Store.
- **Kontoändring**: När den är inställd på **Blockera** kan användaren inte uppdatera enhetsspecifika inställningar från iOS-appens inställningar. Användaren kan t.ex. skapa nya enhetskonton eller ändra användarnamn eller lösenord. **Inte konfigurerad** (standard) tillåter användare att ändra dessa inställningar.

  Den här funktionen gäller även för inställningar som kan nås från appen för iOS-inställningar, som E-post, Kontakter, Kalender, Facebook, Twitter med flera. Den här funktionen gäller inte för appar med kontoinställningar som inte konfigureras från appen för iOS-inställningar, som Microsoft Outlook-appen.

- **Skärmtid**: Välj **Blockera** om du vill hindra användare från att ange sina egna begränsningar i Skärmtid (enhetsinställningar). **Inte konfigurerad** tillåter att användaren konfigurerar enhetsbegränsningar (till exempel kontrollfunktioner för föräldrar eller innehålls- och sekretessbegränsningar) på enheten.

  Den här inställningen har bytt namn från **Aktivera begränsningar i enhetsinställningarna**. Effekten av ändringen:  
  
  - iOS 11.4.1 och tidigare: **Blockera** förhindrar slutanvändare från att ange egna begränsningar i enhetsinställningarna. Beteendet är detsamma. Ingenting har ändrats för slutanvändarna.
  - iOS 12.0 och senare: **Blockera** hindrar slutanvändarna från att ange sin egen **skärmtid** i enhetsinställningarna (Inställningar > Allmänt > Skärmtid), inklusive innehålls- och sekretessbegränsningar. På enheter som har uppgraderats till iOS 12.0 visas inte längre fliken Begränsningar i enhetsinställningarna (Inställningar > Allmänt > Enhetshantering > Hanteringsprofil > Begränsningar). Dessa inställningar finns i **Skärmtid**.
  
- **Användning av alternativet Radera allt innehåll och inställningar på enheten**: Välj **Blockera** så att användarna inte kan använda alternativet att radera allt innehåll och alla inställningar på enheten. **Inte konfigurerad** (standard) ger användarna åtkomst till de här inställningarna.
- **Namnbyte för enhet**: Välj **Blockera** så att enhetens namn inte kan ändras. **Inte konfigurerad** (standard) tillåter användaren att ändra enhetens namn.
- **Ändring av aviseringsinställningar**: Välj **Blockera** så att aviseringsinställningarna inte kan ändras. **Inte konfigurerad** (standard) tillåter användaren att ändra enhetens meddelandeinställningar.
- **Ändring av bakgrundsbild**: **Blockera** förhindrar att bakgrundsbilden ändras. **Inte konfigurerad** (standard) tillåter användaren att ändra enhetens bakgrundsbild.
- **Ändringar av inställningar för företagsappsförtroende**: **Blockera** förhindrar användaren från att ändra inställningarna för företagsappsförtroende på kontrollerade enheter. **Inte konfigurerad** (standard) tillåter användaren att lita på appar som inte laddats ned från App Store.
- **Ändra konfigurationsprofil**: **Blockera** förhindrar ändringar av enhetens konfigurationsprofil. **Inte konfigurerad** (standard) tillåter användaren att installera konfigurationsprofiler.
- **Aktiveringslås**: Välj **Tillåt** för att aktivera aktiveringslåset på övervakade iOS-enheter. Aktiveringslåset gör det svårare att återaktivera en förlorad eller stulen enhet.
- **Blockera borttagning av appar**: Välj **Blockera** för att förhindra att användare tar bort appar. **Inte konfigurerad** (standard) tillåter användaren att ta bort appar från enheten.
- **Blockera USB-begränsat läge**: Välj **Blockera** om du vill inaktivera USB-begränsat läge på övervakade enheter. USB-begränsat läge blockerar USB-tillbehör från att utbyta data med en enhet som har varit låst i över en timma. **Inte konfigurerad** (standard) tillåter USB-begränsat läge.
- **Framtvinga automatisk datum och tid**: **Kräv** tvingar övervakade enheter att konfigurera datum och tid automatiskt. Enhetens tidszon uppdateras när enheten har mobila anslutningar eller har aktiverats för Wi-Fi med platstjänster.
- **Kräv att elever begär tillstånd att lämna Classroom-kurs**: **Kräv** tvingar elever som har registrerats i en ohanterad kurs med appen Classroom att begära tillstånd från läraren om att lämna kursen. **Inte konfigurerad** (standard) tvingar inte eleven att be om behörighet.

  Den här funktionen gäller för:  
  - iOS 11.3 och senare

- **Tillåt Classroom att låsa en app och låsa enheten utan att fråga**: **Aktivera** tillåter att lärare låser appar eller låser enheten med hjälp av Classroom-appen utan att fråga eleven. Applåsning innebär att enheten endast kan komma åt de appar som anges av läraren. **Inte konfigurerad** (standard) förhindrar att lärare låser appar eller enheter med hjälp av Classroom-appen utan att fråga eleven.

  Den här funktionen gäller för:  
  - iOS 11.0 och senare

- **Delta automatiskt i Classroom-klasser utan att fråga**: **Aktivera** tillåter automatiskt elever att ansluta till en klass i Classroom-appen utan att fråga läraren. **Inte konfigurerad** (standard) uppmärksammar lärare på att elever vill ansluta till en klass i Classroom-appen.

  Den här funktionen gäller för:  
  - iOS 11.0 och senare

- **Blockera VPN-skapande**: **Blockera** förhindrar användare från att skapa VPN-konfigurationsinställningar. **Inte konfigurerad** (standard) tillåter användare att skapa virtuella privata nätverk på enheten.
- **Ändrar eSIM-inställningar**: **Blockera** hindrar användarna från att ta bort eller lägga till ett mobilabonnemang till eSIM på enheten. **Inte konfigurerad** (standard) tillåter användare att ändra dessa inställningar.

  Den här funktionen gäller för:  
  - iOS 12.1 och senare

- **Skjut upp programuppdateringar**: När **Inte konfigurerad** (standard) används visas programuppdateringar på enheten när de ges ut av Apple. Om en iOS-uppdatering exempelvis släpps av Apple på ett specifikt datum, visas uppdateringen på enheten runt utgivningsdatumet.

  **Aktivera** gör att du kan skjuta upp visningen av programuppdateringar på enheter i 0–90 dagar. Den här inställningen styr inte när uppdateringar installeras eller inte. 

  - **Fördröj visning av programuppdateringar**: Ange ett värde mellan 0 och 90 dagar. När fördröjningen upphör får användarna ett meddelande om att uppdatera till den tidigaste versionen av OS som var tillgänglig när fördröjningen utlöstes.

    Om iOS 12.a exempelvis blir tillgänglig **den 1 januari** och **Fördröj synlighet** är inställt på **5 dagar**, visas inte iOS 12.som en tillgänglig uppdatering på slutanvändarnas enheter. På **den sjätte dagen** efter utgivningen är uppdateringen tillgänglig och slutanvändarna kan installera den.

    Den här inställningen gäller för:  
    - iOS 11.3 och senare

## <a name="password"></a>Lösenord

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **Lösenord**: **Kräv** att slutanvändaren måste ange ett lösenord för att få åtkomst till enheten. **Inte konfigurerad** (standard) låter användare komma åt enheten utan att ange ett lösenord.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

> [!IMPORTANT]
> Om du konfigurerar en lösenordsinställning på en enhet som registreras via Användarregisterring används automatiskt inställningen **Blockera** för **Enkla lösenord**, och en 6-siffrig PIN-kod krävs.
>
> Du kan till exempel konfigurera inställningen **Lösenordets giltighetstid** och skicka den här principen till användarregistrerade enheter. Följande händer på enheterna:
>
> - Inställningen **Lösenordets giltighetstid** ignoreras.
> - Enkla lösenord, till exempel `1111` eller `1234`, tillåts inte.
> - En 6-siffrig PIN-kod krävs.

- **Enkla lösenord**: Välj **Blockera** om du vill kräva mer avancerade lösenord. **Inte konfigurerad** tillåter enkla lösenord som `0000` och `1234`.

- **Krav på lösenordstyp**: Välj den typ av lösenord som din organisation kräver. Alternativen är:
  - **Standard för enheten**
  - **Numerisk**
  - **Alfanumerisk**
- **Antal icke-alfanumeriska tecken i lösenord**: Ange det antal symboltecken i lösenordet (t.ex. `#` eller `@`) som måste ingå i lösenordet.

- **Minsta längd på lösenord**: Ange den minsta längd som en användare måste ange (mellan 4 och 14 tecken). Ange en längd på mellan 4 och 6 tecken på användarens registrerade enheter.
  
  > [!NOTE]
  > Användare kan ange en PIN-kod som är större än 6 siffror för enheter som har registrerats av användaren. Men högst 6 siffror tillämpas på enheten. En administratör anger till exempel den minsta längden som `8`. På användare-registrerade enheter behöver användarna bara ange en 6-siffrig PIN-kod. Intune tvingar inte en PIN-kod som är större än 6 siffror på användarens registrerade enheter.

- **Antal felaktiga inloggningar innan enheten rensas**: Ange antalet felaktiga inloggningar som tillåts innan enheten rensas (mellan 4–11).
  
  iOS har inbyggd säkerhet som kan påverka den här inställningen. Till exempel kan iOS fördröja utlösandet av principen beroende på antalet inloggnings försök. Det kan också övervägas att upprepade gånger ange samma lösen ord som ett försök. Apples [säkerhets guide för iOS](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) (öppnar Apples webbplats) är en lämplig resurs och ger mer detaljerad information om lösen ord.
  
- **Maximalt antal minuter efter skärmlås innan ett lösenord krävs**<sup>1</sup>: Ange hur länge enheten kan vara inaktiv innan användaren måste ange sitt lösenord på nytt. Om den tid som du anger är längre än vad som är angivet i enhetens inställningar, så ignorerar enheten den tid som du anger. Stöds på enheter med iOS 8.0 och senare.

- **Maximalt antal minuter av inaktivitet innan skärmen låses**<sup>1</sup>: Ange det maximala antal minuter av inaktivitet som ska tillåtas på enheten innan skärmen låses.

  **iOS-alternativ**:  

  - **Inte konfigurerat** (standard): Intune vidrör inte den här inställningen.
  - **Omedelbart**: skärmen låser sig efter 30 sekunders inaktivitet.
  - **1**: skärmen låser sig efter 1 minut inaktivitet.
  - **2**: skärmen låser sig efter 2 minuters inaktivitet.
  - **3**: skärmen låser sig efter 3 minuters inaktivitet.
  - **4**: skärmen låser sig efter 4 minuters inaktivitet.
  - **5**: skärmen låser sig efter 5 minuters inaktivitet.
    
  **iPad-alternativ**:  

  - **Inte konfigurerat** (standard): Intune vidrör inte den här inställningen.
  - **Direkt**: skärmen låser sig efter 2 minuters inaktivitet.
  - **2**: skärmen låser sig efter 2 minuters inaktivitet.
  - **5**: skärmen låser sig efter 5 minuters inaktivitet.
  - **10**: skärmen låser sig efter 10 minuters inaktivitet.
  - **15**: skärmen låser sig efter 15 minuters inaktivitet.

  Om ett värde inte gäller för iOS eller iPad använder Apple det närmast *lägsta* värdet. Om du till exempel anger `4` minuter använder iPad-enheter `2` minuter. Om du anger `10` minuter använder iOS-enheter `5` minuter. Detta är en Apple-begränsning.
  
  > [!NOTE]
  > Intune-ANVÄNDARGRÄNSSNITTET för den här inställningen skiljer inte värdena för iOS och iPad som stöds. Användar gränssnittet kan uppdateras i en framtida version.

- **Lösenordets giltighetstid (dagar)** : Ange antal dagar innan lösenordet för enheten måste ändras.
- **Förhindra återanvändning av tidigare lösenord**: Ange hur många nya lösenord som måste ha använts innan ett gammalt kan återanvändas.
- **Lås upp Touch ID och ansikts-ID**: Välj **blockera** för att förhindra användning av finger avtryck eller ansikte för att låsa upp enheten. **Inte konfigurerad** låter användare låsa upp enheten med dessa metoder.

  Att blockera den här inställningen förhindrar även att du använder FaceID-autentisering för att låsa upp enheten.

  Ansikts-ID gäller för:  
  - iOS 11.0 och senare

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Ändring av lösenkod**: Välj **Blockera** om du vill förhindra att lösenkoden ändras, läggs till eller tas bort. Ändringar av lösenkodsbegränsningar ignoreras på övervakade enheter när den här funktionen har blockerats. **Inte konfigurerad** (standard) tillåter att lösenord läggs till, ändras eller tas bort.

  - **Ändring av Touch-ID och ansikts-ID**: **blockera** hindrar användaren från att ändra, lägga till eller ta bort TouchID-finger avtryck och ansikts-ID. **Inte konfigurerad** (standard) tillåter att användaren uppdaterar TouchID-fingeravtryck och Face ID på enheten.

    Om du blockerar den här inställningen stoppas även användaren från att ändra, lägga till eller ta bort FaceID-autentisering.

    Ansikts-ID gäller för:  
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

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **Åtkomst till Kontrollcenter när enheten är låst**: Välj **Blockera** om du vill förhindra åtkomst till kontrollcenterappen när enheten är låst. **Inte konfigurerad** (standard) låter användare få åtkomst till kontrollcenterappen när enheten är låst.
- **Meddelanden när enheten är låst**: **Blockera** förhindrar åtkomst till meddelanden när enheten är låst. **Inte konfigurerad** (standard) tillåter användaren att få åtkomst till aviseringsvyn utan att låsa upp enheten.
- **Dagsvyn när enheten är låst**: **Block** förhindrar åtkomst till vyn Idag när enheten är låst. **Inte konfigurerad** (standard) tillåter användaren att se vyn Idag när enheten är låst.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

- **Plånboksmeddelanden när enheten är låst**: **Blockera** förhindrar åtkomst till appen Plånbok när enheten är låst. **Inte konfigurerad** (standard) tillåter användare åtkomst till appen Plånbok när enheten är låst.

## <a name="app-store-doc-viewing-gaming"></a>App Store, dokumentvisning, spel

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **Visa företagsdokument i ohanterade appar**: **Blockera** förhindrar visning av företagsdokument i ohanterade appar. **Inte konfigurerad** (standard) tillåter visning av företagsdokument i vilken app som helst. Exempelvis vill du kanske förhindra användare från att spara filer från OneDrive-appen till Dropbox. Konfigurera den här inställningen som **Blockera**. När enheten har hämtat principen (t.ex. efter en omstart) kommer det inte längre att vara tillåtet att spara.


  > [!NOTE]
  > När den här inställningen blockeras blockeras även tredjeparts tangent bord som är installerade från App Store.

  - **Tillåt ohanterade appar att läsa från hanterade kontakt konton**: när den är inställd på **Tillåt**kan ohanterade appar, t. ex. den inbyggda appen iOS-kontakter, läsa och få åtkomst till kontakt information från hanterade appar, inklusive Outlook Mobile-appen. **Inte konfigurerad** (standard) förhindrar läsning, inklusive ta bort dubbletter, från den inbyggda appen Kontakter på enheter.  
  
    Den här inställningen tillåter eller förhindrar läsning av kontakt information. Den styr inte synkroniseringen av kontakter mellan apparna.
  
    Om du vill använda inställningen ställer du in **Visa företagsdokument i ohanterade appar** på **Blockera**.

  Mer information om dessa två inställningar och deras inverkan på Outlook för iOS-synkronisering av kontakt export finns i [support tips: Använd anpassade profil inställningar i Intune med appen inbyggda appar för iOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **Behandla AirDrop som ohanterat mål**: **Kräv** tvingar fram att AirDrop betraktas som ett ohanterat släppmål. Det förhindrar hanterade appar från att skicka data med hjälp av Airdrop. 
- **Visa icke-företagsdokument i ohanterade appar**: **Blockera** förhindrar visning av icke-företagsdokument i företagsappar. **Inte konfigurerad** (standard) tillåter visning av valfria dokument i företagshanterade appar.

  Inställningen till **blockera** förhindrar även synkronisering av kontakt export i Outlook för iOS. Mer information finns i [support tips: Aktivera synkronisering av Outlook iOS-kontakter med IOS12 MDM-kontroller](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

- **Kräv lösen ord för iTunes Store för alla köp**: **Kräv** att användaren anger lösen ordet för Apple-ID för varje app-eller iTunes-inköp. **Inte konfigurerad** (standard) tillåter köp utan att du behöver ange ett lösen ord varje gång.
- **Köp i appar**: Välj **Blockera** om du vill förhindra att köp från butiken görs i appen. **Inte konfigurerad** (standard) tillåter köp i butiken från en app som körs.
- **Ladda ned innehåll från iBook-butiken flaggat som ”erotik”** : Välj **Blockera** om du vill förhindra användare från att ladda ned mediainnehåll som klassificeras som erotik från iBook-butiken. **Inte konfigurerad** (standard) tillåter att användare laddar ned böcker i kategorin Erotik.
- **Tillåt att hanterade appar skriver kontakter till ohanterade kontakt konton**: när de är inställda på **Tillåt**kan hanterade appar, t. ex. Outlook-mobilappen, Spara eller synkronisera kontakt information, inklusive företags-och företags kontakter, till den inbyggda appen för iOS-kontakter. Om det är inställt på **inte konfigurerat** (standard) kan hanterade appar inte spara eller synkronisera kontakt information till den inbyggda appen för iOS-kontakter på enheten.
  
  Om du vill använda inställningen ställer du in **Visa företagsdokument i ohanterade appar** på **Blockera**.

- **Klassificeringsregion**: Välj den klassificeringsregion som du vill använda för tillåtna hämtningsbara filer. Och välj sedan tillåtna klassificeringar för **filmer**, **TV-program** och **appar**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **App Store**: **Blockera** förhindrar åtkomst till App Store på övervakade enheter. **Inte konfigurerat** (standard) tillåter åtkomst.

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

  - **Installera appar från App Store**: Välj **Blockera** om du vill blockera App Store från enhetens startskärm. Användarna kan fortsätta att använda iTunes eller Apple Configurator-verktyget för att installera appar. **Inte konfigurerad** (standard) tillåter att App Store visas på hemskärmen.
  - **Automatisk nedladdning av appar**: Välj **Blockera** om du vill förhindra automatisk nedladdning av appar som har köpts på andra enheter. Det påverkar inte uppdateringar av befintliga appar. **Inte konfigurerad** (standard) tillåter att appar som har köpts på andra iOS-enheter laddas ned på enheten.

- **Stötande musik, podcaster eller nyhetsinnehåll i iTunes**: Välj **Blockera** om du vill stoppa explicit iTunes-musik, podcaster eller nyhetsinnehåll. **Inte konfigurerad** (standard) tillåter att enheten får åtkomst till sådant som är klassificerat som vuxet innehåll i butiken. iOS 13 och senare kan kräva endast övervakade enheter. 

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

- **Lägga till Game Center-vänner**: **Blockera** förhindrar användare från att lägga till Game Center-vänner. **Inte konfigurerad** (standard) tillåter användaren att lägga till vänner i Game Center.

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

- **Game Center**: **Blockera** förhindrar användning av Game Center-appen. **Inte konfigurerad** (standard) tillåter användning av Game Center-appen på enheten.
- **Spel för flera**personer: Välj **blockera** för att förhindra spel i flera personer. **Inte konfigurerad** (standard) tillåter användaren att spela spel för flera personer på enheten.

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

- **Åtkomst till nätverks enhet i filer-appen**: genom att använda SMB-protokollet (Server Message Block) kan enheterna komma åt filer eller andra resurser på en nätverks server. **Inaktivera** förhindrar åtkomst till filer på en nätverks-SMB-enhet. **Inte konfigurerat** (standard) tillåter åtkomst.

  Den här funktionen gäller för:  
  - iOS och iPad 13,0 och senare

## <a name="built-in-apps"></a>Inbyggda appar

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **Siri**: **Blockera** förhindrar åtkomst till Siri. **Inte konfigurerad** (standard) tillåter att röstassistenten Siri används på enheten.
  - **Siri när enheten är låst**: Välj **Blockera** om du vill förhindra åtkomst till Siri när enheten är låst. **Inte konfigurerad** (standard) tillåter att röstassistenten Siri används på enheten när den när låst.

- **Bedrägerivarningar i Safari**: **Kräv** att bedrägerivarningar ska visas i webbläsaren på enheten. **Inte konfigurerad** (standard) inaktiverar den här funktionen.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

- **Spotlight-sökning som returnerar resultat från Internet**: **Blockera** förhindrar Spotlight från att returnera resultat från sökningar på Internet. **Inte konfigurerad** (standard) tillåter att Spotlight-sökningar ansluter till Internet för att visa sökresultat.

- **Cookies i Safari**: Välj hur cookies ska hanteras på enheten. Alternativen är:
  - Tillåt
  - Blockera alla cookies
  - Tillåt cookies från besökta webbplatser
  - Tillåt cookies från aktuell webbplats

- **JavaScript i Safari**: **Blockera** förhindrar att Java-skript i webbläsaren körs på enheten. **Inte konfigurerad** (standard) tillåter Java-skript.

- **Popup-fönster i Safari**: **Blockera** så att blockering av popup-fönster inaktivas i webbläsaren. **Inte konfigurerad** (standard) tillåter blockering av popup-fönster.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Kamera**: Välj **Blockera** om du vill förhindra åtkomst till enhetens kamera. **Inte konfigurerad** (standard) ger åtkomst till enhetens kamera.

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

  - **FaceTime**: **Blockera** förhindrar åtkomst till FaceTime-appen. **Inte konfigurerad** (standard) tillåter åtkomst till FaceTime-appen på enheten.

    Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

- **Filtrering av grovt språk i Siri**: **Kräv** förhindrar att Siri dikterar eller talar ett olämpligt språk.

  Om du vill använda den här inställningen ställer du in inställningen **Siri** på **blockera**.

- **Siri skickar frågor om innehåll som skapats av användare från Internet**: **Blockera** förhindrar Siri från att få åtkomst till webbplatser för att kunna besvara frågor. **Inte konfigurerad** (standard) tillåter Siri att få åtkomst till användargenererat innehåll på Internet.

  Om du vill använda den här inställningen ställer du in inställningen **Siri** på **blockera**.

- **Apple News**: Välj **Blockera** om du vill förhindra åtkomst till Apple News-appen på enheten. **Inte konfigurerad** (standard) tillåter att Apple News-appen används.
- **iBooks-butiken**: **Blockera** förhindrar åtkomst till iBooks-butiken. **Inte konfigurerad** (standard) tillåter användare att söka efter och köpa böcker i iBooks Store.
- **Appen meddelanden på enheten**: **blockera** förhindrar att användare använder appen meddelanden för iMessage. Om enheten har stöd för SMS-meddelanden kan användaren fortfarande skicka och ta emot SMS. **Inte konfigurerad** (standard) låter dig använda appen meddelanden för att skicka och läsa meddelanden via Internet.
- **Podcaster**: **Blockera** förhindrar användare från att använda appen Podcaster. **Inte konfigurerad** (standard) tillåter att Podcaster-appen används.
- **Tjänsten musik**: **Blockera** återställer appen Apple Music till klassiskt läge och inaktiverar tjänsten Musik. **Inte konfigurerad** (standard) tillåter att Apple Music-appen används.
- **iTunes Radio-tjänsten**: **Blockera** förhindrar användare från att använda appen iTunes Radio. **Inte konfigurerad** (standard) tillåter att iTunes Radio-appen används.
- **iTunes Store**: **inte konfigurerat** (standard) tillåter iTunes på enheterna. **Blockera** förhindrar att användare använder iTunes på enheten. 

  Den här funktionen gäller för:  
  - iOS 4.0 och senare

- **Hitta min iPhone**: **inte konfigurerad** (standard) gör att du kan använda den här funktionen Hitta min app för att hämta den ungefärliga platsen för enheten. **Blockera** förhindrar den här funktionen i Hitta min app. 

  Den här funktionen gäller för:  
  - iOS 13,0 och iPad 13,0 och senare

- **Hitta mina vänner**: **inte konfigurerat** (standard) gör att du kan använda den här funktionen Hitta min app för att hitta släkt och vänner från en Apple-enhet eller iCloud.com. **Blockera** förhindrar den här funktionen i Hitta min app.

  Den här funktionen gäller för:  
  - iOS 13,0 och iPad 13,0 och senare

- **Ändringar av inställningarna för appen Find My Friends**: **Blockera** förhindrar att inställningarna för appen Find My Friends ändras. **Inte konfigurerad** (standard) tillåter att användaren ändrar inställningarna för appen Find My Friends.

- **Spotlight-sökning som returnerar resultat från Internet**: **Blockera** förhindrar Spotlight från att returnera resultat från sökningar på Internet. **Inte konfigurerad** (standard) tillåter att Spotlight-sökningar ansluter till Internet för att visa sökresultat.

- **Blockera borttagning av systemappar från enheten**: Om du väljer **Blockera** inaktiverar du möjligheten att ta bort systemappar från enheten. **Inte konfigurerad** (standard) tillåter användarna att ta bort systemappar från enheten.

- **Safari**: **Blockera** webbläsaren Safari från att användas på enheten. **Inte konfigurerad** (standard) tillåter användarna att använda webbläsaren Safari.

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

- **Autofyll i Safari**: **Blockera** inaktiverar funktionen Autofyll i Safari på enheten. **Inte konfigurerad** (standard) tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren.

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

## <a name="restricted-apps"></a>Begränsade appar

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

- **Lista över typer av begränsade appar**: skapa en lista över appar som användarna inte får installera eller använda. Alternativen är:

  - **Inte konfigurerat** (standard): det finns inga begränsningar från Intune. Användare har åtkomst till appar som du tilldelar och inbyggda appar.
  - **Otillåtna appar**: Appar som inte hanteras av Intune som du inte vill ha installerade på enheten. Användare hindras inte från att installera en förbjuden app. Men om en användare installerar en app från den här listan, rapporteras den i Intune.
  - **Godkända appar**: Appar som användare tillåts att installera. Användarna får inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt. Användarna hindras inte från att installera en app som inte finns med i listan över godkända appar. Men om de gör det rapporteras de i Intune.

Om du vill lägga till appar i listorna kan du:

- **Lägga till** iTunes App Store-webbadressen för den önskade appen. Om du t.ex. vill lägga till appen Microsoft Work Folders anger du `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` eller `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  Du hittar webbadressen till en app genom att öppna iTunes App Store och söka efter appen. Du kan t.ex. söka efter `Microsoft Remote Desktop` eller `Microsoft Word`. Välj appen och kopiera webbadressen.

  Du kan även använda iTunes för att hitta appen och sedan använda uppgiften **Kopiera länk** för att hämta appens webbadress.

- **Importera** en CSV-fil med information om appen, inklusive webbadressen. Använd formatet `<app url>, <app name>, <app publisher>`. Eller, **Exportera** en befintlig lista som innehåller listan över begränsade appar i samma format.

> [!IMPORTANT]
> Enhetsprofiler som använder inställningar för begränsade appar måste tilldelas grupper av användare.

## <a name="show-or-hide-apps"></a>Visa eller dölja appar

Gäller enheter som kör iOS 9,3 eller senare.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Lista över typer av appar**: skapa en lista över appar som ska visas eller döljas. Du kan visa eller dölja inbyggda appar och branschspecifika appar. På Apples webbplats finns en lista över [inbyggda Apple-appar](https://support.apple.com/HT208094). Alternativen är:

  - **Dolda appar**: Ange en lista med appar som är dolda för användarna. Användarna kan varken visa eller öppna de här apparna.
  
    Apple förhindrar att vissa inbyggda appar döljs. Du kan till exempel inte dölja **Inställningar** eller **plån boks** program på enheten. [Ta bort inbyggda Apple Apps](https://support.apple.com/HT208094) visar de appar som kan vara dolda.
  
  - **Synliga appar**: Ange en lista med appar som användarna ska kunna se och starta. Inga andra appar kan visas eller startas.

- **App-URL**: Ange Store-appens URL för den app som du vill visa eller dölja. Exempel:

  - Om du vill lägga till appen Microsoft Work Folders anger du `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` eller `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - Ange `https://itunes.apple.com/de/app/microsoft-word/id586447913` eller `https://apps.apple.com/de/app/microsoft-word/id586447913`för att lägga till Microsoft Word-appen.

  Du hittar webbadressen till en app genom att öppna iTunes App Store och söka efter appen. Du kan t.ex. söka efter `Microsoft Remote Desktop` eller `Microsoft Word`. Välj appen och kopiera webbadressen.

  Du kan även använda iTunes för att hitta appen och sedan använda uppgiften **Kopiera länk** för att hämta appens webbadress.
  
  Mer information om hur du hittar ett paket-ID finns i [så här hittar du paket-ID för en iOS-app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- **Appsamlings-ID**: Ange [appsamlings-ID](bundle-ids-built-in-ios-apps.md) för den app som du vill lägga till. Du kan visa eller dölja inbyggda appar och branschspecifika appar. På Apples webbplats finns en lista över [inbyggda Apple-appar](https://support.apple.com/HT208094).
- **Appnamn**: Ange namnet på den app som du vill lägga till. Du kan visa eller dölja inbyggda appar och branschspecifika appar. På Apples webbplats finns en lista över [inbyggda Apple-appar](https://support.apple.com/HT208094).
- **Utgivare**: Ange utgivaren av den app som du vill lägga till.

Om du vill lägga till appar kan du:

- **Lägg till**: Välj om du vill skapa en lista över appar.
- **Importera** en CSV-fil med information om appen, inklusive webbadressen. Använd formatet `<app url>, <app name>, <app publisher>`. Eller **Exportera** för att skapa en lista över begränsade appar som du har lagt till i samma format.

## <a name="wireless"></a>Trådlöst

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

Obs! för data nätverks växling (tips eller viktig information som hjälper till med kund förvirring): den här inställningen visas inte i mål enhetens hanterings profil. Det beror på att den här inställningen behandlas som en fjär renhets åtgärd, och varje gång statusen för data nätverks växling ändras på enheten kommer den att blockeras igen av Intune-tjänsten. Även om den inte finns i hanterings profilen fungerar den om den visas som lyckad från rapportering i administratörs konsolen. 
- **Dataroaming**: Välj **Blockera** om du vill förhindra dataroaming över det mobila nätverket. **Inte konfigurerad** (standard) tillåter dataroaming när enheten är i ett mobilnät.

  > [!IMPORTANT]
  > Den här inställningen behandlas som en fjär renhets åtgärd. Därför visas inte den här inställningen i hanterings profilen på enheten. Varje gång statusen för data nätverks växling ändras på enheten blockeras **data nätverks växling** av Intune-tjänsten. Om rapporterings statusen i Intune visar att den fungerar som den ska, vet du att den fungerar, även om inställningen inte visas i hanterings profilen på enheten.

- **Global bakgrundssamling under nätverksväxling**: **Blockera** förhindrar att funktionen för global bakgrundssamling används under nätverksväxling i mobilnätverket. **Inte konfigurerad** (standard) tillåter att enheten hämtar data, till exempel e-post, när den nätverksväxlar i ett mobilnät.
- **Röstsamtal**: Välj **Blockera** om du vil förhindra användare från att använda enhetens röstsamtalsfunktion. **Inte konfigurerad** (standard) tillåter röstsamtal på enheten.
- **Röstroaming**: Välj **Blockera** om du vill förhindra röstroaming över det mobila nätverket. **Inte konfigurerad** (standard) tillåter röstroaming när enheten är i ett mobilnät.
- **Internetdelning**: **Blockera** inaktiverar Internetdelning på användarnas enheter vid varje enhetssynkronisering. Den här inställningen kanske inte är kompatibel med vissa operatörer. **Inte konfigurerad** (standard) behåller användarens standardinställning för Internetdelning.

  > [!IMPORTANT]
  > Den här inställningen behandlas som en fjär renhets åtgärd. Därför visas inte den här inställningen i hanterings profilen på enheten. Varje gång statusen för personlig hotspot-status ändras på enheten blockeras **personlig hotspot** av Intune-tjänsten. Om rapporterings statusen i Intune visar att den fungerar som den ska, vet du att den fungerar, även om inställningen inte visas i hanterings profilen på enheten.

- **Regler för mobilanvändning (endast hanterade appar)** : Definiera de datatyper som hanterade appar kan använda i mobilnät. Alternativen är:
  - **Blockera användning av mobildata**: Blockera användningen av mobildata för **Alla hanterade appar** eller **Välj särskilda appar**.
  - **Blockera användning av mobildata vid nätverksväxling**: Blockera användningen av mobildata vid nätverksväxling för **Alla hanterade appar** eller **Välj särskilda appar**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Ändringar i inställningarna för användning av appmobildata**: Välj **Blockera** om du vill förhindra att inställningarna för användning av appmobildata ska kunna ändras. **Inte konfigurerad** (standard) tillåter att användaren bestämmer vilka appar som ska få använda mobildata.
- **Ändringar av mobilabonnemangsinställningar**: **Blockera** hindrar användarna från att ändra inställningar i mobilabonnemanget. **Inte konfigurerad** (standard) tillåter att användarna gör ändringar.

  Den här funktionen gäller för:  
  - iOS 11.0 och senare

- **Användar ändring av personlig hotspot**: när den är inställd på **blockera**kan användaren inte ändra inställningen för personlig hotspot. **Inte konfigurerad** (standard) tillåter slutanvändare att aktivera eller inaktivera sitt personliga hotspot.

  Om du blockerar den här inställningen och blockerar inställningen för **personlig hotspot** stängs den personliga hotspot-filen av.

  Den här funktionen gäller för:  
  - iOS 12.2 och senare

- **Anslut till trådlösa nätverk med endast konfigurationsprofiler**: **Kräv** tvingar enheten att endast använda trådlösa nätverk som har konfigurerats med Intunes konfigurationsprofiler. **Inte konfigurerad** (standard) tillåter enheten att använda andra trådlösa nätverk.
- **Wi-Fi är alltid aktiverat**: När inställningen är **nödvändig**stannar Wi-Fi i appen Inställningar. Den kan inte inaktive ras i inställningar eller i kontroll centret, även när enheten är i flyg Plans läge. **Inte konfigurerad** (standard) tillåter att användaren styr aktivering eller inaktive ring av Wi-Fi.

  Att konfigurera den här inställningen hindrar inte användare från att välja ett Wi-Fi-nätverk.

  Den här funktionen gäller för:  
  - iOS och iPad 13,0 och senare

## <a name="connected-devices"></a>Anslutna enheter

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **Handledsavkänning för parkopplad Apple Watch**: **Kräv** tvingar en parkopplad Apple Watch att använda handledsavkänning. När så krävs visar inte Apple Watch meddelanden när den inte bärs runt handleden. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

- **Kräv parkopplingslösenord för utgående AirPlay-förfrågningar**: **Kräv** ett parkopplingslösenord när användaren använder AirPlay för att strömma innehåll till andra Apple-enheter. **Inte konfigurerad** (standard) tillåter att användaren strömmar innehåll med AirPlay utan att behöva ange något lösenord.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **AirDrop**: **Blockera** förhindrar att AirDrop används på enheten. **Inte konfigurerad** (standard) tillåter att funktionen AirDrop används för att utbyta innehåll med enheter i närheten.
- **Apple Watch-ihopparning**: **blockera** förhindrar koppling med en Apple Watch. **Inte konfigurerad** (standard) tillåter att enheten parkopplas med en Apple Watch.
- **Ändring av Bluetooth**: **Blockera** förhindrar att slutanvändaren från att ändra enhetens Bluetooth-inställningar. **Inte konfigurerad** (standard) tillåter att användaren ändrar dessa inställningar.
- **Parkoppling av värd för att styra de enheter som en iOS-enhet kan parkopplas till**: **Inte konfigurerad** (standard) tillåter parkoppling så att administratören kan kontrollera vilka enheter som en iOS-enhet kan kopplas med. **Blockera** förhindrar parkoppling av värd.
- **Blockera AirPrint**: Välj **Blockera** om du vill förhindra att AirPrint-funktionen används på enheten. **Inte konfigurerat** (standard) tillåter användaren att använda AirPrint.
  - **Blockera lagring av AirPrint-autentiseringsuppgifter i nyckelringen**: **Blockera** förhindrar användning av nyckelring vid lagring av användarnamn och lösenord på enheten. **Inte konfigurerad** (standard) tillåter att AirPrint-användarnamnet och lösenordet lagras i nyckelringsappen.
  - **Kräv ett betrott TLS-certifikat för AirPrint**: **Kräv** tvingar enheten att använda betrodda certifikat för TLS-utskriftskommunikation.
  - **Blockera iBeacon-identifiering av AirPrint-skrivare**: **Blockera** förhindrar skadliga AirPrint Bluetooth-sändare från att nätfiska nätverkstrafik. **Inte konfigurerad** (standard) tillåter reklam för AirPrint-skrivare på enheten.
- **Blockera inställning av nya enheter i närheten**: **Blockera** inaktiverar uppmaningen om att konfigurera nya enheter som finns i närheten. **Inte konfigurerad** (standard) tillåter uppmaningar om att ansluta till andra Apple-enheter i närheten.

  Den här funktionen gäller för:  
  - iOS 11.0 och senare

- **Åtkomst till filer på USB-enhet**: enheter kan ansluta till och öppna filer på en USB-enhet. **Inaktivera** förhindrar enhets åtkomst till USB-enheten i Files-appen när en USB-enhet ansluts till enheten. Om du inaktiverar den här funktionen blockeras även slutanvändare från att överföra filer till en USB-enhet som är ansluten till en iPad. **Inte konfigurerad** (standard) tillåter åtkomst till en USB-enhet i appen filer.

  Den här funktionen gäller för:  
  - iOS och iPad 13,0 och senare

## <a name="keyboard-and-dictionary"></a>Tangentbord och ordlista

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Orddefinitionssökning**: **Blockera** förhindrar att användare markerar ett ord och sedan söka upp dess definition på enheten. **Inte konfigurerad** (standard) ger åtkomst till definitionssökningsfunktionen.
- **Tangentbord med förslag**: **Inte konfigurerad** (standard) tillåter tangentbord med förslag på ord som användaren kan ha nytta av. **Blockera** förhindrar den här funktionen.
- **Autokorrigering**: **Inte konfigurerad** (standard) låter enheten automatiskt korrigera felstavade ord. **Blockera** förhindrar att autokorrigering används.
- **Tangent bord med stavnings kontroll**: **inte konfigurerat** (standard) tillåter att stavnings kontroll används på enheten. **Blockera** tillåter stavningskontroll.
- **Kortkommandon:** **inte konfigurerat** (standard) kan använda kortkommandon på enheten. **Blockera** hindrar användaren från att använda kortkommandon.
- **Diktering**: **Blockera** förhindrar att användaren använder röstindata för att ange text. **Inte konfigurerat** (standard) tillåter användaren att använda röstindata.
- **QuickPath**: **inte konfigurerat** (standard) gör att användare kan använda QuickPath, vilket gör att du kan använda kontinuerliga ingångar på enhetens tangent bord. Användare kan skriva genom att svepa över nycklarna för att skapa ord. **Blockera** förhindrar användare från att använda QuickPath. 

  Den här funktionen gäller för:  
  - iOS 13,0 och iPad 13,0 och senare

## <a name="cloud-and-storage"></a>Moln och lagring

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **Krypterad säkerhetskopiering**: **Kräv** att säkerhetskopior av enheter måste vara krypterade.
- **Synkronisering av hanterade appar till molnet**: **Inte konfigurerad** (standard) tillåter att appar som du hanterar med Intune synkroniserar data till användarens iCloud-konton. **Blockera** förhindrar denna datasynkronisering till iCloud.
- **Blockera säkerhetskopiering av företagsbok**: Välj **Blockera** om du vill förhindra användarna från att säkerhetskopiera företagsböcker. **Inte konfigurerad** (standard) tillåter användarna att säkerhetskopiera dessa böcker.
- **Blockera synkronisering av företagsboksmetadata (anteckningar och markeringar)** : **Blockera** förhindrar synkronising av anteckningar och markeringar i företagsböcker. **Inte konfigurerad** (standard) tillåter synkronisering.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

- **Synkronisering av bildström till iCloud**: **Inte konfigurerad** (standard) låter användarna aktivera **My Photo Stream** på sina enheter och synkroniseras med iCloud och låta foton vara tillgängliga på användarens alla enheter. **Blockera** förhindrar bildströmssynkronisering till iCloud. Att blockera den här funktionen kan leda till data förlust. 
- **iCloud-bildbiblioteket**: Ställ in på **Blockera** om du vill inaktivera användning av iCloud-bildbiblioteket för att lagra foton och videoklipp i molnet. Alla bilder som inte har laddats ned till fullo från iCloud-bildbiblioteket till enheten tas bort från enheten. **Inte konfigurerad** (standard) tillåter att iCloud-bildbiblioteket används.
- **Delad bildström**: Välj **Blockera** om du vill inaktivera **iCloud-bilddelning** på enheten. **Inte konfigurerad** (standard) tillåter delad bildström.
- **Leverans**: **inte konfigurerat** (standard) gör det möjligt för användare att börja arbeta med en iOS-enhet och sedan fortsätta att fungera på en annan iOS-eller MacOS-enhet. **Blockera** förhindrar den här överlämningen.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Säkerhetskopiera till iCloud**: **Inte konfigurerad** (standard) tillåter användaren att säkerhetskopiera enheten till iCloud. **Blockera** hindrar användaren från att säkerhetskopiera enheten till iCloud.

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

- **Blockera iCloud-dokumentsynkronisering**: **Inte konfigurerad** (standard) tillåter synkronisering av dokument och nyckelvärden till ditt lagringsutrymme i iCloud. **Blockera** förhindrar iCloud från att synkronisera dokument och data.

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

- **Blockera synkronisering av iCloud-nyckelring**: Välj **Blockera** om du vill inaktivera synkronisering av autentiseringsuppgifter som lagras i nyckelringen till iCloud. **Inte konfigurerad** (standard) tillåter användare att synkronisera dessa autentiseringsuppgifter.

  Från och med iOS 13,0 kräver den här inställningen övervakade enheter.

## <a name="autonomous-single-app-mode"></a>Autonomt enkelt appläge

Använd inställningarna för att konfigurera iOS-enheter så att de kör specifika appar i autonomt enkelappsläge. När det här läget har konfigurerats och appen körs låses enheten. Bara den appen kan köras. Lägg t.ex. till en app som låter användarna göra ett prov på enheten. När appens åtgärder har slutförts, eller om du tar bort principen, återgår enheten till sitt normala tillstånd.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Appnamn**: Ange namnet på den app som du vill lägga till.
- **Appsamlings-ID**: Ange [samlings-ID](bundle-ids-built-in-ios-apps.md) för den önskade appen.
- **Lägg till**: Välj om du vill skapa en lista över appar.

Du kan även **Importera** en CSV-fil med listan över appnamn och deras samlings-ID:n. Eller **exportera** en befintlig lista som innehåller dessa appar.

## <a name="kiosk"></a>Helskärmsläge

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **App för att köra i helskärmsläge**: Välj den apptyp som du vill köra i helskärmsläge. Alternativen är:
  - **Inte konfigurerad** (standard): Inställningar för helskärmsläge tillämpas inte. Enheten körs inte i helskärmsläge.
  - **Store App**: Ange webbadressen till en app i iTunes App Store.
  - **Hanterad app**: Välj en app som du lagt till i Intune.
  - **Inbyggd app**: Ange den inbyggda appens [samlings-ID](bundle-ids-built-in-ios-apps.md).

- **AssistiveTouch**: **Kräv** att hjälpmedelsinställningen för AssistiveTouch ska finnas på enheten. Den här funktionen hjälper användarna med skärmgester som de behöver hjälp med. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Invertera färger**: **Kräv** att hjälpmedelsinställningen Invertera färger ska användas, så att användare med synsvårigheter kan anpassa skärmen. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Monoljud**: **Kräv** att hjälpmedelsinställningen för Monoljud ska finnas på enheten. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Röst kontroll**: **Kräv** aktiverar röst kontroll på enheten och gör det möjligt för användare att fullständigt styra operativ systemet med Siri-kommandon. **Inte konfigurerad** inaktiverar röst kontroll på enheten.

  Den här inställningen gäller för:  
  - iOS 13.0 och senare
  - iPadOS 13.0 och senare
  
  > [!TIP]
  > Om du har LOB-appar som är tillgängliga för din organisation, och de inte **är klara på** dag 0 när iOS 13,0-versioner, rekommenderar vi att du låter den här inställningen vara **konfigurerad**.

- **VoiceOver**: **Kräv** att hjälpmedelsinställningen VoiceOver ska finnas på enheten så att text på skärmen kan läsas upp. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Zooma**: **Kräv** att zoominställningen ska finnas på enheten så att användarna kan använda pekskärmen för att zooma in på skärmen. **Inte konfigurerad** kör eller aktiverar inte den här funktionen i helskärmsläge.
- **Lås automatiskt**: **blockera** förhindrar automatisk låsning av enheten. **Inte konfigurerad** tillåter denna funktion.
- **Ringsignalsväxling** – **Blockera** inaktiverar tyst läge på enheten. **Inte konfigurerad** tillåter denna funktion.
- **Skärmrotation**: **Blockera** hindrar att skärmrotationen ändras när användaren roterar enheten. **Inte konfigurerad** tillåter denna funktion.
- **Viloläge för skärm-knapp**: Välj **Blockera** om du vill inaktivera enhetens knapp för viloläge. **Inte konfigurerad** tillåter denna funktion.
- **Touch**: **Blockera** inaktiverar enhetens pekskärm. **Inte konfigurerad** tillåter användaren att använda pekskärmen.
- **Volym knappar**: **blockera** förhindrar användning av volym knapparna på enheten. **Inte konfigurerad** tillåter volym knapparna.
- **Assistivetouch-knapp**: **Tillåt** låter användarna använda funktionen AssistiveTouch. **Inte konfigurerad** inaktiverar den här funktionen.
- **Invertera färger**: **Tillåt** ändringar av färginvertering så att användarna kan justera funktionen för färginvertering. **Inte konfigurerad** inaktiverar den här funktionen.
- **Läs upp markerad text**: **Tillåt** att hjälpmedelsinställningen Läs upp markering finns på enheten. Den här funktionen läser upp text som användaren väljer. **Inte konfigurerad** inaktiverar den här funktionen.
- **Ändring av röst kontroll**: **Tillåt** användare att ändra läget för röst kontroll på sina enheter. **Inte konfigurerat** blockerar användare från att ändra läget för röst kontroll på sina enheter.

  Den här inställningen gäller för:  
  - iOS 13.0 och senare
  - iPadOS 13.0 och senare

- **VoiceOver-knapp**: **Tillåt** VoiceOver-ändringar så att användarna kan uppdatera VoiceOver-funktionen, t.ex. när det gäller hur snabbt texten ska läsas upp. **Inte konfigurerad** förhindrar VoiceOver-ändringar.
- **Zoomkontroll**: **Tillåt** att användaren kan ändra zoominställningarna. **Inte konfigurerad** förhindrar zoominställningar.

> [!NOTE]
> Innan du kan konfigurera en iOS-enhet för helskärmsläge måste du använda Apple Configurator-verktyget eller Apples enhetsregistreringsprogram för att placera enheten i övervakat läge. Information om hur du använder Apple Configurator-verktyget finns i Apples guide.
> Om den iOS-appen som du anger har installerats efter det att du har tilldelat profilen så går inte enheten över i helskärmsläge förrän den startas om.

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

- **Omarkerade e-postdomäner** > **Webbadress till e-postdomän**: Lägg till en eller flera webbadresser i listan. När slutanvändarna får ett e-postmeddelande från en annan domän än någon av de du har angett, så markeras e-postmeddelandet som ej betrott i iOS-e-postappen.

- **Hanterade webbdomäner** > **Webbadress till webbdomän**: Lägg till en eller flera webbadresser i listan. Dokument som laddas ned från de domäner du anger här anses vara hanterade. Den här inställningen gäller enbart för dokument som hämtas i Safari-webbläsaren.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

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
