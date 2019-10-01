---
title: Kompatibilitetsinställningar för Android Enterprise i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du ställer in kompatibilitet för Android Enterprise-enheter i Microsoft Intune. Ange regler för lösenord, välj en lägsta eller högsta operativsystemversion, begränsa specifika appar, förhindra att lösenord återanvänds och mycket mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6351aa7adf9d9d5ca333bb2bd97e552e6f1e156
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71304143"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android Enterprise-inställningar för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln innehåller en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på Android Enterprise-enheter i Intune. Använd dessa inställningar som en del av din MDM-lösning för hantering av mobilenheter, t.ex. för att markera rotade (jailbreakade) enheter som inkompatibla, ange en tillåten hotnivå eller aktivera Google Play-skydd.

Den här funktionen gäller för:

- Android enterprise

Som Intune-administratör kan du använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Mer om kompatibilitetsprinciper och vad de gör finns i [Komma igång med kompatibilitet](device-compliance-get-started.md).

> [!IMPORTANT]
> Efterlevnadsprinciper tillämpar även Android Enterprise-dedikerade enheter. Om en efterlevnadsprincip tilldelas till en dedikerad enhet kan enheten visas som **Ej kompatibel**. Villkorlig åtkomst och framtvingande av efterlevnad är inte tillgängligt på dedikerade enheter. Se till att slutföra alla uppgifter eller åtgärder för att göra så att dedikerade enheter uppfyller dina tilldelade principer.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). Välj **Android Enterprise** för **Plattform**.

## <a name="device-owner"></a>Enhetens ägare

### <a name="device-health"></a>Enhetens hälsotillstånd

- **Kräv att enheten ska vara på eller under enhets hotnivå**: Välj den högsta tillåtna hot nivån på enhet som har utvärderats av [tjänsten för skydd mot mobila hot](mobile-threat-defense.md). Enheter som överskrider den här hotnivå markeras som inkompatibla. Om du vill använda den här inställningen väljer du den tillåtna hotnivån:

  - **Ej konfigurerad** (standard): Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Skyddad**: Det här alternativet är säkrast och innebär att enheten inte kan ha några hot. Om hot på någon nivå identifieras på enheten betraktas den som inkompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög**: Det här alternativet är det minst säkra då det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
  
> [!NOTE] 
> Följande leverantörer av Mobile Threat försvar (MTD) stöder Android Enterprise-distribution av enhets ägare med hjälp av app-konfiguration:
> - Better Mobile 
> - Pradeo
> - Sophos Mobile
> - Zimperium 
>  
>  Kontrol lera med din MTD-Provider om du vill ha den exakta konfigurationen som krävs för att stödja Android Enterprise-enhetens ägar plattformar på Intune. Den här listan uppdateras eftersom MTD-delar har stöd för Android-scenarier för företags enhets ägare. 

#### <a name="google-play-protect"></a>Google Play-skydd

- **Attesteringen av enhetens SafetyNet**: Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:
  - **Ej konfigurerad** (standard): Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

### <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan uppgradera enheten och sedan få åtkomst till organisationens resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den i regeln blockeras åtkomsten till organisationsresurser. Användaren uppmanas att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän regeln ändras så att operativsystemversionen tillåts.

