---
title: Skyddsinställningar för Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: På Windows 10-enheter kan du använda eller konfigurera inställningar för slutpunktsskydd för att aktivera Windows Defender-funktionalitet, inklusive Application Guard, brandvägg, SmartScreen, kryptering och bitlocker, Exploit Guard, programreglering, Säkerhetscenter och säkerhet på lokala enheter i Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c2df888e146a7f240530e5cbc6628dbce34cb61
ms.sourcegitcommit: b0b1030017e741d92c508130447a8242d9ad7a51
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58343005"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Inställningar för Windows 10 (och senare) för att skydda delade enheter med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune innehåller många inställningar som skyddar dina enheter. Den här artikeln beskriver alla inställningar du kan aktivera och kon i Windows 10 och nyare enheter. Dessa inställningar skapas i en konfigurationsprofil för slutpunktsskydd i Intune för att kontrollera säkerheten, inklusive BitLocker och Windows Defender.

Information om att konfigurera Windows Defender Antivirus finns i [Enhetsbegränsningar för Windows 10](device-restrictions-windows-10.md#windows-defender-antivirus).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil för slutpunktsskydd](endpoint-protection-configure.md).

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Stöds i följande Windows 10-versioner:

- Företag
- Professionell

När du använder Microsoft Edge Windows Defender Application Guard skyddas din miljö från webbplatser som inte är betrodda av din organisation. När användare besöker webbplatser som inte listas i din isolerade nätverksgräns, öppnas webbplatserna i en virtuell webbläsarsession i Hyper-V. Betrodda webbplatser definieras av en nätverksgräns som konfigureras i enhetskonfigurationen.

Application Guard är endast tillgängligt för Windows 10-enheter (64-bitars). Med den här profilen installeras en Win32-komponent för att aktivera Application Guard.

- **Application Guard**: **Aktiverat för Edge** för att aktivera den här funktionen, som öppnar ej betrodda webbplatser i en virtualiserad Hyper-V-webbläsarcontainer. **Inte konfigurerad** (standard) innebär att en plats (betrodda och ej betrodda) öppnas på enheten.
- **Funktionssätt för Urklipp**: Välj vilka åtgärder för kopiera/klistra in som tillåts mellan den lokala datorn och den virtuella Application Guard-webbläsaren.
- **Externt innehåll på företagswebbplatser**: **Blockera** inläsning av innehåll från webbplatser som inte är godkända. **Inte konfigurerad** (standard) innebär att icke-företagswebbplatser kan öppnas på enheten.
- **Skriv ut från virtuell webbläsare**: Välj **Tillåt** så att PDF- och XPS-skrivare samt lokala skrivare och nätverksskrivare kan skriva ut innehåll från den virtuella webbläsaren. **Inte konfigurerad** (standard) inaktiverar alla utskriftsfunktioner.
- **Samla in loggar**: **Tillåt** för att samla in loggar för händelser som inträffar i en Application Guard-webbläsarsession. **Inte konfigurerad** (standard) samlar inte in några loggar inom webbläsarsessionen.
- **Behåll användargenererade webbläsardata**: **Tillåt** sparar användardata (till exempel lösenord, favoriter och cookies) som skapas under en virtuell Application Guard-webbläsarsession. **Inte konfigurerad** (standard) tar bort filer och data som laddats ned av en användare när enheten startas om eller när användaren loggar ut.
- **Grafikacceleration**: Välj **Aktivera** för att läsa in grafikintensiva webbplatser och video snabbare genom att ge åtkomst till en virtuell grafikprocessor. **Inte konfigurerad** (standard) använder enhetens CPU för grafik och använder alltså inte den virtuella grafikprocessorn.
- **Ladda ned filer till värdfilsystemet**: **Aktivera** så att användare laddar ned filer från den virtuella webbläsaren till värdoperativsystemet. **Inte konfigurerad** (standard) håller filerna lokala på enheten och laddar inte ned filer till värdfilsystemet.

## <a name="windows-defender-firewall"></a>Windows Defender-brandvägg

Stöds i följande Windows 10-versioner:
- Hem
- Professionell
- Företag
- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise

### <a name="global-settings"></a>Globala inställningar

De här inställningarna avser alla nätverkstyper.

- **File Transfer Protocol**: **Blockera** för att inaktivera tillståndskänslig FTP. När det här är **Inte konfigurerad** (standard) utför brandväggen tillståndskänslig FTP-filtrering för att tillåta sekundära anslutningar.
- **Inaktiv tid för säkerhetsassociation före borttagning**: Säkerhetsassociationer tas bort om ingen nätverkstrafik har identifierats under *n* sekunder. Ange en inaktivitetstid i sekunder.
- **Kodning av i förväg delad nyckel**: Välj **Aktivera** för att använda kodning av i förväg delad nyckel med hjälp av UTF-8. **Inte konfigurerad** (standard) använder det lokala arkivvärdet.
- **IPsec-undantag**: Konfigurera att specifik trafik ska undantas från IPsec, inklusive:
  - **Granne upptäcker koder av IPv6 ICMP-typ**
  - **ICMP**
  - **Router upptäcker koder av IPv6 ICMP-typ**
  - **Både IPv4 och IPv6 DHCP-nätverkstrafik**
- **Certifikat listan över återkallade**: Välj hur enheten kontrollerar listan över återkallade certifikat. Alternativen är **Inaktivera CRL-verifiering**, **CRL-verifiering misslyckas enbart för återkallade certifikat** och **CRL-verifiering misslyckas för alla påträffade fel**.
- **Matcha autentiseringsuppsättningarna per nyckelmodul**: **Aktivera** så att nyckelmoduler MÅSTE ignorera endast de autentiseringspaket som de inte stödjer. När det här är **Inte konfigurerad** MÅSTE nyckelmoduler ignorera hela autentiseringsuppsättningen om de inte har stöd för alla autentiseringspaket som anges i uppsättningen.
- **Paketkö**: Ange hur programvaruskalning på mottagarsidan aktiveras för den krypterade mottagningen och rensa flyttning av text framåt för scenariot med IPsec-tunnelgatewayen. Denna inställning bekräftar att paketordningen bevaras.

### <a name="network-settings"></a>Nätverksinställningar

De här inställningarna gäller för specifika nätverkstyper, inklusive **Domännätverk (arbetsplats)**, **Privat (identifierbart) nätverk** och **Offentligt (inte identifierbart) nätverk**.

#### <a name="general-settings"></a>Allmänna inställningar  
- **Windows Defender-brandväggen**: Välj **Aktivera** för att aktivera brandväggen och avancerad säkerhet. **Inte konfigurerad** (standard) tillåter all nätverkstrafik oavsett eventuella andra principinställningar.
- **Dolt läge**: **Blockera** brandväggen från att arbeta i dolt läge. Om du blockerar dolt läge blockeras även **IPsec-skyddat paketundantag**. **Inte konfigurerad** (standard) gör så att brandväggen arbetar i dolt läge, vilket hjälper till att förhindra svar på avsökningsbegäranden.
- **Avskärmad**: **Blockera** inaktiverar den här funktionen. **Inte konfigurerad** (standard) aktiverar den här inställningen. När den här inställningen och Windows Defender-brandväggen är aktiverade blockeras all inkommande trafik, oavsett eventuella andra principinställningar.
- **Unicast-svar på multicast-sändningar**: När det här är inställt på **Blockera** inaktiverar det unicast-svar på multicast-sändningar. Normalt vill du inte ta emot unicast-svar på multicast- eller broadcast-meddelanden. Svaren kan indikera en DOS-attack (denial of service), eller en angripare som försöker avsöka en känd live-dator. **Inte konfigurerad** (standard) aktiverar den här inställningen.
- **Inkommande meddelanden**: När det här är inställt på **Blockera** döljer det meddelanden för användare när en app har blockerats från att lyssna på en port. **Inte konfigurerad** (standard) aktiverar den inställningen och kan visa ett meddelande till användare när en app blockeras från att lyssna på en port.
- **Standardåtgärd för inkommande anslutningar**: När det här är inställt på **Blockera** körs inte brandväggens standardåtgärd på inkommande anslutningar. När det här är inställt på **Inte konfigurerad** (standard) körs brandväggens standardåtgärd på inkommande anslutningar.

#### <a name="rule-merging"></a>Sammanslagning av regler

- **Auktoriserade Windows Defender-brandväggsregler från det lokala arkivet**: Välj **Aktivera** för att tillämpa brandväggsregler i det lokala arkivet så att de erkänns och framtvingas. När det här är **Inte konfigurerad** (standard) ignoreras reglerna för den auktoriserade programbrandväggen i det lokala arkivet och framtvingas inte.
- **Globala Windows Defender-portbrandväggsregler från det lokala arkivet**: Välj **Aktivera** för att tillämpa globala portbrandväggsregler i det lokala arkivet att erkännas och framtvingas. När det här är **Inte konfigurerad** (standard) ignoreras reglerna för de globala portbrandväggsreglerna i det lokala arkivet och framtvingas inte.
- **Windows Defender-brandväggsregler från det lokala arkivet**: Välj **Aktivera** för att tillämpa brandväggsregler i det lokala arkivet att erkännas och framtvingas. När det här är **Inte konfigurerad** (standard) ignoreras brandväggsreglerna från det lokala arkivet och framtvingas inte.
- **IPSec-regler från det lokala arkivet**: Välj **Aktivera** för att tillämpa regler för anslutningssäkerhet från det lokala arkivet, oavsett schema eller version av regler för anslutningssäkerhet. När det här är **Inte konfigurerad** (standard) ignoreras reglerna för anslutningssäkerhet från det lokala arkivet och framtvingas inte, oavsett schemaversion eller version av regler för anslutningssäkerhet.

## <a name="windows-defender-smartscreen-settings"></a>Inställningar för Windows Defender SmartScreen

Stöds i följande Windows 10-versioner med Microsoft Edge installerat:
- Hem
- Professionell
- Företag
- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise

**Inställningar**:

- **SmartScreen för appar och filer**: **Aktivera** Windows SmartScreen för körning av filer och program som körs. SmartScreen är en molnbaserad komponent mot nätfiske och skadlig kod. **Inte konfigurerad** (standard) inaktiverar SmartScreen.
- **Körning av overifierade filer**: **Blockera** slutanvändare från att köra filer som inte har verifierats av Windows SmartScreen. **Inte konfigurerad** (standard) inaktiverar den här funktionen och tillåter att slutanvändare kör filer som inte har verifierats.

## <a name="windows-encryption"></a>Windows-kryptering

### <a name="windows-settings"></a>Windows-inställningar

Stöds i följande Windows 10-versioner:

- Professionell
- Företag
- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise

**Inställningar**:

- **Kryptera enheter**: **Kräv** för att uppmana användare att aktivera enhetskryptering. Beroende på Windows-version och systemkonfiguration kan användare uppmanas att:  
  - Bekräfta att kryptering från en annan provider inte är aktiverat
  - Inaktivera Bitlocker-diskkryptering och sedan aktivera Bitlocker igen
    
    Om Windows-kryptering aktiveras samtidigt som en annan krypteringsmetod är aktiv, kan enheten bli instabil. 
- **Kryptera minneskort (endast mobil)**: **Kräv** för att kryptera flyttbara minneskort som används av enheten. **Inte konfigurerad** (standard) kräver inte kryptering av minneskort och uppmanar inte användaren att aktivera det. Den här inställningen gäller endast mobila enheter med Windows 10.

### <a name="bitlocker-base-settings"></a>Grundläggande BitLocker-inställningar

Stöds i följande Windows 10-versioner:

- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise
- Professionell

Grundläggande inställningar är universella BitLocker-inställningar för alla typer av dataenheter. De här inställningarna styr vilka enhetskrypteringsåtgärder eller konfigurationsalternativ som användaren kan ändra för alla typer av dataenheter.

- **Varning för annan hårddiskkryptering**: Välj **Blockera** för att inaktivera varningsmeddelandet om en annan tjänst för hårddiskkryptering finns på enheten. **Inte konfigurerad** (standard) tillåter att varningarna visas.
    - **Tillåt vanliga användare att aktivera kryptering under Azure AD Join**: när du väljer **Tillåt**, standard användare/icke-administratörer kan aktivera BitLocker-kryptering när användaren är inloggad. Den här inställningen gäller bara för Azure Active Directory-anslutna enheter. **Inte konfigurerad** tillåter endast att administratörer aktiverar BitLocker-kryptering på enheten.
      
      Den här inställningen gäller bara för Azure Active Directory-anslutna enheter. Det krävs också att inställningen **Varning för annan hårddiskkryptering** anges till **Blockera**.
- **Konfigurera krypteringsmetoder**: **Aktivera** den här inställningen för att konfigurera krypteringsalgoritmer för operativsystem, data och flyttbara enheter. När det här är **Inte konfigurerad** (standard) använder BitLocker 128-bitars XTS-AES som standardkrypteringsmetod eller använder den krypteringsmetod som anges av något installationsskript.
  - **Kryptering för operativsystemenheter**: Välj krypteringsmetod för operativsystemenheter. Vi rekommenderar att du använder XTS AES-algoritmen.
  - **Kryptering för fasta dataenheter**: Välj krypteringsmetod för fasta (inbyggda) dataenheter. Vi rekommenderar att du använder XTS AES-algoritmen.
  - **Kryptering för flyttbara dataenheter**: Välj krypteringsmetod för flyttbara dataenheter. Om den flyttbara enheten används med enheter som inte kör Windows 10 rekommenderar vi att du använder AES-CBC-algoritmen.

### <a name="bitlocker-os-drive-settings"></a>BitLocker-inställningar för operativsystemenheten
Stöds i följande Windows 10-versioner:

- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise
- Professionell

Dessa inställningar gäller specifikt för operativsystemets dataenheter.

- **Ytterligare autentisering vid start**: Välj **Kräv** för att konfigurera autentiseringskraven för datorstart, inklusive användning av Trusted Platform Module (TPM). Välj **Inte konfigurerad** (standard) för att konfigurera endast grundläggande alternativ på enheter med en TPM.
  - **BitLocker med icke-kompatibelt TPM-chip**: **Blockera** (inaktivera) användning av BitLocker när en enhet inte har ett kompatibelt TPM-chip. När det här är **Inte konfigurerad** kan användare använda BitLocker utan ett kompatibelt TPM-chip. BitLocker kan kräva ett lösenord eller en startnyckel.
  - **Kompatibel TPM-start**: Välj att tillåta, inte tillåta eller kräva TPM-chip.
  - **Kompatibel PIN-kod för TPM-start**: Välj att tillåta, inte tillåta eller kräva användning av en PIN-kod för start med TPM-chippet. För att aktivera en PIN-kod för start krävs interaktion från slutanvändaren. 
  - **Kompatibel nyckel för TPM-start**: Välj att tillåta, inte tillåta eller kräva användning av en nyckel för start med TPM-chippet. För att aktivera en startnyckel krävs interaktion från slutanvändaren. 
  - **Kompatibel nyckel och PIN-kod för TPM-start**: Välj att tillåta, inte tillåta eller kräva användning av en nyckel och PIN-kod för start med TPM-chippet. För att aktivera en startnyckel och en PIN-kod krävs interaktion från slutanvändaren.
- **Minsta PIN-kodslängd**: **Aktivera** den här inställningen för att konfigurera en minsta längd för start-PIN-koden för TPM. När det här är **Inte konfigurerad** (standard) kan användare konfigurera en PIN-kod för start med valfri längd mellan 6 och 20 siffror.
  - **Minsta tecken**: Ange antalet tecken som krävs för PIN-koden från, **4**-**20**.
- **Återställning av operativsystemenhet**: **Aktivera** den här inställningen för att kontrollera hur BitLocker-skyddade operativsystemenheter återställs när nödvändig startinformation saknas. När det här är **Inte konfigurerad** (standard) stöds standardåterställningsalternativen för BitLocker-återställning. Som standard tillåts en DRA, återställningsalternativen väljs av användaren, inklusive återställningslösenordet och återställningsnyckeln och återställningsinformation säkerhetskopieras inte till AD DS.
  - **Certifikatbaserad dataåterställningsagent**: När det här är inställt på **Blockera** kan du inte använda dataåterställningsagent med BitLocker-skyddade operativsystemenheter. Ställ in på **Inte konfigurerad** (standard) för att aktivera den här inställningen, som tillåter att dataåterställningsagenter används med BitLocker-skyddade operativsystemenheter.
  - **Återställningslösenord skapat av användare**: Välj om får, måste eller inte får generera ett 48-siffrigt återställningslösenord.
  - **Återställningsnyckel skapad av användare**: Välj om får, måste eller inte får generera en 256-bitars återställningsnyckel.
  - **Återställningsalternativ i BitLocker-installationsguiden**: Ställ in på **Blockera** så att användarna inte kan se och ändra återställningsalternativen. När värdet är inställt på **Inte konfigurerad** (standard) kan användarna se och ändra återställningsalternativ när de aktiverar BitLocker.
  - **Spara BitLocker-återställningsinformation i AD DS**: Välj **Aktivera** för att lagra BitLocker-återställningsinformationen i Azure Active Directory (AAD). När det här är **Inte konfigurerad** (standard) lagras inte återställningsinformationen i AAD.
  - **BitLocker-återställningsinformation lagrad i AD DS**: Konfigurera vilka delar av BitLocker-återställningsinformation som lagras i Azure AD. Välj mellan:
    - **Säkerhetskopiera återställningslösenord och nyckelpaket**
    - **Säkerhetskopiera endast återställningslösenord**
  - **Lagra återställningsinformation i AD DS innan BitLocker aktiveras**: **Kräv** den här inställningen för att hindra användare från att aktivera BitLocker såvida inte BitLocker-återställningsinformation har lagrats i Azure Active Directory (AAD). **Inte konfigurerad** (standard) tillåter att användare aktiverar BitLocker även om återställningsinformation inte har lagrats i Azure AD.
- **Återställningsmeddelande och webbadress i förstartsmiljö**: **Aktivera** den här inställningen för att konfigurera meddelandet och webbadressen som visas på förstartsskärmen för nyckelåterställning. **Inte konfigurerad** (standard) inaktiverar den här funktionen.
  - **Återställningsmeddelande i förstartsmiljö**: Konfigurera hur återställningsmeddelande i förstartsmiljö visas för användarna. Välj mellan:
    - **Använd standardvärde för återställningsmeddelande och webbadress**
    - **Använd tomt återställningsmeddelande och webbadress**
    - **Använd anpassat återställningsmeddelande**
    - **Använd anpassad återställningswebbadress**

### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker-inställningar för fasta dataenheter

Stöds i följande Windows 10-versioner:

- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise
- Professionell

**Inställningar**:

- **Skrivåtkomst till fast dataenhet som inte skyddas av BitLocker**: Ställ in på **Blockera** för att ge skrivskyddad åtkomst till dataenheter som inte är BitLocker-skyddade. När det här är **Inte konfigurerad** (standard) finns det läs- och skrivåtkomst till dataenheter som inte är BitLocker-skyddade.
- **Återställning av fast enhet**: **Aktivera** den här inställningen för att kontrollera hur BitLocker-skyddade fasta enheter återställs när nödvändig startinformation saknas. **Inte konfigurerad** (standard) inaktiverar den här funktionen.
  - **Dataåterställningsagent**: **Blockera** användning av dataåterställningsagent med principredigeraren för BitLocker-skyddade fasta enheter. **Inte konfigurerad** (standard) gör det möjligt att använda dataåterställningsagenter med BitLocker-skyddade fasta enheter.
  - **Återställningslösenord skapat av användare**: Konfigurera huruvida användare får, måste eller inte får generera ett 48-siffrigt återställningslösenord.  
  - **Återställningsnyckel skapad av användare**: Konfigurera huruvida användare får, måste eller inte får skapa en 256-bitars återställningsnyckel.
  - **Återställningsalternativ i BitLocker-installationsguiden**: Ställ in på **Blockera** så att användarna inte kan se och ändra återställningsalternativen. När värdet är inställt på **Inte konfigurerad** (standard) kan användarna se och ändra återställningsalternativ när de aktiverar BitLocker.
  - **Spara BitLocker-återställningsinformation i Azure Active Directory**: Välj **Aktivera** för att lagra BitLocker-återställningsinformationen i Azure Active Directory (Azure AD). När det här är **Inte konfigurerad** (standard) lagras inte återställningsinformationen i Azure AD.
  - **BitLocker-återställningsinformation lagrad i Azure Active Directory**: Konfigurera vilka delar av BitLocker-återställningsinformation som lagras i Azure AD. Alternativen är:
    - **Säkerhetskopiera återställningslösenord och nyckelpaket**
    - **Säkerhetskopiera endast återställningslösenord**
  - **Lagra återställningsinformation i Azure Active Directory innan BitLocker aktiveras**: **Kräv** den här inställningen för att hindra användare från att aktivera BitLocker såvida inte BitLocker-återställningsinformation har lagrats i Azure AD. **Inte konfigurerad** (standard) tillåter att användare aktiverar BitLocker även om återställningsinformation inte har lagrats i Azure AD.

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker-inställningar för flyttbara dataenheter

Stöds i följande Windows 10-versioner:

- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise
- Professionell

**Inställningar**:

- **Skrivåtkomst till flyttbar dataenhet som inte skyddas av BitLocker**: Ställ in på **Blockera** för att ge skrivskyddad åtkomst till dataenheter som inte är BitLocker-skyddade. När det här är **Inte konfigurerad** (standard) finns det läs- och skrivåtkomst till dataenheter som inte är BitLocker-skyddade.
  - **Skrivåtkomst till enheter som har ställts in i en annan organisation**: **Blockera** tillåter skrivbehörighet för enheter som har konfigurerats i en annan organisation. **Inte konfigurerad** (standard) nekar skrivåtkomst.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Stöds i följande Windows 10-versioner:

- Hem
- Professionell
- Företag
- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise

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

> [!IMPORTANT]
> Om du vill tillåta installation och körning av LOB-Win32-appar, bör skadlig inställningar undanta följande kataloger från att genomsökas:<p>
> **På X64 klientdatorer**:<br>
> *C:\Program filer (x86) \Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **På X86 klientdatorer**:<br>
> *C:\Program Files\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

Hjälp till att skydda värdefulla data från skadliga appar och hot, till exempel utpressningstrojaner.

- **Mappskydd**: Skydda filer och mappar från oönskade ändringar som görs av skadliga appar. Du kan importera en **lista över appar som har åtkomst till skyddade mappar** eller lägga till dem manuellt. Du kan även lägga till en **lista över ytterligare mappar som behöver skyddas** genom en överföring, eller lägga till dem manuellt.

### <a name="network-filtering"></a>Nätverksfiltrering

- **Nätverksskydd**: skyddar utgående anslutningar från alla appar till IP-adresser med dåligt rykte eller domäner. Avsikten är att skydda slutanvändarna från appar med åtkomst till nätfiske, utnyttja-som är värd för webbplatser och skadligt på Internet. Det förhindrar även att tredje parts webbläsare ansluter till farliga platser.

  Alternativen är:

  - **Inte konfigurerad** (standard) inaktiverar den här funktionen. Användare och appar blockeras från att ansluta till farliga domäner. Administratörer kan inte se den här aktiviteten i Windows Defender Security Center.
  - **Aktivera** aktiverar nätverksskydd, och blockerar användare och appar från att ansluta till farliga domäner. Administratörer kan se den här aktiviteten i Windows Defender Security Center.
  - **Endast granskning**: användare och appar blockeras från att ansluta till farliga domäner. Administratörer kan se den här aktiviteten i Windows Defender Security Center.

  [Defender/EnableNetworkProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

### <a name="exploit-protection"></a>Sårbarhetsskydd

För att använda skydd mot sårbarheter skapar du en XML-fil som innehåller de inställningar för system- och programminskning som du önskar. Det finns två metoder:

 1. PowerShell: Använd en eller flera av Get-ProcessMitigation-, Set-ProcessMitigation- och ConvertTo-ProcessMitigationPolicy PowerShell-cmdlets. Cmdlets konfigurerar åtgärdsinställningar och exporterar en XML-representation av dem.

 2. Gränssnittet för Windows Defender Säkerhetscenter: I Windows Defender Säkerhetscenter klickar du på App- & webbläsarkontroll och bläddrar sedan längst ned på skärmen för att hitta Sårbarhetsskydd. Använd först flikarna Systeminställningar och Programinställningar för att konfigurera minskningsinställningar. Leta sedan reda på länken Exportera inställningar längst ned på skärmen för att exportera en XML-återgivning av dem.

Blockera **användarredigering av gränssnittet för sårbarhetsskydd** genom att överföra en XML-fil som tillåter att du konfigurerar minne, kontrollflöde och principbegränsningar. Inställningarna i XML-filen kan användas för att blockera ett program från kryphål. **Inte konfigurerad** (standard) skickar inte ut en anpassad konfiguration. 

## <a name="windows-defender-application-control"></a>Windows Defender Application Control

Stöds i följande Windows 10-versioner:

**Hantering av mobilenheter (MDM)**: 
- Professionell
- Företag
- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise

**Grupprinciphantering**: 
- Företag

Använd **Kodintegritetsprinciper för programkontroll** för att välja ytterligare appar som granskas av eller som är betrodda att köras av Windows Defender Application Control. Windows-komponenter och alla appar från Windows Store är automatiskt betrodda att köras.

Program blockeras inte när de körs i läget **Endast granskning**. I läget **Endast granskning** loggas alla händelser i lokala klientloggar.

När det är aktiverat kan programkontrollen endast inaktiveras genom att ändra läget från **Framtvinga** till **Endast granskning**. Om du ändrar läget från **Framtvinga** till **Inte konfigurerad** fortsätter programkontrollen att tillämpas på tilldelade enheter.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard

Stöds i följande Windows 10-versioner:

- Företag

Windows Defender Credential Guard skyddar mot attacker för stöld av autentiseringsuppgifter. Den isolerar hemligheter så att endast privilegierad programvara kan komma åt dem.

Inställningarna för **Credential Guard** inkluderar:

- **Inaktivera**: Stänger av Credential Guard via fjärranslutning om det tidigare har slagits på med alternativet **Aktivera utan UEFI-lås**.

- **Aktivera med UEFI-lås**: Credential Guard kan inte inaktiveras fjärrstyrt med en registernyckel eller grupprincip.

    > [!NOTE]
    > Om du använder den här inställningen och sedan vill inaktivera Credential Guard, måste du ange grupprincipen till **Inaktiverad**. Och avmarkera UEFI-konfigurationsinformationen fysiskt från varje dator. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.

- **Aktivera utan UEFI-lås**: Tillåter att Credential Guard inaktiveras fjärrstyrt med hjälp av grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 version 1511 eller senare.

När du aktiverar Credential Guard aktiveras även följande nödvändiga funktioner:

- **Virtualiseringsbaserad säkerhet** (VBS): Aktiveras vid nästa omstart. Virtualiseringsbaserad säkerhet använder Windows Hypervisor för att ge stöd för säkerhetstjänster.
- **Säker start med Directory Memory Access**: Aktiverar VBS med Säker start och DMA-skydd (Directory Memory Access). DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade.

## <a name="windows-defender-security-center"></a>Windows Defender Säkerhetscenter

Stöds i följande Windows 10-versioner:

- Hem
- Professionell
- Företag
- Företag
- Utbildning
- Mobiltelefon
- Mobile Enterprise

Windows Defender Security Center fungerar som en separat app eller process från var och en av de enskilda funktionerna. Den visar aviseringar via Action Center. Den fungerar som en insamlare eller enskild plats för att visa status och köra konfiguration för var och en av funktionerna. Läs mer i dokumentationen till [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Appen Windows Defender Säkerhetscenter och meddelanden

Blockera slutanvändarens åtkomst till olika delar av appen Windows Defender Säkerhetscenter. Om ett avsnitt döljs blockeras även relaterade meddelanden.

- **Skydd mot virus och hot**
- **Enhetsprestanda och hälsa**
- **Brandväggs- och nätverksskydd**
- **App- och webbläsarkontroll**
- **Familjealternativ**
- **Aviseringar från områdena som visas i appen**: Välj vilka meddelanden som ska visas för slutanvändare. Meddelanden som är mindre viktiga omfattar sammanfattningar av Windows Defender Antivirus-aktivitet, inklusive meddelanden när genomsökningar har slutförts. Alla andra meddelanden anses viktiga.

#### <a name="it-contact-information"></a>IT-kontaktuppgifter

Ange IT-kontaktuppgifter som ska visas i appen Windows Defender Säkerhetscenter och i appmeddelanden. Du kan välja **Visa i app och i aviseringar**, **Visa endast i app**, **Visa endast i aviseringar** eller **Visa inte**. Ange **IT-organisationens namn** och minst ett av följande kontaktalternativ:

- **IT-avdelningens telefonnummer eller Skype-ID**
- **IT-avdelningens e-postadress**
- **URL till IT-supportwebbplatsen**

## <a name="local-device-security-options"></a>Säkerhetsalternativ för lokal enhet

Stöds i följande Windows 10-versioner:
 
- Hem
- Professionell
- Företag
- Företag
- Utbildning

Använd dessa alternativ för att konfigurera de lokala säkerhetsinställningarna på Windows 10-enheter.

### <a name="accounts"></a>Konton

- **Lägg till nya Microsoft-konton**: Ställ in på **Blockera** för att förhindra att användare lägger till nya Microsoft-konton på enheten. När det här är inställt på **Inte konfigurerad** (standard) kan användare använda Microsoft-konton på enheten.
- **Fjärrinloggning utan lösenord**: **Blockera** tillåter endast lokala konton med tomma lösenord att logga in med enhetens tangentbord. **Inte konfigurerad** (standard) tillåter att lokala konton med tomma lösenord loggar in från andra platser än den fysiska enheten.

#### <a name="admin"></a>Administratör

- **Lokalt administratörskonto**: Ställ in på **Aktiverat** för att tillåta det lokala administratörskontot. Ställ in på **Inte konfigurerad** (standard) för att inaktivera det lokala administratörskontot.
- **Byt namn på administratörskonto**: Definiera att ett annat kontonamn ska associeras med säkerhetsidentifieraren (SID) för administratörskontot.

#### <a name="guest"></a>Gäst

- **Gästkonto**: Ställ in på **Aktiverat** för att tillåta det lokala gästkontot. Ställ in på **Inte konfigurerad** (standard) för att inaktivera det lokala gästkontot.
- **Byt namn på gästkonto**: Definiera att ett annat kontonamn ska associeras med säkerhetsidentifieraren (SID) för gästkontot.

### <a name="devices"></a>Egenskaper

- **Koppla bort enhet från dockningsstation utan inloggning**: Ställ in på **Blockera** så att användarna kan trycka på den fysiska utmatningsknappen på en dockad bärbar enhet för att på ett säkert sätt koppla bort enheten. **Inte konfigurerad** (standard) kräver att användaren loggar in på enheten och får behörighet att koppla från enheten från dockningsstation.
- **Installera skrivardrivrutiner för delade skrivare**: När det här är **Aktiverat** kan alla användare installera en skrivardrivrutin som en del av anslutningen till en delad skrivare. När det här är **Inte konfigurerad** (standard) kan endast administratörer installera en skrivardrivrutin som en del av anslutningen till en delad skrivare.
- **Begränsa CD-ROM-åtkomsten till lokala aktiva användare**: När det här är **Aktiverat** kan endast den interaktivt inloggade användaren använda CD-ROM-media. Om den här principen är aktiverad och ingen är interaktivt inloggad används CD-ROM via nätverket. När det här är **Inte konfigurerad** (standard) kan vem som helst komma åt CD-ROM.
- **Formatera och mata ut flyttbar media**: Definiera vem som får formatera och mata ut flyttbar NTFS-media:
  - **Inte konfigurerat**
  - **Administratörer**
  - **Administratörer och privilegierade användare**
  - **Administratörer och interaktiva användare**

### <a name="interactive-logon"></a>Interaktiv inloggning

- **Minuter av låsskärmsinaktivitet innan skärmsläckaren aktiveras**: Ange högsta antal minuter av inaktivitet på det interaktiva skrivbordets inloggningsskärm tills skärmsläckaren startar.
- **Kräv CTRL+ALT+DEL för att logga in**: Ställ in på **Aktivera** så att användare inte måste trycka på CTRL+ALT+DEL för att logga in. Ställ in på **Inte konfigurerad** (standard) för att kräva att användarna trycker på CTRL+ALT+DEL innan de loggar in på Windows.
- **Beteende vid borttagning av smartkort**: Avgör vad som händer när smartkortet för en inloggad användare tas bort från smartkortsläsaren. Alternativen är:

  - **Låsa arbetsstationen**: arbetsstationen låses när smartkortet tas bort. Med det här alternativet kan användare lämna området, ta med sig smartkortet och fortfarande skydda sessionen.
  - **Framtvinga utloggning**: användaren loggas ut automatiskt när smartkortet tas bort.
  - **Koppla från om Remote Desktop Services-session**: om smartkortet tas bort så kopplas sessionen från utan att användaren loggas ut. Med det här alternativet kan användaren sätta i smartkortet och fortsätta sessionen senare, eller vid en annan dator med smartkortsläsare, utan att behöva logga in igen. Om sessionen är lokal fungerar den här principen precis som Lås arbetsstationen.

    [Alternativ för LocalPoliciesSecurity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) innehåller mer information.

#### <a name="display"></a>Visning

- **Användarinformation på låsskärmen**: Konfigurera användarinformation som visas när sessionen är låst. Om inställningen inte konfigureras visas användarens visningsnamn, domän och användarnamn.
  - **Inte konfigurerat**  
  - **Användarens visningsnamn, domän och användarnamn**
  - **Endast användarens visningsnamn**
  - **Visa inte användarinformation**
- **Dölj senast inloggade användare**: **Aktivera** döljer användarnamnet. **Inte konfigurerad** (standard) visar användarnamnet.
- **Dölj användarnamn vid inloggning**: **Aktivera** döljer användarnamnet. **Inte konfigurerad** (standard) visar användarnamnet.
- **Meddelanderubrik vid inloggning**: Ställ in meddelanderubrik för användare som loggar in.
- **Meddelandetext vid inloggning**: Ställ in meddelandetext för användare som loggar in.

### <a name="network-access-and-security"></a>Åtkomst till nätverket och säkerhet

- **Anonym åtkomst till namngivna pipes och resurser**: Med **Inte konfigurerat** (standardinställning) begränsas anonym åtkomst till resurs- och namngivna pipe-inställningar. Gäller för de inställningar som kan användas anonymt.
- **Anonym uppräkning av SAM-konton**: **Tillåter** att anonyma användare kan räkna upp SAM-konton. Windows låter anonyma användare räkna upp namn på domänkonton och nätverksresurser.
- **Anonym uppräkning av SAM-konton och resurser**: **Inte konfigurerat** (standardinställning) innebär att anonyma användare kan räkna upp namn på domänkonton och nätverksresurser. Använd **Blockera** för att inte tillåta anonym uppräkning av SAM-konton och resurser.
- **LAN Manager-hashvärdet lagras vid ändring av lösenord**: Välj det här om du vill **tillåta** att hashvärdet för LAN Manager (LM) för det nya lösenordet ska lagras vid nästa lösenordsändring. Om det här är inställt på **Inte konfigurerad** (standardinställning) lagras inte hash-värdet.
- **PKU2U-autentiseringsförfrågningar**: **Blockera** PKU2U-autentiseringsbegäranden till den här enheten för att använda online-identiteter. **Inte konfigurerat** (standardinställning) tillåter dessa förfrågningar.
- **Begränsa RPC-fjärranslutningar till SAM**: inställt på **Tillåt** att neka användare och grupper från fjärranslutna RPC-anrop till konton Manager SAM (Security), som lagrar användarkonton och lösenord. **Tillåt** också kan du ändra standardsträngen som uttryckligen tillåter eller nekar användare och grupper för att göra dessa fjärranrop Security Descriptor Definition Language (SDDL). **Inte konfigurerad** (standard) använder säkerhetsbeskrivningen för standard och kan tillåta användare och grupper att göra fjärranrop till hanteraren för Kontosäkerhet RPC.
  - **Säkerhetsbeskrivning**

### <a name="recovery-console-and-shutdown"></a>Återställningskonsol och avstängning

- **Rensa virtuell växlingsfil när du stänger**: Ställ in på **Aktivera** för att rensa den virtuella växlingsfilen när enheten stängs av. **Inte konfigurerad** rensar inte det virtuella minnet.
- **Stäng av utan inloggning**: **Blockera** döljer avstängningsalternativet på Windows-inloggningsskärmen. Användarna måste logga in på enheten och sedan stänga av den. **Inte konfigurerad** (standard) tillåter att användare stänger av enheten från Windows-inloggningsskärmen.

### <a name="user-account-control"></a>User account control

- **UIA-integritet utan säker plats**: När det här är inställt på **Blockera** körs appar som finns på en skyddad plats i filsystemet endast med UIAccess-integritet. **Inte konfigurerad** (standard) gör att appar kan köras med UIAccess-integritet även om apparna inte finns på en säker plats i filsystemet.
- **Virtualisera fil- och registerskrivfel till platser per användare**: när **aktiverad**, program som skriver data till skyddade platser misslyckas. När värdet **inte konfigurerad** (standard), skriva application omdirigeras vid körningstiden på definierade användarplatser för filsystem och register.
- **Utöka endast behörighet för körbara filer som har signerats och verifierat**: Ställ in på **Aktiverat** för att framtvinga verifiering av PKI-certifikatsökväg för en körbar fil innan den kan köras. Ställ in på **Inte konfigurerad** (standard) för att inte framtvinga verifiering av PKI-certifikatsökväg innan en körbar fil kan köras.

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
- **Vidarebefordra frågor om utökade privilegier till användarens interaktiva skrivbord**: **Aktivera** så att alla frågor om utökade privilegier går till den interaktiva användarens skrivbord i stället för det skyddade skrivbordet. Eventuella principinställningar för beteende vid fråga om utökad behörighet för administratörer och standardanvändare används. **Inte konfigurerad** (standard) framtvingar att alla förfrågningar om höjd behörighet går till det skyddade skrivbordet oavsett eventuella principinställningar för beteende vid fråga om utökad behörighet för administratörer och standardanvändare.
- **Fråga om utökad behörighet för appinstallationer**: När det här är inställt på **Aktiverat** identifieras inte paket för programinstallation och uppmanas inte om utökade behörigheter. När det här är inställt på **Inte konfigurerad** (standard) uppmanas användaren att ange ett administrativt användarnamn och lösenord när ett paket för programinstallation kräver utökade behörigheter.
- **Fråga från UIA om utökad behörighet utan skyddat skrivbord**: **Aktivera** för att tillåta att UIAccess-appar frågar om utökade privilegier utan att använda skyddat skrivbord. När det här är **Inte konfigurerad** (standard) använder frågor om utökade privilegier ett skyddat skrivbord.

#### <a name="admin-approval-mode-settings"></a>Inställningar för Läge för administratörstillåtelse

- **Läge för administratörstillåtelse för inbyggd administratör**: **Aktiverad** tillåter att det inbyggda administratörskontot använder läget för administratörstillåtelse. Alla åtgärder som kräver rättighetsökning uppmanar användaren att godkänna åtgärden. **Inte konfigurerad** (standard) kör alla appar med fullständiga administratörsrättigheter.
- **Kör alla administratörer i läge för administratörstillåtelse**: Ställ in på **Aktiverat** för att inaktivera läget för administratörstillåtelse och alla relaterade UAC-principinställningar. **Inte konfigurerad** (standard) aktiverar läget för administratörstillåtelse.

### <a name="microsoft-network-client"></a>Microsoft-nätverksklient

- **Signera kommunikationer digitalt (om servern tillåter)**: Avgör om SMB-klienten förhandlar signering av SMB-paket. När det här är **Inte konfigurerad** eller aktiverat (standard) ber Microsoft-nätverksklienten servern att köra SMB-paketsignering under installationen av sessionen. Om paketsignering är aktiverad på servern så förhandlas paketsignering. Om det här är inställt på **Inaktivera** förhandlar SMB-klienten aldrig SMB-paketsignering.
- **Skicka okrypterade lösenord till SMB-servrar från tredje part**: När det här är inställt på **Aktivera** kan SMB-omdirigeraren (Server Message Block) skicka lösenord i klartext till Microsoft SMB-servrar som inte har stöd för kryptering av lösenord under autentiseringen. När det här är **Inte konfigurerad** (standard) krypteras lösenorden.

### <a name="microsoft-network-server"></a>Microsoft-nätverksserver

- **Signera kommunikation digitalt (om klienten tillåter)**: Anger om SMB-servern förhandlar SNB-paketsignering med klienter som begär det. När det här är inställt på **Aktivera** förhandlar Microsoft-nätverksservern SMB-paketsignering såsom begärs av klienten. D.v.s. om paketsignering är aktiverat på servern, förhandlas paketsignering. När du anger **Inte konfigurerat** eller inaktiverat (standard) förhandlar SMB-klienten aldrig om SMB-paketsignering.
- **Signera kommunikation digitalt (alltid)**: Anger om paketsignering krävs av SMB-serverkomponenten. När det här är inställt på **Aktivera** kommunicerar Microsoft-nätverksservern inte med en Microsoft-nätverksklient såvida inte klienten godkänner signering av SMB-paket. När det här är **Inte konfigurerad** eller inaktiverat (standard) förhandlas signering av SMB-paket mellan klienten och servern.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Konfigurera inställningar för slutpunktsskydd på [macOS](endpoint-protection-macos.md)-enheter.
