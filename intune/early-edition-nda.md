---
title: Tidig utgåva
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e24414d28b8adeae7dfbedb606ca1a7d21497a3f
ms.sourcegitcommit: 698af815f6de2c4f003f6da428bbfb0680daafa0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43093205"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>Den tidiga utgåvan för Microsoft Intune – augusti 2018

> [!Note]
> Meddelande om sekretessavtal: Följande ändringar håller på att utvecklas för Intune. Den här informationen har mycket begränsad spridning, i enlighet med sekretessavtalet. Sprid inte den här informationen vidare på sociala medier eller offentliga webbplatser, till exempel Twitter, UserVoice, Reddit och så vidare. 

Den **tidiga utgåvan** innehåller en lista med funktioner, som delas i enlighet med sekretessavtalet, som ingår i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte den här informationen på Twitter, UserVoice eller på något annat sätt med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1808 start -->

### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello riktar in sig på användare och enheter <!-- 1106609 -->
När du skapar en [Windows Hello för företag](windows-hello.md)-princip gäller den för alla användare i organisationen (i hela klientorganisationen). Med den här uppdateringen kan principen även tillämpas på specifika användare eller specifika enheter med hjälp av en princip för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Identity Protection (Identitetsskydd)** > **Windows Hello för företag**).

I Intune i Azure-portalen kommer konfiguration och inställningar för Windows Hello att finnas i både **Enhetsregistrering** och **Enhetskonfiguration**. **Enhetsregistrering** riktar sig till hela organisationen (i hela klientorganisationen) och har stöd för Windows AutoPilot (OOBE). **Enhetskonfiguration** riktar sig mot enheter och användare som använder en princip som tillämpas under incheckning.

Gäller för:  
- Windows 10 och senare
- Windows 10 Holographic for Business

### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Kontrollera S-läge på Windows 10-enheter och senare enheter – förhandsversion <!-- 1958649 -->
Du kommer att kunna skapa en profil för enhetskonfiguration som växlar en Windows 10-enhet ut ur S-läge, eller förhindra att användare växlar enheten ut ur S-läge. Den här funktionen kommer att finnas i Intune > **Enhetskonfiguration** > **Profiler** >  **Windows 10 och senare** > **Edition upgrade and mode switch** (Versionsuppgradering och lägesväxling).
[Introduktion till Windows 10 i S-läge](https://www.microsoft.com/windows/s-mode) innehåller mer information om S-läge.
Gäller för: Windows 10 och senare (1809 och senare)

### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Uppdateringar med stöd för modernt VPN för iOS <!-- 2459928, 1819876, and 2650856 -->
En kommande uppdatering har stöd för följande VPN-klienter för iOS: 
- F5 Access (version 3.0.1 och senare)
- Citrix SSO
- Palo Alto Networks GlobalProtect (version 5.0 och senare) även i en kommande uppdatering:
- Befintliga **F5 Access**-anslutningstyper kommer att byta namn till **F5 Access Legacy** (enligt uppdateringar av varumärkesanpassning för F5)
- Befintliga **Palo Alto Networks GlobalProtect**-anslutningstyper kommer att byta namn till **Legacy Palo Alto Networks GlobalProtect** (enligt uppdateringar av varumärkesanpassning för Palo Alto). 

Befintliga profiler med de här anslutningstyperna fortsätter att fungera med den äldre VPN-klienten. Om du använder Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN eller Legacy Palo Alto Networks GlobalProtect med iOS bör du gå över till de nya apparna. Gör det så snart som möjligt för att säkerställa att VPN-åtkomst är tillgänglig för iOS-enheter när de uppdaterar till iOS 12.

### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Lås företagsportalen i enkelt appläge tills användaren loggar in <!--1067692 --> 
Du har möjligheten att köra företagsportalen i enkelt appläge om du autentiserar en användare via företagsportalen i stället för installationsassistenten vid DEP-registrering. Det här alternativet låser enheten omedelbart efter att installationsassistenten är klar så att en användare måste logga in för att komma åt enheten. Den här processen ser till att enheten slutför registrering inte frånkopplas i ett tillstånd utan någon kopplad användare.

### <a name="scope-tags-for-policies---1081974-eeready--"></a>Omfångstaggar för principer <!--1081974 eeready-->

Du kommer att kunna skapa omfångstaggar som begränsar åtkomsten till Intune-resurser. Lägg till en omfångstagg till en rolltilldelning och lägg sedan till omfångstaggen i en konfigurationsprofil. Rollen får endast åtkomst till resurser med konfigurationsprofiler som har matchande omfångstaggar (eller inga omfångstaggar).
Om du vill skapa en omfångstagg väljer du **Intune-roller** > **Scope (Tags) (Omfång (taggar))** > **Skapa**.
För att lägga till en omfångstagg till en rolltilldelning väljer du **Intune-roller** > **Alla roller** > **Princip- och profilhanterare** > **Tilldelningar** > **Scope (Tags)** (Omfång (taggar)).
För att lägga till en omfångstagg till en konfigurationsprofil väljer du **Enhetskonfiguration** > **Profiler** > välj en profil > **Egenskaper** > **Scope (Tags)** (Omfång (taggar)).

### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Tilldela en användare och ett eget namn till en Autopilot-enhet <!--1346521 -->
I en kommande offentlig förhandsversion kommer administratörer att kunna tilldela en användare till en enskild Autopilot-enhet.  Administratörer kommer även att kunna ge egna namn som möter användaren vid konfiguration av enheten med Autopilot.

Gäller för: Windows Insider 1809 eller senare versioner (medan den är i förhandsversion).

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-token som används av en annan MDM <!-- 1488946 -->
Intune identifierar och visar information om en token för volyminköpt Apple-program (VPP) används av både Intune och en annan MDM.

### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Stöd för pakettunnel för per app-VPN-profiler i iOS för anpassade anslutningstyper och Pulse Secure-anslutningstyper <!-- 1520957 -->
När du använder per app-VPN-profiler i iOS kommer du att kunna använda händelsedirigering nedåt på applager (app-proxy) eller på paketnivå (paket-tunnel). Dessa alternativ blir tillgängliga med följande anslutningstyper:
- Anpassat VPN
- Pulse Secure om du inte är säker på vilket värde du ska använda läser du VPN-leverantörens dokumentation.
Gäller för: iOS

### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler är en tillgänglig anslutning för VPN-profiler i iOS <!-- 1769858 eeready -->
När du skapar en VPN-profil för enhetskonfiguration i iOS (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS**-plattform > **VPN**-profiltyp) finns det flera anslutningstyper, inklusive Cisco, Citrix och mer. En kommande uppdatering lägger till Zscaler som anslutningstyp. 
[VPN-inställningar för enheter som kör iOS](vpn-settings-ios.md) visar en lista över tillgängliga anslutningstyper.

### <a name="block-windows-personal-device-enrollments----1849498---"></a>Blockera personliga enhetsregistreringar i Windows <!-- 1849498 -->
Du kommer att kunna blockera personliga Windows-enheter från att registrera med [hantering av mobilenheter](windows-enroll.md) i Intune. Enheter som registreras med [Intune PC-agenten](manage-windows-pcs-with-microsoft-intune.md) kan inte blockeras med den här funktionen.
Om du vill se den här funktionen väljer du **Enhetsregistrering** > **Enhetsbegränsningar**.
Aktivering av den här begränsningen har ingen effekt på enheter som redan har registrerats.
När en begränsning aktiveras kontrollerar Intune för att se till att varje ny Windows-registreringsbegäran har auktoriserats som en företagsregistrering. Följande metoder räknas som auktoriserade som företagsregistrering:
- Den registrerande användaren använder ett [konto för enhetsregistreringshanteraren]( device-enrollment-manager-enroll.md).
- Enheten registreras via [Windows Autopilot](enrollment-autopilot.md).
- Enhetens IMEI-nummer anges i **Enhetsregistrering** > **[ID:n för företagsenheter]( corporate-identifiers-add.md)**).
- Enheten registreras via ett [bulketableringspaket](windows-bulk-enroll.md).
- Enheten registreras via [automatisk registrering från SCCM för samhantering](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management).

