---
# required metadata

title: Principinställningar för Windows 10 i Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Principinställningar för Windows 10 i Microsoft Intune

Använd principinställningarna som anges i det här avsnittet om du vill konfigurera inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter.

## Generella inställningar för konfigurationsprinciper

Använd **den allmänna konfigurationsprincipen** för Windows 10 om du vill konfigurera allmänna inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter:


### Lösenord

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Kräv ett lösenord för att låsa upp enheter**|Kräv ett lösenord på enheter som stöds.|Ja|Ja|
|**Lösenordstyp krävs**|Anger vilken typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt|Ja|Ja|
|**Krav på lösenordstyp** - **Minsta antal teckenuppsättningar**|Det finns fyra teckenuppsättningar: gemena bokstäver, versala bokstäver, siffror och symboler. Den här inställningen anger hur många olika teckenuppsättningar som lösenordet måste innehålla.|Ja|Ja|
|**Minsta längd på lösenord**|Anger det minsta antalet tecken som enhetens lösenord måste innehålla.|Nej|Ja|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Rensar enheten om detta antal inloggningsförsök misslyckas.|Ja|Ja|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Anger hur lång tid en enhet måste vara inaktiv innan skärmen låses.|Ja|Ja|
|**Lösenordets giltighetstid (i dagar)**|Anger efter hur lång tid enhetens lösenord måste ändras.|Ja|Ja|
|**Kom ihåg tidigare lösenord**|Anger om du vill hindra användaren från att återanvända tidigare lösenord.|Ja|Ja|
|**Spara lösenordshistorik** - **Förhindra återanvändning av tidigare lösenord **|Anger hur många tidigare använda lösenord som sparas av enheten.|Ja|Ja|
|**Tillåt bildlösenord och PIN**|Låter dig använda enkla gester på en bild eller en enkel PIN-kod för inloggning.|Ja|Nej|
|**Kräv lösenord när enheten återgår från viloläge**|Om den här inställningen är aktiverad måste användaren ange ett lösenord för att låsa upp enheten från inaktivt läge.|Nej|Ja|

### Kryptering

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Filkryptering på mobil enhet**|Aktiverar kryptering på målenheter.|Nej|Ja|

### System

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Tillåt skärmbild**|Låter användaren fånga enhetens skärm som en bild.|Nej|Ja|
|**Tillåt manuell avregistrering**|Tillåter att användaren manuellt raderar sitt arbetsplatskonto från enheten.|Ja|Ja|
|**Tillåt manuell installation av rotcertifikat**|Anger om användaren kan installera rotcertifikat manuellt|Nej|Ja|
|**Tillåt att diagnostik- och användardata skickas till Microsoft**|Anger mängden diagnostik- och användningsdata som skickas till Microsoft från enheter.<br>**Nej** – Inga data skickas till Microsoft<br>**Grundläggande** – Enheten skickar endast begränsad information till Microsoft<br>**Utökad** – Skickar förbättrade diagnostikdata till Microsoft<br>**Fullständig (rekommenderas)** –Skickar samma data som **Utökad**, plus ytterligare information om enhetens tillstånd|Ja|Ja|


### Konto och synkronisering

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Tillåt Microsoft-konto**|Låter användaren associera ett Microsoft-konto med enheten.|Ja|Ja|
|**Tillåt att lägga till icke-Microsoft konton manuellt**|Låter användaren lägga till e-postkonton till enheten som inte är associerade med ett Microsoft-konto.|Ja|Ja|
|**Tillåt synkronisering av inställningar för Microsoft-konton**|Tillåt att enhets- och appinställningar som associeras med ett Microsoft-konto synkroniseras mellan enheter.|Ja|Ja|

### E-postinställningar

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Gör Microsoft-kontot valfritt i Windows Mail-programmet**|Konfigurera den här inställningen om du vill ta bort kravet på ett Microsoft-konto i Windows Mail.|Ja|Nej|



