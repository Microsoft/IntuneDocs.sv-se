---
title: Nyheter de senaste månaderna i Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Granska äldre meddelanden från Intunes sida med nyheter
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d87cf0a56a6b114a210242691d0441882c186964
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Nyheter i Microsoft Intune – föregående månader

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="october-2017"></a>Oktober 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>Versionsnummer för verksamhetsspecifika iOS och Android-program är synliga <!-- 1380712 -->

Appar i Intune visar nu versionsnumret för verksamhetsspecifika iOS och Android-appar. Numret visas på Azure Portal i listan över appar och på bladet med översikt över appar. Slutanvändarna kan se appnumret i företagsportalappen och i webbportalen.

__Fullständigt versionsnummer__ Det fullständiga versionsnumret identifierar en specifik version av appen. Numret visas som _Version_(_Build_). Exempelvis, 2.2(2.2.17560800)

Det fullständiga versionsnumret har två komponenter:

 - **Version**  
   Versionsnumret är det läsbara versionsnumret för appen. Det här numret används av slutanvändare för att identifiera olika versioner av appen.

 - **Build-nummer**  
    Build-numret är ett internt nummer som kan användas i appidentifiering och för att programmässigt hantera appen. Build-nummer refererar till en iteration av appen som refererar till ändringar i koden.

Mer information om versionsnummer och utveckling av verksamhetsspecifika appar finns i [Get started with the Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers) (Kom igång med Microsoft Intune App SDK).

### <a name="device-and-app-management-integration----677972---"></a>Integrering av enhets- och apphantering <!-- 677972 -->   
Nu när Intunes hantering av mobila enheter (MDM) och hantering av mobilprogram (MAM) båda är åtkomliga från Azure-portalen har Intune börjat integrera IT-adminstratörsupplevelsen kring program- och enhetshantering. De här ändringarna är avsedda att förenkla enhets- och apphanteringen.

