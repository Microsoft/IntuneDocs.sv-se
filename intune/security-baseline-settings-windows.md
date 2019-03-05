---
title: Inställningar för Windows-säkerhetsbaslinjer för Intune
titleSuffix: Microsoft Intune
description: Inställningar för Windows-säkerhetsbaslinjer som stöds av Intune
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2dce0b743cd2944569e19a8106327f6735b1d6b
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231714"
---
# <a name="windows-security-baseline-settings-for-intune"></a>Inställningar för Windows-säkerhetsbaslinjer för Intune  

Visa [inställningarna för Windows-säkerhetsbaslinjer](security-baselines.md) som stöds av Microsoft Intune.  

> [!NOTE]  
> Inställningarna för Windows-säkerhetsbaslinjer finns i förhandsversionen. I förhandsversionen varierar listan över tillgängliga inställningar, och ordningen som används i det här innehållet för att presentera inställningarna, jämfört med det som är tillgängligt på portalen.  
>  
> När baslinjeinställningarna inte är i förhandsversion längre uppdateras det här innehållet med en ny lista över säkerhetsbaslinjeinställningar som stöds av Intune.  

## <a name="above-lock"></a>På låsskärmen  
Mer information finns i [CSP-princip – AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) i Windows-dokumentationen.  

- **Block display of toast notifications** (Blockera visning av popup-meddelanden)  
  Med den här principinställningen kan du förhindra att appmeddelanden visas på låsskärmen. Om du aktiverar den här principinställningen visas inga appmeddelanden på låsskärmen. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användarna välja vilka appar som ska visa aviseringar på låsskärmen.
  - **Standard**: Ja  

## <a name="app-runtime"></a>Appkörning    
Mer information finns i [CSP – AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) i Windows-dokumentationen.  

- **Microsoft accounts optional for Windows Store apps** (Microsoft-konton är valfria för Windows Store-appar)  
  Med den här principinställningen kan du ange om Microsoft-konton är valfria för Windows Store-appar som kräver ett konto för inloggning. Den här principen påverkar bara Windows Store-appar som stöder den. Om du aktiverar den här principinställningen tillåter Windows Store-appar som vanligtvis kräver ett Microsoft-konto för inloggning att användarna loggar in med ett företagskonto i stället. Om du inaktiverar eller inte konfigurerar den här principinställningen måste användarna logga in med ett Microsoft-konto.  
  - **Standard**: Aktiverad  

## <a name="application-management"></a>Programhantering   
Mer information finns i [CSP – ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) i Windows-dokumentationen.  

- **Block game DVR (desktop only)** (Blockera spel-DVR (endast skrivbord))  
  Konfigurerar om registrering och sändning av spel tillåts.
  - **Standard**: Ja  

## <a name="auto-play"></a>Spela upp automatiskt   
Mer information finns i [CSP-princip – Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay
) i Windows-dokumentationen.  

- **Auto play default auto run behavior** (Spela upp automatiskt – standardbeteende för autorun)  
  Den här inställningen påverkar standardbeteendet för Autorun-kommandon. Autorun-kommandon lagras i autorun.inf-filer och kan starta installationsprogram eller andra rutiner. När den här inställningen är *aktiverad* kan administratörer ändra standardbeteendet för automatisk körning på en enhet som kör Windows Vista eller senare. Beteendet kan anges till: a) inaktivera autorun-kommandon helt och hållet eller b) återgå till beteendet i äldre operativsystem än Windows Vista och kör autorun-kommandot automatiskt. När den här inställningen är *inaktiverad* eller om den *inte har konfigurerats* frågar enheter som kör Windows Vista eller senare användaren om ett autorun-kommando ska köras.
  - **Standard**: Kör inte  
  
- **Auto play mode** (Läge för automatisk uppspelning)  
  Med den här principinställningen kan du inaktivera funktionen Spela upp automatiskt. Funktionen Spela upp automatiskt börjar läsa från en enhet när du sätter in media i enheten. Därför startar installationsfiler för program och musik på ljudmedier direkt. Före Windows XP SP2 är funktionen Spela upp automatiskt inaktiverad som standard på flyttbara enheter, till exempel diskettenheten (men inte CD-ROM-enheten) och på nätverksenheter. Från och med Windows XP SP2 är funktionen Spela upp automatiskt aktiverad på flyttbara enheter, inklusive Zip-enheter och vissa USB-lagringsenheter. Om du aktiverar den här principinställningen inaktiveras Spela upp automatiskt på CD-ROM-enheter och flyttbara medieenheter, eller inaktiveras på alla enheter. Den här principinställningen inaktiverar Spela upp automatiskt på fler typer av enheter. Du kan inte använda den här inställningen för att aktivera Spela upp automatiskt på enheter där den är inaktiverad som standard. Om du inaktiverar eller inte konfigurerar den här principinställningen aktiveras Spela upp automatiskt. Obs! Den här inställningen visas både i mappen Datorkonfiguration och mappen Användarkonfiguration. Om principinställningarna står i konflikt med varandra har principinställningen i Datorkonfiguration företräde framför principinställningen i Användarkonfiguration.
  - **Standard**: Inaktiverad

- **Block auto play for non-volume devices** (Blockera automatisk uppspelning av andra enheter än volymenheter)  
  Den här principinställningen tillåter inte automatisk uppspelning av MTP-enheter som exempelvis kameror och telefoner. Om du aktiverar den här principinställningen tillåts inte automatisk uppspelning av MTP-enheter som exempelvis kameror och telefoner. Om du inaktiverar eller inte konfigurerar den här principinställningen aktiveras automatisk uppspelning av andra enheter än volymenheter.
  - **Standard**: Aktiverad  

## <a name="bitlocker"></a>BitLocker    
Mer information finns i [CSP-princip – Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) i Windows-dokumentationen.  

- **Bit locker removable drive policy** (Princip för BitLocker på flyttbara enheter)  
  Den här inställningen används för att styra krypteringsmetoden och krypteringsstyrkan. Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering. Företag kanske vill styra krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du aktiverar den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara enheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om enheten ska användas på andra enheter som inte kör Windows 10, version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen.

    - **Require encryption for write access** (Kräv kryptering för skrivåtkomst)
      - **Standard**: Ja  

    - **Krypteringsmetod**
      - **Standard**: AES 256-bitars CBC  

- **Bit locker fixed drive policy** (Princip för BitLocker på fasta enheter)  
  Den här inställningen används för att styra krypteringsmetoden och krypteringsstyrkan. Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering. Företag kanske vill styra krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du aktiverar den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara enheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om enheten ska användas på andra enheter som inte kör Windows 10, version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen.  
 
  - **Krypteringsmetod**
    - **Standard**: AES 256-bitars XTS  

- **Bit locker system drive policy** (Princip för BitLocker på systemenheter)  
  Den här inställningen används för att styra krypteringsmetoden och krypteringsstyrkan. Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering. Företag kanske vill styra krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du aktiverar den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara enheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om enheten ska användas på andra enheter som inte kör Windows 10, version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen.  

  - **Krypteringsmetod**  
    - **Standard**: AES 256-bitars XTS  

## <a name="browser"></a>Webbläsare  
Mer information finns i [CSP-princip – Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) i Windows-dokumentationen.  

- **Require SmartScreen for Microsoft Edge** (Kräv SmartScreen för Microsoft Edge)  
  Microsoft Edge använder som standard Windows Defender SmartScreen (aktiverat) för att skydda användarna mot potentiella nätfiskeförsök och skadlig programvara. Som standard kan användarna inte heller inaktivera (stänga av) Windows Defender SmartScreen. Om den här principen aktiveras inaktiveras Windows Defender SmartScreen och användarna kan inte aktivera funktionen. Konfigurera inte den här principen om du vill att användarna ska kunna aktivera och inaktivera Windows Defender SmartScreen.  
  - **Standard**: Ja  
  
- **Block malicious site access** (Blockera åtkomst till skadliga webbplatser)  
  Som standard tillåter Microsoft Edge att användarna kringgår (ignorerar) Windows Defender SmartScreen-varningar om potentiellt skadliga webbplatser, så att de kan fortsätta till webbplatsen. Med den här principen kan du dock konfigurera Microsoft Edge för att hindra användarna från att kringgå varningar, så att de inte kan fortsätta till webbplatsen.
  - **Standard**: Ja  
  
- **Block unverified file download** (Blockera nedladdning av overifierade filer)  </br>
  Som standard tillåter Microsoft Edge att användarna kringgår (ignorerar) Windows Defender SmartScreen-varningar om potentiellt skadliga filer, så att de kan fortsätta att ladda ned overifierade filer. Om den här principen aktiveras kan användarna inte kringgå varningarna och hindras från att ladda ned overifierade filer.
  - **Standard**: Ja  
  
- **Block Password Manager** (Blockera Lösenordshanteraren)  </br>
  Som standard använder Microsoft Edge Lösenordshanteraren automatiskt, så att användarna kan hantera lösenord lokalt. Om den här principen inaktiveras kan Microsoft Edge inte använda Lösenordshanteraren. Konfigurera inte den här principen om du vill att användarna ska kunna spara och hantera lösenord lokalt med hjälp av Lösenordshanteraren.
  - **Standard**: Ja  
  
- **Prevent certificate error overrides** (Förhindra åsidosättning av certifikatfel)  </br>
  Den här principinställningen hindrar användaren från att ignorera SSL/TLS-certifikatfel (Secure Sockets Layer/Transport Layer Security) som avbryter surfningen (t.ex. fel av typen ”har upphört att gälla”, ”har återkallats” eller ”namnkonflikt”) i Internet Explorer. Användaren kan inte fortsätta att surfa om du aktiverar den här principinställningen. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren välja att ignorera certifikatfel och fortsätta att surfa.
  - **Standard**: Ja  

## <a name="connectivity"></a>Anslutning  
Mer information finns i avsnittet [CSP-princip – Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) i Windows-dokumentationen.  

- **Block Internet download for web publishing and online ordering wizards** (Blockera nedladdning från Internet för webbpublicerings- och onlinebeställningsguider)  
  Den här principinställningen anger om Windows ska ladda ned en lista över leverantörer för webbpublicerings- och onlinebeställningsguider. Dessa guider låter användarna välja från en lista över företag som tillhandahåller tjänster, till exempel onlinelagring eller fotoutskrifter. Som standard visar Windows leverantörer som hämtats från en Windows-webbplats och leverantörer som angetts i registret. Om du aktiverar den här principinställningen hämtar inte Windows leverantörer och endast de tjänstleverantörer som har cachelagrats i det lokala registret visas. Om du inaktiverar eller inte konfigurerar den här principinställningen hämtas en lista över leverantörer när användaren använder webbpublicerings- eller onlinebeställningsguider. Mer information, inklusive information om hur du anger leverantörer i registret, finns i dokumentationen för webbpublicerings- och onlinebeställningsguiderna.  
  - **Standard**: Aktiverad  

- **Block downloading of print drivers over HTTP** (Blockera nedladdning av utskriftsdrivrutiner via HTTP)  
  Den här principinställningen anger om klienten kan ladda ned paket med utskriftsdrivrutiner via HTTP. För att konfigurera HTTP-utskrift måste ”non-inbox”-drivrutiner hämtas via HTTP. Obs! Den här principinställningen hindrar inte klienten från att skriva ut till skrivare i intranätet eller på Internet via HTTP. Den förbjuder bara nedladdningen av drivrutiner som inte redan har installerats lokalt. Om du aktiverar den här principinställningen går det inte att ladda ned utskriftsdrivrutiner via HTTP. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användarna ladda ned utskriftsdrivrutiner via HTTP.
  - **Standard**: Aktiverad  

## <a name="credentials-delegation"></a>Delegering av autentiseringsuppgifter  
Mer information finns i [CSP-princip – CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) i Windows-dokumentationen.  

- **Remote host delegation of non-exportable credentials** (Delegering via fjärrvärd av icke exporterbara autentiseringsuppgifter)  
  Fjärrvärden tillåter delegering av autentiseringsuppgifter som inte kan exporteras. När du använder delegering av autentiseringsuppgifter tillhandahåller enheterna en exporterbar version av autentiseringsuppgifterna till fjärrvärden. Detta medför en risk för stöld av autentiseringsuppgifterna från en angripare på fjärrvärden. Om du aktiverar den här principinställningen kan värden använda läget Restricted Admin (Begränsad administration) eller Remote Credential Guard (Fjärrskydd av autentiseringsuppgifter). Om du inaktiverar eller inte konfigurerar den här principinställningen stöds inte läget Restricted Admin (Begränsad administration) eller Remote Credential Guard (Fjärrskydd av autentiseringsuppgifter). Användaren måste alltid skicka sina autentiseringsuppgifter till värden.  

  - **Standard**: Aktiverad  

## <a name="credentials-ui"></a>Användargränssnitt för autentiseringsuppgifter  
Mer information finns i [CSP-princip – CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) i Windows-dokumentationen.  

- **Enumerate administrators**   (Räkna upp administratörer)  
  Den här principinställningen styr om administratörskonton visas när en användare försöker upphöja ett program som körs. Som standard visas inte administratörskonton när användaren försöker upphöja ett program som körs. Om du aktiverar den här principinställningen visas alla lokala administratörskonton på datorn så att användaren kan välja ett och ange rätt lösenord. Om du inaktiverar den här principinställningen måste användaren alltid ange ett användarnamn och lösenord för att upphöja ett program som körs.  

  - **Standard**: Inaktiverad  

## <a name="data-protection"></a>Dataskydd  
Mer information finns i [CSP-princip – DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) i Windows-dokumentationen.  

- **Block direct memory access**  (Blockera direkt minnesåtkomst)  
  Med den här principinställningen kan du blockera direkt minnesåtkomst (DMA) för alla underordnade PCI-portar med hot plug-stöd tills en användare loggar in i Windows. När en användare loggar in räknar Windows upp PCI-enheterna som är anslutna till PCI-portarna med hot plug-stöd. Varje gång användaren låser datorn blockeras DMA på PCI-portarna med hot plug-stöd utan underordnade enheter tills användaren loggar in igen. Enheter som räknades upp när datorn var upplåst fortsätter att fungera tills de kopplas från. Den här principinställningen tillämpas endast när BitLocker- eller enhetskryptering är aktiverat.
  
  - **Standard**: Ja  

## <a name="device-guard"></a>Device Guard  
Mer information finns i [CSP-princip – DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) i Windows-dokumentationen.  

- **Credential Guard**  
  Den här principinställningen tillåter att användarna aktiverar Credential Guard (Autentiseringsskydd) med virtualiseringsbaserad säkerhet för att skydda autentiseringsuppgifterna vid nästa omstart.
  
  - **Standard**: Aktivera med UEFI-lås 

- **Enable virtualization based security** (Aktivera virtualiseringsbaserad säkerhet)  </br>
  Aktiverar virtualiseringsbaserad säkerhet (VBS) vid nästa omstart. Virtualiseringsbaserad säkerhet använder Windows Hypervisor för att ge stöd för säkerhetstjänster.
  - **Standard**: Ja  

<!-- not yet available 
- **Enable secure boot with DMA**  
  Among the commands that follow, you can choose settings for Secure Boot and Secure Boot with DMA. In most situations, we recommend that you choose Secure Boot. This option provides Secure Boot with as much protection as is supported by a given computer’s hardware. A computer with input/output memory management units (IOMMUs) will have Secure Boot with DMA protection. A computer without IOMMUs will simply have Secure Boot enabled. In contrast, with Secure Boot with DMA, the setting will enable Secure Boot—and VBS itself—only on a computer that supports DMA, that is, a computer with IOMMUs. With this setting, any computer without IOMMUs will not have VBS or HVCI protection, although it can still have WDAC enabled.
  
  - **Default**: Yes  
  -->
- **Launch system guard** (Starta systemskydd)  
  - **Standard**: Aktiverad  

## <a name="device-installation"></a>Enhetsinstallation  
Mer information finns i [CSP-princip – DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) i Windows-dokumentationen.  

- **Hardware device installation by device identifiers** (Installation av maskinvaruenheter efter enhets-ID)  
  Med den här principinställningen kan du ange en lista med ID:n för Plug and Play-maskinvara och kompatibla ID:n för enheter som Windows hindrar från att installeras. Den här inställningen har företräde framför alla andra principinställningar som tillåter att Windows installerar en enhet. Om du aktiverar den här principinställningen hindras Windows från att installera en enhet vars maskinvaru-ID eller kompatibla ID visas i listan som du skapar. Om du aktiverar den här principinställningen på en fjärrskrivbordsserver påverkar principinställningen omdirigeringen av de angivna enheterna från en fjärrskrivbordsklient till fjärrskrivbordsservern. Om du inaktiverar eller inte konfigurerar den här principinställningen kan enheter installeras och uppdateras beroende på vad som tillåts eller förhindras av andra principinställningar.
  - **Standard**: Blockera installation av maskinvaruenheter  
  
    - **Remove matching hardware devices** (Ta bort matchande maskinvaruenheter)  
      Den här inställningen är endast tillgänglig när *Hardware device installation by device identifiers* (Installation av maskinvaruenheter efter enhets-ID) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).
      - **Standard**: Ja
  
    - **Hardware device identifiers that are blocked** (ID:n för blockerade maskinvaruenheter)  </br>
      Den här inställningen är endast tillgänglig när *Hardware device installation by device identifiers* (Installation av maskinvaruenheter efter enhets-ID) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).
      - **Standard**: Ja  
  
- **Hardware device installation by setup classes** (Installation av maskinvaruenheter efter installationsklass)  
  Med den här principinställningen kan du ange en lista med klass-GUID för enhetsinstallation för enhetsdrivrutiner som Windows hindrar från att installeras. Den här inställningen har företräde framför alla andra principinställningar som tillåter att Windows installerar en enhet. Om du aktiverar den här principinställningen kan inte Windows installera eller uppdatera enhetsdrivrutiner vars klass-GUID för enhetsinstallation visas i listan du skapar. Om du aktiverar den här principinställningen på en fjärrskrivbordsserver påverkar principinställningen omdirigeringen av de angivna enheterna från en fjärrskrivbordsklient till fjärrskrivbordsservern. Om du inaktiverar eller inte konfigurerar den här principinställningen kan Windows installera och uppdatera enheter beroende på om de tillåts eller förhindras av andra principinställningar.
  - **Standard**: Blockera installation av maskinvaruenheter  
  
    - **Remove matching hardware devices** (Ta bort matchande maskinvaruenheter)  </br>
      Den här inställningen är endast tillgänglig när *Hardware device installation by setup classes* (Installation av maskinvaruenheter efter installationsklasser) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).
      - **Standard**: *Ingen standardkonfiguration*  
  
    - **Hardware device identifiers that are blocked** (ID:n för blockerade maskinvaruenheter)  </br>
      Den här inställningen är endast tillgänglig när *Hardware device installation by setup classes* (Installation av maskinvaruenheter efter installationsklasser) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).
      - **Standard**: *Ingen standardkonfiguration*  

## <a name="device-lock"></a>Enhetslås  
Mer information finns i [CSP-princip – DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) i Windows-dokumentationen.  

- **Prevent use of camera** (Förhindra användning av kamera)  
  Inaktiverar kameraväxlingsreglaget på låsskärmen i Datorinställningar och förhindrar att en kamera anropas på låsskärmen. Som standard kan användare aktivera anrop av en tillgänglig kameran på låsskärmen. Om du aktiverar den här inställningen kan användarna inte längre aktivera eller inaktivera kameraåtkomst på låsskärmen i Datorinställningar och kameran kan inte anropas på låsskärmen.  
  - **Standard**: Aktiverad  

