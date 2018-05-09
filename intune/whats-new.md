---
title: Nyheter i Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Ta reda på vad som är nytt i Intune Azure-portalen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/27/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 68997e16269f7f7a9265fc96d04de2c39c9fefeb
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Läs mer om varje veckas nyheter i Microsoft Intune. Du kan också läsa mer om [kommande ändringar](#whats-coming), [viktiga meddelanden](#notices) om tjänsten och information om [tidigare versioner](whats-new-archive.md). Vissa funktioner kan distribueras över flera veckor och kanske inte är tillgängliga för alla kunder den första veckan.

> [!Note]
> På [hybridsidan med senaste nytt](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) finns mer information om nya funktioner för hybridhantering av mobilenheter (MDM).


<!-- Common categories:  
  ### App management
  ### Device enrollment
  ### Device management
  ### Device configuration
  ### Intune apps
  ### Monitor and troubleshoot
  ### Role-based access control

-->   

## <a name="week-of-april-23-2018"></a>Veckan 23 april 2018

### <a name="app-management"></a>Apphantering

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Lösenordsstöd för MAM PIN-kod på Android<!-- 1438086 -->

Intune-administratörer kan ange ett programstartskrav för att framtvinga ett lösenord i stället för en numerisk MAM PIN-kod. Om det har konfigurerats måste användaren vid uppmaning ställa in och använda ett lösenord innan användaren får åtkomst till MAM-integrerade program. Ett lösenord definieras som en numerisk PIN-kod med minst ett specialtecken eller en gemen/versal. Intune stöder lösenord på liknande sätt som numeriska PIN-koder. En minsta längd kan anges, vilket tillåter upprepning av tecken och sekvenser via administratörskonsolen. Den här funktionen kräver den senaste versionen av företagsportalen för Android. Funktionen finns redan tillgänglig för iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Stöd för verksamhetsspecifika appar (LOB) för macOS <!-- 1473977 -->
I Microsoft Intune går det att installera branschspecifika macOS-appar från Azure Portal. Du kommer att kunna lägga till en branschspecifik macOS-app i Intune som redan har förbehandlats av verktyget i GitHub. I Azure Portal väljer du **Mobilappar** på bladet **Intune**. På bladet **Mobilappar** väljer du **Appar** > **Lägg till**. På bladet **Lägg till app** väljer du **Branschspecifik app**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Inbyggd apptilldelning av gruppen Alla användare och Alla enheter för Android for Work (AFW) <!-- 1813073 -->
Du kan använda de inbyggda grupperna **Alla användare** och **Alla enheter** vid AFW-apptilldelning. Mer information finns i [Inkludera och exkludera apptilldelningar i Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune kommer att installera om obligatoriska appar som avinstalleras av användare <!-- 1947010 -->
Om en slutanvändare avinstallerar en obligatorisk app, installerar Intune automatiskt om appen igen inom 24 timmar i stället för att vänta på omvärderingscykeln på 7 dagar.

### <a name="device-configuration"></a>Enhetskonfiguration

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Enhetens profildiagram och statuslista visar alla enheter i en grupp <!-- 1449153 eeready -->
När du konfigurerar en enhetsprofil (**Enhetskonfiguration** > **Profiler**) väljer du enhetsprofil, till exempel iOS. Du tilldelar profilen till en grupp med både iOS-enheter och enheter som inte är iOS. Antalet i det grafiska diagrammet visar att profilen tillämpas på både iOS-enheter *och* enheter som inte är iOS (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**). När du väljer det grafiska diagrammet på fliken **Översikt** visar **Enhetsstatus** alla enheterna i gruppen, i stället för enbart iOS-enheterna. 

Med den här uppdateringen visar det grafiska diagrammet (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**) endast antalet för den specifika enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för iOS-enheter, visar diagrammet endast antal iOS-enheter. Om du väljer det grafiska diagrammet och öppnar **Enhetsstatus**, visas endast iOS-enheterna.

När uppdateringen gjorts har det grafiska diagrammet tillfälligt tagits bort. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>AlwaysOn-VPN för Windows 10 <!--1333666 -->

För närvarande kan [AlwaysOn](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) användas på Windows 10-enheter med hjälp av en anpassad VPN-profil (virtuellt privat nätverk) som skapats med OMA-URI.

Med den här uppdateringen kan administratörer aktivera AlwaysOn för VPN-profiler i Windows 10 direkt i Intune i Azure-portalen. VPN-profiler med AlwaysOn ansluts automatiskt när:

- Användarna loggar in på sina enheter
- Nätverket på enheten ändras
- Skärmen på enheten sätts på efter att ha varit avstängd

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nya skrivarinställningar för utbildningsprofiler <!-- 1308900 -->

För utbildningsprofiler finns nya inställningar under kategorin **Skrivare**: **Skrivare**, **Standardskrivare**, **Lägg till nya skrivare**.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Visa nummerpresentation i personlig profil – Android for Work <!--1098984 -->
När du använder en personlig profil på en enhet, kan slutanvändare inte se nummerpresentation för en arbetskontakt. 

I och med uppdateringen finns en ny inställning i **Android for Work** > **Enhetsbegränsningar** > **Arbetsprofilinställningar**:
- Visa arbetskontaktens nummerpresentation i personlig profil

När aktiverat (inte konfigurerat), visas arbetskontaktens nummerpresentation i den personliga profilen. När blockerad, visas inte arbetskontaktens nummerpresentation i den personliga profilen. 

Gäller för: Androids arbetsprofilenheter på Android OS v6.0 och senare

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nya Windows Defender Credential Guard-inställningar har lagts till i inställningarna för slutpunktsskydd<!--1102252 --><!--from 1802 and 1804-->

Med denna uppdatering, inkluderar [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Enhetskonfiguration** > **Profiler** > **Slutpunktsskydd**) följande inställningar: 

- **Windows Defender Credential Guard**: Aktiverar Credential Guard med virtualiseringsbaserad säkerhet. Aktivering av den här funktionen hjälper till att skydda autentiseringsuppgifterna vid nästa omstart när både **Säker start för Säkerhetsnivå för plattform** och **Virtualiseringsbaserad säkerhet** är aktiverade. Alternativen är:
  - **Inaktiverad**: Om Credential Guard tidigare slagits på med alternativet**Aktiverat utan lås**, slås Credential Guard av på distans.

  - **Aktiverat med UEFI-lås**: Ser till att Credential Guard inte kan inaktiveras med registernyckel eller via en grupprincip. Om du vill inaktivera Credential Guard när du använder den här inställningen måste du ställa in Grupprincip som ”Inaktiverad”. Ta sedan bort säkerhetsfunktionen från varje dator med en användare fysiskt närvarande. De här stegen rensar den kvarstående konfigurationen i UEFI. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.

  - **Aktiverat utan lås**: Medför att Credential Guard kan inaktiveras via fjärranslutning med grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 eller senare (version 1511).

Följande beroende tekniker aktiveras automatiskt när du konfigurerar Credential Guard: 

  - **Aktivera virtualiseringsbaserad säkerhet (VBS)**: Aktiverar virtualiseringsbaserad säkerhet (VBS) vid nästa omstart. Virtualiseringsbaserad säkerhet använder Windows Hypervisor för att ge stöd för säkerhetstjänster och kräver Säker start.
  - **Säker start med Direkt minnesåtkomst**: Aktiverar VBS med Säker start och Direkt minnesåtkomst. DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Använda ett anpassat certifikatmottagarnamn på SCEP-certifikat <!-- 2064190 -->
Du kan använda det egna namnet **OnPremisesSamAccountName** i en anpassad certifikatmottagare för en SCEP-certifikatprofil. Du kan till exempel använda `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Blockera kamera och skärmbilder i Android for Work <!-- 1098977 eeready-->
Två nya egenskaper kan blockeras när du konfigurerar enhetsbegränsningar för Android-enheter: 
- Kamera: Blockerar åtkomsten till alla kameror på enheten
- Skärmbild: Blockerar skärmbildtagning och förhindrar också att innehållet visas på enheter som inte har en säker videoutgång

Gäller Android for Work.


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nya registreringssteg för användarna på enheter med macOS High Sierra 10.13.2+ <!--1734567 -->
I macOS High Sierra 10.13.2 finns nu begreppet ”Användargodkänd” MDM-registrering. Godkända registreringar tillåter Intune att hanterar vissa säkerhetskänsliga inställningar. Mer information finns i Apples supportdokumentation här: https://support.apple.com/HT208019.

Enheter som registreras med macOS-företagsportalen betraktas som ”Inte användargodkända” tills användaren öppnar systeminställningarna och ger sitt manuella godkännande. Därför dirigerar macOS-företagsportalen nu användare av macOS 10.13.2 och senare till att manuellt godkänna registreringen i slutet av registreringsprocessen. Intune-administratörskonsolen rapporterar om en registrerad enhet är användargodkänd.



### <a name="device-management"></a>Enhetshantering

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>Advanced Threat Protection (ATP) och Intune är helt integrerade <!-- EEready 1629303 -->

[Avancerat skydd (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) visar risknivån för Windows 10-enheter. I Windows Defender Security Center (ATP-portal), kan du skapa en anslutning till Microsoft Intune. När du skapat anslutningen används en efterlevnadsprincip av Intune för att fastställa en godtagbar hotnivå. Om hotnivån överskrids kan sedan en villkorlig åtkomstprincip för Azure Active Directory (AD) blockera åtkomst till olika appar i din organisation.

Den här funktionen tillåter ATP att söka igenom filer, identifiera hot och rapportera eventuella risker på Windows 10-enheter.

Se [Aktivera ATP med villkorlig åtkomst i Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Stöd för användarlösa enheter <!-- 1637553 -->
Intune stöder möjligheten att utvärdera efterlevnaden på en användarlös enhet som exempelvis Microsoft Surface Hub. Policyer för efterlevnad kan riktas mot specifika enheter. Det innebär att efterlevnad (och inkompatibilitet) kan fastställas för enheter som inte har någon associerad användare.

#### <a name="delete-autopilot-devices----1713650---"></a>Ta bort AutoPilot-enheter <!-- 1713650 -->
Intune-administratörer kan [ta bort AutoPilot-enheter](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Förbättrad enhetsborttagning <!--1832333 -->
Du kommer inte längre behöva ta bort företagets data eller fabriksåterställa en enhet innan du [tar bort enheten från Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Om du vill se den nya funktionen loggar du in på Intune och väljer **Enheter** > **Alla enheter** > namnet på enheten > **Ta bort**.

Om du fortfarande vill att rensningen ska utföras kan du använda standardenhetens livscykel med hjälp av **Ta bort företagsinformation** och **Fabriksåterställning** innan du väljer **Ta bort**. 

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-profiler flyttas till en grupp som är riktad mot <!-- 1877935 -->
AutoPilot-distributionsprofiler kan tilldelas till Azure AD-grupper som innehåller AutoPilot-enheter.

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Spela upp ljud på iOS när den befinner sig i Borttappat läge <!-- 1947769 -->
När övervakade iOS-enheter är i hanteringen av mobilenheters (MDM) [Borttappat läge](device-lost-mode.md), kan du [spela upp ett ljud](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Enheter** > **Alla enheter** > välj en iOS-enhet > **Översikt** > **Mer**). Ljudet fortsätter att spelas upp tills enheten tas bort från Borttappat läge, eller en användare stänger av ljudet. Gäller för iOS-enheter 9.3 och nyare.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Blockera eller tillåta webbresultat i sökningar på en Intune-enhet <!--1972804-->

Administratörer kan nu blockera webbresultat från sökningar gjorda på en enhet.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Förbättrade felmeddelanden när Apple MDM-pushcertifikat inte kan överföras <!-- 2172331 -->

Felmeddelandet förklarar att samma Apple-ID måste användas när du förnyar ett befintligt MDM-certifikat.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Testa företagsportalen för macOS på virtuella datorer <!-- 2216679 -->

Vi har publicerat vägledning som hjälper IT-administratörer testa företagsportalappen för macOS i Parallels Desktop och VMware Fusion. Du hittar mer information i avsnittet om att [registrera virtuella macOS-datorer för testning](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Användargränssnitt

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Förbättrade enhetspaneler i företagsportalen för Windows 10 <!--2213364 -->

Panelerna har uppdaterats för att blir lättillgängligare för användare med sämre syn och för att fungera bättre tillsammans med skärmläsningsverktyg.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Skicka diagnostikrapporter i företagsportalappen för macOS <!-- 2216677 -->
Företagsportalappen för macOS-enheter har uppdaterats för att förbättra hur användarna rapporterar Intune-relaterade fel. Från företagsportalappen kan dina anställda:

- Ladda upp diagnostikrapporter direkt till Microsofts utvecklingsteam.
- E-posta ett incident-ID till ditt företags IT-supportteam.

Mer information finns i [Skicka fel till rätt personer för din hanterade macOS-enhet](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune anpassar sig efter Fluent Design System i företagsportalappen för Windows 10 <!-- 1195010 WNready -->
Intunes företagsportalapp för Windows 10 har uppdaterats med [Fluent Design Systems navigeringsvy](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics). Längs appen ser du en statisk, lodrät lista över alla sidor på översta nivån. Klicka på en länk för att snabbt visa och växla mellan sidor. Det här är den första av flera uppdateringar som visas som en del av vårt pågående arbete för att skapa en mer anpassningsbar, empatisk och bekant upplevelse i Intune. Gå till avsnittet om [nyheter i appgränssnittet](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Veckan 16 april 2018

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>Använda Cisco AnyConnect klienten för iOS <!-- EEready 1333708 -->

När du skapar en ny VPN-profil för iOS finns nu två alternativ: **Cisco AnyConnect** och **Cisco Legacy AnyConnect**. Cisco AnyConnect-profiler stöder 4.0.7x och nyare versioner. Befintliga iOS Cisco AnyConnect VPN-profiler är märkta **Cisco Legacy AnyConnect** och kommer fortsatt att fungera med Cisco AnyConnect 4.0.5x och äldre versioner som de gör i dag.

> [!NOTE]
> Den här ändringen gäller bara för iOS. Det finns fortfarande ett enda Cisco AnyConnect-alternativ för Android-, Android for Work- och macOS-plattformar.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>MacOS Jamf-registrerade enheter kan nu registreras med Intune <!-- 2370684 -->

Version 1.3 och 1.4 av macOS-företagsportal registrerades inte Jamf-enheter med Intune korrekt. Version 1.4.2 av macOS-portalen åtgärdar det här problemet.


## <a name="week-of-april-9-2018"></a>Veckan som börjar med 9 april 2018

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Uppdaterad hjälpfunktion i företagsportalappen för Android <!-- 1631531 -->

Vi har uppdaterat hjälpfunktionen i Android-versionen av företagsportalappen och anpassat den till bästa praxis för Android-plattformen. När användarna stöter på ett problem i appen kan de nu trycka på **Menu (Meny)** > **Help (Hjälp)** och:
- Skicka diagnostikloggar till Microsoft.
- Skicka ett e-postmeddelande som beskriver problemet och incident-ID till företagets supportavdelning.  

Om du vill kolla in den uppdaterade hjälpfunktionen går du till [Send logs using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) (Skicka loggar via e-post) och [Send errors to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (Skicka fel till Microsoft).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nytt trenddiagram för registreringsfel och tabell över felorsaker <!-- 1471783 -->

På registreringsöversiktssidan kan du se trenden för registreringsfel och de fem viktigaste felorsakerna. Genom att klicka på diagrammet eller tabellen kan du gå in på detaljnivå för att hitta felsökningstips och åtgärdsförslag.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Uppdatera var du konfigurerar dina appskyddsprinciper <!-- 2144597 -->

I tjänsten Microsoft Intune i Azure Portal kommer vi att tillfälligt dirigera om dig från bladet för tjänsten **Intune-appskydd** till bladet **Mobilapp**. Alla dina appskyddsprinciper finns redan på bladet **Mobilapp** i Intune under appkonfigurationen. I stället för att gå till Intune-appskydd går du bara till Intune. I april 2018 stoppar vi omdirigeringen och tar helt bort bladet för tjänsten **Intune-appskydd** så att det bara finns en plats för appskyddsprinciper i Intune. 

**Hur påverkar det här mig?**
Den här förändringen påverkar både kunder som har fristående Intune och hybridkunder (Intune med Configuration Manager). Den här integreringen hjälper till att förenkla administrationen av molnhanteringen.

**Vad kan jag göra för att förbereda mig för den här ändringen?**
Lägg till **Intune** som favorit i stället för bladet för tjänsten **Intune-appskydd**, och se till att du känner till arbetsflödet för appskyddsprinciper på bladet **Mobilapp** i Intune. Vi omdirigerar under en kort tidsperiod och tar sedan bort **appskyddsbladet**. Tänk på att alla appskyddsprinciper redan finns i Intune och att du kan ändra dina villkorliga åtkomstprinciper. Mer information om hur du ändrar principer för villkorlig åtkomst finns [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Ytterligare information finns i [Vad är appskyddsprinciper?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Veckan 2 april 2018

### <a name="intune-apps"></a>Intune-appar

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Uppdatering av användarupplevelsen för appen Företagsportal för iOS <!--1412866 -->
Vi har släppt en större uppdatering av användarupplevelsen i företagsportalappen för iOS. Uppdateringen är en fullständig visuell omarbetning som ger appen en modernare design. Vi har bevarat appens funktionalitet men förbättrat användarvänligheten och tillgängligheten.  

Andra nyheter:
- Stöd för iPhone X.
- Snabbare appstart och inläsning som sparar tid för användarna.
- Fler förloppsindikatorer som ger användarna den senaste statusinformationen.
- Sättet att skicka loggar har förbättrats och det har blivit enklare att rapportera om något går fel.  

Gå till avsnittet om [nyheter i appgränssnittet](whats-new-app-ui.md).

#### <a name="protect-on-premise-exchange-data-using-intune-app-and-ca----1056954---"></a>Skydda lokala Exchange-data med hjälp av Intune APP och CA <!-- 1056954 -->
Du kan nu använda Intunes appskyddsprincip (APP) och villkorlig åtkomst (CA) för att skydda åtkomsten till lokala Exchange-data med Outlook Mobile. Om du vill lägga till eller ändra en appskyddsprincip i Azure Portal väljer du **Microsoft Intune** > **Mobilappar** > **Appskyddsprinciper**. Innan du använder den här funktionen måste du se till att du uppfyller [kraven för Outlook för iOS och Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="week-of-march-26-2018"></a>Veckan som börjar med 26 mars 2018

### <a name="app-management"></a>Apphantering

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Aviseringar för utgående verksamhetsspecifika appar för Microsoft Intune <!-- 748789 -->

Du får ett meddelande från Intune i Azure Portal om verksamhetsspecifika iOS-appar som snart förfaller. När du laddar upp en ny version av en verksamhetsspecifik iOS-app tar Intune bort förfalloaviseringen från applistan. Förfalloaviseringen är endast aktiv för nyligen överförda verksamhetsspecifika iOS-appar. En varning visas 30 dagar innan etableringsprofilen för den verksamhetsspecifika iOS-appen upphör att gälla. När den upphör ändras aviseringen till Upphört.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Anpassa teman för företagsportalen med hexkoder <!--1049561 -->

Du kan anpassa temafärgen i företagsportalens appar med hexkoder. När du anger en hexkod kan Intune bestämma vilken textkod som ger den högsta kontrastnivån mellan textfärgen och bakgrundsfärgen. Du kan förhandsgranska både textfärgen och företagets logotyp mot färgen i **Mobilappar** > **Företagsportal**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inklusive och exklusive apptilldelning baserat på grupperna för Android Enterprise <!-- 1813081 -->

Android Enterprise (tidigare Android for Work) stöder inkludering och exkludering av grupper, men stöder inte de inbyggda grupperna **Alla användare** och **Alla enheter**. Mer information finns i [Inkludera och exkludera apptilldelningar i Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Enhetshantering

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Nya säkerhetsförbättringar i Intune-tjänsten <!-- 1637539 -->   

Vi har introducerat en växlingsknapp i Intune på Azure som de som använder fristående Intune kan använda för att hantera enheter utan tilldelad princip som **kompatibla** (säkerhetsfunktionen av) eller som **inte kompatibla** (säkerhetsfunktionen på). Detta gör att det endast går att komma åt resurser efter att enhetskompatibiliteten har utvärderats.

Den här funktionen påverkar dig på olika sätt beroende på om du redan har tilldelats policyer för efterlevnad eller inte.

- Om du har ett nytt eller befintligt konto och inte har några efterlevnadsprinciper tilldelade till enheterna ställs växlingsknappen automatiskt in på **kompatibel**. Funktionen är inaktiverad som standard i konsolen. Slutanvändaren påverkas inte.
- Om du har ett befintligt konto och har enheter med en tilldelad policy för efterlevnad är växlingsknappen automatiskt inställd på **inte kompatibel**. När marsuppdateringen distribueras är den här funktionen på som standard.

Om du använder policyer för efterlevnad med villkorlig åtkomst (CA) och funktionen är aktiverad blockeras nu eventuella enheter utan minst en tilldelad policy för efterlevnad av CA. Slutanvändarna som är kopplade till dessa enheter, och som tidigare kunde komma åt e-post, förlorar sin åtkomst om du inte tilldelar minst en policy för efterlevnad till alla enheter.   

Observera att även om standardväxlingsstatus visas direkt i användargränssnittet med marsuppdateringarna av Intune-tjänsten tillämpas inte växlingsstatusen omedelbart. Ändringarna du gör med växlingsknappen påverkar inte enhetsefterlevnaden förrän vi har förhandstestat ditt konto och du har en fungerande växling. Vi informerar dig via meddelandecentret när vi är klara med att förhandsversionstesta ditt konto. Detta kan ta upp till ett par dagar efter marsuppdateringarna av Intune-tjänsten.

**Ytterligare information**:[https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Förbättrad upplåsningsidentifiering <!-- 846515 -->

Förbättrad upplåsningsidentifiering är en ny efterlevnadsinställning som förbättrar hur Intune utvärderar jailbreakade enheter. Inställningen gör att enheten checkar in till Intune oftare. Detta innebär att enhetens platstjänster används, vilket påverkar batterianvändningen.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Återställa lösenord för Android O-enheter <!-- 1238299 -->
Du kan återställa lösenorden för registrerade Android 8.0-enheter med arbetsprofiler. När du skickar en begäran om att återställa ett lösenord till en Android 8.0-enhet ställer den in ett nytt lösenord för upplåsning av enheten eller en hanterad profilutmaning för den aktuella användaren. Lösenordet eller kontrollfrågan skickas och träder i kraft omedelbart.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ange mål för efterlevnadsprinciper för enheter i enhetsgrupperna <!--1307012 -->

Du kan ange mål för efterlevnadsprinciper för användare i användargrupperna. Med den här uppdateringen kan du ange mål för efterlevnadsprinciper för enheter i användargrupper. Målenheter som ingår i enhetsgrupper får inte några efterlevnadsåtgärder.

#### <a name="new-management-name-column----1333586---"></a>Ny kolumn för hanteringsnamn <!-- 1333586 -->
 En ny kolumn med namnet **Hanteringsnamn** finns på enhetsbladet. Detta är ett automatiskt genererat, icke-redigerbart namn som tilldelas per enhet, baserat på följande formel:
- Standardnamn för alla enheter: <username><em><devicetype></em><enrollmenttimestamp>
- För masstillagda enheter: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

Det här är en valfri kolumn på enhetsbladet. Den är inte tillgänglig som standard och du har bara åtkomst till den via kolumnväljaren. Namnet på enheten påverkas inte av den här nya kolumnen.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>iOS-enheter uppmanas att ange en PIN-kod var 15:e minut <!--1550837 -->
När en policy för efterlevnad eller konfiguration används på en iOS-enhet, uppmanas användarna att ange en PIN-kod var 15:e minut. Användarna uppmanas kontinuerligt tills en PIN-kod anges.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Schemalägga automatiska uppdateringar <!--1805514 -->
Intune ger dig kontroll vid installation av automatiska uppdateringar med hjälp av [Inställningar för Windows 10-uppdateringsring](windows-update-for-business-configure.md). Med den här uppdateringen kan du schemalägga återkommande uppdateringar, inklusive vecka, dag och tid.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Använd ett fullständigt unikt namn som ämne för SCEP-certifikatet <!--2221763 -->
När du skapar en profil för SCEP-certifikat, anger du certifikatets ämnesnamn. Med den här uppdateringen kan du använda det fullständiga unika namnet som ämne. För **Ämnesnamn** väljer du **Anpassad** och sedan `CN={{OnPrem_Distinguished_Name}}`. Om du vill använda variabeln `{{OnPrem_Distinguished_Name}}` måste du synkronisera användarattributet `onpremisesdistingishedname` med hjälp av [Azure Active Directory (AD) Anslut](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) till din Azure AD.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Aktivera kontaktdelning med Bluetooth – Android for Work <!--1098983 -->
Som standard förhindrar Android att kontakter i arbetsprofilen synkroniseras med Bluetooth-enheter. Därför visas inte arbetsprofilkontakter i uppringarens ID för Bluetooth-enheter.

I och med uppdateringen finns en ny inställning i **Android for Work** > **Enhetsbegränsningar** > **Arbetsprofilinställningar**:
- Dela kontakter via Bluetooth

Intune-administratören kan konfigurera dessa inställningar för att aktivera delning. Detta är användbart när du parar ihop en enhet med en bilbaserad Bluetooth-enhet som visar uppringarens ID vid handsfree-användning. När den är aktiverad visas arbetsprofilens kontakter. När den är inaktiverad visas inte arbetsprofilens kontakter.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Konfigurera Gatekeeper till att styra macOS-appens nedladdningskälla <!-- 1690459 -->

Du kan konfigurera Gatekeeper till att skydda dina enheter från appar genom att styra var apparna kan laddas ned från. Du kan konfigurera följande nedladdningskällor: **Mac App Store**, **Mac App Store och identifierade utvecklare**, eller **Valfri plats**. Du kan även konfigurera om användarna ska kunna installera en app med CTRL-klick för att åsidosätta dessa Gatekeeper-kontroller.

Inställningarna finns i **Enhetskonfiguration** -> **Skapa profil** -> **macOS** -> **Slutpunktsskydd**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Konfigurera brandväggen för Mac-program <!-- 1690461 -->

Du kan konfigurera brandväggen för Mac-program. Du kan använda den för att styra anslutningar per program i stället för per port. Det gör det lättare att utnyttja brandväggsskyddet och förhindrar att oönskade appar tar kontroll över nätverksportar som är öppna för legitima appar.

Den här funktionen finns i **Enhetskonfiguration** -> **Skapa profil** -> **macOS** -> **Slutpunktsskydd**.

När du har aktiverat brandväggsinställningen kan du konfigurera brandväggen med hjälp av två olika metoder:

- Blockera alla inkommande anslutningar

   Du kan blockera alla inkommande anslutningar för de aktuella enheterna. Om du väljer att göra detta blockeras inkommande anslutningar för alla appar.

- Tillåta eller blockera specifika appar

   Du kan tillåta eller blockera specifika appar från att ta emot inkommande anslutningar. Du kan också aktivera hemligt läge för att förhindra svar på avsökningsbegäranden.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>Detaljerade felkoder och meddelanden <!-- 1376342 -->

I din enhetskonfiguration finns mer detaljerade felkoder och felmeddelanden. Den här förbättrade rapporteringen visar inställningarna, status för dessa inställningar och information om felsökning.

##### <a name="more-information"></a>Mer information

- Blockera alla inkommande anslutningar

   Detta hindrar alla delade tjänster (till exempel fildelning och delning av skärmen) från att ta emot inkommande anslutningar. Systemtjänster som fortfarande kan ta emot inkommande anslutningar är:
  - configd – Implementerar DHCP- och andra tjänster för nätverkskonfiguration
  - mDNSResponder – Implementerar Bonjour
  - racoon – Implementerar IPSec

    Om du vill använda delade tjänster kontrollerar du att **Inkommande anslutningar** är inställd på **Inte konfigurerad** (inte **Blockera**).

- Hemligt läge

   Aktivera detta om du vill förhindra att datorn svarar på avsökningsbegäranden. Datorn svarar fortfarande på inkommande begäranden för behöriga appar. Oväntade begäranden, till exempel ICMP (ping) ignoreras.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Inaktivera kontroller vid omstart av enheten <!--1805490 -->
Med Intune får du kontroller för att [hantera programuppdateringar]](windows-update-for-business-configure.md). Med den här uppdateringen är egenskapen <strong>Omstartskontroller</strong> tillgänglig och aktiverad som standard. Om du vill hoppa över de vanliga kontroller som utförs när du startar om en enhet (till exempel aktiva användare, batterinivå och så vidare) väljer du <strong>Hoppa över</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Nya Windows 10 Insider Preview-kanaler är tillgängliga för testgrupper för distribution <!-- 1746293 -->
Nu kan du välja följande Windows 10 Insider Preview-underhållskanaler när du skapar en Windows 10-testgrupp för distribution:
- Windows Insider-version &#8208; snabb
- Windows Insider-version &#8208; långsam
- Windows Insider-slutversion 

Mer information om dessa kanaler finns [Manage Insider Preview Builds](https://insider.windows.com/en-us/for-business-organization-admin/) (Hantera Insider Preview-versioner).   
Mer information om hur du skapar distributionskanaler i Intune finns i [Hantera programuppdateringar](windows-update-for-business-configure.md).

### <a name="intune-apps"></a>Intune-appar

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Registreringen av företagsportalen har förbättrats <!-- 1874230 eeready-->
Användare som registrerar en enhet med hjälp av företagsportalen i Windows 10 version 1703 och senare, kan slutföra det första steget i registreringen utan att lämna appen.

#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens och Surface Hub visas nu i enhetslistor <!--1725868 -->
Vi har lagt till stöd för att visa Intune-registrerade HoloLens- och Surface Hub-enheter i företagsportalappen för Android.

#### <a name="custom-book-categories-for-volume-purchase-progream-vpp-ebooks----1488911---"></a>Anpassade bokkategorier för volyminköpsprogram för e-böcker <!-- 1488911 -->
Du kan skapa anpassade e-bokkategorier och sedan tilldela e-böcker i volyminköpsprogram till dessa anpassade e-bokkategorier. Slutanvändarna kan sedan se de nyligen skapade e-bokkategorierna och böcker som tilldelats i kategorierna. Mer information finns i [Hantera volyminköpta appar och böcker med Microsoft Intune](vpp-apps.md).

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nya Windows Defender Application Guard-inställningar <!-- 1631890 -->

- **Aktivera grafikacceleration**: Administratörer kan aktivera en virtuell grafikprocessor för Windows Defender Application Guard. Med den här inställningen kan processorn avlasta grafikåtergivning till vGPU. Detta kan förbättra prestanda när du arbetar med grafikintensiva webbplatser eller tittar på videor inuti behållaren.

- **SaveFilestoHost**: Administratörer kan aktivera att filer kan skickas från Microsoft Edge som körs i behållaren till värdfilsystemet. Det gör att användare kan ladda ned filer från Microsoft Edge i behållaren till värdfilsystemet.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>MAM-skyddsprinciper riktas utifrån hanteringsstatus <!-- 1665993 -->
Du kan rikta MAM-principer baserat på hanteringsstatus för enheten:
- **Android-enheter** – Du kan ange ohanterade enheter, Intune-hanterade enheter och Intune-hanterade Android Enterprise-profiler (tidigare Android for Work) som mål.
- **iOS-enheter** – Du kan ange ohanterade enheter (endast MAM) eller Intune-hanterade enheter som mål.

    > [!NOTE]
    > - iOS-stöd för den här funktionen införs i april 2018.

Mer information finns i [Target app protection policies based on device management state](app-protection-policies.md) (Ange mål för appskyddsprinciper utifrån enhetens hanteringsstatus).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Förbättringar av språket i företagsportalappen för Windows <!-- 1683758 -->
Vi har förbättrat språket i företagsportalen för att Windows 10 ska vara mer användarvänlig och specifik för ditt företag. Du kan se några bildexempel på sidan om [nyheter i appens gränssnitt](whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Nya tillägg till vår dokumentation om användarsekretess <!-- 1440709 -->
Som en del i vårt arbete att ge användarna mer kontroll över sina data och sin sekretess har vi publicerat uppdateringar i vår dokumentation som förklarar hur du visar och tar bort data som lagras lokalt av företagsportalappar. Du hittar uppdateringarna på:

- **Android**: [Så här avregistrerar du en Android-enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, om användaren har avböjt användningsvillkoren** : [Ta bort enhetshantering om du har avböjt användningsvillkoren](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**: [Ta bort en iOS-enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**: [Ta bort en Windows-enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>Veckan som börjar med 19 mars 2018

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Exportera alla enheter till CSV-filer i Internet Explorer, Edge eller Chrome <!-- 2258071 -->
I **Enheter** > **Alla enheter** kan du **exportera** enheterna till en CSV-formaterad lista. Internet Explorer-användare med fler än 10 000 enheter kan exportera enheterna till flera filer. Varje fil kan ha upp till 10 000 enheter.

Edge- och Chrome-användare med fler än 30 000 enheter kan exportera enheterna till flera filer. Varje fil kan ha upp till 30 000 enheter.

I [Hantera enheter](device-management.md) finns mer information om vad du kan göra med de enheter som du hanterar.

## <a name="week-of-march-12-2018"></a>Vecka 12 i mars 2018

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-webbplatser kan kräva appen Intune Managed Browser och ha stöd för enkel inloggning för Managed Browser (allmänt tillgänglig förhandsversion) <!-- 710595 -->

Med Azure Active Directory (Azure AD) kan du nu begränsa åtkomsten till webbplatser på mobila enheter till appen Intune Managed Browser. I Managed Browser förblir webbplatsdata säkra och separata från slutanvändarens personliga data. Dessutom stöder Managed Browser funktioner för enkel inloggning för webbplatser som stöds av Azure AD. När du loggar in på Managed Browser eller använder Managed Browser på en enhet med en annan app som hanteras av Intune, tillåts Managed Browser att få åtkomst till företagswebbplatser som skyddas av Azure AD utan att användaren måste ange sina autentiseringsuppgifter. Den här funktionen gäller för webbplatser som Outlook Web Access (OWA) och SharePoint Online, samt andra företags webbplatser som resurser i intranätet som nås via Azure App Proxy.

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Visuella uppdateringar i företagsportalappen för Android <!--976944 -->

Vi har uppdaterat företagsportalappen för Android så att den följer Androids riktlinjer för [Materialdesign](https://material.io/). Du kan se bilder av de nya ikonerna i artikeln [Nyheter i appens gränssnitt](whats-new-app-ui.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Nya inställningar för Windows Defender Exploit Guard-princip <!-- 1631893 -->

Sex nya inställningar för <strong>minskning av attackytan</strong> och utökade funktioner för <strong>Reglerad mappåtkomst: Mappskydd</strong> är nu tillgängliga. Inställningarna finns här: Device configuration\Profiles\
Create profile\Endpoint protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Minska attackytan

|Inställningsnamn  |Inställningsalternativ  |Description  |
|---------|---------|---------|
|Avancerat skydd för utpressningstrojan|Aktiverad, granskad, inte konfigurerad|Använd aggressivt skydd mot utpressningstrojan.|
|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem|Aktiverad, granskad, inte konfigurerad|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem (lsass.exe).|
|Skapa process från PSExec- och WMI-kommandon|Blockera, Granska, Inte konfigurerat|Blockera skapande av processer från PSExec- och WMI-kommandon.|
|Obetrodda och osignerade processer som körs via USB|Blockera, Granska, Inte konfigurerat|Blockera obetrodda och osignerade processer som körs via USB.|
|Körbara filer som inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista|Blockera, Granska, Inte konfigurerat|Blockera körbara filer från att köras om de inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista.|

#### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

|              Inställningsnamn               |                                                              Inställningsalternativ                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Mappskydd (redan implementerat) | Inte konfigurerad, Aktivera, Endast granskning (redan implementerat)<br><br> <strong>Nytt</strong><br>Blockera diskändring, Granska diskändring |             |

Skydda filer och mappar från obehöriga ändringar av oönskade appar.<br><br>**Aktivera**: Förhindra att obetrodda appar ändrar eller tar bort filer i skyddade mappar och skriver till disksektorer.<br><br>
**Blockera endast diskändring**:<br>Blockera obetrodda appar från att skriva till disksektorer. Obetrodda appar kan fortfarande ändra eller ta bort filer i skyddade mappar.|

## <a name="week-of-february-19-2018"></a>Veckan för 19 februari 2018

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-stöd för flera Apple DEP/Apple School Manager-konton<!-- 747685 -->

Intune stöder nu registrering av enheter från upp till 100 olika [Apple-program för enhetsregistrering (DEP)](device-enrollment-program-enroll-ios.md) eller [Apple School Manager](apple-school-manager-set-up-ios.md)-konton. Varje token som har överförts kan hanteras separat för registreringsprofiler och- enheter. En annan profil kan tilldelas automatiskt per DEP/School Manager-token som har överförts. Om flera School Manager-token har överförs, kan bara en åt gången delas med Microsoft School-datasynkronisering.

Efter migreringen fungerar inte beta-Graph API:er och publicerade skript för att hantera Apple DEP eller ASM över Graph längre. Nya beta-Graph API:er är under utveckling och kommer att släppas efter migreringen.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Visa registreringsbegränsningar per användare <!-- 1634444 eeready wnready -->
På bladet **Felsök** kan du nu se de [registreringsbegränsningar](enrollment-restrictions-set.md) som gäller för varje användare genom att välja **Registreringsbegränsningar** i listan **Tilldelningar**.

### <a name="device-management"></a>Enhetshantering
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Stöd för hälsostatus och hotstatusrapporter i Windows Defender<!--854704 -->

Det är viktigt att förstå Windows Defenders hälsa och status för att hantera Windows-datorer.  Med denna uppdatering lägger Intune till nya rapporter och åtgärder till Windows Defender-agentens status och hälsa. Med hjälp av en statussammanfattningsrapport i [arbetsbelastningen för enhetsefterlevnad](compliance-policy-monitor.md) kan du se de enheter som behöver något av följande:
- signaturuppdatering
- Starta om
- manuella åtgärder
- fullständig genomsökning
- övriga agenttillstånd som kräver åtgärder

En detaljerad rapport för varje statuskategori visar de enskilda datorer som behöver åtgärdas eller vilka som rapporteras som **Rengör**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nya inställningar för enhetsbegränsningar <!--1308926 -->
[Två nya sekretessinställningar](device-restrictions-windows-10.md#privacy) är nu tillgängliga för enheter:
- **Publicera användaraktiviteter**: Ställ in den här på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen.
- **Endast lokala aktiviteter**: Ställ in det här alternativet på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen baserat på lokala aktiviteter.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nya inställningar för Microsoft Edge-webbläsaren <!--1469166 -->
[Två nya inställningar](device-restrictions-windows-10.md#edge-browser) är nu tillgängliga för enheter med Microsoft Edge-webbläsaren: **Sökväg till favoritfil** och **Ändringar i favoriter**.

### <a name="app-management"></a>Apphantering
#### <a name="protocol-exceptions-for-applications---1035509---"></a>Protokollundantag för program<!--1035509 -->

Du kan nu skapa undantag till principen för MAM-dataöverföring (Mobile Application Management) i Intune för att kunna öppna vissa ohanterade program. Sådana program måste vara betrodda av IT-avdelningen. Utöver de undantag som du skapar är dataöverföringen ändå begränsad till program som hanteras av Intune när din dataöverföringsprincip är inställd på **Endast hanterade appar**. Du kan skapa begränsningarna med protokoll (iOS) eller paket (Android).

Du kan exempelvis lägga till Webex-paketet som ett undantag till MAM-dataöverföringsprincipen. Det innebär att Webex-länkar i ett hanterat e-postmeddelande i Outlook kan öppnas direkt i Webex-programmet. Dataöverföringen är fortfarande begränsad i andra ohanterade program. Mer information finns i [Undantag för dataöverföringsprinciper i appar](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows Information Protection (PIA)-krypterad data i Windows-sökresultat <!-- 1469193 -->
En inställning i principen för Windows informationsskydd innebär att du nu kan kontrollera om krypterade data i Windows informationsskydd ingår i Windows-sökresultaten. Ange den här appens skyddsprincipalternativ genom att välja **Tillåt att Windows Search-indexeraren söker efter krypterade objekt**  i **Avancerade inställningar** för Windows informationsskyddsprincip. Appens skyddsprincip måste anges för *Windows 10*-plattformen och apprincipen **Registreringsstatus** måste anges som **Med registrering**. Mer information finns i [Tillåt att Windows Search-indexeraren söker efter krypterade objekt](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Konfigurera en MSI-mobilapp med automatisk uppdatering<!-- 1740840 -->
Du kan konfigurera att en känd MSI-mobilapp med automatisk uppdatering ignorerar versionskontrollen. Den här funktionen är användbar för att undvika konkurrenstillstånd. Den här typen av konkurrenstillstånd kan exempelvis uppstå när appen uppdateras automatiskt av apputvecklaren och även uppdateras av Intune. Båda två kan försöka framtvinga en version av appen på Windows-klienten, vilket kan skapa en konflikt. För dessa automatiskt uppdaterade MSI-appar kan du konfigurera inställningen **Ignore app version** (Ignorera appversion) på bladet **Appinformation**. När den här inställningen växlas till **Ja** kommer Microsoft Intune ignorera den appversion som är installerad på Windows-klienten.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Relaterade uppsättningar applicenser som stöds i Intune <!-- 1864117 -->
Intune i Azure-portalen stöder nu relaterade uppsättningar med applicenser som ett enskilt appobjekt i användargränssnittet. Dessutom konsolideras alla offlinelicensierade appar från Microsoft Store för företag till en enda appinmatning och eventuella distributionsuppgifter från de enskilda paketen migreras över till den enda inmatningen. Om du vill se relaterade uppsättningar applicenser i Azure-portalen väljer du **Applicenser** på bladet **Mobilappar**.

### <a name="device-configuration"></a>Enhetskonfiguration
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Filnamnstillägg i Windows informationsskydd för automatisk kryptering <!-- 1463582 -->
Med en inställning i principen för Windows informationsskydd kan du nu ange vilka filnamnstillägg som krypteras automatiskt vid kopiering från en SMB-resurs (Server Message Block) inom företagets gräns som definierats i Windows informationsskyddsprincip.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Konfigurera resursens kontoinställningar för Surface Hub

Du kan nu fjärrkonfigurera resurskontoinställningar för Surface Hub.

Resurskontot används av en Surface Hub för att autentisera med Skype/Exchange så att den kan ansluta till ett möte.
Du kan skapa ett unikt resurskonto så att Surface Hub visas i mötet som konferensrummet.
Resurskontot kan till exempel visas som **konferensrum B41/6233**.

> [!NOTE]
> - Om du låter fält vara tomma åsidosätter du tidigare konfigurerade attribut på enheten.
>
> - Egenskaper för resurskonto kan ändras dynamiskt på Surface Hub. Exempelvis om lösenordsrotation är på. Det är alltså möjligt att värdena i Azure-konsolen tar lite tid på sig att återspegla enhetens verklighet.
>
>   För att förstå vad som för närvarande konfigureras på Surface Hub kan resurskontoinformationen inkluderas i maskinvaruinventeringen (som redan har en intervall på 7 dagar) eller som skrivskyddade egenskaper. För att förbättra noggrannheten när en fjärråtgärd har vidtagits kan du genast hämta parametrarnas tillstånd när du har kört åtgärden för att uppdatera kontot/parametrarna på Surface Hub.


##### <a name="attack-surface-reduction"></a>Minska attackytan


|Inställningsnamn  |Inställningsalternativ  |Description  |
|---------|---------|---------|
|Körning av lösenordsskyddat körbart innehåll från e-post|Blockera, Granska, Inte konfigurerat|Förhindra körning av körbara filer som skyddas av lösenord och som hämtats via e-post.|
|Avancerat skydd för utpressningstrojan|Aktiverad, granskad, inte konfigurerad|Använd aggressivt skydd mot utpressningstrojan.|
|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem|Aktiverad, granskad, inte konfigurerad|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem (lsass.exe).|
|Skapa process från PSExec- och WMI-kommandon|Blockera, Granska, Inte konfigurerat|Blockera skapande av processer från PSExec- och WMI-kommandon.|
|Obetrodda och osignerade processer som körs via USB|Blockera, Granska, Inte konfigurerat|Blockera obetrodda och osignerade processer som körs via USB.|
|Körbara filer som inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista|Blockera, Granska, Inte konfigurerat|Blockera körbara filer från att köras om de inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista.|

##### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

|              Inställningsnamn               |                                                              Inställningsalternativ                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Mappskydd (redan implementerat) | Inte konfigurerad, Aktivera, Endast granskning (redan implementerat)<br><br> <strong>Nytt</strong><br>Blockera diskändring, Granska diskändring |             |

Skydda filer och mappar från obehöriga ändringar av oönskade appar.<br><br>**Aktivera**: Förhindra att obetrodda appar ändrar eller tar bort filer i skyddade mappar och skriver till disksektorer.<br><br>
**Blockera endast diskändring**:<br>Blockera obetrodda appar från att skriva till disksektorer. Obetrodda appar kan fortfarande ändra eller ta bort filer i skyddade mappar.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Tillägg till efterlevnadsprinciper för inställningar för systemsäkerhet för Windows 10 och senare <!--1704133-->

Tillägg till efterlevnadsinställningar för Windows 10 är nu tillgängliga, däribland krav på brandvägg och Windows Defender Antivirus.


### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll
### <a name="intune-apps"></a>Intune-appar
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Stöd för offline-appar från Microsoft Store för företag <!--1222672-->
Offline-appar som du har köpt från Microsoft Store för företag synkroniseras nu med Azure-portalen. Du kan distribuera apparna till enhetsgrupper eller användargrupper. Offline-appar installeras av Intune och inte av butiken.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Förhindra slutanvändare från att lägga till eller ta bort konton manuellt i arbetsprofilen <!-- 1728700 -->

När du distribuerar Gmail-appen till en Android for Work-profil kan du nu förhindra att användare lägger till eller tar bort konton i arbetsprofilen manuellt genom att använda inställningen **Lägg till och ta bort konton** i profilen för enhetsbegränsningar i Android for Work.

## <a name="week-of-february-5-2018"></a>Veckan för 5 februari 2018

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nya alternativ för användarautentisering för Apple-massregistrering <!-- 747625 eeready -->

> [!NOTE]
> Nya klienter ser det här direkt. Den här funktionen distribueras under april för befintliga klienter. Du kanske inte har åtkomst till de här nya funktionerna förrän den här distributionen är slutförd.

Intune ger dig nu möjlighet att autentisera enheter med hjälp av företagsportalappen för följande registreringsmetoder:

- Apples DEP (Device Enrollment Program)
- Apple School Manager
- Registrera Apple Configurator

När du använder alternativet Företagsportalen, kan Azure Active Directory-multifaktorautentisering tillämpas utan att blockera dessa registreringsmetoder.

När du använder alternativet Företagsportalen, hoppar Intune över användarautentisering i iOS-installationsassistenten för registrering av användartillhörighet. Detta innebär att enheten först registreras som en användarlös enhet och därför inte tar emot konfigurationer eller principer från användargrupper. Den tar bara emot konfigurationer och principer för enhetsgrupper. Intune kommer dock automatiskt att installera företagsportalappen på enheten. Den första användaren som startar och loggar in på företagsportalappen kommer att associeras med enheten i Intune. Användaren får då konfigurationer och principer för sina användargrupper. Användarassociationen kan inte ändras utan omregistrering.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Intune-stöd för flera Apple DEP/Apple School Manager-konton<!-- 747685 eeready -->

Intune stöder nu registrering av enheter från upp till 100 olika Apple-program för enhetsregistrering (DEP) eller Apple School Manager-konton. Varje token som har överförts kan hanteras separat för registreringsprofiler och- enheter. En annan profil kan tilldelas automatiskt per DEP/School Manager-token som har överförts. Om flera School Manager-token har överförs, kan bara en åt gången delas med Microsoft School-datasynkronisering.

Efter migreringen fungerar inte beta-Graph API:er och publicerade skript för att hantera Apple DEP eller ASM över Graph längre. Nya beta-Graph API:er är under utveckling och kommer att släppas efter migreringen.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Fjärrutskrift via ett säkert nätverk <!-- 1709994  -->
PrinterOn:s trådlösa mobila lösningar gör att användare via fjärranslutning kan skriva ut var och när som helst via ett säkert nätverk. PrinterOn kan integreras med Intune APP SDK för både iOS och Android. Du kommer att kunna ange mål för appskyddsprinciper för den här appen via bladet Intune **Appskyddsprinciper** i administrationskonsolen. Användarna kommer att kunna ladda ner appen PrinterOn for Microsoft via Play Store eller iTunes för att använda i sina Intune-ekosystem.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Stöd för macOS-företagsportal för registreringar som använder Enhetsregistreringshanteraren <!-- 1352411 -->

Användarna kan nu använda enhetsregistreringshanteraren när de registrerar sig i macOS-företagsportalen.

## <a name="week-of-january-29-2018"></a>Veckan som börjar med 29 januari 2018

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Aviseringar om att token har upphört att gälla och om att token snart upphör att gälla <!-- 1639263 -->
På översiktssidan visas nu aviseringar om att token har upphört att gälla och om att token snart upphör att gälla. När du klickar på en avisering för en enskild token fortsätter du till denna tokens informationssida.  Om du klickar på avisering för flera token kommer du till en lista över alla token med deras status. Administratörer bör förnya sina tokens innan förfallodatumet.

### <a name="device-management"></a>Enhetshantering

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Stöd för fjärråtkomst till kommandot ”Radera” för macOS-enheter <!-- 1438084 -->

Administratörer kan utfärda ett Radera-kommando via fjärranslutning för macOS-enheter.

> [!IMPORTANT]
> Raderingskommandot kan inte ångras och bör användas med försiktighet.

Raderingskommandot tar bort alla data, inklusive operativsystemet från en enhet. Det tar också bort enheten från Intune-hantering. Ingen varning utfärdas till användaren och raderingen sker omedelbart efter kommandot.

Du måste konfigurera en 6-siffrig PIN-kod för återställning. Den här PIN-kod kan användas för att låsa upp enheten som raderats, då ominstallation av operativsystemet börjar. När raderingen har startats visas PIN-koden i ett statusfält på enhetens översiktsblad i Intune. PIN-koden kommer att finnas kvar så länge raderingen pågår. När raderingen är klar försvinner enheten helt från Intune-hanteringen. Tänk på att notera PIN-koden så att den som återställer enheten kan använda den.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Återkalla licenser för en token för iOS-volyminköpsprogram <!-- 820870 -->
Du kan återkalla licensen för alla iOS-appar för volyminköpsprogram (VPP) för en given VPP-Token.

### <a name="app-management"></a>Apphantering

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Återkallande av iOS-appar från volyminköpsprogram  <!-- 820863 -->
Du kan återkalla associerade enhetsbaserade applicenser för enheten för en given enhet som har en eller flera iOS-appar för volyminköpsprogram (VPP). Om du återkallar en applicens så avinstalleras inte den relaterade VPP-appen från enheten. Om du vill avinstallera en VPP-app, måste du ändra tilldelningsåtgärden till **avinstallera**. Mer information finns i [så här hanterar du iOS-appar som köpts genom ett volyminköpsprogram med Microsoft Intune](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Tilldela Office 365-mobilappar till iOS och Android-enheter med den inbyggda apptypen <!-- 1332318 -->
Den **inbyggda** apptypen gör det enklare att skapa och tilldela Office 365-appar till iOS- och Android-enheter som du hanterar. De här apparna inkluderar 365-appar som Word, Excel, PowerPoint och OneDrive. Du kan tilldela specifika appar till apptypen och redigera konfigurationen för appinformationen.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inklusive och exklusive apptilldelning baserat på grupperna <!-- 1406920 -->

Under apptilldelning och när du har valt en tilldelningstyp kan du välja de grupper som ska inkluderas, samt de grupper som ska undantas.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Du kan tilldela en programkonfigurationsprincip till grupper genom att inkludera och exkludera tilldelningar <!-- 1480316 -->

Du kan tilldela en programkonfigurationsprincip till en grupp användare och enheter genom att använda en kombination av tilldelningar som inkluderar och exkluderar. Tilldelningar kan väljas som ett anpassat urval av grupper eller som en virtuell grupp. En virtuell grupp kan inkludera **Alla användare**, **Alla enheter** eller **Alla användare + Alla enheter**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Stöd för uppgraderingsprincip i Windows 10-utgåvan <!-- 903672(archived), 1119689 -->  
Du kan skapa en uppgraderingsprincip för Windows 10-utgåvan som uppgraderar Windows 10-enheter till Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education och Windows 10 Professional Education N. Mer information om Windows 10-uppgraderingar finns i [Så här konfigurerar du Windows 10-uppgraderingar](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Principer för villkorlig åtkomst för Intune är endast tillgängliga från Azure Portal <!-- 1737088 1634311 -->

Från och med den här versionen måste du konfigurera och hantera dina principer för villkorlig åtkomst på [Azure Portal](https://portal.azure.com) från **Azure Active Directory** > **Villkorlig åtkomst**. Du kan även komma åt det här bladet från Intune på Azure Portal på **Intune** > **Villkorlig åtkomst**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Uppdateringar till efterlevnads-e-post <!--1637547 -->

När ett e-postmeddelande skickas för att rapportera om en inkompatibel enhet inkluderas även information om den inkompatibla enheten.


## <a name="week-of-january-22-2018"></a>Vecka 22 januari 2018

### <a name="intune-apps"></a>Intune-appar

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>En ny funktion för åtgärden ”Lös” för Android-enheter <!--1583480-->

Företagsportalappen för Android utökar ”Lös”-åtgärden för **Uppdatera enhetsinställningar** för att lösa [device encryption issues](/intune-user-help/encrypt-your-device-android) (problem med enhetskryptering).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Fjärrlås är tillgängligt i företagsportalappen för Windows 10 <!--676506-->
Slutanvändare kan nu fjärrlåsa sina enheter från företagsportalappen för Windows 10. Detta visas inte för den lokala enheten som används.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Enklare lösning av efterlevnadsproblem för företagsportalappen för Windows 10 <!--676546-->
Slutanvändare med Windows-enheter kan trycka på orsaken för bristande efterlevnad i företagsportalappen. Om möjligt kommer de då direkt till rätt plats i inställningsappen för att kunna åtgärda problemet.

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
Det finns nu nya processer och verktyg för att flytta användare och deras enheter från hybrid MDM till Intune på Azure Portal. Nu kan du göra följande:
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

Med versionen Android Oreo introducerar Google en uppsättning säkerhetsfunktioner med namnet Google Play Protect, där användare och organisationer kan köra skyddade appar och Android-bilder. Intune stöder nu Google Play Protect-funktionerna, inklusive SafetyNets fjärrattestering. Administratörer kan ange efterlevnadsprincipkrav som kräver att Google Play Protect är konfigurerat och felfritt.
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
SCOM-hanteringspaketet (System Center Operations Manager) för Exchange-anslutningsappen finns nu tillgängligt att hjälpa dig parsa Exchange-anslutningsloggarna. Den här funktionen ger dig flera olika sätt att övervaka tjänsten när du behöver felsöka problem.

## <a name="week-of-november-6-2017"></a>Veckan som börjar med 6 november 2017

### <a name="device-enrollment"></a>Enhetsregistrering
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Samhantering för Windows 10-enheter  <!-- 1243445 -->
Samhantering är en lösning som erbjuder en brygga från traditionell till modern hantering, och det ger dig en sökväg för att göra övergången stegvis. I grund och botten är samhantering en lösning där Windows 10-enheter samtidigt hanteras av Configuration Manager och Microsoft Intune, som är anslutna till Active Directory (AD) och Azure Active Directory (Azure AD).  Den här konfigurationen ger dig en sökväg för att modernisera med tiden i den takt som passar din organisation om du inte kan flytta allt på samma gång.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Begränsa Windows-registrering efter OS-version <!-- 245498 -->
Som Intune-administratör kan du nu ange en lägsta och högsta version av Windows 10 för enhetsregistrering. Du kan ange begränsningarna på bladet **Plattformskonfigurationer**.

Intune fortsätter att stödja registrering av datorer och telefoner med Windows 8.1. Endast Windows 10-versioner kan dock konfigureras med lägsta och högsta gränser. Låt den lägsta gränsen vara tom om du vill tillåta registrering av 8.1-enheter.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Aviseringar för otilldelade Windows AutoPilot-enheter <!-- 1631236 -->
En ny avisering är tillgänglig för otilldelade Windows AutoPilot-enheter på sidan **Microsoft Intune** > **Enhetsregistrering** > **Översikt**. Den här aviseringen visar hur många enheter från AutoPilot-programmet som inte har tilldelade AutoPilot-distributionsprofiler. Använd informationen i aviseringen för att skapa profiler och tilldela dem till de otilldelade enheterna. När du klickar på aviseringen visas en fullständig lista över Windows AutoPilot-enheter och detaljerad information om dem. Läs mer i informationen om att [registrera Windows-enheter med Windows AutoPilot-distributionsprogrammet](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="device-management"></a>Enhetshantering

#### <a name="refresh-button-for-devices-list-------1333581---"></a>Uppdateringsknapp för enhetslista <!-- 1333581 -->
Eftersom enhetslistan inte uppdateras automatiskt kan du använda den nya uppdateringsknappen för att uppdatera vilka enheter som visas i listan.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Stöd för Symantec Cloud Certification Authority (CA)  <!-- 1333638 -->    
Intune stöder nu Symantec Cloud CA, som tillåter att Intune Certificate Connector utfärdar PKCS-certifikat från Symantec Cloud CA till hanterade Intune-enheter. Om du redan använder Intune Certificate Connector med Microsoft Certification Authority (CA) kan du använda den befintliga Intune Certificate Connector-konfigurationen för att lägga till Symantec CA-stöd.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nya objekt som har lagts till i enhetsinventering <!--1404455 -->
Följande nya objekt är nu tillgängliga i den [inventering som görs av registrerade enheter](device-inventory.md):

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
IT-administratörer kan nu ange ett krav via Azure-administrationsportalen på att framtvinga ett lösenord i stället för en numerisk PIN-kod via mobilapphantering (MAM) när programmet startas. Om det har konfigurerats måste användaren vid uppmaning ställa in och använda ett lösenord innan användaren får åtkomst till MAM-integrerade program. Ett lösenord definieras som en numerisk PIN-kod med minst ett specialtecken eller en gemen/versal. Den här versionen av Intune kommer att aktivera den här funktionen **enbart på iOS**. Intune stöder lösenord på liknande sätt som numeriska PIN-koder. En minsta längd krävs och upprepning av tecken och sekvenser tillåts. Den här funktionen kräver att program deltar (dvs. WXP, Outlook, Managed Browser, Yammer) för att integrera Intune APP SDK:n med koden för funktionen på plats för att lösenordsinställningarna ska framtvingas i berörda program.

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
En profil för enhetskonfiguration som heter **Nätverksgräns** finns bland dina övriga enhetskonfigurationsprofiler. Använd den här profilen till att definiera onlineresurser som du anser är företagets och betrodda. Du måste definiera en nätverksgräns för en enhet *innan* funktioner som Windows Defender Application Guard och Windows informationsskydd kan användas på enheten. Det är viktigt att endast definiera en nätverksgräns för varje enhet.

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

Arbetsflödet för enhetskonfiguration har förbättrats i företagsportalappen för iOS. Språket är mer användarvänligt och vi har kombinerat skärmar där det är möjligt. Språket är mer specifikt för ditt företag genom att företagsnamnet används genomgående i installationstexten. Du kan se det uppdaterade arbetsflödet på  [sidan nyheter i appgränssnittet](whats-new-app-ui.md).

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>Användarentiteten innehåller de senaste användardata i datamodellen för informationslagret <!-- 1544273 -->
Den första versionen av datamodellen för Intune-informationslagret innehöll endast de senaste historiska Intune-data. Rapportskaparna kunde inte identifiera det aktuella tillståndet för en användare. I den här uppdateringen fylls **användarentiteten** i med senaste användardata.


## <a name="notices"></a>Meddelanden

### <a name="plan-for-change-new-windows-10-setting-for-kiosk-configuration-in-intune----1560072---"></a>Planera för förändring: Ny Windows 10-inställning för helskärmskonfiguration i Intune <!-- 1560072 -->
Vi ändrar hur och var du konfigurerar datorer med Windows 10 1709 och senare (RS3 och senare) i Intune Azure Portal.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig? 
Vi har information som visar att du använder Windows-10 > Enhetsbegränsningar > inställningen Helskärm (förhandsgranskning). Inställningen kommer att byta namn i maj till Windows 10 > Enhetsbegränsningar > Helskärm (inaktuell) för att ange att den inte längre rekommenderas. Men den kommer att fungera fram till juliuppdateringen av Intune. Sedan blir den inaktuell på serverdelen och slutar fungera. Som ett alternativ släpper vi en ny enhetskonfigurationsprofil i maj: Windows 10 > Helskärm, som innehåller inställningar för att konfigurera helskärmsläge i Windows 10 RS4 och senare.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?  
När underhållsuppdateringen för maj släpps i slutet av maj tillhandahåller vi också instruktioner för hur du kan testa och kontrollera att du kan migrera din helskärmskonfiguration från Windows 10 RS3 till Windows 10 RS4. Använd dessa instruktioner för att konfigurera dina enheter med den nya enhetskonfigurationsprofilen för helskärmsläget.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Den här förändringen påverkar både kunder som har fristående Intune och hybridkunder (Intune med Configuration Manager). Den här integreringen hjälper till att förenkla administrationen av molnhanteringen. Nu behöver du bara gå till ett blad i Azure, Intune-bladet, för att hantera grupper, principer, appar och eventuell hantering av mobilenheter.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Lägg till Intune som favorit i stället för bladet för tjänsten Intune-appskydd, och se till att du känner till arbetsflödet för appskyddsprinciper på bladet Mobilapp i Intune. Vi omdirigerar under en kort tidsperiod och tar sedan bort appskyddsbladet. Kom ihåg att alla appskyddsprinciper redan finns i Intune och du kan ändra dina villkorliga åtkomstprinciper genom att följa dokumentationen här: [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca).

**Ytterligare information**:[https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="plan-for-change-windows-company-portal-send-feedback-option-may-no-longer-work"></a>Planera för förändring: Alternativet för att skicka feedback via företagsportalappen i Windows kanske inte fungerar längre  
I företagsportalappen i Windows finns ett alternativ för att **skicka feedback** som låter användarna dela med sig av sina synpunkter om appen till Microsoft. Från och med 30 april 2018 stöds det här alternativet endast i företagsportalappen i Windows 10 1607 (Anniversary Update) och senare.  

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?  
Du kan bortse från det här meddelandet om du inte har Windows-företagsportalappen installerad för slutanvändare. Om någon av dina slutanvändare har företagsportalappen ska du observera att knappen för att **skicka feedback** inte längre kommer att fungera i appen från och med 30 april i följande:  
- Företagsportalappen i Windows 10 version 1507 och 1511  
- Företagsportalappen i Windows Phone 8.1  

För berörda enheter fungerar inte alternativet att **skicka feedback** (inte heller om du gör ett nytt försök). Om du vill skicka feedback till Microsoft för dessa plattformar kan du använda de alternativa feedbackkanaler som anges nedan.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?  
Informera användarna om den här ändringen och uppdatera eventuella användarriktlinjer om det behövs. Informera de som använder företagsportalappen i Windows Phone 8.1, Windows 10 1507 och Windows 10 1511 om att det finns två alternativa feedbackkanaler. De kan:  
- Använda Feedbackhubben i Windows 10
- Skicka ett e-postmeddelande till WinCPfeedback@microsoft.com  

Be slutanvändare som använder Windows 10 RS1 att uppdatera till den senaste versionen av företagsportalappen i Store.

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Planera för förändring: Ändra i stödet för Microsoft Intune App SDK för Cordova-pluginprogrammet
Microsoft avslutar stödet för [Microsoft Intune App SDK Cordova-pluginprogrammet](app-sdk-cordova.md) 1 maj 2018. Vi rekommenderar att du använder Intunes programhanteringsverktyg i stället, för att förbereda dina Cordova-baserade appar för hantering och tillgänglighet i Intune. När den här ändringen träder i kraft kommer Microsoft Intune APP SDK för Cordova-pluginprogrammet inte längre att hanteras eller bli uppdaterat. Utvecklare av program kommer inte att kunna använda det här pluginprogrammet. Intune planerar att fortsätta att tillhandahålla stöd för appar som utvecklats med Cordova. Alla appar som utvecklats med Microsoft Intune APP SDK för Cordova-pluginprogrammet får dock nedsatt funktionalitet i Intune. Efter att du omslutit en app med Intunes programhanteringsverktyg kan den distribueras till slutanvändare som normalt. För Cordova-baserade Android-appar som publiceras till Google Play-butiken:
- Slutanvändarna uppmanas att ange sina autentiseringsuppgifter för att ta emot Intune-principen vid första start.
- Appar som ska publiceras på appbutiken för Intune-användare, till exempel ”Contoso-appen för Intune”.

Mer information om programhanteringsverktyget finns i [Programhanteringsverktyget för iOS](app-wrapper-prepare-ios.md) och [Programhanteringsverktyget för Android](app-wrapper-prepare-android.md). Om du har problem eller frågor kan du kontakta [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com).

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Planera för förändring: Använd Intune på Azure för MDM-hanteringen <!-- 1227338 -->
För över ett år sedan tillkännagav vi en [allmänt tillgänglig förhandsversion av Intune på Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) och för sex månader sedan följde vi upp med [allmän tillgänglighet för den nya administratörsupplevelsen](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) för Intune. Från och med 31 augusti 2018 inaktiverar vi MDM (hantering av mobilenheter) i den klassiska Silverlight-konsolen för de kunder som använder fristående Intune. Du kan istället använda [Intune på Azure](https://aka.ms/Intune_on_Azure) för MDM-behoven. Om du fortfarande använder den klassiska konsolen för MDM rekommenderar vi att du ägnar en stund åt att bekanta dig med Intune på Azure. Vi förväntar oss inte att slutanvändarna ska påverkas av denna förändring. Klassisk datorhantering kommer att finnas kvar i Silverlight. Du kan läsa mer om den här förändringen och hur den påverkar dig [här](https://aka.ms/Intune_on_Azure_mdm).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->
För Intune-konton som skapades efter januari 2017 har Intune aktiverat direktåtkomst till registreringsscenarier i Apple med arbetsflödet Registrera enheter i Azure-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i den klassiska Intune-portalen. Intune-konton som skapades före januari 2017 måste migreras en gång innan dessa funktioner är tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto inte har åtkomst till Azure-portalen.

## <a name="whats-coming"></a>Kommande nyheter

### <a name="local-device-security-option-settings----1251887---"></a>Inställningar för säkerhetsalternativ för lokal enhet <!-- 1251887 -->
Du kan aktivera säkerhetsinställningarna på Windows 10-enheter med de nya inställningarna för säkerhetsalternativ för den lokala enheten. Inställningarna finns i kategorin Endpoint Protection när du skapar en princip för Windows 10-enhetskonfiguration.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>Ny uppdatering av användarupplevelse för företagsportalens webbsida <!--2000968-->

Vi presenterar en ny webbplats för företagsportalen i april, med uppdateringar av användargränssnittet, effektiva arbetsflöden och åtkomstförbättringar. Detta inkluderar kundefterfrågade förbättringar som appdelning och förbättrad övergripande prestanda för att få en mer användarvänlig upplevelse.
Vi har lagt till några nya funktioner, baserat på feedback från kunder som du, som förbättrar befintliga funktioner och användbarhet:

-   Förbättringar i användargränssnittet på hela webbplatsen
-   Möjlighet att dela direktlänkar till appar
- Förbättrad prestanda för stora app-kataloger

Du behöver inte göra några förberedelser inför den här ändringen. Vi meddelar dig när den uppdaterade webbplatsen för företagsportalen blir tillgänglig för dig. Du kan behöva uppdatera slutanvändardokument med uppdaterade skärmbilder. Observera att du också kan behöva uppdatera dokumentationen för företagsportalappen på iOS då webbplatsen startar avsnittet **Appar** i iOS-app. Du kan se en exempelbild för detta på sidan [vad är nytt i appens användargränssnitt](whats-new-app-ui.md).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->
Apple har tillkännagivit att de kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen. Vi lägger till information i [Intunes supportblogg](https://aka.ms/compportalats).



## <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/cloud-platform/roadmap)
* [Nyheter i företagsportalens gränssnitt](whats-new-app-ui.md)
* [Nyheter från föregående månad](whats-new-archive.md)
