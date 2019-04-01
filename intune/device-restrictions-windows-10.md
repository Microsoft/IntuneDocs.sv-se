---
title: Enhetsbegränsningsinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista med alla inställningar och deras beskrivningar för att skapa enhetsbegränsningar i enheter med Windows 10 och senare. Använd dessa inställningar i en konfigurationsprofil för att styra skärmdumpar, lösenordskrav, inställningar för helskärmsläge, appar i butiken, Edge-webbläsaren, Windows Defender, åtkomst till molnet, startmenyn etc. i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8190365ad2b50dfa7369b8899e8984b6a52f1cba
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566761"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Enhetsinställningar för Windows 10 (och senare) för att tillåta eller begränsa funktioner med hjälp av Intune

Den här artikeln beskriver alla olika inställningar som du kan styra på enheter med Windows 10 och senare. Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar för att tillåta eller inaktivera funktioner, ange lösenordsregler, anpassa låsskärmen använda Windows Defender med mera.

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina Windows 10-enheter.

> [!Note]
> Det är inte alla alternativ som är tillgängliga i alla utgåvor av Windows

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>Appbutik

- **Appbutik (endast mobil)**: Aktivera eller blockera användning av appbutiken på Windows 10 Mobile-enheter.
- **Uppdatera appar automatiskt från Store**: Appar som installeras från Microsoft Store uppdateras automatiskt.
- **Installation av betrodd app**: Appar som signeras med ett betrott certifikat läses in separat.
- **Lås upp via utvecklare**: Tillåter Windows utvecklarinställningar, till exempel att separat inlästa appar ska kunna ändras av användaren.
- **Dela appdata mellan användare**: Tillåter att appar delar data mellan olika användare på samma enhet.
- **Använd endast privat katalog**: Aktivera för att endast tillåta att användarna hämtar appar från din privata katalog.
- **Start av appar från Store**: Används för att inaktivera alla appar som har förinstallerats på enheten eller hämtats från Microsoft Store.
- **Installera appdata på systemvolym**: Hindrar appar från att lagra data på enhetens systemvolym.
- **Installera appar på systemenhet**: Hindrar appar från att lagra data på enhetens systemenhet.
- **Spel-DVR (endast stationär dator)**: Konfigurerar om registrering och sändning av spel tillåts.
- **Endast appar från butik**: Konfigurerar om användare kan installera appar från andra platser än appbutiken.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning

- **Mobildatakanal**: Hindrar användarna från att använda data, t.ex. för webbsurfning, när de är anslutna till ett mobilnät. 
- **Dataroaming**: Tillåt roaming mellan nätverk vid åtkomst till data.
- **VPN över mobilt nätverk**: Styr om enheten har åtkomst till VPN-anslutningar när den är ansluten till ett mobilt nätverk.
- **VPN-roaming över mobilt nätverk**: Styr om enheten har åtkomst till VPN-anslutningar när roaming används i ett mobilt nätverk.
- **Bluetooth**: Styr om användaren kan aktivera och konfigurera Bluetooth på enheten.
- **Bluetooth-identifiering**: Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.
- **Bluetooth-förhandsparkoppling**: Med den här inställningen kan du konfigurera vissa Bluetooth-enheter till att automatiskt parkopplas med en värdenhet.
- **Bluetooth-annonsering**: Låter enheten ta emot annonser via Bluetooth.
- **Connected Devices Service**: Låter dig välja om du vill tillåta tjänsten Connected Devices Service. Tjänsten aktiverar identifiering av och anslutning till andra Bluetooth-enheter.
- **NFC**: Gör att användaren kan aktivera och konfigurera närfältskommunikation (NFC) på enheten.
- **Trådlöst nätverk**: Låter användaren aktivera och konfigurera trådlösa funktioner på enheten (endast Windows 10 Mobile).
- **Anslut automatiskt till trådlösa surfpunkter**: Tillåter att enheten ansluter automatiskt till kostnadsfria trådlösa surfpunkter och att den godkänner eventuella villkor för anslutningen automatiskt.
- **Manuell trådlös konfiguration**: Styr om användarna kan konfigurera egna trådlösa anslutningar, eller om de endast kan använda anslutningar som konfigurerats med en trådlös profil (endast Windows 10 Mobile).
- **Sökintervall för trådlöst nätverk**: Ange hur ofta enheterna ska söka efter trådlösa nätverk. Ange ett värde mellan 1 (mest frekvent) till 500 (minst frekvent).
- **Bluetooth-tillåtna tjänster**: Ange, i form av hexadecimala strängar, en lista över tillåtna Bluetooth-tjänster och Bluetooth-profiler.

## <a name="cloud-and-storage"></a>Moln och lagring

- **Microsoft-konto**: Låter användaren associera ett Microsoft-konto med enheten.
- **Andra konton än Microsoft-konton**: Låter användaren lägga till e-postkonton på enheten som inte är associerade med något Microsoft-konto.
- **Synkroniseringsinställningar för Microsoft-konto**: Tillåt att enhets- och appinställningar som har associerats med ett Microsoft-konto synkroniseras mellan enheter.
- **Inloggningsassistenten för Microsoft-konto**: Välj **Inaktivera** för att förhindra att slutanvändarna styr tjänsten för Microsofts inloggningsassistent (wlidsvc), till exempel genom att stoppa eller starta tjänsten manuellt. När **Inte konfigurerad** har angetts använder wlidsvc NT-tjänsten standardoperativsystemet, vilket kan tillåta att slutanvändarna startar och stoppar tjänsten. Den här tjänsten används av operativsystemet för att tillåta att användaren loggar in på sitt Microsoft-konto.

## <a name="cloud-printer"></a>Molnskrivare

- **URL för skrivaridentifiering**: Ange URL:en för identifiering av molnskrivare.
- **URL för utfärdare av skrivaråtkomst**: Ange URL för autentiseringsslutpunkt för att hämta OAuth-token. Ange något i stil med `https://login.microsoftonline.com/your Azure AD Tenant ID`.
- **GUID för inbyggd Azure-klientapp**: Ange GUID för ett klientprogram som har behörighet att hämta OAuth-token från OAuthAuthority.
- **Resurs-URI för utskriftstjänst**: Ange OAuth resurs-URI för utskriftstjänster som konfigurerats i Azure-portalen. Ange något i stil med `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Maxantal skrivare att fråga efter (endast mobil)**: Ange maximalt antal skrivare som du vill att frågor körs mot. Ange till exempel `10`.
- **Resurs-URI för identifiering av utskriftstjänst**: Ange OAuth resurs-URI för identifiering av utskriftstjänster som konfigurerats i Azure-portalen. Ange något i stil med `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> När du har konfigurerat en [Windows Server Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview) kan du konfigurera dessa inställningar och sedan distribuera till Windows-enheter.

