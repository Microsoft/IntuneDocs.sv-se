---
title: "Skapa en efterlevnadsprincip för Android"
titleSuffix: Azure portal
description: "Lär dig hur du skapar en efterlevnadsprincip för Android-enheter.\""
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6da4e6ffb473cee73f3946e5af3d97ddd5bb6b7b
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-devices-in-intune"></a>Så här skapar du en efterlevnadsprincip för Android-enheter i Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Principer för enhetsefterlevnad skapas för varje plattform i Intune Azure Portal. 

- Mer information om efterlevnadsprinciper finns i [Vad är enhetsefterlevnad?](device-compliance.md).
- Mer information om vilka förhandskrav du måste uppfylla innan du skapar en efterlevnadsprincip finns i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

## <a name="to-create-a-device-compliance-policy"></a>Skapa en princip för enhetsefterlevnad

1. Välj **Ange enhetsefterlevnad** på bladet **Intune**. Välj **Alla enhetsefterlevnadsprinciper** under **Hantera** och välj sedan **Skapa**.
2. Skriv ett namn, ange en beskrivning och välj den plattform som du vill att den här principen ska tillämpas på.
3. Välj **Efterlevnadskrav** och ange inställningar för **Säkerhet**, **Enhetens hälsotillstånd** och **Enhetsegenskap**. När du är klar väljer du **OK**.

<!-- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.-->

## <a name="to-assign-user-groups"></a>Tilldela användargrupper

Om du vill tilldela en efterlevnadsprincip till användare, väljer du en princip som du har konfigurerat. Du hittar befintliga principer på bladet **Efterlevnad – principer**.

1. Välj principen och **Tilldelningar**. Du kan sedan välja **Azure Active Directory-säkerhetsgrupper** och tilldela grupperna till principen.
2. Öppna bladet som visar säkerhetsgrupper för Azure AD genom att välja **Välj grupper**. Här hittar du en lista över alla säkerhetsgrupper i Azure Active Directory.  Du kan välja de användargrupper som du vill att den här principen ska tillämpas på och välja **Välj**. När du väljer **Välj** distribueras principen till användarna.

Du har tillämpat principen på användarna.  Efterlevnaden hos de enheter som används av de användare som principen är inriktad på kommer att utvärderas.

<!---##  Compliance policy settings--->

## <a name="device-health-and-security-settings"></a>Inställningar för enhetens för hälsotillstånd och säkerhet

- **Enheten får inte vara jailbrokad eller rotad**: Om du aktiverar den här inställningen kommer jailbrokade enheter att utvärderas som inkompatibla.
- **Kräv att enheter förhindrar installation av appar från okända källor (Android 4.0 eller senare)**: Om du vill blockera enheter som har aktiverat **Säkerhet** > **Okända källor** på enheten aktiverar du inställningen och väljer **Ja**.

### <a name="important"></a>Viktigt

Inställningen **Okända källor** måste vara aktiverad för program med separat inläsning. Du bör endast tillämpa denna efterlevnadsprincip om du inte läser in Android-appar separat på enheter.

- **Kräv att USB-felsökning är inaktiverat (Android 4.2 eller senare)**: Den här inställningen anger om du vill kontrollera om USB-felsökning är aktiverad på enheten.
- **Kräv att ”Genomsök enhet efter säkerhetshot” (Android 4.2-4.4) är aktiverat på enheter**: Den här inställningen anger att funktionen **Verifiera appar** är aktiverad på enheten.
- **Lägsta Android-säkerhetskorrigeringsnivå (Android 6.0 eller senare)**: Använd den här inställningen för att ange den lägsta Android-korrigeringsnivå. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste ha formatet ÅÅÅÅ-MM-DD.
- **Kräv att enhetsskydd är aktiverat**: Använd den här inställningen för att ta riskbedömningen från Lookout MTP-lösningen som ett villkor för efterlevnad. Välj den högsta tillåtna hotnivån, som är en av följande:
  - **Ingen (skyddad)**: Det här är den säkraste hotnivån. Detta innebär att enheten inte kan ha några hot. Om hot identifieras på enheten kommer den utvärderas som icke-kompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  - **Hög**: Det här är den minst säkra hotnivån. Detta tillåter i princip alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** Välj **Ja** för att ställa in så att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Minsta längd på lösenord**: Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.
- **Lösenordskvalitet**: Den här inställningen identifierar om lösenordskraven som du anger är konfigurerade på enheten. Aktivera den här inställningen för att kräva att användare uppfyller vissa lösenordskrav för Android-enheter. Välj mellan:
  - **Låg säkerhetsbiometri**
  - **Obligatoriskt**
  - **Minst numeriskt**
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Alfanumeriskt med symboler**
- **Minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Spara lösenordshistorik**: Använd den här inställningen i tillsammans med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Om du har valt **Spara lösenordshistorik** anger du hur många tidigare använda lösenord som inte får återanvändas.
- **Kräv lösenord när enheten lämnar inaktivt läge**: Använd den här inställningen tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Användaren uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.

### <a name="encryption"></a>Kryptering

- **Kräv kryptering på den mobila enheten**: Välj **Ja** för att kräva att enheter ska krypteras för att ansluta till resurser. Enheter krypteras när du väljer inställningen **Kräv lösenord för att låsa upp mobila enheter**.

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion som krävs**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Användaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta tillåtna version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

## <a name="how-noncompliant-settings-work-with-conditional-access-policies"></a>Hur fungerar inkompatibla inställningar med principer för villkorlig åtkomst?

I tabellen nedan visas hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

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

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. (Till exempel om användaren tvingas att ange en PIN-kod.)+

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheterna inte uppfyller efterlevnadskraven utförs följande åtgärder:+

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
