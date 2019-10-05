---
title: Kompatibilitetsinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du konfigurerar kompatibilitet för Windows 10-, Windows Holographic- och Surface Hub-enheter i Microsoft Intune. Kontrollera kompatibiliteten för lägsta och högsta operativsystemversion, ange begränsningar och längd för lösenord, kontrollera om det finns antiviruslösningar från tredje part, aktivera kryptering för datalagring och mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 484035603e4fb447b004aad6c6f85726034f3c23
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732834"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Inställningar för Windows 10 och senare för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Den här artikeln innehåller en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på Windows 10-enheter och senare enheter i Intune. Som en del av din MDM-lösning för hantering av mobilenheter kan du använda dessa inställningar för att kräva BitLocker, ange en lägsta och högsta operativsystemversion, ange en risknivå med hjälp av Microsoft Defender Advanced Threat Protection (ATP) och mycket mer.

Den här funktionen gäller för:

- Windows 10 och senare
- Windows 10 Holographic for Business
- Surface Hub

Som Intune-administratör kan du använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Mer om kompatibilitetsprinciper och vad de gör finns i [Komma igång med kompatibilitet](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). För **Plattform** väljer du **Windows 10 och senare**.

## <a name="device-health"></a>Device health

- **Kräv BitLocker**: När inställningen **Kräv** används kan enheten skydda data som lagras på enheten mot obehörig åtkomst när systemet är avstängt eller i viloläge. Med Windows BitLocker-diskkryptering krypteras alla data på volymen för Windows-operativsystemet. BitLocker använder TPM för att skydda Windows-operativsystemet och användardata. Det kan också bekräfta att en dator inte manipuleras, även om den lämnas obevakad, tappas bort eller blir stulen. Om datorn är utrustad med en kompatibel TPM använder BitLocker TPM för att låsa krypteringsnycklarna som skyddar data. Därför är nycklarna inte tillgängliga förrän TPM verifierar datorns tillstånd.

  Om inställningen **Inte konfigurerad** (standard) används görs ingen kompatibilitetskontroll för den här inställningen.

