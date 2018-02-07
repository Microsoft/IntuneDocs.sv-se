---
title: "Skapa en efterlevnadsprincip för Android for Work"
titleSuffix: Azure portal
description: "Lär dig hur du skapar en efterlevnadsprincip för Android for Work-enheter.\""
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e9ec660fcbd1f02fb0767e322edfdfa7f85964a7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Så här skapar du en efterlevnadsprincip för Android for Work-enheter i Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Efterlevnadsprinciper skapas för varje plattform.  Du kan skapa en efterlevnadsprincip i Azure-portalen. Mer information om vad en efterlevnadsprincip är finns i artikeln [Vad är enhetsefterlevnad?](device-compliance.md). Mer information om vilka förhandskrav du måste uppfylla innan du skapar en efterlevnadsprincip finns i artikeln [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

I tabellen nedan visas hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

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

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheterna inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Skapa en efterlevnadsprincip i Azure-portalen

1. Välj **Ange enhetsefterlevnad** på bladet **Intune**. Välj **Alla enhetsefterlevnadsprinciper** under **Hantera** och välj sedan **Skapa**.
2. Skriv ett namn, ge en beskrivning och välj den plattform som du vill att den här principen ska tillämpas på.
3. Välj **Efterlevnadskrav** och ange inställningar för **Säkerhet**, **Enhetens hälsotillstånd** och **Enhetsegenskap**. Välj **OK** när du är klar.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Tilldela användargrupper

Om du vill tilldela en efterlevnadsprincip till användare, väljer du en princip som du har konfigurerat. Du hittar befintliga principer på bladet **Efterlevnad – princip**.

1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas det blad där du kan välja **Azure Active Directory-säkerhetsgrupper** och tilldela dem till principen.
2. Öppna bladet som visar säkerhetsgrupper för Azure AD genom att välja **Välj grupper**.  När du väljer **Välj** distribueras principen till användarna.

Du har tillämpat principen på användarna.  Efterlevnaden hos de enheter som används av de användare som principen är inriktad på kommer att utvärderas.

<!--- ##  Compliance policy settings--->

## <a name="system-security-settings"></a>Systemsäkerhetsinställningar

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** Ställ in på **Ja** för att ställa in så att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Minsta längd på lösenord**: Ange det minsta antal siffror eller tecken som lösenordet måste innehålla.
- **Lösenordskvalitet:** Den här inställningen identifierar om lösenordskraven som du anger är konfigurerade på enheten. Aktivera den här inställningen för att kräva att användare konfigurera vissa lösenordskrav för Android-enheter. Välj mellan:
  - **Låg säkerhetsbiometri**
  - **Obligatoriskt**
  - **Minst numeriskt**
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Alfanumeriskt med symboler**
- **Minuter av inaktivitet innan lösenord måste anges:** Anger efter hur lång tids inaktivitet som användaren måste ange lösenordet igen.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills användarens lösenord upphör att gälla och ett nytt lösenord måste anges.
- **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Om **Spara lösenordshistorik** har valts anger du hur många tidigare använda lösenord som inte får återanvändas.
- **Kräv lösenord när enheten lämnar inaktivt läge:** Den här inställningen bör användas tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Användarna uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.


### <a name="encryption"></a>Kryptering

- **Kräv kryptering på den mobila enheten:** Du behöver inte konfigurera den här inställningen eftersom Android for Work-enheter tvingar fram kryptering.


## <a name="device-health-and-security-settings"></a>Inställningar för enhetens för hälsotillstånd och säkerhet

- **Enheten får inte vara jailbrokad eller rotad:** Om du aktiverar den här inställningen kommer jailbrokade enheter att utvärderas som inkompatibla.
- **Kräv att enheter förhindrar installation av appar från okända källor:** Du behöver inte konfigurera den här inställningen eftersom Android for Work-enheter alltid begränsar installationer från okända källor. .
- **Kräv att USB-felsökning är inaktiverat**: Du behöver inte konfigurera de här inställningarna eftersom USB-felsökning redan är inaktiverat på Android for Work-enheter.
- **Lägsta Android-säkerhetskorrigeringsnivå**: Använd den här inställningen för att ange den lägsta Android-korrigeringsnivån. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste ha formatet ÅÅÅÅ-MM-DD.
- **Kräv att enhetsskydd är aktiverat**: Använd den här inställningen för att använda riskbedömningen från Lookout MTP-lösningen som ett villkor för efterlevnad. Välj den högsta tillåtna hotnivån, som är en av följande:
  - **Ingen (skyddad)**: Det här är det säkraste alternativet. Detta innebär att enheten inte kan ha några hot. Om hot identifieras på enheten kommer den utvärderas som icke-kompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  - **Hög**: Det här alternativet är minst säkert. I grunden innebär detta att alla hotnivåer är tillåtna och kanske är detta endast användbart om du använder den här lösningen för rapportering.

Se [Aktivera regeln för skydd mot enhetshot i policyn för efterlevnad](https://docs.microsoft.com/intune-classic/deploy-use/enable-device-threat-protection-rule-in-compliance-policy) för mer information.

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion som krävs:** När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta tillåtna version av operativsystemet:** När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
