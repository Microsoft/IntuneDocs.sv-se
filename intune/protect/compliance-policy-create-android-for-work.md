---
title: Kompatibilitetsinställningar för Android Enterprise i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du ställer in kompatibilitet för Android Enterprise-enheter i Microsoft Intune. Ange regler för lösenord, välj en lägsta eller högsta operativsystemversion, begränsa specifika appar, förhindra att lösenord återanvänds och mycket mer.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/07/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 60244bb268f7becadc427c397d7c2d1562bcf6b5
ms.sourcegitcommit: ea81ad5f33f18d9fe43254e27e02de5eaef74a05
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/07/2020
ms.locfileid: "75722614"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android Enterprise-inställningar för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

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

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Skyddad** – Det här alternativet är säkrast och innebär att enheten inte kan ha några hot. Om hot på någon nivå identifieras på enheten betraktas den som inkompatibel.
  - **Låg** – Enheten utvärderas som kompatibel om det bara finns lågnivåhot på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel** – Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög** – Det här alternativet är det minst säkra då det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
  
> [!NOTE] 
> Alla MTD-leverantörer (Mobile Threat försvar) stöds på Android Enterprise-enhets ägar distributioner med hjälp av app-konfiguration. Kontrol lera med din MTD-Provider om du vill ha den exakta konfigurationen som krävs för att stödja Android Enterprise-enhetens ägar plattformar på Intune.

#### <a name="google-play-protect"></a>Google Play-skydd

- **SafetyNet-enhetsattestering**: Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

### <a name="device-properties"></a>Egenskaper för enhet

#### <a name="operating-system-version"></a>Operativsystemversion

- **Lägsta version av operativsystemet**: När en enhet inte uppfyller minimikravet på operativsystemversion, rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan uppgradera enheten och sedan få åtkomst till organisationens resurser.

  *Som standard konfigureras ingen version*.

- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den i regeln blockeras åtkomsten till organisationsresurser. Användaren uppmanas att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän regeln ändras så att operativsystemversionen tillåts.

  *Som standard konfigureras ingen version*.

- **Lägsta säkerhetskorrigeringsnivå**:  Välj den äldsta säkerhetskorrigeringsnivå som en enhet kan ha. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste anges i formatet YYYY-MM-DD.

  *Inget datum konfigureras som standard*.


### <a name="system-security"></a>Systemsäkerhet