- **Kräv lösenord**  
  Anger om enhetslås har aktiverats.
  - **Standard**: Ja  
  
  - **Password minimum character set count** (Minsta antal tecken för lösenord)  
    Antalet komplexa elementtyper (versaler och gemener, siffror och skiljetecken) som krävs för en stark PIN-kod eller ett starkt lösenord. För PIN-kod krävs följande för stationära och mobila enheter: 1 – Endast siffror 2 – Siffror och gemener krävs 3 – Siffror, gemener och versaler krävs. Stöds inte med Microsoft-konton för stationära datorer eller domänkonton. 4 – Siffror, gemener, versaler och specialtecken krävs. Stöds inte med stationära datorer. Standardvärdet är 1. 
    - **Standard**: 3  
  
  - **Antal felaktiga inloggningar innan enheten rensas**  
    Antal misslyckade autentiseringsförsök som tillåts innan enheten rensas. Värdet 0 inaktiverar enhetsrensningsfunktionen.
    - **Standard**: 10  
  
  - **Lösenordets giltighetstid (i dagar)**  
    Principinställningen Högsta ålder för lösenord anger tidsperioden (i dagar) som ett lösenord kan användas innan systemet kräver att användaren ändrar det. Du kan ange att lösenord upphör att gälla efter ett visst antal dagar mellan 1 och 999, eller ange att lösenorden aldrig upphör att gälla genom att ange antalet dagar till 0. Om den högsta lösenordsåldern är mellan 1 och 999 dagar, måste den minsta lösenordsåldern vara mindre än den högsta lösenordsåldern. Om den högsta lösenordsåldern anges till 0, kan den minsta lösenordsåldern vara ett värde mellan 0 och 998 dagar.
    - **Standard**: 60  
  
  - **Lösenordstyp krävs**  
    Avgör vilken typ av PIN-kod eller lösenord som krävs.
    - **Standard**: Alfanumerisk  
  
  - **Minsta längd på lösenord**  
    Inställningen Minsta längd för lösenord avgör det minsta antal tecken som ett lösenord för ett användarkonto måste innehålla. Du kan ange ett värde mellan 1 och 14 tecken, eller ange att inga lösenord krävs genom att ange antalet tecken till 0.
    - **Standard**: 8  
  
  - **Blockera enkla lösenord**  
    Anger om PIN-koder eller lösenord, till exempel ”1111” eller ”1234” tillåts. För en stationär dator styr inställningen även användningen av bildlösenord.
    - **Standard**: Ja  
       *Inställningen Ja förhindrar användningen av enkla lösenord.* 

  - **Förhindra återanvändning av tidigare lösenord**  
    Anger hur många lösenord som kan sparas i historiken och som inte får återanvändas. Värdet inkluderar användarens aktuella lösenord. Med inställningen 1 kan användaren inte återanvända det aktuella lösenordet när han eller hon väljer ett nytt lösenord, och med inställningen *5* kan användaren inte använda det aktuella lösenordet eller något av de fyra senaste lösenorden som det nya lösenordet.
    - **Standard**: 24  

- **Prevent slide show** (Förhindra bildspel)  
  Inaktiverar inställningarna för bildspel på låsskärmen i Datorinställningar och förhindrar att ett bildspel spelas upp på låsskärmen. Som standard kan användare aktivera ett bildspel som körs när de låst datorn. Om du aktiverar den här inställningen kan användarna inte längre ändra inställningarna för bildspel i Datorinställningar och inga bildspel startar.
  - **Standard**: Aktiverad  
    *Inställningen Aktiverad förhindrar att bildspel körs.* 

- **Password minimum age in days** (Minsta ålder för lösenord i dagar)  
  Inställningen för minsta lösenordsålder anger hur länge (i antal dagar) ett lösenord måste användas innan användaren kan ändra det. Du kan ange ett värde mellan 1 och 998 dagar, eller tillåta lösenordsändringar direkt genom att ange antalet dagar till 0. Den minsta lösenordsåldern måste vara mindre än den högsta lösenordsåldern, såvida inte den högsta lösenordsåldern har angetts till 0, vilket anger att lösenord aldrig upphör att gälla. Om den högsta lösenordsåldern har angetts till 0, kan den lägsta lösenordsåldern anges till valfritt värde mellan 0 och 998.
  - **Standard**: 1  

## <a name="event-log-service"></a>Händelseloggtjänsten  
Mer information finns i [CSP-princip – EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) i Windows-dokumentationen.  

- **Security log maximum file size in KB** (Största filstorlek i kB för säkerhetslogg)  
  Den här principinställningen anger den högsta storleken för loggfilen i kilobyte. Om du aktiverar den här principinställningen kan du konfigurera den största storleken för loggfilen till mellan 1 megabyte (1 024 kB) och 2 terabyte (2 147 483 647 kilobyte) i steg om en kilobyte. Om du inaktiverar eller inte konfigurerar den här principinställningen används det lokalt konfigurerade värdet som den största storleken för loggfilen. Det här värdet kan ändras av den lokala administratören med hjälp av dialogrutan Egenskaper för logg och har som standard värdet 20 MB.
  - **Standard**: 196608  

- **System log maximum file size in KB** (Största filstorlek i kB för systemlogg)  
  Den här principinställningen anger den högsta storleken för loggfilen i kilobyte. Om du aktiverar den här principinställningen kan du konfigurera den största storleken för loggfilen till mellan 1 megabyte (1 024 kB) och 2 terabyte (2 147 483 647 kilobyte) i steg om en kilobyte. Om du inaktiverar eller inte konfigurerar den här principinställningen används det lokalt konfigurerade värdet som den största storleken för loggfilen. Det här värdet kan ändras av den lokala administratören med hjälp av dialogrutan Egenskaper för logg och har som standard värdet 20 MB.
  - **Standard**: 32768  

- **Application log maximum file size in KB** (Största filstorlek i kB för programlogg)  
  Den här principinställningen anger den högsta storleken för loggfilen i kilobyte. Om du aktiverar den här principinställningen kan du konfigurera den största storleken för loggfilen till mellan 1 megabyte (1 024 kB) och 2 terabyte (2 147 483 647 kilobyte) i steg om en kilobyte. Om du inaktiverar eller inte konfigurerar den här principinställningen används det lokalt konfigurerade värdet som den största storleken för loggfilen. Det här värdet kan ändras av den lokala administratören med hjälp av dialogrutan Egenskaper för logg och har som standard värdet 20 MB.
  - **Standard**: 32768  

## <a name="experience"></a>Erfarenhet  
Mer information finns i [CSP-princip – Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) i Windows-dokumentationen.  

- **Blockera Windows Spotlight**  
  Tillåter IT-administratörer att inaktivera alla Windows Spotlight-funktioner – Windows Spotlight på låsskärmen, Windows-tips, Microsoft-konsumentfunktioner och liknande funktioner.
  - **Standard**: Ja  
  
  - **Block third-party suggestions in Windows Spotlight** (Blockera tredjepartsförslag i Windows Spotlight)  
    Anger om app- och innehållsförslag från utgivare av tredjepartsprogramvara ska tillåtas i Windows Spotlight-funktioner, till exempel låsskärmen, föreslagna appar på Start-menyn och Windows-tips. Användare kan fortfarande se förslag för Microsoft-funktioner, -appar och -tjänster.
     - **Standard**: Ja  
  - **Block consumer specific features** (Blockera konsumentspecifika funktioner)  
    Gör det möjligt för IT-administratörer att aktivera rena konsumentupplevelser, till exempel startförslag, medlemskapsaviseringar, appinstallation efter välkomstprogram (OOBE) och omdirigeringspaneler.
    - **Standard**: Ja  


## <a name="exploit-guard"></a>Sårbarhetsskydd  
Mer information finns i [CSP-princip – ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) i Windows-dokumentationen.  

- **Exploit protection XML** (XML för sårbarhetsskydd)  
  Gör det möjligt för IT-administratören att distribuera en konfiguration som representerar önskade system- och programskyddsalternativ till alla enheter i organisationen. Konfigurationen representeras av en XML-sträng. Sårbarhetsskydd hjälper dig att skydda enheter mot skadlig kod som utnyttjar kryphål för att spridas och infektera. Du kan använda Windows Security-appen eller PowerShell för att skapa en uppsättning skyddsåtgärder (kallas en konfiguration). Du kan exportera den här konfigurationen som en XML-fil och dela den med flera datorer i nätverket så att alla har samma uppsättning skyddsåtgärder. Du kan också konvertera och importera en befintlig EMET XML-konfigurationsfil till en XML-konfigurationsfil för sårbarhetsskydd.
  - **Standard**: *En XML-exempelfil finns tillgänglig* 
 
## <a name="file-explorer"></a>Utforskaren  
Mer information finns i [CSP-princip – FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) i Windows-dokumentationen.  

- **Block data execution prevention** (Blockera dataexekveringsskydd)  
  Om dataexekveringsskydd inaktiveras kan vissa äldre plugin-program fungera utan att Explorer avslutas.
  - **Standard**: Inaktiverad  
   
- **Block heap termination on corruption** (Blockera heap-avslutning vid fel)  
  Om heap-avslutning vid fel inaktiveras kan vissa äldre plugin-program fungera utan att Explorer omedelbart avslutas, även om Explorer fortfarande kan avslutas oväntat senare.
  - **Standard**: Inaktiverad  
    

## <a name="internet-explorer"></a>Internet Explorer  
Mer information finns i [CSP-princip – InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) i Windows-dokumentationen.  
<!-- not yet available 
- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  - **Default**: Disabled  
  
- **Office apps launch child process type**  
  Office apps will not be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  - **Default**: Disable  
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  - **Default**: Disable  
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  - **Default**: Disabled  
 -->
- **Internet Explorer internet zone access to data sources** (Internet Explorer: åtkomst till data i zonen Internet)  
  Med den här inställningen kan du ange om Internet Explorer kan komma åt data från en annan säkerhetszon med hjälp av Microsoft XML Parser (MSXML) eller ActiveX Data Objects (ADO). Om du aktiverar den här principinställningen kan användarna läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta inläsningen av en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du inaktiverar den här principinställningen kan användarna inte läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du inte konfigurerar den här principinställningen kan användarna inte läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen.
  - **Standard**: Inaktivera  
  
- **Internet Explorer restricted zone drag content from different domains within windows** (Internet Explorer: dra innehåll från olika domäner inuti fönster i zonen Begränsad)  
  Med den här principinställningen kan du ange alternativ för att dra innehåll från en domän till en annan domän när källan och målet finns i samma fönster. Om du aktiverar den här principinställningen och klickar på Aktivera kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i samma fönster. Användarna kan inte ändra den här inställningen. Om du aktiverar den här principinställningen och klickar på Inaktivera kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i samma fönster. Användarna kan inte ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 10 kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i samma fönster. Användarna kan ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 9 och tidigare versioner kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen i dialogrutan Internetalternativ.
  - **Standard**: Inaktiverad
  
- **Internet Explorer certificate address mismatch warning** (Internet Explorer: varning om adressmatchningsfel för certifikat)  
  Med den här principinställningen kan du aktivera säkerhetsvarningen för adressmatchningsfel för certifikat. När den här inställningen är aktiverad varnas användarna när de besöker webbplatser med säker HTTP (HTTPS) som visar certifikat som utfärdats för en annan webbadress. Den här varningen hjälper till att förhindra förfalskningsattacker. Om du aktiverar den här principinställningen visas alltid varningen om adressmatchningsfel för certifikat. Om du inaktiverar eller inte konfigurerar den här inställningen kan användarna välja om varningen om adressmatchningsfel för certifikat ska visas (visa sidan Avancerat i Internet på Kontrollpanelen).
  - **Standard**: Aktiverad 
  
- **Internet Explorer restricted zone less privileged sites** (Internet Explorer: mindre privilegierade platser i zonen Begränsad)  
  Med den här principinställningen kan du ange om webbplatser i mindre privilegierade zoner, till exempel webbplatser på Internet, kan navigera till den här zonen. Om du aktiverar den här principinställningen kan webbplatser från mindre privilegierade zoner öppna nya fönster i, eller navigera till, den här zonen. Säkerhetszonen körs utan det ytterligare säkerhetslager som tillhandahålls av säkerhetsfunktionen Skydd mot zonförhöjning. Om du väljer Fråga i listrutan visas en varning för användarna om att potentiellt riskabel navigering snart initieras. Om du inaktiverar den här principinställningen förhindras den potentiellt skadliga navigeringen. Säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på inställningen för funktionen Skydd mot zonförhöjning. Om du inte konfigurerar den här principinställningen förhindras potentiellt skadlig navigering. Säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på inställningen för funktionen Skydd mot zonförhöjning.
  - **Standard**: Inaktivera  
  
- **Internet Explorer restricted zone automatic prompt for file downloads** (Internet Explorer: automatisk fråga om filnedladdning i zonen Begränsad)  </br>
  Den här principinställningen anger om användarna tillfrågas innan en filnedladdning som inte har initierats av användaren inleds. Oavsett den här inställningen visas dialogrutor för filnedladdning vid användarinitierade nedladdningar. Om du aktiverar den här inställningen visas en dialogruta för filnedladdning vid automatiska nedladdningsförsök. Om du inaktiverar eller inte konfigurerar den här inställningen blockeras filnedladdningar som inte har initierats av användaren, och användaren ser meddelandefältet i stället för dialogrutan för filnedladdning. Användare kan sedan klicka på meddelandefältet för att tillåta filhämtningen.
  - **Standard**: Inaktiverad
  
- **Internet Explorer internet zone .NET Framework reliant components** (Internet Explorer: .NET Framework-beroende komponenter i zonen Internet)  
  Med den här inställningen kan du bestämma om .NET Framework-komponenter som inte har signerats med Authenticode kan köras från Internet Explorer. Dessa komponenter är hanterade kontroller som en objekttagg refererar till och hanterade körbara filer som en länk refererar till. Om du aktiverar den här principinställningen kör Internet Explorer osignerade hanterade komponenter. Om du väljer Fråga i listrutan uppmanas användarna att välja om de vill köra osignerade hanterade komponenter i Internet Explorer. Om du inaktiverar den här principinställningen kör Internet Explorer inte osignerade hanterade komponenter. Om du inte konfigurerar den här principinställningen kör Internet Explorer osignerade hanterade komponenter.
  - **Standard**: Inaktivera 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls** (Internet Explorer: tillåt endast att godkända domäner använder TDC ActiveX-kontroller i zonen Internet)  </br>
  Den här principinställningen styr huruvida användaren kan köra TDC ActiveX-kontrollen på webbplatser. Om du aktiverar den här principinställningen körs inte TDC ActiveX-kontrollen från webbplatser i den här zonen. Om du inaktiverar den här principinställningen körs TDC ActiveX-kontrollen från alla platser i den här zonen.
  - **Standard**: Aktiverad 
  
- **Internet Explorer restricted zone script initiated windows** (Internet Explorer: skriptinitierade fönster i zonen Begränsad)  
  Med den här principinställningen kan du hantera begränsningar för skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet. Om du aktiverar den här principinställningen gäller inte begränsningar för Windows-säkerhet i den här zonen. Säkerhetszonen körs utan det ytterligare säkerhetslager som tillhandahålls av den här funktionen. Om du inaktiverar den här principinställningen kan inte de potentiellt skadliga åtgärderna i skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet köras. Den här säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på kontrollinställningen för skriptinitierade säkerhetsbegränsningar för Windows. Om du inte konfigurerar den här principinställningen kan inte de potentiellt skadliga åtgärderna i skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet köras. Den här säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på kontrollinställningen för skriptinitierade säkerhetsbegränsningar för Windows.
  - **Standard**: Inaktiverad 
  
- **Internet Explorer internet zone include local path when uploading files to server** (Internet Explorer: ta med lokal sökväg när filer laddas upp till servern i zonen Internet)  </br>
  Den här principinställningen styr huruvida information om den lokala sökvägen skickas eller inte när användaren laddar upp en fil via ett HTML-formulär. Om information om den lokala sökvägen skickas kan servern oavsiktligt få tillgång till viss information. Filer som skickas från användarens dator kan exempelvis innehålla användarnamnet som en del av sökvägen. Om du aktiverar den här principinställningen skickas information om sökvägen när användaren överför en fil via ett HTML-formulär. Om du inaktiverar den här principinställningen tas information om sökvägen bort när användaren överför en fil via ett HTML-formulär. Om du inte konfigurerar den här principinställningen kan användarna välja om sökvägsinformation ska skickas när de laddar upp en fil via ett HTML-formulär. Sökvägsinformation skickas som standard.
  - **Standard**: Inaktiverad 
  
- **Internet Explorer disable processes in enhanced protected mode** (Internet Explorer: inaktivera processer i utökat skyddat läge)  
  Den här principinställningen anger om Internet Explorer 11 använder 64-bitarsprocesser (för högre säkerhet) eller 32-bitarsprocesser (för bättre kompatibilitet) när programmet körs i utökat skyddat läge i 64-bitarsversioner av Windows. Viktigt: Vissa ActiveX-kontroller och -verktygsfält kanske inte är tillgängliga när 64-bitarsprocesser används. Om du aktiverar den här principinställningen använder Internet Explorer 11 64-bitarsprocesser i utökat skyddat läge i 64-bitarsversioner av Windows. Om du inaktiverar den här principinställningen använder Internet Explorer 11 32-bitarsprocesser i utökat skyddat läge i 64-bitarsversioner av Windows. Om du inte konfigurerar den här principinställningen kan användarna aktivera eller inaktivera den här funktionen via Internet Explorer-inställningarna. Den här funktionen är inaktiverad som standard.
  - **Standard**: Aktiverad 
  
- **Internet Explorer ignore certificate errors** (Internet Explorer: ignorera certifikatfel)  </br>
  Den här principinställningen hindrar användaren från att ignorera SSL/TLS-certifikatfel (Secure Sockets Layer/Transport Layer Security) som avbryter surfningen (t.ex. fel av typen ”har upphört att gälla”, ”har återkallats” eller ”namnkonflikt”) i Internet Explorer. Användaren kan inte fortsätta att surfa om du aktiverar den här principinställningen. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren välja att ignorera certifikatfel och fortsätta att surfa.
  - **Standard**: Inaktiverad 
  
- **Internet Explorer internet zone loading of XAML files** (Internet Explorer: inläsning av XAML-filer i zonen Internet)  
  Med den här principinställningen kan du hantera inläsningen av XAML-filer (Extensible Application Markup Language). XAML är ett XML-baserat deklarativt märkspråk som ofta används för att skapa mångsidiga användargränssnitt och grafik som utnyttjar Windows Presentation Foundation. Om du aktiverar den här inställningen och väljer Aktivera i listrutan läses XAML-filer in automatiskt i Internet Explorer. Användaren kan inte ändra det här beteendet. Om du väljer Fråga i listrutan tillfrågas användaren innan XAML-filerna läses in. Om du inaktiverar den här principinställningen läses XAML-filer inte in i Internet Explorer. Användaren kan inte ändra det här beteendet. Om du inte konfigurerar den här principinställningen kan användaren bestämma om XAML-filerna ska läsas in i Internet Explorer.
  - **Standard**: Inaktivera 
  
