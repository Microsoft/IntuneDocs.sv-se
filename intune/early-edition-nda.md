---
title: Tidig utgåva
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e37a45122ab4950e2a85cc1c6f6696759d429a3f
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828286"
---
# <a name="the-early-edition-for-microsoft-intune---october-2018"></a>Den tidiga utgåvan för Microsoft Intune – Oktober 2018

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

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Använd Microsofts rekommenderade inställningar med säkerhetsbaslinjer <!-- 2055484 -->
Intune integrerar med andra tjänster som fokuserar på säkerhet, inklusive Windows Defender ATP och Office 365 ATP. Kunder efterfrågar en gemensam strategi och en sammanhängande uppsättning säkerhetsarbetsflöden från slutpunkt till slutpunkt för alla Microsoft 365-tjänster. Vårt mål är att optimera strategier och skapa lösningar som kan hantera säkerhetsåtgärder och vanliga administratörsuppgifter. I Intune vill vi uppnå det här målet genom att publicera en uppsättning Microsoft-rekommenderade ”säkerhetsbaslinjer” (**Intune** > **Security baselines** ((Säkerhetsbaslinjer)).  En administratör kommer att kunna skapa säkerhetsprinciper direkt från dessa baslinjer, och sedan distribuera dem till sina användare. De kan också anpassa rekommendationerna om bästa praxis för att uppfylla behoven i deras organisation. Intune kontrollerar att enheterna uppfyller baslinjerna och meddelar administratören om användare eller enheter inte uppfyller efterlevnadskraven.

### <a name="remove-ability-for-admins-to-wipe-personal-devices-and-reset-passcodes----2934699---"></a>Administratörer kan inte rensa personliga enheter och återställa lösenord <!-- 2934699 -->
För att användarna inte ska behöva oroa sig för att företagets administratörer rensar deras personliga enheter har fjärråtgärderna för [rensning](devices-wipe.md#wipe) och [lösenordsåterställning](device-passcode-reset.md) inaktiverats för personliga enheter. Byt typen av enhetsägarskap till företagsägd enhet om du vill aktivera dessa åtgärder för enheter som ägs av organisationen.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices----1048100---"></a>Autopilot-stöd för Azure Active Directory-anslutna hybridenheter <!-- 1048100 -->
Du kan konfigurera Azure Active Directory-anslutna hybridenheter med hjälp av Autopilot. Enheterna måste vara anslutna till organisationens nätverk för att du ska kunna använda Autopilot-hybridfunktionen.

### <a name="scope-tags-for-apps---1081941---"></a>Omfattningstaggar för appar <!--1081941 -->
Du kommer att kunna skapa omfångstaggar som begränsar åtkomsten till Intune-resurser. Lägg till en omfångstagg till en rolltilldelning och lägg sedan till omfångstaggen i en konfigurationsprofil. Rollen får endast åtkomst till resurser med konfigurationsprofiler som har matchande omfångstaggar (eller inga omfångstaggar).
Om du vill skapa en omfångstagg väljer du **Intune-roller** > **Scope (Tags) (Omfång (taggar))** > **Skapa**.
För att lägga till en omfångstagg till en rolltilldelning väljer du **Intune-roller** > **Alla roller** > **Princip- och profilhanterare** > **Tilldelningar** > **Scope (Tags)** (Omfång (taggar)).
För att lägga till en omfångstagg till en konfigurationsprofil väljer du **Enhetskonfiguration** > **Profiler** > välj en profil > **Egenskaper** > **Scope (Tags)** (Omfång (taggar)).

## <a name="tenant-health-dashboard----1124854---"></a>Instrumentpanelen Hälsa för klientorganisation <!-- 1124854 -->
På sidan med klientorganisationens status i Intune hittar du information om klientorganisationens status på ett och samma ställe. Sidan är uppdelad i fyra delar:  
- **Information om klientorganisationen**: Innehåller information, till exempel MDM-utfärdare, totalt antal registrerade enheter i klientorganisationen och antal licenser. I det här avsnittet visas även den aktuella versionen av tjänsten för din klientorganisation.
- **Status för anslutningsprogrammet**: Innehåller information om konfigurerade anslutningsappar, till exempel Apple VPP, Windows Store för företag och certifikatanslutningar. Baserat på deras aktuella tillstånd är anslutningsapparna flaggade med *Felfri*, *Varning* eller *Ej felfri*.
- **Hälsotillstånd för Intune-tjänsten**: Innehåller aktiva incidenter eller avbrott i klientorganisationen. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office ([https://portal.office.com](https://portal.office.com)).
- **Nytt i Intune**: Innehåller aktiva meddelanden för din klientorganisation, t.ex. aviseringar om att klientorganisationen har fått de senaste funktionerna i Intune. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office ([https://portal.office.com](https://portal.office.com)).

### <a name="enrollment-abandonment-report----1382924---"></a>Rapport över avbrutna registreringar <!-- 1382924 -->
En ny rapport som innehåller information om övergivna registreringar kommer att finnas tillgänglig under **Enhetsregistrering** > **Övervaka**.

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Distribuerade WIP-principer utan användarregistrering <!-- 1434452 -->
WIP-principer (Windows Information Protection) kommer att kunna distribueras utan att MDM-användare behöver registrera sina Windows 10-enheter. Med den här konfigurationen kan företag skydda sina företagsdokument baserat på WIP-konfigurationen, samtidigt som användarna kan fortsätta att hantera sina egna Windows-enheter. När dokument skyddas med en WIP-princip kan skyddade data rensas selektivt av en Intune-administratör. Genom att välja användaren och enheten, och skicka en rensningsbegäran, blir alla data som skyddades via WIP-principen oanvändbara. Från Intune på Azure-portalen väljer du **Mobilapp** > **Selektiv radering av app**.


### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Lägga till en anpassad varumärkesbild för företagsportalappen <!-- 1916266 -->
Som Microsoft Intune-administratör kommer du att kunna ladda upp en anpassad varumärkesbild som visas som bakgrundsbild på användarens profilsida i företagsportalappen. Mer information om hur du konfigurerar företagsportalappen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](company-portal-app.md).

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Gruppera Windows Autopilot-registrerade enheter efter korrelator-ID <!-- 2075110 -->
Intune stöder gruppering av Windows-enheter med ett korrelator-ID när de har registrerats med hjälp av [Autopilot för befintliga enheter](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) via Configuration Manager. Korrelator-ID:t är en parameter i Autopilot-konfigurationsfilen. Intune matchar automatiskt [Azure AD-enhetsattributet enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) med ”OfflineAutopilotprofile-\<korrelator-ID:t\>”. På så sätt kan godtyckligt dynamiska grupper i Azure AD skapas baserat på korrelator-ID via attributet enrollmentprofileName för Autopilot-offlineregistreringar. 


### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Stöd för iOS 12 OAuth i iOS-e-postprofiler <!--2155106 -->
Intunes iOS-e-postprofiler kommer att ha stöd för iOS 12 OAuth. Du kommer åt den här funktionen genom att välja **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **OAuth**. Om den här inställningen är aktiverad händer två saker:
1. En ny profil skickas till enheter som redan har konfigurerats som mål.
2. Slutanvändarna uppmanas att ange sina autentiseringsuppgifter igen.

### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Ny standardinställning för ”Krav på lösenordstyp” för Android, Android-företag<!-- 2649963 -->
När du skapar en ny efterlevnadsprincip (**Intune** > **Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Android** eller **Android-företag** för Plattform > Systemsäkerhet), kommer standardvärdet för **Krav på lösenordstyp** att ändras. Nuvarande standardvärde: Standard för enheten. Nytt standardvärde: Minst numeriskt. Gäller för: Android, Android-företag

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Tilldela Autopilot-profiler till den virtuella gruppen Alla enheter <!--2715522 -->
Du kommer att kunna tilldela Autopilot-profiler till den virtuella gruppen Alla enheter. Om du vill göra det väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > välj en profil >  **Tilldelningar** > under **Tilldela till** väljer du **Alla enheter**.

### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Ny funktion för Azure Active Directory-användningsvillkor <!-- 2870393 -->
Azure Active Directory har en funktion för användningsvillkor som du kan använda i stället för de befintliga Intune-villkoren. Funktionen för användningsvillkor i Azure AD ger större flexibilitet över vilka villkor som ska visas och när, bättre lokaliseringsstöd, bättre kontroll över hur villkoren återges och bättre rapportering. Funktionen för användningsvillkor i Azure AD kräver Azure Active Directory Premium P1 som också är en del av programsviten Enterprise Mobility + Security E3.


### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune bevarar det lokaliserade språket i Office när Office uppdateras på slutanvändarnas datorer <!-- 2971030 -->
När Intune installerar Office på slutanvändarnas datorer får användarna automatiskt samma språkpaket som de hade med tidigare .MSI Office-installationer. 

<!-- 1809 start -->  

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter <!-- 2244713 -->
Du kan skilja kontroll över inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter från att ange identiteten för den registrerade användaren. Administratörer som inte använder IntuneMAMUPN kommer inte att se någon funktionalitetsförändring. När den här funktionen är tillgänglig, bör administratörer som använder IntuneMAMUPN för att styra beteende för dataöverföring på registrerade enheter granska de nya inställningarna och uppdatera sina APP-inställningar efter behov.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Använda en i förväg delad nyckel i en Windows 10 Wi-Fi-profil <!-- 2662938 -->
Du kan använda en i förväg delad nyckel (PSK) med säkerhetsprotokollet WPA/WPA2-Personal för att autentisera en Wi-Fi-konfigurationsprofil för Windows 10.
För närvarande måste du importera en Wi-Fi-profil eller skapa en anpassad profil för att använda en i förväg delad nyckel. [Wi-Fi-inställningar för Windows 10](wi-fi-settings-windows.md) visar en lista över de aktuella inställningarna. 

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>APP-inställningar (App Protection Policy) för webbdata <!-- 2662995 -->
Principinställningarna för webbinnehåll på både Android och iOS-enheter kommer att uppdateras så att de blir bättre på att hantera både http- och https-länkar liksom dataöverföring via universella iOS-länkar och Android App-länkar.  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Frekvensen för Autopilot-enhetssynkronisering ökar till var 12:e timme <!-- 2753673 -->
Autopilot-enheter synkroniserar var 12:e timme i stället för var 24:e timme.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Uppdatering av Intune-landningsidan och byte av nodnamn <!--2867309 -->
Uppdateringar på Intune-landningssidan omfattar nya och ändrade övervakningspaneler och diagram för bättre datavisualisering. Noden **Mobilappar** ändras till **Klientappar**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Ökad åtkomst för slutanvändare med företagsportalappen <!-- 772203 -->
Slutanvändare kommer att få åtkomst till viktiga kontoåtgärder, till exempel återställning av lösenord och AAD-profil, från företagsportalappen.  

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

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Förbättrade funktioner i appen Företagsportal för användare av enhetsregistreringshanterare <!-- 675800 -->
När en enhetsregistreringshanterare (DEM) loggar in på appen Företagsportal för Windows visar appen DEM:ens aktuella enhet som körs. Den här förbättringen minskar uppnådda tidsgränser som tidigare förekom när appen försökte läsa in alla DEM-registrerade enheter.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Kontrollera Configuration Manager-kompatibilitet <!-- 2192052 -->
En kommande uppdatering innehåller en ny kompatibilitetsinställning för System Center Configuration Manager (**Enhetskompatibilitet** > **Principer** > **Skapa princip** > **Windows 10**). Configuration Manager skickar signaler till Intune-kompatibilitet. Med hjälp av Intune-inställningen kan du kräva att alla Configuration Manager-signaler returnerar ”kompatibel”.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd kommer enheten inte att vara kompatibel i Intune.

Gäller för Windows 10 och senare

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Aviseringar om utgående VPP-token eller om att kvarvarande licenser för företagsportalen håller på att ta slut <!-- 2237572 -->
Om du använder Volume Purchase Program (VPP) för att företablera företagsportalen vid DEP-registrering visas en varning i Intune när en VPP-token håller på att upphöra och när licenserna för företagsportalen nästan är slut.

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Du kan blockera tangentbord från tredje part via APP-inställningarna i iOS <!-- 1248481 -->
Intune-administratörer kan blockera användningen av tredjepartstangentbord på iOS-enheter vid åtkomst till organisationens data i skyddade appar. När APP (Application Protection Policy) är inställt på att blockera tredjepartstangentbord visas ett meddelande första gången användaren interagerar med företagsdata och använder ett tredjepartstangentbord. Alla alternativ förutom det interna tangentbordet är blockerade och visas inte för användaren. Enhetsanvändarna ser bara det här meddelandet en gång. 

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