### Microsoft Edge

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Tillåt webbläsare**|Tillåt användningen av Edge-webbläsaren på enheten.|Nej|Ja|
|**Tillåt sökförslag i adressfältet**|Tillåter att din sökmotor föreslår platser när du skriver sökord.|Ja|Ja|
|**Tillåt att intranättrafik skickas till Internet Explorer**|Tillåter att användarna öppnar intranätsplatser i Internet Explorer.|Ja|Nej|
|**Tillåt spåra inte**|Konfigurerar Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker.|Ja|Ja|
|**Aktivera SmartScreen**|Aktiverar webbläsarinställningen SmartScreen på enheter.|Ja|Ja|
|**Tillåt active scripting**|Tillåter att skript, t.ex. JavaScript, körs i Edge-webbläsaren.|Ja|Ja|
|**Tillåt popup-fönster**|Aktiverar eller inaktiverar webbläsarens blockering av popup-fönster.|Ja|Nej|
|**Tillåt cookies**|Tillåt eller inaktivera cookies.|Ja|Ja|
|**Tillåt autofyll**|Tillåt att användarna ändrar inställningarna för Komplettera automatiskt i webbläsaren.|Ja|Nej|
|**Tillåt lösenordshanteraren**|Aktivera eller inaktivera lösenordshanteraren för Edge.|Ja|Ja|
|**Listplats för Företagsläge-webbplats**|Anger var man hittar listan över webbsidor som öppnar i Enterprise-läge. Användare kan inte redigera den här listan.|Ja|Nej|

### Appar

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Tillåt appbutik**|Tillåt att användaren kommer åt appbutiken på enheten.|Nej|Ja|



### Mobilnät

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Tillåt dataroaming**|Tillåt växling mellan nätverk vid åtkomst till data.|Ja|Ja|
|**Tillåt VPN via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar när den är ansluten till ett mobilnät.|Ja|Ja|
|**Tillåt VPN-roaming via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar vid roaming i ett mobilnät.|Ja|Ja|

### Maskinvara

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Tillåt kamera**|Anger om enhetens kamera kan användas.|Ja|Ja|
|**Tillåt flyttbara lagringsenheter**|Anger om externa lagringsenheter, till exempel ett SD-kort, kan användas med enheten.|Ja|Ja|
|**Tillåt Wi-Fi**|Tillåter användningen av enheternas Wi-Fi-funktion.|Nej|Ja|
|**Tillåt internetdelning**|Tillåt användningen av Internetanslutningsdelning på enheten.|Ja|Ja|
|**Tillåt manuell Wi-Fi konfiguration**|Styr huruvida användarna kan konfigurera egna trådlösa anslutningar eller om de endast kan använda anslutningar som konfigurerats med en Wi-Fi-profil.|Nej|Ja|
|**Tillåt automatisk anslutning till kostnadsfria, trådlösa surfpunkter**|Tillåter att enheten ansluter automatiskt till kostnadsfria trådlösa surfzoner och att den godkänner eventuella villkor för anslutningen automatiskt.|Ja|Ja|
|**Tillåt geolokalisering**|Anger om enheten kan använda tjänsterna för platsinformation.|Ja|Ja|
|**Tillåt NFC**|Tillåter att enheten använder funktioner för närfältskommunikation.|Ja|Ja|
|**Tillåt Bluetooth**|Tillåter användningen av Bluetooth-funktioner på enheten.|Ja|Ja|
|**Tillåt att Bluetooth kan hittas**|Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.|Ja|Ja|
|**Tillåt Bluetoothreklam**|Tillåter att enheter tar emot reklam via Bluetooth.|Ja|Ja|
|**Tillåt läge för anslutningsbart Bluetooth** **Viktigt!** |Den här inställningen stöds inte längre i Windows 10 och kommer att tas bort i framtiden.|Ja|Ja|
|**Tillåt telefonåterställning**|Styr huruvida användaren kan fabriksåterställa enheten.|Ja|Ja|
|**Tillåt USB-anslutning**|Styr huruvida enheter kan komma åt externa lagringsenheter via en USB-anslutning.|Ja|Ja|
|**Tillåt AntiTheft läge**|Konfigurera om Windows Antitheft läge är aktiverat.|Ja|Ja|

