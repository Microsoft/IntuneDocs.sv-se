---
title: inkludera fil
description: inkludera fil
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 7373ca24c1ae1f439096d9bedcb8e81979c95586
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74828783"
---
Dessa meddelanden innehåller viktig information som kan hjälpa dig att förbereda dig för framtida ändringar och funktioner i Intune.

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Uppdaterad supportinstruktion för mobilappen "Adobe Acrobat Reader för Intune"<!--5746776-->
I MC188653 i slutet på augusti meddelade vi att Adobe Acrobat Reader för Intune-mobilappen når slutet på sin livslängd den 1 december 2019 och att Adobe planerar att stödja Intunes programskyddsprinciper i sin huvudsakliga app i Acrobat Reader. Sedan dess har vi fått feedback från kunder om att de behövde mer tid för att fortsätta att låta IT-administratörerna skapa mål och slutanvändare börja använda Adobe Acrobat Reader för Intune. Med tanke på den stora användningen av Adobe Acrobat Reader för Intune på slutanvändarnas enheter och dess betydelse i företagsscenarier vill vi se till att alla erfarenheter uppfyller din organisations behov av skydd av appar. 

Även om vi fortfarande rekommenderar att du använder den allmänna Acrobat Reader-mobilappen för dina principer eftersom Acrobat Reader-mobilappen har stöd för skyddsprinciper för appar och har integrerat Intune SDK, fortsätter vi att stödja Adobe Acrobat Reader för Intune-appen till och med den 31 mars 2020. 

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Du får det här meddelandet eftersom rapporten visar att en eller flera principer i din organisation är riktade mot Adobe Acrobat Reader för Intune-programmet och/eller att du har fått vårt föregående meddelande om att appen har nått slutet på sin livslängd. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Meddela slutanvändare och supportavdelningen om den här ändringen. Du kan använda funktionen [Supportinformation för företagsportalen](../apps/company-portal-app.md#support-information) för att upprätta en kanal för Intune-relaterade frågor.

#### <a name="additional-information"></a>Ytterligare information
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Support för Windows Phone 8.1 har upphört<!--3544909-->
Microsofts mainstream-support för Windows Phone 8.1 upphörde under juli 2017 och utökad support upphörde under juni 2019. Företagsportalappen för Windows Phone 8.1 har varit i berett läge sedan oktober 2017. Support för Windows Phone 8.1 på Microsoft Intune upphör den 20 februari 2020.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Efter 20 februari 2020 får de här enheterna inga nya säkerhetsuppdateringar och du kommer inte att kunna registrera några nya enheter. Befintliga Windows Phone 8.1-enheter förblir registrerade (policy, appar, rapportering), men observera att felsökning av befintlig registrering inte kommer att stödas efter detta datum eftersom support för plattformen redan har upphört från många komponenter, till exempel certifikat från tredje part. Kompatibilitetstestning mellan Intune och Windows Phone 8.1 kommer att stoppas.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du kan kontrollera din Intune-rapportering för att se vilka enheter eller användare som kan påverkas. Gå till Enheter > Alla enheter och filtrera efter operativsystem. Du kan lägga till fler kolumner för att hjälpa till att identifiera vilka i din organisation som har enheter som kör Windows Phone 8.1. Uppmana dina slutanvändare att uppgradera sina enheter till en operativsystemversion som stöds.

### <a name="update-your-intune-outlook-app-protection-policies-app--2576686--"></a>Uppdatera dina appskyddsprinciper (APP) för Outlook i Intune<!--2576686-->
Om du tagit emot koden MC195618 i Meddelandecenter kan du behöva vidta åtgärder. Som tidigare angetts i produktvägledningen för Microsoft 365:s funktions-ID:n 56325 och 56326 kommer Intune och Outlook för iOS och Android att distribuera stöd för begränsning av känsliga data i e-postmeddelanden och kalenderpåminnelser. Som ett resultat av dessa förbättringar kommer Outlook för iOS och Android att ta bort stödet för flera appkonfigurationsnycklar för dataskydd som du för närvarande använder för att hantera meddelanden.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
De nya funktionerna har ännu inte sjösatts, men när de väl är i bruk kommer följande appkonfigurationsnycklar att sluta fungera i Outlook för iOS och Android:
- com.microsoft.outlook.Mail.NotificationsEnabled
- com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed
- com.microsoft.outlook.Calendar.NotificationsEnabled
- com.microsoft.outlook.Calendar.NotificationsEnabled.UserChangeAllowed

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Vi rekommenderar att du konfigurerar dataskyddsinställningen för meddelanden om organisationsdata i Intunes appskyddsprincip och anger värdet ”Blockera organisationsdata” inför den nya funktionen. Från och med den 16 december 2019 aktiveras dataskyddsinställningen för meddelanden om organisationsdata i Outlook för iOS och Android och har inte längre stöd för de tidigare nycklarna. Genom att konfigurera den nya inställningen säkerställer du att känsliga data inte läcker ut när stödet för ovanstående konfigurationsnycklar försvinner. Om du ställer in dataskyddsinställningen för meddelanden om organisationsdata på ”Blockera organisationsdata” kan Outlook kan dessutom tillhandahålla ytterligare granularitet med hjälp av ytterligare en appkonfigurationsinställning för kalenderaviseringar. Kombinationen av appskyddsprincipinställningen och konfigurationsinställningen appen begränsar användningen av känslig information i e-postmeddelanden, samtidigt som känslig information kan visas i kalenderaviseringar så att användarna snabbt kan få en översikt över mötena genom att titta på meddelandet eller i meddelandecentret.

#### <a name="additional-information"></a>Ytterligare information
Mer information om APP-inställningar och Outlook-inställningar finns i:
- [Inställningar för appskyddsprinciper, Android](../apps/app-protection-policy-settings-android.md)
- [Inställningar för appskyddsprinciper, iOS](../apps/app-protection-policy-settings-ios.md)
- [Distribuera appkonfigurationsinställningar för Outlook för iOS och Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)


### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Ändringsplan för Intune: Stödet för företagsportalen för Windows 10, version 1703, upphör<!--5026679-->
Windows 10, version 1703 (även kallad Windows 10, RS2) tas ur drift den 8 oktober 2019 för företags- och EDU-versioner. Intune avslutar stödet för motsvarande företagsportalsapp för RS2/RS1 med början den 26 december 2019.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Framöver kommer du inte att se några nya funktioner i den specifika versionen av företagsportalsappen, men vi fortsätter att stödja den här versionen av företagsportalsappen till och med den 26 december 2019 och kommer bland annat att fortsätta att tillhandahålla säkerhetsuppdateringar till den vid behov. Eftersom Windows 10, version 1703, inte kommer att få några säkerhetsuppdateringar när det har tagits ur drift, rekommenderar vi starkt att du uppdaterar dina Windows-enheter till en nyare Windows-version och ser till att du använder den senaste företagsportalsappen så att du kan fortsätta att få nya funktioner och ytterligare funktionalitet.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
De steg som du ska vidta beror på hur din miljö är konfigurerad. I allmänhet bör du dock identifiera vilka enheter som har den äldre versionen av operativsystemet och/eller företagsportalen och uppdatera dessa. För att konfigurera dina Windows 10-uppdateringsringar loggar du in på Intune-> Programuppdateringar – Windows 10-uppdateringsringar. Den senaste versionen av företagsportalen är version 10.3.5601.0. Be användarna att ladda ned den från Microsoft Store för att hålla sig uppdaterade med framtida versioner. Du kan också använda Intune för att installera den senaste på dina Windows-enheter via [Microsoft Store för företag](https://docs.microsoft.com/intune/windows-store-for-business).

#### <a name="additional-information"></a>Ytterligare information
[Lägga till appen Företagsportal för Windows 10 manuellt med Microsoft Intune](https://docs.microsoft.com/intune/store-apps-company-portal-app)


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

Stöd för webbklipp i iOS och Android kommer. När det här stödet släpps måste du ange befintliga webbklipp som mål på nytt för att säkerställa att de öppnas i Microsoft Edge i stället för i Managed Browser. 

#### <a name="additional-information"></a>Ytterligare information
Besök våra dokument om att [använda Microsoft Edge med appskyddsprinciper](../apps/manage-microsoft-edge.md) för mer information eller läs vidare i våra [supportbloggsinlägg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).

### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>Planera för förändring: Uppdaterad upplevelse vid registrering av dedikerade Android Enterprise-enheter i Intune<!--5198878-->
I novemberversionen, eller version 1911, av Intune har vi lagt till stöd för distribution av SCEP-enhetscertifikat till dedikerade Android Enterprise-enheter för att möjliggöra certifikatbaserad åtkomst till Wi-Fi-profiler. Den här ändringen omfattar även vissa mindre ändringar i flödet när du registrerar dedikerade Android Enterprise-enheter.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Om du hanterar dedikerade Android Enterprise-enheter i din miljö kommer du att börja se några ändringar i november.

- För nya registreringar av dedikerade Android Enterprise-enheter: Slutanvändarna ser en annan uppsättning steg på enheterna under registreringen. Registreringen startar fortfarande på samma sätt som i dag (med QR, NFC, Zero-Touch eller enhetsidentifierare), men från och med novemberversionen finns det ett obligatoriskt appinstallationssteg.
- För befintliga Android-enheter som registrerats som dedikerade enheter: Intune börjar automatiskt installera Microsoft Intune-appen på enheter från och med början av november. Du behöver inte vidta någon åtgärd. Appen laddas ned och installeras automatiskt på enheterna. 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du bör planera för att uppdatera vägledningen för slutanvändarna och informera supportavdelningen om den här ändringen. Klicka på Ytterligare information för mer information och skärmbilder. Vi uppdaterar sidan Nyheter när ändringen börjar distribueras.

#### <a name="additional-information"></a>Ytterligare information
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="end-of-support-for-legacy-pc-management"></a>Stöd för hantering av äldre datorer upphör

Stöd för hantering av äldre datorer upphör den 15 oktober 2020. Uppgradera dina enheter till Windows 10 och registrera dem igen som MDM-enheter (hanterade mobila enheter) så att de fortsätter att hanteras av Intune.

[Läs mer](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Minskat stöd för Android-enhetsadministratör 
Android-enhetsadministratören (kallas ibland för ”äldre” Android-hantering och lanserades med Android 2.2) är ett sätt att hantera Android-enheter. Det finns dock en bättre hanteringsfunktion med [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (lanseras med Android 5.0). För att kunna flytta till en modern, mer omfattande och säkrare enhetshantering,minskar Google stödet för enhetsadministration i nya versioner av Android.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
På grund av dessa ändringar av Google kommer Intune-användare att påverkas på följande sätt:  
- Intune kommer bara att kunna erbjuda fullt stöd för enhetsadministratörshanterade Android-enheter som kör Android 10 och senare till och med andra kvartalet 2020. Enheter med Android 10 eller senare som hanteras av enhetsadministratörer efter denna tidpunkt kommer inte längre att kunna hanteras fullt ut. Det innebär exempelvis att berörda enheter inte får de nya lösenordskraven.
    - Samsung KNOX-enheter kommer inte att påverkas av denna tidsram, eftersom utökad support tillhandahålls via Intunes integrering med KNOX-plattformen. Detta ger dig mer tid att planera övergången från enhetsadministratörernas hantering.    
- Android-enheter som hanteras av en enhetsadministratör som blir kvar på tidigare versioner av Android än Android 10 påverkas inte och kan fortfarande hanteras av en enhetsadministratör.    
- För alla enheter med Android 10 och senare har Google begränsat möjligheten för hanteringsagenter för enhetsadministratören, t.ex. företagsportalen, att komma åt information om enhetsidentifierare. Denna begränsning påverkar följande Intune-funktioner efter att enheten har uppdaterats till Android 10 eller senare:  
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

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Ändringsplan: Intune App SDK och appskyddsprinciper för Android kommer att stödja Android 5.0 och senare i kommande versioner <!--4911065 -->
Intune kommer att stödja Android 5.x (Lollipop) och högre i kommande versioner. Uppdatera alla omslutna appar med den senaste Intune App SDK:n och uppdatera dina enheter.

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

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Ändringsplan för Intune: Snart upphör stödet för Windows 7<!-- 3042987 -->
Som vi meddelande i MC148476 förra september 2018 och återigen i MC176794 i mars 2019, tar det utökade stödet för Windows 7 slut den 14 januari 2020. Vid detta tillfälle kommer Intune att dra tillbaka stöd för enheter som kör Windows 7, så vi kan fokusera vår investering på att stödja nyare tekniker och tillhandahålla nya slutanvändarupplevelser. Efter det datumet kommer teknisk hjälp och automatiska uppdateringar som skyddar din Windows 7-dator inte längre vara tillgängliga via Intune. Microsoft rekommenderar starkt att du flyttar till Windows 10 före januari 2020 för att undvika ett scenario där du behöver tjänster eller support som inte längre är tillgänglig. Läs mer om Windows Support Lifecycle [ här](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Du får det här meddelandet eftersom du för närvarande hanterar Windows 7-datorer med hjälp av den äldre Intune-programagenten för PC. Med mindre än ett år kvar före slutet av den utökade supporten för Windows 7 uppmuntrar vi starkt att din organisation börjar uppgradera till Windows 10 så snart som möjligt.  

PC-hanteringsfunktionerna är inbyggda direkt i operativsystemet Windows 10 och du behöver inte längre installera en klientagent, såsom exempelvis Intune-klientprogrammet för Windows 7. Från och med Windows 8.1 använder Microsoft MDM-arkitekturen (Mobile Device Management) för att etablera, konfigurera, uppdatera och hantera Windows-datorer. När du har konfigurerat Intune kan du förenkla Windows-registreringen genom att [registrera Windows 10-datorer till Intune](..\windows-enroll.md) via MDM-kanalen. Vi rekommenderar att du använder den här ”agentlösa” MDM-hanteringslösningen för att hantera dina Windows 10-datorer.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Vi uppmuntrar din organisation att omedelbart överväga den här åtgärdsplanen:

- Planera och uppgradera Windows 7-flottan till Windows 10 före 14 januari 2020.
- Utforska [Distributionsstöd för Windows 10](https://docs.microsoft.com/windows/deployment/) om du vill veta mer om hur du uppgraderar din befintliga flotta av Windows 7-datorer till Windows 10.
- [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) är en Microsoft-tjänst som hjälper dig med programkompatibilitet. Du kan utforska tjänsten via FastTrack.
- Migrera befintliga äldre klienthanterade enheter med Intune-program till Microsofts rekommenderade lösning för att hantera Windows 10 med MDM-hantering. Registrera alla nya Windows 10-datorer med MDM-hantering för Intune på Azure-portalen.

Mer information finns i [blogginlägget här](https://aka.ms/Windows7_Intune).


