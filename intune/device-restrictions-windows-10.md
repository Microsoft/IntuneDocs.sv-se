---
title: "Inställningar av begränsningar i Intune-enheter för Windows Phone 10"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs om de Intune-inställningar du kan använda för att styra inställningar och funktioner på Windows 10-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89f2d806-2e97-430c-a9a1-70688269627f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 88910c6628bb356e4a757cbdb4cf63b0acf60040
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="windows-10-and-later-device-restriction-settings-in-microsoft-intune"></a>Inställningar för enhetsbegränsningar för Windows 10 och senare i Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="general"></a>Allmänt
-     **Skärmbild (endast mobil)** – Gör det möjligt för användaren att hämta enhetens skärm som en bild.
-     **Kopiera och klistra in (endast mobil)** – Tillåter funktionen att kopiera och klistra in mellan appar på enheten.
-     **Manuell avregistrering** – Tillåter att användaren manuellt tar bort sitt arbetsplatskonto från enheten.
-     **Manuell installation av rotcertifikat (endast mobil)** – Hindrar användaren att manuellt installera rotcertifikat och mellanliggande CAP-certifikat.
-     **Sändning av diagnostikdata** – Möjliga värden är:
    -         **Inga** Inga data skickas till Microsoft
    -         **Grundläggande** Begränsad information skickas till Microsoft
    -         **Utökade** Utökade diagnostikdata skickas till Microsoft
    -         **Fullständiga** Skickar samma data som i Utökade, plus ytterligare information om enhetens tillstånd
-     **Kamera** – Tillåt eller blockera användning av kameran på enheten.
-     **OneDrive-filsynkronisering** – Blockerar enheten från att synkronisera filer till OneDrive.
-     **Flyttbara lagringsmedier** – Anger om externa lagringsenheter, till exempel ett SD-kort, kan användas med enheten.
-     **Geoplats** – Anger om enheten kan använda information om platstjänster.
-     **Internetdelning** – Tillåter användning av Internetanslutningsdelning på enheten.
-     **Telefonåterställning** – Styr om användaren kan göra en fabriksåterställning på enheten eller inte.
-     **USB-anslutning (endast mobil)** – Styr om enheter har åtkomst till externa lagringsenheter via en USB-anslutning.
-     **Stöldskyddsläge (endast mobil)** – Konfigurera om stöldskyddsläget i Windows ska vara aktiverat.
-     **Aviseringar från Åtgärdscenter (endast mobil)** – Aktivera eller inaktivera aviseringar från Åtgärdscenter på enhetens låsskärm (endast Windows 10 Mobile).
-     **Cortana** – Aktivera eller inaktivera röstassistenten Cortana.
-     **Röstinspelning (endast mobil)** – Tillåt eller blockera användning av enhetens röstinspelare.
-     **Ändra energialternativinställningar (endast skrivbord)** – Förhindrar att användaren ändrar energialternativinställningar på enheten.
-     **Ändra regionsinställningar (endast skrivbord)** – Förhindrar att användaren ändrar regionsinställningar på enheten.
-     **Ändra språkinställningar (endast skrivbord)** – Förhindrar att användaren ändrar språkinställningarna på enheten.
-     **Ändra systemtid** – Förhindrar att användaren ändrar enhetens datum och tid.
-     **Ändra enhetsnamn** – Förhindrar att användaren ändrar enhetens namn.
-     **Lägg till konfigurationspaket** – Blockerar runtime-konfigurationsagenten som installerar konfigurationspaket.
-     **Ta bort konfigurationspaket** – Blockerar runtime-konfigurationsagenten som tar bort konfigurationspaket.
-     **Enhetsidentifiering** – Blockerar en enhet från att identifieras av andra enheter.
-     **Växla mellan aktiviteter (endast mobil)** – Blockerar funktionen Växla mellan aktiviteter på enheten.
-     **Dialogruta om SIM-kortsfel (endast mobil)** – Blockerar ett felmeddelande från att visas på enheten om inget SIM-kort har upptäckts.


