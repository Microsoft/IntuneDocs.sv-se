---
title: Efterlevnadsprinciper för enheter
description: Det här avsnittet förklarar vad efterlevnadsprinciper för enheter är och hur de fungerar.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ce8375a1b946a7ba5286637b1958539fd5015d8a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="device-compliance-policies-in-microsoft-intune"></a>Enhetsefterlevnadsprinciper i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="what-is-a-compliance-policy"></a>Vad är en efterlevnadsprincip?
För att skydda företagets data måste du se till att de enheter som används för åtkomst till företagets appar och data följer särskilda regler. Dessa regler kan till exempel kräva att en PIN-kod används för att komma åt enheter samt kryptering av data som lagras på enheter. En samling regler som dessa kallas för en efterlevnadspolicy.

## <a name="how-should-i-use-compliance-policies"></a>Hur använder jag principer för efterlevnad?
Du kan använda efterlevnadsprinciper med principer för villkorlig åtkomst om du endast vill ge enheter som uppfyller efterlevnadsprincipregler åtkomst till e-post och andra tjänster. Information om hur de två principerna kan användas tillsammans finns i artikeln [Begränsa åtkomst till e-post och O365-tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Du kan också använda principer för efterlevnad oberoende av villkorlig åtkomst. När du använder efterlevnadsprinciper separat utvärderas målenheterna varefter deras efterlevnadsstatus rapporteras. Du kanske vill rapportera om hur många enheter som inte är krypterade eller vilka enheter som är jailbreakade eller rootade. Men när du använder efterlevnadsprinciper separat tillämpas inga åtkomstbegränsningar på företagsresurser.

Du distribuerar efterlevnadsprinciper till användare. När en efterlevnadsprincip distribueras till en användare så kontrolleras om användarens enheter uppfyller efterlevnadskraven.
Information om hur lång tid det tar för mobila enheter att hämta en princip efter att den har distribuerats finns i [Hantera inställningar och funktioner på dina enheter](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies).

Följande tabell innehåller de enhetstyper som har stöd för efterlevnadsprinciper. Tabellen beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst.

-----------------------------

|Principinställningar| Windows 8.1 och senare| Windows Phone 8.1 och senare| iOS 8.0 och senare|Android 4.0 och senare<br/>Samsung Knox Standard 4.0 och senare|
|-----|----|----|----|----|
|**Konfiguration av PIN-kod eller lösenord** |Åtgärdad|Åtgärdad|Åtgärdad|I karantän|
|**Enhetskryptering**|Inte tillämpligt|Åtgärdad|Åtgärdad (genom angiven PIN-kod)|I karantän|
|**Jailbreakad eller rotad enhet**|Inte tillämpligt|Inte tillämpligt|I karantän (inte en inställning)|I karantän (inte en inställning)|
|**E-postprofil**|Inte tillämpligt|Inte tillämpligt|I karantän|Inte tillämpligt|
|**Lägsta version av operativsystemet**|I karantän|I karantän|I karantän|I karantän|
|**Högsta version av operativsystemet**|I karantän|I karantän|I karantän|I karantän|
|**Attestering av hälsotillstånd i Windows**|I karantän: Windows 10 och Windows 10 Mobile<br /><br />Inte tillämpligt: Windows 8.1|Inte tillämpligt|Inte tillämpligt|Inte tillämpligt|

------------------------------

**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. (Till exempel om användaren tvingas att ange en PIN-kod.)

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheterna inte uppfyller efterlevnadskraven utförs följande åtgärder:

-   Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.

-   Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="next-steps"></a>Nästa steg
[Skapa en enhetsefterlevnadsprincip](create-a-device-compliance-policy-in-microsoft-intune.md)

[Distribuera och övervaka en enhetsefterlevnadsprincip](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>Se även
[Begränsa åtkomst till e-post och O365-tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
