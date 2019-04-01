---
title: inkludera fil
description: inkludera fil
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 073115d33f9a4f22fe3706ef15860c2a8d8a68ee
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675501"
---
Dessa meddelanden innehåller viktig information som kan hjälpa dig att förbereda för framtida ändringar i Intune och funktioner. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Ändra i arbetsflöde för registrering med Intune-Företagsportalen på företagets iOS-enheter autentiseras med Installationsassistenten <!-- 1927359 -->
Det finns en förändring i arbetsflödet för registrering av iOS-enheter via någon av Apples företagets registreringsmetoder för enheter – Apple Configurator, Apples Business Manager, Apple School Manager eller Apple Device Enrollment Program (DEP) när du använder installationsprogrammet Installationsassistent för autentisering. Den här ändringen gäller endast för enheter som registrerats med användartillhörighet.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
När den här ändringen lanseras i ~~april~~ kommer profiler för registrering i Intune i Azure-portalen att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Det blir ett förbättrat arbetsflöde för att registrera iOS-enheter med de metoder som anges ovan. 

- När registrera nya enheter och autentisering med Installationsassistenten, du kommer att kunna välja om du vill distribuera automatiskt i appen företagsportal. Slutanvändarna kommer inte längre visas skärmen ”Identifiera enhet” och ”bekräfta din enhet”-skärmen i flödet för registrering.  
- Du måste vidta åtgärder om du vill aktivera villkorlig åtkomst på enheter som redan har registrerats via Installationsassistenten genom någon av Apples metoder för registrering av företagsenheter. Du måste konfigurera en princip för appkonfiguration med en specifik xml till push-Företagsportalen till dessa enheter. Anvisningar för att göra detta finns i blogginlägget på länken ytterligare Information. Om du väljer att skicka Företagsportalen på detta sätt, visas inte längre slutanvändare skärmen ”Identifiera enhet” och ”bekräfta din enhet”-skärmen i flödet för registrering. 
- När den här ändringen distribueras, om du inte har distribuerat Företagsportalen med app-Konfigurationsprofil som nämns ovan och om slutanvändarna ladda ned företagsportalappen från App store, de kan logga in, men de kommer att får ett felmeddelande. De kommer inte att kunna använda appen för villkorlig åtkomst. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Om du tänker använda det ändrade arbetsflödet, kommer du vill uppdatera din vägledning för slutanvändare för att visa att:

- Slutanvändarna kommer inte längre visas två skärmar som nämns ovan i flödet för registrering. 
- De måste logga in på företagsportalen när det distribueras automatiskt och inte ladda ned det från app store. 

Du kan välja att skapa en appkonfigurationsprincip nu om det behövs, som förberedelse inför den här ändringen. När det nya arbetsflödet rullar, visas uppdaterade registreringsprofiler i konsolen. Vi också informerar dig om den här distributionen via meddelandecenter. Därefter kan behöver du vidta åtgärder så att användarna kan registrera via DEP genom att autentisera med Installationsassistenten och du kan använda Företagsportalen för villkorlig åtkomst.

Se vår support-blogginlägget på länken ytterligare Information för mer information om den här ändringen.

#### <a name="additional-information"></a>Ytterligare information 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Ändringsplan: Uppdatering av användarupplevelsen för appen Intune-företagsportal för iOS
Vi är glada att kunna meddela att Intune snart lanserar en större uppdatering av användarupplevelsen i appen Företagsportal för iOS. Uppdateringen omfattar en visuell omarbetning av startsidan med avancerade filter och snabbare åtkomst till appar och böcker.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Nuvarande iOS-funktioner i Företagsportalen bevaras, men den här uppdateringen omfattar följande:
- En startsida med typiskt iOS-utseende 
- Filtreringsfunktioner i innehållslistor och sökning, bland annat möjligheten att filtrera efter innehållstyp (appar eller e-böcker) och tillgänglighet (enhetshantering obligatorisk eller tillgängligt utan registrering)
- Möjligheten att söka i e-böcker
- Sökhistorik för appar och e-böcker

Om du deltar i Apple TestFlight-programmet kommer du att meddelas om förhandsversionen av Intunes uppdaterade företagsportalapp för iOS när den blir tillgänglig. Om du inte deltar i Apple TestFlight-programmet är det inte för sent att registrera dig. Om du registrerar dig kan du använda den uppdaterade appen Företagsportal innan den är tillgänglig för dina slutanvändare. Du kan även tillhandahålla feedback direkt till Intune-teamet.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du behöver inte vidta några åtgärder. De här ändringarna lanseras i en kommande version av appen iOS FP. 

#### <a name="additional-information"></a>Ytterligare information
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)

### <a name="check-your-delay-visibility-of-software-updates-setting-in-intune"></a>Kontrollera din ”fördröjning av programuppdateringar” inställningar i Intune 

Vi delas i MC171466 som vi flytta några inställningar i konsolen. Med mars-uppdatering till Intune tar vi bort ”fördröjning synligheten för programvara uppdateringar” inställningen helt från bladet iOS update-princip. Detta kommer inte att ändra hur dina schemalagda uppdateringar gäller, men det kan påverka hur länge synligheten för en uppdatering är försenad för slutanvändare. Du kan behöva vidta åtgärder innan mars är slut om du använder den här inställningen. 

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Efter tjänstuppdatering februari Intune ser du att inställningen visas både i profiler för enhetsbegränsningar i konsolen och i iOS-uppdateringsprinciper på bladet Software update. När den här ändringen visas i konsolen visas är här vad du kan behöva göra.

