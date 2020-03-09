---
title: Inställningar för Intune-säkerhetsbaslinjer för Windows 10 MDM
titleSuffix: Microsoft Intune
description: Granska standardinställningarna och de tillgängliga inställningarna för de olika versionerna av säkerhetsbaslinjen för mobilenhetshantering i Windows som du kan hantera med Microsoft Intune.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/07/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
zone_pivot_groups: windows-mdm-versions
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a46532467f8de7caf8cc88fe60e7a5cbc10ba147
ms.sourcegitcommit: a25f556aa9df4fcd9fdacccd12c9029bc6c5fe20
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256534"
---
# <a name="windows-mdm-security-baseline-settings-for-intune"></a>Inställningar för Windows MDM-säkerhetsbaslinjer för Intune

Visa inställningarna för MDM-säkerhetsbaslinjer som Microsoft Intune stödjer för enheter som kör Windows 10 eller senare. Standardvärdena för inställningarna i den här baslinjen representerar den rekommenderade konfigurationen för tillämpliga enheter. Standardvärden för en baslinje kanske inte matchar standardvärden för andra säkerhetsbaslinjer eller andra versioner av den här baslinjen.

- Mer information om hur du använder säkerhetsbaslinjer med Intune och hur du uppgraderar baslinjeversionen i dina säkerhetsbaslinjeprofiler finns i [Använda säkerhetsbaslinjer](../security-baselines.md).
- Den senaste baslinjeversionen är **Säkerhetsbaslinje för mobilenhetshantering för maj 2019**

Se till att du väljer den version av baslinjen som du vill visa.
<!-- Cookies might be required to enable some browsers to display the zone options -->

::: zone pivot="mdm-may-2019"
**MDM-säkerhetsbaslinje för maj 2019**:  
> [!NOTE]
> I juni 2019 släpptes mallen *Säkerhetsbaslinje för mobilenhetshantering för maj 2019* som allmänt tillgänglig (inte förhandsversion). Den här versionen av säkerhetsbaslinjen ersätter den tidigare baslinjen, *MDM-säkerhetsbaslinje för oktober 2018*.  Profiler som har skapats före maj 2019-baslinjen kommer inte att uppdateras för att avspegla de inställningar och värden som finns i maj 2019-versionen.  Du kan inte skapa nya profiler baserat på förhandsversionsmallen, men du kan redigera och fortsätta att använda profiler som du skapat tidigare som är baserade på förhandsversionsmallen.

Information om vad som har ändrats i den här versionen av baslinjen jämfört med den tidigare versionen finns i [Ändringar i den nya mallen](#whats-changed-in-the-new-template).

::: zone-end
::: zone pivot="mdm-preview"
**Förhandsversion – MDM-säkerhetsbaslinje för oktober 2018**:  
> [!NOTE]
> Det här är förhandsversionen av säkerhetsbaslinjen för mobilenhetshantering, som lanserades i oktober 2018. I juni 2019 ersattes förhandsversionen av mallen *Säkerhetsbaslinje för mobilenhetshantering för maj 2019*, som är allmänt tillgänglig (inte en förhandsversion). Profiler som har skapats innan *Säkerhetsbaslinje för mobilenhetshantering för maj 2019* blev tillgänglig kommer inte att uppdateras för att avspegla de inställningar och värden som finns i MDM-säkerhetsbaslinje för maj 2019. Du kan inte skapa nya profiler baserat på förhandsversionsmallen, men du kan redigera och fortsätta att använda profiler som du skapat tidigare som är baserade på förhandsversionsmallen.

::: zone-end
::: zone pivot="mdm-may-2019,mdm-preview"

## <a name="above-lock"></a>På låsskärmen

Mer information finns i [CSP-princip – AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) i Windows-dokumentationen.  

- **Blockera visning av popupmeddelanden**:  
  Med den här principinställningen kan du förhindra att appmeddelanden visas på låsskärmen. Om du aktiverar den här principinställningen visas inga appmeddelanden på låsskärmen. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användarna välja vilka appar som ska visa aviseringar på låsskärmen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067101)

  **Standard**: Ja

::: zone-end
::: zone pivot="mdm-may-2019"

- **Röstaktivera appar från en låst skärm**:  
  **Standard**: Inaktiverad

::: zone-end
::: zone pivot="mdm-may-2019,mdm-preview"

## <a name="app-runtime"></a>Appkörning

Mer information finns i [CSP – AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime) i Windows-dokumentationen.

- **Microsoft-konton är valfria för Windows Store-appar**:  
  Med den här principinställningen kan du ange om Microsoft-konton är valfria för Windows Store-appar som kräver ett konto för inloggning. Den här principen påverkar bara Windows Store-appar som stöder den. Om du aktiverar den här principinställningen tillåter Windows Store-appar som vanligtvis kräver ett Microsoft-konto för inloggning att användarna loggar in med ett företagskonto i stället. Om du inaktiverar eller inte konfigurerar den här principinställningen måste användarna logga in med ett Microsoft-konto.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067104)
  
  **Standard**: Aktiverad

## <a name="application-management"></a>Programhantering

Mer information finns i [CSP – ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) i Windows-dokumentationen.

::: zone-end
::: zone pivot="mdm-may-2019"

- **Blockera användarkontroll över installationer**:  
  Med den här principinställningen kan användarna ändra installationsalternativ som vanligtvis bara är tillgängliga för systemadministratörer. Om du aktiverar den här principinställningen kringgås vissa av säkerhetsfunktionerna i Windows Installer. Det gör att installationer, som annars skulle stoppas på grund av säkerhetsöverträdelse, kan slutföras. Om du inaktiverar eller inte konfigurerar den här principinställningen kan säkerhetsfunktionerna i Windows Installer hindra användare från att ändra installationsalternativ som vanligtvis är reserverade för systemadministratörer, till exempel att ange vilken katalog som filerna ska installeras i. Om Windows Installer upptäcker att ett installationspaket har tillåtit användaren att ändra ett skyddat alternativ, stoppas installationen och ett meddelande visas. Dessa säkerhetsfunktioner fungerar bara när installationsprogrammet körs i en privilegierad säkerhetskontext där det har åtkomst till kataloger som användaren nekas åtkomst till. Den här principinställningen är utformad för mindre restriktiva miljöer. Den kan användas för att kringgå fel i ett installationsprogram som förhindrar att programvara installeras.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067060)

  **Standard**: Ja

- **Blockera MSI-appinstallationer med utökade privilegier**:  
  Den här policyinställningen säger till Windows Installer att använda förhöjda behörigheter när alla program installeras på systemet.

  - *Om du aktiverar den här principinställningen*utökas behörigheterna till alla program. Dessa behörigheter är vanligtvis reserverade för program som har tilldelats till användaren (erbjuds på skrivbordet), som har tilldelats datorn (har installerats automatiskt) eller som har gjorts tillgängliga i Lägg till eller ta bort program på Kontrollpanelen. Med den här profilinställningen kan användare installera program som kräver åtkomst till kataloger som användaren kanske inte har behörighet att visa eller ändra, inklusive kataloger i starkt begränsade datorer.

  - *Om du inaktiverar eller inte konfigurerar den här principinställningen* tillämpas den aktuella användarens behörighet vid installation av program som en systemadministratör inte distribuerar eller erbjuder. Obs! Den här inställningen visas både i mappen Datorkonfiguration och mappen Användarkonfiguration. För att den här inställningen ska gälla måste du aktivera den i båda mapparna. Varning: Erfarna användare kan dra nytta av de behörigheter som den här policyinställningen ger för att ändra sin behörighet och få permanent åtkomst till begränsade filer och mappar. Det är inte garanterat att användarkonfigurationsversionen av den här principinställningen är säker.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067134)

  **Standard**: Ja

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Blockera spel-DVR (endast skrivbord)** :  
  Konfigurerar om registrering och sändning av spel tillåts.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067056)

  **Standard**: Ja

## <a name="auto-play"></a>Spela upp automatiskt

Mer information finns i [CSP-princip – Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) i Windows-dokumentationen.

- **Spela upp automatiskt – standardbeteende för autorun**:  
  Den här inställningen påverkar standardbeteendet för Autorun-kommandon. Autorun-kommandon lagras i autorun.inf-filer och kan starta installationsprogram eller andra rutiner. När den här inställningen är *aktiverad* kan administratörer ändra standardbeteendet för automatisk körning på en enhet som kör Windows Vista eller senare. Beteendet kan anges till: a) inaktivera autorun-kommandon helt och hållet eller b) återgå till beteendet i äldre operativsystem än Windows Vista och kör autorun-kommandot automatiskt. När den här inställningen är *inaktiverad* eller om den *inte har konfigurerats* frågar enheter som kör Windows Vista eller senare användaren om ett autorun-kommando ska köras.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067133)

  **Standard**: Kör inte

- **Läge för automatisk uppspelning**:  
  Med den här principinställningen kan du inaktivera funktionen Spela upp automatiskt. Funktionen Spela upp automatiskt börjar läsa från en enhet när du sätter in media i enheten. Därför startar installationsfiler för program och musik på ljudmedier direkt. Med Windows XP SP2 och tidigare är funktionen Spela upp automatiskt inaktiverad som standard på flyttbara enheter, till exempel diskettenheten (men inte CD-ROM-enheten) och på nätverksenheter. Från och med Windows XP SP2 är funktionen Spela upp automatiskt aktiverad på flyttbara enheter, inklusive Zip-enheter och vissa USB-lagringsenheter. Om du aktiverar den här principinställningen inaktiveras Spela upp automatiskt på CD-ROM-enheter och flyttbara medieenheter, eller inaktiveras på alla enheter. Den här principinställningen inaktiverar Spela upp automatiskt på fler typer av enheter. Du kan inte använda den här inställningen för att aktivera Spela upp automatiskt på enheter där det är inaktiverat som standard. Om du inaktiverar eller inte konfigurerar den här principinställningen aktiveras Spela upp automatiskt. Obs! Den här inställningen visas både i mappen Datorkonfiguration och mappen Användarkonfiguration. Om principinställningarna står i konflikt med varandra har principinställningen i Datorkonfiguration företräde framför principinställningen i Användarkonfiguration.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2066793)

  **Standard**: Inaktiverad

- **Blockera automatisk uppspelning av andra enheter än volymenheter**:  
  Den här principinställningen tillåter inte automatisk uppspelning av MTP-enheter som exempelvis kameror och telefoner. Om du aktiverar den här principinställningen tillåts inte automatisk uppspelning för MTP-enheter såsom kameror och telefoner. Om du inaktiverar eller inte konfigurerar den här principinställningen aktiveras automatisk uppspelning för andra enheter än volymenheter.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067106)

  **Standard**: Aktiverad

## <a name="bitlocker"></a>BitLocker

Mer information finns i [CSP-princip – Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker) i Windows-dokumentationen.

- **Princip för BitLocker på flyttbara enheter**:  
  Den här inställningen används för att styra krypteringsmetoden och krypteringsstyrkan. Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering. Företag kanske vill styra krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du aktiverar den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara dataenheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om dataenheten används i andra enheter som inte kör Windows 10 version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067140)

  Konfigurera följande inställningar för BitLockers princip för flyttbar enhet:

  - **Kräv kryptering för skrivåtkomst**:  
    **Standard**: Ja

::: zone-end
::: zone pivot="mdm-preview"

- **Princip för BitLocker på flyttbara enheter**:  
  Den här inställningen används för att styra krypteringsmetoden och krypteringsstyrkan. Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering. Företag kanske vill styra krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du aktiverar den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara dataenheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om dataenheten används i andra enheter som inte kör Windows 10 version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067140)

  Konfigurera följande inställningar för BitLockers princip för flyttbar enhet:

  - **Kräv kryptering för skrivåtkomst**:  
    **Standard**: Ja  

  - **Krypteringsmetod**:  
    **Standard**: AES 256-bitars CBC  

- **Princip för BitLocker på fasta enheter**:  
  Den här inställningen används för att styra krypteringsmetoden och krypteringsstyrkan. Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering. Företag kanske vill styra krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du aktiverar den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara dataenheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om dataenheten används i andra enheter som inte kör Windows 10 version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen.

  Konfigurera följande inställningar för BitLockers princip för fasta enheter:

  - **Krypteringsmetod**:  
    **Standard**: AES 256-bitars XTS  

- **Princip för BitLocker på systemenheter**:  
  Den här inställningen används för att styra krypteringsmetoden och krypteringsstyrkan. Värdena för den här principen avgör krypteringsstyrkan som BitLocker använder för kryptering. Företag kanske vill styra krypteringsnivån för ökad säkerhet (AES-256 är starkare än AES-128). Om du aktiverar den här inställningen kan du konfigurera en krypteringsalgoritm och krypteringsstyrkan för nycklar för fasta dataenheter, operativsystemenheter och flyttbara dataenheter separat. För fasta enheter och operativsystemenheter rekommenderar vi att du använder XTS-AES-algoritmen. För flyttbara dataenheter bör du använda AES-CBC 128-bitars eller AES-CBC 256-bitars om dataenheten används i andra enheter som inte kör Windows 10 version 1511 eller senare. Ändringar av krypteringsmetoden har ingen effekt om enheten redan har krypterats eller om kryptering pågår. I dessa fall ignoreras den här principinställningen.

  Konfigurera följande inställningar för BitLockers princip för systemenhet:

  - **Krypteringsmetod**:  
    **Standard**: AES 256-bitars XTS

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="browser"></a>Webbläsare

Mer information finns i [CSP-princip – Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) i Windows-dokumentationen.

- **Kräv SmartScreen för Microsoft Edge**:  
  Microsoft Edge använder som standard Microsoft Defender SmartScreen (aktiverat) för att skydda användarna mot potentiella nätfiskeförsök och skadlig programvara. Som standard kan användarna inte heller inaktivera (stänga av) Microsoft Defender SmartScreen. Om den här principen aktiveras inaktiveras Microsoft Defender SmartScreen och användarna kan inte aktivera funktionen. Konfigurera inte den här principen om du vill att användarna ska kunna aktivera och inaktivera Microsoft Defender SmartScreen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067029)

  **Standard**: Ja

- **Blockera åtkomst till skadliga webbplatser**:  
  Som standard tillåter Microsoft Edge att användarna kringgår (ignorerar) Microsoft Defender SmartScreen-varningar om potentiellt skadliga webbplatser, så att de kan fortsätta till webbplatsen. Med den här principen kan du dock konfigurera Microsoft Edge för att hindra användarna från att kringgå varningar, så att de inte kan fortsätta till webbplatsen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067040)
  
  **Standard**: Ja
  
- **Blockera nedladdning av overifierade filer**:  
  Som standard tillåter Microsoft Edge att användarna kringgår (ignorerar) Microsoft Defender SmartScreen-varningar om potentiellt skadliga filer, så att de kan fortsätta att ladda ned overifierade filer. Om den här principen aktiveras kan användarna inte kringgå varningarna och hindras från att ladda ned overifierade filer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067023)
  
  **Standard**: Ja
  
- **Blockera Lösenordshanteraren**:  
  Som standard använder Microsoft Edge Lösenordshanteraren automatiskt, så att användarna kan hantera lösenord lokalt. Om den här principen inaktiveras kan Microsoft Edge inte använda Lösenordshanteraren. Konfigurera inte den här principen om du vill att användarna ska kunna spara och hantera lösenord lokalt med hjälp av Lösenordshanteraren.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067128)
  
  **Standard**: Ja
  
- **Hindra användare från att åsidosätta certifikatfel**:  
  Den här principinställningen hindrar användaren från att ignorera SSL/TLS-certifikatfel (Secure Sockets Layer/Transport Layer Security) som avbryter surfningen (t.ex. fel av typen ”har upphört att gälla”, ”har återkallats” eller ”namnkonflikt”) i Internet Explorer. Användaren kan inte fortsätta att surfa om du aktiverar den här principinställningen. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren välja att ignorera certifikatfel och fortsätta att surfa.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067126)
  
  **Standard**: Ja

## <a name="connectivity"></a>Anslutningar

Mer information finns i avsnittet [CSP-princip – Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) i Windows-dokumentationen.

- **Blockera nedladdning från Internet för webbpublicerings- och onlinebeställningsguider**:  
  Den här principinställningen anger om Windows ska ladda ned en lista över leverantörer för webbpublicerings- och onlinebeställningsguider. Dessa guider låter användarna välja från en lista över företag som tillhandahåller tjänster, till exempel onlinelagring eller fotoutskrifter. Som standard visar Windows leverantörer som hämtats från en Windows-webbplats och leverantörer som angetts i registret. Om du aktiverar den här principinställningen laddar Windows inte ned leverantörer, och endast de tjänstleverantörer som cachelagras i det lokala registret visas. Om du inaktiverar eller inte konfigurerar den här principinställningen laddas en lista över leverantörer ned när användaren använder webbpublicerings- eller onlinebeställningsguider. Mer information med detaljer om hur du anger leverantörer i registret finns i dokumentationen för webbpublicerings- och onlinebeställningsguiderna.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067136)
  
  **Standard**: Aktiverad

::: zone-end
::: zone pivot="mdm-may-2019"

- **Konfigurera säker åtkomst till UNC-sökvägar**:  
  Den här principinställningen konfigurerar säker åtkomst till UNC-sökvägar. Om du aktiverar principen tillåter Windows endast åtkomst till de UNC-sökvägar som angetts efter att ytterligare säkerhetskrav uppfyllts.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067243)

  **Standard**: Ställ in att Windows bara ska tillåta åtkomst till de angivna UNC-sökvägarna efter att ha uppfyllt ytterligare säkerhetskrav.

  När *Konfigurera Windows till att endast tillåta åtkomst till de UNC-sökvägar som angetts efter att ytterligare säkerhetskrav uppfyllts* har valts kan du konfigurera *listan över härdade UNC-sökvägar*.

  - **Lista över härdade UNC-sökvägar**:  
    Välj **Lägg till** för att ange ytterligare säkerhetsflaggor och serversökvägar.

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Blockera nedladdning av utskriftsdrivrutiner via HTTP**:  
  Den här principinställningen anger om klienten kan ladda ned paket med utskriftsdrivrutiner via HTTP. För att konfigurera HTTP-utskrift måste ”non-inbox”-drivrutiner hämtas via HTTP. Obs! Den här principinställningen hindrar inte klienten från att skriva ut till skrivare i intranätet eller på Internet via HTTP. Den förbjuder endast nedladdningen av drivrutiner som inte redan har installerats lokalt. Om du aktiverar den här principinställningen går det inte att ladda ned utskriftsdrivrutiner via HTTP. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användarna ladda ned utskriftsdrivrutiner via HTTP.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067141)
  
  **Standard**: Aktiverad

## <a name="credentials-delegation"></a>Delegering av autentiseringsuppgifter

Mer information finns i [CSP-princip – CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation) i Windows-dokumentationen.

- **Delegering via fjärrvärd av icke exporterbara autentiseringsuppgifter**:  
  Fjärrvärden tillåter delegering av autentiseringsuppgifter som inte kan exporteras. När du använder delegering av autentiseringsuppgifter, ger enheter en exporteringsbar version av autentiseringsuppgifter till fjärrvärden vilket exponerar användare för risk för stöld av autentiseringsuppgifter från angripare på fjärrdatorn. Om du aktiverar den här principinställningen kan värden använda läget Restricted Admin (Begränsad administration) eller Remote Credential Guard (Fjärrskydd av autentiseringsuppgifter). Om du inaktiverar eller inte konfigurerar den här principinställningen stöds inte läget Restricted Admin (Begränsad administration) eller Remote Credential Guard (Fjärrskydd av autentiseringsuppgifter). Användaren måste alltid skicka sina autentiseringsuppgifter till värden.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067103)
  
  **Standard**: Aktiverad

## <a name="credentials-ui"></a>Användargränssnitt för autentiseringsuppgifter

Mer information finns i [CSP-princip – CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) i Windows-dokumentationen.

- **Räkna upp administratörer**:  
  Den här principinställningen styr om administratörskonton visas när en användare försöker upphöja ett program som körs. Som standard visas inte administratörskonton när användaren försöker upphöja ett program som körs. Om du aktiverar den här principinställningen visas alla lokala administratörskonton på datorn så att användaren kan välja ett och ange rätt lösenord. Om du inaktiverar den här principinställningen måste användaren alltid ange ett användarnamn och lösenord för att upphöja ett program som körs.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067021)

  **Standard**: Inaktiverad

## <a name="data-protection"></a>Dataskydd

Mer information finns i [CSP-princip – DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection) i Windows-dokumentationen.

- **Blockera direkt minnesåtkomst**:  
  Med den här principinställningen kan du blockera direkt minnesåtkomst (DMA) för alla underordnade PCI-portar med hot plug-stöd tills en användare loggar in i Windows. När en användare loggar in räknar Windows upp PCI-enheterna som är anslutna till PCI-portarna med hot plug-stöd. Varje gång användaren låser datorn blockeras DMA på PCI-portarna med hot plug-stöd utan underordnade enheter tills användaren loggar in igen. Enheter som räknades upp när datorn var upplåst fortsätter att fungera tills de kopplas från. Den här principinställningen tillämpas endast när BitLocker- eller enhetskryptering är aktiverat.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067031)

  **Standard**: Ja

## <a name="device-guard"></a>Device Guard

Mer information finns i [CSP-princip – DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard) i Windows-dokumentationen.

- **Credential Guard**:  
  Den här principinställningen tillåter att användarna aktiverar Credential Guard (Autentiseringsskydd) med virtualiseringsbaserad säkerhet för att skydda autentiseringsuppgifterna vid nästa omstart.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067044)

  **Standard**: Aktivera med UEFI-lås

::: zone-end
::: zone pivot="mdm-may-2019"

- **Virtualiseringsbaserad säkerhet**:  
  **Standard**: Aktivera virtualiseringsbaserad säkerhet med säker start

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Aktivera virtualiseringsbaserad säkerhet**:  
  Aktiverar virtualiseringsbaserad säkerhet (VBS) vid nästa omstart. Virtualiseringsbaserad säkerhet använder Windows Hypervisor för att ge stöd för säkerhetstjänster.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067066)
  
  **Standard**: Ja

- **Starta systemskydd**:  
  **Standard**: Aktiverad

