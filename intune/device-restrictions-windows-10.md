---
title: "Inställningar av enhetsbegränsningar för Windows 10 i Microsoft Intune"
titlesuffix: 
description: "Läs vilka Microsoft Intune-inställningar du kan använda för att kontrollera enhetsinställningar och funktioner på enheter som kör Windows 10."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 861c971c98493f6adab78e6bc93d560bbc1d5243
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2018
---
#<a name="microsoft-intune-windows-10-and-later-device-restriction-settings"></a>Inställningar av enhetsbegränsningar för Microsoft Intune i Windows 10 och senare
I den här artikeln visas alla inställningar av enhetsbegränsningar som du kan konfigurera för enheter som kör Windows 10.

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>Allmänt
- **Skärmbild (endast mobil)** – Gör det möjligt för användaren att hämta enhetens skärm som en bild.
- **Kopiera och klistra in (endast mobil)** – Tillåter funktionen att kopiera och klistra in mellan appar på enheten.
- **Manuell avregistrering** – Tillåter att användaren manuellt tar bort sitt arbetsplatskonto från enheten.
   - Den här inställningen används inte om datorn är ansluten till Azure Active Directory och automatisk registrering har aktiverats. 
   - Den här principinställningen gäller inte för datorer som kör Windows 10 Home.
- **Manuell installation av rotcertifikat (endast mobil)** – Hindrar användaren att manuellt installera rotcertifikat och mellanliggande CAP-certifikat.

- **Kamera** – Tillåt eller blockera användning av kameran på enheten.
- **OneDrive-filsynkronisering** – Blockerar enheten från att synkronisera filer till OneDrive.
- **Flyttbara lagringsmedier** – Anger om externa lagringsenheter, t.ex. SD-kort, kan användas med enheten.
- **Geoplats** – Anger om enheten kan använda information om platstjänster.
- **Internetdelning** – Tillåter användning av Internetanslutningsdelning på enheten.
- **Telefonåterställning** – Styr om användaren kan göra en fabriksåterställning på enheten eller inte.
- **USB-anslutning (endast mobil)** – Styr om enheter har åtkomst till externa lagringsenheter via en USB-anslutning.
- **Stöldskyddsläge (endast mobil)** – Konfigurera om stöldskyddsläget i Windows ska vara aktiverat.
- **Cortana** – Aktivera eller inaktivera röstassistenten Cortana.
- **Röstinspelning (endast mobil)** – Tillåt eller blockera användning av enhetens röstinspelare.
- **Ändra enhetsnamn** – Förhindrar att slutanvändaren ändrar enhetens namn (endast Windows 10 Mobile)
- **Lägg till konfigurationspaket** – Blockerar runtime-konfigurationsagenten som installerar konfigurationspaket.
- **Ta bort konfigurationspaket** – Blockerar runtime-konfigurationsagenten som tar bort konfigurationspaket.
- **Enhetsidentifiering** – Blockerar en enhet från att identifieras av andra enheter.
- **Växla mellan aktiviteter (endast mobil)** – Blockerar funktionen Växla mellan aktiviteter på enheten.
- **Dialogruta om SIM-kortsfel (endast mobil)** – Blockerar ett felmeddelande från att visas på enheten om inget SIM-kort har upptäckts.
- **Ink-arbetsytan** – Blockerar användare från att komma åt Ink-arbetsytan. När den här inställningen inte är konfigurerad är Ink-arbetsytan aktiverad (funktionen är på) och användaren kan använda den ovanför låsskärmen.
- **Automatisk omdistribution** – Låter användare med administrativ behörighet ta bort alla användardata och inställningar med hjälp av **Ctrl + Win + R** på enhetens låsskärm. Enheten omkonfigureras automatiskt och omregistreras för hantering.


## <a name="password"></a>Lösenord
-   **Lösenord** – Kräver att användaren måste ange ett lösenord för att få åtkomst till enheten.
    -   **Krav på lösenordstyp** – Anger om lösenordet måste vara enbart numeriskt, eller om det kan vara alfanumeriskt.
    -   **Minsta längd på lösenord** – Gäller endast Windows 10 Mobile.
    -   **Antal felaktiga inloggningar innan enheten rensas** – För enheter som kör Windows 10: Om BitLocker är aktiverat på enheten försätts den i återställningsläget för BitLocker när den gräns för antal misslyckade inloggningar som du har angett har uppnåtts. Om BitLocker inte är aktiverat på enheten tillämpas inte den här inställningen.