- **Internet Explorer internet zone automatic prompt for file downloads** (Internet Explorer: automatisk fråga om filnedladdning i zonen Internet)  </br>
  Den här principinställningen anger om användarna tillfrågas innan en filnedladdning som inte har initierats av användaren inleds. Oavsett den här inställningen visas dialogrutor för filnedladdning vid användarinitierade nedladdningar. Om du aktiverar den här inställningen visas en dialogruta för filnedladdning vid automatiska nedladdningsförsök. Om du inaktiverar eller inte konfigurerar den här inställningen blockeras filnedladdningar som inte har initierats av användaren, och användaren ser meddelandefältet i stället för dialogrutan för filnedladdning. Användare kan sedan klicka på meddelandefältet för att tillåta filhämtningen.
  - **Standard**: Aktiverad  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files** (Internet Explorer: säkerhetsvarning om potentiellt skadliga filer i zonen Begränsad)  
  Den här principinställningen styr huruvida meddelandet ”Öppna fil – säkerhetsvarning” visas när användaren försöker öppna körbara filer eller andra potentiellt skadliga filer (till exempel från en filresurs i intranätet med hjälp av Utforskaren). Om du aktiverar den här principinställningen och väljer Aktivera i listrutan öppnas dessa filer utan någon säkerhetsvarning. Om du väljer Fråga i listrutan visas en säkerhetsvarning innan filerna öppnas. Om du inaktiverar den här principinställningen öppnas inte dessa filer. Om du inte konfigurerar den här principinställningen kan användaren konfigurera hur datorn hanterar dessa. Som standard blockeras dessa filer i zonen Begränsad, tillåts i zonerna Intranät och Lokal dator och har inställningen Fråga i zonerna Internet och Betrodda platser.
  - **Standard**: Inaktivera  
  
- **Internet Explorer internet zone cross site scripting filter** (Internet Explorer: XSS-filter i zonen Internet)  
  Den här principen styr huruvida XSS-filtret (Cross Site-Scripting) identifierar och förhindrar XSS-inmatningar till webbplatser i den här zonen. Om du aktiverar den här principinställningen aktiveras XSS-filtret för platser i den här zonen och XSS-filtret försöker blockera XSS-inmatningar. Om du inaktiverar den här principinställningen inaktiveras XSS-filtret för platser i den här zonen och Internet Explorer tillåter XSS-inmatningar.
  - **Standard**: Aktiverad 
  
- **Internet Explorer fallback to SSL3** (Internet Explorer-återställning till SSL3)  
  Med den här principinställningen kan du blockera en osäker återställning till SSL 3.0. När den här principen är aktiverad försöker Internet Explorer ansluta till platser med hjälp av SSL 3.0 eller lägre om TLS 1.0 eller senare misslyckas. Vi rekommenderar att du inte tillåter osäker återställning för att förhindra en man-i-mitten-attack. Den här principen påverkar inte vilka säkerhetsprotokoll som aktiveras. Om du inaktiverar den här principen används standardvärdena.
  - **Standard**: Inga platser 
  
- **Internet Explorer locked down internet zone smart screen** (Internet Explorer: låst SmartScreen i zonen Internet)  
  Den här principinställningen styr huruvida SmartScreen-filtret söker igenom sidor i den här zonen och letar efter skadligt innehåll. Om du aktiverar den här principinställningen söker SmartScreen-filtret igenom sidor i den här zonen och letar efter skadligt innehåll. Om du inaktiverar den här principinställningen söker SmartScreen-filtret inte igenom sidor i den här zonen för att leta efter skadligt innehåll. Om du inte konfigurerar den här principinställningen kan användaren välja om SmartScreen-filtret ska söka igenom sidor i den här zonen och leta efter skadligt innehåll. Obs! I Internet Explorer 7 styr den här principinställningen om nätfiskefiltret söker igenom sidor i den här zonen och letar efter skadligt innehåll.
  - **Standard**: Aktiverad 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame** (Internet Explorer: starta program och filer i en iFrame i zonen Begränsad)  
  Med den här principinställningen kan du ange om program kan köras och om filer kan laddas ned från en IFRAME-referens i HTML-koden för sidorna i den här zonen. Om du aktiverar den här principinställningen kan användarna köra program och ladda ned filer från en IFRAME på sidorna i den här zonen utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill köra program och ladda ned filer från en IFRAME på sidorna i den här zonen. Om du inaktiverar den här principinställningen hindras användarna från att köra program och ladda ned filer från en IFRAME på sidorna i den här zonen. Om du inte konfigurerar den här principinställningen hindras användarna från att köra program och ladda ned filer från en IFRAME på sidorna i den här zonen.
  - **Standard**: Inaktivera 
  
- **Internet Explorer bypass smart screen warnings about uncommon files** (Internet Explorer: kringgå SmartScreen-varningar om ovanliga filer) Den här principinställningen avgör om användaren kan kringgå varningar från SmartScreen-filtret. SmartScreen-filtret varnar användaren om körbara filer som Internet Explorer-användare vanligtvis inte laddar ned från Internet. Om du aktiverar den här principinställningen blockerar SmartScreen-filtret användaren. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren kringgå varningar från SmartScreen-filtret.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer internet zone popup blocker** (Internet Explorer: blockera popup-fönster i zonen Internet)  
  Med den här principinställningen kan du ange om oönskade popup-fönster ska visas eller inte. Popup-fönster som öppnas när slutanvändaren klickar på en länk blockeras inte. Om du aktiverar den här principinställningen hindras de flesta oönskade popup-fönster från att visas. Om du inaktiverar den här principinställningen hindras inte popup-fönster från att visas. Om du inte konfigurerar den här principinställningen hindras de flesta oönskade popup-fönster från att visas.
  - **Standard**: Aktivera  
  
- **Internet Explorer processes consistent MIME handling** (Internet Explorer: konsekvent MIME-hantering av processer)  
  Internet Explorer innehåller dynamiska binära beteenden: komponenter som kapslar in specifika funktioner för HTML-elementen som de är kopplade till. Den här inställningen styr huruvida inställningen Säkerhetsbegränsning för uppföranden i binärkod ska tillåtas eller blockeras. Om du aktiverar den här principinställningen förhindras binära beteenden för processer relaterade till Utforskaren och Internet Explorer. Om du inaktiverar den här principinställningen tillåts binära beteenden för processer relaterade till Utforskaren och Internet Explorer. Om du inte konfigurerar den här principinställningen förhindras binära beteenden för processer relaterade till Utforskaren och Internet Explorer.
  - **Standard**: Aktiverad  
  
- **Internet Explorer restricted zone java permissions** (Internet Explorer: Java-behörigheter i zonen Begränsad) Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop), samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar.
  - **Standard**: Inaktivera Java  
    
  
- **Internet Explorer Active X controls in protected mode** (Internet Explorer: Active X-kontroller i skyddat läge)  
  Den här principinställningen förhindrar att ActiveX-kontroller körs i skyddat läge när utökat skyddat läge är aktiverat. När en användare har en ActiveX-kontroll installerad som inte är kompatibel med utökat skyddat läge och en webbplats försöker läsa in kontrollen, meddelar Internet Explorer användaren om detta och ger möjlighet att köra webbplatsen i det vanliga skyddade läget. Den här inställningen inaktiverar det här meddelandet och tvingar alla webbplatser att köras i utökat skyddat läge. Utökat skyddat läge ger ytterligare skydd mot skadliga webbplatser genom att använda 64-bitarsprocesser i 64-bitarsversioner av Windows. För datorer som kör minst Windows 8 begränsar utökat skyddat läge också vilka platser Internet Explorer kan läsa från i registret och filsystemet. När utökat skyddat läge är aktiverat och en användare påträffar en webbplats som försöker läsa in en ActiveX-kontroll som inte är kompatibel med utökat skyddat läge, meddelar Internet Explorer användaren och ger möjlighet att inaktivera utökat skyddat läge för den specifika webbplatsen. Om du aktiverar den här principinställningen ger Internet Explorer inte användaren möjlighet att inaktivera utökat skyddat läge. Alla webbplatser i skyddat läge körs i utökat skyddat läge. Om du inaktiverar eller inte konfigurerar den här principinställningen meddelar Internet Explorer användaren, som ges möjlighet att köra webbplatser med inkompatibla ActiveX-kontroller i det vanliga skyddade läget. Det här är standardbeteendet.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer restricted zone loading of XAML files** (Internet Explorer: inläsning av XAML-filer i zonen Begränsad)  
  Med den här principinställningen kan du hantera inläsningen av XAML-filer (Extensible Application Markup Language). XAML är ett XML-baserat deklarativt märkspråk som ofta används för att skapa mångsidiga användargränssnitt och grafik som utnyttjar Windows Presentation Foundation. Om du aktiverar den här inställningen och väljer Aktivera i listrutan läses XAML-filer in automatiskt i Internet Explorer. Användaren kan inte ändra det här beteendet. Om du väljer Fråga i listrutan tillfrågas användaren innan XAML-filerna läses in. Om du inaktiverar den här principinställningen läses XAML-filer inte in i Internet Explorer. Användaren kan inte ändra det här beteendet. Om du inte konfigurerar den här principinställningen kan användaren bestämma om XAML-filerna ska läsas in i Internet Explorer.
  - **Standard**: Inaktivera  
  
- **Internet Explorer processes scripted window security restrictions** (Internet Explorer: hantering av skriptbegränsningar för fönstersäkerhet)  
  Internet Explorer tillåter att skript öppnar, ändrar storlek på och flyttar olika typer av fönster via programmering. Säkerhetsfunktionen för fönsterbegränsningar begränsar popup-fönster och hindrar skript från att visa fönster där namnlisten och statusfältet inte visas för användaren eller som förvränger andra namnlister eller statusfält i Windows. Om du aktiverar den här principinställningen begränsas skriptbaserade fönster för alla processer. Om du inaktiverar eller inte konfigurerar den här principinställningen begränsas inte skriptbaserade fönster.
  - **Standard**: Aktiverad   
  
- **Internet Explorer restricted zone run Active X controls and plugins** (Internet Explorer: kör Active X-kontroller och plugin-program i zonen Begränsad)  
  Med den här principinställningen kan du ange om ActiveX-kontroller och plugin-program kan köras på sidor från den angivna zonen. Om du aktiverar den här principinställningen kan kontroller och plugin-program köras utan inblandning av användaren. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontroller eller plugin-programmet körs. Om du inaktiverar den här principinställningen hindras kontroller och plugin-program från att köras. Om du inte konfigurerar den här principinställningen hindras kontroller och plugin-program från att köras.
  - **Standard**: Inaktivera  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting** (Internet Explorer: Active X-kontroller markerade som säkra för skriptkörning i zonen Begränsad)  
  Med den här principinställningen kan du ange om en ActiveX-kontroll som markerats som säker för skriptkörning kan interagera med ett skript. Om du aktiverar den här principinställningen kan interaktion med skript ske automatiskt utan inblandning av användaren. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta interaktion med skript. Om du inaktiverar den här principinställningen förhindras interaktion med skript. Om du inte konfigurerar den här inställningen förhindras interaktion med skript.
  - **Standard**: Inaktivera  
  
- **Internet Explorer restricted zone logon options** (Internet Explorer: inloggningsalternativ i zonen Begränsad)  
  Med den här principinställningen kan du hantera inställningar för inloggningsalternativ. Om du aktiverar den här principinställningen kan du välja något av följande inloggningsalternativ. Anonym inloggning om du vill inaktivera HTTP-autentisering och gästkontot endast för CIFS-protokollet (Common Internet File System). Fråga efter användarnamn och lösenord om du vill uppmana användare att ange användar-ID:n och lösenord. När en användare har angett värdena kan de användas tyst i bakgrunden under resten av sessionen. Automatisk inloggning endast i zonen Intranät om du vill uppmana användaren att ange användar-ID:n och lösenord i andra zoner. När en användare har angett värdena kan de användas tyst i bakgrunden under resten av sessionen. Automatisk inloggning med aktuellt användarnamn och lösenord för att försöka logga in med Windows NT Challenge Response (även kallat NTLM-autentisering). Om Windows NT Challenge Response stöds av servern används användarens användarnamn och lösenord för nätverket vid inloggningen. Om Windows NT Challenge Response inte stöds av servern uppmanas användaren att ange användarnamnet och lösenordet. Om du inaktiverar den här principinställningen anges inloggningen endast till Automatisk inloggning i zonen Intranät. Om du inte konfigurerar den här principen uppmanas användaren att ange användarnamn och lösenord för att logga in.
  - **Standard**: Anonym  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe** (Internet Explorer: initiera och kör skript för Active X-kontroller som inte markerats som säkra i zonen Betrodda platser)  
  Med den här principinställningen kan du hantera ActiveX-kontroller som inte har markerats som säkra. Om du aktiverar den här principinställningen körs ActiveX-kontroller, initieras med parametrar och körs med skript utan att objektsäkerhet anges för obetrodda data eller skript. Den här inställningen rekommenderas inte, förutom för säkra och administrerade zoner. Den här inställningen gör att både osäkra och säkra kontroller initieras och körs med skript, samtidigt som ActiveX-skriptkontrollerna som markerats som säkra i skriptalternativet ignoreras. Om du aktiverar den här principinställningen och väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontrollen initieras med parametrar eller körs med skript. Om du inaktiverar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar och körs inte med skript. Om du inte konfigurerar den här principen tillfrågas användarna om de vill tillåta att kontrollen startas med parametrar eller körs med skript.
  - **Standard**: Inaktivera  
  
- **Internet Explorer check server certificate revocation** (Internet Explorer: kontrollera återkallelsestatus för servercertifikat)  
  Med den här principinställningen kan du ange om Internet Explorer ska kontrollera återkallelsestatusen för servercertifikat. Certifikat återkallas när de har komprometterats eller inte längre är giltiga och det här alternativet hindrar användarna från att skicka känsliga data till en webbplats som kan vara bedräglig eller inte säker. Om du aktiverar den här principinställningen kontrollerar Internet Explorer om servercertifikat har återkallats. Om du inaktiverar den här principinställningen kontrollerar Internet Explorer inte om servercertifikat har återkallats. Om du inte konfigurerar den här principinställningen kontrollerar Internet Explorer inte om servercertifikat har återkallats.
  - **Standard**: Aktiverad 
  
- **Internet Explorer internet zone less privileged sites** (Internet Explorer: mindre privilegierade platser i zonen Internet)  
  Med den här principinställningen kan du ange om webbplatser i mindre privilegierade zoner, till exempel Begränsade platser, kan navigera till den här zonen. Om du aktiverar den här principinställningen kan webbplatser från mindre privilegierade zoner öppna nya fönster i, eller navigera till, den här zonen. Säkerhetszonen körs utan det ytterligare säkerhetslager som tillhandahålls av säkerhetsfunktionen Skydd mot zonförhöjning. Om du väljer Fråga i listrutan visas en varning för användarna om att potentiellt riskabel navigering snart initieras. Om du inaktiverar den här principinställningen förhindras den potentiellt skadliga navigeringen. Säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på inställningen för funktionen Skydd mot zonförhöjning. Om du inte konfigurerar den här principinställningen kan webbplatser från mindre privilegierade zoner öppna nya fönster i, eller navigera till, den här zonen.
  - **Standard**: Inaktivera  

- **Internet Explorer restricted zone file downloads** (Internet Explorer: filhämtningar i zonen Begränsad)  </br>
  Med den här principinställningen kan du ange om filhämtningar ska tillåtas från zonen. Det här alternativet bestäms av zonen på sidan med länken för nedladdningen, inte zonen som filen levereras från. Om du aktiverar den här principinställningen kan filerna laddas ned från zonen. Om du inaktiverar den här inställningen kan inte filer laddas ned från zonen. Om du inte konfigurerar den här principinställningen kan inte filer laddas ned från zonen.
  - **Standard**: Inaktivera  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with authenticode** (Internet Explorer: kör .NET Framework-beroende komponenter som har signerats med Authenticode i zonen Internet)  
  Med den här inställningen kan du ange om .NET Framework-komponenter som har signerats med Authenticode kan köras från Internet Explorer. Dessa komponenter är hanterade kontroller som en objekttagg refererar till och hanterade körbara filer som en länk refererar till. Om du aktiverar den här principinställningen kör Internet Explorer signerade hanterade komponenter. Om du väljer Fråga i listrutan uppmanas användarna att välja om de vill köra signerade hanterade komponenter i Internet Explorer. Om du inaktiverar den här principinställningen kör Internet Explorer inte signerade hanterade komponenter. Om du inte konfigurerar den här principinställningen kör Internet Explorer inte signerade hanterade komponenter.
  - **Standard**: Inaktivera  
  
- **Internet Explorer prevent per user installation of Active X controls** (Internet Explorer: förhindra installation av Active X-kontroller per användare)  </br>
  Med den här principinställningen kan du förhindra installationen av ActiveX-kontroller separat för varje enskild användare. Om du aktiverar den här principinställningen kan ActiveX-kontroller inte installeras per användare. Om du inaktiverar eller inte konfigurerar den här principinställningen kan ActiveX-kontroller installeras per användare.
  - **Standard**: Aktiverad  
  
- **Internet Explorer prevent managing smart screen filter** (Internet Explorer: förhindra hantering av SmartScreen-filtret)  </br>
  Den här inställningen hindrar användarna från att hantera SmartScreen-filtret, som varnar användarna om den webbplats som de besöker är känd för att försöka samla in personlig information via ”nätfiske” eller är känd för att innehålla skadlig kod. Om du aktiverar den här principinställningen uppmanas användaren inte om att aktivera SmartScreen-filtret. Alla webbplatsadresser som inte finns med på filtrets lista för tillåtna webbplatser skickas automatiskt till Microsoft utan att fråga användaren. Om du inaktiverar eller inte konfigurerar den här principinställningen uppmanas användarna att bestämma om de vill aktivera SmartScreen-filtret vid första körningen.
  - **Standard**: Aktivera  
  
- **Internet Explorer processes MIME sniffing safety feature** (Internet Explorer-processer: säkerhetsfunktionen MIME-kontroll)  
  Den här principinställningen anger om funktionen MIME-kontroll i Internet Explorer ska förhindra upphöjning av en fil av en typ till en farligare filtyp. Om du aktiverar den här principinställningen upphöjer funktionen MIME-kontroll aldrig en fil av en typ till en farligare filtyp. Om du inaktiverar den här principinställningen kan Internet Explorer-processer tillåta att MIME-kontroll höjer upp en fil av en typ till en farligare filtyp. Om du inte konfigurerar den här principen upphöjer MIME-kontroll aldrig en fil av en typ till en farligare filtyp.
  - **Standard**: Aktiverad  
  
- **Internet Explorer restricted zone download signed Active X controls** (Internet Explorer: ladda ned signerade Active X-kontroller i zonen Begränsad)  </br>
  Med den här principinställningen kan du bestämma om användare kan ladda ned signerade ActiveX-kontroller från en sida i zonen. Om du aktiverar den här principen kan användarna ladda ned signerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill hämta kontroller som signerats av utfärdare som inte är betrodda. Kod som signerats av betrodda utfärdare hämtas i bakgrunden. Om du inaktiverar den här inställningen kan inte signerade kontroller hämtas. Om du inte konfigurerar den här principinställningen tillfrågas användarna om de vill hämta kontroller som signerats av utfärdare som inte är betrodda. Kod som signerats av betrodda utfärdare hämtas i bakgrunden.
  - **Standard**: Inaktivera  
  
- **Internet Explorer auto complete** (Internet Explorer: automatisk komplettering)  </br>
  Funktionen Komplettera automatiskt kan komma ihåg och föreslå användarnamn och lösenord för formulär. Om du aktiverar den här inställningen kan användarna inte ändra användarnamn och lösenord för formulär eller välja att spara lösenord. Funktionen Komplettera automatiskt för användarnamn och lösenord för formulär aktiveras. Du måste ange om det ska gå att spara lösenord. Om du inaktiverar den här inställningen kan användarna inte ändra användarnamn och lösenord för formulär eller välja om de vill spara lösenord. Funktionen Komplettera automatiskt för användarnamn och lösenord för formulär inaktiveras. Användarna kan inte heller välja om de vill spara lösenord. Om du inte konfigurerar den här inställningen kan användarna välja att aktivera Komplettera automatiskt för användarnamn och lösenord för formulär och välja att bli tillfrågade om de vill spara lösenord. För att visa det här alternativet öppnar användarna dialogrutan Internetalternativ, klickar på fliken Innehåll och sedan på knappen Inställningar.
  - **Standard**: Inaktivera  
  
