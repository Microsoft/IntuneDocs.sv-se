---
title: inkludera fil
description: inkludera fil
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 90c770fec5bd9456151e601188254a3a022cd13f
ms.sourcegitcommit: 62c41976c4da43b36015b715bc255397ebb8c6ad
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71279912"
---
Dessa meddelanden innehåller viktig information som kan hjälpa dig att förbereda dig för framtida ändringar och funktioner i Intune. 


### <a name="decreasing-support-for-android-device-administrator"></a>Minskat stöd för Android-enhetsadministratör 
Enhetsadministratören för Android (kallas ibland för "äldre" Android-hantering och lanseras med Android 2.2) är ett sätt att hantera Android-enheter. Det finns dock en bättre hanteringsfunktion med [Android Enterprise](../connect-intune-android-enterprise.md) (lanseras med Android 5.0). För att kunna flytta till en modern, mer omfattande och säkrare enhetshantering,minskar Google stödet för enhetsadministration i nya versioner av Android.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
På grund av dessa ändringar av Google kommer Intune-användare att påverkas på följande sätt: 
- Intune kommer bara att kunna tillhandahålla stöd för enhetsadministratörshanterade Android-enheter som kör Android 10 och senare (även kallat Android Q) till och med sommaren 2020. Det här datumet är när nästa högre version av Android förväntas släppas.  
- Enheter som hanteras av en enhetsadministratör som använder Android 10 eller senare efter sommaren 2020 kommer inte längre att kunna hanteras helt.    
- Android-enheter som hanteras av en enhetsadministratör som blir kvar på tidigare versioner av Android än Android 10 påverkas inte och kan fortfarande hanteras av en enhetsadministratör.  
- För alla enheter med Android 10 och senare har Google begränsat möjligheten för hanteringsagenter för enhetsadministratörer som företagsportalen att komma åt information om enhetsidentifieraren. Detta påverkar följande Intune-funktioner efter att enheten har uppdaterats till Android 10 eller senare: 
    - Nätverksåtkomstkontroll för VPN fungerar inte längre.  
    - Om enheter identifieras som företagsägda med IMEI eller serienummer markeras de inte automatiskt som företagsägda. 
    - IMEI och serienumret kommer inte längre att vara synligt för IT-administratörer i Intune. 
        > [!Note]
        > Detta påverkar endast enheter som hanteras av enhetsadministratörer på Android 10 och senare och påverkar inte enheter som hanteras som Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
För att undvika den minskade funktionalitet som sker under sommaren 2020 rekommenderar vi följande:
- Publicera inte nya enheter i hanteringen av enhetsadministratörer.
- Om en enhet förväntas ta emot en uppdatering av Android 10 kan du migrera den från enhetsadministratörshantering för Android Enterprise och/eller appskyddsprinciper.

