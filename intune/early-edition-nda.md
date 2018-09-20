---
title: Tidig utgåva
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/4/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: beee1462c1b6e683287b4d304df386ce525be820
ms.sourcegitcommit: 8fdddb684ecf5eabf071907168413bcd89a2f702
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141651"
---
# <a name="the-early-edition-for-microsoft-intune---september-2018"></a>Den tidiga utgåvan för Microsoft Intune – september 2018

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

<!-- 1809 start -->

### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices-----1248496----"></a>Åtkomst till användarkonto för Intune-appar på hanterade Android- och iOS-enheter <!-- ! 1248496  -->

Som Microsoft Intune-administratör kan du styra vilka användarkonton som läggs till i Microsoft Office-program på hanterade enheter. Du kan begränsa åtkomsten till endast tillåtna användarkonton i organisationen och blockera personliga konton på registrerade enheter. 

### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10----1333668---"></a>Skapa DNS-suffix i VPN-konfigurationsprofiler på enheter som kör Windows 10 <!-- 1333668 -->
När du skapar en profil för VPN-enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  plattform: **Windows 10 och senare** > profiltyp: **VPN**), anger du vissa DNS-inställningar. Du kan även ange flera **DNS-suffix** i Intune. När du använder DNS-suffix, kan du söka efter en nätverksresurs med dess korta namn i stället för det fullständiga domännamnet (FQDN). I och med den här uppdateringen kan du ändra ordningen på DNS-suffix i Intune.
[Windows 10-VPN-inställningar](vpn-settings-windows-10.md#dns-settings) visar en lista över aktuella DNS-inställningar.
Gäller för: Windows 10-enheter

### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Stöd för ständig VPN för Android-arbetsprofiler <!-- 1333705 -->
Du kan använda ständiga VPN-anslutningar på Android-företagsenheter med hanterade arbetsprofiler. Ständiga VPN-anslutningar förblir anslutna eller återansluter omedelbart när användaren låser upp sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. Du kan också placera anslutningen i ”låst” läge, vilket blockerar all nätverkstrafik tills VPN-anslutningen aktiveras.
Inställningar för Ständig VPN finns i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android-företag** som plattform > **Enhetsbegränsningar** under **Endast arbetsprofiler** som Profiltyp > inställningar för **Anslutning**. 

### <a name="outlook-for-ios-and-android-app-configuration-policy---1828527---"></a>Outlook för iOS och Android – Princip för appkonfiguration <!--1828527 -->
Du kan skapa en appkonfigurationsprincip för iOS för Outlook för iOS och Android. Ytterligare konfigurationsinställningar läggs till vartefter de aktiveras för Outlook för iOS och Android.

### <a name="remotely-lock-noncompliant-devices----2064495---"></a>Fjärrlåsa icke-kompatibla enheter <!-- 2064495 -->
När en enhet inte är kompatibel, kan du skapa en åtgärd i kompatibilitetsprincipen som låser enheten via en fjärranslutning. I Intune > **Enhetskompatibilitet** skapar du en ny princip eller väljer en befintlig princip. Välj **Åtgärder vid inkompatibilitet** > **Lägg till** och välj att fjärrlåsa enheten.
Stöds på: 
- Android
- iOS
- macOS
- Windows 10 Mobil 
- Windows Phone 8.1 och senare 

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter <!-- 2244713 -->
Du kan skilja kontroll över inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter från att ange identiteten för den registrerade användaren. Administratörer som inte använder IntuneMAMUPN kommer inte att se någon funktionalitetsförändring. När den här funktionen är tillgänglig, bör administratörer som använder IntuneMAMUPN för att styra beteende för dataöverföring på registrerade enheter granska de nya inställningarna och uppdatera sina APP-inställningar efter behov.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Använda en i förväg delad nyckel i en Windows 10 Wi-Fi-profil <!-- 2662938 -->
Du kan använda en i förväg delad nyckel (PSK) med säkerhetsprotokollet WPA/WPA2-Personal för att autentisera en Wi-Fi-konfigurationsprofil för Windows 10.
För närvarande måste du importera en Wi-Fi-profil eller skapa en anpassad profil för att använda en i förväg delad nyckel. [Wi-Fi-inställningar för Windows 10](wi-fi-settings-windows.md) visar en lista över de aktuella inställningarna. 

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Frekvensen för Autopilot-enhetssynkronisering ökar till var 12:e timme <!-- 2753673 -->
Autopilot-enheter synkroniserar var 12:e timme i stället för var 24:e timme.

### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Använda Autopilot-profil för registrerade Windows 10-enheter som inte redan har registrerats för Autopilot <!-- 1558983 -->
Du kan använda Autopilot-profiler för registrerade Windows 10-enheter som inte redan har registrerats för Autopilot. I Autopilot-profilen väljer du alternativet **Omvandla alla målenheter till Autopilot** för att automatiskt registrera andra än Autopilot-enheter med Autopilot-distributionstjänsten. Det kan ta upp till 48 timmar för registreringen att bearbetas. Autopilot konfigurerar enheten efter att den har avregistrerats och återställts. 

### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564--"></a>Skapa flera profiler för sidan för registreringsstatus och tilldela dem till Azure AD-grupper <!-- 2526564-->
Du kan skapa flera profiler för en sida för registreringsstatus och tilldela dem till AAD-grupper.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Uppdatering av Intune-landningsidan och byte av nodnamn <!--2867309 -->
Uppdateringar på Intune-landningssidan omfattar nya och ändrade övervakningspaneler och diagram för bättre datavisualisering. Noden **Mobilappar** ändras till **Klientappar**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Ökad åtkomst för slutanvändare med företagsportalappen <!-- 772203 -->
Slutanvändare kommer att få åtkomst till viktiga kontoåtgärder, till exempel återställning av lösenord och AAD-profil, från företagsportalappen.

### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Utfärda SCEP-certifikat till användarlösa enheter <!-- 1744554 -->
För närvarande utfärdas certifikat till användare. Du kommer att kunna utfärda SCEP-certifikat till enheter, inklusive användarlösa enheter som informationsdatorer (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** som plattform > **SCEP-certifikat** som profil). Övriga uppdateringar:
- Egenskapen **Ämne** i en SCEP-profil är nu en anpassad textruta och kan innehålla nya variabler. 
- Egenskapen **Alternativt namn för certifikatmottagare (SAN)** i en SCEP-profil är nu i tabellformat och kan innehålla nya variabler. I tabellen kan en administratör lägga till ett attribut och fylla i värdet i en anpassad textruta. SAN stöder följande attribut: 
  - DNS
  - E-postadress
  - UPN Dessa nya variabler kan läggas till med statisk text i en textruta för anpassat värde. Till exempel DNS-attributet kan läggas till som `DNS = {{AzureADDeviceId}}.domain.com`.
  > [!NOTE]
  > Klammerparenteser { }, semikolon ; och vertikalstreck | fungerar inte i den statiska texten för SAN. Klammerparenteser får endast omfatta en av de nya variablerna för enhetscertifikat för antingen `Subject` eller `Subject alternative name`. Nya variabler för enhetscertifikat:  
```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` fungerar endast för Windows-enheter och domänanslutna enheter. 
>  -  När du anger enhetsegenskaper som IMEI, serienummer och fullständigt domännamn i ämnet eller SAN för ett certifikat, tänk på att de här egenskaperna kan förfalskas av en person med åtkomst till enheten. 

[Skapa en SCEP-certifikatprofil](certificates-scep-configure.md#create-a-scep-certificate-profile) visar en lista över aktuella variabler när du skapar en konfigurationsprofil för SCEP. 

Gäller för: Windows 10 och senare samt iOS, stöds för Wi-Fi



<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-token som används av en annan MDM <!-- 1488946 -->
Intune identifierar och visar information om en token för volyminköpt Apple-program (VPP) används av både Intune och en annan MDM.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>iOS-versionsnumret och byggenumret visas <!-- 1892471 -->
I **Enhetsefterlevnad** > **Enhetsefterlevnad** visas iOS-operativsystemets version. I kommande uppdateringar visas även byggenumret.
När säkerhetsuppdateringar lanseras låter Apple vanligtvis versionsnumret vara som det är men uppdaterar byggenumret. Genom att visa byggenumret kan du enkelt kontrollera om en säkerhetsriskuppdatering har installerats.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Tillbakadragna enheter i instrumentpanelen för enhetsefterlevnad <!-- 1981119 -->
I en kommande uppdatering tas tillbakadragna enheter bort från instrumentpanelen för enhetsefterlevnad. Detta ändrar dina efterlevnadsnummer.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Ändra i uppdateringsprocessen för lokala anslutningsappar <!-- 2277554 -->
Baserat på feedback från kunder kommer det sätt som uppdateringar av lokala anslutningsappar sker på att ändras. När du först installerar en lokal anslutningsapp sker uppdateringar automatiskt. Den här ändringen börjar i och med den nya PFX-certifikatanslutningsappen för Microsoft Intune och kommer därefter att distribueras till andra typer av lokala anslutningsappar. 

### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224-eeready---"></a>Profilförbättringar för informationsdatorer med Windows 10 och senare i Azure Portal <!-- 2748224 eeready -->
Profilen för enhetskonfiguration för informationsdatorer med Windows 10 (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  plattform: **Windows 10 och senare** > profiltyp: **VPN**) förbättras: 
- För närvarande kan du skapa flera informationsdatorprofiler på samma enhet. I och med den här uppdateringen stöder Intune endast en informationsdatorprofil per enhet. Om du fortfarande behöver flera informationsdatorprofiler på en enskild enhet kan du använda en anpassad URI.
– I en profil för **informationsdator med flera appar** kan du välja programikonernas storlek och ordning i **Startmenylayout** i programrutnätet. Om du vill anpassa mera, kan du ladda upp en XML-fil.
- Inställningarna för webbläsare för informationsdator flyttas till inställningarna för **Informationsdator**. För närvarande har inställningarna för **Webbläsare för informationsdator** sin egen kategori i Azure Portal.
Gäller: Windows 10 och senare

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Förbättrade funktioner i appen Företagsportal för användare av enhetsregistreringshanterare <!-- 675800 -->
När en enhetsregistreringshanterare (DEM) loggar in på appen Företagsportal för Windows visar appen DEM:ens aktuella enhet som körs. Den här förbättringen minskar uppnådda tidsgränser som tidigare förekom när appen försökte läsa in alla DEM-registrerade enheter.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Kontrollera Configuration Manager-kompatibilitet <!-- 2192052 -->
En kommande uppdatering innehåller en ny kompatibilitetsinställning för System Center Configuration Manager (**Enhetskompatibilitet** > **Principer** > **Skapa princip** > **Windows 10**). Configuration Manager skickar signaler till Intune-kompatibilitet. Med hjälp av Intune-inställningen kan du kräva att alla Configuration Manager-signaler returnerar ”kompatibel”.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd kommer enheten inte att vara kompatibel i Intune.

Gäller för Windows 10 och senare

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Aviseringar om utgående VPP-token eller om att kvarvarande licenser för företagsportalen håller på att ta slut <!-- 2237572 -->
Om du använder Volume Purchase Program (VPP) för att företablera företagsportalen vid DEP-registrering visas en varning i Intune när en VPP-token håller på att upphöra och när licenserna för företagsportalen nästan är slut.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Ytterligare säkerhetsinställningar för Windows Installer <!-- 2282430 -->
Du kommer att kunna tillåta användare att styra appinstallationer. Om den här inställningen är aktiverad tillåts installationer som i annat fall skulle stoppats på grund av en säkerhetsöverträdelse. Du kommer att kunna ange att Windows-installationsprogrammet ska använda förhöjd behörighet när program installeras i ett system. Du kommer även att kunna ange att WIP-objekt (Windows Information Protection) ska indexeras och att deras metadata ska lagras på en okrypterad plats. När principen är inaktiverad kommer Windows-informationsskyddade objekt inte att indexeras och visas inte i resultaten i Cortana eller Utforskaren. Funktionerna för dessa alternativ kommer att vara inaktiverade som standard. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Du kan blockera tangentbord från tredje part via APP-inställningarna i iOS <!-- 1248481 -->
Intune-administratörer kan blockera användningen av tredjepartstangentbord på iOS-enheter vid åtkomst till organisationens data i skyddade appar. När APP (Application Protection Policy) är inställt på att blockera tredjepartstangentbord visas ett meddelande första gången användaren interagerar med företagsdata och använder ett tredjepartstangentbord. Alla alternativ förutom det interna tangentbordet är blockerade och visas inte för användaren. Enhetsanvändarna ser bara det här meddelandet en gång. 

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Språkpaket för Office 365 Pro Plus <!-- 1833450 -->
Som Intune-administratör kommer du att kunna distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Gå till Azure Portal och välj **Microsoft Intune** > **Mobilappar** > **Appar** > **Lägg till**. I listan **Apptyp** på bladet **Lägg till app** väljer du **Windows 10** under **Office 365 Suite**. Välj **Språk** på bladet **Inställningar för appsviten**.

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>Kräv icke-biometrisk efter angiven tidsgräns <!-- 1506985 --> 

Genom att kräva en icke-biometrisk PIN-kod efter en tidsgräns angiven av en administratör förbättras säkerheten för appar som har aktiverats för hantering av mobilprogram (MAM) genom att användningen av biometrisk identifiering för åtkomst till företagets data begränsas av Intune. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Mobilappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar.

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Uppdatera Hjälp och Feedback i företagsportalappen för Android <!--1631531 -->

Vi kommer att uppdatera Hjälp och Feedback i företagsportalappen för Android för att följa standarden för Android-appar. Vi kommer att uppdatera företagsportalappen för Android under de kommande månaderna för att dela upp **Hjälp och Feedback** och skilja på menykommandona **Hjälp** och **Skicka feedback**. På sidan **Hjälp** kommer det finnas ett avsnitt med **Vanliga frågor och svar** och **E-postsupport** som visar slutanvändarna hur de laddar upp loggar till Microsoft samt skickar e-post till företagssupporten och beskriver problemet. **Skicka feedback** vägleder användaren via Microsofts standardfeedback, som uppmanar användaren att välja ”Jag gillar det”, ”Jag tycker inte om det” eller ”Jag har en idé”.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).



