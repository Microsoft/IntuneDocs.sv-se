---
title: Nyheter i Microsoft Intune
titlesuffix: Azure portal
description: "Ta reda på vad som är nytt i Intune Azure-portalen"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 861d28b75d72a2784fc1c73a6f770d44cf1a21b3
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Läs mer om varje veckas nyheter i Microsoft Intune. Du kan också läsa mer om [kommande ändringar](#whats-coming), [viktiga meddelanden](#notices) om tjänsten och information om [tidigare versioner](whats-new-archive.md).

> [!Note]
> På [hybridsidan med senaste nytt](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) finns mer information om nya funktioner för hybridhantering av mobilenheter (MDM).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-january-22-2018"></a>Vecka 22 januari 2018

### <a name="intune-apps"></a>Intune-appar

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Fjärrlås är tillgängligt i företagsportalappen för Windows 10 <!--676506-->
Slutanvändare kan nu fjärrlåsa sina enheter från företagsportalappen för Windows 10. Detta visas inte för den lokala enheten som används.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Enklare lösning av efterlevnadsproblem för företagsportalappen för Windows 10 <!--676546-->
Slutanvändare med Windows-enheter kan trycka på orsaken till bristande efterlevnad i företagsportalappen. Om möjligt kommer de då direkt till rätt plats i inställningsappen för att kunna åtgärda problemet.

## <a name="week-of-december-11-2017"></a>Veckan som börjar med 11 December 2017

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Ny inställning för automatisk omdistribution <!-- 1469168 -->
Inställningen **Automatisk omdistribution** låter användare med administrativ behörighet ta bort alla användardata och inställningar med hjälp av **Ctrl + Win + R** på enhetens låsskärm. Enheten omkonfigureras automatiskt och omregistreras för hantering. Den här inställningen finns under Windows 10 > Enhetsbegränsningar > Allmänt -> Automatisk omdistribution. Mer information finns i [Inställningar för begränsningar i Intune-enheter för Windows 10](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Stöd för ytterligare källutgåvor i Windows 10 med principen för versionsuppgradering<!-- 903672,  1119689 -->
Du kan nu använda uppgraderingsprincipen för Windows 10 för att uppgradera från ytterligare Windows 10-versioner (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud, o.s.v.). Innan den här versionen var de uppgraderingsvägar som stöddes för utgåvan mer begränsade. Du hittar mer information i [Så här konfigurerar du uppgraderingar av Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Profilinställningar för enhetskonfiguration för Nya Windows Defender Security Center (WDSC) <!-- 1335507 -->

Intune lägger till ett nytt avsnitt med profilinställningar för enhetskonfiguration under Endpoint Protection som heter **Windows Defender Security Center**. IT-administratörer kan konfigurera vilka pelare Windows Defender Security Center-appen som slutanvändare kan komma åt. Om IT-administratör döljer en pelare i Windows Defender Security Center-appen, döljs alla meddelanden som rör den dolda pelare på användarens enhet.

Dessa är de pelare som administratörer kan dölja från profilinställningarna för enhetskonfiguration för Windows Defender Security Center:
- Skydd mot virus och hot
- Enhetsprestanda och hälsa
- Brandväggs- och nätverksskydd
- App- och webbläsarkontroll
- Familjealternativ

IT-administratörer kan också anpassa de meddelanden som användare tar emot. Du kan till exempel konfigurera om användarna får alla meddelanden som skapas av synliga pelare i WDSC, eller enbart viktiga meddelanden. Meddelanden som är mindre viktiga inkluderar periodiska sammanfattningar av Windows Defender Antivirus-aktivitet och meddelanden när genomsökningar har slutförts. Alla andra meddelanden anses viktiga. Dessutom kan du kan också anpassa själva meddelandeinnehållet, du kan till exempel ange IT-kontaktinformation att bädda in i meddelanden som visas på användarnas enheter.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Stöd för flera anslutningsappar för hantering av SCEP- och PFX-certifikat <!-- 1361755 -->

Kunder som använder den lokala NDES-anslutningsappen för att leverera certifikat till enheter kan nu konfigurera flera anslutningsappar i en enda klient.

Den här nya funktionen stöder följande scenarion:

- **Hög tillgänglighet**

Varje NDES-anslutningsapp tar emot certifikatbegäranden från Intune.  Om en NDES-anslutningsapp kopplas från, kan den andra anslutningsappen fortsätta att bearbeta begäranden.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Ämnesnamnet för kunden kan använda variabeln AAD_DEVICE_ID <!-- 1468599 -->

När du skapar en profil för SCEP-certifikatet i Intune kan du nu använda variabeln AAD_DEVICE_ID när du skapar det anpassade ämnesnamnet.   När certifikatet har begärts med hjälp av den här SCEP-profilen, ersätts variabeln med ADD-enhetens ID för den enhet som gör certifikatbegäran.


### <a name="device-management"></a>Enhetshantering

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Hantera Jamf-registrerade macOS-enheter med Intunes motor för enhetsefterlevnad <!-- 1592747 -->
Du kan nu använda Jamf statusinformation för macOS-enheter till Intune, som sedan utvärderar den för efterlevnad av de principer som definierats i Intune-konsolen. Baserat på enhetens efterlevnadsstatus samt andra villkor (till exempel plats, användarrisk osv.), framtvingar villkorsstyrd åtkomst efterlevnad för macOS-enheter som har åtkomst till molnet och lokala program som är anslutna till Azure AD, inklusive Office 365. Lär dig mer om att [ställa in Jamf-integration](conditional-access-integrate-jamf.md) och [tillämpa kompatibilitet för enheter som hanteras av Jamf](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Ny iOS-enhetsåtgärd   <!-- 1424701 -->

Du kan nu stänga av iOS 10.3-övervakade enheter. Den här åtgärden stänger av enheten omedelbart utan varning till slutanvändaren. Åtgärden **stäng ner (endast övervakat)** finns i enhetsegenskaperna när du väljer en enhet i arbetsbelastningen **enhet**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Tillåt inte ändringar av datum/tid för Samsung Knox-enheter<!-- 1468103 -->

Vi har lagt till en ny funktion som gör det möjligt att blockera datum- och tidändringar på Samsung Knox-enheter. Du hittar den i **Profiler för enhetskonfiguration** > **Enhetsbegränsningar (Android)** > **Allmänt**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Stöd för Surface Hub-resurskonto <!-- 1566442  -->

En ny enhetsåtgärd har lagts till så att administratörer kan definiera och uppdatera resurskonton som är associerade med en Surface Hub.

Resurskontot används av en Surface Hub för att autentisera med Skype/Exchange så att den kan ansluta till ett möte. Du kan skapa ett unikt resurskonto så att Surface Hub visas i mötet som konferensrummet. Resurskontot kan till exempel visas som *konferensrum B41/6233*. Resurskontot (kallas även enhetskontot) för Surface Hub måste vanligtvis konfigureras för konferensrumsplatsen och när andra parametrar för resurskontot måste ändras.

När administratörer vill uppdatera resurskontot på en enhet, måste de ange de aktuella autentiseringsuppgifterna för Active Directory/Azure Active Directory som är kopplade till enheten. Om lösenordsrotation är aktiverat för enheten, måste administratörer gå till Azure Active Directory för att hitta lösenordet.

> [!NOTE]
> Alla fält skickas i ett paket och skriver över alla fält som tidigare var konfigurerade. Tomma fält skriver också över befintliga fält.

Följande är de inställningar som administratörer kan konfigurera:

- **Resurskonto**
   - **Active Directory-användare**

      Domännamn\användarnamn eller användarens huvudnamn (UPN):user@domainname.com

   - **Lösenord**

- **Valfria parametrar för resurskontot** (måste anges med det angivna resurskontot)

   - **Intervall för lösenordsrotation**

     Garanterar att kontolösenordet uppdateras automatiskt av Surface Hub varje vecka av säkerhetsskäl. Om du vill konfigurera parametrar efter att det här har aktiverats, måste kontot i Azure Active Directory få lösenordet nollställt.

   - **SIP-adress (Session Initiation Protocol)**

     Används endast när automatisk identifiering misslyckas.

   - **E-post**

     E-postadress för enhets-/resurskontot.

   - **Exchange-server**

     Krävs endast om automatisk identifiering misslyckas.

   - **Kalendersynkronisering**

     Anger om kalendersynkronisering och andra Exchange-servertjänster är aktiverade. Till exempel: mötessynkronisering.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Installera Office-appar på macOS-enheter<!-- 1494311 -->
Du kommer nu att kunna installera Office-appar på macOS-enheter. Den här nya apptypen låter dig installera Word, Excel, PowerPoint, Outlook och OneNote. De här apparna inkluderar även Microsoft AutoUpdater (MAU), för att hålla dina appar säkra och uppdaterade.

### <a name="app-management"></a>Apphantering

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Ta bort en iOS-token för volyminköpsprogram <!-- 820879 -->
Du kan ta bort token för iOS-volyminköpsprogram (VPP) med hjälp av konsolen. Detta kan vara nödvändigt när du har dubblettinstanser av en VPP-token.

### <a name="intune-apps"></a>Intune-appar

#### <a name="end-user-messaging-for-accounts---1573558-for-1712--"></a>Meddelandefunktion för slutanvändare för konton <!--1573558 for 1712-->

Användare av företagsportalens webbsida kommer att blockeras från att vidta åtgärder som kräver skrivbehörighet till din klient. De kommer att se lämpligt felmeddelande som förklarar att deras konto är under underhåll. Liknande ändringar finns snart för appar i företagsportalen för Android, iOS, macOS och Windows. Du kan se detta fel på [Nyheter i appens användargränssnitt](whats-new-app-ui.md).



### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>En ny entitetssamling med namnet aktuell användare, är begränsad till aktuell aktiv användardata <!-- 1667026 -->

Entitetssamlingen **Användare** innehåller alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i ditt företag. En användare kan till exempel läggas till i Intune och sedan tas bort under den senaste månaden. Användaren är då inte tillgänglig vid tidpunkten för rapporten, men användaren och tillståndet finns i data. Du kan skapa en rapport som visar varaktigheten för användarens historiska förekomst i dina data.

Den nya entitetssamlingen **aktuell användare** innehåller däremot bara användare som inte har tagits bort. Entitetssamlingen **aktuell användare** innehåller bara användare som är aktiva för tillfället. Mer information om entitetssamlingen **aktuell användare** finns i [referens för den aktuella användarentiteten](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>Uppdaterade Graph API:er<!-- 1736360 -->

Vi har uppdaterat några av Graph API:erna för Intune i den här betaversionen. Kontrollera den månatliga [Ändringsloggen för Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog) för mer information.


## <a name="week-of-december-4-2017"></a>Veckan som börjar med 4 December 2017

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune har stöd för appar som nekats av Windows informationsskydd (WIP) <!-- 1479103 -->
Du kan ange nekade appar i Intune. Om en app nekas blockeras den från att komma åt företagsinformation. Detta är i praktiken motsatsen till listan över tillåtna appar. Mer information finns i [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Rekommenderad neka-lista för Windows Information Protection).


## <a name="week-of-november-27-2017"></a>Veckan som börjar med 27 november 2017

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>Felsöka problem med registreringen  <!-- 746324 -->

I **felsökningsarbetsytan** visas nu problem med användarregistreringen. Information om problemet och förslagna lösningar kan hjälpa administratörer och medarbetare på supportavdelningen att felsöka problem. Vissa problem med registreringen inte fångas upp, och vissa fel kanske inte har några reparationsförslag.

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>Grupptilldelade registreringsbegränsningar <!-- 747598 -->

Som Intune-administratör kan du nu [skapa anpassade registreringsbegränsningar för enhetstyp och enhetsgräns för användargrupper](enrollment-restrictions-set.md).

Du kan skapa upp till 25 instanser av varje begränsningstyp med Intune Azure Portal som du sedan kan tilldela till användargrupper. Grupptilldelade begränsningar åsidosätter standardbegränsningarna.

Alla instanser av en begränsningstyp lagras i ett strikt sorterad lista. Den här ordningen definierar prioritetsvärden för konfliktlösning. En användare som påverkas av mer än en begränsningsinstans begränsas endast av instansen med det högsta prioritetsvärdet. Du kan ändra prioriteten för en viss instans genom att dra den till en annan plats i listan.

Den här funktionen kommer att lanseras med migreringen av Android for Work-inställningar från registreringsmenyn för Android for Work till menyn för registreringsbegränsningar. Den här migreringen kan ta flera dagar. Ditt konto kan uppgraderas för andra delar av novemberversionen innan grupptilldelning aktiveras för registreringsbegränsningar.

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Stöd för flera anslutningsprogram för registreringstjänster för nätverksenheter (NDES) <!-- 1528104 -->

Registreringstjänsten för nätverksenheter (NDES) gör det möjligt för mobilenheter som körs utan domänautentiseringsuppgifter att hämta certifikat baserade på SCEP-tillägg (Simple Certificate Enrollment Protocol).
Med den här uppdateringen stöds flera NDES-anslutningsprogram.

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Hantera Android for Work-enheter oberoende av Android-enheter <!-- 1490731 EEready-->

**Obs!** Följande ändringar börjar distribueras med novemberuppdateringen, men det kan ta tid innan de tillämpas på ditt konto. Du får ett bekräftelsemeddelande i Office 365-portalen när ändringarna är applicerade på ditt konto. Efter distributionen får du ytterligare hanteringsalternativ. Slutanvändarens upplevelse ändras inte under distributionen.

Intune stöder registrering av hantering av Android for Work-enheter oberoende av Android-plattformen. De här inställningarna hanteras under **Enhetsregistrering** > **Registreringsbegränsningar** > **Begränsningar för enhetstyper**. (De fanns tidigare **Enhetsregistrering** > **Android for Work-registrering** > **Registreringsinställningar för Android for Work**.)

Som standard är dina Android for Work-enhetsinställningar samma som inställningarna för dina Android-enheter. Men när du har ändrat dina Android for Work-inställningar kommer det här inte längre att vara fallet.

Om du blockerar registrering av personligt ägda Android for Work-enheter så kan endast företagsägda Android-enheter att registrera Android for Work.

Tänk på följande när du konfigurerar nya inställningar:

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Om du aldrig tidigare har publicerat Android for Work-registrering

Den nya Android for Work-plattformen blockeras av standardbegränsningarna för enhetstyper. När du har publicerat funktionen kan du tillåta enheter att registreras med Android for Work. För att göra detta ändrar du på standardvärdena eller skapar en ny begränsning för enhetstyp för att ersätta begränsningen för enhetstyp som är standard.

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Om du har publicerat Android for Work-registrering

Om du har publicerat tidigare så beror din situation på de inställningar du väljer:

| Inställningen | Statusen för Android for Work under begränsningar för enhetstyper | Obs! |
| --- | --- | --- |
| **Hantera alla enheter som Android** | Blockerad | Alla Android-enheter måste registreras utan Android for Work. |
| **Hantera enheter som stöds som Android for Work** | Tillåts | Alla Android-enheter som har stöd för Android for Work måste registreras med Android for Work. |
| **Hantera endast enheter som stöds i de här grupperna som Android for Work för användare** | Blockerad | En separat princip för begränsningar för enhetstyper skapades för att åsidosätta standardinställningen. Den här principen definierar de grupper som du tidigare valde för att tillåta Android for Work-registrering. Användare i de valda grupperna fortsätter att kunna registrera sina Android for Work-enheter. Alla andra användare är begränsade från att registrera med Android for Work. |

I samtliga fall bevaras din avsedda regler. Ingen åtgärd krävs från din sida för att underhålla den globala begränsningen eller per grupp-begränsningen för Android for Work i din miljö.

### <a name="app-management"></a>Apphantering

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Rapporten om appinstallation har uppdaterats. Den omfattar nu statusen Installation väntar <!-- 1249446 -->  

Rapporten **Status för appinstallation** som är tillgänglig för varje app via listan **Appar** i arbetsbelastningen **Mobilappar** innehåller nu en sammanräkning av antalet **Installation väntar** för användare och enheter.

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API för appinventering för iOS 11 för mobil hotidentifiering <!-- 1391759 -->

Intune samlar in information om appinventering från både personliga och företagsägda enheter och gör den tillgänglig för leverantörer av mobil hotidentifiering (MTD) att hämta, till exempel Lookout for Work. Du kan samla in en appinventering från användare av enheter med iOS 11+.

**Appinventering**  
Inventeringar från både företagsägda iOS 11+ och personligt ägda enheter skickas till MTD-leverantören. Data i appinventeringen omfattar:

 - App-ID
 - Appversion
 - Kort appversion
 - Appnamn
 - Storlek på appsamling
 - Dynamisk appstorlek
 - Om appen har verifierats eller inte
 - Om appen är hanterad eller inte


### <a name="device-management"></a>Enhetshantering

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Migrera användare och enheter från hybrid MDM till fristående Intune <!-- 1463747 wnready -->
Vi har en ny process och nya verktyg för att flytta användare och deras enheter från hybrid MDM till Intune på Azure Portal. Nu kan du göra följande:
- Kopiera principer och profiler från Configuration Manager-konsolen till Intune på Azure Portal
- Flytta en del av användarna till Intune på Azure Portal medan resten fortsätter att använda hybrid MDM
- Migrera enheter till Intune på Azure Portal utan att behöva registrera dem på nytt

Mer information finns i [Migrate hybrid MDM users and devices to Intune standalone](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa) (Migrera hybrida MDM-användare och -enheter till fristående Intune).

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram <!-- 676614 -->
När Exchange-anslutningsappen skapar en anslutning till Exchange med angiven CAS, har anslutningsappen nu möjlighet att identifiera andra CAS. Om den primära certifikatutfärdaren blir otillgänglig, kommer anslutningsappen att växla till en annan certifikatutfärdare, om tillgänglig, tills den primära certifikatutfärdaren blir tillgänglig. Du hittar mer information i [Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Starta om en iOS-enhet via en fjärranslutning (endast övervakade) <!-- 1424595 -->

Du kan nu få en övervakad iOS 10.3 +-enhet att starta om med en enhetsåtgärd. Mer information om hur du använder åtgärden för omstart av enhet finns i [Starta om enheter med Intune med en fjärråtgärd](device-restart.md).

> [!Note]
> Det här kommandot kräver en övervakad enhet och behörighet till **Enhetslås**. Enheten startas om direkt. iOS-enheter låsta med lösenord kommer inte återansluta till ett Wi-Fi-nätverk efter omstarten. Efter omstart kanske de inte kan kommunicera med servern.

#### <a name="single-sign-on-support-for-ios----1333645---"></a>Stöd för enkel inloggning (SSO) på iOS <!-- 1333645 -->  

Du kan använda enkel inloggning för iOS-användare. iOS-appar som är kodade för att leta efter användares autentiseringsuppgifter i nyttolasten för enkel inloggning fungerar med den här uppdateringen av nyttolastkonfigurationen. Du kan även använda UPN och Intune-enhets-ID för att konfigurera huvudnamn och sfär. Mer information finns i [Konfigurera enkel inloggning för Intune för iOS-enheter](sso-ios.md).

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Lägg till ”Hitta min iPhone” för personliga enheter <!--1427287-->
Du kan nu se om iOS-enheter har aktiveringslåset aktiverat. Den här funktionen kunde tidigare hittas i den klassiska Intune-portalen.


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Fjärrlåsa hanterade macOS-enheter med Intune <!-- 1437691 -->

Du kan låsa en förlorad macOS-enhet och ange en PIN-kod för återställning på 6 siffror. När enheten är låst visar bladet **Enhetsöversikt** PIN-koden tills en annan enhetsåtgärd skickas.

Mer information finns i [Fjärrlåsa hanterade enheter med Intune](device-remote-lock.md).

#### <a name="new-scep-profile-details-supported----1559808---"></a>Ny SCEP-profilinformation som stöds <!-- 1559808 -->

Administratörer kan nu ange fler inställningar när de skapar en SCEP-profil på Windows-, iOS-, macOS- och Android-plattformar.  Administratörer kan ange IMEI, serienummer eller eget namn inklusive e-post i ämnesnamnets format.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>Behåll data under en fabriksåterställning <!--1588489 -->
En ny funktion är tillgänglig när du återställer Windows 10 version 1709 och senare till fabriksinställningarna. Administratörer kan ange om enhetsregistrering och andra etablerade data ska finnas kvar på en enhet efter att en fabriksåterställning har utförts.

Följande data behålls efter en fabriksåterställning:
- Användarkonton kopplade till enheten
- Datortillstånd (domänansluten, ansluten till Azure Active Directory)
- MDM-registrering
- Installerade OEM-appar (store och Win32-appar)
- Användarprofil
- Användardata utanför användarprofilen
- Automatisk inloggning för användare

Följande data bevaras inte:
- Användarfiler
- Användarinstallerade appar (store och Win32-appar)
- Enhetsinställningar som inte är standard

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Tilldelningar till Windows 10-uppdateringstestgrupper visas.<!-- 1621837 -->
Du kan se alla tilldelningar till Windows 10-uppdateringstestgrupper för den användare du visar när du **felsöker**.  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Inställningar för rapporteringsfrekvens för Windows Defender Avancerat skydd <!-- 1455974  -->
Tjänsten Windows Defender Avancerat skydd (WDATP) låter administratörer hantera rapporteringsfrekvensen för hanterade enheter. Med det nya alternativet **Skicka frekvensvärde för telemetrirapportering** samlar WDATP in data och utvärderar risker oftare. Standardvärdet för rapporteringsfrekvensen optimerar hastighet och prestanda. Att öka frekvensen för rapportering kan vara användbart för högriskenheter. Den här inställningen finns i profilen **Windows Defender ATP** i **Enhetskonfigurationer**.

#### <a name="audit-updates----1412961---"></a>Granska uppdateringar <!-- 1412961 -->  
Intune-granskning tillhandahåller en post med förändringsåtgärder relaterade till Intune.  Alla åtgärder för att skapa, uppdatera och ta bort, samt fjärruppgifter, sparas och lagras i ett år.  Azure Portal visar granskningsdata i varje arbetsbelastning för de senaste 30 dagarna. Det går även att filtrera bland dessa data.  En motsvarande Graph API gör det möjligt att hämta granskningsdata som lagrats under det senaste året.

Granskning hittas under gruppen **ÖVERVAKA**. Det finns ett menyalternativ för **Granskningsloggar** för varje arbetsbelastning.




## <a name="week-of-november-20-2017"></a>Veckan som börjar med 20 november 2017

### <a name="app-management"></a>Apphantering

#### <a name="google-play-protect-support-on-android----908720---"></a>Stöd för Google Play Protect på Android <!-- 908720 -->

Med versionen Android Oreo introducerar Google en uppsättning säkerhetsfunktioner med namnet Google Play Protect, där användare och organisationer kan köra skyddade appar och Android-bilder. Intune stöder Google Play Protect-funktionerna, inklusive SafetyNets fjärrattestering. Administratörer kan ange efterlevnadsprincipkrav som kräver att Google Play Protect är konfigurerat och felfritt.
Inställningen **SafetyNets enhetsattestering** kräver att enheten ansluter med en Google-tjänst för att kontrollera att enheten är felfri och inte har komprometterats. Administratörer kan också ange en konfigurationsprofilinställning för Android for Work som kräver att installerade program verifieras av Google Play-tjänsterna. Villkorlig åtkomst kan blockera användare från att komma åt företagets resurser om en enhet inte är kompatibel med Google Play Protect-kraven.

- Lär dig [hur du skapar en princip för enhetsefterlevnad om du vill aktivera Google Play-skydd](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Textprotokollet som tillåts från hanterade appar <!-- 1414050  -->

Appar som hanteras av Intune App SDK kan skicka SMS-meddelanden.

## <a name="week-of-november-13-2017"></a>Veckan som börjar 13 november 2017

### <a name="intune-apps"></a>Intune-appar
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>Företagsportalappen för macOS finns tillgänglig <!--1541700-->
Intunes företagsportal på macOS har en uppdaterad upplevelse som har optimerats för att visa all information och de efterlevnadsmeddelanden som användare behöver för alla enheter som de har registrerat. När Intunes företagsportal har distribuerats till en enhet, kommer Microsoft AutoUpdate för macOS att ge den uppdateringar. Du kan hämta den nya Intune-företagsportalen för macOS genom att logga in på webbplatsen för Intune-företagsportalen från en macOS-enhet.

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner är nu en del av MAM-listan (hantering av mobilappar) över godkända appar<!-- 1248473 -->
Microsoft Planner-appen för iOS och Android är nu del av de godkända apparna för hantering av mobilappar (MAM). Appen kan konfigureras via bladet för Intune-appskydd i Azure-portalen för alla klienter.
- Läs mer i [MAM-listan över godkända appar](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Uppdateringsfrekvensen för per App-VPN-kravet på iOS-enheter <!-- 1547061 -->  
Administratörer kan nu ta bort per App-VPN-kravet för appar på iOS-enheter. Berörda enheter kommer efter deras nästa Intune-incheckning, vilket vanligtvis sker inom 15 minuter.  

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Stöd för System Center Operations Manager-hanteringspaketet för Exchange-anslutningsappen <!-- 885457 -->
SCOM-hanteringspaketet (System Center Operations Manager) för Exchange-anslutningsappen finns nu tillgängligt att hjälpa dig parsa Exchange-anslutningsloggarna. Det ger dig flera olika sätt att övervaka tjänsten när du behöver felsöka problem.

## <a name="week-of-november-6-2017"></a>Veckan som börjar med 6 november 2017

### <a name="device-enrollment"></a>Enhetsregistrering
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Samhantering för Windows 10-enheter  <!-- 1243445 -->
Samhantering är en lösning som erbjuder en brygga från traditionell till modern hantering, och det ger dig en sökväg för att göra övergången stegvis. I grund och botten är samhantering en lösning där Windows 10-enheter samtidigt hanteras av Configuration Manager och Microsoft Intune, som är anslutna till Active Directory (AD) och Azure Active Directory (Azure AD).  Den här konfigurationen ger dig en sökväg för att modernisera med tiden i den takt som passar din organisation om du inte kan flytta allt på samma gång.  

#### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Ny registreringsstatussida för Windows 10-registreringar <!--1063201-->    
Nu kan du konfigurera en hälsning som visas när dina användare registrerar Windows 10-enheter. Använd **registreringsstatusskärmen** för att konfigurera ett anpassat meddelande och en hyperlänk som ska visas för dina slutanvändare när de registrerar sina Windows 10-enheter.  **Registreringsstatusskärmen** ger också slutanvändarna en översikt över förloppet för policyinställningar som används för deras enhet.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Begränsa Windows-registrering efter OS-version <!-- 245498 -->
Som Intune-administratör kan du nu ange en lägsta och högsta version av Windows 10 för enhetsregistrering. Du kan ange begränsningarna på bladet **Plattformskonfigurationer**.

Intune fortsätter att stödja registrering av datorer och telefoner med Windows 8.1. Endast Windows 10-versioner kan dock konfigureras med lägsta och högsta gränser. Låt den lägsta gränsen vara tom om du vill tillåta registrering av 8.1-enheter.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Aviseringar för otilldelade Windows AutoPilot-enheter <!-- 1631236 -->
En ny avisering är tillgänglig för otilldelade Windows AutoPilot-enheter på sidan **Microsoft Intune** > **Enhetsregistrering** > **Översikt**. Den här aviseringen visar hur många enheter från AutoPilot-programmet som inte har tilldelade AutoPilot-distributionsprofiler. Använd informationen i aviseringen för att skapa profiler och tilldela dem till de otilldelade enheterna. När du klickar på aviseringen visas en fullständig lista över Windows AutoPilot-enheter och detaljerad information om dem. Läs mer i informationen om att [registrera Windows-enheter med Windows AutoPilot-distributionsprogrammet](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="device-management"></a>Enhetshantering

#### <a name="refresh-button-for-devices-list-------1333581---"></a>Uppdateringsknapp för enhetslista <!-- 1333581 -->
Eftersom enhetslistan inte uppdateras automatiskt kan du använda den nya uppdateringsknappen för att uppdatera vilka enheter som visas i listan.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Stöd för Symantec Cloud Certification Authority (CA)  <!-- 1333638 -->    
Intune stöder nu Symantec Cloud CA, som tillåter att Intune Certificate Connector utfärdar PKCS-certifikat från Symantec Cloud CA till hanterade Intune-enheter. Om du redan använder Intune Certificate Connector med Microsoft Certification Authority (CA) kan du utnyttja den befintliga Intune Certificate Connector-konfigurationen för att lägga till Symantec CA-stöd.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nya objekt som har lagts till i enhetsinventering <!--1404455 -->
I den här versionen har vi lagt till följande nya objekt i den [inventering som görs av registrerade enheter](device-inventory.md):

- Wi-Fi MAC-adress
- Totalt lagringsutrymme
- Totalt ledigt utrymme
- MEID
- Abonnentens operatör


### <a name="app-management"></a>Apphantering
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Ange åtkomst för appar med den lägsta Android-säkerhetskorrigeringen på enheten<!-- 1278463 -->   
En administratör kan definiera den lägsta Android-säkerhetskorrigering som måste vara installerad på enheten för beviljad åtkomst till ett hanterat program under ett hanterat konto.

> [!Note]  
> Den här funktionen begränsar endast säkerhetsuppdateringar som ges ut av Google på Android 6.0+-enheter.

#### <a name="app-conditional-launch-support----1193313---"></a>Stöd för appvillkorlig start <!-- 1193313 -->
IT-administratörer kan nu ange ett krav via Azure-administrationsportalen på att framtvinga ett lösenord i stället för en numerisk PIN-kod via mobilapphantering (MAM) när programmet startas. Om det har konfigurerats måste användaren vid uppmaning ställa in och använda ett lösenord innan användaren får åtkomst till MAM-integrerade program. Ett lösenord definieras som en numerisk PIN-kod med minst ett specialtecken eller en gemen/versal. Den här versionen av Intune kommer att aktivera den här funktionen **enbart på iOS**. Intune stöder lösenord på liknande sätt som numeriska PIN-koder. En minsta längd krävs och upprepning av tecken och sekvenser tillåts. Den här funktionen kräver att program deltar (t.ex. WXP, Outlook, Managed Browser, Yammer) för att integrera Intune APP SDK:n med koden för funktionen på plats för att lösenordsinställningarna ska framtvingas i berörda program.

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>App-versionsnumret för verksamhetsspecifika rapporter för installationsstatus för enhet <!-- 1233999 -->
I den här versionen visar rapporten för installationsstatus för enhet appversionsnumret för verksamhetsspecifika appar för iOS och Android. Du kan använda den här informationen för att felsöka dina appar och hitta enheter som kör gamla appversioner.


### <a name="device-configuration"></a>Enhetskonfiguration
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Administratörer kan nu konfigurera brandväggsinställningar på en enhet med en profil för konfiguration av enheter <!-- 951708 -->   
Administratörer kan aktivera brandvägg för enheter och konfigurera olika protokoll för domän-, privata och offentliga nätverk.  Brandväggsinställningarna finns i profilen för slutpunktsskydd.

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard skyddar enheter mot ej betrodda webbplatser enligt organisationens definition <!-- 958257 -->   
Administratörer kan definiera platser som ”betrodda” eller ”företagsdata” med hjälp av Windows Information Protection-arbetsflödet eller den nya profilen "Nätverksgräns" under enhetskonfigurationer. Webbplatser som inte är angivna i en 64-bitars Windows 10-enhets betrodda nätverk och som öppnas med Microsoft Edge öppnas istället i en webbläsare i en virtuell Hyper-V-dator.

Application Guard finns i profilerna för enhetskonfiguration i profilen ”Endpoint protection”. Därifrån kan administratörer konfigurera interaktion mellan den virtualiserade webbläsaren och värddatorn, ej betrodda och betrodda webbplatser och lagra data som genererats i den virtualiserade webbläsaren. Om du vill använda Application Guard på en enhet måste du först konfigurera en nätverksgräns. Det är viktigt att endast definiera en nätverksgräns för en enhet.  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>I Windows Defender Application Control på Windows 10 Enterprise finns ett läge för att enbart lita på godkända appar <!-- 1031096 -->    
Tusentals nya skadliga filer skapas varje dag, och användningen av signaturbaserat antivirusskydd för att bekämpa skadlig programvara kanske inte längre ger ett tillräckligt försvar mot nya attacker. Om du använder Windows Defender Application Control på Windows 10 Enterprise kan du ändra enhetskonfiguration från ett läge där appar är betrodda och annars blockeras av en antiviruslösning eller en annan säkerhetslösning till ett läge där operativsystemet enbart litar på appar som företaget har godkänt. Du tilldelar förtroende till appar i Windows Defender Application Control.

Med Intune kan du konfigurera principer för programkontroll i läget för ”endast granskning” eller i tvingande läge. Appar blockeras inte i läget för ”endast granskning”. Läget för ”endast granskning” loggar alla händelser i lokala klientloggar. Du kan också konfigurera om enbart Microsoft-komponenter och Windows Store-appar ska tillåtas att köras eller om ytterligare appar med gott rykte enligt Intelligent Security Graphs definition också ska tillåtas.

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Window Defender Exploit Guard är en ny uppsättning intrångsförebyggande funktioner för Windows 10 <!-- 1063615 -->   
Window Defender Exploit Guard innehåller anpassade regler för att minska sårbarheter i program, förhindra makro- och skripthot, automatiskt blockera nätverksanslutningar till IP-adresser med dåligt rykte och kan skydda data mot utpressningstrojaner och okända hot. Windows Defender Exploit Guard består av följande komponenter:

- **Attack Surface Reduction (ASR)** tillhandahåller regler som tillåter dig att förhindra hot via makron, skript och e-post.
- **Reglerad mappåtkomst** blockerar automatiskt åtkomst till innehåll i skyddade mappar.
- **Nätverksfilter** blockerar utgående anslutning från valfri app för IP/domän med dåligt rykte
- **Sårbarhetsskydd** erbjuder begränsningar för minne, kontrollflöde och principer som kan användas för att skydda ett program mot sårbarheter.


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Hantera PowerShell-skript i Intune för Windows 10-enheter <!-- 790537 -->

Intunes hanteringstillägg gör det möjligt att ladda upp PowerShell-skript i Intune för att köra Windows 10-enheter. Tillägget kompletterar funktioner för hantering av mobilenheter (MDM) i Windows 10 och gör det enklare för dig att flytta till modern hantering. Mer information finns i [Hantera PowerShell-skript i Intune för Windows 10-enheter](intune-management-extension.md).

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Inställningar för enhetsbegränsningar för Windows 10      <!-- 1308850 -->
-    Meddelandefunktion (endast mobil) – inaktivera testning eller MMS-meddelanden
-    Lösenord – inställningar för att aktivera FIPS och användning av sekundära Windows Hello-enheter för autentisering 
-    Skärm – inställningar för att slå på eller stänga av GDI-skalning för äldre appar

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Begränsningar för fullskärmsläge för Windows 10-enheter <!-- 1308872 -->   
Du kan begränsa användare av Windows 10-enheter till helskärmsläge, vilket begränsar användarna till en uppsättning fördefinierade appar.  Det gör du genom att skapa en begränsningsprofil för Windows 10-enheter och ange inställningar för helskärmsläge.

Helskärmsläge stöder två lägen: **en enda app** (gör att användaren endast kan köra en enda app) eller **flerappsläge** (tillåter åtkomst till en uppsättning appar).  Du definierar användarkontot och enhetens namn, vilket avgör vilka appar som stöds).  Inloggade användare är begränsade till definierade appar.  Mer information finns i [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (Begränsad CSP-åtkomst). 

Krav för helskärmsläge:

- Intune måste vara MDM-författare.
- Apparna måste redan vara installerade på målenheten.
- Enheten måste vara [rätt etablerad](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Ny profil för enhetskonfiguration för att skapa nätverksgränser<!-- 1311967 -->   
Vi har skapat en profil för enhetskonfiguration som heter **Nätverksgräns** som finns bland dina övriga enhetskonfigurationsprofiler. Använd den här profilen till att definiera onlineresurser som du anser är företagets och betrodda. Du måste definiera en nätverksgräns för en enhet *innan* funktioner som Windows Defender Application Guard och Windows informationsskydd kan användas på enheten. Det är viktigt att endast definiera en nätverksgräns för varje enhet.

Du kan definiera företagets molnresurser, IP-adressintervall och interna proxyservrar som du anser är betrodda. När en nätverksgräns är definierad kan den användas av andra funktioner som Windows Defender Application Guard och Windows informationsskydd.

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Två ytterligare inställningar för Windows Defender Antivirus <!-- 1338409 -->  
**Filblockeringsnivå**

| | |
|---|---|
| Inte konfigurerat | **Ej konfigurerad** använder standardnivån för Windows Defender Antivirus-blockering och ger ett starkt skydd utan att öka risken för att upptäcka legitima filer. |
| Hög | **Hög** tillämpar en hög skyddsnivå.
| Hög +  | **Hög +** erbjuder Hög-nivån med extra skyddsåtgärder som kan påverka klientprestanda.
| Nolltolerans  | **Nolltolerans** blockerar alla okända körbara filer. |

Inställningen **Hög** kan orsaka att vissa legitima filer upptäcks, men det är osannolikt.
Vi rekommenderar att du ställer in filblockeringsnivån på standardläget **Ej konfigurerad**.

**Tidsgränstillägg för filgenomsökning av molnet**  

| | |
|--|--|
| Antal sekunder (0–50) | Ange den längsta tid som Windows Defender Antivirus ska blockera en fil under väntan på ett resultat från molnet. Standardvärdet är 10 sekunder: ytterligare tid som anges här (upp till 50 sekunder) läggs på för de 10 sekunderna. I de flesta fall går genomsökningen mycket snabbare än maxvärdet. En utökning av tiden gör att molnet kan undersöka misstänkta filer noggrant. Vi rekommenderar att du aktiverar den här inställningen och anger minst 20 ytterligare sekunder. |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Citrix VPN tillagt för Windows 10-enheter <!-- 1512457 -->  
Du kan konfigurera Citrix VPN för Windows 10-enheter. Du kan välja Citrix VPN i listan *Välj en anslutningstyp* på bladet **Bas-VPN** när du konfigurerar en VPN för Windows 10 och senare.

> [!Note]
> Det fanns Citrix-konfiguration för iOS och Android.

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Wi-Fi-anslutningar stöder i förväg delade nycklar på iOS <!-- 1550823 -->
Kunder kan konfigurera Wi-Fi-profiler för att använda i förväg delade nycklar (PSK) för personliga WPA/WPA2-anslutningar på iOS-enheter. De här profilerna pushas till användarens enhet när enheten registreras i Intune.

När profilen har pushats till enheten beror nästa steg på profilkonfigurationen.  Om automatisk anslutning är konfigurerad sker det när nätverket behövs härnäst.  Om profilen ska anslutas manuellt måste användaren aktivera anslutningen manuellt.  

### <a name="intune-apps"></a>Intune-appar

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Åtkomst till loggar för hanterade appar för iOS <!-- 1469920 -->
Slutanvändare med Managed Browser installerad kan nu se hanteringsstatus för alla appar som har publicerats av Microsoft och kan skicka loggar för felsökning av hanterade iOS-appar.

Om du vill lära dig att aktivera felsökningsläget i Managed Browser på en iOS-enhet kan du läsa [Komma åt loggar för hanterade appar med Managed Browser i iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Förbättringar av arbetsflödet för enhetskonfiguration i företagsportalen för iOS i version 2.9.0 <!-- 1417174 -->

Vi har förbättrat arbetsflödet för enhetskonfiguration i företagsportalappen för iOS. Språket är mer användarvänligt och vi har kombinerat skärmar där det är möjligt. Vi har också gjort språket mer specifikt för ditt företag genom att använda företagsnamnet genomgående i installationstexten. Du kan se det uppdaterade arbetsflödet på  [sidan nyheter i appgränssnittet](whats-new-app-ui.md).

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>Användarentiteten innehåller de senaste användardata i datamodellen för informationslagret <!-- 1544273 -->
Den första versionen av datamodellen för Intune-informationslagret innehöll endast de senaste historiska Intune-data. Rapportskaparna kunde inte identifiera det aktuella tillståndet för en användare. I den här uppdateringen fylls **användarentiteten** i med senaste användardata.


## <a name="week-of-october-30-2017"></a>Veckan som börjar med 30 oktober 2017

### <a name="app-management"></a>Apphantering

#### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>Versionsnummer för verksamhetsspecifika iOS och Android-program är synliga <!-- 1380712 -->

Appar i Intune visar nu versionsnumret för verksamhetsspecifika iOS och Android-appar. Numret visas på Azure Portal i listan över appar och på bladet med översikt över appar. Slutanvändarna kan se appnumret i företagsportalappen och i webbportalen.

__Fullständigt versionsnummer__ Det fullständiga versionsnumret identifierar en specifik version av appen. Numret visas som _Version_(_Build_). Exempelvis, 2.2(2.2.17560800)

Det fullständiga versionsnumret har två komponenter:

 - **Version**  
   Versionsnumret är det läsbara versionsnumret för appen. Det här numret används av slutanvändare för att identifiera olika versioner av appen.

 - **Build-nummer**  
    Build-numret är ett internt nummer som kan användas i appidentifiering och för att programmässigt hantera appen. Build-nummer refererar till en iteration av appen som refererar till ändringar i koden.

Mer information om versionsnummer och utveckling av verksamhetsspecifika appar finns i [Get started with the Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers) (Kom igång med Microsoft Intune App SDK).

#### <a name="device-and-app-management-integration----677972---"></a>Integrering av enhets- och apphantering <!-- 677972 -->   
Nu när Intunes hantering av mobila enheter (MDM) och hantering av mobilprogram (MAM) båda är åtkomliga från Azure-portalen har Intune börjat integrera IT-adminstratörsupplevelsen kring program- och enhetshantering. De här ändringarna är avsedda att förenkla enhets- och apphanteringen.

Läs mer om ändringarna i MDM och MAM som presenteras i [Intune-supportteamets blogg](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

#### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Nya registreringsaviseringar för Apple-enheter <!-- 1471790 -->
Översiktssidan för registrering visar användbara aviseringar för IT-administratörer som gäller hantering av Apple-enheter. Aviseringar visas på översiktssidan när Apple MDM-push-certifikatet upphör att gälla eller redan har gått ut; när DEP-token upphör att gälla eller redan har gått ut eller när det finns enheter i programmet för enhetsregistrering som inte är tilldelade.

#### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Stöd för token-ersättning för appkonfiguration utan enhetsregistrering <!-- 1080364 -->

Du kan använda token för dynamiska värden i appkonfigurationer för appar på enheter som inte har registrerats. Mer information finns i [Add app configuration policies for managed apps without device enrollment](app-configuration-policies-managed-app.md) (Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering).

### <a name="intune-apps"></a>Intune-appar

#### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Uppdateringar i företagsportalappen för Windows 10 <!--1299474-->
Inställningssidan i företagsportalappen för Windows 10 har uppdaterats för att inställningar och avsedda användaråtgärder ska vara mer konsekventa över alla inställningar. Den har också uppdaterats så att den matchar layouten för andra Windows-appar. Du hittar före-/efter-bilder på sidan [nyheter i appgränssnittet](whats-new-app-ui.md).

#### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Informera slutanvändarna om vilken enhetsinformation som kan visas för Windows 10-enheter <!--1337920-->
Vi har lagt till **ägarskapstyp** till skärmen enhetsinformation i företagsportalappen för Windows 10. På så sätt kan användarna få mer information om sekretess direkt från den här sidan från Intunes slutanvändardokumentation. De kommer även att kunna hitta den här informationen på **Om**-skärmen.

#### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Feedbackfrågor för företagsportalappen för Android <!--1165249-->
Företagsportalappen för Android ber nu om feedback från slutanvändare. Denna feedback skickas direkt till Microsoft och ger slutanvändarna en möjlighet att recensera appen i den offentliga Google Play-butiken. Feedback är inte obligatoriskt och kan enkelt ignoreras så att användarna kan fortsätta att använda appen.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

#### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Hjälper dina användare att hjälpa sig själva med företagsportalsappen för Android <!-- 1573324, 1573150, 1558616, 1564878 -->

Företagsportalappen för Android har lagt till anvisningar för slutanvändare för att hjälpa dem att förstå och om möjligt, själva lösa nya problem.
- Slutanvändare dirigeras till [Azure Active Directory-portalen](https://account.activedirectory.windowsazure.com/r/#/profile) för att ta bort en enhet om de har nått det högsta antalet enheter som de tillåts ha.
- Slutanvändare rekommenderas åtgärder att vidta för att hjälpa dem att [åtgärda aktiveringsfel på Samsung Knox-enheter](https://go.microsoft.com/fwlink/?linkid=859718) eller för att [inaktivera energisparläge](/intune-user-help/power-saving-mode-android). Om ingen av dessa lösningar löser problemet tillhandahåller vi en förklaring om hur du [submit logs to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (skickar loggar till Microsoft).

#### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>En ny funktion, ”Lös”, är tillgänglig för Android-enheter <!-- 1583480 -->

Företagsportalappen för Android presenterar en ”Lös”-åtgärd på sidan _Uppdatera enhetsinställningar_. Det här alternativet tar slutanvändaren direkt till inställningen som gör att enheten är icke-kompatibel. Företagsportalappen för Android stöder för närvarande den här åtgärden för inställningarna [enhetens lösenord](/intune-user-help/set-your-pin-or-password-android), [USB-felsökning](/intune-user-help/you-need-to-turn-off-usb-debugging-android) och [Okända källor](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

#### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Förloppsindikator för enhetsinstallationen i Android-företagsportalen <!-- 1565657 -->
Företagsportalappen för Android visar en förloppsindikator för installationen av enheten när en användare registrerar sin enhet. Indikatorn visas nya statusar, som börjar med ”ställer in din enhet...” och sedan ”registrerar din enhet...”, därefter ”slutför registrering av din enhet...” och ”slutför konfigurationen av din enhet...”.

## <a name="week-of-october-23-2017"></a>Veckan som börjar med 23 oktober 2017

### <a name="intune-apps"></a>Intune-appar
#### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Stöd för certifikatbaserad autentisering på företagsportalen för iOS <!--1029830-->
Vi har lagt till stöd för certifikatbaserad autentisering (CBA) i företagsportalappen för iOS. Användare med CBA anger sitt användarnamn och trycker på länken ”Signera med ett digitalt certifikat”. CBA stöds redan på företagsportalappar för Android och Windows. Du kan läsa mer på sidan [Logga in på företagsportal-appen](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

#### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Program som är tillgängliga med eller utan registrering kan nu installeras utan att först uppmanas till registrering. <!-- 1334712 -->

Företagsprogram som har gjorts tillgängliga med eller utan registreringen i Androids företagsportalapp kan nu installeras utan någon uppmaning att registrera.

## <a name="week-of-october-16-2017"></a>Veckan som börjar med 16 oktober 2017
### <a name="device-enrollment"></a>Enhetsregistrering
#### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Stöd för Windows AutoPilot-distributionsprogram i Microsoft Intune  <!-- 747617  -->
Nu kan du använda Microsoft Intune med Windows AutoPilot-distributionsprogrammet och ge dina användare möjlighet att etablera sina företagsenheter utan hjälp från IT-avdelningen. Du kan anpassa OOBE-åtgärderna (Out-of-Box Experience) och vägleda användarna när de ska ansluta sina enheter till Azure AD och registrera sig i Intune. Microsoft Intune och Windows AutoPilot samarbetar för att eliminera behovet av att distribuera, underhålla och hantera operativsystemavbildningar. Läs mer i informationen om att [registrera Windows-enheter med Windows AutoPilot-distributionsprogrammet](https://docs.microsoft.com/intune/enrollment-autopilot).

#### <a name="quick-start-for-device-enrollment-----1425655---"></a>Snabbstart för enhetsregistrering  <!-- 1425655 --> 
Nu är snabbstart tillgängligt i **Enhetsregistrering** och innehåller en tabell med referenser för hantering av plattformar och konfigurering av registreringsprocessen. Via en kort beskrivning av varje objekt och länkar till dokumentation med stegvisa instruktioner får du användbar dokumentation för att enklare komma igång.

#### <a name="device-categorization----1427491---"></a>Enhetskategorisering <!-- 1427491 -->
De registrerade enheternas plattformsdiagram på bladet **Enheter > Översikt** ordnar enheter efter plattform, inklusive Android, iOS, macOS, Windows och Windows Mobile.  Enheter som kör andra operativsystem är grupperade i ”Övrigt”.  Detta inkluderar enheter som har tillverkats av Blackberry och NOKIA.  

Om du vill veta vilka enheter som påverkas i din klientorganisation väljer du **Hantera> Alla enheter** och använder sedan **Filter** för att begränsa **OS**-fältet.

### <a name="device-management"></a>Enhetshantering
#### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – Ny partner för skydd mot mobilhot <!-- 954681 -->  
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Zimperium, en Mobile Threat Defense-lösning som är integrerad med Microsoft Intune.

##### <a name="how-integration-with-intune-works"></a>Så här fungerar integrering med Intune
Risken bedöms utifrån telemetri som samlas in från enheter som kör Zimperium. Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Zimperiums riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera icke-kompatibla enheter för företagets resurser baserat på de hot som har identifierats.

#### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Nya inställningar för enhetsbegränsningsprofilen i Windows 10 <!--- 978575, 1308849, -->  
Vi lägger till nya inställningar i enhetsbegränsningsprofilen i Windows 10 i kategorin Windows Defender SmartScreen.

Mer information om enhetsbegränsningsprofilen för Windows 10 finns i [Inställningar för enhetsbegränsning i Windows 10 och senare]( device-restrictions-windows-10.md).

#### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Fjärrsupport för Windows- och Windows Mobile-enheter <!-- 1070473 -->  
Intune kan nu använda [TeamViewer](https://www.teamviewer.com)-programvaran (säljs separat) för att du ska kunna ge fjärrhjälp till de användare som kör Windows- och Windows Mobile-enheter.

#### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Genomsök enheter med Windows Defender <!-- 1280988  1280990   -->
Du kan nu även köra en **snabbsökning**, **fullständig genomsökning** och **uppdatering av signaturer** med Windows Defender Antivirus på hanterade Windows 10-enheter. På enhetens översiktsblad väljer du den åtgärd som ska köras på enheten. Du uppmanas att bekräfta åtgärden innan kommandot skickas till enheten. 

**Snabbsökning**: En snabbsökning genomsöker platser där skadliga register startas, till exempel registernycklar och kända startmappar i Windows. En snabbsökning tar i genomsnitt fem minuter. I kombination med inställningen **Realtidsskydd alltid på** som söker igenom filer när de öppnas, stängs och när användaren navigerar till en mapp, ger snabbsökningen skydd mot skadlig kod som kan finnas i systemet eller kärnan. Användarna ser resultatet av genomsökningen på sina enheter när den är klar. 

**Fullständig genomsökning**: En fullständig genomsökning kan användas på enheter där det finns en skadlig kod för att se om det finns några inaktiva komponenter som kräver en mer omfattande rensning. Den är även användbar för att köra genomsökningar på begäran. En fullständig genomsökning kan ta en timme att köra. Användarna ser resultatet av genomsökningen på sina enheter när den är klar. 

**Uppdatering av signaturer**: Kommandot för att uppdatera signaturer uppdaterar Windows Defender Antivirus-definitionerna för skadlig kod och signaturerna. På så sätt kan du vara säker på att Windows Defender Antivirus fungerar när det gäller att identifiera skadlig kod. Den här funktionen finns endast för Windows 10-enheter och väntar på att enheten ska ansluta till Internet. 

#### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Knappen för att aktivera/inaktivera har tagits bort från sidan med Intune-certifikatutfärdare i Intune Azure-portalen <!-- 1400455 -->
 Vi tar bort ett extra steg vid konfigurationen av certifikatanslutningen i Intune. För närvarande laddar du ned certifikatanslutningen och aktiverar den sedan i Intune-konsolen. Om du emellertid inaktiverar anslutningsprogrammet i Intune-konsolen fortsätter anslutningsprogrammet att utfärda certifikat.

##### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Från oktober finns inte längre knappen för att aktivera/inaktivera på sidan Intune Certificate Authority (Intune-certifikatutfärdare) i Intune Azure-portalen. Anslutningsfunktionen förblir densamma. Certifikat distribueras fortfarande för enheter som har registrerats i Intune. Du kan fortsätta att ladda ned och installera certifikatanslutningen. Om du vill stoppa att certifikat utfärdas avinstallerar du nu certifikatanslutningen istället för att inaktivera den.

##### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Om du för närvarande har certifikatanslutningen inaktiverad bör du avinstallera den.

### <a name="device-configuration"></a>Enhetskonfiguration
#### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Nya inställningar för enhetsbegränsningsprofilen i Windows 10 Team <!--- 1308838 -->
I den här versionen har vi lagt till många nya inställningar för Windows 10 Team-enhetens begränsningsprofil som hjälper dig att styra Surface Hub-enheter.

Mer information om profilen finns i [Begränsningsinställningar för Windows 10 Team-enheter](device-restrictions-windows-10-teams.md).

#### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Förhindra att användare av Android-enheter ändrar sin enhets datum och tid <!-- 1333292 -->
Du kan använda en [anpassad Android-enhetsprincip](custom-settings-android.md) för att förhindra att Android-enhetsanvändarna ändrar enhetens datum och tid.

Gör detta genom att konfigurera en anpassad Android-princip med inställnings-URI:n ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange Ange den till **TRUE** och tilldela den sedan till de grupper som krävs.

#### <a name="bitlocker-device-configuration----1397398---"></a>Enhetskonfiguration för BitLocker <!-- 1397398 -->
**Windows-kryptering > Grundinställningar** innehåller en ny inställning för **Varning för annan hårddiskkryptering**, där du kan inaktivera [varningen](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) för annan diskkryptering som kanske används på användarens enhet.  Varningen kräver slutanvändarens medgivande innan BitLocker konfigureras på enheten och blockerar installationen av BitLocker tills den har bekräftats av slutanvändaren.  Den nya inställningen inaktiverar varningen till slutanvändaren.


### <a name="app-management"></a>Apphantering
#### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Volyminköpsprogram för företagsprogram synkroniseras nu till din Intune-klient <!-- 800882 -->  
Tredjepartsutvecklare kan även distribuera appar privat till auktoriserade medlemmar i volyminköpsprogram (VPP) för företag som anges i iTunes Connect. Dessa medlemmar i volyminköpsprogram för företag kan logga in i appbutiken för volyminköpsprogram och köpa sina appar.

Med den här versionen synkroniseras appar för volyminköpsprogram för företag som slutanvändaren köper med Intune-klienterna.

#### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Välj landets Apple Store för att synkronisera VPP-appar <!-- 1332311 -->  
Du kan konfigurera volymköpsprogrammets land när du laddar upp din VPP-token. Intune synkroniserar VPP-appar för alla språk från det angivna VPP-landets App Store.

> [!NOTE]  
> I dag synkroniserar Intune endast VPP-appar från VPP-landet som matchar det Intune-språk som Intune-klienten skapades i.


### <a name="intune-apps"></a>Intune-appar
#### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Blockera att kopiera och klistra in mellan arbetsprofiler och personliga profiler i Android for Work <!-- 1098994 -->
I den här versionen kan du konfigurera arbetsprofilen för Android for Work till att blockera kopiering och inklistring mellan arbetsappar och privata appar. Du hittar den här nya inställningen i profilen **Enhetsbegränsningar** för **Android for Work**-plattformen i **Arbetsprofilinställningar**.

#### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Skapa iOS-appar som är begränsade till specifika regionala Apple App Stores <!-- 1281692 -->
Du kommer att kunna ange en språkinställning när du skapar en hanterad app i Apple App Store.

> [!Note]  
> För närvarande kan du bara skapa hanterade appar för Apple App Store som finns i USA.

####  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Uppdatera VPP-användare och enhetslicensierade appar i iOS <!-- 1305564 -->  
Du kommer att kunna konfigurera iOS VPP-token för att uppdatera alla appar som köpts för den token via Intune-tjänsten. Intune identifierar VPP-appuppdateringar i appbutiken och push-installerar dem automatiskt på enheten när den checkas in.

Instruktioner om hur du konfigurerar en VPP-token och aktiverar automatiska uppdateringar finns i [Så här hanterar du iOS-appar som har köpts via ett volyminköpsprogram med Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka
#### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Användarenhetens associationsentitetssamling lades till i datamodellen för Intunes informationslager <!-- 1187917 -->
Du kan nu skapa rapporter och datavisualiseringar med hjälp av enhetens associationsinformation som associerar användaren och enhetens entitetssamlingar. Datamodellen kan nås via Power BI-filen (PBIX) som hämtas från Intune-sidan Informationslager via OData-slutpunkten, eller genom att utveckla en anpassad klient.

#### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Kontrollera principefterlevnaden för Windows 10:s uppdateringstestgrupper <!-- 1067886 -->
Du kommer att kunna granska en principrapport för din Windows 10-uppdateringstestgrupp i Programuppdateringar > Distributionsstatus per uppdateringstestgrupp. Principrapporten innehåller distributionsstatus för de uppdateringstestgrupper som du har konfigurerat. 

#### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Ny rapport som visar en lista över iOS-enheter med äldre iOS-versioner <!-- 1352223 -->
Rapporten **Out-of-date iOS Devices** (Gamla iOS-enheter) är tillgänglig i arbetsytan **Programuppdateringar**. I rapporten kan du visa en lista över alla övervakade iOS-enheter som har varit mål för en iOS-uppdateringsprincip och som har tillgängliga uppdateringar. Du kan se en status för varje enhet och se varför enheten inte har uppdaterats automatiskt. 

#### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Visa programskyddets principtilldelningar för felsökning <!--  1475003 -->
I den här kommande versionen kommer alternativet **Appskyddsprincip** att läggas till i listrutan **Tilldelningar** på bladet för felsökning. Nu kan du välja programskyddsprinciper för att se de programskyddsprinciper som tilldelats de valda användarna.



## <a name="week-of-october-2-2017"></a>Veckan då den 2 oktober 2017 infaller
### <a name="intune-apps"></a>Intune-appar
#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Förbättringar av arbetsflödet för enhetskonfiguration i företagsportalen <!--1490692-->
Vi har förbättrat arbetsflödet för enhetskonfiguration i företagsportalappen för Android. Språket är mer användarvänligt och specifikt för ditt företag, och vi har kombinerat skärmar där det är möjligt. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md#week-of-october-2-2017).

#### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Förbättrade riktlinjer för begäran om åtkomst till kontakter på Android-enheter <!--1484985-->

Företagsportalappen för Android kräver ofta att slutanvändaren godkänner behörighet för Kontakter. Om en slutanvändare nekar denna åtkomst kommer det nu att visas en avisering i appen som uppmanar till att godkänna det för villkorlig åtkomst. 

#### <a name="secure-startup-remediation-for-android---1490712--"></a>Reparation av säker start för Android <!--1490712-->

Slutanvändare med Android-enheter kan trycka på orsaken till bristande efterlevnad i företagsportalappen. Om möjligt kommer de då direkt till rätt plats i inställningsappen för att kunna åtgärda problemet. 

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Ytterligare push-meddelanden för slutanvändare i företagsportalappen för Android Oreo <!--1475932-->

Slutanvändarna ser ytterligare meddelanden som anger när företagsportalen för Android Oreo utför bakgrundsaktiviteter, till exempel när principer hämtas från Intune-tjänsten. Detta ger bättre transparens för slutanvändarna eftersom de ser när företagsportalen utför administrativa uppgifter på deras enheter. Det här är en del av [optimeringen av företagsportalens användargränssnitt](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) för företagsportalappen för Android Oreo. 

Det finns ytterligare optimeringar för nya UI-element som är aktiverade i Android Oreo.  Slutanvändarna ser ytterligare meddelanden som anger när företagsportalen utför bakgrundsaktiviteter, till exempel när principer hämtas från Intune-tjänsten.  Detta ger bättre transparens för slutanvändarna eftersom de ser när företagsportalen utför administrativa uppgifter på deras enheter.

#### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nya funktioner i företagsportalappen för Android med arbetsprofiler <!-- 1485783 -->

När du registrerar en Android for Work-enhet med en arbetsprofil, är det företagsportalappen i arbetsprofilen som utför hanteringsuppgifterna på enheten. 

Såvida du inte använder en MAM-aktiverad app i den personliga profilen, har du inte längre någon användning av företagsportalappen för Android. För att förbättra användningen av arbetsprofilen kommer Intune automatiskt dölja den personliga företagsportalappen efter en lyckad arbetsprofilregistrering.

Företagsportalappen för Android kan aktiveras när som helst i den personliga profilen genom att du bläddrar efter [Företagsportal i Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) och sedan trycker på **Aktivera**.

#### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Företagsportal för Windows 8.1 och Windows Phone 8.1 flyttas till hanteringsläget <!--1428681-->

Från oktober 2017 flyttas företagsportalapparna för Windows 8.1 och Windows Phone 8.1 till hanteringsläget. Det innebär att program och befintliga scenarier, till exempel registrering och kompatibilitet, fortsätter att ha stöd för dessa plattformar. De här programmen fortsätter att vara tillgängliga för hämtning via den befintliga versionens kanaler, till exempel Microsoft Store. 

När programmen finns i hanteringsläget kommer de endast kunna ta emot kritiska säkerhetsuppdateringar. Inga ytterligare uppdateringar eller funktioner kommer att släppas för dessa program. Om du vill ha nya funktioner rekommenderar vi att du uppdaterar enheterna till Windows 10 eller Windows 10 Mobile. 


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>Blockera enhetsregistrering med Samsung Knox som inte stöds <!-- 1490695 -->

Företagsportalappen försöker endast att registrera Samsung Knox-enheter som stöds. För att undvika Knox-aktiveringsfel som förhindrar MDM-registrering görs försök att genomföra enhetsregistrering endast om enheten syns i [listan över enheter som har publicerats av Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Samsung-enheter kan ha modellnummer som har stöd för Knox medan andra inte stöds. Kontrollera att Knox är kompatibelt med enhetsåterförsäljaren innan du köper och distribuerar. En fullständig lista över verifierade enheter finns i [Inställningar för Android- och Samsung Knox Standard-principer](/intune/supported-devices-browsers.md#intune-supported-devices).

#### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Stöd för Android 4.3 och lägre upphör <!-- 1171126, 1326920 -->
Hanterade appar och företagsportalappen för Android kräver Android 4.4 och högre för åtkomst till företagets resurser. I december kommer alla registrerade enheter att tvingas att dras tillbaka, vilket innebär att de förlorar åtkomst till företagets resurser. Om du använder principer för appskydd utan MDM kommer appar inte ta emot uppdateringar och kvaliteten på användningsupplevelsen minskar över tid.

#### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Informera slutanvändarna om vilken enhetsinformation som kan visas på registrerade enheter <!--1165314-->
Vi lägger till **Typ av ägarskap** på skärmen Enhetsinformation i alla företagsportalappar. På så sätt kan användarna få mer information om sekretess direkt från artikeln [Vilken information kan företaget se?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Det här kommer snart att lanseras i alla företagsportalappar. Vi tillkännagav detta för iOS under [september](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).


## <a name="week-of-september-25-2017"></a>Veckan då den 25 september 2017 infaller

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="intune-supports-ios-11---1428975--"></a>Intune stöder iOS 11 <!--1428975-->
Intune stöder iOS 11. Det här meddelades tidigare på [Intunes supportblogg](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

#### <a name="end-of-support-for-ios-80----1164477---"></a>Stöd för iOS 8.0 upphör <!-- 1164477 -->
Hanterade appar och företagsportalappen för iOS kräver iOS 9.0 och högre för åtkomst till företagets resurser. Enheter som inte är uppdaterade innan september kommer inte längre att ha åtkomst till Företagsportalen eller apparna. 

### <a name="intune-apps"></a>Intune-appar

#### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Uppdateringsåtgärden lades till i företagsportalappen för Windows 10 <!--1132468-->
Företagsportalappen för Windows 10 tillåter att användarna uppdaterar data i appen genom att antingen dra för att uppdatera eller trycka på F5 på stationära datorer.



## <a name="notices"></a>Meddelanden

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Planera för förändring: Använd Intune på Azure för MDM-hanteringen <!-- 1227338 -->
För över ett år sedan tillkännagav vi en [allmänt tillgänglig förhandsversion av Intune på Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) och för sex månader sedan följde vi upp med [allmän tillgänglighet för den nya administratörsupplevelsen](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) för Intune. Från och med 2 april 2018 kommer vi att avsluta hantering av mobilenheter (MDM) i den klassiska Silverlight-konsolen för de kunder som använder fristående Intune. Du kan istället använda [Intune på Azure](https://aka.ms/Intune_on_Azure) för MDM-behoven. Om du fortfarande använder den klassiska konsolen för MDM rekommenderar vi att du ägnar en stund åt att bekanta dig med Intune på Azure. Vi förväntar oss inte att slutanvändarna ska påverkas av denna förändring. Klassisk datorhantering kommer att finnas kvar i Silverlight. Du kan läsa mer om den här förändringen och hur den påverkar dig [här](https://aka.ms/Intune_on_Azure_mdm).


### <a name="plan-for-change-easy-assist-end-of-life----1556480---"></a>Plan för förändring: Easy Assist blir inaktuell <!-- 1556480 -->
Intune använder Microsoft Easy Assist för fjärrhjälp för datorhantering. En sak du kanske inte vet är att Microsoft Easy Assist är en komponent i Office Live Meeting, en tjänst som blev inaktuell den 31 december 2017. Intunes Easy Assist-erbjudande kommer därför också att nå slutet på sin livscykel den 31 december 2017.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Hantera Android for Work-enheter oberoende av Android-enheter <!-- 1490731 EEready-->    
**Obs!** Följande ändringar börjar distribueras med novemberuppdateringen, men det kan ta tid innan de tillämpas på ditt konto. Du får ett bekräftelsemeddelande i Office 365-portalen när ändringarna är applicerade på ditt konto. Efter distributionen får du ytterligare hanteringsalternativ. Slutanvändarens upplevelse ändras inte under distributionen.

Intune stöder registrering av hantering av Android for Work-enheter oberoende av Android-plattformen. De här inställningarna hanteras under **Enhetsregistrering** > **Registreringsbegränsningar** > **Begränsningar för enhetstyper**. (De fanns tidigare **Enhetsregistrering** > **Android for Work-registrering** > **Registreringsinställningar för Android for Work**.)

Som standard är dina Android for Work-enhetsinställningar samma som dina inställningar för Android-enheter. Men när du har ändrat dina Android for Work-inställningar kommer det här inte längre att vara fallet.

Om du blockerar registrering av personligt ägda Android for Work-enheter så kan endast företagsägda Android-enheter att registrera Android for Work.

Tänk på följande när du konfigurerar nya inställningar:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Om du aldrig tidigare har publicerat Android for Work-registrering

Den nya Android for Work-plattformen blockeras av standardbegränsningarna för enhetstyper. När du har publicerat funktionen kan du tillåta enheter att registreras med Android for Work. För att göra detta ändrar du på standardvärdena eller skapar en ny begränsning för enhetstyp för att ersätta begränsningen för enhetstyp som är standard.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Om du har publicerat Android for Work-registrering

Om du har publicerat tidigare så beror din situation på de inställningar du väljer:

| Inställningen | Statusen för Android for Work under begränsningar för enhetstyper | Obs! |
| --- | --- | --- |
| **Hantera alla enheter som Android** | Blockerad | Alla Android-enheter måste registreras utan Android for Work. |
| **Hantera enheter som stöds som Android for Work** | Tillåts | Alla Android-enheter som har stöd för Android for Work måste registreras med Android for Work. |
| **Hantera endast enheter som stöds i de här grupperna som Android for Work för användare** | Blockerad | En separat princip för begränsningar för enhetstyper skapades för att åsidosätta standardinställningen. Den här principen definierar de grupper som du tidigare valde för att tillåta Android for Work-registrering. Användare i de valda grupperna fortsätter att kunna registrera sina Android for Work-enheter. Alla andra användare är begränsade från att registrera med Android for Work. |

I samtliga fall bevaras din avsedda regler. Ingen åtgärd krävs från din sida för att underhålla den globala begränsningen eller per grupp-begränsningen för Android for Work i din miljö.

### <a name="deprecating-support-for-os-x-mavericks-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>Avsluta stöd för OS X Mavericks 10.10 och äldre versioner av macOS <!--1489263, plan for change for 1802-->
Vi vill meddela att vi påbörjar avvecklingen av registrering för enheter med OS X Yosemite 10.10 och äldre versioner av macOS i februari 2018. Intune har fullständigt stöd för OS X El Capitan 10.11 och senare.

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Ny sökväg för hanterade enheter i Graph API <!-- 1586728 -->
Vi gör en ändring i sökvägen som används för att nå hanterade enheter i betaversionen av Graph API. 

| | |
|--|--|
| Aktuell sökväg |  https://graph.microsoft.com/beta/managedDevices |
| Ny sökväg | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

Båda sökvägarna fungerar oktober ut. Efter lanseringen av tjänsten i oktober fungerar endast den nya sökvägen.  Om du använder Graph API för att få åtkomst till hanterade enheter ska du uppdatera och verifiera dina skript och program med den nya sökvägen. För ytterligare ändringar kollar du den månadsvisa [ändringsloggen för Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog).


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->
För Intune-konton som skapades efter januari 2017 har Intune aktiverat direktåtkomst till registreringsscenarier i Apple med arbetsflödet Registrera enheter i Azure-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i den klassiska Intune-portalen. Intune-konton som skapades före januari 2017 måste migreras en gång innan dessa funktioner är tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till Azure-portalen.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Administratörsroller ersätts i Azure Portal
De befintliga MAM-administratörsrollerna (deltagare, ägare och skrivskyddat) som används i den klassiska Intune-portalen (Silverlight) ersätts med en helt ny uppsättning rollbaserade administratörskontroller (RBAC) i Intune Azure Portal. När du har migrerat till Azure-portalen måste du tilldela de nya administratörsrollerna till dina administratörer. Mer information om RBAC och nya de nya rollerna finns i [Rollbaserad åtkomstkontroll för Microsoft Intune](/intune/role-based-access-control).

## <a name="whats-coming"></a>Kommande nyheter

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Uppdatering av användarupplevelsen för appen Företagsportal för iOS <!--1412866-->

Vi kommer att släppa en större uppdatering av användarupplevelsen i appen Företagsportal för iOS. Uppdateringen medför en komplett visuell uppfräschning, vilket omfattar ett modernare utseende med bättre användbarhet och tillgänglighet. Alla befintliga funktioner i företagsportalen för iOS kommer att finnas kvar.

Vi har en förhandsversion av den uppdaterade appen Företagsportal för iOS som är tillgänglig via Apple TestFlight-programmet, som du kan använda och lämna feedback på. Registrera dig på https://aka.ms/intune_ios_cp_testflight för att få åtkomst till TestFlight.

### <a name="conditional-access-policies-for-intune-will-only-be-available-from-the-azure-portal-----1737088---"></a>Principer för villkorlig åtkomst för Intune är endast tillgängliga från Azure Portal <!-- 1737088 -->
Vi gör det enklare för dig att konfigurera och hantera villkorlig åtkomst. För närvarande kan du hantera villkorlig åtkomst från bladet Intune App Protection (MAM) och via klassiska Azure AD i [Windows Azure Portal](https://manage.windowsazure.com). Från och med januari kan du endast konfigurera och hantera dina principer på [Azure Portal](https://portal.azure.com) från **Azure Active Directory** > **Villkorlig åtkomst**. Du kan även komma åt det här bladet från Intune på Azure Portal på **Intune** > **Villkorlig åtkomst**.

### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747--"></a>Hantera Jamf-registrerade macOS-enheter med Intunes motor för enhetsefterlevnad <!--1592747-->
Från och med tidigt 2018, skickar Jamf statusinformation för macOS-enheter till Intune, som sedan utvärderar den för efterlevnad av de principer som definierats i Intune-konsolen. Baserat på enhetens efterlevnadsstatus samt andra villkor (till exempel plats, användarrisk osv.), framtvingar villkorsstyrd åtkomst efterlevnad för macOS-enheter som har åtkomst till molnet och lokala program som är anslutna till Azure AD, inklusive Office 365.

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

## <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Nyheter i företagsportalens gränssnitt](whats-new-app-ui.md)
* [Nyheter från föregående månad](whats-new-archive.md)