### Funktioner

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|----------------------|---------------------|
|**Tillåt kopiera och klistra in**|Aktivera eller inaktivera användningen av Kopiera och Klistra in på enheten.|Nej|Ja|
|**Tillåt röstinspelning**|Aktivera eller inaktivera röstinspelningsfunktionerna på enheten.|Nej|Ja|
|**Tillåt Cortana**|Aktivera eller inaktivera röstassistenten Cortana.|Ja|Ja|
|**Tillåt action center meddelanden**|Aktivera eller inaktivera aviseringar från Åtgärdscenter på enhetens låsskärm.|Nej|Ja|

### Defender

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|-|-|
|**Tillåt realtidsövervakning**|Tillåter genomsökning i realtid efter skadlig programvara, spionprogram och annan oönskad programvara.|Ja|Nej|
|**Tillåt beteendeövervakning**|Tillåter att Defender söker efter kända mönster på misstänkt aktivitet på enheter.|Ja|Nej
|**Aktivera system för nätverksinspektion**|Kontrollsystemet för nätverk (NIS) hjälper till att skydda enheter mot nätverksbaserade kryphål genom att använda signaturerna för kända säkerhetsrisker från Microsoft Endpoint Protection Center för att identifiera och blockera skadlig trafik.|Ja|Nej
|**Skanna alla hämtningar**|Kontrollerar om Defender söker igenom alla filer som hämtas från Internet.|Ja|Nej
|**Tillåt skriptgenomsökning**|Tillåter att Defender genomsöker skript som används i Internet Explorer.|Ja|Nej
|**Övervaka fil- och programaktivitet**|Aktivera den här inställningen om du vill att Defender ska övervaka fil- och programaktivitet på enheter.|Ja|Nej
|**Dagar som löst skadlig kod ska spåras**|Tillåter att Defender fortsätter spåra åtgärdad skadlig kod det antal dagar som du anger så att du kan kontrollera tidigare berörda enheter manuellt. Om du ställer in antalet dagar till **0** finns skadlig kod kvar i karantänmappen och tas inte bort automatiskt. |Ja|Nej
|**Tillåt användargränssnittåtkomst för klient**|Styr huruvida Windows Defender-användargränssnittet är dolt från slutanvändarna.<br>Om den här inställningen ändras börjar den gälla nästa gång slutanvändarens dator startas om.|Ja|Nej
|**Schemalägg en snabb daglig genomgång**|Tillåter att du schemalägger en snabbgenomsökning som körs varje dag vid den tidpunkt som du väljer.|Ja|Nej
|**Schemalägg en systemsökning**|Tillåter att du schemalägger en fullständig sökning eller en snabbsökning som körs regelbundet på den dag och vid den tidpunkt som du väljer.|Ja|Nej
|**Begränsa CPU-användning under en skanning**|Tillåter att du begränsar hur mycket processorkraft som genomsökningarna får använda (från **1** till **100**)|Ja|Nej
|**Skanna arkivfiler**|Tillåter att Defender söker igenom arkiverade filer, till exempel ZIP- eller CAB-filer.|Ja|Nej
|**Skanna e-postmeddelanden**|Tillåter att Defender söker igenom e-postmeddelanden när de tas emot på enheten.|Ja|Nej
|**Skanna flyttbara enheter**|Tillåter att Defender söker igenom flyttbara enheter, t.ex. USB-minnen.|Ja|Nej
|**Skanna mappade nätverksenheter**|Tillåter att Defender söker igenom filer på mappade nätverksenheter.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|Ja|Nej
|**Skanna filer som har öppnats från delade nätverksmappar**|Tillåter att Defender söker igenom filer på delade nätverksenheter, till exempel de som nås från en UNC-sökväg.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|Ja|Nej
|**Intervall för signaturuppdatering**|Ange med vilket intervall som Defender ska söka efter nya signaturfiler.|Ja|Nej
|**Tillåt molnskydd**|Tillåt eller förhindra att Microsoft Active Protection Service tar emot information om skadlig kod från enheter som du hanterar. Den här informationen används för att förbättra tjänsten i framtiden.|Ja|Nej
|**Be användarna att skicka exempel**|Styr huruvida filer som kan kräva ytterligare analys av Microsoft för att avgöra om de är skadliga ska skickas automatiskt till Microsoft.|Ja|Nej
|**Filer och mappar som ska undantas när du kör en skanning eller använder realtidsskydd**|Lägg till en eller flera filer och mappar som **C:\Sökväg** eller **%ProgramFiles%\Sökväg\filnamn.exe** i undantagslistan. Dessa filer och mappar tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|Ja|Nej
|**Filändelser som ska undantas när du kör en skanning eller använder realtidsskydd**|Lägg till ett eller flera filnamnstillägg som **jpg** eller **txt** i undantagslistan. Filer med dessa filnamnstillägg tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|Ja|Nej
|**Processer som ska undantas när du kör en skanning eller använder realtidsskydd**|Lägg till en eller flera processer av typen **.exe**, **.com** eller **.scr** i undantagslistan. De här processerna tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|Ja|Nej| 


