---
title: Tidig utgåva
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0500194f5afaba11f37b84bbdf606e6167632a71
ms.sourcegitcommit: afa2e84d5cadf5542ecabc26e61dc71919992a22
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37340198"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Den tidiga utgåvan för Microsoft Intune – juli 2018

> [!Note]
> Meddelande om sekretessavtal: Följande ändringar håller på att utvecklas för Intune. Den här informationen har mycket begränsad spridning, i enlighet med sekretessavtalet. Sprid inte den här informationen vidare på sociala medier eller offentliga webbplatser som till exempel Twitter, UserVoice, Reddit och så vidare. 

Den **tidiga utgåvan** innehåller en lista med funktioner, som delas i enlighet med sekretessavtalet, som ingår i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte den här informationen på Twitter, UserVoice eller på något annat sätt med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1807 start -->

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Återställa lösenord för enheter från företagsportalappen för Windows 10 <!-- 2101282 --> 
Dina anställda kommer snart att kunna återställa sina enheters PIN-koder eller lösenord direkt från företagsportalappen för Windows 10. Den här funktionen blir tillgänglig både via fjärranslutningar till Intune-hanterade enheter och i lokala Intune-hanterade enheter som har stöd för lösenordsåterställning. Beroende på typen av enhet tar en begäran för en fjärransluten enhet bort enhetens aktuella lösenord eller skapar ett tillfälligt lösenord. Användare som begär en återställning för en lokal enhet dirigeras om till enhetens appinställningar.

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Använda S/MIME för att kryptera och signera en användares enheter <!-- 1333642 -->
En kommande uppdatering innehåller S/MIME-e-postkryptering som använder en ny importerad certifikatprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj plattformen > profiltypen **PKCS-importerat certifikat**). Du kan importera certifikat i PFX-format i Intune. Intune kan sedan leverera samma certifikat till flera enheter som registrerats av en enda användare. Detta omfattar även följande:

- Den interna e-postprofilen för iOS har stöd för att aktivera S/MIME-kryptering med importerade certifikat i PFX-format.
- Den interna e-postappen på Windows Phone 10-enheter använder S/MIME-certifikatet automatiskt.
- Det privata certifikatet kan levereras över flera plattformar. Men alla e-postappar har inte stöd för S/MIME.
- På andra plattformar kan du behöva konfigurera e-postappen manuellt för att aktivera S/MIME.  
- E-postappar som har stöd för S/MIME-kryptering kan hantera hämtning av certifikat för S/MIME-kryptering av e-post på ett sätt som MDM inte stöder, till exempel genom att läsa från utgivarens certifikatarkiv.

Stöds på: Windows, Windows Phone 10, macOS, iOS och Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Använda VPP enhetslicenser för att företablera företagsportalen vid DEP-registrering <!-- 1608345 -->
Du kan använda VPP-enhetslicenser (volymköpsprogram) för att företablera företagsportalen under registreringar med Programmet för enhetsregistrering (DEP). Detta gör du genom att ange den VPP-token som du vill använda för att installera företagsportalen när du skapar eller redigerar en registreringsprofil. Se till att din token inte upphör att gälla och att du har tillräckligt många licenser för företagsportalappen. Om token upphör att gälla eller om licenserna tar slut kan Intune push-överföra företagsportalen från App Store istället (då krävs ett Apple-ID).

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Massborttagning av enheter på enhetsbladet <!-- 1793693 -->
Du kommer att kunna ta bort flera enheter samtidigt på enhetsbladet. Välj **Enheter** > **Alla enheter** > välj de enheter som du vill ta bort > **Ta bort**. En avisering visas för enheter som inte kan tas bort.

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Ny enhetskonfigurationsprofil för Wi-Fi för Windows 10 och senare <!-- 1879077 -->
För närvarande kan du importera och exportera Wi-Fi-profiler med hjälp av XML-filer. Du kommer att kunna skapa en enhetskonfigurationsprofil för Wi-Fi direkt i Intune, precis som på vissa andra plattformar.

Om du vill skapa profilen öppnar du **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** > **Wi-Fi**. 

Gäller för Windows 10 och senare.

###  <a name="windows-line-of-business-lob-apps-file-extension-rename----1884873---"></a>Namnbyte på filnamnstillägg för verksamhetsspecifika appar (LOB) för Windows <!-- 1884873 -->
Filnamnstillägg för LOB-appar på Windows kommer att byta namn från *.appx* och *.appxbundle* till *.msix* och *.msixbundle*. Du kan lägga till en app i Microsoft Intune genom att välja **Mobilappar** > **Appar** > **Lägg till**. Fönstret **Lägg till app** visas och där du kan välja **Apptyp**. För LOB-appar på Windows väljer du **Verksamhetsspecifik app** som apptyp, väljer **Appaketfil** och anger sedan en installationsfil med rätt filnamnstillägg.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Konfigurationspaketet för Windows Defender ATP läggs automatiskt till i konfigurationsprofilen <!-- 2144658 -->
När du använder enheter med [Advanced Threat Protection och registrering](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) i Intune kan du för närvarande ladda ned ett konfigurationspaket och lägga till det i din konfigurationsprofil. I en kommande uppdatering hämtar Intune paketet automatiskt från Windows Defender Säkerhetscenter och lägger till det i din profil.

