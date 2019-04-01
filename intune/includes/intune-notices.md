---
ms.openlocfilehash: dc86f2c22410236368753acd4dd3b66698037241
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57736851"
---

Dessa meddelanden innehåller viktig information som kan hjälpa dig att förbereda för framtida ändringar i Intune och funktioner. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Ändra i arbetsflöde för registrering med Intune-Företagsportalen på företagets iOS-enheter autentiseras med Installationsassistenten <!-- 1927359 -->
Det finns en förändring i arbetsflödet för registrering av iOS-enheter via någon av Apples företagets registreringsmetoder för enheter – Apple Configurator, Apples Business Manager, Apple School Manager eller Apple Device Enrollment Program (DEP) när du använder installationsprogrammet Installationsassistent för autentisering. Den här ändringen gäller endast för enheter som registrerats med användartillhörighet.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
När den här ändringen lanseras i ~~april~~ kommer profiler för registrering i Intune i Azure-portalen att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Det blir ett förbättrat arbetsflöde för att registrera iOS-enheter med de metoder som anges ovan. Obs!

- När registrera nya enheter och autentisering med Installationsassistenten, du kommer att kunna välja om du vill distribuera automatiskt i appen företagsportal. Slutanvändarna kommer inte längre visas skärmen ”Identifiera enhet” och ”bekräfta din enhet”-skärmen i flödet för registrering.  
- Du måste vidta åtgärder om du vill aktivera villkorlig åtkomst på enheter som redan har registrerats via Installationsassistenten genom någon av Apples metoder för registrering av företagsenheter. Du måste konfigurera en princip för appkonfiguration med en specifik xml till push-Företagsportalen till dessa enheter. Anvisningar för att göra detta finns i blogginlägget på länken ytterligare Information. Om du väljer att skicka Företagsportalen på detta sätt, visas inte längre slutanvändare skärmen ”Identifiera enhet” och ”bekräfta din enhet”-skärmen i flödet för registrering. 
- När den här ändringen distribueras, om du inte har distribuerat Företagsportalen med app-Konfigurationsprofil som nämns ovan och om slutanvändarna ladda ned företagsportalappen från App store, kommer de kan logga in, men de kommer att får ett felmeddelande. De kommer inte att kunna använda appen för villkorlig åtkomst. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Om du tänker använda det ändrade arbetsflödet, kommer du vill uppdatera din vägledning för slutanvändare för att visa att:

- Slutanvändarna kommer inte längre visas två skärmar som nämns ovan i flödet för registrering. 
- De måste logga in på företagsportalen när det distribueras automatiskt och inte ladda ned det från app store. 

Du kan välja att skapa en appkonfigurationsprincip nu om det behövs, som förberedelse inför den här ändringen. När det nya arbetsflödet rullar, visas uppdaterade registreringsprofiler i konsolen. Vi också informerar dig om den här distributionen via meddelandecenter. Därefter kan behöver du vidta åtgärder så att användarna kan registrera via DEP genom att autentisera med Installationsassistenten och du kan använda Företagsportalen för villkorlig åtkomst.

Se vår support-blogginlägget på länken ytterligare Information för mer information om den här ändringen.

#### <a name="additional-information"></a>Ytterligare information 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="company-portal-changes-for-ios-122-enrollment-in-intune"></a>Portalen företagsändringar för iOS 12.2 registrering i Intune
Vi meddelande i MC172534 att Apple har tillkännagivit några ändringar relaterade till iOS-enheters registrering i MDM-tjänster. Ändringen visas sannolikt i denna version av iOS som kommer i mars 2019 samt alla framtida iOS-versioner. Vi gör vissa uppdateringar i Företagsportalen så att ändringar av Apple. 
 
#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Om dina slutanvändare uppgraderar sina enheter till iOS 12.2 och ovan, vet du att det finns en ändrade arbetsflödet och de måste vidta ytterligare åtgärder för att slutföra en registrering i Intune. När mars-uppdatering till Intune är här vad de ska göra följande:  

- Börja registreringen i företagsportalappen för att ladda ned en hanteringsprofil
- Gå till Inställningar > Allmänt > profiler och leta efter ett meddelande i rött märket
- Välj rätt profil och klicka här för att installera
- Gå tillbaka till Företagsportalen för att slutföra en registrering

Klicka på mer detaljerad information om registrering flödet.

Om de är avregistreras och behöver en ny registrering, enheter som redan är registrerade och uppgradera till iOS 12.2 och ovan bör inte påverkas. Registreringsprocessen på enheter som kör iOS 12.1 eller tidigare ändras inte med den här nya versionen från Apple. Enheter som registrerats via en eller Apples metoder för företagets registrering (Program för Enhetsregistrering, Apple School Manager eller Apple Business Manager) påverkas inte.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du bör planera en uppgradering av dokumentationen och vägledningen för slutanvändare. Du kanske också vill meddela supportavdelningen om ändringarna. Vi håller dig informerad via vår sidan med nyheter om den här ändringen går live. 

Om du vill dra nytta av företagsportal-ändringar som Vi presenterar be slutanvändarna att uppdatera enheten till den nya versionen för iOS efter mars-uppdatering till Intune service när Företagsportalen appversion 3.9.0. släpps.

Klicka på ytterligare Information för ett blogginlägg för support med förhandsversion skärmdumpar av Företagsportalen ändringarna.

