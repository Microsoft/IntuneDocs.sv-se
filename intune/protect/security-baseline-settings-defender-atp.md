---
title: Baslinjeinställningar för Intune-säkerhet för Microsoft Defender Avancerat skydd
titleSuffix: Microsoft Intune
description: Inställningar för säkerhetsbaslinjer som stöds av Intune för att hantera Microsoft Defender Avancerat skydd
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa3cb3481de6e1fdc3790b7330ac521772e252be
ms.sourcegitcommit: 5932da3ed8f52c7b0f0d71c1801f81c85952cf0c
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72923408"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Baslinjeinställningar för Intune för Microsoft Defender Avancerat skydd

Visa baslinjeinställningarna för Microsoft Defender Avancerat skydd (tidigare Windows Defender Avancerat skydd) som stöds av Microsoft Intune. Standardinställningarna för ATP-baslinjen (Advanced Threat Protection) representerar den rekommenderade konfigurationen för ATP och kanske inte överensstämmer med baslinjens standardvärden för andra säkerhetsbaslinjer.  

Baslinjen för Microsoft Defender Advanced Threat Protection är tillgänglig när din miljö uppfyller förhandskraven för att använda [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites). 

Den här bas linjen är optimerad för fysiska enheter och rekommenderas inte för användning på virtuella datorer (VM) eller VDI-slutpunkter. Vissa baslinjeinställningar kan påverka fjärranslutna interaktiva sessioner i virtualiserade miljöer. Mer information finns i [Öka efterlevnaden med säkerhetsbaslinjen i Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) i Windows-dokumentationen.

## <a name="application-guard"></a>Application Guard  
Mer information finns i [WindowsDefenderApplicationGuard CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp) i Windows-dokumentationen.  

När du använder Microsoft Edge Microsoft Defender Application Guard skyddas din miljö från webbplatser som inte är betrodda av din organisation. När användare besöker webbplatser som inte listas i din isolerade nätverksgräns, öppnas webbplatserna i en virtuell webbläsarsession i Hyper-V. Betrodda webbplatser definieras av en nätverksgräns.  

- **Application Guard** - *Settings/AllowWindowsDefenderApplicationGuard*  
  Välj *Ja* för att aktivera den här funktionen, som öppnar ej betrodda webbplatser i en virtualiserad Hyper-V-webbläsarcontainer. Då inställt till *Inte konfigurerad*, öppnas vilken plats (betrodd och ej betrodd) som helst på enheten och inte i en virtualiserad container.  

  **Standard**: Ja
 
  - **Externt innehåll på företagswebbplatser** - *inställningar/BlockNonEnterpriseContent*  
    Välj *Ja* för att blockera inläsning av innehåll från webbplatser som inte är godkända. Då inställt till *Inte konfigurerad* innebär det att icke-företagswebbplatser kan öppnas på enheten. 
 
    **Standard**: Ja

  - **Funktionssätt för Urklipp** - *Inställningar/ClipboardSettings*  
    Välj vilka åtgärder för kopiera och klistra in som tillåts mellan den lokala datorn och den virtuella Application Guard-webbläsaren.  Alternativen är:
    - Inte konfigurerat  
    - Blockera kopiera och klistra in mellan både PC och webbläsar-block båda. Blockera båda – Data kan inte överföras mellan datorn och den virtuella webbläsaren.  
    - Tillåt endast kopiering och inklistring från webbläsare till dator – data kan inte överföras från datorn till den virtuella webbläsaren.
    - Tillåt endast kopiera och klistra in från PC till webbläsare – data kan inte överföras från den virtuella webbläsaren till värd datorn.
    - Tillåt kopiera och klistra in mellan dator och webbläsare – det finns inget block för innehåll.  

    **Standard**: blockera kopiera och klistra in mellan datorer och webbläsare  

- **Isoleringsprincip för Windows-nätverk – domännamn på företagsnätverk**  
  Mer information finns i [CSP-princip – NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation) i Windows-dokumentationen.
  
  Ange en lista över Enterprise-resurser som domäner, IP-adressintervall och nätverksgränser som finns i molnet som Application Guard behandlar som företagswebbplatser.  

  **Standard**: securitycenter.windows.com

## <a name="application-reputation"></a>Klassificering  

Mer information finns i [CSP-princip – SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) i Windows-dokumentationen.

- **Block execution of unverified files** (Blockera körning av overifierade filer)  
    Blockera användare från att köra overifierade filer. Då inställt till *Inte konfigurerat* kan medarbetare ignorera SmartScreen-varningar och köra skadliga filer. Inställt till *Ja* så att medarbetare inte kan ignorera SmartScreen-varningar och köra skadliga filer.  
  
    **Standard**: Ja

- **Require SmartScreen for apps and files** (Kräv SmartScreen för appar och filer)  
  Inställt till *Ja* för att aktivera SmartScreen för Windows.  

  **Standard**: Ja

