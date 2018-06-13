---
title: Tidig utgåva
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95ad588b084319cd8a0f5f5c5d92da0e892eed50
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745051"
---
# <a name="the-early-edition-for-microsoft-intune---june-2018"></a>Den tidiga utgåvan för Microsoft Intune – juni 2018

Den **tidiga utgåvan** innehåller en lista med funktioner i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte denna information med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
>Följande ändringar är under utveckling för Intune. Mer information om nya hybridfunktioner finns på sidan med [nyheter om hybridfunktioner](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1806 start -->

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>COSU-stöd (corporate owned, single use) för Android-enheter <!-- 1630973 -->

Intune kommer att ha stöd för strikt hanterade och låsta Android-enheter i helskärmsläge. Det här gör att administratörer får fler verktyg när det gäller att begränsa användningen på en enhet till en enda upp eller en grupp av appar, så att användarna inte kan starta andra appar eller utföra andra åtgärder på enheten.

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS-stöd för Apples program för enhetsregistrering (Device Enrollment Program) <!-- 747651 -->

Intune kommer att ha stöd för registrering av macOS-enheter i Apples program för enhetsregistrering (DEP). Så här gör du:

1. Gå till deploy.apple.com och tilldela macOS-serienummer till en MDM-server.
2. Importera serienumren till Intune.
3. Skapa en registreringsprogramprofil som är specifik för macOS-enheterna.

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Googla namnändringar för Android for Work och Play for Work <!--842873 -->
Intune uppdaterar ”Android for Work”-terminologin med Googles namnändringar.  Termerna ”Android for Work” och ”Play for Work” används inte längre. Annan terminologi används beroende på kontext:

- ”Android enterprise” syftar på den moderna programserien för Android-hantering som helhet.
- ”Arbetsprofil” eller ”profilägare” syftar på BYOD-enheter som hanteras med arbetsprofiler.
- ”Managed Google Play” syftar på Googles appbutik.

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>Övervaka konfigurationsstatus för iOS-appar per enhet <!-- 880037 eeready eestaged -->

Som administratör för Microsoft Intune kan du övervaka konfigurationsstatus för iOS-appar för varje hanterad enhet. Gå till **Microsoft Intune** i Azure Portal och välj **Enheter** > **Alla enheter**. Välj en specifik enhet från listan med hanterade enheter för att visa ett blad för enheten. Välj **Appkonfiguration** på enhetsbladet.  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Du kan blockera tangentbord från tredje part via APP-inställningarna i iOS <!-- 1248481 -->
Intune-administratörer kan blockera användningen av tredjepartstangentbord på iOS-enheter vid åtkomst till organisationens data i skyddade appar. När APP (Application Protection Policy) är inställt på att blockera tredjepartstangentbord visas ett meddelande första gången användaren interagerar med företagsdata och använder ett tredjepartstangentbord. Alla alternativ förutom det interna tangentbordet är blockerade och visas inte för användaren. Enhetsanvändarna ser bara det här meddelandet en gång. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Skapa en princip för enhetskompatibilitet med hjälp av brandväggsinställningar på macOS-enheter <!-- 1497640 -->
När du skapar en ny efterlevnadsprincip i macOS (**Enhetsefterlevnad** > **Principer** > **skapa princip** > **Plattform: macOS** > **Systemsäkerhet**) kommer några nya **brandväggsinställningar** att vara tillgängliga: 
- **Brandvägg**: konfigurera hur inkommande anslutningar ska hanteras i din miljö.
- **Inkommande anslutningar**: **Blockera** alla inkommande anslutningar utom de som behövs för grundläggande internettjänster, som DHCP, Bonjour och IPSec. Den här inställningen blockerar också alla delningstjänster.
- **Stealthläge**: **Aktivera** stealthläget om du vill förhindra att enheten svarar på avsökningsförfrågningar. Enheten fortsätter att besvara inkommande begäranden för godkända appar.

Gäller: macOS 10.12 och senare

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Använd sAMAccountName som användarnamn för e-postprofiler <!-- 1500307 -->

Du kommer att kunna använda det lokala **sAMAccountName** som kontonamn för e-postprofiler för Android, iOS och Windows 10. Du kommer även att kunna hämta domänen från attributet `domain` eller `ntdomain` i Azure Active Directory (Azure AD). Eller ange en anpassad statisk domän.

Om du vill använda den här funktionen måste du synkronisera attributet `sAMAccountName` från din lokala Active Directory-miljö till Azure AD.

Gäller: Android, iOS, Windows 10 och senare

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Kräva icke-biometriskt lösenord vid appstart och viloläge <!-- 1506985 -->

Genom att kräva ett icke-biometriskt lösenord när appen startas och efter angivna tidsgränser så förbättrar Intune säkerheten för MAM-aktiverade (Mobile Application Management) genom att användningen av biometrisk identifiering begränsas till åtkomst av företagets data. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Mobilappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar.

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Selektiv rensning av organisations appdata <!-- 1507030 -->
Administratörer kommer att kunna konfigurera selektiv rensning av organisationens data som en ny åtgärd när villkoren i APP-åtkomstinställningarna inte är uppfyllda.  Den här funktionen gör att administratörer kan skydda och ta bort känsliga organisationsdata från appar baserat på förkonfigurerade kriterier.

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Återkalla en iOS-app som köpts via VPP <!-- 1777384 -->
Som Microsoft Intune-administratör kan du återkalla licensen för en iOS-app som köpts via volyminköpsprogrammet (VPP). Du kan meddela användare när en app inte längre är tilldelad till dem. Om du återkallar en applicens så avinstalleras inte den relaterade VPP-appen från enheten. Om du vill avinstallera en VPP-app, måste du ändra tilldelningsåtgärden till **avinstallera**. Du kan se antalet återkallade licenser vid noden **Licensierade appar** i arbetsbelastningen **App** i Intune. Mer information om VPP-appar i iOS finns i [Så här hanterar du iOS-appar som köpts genom ett volyminköpsprogram med Microsoft Intune](vpp-apps-ios.md).

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Språkpaket för Office 365 Pro Plus <!-- 1833450 -->
Som Intune-administratör kan du distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Gå till Azure Portal och välj **Microsoft Intune** > **Mobilappar** > **Appar** > **Lägg till**. I listan **Apptyp** på bladet **Lägg till app** väljer du **Windows 10** under **Office 365 Suite**. Välj **Språk** på bladet **Inställningar för appsviten**.

### <a name="revoke-ios-vpp-app-license----1863797---"></a>Återkalla VPP-applicenser i iOS <!-- 1863797 -->
Som administratör kan du återkalla licenser för VPP-appar i iOS som tilldelats till en användare eller enhet. När du avinstallerar en VPP-app i iOS kan du också återkalla applicensen. Sedan kan du tilldela applicensen till en annan användare eller enhet. Mer information om licenser för VPP-appar i iOS finns i [Hantera volyminköpta iOS-appar i Microsoft Intune](vpp-apps-ios.md).

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Ny uppdatering av användarupplevelse för företagsportalens webbsida <!--2000968 -->
Vi lägger till nya funktioner på företagsportalen baserat på våra kunders synpunkter. Du kommer att se tydliga förbättringar av befintliga funktioner och användbarheten jämfört med dina Android-, iOS- och Windows-enheter. Delar av webbplatsen, som enhetsinformation, feedback och support samt enhetsöversikten, kommer att få en ny och modern design. Andra nyheter:

- Effektiva arbetsflöden mellan olika plattformar
- Bättre flöden för identifiering och registrering av enheter
- Fler användbara felmeddelanden
- Mer användarvänligt språk, mindre teknisk jargong
- Möjlighet att dela direktlänkar till appar
- Förbättrad prestanda för stora app-kataloger
- Bättre tillgänglighet för alla användare

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Redigera dina distributioner av Office 365 Pro Plus-appar <!-- 2150145 -->
Som Microsoft Intune-administratör kan du enklare redigera distributioner av Office 365 Pro Plus-appar. Gå till Azure Portal och välj **Microsoft Intune** > **Mobilappar** > **Appar**. Välj Office 365 Pro Plus Suite i listan med appar.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Radgranskning av dubbletter av uppladdade företagsenhets-id:n <!-- 2203794 -->
När du laddar upp företags-id:n så får du en lista med eventuella dubbletter i Intune, och du kan välja mellan att ta bort eller behålla den befintliga informationen. Rapporten visas om det finns dubbletter när du har valt **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till id:n**. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Lägga till företagsenhets-id:n manuellt <!-- 2203803 -->
Du kommer att kunna lägga till företagsenhets-id:n manuellt. Välj **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till**.

### <a name="new-status-for-devices-in-device-configuration----2308882---"></a>Ny status för enheter i enhetskonfigurationen <!-- 2308882 -->
Följande nya statusar läggs till i **Enhetskonfiguration** > **Översikt**:
- lyckades
- fel
- konflikt
- väntar
- inte tillämpligt En bild med antalet enheter på andra plattformar visas också. Om du till exempel tittar på en iOS-profil visas antalet enheter med andra system än iOS som också har tilldelats till den här profilen. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Enhetsefterlevnaden får stöd för antiviruslösningar från tredje part <!-- 2325484 -->
När du skapar en ny princip för enhetsefterlevnad (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Plattform: Windows 10 eller senare** > **Inställningar** > **Systemsäkerhet**) kommer några nya alternativ för **Enhetssäkerhet** att vara tillgängliga: 
- **Antivirus**: När **Kräv** är valt kan du kontrollera efterlevnad med antivirusprogram som är registrerade i Windows Security Center, som Symantec. 
- **Antispionprogram**: När **Kräv** är valt kan du kontrollera efterlevnad med antispionprogram som är registrerade i Windows Security Center, som Symantec. 

Gäller: Windows 10 och senare 

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Stöd för Palo Alto Networks GlobalProtect VPN-profiler <!-- 1333680 eeready ! -->

Med den här uppdateringen kan du välja Palo Alto Networks GlobalProtect som VPN-anslutningstyp för VPN-profiler i Intune (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Profiltyp** > **VPN**). I den här versionen stöds följande plattformar: 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>Ange efterlevnad enligt enhetsplats <!-- 851881 ! -->
I vissa fall kanske du vill begränsa åtkomsten till företagets resurser till en specifik plats som definierats av en nätverksanslutning. Du kommer att kunna skapa en efterlevnadsprincip (**Enhetsefterlevnad** > **Platser**) baserat på IP-adressen till enheten. Om enheten flyttas utanför IP-intervallet kan enheten inte komma åt företagets resurser.

Gäller: Android-enheter 6.0 och senare med den uppdaterade företagsportalappen

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Förbättrad felsökning för appinstallationen <!-- 928990 -->
På Microsoft Intune MDM-hanterade enheter kan ibland appinstallationer misslyckas. När dessa appinstallationer misslyckas, kan det vara en utmaning att förstå felorsaken eller felsöka problemet. Vi levererar en allmänt tillgänglig förhandsversion av våra appfelsökningsfunktioner. Du ser en ny nod under varje enskild enhet som kallas **Hanterade appar**. Den visar en lista med appar som har levererats via Intune MDM. I noden visas en lista över installeringstillstånd för appar. Om du väljer en enskild app visas vyn felsökning för den specifika appen. I felsökningsvyn visas slutpunkt till slutpunkt-livscykeln för appen, till exempel när appen har skapats, ändrats, riktats och levererats till en enhet. Dessutom, om inte appinstallationen lyckades visas felkoden och ett användbart meddelande om orsaken till felet.

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Kräva icke-biometriskt lösenord vid kall appstart och viloläge <!-- 1506985 --> 

Genom att kräva ett icke-biometriskt lösenord när appen kallstartas och efter angivna tidsgränser så förbättrar Intune säkerheten för MAM-aktiverade (Mobile Application Management) genom att användningen av biometrisk identifiering begränsas till åtkomst av företagets data. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Mobilappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Blockera åtkomst till appen baserat på icke-godkända enhetsleverantörer och modeller  <!-- 1425689 ! -->
Intune IT-administratören kommer att kunna tillämpa en angiven lista över Android-tillverkare och/eller iOS-modeller via Intune App Protection-principer. IT-administratören kan ange en semikolonavgränsad lista över tillverkare för Android-principer och enhetsmodeller för iOS-principer. Intune App Protection-principer gäller endast för Android och iOS. Det ska finnas två separata åtgärder som kan utföras på den angivna listan:
- En blockering från åtkomst till appen på enheter som inte har angetts.
- Eller en selektiv rensning av företagets data på enheter som inte har angetts. 

Användaren kommer inte att få åtkomst till det aktuella programmet om principkraven inte uppfylls. Baserat på inställningarna kan användaren bli blockerad eller rensas selektivt på sina företagsdata i appen. På iOS-enheter kräver den här funktionen medverkan av program (d.v.s. WXP, Outlook, Managed Browser, Yammer) för att integrera Intune APP SDK för att de minsta versionsinställningarna ska tillämpas för de berörda programmen. Den här integreringen händer på löpande bas, och är beroende av specifika programteam. På Android kräver funktionen den senaste företagsportalen. 

På slutanvändarens enheter kan Intune-klienten göra åtgärder baserat på en enkel matchning av strängar som angetts i Intune-bladet för programskyddsprinciper. Detta beror helt på värdet som enheten rapporterar. IT-administratören rekommenderas därför att säkerställa att det avsedda funktionssättet är korrekt. Detta kan åstadkommas genom att testa den här inställningen baserat på en rad olika enhetstillverkare och modeller som är riktade till en liten användargrupp. I Microsoft Intune, välj **Mobilappar** > **Appskyddsprinciper** för att visa och lägga till appskyddsprinciper. Mer information om att appskyddsprinciper finns i [Vad är appskyddsprinciper](app-protection-policy.md).

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Aktivera helskärmsläge på Windows 10-enheter <!-- 1560072 ! -->
På Windows 10-enheter kan du skapa en konfigurationsfil och aktivera helskärmsläge (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10** > **Enhetsbegränsningar** > **Helskärmsläge**). I den här uppdateringen av **Helskärmsläge (förhandsgranskning)** döps inställningen om till **Helskärmsläge (föråldrad)**. **Helskärmsläge (föråldrad)** rekommenderas inte längre för användning, men fortsätter att fungera fram till juli-uppdateringen. **Helskärmsläge (föråldrad)** ersätts av den nya profiltypen **Helskärmsläge** (**Skapa profil** > **Windows 10**  >  **Helskärmsläge (förhandsgranskning)**), som innehåller inställningar för att konfigurera helskärmslägen på Windows 10 RS4 och senare.

Gäller för Windows 10 och senare.

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Hämta den kopplade appanvändarens modell-ID (AUMID) för Microsoft Store för företagsappar i helskärmsläge <!-- 1560077 ! -->
Intune kommer att kunna hämta appanvändarens modell-ID:n (AUMID:er) för Microsoft Store för företagsappar (WSfB) för bättre konfiguration av helskärmslägesprofilen.

Mer information om Microsoft Store för företagsappar finns i [Hantera appar från Microsoft Store för företag](windows-store-for-business.md).

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Åtkomståtgärder för appskyddsprinciper <!-- 1483510 EEready -->
Du kommer snart att kunna konfigurera appskyddsprinciper för att uttryckligen rensa, blockera eller varna icke-kompatibla enheter. Den senaste åtgärden *Rensa* tar bort företagets företagsdata från en enhet. Om det uppstår en rensning meddelas enhetens användare om både orsaken för rensning och åtgärdsstegen. För vissa inställningar som lägsta version av operativsystemet, kommer du att kunna använda flera åtgärder, till exempel blockering och rensa. De här åtgärderna utlöses när appen startas.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Ny inventeringsinformation för Windows-enheter <!-- 1333569 eeready -->

För Windows-enheter är följande inventeringsinformation tillgänglig för varje enhet i fliken **Maskinvara** (**Grupper** > **Alla mobila enheter**  >  **Enheter** > välj användarens enhet > **Visa egenskaper** > **Maskinvara**):
- TPM
- Antivirus
- Antispionprogram
- Brandvägg
- UAC
- Batteri
- Domännamn

Mer information om hur dessa data hämtas av kryptografiprovidern finns i DeviceStatus-posterna i artikeln [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp).

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune och Microsoft Edge-webbläsaren <!-- 1818969 -->
Microsoft Edge-webbläsaren för mobila enheter (iOS och Android) har nu stöd för Intune-appskyddsprinciper. Användare som loggar in med sina företags Azure AD-konton i Edge-webbläsarprogram kommer att skyddas av Intune. 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Ny språk-/regionsinställning när du konfigurerar OOBE för Autopilot <!-- 1821766 -->
En ny konfigurationsinställning kommer att kunna ange språk och region för Autopilot-profiler under Out of Box-upplevelsen.

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Ny inställning för att konfigurera enhetstangentbord <!-- 1821768 -->
En ny inställning kommer att kunna konfigurera tangentbordet för Autopilot-profiler under Out of Box-upplevelsen.

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Använd TeamViewer för att skärmdela iOS- och MacOS-enheter <!-- 1985547 -->
För närvarande kan du använda TeamViewer för att fjärradministrera [Intune-hanterade Android- och Windows-enheter](device-profile-android-teamviewer.md).

Administratörer kommer att kunna ansluta till TeamViewer och börja skärmdela en session med iOS- och macOS-enheter. iPhone-, iPad- och macOS-användare kan dela sina skärmar live med andra stationära och mobila enheter. 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Enhetsprofilens grafiska användardiagram är tillbaka <!-- 2160133 -->
För att förbättra det numeriska antal som visas på enhetsprofilens grafiska diagram (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt** ), togs det grafiska diagrammet tillfälligt bort.

Med den här uppdateringen är det grafiska användardiagrammet tillbaka och visas i Azure Portal.

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Tilldela alla användare och alla enheter som omfångsgrupper <!-- 2196803 -->
Du kommer att kunna tilldela alla användare, alla enheter och alla användare och alla enheter i omfångsgrupper. Om du vill göra det väljer du **Intune-roller** > **Alla roller** > **Policy and profile manager** > **Tilldelningar** > välj en tilldelning > **Omfång (grupper)**.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-profiler flyttas till en grupp som är riktad mot <!-- 1877935 -->
För närvarande kan AutoPilot-distributionsprofiler tilldelas till valda enheter. När den här funktionen har släppts är det här vad du ska göra om du vill tilldela dessa profiler:
- Skapa grupper (Azure AD) som innehåller AutoPilot-enheter
- Tilldela önskade profiler till en Azure AD-grupp. AutoPilot-profilen kommer nu att tilldelas till AutoPilot-enheter i gruppen.

### <a name="management-name-field-will-be-editable----1875989---"></a>Hanteringsnamnfältet kan redigeras <!-- 1875989 -->
Du kommer att kunna redigera hanteringsnamnfältet på en enhets blad för **Egenskaper**. Om du vill redigera det här fältet väljer du **Enheter** > **Alla enheter** > välj enheten > **Egenskaper**. Du kan använda hanteringsnamnfältet för att unikt identifiera en enhet.

<!-- 1804 start -->

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Tillägg till inställningar av säkerhetsalternativ för lokal enhet <!-- 1403702 -->
Du kommer att kunna konfigurera ytterligare inställningar av säkerhetsalternativ för lokala Windows 10-enheter. Det kommer att finnas fler inställningar i Microsoft-nätverksklienten, Microsoft-nätverksservern, nätverksåtkomst och säkerhet, samt interaktiv inloggning. Inställningarna finns i kategorin Endpoint Protection när du skapar en princip för Windows 10-enhetskonfiguration.

### <a name="rules-for-removing-devices----1609459---"></a>Regler för att ta bort enheter <!-- 1609459 -->
Det kommer att finnas nya regler som gör att du automatiskt kan ta bort enheter som inte har checkats in under ett visst antal dagar som du anger. Om du vill se den nya regeln går du till fönstret **Intune**, väljer **Enheter** och sedan **Regler för borttagning av enheter**.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Förhindra konsumentappar och funktioner för anpassad upplevelse i Windows 10 Enterprise RS4 AutoPilot-enheter<!-- 1621980 -->
Du kommer att kunna förhindra installationen av konsumentappar och funktioner för anpassad upplevelse på dina Windows 10 Enterprise RS4 AutoPilot-enheter. Om du vill se den här funktionen går du till **Intune** > **Enhetsregistrering** > **Windows-registrering** > **Windows AutoPilot-profiler** > **Skapa nytt** > **Registreringsinställningar**. 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Stöd för flera Exchange Connector <!-- 2070451 -->

Du kommer inte längre vara begränsad till en Exchange Connector per klient i Microsoft Intune. Intune stöder flera Exchange Connector, så du kan ställa in villkorlig åtkomst i Intune med flera lokala Exchange-organisationer.

Med en lokal Exchange Connector för Intune kan du hantera enhetsåtkomst till dina lokala Exchange-postlådor, baserat på om en enhet har registrerats i Intune och uppfyller Intunes enhetsefterlevnadsprinciper. Om du vill konfigurera ett anslutningsprogram laddar du ned den lokala Exchange Connector för Intune från Azure-portalen och installerar den på en server i Exchange-organisationen. På Microsoft Intune-instrumentpanelen väljer du **Lokal åtkomst** och under **Installation** väljer du sedan **Exchange ActiveSync Connector**. Ladda ned det lokala Exchange-anslutningsprogrammet och installera det på en server i din Exchange-organisation. Nu när du är inte längre begränsad till ett Exchange-anslutningsprogram per klient, och om du har ytterligare Exchange-organisationer, kan du följa samma process för att ladda ned och installera ett anslutningsprogram för varje ytterligare Exchange-organisation.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Möjlighet att distribuera nödvändiga verksamhetsspecifika appar till alla användare på Windows 10 Desktop-enheter <!-- 1627835 RS4 -->
Kunderna kommer att kunna distribuera nödvändiga verksamhetsspecifika appar för Windows 10 som kan installeras i enhetens sammanhang. Detta innebär att apparna blir tillgängliga för alla användare på enheten. Detta gäller endast för Windows 10 Desktop-enheter.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registreringen av företagsportalen har förbättrats <!-- 1874230-->
Användare som registrerar en enhet med hjälp av företagsportalen i Windows 10 version 1703 och senare, kommer att kunna slutföra det första steget i registreringen utan att lämna appen.

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



