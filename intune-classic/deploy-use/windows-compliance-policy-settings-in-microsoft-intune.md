---
title: "Inställningar för policy för efterlevnad för Windows-enheter"
description: "Det här avsnittet beskriver de regler och inställningar som du kan konfigurera för en efterlevnadsprincip för Windows-enheter."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f996842c-e9a4-4819-acb4-ee66e8fb35b8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1c9a59fa97c11794ff8ad0a0eaa41630bfdf847e
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="compliance-policy-settings-for-windows-devices-in-microsoft-intune"></a>Inställningar för efterlevnadsprinciper för Windows-enheter i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Principinställningarna som beskrivs i det här avsnittet gäller enheter som kör Windows-operativsystemet. I följande avsnitt beskrivs de Windows-versioner som stöds.

Om du letar efter information om andra plattformar väljer du något av följande:
> [!div class="op_single_selector"]
- [Inställningar för policy för efterlevnad för iOS-enheter](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för policy för efterlevnad för Android-enheter](android-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för policy för efterlevnad för Android for Work-enheter](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="compliance-policy-settings-for-windows-phone-devices"></a>Inställningar för efterlevnadsprinciper för Windows Phone-enheter
Inställningarna i det här avsnittet stöds på Windows Phone 8.1 och senare.

### <a name="system-security-settings"></a>Inställningar för systemsäkerhet
#### <a name="password"></a>Lösenord
- **Kräv lösenord för att låsa upp mobila enheter:** Välj **Ja** om du vill kräva att användarna anger ett lösenord för att få åtkomst till sina enheter.

- **Tillåt enkla lösenord**: Välj **Ja** om du vill att användaren ska kunna skapa enkla lösenord som **1234** eller **1111**.

-  **Minsta längd på lösenord**: Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.
- **Krav på lösenordstyp**: Ange om användaren måste skapa ett **alfanumeriskt** lösenord eller ett **numeriskt** lösenord.

  För enheter som kör Windows och som nås med ett Microsoft-konto utvärderas efterlevnadsprincipen inte korrekt om Minsta längd på lösenord är större än åtta tecken eller om Minsta antal teckenuppsättningar är större än två.

- **Minsta antal teckenuppsättningar:** Om alternativet för **Krav på lösenordstyp** är **Alfanumeriskt** anger den här inställningen det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
  -   Gemener
  -   Versaler
  -   Symboler
  -   Siffror

  Om du anger en hög siffra för den här inställningen måste användaren skapa ett lösenord som är mer komplext. För enheter som kör Windows och som nås med ett Microsoft-konto utvärderas efterlevnadsprincipen inte korrekt om Minsta längd på lösenord är större än åtta tecken eller om Minsta antal teckenuppsättningar är större än två.

- **Minuter av inaktivitet innan lösenord måste anges:** Den här inställningen anger efter hur lång tids inaktivitet som användaren måste ange lösenordet igen.

- **Lösenordets giltighetstid (dagar)**: Välj antalet dagar tills användarens lösenord upphör att gälla och användaren måste ange ett nytt lösenord.

- **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.

- **Förhindra återanvändning av tidigare lösenord**: Om **Spara lösenordshistorik** har valts anger du hur många tidigare använda lösenord som inte får återanvändas.
- **Kräv lösenord när enheten lämnar inaktivt läge**: Använd den här inställningen tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Användaren uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.

  > [!NOTE]
  > Den här inställningen gäller endast för Windows 10 Mobile-enheter.

#### <a name="encryption"></a>Kryptering
- **Kräv kryptering på den mobila enheten:** Välj **Ja** för den här inställningen om du vill kräva att enheten ska krypteras för att ansluta till resurser.

### <a name="device-health-settings"></a>Inställningar för enhetens hälsotillstånd
- **Kräv att enheter ska rapporteras som felfria:** Du kan ange en regel för att kräva att **Windows 10 Mobile**-enheter rapporteras som felfria i nya eller befintliga efterlevnadsprinciper.  Om den här inställningen är aktiverad utvärderas Windows 10-enheter via hälsoattesteringstjänsten (HAS) för följande datapunkter:
  -  **BitLocker är aktiverat:** Om BitLocker är aktiverat kan enheten skydda data mot obehörig åtkomst när datorn är avstängd eller försätts i viloläge. Med Windows BitLocker-diskkryptering krypteras alla data på volymen för Windows-operativsystemet. BitLocker använder TPM för att skydda Windows-operativsystemet och användardata. BitLocker kan också se till att en dator inte manipuleras, även om den lämnas obevakad, tappas bort eller blir stulen. Om datorn är utrustad med en kompatibel TPM använder BitLocker TPM för att låsa krypteringsnycklarna som skyddar data. Därför är nycklarna inte tillgängliga förrän TPM-modulen har verifierat datorns tillstånd.
  -  **Kodintegritet är inte aktiverat:** Kodintegritet är en funktion som kontrollerar integriteten för en drivrutin eller systemfil varje gång den läses in i minnet. Kodintegritet kontrollerar om en osignerad drivrutin eller systemfil läses in i kerneln. Funktionen kontrollerar också om en fil har ändrats av skadlig programvara som körs av ett användarkonto med administratörsbehörighet.
  - **Säker start är aktiverat:** När säker start är aktiverat tvingas systemet att starta i ett fabriksinställt betrott läge. När säker start är aktiverat måste huvudkomponenterna som används för att starta datorn dessutom ha rätt kryptografiska signaturer som är betrodda av den organisation som tillverkade enheten. UEFI-baserad inbyggd programvara kontrollerar detta innan den låter datorn starta. Om filer har manipulerats som gör att signaturen skadas, så startar inte datorn.

  > [!IMPORTANT]
  > Windows-enheter stöder inte **tidig lansering av program mot skadlig kod (Early Launch Anti Malware)** från tredje part som installerats som en del av attesteringen av enhetens hälsotillstånd.

  Mer information om hur hälsoattesteringstjänsten fungerar finns i avsnittet om [kryptografiprovidern för hälsoattesteringstjänsten](https://msdn.microsoft.com/library/dn934876.aspx).
###  <a name="device-property-settings"></a>Inställningar för enhetsegenskaper
- **Lägsta operativsystemversion som krävs**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel.
    En länk med information om hur du uppgraderar visas. Användaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.

- **Högsta tillåtna version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.


## <a name="compliance-policy-settings-for-windows-pcs"></a>Inställningar för efterlevnadsprinciper för Windows-datorer
Inställningarna i det här avsnittet stöds på Windows-datorer.
### <a name="system-security-settings"></a>Inställningar för systemsäkerhet
#### <a name="password"></a>Lösenord
- **Minsta längd på lösenord**: Stöds i Windows 8.1.

  Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.

  För enheter som nås med ett Microsoft-konto utvärderas efterlevnadsprincipen inte korrekt om **Minsta längd på lösenord** är längre än åtta tecken eller om **Minsta antal teckenuppsättningar** är större än två.

- **Krav på lösenordstyp**: Stöds på Windows RT, Windows RT 8.1 och Windows 8.1.

  Ange om användaren måste skapa ett **alfanumeriskt** lösenord eller ett **numeriskt** lösenord.

- **Minsta antal teckenuppsättningar**: Stöds på Windows RT, Windows RT 8.1 och Windows 8.1.

  Om alternativet för **Krav på lösenordstyp** är **Alfanumeriskt** anger den här inställningen det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
  -   Gemener
  -   Versaler
  -   Symboler
  -   Siffror     

  Om du anger en hög siffra för den här inställningen måste användaren skapa ett lösenord som är mer komplext. För enheter som nås med ett Microsoft-konto utvärderas efterlevnadsprincipen inte korrekt om **Minsta längd på lösenord** är längre än åtta tecken eller om **Minsta antal teckenuppsättningar** är större än två.

- **Minuter av inaktivitet innan lösenord måste anges**: Stöds på Windows RT, Windows RT 8.1 och Windows 8.1.

  Ange efter hur lång tids inaktivitet som användaren måste ange sitt lösenord igen.

- **Lösenordets giltighetstid (dagar)**: Stöds på Windows RT, Windows RT 8.1 och Windows 8.1.

  Välj antalet dagar tills användarens lösenord upphör att gälla och användaren måste ange ett nytt lösenord.

- **Spara lösenordshistorik**: Stöds på Windows RT, Windows RT och Windows 8.1.

  Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.

- **Förhindra återanvändning av tidigare lösenord:** Stöds på Windows RT, Windows RT 8.1 och Windows 8.1.

  Om **Spara lösenordshistorik** har valts anger du hur många tidigare använda lösenord som inte får återanvändas.

### <a name="device-health-settings"></a>Inställningar för enhetens hälsotillstånd
- **Kräv att enheter ska rapporteras som felfria**: Stöds på Windows 10-enheter.
Du kan ange en regel för att begära att Windows 10-enheter rapporteras som felfria i nya eller befintliga efterlevnadsprinciper. Om den här inställningen är aktiverad utvärderas Windows 10-enheter via hälsoattesteringstjänsten (HAS) för följande datapunkter:
  -  **BitLocker är aktiverat:** Om BitLocker är aktiverat kan enheten skydda data mot obehörig åtkomst när datorn är avstängd eller försätts i viloläge. Med Windows BitLocker-diskkryptering krypteras alla data på volymen för Windows-operativsystemet. BitLocker använder TPM för att skydda Windows-operativsystemet och användardata. BitLocker kan också se till att en dator inte manipuleras, även om den lämnas obevakad, tappas bort eller blir stulen. Om datorn är utrustad med en kompatibel TPM använder BitLocker TPM för att låsa krypteringsnycklarna som skyddar data. Därför är nycklarna inte tillgängliga förrän TPM-modulen har verifierat datorns tillstånd.
  -  **Kodintegritet är inte aktiverat:** Kodintegritet är en funktion som kontrollerar integriteten för en drivrutin eller systemfil varje gång den läses in i minnet. Kodintegritet kontrollerar om en osignerad drivrutin eller systemfil läses in i kerneln. Funktionen kontrollerar också om en fil har ändrats av skadlig programvara som körs av ett användarkonto med administratörsbehörighet.
  - **Säker start är aktiverat:** När säker start är aktiverat tvingas systemet att starta i ett fabriksinställt betrott läge. När säker start är aktiverat måste huvudkomponenterna som används för att starta datorn dessutom ha rätt kryptografiska signaturer som är betrodda av den organisation som tillverkade enheten. UEFI-baserad inbyggd programvara kontrollerar detta innan den låter datorn starta. Om filer har manipulerats som gör att signaturen skadas, så startar inte datorn.
  - **Tidig lansering av program mot skadlig kod:** Tidig lansering av program mot skadlig kod (ELAM) ger skydd för datorer i nätverket när de startar och innan drivrutiner från tredje part initieras.

  Mer information om hur hälsoattesteringstjänsten fungerar finns i avsnittet om [kryptografiprovidern för hälsoattesteringstjänsten](https://msdn.microsoft.com/library/dn934876.aspx).

### <a name="device-property-settings"></a>Inställningar för enhetsegenskaper
- **Lägsta version av operativsystemet som krävs**: Stöds på Windows 8.1 och Windows 10.

  Ange ”högre.lägre.version”-numret här. Versionsnumret måste motsvara den version som returneras av kommandot **winver**.

  Om en enhet har en tidigare version än den angivna operativsystemsversionen rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Användaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.

- **Högsta tillåtna version av operativsystemet**: Stöds på Windows 8.1 och Windows 10.

  När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

Du kan ta reda på vilken operativsystemversion som krävs för inställningarna **Lägsta version av operativsystemet som krävs** och **Högsta tillåtna version av operativsystemet** genom att köra kommandot **winver** från Kommandotolken. Kommandot **winver** returnerar den rapporterade versionen av operativsystemet.

- Datorer med Windows 8.1 returnerar en **6.3**-version. Om regeln för operativsystemsversion är inställd på Windows 8.1 för Windows rapporteras enheten som inkompatibel även om den har Windows 8.1.

- För datorer som kör Windows 10 bör versionen anges som **10.0** plus OS-versionsnumret som returneras av kommandot **winver**. Det kan till exempel vara något liknande 10.0.10586.
> ![OS-versionsnumret visas i dialogrutan ”Om Windows”](./media/ca_win10-os-version.png)