## <a name="attack-surface-reduction"></a>Minska attackytan  

- **Office apps launch child process type** (Office-appar startar underordnad processtyp)  
  [Regel för minskning av attackytan](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – Då inställt till *Blockera*, kommer Office-appar inte att kunna skapa underordnade processer. Office-appar inkluderar Word, Excel, PowerPoint, OneNote och Access. Att skapa en underordnad process är ett typiskt beteende i skadlig kod, särskilt vid makrobaserade attacker som försöker använda Office-appar för att starta eller hämta skadliga körbara filer.  

  **Standard**: Blockera

- **Script downloaded payload execution type** (Körningstyp för nedladdad nyttolast med skript)  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – Ange en identifieringsnivå för potentiellt oönskade program som laddar ned eller försöker att installera.  

  **Standard**: Blockera 

- **Prevent credential stealing type** (Förhindra typ av stöld av autentiseringsuppgifter)  
  Ställ in till *Aktivera* för att [Skydda härledda domänautentiseringsuppgifter med Credential Guard](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard). Windows Defender Credential Guard använder virtualiseringsbaserad säkerhet för att isolera hemligheter så att endast privilegierad programvara kan komma åt dem. Obehörig åtkomst till dessa hemligheter kan leda till stöld av autentiseringsuppgifter, till exempel Pass-The-Hash eller Pass-The-Ticket. Windows Defender Credential Guard förhindrar dessa attacker genom att skydda NTLM-hashvärden för lösenord, biljettbeviljande Kerberos-biljetter och autentiseringsuppgifter som lagras av program som autentiseringsuppgifter för en domän.  

  **Standard**: Aktivera

- **Email content execution type** (Körbara filtyper i e-postinnehåll)  
  [Regel för minskning av attackytan](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – Då inställt till *Blockera* blockerar den här regeln följande filtyper från att köras eller startas från ett e-postmeddelande i Microsoft Outlook eller webbaserad e-post (till exempel Gmail.com eller Outlook.com):  

  - Körbara filer (till exempel .exe, .dll eller .scr)  
  - Skriptfiler (till exempel en PowerShell .ps-, VisualBasic .vbs- eller JavaScript .js-fil)  
  - Skript för arkivfiler  

  **Standard**: Blockera

- **Adobe Reader-start i en underordnad process**  
  [Regel för minskning av attackytan](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – *Aktivera* den här regeln för att blockera Adobe Reader från att skapa en underordnad process. Via sociala tekniker eller kryphål kan skadlig kod ladda ned och starta ytterligare nyttolaster och bryta ut från Adobe Reader.  

  **Standard**: Aktivera

- **Script obfuscated macro code type** (Makrokod dold i skriptfiler)  
  [Regel för minskning av attackytan](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – Skadlig kod och andra hot kan försöka förvränga eller dölja skadlig kod i vissa skriptfiler. Den här regeln förhindrar att skript som verkar vara dolda körs.  
    
  **Standard**: Blockera

- **Untrusted USB process type** (Obetrodd USB-processtyp)  
  [Regel för minskning av attackytan](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – Då inställt till *Blockera*, kan osignerade eller ej betrodda körbara filer från flyttbara USB-enheter och SD-kort inte köras.

  Körbara filer inkluderar:
  - Körbara filer (till exempel .exe, .dll eller .scr)
  - Skriptfiler (till exempel en PowerShell .ps-, VisualBasic .vbs- eller JavaScript .js-fil)  

  **Standard**: Blockera

- **Office apps other process injection type** (Annan processinmatningstyp i Office-appar)  
  [Regel för minskning av attackytan](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – Då inställt till *Blockera*, kan inte Office-appar, inklusive Word, Excel, PowerPoint och OneNote, mata in kod i andra processer. Kodinmatning används vanligtvis av skadlig kod för att köra skadlig kod i ett försök att dölja aktivitet från motorer för virusgenomsökning.  

  **Standard**: Blockera

- **Office macro code allow Win32 imports type** (Office-makrokod tillåter Win32-importer)  
  [Regel för minskning av attackytan](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – Då inställt till *Blockera*, försöker den här regeln att blockera Office-filer som innehåller makrokod som kan importera Win32-DLL:er. Office-filer inkluderar Word, Excel, PowerPoint och OneNote. Skadlig kod kan använda makrokod i Office-filer för att importera och läsa in Win32-DLL:er, som sedan används för att göra API-anrop som leder till ytterligare infektion hela systemet.  

  **Standard**: Blockera

- **Office-kommunikationsappar startar i en underordnad process**  
  [Regel för minskning av attackytan](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – Då inställt till *Aktivera*, förhindrar den här regeln att Outlook skapar underordnade processer. Genom att blockera skapandet av en underordnad process skyddar regeln mot sociala manipulationsangrepp och förhindrar att koden missbrukar en svaghet i Outlook.  

  **Standard**: Aktivera

- **Office apps executable content creation or launch type** (Generering eller starttyp för körbart innehåll i Office-appar)  
  [Regel för minskning av attackytan](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – Då inställt till *Blockera*, kan inte Office-appar skapa körbart innehåll. Office-appar inkluderar Word, Excel, PowerPoint, OneNote och Access.  

  Den här regeln gäller typiska beteenden som används av misstänkta och skadliga tillägg och skript (tillägg) som skapar eller startar körbara filer. Det här är en vanlig teknik som används av skadlig kod. Tillägg hindras från att användas av Office-appar. De här tilläggen använder vanligtvis Windows Scripting Host (WSH-filer) för att köra skript som automatiserar vissa uppgifter eller tillhandahåller användargenererade tilläggsfunktioner.

  **Standard**: Blockera

## <a name="bitlocker"></a>BitLocker  

Mer information finns i [BitLocker-grupprincipinställningar](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings) i Windows-dokumentationen.  

- **Kryptera enheter**  
  Välj *Ja* för att aktivera BitLocker-enhetskryptering. Beroende på enheternas maskinvara och version av Windows, kan användare av enheter uppmanas att bekräfta att det inte finns någon kryptering från tredje part på enheten. Att aktivera Windows-kryptering medan kryptering från tredje part är aktiv kommer att återge enheten som instabil.  

   **Standard**: Ja

- **Bit locker removable drive policy** (Princip för BitLocker på flyttbara enheter)  
  Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering av borttagbara enheter. Företag styr krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du väljer *Ja* för att aktivera den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara dataenheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om dataenheten används i andra enheter som inte kör Windows 10 version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen. 

  Konfigurera följande inställningar för BitLockers princip för flyttbar enhet:

  - **Require encryption for write access** (Kräv kryptering för skrivåtkomst)  
    **Standard**: Ja

  - **Krypteringsmetod**  
    **Standard**: AES 128-bitars CBC

- **Kryptera minnes kort (endast mobil)** Om du väljer *Ja* krypteras den mobila enhetens minnes kort.  

   **Standard**: Ja

- **Bit locker fixed drive policy** (Princip för BitLocker på fasta enheter)  
  Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering av fasta enheter. Företag kan styra krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du aktiverar den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara dataenheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om dataenheten används i andra enheter som inte kör Windows 10 version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen.

  Konfigurera följande inställningar för BitLockers princip för fasta enhet:

  - **Require encryption for write access** (Kräv kryptering för skrivåtkomst)  
    **Standard**: Ja

  - **Krypteringsmetod**  
    **Standard**: AES 128-bitars XTS

- **Bit locker system drive policy** (Princip för BitLocker på systemenheter)  
  Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering av systemenheten. Företag kanske vill styra krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du aktiverar den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara dataenheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om dataenheten används i andra enheter som inte kör Windows 10 version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen.  

  Konfigurera följande inställningar för BitLockers princip för systemenhet:  

  - **Krypteringsmetod**  
    **Standard**: AES 128-bitars XTS

## <a name="device-control"></a>Enhetskontroll  

- **Sök igenom flyttbara drivrutiner vid fullständig genomsökning**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) – Om det är inställt på *Ja* söker Defender efter skadlig och oönskad programvara i flyttbara enheter, som flash-enheter, under en fullständig genomsökning. Defender Antivirus söker igenom alla filer på USB-enheter innan filerna på USB-enheten kan köras.

  Relaterade inställning i den här listan: *Defender/AllowFullScanOnMappedNetworkDrives*  

  **Standard**: Ja

- **Uppräkning av externa enheter som är inkompatibla med Kernel DMA-skydd**  
   Se *DmaGuard/DeviceEnumerationPolicy* i [CSP-princip – DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  Den här principen ger ökad säkerhet mot externa DMA-kompatibla enheter. Det möjliggör större kontroll över uppräkning av externa DMA-kompatibla enheter som inte är kompatibla med minnesisolering och sandbox-miljö för DMA-enhet.

  Den här principen börjar bara gälla när Kernel DMA-skydd stöds och aktiveras av datorns inbyggda programvara. Kernel DMA-skydd är en plattformsfunktion som inte kan styras av en princip eller av en enhets användare. Den måste stödjas av systemet vid tidpunkten för tillverkning. 

  Om du vill kontrollera om systemet har stöd för Kernel DMA-skydd, kör MSINFO32.exe i systemet och granska fältet *Kernel DMA-skydd* på sammanfattningssidan.  

  Alternativen är: 
  - *Standard för enheten* – Efter inloggning eller när skärmen låsts upp, tillåts enheter med drivrutiner som är kompatibla med DMA-ommappning att räknas upp när som helst. Enheter med drivrutiner som är inkompatibla med DMA-ommappning kommer endast att uppräknas efter att användaren låser upp skärmen
  - *Tillåt alla* – Alla externa DMA-kompatibla PCIe-enheter räknas upp när som helst
  - *Blockera alla* – Enheter med drivrutiner som är kompatibla med DMA-ommappning tillåts att räkna upp när som helst. Enheter med drivrutiner som är inkompatibla för DMA-ommappning får aldrig starta och utföra DMA när som helst.

  **Standard**: Standard för enheten

- **Hardware device installation by device identifiers** (Installation av maskinvaruenheter efter enhets-ID)  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) – Med denna princip anger du en lista med ID:n för Plug and Play-maskinvara och kompatibla ID:n för enheter som Windows hindrar från att installeras. Den här inställningen har företräde framför alla andra principinställningar som tillåter att Windows installerar en enhet. Om du aktiverar den här principinställningen (inställd på *Blockera installation av maskinvaruenheter*), hindras Windows från att installera en enhet vars maskinvaru-ID eller kompatibla ID visas i listan som du skapar. Om du aktiverar den här principen på en fjärrskrivbordsserver påverkar principen omdirigeringen av de angivna enheterna från en fjärrskrivbordsklient till fjärrskrivbordsservern. Om du inaktiverar eller inte konfigurerar den här principinställningen (inställd på *Tillåt installation av maskinvaruenheter*), kan enheter installera och uppdatera beroende på om de tillåts eller förhindras av andra principinställningar.  

  **Standard**: Blockera installation av maskinvaruenheter  

  När *Blockera installation av maskinvaruenheter* är valt, är följande inställningar tillgängliga.
  - **Remove matching hardware devices** (Ta bort matchande maskinvaruenheter)  
    Den här inställningen är endast tillgänglig när *Hardware device installation by device identifiers* (Installation av maskinvaruenheter efter enhets-ID) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).  

    **Standard**: Ja

  - **Hardware device identifiers that are blocked** (ID:n för blockerade maskinvaruenheter)  
    Den här inställningen är endast tillgänglig när *Hardware device installation by device identifiers* (Installation av maskinvaruenheter efter enhets-ID) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter). Expandera alternativet om du vill konfigurera den här inställningen, välj **+ Lägg till**, och ange sedan maskinvarans enhets-ID som du vill blockera.  

    **Standard**: PCI\CC_0C0A

- **Block direct memory access** (Blockera direkt minnesåtkomst)  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) – Använd den här principinställningen för att blockera direkt minnesåtkomst (DMA) för alla underordnade PCI-portar med hot plug-stöd tills en användare loggar in i Windows. När en användare loggar in räknar Windows upp PCI-enheterna som är anslutna till PCI-portarna med hot plug-stöd. Varje gång användaren låser datorn blockeras DMA på PCI-portarna med hot plug-stöd utan underordnade enheter tills användaren loggar in igen. Enheter som räknades upp när datorn var upplåst fortsätter att fungera tills de kopplas från. 

  Den här principinställningen tillämpas endast när BitLocker- eller enhetskryptering är aktiverat.  

  **Standard**: Ja


- **Hardware device installation by setup classes** (Installation av maskinvaruenheter efter installationsklass)  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) – Med den här principen kan du ange en lista med klass-GUID för enhetsinstallation för enhetsdrivrutiner som Windows hindrar från att installeras. Den här inställningen har företräde framför alla andra principinställningar som tillåter att Windows installerar en enhet. Om du aktiverar den här principinställningen (inställd till *Blockera installation av maskinvaruenheter*), kan inte Windows installera eller uppdatera enhetsdrivrutiner vars klass-GUID för enhetsinstallation visas i listan du skapar. Om du aktiverar den här principinställningen på en fjärrskrivbordsserver påverkar principinställningen omdirigeringen av de angivna enheterna från en fjärrskrivbordsklient till fjärrskrivbordsservern. Om du inaktiverar eller inte konfigurerar den här principinställningen (inställd på *Tillåt installation av maskinvaruenheter*), kan Windows installera och uppdatera enheter beroende på om de tillåts eller förhindras av andra principinställningar.  

  **Standard**: Blockera installation av maskinvaruenheter

  När *Blockera installation av maskinvaruenheter* är valt, är följande inställningar tillgängliga.  

  - **Remove matching hardware devices** (Ta bort matchande maskinvaruenheter)  
    Den här inställningen är endast tillgänglig när *Hardware device installation by setup classes* (Installation av maskinvaruenheter efter installationsklasser) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).  
 
    **Standard**: Ja  

  - **Hardware device identifiers that are blocked** (ID:n för blockerade maskinvaruenheter)  
    Den här inställningen är endast tillgänglig när Installation av maskinvaruenheter efter installationsklasser har inställningen Blockera installation av maskinvaruenheter. Expandera alternativet om du vill konfigurera den här inställningen, välj **+ Lägg till**, och ange sedan maskinvarans enhets-ID som du vill blockera.  
 
    **Standard**: {d48179be-EC20-11D1-b6b8-00c04fa372a7}

## <a name="endpoint-detection-and-response"></a>Slutpunktsidentifiering och svar  
Mer information finns i [WindowsAdvancedThreatProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp) i Windows-dokumentationen.  

- **Skicka frekvensvärde för telemetrirapportering** - *Configuration/TelemetryReportingFrequency*

  Skicka frekvensvärde för telemetrirapportering för Microsoft Defender Avancerat skydd.  

  **Standard**: Ja

- **Exempeldelning för alla filer** - *Configuration/SampleSharing* 

  Returnerar eller anger konfigurationsparametern för exempeldelning i Microsoft Defender Avancerat skydd.  

  **Standard**: Ja

## <a name="exploit-protection"></a>Sårbarhetsskydd  

- **Exploit protection XML** (XML för sårbarhetsskydd)  
  Mer information finns i [Importera, exportera och distribuera konfigurationer för sårbarhetsskydd](/windows/security/threat-protection/microsoft-defender-atp/import-export-exploit-protection-emet-xml) i Windows-dokumentationen.  

  Gör det möjligt för IT-administratören att distribuera en konfiguration som representerar önskade system- och programskyddsalternativ till alla enheter i organisationen. Konfigurationen representeras av en XML-sträng. 

  Sårbarhetsskydd hjälper dig att skydda enheter mot skadlig kod som utnyttjar kryphål för att spridas och infektera. Du kan använda Windows Security-appen eller PowerShell för att skapa en uppsättning skyddsåtgärder (kallas en konfiguration). Du kan exportera den här konfigurationen som en XML-fil och dela den med flera datorer i nätverket så att alla har samma uppsättning skyddsåtgärder.
 
  Du kan också konvertera och importera en befintlig EMET XML-konfigurationsfil till en XML-konfigurationsfil för sårbarhetsskydd.

- **Blockera åsidosättning av sårbarhetsskydd**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) – Inställt på *Ja* för att förhindra användare från att göra ändringar i inställningsområdet för sårbarhetsskydd i Windows Defender Security Center. Om du inaktiverar eller inte konfigurerar denna inställning kan lokala användare göra ändringar i inställningsområdet för sårbarhetsskydd.  
  **Standard**: Ja  

## <a name="microsoft-defender-antivirus"></a>Microsoft Defender Antivirus  

Mer information finns i [CSP-princip – Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) i Windows-dokumentationen.

- **Sök igenom skript som har lästs in via Microsoft-webbläsare**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) – Inställd på *Ja* för att tillåta Windows Defender-funktioner för skriptgenomsökning.  

  **Standard**: Ja

- **Scan incoming mail messages** (Sök igenom inkommande e-postmeddelanden)  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) – Inställd på *Ja* för att tillåta Windows Defender att skanna e-post.  

  **Standard**: Ja

