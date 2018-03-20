---
title: "Skapa en efterlevnadsprincip för Windows-enheter i Microsoft Intune"
titleSuffix: 
description: "Skapa en efterlevnadsprincip i Microsoft Intune för Windows-enheter så att du kan ange de krav som en enhet måste uppfylla för att vara kompatibel."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 32af54e3e753e7ded3c86d9d44b793da7fe2e9c0
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-windows-devices-in-intune"></a>Lär dig hur du skapar en enhetsefterlevnadsprincip för Windows-enheter i Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En efterlevnadsprincip i Intune för Windows-enheter anger de regler och inställningar som Windows-enheter måste uppfylla för att anses vara kompatibla. Du kan använda dessa principer med villkorlig åtkomst för att tillåta eller blockera åtkomst till företagets resurser. Du kan även få enhetsrapporter och vidta åtgärder vid inkompatibilitet. Du skapar efterlevnadsprinciper för enheter för varje plattform i Intune Azure-portalen. Mer information om efterlevnadsprinciper och de förhandskrav du måste uppfylla innan du skapar en efterlevnadsprincip finns i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

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

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Skapa en efterlevnadsprincip i Azure-portalen

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
1. I fönstret **Intune** väljer du **Enhetsefterlevnad**. Under **Hantera** väljer du **Principer** och **Skapa princip**.
2. Skriv ett namn, ge en beskrivning och välj den plattform som du vill att den här principen ska tillämpas på.
3. Välj **Konfigurera inställningar** för att ange **Systemsäkerhet**, **Enhetens hälsotillstånd** och **Enhetsegenskaper** här. När du är klar väljer du **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Tilldela användargrupper

Om du vill tilldela en efterlevnadsprincip till användare, väljer du en princip som du har konfigurerat. Du hittar befintliga principer i fönstret **Enhetsefterlevnad – Principer**.

1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas det fönster där du kan välja **Azure Active Directory-säkerhetsgrupper** och tilldela dem till principen.
2. Öppna fönstret som visar Azure AD-säkerhetsgrupperna genom att välja **Valda grupper**.  När du väljer **Spara** distribueras principen till användarna.

Du har tillämpat principen på användarna. Efterlevnaden hos de enheter som används av de användare som principen är inriktad på kommer att utvärderas.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Systemsäkerhetsinställningar

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** Ställ in på **Ja** för att ställa in så att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Tillåt enkla lösenord:** Ställ in på **Ja** för att låta användarna skapa enkla lösenord som ”**1234**” eller ”**1111**”.
- **Minsta längd på lösenord:** Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.
- **Lösenordstyp som krävs**: Ange om användarna måste skapa ett **alfanumeriskt** eller **numeriskt lösenord**.

För enheter som kör Windows och som nås med ett Microsoft-konto utvärderas efterlevnadsprincipen inte korrekt om Minsta längd på lösenord är större än åtta tecken eller om Minsta antal teckenuppsättningar är större än två.

- **Minsta antal teckenuppsättningar:** Om alternativet för **Krav på lösenordstyp** är **Alfanumeriskt** anger den här inställningen det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
  - Gemener
  - Versaler
  - Symboler
  - Siffror

Om du anger en hög siffra för den här inställningen kräver det att användarna skapar lösenord som är mer komplexa. För enheter som kör Windows och som nås med ett Microsoft-konto utvärderas efterlevnadsprincipen inte korrekt om Minsta längd på lösenord är större än åtta tecken eller om Minsta antal teckenuppsättningar är större än två.

- **Minuter av inaktivitet innan lösenord måste anges:** Anger efter hur lång tids inaktivitet som användaren måste ange lösenordet igen.
- **Lösenordets giltighetstid (dagar)**: Ange antalet dagar tills användarens lösenord upphör att gälla och användaren måste skapa ett nytt lösenord.
- **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Om **Spara lösenordshistorik** har valts anger du hur många tidigare använda lösenord som inte får återanvändas.
- **Kräv lösenord när enheten lämnar inaktivt läge:** Den här inställningen bör användas tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Användarna uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.

**Den här inställningen gäller endast Windows 10 Mobile-enheter.**

### <a name="encryption"></a>Kryptering