Gäller för Windows 10 och senare.

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Helskärmsläge – inaktuell är nedtonad och kan inte ändras <!-- 2149998 -->
Funktionen [Helskärmsläge](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10 och senare** > **Enhetsbegränsningar**) är inaktuell och ersätts med [Inställningar för helskärmsläge för Windows 10 och senare](kiosk-settings.md). Funktionen **Helskärmsläge – inaktuell** är nedtonad och användargränssnittet kan inte ändras eller uppdateras. 

Om du vill aktivera helskärmsläge kan du läsa mer i [Inställningar för helskärmsläge för Windows 10 och senare](kiosk-settings.md).

Gäller för Windows 10 och senare, Windows 10 Holographic for Business

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API:erna använder tredjeparts certifikatutfärdare <!-- 2184013 -->
Ett Java-API som gör det möjligt för tredjeparts certifikatutfärdare att integrera med Intune och SCEP kommer att finnas tillgängligt. Sedan kan användarna lägga till SCEP-certifikatet till en profil och tillämpa det på enheter med hjälp av MDM.

Intune stöder för närvarande [SCEP-förfrågningar med hjälp av Active Directory Certificate Services](certificates-scep-configure.md).

### <a name="check-for-sccm-compliance----2192052---"></a>Kontrollera SCCM-efterlevnad <!-- 2192052 -->
En kommande uppdatering innehåller en ny efterlevnadsinställning för System Center Configuration Manager (SCCM) (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Windows 10**). SCCM skickar signaler till Intunes efterlevnadsprinciper. Du kan kräva att alla SCCM-signaler returnerar ”kompatibel” med hjälp av Intune-inställningarna.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i SCCM. Om några program på enheten är i ett okänt tillstånd kommer enheten inte att vara kompatibel i Intune.

Gäller för Windows 10 och senare

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Aviseringar om utgående VPP-token eller om att kvarvarande licenser för företagsportalen håller på att ta slut <!-- 2237572 -->
Om du använder Volume Purchase Program (VPP) för att företablera företagsportalen vid DEP-registrering visas en varning i Intune när en VPP-token håller på att upphöra och när licenserna för företagsportalen nästan är slut.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Om du vill ta bort en VPP-token som används för företablering av företagsportalen krävs en bekräftelse <!-- 2237634 -->
En bekräftelse krävs för att ta bort en token för Volymköpsprogram (VPP) om den används för att företablera företagsportalen vid DEP-registrering.

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Markera automatiskt Android-enheter som registrerats med hjälp av Samsung Knox Mobile-registrering som ”företagsägda” <!-- 2404851 -->
Som standard kommer Android-enheter som registrerats med Samsung Knox Mobile-registrering markeras som **företagsägda** under **Ägarskap för enhet**. Du behöver inte identifiera företagets enheter manuellt med hjälp av IMEI- eller serienummer innan du registrerar med Samsung Knox Mobile-registrering.

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Växla för att visa eller dölja knappen Avsluta session i en webbläsare i helskärmsläge <!-- 2455253 -->
Du kommer att kunna konfigurera om webbläsare i helskärmsläge ska visa knappen Avsluta session. Du kan se kontrollen under **Enhetskonfiguration** > **Helskärmsläge (förhandsgranskning)** > **Webbläsare i helskärmsläge**. När en användare klickar på knappen när den är aktiverad frågar appen om du verkligen vill avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata och går tillbaka till den webbadress som är standard.

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Skapa en konfigurationsprofil för eSIM-mobilnät <!-- 2564077 -->
Du kommer att kunna skapa en profil för eSIM-mobilnät under **Enhetskonfiguration**. Du kan importera en fil som innehåller aktiveringskoder för mobilnät som tillhandahålls av din mobiloperatör. Du kan sedan distribuera de här profilerna till dina Windows 10-enheter som aktiverat eSIM LTE, till exempel Surface Pro LTE och andra eSIM-kompatibla enheter.

