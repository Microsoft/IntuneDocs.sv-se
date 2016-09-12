---
title: "Principinställningar för Windows 10 |Microsoft Intune"
description: "Använd principinställningarna som anges i det här avsnittet om du vill konfigurera inbyggda och anpassade inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7ef205aece89667ea84b9b73e42e71fc540fa257
ms.openlocfilehash: cbfd2da544814dc93a818a1ca5bd0496a268634b


---

# Principinställningar för Windows 10 i Microsoft Intune

Använd principinställningarna som anges i det här avsnittet om du vill konfigurera inbyggda och anpassade inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter.

> [!IMPORTANT]
> Du kan hantera Windows 10-datorer på två olika sätt: Genom att registrera dem eller genom att installera Intune-klientprogramvara. Varje metod erbjuder olika funktioner (mer information finns i [Välj hur du vill hantera enheter](/intune/get-started/choose-how-to-manage-devices)).
> När du hanterar Windows 10-enheter med Intune-klientprogramvaran kan du inte använda de principer och inställningar som anges i det här avsnittet. Om du vill använda dessa inställningar måste du registrera Windows 10-enheterna i Intune.

## Generella inställningar för konfigurationsprinciper

Använd den **allmänna konfigurationsprincipen** för Windows Intune för Windows 10 om du vill konfigurera allmänna inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter. 


### Lösenord

|Inställningsnamn|Information|
|----------------|----------------------|
|**Kräv ett lösenord för att låsa upp enheter**|Kräv ett lösenord på enheter som stöds.|
|**Lösenordstyp krävs**|Anger vilken typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt|
|**Krav på lösenordstyp** - **Minsta antal teckenuppsättningar**|Det finns fyra teckenuppsättningar: gemena bokstäver, versala bokstäver, siffror och symboler. Den här inställningen anger hur många olika teckenuppsättningar som lösenordet måste innehålla.|
|**Minsta längd på lösenord**|Anger det minsta antalet tecken som enhetens lösenord måste innehålla.<br>(endast Windows 10 Mobile)|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Rensar enheten om detta antal inloggningsförsök misslyckas.|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Anger hur lång tid en enhet måste vara inaktiv innan skärmen låses.|
|**Lösenordets giltighetstid (i dagar)**|Anger efter hur lång tid enhetens lösenord måste ändras.|
|**Kom ihåg tidigare lösenord**|Anger om du vill hindra användaren från att återanvända tidigare lösenord.|
|**Spara lösenordshistorik** - **Förhindra återanvändning av tidigare lösenord **|Anger hur många tidigare använda lösenord som sparas av enheten.|
|**Kräv lösenord när enheten återgår från viloläge**|Om den här inställningen är aktiverad måste användaren ange ett lösenord för att låsa upp enheten från inaktivt läge.<br>(endast Windows 10 Mobile)|

### Kryptering

|Inställningsnamn|Information|
|----------------|----------------------|
|**Filkryptering på mobil enhet**|Aktiverar kryptering på målenheter.<br>(endast Windows 10 Mobile)|

### System

|Inställningsnamn|Information|
|----------------|----------------------|
|**Tillåt skärmbild**|Låter användaren fånga enhetens skärm som en bild.<br>(endast Windows 10 Mobile)|
|**Tillåt manuell avregistrering**|Tillåter att användaren manuellt raderar sitt arbetsplatskonto från enheten.|
|**Tillåt manuell installation av rotcertifikat**|Anger om användaren kan installera rotcertifikat manuellt.<br>(endast Windows 10 Mobile)|
|**Tillåt att diagnostik- och användardata skickas till Microsoft**|Anger mängden diagnostik- och användningsdata som skickas till Microsoft från enheter.<br><br>**Nej** – Inga data skickas till Microsoft<br>**Grundläggande** – Enheten skickar endast begränsad information till Microsoft<br>**Utökad** – Skickar förbättrade diagnostikdata till Microsoft<br>**Fullständig (rekommenderas)** –Skickar samma data som **Utökad**, plus ytterligare information om enhetens tillstånd|