- **Defender sample submission consent type** (Medgivandetyp i Defender för överföring av dataprover)  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) – Kontrollerar nivån för användarmedgivande i Windows Defender för att skicka data. Om nödvändigt godkännande redan har beviljats, skickar Windows Defender dem. Annars (och om användaren har valt att aldrig bli tillfrågad) startas användargränssnittet för att be om användarens medgivande (när *Molnlevererat skydd* är inställt på *Ja*) innan data skickas.  

  **Standard**: Skicka säkra prover automatiskt

- **kontrollsystem för nätverk (NIS)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) – Blockera skadlig trafik som identifierats av signaturer i Kontrollsystem för nätverk (NIS).  
 
  **Standard**: Ja

- **Intervall för signaturuppdatering (i timmar)**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) – Ange i timmar hur ofta enheten söker efter nya uppdateringar för Defender-signatur.  
 
  **Standard**: 4

- **Konfigurera låg CPU-prioritet för schemalagda genomsökningar**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) – Då inställt till *Ja*, är processorprioritet för genomsökningar inställt till lågt. När *Inte konfigurerad*, gör inga ändringar till processorprioritet för schemalagda genomsökningar.  

    **Standard**: Ja

- **Defender-blockering på åtkomstskydd**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) – Då inställt till *Ja*, är Windows Defender på NAP aktiverat.  

  **Standard**: Ja