- **Internet Explorer internet zone allow VBscript to run** (Internet Explorer: tillåt att VBscript-körs i zonen Internet)  </br>
  Med den här inställningen kan du välja om VBScript kan köras på sidor i specifika Internet Explorer-zoner. Om du aktiverar den här principinställningen (standard) måste du även välja något av följande alternativ från rutan Alternativ: Aktivera. VBScript körs på sidor i specifika zoner, utan manuella användaråtgärder. Fråga. Anställda tillfrågas om de vill tillåta att VBScript körs i zonen. Inaktivera. VBScript förhindras att köra i zonen. Om du inaktiverar eller inte konfigurerar den här principinställningen körs VBScript utan inblandning av användaren i den angivna zonen
  - **Standard**: Inaktivera  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls** (Internet Explorer: tillåt endast att godkända domäner använder TDC Active X-kontroller i zonen Begränsad)  </br>
  Den här principinställningen styr huruvida användaren kan köra TDC ActiveX-kontrollen på webbplatser. Om du aktiverar den här principinställningen körs inte TDC ActiveX-kontrollen från webbplatser i den här zonen. Om du inaktiverar den här principinställningen körs TDC ActiveX-kontrollen från alla platser i den här zonen.
  - **Standard**: Aktiverad  
  
- **Internet Explorer trusted zone do not run antimalware against Active X controls** (Internet Explorer: kör inte program mot skadlig kod mot Active X-kontroller i zonen Betrodda platser)   </br>
  Den här principinställningen anger om Internet Explorer kör program mot skadlig kod mot ActiveX-kontroller för att se om det är säkert att läsa in dem på sidor. Om du aktiverar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inaktiverar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inte konfigurerar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Användare kan aktivera eller inaktivera det här beteendet med hjälp av säkerhetsinställningarna för Internet Explorer.
  - **Standard**: Inaktiverad 
  
- **Internet Explorer local machine zone java permissions** (Internet Explorer: Java-behörigheter i zonen Lokal dator)  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop), samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen ställs behörigheten in på Normal säkerhet.
  - **Standard**: Inaktivera Java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls** (Internet Explorer: kör inte program mot skadlig kod mot Active X-kontroller i zonen Intranät)  </br>
  Den här principinställningen anger om Internet Explorer kör program mot skadlig kod mot ActiveX-kontroller för att se om det är säkert att läsa in dem på sidor. Om du aktiverar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inaktiverar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inte konfigurerar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Användare kan aktivera eller inaktivera det här beteendet med hjälp av säkerhetsinställningarna för Internet Explorer.
  - **Standard**: Inaktiverad  

- **Internet Explorer restricted zone scriptlets** (Internet Explorer: skriptlet i zonen Begränsad)  
  Med den här principinställningen kan du ange om användaren kan köra skriptlet. Om du aktiverar den här principinställningen kan användaren köra skriptlet. Om du inaktiverar den här principinställningen kan användaren inte köra skriptlet. Om du inte konfigurerar den här principinställningen kan användaren aktivera eller inaktivera skriptlet.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer processes notification bar** (Internet Explorer-processer: meddelandefältet)  </br>  
  Med den här inställningen kan du ange om meddelandefältet ska visas i Internet Explorer-processer när fil- eller kodinstallationer begränsas. Som standard visas meddelandefältet i Internet Explorer-processer. Om du aktiverar den här principinställningen visas meddelandefältet i Internet Explorer-processer. Om du inaktiverar den här principinställningen visas inte meddelandefältet i Internet Explorer-processer. Om du inte konfigurerar den här principinställningen visas meddelandefältet i Internet Explorer-processer.
  - **Standard**: Aktiverad  
  
- **Internet Explorer internet zone download signed ActiveX controls** (Internet Explorer: ladda ned signerade ActiveX-kontroller i zonen Internet)  </br>
  Med den här principinställningen kan du bestämma om användare kan ladda ned signerade ActiveX-kontroller från en sida i zonen. Om du aktiverar den här principen kan användarna ladda ned signerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill hämta kontroller som signerats av utfärdare som inte är betrodda. Kod som signerats av betrodda utfärdare hämtas i bakgrunden. Om du inaktiverar den här inställningen kan inte signerade kontroller hämtas. Om du inte konfigurerar den här principinställningen tillfrågas användarna om de vill hämta kontroller som signerats av utfärdare som inte är betrodda. Kod som signerats av betrodda utfärdare hämtas i bakgrunden.
  - **Standard**: Inaktivera  
  
- **Internet Explorer restricted zone smart screen** (Internet Explorer: SmartScreen i zonen Begränsad)  
  Den här principinställningen styr huruvida SmartScreen-filtret söker igenom sidor i den här zonen och letar efter skadligt innehåll. Om du aktiverar den här principinställningen söker SmartScreen-filtret igenom sidor i den här zonen och letar efter skadligt innehåll. Om du inaktiverar den här principinställningen söker SmartScreen-filtret inte igenom sidor i den här zonen för att leta efter skadligt innehåll. Om du inte konfigurerar den här principinställningen kan användaren välja om SmartScreen-filtret ska söka igenom sidor i den här zonen och leta efter skadligt innehåll. Obs! I Internet Explorer 7 styr den här principinställningen om nätfiskefiltret söker igenom sidor i den här zonen och letar efter skadligt innehåll.
  - **Standard**: Aktiverad  
  
- **Internet Explorer remove run this time button for outdated Active X controls** (Internet Explorer: ta bort knappen Kör den här gången för inaktuella Active X-kontroller)  </br>
  Med den här principinställningen kan du hindra användare från att se knappen ”Kör den här gången” och från att köra specifika inaktuella ActiveX-kontroller i Internet Explorer. Om du aktiverar den här principinställningen ser inte användarna knappen ”Kör den här gången” i varningsmeddelandet som visas när Internet Explorer blockerar en inaktuell ActiveX-kontroll. Om du inaktiverar eller inte konfigurerar den här principinställningen ser användarna knappen ”Kör den här gången” i varningsmeddelandet som visas när Internet Explorer blockerar en inaktuell ActiveX-kontroll. Genom att klicka på den här knappen kan användaren köra den inaktuella ActiveX-kontrollen en gång. Mer information finns i avsnittet om inaktuella ActiveX-kontroller i TechNet-biblioteket för Internet Explorer.
  - **Standard**: Aktiverad 
  
- **Internet Explorer internet zone launch applications and files in an iframe** (Internet Explorer: starta program och filer i en iframe i zonen Internet)  
  Med den här principinställningen kan du ange om program kan köras och om filer kan laddas ned från en IFRAME-referens i HTML-koden för sidorna i den här zonen. Om du aktiverar den här principinställningen kan användarna köra program och ladda ned filer från en IFRAME på sidorna i den här zonen utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill köra program och ladda ned filer från en IFRAME på sidorna i den här zonen. Om du inaktiverar den här principinställningen hindras användarna från att köra program och ladda ned filer från en IFRAME på sidorna i den här zonen. Om du inte konfigurerar den här principinställningen tillfrågas användarna om de vill köra program och hämta filer från en IFRAME på sidorna i den här zonen
  - **Standard**: Inaktivera 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains** (Internet Explorer: navigera i fönster och ramar mellan olika domäner i zonen Begränsad)  </br>
  Med den här principinställningen kan du ange alternativ för att dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Om du aktiverar den här principinställningen och klickar på Aktivera kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen. Om du aktiverar den här principinställningen och klickar på Inaktivera kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 10 kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 9 och tidigare versioner kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen.
  - **Standard**: Inaktivera  
  
- **Internet Explorer internet zone smart screen** (Internet Explorer: SmartScreen i zonen Internet)  
  Den här principinställningen styr huruvida SmartScreen-filtret söker igenom sidor i den här zonen och letar efter skadligt innehåll. Om du aktiverar den här principinställningen söker SmartScreen-filtret igenom sidor i den här zonen och letar efter skadligt innehåll. Om du inaktiverar den här principinställningen söker SmartScreen-filtret inte igenom sidor i den här zonen för att leta efter skadligt innehåll. Om du inte konfigurerar den här principinställningen kan användaren välja om SmartScreen-filtret ska söka igenom sidor i den här zonen och leta efter skadligt innehåll. Obs! I Internet Explorer 7 styr den här principinställningen om nätfiskefiltret söker igenom sidor i den här zonen och letar efter skadligt innehåll.
  - **Standard**: Aktiverad  
  
- **Internet Explorer locked down trusted zone java permissions** (Internet Explorer: låsta Java-behörigheter i zonen Betrodda platser)  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop), samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar.
  - **Standard**: Inaktivera Java 
  
- **Internet Explorer check signatures on downloaded programs** (Internet Explorer: kontrollera signaturer för nedladdade program)  
  Med den här principinställningen kan du ange om Internet Explorer ska söka efter digitala signaturer (som identifierar utgivaren av signerad programvara och verifierar att den inte har ändrats eller manipulerats) på användarnas datorer innan körbara program laddas ned. Om du aktiverar den här principinställningen letar Internet Explorer efter digitala signaturer för körbara program och visar deras identiteter innan de laddas ned till användarnas datorer. Om du inaktiverar den här principinställningen letar inte Internet Explorer efter digitala signaturer för körbara program och visar inte deras identiteter innan de laddas ned till användarnas datorer. Om du inte konfigurerar den här principen letar inte Internet Explorer efter digitala signaturer för körbara program och visar inte deras identiteter innan de laddas ned till användarnas datorer.
  - **Standard**: Aktiverad  
  
- **Internet Explorer restricted zone scripting of web browser controls** (Internet Explorer: skriptkörning med webbläsarkontroller i zonen Begränsad)  
  Den här principinställningen anger om en sida kan styra inbäddade WebBrowser-kontroller via skript. Om du aktiverar den här principinställningen tillåts skriptåtkomst till WebBrowser-kontrollen. Om du inaktiverar den här principinställningen tillåts inte skriptåtkomst till WebBrowser-kontrollen. Om du inte konfigurerar den här principinställningen kan användarna aktivera eller inaktivera skriptåtkomst till WebBrowser-kontrollen. Som standard tillåts skriptåtkomst till WebBrowser-kontrollen endast i zonerna Lokal dator och Intranät.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer restricted zone cross site scripting filter** (Internet Explorer: skriptfiler mellan webbplatser i zonen Begränsad)  
  Den här principen styr huruvida XSS-filtret (Cross Site-Scripting) identifierar och förhindrar XSS-inmatningar till webbplatser i den här zonen. Om du aktiverar den här principinställningen aktiveras XSS-filtret för platser i den här zonen och XSS-filtret försöker blockera XSS-inmatningar. Om du inaktiverar den här principinställningen inaktiveras XSS-filtret för platser i den här zonen och Internet Explorer tillåter XSS-inmatningar.
  - **Standard**: Aktiverad  
  
- **Internet Explorer restricted zone binary and script behaviors** (Internet Explorer: beteenden för binärfiler och skript i zonen Begränsad)  
  Med den här principinställningen kan du hantera dynamiska beteenden för binärfiler och skript: komponenter som kapslar in specifika funktioner för HTML-element som de kopplats till. Om du aktiverar den här principinställningen är binärfiler och skript tillgängliga. Om du väljer Godkänns av administratör i listrutan är endast beteenden som visas i Uppföranden som godkänns av administratören under säkerhetsbegränsningsprincipen för binärt beteende tillgängliga. Om du inaktiverar den här principinställningen är beteenden för binärfiler och skript inte tillgängliga såvida inte programmen har implementerat en anpassad säkerhetshanterare. Om du inte konfigurerar den här principinställningen är beteenden för binärfiler och skript inte tillgängliga såvida inte programmen har implementerat en anpassad säkerhetshanterare.
  - **Standard**: Inaktivera  
  
- **Internet Explorer security settings check** (Internet Explorer: kontroll av säkerhetsinställningar)  </br>
  Den här principinställningen inaktiverar funktionen för kontroll av säkerhetsinställningar, som kontrollerar säkerhetsinställningarna i Internet Explorer för att avgöra om inställningarna utsätter Internet Explorer för risk. Om du aktiverar den här principinställningen inaktiveras funktionen. Om du inaktiverar eller inte konfigurerar den här principinställningen aktiveras funktionen.
  - **Standard**: Aktiverad  
  
- **Internet Explorer internet zone security warning for potentially unsafe files** (Internet Explorer: säkerhetsvarning om potentiellt osäkra filer i zonen Internet)  
  Den här principinställningen styr huruvida meddelandet ”Öppna fil – säkerhetsvarning” visas när användaren försöker öppna körbara filer eller andra potentiellt skadliga filer (till exempel från en filresurs i intranätet med hjälp av Utforskaren). Om du aktiverar den här principinställningen och väljer Aktivera i listrutan öppnas dessa filer utan någon säkerhetsvarning. Om du väljer Fråga i listrutan visas en säkerhetsvarning innan filerna öppnas. Om du inaktiverar den här principinställningen öppnas inte dessa filer. Om du inte konfigurerar den här principinställningen kan användaren konfigurera hur datorn hanterar dessa. Som standard blockeras dessa filer i zonen Begränsad, tillåts i zonerna Intranät och Lokal dator och har inställningen Fråga i zonerna Internet och Betrodda platser.
  - **Standard**: Fråga  
  
- **Internet Explorer intranet zone java permissions** (Internet Explorer: Java-behörigheter i zonen Intranät)  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop), samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen ställs behörigheten in på Normal säkerhet.
  - **Standard**: Hög säkerhet 
  
- **Internet Explorer block outdated Active X controls** (Internet Explorer: blockera inaktuella Active X-kontroller)  </br>
  Den här principinställningen anger om Internet Explorer blockerar specifika inaktuella ActiveX-kontroller. Inaktuella ActiveX-kontroller blockeras aldrig i zonen Intranät. Om du aktiverar den här principinställningen slutar Internet Explorer att blockera inaktuella ActiveX-kontroller. Om du inaktiverar eller inte konfigurerar den här principinställningen fortsätter Internet Explorer att blockera specifika inaktuella ActiveX-kontroller. Mer information finns i avsnittet om inaktuella ActiveX-kontroller i TechNet-biblioteket för Internet Explorer.
  - **Standard**: Aktiverad  
  
- **Internet Explorer restricted zone popup blocker** (Internet Explorer: popup-blockerare i zonen Begränsad)  
  Med den här principinställningen kan du ange om oönskade popup-fönster ska visas eller inte. Popup-fönster som öppnas när slutanvändaren klickar på en länk blockeras inte. Om du aktiverar den här principinställningen hindras de flesta oönskade popup-fönster från att visas. Om du inaktiverar den här principinställningen hindras inte popup-fönster från att visas. Om du inte konfigurerar den här principinställningen hindras de flesta oönskade popup-fönster från att visas.
  - **Standard**: Aktivera  
  
- **Internet Explorer processes MK protocol security restriction** (Internet Explorer: bearbetning av Säkerhetsbegränsningar för protokollet MK)  
  Principinställningen Säkerhetsbegränsningar för protokollet MK minskar angreppsytan genom att förhindra MK-protokollet. Resurser som hanteras av MK-protokollet misslyckas. Om du aktiverar den här principinställningen blockeras MK-protokollet för Utforskaren och Internet Explorer och resurser som hanteras av MK-protokollet misslyckas. Om du inaktiverar den här principinställningen kan program använda API:et för MK-protokollet. Resurser som hanteras av MK-protokollet fungerar för processerna i Utforskaren och Internet Explorer. Om du inte konfigurerar den här principinställningen blockeras MK-protokollet för Utforskaren och Internet Explorer och resurser som hanteras av MK-protokollet misslyckas.
  - **Standard**: Aktiverad  
  
- **Internet Explorer trusted zone java permissions** (Internet Explorer: Java-behörigheter i zonen Betrodda platser)  </br>
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop), samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen ställs behörigheten in på Låg säkerhet.
  - **Standard**: Hög säkerhet  
  
- **Internet Explorer restricted zone scripting of java applets** (Internet Explorer: skriptkörning med Java-appletar i zonen Begränsad)  
  Med den här principinställningen kan du ange om appletar exponeras för skript i zonen. Om du aktiverar den här principinställningen kan skript komma åt appletar automatiskt utan inblandning av användaren. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att skript kommer åt appletar. Om du inaktiverar den här principinställningen förhindras skript från att komma åt appletar. Om du inte konfigurerar den här inställningen förhindras skript från att komma åt appletar.
  - **Standard**: Inaktivera  
  
- **Internet Explorer locked down restricted zone java permissions** (Internet Explorer: låsta Java-behörigheter i zonen Begränsad)  </br>
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop), samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar.
  - **Standard**: Inaktivera Java 
  
- **Internet Explorer internet zone allow only approved domains to use ActiveX controls** (Internet Explorer: tillåt endast att godkända domäner använder ActiveX-kontroller i zonen Internet)  </br>
  Den här principinställningen styr huruvida användarna tillfrågas om de vill tillåta att ActiveX-kontroller körs på andra webbplatser än den webbplats som ActiveX-kontrollen installerades på. Om du aktiverar den här principinställningen tillfrågas användaren innan ActiveX-kontroller kan köras från webbplatser i den här zonen. Användaren kan välja att tillåta att kontrollen körs från den aktuella webbplatsen eller från alla webbplatser. Om du inaktiverar den här principinställningen ser inte användarna ActiveX-prompten per webbplats och ActiveX-kontroller kan köras från alla webbplatser i den här zonen.
  - **Standard**: Aktiverad  
  
- **Internet Explorer include all network paths** (Internet Explorer: ta med alla nätverkssökvägar)  
  Internet Explorer include all network paths (Internet Explorer: ta med alla nätverkssökvägar)
  - **Standard**: Inaktiverad 
  
- **Internet Explorer internet zone protected mode** (Internet Explorer: skyddat läge i zonen Internet)  
  Med den här principinställningen kan du aktivera skyddat läge. Skyddat läge hjälper dig att skydda Internet Explorer mot säkerhetsproblem genom att begränsa de platser som Internet Explorer kan skriva till i registret och filsystemet. Om du aktiverar den här principinställningen aktiveras skyddat läge. Användaren kan inte inaktivera skyddat läge. Om du inaktiverar den här principinställningen inaktiveras skyddat läge. Användaren kan inte aktivera skyddat läge. Om du inte konfigurerar den här principen kan användaren aktivera eller inaktivera skyddat läge.
  - **Standard**: Aktivera 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe** (Internet Explorer: initiera och kör skript för Active X-kontroller som inte markerats som säkra i zonen Internet)  
  Med den här principinställningen kan du hantera ActiveX-kontroller som inte har markerats som säkra. Om du aktiverar den här principinställningen körs ActiveX-kontroller, initieras med parametrar och körs med skript utan att objektsäkerhet anges för obetrodda data eller skript. Den här inställningen rekommenderas inte, förutom för säkra och administrerade zoner. Den här inställningen gör att både osäkra och säkra kontroller initieras och körs med skript, samtidigt som ActiveX-skriptkontrollerna som markerats som säkra i skriptalternativet ignoreras. Om du aktiverar den här principinställningen och väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontrollen initieras med parametrar eller körs med skript. Om du inaktiverar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar och körs inte med skript. Om du inte konfigurerar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar och körs inte med skript.
  - **Standard**: Inaktivera 
  
