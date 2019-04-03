---
title: Kontrollera om det finns en efterlevnadsprincip för Windows-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa eller konfigurera en enhetsefterlevnadsprincip i Microsoft Intune för Windows Phone 8.1, Windows 8.1 och senare, och Windows 10 och senare enheter. Kontrollera efterlevnad på det lägsta och högsta operativsystemet, ange begränsningar för lösenord och längd, kräv BitLocker, sök efter AV-lösningar från tredje part, ställ in godkänd hotnivå och aktivera kryptering för lagring av data, inklusive Surface Hub och Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: acf14ea6f1b667cb631a424223a40e44a8338edd
ms.sourcegitcommit: 768430b5296573c6e007ae4e13d57aeda4be4b7e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58306850"
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>Lägg till en enhetsefterlevnadsprincip för Windows-enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En Intune-enhetsefterlevnadsprincip innehåller de regler och inställningar som enheter måste uppfylla för att anses vara kompatibla. Använd dessa principer med villkorsstyrd åtkomst för att tillåta eller blockera åtkomst till organisationens resurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet.

Läs mer om efterlevnadsprinciper och eventuella förutsättningar i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

Följande tabell beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

---------------------------

| **Principinställning** | **Windows 8.1 och senare** | **Windows Phone 8.1 och senare** |
|----| ----| --- |
| **Konfiguration av PIN-kod eller lösenord** | Åtgärdad | Åtgärdad |   
| **Enhetskryptering** | Inte tillämpligt | Åtgärdad |   
| **Jailbreakad eller rotad enhet** | Inte tillämpligt | Inte tillämpligt |  
| **E-postprofil** | Inte tillämpligt | Inte tillämpligt |   
| **Lägsta version av operativsystemet** | I karantän | I karantän |   
| **Högsta version av operativsystemet** | I karantän | I karantän |   
| **Attestering av hälsotillstånd i Windows** | I karantän: Windows 10 och Windows 10 Mobile|Inte tillämpligt: Windows 8.1 |

-------------------------------

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. (Till exempel om användaren tvingas att ange en PIN-kod.)

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. För **Plattform**, väljer **Windows Phone 8.1**, **Windows 8.1 och senare** eller **Windows 10 och senare**.
6. Välj **Inställningar** för att konfigurera och ange inställningar för **Enhetens hälsotillstånd**, **Enhetsegenskaper** och **Systemsäkerhet**. När du är klar väljer du **OK**, och **Skapa**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Principinställningar för Windows 8.1-enheter

Dessa inställningar gäller för enheter som kör följande plattformar:

- Windows Phone 8.1
- Windows 8.1 och senare

### <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion som krävs:** När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta tillåtna version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som anges i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Enheten kan inte komma åt företagsresurser förrän du ändrar regeln för att tillåta operativsystemets version.

Datorer med Windows 8.1 returnerar en **3**-version. Om regeln för operativsystemsversion är inställd på Windows 8.1 för Windows rapporteras enheten som inkompatibel även om den har Windows 8.1.

### <a name="system-security"></a>Systemsäkerhet

#### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Enkla lösenord**: Ställ in på **Blockera** om du vill att användaren inte ska kunna skapa enkla lösenord såsom **1234** eller **1111**. Ange till **Inte konfigurerad** så att användarna kan skapa lösenord som **1234** eller **1111**.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.

  För enheter som kör Windows och som nås med ett Microsoft-konto, kan inte efterlevnadsprincipen utvärdera korrekt:
  - Om minsta längd på lösenordet är längre än åtta tecken
  - Eller om minsta antal teckenuppsättningar är större än två

- **Lösenordstyp**: Ange om ett lösenord endast ska ha **numeriska** tecken, eller om det ska vara en blandning av siffror och andra tecken (**alfanumeriska**).
  
  - **Antal icke-alfanumeriska tecken i lösenordet:** Om **Krav på lösenordstyp** är inställt till **Alfanumeriskt** anger den här inställningen det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
    - Gemener
    - Versaler
    - Symboler
    - Siffror

    Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext. För enheter som nås med ett Microsoft-konto, kan efterlevnadsprincipen inte korrekt utvärdera:

    - Om minsta längd på lösenordet är längre än åtta tecken
    - Eller om minsta antal teckenuppsättningar är större än två

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Antal tidigare lösenord för att förhindra återanvändning**: Ange det antal tidigare lösenord som inte får återanvändas.

