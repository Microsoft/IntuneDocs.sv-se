---
title: Skapa en efterlevnadsprincip för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa en efterlevnadsprincip för Microsoft Intune-enheter för iOS-enheter för att ange ett e-postkonto, kontrollera jailbrokade enheter, kontrollera lägsta och högsta operativsystem och ange begränsningar för lösenord, inklusive lösenordslängd och enhetsinaktivitet.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b05eb725adb61ae47a24ca884d0e73ffe0dd269f
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/23/2018
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Lägga till en enhetsefterlevnadsprincip för iOS-enheter i Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En Intune iOS-enhetsefterlevnadsprincip anger de regler och inställningar som iOS-enheter måste uppfylla för att vara kompatibla. När du använder principer för enhetsefterlevnad med villkorlig åtkomst kan du tillåta eller blockera åtkomst till företagsresurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet. Du kan skapa efterlevnadsprinciper för enheter för varje plattform i Intune Azure-portalen. Mer information om efterlevnadsprinciper och de förhandskrav du måste uppfylla innan du skapar en efterlevnadsprincip finns i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

Följande tabell beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

| **Principinställning** | **iOS 8.0 och senare** |
| --- | --- |
| **Konfiguration av PIN-kod eller lösenord** | Åtgärdad |
| **Enhetskryptering** | Åtgärdad (genom angiven PIN-kod) |
| **Jailbreakad eller rotad enhet** | I karantän (inte en inställning)
| **E-postprofil** | I karantän |
|**Lägsta version av operativsystemet** | I karantän |
| **Högsta version av operativsystemet** | I karantän |
| **Attestering av hälsotillstånd i Windows** | Inte tillämpligt |

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. (Till exempel om användaren tvingas att ange en PIN-kod.)

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Skapa en efterlevnadsprincip i Azure-portalen

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetsefterlevnad** > **Principer** > **Skapa princip**.
4. Ange ett namn, ange en beskrivning och välj den plattform där du vill att den här principen ska tillämpas.
5. Välj **Inställningar** för att ange inställningar för **E-post**, **Enhetens hälsotillstånd**, **Enhetsegenskaper** och **Systemsäkerhet**. När du är klar väljer du **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Tilldela användargrupper

Om du vill tilldela en efterlevnadsprincip till användare, väljer du en princip som du har konfigurerat. Du hittar befintliga principer i fönstret **Enhetsefterlevnad – Principer**.

1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas det fönster där du kan välja **Azure Active Directory-säkerhetsgrupper** och tilldela dem till principen.
2. Öppna fönstret som visar säkerhetsgrupper för Azure AD genom att välja **Valda grupper**.  När du väljer **Spara** distribueras principen till användarna.

Du har tillämpat principen på användarna.  Enheterna som används av de användare som principen är inriktad på kommer att utvärderas för att se om de följer standard.

<!---## Compliance policy settings--->

## <a name="email"></a>E-post

- **E-postkontot måste hanteras av Intune:** Om det här alternativet är inställt på **Ja** måste enheten använda e-postprofilen som har distribuerats till enheten. Enheten betraktas som icke-kompatibel i följande situationer:
  - E-postprofilen har distribuerats till en annan användargrupp än användargruppen som är kompatibilitetsprincipens mål.
  - Användaren har redan konfigurerat ett e-postkonto på enheten som matchar Intune-e-postprofilen som distribuerats till enheten. Intune kan inte skriva över den användartillhandahållna profilen, och kan därför inte hantera den. För att säkerställa efterlevnad måste användaren ta bort de befintliga e-postinställningarna. Sedan kan Intune installera den hantera e-postprofilen.
- **Välj den e-postprofil som måste hanteras av Intune**: Om inställningen **E-postkontot måste hanteras av Intune** har valts väljer du **Välj** för att ange Intune-e-postprofilen. E-postprofilen måste finnas på enheten.

Information om e-postprofiler finns i [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health"></a>Device health

- **Jailbrokade enheter**: Om du aktiverar den här inställningen är jailbrokade enheter inte kompatibla.
- **Enheten måste ligga på eller under enhetshotnivån**: Välj den högsta hotnivån för att markera enheter som inkompatibla. Om du exempelvis anger hotnivån som **Mellan** är enheter på nivåerna mellan, låg eller säkrad kompatibla. Enheter med en hög hotnivå är inkompatibla.

## <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion som krävs**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Användarna kan välja att uppgradera sina enheter. Därefter har de åtkomst till företagsresurser.
- **Högsta tillåtna version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som anges i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Enheten kan inte komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

## <a name="system-security"></a>Systemsäkerhet

### <a name="password"></a>Lösenord

> [!NOTE]
> När en efterlevnads- eller konfigurationsprincip används på en iOS-enhet, uppmanas användarna att ange ett lösenord var 15:e minut. Användarna uppmanas kontinuerligt tills ett lösenord anges.

- **Kräv lösenord för att låsa upp mobila enheter:** Välj **Ja** om du vill kräva att användarna anger ett lösenord för att få åtkomst till sina enheter. iOS-enheter som använder lösenord krypteras.
- **Enkla lösenord**: Välj **Ja** om du vill att användaren ska kunna skapa ett lösenord som **1234** eller **1111**.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.
- **Krav på lösenordstyp**: Ange om användaren måste skapa ett **alfanumeriskt** lösenord eller ett **numeriskt** lösenord.
- **Antal icke-alfanumeriska tecken i lösenord**: Ange det lägsta antalet specialtecken lösenordet (&, #, %, ! och så vidare) som måste ingå i lösenordet.

    Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Ange antalet tidigare lösenord som inte får återanvändas.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