### Inställningar för uppdateringar

|Inställningsnamn|Information|Windows 10 Desktop|Windows 10 Mobil|
|----------------|---------------|----------------------|---------------------|
|**Tillåt automatiska uppdateringar**|Aktivera den här inställningen för att tillåta automatiska uppdateringar. Konfigurera sedan någon av följande inställningar för att kontrollera uppdateringsbeteende:<br /><br />**Meddela om hämtning**<br /><br />**Automatisk installation vid underhållstidpunkt**<br /><br />**Automatisk installation och omstart vid underhållstidpunkt**<br /><br />**Installera automatiskt och starta om enligt schema** **Obs!** Om det här alternativet har valts kan du också konfigurera följande inställningar: **Meddela inte slutanvändare** och **Definiera installationsdag för schemalagda uppdateringar**.|Ja|Nej|

## Anpassade principinställningar
Använd Microsoft Intunes **anpassade konfigurationsprincip** för Windows 10 och Windows 10 Mobile om du vill distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på Windows 10- och Windows 10 Mobile-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Med den här funktionen kan du distribuera Windows 10-inställningar som inte kan konfigureras med en allmän Intune-konfigurationsprincip. Information om vilka inställningar som du kan konfigurera med dessa principer finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

En lista över OMA-URI-inställningar som du kan konfigurera på registrerade Windows 10-enheter finns i Anpassade URI-inställningar för Windows 10-enheter senare i det här avsnittet.

### Allmänna inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för principen som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en lämplig beskrivning av principen och annan information som gör det enkelt att hitta den.|

### OMA-URI-inställningar

|Inställningsnamn|Information|
    |--------|--------------------|
    |**Inställningsnamn**|Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.|
    |**Beskrivning av inställning**|Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.|
    |**Datatyp**|Ange den datumtyp med vilken du vill specificera den här OMA-URI-inställningen. Välj mellan:<br /><br />-   **Sträng**<br />-   **Sträng (XML)**<br />-   **Datum och tid**<br />-   **Heltal**<br />-   **Flyttal**<br />-   **Boolesk**|
    |**OMA-URI (skiftlägeskänslig)**|Ange den OMA-URI som du vill tillhandahålla en inställning för.|
    |**Värde**|Ange det värde som ska associeras med den OMA-URI som du tidigare angav.|


## URI kundinställningar för Windows 10 enheter
Det här avsnittet innehåller de inställningar som du kan konfigurera för Windows 10- och Windows 10 Mobile-enheter i en **anpassad Microsoft Intune-princip för Windows 10**..


> [!NOTE]
> I **Supports** kolumnen i tabellen nedan, används följande värden:
> 
> -   **Skrivbord** – Inställningen stöder datorer med Windows 10 Professional och Enterprise som endast är registrerade med Intune.
> -   **Mobil** –Inställningen stöder endast Windows 10 mobilenheter.
> -   **Båda** – Inställningen stöder både stationära och mobila enheter.
> 
> Alla enheter måste vara registrerade med Intune om du vill använda principen för anpassad URI för Windows.

### Princip

