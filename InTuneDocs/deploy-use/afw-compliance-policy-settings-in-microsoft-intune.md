---
title: "Efterlevnadsinställningar för Android for Work | Microsoft Docs"
description: "I det här avsnittet beskrivs inställningarna för efterlevnadsprinciper för Android-enheter som är kompatibla med Android for Work."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 31e28514ab4bdb0f5af261a1f7c87633ca0bd4a6
ms.openlocfilehash: 1b84b7137bd01b695d20bea67d77c694f2533b4e


---


# <a name="compliance-policy-settings-for-android-for-work-devices-in-microsoft-intune"></a>Inställningar för efterlevnadsprinciper för Android for Work-enheter i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Principinställningarna som beskrivs i det här avsnittet gäller för Android for Work-enheter.

Om du letar efter information om andra plattformar väljer du något av följande:
> [!div class="op_single_selector"]
- [Inställningar för efterlevnadsprinciper för Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för efterlevnadsprinciper för iOS-enheter](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för efterlevnadsprinciper för Windows-enheter](windows-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Systemsäkerhetsinställningar
### <a name="password"></a>Lösenord
- **Kräv lösenord för att låsa upp mobila enheter:** Ställ in på **Ja** för att ställa in så att användare måste ange ett lösenord för att få åtkomst till sina enheter.

-  **Minsta längd på lösenord:** Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.

- **Lösenordskvalitet:** Den här inställningen identifierar om lösenordskraven som du anger är konfigurerade på enheten. Aktivera den här inställningen för att kräva att användare konfigurera vissa lösenordskrav för Android-enheter. Välj mellan:
  -   **Låg säkerhetsbiometri**
  - **Obligatoriskt**
  -   **Minst numeriskt**
  -   **Minst alfabetiskt**
  -   **Minst alfanumeriskt**
  -   **Alfanumeriskt med symboler**

- **Minuter av inaktivitet innan lösenord måste anges:** Anger efter hur lång tids inaktivitet som användaren måste ange lösenordet igen.

- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills användarens lösenord upphör att gälla och användaren måste ange ett nytt lösenord.

- **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.

- **Förhindra återanvändning av tidigare lösenord**: Om **Spara lösenordshistorik** har valts anger du hur många tidigare använda lösenord som inte får återanvändas.

- **Kräv lösenord när enheten lämnar inaktivt läge:** Den här inställningen bör användas tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Användarna uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.

### <a name="encryption"></a>Kryptering
- **Kräv kryptering på den mobila enheten:** Du behöver inte konfigurera den här inställningen eftersom Android for Work-enheter tvingar fram kryptering.

## <a name="device-health-and-security-settings"></a>Inställningar för enhetens för hälsotillstånd och säkerhet

- **Enheten får inte vara jailbrokad eller rotad:** Om du aktiverar den här inställningen kommer jailbrokade enheter att utvärderas som inkompatibla.
- **Kräv att enheter förhindrar installation av appar från okända källor:** Du behöver inte konfigurera den här inställningen eftersom Android for Work-enheter alltid begränsar installationer från okända källor. .  

- **Kräv att USB-felsökning är inaktiverat**: Du behöver inte konfigurera de här inställningarna eftersom USB-felsökning redan är inaktiverat på Android for Work-enheter.

- **Lägsta Android-säkerhetskorrigeringsnivå**: Använd den här inställningen för att ange den lägsta Android-korrigeringsnivån.  Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste ha formatet ÅÅÅÅ-MM-DD.
- **Kräv att enhetsskydd är aktiverat**: Använd den här inställningen för att ta riskbedömningen från enhetsskyddslösningen som ett villkor för efterlevnad. Välj den högsta tillåtna hotnivån, som är en av följande:

  - **Ingen (skyddad)**: Det här är det säkraste alternativet. Detta innebär att enheten inte kan ha några hot. Om hot identifieras på enheten kommer den utvärderas som icke-kompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  - **Hög**: Det här alternativet är minst säkert. I grunden innebär detta att alla hotnivåer är tillåtna och kanske är detta endast användbart om du använder den här lösningen för rapportering.

  Se [Aktivera regeln för skydd mot enhetshot i policyn för efterlevnad](enable-device-threat-protection-rule-in-compliance-policy.md) för mer information.

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper
- **Lägsta operativsystemversion som krävs**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel.
  En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.

- **Högsta tillåtna version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.



<!--HONumber=Feb17_HO1-->