## <a name="password"></a>Lösenord
-     **Lösenord** – Kräver att användaren måste ange ett lösenord för att få åtkomst till enheten.
    -     **Krav på lösenordstyp** – Anger om lösenordet måste vara enbart numeriskt, eller om det kan vara alfanumeriskt.
    -     **Minsta längd på lösenord** – Gäller endast Windows 10 Mobile.
    -     **Antal felaktiga inloggningar innan enheten rensas** – För enheter som kör Windows 10: Om BitLocker är aktiverat på enheten försätts den i återställningsläget för BitLocker när den gräns för antal misslyckade inloggningar som du har angett har uppnåtts. Om BitLocker inte är aktiverat på enheten tillämpas inte den här inställningen.
För enheter som kör Windows 10 Mobile: Om inloggningen misslyckas ett visst antal gånger (som du angett) rensas enheten.
    -     **Maximalt antal minuter av inaktivitet innan skärmen låses** – Anger hur lång tid en enhet måste vara i viloläge innan skärmen låses.
    -     **Lösenordets giltighetstid (dagar)** – Anger efter hur lång tid enhetens lösenord måste ändras.
    -     **Förhindra återanvändning av tidigare lösenord** – Anger hur många tidigare använda lösenord enheten kommer ihåg.
    -     **Kräv lösenord när enheten lämnar inaktivt läge** – Anger att användaren måste ange ett lösenord för att kunna låsa upp enheten (endast Windows 10 Mobile).
-     **Kryptering** – Aktivera kryptering på målenheter (endast Windows 10 Mobile).

## <a name="personalization"></a>Anpassning

-     **URL för skrivbordsbakgrundsbild (endast skrivbord)** – Anger URL:en till en bild i PNG-, JPG- eller JPEG-format som ska användas som skrivbordsbakgrund i Windows. Användarna kommer inte att kunna ändra detta.

## <a name="locked-screen-experience"></a>Låsskärm

-     **URL till bild av låst skärm (endast skrivbord)** – Anger webbadressen till en bild i PNG-, JPG- eller JPEG-format som ska användas som låsskärmsbild i Windows. Användarna kommer inte att kunna ändra detta.


## <a name="app-store"></a>Appbutik

-     **Appbutik (endast mobil)** – Aktivera eller blockera användning av appbutiken på Windows 10 Mobile-enheter.
-     **Uppdatera appar automatiskt från Store** – Appar som installeras från Windows Store uppdateras automatiskt.
-     **Installation av betrodd app** – Appar som signeras med ett betrott certifikat läses in separat.
-     **Lås upp via utvecklare** – Tillåter Windows utvecklarinställningar, till exempel att separat inlästa appar ska kunna ändras av användaren.
-     **Dela appdata mellan användare** – Tillåter att appar delar data mellan olika användare på samma enhet.
-     **Använd endast privat katalog** – Aktivera det här alternativet för att endast tillåta att användarna hämtar appar från din privata katalog.
-     **Start av appar från Store** – Används för att inaktivera alla appar som har förinstallerats på enheten eller hämtats från Windows Store.
-     **Installera appdata på systemvolym** – Hindrar appar från att lagra data på enhetens systemvolym.
-     **Installera appar på systemenhet** – Hindrar appar från att lagra data på enhetens systemenhet.
-     **Game DVR (endast skrivbord)** – Konfigurerar om registrering och sändning av spel tillåts.