### Konto och synkronisering

|Inställningsnamn|Information|
|----------------|----------------------|---------------------|
|**Tillåt Microsoft-konto**|Låter användaren associera ett Microsoft-konto med enheten.|
|**Tillåt att lägga till icke-Microsoft konton manuellt**|Låter användaren lägga till e-postkonton till enheten som inte är associerade med ett Microsoft-konto.|
|**Tillåt synkronisering av inställningar för Microsoft-konton**|Tillåt att enhets- och appinställningar som associeras med ett Microsoft-konto synkroniseras mellan enheter.|

### Microsoft Edge

|Inställningsnamn|Information|
|----------------|----------------------|
|**Tillåt webbläsare**|Tillåt användningen av Microsoft Edge-webbläsaren på enheten.<br>(endast Windows 10 Mobile)|
|**Tillåt sökförslag i adressfältet**|Tillåter att din sökmotor föreslår platser när du skriver sökord.|
|**Tillåt att intranättrafik skickas till Internet Explorer**|Tillåter att användarna öppnar intranätsplatser i Internet Explorer.<br>(endast Windows 10 Desktop)|
|**Tillåt spåra inte**|Konfigurerar Microsoft Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker.|
|**Aktivera SmartScreen**|Aktiverar webbläsarinställningen SmartScreen på enheter.|
|**Tillåt active scripting**|Tillåter att skript, t.ex. JavaScript, körs i Microsoft Edge-webbläsaren.|
|**Tillåt popup-fönster**|Aktiverar eller inaktiverar webbläsarens blockering av popup-fönster.<br>(endast Windows 10 Desktop)|
|**Tillåt cookies**|Tillåt eller inaktivera cookies.|
|**Tillåt autofyll**|Tillåt att användarna ändrar inställningarna för Komplettera automatiskt i webbläsaren.<br>(endast Windows 10 Desktop)|
|**Tillåt lösenordshanteraren**|Aktivera eller inaktivera lösenordshanteraren för Microsoft Edge.|
|**Listplats för Företagsläge-webbplats**|Anger var man hittar listan över webbsidor som öppnar i Enterprise-läge. Användare kan inte redigera den här listan.<br>(endast Windows 10 Desktop)|

### Appar

|Inställningsnamn|Information|
|----------------|----------------------|---------------------|
|**Tillåt appbutik**|Tillåt att användaren kommer åt appbutiken på enheten.<br>(endast Windows 10 Mobile)|



### Mobilnät

|Inställningsnamn|Information|
|----------------|----------------------|---------------------|
|**Tillåt dataroaming**|Tillåt växling mellan nätverk vid åtkomst till data.|
|**Tillåt VPN via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar när den är ansluten till ett mobilnät.|
|**Tillåt VPN-roaming via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar vid roaming i ett mobilnät.|

### Maskinvara

