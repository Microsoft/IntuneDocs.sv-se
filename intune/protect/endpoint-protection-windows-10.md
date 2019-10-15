---
title: Skyddsinställningar för Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: På Windows 10-enheter kan du använda eller konfigurera inställningar för slutpunktsskydd för att aktivera Windows Defender-funktionalitet, inklusive Application Guard, brandvägg, SmartScreen, kryptering och bitlocker, Exploit Guard, programreglering, Säkerhetscenter och säkerhet på lokala enheter i Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: karthig
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22e3779cd0772753ccd8843cd1f1ff38617298d6
ms.sourcegitcommit: 884654da8e72a63bfaea6b5def6c7891b065f251
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163585"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Inställningar för Windows 10 (och senare) för att skydda delade enheter med Intune  

[!INCLUDE [azure_portal](../includes/azure_portal.md)]  

Microsoft Intune innehåller många inställningar som skyddar dina enheter. Den här artikeln beskriver alla inställningar du kan aktivera och kon i Windows 10 och nyare enheter. Dessa inställningar skapas i en konfigurationsprofil för slutpunktsskydd i Intune för att kontrollera säkerheten, inklusive BitLocker och Windows Defender.  

Information om att konfigurera Windows Defender Antivirus finns i [Enhetsbegränsningar för Windows 10](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).  

## <a name="before-you-begin"></a>Innan du börjar  

[Skapa en enhetskonfigurationsprofil för slutpunktsskydd](endpoint-protection-configure.md).  

Mer information om konfigurations tjänst leverantörer (CSP: er) finns i [referens för Configuration Service-Provider](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).  

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard  

När du använder Microsoft Edge Windows Defender Application Guard skyddas din miljö från webbplatser som inte är betrodda av din organisation. När användare besöker webbplatser som inte listas i din isolerade nätverksgräns, öppnas webbplatserna i en virtuell webbläsarsession i Hyper-V. Betrodda webbplatser definieras av en nätverksgräns som konfigureras i enhetskonfigurationen.  

Application Guard är endast tillgängligt för Windows 10-enheter (64-bitars). Med den här profilen installeras en Win32-komponent för att aktivera Application Guard.  

