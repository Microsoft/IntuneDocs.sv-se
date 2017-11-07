---
title: "iOS-principinställningar"
description: "Skapa principer som styr inställningar och funktioner på iOS-enheter som du hanterar med Intune."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 58be7ad24da7e4eadc1c67016979396114799bd8
ms.sourcegitcommit: 0f877251e6adf4e45b918cc8dc9193626727f2d9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2017
---
# <a name="ios-policy-settings-in-microsoft-intune"></a>Principinställningar för iOS i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i iOS-enheter. Du kan också använda verktyget Apple Configurator för att skapa anpassade inställningar som inte är tillgängliga från Intune.

## <a name="general-configuration-policy-settings"></a>Generella inställningar för konfigurationsprinciper

Använd Microsoft Intunes **allmänna konfigurationsprincip** för iOS om du vill konfigurera inställningar för:

-   **Allmänna enhets- och säkerhetsinställningar**. Välj i en lista med fördefinierade inställningar som du kan använda för att styra många av enhetens egenskaper och funktioner.

-   **Helskärmsläge**. Lås en enhet så att bara vissa funktioner fungerar. Du kan t.ex. tillåta att enheten ska kunna köra endast en hanterad app som du anger, eller så kan du inaktivera volymknapparna på en enhet. De här inställningarna kan användas på en demonstrationsmodell av en enhet, eller en enhet som bara används för att utföra en enda funktion, till exempel i en butikskassa.

-   **Kompatibla och icke-kompatibla appar**. Ange en lista över appar i företaget som är kompatibla eller inkompatibla. För Android- och iOS-enheter kan **Inkompatibilitetsrapporter för appar** användas för att visa om de appar du har angett i listan är kompatibla med appar som användare har installerat (men det går inte att blockera installationen av appen).