- **Kräv kryptering på den mobila enheten:** Välj **Ja** för den här inställningen om du vill kräva att enheten ska krypteras för att ansluta till resurser.



## <a name="device-health-settings"></a>Inställningar för enhetens hälsotillstånd

- **Kräv att enheter ska rapporteras som felfria:** Du kan ange en regel för att kräva att **Windows 10 Mobile**-enheter rapporteras som felfria i nya eller befintliga efterlevnadsprinciper. Om den här inställningen är aktiverad utvärderas Windows 10-enheter via hälsoattesteringstjänsten (HAS) för följande datapunkter:
  - **BitLocker är aktiverat:** Om BitLocker är aktiverat kan enheten skydda data mot obehörig åtkomst när datorn är avstängd eller försätts i viloläge. Windows BitLocker-diskkryptering krypterar alla data som lagras på Windows-operativsystemsvolymen. BitLocker använder TPM-modulen för att skydda Windows-operativsystemet och användardata och ser till att datorn inte har manipulerats, även om den lämnas obevakad, tappas bort eller blir stulen. Om datorn är utrustad med en kompatibel TPM använder BitLocker TPM för att låsa krypteringsnycklarna som skyddar data. Därför kan inte nycklarna användas förrän TPM har verifierat datorns tillstånd
  - **Kodintegritet är inte aktiverat:** Kodintegritet är en funktion som kontrollerar integriteten för en drivrutin eller systemfil varje gång den läses in i minnet. Kodintegritetsfunktionen kontrollerar om en osignerad drivrutin eller systemfil läses in i kerneln, eller om en systemfil har ändrats av skadlig programvara som körs av ett användarkonto med administratörsbehörighet.
  - **Säker start är aktiverat:** När säker start är aktiverat tvingas systemet att starta i ett fabriksinställt betrott läge. När säker start är aktiverat måste huvudkomponenterna som används för att starta datorn dessutom ha rätt kryptografiska signaturer som är betrodda av den organisation som tillverkade enheten. UEFI verifierar detta innan datorn startas. Om några filer har manipulerats och signaturerna brutits startas inte datorn.