## <a name="control-panel-and-settings"></a>Kontrollpanel och inställningar

- **Inställningsapp**: Blockera åtkomst till appen för Windows-inställningar.
  - **System**: Blockerar åtkomsten till systemområdet för inställningsappen.
    - **Ändra energialternativinställningar (endast stationär dator)**: Förhindrar att användaren ändrar energialternativinställningar på enheten.
  - **Enheter**: Blockerar åtkomsten till enhetsområdet för inställningsappen.
  - **Nätverk och Internet**: Blockerar åtkomsten till nätverket och Internetområdet för inställningsappen.
  - **Anpassning**: Blockerar åtkomsten till anpassningsområdet för inställningsappen.
  - **Konton**: Blockerar åtkomsten till kontoområdet för inställningsappen.
  - **Tid och språk**: Blockerar åtkomsten till tid- och språkområdet för inställningsappen.
    - **Ändra systemtid**: Förhindrar att slutanvändaren ändrar enhetens datum och tid.
    - **Ändra nationella inställningar (endast stationär dator)**: Förhindrar att slutanvändaren ändrar de nationella inställningarna på enheten.
    - **Ändra språkinställningar (endast stationär dator)**: Förhindrar att användaren ändrar språkinställningarna på enheten.
  - **Spel**: Blockerar åtkomst till spelappen i inställningarna.
  - **Hjälpmedel**: Blockerar åtkomsten till området Hjälpmedel i inställningsappen.
  - **Sekretess**: Blockerar åtkomsten till sekretessområdet för inställningsappen.
  - **Uppdatering och säkerhet**: Blockerar åtkomst till uppdaterings- och säkerhetsområdet i inställningsappen.

## <a name="display"></a>Visning

- **Aktivera GDI-skalning för appar**
- **Stäng av GDI-skalning för appar**

  Med GDI DPI-skalning kan appar som inte är DPI-medvetna bli DPI-medvetna per övervakare. Ange äldre appar som har DPI-GDI-skalning aktiverat. Med GDI DPI-skalning konfigurerat till att både aktivera och inaktivera en app, är skalning inaktiverat för appen.

## <a name="general"></a>Allmänt

- **Skärmdump (endast mobil)**: Låter användaren hämta enhetens skärm som en bild.
- **Kopiera och klistra in (endast mobil)**: Tillåter att man kan kopiera och klistra in mellan appar på enheten.
- **Manuell avregistrering**: Låter användaren ta bort sitt arbetsplatskonto från enheten manuellt.
  - Den här inställningen används inte om datorn är ansluten till Azure AD och automatisk registrering har aktiverats. 
  - Den här principinställningen gäller inte för datorer som kör Windows 10 Home.
- **Manuell installation av rotcertifikat (endast mobil)**: Hindrar användaren att manuellt installera rotcertifikat och mellanliggande CAP-certifikat.

- **Kamera**: Tillåter eller blockerar användning av kameran på enheten.
- **OneDrive-filsynkronisering**: Blockerar enheten från att synkronisera filer till OneDrive.
- **Flyttbara lagringsmedier**: Anger om externa lagringsenheter, t.ex. SD-kort, kan användas med enheten.
- **Geoplats**: Anger om enheten kan använda information om platstjänster.
- **Internetdelning**: Tillåter användning av Internetanslutningsdelning på enheten.
- **Telefonåterställning**: Styr om användaren kan göra en rensning på enheten eller inte.
- **USB-anslutning (endast mobil)**: Styr om enheter har åtkomst till externa lagringsenheter via en USB-anslutning.
- **Stöldskyddsläge (endast mobil)**: Konfigurerar om stöldskyddsläget i Windows ska vara aktiverat.
- **Cortana**: Aktiverar eller inaktiverar röstassistenten Cortana.
- **Röstinspelning (endast mobil)**: Tillåter eller blockerar användning av enhetens röstinspelare.
- **Ändra enhetsnamn**: Förhindrar att slutanvändaren ändrar enhetens namn (endast Windows 10 Mobile)
- **Lägg till konfigurationspaket**: Blockerar runtime-konfigurationsagenten som installerar konfigurationspaketen.
- **Ta bort konfigurationspaket**: Blockerar runtime-konfigurationsagenten som tar bort konfigurationspaketen.
- **Enhetsidentifiering**: Blockerar en enhet från att identifieras av andra enheter.
- **Växla mellan aktiviteter (endast mobil)**: Blockerar funktionen Växla mellan aktiviteter på enheten.
- **Dialogruta om SIM-kortsfel (endast mobil)**: Blockerar ett felmeddelande från att visas på enheten om inget SIM-kort har upptäckts.
- **Ink-arbetsytan**: Blockerar användare från att komma åt Ink-arbetsytan. **Inte konfigurerat** aktiverar Ink-arbetsytan och användaren kan använda den ovanför låsskärmen.
- **Automatisk omdistribution**: Låter användare med administrativ behörighet ta bort alla användardata och inställningar med hjälp av **Ctrl + Win + R** på enhetens låsskärm. Enheten omkonfigureras automatiskt och omregistreras för hantering.
- **Kräv att användarna ansluter till nätverket när enheten installeras (endast Windows Insider)**: Välj **Kräv** så att enheten ansluter till ett nätverk innan den fortsätter förbi sidan Nätverk under konfigurationen av Windows 10. När den här funktionen är i förhandsversion krävs Windows Insider-version 1809 eller senare för att använda den här inställningen.
- **Direct Memory Access**: **Blockera** förhindrar direkt minnesåtkomst (DMA) för alla underordnade PCI-portar med enhetsbyte vid drift tills en användare loggar in i Windows. **Aktiverad** (standard) ger åtkomst till DMA, även när en användare inte har loggat in.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Avsluta processer i Aktivitetshanteraren**: den här inställningen avgör om icke-administratörer kan använda Aktivitetshanteraren för att avsluta aktiviteter. **Blockera** förhindrar standardanvändare (icke-administratörer) att använda Aktivitetshanteraren till att avsluta en process eller uppgift på enheten. **Inte konfigurerad** (standard) låter standardanvändare att avsluta en process eller uppgift med Aktivitetshanteraren.


## <a name="locked-screen-experience"></a>Låsskärm