## <a name="device-installation"></a>Enhetsinstallation

Mer information finns i [CSP-princip – DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) i Windows-dokumentationen.

- **Installation av maskinvaruenheter efter enhets-ID**:  
  Med den här principinställningen kan du ange en lista med ID:n för Plug and Play-maskinvara och kompatibla ID:n för enheter som Windows hindrar från att installeras. Den här inställningen har företräde framför alla andra principinställningar som tillåter att Windows installerar en enhet. Om du aktiverar den här principinställningen kan Windows inte installera en enhet vars maskinvaru-ID eller kompatibla ID visas i listan som du skapar. Om du aktiverar den här principinställningen på en fjärrskrivbordsserver påverkar principinställningen omdirigeringen av de angivna enheterna från en fjärrskrivbordsklient till fjärrskrivbordsservern. Om du inaktiverar eller inte konfigurerar den här principinställningen kan enheter installera och uppdatera beroende på om de tillåts eller förhindras av andra principinställningar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2066794)

  **Standard**: Blockera installation av maskinvaruenheter

  När *Blockera installation av maskinvaruenheter* är valt, är följande inställningar tillgängliga.

  - **Ta bort matchande maskinvaruenheter**:  
    Den här inställningen är endast tillgänglig när *Hardware device installation by device identifiers* (Installation av maskinvaruenheter efter enhets-ID) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).

    **Standard**: Ja

  - **ID:n för blockerade maskinvaruenheter**:  
    Den här inställningen är endast tillgänglig när *Hardware device installation by device identifiers* (Installation av maskinvaruenheter efter enhets-ID) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).

    **Standard**: Ja

- **Installation av maskinvaruenheter efter installationsklass**:  
  Med den här principinställningen kan du ange en lista med klass-GUID för enhetsinstallation för enhetsdrivrutiner som Windows hindrar från att installeras. Den här inställningen har företräde framför alla andra principinställningar som tillåter att Windows installerar en enhet. Om du aktiverar den här principinställningen kan inte Windows installera eller uppdatera enhetsdrivrutiner vars klass-GUID för enhetsinstallation visas i listan du skapar. Om du aktiverar den här principinställningen på en fjärrskrivbordsserver påverkar principinställningen omdirigeringen av de angivna enheterna från en fjärrskrivbordsklient till fjärrskrivbordsservern. Om du inaktiverar eller inte konfigurerar den här principinställningen kan Windows installera och uppdatera enheter beroende på om de tillåts eller förhindras av andra principinställningar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067048)

  **Standard**: Blockera installation av maskinvaruenheter

  När *Blockera installation av maskinvaruenheter* är valt, är följande inställningar tillgängliga.

  - **Ta bort matchande maskinvaruenheter**:  
    Den här inställningen är endast tillgänglig när *Hardware device installation by setup classes* (Installation av maskinvaruenheter efter installationsklasser) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).

    **Standard**: *Ingen standardkonfiguration*

  - **ID:n för blockerade maskinvaruenheter**:  
    Den här inställningen är endast tillgänglig när *Hardware device installation by setup classes* (Installation av maskinvaruenheter efter installationsklasser) har inställningen *Block hardware device installation* (Blockera installation av maskinvaruenheter).

    **Standard**: *Ingen standardkonfiguration*

## <a name="device-lock"></a>Enhetslås

Mer information finns i [CSP-princip – DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) i Windows-dokumentationen.

- **Förhindra användning av kamera**:  
  Inaktiverar kameraväxlingsreglaget på låsskärmen i Datorinställningar och förhindrar att en kamera anropas på låsskärmen. Som standard kan användare aktivera anrop av en tillgänglig kameran på låsskärmen. Om du aktiverar den här inställningen kan användarna inte längre aktivera eller inaktivera kameraåtkomst på låsskärmen i Datorinställningar, och kameran kan inte anropas på låsskärmen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067052)

  **Standard**: Aktiverad

- **Kräv lösenord**:  
  Anger om enhetslås har aktiverats.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067049)  

  **Standard**: Ja
  
  När *Kräv lösenord* är inställt på *Ja*, är följande inställningar tillgängliga.

  - **Minsta antal tecken för lösenord**:  
    Antalet komplexa elementtyper (versaler och gemener, siffror och skiljetecken) som krävs för en stark PIN-kod eller ett starkt lösenord. För PIN-kod krävs följande för stationära och mobila enheter: 1 – Endast siffror 2 – Siffror och gemener krävs 3 – Siffror, gemener och versaler krävs. Stöds inte med Microsoft-konton för stationära datorer eller domänkonton. 4 – Siffror, gemener, versaler och specialtecken krävs. Stöds inte med stationära datorer.  
    [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067055)

    **Standard**: 3

  - **Antal felaktiga inloggningar innan enheten rensas**:  
    Antal misslyckade autentiseringsförsök som tillåts innan enheten rensas. Värdet 0 inaktiverar enhetsrensningsfunktionen.  
    [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067030)

    **Standard**: 10  

  - **Lösenordets giltighetstid (dagar)** :  
    Principinställningen Högsta ålder för lösenord anger hur länge (i dagar) som ett lösenord kan användas innan systemet kräver att användaren ändrar det. Du kan ange att lösenord upphör att gälla efter ett visst antal dagar mellan 1 och 999, eller ange att lösenorden aldrig upphör att gälla genom att ange antalet dagar till 0. Om den högsta lösenordsåldern är mellan 1 och 999 dagar, måste den minsta lösenordsåldern vara mindre än den högsta lösenordsåldern. Om den högsta lösenordsåldern anges till 0, kan den minsta lösenordsåldern vara ett värde mellan 0 och 998 dagar.  
    [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067028)

    **Standard**: 60

  - **Lösenordstyp som krävs**:  
    Avgör vilken typ av PIN-kod eller lösenord som krävs.  
    [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067027)

    **Standard**: Alfanumerisk

  - **Minsta lösenordslängd**:  
    Inställningen Minsta längd för lösenord avgör det minsta antal tecken som ett lösenord för ett användarkonto måste innehålla. Du kan ange ett värde mellan 1 och 14 tecken, eller ange att inga lösenord krävs genom att ange antalet tecken till 0.  
    [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067024)

    **Standard**: 8

  - **Blockera enkla lösenord**:  
    Anger om PIN-koder eller lösenord, till exempel ”1111” eller ”1234” tillåts. För en stationär dator styr inställningen även användningen av bildlösenord.  
    [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067127)

    **Standard**: Ja  
    *Inställningen Ja förhindrar användningen av enkla lösenord.*

  - **Förhindra återanvändning av tidigare lösenord**:  
    Anger hur många lösenord som kan sparas i historiken och som inte får återanvändas. Värdet inkluderar användarens aktuella lösenord. Till exempel med en inställning på *1* kan användaren inte återanvända deras aktuella lösenord när du väljer ett nytt lösenord. En inställning på *5* innebär att en användare inte kan ange sitt nya lösenord till sitt aktuella lösenord eller något av de fyra tidigare lösenorden.  
    [Läs mer](https://go.microsoft.com/fwlink/?linkid=2066795)

    **Standard**: 24

- **Förhindra bildspel**:  
  Inaktiverar inställningarna för bildspel på låsskärmen i Datorinställningar och förhindrar att ett bildspel spelas upp på låsskärmen. Som standard kan användare aktivera ett bildspel som körs när de låst datorn. Om du aktiverar den här inställningen kan användarna inte ändra inställningarna för bildspel i Datorinställningar och inga bildspel kan starta.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067105)

  **Standard**: Aktiverad  

  *Inställningen Aktiverad förhindrar att bildspel körs.*

- **Minsta ålder för lösenord i dagar**:  
  Inställningen för minsta lösenordsålder anger hur länge (i antal dagar) ett lösenord måste användas innan användaren kan ändra det. Du kan ange ett värde mellan 1 och 998 dagar, eller tillåta lösenordsändringar direkt genom att ange antalet dagar till 0. Den minsta lösenordsåldern måste vara mindre än den högsta lösenordsåldern, såvida inte den högsta lösenordsåldern har angetts till 0, vilket anger att lösenord aldrig upphör att gälla. Om den högsta lösenordsåldern har angetts till 0, kan den lägsta lösenordsåldern anges till valfritt värde mellan 0 och 998.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067022)

  **Standard**: 1

::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="dma-guard"></a>DMA Guard

Mer information finns i [CSP-princip – DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) i Windows-dokumentationen.

- **Uppräkning av externa enheter som är inkompatibla med Kernel DMA-skydd**:  
  Den här principen är avsedd att ge ytterligare skydd mot externa DMA-kompatibla enheter. Det möjliggör större kontroll över uppräkning av externa DMA-kompatibla enheter som inte är kompatibla med minnesisolering och sandbox-miljö för DMA-mappning/-enhet. Den här principen börjar bara gälla när Kernel DMA-skydd stöds och aktiveras av datorns inbyggda programvara. Kernel DMA-skydd är en plattformsfunktion som inte kan styras via en princip eller av slutanvändaren. Den måste stödjas av systemet vid tidpunkten för tillverkning. Om du vill kontrollera om systemet har stöd för kernel DMA-skydd kontrollerar du fältet Kernel DMA-skydd på sammanfattningssidan i MSINFO32.exe.  
  [Läs mer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Standard**: Blockera alla

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="event-log-service"></a>Händelseloggtjänsten

Mer information finns i [CSP-princip – EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) i Windows-dokumentationen.

- **Största filstorlek i kB för säkerhetslogg**:  
  Den här principinställningen anger den högsta storleken för loggfilen i kilobyte. Om du aktiverar den här principinställningen kan du konfigurera den största storleken för loggfilen till mellan 1 megabyte (1 024 kB) och 2 terabyte (2 147 483 647 kilobyte) i steg om en kilobyte. Om du inaktiverar eller inte konfigurerar den här principinställningen används det lokalt konfigurerade värdet som den maximala storleken för loggfilen. Det här värdet kan ändras av den lokala administratören med hjälp av dialogrutan Egenskaper för logg och har som standard värdet 20 MB.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067042)

   **Standard**: 196608

- **Största filstorlek i kB för systemlogg**:  
  Den här principinställningen anger den högsta storleken för loggfilen i kilobyte. Om du aktiverar den här principinställningen kan du konfigurera den största storleken för loggfilen till mellan 1 megabyte (1 024 kB) och 2 terabyte (2 147 483 647 kilobyte) i steg om en kilobyte. Om du inaktiverar eller inte konfigurerar den här principinställningen används det lokalt konfigurerade värdet som den maximala storleken för loggfilen. Det här värdet kan ändras av den lokala administratören med hjälp av dialogrutan Egenskaper för logg och har som standard värdet 20 MB.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2066798)

  **Standard**: 32768

- **Största filstorlek i kB för programlogg**:  
  Den här principinställningen anger den högsta storleken för loggfilen i kilobyte. Om du aktiverar den här principinställningen kan du konfigurera den största storleken för loggfilen till mellan 1 megabyte (1 024 kB) och 2 terabyte (2 147 483 647 kilobyte) i steg om en kilobyte. Om du inaktiverar eller inte konfigurerar den här principinställningen används det lokalt konfigurerade värdet som den maximala storleken för loggfilen. Det här värdet kan ändras av den lokala administratören med hjälp av dialogrutan Egenskaper för logg och har som standard värdet 20 MB.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067125)

  **Standard**: 32768

## <a name="experience"></a>Erfarenhet

Mer information finns i [CSP-princip – Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) i Windows-dokumentationen.

- **Blockera Windows Spotlight**:  
  Tillåter IT-administratörer att inaktivera alla Windows Spotlight-funktioner – Windows Spotlight på låsskärmen, Windows-tips, Microsoft-konsumentfunktioner och liknande funktioner.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067037)

  **Standard**: Ja

  När *Blockera Windows Spotlight* är inställt på *Ja*, är följande inställningar tillgängliga.

  - **Blockera tredjepartsförslag i Windows Spotlight**:  
    Anger om app- och innehållsförslag från utgivare av tredjepartsprogramvara ska tillåtas i Windows Spotlight-funktioner, till exempel låsskärmen, föreslagna appar på Start-menyn och Windows-tips. Användare kan fortfarande se förslag för Microsoft-funktioner, -appar och -tjänster.  
    [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067045)

    **Standard**: Ja

  - **Blockera konsumentspecifika funktioner**:  
    Gör det möjligt för IT-administratörer att aktivera rena konsumentupplevelser, till exempel startförslag, medlemskapsaviseringar, appinstallation efter välkomstprogram (OOBE) och omdirigeringspaneler.  
    [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067054)

    **Standard**: Ja

## <a name="exploit-guard"></a>Sårbarhetsskydd

Mer information finns i [CSP-princip – ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) i Windows-dokumentationen.

- **Ladda upp XML**:  
  Gör det möjligt för IT-administratören att distribuera en konfiguration som representerar önskade system- och programskyddsalternativ till alla enheter i organisationen. Konfigurationen representeras av en XML-sträng. Sårbarhetsskydd hjälper dig att skydda enheter mot skadlig kod som utnyttjar kryphål för att spridas och infektera. Du kan använda Windows Security-appen eller PowerShell för att skapa en uppsättning skyddsåtgärder (kallas en konfiguration). Du kan exportera den här konfigurationen som en XML-fil och dela den med flera datorer i nätverket så att alla har samma uppsättning skyddsåtgärder. Du kan också konvertera och importera en befintlig EMET XML-konfigurationsfil till en XML-konfigurationsfil för sårbarhetsskydd.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067035)

  **Standard**: *En XML-exempelfil finns tillgänglig*

## <a name="file-explorer"></a>Utforskaren

Mer information finns i [CSP-princip – FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) i Windows-dokumentationen.  

- **Blockera dataexekveringsskydd**:  
  Om dataexekveringsskydd inaktiveras kan vissa äldre plugin-program fungera utan att Explorer avslutas.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067043)  

  **Standard**: Inaktiverad

- **Blockera heap-avslutning vid fel**:  
  Om heap-avslutning vid fel inaktiveras kan vissa äldre plugin-program fungera utan att Explorer omedelbart avslutas, även om Explorer fortfarande kan avslutas oväntat senare.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067107)

  **Standard**: Inaktiverad

## <a name="firewall"></a>Brandvägg

Mer information finns i [2.2.2 FW_PROFILE_TYPE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) i dokumentationen för Windows-protokoll.

- **Domän för brandväggsprofil**:  
  Anger de profiler som regeln tillhör: Domän, Privat eller Allmän. Det här värdet representerar profilen för nätverk som är anslutna till domäner.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2066796)

  - **Inkommande anslutningar blockerade**:  
    **Standard**: Ja

  - **Utgående anslutningar krävs**:  
    **Standard**: Ja

  - **Inkommande meddelanden blockerade**:  
    **Standard**: Ja

  - **Brandväggen är aktiverad**:  
    **Standard**: Tillåts

- **Offentlig brandväggsprofil**:  
  Anger de profiler som regeln tillhör: Domän, Privat eller Allmän. Det här värdet representerar profilen för offentliga nätverk. Dessa nätverk klassificeras som offentliga av administratörer i server-värden. Klassificeringen sker första gången värden ansluter till nätverket. Dessa nätverk är vanligtvis på flygplatser eller kaféer och andra offentliga platser där peer-datorer i nätverket eller nätverksadministratörer inte är betrodda.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067143)

  - **Inkommande anslutningar blockerade**:  
    **Standard**: Ja

  - **Utgående anslutningar krävs**:  
    **Standard**: Ja

  - **Inkommande meddelanden blockerade**:  
    **Standard**: Ja

  - **Brandväggen är aktiverad**:  
    **Standard**: Tillåts

  - **Regler för anslutningssäkerhet från inte sammanfogad grupprincip**:  
    **Standard**: Ja

  - **Principregler från inte sammanfogad grupprincip**:  
    **Standard**: Ja

- **Privat brandväggsprofil**:  
  Anger de profiler som regeln tillhör: Domän, Privat eller Allmän. Det här värdet representerar profilen för privata nätverk.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067041)

  - **Inkommande anslutningar blockerade**:  
    **Standard**: Ja

  - **Utgående anslutningar krävs**:  
    **Standard**: Ja

  - **Inkommande meddelanden blockerade**:  
    **Standard**: Ja

  - **Brandväggen är aktiverad**:  
    **Standard**: Tillåts

## <a name="internet-explorer"></a>Internet Explorer

Mer information finns i [CSP-princip – InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) i Windows-dokumentationen.

- **Internet Explorer: uppdateringar av statusfältet via skript i zonen Begränsad**:  
  Med den här principinställningen kan du bestämma om skript ska tillåtas att uppdatera statusfältet i zonen.

  - *Om du aktiverar den här principinställningen* kan skript uppdatera statusfältet.
  - *Om du inaktiverar eller inte konfigurerar den här principinställningen* kan inte skript uppdatera statusfältet.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067074)

  **Standard**: Inaktiverad

::: zone-end
::: zone pivot="mdm-may-2019"

- **Internet Explorer: dra eller kopiera och klistra in filer i zonen Internet**:  
  Med den här principinställningen kan du ange om användarna kan dra filer eller kopiera och klistra in filer från en källa i zonen. Om du aktiverar den här principinställningen kan användarna automatiskt dra filer eller kopiera och klistra in filer från den här zonen. Om du väljer Fråga i listrutan tillfrågas användarna om de vill dra eller kopiera filer från den här zonen. Om du inaktiverar den här principinställningen hindras användarna från att dra filer eller att kopiera och klistra in filer från den här zonen. Om du inte konfigurerar den här principinställningen kan användarna automatiskt dra filer eller kopiera och klistra in filer från den här zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067076)

  **Standard**: Inaktivera

- **Internet Explorer: .NET Framework-beroende komponenter i zonen Begränsad**:  
  Med den här inställningen kan du ange huruvida .NET Framework-komponenter som har signerats med Authenticode kan köras från Internet Explorer. Dessa komponenter är hanterade kontroller som en objekttagg refererar till och hanterade körbara filer som en länk refererar till. Om du aktiverar den här principinställningen kör Internet Explorer osignerade hanterade komponenter. Om du väljer Fråga i listrutan uppmanas användarna att välja om de vill köra osignerade hanterade komponenter i Internet Explorer. Om du inaktiverar den här principinställningen kör Internet Explorer inte osignerade hanterade komponenter. Om du inte konfigurerar den här principinställningen kör Internet Explorer inte osignerade hanterade komponenter.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Standard**: Inaktivera

- **Internet Explorer: kör inte program mot skadlig kod mot Active X-kontroller i zonen Lokal dator**:  
  Den här principinställningen anger om Internet Explorer kör program mot skadlig kod mot ActiveX-kontroller för att se om det är säkert att läsa in dem på sidor. Om du aktiverar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inaktiverar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inte konfigurerar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Användare kan aktivera eller inaktivera det här beteendet med hjälp av säkerhetsinställningarna för Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Standard**: Inaktiverad

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Internet Explorer: åtkomst till data i zonen Internet**:  
  Med den här inställningen kan du ange om Internet Explorer kan komma åt data från en annan säkerhetszon med hjälp av Microsoft XML Parser (MSXML) eller ActiveX Data Objects (ADO). Om du aktiverar den här principinställningen kan användarna läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta inläsningen av en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du inaktiverar den här principinställningen kan användarna inte läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du inte konfigurerar den här principinställningen kan användarna inte läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067078)  

  **Standard**: Inaktivera

- **Internet Explorer: dra innehåll från olika domäner inuti fönster i zonen Begränsad**:  
  Med den här principinställningen kan du ange alternativ för att dra innehåll från en domän till en annan domän när källan och målet finns i samma fönster. Om du aktiverar den här principinställningen och klickar på Aktivera kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i samma fönster. Användarna kan inte ändra denna inställning. Om du aktiverar den här principinställningen och klickar på Inaktivera kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i samma fönster. Användarna kan inte ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 10 kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i samma fönster. Användarna kan ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 9 och tidigare versioner kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra den här inställningen i dialogrutan Internetalternativ.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067079)  

  **Standard**: Inaktiverad

- **Internet Explorer: varning om adressmatchningsfel för certifikat**:  
  Med den här principinställningen kan du aktivera säkerhetsvarningen för adressmatchningsfel för certifikat. När den här inställningen är aktiverad varnas användarna när de besöker webbplatser med säker HTTP (HTTPS) som visar certifikat som utfärdats för en annan webbadress. Den här varningen hjälper till att förhindra förfalskningsattacker. Om du aktiverar den här principinställningen visas alltid varningen om adressmatchningsfel för certifikat. Om du inaktiverar eller inte konfigurerar den här inställningen kan användarna välja om varningen om adressmatchningsfel för certifikat ska visas (visa sidan Avancerat i Internet på Kontrollpanelen).  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067153)  

  **Standard**: Aktiverad

- **Internet Explorer: mindre privilegierade platser i zonen Begränsad**:  
  Med den här principinställningen kan du ange om webbplatser i mindre privilegierade zoner, till exempel webbplatser på Internet, kan navigera till den här zonen. Om du aktiverar den här principinställningen kan webbplatser från mindre privilegierade zoner öppna nya fönster i, eller navigera till, den här zonen. Säkerhetszonen körs utan det ytterligare säkerhetslager som tillhandahålls av säkerhetsfunktionen Skydd mot zonförhöjning. Om du väljer Fråga i listrutan visas en varning för användarna om att potentiellt riskabel navigering snart initieras. Om du inaktiverar den här principinställningen förhindras potentiellt skadlig navigering. Säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på inställningen för funktionen Skydd mot zonförhöjning. Om du inaktiverar den här principinställningen förhindras potentiellt skadlig navigering. Säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på inställningen för funktionen Skydd mot zonförhöjning.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067148)

  **Standard**: Inaktivera

- **Internet Explorer: automatisk fråga om filnedladdning i zonen Begränsad**:  
  Den här principinställningen anger huruvida användarna tillfrågas innan en filnedladdning som inte har initierats av användaren inleds. Oavsett den här inställningen visas dialogrutor för filnedladdning vid användarinitierade nedladdningar. Om du aktiverar den här inställningen visas en dialogruta för filnedladdning vid automatiska nedladdningsförsök. Om du inaktiverar eller inte konfigurerar den här inställningen blockeras filnedladdningar som inte har initierats av användaren, och användaren ser meddelandefältet i stället för dialogrutan för filnedladdning. Användare kan sedan klicka på meddelandefältet för att tillåta filhämtningen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067150)

  **Standard**: Inaktiverad

