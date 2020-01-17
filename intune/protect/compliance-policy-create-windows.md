---
title: Kompatibilitetsinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du konfigurerar kompatibilitet för Windows 10-, Windows Holographic- och Surface Hub-enheter i Microsoft Intune. Kontrollera kompatibiliteten för lägsta och högsta operativsystemversion, ange begränsningar och längd för lösenord, kontrollera om det finns antiviruslösningar från tredje part, aktivera kryptering för datalagring och mer.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ca5d475f92cbe3298689273dcdf0da1644078b2
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547042"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Inställningar för Windows 10 och senare för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

Den här artikeln innehåller en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på Windows 10-enheter och senare enheter i Intune. Som en del av din MDM-lösning för hantering av mobilenheter kan du använda dessa inställningar för att kräva BitLocker, ange en lägsta och högsta operativsystemversion, ange en risknivå med hjälp av Microsoft Defender Advanced Threat Protection (ATP) och mycket mer.

Den här funktionen gäller för:

- Windows 10 och senare
- Windows 10 Holographic for Business
- Surface Hub

Som Intune-administratör kan du använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Mer om kompatibilitetsprinciper och vad de gör finns i [Komma igång med kompatibilitet](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). För **Plattform** väljer du **Windows 10 och senare**.

## <a name="device-health"></a>Enhetens hälsotillstånd

### <a name="windows-health-attestation-service-evaluation-rules"></a>Utvärderings regler för tjänsten Windows Health attestering

- **Kräv BitLocker**:  
   Med Windows BitLocker-diskkryptering krypteras alla data på volymen för Windows-operativsystemet. BitLocker använder Trusted Platform Module (TPM) för att skydda Windows-operativsystemet och användar data. Det kan också bekräfta att en dator inte manipuleras, även om den lämnas obevakad, tappas bort eller blir stulen. Om datorn är utrustad med en kompatibel TPM använder BitLocker TPM för att låsa krypteringsnycklarna som skyddar data. Därför är nycklarna inte tillgängliga förrän TPM verifierar datorns tillstånd.  

   - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
   - **Kräv** – Enheten skydda data som lagras på enheten mot obehörig åtkomst när systemet är avstängt eller i viloläge.  