- **Typ av systemgenomsökning som ska utföras**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) – Defender genomsökningstyp.  

  **Standard**: Snabbsökning

- **Sök igenom alla hämtningar**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) – Då inställt på *Ja*, söker Defender igenom alla hämtade filer och bifogade filer.  

  **Standard**: Ja

- **Dagar innan skadlig kod i karantän tas bort**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) – Ange hur många dagar objekt ska hållas i karantän i systemet innan de automatiskt bort. Om värdet är noll, tas aldrig objekt i karantän bort automatiskt.  

  **Standard**: 0

- **Schemalagd starttid för genomsökning**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) – Schemalägga en tid på dagen då Defender söker igenom enheter. 
  
  Relaterade alternativ i den här listan: *Defender/ScheduleScanDay*   

  **Standard**: 02.00

- **Molnlevererat skydd**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) – Då inställt till *Ja*, skickar Windows Defender information till Microsoft om något problem påträffas. Microsoft analyserar informationen, lär sig mer om problem som påverkar dig och andra kunder och erbjuder bättre lösningar.

  När den här principen är inställd till *Ja*, kan du använda *Medgivandetyp för Defender-exempelsändning* för att ge användare kontroll över att skicka information från sina enheter.  

  **Standard**: Ja

- **Defender potentially unwanted app action** (Potentiellt oönskad appåtgärd i Defender)  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – i Windows Defender Antivirus kan identifiera och hindra *potentiellt oönskade program* från att hämtas och installeras på slutpunkter i ditt nätverk. 
 
  - Då inställt till *Blockera*, blockerar Windows Defender potentiellt oönskade program och visar dem i historiken tillsammans med andra hot.
  - Då inställt till *Granskning*, identifierar Windows Defender potentiellt oönskade program men blockerar dem inte. Information om vilka program som Windows Defender skulle ha tagit åtgärder mot kan hittas genom att söka efter händelser som har skapats av Windows Defender i Loggboken.  
  - Då inställt till *Enhetsstandard*, är skydd mot oönskade program inaktiverat.  
 
  **Standard**: Blockera