- **Internet Explorer: .NET Framework-beroende komponenter i zonen Internet**:  
  Med den här inställningen kan du ange huruvida .NET Framework-komponenter som har signerats med Authenticode kan köras från Internet Explorer. Dessa komponenter är hanterade kontroller som en objekttagg refererar till och hanterade körbara filer som en länk refererar till. Om du aktiverar den här principinställningen kör Internet Explorer osignerade hanterade komponenter. Om du väljer Fråga i listrutan uppmanas användarna att välja om de vill köra osignerade hanterade komponenter i Internet Explorer. Om du inaktiverar den här principinställningen kör Internet Explorer inte osignerade hanterade komponenter. Om du inte konfigurerar den här principinställningen kör Internet Explorer osignerade hanterade komponenter.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067073)

  **Standard**: Inaktivera

- **Internet Explorer: tillåt endast att godkända domäner använder TDC ActiveX-kontroller i zonen Internet**:  
  Den här principinställningen styr om användaren kan köra TDC ActiveX-kontrollen på webbplatser. Om du aktiverar den här principinställningen körs inte TDC ActiveX-kontrollen från webbplatser i den här zonen. Om du inaktiverar den här principinställningen körs TDC ActiveX-kontrollen från alla platser i den här zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067151)

  **Standard**: Aktiverad

- **Internet Explorer: skriptinitierade fönster i zonen Begränsad**:  
  Med den här principinställningen kan du hantera begränsningar för skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet. Om du aktiverar den här principinställningen gäller inte begränsningar för Windows-säkerhet i den här zonen. Säkerhetszonen körs utan det ytterligare säkerhetslager som tillhandahålls av den här funktionen. Om du inaktiverar den här principinställningen kan inte de potentiellt skadliga åtgärderna i skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet köras. Den här säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på kontrollinställningen för skriptinitierade säkerhetsbegränsningar för Windows. Om du inte konfigurerar den här principinställningen kan inte de potentiellt skadliga åtgärderna i skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet köras. Den här säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på kontrollinställningen för skriptinitierade säkerhetsbegränsningar för Windows.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067075)

  **Standard**: Inaktiverad

- **Internet Explorer: ta med lokal sökväg när filer laddas upp till servern i zonen Internet**:  
  Den här principinställningen styr huruvida information om den lokala sökvägen skickas när användaren laddar upp en fil via ett HTML-formulär. Om information om den lokala sökvägen skickas kan servern oavsiktligt få tillgång till viss information. Filer som skickas från användarens dator kan exempelvis innehålla användarnamnet som en del av sökvägen. Om du aktiverar den här principinställningen skickas information om sökvägen när användaren överför en fil via ett HTML-formulär. Om du inaktiverar den här principinställningen tas information om sökvägen bort när användaren överför en fil via ett HTML-formulär. Om du inte konfigurerar den här principinställningen kan användarna välja om sökvägsinformation skickas när de laddar upp en fil via ett HTML-formulär. Sökvägsinformation skickas som standard.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067072)

  **Standard**: Inaktiverad

- **Internet Explorer: inaktivera processer i utökat skyddat läge**:  
  Den här principinställningen anger om Internet Explorer 11 använder 64-bitarsprocesser (för högre säkerhet) eller 32-bitarsprocesser (för bättre kompatibilitet) när programmet körs i utökat skyddat läge i 64-bitarsversioner av Windows. Viktigt! Vissa ActiveX-kontroller och -verktygsfält kanske inte är tillgängliga när 64-bitarsprocesser används. Om du aktiverar den här principinställningen använder Internet Explorer 11 64-bitarsprocesser i utökat skyddat läge i 64-bitarsversioner av Windows. Om du inaktiverar den här principinställningen använder Internet Explorer 11 32-bitarsprocesser i utökat skyddat läge i 64-bitarsversioner av Windows. Om du inte konfigurerar den här principinställningen kan användarna aktivera eller inaktivera den här funktionen via Internet Explorer-inställningarna. Den här funktionen är inaktiverad som standard.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067149)

  **Standard**: Aktiverad

- **Internet Explorer: ignorera certifikatfel**:  
  Den här principinställningen hindrar användaren från att ignorera SSL/TLS-certifikatfel (Secure Sockets Layer/Transport Layer Security) som avbryter surfningen (t.ex. fel av typen ”har upphört att gälla”, ”har återkallats” eller ”namnkonflikt”) i Internet Explorer. Användaren kan inte fortsätta att surfa om du aktiverar den här principinställningen. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren ignorera certifikatfel och fortsätta att surfa.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067071)

  **Standard**: Inaktiverad

- **Internet Explorer: inläsning av XAML-filer i zonen Internet**:  
  Med den här principinställningen kan du hantera inläsningen av XAML-filer (Extensible Application Markup Language). XAML är ett XML-baserat deklarativt märkspråk som ofta används för att skapa mångsidiga användargränssnitt och grafik som utnyttjar Windows Presentation Foundation. Om du aktiverar den här inställningen och väljer Aktivera i listrutan läses XAML-filer in automatiskt i Internet Explorer. Användaren kan inte ändra det här beteendet. Om du väljer Fråga i listrutan tillfrågas användaren innan XAML-filerna läses in. Om du inaktiverar den här principinställningen läses XAML-filer inte in i Internet Explorer. Användaren kan inte ändra det här beteendet. Om du inte konfigurerar den här principinställningen kan användaren bestämma huruvida XAML-filerna ska läsas in i Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067147)

  **Standard**: Inaktivera

::: zone-end
::: zone pivot="mdm-may-2019"

- **Internet Explorer: automatisk fråga om filnedladdning i zonen Internet**:  
  Den här principinställningen anger huruvida användarna tillfrågas innan en filnedladdning som inte har initierats av användaren inleds. Oavsett den här inställningen visas dialogrutor för filnedladdning vid användarinitierade nedladdningar. Om du aktiverar den här inställningen visas en dialogruta för filnedladdning vid automatiska nedladdningsförsök. Om du inaktiverar eller inte konfigurerar den här inställningen blockeras filnedladdningar som inte har initierats av användaren, och användaren ser meddelandefältet i stället för dialogrutan för filnedladdning. Användare kan sedan klicka på meddelandefältet för att tillåta filhämtningen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067117)

  **Standard**: Inaktiverad

::: zone-end
::: zone pivot="mdm-preview"

- **Internet Explorer: automatisk fråga om filnedladdning i zonen Internet**:  
  Den här principinställningen anger huruvida användarna tillfrågas innan en filnedladdning som inte har initierats av användaren inleds. Oavsett den här inställningen visas dialogrutor för filnedladdning vid användarinitierade nedladdningar. Om du aktiverar den här inställningen visas en dialogruta för filnedladdning vid automatiska nedladdningsförsök. Om du inaktiverar eller inte konfigurerar den här inställningen blockeras filnedladdningar som inte har initierats av användaren, och användaren ser meddelandefältet i stället för dialogrutan för filnedladdning. Användare kan sedan klicka på meddelandefältet för att tillåta filhämtningen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067117)

  **Standard**: Aktiverad

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Internet Explorer: säkerhetsvarning om potentiellt skadliga filer i zonen Begränsad**:  
  Den här principinställningen styr huruvida meddelandet ”Öppna fil – säkerhetsvarning” visas när användaren försöker öppna körbara filer eller andra potentiellt skadliga filer (till exempel från en filresurs i intranätet med hjälp av Utforskaren). Om du aktiverar den här principinställningen och väljer Aktivera i listrutan öppnas dessa filer utan någon säkerhetsvarning. Om du väljer Fråga i listrutan visas en säkerhetsvarning innan filerna öppnas. Om du inaktiverar den här principinställningen öppnas inte dessa filer. Om du inte konfigurerar den här principinställningen kan användaren konfigurera hur datorn hanterar dessa. Som standard blockeras dessa filer i zonen Begränsad, tillåts i zonerna Intranät och Lokal dator och har inställningen Fråga i zonerna Internet och Betrodda platser.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2066797)

  **Standard**: Inaktivera

- **Internet Explorer: XSS-filter i zonen Internet**:  
  Den här principen styr huruvida XSS-filtret (Cross Site-Scripting) identifierar och förhindrar XSS-inmatningar till webbplatser i den här zonen. Om du aktiverar den här principinställningen aktiveras XSS-filtret för platser i den här zonen och XSS-filtret försöker blockera XSS-inmatningar. Om du inaktiverar den här principinställningen inaktiveras XSS-filtret för platser i den här zonen och Internet Explorer tillåter XSS-inmatningar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067053)

  **Standard**: Aktiverad

- **Internet Explorer-återställning till SSL3**:  
  Med den här principinställningen kan du blockera en osäker återställning till SSL 3.0. När den här principen är aktiverad försöker Internet Explorer ansluta till platser med hjälp av SSL 3.0 eller lägre om TLS 1.0 eller senare misslyckas. Vi rekommenderar att du inte tillåter osäker återställning för att förhindra en man-i-mitten-attack. Den här principen påverkar inte vilka säkerhetsprotokoll som aktiveras. Om du inaktiverar den här principen används standardvärdena för systemet.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067118)

  **Standard**: Inga platser

::: zone-end
::: zone pivot="mdm-may-2019"

- **Krypteringsstöd för Internet Explorer**:  
  Med den här principinställningen kan du inaktivera stöd för Transport Layer Security (TLS) 1.0, TLS 1.1, TLS 1.2, Secure Sockets Layer (SSL) 2.0 eller SSL 3.0 i webbläsaren. TLS och SSL är protokoll som skyddar kommunikationen mellan webbläsaren och målservern. När webbläsaren försöker skapa en säker anslutning till målservern kommer webbläsaren och servern att förhandla om vilket protokoll och vilken version de ska använda. Webbläsaren och servern försöker matcha varandras listor över protokoll och versioner som stöds och väljer den bästa matchningen. Om du aktiverar den här principinställningen kommer webbläsaren att förhandla eller inte förhandla om en krypteringstunnel med hjälp av de krypteringsmetoder som du väljer i listrutan. Om du inaktiverar eller låter bli att konfigurera den här principinställningen kan användaren välja vilken krypteringsmetod som ska stödjas av webbläsaren.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Standard**: 2 objekt:  TLS v1.1 och TLS v1.2  
  *Välj nedpilen för att visa de alternativ som du kan välja för den här inställningen.*

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Internet Explorer: låst SmartScreen i zonen Internet**:  
  Den här principinställningen styr huruvida SmartScreen-filtret söker igenom sidor i den här zonen och letar efter skadligt innehåll. Om du aktiverar den här principinställningen söker SmartScreen-filtret igenom sidor i den här zonen och letar efter skadligt innehåll. Om du inaktiverar den här principinställningen söker SmartScreen-filtret inte igenom sidor i den här zonen för att leta efter skadligt innehåll. Om du inte konfigurerar den här principinställningen kan användaren välja huruvida SmartScreen-filtret ska söka igenom sidor i den här zonen och leta efter skadligt innehåll. Obs! I Internet Explorer 7 styr den här principinställningen om nätfiskefiltret söker igenom sidor i den här zonen och letar efter skadligt innehåll.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067059)

  **Standard**: Aktiverad

- **Internet Explorer: starta program och filer i en iFrame i zonen Begränsad**:  
  Med den här principinställningen kan du ange om program kan köras och om filer kan laddas ned från en IFRAME-referens i HTML-koden för sidorna i den här zonen. Om du aktiverar den här principinställningen kan användarna köra program och ladda ned filer från en IFRAME på sidorna i den här zonen utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill köra program och ladda ned filer från en IFRAME på sidorna i den här zonen. Om du inaktiverar den här principinställningen kan användarna inte köra program och ladda ned filer från en IFRAME på sidorna i den här zonen. Om du inte konfigurerar den här principinställningen kan användarna inte köra program och ladda ned filer från en IFRAME på sidorna i den här zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067061)

  **Standard**: Inaktivera

- **Internet Explorer: kringgå SmartScreen-varningar om ovanliga filer**:  
  Den här principinställningen anger om användaren kan kringgå varningar från SmartScreen-filtret. SmartScreen-filtret varnar användaren om körbara filer som Internet Explorer-användare vanligtvis inte laddar ned från Internet. Om du aktiverar den här principinställningen blockerar SmartScreen-filtret användaren. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren kringgå varningar från SmartScreen-filtret.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067068)

  **Standard**: Inaktiverad

- **Internet Explorer: blockera popup-fönster i zonen Internet**:  
  Med den här principinställningen kan du ange om oönskade popup-fönster ska visas eller inte. Popup-fönster som öppnas när slutanvändaren klickar på en länk blockeras inte. Om du aktiverar den här principinställningen hindras de flesta oönskade popup-fönster från att visas. Om du inaktiverar den här principinställningen hindras inte popup-fönster från att visas. Om du inte konfigurerar den här principinställningen hindras de flesta oönskade popup-fönster från att visas.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067069)

  **Standard**: Aktivera

- **Internet Explorer: konsekvent MIME-hantering av processer**:  
  Internet Explorer innehåller dynamiska binära beteenden: komponenter som kapslar in specifika funktioner för HTML-elementen som de är kopplade till. Den här inställningen styr huruvida inställningen Säkerhetsbegränsning för uppföranden i binärkod ska tillåtas eller blockeras. Om du aktiverar den här principinställningen förhindras binära beteenden för processer relaterade till Utforskaren och Internet Explorer. Om du inaktiverar den här principinställningen tillåts binära beteenden för processer relaterade till Utforskaren och Internet Explorer. Om du inte konfigurerar den här principinställningen förhindras binära beteenden för processer relaterade till Utforskaren och Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067144)  

  **Standard**: Aktiverad

- **Internet Explorer: Java-behörigheter i begränsad plats**:  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop) samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067132)

  **Standard**: Inaktivera Java

- **Internet Explorer: Active X-kontroller i skyddat läge**:  
  Den här principinställningen förhindrar att ActiveX-kontroller körs i skyddat läge när utökat skyddat läge är aktiverat. När en användare har en ActiveX-kontroll installerad som inte är kompatibel med utökat skyddat läge och en webbplats försöker läsa in kontrollen, meddelar Internet Explorer användaren om detta och ger möjlighet att köra webbplatsen i det vanliga skyddade läget. Den här inställningen inaktiverar det här meddelandet och tvingar alla webbplatser att köras i utökat skyddat läge. Utökat skyddat läge ger ytterligare skydd mot skadliga webbplatser genom att använda 64-bitarsprocesser i 64-bitarsversioner av Windows. För datorer som kör minst Windows 8 begränsar utökat skyddat läge också vilka platser Internet Explorer kan läsa från i registret och filsystemet. När utökat skyddat läge är aktiverat och en användare påträffar en webbplats som försöker läsa in en ActiveX-kontroll som inte är kompatibel med utökat skyddat läge, meddelar Internet Explorer användaren och ger möjlighet att inaktivera utökat skyddat läge för den specifika webbplatsen. Om du aktiverar den här principinställningen ger Internet Explorer inte användaren möjlighet att inaktivera utökat skyddat läge. Alla webbplatser i skyddat läge körs i utökat skyddat läge. Om du inaktiverar eller inte konfigurerar den här principinställningen meddelar Internet Explorer användaren, som ges möjlighet att köra webbplatser med inkompatibla ActiveX-kontroller i det vanliga skyddade läget.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067145)

  **Standard**: Inaktiverad

- **Internet Explorer: inläsning av XAML-filer i zonen Begränsad**:  
  Med den här principinställningen kan du hantera inläsningen av XAML-filer (Extensible Application Markup Language). XAML är ett XML-baserat deklarativt märkspråk som ofta används för att skapa mångsidiga användargränssnitt och grafik som utnyttjar Windows Presentation Foundation. Om du aktiverar den här inställningen och väljer Aktivera i listrutan läses XAML-filer in automatiskt i Internet Explorer. Användaren kan inte ändra det här beteendet. Om du väljer Fråga i listrutan tillfrågas användaren innan XAML-filerna läses in. Om du inaktiverar den här principinställningen läses XAML-filer inte in i Internet Explorer. Användaren kan inte ändra det här beteendet. Om du inte konfigurerar den här principinställningen kan användaren bestämma huruvida XAML-filerna ska läsas in i Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067070)

  **Standard**: Inaktivera

- **Internet Explorer: hantering av skriptbegränsningar för fönstersäkerhet**:  
  Internet Explorer tillåter att skript öppnar, ändrar storlek på och flyttar olika typer av fönster via programmering. Säkerhetsfunktionen för fönsterbegränsningar begränsar popup-fönster och hindrar skript från att visa fönster där namnlisten och statusfältet inte visas för användaren eller som förvränger andra namnlister eller statusfält i Windows. Om du aktiverar den här principinställningen begränsas skriptbaserade fönster för alla processer. Om du inaktiverar eller inte konfigurerar den här principinställningen begränsas inte skriptbaserade fönster.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067146)

  **Standard**: Aktiverad

- **Internet Explorer: kör Active X-kontroller och plugin-program i zonen Begränsad**:  
  Med den här principinställningen kan du ange huruvida ActiveX-kontroller och plugin-program kan köras på sidor från den angivna zonen. Om du aktiverar den här principinställningen kan kontroller och plugin-program köras utan inblandning av användaren. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontroller eller plugin-programmet körs. Om du inaktiverar den här principinställningen hindras kontroller och plugin-program från att köras. Om du inte konfigurerar den här principinställningen hindras kontroller och plugin-program från att köras.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067114)

  **Standard**: Inaktivera

- **Internet Explorer: Active X-kontroller markerade som säkra för skriptkörning i zonen Begränsad**:  
  Med den här principinställningen kan du ange om en ActiveX-kontroll som markerats som säker för skriptkörning kan interagera med ett skript. Om du aktiverar den här principinställningen kan interaktion med skript ske automatiskt utan inblandning av användaren. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta interaktion med skript. Om du inaktiverar den här principinställningen förhindras interaktion med skript. Om du inte konfigurerar den här inställningen förhindras interaktion med skript.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067062)

  **Standard**: Inaktivera

- **Internet Explorer: inloggningsalternativ i zonen Begränsad**:  
  Med den här principinställningen kan du hantera inställningar för inloggningsalternativ. Om du aktiverar den här principinställningen kan du välja något av följande inloggningsalternativ.

  - *Anonym* – Använd anonym inloggning om du vill inaktivera HTTP-autentisering och använda gästkontot endast för CIFS-protokollet (Common Internet File System).

  - *Fråga* – Använd en fråga efter användarnamn och lösenord om du vill uppmana användare att ange användar-ID:n och lösenord. När en användare har angett värdena kan de användas tyst i bakgrunden under resten av sessionen.

  - *Automatisk inloggning endast i zonen Intranät* – Använd det här alternativet om du vill uppmana användaren att ange användar-ID:n och lösenord i andra zoner. När en användare har angett värdena kan de användas tyst i bakgrunden under resten av sessionen.

  - *Automatisk inloggning med aktuellt användarnamn och lösenord* – Använd det här alternativet för att försöka logga in med Windows NT Challenge Response (även kallat NTLM-autentisering). Om servern har stöd för Windows NT Challenge Response används användarens användarnamn och lösenord för nätverket vid inloggningen. Om servern inte stöder Windows NT Challenge Response uppmanas användaren att ange användarnamnet och lösenordet.

  Om du inaktiverar den här principinställningen anges inloggningen till *Automatisk inloggning endast i Intranät-zonen*. Om du inte konfigurerar den här principen anges inloggningen till att *Fråga* efter användarnamn och lösenord.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067110)

  **Standard**: Anonym

- **Internet Explorer: initiera och kör skript för Active X-kontroller som inte markerats som säkra i zonen Betrodda platser**:  
  Med den här principinställningen kan du hantera ActiveX-kontroller som inte har markerats som säkra. Om du aktiverar den här principinställningen körs ActiveX-kontroller, initieras med parametrar och körs med skript utan att objektsäkerhet anges för obetrodda data eller skript. Den här inställningen rekommenderas inte, förutom för säkra och administrerade zoner. Den här inställningen gör att både osäkra och säkra kontroller initieras och körs med skript, samtidigt som ActiveX-skriptkontrollerna som markerats som säkra i skriptalternativet ignoreras. Om du aktiverar den här principinställningen och väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontrollen initieras med parametrar eller körs med skript. Om du inaktiverar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar, och de körs inte med skript. Om du inte konfigurerar den här principen tillfrågas användarna om de vill tillåta att kontrollen startas med parametrar eller körs med skript.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067137)

  **Standard**: Inaktivera

- **Internet Explorer: kontrollera återkallelsestatus för servercertifikat**:  
  Med den här principinställningen kan du ange om Internet Explorer ska kontrollera återkallelsestatusen för servercertifikat. Certifikat återkallas när de komprometteras eller inte längre är giltiga, och det här alternativet hindrar användarna från att skicka känsliga data till en webbplats som kan vara bedräglig eller inte säker. Om du aktiverar den här principinställningen kontrollerar Internet Explorer om servercertifikat har återkallats. Om du inaktiverar den här principinställningen kontrollerar Internet Explorer inte om servercertifikat har återkallats. Om du inte konfigurerar den här principinställningen kontrollerar Internet Explorer inte om servercertifikat har återkallats.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067046)

  **Standard**: Aktiverad

- **Internet Explorer: mindre privilegierade platser i zonen Internet**:  
  Med den här principinställningen kan du ange om webbplatser i mindre privilegierade zoner, till exempel Begränsade platser, kan navigera till den här zonen. Om du aktiverar den här principinställningen kan webbplatser från mindre privilegierade zoner öppna nya fönster i, eller navigera till, den här zonen. Säkerhetszonen körs utan det ytterligare säkerhetslager som tillhandahålls av säkerhetsfunktionen Skydd mot zonförhöjning. Om du väljer Fråga i listrutan visas en varning för användarna om att potentiellt riskabel navigering snart initieras. Om du inaktiverar den här principinställningen förhindras potentiellt skadlig navigering. Säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på inställningen för funktionen Skydd mot zonförhöjning. Om du inte konfigurerar den här principinställningen kan webbplatser från mindre privilegierade zoner öppna nya fönster i, eller navigera till, den här zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067109)

  **Standard**: Inaktivera