Obehöriga registreringar kommer att blockeras. Följande registreringar markeras som företagsregistreringar av Intune, men eftersom de inte innehåller per enhet-kontroll för Intune-administratören kommer de att blockeras:
- [Automatisk MDM-registrering](windows-enroll.md#enable-windows-10-automatic-enrollment) med [Azure Active Directory-anslutning under Windows-installation](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).
- [Automatisk MDM-registrering](windows-enroll.md#enable-windows-10-automatic-enrollment) med [Azure Active Directory-anslutning från Windows-installation](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).

Följande personliga registreringsmetoder blockeras också:
- [Automatisk MDM-registrering](windows-enroll.md#enable-windows-10-automatic-enrollment) med [Add Work Account from Windows Settings](https://docs.microsoft.com/azure/active-directory/user-help/device-management-azuread-registered-devices-windows10-setup) (Lägg till arbetskonto från Windows-inställningarna).
- Alternativet [MDM enrollment only]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) (Endast MDM-registrering) från Windows-inställningarna.

### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Ange mönster för datornamn i en Autopilot-profil <!--1849855-->
Du kommer att kunna ange en mall för datornamn för att generera och ange [datornamnet](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) under Autopilot-registreringen. Du måste ange detta i den Autopilot-profil som finns i **Enhetsregistrering** > **Windows-registrering** > **Windows Autopilot-distributionstjänsten** > **Profiler**. Endast alfanumeriska tecken och bindestreck kan användas.
Gäller för: Windows Insider 1809 eller senare versioner (medan den är i förhandsversion).

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>iOS-versionsnumret och byggenumret visas <!-- 1892471 -->
I **Enhetsefterlevnad** > **Enhetsefterlevnad** visas iOS-operativsystemets version. I kommande uppdateringar visas även byggenumret.
När säkerhetsuppdateringar lanseras låter Apple vanligtvis versionsnumret vara som det är men uppdaterar byggenumret. Genom att visa byggenumret kan du enkelt kontrollera om en säkerhetsriskuppdatering har installerats.

### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>För Windows Autopilot-profiler döljer du alternativen för att ändra konto på företagets inloggningssida och sidan för domänfel <!--1901669 -->
En offentlig förhandsversion kommer att innehålla nya Windows Autopilot-profilalternativ som administratörer kan använda till att dölja ändra alternativ för att ändra konto på företagets inloggningssida och sidorna för domänfel. För att dölja de här alternativen krävs att företagsanpassning konfigureras i Azure Active Directory. Gäller för: Windows Insider 1809 eller senare versioner (medan den är i förhandsversion).

### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Fördröjning när iOS-programuppdateringar visas på enheten <!-- 1949583 -->
I Intune > **Programuppdateringar** > **Uppdateringsprinciper för iOS** kan du konfigurera dagar och tider då du inte vill att enheter installerar uppdateringar. I en kommande uppdatering kommer du kunna fördröja tidpunkten då en programuppdatering visas på enheten från 1–90 dagar. 
[Konfigurera uppdateringsprinciper för iOS i Microsoft Intune](software-updates-ios.md) visar en lista över aktuella inställningar.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Tillbakadragna enheter i instrumentpanelen för enhetsefterlevnad <!-- 1981119 -->
I en kommande uppdatering tas tillbakadragna enheter bort från instrumentpanelen för enhetsefterlevnad. Detta ändrar dina efterlevnadsnummer.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Ny uppdatering av användarupplevelse för företagsportalens webbsida <!--2000968 -->
Nya funktioner kommer att läggas till på företagsportalen baserat på våra kunders synpunkter. Du kommer att se tydliga förbättringar av befintliga funktioner och användbarheten jämfört med dina Android-, iOS- och Windows-enheter. Delar av webbplatsen, som enhetsinformation, feedback och support samt enhetsöversikten, kommer att få en ny och modern design. Andra nyheter:
- Effektiva arbetsflöden mellan olika plattformar
- Bättre flöden för identifiering och registrering av enheter
- Fler användbara felmeddelanden
- Mer användarvänligt språk, mindre teknisk jargong
- Möjlighet att dela direktlänkar till appar
- Förbättrad prestanda för stora app-kataloger
- Bättre tillgänglighet för alla användare

### <a name="office-365-proplus-version----2213968-eeready---"></a>Office 365 ProPlus version <!-- 2213968 eeready -->
När du tilldelar Office 365 ProPlus-appar till Windows 10-enheter med Intune kommer du att kunna välja version av Office. I Azure-portalen väljer du **Microsoft Intune** > **Appar** > **Lägg till app**. Välj sedan **Office 365 ProPlus-paket (Windows 10)** från listrutan **Typ**. Välj **Inställningar för appsvit** för att visa det associerade bladet. Ange **Uppdateringskanalen** till ett värde såsom **Varje månad**. Du kan även ta bort andra versioner av Office (msi) från slutanvändarenheter genom att välja **Ja**. Välj **Specifik** för att installera en specifik version av Office för den valda kanalen på slutanvändarenheter. Nu kan du välja den **specifika version** av Office som ska användas. De versioner som är tillgängliga ändras över tid. När du skapar en ny distribution kan de versioner som är tillgängliga därför vara nyare och inte ha vissa äldre versioner tillgängliga. Befintliga distributioner fortsätter att distribuera den äldre versionen, men versionslistan uppdateras kontinuerligt per kanal. Mer information finns i [Översikt över uppdateringskanaler för Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Konfigurera profilen om du vill hoppa över vissa av skärmarna i installationsassistenten <!-- 2276470 -->
När du skapar en macOS-registreringsprofil kommer du att kunna konfigurera den för att hoppa över valfria följande skärmar när en användare går igenom installationsassistenten:
- Android-migrering
- Visningston
- Sekretess
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Ändra i uppdateringsprocessen för lokala anslutningsappar <!-- 2277554 -->
Baserat på feedback från kunder kommer det sätt som uppdateringar av lokala anslutningsappar sker på att ändras. När du först installerar en lokal anslutningsapp sker uppdateringar automatiskt. Den här ändringen börjar i och med den nya PFX-certifikatanslutningsappen för Microsoft Intune och kommer därefter att distribueras till andra typer av lokala anslutningsappar. 

### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Stöd för inställningen Registrera DNS för Windows 10-VPN <!-- 2282852 -->
Du kommer att kunna konfigurera Windows 10-VPN-profiler att dynamiskt registrera de IP-adresser som tilldelas till VPN-gränssnittet med intern DNS, utan behov av anpassade profiler.
[Windows 10-VPN-inställningar](vpn-settings-windows-10.md) visar en lista över aktuella VPN-profilinställningar som är tillgängliga. 

### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-for-work-devices----2451462---"></a>Begränsa appar och blockera åtkomst till företagsresurser på iOS- och Android for Work-enheter <!-- 2451462 -->
I **Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Android for Work** > **Systemsäkerhet** kommer det att finnas en ny inställning för **Begränsade program**. Den här nya inställningen använder en policy för efterlevnad för att blockera åtkomst till företagsresurser om vissa appar är installerade på enheten. Enheten betraktas som icke-kompatibel tills de begränsade apparna tas bort från enheten.
Gäller för: 
- iOS

### <a name="export-azure-classic-portal-compliance-policies-to-csv-file----2469637---"></a>Exportera efterlevnadsprinciper för den klassiska Azure-portalen till CSV-fil <!-- 2469637 -->
Principer för enhetsefterlevnad som skapats i den klassiska Azure-portalen upphör att gälla.  När det sker kan du granska och ta bort alla befintliga principer. Du kan dock inte uppdatera dem. Du kan exportera principerna som en kommaavgränsad fil (CSV). Använd sedan informationen i filen för att återskapa dessa principer i Intune Azure-portalen.
> [!IMPORTANT]
> När den klassiska Azure-portalen upphör kan du inte komma åt dina principer, vilket bland annat betyder att du inte kan se dem. Därför bör du exportera dem och återskapa dem i Azure-portalen innan den klassiska Azure-portalen upphör.

### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Ändra terminologin till ”dra tillbaka” och ”rensa” <!-- 2175759 -->
För att överensstämma med Graph API, kommer följande termer för Intune-användargränssnittet och dokumentationen att ändras:
- **Ta bort företagsinformation** ändras till **Dra tillbaka**
- **Fabriksåterställning** ändras till **Rensa**

### <a name="delete-jamf-devices----2653306---"></a>Ta bort Jamf-enheter <!-- 2653306 -->
Du kommer att kunna ta bort JAMF-hanterade enheter genom att gå till **Enheter** > välj Jamf-enheten > **Ta bort**.

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Fler synkroniseringsalternativ i företagsportalappen för Windows <!-- 2683177 -->
Företagsportalappen för Windows lägger till en åtgärd för enhetssynkronisering till Windows-aktivitetsfältet och snabblistor i startmenyn. Klicka från någon av dessa platser för att snabbt synkronisera dina enheter och få åtkomst till företagets resurser.  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Återställa lösenord för enheter från företagsportalappen för Windows 10 <!-- 2101282 --> 
Dina anställda kommer snart att kunna återställa sina enheters PIN-koder eller lösenord direkt från företagsportalappen för Windows 10. Den här funktionen blir tillgänglig både via fjärranslutningar till Intune-hanterade enheter och i lokala Intune-hanterade enheter som har stöd för lösenordsåterställning. Beroende på typen av enhet tar en begäran för en fjärransluten enhet bort enhetens aktuella lösenord eller skapar ett tillfälligt lösenord. Användare som begär en återställning för en lokal enhet dirigeras om till enhetens appinställningar.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Nya bläddringsfunktioner i appen Företagsportal för Windows <!-- 2317227 -->  
När du bläddrar eller söker efter appar i appen Företagsportal kan du växla mellan den befintliga vyn **Paneler** och den nyligen tillagda vyn **Information**. Den nya vyn visar information om programmet, som namn, utgivare, publiceringsdatum och installationsstatus.  

På sidan **Appar** introduceras vyn **Installerad** där du ser information om slutförda och pågående appinstallationer. Vill du dela med dig av feedback eller tankar om de nya ändringarna? Skicka oss din feedback i appen Företagsportal.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Förbättrade funktioner i appen Företagsportal för användare av enhetsregistreringshanterare <!-- 675800 -->
När en enhetsregistreringshanterare (DEM) loggar in på appen Företagsportal för Windows visar appen DEM:ens aktuella enhet som körs. Den här förbättringen minskar uppnådda tidsgränser som tidigare förekom när appen försökte läsa in alla DEM-registrerade enheter.  

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Konfigurationspaketet för Windows Defender ATP läggs automatiskt till i konfigurationsprofilen <!-- 2144658 -->
När du använder enheter med [Advanced Threat Protection och registrering](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) i Intune kan du för närvarande ladda ned ett konfigurationspaket och lägga till det i din konfigurationsprofil. I en kommande uppdatering hämtar Intune paketet automatiskt från Windows Defender Säkerhetscenter och lägger till det i din profil.

Gäller för Windows 10 och senare.

### <a name="check-for-sccm-compliance----2192052---"></a>Kontrollera SCCM-efterlevnad <!-- 2192052 -->
En kommande uppdatering innehåller en ny efterlevnadsinställning för System Center Configuration Manager (SCCM) (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Windows 10**). SCCM skickar signaler till Intunes efterlevnadsprinciper. Du kan kräva att alla SCCM-signaler returnerar ”kompatibel” med hjälp av Intune-inställningarna.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i SCCM. Om några program på enheten är i ett okänt tillstånd kommer enheten inte att vara kompatibel i Intune.

Gäller för Windows 10 och senare

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Aviseringar om utgående VPP-token eller om att kvarvarande licenser för företagsportalen håller på att ta slut <!-- 2237572 -->
Om du använder Volume Purchase Program (VPP) för att företablera företagsportalen vid DEP-registrering visas en varning i Intune när en VPP-token håller på att upphöra och när licenserna för företagsportalen nästan är slut.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Om du vill ta bort en VPP-token som används för företablering av företagsportalen krävs en bekräftelse <!-- 2237634 -->
En bekräftelse krävs för att ta bort en token för Volymköpsprogram (VPP) om den används för att företablera företagsportalen vid DEP-registrering.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Ytterligare säkerhetsinställningar för Windows Installer <!-- 2282430 -->
Du kommer att kunna tillåta användarna att styra appinstallationer. Om den här inställningen är aktiverad tillåts installationer som i annat fall skulle stoppats på grund av en säkerhetsöverträdelse. Du kommer att kunna ange att Windows Installer ska använda förhöjd behörighet när program installeras i ett system. Du kommer även att kunna ange att WIP-objekt (Windows Information Protection) ska indexeras och att deras metadata ska lagras på en okrypterad plats. När principen är inaktiverad kommer Windows-informationsskyddade objekt inte att indexeras och visas inte i resultaten i Cortana eller Utforskaren. Funktionerna för dessa alternativ kommer att vara inaktiverade som standard. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Du kan blockera tangentbord från tredje part via APP-inställningarna i iOS <!-- 1248481 -->
Intune-administratörer kan blockera användningen av tredjepartstangentbord på iOS-enheter vid åtkomst till organisationens data i skyddade appar. När APP (Application Protection Policy) är inställt på att blockera tredjepartstangentbord visas ett meddelande första gången användaren interagerar med företagsdata och använder ett tredjepartstangentbord. Alla alternativ förutom det interna tangentbordet är blockerade och visas inte för användaren. Enhetsanvändarna ser bara det här meddelandet en gång. 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Kräva icke-biometriskt lösenord vid appstart och viloläge <!-- 1506985 -->

Genom att kräva ett icke-biometriskt lösenord när appen startas och efter angivna tidsgränser så förbättrar Intune säkerheten för MAM-aktiverade (Mobile Application Management) genom att användningen av biometrisk identifiering begränsas till åtkomst av företagets data. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Mobilappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Språkpaket för Office 365 Pro Plus <!-- 1833450 -->
Som Intune-administratör kan du distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Gå till Azure Portal och välj **Microsoft Intune** > **Mobilappar** > **Appar** > **Lägg till**. I listan **Apptyp** på bladet **Lägg till app** väljer du **Windows 10** under **Office 365 Suite**. Välj **Språk** på bladet **Inställningar för appsviten**.

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Förhandsgranska en ny uppdatering av användarupplevelsen för företagsportalens webbplats <!--2000968 -->
Vi lägger till nya funktioner på företagsportalen/iOS-appkatalogen baserat på våra kunders synpunkter. Du kommer att se tydliga förbättringar av befintliga funktioner och användbarheten jämfört med dina Android-, iOS- och Windows-enheter. Delar av webbplatsen, som enhetsinformation, feedback och support samt enhetsöversikten, kommer att få en ny och modern design. Andra nyheter:

- Effektiva arbetsflöden mellan olika plattformar
- Bättre flöden för identifiering och registrering av enheter
- Fler användbara felmeddelanden
- Mer användarvänligt språk, mindre teknisk jargong
- Möjlighet att dela direktlänkar till appar
- Förbättrad prestanda för stora app-kataloger
- Bättre tillgänglighet för alla användare

Uppdateringen förhandsvisas just nu. Du kan registrera dig för att ta del av förhandsgranskningen på http://aka.ms/webcpflighting

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Kräva icke-biometriskt lösenord vid kall appstart och viloläge <!-- 1506985 --> 

Genom att kräva ett icke-biometriskt lösenord när appen kallstartas och efter angivna tidsgränser så förbättrar Intune säkerheten för MAM-aktiverade (Mobile Application Management) genom att användningen av biometrisk identifiering begränsas till åtkomst av företagets data. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Mobilappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar.

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Möjlighet att distribuera nödvändiga verksamhetsspecifika appar till alla användare på Windows 10 Desktop-enheter <!-- 1627835 RS4 -->
Kunderna kommer att kunna distribuera nödvändiga verksamhetsspecifika appar för Windows 10 som kan installeras i enhetens sammanhang. Detta innebär att apparna blir tillgängliga för alla användare på enheten. Detta gäller endast för Windows 10 Desktop-enheter.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Uppdatera Hjälp och Feedback i företagsportalappen för Android <!--1631531 -->

Vi kommer att uppdatera Hjälp och Feedback i företagsportalappen för Android för att följa standarden för Android-appar. Vi kommer att uppdatera företagsportalappen för Android under de kommande månaderna för att dela upp **Hjälp och Feedback** och skilja på menykommandona **Hjälp** och **Skicka feedback**. På sidan **Hjälp** kommer det finnas ett avsnitt med **Vanliga frågor och svar** och **E-postsupport** som visar slutanvändarna hur de laddar upp loggar till Microsoft samt skickar e-post till företagssupporten och beskriver problemet. **Skicka feedback** vägleder användaren via Microsofts standardfeedback, som uppmanar användaren att välja ”Jag gillar det”, ”Jag tycker inte om det” eller ”Jag har en idé”.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Appskyddsprinciper  <!-- 679615 -->
Intunes appskyddsprinciper ger dig möjligheten att skapa globala standardprinciper för att snabbt aktivera skydd för alla användare i hela klientorganisationen.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).