- **Defender-molnet utökade tidsgränsen**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) – Ange den längsta tid som Windows Defender Antivirus ska blockera en fil under väntan på ett resultat från molnet. Den grundläggande mängd tid som Windows Defender väntar är 10 sekunder. Ytterligare tid som du anger här (upp till 50 sekunder) läggs till de 10 sekunderna. I de flesta fall går genomsökningen snabbare än maxvärdet. En utökning av tiden gör att molnet kan undersöka misstänkta filer noggrant.  

  Som standard är utökat tidsvärde 0 (inaktiverad). Intune rekommenderar att du aktiverar den här inställningen och anger minst 20 ytterligare sekunder.  
 
  **Standard**: 0

- **Sök igenom arkivfiler**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) – Inställd på *Ja* för att Windows Defender ska söka igenom arkivfiler.  

  **Standard**: Ja

- **Genomsökningsschema för Defender-system**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) – Schemalägg vilken dag Defender söker igenom enheter. 
 
  Relaterade alternativ i den här listan: *Defender/ScheduleScanTime*

  **Standard**: Användardefinierad

- **Beteendeövervakning**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) – Inställd på *Ja* för att aktivera beteendeövervakning för Windows Defender-funktioner. Inbäddad i Windows 10, övervakar funktionssätt i Windows Defender och samlar in och bearbetar beteendesignaler från operativsystemet och skickar dessa sensordata till din privata, isolerade molninstans av Microsoft Defender ATP.  

  **Standard**: Ja

