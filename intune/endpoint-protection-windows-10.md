---
title: "Microsoft Intune Endpoint Protection-inställningar för Windows 10"
titlesuffix: 
description: "Läs om Intune-inställningarna du kan använda för att konfigurera Endpoint Protection-inställningar, för exempelvis BitLocker, på Windows 10-enheter."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 02a32f678b40b2b40535984e17b41e0a864d8fdf
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="create-endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Skapa Endpoint Protection-inställningar för Windows 10 och senare i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med en Endpoint Protection-profil kan du konfigurera säkerhetsfunktioner, t.ex. BitLocker och Windows Defender för Windows 10-enheter.

Använd informationen i den här artikeln för att lära dig skapa Endpoint Protection-profiler.

> [!Note]
> De här inställningarna stöds inte av versionerna Home och Professional av Windows 10.

## <a name="create-an-endpoint-protection-profile"></a>Skapa en Endpoint Protection-profil

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. På bladet **Enhetskonfiguration** under avsnittet **Hantera** väljer du **Profiler**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för enhetens funktionsprofil.
5. I listrutan **Plattform** väljer du **Windows 10 och senare**.
6. Välj **Endpoint Protection** i listrutan **Profiltyp**.
7. Konfigurera de inställningar du vill använda. Informationen i den här artikeln hjälper dig förstå vad varje inställning gör. Välj **OK** när du är klar.
8. Gå tillbaka till bladet **Skapa profil** och välj **Skapa**.

Profilen skapas och visas på bladet med profillistan.

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Application Guard är endast tillgängligt för Windows 10-enheter (64-bitars). Med den här profilen installeras en Win32-komponent för att aktivera Application Guard.

- **Application Guard** – Öppna ej godkända webbplatser i en virtualiserad Hyper-V-webbläsarbehållare.
- **Funktionssätt för Urklipp** – Välj vilka åtgärder för kopiera/klistra in som tillåts mellan den lokala datorn och den virtuella Application Guard-webbläsaren.
- **Externt innehåll på företagswebbplatser** – Blockera inläsning av innehåll från webbplatser som inte är godkända.
- **Skriv ut från virtuell webbläsare** – Tillåt att PDF- och XPS-skrivare, samt lokala skrivare och/eller nätverksskrivare skriver ut innehåll från den virtuella webbläsaren.
- **Samla in loggar** – Samla in loggar för händelser som inträffar i en Application Guard-webbläsarsession.
- **Behåll användargenererade webbläsardata** – Tillåt att användardata (t.ex. lösenord, favoriter och cookies) som skapas under en virtuell Application Guard-webbläsarsession sparas.
- **Grafikacceleration** – Läs in grafikintensiva webbplatser snabbare när du arbetar i en virtuell Application Guard-webbläsarsession genom att aktivera åtkomst till en virtuell grafikprocessor.


## <a name="windows-defender-firewall"></a>Windows Defender-brandvägg

### <a name="global-settings"></a>Globala inställningar

De här inställningarna avser alla nätverkstyper.

- **File Transfer Protocol** – Blockera tillståndskänslig FTP.
- **Inaktiv tid för säkerhetsassociation före borttagning** – Säkerhetsassociationer tas bort om ingen nätverkstrafik har identifierats under *n* sekunder.
- **I förväg delad nyckelkodning** – Koda i förväg delade nycklar med UTF-8.
- **IPsec-undantag** – Konfigurera specifik trafik som ska undantas från IPsec, t.ex. **Granne upptäcker koder av IPv6 ICMP-typ**, **ICMP**, **Router upptäcker koder av IPv6 ICMP-typ** och **Både IPv4- och IPv6 DHCP-nätverkstrafik**.
- **Verifiering av listan över återkallade certifikat** – Ange ett värde för hur listan över återkallade certifikat genomförs, inklusive **Inaktivera CRL-verifiering**, **CRL-verifiering misslyckas enbart för återkallade certifikat** och **CRL-verifiering misslyckas för alla påträffade fel**.
- **Matcha autentiseringsuppsättningarna per nyckelmodul** – Ange nyckelmoduler för att ignorera hela autentiseringsuppsättningen om de inte har stöd för alla autentiseringspaket i den uppsättningen.
- **Paketkö** – Ange hur skalning för programvara på mottagarsidan aktiveras för den krypterade mottagningen och rensa flyttning av text framåt för scenariot med IPsec-tunnelgatewayen. Detta säkerställer att paketordningen bevaras.