Kontrollera om dina [enheter stöder eSIM-profiler](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Gäller för Windows 10 och senare. 




<!-- 1806 start -->

### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Se enhetskonfigurationsprofiler som har konflikter <!-- 1556983 -->
En lista över de befintliga profilerna visas under **Enhetskonfiguration**. I och med den här uppdateringen läggs en ny kolumn till som innehåller information om profilerna som står i konflikt. Du kan välja en rad med en konflikt för att se inställningen och profilen som orsakar konflikten. 

Mer om [enhetskonfigurationsprofiler](device-profiles.md).

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

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Förhandsgranska en ny uppdatering av användarupplevelsen för företagsportalens webbsida <!--2000968 -->
Vi lägger till nya funktioner på företagsportalen/iOS-appkatalogen baserat på våra kunders synpunkter. Du kommer att se tydliga förbättringar av befintliga funktioner och användbarheten jämfört med dina Android-, iOS- och Windows-enheter. Delar av webbplatsen, som enhetsinformation, feedback och support samt enhetsöversikten, kommer att få en ny och modern design. Andra nyheter:

- Effektiva arbetsflöden mellan olika plattformar
- Bättre flöden för identifiering och registrering av enheter
- Fler användbara felmeddelanden
- Mer användarvänligt språk, mindre teknisk jargong
- Möjlighet att dela direktlänkar till appar
- Förbättrad prestanda för stora app-kataloger
- Bättre tillgänglighet för alla användare

Uppdateringen förhandsvisas just nu. Du kan registrera dig för att ta del av förhandsgranskningen på http://aka.ms/webcpflighting

### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Uppdateringar till meddelanden om brist på efterlevnad i företagsportalappen <!-- 1832222 -->
Vi uppdaterar meddelanden som användare ser när en enhet inte är kompatibel. Meddelandena behåller sina ursprungliga betydelser men kommer att uppdateras med mer användarvänligt språk och mindre teknisk jargong. Vi uppdaterar även länkar till dokumentation och reparationssteg för att hålla dem uppdaterade.  

Följande text är ett exempel på de förbättrade meddelandena som du kommer att se:  

Före: *Den här enheten har inte kontaktat Intune-tjänsten inom den tidsperiod som krävs av din IT-administratör. Du kan lösa det här problemet genom att öppna företagsportalappen på enheten och klicka på knappen Kontrollera efterlevnad.*  

Efter: *Din enhet har inte checkat in med organisationen på ett tag. Öppna företagsportalappen på enheten och tryck på Kontrollera inställningar för din enhet för att återetablera anslutningen*.  

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Redigera dina distributioner av Office 365 Pro Plus-appar <!-- 2150145 -->
Som Microsoft Intune-administratör kan du enklare redigera distributioner av Office 365 Pro Plus-appar. Gå till Azure Portal och välj **Microsoft Intune** > **Mobilappar** > **Appar**. Välj Office 365 Pro Plus Suite i listan med appar.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Radgranskning av dubbletter av uppladdade företagsenhets-id:n <!-- 2203794 -->
När du laddar upp företags-id:n så får du en lista med eventuella dubbletter i Intune, och du kan välja mellan att ta bort eller behålla den befintliga informationen. Rapporten visas om det finns dubbletter när du har valt **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till id:n**. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Lägga till företagsenhets-id:n manuellt <!-- 2203803 -->
Du kommer att kunna lägga till företagsenhets-id:n manuellt. Välj **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till**.

### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Ny status för enheter i enhetsefterlevnad <!-- 2308882 -->
Följande nya tillstånd läggs till i **Enhetskonfiguration** > **Principer** > välj en princip > **Översikt**:
- lyckades
- fel
- konflikt
- Väntar
- inte tillämpligt

En bild som visar antalet enheter på andra plattformar visas också. Om du till exempel tittar på en iOS-profil visas antalet enheter med andra system än iOS som också har tilldelats till den här profilen. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Enhetsefterlevnaden får stöd för antiviruslösningar från tredje part <!-- 2325484 -->
När du skapar en ny princip för enhetsefterlevnad (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Plattform: Windows 10 eller senare** > **Inställningar** > **Systemsäkerhet**) kommer några nya alternativ för **Enhetssäkerhet** att vara tillgängliga: 
- **Antivirus**: När **Kräv** är valt kan du kontrollera efterlevnad med antivirusprogram som är registrerade i Windows Security Center, som Symantec. 
- **Antispionprogram**: När **Kräv** är valt kan du kontrollera efterlevnad med antispionprogram som är registrerade i Windows Security Center, som Symantec. 

Gäller: Windows 10 och senare 

<!-- 1805 start -->

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

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Åtkomståtgärder för appskyddsprinciper <!-- 1483510 EEready -->
Du kommer snart att kunna konfigurera appskyddsprinciper för att uttryckligen rensa, blockera eller varna icke-kompatibla enheter. Den senaste åtgärden *Rensa* tar bort företagets företagsdata från en enhet. Om det uppstår en rensning meddelas enhetens användare om både orsaken för rensning och åtgärdsstegen. För vissa inställningar som lägsta version av operativsystemet, kommer du att kunna använda flera åtgärder, till exempel blockering och rensa. De här åtgärderna utlöses när appen startas.

<!-- 1804 start -->

### <a name="rules-for-removing-devices----1609459---"></a>Regler för att ta bort enheter <!-- 1609459 -->
Det kommer att finnas nya regler som gör att du automatiskt kan ta bort enheter som inte har checkats in under ett visst antal dagar som du anger. Om du vill se den nya regeln går du till fönstret **Intune**, väljer **Enheter** och sedan **Regler för borttagning av enheter**.

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