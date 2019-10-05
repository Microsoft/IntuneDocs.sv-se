---
title: Kompatibilitetsinställningar för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du konfigurerar kompatibilitet för macOS-enheter i Microsoft Intune. Kräv Apples systemintegritetsskydd, ange begränsningar för lösenord, kräv en brandvägg, tillåt gatekeeper och mycket mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22bd3dd50f6c2cbeba59aad4dd00683d52668f72
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733042"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>macOS-inställningar för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Den här artikeln innehåller en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på macOS-enheter i Intune. Använd dessa inställningar som en del av din MDM-lösning för hantering av mobilenheter, t.ex. för att ställa in en lägsta eller högsta operativsystemversion eller ange när lösenord upphör att gälla.

Den här funktionen gäller för:

- macOS

Som Intune-administratör kan du använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Mer om kompatibilitetsprinciper och vad de gör finns i [Komma igång med kompatibilitet](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). Som **Plattform**, välj **macOS**.

## <a name="device-health"></a>Enhetens hälsotillstånd

- **Kräv systemintegritetsskydd**: **Kräv** att [Systemintegritetsskydd](https://support.apple.com/HT204899) är aktiverat för dina macOS-enheter (Apples webbplats öppnas). Om inställningen **Inte konfigurerad** (standard) används görs ingen kompatibilitetskontroll för den här inställningen.

## <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.
- **Högsta version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som anges i regeln blockeras åtkomsten till företagsresurser. Användaren uppmanas sedan att kontakta IT-administratören. Enheten kan inte komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.
- **Lägsta OS-versionsnumret**: När Apple publicerar säkerhetsuppdateringar, uppdateras normalt inte versionsnumret av Operativsystemet. Använd denna funktion för att ange ett minsta tillåtna versionsnummer på enheten.
- **Högsta OS-versionsnumret**: När Apple publicerar säkerhetsuppdateringar, uppdateras normalt inte versionsnumret av Operativsystemet. Använd denna funktion för att ange ett högsta tillåtna versionsnummer på enheten.

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter:** **Begär** att användare måste ange ett lösenord för att få åtkomst till sina enheter.
- **Enkla lösenord**: Ställ in på **Blockera** om du vill att användaren inte ska kunna skapa enkla lösenord såsom **1234** eller **1111**. Ange till **Inte konfigurerad** så att användarna kan skapa lösenord som **1234** eller **1111**.
- **Minsta längd på lösenord**: Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.
- **Lösenordstyp**: Ange om ett lösenord endast ska ha **numeriska** tecken, eller om det ska vara en blandning av siffror och andra tecken (**alfanumeriska**).
- **Antal icke-alfanumeriska tecken i lösenord**: Ange det lägsta antalet specialtecken, t.ex. `&`, `#`, `%` och `!`, som lösenordet måste innehålla.

    Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

- **Max antal minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.
- **Antal tidigare lösenord för att förhindra återanvändning**: Ange det antal tidigare lösenord som inte får återanvändas.

    > [!IMPORTANT]
    > När lösenordskravet ändras på en macOS-enhet börjar det inte gälla förrän nästa gång användaren ändrar sitt lösenord. Om du till exempel ställer in begränsning av lösenordslängd till åtta siffror och macOS-enheten för närvarande har lösenord med sex siffror så fortsätter enheten att vara kompatibel till nästa gång användaren uppdaterar sitt lösenord på enheten.

### <a name="encryption"></a>Kryptering

- **Kryptering för lagring av data på en enhet**: Välj **Kräv** för att kryptera lagring av data på dina enheter.

### <a name="device-security"></a>Enhetssäkerhet

Brandväggen skyddar enheter mot obehörig nätverksåtkomst. Du kan använda brandväggen för att styra anslutningar per program. 

- **Brandvägg**: Välj **Aktivera** för att skydda enheter mot obehörig åtkomst. Genom att aktivera den här funktionen kan du hantera inkommande Internetanslutningar och använda dolt läge. **Inte konfigurerad** (standard) lämnar brandväggen avstängd, och nätverkstrafik tillåts (inte blockerad).
- **Inkommande anslutningar**: **Blockera** alla inkommande nätverksanslutningar utom de anslutningar som krävs för grundläggande Internettjänster, till exempel DHCP, Bonjour och IPSec. Den här inställningen blockerar även alla delningstjänster, inklusive skärmdelning, fjärråtkomst, iTunes-musikdelning med mera. **Inte konfigurerad** (standard) tillåter inkommande anslutningar och delningstjänster.
- **Dolt läge**: **Aktivera** dolt läge om du vill förhindra att enheter svarar på avsökningsförfrågningar, som kan göras av illvilliga användare. När det här är aktiverat fortsätter enheten att besvara inkommande begäranden för godkända appar. **Inte konfigurerad** (standard) lämnar dolt läge avstängt.

### <a name="gatekeeper"></a>Gatekeeper

Mer information finns i [Gatekeeper i macOS](https://support.apple.com/HT202491) (Apples webbplats öppnas).

**Tillåt nedladdade appar från de här platserna**: Gör att program som stöds kan installeras på dina enheter från olika platser. Du kan välja mellan följande platsalternativ:

- **Inte konfigurerat**: Standard. Gatekeeper-alternativet har ingen effekt på kompatibilitet eller inkompatibilitet. 
- **Mac App Store**: Installera endast appar för Mac App Store. Appar kan inte installeras från tredje part eller identifierade utvecklare. Om en användare väljer Gatekeeper för att installera appar utanför Mac App Store utvärderas enheten som inkompatibel.
- **Mac App Store och identifierade utvecklare**: Installera appar för Mac App Store och från identifierade utvecklare. macOS kontrollerar utvecklarens identitet och gör vissa andra kontroller för att kontrollera appintegriteten. Om en användare väljer Gatekeeper för att installera appar som inte matchar dessa alternativ utvärderas enheten som inkompatibel.
- **Överallt**: Appar kan installeras från valfri plats och utvecklare. Det här alternativet är det minst säkra.

Välj **OK** > **Skapa** för att spara ändringarna.

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](../fundamentals/scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för iOS-enheter](compliance-policy-create-ios.md).