---
title: Lägga till slutpunktsskydd i Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: På Windows 10-enheter kan du använda eller konfigurera inställningar för slutpunktsskydd för att aktivera Windows Defender-funktionalitet, inklusive Application Guard, brandvägg, SmartScreen, kryptering och bitlocker, Exploit Guard, programreglering, Säkerhetscenter och säkerhet på lokala enheter i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 069f71d75c0a9c7cec083a929f89a2b39bb4aac5
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/03/2018
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Endpoint Protection-inställningar för Windows 10 och senare i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Med en Endpoint Protection-profil kan du konfigurera säkerhetsfunktioner, t.ex. BitLocker och Windows Defender för Windows 10-enheter.

Använd informationen i den här artikeln för att skapa Endpoint Protection-profiler. Information om att konfigurera Windows Defender Antivirus finns i [Enhetsbegränsningar för Windows 10](device-restrictions-windows-10.md#windows-defender-antivirus). 

> [!NOTE]
> De här inställningarna stöds inte av versionerna Home och Professional av Windows 10.

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

När du använder Microsoft Edge Windows Defender Application Guard skyddas din miljö från webbplatser som inte har definierats som betrodda av din organisation. När användare besöker webbplatser som inte listas i din isolerade nätverksgräns, öppnas webbplatserna i en virtuell session i Hyper-V. Betrodda webbplatser definieras av en nätverksgräns som kan konfigureras i enhetskonfigurationen. 

Application Guard är endast tillgängligt för Windows 10-enheter (64-bitars). Med den här profilen installeras en Win32-komponent för att aktivera Application Guard.

- **Application Guard**: Öppna ej godkända webbplatser i en virtualiserad Hyper-V-webbläsarbehållare.
- **Funktionssätt för Urklipp**: Välj vilka åtgärder för kopiera/klistra in som tillåts mellan den lokala datorn och den virtuella Application Guard-webbläsaren.
- **Externt innehåll på företagswebbplatser**: Blockera inläsning av innehåll från webbplatser som inte är godkända.
- **Skriv ut från virtuell webbläsare**: Tillåt att PDF- och XPS-skrivare, samt lokala skrivare och/eller nätverksskrivare skriver ut innehåll från den virtuella webbläsaren.
- **Samla in loggar**: Samla in loggar för händelser som inträffar i en Application Guard-webbläsarsession.
- **Behåll användargenererade webbläsardata**: Spara användardata (t.ex. lösenord, favoriter och cookies) som skapas under en virtuell Application Guard-webbläsarsession.
- **Grafikacceleration**: Läs in grafikintensiva webbplatser snabbare när du arbetar i en virtuell Application Guard-webbläsarsession. Webbplatser läses in snabbare genom åtkomst till en virtuell grafikprocessor.
- **Ladda ned filer till värdfilsystemet**: Låt användare ladda ned filer från den virtuella webbläsaren till värdoperativsystemet.

## <a name="windows-defender-firewall"></a>Windows Defender-brandvägg

### <a name="global-settings"></a>Globala inställningar

De här inställningarna avser alla nätverkstyper.

- **File Transfer Protocol**: Blockera tillståndskänslig FTP.
- **Inaktiv tid för säkerhetsassociation före borttagning**: Säkerhetsassociationer tas bort om ingen nätverkstrafik har identifierats under *n* sekunder.
- **I förväg delad nyckelkodning**: Koda i förväg delade nycklar med UTF-8.
- **IPsec-undantag**: Konfigurera specifik trafik som ska undantas från IPsec, t.ex. **Granne upptäcker koder av IPv6 ICMP-typ**, **ICMP**, **Router upptäcker koder av IPv6 ICMP-typ** och **Både IPv4- och IPv6 DHCP-nätverkstrafik**.
- **Verifiering av listan över återkallade certifikat**: Ange ett värde för hur listan över återkallade certifikat genomförs, inklusive **Inaktivera CRL-verifiering**, **CRL-verifiering misslyckas enbart för återkallade certifikat** och **CRL-verifiering misslyckas för alla påträffade fel**.
- **Matcha autentiseringsuppsättningarna per nyckelmodul**: Ange nyckelmoduler för att ignorera hela autentiseringsuppsättningen om de inte har stöd för alla autentiseringspaket i den uppsättningen.
- **Paketkö**: Ange hur programvaruskalning på mottagarsidan aktiveras för den krypterade mottagningen och rensa flyttning av text framåt för scenariot med IPsec-tunnelgatewayen. Denna inställning säkerställer att paketordningen bevaras.

### <a name="network-settings"></a>Nätverksinställningar

De här inställningarna gäller för specifika nätverkstyper, inklusive **Domännätverk (arbetsplats)**, **Privat (identifierbart) nätverk** och **Offentligt (inte identifierbart) nätverk**.

#### <a name="general-settings"></a>Allmänna inställningar

- **Windows Defender-brandvägg**: Aktivera den här inställningen för att blockera nätverkstrafik.
- **Dolt läge**: Hindra brandväggen från att arbeta i dolt läge. Om du blockerar dolt läge blockeras även **IPsec-skyddat paketundantag**.
- **Avskärmad**: Om du aktiverar den här inställningen blockerar brandväggsinställningen all inkommande trafik.
- **Unicast-svar på multicast-sändningar**: Blockera unicast-svar på multicast-sändningar. Normalt vill du inte ta emot unicast-svar på multicast- eller broadcast-meddelanden. Svaren kan indikera en DOS-attack (denial of service), eller en angripare som försöker avsöka en känd live-dator.
- **Inkommande meddelanden**: Blockera visning av meddelanden för användare när ett program har blockerats från att lyssna på en port.
- **Standardåtgärd för inkommande anslutningar**: Blockera standardåtgärden som brandväggen utför på inkommande anslutningar.

#### <a name="rule-merging"></a>Sammanslagning av regler

- **Auktoriserade Windows Defender-brandväggsregler från det lokala arkivet**: Tillåt att auktoriserade brandväggsregler i det lokala arkivet erkänns och framtvingas.
- **Globala Windows Defender-portbrandväggsregler från det lokala arkivet**: Tillåt att globala portbrandväggsregler i det lokala arkivet erkänns och framtvingas.
- **Windows Defender-brandväggsregler från det lokala arkivet**: Tillåt att globala brandväggsregler i det lokala arkivet erkänns och framtvingas.
- **IPSec-regler från det lokala arkivet**: Använd regler för anslutningssäkerhet från det lokala lagret, oavsett schema eller version av regler för anslutningssäkerhet.

## <a name="windows-defender-smartscreen-settings"></a>Inställningar för Windows Defender SmartScreen

- **SmartScreen för appar och filer**: Aktivera Windows SmartScreen för körning av filer och program som körs.
- **Körning av overifierade filer**: Blockera användaren från att köra filer som inte har verifierats av Windows SmartScreen.

## <a name="windows-encryption"></a>Windows-kryptering

### <a name="windows-settings"></a>Windows-inställningar

Följande två inställningarna gäller för alla versioner av Windows 10:

- **Kryptera enheter**: Om den här inställningen är aktiverad uppmanas användarna att aktivera enhetskryptering. Dessutom uppmanas de att bekräfta att kryptering från en annan provider inte har aktiverats. Om Windows-kryptering aktiveras samtidigt som en annan krypteringsmetod är aktiv, kan enheten bli instabil.
- **Kryptera minneskortet**: Aktivera den här inställningen för att kryptera flyttbara minneskort som används av enheten.


### <a name="bitlocker-base-settings"></a>Grundläggande BitLocker-inställningar

Grundläggande inställningar är universella BitLocker-inställningar för alla typer av dataenheter. Inställningarna för BitLocker-grupprincipen styr vilka enhetskrypteringsåtgärder eller konfigurationsalternativ som användaren kan ändra för alla typer av dataenheter.

- **Varning för annan hårddiskkryptering**: Inaktivera varningsmeddelandet för annan hårddiskkryptering på slutanvändarnas datorer.
- **Konfigurera krypteringsmetoder**: Aktivera den här inställningen för att konfigurera krypteringsalgoritmer för operativsystem, data och flyttbara enheter.
  - **Kryptering för operativsystemenheter**: Välj krypteringsmetod för operativsystemenheter. Vi rekommenderar att du använder XTS AES-algoritmen.
  - **Kryptering för fasta dataenheter**: Välj krypteringsmetod för fasta (inbyggda) dataenheter. Vi rekommenderar att du använder XTS AES-algoritmen.
  - **Kryptering för flyttbara dataenheter**: Välj krypteringsmetod för flyttbara dataenheter. Om den flyttbara enheten används med enheter som inte kör Windows 10, rekommenderar vi att du använder AES-CBC-algoritmen.

### <a name="bitlocker-os-drive-settings"></a>BitLocker-inställningar för operativsystemenheten

Dessa inställningar gäller specifikt för operativsystemets dataenheter.

- **Ytterligare autentisering vid start**: Konfigurera autentiseringskrav för datorstart, inklusive användning av Trusted Platform Module (TPM).
  - **BitLocker med icke-kompatibelt TPM-chip**
  - **Kompatibel TPM-start**: Välj att tillåta, inte tillåta eller kräva TPM-chip.
  - **Kompatibel PIN-kod för TPM-start**: Välj att tillåta, inte tillåta eller kräva användning av en PIN-kod för start med TPM-chippet.
  - **Kompatibel nyckel för TPM-start**: Välj att tillåta, inte tillåta eller kräva användning av en nyckel för start med TPM-chippet.
  - **Kompatibel nyckel och PIN-kod för TPM-start**: Välj att tillåta, inte tillåta eller kräva användning av en nyckel och PIN-kod för start med TPM-chippet.
- **Minsta PIN-kodslängd**: Aktivera den här inställningen för att konfigurera en minsta längd för start-PIN-koden för TPM.
  - **Minsta tecken**: Ange antalet tecken som krävs för PIN-koden från, **4**-**20**.
- **Återställning av operativsystemenhet**: Aktivera den här inställningen för att ange hur BitLocker-skyddade operativsystemenheter återställs när nödvändig startinformation saknas.
  - **Certifikatbaserad dataåterställningsagent**: Aktivera den här inställningen om du vill att dataåterställningsagenter ska kunna användas med BitLocker-skyddade operativsystemenheter.
  - **Återställningslösenord skapat av användare**: Välj om får, måste eller inte får generera ett 48-siffrigt återställningslösenord.
  - **Återställningsnyckel skapad av användare**: Välj om får, måste eller inte får generera en 256-bitars återställningsnyckel.
  - **Återställningsalternativ i BitLocker-installationsguiden**: Aktivera den här inställningen om du vill hindra användare från att se och ändra återställningsalternativ när de aktiverar BitLocker.
  - **Spara BitLocker-återställningsinformation i AD DS**: Aktivera lagring av BitLocker-återställningsinformation i Active Directory.
  - **BitLocker-återställningsinformation lagrad i AD DS**: Konfigurera vilka delar av BitLocker-återställningsinformation som lagras i Active Directory. Välj mellan:
    - **Säkerhetskopiera återställningslösenord och nyckelpaket**
    - **Säkerhetskopiera endast återställningslösenord**
  - **Lagra återställningsinformation i AD DS innan BitLocker aktiveras**: Aktivera den här inställningen för att hindra användare från att aktivera BitLocker om enheten är ansluten till domänen och BitLocker-återställningsinformation har lagrats i Active Directory.
- **Återställningsmeddelande och webbadress i förstartsmiljö**: Aktivera den här inställningen för att konfigurera meddelandet och webbadressen som visas på förstartsskärmen för nyckelåterställning.
  - **Återställningsmeddelande i förstartsmiljö**: Konfigurera hur återställningsmeddelande i förstartsmiljö visas för användarna. Välj mellan:
    - **Använd standardvärde för återställningsmeddelande och webbadress**
    - **Använd tomt återställningsmeddelande och webbadress**
    - **Använd anpassat återställningsmeddelande**
    - **Använd anpassad återställningswebbadress**

### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker-inställningar för fasta dataenheter

- **Neka skrivåtkomst till fast dataenhet som inte skyddas av BitLocker**: Om den här inställningen aktiveras måste BitLocker-skyddet aktiveras på alla fasta eller inbyggda dataenheter för att det ska gå att skriva till dem.
- **Återställning av fast enhet**: Aktivera den här inställningen för att ange hur BitLocker-skyddade fasta enheter återställs när nödvändig startinformation saknas.
  - **Dataåterställningsagent**: Aktivera den här inställningen om du vill att dataåterställningsagenter som ska användas med BitLocker-skyddade fasta enheter.
  - **Återställningslösenord skapat av användare**: Konfigurera huruvida användare får, måste eller inte får generera ett 48-siffrigt återställningslösenord.  
  - **Återställningsnyckel skapad av användare**: Konfigurera huruvida användare får, måste eller inte får skapa en 256-bitars återställningsnyckel.
  - **Återställningsalternativ i BitLocker-installationsguiden**: Aktivera den här inställningen om du vill hindra användare från att se och ändra återställningsalternativ när de aktiverar BitLocker.
  - **Spara BitLocker-återställningsinformation i AD DS**: Aktivera lagring av BitLocker-återställningsinformation i Active Directory.
  - **BitLocker-återställningsinformation i AD DS**: Konfigurera vilka delar av BitLocker-återställningsinformation som lagras i Active Directory. Välj mellan:
    - **Säkerhetskopiera återställningslösenord och nyckelpaket**
    - **Säkerhetskopiera endast återställningslösenord**
  - **Lagra återställningsinformation i AD DS innan BitLocker aktiveras**: Aktivera den här inställningen för att hindra användare från att aktivera BitLocker om enheten är ansluten till domänen och BitLocker-återställningsinformation har lagrats i Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker-inställningar för flyttbara dataenheter

- **Skrivåtkomst till flyttbar dataenhet som inte skyddas av BitLocker**: Ange om BitLocker-kryptering krävs för flyttbara lagringsenheter.
  - **Skrivåtkomst till enheter som har ställts in i en annan organisation**: Ange om det går att skriva till flyttbara enheter som tillhör en annan organisation.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Använd [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) för att hantera och minska attackytan för appar som medarbetarna använder.

### <a name="attack-surface-reduction"></a>Minska attackytan

- **Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem**

Hjälp till att [förhindra åtgärder och appar](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) som normalt används av skadlig kod som söker sårbarheter för att angripa datorer.

#### <a name="rules-to-prevent-office-macro-threats"></a>Regler för att förhindra Office-makrohot

Blockera Office-appar från att vidta följande åtgärder:

- **Office-appar som infogar i andra processer (inga undantag)**
- **Office-appar/-makron som skapar körbart innehåll**
- **Office-appar som startar underordnade processer**
- **Win32-importer från Office-makrokod**

#### <a name="rules-to-prevent-script-threats"></a>Regler för att förhindra skripthot

Blockera följande för att hjälpa till att förhindra skripthot:

- **Dold js/vbs/ps/makrokod**
- **js/vbs kör nyttolaster som laddats ned från Internet (inga undantag)**
- **Skapa process från PSExec- och WMI-kommandon**
- **Ej betrodda och osignerade processer som körs via USB**
- **Körbara filer som inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista**

#### <a name="rules-to-prevent-email-threats"></a>Regler för att förhindra e-posthot

Blockera följande för att hjälpa till att förhindra e-posthot:

- **Körning av körbart innehåll (exe, dll, ps, js, vbs, osv.) som har tagits bort från e-post (webbaserad e-post/e-postklient) (inga undantag)**

#### <a name="rules-to-protect-against-ransomware"></a>Regler för skydd mot utpressningstrojaner
- **Avancerat skydd mot utpressningstrojaner**

> [!TIP]
> [Reduce attack surfaces with Windows Defender Exploit Guard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) (Minska attackytorna med Windows Defender Exploit Guard) innehåller mer information om dessa regler.

#### <a name="attack-surface-reduction-exceptions"></a>Undantag för att minska attackytan

- **Filer och mappar som ska uteslutas från reglerna för att minska attackytan**: Importera/lägg till en lista över platser som ska uteslutas från de konfigurerade reglerna.

### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

Hjälp till att skydda värdefulla data från skadliga appar och hot, till exempel utpressningstrojaner.

- **Mappskydd**: Skydda filer och mappar från oönskade ändringar som görs av skadliga appar. Du kan importera en **lista över appar som har åtkomst till skyddade mappar** eller lägga till dem manuellt. Du kan även lägga till en **lista över ytterligare mappar som behöver skyddas** genom en överföring, eller lägga till dem manuellt.

### <a name="network-filtering"></a>Nätverksfiltrering

Blockera utgående anslutningar från alla appar till IP-adresser/domäner med dåligt rykte.

### <a name="exploit-protection"></a>Sårbarhetsskydd

Blockera **användarredigering av gränssnittet för sårbarhetsskydd** genom att överföra en XML-fil som tillåter att du konfigurerar minne, kontrollflöde och principbegränsningar. Inställningarna i XML-filen kan användas för att blockera ett program från kryphål.

Aktivera skydd av sårbarheter genom att skapa en XML-fil som representerar systemet och de inställningar för programminskning som du önskar. Du kan använda någon av dessa två metoder för att göra detta:

 1. PowerShell: Använd en eller flera av Get-ProcessMitigation-, Set-ProcessMitigation- och ConvertTo-ProcessMitigationPolicy PowerShell-cmdlets. Cmdlets konfigurerar åtgärdsinställningar och exporterar en XML-representation av dem.

 2. Gränssnittet för Windows Defender Säkerhetscenter: I Windows Defender Säkerhetscenter klickar du på App- & webbläsarkontroll och bläddrar sedan längst ned på skärmen för att hitta Sårbarhetsskydd. Använd först flikarna Systeminställningar och Programinställningar för att konfigurera minskningsinställningar. Leta sedan reda på länken Exportera inställningar längst ned på skärmen för att exportera en XML-återgivning av dem.

## <a name="windows-defender-application-control"></a>Windows Defender Application Control

Använd **Kodintegritetsprinciper för programkontroll** för att välja ytterligare appar som måste granskas av eller som kan vara betrodda att köras av Windows Defender Application Control. Windows-komponenter och alla appar från Windows Store är automatiskt betrodda att köras.

Program blockeras inte i läget **Endast granskning**. I läget **Endast granskning** loggas alla händelser i lokala klientloggar.

När det är aktiverat kan programkontrollen endast inaktiveras genom att ändra läget från **Framtvinga** till **Endast granskning**. Om du ändrar läget från **Framtvinga** till **Inte konfigurerad** fortsätter programkontrollen att tillämpas på tilldelade enheter.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard
Windows Defender Credential Guard skyddar mot attacker för stöld av autentiseringsuppgifter. Den isolerar hemligheter så att endast privilegierad programvara kan komma åt dem.

Inställningarna för **Credential Guard** inkluderar:

- **Inaktivera**: Stänger av Credential Guard via fjärranslutning om det tidigare har slagits på med alternativet **Aktivera utan UEFI-lås**.
- **Aktiverat med UEFI-lås**: Ser till att Credential Guard inte kan inaktiveras fjärrstyrt med en registernyckel eller grupprincip.

    > [!NOTE]
    > Om du använder den här inställningen och sedan vill inaktivera Credential Guard, måste du ange grupprincipen till **Inaktiverad**. Och avmarkera UEFI-konfigurationsinformationen fysiskt från varje dator. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.

- **Aktiverat utan UEFI-lås**: Medför att Credential Guard kan inaktiveras via fjärranslutning med grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 version 1511 eller senare.

När du aktiverar Credential Guard aktiveras även följande nödvändiga funktioner:

- **Virtualiseringsbaserad säkerhet** (VBS): Aktiveras vid nästa omstart. Virtualiseringsbaserad säkerhet använder Windows Hypervisor för att ge stöd för säkerhetstjänster.
- **Säker start med Directory Memory Access**: Aktiverar VBS med Säker start och DMA-skydd (Directory Memory Access). DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade.

## <a name="windows-defender-security-center"></a>Windows Defender Säkerhetscenter

Appen Windows Defender Security Center fungerar som en separat app eller process från var och en av de enskilda funktionerna. Den visar aviseringar via Action Center. Den fungerar som en insamlare eller enskild plats för att visa status och utföra konfiguration för var och en av funktionerna. Läs mer i dokumentationen till [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Appen Windows Defender Säkerhetscenter och meddelanden

Blockera slutanvändarens åtkomst till olika delar av appen Windows Defender Säkerhetscenter. Om ett avsnitt döljs blockeras även relaterade meddelanden.

- **Skydd mot virus och hot**
- **Enhetsprestanda och hälsa**
- **Brandväggs- och nätverksskydd**
- **App- och webbläsarkontroll**
- **Familjealternativ**
- **Aviseringar från områdena som visas i appen**: Välj vilka meddelanden som ska visas för slutanvändare. Meddelanden som är mindre viktiga omfattar sammanfattningar av Windows Defender Antivirus-aktivitet, inklusive meddelanden när genomsökningar har slutförts. Alla andra meddelanden anses viktiga.

#### <a name="it-contact-information"></a>IT-kontaktuppgifter

Ange IT-kontaktuppgifter som ska visas i appen Windows Defender Säkerhetscenter och i appmeddelanden. Du kan välja **Visa i app och i aviseringar**, **Visa endast i app**, **Visa endast i aviseringar** eller **Visa inte**. Du måste ange **IT-organisationens namn** och minst ett av följande kontaktalternativ:

- **IT-avdelningens telefonnummer eller Skype-ID**
- **IT-avdelningens e-postadress**
- **URL till IT-supportwebbplatsen**

## <a name="local-device-security-options"></a>Säkerhetsalternativ för lokal enhet

Använd dessa alternativ för att konfigurera de lokala säkerhetsinställningarna på Windows 10-enheter.

### <a name="accounts"></a>Konton

- **Lägg till nya Microsoft-konton**: Förhindrar att användare lägger till nya Microsoft-konton på den här datorn.
- **Fjärrinloggning utan lösenord**: Aktivera att lokala konton som inte är lösenordsskyddade kan att logga in från andra platser än den fysiska enheten.

#### <a name="admin"></a>Administratör

- **Lokalt administratörskonto**: Avgör om det lokala administratörskontot är aktiverat eller inaktiverat.
- **Byt namn på administratörskonto**: Definiera att ett annat kontonamn ska associeras med säkerhetsidentifieraren (SID) för administratörskontot.

#### <a name="guest"></a>Gäst

- **Gästkontot**: Avgör om gästkontot är aktiverat eller inaktiverat.
- **Byt namn på gästkonto**: Definiera att ett annat kontonamn ska associeras med säkerhetsidentifieraren (SID) för gästkontot.

### <a name="devices"></a>Egenskaper

- **Koppla bort enhet från dockningsstation utan inloggning**: Förhindra att en bärbar dator kopplas bort från dockningsstationen utan att behöva logga in.
- **Installera skrivardrivrutiner för delade skrivare**: Begränsa installation av skrivardrivrutiner som en del av anslutningen till en delad skrivare till administratörer.
- **Begränsa CD-ROM-åtkomsten till lokala aktiva användare**: Om du aktiverar den här inställningen kan endast interaktivt inloggade användare komma åt CD-ROM-media
- **Formatera och mata ut flyttbar media**: Definiera vem som får formatera och mata ut flyttbar NTFS-media:
  - **Inte konfigurerat**
  - **Administratörer och privilegierade användare**
  - **Administratörer och interaktiva användare**

### <a name="interactive-logon"></a>Interaktiv inloggning

- **Minuter av låsskärmsinaktivitet innan skärmsläckaren aktiveras**: Definiera högsta antal minuter av inaktivitet på det interaktiva skrivbordets inloggningsskärm tills skärmsläckaren aktiveras.
- **Kräv CTRL+ALT+DEL för att logga in**: Kräv att CTRL+ALT+DEL trycks ned innan en användare kan logga in.
- **Beteende vid borttagning av smartkort**: Avgör vad som händer när smartkortet för en inloggad användare tas bort från smartkortsläsaren.
[Alternativ för LocalPoliciesSecurity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) innehåller mer information.

#### <a name="display"></a>Visning

- **Användarinformation på låsskärmen**: Konfigurera användarinformation som visas när sessionen är låst. Om inställningen inte konfigureras visas användarens visningsnamn, domän och användarnamn.
  - **Endast användarens visningsnamn**
  - **Visa inte användarinformation**
  - **Inte konfigurerad**: Användarens visningsnamn, domän och användarnamn
- **Dölj senast inloggade användare**: Visa inte användarnamnet för den senaste personen som loggat in på den här enheten.
- **Dölj användarnamn vid inloggning**: Visa inte användarnamnet för personen som loggar in på den här enheten när autentiseringsuppgifter har angetts och innan enhetens skrivbord visas.
- **Meddelanderubrik vid inloggning**: Ställ in meddelanderubrik för användare som försöker logga in.
- **Meddelandetext vid inloggning**: Ställ in meddelandetext för användare som försöker logga in.

### <a name="network-access-and-security"></a>Åtkomst till nätverket och säkerhet

- **Anonym åtkomst till namngivna pipes och resurser**: Begränsas anonym åtkomst till resurs- och namngivna pipe-inställningar. Gäller för de inställningar som kan användas anonymt.
- **Anonym uppräkning av SAM-konton**: Tillåter att anonyma användare kan räkna upp SAM-konton. Windows låter anonyma användare räkna upp namn på domänkonton och nätverksresurser.
- **Anonym uppräkning av SAM-konton och resurser**: Blockera anonym uppräkning av SAM-konton och resurser. Windows låter anonyma användare räkna upp namn på domänkonton och nätverksresurser.
- **LAN Manager-hashvärdet lagras vid ändring av lösenord**: Välj om hashvärdet för LAN Manager (LM) för det nya lösenordet ska lagras vid nästa lösenordsändring. Det lagras inte som standard.
- **PKU2U-autentiseringsbegäranden**: Blockera PKU2U-autentiseringsbegäranden till den här enheten för att använda online-identiteter.
- **Begränsa RPC-fjärranslutningar till SAM**: Redigera standardsträngen för Security Descriptor Definition Language om du vill tillåta eller neka användare och grupper att göra fjärranrop till SAM.
- **Säkerhetsbeskrivning**

### <a name="recovery-console-and-shutdown"></a>Återställningskonsol och avstängning

- **Rensa virtuell växlingsfil när du stänger**: Rensa den virtuella växlingsfilen när enheten stängs av.
- **Avstängning utan inloggning**: Blockera alternativet för att stänga av datorn från Windows-inloggningsskärmen. I det här fallet måste användare kunna logga in på datorn korrekt innan de kan utföra en systemavstängning.

### <a name="user-account-control"></a>User account control

- **UIA-integritet utan säker plats**: Aktivera appar från oskyddade platser i filsystemet för att köra med UIAccess-integritetsnivå.
- **Virtualisera fil- och registerskrivfel till platser per användare**: Avgör om appens skrivfel omdirigeras till definierade register- och filsystemplatser. Eller orsaka att appen misslyckas.
- **Utöka endast behörighet för körbara filer som har signerats och verifierat**: Tvinga PKI-certifikatverifiering av en körbar fil innan den kan köras.

#### <a name="uia-elevation-prompt-behavior-settings"></a>Beteende vid UIA:s fråga om utökad behörighet

- **Fråga om utökade privilegier för administratörer**: Definiera funktionssätt för fråga om utökade privilegier för administratörer i 	Läge för administratörstillåtelse:
  - **Utöka privilegier utan att fråga**
  - **Fråga efter autentiseringsuppgifter på det skyddade skrivbordet**
  - **Fråga efter medgivande på det skyddade skrivbordet**
  - **Fråga efter autentiseringsuppgifter**
  - **Fråga efter medgivande**
  - **Inte konfigurerad**: Fråga efter medgivande för binärfiler som inte är Windows
- **Fråga om utökade privilegier för standardanvändare**: Definiera funktionssätt för fråga om utökade privilegier för standardanvändare:
  - **Neka förfrågningar om höjd behörighet automatiskt**
  - **Fråga efter autentiseringsuppgifter på det skyddade skrivbordet**
  - **Inte konfigurerad**: Fråga efter autentiseringsuppgifter
- **Vidarebefordra frågor om utökade privilegier till användarens interaktiva skrivbord**: Aktivera alla frågor om utökade privilegier att gå till den interaktiva användarens skrivbord i stället för det skyddade skrivbordet. Principinställningar för beteende vid fråga om utökad behörighet för administratörer och standardanvändare används.
- **Fråga om utökad behörighet för appinstallationer**: Installationer av appar som kräver utökade privilegier frågar efter autentiseringsuppgifter för administratör.
- **Fråga från UIA om utökad behörighet utan skyddat skrivbord**: Tillåt UIAccess-program att fråga om utökade privilegier utan att använda skyddat skrivbord.

#### <a name="admin-approval-mode-settings"></a>Inställningar för Läge för administratörstillåtelse

- **Läge för administratörstillåtelse för inbyggd administratör**: Definierar om det inbyggda administratörskontot använder läge för administratörstillåtelse eller kör alla appar med fullständiga administratörsprivilegier.
- **Kör alla administratörer i läge för administratörstillåtelse**: Definiera om läge för administratörstillåtelse och alla UAC-principinställningar är aktiverade.

### <a name="microsoft-network-client"></a>Microsoft-nätverksklient

- **Signera kommunikationer digitalt (om servern tillåter)**: Avgör om SMB-klienten försöker att förhandla signering av SMB-paket. När aktiverad (standard), ber Microsoft-nätverksklienten servern att utföra SMB-paketsignering under installationen av sessionen. Om paketsignering har aktiverats på servern, förhandlas paketsignering. Om principen är inaktiverad förhandlar SMB-klienten aldrig SMB-paketsignering.
- **Skicka okrypterade lösenord till SMB-servrar från tredje part**: När aktiverat, tillåts SMB-omdirigeraren (Server Message Block) att skicka lösenord till SMB-servrar som inte har stöd för kryptering av lösenord under autentiseringen.

### <a name="microsoft-network-server"></a>Microsoft-nätverksserver

- **Signera kommunikation digitalt (om klienten tillåter)**: Anger om SMB-servern förhandlar SNB-paketsignering med klienter som begär det. När aktiverad förhandlar Microsoft-nätverksservern SMB-paketsignering såsom begärs av klienten. D.v.s. om paketsignering är aktiverat på servern, förhandlas paketsignering. När inaktiverad (standar) förhandlar SMB-klienten aldrig SMB-paketsignering.
- **Signera kommunikation digitalt (alltid)**: Anger om paketsignering krävs av SMB-serverkomponenten. När aktiverat, kommunicerar Microsoft-nätverksservern inte med en Microsoft-nätverksklient såvida inte klienten godkänner att signera SMB-paket. När inaktiverad (standard), förhandlas SMB-paketsignering mellan klienten och servern.

## <a name="next-steps"></a>Nästa steg

Information om hur du tilldelar den här profilen till grupper finns i [Tilldela enhetsprofiler](device-profile-assign.md).