För enheter som kör Windows 10 Mobile: Om inloggningen misslyckas ett visst antal gånger (som du angett) rensas enheten.
    -   **Maximalt antal minuter av inaktivitet innan skärmen låses** – Anger hur lång tid en enhet måste vara i viloläge innan skärmen låses.
    -   **Lösenordets giltighetstid (dagar)** – Anger efter hur lång tid enhetens lösenord måste ändras.
    -   **Förhindra återanvändning av tidigare lösenord** – Anger hur många tidigare använda lösenord enheten kommer ihåg.
    -   **Kräv lösenord när enheten lämnar inaktivt läge (endast Mobile)** – Anger att användaren måste ange ett lösenord för att kunna låsa upp enheten (endast Windows 10 Mobile).
    -   **Enkla lösenord** – Du kan använda enkla lösenord som 1111 och 1234. Dessutom tillåter eller blockerar den här inställningen användningen av Windows-bildlösenord.
-   **Kryptering** – Aktivera kryptering på målenheter.

## <a name="personalization"></a>Anpassning

- **URL för skrivbordsbakgrundsbild (endast skrivbord)** – Ange URL:en till en bild i JPEG-format som du vill använda som skrivbordsbakgrund i Windows. Användare kan inte ändra det här.

## <a name="privacy"></a>Sekretess

-   **Anpassning av inmatning** – Tillåt inte användning av molnbaserade taltjänster för Cortana, diktering eller Microsoft Store-appar. Om du tillåter dessa tjänster kan det hända att Microsoft samlar in röstdata för att förbättra tjänsten.
-   **Automatiskt godkännande av frågor om användarens medgivande till parkoppling och sekretess** – Tillåt Windows att automatiskt godkänna meddelanden om medgivande till parkoppling och sekretess när appar körs.
- **Publicera användaraktiviteter**: Ställ in den här på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen.
- **Endast lokala aktiviteter**: Ställ in det här alternativet på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen baserat på lokala aktiviteter.


Du kan ange information som alla appar på enheten kan komma åt. Du kan också definiera undantag per app med hjälp av **Sekretessundantag per app**.

### <a name="exceptions"></a>Undantag

- **Kontoinformation** – Definiera om den här appen kan komma åt användarnamnet, bilden och annan kontaktinformation.
- **Bakgrundsappar** – Definiera om den här appen kan köras i bakgrunden.
- **Kalender** – Definiera om den här appen kan komma åt kalendern.
- **Samtalshistorik** – Definiera om den här appen kan komma åt samtalshistorik.
- **Kamera** – Definiera om den här appen kan komma åt kameran.
- **Kontakter** – Definiera om den här appen kan komma åt kontakter.
- **E-post** – Definiera om den här appen kan skicka e-post.
- **Plats** – Definiera om den här appen kan komma åt platsinformation.
- **Meddelandefunktioner** – Ange om den här appen kan läsa eller skicka SMS- och MMS-meddelanden.
- **Mikrofon** – Definiera om den här appen kan använda mikrofonen.
- **Rörelse** – Definiera om den här appen kan komma åt rörelseinformation.
- **Meddelanden** – Definiera om den här appen kan komma åt meddelanden.
- **Telefon** – Definiera om den här appen kan komma åt telefonen.
- **Radio** – Vissa appar kan använda radiofunktioner (t.ex. Bluetooth) i din enhet för att skicka och ta emot data och behöver sätta igång eller stänga av de här radiofunktionerna. Definiera om den här appen kan styra dessa radiofunktioner.
- **Uppgifter** – Definiera om den här appen kan komma åt dina uppgifter.
- **Betrodda enheter** – Definiera om den här appen kan använda betrodda enheter (maskinvara du redan har anslutit eller som medföljer den här datorn, surfplattan eller telefonen). Till exempel: TV-apparater, projektorer och så vidare.
- **Feedback och diagnostik** – Definiera om den här appen kan komma åt diagnostisk information.
- **Synkronisering med enheter** – Definiera om den här appen automatiskt kan dela och synkronisera information med trådlösa enheter som inte uttryckligen kopplats ihop med den här datorn, surfplattan eller telefonen.

## <a name="per-app-privacy-exceptions"></a>Sekretessundantag per app

