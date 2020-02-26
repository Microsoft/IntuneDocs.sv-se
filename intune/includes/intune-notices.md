---
title: inkludera fil
description: inkludera fil
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 373aeea9ab4fcbd075ac2ab18f205f3ddd191a39
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609289"
---
Dessa meddelanden innehåller viktig information som kan hjälpa dig att förbereda dig för framtida ändringar och funktioner i Intune.

### <a name="microsoft-intune-support-for-windows-10-mobile-ending--3544938--"></a>Microsoft Intunes support för Windows 10 Mobile upphör<!--3544938-->
Microsofts mainstream-support för Windows 10 Mobile upphörde i december 2019. Som vi har nämnt i den här supportinstruktionen kommer Windows 10 Mobile-användare inte längre att kunna ta emot nya säkerhetsuppdateringar, snabbkorrigeringar som inte är av säkerhetstyp, kostnadsfria supportalternativ eller onlineuppdateringar av tekniskt innehåll från Microsoft. Microsoft Intune kommer nu även att upphöra med all support för både företagsportalen för Windows 10 Mobile-appen och Windows 10 Mobile-operativsystemet den 11 maj 2020.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Om du har Windows 10 Mobile-enheter distribuerade i din organisation, kan du mellan nu och den 11 maj 2020 registrera nya enheter, lägga till eller ta bort principer och appar eller uppdatera eventuella hanteringsinställningar. Efter den 11 maj kommer vi att stoppa nya registreringar och slutligen ta bort hanteringen av Windows 10 Mobile från Intune-användargränssnittet. Enheter kommer inte längre att checka in till Intune-tjänsten och vi kommer att ta bort enhets- och principdata.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du kan kontrollera din Intune-rapportering för att se vilka enheter eller användare som kan påverkas. Gå till **Enheter** > **Alla enheter** och filtrera efter operativsystem. Du kan lägga till fler kolumner för att hjälpa till att identifiera vilka i din organisation som har enheter som kör Windows 10 Mobile. Begär att dina slutanvändare uppgraderar sina enheter eller slutar att använda enheterna för företagsåtkomst.



### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>Planera för förändring: Ändring av upplevelse vid registrering av dedikerade Android Enterprise-enheter i Intune<!--6114580-->
I novemberversionen som vi delade lade vi till stöd för distribution av SCEP-certifikat till dedikerade Android Enterprise-enheter för att möjliggöra certifikatbaserad åtkomst till Wi-Fi-profiler. Den här ändringen involverade några mindre registreringsflödesändringar för Android Enterprise-dedikerade enheter. I den kommande mars-tjänstuppdateringen eller 2003 finns det ytterligare ändringar som vi vill att du ska känna till.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Om du hanterar dedikerade Android Enterprise-enheter i din miljö kommer du att börja se några ändringar i mars.
- För befintliga Android-dedikerade enheter som registrerats före den 22 november 2019 eller tjänstuppdateringen för 1911: De här enheterna har Microsoft Intune-appen installerad. När serverdelsändringarna införs i Intune-tjänsten i mars, börjar SCEP-certifikaten som har distribuerats till enheter och som har associerats med Wi-Fi-profiler att tillämpas.
- För enheter som har registrerats efter den 22 november 2019 och innan denna ändring införs i mars: De här enheterna har Microsoft Intune-appen installerad. SCEP-certifikat som har distribuerats till enheter och som har associerats med Wi-Fi-profiler fortsätter att tillämpas.
- För registrering av nya Android Enterprise-dedikerade enheter efter att ändringen har införts i mars: Slutanvändarna ser en annan uppsättning steg på enheterna under registreringen. Registreringen startar fortfarande på samma sätt som i dag (med QR, NFC, Zero-Touch eller enhetsidentifierare), men det kommer inte att finnas något obligatoriskt appinstallationssteg. I stället installeras Microsoft Intune-appen automatiskt på enheter. Användarna behöver dessutom inte trycka på "Aktivera Intune-agent" under flödet. SCEP-certifikat som är associerade till WiFi-profiler kan distribueras till dessa enheter.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du kan uppdatera vägledningen för slutanvändarna och informera supportavdelningen om den här ändringen. Vi kommer att uppdatera sidan Nyheter och meddela dig via meddelandecentret när ändringen börjar införas.