- **Sök igenom filer öppnade från nätverksmappar**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) – Inställd till *Ja* för att Windows Defender ska söka igenom filer i nätverket. Användaren kan inte ta bort identifierad skadlig kod från skrivskyddade filer.  

  **Standard**: Ja

- **Defender cloud block level** (Molnblockeringsnivå i Defender)  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) – Använd den här principen för att avgöra hur aggressiva Windows Defender Antivirus är vid blockering och genomsökning av misstänkta filer. Alternativen är:

  - Hög – aggressiv blockering av okända filer och samtidigt optimering av klientprestanda (större risk för falska positiva resultat)
  - Hög plus – aggressiv blockering av okända filer och tillämpning av ytterligare skyddsåtgärder (kan påverka klientprestanda)
  - Nolltolerans – blockerar alla okända körbara filer

  **Standard**: Inte konfigurerat

- **Realtidsövervakning**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring) – Inställd på *Ja* för att tillåta övervakning för Windows Defender i realtid.  

  **Standard**: Ja

- **Gräns för processoranvändning under genomsökning**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) – Ange den högsta genomsnittliga CPU-användning i procent som Windows Defender kan använda under en genomsökning.  

  **Standard**: 50

- **Sök igenom mappade nätverksdrivrutiner vid fullständig genomsökning**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) – Inställd på *Ja* för att Windows Defender ska söka igenom filer i nätverket. Användaren kan inte ta bort identifierad skadlig kod från skrivskyddade filer,

  Relaterade inställning i den här listan: *Defender/AllowScanningNetworkFiles*

  **Standard**: Ja

- **Blockera användaråtkomst till Defender**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) – Inställd på *Ja* för att blockera slutanvändaråtkomst till Windows Defender-gränssnittet på enheten.  

  **Standard**: Ja

- **Snabbgenomsökning startades**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) – Schemalägger en tid på dagen då Defender kör en snabbgenomsökning.  

  **Standard**: 02.00

## <a name="windows-defender-firewall"></a>Windows Defender-brandvägg
Mer information finns i [CSP-brandvägg](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) i Windows-dokumentationen.

