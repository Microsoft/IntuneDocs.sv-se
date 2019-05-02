---
title: Skapa en efterlevnadsprincip för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista över alla inställningar som du kan använda när du ställer in efterlevnad för Android-enheter i Microsoft Intune. Ange regler för lösenord, Välj en lägsta eller högsta operativsystemversion, begränsa specifika appar, förhindra att återanvända lösenord och mycket mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7670af46657fed048bfe10b8659eae6d45db7620
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423585"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Inställningar för Android kunna markera enheter som kompatibla eller inte är kompatibla med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln visar en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera i Android-enheter i Intune. Använd inställningarna som en del av din lösning för hantering av mobila enheter, för att markera rotade (jailbreakade) enheter som inte är kompatibla, ange en tillåtna hotnivån, aktivera Google Play-skydd och mycket mer.

Den här funktionen gäller för:

- Android

Som Intune-administratör kan använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Läs mer om efterlevnadsprinciper och eventuella förutsättningar i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). För **Plattform**, välj **Android**.

## <a name="device-health"></a>Device health

- **Rotade enheter**: Välj **Blockera** för att markera rotade (jailbreakade) enheter som inkompatibla. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Kräv att enheten ska vara på eller under hotnivån för enheten**: Använd den här inställningen för att använda riskbedömningen från Lookout MTP-lösningen som ett villkor för efterlevnad. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen. Om du vill använda den här inställningen väljer du den tillåtna hotnivån:
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
> För att konfigurera inställningarna för Google Play-skydd med hjälp av appskyddsprinciper, se [inställningar för Intune-appskyddsprinciper](app-protection-policy-settings-android.md#conditional-launch) på Android.

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som anges i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Den här enheten kan inte komma åt företagsresurser förrän en regel ändras så att operativsystemversionen tillåts.

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

Välj **OK** > **Skapa** för att spara ändringarna.

## <a name="locations"></a>Platser:

Du kan framtvinga efterlevnad av platsen för enheten i din princip. Välj från befintliga platser. Har du inga platser ännu? Du kan läsa mer i [Använda platser (nätverksstängsel) i Intune](use-network-locations.md).

1. Välj **platser** > **välja platser**.
2. Kontrollera din plats i listan > **Välj**.
3. **Spara** principen.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [använda omfångstaggar om du vill filtrera principer](scope-tags.md).
- [Övervaka dina efterlevnadspolicyer](compliance-policy-monitor.md).
- [Inställningar för efterlevnadsprinciper för Android Enterprise](compliance-policy-create-android-for-work.md)