|Inställningsnamn|Information|
|----------------|----------------------|
|**Tillåt kamera**|Anger om enhetens kamera kan användas.|
|**Tillåt flyttbara lagringsenheter**|Anger om externa lagringsenheter, till exempel ett SD-kort, kan användas med enheten.|
|**Tillåt Wi-Fi**|Tillåter användningen av enheternas Wi-Fi-funktion.<br>(endast Windows 10 Mobile)|
|**Tillåt internetdelning**|Tillåt användningen av Internetanslutningsdelning på enheten.|
|**Tillåt manuell Wi-Fi konfiguration**|Styr huruvida användarna kan konfigurera egna trådlösa anslutningar eller om de endast kan använda anslutningar som konfigurerats med en Wi-Fi-profil.<br>(endast Windows 10 Mobile)|
|**Tillåt automatisk anslutning till kostnadsfria, trådlösa surfpunkter**|Tillåter att enheten ansluter automatiskt till kostnadsfria trådlösa surfzoner och att den godkänner eventuella villkor för anslutningen automatiskt.|
|**Tillåt geolokalisering**|Anger om enheten kan använda tjänsterna för platsinformation.|
|**Tillåt NFC**|Tillåter att enheten använder funktioner för närfältskommunikation.|
|**Tillåt Bluetooth**|Tillåter användningen av Bluetooth-funktioner på enheten.|
|**Tillåt att Bluetooth kan hittas**|Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.|
|**Tillåt Bluetoothreklam**|Tillåter att enheter tar emot reklam via Bluetooth.|
|**Tillåt telefonåterställning**|Styr huruvida användaren kan fabriksåterställa enheten.|
|**Tillåt USB-anslutning**|Styr huruvida enheter kan komma åt externa lagringsenheter via en USB-anslutning.|
|**Tillåt AntiTheft läge**|Konfigurera om Windows Antitheft läge är aktiverat.|

### Funktioner

|Inställningsnamn|Information|
|----------------|----------------------|---------------------|
|**Tillåt kopiera och klistra in**|Aktivera eller inaktivera användningen av Kopiera och Klistra in på enheten.<br>(endast Windows 10 Mobile)|
|**Tillåt röstinspelning**|Aktivera eller inaktivera röstinspelningsfunktionerna på enheten.<br>(endast Windows 10 Mobile)|
|**Tillåt Cortana**|Aktivera eller inaktivera röstassistenten Cortana.|
|**Tillåt action center meddelanden**|Aktivera eller inaktivera aviseringar från Åtgärdscenter på enhetens låsskärm.<br>(endast Windows 10 Mobile)|

### Defender

Alla inställningar gäller endast Windows 10 Desktop.