#### <a name="additional-information"></a>Ytterligare information
[Stöd för SCEP-certifikat i Android Enterprise-dedikerade enheter](https://aka.ms/Dedicated_devices_enrollment)

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Uppdaterad supportinstruktion för mobilappen "Adobe Acrobat Reader för Intune"<!--5746776-->
I MC188653 i slutet på augusti meddelade vi att Adobe Acrobat Reader för Intune-mobilappen når slutet på sin livslängd den 1 december 2019 och att Adobe planerar att stödja Intunes programskyddsprinciper i sin huvudsakliga app i Acrobat Reader. Sedan dess har vi fått feedback från kunder om att de behövde mer tid för att fortsätta att låta IT-administratörerna skapa mål och slutanvändare börja använda Adobe Acrobat Reader för Intune. Med tanke på den stora användningen av Adobe Acrobat Reader för Intune på slutanvändarnas enheter och dess betydelse i företagsscenarier vill vi se till att alla erfarenheter uppfyller din organisations behov av skydd av appar. 

Även om vi fortfarande rekommenderar att du använder den allmänna Acrobat Reader-mobilappen för dina principer eftersom Acrobat Reader-mobilappen har stöd för skyddsprinciper för appar och har integrerat Intune SDK, fortsätter vi att stödja Adobe Acrobat Reader för Intune-appen till och med den 31 mars 2020. 

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Du får det här meddelandet eftersom rapporten visar att en eller flera principer i din organisation är riktade mot Adobe Acrobat Reader för Intune-programmet och/eller att du har fått vårt föregående meddelande om att appen har nått slutet på sin livslängd. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Meddela slutanvändare och supportavdelningen om den här ändringen. Du kan använda funktionen [Supportinformation för företagsportalen](../apps/company-portal-app.md#support-information) för att upprätta en kanal för Intune-relaterade frågor.

#### <a name="additional-information"></a>Ytterligare information
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Vidta åtgärd: Använd Microsoft Edge för att skydda din Intune-webbläsarupplevelse<!--5728447-->
Som vi har berättat under det senaste året stöder Microsoft Edge för mobil samma uppsättning hanteringsfunktioner som Managed Browser, samtidigt som du får en mycket bättre slutanvändarupplevelse. För att bereda vägen för Microsoft Edges robusta upplevelser kommer vi att dra tillbaka Intune Managed Browser. Från och med den 27 januari 2020 kommer Intune inte längre att stödja Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig? 
Från den 1 februari 2020 är Intune Managed Browser inte längre tillgänglig i Google Play Butik eller iOS App Store. Vid den här tidpunkten kan du fortfarande ange nya appskyddsprinciper i Intune Managed Browser som mål, men nya användare kommer inte att kunna hämta Intune Managed Browser-appen. Dessutom kommer nya webbklipp i iOS som flyttas ned till en MDM-registrerad enhet att öppnas i Microsoft Edge i stället för i Intune Managed Browser.  

Den 31 mars 2020 tas Intune Managed Browser bort från Azure-konsolen. Det innebär att du inte längre kommer att kunna skapa nya principer för Intune Managed Browser. Om du har befintliga Intune Managed Browser-principer på plats kommer de inte att påverkas. Intune Managed Browser visas i konsolen som en LOB-app utan ikon och befintliga policyer visas fortfarande som mål för appen. Vid den här tidpunkten kommer vi också att ta bort alternativet för att omdirigera webbinnehåll till Intune Managed Browser i dataskyddsavsnittet för appskyddsprinciper.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen? 
För att säkerställa en smidig övergång från Intune Managed Browser till Microsoft Edge, rekommenderar vi att du utför följande steg proaktivt: 

1. Ange Microsoft Edge för iOS och Android som mål med appskyddsprincip (kallas även MAM) och appkonfigurationsinställningar. Du kan återanvända dina Intune Managed Browser-principer för Microsoft Edge genom att också ange dessa befintliga principer som mål för Microsoft Edge.  
2. Se till att alla MAM-skyddade appar i din miljö har appskyddsprincipsinställningen "Begränsa överföring av webbinnehåll till andra appar" inställd på "Principhanterade webbläsare". 
3. Ange alla MAM-skyddade med den hanterade appkonfigurationsinställningen "com.microsoft.intune.useEdge" inställd som sant som mål. Från och med nästa månad med lanseringen av 1911, kommer du att kunna utföra steg 2 och 3 genom att helt enkelt konfigurera inställningen "Begränsa överföring av webbinnehåll till andra appar" så att "Microsoft Edge" är valt i dataskyddsavsnittet i appskyddsprinciperna. 

Stöd för webbklipp i iOS och Android kommer. När det här stödet lanseras måste du rikta om befintliga webbklipp så att de öppnas i Microsoft Edge i stället för i Managed Browser. 

#### <a name="additional-information"></a>Ytterligare information
Läs våra dokument om att [använda Microsoft Edge med policyer för appsäkerhet](../apps/manage-microsoft-edge.md) om du vill veta mer, eller läs våra [blogginlägg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


### <a name="end-of-support-for-legacy-pc-management"></a>Stöd för hantering av äldre datorer upphör

Stöd för hantering av äldre datorer upphör den 15 oktober 2020. Uppgradera dina enheter till Windows 10 och registrera dem igen som MDM-enheter (hanterade mobila enheter) så att de fortsätter att hanteras av Intune.

[Läs mer](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator--5857738--"></a>Minskat stöd för Android-enhetsadministratör<!--5857738-->
Android-enhetsadministratören (kallas ibland för ”äldre” Android-hantering och lanserades med Android 2.2) är ett sätt att hantera Android-enheter. Det finns dock en bättre hanteringsfunktion med [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (lanseras med Android 5.0). För att kunna flytta till en modern, mer omfattande och säkrare enhetshantering,minskar Google stödet för enhetsadministration i nya versioner av Android.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
På grund av dessa ändringar av Google kommer Intune-användare att påverkas på följande sätt:  
- Intune kommer bara att kunna erbjuda fullt stöd för enhetsadministratörshanterade Android-enheter som kör Android 10 och senare till och med andra kvartalet 2020. Enheter med Android 10 eller senare som hanteras av enhetsadministratörer efter denna tidpunkt kommer inte längre att kunna hanteras fullt ut. Det innebär exempelvis att berörda enheter inte får de nya lösenordskraven.
    - Samsung KNOX-enheter kommer inte att påverkas av denna tidsram, eftersom utökad support tillhandahålls via Intunes integrering med KNOX-plattformen. Detta ger dig mer tid att planera övergången från enhetsadministratörernas hantering.    
- Android-enheter som hanteras av en enhetsadministratör som blir kvar på tidigare versioner av Android än Android 10 påverkas inte och kan fortfarande hanteras av en enhetsadministratör.    
- För alla enheter med Android 10 och senare har Google begränsat möjligheten för hanteringsagenter för enhetsadministratören, t.ex. företagsportalen, att komma åt information om enhetsidentifierare. Den här begränsningen påverkar följande Intune-funktioner när enheten uppdateras till Android 10 eller senare:  
    - Nätverksåtkomstkontroll för VPN fungerar inte längre.   
    - Om enheter identifieras som företagsägda med IMEI eller serienummer markeras de inte automatiskt som företagsägda.  
    - IMEI och serienumret kommer inte längre att vara synligt för IT-administratörer i Intune. 
        > [!NOTE]
        > Detta påverkar endast enheter som hanteras av enhetsadministratören på Android 10 och senare och påverkar inte enheter som hanteras som Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
För att undvika den minskade funktionaliteten i tredje kvartalet 2020, rekommenderar vi följande:
- Publicera inte nya enheter för hantering av enhetsadministratören.
- Om en enhet väntar på en Android 10-uppdatering kan du migrera den från enhetsadministratörshantering till Android Enterprise-hantering och/eller appskyddsprinciper.

#### <a name="additional-information"></a>Ytterligare information
- [Googles vägledning för migrering från enhetsadministratören till Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Googles dokumentation om tillbakadragningen av API:et för enhetsadministratören](https://developers.google.com/android/work/device-admin-deprecation)