### <a name="network-settings"></a>Nätverksinställningar

De här inställningarna gäller för specifika nätverkstyper, inklusive **Domännätverk (arbetsplats)**, **Privat (identifierbart) nätverk** och **Offentligt (inte identifierbart) nätverk**.

#### <a name="general-settings"></a>Allmänna inställningar

- **Windows Defender-brandvägg** – Aktivera den här inställningen för att blockera nätverkstrafik.
- **Dolt läge** – Hindra brandväggen från att arbeta i dolt läge. Om du blockerar detta blockeras även **IPsec-skyddat paketundantag**.
- **Avskärmad** – Om du aktiverar detta blockerar brandväggsinställningen all inkommande trafik.
- **Unicast-svar på multicast-sändningar** – Blockera unicast-svar på multicast-sändningar. Du vill normalt inte ta emot unicast-svar på multicast- eller broadcast-meddelanden, eftersom sådana svar kan tyda på en överbelastningsattack eller att en angripare försöker ge sig på en känd aktiv dator.
- **Inkommande meddelanden** – Blockera visning av meddelanden för användare när ett program har blockerats från att lyssna på en port.
- **Standardåtgärd för inkommande anslutningar** – Blockera standardåtgärden som brandväggen utför på inkommande anslutningar.

#### <a name="rule-merging"></a>Sammanslagning av regler

- **Auktoriserade Windows Defender-brandväggsregler från det lokala arkivet** – Tillåt att auktoriserade brandväggsregler i det lokala arkivet erkänns och framtvingas.
- **Globala Windows Defender-portbrandväggsregler från det lokala arkivet** – Tillåt att globala portbrandväggsregler i det lokala arkivet erkänns och framtvingas.
- **Windows Defender-brandväggsregler från det lokala arkivet** – Tillåt att globala brandväggsregler i det lokala arkivet erkänns och framtvingas.
- **IPSec-regler från det lokala arkivet** – Använd regler för anslutningssäkerhet från det lokala lagret, oavsett schema eller version av regler för anslutningssäkerhet.

## <a name="windows-defender-smartscreen-settings"></a>Inställningar för Windows Defender SmartScreen

- **SmartScreen för appar och filer** – Aktivera Windows SmartScreen för körning av filer och program som körs.
- **Körning av overifierade filer** – Blockera användaren från att köra filer som inte har verifierats av Windows SmartScreen.

## <a name="windows-encryption"></a>Windows-kryptering

### <a name="windows-settings"></a>Windows-inställningar

De här inställningarna gäller för alla versioner av Windows 10.

- **Kryptera enheter** – Om den här inställningen är aktiverad uppmanas användarna att aktivera enhetskryptering. Dessutom uppmanas de att bekräfta att kryptering från en annan provider inte har aktiverats. Om Windows-kryptering aktiveras samtidigt som en annan krypteringsmetod är aktiv, kan enheten bli instabil.
- **Kryptera minneskortet** – Aktivera den här inställningen för att kryptera flyttbara minneskort som används av enheten.


### <a name="bitlocker-base-settings"></a>Grundläggande BitLocker-inställningar

Grundläggande inställningar är universella BitLocker-inställningar för alla typer av dataenheter. Inställningarna för BitLocker-grupprincipen styr vilka enhetskrypteringsåtgärder eller konfigurationsalternativ som användaren kan ändra för alla typer av dataenheter.