> [!TIP]
> Du kan konfigurera villkor för användarna för att säkerställa att de är medvetna om att apparna på deras enheter, även personliga appar, kommer att utvärderas och inkompatibla appar antingen kommer att blockeras eller rapporteras som inkompatibla. Användarna måste acceptera dessa villkor innan de kan registrera sina enheter och använda företagsportalen för att hämta appar. Mer information om de allmänna villkoren finns i [Principinställningar för användarvillkor i Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Om den inställning som du söker efter inte visas i det här avsnittet kan du eventuellt skapa den med hjälp av en anpassad iOS-princip med vilken du kan importera inställningar som du har skapat med hjälp av [Apple Configurator-verktyget](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Mer information finns i "Anpassade principinställningar" senare i det här avsnittet.

### <a name="security-settings"></a>Säkerhetsinställningar
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Ange om användaren måste ange ett lösenord för att komma åt sin enhet.|
|**Lösenordstyp krävs**|Ange vilken typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt.|
|**Antal avancerade tecken som krävs i lösenord**|Ange antalet symboltecken (till exempel **#** eller **@**) som måste tas med i lösenordet.|
|**Minsta längd på lösenord**|Ange det minsta antalet tecken som lösenordet måste innehålla.|
|**Tillåt enkla lösenord**|Tillåt enkla lösenord som **0000** och **1234**.|
|**Antal tillåtna, upprepade felinloggningar innan enheten rensas**|Ange antalet misslyckade inloggningsförsök innan den här inställningen rensar enheten.|
|**Antal minuters inaktivitet innan lösenord krävs**<sup>1</sup>|Ange hur länge enheten kan vara inaktiv innan användaren måste ange sitt lösenord på nytt.|
|**Lösenordets giltighetstid (i dagar)**|Ange antalet dagar innan lösenordet måste ändras.|
|**Kom ihåg tidigare lösenord**|Ange om användaren kan använda lösenord som de har använt tidigare.|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Ange antalet tidigare använda lösenord som enheten sparar.|
|**Minuter av inaktivitet innan skärmen stängs av**<sup>1</sup>|Ange antalet minuter innan enhetens skärm är inaktiverad.|
|**Tillåt fingeravtrycksupplåsning**|Tillåt att enheten kan låsas upp med ett fingeravtryck.|
<sup>1</sup> När du konfigurerar inställningarna **Minuter av inaktivitet innan skärmen stängs av** och **Minuter av inaktivitet innan lösenord måste anges** för iOS-enheter tillämpas de i följd. Om du t.ex. ställer in värdet för båda inställningarna till **5** minuter så stängs skärmen av automatiskt efter 5 minuter, och enheten låses efter ytterligare 5 minuter. Om användaren däremot stänger av skärmen manuellt så tillämpas den andra inställningen omedelbart. Efter det att användaren i det här exemplet har stängt av skärmen låses enheten 5 minuter senare.

### <a name="system-settings"></a>Systeminställningar
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt skärmdump**|Tillåt användare att fånga innehållet på skärmen i en bild.|
|**Tillåt kontrollcenter på låsskärm**|Tillåt användare att komma åt kontrollcenterappen när enheten är låst.|
|**Tillåt notisvy på låsskärm**|Tillåter användaren att få åtkomst till aviseringsvyn utan att låsa upp enheten.|
|**Tillåt dagsvy på låsskärm**|Tillåt användare att visa aviseringar när enheten är låst.|
|**Tillåt ej betrodda TLS-certifikat**|Tillåt ej betrodda Transport Layer Security-certifikat på enheten.|
|**Tillåt sändning av diagnostikdata**|Tillåt eller blockera enheter från att skicka diagnostikdata till Apple.|
|**Tillåt sparbok när låst**|Tillåt användare att komma åt appen Sparbok när enheten är låst.|

### <a name="cloud-settings-for-documents-and-data"></a>Molninställningar för dokument och data
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt säkerhetskopiering till iCloud**|Tillåt användare att säkerhetskopiera enheten till iCloud.|
|**Tillåt dokumentsynkronisering till iCloud**|Tillåt synkronisering av dokument och nyckel/värde till ditt lagringsutrymme i iCloud.|
|**Tillåt bildströmssynkronisering till iCloud**|Låter användare aktivera **My Photo Stream** (Min bildström) på sina enheter vilket gör att foton kan synkronisera till iCloud och vara tillgängliga på alla användarnas enheter.|
|**Kräv krypterad säkerhetskopiering**|Kräv att säkerhetskopior av enheter måste vara krypterade.|
|**Tillåt att hanterade appar synkroniserar data till iCloud**|Tillåt att appar som du hanterar med Intune synkroniserar data till användarnas iCloud-konto.|
|**Tillåt Handoff för att fortsätta med aktiviteter på en annan enhet**|Tillåt användare att återuppta det arbete som de påbörjat på en iOS-enhet på en annan iOS- eller Mac OS X-enhet.|
|**Tillåt iCloud-bilddelning**|Ställ in på **Nej** för att inaktivera **iCloud-bilddelning** på enheten.|
|**Tillåt iCloud-bildbibliotek**|Om det är inställt på **Nej**, inaktiveras användningen av iCloud-bildbiblioteket som låter användare att lagra foton och videoklipp i molnet.   Alla bilder som inte har laddats ned till enheten helt från iCloud-bildbiblioteket tas bort från enheten om detta är inställt på **Nej**.|

### <a name="application-settings-for-the-browser"></a>Programinställningar för webbläsaren
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt Safari**|Ange om webbläsaren Safari kan användas på enheten.|
|**Tillåt autofyll**|Tillåt användare att ändra inställningarna för Komplettera automatiskt i webbläsaren.|
|**Tillåt blockering av popup-fönster**|Aktiverar eller inaktiverar webbläsarens blockering av popup-fönster.|
|**Tillåt cookies**|Tillåt webbläsaren att använda cookies.|
|**Tillåt Java-skript**|Tillåt att Java-skript körs i webbläsaren.|
|**Tillåt bedrägerivarning**|Tillåt bedrägerivarningar i webbläsaren.|

### <a name="application-settings-for-apps"></a>Programinställningar för appar
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt installation av appar**|Tillåt åtkomst till appbutiken och installation av appar på enheten.|
|**Kräv lösenord för åtkomst till appbutik**|Kräv att användarna anger ett lösenord innan de kan besöka appbutiken.|
|**Tillåt köp via app**|Tillåt att inköp görs från en app som körs.|
|**Tillåt hanterade dokument i andra ohanterade appar**|Tillåt visning av företagsdokument i vilken app som helst.<br>**Exempel:** Du vill förhindra att användare sparar filer från OneDrive-appen i Dropbox. Konfigurera den här inställningen till Nej. När enheten har hämtat principen (till exempel efter en omstart) kommer den inte längre att tillåta att spara.|
|**Tillåt ohanterade dokument i andra hanterade appar**|Tillåt visning av valfria dokument i hanterade företagsappar.|
|**Tillåt videokonferens**|Tillåt videokonferensappar, till exempel FaceTime, på enheten.|
|**Tillåt användaren att betro nya företagsapputvecklare**|Låter användaren välja att lita på appar som inte laddats ned från App Store.|


### <a name="application-settings-for-games"></a>Programinställningar för spel
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt att Game Center-vänner läggs till**|Tillåt användaren att lägga till vänner i Game Center.|
|**Tillåt spel för flera personer**|Tillåt användaren att spela spel för flera personer på enheten.|

### <a name="application-settings-for-media-content"></a>Programinställningar för medieinnehåll
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Klassificeringsregion**|Välj en region och välj sedan högsta tillåtna klassificering som användare får ladda ned för **Filmer**, **TV-program** och **Appar**.|
|**Tillåt innehåll för vuxna i mediebutik**|Tillåt att enheten får åtkomst till innehåll som är klassificerade som för vuxna i butiken.|
|**Tillåt att användaren laddar ned innehåll från iBook-butiken som flaggats som ”Erotik”**|Tillåt att användare laddar ned böcker i kategorin Erotik.|


### <a name="device-capabilities-settings-for-hardware"></a>Enhetskapacitetsinställningar för maskinvara
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt kamera**|Ange om kameran på enheten får användas.|
|**Tvinga parkopplade Apple Watches att använda handledsavkänningen**|När den här inställningen är aktiverad visas meddelanden bara när användaren bär sin Apple Watch runt handleden.|
|**Kräv ett kopplat lösenord för utgående AirPlay-begäranden**|Kräv ett kopplat lösenord när användaren använder AirPlay för att strömma innehåll till andra Apple-enheter.|

### <a name="device-capabilities-settings-for-cellular"></a>Enhetskapacitetsinställningar för mobil
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt röstnätverksväxling**|Tillåt röstnätverksväxling när enheten är på ett mobilnät.|
|**Tillåt datanätverksväxling**|Tillåt datanätverksväxling när enheten använder ett mobilnät.|
|**Tillåt hämtning av global bakgrund under nätverksväxling**|Tillåt att enheten att hämtar data, till exempel e-post när den nätverksväxlar på ett mobilnät.|

### <a name="device-capabilities-settings-for-features"></a>Enhetskapacitetsinställningar för funktioner
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt Siri**|Tillåt användning av röstassistenten Siri på enheten.|
|**Tillåt Siri när enheten är låst**|Tillåt användning av röstassistenten Siri på enheten när den är låst|
|**Tillåt röstsamtal**|Tillåt användning av röstsamtalsfunktionen på enheten.|
|**Tillåt inte Airdrop från hanterade appar**|Hindrar hanterade appar från att kunna skicka data via Airdrop.|


### <a name="settings-for-compliant-and-noncompliant-apps"></a>Inställningar för kompatibla och icke-kompatibla appar
I listan över **kompatibla &amp; inkompatibla appar** skapar du en lista över kompatibla eller inkompatibla appar med hjälp av följande information:

> [!NOTE]
> En enda princip kan innehålla endast en lista över kompatibla appar eller en lista över inkompatibla appar. Du kan inte ange båda i samma princip.

|Inställningsnamn|Information|
|----------------|--------------------|
|**Rapportera inkompatibilitet när användare installerar apparna i listan**|Ange de appar (som inte hanteras av Intune) som användarna inte får installera och köra.|
|**Rapportera inkompatibilitet när användare installerar appar som inte är listade**|Ange de appar som användare tillåts att installera. För att fortsätta vara kompatibla får användarna inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt.|
|**Lägg till**|Lägg till en app i den markerade listan. Ange ett namn, eventuellt appens utgivare och webbadressen till appen i appbutiken. Läs "Så här anger du webbadresser till appbutiker" senare i det här avsnittet för mer hjälp.|
|**Importera appar**|Importera en lista med appar som du har angett i en fil med kommaseparerade värden. I filen använder du det här formatet: appnamn, utgivare, app-URL.|
|**Redigera**|Redigera namn, utgivare och webbadress för den valda appen.|
|**Ta bort**|Ta bort den markerade appen från listan.|

Principer som innehåller inställningar för kompatibla och ej kompatibla program måste distribueras till användargrupper.

### <a name="kiosk-mode-settings"></a>Helskärmsinställningar

|Inställningsnamn|Information|
|----------------|--------------------|
|**Välj en hanterad app som ska kunna köras när enheten är i helskärmsläge**|Välj **Bläddra** och ange den hanterade appen eller en app från en butik som ska kunna köras när enheten är i helskärmsläge. Inga andra appar kommer att kunna köras på enheten. Mer hjälp finns i "Så här anger du webbadresser till appbutiker" senare i det här avsnittet.|
|**Tillåt pekskärm**|Aktivera eller inaktivera pekskärmen på enheten.|
|**Tillåt rotering av skärmbild**|Aktivera eller inaktivera ändring av skärmens orientering när användaren roterar enheten.|
|**Tillåt volymknappar**|Aktivera eller inaktivera användningen av volymknapparna på enheten.|
|**Tillåt ringsignalsomkopplare**|Aktivera eller inaktivera tyst läge på enheten.|
|**Tillåt aktiveringsknapp på skärmen**|Aktivera eller inaktivera aktiveringsknappen på enhetens skärm.|
|**Tillåt automatiskt lås**|Aktivera eller inaktivera automatisk låsning av enheten.|
|**Aktivera monoljud**|Aktivera eller inaktivera hjälpmedelsinställningen **Monoljud**.|
|**Aktivera text-till-tal**|Aktivera eller inaktivera hjälpmedelsinställningen **Text-till-tal** som läser upp text på enhetsskärmen.|
|**Aktivera justering av text-till-tal**|Aktivera eller inaktivera justeringar av text-till-talfunktionen så att användare kan justera funktionen text-till-tal (till exempel hur snabbt texten ska läsas upp).|
|**Aktivera zoom**|Aktivera eller inaktivera hjälpmedelsinställningen **Zoom** som gör att användare kan använda pekskärmen för att zooma in det som visas på enheten.|
|**Aktivera zoomjusteringar**|Aktivera eller inaktivera justeringar i zoomfunktionen.|
|**Aktivera inverterade färger**|Aktivera eller inaktivera hjälpmedelsinställningen **Invertera färger** som anpassar skärmen för att hjälpa användare med synfel.|
|**Aktivera anpassning av inverterade färger**|Aktivera eller inaktivera justeringar i funktionen inverterade färger.|
|**Aktivera Assistive Touch**|Aktivera eller inaktivera hjälpmedelsinställningen **Assistive Touch** som hjälper användare med gester på skärmen som kan vara svåra att utföra.|
|**Aktivera anpassning av Assistive Touch**|Aktivera eller inaktivera anpassning av funktionen Assistive Touch.|
|**Aktivera Läs upp markering**|Aktivera eller inaktivera hjälpmedelsinställningen **Läs upp markering** som kan läsa upp texten som användaren väljer.|
> [!NOTE]
> Följande information gäller inställningar för helskärmsläge på iOS-enheter:
>
> -   Innan du kan konfigurera en iOS-enhet för helskärmsläge måste du använda [Apple Configurator-verktyget](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) eller [Apples enhetsregistreringsprogram](ios-device-enrollment-program-in-microsoft-intune.md) för att placera enheten i övervakat läge. Mer information om Apple Configurator-verktyget finns i Apples dokumentation.
> -   Om iOS-appen som du anger har installerats efter det att du har distribuerat konfigurationsprincipen kommer enheten inte att gå över i helskärmsläge förrän den startas om.

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Referensinformation för kompatibla och icke-kompatibla appar

Använd **Inkompatibilitetsrapporter för appar** för att visa kompatibiliteten för tillåtna och blockerade appar.

##### <a name="to-run-the-noncompliant-apps-report"></a>Så här kör du Inkompatibilitetsrapporter för appar

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Rapporter** &gt; **Inkompatibilitetsrapport för appar**.

2.  Välj de enhetsgrupper du vill kontrollera, välj om du vill söka efter kompatibla appar, icke kompatibla appar eller båda och välj sedan **Visa rapport**.

#### <a name="how-to-specify-urls-to-app-stores"></a>Så här anger du webbadresser till appbutiker
Om du vill ange en webbadress till en app i listan kompatibla och inkompatibla appar eller i alternativet **Välj en hanterad app som kommer att kunna köras när enheten är i helskärmsläge** (endast iOS), använder du följande format:

1. Använd en sökmotor för att hitta den app du vill använda i iTunes App Store och öppna appens sida.

2. Kopiera webbadressen till sidan och använd den som webbadress för att konfigurera listan med kompatibla eller inkompatibla appar eller den app du vill köra i helskärmsläge.

**Exempel:** Sök efter **Microsoft Word för iPad**. Webbadressen du använder är **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> Du kan också använda iTunes-programmet för att hitta appen och sedan använda kommandot **Kopiera länk** för att hämta appens webbadress.

### <a name="enrollment-settings"></a>Registreringsinställningar
Alla inställningar gäller för iOS 8.0 och senare.

|Inställningsnamn|Information|
|----------------|--------------------|
|**Tillåt aktiveringslås när enheten är i övervakat läge**|Aktivera aktiveringslåset på övervakade iOS-enheter.|

### <a name="supervised-mode-settings"></a>Inställningar för övervakat läge
Du kan konfigurera följande inställningar på enheter som kör iOS 8.0 och senare i övervakat läge.

### <a name="supervised-mode-settings-for-device-restrictions"></a>Inställningar för enhetsbegränsningar för övervakat läge

|Inställningsnamn|Information|
|----------------|--------------------|
|**Tillåt kontoändring**|Tillåt att användaren ändrar kontoinställningar, till exempel inställningar för e-post.|
|**Tillåt ändringar i inställningar för mobildataanvändning i appar**|Tillåt att användaren bestämmer vilka appar som ska få använda mobildata.|
|**Tillåt att alternativet att radera allt innehåll och alla inställningar på enheten används**|Tillåt att användaren använder alternativet att radera allt innehåll och alla inställningar på enheten.|
|**Tillåt att användaren aktiverar begränsningar i enhetsinställningarna**|Tillåt att användaren konfigurerar enhetsbegränsningar (kontrollfunktioner för föräldrar) på enheten.|
|**Tillåt värdkoppling för att övervaka med vilka enheter en iOS-enhet kan kopplas**|Tillåt värdkoppling så att administratören kan styra vilka enheter en iOS-enhet kan sammankopplas med.|
|**Tillåt att användaren installerar konfigurationsprofiler och certifikat**|Tillåt att användaren installerar konfigurationsprofiler och certifikat.|
|**Tillåt namnbyte för enhet**|Tillåt att användaren ändrar namnet på enheten.|
|**Tillåt ändring av lösenord**|Tillåt att enhetens lösenord läggs till, ändras eller tas bort.|
|**Tillåt Apple Watch-parkoppling**|Tillåt att enheten parkopplas med en Apple Watch.|
|**Tillåt ändring av meddelandeinställningar**|Tillåt att användaren ändrar meddelandeinställningarna för enheten.|
|**Tillåt ändring av bakgrundsbild**|Tillåt att användaren ändrar enhetens bakgrundsbild.|

### <a name="supervised-mode-settings-for-feature-restrictions"></a>Inställningar för funktionsbegränsningar för övervakat läge

|Inställningsnamn|Information|
|----------------|--------------------|
|**Tillåt AirDrop**|Tillåt att funktionen AirDrop används för att utbyta innehåll med enheter i närheten.|
|**Tillåt att Siri skickar frågor om innehåll som skapats av användare från Internet**|Tillåt att Siri besöker webbplatser för att besvara frågor.|
|**Använd Siris filter mot olämpligt språk**|Förhindrar att Siri från dikterar eller talar ett olämpligt språk.|
|**Tillåt Spotlight-sökning för att returnera resultat från Internet**|Tillåt att Spotlight-sökning ansluter till Internet för att visa ytterligare resultat.|
|**Tillåt orddefinitionssökning**|Tillåt iOS-funktionen som gör att du kan markera ett ord och leta upp dess definition.|
|**Tillåt förutseende tangentbord**|Tillåt användning av förutseende tangentbord som föreslår ord som användaren kanske vill använda.|
|**Tillåt autokorrigering**|Låter enheten automatiskt korrigera felstavade ord.|
|**Tillåt tangentbord med stavningskontroll**|Tillåter stavningskontroll på enheten.|
|**Tillåt kortkommandon**|Tillåter användning av kortkommandon.|

### <a name="supervised-mode-settings-for-app-restrictions"></a>Inställningar för appbegränsningar för övervakat läge

|Inställningsnamn|Information|
|----------------|--------------------|
|**Tillåt ändringar av inställningar för att betro företagsappar**|Låter användarna att ändra förtroendeinställningarna för företagsappar.|
|**Tillåt installation av appar endast med hjälp av Apple-konfiguration och iTunes**|Aktiverar eller inaktiverar App Store på enhetens startsida. Användarna kan fortfarande använda iTunes eller Apple Configurator-verktyget för att installera och uppdatera appar.|
|**Tillåt automatisk nedladdning av appar**|Tillåt att appar som köpts på andra enheter automatiskt laddas ned till den här enheten. Den här inställningen påverkar inte uppdateringar av appar.|
|**Tillåt ändringar i Find My Friends-appinställningar**|Tillåt att användaren ändrar inställningarna för Find My Friends-appen.|
|**Tillåt åtkomst till iBooks-butiken**|Tillåt användare att bläddra bland och köpa böcker i iBooks-butiken.|
|**Tillåt användning av appen Meddelanden på enheten**|Tillåt att appen Meddelanden används för att skicka sms.|
|**Tillåt användning av Podcaster**|Tillåt användning av appen Podcaster.|
|**Tillåt användning av musiktjänsten**|Tillåt användning av appen Apple Music.|
|**Tillåt iTunes Radio-tjänsten**|Tillåt användning av appen iTunes Radio.|
|**Tillåt Apple News**|Tillåt användning av appen Apple News.|
|**Tillåt Game Center**|Tillåt att Game Center-appen används.|


### <a name="show-or-hide-apps"></a>Visa eller dölja appar

Med **listan över dolda och visade appar** kan du styra följande på övervakade enheter som kör iOS 9.3 eller senare:

- Ange en lista över appar som ska vara dolda från användare. Användare kan inte visa eller starta dessa appar.
- Ange en lista över appar som användare kan visa och starta. Inga andra appar kan visas eller startas.


#### <a name="how-to-create-a-hidden-or-shown-app-list"></a>Så här skapar du en lista över dolda eller visade appar

Ange följande inställningar.

|Inställningsnamn|Information|
|-|-|
|**Lista över dolda och visade appar**|Aktivera den här inställningen om du vill skapa en lista över dolda eller visade appar.|
|**Dölj apparna i listan från användarna**|Välj det här alternativet om du vill skapa en lista över appar som är dolda för användarna.<br>När du skapar den här listtypen kan alla appar utom iOS-apparna **Inställningar** och **Telefon** (för iPhones) döljas.|
|**Visa enbart appar som finns med i listan för användarna**|Välj det här alternativet om du vill skapa en lista över appar som visas för användarna.<br>När du skapar den här listtypen döljs alla andra appar utom iOS-apparna **Inställningar** och **Telefon** (för iPhones).<br>Dessutom måste du lägga till företagsportalen och alla program som du har distribuerat och hanterar med Intune i listan.|
|**Lägg till**|Lägger till en app i den markerade listan.<br>För den dolda listan måste du ange **namn**, **utgivare**, och **app-URL eller paket-ID** för varje app som du vill dölja.<br>För den visade listan kan du antingen **välja en hanterad app** som visar en lista över Intune-hanterade appar som du kan välja från, eller så kan du välja en butiksapp och sedan ange **namn**, **utgivare** och **app-URL eller paket-ID** för varje app som du vill visa.|
|**Importera appar**|Importerar en lista med appar som du har angett i en fil med kommaseparerade värden. Använd format, appnamn, utgivare och app-URL i filen.|
|**Redigera**|Du kan redigera namn, utgivare och webbadress för den valda appen.|
|**Ta bort**|Tar bort den markerade appen från listan.|

#### <a name="app-information-for-built-in-ios-apps"></a>Appinformation för inbyggda iOS-appar

Med informationen i den här listan kan du identifiera namn, utgivare och paket-ID för de inbyggda iOS-appar som du kan välja att visa eller dölja. Om du vill visa eller dölja alla appar i listan kan du kopiera data till en textfil med filnamnstillägget **.csv** och sedan importera alla appar samtidigt med alternativet **Importera appar**.

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




## <a name="custom-policy-settings"></a>Anpassade principinställningar

Använd Microsoft Intunes **anpassade princip för iOS** för att distribuera inställningar som du har skapat med hjälp av [Apple Configurator-verktyget](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) till iOS-enheter. Med detta verktyg kan du skapa många inställningar som styr driften av dessa enheter och exportera dem till en konfigurationsprofil. Du kan sedan importera denna konfigurationsprofil till en anpassad princip för Intune iOS och distribuera inställningarna för användare och enheter i organisationen.

Med den här funktionen kan du distribuera iOS-inställningar som inte kan konfigureras med allmänna konfigurationsprinciper för Intune.

### <a name="prerequisites"></a>Förutsättningar
Innan du börjar måste du ha installerat Apple Configurator och skapat en konfigurationsfil som innehåller de inställningar som du vill distribuera till användare eller enheter. Du kan ladda ned och lära dig om Apple Configurator från [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

> [!NOTE]
> Intune rapporterar inte efterlevnaden för enskilda inställningar i en anpassad princip för iOS. Dock rapporteras uppfyllande av principen som helhet.

### <a name="general-settings"></a>Allmänna inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för en anpassad princip för iOS som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en beskrivning som ger en översikt över en anpassad princip för iOS och annan relevant information som hjälper dig att hitta den.|

### <a name="custom-settings"></a>Anpassade inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
|**Anpassat konfigurationsprofilnamn (visas för användare)**|Ange ett namn för principen som den kommer att visas på enheten och i principrapporter för Intune.|
|**Konfigurationsprofilfil**|Välj **Importera** och bläddra sedan till den konfigurationsprofil som du skapat med hjälp av Apple Configurator. **Obs!** Se till att de inställningar som du exporterar från verktyget Apple Configurator är kompatibla med iOS-versionen på de enheter som du distribuerar den anpassade iOS-principen till. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen [Apple Developer](https://developer.apple.com/).|
    |**Information om konfigurationsprofilen**|Visa XML-koden för den konfigurationsprofil du har importerat.|

### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