### <a name="system-security"></a>Systemsäkerhet

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  Den här inställningen tillämpas på enhetsnivå. Om du bara behöver kräva ett lösenord på arbetsprofilnivå, använder du en konfigurationsprincip. Mer information finns i avsnittet om [konfigurationsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

  - **Krav på lösenordstyp**: Välj om ett lösenord ska innehålla endast numeriska tecken eller en blandning av siffror och andra tecken. Alternativen är:
    - **Enhets standard**: om du vill utvärdera lösen ordet kontrollerar du att du väljer en annan lösen ords grad än **enhetens standardvärde**.  
    - **Lösenord krävs, inga begränsningar**
    - **Svag biometrik**: [Stark eller svag biometri](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (öppnar Androids webbplats)
    - **Numeriskt** (standard): Lösenordet får bara innehålla siffror, till exempel `123456789`. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
    - **Numeriskt avancerat**: Upprepade eller efterföljande siffror, till exempel ”1111” eller ”1234”, tillåts inte. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
    - **Alfabetiskt**: Bokstäver i alfabetet krävs. Siffror och symboler krävs inte. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
    - **Alfanumeriskt**: Innehåller versaler, gemener och numeriska tecken. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
    - **Alfanumeriskt med symboler**: Innehåller versaler, gemener, numeriska tecken, skiljetecken och symboler. Ange även:

      - **Minsta längd på lösenord**: Ange den minsta längd som lösenordet måste ha (mellan 4 och 16 tecken).
      - **Antal tecken som krävs**: Ange hur många tecken som lösenordet måste innehålla (mellan 0 och 16 tecken).
      - **Antal gemener som krävs**: Ange hur många gemener som lösenordet måste innehålla (mellan 0 och 16 tecken).
      - **Antal versaler som krävs** : Ange hur många versaler som lösenordet måste innehålla (mellan 0 och 16 tecken).
      - **Antal icke-bokstavstecken som krävs**: Ange hur många icke-bokstavstecken (bokstäver som inte ingår i alfabetet) som lösenordet måste innehålla (mellan 0 och 16 tecken).
      - **Antal numeriska tecken som krävs**: Ange hur många numeriska tecken (till exempel `1`, `2` eller `3`) som lösenordet måste innehålla (mellan 0 och 16 tecken).
      - **Antal symboltecken som krävs**: Ange hur många symboltecken (till exempel `&`, `#` eller `%`) som lösenordet måste innehålla (mellan 0 och 16 tecken).

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Antal dagar tills lösenordet går ut**: Ange antal dagar innan lösenordet för enheten måste ändras (mellan 1 och 365). Exempel: Om du vill att lösenordet ska ändras om 60 dagar anger du `60`. När lösenordet upphör att gälla uppmanas användarna att skapa ett nytt lösenord.
- **Antal lösenord som krävs innan användaren kan återanvända ett lösenord**: Ange hur många av de senast använda lösenorden som inte kan återanvändas (mellan 1 och 24). Använd den här inställningen för att förhindra att användaren återanvänder tidigare använda lösenord.

- **Kryptering för lagring av data på en enhet**: Välj **Kräv** för att kryptera lagring av data på dina enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  Du behöver inte konfigurera den här inställningen eftersom Android Enterprise-enheter tvingar fram kryptering.

## <a name="work-profile"></a>Arbetsprofil

### <a name="device-health"></a>Device health

- **Rotade enheter**: Välj **Blockera** för att markera rotade (jailbreakade) enheter som inkompatibla. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Kräv att enheten ska vara på eller under enhets hotnivå**: Välj den högsta tillåtna hot nivån på enhet som har utvärderats av [tjänsten för skydd mot mobila hot](mobile-threat-defense.md). Enheter som överskrider den här hotnivå markeras som inkompatibla. Om du vill använda den här inställningen väljer du den tillåtna hotnivån:

  - **Ej konfigurerad** (standard): Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Skyddad**: Det här alternativet är säkrast och innebär att enheten inte kan ha några hot. Om hot på någon nivå identifieras på enheten betraktas den som inkompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög**: Det här alternativet är det minst säkra då det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.

#### <a name="google-play-protect"></a>Google Play-skydd

- **Google Play-tjänster har konfigurerats**: **Kräv** att appen Google Play-tjänster är installerad och aktiverad. Google Play-tjänster tillåter säkerhetsuppdateringar, vilket är ett beroende på grundnivå för många säkerhetsfunktioner på certifierade Google-enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Uppdaterad säkerhetsprovider**: **Kräv** att en uppdaterad säkerhetsprovider kan skydda en enhet från kända säkerhetsproblem. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Attesteringen av enhetens SafetyNet**: Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:
  - **Ej konfigurerad** (standard): Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

> [!NOTE]
> På Android Enterprise-enheter är **Hotgenomsökning för appar** en enhetskonfigurationsprincip. Administratörer kan aktivera inställningen på en enhet med hjälp av en konfigurationsprincip. Mer information finns i avsnittet om [begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan uppgradera enheten och sedan få åtkomst till organisationens resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den i regeln blockeras åtkomsten till organisationsresurser. Användaren uppmanas att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän regeln ändras så att operativsystemversionen tillåts.

### <a name="system-security"></a>Systemsäkerhet

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen. Den här inställningen tillämpas på enhetsnivå. Om du bara behöver kräva ett lösenord på arbetsprofilnivå, använder du en konfigurationsprincip. Mer information finns i avsnittet om [konfigurationsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).
- **Krav på lösenordstyp**: Välj om ett lösenord ska innehålla endast numeriska tecken eller en blandning av siffror och andra tecken. Alternativen är:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Lägst antal siffror** (standard): Ange den **minsta längd på ett lösenord** som en användare måste ange (mellan 4 och 16 tecken).
  - **Numeriskt komplext**: Ange den **minsta längd på ett lösenord** som en användare måste ange (mellan 4 och 16 tecken).
  - **Lägst antal siffror**: Ange den **minsta längd på ett lösenord** som en användare måste ange (mellan 4 och 16 tecken).
  - **Lägst antal siffror och bokstäver**: Ange den **minsta längd på ett lösenord** som en användare måste ange (mellan 4 och 16 tecken).
  - **Minst alfanumeriskt med symboler**: ange **minsta längd på lösen ord** som en användare måste ange, mellan 4 och 16 tecken.

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Antal dagar tills lösenordet upphör**: Ange antalet dagar tills lösenord upphör att gälla och användaren måste skapa ett nytt lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Ange antalet senast använda lösenord som inte får återanvändas. Använd den här inställningen för att förhindra att användaren återanvänder tidigare använda lösenord.

#### <a name="encryption"></a>Kryptering

- **Kryptering för lagring av data på en enhet**: Välj **Kräv** för att kryptera lagring av data på dina enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen. 

  Du behöver inte konfigurera den här inställningen eftersom Android Enterprise-enheter tvingar fram kryptering.

#### <a name="device-security"></a>Enhetssäkerhet

- **Blockera appar från okända källor**: Välj att **blockera** enheter med **Säkerhet** > **Okända källor**-aktiverade källor (stöds på Android 4.0 – Android 7.x; stöds inte av Android 8.0 och senare). Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  Om du vill att läsa in appar separat, måste okända källor tillåtas. Om du inte läser in Android-appar separat konfigurerar du den här funktionen med **Blockera** om du vill aktivera den här efterlevnadsprincipen.

  > [!IMPORTANT]
  > Inställningen **Blockera appar från okända källor** måste vara aktiverad för program med separat inläsning. Du bör endast tillämpa den här efterlevnadsprincipen om du inte läser in Android-appar separat på enheter.

  Du behöver inte konfigurera den här inställningen eftersom Android Enterprise-enheter alltid begränsar installationer från okända källor.

- **Körningsintegritet för appen Företagsportal**: Välj **Kräv** för att bekräfta att företagsportalappen uppfyller följande krav:

  - Har standardkörningsmiljön installerad
  - Är korrekt signerad
  - Är inte i felsökningsläge
  - Har installerats från en känd källa

  Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

- **Blockera USB-felsökning på enheten**: Välj **Blockera** för att förhindra att enheter använder USB-felsökningsfunktionen. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  Du behöver inte konfigurera den här inställningen eftersom USB-felsökning redan är inaktiverat på Android Enterprise-enheter.

- **Lägsta säkerhetskorrigeringsnivå**: Välj den äldsta säkerhetskorrigeringsnivå som en enhet kan ha. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste anges i formatet *ÅÅÅÅ-MM-DD*.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för Android-enheter](compliance-policy-create-android.md).
