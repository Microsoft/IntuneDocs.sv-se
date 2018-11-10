---
title: Skapa en efterlevnadsprincip för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa eller konfigurera en Microsoft Intune-enhetsefterlevnadsprincip för macOS-enheter för att använda systemintegritetsskydd, ange lägsta och högsta operativsystemversion, välja dina lösenordskrav och kryptera datalagring.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a0d9d0ac3c0cd8804ffc401cd3041d5b9a17e64f
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236415"
---
# <a name="add-a-device-compliance-policy-for-macos-devices-with-intune"></a>Lägg till en enhetsefterlevnadsprincip för macOS-enheter med Intune

En Intune macOS-enhetsefterlevnadsprincip anger de regler och inställningar som macOS-enheter måste uppfylla för att vara kompatibla. När du använder principer för enhetsefterlevnad med villkorlig åtkomst kan du tillåta eller blockera åtkomst till företagsresurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet. Du kan skapa efterlevnadsprinciper för enheter för varje plattform i Intune Azure-portalen. Läs mer om efterlevnadsprinciper och eventuella förutsättningar i [Kom igång med enhetsefterlevnad](device-compliance-get-started.md).

Följande tabell beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst:

---------------------------

| Principinställningar | macOS 10.11 och senare |
| --- | --- |
| **Konfiguration av PIN-kod eller lösenord** | Åtgärdad |   
| **Enhetskryptering** | Åtgärdad (genom angiven PIN-kod) |
| **E-postprofil** | I karantän |
|**Lägsta version av operativsystemet** | I karantän |
| **Högsta version av operativsystemet** | I karantän |

---------------------------

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. Till exempel om användaren tvingas att ange en PIN-kod.

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Som **Plattform**, välj **macOS**. Välj **Inställningar** för att konfigurera och ange inställningar för **Enhetens hälsotillstånd**, **Enhetsegenskaper** och **Systemsäkerhet**. När du är klar väljer du **OK**, och **Skapa**.

## <a name="device-health"></a>Enhetens hälsotillstånd

- **Kräv ett systemintegritetsskydd**: **Kräv** att dina macOS-enheter har [systemintegritetsskydd](https://support.apple.com/HT204899) aktiverat.

## <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som anges i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Enheten kan inte komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Enkla lösenord**: Ställ in på **Blockera** om du vill att användaren inte ska kunna skapa enkla lösenord såsom **1234** eller **1111**. Ange till **Inte konfigurerad** så att användarna kan skapa lösenord som **1234** eller **1111**.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.
- **Lösenordstyp**: Ange om ett lösenord endast ska ha **numeriska** tecken, eller om det ska vara en blandning av siffror och andra tecken (**alfanumeriska**).
- **Antal icke-alfanumeriska tecken i lösenord**: Ange det lägsta antalet specialtecken lösenordet (&, #, %, ! och så vidare) som måste ingå i lösenordet.

    Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Förhindra återanvändning av tidigare lösenord**: Ange antalet tidigare lösenord som inte får återanvändas.

    > [!IMPORTANT]
    > När lösenordskravet ändras på en macOS-enhet börjar det inte gälla förrän nästa gång användaren ändrar sitt lösenord. Om du till exempel ställer in begränsning av lösenordslängd till åtta siffror och macOS-enheten för närvarande har lösenord med sex siffror så fortsätter enheten att vara kompatibel till nästa gång användaren uppdaterar sitt lösenord på enheten.

### <a name="encryption"></a>Kryptering

- **Kryptering för lagring av data på en enhet**: Välj **Kräv** för att kryptera lagring av data på dina enheter.

### <a name="device-security"></a>Enhetssäkerhet
Brandväggen skyddar enheter mot obehörig nätverksåtkomst. Du kan använda brandväggen för att styra anslutningar per program. 

- **Brandvägg**: **Aktivera** för att skydda enheter mot obehörig åtkomst. Genom att aktivera den här funktionen kan du hantera inkommande Internetanslutningar och använda dolt läge. **Inte konfigurerad** (standard) lämnar brandväggen avstängd, och nätverkstrafik tillåts (inte blockerad).
- **Inkommande anslutningar**: **Blockera** alla inkommande nätverksanslutningar förutom de som behövs för grundläggande internettjänster, som DHCP, Bonjour och IPSec. Den här inställningen blockerar även alla delningstjänster, inklusive skärmdelning, fjärråtkomst, iTunes-musikdelning med mera. **Inte konfigurerad** (standard) tillåter inkommande anslutningar och delningstjänster. 
- **Dolt läge**: **Aktivera** dolt läge om du vill förhindra att enheten svarar på avsökningsförfrågningar, vilka kan utföras av användare som vill vålla skada. När det här är aktiverat fortsätter enheten att besvara inkommande begäranden för godkända appar. **Inte konfigurerad** (standard) lämnar dolt läge avstängt.

### <a name="gatekeeper"></a>Gatekeeper

**Tillåt nedladdade appar från de här platserna**: Gör att program som stöds kan installeras på dina enheter från olika platser. Du kan välja mellan följande platsalternativ:

- **Inte konfigurerat**: Standard. Gatekeeper-alternativet har ingen effekt på kompatibilitet eller inkompatibilitet. 
- **Mac App Store**: Installera endast appar för Mac App Store. Appar kan inte installeras från tredje part eller identifierade utvecklare. Om en användare väljer Gatekeeper för att installera appar utanför Mac App Store utvärderas enheten som inkompatibel.
- **Mac App Store och identifierade utvecklare**: Installera appar för Mac App Store och från identifierade utvecklare. macOS kontrollerar utvecklarens identitet och gör vissa andra kontroller för att kontrollera appintegriteten. Om en användare väljer Gatekeeper för att installera appar som inte matchar dessa alternativ utvärderas enheten som inkompatibel.
- **Överallt**: Appar kan installeras från valfri plats och utvecklare. Det här alternativet är det minst säkra.

Mer information i Apple-dokumentationen finns i avsnittet om [Gatekeeper på macOS](https://support.apple.com/HT202491).

## <a name="assign-user-groups"></a>Tilldela användargrupper

1. Välj en princip som du har konfigurerat. Befintliga principer finns i **Enhetsefterlevnad** > **Principer**.
2. Välj principen och välj **Tilldelningar**. Du kan inkludera eller exkludera säkerhetsgrupper i Azure Active Directory (AD).
3. Välj **Valda grupper** för att se dina Azure AD-säkerhetsgrupper. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj **Spara** för att distribuera principen till användare.

> [!TIP]
> Som standard kontrollerat enheter efterlevnad var åttonde timme. Men användarna kan framtvinga den här processen via företagsportalappen.

Du har tillämpat principen på användarna. Enheterna som används av de användare som principen är inriktad på kommer att utvärderas för att se om de följer standard.

## <a name="next-steps"></a>Nästa steg
[Automatisera e-post och lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md)  
[Övervaka efterlevnadsprinciper för Intune-enheter](compliance-policy-monitor.md)