## <a name="edge-browser"></a>Edge-webbläsare
-     **Microsoft Edge-webbläsare (endast mobil)** – Tillåt användning av Edge-webbläsaren på enheten.
-     **SmartScreen** – Aktiverar eller inaktiverar SmartScreen som blockerar bedrägliga webbplatser.
-     **Skicka Do Not Track-huvuden** – Konfigurerar Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker.
-     **Cookies** – Gör att webbläsaren sparar Internetcookies på enheten.
-     **JavaScript** – Tillåter att skript (exempelvis JavaScript) körs i Edge-webbläsaren.
-     **Popup-fönster** – Blockerar popup-fönster i webbläsaren (gäller endast Windows 10 Desktop).
-     **Sökförslag** – Tillåter att din sökmotor föreslår webbplatser när du skriver sökfraser.
-     **Skicka intranätstrafik till Internet Explorer** – Låter användarna öppna intranätswebbplatser i Internet Explorer (endast Windows 10 Desktop).
-     **Autofyll** – Tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren (endast Windows 10 Desktop).
-     **Lösenordshanteraren** – Aktivera eller inaktivera lösenordshanteraren för Edge.
-     **Plats för webbplatslista för företagsläge** – Anger var du hittar listan med webbplatser som kan öppnas i företagsläge. Användare kan inte redigera den här listan.<br>(Endast Windows 10 Desktop.)
-     **Utvecklarverktyg** – Förhindrar att användaren kan öppna Edge-utvecklingsverktygen.
-     **Tillägg** – Tillåter att användaren installerar Edge-tillägg på enheten.
-     **InPrivate-surfning** – Förhindrar att användaren öppnar InPrivate-surfningssessioner.
-     **Första körningswebbadress** – Ange den webbadress som Edge-webbläsaren öppnar första gången den körs (endast mobil).
-     **Startsidor** – Lägg till en lista över webbplatser som ska användas som startsidor i Edge-webbläsaren (endast skrivbord).
-     **Blockera åtkomst till about:flags** – Förhindra att användaren kommer åt sidan about:flags i Edge som innehåller inställningar för utvecklare och experiment.
-     **Åsidosätt SmartScreen-meddelande** – Tillåt att användaren kringgår SmartScreen-filtrets varningar om potentiellt skadliga webbplatser.
-     **Åsidosätt SmartScreen-meddelande om filer** – Tillåt att användaren kringgår SmartScreen-filtrets varningar vid hämtning av potentiellt skadliga filer.
-     **localhost-ip-adress via WebRtc** – Blockera användarens ip-adress till localhost vid telefonsamtal via WebRTC-protokollet.
-     **Standardsökmotor** – Ange den standardsökmotor som ska användas. Användarna kan ändra det här värdet när som helst.

## <a name="search"></a>Sök
- **Säker sökning (endast mobil)** – Styr hur Cortana filtrerar innehåll för vuxna i sökresultaten. Du kan välja **Strikt**, **Måttlig** eller tillåta att användaren väljer sina egna inställningar.

## <a name="cloud-and-storage"></a>Moln och lagring
-     **Microsoft-konto** – Låter användaren associera ett Microsoft-konto med enheten.
-     **Andra konton än Microsoft-konton** – Låter användaren lägga till e-postkonton på enheten som inte är associerade med något Microsoft-konto.
-     **Synkroniseringsinställningar för Microsoft-konto** – Tillåt att enhets- och appinställningar som har associerats med ett Microsoft-konto synkroniseras mellan enheter.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning
-     **Datanätverksväxling** – Tillåt växling mellan nätverk vid åtkomst till data.
-     **VPN över mobilt nätverk** – Styr om enheten har åtkomst till VPN-anslutningar när den är ansluten till ett mobilt nätverk.
-     **VPN-nätverksväxling över mobilt nätverk** – Styr om enheten har åtkomst till VPN-anslutningar när den är nätverksväxlas i ett mobilt nätverk.
-     **Bluetooth** – Styr om användaren kan aktivera och konfigurera Bluetooth på enheten.
-     **Bluetooth-identifiering** – Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.
-     **Bluetooth-annonsering** – Låter enheten ta emot annonser via Bluetooth.
-     **Enhetens Bluetooth-namn** – Låter dig ange Bluetooth-namnet på enheten.
-     **NFC** – Låter användaren aktivera och konfigurera närfältskommunikation på enheten.
-     **Trådlöst** – Låter användaren aktivera och konfigurera trådlösa funktioner på enheten (endast Windows 10 Mobile).
-     **Anslut automatiskt till trådlösa surfpunkter** – Tillåter att enheten ansluter automatiskt till kostnadsfria trådlösa surfpunkter och att den godkänner eventuella villkor för anslutningen automatiskt.
-     **Manuell trådlös konfiguration** – Styr om användarna kan konfigurera egna trådlösa anslutningar, eller om de endast kan använda anslutningar som konfigurerats med en trådlös profil (endast Windows 10 Mobile).
-     **Sökintervall för trådlöst nätverk** – Ange hur ofta enheterna ska söka efter trådlösa nätverk.

