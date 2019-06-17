---
title: inkludera fil
description: inkludera fil
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fab8f2be48a30f6ad058b3eeb6874a44ff04e6ac
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744295"
---
Dessa meddelanden innehåller viktig information som kan hjälpa dig att förbereda dig för framtida ändringar och funktioner i Intune. 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Uppdatera företagsportalappen för Android till den senaste versionen <!--4536963-->
Intune släpper regelbundet uppdateringar till företagsportalsappen för Android. I November 2018 släppte vi en uppdatering av företagsportalen som innehåller en serverdeländring. Detta är en förberedelse inför Googles övergång från deras befintliga meddelandeplattform till Googles Firebase Cloud Messaging (FCM). När Google drar tillbaka sin nuvarande plattform och flyttar till FCM måste användarna ha uppdaterat företagsportalsappen till versionen från november 2018 eller senare för att fortsätta kommunicera med Google Play-butiken.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Vår telemetri visar att du har enheter med en version av företagsportalen som är äldre än 5.0.4269.0. Om den här versionen eller en senare av företagsportalappen inte är installerad, kan enhetsåtgärder som utförs av IT-personal som att rensa, återställa lösenord, installation av tillgängliga och nödvändiga appar samt certifikatregistrering kanske inte fungera som förväntat. Om enheterna är registrerade i Intune MDM kan du se företagets portalversioner och -användare genom att gå till klientappar – identifierade appar. Genom att välja tidigare versioner av företagsportalen kan du se vilka användare som har enheter som inte har uppdaterat företagsportalen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Be slutanvändare av Android-enheter som inte har uppdaterats att uppdatera företagsportalen via Google play. Meddela supportavdelningen om en användare inte har aktiverat automatisk uppdatering av företagsportalappen. Se länken i Ytterligare information för mer information om Googles FCM-plattform och övergång.

#### <a name="additional-information"></a>Ytterligare information
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Den nya helskärmsupplevelsen kommer till Intune <!--4593669-->
Vi lanserar uppdaterade upplevelser för att skapa och redigera användargränssnitt i Intune i Azure-portalen. Den här nya upplevelsen förenklar befintliga arbetsflöden genom att använda ett guidestilformat som ryms inom ett blad. Den här uppdateringen kommer att avlägsna ”bladspridning” eller andra redigeringsflöden som kräver att du granskar bladet djupgående. Skapa arbetsflöden kommer också att uppdateras för att inkludera tilldelningar (förutom apptilldelning).

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Helskärmsupplevelsen kommer att lanseras till Intune både på portal.azure.com och devicemanagement.microsoft.com under de kommande månaderna. Den här uppdateringen i användargränssnittet påverkar inte funktionerna i dina befintliga principer och profiler, men du ser ett något justerat arbetsflöde. När du skapar nya principer, kommer du till exempel att kunna ange vissa tilldelningar som en del av det här flödet i stället för att göra det när du har skapat principen. Du hittar mer information i blogginlägget med skärmbilder över hur den nya upplevelsen ser ut i konsolen.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du behöver inte vidta några åtgärder, men du kan överväga att uppdatera din IT Pro-vägledning om det behövs. Vi kommer att uppdatera vår dokumentation då den här upplevelsen distribueras till olika blad i Intune på Azure-portalen.

#### <a name="additional-information"></a>Ytterligare information 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>Planera för förändring: Intune går över till iOS 11 och senare i september <!-- 4665342-->
Vi förväntar oss att Apple lanserar iOS 13 i september. Strax efter lanseringen av iOS 13 går Intune, inklusive Intune-registreringen, företagsportalen och den hanterade webbläsaren, över till iOS 11 och senare.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Förutsatt att mobilappar för O365 stöds i iOS 11.0 och senare kanske detta inte påverkar dig. Du har förmodligen redan uppgraderat operativsystemet eller enheterna. Om du däremot har någon av enheterna som anges nedan, eller om du beslutar dig för att registrera någon av enheterna som anges nedan, bör du vara medveten om att enheterna nedan inte stöder operativsystem efter iOS 10. Enheterna måste uppgraderas till en enhet som stöder iOS 11 eller senare:

- iPhone 5
- iPhone 5c
- iPad (4:e generationen)

Med början i juli får MDM-registrerade enheter med iOS 10 och företagsportalen en uppmaning om att uppgradera operativsystemet eller enheten. Om du använder appskyddsprinciper (APP) kan du även konfigurera åtkomstinställningen ”Kräv lägsta iOS-operativsystem (endast varning)”.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Kontrollera din Intune-rapportering för att se vilka enheter eller användare som kan påverkas. Gå till **Enheter** > **Alla enheter** och filtrera efter operativsystem. Du kan lägga till fler kolumner för att hjälpa till att identifiera vem i din organisation som har enheter som kör iOS 10. Uppmana dina slutanvändare att uppgradera sina enheter till en operativsystemversion som stöds innan september.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Planera för förändring: Stöd för version 8.1.1 och senare för Intune App SDK för iOS <!-- 3586942-->
Från och med september 2019 börjar Intune stödja iOS-appar med Intune App SDK 8.1.1 och senare. Appar som skapats med SDK-versioner som är lägre än 8.1.1 kommer inte längre att stödjas. Den här ändringen ska börja gälla i och med Apple-versionen av iOS 13 som förväntas komma runt september. Det har även tillkännagivits i MC181399.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Du kan skydda företagets data från icke-godkända applikationer och användare via datakryptering med Intune App SDK eller genom att integrera programhantering. Intune App SDK för iOS använder 256-bitars krypteringsnycklar som standard när kryptering har aktiverats av Intune-appskyddsprinciper (APP). Efter den här ändringen kommer alla iOS-appar i SDK-versioner före 8.1.1, som använder 128-bitars krypteringsnycklar, inte längre att kunna dela data med program som är integrerade med SDK 8.1.1 eller med 256-bitars nycklar. Alla iOS-appar måste vara i SDK-version 8.1.1 eller senare för att delning av skyddade data ska vara möjlig.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Kontrollera dina appar från Microsoft och tredje part samt dina verksamhetsspecifika appar (LOB). Du bör se till att alla dina program som skyddas med Intune-appen använder SDK-version 8.1.1 eller senare.

- För LOB-appar: Du kan behöva publicera dina appar som är inbyggda i SDK-version 8.1.1 eller senare på nytt. Vi rekommenderar den senaste SDK-versionen. Mer information om hur du förbereder dina LOB-appar för appskyddsprinciper finns i [Förbereda branschspecifika appar för appskyddsprinciper](../apps-prepare-mobile-application-management.md).
- För appar från Microsoft/tredje part: Se till att du distribuerar den senaste versionen av de här apparna till användarna.

Du bör också uppdatera din dokumentation eller vägledning för utvecklare om det är tillämpligt för att inkludera den här ändringen i stödet för SDK.

#### <a name="additional-information"></a>Ytterligare information
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management