Du kan lägga till appar som ska ha en annan sekretess jämfört med vad du har definierat i din ”standardsekretess”.

- **Paketnamn** – Appaketets familjenamn.
- **Appnamn** – Namnet på appen.

### <a name="exceptions"></a>Undantag

- **Kontoinformation** – Definiera om den här appen kan komma åt användarnamnet, bilden och annan kontaktinformation.
- **Bakgrundsappar** – Definiera om den här appen kan köras i bakgrunden.
- **Kalender** – Definiera om den här appen kan komma åt kalendern.
- **Samtalshistorik** – Definiera om den här appen kan komma åt samtalshistorik.
- **Kamera** – Definiera om den här appen kan komma åt kameran.
- **Kontakter** – Definiera om den här appen kan komma åt kontakter.
- **E-post** – Definiera om den här appen kan skicka e-post.
- **Plats** – Definiera om den här appen kan komma åt platsinformation.
- **Meddelandefunktioner** – Ange om den här appen kan läsa eller skicka SMS- och MMS-meddelanden.
- **Mikrofon** – Definiera om den här appen kan använda mikrofonen.
- **Rörelse** – Definiera om den här appen kan komma åt rörelseinformation.
- **Meddelanden** – Definiera om den här appen kan komma åt meddelanden.
- **Telefon** – Definiera om den här appen kan komma åt telefonen.
- **Radio** – Vissa appar kan använda radiofunktioner (t.ex. Bluetooth) i din enhet för att skicka och ta emot data och behöver sätta igång eller stänga av de här radiofunktionerna. Definiera om den här appen kan styra dessa radiofunktioner.
- **Uppgifter** – Definiera om den här appen kan komma åt dina uppgifter.
- **Betrodda enheter** – Definiera om den här appen kan använda betrodda enheter (maskinvara du redan har anslutit eller som medföljer den här datorn, surfplattan eller telefonen). Till exempel: TV-apparater, projektorer och så vidare.
- **Feedback och diagnostik** – Definiera om den här appen kan komma åt diagnostisk information.
- **Synkronisering med enheter** – Definiera om den här appen automatiskt kan dela och synkronisera information med trådlösa enheter som inte uttryckligen kopplats ihop med den här datorn, surfplattan eller telefonen.

## <a name="locked-screen-experience"></a>Låsskärm

- **Aviseringar från Åtgärdscenter (endast mobil)** – Aviseringar från Åtgärdscenter visas på enhetens låsskärm (endast Windows 10 Mobile).
- **URL till bild av låst skärm (endast skrivbord)** – Anger webbadressen till en bild i JPEG-format som ska användas som låsskärmsbild i Windows. Användare kan inte ändra det här.
-   **Skärmtidsgräns kan ställas in av användaren (endast Mobile)** – Användarna kan konfigurera tiden 
-   **Cortana på låst skärm (endast stationär dator)** – Tillåt inte användare att interagera med Cortana när enheten har låst skärm (endast stationära datorer med Windows 10).
-   **Popup-meddelanden på låst skärm** – Hindra varningsmeddelanden från att visas på enhetens låsskärm.
-   **Skärmtidsgräns (endast Mobile)** – Anger tiden i sekunder mellan att skärmen låses och stängs av.



## <a name="app-store"></a>Appbutik

-   **Appbutik (endast mobil)** – Aktivera eller blockera användning av appbutiken på Windows 10 Mobile-enheter.
-   **Uppdatera appar automatiskt från Store** – Appar som installeras från Microsoft Store uppdateras automatiskt.
-   **Installation av betrodd app** – Appar som signeras med ett betrott certifikat läses in separat.
-   **Lås upp via utvecklare** – Tillåter Windows utvecklarinställningar, till exempel att separat inlästa appar ska kunna ändras av användaren.
-   **Dela appdata mellan användare** – Tillåter att appar delar data mellan olika användare på samma enhet.
-   **Använd endast privat katalog** – Aktivera det här alternativet för att endast tillåta att användarna hämtar appar från din privata katalog.
-   **Start av appar från Store** – Används för att inaktivera alla appar som har förinstallerats på enheten eller hämtats från Microsoft Store.
-   **Installera appdata på systemvolym** – Hindrar appar från att lagra data på enhetens systemvolym.
-   **Installera appar på systemenhet** – Hindrar appar från att lagra data på enhetens systemenhet.
-   **Game DVR (endast skrivbord)** – Konfigurerar om registrering och sändning av spel tillåts.
-   **Endast appar från butik** – Konfigurerar om användare kan installera appar från andra platser än appbutiken.