## <a name="control-panel-and-settings"></a>Kontrollpanel och inställningar

-     **Inställningsapp** – Blockera åtkomst till appen för Windows-inställningar.
    -     **System** – Blockerar åtkomsten till systemområdet för inställningsappen.
    -     **Enheter** – Blockerar åtkomsten till enhetsområdet för inställningsappen.
    -     **Nätverk och Internet** – Blockerar åtkomsten till nätverket och Internetområdet för inställningsappen.
    -     **Anpassning** – Blockerar åtkomsten till anpassningsområdet för inställningsappen.
    -     **Konton** – Blockerar åtkomsten till kontoområdet för inställningsappen.
    -     **Tid och språk** – Blockerar åtkomsten till tid- och språkområdet för inställningsappen.
    -     **Hjälpmedel** – Blockerar åtkomsten till området Hjälpmedel för inställningsappen.
    -     **Sekretess** – Blockerar åtkomsten till sekretessområdet för inställningsappen.
    -     **Uppdatering och säkerhet** – Blockerar åtkomst till uppdaterings- och säkerhetsområdet i inställningsappen.

## <a name="defender"></a>Defender

-     **Övervakning i realtid** – Tillåter genomsökning i realtid efter skadlig programvara, spionprogram och annan oönskad programvara.
-     **Övervaka funktionssätt** – Tillåter att Defender söker efter kända mönster för misstänkt aktivitet på enheterna.
-     **NIS (Network Inspection System)** – NIS hjälper till att skydda enheter mot nätverksbaserade hot genom att använda signaturerna för kända säkerhetsrisker från Microsoft Endpoint Protection Center för att upptäcka och blockera skadlig trafik.
-     **Sök igenom alla nedladdningar** – Styr om Defender genomsöker alla filer som laddas ner från Internet.
-     **Sök igenom skripts som har lästs in via Microsoft-webbläsare** – Tillåter Defender-genomsökning av skript som används i Internet Explorer.
-     **Användaråtkomst till Defender** – Styr om Windows Defender-användargränssnittet är dolt för slutanvändarna.
Om den här inställningen ändras börjar den gälla nästa gång slutanvändarens dator startas om.
-     **Intervall för signaturuppdatering (i timmar)** – Ange med vilket intervall som Defender ska söka efter nya signaturfiler.
-     **Övervaka fil- och programaktivitet** – Tillåter att Defender övervakar fil- och programaktivitet på enheter.
-     **Dagar innan skadlig kod i karantän tas bort** – Tillåter att Defender fortsätter spåra åtgärdad skadlig kod det antal dagar som du anger, för att du ska kunna kontrollera tidigare berörda enheter manuellt. Om du ställer in antalet dagar till **0** finns skadlig kod kvar i karantänmappen och tas inte bort automatiskt.
-     **Gräns för processoranvändning under genomsökning** – Tillåter att du begränsar hur mycket processorkraft som genomsökningarna får använda (från **1** till **100**).
-     **Sök igenom arkivfiler** – Tillåter att Defender söker igenom arkiverade filer, till exempel ZIP- eller CAB-filer.
-     **Sök igenom inkommande e-postmeddelanden** – Tillåter att Defender söker igenom e-postmeddelanden när de tas emot på enheten.
-     **Sök igenom flyttbara enheter vid fullständig genomsökning** –Tillåter att Defender genomsöker flyttbara enheter, som t.ex. USB-minnen.
-     **Sök igenom mappade nätverksenheter vid fullständig genomsökning** – Tillåter att Defender genomsöker filer på mappade nätverksenheter.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.
-     **Sök igenom filer öppnade från nätverksmappar** – Tillåter att Defender genomsöker filer på delade nätverksenheter (till exempel de som nås från en UNC-sökväg).
Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.
-     **Molnskydd** – Tillåter eller förhindrar att Microsoft Active Protection Service tar emot information om aktiviteter mot skadlig kod från enheter som du hanterar. Den här informationen används för att förbättra tjänsten i framtiden.
-     **Tillfråga användarna innan exempel skickas** – Styr om filer som kan kräva ytterligare analys av Microsoft för att avgöra om de är skadliga ska skickas automatiskt till Microsoft.
-     **Tidpunkt för daglig snabbsökning** – Tillåter att du schemalägger en snabbgenomsökning som körs varje dag vid den tidpunkt som du väljer.
-     **Typ av systemgenomsökning som ska utföras** – Här kan du ange nivå för genomsökningen som ska utföras när du schemalägger en systemgenomsökning.