- **Kräv ett lösenord för att låsa upp mobila enheter**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** – Användarna måste ange ett lösenord innan de får åtkomst till sina enheter. 

  Den här inställningen gäller på enhets nivå. Om du bara behöver kräva ett lösenord på arbetsprofilnivå, använder du en konfigurationsprincip. Mer information finns i avsnittet om [konfigurationsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).

  - **Lösenordstyp som krävs**: Välj om ett lösenord endast ska innehålla numeriska tecken, eller en blandning av siffror och andra tecken. Alternativen är:
    - **Enhets standardvärde** – om du vill utvärdera lösen ordet måste du välja en annan lösen ords styrka än **enhetens standardvärde**.  
    - **Lösenord krävs, inga begränsningar**
    - **Svag biometrik** - [Stark eller svag biometri](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (öppnar Androids webbplats)
    - **Numeriskt** (*standard*): Lösenordet får bara innehålla siffror, till exempel `123456789`. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
    - **Numeriskt avancerat** – Upprepade eller efterföljande siffror, till exempel ”1111” eller ”1234”, tillåts inte. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
    - **Alfabetiskt** – Bokstäver i alfabetet måste anges. Siffror och symboler krävs inte. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
    - **Alfanumeriskt** – Innehåller versaler, gemener och numeriska tecken. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
    - **Alfanumeriskt med symboler** – Innehåller versaler, gemener, numeriska tecken, skiljetecken och symboler. Ange även:
    
    Beroende på vilken *lösen ords typ* du väljer är följande inställningar tillgängliga:  
    - **Minsta lösenordslängd**: Ange den minsta längd som lösenordet måste ha (mellan 4 och 16 tecken).  

    - **Antal tecken som krävs**: Ange hur många tecken som lösenordet måste innehålla (mellan 0 och 16 tecken).

    - **Antal gemener som krävs**: Ange hur många gemener som lösenordet måste innehålla (mellan 0 och 16 tecken).

    - **Antal versaler som krävs**: Ange hur många versaler som lösenordet måste innehålla (mellan 0 och 16 tecken).

    - **Antal icke-bokstavstecken som krävs**: Ange hur många icke-bokstavstecken (bokstäver som inte ingår i alfabetet) som lösenordet måste innehålla (mellan 0 och 16 tecken).

    - **Antal numeriska tecken som krävs**: Ange hur många numeriska tecken (till exempel `1`, `2` eller `3`) som lösenordet måste innehålla (mellan 0 och 16 tecken).
    
    - **Antal symboltecken som krävs**: Ange hur många symboltecken (till exempel `&`, `#` eller `%`) som lösenordet måste innehålla (mellan 0 och 16 tecken).
 
- **Maximalt antal minuters inaktivitet innan lösenord krävs**: Ange efter hur lång tids inaktivitet som användaren måste ange sitt lösenord igen. Alternativen inkluderar standardvärdet *inte konfigurerad*och från *1 minut* till *8 timmar*.

- **Antal dagar tills lösenordet går ut**: Ange antal dagar innan lösenordet för enheten måste ändras (mellan 1 och 365). Exempel: Om du vill att lösenordet ska ändras om 60 dagar anger du `60`. När lösenordet upphör att gälla uppmanas användarna att skapa ett nytt lösenord.

   *Inget värde har konfigurerats som standard*.

- **Antal lösenord som krävs innan användaren kan återanvända ett lösenord**: Ange antalet senast använda lösenord som inte får återanvändas, mellan 1 och 24. Använd den här inställningen för att förhindra att användaren återanvänder tidigare använda lösenord.  

    *Som standard konfigureras ingen version*.

#### <a name="encryption"></a>Kryptering

- **Kryptering av datalagring på enheten**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** kryptering av data lagring på dina enheter.  

  Du behöver inte konfigurera den här inställningen eftersom Android Enterprise-enheter tvingar fram kryptering.

## <a name="work-profile"></a>Arbetsprofil

### <a name="device-health"></a>Enhetens hälsotillstånd

- **Rotade enheter**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Blockera** – Markera rotade (jailbreakade) enheter som inkompatibla.  

- **Kräv att enheten ska vara på eller under enhets hotnivå**: Välj den högsta tillåtna hot nivån på enhet som har utvärderats av [tjänsten för skydd mot mobila hot](mobile-threat-defense.md). Enheter som överskrider den här hotnivå markeras som inkompatibla. Om du vill använda den här inställningen väljer du den tillåtna hotnivån:

  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Skyddad** – Det här alternativet är säkrast och innebär att enheten inte kan ha några hot. Om hot på någon nivå identifieras på enheten betraktas den som inkompatibel.
  - **Låg** – Enheten utvärderas som kompatibel om det bara finns lågnivåhot på den. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel** – Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög** – Det här alternativet är det minst säkra då det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.

#### <a name="google-play-protect"></a>Google Play-skydd

- **Google Play-tjänster har konfigurerats**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** – Kräv att Google Play-tjänstappen installeras och aktiveras. Google Play-tjänster tillåter säkerhetsuppdateringar, vilket är ett beroende på grundnivå för många säkerhetsfunktioner på certifierade Google-enheter. 
  
- **Uppdaterad säkerhetsprovider**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** – Kräv att en uppdaterad säkerhetsprovider kan skydda enheten mot kända säkerhetsproblem. 
  
- **SafetyNet-enhetsattestering**: Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

> [!NOTE]
> På Android Enterprise-enheter är **Hotgenomsökning för appar** en enhetskonfigurationsprincip. Administratörer kan aktivera inställningen på en enhet med hjälp av en konfigurationsprincip. Mer information finns i avsnittet om [begränsningsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Egenskaper för enhet

#### <a name="operating-system-version"></a>Operativsystemversion

- **Lägsta version av operativsystemet**: När en enhet inte uppfyller minimikravet på operativsystemversion, rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan uppgradera enheten och sedan få åtkomst till organisationens resurser.

  *Som standard konfigureras ingen version*.

- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den i regeln blockeras åtkomsten till organisationsresurser. Användaren uppmanas att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän regeln ändras så att operativsystemversionen tillåts.

  *Som standard konfigureras ingen version*.

### <a name="system-security"></a>Systemsäkerhet

- **Kräv ett lösenord för att låsa upp mobila enheter**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen. 
  - **Kräv** – Användarna måste ange ett lösenord innan de får åtkomst till sina enheter.  

  Den här inställningen gäller på enhets nivå. Om du bara behöver kräva ett lösenord på arbetsprofilnivå, använder du en konfigurationsprincip. Mer information finns i avsnittet om [konfigurationsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).

- **Lösenordstyp som krävs**: Välj om ett lösenord endast ska innehålla numeriska tecken, eller en blandning av siffror och andra tecken. Alternativen är:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Minst numeriskt** (*standard*): Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
  - **Numeriskt avancerat**: Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
  - **Minst alfabetiskt**: Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
  - **Minst alfanumeriskt**: Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
  - **Minst alfanumeriskt med symboler**: Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).

  Beroende på vilken *lösen ords typ* du väljer är följande inställningar tillgängliga:  
  - **Maximalt antal minuters inaktivitet innan lösenord krävs**: Ange efter hur lång tids inaktivitet som användaren måste ange sitt lösenord igen. Alternativen inkluderar standardvärdet *inte konfigurerad*och från *1 minut* till *8 timmar*.

  - **Antal dagar tills lösenordet går ut**: Ange antal dagar innan lösenordet för enheten måste ändras (mellan 1 och 365). Exempel: Om du vill att lösenordet ska ändras om 60 dagar anger du `60`. När lösenordet upphör att gälla uppmanas användarna att skapa ett nytt lösenord.

  - **Minsta lösenordslängd**: Ange den minsta längd som lösenordet måste ha (mellan 4 och 16 tecken). 
  
  - **Antal tidigare lösenord för att förhindra återanvändning**: Ange antalet senast använda lösenord som inte får återanvändas. Använd den här inställningen för att förhindra att användaren återanvänder tidigare använda lösenord.

#### <a name="encryption"></a>Kryptering

- **Kryptering av datalagring på enheten**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** kryptering av data lagring på dina enheter.  

  Du behöver inte konfigurera den här inställningen eftersom Android Enterprise-enheter tvingar fram kryptering.

#### <a name="device-security"></a>Enhetssäkerhet

- **Blockera appar från okända källor**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Blockera** – blockera enheter med **säkerhet** > **okända källor** aktiverade källor (*stöds på Android 4,0 via Android 7. x. Stöds inte av Android 8.0 och senare*).  

  Om du vill att läsa in appar separat, måste okända källor tillåtas. Om du inte läser in Android-appar separat konfigurerar du den här funktionen med **Blockera** om du vill aktivera den här efterlevnadsprincipen.

  > [!IMPORTANT]
  > Inställningen **Blockera appar från okända källor** måste vara aktiverad för program med separat inläsning. Du bör endast tillämpa den här efterlevnadsprincipen om du inte läser in Android-appar separat på enheter.

  Du behöver inte konfigurera den här inställningen eftersom Android Enterprise-enheter alltid begränsar installationer från okända källor.

- **Körningsintegritet för företagsportalappen**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** – Välj *Kräv* om du vill bekräfta att företagsportalsappen uppfyller följande krav:
    - Har standardkörningsmiljön installerad
    - Är korrekt signerad
    - Är inte i felsökningsläge
    - Har installerats från en känd källa

- **Blockera USB-felsökning på enheten**: 
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Blockera** – Förhindra att enheter använder USB-felsökningsfunktionen.  

  Du behöver inte konfigurera den här inställningen eftersom USB-felsökning redan är inaktiverat på Android Enterprise-enheter.

- **Lägsta säkerhetskorrigeringsnivå**:  Välj den äldsta säkerhetskorrigeringsnivå som en enhet kan ha. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste anges i formatet YYYY-MM-DD.

  *Inget datum konfigureras som standard*.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](../fundamentals/scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för Android-enheter](compliance-policy-create-android.md).
