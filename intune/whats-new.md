---
title: Nyheter i Microsoft Intune
titleSuffix: Intune on Azure
description: "Ta reda på vad som är nytt i Intune Azure-portalen"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/01/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c27ce82d10b927fdecec3ea2952376dc7b1f792e
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Läs mer om varje veckas nyheter i Microsoft Intune. Du kan också läsa mer om [kommande ändringar](#whats-coming), [viktiga meddelanden](#notices) om tjänsten och information om [tidigare versioner](whats-new-archive.md).

> [!Note]
> Hybriddistributioner med Configuration Manager kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Role-based access control
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
-->   

## <a name="week-of-july-31-2017"></a>Veckan 31 juli 2017

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Gränssnittsuppdateringar på företagsportalswebbplatsen <!--1313244 part 1-->
Vi har gjort flera uppdateringar i gränssnittet för [företagsportalswebbplatsen](https://portal.manage.microsoft.com) för att förbättra användarupplevelsen.

__Förbättringar av appaneler__ Appikoner som är mindre än 79x79 pixlar visas nu med en automatiskt genererad bakgrund som baseras på ikonens huvudsakliga färg. Detta ersätter den grå kantlinje som tidigare fanns på appaneler med små ikoner. Större ikoner ändras så att de fyller appanelen så mycket som möjligt, samtidigt som bildkvaliteten bibehålls.

Vi rekommenderar att IT-administratörer publicerar appar med ikoner som har en minsta storlek på 120 x120 pixlar.

__Navigeringsändringar__ Objekt i navigeringsraden har flyttats till menyn längst upp till vänster. Sidan Kategorier har tagits bort. Användarna kan nu filtrera innehåll efter kategori när de bläddrar.

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Förbättrad inloggning i företagsportalens appar för alla plattformar <!--User Story 1132123-->

Vi informerar om en förändring som kommer under de kommande månaderna som kommer att förbättra inloggningen för Intune-företagsappar för Android, iOS och Windows. Det nya användargränssnittet visas automatiskt på alla plattformar för företagsportalappen när Azure AD genomför ändringen. Dessutom kan användarna nu logga in på företagsportalen från en annan enhet med en engångskod som genereras. Detta är särskilt användbart när användarna måste logga in utan autentiseringsuppgifter.

För att visa skärmbilder med den tidigare inloggningsmiljön, den nya inloggningsmiljön med inloggningsuppgifter och den nya inloggningsmiljön från en annan enhet, se [Nyheter i appgränssnittet](/intune/whats-new-app-ui).


## <a name="week-of-july-23rd-2017"></a>Veckan 23 juli 2017

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Ljust och mörkt läge är tillgängligt för företagsportalappen för Windows 10 <!---676547--->
Slutanvändare kan anpassa färgläget för företagsportalappen för Windows 10. Användaren kan göra ändringarna i avsnittet Inställningar i företagsportalappen. Ändringen tillämpas när användaren har startat om appen. För Windows 10 version 1607 och senare kommer standardläget för appen bero på systeminställningen. För Windows 10 version 1511 och tidigare kommer standardläget för appen vara det ljusa läget.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Gör det möjligt för slutanvändare att tagga sin enhetsgrupp i företagsportalappen för Windows 10 <!---807046-->
Slutanvändare kan nu välja vilken grupp deras enhet tillhör genom att tagga den direkt från företagsportalappen för Windows 10.

## <a name="week-of-june-26th-2017"></a>Veckan som inleds med 26 juni 2017

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll
#### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Ny rollbaserad administrationsåtkomst för Intune-administratörer <!-- 1099990 -->  
En ny administratörsroll för villkorlig åtkomst läggs till för att kunna visa, skapa, ändra och ta bort Azure AD:s villkorliga åtkomstprinciper. Tidigare hade endast globala administratörer och säkerhetsadministratörer den här behörigheten. Intune-administratörer kan tilldelas den här rollbehörigheten så att de får åtkomst till principer för villkorlig åtkomst.


### <a name="device-enrollment"></a>Enhetsregistrering
#### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Tagga företagsägda enheter med serienummer <!-- 1215070 -->  
Intune stöder nu uppladdning av iOS-, macOS- och Android-serienummer som identifierare för företagsägda enheter. Du kan inte använda serienummer för att blockera personliga enheter från registrering än, eftersom serienummer inte verifieras under registreringen. Blockering av personliga enheter med serienummer kommer att kunna göras inom en snar framtid.


### <a name="device-management"></a>Enhetshantering
#### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nya fjärråtgärder för iOS-enheter <!-- 854689 -->
I den här versionen har vi lagt till två nya fjärråtgärder som hanterar Apple Classroom-appen på delade iPad-enheter:

-   [Logga ut aktuell användare](device-logout-user.md) – Loggar ut den aktuella användaren av den valda iOS-enheten.
-   [Ta bort användare](device-remove-user.md) – Tar bort en vald användare från den lokala cachen på en iOS-enhet.


#### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Stöd för delade iPad-enheter med iOS Klassrum-appen <!-- 1044681 -->
Från och med den här versionen har vi utökat stödet för hantering av Klassrum-appen i iOS, så att vi kan inkludera elever som loggar in på delade iPad-enheter med sina hanterade Apple-ID:n.


### <a name="app-management"></a>Apphantering  

#### <a name="changes-to-intune-built-in-apps----1332306---"></a>Ändringar i Intunes inbyggda appar<!-- 1332306 -->

Tidigare innehöll Intune ett antal inbyggda appar för snabb tilldelning. Efter feedback från användarna har vi beslutat oss för att ta bort listan och dess inbyggda appar visas inte längre.
Om du har redan har tilldelat några inbyggda appar kommer dessa även i fortsättningen att finnas kvar i listan över appar. Du kan fortsätta att tilldela dessa appar vid behov.
I en senare version planerar vi att lägga till en enklare metod för att välja och tilldela inbyggda appar från Intune-portalen.

#### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Enklare installation av Office 365-appar <!--- 1121362 --->
Med den nya **Office 365 ProPlus**-appen kan du enkelt tilldela Office 365 ProPlus 2016-appar till enheter som du hanterar och som kör den senaste versionen av Windows 10. Dessutom kan du installera Microsoft Project och Microsoft Visio om du har licenser för dem. Appar som du vill använda paketeras tillsammans och visas som en enda app i listan med appar i Intune-konsolen.
Läs mer i informationen om [hur du lägger till Office 365-appar för Windows 10](apps-add-office365.md).


#### <a name="support-for-offline-apps-from-the-windows-store-for-business-----777044----"></a>Stöd för offline-appar från Windows Store för företag <!--- 777044 --->
Offline-appar som du köpt från Windows Store för företag kommer nu att synkroniseras med Intune-portalen. Du kommer sedan att kunna distribuera apparna till enhetsgrupper eller användargrupper. Offline-appar installeras av Intune och inte av butiken.

#### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft Teams finns nu på den appbaserade listan över godkända appar<!-- 1257019 -->

Microsoft Teams-appen för iOS och Android finns nu på listan över godkända appar för appbaserade villkorliga åtkomstprinciper för Exchange och SharePoint Online. Appen kan konfigureras via bladet för Intune-appskydd i Azure-portalen för alla klienter som för tillfället använder appbaserad villkorlig åtkomst.

#### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Integrering av Managed Browser och programproxy <!-- 1287310 -->
 Intune Managed Browser kan nu integreras med programproxy för Azure AD, så att användarna kan komma åt interna webbplatser även när de arbetar på distans. Användarna anger webbadressen i webbläsaren precis som vanligt. Managed Browser skickar begäran via programproxyns webbgateway. Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper](app-configuration-managed-browser.md).


#### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nya appkonfigurationsinställningar för Intune Managed Browser <!-- 682951 -->
I den här versionen har vi lagt till fler konfigurationer för Intune Managed Browser-appen för iOS och Android. Du kan nu använda en appkonfigurationsprincip för att konfigurera standardstartsidan och bokmärken i webbläsaren.
Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper](app-configuration-managed-browser.md)




