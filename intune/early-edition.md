---
title: "Tidig utgåva"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5d5d8e0500a0ee928b1037a978f6d4dadab71495
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2017
---
# <a name="the-early-edition-for-microsoft-intune---august-2017"></a>Den tidiga utgåvan för Microsoft Intune – augusti 2017

Den **tidiga utgåvan** innehåller en lista med funktioner i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte denna information med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
>Följande ändringar är under utveckling för Intune. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Intune på Azure Portal

### <a name="actions-for-non-compliance----730266--"></a>Åtgärder vid inkompatibilitet <!--730266-->     
*Åtgärder vid inkompatibilitet* är en ny funktion för efterlevnadsprinciper som gör det möjligt att vidta åtgärder för enheter som inte är kompatibla. Du kan ange en eller flera åtgärder och ange den tidsperiod då dessa åtgärder måste äga rum. Du kan till exempel meddela användare med inkompatibla enheter via e-post direkt efter att enheterna har blivit inkompatibla, eller så kan du blockera inkompatibla enheter från att få åtkomst till företagsresurser efter en respitperiod på tre dagar via villkorsstyrd åtkomst.

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Ny rapport som visar en lista över iOS-enheter med äldre iOS-versioner <!-- 1352223 -->
Rapporten **Out-of-date iOS Devices** (Gamla iOS-enheter) är tillgänglig i arbetsytan **Programuppdateringar**. I rapporten kan du visa en lista över alla övervakade iOS-enheter som har varit mål för en iOS-uppdateringsprincip och som har tillgängliga uppdateringar. Du kan se en status för varje enhet och se varför enheten inte har uppdaterats automatiskt. 

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>Nya inställningar för att tillåta och blockera appar på Samsung KNOX Standard-enheter <!-- 822899,  1305423-->   
Vi lägger till nya [device restriction settings](device-restrictions-android.md) (inställningar för enhetsbegränsning) som låter dig att ange följande applistor:
  - Appar som användare tillåts att installera
  - Appar som användare är blockerade från att installera
  - Appar som är dolda från användaren på enheten  

Du kan ange appen med hjälp av URL, paketnamn eller från listan över appar som du hanterar.

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Nya inställningar för enhetsbegränsningsprofilen i Windows 10
<!--- 978575, 1308849, 1308850 -->
Vi lägger till nya inställningar i enhetsbegränsningsprofilen i Windows 10 i kategorin Windows Defender SmartScreen.

Mer information om enhetsbegränsningsprofilen för Windows 10 finns i [Inställningar för enhetsbegränsning i Windows 10 och senare]( device-restrictions-windows-10.md).

### <a name="new-device-restriction-settings-for-windows-10------1063965---"></a>Inställningar för enhetsbegränsningar för Windows 10 <!-- 1063965 -->
Vi har lagt till nya inställningar för [begränsningsprofilen för Windows 10-enheter](/intune/device-restrictions-windows-10). Nyheterna finns i följande kategorier:
- Windows Defender SmartScreen
- Appbutik


### <a name="android-for-work-support-for-lookout----1087312---"></a>Android for Work-stöd för Lookout <!-- 1087312 -->   
Intune-anslutningsprogrammet med Lookout stöder Android for Work-enheter när du använder Lookout for Work-appen. Du kan distribuera Lookout-appen innanför eller utanför behållaren.


### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Appskydd i Intune och Citrix MDX-utvecklingsverktyg <!-- 709185 -->
Du kan hantera enheter och appar med en kombination av Citrix XenMobile MDX och Microsoft Intune. Det gör det möjligt att hantera appar med Intunes appskyddsprincip samtidigt som du använder Citrix mVPN-teknik.

Du kan hitta ett kodcentrallager som innehåller Intune Apphanteringsverktyg och Intune App SDK för iOS och Android, som integreras med Citrix MDX mVPN-teknik.


### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – Ny partner för skydd mot mobilhot <!-- 954681 -->
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Zimperium, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Hur fungerar integrering med Intune?
Risken bedöms utifrån telemetri som samlas in från enheter som kör Zimperium. Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Zimperiums riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera icke-kompatibla enheter för företagets resurser baserat på de hot som har identifierats.

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Ny gränssnittslänk för princip för villkorlig åtkomst för Azure AD från Intune  <!-- 1016201 -->
IT-administratörer kan ange appbaserade villkorsprinciper via det nya gränssnittet för villkorlig åtkomstprincip i Azure AD-arbetsbelastningen. De appbaserade villkorliga åtkomstprinciperna som finns i avsnittet Intune-appskydd i Azure finns kvar där för tillfället och tillämpas sida vid sida. Det finns även en praktisk länk till det nya gränssnittet för villkorlig åtkomstprincip i Azure AD från Intune-arbetsbelastningen.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram <!-- 676614 -->   
Du kan ha fler roller för klientåtkomstservrar (CAS) för lokala Exchange-anslutningsprogram. Om de viktigaste klientåtkomstservrarna misslyckas till exempel, så tar Exchange-anslutningsprogrammet emot en fråga för att gå över till andra klientåtkomstservrar. Den här funktionen ser till att tjänsten inte avbryts.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Hanteringspaket för Exchange-anslutningsprogram i System Center Operations Manager <!-- 885457 -->   
Med System Center Operations Manager-hanteringspaketet för Exchange-anslutningsprogrammet kommer du att kunna tolka Exchange-anslutningsloggarna. Det här hanteringspaketet ger dig flera olika sätt att övervaka Intune när du behöver felsöka problem.