- **Inaktiv tid för säkerhetsassociation före borttagning** - *MdmStore/Global/SaIdleTime*   
  Säkerhetsassociationer tas bort om ingen nätverkstrafik har noterats för detta antal sekunder.  
  **Standard**: 300

- **Filöverföringsprotokoll** - *MdmStore/Global/DisableStatefulFtp*   
  Blockera tillståndskänsligt filöverföringsprotokoll (FTP).  
  **Standard**: Ja

- **Paketkö** - *MdmStore/Global/EnablePacketQueue*    
  Ange hur skalning för programvara på mottagarsidan aktiveras för den krypterade mottagningen och rensa flyttning av text framåt för scenariot med IPsec-tunnelgatewayen. Detta säkerställer att paketordningen bevaras.  
  **Standard**: Standard för enheten

- **Brandvägg för profildomän** - *FirewallRules/FirewallRuleName/Profiles*  
  Anger de profiler som regeln tillhör: domän, privat, offentlig. Det här värdet representerar profilen för nätverk som är anslutna till domäner.  

  Tillgängliga inställningar:  
  - **Unicast-svar på multicast-sändningar krävs**  
    **Standard**: Ja

  - **Auktoriserade programregler från sammanfogad grupprincip**  
    **Standard**: Ja

  - **Inkommande meddelanden blockerade**  
    **Standard**: Ja

  - **Globala portregler från sammanfogad grupprincip**  
    **Standard**: Ja

  - **Dolt läge blockerat**  
    **Standard**: Ja

  - **Brandväggen är aktiverad**  
    **Standard**: Tillåten

  - **Regler för anslutningssäkerhet från inte sammanfogad grupprincip**  
    **Standard**: Ja

  - **Principregler från inte sammanfogad grupprincip**  
    **Standard**: Ja

- **Brandvägg för offentlig profil** - *FirewallRules/FirewallRuleName/Profiles*  
  Anger de profiler som regeln tillhör: domän, privat, offentlig. Det här värdet representerar profilen för offentliga nätverk. Dessa nätverk klassificeras som offentliga av administratörer i server-värden. Klassificeringen sker första gången värden ansluter till nätverket. Dessa nätverk är vanligtvis på flygplatser eller kaféer och andra offentliga platser där peer-datorer i nätverket eller nätverksadministratörer inte är betrodda.  

  Tillgängliga inställningar:

  - **Inkommande anslutningar blockerade**  
    **Standard**: Ja 

  - **Unicast-svar på multicast-sändningar krävs**  
    **Standard**: Ja  

  - **Dolt läge krävs**  
    **Standard**: Ja 
 
  - **Utgående anslutningar krävs**  
    **Standard**: Ja  

  - **Auktoriserade programregler från sammanfogad grupprincip**  
    **Standard**: Ja  

  - **Inkommande meddelanden blockerade**  
    **Standard**: Ja  

  - **Globala portregler från sammanfogad grupprincip**  
    **Standard**: Ja

  - **Dolt läge blockerat**  
    **Standard**: Ja

  - **Brandväggen är aktiverad**  
    **Standard**: Tillåten  

  - **Regler för anslutningssäkerhet från inte sammanfogad grupprincip**  
    **Standard**: Ja  

  - **Inkommande trafik krävs**  
    **Standard**: Ja

  - **Principregler från inte sammanfogad grupprincip**  
    **Standard**: Ja  

- **Brandvägg för privat profil** - *FirewallRules/FirewallRuleName/Profiles*  
  Anger de profiler som regeln tillhör: domän, privat, offentlig. Det här värdet representerar profilen för privata nätverk.  

  Tillgängliga inställningar: 

  - **Inkommande anslutningar blockerade**  
    **Standard**: Ja

  - **Unicast-svar på multicast-sändningar krävs**  
    **Standard**: Ja

  - **Dolt läge krävs**  
    **Standard**: Ja

  - **Utgående anslutningar krävs**  
    **Standard**: Ja

  - **Inkommande meddelanden blockerade**  
    **Standard**: Ja

  - **Globala portregler från sammanfogad grupprincip**  
    **Standard**: Ja

  - **Dolt läge blockerat**  
    **Standard**: Ja  

  - **Brandväggen är aktiverad**  
    **Standard**: Tillåten

  - **Auktoriserade programregler från inte sammanfogad grupprincip**  
    **Standard**: Ja

  - **Regler för anslutningssäkerhet från inte sammanfogad grupprincip**  
    **Standard**: Ja

  - **Inkommande trafik krävs**  
    **Standard**: Ja

  - **Principregler från inte sammanfogad grupprincip**  
    **Standard**: Ja  

- **Kodningsmetod för i förväg delad nyckel för brandvägg**  
  **Standard**: UTF8

- **Verifiering av listan över återkallade certifikat**  
  **Standard**: Standard för enheten

