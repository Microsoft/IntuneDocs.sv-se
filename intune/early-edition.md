---
title: "Tidig utgåva"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b8d281e3af2458bd5ab343dfa5123b31075d28ed
ms.sourcegitcommit: 2a6ad3c233d15a9fb441362105f64b2bdd550c34
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/13/2017
---
# <a name="the-early-edition-for-microsoft-intune---july-2017"></a>Den tidiga utgåvan för Microsoft Intune – juli 2017

Den **tidiga utgåvan** innehåller en lista med funktioner i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett ytterst begränsat sätt och kan komma att ändras. Dela inte denna information med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
>Följande ändringar är under utveckling för Intune. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Intune på Azure Portal

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Enklare installation av Office 365-appar <!--- 1121362 --->
En ny **Office 365 ProPlus**-apptyp gör det enkelt att tilldela Office 365 ProPlus-appar till enheter som du hanterar och som körs på den senaste versionen av Windows 10. Dessutom kommer du att kunna installera Microsoft Project och Microsoft Visio om du har licenser för dem. Appar som du vill använda paketeras tillsammans och visas som en enda app i listan med appar i Intune-konsolen.


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Ny enhetsåtgärd för att tvinga enheter att synkronisera med Intune <!-- 711369 -->    
Vi lägger till en ny enhetsåtgärd som tvingar den valda enheten att omedelbart checka in med Intune. När en enhet checkar in tar den omedelbart emot eventuella väntande åtgärder eller principer som har tilldelats till den.  Den här åtgärden kan hjälpa dig att validera och felsöka principer som du har tilldelat utan att du behöver vänta på nästa schemalagda incheckning.

### <a name="actions-for-non-compliance----730266--"></a>Åtgärder vid inkompatibilitet <!--730266-->     
*Åtgärder vid inkompatibilitet* är en ny funktion för efterlevnadsprinciper som gör det möjligt att vidta åtgärder för enheter som inte är kompatibla. Du kan ange en eller flera åtgärder och ange den tidsperiod då dessa åtgärder måste äga rum. Du kan till exempel meddela användare med inkompatibla enheter via e-post direkt efter att enheterna har blivit inkompatibla, eller så kan du blockera inkompatibla enheter från att få åtkomst till företagsresurser efter en respitperiod på tre dagar via villkorsstyrd åtkomst.

### <a name="new-app-configuration-settings-for-the-intune-managed-browser-----682951----"></a>Nya appkonfigurationsinställningar för Intune Managed Browser <!--- 682951 --->
Vi kommer att lägga till ytterligare konfigurationer för Intune Managed Browser-appen. Du kommer att kunna använda en appkonfigurationsprincip för att konfigurera standardstartsidan och bokmärken i webbläsaren.

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Begränsa Android- och iOS-enhetsregistrering per OS-version <!--- 1333256,  1245463 --->  
Intune har nu stöd för att begränsa iOS- och Android-registrering efter operativsystemets versionsnummer. Under **Intune** > **Registreringsbegränsningar** > **Begränsning för enhetstyp** > **Standard** > **Plattformsbegränsningar** kan IT-administratören konfigurera en plattformskonfiguration som begränsar registrering mellan ett lägsta och högsta operativsystemsvärde. Versionerna för operativsystemet Android måste anges som Major.Minor.Build.Rev, där Build och Rev är valfria. iOS-versionerna måste anges som Major.Minor.Build, där Build är valfritt.

>[!NOTE]
>Den här inställningen begränsar inte registrering via Apples registreringsprogram, som till exempel Apple DEP, Apple School Manager eller Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Begränsa registrering av personligt ägda Android-, iOS- macOS-enheter <!--- 1333272,  1333275, 1245709 --->
Intune stöder nu begränsning av registrering av personligt ägda iOS-, Android- och macOS-enheter med enhetsserienummer. Vissa enheter rapporterar inte serienummer. Kontrollera med enhetstillverkarna för ytterligare information. Genom att ladda upp serienumren till Intune kan du fördeklarera enheter som företagsägda. Med begränsningar för registrering kan du blockera personligt ägda enheter (BYOD) och endast tillåta registrering av företagsägda enheter.