- **Internet Explorer: filhämtningar i zonen Begränsad**:  
  Med den här principinställningen kan du ange om filhämtningar ska tillåtas från zonen. Det här alternativet bestäms av zonen på sidan med länken för nedladdningen, inte den zon som filen levereras från. Om du aktiverar den här principinställningen kan filerna laddas ned från zonen. Om du inaktiverar den här inställningen kan inte filer laddas ned från zonen. Om du inte konfigurerar den här principinställningen kan inte filer laddas ned från zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067038)

  **Standard**: Inaktivera

- **Internet Explorer: kör .NET Framework-beroende komponenter som har signerats med Authenticode i zonen Internet**:  
  Med den här inställningen kan du ange om .NET Framework-komponenter som har signerats med Authenticode kan köras från Internet Explorer. Dessa komponenter är hanterade kontroller som en objekttagg refererar till och hanterade körbara filer som en länk refererar till. Om du aktiverar den här principinställningen kör Internet Explorer signerade hanterade komponenter. Om du väljer Fråga i listrutan uppmanas användarna att välja om de vill köra signerade hanterade komponenter i Internet Explorer. Om du inaktiverar den här principinställningen kör Internet Explorer inte osignerade hanterade komponenter. Om du inte konfigurerar den här principinställningen kör Internet Explorer inte osignerade hanterade komponenter.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067033)

  **Standard**: Inaktivera

- **Internet Explorer: förhindra installation av Active X-kontroller per användare**:  
  Med den här principinställningen kan du förhindra installationen av ActiveX-kontroller separat för varje enskild användare. Om du aktiverar den här principinställningen kan ActiveX-kontroller inte installeras per användare. Om du inaktiverar eller inte konfigurerar den här principinställningen kan ActiveX-kontroller installeras per användare.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067058)

  **Standard**: Aktiverad

- **Internet Explorer: förhindra hantering av SmartScreen-filtret**:  
  Den här inställningen hindrar användarna från att hantera SmartScreen-filtret, som varnar användarna om den webbplats som de besöker är känd för att försöka samla in personlig information via ”nätfiske” eller är känd för att innehålla skadlig kod. Om du aktiverar den här principinställningen uppmanas användaren inte om att aktivera SmartScreen-filtret. Alla webbplatsadresser som inte finns med på filtrets lista för tillåtna webbplatser skickas automatiskt till Microsoft utan att fråga användaren. Om du inaktiverar eller inte konfigurerar den här principinställningen uppmanas användarna att bestämma om de vill aktivera SmartScreen-filtret vid första körningen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067135)

  **Standard**: Aktivera

- **Internet Explorer-processer: säkerhetsfunktionen MIME-kontroll**:  
  Den här principinställningen anger om funktionen MIME-kontroll i Internet Explorer ska förhindra upphöjning av en fil av en typ till en farligare filtyp. Om du aktiverar den här principinställningen upphöjer funktionen MIME-kontroll aldrig en fil av en typ till en farligare filtyp. Om du inaktiverar den här principinställningen kan Internet Explorer-processer tillåta att MIME-kontroll höjer upp en fil av en typ till en farligare filtyp. Om du inte konfigurerar den här principen upphöjer MIME-kontroll aldrig en fil av en typ till en farligare filtyp.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067124)

  **Standard**: Aktiverad

- **Internet Explorer: ladda ned signerade Active X-kontroller i zonen Begränsad**:  
  Med den här principinställningen kan du bestämma om användare kan ladda ned signerade ActiveX-kontroller från en sida i zonen. Om du aktiverar den här principen kan användarna ladda ned signerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill hämta kontroller som signerats av utfärdare som inte är betrodda. Kod som signerats av betrodda utfärdare hämtas i bakgrunden. Om du inaktiverar den här inställningen kan inte signerade kontroller laddas ned. Om du inte konfigurerar den här principinställningen tillfrågas användarna om de vill ladda ned kontroller som signerats av utfärdare som inte är betrodda. Kod som signerats av betrodda utfärdare hämtas i bakgrunden.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067120)

  **Standard**: Inaktivera

- **Internet Explorer: automatisk komplettering**:  
  Funktionen Komplettera automatiskt kan komma ihåg och föreslå användarnamn och lösenord för formulär. Om du aktiverar den här inställningen kan användarna inte ändra ”Användarnamn och lösenord i formulär” eller ”Fråga mig om jag vill spara lösenord”. Funktionen Komplettera automatiskt för användarnamn och lösenord för formulär aktiveras. Ange om det ska gå att spara lösenord. Om du inaktiverar den här inställningen kan användarna inte ändra ”Användarnamn och lösenord i formulär” eller ”Fråga mig om jag vill spara lösenord”. Funktionen Komplettera automatiskt för användarnamn och lösenord för formulär inaktiveras. Användarna kan inte heller välja om de vill tillfrågas om att spara lösenord. Om du inte konfigurerar den här inställningen kan användarna välja att aktivera Komplettera automatiskt för användarnamn och lösenord för formulär och välja att bli tillfrågade om de vill spara lösenord. För att visa det här alternativet öppnar användarna dialogrutan Internetalternativ, klickar på fliken Innehåll och sedan på knappen Inställningar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067122)

  **Standard**: Inaktiverad

- **Internet Explorer: tillåt att VBscript-körs i zonen Internet**:  
  Med den här inställningen kan du välja om VBScript kan köras på sidor i specifika Internet Explorer-zoner. Alternativen är:

  - *Aktivera* – VBScript körs på sidor i specifika zoner, utan manuella användaråtgärder.

  - *Fråga* – Medarbetare tillfrågas om de vill tillåta att VBScript körs i zonen.

  - *Inaktivera* – VBScript förhindras att köra i zonen. Om du inaktiverar eller inte konfigurerar den här principinställningen körs VBScript utan inblandning av användaren i den angivna zonen.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067119)

  **Standard**: Inaktivera

- **Internet Explorer: tillåt endast att godkända domäner använder TDC Active X-kontroller i zonen Begränsad**:  
  Den här principinställningen styr om användaren kan köra TDC ActiveX-kontrollen på webbplatser. Om du aktiverar den här principinställningen körs inte TDC ActiveX-kontrollen från webbplatser i den här zonen. Om du inaktiverar den här principinställningen körs TDC ActiveX-kontrollen från alla platser i den här zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067032)

  **Standard**: Aktiverad

- **Internet Explorer-betrodda zoner kör inte program mot skadlig kod mot Active X-kontroller**:  
  Den här principinställningen anger om Internet Explorer kör program mot skadlig kod mot ActiveX-kontroller för att se om det är säkert att läsa in dem på sidor. Om du aktiverar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inaktiverar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inte konfigurerar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Användare kan aktivera eller inaktivera det här beteendet med hjälp av säkerhetsinställningarna för Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067115)

  **Standard**: Inaktiverad

- **Internet Explorer: Java-behörigheter i zonen Lokal dator**:  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop) samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen ställs behörigheten in på Normal säkerhet.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067113)

  **Standard**: Inaktivera Java

- **Internet Explorer: kör inte program mot skadlig kod mot Active X-kontroller i zonen Intranät**:  
  Den här principinställningen anger om Internet Explorer kör program mot skadlig kod mot ActiveX-kontroller för att se om det är säkert att läsa in dem på sidor. Om du aktiverar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inaktiverar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inte konfigurerar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Användare kan aktivera eller inaktivera det här beteendet med hjälp av säkerhetsinställningarna för Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067138)

  **Standard**: Inaktiverad

- **Internet Explorer: skriptlet i zonen Begränsad**:  
  Med den här principinställningen kan du ange om användaren kan köra skriptlet. Om du aktiverar den här principinställningen kan användaren köra skriptlet. Om du inaktiverar den här principinställningen kan användaren inte köra skriptlet. Om du inte konfigurerar den här principinställningen kan användaren aktivera eller inaktivera skriptlet.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067112)

  **Standard**: Inaktiverad

- **Internet Explorer-processer: meddelandefältet**:  
  Med den här inställningen kan du ange om meddelandefältet ska visas i Internet Explorer-processer när fil- eller kodinstallationer begränsas. Som standard visas meddelandefältet i Internet Explorer-processer. Om du aktiverar den här principinställningen visas meddelandefältet för Internet Explorer-processerna. Om du inaktiverar den här principinställningen visas inte meddelandefältet för Internet Explorer-processerna. Om du inte konfigurerar den här principinställningen visas inte meddelandefältet för Internet Explorer-processerna.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067139)

  **Standard**: Aktiverad

- **Internet Explorer: ladda ned signerade ActiveX-kontroller i zonen Internet**:  
  Med den här principinställningen kan du bestämma om användare kan ladda ned signerade ActiveX-kontroller från en sida i zonen. Om du aktiverar den här principen kan användarna ladda ned signerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill hämta kontroller som signerats av utfärdare som inte är betrodda. Kod som signerats av betrodda utfärdare hämtas i bakgrunden. Om du inaktiverar den här inställningen kan inte signerade kontroller laddas ned. Om du inte konfigurerar den här principinställningen tillfrågas användarna om de vill ladda ned kontroller som signerats av utfärdare som inte är betrodda. Kod som signerats av betrodda utfärdare hämtas i bakgrunden.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067064)

  **Standard**: Inaktivera

- **Internet Explorer: SmartScreen i zonen Begränsad**:  
  Den här principinställningen styr huruvida SmartScreen-filtret söker igenom sidor i den här zonen och letar efter skadligt innehåll. Om du aktiverar den här principinställningen söker SmartScreen-filtret igenom sidor i den här zonen och letar efter skadligt innehåll. Om du inaktiverar den här principinställningen söker SmartScreen-filtret inte igenom sidor i den här zonen för att leta efter skadligt innehåll. Om du inte konfigurerar den här principinställningen kan användaren välja huruvida SmartScreen-filtret ska söka igenom sidor i den här zonen och leta efter skadligt innehåll. Obs! I Internet Explorer 7 styr den här principinställningen om nätfiskefiltret söker igenom sidor i den här zonen och letar efter skadligt innehåll.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067034)

  **Standard**: Aktiverad

- **Internet Explorer: ta bort knappen Kör den här gången för inaktuella Active X-kontroller**:  
  Med den här principinställningen kan du hindra användare från att se knappen ”Kör den här gången” och från att köra specifika inaktuella ActiveX-kontroller i Internet Explorer. Om du aktiverar den här principinställningen ser inte användarna knappen ”Kör den här gången” i varningsmeddelandet som visas när Internet Explorer blockerar en inaktuell ActiveX-kontroll. Om du inaktiverar eller inte konfigurerar den här principinställningen ser användarna knappen ”Kör den här gången” i varningsmeddelandet som visas när Internet Explorer blockerar en inaktuell ActiveX-kontroll. Genom att klicka på den här knappen kan användaren köra den inaktuella ActiveX-kontrollen en gång. Mer information finns i avsnittet om inaktuella ActiveX-kontroller i TechNet-biblioteket för Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067123)

  **Standard**: Aktiverad

- **Internet Explorer: starta program och filer i en iFrame i zonen Internet**:  
  Med den här principinställningen kan du ange om program kan köras och om filer kan laddas ned från en IFRAME-referens i HTML-koden för sidorna i den här zonen. Om du aktiverar den här principinställningen kan användarna köra program och ladda ned filer från en IFRAME på sidorna i den här zonen utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill köra program och ladda ned filer från en IFRAME på sidorna i den här zonen. Om du inaktiverar den här principinställningen kan användarna inte köra program och ladda ned filer från en IFRAME på sidorna i den här zonen. Om du inte konfigurerar den här principinställningen tillfrågas användarna om de vill köra program och ladda ned filer från en IFRAME på sidorna i den här zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067020)

  **Standard**: Inaktivera

- **Internet Explorer: navigera i fönster och ramar mellan olika domäner i zonen Begränsad**:  
  Med den här principinställningen kan du ange alternativ för att dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Om du aktiverar den här principinställningen och klickar på Aktivera kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra denna inställning. Om du aktiverar den här principinställningen och klickar på Inaktivera kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra denna inställning. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 10 kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 9 och tidigare versioner kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra denna inställning.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067050)

  **Standard**: Inaktivera

- **Internet Explorer: SmartScreen i zonen Internet**:  
  Den här principinställningen styr huruvida SmartScreen-filtret söker igenom sidor i den här zonen och letar efter skadligt innehåll. Om du aktiverar den här principinställningen söker SmartScreen-filtret igenom sidor i den här zonen och letar efter skadligt innehåll. Om du inaktiverar den här principinställningen söker SmartScreen-filtret inte igenom sidor i den här zonen för att leta efter skadligt innehåll. Om du inte konfigurerar den här principinställningen kan användaren välja huruvida SmartScreen-filtret ska söka igenom sidor i den här zonen och leta efter skadligt innehåll. Obs! I Internet Explorer 7 styr den här principinställningen om nätfiskefiltret söker igenom sidor i den här zonen och letar efter skadligt innehåll.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067047)

  **Standard**: Aktiverad

- **Internet Explorer: låsta Java-behörigheter i zonen Betrodda platser**:  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop) samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067142)

  **Standard**: Inaktivera Java

- **Internet Explorer: kontrollera signaturer för nedladdade program**:  
  Med den här principinställningen kan du ange om Internet Explorer ska söka efter digitala signaturer (som identifierar utgivaren av signerad programvara och verifierar att den inte har ändrats eller manipulerats) på användarnas datorer innan körbara program laddas ned. Om du aktiverar den här principinställningen letar Internet Explorer efter digitala signaturer för körbara program och visar deras identiteter innan de laddas ned till användarnas datorer. Om du inaktiverar den här principinställningen letar inte Internet Explorer efter digitala signaturer för körbara program och visar inte deras identiteter innan de laddas ned till användarnas datorer. Om du inte konfigurerar den här principen letar inte Internet Explorer efter digitala signaturer för körbara program och visar inte deras identiteter innan de laddas ned till användarnas datorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067051)

  **Standard**: Aktiverad

- **Internet Explorer: skriptkörning med webbläsarkontroller i zonen Begränsad**:  
  Den här principinställningen anger om en sida kan styra inbäddade WebBrowser-kontroller via skript. Om du aktiverar den här principinställningen tillåts skriptåtkomst till WebBrowser-kontrollen. Om du inaktiverar den här principinställningen tillåts inte skriptåtkomst till WebBrowser-kontrollen. Om du inte konfigurerar den här principinställningen kan användarna aktivera eller inaktivera skriptåtkomst till WebBrowser-kontrollen. Som standard tillåts skriptåtkomst till WebBrowser-kontrollen endast i zonerna Lokal dator och Intranät.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067098)

  **Standard**: Inaktiverad

- **Internet Explorer: skriptfiler mellan webbplatser i zonen Begränsad**:  
  Den här principen styr huruvida XSS-filtret (Cross Site-Scripting) identifierar och förhindrar XSS-inmatningar till webbplatser i den här zonen. Om du aktiverar den här principinställningen aktiveras XSS-filtret för platser i den här zonen och XSS-filtret försöker blockera XSS-inmatningar. Om du inaktiverar den här principinställningen inaktiveras XSS-filtret för platser i den här zonen och Internet Explorer tillåter XSS-inmatningar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067178)

  **Standard**: Aktiverad

- **Internet Explorer: beteenden för binärfiler och skript i zonen Begränsad**:  
  Med den här principinställningen kan du hantera dynamiska beteenden för binärfiler och skript: komponenter som kapslar in specifika funktioner för HTML-element som de kopplats till. Om du aktiverar den här principinställningen är binärfiler och skript tillgängliga. Om du väljer Godkänns av administratör i listrutan är endast beteenden som visas i Uppföranden som godkänns av administratören under säkerhetsbegränsningsprincipen för binärt beteende tillgängliga. Om du inaktiverar den här principinställningen är beteenden för binärfiler och skript inte tillgängliga såvida inte programmen har implementerat en anpassad säkerhetshanterare. Om du inte konfigurerar den här principinställningen är beteenden för binärfiler och skript inte tillgängliga såvida inte programmen har implementerat en anpassad säkerhetshanterare.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067224)

  **Standard**: Inaktivera

- **Internet Explorer: kontroll av säkerhetsinställningar**:  
  Den här principinställningen inaktiverar funktionen för kontroll av säkerhetsinställningar, som kontrollerar säkerhetsinställningarna i Internet Explorer för att avgöra om inställningarna utsätter Internet Explorer för risk. Om du aktiverar den här principinställningen inaktiveras funktionen. Om du inaktiverar eller inte konfigurerar den här principinställningen aktiveras funktionen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067182)

  **Standard**: Aktiverad

- **Internet Explorer: säkerhetsvarning om potentiellt osäkra filer i zonen Internet**:  
  Den här principinställningen styr huruvida meddelandet ”Öppna fil – säkerhetsvarning” visas när användaren försöker öppna körbara filer eller andra potentiellt skadliga filer (till exempel från en filresurs i intranätet med hjälp av Utforskaren). Om du aktiverar den här principinställningen och väljer Aktivera i listrutan öppnas dessa filer utan någon säkerhetsvarning. Om du väljer Fråga i listrutan visas en säkerhetsvarning innan filerna öppnas. Om du inaktiverar den här principinställningen öppnas inte dessa filer. Om du inte konfigurerar den här principinställningen kan användaren konfigurera hur datorn hanterar dessa. Som standard blockeras dessa filer i zonen Begränsad, tillåts i zonerna Intranät och Lokal dator och har inställningen Fråga i zonerna Internet och Betrodda platser.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067204)

  **Standard**: Fråga

- **Internet Explorer: Java-behörigheter i zonen Intranät**:  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop) samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen ställs behörigheten in på Normal säkerhet.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067206)

  **Standard**: Hög säkerhet

- **Internet Explorer: blockera inaktuella Active X-kontroller**:  
  Den här principinställningen anger om Internet Explorer blockerar specifika inaktuella ActiveX-kontroller. Inaktuella ActiveX-kontroller blockeras aldrig i zonen Intranät. Om du aktiverar den här principinställningen slutar Internet Explorer att blockera inaktuella ActiveX-kontroller. Om du inaktiverar eller inte konfigurerar den här principinställningen fortsätter Internet Explorer att blockera specifika inaktuella ActiveX-kontroller. Mer information finns i avsnittet om inaktuella ActiveX-kontroller i TechNet-biblioteket för Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067203)

  **Standard**: Aktiverad

- **Internet Explorer: popup-blockerare i zonen Begränsad**:  
  Med den här principinställningen kan du ange om oönskade popup-fönster ska visas eller inte. Popup-fönster som öppnas när slutanvändaren klickar på en länk blockeras inte. Om du aktiverar den här principinställningen hindras de flesta oönskade popup-fönster från att visas. Om du inaktiverar den här principinställningen hindras inte popup-fönster från att visas. Om du inte konfigurerar den här principinställningen hindras de flesta oönskade popup-fönster från att visas.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067180)

  **Standard**: Aktivera

- **Internet Explorer: bearbetning av Säkerhetsbegränsningar för protokollet MK**:  
  Principinställningen Säkerhetsbegränsningar för protokollet MK minskar angreppsytan genom att förhindra MK-protokollet. Resurser som hanteras av MK-protokollet misslyckas. Om du aktiverar den här principinställningen blockeras MK-protokollet för Utforskaren och Internet Explorer och resurser som hanteras av MK-protokollet misslyckas. Om du inaktiverar den här principinställningen kan program använda API:et för MK-protokollet. Resurser som hanteras av MK-protokollet fungerar för processerna i Utforskaren och Internet Explorer. Om du inte konfigurerar den här principinställningen blockeras MK-protokollet för Utforskaren och Internet Explorer och resurser som hanteras av MK-protokollet misslyckas.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067179)

  **Standard**: Aktiverad

- **Internet Explorer: Java-behörigheter i zonen Betrodda platser**:  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop) samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen ställs behörigheten in på Låg säkerhet.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067200)

  **Standard**: Hög säkerhet

- **Internet Explorer: skriptkörning med Java-appletar i zonen Begränsad**:  
  Med den här principinställningen kan du ange om appletar exponeras för skript i zonen. Om du aktiverar den här principinställningen kan skript komma åt appletar automatiskt utan inblandning av användaren. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att skript kommer åt appletar. Om du inaktiverar den här principinställningen förhindras skript från att komma åt appletar. Om du inte konfigurerar den här principinställningen förhindras skript från att komma åt appletar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067202)

  **Standard**: Inaktivera

- **Internet Explorer: låsta Java-behörigheter i zonen Begränsad**:  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop) samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067181)

  **Standard**: Inaktivera Java

- **Internet Explorer: tillåt endast att godkända domäner använder ActiveX-kontroller i zonen Internet**:  
  Den här principinställningen styr huruvida användarna tillfrågas om de vill tillåta att ActiveX-kontroller körs på andra webbplatser än den webbplats som ActiveX-kontrollen installerades på. Om du aktiverar den här principinställningen tillfrågas användaren innan ActiveX-kontroller kan köras från webbplatser i den här zonen. Användaren kan välja att tillåta att kontrollen körs från den aktuella webbplatsen eller från alla webbplatser. Om du inaktiverar den här principinställningen ser inte användarna ActiveX-prompten per webbplats, och ActiveX-kontroller kan köras från alla webbplatser i den här zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067091)

  **Standard**: Aktiverad

- **Internet Explorer: ta med alla nätverkssökvägar**:  
  Internet Explorer: ta med alla nätverkssökvägar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067090)

  **Standard**: Inaktiverad

- **Internet Explorer: skyddat läge i zonen Internet**:  
  Med den här principinställningen kan du aktivera skyddat läge. Skyddat läge hjälper dig att skydda Internet Explorer mot säkerhetsproblem genom att begränsa de platser som Internet Explorer kan skriva till i registret och filsystemet. Om du aktiverar den här principinställningen aktiveras skyddat läge. Användaren kan inte inaktivera skyddat läge. Om du inaktiverar den här principinställningen inaktiveras skyddat läge. Användaren kan inte aktivera skyddat läge. Om du inte konfigurerar den här principinställningen kan användaren aktivera eller inaktivera skyddat läge.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067171)

  **Standard**: Aktivera

