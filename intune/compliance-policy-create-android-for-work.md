---
title: Skapa en efterlevnadsprincip för Android for Work i Microsoft Intune – Azure | Microsoft Docs
description: Skapa eller konfigurera en enhetsefterlevnadsprincip i Microsoft Intune för Android for Work-enheter. Välj att tillåta jailbrokade enheter, ställ in godkänd hotnivå, kontrollera efter Google Play, ange lägsta och högsta operativsystemversion, välj dina lösenordskrav och tillåt program med separat inläsning.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1d438aa7416b1629af7ab2b899afa06720e2b49
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="add-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Lägg till en efterlevnadsprincip för Android for Work-enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En efterlevnadsprincip i Intune för Android for Work-enheter anger de regler och inställningar som dessa enheter måste uppfylla för att anses vara kompatibla. Du kan använda dessa principer med villkorlig åtkomst för att tillåta eller blockera åtkomst till företagets resurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet. Du skapar efterlevnadsprinciper för enheter för olika plattformar i Intune Azure-portalen. Läs mer om efterlevnadsprinciper och eventuella förutsättningar i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

Följande tabell beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

--------------------------

|**principinställning**| **Android for Work** |
| --- | --- |
| **Konfiguration av PIN-kod eller lösenord** |  I karantän |
| **Enhetskryptering** |  I karantän |
| **Jailbreakad eller rotad enhet** | I karantän (inte en inställning) |
| **e-postprofil** | Inte tillämpligt |
| **Lägsta version av operativsystemet** | I karantän |
| **Högsta version av operativsystemet** | I karantän |
| **Attestering av hälsotillstånd i Windows** |Inte tillämpligt |

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. (Till exempel om användaren tvingas att ange en PIN-kod.)+

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Som **Plattform**, välj **Android for Work**. Välj **Inställningar** för att konfigurera och ange inställningar för **Enhetens hälsotillstånd**, **Enhetsegenskaper** och **Systemsäkerhet**. När du är klar väljer **OK** och **Skapa**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="device-health"></a>Device health

- **Rotade enheter**: Om du aktiverar den här inställningen utvärderas jailbrokade enheter som inkompatibla.
- **Kräv att enheten ska vara på eller under hotnivån för enheten**: Använd den här inställningen för att använda riskbedömningen från Lookout MTP-lösningen som ett villkor för efterlevnad. Välj högsta tillåtna hotnivå:
  - **Skyddad**: Det här alternativet är säkrast och innebär att enheten inte kan ha några hot. Om hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  - **Hög**: Det här alternativet är det minst säkra då det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.
- **Google Play-tjänster har konfigurerats**: Kräver att appen Google Play-tjänster är installerad och aktiverad. Google Play-tjänster tillåter säkerhetsuppdateringar, vilket är ett beroende på grundnivå för många säkerhetsfunktioner på certifierade Google-enheter.
- **Uppdaterad säkerhetsprovider**: Kräv att en uppdaterad säkerhetsprovider kan skydda en enhet från kända säkerhetsproblem.
- **Attesteringen av enhetens SafetyNet**: Ange den nivå av [SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation.html) som måste uppfyllas. Alternativen är:
  - **Inte konfigurerat**
  - **Kontrollera grundläggande integritet**
  - **Kontrollera grundläggande integritet och certifierade enheter**

#### <a name="threat-scan-on-apps"></a>Hotgenomsökning för appar

På enheter med arbetsprofiler (Android for Work), hittar du inställningen **Hotgenomsökning för appar** som en konfigurationsinställning för principen. Administratörer kan aktivera inställningen för en enhet.

Om företaget använder Androids arbetsprofiler kan du aktivera **Hotgenomsökning för appar** för registrerade enheter. Upprätta en enhetsprofil och kräv systemsäkerhetsinställningen. Mer information finns i [Enhetsbegränsningar i Intune med Android for Work](device-restrictions-android-for-work.md).

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Enheten kan inte komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som användarens lösenordet måste innehålla.
- **Krav på lösenordstyp**: Välj om ett lösenord ska innehålla endast numeriska tecken eller en blandning av siffror och andra tecken. Välj mellan:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Minst numeriskt**
  - **Numeriskt avancerat**
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**
- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Ange antalet senast använda lösenord som inte får återanvändas. Använd den här inställningen för att förhindra att användaren återanvänder tidigare använda lösenord.

### <a name="encryption"></a>Kryptering

- **Kräv kryptering på den mobila enheten:** Du behöver inte konfigurera den här inställningen eftersom Android for Work-enheter tvingar fram kryptering.

### <a name="device-security"></a>Enhetssäkerhet

- **Blockera appar från okända källor:** Du behöver inte konfigurera den här inställningen eftersom Android for Work-enheter alltid begränsar installationer från okända källor.
- **Körningsintegritet för företagsportalappen**: Kontrollerar om företagsportalappen har körningsmiljön standard installerad, är korrekt signerad, inte är i felsökningsläge och har installerats från en känd källa.
- **Blockera USB-felsökning på enheten**: Du behöver inte konfigurera de här inställningarna eftersom USB-felsökning redan är inaktiverat på Android for Work-enheter.
- **Lägsta säkerhetskorrigeringsnivå**: Välj den äldsta säkerhetskorrigeringsnivå som en enhet kan ha. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste anges i formatet `YYYY-MM-DD`.

## <a name="assign-user-groups"></a>Tilldela användargrupper

1. Välj en princip som du har konfigurerat. Befintliga principer finns i **Enhetsefterlevnad** > **Principer**.
2. Välj principen och välj **Tilldelningar**. Du kan inkludera eller exkludera säkerhetsgrupper i Azure Active Directory (AD).
3. Välj **Valda grupper** för att se dina Azure AD-säkerhetsgrupper. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj **Spara** för att distribuera principen till användare.

Du har tillämpat principen på användarna. Enheterna som används av de användare som principen är inriktad på kommer att utvärderas för att se om de följer standard.

## <a name="next-steps"></a>Nästa steg
[Automatisera e-post och lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md)  
[Övervaka efterlevnadsprinciper för Intune-enheter](compliance-policy-monitor.md)
