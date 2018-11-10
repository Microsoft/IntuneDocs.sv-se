---
title: Skapa en efterlevnadsprincip för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa eller konfigurera en enhetsefterlevnadsprincip i Microsoft Intune för Android-enheter. Välj att tillåta jailbrokade enheter, ställ in godkänd hotnivå, kontrollera efter Google Play, ange lägsta och högsta operativsystemversion, välj dina lösenordskrav och tillåt program med separat inläsning.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1108a208a324b5ed4c46248dc986dcf08e6293fe
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236551"
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Lägg till en efterlevnadsprincip för Android-enheter i Intune

En Intune-enhetsefterlevnadsprincip för Android anger de regler och inställningar som Android-enheter måste uppfylla för att anses vara kompatibla. Du kan använda dessa principer med [villkorsstyrd åtkomst](conditional-access.md) för att tillåta eller blockera åtkomst till organisationens resurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet. 

Läs mer om efterlevnadsprinciper och eventuella förutsättningar i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

Det här avsnittet innehåller de inställningar som du kan använda i en efterlevnadsprincip för Android-enheter.

## <a name="non-compliance-and-conditional-access"></a>Inkompatibilitet och villkorlig åtkomst

Följande tabell beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

--------------------

|**Principinställning**| **Android 4.0 och senare, Samsung Knox Standard 4.0 och senare** |
| --- | ----|
| **Konfiguration av PIN-kod eller lösenord** |  I karantän |
| **Enhetskryptering** | I karantän |
| **Jailbreakad eller rotad enhet** | I karantän (inte en inställning) |
| **e-postprofil** | Inte tillämpligt |
| **Lägsta version av operativsystemet** | I karantän |
| **Högsta version av operativsystemet** |   I karantän |
| **Attestering av hälsotillstånd i Windows** | Inte tillämpligt |

--------------------------

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. Till exempel om användaren tvingas att ange en PIN-kod.

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. Till exempel om Android-enheter inte tvingar användaren att kryptera enheten. När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

  - Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
  - Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. För **Plattform**, välj **Android**. 
5. Välj **Konfigurera inställningar**. Ange inställningar för **Enhetens hälsotillstånd**, **Enhetsegenskaper** och **Systemsäkerhet** genom att följa anvisningarna i den här artikeln.

## <a name="device-health"></a>Device health

- **Rotade enheter**: Välj **Blockera** för att markera rotade (jailbreakade) enheter som inkompatibla. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Kräv att enheten ska vara på eller under hotnivån för enheten**: Använd den här inställningen för att använda riskbedömningen från Lookout MTP-lösningen som ett villkor för efterlevnad. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen. Om du vill använda den här inställningen väljer du den tillåtna hotnivån:
  - **Säkrad**: Det här alternativet är det säkraste eftersom enheten inte kan ha några hot. Om hot på någon nivå identifieras på enheten betraktas den som inkompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om existerande hot på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög**: Det här alternativet är det minst säkra och det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
- **Google Play-tjänster har konfigurerats**: **Kräv** att appen Google Play-tjänster är installerad och aktiverad. Google Play-tjänster tillåter säkerhetsuppdateringar, vilket är ett beroende på grundnivå för många säkerhetsfunktioner på certifierade Google-enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Uppdaterad säkerhetsprovider**: **Kräv** att en uppdaterad säkerhetsprovider kan skydda en enhet från kända säkerhetsproblem. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Hotgenomsökning för appar**: **Kräv** att Android-funktionen **Verifiera appar** är aktiverad. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  > [!NOTE]
  > Den här funktionen är en kompatibilitetsinställning på den äldre Android-plattformen. Intune kan bara kontrollera om den här inställningen är aktiverad på enhetsnivå.

- **Attesteringen av enhetens SafetyNet**: Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:
  - **Ej konfigurerad** (standard): Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som anges i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Den här enheten kan inte komma åt företagsresurser förrän en regel ändras att tillåta operativsystemversionen.

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som användarens lösenordet måste innehålla.
- **Krav på lösenordstyp**: Välj om ett lösenord ska innehålla endast numeriska tecken eller en blandning av siffror och andra tecken. Alternativen är:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Minst numeriskt** (standard)
  - **Numeriskt avancerat**: Upprepade eller efterföljande siffror, till exempel `1111` eller `1234`, tillåts inte.
  - **Minst alfabetiskt** 
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Lösenordets giltighetstid (dagar)**: Ange antalet dagar tills lösenord upphör att gälla och användaren måste skapa ett nytt lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Ange antalet senast använda lösenord som inte får återanvändas. Använd den här inställningen för att förhindra att användaren återanvänder tidigare använda lösenord.