- **Internet Explorer: initiera och kör skript för Active X-kontroller som inte markerats som säkra i zonen Internet**:  
  Med den här principinställningen kan du hantera ActiveX-kontroller som inte har markerats som säkra. Om du aktiverar den här principinställningen körs ActiveX-kontroller, initieras med parametrar och körs med skript utan att objektsäkerhet anges för obetrodda data eller skript. Den här inställningen rekommenderas inte, förutom för säkra och administrerade zoner. Den här inställningen gör att både osäkra och säkra kontroller initieras och körs med skript, samtidigt som ActiveX-skriptkontrollerna som markerats som säkra i skriptalternativet ignoreras. Om du aktiverar den här principinställningen och väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontrollen initieras med parametrar eller körs med skript. Om du inaktiverar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar, och de körs inte med skript. Om du inte konfigurerar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar, och de körs inte med skript.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067170)

  **Standard**: Inaktivera

- **Internet Explorer: låst SmartScreen i zonen Begränsad**:  
  Den här principinställningen styr huruvida SmartScreen-filtret söker igenom sidor i den här zonen och letar efter skadligt innehåll. Om du aktiverar den här principinställningen söker SmartScreen-filtret igenom sidor i den här zonen och letar efter skadligt innehåll. Om du inaktiverar den här principinställningen söker SmartScreen-filtret inte igenom sidor i den här zonen för att leta efter skadligt innehåll. Om du inte konfigurerar den här principinställningen kan användaren välja huruvida SmartScreen-filtret ska söka igenom sidor i den här zonen och leta efter skadligt innehåll. Obs! I Internet Explorer 7 styr den här principinställningen om nätfiskefiltret söker igenom sidor i den här zonen och letar efter skadligt innehåll.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067092)

  **Standard**: Aktiverad

- **Internet Explorer: kraschidentifiering**:  
  Med den här principinställningen kan du hantera kraschidentifieringsfunktionen för tilläggshantering. Om du aktiverar den här principinställningen uppvisar en krasch i Internet Explorer samma beteende som i Windows XP Professional Service Pack 1 och tidigare, nämligen att Windows Felrapportering anropas. Alla principinställningar för Windows Felrapportering fortsätter att tillämpas. Om du inaktiverar eller inte konfigurerar den här principinställningen fungerar kraschidentifieringsfunktionen för tilläggshantering.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067094)

  **Standard**: Inaktiverad

- **Internet Explorer: Java-behörigheter i zonen Internet**:  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop) samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen ställs behörigheten in på Hög säkerhet.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067174)

  **Standard**: Inaktivera Java

- **Internet Explorer: aktiv skriptkörning i zonen Begränsad**:  
  Med den här principinställningen kan du ange om skriptkod på sidor i zonen kan köras. Om du aktiverar den här principinställningen kan skriptkod på sidor i zonen köras automatiskt. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att skriptkod på sidor i zonen körs. Om du inaktiverar den här principinställningen förhindras skriptkod från att köras på sidor i zonen. Om du inte konfigurerar den här principinställningen förhindras skriptkod på sidor i zonen från att köras.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067172)

  **Standard**: Inaktivera

- **Internet Explorer: inloggningsalternativ i zonen Internet**:  
  Med den här principinställningen kan du hantera inställningar för inloggningsalternativ. Om du aktiverar den här principinställningen kan du välja något av följande inloggningsalternativ. Anonym inloggning om du vill inaktivera HTTP-autentisering och gästkontot endast för CIFS-protokollet (Common Internet File System). Fråga efter användarnamn och lösenord om du vill uppmana användare att ange användar-ID:n och lösenord. När en användare har angett värdena kan de användas tyst i bakgrunden under resten av sessionen. Automatisk inloggning endast i zonen Intranät om du vill uppmana användaren att ange användar-ID:n och lösenord i andra zoner. När en användare har angett värdena kan de användas tyst i bakgrunden under resten av sessionen. Automatisk inloggning med aktuellt användarnamn och lösenord för att försöka logga in med Windows NT Challenge Response (även kallat NTLM-autentisering). Om servern har stöd för Windows NT Challenge Response används användarens användarnamn och lösenord för nätverket vid inloggningen. Om servern inte stöder Windows NT Challenge Response uppmanas användaren att ange användarnamnet och lösenordet. Om du inaktiverar den här principinställningen anges inloggningen endast till Automatisk inloggning i zonen Intranät. Om du inte konfigurerar den här principinställningen anges inloggningen till Automatisk inloggning endast i Intranät-zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067194)

  **Standard**: Fråga

- **Internet Explorer: tillåt att VBScript körs i zonen Begränsad**:  
  Med den här principinställningen kan du ange om VBScript kan köras på sidor från den angivna zonen i Internet Explorer. Om du valde Aktivera i listrutan kan VBScript köras utan inblandning av användaren. Om du valde Fråga i listrutan uppmanas användarna att välja om de vill tillåta att VBScript körs. Om du valde Inaktivera i listrutan förhindras VBScript från att köras. Om du inte konfigurerar eller om du inaktiverar den här principinställningen förhindras VBScript från att köra.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067173)

  **Standard**: Inaktivera

- **Internet Explorer: dra innehåll från olika domäner mellan fönster i zonen Internet**:  
  Med den här principinställningen kan du ange alternativ för att dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Om du aktiverar den här principinställningen och klickar på Aktivera kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra denna inställning. Om du aktiverar den här principinställningen och klickar på Inaktivera kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra denna inställning. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 10 kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 9 och tidigare versioner kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra denna inställning.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067093)

  **Standard**: Inaktiverad

- **Internet Explorer: initiera och kör skript för Active X-kontroller som inte markerats som säkra i zonen Intranät**:  
  Med den här principinställningen kan du hantera ActiveX-kontroller som inte har markerats som säkra. Om du aktiverar den här principinställningen körs ActiveX-kontroller, initieras med parametrar och körs med skript utan att objektsäkerhet anges för obetrodda data eller skript. Den här inställningen rekommenderas inte, förutom för säkra och administrerade zoner. Den här inställningen gör att både osäkra och säkra kontroller initieras och körs med skript, samtidigt som ActiveX-skriptkontrollerna som markerats som säkra i skriptalternativet ignoreras. Om du aktiverar den här principinställningen och väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontrollen initieras med parametrar eller körs med skript. Om du inaktiverar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar, och de körs inte med skript. Om du inte konfigurerar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar, och de körs inte med skript.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067175)

  **Standard**: Inaktivera

- **Internet Explorer: ladda ned inneslutningar**:  
  Den här principinställningen hindrar användaren från att ladda ned bilagor (bifogade filer) från en feed till användarens dator. Om du aktiverar den här principinställningen kan användaren inte ange att feed-synkroniseringsmotorn ska ladda ned en bilaga via sidan för feed-egenskaper. Utvecklare kan inte ändra nedladdningsinställningen via Feed-API:erna. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren ange att feed-synkroniseringsmotorn ska ladda ned en bilaga via sidan för feed-egenskaper. Utvecklare kan ändra nedladdningsinställningen via Feed-API:et.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067245)

  **Standard**: Inaktiverad

- **Internet Explorer: ladda ned osignerade Active X-kontroller i zonen Begränsad**:  
  Med den här principinställningen kan du ange om användarna kan ladda ned osignerade ActiveX-kontroller från zonen. Den här typen av kod kan vara skadlig, särskilt om den kommer från en obetrodd zon. Om du aktiverar den här principinställningen kan användarna köra osignerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att den osignerade kontrollen körs eller inte. Om du inaktiverar den här principinställningen kan användarna inte köra osignerade kontroller. Om du inte konfigurerar den här principinställningen kan användarna inte köra osignerade kontroller.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067177)

  **Standard**: Inaktivera

- **Internet Explorer: dra innehåll från olika domäner inuti fönster i zonen Internet**:  
  Med den här principinställningen kan du ange om användarna kan ladda ned osignerade ActiveX-kontroller från zonen. Den här typen av kod kan vara skadlig, särskilt om den kommer från en obetrodd zon. Om du aktiverar den här principinställningen kan användarna köra osignerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att den osignerade kontrollen körs eller inte. Om du inaktiverar den här principinställningen kan användarna inte köra osignerade kontroller. Om du inte konfigurerar den här principinställningen kan användarna inte köra osignerade kontroller.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067095)

  **Standard**: Inaktiverad

- **Internet Explorer-processer: begränsa Active X-installation**:  
  Den här principinställningen gör det möjligt för program som hanterar webbläsarkontrollen att blockera automatiska frågor om installationen av ActiveX-kontroller. Om du aktiverar den här principinställningen blockerar webbläsarkontrollen automatiska frågor om installationen av ActiveX-kontroller för alla processer. Om du inaktiverar eller inte konfigurerar den här principinställningen blockerar inte webbläsarkontrollen automatiska frågor om installationen av ActiveX-kontroller för alla processer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067250)

  **Standard**: Aktiverad

- **Internet Explorer: skriplet i zonen Internet**:  
  Med den här principinställningen kan du ange om användaren kan köra skriptlet. Om du aktiverar den här principinställningen kan användaren köra skriptlet. Om du inaktiverar den här principinställningen kan användaren inte köra skriptlet. Om du inte konfigurerar den här principinställningen kan användaren aktivera eller inaktivera skriptlet.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067176)

  **Standard**: Inaktivera

- **Internet Explorer: dra eller kopiera och klistra in filer i zonen Begränsad**:  
  Med den här principinställningen kan du ange om användarna kan dra filer eller kopiera och klistra in filer från en källa i zonen. Om du aktiverar den här principinställningen kan användarna automatiskt dra filer eller kopiera och klistra in filer från den här zonen. Om du väljer Fråga i listrutan tillfrågas användarna om de vill dra eller kopiera filer från den här zonen. Om du inaktiverar den här principinställningen hindras användarna från att dra filer eller att kopiera och klistra in filer från den här zonen. Om du inte konfigurerar den här principinställningen tillfrågas användarna om de vill dra eller kopiera filer från den här zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067096)

  **Standard**: Inaktivera

- **Internet Explorer: programvara när signaturen är ogiltig**:  
  Med den här principinställningen kan du ange om programvara, till exempel ActiveX-kontroller och nedladdning av filer, kan installeras och köras av användaren även om signaturen är ogiltig. En ogiltig signatur kan tyda på att någon har manipulerat filen. Om du aktiverar den här principinställningen tillfrågas användarna innan de kan installera eller köra filer med en ogiltig signatur. Om du inaktiverar den här principinställningen kan användarna inte köra eller installera filer med en ogiltig signatur. Om du inte konfigurerar den här principinställningen kan användarna välja om de vill köra eller installera filer med en ogiltig signatur.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067201)

  **Standard**: Inaktiverad

- **Internet Explorer: kopiera och klistra in via skript i zonen Begränsad**:  
  Med den här principinställningen kan du ange om skript kan utföra åtgärder med Urklipp (till exempel Klipp ut, Kopiera och Klistra in) i en angiven region. Om du aktiverar den här principinställningen kan skript utföra åtgärder med Urklipp. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta åtgärder med Urklipp. Om du inaktiverar den här principinställningen kan skript inte utföra åtgärder med Urklipp. Om du inte konfigurerar den här principinställningen kan skript inte utföra åtgärder med Urklipp.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067165)

  **Standard**: Inaktivera

- **Internet Explorer: dra innehåll från olika domäner mellan fönster i zonen Begränsad**:  
  Med den här principinställningen kan du ange alternativ för att dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Om du aktiverar den här principinställningen och klickar på Aktivera kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra denna inställning. Om du aktiverar den här principinställningen och klickar på Inaktivera kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra denna inställning. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 10 kan användarna inte dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan ändra den här inställningen i dialogrutan Internetalternativ. Om du inaktiverar den här principinställningen eller inte konfigurerar den i Internet Explorer 9 och tidigare versioner kan användarna dra innehåll från en domän till en annan domän när källan och målet finns i olika fönster. Användarna kan inte ändra denna inställning.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067166)

  **Standard**: Inaktiverad

- **Internet Explorer: användarna lägger till platse**:  
  Förhindrar att användarna kan lägga till eller ta bort platser från säkerhetszoner. En säkerhetszon är en grupp med webbplatser med samma säkerhetsnivå. Om du aktiverar den här principen inaktiveras platshanteringsinställningarna för säkerhetszoner. (Du kan visa platshanteringsinställningarna för säkerhetszoner i dialogrutan Internetalternativ genom att klicka på fliken Säkerhet och sedan på knappen Platser.) Om du inaktiverar den här principen eller inte konfigurerar den kan användarna lägga till webbplatser till eller ta bort webbplatser från zonerna Betrodda platser och Begränsade platser och ändra inställningarna för zonen Lokalt intranät. Den här principen förhindrar att användarna kan ändra platshanteringsinställningar för säkerhetszoner som angetts av administratören. Obs! Principen ”Inaktivera fliken Säkerhet” (i \Användarkonfiguration\Administrativa mallar\Windows-komponenter\Internet Explorer\Internet på Kontrollpanelen), som tar bort fliken Säkerhet från gränssnittet, prioriteras framför den här principen. Om den aktiveras så ignoreras den här principen. Se även principen”Säkerhetszoner: Använd endast datorinställningar”.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067167)

  **Standard**: Inaktiverad

- **Internet Explorer: skriptinitierade fönster i zonen Internet**:  
  Med den här principinställningen kan du hantera begränsningar för skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet. Om du aktiverar den här principinställningen gäller inte begränsningar för Windows-säkerhet i den här zonen. Säkerhetszonen körs utan det ytterligare säkerhetslager som tillhandahålls av den här funktionen. Om du inaktiverar den här principinställningen kan inte de potentiellt skadliga åtgärderna i skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet köras. Den här säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på kontrollinställningen för skriptinitierade säkerhetsbegränsningar för Windows. Om du inte konfigurerar den här principinställningen kan inte de potentiellt skadliga åtgärderna i skriptinitierade popup-fönster och fönster som innehåller namnlisten och statusfältet köras. Den här säkerhetsfunktionen i Internet Explorer aktiveras i den här zonen baserat på kontrollinställningen för skriptinitierade säkerhetsbegränsningar för Windows.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067088)

  **Standard**: Inaktiverad

- **Internet Explorer: säkerhetszoner använder endast datorinställningar**:  
  Använder information om säkerhetszoner för alla användare på samma dator. En säkerhetszon är en grupp med webbplatser med samma säkerhetsnivå. Om du aktiverar den här principen tillämpas ändringar som användaren gör i en säkerhetszon på alla användare av den aktuella datorn. Om du inaktiverar den här principen eller inte konfigurerar den kan användare på samma dator konfigurera egna inställningar för säkerhetszoner. Använd den här principen om du vill se till att inställningarna för säkerhetszoner är enhetliga på samma dator och att de inte varierar mellan användare. Se även principen ”Säkerhetszoner: Tillåt inte att användare ändrar principer”.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067086)

  **Standard**: Aktiverad

- **Internet Explorer: låsta Java-behörigheter i zonen Lokal dator**:  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop) samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067253)

  **Standard**: Inaktivera Java

- **Internet Explorer: kör inte program mot skadlig kod mot Active X-kontroller i zonen Begränsad**:  
  Den här principinställningen anger om Internet Explorer kör program mot skadlig kod mot ActiveX-kontroller för att se om det är säkert att läsa in dem på sidor. Om du aktiverar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inaktiverar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inte konfigurerar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Användare kan aktivera eller inaktivera det här beteendet med hjälp av säkerhetsinställningarna för Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067089)

  **Standard**: Inaktiverad

- **Internet Explorer: kör .NET Framework-beroende komponenter som har signerats med Authenticode i zonen Begränsad**:  
  Med den här inställningen kan du ange om .NET Framework-komponenter som har signerats med Authenticode kan köras från Internet Explorer. Dessa komponenter är hanterade kontroller som en objekttagg refererar till och hanterade körbara filer som en länk refererar till. Om du aktiverar den här principinställningen kör Internet Explorer signerade hanterade komponenter. Om du väljer Fråga i listrutan uppmanas användarna att välja om de vill köra signerade hanterade komponenter i Internet Explorer. Om du inaktiverar den här principinställningen kör Internet Explorer inte osignerade hanterade komponenter. Om du inte konfigurerar den här principinställningen kör Internet Explorer inte osignerade hanterade komponenter.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067169)

  **Standard**: Inaktivera

- **Internet Explorer: åtkomst till datakällor i zonen Begränsad**:  
  Med den här inställningen kan du ange om Internet Explorer kan komma åt data från en annan säkerhetszon med hjälp av Microsoft XML Parser (MSXML) eller ActiveX Data Objects (ADO). Om du aktiverar den här principinställningen kan användarna läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta inläsningen av en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du inaktiverar den här principinställningen kan användarna inte läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen. Om du inte konfigurerar den här principinställningen kan användarna inte läsa in en sida i zonen som använder MSXML eller ADO för att komma åt data från en annan plats i zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067161)

  **Standard**: Inaktivera

- **Internet Explorer-Internetzoner kör inte program mot skadlig kod mot ActiveX-kontroller**:  
  Den här principinställningen anger om Internet Explorer kör program mot skadlig kod mot ActiveX-kontroller för att se om det är säkert att läsa in dem på sidor. Om du aktiverar den här principinställningen stämmer inte Internet Explorer av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inaktiverar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Om du inte konfigurerar den här principinställningen stämmer Internet Explorer alltid av med ditt program mot skadlig kod för att se om det är säkert att skapa en instans av ActiveX-kontrollen. Användare kan aktivera eller inaktivera det här beteendet med hjälp av säkerhetsinställningarna för Internet Explorer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067162)

  **Standard**: Inaktiverad

- **Internet Explorer: kopiera och klistra in via skript i zonen Internet**:  
  Med den här principinställningen kan du ange om skript kan utföra åtgärder med Urklipp (till exempel Klipp ut, Kopiera och Klistra in) i en angiven region. Om du aktiverar den här principinställningen kan skript utföra åtgärder med Urklipp. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta åtgärder med Urklipp. Om du inaktiverar den här principinställningen kan skript inte utföra åtgärder med Urklipp. Om du inte konfigurerar den här principinställningen kan skript inte utföra åtgärder med Urklipp.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067084)

  **Standard**: Inaktivera

- **Internet Explorer: använd Active X-installationstjänsten**:  
  Med den här principinställningen kan du ange hur ActiveX-kontroller installeras. Om du aktiverar den här principinställningen installeras ActiveX-kontroller endast om ActiveX-installationstjänsten är tillgänglig och har konfigurerats att tillåta installationen av ActiveX-kontroller. Om du inaktiverar eller inte konfigurerar den här principinställningen installeras ActiveX-kontroller, inklusive kontroller för varje användare, via standardinstallationsprocessen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067163)

  **Standard**: Aktiverad

- **Internet Explorer: skydda processer från zonupplyftning**:  
  Internet Explorer begränsar varje webbsida som öppnas. Begränsningarna är beroende av webbsidans plats (Internet, intranät, zonen Lokal dator och så vidare). Till exempel har webbsidor på den lokala datorn minst begränsningar och finns i zonen Lokal dator, vilket gör den lokala datorn till ett favoritmål för illvilliga användare. Om du aktiverar den här principinställningen kan alla zoner skyddas från zonupplyftning för alla processer. Om du inaktiverar eller inte konfigurerar den här principinställningen skyddas inte andra processer än Internet Explorer och de som anges i processlistan på detta sätt.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067160)

  **Standard**: Aktiverad

- **Internet Explorer: ladda ned osignerade ActiveX-kontroller i zonen Internet**:  
  Med den här principinställningen kan du ange om användarna kan ladda ned osignerade ActiveX-kontroller från zonen. Den här typen av kod kan vara skadlig, särskilt om den kommer från en obetrodd zon. Om du aktiverar den här principinställningen kan användarna köra osignerade kontroller utan manuella åtgärder. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att den osignerade kontrollen körs eller inte. Om du inaktiverar den här principinställningen kan användarna inte köra osignerade kontroller. Om du inte konfigurerar den här principinställningen kan användarna inte köra osignerade kontroller.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067325)

  **Standard**: Inaktivera

- **Internet Explorer: navigera i fönster och ramar mellan olika domäner i zonen Internet**:  
  Med den här principinställningen kan du ange hur fönster och ramar öppnas och hur program kommer åt dem från olika domäner. Om du aktiverar den här principinställningen kan användarna öppna fönster och ramar från andra domäner och komma åt program från andra domäner. Om du väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att fönster och ramar kommer åt program från andra domäner. Om du inaktiverar den här principinställningen kan användarna inte öppna fönster och ramar för att komma åt program från olika domäner. Om du inte konfigurerar den här principinställningen kan användarna öppna fönster och ramar från andra domäner och komma åt program från andra domäner.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067083)

  **Standard**: Inaktivera

- **Internet Explorer: uppdateringar av statusfältet via skript i zonen Internet**:  
  Med den här principinställningen kan du bestämma huruvida skript kan uppdatera statusfältet i zonen. Om du aktiverar den här principinställningen kan skript uppdatera statusfältet. Om du inaktiverar eller inte konfigurerar den här principinställningen kan inte skript uppdatera statusfältet.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067087)

  **Standard**: Inaktiverad

- **Internet Explorer: ta med lokal sökväg när filer laddas upp till servern i zonen Begränsad**:  
  Den här principinställningen styr huruvida information om den lokala sökvägen skickas när användaren laddar upp en fil via ett HTML-formulär. Om information om den lokala sökvägen skickas kan servern oavsiktligt få tillgång till viss information. Filer som skickas från användarens dator kan exempelvis innehålla användarnamnet som en del av sökvägen. Om du aktiverar den här principinställningen skickas information om sökvägen när användaren överför en fil via ett HTML-formulär. Om du inaktiverar den här principinställningen tas information om sökvägen bort när användaren överför en fil via ett HTML-formulär. Om du inte konfigurerar den här principinställningen kan användarna välja om sökvägsinformation ska skickas när de laddar upp en fil via ett HTML-formulär. Sökvägsinformation skickas som standard.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067085)

  **Standard**: Inaktiverad