- **Internet Explorer locked down restricted zone smart screen** (Internet Explorer: låst SmartScreen i zonen Begränsad)  </br>
  Den här principinställningen styr huruvida SmartScreen-filtret söker igenom sidor i den här zonen och letar efter skadligt innehåll. Om du aktiverar den här principinställningen söker SmartScreen-filtret igenom sidor i den här zonen och letar efter skadligt innehåll. Om du inaktiverar den här principinställningen söker SmartScreen-filtret inte igenom sidor i den här zonen för att leta efter skadligt innehåll. Om du inte konfigurerar den här principinställningen kan användaren välja om SmartScreen-filtret ska söka igenom sidor i den här zonen och leta efter skadligt innehåll. Obs! I Internet Explorer 7 styr den här principinställningen om nätfiskefiltret söker igenom sidor i den här zonen och letar efter skadligt innehåll.
  - **Standard**: Aktiverad  
  
- **Internet Explorer crash detection** (Internet Explorer: kraschidentifiering)  
  Med den här principinställningen kan du hantera kraschidentifieringsfunktionen för tilläggshantering. Om du aktiverar den här principinställningen uppvisar en krasch i Internet Explorer samma beteende som i Windows XP Professional Service Pack 1 och tidigare, nämligen att Windows Felrapportering anropas. Alla principinställningar för Windows Felrapportering fortsätter att tillämpas. Om du inaktiverar eller inte konfigurerar den här principinställningen fungerar kraschidentifieringsfunktionen för tilläggshantering.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer internet zone java permissions** (Internet Explorer: Java-behörigheter i zonen Internet)  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop), samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen ställs behörigheten in på Hög säkerhet.
  - **Standard**: Inaktivera Java  
  
- **Internet Explorer restricted zone active scripting** (Internet Explorer: aktiv skriptkörning i zonen Begränsad)  
  Med den här principinställningen kan du ange om skriptkod på sidor i zonen kan köras. Om du aktiverar den här principinställningen kan skriptkod på sidor i zonen köras automatiskt. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att skriptkod på sidor i zonen körs. Om du inaktiverar den här principinställningen förhindras skriptkod från att köras på sidor i zonen. Om du inte konfigurerar den här principinställningen förhindras skriptkod på sidor i zonen från att köras.
  - **Standard**: Inaktivera  
  
- **Internet Explorer internet zone logon options** (Internet Explorer: inloggningsalternativ i zonen Internet)  
  Med den här principinställningen kan du hantera inställningar för inloggningsalternativ. Om du aktiverar den här principinställningen kan du välja något av följande inloggningsalternativ. Anonym inloggning om du vill inaktivera HTTP-autentisering och gästkontot endast för CIFS-protokollet (Common Internet File System). Fråga efter användarnamn och lösenord om du vill uppmana användare att ange användar-ID:n och lösenord. När en användare har angett värdena kan de användas tyst i bakgrunden under resten av sessionen. Automatisk inloggning endast i zonen Intranät om du vill uppmana användaren att ange användar-ID:n och lösenord i andra zoner. När en användare har angett värdena kan de användas tyst i bakgrunden under resten av sessionen. Automatisk inloggning med aktuellt användarnamn och lösenord för att försöka logga in med Windows NT Challenge Response (även kallat NTLM-autentisering). Om Windows NT Challenge Response stöds av servern används användarens användarnamn och lösenord för nätverket vid inloggningen. Om Windows NT Challenge Response inte stöds av servern uppmanas användaren att ange användarnamnet och lösenordet. Om du inaktiverar den här principinställningen anges inloggningen endast till Automatisk inloggning i zonen Intranät. Om du inte konfigurerar den här principinställningen anges inloggningen endast till Automatisk inloggning i zonen Intranät.
  - **Standard**: Fråga  
  
- **Internet Explorer restricted zone allow vbscript to run** (Internet Explorer: tillåt att vbscript körs i zonen Begränsad)  </br>  
  Med den här principinställningen kan du ange om VBScript kan köras på sidor från den angivna zonen i Internet Explorer. Om du valde Aktivera i listrutan kan VBScript köras utan inblandning av användaren. Om du valde Fråga i listrutan uppmanas användarna att välja om de vill tillåta att VBScript körs. Om du valde Inaktivera i listrutan förhindras VBScript från att köras. Om du inte konfigurerar eller om du inaktiverar den här principinställningen förhindras VBScript från att köra.
  - **Standard**: Inaktivera  
  
- **Internet Explorer internet zone drag content from different domains across windows** (Internet Explorer: dra innehåll från olika domäner mellan fönster i zonen Internet)  
  Med den här principinställningen kan du ange alternativ för att dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Om du aktiverar den här principinställningen och klickar på Aktivera kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen. Om du aktiverar den här principinställningen och klickar på Inaktivera kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 10 kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 9 och tidigare versioner kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen.
  - **Standard**: Inaktiverad 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe** (Internet Explorer: initiera och kör skript för Active X-kontroller som inte markerats som säkra i zonen Intranät)  
  Med den här principinställningen kan du hantera ActiveX-kontroller som inte har markerats som säkra. Om du aktiverar den här principinställningen körs ActiveX-kontroller, initieras med parametrar och körs med skript utan att objektsäkerhet anges för obetrodda data eller skript. Den här inställningen rekommenderas inte, förutom för säkra och administrerade zoner. Den här inställningen gör att både osäkra och säkra kontroller initieras och körs med skript, samtidigt som ActiveX-skriptkontrollerna som markerats som säkra i skriptalternativet ignoreras. Om du aktiverar den här principinställningen och väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontrollen initieras med parametrar eller körs med skript. Om du inaktiverar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar och körs inte med skript. Om du inte konfigurerar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar och körs inte med skript.
  - **Standard**: Inaktivera 
  
- **Internet Explorer download enclosures** (Internet Explorer: ladda ned bilagor)  
  Den här principinställningen hindrar användaren från att ladda ned bilagor (bifogade filer) från en feed till användarens dator. Om du aktiverar den här principinställningen kan användaren inte ange att feed-synkroniseringsmotorn ska ladda ned en bilaga via sidan för feed-egenskaper. Utvecklare kan inte ändra nedladdningsinställningen via Feed-API:et. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren ange att feed-synkroniseringsmotorn ska ladda ned en bilaga via sidan för feed-egenskaper. Utvecklare kan ändra nedladdningsinställningen via Feed-API:et.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer restricted zone download unsigned Active X controls** (Internet Explorer: ladda ned osignerade Active X-kontroller i zonen Begränsad)  </br>
  Med den här principinställningen kan du ange om användarna kan ladda ned osignerade ActiveX-kontroller från zonen. Den här typen av kod kan vara skadlig, särskilt om den kommer från en obetrodd zon. Om du aktiverar den här principinställningen kan användarna köra osignerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att den osignerade kontrollen körs eller inte. Om du inaktiverar den här principinställningen kan användarna inte köra osignerade kontroller. Om du inte konfigurerar den här principinställningen kan användarna inte köra osignerade kontroller.
  - **Standard**: Inaktivera  
  
- **Internet Explorer internet zone drag content from different domains within windows** (Internet Explorer: dra innehåll från olika domäner inuti fönster i zonen Internet)  
  Med den här principinställningen kan du ange om användarna kan ladda ned osignerade ActiveX-kontroller från zonen. Den här typen av kod kan vara skadlig, särskilt om den kommer från en obetrodd zon. Om du aktiverar den här principinställningen kan användarna köra osignerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att den osignerade kontrollen körs eller inte. Om du inaktiverar den här principinställningen kan användarna inte köra osignerade kontroller. Om du inte konfigurerar den här principinställningen kan användarna inte köra osignerade kontroller.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer processes restrict Active X install** (Internet Explorer-processer: begränsa Active X-installation)  </br>
  Den här principinställningen gör det möjligt för program som hanterar webbläsarkontrollen att blockera automatiska frågor om installationen av ActiveX-kontroller. Om du aktiverar den här principinställningen blockerar webbläsarkontrollen automatiska frågor om installationen av ActiveX-kontroller för alla processer. Om du inaktiverar eller inte konfigurerar den här principinställningen blockerar inte webbläsarkontrollen automatiska frågor om installationen av ActiveX-kontroller för alla processer.
  - **Standard**: Aktiverad  
  
- **Internet Explorer internet zone scriptlets** (Internet Explorer: skriptlet i zonen Internet) Med den här principinställningen kan du bestämma om användarna kan köra scriptlet. Om du aktiverar den här principinställningen kan användaren köra skriptlet. Om du inaktiverar den här principinställningen kan användaren inte köra skriptlet. Om du inte konfigurerar den här principinställningen kan användaren aktivera eller inaktivera skriptlet.
  - **Standard**: Inaktivera  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files** (Internet Explorer: dra eller kopiera och klistra in filer i zonen Begränsad)  
  Med den här principinställningen kan du ange om användarna kan dra filer eller kopiera och klistra in filer från en källa i zonen. Om du aktiverar den här principinställningen kan användarna automatiskt dra filer eller kopiera och klistra in filer från den här zonen. Om du väljer Fråga i listrutan tillfrågas användarna om de vill dra eller kopiera filer från den här zonen. Om du inaktiverar den här principinställningen hindras användarna från att dra filer eller att kopiera och klistra in filer från den här zonen. Om du inte konfigurerar den här principinställningen tillfrågas användarna om de vill dra eller kopiera filer från den här zonen.
  - **Standard**: Inaktivera  
  
- **Internet Explorer software when signature is invalid** (Internet Explorer: programvara när signaturen är ogiltig) </br>
  Med den här principinställningen kan du ange om programvara, till exempel ActiveX-kontroller och nedladdning av filer, kan installeras och köras av användaren även om signaturen är ogiltig. En ogiltig signatur kan tyda på att någon har manipulerat filen. Om du aktiverar den här principinställningen tillfrågas användarna innan de kan installera eller köra filer med en ogiltig signatur. Om du inaktiverar den här principinställningen kan användarna inte köra eller installera filer med en ogiltig signatur. Om du inte konfigurerar den här principinställningen kan användarna välja om de vill köra eller installera filer med en ogiltig signatur.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer restricted zone copy and paste via script** (Internet Explorer: kopiera och klistra in via skript i zonen Begränsad) </br> Med den här principinställningen kan du ange om skript kan utföra åtgärder med Urklipp (till exempel Klipp ut, Kopiera och Klistra in) i en angiven region. Om du aktiverar den här principinställningen kan skript utföra åtgärder med Urklipp. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta åtgärder med Urklipp. Om du inaktiverar den här principinställningen kan skript inte utföra åtgärder med Urklipp. Om du inte konfigurerar den här principen kan skript inte utföra åtgärder med Urklipp.
  - **Standard**: Inaktivera  
  
- **Internet Explorer restricted zone drag content from different domains across windows** (Internet Explorer: dra innehåll från olika domäner mellan fönster i zonen Begränsad)  
  Med den här principinställningen kan du ange alternativ för att dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Om du aktiverar den här principinställningen och klickar på Aktivera kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen. Om du aktiverar den här principinställningen och klickar på Inaktivera kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 10 kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 9 och tidigare versioner kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer users adding sites** (Internet Explorer: användarna lägger till platser)  
  Förhindrar att användarna kan lägga till eller ta bort platser från säkerhetszoner. En säkerhetszon är en grupp med webbplatser med samma säkerhetsnivå. Om du aktiverar den här principen inaktiveras platshanteringsinställningarna för säkerhetszoner. (Du kan visa platshanteringsinställningarna för säkerhetszoner i dialogrutan Internetalternativ genom att klicka på fliken Säkerhet och sedan på knappen Platser.) Om du inaktiverar den här principen eller inte konfigurerar den kan användarna lägga till webbplatser till eller ta bort webbplatser från zonerna Betrodda platser och Begränsade platser och ändra inställningarna för zonen Lokalt intranät. Den här principen förhindrar att användarna kan ändra platshanteringsinställningar för säkerhetszoner som angetts av administratören. Obs! Principen ”Inaktivera fliken Säkerhet” (i \Användarkonfiguration\Administrativa mallar\Windows-komponenter\Internet Explorer\Internet på Kontrollpanelen), som tar bort fliken Säkerhet från gränssnittet, prioriteras framför den här principen. Om den aktiveras, ignoreras den här principen. Se även principen”Säkerhetszoner: Använd endast datorinställningar”.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer internet zone script initiated windows** (Internet Explorer: skriptinitierade fönster i zonen Internet)  
  Med den här principinställningen kan du hantera begränsningar för skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet. Om du aktiverar den här principinställningen gäller inte begränsningar för Windows-säkerhet i den här zonen. Säkerhetszonen körs utan det ytterligare säkerhetslager som tillhandahålls av den här funktionen. Om du inaktiverar den här principinställningen kan inte de potentiellt skadliga åtgärderna i skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet köras. Den här säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på kontrollinställningen för skriptinitierade säkerhetsbegränsningar för Windows. Om du inte konfigurerar den här principinställningen kan inte de potentiellt skadliga åtgärderna i skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet köras. Den här säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på kontrollinställningen för skriptinitierade säkerhetsbegränsningar för Windows.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer security zones use only machine settings** (Internet Explorer: säkerhetszoner använder endast datorinställningar)  
  Använder information om säkerhetszoner för alla användare på samma dator. En säkerhetszon är en grupp med webbplatser med samma säkerhetsnivå. Om du aktiverar den här principen tillämpas ändringar som användaren gör i en säkerhetszon på alla användare av den aktuella datorn. Om du inaktiverar den här principen eller inte konfigurerar den kan användare på samma dator konfigurera egna inställningar för säkerhetszoner. Den här principen ser till att inställningarna för säkerhetszoner är enhetliga på samma dator och att de inte varierar mellan användare. Se även principen”Säkerhetszoner: Tillåt inte att användare ändrar principer”.
  - **Standard**: Aktiverad  
  
- **Internet Explorer locked down local machine zone java permissions** (Internet Explorer: låsta Java-behörigheter i zonen Lokal dator)  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop), samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar
  - **Standard**: Inaktivera Java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls** (Internet Explorer: kör inte program mot skadlig kod mot Active X-kontroller i zonen Begränsad)  </br>
  Den här principinställningen anger om Internet Explorer kör program mot skadlig kod mot ActiveX-kontroller för att se om det är säkert att läsa in dem på sidor. Om du aktiverar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inaktiverar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inte konfigurerar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Användare kan aktivera eller inaktivera det här beteendet med hjälp av säkerhetsinställningarna för Internet Explorer.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode** (Internet Explorer: kör .NET Framework-beroende komponenter som har signerats med Authenticode i zonen Begränsad)  
  Med den här inställningen kan du ange om .NET Framework-komponenter som har signerats med Authenticode kan köras från Internet Explorer. Dessa komponenter är hanterade kontroller som en objekttagg refererar till och hanterade körbara filer som en länk refererar till. Om du aktiverar den här principinställningen kör Internet Explorer signerade hanterade komponenter. Om du väljer Fråga i listrutan uppmanas användarna att välja om de vill köra signerade hanterade komponenter i Internet Explorer. Om du inaktiverar den här principinställningen kör Internet Explorer inte signerade hanterade komponenter. Om du inte konfigurerar den här principinställningen kör Internet Explorer inte signerade hanterade komponenter.
  - **Standard**: Inaktivera  
  
- **Internet Explorer restricted zone access to data sources** (Internet Explorer: åtkomst till datakällor i zonen Begränsad)  
  Med den här inställningen kan du ange om Internet Explorer kan komma åt data från en annan säkerhetszon med hjälp av Microsoft XML Parser (MSXML) eller ActiveX Data Objects (ADO). Om du aktiverar den här principinställningen kan användarna läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta inläsningen av en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du inaktiverar den här principinställningen kan användarna inte läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du inte konfigurerar den här principinställningen kan användarna inte läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen.
  - **Standard**: Inaktivera 
  
- **Internet Explorer internet zone do not run antimalware against ActiveX controls** (Internet Explorer: kör inte program mot skadlig kod mot ActiveX-kontroller i zonen Internet)  </br>
  Den här principinställningen anger om Internet Explorer kör program mot skadlig kod mot ActiveX-kontroller för att se om det är säkert att läsa in dem på sidor. Om du aktiverar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inaktiverar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inte konfigurerar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Användare kan aktivera eller inaktivera det här beteendet med hjälp av säkerhetsinställningarna för Internet Explorer.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer internet zone copy and paste via script** (Internet Explorer: kopiera och klistra in via skript i zonen Internet) </br> Med den här principinställningen kan du ange om skript kan utföra åtgärder med Urklipp (till exempel Klipp ut, Kopiera och Klistra in) i en angiven region. Om du aktiverar den här principinställningen kan skript utföra åtgärder med Urklipp. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta åtgärder med Urklipp. Om du inaktiverar den här principinställningen kan skript inte utföra åtgärder med Urklipp. Om du inte konfigurerar den här principen kan skript utföra åtgärder med Urklipp.
  - **Standard**: Inaktivera  
  
- **Internet Explorer use Active X installer service** (Internet Explorer: använd Active X-installationstjänsten)  </br>
  Med den här principinställningen kan du ange hur ActiveX-kontroller installeras. Om du aktiverar den här principinställningen installeras ActiveX-kontroller endast om ActiveX-installationstjänsten är tillgänglig och har konfigurerats att tillåta installationen av ActiveX-kontroller. Om du inaktiverar eller inte konfigurerar den här principinställningen installeras ActiveX-kontroller, inklusive kontroller för varje användare, via standardinstallationsprocessen.
  - **Standard**: Aktiverad  
  
- **Internet Explorer processes protection from zone elevation** (Internet Explorer: skydda processer från zonupplyftning)  
  Internet Explorer begränsar varje webbsida som öppnas. Begränsningarna är beroende av webbsidans plats (Internet, intranät, zonen Lokal dator och så vidare). Till exempel har webbsidor på den lokala datorn minst begränsningar och finns i zonen Lokal dator, vilket gör den lokala datorn till ett favoritmål för illvilliga användare. Om du aktiverar den här principinställningen kan alla zoner skyddas från zonupplyftning för alla processer. Om du inaktiverar eller inte konfigurerar den här principinställningen skyddas inte andra processer än Internet Explorer och de som anges i processlistan på detta sätt.
  - **Standard**: Aktiverad  
  
- **Internet Explorer internet zone download unsigned ActiveX controls** (Internet Explorer: ladda ned osignerade ActiveX-kontroller i zonen Internet)  </br>
  Med den här principinställningen kan du ange om användarna kan ladda ned osignerade ActiveX-kontroller från zonen. Den här typen av kod kan vara skadlig, särskilt om den kommer från en obetrodd zon. Om du aktiverar den här principinställningen kan användarna köra osignerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att den osignerade kontrollen körs eller inte. Om du inaktiverar den här principinställningen kan användarna inte köra osignerade kontroller. Om du inte konfigurerar den här principinställningen kan användarna inte köra osignerade kontroller.
  - **Standard**: Inaktivera  
  
- **Internet Explorer internet zone navigate windows and frames across different domains** (Internet Explorer: navigera i fönster och ramar mellan olika domäner i zonen Internet)  </br>
  Med den här principinställningen kan du ange hur fönster och ramar öppnas och hur program kommer åt dem från olika domäner. Om du aktiverar den här principinställningen kan användarna öppna fönster och ramar från andra domäner och komma åt program från andra domäner. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att fönster och ramar kommer åt program från andra domäner. Om du inaktiverar den här principinställningen kan användarna inte öppna fönster och ramar för att komma åt program från olika domäner. Om du inte konfigurerar den här principinställningen kan användarna öppna fönster och ramar från andra domäner och komma åt program från andra domäner.
  - **Standard**: Inaktivera  
  