Om du vill importera serienummer i Intune-portalen går du till **Enhetsregistrering** > **ID:n för företagsenheter** och klickar på **Lägg till**. Sedan laddar du upp en. CSV-fil (ingen rubrik, två kolumner för serienummer och detaljer som IMEI-nummer).  Om du vill begränsa personligt ägda enheter, går du till **Enhetsregistrering** > **Registreringsbegränsningar**. Under **Begränsningar av enhetstyp** väljer du **Standard** och sedan **Plattformskonfigurationer**. Du kan **Tillåta** eller **Blockera** personligt ägda iOS-, Android- och macOS-enheter. 

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen <!-- 777100 -->   
En ny princip kommer att vara tillgänglig från arbetsytan Programuppdateringar där du kan tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga programuppdateringen. Du kan även se en ny rapport som visar en lista över iOS-enheter med äldre versioner och en sammanfattning för varför de är inaktuella.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>Nya inställningar för att tillåta och blockera appar på Samsung KNOX Standard-enheter <!-- 822899,  1305423-->   
Vi lägger till nya [device restriction settings](device-restrictions-android.md) (inställningar för enhetsbegränsning) som låter dig att ange följande applistor:
  - Appar som användare tillåts att installera
  - Appar som användare är blockerade från att installera
  - Appar som är dolda från användaren på enheten  

Du kan ange appen med hjälp av URL, paketnamn eller från listan över appar som du hanterar.

### <a name="android-for-work-support-for-lookout----1087312---"></a>Android for Work-stöd för Lookout <!-- 1087312 -->   
Intune-anslutningsprogrammet med Lookout stöder Android for Work-enheter när du använder Lookout for Work-appen. Du kommer att kunna distribuera Lookout-appen innanför eller utanför behållaren.


### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651--and--1172027----"></a>Check Point SandBlast Mobile – Ny partner för skydd mot mobilhot <!-- 954651  and  1172027 ? -->  
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Check Point SandBlast Mobile, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Hur fungerar integrering med Intune?
Risken bedöms utifrån telemetri som samlas in från enheter som kör Check Point SandBlast Mobile. Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Check Point SandBlast Mobiles riskbedömning som aktiveras via Intunes principer för enhetsefterlevnad. Du kan tillåta eller blockera inkompatibla enheters åtkomst till företagets resurser utifrån identifierade hot.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – Ny partner för skydd mot mobilhot <!-- 954681 -->
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Zimperium, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Hur fungerar integrering med Intune?
Risken bedöms utifrån telemetri som samlas in från enheter som kör Zimperium. Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Zimperiums riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera icke-kompatibla enheter för företagets resurser baserat på de hot som har identifierats.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram <!-- 676614 -->   
Du kan ha fler roller för klientåtkomstservrar (CAS) för lokala Exchange-anslutningsprogram. Om de viktigaste klientåtkomstservrarna misslyckas till exempel, så tar Exchange-anslutningsprogrammet emot en fråga för att gå över till andra klientåtkomstservrar. Den här funktionen ser till att tjänsten inte avbryts.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Hanteringspaket för Exchange-anslutningsprogram i System Center Operations Manager <!-- 885457 -->   
Med System Center Operations Manager-hanteringspaketet för Exchange-anslutningsprogrammet kommer du att kunna tolka Exchange-anslutningsloggarna. Du får därmed flera olika sätt att övervaka Intune när du behöver felsöka problem.

### <a name="conditional-access-support-for-mac-devices-----720172---"></a>Stöd för villkorlig åtkomst på Mac-enheter <!-- 720172 -->   
Du kommer snart att kunna skapa en princip för villkorlig åtkomst som kräver att Mac-enheter ska vara registrerade i Intune och kompatibla med dess efterlevnadsprinciper för enheter. Användarna kan till exempel ladda ned appen för Intune-företagsportalen på macOS och registrera sina Mac-enheter i Intune. Intune utvärderar om Mac-enheten följer standard eller inte med krav som PIN, kryptering, OS-version och systemintegritet.

### <a name="end-of-support-for-ios-80----1164477---"></a>Stöd för iOS 8.0 upphör <!---1164477--->
Hanterade appar och företagsportalappen för iOS kräver iOS 9.0 och högre för åtkomst till företagets resurser. Enheter som inte är uppdaterade innan september kommer inte längre att ha åtkomst till Företagsportalen eller apparna. I december kommer all åtkomst till företagets resurser inklusive e-post att förhindras. 

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Stöd för Android 4.3 och lägre upphör <!---1171127, 1326920 --->
Hanterade appar och företagsportalappen för Android kräver Android 4.4 och högre för åtkomst till företagets resurser. Enheter som inte har uppdaterats innan början i oktober kommer inte längre att ha åtkomst till företagsportalen eller apparna. I december kommer alla registrerade enheter att tvingas att dras tillbaka, vilket innebär att de förlorar åtkomst till företagets resurser. Om du använder principer för appskydd utan MDM kommer appar inte ta emot uppdateringar och kvaliteten på användningsupplevelsen minskar över tid.





### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>Påminnelse om plattformsstöd: Mainstream-support för Windows Phone 8.1 upphör 11 juli 2017<!-- 1327781 -->  
Den 11 juli 2017 upphör mainstream-support för Windows Phone 8.1-plattformen. Stöd för Windows 8.1 PC påverkas inte.

Windows Phone 8.1-enheter som hanteras av Intune-tjänsten påverkas inte direkt. Enheter som är registrerade fortsätter att fungera och alla principer, konfigurationer och appar fortsätter att fungera som förväntat. Observera att inga förbättringar för Windows Phone 8.1-plattformen i Intune Service och företagsportalappen för Windows Phone 8.1 kommer att distribueras.

Vi rekommenderar att du uppgraderar berättigade Windows Phone 8.1-enheter till Windows 10 Mobile så snart som möjligt. 




## <a name="intune-apps"></a>Intune-appar

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Förbättrad inloggning i företagsportalens appar för alla plattformar <!--User Story 1132123-->    
Vi presenterar en ändring under de kommande månaderna som förbättrar inloggningen för Intune-företagsportalens appar för Android, iOS och Windows. Det nya användargränssnittet visas automatiskt på alla plattformar för företagsportalappen när Azure AD genomför ändringen. Dessutom kan användarna nu logga in på företagsportalen från en annan enhet med en engångskod som genereras. Detta är särskilt användbart när användarna måste logga in utan autentiseringsuppgifter.

Du hittar skärmdumpar av föregående inloggning, den nya inloggningen med autentiseringsuppgifter och den nya inloggningen från en annan enhet på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Ljust och mörkt läge är tillgängligt för företagsportalappen för Windows 10 <!---676547--->
Slutanvändare kan anpassa färgläget för företagsportalappen för Windows 10. Användaren kan göra ändringarna i avsnittet Inställningar i företagsportalappen. Ändringen tillämpas när användaren har startat om appen. För Windows 10 version 1607 och kommer standardläget för appen bero på systeminställningen. För datorer som kör Windows 10 version 1511 och tidigare kommer standardläget för appen vara det ljusa läget.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Gör det möjligt för slutanvändare att tagga sin enhetsgrupp i företagsportalappen för Windows 10 <!---807046-->    
Slutanvändare kan välja vilken grupp deras enhet tillhör genom att tagga den direkt från företagsportalappen för Windows 10.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Tillåt att slutanvändare får åtkomst till företagsportalappen för Android utan registrering <!---1169910--->  
Slutanvändare behöver snart inte att registrera sina enheter för att komma åt företagsportalappen för Android. Slutanvändare i organisationer som använder principer för appskydd får inte längre uppmaningar att registrera sina enheter när de öppnar företagsportalen. Slutanvändarna kommer också att kunna installera appar från företagsportalen utan att registrera sina enheter. 

### <a name="users-who-are-signed-in-to-exchange-can-automatically-access-the-company-portal-website-on-windows-10-devices---1323204--"></a>Användare som är inloggade på Exchange får automatiskt åtkomst till företagsportal-webbplatsen på Windows 10-enheter <!--1323204-->  
Windows 10-användare som redan har autentiserats i Exchange och som tagit emot karantänmeddelandet om villkorlig åtkomst och klickat på länken i e-postmeddelandet behöver inte längre återautentisera i webbläsaren innan de börjar konfigurera företagsåtkomst.


## <a name="notices"></a>Meddelanden

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->   
Apple har tillkännagivit att de från och med våren 2017 kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen. Läs [Intunes supportblogg](https://aka.ms/compportalats) för mer information.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->   
För Intune-konto som har skapats senare än januari 2017 har Intune möjliggjort direktåtkomst till Apples-registreringsscenarier med arbetsbelastningen Registrera enheter i Azure Preview-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i den klassiska Intune-portalen. Intune-konton som skapats före januari 2017 behöver migreras vid ett tillfälle innan de här funktionerna finns tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till förhandsversionen.

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan för ändringar: Intune ändrar Intune-partnerportalens gränssnitt<!-- 1050016 -->
Vi tar bort sidan Intune-Partner från manage.microsoft.com från och med tjänstuppdateringen i mitten på maj 2017.  

Om du är partneradministratör, kommer du inte längre att kunna visa och vidta åtgärder åt dina kunder från sidan Intune Partner. I stället måste du logga in på en av två andra partnerportaler hos Microsoft.

Både [Microsoft Partner Center](https://partnercenter.microsoft.com/) och [Administrationscenter för Microsoft Office 365 Partner](https://portal.office.com/) gör att du kan logga in på kundkonton som du hanterar. I framtiden kan du som partner använda en av dessa webbplatser för att hantera dina kunder.



### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).
