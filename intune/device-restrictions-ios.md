---
title: Inställningar för enhetsbegränsningar i Microsoft Intune för iOS
titleSuffix: ''
description: Läs vilka Intune-inställningar du kan använda för att kontrollera enhetsinställningar och funktioner på enheter som kör iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2987ca7ce3a9b99249fc62fc7de5c9cca22b0b26
ms.sourcegitcommit: d1420a5d2d2c1da40cc4dac165ca9173c22323d3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34803830"
---
# <a name="microsoft-intune-ios-device-restriction-settings"></a>Inställningar för enhetsbegränsningar i Microsoft Intune för iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln visas inställningarna för enhetsbegränsningar i Microsoft Intune som du kan konfigurera för enheter som kör iOS.

## <a name="general"></a>Allmänt

-   **Dela användningsdata** – Tillåt eller blockera enheten från att skicka diagnostik- och telemetridata om användning till Apple.
-   **Sändning av diagnostikdata** – Tillåt eller blockera enheter från att skicka diagnostikdata till Apple.
-   **Skärmdump** – Tillåt användare att fånga innehållet på skärmen som en bild.
    - **Fjärrskärmsvisning i appen Klassrum (endast övervakat)** – Tillåt eller blockera appen Klassrum från att visa skärmarna på iOS-enheter.
    - **Skärmvisning utan uppmaning i appen Klassrum (endast övervakat)** – Om det är tillåtet kan lärarna tyst övervaka skärmarna på elevernas iOS-enheter med hjälp av appen Klassrum utan att eleverna vet om det.
-   **Ej betrodda TLS-certifikat** – Tillåt ej betrodda Transport Layer Security-certifikat på enheten.
-   **Företagsappförtroende** – Låter användaren välja att lita på appar som inte laddats ned från App Store.
- **Kontoändring (endast övervakat)** – När en blockering sker förhindras användaren från att ändra enhetsspecifika inställningar från iOS-appens inställningar, som t.ex. att skapa nya enhetskonton och ändra användarnamn eller lösenord.
Detta gäller även för inställningar som kan nås från appen för iOS-inställningar som E-post, Kontakter, Kalender, Facebook och Twitter. Detta gäller inte för appar med kontoinställningar som inte konfigureras från appen för iOS-inställningar, till exempel Microsoft Outlook-appen.
- **Aktivera begränsningar i enhetsinställningarna (endast övervakat)** -Tillåt användaren att konfigurera enhetsbegränsningar (föräldrakontroll) på enheten.
- **Användning av alternativet Radera allt innehåll och inställningar på enheten (endast övervakat)** -Tillåt användaren att använda alternativet att radera allt innehåll och alla inställningar på enheten.
- **Ändring av enhetens namn (endast övervakat)** – Tillåt användaren att ändra namnet på enheten.
- **Ändring av aviseringsinställningar (endast övervakat)** – Tillåt användaren att ändra enhetens aviseringsinställningar.
- **Ändring av behörighetsinställningar för företagsappar (endast övervakat)** – Låter användaren välja att lita på appar som inte laddats ned från App Store.
- **Ändra konfigurationsprofil (endast övervakat)** – Tillåt att användaren installerar konfigurationsprofiler.
- **Aktiveringslås (endast övervakat)** – Aktivera aktiveringslåset på övervakade iOS-enheter.

## <a name="configurations-requiring-supervision"></a>Konfigurationer som kräver övervakning

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
> Apple har bekräftat att vissa inställningar flyttas till endast övervakat läge under 2018. Vi rekommenderar att du tänker på detta när du använder de här inställningarna i stället för att vänta på att Apple ska migrera dem till endast övervakat läge:
> - Appinstallation av slutanvändare
> - Borttagning av app
> - FaceTime
> - Safari
> - iTunes
> - Barnförbjudet innehåll
> - Dokument och data i iCloud
> - Spel för flera personer
> - Lägg till spelcentervänner