- **Internet Explorer internet zone updates to status bar via script** (Internet Explorer: uppdateringar av statusfältet via skript i zonen Internet)  
  Med den här principinställningen kan du bestämma om skript ska tillåtas att uppdatera statusfältet i zonen. Om du aktiverar den här principinställningen kan skript uppdatera statusfältet. Om du inaktiverar eller inte konfigurerar den här principinställningen kan inte skript uppdatera statusfältet.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer restricted zone include local path when uploading files to server** (Internet Explorer: ta med lokal sökväg när filer laddas upp till servern i zonen Begränsad)  </br> Den här principinställningen styr huruvida information om den lokala sökvägen skickas eller inte när användaren laddar upp en fil via ett HTML-formulär. Om information om den lokala sökvägen skickas kan servern oavsiktligt få tillgång till viss information. Filer som skickas från användarens dator kan exempelvis innehålla användarnamnet som en del av sökvägen. Om du aktiverar den här principinställningen skickas information om sökvägen när användaren överför en fil via ett HTML-formulär. Om du inaktiverar den här principinställningen tas information om sökvägen bort när användaren överför en fil via ett HTML-formulär. Om du inte konfigurerar den här principinställningen kan användarna välja om sökvägsinformation ska skickas när de laddar upp en fil via ett HTML-formulär. Sökvägsinformation skickas som standard.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer processes restrict file download** (Internet Explorer-processer: begränsa filnedladdning)  </br> Den här principinställningen gör det möjligt för program som hanterar webbläsarkontrollen att blockera automatiska frågor om filnedladdningar som inte har initierats av användaren. Om du aktiverar den här principinställningen blockerar webbläsarkontrollen automatiska frågor om filnedladdningar som inte har initierats av användaren för alla processer. Om du inaktiverar den här principinställningen blockerar webbläsarkontrollen inte automatiska frågor om filnedladdningar som inte har initierats av användaren för alla processer.
  - **Standard**: Aktiverad  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls** (Internet Explorer: tillåt endast att godkända domäner använder Active X-kontroller i zonen Begränsad)  </br>
  Den här principinställningen styr huruvida användarna tillfrågas om de vill tillåta att ActiveX-kontroller körs på andra webbplatser än den webbplats som ActiveX-kontrollen installerades på. Om du aktiverar den här principinställningen tillfrågas användaren innan ActiveX-kontroller kan köras från webbplatser i den här zonen. Användaren kan välja att tillåta att kontrollen körs från den aktuella webbplatsen eller från alla webbplatser. Om du inaktiverar den här principinställningen ser inte användarna ActiveX-prompten per webbplats och ActiveX-kontroller kan köras från alla webbplatser i den här zonen.
  - **Standard**: Aktiverad  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe** (Internet Explorer: initiera och kör skript för Active X-kontroller som inte markerats som säkra i zonen Begränsad)  
  Med den här principinställningen kan du hantera ActiveX-kontroller som inte har markerats som säkra. Om du aktiverar den här principinställningen körs ActiveX-kontroller, initieras med parametrar och körs med skript utan att objektsäkerhet anges för obetrodda data eller skript. Den här inställningen rekommenderas inte, förutom för säkra och administrerade zoner. Den här inställningen gör att både osäkra och säkra kontroller initieras och körs med skript, samtidigt som ActiveX-skriptkontrollerna som markerats som säkra i skriptalternativet ignoreras. Om du aktiverar den här principinställningen och väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontrollen initieras med parametrar eller körs med skript. Om du inaktiverar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar och körs inte med skript. Om du inte konfigurerar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar och körs inte med skript.
  - **Standard**: Inaktivera  
  
- **Internet Explorer users changing policies** (Internet Explorer: användare ändrar principer)  
    Hindrar användare från att ändra inställningarna för säkerhetszoner. En säkerhetszon är en grupp med webbplatser med samma säkerhetsnivå. Om du aktiverar den här principen inaktiveras knappen Anpassad nivå och skjutreglaget för säkerhetsnivå på fliken Säkerhet i dialogrutan Internetalternativ. Om du inaktiverar den här principen eller inte konfigurerar den kan användarna ändra inställningarna för säkerhetszoner. Den här principen hindrar användarna från att ändra inställningarna för säkerhetszoner som angetts av administratören. Obs! Principen ”Inaktivera fliken Säkerhet” (i \Användarkonfiguration\Administrativa mallar\Windows-komponenter\Internet Explorer\Internet på Kontrollpanelen), som tar bort fliken Säkerhet i Internet Explorer på Kontrollpanelen prioriteras framför den här principen. Om den aktiveras, ignoreras den här principen. Se även principen”Säkerhetszoner: Använd endast datorinställningar”.
    - **Standard**: Inaktiverad  
  
- **Internet Explorer restricted zone protected mode** (Internet Explorer: skyddat läge i zonen Begränsad)  
  Med den här principinställningen kan du aktivera skyddat läge. Skyddat läge hjälper dig att skydda Internet Explorer mot säkerhetsproblem genom att begränsa de platser som Internet Explorer kan skriva till i registret och filsystemet. Om du aktiverar den här principinställningen aktiveras skyddat läge. Användaren kan inte inaktivera skyddat läge. Om du inaktiverar den här principinställningen inaktiveras skyddat läge. Användaren kan inte aktivera skyddat läge. Om du inte konfigurerar den här principen kan användaren aktivera eller inaktivera skyddat läge.
  - **Standard**: Aktivera  
  
- **Internet Explorer internet zone user data persistence** (Internet Explorer: datapersistence av användare i zonen Internet)  
  Med den här principinställningen kan du hantera lagringen av information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. När en användare kommer tillbaka till en bestående sida, kan sidans tillstånd återställas om den här principinställningen är korrekt konfigurerad. Om du aktiverar den här principinställningen kan användarna lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. Om du inaktiverar den här principinställningen kan användarna inte lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. Om du inte konfigurerar den här principinställningen kan användarna lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer internet zone scripting of web browser controls** (Internet Explorer: skriptkörning med webbläsarkontroller i zonen Internet)  
 
  Den här principinställningen anger om en sida kan styra inbäddade WebBrowser-kontroller via skript. Om du aktiverar den här principinställningen tillåts skriptåtkomst till WebBrowser-kontrollen. Om du inaktiverar den här principinställningen tillåts inte skriptåtkomst till WebBrowser-kontrollen. Om du inte konfigurerar den här principinställningen kan användarna aktivera eller inaktivera skriptåtkomst till WebBrowser-kontrollen. Som standard tillåts skriptåtkomst till WebBrowser-kontrollen endast i zonerna Lokal dator och Intranät.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer restricted zone user data persistence** (Internet Explorer: datapersistence av användare i zonen Begränsad)  
    Med den här principinställningen kan du hantera lagringen av information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. När en användare kommer tillbaka till en bestående sida, kan sidans tillstånd återställas om den här principinställningen är korrekt konfigurerad. Om du aktiverar den här principinställningen kan användarna lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. Om du inaktiverar den här principinställningen kan användarna inte lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. Om du inte konfigurerar den här principinställningen kan användarna inte lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk.  
  - **Standard**: Inaktiverad  
  
- **Internet Explorer locked down intranet zone java permissions** (Internet Explorer: låsta Java-behörigheter i zonen Intranät)  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop), samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar.
  - **Standard**: Inaktivera Java  
  
- **Internet Explorer enhanced protected mode** (Internet Explorer: utökat skyddat läge)  
  Utökat skyddat läge ger ytterligare skydd mot skadliga webbplatser genom att använda 64-bitarsprocesser i 64-bitarsversioner av Windows. För datorer som kör minst Windows 8 begränsar utökat skyddat läge också vilka platser Internet Explorer kan läsa från i registret och filsystemet. Om du aktiverar den här principinställningen aktiveras utökat skyddat läge. Alla zoner som har skyddat läge aktiverat använder utökat skyddat läge. Användarna kan inte inaktivera utökat skyddat läge. Om du inaktiverar den här principinställningen inaktiveras utökat skyddat läge. Alla zoner som har skyddat läge aktiverat använder den version av skyddat läge som introducerades i Internet Explorer 7 för Windows Vista. Om du inte konfigurerar den här principen kan användarna aktivera eller inaktivera utökat skyddat läge på fliken Avancerat i dialogrutan Internetalternativ.
  - **Standard**: Aktiverad  
  
- **Internet Explorer bypass smart screen warnings** (Internet Explorer: kringgå SmartScreen-varningar)  
  Den här principinställningen anger om användaren kan kringgå varningar från SmartScreen-filtret. SmartScreen-filtret varnar användaren om körbara filer som Internet Explorer-användare vanligtvis inte laddar ned från Internet. Om du aktiverar den här principinställningen blockerar SmartScreen-filtret användaren. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren kringgå varningar från SmartScreen-filtret.
  - **Standard**: Inaktiverad  
  
- **Internet Explorer restricted zone meta refresh** (Internet Explorer: metauppdatering i zonen Begränsad)  
  Med den här principinställningen kan du ange om en användares webbläsare kan omdirigeras till en annan webbsida om den som skapat webbsidan använder inställningen för uppdatering av metadata (tagg) för att omdirigera till en annan webbsida. Om du aktiverar den här principinställningen kan en användares webbläsare som läser in en sida som innehåller en aktiv inställning för metadatauppdatering omdirigeras till en annan webbsida. Om du inaktiverar den här principinställningen kan inte en användares webbläsare som läser in en sida som innehåller en aktiv inställning för metadatauppdatering omdirigeras till en annan webbsida. Om du inte konfigurerar den här principinställningen kan inte en användares webbläsare som läser in en sida som innehåller en aktiv inställning för metadatauppdatering omdirigeras till en annan webbsida.
  - **Standard**: Inaktiverad  
  
## <a name="local-policies-security-options"></a>Säkerhetsalternativ för lokala principer
Mer information finns i [CSP-princip – LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) i Windows-dokumentationen. 

- **Restrict anonymous access to named pipes and shares** (Begränsa anonym åtkomst till namngivna pipes och resurser)  
  När den här säkerhetsinställningen är aktiverad begränsar den anonym åtkomst för resurser och pipes till inställningar för: (1) Namngivna pipes som kan nås anonymt (2) Resurser som kan nås anonymt
  - **Standard**: Ja  
  
- **Minimum session security for NTLM SSP based servers** (Minsta sessionssäkerhet för NTLM SSP-baserade servrar)  
  Den här säkerhetsinställningen gör att en server kan kräva förhandling av 128-bitarskryptering och/eller NTLMv2-sessionssäkerhet. Dessa värden är beroende av säkerhetsinställningen för autentiseringsnivån för LAN Manager. Alternativen är: Kräv NTLMv2-sessionssäkerhet: Anslutningen misslyckas om inte meddelandeintegritet förhandlas. Kräv 128-bitarskryptering. Anslutningen misslyckas om inte stark kryptering (128-bitars) förhandlas.
  - **Standard**: Kräv NTLM V2 och 128-bitarskryptering  
  
- **Minuter av låsskärmsinaktivitet innan skärmsläckaren aktiveras**  
  Windows övervakar inaktiviteten för en inloggningssession och om inaktiviteten överstiger inaktivitetsgränsen aktiveras skärmsläckaren och sessionen låses.
  - **Standard**: 15
  
- **Require client to always digitally sign communications** (Kräv att klienten alltid signerar kommunikation digitalt) Den här säkerhetsinställningen anger om all säker trafik som initieras av domänmedlemmen måste signeras eller krypteras. När en dator ansluter till en domän skapas ett datorkonto. När datorn sedan startas använder den lösenordet för datorkontot för att skapa en säker kanal med en domänkontrollant för dess domän. Den här säkra kanalen används för att utföra åtgärder som NTLM-direktautentisering, LSA SID/namnuppslag osv. Den här inställningen anger huruvida all säker kanaltrafik som initieras av domänmedlemmen uppfyller säkerhetskraven. Mer specifikt anger den om all säker kanaltrafik som initieras av domänmedlemmen måste signeras eller krypteras. Om den här principen aktiveras upprättas inte den säkra kanalen, såvida inte signering eller kryptering av all säker kanaltrafik förhandlas. Om den här principen inaktiveras förhandlas kryptering och signering av all säker kanaltrafik med domänkontrollanten. I så fall beror signerings- och krypteringsnivån på domänkontrollantens version och inställningarna för följande två principer: Domänmedlem: Kryptera data för säker kanal digitalt (om det är möjligt) Domänmedlem: Signera säkra kanaldata digitalt (om det är möjligt)
  - **Standard**: Ja
  
- **Autentiseringsnivå**  
  Den här säkerhetsinställningen avgör vilket autentiseringsprotokoll för anrop/svar som används för nätverksinloggningar. Den här inställningen påverkar nivån för autentiseringsprotokollet som används av klienter, nivån för den förhandlade sessionssäkerheten och autentiseringsnivån som accepteras av servrar enligt följande: Skicka LM- och NTLM-svar: Klienter använder LM- och NTLM-autentisering och använder aldrig NTLMv2-sessionssäkerhet; domänkontrollanter accepterar LM-, NTLM- och NTLMv2-autentisering. Skicka LM och NTLM – använd NTLMv2-sessionssäkerhet om det förhandlats: Klienter använder LM- och NTLM-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det; domänkontrollanter accepterar LM-, NTLM- och NTLMv2-autentisering. Skicka endast NTLM-svar: Klienter använder endast NTLM-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det; domänkontrollanter accepterar LM-, NTLM- och NTLMv2-autentisering. Skicka endast NTLMv2-svar: Klienter använder endast NTLMv2-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det; domänkontrollanter accepterar LM-, NTLM- och NTLMv2-autentisering. Skicka endast NTLMv2-svar/neka LM: Klienter använder endast NTLMv2-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det; domänkontrollanter nekar LM (accepterar endast NTLM- och NTLMv2-autentisering). Skicka endast NTLMv2-svar/neka LM och NTLM: Klienter använder endast NTLMv2-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det; domänkontrollanter nekar LM- och NTLM (accepterar endast NTLMv2-autentisering).
  - **Standard**: Skicka endast NTLMv2-svar. Neka LM och NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers** (Förhindra att klienter skickar okrypterade lösenord till SMB-servrar från tredje part)  
  Om den här säkerhetsinställningen är aktiverad kan SMB-omdirigeraren (Server Message Block) skicka lösenord i klartext till SMB-servrar från tredje part som inte har stöd för lösenordskryptering under autentiseringen. Att skicka okrypterade lösenord utgör en säkerhetsrisk.
  - **Standard**: Ja
  
- **Disable server digitally signing communications always** (Inaktivera alltid digital signering av kommunikation av servrar)  
  Den här säkerhetsinställningen anger om SMB-klienten ska försöka förhandla om SMB-paketsignering. SMB-protokollet (Server Message Block) lägger grunden för Microsofts fil- och skrivardelning och många andra nätverksfunktioner, till exempel fjärradministration för Windows. För att förhindra man-i-mitten-attacker som ändrar SMB-paket under överföring, stöder SMB-protokollet digital signering av SMB-paket. Den här principinställningen anger om SMB-klientkomponenten ska försöka förhandla om SMB-paketsignering när den ansluter till en SMB-server. Om den här inställningen är aktiverad uppmanar Microsoft-nätverksklienten servern att utföra SMB-paketsignering när sessionen upprättas. Om paketsignering har aktiverats på servern, förhandlas paketsignering. Om principen är inaktiverad förhandlar SMB-klienten aldrig om SMB-paketsignering.
  - **Standard**: Ja
  
- **Administrator elevation prompt behavior** (Fråga om beteende för utökade administratörsprivilegier)  
  Den här principinställningen styr beteendet för frågan om utökade privilegier för administratörer. Alternativen är: 0 – Utöka privilegier utan att fråga: Tillåter att behöriga konton utför en åtgärd som kräver utökade privilegier utan att kräva godkännande eller autentiseringsuppgifter. Obs! Använd endast det här alternativet i de mest begränsade miljöerna. 1 – Fråga efter autentiseringsuppgifter på det skyddade skrivbordet: När en åtgärd kräver utökade privilegier uppmanas användaren att ange ett privilegierat användarnamn och lösenord på det skyddade skrivbordet. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med användarens högsta behörigheter. 2 – Fråga efter medgivande på det skyddade skrivbordet: När en åtgärd kräver utökade privilegier uppmanas användaren att välja Tillåt eller Neka på det skyddade skrivbordet. Om användaren väljer Tillåt fortsätter åtgärden med användarens högsta behörigheter. 3 – Fråga efter autentiseringsuppgifter: När en åtgärd kräver utökade privilegier uppmanas användaren att ange ett användarnamn och lösenord för administratörer. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med tillämplig behörighet. 4 – Fråga efter medgivande: När en åtgärd kräver utökade privilegier uppmanas användaren att välja Tillåt eller Neka. Om användaren väljer Tillåt fortsätter åtgärden med användarens högsta behörigheter. 5 – Fråga efter medgivande för binära filer som inte tillhör Windows: (Standard) När en åtgärd för ett program från tredje part kräver utökade privilegier uppmanas användaren att välja Tillåt eller Neka på det skyddade skrivbordet. Om användaren väljer Tillåt fortsätter åtgärden med användarens högsta behörigheter
  - **Standard**: Fråga efter medgivande på det skyddade skrivbordet
  
- **Minimum session security for NTLM SSP based clients** (Minsta sessionssäkerhet för NTLM SSP-baserade klienter)  
  Den här säkerhetsinställningen gör att en klient kan kräva förhandling av 128-bitarskryptering och/eller NTLMv2-sessionssäkerhet. Dessa värden är beroende av säkerhetsinställningen för autentiseringsnivån för LAN Manager. Alternativen är: Kräv NTLMv2-sessionssäkerhet: Anslutningen misslyckas om inte NTLMv2-protokollet förhandlas. Kräv 128-bitarskryptering: Anslutningen misslyckas om inte stark kryptering (128-bitars) förhandlas.
  - **Standard**: Kräv NTLM V2 128-kryptering
  
- **Beteende vid borttagning av smartkort**  
  Den här säkerhetsinställningen avgör vad som händer när smartkortet för en inloggad användare tas bort från smartkortsläsaren. Alternativen är: Ingen åtgärd Lås arbetsstation Framtvinga utloggning Koppla från om Remote Desktop Services-session Om du klickar på Lås arbetsstation i dialogrutan Egenskaperna för den här principen kommer arbetsstationen att låsas när smartkortet tas bort, så att användarna kan lämna området, ta med sig smartkortet och ändå upprätthålla en skyddad session. Om du klickar på Framtvinga utloggning i dialogrutan Egenskaper för den här principen loggas du automatiskt ut när smartkortet tas bort. Om du klickar på Koppla från om Remote Desktop Services-session, kopplas sessionen från utan att användaren loggas ut när smartkortet avlägsnas. Med det här alternativet kan användaren sätta i smartkortet och fortsätta sessionen senare, eller vid en annan dator med smartkortsläsare, utan att behöva logga in igen. Om sessionen är lokal fungerar den här principen precis som Lås arbetsstationen.
  - **Standard**: Lås arbetsstation
  
- **Block anonymous enumeration of SAM accounts and shares** (Blockera anonym uppräkning av SAM-konton och resurser)  
  Den här säkerhetsinställningen anger om anonym uppräkning av SAM-konton och resurser tillåts. Windows tillåter att anonyma användare utför vissa aktiviteter, till exempel att räkna upp namn på domänkonton och nätverksresurser. Detta är exempelvis praktiskt när en administratör vill bevilja åtkomst till användare i en betrodd domän som inte har ett ömsesidigt förtroende. Aktivera den här principen om du inte vill tillåta anonym uppräkning av SAM-konton och resurser.
  - **Standard**: Ja
  