## <a name="web--network-protection"></a>Webb- och nätverksskydd  

- **Network protection type** (Typ av nätverksskydd)  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)  – Med den här principen kan du aktivera eller inaktivera nätverksskydd i Windows Defender Exploit Guard. Nätverksskydd är en funktion i Windows Defender Exploit Guard som skyddar anställda som använder appar mot nätfiske, webbplatser som utnyttjar sårbarheter samt skadligt innehåll på Internet. Exempelvis hindras webbläsare från tredje part från att ansluta till farliga platser.  

  Då inställd på antingen *Aktivera* eller *Granskningsläge* kan användare inte inaktivera nätverksskydd och du kan använda Windows Defender Security Center för att visa information om anslutningsförsök.  
 
  - *Aktivera* blockerar användare och appar från att ansluta till farliga domäner.  
  - *Granskningsläge* blockerar inte användare och appar från att ansluta till farliga domäner.  

  Då inställd till *Användardefinierad*, blockeras användare och appar inte från att ansluta till farliga domäner och information om anslutningar är inte tillgänglig i Windows Defender Security Center.  

  **Standard**: Granskningsläge

- **Require SmartScreen for Microsoft Edge** (Kräv SmartScreen för Microsoft Edge)  
  [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) – Microsoft Edge använder som standard Windows Defender SmartScreen (aktiverat) för att skydda användarna mot potentiella nätfiskeförsök och skadlig programvara. Som standard är den här principen aktiverad (inställd på *Ja*), och då den är aktiverad förhindras användare från att stänga av Windows Defender SmartScreen.  När principen för en enhet inte är konfigurerad, kan användare inaktivera Windows Defender SmartScreen, vilket lämnar enheten oskyddad.  

  **Standard**: Ja
  
- **Block malicious site access** (Blockera åtkomst till skadliga webbplatser)  
  [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) – Som standard tillåter Microsoft Edge att användarna kringgår (ignorerar) Windows Defender SmartScreen-varningar om potentiellt skadliga webbplatser, så att användare kan fortsätta till webbplatsen. Med den här principen aktiverad (inställd till *Ja*) förhindrar Microsoft Edge användarna från att kringgå varningar och blockerar dem från att fortsätta till webbplatsen.  

  **Standard**: Ja

- **Block unverified file download** (Blockera nedladdning av overifierade filer)  
  [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) – Som standard tillåter Microsoft Edge att användarna kringgår (ignorerar) Windows Defender SmartScreen-varningar om potentiellt skadliga filer så att de kan fortsätta hämta overifierade filer. Med den här principen aktiverad (inställd på *Ja*), förhindras användare från att kringgå varningar och det går inte att hämta overifierade filer.  

  **Standard**: Ja

## <a name="windows-hello-for-business"></a>Windows Hello för företag  

Mer information finns i [PassportForWork CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp) i Windows-dokumentationen.

- **Konfigurera Windows Hello för företag** - *TenantId/principer/UsePassportForWork*    
  Windows Hello för företag är en alternativ metod för att logga in till Windows genom att ersätta lösenord, smartkort och virtuella smartkort.  

  - När det är inställt på *Ja*aktiverar du den här principen och enheten etablerar Windows Hello för företag.  
  - Om inställningen *inte är konfigurerad*, påverkar inte bas linjen enhetens princip inställning. Det innebär att om Windows Hello för företag är inaktiverat på en enhet förblir det inaktiverat. Om den är aktive rad förblir den aktive rad. 

  Du kan inte inaktivera Windows Hello för företag via den här bas linjen. Du kan inaktivera Windows Hello för företag när du konfigurerar [Windows-registrering](windows-hello.md)eller som en del av en enhets konfigurations profil för [identitets skydd](identity-protection-configure.md).  

Windows Hello för företag är en alternativ metod för att logga in till Windows genom att ersätta lösenord, smartkort och virtuella smartkort.  

  Om du aktiverar eller inte konfigurerar den här principinställningen etablerar enheten Windows Hello för företag. Om du inaktiverar den här principinställningen kan enheten inte etablera Windows Hello för företag för alla användare.

  Intune stöder inte inaktivering av Windows Hello. I stället kan du konfigurera principen till att aktivera Windows Hello för företag (Ja) eller att inte konfigurera Windows Hello direkt (inte konfigurerad). Om den inte har konfigurerats, kan en enhet ta emot konfigurationen via andra principer som kan aktivera eller inaktivera den här funktionen.  

  **Standard**: Ja  

- **Kräv gemener i PIN-kod** - *TenantId/principer/PINComplexity/LowercaseLetters*  
  **Standard**: Tillåten  

- **Kräv specialtecken i PIN-kod** - *TenantId/principer/PINComplexity/SpecialCharacters*  
  **Standard**: Tillåten  

- **Kräv versaler i PIN-kod** - *TenantId/principer/PINComplexity/UppercaseLetters*   
  **Standard**: Tillåten  

