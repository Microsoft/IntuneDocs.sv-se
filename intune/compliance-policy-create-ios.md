---
title: Skapa en efterlevnadsprincip för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa eller konfigurera en efterlevnadsprincip för Microsoft Intune-enheter för iOS-enheter för att ange ett e-postkonto, kontrollera jailbrokade enheter, kontrollera lägsta och högsta operativsystem och ange begränsningar för lösenord, inklusive lösenordslängd och enhetsinaktivitet.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f711a6bec9be0ac1fd94183931070f9988d49e3
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/18/2018
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Lägga till en enhetsefterlevnadsprincip för iOS-enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En Intune iOS-enhetsefterlevnadsprincip anger de regler och inställningar som iOS-enheter måste uppfylla för att vara kompatibla. När du använder principer för enhetsefterlevnad med villkorlig åtkomst kan du tillåta eller blockera åtkomst till företagsresurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet. Du kan skapa efterlevnadsprinciper för enheter för varje plattform i Intune Azure-portalen. Läs mer om efterlevnadsprinciper och eventuella förutsättningar i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

Följande tabell beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

---------------------------

| **Principinställning** | **iOS 8.0 och senare** |
| --- | --- |
| **Konfiguration av PIN-kod eller lösenord** | Åtgärdad |
| **Enhetskryptering** | Åtgärdad (genom angiven PIN-kod) |
| **Jailbreakad eller rotad enhet** | I karantän (inte en inställning)
| **E-postprofil** | I karantän |
|**Lägsta version av operativsystemet** | I karantän |
| **Högsta version av operativsystemet** | I karantän |
| **Attestering av hälsotillstånd i Windows** | Inte tillämpligt |

---------------------------

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. (Till exempel om användaren tvingas att ange en PIN-kod.)

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. För **Plattform**, välj **iOS**. Välj **Inställningar** för att konfigurera och ange inställningar för **E-post**, **Enhetens hälsotillstånd**, **Enhetsegenskaper** och **Systemsäkerhet**. När du är klar väljer du **OK**, och **Skapa**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>E-post

- **Kräv att mobila enheter har en hanterad e-postprofil**: Om du väljer Kräv, anses enheter som inte har en e-postmeddelandeprofil som hanteras av Intune som icke-kompatibla. En enhet kan inte ha en hanterad e-postprofil när den inte är korrekt riktad, eller om användaren manuellt konfigurerar e-postkontot på enheten.

  Enheten betraktas som icke-kompatibel i följande situationer:
  - E-postprofilen har distribuerats till en annan användargrupp än användargruppen som är kompatibilitetsprincipens mål.
  - Användaren har redan konfigurerat ett e-postkonto på enheten som matchar Intune-e-postprofilen som distribuerats till enheten. Intune kan inte skriva över den användartillhandahållna profilen, och kan därför inte hantera den. För att säkerställa efterlevnad måste användaren ta bort de befintliga e-postinställningarna. Sedan kan Intune installera den hantera e-postprofilen.

- **Välj den e-postprofil som måste hanteras av Intune**: Om inställningen **E-postkontot måste hanteras av Intune** har valts väljer du **Välj** för att ange Intune-e-postprofilen. E-postprofilen måste finnas på enheten.

Information om e-postprofiler finns i [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health"></a>Device health

- **Jailbrokade enheter**: Om du aktiverar den här inställningen är jailbrokade enheter inte kompatibla.
- **Enheten måste ligga på eller under enhetshotnivån** (iOS 8.0 eller nyare): Välj den högsta hotnivån för att markera enheter som inkompatibla. Enheter som överskrider den här hotnivå markeras som inkompatibla:
  - **Säkrad**: Det här alternativet är det säkraste eftersom enheten inte kan ha några hot. Om hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om existerande hot på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  - **Hög**: Det här alternativet är det minst säkra och det tillåter alla hotnivåer. Det skulle kunna vara användbart om lösningen endast används i rapporteringssyfte.

## <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion som krävs**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Användarna kan välja att uppgradera sina enheter. Därefter har de åtkomst till företagsresurser.
- **Högsta tillåtna version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som anges i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Enheten kan inte komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

## <a name="system-security"></a>Systemsäkerhet

### <a name="password"></a>Lösenord

> [!NOTE]
> När en efterlevnads- eller konfigurationsprincip används på en iOS-enhet, uppmanas användarna att ange ett lösenord var 15:e minut. Användarna uppmanas kontinuerligt tills ett lösenord anges.

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter. iOS-enheter som använder lösenord krypteras.
- **Enkla lösenord**: Ställ in på **Blockera** om du vill att användaren inte ska kunna skapa enkla lösenord såsom **1234** eller **1111**. Ange till **Inte konfigurerad** så att användarna kan skapa lösenord som **1234** eller **1111**.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.
- **Krav på lösenordstyp**: Ange om ett lösenord endast ska ha **numeriska** tecken, eller om det ska vara en blandning av siffror och andra tecken (**alfanumeriska**).
- **Antal icke-alfanumeriska tecken i lösenord**: Ange det lägsta antalet specialtecken lösenordet (&, #, %, ! och så vidare) som måste ingå i lösenordet.

    Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Ange antalet tidigare lösenord som inte får återanvändas.

## <a name="assign-user-groups"></a>Tilldela användargrupper

1. Välj en princip som du har konfigurerat. Befintliga principer finns i **Enhetsefterlevnad** > **Principer**.
2. Välj principen och välj **Tilldelningar**. Du kan inkludera eller exkludera säkerhetsgrupper i Azure Active Directory (AD).
3. Välj **Valda grupper** för att se dina Azure AD-säkerhetsgrupper. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj **Spara** för att distribuera principen till användare.

Du har tillämpat principen på användarna. Enheterna som används av de användare som principen är inriktad på kommer att utvärderas för att se om de följer standard.

## <a name="next-steps"></a>Nästa steg
[Automatisera e-post och lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md)  
[Övervaka efterlevnadsprinciper för Intune-enheter](compliance-policy-monitor.md)