### <a name="encryption"></a>Kryptering

- **Kryptering för lagring av data på en enhet** (Android 4.0 och senare, eller KNOX 4.0 och senare): Välj **Kräv** för att kryptera lagring av data på dina enheter. Enheter krypteras när du väljer inställningen **Kräv lösenord för att låsa upp mobila enheter**. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

### <a name="device-security"></a>Enhetssäkerhet

- **Blockera appar från okända källor**: Välj att **blockera** enheter med ”Säkerhet > Okända källor”-aktiverade källor (stöds på Android 4.0 – Android 7.x; stöds inte av Android 8.0 och senare). Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  Om du vill att läsa in appar separat, måste okända källor tillåtas. Om du inte läser in Android-appar separat konfigurerar du den här funktionen med **Blockera** om du vill aktivera den här efterlevnadsprincipen. 

  > [!IMPORTANT]
  > Inställningen **Blockera appar från okända källor** måste vara aktiverad för program med separat inläsning. Du bör endast tillämpa den här efterlevnadsprincipen om du inte läser in Android-appar separat på enheter.

- **Körningsintegritet för appen Företagsportal**: Välj **Kräv** för att bekräfta att företagsportalappen uppfyller följande krav:

  - Har standardkörningsmiljön installerad
  - Är korrekt signerad
  - Är inte i felsökningsläge
  - Har installerats från en känd källa

  Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

- **Blockera USB-felsökning på enheten** (Android 4.2 eller senare): Välj **Blockera** för att förhindra att enheter använder funktionen USB-felsökning. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Lägsta säkerhetskorrigeringsnivå** (Android 6.0 eller senare): Välj den äldsta säkerhetskorrigeringsnivå som en enhet kan ha. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste anges i formatet `YYYY-MM-DD`.
- **Begränsade appar**: Ange **appnamnet** och **appsamlings-ID:t** för appar som ska vara begränsade. Välj **Lägg till**. En enhet med minst en begränsad app installerad har markerats som inkompatibel.

När du är klar väljer du **OK** > **OK** för att spara dina ändringar.

## <a name="locations"></a>Platser

Välj bland befintliga platser i din princip. Har du inga platser ännu? Du kan läsa mer i [Använda platser (nätverksstängsel) i Intune](use-network-locations.md).

1. Välj **Platser**.
2. Välj en plats från listan och välj **Välj**.
3. **Spara** principen.

## <a name="actions-for-noncompliance"></a>Åtgärder för inkompatibilitet

Välj **Åtgärder för inkompatibilitet**. Standardåtgärden markerar enheten som inkompatibel omedelbart.

Du kan ändra schemat när enheten har markerats som inkompatibel, till exempel efter en dag. Du kan också konfigurera en andra åtgärd som skickar ett e-postmeddelande till användaren när enheten inte är kompatibel.

[Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) innehåller mer information, inklusive anvisningar för hur du skapar ett e-postmeddelande till användarna.

Anta till exempel att du använder funktionen Platser och lägger till en plats i en efterlevnadsprincip. Standardåtgärden för inkompatibilitet tillämpas när du väljer minst en plats. Om enheten inte är ansluten till de valda platserna utvärderas den omedelbart som inkompatibel. Du kan ge användarna en respitperiod, till exempel en dag.

## <a name="scope-tags"></a>Omfångstaggar

Omfångstaggar är ett bra sätt att tilldela principer till specifika grupper, till exempel Försäljning, Teknik, HR och så vidare. Du kan lägga till omfångstaggar till efterlevnadsprinciper. Mer information finns i avsnittet [Använda omfångstaggar för att filtrera principer](scope-tags.md). 

## <a name="assign-user-groups"></a>Tilldela användargrupper

När en princip har skapats gör den inte något förrän du tilldelar principen. Så här tilldelar du principen: 

1. Välj en princip som du har konfigurerat. Befintliga principer finns i **Enhetsefterlevnad** > **Principer**.
2. Välj principen och välj **Tilldelningar**. Du kan inkludera eller exkludera säkerhetsgrupper i Azure Active Directory (AD).
3. Välj **Valda grupper** för att se dina Azure AD-säkerhetsgrupper. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj **Spara** för att distribuera principen till användare.

Du har tillämpat principen på användarna. Enheter som används av användare som omfattas av principen utvärderas för att kontrollera att de är kompatibla.

## <a name="next-steps"></a>Nästa steg
[Automatisera e-post och lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md)  
[Övervaka efterlevnadsprinciper för Intune-enheter](compliance-policy-monitor.md)  
[Inställningar för efterlevnadsprinciper för Android Enterprise](compliance-policy-create-android-for-work.md)