Mer information om hur hälsoattesteringstjänsten fungerar finns i avsnittet om [kryptografiprovidern för hälsoattesteringstjänsten](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion som krävs:** När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta tillåtna version av operativsystemet:** När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

<!---## Compliance policy settings for Windows PCs--->

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Minsta längd på lösenord:** – Stöds i Windows 8.1.

Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.

För enheter som nås med ett Microsoft-konto utvärderas efterlevnadsprincipen inte korrekt om **Minsta längd på lösenord** är längre än åtta tecken eller om **Minsta antal teckenuppsättningar** är större än två.

- **Krav på lösenordstyp**: Stöds på Windows RT, Windows RT 8.1 och Windows 8.1

Ange om användarna måste skapa ett **alfanumeriskt** eller **numeriskt** lösenord.

- **Minsta antal teckenuppsättningar**: Stöds på Windows RT, Windows RT 8.1 och Windows 8.1. Om alternativet för **Krav på lösenordstyp** är **Alfanumeriskt** anger den här inställningen det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
  - Gemener
  - Versaler
  - Symboler
  - Siffror: Om du anger en hög siffra för den här inställningen kräver det att användarna skapar lösenord som är mer komplexa.

För enheter som nås med ett Microsoft-konto utvärderas efterlevnadsprincipen inte korrekt om **Minsta längd på lösenord** är längre än åtta tecken eller om **Minsta antal teckenuppsättningar** är större än två.

- **Minuter av inaktivitet innan lösenord måste anges:** – Stöds på Windows RT, Windows RT 8.1 och Windows 8.1

Ange efter hur lång tids inaktivitet som användaren måste ange sitt lösenord igen.

- **Lösenordets giltighetstid (dagar)**: Stöds på Windows RT, Windows RT 8.1 och Windows 8.1.

Ange antalet dagar tills användarens lösenord upphör att gälla och användaren måste skapa ett nytt lösenord.

- **Spara lösenordshistorik:** – Stöds på Windows RT, Windows RT och Windows 8.1.

Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.

- **Förhindra återanvändning av tidigare lösenord:** – Stöds på Windows RT, Windows RT 8.1 och Windows 8.1

Om **Spara lösenordshistorik:** har valts anger du hur många tidigare använda lösenord som inte får återanvändas.


## <a name="device-health-settings"></a>Inställningar för enhetens hälsotillstånd

- **Kräv att enheter ska rapporteras som felfria:** – Stöds på Windows 10-enheter. Du kan ange en regel för att begära att Windows 10-enheter rapporteras som felfria i nya eller befintliga efterlevnadsprinciper. Om den här inställningen är aktiverad utvärderas Windows 10-enheter via hälsoattesteringstjänsten (HAS) för följande datapunkter:
  - **BitLocker är aktiverat:** Om BitLocker är aktiverat kan enheten skydda data mot obehörig åtkomst när datorn är avstängd eller försätts i viloläge. Windows BitLocker-diskkryptering krypterar alla data som lagras på Windows-operativsystemsvolymen. BitLocker använder TPM-modulen för att skydda Windows-operativsystemet och användardata och ser till att datorn inte har manipulerats, även om den lämnas obevakad, tappas bort eller blir stulen. Om datorn är utrustad med en kompatibel TPM använder BitLocker TPM för att låsa krypteringsnycklarna som skyddar data. Därför kan inte nycklarna användas förrän TPM har verifierat datorns tillstånd
  - **Kodintegritet är inte aktiverat:** Kodintegritet är en funktion som kontrollerar integriteten för en drivrutin eller systemfil varje gång den läses in i minnet. Kodintegritetsfunktionen kontrollerar om en osignerad drivrutin eller systemfil läses in i kerneln, eller om en systemfil har ändrats av skadlig programvara som körs av ett användarkonto med administratörsbehörighet.
  - **Säker start är aktiverat:** När säker start är aktiverat tvingas systemet att starta i ett fabriksinställt betrott läge. När säker start är aktiverat måste huvudkomponenterna som används för att starta datorn dessutom ha rätt kryptografiska signaturer som är betrodda av den organisation som tillverkade enheten. UEFI verifierar detta innan datorn startas. Om några filer har manipulerats och signaturerna brutits startas inte datorn.
  - **Tidig lansering av program mot skadlig kod:** Tidig lansering av program mot skadlig kod (ELAM) ger skydd för datorer i nätverket när de startar och innan drivrutiner från tredje part initieras.

Mer information om hur hälsoattesteringstjänsten fungerar finns i avsnittet om [kryptografiprovidern för hälsoattesteringstjänsten](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta version av operativsystemet som krävs:** – Stöds på Windows 8.1 och Windows 10.

Ange ”högre.lägre.version”-numret här. Versionsnumret måste motsvara den version som returneras av kommandot ```winver```.

Om en enhet har en tidigare version än den angivna operativsystemversionen rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.

- **Högsta tillåtna version av operativsystemet:** – Stöds på Windows 8.1 och Windows 10.

När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

Du kan ta reda på vilken operativsystemversion som krävs för inställningarna **Lägsta version av operativsystemet som krävs** och **Högsta tillåtna version av operativsystemet** genom att köra kommandot **winver** från Kommandotolken. Kommandot winver returnerar den rapporterade versionen av operativsystemet.

- Datorer med Windows 8.1 returnerar en **3**-version. Om regeln för operativsystemsversion är inställd på Windows 8.1 för Windows rapporteras enheten som inkompatibel även om den har Windows 8.1.
- För datorer som kör Windows 10 anger du versionen som ”10.0” + numret för operativsystemsversionen som returneras av kommandot winver.

## <a name="windows-holographic-for-business-support"></a>Stöd för Windows Holographic for Business

Windows Holographic for Business har stöd för följande inställningar:

- Systemsäkerhet/kryptering

  **Kryptering av datalagring på enheten**.

Om du vill verifiera enhetskryptering på Microsoft HoloLens kan du läsa avsnittet [Verifiera enhetskryptering](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="next-steps"></a>Nästa steg

Se följande avsnitt om du vill lära dig hur du kan övervaka enhetsefterlevnad:

- [Hur du övervakar enhetsefterlevnad](device-compliance-monitor.md)
