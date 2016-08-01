---
title: "iOS-principinställningar | Microsoft Intune"
description: "Skapa principer som styr inställningar och funktioner på iOS-enheter som du hanterar med Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 947328a5c28839d8227a9e5ae0dd8b1fc5ad8e81
ms.openlocfilehash: 63bc2cedf8d81b050a384a947a0b43827de5c352


---

# Principinställningar för iOS i Microsoft Intune

I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i iOS-enheter. Du kan också använda verktyget Apple Configurator för att skapa anpassade inställningar som inte är tillgängliga från Intune.

## Generella inställningar för konfigurationsprinciper

Använd Microsoft Intunes **allmänna konfigurationsprincip** för iOS om du vill konfigurera inställningar för:

-   **Allmänna enhets- och säkerhetsinställningar** – Välj i en lista fördefinierade inställningar med vilka du kan reglera många av enhetens egenskaper och funktioner.

-   **Helskärmsläge** – Lås en enhet så att bara vissa funktioner fungerar. Du kan t.ex. tillåta att enheten endast ska kunna köra en hanterad app som du anger, eller så kan du inaktivera volymknapparna på en enhet. De här inställningarna kan användas på en demonstrationsmodell av en enhet, eller en enhet som bara används för att utföra en enda funktion, till exempel i en butikskassa.

-   **Kompatibla och inkompatibla appar** – Ange en lista över appar i företaget som är kompatibla eller inkompatibla. För Android- och iOS-enheter kan **Inkompatibilitetsrapporter för appar** användas för att visa om de appar du har angett i listan är kompatibla med appar som användare har installerat (men det inte går att blockera installationen av programmet).

