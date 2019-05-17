---
title: Kompatibilitetsinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du konfigurerar kompatibilitet för Windows 10-, Windows Holographic- och Surface Hub-enheter i Microsoft Intune. Kontrollera kompatibiliteten för lägsta och högsta operativsystemversion, ange begränsningar och längd för lösenord, kontrollera om det finns antiviruslösningar från tredje part, aktivera kryptering för datalagring och mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d956526d483a74ca5929180a48ea2dcd8b3eab7
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423636"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Inställningar för Windows 10 och senare för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln innehåller en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på Windows 10-enheter och senare enheter i Intune. Som en del av din MDM-lösning för hantering av mobilenheter kan du använda dessa inställningar för att kräva BitLocker, ange en lägsta och högsta operativsystemversion, ange en risknivå med hjälp av Windows Defender Advanced Threat Protection (ATP) och mycket mer.

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

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Enkla lösenord**: Ställ in på **Blockera** om du vill att användaren inte ska kunna skapa enkla lösenord såsom **1234** eller **1111**. Ange till **Inte konfigurerad** så att användarna kan skapa lösenord som **1234** eller **1111**.
- **Lösenordstyp**: Ange om ett lösenord endast ska ha **numeriska** tecken, eller om det ska vara en blandning av siffror och andra tecken (**alfanumeriska**).

  - **Antal icke-alfanumeriska tecken i lösenordet:** Om **Krav på lösenordstyp** är inställt till **Alfanumeriskt** anger den här inställningen det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
    - Gemener
    - Versaler
    - Symboler
    - Siffror

    Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.
- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Antal tidigare lösenord för att förhindra återanvändning**: Ange det antal tidigare lösenord som inte får återanvändas.
- **Kräv lösenord när enheten lämnar inaktivt läge (mobil och holografiskt)**: Tvinga användare att ange lösenordet varje gång enheten lämnar inaktivt läge.

### <a name="encryption"></a>Kryptering

- **Kryptering för lagring av data på en enhet**: Välj **Kräv** för att kryptera lagring av data på dina enheter.

  > [!NOTE]
  > Inställningen **Kryptering för lagring av data på en enhet** kontrollerar om kryptering används på enheten. Om du behöver en starkare krypteringsinställning bör du överväga att använda **Kräv BitLocker**, som använder Attestering för Windows-enhetens hälsotillstånd för att verifiera Bitlocker-status på TPM-nivå.

### <a name="device-security"></a>Enhetssäkerhet

- **Antivirus**: När **Kräv** har valts kan du kontrollera efterlevnaden med hjälp av antivirusprogram som är registrerade i [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), till exempel Symantec och Windows Defender. När Intune **inte är konfigurerat** görs inga sökningar efter AV-lösningar installerade på enheten.
- **Antispionprogram**: När **Kräv** har valts kan du kontrollera efterlevnaden med antispionprogram som har registrerats med [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), till exempel Symantec och Windows Defender. När Intune **inte är konfigurerat** görs inga sökningar efter lösningar med antispionprogram installerade på enheten.

## <a name="windows-defender-atp"></a>Windows Defender ATP

- **Kräv att enheten ska vara på eller under hotnivån för datorn**: Använd den här inställningen för att använda riskbedömningen från dina tjänster för skydd mot hot som ett villkor för efterlevnad. Välj högsta tillåtna hotnivå:

  - **Säkrad**: Det här alternativet är det säkraste eftersom enheten inte kan ha några hot. Om hot identifieras på enheten kommer den att utvärderas som inkompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om existerande hot på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög**: Det här alternativet är det minst säkra och det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
  
  Information om hur du konfigurerar Windows Defender ATP (Advanced Threat Protection – Avancerat skydd) som skyddstjänst finns i [Aktivera Windows Defender ATP med villkorsstyrd åtkomst](advanced-threat-protection.md).

Välj **OK** > **Skapa** för att spara ändringarna.

## <a name="windows-holographic-for-business"></a>Windows 10 Holographic for Business

Windows Holographic för företag använder plattformen **Windows 10 och senare**. Windows Holographic for Business har stöd för följande inställningar:

- **Systemsäkerhet** > **Kryptering** > **Kryptering av lagring av data på enheten**.

Om du vill verifiera enhetskryptering på Microsoft HoloLens kan du läsa avsnittet [Verifiera enhetskryptering](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub använder plattformen **Windows 10 och senare**. Surface Hub har stöd för både efterlevnad och villkorlig åtkomst. Om du vill aktivera dessa funktioner på Surface Hub-enheter rekommenderar vi att du [aktiverar automatisk registrering av Windows 10](windows-enroll.md) i Intune (kräver Azure Active Directory) och anger Surface Hub-enheter som enhetsgrupper. Surface Hub behöver vara Azure AD-anslutet för att efterlevnad och villkorlig åtkomst ska fungera.

Se [konfigurera registrering för Windows-enheter](windows-enroll.md) för vägledning.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för Windows 8.1-enheter](compliance-policy-create-windows-8-1.md).