- **Aviseringar från Åtgärdscenter (endast mobil)**: Aviseringar från Åtgärdscenter visas på enhetens låsskärm (endast Windows 10 Mobile).
- **URL till bild på låst skärm (endast stationär dator)**: Anger webbadressen till en bild i JPEG-format som används som låsskärmsbild i Windows. Den här inställningen låser avbildningen. Avbildningen kan inte ändras efteråt.
- **Skärmtidsgräns kan ställas in av användaren (endast mobil)**: Användarna kan konfigurera tiden 
- **Cortana på låst skärm (endast stationär dator)**: Tillåter inte att användaren interagerar med Cortana när enheten har låst skärm (endast Windows 10 Desktop).
- **Popup-meddelanden på låst skärm**: Hindra att varningsmeddelanden visas på enhetens låsskärm.
- **Skärmtidsgräns (endast mobil)**: Anger tiden i sekunder mellan att skärmen låses och stängs av.

## <a name="messaging"></a>Meddelandefunktion

- **Meddelandesynkronisering (endast mobil)**: Inaktivera meddelandefunktioner överallt samt säkerhetskopiering och återställning av textmeddelanden.
- **MMS (endast mobil)**: Inaktivera funktionen för att skicka och ta emot MMS på enheten.
- **RCS (endast mobil)**: Inaktivera funktionen för att skicka och ta emot Rich Communication Services på enheten.

## <a name="microsoft-edge-browser"></a>Microsoft Edge-webbläsaren

### <a name="use-microsoft-edge-kiosk-mode"></a>Använda Microsoft Edge helskärmsläge

De tillgängliga inställningarna ändras beroende på vad du väljer. Alternativen är:

- **Inte** (standard): Microsoft Edge inte körs i helskärmsläge. Alla Microsoft Edge-inställningar är tillgängliga för dig att ändra och konfigurera.
- **Digital/interaktiv signering (kiosk för enskilda appar)**: filter Edge-inställningar som gäller för Digital/interaktiv signering Edge helskärmsläge för användning endast på Windows 10 single-appar. Välj den här inställningen för att öppna URL: en helskärm och endast visa innehållet på webbplatsen. [Ställ in digitala loggar](https://docs.microsoft.com/windows/configuration/setup-digital-signage) finns mer information om den här funktionen.
- **InPrivate-offentliga surfning (kiosk för enskilda appar)**: filter Edge-inställningar som gäller för InPrivate offentliga surfning Edge helskärmsläge för användning på Windows 10 single-appar. Kör en flera fliken version av Microsoft Edge.
- **Normalt läge (helskärmsläge)**: filter Edge-inställningar som gäller för Normal Edge helskärmsläge. Kör en fullständig version av Microsoft Edge med alla webbläsarens funktioner.
- **Offentliga surfning (helskärmsläge)**: filter Edge-inställningar som gäller för offentliga surfning på en Windows 10-helskärmsläge.  Kör en flera fliken version av Microsoft Edge InPrivate.

> [!TIP]
> Läs mer om vad dessa alternativ göra [konfigurationerna för Microsoft Edge helskärmsläge läge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Den här profilen för enhetsbegränsningar är direkt relaterad till kioskprofilen du skapar med den [Windows-inställningar för helskärmsläge](kiosk-settings-windows.md). Sammanfattningsvis:

1. Skapa den [Windows-inställningar för helskärmsläge](kiosk-settings-windows.md) profil för att köra enheten i helskärmsläge. Välj Microsoft Edge som programmet och ställa in helskärmsläge Edge i profilen för helskärmsläge.
2. Skapar en enhetsprofil begränsningar som beskrivs i den här artikeln och konfigurera specifika funktioner och inställningar i Microsoft Edge. Se till att välja samma Edge helskärmsläge läge typ som markerats i din kioskprofilen ([Windows-inställningar för helskärmsläge](kiosk-settings-windows.md)). 

    [Stöd för inställningar för helskärmsläge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) är en bra resurs.

> [!IMPORTANT] 
> Se till att tilldela den här Microsoft Edge-profilen till samma enheter som din kioskprofilen ([Windows-inställningar för helskärmsläge](kiosk-settings-windows.md)).

CSP: [ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Startupplevelse

- **Starta Microsoft Edge med**: Välj vilka sidor som ska öppnas när Microsoft Edge startar. Alternativen är:
  - **Startsidor**: Microsoft Edge startar med den standardstartsida som definieras av operativsystemet
  - **Sidan Ny flik**: Microsoft Edge läser in det som definieras i inställningen **Webbadress till sidan Ny flik**
  - **Senaste sessionssidan**: Microsoft Edge läser in den senaste sessionssidan 
  - **Anpassad startsida**: Microsoft Edge läser in den startsida som definierats av IT-administratören
- **Användaren kan ändra startsidor**: **Tillåt** låter användarna ändra startsidorna. Administratörer kan använda `EdgeHomepageUrls` till att ange de startsidor som användarna ser som standard när de öppnar Microsoft Edge. **Inte konfigurerad** blockerar användarna från att ändra startsidorna.
- **Webbadress till sidan Ny flik**: Ange den webbadress som ska öppnas på sidan Ny flik. Ange till exempel `https://www.bing.com`.
- **Öppna webbinnehåll på sidan Ny flik**: Välj **Blockera** för att stoppa Microsoft Edge från att öppna en webbplats på en ny flik. När den är blockerad är den nya fliken tom när den öppnas. **Inte konfigurerad** använder operativsystemets standardbeteende på enheten, vilket kan tillåta att användarna får välja vad som ska visas.
- **Hemknapp**: Ange vad som händer när hemknappen väljs. Alternativen är:
  - **Startsidor**: Det alternativ som du valde för inställningen **Starta Microsoft Edge med** öppnas
  - **Sidan Ny flik**: Det alternativ som du valde för inställningen **Webbadress till sidan Ny flik** öppnas
  - **Webbadress till anpassad hemknapp**: Det alternativ som du valde för inställningen **Webbadress till hemknapp** öppnas
  - **Dölj hemknapp**: Döljer hemknappen
- **Användaren kan ändra hemknapp**: **Tillåt** låter användarna ändra hemknappen. Användarens ändringar åsidosätter eventuella administratörsinställningar för hemknappen. **Inte konfigurerad** använder operativsystemets standardbeteende på enheten, vilket kan hindra användare från att ändra hur administratören har konfigurerat hemknappen.
- **Visa sidan Välkomstprogram**: **Blockera** hindrar introduktionssidan från att visas första gången du kör Microsoft Edge. Med den här funktionen kan företag som t.ex. är anslutna till nollutsläppskonfigurationer blockera den här sidan. **Inte konfigurerad** visar introduktionssidan.
  - **Webbadress till välkomstprogram**: Ange webbadressen som ska visas första gången en användare kör Microsoft Edge (endast Windows 10 Mobile).
- **Uppdatera webbläsaren efter hur lång tids inaktivitet**: Ange antalet inaktiva minuter tills webbläsaren uppdateras från 0 – 1440 minuter. Standardvärdet är `5` minuter. När värdet `0` (noll), som webbläsaren inte uppdatera efter inaktivitet.

  Den här inställningen är endast tillgänglig när du kör i [offentliga InPrivate-surfning (för enskild kiosk)](#use-microsoft-edge-kiosk-mode).

  CSP: [ConfigureKioskResetAfterIdleTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskresetafteridletimeout)

- **Popup-fönster**: Välj **Blockera** för att stoppa popup-fönster i webbläsaren. Gäller endast Windows 10 Desktop. **Inte konfigurerad** tillåter popup-fönster i webbläsaren.
- **Skicka intranätstrafik till Internet Explorer**: **Tillåt** låter användarna öppna intranätplatser i Internet Explorer i stället för Microsoft Edge (endast Windows 10 Desktop). **Inte konfigurerad** tillåter att användarna använder Microsoft Edge.
- **Plats för webbplatslista för företagsläge**: Ange den URL som innehåller en lista med webbplatser som kan öppnas i företagsläge. Användarna kan inte ändra denna lista. Gäller endast Windows 10 Desktop.
- **Meddelande när webbplatser öppnas i Internet Explorer**: Använd den här inställningen för att konfigurera att Microsoft Edge ska visa ett meddelande innan en webbplats öppnas i Internet Explorer 11. Alternativen är:
  - **Inte konfigurerad**: Operativsystemets standardbeteende används, vilket kan innebära att ett meddelande inte visas.
  - **Visa meddelande utan något alternativ att öppna webbplatser i Microsoft Edge**: Visar meddelandet när webbplatser öppnas i Internet Explorer. Webbplatser öppnas i Internet Explorer. Det finns inte något alternativ för att öppna webbplatser i Microsoft Edge.
  - **Visa meddelandet när webbplatser öppnas i Microsoft Edge**: Visar meddelandet när webbplatser öppnas i Internet Explorer. Meddelandet innehåller länken **Fortsätt i Microsoft Edge** för att användarna ska kunna välja Microsoft Edge i stället för Internet Explorer.

  > [!IMPORTANT]
  > Den här inställningen kräver att du aktiverar inställningen **Konfigurera webbplatslista för företagsläge**, **Skicka alla intranätplatser till Internet Explorer 11** eller båda inställningarna.

- **Microsoft-kompatibilitetslista**: **Blockera** förhindrar Microsoft-kompatibilitetslistan i Microsoft Edge. Med den här listan från Microsoft kan Microsoft Edge korrekt visa webbplatser med kända kompatibilitetsproblem. **Inte konfigurerad** tillåter att en Microsoft-kompatibilitetslista används.
- **Läs in startsidor och sidan Ny flik i förväg**: Välj **Blockera** för att förhindra att Microsoft Edge läser in startsidor och sidan Ny flik i förväg. Förinläsningen minimerar den tid det tar att starta Microsoft Edge och läsa in en ny flik. **Inte konfigurerad** använder operativsystemets standardbeteende, vilket kan vara att förinläsa dessa sidor.
- **Starta startsidor och sidan Ny flik i förväg**: Välj **Blockera** för att förhindra att Microsoft Edge startar startsidor och sidan Ny flik i förväg. Genom att starta Microsoft Edge i förväg förbättras prestandan och den tid som krävs för att starta Microsoft Edge minimeras. **Inte konfigurerad** använder operativsystemets standardbeteende, vilket kan vara att starta dessa sidor i förväg.

### <a name="favorites-and-search"></a>Favoriter och sökning

- **Fältet Favoriter**: Välj vad som ska hända i fältet Favoriter på valfri Microsoft Edge-sida. Alternativen är:
  - **Inte konfigurerad**: Använder operativsystemets standardbeteende, vilket kan vara att dölja fältet Favoriter på alla sidor. Användaren kan ändra den här inställningen.
  - **Dölj**: Döljer fältet Favoriter på alla sidor. Användaren kan inte ändra den här inställningen.
  - **Visa**: Visar fältet Favoriter på alla sidor. Användaren kan inte ändra den här inställningen.
- **Listan Favoriter**: Lägg till en lista med webbadresser i filen med Favoriter. Lägg exempelvis till `http://contoso.com/favorites.html`.
- **Begränsa ändringar i Favoriter**: **Blockera** för att hindra användarna från att lägga till, importera, sortera och redigera listan Favoriter. **Inte konfigurerad** använder operativsystemets standardvärde, vilket kan tillåta användarna att ändra listan.
- **Synkronisera favoriter mellan Microsoft-webbläsare (endast stationär dator)**: **Kräv** tvingar Windows att synkronisera favoriter mellan Internet Explorer och Microsoft Edge. Tillägg, borttagningar, modifieringar och sorteringsändringar i Favoriter delas mellan webbläsarna.  **Inte konfigurerad** använder operativsystemets standard, vilket kan ge användarna möjlighet att synkronisera favoriter mellan webbläsarna.
- **Standardsökmotor**: Välj den standardsökmotor som ska användas på enheten. Användarna kan ändra det här värdet när som helst. Alternativen är:
  - Standardvärde
  - Bing
  - Google
  - Yahoo
  - Anpassat värde
- **Sökförslag**: **Inte konfigurerat** innebär att din sökmotor föreslår webbplatser när du skriver sökfraser i adressfältet. **Blockera** förhindrar den här funktionen.
- **Tillåt ändringar av sökmotor**: **Ja** (standard) kan du lägga till nya sökmotorer eller ändra standardsökmotorn i Microsoft Edge. Välj **nr** att hindra användare från att anpassa sökmotorn.

  Den här inställningen är endast tillgänglig när du kör i [normalläge (helskärmsläge)](#use-microsoft-edge-kiosk-mode).

  CSP: [AllowSearchEngineCustomization](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsearchenginecustomization)

### <a name="privacy-and-security"></a>Sekretess och säkerhet

- **InPrivate-surfning**: **Blockera** förhindrar att slutanvändarna öppnar InPrivate-surfningssessioner. **Inte konfigurerad** tillåter denna funktion.
- **Spara webbhistorik**: **Blockera** hindrar Microsoft Edge från att spara webbhistoriken. **Inte konfigurerad** tillåter att webbhistoriken sparas.
- **Rensa webbdata vid avslut (endast stationär dator)**: **Kräv** rensar historik och webbdata när användaren avslutar Microsoft Edge. **Inte konfigurerad** använder operativsystemets standard, vilket kan innebära att webbdata cachelagras.
- **Synkronisera webbläsarens inställningar mellan användarens enheter**: Välj hur du vill synkronisera webbläsarinställningar mellan enheter. Alternativen är:
  - **Tillåt**: Tillåt synkronisering av Microsoft Edge-webbläsarinställningar mellan användarens enheter
  - **Blockera och aktivera åsidosättning av användaren**: Blockera synkronisering av Microsoft Edge-webbläsarinställningar mellan användarens enheter. Användarna kan åsidosätta den här inställningen.
  - **Blockera**: Blockerar synkronisering av Microsoft Edge-webbläsarinställningar mellan användarens enheter. Användarna kan inte åsidosätta den här inställningen.
- **Lösenordshanteraren**: **Blockera** inaktiverar lösenordshanteraren för Microsoft Edge. **Inte konfigurerad** tillåter denna funktion.
- **Cookies**: Välj hur cookies ska hanteras i webbläsaren. Alternativen är:
  - **Tillåt**: Cookies sparas på enheten.
  - **Blockera alla cookies**: Cookies sparas inte på enheten.
  - **Blockera endast cookies från tredje part**: Cookies från tredje part eller partner sparas inte på enheten.
- **Autofyll**: **Blockera** inaktiverar funktionen Autofyll på enheten. **Inte konfigurerad** tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren (endast Windows 10 Desktop).
- **Skicka Do Not Track-huvuden**: **Inte konfigurerad** kräver att enheter skickar Do Not Track-huvuden till webbplatser som kräver spårningsinfo (rekommenderas). Välj **Blockera** om enheten ska hindras från att skicka dessa huvuden, vilket gör att webbplatser kan spåra användaren.
- **LocalHost-IP-adress för WebRTC**: **Blockera** förhindrar att användarnas LocalHost-IP-adress visas vid telefonsamtal via WebRTC-protokollet. **Inte konfigurerad** tillåter att användarnas LocalHost-IP-adress visas vid telefonsamtal med detta protokoll.
- **Datainsamling för levande panel**. Välj **Blockera** för att hindra Windows från att samla in information från den levande panelen när användaren fäster något på Start-menyn från Microsoft Edge. Med **Inte konfigurerad** kan den här informationen samlas in.
- **Användaren kan åsidosätta certifikatfel**: **Blockera** förhindrar användarna från att komma åt webbplatser med SSL- eller TLS-fel. **Inte konfigurerad** ger användarna åtkomst till dessa webbplatser.

### <a name="additional"></a>Mer information

- **Microsoft Edge-webbläsare (endast mobil)**: Välj **Blockera** för att förhindra att Microsoft Edge används på enheten. Om du blockerar Microsoft Edge tillämpas de enskilda inställningarna endast på den stationära datorn. **Inte konfigurerad** tillåter att Microsoft Edge-webbläsaren används på enheten.
- **Listruta i adressfältet (endast stationär dator)**: **Blockera** hindrar Microsoft Edge från att visa en listruta med förslag när du skriver. Det här alternativet hjälper till att minimera nätverksbandbredden mellan Microsoft Edge och Microsoft-tjänster. **Inte konfigurerad** tillåter att Microsoft Edge visar en lista med förslag.
- **Helskärm**: Välj **Blockera** för att förhindra att Microsoft Edge endast visar webbinnehåll och för att dölja Microsoft Edge (helskärmsläge). **Inte konfigurerad** använder operativsystemets standardvärde, vilket gör att Microsoft Edge kan använda helskärmsläge.
- **Om flaggor**: **Blockera** hindrar slutanvändarna från att komma åt sidan `about:flags` i Microsoft Edge som innehåller inställningar för utvecklare och experiment. **Inte konfigurerad** använder operativsystemets standardvärde, vilket kan tillåta åtkomst till sidan `about:flags`.
- **Utvecklarverktyg**: **Blockera** förhindrar att användaren öppnar utvecklarverktygen för Microsoft Edge. Med **Inte konfigurerad** kan användarna öppna utvecklarverktygen.
- **Tillägg**: **Inte konfigurerad** tillåter att slutanvändarna installerar Microsoft Edge-tillägg på enheten. **Blockera** förhindrar installationen.
- **Separat inläsning av utvecklartillägg**: **Blockera** förhindrar separat inläsning i Microsoft Edge, vilket installerar och kör overifierade tillägg med funktionen **Läs in tillägg**. **Inte konfigurerad** använder operativsystemets standardvärde, vilket kan tillåta separat inläsning.
- **Tillägg som krävs**: Välj vilka tillägg som inte ska kunna inaktiveras av slutanvändarna i Microsoft Edge. Ange paketfamiljenamnet och välj **Lägg till**. I listorna [Hitta ett paketfamiljenamn (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) finns viss vägledning.

  Du kan också **Importera** en CSV-fil som innehåller paketfamiljenamnen.

- **JavaScript**: Välj **Blockera** för att förhindra att Java-skript i webbläsaren körs på enheten. **Inte konfigurerad** tillåter att skript, exempelvis JavaScript, körs i Microsoft Edge-webbläsaren.

## <a name="network-proxy"></a>Nätverksproxy

- **Identifiera proxyinställningar automatiskt**: När det här alternativet är aktiverat kommer enheten att försöka hitta sökvägen till ett PAC-skript.
- **Använd proxyskript**: Välj det här alternativet om du vill ange en sökväg till ett PAC-skript för att konfigurera proxyservern.
  - **Ställ in webbadress till skript**: Ange webbadressen för ett PAC-skript som du vill använda för att konfigurera proxyservern.
- **Använd manuell proxyserver**: Välj det här alternativet om du vill ange proxyserverinformationen manuellt.
  - **Adress**: Ange namn eller IP-adress för proxyservern.
  - **Portnummer**: Ange portnumret till proxyservern.
  - **Proxyundantag**: Ange de webbadresser som inte får använda proxyservern. Använd semikolon för att avgränsa varje objekt.
  - **Använd ingen proxyserver för lokal adress**: Aktivera det här alternativet om du inte vill använda proxyservern för lokala adresser på intranätet.

## <a name="password"></a>Lösenord

- **Lösenord**: Kräver att användaren måste ange ett lösenord för att få åtkomst till enheten.
  - **Krav på lösenordstyp**: Anger om lösenordet måste vara enbart numeriskt, eller om det kan vara alfanumeriskt.
  - **Minsta längd på lösenord**: Gäller endast Windows 10 Mobile.
  - **Antal felaktiga inloggningar innan enheten rensas**: För enheter som kör Windows 10: Om BitLocker är aktiverat på enheten försätts den i återställningsläget för BitLocker när gränsen för antal misslyckade inloggningar som du har angett har uppnåtts. Om BitLocker inte är aktiverat på enheten tillämpas inte den här inställningen. För enheter som kör Windows 10 Mobile: Om inloggningen misslyckas ett visst antal gånger (som du har angett) rensas enheten.
  - **Maximalt antal minuter av inaktivitet innan skärmen låses**: Anger hur lång tid en enhet måste vara i viloläge innan skärmen låses.
  - **Lösenordets giltighetstid (dagar)**: Anger efter hur lång tid enhetens lösenord måste ändras.
  - **Förhindra återanvändning av tidigare lösenord**: Anger hur många tidigare använda lösenord enheten kommer ihåg.
  - **Kräv lösenord när enheten lämnar inaktivt läge (endast mobil)**: Anger att användaren måste ange ett lösenord för att kunna låsa upp enheten (endast Windows 10 Mobile).
  - **Enkla lösenord**: Låter dig använda enkla lösenord som 1111 och 1234. Dessutom tillåter eller blockerar den här inställningen användningen av Windows-bildlösenord.

## <a name="per-app-privacy-exceptions"></a>Sekretessundantag per app

Du kan lägga till appar som ska ha en annan sekretess jämfört med vad du har definierat i din ”standardsekretess”.

- **Paketnamn**: Namn på appens paketfamilj.
- **Appnamn**: Namnet på appen.

### <a name="exceptions"></a>Undantag

- **Kontoinformation**: Definiera om den här appen kan komma åt användarnamn, bild och annan kontaktinformation.
- **Bakgrundsappar**: Definiera om den här appen kan köras i bakgrunden.
- **Kalender**: Definiera om den här appen kan komma åt kalendern.
- **Samtalshistorik**: Definiera om den här appen kan komma åt samtalshistoriken.
- **Kamera**: Definiera om den här appen kan komma åt kameran.
- **Kontakter**: Definiera om den här appen kan komma åt kontakter.
- **E-post**: Definiera om den här appen kan komma åt och skicka e-post.
- **Plats**: Definiera om den här appen kan komma åt platsinformation.
- **Meddelandefunktion**: Ange om den här appen kan läsa eller skicka SMS- och MMS-meddelanden.
- **Mikrofon**: Definiera om den här appen kan använda mikrofonen.
- **Rörelse**: Definiera om den här appen kan komma åt rörelseinformation.
- **Meddelanden**: Definiera om den här appen kan komma åt meddelanden.
- **Telefon**: Definiera om den här appen kan komma åt telefonen.
- **Radio**: Vissa appar kan använda radiofunktioner (t.ex. Bluetooth) i din enhet till att skicka och ta emot data. De behöver därför kunna sätta igång eller stänga av de här radiofunktionerna. Definiera om den här appen kan styra dessa radiofunktioner.
- **Uppgifter**: Definiera om den här appen kan komma åt dina uppgifter.
- **Betrodda enheter**: Välj om den här appen kan använda betrodda enheter, t.ex. maskinvara som du redan har anslutit eller som medföljer enheten. Du kan t.ex. använda tv-apparater, projektorer osv. som betrodda enheter.
- **Feedback och diagnostik**: Definiera om den här appen kan komma åt diagnostisk information.
- **Synkronisering med enheter**: Välj om den här appen automatiskt kan dela och synkronisera information med trådlösa enheter som inte uttryckligen kopplats ihop med enheten.

## <a name="personalization"></a>Anpassning

- **URL för skrivbordsbakgrundsbild (endast stationär dator)**: Ange URL:en till en bild i JPEG-format som du vill använda som skrivbordsbakgrund i Windows. Användare kan inte ändra bilden.

## <a name="printer"></a>Skrivare

- **Skrivare**: Lista över lokala skrivare som har lagts till.
- **Standardskrivare**: Ange standardskrivaren.
- **Användarbehörighet att lägga till nya skrivare**: Tillåt eller blockera användning av lokala skrivare.

## <a name="privacy"></a>Sekretess

- **Anpassning av inmatning**: Tillåt inte användning av molnbaserade taltjänster för Cortana, diktering eller Microsoft Store-appar. Om du tillåter dessa tjänster kan det hända att Microsoft samlar in röstdata för att förbättra tjänsten.
- **Automatiskt godkännande av frågor om användarens medgivande till parkoppling och sekretess**: Tillåt att Windows automatiskt godkänner meddelanden om medgivande till parkoppling och sekretess när appar körs.
- **Publicera användaraktiviteter**: **Blockera** förhindrar delad användning och identifiering av nyligen använda resurser i aktivitetsväxlingen.
- **Endast lokala aktiviteter**: **Blockera** förhindrar delad användning och identifiering av nyligen använda resurser i aktivitetsväxlingen, enbart baserat på lokal aktivitet.

Du kan konfigurera den information som alla appar på enheten kan komma åt. Du kan också definiera undantag per app med hjälp av **Sekretessundantag per app**.

### <a name="exceptions"></a>Undantag

- **Kontoinformation**: Definiera om den här appen kan komma åt användarnamn, bild och annan kontaktinformation.
- **Bakgrundsappar**: Definiera om den här appen kan köras i bakgrunden.
- **Kalender**: Definiera om den här appen kan komma åt kalendern.
- **Samtalshistorik**: Definiera om den här appen kan komma åt samtalshistoriken.
- **Kamera**: Definiera om den här appen kan komma åt kameran.
- **Kontakter**: Definiera om den här appen kan komma åt kontakter.
- **E-post**: Definiera om den här appen kan komma åt och skicka e-post.
- **Plats**: Definiera om den här appen kan komma åt platsinformation.
- **Meddelandefunktion**: Ange om den här appen kan läsa eller skicka SMS- och MMS-meddelanden.
- **Mikrofon**: Definiera om den här appen kan använda mikrofonen.
- **Rörelse**: Definiera om den här appen kan komma åt rörelseinformation.
- **Meddelanden**: Definiera om den här appen kan komma åt meddelanden.
- **Telefon**: Definiera om den här appen kan komma åt telefonen.
- **Radio**: Vissa appar kan använda radiofunktioner (t.ex. Bluetooth) i din enhet till att skicka och ta emot data. De behöver därför kunna sätta igång eller stänga av de här radiofunktionerna. Definiera om den här appen kan styra dessa radiofunktioner.
- **Uppgifter**: Definiera om den här appen kan komma åt dina uppgifter.
- **Betrodda enheter**: Välj om den här appen kan använda betrodda enheter. Betrodda enheter är maskinvara som du redan har anslutit eller som medföljer den här datorn. Du kan t.ex. använda tv-apparater, projektorer osv. som betrodda enheter.
- **Feedback och diagnostik**: Välj om den här appen ska komma åt diagnostisk information.
- **Synkronisering med enheter** – Definiera om den här appen automatiskt kan dela och synkronisera information med trådlösa enheter som inte uttryckligen kopplats ihop med den här datorn, surfplattan eller telefonen.

## <a name="projection"></a>Projektion

- **Användarindata från trådlösa visningsmottagare**: Blockerar användarindata från trådlösa visningsmottagare.
- **Projektion till den här datorn**: Stoppar andra enheter från att upptäcka datorn för projektion.
- **Kräv en PIN-kod för parkoppling**: Kräver en PIN-kod när du ansluter till en projektionsenhet.

## <a name="reporting-and-telemetry"></a>Rapportering och telemetri

- **Dela användningsdata**: Välj nivå av diagnostikdata som skickas. Alternativen är:
  - Säkerhet
  - Grundläggande
  - Utökat
  - Fullständig
- **Skicka Microsoft Edge-webbdata till Microsoft 365 Analytics**: Om du vill använda denna funktion kan du ange inställningar för **Dela användningsdata** till **Utökad** eller **Fullständig**. Den här funktionen styr vilka data Microsoft Edge skickar till Microsoft 365 Analytics för Enterprise-enheter med ett konfigurerat kommersiellt ID. Alternativen är:
  - **Inte konfigurerad**: Använder operativsystemets standard, vilket kanske inte skickar webbhistorik
  - **Skicka endast data för intranät**: Låter administratören skicka historik för intranät
  - **Skicka endast data för Internet**: Låter administratören skicka historik för Internet
  - **Skicka data för intranät och Internet**: Låter administratören skicka historik för intranät och Internet
- **Telemetriproxyserver**: Ange det fullständiga domännamnet (FQDN) eller IP-adressen för en proxyserver för att vidarebefordra anslutna användarupplevelser och telemetribegäranden som använder en SSL-anslutning (Secure Sockets Layer). Formatet för den här inställningen är *server*:*port*. Om den namngivna proxyn misslyckas, eller om det inte finns någon proxy angiven när principen aktiveras, överförs inte anslutna användarupplevelser och telemetridata, utan de finns kvar på den lokala enheten.

  Exempelformat:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>Sök

- **Säker sökning (endast mobil)**: Styr hur Cortana filtrerar innehåll för vuxna i sökresultaten. Du kan välja **Strikt**, **Måttlig** eller tillåta att användaren väljer sina egna inställningar.
- **Visa webbresultat i sökning**: Blockera eller tillåt att webbresultat visas i sökningar på enheten.

## <a name="start"></a>Start

- **Layout för Start-menyn**: Om du vill anpassa Start-menyn på stationära enheter kan du ladda upp en XML-fil som innehåller dina anpassningar, inklusive den ordning som apparna visas i listan etc. Användarna kan inte ändra den layout för Start-menyn som du anger.
- **Fäst webbplatser på paneler i Start-menyn**: Importera bilder från Microsoft Edge som visas som länkar i Windows Start-menyn för stationära enheter.
- **Ta bort appar från aktivitetsfältet**: Välj **Blockera** om du vill förhindra användaren från att ta bort appar från aktivitetsfältet.
- **Snabbt användarbyte**: Välj **Blockera** om du vill förhindra växling mellan användare som är inloggade samtidigt utan utloggning.
- **Appar som används oftast**: Välj **Blockera** om du vill dölja de appar som oftast används från att visas på Start-menyn. Detta inaktiverar även motsvarande reglage i appen Inställningar.
- **Nyligen tillagda appar**: Välj **Blockera** om du vill hindra nyligen tillagda appar från att visas på Start-menyn. Detta inaktiverar även motsvarande reglage i appen Inställningar.
- **Starta skärmläge**: Välj hur Start-skärmen ska visas. Välja att visa den som **helskärm** eller **icke-helskärm**.
- **Nyligen öppnade objekt i snabblistor**: Välj **Blockera** om du vill hindra de senaste snabblistorna från att visas på Start-menyn och i aktivitetsfältet. Detta inaktiverar även motsvarande reglage i appen Inställningar.
- **Applista**: Välj hur appen Inställningar ska visas. Alternativen är: 
  - Dölj
  - Dölj och inaktivera appen Inställningar 
  - Döljer och inaktiverar appen Inställningar
- **Strömknapp**: Välj **Blockera** om du vill hindra strömknappen från att visas på Start-menyn.
- **Användarpanel**: Välj **Blockera** om du vill hindra användarpanelen från att visas på Start-menyn.
  - **Lås**: Välj **Blockera** om du vill hindra alternativet `Lock` från att visas i användarpanelen på Start-menyn.
  - **Logga ut**: Välj **Blockera** om du vill hindra alternativet `Sign out` från att visas i användarpanelen på Start-menyn.
- **Stäng av**: Välj **Blockera** om du vill hindra alternativen `Update and shut down` och `Shut down` från att visas i strömknappen på Start-menyn.
- **Strömsparläge**: Välj **Blockera** om du vill hindra alternativet `Sleep` från att visas i strömknappen på Start-menyn.
- **Viloläge**: Välj **Blockera** om du vill hindra alternativet `Hibernate` från att visas i strömknappen på Start-menyn.
- **Växla konto**: Välj **Blockera** om du vill hindra `Switch account` från att visas i användarpanelen på Start-menyn.
- **Omstartsalternativ**: Välj **Blockera** om du vill hindra alternativen `Update and restart` och `Restart` från att visas i strömknappen på Start-menyn.
- **Dokument på Start**: Dölj eller visa mappen Dokument i Start-menyn i Windows.
- **Nedladdningar på Start**: Dölj eller visa mappen Nedladdningar i Start-menyn i Windows.
- **Utforskaren på Start**: Dölj eller visa Utforskaren i Start-menyn i Windows.
- **Hemgrupp på Start**: Dölj eller visa mappen Hemgrupp i Start-menyn i Windows.
- **Musik på Start**: Dölj eller visa mappen Musik i Start-menyn i Windows.
- **Nätverk på Start**: Dölj eller visa mappen Nätverk i Start-menyn i Windows.
- **Personlig mapp på Start**: Dölj eller visa den personliga mappen i Start-menyn i Windows.
- **Bilder på Start**: Dölj eller visa mappen för bilder i Start-menyn i Windows.
- **Inställningar på Start**: Dölj eller visa appen Inställningar i Start-menyn i Windows.
- **Videor på Start**: Dölj eller visa mappen för videor i Start-menyn i Windows.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **SmartScreen för Microsoft Edge**: Aktivera Microsoft Edge SmartScreen för åtkomst till webbplats och filnedladdningar.
- **Åtkomst till skadlig webbplats**: Blockera användarna från att ignorera varningarna från Windows Defender SmartScreen-filtret och blockera dem från att gå till webbplatsen.
- **Overifierad filhämtning**: Blockera användarna från att ignorera varningarna från Windows Defender SmartScreen-filtret och blockera dem från att hämta overifierade filer.

## <a name="windows-spotlight"></a>Windows Spotlight

- **Windows Spotlight**: Använd den här inställningen för att blockera alla Windows Spotlight-funktioner på Windows 10-enheter. Följande inställningar är inte tillgängliga om du blockerar den här inställningen:
  - **Windows Spotlight på låsskärm**: Hindra Windows Spotlight från att visa information på enhetens låsskärm.
  - **Tredjepartsförslag i Windows Spotlight**: Hindra Windows Spotlight från att föreslå innehåll som inte har publicerats av Microsoft.
  - **Konsumentfunktioner**: Låter dig blockera konsumentfunktioner som t.ex. förslag för startmenyn och medlemskapsaviseringar.
  - **Windows-tips**: Låter dig blockera popup-tips från att visas i Windows.
  - **Windows Spotlight i Åtgärdscenter**: Blockera Windows Spotlight-förslag, på t.ex. nya appar eller säkerhetsinnehåll, från att visas i Windows Åtgärdscenter.
  - **Windows Spotlight-anpassning**: Hindra Windows Spotlight från att anpassa resultat baserat på användningen av en enhet.
  - **Välkommen till Windows-skärm**: Blockera Välkommen till Windows-skärmen där användarinformation om nya eller uppdaterade funktioner visas.

## <a name="windows-defender-antivirus"></a>Windows Defender Antivirus

- **Övervakning i realtid**: Tillåter genomsökning i realtid efter skadlig programvara, spionprogram och annan oönskad programvara.
- **Övervaka funktionssätt**: Tillåter att Defender söker efter kända mönster för misstänkt aktivitet på enheterna.
- **NIS (Network Inspection System)**: NIS hjälper till att skydda enheter mot nätverksbaserade säkerhetsrisker. Det använder signaturer för kända problem från Microsoft Endpoint Protection Center för att identifiera och blockera skadlig trafik.
- **Sök igenom alla nedladdningar**: Styr om Defender genomsöker alla filer som laddas ner från Internet.
- **Sök igenom skript som har lästs in via Microsoft-webbläsare**: Tillåter Defender-genomsökning av skript som används i Internet Explorer.
- **Användaråtkomst till Defender**: Styr om Windows Defender-användargränssnittet är dolt för slutanvändarna. När den här inställningen ändras börjar den gälla nästa gång användarens dator startas om.
- **Intervall för signaturuppdatering (i timmar)**: Ange med vilket intervall Defender söker efter nya signaturfiler.
- **Övervaka fil- och programaktivitet**: Tillåter att Defender övervakar fil- och programaktivitet på enheter.
- **Dagar innan skadlig kod i karantän tas bort**: Tillåter att Defender fortsätter spåra åtgärdad skadlig kod det antal dagar som du anger, för att du ska kunna kontrollera tidigare berörda enheter manuellt. Om du ställer in antalet dagar till **0** finns skadlig kod kvar i karantänmappen och tas inte bort automatiskt.
- **Gräns för processoranvändning under genomsökning**: Tillåter att du begränsar hur mycket processorkraft som genomsökningarna får använda (från **1** till **100**).
- **Sök igenom arkivfiler**: Tillåter att Defender söker igenom arkiverade filer, till exempel ZIP- eller CAB-filer.
- **Sök igenom inkommande e-postmeddelanden**: Tillåter att Defender söker igenom e-postmeddelanden när de tas emot på enheten.
- **Sök igenom flyttbara enheter vid fullständig genomsökning**: Tillåter att Defender genomsöker flyttbara enheter, som t.ex. USB-minnen.
- **Sök igenom mappade nätverksenheter vid fullständig genomsökning**: Tillåter att Defender genomsöker filer på mappade nätverksenheter.
  Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.
- **Sök igenom filer öppnade från nätverksmappar**: Tillåter att Defender genomsöker filer på delade nätverksenheter (till exempel filer som nås från en UNC-sökväg). Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.
- **Molnskydd**: Tillåter eller förhindrar att Microsoft Active Protection Service tar emot information om aktiviteter med skadlig kod från enheter som du hanterar. Den här informationen används för att förbättra tjänsten i framtiden.
- **Be användarna att skicka exempel**: Anger om potentiellt skadliga filer som kan kräva ytterligare analys ska skickas automatiskt till Microsoft.
- **Tidpunkt för daglig snabbsökning**: Tillåter att du schemalägger en snabbgenomsökning som körs varje dag vid den tidpunkt som du väljer.
- **Typ av systemgenomsökning som ska utföras**: Ange nivå för genomsökningen som ska utföras när du schemalägger en systemgenomsökning.
- **Identifiera potentiellt oönskade program**: Välj nivå av skydd när Windows identifierar potentiellt oönskade appar från:
  - **Blockera**
  - **Granska** Mer information om potentiellt oönskade appar finns i [Identifiera och blockera potentiellt oönskade program](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
- **Åtgärder vid hot om identifierad skadlig kod**: Använd det här alternativet för att välja vilka åtgärder du vill att Defender ska vidta för varje hotnivå den identifierar (låg, måttlig, hög och allvarlig). Alternativen är:
  - **Rensa**
  - **Karantän**
  - **Ta bort**
  - **Tillåt**
  - **Användardefinierad**
  - **Blockera**

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender antivirusundantag

- **Filer och mappar som ska undantas från genomsökningar och realtidsskydd**: Lägger till en eller flera filer och mappar, som t.ex. **C:\Path** eller **%ProgramFiles%\Path\filename.exe**, i undantagslistan. Dessa filer och mappar tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.
- **Filnamnstillägg som ska undantas från genomsökningar och realtidsskydd**: Lägg till ett eller flera filnamnstillägg, som t.ex. **jpg** eller **txt**, i undantagslistan. Filer med dessa filnamnstillägg tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.
- **Processer som ska undantas från genomsökningar och realtidsskydd**: Lägg till en eller flera processer av typen **.exe**, **.com** eller **.scr** i undantagslistan. Dessa processer tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.

## <a name="next-steps"></a>Nästa steg

Mer teknisk information om varje inställning och vilka utgåvor av Windows som stöds finns i [CSP-referens för Windows 10-princip](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)