- **Internet Explorer-processer: begränsa filnedladdning**:  
  Den här principinställningen gör det möjligt för program som hanterar webbläsarkontrollen att blockera automatiska frågor om filnedladdningar som inte har initierats av användaren. Om du aktiverar den här principinställningen blockerar webbläsarkontrollen automatiska frågor om filnedladdningar som inte har initierats av användaren för alla processer. Om du inaktiverar den här principinställningen blockerar inte webbläsarkontrollen automatiska frågor om filnedladdningar som inte har initierats av användaren för alla processer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067164)

  **Standard**: Aktiverad

- **Internet Explorer: tillåt endast att godkända domäner använder Active X-kontroller i zonen Begränsad**:  
  Den här principinställningen styr huruvida användarna tillfrågas om de vill tillåta att ActiveX-kontroller körs på andra webbplatser än den webbplats som ActiveX-kontrollen installerades på. Om du aktiverar den här principinställningen tillfrågas användaren innan ActiveX-kontroller kan köras från webbplatser i den här zonen. Användaren kan välja att tillåta att kontrollen körs från den aktuella webbplatsen eller från alla webbplatser. Om du inaktiverar den här principinställningen ser inte användarna ActiveX-prompten per webbplats, och ActiveX-kontroller kan köras från alla webbplatser i den här zonen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067233)

  **Standard**: Aktiverad

- **Internet Explorer: initiera och kör skript för Active X-kontroller som inte markerats som säkra i zonen Begränsad**:  
  Med den här principinställningen kan du hantera ActiveX-kontroller som inte har markerats som säkra. Om du aktiverar den här principinställningen körs ActiveX-kontroller, initieras med parametrar och körs med skript utan att objektsäkerhet anges för obetrodda data eller skript. Den här inställningen rekommenderas inte, förutom för säkra och administrerade zoner. Den här inställningen gör att både osäkra och säkra kontroller initieras och körs med skript, samtidigt som ActiveX-skriptkontrollerna som markerats som säkra i skriptalternativet ignoreras. Om du aktiverar den här principinställningen och väljer Fråga i listrutan tillfrågas användarna om de vill tillåta att kontrollen initieras med parametrar eller körs med skript. Om du inaktiverar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar, och de körs inte med skript. Om du inte konfigurerar den här principinställningen initieras inte ActiveX-kontroller som inte kan göras säkra med parametrar, och de körs inte med skript.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067097)

  **Standard**: Inaktivera

- **Internet Explorer: användare ändrar principer**:  
  Hindrar användare från att ändra inställningarna för säkerhetszoner. En säkerhetszon är en grupp med webbplatser med samma säkerhetsnivå. Om du aktiverar den här principen inaktiveras knappen Anpassad nivå och skjutreglaget för säkerhetsnivå på fliken Säkerhet i dialogrutan Internetalternativ. Om du inaktiverar den här principen eller inte konfigurerar den kan användarna ändra inställningarna för säkerhetszoner. Den här principen hindrar användarna från att ändra inställningarna för säkerhetszoner som angetts av administratören. Obs! Principen ”Inaktivera fliken Säkerhet” (i \Användarkonfiguration\Administrativa mallar\Windows-komponenter\Internet Explorer\Internet på Kontrollpanelen), som tar bort fliken Säkerhet i Internet Explorer på Kontrollpanelen prioriteras framför den här principen. Om den aktiveras så ignoreras den här principen. Se även principen”Säkerhetszoner: Använd endast datorinställningar”.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067155)

  **Standard**: Inaktiverad

- **Internet Explorer: skyddat läge i zonen Begränsad**:  
  Med den här principinställningen kan du aktivera skyddat läge. Skyddat läge hjälper dig att skydda Internet Explorer mot säkerhetsproblem genom att begränsa de platser som Internet Explorer kan skriva till i registret och filsystemet. Om du aktiverar den här principinställningen aktiveras skyddat läge. Användaren kan inte inaktivera skyddat läge. Om du inaktiverar den här principinställningen inaktiveras skyddat läge. Användaren kan inte aktivera skyddat läge. Om du inte konfigurerar den här principinställningen kan användaren aktivera eller inaktivera skyddat läge.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067080)

  **Standard**: Aktivera

- **Internet Explorer: datapersistence av användare i zonen Internet**:  
  Med den här principinställningen kan du hantera lagringen av information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. När en användare kommer tillbaka till en bestående sida, kan sidans tillstånd återställas om den här principinställningen är korrekt konfigurerad. Om du aktiverar den här principinställningen kan användarna lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. Om du inaktiverar den här principinställningen kan användarna inte lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. Om du inte konfigurerar den här principinställningen kan användarna lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067156)

  **Standard**: Inaktiverad

- **Internet Explorer: skriptkörning med webbläsarkontroller i zonen Internet**:  
  Den här principinställningen anger om en sida kan styra inbäddade WebBrowser-kontroller via skript. Om du aktiverar den här principinställningen tillåts skriptåtkomst till WebBrowser-kontrollen. Om du inaktiverar den här principinställningen tillåts inte skriptåtkomst till WebBrowser-kontrollen. Om du inte konfigurerar den här principinställningen kan användarna aktivera eller inaktivera skriptåtkomst till WebBrowser-kontrollen. Som standard tillåts skriptåtkomst till WebBrowser-kontrollen endast i zonerna Lokal dator och Intranät.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067157)

  **Standard**: Inaktiverad

- **Internet Explorer: datapersistence av användare i zonen Begränsad**:  
  Med den här principinställningen kan du hantera lagringen av information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. När en användare kommer tillbaka till en bestående sida, kan sidans tillstånd återställas om den här principinställningen är korrekt konfigurerad. Om du aktiverar den här principinställningen kan användarna lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. Om du inaktiverar den här principinställningen kan användarna inte lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk. Om du inte konfigurerar den här principinställningen kan inte användarna lagra information i webbläsarens historik, i Favoriter, i ett XML-arkiv eller direkt i en webbsida som sparats till disk.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067081)

  **Standard**: Inaktiverad

- **Internet Explorer: låsta Java-behörigheter i zonen Intranät**:  
  Med den här principinställningen kan du hantera behörigheter för Java-appletar. Om du aktiverar den här principinställningen kan du välja alternativ från listrutan. Anpassat om du vill kontrollera behörighetsinställningar individuellt. Låg säkerhet innebär att appletar kan utföra alla åtgärder. Normal säkerhet innebär att appletar kan köra i sandbox-miljöer (ett område i minnet utanför vilket programmet inte kan göra anrop) samt funktioner som tillfälligt utrymme (ett säkert och skyddat lagringsområde på klientdatorn) och användarstyrd I/O för filer. Hög säkerhet innebär att appletar kan köra i sandbox-miljöer. Inaktivera Java om du vill förhindra att appletar körs. Om du inaktiverar den här principinställningen kan inte Java-appletar köras. Om du inte konfigurerar den här principinställningen inaktiveras Java-appletar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067082)

  **Standard**: Inaktivera Java

- **Internet Explorer: utökat skyddat läge**:  
  Utökat skyddat läge ger ytterligare skydd mot skadliga webbplatser genom att använda 64-bitarsprocesser i 64-bitarsversioner av Windows. För datorer som kör minst Windows 8 begränsar utökat skyddat läge också vilka platser Internet Explorer kan läsa från i registret och filsystemet. Om du aktiverar den här principinställningen aktiveras utökat skyddat läge. Alla zoner som har skyddat läge aktiverat använder utökat skyddat läge. Användare kan inte inaktivera utökat skyddat läge. Om du inaktiverar den här principinställningen inaktiveras utökat skyddat läge. Alla zoner som har skyddat läge aktiverat använder den version av skyddat läge som introducerades i Internet Explorer 7 för Windows Vista. Om du inte konfigurerar den här principen kan användarna aktivera eller inaktivera utökat skyddat läge på fliken Avancerat i dialogrutan Internetalternativ.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067158)

  **Standard**: Aktiverad

- **Internet Explorer: kringgå SmartScreen-varningar**:  
  Den här principinställningen anger om användaren kan kringgå varningar från SmartScreen-filtret. SmartScreen-filtret varnar användaren om körbara filer som Internet Explorer-användare vanligtvis inte laddar ned från Internet. Om du aktiverar den här principinställningen blockerar SmartScreen-filtret användaren. Om du inaktiverar eller inte konfigurerar den här principinställningen kan användaren kringgå varningar från SmartScreen-filtret.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067159)

  **Standard**: Inaktiverad

- **Internet Explorer: metauppdatering i zonen Begränsad**:  
  Med den här principinställningen kan du ange om en användares webbläsare kan omdirigeras till en annan webbsida om den som skapat webbsidan använder inställningen för uppdatering av metadata (tagg) för att omdirigera till en annan webbsida. Om du aktiverar den här principinställningen kan en användares webbläsare som läser in en sida som innehåller en aktiv inställning för metadatauppdatering omdirigeras till en annan webbsida. Om du inaktiverar den här principinställningen kan inte en användares webbläsare som läser in en sida som innehåller en aktiv inställning för metadatauppdatering omdirigeras till en annan webbsida. Om du inte konfigurerar den här principinställningen kan inte en användares webbläsare som läser in en sida som innehåller en aktiv inställning för metadatauppdatering omdirigeras till en annan webbsida.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067154)

  **Standard**: Inaktiverad

## <a name="local-policies-security-options"></a>Säkerhetsalternativ för lokala principer

Mer information finns i [CSP-princip – LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) i Windows-dokumentationen.

- **Begränsa anonym åtkomst till namngivna pipes och resurser**:  
  När den här säkerhetsinställningen är aktiverad begränsar den anonym åtkomst för resurser och pipes till inställningar för: (1) Namngivna pipes som kan nås anonymt (2) Resurser som kan nås anonymt.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067212)

  **Standard**: Ja

- **Minsta sessionssäkerhet för NTLM SSP-baserade servrar**:  
  Den här säkerhetsinställningen gör att en server kan kräva förhandling av 128-bitarskryptering och NTLMv2-sessionssäkerhet. Dessa värden är beroende av säkerhetsinställningen för autentiseringsnivån för LAN Manager. Alternativen är: Kräv NTLMv2-sessionssäkerhet: Anslutningen misslyckas om inte meddelandeintegritet förhandlas. Kräv 128-bitarskryptering. Anslutningen misslyckas om inte stark kryptering (128-bitars) förhandlas.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067246)

  **Standard**: Kräv NTLM V2 och 128-bitarskryptering

- **Minuter av låsskärmsinaktivitet innan skärmsläckaren aktiveras**:  
  Windows övervakar inaktiviteten för en inloggningssession och om inaktiviteten överstiger inaktivitetsgränsen aktiveras skärmsläckaren och sessionen låses.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067210)

  **Standard**: 15

- **Kräv att klienten signerar all kommunikation digitalt**:  
  Säkerhetsinställningen anger den om all säker kanaltrafik som initieras av domänmedlemmen måste signeras eller krypteras. När en dator ansluter till en domän skapas ett datorkonto. När datorn sedan startas använder den lösenordet för datorkontot för att skapa en säker kanal med en domänkontrollant för dess domän. Den här säkra kanalen används för att utföra åtgärder som NTLM-direktautentisering, LSA SID/namnuppslag och mer. Den här inställningen anger huruvida all säker kanaltrafik som initieras av domänmedlemmen uppfyller säkerhetskraven. Mer specifikt anger den huruvida all säker kanaltrafik som startas av domänmedlemmen måste signeras eller krypteras. Om den här principen aktiveras upprättas inte den säkra kanalen, såvida inte signering eller kryptering av all säker kanaltrafik förhandlas. Om den här principen inaktiveras förhandlas kryptering och signering av all säker kanaltrafik med domänkontrollanten. I så fall beror signerings- och krypteringsnivån på domänkontrollantens version och inställningarna för följande två principer: Domänmedlem: Kryptera data för säker kanal digitalt (om det är möjligt) Domänmedlem: Signera säkra kanaldata digitalt (om det är möjligt).  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067187)

  **Standard**: Ja

- **Autentiseringsnivå**:  
  Den här säkerhetsinställningen avgör vilket autentiseringsprotokoll för anrop/svar som används för nätverksinloggningar. Den här inställningen påverkar nivån för autentiseringsprotokollet som används av klienter, nivån för den förhandlade sessionssäkerheten och autentiseringsnivån som accepteras av servrar enligt följande:

  - *Skicka LM- och NTLM-svar* – Klienter använder LM- och NTLM-autentisering och använder aldrig NTLMv2-sessionssäkerhet; domänkontrollanter accepterar LM-, NTLM- och NTLMv2-autentisering.

  - *Skicka LM och NTLM - använd NTLMv2-sessionssäkerhet om detta förhandlats* – Klienter använder LM- och NTLM-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det. Domänkontrollanter accepterar LM-, NTLM- och NTLMv2-autentisering.

  - *Skicka endast NTLM-svar* – Klienter använder endast NTLM-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det; domänkontrollanter accepterar LM-, NTLM- och NTLMv2-autentisering.

  - *Skicka endast NTLMv2-svar* – Klienter använder endast NTLMv2-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det; domänkontrollanter accepterar LM-, NTLM- och NTLMv2-autentisering.

  - *Skicka endast NTLMv2-svar. Neka LM* – Klienter använder endast NTLMv2-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det. Domänkontrollanter nekar LM (endast NTLM- och NTLMv2-autentisering accepteras).

  - *Skicka endast NTLMv2-svar. Neka LM och NTLM* – Klienter använder endast NTLMv2-autentisering och använder NTLMv2-sessionssäkerhet om servern stöder det. Domänkontrollanter nekar LM och NTLM (endast NTLMv2-autentisering accepteras).

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067189)

  **Standard**: Skicka endast NTLMv2-svar. Neka LM och NTLM

- **Förhindra att klienter skickar okrypterade lösenord till SMB-servrar från tredje part**:  
  Om den här säkerhetsinställningen är aktiverad kan SMB-omdirigeraren (Server Message Block) skicka lösenord i klartext till SMB-servrar från tredje part som inte har stöd för lösenordskryptering under autentiseringen. Att skicka okrypterade lösenord utgör en säkerhetsrisk.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067235)

  **Standard**: Ja

- **Kräv alltid digital signering av kommunikation av servrar**:  
  Den här säkerhetsinställningen anger om SMB-klienten ska försöka förhandla om SMB-paketsignering. SMB-protokollet (Server Message Block) lägger grunden för Microsofts fil- och skrivardelning och många andra nätverksfunktioner, till exempel fjärradministration för Windows. För att förhindra man-i-mitten-attacker som ändrar SMB-paket under överföring, stöder SMB-protokollet digital signering av SMB-paket. Den här principinställningen anger om SMB-klientkomponenten ska försöka förhandla om SMB-paketsignering när den ansluter till en SMB-server. Om den här inställningen är aktiverad uppmanar Microsoft-nätverksklienten servern att utföra SMB-paketsignering när sessionen upprättas. Om paketsignering har aktiverats på servern, förhandlas paketsignering. Om principen är inaktiverad förhandlar SMB-klienten aldrig om SMB-paketsignering.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067319)

  **Standard**: Ja

- **Fråga om beteende för utökade administratörsprivilegier**:  
  Den här principinställningen styr beteendet för frågan om utökade privilegier för administratörer. Alternativen är:

  - *Utöka privilegier utan att fråga* – Tillåter att behöriga konton utför en åtgärd som kräver utökade privilegier utan att kräva godkännande eller autentiseringsuppgifter. Obs! Använd endast det här alternativet i de mest begränsade miljöerna.

  - *Fråga efter autentiseringsuppgifter på skyddat skrivbord* – När en åtgärd kräver utökade privilegier uppmanas användaren att ange ett privilegierat användarnamn och lösenord på det skyddade skrivbordet. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med användarens högsta behörigheter.

  - *Fråga efter medgivande på skyddat skrivbord* – När en åtgärd kräver utökade privilegier uppmanas användaren att välja antingen Tillåt eller Neka på det skyddade skrivbordet. Om användaren väljer Tillåt fortsätter åtgärden med användarens högsta behörigheter.

  - *Fråga efter autentiseringsuppgifter* – När en åtgärd kräver utökade privilegier uppmanas användaren att ange ett användarnamn och lösenord för administratörer. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med tillämplig behörighet.

  - *Fråga efter medgivande* – När en åtgärd kräver utökade privilegier uppmanas användaren att välja Tillåt eller Neka. Om användaren väljer Tillåt fortsätter åtgärden med användarens högsta behörigheter.

  - *Fråga efter medgivande för binära filer som inte tillhör Windows* – När en åtgärd för ett program från tredje part kräver utökade privilegier uppmanas användaren att välja Tillåt eller Neka på det skyddade skrivbordet. Om användaren väljer Tillåt fortsätter åtgärden med användarens högsta behörigheter.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067215)

  **Standard**: Fråga efter medgivande på det skyddade skrivbordet

- **Minsta sessionssäkerhet för NTLM SSP-baserade klienter**:  
  Den här säkerhetsinställningen gör att en klient kan kräva förhandling av 128-bitarskryptering och NTLMv2-sessionssäkerhet. Dessa värden är beroende av säkerhetsinställningen för autentiseringsnivån för LAN Manager. Alternativen är:

  - *Kräv NTLMv2-sessionssäkerhet* – Anslutningen misslyckas om NTLMv2-protokoll inte förhandlas.

  - *Kräv 128-bitarskryptering* – Anslutningen misslyckas om inte stark kryptering (128-bitars) förhandlas.

  - *Kräv NTLMv2 och 128-bitarskryptering*.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067324)

  **Standard**: Kräv NTLM V2 128-kryptering

- **Beteende vid borttagning av smartkort**:  
  Den här säkerhetsinställningen avgör vad som händer när smartkortet för en inloggad användare tas bort från smartkortsläsaren. Alternativen är:

  - *Ingen åtgärd*.

  - *Lås arbetsstation* – Arbetsstationen låses när smartkortet tas bort, vilket gör att användare kan lämna området, ta sina smartkort med sig och behålla en skyddad session.

  - *Framtvinga utloggning* – användaren loggas ut automatiskt när smartkortet tas bort.

  - *Koppla från Remote Desktop Services-session* – om smartkortet tas bort så kopplas sessionen från utan att användaren loggas ut. Med det här alternativet kan användaren sätta i smartkortet och fortsätta sessionen senare, eller vid en annan dator med smartkortsläsare, utan att behöva logga in igen. Om sessionen är lokal fungerar den här principen precis som Lås arbetsstationen.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067331)

  **Standard**: Lås arbetsstation

- **Blockera anonym uppräkning av SAM-konton och resurser**:  
  Den här säkerhetsinställningen styr huruvida anonym uppräkning av SAM-konton och resurser tillåts. Windows tillåter att anonyma användare utför vissa aktiviteter, till exempel att räkna upp namn på domänkonton och nätverksresurser. Detta är exempelvis praktiskt när en administratör vill bevilja åtkomst till användare i en betrodd domän som inte har ett ömsesidigt förtroende. Om du inte vill tillåta anonym uppräkning av SAM-konton och resurser anger du den här principen till *Ja*.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067191)

  **Standard**: Ja

- **Blockera fjärrinloggning med tomt lösenord**:  
  Den här säkerhetsinställningen anger huruvida lokala konton som inte är lösenordsskyddade kan användas för att logga in från andra platser än den fysiska datorkonsolen. Om inställningen är aktiverad måste lokala konton som inte är lösenordsskyddade använda datorns tangentbord för att logga in.

  *Varning!* Datorer som inte är skyddade rent fysiskt bör alltid framtvinga principer för starka lösenord för alla lokala användarkonton. Annars kan alla med fysisk tillgång till datorn logga in med ett användarkonto som inte har något lösenord. Detta är särskilt viktigt för bärbara datorer.

  Om du använder den här säkerhetsprincipen för gruppen Alla kommer ingen att kunna logga in via Fjärrskrivbordstjänster. Den här inställningen påverkar inte inloggningar som använder domänkonton. Det är möjligt för program som använder interaktiva fjärrinloggningar att kringgå den här inställningen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067219)

  **Standard**: Ja

- **Standardbeteende för utökade användarprivilegier**:  
  Den här principinställningen styr beteendet för frågan om utökade privilegier för användare.

  - *Neka begäran om höjd behörighet automatiskt* – När en åtgärd kräver utökade privilegier visas ett konfigurerbart felmeddelande om nekad åtkomst. Ett företag som kör skrivbordsdatorer som standardanvändare kan välja den här inställningen för att minska antalet supportsamtal.

  - *Fråga efter autentiseringsuppgifter på skyddat skrivbord* – När en åtgärd kräver utökade privilegier uppmanas användaren att ange ett annat användarnamn och lösenord på det skyddade skrivbordet. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med tillämplig behörighet.

  - *Fråga efter autentiseringsuppgifter* – När en åtgärd kräver utökade privilegier uppmanas användaren att ange ett användarnamn och lösenord för administratörer. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med tillämplig behörighet.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067183)

  **Standard**: Neka förfrågningar om utökade privilegier automatiskt

- **Kräv läge för administratörstillåtelse för administratörer**:  
  Den här principinställningen styr beteendet för alla UAC-principinställningar (User Account Control) för datorn. Om du ändrar den här inställningen måste du starta om datorn. Alternativen är:

  - *Inte konfigurerat* – Läge för administratörstillåtelse och alla relaterade UAC-principinställningar är inaktiverade. Obs! Om den här inställningen är inaktiverad meddelar i Security Center dig om att den övergripande säkerheten för operativsystemet har minskas.

  - *Ja* – Läge för administratörstillåtelse är aktiverat. Den här principen måste vara aktiverad och associerade UAC-principinställningar måste anges på lämpligt sätt så att det inbyggda administratörskontot och alla andra användare som är medlemmar i gruppen Administratörer kan köra i läget för administratörstillåtelse.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067184)

  **Standard**: Ja

- **Förhindra anonym uppräkning av SAM-konton**:  
  Den här säkerhetsinställningen anger vilka ytterligare behörigheter som beviljas för anonyma anslutningar till datorn. Windows tillåter att anonyma användare utför vissa aktiviteter, till exempel att räkna upp namn på domänkonton och nätverksresurser. Detta är exempelvis praktiskt när en administratör vill bevilja åtkomst till användare i en betrodd domän som inte har ett ömsesidigt förtroende. Det här säkerhetsalternativet tillåter ytterligare begränsningar för anonyma anslutningar på följande sätt:

  - *Ja* – Tillåt inte uppräkning av SAM-konton. Det här alternativet ersätter alternativet Alla med Autentiserade användare i säkerhetsbehörigheterna för resurser.

  - *Inte konfigurerad* – Inga ytterligare begränsningar. Använd standardbehörigheter.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067318)

  **Standard**: Ja