## <a name="edge-browser"></a>Microsoft Edge-webbläsare

-   **Microsoft Edge-webbläsare (endast mobil)** – Tillåt användning av Edge-webbläsaren på enheten.
-   **Listruta i adressfältet (endast skrivbord)** – Använd den här inställningen till att hindra Edge från att visa en lista med förslag när du skriver. Det här hjälper till att minimera användningen av nätverksbandbredd mellan Edge och Microsoft-tjänster.
-   **Synkronisera favoriter mellan Microsoft-webbläsare (endast skrivbord)** – Tillåter att Windows synkroniserar favoriter mellan Internet Explorer och Edge.
-   **Skicka Do Not Track-huvuden** – Konfigurerar Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker.
-   **Cookies** – Gör att webbläsaren sparar Internetcookies på enheten.
-   **JavaScript** – Tillåter att skript (exempelvis JavaScript) körs i Edge-webbläsaren.
-   **Popup-fönster** – Blockerar popup-fönster i webbläsaren (gäller endast Windows 10 Desktop).
-   **Sökförslag** – Tillåter att din sökmotor föreslår webbplatser när du skriver sökfraser.
-   **Skicka intranätstrafik till Internet Explorer** – Låter användarna öppna intranätswebbplatser i Internet Explorer (endast Windows 10 Desktop).
-   **Autofyll** – Tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren (endast Windows 10 Desktop).
-   **Lösenordshanteraren** – Aktivera eller inaktivera lösenordshanteraren för Microsoft Edge.
-   **Plats för webbplatslista för företagsläge** – Anger var du hittar listan med webbplatser som kan öppnas i företagsläge. Användare kan inte redigera den här listan.<br>(Endast Windows 10 Desktop.)
-   **Utvecklarverktyg** – Förhindrar att användaren kan öppna Edge-utvecklingsverktygen.
-   **Tillägg** – Tillåter att användaren installerar Edge-tillägg på enheten.
-   **InPrivate-surfning** – Förhindrar att användaren öppnar InPrivate-surfningssessioner.
-   **Visa sidan Första körningen** – Hindrar startsidan från att visas första gången du kör Edge.
    -   **Första körningswebbadress** – Anger webbadressen till en sida som visas första gången en användare kör Edge (endast Windows 10 Mobile).
-   **Startsidor** – Lägg till en lista över webbplatser du vill använda som startsidor i Edge-webbläsaren (endast skrivbord).
-   **Ändringar av startsidan** – Tillåter användare att ändra de startsidor som visas när Edge öppnas. Använd inställningen Startsidor för att skapa sidan eller använd en lista över sidor som öppnas när Microsoft Edge startar.
-   **Blockera åtkomst till Om flaggor** – Förhindra att användaren kommer åt sidan about:flags i Microsoft Edge som innehåller inställningar för utvecklare och experiment.
-   **localhost-ip-adress via WebRtc** – Blockera användarens ip-adress till localhost vid telefonsamtal via WebRTC-protokollet.
-   **Standardsökmotor** – Ange den standardsökmotor som ska användas. Användarna kan ändra det här värdet när som helst.
-   **Rensa webbläsardata vid avslut** – Rensar historik och webbdata när användaren avslutar Edge.
-   **Datainsamling för levande panel** – Stoppar Windows från att samla in information från den levande panelen när användaren fäster en plats på Start-menyn från Microsoft Edge.
-  **Listan Favoriter** – Definierar sökvägen till filen med favoriter. Till exempel http://contoso.com/favorites.html.
-  **Begränsa ändringar i Favoriter** – Ställ in detta på **Blockera** för att hindra användarna från att lägga till, importera, sortera och redigera i listan Favoriter. 

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **SmartScreen för Microsoft Edge** – Aktivera Edge SmartScreen för att komma åt plats och filhämtningar.
- **Obehörig åtkomst** – Blockera användare från att ignorera varningarna från Windows Defender SmartScreen-filtret och blockera dem från att gå till webbplatsen.
- **Overifierad filhämtning** – Blockera användare från att ignorera varningarna från Windows Defender SmartScreen-filtret och blockera dem från att hämta overifierade filer.

