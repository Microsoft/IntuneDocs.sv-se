---
title: "Principinställningar för Windows 10"
description: "Använd principinställningarna som anges i det här avsnittet om du vill konfigurera inbyggda och anpassade inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/03/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 85612fc63b3fb738e6135ac71065edc06169fa9e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Intune-principinställningar för Windows 10-enheter i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet innehåller information om de Intune-principinställningar som du kan använda för att hantera Windows 10-enheter. Läs det här avsnittet samt anvisningarna i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](/intune-classic/get-started/windows-pc-management-capabilities-in-microsoft-intune).

Du kan välja mellan två principtyper:

- **Anpassad princip**: Använd Microsoft Intunes **anpassade princip** för Windows 10 och Windows 10 Mobile för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. I Windows 10 är många CSP-inställningar tillgängliga, t.ex. [Princip-CSP (Configuration Service Provider)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Allmän konfigurationspolicy**: Använd den här principtypen om du vill välja inställningar från den inbyggda listan som medföljer Microsoft Intune.

## <a name="custom-policy-settings"></a>Anpassade principinställningar

Ange följande inställningar i en anpassad princip.

### <a name="general-settings"></a>Allmänna inställningar

Ange ett namn, och eventuellt en beskrivning, för principen så att du kan identifiera den i Intune-konsolen.

### <a name="oma-uri-settings"></a>OMA-URI-inställningar

Ange följande information för varje OMA-URI-inställning som du vill lägga till. Läs [URI-inställningar för Windows 10](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) i det här avsnittet om du vill veta mer om vilka inställningar du kan använda:

- **Inställningsnamn**: Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
- **Inställningsbeskrivning**: Ange en beskrivning för inställningen.
- **Datatyp**: Välj från följande datatyper:
    - **Sträng**
    - **Sträng (XML)**
    - **Datum och tid**
    - **Heltal**
    - **Flyttal**
    - **Boolesk**
- **OMA-URI (skiftlägeskänslig)**: Ange den OMA-URI som du vill tillhandahålla en inställning för.
- **Värde**: Ange det värde som ska associeras med den OMA-URI som du har angett.

### <a name="example"></a>Exempel
I följande skärmbild har inställningen **Connectivity/AllowVPNOverCellular** aktiverats. Detta innebär att en Windows 10-enhet öppnar en VPN-anslutning när enheten använder ett mobilnät.

> ![Exempel på en anpassad princip som innehåller VPN-inställningar](./media/custom-policy-example.png)

### <a name="how-to-find-the-policies-you-can-configure"></a>Så här hittar du de principer som du kan konfigurera

Du hittar en lista med alla CSP:er som har stöd för Windows 10 i [Referens till CSP (Configuration Service Provider)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) i dokumentationsbiblioteket för Windows.

Alla inställningar är inte kompatibla med alla versioner av Windows 10. I tabellen i avsnittet om Windows kan du se vilka versioner som stöds för varje CSP.

Dessutom stöder Intune inte alla inställningar som anges i avsnittet. Om du vill veta om Intune har stöd för den inställning som du vill använda, öppnar du avsnittet för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Lägg till** eller **Ersätt**.

## <a name="general-configuration-policy-settings"></a>Generella inställningar för konfigurationsprinciper

Använd den **allmänna konfigurationsprincipen** för Windows Intune för Windows 10 om du vill konfigurera inbyggda inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter.

### <a name="password"></a>Lösenord

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Kräv ett lösenord för att låsa upp enheter**|-|
|**Lösenordstyp krävs**|Anger om lösenordet måste vara alfanumeriskt eller endast numeriskt|
|**Krav på lösenordstyp** - **Minsta antal teckenuppsättningar**| Anger hur många teckenuppsättningar (gemener, versaler, siffror och symboler) som måste ingå i lösenordet|
|**Minsta längd på lösenord**|Gäller endast för Windows 10 Mobile|
|**Antal tillåtna, upprepade felinloggningar innan enheten rensas**.|För enheter som kör Windows 10: Om BitLocker är aktiverat på enheten placeras den i återställningsläget för BitLocker efter den gräns för antal misslyckade inloggningar som du har angett. Om BitLocker inte är aktiverat på enheten tillämpas inte den här inställningen.<br>För enheter som kör Windows 10 Mobile: Om inloggningen misslyckas ett visst antal gånger (som du angett) rensas enheten.|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Anger hur lång tid en enhet måste vara inaktiv innan skärmen låses|
|**Lösenordets giltighetstid (i dagar)**|Anger efter hur lång tid enhetens lösenord måste ändras|
|**Kom ihåg tidigare lösenord**|Anger om du vill förhindra att användaren återanvänder tidigare använda lösenord|
|**Spara lösenordshistorik** - **Förhindra återanvändning av tidigare lösenord** |Anger antalet tidigare använda lösenord som enheten sparar|
|**Kräv lösenord när enheten återgår från viloläge**|Anger att användaren måste ange ett lösenord för att låsa upp enheten (endast Windows 10 Mobile)|

### <a name="encryption"></a>Kryptering

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Filkryptering på mobil enhet**|Aktiverar kryptering på målenheter<br>(endast Windows 10 Mobile)|

### <a name="system"></a>System

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Tillåt skärmbild**|Användaren kan ta en skärmbild av enhetens skärm (endast Windows 10 Mobile)|
|**Tillåt manuell avregistrering**|Tillåter att användaren manuellt raderar sitt arbetsplatskonto från enheten|
|**Tillåt manuell installation av rotcertifikat**|Gäller för Windows 10 Mobile|
|**Tillåt att diagnostik- och användardata skickas till Microsoft**|Möjliga värden är:<br><br>**Nej** – Inga data skickas till Microsoft<br>**Grundläggande** – Begränsad information skickas till Microsoft<br>**Utökad** – Utökade diagnostikdata skickas till Microsoft<br>**Fullständig (rekommenderas)** –Skickar samma data som **Utökad**, plus ytterligare information om enhetens tillstånd|


### <a name="account-and-synchronization"></a>Konto och synkronisering

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt Microsoft-konto**|Låter användaren associera ett Microsoft-konto med enheten|
|**Tillåt att andra konton än Microsoft-konton får läggas till manuellt**|Låter användaren lägga till e-postkonton till enheten som inte är associerade med ett Microsoft-konto|
|**Tillåt synkronisering av inställningar för Microsoft-konton**|Tillåt att enhets- och appinställningar som associeras med ett Microsoft-konto synkroniseras mellan enheter|

### <a name="microsoft-edge"></a>Microsoft Edge

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Tillåt webbläsare**|Tillåter användningen av Microsoft Edge-webbläsaren på enheten<br>(endast Windows 10 Mobile)|
|**Tillåt sökförslag i adressfältet**|Tillåter att din sökmotor föreslår platser när du skriver sökord|
|**Tillåt att intranättrafik skickas till Internet Explorer**|Tillåter att användarna öppnar intranätsplatser i Internet Explorer<br>(endast Windows 10 Desktop)|
|**Tillåt Spåra inte**|Konfigurerar Microsoft Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker|
|**Aktivera SmartScreen**||
|**Tillåt Active scripting**|Tillåter att skript (exempelvis JavaScript) körs i webbläsaren Edge|
|**Tillåt popup-fönster**|Gäller endast för Windows 10 Desktop|
|**Tillåt cookies**||
|**Tillåt autofyll**|Tillåter att användarna kan ändra inställningarna för att automatiskt komplettera i webbläsaren<br>(endast Windows 10 Desktop)|
|**Tillåt lösenordshanteraren**|Aktiverar eller inaktiverar lösenordshanteraren i Microsoft Edge|
|**Listplats för Företagsläge-webbplats**|Anger var du hittar listan över webbsidor som öppnas i Enterprise-läge. Användare kan inte redigera den här listan.<br>(endast Windows 10 Desktop)|

### <a name="apps"></a>Appar

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt appbutik**|Gäller endast för Windows 10 Mobile|



### <a name="cellular"></a>Mobilnät

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåter datanätverksväxling**|Tillåt växling mellan nätverk vid åtkomst till data.|
|**Tillåt VPN via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar när den är ansluten till ett mobilnät.|
|**Tillåt VPN-roaming via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar vid roaming i ett mobilnät.|

### <a name="hardware"></a>Maskinvara

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Tillåt kamera**|-|
|**Tillåt flyttbara lagringsmedier**|Anger om externa lagringsenheter, till exempel ett SD-kort, kan användas med enheten.|
|**Tillåt Wi-Fi**|Gäller endast för Windows 10 Mobile|
|**Tillåt internetdelning**|Tillåter användningen av internetanslutningsdelning på enheten|
|**Tillåt manuell Wi-Fi konfiguration**|Styr huruvida användarna kan konfigurera egna trådlösa anslutningar eller om de endast kan använda anslutningar som konfigurerats med en Wi-Fi-profil.<br>(endast Windows 10 Mobile)|
|**Tillåt automatisk anslutning till kostnadsfria trådlösa surfzoner**|Tillåter att enheten ansluter automatiskt till kostnadsfria trådlösa surfzoner och att den godkänner eventuella villkor för anslutningen automatiskt.|
|**Tillåt geolokalisering**|Anger om enheten kan använda tjänsterna för platsinformation.|
|**Tillåt NFC**|Tillåter att enheten använder funktioner för närfältskommunikation.|
|**Tillåt Bluetooth**|-|
|**Tillåt läge för identifierbart Bluetooth**|Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.|
|**Tillåt Bluetoothreklam**|Tillåter att enheter tar emot meddelanden via Bluetooth.|
|**Tillåt telefonåterställning**|Styr om användaren kan göra en fabriksåterställning på enheten eller inte|
|**Tillåt USB-anslutning**|Styr huruvida enheter kan komma åt externa lagringsenheter via en USB-anslutning.|
|**Tillåt AntiTheft läge**|Ange om stöldskyddsläge i Windows är aktiverat|

### <a name="features"></a>Funktioner

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt kopiera och klistra in**|Gäller endast för Windows 10 Mobile|
|**Tillåt röstinspelning**|Gäller endast för Windows 10 Mobile|
|**Tillåt Cortana**|Aktivera eller inaktivera röstassistenten Cortana.|
|**Tillåt action center meddelanden**|Aktivera eller inaktivera aviseringar från Åtgärdscenter på enhetens låsskärm.<br>(endast Windows 10 Mobile)|

### <a name="windows-defender"></a>Windows försvarare

Alla inställningar gäller endast Windows 10 Desktop.

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt realtidsövervakning**|Tillåter genomsökning i realtid efter skadlig programvara, spionprogram och annan oönskad programvara|
|**Tillåt beteendeövervakning**|Tillåter att Defender söker efter kända mönster på misstänkt aktivitet på enheter|
|**Aktivera kontrollsystem för nätverk**|Kontrollsystemet för nätverk (NIS) hjälper till att skydda enheter mot nätverksbaserade kryphål genom att använda signaturerna för kända säkerhetsrisker från Microsoft Endpoint Protection Center för att identifiera och blockera skadlig trafik|
|**Sök igenom alla hämtningar**|Kontrollerar om Defender söker igenom alla filer som hämtas från Internet|
|**Tillåt skriptgenomsökning**|Tillåter att Defender genomsöker skript som används i Internet Explorer|
|**Övervaka fil- och programaktivitet**|Tillåter att Defender övervakar fil- och programaktivitet på enheter|
|**Dagar som löst skadlig kod ska spåras**|Tillåter att Defender fortsätter spåra åtgärdad skadlig kod det antal dagar som du anger så att du kan kontrollera tidigare berörda enheter manuellt. Om du ställer in antalet dagar till **0** finns skadlig kod kvar i karantänmappen och tas inte bort automatiskt. |
|**Tillåt användargränssnittsåtkomst för klient**|Styr huruvida Windows Defender-användargränssnittet är dolt från användarna.<br>När den här inställningen ändras börjar den gälla nästa gång användarens dator startas om.|
|**Schemalägg daglig snabbsökning**|Tillåter att du schemalägger en snabbgenomsökning som körs varje dag vid den tidpunkt som du väljer|
|**Schemalägg en systemsökning**|Tillåter att du schemalägger en fullständig sökning eller en snabbsökning som körs regelbundet på den dag och vid den tidpunkt som du väljer|
|**Begränsa processoranvändning under en sökning**|Tillåter att du begränsar hur mycket processorkraft som genomsökningarna får använda (från **1** till **100**)|
|**Sök igenom arkivfiler**|Tillåter att Defender söker igenom arkiverade filer, till exempel ZIP- eller CAB-filer.|
|**Sök igenom e-postmeddelanden**|Tillåter att Defender söker igenom e-postmeddelanden när de tas emot på enheten|
|**Sök igenom flyttbara enheter**|Tillåter att Defender söker igenom flyttbara enheter, t.ex. USB-minnen|
|**Sök igenom mappade nätverksenheter**|Tillåter att Defender söker igenom filer på mappade nätverksenheter.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|
|**Sök igenom filer öppnade från delade nätverksmappar**|Tillåter att Defender söker igenom filer på delade nätverksenheter, till exempel de som nås från en UNC-sökväg.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|
|**Intervall för signaturuppdatering**|Ange med vilket intervall som Defender ska söka efter nya signaturfiler.|
|**Tillåt molnskydd**|Tillåt eller förhindra att Microsoft Active Protection Service tar emot information om skadlig kod från enheter som du hanterar. Den här informationen används för att förbättra tjänsten i framtiden.|
|**Be användarna att skicka exempel**|Styr huruvida filer som kan kräva ytterligare analys av Microsoft för att avgöra om de är skadliga ska skickas automatiskt till Microsoft|
|**Identifiering av potentiellt oönskade program**|Skyddar registrerade Windows Desktop-enheter mot aktiv programvara som klassificerats som oönskad av Windows Defender. Du kan skydda dig mot att dessa program körs eller använda granskningsläget för att rapportera att ett potentiellt oönskat program har installerats.|
|**Filer och mappar som ska undantas när en sökning körs eller när realtidsskyddet används**|Lägger till en eller flera filer och mappar som **C:\Sökväg** eller **%ProgramFiles%\Sökväg\filnamn.exe** i undantagslistan. Dessa filer och mappar tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|
|**Filnamnstillägg att undanta när en sökning körs eller när realtidsskyddet används**|Lägg till ett eller flera filnamnstillägg som **jpg** eller **txt** i undantagslistan. Filer med dessa filnamnstillägg tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|
|**Processer att undanta när en sökning körs eller när realtidsskyddet används**|Lägger till en eller flera processer av typen **.exe**, **.com** eller **.scr** i undantagslistan. Dessa processer tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|


### <a name="updates"></a>Updates

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|---------------|
|**Tillåt automatiska uppdateringar**|Tillåt automatiska uppdateringar. Konfigurera någon av följande inställningar för att kontrollera uppdateringsbeteendet:<br />**Meddela om hämtning**<br />**Automatisk installation vid underhållstidpunkt**<br />**Automatisk installation och omstart vid underhållstidpunkt**<br />**Installera automatiskt och starta om enligt schema**: Om det här alternativet har valts kan du också konfigurera följande inställningar: **Meddela inte slutanvändare** och **Definiera installationsdag för schemalagda uppdateringar**.<br>(endast Windows 10 Desktop)|
|**Tillåt förhandsfunktioner**|Låter Microsoft distribuera förhandsversionsinställningar och -funktioner till Windows 10-enheter. Du kan välja att tillåta att endast inställningar eller alla förhandsversionsinställningar och -funktioner installeras.|

### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