- **Tillåt fjärranrop till hanteraren för kontosäkerhet**:  
  Med den här principinställningen kan du begränsa RPC-fjärranslutningar till SAM. Om du inte väljer den används standardsäkerhetsbeskrivningen.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067209)

  **Standard**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Använd läge för administratörstillåtelse**:  
  Den här principinställningen styr beteendet för läget för administratörstillåtelse för det inbyggda administratörskontot. Alternativen är:

  - *Ja* – Det inbyggda administratörskontot använder läget för administratörstillåtelse. Som standard uppmanas användaren att tillåta åtgärder som kräver utökade privilegier.

  - *Inte konfigurerat* – Det inbyggda administratörskontot kör alla program med administratörsprivilegier.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067186)

  **Standard**: Ja
  
- **Tillåt att gränssnittet får åtkomst till program för säkra platser**:  
  Den här principinställningen styr om UIAccess- eller UIA-program (User Interface Accessibility ) kan inaktivera det säkra skrivbordet automatiskt för att fråga om förhöjd behörighet när de används av en standardanvändare.

  - *Ja* – UIA-program, inklusive Windows Fjärrhjälp, inaktiverar automatiskt det skyddade skrivbordet för frågor om utökade privilegier. Om du inte inaktiverar principinställningen ”User Account Control: Switch to the secure desktop when prompting for elevation” (User Account Control: Växla till det säkra skrivbordet vid frågor om utökade privilegier) visas frågorna på den interaktiva användarens skrivbord i stället för på det skyddade skrivbordet.

  - *Inte konfigurerat*: Det skyddade skrivbordet kan endast inaktiveras av användaren av det interaktiva skrivbordet eller genom att principinställningen ”User Account Control: Switch to the secure desktop when prompting for elevation” inaktiveras (User Account Control: Växla till det säkra skrivbordet vid frågor om utökade privilegier).

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067185)

  **Standard**: Ja

- **Identifiera programinstallationer och fråga om utökade privilegier**:  
  Den här principinställningen styr beteendet för identifiering av programinstallationer för datorn. Alternativen är:

  - *Aktiverat* – När ett programinstallationspaket identifieras som kräver utökade privilegier uppmanas användaren att ange användarnamnet och lösenordet för en administrativ användare. Om användaren anger giltiga autentiseringsuppgifter fortsätter åtgärden med tillämplig behörighet.

  - *Inaktiverat* – Programinstallationspaket identifieras inte och inga frågor om utökade privilegier visas. Företag som kör skrivbord för standardanvändare och använder tekniker för delegerad installation, till exempel programvaruinstallation för Grupprincip eller SMS (Systems Management Server), bör inaktivera den här principinställningen. I det här fallet är identifieringen av installationsprogram inte nödvändigt.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067208)

  **Standard**: Ja

- **Förhindra lagring av hash-värdet för LAN Manager vid nästa lösenordsändring**:  
  Den här säkerhetsinställningen anger om hash-värdet för LAN Manager (LM) för det nya lösenordet lagras vid nästa lösenordsändring. LM-hashen är relativt svag och känslig för attacker jämfört med den kryptografiskt starkare Windows NT-hashen. Eftersom LM-hashvärdet lagras på den lokala datorn i säkerhetsdatabasen kan lösenorden komprometteras om säkerhetsdatabasen attackeras.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067213)

  **Standard**: Ja

- **Virtualisera skrivfel för filer och register till platser per användare**:  
  Den här principinställningen styr om programskrivningsfel omdirigeras till angivna register- och filsystemplatser. Den här principinställningen minskar risken med program som kör som administratörer och skriver körningsprogramdata till *%ProgramFiles%* , *%Windir%* , *%Windir%\system32* eller *HKLM\Software*.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067321)

  **Standard**: Ja

## <a name="microsoft-defender"></a>Microsoft Defender

Mer information finns i [CSP-princip – Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) i Windows-dokumentationen.

- **Sök igenom inkommande e-postmeddelanden**:  
  Tillåter eller nekar genomsökning av e-post.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067116)

  **Standard**: Ja

- **Office-appar startar underordnad processtyp**:  
  Office-appar kan inte skapa underordnade processer. Detta inkluderar Word, Excel, PowerPoint, OneNote och Access. Det här är ett typiskt beteende i skadlig kod, särskilt vid makrobaserade attacker som försöker använda Office-appar för att starta eller hämta skadliga körbara filer.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067121)

  **Standard**: Blockera

- **Medgivandetyp i Defender för överföring av dataprover**:  
  Kontrollerar nivån för användarmedgivande i Microsoft Defender för överföring av data. Om nödvändigt godkännande redan har beviljats, skickar Microsoft Defender dem. Annars (och om användaren har valt att aldrig bli tillfrågad) startas användargränssnittet för att be om användarens medgivande (när Defender/AllowCloudProtection tillåts) innan data skickas.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067131)

  **Standard**: Skicka säkra prover automatiskt

- **Intervall för signaturuppdatering (i timmar)** :  
  Signaturuppdateringsintervall i timmar i Defender.

  **Standard**: 4

- **Körningstyp för nedladdad nyttolast med skript**:  
  Körningstyp för nedladdad nyttolast med skript i Defender.

  **Standard**: Blockera
  
- **Förhindra typ av stöld av autentiseringsuppgifter**:  
  Microsoft Defender Credential Guard använder virtualiseringsbaserad säkerhet för att isolera hemligheter så att endast privilegierad programvara kan komma åt dem. Obehörig åtkomst till hemligheterna kan leda till stöld av autentiseringsuppgifter i form av Pass-the-Hash och Pass-The-Ticket. Microsoft Defender Credential Guard förhindrar dessa attacker genom att skydda NTLM-hashvärden för lösenord, biljettbeviljande Kerberos-biljetter och autentiseringsuppgifter som lagras av program som autentiseringsuppgifter för en domän.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067065)
  
  **Standard**: Aktivera

- **Körbara filtyper i e-postinnehåll**:  
  Den här regeln blockerar följande filtyper från att köras eller startas från ett e-postmeddelande i Microsoft Outlook eller webbaserad e-post (till exempel Gmail.com eller Outlook.com): Körbara filer (t.ex. .exe, .dll eller .scr), skriptfiler (t.ex. en PowerShell .ps-fil, VisualBasic .vbs-fil eller JavaScript .js-fil) och skriptarkivfiler.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067063)

  **Standard**: Blockera

::: zone-end
::: zone pivot="mdm-may-2019"

- **Adobe Reader-start i en underordnad process**:  
  **Standard**: Aktivera

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Nätverksskydd**:  
  Med den här principen kan du aktivera nätverksskydd (blockera/granska) eller inaktivera nätverksskydd i Microsoft Defender Exploit Guard. Nätverksskydd är en funktion i Microsoft Defender Exploit Guard som skyddar anställda som använder appar mot nätfiske, webbplatser som utnyttjar sårbarheter samt skadligt innehåll på Internet. Exempelvis hindras webbläsare från tredje part från att ansluta till farliga platser. Värdetypen är ett heltal. Om du aktiverar den här principinställningen aktiveras nätverksskydd och anställda kan inte inaktivera funktionen. Beteendet kan styras med följande alternativ: Blockera och granska. Om du aktiverar den här principen med alternativet ”Blockera” hindras användare och appar från att ansluta till farliga domäner. Du kan se den här aktiviteten i Microsoft Defender Säkerhetscenter. Om du aktiverar den här principen med alternativet ”Granska” hindras inte användare/appar från att ansluta till farliga domäner. Du kommer dock fortfarande att se den här aktiviteten i Microsoft Defender Security Center. Om du inaktiverar den här principen blockeras inte användare/appar från att ansluta till farliga domäner. Du kommer inte att se någon nätverksaktivitet i Microsoft Defender Security Center. Om du inte konfigurerar den här principen inaktiveras nätverksblockering som standard.  
  [Läs mer](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)

  **Standard**: Aktivera

- **Genomsökningsschema (dag) i Defender**:  
  Genomsökningsschema (dag) i Defender.

  **Standard**: Varje dag

- **Molnlevererat skydd**:  
  För att skydda din dator på bästa sätt skickar Microsoft Defender information till Microsoft om problem påträffas. Microsoft analyserar informationen, lär sig mer om problem som påverkar dig och andra kunder och erbjuder bättre lösningar.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067039)

  **Standard**:  Ja  

- **Potentiellt oönskad appåtgärd i Defender**:  
  Funktionen för skydd mot potentiellt oönskade program (PUA, Potentially Unwanted Application) i Microsoft Defender Antivirus kan identifiera och hindra potentiellt oönskade program från att hämtas och installeras på slutpunkter i ditt nätverk. Dessa program betraktas inte som virus, skadlig kod eller andra typer av hot, men kan utföra åtgärder på slutpunkter som negativt påverkar deras prestanda eller användning. Potentiellt oönskade program syftar även på program med dåligt rykte. Exempel på potentiellt oönskade program är: Olika typer av programvarupaket, AD-inmatning i webbläsare, drivrutins- och registeroptimerare som identifierar problem och begär betalning för att åtgärda felen, men som finns kvar på slutpunkten utan att göra några ändringar eller optimeringar (även kallade ”falska” antivirusprogram). Dessa program kan öka risken för att nätverket infekteras av skadlig kod, orsaka att infektioner av skadlig kod är vara svårare att identifiera och slösa på IT-resurser vid rensning av program.  
  [Läs mer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

  **Standard**: Blockera  

- **Makrokod dold i skriptfiler**:  
  Skadlig kod och andra hot kan försöka förvränga eller dölja skadlig kod i vissa skriptfiler. Den här regeln förhindrar att skript som verkar vara dolda körs.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067026)

  **Standard**: Blockera

- **Sök igenom flyttbara drivrutiner vid fullständig genomsökning**:  
  Tillåter att Microsoft Defender söker efter skadlig och oönskad programvara på flyttbara enheter (till exempel flash-enheter) under en fullständig genomsökning. Microsoft Defender Antivirus söker igenom alla filer på USB-enheter innan de körs.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067036)

  **Standard**: Ja  

- **Sök igenom arkivfiler**:  
  Defender söker igenom arkivfiler.

  **Standard**: Ja

- **Beteendeövervakning**  
  Tillåter eller tillåter inte beteendeövervakning i Microsoft Defender. Dessa sensorer är inbäddade i Windows 10 och samlar in och bearbetar beteendesignaler från operativsystemet samt skickar dessa sensordata till din privata, isolerade molninstans av Microsoft Defender ATP.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067111)

  **Standard**: Ja

- **Sök igenom filer öppnade från nätverksmappar**:  
  Om filerna är skrivskyddade kan användaren inte ta bort identifierad skadlig kod.

  **Standard**: Ja

- **Obetrodd USB-processtyp**:  
  Med den här regeln kan administratörer förhindra att osignerade eller ej betrodda körbara filer körs från flyttbara USB-enheter, till exempel SD-kort.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067100)

  **Standard**: Blockera

- **Annan processinmatningstyp i Office-appar**:  
  Office-appar, inklusive Word, Excel, PowerPoint och OneNote, kan inte mata in kod i andra processer. Detta används vanligtvis av skadlig kod för att köra skadlig kod i ett försök att dölja aktivitet från motorer för virusgenomsökning.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067019)

  **Standard**:  Blockera

- **Office-makrokod tillåter Win32-importer**:  
  Skadlig kod kan använda makrokod i Office-filer för att importera och läsa in Win32-DLL:er, som sedan används för att göra API-anrop som leder till ytterligare infektion hela systemet. Den här regeln försöker blockera Office-filer som innehåller makrokod som kan importera Win32-DLL:er. Detta inkluderar Word, Excel, PowerPoint och OneNote.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067130)

  **Standard**: Blockera

- **Molnblockeringsnivå i Defender**:  
  Molnblockeringsnivå i Defender.

  **Standard**: Inte konfigurerat

- **Realtidsövervakning**:  
  Defender kräver övervakning i realtid.

  **Standard**: Ja

::: zone-end
::: zone pivot="mdm-may-2019"

- **Office-kommunikationsappar startar i en underordnad process**:  
  **Standard**:  Aktivera

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Genererings- eller starttyp för körbart innehåll i Office-appar**:  
  Den här regeln gäller typiska beteenden som används av misstänkta och skadliga tillägg och skript (tillägg) som skapar eller startar körbara filer. Det här är en vanlig teknik som används av skadlig kod. Tillägg hindras från att användas av Office-appar. De här tilläggen använder vanligtvis Windows Scripting Host (.WSH-filer) för att köra skript som automatiserar vissa uppgifter eller tillhandahåller användargenererade tilläggsfunktioner.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067108)

  **Standard**: Blockera

## <a name="ms-security-guide"></a>MS-Säkerhetsguide

Mer information finns i [CSP-princip – MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) i Windows-dokumentationen.

- **Använd UAC-begränsningar för lokala konton vid nätverksinloggning**:  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067188)

  **Standard**: Aktiverad

- **Startkonfiguration för SMB v1-klientdrivrutin**:  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067214)

  **Standard**: Inaktiverad drivrutin

- **SMB v1-server**:  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067190)

  **Standard**: Inaktiverad

- **Sammanfattad autentisering**:  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067193)

  **Standard**: Inaktiverad

- **Strukturerat överskrivningsskydd vid undantagshantering**:  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067217)

  **Standard**: Aktiverad

## <a name="mss-legacy"></a>MSS Legacy

Mer information finns i [CSP-princip – MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) i Windows-dokumentationen.

- **Skyddsnivå för routning för IP-nätverkskälla**:  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067220)

  **Standard**: Högsta skydd  

- **Ignorera begäranden om NetBIOS-namnfrigörande från WINS-servrar i nätverket**:  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067218)

  **Standard**: Aktiverad

- **Skyddsnivå för routning för IPv6-nätverkskälla**:  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067216)

  **Standard**: Högsta skydd

- **ICMP-omdirigeringar åsidosätter OSPF-genererade rutter i nätverket**:  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067326)

  **Standard**: Inaktiverad

## <a name="power"></a>Ström

Mer information finns i [CSP-princip – Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) i Windows-dokumentationen.

- **Kräv lösenord när datorn aktiveras och är ansluten**:  
  Den här principinställningen anger huruvida användaren uppmanas att ange ett lösenord när datorn återgår från strömsparläge. Om du aktiverar eller inte konfigurerar den här principinställningen uppmanas användaren att ange ett lösenord när datorn återgår från strömsparläge. Om du inaktiverar den här principinställningen uppmanas inte användaren att ange ett lösenord när datorn återgår från strömsparläge.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067221)

  **Standard**: Aktiverad

- **Vänteläget aktiveras i viloläge vid batteridrift**:  
  Den här principinställningen hanterar om Windows kan använda väntelägen när datorn försätts i viloläge. Om du aktiverar eller inte konfigurerar den här principinställningen använder Windows väntelägen för att försätta datorn i viloläge. Om du inaktiverar den här principinställningen tillåts inte väntelägen (S1–S3).  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067195)

  **Standard**: Inaktiverad

- **Vänteläget startar när datorn är i viloläge och ansluten**:  
  Den här principinställningen hanterar om Windows kan använda väntelägen när datorn försätts i viloläge. Om du aktiverar eller inte konfigurerar den här principinställningen använder Windows väntelägen för att försätta datorn i viloläge. Om du inaktiverar den här principinställningen tillåts inte väntelägen (S1–S3).  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067196)

  **Standard**: Inaktiverad

- **Kräv lösenord vid aktivering under batteridrift**:  
  Den här principinställningen anger huruvida användaren uppmanas att ange ett lösenord när datorn återgår från strömsparläge. Om du aktiverar eller inte konfigurerar den här principinställningen uppmanas användaren att ange ett lösenord när datorn återgår från strömsparläge. Om du inaktiverar den här principinställningen uppmanas inte användaren att ange ett lösenord när datorn återgår från strömsparläge.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067322)

  **Standard**: Aktiverad

::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="remote-assistance"></a>Fjärrhjälp

Mer information finns i [CSP-princip – RemoteAssistance](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteassistance#remoteassistance-solicitedremoteassistance) i Windows-dokumentationen.

- **Begärd fjärrhjälp**:  
  Med den här principinställningen kan du aktivera eller inaktivera funktionen Begärd fjärrhjälp på den här datorn.
  
  - *Om du aktiverar den här principinställningen* kan de som använder datorn be någon om hjälp via e-post eller filöverföring. Användarna kan också använda program för snabbmeddelanden för att tillåta anslutningar till den här datorn, och du kan konfigurera ytterligare inställningar för Fjärrhjälp.

  - *Om du inaktiverar den här principinställningen* kan de som använder datorn inte be någon om hjälp via e-post eller filöverföring. Användarna kan inte heller utnyttja program för snabbmeddelanden för att tillåta anslutningar till den här datorn.

  - *Om du inte konfigurerar den här principinställningen* kan användarna aktivera eller inaktivera Begärd fjärrhjälp själva i Systemegenskaper på Kontrollpanelen. Användarna kan också konfigurera inställningar för Fjärrhjälp.

  Om du aktiverar den här policyinställningen har du två sätt att tillåta Fjärrhjälp: ”Låt handledare endast se datorn” eller ”Låt handledare fjärrstyra datorn”. Principinställningen Högsta biljettid anger hur länge en fjärrhjälpsinbjudan skapad via e-post eller filöverföring, är giltig. Inställningen Metod för att skicka inbjudningar via e-post anger vilken e-poststandard som ska användas när en fjärrhjälpsinbjudan skickas. Beroende på vilket e-postprogram som används kan du använda protokollet *Mailto* (mottagaren ansluter genom en vanlig Internetlänk) eller protokollet SMAPI (inbjudan bifogas i ett e-postmeddelande). Den här principinställningen är inte tillgänglig i Windows Vista eftersom SMAPI är den enda metod som stöds. Om du aktiverar den här principinställningen bör du även aktivera tillämpliga brandväggsundantag för att tillåta fjärrhjälpkommunikation.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Standard**: Inaktivera Fjärrhjälp

  När *Aktivera Fjärrhjälp* har angetts konfigurerar du ytterligare inställningar:

  - **Fjärrhjälp bad om behörighet**:  
    **Standard**: Vy

  - **Högsta biljettid, värde**:  
    **Standard**: *Inte konfigurerat*

  - **Högsta biljettid, period**:  
    **Standard**: Minuter

  - **Metod för e-postinbjudan**:  
    **Standard**: Enkel MAPI

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="remote-desktop-services"></a>Fjärrskrivbordstjänster

Mer information finns i [CSP-princip – RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) i Windows-dokumentationen.

- **Tillåt inte att lösenord sparas**:  
  Styr om lösenord kan sparas på den här datorn från Anslutning till fjärrskrivbord. Om du aktiverar den här inställningen inaktiveras kryssrutan om att spara lösenord i Anslutning till fjärrskrivbord, och användarna kan inte längre spara lösenord. När en användare öppnar en RDP-fil med hjälp av Anslutning till fjärrskrivbord och sparar sina inställningar tas eventuella lösenord som tidigare fanns i RDP-filen bort. Om du inaktiverar den här inställningen eller inte konfigurerar den kan användaren spara lösenord med hjälp av Anslutning till fjärrskrivbord.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067301)

   **Standard**: Aktiverad

- **Säker RPC-kommunikation**:  
  Anger om en värdserver för fjärrskrivbordssessioner kräver säker RPC-kommunikation med alla klienter eller om osäker kommunikation tillåts. Du kan använda den här inställningen för att öka säkerheten vid RPC-kommunikation med klienter genom att endast tillåta autentiserade och krypterade begäranden. Om statusen är inställd på Aktiverad accepterar Fjärrskrivbordstjänster begäranden från RPC-klienter som stöder säkra begäranden och tillåter inte osäker kommunikation med obetrodda klienter. Om statusen är inställd på Inaktiverad begär Fjärrskrivbordstjänster alltid säkerhet för all RPC-trafik. Osäker kommunikation tillåts dock för RPC-klienter som inte svarar på begäran. Om statusen är inställd på Inte konfigurerad tillåts osäker kommunikation. Obs! RPC-gränssnittet används för att administrera och konfigurera Fjärrskrivbordstjänster.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067248)

  **Standard**: Aktiverad

- **Blockera omdirigering av enheter**:  
  Med den här principinställningen kan du ange om du vill förhindra mappningen av klientenheter i en session med Fjärrskrivbordstjänster (omdirigering). Som standard mappar en värdserver för fjärrskrivbordssessioner automatiskt klientenheter när anslutningen upprättas. Mappade enheter visas i trädet för sessionsmappar i Utforskaren eller på datorn i formatet *\<enhetsbeteckning >* på *\<datornamn>* . Du kan använda den här principinställningen om du vill åsidosätta detta beteende. Om du aktiverar den här principinställningen tillåts inte omdirigering av klientenheter i sessioner med Fjärrskrivbordstjänster och omdirigeringar av filkopiering med Urklipp tillåts inte på datorer som kör Windows Server 2003, Windows 8 och Windows XP. Om du inaktiverar den här principinställningen tillåts alltid omdirigering av klientenheter. Dessutom tillåts alltid omdirigering av filkopiering med Urklipp om omdirigering av Urklipp är tillåtet. Om du inte konfigurerar den här principinställningen anges inte omdirigering av klientenheter och omdirigering av filkopiering med Urklipp på grupprincipnivå.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067197)

  **Standard**: Aktiverad

- **Fråga efter lösenord vid anslutning**:  
  Den här principinställningen anger om Fjärrskrivbordstjänster alltid frågar klienten efter ett lösenord när anslutningen upprättas. Du kan använda den här inställningen för att framtvinga en lösenordsfråga för användare som loggar in i Fjärrskrivbordstjänster, även om de redan har angett lösenordet i Anslutning till fjärrskrivbord-klienten. Som standard tillåter Fjärrskrivbordstjänster användarna att logga in automatiskt genom att ange ett lösenord i Anslutning till fjärrskrivbord-klienten. Om du aktiverar den här principinställningen kan användarna inte logga in automatiskt i Fjärrskrivbordstjänster genom att ange lösenord i Anslutning till fjärrskrivbord-klienten. De uppmanas att ange ett lösenord för att logga in. Om du inaktiverar den här principinställningen kan användarna alltid logga in i Fjärrskrivbordstjänster automatiskt genom att ange lösenord i Anslutning till fjärrskrivbord-klienten. Om du inte konfigurerar den här principinställningen anges inte automatisk inloggning på grupprincipnivå.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067328)

  **Standard**: Aktiverad