## <a name="search"></a>Sök
- **Säker sökning (endast mobil)** – Styr hur Cortana filtrerar innehåll för vuxna i sökresultaten. Du kan välja **Strikt**, **Måttlig** eller tillåta att användaren väljer sina egna inställningar.

## <a name="cloud-and-storage"></a>Moln och lagring
-   **Microsoft-konto** – Låter användaren associera ett Microsoft-konto med enheten.
-   **Andra konton än Microsoft-konton** – Låter användaren lägga till e-postkonton på enheten som inte är associerade med något Microsoft-konto.
-   **Synkroniseringsinställningar för Microsoft-konto** – Tillåt att enhets- och appinställningar som har associerats med ett Microsoft-konto synkroniseras mellan enheter.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning

-   **Mobildatakanal** – Hindrar användare från att använda data, t.ex. för webbsurfning, när de är anslutna till ett mobilnät. 
-   **Datanätverksväxling** – Tillåt växling mellan nätverk vid åtkomst till data.
-   **VPN över mobilt nätverk** – Styr om enheten har åtkomst till VPN-anslutningar när den är ansluten till ett mobilt nätverk.
-   **VPN-nätverksväxling över mobilt nätverk** – Styr om enheten har åtkomst till VPN-anslutningar när den är nätverksväxlas i ett mobilt nätverk.
-   **Bluetooth** – Styr om användaren kan aktivera och konfigurera Bluetooth på enheten.
-   **Bluetooth-identifiering** – Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.
-   **Bluetooth-förhandsparkoppling** – Med den här inställningen kan du konfigurera vissa Bluetooth-enheter till att automatiskt parkopplas med en värdenhet.
-   **Bluetooth-annonsering** – Låter enheten ta emot annonser via Bluetooth.
-   **Connected Devices Service** – Låter dig välja om du vill tillåta tjänsten Connected Devices Service. Tjänsten aktiverar identifiering av och anslutning till andra Bluetooth-enheter.
-   **NFC** – Låter användaren aktivera och konfigurera närfältskommunikation på enheten.
-   **Trådlöst** – Låter användaren aktivera och konfigurera trådlösa funktioner på enheten (endast Windows 10 Mobile).
-   **Anslut automatiskt till trådlösa surfpunkter** – Tillåter att enheten ansluter automatiskt till kostnadsfria trådlösa surfpunkter och att den godkänner eventuella villkor för anslutningen automatiskt.
-   **Manuell trådlös konfiguration** – Styr om användarna kan konfigurera egna trådlösa anslutningar, eller om de endast kan använda anslutningar som konfigurerats med en trådlös profil (endast Windows 10 Mobile).
-   **Sökintervall för trådlöst nätverk** – Ange hur ofta enheterna ska söka efter trådlösa nätverk. Ange ett värde mellan 1 (mest frekvent) till 500 (minst frekvent).
-   **Bluetooth-tillåtna tjänster** – Ange, i form av hexadecimala strängar, en lista över tillåtna Bluetooth-tjänster och Bluetooth-profiler.


## <a name="control-panel-and-settings"></a>Kontrollpanel och inställningar

-   **Inställningsapp** – Blockera åtkomst till appen för Windows-inställningar.
    -   **System** – Blockerar åtkomsten till systemområdet för inställningsappen.
        -   **Ändra energialternativinställningar (endast skrivbord)** – Förhindrar att användaren ändrar energialternativinställningar på enheten.
    -   **Enheter** – Blockerar åtkomsten till enhetsområdet för inställningsappen.
    -   **Nätverk och Internet** – Blockerar åtkomsten till nätverket och Internetområdet för inställningsappen.
    -   **Anpassning** – Blockerar åtkomsten till anpassningsområdet för inställningsappen.
    -   **Konton** – Blockerar åtkomsten till kontoområdet för inställningsappen.
    -   **Tid och språk** – Blockerar åtkomsten till tid- och språkområdet för inställningsappen.
        -   **Ändra systemtid** – Förhindrar att användaren ändrar enhetens datum och tid.
        -   **Ändra nationella inställningar (endast skrivbord)** – Förhindrar att användaren ändrar de nationella inställningarna på enheten.
        -   **Ändra språkinställningar (endast skrivbord)** – Förhindrar att användaren ändrar språkinställningarna på enheten.
    -   **Spel** – Blockerar åtkomsten till spelappen i inställningar.
    -   **Hjälpmedel** – Blockerar åtkomsten till området Hjälpmedel för inställningsappen.
    -   **Sekretess** – Blockerar åtkomsten till sekretessområdet för inställningsappen.
    -   **Uppdatering och säkerhet** – Blockerar åtkomst till uppdaterings- och säkerhetsområdet i inställningsappen.

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

