---
title: Tidig utgåva
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6cc33bc6e03d2e0370c9e2c2dd9d3462296710e6
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329692"
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



### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-token som används av en annan MDM <!-- 1488946 -->
Intune identifierar och visar information om en token för volyminköpt Apple-program (VPP) används av både Intune och en annan MDM.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>iOS-versionsnumret och byggenumret visas <!-- 1892471 -->
I **Enhetsefterlevnad** > **Enhetsefterlevnad** visas iOS-operativsystemets version. I kommande uppdateringar visas även byggenumret.
När säkerhetsuppdateringar lanseras låter Apple vanligtvis versionsnumret vara som det är men uppdaterar byggenumret. Genom att visa byggenumret kan du enkelt kontrollera om en säkerhetsriskuppdatering har installerats.

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

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Konfigurera profilen om du vill hoppa över vissa av skärmarna i installationsassistenten <!-- 2276470 -->
När du skapar en macOS-registreringsprofil kommer du att kunna konfigurera den för att hoppa över valfria följande skärmar när en användare går igenom installationsassistenten:
- Android-migrering
- Visningston
- Sekretess
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Ändra i uppdateringsprocessen för lokala anslutningsappar <!-- 2277554 -->
Baserat på feedback från kunder kommer det sätt som uppdateringar av lokala anslutningsappar sker på att ändras. När du först installerar en lokal anslutningsapp sker uppdateringar automatiskt. Den här ändringen börjar i och med den nya PFX-certifikatanslutningsappen för Microsoft Intune och kommer därefter att distribueras till andra typer av lokala anslutningsappar. 



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

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Använda VPP enhetslicenser för att företablera företagsportalen vid DEP-registrering <!-- 1608345 -->
Du kan använda VPP-enhetslicenser (volymköpsprogram) för att företablera företagsportalen under registreringar med Programmet för enhetsregistrering (DEP). Detta gör du genom att ange den VPP-token som du vill använda för att installera företagsportalen när du skapar eller redigerar en registreringsprofil. Se till att din token inte upphör att gälla och att du har tillräckligt många licenser för företagsportalappen. Om token upphör att gälla eller om licenserna tar slut kan Intune push-överföra företagsportalen från App Store istället (då krävs ett Apple-ID).

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

Genom att kräva ett icke-biometriskt lösenord när appen startas och efter angivna tidsgränser så förbättrar Intune säkerheten för MAM-aktiverade (Mobile Application Management) genom att användningen av biometrisk identifiering begränsas till åtkomst av företagets data. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Klientappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Språkpaket för Office 365 Pro Plus <!-- 1833450 -->
Som Intune-administratör kan du distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Gå till Azure Portal och välj **Microsoft Intune** > **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** på bladet **Lägg till app** väljer du **Windows 10** under **Office 365 Suite**. Välj **Språk** på bladet **Inställningar för appsviten**.

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

Genom att kräva ett icke-biometriskt lösenord när appen kallstartas och efter angivna tidsgränser så förbättrar Intune säkerheten för MAM-aktiverade (Mobile Application Management) genom att användningen av biometrisk identifiering begränsas till åtkomst av företagets data. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Klientappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar.

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



