---
title: Skapa en efterlevnadsprincip för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa eller konfigurera en enhetsefterlevnadsprincip i Microsoft Intune för Android-enheter. Välj att tillåta jailbrokade enheter, ställ in godkänd hotnivå, kontrollera efter Google Play, ange lägsta och högsta operativsystemversion, välj dina lösenordskrav och tillåt program med separat inläsning.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 559fd83d83c7312e0efe0d2c3f6bb7e5ec596a1b
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Lägg till en efterlevnadsprincip för Android-enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En Intune-enhetsefterlevnadsprincip för Android anger de regler och inställningar som Android-enheter måste uppfylla för att anses vara kompatibla. Du kan använda dessa principer med villkorlig åtkomst för att tillåta eller blockera åtkomst till företagets resurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet. Du skapar efterlevnadsprinciper för enheter för varje plattform i Intune Azure-portalen. Läs mer om efterlevnadsprinciper och eventuella förutsättningar i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

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

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. (Till exempel om användaren tvingas att ange en PIN-kod.)

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. För **Plattform**, välj **Android**. Välj **Inställningar** för att konfigurera och ange inställningar för **Enhetens hälsotillstånd**, **Enhetsegenskaper** och **Systemsäkerhet**. När du är klar väljer **OK** och **Skapa**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.--->

<!---##  Compliance policy settings--->

## <a name="device-health"></a>Device health

- **Rotade enheter**: Om du aktiverar den här inställningen utvärderas jailbrokade enheter som inkompatibla.
- **Kräv att enheten ska vara på eller under hotnivån för enheten**: Använd den här inställningen för att använda riskbedömningen från Lookout MTP-lösningen som ett villkor för efterlevnad. Välj högsta tillåtna hotnivå:
  - **Säkrad**: Det här alternativet är det säkraste eftersom enheten inte kan ha några hot. Om hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om existerande hot på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  - **Hög**: Det här alternativet är det minst säkra och det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
- **Google Play-tjänster har konfigurerats**: Kräver att appen Google Play-tjänster är installerad och aktiverad. Google Play-tjänster tillåter säkerhetsuppdateringar, vilket är ett beroende på grundnivå för många säkerhetsfunktioner på certifierade Google-enheter.
- **Uppdaterad säkerhetsprovider**: Kräv att en uppdaterad säkerhetsprovider kan skydda en enhet från kända säkerhetsproblem.
- **Hotgenomsökning för appar**: Kräv att Android-funktionen **Verifiera appar** har aktiverats.

  > [!NOTE]
  > Den här funktionen är en kompatibilitetsinställning på den äldre Android-plattformen. Intune kan bara kontrollera om den här inställningen är aktiverad på enhetsnivå. På enheter med arbetsprofiler (Android for Work), finns den här inställningen som en konfigurationsinställning för principen. På så sätt kan administratörer aktivera inställningen för en enhet.

  Om företaget använder Androids arbetsprofiler kan du aktivera **Hotgenomsökning för appar** för registrerade enheter. Upprätta en enhetsprofil och kräv systemsäkerhetsinställningen. Mer information finns i [Enhetsbegränsningar i Intune med Android for Work](device-restrictions-android-for-work.md).

- **Attesteringen av enhetens SafetyNet**: Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:
  - **Inte konfigurerat**
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som anges i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Enheten kan inte komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som användarens lösenordet måste innehålla.
- **Krav på lösenordstyp**: Välj om ett lösenord endast ska ha numeriska tecken, eller om det ska vara en blandning av siffror och andra tecken. Välj mellan:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Minst numeriskt**
  - **Numeriskt avancerat**: Upprepade eller efterföljande siffror (till exempel ”1 111” eller ”1234”) är inte tillåtna.
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**
- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar)**: Ange antalet dagar tills lösenord upphör att gälla och användaren måste skapa ett nytt lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Ange antalet senast använda lösenord som inte får återanvändas. Använd den här inställningen för att förhindra att användaren återanvänder tidigare använda lösenord.

### <a name="encryption"></a>Kryptering

- **Kryptering för lagring av data på en enhet** (Android 4.0 och senare, eller KNOX 4.0 och senare): Välj **Kräv** för att kryptera lagring av data på dina enheter. Enheter krypteras när du väljer inställningen **Kräv lösenord för att låsa upp mobila enheter**.

### <a name="device-security"></a>Enhetssäkerhet

- **Blockera appar från okända källor**: Välj att blockera enheter med ”Säkerhet > Okända källor” aktiverade källor (Android 4.0–Android 7.x. Stöds inte av Android 8.0 och senare). Om du vill att läsa in appar separat, måste okända källor tillåtas. Om du inte läser in Android-appar separat, aktivera då den här efterlevnadsprincipen.

  > [!IMPORTANT]
  > Inställningen **Blockera appar från okända källor** måste vara aktiverad för program med separat inläsning. Du bör endast tillämpa denna efterlevnadsprincip om du inte läser in Android-appar separat på enheter.

- **Körningsintegritet för företagsportalappen**: Kontrollerar om företagsportalappen har körningsmiljön standard installerad, är korrekt signerad, inte är i felsökningsläge och har installerats från en känd källa.
- **Blockera USB-felsökning på enheten** (Android 4.2 eller senare): Välj att förhindra att enheter använder funktionen USB-felsökning.
- **Lägsta säkerhetskorrigeringsnivå** (Android 6.0 eller senare): Välj den äldsta säkerhetskorrigeringsnivå som en enhet kan ha. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste anges i formatet `YYYY-MM-DD`.

## <a name="assign-user-groups"></a>Tilldela användargrupper

1. Välj en princip som du har konfigurerat. Befintliga principer finns i **Enhetsefterlevnad** > **Principer**.
2. Välj principen och välj **Tilldelningar**. Du kan inkludera eller exkludera säkerhetsgrupper i Azure Active Directory (AD).
3. Välj **Valda grupper** för att se dina Azure AD-säkerhetsgrupper. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj **Spara** för att distribuera principen till användare.

Du har tillämpat principen på användarna. Enheterna som används av de användare som principen är inriktad på kommer att utvärderas för att se om de följer standard.

## <a name="next-steps"></a>Nästa steg
[Automatisera e-post och lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md)  
[Övervaka efterlevnadsprinciper för Intune-enheter](compliance-policy-monitor.md)
