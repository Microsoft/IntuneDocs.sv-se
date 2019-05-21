---
title: inkludera fil
description: inkludera fil
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: ffcef5b4d78856709f8563ee1f667ec7e5d993b3
ms.sourcegitcommit: d2e04a38e024b0f5afb0ca202823227de9da3ad1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65732617"
---
Dessa meddelanden innehåller viktig information som kan hjälpa dig att förbereda dig för framtida ändringar och funktioner i Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Ändring i arbetsflöde för registrering med Intune-företagsportalen på företagets iOS-enheter som autentiseras med installationsassistenten <!-- 1927359 -->
Det finns en kommande förändring i arbetsflödet för registrering av iOS-enheter via någon av Apples företagsregistreringsmetoder för enheter – Apple Configurator, Apples Business Manager, Apple School Manager eller Apples program för enhetsregistrering(DEP) när du använder installationsassistenten för autentisering. Den här ändringen gäller endast för enheter som registrerats med användartillhörighet.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
När den här ändringen lanseras kommer profiler för registrering i Intune i Azure-portalen att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Det kommer att finnas ett förbättrat arbetsflöde för att registrera iOS-enheter med de metoder som anges ovan. 

- När du registrerar nya enheter och autentiserar med installationsassistenten kommer du att kunna välja om du vill distribuera automatiskt i företagsportalsappen. Slutanvändarna kommer inte längre visas skärmarna ”Identifiera enhet” och ”Bekräfta din enhet” i flödet för registrering.  
- Du måste vidta åtgärder om du vill aktivera villkorlig åtkomst på enheter som redan har registrerats via installationsassistenten genom någon av Apples metoder för registrering av företagsenheter. Du måste [konfigurera en appkonfigurationsprincip](https://aka.ms/enrollment_setup_assistant) med en specifik xml för att pusha företagsportalen till dessa enheter.  Om du väljer att pusha företagsportalen på detta sätt kommer slutanvändarna inte längre visas skärmarna ”Identifiera enhet” och ”Bekräfta din enhet” i flödet för registrering. 
- Om du inte har distribuerat företagsportalen med den appkonfigurationsprofil som nämns ovan när den här ändringen distribueras och om slutanvändarna hämtar företagsportalappen från App store, kan de logga in, men de kommer att se ett felmeddelande. De kommer inte att kunna använda appen för villkorlig åtkomst. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Om du tänker använda det ändrade arbetsflödet måste du ändra anvisningarna för slutanvändaren för att visa att:

- Slutanvändarna kommer inte längre visas de två skärmarna som nämns i registreringsflödet ovan. 
- De måste logga in på företagsportalen när den distribueras automatiskt och inte ladda ned den från app store. 

Du kan välja att skapa en appkonfigurationsprincip nu som förberedelse inför den här ändringen, om det behövs. När det nya arbetsflödet distribueras visas uppdaterade registreringsprofiler i konsolen. Vi kommer också att informera dig om den här distributionen via vårt meddelandecenter. Du måste sedan vidta åtgärden så att användarna kan registrera via DEP genom att autentisera med installationsassistenten. Du kan använda företagsportalen för villkorlig åtkomst.

#### <a name="additional-information"></a>Mer information 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Uppdatera företagsportalappen för Android till den senaste versionen <!--4536963-->
Intune släpper regelbundet uppdateringar till företagsportalsappen för Android. I November 2018 släppte vi en uppdatering av företagsportalen som innehåller en serverdeländring. Detta är en förberedelse inför Googles övergång från deras befintliga meddelandeplattform till Googles Firebase Cloud Messaging (FCM). När Google drar tillbaka sin nuvarande plattform och flyttar till FCM måste användarna ha uppdaterat företagsportalsappen till versionen från november 2018 eller senare för att fortsätta kommunicera med Google Play-butiken.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Vår telemetri visar att du har enheter med en version av företagsportalen som är äldre än 5.0.4269.0. Om den här versionen eller en senare av företagsportalappen inte är installerad, kan enhetsåtgärder som utförs av IT-personal som att rensa, återställa lösenord, installation av tillgängliga och nödvändiga appar samt certifikatregistrering kanske inte fungera som förväntat. Om enheterna är registrerade i Intune MDM kan du se företagets portalversioner och -användare genom att gå till klientappar – identifierade appar. Genom att välja tidigare versioner av företagsportalen kan du se vilka användare som har enheter som inte har uppdaterat företagsportalen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Be slutanvändare av Android-enheter som inte har uppdaterats att uppdatera företagsportalen via Google play. Meddela supportavdelningen om en användare inte har aktiverat automatisk uppdatering av företagsportalappen. Se länken i Ytterligare information för mer information om Googles FCM-plattform och övergång.

#### <a name="additional-information"></a>Mer information
https://firebase.google.com/docs/cloud-messaging/