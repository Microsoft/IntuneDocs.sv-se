---
title: "Skapa en efterlevnadsprincip för iOS"
titleSuffix: Intune on Azure
description: "Lär dig hur du skapar en efterlevnadsprincip för iOS-enheter.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9337586ad5daa909f38aba2b25fc159b44f55e65
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune"></a>Lär dig hur du skapar en enhetsefterlevnadsprincip för iOS-enheter i Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Efterlevnadsprinciper skapas för varje plattform.  Du kan skapa en efterlevnadsprincip i Azure-portalen. Mer information om vad en efterlevnadsprincip är finns i artikeln [Vad är enhetsefterlevnad](device-compliance.md). Mer information om vilka förhandskrav du måste uppfylla innan du skapar en efterlevnadsprincip finns i artikeln [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

I tabellen nedan visas hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

-------------------------------


| **Principinställning** | **iOS 8.0 och senare** |
| --- | --- |
| **Konfiguration av PIN-kod eller lösenord** | Åtgärdad |   
| **Enhetskryptering** | Åtgärdad (genom angiven PIN-kod) |
| **Jailbreakad eller rotad enhet** | I karantän (inte en inställning)
| **E-postprofil** | I karantän |
|**Lägsta version av operativsystemet** | I karantän |
| **Högsta version av operativsystemet** | I karantän |  
| **Attestering av hälsotillstånd i Windows** | Inte tillämpligt |  
----------------------------


**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. (Till exempel om användaren tvingas att ange en PIN-kod.)

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheterna inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Skapa en efterlevnadsprincip i Azure-portalen

1. Välj **Ange enhetsefterlevnad** på bladet **Intune**. Välj **Alla enhetsefterlevnadsprinciper** under **Hantera** och välj sedan **Skapa**.
2. Skriv ett namn, ge en beskrivning och välj den plattform som du vill att den här principen ska tillämpas på.
3. Välj **Efterlevnadskrav** och ange inställningar för **Säkerhet**, **Enhetens hälsotillstånd** och **Enhetsegenskap**. Välj **OK** när du är klar.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Tilldela användargrupper

Om du vill tilldela en efterlevnadsprincip till användare, väljer du en princip som du har konfigurerat. Du hittar befintliga principer på bladet **Efterlevnad – principer**.

1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas det blad där du kan välja **Azure Active Directory-säkerhetsgrupper** och tilldela dem till principen.
2. Öppna bladet som visar säkerhetsgrupper för Azure AD genom att välja **Välj grupper**.  När du väljer **Välj** distribueras principen till användarna.

Du har tillämpat principen på användarna.  Efterlevnaden hos de enheter som används av de användare som principen är inriktad på kommer att utvärderas.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Systemsäkerhetsinställningar

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** Välj **Ja** om du vill kräva att användarna anger ett lösenord för att få åtkomst till sina enheter. iOS-enheter som använder lösenord krypteras.
- **Tillåt enkla lösenord**: Välj **Ja** om du vill att användaren ska kunna skapa enkla lösenord som **1234** eller **1111**.
- **Minsta längd på lösenord**: Ange det minsta antal siffror eller tecken som lösenordet måste innehålla.
- **Krav på lösenordstyp**: Ange om användaren måste skapa ett **alfanumeriskt** lösenord eller ett **numeriskt** lösenord.
- **Minsta antal teckenuppsättningar:** Om du konfigurerar alternativet för **Krav på lösenordstyp** som **Alfanumeriskt** använder du den här inställningen för att specificera det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
  - Gemener
  - Versaler
  - Symboler
  - Siffror

Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

För iOS-enheter refererar den här inställningen för antalet specialtecken (t.ex, **!** , **#**, **&amp;**) som måste inkluderas i lösenordet.

- **Minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Om du har valt **Spara lösenordshistorik** anger du hur många tidigare använda lösenord som inte får återanvändas.
- **Kräv lösenord när enheten lämnar inaktivt läge**: Använd den här inställningen tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Användaren uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.

### <a name="email-profile"></a>E-postprofil

- **E-postkontot måste hanteras av Intune:** Om det här alternativet är inställt på **Ja** måste enheten använda e-postprofilen som har distribuerats till enheten. Enheten betraktas som icke-kompatibel i följande situationer:
  - E-postprofilen har distribuerats till en annan användargrupp än användargruppen som är kompatibilitetsprincipens mål.
  - Användaren har redan konfigurerat ett e-postkonto på enheten som matchar Intune-e-postprofilen som distribuerats till enheten. Intune kan inte skriva över den användartillhandahållna profilen, och kan därför inte hantera den. För att säkerställa efterlevnad måste användaren ta bort de befintliga e-postinställningarna. Sedan kan Intune installera den hantera e-postprofilen.
- **Välj den e-postprofil som måste hanteras av Intune**: Om inställningen **E-postkontot måste hanteras av Intune** har valts väljer du **Välj** för att ange Intune-e-postprofilen. E-postprofilen måste finnas på enheten.

Information om e-postprofiler finns i [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health-settings"></a>Inställningar för enhetens hälsotillstånd

- **Enheten får inte vara upplåst (jailbroken/rooted)**: Om du aktiverar den här inställningen kommer upplåsta enheter att vara inkompatibla.

## <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion som krävs**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Användarna kan välja att uppgradera sina enheter. Därefter har de åtkomst till företagsresurser.
- **Högsta tillåtna operativsystemversion**: När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