|Inställningsnamn|Information|
|-|-|
|**Tillåt realtidsövervakning**|Tillåter genomsökning i realtid efter skadlig programvara, spionprogram och annan oönskad programvara.|
|**Tillåt beteendeövervakning**|Tillåter att Defender söker efter kända mönster på misstänkt aktivitet på enheter.|
|**Aktivera system för nätverksinspektion**|Kontrollsystemet för nätverk (NIS) hjälper till att skydda enheter mot nätverksbaserade kryphål genom att använda signaturerna för kända säkerhetsrisker från Microsoft Endpoint Protection Center för att identifiera och blockera skadlig trafik.|
|**Skanna alla hämtningar**|Kontrollerar om Defender söker igenom alla filer som hämtas från Internet.|
|**Tillåt skriptgenomsökning**|Tillåter att Defender genomsöker skript som används i Internet Explorer.|
|**Övervaka fil- och programaktivitet**|Aktivera den här inställningen om du vill att Defender ska övervaka fil- och programaktivitet på enheter.|
|**Dagar som löst skadlig kod ska spåras**|Tillåter att Defender fortsätter spåra åtgärdad skadlig kod det antal dagar som du anger så att du kan kontrollera tidigare berörda enheter manuellt. Om du ställer in antalet dagar till **0** finns skadlig kod kvar i karantänmappen och tas inte bort automatiskt. |
|**Tillåt användargränssnittåtkomst för klient**|Styr huruvida Windows Defender-användargränssnittet är dolt från slutanvändarna.<br>Om den här inställningen ändras börjar den gälla nästa gång slutanvändarens dator startas om.|
|**Schemalägg en snabb daglig genomgång**|Tillåter att du schemalägger en snabbgenomsökning som körs varje dag vid den tidpunkt som du väljer.|
|**Schemalägg en systemsökning**|Tillåter att du schemalägger en fullständig sökning eller en snabbsökning som körs regelbundet på den dag och vid den tidpunkt som du väljer.|
|**Begränsa CPU-användning under en skanning**|Tillåter att du begränsar hur mycket processorkraft som genomsökningarna får använda (från **1** till **100**)|
|**Skanna arkivfiler**|Tillåter att Defender söker igenom arkiverade filer, till exempel ZIP- eller CAB-filer.|
|**Skanna e-postmeddelanden**|Tillåter att Defender söker igenom e-postmeddelanden när de tas emot på enheten.|
|**Skanna flyttbara enheter**|Tillåter att Defender söker igenom flyttbara enheter, t.ex. USB-minnen.|
|**Skanna mappade nätverksenheter**|Tillåter att Defender söker igenom filer på mappade nätverksenheter.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|
|**Skanna filer som har öppnats från delade nätverksmappar**|Tillåter att Defender söker igenom filer på delade nätverksenheter, till exempel de som nås från en UNC-sökväg.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|
|**Intervall för signaturuppdatering**|Ange med vilket intervall som Defender ska söka efter nya signaturfiler.|
|**Tillåt molnskydd**|Tillåt eller förhindra att Microsoft Active Protection Service tar emot information om skadlig kod från enheter som du hanterar. Den här informationen används för att förbättra tjänsten i framtiden.|
|**Be användarna att skicka exempel**|Styr huruvida filer som kan kräva ytterligare analys av Microsoft för att avgöra om de är skadliga ska skickas automatiskt till Microsoft.|
|**Identifiering av potentiellt oönskade program**|Du kan använda den här inställningen för att skydda registrerade Windows-skrivbordsenheter från att köra program som Windows Defender har klassificerat som potentiellt oönskade. Du kan skydda dig mot att dessa program körs eller använda granskningsläget för att rapportera att ett potentiellt oönskat program har installerats.|
|**Filer och mappar som ska undantas när du kör en skanning eller använder realtidsskydd**|Lägg till en eller flera filer och mappar som **C:\Sökväg** eller **%ProgramFiles%\Sökväg\filnamn.exe** i undantagslistan. Dessa filer och mappar tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|
|**Filändelser som ska undantas när du kör en skanning eller använder realtidsskydd**|Lägg till ett eller flera filnamnstillägg som **jpg** eller **txt** i undantagslistan. Filer med dessa filnamnstillägg tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|
|**Processer som ska undantas när du kör en skanning eller använder realtidsskydd**|Lägg till en eller flera processer av typen **.exe**, **.com** eller **.scr** i undantagslistan. De här processerna tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.| 


### Inställningar för uppdateringar

|Inställningsnamn|Information|
|----------------|---------------|
|**Tillåt automatiska uppdateringar**|Aktivera den här inställningen för att tillåta automatiska uppdateringar. Konfigurera sedan någon av följande inställningar för att kontrollera uppdateringsbeteende:<br /><br />**Meddela om hämtning**<br /><br />**Automatisk installation vid underhållstidpunkt**<br /><br />**Automatisk installation och omstart vid underhållstidpunkt**<br /><br />**Installera automatiskt och starta om enligt schema****Obs!** Om det här alternativet har valts kan du också konfigurera följande inställningar: **Meddela inte slutanvändare** och **Definiera installationsdag för schemalagda uppdateringar**.<br>(endast Windows 10 Desktop)|
|**Tillåt förhandsfunktioner**|Låter Microsoft distribuera förhandsversionsinställningar och -funktioner till Windows 10-enheter. Du kan välja att tillåta att endast inställningar eller alla förhandsversionsinställningar och -funktioner installeras.|

## Anpassade principinställningar
Använd Microsoft Intunes **anpassade konfigurationsprincip** för Windows 10 och Windows 10 Mobile om du vill distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på Windows 10- och Windows 10 Mobile-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Med den här funktionen kan du distribuera Windows 10-inställningar som inte kan konfigureras med en allmän Intune-konfigurationsprincip.



### Allmänna inställningar för anpassade principer

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för principen som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en lämplig beskrivning av principen och annan information som gör det enkelt att hitta den.|

### Anpassad princip för OMA-URI-inställningar