### <a name="device-configuration"></a>Enhetskonfiguration  
#### <a name="bitlocker-settings-for-windows-10-----951707---"></a>BitLocker-inställningar för Windows 10 <!-- 951707 -->
Du kan nu konfigurera BitLocker-inställningar för Windows 10-enheter med hjälp av en ny enhetsprofil i Intune. Du kan t.ex. kräva att enheter krypteras och även ange ytterligare inställningar som ska användas när BitLocker är aktiverat.
Mer information finns i [Endpoint Protection-inställningar för Windows 10 och senare](endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Nya inställningar för enhetsbegränsningsprofilen i Windows 10 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->

I den här versionen har vi lagt till nya inställningar för begränsningsprofilen för Windows 10-enheter. Nyheterna finns i följande kategorier:

-  Windows försvarare
-  Mobilnät och anslutning
-  Låsskärm
-  Sekretess
-  Sök
-  Windows Spotlight
-  Edge-webbläsare

Mer information om inställningar för Windows 10 finns i [Begränsningsinställningar för enheter med Windows 10 och senare](device-restrictions-windows-10.md).

## <a name="week-of-june-12-2017"></a>Vecka 12 juni 2017

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Företagsportalappen för Android har nu ett nytt användargränssnitt för appskyddsprinciper <!--1305217-->
Baserat på feedback från våra kunder har vi ändrat företagsportalappen för Android så att den visar knappen **Åtkomst till företagsinnehåll**. Avsikten är att förhindra användare från att i onödan gå genom registreringsprocessen när de bara behöver åtkomst till appar som stöder appskyddsprinciper, en funktion i Intune för hantering av mobilappar. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Ny menyåtgärd för att enkelt ta bort Företagsportalen <!--1164569-->
Baserat på användarfeedback har vi lagt till en ny menyåtgärd i företagsportalen för Android för att ta bort den från din enhet. Den här åtgärden tar bort enheten från Intune-hanteringen så att användaren kan ta bort appen från enheten. Du kan se dessa ändringar på sidan [Vad är nytt i appens gränssnitt](whats-new-app-ui.md) och i [bruksanvisningen för din Android-enhet](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Förbättringar av appsynkronisering med Windows 10 Creators Update <!--676505-->

Företagsportalen för Windows 10 kommer automatiskt att initiera en synkronisering för appinstallationsbegäranden för enheter med Windows 10 Creators Update (1703). Detta minskar problemen där appen fastnar vid tillståndet ”Väntar på synkronisering” när installationer utförs. Dessutom kommer användare att kunna initiera en synkronisering från appen manuellt. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Ny guidad upplevelse för Windows 10-företagsportalen <!---1058938--->

Företagsportalappen för Windows 10 kommer att innehålla en guidad Intune-genomgång för enheter som inte har identifierats eller registrerats. Den nya guiden innehåller stegvisa anvisningar som hjälper användaren att utföra AAD-registrering (krävs för villkorliga åtkomstfunktioner) och MDM-registrering (krävs för enhetshanteringsfunktioner). Guiden kommer att vara tillgänglig på företagsportalens startsida. Användarna kan fortsätta att använda appen även om de inte slutför registreringen, men de får begränsad funktionalitet.

Den här uppdateringen visas bara på enheter som kör Windows 10 Anniversary Update (version 1607) eller senare. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

## <a name="week-of-june-5-2017"></a>Vecka 5 juni 2017

### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Administratörskonsoler till Microsoft Intune och villkorlig åtkomst är allmänt tillgängliga

Vi kommer att göra den nya Intune på Azure-administrationskonsolen och administrationskonsolen för villkorlig åtkomst allmänt tillgängliga. Via Intune på Azure kan du nu hantera alla Intune MAM och MDM-funktioner i en konsoliderad administratörsmiljö och använda Azure AD-gruppering och -mål. Villkorlig åtkomst i Azure ger de avancerade funktionerna i Azure AD och Intune tillsammans i en enhetlig konsol. Och från ett administrativt perspektiv innebär övergången till Azure-plattformen att du kan använda moderna webbläsare.

Intune visas nu utan etiketten **preview** i Azure-konsolen på portal.azure.com.

Det krävs ingen åtgärd för befintliga kunder just nu, om du inte har tagit emot en av en serie meddelanden i meddelandecentret om att vidta åtgärder så att vi kan migrera dina grupper. Du kan också ha fått ett meddelande i meddelandecentret som informerar dig om att migreringen tar längre tid på grund av programfel på vår sida. Vi arbetar hårt på att migrera alla berörda kunder.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Förbättringar av appaneler i företagsportalappen för iOS
Vi har uppdaterat designen av appaneler på startsidan så att de återspeglar anpassningsfärgen som du angett för Företagsportalen. Mer information finns i [nyheter i appgränssnittet](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Kontoväljaren finns nu tillgänglig för företagsportalappen för iOS
Användare av iOS-enheter kan se vår nya kontoväljare när de loggar in på företagsportalen om de använder sitt arbets- eller skolkonto för att logga in på andra Microsoft-appar. Mer information finns i [nyheter i appgränssnittet](whats-new-app-ui.md).

## <a name="week-of-may-29-2017"></a>Vecka 29 maj 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Ändra din utfärdare för hantering av mobila enheter utan att avregistrera hanterade enheter <!--1103950-->

Du kommer att kunna ändra din utfärdare för hantering av mobila enheter utan att behöva kontakta Microsoft Support och utan att behöva avregistrera och omregistrera dina befintliga hanterade enheter. I Configuration Manager-konsolen kan du [ändra utfärdare för hantering av mobila enheter](/sccm/mdm/deploy-use/change-mdm-authority) från Ange till Configuration Manager (hybrid) till Microsoft Intune (fristående) eller vice versa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Förbättrat meddelande för PIN-koder vid start av Samsung KNOX <!--1087143-->
När användarna måste ange en PIN-kod för start på Samsung KNOX-enheter för att bli kompatibla med kryptering, visas meddelandet för användarna. De kommer till rätt plats i appen Inställningar när de trycker på meddelandet.  Meddelandet tog tidigare användaren till skärmen där lösenord ändras.


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Stöd för Apple School Manager (ASM) med delad iPad <!-- 748864, 770395-->

Intune stöder användning av Apple School Manager (ASM) för extern registrering av iOS-enheter, i stället för Apples program för enhetsregistrering. ASM-integrering krävs för att använda Classroom-appen på delade iPads, samt krävs för att aktivera datasynkronisering från ASM till Azure Active Directory via Microsoft School Data Sync (SDS). Mer information finns i [Aktivera registrering av iOS-enheter med Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> För att konfigurera delade iPad-enheter så att de fungerar med klassrumsappen behövs iOS Education i Azure som ännu inte är tillgänglig.  Den här funktionen läggs snart till.

### <a name="device-management"></a>Enhetshantering

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Ge fjärrhjälp till Android-enheter med hjälp av TeamViewer <!-- 675418 -->

Intune kan använda [TeamViewer](https://www.teamviewer.com)-programmet (köps separat) för att ge fjärrhjälp till användare med Android-enheter. För mer information, se [Ge fjärrhjälp för Intune-hanterade Android-enheter](device-profile-android-teamviewer.md).

### <a name="app-management"></a>Apphantering

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Nya villkor för appskyddsprinciper i MAM <!-- 679864 -->

Du kommer att kunna ange ett krav för MAM utan att registrera användare för följande principer:

- Lägsta programversion
- Lägsta operativsystemversion
- Lägsta Intune APP SDK-version i det aktuella programmet (endast iOS)

Den här funktionen är tillgänglig för både Android och iOS. Intune stöder krav på minimiversion för operativsystemversioner, programversioner och Intune APP SDK. I iOS kan program som har integrerat SDK också ange ett lägsta versionskrav på SDK-nivå. Användaren kommer inte att få åtkomst till det aktuella programmet om minimikraven via appskyddsprincipen inte uppfylls på de tre olika nivåer som nämns ovan. Nu kan användaren kan antingen ta bort sitt konto (för program med flera identiteter), stänga programmet och/eller uppdatera sitt operativsystem eller program.

Dessutom kan du också konfigurera ytterligare inställningar för ett icke-blockerande meddelande som rekommenderar en uppgradering av operativsystemet eller programmet. Det här meddelandet kan stängas och programmet kan då användas som vanligt.

Mer information finns i [Principinställningar för iOS-appskydd](app-protection-policy-settings-ios.md) och [Principinställningar för Android-appskydd](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Konfigurera appkonfigurationer för Android for Work <!-- 621621 -->
Vissa Android-appar från webbutiken stöder hanterade konfigurationsalternativ som gör att en IT-administratör kan kontrollera hur appen körs i en arbetsprofil. Med Intune kan du nu visa de konfigurationer som stöds av en app och konfigurera dem från Intune-portalen med en konfigurationsdesigner eller en JSON-redigerare. Mer information finns i [Använda appkonfigurationer för Android for Work](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Ny konfigurationsfunktion för appar för MAM utan registrering <!-- 677969 -->

Du kan nu skapa appkonfigurationsprinciper via MAM utan registrering. Den här funktionen motsvarar appkonfigurationsprinciper som är tillgängliga i appkonfigurationen för mobil enhetshantering (MDM). Ett exempel på konfiguration av en mobilapp med hjälp av MAM utan registrering finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Så här anger du tillåtna och blockerade URL:er för Managed Browser <!-- 682960 -->

Du kan nu konfigurera en lista över tillåtna och blockerade domäner och webbadresser för Intune Managed Browser med konfigurationsinställningarna i Azure-portalen. Detta kan konfigureras oavsett om den används på en hanterad eller ohanterad enhet. Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Principinställningar för appskydd <!-- 1069473 -->

Användare från IT-supportavdelningen kan nu kontrollera licensstatusen för användaren och status för principer för appskydd som är tilldelade till användare i felsökningsbladet. Se [felsökning](./help-desk-operators.md) för mer information.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Kontrollera webbplatsbesök på iOS-enheter <!-- 723832 -->

Du kommer att kunna styra vilka webbplatser iOS-enhetsanvändarna kan besöka, med hjälp av någon av följande två metoder:

- Lägg till tillåtna och blockerade URL:er med hjälp av Apples inbyggda webbinnehållsfilter.

- Tillåt endast åtkomst till angivna webbplatser från webbläsaren Safari. Bokmärken skapas i Safari för varje plats som du anger.

För mer information, se [Inställningar för Intunes webbinnehållsfilter för iOS-enheter](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Förkonfigurera enhetsbehörigheter för Android for Work-appar <!-- 621614 -->

För appar som distribuerats till Android for Work-arbetsprofiler, kommer du att kunna konfigurera behörighetstillstånd för enskilda appar.  Som standard kommer Android-appar som kräver enhetsbehörigheter, som t.ex. åtkomst till en plats eller enhetens kamera, att uppmana användarna att godkänna eller neka behörigheter.  Om till exempel en app ska använda enhetens mikrofon, ombeds användaren att bevilja appen behörighet att använda mikrofonen. Med den här funktionen kan du ange behörigheter åt användaren.  Du kan konfigurera behörigheter för att a) automatiskt neka utan att meddela användaren, b) automatiskt godkänna utan att meddela användaren eller c) uppmana användaren att godkänna eller neka. Mer information finns i [Enhetsbegränsningar i Microsoft Intune med Android for Work](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Definiera en appspecifik PIN-kod för Android for Work-enheter <!-- 728976, 1102534 -->

Enheter med Android 7.0 eller senare med en arbetsprofil som hanteras som Android for Work-enheter låter administratören definiera en lösenordspolicy som endast tillämpas på appar i arbetsprofilen.  Alternativen är:

- Definiera bara en enhetsomfattande lösenordsprincip – Detta är det lösenord som användaren måste använda för att låsa upp hela enheten.
- Definiera bara en lösenordsprincip för arbetsprofilen. Användarna uppmanas att ange ett lösenord varje gång en app i arbetsprofilen öppnas.
- Definiera både en enhets- och en arbetsprofilprincip. IT-administratören kan välja att definiera både en lösenordsprincip för enheten och en lösenordsprincip för arbetsprofilen med olika styrkor (t.ex. en 4-siffrig PIN-kod för att låsa upp enheten, men en 6-siffrig PIN-kod för att öppna arbetsappar).

Mer information finns i [Enhetsbegränsningar i Microsoft Intune med Android for Work](device-restrictions-android-for-work.md).

> [!NOTE]
> Det här är bara tillgängligt på Android 7.0 och högre.  Användaren kan som standard välja att använda två separat definierade PIN-koder, eller välja att kombinera de två definierade PIN-koderna till den starkaste av de två.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Nya inställningar för Windows 10-enheter <!-- 978585 -->

Vi lägger till nya [inställningar i begränsningsprofilen för Windows-enheter](device-restrictions-windows-10.md) som styr funktioner som trådlösa skärmar, enhetsidentifiering, programväxling och felmeddelanden för SIM-kort.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>APN-certifikatet har konfigurerats <!-- 918991 and 823198 -->

När skapar en SCEP certifikatet profil för **Ämnesnamnets format**, **Anpassad** alternativet är tillgängligt för iOS, Android och Windows-enheter. Innan den här uppdateringen var fältet **Anpassad** endast tillgängligt för iOS-enheter. Mer information finns i [så här skapar du en SCEP-certifikatprofil] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile).

När du skapar en PKCS-certifikatprofil för **Alternativt ämnesnamn** är **attributet anpassad Azure AD** tillgängligt. Alternativet **Avdelning** är tillgängligt när du väljer **attributet anpassad Azure AD**. Mer information finns i [så här skapar du en PKCS-certifikatprofil] (certficates-pfx-configure.md#how-to-create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Konfigurera flera appar som kan köras när en Android-enhet är i helskärmsläge <!-- 662059 -->

När en Android-enhet är i helskärmsläge, kunde du tidigare endast konfigurera en app som hade tillstånd att köras. Nu kan du konfigurera flera appar med hjälp av app-ID, lagrings-URL eller genom att välja en Android-app som du redan hanterar. Mer information finns i [helskärmsinställningar](device-restrictions-android.md#kiosk).


## <a name="notices"></a>Meddelanden

### <a name="ip-addresses-for-intune-updated----1175274---"></a>IP-adresser för Intune, uppdaterade <!-- 1175274 -->

En [uppdaterad lista med DNS-namn och IP-adresser](/intune/network-bandwidth-use) är tillgänglig för proxy-inställningarna för brandväggen.

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Använd Azure Active Directory för villkorlig åtkomst <!-- 967947 -->

Villkorlig åtkomst finns i området Azure Active Directory i Azure-konsolen och ger ett mer effektivt och flexibelt ramverk för att ange principer för appmolntjänster som Office 365 Exchange Online och SharePoint Online.  Använd bladet **Villkorlig åtkomst i Azure Active Directory** för att konfigurera principer i stället för klassiska Intune-konsolen. Befintliga principer i den klassiska Intune-konsolen måste återskapas i Azure-konsolen. Se [Skapa villkorliga åtkomstprinciper i Azure AD](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview) för mer information

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->

För Intune-konton som skapades efter januari 2017 har Intune aktiverat direktåtkomst till registreringsscenarier i Apple med arbetsflödet Registrera enheter i Azure-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i den klassiska Intune-portalen. Intune-konton som skapades före januari 2017 måste migreras en gång innan dessa funktioner är tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till Azure-portalen.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Administratörsroller ersätts i Azure Portal

De befintliga MAM-administratörsrollerna (deltagare, ägare och skrivskyddat) som används i den klassiska Intune-portalen (Silverlight) ersätts med en helt ny uppsättning rollbaserade administratörskontroller (RBAC) i Intune Azure Portal. När du har migrerat till Azure-portalen måste du tilldela de nya administratörsrollerna till dina administratörer. Mer information om RBAC och nya de nya rollerna finns i [Rollbaserad åtkomstkontroll för Microsoft Intune](/intune/role-based-access-control).

## <a name="whats-coming"></a>Kommande nyheter

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Gränssnittsuppdateringar på företagsportalswebbplatsen <!--1313244 part 2-->

__Uppdateringar av aktuella appar__ Vi har lagt till en särskild sida på webbplatsen där användarna kan bläddra bland appar som du har valt att presentera, och vi har gjort några gränssnittsförändringar på avsnittet Aktuella på startsidan. Du kan se hur ändringarna ser ut på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Stöd för Android 4.3 och lägre upphör <!---1171127, 1326920 --->
Hanterade appar och företagsportalappen för Android kräver Android 4.4 och högre för åtkomst till företagets resurser. Enheter som inte har uppdaterats innan början i oktober kommer inte längre att ha åtkomst till företagsportalen eller apparna. I december kommer alla registrerade enheter att tvingas att dras tillbaka, vilket innebär att de förlorar åtkomst till företagets resurser. Om du använder principer för appskydd utan MDM kommer appar inte ta emot uppdateringar och kvaliteten på användningsupplevelsen minskar över tid.


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017"></a>Påminnelse om plattformsstöd: Mainstream-support för Windows Phone 8.1 upphör 11 juli 2017
<!-- 1327781 -->

Den 11 juli 2017 upphör mainstream-support för Windows Phone 8.1-plattformen. Stöd för Windows 8.1 PC påverkas inte.

Windows Phone 8.1-enheter som hanteras av Intune-tjänsten påverkas inte direkt. Enheter som är registrerade fortsätter att fungera och alla principer, konfigurationer och appar fortsätter att fungera som förväntat. Observera att inga förbättringar av Windows Phone 8.1-plattformen i Intune Service och företagsportalappen för Windows Phone 8.1 kommer att distribueras.

Vi rekommenderar att du uppgraderar berättigade Windows Phone 8.1-enheter till Windows 10 Mobile så snart som möjligt. 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Ändringar i stödet för iOS-företagsportalappen <!-- 1164474  -->


Snart kommer det en uppdatering för Microsoft Intunes företagsportalapp för iOS som bara har stöd för enheter som kör iOS 9.0 eller senare. Versionen av Företagsportal som har stöd för iOS 8 kommer att finnas kvar under en kortare övergångsperiod. Om du använder MAM-aktiverade iOS-appar har vi även där bara stöd för iOS 9.0 och senare. Se till så att dina slutanvändare uppdaterar till den senaste versionen av operativsystemet. 

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
I nuläget har vi inte hunnit fastställa några datum, men vi passar på att informera om detta i god tid så att du har tid att planera. Se till att dina användare har uppdaterat till iOS 9+. När den nya versionen av företagsportalappen släpps ska du också uppmana användarna att uppdatera sina företagsportalappar.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?

Uppmana användarna att uppdatera till iOS 9.0 eller senare för att kunna dra full nytta av de nya funktionerna i Intune.  Uppmana användarna att installera den nya versionen av företagsportalen för att kunna dra full nytta av de nya funktionerna.

Gå till Intune på Azure-portalen och visa Enheter > Alla enheter. Filtrera efter iOS-versionen för att se alla befintliga enheter med operativsystem tidigare än iOS 9.

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan för ändringar: Intune ändrar Intune-partnerportalens gränssnitt<!-- 1050016 -->

Vi tar bort sidan Intune-Partner från manage.microsoft.com från och med tjänstuppdateringen i mitten på maj 2017.  

Om du är partneradministratör, kommer du inte längre att kunna visa och vidta åtgärder åt dina kunder från sidan Intune Partner. I stället måste du logga in på en av två andra partnerportaler hos Microsoft.

Både [Microsoft Partner Center](https://partnercenter.microsoft.com/) och [Administrationscenter för Microsoft Office 365 Partner](https://portal.office.com/) gör att du kan logga in på kundkonton som du hanterar. I framtiden kan du som partner använda en av dessa webbplatser för att hantera dina kunder.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->

Apple har tillkännagivit att de kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen.

Vi har gjort en version av företagsportalens app tillgänglig för iOS genom Apple TestFlight-programmet som genomdriver de nya ATS-kraven. Om du vill prova, så att du kan testa din ATS-kompatibilitet, kan du skicka ett e-post-meddelande till <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app"> CompanyPortalBeta@microsoft.com </a> med ditt förnamn, efternamn, din e-postadress och företagets namn. Läs [Intunes supportblogg](https://aka.ms/compportalats) för mer information.

### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Nyheter i företagsportalens gränssnitt](whats-new-app-ui.md)
* [Nyheter från föregående månad](whats-new-archive.md)