- **Kräv att säker start är aktiverat på enheten**: När inställningen **Krävs** används tvingas systemet att starta i ett fabriksinställt betrott läge. När inställningen är aktiverad måste huvudkomponenterna som används för att starta datorn dessutom ha rätt kryptografiska signaturer som är betrodda av den organisation som tillverkade enheten. UEFI-baserad inbyggd programvara kontrollerar signaturen innan den låter datorn starta. Om filer har manipulerats, vilket delar deras signatur, kan systemet inte starta om.

  Om inställningen **Inte konfigurerad** (standard) används görs ingen kompatibilitetskontroll för den här inställningen.

  > [!NOTE]
  > Inställningen **Kräv att säker start är aktiverat på enheten** stöds på vissa TPM 1.2- och 2.0-enheter. För enheter som inte stöder TPM 2.0 eller senare, visas principstatusen i Intune som **Ej ompatibel**. Mer information om vilka versioner som stöds finns i [Hälsoattestering för enhet](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Kräv kodintegritet:** Kodintegritet är en funktion som kontrollerar integriteten för en drivrutin eller systemfil varje gång den läses in i minnet. När inställningen **Krävs** används kontrollerar kodintegritetsfunktionen om en osignerad drivrutin eller systemfil läses in i kerneln. Den upptäcker också om en systemfil ändras av skadlig programvara som körs av ett användarkonto med administratörsbehörighet.

  Om inställningen **Inte konfigurerad** (standard) används görs ingen kompatibilitetskontroll för den här inställningen.

Fler resurser:

- Mer information om hur hälsoattesteringstjänsten fungerar finns i [CSP för hälsoattestering](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Supporttips: Använda Hälsoattestering för enhet som en del av din Intune-kompatibilitetsprincip](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemsversion**: Ange den lägsta tillåtna versionen i formatet **major.minor.build.CU**. Öppna en kommandotolk och skriv `ver` för att visa det korrekta värdet. Kommandot `ver` returnerar versionen i följande format:

  `Microsoft Windows [Version 10.0.17134.1]`

  Om en enhet har en tidigare version än operativsystemsversionen du anger rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändarna kan välja att uppgradera sina enheter. När de har uppgraderat har de åtkomst till företagsresurser.

- **Maximal operativsystemversion**: Ange den högsta tillåtna versionen i formatet **major.minor.build.revision**. Öppna en kommandotolk och skriv `ver` för att visa det korrekta värdet. Kommandot `ver` returnerar versionen i följande format:

  `Microsoft Windows [Version 10.0.17134.1]`

  När en enhet använder en senare operativsystemversion än den version som har angett blockeras åtkomsten till organisationens resurser. Slutanvändaren uppmanas att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän regeln ändras så att operativsystemversionen tillåts.

- **Lägsta operativsystemversion som krävs för mobila enheter**: Ange den lägsta tillåtna versionen i formatet major.minor.build number.

  Om en enhet har en tidigare version än operativsystemsversionen du anger rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändarna kan välja att uppgradera sina enheter. När de har uppgraderat har de åtkomst till företagsresurser.

- **Högsta operativsystemversion som krävs för mobila enheter**: Ange den högsta tillåtna versionen i formatet major.minor.build number.

  När en enhet använder en senare operativsystemversion än den version som har angett blockeras åtkomsten till organisationens resurser. Slutanvändaren uppmanas att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän regeln ändras så att operativsystemversionen tillåts.

- **Giltiga operativsystemversioner**: Ange ett intervall för godkända operativsystemversioner, inklusive ett minimum och maximum. Du kan också **exportera** en lista med kommaavgränsade värden över dessa godkända OS-versionsnummer i en CSV-fil.

## <a name="configuration-manager-compliance"></a>Configuration Manager-kompatibilitet

Gäller enbart för samhanterade enheter som kör Windows 10 och senare. Enheter med enbart Intune returnerar statusen inte tillgänglig.

- **Kräv enhetskompatibilitet från System Center Configuration Manager**: Välj **Krävs** om alla inställningar (konfigurationsobjekt) i System Center Configuration Manager måste vara kompatibla. 

  Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd är enheten inte kompatibel i Intune.
  
  Är den **Inte konfigurerad** så kontrollerar inte Intune inställningarna i Configuration Manager för kompatibilitet.

## <a name="system-security"></a>Systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter. När det **inte är konfigurerat**utvärderar Intune inte enheten för lösen ords inställningar för efterlevnad.
- **Enkla lösenord**: Ställ in på **Blockera** om du vill att användaren inte ska kunna skapa enkla lösenord såsom **1234** eller **1111**. Ange till **Inte konfigurerad** så att användarna kan skapa lösenord som **1234** eller **1111**.
- **Krav på lösenordstyp**: Välj typ av lösenord eller PIN-kod. Alternativen är:

  - **Enhets standard**: Kräv lösen ord, numerisk PIN-kod eller alfanumerisk PIN-kod
  - **Numerisk**: Kräv ett lösen ord eller en numerisk PIN-kod
  - **Alfanumeriskt**: Kräv ett lösen ord eller en alfanumerisk PIN-kod. Välj också **lösen ords komplexitet**: 
    
    - **Kräv siffror och gemener**
    - **Kräv siffror, gemener och versaler**
    - **Siffror, gemener, versaler och specialtecken krävs.**

    > [!TIP]
    > De alfanumeriska lösen ords principerna kan vara komplexa. Vi uppmuntrar administratörer att läsa kryptografiproviders för mer information:
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.
- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar)** : Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord, från 1-730.
- **Antal tidigare lösenord för att förhindra återanvändning**: Ange det antal tidigare lösenord som inte får återanvändas.
- **Kräv lösenord när enheten lämnar inaktivt läge (mobil och holografiskt)** : Tvinga användare att ange lösenordet varje gång enheten lämnar inaktivt läge.

  > [!IMPORTANT]
  > När lösenordskravet ändras på ett Windows-skrivbord påverkas användarna nästa gång de loggar in, eftersom det är då enheten går från inaktiv till aktiv. Användare med lösenord som uppfyller kravet uppmanas ändå att ändra sina lösenord.

### <a name="encryption"></a>Kryptering

- **Kryptering för lagring av data på en enhet**: Välj **Kräv** för att kryptera lagring av data på dina enheter.

  > [!NOTE]
  > Inställningen **Kryptering för lagring av data på en enhet** kontrollerar om kryptering används på enheten. Om du behöver en starkare krypteringsinställning bör du överväga att använda **Kräv BitLocker**, som använder Attestering för Windows-enhetens hälsotillstånd för att verifiera Bitlocker-status på TPM-nivå.

### <a name="device-security"></a>Enhetssäkerhet

- **Brand vägg**: Ställ in på **Kräv** att aktivera Microsoft Defender-brandväggen och hindra användare från att stänga av den. **Inte konfigurerad** (standard) styr inte Microsoft Defender-brandväggen eller ändra befintliga inställningar.

  [Brand vägg CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

- **Trusted Platform Module (TPM)** : När inställningen är **obligatorisk**kontrollerar Intune versionen för kompatibilitet. Enheten är kompatibel om TPM-chipets version är större än 0 (noll). Enheten är inte kompatibel om det inte finns någon TPM-version på enheten. När det **inte är konfigurerat**kontrollerar Intune inte enheten för en TPM-krets-version.

  [DeviceStatus CSP-DeviceStatus/TPM/SpecificationVersion Node](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivirus**: När **Kräv** har valts kan du kontrollera efterlevnaden med hjälp av antivirusprogram som är registrerade i [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), till exempel Symantec och Microsoft Defender. När Intune **inte är konfigurerat** görs inga sökningar efter AV-lösningar installerade på enheten.
- **Antispionprogram**: När **Kräv** har valts kan du kontrollera efterlevnaden med antispionprogram som har registrerats med [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), till exempel Symantec och Microsoft Defender. När Intune **inte är konfigurerat** görs inga sökningar efter lösningar med antispionprogram installerade på enheten.

### <a name="defender"></a>Defender

- **Microsoft Defender program mot skadlig kod**: Ställ in på **Kräv** att aktivera tjänsten Microsoft Defender skydd mot skadlig kod och hindra användare från att stänga av den. **Inte konfigurerad** (standard) styr inte tjänsten eller ändrar inte befintliga inställningar.
- **Lägsta version av Microsoft Defender antimalware-skadlig kod**: Ange den lägsta tillåtna versionen av Microsoft Defender-tjänsten för skydd mot skadlig kod. Ange till exempel `4.11.0.0`. Om du lämnar tomt kan du använda en version av tjänsten Microsoft Defender program mot skadlig kod.
- **Microsoft Defender program mot skadlig kod – säkerhets information uppdaterad**: styr uppdateringar av Windows säkerhets virus och hot skydd på enheterna. **Kräver** att Microsoft Defender Security Intelligence är uppdaterat. **Inte konfigurerad** (standard) upprätthåller inte några krav.

  [Säkerhets information uppdateringar för Microsoft Defender Antivirus och andra Microsoft antimalware-program](https://www.microsoft.com/en-us/wdsi/defenderupdates) har mer information om säkerhets information.

- **Real tids skydd**: **Kräv** aktiverar real tids skydd, som söker efter skadlig kod, spionprogram och annan oönskad program vara. **Inte konfigurerad** (standard) styr inte den här funktionen eller ändra befintliga inställningar.

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

- **Kräv att enheten ska vara på eller under hotnivån för datorn**: Använd den här inställningen för att använda riskbedömningen från dina tjänster för skydd mot hot som ett villkor för efterlevnad. Välj högsta tillåtna hotnivå:

  - **Säkrad**: Det här alternativet är det säkraste eftersom enheten inte kan ha några hot. Om hot identifieras på enheten kommer den att utvärderas som inkompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om existerande hot på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög**: Det här alternativet är det minst säkra och det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
  
  Information om hur du konfigurerar Microsoft Defender ATP (Advanced Threat Protection – Avancerat skydd) som skyddstjänst finns i [Aktivera Microsoft Defender ATP med villkorsstyrd åtkomst](advanced-threat-protection.md).

Välj **OK** > **Skapa** för att spara ändringarna.

## <a name="windows-holographic-for-business"></a>Windows 10 Holographic for Business

Windows Holographic för företag använder plattformen **Windows 10 och senare**. Windows Holographic for Business har stöd för följande inställningar:

- **Systemsäkerhet** > **Kryptering** > **Kryptering av lagring av data på enheten**.

Om du vill verifiera enhetskryptering på Microsoft HoloLens kan du läsa avsnittet [Verifiera enhetskryptering](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub använder plattformen **Windows 10 och senare**. Surface Hub har stöd för både efterlevnad och villkorlig åtkomst. Om du vill aktivera dessa funktioner på Surface Hub-enheter rekommenderar vi att du [aktiverar automatisk registrering av Windows 10](../enrollment/windows-enroll.md) i Intune (kräver Azure Active Directory) och anger Surface Hub-enheter som enhetsgrupper. Surface Hub behöver vara Azure AD-anslutet för att efterlevnad och villkorlig åtkomst ska fungera.

Se [konfigurera registrering för Windows-enheter](../enrollment/windows-enroll.md) för vägledning.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](../fundamentals/scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för Windows 8.1-enheter](compliance-policy-create-windows-8-1.md).