|Inställningsnamn|Information|
    |--------|--------------------|
    |**Inställningsnamn**|Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.|
    |**Beskrivning av inställning**|Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.|
    |**Datatyp**|Ange den datumtyp med vilken du vill specificera den här OMA-URI-inställningen. Välj mellan:<br /><br />-   **Sträng**<br />-   **Sträng (XML)**<br />-   **Datum och tid**<br />-   **Heltal**<br />-   **Flyttal**<br />-   **Boolesk**|
    |**OMA-URI (skiftlägeskänslig)**|Ange den OMA-URI som du vill tillhandahålla en inställning för.|
    |**Värde**|Ange det värde som ska associeras med den OMA-URI som du tidigare angav.|


## URI kundinställningar för Windows 10 enheter
Det här avsnittet innehåller de inställningar som du kan konfigurera för Windows 10- och Windows 10 Mobile-enheter i en **anpassad Microsoft Intune-princip för Windows 10**.

Alla enheter måste vara registrerade med Intune om du vill använda principen för anpassad URI för Windows.

### URI-inställningar för principen

|Principnamn|Information|
|---------------|------------|-----------|
|**​Tillåt automatiskt uppdatering**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** - **5** (standard: **1**)|
|**Schema installationsdag**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Varje dag (standard)<br>**1** – Söndag<br>**2** – Måndag<br>**3** – Tisdag<br>**4** – Onsdag<br>**5** – Torsdag<br>**6** – Fredag<br>**7** – Lördag|
|**Schema installationstid**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0**–**23** timmar (**0** är midnatt) (standard: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – användaren har inte möjlighet att ställa in respittiden för lösenordet, och värdet ställs in som ”varje gång”<br>**1** – användaren kan ställa in respittiden för lösenordet (standard)|
|**WiFi/AllowWiFi**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – **Tillåt inte Wi-Fi-anslutning**.<br>**1** –**Tillåt användning av Wi-Fi-anslutning** (standard)|
|**WiFi/AllowInternetSharing**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Tillåt inte internet delning.<br>**1** – Tillåt internetdelning (standard)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**WiFi/AllowManualWiFiConfiguration**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Ingen Wi-Fi-anslutning utanför etablerad MDM är tillåtet.<br>**1** – Att lägga till nya SSID:er för nätverket utöver de som MDM redan har tillhandahållit tillåts (standard)|
|**System/AllowLocation**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**System/AllowTelemetry**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Inte tillåten (endast Enterprise inställningar)<br>**1** – Begränsad<br>**2** – Fullständig (standard)<br>**3** – Fullständig information och diagnostikinformation|
|**System/AllowExperimentation**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Inte tillåten<br>**1** – Endast inställningar (standard)<br>**2** – Inställningar och experiment|
|**Security/AntiTheftMode**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Tillåt inte antistöldläge<br>**1** Användarpreferenser (standard)|
|**Connectivity/AllowUSBConnection**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**System/AllowUserToResetPhone**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Connectivity/AllowCellularDataRoaming**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Connectivity/AllowVPNOverCellular**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – VPN är inte tillåtet över mobilnät<br>**1** – VPN kan använda alla anslutningar inklusive mobil anslutning (standard)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Connectivity/AllowBluetooth**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Tillåt inte att användaren aktiverar Bluetooth.<br>**1** – Reserverad. Användaren kan aktivera och konfigurera Bluetooth (stöds inte i Windows Phone 8.1 för MDM, EAS, Windows 10 Desktop eller Windows 10 Mobile)<br>**2** – Tillåts. Användaren kan aktivera och konfigurera Bluetooth (standard)|
|**Experience/AllowScreenCapture**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Experience/AllowTaskSwitcher**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Experience/AllowVoiceRecording**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Experience/AllowSyncMySettings**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – tillåt inte roaming<br>**1** – Tillåt roaming (standard)|
|**Experience/AllowManualMDMUnenrollment**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Accounts/AllowMicrosoftAccountConnection**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Security/AllowManualRootCertificateInstallation**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Security/AllowAddProvisioningPackages**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Search/DisableBackoff**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** (standard)<br>**1**|
|**Search/PreventRemoteQueries**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0**<br>**1** (standard)|
|**Search/AllowUsingDiacritics**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br> **0** (standard)<br>**1**|
|**Search/AlwaysUseAutoLangDetection**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** (standard)<br>**1**|
|**Search/DisableRemovableDriveIndexing**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** (standard)<br>**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0**<br>**1** (standard)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** (standard)<br>**1**|
|**Security/AllowRemoveProvisioningPackage**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Security/RequireProvisioningPackageSignature**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** (standard)<br>**1**|
|**AboveLock/AllowActionCenterNotifications**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**TextInput/AllowIMENetworkAccess**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – tillåt inte<br>Öppen utökad ordbok är avstängd.<br>En användare kan inte:<br>Lägga till en ny utökad ordbok<br /><br />Lägga till en ny sökningsintegrerad konfigurationsfil<br>Använd molnkandidats funktionen<br>Skicka användare registrerat ord<br>Dessutom:<br>Ett öppen utökad ordbok som lades till innan du aktiverade den här principinställningen används inte för konvertering.<br>En integrerad sökningskonfigurationsfil som installerades innan du aktiverade den här principinställningen används inte.<br>**1** – Tillåt<br>Öppen utökad ordbok kan läggas till och användas som standard. Dessutom kan integrationsfunktionssökningen användas som standard.<br>En användare kan:<br>Använd molnkandidats funktionen<br>Skicka användarregistrerat ord.|
|**TextInput/AllowIMELogging**<br>(endast stationär dator)|**URI sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Loggning av felkonverteringar är inaktiverat. Auto-tuned uppgifter och inmatade historikdatauppgifter sparas inte till en fil.<br>**1** – Loggning av felkonverteringar är aktiverat. Automatiskt justerade datauppgifter och inmatade historikdatauppgifter sparas i en fil (standard)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**TextInput/AllowJapaneseIVSCharacters**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**TextInput/AllowJapaneseUserDictionary**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Inga tecken filtreras (standard)<br>**1** – Alla tecken utom JIS-skifttecken filtreras|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Inga tecken filtreras (standard)<br>**1** – Alla tecken utom JIS0208-tecken filtreras|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Inga tecken filtreras (standard)<br>**1** – Alla tecken utom JIS0208-tecken och EUDC-tecken filtreras|
|**TextInput/AllowInputPanel**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Bluetooth/AllowDiscoverableMode**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Bluetooth/AllowAdvertising**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowDataSense**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowVPN**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowWorkplace**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowDateTime**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowLanguage**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowRegion**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowSignInOptions**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowYourAccount**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowPowerSleep**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Settings/AllowAutoPlay**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Experience/AllowCortana**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Search/SafeSearchPermissions**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Strikt, högsta filtrering mot vuxet innehåll<br>**1** – Måttlig, måttlig filtrering mot vuxet innehåll (giltiga sökresultat filtreras inte – standard)|
|**Experience/AllowCopyPaste**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**Forcerad startstorlek**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – tillåt användaren att ändra storlek (standard)<br>**1** – Framtvinga skärm som inte är helskärm<br>**2** – Framtvinga helskärm|
|**Update/RequireDeferUpgrade**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0**: skjut inte upp uppgradering (stanna i aktuell gren, CB – standard)<br>**1**: Aktivera uppdateringar och uppgraderingar som ska skjutas upp (enheten följer aktuell företagsgren, CBB, regler)<br /><br />Mer information finns i:<br>[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>(stationär dator och mobil)|**Beskrivning:** Princip för att skjuta upp programuppdateringar i upp till fyra veckor<br /><br />**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br> **0**: Tillämpa uppdateringar direkt (standard)<br>**1**-**4**: antal veckor som programvaruuppdateringarna ska skjutas upp.<br /><br />Mer information finns i:<br>[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>(stationär dator och mobil)|**Beskrivning:** Princip för att skjuta upp funktionsuppgraderingar i upp till åtta månader<br /><br />**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0**: Tillämpa uppdateringar direkt (standard)<br>**1**-**8**: antal månader som funktionsuppgraderingar ska skjutas upp.<br /><br />Mer information finns i:<br>[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>(stationär dator och mobil)|**Beskrivning:** Tillåter att en CBB-dator slutar få uppdateringar och uppgraderingar i fem veckor. Ska användas om det är problem med en uppdatering.<br /><br />**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0**: Tillämpa uppdateringar direkt (standard)<br>**1**: Pausa uppdateringar och uppgraderingar (upphör att gälla efter 5 veckor)|

### Inställningar för Windows Defender-URI

|Principnamn|Information|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**AllowBehaviorMonitoring**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**AllowIntrusionPreventionSystem**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**AllowIOAVProtection**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**AllowScriptScanning**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**AllowOnAccessProtection**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**RealTimeScanDirection**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Övervaka alla filer (dubbelriktat – standard)<br>**1** – Övervaka inkommande filer<br>**2** – Övervaka utgående filer|
|**DaysToRetainCleanedMalware**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** - **90** – Visar hur länge skadlig programvara kommer att hållas kvar<br>**Standardvärde:** **0** – Behålls i karantänmappen för alltid och tas inte bort automatiskt|
|**AllowUserUIAccess**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**ScanParameter**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**1** – Snabbsökning (standard)<br>**2** – Full scanning|
|**ScheduleScanDay**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Varje dag (standard)<br>**1** – Måndag<br>**2** – Tisdag<br>**3** – Onsdag<br>**4** – Torsdag<br>**5** – Fredag<br>**6** – Lördag<br>**7** – Söndag<br>**8** – Ingen schemalagd scanning|
|**ScheduleScanTime**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – 12:00 am<br>**60** – 1:00 am<br>**120** – 02:00 (standard)<br>**180** – 3:00 am<br>**240** – 4:00 am<br>**300** – 5:00 am<br>**360** – 6:00 am<br>**420** – 7:00 am<br>**480** – 8:00 am<br>**540** – 9:00 am<br>**600** – 10:00 am<br>**660** – 11:00 am<br>**720** – 12:00 pm<br>**780** – 1:00 pm<br>**840** – 2:00 pm<br>**900** – 3:00 pm<br>**960** – 4:00 pm<br>**1020** – 5:00 pm<br>**1080** – 6:00 pm<br>**1140** – 7:00 pm<br>**1200** – 8:00 pm<br>**1260** – 9:00 pm<br>**1320** – 10:00 pm<br>**1381** – Underhållsfönster|
|**ScheduleQuickScanTime**<br>(endast stationär dator)|**URI full path:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br>**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – 12:00 am<br>**60** – 1:00 am<br>**120** – 02:00 (standard)<br>**180** – 3:00 am<br>**240** – 4:00 am<br>**300** – 5:00 am<br>**360** – 6:00 am<br>**420** – 7:00 am<br>**480** – 8:00 am<br>**540** – 9:00 am<br>**600** – 10:00 am<br>**660** – 11:00 am<br>**720** – 12:00 pm<br>**780** – 1:00 pm<br>**840** – 2:00 pm<br>**900** – 3:00 pm<br>**960** – 4:00 pm<br>**1020** – 5:00 pm<br>**1080** – 6:00 pm<br>**1140** – 7:00 pm<br>**1200** – 8:00 pm<br>**1260** – 9:00 pm<br>**1320** – 10:00 pm<br>**1380** – 11:00 pm|
|**AVGCPULoadFactor**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** - **100** (standard: **50**)|
|**AllowArchiveScanning**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**AllowEmailScanning**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**Datatyp:** heltal<br>**Tillåtna värden:**<br>**0** – ej tillåten (standard)<br>**1** – tillåten|
|**AllowFullScanRemovableDriveScanning**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – ej tillåten (standard)<br>**1** – tillåten|
|**AllowFullScanOnMappedNetworkDrives**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**AllowScanningNetworkFiles**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåten (standard) – Körs även när RTP är aktiverad när den är inställd på tillåten|
|**SignatureUpdateInterval**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Kontrollera inte signaturer på en intervall<br>**1** – Kontrollera om signaturer finns varje timme<br>**2** – Kontrollera om signaturer finns varannan timme<br>**24** – Kontrollera om signaturer finns varje dag<br>**Standardvärde:** 8 – Sök efter signaturer var 8:e timme|
|**AllowCloudProtection**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – inte tillåten<br>**1** – tillåtet (standard)|
|**SubmitSamplesConsent**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Fråga alltid (default)<br>**1** – Skicka säkra prover automatiskt<br>**2** – Skicka aldrig<br>**3** – Skicka alla prover automatiskt|
|**ExcludedExtensions**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**Datatyp:** Sträng<br /><br />**Tillåtna värden:**<br>*&lt;lista över tillägg avgränsade med semikolon&gt;* Exempel: **obj;lib**<br>**Standard:** Inga tillägg utesluts|
|**ExcludedPaths**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**Datatyp:** Sträng<br /><br />**Tillåtna värden:**<br /><br />*&lt;lista över sökvägar avgränsade med semikolon&gt;*<br /><br />Exempel: **c:\test;c:\test1.exe**<br /><br />**Standardvärde:** Inga sökvägar utesluts|
|**ExcludedProcesses**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**Datatyp:** Sträng<br /><br />**Tillåtna värden:**<br>*&lt;lista över sökvägar avgränsade med semikolon&gt;*<br>Exempel: **c:\test.exe;c:\test1.exe**<br>**Standardvärde:** Inga processer utesluts|

### URI-inställningar för Microsoft Edge-webbläsare

|Principnamn|Information|
|---------------|------------|-----------|
|**Tillåt webbläsare**<br>(endast mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0**: navigering inaktiverat<br>**1**: navigering aktiverat (standard)|
|**AllowSearchSuggestionsinAddressBar**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0**: Visa inte sökförslag<br>**1**: Visa sökförslag (standard)|
|**SendIntranetTraffictoInternetExplorer**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0**: Inaktiverad (öppna intranätsplatser i Microsoft Edge-webbläsare – standard)<br>**1** – Aktiverad (öppna intranätsplatser i Internet Explorer).|
|**Tillåt Do Not Track**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Inaktiverad (DNT skickas inte – standard)<br>**1** – Aktiverad (skicka DNT)|
|**Konfigurera SmartScreen**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Tillåt inte<br>**1** – Tillåt (standard)|
|**Tillåt popup-fönster**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Blockera popup-fönster (standard)<br>**1** – Tillåt popup-fönster|
|**Tillåt cookies**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Blockera inte. Tillåt cookies från alla webbplatser (standard)<br>**1** – Blockera endast cookies från tredje part<br>**2** – Blockera alla cookies|
|**Tillåt att spara lösenord**<br>(stationär dator och mobil)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Lösenordshanteraren är inaktiverad; <br>**1** – Lösenordshanteraren är aktiverad (standard)|
|**Tillåt autofyll**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br>**0** – Inaktiverad (standard)<br>**1** – Aktiverad|
|**Konfigurera företagswebbplatslista**<br>(endast stationär dator)|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**Datatyp:** Sträng<br /><br />**Tillåtna värden:<br>0** – Inte konfigurerat<br>**1** – Använd Internet Explorers webbplatslista för företagsläge om den är konfigurerad (standard)<br>**2** – Ange plats för företagswebbplatslista|

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Aug16_HO1-->