Läs mer om ändringarna i MDM och MAM som presenteras i [Intune-supportteamets blogg](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Nya registreringsaviseringar för Apple-enheter <!-- 1471790 -->
Översiktssidan för registrering visar användbara aviseringar för IT-administratörer som gäller hantering av Apple-enheter. Aviseringar visas på översiktssidan när Apple MDM-push-certifikatet upphör att gälla eller redan har gått ut; när DEP-token upphör att gälla eller redan har gått ut eller när det finns enheter i programmet för enhetsregistrering som inte är tilldelade.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Stöd för token-ersättning för appkonfiguration utan enhetsregistrering <!-- 1080364 -->

Du kan använda token för dynamiska värden i appkonfigurationer för appar på enheter som inte har registrerats. Mer information finns i [Add app configuration policies for managed apps without device enrollment](app-configuration-policies-managed-app.md) (Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Uppdateringar i företagsportalappen för Windows 10 <!--1299474-->
Inställningssidan i företagsportalappen för Windows 10 har uppdaterats för att inställningar och avsedda användaråtgärder ska vara mer konsekventa över alla inställningar. Den har också uppdaterats så att den matchar layouten för andra Windows-appar. Du hittar före-/efter-bilder på sidan [nyheter i appgränssnittet](whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Informera slutanvändarna om vilken enhetsinformation som kan visas för Windows 10-enheter <!--1337920-->
Vi har lagt till **ägarskapstyp** till skärmen enhetsinformation i företagsportalappen för Windows 10. På så sätt kan användarna få mer information om sekretess direkt från den här sidan från Intunes slutanvändardokumentation. De kommer även att kunna hitta den här informationen på **Om**-skärmen.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Feedbackfrågor för företagsportalappen för Android <!--1165249-->
Företagsportalappen för Android ber nu om feedback från slutanvändare. Denna feedback skickas direkt till Microsoft och ger slutanvändarna en möjlighet att recensera appen i den offentliga Google Play-butiken. Feedback är inte obligatoriskt och kan enkelt ignoreras så att användarna kan fortsätta att använda appen.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Hjälper dina användare att hjälpa sig själva med företagsportalsappen för Android <!-- 1573324, 1573150, 1558616, 1564878 -->

Företagsportalappen för Android har lagt till anvisningar för slutanvändare för att hjälpa dem att förstå och om möjligt, själva lösa nya problem.
- Slutanvändare dirigeras till [Azure Active Directory-portalen](https://account.activedirectory.windowsazure.com/r/#/profile) för att ta bort en enhet om de har nått det högsta antalet enheter som de tillåts ha.
- Slutanvändare rekommenderas åtgärder att vidta för att hjälpa dem att [åtgärda aktiveringsfel på Samsung Knox-enheter](https://go.microsoft.com/fwlink/?linkid=859718) eller för att [inaktivera energisparläge](/intune-user-help/power-saving-mode-android). Om ingen av dessa lösningar löser problemet tillhandahåller vi en förklaring om hur du [submit logs to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (skickar loggar till Microsoft).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>En ny funktion, ”Lös”, är tillgänglig för Android-enheter <!-- 1583480 -->

Företagsportalappen för Android presenterar en ”Lös”-åtgärd på sidan _Uppdatera enhetsinställningar_. Det här alternativet tar slutanvändaren direkt till inställningen som gör att enheten är icke-kompatibel. Företagsportalappen för Android stöder för närvarande den här åtgärden för inställningarna [enhetens lösenord](/intune-user-help/set-your-pin-or-password-android), [USB-felsökning](/intune-user-help/you-need-to-turn-off-usb-debugging-android) och [Okända källor](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Förloppsindikator för enhetsinstallationen i Android-företagsportalen <!-- 1565657 -->
Företagsportalappen för Android visar en förloppsindikator för installationen av enheten när en användare registrerar sin enhet. Indikatorn visas nya statusar, som börjar med ”ställer in din enhet...” och sedan ”registrerar din enhet...”, därefter ”slutför registrering av din enhet...” och ”slutför konfigurationen av din enhet...”.

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Stöd för certifikatbaserad autentisering på företagsportalen för iOS <!--1029830-->
Vi har lagt till stöd för certifikatbaserad autentisering (CBA) i företagsportalappen för iOS. Användare med CBA anger sitt användarnamn och trycker på länken ”Signera med ett digitalt certifikat”. CBA stöds redan på företagsportalappar för Android och Windows. Du kan läsa mer på sidan [Logga in på företagsportal-appen](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Program som är tillgängliga med eller utan registrering kan nu installeras utan att först uppmanas till registrering. <!-- 1334712 -->

Företagsprogram som har gjorts tillgängliga med eller utan registreringen i Androids företagsportalapp kan nu installeras utan någon uppmaning att registrera.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Stöd för Windows AutoPilot-distributionsprogram i Microsoft Intune  <!-- 747617  -->
Nu kan du använda Microsoft Intune med Windows AutoPilot-distributionsprogrammet och ge dina användare möjlighet att etablera sina företagsenheter utan hjälp från IT-avdelningen. Du kan anpassa OOBE-åtgärderna (Out-of-Box Experience) och vägleda användarna när de ska ansluta sina enheter till Azure AD och registrera sig i Intune. Microsoft Intune och Windows AutoPilot samarbetar för att eliminera behovet av att distribuera, underhålla och hantera operativsystemavbildningar. Läs mer i informationen om att [registrera Windows-enheter med Windows AutoPilot-distributionsprogrammet](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="quick-start-for-device-enrollment-----1425655---"></a>Snabbstart för enhetsregistrering  <!-- 1425655 --> 
Nu är snabbstart tillgängligt i **Enhetsregistrering** och innehåller en tabell med referenser för hantering av plattformar och konfigurering av registreringsprocessen. Via en kort beskrivning av varje objekt och länkar till dokumentation med stegvisa instruktioner får du användbar dokumentation för att enklare komma igång.

### <a name="device-categorization----1427491---"></a>Enhetskategorisering <!-- 1427491 -->
De registrerade enheternas plattformsdiagram på bladet **Enheter > Översikt** ordnar enheter efter plattform, inklusive Android, iOS, macOS, Windows och Windows Mobile.  Enheter som kör andra operativsystem är grupperade i ”Övrigt”.  Detta inkluderar enheter som har tillverkats av Blackberry och NOKIA.  

Om du vill veta vilka enheter som påverkas i din klientorganisation väljer du **Hantera> Alla enheter** och använder sedan **Filter** för att begränsa **OS**-fältet.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – Ny partner för skydd mot mobilhot <!-- 954681 -->  
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Zimperium, en Mobile Threat Defense-lösning som är integrerad med Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Så här fungerar integrering med Intune
Risken bedöms utifrån telemetri som samlas in från enheter som kör Zimperium. Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Zimperiums riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera icke-kompatibla enheter för företagets resurser baserat på de hot som har identifierats.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Nya inställningar för enhetsbegränsningsprofilen i Windows 10 <!--- 978575, 1308849, -->  
Vi lägger till nya inställningar i enhetsbegränsningsprofilen i Windows 10 i kategorin Windows Defender SmartScreen.

Mer information om enhetsbegränsningsprofilen för Windows 10 finns i [Inställningar för enhetsbegränsning i Windows 10 och senare]( device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Fjärrsupport för Windows- och Windows Mobile-enheter <!-- 1070473 -->  
Intune kan nu använda [TeamViewer](https://www.teamviewer.com)-programvaran (säljs separat) för att du ska kunna ge fjärrhjälp till de användare som kör Windows- och Windows Mobile-enheter.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Genomsök enheter med Windows Defender <!-- 1280988  1280990   -->
Du kan nu även köra en **snabbsökning**, **fullständig genomsökning** och **uppdatering av signaturer** med Windows Defender Antivirus på hanterade Windows 10-enheter. På enhetens översiktsblad väljer du den åtgärd som ska köras på enheten. Du uppmanas att bekräfta åtgärden innan kommandot skickas till enheten. 

**Snabbsökning**: En snabbsökning genomsöker platser där skadliga register startas, till exempel registernycklar och kända startmappar i Windows. En snabbsökning tar i genomsnitt fem minuter. I kombination med inställningen **Realtidsskydd alltid på** som söker igenom filer när de öppnas, stängs och när användaren navigerar till en mapp, ger snabbsökningen skydd mot skadlig kod som kan finnas i systemet eller kärnan. Användarna ser resultatet av genomsökningen på sina enheter när den är klar. 

**Fullständig genomsökning**: En fullständig genomsökning kan användas på enheter där det finns en skadlig kod för att se om det finns några inaktiva komponenter som kräver en mer omfattande rensning. Den är även användbar för att köra genomsökningar på begäran. En fullständig genomsökning kan ta en timme att köra. Användarna ser resultatet av genomsökningen på sina enheter när den är klar. 

**Uppdatering av signaturer**: Kommandot för att uppdatera signaturer uppdaterar Windows Defender Antivirus-definitionerna för skadlig kod och signaturerna. På så sätt kan du vara säker på att Windows Defender Antivirus fungerar när det gäller att identifiera skadlig kod. Den här funktionen finns endast för Windows 10-enheter och väntar på att enheten ska ansluta till Internet. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Knappen för att aktivera/inaktivera har tagits bort från sidan med Intune-certifikatutfärdare i Intune Azure-portalen <!-- 1400455 -->
 Vi tar bort ett extra steg vid konfigurationen av certifikatanslutningen i Intune. För närvarande laddar du ned certifikatanslutningen och aktiverar den sedan i Intune-konsolen. Om du emellertid inaktiverar anslutningsprogrammet i Intune-konsolen fortsätter anslutningsprogrammet att utfärda certifikat.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Från oktober finns inte längre knappen för att aktivera/inaktivera på sidan Intune Certificate Authority (Intune-certifikatutfärdare) i Intune Azure-portalen. Anslutningsfunktionen förblir densamma. Certifikat distribueras fortfarande för enheter som har registrerats i Intune. Du kan fortsätta att ladda ned och installera certifikatanslutningen. Om du vill stoppa att certifikat utfärdas avinstallerar du nu certifikatanslutningen istället för att inaktivera den.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Om du för närvarande har certifikatanslutningen inaktiverad bör du avinstallera den.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Nya inställningar för enhetsbegränsningsprofilen i Windows 10 Team <!--- 1308838 -->
I den här versionen har vi lagt till många nya inställningar för Windows 10 Team-enhetens begränsningsprofil som hjälper dig att styra Surface Hub-enheter.

Mer information om profilen finns i [Begränsningsinställningar för Windows 10 Team-enheter](device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Förhindra att användare av Android-enheter ändrar sin enhets datum och tid <!-- 1333292 -->
Du kan använda en [anpassad Android-enhetsprincip](custom-settings-android.md) för att förhindra att Android-enhetsanvändarna ändrar enhetens datum och tid.

Gör detta genom att konfigurera en anpassad Android-princip med inställnings-URI:n ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange Ange den till **TRUE** och tilldela den sedan till de grupper som krävs.

### <a name="bitlocker-device-configuration----1397398---"></a>Enhetskonfiguration för BitLocker <!-- 1397398 -->
**Windows-kryptering > Grundinställningar** innehåller en ny inställning för **Varning för annan hårddiskkryptering**, där du kan inaktivera [varningen](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) för annan diskkryptering som kanske används på användarens enhet.  Varningen kräver slutanvändarens medgivande innan BitLocker konfigureras på enheten och blockerar installationen av BitLocker tills den har bekräftats av slutanvändaren.  Den nya inställningen inaktiverar varningen till slutanvändaren.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Volyminköpsprogram för företagsprogram synkroniseras nu till din Intune-klient <!-- 800882 -->  
Tredjepartsutvecklare kan även distribuera appar privat till auktoriserade medlemmar i volyminköpsprogram (VPP) för företag som anges i iTunes Connect. Dessa medlemmar i volyminköpsprogram för företag kan logga in i appbutiken för volyminköpsprogram och köpa sina appar.

Med den här versionen synkroniseras appar för volyminköpsprogram för företag som slutanvändaren köper med Intune-klienterna.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Välj landets Apple Store för att synkronisera VPP-appar <!-- 1332311 -->  
Du kan konfigurera volymköpsprogrammets land när du laddar upp din VPP-token. Intune synkroniserar VPP-appar för alla språk från det angivna VPP-landets App Store.

> [!NOTE]  
> I dag synkroniserar Intune endast VPP-appar från VPP-landet som matchar det Intune-språk som Intune-klienten skapades i.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Blockera att kopiera och klistra in mellan arbetsprofiler och personliga profiler i Android for Work <!-- 1098994 -->
I den här versionen kan du konfigurera arbetsprofilen för Android for Work till att blockera kopiering och inklistring mellan arbetsappar och privata appar. Du hittar den här nya inställningen i profilen **Enhetsbegränsningar** för **Android for Work**-plattformen i **Arbetsprofilinställningar**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Skapa iOS-appar som är begränsade till specifika regionala Apple App Stores <!-- 1281692 -->
Du kommer att kunna ange en språkinställning när du skapar en hanterad app i Apple App Store.

> [!Note]  
> För närvarande kan du bara skapa hanterade appar för Apple App Store som finns i USA.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Uppdatera VPP-användare och enhetslicensierade appar i iOS <!-- 1305564 -->  
Du kommer att kunna konfigurera iOS VPP-token för att uppdatera alla appar som köpts för den token via Intune-tjänsten. Intune identifierar VPP-appuppdateringar i appbutiken och push-installerar dem automatiskt på enheten när den checkas in.

Instruktioner om hur du konfigurerar en VPP-token och aktiverar automatiska uppdateringar finns i [Så här hanterar du iOS-appar som har köpts via ett volyminköpsprogram med Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Användarenhetens associationsentitetssamling lades till i datamodellen för Intunes informationslager <!-- 1187917 -->
Du kan nu skapa rapporter och datavisualiseringar med hjälp av enhetens associationsinformation som associerar användaren och enhetens entitetssamlingar. Datamodellen kan nås via Power BI-filen (PBIX) som hämtas från Intune-sidan Informationslager via OData-slutpunkten, eller genom att utveckla en anpassad klient.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Kontrollera principefterlevnaden för Windows 10:s uppdateringstestgrupper <!-- 1067886 -->
Du kommer att kunna granska en principrapport för din Windows 10-uppdateringstestgrupp i Programuppdateringar > Distributionsstatus per uppdateringstestgrupp. Principrapporten innehåller distributionsstatus för de uppdateringstestgrupper som du har konfigurerat. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Ny rapport som visar en lista över iOS-enheter med äldre iOS-versioner <!-- 1352223 -->
Rapporten **Out-of-date iOS Devices** (Gamla iOS-enheter) är tillgänglig i arbetsytan **Programuppdateringar**. I rapporten kan du visa en lista över alla övervakade iOS-enheter som har varit mål för en iOS-uppdateringsprincip och som har tillgängliga uppdateringar. Du kan se en status för varje enhet och se varför enheten inte har uppdaterats automatiskt. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Visa programskyddets principtilldelningar för felsökning <!--  1475003 -->
I den här kommande versionen kommer alternativet **Appskyddsprincip** att läggas till i listrutan **Tilldelningar** på bladet för felsökning. Nu kan du välja programskyddsprinciper för att se de programskyddsprinciper som tilldelats de valda användarna.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Förbättringar av arbetsflödet för enhetskonfiguration i företagsportalen <!--1490692-->
Vi har förbättrat arbetsflödet för enhetskonfiguration i företagsportalappen för Android. Språket är mer användarvänligt och specifikt för ditt företag, och vi har kombinerat skärmar där det är möjligt. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Förbättrade riktlinjer för begäran om åtkomst till kontakter på Android-enheter <!--1484985-->

Företagsportalappen för Android kräver ofta att slutanvändaren godkänner behörighet för Kontakter. Om en slutanvändare nekar denna åtkomst kommer det nu att visas en avisering i appen som uppmanar till att godkänna det för villkorlig åtkomst. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Reparation av säker start för Android <!--1490712-->

Slutanvändare med Android-enheter kan trycka på orsaken till bristande efterlevnad i företagsportalappen. Om möjligt kommer de då direkt till rätt plats i inställningsappen för att kunna åtgärda problemet. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Ytterligare push-meddelanden för slutanvändare i företagsportalappen för Android Oreo <!--1475932-->

Slutanvändarna ser ytterligare meddelanden som anger när företagsportalen för Android Oreo utför bakgrundsaktiviteter, till exempel när principer hämtas från Intune-tjänsten. Detta ger bättre transparens för slutanvändarna eftersom de ser när företagsportalen utför administrativa uppgifter på deras enheter. Det här är en del av [optimeringen av företagsportalens användargränssnitt](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) för företagsportalappen för Android Oreo. 

Det finns ytterligare optimeringar för nya UI-element som är aktiverade i Android Oreo.  Slutanvändarna ser ytterligare meddelanden som anger när företagsportalen utför bakgrundsaktiviteter, till exempel när principer hämtas från Intune-tjänsten.  Detta ger bättre transparens för slutanvändarna eftersom de ser när företagsportalen utför administrativa uppgifter på deras enheter.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nya funktioner i företagsportalappen för Android med arbetsprofiler <!-- 1485783 -->

När du registrerar en Android for Work-enhet med en arbetsprofil, är det företagsportalappen i arbetsprofilen som utför hanteringsuppgifterna på enheten. 

Såvida du inte använder en MAM-aktiverad app i den personliga profilen, har du inte längre någon användning av företagsportalappen för Android. För att förbättra användningen av arbetsprofilen kommer Intune automatiskt dölja den personliga företagsportalappen efter en lyckad arbetsprofilregistrering.

Företagsportalappen för Android kan aktiveras när som helst i den personliga profilen genom att du bläddrar efter [Företagsportal i Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) och sedan trycker på **Aktivera**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Företagsportal för Windows 8.1 och Windows Phone 8.1 flyttas till hanteringsläget <!--1428681-->

Från oktober 2017 flyttas företagsportalapparna för Windows 8.1 och Windows Phone 8.1 till hanteringsläget. Det innebär att program och befintliga scenarier, till exempel registrering och kompatibilitet, fortsätter att ha stöd för dessa plattformar. De här programmen fortsätter att vara tillgängliga för hämtning via den befintliga versionens kanaler, till exempel Microsoft Store. 

När programmen finns i hanteringsläget kommer de endast kunna ta emot kritiska säkerhetsuppdateringar. Inga ytterligare uppdateringar eller funktioner kommer att släppas för dessa program. Om du vill ha nya funktioner rekommenderar vi att du uppdaterar enheterna till Windows 10 eller Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>Blockera enhetsregistrering med Samsung Knox som inte stöds <!-- 1490695 -->

Företagsportalappen försöker endast att registrera Samsung Knox-enheter som stöds. För att undvika Knox-aktiveringsfel som förhindrar MDM-registrering görs försök att genomföra enhetsregistrering endast om enheten syns i [listan över enheter som har publicerats av Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Samsung-enheter kan ha modellnummer som har stöd för Knox medan andra inte stöds. Kontrollera att Knox är kompatibelt med enhetsåterförsäljaren innan du köper och distribuerar. En fullständig lista över verifierade enheter finns i [Inställningar för Android- och Samsung Knox Standard-principer](/intune/supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Stöd för Android 4.3 och lägre upphör <!-- 1171126, 1326920 -->
Hanterade appar och företagsportalappen för Android kräver Android 4.4 och högre för åtkomst till företagets resurser. I december kommer alla registrerade enheter att tvingas att dras tillbaka, vilket innebär att de förlorar åtkomst till företagets resurser. Om du använder principer för appskydd utan MDM kommer appar inte ta emot uppdateringar och kvaliteten på användningsupplevelsen minskar över tid.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Informera slutanvändarna om vilken enhetsinformation som kan visas på registrerade enheter <!--1165314-->
Vi lägger till **Typ av ägarskap** på skärmen Enhetsinformation i alla företagsportalappar. På så sätt kan användarna få mer information om sekretess direkt från artikeln [Vilken information kan företaget se?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Det här kommer snart att lanseras i alla företagsportalappar. Vi tillkännagav detta för iOS under [september](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).

## <a name="september-2017"></a>September 2017

### <a name="intune-supports-ios-11---1428975--"></a>Intune stöder iOS 11 <!--1428975-->
Intune stöder iOS 11. Det här meddelades tidigare på [Intunes supportblogg](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80----1164477---"></a>Stöd för iOS 8.0 upphör <!-- 1164477 -->
Hanterade appar och företagsportalappen för iOS kräver iOS 9.0 och högre för åtkomst till företagets resurser. Enheter som inte är uppdaterade innan september kommer inte längre att ha åtkomst till Företagsportalen eller apparna. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Uppdateringsåtgärden lades till i företagsportalappen för Windows 10 <!--1132468-->
Företagsportalappen för Windows 10 tillåter att användarna uppdaterar data i appen genom att antingen dra för att uppdatera eller trycka på F5 på stationära datorer.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informera användarna vilken enhetsinformation som kan visas för iOS <!--739894-->

Vi har lagt till **Typ av ägarskap** på skärmen Enhetsinformation i företagsportalappen för iOS. På så sätt kan användarna få mer information om sekretess direkt från den här sidan från Intunes slutanvändardokumentation. De kan även hitta denna information på skärmen Om.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Tillåt att slutanvändare får åtkomst till företagsportalappen för Android utan registrering <!---1169910--->

Slutanvändare behöver snart inte att registrera sina enheter för att komma åt företagsportalappen för Android. Slutanvändare i organisationer som använder principer för appskydd får inte längre uppmaningar att registrera sina enheter när de öppnar företagsportalen. Slutanvändarna kommer också att kunna installera appar från företagsportalen utan att registrera sina enheter. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Enklare formuleringar i företagsportalappen för Android <!---1396349--->  

Registreringen av företagsportalappen för Android har förenklats med ny text för att göra det enklare för slutanvändarna att registrera. Om du har anpassad registreringsdokumentation bör du uppdatera den så att den återspeglar de nya skärmarna. Du hittar exempelbilder på sidan om [uppdateringar i användargränssnittet för Intunes slutanvändarappar](whats-new-app-ui.md#week-of-september-11-2017) page.

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 10-företagsportalappen lades till i Windows informationsskydd för att tillåta principen <!-- 677129 -->

Företagsportalappen för Windows 10 har uppdaterats så att den stöder Windows Information Protection (WIP). Programmet kan läggas till i den tillåtna WIP-principen. Med den här ändringen behöver programmet inte längre läggas till i listan **Undantag**.


## <a name="august-2017"></a>Augusti 2017

### <a name="improvements-to-device-overview----1404453---"></a>Förbättringar av enhetsöversikt <!-- 1404453 -->  
Förbättringar av enhetsöversikt visar nu registrerade enheter, men inte enheter som hanteras av Exchange ActiveSync. Exchange ActiveSync-enheter har inte samma hanteringsalternativ som registrerade enheter. Om du vill se antalet registrerade enheter och antalet registrerade enheter efter plattform går du till **enheter** > **översikt** i Intune i Azure Portal.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Förbättringar av enhetsinventering som samlas in av Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
I den här versionen har vi gjort följande förbättringar i inventeringsinformationen som samlas in av de enheter som du hanterar:
 
-   För Android-enheter kan du nu lägga till en kolumn i enhetsinventeringen som visar den senaste korrigeringsnivån för varje enhet. Lägg till kolumnen med **säkerhetskorrigeringsnivån** i enhetslistan för att se detta.
-   När du filtrerar enhetsvyn kan du nu filtrera enheter efter deras registreringsdatum. Du kan till exempel endast visa de enheter som har registrerats efter ett angivet datum.
-   Vi har gjort förbättringar för filter som används av objektet **Last Check-in Date** (Senaste incheckningsdatum).
-   I enhetslistan kan du nu visa telefonnummer för företagsägda enheter.
Du kan dessutom använda filterfönstret för att söka efter enheter efter telefonnummer.
 
Mer information om enhetsinventering finns i [Så här visar du Intunes enhetsinventering](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Stöd för villkorlig åtkomst på macOS-enheter 
<!-- 720172 -->
Nu kan du skapa en princip för villkorlig åtkomst som kräver att Mac-enheter ska vara registrerade i Intune och kompatibla med dess efterlevnadsprinciper för enheter. Användarna kan till exempel ladda ned appen för Intune-företagsportalen på macOS och registrera sina Mac-enheter i Intune. Intune utvärderar om Mac-enheten följer standard eller inte med krav som PIN, kryptering, OS-version och systemintegritet.

- Läs mer om [stöd för villkorlig åtkomst på macOS-enheter](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>Företagsportalappen för macOS är tillgänglig som förhandsversion <!---1484796--->
Företagsportalappen för macOS är nu tillgänglig som en del av den allmänt tillgängliga förhandsversionen för villkorlig åtkomst i Enterprise Mobility + Security. Den här versionen stöder macOS 10.11 och högre. Hämta den på [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Inställningar för enhetsbegränsningar för Windows 10    
<!--1063965, 1308850  -->
I den här versionen har vi lagt till nya inställningar för [begränsningsprofilen för Windows 10-enheter](/intune/device-restrictions-windows-10). Nyheterna finns i följande kategorier:

-   Windows Defender SmartScreen
-   Appbutik

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Uppdateringar för BitLocker-inställningar för enhetsprofiler för Windows 10 Endpoint Protection
<!--1459533 -->    
I den här versionen har vi gjort följande förbättringar för hur BitLocker-inställningar fungerar i en enhetsprofil för Windows 10 Endpoint Protection:
 
När du tidigare valde **Blockera** för inställningen **BitLocker med icke kompatibelt TPM-chip** under **Inställningar för BitLocker-operativsystemenhet** gjorde detta tidigare att BitLocker ändå tilläts. Vi har nu löst problemet och BitLocker blockeras nu när det är markerat.
För inställningen **certifikatbaserad dataåterställningsagent** under **Inställningar för BitLocker-operativsystemenhet** kan du nu uttryckligen blockera den certifikatbaserade dataåterställningsagenten. Som standard tillåts agenten.
För inställningen **Dataåterställningsagent** under **Inställningar för fast BitLocker-dataenhet** kan du nu uttryckligen blockera dataåterställningsagenten.
Mer information finns i [Endpoint Protection-inställningar för Windows 10 och senare](endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Ny inloggad upplevelse för användare av Android-företagsportalen och appskyddsprincip <!-- 621669 -->
Slutanvändarna kan nu bläddra bland appar, hantera enheter och visa it-kontaktinformation med hjälp av Android-företagsportalappen utan att registrera sina Android-enheter. Om en användare dessutom redan använder en app som skyddas av principer för Intune-appskydd och startar Android-företagsportalen får slutanvändaren inte längre någon uppmaning att registrera enheten.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Ny inställning i Android-företagsportalappen för att ändra batterioptimering <!--1405990-->
Sidan **Inställningar** i företagsportalappen för Android har en ny inställning som gör det enkelt för användarna att stänga av batterioptimering för företagsportalen och Microsoft Authenticator-appar. Appnamnet som visas i inställningen beror på vilken app som hanterar arbetskontot. Vi rekommenderar att användarna stänger av batterioptimering för att få bättre prestanda med arbetsappar som synkroniserar e-post och data. 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Stöd för flera identiteter med OneNote för iOS...<!-- 1234281 -->
Slutanvändare kan nu använda olika konton (arbete och personliga) med Microsoft OneNote för iOS. Programskyddsprinciper kan tillämpas på företagsdata i arbetsanteckningsböcker utan att de personliga anteckningsböckerna påverkas. En princip kan till exempel tillåta en användare att söka efter information i anteckningsböcker för arbete, men användaren kan inte kopiera och klistra in företagets data från anteckningsboken för arbete till en personlig anteckningsbok.
 
- Mer information om appar som stöder [appskydd och multiidentitet](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) med Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nya inställningar för att tillåta och blockera appar på Samsung Knox Standard-enheter
<!-- 1305423 822899-->  
Den här versionen innehåller nya [inställningar för enhetsbegränsning](device-restrictions-android.md) som du kan använda för att ange följande applistor:
 
- Appar som användare tillåts att installera
- Appar som användare är blockerade från att installera
- Appar som är dolda från användaren på enheten
 
Du kan ange appen med hjälp av URL, paketnamn eller från listan över appar som du hanterar.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Ny gränssnittslänk för princip för appbaserad villkorlig åtkomst för Azure AD från Intune
<!-- 1016201 -->
IT-administratörer kan nu ange appbaserade villkorsprinciper via det nya gränssnittet för villkorlig åtkomstprincip i Azure AD-arbetsbelastningen. Den appbaserade villkorliga åtkomsten som finns i avsnittet Intune-appskydd i Azure Portal finns kvar där för tillfället och tillämpas sida vid sida. Det finns även en praktisk länk till det nya gränssnittet för villkorlig åtkomstprincip i Intune-arbetsbelastningen.

- Läs mer om [appbaserad villkorlig åtkomst i Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## <a name="july-2017"></a>Juli 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Begränsa Android- och iOS-enhetsregistrering per OS-version <!--- 1333256,  1245463 --->
Intune har nu stöd för att begränsa iOS- och Android-registrering efter operativsystemets versionsnummer. Under **Begränsning för enhetstyp** kan IT-administratören nu konfigurera en plattformskonfiguration som begränsar registrering mellan ett lägsta och högsta operativsystemsvärde. Versionerna för Android-operativsystemet måste anges som Major.Minor.Build.Rev, där Minor, Build och Rev är valfria. iOS-versionerna måste anges som Major.Minor.Build, där Minor och Build är valfria. Läs mer om [enhetsregistreringsbegränsningar](enrollment-restrictions-set.md).

>[!NOTE]
>Begränsar inte registrering via Apples registreringsprogram eller Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Begränsa registrering av personligt ägda Android-, iOS- macOS-enheter <!--- 1333272,  1333275, 1245709 --->
Intune kan begränsa registrering av personliga enheter genom att skapa en lista över tillåtna IMEI-nummer för företagsenheter. Intune har nu expanderat den här funktionen till iOS, Android och macOS med hjälp av enhetsserienummer. Genom att ladda upp serienumren till Intune kan du fördeklarera enheter som företagsägda. Med begränsningar för registrering kan du blockera personligt ägda enheter (BYOD) och endast tillåta registrering av företagsägda enheter. Läs mer om [enhetsregistreringsbegränsningar](enrollment-restrictions-set.md).

Om du vill importera serienummer går du till **Enhetsregistrering** > **ID:n för företagsenheter** och klickar på **Lägg till**. Sedan laddar du upp en. CSV-fil (ingen rubrik, två kolumner för serienummer och detaljer som IMEI-nummer).  Om du vill begränsa personligt ägda enheter, går du till **Enhetsregistrering** > **Registreringsbegränsningar**. Under **Begränsningar av enhetstyp** väljer du **Standard** och sedan **Plattformskonfigurationer**. Du kan **Tillåta** eller **Blockera** personligt ägda iOS-, Android- och macOS-enheter. 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Ny enhetsåtgärd för att tvinga enheter att synkronisera med Intune <!-- 711369 -->
I den här versionen har vi lagt till en ny enhetsåtgärd som tvingar den valda enheten att omedelbart checka in med Intune. När en enhet checkar in tar den omedelbart emot eventuella väntande åtgärder eller principer som har tilldelats till den.  Den här åtgärden kan hjälpa dig att validera och felsöka principer som du har tilldelat utan att du behöver vänta på nästa schemalagda incheckning.
Mer information finns i [Synkronisera enheten](device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen <!-- 777100 -->
En ny princip är tillgänglig från arbetsytan Programuppdateringar där du kan tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga programuppdateringen. Mer information finns i [Konfigurera iOS-uppdateringsprinciper](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile – Ny partner för skydd mot mobilhot <!-- 954651, 1172027 -->
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst baserat på riskbedömning som utförs av Checkpoint SandBlast Mobile, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Hur fungerar integrering med Intune?
Risken bedöms utifrån telemetri som samlas in från enheter som kör Checkpoint SandBlast Mobile. Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Checkpoint SandBlast Mobiles riskbedömning som aktiveras via Intunes principer för enhetsefterlevnad. Du kan tillåta eller blockera inkompatibla enheters åtkomst till företagets resurser utifrån identifierade hot.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Distribuera en app som tillgänglig i Microsoft Store för företag <!-- 748101 -->
Med den här versionen kan administratörer nu ställa in Microsoft-Store för företag som tillgänglig. Slutanvändarna kan installera appen från företagsportalappen eller webbplatsen utan att dirigeras om till Microsoft-Store när den är inställd som tillgänglig.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Gränssnittsuppdateringar på företagsportalswebbplatsen <!--1313244 part 1-->
Vi har gjort flera uppdateringar i gränssnittet för [företagsportalswebbplatsen](https://portal.manage.microsoft.com) för att förbättra användarupplevelsen.

- __Förbättringar av appaneler__: Appikoner visas nu med en automatiskt genererad bakgrund som baseras på ikonens huvudsakliga färg (om den kan identifieras). När tillämpligt ersätter den här bakgrunden den grå kantlinje som tidigare fanns på appanelerna.

    Företagsportalens webbplats visar stora ikoner när det är möjligt i en kommande version. Vi rekommenderar att IT-administratörer publicerar appar med högupplösta ikoner som har en storlek på minst 120 x120 pixlar. 

- __Navigeringsändringar__: Objekt i navigeringsraden har flyttats till menyn längst upp till vänster. Sidan Kategorier har tagits bort. Användarna kan nu filtrera innehåll efter kategori när de bläddrar.

- __Uppdateringar av aktuella appar__: Vi har lagt till en särskild sida på webbplatsen där användarna kan bläddra bland appar som du har valt att presentera och vi har gjort några gränssnittsförändringar på avsnittet Aktuella på startsidan.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Stöd för iBooks på Företagsportalens webbplats <!--1231841-->
Vi har lagt till en särskild sida på Företagsportalens webbplats där användare kan bläddra och hämta iBooks. 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Ytterligare information om felsökning för supportavdelningen<!---  Applies to 1263399, 1326964, 1341642 --->
Intune har uppdaterat felsökningsskärmen och lagt till information för administratörer och supportpersonal. Nu visas tabellen **Tilldelningar** med en sammanfattning av alla användarens tilldelningar baserat på gruppmedlemskap. Listan innehåller:
- Mobilappar
- Efterlevnadsprinciper
- Konfigurationsprofiler
 
Tabellen **Enheter** innehåller nu även kolumnerna **Azure AD-anslutningstyp** och **Azure AD-kompatibel**. Mer information finns i [hjälpa användare att felsöka problem](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Intune-informationslager (Allmänt tillgänglig förhandsversion)
Intune-informationslagret samplar data dagligen och visar historik över din klient. Du kan komma åt data med en Power BI-fil (PBIX), en OData-länk som är kompatibel med många analytiska verktyg eller genom att interagera med REST API. Mer information finns i [Använd Intune-informationslagret](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Ljust och mörkt läge är tillgängligt för företagsportalappen för Windows 10 <!---676547--->
Slutanvändare kan anpassa färgläget för företagsportalappen för Windows 10. Användaren kan göra ändringarna i avsnittet Inställningar i företagsportalappen. Ändringen tillämpas när användaren har startat om appen. För Windows 10 version 1607 och senare kommer standardläget för appen bero på systeminställningen. För Windows 10 version 1511 och tidigare kommer standardläget för appen vara det ljusa läget.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Gör det möjligt för slutanvändare att tagga sin enhetsgrupp i företagsportalappen för Windows 10 <!---807046-->
Slutanvändare kan nu välja vilken grupp deras enhet tillhör genom att tagga den direkt från företagsportalappen för Windows 10.



## <a name="june-2017"></a>Juni 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Ny rollbaserad administrationsåtkomst för Intune-administratörer <!-- 1099990 -->  
En ny administratörsroll för villkorlig åtkomst läggs till för att kunna visa, skapa, ändra och ta bort Azure AD:s villkorliga åtkomstprinciper. Tidigare hade endast globala administratörer och säkerhetsadministratörer den här behörigheten. Intune-administratörer kan tilldelas den här rollbehörigheten så att de får åtkomst till principer för villkorlig åtkomst.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Tagga företagsägda enheter med serienummer <!-- 1215070 -->  
Intune stöder nu uppladdning av iOS-, macOS- och Android-serienummer som identifierare för företagsägda enheter. Du kan inte använda serienummer för att blockera personliga enheter från registrering än, eftersom serienummer inte verifieras under registreringen. Blockering av personliga enheter med serienummer kommer att kunna göras inom en snar framtid.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nya fjärråtgärder för iOS-enheter <!-- 854689 -->
I den här versionen har vi lagt till två nya fjärråtgärder som hanterar Apple Classroom-appen på delade iPad-enheter:

-   [Logga ut aktuell användare](device-logout-user.md) – Loggar ut den aktuella användaren av den valda iOS-enheten.
-   [Ta bort användare](device-remove-user.md) – Tar bort en vald användare från den lokala cachen på en iOS-enhet.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Stöd för delade iPad-enheter med iOS Klassrum-appen <!-- 1044681 -->
Från och med den här versionen har vi utökat stödet för hantering av Klassrum-appen i iOS, så att vi kan inkludera elever som loggar in på delade iPad-enheter med sina hanterade Apple-ID:n.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Ändringar i Intunes inbyggda appar<!-- 1332306 -->
Tidigare innehöll Intune ett antal inbyggda appar för snabb tilldelning. Efter feedback från användarna har vi beslutat oss för att ta bort listan och dess inbyggda appar visas inte längre.
Om du har redan har tilldelat några inbyggda appar kommer dessa även i fortsättningen att finnas kvar i listan över appar. Du kan fortsätta att tilldela dessa appar vid behov.
I en senare version planerar vi att lägga till en enklare metod för att välja och tilldela inbyggda program från Azure-portalen.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Enklare installation av Office 365-appar <!--- 1121362 --->
Med den nya **Office 365 ProPlus**-appen kan du enkelt tilldela Office 365 ProPlus 2016-appar till enheter som du hanterar och som kör den senaste versionen av Windows 10. Dessutom kan du installera Microsoft Project och Microsoft Visio om du har licenser för dem. Appar som du vill använda paketeras tillsammans och visas som en enda app i listan med appar i Intune-konsolen.
Läs mer i informationen om [hur du lägger till Office 365-appar för Windows 10](apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Stöd för offline-appar från Microsoft Store för företag <!--- 777044 --->
Offline-program som du köpt från Microsoft Store för företag kommer nu att synkroniseras med Azure-portalen. Du kommer sedan att kunna distribuera apparna till enhetsgrupper eller användargrupper. Offline-appar installeras av Intune och inte av butiken.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft Teams finns nu på den appbaserade listan över godkända appar<!-- 1257019 -->
Microsoft Teams-appen för iOS och Android finns nu på listan över godkända appar för appbaserade villkorliga åtkomstprinciper för Exchange och SharePoint Online. Appen kan konfigureras via bladet för Intune-appskydd i Azure-portalen för alla klienter som för tillfället använder appbaserad villkorlig åtkomst.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Integrering av Managed Browser och programproxy <!-- 1287310 -->
Intune Managed Browser kan nu integreras med programproxy för Azure AD, så att användarna kan komma åt interna webbplatser även när de arbetar på distans. Användarna anger webbadressen i webbläsaren precis som vanligt. Managed Browser skickar begäran via programproxyns webbgateway. Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper](app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nya appkonfigurationsinställningar för Intune Managed Browser <!-- 682951 -->
I den här versionen har vi lagt till fler konfigurationer för Intune Managed Browser-appen för iOS och Android. Du kan nu använda en appkonfigurationsprincip för att konfigurera standardstartsidan och bokmärken i webbläsaren.
Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper](app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>BitLocker-inställningar för Windows 10 <!-- 951707 -->
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
-  Microsoft Edge-webbläsare

Mer information om inställningar för Windows 10 finns i [Begränsningsinställningar för enheter med Windows 10 och senare](device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Företagsportalappen för Android har nu ett nytt användargränssnitt för appskyddsprinciper <!--1305217-->
Baserat på feedback från våra kunder har vi ändrat företagsportalappen för Android så att den visar knappen **Åtkomst till företagsinnehåll**. Avsikten är att förhindra användare från att i onödan gå genom registreringsprocessen när de bara behöver åtkomst till appar som stöder appskyddsprinciper, en funktion i Intune för hantering av mobilappar. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Ny menyåtgärd för att enkelt ta bort Företagsportalen <!--1164569-->
Baserat på användarfeedback har vi lagt till en ny menyåtgärd i företagsportalen för Android för att ta bort den från din enhet. Den här åtgärden tar bort enheten från Intune-hanteringen så att användaren kan ta bort appen från enheten. Du kan se dessa ändringar på sidan [Vad är nytt i appens gränssnitt](whats-new-app-ui.md) och i [bruksanvisningen för din Android-enhet](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Förbättringar av appsynkronisering med Windows 10 Creators Update <!--676505-->
Företagsportalen för Windows 10 kommer automatiskt att initiera en synkronisering för appinstallationsbegäranden för enheter med Windows 10 Creators Update (1703). Detta minskar problemen där appen fastnar vid tillståndet ”Väntar på synkronisering” när installationer utförs. Dessutom kommer användare att kunna initiera en synkronisering från appen manuellt. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Ny guidad upplevelse för Windows 10-företagsportalen <!---1058938--->
Företagsportalappen för Windows 10 kommer att innehålla en guidad Intune-genomgång för enheter som inte har identifierats eller registrerats. Den nya guiden innehåller stegvisa anvisningar som hjälper användaren att utföra AAD-registrering (krävs för villkorliga åtkomstfunktioner) och MDM-registrering (krävs för enhetshanteringsfunktioner). Guiden kommer att vara tillgänglig på företagsportalens startsida. Användarna kan fortsätta att använda appen även om de inte slutför registreringen, men de får begränsad funktionalitet.

Den här uppdateringen visas bara på enheter som kör Windows 10 Anniversary Update (version 1607) eller senare. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Administratörskonsoler till Microsoft Intune och villkorlig åtkomst är allmänt tillgängliga
Vi kommer att göra nya Intune i Azure-administrationskonsolen och administrationskonsolen för villkorlig åtkomst allmänt tillgängliga. Via Intune i Azure-portalen kan du nu hantera alla Intune MAM- och MDM-funktioner i en konsoliderad administratörsmiljö och använda Azure AD-gruppering och -mål. Villkorlig åtkomst i Azure ger de avancerade funktionerna i Azure AD och Intune tillsammans i en enhetlig konsol. Och från ett administrativt perspektiv innebär övergången till Azure-plattformen att du kan använda moderna webbläsare.

Intune visas nu utan etiketten **preview** i Azure-portalen på portal.azure.com.

Det krävs ingen åtgärd för befintliga kunder just nu, om du inte har tagit emot en av en serie meddelanden i meddelandecentret om att vidta åtgärder så att vi kan migrera dina grupper. Du kan också ha fått ett meddelande i meddelandecentret som informerar dig om att migreringen tar längre tid på grund av programfel på vår sida. Vi arbetar hårt på att migrera alla berörda kunder.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Förbättringar av appaneler i företagsportalappen för iOS
Vi har uppdaterat designen av appaneler på startsidan så att de återspeglar anpassningsfärgen som du angett för Företagsportalen. Mer information finns i [nyheter i appgränssnittet](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Kontoväljaren finns nu tillgänglig för företagsportalappen för iOS
Användare av iOS-enheter kan se vår nya kontoväljare när de loggar in på företagsportalen om de använder sitt arbets- eller skolkonto för att logga in på andra Microsoft-appar. Mer information finns i [nyheter i appgränssnittet](whats-new-app-ui.md).

## <a name="may-2017"></a>Maj 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Ändra din utfärdare för hantering av mobila enheter utan att avregistrera hanterade enheter <!--1103950-->
Du kommer att kunna ändra din utfärdare för hantering av mobila enheter utan att behöva kontakta Microsoft Support och utan att behöva avregistrera och omregistrera dina befintliga hanterade enheter. I Configuration Manager-konsolen kan du [ändra utfärdare för hantering av mobila enheter](/sccm/mdm/deploy-use/change-mdm-authority) från Ange till Configuration Manager (hybrid) till Microsoft Intune (fristående) eller vice versa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Förbättrat meddelande för PIN-koder vid start av Samsung Knox <!--1087143-->
När användarna måste ange en PIN-kod för start på Samsung Knox-enheter för att bli kompatibla med kryptering, visas meddelandet för användarna. De kommer till rätt plats i appen Inställningar när de trycker på meddelandet.  Meddelandet tog tidigare användaren till skärmen där lösenord ändras.

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
Vissa Android-appar från webbutiken stöder hanterade konfigurationsalternativ som gör att en IT-administratör kan kontrollera hur appen körs i en arbetsprofil. Med Intune kan du nu se de konfigurationer som stöds av ett program och konfigurera dem från Azure-portalen med en konfigurationsdesigner eller en JSON-redigerare. Mer information finns i [Använda appkonfigurationer för Android for Work](app-configuration-policies-use-android.md).

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
När skapar en SCEP certifikatet profil för <strong>Ämnesnamnets format</strong>, <strong>Anpassad</strong> alternativet är tillgängligt för iOS, Android och Windows-enheter. Innan den här uppdateringen var fältet <strong>Anpassad</strong> endast tillgängligt för iOS-enheter. Mer information finns i [Skapa en SCEP-certifikatprofil](certificates-scep-configure.md#create-a-scep-certificate-profile).

När du skapar en PKCS-certifikatprofil för **Alternativt ämnesnamn** är **attributet anpassad Azure AD** tillgängligt. Alternativet **Avdelning** är tillgängligt när du väljer **attributet anpassad Azure AD**. Mer information finns i [så här skapar du en PKCS-certifikatprofil](certficates-pfx-configure.md#create-a-device-configuration-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Konfigurera flera appar som kan köras när en Android-enhet är i helskärmsläge <!-- 662059 -->
När en Android-enhet är i helskärmsläge, kunde du tidigare endast konfigurera en app som hade tillstånd att köras. Nu kan du konfigurera flera appar med hjälp av app-ID, lagrings-URL eller genom att välja en Android-app som du redan hanterar. Mer information finns i [helskärmsinställningar](device-restrictions-android.md#kiosk).



## <a name="april-2017"></a>April 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Stöd för hantering av Apples Klassrum-app
Du kan nu hantera iOS Klassrum-app på iPad-enheter. Konfigurera Klassrum-appen på lärarens iPad med rätt klass- och elevinformation, konfigurera sedan elevernas iPad-enheter som är registrerade till en klass, så att du kan kontrollera dem med hjälp av appen.
Mer information finns i [Konfigurera utbildningsinställningar för iOS](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Stöd för hanterade konfigurationsalternativ för Android-appar <!-- 621621 -->
Android-appar i Play Store som har stöd för hanterade konfigurationsalternativ kan nu konfigureras av Intune.  Med hjälp av den här funktionen kan IT-personal visa listan över konfigurationsvärden som stöds av en app, vilket ger ett tydligt gränssnitt som gör det möjligt att konfigurera dessa värden.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Ny Android-princip för komplexa PIN-koder <!-- 722069 -->
Du kan ange den obligatoriska [lösenords](device-restrictions-android.md#password)typen Numeriskt avancerat i en Android-enhetsprofil för enheter som kör Android 5.0 och senare.  Använd den här inställningen för att hindra att enhetsanvändare skapar en PIN-kod som innehåller upprepande eller efterföljande siffror, t.ex. 1111 eller 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Ytterligare stöd för Android for Work-enheter
- **Hantera inställningar för lösenord och arbetsprofil** <!-- 612808 -->

  Med den här nya enhetsbegränsningsprincipen för Android for Work kan du nu hantera inställningar för lösenord och arbetsprofil på de Android for Work-enheter som du hanterar.

- **Tillåt datadelning mellan arbetsprofiler och personliga profiler** <!-- 1045102 -->

Den här enhetsbegränsningsprofilen för Android for Work har nu nya alternativ som hjälper dig att konfigurera datadelning mellan arbetsprofiler och personliga profiler.

- **Begränsa kopiera och klistra in mellan arbetsprofiler och personliga profiler** <!-- 1046094 -->

  En ny anpassad enhetsprofil för Android for Work-enheter gör det nu möjligt att begränsa om åtgärderna för att kopiera och klistra in mellan arbetsappar och personliga appar ska vara tillåtna.

Mer information finns i [Enhetsbegränsningar för Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Tilldela branschspecifika appar till iOS- och Android-enheter <!-- 1057568 -->
Du kan nu tilldela branschspecifika appar för [iOS](lob-apps-ios.md) (.ipa-filer) och [Android](lob-apps-android.md) (.apk-filer) till användare eller enheter.


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nya enhetsprinciper för iOS <!-- 723774, 723815, 723826, 723830 -->
- **Appar på startskärmen** – Styr vilka appar användarna ser på [startskärmen på sina iOS-enheter](home-screen-settings-ios.md). Den här principen ändrar layouten på startsidan, men distribuerar inga appar.

- **Anslutningar till AirPrint-enheter** – Styr vilka [AirPrint-enheter](air-print-settings-ios-macos.md) (nätverksskrivare) som användarna av iOS-enheter kan ansluta till.

- **Anslutningar till AirPlay-enheter** – Styr vilka [AirPlay-enheter](airplay-settings-ios.md) (t.ex. Apple TV) som användarna av iOS-enheter kan ansluta till.

- **Anpassat meddelande på låsskärmen** – Konfigurerar ett anpassat meddelande som ersätter det standardmeddelande som användarna ser på låsskärmen på sina iOS-enheter. Mer information finns i [Aktivera borttappat läge på iOS-enheter](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Begränsa push-meddelanden för iOS-appar <!-- 723767 -->
Du kan nu konfigurera följande [aviseringsinställningar](app-notification-settings-ios.md) för iOS-enheter i en begränsningsprofil för Intune-enheter:

- Aktivera eller inaktivera aviseringar helt för en angiven app.
- Aktivera eller inaktivera aviseringar i aviseringscentret för en angiven app.
- Ange aviseringstypen, antingen **Ingen**, **Banderoll** eller **Modal avisering**.
- Ange om aktivitetsikoner tillåts för den här appen.
- Ange om aviseringsljud tillåts.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Konfigurera iOS-appar för att köras i autonomt enkelappsläge <!-- 737837 -->
Du kan nu använda en Intune-enhetsprofil för att konfigurera iOS-enheter till att köra angivna appar i [autonomt enkelt appläge](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). När det här läget är konfigurerat och appen körs kommer enheten att låsas så att den endast kan köra den appen. Ett exempel på detta är när du konfigurerar en app som gör att användarna kan genomföra ett test på enheten. När appens åtgärder har slutförts, eller om du tar bort principen, återgår enheten till sitt normala tillstånd.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Konfigurera betrodda domäner för e-post och webbläsare på iOS-enheter <!-- 723765 -->
Du kan nu konfigurera följande [domäninställningar](device-restrictions-ios.md#domains) i en begränsningsprofil för iOS-enheter:

- **Omarkerade e-postdomäner** – E-postmeddelanden som användaren skickar eller tar emot och som inte matchar de domäner du anger här, markeras som icke tillförlitliga.

- **Hanterade webbdomäner** – Dokument som laddats ned från de webbadresser du anger här betraktas som hanterade (endast Safari).  

- **Fyll i lösenord automatiskt för Safari-domäner** – Användare kan spara lösenord endast i Safari från URL:er som matchar de mönster du anger här. Om du vill använda den här inställningen måste enheten vara i övervakat läge och får inte vara konfigurerad för flera användare. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>VPP-appar som är tillgängliga i iOS-företagsportalen <!-- 748782 -->
Du kan nu tilldela volyminköpsappar för iOS som **Tillgängliga** installationer till användarna. Användarna behöver ett Apple Store-konto för att installera appen.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Synkronisera e-böcker från Apple VPP Store <!-- 800878 -->
Du kan nu [synkronisera böcker](vpp-apps-ios.md) som du har köpt från Apples butik för volyminköpsappar med Intune och tilldela dem till användarna.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Hantering av flera användare för Samsung Knox Standard-enheter <!-- 971988 -->
Enheter som kör Samsung Knox Standard har nu stöd för [hantering av flera användare](android-enroll.md) i Intune. Det innebär att slutanvändarna kan logga in och ut från enheten med sina autentiseringsuppgifter för Azure Active Directory, och enheten hanteras centralt oavsett om den används eller inte.  När slutanvändare loggar in så får de tillgång till appar och eventuella principer tillämpas på dem. Alla appdata rensas när användaren loggar ut.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Ytterligare begränsningsinställningar för Windows-enheter <!-- 818566 -->
Vi har lagt till stöd för fler [begränsningsinställningar för Windows-enheter](device-restrictions-windows-10.md), t.ex. ytterligare Edge-webbläsarstöd, anpassning av enhetens låsskärm, anpassning av startmenyn, bakgrund för Windows Spotlight-sökning och proxyinställningar.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Stöd för flera användare för Windows 10 Creators Update <!-- 822547 -->
Vi har lagt till stöd för [hantering av flera användare](windows-enroll.md) för enheter som kör Windows 10 Creators-uppdateringen och som är domänanslutna med Azure Active Directory. Det innebär att när olika standardanvändare loggar in på enheten med sina autentiseringsuppgifter för Azure AD, får de alla appar och principer som har tilldelats till deras användarnamn. Användare kan för närvarande inte använda Företagsportalen för självbetjäningsscenarier som att installera appar.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start för Windows 10-datorer<!-- 1004830 -->
En ny [Fresh Start-enhetsåtgärd](device-fresh-start.md) för Windows 10-datorer finns nu tillgänglig.  När du kör den här åtgärden tas alla appar som har installerats på datorn bort, och datorn uppdateras automatiskt till den senaste Windows-versionen. Detta kan användas för att ta bort förinstallerade OEM-appar som ofta levereras med en ny dator. Du kan konfigurera om användardata ska behållas när den här enhetsåtgärden utförs.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Ytterligare uppgraderingsvägar i Windows 10 <!-- 903672 -->
Nu kan du skapa en [uppgraderingsprincip för utgåvor för att uppgradera enheter](edition-upgrade-configure-windows-10.md) till följande Windows 10-utgåvor:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Massregistrera Windows 10-enheter <!-- 747607 -->
Nu kan du ansluta ett stort antal enheter som kör Windows 10 Creators-uppdateringen till Azure Active Directory och Intune med Windows Configuration Designer (WCD). Aktivera [MDM-massregistrering](windows-bulk-enroll.md) för din Azure AD-klient genom att skapa ett konfigurationspaket som ansluter enheter till din Azure AD-klient med hjälp av Windows Configuration Designer. Tillämpa sedan paketet på de företagsägda enheter som du vill massregistrera och hantera. När paketet har tillämpats på dina enheter kommer de anslutas till Azure AD, registreras i Intune och vara redo för att Azure AD-användarna ska logga in.  Azure AD-användare är standardanvändare på de här enheterna och tar emot tilldelade principer och nödvändiga appar. Självbetjäning och företagsportalscenarier stöds inte för närvarande.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nya MAM-inställningar för PIN-kod och hanterade lagringsplatser <!-- 581122, 736644 -->
Det finns nu två nya appinställningar som hjälper dig med scenarier för hantering av mobilprogram (MAM):

- **Inaktivera app-PIN när enhets-PIN är hanterad** – Identifierar om det finns en enhets-PIN på den registrerade enheten och förbigår i så fall den app-PIN som utlöses av appskyddsprinciperna. Den här inställningen minskar antalet gånger en PIN-uppmaning visas för användare som öppnar ett MAM-aktiverat program på en registrerad enhet. Den här funktionen är tillgänglig för både Android och iOS.

- **Välj med vilka lagringstjänster företagsdata ska sparas** – Gör det möjligt att ange de lagringsplatser där företagsdata ska sparas. Användare kan spara i valda lagringsplatstjänster, vilket innebär att alla lagringsplatstjänster som inte anges kommer att blockeras.

  Lista över lagringsplatstjänster som stöds:

  - OneDrive
  - Business SharePoint Online
  - Lokal lagring

### <a name="help-desk-troubleshooting-portal----907448---"></a>Supportavdelningens felsökningsportal <!-- 907448 -->
Med den nya [felsökningsportalen](help-desk-operators.md) kan supportansvariga och Intune-administratörer se användarna och deras enheter, samt utföra åtgärder för att lösa tekniska problem i Intune.

## <a name="march-2017"></a>Mars 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Stöd för iOS borttappat läge <!--431695-->
För iOS 9.3-enheter och senare har Intune lagt till stöd för **Borttappat läge**. Nu kan du låsa en enhet för att förhindra all användning och visa ett meddelande och ett telefonnummer på enhetens låsskärm.

Användaren kommer inte att kunna låsa upp enheten förrän en administratör har inaktiverat borttappat läge. När Borttappat läge har aktiverats kan du använda åtgärden **Hitta enhet** för att visa enhetens geografiska plats på en karta i Intune-konsolen.

Enheten måste vara en företagsägd iOS-enhet, registrerad med DEP, som är i övervakat läge.

Mer information finns i [Vad är Microsoft Intune-enhetshantering](device-management.md)?

### <a name="improvements-to-device-actions-report---677150--"></a>Förbättringar av rapporten Enhetsåtgärder<!--677150-->
Vi har förbättrat rapporten Enhetsåtgärder för att förbättra dess prestanda. Nu kan du filtrera rapporten efter tillstånd. Exempelvis kan du filtrera rapporten för att endast visa enhetsåtgärder som har slutförts.

### <a name="custom-app-categories---748805--"></a>Anpassade appkategorier <!--748805-->
Du kan nu skapa, redigera och tilldela kategorier för appar som du lägger till i Intune. Kategorier kan för närvarande kan bara anges på engelska.
Läs [How to add an app to Intune](apps-add.md) (Lägga till en app i Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Tilldela LOB-appar till användare med oregistrerade enheter <!--748823-->
Du kan nu tilldela branschspecifika appar och appar från butiken till användare, oavsett om deras enheter är registrerade i Intune eller inte. Om användarens enhet inte har registrerats i Intune måste användaren gå till företagsportalens webbplats, inte dess app, för att installera den.

### <a name="new-compliance-reports---846671--"></a>Nya efterlevnadsrapporter <!--846671-->
Nu har du efterlevnadsrapporter som ger ditt företags enheters efterlevnadsprofil och låter dig felsöka problem som berör efterlevnad snabbt efter hand som de upptäcks av dina användare. Du kan visa information om

- Övergripande efterlevnadstatus för enheter
- Efterlevnadstatus för en enskild inställning
- Efterlevnadstatus för en enskild princip

Du kan även använda dessa rapporter för att undersöka en individuell enhet på djupet för att se de inställningar och principer som påverkar enheten.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->
För Intune-konton som skapades efter januari 2017 har Intune aktiverat direktåtkomst till registreringsscenarier i Apple med arbetsflödet Registrera enheter i Azure-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i Azure-portalen. Intune-konton som skapats före januari 2017 behöver migreras vid ett tillfälle innan de här funktionerna finns tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till förhandsversionen.


## <a name="february-2017"></a>Februari 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Möjlighet att begränsa registrering av mobila enheter <!--747600, 795782-->
Intune lägger till nya registreringsbegränsningar som avgör vilka plattformar som mobila enheter ska kunna registrera. Intune skiljer mellan mobilplattformar som iOS, macOS, Android, Windows och Windows Mobile.

* Begränsningen av registrering av mobila enheter begränsar inte registreringen av datorklienter.  
* För iOS och Android finns det ytterligare ett alternativ för att blockera registrering av personligt ägda enheter.

Intune markerar alla nya enheter som personliga såvida inte IT-administratören vidtar åtgärder för att markera dem som företagsägda, vilket beskrivs i [den här artikeln](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Visa alla åtgärder på hanterade enheter <!--677150-->
En ny rapport om __enhetsåtgärder__ visar vem som har utfört fjärråtgärder som fabriksåterställning på enheter, och dessutom visas status för åtgärden. Se [Vad är enhetshantering?](device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Icke-hanterade enheter kan komma åt tilldelade appar <!--664691-->
Som en del av designändringarna på företagsportalens webbplats ska iOS- och Android-användare kunna installera appar som har tilldelats dem som "tillgänglig utan registrering" på sina icke-hanterade enheter. Med sina Intune-autentiseringsuppgifter kan användare logga in på företagsportalens webbplats och se en lista över appar som tilldelats dem. App-paket för apparna som är "tillgängliga utan registrering" görs tillgängliga för hämtning via företagsportalens webbplats. Appar som kräver registrering för installation påverkas inte av den här ändringen, eftersom användarna uppmanas att registrera sina enheter om de vill installera apparna.

### <a name="custom-app-categories---748805--"></a>Anpassade appkategorier <!--748805-->
Du kan nu skapa, redigera och tilldela kategorier för appar som du lägger till i Intune. Kategorier kan för närvarande kan bara anges på engelska.
Läs [How to add an app to Intune](apps-add.md) (Lägga till en app i Intune).

### <a name="display-device-categories---814654--"></a>Visa enhetskategorier <!--814654-->
Du kan nu visa enhetskategorin som en kolumn i listan över enheter. Du kan också redigera kategorin från avsnittet med egenskaper på bladet Enhetsegenskaper. Läs [How to add an app to Intune](apps-add.md) (Lägga till en app i Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Konfigurera inställningar för Windows Update för företag <!--776716-->

Windows som en tjänst är det nya sättet för att tillhandahålla uppdateringar för Windows 10. Från och med Windows 10 innehåller alla nya funktions- och kvalitets även innehållet från alla tidigare uppdateringar. Det innebär att så länge som du har installerat den senaste uppdateringen så vet du att dina Windows 10-enheter är helt uppdaterade. Till skillnad från vad som var fallet i tidigare versioner av Windows måste du nu installera hela uppdateringen i stället för en del av en uppdatering.

Med hjälp av Windows Update för företag kan du förenkla hanteringen av uppdateringar så att du inte behöver godkänna varje enskild uppdatering för enhetsgrupperna. Du kan fortfarande hantera risker i din miljö genom att konfigurera en strategi för uppdateringarna installeras, och Windows Update ser till att uppdateringarna installeras vid rätt tidpunkt. Microsoft Intune ger dig möjlighet att konfigurera enheternas inställningar och att skjuta upp installationen av uppdateringar. Intune lagrar inte uppdateringar, utan enbart uppdateringarnas principtilldelning. Enheterna har direkt åtkomst till uppdateringarna via Windows Update. Använd Intune för att konfigurera och hantera **Windows 10-uppdateringsringar**. En uppdateringsring innehåller en grupp med inställningar som anger när och hur uppdateringar av Windows 10 updates installeras. Mer information finns i [Konfigurera inställningar för Windows Update för företag](windows-update-for-business-configure.md).