### <a name="end-of-support-for-ios-80----1164477---"></a>Stöd för iOS 8.0 upphör <!---1164477--->
Hanterade appar och företagsportalappen för iOS kräver iOS 9.0 och högre för åtkomst till företagets resurser. Enheter som inte är uppdaterade innan september kommer inte längre att ha åtkomst till Företagsportalen eller apparna. I december kommer all åtkomst till företagets resurser inklusive e-post att förhindras. 

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Stöd för Android 4.3 och lägre upphör <!---1171127, 1326920 --->
Hanterade appar och företagsportalappen för Android kräver Android 4.4 och högre för åtkomst till företagets resurser. Enheter som inte har uppdaterats innan början i oktober kommer inte längre att ha åtkomst till företagsportalen eller apparna. I december kommer alla registrerade enheter att tvingas att dras tillbaka, vilket innebär att de förlorar åtkomst till företagets resurser. Om du använder principer för appskydd utan MDM kommer appar inte ta emot uppdateringar och kvaliteten på användningsupplevelsen minskar över tid.


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>Påminnelse om plattformsstöd: Mainstream-support för Windows Phone 8.1 upphör 11 juli 2017<!-- 1327781 -->  
Den 11 juli 2017 upphör mainstream-support för Windows Phone 8.1-plattformen. Stöd för Windows 8.1 PC påverkas inte.

Windows Phone 8.1-enheter som hanteras av Intune-tjänsten påverkas inte direkt. Enheter som är registrerade fortsätter att fungera och alla principer, konfigurationer och appar fortsätter att fungera som förväntat. Observera att inga förbättringar för Windows Phone 8.1-plattformen i Intune Service och företagsportalappen för Windows Phone 8.1 kommer att distribueras.

Vi rekommenderar att du uppgraderar berättigade Windows Phone 8.1-enheter till Windows 10 Mobile så snart som möjligt. 

## <a name="intune-apps"></a>Intune-appar

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Intune Managed Browser har stöd för iOS och Android <!---1374196--->

Från och med oktober 2017 stöder Intune Managed Browser-appen på Android-appen endast enheter som körs på Android 4.4 och senare. Intune Managed Browser-appen på iOS har endast stöd för enheter som körs på iOS 9.0 eller senare. Tidigare versioner av Android och iOS kommer att kunna fortsätta att använda Managed Browser, men kommer inte att kunna installera nya versioner av appen och kanske inte använda alla funktioner. Vi rekommenderar att du uppdaterar de här enheterna till en version av operativsystemet som stöds.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Tillåt att slutanvändare får åtkomst till företagsportalappen för Android utan registrering <!---1169910--->  
Slutanvändare behöver snart inte att registrera sina enheter för att komma åt företagsportalappen för Android. Slutanvändare i organisationer som använder principer för appskydd får inte längre uppmaningar att registrera sina enheter när de öppnar företagsportalen. Slutanvändarna kommer också att kunna installera appar från företagsportalen utan att registrera sina enheter. 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Förbättrat felmeddelande när en användare når det högsta antalet enheter som tillåts för registrering <!-- 1270370 -->
I stället för ett allmänt felmeddelande ser slutanvändarna ett vänligt felmeddelande med en åtgärd: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin.” (Du har registrerat det högsta antalet enheter som IT-administratören tillåter. Ta bort en registrerad enhet eller be IT-administratören om hjälp.)

### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Ny inloggad upplevelse för användare av Android-företagsportalen och appskyddsprincip <!-- 621669 -->
Slutanvändarna kan bläddra bland appar, hantera enheter och visa IT-kontaktinformation med hjälp av Android-företagsportalappen utan att registrera sina Android-enheter. Om en användare dessutom redan använder en app som skyddas av Intune-appskyddsprinciper och startar Android-företagsportalen får slutanvändaren inte längre en uppmaning att registrera enheten. 

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informera användarna vilken enhetsinformation som kan visas för iOS <!--739894-->
Vi lägger till **Typ av ägarskap** på skärmen Enhetsinformation i företagsportalappen för iOS. Det gör det möjligt för användarna att få mer information om sekretess direkt från den här sidan från Intunes slutanvändardokument. De kan även hitta denna information på skärmen Om.

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>Sidor med appinformation visar ny information för Android-enheter <!--1287476-->
Sidan med appinformation i företagsportalappen för Android visar de appkategorier som IT-administratören har definierat för den appen.

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>Dialogrutor för hantering av mobilprogram i Intune (MAM) har nu ett modernt gränssnitt <!-- 1199015 -->
Dialogrutor för hantering av mobilprogram i Intune (MAM) har uppdaterats med ett modernt utseende. Dialogrutorna fungerar på samma sätt som tidigare stil.

På moderna Android-enheter har nu fel- eller meddelandedialogrutor som visas av Intune ett uppdaterat utseende.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Ny inställning i Android-företagsportalappen för att ändra batterioptimering <!--1405990-->
Sidan **Inställningar** i företagsportalappen för Android har en ny inställning som gör det enkelt för användarna att stänga av batterioptimering för företagsportalen och Microsoft Authenticator-appar. Appnamnet som visas i inställningen beror på vilken app som hanterar arbetskontot. Vi rekommenderar att användarna stänger av batterioptimering för att få bättre prestanda med arbetsappar som synkroniserar e-post och data. 




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