#### <a name="encryption"></a>Kryptering

- **Kräv kryptering på mobila enheter**: **Kräv** att enheten krypteras för att ansluta till data-lagringsresurser.

## <a name="windows-10-and-later-policy-settings"></a>Windows 10 och senare principinställningar

### <a name="device-health"></a>Device health

- **Kräv BitLocker**: När Bitlocker är på kan enheten skydda data lagrad på enheten från obehörig åtkomst när datorn är avstängd eller försätts i viloläge. Med Windows BitLocker-diskkryptering krypteras alla data på volymen för Windows-operativsystemet. BitLocker använder TPM för att skydda Windows-operativsystemet och användardata. Det kan också bekräfta att en dator inte manipuleras, även om den lämnas obevakad, tappas bort eller blir stulen. Om datorn är utrustad med en kompatibel TPM använder BitLocker TPM för att låsa krypteringsnycklarna som skyddar data. Därför är nycklarna inte tillgängliga förrän TPM verifierar datorns tillstånd.
- **Kräv att säker start är aktiverat på enheten:** När säker start är aktiverat tvingas systemet att starta i ett fabriksinställt betrott läge. När säker start är aktiverat måste huvudkomponenterna som används för att starta datorn dessutom ha rätt kryptografiska signaturer som är betrodda av den organisation som tillverkade enheten. UEFI-baserad inbyggd programvara kontrollerar signaturen innan den låter datorn starta. Om filer har manipulerats, vilket delar deras signatur, kan systemet inte starta om.

  > [!NOTE]
  > Inställningen **Kräv att säker start är aktiverat på enheten** stöds på vissa TPM 1.2- och 2.0-enheter. För enheter som inte stöder TPM 2.0 eller senare, visas principstatusen i Intune som **Ej ompatibel**. Mer information om versioner som stöds finns i [Hälsoattestering för enhet](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Kräv kodintegritet:** Kodintegritet är en funktion som kontrollerar integriteten för en drivrutin eller systemfil varje gång den läses in i minnet. Kodintegritet kontrollerar om en osignerad drivrutin eller systemfil läses in i kerneln. Den upptäcker också om en systemfil ändras av skadlig programvara som körs av ett användarkonto med administratörsbehörighet.

Ytterligare resurser:

- Mer information om hur hälsoattesteringstjänsten fungerar finns i [CSP för hälsoattestering](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Tips för support: Med hjälp av Hälsoattestering för enhet som en del av din Intune-Efterlevnadsprincip ](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

### <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemsversion**: Ange den lägsta tillåtna versionen i formatet **major.minor.build.CU**. Öppna en kommandotolk och skriv `ver` för att visa det korrekta värdet. Kommandot `ver` returnerar versionen i följande format:

  `Microsoft Windows [Version 10.0.17134.1]`

  Om en enhet har en tidigare version än operativsystemsversionen du anger rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändarna kan välja att uppgradera sina enheter. När de har uppgraderat har de åtkomst till företagsresurser.

- **Maximal operativsystemversion**: Ange den högsta tillåtna versionen i formatet **major.minor.build.revision**. Öppna en kommandotolk och skriv `ver` för att visa det korrekta värdet. Kommandot `ver` returnerar versionen i följande format:

  `Microsoft Windows [Version 10.0.17134.1]`

  När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte komma åt företagsresurser förrän regeln ändras så att operativsystemversionen tillåts.

- **Lägsta operativsystemversion som krävs för mobila enheter**: Ange den lägsta tillåtna versionen i formatet major.minor.build number.

  Om en enhet har en tidigare version än operativsystemsversionen du anger rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändarna kan välja att uppgradera sina enheter. När de har uppgraderat har de åtkomst till företagsresurser.

- **Högsta operativsystemversion som krävs för mobila enheter**: Ange den högsta tillåtna versionen i formatet major.minor.build number.

  När en enhet använder en senare version av operativsystemet än den du anger i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte komma åt företagsresurser förrän regeln ändras så att operativsystemversionen tillåts.

- **Giltiga operativsystemversioner**: Ange ett intervall för godkända operativsystemversioner, inklusive ett minimum och maximum. Du kan också **exportera** en lista med kommaavgränsade värden över dessa godkända OS-versionsnummer i en CSV-fil.

### <a name="configuration-manager-compliance"></a>Configuration Manager-kompatibilitet

Gäller enbart för samhanterade enheter som kör Windows 10 och senare. Enheter med enbart Intune returnerar statusen inte tillgänglig.

- **Kräv enhetens efterlevnad från System Center Configuration Manager**: Välj **kräver** att tvinga alla inställningar (konfigurationsobjekt) i System Center Configuration Manager att vara kompatibel. 

  Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd är enheten inte kompatibel i Intune.
  
  Är den **Inte konfigurerad** så kontrollerar inte Intune inställningarna i Configuration Manager för kompatibilitet.

### <a name="system-security-settings"></a>Inställningar för systemsäkerhet

#### <a name="password"></a>Lösenord

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

#### <a name="encryption"></a>Kryptering

- **Kryptering för lagring av data på en enhet**: Välj **Kräv** för att kryptera lagring av data på dina enheter.

  > [!NOTE]
  > Inställningen **Kryptering för lagring av data på en enhet** kontrollerar om kryptering används på enheten. Om du behöver en starkare krypteringsinställning bör du överväga att använda **Kräv BitLocker**, som använder Attestering för Windows-enhetens hälsotillstånd för att verifiera Bitlocker-status på TPM-nivå.

#### <a name="device-security"></a>Enhetssäkerhet

- **Antivirus**: När **Kräv** har valts kan du kontrollera efterlevnaden med hjälp av antivirusprogram som är registrerade i [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), till exempel Symantec och Windows Defender. När Intune **inte är konfigurerat** görs inga sökningar efter AV-lösningar installerade på enheten.
- **Antispionprogram**: När **Kräv** har valts kan du kontrollera efterlevnaden med antispionprogram som har registrerats med [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), till exempel Symantec och Windows Defender. När Intune **inte är konfigurerat** görs inga sökningar efter lösningar med antispionprogram installerade på enheten.

### <a name="windows-defender-atp"></a>Windows Defender ATP

- **Kräv att enheten ska vara på eller under hotnivån för datorn**: Använd den här inställningen för att använda riskbedömningen från dina tjänster för skydd mot hot som ett villkor för efterlevnad. Välj högsta tillåtna hotnivå:
  - **Säkrad**: Det här alternativet är det säkraste eftersom enheten inte kan ha några hot. Om hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om existerande hot på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög**: Det här alternativet är det minst säkra och det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
  
  Information om hur du konfigurerar Windows Defender ATP (Advanced Threat Protection – Avancerat skydd) som skyddstjänst finns i [Aktivera Windows Defender ATP med villkorsstyrd åtkomst](advanced-threat-protection.md).

## <a name="windows-holographic-for-business"></a>Windows 10 Holographic for Business

Windows Holographic för företag använder plattformen **Windows 10 och senare**. Windows Holographic for Business har stöd för följande inställningar:

- **Systemsäkerhet** > **Kryptering** > **Kryptering av lagring av data på enheten**.

Om du vill verifiera enhetskryptering på Microsoft HoloLens kan du läsa avsnittet [Verifiera enhetskryptering](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub
Surface Hub använder plattformen **Windows 10 och senare**. Surface Hub har stöd för både efterlevnad och villkorlig åtkomst. Om du vill aktivera dessa funktioner på Surface Hub-enheter, rekommenderar vi att du [aktiverar automatisk registrering av Windows 10](windows-enroll.md) i Intune (kräver också Azure Active Directory) och anger Surface Hub-enheter som enhetsgrupper. Surface Hub behöver vara Azure AD-anslutet för att efterlevnad och villkorlig åtkomst ska fungera.

Se [konfigurera registrering för Windows-enheter](windows-enroll.md) för vägledning.

## <a name="assign-user-or-device-groups"></a>Tilldela användar- eller enhetsgrupper

1. Välj en princip som du har konfigurerat. Befintliga principer finns i **Enhetsefterlevnad** > **Principer**.
2. Välj principen och välj **Tilldelningar**. Du kan inkludera eller exkludera Azure AD-säkerhetsgrupper.
3. Välj **Valda grupper** för att se dina Azure AD-säkerhetsgrupper. Välj de användar- eller enhetsgrupper som du vill att den här principen ska tillämpas på och välj **Spara** för att distribuera principen.

Du har tillämpat principen. Enheter som används av användare som omfattas av principen utvärderas för att kontrollera att de är kompatibla.

## <a name="next-steps"></a>Nästa steg
[Automatisera e-post och lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md)  
[Övervaka efterlevnadsprinciper för Intune-enheter](compliance-policy-monitor.md)
