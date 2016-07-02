---
title: Enhetsefterlevnadsprinciper | Microsoft Intune
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9e069a2887b812b30c620634a8e0d093093b460
ms.openlocfilehash: c443bb51ba05161c5088475e528e6ada28c105a5


---

# Enhetsefterlevnadsprinciper i Microsoft Intune
## Vad är en efterlevnadsprincip?
För att skydda företagets data, måste du se till att de enheter som används för åtkomst till företagets appar och data överensstämmer med vissa regler, t.ex. använder en PIN-kod för att komma åt enheten, och kryptering av data som lagras på enheten. Dessa regler kallas för en princip för efterlevnad.

## Hur använder jag principer för efterlevnad?
Du kan använda principer för efterlevnad med principer för villkorlig åtkomst för att endast tillåta åtkomst för enheter som uppfyller principregler för efterlevnad för åtkomst till e-post och andra tjänster. Läs artikeln om att [begränsa åtkomst till e-post och O365-tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) för att förstå hur två principer kan användas tillsammans.

Du kan också använda principer för efterlevnad oberoende av villkorlig åtkomst. När de används oberoende kommer de aktuella enheterna att utvärderas och rapporteras med deras efterlevnadsstatus. Du kanske vill rapportera om hur många enheter som inte är krypterade eller vilka enheter som är jailbreakade eller rootade. När funktionen används enskilt, finns inga åtkomstbegränsningar till företagsresurser på plats.

Du distribuerar efterlevnadsprinciper till användare. När en efterlevnadsprincip distribueras till en användare så kontrolleras om användarens enheter uppfyller efterlevnadskraven.

I följande tabell förtecknas de enhetstyper som stöds av efterlevnadsprinciper och hur inkompatibla inställningar hanteras när principen används med en princip för villkorlig åtkomst.

--------------

|Principinställning| Windows 8.1 och senare| Windows Phone 8.1 och senare| iOS 6.0 och senare|Android 4.0 och senare<br/>Samsung KNOX Standard 4.0 och senare|
|-----|----|----|----|
|**Konfiguration av PIN-kod eller lösenord** |Åtgärdad|Åtgärdad|Åtgärdad|I karantän|
|**Enhetskryptering**|E.t.|Åtgärdad|Åtgärdad (genom angiven PIN-kod)|I karantän|
|**Jailbreakad eller rotad enhet**|E.t.|E.t.|I karantän (inte en inställning)|I karantän (inte en inställning)|
|**E-postprofil**|E.t.|E.t.|I karantän|E.t.|
|**Lägsta version av operativsystemet**|I karantän|I karantän|I karantän|I karantän|
|**Högsta version av operativsystemet**|I karantän| I karantän| I karantän| I karantän|
|**Attesteringen av hälsotillstånd i Windows**|Windows 10 och Windows 10 Mobile är i karantän.<br /><br />Inställningen gäller inte för Windows 8.1|E.t.|E.t.|E.t.|
--------------
**Åtgärdad** = Efterlevnad påtvingas av enhetens operativsystem (t.ex. om användaren tvingas ange en PIN-kod).  Det finns inga fall där inställningen inte uppfyller efterlevnadskraven.

**I karantän** = Enhetens operativsystem påtvingar inte efterlevnad (Android-enheter tvingar t.ex. inte användaren att kryptera enheten). När enheterna inte uppfyller efterlevnadskraven utförs följande åtgärder:

-   Enheten blockeras om användaren utsätts för en princip för villkorlig åtkomst.

-   Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## Nästa steg
[Skapa en enhetsefterlevnadsprincip](create-a-device-compliance-policy-in-microsoft-intune.md)

[Distribuera och övervaka en enhetsefterlevnadsprincip](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### Se även
[Begränsa åtkomst till e-post och O365-tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


