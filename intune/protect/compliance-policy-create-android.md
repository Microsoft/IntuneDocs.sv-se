---
title: Kompatibilitetsinställningar för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du konfigurerar kompatibilitet för Android-enheter i Microsoft Intune. Ange regler för lösenord, välj en lägsta eller högsta operativsystemversion, begränsa specifika appar, förhindra att lösenord återanvänds och mycket mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4237b54b3ea89fcf75ce5a21f08012f384eed95c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502513"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android-inställningar för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Den här artikeln innehåller en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på Android-enheter i Intune. Använd dessa inställningar som en del av din MDM-lösning för hantering av mobilenheter, t.ex. för att markera rotade (jailbreakade) enheter som inkompatibla, ange en tillåten hotnivå eller aktivera Google Play-skydd.

Den här funktionen gäller för:

- Android

Som Intune-administratör kan du använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Mer om kompatibilitetsprinciper och vad de gör finns i [Komma igång med kompatibilitet](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). För **Plattform**, välj **Android**.

## <a name="device-health"></a>Device health

- **Rotade enheter**: Välj **Blockera** för att markera rotade (jailbreakade) enheter som inkompatibla. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Kräv att enheten ska vara på eller under hotnivån för enheten**: Använd den här inställningen för att använda riskbedömningen från Lookout Mobile Endpoint Security-lösningen som ett villkor för efterlevnad. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen. Om du vill använda den här inställningen väljer du den tillåtna hotnivån:
  - **Säkrad**: Det här alternativet är det säkraste eftersom enheten inte kan ha några hot. Om hot på någon nivå identifieras på enheten betraktas den som inkompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om existerande hot på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög**: Det här alternativet är det minst säkra och det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.

### <a name="google-play-protect"></a>Google Play-skydd

- **Google Play-tjänster har konfigurerats**: **Kräv** att appen Google Play-tjänster är installerad och aktiverad. Google Play-tjänster tillåter säkerhetsuppdateringar, vilket är ett beroende på grundnivå för många säkerhetsfunktioner på certifierade Google-enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Uppdaterad säkerhetsprovider**: **Kräv** att en uppdaterad säkerhetsprovider kan skydda en enhet från kända säkerhetsproblem. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Hotgenomsökning för appar**: **Kräv** att Android-funktionen **Verifiera appar** är aktiverad. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  > [!NOTE]
  > Den här funktionen är en kompatibilitetsinställning på den äldre Android-plattformen. Intune kan bara kontrollera om den här inställningen är aktiverad på enhetsnivå.

- **Attesteringen av enhetens SafetyNet**: Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:
  - **Ej konfigurerad** (standard): Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

> [!NOTE]
> Information om hur du konfigurerar inställningar för Google Play-skydd med hjälp av appskyddsprinciper finns i [Inställningar för appskyddsprinciper i Intune](../apps/app-protection-policy-settings-android.md#conditional-launch) på Android.

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som anges i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Den här enheten kan inte komma åt företagsresurser förrän en regel ändras så att operativsystemversionen tillåts.

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som användarens lösenordet måste innehålla.
- **Krav på lösenordstyp**: Välj om ett lösenord ska innehålla endast numeriska tecken eller en blandning av siffror och andra tecken. Alternativen är:
  - **Enhets standard**: om du vill utvärdera lösen ordet kontrollerar du att du väljer en annan lösen ords grad än **enhetens standardvärde**.
  - **Låg säkerhetsbiometri**
  - **Minst numeriskt** (standard)
  - **Numeriskt avancerat**: Upprepade eller efterföljande siffror, till exempel `1111` eller `1234`, tillåts inte.
  - **Minst alfabetiskt** 
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Lösenordets giltighetstid (dagar)** : Ange antalet dagar tills lösenord upphör att gälla och användaren måste skapa ett nytt lösenord.
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

Välj **OK** > **Skapa** för att spara ändringarna.

## <a name="locations"></a>Platser

I principen kan du framtvinga kompatibilitet baserat på enhetens plats. Välj från befintliga platser. Har du inga platser ännu? Du kan läsa mer i [Använda platser (nätverksstängsel) i Intune](use-network-locations.md).

1. Välj **Platser** > **Välj platser**.
2. Markera din plats i listan > **Välj**.
3. **Spara** principen.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](../fundamentals/scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för Android Enterprise-enheter](compliance-policy-create-android-for-work.md).
