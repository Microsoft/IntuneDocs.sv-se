---
title: Skapa en efterlevnadsprincip för Android Enterprise i Microsoft Intune – Azure | Microsoft Docs
description: Skapa eller konfigurera en enhetsefterlevnadsprincip i Microsoft Intune för Android Enterprise eller arbetsprofilenheter. Välj att tillåta jailbrokade enheter, ställ in godkänd hotnivå, kontrollera efter Google Play, ange lägsta och högsta operativsystemversion, välj dina lösenordskrav och tillåt program med separat inläsning.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: aab8208865fb072170a670d1da25e7f02448c38f
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642871"
---
# <a name="add-a-device-compliance-policy-for-android-enterprise-devices-in-intune"></a>Lägg till en enhetsefterlevnadsprincip för Android Enterprise-enheter i Intune

Enhetsefterlevnadsprinciper är en viktig funktion när du använder Intune för att skydda din organisations resurser. I Intune kan du skapa regler och inställningar som enheter måste uppfylla för att anses vara kompatibla, till exempel en lösenordslängd. Om enheten inte är kompatibel kan du blockera åtkomst till data och resurser med hjälp av [villkorlig åtkomst](conditional-access.md). 

Du kan också få enhetsrapporter och vidta åtgärder vid inkompatibilitet. Du kan till exempel skicka ett e-postmeddelande till användaren. Läs mer om efterlevnadsprinciper och eventuella förutsättningar i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

Den här artikeln innehåller de inställningar som du kan använda i en efterlevnadsprincip för enheter som kör Android Enterprise.

## <a name="non-compliance-and-conditional-access"></a>Inkompatibilitet och villkorlig åtkomst

Följande tabell beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

--------------------------

|**principinställning**| **Android Enterprise-profil** |
| --- | --- |
| **Konfiguration av PIN-kod eller lösenord** |  I karantän |
| **Enhetskryptering** |  I karantän |
| **Jailbreakad eller rotad enhet** | I karantän (inte en inställning) |
| **e-postprofil** | Inte tillämpligt |
| **Lägsta version av operativsystemet** | I karantän |
| **Högsta version av operativsystemet** | I karantän |
| **Attestering av hälsotillstånd i Windows** |Inte tillämpligt |

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. Till exempel om användaren tvingas att ange en PIN-kod.

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. Till exempel om Android-enheter inte tvingar användaren att kryptera enheten. När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

  - Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
  - Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. I **Plattform** väljer du **Android enterprise**. 
5. Välj **Konfigurera inställningar**. Ange inställningar för **Enhetens hälsotillstånd**, **Enhetsegenskaper** och **Systemsäkerhet** genom att följa anvisningarna i den här artikeln.

## <a name="device-health"></a>Device health

- **Rotade enheter**: Välj **Blockera** för att markera att rotade (jailbreakade) enheter är inkompatibla. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Kräv att enheten ligger på eller under enhetshotnivån**: Använd den här inställningen för att använda riskbedömningen från Lookout MTP-lösningen som ett villkor för efterlevnad. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen. Om du vill använda den här inställningen väljer du den tillåtna hotnivån:
  - **Skyddad**: Det här alternativet är säkrast och innebär att enheten inte kan ha några hot. Om hot på någon nivå identifieras på enheten betraktas den som inkompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på låg nivå. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen inkompatibel.
  - **Hög**: Det här alternativet är det minst säkra då det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
- **Google Play-tjänster har konfigurerats**: **Kräv** att Google Play-tjänstappen är installerad och aktiverad. Google Play-tjänster tillåter säkerhetsuppdateringar, vilket är ett beroende på grundnivå för många säkerhetsfunktioner på certifierade Google-enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Uppdaterad säkerhetsprovider**: **Kräv** att en uppdaterad säkerhetsprovider kan skydda enheten mot kända säkerhetsproblem. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **SafetyNet-enhetsattestering**: Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:
  - **Inte konfigurerat** (standard): Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

#### <a name="threat-scan-on-apps"></a>Hotgenomsökning för appar