- **Kräv att säker start ska vara aktiverat på enheten**:  
    - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
    - **Kräv** – systemet måste tvingas att starta till en fabriks betrott tillstånd. Huvudkomponenterna som används för att starta datorn dessutom ha rätt kryptografiska signaturer som är betrodda av den organisation som tillverkade enheten. UEFI-baserad inbyggd programvara kontrollerar signaturen innan den låter datorn starta. Om filer har manipulerats, vilket delar deras signatur, kan systemet inte starta om.

  > [!NOTE]
  > Inställningen **Kräv att säker start är aktiverat på enheten** stöds på vissa TPM 1.2- och 2.0-enheter. För enheter som inte stöder TPM 2.0 eller senare, visas principstatusen i Intune som **Ej ompatibel**. Mer information om vilka versioner som stöds finns i [Hälsoattestering för enhet](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Kräv kodintegritet**:  
  Kodintegritet är en funktion som kontrollerar integriteten för en drivrutin eller systemfil varje gång de läses in i minnet.
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  -  **Kräv** – Kräv kodintegritet, som upptäcker om en osignerad drivrutin eller systemfil läses in i kerneln. Den upptäcker också om en systemfil ändras av skadlig programvara eller körs av ett användarkonto med administratörsbehörighet.

Fler resurser:

- Mer information om hur tjänsten hälsoattestering fungerar finns i CSP för [hälsoattestering](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Tips för support: Använda Hälsoattestering för enhet som en del av din Intune-kompatibilitetsprincip](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643).

## <a name="device-properties"></a>Egenskaper för enhet

### <a name="operating-system-version"></a>Operativsystemversion

- **Lägsta version av operativsystemet**:  
  Ange den lägsta tillåtna versionen i formatet **major.minor.build.CU**. Öppna en kommandotolk och skriv `ver` för att visa det korrekta värdet. Kommandot `ver` returnerar versionen i följande format:

  `Microsoft Windows [Version 10.0.17134.1]`

  Om en enhet har en tidigare version än operativsystemsversionen du anger rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändarna kan välja att uppgradera sina enheter. När de har uppgraderat har de åtkomst till företagsresurser.

- **Högsta version av operativsystemet**:  
  Ange den högsta tillåtna versionen i formatet **major.minor.build.revision**. Öppna en kommandotolk och skriv `ver` för att visa det korrekta värdet. Kommandot `ver` returnerar versionen i följande format:

  `Microsoft Windows [Version 10.0.17134.1]`

  När en enhet använder en senare operativsystemversion än den version som har angett blockeras åtkomsten till organisationens resurser. Slutanvändaren uppmanas att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän regeln ändras så att operativsystemversionen tillåts.

- **Lägsta version av operativsystemet som krävs för mobila enheter**:  
  Ange den lägsta tillåtna versionen i formatet major.minor.versionsnummer.

  Om en enhet har en tidigare version än operativsystemsversionen du anger rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändarna kan välja att uppgradera sina enheter. När de har uppgraderat har de åtkomst till företagsresurser.

- **Högsta version av operativsystemet som krävs för mobila enheter**:  
  Ange den högsta tillåtna versionen enligt major.minor.versionsnummer.

  När en enhet använder en senare operativsystemversion än den version som har angett blockeras åtkomsten till organisationens resurser. Slutanvändaren uppmanas att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän regeln ändras så att operativsystemversionen tillåts.

- **Giltiga operativsystemversioner**:  
  Ange ett intervall för godkända operativsystemversioner, inklusive ett minimum och maximum. Du kan också **exportera** en lista med kommaavgränsade värden över dessa godkända OS-versionsnummer i en CSV-fil.

## <a name="configuration-manager-compliance"></a>Configuration Manager-kompatibilitet

Gäller enbart för samhanterade enheter som kör Windows 10 och senare. Enheter med enbart Intune returnerar statusen inte tillgänglig.

- **Kräv att enheten följer Configuration Manager**:  
  - **Inte konfigurerad** (*standard*) – Intune gör inte några kompatibilitetskontroller av inställningarna i Configuration Manager.
  - **Kräv** – Kräv att alla inställningar (konfigurationsobjekt) i Configuration Manager följer standard.  

    Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd är enheten inte kompatibel i Intune.

## <a name="system-security"></a>Systemsäkerhet

### <a name="password"></a>lösenordsinställning

- **Kräv ett lösenord för att låsa upp mobila enheter**:  
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** – Användarna måste ange ett lösenord innan de får åtkomst till sina enheter. 

- **Enkla lösenord**:  
  - **Inte konfigurerad** (*standard*) – användare kan skapa enkla lösen ord, till exempel **1234** eller **1111**.
  - **Blockera** – Användarna kan inte skapa enkla lösenord, som exempelvis **1234** eller **1111**.

- **Lösenordstyp**:  
  Välj typ av lösenord eller PIN-kod. Alternativen är:
  - **Enhets standard** (*standard*) – Kräv ett lösen ord, en numerisk PIN-kod eller en alfanumerisk PIN-kod
  - **Numeriskt** – Kräv ett lösen ord eller en numerisk PIN-kod
  - **Alfanumerisk** – Kräv ett lösen ord eller en alfanumerisk PIN-kod.  
  
  När värdet är *alfanumeriskt*är följande inställningar tillgängliga:  
  - **Lösenordskomplexitet**:  
    Alternativen är: 
    - **Kräv siffror och gemener** (*standard*)
    - **Kräv siffror, gemener och versaler**
    - **Siffror, gemener, versaler och specialtecken krävs.**

    > [!TIP]
    > De alfanumeriska lösen ords principerna kan vara komplexa. Vi uppmuntrar administratörer att läsa kryptografiproviders för mer information:
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Minsta lösenordslängd**:  
  Ange det minsta antal siffror eller tecken som lösenordet måste innehålla.

- **Maximalt antal minuters inaktivitet innan lösenord krävs**:  
  Ange efter hur lång tids inaktivitet som användaren måste ange sitt lösenord igen.

- **Lösenordets giltighetstid (dagar)** :  
  Ange antalet dagar tills lösenordet upphör att gälla och användaren måste skapa ett nytt. Värdet kan vara 1-730.

- **Antal tidigare lösenord för att förhindra återanvändning**:  
  Ange antal tidigare använda lösenord som inte får återanvändas.

- **Kräv lösenord när enheten återgår från viloläge (Mobile och Holographic)** :  
  - **Ej konfigurerat** (*standard*)
  - **Kräv** – Kräv att enhetens användare anger lösenordet varje gång som enheten lämnar inaktivt läge.

  > [!IMPORTANT]
  > När lösenordskravet ändras på ett Windows-skrivbord påverkas användarna nästa gång de loggar in, eftersom det är då enheten går från inaktiv till aktiv. Användare med lösenord som uppfyller kravet uppmanas ändå att ändra sina lösenord.

### <a name="encryption"></a>Kryptering

- **Kryptering av datalagring på en enhet**:  
  Den här inställningen gäller för alla enheter på en enhet.
  - **Ej konfigurerat** (*standard*)
  - **Kräv** – Använd *Kräv* när du ska kryptera datalagring på dina enheter.

  > [!NOTE]
  > Inställningen **Kryptering för lagring av data på en enhet** kontrollerar om kryptering används på enheten. Om du behöver en starkare krypteringsinställning bör du överväga att använda **Kräv BitLocker**, som använder Attestering för Windows-enhetens hälsotillstånd för att verifiera Bitlocker-status på TPM-nivå.

### <a name="device-security"></a>Enhetssäkerhet  

- **Brandvägg**:  
  - **Inte konfigurerat** (*standard*) – Intune styr inte Microsoft Defender-brandväggen eller ändra befintliga inställningar.
  - **Kräv** – aktivera Microsoft Defender-brandväggen och förhindra att användare stänger av den.  

  [Brand vägg CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Om enheten omedelbart synkroniseras efter en omstart eller om synkroniseringen genast aktive ras från vilo läge, kan den här inställningen rapportera **fel**. Det här scenariot kanske inte påverkar den övergripande status för enhetens efterlevnad. [Synkronisera enheten](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)manuellt om du vill utvärdera kompatibilitetsstatus igen.

- **Trusted Platform Module (TPM)** :  
  - **Inte konfigurerat** (*standard*) – Intune kontrollerar inte enheten för en TPM-krets-version.
  - **Kräv** -INTUNE kontrollerar TPM-chipet för efterlevnad. Enheten är kompatibel om TPM-chipets version är större än **0** (noll). Enheten är inte kompatibel om det inte finns någon TPM-version på enheten.  

  [DeviceStatus CSP-DeviceStatus/TPM/SpecificationVersion Node](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivirus**:  
  - **Ej konfigurerad** (*standard*) – Intune kontrollerar inte om några antiviruslösningar har installerats på enheten. 
  - **Kräv** – Kontrollera efterlevnaden med hjälp av antiviruslösningar som har registrerats i [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), exempelvis Symantec och Microsoft Defender.

- **Antispionprogram**:  
  - **Ej konfigurerat** (*standard*) – Intune kontrollerar inte om några antspionslösningar har installerats på enheten.
  - **Kräv** – Kontrollera efterlevnaden med hjälp av antispionlösningar som har registrerats i [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), exempelvis Symantec och Microsoft Defender.  

### <a name="defender"></a>Defender

*Följande kompatibilitetsinställningar stöds med Windows 10 Desktop.*

- **Microsoft Defender program mot skadlig kod**:  
  - **Inte konfigurerat** (*standard*) – Intune kontrollerar inte tjänsten eller ändrar befintliga inställningar.
  - **Kräv** – aktivera tjänsten Microsoft Defender program mot skadlig kod och förhindra att användare stänger av den.

- **Lägsta version för Microsoft Defender antimalware-skadlig kod**:  
  Ange den lägsta tillåtna versionen av Microsoft Defender-tjänsten för skydd mot skadlig kod. Ange till exempel `4.11.0.0`. Om du lämnar tomt kan du använda en version av tjänsten Microsoft Defender program mot skadlig kod.  

  *Som standard konfigureras ingen version*.

- **Microsoft Defender program mot skadlig kod – säkerhets information uppdaterad**:  
  Kontrollerar uppdateringar av Windows säkerhets virus och hot skydd på enheterna.
  - **Inte konfigurerat** (*standard*) – Intune upprätthåller inte några krav.
  - **Kräv** -Force att Microsoft Defender Security Intelligence är uppdaterad.

  [Defender/Health/SignatureOutOfDate CSP](https://docs.microsoft.com/windows/client-management/mdm/defender-csp)
  
  Mer information finns i [Security Intelligence-uppdateringar för Microsoft Defender Antivirus och andra Microsoft antimalware-program](https://www.microsoft.com/en-us/wdsi/defenderupdates).

- **Realtidsskydd**:  
  - **Inte konfigurerat** (*standard*) – Intune styr inte den här funktionen eller ändra befintliga inställningar.
  - **Kräv** -aktivera real tids skydd, som söker efter skadlig kod, spionprogram och annan oönskad program vara.  

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Regler för Microsoft Defender Avancerat skydd

- **Kräv att enheten ska hållas vid eller under riskpoängen**:  
  Använd den här inställningen för att använda riskbedömningen från dina tjänster för skydd mot hot som ett villkor för efterlevnad. Välj högsta tillåtna hotnivå:
  - **Ej konfigurerat** (*standard*)  
  - **Rensa** – Det här alternative är det säkraste, eftersom enheten inte utsätts för några hot. Om hot identifieras på enheten kommer den att utvärderas som inkompatibel.
  - **Låg** – Enheten utvärderas som kompatibel om det bara finns lågnivåhot på den. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel** – Enheten utvärderas som kompatibel om befintliga hot på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög** – Det här alternativet är det minst säkra, och det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
  
  Information om hur du konfigurerar Microsoft Defender ATP (Advanced Threat Protection – Avancerat skydd) som skyddstjänst finns i [Aktivera Microsoft Defender ATP med villkorsstyrd åtkomst](advanced-threat-protection.md).


## <a name="windows-holographic-for-business"></a>Windows 10 Holographic for Business

Windows Holographic för företag använder plattformen **Windows 10 och senare**. Windows Holographic for Business har stöd för följande inställningar:

- **Systemsäkerhet** > **Kryptering** > **Kryptering av lagring av data på enheten**.

Om du vill verifiera enhetskryptering på Microsoft HoloLens kan du läsa avsnittet [Verifiera enhetskryptering](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub använder plattformen **Windows 10 och senare**. Surface Hub har stöd för både efterlevnad och villkorlig åtkomst. Om du vill aktivera dessa funktioner på Surface Hub-enheter rekommenderar vi att du [aktiverar automatisk registrering av Windows 10](../enrollment/windows-enroll.md) i Intune (kräver Azure Active Directory) och anger Surface Hub-enheter som enhetsgrupper. Surface Hub behöver vara Azure AD-anslutet för att efterlevnad och villkorlig åtkomst ska fungera.

Mer information finns i [Konfigurera registrering för Windows-enheter](../enrollment/windows-enroll.md).

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](../fundamentals/scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för Windows 8.1-enheter](compliance-policy-create-windows-8-1.md).