Ytterligare information [https://aka.ms/CP_changes_iOS12](https://aka.ms/CP_changes_iOS12)

### <a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>Planera för förändring: ändras arbetsflödet för registrering av iOS 12 i Intune
Apple har tillkännagivit några ändringar relaterade till iOS-enheters registrering i MDM-tjänster. Ändringen kommer sannolikt i iOS-utgåvan som släpps på våren 2019 och alla framtida iOS-versioner.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Om dina slutanvändare uppgraderar sina enheter till den här nya versionen av iOS 12 under våren bör du känna till att arbetsflödet ändras och att de behöver vidta ytterligare åtgärder för att slutföra registreringen till Intune. När Apple introducerar dessa ändringar, måste slutanvändare:

- Börja registreringen i företagsportalappen för att ladda ned en hanteringsprofil
- Gå till Inställningar > Allmänt > profiler
- Välj rätt profil och klicka här för att installera
- Gå tillbaka till Företagsportalen för att slutföra en registrering 

Såvida de inte har avregistrerats och behöver en ny registrering borde inte enheter som redan har registrerats och uppgraderats till den nya iOS-versionen påverkas.

Registreringsprocessen på enheter som kör iOS 12.1 eller tidigare ändras inte med den här nya versionen från Apple.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du bör planera en uppgradering av dokumentationen och vägledningen för slutanvändare. Du kanske också vill meddela supportavdelningen om ändringarna. Vi informerar dig via Meddelandecenter och sidan Nyheter när den här ändringen börjar gälla.

#### <a name="additional-information"></a>Ytterligare information
[Stöd för blogginlägget med skärmbilder och video med det förväntade flödet](https://aka.ms/iOS_enrollment_changes).

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Ändringsplan: Uppdatering av användarupplevelsen för appen Intune-företagsportal för iOS
Vi är glada att kunna meddela att Intune snart lanserar en större uppdatering av användarupplevelsen i appen Företagsportal för iOS. Uppdateringen omfattar en visuell omarbetning av startsidan med avancerade filter och snabbare åtkomst till appar och böcker.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Nuvarande iOS-funktioner i Företagsportalen bevaras, men den här uppdateringen omfattar följande:
- En startsida med typiskt iOS-utseende 
- Filtreringsfunktioner i innehållslistor och sökning, bland annat möjligheten att filtrera efter innehållstyp (appar eller e-böcker) och tillgänglighet (enhetshantering obligatorisk eller tillgängligt utan registrering)
- Möjligheten att söka i e-böcker
- Sökhistorik för appar och e-böcker

Om du deltar i Apple TestFlight-programmet kommer du att meddelas om förhandsversionen av Intunes uppdaterade företagsportalapp för iOS när den blir tillgänglig. Om du inte deltar i Apple TestFlight-programmet är det inte för sent att registrera dig. Om du registrerar dig kan du använda den uppdaterade appen Företagsportal innan den är tillgänglig för dina slutanvändare. Du kommer också kan ge feedback direkt till Intune-teamet.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du behöver inte vidta några åtgärder. De här ändringarna lanseras i en kommande version av appen iOS FP. 

#### <a name="additional-information"></a>Ytterligare information
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="reminder-removal-of-existing-exchange-online-to-intune-connectors----3105122---"></a>Påminnelse: Borttagning av befintliga Exchange Online till Intune-kopplingar <!-- 3105122 -->
I MC165575 meddelade vi att vi skulle tar bort Exchange Online till Intune Service to Service connector-funktioner i en kommande uppdatering. Med den februari uppdateringen till Intune-tjänsten, kommer vi att inaktivera knappen för att konfigurera nya anslutningar. Vi planerar att ta bort alla befintliga Exchange Online till Intune-kopplingar i mars 2019.
 
#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Du får det här meddelandet eftersom våra uppgifter visar att du använder anslutningsfunktionen ”Service to Service” i din miljö. ”Service to Service”-anslutningsprogrammet stöder Intune-hantering av enheter med endast Exchange Active Sync för Exchange Online, och stöder inte lokal infrastruktur. På grund av det sätt som anslutningsprogrammet visas på konsolen verkar det vara nödvändigt för villkorlig åtkomst (CA), men i verkligheten behövs det inte för CA. Du kanske har använt den här anslutningen för att förstå användningen av Exchange Online innan du tillämpar villkorlig åtkomst. Den här informationen tillhandahålls redan av Microsoft 365 Admin Center. Här hittar du tillhandahåller användningsrapporter för Exchange Online, inklusive appen skriver som används för mellan 7 och 180 dagar. Mer information finns i [Office 365-rapporter i Administrationscenter - användningen för e-post-appar](https://docs.microsoft.com/office365/admin/activity-reports/email-apps-usage?view=o365-worldwide).  
 
Om du använder det här anslutningsprogrammet i din miljö kommer du inte kunna övervaka eller rensa enheter med endast Exchange Active Sync i Intune efter att anslutningsprogram har inaktiverats i februari. Det finns ingen förväntad påverkan för slutanvändare under den här ändringen.
 
#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Om du har anslutningsprogrammet ”Service to Service” konfigurerat och enheter med endast Exchange Active Sync måste du byta till andra hanteringsmetoder för dina enheter. Du kan välja mellan följande alternativ:

- Registrera enheter i hantering av mobilenheter (MDM) 
- Använd Intunes appskyddsprinciper för att hantera dina enheter 
- Använd Exchange-kontrollerna enligt beskrivningen i dokumentationen [här](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online) 

#### <a name="additional-information"></a>Ytterligare information  
https://docs.microsoft.com/intune/exchange-service-connector-configure




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