På Android Enterprise-enheter är inställningen **Hotgenomsökning för appar** en konfigurationsprincip. Mer information finns i avsnittet om [begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

## <a name="device-properties-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta version av operativsystemet**: När en enhet inte uppfyller minimikravet på operativsystemversion, rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den i regeln, blockeras åtkomsten till företagets resurser. Användaren uppmanas sedan att kontakta IT-administratören. Den här enheten kan inte komma åt företagsresurser förrän en regel ändras så att operativsystemversionen tillåts.

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv ett lösenord för att låsa upp mobila enheter**: **Kräv** att användarna anger ett lösenord innan de får åtkomst till sin enhet. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen. Den här inställningen tillämpas på enhetsnivå. Om du bara behöver kräva ett lösenord på arbetsprofilnivå, använder du en konfigurationsprincip. Mer information finns i avsnittet om [konfigurationsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).
- **Minsta lösenordslängd**: Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.
- **Lösenordstyp som krävs**: Välj om ett lösenord endast ska innehålla numeriska tecken, eller en blandning av siffror och andra tecken. Alternativen är:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Minst numeriskt** (standard)
  - **Numeriskt avancerat**
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**

- **Maximalt antal minuters inaktivitet innan lösenord krävs**: Ange efter hur lång tids inaktivitet som användaren måste ange sitt lösenord igen. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.
- **Lösenordets giltighetstid (dagar)**: Ange antalet dagar tills lösenordet upphör att gälla och användaren måste skapa ett nytt.
- **Antal tidigare lösenord för att förhindra återanvändning**: Ange antalet senast använda lösenord som inte får återanvändas. Använd den här inställningen för att förhindra att användaren återanvänder tidigare använda lösenord.

### <a name="encryption"></a>Kryptering

- **Kryptering av datalagring på enheten**: Välj **Kräv** för att kryptera lagring av data på dina enheter. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen. 

  Du behöver inte konfigurera den här inställningen eftersom Android-arbetsprofilenheter tvingar fram kryptering.

### <a name="device-security"></a>Enhetssäkerhet

- **Blockera appar från okända källor**: Välj att **blockera** enheter med ”Säkerhet > Okända källor”-aktiverade källor (stöds på Android 4.0–7.x; stöds inte av Android 8.0 och senare). Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  Om du vill att läsa in appar separat, måste okända källor tillåtas. Om du inte läser in Android-appar separat konfigurerar du den här funktionen med **Blockera** om du vill aktivera den här efterlevnadsprincipen. 

  > [!IMPORTANT]
  > Inställningen **Blockera appar från okända källor** måste vara aktiverad för program med separat inläsning. Du bör endast tillämpa den här efterlevnadsprincipen om du inte läser in Android-appar separat på enheter.

  Du behöver inte konfigurera den här inställningen eftersom Android-arbetsprofilenheter alltid begränsar installationer från okända källor.

- **Körningsintegritet för företagsportalappen**: Välj **Kräv** för att bekräfta att företagsportalappen uppfyller följande krav:

  - Har standardkörningsmiljön installerad
  - Är korrekt signerad
  - Är inte i felsökningsläge
  - Har installerats från en känd källa

  Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

- **Blockera USB-felsökning på enheten**: Välj **Blockera** för att förhindra att enheter använder USB-felsökningsfunktionen. Om du väljer **Ej konfigurerad** (standard) görs ingen kompatibilitetskontroll för den här inställningen.

  Du behöver inte konfigurera den här inställningen eftersom USB-felsökning redan är inaktiverat på Android-arbetsprofilenheter.

- **Lägsta säkerhetskorrigeringsnivå**: Välj den äldsta säkerhetskorrigeringsnivå som en enhet kan ha. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste anges i formatet *ÅÅÅÅ-MM-DD*.

När du är klar väljer du **OK** > **OK** för att spara dina ändringar.

## <a name="actions-for-noncompliance"></a>Åtgärder för inkompatibilitet

Välj **Åtgärder för inkompatibilitet**. Standardåtgärden markerar enheten som inkompatibel omedelbart.

Du kan ändra schemat när enheten har markerats som inkompatibel, till exempel efter en dag. Du kan också konfigurera en andra åtgärd som skickar ett e-postmeddelande till användaren när enheten inte är kompatibel.

[Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) innehåller mer information, inklusive anvisningar för hur du skapar ett e-postmeddelande till användarna.

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
[Inställningar för efterlevnadsprinciper för Android](compliance-policy-create-android.md)