## <a name="display"></a>Visning

- **Aktivera GDI-skalning för appar**
- **Stäng av GDI-skalning för appar**

  Med GDI DPI-skalning kan appar som inte är DPI-medvetna bli DPI-medvetna per övervakare. Ange äldre appar som har DPI-GDI-skalning aktiverat. Med GDI DPI-skalning konfigurerat till att både aktivera och inaktivera en app, är skalning inaktiverat för appen.

## <a name="kiosk-preview"></a>Helskärmsläge (förhandsgranskning)

-   **Helskärmsläge** – Identifierar den typ av [helskärmsläge](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc) som stöds av principen. Alternativen är:

      - **Inte konfigurerad** (standard) – Principen aktiverar inte ett helskärmsläge. 
      - **Läget för enskilda appar för kiosk** – Profilen gör att enheten kan användas som en kiosk för enskilda appar.
      - **Flerappsläge för kiosk** – Profilen gör att enheten kan användas som en kiosk för flera appar.

    Kiosker för enskilda appar kräver följande inställningar:

      - **Användarkonto** – Anger det lokala (för enheten) användarkontot eller Azure AD-kontoinloggning som är kopplat till kioskappen. För konton som är kopplade till Azure AD-domäner ska kontot anges i formatet `domain\\username@tenant.org`.

         För enheter i offentliga miljöer ska man använda konton med minimal behörighet för att förhindra obehöriga aktiviteter.  

      - **Appens programanvändarmodell-ID (AUMID)** – Anger AUMID för kioskappen. Läs mer i [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Hitta programanvändarmodell-ID för en installerad app).

    [Flerappsläge för kiosk](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) kräver en kioskkonfiguration. Använd knappen **Lägg till** för att skapa en kioskkonfiguration eller välja en befintlig.

    Kioskkonfigurationer för flera appar omfattar följande inställningar:

    - **Namn på kioskkonfiguration** – Ett eget namn som används för att identifiera en viss konfiguration.

    - En eller flera **kioskappar** som består av:

        - **Apptyp** som anger typen av kioskapp.  Värden som stöds är:   

            - **Win32-app** – En traditionell skrivbordsapp. (Du behöver den fullständigt kvalificerade sökvägen till den körbara filen, med hänsyn till enheten.)

            - **UWP-app** – En universell Windows-app. Du behöver [AUMID för appen](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

        - **Appidentifierare** – Anger antingen den fullständigt kvalificerade sökvägen för den körbara filen (Win32-appar) eller [appens AUMID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (UWP-appar).

    - **Verktygsfält** anger om verktygsfältet ska visas (**Aktiverat**) eller döljas (**Inte konfigurerat**) i kiosken.

    - **Startmenylayout** – Anger en XML-fil som beskriver hur apparna [visas på Start-menyn](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file).

    - **Tilldelade användare** – Anger ett eller flera användarkonton som är kopplade till kioskkonfigurationen. Kontot kan vara lokalt på enheten eller en Azure AD-kontoinloggning som är kopplad till kioskappen. Ange domänanslutna konton med formatet `domain\\username@tenant.org`.

## <a name="windows-defender-antivirus"></a>Windows Defender Antivirus

-   **Övervakning i realtid** – Tillåter genomsökning i realtid efter skadlig programvara, spionprogram och annan oönskad programvara.
-   **Övervaka funktionssätt** – Tillåter att Defender söker efter kända mönster för misstänkt aktivitet på enheterna.
-   **NIS (Network Inspection System)** – NIS hjälper till att skydda enheter mot nätverksbaserade säkerhetsrisker. Det använder signaturer för kända problem från Microsoft Endpoint Protection Center för att identifiera och blockera skadlig trafik.
-   **Sök igenom alla nedladdningar** – Styr om Defender genomsöker alla filer som laddas ner från Internet.
-   **Sök igenom skripts som har lästs in via Microsoft-webbläsare** – Tillåter Defender-genomsökning av skript som används i Internet Explorer.
-   **Användaråtkomst till Defender** – Styr om Windows Defender-användargränssnittet är dolt för slutanvändarna.
När den här inställningen ändras börjar den gälla nästa gång användarens dator startas om.
-   **Intervall för signaturuppdatering (i timmar)** – Ange med vilket intervall Defender söker efter nya signaturfiler.
-   **Övervaka fil- och programaktivitet** – Tillåter att Defender övervakar fil- och programaktivitet på enheter.
-   **Dagar innan skadlig kod i karantän tas bort** – Tillåter att Defender fortsätter spåra åtgärdad skadlig kod det antal dagar som du anger, för att du ska kunna kontrollera tidigare berörda enheter manuellt. Om du ställer in antalet dagar till **0** finns skadlig kod kvar i karantänmappen och tas inte bort automatiskt.
-   **Gräns för processoranvändning under genomsökning** – Tillåter att du begränsar hur mycket processorkraft som genomsökningarna får använda (från **1** till **100**).
-   **Sök igenom arkivfiler** – Tillåter att Defender söker igenom arkiverade filer, till exempel ZIP- eller CAB-filer.
-   **Sök igenom inkommande e-postmeddelanden** – Tillåter att Defender söker igenom e-postmeddelanden när de tas emot på enheten.
-   **Sök igenom flyttbara enheter vid fullständig genomsökning** –Tillåter att Defender genomsöker flyttbara enheter, som t.ex. USB-minnen.
-   **Sök igenom mappade nätverksenheter vid fullständig genomsökning** – Tillåter att Defender genomsöker filer på mappade nätverksenheter.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.
-   **Sök igenom filer öppnade från nätverksmappar** – Tillåter att Defender genomsöker filer på delade nätverksenheter (till exempel filer som nås från en UNC-sökväg).
Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.
-   **Molnskydd** – Tillåter eller förhindrar att Microsoft Active Protection Service tar emot information om aktiviteter mot skadlig kod från enheter som du hanterar. Den här informationen används för att förbättra tjänsten i framtiden.
-   **Be användarna att skicka exempel** – Anger om potentiellt skadliga filer som kan kräva ytterligare analys ska skickas automatiskt till Microsoft.
-   **Tidpunkt för daglig snabbsökning** – Tillåter att du schemalägger en snabbgenomsökning som körs varje dag vid den tidpunkt som du väljer.
-   **Typ av systemgenomsökning som ska utföras** – Här kan du ange nivå för genomsökningen som ska utföras när du schemalägger en systemgenomsökning.
-   **Identifiera potentiellt oönskade program** – Välj nivå av skydd när Windows identifierar potentiellt oönskade appar från:
        - **Blockera**
        - **Granska** Mer information om potentiellt oönskade appar finns i [det här avsnittet](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
-   **Åtgärder vid hot om identifierad skadlig kod** – Aktivera det här alternativet för att ange vilka åtgärder du vill att Defender ska vidta för varje hotnivå den identifierar (låg, måttlig, hög och allvarlig). De åtgärder du kan vidta är:
    -   **Rensa**
    -   **Karantän**
    -   **Ta bort**
    -   **Tillåt**
    -   **Användardefinierad**
    -   **Blockera**



### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender antivirusundantag

-   **Filer och mappar som ska undantas från genomsökningar och realtidsskydd** – Lägger till en eller flera filer och mappar, som t.ex. **C:\Path** eller **%ProgramFiles%\Path\filename.exe**, i undantagslistan. Dessa filer och mappar tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.
-   **Filnamnstillägg som ska undantas från genomsökningar och realtidsskydd** – Lägg till ett eller flera filnamnstillägg, som t.ex. **jpg** eller **txt**, i undantagslistan. Filer med dessa filnamnstillägg tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.
-   **Processer som ska undantas från genomsökningar och realtidsskydd** – Lägg till en eller flera processer av typen **.exe**, **.com** eller **.scr** i undantagslistan. Dessa processer tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.


## <a name="network-proxy"></a>Nätverksproxy

-   **Identifiera proxyinställningar automatiskt** – När det här alternativet är aktiverat kommer enheten att försöka hitta sökvägen till ett PAC-skript.
-   **Använd proxyskript** – Välj detta alternativ om du vill ange en sökväg till ett PAC-skript för att konfigurera proxyservern.
    -   **Ställ in webbadress till skript** – Ange webbadressen för ett PAC-skript som du vill använda för att konfigurera proxyservern.
-   **Använd manuell proxyserver** – Välj detta alternativ om du vill ange proxyserverinformationen manuellt.
    -   **Adress** – Ange namn eller IP-adress för proxyservern.
    -   **Portnummer** – Ange portnumret till proxyservern.
    -   **Proxy-undantag** – Ange de webbadresser som inte får använda proxyservern. Använd semikolon för att avgränsa varje objekt.
    -   **Använd ingen proxyserver för lokal adress** – Aktivera det här alternativet om du inte vill använda proxyservern för lokala adresser på intranätet.


## <a name="windows-spotlight"></a>Windows Spotlight


- **Windows Spotlight** – Använd den här inställningen för att blockera alla Windows Spotlight-funktioner på Windows 10-enheter. Följande inställningar är inte tillgängliga om du blockerar den här inställningen.
    - **Windows Spotlight på låsskärm** – Hindra Windows Spotlight från att visa information på enhetens låsskärm.
    - **Tredjepartsförslag i Windows Spotlight** – Hindra Windows Spotlight från att föreslå innehåll som inte har publicerats av Microsoft.
    - **Konsumentfunktioner** – Låter dig blockera konsumentfunktioner som t.ex. förslag för startmenyn och medlemskapsaviseringar.
    - **Windows-tips** – Låter dig blockera popup-tips från att visas i Windows.
    - **Windows Spotlight i Åtgärdscenter** – Blockera Windows Spotlight-förslag, på t.ex. nya appar eller säkerhetsinnehåll, från att visas i Windows Åtgärdscenter.
    - **Windows Spotlight-anpassning** – Hindra Windows Spotlight från att anpassa resultat baserat på användningen av en enhet.
    - **Välkommen till Windows-skärm** – Blockera Välkommen till Windows-skärmen där användarinformation om nya eller uppdaterade funktioner visas.


## <a name="projection"></a>Projektion

- **Användarindata från trådlösa visningsmottagare** – Blockerar användarindata från trådlösa visningsmottagare.
- **Projektion till den här datorn** – Stoppar andra enheter från att upptäcka datorn för projektion.
- **Kräv en PIN-kod för parkoppling** – Kräver en PIN-kod när du ansluter till en projektionsenhet.

## <a name="cloud-printer"></a>Molnskrivare

- **URL för skrivaridentifiering** – Slutpunkt för identifiering av molnskrivare.
- **URL för utfärdare av skrivaråtkomst** – Autentiseringsslutpunkt för att hämta OAuth-token.
- **GUID för inbyggd Azure-klientapp** – GUID för ett klientprogram som har behörighet att hämta OAuth-token från OAuthAuthority.
- **Resurs-URI för utskriftstjänst** – OAuth resurs-URI för utskriftstjänster som konfigurerats i Azure-portalen.
- **Maxantal skrivare att fråga efter (endast mobil)** – maximalt antal skrivare som ska efterfrågas från en slutpunkt för identifiering.
- **Resurs-URI för identifiering av utskriftstjänst** – OAuth resurs-URI för identifiering av utskriftstjänster som konfigurerats i Azure-portalen.

## <a name="reporting-and-telemetry"></a>Rapportering och telemetri

- **Dela användningsdata** – Välj nivå av diagnostikdata.
- **Proxyserver för telemetri**

  Ange det fullständigt kvalificerade domännamnet (FQDN) eller IP-adressen för en proxyserver för att vidarebefordra anslutna användarupplevelser och telemetribegäranden som använder en SSL-anslutning (Secure Sockets Layer). Formatet för den här inställningen är *server*:*port*. Om den namngivna proxyn misslyckas, eller om det inte finns någon proxyserver angiven när den här principen aktiveras, överförs inte anslutna användarupplevelser och telemetridata, utan de finns kvar på den lokala enheten.

   Exempelformat:

   IPv4: 192.246.246.106:100<br>
 IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100<br> FQDN: www.contoso.com:345

## <a name="messaging"></a>Meddelandefunktion

- **Meddelandesynkronisering (endast mobil)** – Inaktivera meddelandefunktioner överallt och säkerhetskopiering och återställning av textmeddelanden.
- **MMS (endast mobil)** – Inaktivera funktionen för att skicka och ta emot MMS på enheten.
- **RCS (endast mobil)** – Inaktivera funktionen för att skicka och ta emot Rich Communication Services på enheten.












