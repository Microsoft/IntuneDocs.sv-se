---
title: Kompatibilitetsinställningar för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Visa en lista över alla inställningar som du kan använda när du konfigurerar kompatibilitet för macOS-enheter i Microsoft Intune. Kräv Apples systemintegritetsskydd, ange begränsningar för lösenord, kräv en brandvägg, tillåt gatekeeper och mycket mer.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 518f0b825b71a9773ed66dd480b329e998f919c4
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813499"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>macOS-inställningar för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune

Den här artikeln innehåller en lista över och beskriver de olika kompatibilitetsinställningar som du kan konfigurera på macOS-enheter i Intune. Använd dessa inställningar som en del av din MDM-lösning för hantering av mobilenheter, t.ex. för att ställa in en lägsta eller högsta operativsystemversion eller ange när lösenord upphör att gälla.

Den här funktionen gäller för:

- macOS

Som Intune-administratör kan du använda dessa kompatibilitetsinställningar för att skydda din organisations resurser. Mer om kompatibilitetsprinciper och vad de gör finns i [Komma igång med kompatibilitet](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en efterlevnadsprincip](create-compliance-policy.md#create-the-policy). Som **Plattform**, välj **macOS**.

## <a name="device-health"></a>Enhetens hälsotillstånd

- **Kräv ett system integritets skydd**:  
  - **Ej konfigurerad** (*standard*) – Ingen kompatibilitetskontroll görs för den här inställningen.
  - **Kräv** -kräver att MacOS-enheter har [system integritets skydd](https://support.apple.com/HT204899) (öppnar Apples webbplats) aktiverat.  

## <a name="device-properties"></a>Egenskaper för enhet

- **Lägsta version av operativsystem som krävs**:  
  När en enhet inte uppfyller minimikravet på operativsystemversion, rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Enhetsanvändarna kan välja att uppgradera sina enheter. Därefter kan de komma åt organisationens resurser.

- **Högsta tillåtna version av operativsystemet**:  
  När en enhet använder en senare version av operativsystemet än den version som anges i regeln, så blockeras åtkomsten till organisationens resurser. Användaren av enheten ombeds att kontakta IT-administratören. Enheten kan inte komma åt organisationens resurser förrän en regel ändras så att operativsystemversionen stöds.

- **Lägsta operativsystembyggversion**:  
  När Apple publicerar säkerhetsuppdateringar, uppdateras normalt inte versionsnumret av operativsystemet. Använd denna funktion för att ange ett minsta tillåtna versionsnummer på enheten.

- **Högsta operativsystembyggversion**:  
  När Apple publicerar säkerhetsuppdateringar, uppdateras normalt inte versionsnumret av operativsystemet. Använd denna funktion för att ange ett högsta tillåtna versionsnummer på enheten.

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet

### <a name="password"></a>Lösenord

- **Kräv ett lösenord för att låsa upp mobila enheter**:  
  - **Ej konfigurerat** (*standard*)
  - **Kräv** Användarna måste ange ett lösenord innan de får åtkomst till sina enheter.

- **Enkla lösenord**:  
  - **Inte konfigurerad** (*standard*) – användare kan skapa lösen ord enkelt som **1234** eller **1111**.
  - **Blockera** – Användarna kan inte skapa enkla lösenord, som exempelvis **1234** eller **1111**.

- **Minsta lösenordslängd**:  
  Ange det minsta antal siffror eller tecken som lösenordet måste innehålla.

- **Lösenordstyp**: Ange om ett lösenord endast ska ha **numeriska** tecken, eller om det ska vara en blandning av siffror och andra tecken (**alfanumeriska**).

- **Antal icke-alfanumeriska tecken i lösenord**:  
  Ange det lägsta antalet specialtecken (`&`, `#`, `%`, `!` osv) som måste ingå i lösenordet.

  Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

- **Maximalt antal minuters inaktivitet innan lösenord krävs**:  
  Ange efter hur lång tids inaktivitet som användaren måste ange sitt lösenord igen.

- **Förfallotid för lösenord (dagar)** :  
  Ange antalet dagar tills lösenordet upphör att gälla och användaren måste skapa ett nytt.

- **Antal tidigare lösenord för att förhindra återanvändning**:  
  Ange antal tidigare använda lösenord som inte får återanvändas.
> [!IMPORTANT]
> När lösenordskravet ändras på en macOS-enhet börjar det inte gälla förrän nästa gång användaren ändrar sitt lösenord. Om du till exempel ställer in begränsning av lösenordslängd till åtta siffror och macOS-enheten för närvarande har lösenord med sex siffror så fortsätter enheten att vara kompatibel till nästa gång användaren uppdaterar sitt lösenord på enheten.

### <a name="encryption"></a>Kryptering

- **Kryptering av datalagring på en enhet**:  
  - **Ej konfigurerat** (*standard*)
  - **Kräv** – Använd *Kräv* när du ska kryptera datalagring på dina enheter.

### <a name="device-security"></a>Enhetssäkerhet

Brandväggen skyddar enheter mot obehörig nätverksåtkomst. Du kan använda brandväggen för att styra anslutningar per program. 

- **Brandvägg**:  
  - **Ej konfigurerad** (*standard*) – Den här inställningen lämnar brandväggen avstängd, och nätverkstrafik tillåts (blockeras ej).
  - **Aktivera** – Använd *Aktivera* om du vill skydda enheter mot obehörig åtkomst. Genom att aktivera den här funktionen kan du hantera inkommande Internetanslutningar och använda dolt läge. 

- **Inkommande anslutningar**:  
  - **Ej konfigurerad** (*standard*) tillåter inkommande anslutningar och delningstjänster.
  - **Block** – Blockera alla inkommande nätverksanslutningar utom de anslutningar som krävs för grundläggande Internettjänster, till exempel DHCP, Bonjour och IPSec. Den här inställningen blockerar även alla delningstjänster, inklusive skärmdelning, fjärråtkomst, iTunes-musikdelning med mera.  

- **Dolt läge**:  
  - **Inte konfigurerad** (*standard*) – den här inställningen låter dolt-läget vara inaktiverat.
  - **Aktivera** – Aktivera dolt läge om du vill förhindra att enheter svarar på avsökningsförfrågningar, som kan göras av illvilliga användare. När det här är aktiverat fortsätter enheten att besvara inkommande begäranden för godkända appar.  

### <a name="gatekeeper"></a>Gatekeeper

Mer information finns i [Gatekeeper i macOS](https://support.apple.com/HT202491) (Apples webbplats öppnas).

**Tillåt nedladdade appar från de här platserna**: Gör att program som stöds kan installeras på dina enheter från olika platser. Du kan välja mellan följande platsalternativ:

- **Inte konfigurerat** (*standard*) – Gatekeeper-alternativet har ingen inverkan på efterlevnad eller inkompatibilitet.  
- **Mac App Store** – Installera endast appar för Mac App Store. Appar kan inte installeras från tredje part eller identifierade utvecklare. Om en användare väljer Gatekeeper för att installera appar utanför Mac App Store utvärderas enheten som inkompatibel.
- **Mac App Store och identifierade utvecklare** – Installera appar för Mac App Store och från identifierade utvecklare. macOS kontrollerar utvecklarens identitet och gör vissa andra kontroller för att kontrollera appintegriteten. Om en användare väljer Gatekeeper för att installera appar som inte matchar dessa alternativ utvärderas enheten som inkompatibel.
- **Överallt** – Appar kan installeras från valfri plats och utvecklare. Det här alternativet är det minst säkra.
 

## <a name="next-steps"></a>Nästa steg

- [Lägga till åtgärder för inkompatibla enheter](actions-for-noncompliance.md) och [Filtrera principer med hjälp av omfångstaggar](../fundamentals/scope-tags.md).
- [Övervaka dina kompatibilitetsprinciper](compliance-policy-monitor.md).
- Mer information finns i [Inställningar för kompatibilitetsprinciper för iOS-enheter](compliance-policy-create-ios.md).