## <a name="password"></a>Lösenord
-   **Lösenord** – Kräver att användaren måste ange ett lösenord för att få åtkomst till enheten.
    -   **Enkla lösenord** – Tillåt enkla lösenord som 0000 och 1234.
    -   **Krav på lösenordstyp** – Ange vilken typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt.
    -   **Antal icke-alfanumeriska tecken i lösenord** – Ange det antal symboltecken i lösenordet (som **#** eller **@**) som måste ingå i lösenordet.
    -   **Minsta längd på lösenord** – Ange det minsta antalet tecken som lösenordet måste innehålla.
    -   **Antal felaktiga inloggningar innan enheten rensas** – Ange antalet unika felaktiga lösenordsförsök innan den här inställningen rensar enheten.
    -   **Maximalt antal minuter efter skärmlås innan ett lösenord krävs** <sup>1</sup> – Ange hur länge enheten kan vara inaktiv innan användaren måste ange sitt lösenord på nytt.
    -   **Maximalt antal minuter av inaktivitet innan skärmen låses**<sup>1</sup> – Ange hur många minuter som ska förflyta innan skärmen stängs av.
    -   **Lösenordets giltighetstid (dagar)** – Ange antal dagar innan lösenordet för enheten måste ändras.
    -   **Förhindra återanvändning av tidigare lösenord** – Ange antalet tidigare lösenord som enheten kommer ihåg.
    -   **Upplåsning med fingeravtryck** – Tillåt att fingeravtryck används för att låsa upp kompatibla enheter.
- **Ändring av lösenkod (endast övervakat)** – Hindrar att lösenkoden ändras, läggs till eller tas bort.
    - **Ändring av fingeravtryck (endast övervakat)** – Hindrar att användaren ändar, lägger till eller tar bort TouchID-inställningar.

<sup>1</sup> När du konfigurerar inställningarna **Maximalt antal minuter av inaktivitet innan skärmen låses** och **Maximalt antal minuter efter skärmlås innan ett lösenord krävs** tillämpas de i följd. Om du t.ex. ställer in värdet för båda inställningarna till **5** minuter så stängs skärmen av automatiskt efter fem minuter. Enheten låses efter ytterligare fem minuter. Om användaren däremot stänger av skärmen manuellt så tillämpas den andra inställningen omedelbart. När användaren i det här exemplet har stängt av skärmen låses enheten fem minuter senare.

## <a name="locked-screen-experience"></a>Låsskärm

-   **Åtkomst till Kontrollcenter när enheten är låst** – Tillåt användare att komma åt kontrollcenterappen när enheten är låst.
-   **Notiser när enheten är låst** – Tillåter användaren att få åtkomst till aviseringsvyn utan att låsa upp enheten.
-   **Sparbok när enheten är låst** – Tillåt användare att komma åt appen Sparbok när enheten är låst.
-   **Dagsvyn när enheten är låst** – Tillåt användare att se vyn Idag när enheten är låst.

## <a name="app-store-doc-viewing-gaming"></a>App Store, dokumentvisning, spel


-   **App Store** – Blockera åtkomst till App Store på övervakade enheter.
    - **Installera appar från App Store (endast övervakat)** – Blockerar App Store från enhetens startskärm. Användarna kan fortsätta att använda iTunes eller Apple Configurator-verktyget för att installera appar.
    - **Automatisk nedladdning av appar (endast övervakat)** – Hindrar appar som har köpts på en annan iOS-enhet från att laddas ned till denna enhet.
-   **Lösenord till App Store** – Kräv att användarna anger ett lösenord innan de kan besöka App Store.
-   **Köp via app** – Tillåt att inköp görs från en app som körs.
-   **Stötande innehåll i iTunes-musik, podcast eller nyheter (endast övervakat)** – Tillåt att enheten får åtkomst i butiken till innehåll som är klassificerat som vuxet (olämpligt för barn).
-   **Ladda ned innehåll från iBook-butiken flaggat som Erotik** – Tillåt att användaren laddar ned innehåll från iBook-butiken som flaggats som Erotik.
-   **Visa företagsdokument i ohanterade appar** – Tillåt att företagets dokument visas i alla appar.<br>**Exempel:** Du vill förhindra att användare sparar filer från OneDrive-appen i Dropbox. Konfigurera den här inställningen till Nej. När enheten har hämtat principen (till exempel efter en omstart) kommer den inte längre att tillåta att spara.
-   **Visa dokument som inte gäller företag i företagsappar** – Tillåt att alla dokument visas i företagshanterade appar.
-   **Behandla AirDrop som ett ohanterat mål** – Stoppar hanterade appar från att kunna skicka data. Airdrop.
-   **Lägga till Game Center-vänner (endast övervakat)** – Tillåt användaren att lägga till vänner i Game Center.
-   **Game Center (endast övervakat)**  – Blockera eller aktivera användning av appen Game Center.
-   **Spel för flera personer (endast övervakat)** – Tillåt användaren att spela spel för flera personer på enheten.
-   **Klassificeringsregion** – Välj den klassificeringsregion som du vill konfigurera tillåtna hämtningsbara filer för, och välj tillåtna klassificeringar för **filmer** och **TV-program**.
-   **Appar** – Välj åldersklassificering för de appar som användarna kan ladda ned eller välj **Tillåt alla appar**.

## <a name="built-in-apps"></a>Inbyggda appar

-   **Kamera** – Ange om kameran på enheten får användas.
    -   **FaceTime** -Tillåt att appen FaceTime får användas på enheten.
-   **Siri** – Tillåt användning av röstassistenten Siri på enheten.
    -   **Tillåt Siri när enheten är låst** – Tillåt användning av röstassistenten Siri på enheten när den är låst.
    -   **Filtrering av grovt språk i Siri (endast övervakat)** – Förhindrar att Siri från dikterar eller talar ett olämpligt språk.
    -   **Siri skickar frågor om innehåll som skapats av användare från Internet (endast övervakat)** – Ger Siri åtkomst till webbplatser för att kunna besvara frågor.
- **Apple News (endast övervakat)** – Tillåt att appen Apple News används.
- **iBooks-butik (endast övervakat)** – Tillåt användare att bläddra bland och köpa böcker i iBooks-butiken.
- **Appen Meddelanden på enheten (endast övervakat)** – Tillåt att appen Meddelanden för att skicka och läsa meddelanden.
- **Podcaster (endast övervakat)** – Tillåt att appen Podcaster används.
- **Musiktjänst (endast övervakat)** – Tillåt att appen Musiktjänst används.
- **iTunes Radio-tjänst (endast övervakat)** – Tillåt att appen iTunes Radio-tjänst används.
- **Ändringar av inställningarna för appen Hitta mina vänner (endast övervakat)** – Tillåt användaren att ändra inställningarna för appen Hitta mina vänner.
- **Spotlight-sökning för att returnera resultat från Internet (endast övervakat)** – Låt Spotlight-sökningen ansluta till Internet så att ytterligare resultat kan tillhandahållas.

## <a name="restricted-apps"></a>Begränsade appar

Du kan konfigurera en av följande listor i listan med begränsade appar:

- Listan **Otillåtna appar** – Ange de appar (som inte hanteras av Intune) som användarna inte får installera och köra. Användarna hindras inte från att installera en förbjuden app, men om de gör det rapporteras det till dig.
- Listan **Godkända appar** – Ange de appar som användare tillåts att installera. Användarna får inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt. Användare hindras inte från att installera en app som inte finns med på listan över godkända appar, men om de gör det rapporteras detta till dig.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare samt webbadressen till appen i appbutiken.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Så här anger du webbadressen till appen i butiken

Om du vill ange en app-URL i applistan använder du följande format:

Använd en sökmotor för att hitta den app du vill använda i iTunes App Store och öppna appens sida.
Kopiera sidans URL och använd den som URL för att konfigurera listan över tillåtna eller förbjudna appar som du vill köra i helskärmsläge.
Enhetsprofiler som innehåller inställningar för begränsade appar måste tilldelas grupper av användare.

Exempel: Sök efter Microsoft Word för iPad. Den URL som du använder är https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> Du kan även använda iTunes för att hitta appen och sedan använda kommandot **Kopiera länk** för att hämta appens webbadress.

### <a name="additional-options"></a>Ytterligare alternativ

Du kan också klicka på **Importera** för att fylla i listan från en csv-fil i formatet <*app-url*>, <*appnamn*>, <*appens utgivare*>, eller klicka på **Exportera** för att skapa en csv-fil med innehållet i listan över begränsade appar i samma format.

## <a name="show-or-hide-apps-supervised-only"></a>Visa eller dölj appar (endast övervakat)

I listan för att visa eller dölja appar kan du konfigurera en av följande listor (kräver övervakade enheter som kör iOS 9.3 eller senare).

En lista med **dolda appar** – Ange en lista med appar som är dolda för användarna. Användare kan inte visa eller starta dessa appar.
En lista med **synliga appar** – Ange en lista med appar som användarna ska kunna se och starta. Inga andra appar kan visas eller startas.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare samt webbadressen till appen i appbutiken.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Så här anger du webbadressen till appen i butiken

Om du vill ange en app-URL i applistan använder du följande format:

Använd en sökmotor för att hitta den app du vill använda i iTunes App Store och öppna appens sida.
Kopiera sidans URL och använd den som URL för att konfigurera listan över tillåtna eller förbjudna appar som du vill köra i helskärmsläge.

Exempel: Sök efter Microsoft Word för iPad. Den URL som du använder är https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> Du kan också använda iTunes-programmet för att hitta appen och sedan använda kommandot **Kopiera länk** för att hämta appens webbadress.

### <a name="additional-options"></a>Ytterligare alternativ

Du kan också klicka på **Importera** för att fylla i listan från en csv-fil i formatet <*app-url*>, <*appnamn*>, <*appens utgivare*>, eller klicka på **Exportera** för att skapa en csv-fil med innehållet i listan över dolda eller synliga appar i samma format.


## <a name="wireless"></a>Trådlöst
-   **Dataroaming** – Tillåt dataroaming när enheten använder ett mobilnät.
-   **Hämtning av global bakgrund under nätverksväxling** – Tillåt att enheten att hämtar data, t.ex. e-post, när den nätverksväxlar i ett mobilnät.
-   **Röstsamtal** – Tillåt att röstsamtalsfunktionen används på enheten.
-   **Röstroaming** – Tillåt att röstroaming används när enheten är ansluten till ett mobilnät.
-   **Ändringar av inställningar för mobildataanvändning (endast övervakat)** – Tillåt användaren att kontrollera vilka appar som får använda mobildata.
-   **Internetdelning** – Tillåter inte att enheten används för Internetdelning. Den här inställningen kanske inte är kompatibel med vissa operatörer.
-   **Anslut till trådlösa nätverk med endast konfigurationsprofiler (endast övervakat)** – Tillåter endast att enheten ansluter till trådlösa nätverk som har konfigurerats med en Wi-Fi-profil i Intune.

- **Regler för mobilanvändning (endast hanterade appar)** – Gör det möjligt att definiera de datatyper som hanterade appar kan använda i mobilnät. Välj mellan:
    - **Blockera användning av mobildata** – Du kan blockera användningen av mobildata för ** Alla hanterade appar** eller **Välj särskilda appar**.
    - **Blockera användning av mobildata vid nätverksväxling** – Du kan blockera användningen av mobildata för ** Alla hanterade appar** eller **Välj särskilda appar**.

## <a name="connected-devices"></a>Anslutna enheter

-   **AirDrop (endast övervakat)** – Tillåt att funktionen AirDrop används för att utbyta innehåll med enheter i närheten.
-   **Apple Watch-parkoppling (endast övervakat)** – Tillåt att enheten parkopplas med en Apple Watch.
-   **Handledsavkänning för parkopplad Apple Watch** – När den här inställningen är aktiverad visas meddelanden bara när användaren bär sin Apple Watch runt handleden.
-   **Ändring av Bluetooth (endast övervakat)** – Blockerar slutanvändaren från att ändra Bluetooth-inställningar på enheten.
-   **Parkoppling av värd för att styra de enheter som en iOS-enhet kan parkopplas till (endast övervakat)** – Tillåt parkoppling så att administratören kan kontrollera vilka enheter som en iOS-enhet kan kopplas med.
-   **Kräv parkopplingslösenord för utgående AirPlay-förfrågningar** – Kräv ett parkopplingslösenord när användaren använder AirPlay för att strömma innehåll till andra Apple-enheter.

## <a name="keyboard-and-dictionary"></a>Tangentbord och ordlista

-   **Namn på sökdefinition (endast övervakat)** – Tillåt den iOS-funktion som gör att du kan markera ett ord och leta upp dess definition.
-   **Förutseende tangentbord (endast övervakat)** – Tillåt användning av förutseende tangentbord som föreslår ord som användaren kanske vill använda.
-   **Autokorrigering (endast övervakat)** – Låter enheten automatiskt korrigera felstavade ord.
-   **Tangentbord med stavningskontroll (endast övervakat)** – Tillåter att stavningskontroll används.
-   **Kortkommandon (endast övervakat)** – Tillåter att kortkommandon används.
-   **Diktering (endast övervakat)** – Hindrar användaren från att använda röstindata för att ange text.

## <a name="cloud-and-storage"></a>Moln och lagring
-   **Säkerhetskopiera till iCloud** – Tillåt användare att säkerhetskopiera enheten till iCloud.
-   **Dokumentsynkronisering till iCloud (endast övervakat)** – Tillåt synkronisering av dokument och nyckelvärden till ditt lagringsutrymme i iCloud.
-   **Synkronisering av Bildström till iCloud** – Låter användare aktivera **My Photo Stream** (Min bildström) på sina enheter vilket gör att foton kan synkroniseras till iCloud och vara tillgängliga på alla användarnas enheter.
-   **Krypterad säkerhetskopiering** – Kräv att säkerhetskopior av enheter måste vara krypterade.
-   **iCloud-bildbiblioteket** – Om det är inställt på **Nej** inaktiveras användningen av iCloud-bildbiblioteket som låter användare lagra foton och videoklipp i molnet.   Alla bilder som inte har laddats ned till fullo från iCloud-bildbiblioteket till enheten tas bort från enheten om detta är inställt på **Nej**.
-   **Synkronisering av hanterade appar till molnet** – Tillåt att appar som du hanterar med Intune synkroniserar data till användarnas iCloud-konton.
-   **Delad bildström** – Ställ in på **Nej** om du vill inaktivera **iCloud-bilddelning** på enheten.
-   **Aktivitetsfortsättning** – Tillåt användare att återuppta det arbete som de påbörjat på en iOS-enhet på en annan iOS- eller macOS-enhet (överlämning).

## <a name="autonomous-single-app-mode-supervised-only"></a>Autonomt enkelt appläge (endast övervakat)

Använd inställningarna för att konfigurera iOS-enheter så att de kör angivna appar i autonomt enkelt appläge. När det här läget är konfigurerat och appen körs kommer enheten att låsas så att den endast kan köra den appen. Ett exempel på detta är när du konfigurerar en app som gör att användarna kan genomföra ett test på enheten. När appens åtgärder har slutförts, eller om du tar bort principen, återgår enheten till sitt normala tillstånd.

### <a name="settings"></a>Inställningar

- **Appnamn** – Ange det namn på appen som visas i applistan på det här bladet.
- **Appsamlings-id** – Ange samlings-ID för appen. Hjälp finns i **Referens till samlings-ID för inbyggda iOS-appar** i det här avsnittet.

När du har angett varje appnamn och appsamlings-ID väljer du **Lägg till** för att lägga till dem i listan.

- **Importera** – Importera en fil med kommaavgränsade värden (.csv), som innehåller en lista med appnamn och deras associerade appsamlings-ID:n.
- **Exportera** – Exportera appnamnen och associerade appsamlings-ID:n som du har konfigurerat, till en fil med kommaavgränsade värden (.csv).

### <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referens till samlings-ID för inbyggda iOS-appar

I listan visas appsamlings-ID:n för några vanliga inbyggda iOS-appar. Kontakta programvaruleverantören för att hitta appsamlings-ID:n för andra appar.

```
,com.apple.AppStore,App Store,Apple
,com.apple.calculator,Calculator,Apple
,com.apple.mobilecal,Calendar,Apple
,com.apple.camera,Camera,Apple
,com.apple.mobiletimer,Clock,Apple
,com.apple.compass,Compass,Apple
,com.apple.MobileAddressBook,Contacts,Apple
,com.apple.facetime,FaceTime,Apple
,com.apple.mobileme.fmf1,Find Friends,Apple
,com.apple.mobileme.fmip1,Find iPhone,Apple
,com.apple.gamecenter,Game Center,Apple
,com.apple.mobilegarageband,GarageBand,Apple
,com.apple.Health,Health,Apple
,com.apple.iBooks,iBooks,Apple
,com.apple.MobileStore,iTunes Store,Apple
,com.apple.itunesu,iTunes U,Apple
,com.apple.Keynote,Keynote,Apple
,com.apple.mobilemail,Mail,Apple
,com.apple.MapsMaps,Apple
,com.apple.MobileSMS,Messages,Apple
,com.apple.Music,Music,Apple
,com.apple.news,News,Apple
,com.apple.mobilenotes,Notes,Apple
,com.apple.Numbers,Numbers,Apple
,com.apple.Pages,Pages,Apple
,com.apple.Photo-Booth,Photo Booth,Apple
,com.apple.mobileslideshow,Photos,Apple
,com.apple.podcasts,Podcasts,Apple
,com.apple.reminders,Reminders,Apple
,com.apple.MobileSafari,Safari,Apple
,com.apple.Preferences,Settings,Apple
,com.apple.stocks,Stocks,Apple
,com.apple.tips,Tips,Apple
,com.apple.videos,Videos,Apple
,com.apple.VoiceMemos,VoiceMemos,Apple
,com.apple.Passbook,Wallet,Apple
,com.apple.Bridge,Watch,Apple
,com.apple.weather,Weather,Apple
```


## <a name="kiosk-supervised-only"></a>Helskärm (endast övervakat)
-   **App som körs i helskärmsläge** – Välj **Hanterade appar** om du vill välja en app som du har lagt till Intune, eller **Store-app** om du vill ange URL:en till appen i Store. Inga andra appar tillåts köra på enheten. Mer hjälp finns i "Så här anger du webbadresser till appbutiker" senare i det här avsnittet.
    -   **AssistiveTouch** – Aktivera eller inaktivera hjälpmedelsinställningen **AssistiveTouch** som hjälper användare att utföra gester på skärmen som annars kan vara svåra att utföra.
    -   **Invertera färger** – Aktivera eller inaktivera hjälpmedelsinställningen Invertera färger som anpassar skärmen för att hjälpa användare med synfel.
    -   **Monoljud** – Aktivera eller inaktivera hjälpmedelsinställningen Monoljud.
    -   **VoiceOver** – Aktivera eller inaktivera hjälpmedelsinställningen **VoiceOver** som läser upp text på enhetens skärm.
    -   **Zoom** – Aktivera eller inaktivera hjälpmedelsinställningen **Zoom** som gör att användare kan använda pekskärmen för att zooma in det som visas på enheten.
    -   **Autolås** – Aktivera eller inaktivera automatisk låsning av enheten.
    -   **Ringsignalsknapp** – Aktiverar eller inaktiverar tyst läge på enheten.
    -   **Skärmrotation** – Aktivera eller inaktivera ändring av skärmens orientering när användaren roterar enheten.
    -   **Viloläge för skärmknapp** – Aktivera eller inaktivera enhetens knapp för viloläge.
    -   **Touch** – Aktivera eller inaktivera enhetens pekskärm.
    -   **Volymknappar** – Aktivera eller inaktivera användningen av enhetens volymknappar.
    -   **AssistiveTouch-knapp** – Aktivera eller inaktivera anpassning av funktionen AssistiveTouch.
    -   **Invertera färger-knapp** – Aktivera eller inaktivera justeringar i funktionen för inverterade färger.
    -   **Läs upp markerad text** – Aktivera eller inaktivera hjälpmedelsinställningen Läs upp markerad text som kan läsa upp den text som användaren markerar.
    -   **VoiceOver-knapp** – Aktivera eller inaktivera justeringar av VoiceOver-funktionen så att användare kan justera VoiceOver-funktionen (t.ex. hur snabbt texten ska läsas upp).
    -   **Zoomkontroll** – Aktivera eller inaktivera justeringar i zoomfunktionen.

>[!NOTE]
> Innan du kan konfigurera en iOS-enhet för helskärmsläge måste du använda Apple Configurator-verktyget eller Apples enhetsregistreringsprogram för att placera enheten i övervakat läge. Mer information om Apple Configurator-verktyget finns i Apples dokumentation.
>Om iOS-appen som du anger har installerats efter det att du har tilldelat profilen kommer enheten inte att gå över i helskärmsläge förrän den startas om.

## <a name="safari"></a>Safari
-   **Safari (endast övervakat)** – Ange om webbläsaren Safari kan användas på enheten.
-   **Autofyll** – Tillåt användare att ändra inställningarna för Autofyll i webbläsaren.
-   **Cookies** – Tillåt webbläsaren att använda cookies.
-   **JavaScript** – Tillåt att JavaScript körs i webbläsaren.
-   **Bedrägerivarningar** – Tillåt bedrägerivarningar i webbläsaren.
-   **Popup-fönster** – Aktivera eller inaktivera webbläsarens blockering av popup-fönster.


## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Avmarkerade e-postdomäner

I fältet **Webbadress till e-postdomän** lägger du till en eller flera webbadresser i listan. När slutanvändarna får ett e-postmeddelande från en annan domän än de du har konfigurerat, markeras e-postmeddelandet som ej betrott i iOS e-postapp.


### <a name="managed-web-domains"></a>Hanterade webbdomäner

I fältet **Webbadress till webbdomän** lägger du till en eller flera webbadresser i listan. Dokument som laddas ned från de domäner du anger här anses vara hanterade. Den här inställningen gäller enbart för dokument som hämtas i Safari-webbläsaren.


### <a name="safari-password-autofill-domains"></a>Fyll i lösenord automatiskt på Safari-domäner

I fältet **Domänwebbadress** lägger du till en eller flera webbadresser i listan. Användarna kan bara spara webblösenord från webbadresser i den här listan. Den här inställningen gäller enbart för Safari-webbläsaren, samt för iOS 9.3 och senare enheter i övervakat läge. Om du inte anger någon webbadress, kan lösenorden sparas från alla webbplatser.
