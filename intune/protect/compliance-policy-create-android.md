---
title: Kompatibilitetsinställningar för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du konfigurerar kompatibilitet för Android-enheter i Microsoft Intune. Ange regler för lösenord, välj en lägsta eller högsta operativsystemversion, begränsa specifika appar, förhindra att lösenord återanvänds och mycket mer.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8efb9dcf9129375252b5d9a7d1e6255dce39625c
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801411"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android-inställningar för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

Den här artikeln innehåller en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på Android-enheter i Intune. Använd dessa inställningar som en del av din MDM-lösning för hantering av mobilenheter, t.ex. för att markera rotade (jailbreakade) enheter som inkompatibla, ange en tillåten hotnivå eller aktivera Google Play-skydd.

Den här funktionen gäller för:

- Android-enhetsadministratör

Som Intune-administratör kan du använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Mer om kompatibilitetsprinciper och vad de gör finns i [Komma igång med kompatibilitet](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). För **plattform**väljer du **Android-enhets administratör**.

## <a name="device-health"></a>Enhetens hälsotillstånd

- **Rotade enheter**:

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Blockera** – Markera rotade (jailbreakade) enheter som inkompatibla.

- **Kräv att enheten ligger på eller under enhetshotnivån**:

  Använd den här inställningen för att ta riskbedömningen från en ansluten tjänst för skydd mot mobila hot som ett villkor för efterlevnad.
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen. 
  - **Säkrad** – Det här alternativet är det säkraste eftersom enheten inte kan ha några hot. Om hot på någon nivå identifieras på enheten betraktas den som inkompatibel.
  - **Låg** – Enheten utvärderas som kompatibel om det bara finns lågnivåhot på den. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel** – Enheten utvärderas som kompatibel om befintliga hot på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög** – Det här alternativet är det minst säkra, och det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.

### <a name="google-play-protect"></a>Google Play-skydd

- **Google Play-tjänster har konfigurerats**:

  Google Play-tjänster tillåter säkerhetsuppdateringar, vilket är ett beroende på grundnivå för många säkerhetsfunktioner på certifierade Google-enheter.

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.  
  - **Kräv** – Kräv att Google Play-tjänstappen installeras och aktiveras.  

- **Uppdaterad säkerhetsprovider**:

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** – Kräv att en uppdaterad säkerhetsprovider kan skydda enheten mot kända säkerhetsproblem.

- **Hotgenomsökning för appar**:

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** – Kräv att funktionen **Verifiera appar** i Android har aktiverats.

  > [!NOTE]
  > Den här funktionen är en kompatibilitetsinställning på den äldre Android-plattformen. Intune kan bara kontrollera om den här inställningen är aktiverad på enhetsnivå.

- **SafetyNet-enhetsattestering**:

  Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

> [!NOTE]
> Information om hur du konfigurerar inställningar för Google Play-skydd med hjälp av appskyddsprinciper finns i [Inställningar för appskyddsprinciper i Intune](../apps/app-protection-policy-settings-android.md#conditional-launch) på Android.

## <a name="device-properties"></a>Egenskaper för enhet

### <a name="operating-system-version"></a>Operativsystemversion 

- **Lägsta version av operativsystemet**:

  När en enhet inte uppfyller minimikravet på operativsystemversion, rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.

  *Som standard konfigureras ingen version*.

- **Högsta version av operativsystemet**:

  När en enhet använder en senare version av operativsystemet än den som har specificerats i regeln, så blockeras åtkomsten till företagets resurser. Användaren uppmanas sedan att kontakta IT-administratören. Den här enheten kan inte komma åt företagsresurser förrän en regel ändras så att operativsystemversionen tillåts.

  *Som standard konfigureras ingen version*.

## <a name="system-security"></a>Systemsäkerhet

### <a name="password"></a>Lösenord

<!-- Removed
- **Minimum password length**: Enter the minimum number of digits or characters that the user's password must have.   


- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password. When you choose **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

- **Password expiration (days)**: Select the number of days before the password expires and the user must create a new password.

- **Number of previous passwords to prevent reuse**: Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

-->

- **Kräv ett lösenord för att låsa upp mobila enheter**:

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** – Användarna måste ange ett lösenord innan de får åtkomst till sina enheter.

- **Lösenordstyp som krävs**:

  Välj om ett lösenord endast ska innehålla numeriska tecken, eller en blandning av siffror och andra tecken. Alternativen är:

  - **Enhets standardvärde** – om du vill utvärdera lösen ordet måste du välja en annan lösen ords styrka än **enhetens standardvärde**.
  - **Låg säkerhetsbiometri**
  - **Minst numeriskt**
  - **Numeriskt avancerat** – Upprepade eller efterföljande siffror, till exempel `1111` eller `1234`, tillåts inte.
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**

### <a name="encryption"></a>Kryptering

- **Kryptering av datalagring på en enhet**:  
  *Stöds på Android 4,0 och senare, eller KNOX 4,0 och senare.*

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** kryptering av data lagring på dina enheter. Enheter krypteras när du väljer inställningen **Kräv lösenord för att låsa upp mobila enheter**.

### <a name="device-security"></a>Enhetssäkerhet

- **Blockera appar från okända källor**:

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Blockera** – blockera enheter med **Säkerhet > okända källor** aktiverade källor (*stöds på Android 4,0 via Android 7. x. Stöds inte av Android 8.0 och senare).

  Om du vill att läsa in appar separat, måste okända källor tillåtas. Om du inte läser in Android-appar separat konfigurerar du den här funktionen med **Blockera** om du vill aktivera den här efterlevnadsprincipen.

  > [!IMPORTANT]
  > Inställningen **Blockera appar från okända källor** måste vara aktiverad för program med separat inläsning. Du bör endast tillämpa den här efterlevnadsprincipen om du inte läser in Android-appar separat på enheter.

- **Körningsintegritet för företagsportalappen**:

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** – Välj *Kräv* om du vill bekräfta att företagsportalsappen uppfyller följande krav:

    - Har standardkörningsmiljön installerad
    - Är korrekt signerad
    - Är inte i felsökningsläge
    - Har installerats från en känd källa

- **Blockera USB-felsökning på enheten** *(Android 4,2 eller senare)* :

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Blockera** – Förhindra att enheter använder USB-felsökningsfunktionen.

- **Lägsta säkerhets korrigerings nivå** *(Android 6,0 eller senare)* :

  Välj den äldsta säkerhetskorrigeringsnivå som en enhet kan ha. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste anges i formatet `YYYY-MM-DD`.

  *Inget datum konfigureras som standard*.

- **Begränsade appar**:

  Ange **appnamnet** och **appsamlings-ID:t** för appar som ska vara begränsade, och välj sedan **Lägg till**. En enhet med minst en begränsad app installerad har markerats som inkompatibel.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](../fundamentals/scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för Android Enterprise-enheter](compliance-policy-create-android-for-work.md).