- För befintliga uppdateringsprinciper för iOS: Om du har anpassade konfigurerat den här inställningen till något annat än standardvärdet 30 dagar och vill att dina befintliga konfigurationer för fördröjning synlighetsinställningen om du vill fortsätta att gälla efter slutet av mars, måste du skapa en ny begränsningsprofil för iOS-enheter. Här kan måste fördröjning inställningar ha samma värden som i den befintliga iOS-uppdateringsprincipen och riktas mot samma grupper. Efter tjänstuppdatering mars kommer du inte längre att kunna redigera värden för den här inställningen i befintliga iOS-uppdateringsprinciper eftersom den inte längre visas i det här bladet. Du konfigurerar den här inställningen i de nya profilerna i stället.
  Om värdet för antal dagar som du kan fördröja synlighet matchar inte på båda platserna för anpassade konfigurerade inställningsvärden, fördröjning synlighet inställningen inte fungerar, och slutanvändarna ser uppdateringen på sina enheter när den är tillgänglig. Detta kan påverka minimal för de flesta kunder eftersom de andra inställningarna på bladet princip för programuppdateringar har alltid vidtagit företräde över den här inställningen i konsolen.
- För nya uppdateringsprinciper för iOS: Om du försöker skapa nya principer på bladet programvara uppdateringar efter tjänstuppdateringen Intune februari, visas den här inställningen nedtonade. Du ser en anteckning i konsolen omdirigeras du till konfigurationsbladet om du vill fördröja synligheten för uppdateringar.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du behöver inte vidta åtgärder om du inte använder den här inställningen eller inte vill att fördröja synligheten för programuppdateringar för dina slutanvändare.

Om du vill att fördröja visningen av uppdateringar kan du börja konfigurera inställningen i nya profiler i bladet enhetskonfiguration under Enhetsbegränsningar > Allmänt. Om du har konfigurerat i befintliga iOS-uppdateringsprinciper den här anpassade inställningen, skapa en ny motsvarande profil för enhetsbegränsningar med samma värde för ”dagar” att fördröja visningen av uppdateringar till dina användare, när februari uppdatering och innan mars distribueras. 

Du kanske vill uppdatera din IT-proffs vägledning och informera supportavdelningen.

Se vår support blogginlägget för mer Information finns mer information om hur du konfigurerar den här inställningen.

#### <a name="additional-information"></a>Ytterligare information 
[https://aka.ms/Delay_visibility_setting_iOS](https://aka.ms/Delay_visibility_setting_iOS)

### <a name="plan-for-change-upcoming-fix-for-windows-10-email-profiles-in-intune---3904031--"></a>Planera för förändring: korrigering för Windows 10 e-postprofiler i Intune <!--3904031-->
Vi uppdaterar hur Intune skriver e-post profiler för Windows 10 i April uppdatera till Intune-tjänsten för att åtgärda en bugg samt att säkerställa att din e-postprofiler fortsätter att fungera i framtida versioner av Windows 10. Det finns åtgärder som du måste utföra när den här snabbkorrigeringen har distribuerats.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Den här ändringen påverkar du om du använder Windows 10 e-postprofiler med
- Den inbyggda e-klienten i Windows 10-datorer eller
- Outlook-e-klienten på Windows 10 Mobile

Detta påverkar både Intune fristående och hybrid-Mobile Device Management (MDM)-kunder.

När den April distribueras, måste du återskapa dessa profiler i Intune-konsolen (i Configuration Manager-administratörskonsolen om du använder hybrid-MDM).

Om du inte vidta åtgärder, är här vad du ser för profiler som skapats före uppdateringen April:

- Den befintliga e-postprofiler visas i feltillstånd i Intune-konsolen eller Configuration Manager-administratörskonsolen, men användarna har fortfarande åtkomst till e-post. När en efterföljande Windows distribueras, fungerar inte de här profilerna. Slutanvändare på enheter som är riktade mot de här profilerna förlorar åtkomsten till e-post.
- Ändringar som gjorts till dessa profiler efter April inte återspeglas i målenheterna.
- Selektiv rensning fungerar inte för att ta bort de här profilerna även efter att korrigeringen lanseras i April.

Om du vidta åtgärder och skapa e-postprofiler behöver slutanvändarna gå igenom steg som är samma som när en e-postprofil har distribuerats för första gången. Sin e-post kommer att blockeras från att synkronisera tills de accepterar den uppdatering som gäller den nya profilen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du måste vidta åtgärder endast efter att korrigeringen distribueras med April uppdateringen. Vi kommer att kontakta dig via meddelandecenter när den här ändringen lanseras så du kan börja skapa dina profiler i Intune.

Om du använder Windows 10 e-postprofiler i Intune, behöver du vidta följande åtgärder:

1. Samla in befintliga konfigurationsupplevelsen för Windows 10-profilinställningar
2. Ta bort tilldelning av och/eller ta bort befintliga profiler
3. Skapa nya profiler med hjälp av de avbildade inställningarna och tilldela nya profiler till samma grupper

Du kan behöva meddela slutanvändarna och låt supportavdelningen känner till den här ändringen. Läs blogginlägget support för mer Information finns information om fel och instruktioner för att återskapa de här profilerna.

#### <a name="additional-information"></a>Ytterligare information
https://aka.ms/Win10EmailProfiles

