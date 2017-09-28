---
title: Nyheter i Microsoft Intune
titlesuffix: Azure portal
description: "Ta reda på vad som är nytt i Intune Azure-portalen"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/18/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 08a22a1fa6829807860b6278181dd638f1049770
ms.sourcegitcommit: 0d9bfd92bf5958261ed83b1f150bf207b7ba7e56
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/21/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Läs mer om varje veckas nyheter i Microsoft Intune. Du kan också läsa mer om [kommande ändringar](#whats-coming), [viktiga meddelanden](#notices) om tjänsten och information om [tidigare versioner](whats-new-archive.md).

> [!Note]
> Hybriddistributioner med Configuration Manager kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-september-11-2017"></a>Veckan då den 11 september 2017 infaller

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo----1475932---"></a>Ytterligare push-meddelanden för slutanvändare i företagsportalappen för Android Oreo <!---1475932--->

Slutanvändarna ser ytterligare meddelanden som anger när företagsportalen för Android Oreo utför bakgrundsaktiviteter, till exempel när principer hämtas från Intune-tjänsten. Detta ger bättre transparens för slutanvändarna eftersom de ser när företagsportalen utför administrativa uppgifter på deras enheter. Det här är en del av [optimeringen av företagsportalens användargränssnitt](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) för företagsportalappen för Android Oreo. 

#### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informera användarna vilken enhetsinformation som kan visas för iOS <!--739894--> 

Vi har lagt till **Typ av ägarskap** på skärmen Enhetsinformation i företagsportalappen för iOS. På så sätt kan användarna få mer information om sekretess direkt från den här sidan från Intunes slutanvändardokumentation. De kan även hitta denna information på skärmen Om. 

#### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Tillåt att slutanvändare får åtkomst till företagsportalappen för Android utan registrering <!---1169910--->

Slutanvändare behöver snart inte att registrera sina enheter för att komma åt företagsportalappen för Android. Slutanvändare i organisationer som använder principer för appskydd får inte längre uppmaningar att registrera sina enheter när de öppnar företagsportalen. Slutanvändarna kommer också att kunna installera appar från företagsportalen utan att registrera sina enheter. 


#### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Enklare formuleringar i företagsportalappen för Android <!---1396349--->  

Registreringen av företagsportalappen för Android har förenklats med ny text för att göra det enklare för slutanvändarna att registrera. Om du har anpassad registreringsdokumentation bör du uppdatera den så att den återspeglar de nya skärmarna. Du hittar exempelbilder på sidan om [uppdateringar i användargränssnittet för Intunes slutanvändarappar](whats-new-app-ui.md#week-of-september-11-2017) page.

#### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 10-företagsportalappen lades till i Windows informationsskydd för att tillåta principen <!-- 677129 -->

Företagsportalappen för Windows 10 har uppdaterats så att den stöder Windows Information Protection (WIP). Programmet kan läggas till i den tillåtna WIP-principen. Med den här ändringen behöver programmet inte längre läggas till i listan **Undantag**. 


## <a name="week-of-august-21-2017"></a>Veckan 21 augusti 2017

### <a name="device-enrollment"></a>Enhetsregistrering
#### <a name="improvements-to-device-overview----1404453---"></a>Förbättringar av enhetsöversikt <!-- 1404453 -->  
Förbättringar av enhetsöversikt visar nu registrerade enheter, men inte enheter som hanteras av Exchange ActiveSync. Exchange ActiveSync-enheter har inte samma hanteringsalternativ som registrerade enheter. Om du vill se antalet registrerade enheter och antalet registrerade enheter efter plattform går du till **enheter** > **översikt** i Intune i Azure Portal.

### <a name="device-management"></a>Enhetshantering
#### <a name="improvements-to-device-inventory-collected-by-intune"></a>Förbättringar av enhetsinventering som samlas in av Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
I den här versionen har vi gjort följande förbättringar i inventeringsinformationen som samlas in av de enheter som du hanterar:
 
-   För Android-enheter kan du nu lägga till en kolumn i enhetsinventeringen som visar den senaste korrigeringsnivån för varje enhet. Lägg till kolumnen med **säkerhetskorrigeringsnivån** i enhetslistan för att se detta.
-   När du filtrerar enhetsvyn kan du nu filtrera enheter efter deras registreringsdatum. Du kan till exempel endast visa de enheter som har registrerats efter ett angivet datum.
-   Vi har gjort förbättringar för filter som används av objektet **Last Check-in Date** (Senaste incheckningsdatum).
-   I enhetslistan kan du nu visa telefonnummer för företagsägda enheter.
Du kan dessutom använda filterfönstret för att söka efter enheter efter telefonnummer.
 
Mer information om enhetsinventering finns i [Så här visar du Intunes enhetsinventering](device-inventory.md).

#### <a name="conditional-access-support-for-macos-devices"></a>Stöd för villkorlig åtkomst på macOS-enheter 
<!-- 720172 -->
Nu kan du skapa en princip för villkorlig åtkomst som kräver att Mac-enheter ska vara registrerade i Intune och kompatibla med dess efterlevnadsprinciper för enheter. Användarna kan till exempel ladda ned appen för Intune-företagsportalen på macOS och registrera sina Mac-enheter i Intune. Intune utvärderar om Mac-enheten följer standard eller inte med krav som PIN, kryptering, OS-version och systemintegritet.

- Läs mer om [stöd för villkorlig åtkomst på macOS-enheter](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

#### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>Företagsportalappen för macOS är tillgänglig som förhandsversion <!---1484796--->
Företagsportalappen för macOS är nu tillgänglig som en del av den allmänt tillgängliga förhandsversionen för villkorlig åtkomst i Enterprise Mobility + Security. Den här versionen stöder macOS 10.11 och högre. Hämta den på [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


#### <a name="new-device-restriction-settings-for-windows-10"></a>Inställningar för enhetsbegränsningar för Windows 10    
<!--1063965, 1308850  -->
I den här versionen har vi lagt till nya inställningar för [begränsningsprofilen för Windows 10-enheter](/intune/device-restrictions-windows-10). Nyheterna finns i följande kategorier:

-   Windows Defender SmartScreen
-   Appbutik

#### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Uppdateringar för BitLocker-inställningar för enhetsprofiler för Windows 10 Endpoint Protection
<!--1459533 -->    
I den här versionen har vi gjort följande förbättringar för hur BitLocker-inställningar fungerar i en enhetsprofil för Windows 10 Endpoint Protection:
 
När du tidigare valde **Blockera** för inställningen **BitLocker med icke kompatibelt TPM-chip** under **Inställningar för BitLocker-operativsystemenhet** gjorde detta tidigare att BitLocker ändå tilläts. Vi har nu löst problemet och BitLocker blockeras nu när det är markerat.
För inställningen **certifikatbaserad dataåterställningsagent** under **Inställningar för BitLocker-operativsystemenhet** kan du nu uttryckligen blockera den certifikatbaserade dataåterställningsagenten. Som standard tillåts agenten.
För inställningen **Dataåterställningsagent** under **Inställningar för fast BitLocker-dataenhet** kan du nu uttryckligen blockera dataåterställningsagenten.
Mer information finns i [Endpoint Protection-inställningar för Windows 10 och senare](endpoint-protection-windows-10.md).


### <a name="app-management"></a>Apphantering
#### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Ny inloggad upplevelse för användare av Android-företagsportalen och appskyddsprincip <!-- 621669 -->
Slutanvändarna kan nu bläddra bland appar, hantera enheter och visa it-kontaktinformation med hjälp av Android-företagsportalappen utan att registrera sina Android-enheter. Om en användare dessutom redan använder en app som skyddas av principer för Intune-appskydd och startar Android-företagsportalen får slutanvändaren inte längre någon uppmaning att registrera enheten.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Ny inställning i Android-företagsportalappen för att ändra batterioptimering <!--1405990-->
Sidan **Inställningar** i företagsportalappen för Android har en ny inställning som gör det enkelt för användarna att stänga av batterioptimering för företagsportalen och Microsoft Authenticator-appar. Appnamnet som visas i inställningen beror på vilken app som hanterar arbetskontot. Vi rekommenderar att användarna stänger av batterioptimering för att få bättre prestanda med arbetsappar som synkroniserar e-post och data. 

#### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Stöd för flera identiteter med OneNote för iOS...<!-- 1234281 -->
Slutanvändare kan nu använda olika konton (arbete och personliga) med Microsoft OneNote för iOS. Programskyddsprinciper kan tillämpas på företagsdata i arbetsanteckningsböcker utan att de personliga anteckningsböckerna påverkas. En princip kan till exempel tillåta en användare att söka efter information i anteckningsböcker för arbete, men användaren kan inte kopiera och klistra in företagets data från anteckningsboken för arbete till en personlig anteckningsbok.
 
- Mer information om appar som stöder [appskydd och multiidentitet](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) med Intune.

#### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nya inställningar för att tillåta och blockera appar på Samsung KNOX Standard-enheter
<!-- 1305423 822899-->  
Den här versionen innehåller nya [inställningar för enhetsbegränsning](device-restrictions-android.md) som du kan använda för att ange följande applistor:
 
- Appar som användare tillåts att installera
- Appar som användare är blockerade från att installera
- Appar som är dolda från användaren på enheten
 
Du kan ange appen med hjälp av URL, paketnamn eller från listan över appar som du hanterar.

#### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Ny gränssnittslänk för princip för appbaserad villkorlig åtkomst för Azure AD från Intune
<!-- 1016201 -->
IT-administratörer kan nu ange appbaserade villkorsprinciper via det nya gränssnittet för villkorlig åtkomstprincip i Azure AD-arbetsbelastningen. Den appbaserade villkorliga åtkomsten som finns i avsnittet Intune-appskydd i Azure Portal finns kvar där för tillfället och tillämpas sida vid sida. Det finns även en praktisk länk till det nya gränssnittet för villkorlig åtkomstprincip i Intune-arbetsbelastningen.

- Läs mer om [appbaserad villkorlig åtkomst i Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).


## <a name="notices"></a>Meddelanden

### <a name="ip-addresses-for-intune-updated----1175274---"></a>IP-adresser för Intune, uppdaterade <!-- 1175274 -->
En [uppdaterad lista med DNS-namn och IP-adresser](/intune/network-bandwidth-use) är tillgänglig för proxy-inställningarna för brandväggen.

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Använd Azure Active Directory för villkorlig åtkomst <!-- 967947 -->
Villkorlig åtkomst finns i området Azure Active Directory i Azure-portalen och ger ett mer effektivt och flexibelt ramverk för att ange principer för programmolntjänster som Office 365 Exchange Online och SharePoint Online.  Använd bladet **Villkorlig åtkomst i Azure Active Directory** för att konfigurera principer i stället för Intune-konsolen. Befintliga principer i Intune-konsolen måste återskapas i Azure-portalen. Se [Skapa villkorliga åtkomstprinciper i Azure AD](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview) för mer information.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->
För Intune-konton som skapades efter januari 2017 har Intune aktiverat direktåtkomst till registreringsscenarier i Apple med arbetsflödet Registrera enheter i Azure-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i den klassiska Intune-portalen. Intune-konton som skapades före januari 2017 måste migreras en gång innan dessa funktioner är tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till Azure-portalen.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Administratörsroller ersätts i Azure Portal
De befintliga MAM-administratörsrollerna (deltagare, ägare och skrivskyddat) som används i den klassiska Intune-portalen (Silverlight) ersätts med en helt ny uppsättning rollbaserade administratörskontroller (RBAC) i Intune Azure Portal. När du har migrerat till Azure-portalen måste du tilldela de nya administratörsrollerna till dina administratörer. Mer information om RBAC och nya de nya rollerna finns i [Rollbaserad åtkomstkontroll för Microsoft Intune](/intune/role-based-access-control).



## <a name="whats-coming"></a>Kommande nyheter

#### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>E-postprogrammet för iOS 11 stöder OAuth<!---1196951--->
Villkorlig åtkomst med Intune stöder säkrare autentisering på iOS-enheter med OAuth. Ett annat flöde på företagsportalappen för iOS kommer att användas för att möjliggöra säkrare autentisering. När användare försöker logga in på ett nytt Exchange-konto i e-postprogrammet visas en dialogruta om webbvyn. Vid registreringen i Intune visas en dialogruta som ger det inbyggda e-postprogrammet åtkomst till ett certifikat. De flesta användarna kommer inte att se e-postmeddelanden i karantän längre. För befintliga e-postkonton används även i fortsättningen det grundläggande protokollet för autentisering, så dessa användare kommer fortfarande att få e-postmeddelanden i karantän levererade till sig. Den här inloggningen för slutanvändare liknar den på Office-mobilappar.

### <a name="end-of-support-for-ios-80----1164477---"></a>Stöd för iOS 8.0 upphör <!---1164477--->
Hanterade appar och företagsportalappen för iOS kräver iOS 9.0 och högre för åtkomst till företagets resurser. Enheter som inte är uppdaterade innan september kommer inte längre att ha åtkomst till Företagsportalen eller apparna. 

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Gränssnittsuppdateringar på företagsportalswebbplatsen <!--1313244 part 2-->
__Uppdateringar av aktuella appar__  
Vi har lagt till en särskild sida på webbplatsen där användarna kan bläddra bland appar som du har valt att presentera och vi har gjort några gränssnittsförändringar på avsnittet Aktuella på startsidan. Du kan se hur ändringarna ser ut på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Stöd för Android 4.3 och lägre upphör <!---1171127, 1326920 --->
Hanterade appar och företagsportalappen för Android kräver Android 4.4 och högre för åtkomst till företagets resurser. Enheter som inte har uppdaterats innan början i oktober kommer inte längre att ha åtkomst till företagsportalen eller apparna. I december kommer alla registrerade enheter att tvingas att dras tillbaka, vilket innebär att de förlorar åtkomst till företagets resurser. Om du använder principer för appskydd utan MDM kommer appar inte ta emot uppdateringar och kvaliteten på användningsupplevelsen minskar över tid.


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>Påminnelse om plattformsstöd: Mainstream-support för Windows Phone 8.1 upphörde 11 juli 2017
<!-- 1327781 -->
Den 11 juli 2017 upphörde mainstream-support för Windows Phone 8.1-plattformen. Stöd för Windows 8.1 PC påverkas inte.

Windows Phone 8.1-enheter som hanteras av Intune-tjänsten påverkas inte direkt. Enheter som är registrerade fortsätter att fungera och alla principer, konfigurationer och appar fortsätter att fungera som förväntat. Observera att inga förbättringar av Windows Phone 8.1-plattformen i Intune Service och företagsportalappen för Windows Phone 8.1 kommer att distribueras.

Vi rekommenderar att du uppgraderar berättigade Windows Phone 8.1-enheter till Windows 10 Mobile så snart som möjligt. 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Ändringar i stödet för iOS-företagsportalappen <!-- 1164474  -->
Snart kommer det en uppdatering för Microsoft Intunes företagsportalapp för iOS som bara har stöd för enheter som kör iOS 9.0 eller senare. Versionen av Företagsportal som har stöd för iOS 8 kommer att finnas kvar under en kortare övergångsperiod. Om du använder MAM-aktiverade iOS-appar har vi även där enbart stöd för iOS 9.0 och senare. Se till att slutanvändarna uppdaterar till den senaste versionen av operativsystemet. 

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
I nuläget har vi inte hunnit fastställa några datum, men vi passar på att informera om detta i god tid så att du har tid att planera. Se till att användarna har uppdaterat till iOS 9+. När den nya versionen av företagsportalappen släpps bör du även uppmana användarna att uppdatera sina företagsportalappar.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Uppmana användarna att uppdatera till iOS 9.0 eller senare för att kunna dra full nytta av de nya funktionerna i Intune.  Uppmana användarna att installera den nya versionen av företagsportalen för att kunna dra full nytta av de nya funktionerna.

Gå till Intune i Azure-portalen och visa Enheter > Alla enheter. Filtrera efter iOS-versionen för att se alla befintliga enheter med operativsystem som är tidigare än iOS 9.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->
Apple har tillkännagivit att de kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen.

Vi har gjort en version av företagsportalens app tillgänglig för iOS genom Apple TestFlight-programmet som genomdriver de nya ATS-kraven. Om du vill prova, så att du kan testa din ATS-kompatibilitet, kan du skicka ett e-post-meddelande till <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app"> CompanyPortalBeta@microsoft.com </a> med ditt förnamn, efternamn, din e-postadress och företagets namn. Läs [Intunes supportblogg](https://aka.ms/compportalats) för mer information.

### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Nyheter i företagsportalens gränssnitt](whats-new-app-ui.md)
* [Nyheter från föregående månad](whats-new-archive.md)