- **Application Guard**  
  **Standard**: Inte konfigurerat  
   Application Guard CSP: [Settings/AllowWindowsDefenderApplicationGuard](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **Aktivera för Edge** – aktiverar den här funktionen, som öppnar ej betrodda webbplatser i en virtualiserad Hyper-V-webbläsarcontainer.  
  - **Inte konfigurerad** – ingen plats (betrodd och ej betrodd) kan öppnas på enheten.  

- **Funktionssätt för Urklipp**  
  **Standard**: Inte konfigurerat  
   Application Guard CSP: [Settings/ClipboardSettings](https://go.microsoft.com/fwlink/?linkid=872351)  

  Välj vilka åtgärder för kopiera och klistra in som tillåts mellan den lokala datorn och den virtuella Application Guard-webbläsaren.  
  - **Inte konfigurerat**  
  - **Tillåt endast kopiera och klistra in från PC till webbläsare**  
  - **Tillåt endast kopiera och klistra in från webbläsare till dator**  
  - **Tillåt kopiera och klistra in mellan datorer och webbläsare**  
  - **Blockera kopiering och inklistring mellan datorer och webbläsare**  

- **Urklipps innehåll**  
  Den här inställningen är endast tillgänglig när *beteendet för Urklipp* har angetts till någon av inställningarna för *Tillåt* .  
  **Standard**: Inte konfigurerat  
  Application Guard CSP: [Settings/ClipboardFileType](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  Välj det tillåtna Urklipp-innehållet.  
  - **Inte konfigurerat**  
  - **Text**  
  - **Bilder**  
  - **Text och bilder**  

- **Externt innehåll på företagswebbplatser**  
  **Standard**: Inte konfigurerat  
  Application Guard CSP: [Settings/BlockNonEnterpriseContent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - **Blockera** – blockera inläsning av innehåll från webbplatser som inte är godkända.  
  - **Inte konfigurerad** – icke-företagswebbplatser kan öppnas på enheten.  
 
- **Skriv ut från virtuell webbläsare**  
  **Standard**: Inte konfigurerat  
  Application Guard CSP: [Settings/PrintingSettings](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **Tillåt** – tillåter utskrift av valt innehåll från den virtuella webbläsaren.  
  - **Inte konfigurerat** Inaktivera alla utskrifts funktioner.  

  När du *tillåter* utskrift kan du konfigurera följande inställningar:
  - **Utskrifts typ (er)** Välj ett eller flera av följande alternativ:  
    - PDF  
    - XPS  
    - Lokala skrivare
    - Nätverks skrivare  

- **Samla in loggar**  
  **Standard**: Inte konfigurerat  
  Application Guard CSP: [audit/AuditApplicationGuard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **Tillåt** – samla in loggar för händelser som inträffar i en Application Guard-webbläsarsession.  
  - **Inte konfigurerad** – samlar inte in några loggar inom webbläsarsessionen.  

- **Behåll användargenererade webbläsardata**  
  **Standard**: Inte konfigurerat  
  Application Guard CSP: [Settings/AllowPersistence](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **Tillåt** – spara användardata (t.ex. lösenord, favoriter och cookies) som skapas under en virtuell Application Guard-webbläsarsession.  
  - **Inte konfigurerad** – ta bort filer och data som laddats ned av en användare när enheten startas om eller när användaren loggar ut.  

- **Grafikacceleration**  
 **Standard**: Inte konfigurerat  
  Application Guard CSP: [Settings/AllowVirtualGPU](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - **Aktivera** – läs in grafikintensiva webbplatser och video snabbare genom att få åtkomst till en virtuell grafikprocessor.  
  - **Inte konfigurerat** Använd enhetens processor för grafik. Använd inte den virtuella grafik bearbetnings enheten.  

- **Ladda ned filer till värdfilsystemet**  
  **Standard**: Inte konfigurerat  
  Application Guard CSP: [Settings/SaveFilesToHost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **Aktivera** – användare laddar ned filer från den virtuella webbläsaren till värdoperativsystemet.  
  - **Inte konfigurerad** – håller filerna lokala på enheten och laddar inte ned filer till värdfilsystemet.  

## <a name="windows-defender-firewall"></a>Windows Defender-brandvägg  
 
### <a name="global-settings"></a>Globala inställningar  

De här inställningarna avser alla nätverkstyper.  

- **File Transfer Protocol**  
  **Standard**: Inte konfigurerat  
   Brand Väggs [-CSP: MdmStore/global/DisableStatefulFtp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - **Blockera** – inaktivera tillståndskänslig FTP.  
  - **Inte konfigurerad** – brandväggen utför tillståndskänslig FTP-filtrering för att tillåta sekundära anslutningar.  

- **Inaktiv tid för säkerhetsassociation före borttagning**  
  **Standard**: *Inte konfigurerat*  
   Brand Väggs [-CSP: MdmStore/global/SaIdleTime](https://go.microsoft.com/fwlink/?linkid=872539)  

   Ange en inaktiv tid i sekunder, efter vilken säkerhets associationer tas bort.   

- **Kodning av i förväg delad nyckel**  
  **Standard**: Inte konfigurerat  
   Brand Väggs [-CSP: MdmStore/global/PresharedKeyEncoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - **Aktivera** förskevade nycklar med UTF-8.  
   - **Inte konfigurerad** – koda förskevade nycklar med det lokala lagring svärdet.  

- **IPsec-undantag**  
  **Standard**: *0 valda*  
   Brand Väggs [-CSP: MdmStore/global/IPsecExempt](https://go.microsoft.com/fwlink/?linkid=872547)

   Välj en eller flera av följande typer av trafik som ska undantas från IPsec:  
   - **Granne upptäcker koder av IPv6 ICMP-typ**  
   - **ICMP**  
   - **Router upptäcker koder av IPv6 ICMP-typ**  
   - **Både IPv4 och IPv6 DHCP-nätverkstrafik**  

- **Verifiering av listan över återkallade certifikat**  
  **Standard**: Inte konfigurerat  
  Brand Väggs [-CSP: MdmStore/global/CRLcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  Välj hur enheten verifierar listan över återkallade certifikat. Alternativen är:  
  - **Inaktivera CRL-verifiering**  
  - **Misslyckad CRL-verifiering för återkallade certifikat**  
  - Det gick **inte att verifiera CRL på ett fel som påträffats**.  
 

- **Matcha autentiseringsuppsättningarna per nyckelmodul**  
  **Standard**: Inte konfigurerat  
  Brand Väggs [-CSP: MdmStore/global/OpportunisticallyMatchAuthSetPerKM](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **Aktivera** – nyckelmoduler MÅSTE endast ignorera de autentiseringspaket som de inte stödjer.  
  - **Inte konfigurerad** – nyckelmoduler MÅSTE ignorera hela autentiseringsuppsättningen om de inte har stöd för alla autentiseringspaket som anges i uppsättningen.  


- **Paketkö**  
  **Standard**: Inte konfigurerat  
  Brand Väggs [-CSP: MdmStore/global/EnablePacketQueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  Ange hur programvaruskalning på mottagarsidan aktiveras för den krypterade mottagningen och rensa flyttning av text framåt för scenariot med IPsec-tunnelgatewayen. Denna inställning bekräftar att paketordningen bevaras. Alternativen är:  
  - **Inte konfigurerat**  
  - **Inaktivera alla paket köer**  
  - **Köa endast inkommande krypterade paket**  
  - **Köa paket efter dekryptering utförs endast för vidarebefordran**  
  - **Konfigurera både inkommande och utgående paket**  

### <a name="network-settings"></a>Nätverksinställningar  

Följande inställningar visas i den här artikeln en gång, men alla gäller för de tre angivna nätverks typerna:  
- **Domän nätverk (arbets plats)**  
- **Privat (identifierbart) nätverk**  
- **Offentligt (inte identifierbart) nätverk**  

#### <a name="general-settings"></a>Allmänna inställningar  

- **Windows Defender-brandvägg**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [EnableFirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **Aktivera** – aktivera brandväggen och avancerad säkerhet. 
  - **Inte konfigurerad** – tillåt all nätverkstrafik oavsett eventuella andra principinställningar.  

- **Dolt läge**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [DisableStealthMode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - **Inte konfigurerat**  
  - **Blockera** – brand väggen blockeras från att fungera i dolt-läge. Om du blockerar dolt läge blockeras även **IPsec-skyddat paketundantag**.  
  - **Tillåt** – brand väggen fungerar i dolt-läge, vilket förhindrar svar på avsöknings begär Anden.  

- **IPsec-skyddat paket undantag med dolt-läge**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [DisableStealthModeIpsecSecuredPacketExemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  Det här alternativet ignoreras om *dolt läge* är inställt på *blockera*.  

  - **Inte konfigurerat**  
  - **Blockera** -IPsec-skyddade paket får inte undantag.  
  - **Tillåt** – Aktivera undantag. Brand väggens dolt-läge får inte hindra värddatorn från att svara på oönskad nätverks trafik som skyddas av IPsec.  

- **Avskärmad**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [skärmad](https://go.microsoft.com/fwlink/?linkid=872561)  
    - **Inte konfigurerat**  
    - **Blockera** – när Windows Defender-brandväggen är aktive rad och den här inställningen är inställd på *blockera*, blockeras all inkommande trafik, oavsett andra princip inställningar. 
    - **Tillåt** – när är inställt på *Tillåt*är den här inställningen inaktive rad och inkommande trafik tillåts baserat på andra princip inställningar.

- **Unicast-svar på multicast-sändningar**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [DisableUnicastResponsesToMulticastBroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  Normalt vill du inte ta emot unicast-svar på multicast- eller broadcast-meddelanden. Svaren kan indikera en DOS-attack (denial of service), eller en angripare som försöker avsöka en känd live-dator.  
  - **Inte konfigurerat**  
  - **Block** – Inaktivera Unicast-svar på multicast-sändningar.  
  - **Tillåt** – tillåt Unicast-svar på multicast-sändningar.  

- **Inkommande meddelanden**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [DisableInboundNotifications](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - **Inte konfigurerat**  
  - **Blockera** – Dölj meddelanden som ska användas när en app blockeras från att lyssna på en port.  
  - **Inte konfigurerad** – aktiverar inställningen och kan visa ett meddelande till användare när en app blockeras från att lyssna på en port.  

- **Standardåtgärd för inkommande anslutningar**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [DefaultOutboundAction](https://aka.ms/intune-firewall-outboundaction)  
  
  Konfigurera standard åtgärds brand väggen utför på utgående anslutningar. Den här inställningen tillämpas på Windows version 1809 och senare.  

  - **Inte konfigurerat**  
  - **Blockera** – standard brand Väggs åtgärden körs inte på utgående trafik om den inte uttryckligen har angetts att blockera.  
  - **Tillåt** -standard brand Väggs åtgärder körs på utgående anslutningar.  

- **Standardåtgärd för inkommande anslutningar**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [DefaultInboundAction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - **Inte konfigurerat**  
  - **Blockera** – brandväggens standardåtgärd körs inte på inkommande anslutningar.  
  - **Tillåt** -standard brand Väggs åtgärder körs på inkommande anslutningar.  

#### <a name="rule-merging"></a>Sammanslagning av regler  

- **Windows Defender-brandväggsregler från det lokala arkivet**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [AuthAppsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - **Inte konfigurerat**  
  - **Blockera inte** – reglerna för den auktoriserade programbrandväggen i det lokala arkivet ignoreras och framtvingas inte.  
  - **Tillåt** -
   Välj **Aktivera** för att tillämpa brandväggsregler i det lokala arkivet så att de känns igen och framtvingas.  

- **Globala Windows Defender-portalbrandväggen från det lokala arkivet**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [GlobalPortsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - **Inte konfigurerat**  
  - **Blockera** – de globala port brand Väggs reglerna i det lokala arkivet ignoreras och verkställs inte.  
  - **Aktivera** – tillämpa brandväggsregler på globala portar i det lokala arkivet så att de känns igen och framtvingas.  

- **Windows Defender-brandväggsregler från det lokala arkivet**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [AllowLocalPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872567)  

  - **Inte konfigurerat**  
  - **Blockera** – brand Väggs regler från det lokala arkivet ignoreras och verkställs inte.
  - **Aktivera** – tillämpa brandväggsregler i det lokala arkivet så att de känns igen och framtvingas.  

- **IPSec-regler från det lokala arkivet**  
  **Standard**: Inte konfigurerat  
  Brand Väggs-CSP: [AllowLocalIpsecPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - **Inte konfigurerat**  
  - **Blockerad** – reglerna för anslutningssäkerhet från det lokala arkivet ignoreras och framtvingas inte, oavsett schemaversion eller version av regler för anslutningssäkerhet.  
  - **Tillåt** – tillämpa regler för anslutningssäkerhet från det lokala arkivet, oavsett schema eller version av regler för anslutningssäkerhet.  

### <a name="firewall-rules"></a>Brandväggsregler  

Du kan **lägga till** en eller flera anpassade brand Väggs regler. Mer information finns i [lägga till anpassade brand Väggs regler för Windows 10-enheter](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices).  

Anpassade brand Väggs regler stöder följande alternativ:  

#### <a name="general-settings"></a>Allmänna inställningar:  

- **Namn**  
  **Standard**: *inget namn*  

  Ange ett eget namn för regeln. Det här namnet visas i listan med regler som hjälper dig att identifiera det.  

- **Beskrivning**  
  **Standard**: *ingen beskrivning*  

  Ange en beskrivning av regeln.  

- **Riktning**   
  **Standard**: Inte konfigurerat  
  Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/Direction](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  Ange om den här regeln gäller **inkommande**eller **utgående** trafik. När inställningen **inte är konfigurerad**gäller regeln automatiskt för utgående trafik.  

- **Åtgärd**  
  **Standard**: Inte konfigurerat  
  Brand vägg CSP: [FirewallRules/*FirewallRuleName*/Action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action)och [FirewallRules/*FirewallRuleName*/Action/Type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  Välj från **Tillåt** eller **blockera**. När inställningen **inte är konfigurerad**tillåter regeln att trafik används.  

- **Nätverkstyp**  
  **Standard**: 0 valda  
  Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/Profiles](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  Välj upp till tre typer av nätverks typer som den här regeln tillhör. Alternativen omfattar **domän**, **privat**och **offentlig**.  Om inga nätverks typer väljs gäller regeln för alla tre nätverks typer.  

#### <a name="application-settings"></a>Programinställningar  

- **Program**  
  **Standard**: alla  

  Kontrol lera anslutningar för en app eller ett program. Välj ett av följande alternativ och slutför sedan den ytterligare konfigurationen:  
  - **Paket familje namn** – ange ett paket familje namn. Använd PowerShell **-kommandot Get-AppxPackage**för att hitta paket familje namnet.   
    Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/app/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - **Fil Sök väg** – du måste ange en fil Sök väg till en app på klienten het, som kan vara en absolut sökväg eller en relativ sökväg. Till exempel: C:\Windows\System\Notepad.exe eller%WINDIR%\Notepad.exe.  
    Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/app/filepath](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Windows-** tjänst – ange kort namnet för Windows-tjänsten om det är en tjänst och inte ett program som skickar eller tar emot trafik. Använd PowerShell **-kommandot Get-service**för att hitta tjänstens korta namn.  
    Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/app/ServiceName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **Alla**– *ingen ytterligare konfiguration är tillgänglig*.  

#### <a name="ip-address-settings"></a>Inställningar för IP-adress  

Ange de lokala och fjärranslutna adresserna som regeln gäller.  

- **Lokala adresser**    
  **Standard**: valfri adress  
  Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  Välj **valfri adress** eller **angiven adress**.  

  När du använder den *angivna adressen*lägger du till en eller flera adresser som en kommaavgränsad lista över lokala adresser som omfattas av regeln. Giltiga token är:  
  - Använd en asterisk "*" för *alla* lokala adresser. Om du använder en asterisk måste det vara den token som du använder.  
  - Om du vill ange ett undernät använder du antingen nät masken eller nätverkets prefix. Om varken en nätmask eller ett nätverksprefix anges, är nät masken standardvärdet 255.255.255.255.  
  - En giltig IPv6-adress.  
  - Ett IPv4-adressintervall i formatet "Start adress-slut adress" utan blank steg.  
  - Ett IPv6-adressintervall i formatet "Start adress-slut adress" utan blank steg.  

- **Fjär adresser**  
  **Standard**: valfri adress  
  Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/RemoteAddressRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  Välj **valfri adress** eller **angiven adress**.  

  När du använder den *angivna adressen*lägger du till en eller flera adresser som en kommaavgränsad lista med fjär adresser som omfattas av regeln. Tokens är inte Skift läges känsliga. Giltiga token är:  
  - Använd en asterisk "*" för *alla* fjärradresser. Om du använder en asterisk måste det vara den token som du använder.  
  - Gateway  
  - "DHCP"  
  - "DNS"  
  - ”WINS”  
  - "Intranät" (stöds i Windows-versioner 1809 och senare)  
  - "RmtIntranet" (stöds i Windows-versioner 1809 och senare)  
  - "Internet" (stöds i Windows-versioner 1809 och senare)  
  - "Ply2Renders" (stöds i Windows-versioner 1809 och senare)  
  - "LocalSubnet" anger en lokal adress i det lokala under nätet.  
  - Om du vill ange ett undernät använder du antingen nät masken eller nätverkets prefix. Om varken en nätmask eller ett nätverksprefix anges, är nät masken standardvärdet 255.255.255.255.  
  - En giltig IPv6-adress.  
  - Ett IPv4-adressintervall i formatet "Start adress-slut adress" utan blank steg.  
  - Ett IPv6-adressintervall i formatet "Start adress-slut adress" utan blank steg.  

#### <a name="port-and-protocol-settings"></a>Port-och protokoll inställningar  
Ange de lokala portar och fjärrportar som regeln gäller.  

- **Protokoll**  
  **Standard**: alla  
  Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/Protocol](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  Välj bland följande och slutför alla konfigurationer som krävs:  
  - **Alla** – ingen ytterligare konfiguration är tillgänglig.  
  - **TCP** – konfigurera lokala och fjärranslutna portar. Båda alternativen stöder alla portar eller angivna portar. Ange de angivna portarna genom att använda en kommaavgränsad lista.  
    - **Lokala portar** – brand Väggs-CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Fjärrports** -Firewall CSP: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** – konfigurera lokala och fjärranslutna portar. Båda alternativen stöder alla portar eller angivna portar. Ange de angivna portarna genom att använda en kommaavgränsad lista.  
    - **Lokala portar** – brand Väggs-CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Fjärrports** -Firewall CSP: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **Anpassad** – ange ett anpassat **protokoll** nummer från 0 till 255.  

#### <a name="advanced-configuration"></a>Avancerad konfiguration  
- **Gränssnittstyper**  
  **Standard**: 0 valda  
  Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/InterfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  Välj bland följande alternativ:  
  - **Fjärråtkomst**  
  - **Trådlöst**  
  - **Lokalt nätverk**  

- **Tillåt endast anslutningar från dessa användare**  
  **Standard**: alla användare *(används som standard när ingen lista har angetts)*  
  Brand Väggs [-CSP: FirewallRules/*FirewallRuleName*/LocalUserAuthorizationList](https://aka.ms/intunefirewallauthorizedusers)  

  Ange en lista över behöriga lokala användare för den här regeln. Det går inte att ange en lista över behöriga användare om den här regeln gäller för en Windows-tjänst.  


## <a name="windows-defender-smartscreen-settings"></a>Inställningar för Windows Defender SmartScreen  
 
Microsoft Edge måste vara installerat på enheten.  

- **SmartScreen för appar och filer**  
  **Standard**: Inte konfigurerat  
   SmartScreen-CSP: [SmartScreen/EnableSmartScreenInShell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **Inte konfigurerad** – inaktiverar användning av SmartScreen.  
  - **Aktivera** – aktiverar Windows SmartScreen för körning av filer och program som körs. SmartScreen är en molnbaserad komponent mot nätfiske och skadlig kod.  

- **Körning av overifierade filer**  
  **Standard**: Inte konfigurerat  
   SmartScreen-CSP: [SmartScreen/PreventOverrideForFilesInShell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **Inte konfigurerad** – inaktiverar den här funktionen och tillåter att slutanvändare kör filer som inte har verifierats.  
  - **Blockera** – hindrar slutanvändare från att köra filer som inte har verifierats av Windows SmartScreen.  

## <a name="windows-encryption"></a>Windows-kryptering  
 
### <a name="windows-settings"></a>Windows-inställningar  

Dessa krypterings inställningar gäller för alla versioner av Windows 10.  

- **Kryptera enheter**  
  **Standard**: Inte konfigurerat  
  BitLocker CSP: [RequireDeviceEncryption](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **Kräv** – uppmana användare att aktivera enhetskryptering. Beroende på Windows-version och systemkonfiguration kan användare uppmanas att:  
    - Bekräfta att kryptering från en annan provider inte är aktiverat.  
    - Inaktivera Bitlocker-diskkryptering och aktivera sedan Bitlocker igen.  
  - **Inte konfigurerat**  
  
  Om Windows-kryptering aktiveras samtidigt som en annan krypteringsmetod är aktiv, kan enheten bli instabil.  

- **Kryptera minneskort (endast mobil)**  
  *Den här inställningen gäller endast mobila enheter med Windows 10.*  
  **Standard**: Inte konfigurerat  
  BitLocker CSP: [RequireStorageCardEncryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - **Kräv** för att kryptera flyttbara minneskort som används av enheten.  
  - **Inte konfigurerad** – kräv inte kryptering av minneskort och uppmana inte användaren att aktivera det.  

### <a name="bitlocker-base-settings"></a>Grundläggande BitLocker-inställningar  

Grundläggande inställningar är universella BitLocker-inställningar för alla typer av dataenheter. De här inställningarna styr vilka enhetskrypteringsåtgärder eller konfigurationsalternativ som användaren kan ändra för alla typer av dataenheter.  

- **Varning för annan hårddiskkryptering**  
  **Standard**: Inte konfigurerat  
  BitLocker CSP: [AllowWarningForOtherDiskEncryption](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **Blockera** – inaktivera varningsmeddelandet om en annan tjänst för hårddiskkryptering finns på enheten.  
  - **Inte konfigurerad** – Tillåt att varningen för annan disk kryptering visas.  

  När inställningen är *blockerad*kan du konfigurera följande inställning:  

  - **Låt standardanvändare aktivera kryptering under Azure AD-anslutning**  
    *Den här inställningen gäller bara för Azure Active Directory anslutna (Azure rejust) enheter och är beroende av den föregående inställningen `Warning for other disk encryption`.*  
    **Standard**: Inte konfigurerat  
    BitLocker CSP: [AllowStandardUserEncryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **Tillåt** – standard användare (icke-administratörer) kan aktivera BitLocker-kryptering när det är inloggad.  
     - **Inte konfigurerad** – endast att administratörer får aktivera BitLocker-kryptering på enheten.  

- **Konfigurera krypteringsmetoder**  
  **Standard**: Inte konfigurerat  
  BitLocker CSP: [EncryptionMethodByDriveType](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **Aktivera** – konfigurera krypteringsalgoritmer för operativsystem, data och flyttbara enheter.  
  - **Inte konfigurerad** – BitLocker använder 128-bitars XTS-AES som standardkrypteringsmetod eller använder den krypteringsmetod som anges av något installationsskript.  

  När värdet är *Aktivera* kan du konfigurera följande inställningar:  

  - **Kryptering för operativsystemenheter**  
    **Standard**: XTS-AES 128-bit  
   
    Välj krypteringsmetod för operativsystemenheter. Vi rekommenderar att du använder XTS AES-algoritmen.  
    - **AES-CBC 128-bit**  
    - **AES-CBC 256-bit**  
    - **XTS-AES 128-bit**  
    - **XTS-AES 256-bit**  

  - **Kryptering för fasta dataenheter**  
    **Standard**: AES-CBC 128-bit  
   
    Välj krypteringsmetod för fasta (inbyggda) dataenheter. Vi rekommenderar att du använder XTS AES-algoritmen.  
    - **AES-CBC 128-bit**  
    - **AES-CBC 256-bit**  
    - **XTS-AES 128-bit**  
    - **XTS-AES 256-bit**  

  - **Kryptering för flyttbara dataenheter**  
    **Standard**: AES-CBC 128-bit  

    Välj krypteringsmetod för flyttbara dataenheter. Om den flyttbara enheten används med enheter som inte kör Windows 10 rekommenderar vi att du använder AES-CBC-algoritmen.  
    - **AES-CBC 128-bit**  
    - **AES-CBC 256-bit**  
    - **XTS-AES 128-bit**  
    - **XTS-AES 256-bit**  

### <a name="bitlocker-os-drive-settings"></a>BitLocker-inställningar för operativsystemenheten  

Dessa inställningar gäller specifikt för operativsystemets dataenheter.  

- **Ytterligare autentisering vid start**  
  **Standard**: Inte konfigurerat  
  BitLocker CSP: [SystemDrivesRequireStartupAuthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **Kräv** – konfigurera autentiseringskraven för datorstart, inklusive användning av Trusted Platform Module (TPM).  
  - **Inte konfigurerad** – konfigurera endast grundläggande alternativ på enheter med en TPM.  

  När värdet är *Kräv* kan du konfigurera följande inställningar:  

  - **BitLocker med icke-kompatibelt TPM-chip**  
    **Standard**: Inte konfigurerat  

    - **Blockera** – inaktivera användning av BitLocker när en enhet inte har ett kompatibelt TPM-chip.  
    - **Inte konfigurerad** – användare kan använda BitLocker utan ett kompatibelt TPM-chip. BitLocker kan kräva ett lösenord eller en startnyckel.  

  - **Kompatibel TPM-start**  
    **Standard**: Tillåt TPM  

    Konfigurera om TPM tillåts, krävs eller inte tillåts.  

    - **Tillåt TPM**  
    - **Tillåt inte TPM**  
    - **Kräv TPM**  

  - **Kompatibel PIN-kod för TPM-start**  
    **Standard**: Tillåt start-PIN med TPM  

    Välj att tillåta, inte tillåta eller kräva användning av en PIN-kod för start med TPM-chippet. För att aktivera en PIN-kod för start krävs interaktion från slutanvändaren.  

    - **Tillåt start-PIN med TPM**  
    - **Tillåt inte start-PIN-kod med TPM**  
    - **Kräv start-PIN-kod med TPM**

  - **Kompatibel nyckel för TPM-start**  
    **Standard**: Tillåt start nyckel med TPM  

    Välj att tillåta, inte tillåta eller kräva användning av en nyckel för start med TPM-chippet. För att aktivera en startnyckel krävs interaktion från slutanvändaren.  

    - **Tillåt start nyckel med TPM**  
    - **Tillåt inte start nyckel med TPM**  
    - **Kräv start nyckel med TPM**  

  - **Kompatibel nyckel och PIN-kod för TPM-start**  
    **Standard**: Tillåt start nyckel och PIN-kod med TPM  

    Välj att tillåta, inte tillåta eller kräva användning av en nyckel och PIN-kod för start med TPM-chippet. För att aktivera en startnyckel och en PIN-kod krävs interaktion från slutanvändaren.  
    - **Tillåt start nyckel och PIN-kod med TPM**  
    - **Tillåt inte start nyckel och PIN-kod med TPM**  
    - **Kräv start nyckel och PIN-kod med TPM**   

- **Minimilängd för PIN-kod**  
    **Standard**: Inte konfigurerat  
    BitLocker CSP: [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **Aktivera** Konfigurera en minimilängd för PIN-koden för TPM-start.  
    - **Inte konfigurerad** – användare kan konfigurera en PIN-kod för start med valfri längd mellan 6 och 20 siffror.  

  När värdet är *Aktivera* kan du konfigurera följande inställning:  

  - **Minsta tecken**  
    **Standard**: *inte konfigurerad* BitLocker CSP: [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)  

    Ange antalet tecken som krävs för PIN-koden från, **4**-**20**.  

- **Återställning av operativsystemenhet**  
  **Standard**: Inte konfigurerat   
  BitLocker CSP: [SystemDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **Aktivera** – ange hur BitLocker-skyddade operativsystemenheter återställs när nödvändig startinformation saknas.  
  - **Inte konfigurerad** – standardåterställningsalternativen för BitLocker-återställning stöds. Som standard tillåts en DRA, återställningsalternativen väljs av användaren, inklusive återställningslösenordet och återställningsnyckeln och återställningsinformation säkerhetskopieras inte till AD DS.  

  När värdet är *Aktivera* kan du konfigurera följande inställningar:  

  - **Certifikatbaserad dataåterställningsagent**  
    **Standard**: Inte konfigurerat  
     
    - **Blockera** – förhindra användning av data återställnings agent med BitLocker-skyddade OS-enheter.  
    - **Inte konfigurerad** – Tillåt att data återställnings agenter används med BitLocker-skyddade operativ system enheter.  

  - **Återställningslösenord skapat av användare**  
    **Standard**: Tillåt 48-siffrigt återställnings lösen ord  

    Välj om användarna får, måste eller inte får generera ett 48-siffrigt återställningslösenord.  
    - **Tillåt 48-siffrigt återställnings lösen ord**  
    - **Tillåt inte 48-siffrigt återställnings lösen ord**  
    - **Kräv 48-siffrigt återställnings lösen ord**  

  - **Återställningsnyckel skapad av användare**  
    **Standard**: Tillåt 256-bitars återställnings nyckel  

    Välj om användarna får, måste eller inte får skapa en 256-bitars återställningsnyckel.  
    - **Tillåt 256-bitars återställnings nyckel**  
    - **Tillåt inte 256-bitars återställnings nyckel**  
    - **Kräv 256-bitars återställnings nyckel**  

  - **Återställningsalternativ i BitLocker-installationsguiden**  
    **Standard**: Inte konfigurerat  

    - **Blockera** – användarna kan inte se och ändra återställningsalternativen. När det är inställt på 
    - **Inte konfigurerad** – användarna kan se och ändra återställningsalternativ när de aktiverar BitLocker. 
 
  - **Spara BitLocker-återställningsinformation till Azure Active Directory**  
    **Standard**: Inte konfigurerat  

    - **Aktivera** – lagra BitLocker-återställningsinformationen i Azure Active Directory (AAD).  
    - **Inte konfigurerad** – BitLocker-återställningsinformation lagras inte i AAD.  

  - **BitLocker-återställningsinformation lagrad i Azure Active Directory**  
    **Standard**: Säkerhetskopiera återställningslösenord och nyckelpaket  

    Konfigurera vilka delar av BitLocker-återställningsinformation som lagras i Azure AD. Välj mellan:  
    - **Säkerhetskopiera återställningslösenord och nyckelpaket**  
    - **Säkerhetskopiera endast återställningslösenord**  

  - **Rotation av lösen ord för klient driven återställning**  
    **Standard**: nyckel rotation aktive rad för Azure AD-anslutna enheter  
    BitLocker CSP: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Den här inställningen initierar en rotation av lösen ord för klient driven återställning efter återställning av operativ system enheter (antingen med hjälp av Bootmgr eller WinRE).  

    - Inte konfigurerat  
    - Nyckel rotation inaktive rad  
    - Nyckel rotation aktive rad för Azure AD-ansluten inices  
    - Nyckel rotation aktive rad för Azure AD och hybrid-anslutna enheter  

  - **Lagra återställnings information i Azure Active Directory innan du aktiverar BitLocker**  
    **Standard**: Inte konfigurerat  
 
     Hindra användare från att aktivera BitLocker om inte datorn har säkerhetskopierat BitLocker-återställningsinformation till Azure Active Directory.  

    - **Kräv** – hindra användare från att aktivera BitLocker såvida inte BitLocker-återställningsinformation har lagrats i Azure AD.  
    - **Inte konfigurerad** – användare kan aktiverar BitLocker även om återställningsinformation inte har lagrats i Azure AD.  

- **Återställningsmeddelande och webbadress i förstartsmiljö**  
  **Standard**: Inte konfigurerat  
  BitLocker CSP: [SystemDrivesRecoveryMessage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **Aktivera** – konfigurera meddelandet och URL: en som visas på skärmen för nyckel återställning före start.  
  - **Inte konfigurerad** – inaktivera den här funktionen.  
  
  När värdet är *Aktivera* kan du konfigurera följande inställning:  
  - **Återställningsmeddelande i förstartsmiljö**  
    **Standard**: Använd standardvärde för återställningsmeddelande och webbadress   
 
    Konfigurera hur återställningsmeddelande i förstartsmiljö visas för användarna. Välj mellan:  
    - **Använd standardvärde för återställningsmeddelande och webbadress**  
    - **Använd tomt återställningsmeddelande och webbadress**  
    - **Använd anpassat återställningsmeddelande**  
    - **Använd anpassad återställningswebbadress**  

### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker-inställningar för fasta dataenheter  

De här inställningarna gäller specifikt för fasta data enheter.  

- **Skrivåtkomst till fast dataenhet som inte skyddas av BitLocker**  
  **Standard**: Inte konfigurerat  
  BitLocker CSP: [FixedDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **Blockera** – ge skrivskyddad åtkomst till dataenheter som inte är BitLocker-skyddade.  
  - **Inte konfigurerad** – som standard är Läs-och skriv åtkomst till data enheter som inte är krypterade.  

- **Återställning av fast enhet**  
  **Standard**: Inte konfigurerat  
  BitLocker CSP: [FixedDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **Aktivera** – ange hur BitLocker-skyddade fasta enheter återställs när nödvändig startinformation saknas.  
  - **Inte konfigurerad** – inaktivera den här funktionen.  

  När värdet är *Aktivera* kan du konfigurera följande inställningar:  

  - **Dataåterställningsagent**  
    **Standard**: Inte konfigurerat  
 
    - **Blockera** – förhindra användning av dataåterställningsagent med principredigeraren för BitLocker-skyddade fasta enheter. 
    - **Inte konfigurerad** – tillåter användning av dataåterställningsagenter med BitLocker-skyddade fasta enheter.  

  - **Återställningslösenord skapat av användare**  
    **Standard**: Tillåt 48-siffrigt återställnings lösen ord  

    Välj om användarna får, måste eller inte får generera ett 48-siffrigt återställningslösenord.  
    - **Tillåt 48-siffrigt återställnings lösen ord**  
    - **Tillåt inte 48-siffrigt återställnings lösen ord**  
    - **Kräv 48-siffrigt återställnings lösen ord**  

  - **Återställningsnyckel skapad av användare**  
    **Standard**: Tillåt 256-bitars återställnings nyckel

    Välj om användarna får, måste eller inte får skapa en 256-bitars återställningsnyckel.
    - **Tillåt 256-bitars återställnings nyckel**  
    - **Tillåt inte 256-bitars återställnings nyckel**  
    - **Kräv 256-bitars återställnings nyckel**  

  - **Återställningsalternativ i BitLocker-installationsguiden**  
    **Standard**: Inte konfigurerat  

    - **Blockera** – användarna kan inte se och ändra återställningsalternativen. När det är inställt på 
    - **Inte konfigurerad** – användarna kan se och ändra återställningsalternativ när de aktiverar BitLocker.
 
  - **Spara BitLocker-återställningsinformation till Azure Active Directory**  
    **Standard**: Inte konfigurerat  

    - **Aktivera** – lagra BitLocker-återställningsinformationen i Azure Active Directory (AAD).  
    - **Inte konfigurerad** – BitLocker-återställningsinformation lagras inte i AAD.

  - **BitLocker-återställningsinformation lagrad i Azure Active Directory**  
    **Standard**: Säkerhetskopiera återställningslösenord och nyckelpaket  

    Konfigurera vilka delar av BitLocker-återställningsinformation som lagras i Azure AD. Välj mellan:  
    - **Säkerhetskopiera återställningslösenord och nyckelpaket**  
    - **Säkerhetskopiera endast återställningslösenord**  

  - **Rotation av lösen ord för klient driven återställning**  
    **Standard**: nyckel rotation aktive rad för Azure AD-anslutna enheter  
    BitLocker CSP: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Den här inställningen initierar en rotation av lösen ord för klient driven återställning efter återställning av operativ system enheter (antingen med hjälp av Bootmgr eller WinRE).  

    - Inte konfigurerat  
    - Nyckel rotation inaktive rad  
    - Nyckel rotation aktive rad för Azure AD-ansluten inices  
    - Nyckel rotation aktive rad för Azure AD och hybrid-anslutna enheter  

  - **Lagra återställnings information i Azure Active Directory innan du aktiverar BitLocker**  
    **Standard**: Inte konfigurerat  
 
    Hindra användare från att aktivera BitLocker om inte datorn har säkerhetskopierat BitLocker-återställningsinformation till Azure Active Directory.  

    - **Kräv** – hindra användare från att aktivera BitLocker såvida inte BitLocker-återställningsinformation har lagrats i Azure AD.  
    - **Inte konfigurerad** – användare kan aktiverar BitLocker även om återställningsinformation inte har lagrats i Azure AD.  

### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker-inställningar för flyttbara dataenheter  

De här inställningarna gäller specifikt för flyttbara data enheter.  

- **Skrivåtkomst till flyttbar dataenhet som inte skyddas av BitLocker**  
  **Standard**: Inte konfigurerat  
  BitLocker CSP: [RemovableDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **Blockera** – ge skrivskyddad åtkomst till dataenheter som inte är BitLocker-skyddade.  
  - **Inte konfigurerad** – som standard är Läs-och skriv åtkomst till data enheter som inte är krypterade.  

  När värdet är *Aktivera* kan du konfigurera följande inställning:  

  - **Skrivåtkomst till enheter som har ställts in i en annan organisation**  
    **Standard**: Inte konfigurerat  

    - **Blockera** – blockerar skrivbehörighet för enheter som har konfigurerats i en annan organisation.  
    - **Inte konfigurerad** -neka skriv åtkomst.  
 
## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard  

Använd [sårbarhets skydd](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) för att hantera och minska risken för angrepp i appar som används av dina anställda.  

### <a name="attack-surface-reduction"></a>Minska attackytan  

Reglerna för minskning av attack ytan förhindrar att skadlig kod används ofta för att infektera datorer med skadlig kod.  

#### <a name="attack-surface-reduction-rules"></a>Regler för att minska attackytan  

- **Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem**  
  **Standard**: Inte konfigurerat  
  Regel: [Blockera stöld av autentiseringsuppgifter från det lokala säkerhetsundersystemet i Windows (lsass.exe)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe)

  Hjälp till att förhindra åtgärder och appar som normalt används av skadlig kod som söker sårbarheter för att angripa datorer.  

  - **Inte konfigurerat**  
  - **Aktivera** Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem (lsass.exe).  
  - **Endast granskning**  

- **Skapa process från Adobe Reader (beta)**  
  **Standard**: Inte konfigurerat  
  Regel: [blockera Adobe Reader från att skapa underordnade processer](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)  

  - **Inte konfigurerat**  
  - **Aktivera** -blockera underordnade processer som skapas från Adobe Reader.  
  - **Endast granskning**  

#### <a name="rules-to-prevent-office-macro-threats"></a>Regler för att förhindra Office-makrohot  

Blockera Office-appar från att vidta följande åtgärder:  

- **Office-appar som infogar i andra processer (inga undantag)**  
  **Standard**: Inte konfigurerat  
  Regel: [blockera Office-program från att injicera kod i andra processer](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes)  

  - **Inte konfigurerat**  
  - **Blockera** – blockera Office-appar från att injiceras i andra processer.  
  - **Endast granskning**  

- **Office-appar/-makron som skapar körbart innehåll**  
  **Standard**: Inte konfigurerat  
  Regel: [blockera Office-program från att skapa körbart innehåll](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content)  

  - **Inte konfigurerat**  
  - **Blockera** – blockera Office-appar och makron från att skapa körbart innehåll.  
  - **Endast granskning**  

- **Office-appar som startar underordnade processer**  
  **Standard**: Inte konfigurerat  
  Regel: [Blockera alla Office-program från att skapa underordnade processer](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)  

  - **Inte konfigurerat**  
  - **Blockera** – blockera Office-appar från att starta underordnade processer.  
  - **Endast granskning**  
  
- **Win32-importer från Office-makrokod**  
  **Standard**: Inte konfigurerat  
  Regel: [blockera Win32 API-anrop från Office-makron](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros)  

  - **Inte konfigurerat**  
  - **Blockera** – blockera Win32-importer från makrokod i Office.  
  - **Endast granskning**  
  
- **Skapa process från produkter för Office-kommunikation**  
  **Standard**: Inte konfigurerat  
  Regel: [blockera program från Office-kommunikation från att skapa underordnade processer](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)  

  - **Inte konfigurerat**  
  - **Aktivera** skapande av underordnade processer från appar för Office-kommunikation.  
  - **Endast granskning**  

#### <a name="rules-to-prevent-script-threats"></a>Regler för att förhindra skripthot  

Blockera följande för att hjälpa till att förhindra skripthot:  

- **Dold js/vbs/ps/makrokod**  
  **Standard**: Inte konfigurerat  
  Regel: [blockera körning av potentiellt fördunklade skript](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts)    

  - **Inte konfigurerat**  
  - **Blockera** – blockera alla fördunklade JS/vbs/PS/makrokod.  
  - **Endast granskning**  

- **js/vbs kör nyttolaster som laddats ned från Internet (inga undantag)**  
  **Standard**: Inte konfigurerat  
  Regel: [blockera java script eller VBScript från att starta hämtat körbart innehåll](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content)  

  - **Inte konfigurerat**  
  - **Blockera** – blockera JS/vbs från att köra nytto last som hämtats från Internet.  
  - **Endast granskning**  

- **Skapa process från PSExec- och WMI-kommandon**  
  **Standard**: Inte konfigurerat  
  Regel: [Blockera processer som skapas från PSExec- och WMI-kommandon](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)  

  - **Inte konfigurerat**  
  - **Blockera** – blockera skapande av processer från PSExec- och WMI-kommandon.  
  
  - **Endast granskning**  

- **Ej betrodda och osignerade processer som körs via USB**  
  **Standard**: Inte konfigurerat  
  Regel: [Blockera obetrodda och osignerade processer som körs via USB](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb)    

  - **Inte konfigurerat**  
  - **Blockera** – blockera obetrodda och osignerade processer som körs via USB.  
  - **Endast granskning**  
  
- **Körbara filer som inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista**  
  **Standard**: Inte konfigurerat  
  Regel: [Blockera körbara filer från att köras om de inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)    

  - **Inte konfigurerat**  
  - **Blockera** – blockera körbara filer från att köras om de inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista.  
  - **Endast granskning**  

#### <a name="rules-to-prevent-email-threats"></a>Regler för att förhindra e-posthot  

Blockera följande för att hjälpa till att förhindra e-posthot:  

- **Körning av körbart innehåll (exe, dll, ps, js, vbs, osv.) som har tagits bort från e-post (webbaserad e-post/e-postklient) (inga undantag)**  
  **Standard**: Inte konfigurerat  
  Regel: [blockera körbart innehåll från e-postklient och webbaserad e-post](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail)  

  - **Inte konfigurerat**  
  - **Blockera** – blockera körning av körbart innehåll (exe, dll, ps, js, vbs, osv.) som har tagits bort från e-post (webbaserad e-post/e-postklient).  
  - **Endast granskning**  

#### <a name="rules-to-protect-against-ransomware"></a>Regler för skydd mot utpressningstrojaner  

- **Avancerat skydd mot utpressningstrojaner**  
  Standard: ej konfigurerad  
  Regel: [Använd avancerat skydd mot utpressnings tro Jan](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware)  

  - **Inte konfigurerat**  
  - **Aktivera** – använd aggressivt skydd mot utpressningstrojan.  
  - **Endast granskning**  

#### <a name="attack-surface-reduction-exceptions"></a>Undantag för att minska attackytan

- **Filer och mappar som ska uteslutas från reglerna för att minska attackytan**  
  Defender CSP: [AttackSurfaceReductionOnlyExclusions](https://go.microsoft.com/fwlink/?linkid=872981)  

  - **Importera** en. csv-fil som innehåller filer och mappar som ska undantas från reglerna för minskning av attack ytan.  
  - **Lägg till** lokala filer eller mappar manuellt.  

> [!IMPORTANT]  
> För att tillåta korrekt installation och körning av verksamhetsspecifika Win32-appar bör inställningar för program mot skadlig kod undanta följande kataloger från att genomsökas:  
> **På X64-klientdatorer**:  
> *C:\Program Files (x86)\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  
>  
> **På X86-klientdatorer**:  
> *C:\Program Files\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  

### <a name="controlled-folder-access"></a>Reglerad mappåtkomst  

Hjälp till att [skydda värdefulla data](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) från skadliga appar och hot, till exempel utpressningstrojaner.  

- **Mappskydd**  
  **Standard**: Inte konfigurerat  
  Defender CSP: [EnableControlledFolderAccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  Skydda filer och mappar från obehöriga ändringar av oönskade appar.  

  - **Inte konfigurerat**  
  - **Aktivera**  
  - **Endast granskning**  
  - **Blockera diskändring**  
  - **Granska diskändring**  

  När du väljer en annan konfiguration än *inte konfigurerad*kan du konfigurera:  
  - **Lista över appar som har åtkomst till skyddade mappar**  
    Defender CSP: [ControlledFolderAccessAllowedApplications](https://go.microsoft.com/fwlink/?linkid=872616)  

    - **Importera** en. csv-fil som innehåller en app-lista.  
    - **Lägg till** appar i den här listan manuellt.  

  - **Lista över ytterligare mappar som behöver skyddas**  
    Defender CSP: [ControlledFolderAccessProtectedFolders](https://go.microsoft.com/fwlink/?linkid=872617)  

    - **Importera** en. csv-fil som innehåller en mapplista.  
    - **Lägg till** mappar i den här listan manuellt.  

### <a name="network-filtering"></a>Nätverksfiltrering  

Blockera utgående anslutningar från alla appar till IP-adresser eller domäner med låga rykte. Nätverks filtrering stöds i både gransknings-och spärr läge.  

- **Nätverksskydd**  
  **Standard**: Inte konfigurerat  
  Defender CSP: [EnableNetworkProtection](https://go.microsoft.com/fwlink/?linkid=872618)  

  Avsikten med den här inställningen är att skydda slutanvändare från appar med åtkomst till nätfiske-bedrägerier, webbplatser för sårbarhets värd och skadligt innehåll på Internet. Det förhindrar också att tredje parts webbläsare ansluter till farliga platser.  

  - **Inte konfigurerad** – inaktivera den här funktionen. Användare och appar blockeras inte från att ansluta till farliga domäner. Administratörer kan inte se den här aktiviteten i Windows Defender Security Center.  
  - **Aktivera** – aktivera nätverks skydd och blockera användare och appar från att ansluta till farliga domäner. Aktivera kan se den här aktiviteten i Windows Defender Security Center.  
  - **Endast granskning**: – användare och appar blockeras inte från att ansluta till farliga domäner. Aktivera kan se den här aktiviteten i Windows Defender Security Center.  

### <a name="exploit-protection"></a>Sårbarhetsskydd  
 

- **Ladda upp XML**  
  **Standard**: *Inte konfigurerat*  

  Om du vill använda sårbarhets skydd för att [skydda enheter från sårbarheter](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)skapar du en XML-fil som innehåller de inställningar för system-och program minskning som du vill ha. Det finns två metoder för att skapa XML-filen:  

  - *PowerShell* – använd en eller flera av *Get-ProcessMitigation-* , *Set-ProcessMitigation-* och *ConvertTo-ProcessMitigationPolicy* PowerShell-cmdlets. Cmdlets konfigurerar åtgärdsinställningar och exporterar en XML-representation av dem.  

  - *Gränssnittet för Windows Defender Säkerhetscenter* – i Windows Defender Säkerhetscenter klickar du på App- & webbläsarkontroll och bläddrar sedan längst ned på skärmen för att hitta Sårbarhetsskydd. Använd först flikarna Systeminställningar och Programinställningar för att konfigurera minskningsinställningar. Leta sedan reda på länken Exportera inställningar längst ned på skärmen för att exportera en XML-återgivning av dem.  

- **Användar redigering av gränssnittet för sårbarhets skydd**  
  **Standard**: Inte konfigurerat  
  ExploitGuard CSP: [ExploitProtectionSettings](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **Blockera** – Ladda upp en XML-fil som gör att du kan konfigurera minnes-, kontroll flödes-och princip begränsningar. Inställningarna i XML-filen kan användas för att blockera ett program från kryphål.  
  - **Inte konfigurerad** – ingen anpassad konfiguration används.  

## <a name="windows-defender-application-control"></a>Windows Defender Application Control  

Välj ytterligare appar som antingen måste granskas av eller som är betrodda att köras av Windows Defender Application Control. Windows-komponenter och alla appar från Windows Store är automatiskt betrodda att köras.  


- **Kod integritets principer för program kontroll**  
  **Standard**: Inte konfigurerat  
   CSP: [APPLOCKER CSP](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **Framtvinga** – Välj kod integritets principer för program kontroll för användarnas enheter.  
  
    När det är aktiverat kan programkontrollen endast inaktiveras genom att ändra läget från *Framtvinga* till *Endast granskning*. Om du ändrar läget från *Framtvinga* till *Inte konfigurerad* fortsätter programkontrollen att tillämpas på tilldelade enheter.  

  - **Inte konfigurerad** – program kontroll har inte lagts till i enheter. Inställningar som tidigare lades till fortsätter dock att tillämpas på tilldelade enheter. 
 
  - **Endast granskning** – program blockeras inte. Alla händelser loggas i de lokala klient loggarna.  

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard  

Windows Defender Credential Guard skyddar mot attacker för stöld av autentiseringsuppgifter. Den isolerar hemligheter så att endast privilegierad programvara kan komma åt dem.  

- **Credential Guard**  
  **Standard**: Inaktivera  
  [DeviceGuard CSP](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **Inaktivera** – stänger av Credential Guard via fjärranslutning om det tidigare har slagits på med alternativet **Aktivera utan UEFI-lås**.  

  - **Aktivera med UEFI-lås** – Credential Guard kan inte inaktiveras fjärrstyrt med en registernyckel eller grupprincip.  

    > [!NOTE]
    > Om du använder den här inställningen och sedan vill inaktivera Credential Guard, måste du ange grupprincipen till **Inaktiverad**. Och avmarkera UEFI-konfigurationsinformationen fysiskt från varje dator. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.  

  - **Aktivera utan UEFI-lås** – tillåter att Credential Guard inaktiveras fjärrstyrt med hjälp av grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 version 1511 eller senare.  

  När du *aktiverar* Credential Guard aktiveras även följande nödvändiga funktioner:  
  
  - **Virtualiseringsbaserad säkerhet** (VBS)  
    Aktiveras vid nästa omstart. Virtualiseringsbaserad säkerhet använder Windows Hypervisor för att ge stöd för säkerhetstjänster.  
  - **Säker start med direkt minnesåtkomst**  
    Aktiverar VBS med säker start och DMA-skydd (direkt minnesåtkomst). DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade.  

## <a name="windows-defender-security-center"></a>Windows Defender Säkerhetscenter  

Windows Defender Security Center fungerar som en separat app eller process från var och en av de enskilda funktionerna. Den visar aviseringar via Action Center. Den fungerar som en insamlare eller enskild plats för att visa status och köra konfiguration för var och en av funktionerna. Läs mer i dokumentationen till [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).  

### <a name="windows-defender-security-center-app-and-notifications"></a>Appen Windows Defender Säkerhetscenter och meddelanden  

Blockera slutanvändarens åtkomst till olika delar av appen Windows Defender Säkerhetscenter. Om ett avsnitt döljs blockeras även relaterade meddelanden.  

- **Skydd mot virus och hot**  
  **Standard**: Inte konfigurerat  
  WindowsDefenderSecurityCenter CSP: [DisableVirusUI](https://go.microsoft.com/fwlink/?linkid=873662)  

  Konfigurera om slutanvändarna ska kunna visa skydds ytan för virus och hot i Windows Defender Security Center. Om du döljer det här avsnittet blockeras även alla meddelanden som rör virus-och hot skydd.  

  - **Inte konfigurerat**  
  - **Dölj**  

- **Skydd mot utpressnings tro Jan**  
  **Standard**: Inte konfigurerat  
  WindowsDefenderSecurityCenter CSP: [HideRansomwareDataRecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  Konfigurera om slutanvändare ska kunna visa skydds ytan för utpressnings områden i Windows Defender Security Center. Om du döljer det här avsnittet blockeras även alla meddelanden som rör utpressnings skydd.  

  - **Inte konfigurerat**  
  - **Dölj**  

- **Konto skydd**  
  **Standard**: Inte konfigurerat  
  WindowsDefenderSecurityCenter CSP: [DisableAccountProtectionUI](https://go.microsoft.com/fwlink/?linkid=873666)  

  Konfigurera om slutanvändarna ska kunna Visa konto skydds ytan i Windows Defender Security Center. Om du döljer det här avsnittet blockeras även alla meddelanden relaterade till konto skydd.  

  - **Inte konfigurerat**  
  - **Dölj**  

- **Brandväggs- och nätverksskydd**  
  **Standard**: Inte konfigurerat  
  WindowsDefenderSecurityCenter CSP: [DisableNetworkUI](https://go.microsoft.com/fwlink/?linkid=873668)  

  Konfigurera om slutanvändarna ska kunna se sektionen brand vägg och nätverks skydd i Windows Defender Security Center. Om du döljer det här avsnittet blockeras även alla meddelanden som rör brand vägg och nätverks skydd.  

  - **Inte konfigurerat**  
  - **Dölj**  

- **App- och webbläsarkontroll**  
  **Standard**: Inte konfigurerat  
  WindowsDefenderSecurityCenter CSP: [DisableAppBrowserUI](https://go.microsoft.com/fwlink/?linkid=873669)  

  Konfigurera om slutanvändarna ska kunna visa kontroll områden för appar och webbläsare i Windows Defender Security Center. Om du döljer det här avsnittet blockeras även alla meddelanden som rör app-och webb läsar kontroll.  

  - **Inte konfigurerat**  
  - **Dölj**  

- **Maskin varu skydd**  
  **Standard**: Inte konfigurerat  
  WindowsDefenderSecurityCenter CSP: [DisableDeviceSecurityUI](https://go.microsoft.com/fwlink/?linkid=873670)  

  Konfigurera om slutanvändare ska kunna se avsnittet maskin varu skydd i Windows Defender Security Center. Om du döljer det här avsnittet blockeras även alla meddelanden som rör maskin varu skydd.  

  - **Inte konfigurerat**  
  - **Dölj**  

- **Enhetsprestanda och hälsa**  
  **Standard**: Inte konfigurerat  
  WindowsDefenderSecurityCenter CSP: [DisableHealthUI](https://go.microsoft.com/fwlink/?linkid=873671)  

  Konfigurera om slutanvändarna ska kunna se området för enhets prestanda och hälsa i Windows Defender Security Center. Om du döljer det här avsnittet blockeras även alla meddelanden som rör enhetens prestanda och hälsa.  
  
  - **Inte konfigurerat**  
  - **Dölj**  

- **Familjealternativ**  
  **Standard**: Inte konfigurerat  
  WindowsDefenderSecurityCenter CSP: [DisableFamilyUI](https://go.microsoft.com/fwlink/?linkid=873673)  

  Konfigurera om slutanvändare ska kunna se avsnittet familje alternativ i Windows Defender Security Center. Om du döljer det här avsnittet blockeras även alla meddelanden som är relaterade till familje alternativ.  
  
  - **Inte konfigurerat**  
  - **Dölj**  

- **Aviseringar från områdena som visas i appen**  
  **Standard**: Inte konfigurerat  
  WindowsDefenderSecurityCenter CSP: [DisableNotifications](https://go.microsoft.com/fwlink/?linkid=873675)  

  Välj vilka meddelanden som ska visas för slutanvändare. Meddelanden som är mindre viktiga omfattar sammanfattningar av Windows Defender Antivirus-aktivitet, inklusive meddelanden när genomsökningar har slutförts. Alla andra meddelanden anses viktiga.  

  - **Inte konfigurerat**  
  - **Blockera icke-kritiska meddelanden**  
  - **Blockera alla meddelanden**  

- **Windows Security Center-ikonen i system fältet**  
  **Standard**: Inte konfigurerat  

  Konfigurera visning av meddelande fältets kontroll. Användaren måste antingen logga ut och logga in eller starta om datorn för att den här inställningen ska börja gälla.  
  
  - **Inte konfigurerat**  
  - **Dölj**  

- **Rensa TPM-knapp**  
  **Standard**: Inte konfigurerat  

  Konfigurera visning av knappen rensa TPM.  
  
  - **Inte konfigurerat**  
  - **Inaktivera**  

- **Varning om uppdatering av inbyggd TPM-programvara**  
  **Standard**: Inte konfigurerat  
  
  Konfigurera visning av inbyggd uppdatering av TPM-programvara när en sårbar inbyggd program vara upptäcks.  

  - **Inte konfigurerat**  
  - **Dölj**  

- **Skydd mot manipulering**  
  **Standard**: Inte konfigurerat

  Aktivera eller inaktivera manipulering av skydd på enheter. Om du vill använda skydd mot manipulering måste du [integrera Microsoft Defender Avancerat skydd med Intune](advanced-threat-protection.md)och ha [Enterprise Mobility + Security E5-licenser](../fundamentals/licenses.md).  
  - **Inte konfigurerad** – ingen ändring görs i enhets inställningarna.
  - **Aktiverat** skydd av manipulering är aktiverat och begränsningar tillämpas på enheter.
  - **Inaktiverat** skydd mot manipulering är inaktiverat och begränsningar är inte tvingande.

### <a name="it-contact-information"></a>IT-kontaktuppgifter  

Ange IT-kontaktuppgifter som ska visas i appen Windows Defender Säkerhetscenter och i appmeddelanden.  

Du kan välja **Visa i app och i aviseringar**, **Visa endast i app**, **Visa endast i aviseringar** eller **Visa inte**. Ange **IT-organisationens namn** och minst ett av följande kontaktalternativ:  


- **IT-kontaktuppgifter**  
  **Standard**: Visa inte  
  WindowsDefenderSecurityCenter CSP: [EnableCustomizedToasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  Konfigurera var kontakt information ska visas för slutanvändarna.  
  
  - **Visa i app och i aviseringar**  
  - **Visa endast i app**  
  - **Visa endast i meddelanden**  
  - **Visa inte**  

  När du har konfigurerat att Visa kan du konfigurera följande inställningar:  

  - **IT-organisationsnamn**  
    **Standard**: *Inte konfigurerat*  
    WindowsDefenderSecurityCenter CSP: [företags namn](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **IT-avdelningens telefonnummer eller Skype-ID**  
    **Standard**: *Inte konfigurerat*  
    WindowsDefenderSecurityCenter CSP: [telefon](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **IT-avdelningens e-postadress**  
    **Standard**: *Inte konfigurerat*  
    WindowsDefenderSecurityCenter CSP: [e-post](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **URL till IT-supportwebbplatsen**  
    **Standard**: *Inte konfigurerat*  
    WindowsDefenderSecurityCenter CSP: [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>Säkerhetsalternativ för lokal enhet  

Använd dessa alternativ för att konfigurera de lokala säkerhetsinställningarna på Windows 10-enheter.  

### <a name="accounts"></a>Konton  

- **Lägg till nya Microsoft-konton**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **Blockera** – förhindra att användare lägger till nya Microsoft-konton på enheten.  
  - **Inte konfigurerad** – användare kan använda Microsoft-konton på enheten.  

- **Fjärrinloggning utan lösenord**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **Aktivera** – tillåter endast lokala konton med tomma lösenord att logga in med enhetens tangentbord.  
   - **Inte konfigurerad** – tillåter att lokala konton med tomma lösenord loggar in från andra platser än den fysiska enheten.  

#### <a name="admin"></a>Administratör  

- **Lokalt administratörskonto**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **Blockera** Förhindra användning av ett lokalt administratörs konto.  
  - **Inte konfigurerat**  

- **Byt namn på administratörskonto**  
  **Standard**: *Inte konfigurerat*  
  LocalPoliciesSecurityOptions CSP: [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  Definiera att ett annat kontonamn ska associeras med säkerhetsidentifieraren (SID) för kontot ”Administratör”.  

 #### <a name="guest"></a>Gäst  

- **Gästkonto**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [LocalPoliciesSecurityOptions](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **Blockera** – förhindra att ett gäst konto används.  
  - **Inte konfigurerat**  

- **Byt namn på gästkonto**  
  **Standard**: *Inte konfigurerat*  
  LocalPoliciesSecurityOptions CSP: [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  Definiera att ett annat kontonamn ska associeras med säkerhetsidentifieraren (SID) för kontot ”Gäst”.  

### <a name="devices"></a>Egenskaper  

- **Koppla bort enhet från dockningsstation utan inloggning**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **Blockera** – användarna kan trycka på den fysiska utmatningsknappen på en dockad bärbar enhet för att på ett säkert sätt koppla bort enheten.  
  - **Inte konfigurerad** – en användare måste logga in på enheten och få behörighet att koppla från enheten.  

- **Installera skrivardrivrutiner för delade skrivare**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **Aktiverat** – alla användare kan installera en skrivardrivrutin som en del av anslutningen till en delad skrivare.  
  - **Inte konfigurerad** – endast administratörer kan installera en skrivardrivrutin som en del av anslutningen till en delad skrivare.  

- **Begränsa CD-ROM-åtkomsten till lokala aktiva användare**  
  **Standard**: Inte konfigurerat  
  CSP: [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **Aktiverat** – endast den interaktivt inloggade användaren kan använda CD-ROM-media. Om den här principen är aktiverad och ingen är interaktivt inloggad används CD-ROM via nätverket.  
  - **Inte konfigurerad** – vem som helst har åtkomst till CD-ROM-skivan.  

- **Formatera och mata ut flyttbar media**  
  **Standard**: administratörer  
  CSP: [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  Definiera vem som får formatera och mata ut flyttbar NTFS-media:  
  - **Inte konfigurerat**  
  - **Administratörer**  
  - **Administratörer och privilegierade användare**  
  - **Administratörer och interaktiva användare**  

### <a name="interactive-logon"></a>Interaktiv inloggning  

- **Minuter av låsskärmsinaktivitet innan skärmsläckaren aktiveras**  
  **Standard**: *Inte konfigurerat*  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  Ange högsta antal minuter av inaktivitet på det interaktiva skrivbordets inloggningsskärm tills skärmsläckaren startar. (**0** - **99999**)  

- **Kräv CTRL+ALT+DEL för att logga in**:  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **Aktivera** – användare måste inte trycka på CTRL+ALT+DEL för att logga in.  
  - **Inte konfigurerad** – kräv att användarna trycker på CTRL+ALT+DEL innan de loggar in på Windows.  

- **Beteende vid borttagning av smartkort**  
  **Standard**: Lås arbetsstation   
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  Avgör vad som händer när smartkortet för en inloggad användare tas bort från smartkortsläsaren. Alternativen är:  

  - **Låsa arbetsstationen** – arbetsstationen låses när smartkortet tas bort. Med det här alternativet kan användare lämna området, ta med sig smartkortet och fortfarande skydda sessionen.  
  - **Ingen åtgärd**  
  - **Framtvinga utloggning** – användaren loggas ut automatiskt när smartkortet tas bort.  
  - **Koppla från om Remote Desktop Services-session** – om smartkortet tas bort så kopplas sessionen från utan att användaren loggas ut. Med det här alternativet kan användaren sätta i smartkortet och fortsätta sessionen senare, eller vid en annan dator med smartkortsläsare, utan att behöva logga in igen. Om sessionen är lokal fungerar den här principen precis som Lås arbetsstationen.  

#### <a name="display"></a>Visning  

- **Användarinformation på låsskärmen**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  Konfigurera användarinformation som visas när sessionen är låst. Om inställningen inte konfigureras visas användarens visningsnamn, domän och användarnamn.  

  - **Inte konfigurerat**  
  - **Användarens visningsnamn, domän och användarnamn**  
  - **Endast användarens visningsnamn**  
  - **Visa inte användarinformation**  

- **Dölj användarnamn vid inloggning**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **Aktivera** – Dölj användar namnet.  
  - **Inte konfigurerad** – Visa senaste användar namn.  

- **Dölj användar namn vid inloggning**
  **standard**: inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **Aktivera** – Dölj användar namnet.  
  - **Inte konfigurerad** – Visa senaste användar namn.  

- **Meddelanderubrik vid inloggning**  
  **Standard**: *Inte konfigurerat*  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  Ställ in meddelanderubrik för användare som loggar in.  

- **Meddelandetext vid inloggning**  
  **Standard**: *Inte konfigurerat*  
  LocalPoliciesSecurityOptions CSP: [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  Ställ in meddelandetext för användare som loggar in.  
  
### <a name="network-access-and-security"></a>Åtkomst till nätverket och säkerhet

- **Anonym åtkomst till namngivna pipes och resurser**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **Inte konfigurerat** – anonym åtkomst begränsas till resurs- och namngivna pipe-inställningar. Gäller för de inställningar som kan användas anonymt.  
  - **Blockera** – inaktivera den här principen och gör anonym åtkomst tillgänglig.  

- **Anonym uppräkning av SAM-konton**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **Inte konfigurerad** – anonyma användare kan räkna upp SAM-konton.  
  - **Blockera** – förhindra anonym uppräkning av SAM-konton.  

- **Anonym uppräkning av SAM-konton och resurser**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **Inte konfigurerat** – anonyma användare kan räkna upp namn på domänkonton och nätverksresurser.  
  - **Blockera** – blockera anonym uppräkning av SAM-konton och resurser. 

- **LAN Manager-hashvärdet lagras vid ändring av lösenord**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  Kontrol lera om hash-värdet för lösen ord lagras nästa gången du ändrar lösen ordet. 
  - **Inte konfigurerad** – hash-värdet är inte lagrat  
  - **Blockera** – LAN Manager (LM) lagrar hash-värdet för det nya lösen ordet.  

- **PKU2U-autentiseringsförfrågningar**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **Inte konfigurerad**– Tillåt PU2U-begäranden.  
  - **Blockera** – blockera PKU2U autentiseringsbegäranden till enheten.  

- **Begränsa RPC-fjärranslutningar till SAM**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **Inte konfigurerad** – Använd standard säkerhets beskrivningen, vilket kan göra det möjligt för användare och grupper att göra fjärr-RPC-anrop till Sam.
  - **Tillåt** -neka användare och grupper från att göra fjärr-RPC-anrop till hanteraren för konto säkerhet (SAM), som lagrar användar konton och lösen ord. Med **Tillåt** kan du också ändra standard-SDDL-strängen (Security Descriptor Definition Language) så att den uttryckligen tillåter eller nekar användare och grupper att göra dessa fjärran rop.  

    - **Säkerhetsbeskrivning**  
      **Standard**: *Inte konfigurerat*  
    
- **Minsta sessionssäkerhet för NTLM SSP-baserade klienter**  
  **Standard**: ingen  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  Den här säkerhetsinställningen gör att en server kan kräva förhandling av 128-bitarskryptering och/eller NTLMv2-sessionssäkerhet.  

  - **Inga**  
  - **Kräv NTLMv2-sessionssäkerhet**  
  - **Kräv 128-bitarskryptering**  
  - **NTLMv2 och 128-bitarskryptering**  
 
- **Minsta sessionssäkerhet för NTLM SSP-baserade servrar**  
  **Standard**: ingen  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  Den här säkerhetsinställningen avgör vilket autentiseringsprotokoll för anrop/svar som används för nätverksinloggningar.  

  - **Inga**  
  - **Kräv NTLMv2-sessionssäkerhet**  
  - **Kräv 128-bitarskryptering**  
  - **NTLMv2 och 128-bitarskryptering**  

- **Autentiseringsnivå för LAN Manager**  
  **Standard**: LM och NTLM  
  LocalPoliciesSecurityOptions CSP: [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM och NTLM**  
  - **LM, NTLM och NTLMv2**  
  - **NTLM**  
  - **Endast**  
  - **NTLMv2 och inte LM**  
  - **NTLMv2 och inte LM eller NTLM**  
  
- **Osäkra gäst inloggningar**  
  **Standard**: Inte konfigurerat  
  LanmanWorkstation CSP: [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  Om du aktiverar den här inställningen avvisar SMB-klienten oskyddade gäst inloggningar.  

  - **Inte konfigurerat**  
  - **Blockera** – SMB-klienten avvisar oskyddade gäst inloggningar.  

### <a name="recovery-console-and-shutdown"></a>Återställningskonsol och avstängning  

- **Rensa virtuell växlingsfil när du stänger**  
  **Standard**: Inte konfigurerat  
   LocalPoliciesSecurityOptions CSP: [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **Aktivera** – rensa den virtuella växlingsfilen när enheten stängs av.  
  - **Inte konfigurerad** – rensar inte det virtuella minnet.  

- **Stäng av utan inloggning**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **Blockera** – dölj avstängningsalternativet på Windows-inloggningsskärmen. Användarna måste logga in på enheten och sedan stänga av den.  
  - **Inte konfigurerad** – användare kan stänga av enheten från Windows-inloggningsskärmen.  

### <a name="user-account-control"></a>User account control  

- **UIA-integritet utan säker plats**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - **Blockera** – appar som finns på en säker plats i fil systemet körs bara med UIAccess-integritet.  
  - **Inte konfigurerad** – appar kan köras med UIAccess-integritet även om apparna inte finns på en säker plats i filsystemet.  

- **Virtualisera skrivfel för filer och register till platser per användare**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **Aktive rad** – program som skriver data till skyddade platser fungerar inte.  
  - **Ej konfigurerad** – programskrivfel omdirigeras under körning till definierade användarplatser för filsystemet och registret.  

- **Utöka endast behörighet för körbara filer som har signerats och verifierats**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **Aktiverat** – framtvinga verifiering av PKI-certifikatsökväg för en körbar fil innan den kan köras.  
  - **Inte konfigurerad** – framtvinga inte verifiering av PKI-certifikatsökväg innan en körbar fil kan köras.  

#### <a name="uia-elevation-prompt-behavior"></a>Beteende vid UIA:s fråga om utökad behörighet  

- **Fråga om utökade privilegier för administratörer**  
  **Standard**: Fråga efter medgivande för binära filer som inte tillhör Windows  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  Definiera funktionssätt för fråga om utökade privilegier för administratörer i Läge för administratörstillåtelse.  

  - **Inte konfigurerat**  
  - **Utöka privilegier utan att fråga**  
  - **Fråga efter autentiseringsuppgifter på det skyddade skrivbordet**  
  - **Fråga efter autentiseringsuppgifter**  
  - **Fråga efter medgivande**  
  - **Fråga efter medgivande för binära filer som inte tillhör Windows**  


- **Fråga om utökade privilegier för standardanvändare**  
  **Standard**: fråga efter autentiseringsuppgifter  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  Definiera funktionssätt för fråga om utökade privilegier för standardanvändare.  

  - **Inte konfigurerat**  
  - **Neka förfrågningar om höjd behörighet automatiskt**  
  - **Fråga efter autentiseringsuppgifter på det skyddade skrivbordet**  
  - **Fråga efter autentiseringsuppgifter**  

- **Vidarebefordra frågor om utökade privilegier till användarens interaktiva skrivbord**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - **Aktive rad** – alla höjnings begär Anden för att gå till den interaktiva användarens skriv bord snarare än det skyddade Skriv bordet. Eventuella principinställningar för beteende vid fråga om utökad behörighet för administratörer och standardanvändare används.  
  - **Inte konfigurerad** – framtvingar att alla förfrågningar om höjd behörighet går till det skyddade skrivbordet oavsett eventuella principinställningar för beteende vid fråga om utökad behörighet för administratörer och standardanvändare.

- **Fråga om utökad behörighet för appinstallationer**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **Aktiverat** – Programinstallationspaket identifieras inte eller inga frågor om utökade privilegier visas.
   - **Inte konfigurerad** – användaren uppmanas att ange ett administrativt användarnamn och lösenord när ett paket för programinstallation kräver utökade behörigheter.

- **Fråga från UIA om utökad behörighet utan skyddat skrivbord**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **Aktivera** – tillåter UIAccess-appar att fråga om utökade privilegier utan att använda skyddat skrivbord.  
- **Inte konfigurerad** – utökade uppmaningar använder ett säkert skriv bord.  

#### <a name="admin-approval-mode"></a>Använd läge för administratörstillåtelse  

- **Läge för administratörstillåtelse för inbyggd administratör**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **Aktiverad** – tillåter att det inbyggda administratörskontot använder läget för administratörstillåtelse. Alla åtgärder som kräver rättighetsökning uppmanar användaren att godkänna åtgärden.  
  - **Inte konfigurerad** – kör alla appar med fullständiga administratörsrättigheter.  

- **Kör alla administratörer i läge för administratörstillåtelse**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - **Aktive rad**– aktivera läge för administratörs godkännande.  
  - **Inte konfigurerat** – läge för administratörstillåtelse och alla relaterade UAC-principinställningar.  

### <a name="microsoft-network-client"></a>Microsoft-nätverksklient  

- **Signera kommunikationer digitalt (om servern tillåter)**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  Avgör om SMB-klienten förhandlar signering av SMB-paket.  
  - **Blockera** – SMB-klienten förhandlar aldrig om signering av SMB-paket.
  - **Inte konfigurerat** – Microsoft-nätverksklienten ber servern att utföra SMB-paketsignering när sessionen konfigureras. Om paketsignering är aktiverad på servern så förhandlas paketsignering.  

- **Skicka okrypterade lösenord till SMB-servrar från tredje part**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **Blockera** – SMB-omdirigeraren (Server Message Block) kan skicka lösenord i klartext till Microsoft SMB-servrar som inte har stöd för kryptering av lösenord under autentiseringen.  
  - **Inte konfigurerad** -blockera sändning av lösen ord i klartext. Lösen orden är krypterade.  

- **Signera kommunikation digitalt (alltid)**  
  **Standard**: Inte konfigurerat  
  LocalPoliciesSecurityOptions CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **Aktivera** – Microsoft-nätverksservern kommunicerar inte med en Microsoft-nätverksklient såvida inte klienten godkänner signering av SMB-paket.  
  - **Inte konfigurerad** – signering av SMB-paket förhandlas mellan klienten och servern.  

### <a name="microsoft-network-server"></a>Microsoft-nätverksserver  
  
- **Signera kommunikation digitalt (om klienten tillåter)**  
  **Standard**: Inte konfigurerat  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **Aktiverad** – Microsoft-nätverksservern förhandlar SMB-paketsignering såsom begärs av klienten. D.v.s. om paketsignering är aktiverat på servern, förhandlas paketsignering.  
  - **Inte konfigurerad** – SMB-klienten förhandlar aldrig om signering av SMB-paket.  

- **Signera kommunikation digitalt (alltid)**  
  **Standard**: Inte konfigurerat  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **Aktivera** – Microsoft-nätverksservern kommunicerar inte med en Microsoft-nätverksklient såvida inte klienten godkänner signering av SMB-paket.  
  - **Inte konfigurerad** – signering av SMB-paket förhandlas mellan klienten och servern.  

## <a name="xbox-services"></a>Xbox-tjänster

- **Spel Spara uppgift i Xbox Game**  
  **Standard**: Inte konfigurerat  
  CSP: [TaskScheduler/EnableXboxGameSaveTask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  Den här inställningen avgör om spel aktiviteten Spara i Xbox-spel är aktive rad eller inaktive rad.  
  - **Aktiverad**
  - **Inte konfigurerat**

- **Xbox tillbehörs hanterings tjänst**  
  **Standard**: manuell  
  CSP: [SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875481)  

  Den här inställningen avgör start typen för tillbehörs hanterings tjänsten.  
  - **Manuell**
  - **Automatiskt**
  - **Inaktiverad**

- **Tjänsten Xbox Live auth Manager**  
  **Standard**: manuell  
  CSP: [SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  Den här inställningen avgör start typen för tjänsten Live auth Manager.  
  - **Manuell**
  - **Automatiskt**
  - **Inaktiverad**
 
- **Xbox Live Game Save-tjänsten**  
  **Standard**: manuell  
  CSP: [SystemServices/ConfigureXboxLiveGameSaveServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875483)  

  Den här inställningen avgör start typen för Live Game Save-tjänsten.  
  - **Manuell**
  - **Automatiskt**
  - **Inaktiverad**

- **Xbox Live-nätverkstjänster**  
  **Standard**: manuell  
  CSP: [SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875484)  

  Den här inställningen avgör start typen för nätverks tjänsten.  
  - **Manuell**
  - **Automatiskt**
  - **Inaktiverad**

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](../configuration/device-profile-assign.md) och [övervaka dess status](../configuration/device-profile-monitor.md).  

Konfigurera inställningar för slutpunktsskydd på [macOS](endpoint-protection-macos.md)-enheter.  
