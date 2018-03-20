---
title: "Skapa en efterlevnadsprincip för Android for Work"
titleSuffix: Microsoft Intune
description: "Skapa en efterlevnadsprincip i Intune för Android for Work-enheter, för att kunna ange krav som en enhet måste uppfylla för att vara kompatibel."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8ca31d4c83ccc6b786933080b96f66953cf1a108
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Så här skapar du en efterlevnadsprincip för Android for Work-enheter i Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En efterlevnadsprincip i Intune för Android for Work-enheter anger de regler och inställningar som Android for Work-enheter måste uppfylla för att anses vara kompatibla. Du kan använda dessa principer med villkorlig åtkomst för att tillåta eller blockera åtkomst till företagets resurser. Du kan även få enhetsrapporter och vidta åtgärder för inkompatibilitet. Du skapar efterlevnadsprinciper för enheter för varje plattform i Intune Azure-portalen. Mer information om efterlevnadsprinciper och de förhandskrav du måste uppfylla innan du skapar en efterlevnadsprincip finns i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

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

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Skapa en efterlevnadsprincip i Azure-portalen

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
1. I fönstret **Intune** väljer du **Enhetsefterlevnad**. Under **Hantera** väljer du **Principer** och **Skapa princip**.
2. Skriv ett namn, ge en beskrivning och välj den plattform som du vill att den här principen ska tillämpas på.
3. Välj **Konfigurera inställningar** för att ange **Systemsäkerhet**, **Enhetens hälsotillstånd** och **Enhetsegenskaper** här. När du är klar väljer du **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Tilldela användargrupper

Om du vill tilldela en efterlevnadsprincip till användare, väljer du en princip som du har konfigurerat. Du hittar befintliga principer i fönstret **Enhetsefterlevnad – Principer**.

1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas det fönster där du kan välja **Azure Active Directory-säkerhetsgrupper** och tilldela dem till principen.
2. Öppna fönstret som visar Azure AD-säkerhetsgrupperna genom att välja **Valda grupper**.  När du väljer **Spara** distribueras principen till användarna.

Du har tillämpat principen på användarna.  Efterlevnaden hos de enheter som används av de användare som principen är inriktad på kommer att utvärderas.

<!--- ##  Compliance policy settings--->

## <a name="system-security-settings"></a>Systemsäkerhetsinställningar

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter**: Ställ in på **Ja** för att ställa in så att användare måste ange ett lösenord för att få åtkomst till sina enheter.
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
- **Kräv lösenord när enheten lämnar inaktivt läge:** Den här inställningen bör användas tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Slutanvändarna uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.


### <a name="encryption"></a>Kryptering

- **Kräv kryptering på den mobila enheten:** Du behöver inte konfigurera den här inställningen eftersom Android for Work-enheter tvingar fram kryptering.


## <a name="device-health-and-security-settings"></a>Inställningar för enhetens för hälsotillstånd och säkerhet

- **Enheten får inte vara jailbrokad eller rotad**: Om du aktiverar den här inställningen utvärderas jailbrokade enheter som inkompatibla.
- **Kräv att enheter förhindrar installation av appar från okända källor:** Du behöver inte konfigurera den här inställningen eftersom Android for Work-enheter alltid begränsar installationer från okända källor.
- **Kräv att USB-felsökning är inaktiverat**: Du behöver inte konfigurera de här inställningarna eftersom USB-felsökning redan är inaktiverat på Android for Work-enheter.
- **Lägsta Android-säkerhetskorrigeringsnivå**: Använd den här inställningen för att ange den lägsta Android-korrigeringsnivån. Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste ha formatet ÅÅÅÅ-MM-DD.
- **Kräv att enhetsskydd är aktiverat**: Använd den här inställningen för att ta riskbedömningen från Lookout MTP-lösningen som ett villkor för efterlevnad. Välj den högsta tillåtna hotnivån, som är en av följande:
  - **Ingen (skyddad)**: Det här är det säkraste alternativet. Detta innebär att enheten inte kan ha några hot. Om hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  - **Hög**: Det här alternativet är minst säkert. I grunden innebär detta att alla hotnivåer är tillåtna och kanske är detta endast användbart om du använder den här lösningen för rapportering.

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion som krävs**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta tillåtna version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