|Principnamn|Support|Information|
|---------------|------------|-----------|
|**​Tillåt automatiskt uppdatering**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** - **5**<br /><br />**Standardvärde:** 1|
|**Schema installationsdag**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Varje dag<br /><br />**1** – Söndag<br /><br />**2** – Måndag<br /><br />**3** – Tisdag<br /><br />**4** – Onsdag<br /><br />**5** – Torsdag<br /><br />**6** – Fredag<br /><br />**7** – Lördag<br /><br />**Standardvärde:** 0|
|**Schema installationstid**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0**–**23** timmar (0 är midnatt) <br /><br />**Standardvärde:** 3|
|**DeviceLock/AllowIdleReturnWithoutPassword**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – användaren har inte möjlighet att ställa in respittiden för lösenordet, och värdet ställs in som ”varje gång”<br /><br />**1** – användaren kan ställa in respittiden för lösenordet<br /><br />**Standardvärde:** 1|
|**WiFi/AllowWiFi**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – **Tillåt inte Wi-Fi-anslutning**.<br /><br />**1** – **Tillåt Wi-Fi anslutning**.<br /><br />**Standardvärde:** 1|
|**WiFi/AllowInternetSharing**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Tillåt inte internet delning.<br /><br />**1** – Tillåt internet delning.<br /><br />**Standardvärde:** 1|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**WiFi/AllowManualWiFiConfiguration**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Ingen Wi-Fi-anslutning utanför etablerad MDM är tillåtet.<br /><br />**1** – Lägger till nya nätverks SSIDs efter de MDM som redan tillhandahållits när detta tillåts.<br /><br />**Standardvärde:** 1|
|**System/AllowLocation**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**System/AllowTelemetry**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Inte tillåten (endast Enterprise inställningar)<br /><br />**1** – Begränsad<br /><br />**2** – Full<br /><br />**3** – Fullständig information och diagnostikinformation<br /><br />**Standardvärde:** 2|
|**System/AllowExperimentation**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Inte tillåten<br /><br />**1**– Endast inställningar<br /><br />**2** – Inställningar och experiment<br /><br />**Standardvärde:** 1|
|**Security/AntiTheftMode**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Tillåt inte antistöldläge<br /><br />**1** Användarpreferenser<br /><br />**Standardvärde:** 1|
|**Connectivity/AllowUSBConnection**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**System/AllowUserToResetPhone**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Connectivity/AllowCellularDataRoaming**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Connectivity/AllowVPNOverCellular**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – VPN är inte tillåtet över mobilnät<br /><br />**1** – VPN kunde använda vilken som helst anslutning som ingår i cellen.<br /><br />**Standardvärde:** 1|
|**Connectivity/AllowVPNRoamingOverCellular**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Connectivity/AllowVPNRoamingOverCellular**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Connectivity/AllowBluetooth**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Tillåt inte att användaren aktiverar Bluetooth.<br /><br />**1** – Reserverad. Användaren kan aktivera och konfigurera Bluetooth (stöds inte i Windows Phone 8.1 för MDM, EAS, Windows 10 Desktop eller Windows 10 Mobile)<br /><br />**2** – Tillåts. Användaren kan aktivera och konfigurera Bluetooth.<br /><br />**Standardvärde:** 2|
|**Experience/AllowScreenCapture**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Experience/AllowTaskSwitcher**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Experience/AllowVoiceRecording**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Experience/AllowSyncMySettings**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – tillåt inte roaming<br /><br />**1** – tillåt roaming<br /><br />**Standardvärde:** 1|
|**Experience/AllowManualMDMUnenrollment**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Accounts/AllowMicrosoftAccountConnection**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Security/AllowManualRootCertificateInstallation**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Security/AllowAddProvisioningPackages**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Search/DisableBackoff**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**<br /><br />**1**<br /><br />**Standardvärde:** 0|
|**Search/PreventRemoteQueries**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**<br /><br />**1**<br /><br />**Standardvärde:** 1|
|**Search/AllowUsingDiacritics**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**<br /><br />**1**<br /><br />**Standardvärde:** 0|
|**Search/AlwaysUseAutoLangDetection**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**<br /><br />**1**<br /><br />**Standardvärde:** 0|
|**Search/DisableRemovableDriveIndexing**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**<br /><br />**1**<br /><br />**Standardvärde:** 0|
|**Search/PreventIndexingLowDiskSpaceMB**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**<br /><br />**1**<br /><br />**Standardvärde:** 1|
|**Search/AllowIndexingEncryptedStoresOrItems**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**<br /><br />**1**<br /><br />**Standardvärde:** 0|
|**Security/AllowRemoveProvisioningPackage**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Security/RequireProvisioningPackageSignature**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**<br /><br />**1**<br /><br />**Standardvärde:** 0|
|**AboveLock/AllowActionCenterNotifications**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**TextInput/AllowIMENetworkAccess**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – tillåt inte<br /><br />Öppen utökad ordbok är avstängd.<br /><br />En användare kan inte:<br /><br />Lägga till en ny utökad ordbok<br /><br />Lägga till en ny sökningsintegrerad konfigurationsfil<br /><br />Använd molnkandidats funktionen<br /><br />Skicka användare registrerat ord<br /><br />Dessutom:<br /><br />Ett öppen utökad ordbok som lades till innan du aktiverade den här principinställningen används inte för konvertering.<br /><br />En integrerad sökningskonfigurationsfil som installerades innan du aktiverade den här principinställningen används inte.<br /><br />**1** – Tillåt<br /><br />Öppen utökad ordbok kan läggas till och användas som standard. Dessutom kan integrationsfunktionssökningen användas som standard.<br /><br />En användare kan:<br /><br />Använd molnkandidats funktionen<br /><br />Skicka användare registrerat ord<br /><br />**Standardvärde:**|
|**TextInput/AllowKoreanExtendedHanja**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowKoreanExtendedHanja<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**TextInput/AllowIMELogging**|skrivbords-|**URI sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Loggning av felkonverteringar är inaktiverat. Auto-tuned uppgifter och inmatade historikdatauppgifter sparas inte till en fil.<br /><br />**1** – Loggning av felkonverteringar är aktiverat. Automatiskt justerade datauppgifter och inmatade historikdatauppgifter sparas inte till en fil.<br /><br />**Standardvärde:** 1|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**TextInput/AllowJapaneseIVSCharacters**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**TextInput/AllowJapaneseUserDictionary**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Alla tecken utom JIS-tecken filtreras<br /><br />**1** – Tecken filtreras inte<br /><br />**Standardvärde:** 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Alla tecken utom JIS0208-tecken filtreras<br /><br />**1** – Tecken filtreras inte<br /><br />**Standardvärde:** 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Alla tecken utom JIS0208-tecken och EUDC-tecken filtreras<br /><br />**1** – Inga tecken filtreras.<br /><br />**Standardvärde:** 1|
|**TextInput/AllowInputPanel**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Bluetooth/AllowDiscoverableMode**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Bluetooth/AllowAdvertising**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowDataSense**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowVPN**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowWorkplace**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowDateTime**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowLanguage**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowRegion**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowSignInOptions**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowYourAccount**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowPowerSleep**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Settings/AllowAutoPlay**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Experience/AllowCortana**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Search/SafeSearchPermissions**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Strikt, högsta filtrering mot vuxet innehåll<br /><br />**1** – Måttlig, måttlig filtrering mot vuxet innehåll (giltiga sökresultat kommer inte att filtreras)<br /><br />**Standardvärde:** 1|
|**Experience/AllowCopyPaste**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**Forcerad startstorlek**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Tillåt användaren att ändra storlek<br /><br />**1** – Framtvinga skärm som inte är helskärm<br /><br />**2** – Framtvinga helskärm<br /><br />**Standardvärde:** 0|
|**Update/RequireDeferUpgrade**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**: Skjut inte upp uppgradering (stanna i aktuell gren, CB)<br /><br />**1**: Aktivera uppdateringar och uppgraderingar som ska skjutas upp (enheten följer aktuell företagsgren, CBB, regler)<br /><br />**Standardvärde: 0**<br /><br />Mer information finns i:<br /><br />[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/DeferUpdatePeriod**|Båda|**Beskrivning:** Princip för att skjuta upp programuppdateringar i upp till fyra veckor<br /><br />**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:** 0: Tillämpa uppdateringar direkt; 1–4: antalet veckor som programuppdateringar ska skjutas upp.<br /><br />**Standardvärde: 0**<br /><br /><br />Mer information finns i:<br /><br />[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/DeferUpgradePeriod**|Båda|**Beskrivning:** Princip för att skjuta upp funktionsuppgraderingar i upp till åtta månader<br /><br />**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:** 0: Tillämpa uppdateringar direkt; 1–8: antalet månader som funktionsuppgraderingar ska skjutas upp.<br /><br />**Standardvärde: 0**<br /><br />Mer information finns i:<br /><br />[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/PauseDeferrals**|Båda|**Beskrivning:** Tillåter att en CBB-dator slutar få uppdateringar och uppgraderingar i fem veckor. Ska användas om det är problem med en uppdatering.<br /><br />**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0**: Tillämpa uppdateringar direkt (standard)<br /><br />**1**: Pausa uppdateringar och uppgraderingar (upphör att gälla efter 5 veckor)<br /><br />**Standardvärde: 0**|

### Windows försvarare

|Principnamn|Support|Information|
|---------------|------------|-----------|
|**AllowRealtimeMonitoring**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**AllowBehaviorMonitoring**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**AllowIntrusionPreventionSystem**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**AllowIOAVProtection**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**AllowScriptScanning**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**AllowOnAccessProtection**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**RealTimeScanDirection**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Övervaka alla filer (dubbelriktat)<br /><br />**1** – Övervaka inkommande filer<br /><br />**2** – Övervaka utgående filer<br /><br />**Standardvärde:** 0|
|**DaysToRetainCleanedMalware**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** - **90** – Anger hur länge skadlig kod ska behållas<br /><br />**Standardvärde:** 0 – Behålls i karantänmappen för alltid och tas inte bort automatiskt|
|**AllowUserUIAccess**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**ScanParameter**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**1** – Snabb scanning<br /><br />**2** – Full scanning<br /><br />**Standardvärde:** 1|
|**ScheduleScanDay**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Varje dag<br /><br />**1** – Måndag<br /><br />**2** – Tisdag<br /><br />**3** – Onsdag<br /><br />**4** – Torsdag<br /><br />**5** – Fredag<br /><br />**6** – Lördag<br /><br />**7** – Söndag<br /><br />**8** – Ingen schemalagd scanning<br /><br />**Standardvärde:** 0|
|**ScheduleScanTime**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – 12:00 am<br /><br />**60** – 1:00 am<br /><br />**120** – 2:00 am<br /><br />**180** – 3:00 am<br /><br />**240** – 4:00 am<br /><br />**300** – 5:00 am<br /><br />**360** – 6:00 am<br /><br />**420** – 7:00 am<br /><br />**480** – 8:00 am<br /><br />**540** – 9:00 am<br /><br />**600** – 10:00 am<br /><br />**660** – 11:00 am<br /><br />**720** – 12:00 pm<br /><br />**780** – 1:00 pm<br /><br />**840** – 2:00 pm<br /><br />**900** – 3:00 pm<br /><br />**960** – 4:00 pm<br /><br />**1020** – 5:00 pm<br /><br />**1080** – 6:00 pm<br /><br />**1140** – 7:00 pm<br /><br />**1200** – 8:00 pm<br /><br />**1260** – 9:00 pm<br /><br />**1320** – 10:00 pm<br /><br />**1381** – Underhållsfönster<br /><br />**Standardvärde:** 120|
|**ScheduleQuickScanTime**|skrivbords-|**URI full path:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – 12:00 am<br /><br />**60** – 1:00 am<br /><br />**120** – 2:00 am<br /><br />**180** – 3:00 am<br /><br />**240** – 4:00 am<br /><br />**300** – 5:00 am<br /><br />**360** – 6:00 am<br /><br />**420** – 7:00 am<br /><br />**480** – 8:00 am<br /><br />**540** – 9:00 am<br /><br />**600** – 10:00 am<br /><br />**660** – 11:00 am<br /><br />**720** – 12:00 pm<br /><br />**780** – 1:00 pm<br /><br />**840** – 2:00 pm<br /><br />**900** – 3:00 pm<br /><br />**960** – 4:00 pm<br /><br />**1020** – 5:00 pm<br /><br />**1080** – 6:00 pm<br /><br />**1140** – 7:00 pm<br /><br />**1200** – 8:00 pm<br /><br />**1260** – 9:00 pm<br /><br />**1320** – 10:00 pm<br /><br />**1380** – 11:00 pm<br /><br />**Standardvärde:** 120|
|**AVGCPULoadFactor**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** - **100**<br /><br />**Standardvärde:** 50|
|**AllowArchiveScanning**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**AllowEmailScanning**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 0|
|**AllowFullScanRemovableDriveScanning**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 0|
|**AllowFullScanOnMappedNetworkDrives**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**AllowScanningNetworkFiles**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1 – Körs även när RTP är på när den är inställd på tillåten|
|**SignatureUpdateInterval**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Kontrollera inte signaturer på en intervall<br /><br />**1** – Kontrollera om signaturer finns varje timme<br /><br />**2** – Kontrollera om signaturer finns varannan timme<br /><br />**24** – Kontrollera om signaturer finns varje dag<br /><br />**Standardvärde:** 8 – Sök efter signaturer var 8:e timme|
|**AllowCloudProtection**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – inte tillåten<br /><br />**1** – tillåten<br /><br />**Standardvärde:** 1|
|**SubmitSamplesConsent**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden:**<br /><br />**0** – Alltid snabb<br /><br />**1** – Skicka säkra prover automatiskt<br /><br />**2** – Skicka aldrig<br /><br />**3** – Skicka alla prover automatiskt<br /><br />**Standardvärde:** 0|
|**ExcludedExtensions**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**Datatyp:** Sträng<br /><br />**Tillåtna värden:**<br /><br />*&lt;lista över tillägg avgränsade med semikolon&gt;* Exempel: **obj;lib**<br /><br />**Standardvärde:** Inga tillägg utesluts|
|**ExcludedPaths**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**Datatyp:** Sträng<br /><br />**Tillåtna värden:**<br /><br />*&lt;lista över sökvägar avgränsade med semikolon&gt;*<br /><br />Exempel: **c:\test;c:\test1.exe**<br /><br />**Standardvärde:** Inga sökvägar utesluts|
|**ExcludedProcesses**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**Datatyp:** Sträng<br /><br />**Tillåtna värden:**<br /><br />*&lt;lista över sökvägar avgränsade med semikolon&gt;*<br /><br />Exempel: **c:\test.exe;c:\test1.exe**<br /><br />**Standardvärde:** Inga processer utesluts|

### Edge-webbläsare

|Principnamn|Support|Information|
|---------------|------------|-----------|
|**Tillåt webbläsare**|Mobiltelefon|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0**– Bläddring är inaktiverat; **1** – Bläddring är aktiverat.<br /><br />**Standardvärde:** 1|
|**AllowSearchSuggestionsinAddressBar**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0**: Visa inte sökförslag; **1**: Visa sökförslag.<br /><br />**Standardvärde:** 1|
|**SendIntranetTraffictoInternetExplorer**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** – Inaktiverat (öppna intranätplatser i Edge-webbläsaren); **1**– Aktiverat (öppna intranätplatser i Internet Explorer).<br /><br />**Standardvärde:** 0|
|**Tillåt Do Not Track**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** – Inaktiverat (DNT skickas inte); **1** – Aktiverat (DNT skickas)<br /><br />**Standardvärde:** 0|
|**Konfigurera SmartScreen**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** – Tillåt inte;  **1** – Tillåt<br /><br />**Standardvärde:** 1|
|**Tillåt popup-fönster**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** – Blockera popup-fönster; **1** – Tillåt popup-fönster<br /><br />**Standardvärde:** 0|
|**Tillåt cookies**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** – Blockera inte. Tillåt cookies från alla webbplatser; **1** – Blockera endast cookies från tredje part; **2** – Blockera alla cookies<br /><br />**Standardvärde:** 0|
|**Tillåt att spara lösenord**|Båda|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** – Lösenordshanteraren är inaktiverad; <br />                        **1** – Lösenordshanteraren är aktiverad<br /><br />**Standardvärde:** 1|
|**Tillåt autofyll**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**Datatyp:** heltal<br /><br />**Tillåtna värden: 0** – Inaktiverat; **1** – Aktiverat<br /><br />**Standardvärde:** 0|
|**Konfigurera företagswebbplatslista**|skrivbords-|**Fullständig URI-sökväg:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**Datatyp:** Sträng<br /><br />**Tillåtna värden: 0** – Inte konfigurerat; **1** – Använd webbplatslista för företagsläge i IE om konfigurerat; **2** – Ange plats för webbplatslista för företagsläge<br /><br />**Standardvärde:** 1|

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