- **Varning för annan hårddiskkryptering** – Inaktivera varningsmeddelandet för annan hårddiskkryptering på slutanvändarnas datorer.
- **Konfigurera krypteringsmetoder** – Aktivera den här inställningen för att konfigurera krypteringsalgoritmer för operativsystem, data och flyttbara enheter.
    - **Kryptering för operativsystemenheter** – Välj krypteringsmetod för operativsystemenheter. Vi rekommenderar att du använder XTS AES-algoritmen.
    - **Kryptering för fasta dataenheter** – Välj krypteringsmetod för fasta (inbyggda) dataenheter. Vi rekommenderar att du använder XTS AES-algoritmen.
    - **Kryptering för flyttbara dataenheter** – Välj krypteringsmetod för flyttbara dataenheter. Om den flyttbara enheten används med enheter som inte kör Windows 10, rekommenderar vi att du använder AES-CBC-algoritmen.

### <a name="bitlocker-os-drive-settings"></a>BitLocker-inställningar för operativsystemenheten

Dessa inställningar gäller specifikt för operativsystemets dataenheter.

- **Ytterligare autentisering vid start** – Konfigurera autentiseringskrav för datorstart, inklusive användning av Trusted Platform Module (TPM).
    - **BitLocker med icke-kompatibelt TPM-chip**
    - **Kompatibel TPM-start** – Konfigurera huruvida TPM-kretsen tillåts, inte tillåts eller krävs.
    - **PIN-kod för kompatibel TPM-start** – Konfigurera om en start-PIN-kod tillåts, inte tillåts eller måste användas med TPM-kretsen.
    - **Kompatibel TPM-startnyckel** – Konfigurera om en startnyckel tillåts, inte tillåts eller måste användas med TPM-kretsen.
    - **Kompatibel TPM-startnyckel och PIN-kod** – Konfigurera om en startnyckel och PIN-kod tillåts, inte tillåts eller måste användas med TPM-kretsen.
- **Minsta PIN-kodslängd** – Aktivera den här inställningen för att konfigurera en minsta längd för start-PIN-koden för TPM.
    - **Minsta tecken** – Ange antalet tecken som krävs för start-PIN-koden för TPM, **4**-**20** tecken.
- **Återställning av operativsystemenhet** – Aktivera den här inställningen för att ange hur BitLocker-skyddade operativsystemenheter återställs när nödvändig startinformation saknas.
    - **Certifikatbaserad dataåterställningsagent** – Aktivera den här inställningen om du vill att dataåterställningsagenter ska kunna användas med BitLocker-skyddade operativsystemenheter.
    - **Återställningslösenord skapat av användare** – Konfigurera huruvida användare får, måste eller inte får generera ett 48-siffrigt återställningslösenord.
    - **Återställningsnyckel skapad av användare** – Konfigurera huruvida användare får, måste eller inte får skapa en 256-bitars återställningsnyckel.
    - **Återställningsalternativ i BitLocker-installationsguiden** – Aktivera den här inställningen om du vill hindra användare från att se och ändra återställningsalternativ när de aktiverar BitLocker.
    - **Spara BitLocker-återställningsinformation i AD DS** – Aktivera lagring av BitLocker-återställningsinformation i Active Directory.
    - **BitLocker-återställningsinformation lagrad i AD DS** – Konfigurera vilka delar av BitLocker-återställningsinformation som lagras i Active Directory. Välj mellan:
        - **Säkerhetskopiera återställningslösenord och nyckelpaket**
        - **Säkerhetskopiera endast återställningslösenord**
    - **Lagra återställningsinformation i AD DS innan BitLocker aktiveras** – Aktivera den här inställningen för att hindra användare från att aktivera BitLocker om enheten är ansluten till domänen och BitLocker-återställningsinformation har lagrats i Active Directory.
- **Återställningsmeddelande och webbadress i förstartsmiljö** – Aktivera den här inställningen för att konfigurera meddelandet och webbadressen som visas på förstartsskärmen för nyckelåterställning.
    - **Återställningsmeddelande i förstartsmiljö** – Konfigurera hur återställningsmeddelande i förstartsmiljö visas för användarna. Välj mellan:
        - **Använd standardvärde för återställningsmeddelande och webbadress**
        - **Använd tomt återställningsmeddelande och webbadress**
        - **Använd anpassat återställningsmeddelande**
        - **Använd anpassad återställningswebbadress**


### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker-inställningar för fasta dataenheter

- **Neka skrivåtkomst till fast dataenhet som inte skyddas av BitLocker** – Om den här inställningen aktiveras måste BitLocker-skyddet aktiveras på alla fasta eller inbyggda dataenheter för att det ska gå att skriva till dem.
- **Återställning av fast enhet** – Aktivera den här inställningen för att ange hur BitLocker-skyddade fasta enheter återställs när nödvändig startinformation saknas.
    - **Dataåterställningsagent** – Aktivera den här inställningen om du vill att dataåterställningsagenter som ska användas med BitLocker-skyddade fasta enheter.
    - **Återställningslösenord skapat av användare** – Konfigurera huruvida användare får, måste eller inte får generera ett 48-siffrigt återställningslösenord.  
    - **Återställningsnyckel skapad av användare** – Konfigurera huruvida användare får, måste eller inte får skapa en 256-bitars återställningsnyckel.
    - **Återställningsalternativ i BitLocker-installationsguiden** – Aktivera den här inställningen om du vill hindra användare från att se och ändra återställningsalternativ när de aktiverar BitLocker.
    - **Spara BitLocker-återställningsinformation i AD DS** – Aktivera lagring av BitLocker-återställningsinformation i Active Directory.
    - **BitLocker-återställningsinformation i AD DS** – Konfigurera vilka delar av BitLocker-återställningsinformation som lagras i Active Directory. Välj mellan:
        - **Säkerhetskopiera återställningslösenord och nyckelpaket**
        - **Säkerhetskopiera endast återställningslösenord**
    - **Lagra återställningsinformation i AD DS innan BitLocker aktiveras** – Aktivera den här inställningen för att hindra användare från att aktivera BitLocker om enheten är ansluten till domänen och BitLocker-återställningsinformation har lagrats i Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker-inställningar för flyttbara dataenheter

- **Skrivåtkomst till flyttbar dataenhet som inte skyddas av BitLocker** – Ange om BitLocker-kryptering krävs för flyttbara lagringsenheter.
  - **Skrivåtkomst till enheter som har ställts in i en annan organisation** – Ange om det går att skriva till flyttbara enheter som tillhör en annan organisation.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Använd [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) för att hantera och minska attackytan för appar som medarbetarna använder.

### <a name="attack-surface-reduction"></a>Minska attackytan

Hjälp till att [förhindra åtgärder och appar](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) som normalt används av skadlig kod som söker sårbarheter för att angripa datorer.

#### <a name="rules-to-prevent-office-macro-threats"></a>Regler för att förhindra Office-makrohot

Blockera Office-appar från att vidta följande åtgärder:

- **Office-appar som infogar i andra processer (inga undantag)**
- **Office-appar/-makron som skapar körbart innehåll**
- **Office-appar som startar underordnade processer**
- **Win32-importer från Office-makrokod**

#### <a name="rules-to-prevent-script-threats"></a>Regler för att förhindra skripthot

Blockera dessa för att hjälpa till att förhindra skripthot:

- **Dold js/vbs/ps/makrokod**
- **js/vbs kör nyttolaster som laddats ned från Internet (inga undantag)**

#### <a name="rules-to-prevent-email-threats"></a>Regler för att förhindra e-posthot

Blockera detta för att hjälpa till att förhindra e-posthot:

- **Körning av körbart innehåll (exe, dll, ps, js, vbs, osv.) som har tagits bort från e-post (webbaserad e-post/e-postklient) (inga undantag)**

#### <a name="attack-surface-reduction-exceptions"></a>Undantag för att minska attackytan

- **Filer och mappar som ska uteslutas från reglerna för att minska attackytan** – Importera/lägg till en lista över platser som ska uteslutas från de konfigurerade reglerna.

### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

Hjälp till att skydda värdefulla data från skadliga appar och hot, till exempel utpressningstrojaner.