- **Block remote logon with blank password** (Blockera fjärrinloggning med tomt lösenord)  
  Den här säkerhetsinställningen anger om lokala konton som inte är lösenordsskyddade kan användas för att logga in från andra platser än den fysiska datorkonsolen. Om inställningen är aktiverad kommer lokala konton som inte är lösenordsskyddade endast att kunna logga in via datorns tangentbord. Varning! Datorer som inte är skyddade rent fysiskt bör alltid framtvinga principer för starka lösenord för alla lokala användarkonton. Annars kan alla med fysisk tillgång till datorn logga in med ett användarkonto som inte har något lösenord. Detta är särskilt viktigt för bärbara datorer. Om du använder den här säkerhetsprincipen för gruppen Alla kommer ingen att kunna logga in via Fjärrskrivbordstjänster. Den här inställningen påverkar inte inloggningar som använder domänkonton. Det är möjligt för program som använder interaktiva fjärrinloggningar att kringgå den här inställningen.
  - **Standard**: Ja
  
- **Standard user elevation prompt behavior** (Standardbeteende för utökade användarprivilegier)  
  Den här principinställningen styr beteendet för frågan om utökade privilegier för användare. 0 – Neka förfrågningar om höjd behörighet automatiskt: När en åtgärd kräver utökade privilegier visas ett konfigurerbart felmeddelande om nekad åtkomst. Ett företag som kör skrivbordsdatorer som standardanvändare kan välja den här inställningen för att minska antalet supportsamtal. 1 – Fråga efter autentiseringsuppgifter på det skyddade skrivbordet: När en åtgärd kräver utökade privilegier uppmanas användaren att ange ett annat användarnamn och lösenord på det skyddade skrivbordet. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med tillämplig behörighet. 3 (standard) – fråga efter autentiseringsuppgifter: När en åtgärd kräver utökade privilegier uppmanas användaren att ange ett användarnamn och lösenord för administratörer. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med tillämplig behörighet.
  - **Standard**: Neka förfrågningar om utökade privilegier automatiskt
  
- **Require admin approval mode for administrators** (Kräv läge för administratörstillåtelse för administratörer)  
  Den här principinställningen styr beteendet för alla UAC-principinställningar (User Account Control) för datorn. Om du ändrar den här inställningen måste du starta om datorn. Alternativen är: 0 – Inaktiverad: Läge för administratörstillåtelse och alla relaterade UAC-principinställningar är inaktiverade. Obs! Om den här inställningen är inaktiverad meddelar i Security Center dig om att den övergripande säkerheten för operativsystemet har minskas. 1 – Aktiverad: (Standard) Läge för administratörstillåtelse är aktiverat. Den här principen måste vara aktiverad och associerade UAC-principinställningar måste också anges på lämpligt sätt så att det inbyggda administratörskontot och alla andra användare som är medlemmar i gruppen Administratörer kan köra i läget för administratörstillåtelse.
  - **Standard**: Ja
  
- **Prevent anonymous enumeration of SAM accounts** (Förhindra anonym uppräkning av SAM-konton)  
  Den här säkerhetsinställningen anger vilka ytterligare behörigheter som beviljas för anonyma anslutningar till datorn. Windows tillåter att anonyma användare utför vissa aktiviteter, till exempel att räkna upp namn på domänkonton och nätverksresurser. Detta är exempelvis praktiskt när en administratör vill bevilja åtkomst till användare i en betrodd domän som inte har ett ömsesidigt förtroende. Det här säkerhetsalternativet tillåter ytterligare begränsningar för anonyma anslutningar på följande sätt: Aktiverad: Tillåt inte uppräkning av SAM-konton. Det här alternativet ersätter alternativet Alla med Autentiserade användare i säkerhetsbehörigheterna för resurser. Inaktiverad: Inga ytterligare begränsningar. Använd standardbehörigheter. Standardvärde på arbetsstationer: Aktiverad. Standardvärde på servern: Aktiverad.
  - **Standard**: Ja
  
- **Allow remote calls to security accounts manager** (Tillåt fjärranrop till hanteraren för kontosäkerhet)  
  Med den här principinställningen kan du begränsa RPC-fjärranslutningar till SAM. Om du inte väljer den används standardsäkerhetsbeskrivningen.
  - **Standard**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode** (Använd läge för administratörstillåtelse)  
  Den här principinställningen styr beteendet för läget för administratörstillåtelse för det inbyggda administratörskontot. Alternativen är: • Aktiverad: Det inbyggda administratörskontot använder läget för administratörstillåtelse. Som standard uppmanas användaren att tillåta åtgärder som kräver utökade privilegier. • Inaktiverad: (Standard) Det inbyggda administratörskontot kör alla program med administratörsprivilegier.
  - **Standard**: Ja
  
- **Allow UI access applications for secure locations** (Tillåt UIAccess-program för säkra platser)  
  Den här principinställningen styr om UIAccess- eller UIA-program (User Interface Accessibility ) kan inaktivera det säkra skrivbordet automatiskt för att fråga om förhöjd behörighet när de används av en standardanvändare. Aktiverad: UIA-program, inklusive Windows Fjärrhjälp, inaktiverar automatiskt det skyddade skrivbordet för frågor om utökade privilegier. Om du inte inaktiverar principinställningen ”User Account Control: Switch to the secure desktop when prompting for elevation” (User Account Control: Växla till det säkra skrivbordet vid frågor om utökade privilegier) visas frågorna på den interaktiva användarens skrivbord i stället för på det skyddade skrivbordet. Inaktiverad: (Standard) Det skyddade skrivbordet kan endast inaktiveras av användaren av det interaktiva skrivbordet eller genom att principinställningen ”User Account Control: Switch to the secure desktop when prompting for elevation” inaktiveras (User Account Control: Växla till det säkra skrivbordet vid frågor om utökade privilegier).
  - **Standard**: Ja

- **Detect application installations and prompt for elevation** (Identifiera programinstallationer och fråga om utökade privilegier)  
  Den här principinställningen styr beteendet för identifiering av programinstallationer för datorn. Alternativen är: Aktiverad: (Standard) När ett programinstallationspaket identifieras som kräver utökade privilegier uppmanas användaren att ange användarnamnet och lösenordet för en administrativ användare. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med tillämplig behörighet. Inaktiverad: Programinstallationspaket identifieras inte och inga frågor om utökade privilegier visas. Företag som kör skrivbord för standardanvändare och använder tekniker för delegerad installation, till exempel programvaruinstallation för Grupprincip eller SMS (Systems Management Server), bör inaktivera den här principinställningen. I det här fallet är identifieringen av installationsprogram inte nödvändigt.
  - **Standard**: Ja
  
- **Prevent storing LAN manager hash value on next password change** (Förhindra lagring av hash-värdet för LAN Manager vid nästa lösenordsändring)  
  Den här säkerhetsinställningen anger om hash-värdet för LAN Manager (LM) för det nya lösenordet lagras vid nästa lösenordsändring. LM-hashen är relativt svag och känslig för attacker jämfört med den kryptografiskt starkare Windows NT-hashen. Eftersom LM-hashvärdet lagras på den lokala datorn i säkerhetsdatabasen kan lösenorden komprometteras om säkerhetsdatabasen attackeras.
  - **Standard**: Ja

- **Virtualize file and registry write failures to per user locations** (Virtualisera skrivfel för filer och register till platser per användare)  
  Den här principinställningen styr om programskrivningsfel omdirigeras till angivna register- och filsystemplatser. Den här principinställningen minskar risken med program som kör som administratörer och skriver körningsprogramdata till %ProgramFiles%, %Windir%, %Windir%\system32, or HKLM\Software.
  - **Standard**: Ja

## <a name="ms-security-guide"></a>MS-Säkerhetsguide  
Mer information finns i [CSP-princip – MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) i Windows-dokumentationen.  

- **Apply UAC restrictions to local accounts on network logon** (Använd UAC-begränsningar för lokala konton vid nätverksinloggning)  
    - **Standard**: Aktiverad
  
- **SMB v1 client driver start configuration** (Startkonfiguration för SMB v1-klientdrivrutin)  
  - **Standard**: Inaktiverad drivrutin
  
- **SMB v1-server**  
  - **Standard**: Inaktiverad
  
- **Sammanfattad autentisering**  
  - **Standard**: Inaktiverad
  
- **Structured exception handling overwrite protection** (Strukturerat överskrivningsskydd vid undantagshantering)  
  - **Standard**: Aktiverad
  
## <a name="mss-legacy"></a>MSS Legacy  
Mer information finns i [CSP-princip – MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) i Windows-dokumentationen.  

- **Network IP source routing protection level** (Skyddsnivå för routning för IP-nätverkskälla)  
  - **Standard**: Högsta skydd 
  
- **Network ignore NetBIOS name release requests except from WINS servers** (Ignorera begäranden om NetBIOS-namnfrigörande från WINS-servrar i nätverket)  
  - **Standard**: Aktiverad
  
- **Network IPv6 source routing protection level** (Skyddsnivå för routning för IPv6-nätverkskälla)  
  - **Standard**: Högsta skydd

- **Network ICMP redirects override OSPF generated** (ICMP-omdirigeringar åsidosätter OSPF-genererade rutter i nätverket)  
  - **Standard**: Inaktiverad
  
## <a name="power"></a>Ström  
Mer information finns i [CSP-princip – Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) i Windows-dokumentationen.  

- **Require password on wake while plugged in** (Kräv lösenord när datorn aktiveras och är ansluten)  
  Den här principinställningen anger om användaren uppmanas att ange ett lösenord när datorn återgår från strömsparläge. Om du aktiverar eller inte konfigurerar den här principinställningen uppmanas användaren att ange ett lösenord när datorn återgår från strömsparläge. Om du inaktiverar den här principinställningen uppmanas inte användaren att ange ett lösenord när datorn återgår från strömsparläge.
  - **Standard**: Aktiverad
  
- **Standby states when sleeping while on battery** (Väntelägen i viloläge vid batteridrift)  
  Den här principinställningen anger om Windows kan använda väntelägen när datorn försätts i viloläge. Om du aktiverar eller inte konfigurerar den här principinställningen använder Windows väntelägen för att försätta datorn i viloläge. Om du inaktiverar den här principinställningen tillåts inte väntelägen (S1 S3).
  - **Standard**: Inaktiverad
  
- **Standby states when sleeping while plugged in** (Väntelägen där datorn är i viloläge och ansluten)  
  Den här principinställningen anger om Windows kan använda väntelägen när datorn försätts i viloläge. Om du aktiverar eller inte konfigurerar den här principinställningen använder Windows väntelägen för att försätta datorn i viloläge. Om du inaktiverar den här principinställningen tillåts inte väntelägen (S1 S3).
  - **Standard**: Inaktiverad
  
- **Require password on wake while on battery** (Kräv lösenord vid aktivering under batteridrift)  
  Den här principinställningen anger om användaren uppmanas att ange ett lösenord när datorn återgår från strömsparläge. Om du aktiverar eller inte konfigurerar den här principinställningen uppmanas användaren att ange ett lösenord när datorn återgår från strömsparläge. Om du inaktiverar den här principinställningen uppmanas inte användaren att ange ett lösenord när datorn återgår från strömsparläge.
  - **Standard**: Aktiverad
  
## <a name="remote-desktop-services"></a>Fjärrskrivbordstjänster  
Mer information finns i [CSP-princip – RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) i Windows-dokumentationen.  

- **Block password saving** (Tillåt inte att lösenord sparas)  
  Styr om lösenord kan sparas på den här datorn från Anslutning till fjärrskrivbord. Om du aktiverar den här inställningen inaktiveras kryssrutan om att spara lösenord i Anslutning till fjärrskrivbord och användarna kan inte längre spara lösenord. När en användare öppnar en RDP-fil med hjälp av Anslutning till fjärrskrivbord och sparar sina inställningar tas eventuella lösenord som tidigare fanns i RDP-filen bort. Om du inaktiverar den här inställningen eller inte konfigurerar den kan användaren spara lösenord med hjälp av Anslutning till fjärrskrivbord.
  - **Standard**: Aktiverad
  
- **Secure RPC communication** (Säker RPC-kommunikation)  
  Anger om en värdserver för fjärrskrivbordssessioner kräver säker RPC-kommunikation med alla klienter eller om osäker kommunikation tillåts. Du kan använda den här inställningen för att öka säkerheten vid RPC-kommunikation med klienter genom att endast tillåta autentiserade och krypterade begäranden. Om statusen är inställd på Aktiverad accepterar Fjärrskrivbordstjänster begäranden från RPC-klienter som stöder säkra begäranden och tillåter inte osäker kommunikation med obetrodda klienter. Om statusen är inställd på Inaktiverad begär Fjärrskrivbordstjänster alltid säkerhet för all RPC-trafik. Osäker kommunikation tillåts dock för RPC-klienter som inte svarar på begäran. Om statusen är inställd på Inte konfigurerad tillåts osäker kommunikation. Obs! RPC-gränssnittet används för att administrera och konfigurera Fjärrskrivbordstjänster.
  - **Standard**: Aktiverad
  
- **Block drive redirection** (Blockera omdirigering av enheter)  
  Med den här principinställningen kan du ange om du vill förhindra mappningen av klientenheter i en session med Fjärrskrivbordstjänster (omdirigering). Som standard mappar en värdserver för fjärrskrivbordssessioner automatiskt klientenheter när anslutningen upprättas. Mappade enheter visas i trädet för sessionsmappar i Utforskaren eller på datorn i formatet *\<enhetsbeteckning >* på *\<datornamn>*. Du kan använda den här principinställningen om du vill åsidosätta detta beteende. Om du aktiverar den här principinställningen tillåts inte omdirigering av klientenheter i sessioner med Fjärrskrivbordstjänster och omdirigeringar av filkopiering med Urklipp tillåts inte på datorer som kör Windows Server 2003, Windows 8 och Windows XP. Om du inaktiverar den här principinställningen tillåts alltid omdirigering av klientenheter. Dessutom tillåts alltid omdirigering av filkopiering med Urklipp om omdirigering av Urklipp är tillåtet. Om du inte konfigurerar den här principinställningen anges inte omdirigering av klientenheter och omdirigering av filkopiering med Urklipp på grupprincipnivå.
  - **Standard**: Aktiverad
  
- **Prompt for password upon connection** (Fråga efter lösenord vid anslutning)  
  Den här principinställningen anger om Fjärrskrivbordstjänster alltid frågar klienten efter ett lösenord när anslutningen upprättas. Du kan använda den här inställningen för att framtvinga en lösenordsfråga för användare som loggar in i Fjärrskrivbordstjänster, även om de redan har angett lösenordet i Anslutning till fjärrskrivbord-klienten. Som standard tillåter Fjärrskrivbordstjänster användarna att logga in automatiskt genom att ange ett lösenord i Anslutning till fjärrskrivbord-klienten. Om du aktiverar den här principinställningen kan användarna inte logga in automatiskt i Fjärrskrivbordstjänster genom att ange lösenord i Anslutning till fjärrskrivbord-klienten. De uppmanas att ange ett lösenord för att logga in. Om du inaktiverar den här principinställningen kan användarna alltid logga in i Fjärrskrivbordstjänster automatiskt genom att ange lösenord i Anslutning till fjärrskrivbord-klienten. Om du inte konfigurerar den här principinställningen anges inte automatisk inloggning på grupprincipnivå. 
  - **Standard**: Aktiverad
  
- **Remote desktop services client connection encryption level** (Krypteringsnivå för klientanslutning med Fjärrskrivbordstjänster)  
  Anger om du vill kräva en specifik krypteringsnivå för att skydda kommunikationen mellan klientdatorer och värdservrar för fjärrskrivbordssessioner under RDP-anslutningar (Remote Desktop Protocol). Den här principen gäller bara när du använder inbyggd RDP-kryptering. Inbyggd RDP-kryptering (till skillnad mot SSL-kryptering) rekommenderas dock inte. Den här principen gäller inte för SSL-kryptering. Om du aktiverar den här principinställningen måste all kommunikation mellan klienter och värdservrar för fjärrskrivbordssessioner under fjärranslutningar använda krypteringsmetoden som anges i den här inställningen. Som standard är krypteringsnivån inställd på Hög. Följande krypteringsmetoder är tillgängliga:  
  - *Hög*: Med inställningen Hög krypteras data som skickas från klienten till servern och från servern till klienten med hjälp av stark 128-bitarskryptering. Använd den här krypteringsnivån i miljöer som bara innehåller 128-bitarsklienter (till exempel klienter som kör Anslutning till fjärrskrivbord). Klienter som inte stöder den här krypteringsnivån kan inte ansluta till värdservrar för fjärrskrivbordssessioner.  
  - *Klientkompatibel* : Med inställningen Klientkompatibel krypteras data som skickas mellan klienten och servern med den högsta nyckellängden som stöds av klienten. Använd den här krypteringsnivån i miljöer som inkluderar klienter som inte stöder 128-bitarskryptering.  
  - *Låg*: Med inställningen Låg krypteras endast data som skickas från klienten till servern med hjälp av 56-bitarskryptering.  
  
  Om du inaktiverar eller inte konfigurerar den här inställningen tillämpas inte krypteringsnivån som ska användas för fjärranslutningar till värdservrar för fjärrskrivbordssessioner via en grupprincip. Viktigt! FIPS-kompatibilitet kan konfigureras via Systemkryptografi. Använd FIPS-kompatibla algoritmer för krypterings-, hashing- och signeringsinställningar i Grupprincip (under Datorkonfiguration\Windows-inställningar\Säkerhetsinställningar\Lokala principer\Säkerhetsalternativ.) Inställningen FIPS-kompatibel krypterar och dekrypterar data som skickas från klienten till servern och från servern till klienten med FIPS 140-krypteringsalgoritmerna (Federal Information Processing Standard) med hjälp av Microsofts kryptografiska moduler. Använd den här krypteringsnivån när kommunikation mellan klienter och värdservrar för fjärrskrivbordssessioner kräver högsta krypteringsnivå.
  - **Standard**: Hög
  
## <a name="remote-management"></a>Fjärrhantering  
Mer information finns i [CSP-princip – RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) i Windows-dokumentationen.  

- **Block storing run as credentials** (Blockera lagring av ”kör som”-autentiseringsuppgifter)  
  Client basic authentication (Grundläggande klientautentisering)
  - **Standard**: Aktiverad
  
- **Grundläggande autentisering**  
  Med den här principinställningen kan du ange om tjänsten WinRM (Windows Remote Management) accepterar grundläggande autentisering från en fjärransluten klient. Om du aktiverar den här principinställningen accepterar WinRM-tjänsten grundläggande autentisering från en fjärransluten klient. Om du inaktiverar eller inte konfigurerar den här principinställningen accepterar WinRM-tjänsten inte grundläggande autentisering från en fjärransluten klient.
  - **Standard**: Inaktiverad
  
- **Block client digest authentication** (Blockera sammanfattad autentisering för klient)  
  Med den här inställningen kan du ange om WinRM-klienten (Windows Remote Management) använder sammanfattad autentisering. Om du aktiverar den här principinställningen använder inte WinRM-klienten sammanfattad autentisering. Om du inaktiverar eller inte konfigurerar den här principinställningen använder WinRM-klienten sammanfattad autentisering.
  - **Standard**: Aktiverad
  
- **Okrypterad trafik**  
  Med den här principinställningen kan du ange om tjänsten WinRM (Windows Remote Management) skickar och tar emot okrypterade meddelanden över nätverket. Om du aktiverar den här principinställningen skickar och tar WinRM-klienten emot okrypterade meddelanden över nätverket. Om du inaktiverar eller inte konfigurerar den här principinställningen skickar eller tar WinRM-klienten endast emot krypterade meddelanden över nätverket.  
  - **Standard**: Inaktiverad
  
