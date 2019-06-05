---
title: inkludera fil
description: inkludera fil
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 1073a38da8a5b2467b1ff8c97b32b93f92e34e4c
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454122"
---
Dessa meddelanden innehåller viktig information som kan hjälpa dig att förbereda dig för framtida ändringar och funktioner i Intune. 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Uppdatera företagsportalappen för Android till den senaste versionen <!--4536963-->
Intune släpper regelbundet uppdateringar till företagsportalsappen för Android. I November 2018 släppte vi en uppdatering av företagsportalen som innehåller en serverdeländring. Detta är en förberedelse inför Googles övergång från deras befintliga meddelandeplattform till Googles Firebase Cloud Messaging (FCM). När Google drar tillbaka sin nuvarande plattform och flyttar till FCM måste användarna ha uppdaterat företagsportalsappen till versionen från november 2018 eller senare för att fortsätta kommunicera med Google Play-butiken.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Vår telemetri visar att du har enheter med en version av företagsportalen som är äldre än 5.0.4269.0. Om den här versionen eller en senare av företagsportalappen inte är installerad, kan enhetsåtgärder som utförs av IT-personal som att rensa, återställa lösenord, installation av tillgängliga och nödvändiga appar samt certifikatregistrering kanske inte fungera som förväntat. Om enheterna är registrerade i Intune MDM kan du se företagets portalversioner och -användare genom att gå till klientappar – identifierade appar. Genom att välja tidigare versioner av företagsportalen kan du se vilka användare som har enheter som inte har uppdaterat företagsportalen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Be slutanvändare av Android-enheter som inte har uppdaterats att uppdatera företagsportalen via Google play. Meddela supportavdelningen om en användare inte har aktiverat automatisk uppdatering av företagsportalappen. Se länken i Ytterligare information för mer information om Googles FCM-plattform och övergång.

#### <a name="additional-information"></a>Mer information
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Den nya helskärmsupplevelsen kommer till Intune <!--4593669-->
Vi lanserar uppdaterade upplevelser för att skapa och redigera användargränssnitt i Intune i Azure-portalen. Den här nya upplevelsen förenklar befintliga arbetsflöden genom att använda ett guidestilformat som ryms inom ett blad. Den här uppdateringen kommer att avlägsna ”bladspridning” eller andra redigeringsflöden som kräver att du granskar bladet djupgående. Skapa arbetsflöden kommer också att uppdateras för att inkludera tilldelningar (förutom apptilldelning).

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Helskärmsupplevelsen kommer att lanseras till Intune både på portal.azure.com och devicemanagement.microsoft.com under de kommande månaderna. Den här uppdateringen i användargränssnittet påverkar inte funktionerna i dina befintliga principer och profiler, men du ser ett något justerat arbetsflöde. När du skapar nya principer, kommer du till exempel att kunna ange vissa tilldelningar som en del av det här flödet i stället för att göra det när du har skapat principen. Du hittar mer information i blogginlägget med skärmbilder över hur den nya upplevelsen ser ut i konsolen.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du behöver inte vidta några åtgärder, men du kan överväga att uppdatera din IT Pro-vägledning om det behövs. Vi kommer att uppdatera vår dokumentation då den här upplevelsen distribueras till olika blad i Intune på Azure-portalen.

#### <a name="additional-information"></a>Mer information 
https://aka.ms/intune_fullscreen