## <a name="defender-exclusions"></a>Defender-undantag

-     **Filer och mappar som ska undantas från genomsökningar och realtidsskydd** – Lägger till en eller flera filer och mappar, som t.ex. **C:\Path** eller **%ProgramFiles%\Path\filename.exe**, i undantagslistan. Dessa filer och mappar tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.
-     **Filnamnstillägg som ska undantas från genomsökningar och realtidsskydd** – Lägg till ett eller flera filnamnstillägg, som t.ex. **jpg** eller **txt**, i undantagslistan. Filer med dessa filnamnstillägg tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.
-     **Processer som ska undantas från genomsökningar och realtidsskydd** – Lägg till en eller flera processer av typen **.exe**, **.com** eller **.scr** i undantagslistan. De här processerna tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.


## <a name="network-proxy"></a>Nätverksproxy

-     **Identifiera proxyinställningar automatiskt** – När detta är aktiverat kommer enheten försöka hitta sökvägen till ett PAC-skript.
-     **Använd proxyskript** – Välj detta alternativ om du vill ange en sökväg till ett PAC-skript för att konfigurera proxyservern.
    -     **Ställ in webbadress till skript** – Ange webbadressen för ett PAC-skript som du vill använda för att konfigurera proxyservern.
-     **Använd manuell proxyserver** – Välj detta alternativ om du vill ange proxyserverinformationen manuellt.
    -     **Adress** – Ange namn eller IP-adress för proxyservern.
    -     **Portnummer** – Ange portnumret till proxyservern.
    -     **Proxy-undantag** – Ange de webbadresser som inte får använda proxyservern. Använd semikolon för att avgränsa varje objekt.
    -     **Använd ingen proxyserver för lokal adress** – Aktivera det här alternativet om du inte vill använda proxyservern för lokala adresser på intranätet.


## <a name="windows-spotlight"></a>Windows Spotlight

-     **Windows Spotlight** – Tillåt eller blockera Windows Spotlight som innehåller funktioner som tips och råd, meddelanden på låsskärmen i Windows och mycket annat.
    -     **Windows-tips** – Låter dig blockera popup-tips från att visas i Windows.
    -     **Konsumentfunktioner** – Låter dig blockera konsumentfunktioner som t.ex. förslag för startmenyn och medlemskapsaviseringar.

## <a name="display"></a>Visning

- **Användarindata från trådlösa visningsmottagare** – Blockerar användarindata från trådlösa visningsmottagare.
- **Projektion till den här datorn** – Stoppar andra enheter från att upptäcka datorn för projektion.
- **Kräv en PIN-kod för parkoppling** – Kräver en PIN-kod när du ansluter till en projektionsenhet.

## <a name="start"></a>Start

- **Ta bort appar från aktivitetsfältet** – Hindra användaren från att ta bort appar i Start-menyn.
- **Dokument på Start** – Dölj eller visa mappen Dokument i Start-menyn i Windows.
- **Nedladdningar på Start** – Dölj eller visa mappen Nedladdningar i Start-menyn i Windows.
- **Utforskaren på Start** – Dölj eller visa Utforskaren i Start-menyn i Windows.
- **Hemgrupp på Start** – Dölj eller visa mappen Hemgrupp i Start-menyn i Windows.
- **Musik på Start** – Dölj eller visa mappen Musik i Start-menyn i Windows.
- **Nätverk på Start** – Dölj eller visa mappen Nätverk i Start-menyn i Windows.
- **Personlig mapp på Start** – Dölj eller visa den personliga mappen i Start-menyn i Windows.
- **Bilder på Start** – Dölj eller visa mappen för bilder i Start-menyn i Windows.
- **Inställningar på Start** – Dölj eller visa appen Inställningar i Start-menyn i Windows.
- **Videor på Start** – Dölj eller visa mappen för videor i Start-menyn i Windows.