- **Mappskydd** – Skydda filer och mappar från oönskade ändringar som görs av skadliga appar. Du kan importera en **lista över appar som har åtkomst till skyddade mappar** eller lägga till dem manuellt. Du kan även lägga till en **lista över ytterligare mappar som behöver skyddas** genom en överföring, eller lägga till dem manuellt.

### <a name="network-filtering"></a>Nätverksfiltrering

Blockera utgående anslutningar från alla appar till IP-adresser/domäner med dåligt rykte.

### <a name="exploit-protection"></a>Sårbarhetsskydd

Blockera **användarredigering av gränssnittet för sårbarhetsskydd** genom att överföra en XML-fil som tillåter att du konfigurerar minne, kontrollflöde och principbegränsningar som kan användas för att blockera ett program från sårbarheter.

Aktivera skydd av sårbarheter genom att skapa en XML-fil som representerar systemet och de inställningar för programminskning som du önskar. Du kan använda någon av dessa två metoder för att göra detta:

 1. PowerShell: Använd en eller flera av cmdlet:arna Get-ProcessMitigation, Set-ProcessMitigation och ConvertTo-ProcessMitigationPolicy PowerShell för att konfigurera minskningsinställningar och exportera en XML-representation av dem.

 2. Gränssnittet för Windows Defender Säkerhetscenter: I Windows Defender Säkerhetscenter klickar du på App- & webbläsarkontroll och bläddrar sedan längst ned på skärmen för att hitta Sårbarhetsskydd. Använd först flikarna Systeminställningar och Programinställningar för att konfigurera minskningsinställningar. Leta sedan reda på länken Exportera inställningar längst ned på skärmen för att exportera en XML-återgivning av dem.

## <a name="windows-defender-application-control"></a>Windows Defender Application Control

Använd **Kodintegritetsprinciper för programkontroll** för att välja ytterligare appar som antingen behöver granskas av eller som kan vara betrodda att köras av Windows Defender Application Control. Windows-komponenter och alla appar från Windows Store är automatiskt betrodda att köras.

Program blockeras inte i läget **Endast granskning**. I läget **Endast granskning** loggas alla händelser i lokala klientloggar.

När det är aktiverat kan programkontrollen endast inaktiveras genom att ändra läget från **Framtvinga** till **Endast granskning**. Om du ändrar läget från **Framtvinga** till **Inte konfigurerad** fortsätter programkontrollen att tillämpas på tilldelade enheter.

## <a name="windows-defender-security-center"></a>Windows Defender Säkerhetscenter

Appen Windows Defender Säkerhetscenter fungerar som en separat app eller process från var och en av de enskilda funktionerna, och visar endast meddelanden via Åtgärdscenter. Den fungerar som en insamlare eller enskild plats för att visa status och utföra konfiguration för var och en av funktionerna. Läs mer i dokumentationen till [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Appen Windows Defender Säkerhetscenter och meddelanden

Blockera slutanvändarens åtkomst till olika delar av appen Windows Defender Säkerhetscenter. Om ett avsnitt döljs blockeras även relaterade meddelanden.

- **Skydd mot virus och hot**
- **Enhetsprestanda och hälsa**
- **Brandväggs- och nätverksskydd**
- **App- och webbläsarkontroll**
- **Familjealternativ**
- **Aviseringar från områdena som visas i appen** – Välj vilka meddelanden som ska visas för slutanvändare. Meddelanden som är mindre viktiga omfattar sammanfattningar av Windows Defender Antivirus-aktivitet, inklusive meddelanden när genomsökningar har slutförts. Alla andra meddelanden anses viktiga.

#### <a name="it-contact-information"></a>IT-kontaktuppgifter

Ange IT-kontaktuppgifter som ska visas i appen Windows Defender Säkerhetscenter och appmeddelanden. Du kan välja **Visa i app och i aviseringar**, **Visa endast i app**, **Visa endast i aviseringar** eller **Visa inte**. Du måste ange **IT-organisationens namn** och minst ett av följande kontaktalternativ:

- **IT-avdelningens telefonnummer eller Skype-ID**
- **IT-avdelningens e-postadress**
- **URL till IT-supportwebbplatsen**

## <a name="next-steps"></a>Nästa steg

Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).