#### <a name="additional-information"></a>Ytterligare information
- [Googles vägledning för migrering från enhetsadministratör till Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Googles dokumentation om planen för att ta enhetsadministratörs-API:et ur drift](https://developers.google.com/android/work/device-admin-deprecation)

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

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>Ändringsplan: Nya inställningar för Windows-uppdateringar i Intune <!-- 4464404 -->
Från och med augustiversionen till Intune-tjänsten eller 1908 lägger vi till nya ”Inställningar för tidsgräns” som du kan konfigurera i stället för inställningarna ”Tillåt att användaren startar om (interaktiv omstart)”. Vi planerar att inaktivera inställningarna för interaktiv omstart i användargränssnittet i 1909 eller septemberuppdateringen och sedan ta bort dem från konsolen i slutet av oktober. 

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Om du hanterar Windows 10-enheter i din miljö: 
- Med Intune-uppdateringen i augusti eller 1908 visas nya inställningar för tidsgränser i konsolen utöver de gamla inställningarna för att starta om datorn.
- När båda dessa gamla och nya inställningar har konfigurerats åsidosätter inställningarna för tidsgräns inställningen för att starta om datorn.
- Inställningarna för tidsgräns kommer att ersätta alternativet ”Tillåt att användaren startar om (interaktiv omstart)” på konsolen i 1910-uppdateringen.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Börja använda inställningarna för tidsgräns i 1908 genom att konfigurera dem med önskade värden. När du har det på plats kan du ställa in inställningen för interaktiv omstart till ”Inte konfigurerad” för att förbereda inför att dessa tas bort från konsolen i oktober.

Uppdatera din dokumentation och eventuella automatiserade skript om det behövs. 

Vi håller dig uppdaterad och publicerar en påminnelse i meddelandecentret innan vi tar bort inställningarna för den interaktiva omstarten.

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>Ändringsplan: Intune App SDK och appskyddsprinciper för Android kommer att stödja Android 5.0 och senare i oktober <!--4911065 -->
Intune kommer att stödja Android 5.x (Lollipop) och högre i oktober. Uppdatera alla omslutna appar med den senaste Intune App SDK:n och uppdatera dina enheter.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Om du inte använder eller planerar att använda antingen SDK eller appen för Android påverkar den här ändringen inte dig. Om du använder Intune App SDK måste du uppdatera till den senaste versionen och även uppdatera dina enheter till Android 5.x och högre. Om du inte uppdaterar kommer appar inte ta emot uppdateringar och kvaliteten på användningsupplevelsen minskar över tid. 

Nedan hittar du en lista över vanliga enheter som har registrerats i Intune och som kör Android version 4.x. Om du har någon av dessa enheter bör du vidta lämpliga åtgärder för att se till att enheten stöder Android version 5.0 eller högre eller att den ersätts med en enhet som stöder Android version 5.0 eller högre. Den här listan är inte uttömmande för alla enheter som kan behöva utvärderas:
- Samsung SM-T561  
- Samsung SM-T365 
- Samsung GT-I9195 
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Omslut dina appar med den senaste Intune App SDK:n. Du kan också ställa in inställningen för villkorsstyrd start ”Kräv lägsta operativsystemversion (Endast varning)” för att meddela slutanvändare med personliga enheter om att uppgradera dem.


### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Intune-ändringsplan: närmar sig slutet på support för Windows 7 <!-- 3042987 -->
Som vi meddelande i MC148476 förra september 2018 och återigen i MC176794 i mars 2019, tar det utökade stödet för Windows 7 slut den 14 januari 2020. Vid detta tillfälle kommer Intune att dra tillbaka stöd för enheter som kör Windows 7, så vi kan fokusera vår investering på att stödja nyare tekniker och tillhandahålla nya slutanvändarupplevelser. Efter det datumet kommer teknisk hjälp och automatiska uppdateringar som skyddar din Windows 7-dator inte längre vara tillgängliga via Intune. Microsoft rekommenderar starkt att du flyttar till Windows 10 före januari 2020 för att undvika ett scenario där du behöver tjänster eller support som inte längre är tillgänglig. Läs mer om Windows Support Lifecycle [ här](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Du får det här meddelandet eftersom du för närvarande hanterar Windows 7-datorer med hjälp av den äldre Intune-programagenten för PC. Med mindre än ett år kvar före slutet av den utökade supporten för Windows 7 uppmuntrar vi starkt att din organisation börjar uppgradera till Windows 10 så snart som möjligt. PC-hanteringsfunktionerna är inbyggda direkt i operativsystemet Windows 10 och du behöver inte längre installera en klientagent, såsom exempelvis Intune-klientprogrammet för Windows 7. Från och med Windows 8.1 använder Microsoft MDM-arkitekturen (Mobile Device Management) för att etablera, konfigurera, uppdatera och hantera Windows-datorer. När du har konfigurerat Intune kan du förenkla Windows-registreringen genom att [registrera Windows 10-datorer till Intune](..\windows-enroll.md) via MDM-kanalen. Vi rekommenderar att du använder den här ”agentlösa” MDM-hanteringslösningen för att hantera dina Windows 10-datorer.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Vi uppmuntrar din organisation att omedelbart överväga den här åtgärdsplanen:

- Planera och uppgradera Windows 7-flottan till Windows 10 före 14 januari 2020.
- Utforska [Distributionsstöd för Windows 10](https://docs.microsoft.com/windows/deployment/) om du vill veta mer om hur du uppgraderar din befintliga flotta av Windows 7-datorer till Windows 10.
- Granska erbjudandet [Skrivbordsappen Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) via FastTrack som hjälper dig med Microsofts löfte om programkompatibilitet.
- Övergång av befintliga äldre klienthanterade enheter med Intune-program till Microsofts rekommenderade lösning för att hantera Windows 10 med MDM-hantering. Registrera alla nya Windows 10-datorer med MDM-hantering för Intune i Azure Portal.
- Mer information finns i [blogginlägget här](https://aka.ms/Windows7_Intune).