- **Krypteringsnivå för klientanslutning med Fjärrskrivbordstjänster**:  
  Anger om du vill kräva en specifik krypteringsnivå för att skydda kommunikationen mellan klientdatorer och värdservrar för fjärrskrivbordssessioner under RDP-anslutningar (Remote Desktop Protocol). Den här principen gäller bara när du använder inbyggd RDP-kryptering. Inbyggd RDP-kryptering (till skillnad mot SSL-kryptering) rekommenderas dock inte. Den här principen gäller inte för SSL-kryptering. Om du aktiverar den här principinställningen måste all kommunikation mellan klienter och värdservrar för fjärrskrivbordssessioner under fjärranslutningar använda krypteringsmetoden som anges i den här inställningen. Som standard är krypteringsnivån inställd på Hög. Följande krypteringsmetoder är tillgängliga:

  - *Hög* – Med inställningen Hög krypteras data som skickas från klienten till servern och från servern till klienten med hjälp av stark 128-bitarskryptering. Använd den här krypteringsnivån i miljöer som bara innehåller 128-bitarsklienter (till exempel klienter som kör Anslutning till fjärrskrivbord). Klienter som inte stöder den här krypteringsnivån kan inte ansluta till värdservrar för fjärrskrivbordssessioner.

  - *Klientkompatibel* – Med inställningen Klientkompatibel krypteras data som skickas mellan klienten och servern med den högsta nyckellängden som stöds av klienten. Använd den här krypteringsnivån i miljöer som inkluderar klienter som inte stöder 128-bitarskryptering.

  - *Låg* – Med inställningen Låg krypteras endast data som skickas från klienten till servern med hjälp av 56-bitarskryptering.  
  
  Om du inaktiverar eller inte konfigurerar den här inställningen tillämpas inte krypteringsnivån som ska användas för fjärranslutningar till värdservrar för fjärrskrivbordssessioner via en grupprincip. Viktigt! FIPS-kompatibilitet kan konfigureras via Systemkryptografi. Använd FIPS-kompatibla algoritmer för krypterings-, hashing- och signeringsinställningar i Grupprincip (under Datorkonfiguration\Windows-inställningar\Säkerhetsinställningar\Lokala principer\Säkerhetsalternativ.) Inställningen FIPS-kompatibel krypterar och dekrypterar data som skickas från klienten till servern och från servern till klienten med FIPS 140-krypteringsalgoritmerna (Federal Information Processing Standard) med hjälp av Microsofts kryptografiska moduler. Använd den här krypteringsnivån när kommunikation mellan klienter och värdservrar för fjärrskrivbordssessioner kräver högsta krypteringsnivå.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067222)

  **Standard**: Hög

## <a name="remote-management"></a>Fjärrhantering

Mer information finns i [CSP-princip – RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) i Windows-dokumentationen.

- **Blockera lagring av körning som autentiseringsuppgifter**:  
  Grundläggande klientautentisering.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067300)

  **Standard**: Aktiverad

- **Grundläggande autentisering**:  
  Med den här principinställningen kan du ange om tjänsten WinRM (Windows Remote Management) accepterar grundläggande autentisering från en fjärransluten klient. Om du aktiverar den här principinställningen accepterar WinRM-tjänsten grundläggande autentisering från en fjärransluten klient. Om du inaktiverar eller inte konfigurerar den här principinställningen accepterar WinRM-tjänsten inte grundläggande autentisering från en fjärransluten klient.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067223)

  **Standard**: Inaktiverad

- **Blockera sammanfattad autentisering för klient**:  
  Med den här inställningen kan du ange om WinRM-klienten (Windows Remote Management) använder sammanfattad autentisering. Om du aktiverar den här principinställningen använder inte WinRM-klienten sammanfattad autentisering. Om du inaktiverar eller inte konfigurerar den här principinställningen använder WinRM-klienten sammanfattad autentisering.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067302)

  **Standard**: Aktiverad

- **Okrypterad trafik**:  
  Med den här principinställningen kan du ange om tjänsten WinRM (Windows Remote Management) skickar och tar emot okrypterade meddelanden över nätverket. Om du aktiverar den här principinställningen skickar och tar WinRM-klienten emot okrypterade meddelanden över nätverket. Om du inaktiverar eller inte konfigurerar den här principinställningen skickar eller tar WinRM-klienten endast emot krypterade meddelanden över nätverket.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067226)

  **Standard**: Inaktiverad

- **Okrypterad klienttrafik**:  
  Med den här principinställningen kan du ange om klienten WinRM (Windows Remote Management) ska skicka och ta emot okrypterade meddelanden över nätverket. Om du aktiverar den här principinställningen skickar och tar WinRM-klienten emot okrypterade meddelanden över nätverket. Om du inaktiverar eller inte konfigurerar den här principinställningen skickar eller tar WinRM-klienten endast emot krypterade meddelanden över nätverket.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067304)

  **Standard**: Inaktiverad

- **Grundläggande klientautentisering**:  
  Med den här inställningen kan du ange om WinRM-klienten (Windows Remote Management) använder grundläggande autentisering. Om du aktiverar den här principinställningen använder WinRM-klienten grundläggande autentisering. Om WinRM har konfigurerats att använda HTTP-transport skickas användarnamnet och lösenordet över nätverket i klartext. Om du inaktiverar eller inte konfigurerar den här principinställningen använder inte WinRM-klienten grundläggande autentisering.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067252)

  **Standard**: Inaktiverad

## <a name="remote-procedure-call"></a>RPC (Remote Procedure Call)

Mer information finns i [CSP-princip – RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) i Windows-dokumentationen.

- **Alternativ för oautentiserad klient med RPC**:  
  Den här principinställningen styr hur RPC-serverkörningar hanterar oautentiserade RPC-klienter som ansluter till RPC-servrar. Den här principinställningen påverkar alla RPC-program. I en domänmiljö ska den här principinställningen används med försiktighet eftersom den kan påverka en mängd olika funktioner, inklusive själva bearbetningen av grupprinciper. Återställning av ändringar i den här principinställningen kan kräva manuella åtgärder på varje dator som påverkas. Tillämpa inte den här principinställningen på en domänkontrollant. Om du inaktiverar den här inställningen använder RPC-serverkörningen värdet ”Autentiserad” på Windows-klienten och värdet ”Ingen” i Windows Server-versioner som stöder den här principinställningen. Om du inte konfigurerar den här principinställningen förblir den inaktiverad. RPC-serverkörningen beter sig som om den vore aktiverad med värdet ”Autentiserad” för Windows-klienter och värdet ”Ingen” för Server-SKU:er som har stöd för den här principinställningen. Om du aktiverar den här principinställningen beordras RPC-serverkörningen att begränsa oautentiserade RPC-klienter som ansluter till RPC-servrar på en dator. En klient betraktas som en autentiserad klient om den använder en namngiven pipe för att kommunicera med servern eller om den använder RPC-säkerhet. RPC-gränssnitt som uttryckligen har begärt att vara tillgängliga för oautentiserade klienter kan undantas från den här begränsningen, beroende på det valda värdet för den här principinställningen.

  - *Ingen* gör att alla RPC-klienter kan ansluta till RPC-servrar som körs på den dator där principinställningen tillämpas.

  - *Autentiserad* tillåter endast att autentiserade RPC-klienter (enligt definitionen ovan) ansluter till RPC-servrar som körs på den dator där principinställningen tillämpas. Undantag beviljas till gränssnitt som har begärt dem.

  - *Autentiserad utan undantag* tillåter endast att autentiserade RPC-klienter (enligt definitionen ovan) ansluter till RPC-servrar som körs på den dator där principinställningen tillämpas. Inga undantag tillåts. Obs! Den här principinställningen tillämpas inte förrän systemet startas om.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067225)

  **Standard**: Autentiserad

## <a name="search"></a>Sök

Mer information finns i [CSP-princip – Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) i Windows-dokumentationen.

- **Inaktivera indexering av krypterade objekt**:  
  Tillåter eller nekar indexering av objekt. Den här växeln används för Windows Search-indexeraren och styr om objekt som är krypterade indexeras, till exempel WIP-skyddade filer (Windows Information Protection). När principen är aktiverad indexeras Windows informationsskyddade objekt och deras metadata lagras på en okrypterad plats. Dessa metadata innehåller exempelvis ändrade sökvägar och datum. När principen är inaktiverad indexeras inte WIP-skyddade objekt, och resultaten visas inte i Cortana eller Utforskaren. Det kan också förekomma en prestandapåverkan på foton och Groove-appar om det finns många Windows informationsskyddade mediefiler på enheten.  
  [Läs mer]( https://go.microsoft.com/fwlink/?linkid=2067303)

  **Standard**: Ja

## <a name="smart-screen"></a>Smart skärm

Mer information finns i [CSP-princip – SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) i Windows-dokumentationen.

- **Blockera körning av overifierade filer**:  
  Blockera användare från att köra overifierade filer.

  - *Inte konfigurerat* – Medarbetare kan ignorera SmartScreen-varningar och köra skadliga filer.

  - *Ja* – Medarbetare kan inte ignorera SmartScreen-varningar och köra skadliga filer.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067228)

  **Standard**: Ja

- **Kräv SmartScreen för appar och filer**:  
  Gör det möjligt för IT-administratörer att konfigurera SmartScreen för Windows.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067168)

  **Standard**: Ja

## <a name="system"></a>System

Mer information finns i [CSP-princip – System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) i Windows-dokumentationen.

- **Initiering av startdrivrutiner för systemstart**:  
  Med den här principinställningen kan du ange vilka startdrivrutiner för systemstart som ska initieras baserat på en klassificering som bestäms av en ELAM-startdrivrutin (Early Launch Antimalware). ELAM-startdrivrutinen (Early Launch Antimalware) kan returnera följande klassificeringar för varje startdrivrutin:

  - *Bra* – Drivrutinen har signerats och har inte manipulerats.

  - *Dålig* – Drivrutinen har identifierats som skadlig kod. Vi rekommenderar att du inte tillåter att kända skadliga drivrutiner initieras.

  - *Dålig men krävs för start* – Drivrutinen har identifierats som skadlig kod, men måste läsas in för att datorn ska kunna starta korrekt.

  - *Okänd* – Drivrutinen har inte utvärderats av ditt program för identifiering av skadlig kod och har inte klassificerats av ELAM-startdrivrutinen.

  Om du aktiverar den här principinställningen kan du välja vilka startdrivrutiner som ska initieras nästa gång datorn startas. Om du inaktiverar eller inte konfigurerar den här principinställningen initieras startdrivrutiner som har bedömts vara bra, okända eller dåliga, men nödvändiga för systemstart och initieringen av drivrutiner som har bedömts vara dåliga hoppas över. Om ditt program för identifiering av skadlig kod inte inkluderar en ELAM-startdrivrutin eller om ELAM-startdrivrutinen har inaktiverats har den här inställningen ingen effekt och alla startdrivrutiner initieras.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067307)

  **Standard**: Bra, okänd och dålig men nödvändig

## <a name="wi-fi"></a>Wi-Fi

Mer information finns i [CSP-princip – Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) i Windows-dokumentationen.

- **Blockera Internetdelning**:  
  Anger om Internetdelning är möjligt på enheten.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067327)

  **Standard**: Ja

- **Blockera automatiskt anslutning till Wi-Fi-hotspot**:  
  Tillåt eller förhindra att enheten ansluter automatiskt till en Wi-Fi-hotspot.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067320)

  **Standard**: Ja

## <a name="windows-connection-manager"></a>Windows Connection Manager

Mer information finns i [CSP-princip – WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) i Windows-dokumentationen.

- **Blockera anslutning till icke-domänbaserade nätverk**:  
  Den här principinställningen förhindrar att datorer ansluter till både ett domänbaserat nätverk och ett icke-domänbaserat nätverk på samma gång. Om den här principinställningen är aktiverad svarar datorn på automatiska och manuella anslutningsförsök baserat på följande villkor:

  - *Automatiska anslutningsförsök* – Om datorn redan är ansluten till ett domänbaserat nätverk blockeras alla automatiska anslutningsförsök till icke-domänbaserade nätverk. Om datorn redan är ansluten till ett icke-domänbaserat nätverk blockeras automatiska anslutningsförsök till domänbaserade nätverk.

  - *Manuella anslutningsförsök* – Om datorn redan är ansluten till antingen ett icke-domänbaserat nätverk eller till ett domänbaserat nätverk över ett annat medium än Ethernet, och en användare försöker skapa en manuell anslutning till ytterligare ett nätverk i strid med den här principinställningen, kopplas den befintliga nätverksanslutningen från och den manuella anslutningen tillåts. Om datorn redan är ansluten till antingen ett icke-domänbaserat nätverk eller till ett domänbaserat nätverk över Ethernet, och en användare försöker skapa en manuell anslutning till ytterligare ett nätverk i strid mot den här principinställningen, upprätthålls den befintliga Ethernet-anslutningen och det manuella anslutningsförsöket blockeras.

  Om den här inställningen inte konfigureras eller om den inaktiveras kan datorer ansluta samtidigt till både domänbaserade nätverk och icke-domänbaserade nätverk.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067323)

  **Standard**: Aktiverad

::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="windows-hello-for-business"></a>Windows Hello för företag

- **Aktivera om du vill använda utökat skydd mot förfalskning när det är tillgängligt**

  Om Ja, används utökat skydd mot förfalskning på enheterna när det är tillgängligt. Om Nej, blockeras skydd mot förfalskning. Om det inte är konfigurerat gäller de inställningar som gjorts på klienten.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067192)

  **Standard**: Ja

- **Konfigurera Windows Hello för företag**

  Windows Hello för företag är en alternativ metod för att logga in till Windows genom att ersätta lösenord, smartkort och virtuella smartkort.

  > [!IMPORTANT]
  > Alternativen blir felaktiga för den här inställningen (omvända). Värdet *Ja* aktiverar inte Windows Hello när inställningarna är omvända utan hanteras som *Inte konfigurerad*. När *Inte konfigurerad* har angetts aktiveras Windows Hello på enheter som får den här baslinjen.
  >
  > Följande beskrivningar har ändrats för att återspegla detta beteende. De omvända inställningarna kommer att åtgärdas i en framtida uppdatering av den här säkerhetsbaslinjen.

  - När *Inte konfigurerad* har angetts är Windows Hello aktiverat och enheten etablerar Windows Hello för företag.
  - När *Ja* har angetts påverkar baslinjen inte principinställningen för enheten. Det innebär att om Windows Hello för företag är inaktiverat på en enhet förblir det inaktiverat. Och om det är aktiverat förblir det aktiverat.
  <!-- expected behavior 
  - When set to *Yes*, you  enable this policy and the device provisions Windows Hello for Business.  
  - When set to *Not configured*, the baseline does not affect the policy setting of the device. This means that if Windows Hello for Business is disabled on a device, it remains disabled. If its enabled, it remains enabled. 
  -->

  Du kan inte inaktivera Windows Hello för företag via den här baslinjen. Du kan inaktivera Windows Hello för företag när du konfigurerar [Windows-registrering](windows-hello.md), eller som en del i enhetskonfigurationsprofilen för [identitetsskydd](identity-protection-configure.md).  

  **Standard**: Ja

- **Kräv gemener i PIN-koden**:  
  Om alternativet krävs måste användarens PIN-kod innehålla minst en liten bokstav.

  **Standard**: Tillåts

- **Kräv specialtecken i PIN-koden**:  
  Om alternativet krävs måste användarens PIN-kod innehålla minst ett specialtecken.

  **Standard**: Tillåts

- **Minimilängd för PIN-kod**:  
  Minimilängd för PIN-kod måste vara mellan 4 och 127.

  **Standard**: 6

- **Kräv versaler i PIN-koden**:  
  Om alternativet krävs måste användarens PIN-kod innehålla minst en stor bokstav.

  **Standard**: Tillåts

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="windows-ink-workspace"></a>Windows Ink-arbetsytan

Mer information finns i [CSP-princip – WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) i Windows-dokumentationen.

- **Ink-arbetsytan**:  
  Anger huruvida användaren ska få åtkomst till Ink-arbetsytan.

  - *Inaktiverat* – åtkomsten till ink-arbetsytan är inaktiverad. Funktionen är inaktiverad.

  - *Aktiverat* – funktionen för ink-arbetsyta är aktiverad, men användaren kan inte komma åt den på låsskärmen.

  - *Inte konfigurerad* – Funktionen för ink-arbetsyta är aktiverad, och användaren kan använda den ovanpå låsskärmen.

  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067241)

  **Standard**: Aktiverad

## <a name="windows-powershell"></a>Windows PowerShell

Mer information finns i [CSP-princip – WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) i Windows-dokumentationen.

- **Loggning av skriptblock i PowerShell-gränssnittet**:  
  Den här inställningen aktiverar loggning av alla PowerShell-skriptindata i Microsoft-Windows-PowerShell/Operational-händelseloggen. Om du aktiverar den här principinställningen loggar Windows PowerShell bearbetningen av kommandon, skriptblock, funktioner och skript – oavsett om de anropas interaktivt eller via automatisering. Om du inaktiverar den här principinställningen inaktiveras loggning av PowerShell-skriptindata. Om du aktiverar loggning av indata av skriptblock loggar PowerShell även händelser om anrop av ett kommando, skriptblock, funktion eller skript startar eller stoppar. Om du aktiverar loggning av anrop genereras ett stort antal händelseloggar. Obs! Den här principinställningen finns under både Datorkonfiguration och Användarkonfiguration i redigeraren för grupprinciper. Principinställningen Datorkonfiguration ges företräde framför principinställningen Användarkonfiguration.  
  [Läs mer](https://go.microsoft.com/fwlink/?linkid=2067330)

  **Standard**: Aktiverad

::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="whats-changed-in-the-new-template"></a>Ändringar i den nya mallen

Följande ändringar har gjorts i mallen *Säkerhetsbaslinje för mobilenhetshantering för maj 2019* från *förhandsversionen*.

### <a name="changes-to-the-baseline-settings"></a>Ändringar i baslinjeinställningarna

Följande inställningar är antingen:

- *Nytt* i den senaste versionen av baslinjen.
- *Har tagits bort* från den senaste baslinjeversionen, men fanns i den tidigare versionen.
- *Har ändrats* på något sätt jämfört med hur inställningarna visades i den tidigare versionen.

*[Nytt]* [**På låsskärmen**](#above-lock):

- **Röstaktivera appar från en låst skärm**

*[Nytt]* [**Programhantering**](#application-management):

- **Blockera användarkontroll över installationer**
- **Blockera MSI-appinstallationer med utökade privilegier**

*[Borttaget]* [**BitLocker**](#bitlocker):

- Princip för BitLocker på flyttbara enheter > **Krypteringsmetod**
- **Princip för BitLocker på fasta enheter** *(alla inställningar)*
- **Princip för BitLocker på systemenheter** *(alla inställningar)*

*[Nytt]* [**Anslutningar**](#connectivity):

- **Konfigurera säker åtkomst till UNC-sökvägar**

*[Nytt]* [**Device Guard**](#device-guard):

- **Virtualiseringsbaserad säkerhet**

*[Nytt]* [**DMA Guard**](#dma-guard):

- **Uppräkning av externa enheter som är inkompatibla med Kernel DMA-skydd**

*[Nytt]* [**Internet Explorer**](#internet-explorer):

- **Internet Explorer internet zone updates to status bar via script** (Internet Explorer: uppdateringar av statusfältet via skript i zonen Internet)
- **Internet Explorer: dra eller kopiera och klistra in filer i zonen Internet**
- **Internet Explorer: .NET Framework-beroende komponenter i zonen Begränsad**
- **Internet Explorer: kör inte program mot skadlig kod mot Active X-kontroller i zonen Lokal dator**
- **Krypteringsstöd för Internet Explorer**

*[Ändrad]* [**Internet Explorer**](#internet-explorer):

- **Internet Explorer: fråga automatiskt vid filnedladdningar i zonen Internet** > standardvärdet är nu **Inaktiverat**. I förhandsversionen var inställningen Aktiverat.

*[Nytt]* [**Fjärrhjälp**](#remote-assistance):

- **Begärd fjärrhjälp**
  - **Fjärrhjälp bad om behörighet**
  - **Högsta biljettid, värde**
  - **Högsta biljettid, period**
  - **Metod för e-postinbjudan**

*[Nytt]* [**Microsoft Defender**](#microsoft-defender):

- **Adobe Reader-start i en underordnad process**
- **Office-kommunikationsappar startar i en underordnad process**

*[Nytt]* [**Brandvägg**](#firewall)

- **Domän för brandväggsprofil**
  - **Inkommande anslutningar blockerade**
  - **Utgående anslutningar krävs**
  - **Inkommande meddelanden blockerade**
  - **Brandväggen är aktiverad**
- **Offentlig brandväggsprofil**
  - **Inkommande anslutningar blockerade**
  - **Utgående anslutningar krävs**
  - **Inkommande meddelanden blockerade**
  - **Brandväggen är aktiverad**
  - **Regler för anslutningssäkerhet från inte sammanfogad grupprincip**
  - **Principregler från inte sammanfogad grupprincip**
- **Privat brandväggsprofil**
  - **Inkommande anslutningar blockerade**
  - **Utgående anslutningar krävs**
  - **Inkommande meddelanden blockerade**
  - **Brandväggen är aktiverad**

*[Nytt]* [**Windows Hello för företag**](#windows-hello-for-business):

- **Kräv utökat skydd mot förfalskning när det är tillgängligt**
- **Konfigurera Windows Hello för företag**
- **Kräv gemener i PIN-koden**
- **Kräv specialtecken i PIN-koden**
- **Minimilängd för PIN-kod**
- **Kräv versaler i PIN-koden**

::: zone-end