- **Okrypterad klienttrafik**  
  Med den här principinställningen kan du ange om klienten WinRM (Windows Remote Management) ska skicka och ta emot okrypterade meddelanden över nätverket. Om du aktiverar den här principinställningen skickar och tar WinRM-klienten emot okrypterade meddelanden över nätverket. Om du inaktiverar eller inte konfigurerar den här principinställningen skickar eller tar WinRM-klienten endast emot krypterade meddelanden över nätverket.
  - **Standard**: Inaktiverad
  
- **Grundläggande klientautentisering**  
  Med den här inställningen kan du ange om WinRM-klienten (Windows Remote Management) använder grundläggande autentisering. Om du aktiverar den här principinställningen använder WinRM-klienten grundläggande autentisering. Om WinRM har konfigurerats att använda HTTP-transport skickas användarnamnet och lösenordet över nätverket i klartext. Om du inaktiverar eller inte konfigurerar den här principinställningen använder WinRM-klienten inte grundläggande autentisering.
  - **Standard**: Inaktiverad
  

## <a name="remote-procedure-call"></a>RPC (Remote Procedure Call)  
Mer information finns i [CSP-princip – RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) i Windows-dokumentationen.  

- **RPC unauthenticated client options** (Alternativ för oautentiserad klient med RPC)  
  Den här principinställningen styr hur RPC-serverkörningar hanterar oautentiserade RPC-klienter som ansluter till RPC-servrar. Den här principinställningen påverkar alla RPC-program. I en domänmiljö bör den här principinställningen används med försiktighet eftersom den kan påverka en mängd olika funktioner, inklusive själva bearbetningen av grupprinciper. Återställning av ändringar i den här principinställningen kan kräva manuella åtgärder på varje dator som påverkas. Den här principinställningen bör aldrig tillämpas på en domänkontrollant. Om du inaktiverar den här inställningen använder RPC-serverkörningen värdet ”Autentiserad” på Windows-klienten och värdet ”Ingen” i Windows Server-versioner som stöder den här principinställningen. Om du inte konfigurerar den här principinställningen förblir den inaktiverad. RPC-serverkörningen beter sig som om den var aktiverad med värdet ”Autentiserad” för Windows-klienter och värdet ”Ingen” för Server-SKU:er som har stöd för den här principinställningen. Om du aktiverar den här principinställningen beordras RPC-serverkörningen att begränsa oautentiserade RPC-klienter som ansluter till RPC-servrar på en dator. En klient betraktas som en autentiserad klient om den använder en namngiven pipe för att kommunicera med servern eller om den använder RPC-säkerhet. RPC-gränssnitt som uttryckligen har begärt att vara tillgängliga för oautentiserade klienter kan undantas från den här begränsningen, beroende på det valda värdet för den här principinställningen.  
  - *Ingen* gör att alla RPC-klienter kan ansluta till RPC-servrar som körs på den dator där principinställningen tillämpas. 
  - *Autentiserad* tillåter endast att autentiserade RPC-klienter (enligt definitionen ovan) ansluter till RPC-servrar som körs på den dator där principinställningen tillämpas. Undantag beviljas till gränssnitt som har begärt dem. 
  - *Autentiserad utan undantag* tillåter endast att autentiserade RPC-klienter (enligt definitionen ovan) ansluter till RPC-servrar som körs på den dator där principinställningen tillämpas. Inga undantag tillåts. Obs! Den här principinställningen tillämpas inte förrän datorn startas om.  

  - **Standard**: Autentiserad

## <a name="search"></a>Sök 
Mer information finns i [CSP-princip – Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) i Windows-dokumentationen.  

- **Disable indexing encrypted items** (Inaktivera indexering av krypterade objekt)  
  Tillåter eller nekar indexering av objekt. Den här växeln används för Windows Search-indexeraren och styr om objekt som är krypterade indexeras, till exempel WIP-skyddade filer (Windows Information Protection). När principen är aktiverad indexeras Windows informationsskyddade objekt och deras metadata lagras på en okrypterad plats. Dessa metadata innehåller exempelvis ändrade sökvägar och datum. När principen är inaktiverad indexeras inte Windows informationsskyddade objekt och resultaten visas inte i Cortana eller Utforskaren. Prestanda kan även påverkas med foton och Groove-appar om det finns många WIP-skyddade mediefiler på enheten.
  - **Standard**: Ja
  
## <a name="smart-screen"></a>Smart skärm  
Mer information finns i [CSP-princip – SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) i Windows-dokumentationen.  

- **Block execution of unverified files** (Blockera körning av overifierade filer)  
  Blockera användare från att köra overifierade filer. 0 – Anställda kan ignorera SmartScreen-varningar och köra skadliga filer. 1 – Anställda kan inte ignorera SmartScreen-varningar och köra skadliga filer.
  - **Standard**: Ja

- **Block unverified file download** (Blockera nedladdning av overifierade filer)  
  Som standard tillåter Microsoft Edge att användarna kringgår (ignorerar) Windows Defender SmartScreen-varningar om potentiellt skadliga filer, så att de kan fortsätta att ladda ned overifierade filer. Om den här principen aktiveras kan användarna inte kringgå varningarna och hindras från att ladda ned overifierade filer.
  - **Standard**: Ja
  
- **Require SmartScreen for apps and files** (Kräv SmartScreen för appar och filer)  
  Gör det möjligt för IT-administratörer att konfigurera SmartScreen för Windows.
  - **Standard**: Ja
  
## <a name="system"></a>System  
Mer information finns i [CSP-princip – System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) i Windows-dokumentationen.  

- **System boot start driver initialization** (Initiering av startdrivrutiner för systemstart)  
  Med den här principinställningen kan du ange vilka startdrivrutiner för systemstart som ska initieras baserat på en klassificering som bestäms av en ELAM-startdrivrutin (Early Launch Antimalware). ELAM-startdrivrutinen (Early Launch Antimalware) kan returnera följande klassificeringar för varje startdrivrutin: – Bra: Drivrutinen har signerats och har inte manipulerats.  
  - *Dålig* – Drivrutinen har identifierats som skadlig kod. Vi rekommenderar att du inte tillåter att kända skadliga drivrutiner initieras. – Dålig, men krävs för start: Drivrutinen har identifierats som skadlig kod, men måste läsas in för att datorn ska kunna starta korrekt. 
  - *Okänd* – Drivrutinen har inte utvärderats av ditt program för identifiering av skadlig kod och har inte klassificerats av ELAM-startdrivrutinen.  

  Om du aktiverar den här principinställningen kan du välja vilka startdrivrutiner som ska initieras nästa gång datorn startas. Om du inaktiverar eller inte konfigurerar den här principinställningen initieras startdrivrutiner som har bedömts vara bra, okända eller dåliga men nödvändiga för systemstart och initieringen av drivrutiner som har bedömts vara dåliga hoppas över. Om ditt program för identifiering av skadlig kod inte inkluderar en ELAM-startdrivrutin eller om ELAM-startdrivrutinen har inaktiverats har den här inställningen ingen effekt och alla startdrivrutiner initieras.  
  - **Standard**: Bra, okänd och dålig men nödvändig

## <a name="wi-fi"></a>Wi-Fi  
Mer information finns i [CSP-princip – Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) i Windows-dokumentationen.  

- **Wi-Fi**  
  Anger om Internetdelning är möjligt på enheten.
  - **Standard**: Ja  

- **Block Automatically connecting to Wi-Fi hotspots** (Blockera automatiskt anslutning till Wi-Fi-hotspot)  
  Tillåt eller förhindra att enheten ansluter automatiskt till en Wi-Fi-hotspot.  
  - **Standard**: Ja  
  
## <a name="windows-connection-manager"></a>Windows Connection Manager  
Mer information finns i [CSP-princip – WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) i Windows-dokumentationen.  

- **Block connection to non-domain networks** (Blockera anslutning till icke-domänbaserade nätverk)  
  Den här principinställningen förhindrar att datorer ansluter till både ett domänbaserat nätverk och ett icke-domänbaserat nätverk på samma gång. Om den här principinställningen är aktiverad svarar datorn på automatiska och manuella anslutningsförsök baserat på följande villkor: 
  - Automatiska anslutningsförsök Om datorn redan är ansluten till ett domänbaserat nätverk blockeras alla automatiska anslutningsförsök till icke-domänbaserade nätverk. Om datorn redan är ansluten till ett icke-domänbaserat nätverk blockeras automatiska anslutningsförsök till domänbaserade nätverk. 
  - Manuella anslutningsförsök Om datorn redan är ansluten till antingen ett icke-domänbaserat nätverk eller till ett domänbaserat nätverk över ett annat medium än Ethernet, och en användare försöker skapa en manuell anslutning till ytterligare ett nätverk i strid med den här principinställningen, kopplas den befintliga nätverksanslutningen från och den manuella anslutningen tillåts. Om datorn redan är ansluten till antingen ett icke-domänbaserat nätverk eller till ett domänbaserat nätverk över Ethernet, och en användare försöker skapa en manuell anslutning till ytterligare ett nätverk i strid mot den här principinställningen, upprätthålls den befintliga Ethernet-anslutningen och det manuella anslutningsförsöket blockeras.  

  Om den här inställningen inte konfigureras eller om den inaktiveras kan datorer ansluta samtidigt till både domänbaserade nätverk och icke-domänbaserade nätverk.
  - **Standard**: Aktiverad
  
## <a name="windows-defender"></a>Windows försvarare  
Mer information finns i [CSP-princip – Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) i Windows-dokumentationen.  

- **Scan incoming mail messages** (Sök igenom inkommande e-postmeddelanden)  
  Tillåter eller nekar genomsökning av e-post.
  - **Standard**: Ja  

- **Office apps launch child process type** (Office-appar startar underordnad processtyp)  
  Office-appar kan inte skapa underordnade processer. Detta inkluderar Word, Excel, PowerPoint, OneNote och Access. Det här är ett typiskt beteende i skadlig kod, särskilt vid makrobaserade attacker som försöker använda Office-appar för att starta eller hämta skadliga körbara filer.
  - **Standard**: Blockera
  
- **Defender sample submission consent type** (Medgivandetyp i Defender för överföring av dataprover)  
  Kontrollerar nivån för användarmedgivande i Windows Defender för att skicka data. Om nödvändigt godkännande redan har beviljats, skickar Windows Defender dem. Om inte (och om användaren har valt att aldrig bli tillfrågad) startas användargränssnittet för att be om användarens medgivande (när Defender/AllowCloudProtection tillåts) innan data skickas.
  - **Standard**: Skicka säkra prover automatiskt 
  
- **Intervall för signaturuppdatering (i timmar)**  
  Signaturuppdateringsintervall i timmar i Defender
  - **Standard**: 4
  
- **Script downloaded payload execution type** (Körningstyp för nedladdad nyttolast med skript)  
  Körningstyp för nedladdad nyttolast med Defender-skript
  - **Standard**: Blockera
  
- **Prevent credential stealing type** (Förhindra typ av stöld av autentiseringsuppgifter)  
  Windows Defender Credential Guard använder virtualiseringsbaserad säkerhet för att isolera hemligheter så att endast privilegierad programvara kan komma åt dem. Obehörig åtkomst till dessa hemligheter kan leda till stöld av autentiseringsuppgifter, till exempel Pass-The-Hash eller Pass-The-Ticket. Windows Defender Credential Guard förhindrar dessa attacker genom att skydda NTLM-hashvärden för lösenord, biljettbeviljande Kerberos-biljetter och autentiseringsuppgifter som lagras av program som autentiseringsuppgifter för en domän.
  - **Standard**: Aktivera

- **Email content execution type** (Körbara filtyper i e-postinnehåll)  
  Den här regeln blockerar följande filtyper från att köras eller startas från ett e-postmeddelande i Microsoft Outlook eller webbaserad e-post (till exempel Gmail.com eller Outlook.com): Körbara filer (t.ex. .exe, .dll eller .scr), skriptfiler (t.ex. en PowerShell .ps-fil, VisualBasic .vbs-fil eller JavaScript .js-fil) och skriptarkivfiler.
  - **Standard**: Blockera
  
- **Network protection type** (Typ av nätverksskydd)  
  Med den här principen kan du aktivera nätverksskydd (blockera/granska) eller inaktivera nätverksskydd i Windows Defender Exploit Guard. Nätverksskydd är en funktion i Windows Defender Exploit Guard som skyddar anställda som använder appar mot nätfiske, webbplatser som utnyttjar sårbarheter samt skadligt innehåll på Internet. Exempelvis hindras webbläsare från tredje part från att ansluta till farliga platser. Värdetypen är ett heltal. Om du aktiverar den här principinställningen aktiveras nätverksskydd och anställda kan inte inaktivera funktionen. Beteendet kan styras med följande alternativ: Blockera och granska. Om du aktiverar den här principen med alternativet ”Blockera” hindras användare/appar från att ansluta till farliga domäner. Du kan se den här aktiviteten i Windows Defender Security Center. Om du aktiverar den här principen med alternativet ”Granska” hindras inte användare/appar från att ansluta till farliga domäner. Du kommer dock fortfarande att se den här aktiviteten i Windows Defender Security Center. Om du inaktiverar den här principen blockeras inte användare/appar från att ansluta till farliga domäner. Du kommer inte att se någon nätverksaktivitet i Windows Defender Security Center. Om du inte konfigurerar den här principen inaktiveras nätverksblockering som standard.
  - **Standard**: Aktivera
  
- **Defender schedule scan day** (Genomsökningsschema (dag) i Defender)  
  Genomsökningsschema (dag) i Defender.
  - **Standard**: Varje dag
  
- **Molnlevererat skydd**  
  För att skydda din dator på bästa sätt skickar Windows Defender information till Microsoft om problem påträffas. Microsoft analyserar informationen, lär sig mer om problem som påverkar dig och andra kunder och erbjuder bättre lösningar.
  - **Standard**:  Ja  

- **Defender potentially unwanted app action** (Potentiellt oönskad appåtgärd i Defender)  
  Funktionen för skydd mot potentiellt oönskade program (PUA, Potentially Unwanted Application) i Windows Defender Antivirus kan identifiera och hindra potentiellt oönskade program från att hämtas och installeras på slutpunkter i ditt nätverk. Dessa program betraktas inte som virus, skadlig kod eller andra typer av hot, men kan utföra åtgärder på slutpunkter som negativt påverkar deras prestanda eller användning. Potentiellt oönskade program syftar även på program med dåligt rykte. Exempel på potentiellt oönskade program är: Olika typer av programvarupaket, AD-inmatning i webbläsare, drivrutins- och registeroptimerare som identifierar problem och begär betalning för att åtgärda felen, men som finns kvar på slutpunkten utan att göra några ändringar eller optimeringar (även kallade ”falska” antivirusprogram). Dessa program kan öka risken för att ditt nätverk infekteras av skadlig kod, kan göra det svårare att identifiera infektioner av skadlig kod, samt kan leda till slöseri med IT-resurser som tvingas rensa bort programmen.  
  - **Standard**: Blockera  

- **Script obfuscated macro code type** (Makrokod dold i skriptfiler)  
  Skadlig kod och andra hot kan försöka förvränga eller dölja skadlig kod i vissa skriptfiler. Den här regeln förhindrar att skript som verkar vara dolda körs.
  - **Standard**: Blockera
  
- **Sök igenom flyttbara drivrutiner vid fullständig genomsökning**  
  Tillåter att Windows Defender söker efter skadlig och oönskad programvara på flyttbara enheter (till exempel flash-enheter) under en fullständig genomsökning. Windows Defender Antivirus söker igenom alla filer på USB-enheter innan de körs.
  - **Standard**: Ja  
  
- **Sök igenom arkivfiler**  
  Defender söker igenom arkivfiler.
  - **Standard**: Ja
  
- **Beteendeövervakning**  
  Tillåter eller nekar funktionen Övervaka funktionssätt i Windows Defender. Dessa sensorer är inbäddade i Windows 10 och samlar in och bearbetar beteendesignaler från operativsystemet och skickar dessa sensordata till din privata, isolerade molninstans av Windows Defender ATP.
  - **Standard**: Ja

- **Sök igenom filer öppnade från nätverksmappar**  
  Om filerna är skrivskyddade kan användaren inte ta bort identifierad skadlig kod.
  - **Standard**: Ja

- **Untrusted USB process type** (Obetrodd USB-processtyp)  
  Med den här regeln kan administratörer förhindra att osignerade eller ej betrodda körbara filer körs från flyttbara USB-enheter, till exempel SD-kort.
  - **Standard**: Blockera
  
- **Office apps other process injection type** (Annan processinmatningstyp i Office-appar)  
  Office-appar, inklusive Word, Excel, PowerPoint och OneNote kan inte mata in kod i andra processer. Detta används vanligtvis av skadlig kod för att köra skadlig kod i ett försök att dölja aktivitet från motorer för virusgenomsökning.
  - **Standard**:  Blockera
  
- **Office macro code allow Win32 imports type** (Office-makrokod tillåter Win32-importer)  
  Skadlig kod kan använda makrokod i Office-filer för att importera och läsa in Win32-DLL:er, som sedan kan användas för att göra API-anrop som leder till ytterligare infektion hela systemet. Den här regeln försöker blockera Office-filer som innehåller makrokod som kan importera Win32-DLL:er. Detta inkluderar Word, Excel, PowerPoint och OneNote.
  - **Standard**: Blockera  
  
- **Defender cloud block level** (Molnblockeringsnivå i Defender)  
  Molnblockeringsnivå i Defender.
  - **Standard**: Inte konfigurerat

- **Realtidsövervakning**  
  Defender kräver övervakning i realtid.
  - **Standard**: Ja
  
- **Office apps executable content creation or launch type** (Generering eller starttyp för körbart innehåll i Office-appar)  
  Den här regeln gäller typiska beteenden som används av misstänkta och skadliga tillägg och skript (tillägg) som skapar eller startar körbara filer. Det här är en vanlig teknik som används av skadlig kod. Tillägg hindras från att användas av Office-appar. De här tilläggen använder vanligtvis Windows Scripting Host (WSH-filer) för att köra skript som automatiserar vissa uppgifter eller tillhandahåller användargenererade tilläggsfunktioner
  - **Standard**: Blockera

## <a name="windows-ink-workspace"></a>Windows Ink-arbetsytan  
Mer information finns i [CSP-princip – WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) i Windows-dokumentationen.  

- **Ink-arbetsytan**  
  Anger huruvida användaren ska få åtkomst till Ink-arbetsytan. 0 – åtkomsten till ink-arbetsytan är inaktiverad. Funktionen är inaktiverad. 1 – ink-arbetsytan är aktiverad, men användaren kan inte komma åt den på låsskärmen. 2 (standard) – ink-arbetsytan är aktiverad och användaren kan använda den på låsskärmen.
  - **Standard**: Aktiverad
 
## <a name="windows-powershell"></a>Windows PowerShell  
Mer information finns i [CSP-princip – WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) i Windows-dokumentationen.  

- **Power shell shell script block logging** (Loggning av skriptblock i PowerShell-gränssnittet)  
  Den här inställningen aktiverar loggning av alla PowerShell-skriptindata i Microsoft-Windows-PowerShell/Operational-händelseloggen. Om du aktiverar den här principinställningen loggar Windows PowerShell bearbetningen av kommandon, skriptblock, funktioner och skript – oavsett om de anropas interaktivt eller via automatisering. Om du inaktiverar den här principinställningen inaktiveras loggning av PowerShell-skriptindata. Om du aktiverar loggning av indata av skriptblock loggar PowerShell även händelser om anrop av ett kommando, skriptblock, funktion eller skript startar eller stoppar. Om du aktiverar loggning av anrop genereras ett stort antal händelseloggar. Obs! Den här principinställningen finns under både Datorkonfiguration och Användarkonfiguration i redigeraren för grupprinciper. Principinställningen Datorkonfiguration ges företräde framför principinställningen Användarkonfiguration.
  - **Standard**: Aktiverad
 