> [!TIP]
> Du kan konfigurera villkor för användarna för att säkerställa att de är medvetna om att apparna på deras enheter, även personliga appar, kommer att utvärderas och inkompatibla appar antingen kommer att blockeras eller rapporteras som inkompatibla. Användarna måste acceptera dessa villkor innan de kan registrera sina enheter och använda företagsportalen för att hämta appar. Mer information om de allmänna villkoren finns i [Principinställningar för användarvillkor i Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Om den inställning som du söker efter inte visas i avsnittet kan du skapa den med hjälp av en anpassad iOS-princip med vilken du kan importera inställningar som du har skapat med hjälp av [Apple-konfigurationsverktyget](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Mer information finns i **Anpassade principinställningar** senare i det här avsnittet.

### Säkerhetsinställningar
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Ange om användare måste ange ett lösenord för att komma åt sin enhet.|
|**Lösenordstyp krävs**|Anger vilken typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt.|
|**Antal avancerade tecken som krävs i lösenord**|Detta anger antalet symboltecken (till exempel **#** eller **@**) som måste tas med i lösenordet.|
|**Minsta längd på lösenord**|Anger det minsta antalet tecken som lösenordet måste innehålla.|
|**Tillåt enkla lösenord**|Tillåt enkla lösenord som "0000" och "1234"|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Rensar enheten om detta antal inloggningsförsök misslyckas.|
|**Antal minuters inaktivitet innan lösenord krävs**<sup>1</sup>|Anger hur länge enheten kan vara inaktiv innan användaren måste ange sina lösenord på nytt.|
|**Förfallotid för lösenord (dagar)**|Anger antalet dagar innan lösenordet måste ändras.|
|**Kom ihåg tidigare lösenord**|Anger om användaren kan använda lösenord som de har använt tidigare.|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Anger antalet tidigare använda lösenord som enheten sparar.|
|**Minuter av inaktivitet innan skärmen stängs av**<sup>1</sup>|Ange antalet minuter innan enhetens skärm är inaktiverad.|
|**Tillåt fingeravtrycksupplåsning**|Tillåt att enheten kan låsas upp med ett fingeravtryck.|
<sup>1</sup> När du konfigurerar inställningarna **Minuter av inaktivitet innan skärmen stängs av** och **Minuter av inaktivitet innan lösenord måste anges** för iOS-enheter tillämpas de i följd. Om du t.ex. ställer in värdet för båda inställningarna till **5** minuter så stängs skärmen av automatiskt efter 5 minuter, och enheten låses efter ytterligare 5 minuter. Om användaren däremot stänger av skärmen manuellt så tillämpas den andra inställningen omedelbart. Efter det att användaren i det här exemplet har stängt av skärmen låses enheten 5 minuter senare.

### Systeminställningar
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt skärmdump**|Tillåter användare att fånga innehållet på skärmen i en bild.|
|**Tillåt Kontrollcenter på låsskärm**|Styr om kontrollcenterappen kan användas när enheten är låst.|
|**Tillåt notisvy på låsskärm**|Tillåter användaren att få åtkomst till aviseringsvyn utan att låsa upp enheten.|
|**Tillåt dagsvy på låsskärm**|Styr om aviseringar kan visas när enheten är låst.|
|**Tillåt ej betrodda TLS-certifikat**|Tillåt ej betrodda Transport Layer Security-certifikat på enheten.|
|**Tillåt sändning av diagnostikdata**|Tillåt eller blockera enheter från att skicka diagnostikdata till Apple.|
|**Tillåt sparbok när låst**|Tillåt användare att komma åt appen Sparbok när enheten är låst.|

### Molninställningar – dokument och data
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt säkerhetskopiering till iCloud**|Tillåter användare att säkerhetskopiera enheten till iCloud.|
|**Tillåt dokumentsynkronisering till iCloud**|Tillåt synkronisering av dokument och nyckel/värde till ditt lagringsutrymme i iCloud.|
|**Tillåt bildströmssynkronisering till iCloud**|Tillåt foton på enheten att synkronisera med iCloud.|
|**Kräv krypterad säkerhetskopiering**|Kräv att säkerhetskopior av enheter måste vara krypterade.|
|**Tillåt att hanterade appar synkroniserar data till iCloud**|Tillåt att appar som du hanterar med Intune synkroniserar data till användarnas iCloud-konto.|
|**Tillåt Handoff för att fortsätta med aktiviteter på en annan enhet**|Med Handoff kan du återuppta det arbete som du påbörjat i en iOS-enhet på en annan iOS- eller Mac OS X-enhet.|

### Programinställningar - webbläsare
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt Safari**|Ange om webbläsaren Safari kan användas på enheten.|
|**Tillåt autofyll**|Användaren kan ändra inställningar för Komplettera automatiskt i webbläsaren.|
|**Tillåt blockering av popup-fönster**|Aktiverar eller inaktiverar webbläsarens blockering av popup-fönster.|
|**Tillåt cookies**|Tillåt enhetens webbläsare att använda cookies.|
|**Tillåt Java-skript**|Tillåt att Java-skript körs i webbläsaren.|
|**Tillåt bedrägerivarning**|Tillåt bedrägerivarningar i enhetens webbläsare.|

### Programinställningar - appar
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt appbutik**|Tillåter enheten att få åtkomst till appbutiken.|
|**Kräv ett lösenord om du vill komma åt programbutiken.**|Kräver att användarna anger ett lösenord innan de kan besöka app store.|
|**Tillåt köp via app**|Tillåt att inköp görs från en app som körs.|
|**Tillåt hanterade dokument i andra ohanterade appar**|Tillåter visning av företagsdokument i vilken app som helst.<br>**Exempel:** Du vill förhindra att användare sparar filer från OneDrive-appen till Dropbox. Konfigurera den här inställningen till Nej. När enheten har hämtat principen (till exempel efter en omstart) kommer den inte längre att tillåta att spara.|
|**Tillåt ohanterade dokument i andra hanterade appar**|Tillåt visning av valfria dokument i hanterade företagsappar.|
|**Tillåt videokonferens**|Tillåt videokonferensappar, till exempel Facetime på enheten.|
|**Tillåt innehåll för vuxna i mediebutik**|Tillåt att enheten får åtkomst till innehåll som är klassificerade som för vuxna i butiken.|
|**Tillåt att användaren laddar ned innehåll från iBook-butiken som flaggats som ”Erotik”**|Tillåt att användaren hämtar böcker i kategorin Erotik.|

### Programinställningar - spel
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt att Game Center-vänner läggs till**|Tillåt användaren att lägga till vänner i Game Center.|
|**Tillåt spel för flera personer**|Tillåt användaren att spela spel för flera personer på enheten.|

### Enhetskapacitetsinställningar - maskinvara
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt kamera**|Anger om kameran på enheten får användas.|
|**Kräv ett kopplat lösenord för utgående AirPlay-begäranden**|Med Airplay kan du strömma innehåll till andra Apple-enheter. Använd den här inställningen om du vill kräva ett kopplat lösenord för att ansluta till andra enheter.|

### Enhetskapacitetsinställningar - mobil
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt röstroaming**|Tillåt röstnätverksväxling när enheten är på ett mobilnät.|
|**Tillåt dataroaming**|Tillåt datanätverksväxling när enheten använder ett mobilnät.|
|**Tillåt hämtning av global bakgrund under nätverksväxling**|Tillåt att enheten att hämtar data, till exempel e-post när den nätverksväxlar på ett mobilnät.|

### Enhetskapacitetsinställningar - funktioner
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|-------|
|**Tillåt Siri**|Tillåt användning av röstassistenten Siri på enheten.|
|**Tillåt Siri när enheten är låst**|Tillåt användning av röstassistenten Siri på enheten när den är låst|
|**Tillåt röstsamtal**|Tillåt användning av röstsamtalsfunktionen på enheten.|


### Inställningar för kompatibla och icke-kompatibla appar
I listan över **kompatibla och &amp;inkompatibla appar** skapar du en lista över kompatibla eller inkompatibla appar med hjälp av följande information:

> [!NOTE]
> En enda princip kan bara innehålla en lista över kompatibla eller en lista över inkompatibel appar. Du kan inte ange båda i samma princip.

|Inställningsnamn|Information|
|----------------|--------------------|
|**Rapportera inkompatibilitet när användare installerar apparna i listan**|Visar en lista med de appar som inte hanteras av Intune och som användarna inte får installera och köra.|
|**Rapportera inkompatibilitet när användare installerar appar som inte är listade**|Visar listan med de appar som användare tillåts att installera. För att fortsätta vara kompatibla får användarna inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt.|
|**Lägg till**|Lägger till en app i den markerade listan. Ange ett namn, eventuellt appens utgivare och webbadressen till appen i appbutiken. Läs **Så här anger du webbadresser till appbutiker** senare i det här avsnittet för mer hjälp.|
|**Importera appar**|Importerar en lista med appar som du har angett i en fil med kommaseparerade värden. Använd format, appnamn, utgivare och app-URL i filen.|
|**Redigera**|Du kan redigera namn, utgivare och webbadress för den valda appen.|
|**Ta bort**|Tar bort den markerade appen från listan.|

### Helskärmsinställningar

|Inställningsnamn|Information|
|----------------|--------------------|
|**Välj en hanterad app som ska kunna köras när enheten är i helskärmsläge**|Välj **Bläddra**, ange den hanterade appen eller en app från en butik som ska kunna köras när enheten är i helskärmsläge. Inga andra appar kommer att kunna köras på enheten. Mer hjälp finns i **Så anger du webbadresser till appbutiker** senare i det här avsnittet.|
|**Tillåt pekskärm**|Aktiverar eller inaktiverar pekskärm på enheten.|
|**Tillåt rotering av skärmbild**|Aktiverar eller inaktiverar ändring av skärmens orientering när du roterar hela enheten.|
|**Tillåt volymknappar**|Aktiverar eller inaktiverar användningen av volymknapparna på enheten.|
|**Tillåt ringsignalsomkopplare**|Aktiverar eller inaktiverar tyst läge på enheten.|
|**Tillåt aktiveringsknapp på skärmen**|Aktiverar eller inaktiverar aktiveringsknappen på enhetens skärm.|
|**Tillåt automatiskt lås**|Aktiverar eller inaktiverar automatisk låsning av enheten.|
|**Aktivera monoljud**|Aktiverar eller inaktiverar hjälpmedelsinställningen **Monoljud**.|
|**Aktivera text-till-tal**|Aktiverar eller inaktiverar hjälpmedelsinställningen **Text-till-tal** som läser upp text på enhetsskärmen.|
|**Aktivera justering av text-till-tal**|Aktiverar eller inaktiverar justeringar av text-till-talfunktionen så att du kan justera funktionen text-till-tal (till exempel hur snabbt texten ska läsas upp).|
|**Aktivera zoom**|Aktiverar eller inaktiverar hjälpmedelsinställningen **Zoom** som gör att du kan använda pekskärmen för att zooma in det som visas på enheten.|
|**Aktivera zoomjusteringar**|Aktiverar eller inaktiverar justeringar i zoomfunktionen.|
|**Aktivera inverterade färger**|Aktiverar eller inaktiverar hjälpmedelsinställningen **Invertera färger** som anpassar skärmen för att hjälpa användare med synfel.|
|**Aktivera anpassning av inverterade färger**|Aktiverar eller inaktiverar justeringar i funktionen inverterade färger.|
|**Aktivera Assistive Touch**|Aktiverar eller inaktiverar hjälpmedelsinställningen **Assistive Touch** som hjälper användaren med gester på skärmen som kan vara svåra att utföra.|
|**Aktivera anpassning av Assistive Touch**|Aktiverar eller inaktiverar anpassning av funktionen Assistive Touch.|
|**Aktivera Läs upp markering**|Aktiverar eller inaktiverar hjälpmedelsinställningen **Läs upp markering** som kan läsa upp texten du väljer.|
> [!NOTE]
> Följande information gäller inställningar för helskärmsläge på iOS-enheter:
> 
> -   Innan du kan konfigurera en iOS-enhet för helskärmsläge måste du använda [Apple Configurator Tool](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) eller Enhetsregistreringshanteraren för att placera enheten i övervakat läge Mer information om Apple Configurator Tool, se dokumentationen till Apple.
> -   Om iOS-appen du anger har installerats efter det att du har distribuerat konfigurationsprincipen kommer enheten inte att gå över i helskärmsläge förrän den startas om.

### Referensinformation för kompatibla och icke-kompatibla appar

#### Övervaka kompatibla och icke-kompatibla appar
Använd **Inkompatibilitetsrapporter för appar** för att visa kompatibiliteten för tillåtna och blockerade appar.

##### Så här kör du Inkompatibilitetsrapporter för appar

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Rapporter** &gt; **Inkompatibilitetsrapport för appar**.

2.  Välj de enhetsgrupper du vill kontrollera, om du vill söka efter kompatibla eller icke kompatibla appar och välj sedan **Visa rapport**.

#### Så här anger du webbadresser till appbutiker
Om du vill ange en webbadress till en app i listan kompatibla och inkompatibla appar eller i alternativet **Välj en hanterad app som kommer att kunna köras när enheten är i helskärmsläge** (endast iOS), använder du följande format:

Använd en sökmotor för att hitta den app du vill använda i iTunes App Store och öppna appens sida.

Kopiera webbadressen till sidan och använd den som webbadress för att konfigurera listan med kompatibla eller inkompatibla appar eller den app du vill köra i helskärmsläge.

**Exempel:** Sök efter **Microsoft Word för iPad**. Webbadressen du använder är **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> Du kan också använda iTunes-programmet för att hitta appen och sedan använda kommandot **Kopiera länk** för att hämta appens webbadress.

### Registreringsinställningar
Alla inställningar gäller för iOS 7.1 och senare.

|Inställningsnamn|Information|
|----------------|--------------------|
|**Tillåt aktiveringslås när enheten är i övervakat läge**|Aktiverar aktiveringslåset på övervakade iOS-enheter.|

### Övervakning
Följande inställningar kan konfigureras på enheter som kör iOS 7.1 och senare i övervakat läge.

|Inställningsnamn|Information|
|----------------|--------------------|
|**Tillåt kontoändring**|Tillåt att användaren ändrar kontoinställningar, till exempel inställningar för e-post.|
|**Tillåt AirDrop**|Tillåt att funktionen Airdrop används för att utbyta innehåll med enheter i närheten.|
|**Tillåt ändringar i inställningar för mobildataanvändning i appar**|Tillåt att användaren bestämmer vilka appar som ska få använda mobildata.|
|**Tillåt att Siri skickar frågor om innehåll som skapats av användare från Internet**|Tillåt att Siri besöker webbplatser för att besvara frågor.|
|**Tillåt åtkomst till iBooks-butiken**|Tillåt användare att bläddra bland och köpa böcker i iBooks-butiken.|
|**Tillåt ändringar i Find My Friends-appinställningar**|Tillåt att användaren ändrar inställningarna för Find My Friends-appen.|
|**Tillåt att alternativet att radera allt innehåll och alla inställningar på enheten används**|Tillåt att användaren använder alternativet att radera allt innehåll och alla inställningar på enheten.|
|**Tillåt att användaren aktiverar begränsningar i enhetsinställningarna**|Tillåt att användaren konfigurerar enhetsbegränsningar (kontrollfunktioner för föräldrar) på enheten|
|**Tillåt Spotlight-sökning för att returnera resultat från Internet**|Tillåt att Spotlight-sökning ansluter till Internet för att visa ytterligare resultat.|
|**Tillåt att Game Center-appen används**|Tillåt att Game Center-appen används.|
|**Tillåt värdkoppling för att övervaka med vilka enheter en iOS-enhet kan kopplas**|Med värdkoppling kan administratören styra vilka enheter en iOS 7-enhet kan sammankopplas med.|
|**Tillåt att användaren installerar konfigurationsprofiler och certifikat**|Tillåt att användaren installerar konfigurationsprofiler och certifikat.|
|**Tillåt användning av appen Meddelanden på enheten**|Tillåt att appen Meddelanden används för att skicka sms.|


## Anpassade principinställningar

Använd Microsoft Intunes **anpassade konfigurationsprincip för iOS** för att distribuera inställningar till iOS-enheter som du har skapat med hjälp av [verktyget Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Med detta verktyg kan du skapa många inställningar som styr driften av dessa enheter och exportera dem till en konfigurationsprofil. Du kan sedan importera denna konfigurationsprofil till en anpassad princip för Intune iOS och distribuera inställningarna för användare och enheter i organisationen.

Den här funktionen är avsedd för att distribuera iOS-inställningar som inte kan konfigureras med allmänna konfigurationsprinciper för Intune.

### Krav
Innan du börjar, måste du har installerat Apple Configurator och skapat en konfigurationsfil som innehåller de inställningar som du vill distribuera till användare eller enheter. Du kan hämta hem och lära dig om Apple Configurator från [Mac App-butiken](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)

> [!NOTE]
> Intune rapporterar inte efterlevnaden för enskilda inställningar i en anpassad princip för iOS. Dock rapporteras uppfyllande av principen som helhet.

### Allmänna inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för en anpassad princip för iOS som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en beskrivning som ger en översikt över en anpassad princip för iOS och annan relevant information som hjälper dig att hitta den.|

### Anpassade inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
|**Anpassat konfigurationsprofilsnamn (visas för användare)**|Ange ett namn för principen som den kommer att visas på enheten och i principrapporter för Intune.|
|**Konfigurationsprofilsfil**|Välj **Importera**, bläddra sedan till den konfigurationsprofil som du skapat med hjälp av Apple Configurator. **Obs!** Se till att de inställningar som du exporterar från verktyget Apple Configurator är kompatibla med iOS-versionen på de enheter som du distribuerar den anpassade iOS-principen till. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen för [Apple-utvecklare](https://developer.apple.com/).|
    |**Information om konfigurationsprofilen**|Visar XML-koden för den konfigurationsprofil du har importerat.|

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jul16_HO4-->


