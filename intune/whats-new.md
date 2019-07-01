---
title: Nyheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Ta reda på vad som är nytt i Intune Azure-portalen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 756fafc02a6d64b1495a838ab8eee4130ee77361
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389341"
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune

Läs mer om varje veckas nyheter i Microsoft Intune. Du kan också hitta [viktiga meddelanden](#notices), [tidigare versioner](whats-new-archive.md) och information om [hur uppdateringar av Intune-tjänsten släpps](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> Varje [månadsuppdatering](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) kan ta upp till tre dagar att distribuera och sker i följande ordning:
> - Dag 1: Asien och stillahavsområdet
> - Dag 2: Europa, Mellanöstern och Afrika
> - Dag 3: Nordamerika
> 
> Vissa funktioner kan distribueras över flera veckor och kanske inte är tillgängliga för alla kunder den första veckan.
>
> Titta närmare på sidan [Under utveckling ](in-development.md) för en lista över kommande funktioner i en version.

**RSS-feed**: Håll dig informerad när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-june-17-2019"></a>Veckan som inleds med 17 juni 2019   

### <a name="app-management"></a>Apphantering

#### <a name="new-features-in-microsoft-intune-app"></a>Nya funktioner i Microsofts Intune-app
Vi har lagt till nya funktioner i Microsoft Intune-appen (förhandsversion) för Android. Användare på fullständigt hanterade Android-enheter kan nu  

* visa och hantera enheterna som de har registrerat genom Intune-företagsportalen eller Microsoft Intune-appen    
* kontakta sin organisation för support    
* skicka feedback till Microsoft    
* visa villkor och bestämmelser, om sådana har angetts av deras organisation.  

## <a name="week-of-june-10-2019"></a>Veckan som inleds med 10 juni 2019 

### <a name="app-management"></a>Apphantering  

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>Nya exempelappar som visar Intune SDK-integrering tillgänglig på GitHub <!-- 2653471 -->
GitHub-kontot msintuneappsdk har lagt till nya exempelprogram för iOS (Swift), Android, Xamarin.iOS, Xamarin Forms och Xamarin.Android. De här apparna är avsedda som komplement till vår befintliga dokumentation och visar hur du integrerar Intune APP SDK i dina egna mobilappar. Om du är apputvecklare och behöver ytterligare hjälp med Intune SDK hittar du fler exempel i de här länkarna:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) – en snabbmeddelandeapp för ursprungligt iOS-system (Swift) som använder Azure Active Directory Authentication Library (ADAL) för asynkron autentisering.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) – en att-göra-lista-app för ursprungligt Android-system som använder ADAL för asynkron autentisering.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) – en att-göra-lista-app för Xamarin.Android som använder ADAL för asynkron autentisering, den här lagringsplatsen har också Xamarin.Forms-appen.
- [Xamarin.iOS-exempelapp](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) – en Xamarin.iOS-exempelapp för barebonedatorer.

## <a name="week-of-may-27-2019"></a>Den vecka som börjar 27 maj 2019 

### <a name="app-management"></a>Apphantering

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Rapportering för potentiellt skadliga appar på Android-enheter <!-- 4223162 -->
Intune tillhandahåller nu ytterligare rapporteringsinformation om potentiellt skadliga appar på Android-enheter. 

## <a name="week-of-may-20-2019"></a>Den vecka som börjar 20 maj 2019 

### <a name="app-management"></a>Apphantering

#### <a name="windows-company-portal-app----3316993---"></a>Windows företagsportalapp <!-- 3316993 -->
Windows-företagsportalappen har nu en ny sida med etiketten **Enheter**. På sidan **Enheter** ser slutanvändare alla sina registrerade enheter. Användarna ser den här ändringen i företagsportalen när de använder version 10.3.4291.0 och senare. Mer information om hur du konfigurerar företagsportalen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](company-portal-app.md).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>OrderID-attributet på Autopilot-enheter har bytt namn till Grupptagg <!-- 4659453 -->

För att göra det mer intuitivt har **OrderID**-attributets namn på Autopilot-enheter ändrats till **Grupptagg**. När du använder CSV-filer för att ladda upp Autopilot-enhetsinformation måste du använda Grupptagg som kolumnrubrik, inte OrderID.  

## <a name="week-of-may-13-2019"></a>Den vecka som börjar 13 maj 2019 

### <a name="app-management"></a>Apphantering

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359-idready-wnready--"></a>Uppdatering av Intune-principers autentiseringsmetod och installation av företagsportalappen  <!-- 1927359 idready wnready-->
På enheter som redan har registrerats via Installationsassistenten med någon av Apples metoder för registrering av företagsenheter, stöder Intune inte längre företagsportalen om den installeras manuellt av slutanvändarna från App Store. Den här ändringen gäller endast när du autentiserar med Apple-installationsassistenten under registreringen. Den här ändringen påverkar också bara iOS-enheter som registrerats via:  
* Apple configurator

* Apple Business Manager

* Apple School Manager

* Apples program för enhetsregistrering (DEP)

Om användare installerar företagsportalappen från App store och sedan försöker att registrera enheterna genom den, får de ett felmeddelande. Dessa enheter kommer förväntas att bara använda företagsportalen när den har skickats automatiskt av Intune under registreringen. Profiler för registrering i Intune i Azure-portalen kommer att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Om du vill att dina DEP-enhetsanvändare ska ha företagsportalen behöver du ange dina preferenser i en registreringsprofil. 

Dessutom håller skärmen **Identifiera din enhet** i iOS-företagsportalen på att tas bort. Administratörer som vill aktivera villkorlig åtkomst eller distribuera företagsappar måste därför uppdatera profilen för DEP-registrering. Det här kravet gäller endast om DEP-registrering har verifierats med Installationsassistenten. I så fall måste du installera företagsportalen på enheten. För att göra det ska du välja **Intune** > **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram** > välja en token > **Profiler** > välja en profil > **Egenskaper** > och ställa in **Installera företagsportal** på **Ja**.

För att installera företagsportalen på redan registrerade DEP-enheter måste du gå till Intune > Klientappar och installera den som en hanterad app med konfigurationsprinciper för appar. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Konfigurera hur användarna uppdaterar en affärsapplikation (LOB)-app med hjälp av en appskyddsprincip <!-- 3568384 -->
Du kan nu konfigurera var användarna kan få en uppdaterad version av en affärsapplikation (LOB). Slutanvändarna ser den här funktionen i dialogen för villkorlig start **Lägsta appversion**, där slutanvändarna uppmanas att uppdatera till en lägsta version av LOB-appen. Du måste ange denna uppdateringsinformation som en del av din LOB-appskyddsprincip (APP). Den här funktionen är tillgänglig för iOS och Android. På iOS kräver den här funktionen att appen integreras (eller packas in med hjälp av programhanteringsverktyget) med Intune SDK för iOS v. 10.0.7 eller senare. På Android kräver funktionen den senaste företagsportalen. Om du vill konfigurera hur en slutanvändare uppdaterar en LOB-app behöver appen en hanterad appkonfigurationspolicy som skickas till den med nyckeln, `com.microsoft.intune.myappstore`. Det skickade värdet anger vilket lager som slutanvändaren laddar ner appen från. Om appen distribueras via företagsportalen måste värdet vara `CompanyPortal`. Du måste ange en fullständig URL för andra lager.

#### <a name="intune-management-extension-powershell-scripts-----3734186-idready---"></a>PowerShell-skript i Intune-hanteringstillägget  <!-- 3734186 idready -->
Du kan konfigurera PowerShell-skript så att det körs med användarens administratörsprivilegier på enheten. Mer information finns i [Använda PowerShell-skript på Windows 10-enheter i Intune](intune-management-extension.md) och [Win 32-apphantering](apps-win32-app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Apphantering med Android Enterprise <!-- 4459905 -->
Intune lägger automatiskt till fyra vanliga Android Enterprise-relaterade appar till Intune-administratörskonsolen för att göra det enklare för IT-administratörer att konfigurera och använda Android Enterprise-hantering. Detta är de fyra Android Enterprise-apparna:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – Används för fullständigt hanterade Android Enterprise-scenarier.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – Hjälper dig att logga in på dina konton om du använder tvåfaktorautentisering.
- **[Intune-företagsportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – Används för appskyddsprinciper och scenarier med Android Enterprise-arbetsprofiler.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) – Används för dedikerade/helskärmslägesscenarier i Android Enterprise.

Tidigare var IT-administratörer tvungna att hitta och godkänna de här apparna manuellt i den [hanterade Google Play-butiken](https://play.google.com/store/apps) som en del av konfigurationen. Den här ändringen tar bort de tidigare manuella stegen för att göra det enklare och snabbare för kunder att använda Android Enterprise-hantering.

Administratörer kommer att se att dessa fyra appar läggs till i listan över appar i Intune automatiskt när de ansluter Intune-klienten till hanterade Google Play för första gången. Läs [Anslut ditt Intune-konto till ditt hanterade Google Play-konto](connect-intune-android-enterprise.md) för mer information. Administratörer behöver inte göra något för klienter som redan har anslutit sin klient eller som redan använder Android Enterprise. De fyra apparna visas automatiskt inom sju dagar efter slutförandet av tjänstlanseringen under maj 2019.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>Uppdaterat PFX-certifikatanslutningsprogram för Microsoft Intune  <!-- 1533038 -->
Vi har släppt en uppdatering för [PFX-certifikatanslutningsappen för Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) som löser problemet där befintliga PFX-certifikat fortsätter att bearbetas, vilket orsakar att anslutningsappen slutar att bearbeta nya begäranden.

####  <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Intune-säkerhetsuppgifter för Defender ATP (i allmänt tillgänglig förhandsversion)     <!-- 3208597 -->
Du kan använda Intune för att hantera [säkerhetsuppgifter för Microsoft Defender Advanced Threat Protection (ATP) i den allmänt tillgängliga förhandsversionen](atp-manage-vulnerabilities.md). Det här möjliggör integrering med ATP och lägger till en riskbaserad metod för att identifiera, prioritera och åtgärda säkerhetsrisker och felkonfigurationer på slutpunkter, samtidigt som det minskar tiden mellan identifiering till problemlösning.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Söka efter en TPM-kretsuppsättning i en efterlevnadsprincip för Windows 10-enheter <!-- 3617671   idstaged-->
Många Windows 10-enheter och senare enheter har TPM-kretsuppsättningar (Trusted Platform Module). Den här uppdateringen innehåller en ny efterlevnadsinställning som kontrollerar versionen på TPM-chippet i enheten. 

[Inställningar för kompatibilitetsprinciper i Windows 10 och senare](compliance-policy-create-windows.md#device-security) beskriver den här inställningen.

Gäller för: Windows 10 och senare

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Förhindra slutanvändare från att ändra sin Internetdelning och inaktivera Siri-serverloggning på iOS-enheter <!-- 4097904   -->  
Du kan skapa en enhetsbegränsningsprofil på en iOS-enhet (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp). Den här uppdateringen innehåller nya inställningar som du kan konfigurera:

- **Inbyggda appar**: Loggning på serversidan av Siri kommandon
- **Trådlöst**: Användarmodifiering av internetdelning (endast övervakat)

Om du vill se de här inställningarna går du till [inbyggda app-inställningar för iOS](device-restrictions-ios.md#built-in-apps) och [trådlösa inställningar för iOS](device-restrictions-ios.md#wireless).

Gäller för: iOS 12.2 och senare

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Nya inställningar för enhetsbegränsning i appen Klassrum för macOS-enheter <!-- 4097905   --> 
Du kan skapa profiler för enhetskonfiguration för macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsbegränsningar** för profiltyp). Den här uppdateringen innehåller nya inställningar för appen Klassrum, alternativet att blockera skärmbilder och inaktivera iCloud-bildbiblioteket.

Gå till [macOS-enhetsinställningar för att tillåta eller begränsa funktioner med Intune](device-restrictions-macos.md) för att se de aktuella inställningarna.

Gäller för: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>iOS lösenordet för åtkomst till appbutiksinställningen har bytt namn<!-- 4557891  -->
Inställningen **Lösenord till appbutik** har bytt namn till **Kräv iTunes Store-lösenord för alla köp** (**Enhetskonfiguration**  >  **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel**).

Om du vill se de tillgängliga inställningarna går du till [iOS-inställningar för App Store, dokumentvisning, spel](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gäller för: iOS

####  <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Baslinjer för Microsoft Defender Advanced Threat Protection (Förhandsversion)  <!--  3754134 -->
Vi har lagt till en förhandsversion med säkerhetsbaslinje för [Microsoft Defender Advanced Threat Protection](security-baseline-settings-defender-atp.md)-inställningar. Denna baslinje finns tillgänglig när din miljö uppfyller förhandskraven för att använda [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Windows registreringsstatussida (ESP) är nu allmänt tillgänglig <!-- 3605348 -->
Registreringsstatussidan är inte längre en förhandsversion. Mer information finns i [Konfigurera en sida för registreringsstatus](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Uppdatering av användargränssnittet i Intune – Skapa Autopilot-registreringsprofil  <!-- 4593669 -->
Användargränssnittet för att skapa en Autopilot-profil för registrering har uppdaterats så att den överensstämmer med Azures användargränssnitt. Mer information finns i [Skapa en Autopilot-registreringsprofil](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile). Framöver kommer ytterligare Intune scenarier att uppdateras till det här nya användargränssnittet.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Aktivera Autopilot-återställning av alla Windows-enheter <!-- 4225665 -->
Autopilot-återställning fungerar nu för alla Windows-enheter, även de som inte har konfigurerats för att använda registreringsstatussidan. Om en registreringsstatussida inte har konfigurerats för enheten under den första enhetsregistreringen kommer enheten att gå direkt till skrivbordet efter inloggningen. Det kan ta upp till åtta timmar att synkroniseras och visas som kompatibel i Intune. Mer information finns i [Återställa enheter med fjärransluten Windows Autopilot-återställning](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Exakta IMEI-format krävs inte när du söker igenom alla enheter <!--30407680 -->
Du behöver inte ta med mellanslag i IMEI-nummer när du söker igenom **Alla enheter**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Om du tar bort en enhet i Apples portal visas ändringen även i Intune-portalen <!--2489996 -->
Om en enhet tas bort från Apples program för enhetsregistrering eller Apple Business Manager-portalen tas den även automatiskt bort från Intune vid nästa synkronisering.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>Registreringsstatussidan spårar nu Win32-appar <!-- 2714451 -->
Detta gäller endast enheter som kör Windows 10, version 1903 och senare. Mer information finns i [Konfigurera en sida för registreringsstatus](windows-enrollment-status.md).

### <a name="device-management"></a>Enhetshantering

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Återställa och rensa enheter i grupp med hjälp av Graph API <!-- 3295288 -->
Du kan nu återställa och rensa upp till 100 enheter i grupp med Graph API.


### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>Krypteringsrapport är inte längre en allmänt tillgänglig förhandsversion   <!-- 4587546      -->
[Rapporten för kryptering av BitLocker och enheter](encryption-monitor.md) är nu allmänt tillgänglig och inte längre en del av förhandsversionen. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Outlook-signatur och biometriska inställningar för iOS och Android-enheter <!-- 4050557 -->
Du kan nu ange om standardsignaturen är aktiverad i Outlook för iOS och Android-enheter. Dessutom kan du välja om du vill tillåta användare att ändra den biometriska inställningen i Outlook för iOS.

## <a name="week-of-may-6-2019"></a>Den vecka som börjar 6 maj 2019 

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>Stöd för Network Access Control (NAC) för F5 Access för iOS-enheter <!-- 4500808 -->

F5 släppte en uppdatering för BIG-IP-13 som tillåter NAC-funktioner för F5 Access på iOS i Intune. Gör så här för att använda funktionen:

- Uppdatera BIG-IP till 13.1.1.5. BIG-IP 14 stöds inte.
- Integrera BIG-IP med Intune för NAC. Stegen i [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html) (Översikt: Konfigurera APM för enhetsstatuskontroller med slutpunktshanteringssystem).
- Aktivera inställningen **Aktivera nätverksåtkomstkontroll** i VPN-profilen i Intune.

Om du vill se den tillgängliga inställningen går du till [Konfigurera VPN-inställningar på iOS-enheter](vpn-settings-ios.md).

Gäller för: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>Uppdaterat PFX-certifikatanslutningsprogram för Microsoft Intune <!-- doc-vso 1521237  -->  
Vi har släppt en uppdatering till [PFX-certifikatanslutningsappen för Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) som utelämnar avsökningsintervallet från 5 minuter till 30 sekunder.

## <a name="week-of-april-22-2019"></a>Den vecka som börjar 22 april 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Använd Compliance Manager för att skapa utvärderingar för Microsoft Intune<!-- 4404750 -->

[Compliance Manager](https://servicetrust.microsoft.com/ComplianceManager) (öppnar en annan Microsoft-webbplats) är ett verktyg för arbetsflödesbaserad riskbedömning i Microsoft Service Trust Portal. Det gör att du kan spåra, tilldela och verifiera din organisations aktiviteter för regelefterlevnad aktiviteter relaterade till Microsoft-tjänster. Du kan skapa din egen efterlevnadsbedömning med Office 365, Azure, Dynamics, Professionella tjänster och Intune. Intune har två utvärderingar – FFIEC och GDPR.

Compliance Manager hjälper dig att fokusera arbetet genom att dela in kontroller – kontroller som hanteras av Microsoft samt kontroller som hanteras av din organisation. Du kan slutföra utvärderingarna och sedan exportera och skriva ut dem.

Efterlevnad med [Federal Financial Institutions Examination Council (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (öppnar en annan Microsoft-webbplats) är en uppsättning standarder för onlinebanktjänster som utfärdas av FFIEC. Det är den mest efterfrågade utvärderingen för finansiella institutioner som använder Intune. Det tolkar hur Intune hjälper dem att uppfylla FFIEC-riktlinjer för cybersäkerhet relaterade till arbetsbelastningar med offentligt moln. Intunes FFIEC-utvärdering är den andra FFIEC-utvärderingen i Compliance Manager.

I följande exempel visas en analys av FFIEC-kontrollerna. Microsoft hanterar 64 kontroller. Du ansvarar för de återstående 12 kontrollerna.

![Se ett exempel på Intune-utvärdering för FFIEC, inklusive kundåtgärderna och Microsofts åtgärder](./media/intune-ffiec-assessment-status.png)

[Allmänna dataskyddsförordningen (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (öppnar en annan Microsoft-webbplats) är en EU-lag som hjälper till att skydda enskilda personers rättigheter och deras data. GDPR är mest efterfrågade utvärderingen för stöd med efterlevnad av sekretesskrav. 

I följande exempel visas en analys av GDPR-kontrollerna. Microsoft hanterar 49 kontroller. Du ansvarar för de återstående 66 kontrollerna.

![Se ett exempel på Intune-utvärdering för GDPR, inklusive kundåtgärderna och Microsofts åtgärder](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Den vecka som börjar 15 april 2019

### <a name="app-management"></a>Apphantering

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>OpenSSL-kryptering för Android-appskyddsprinciper <!-- 3747362 -->
Intune-appskyddsprinciper (APP) på Android-enheter använder nu ett OpenSSL-krypteringsbibliotek som är kompatibelt med FIPS 140-2. Mer information finns i avsnittet för [kryptering](app-protection-policy-settings-android.md#encryption) i [Inställningar för Android-appskyddsprinciper i Microsoft Intune](app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Aktivera Win32-appsamband <!-- 2617348  -->
Som administratör kan du kräva du att andra appar installeras som beroenden innan Win32-appen installeras. Mer specifikt måste enheten installera de beroende apparna innan den installerar Win32-appen. I Intune väljer du **Klientappar** > **Appar** > **Lägg till** för att visa bladet **Lägg till app**. Välj **Windows-app (Win32)** som **Apptyp**. När du har lagt till appen kan du välja **Beroenden** för att lägga till de beroende appar som måste installeras innan Win32-appen kan installeras. Mer information finns i [Fristående Intune – Win32-apphantering](apps-win32-app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Installationsinformation om appversion för Microsoft Store för företagsprogram <!-- 3537391   -->
Rapporter för appinstallation innehåller information om appversion för Microsoft Store för företagsprogram. I Intune väljer du **Klientappar** > **Appar**. Välj en **Microsoft Store för företag-app** och välj sedan **Installationsstatus för enhet** i avsnittet **Övervaka**.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Tillägg till reglerna för krav för Win32-appar <!-- 3676883   -->
Du kan skapa kravregler baserat på PowerShell-skript, registervärden och filsysteminformation. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **Windows-app (Win32)** som **Apptyp** på bladet **Lägg till app**.  Välj **Krav** > **Lägg till** för att konfigurera ytterligare kravregler. Sedan väljer du antingen **Filtyp**, **Register** eller **Skript** som **Typ av krav**. Mer information finns i [Win32-apphantering](apps-win32-app-management.md).

 #### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Konfigurera Win32-appar att installeras på Intune-registrerade Azure AD-anslutna enheter <!-- 3695227  -->
Du kan konfigurera Win32-appar att installeras på Intune-registrerade Azure AD-anslutna enheter. Mer information om Win32-appar i Intune finns i [Win32-apphantering](apps-win32-app-management.md).

#### <a name="device-overview-shows-primary-user---794259----"></a>Enhetsöversikt som visar primär användare <!--794259  -->
På sidan för enhetsöversikt visas den primära användaren, som även kallas användartillhörighetsanvändaren (UDA). Om du vill se den primära användaren för en enhet väljer du **Intune** > **Enheter** > **Alla enheter** > välj en enhet. Den primära användaren visas nästan längst upp på sidan **Översikt**.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Ytterligare rapportering för Managed Google Play-app för Android Enterprise-arbetsprofilenheter <!-- 4105925  -->
För Managed Google Play-appar som distribueras till Android Enterprise-arbetsprofilenheter kan du visa det specifika versionsnumret för den app som är installerad på en enhet. Det här gäller endast för obligatoriska appar.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>iOS-tangentbord från tredje part <!-- 4111843   -->
Stödet för Intunes appskyddsprincip (APP) för inställningen **Tangentbord från tredje part** för iOS kommer att tas bort på grund av en iOS-plattformsändring. Du kommer inte att kunna konfigurera den här inställningen i Intune-administratörskonsolen och den kommer inte att tillämpas på klienten i Intune App SDK.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Ange inställningarna för inloggning och kontrollera omstartsalternativ på macOS-enheter <!-- 1210083  -->
På macOS-enheter kan du skapa en profil för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **macOS** för plattformen > **Enhetsfunktioner** för profiltypen). Den här uppdateringen innehåller nya inställningar för inloggningsfönstret, till exempel att visa en anpassad banderoll, ändra hur användare loggar in, visa eller dölja energiinställningarna och mer.

Om du vill se de här inställningarna går du till [inställningarna för iOS-enhetsfunktioner](macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Konfigurera Wi-Fi på enhetsägardedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar <!--3041940  -->
Du kan aktivera inställningar på Android Enterprise-enhetsägarenheter när de körs som dedikerade enheter i helskärmsläge för flera appar. I den här uppdateringen kan du ge användare möjlighet att konfigurera och ansluta till Wi-Fi-nätverk (**Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetens ägare, Enhetsbegränsningar** för profiltyp > **Dedikerade enheter** > **Helskärmsläge**: **Flera appar** > **WiFi-konfiguration**). 

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](device-restrictions-android-for-work.md).

Gäller för: Dedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Konfigurera Bluetooth och parkoppling på enhetsägardedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar <!-- 3041941  -->
Du kan aktivera inställningar på Android Enterprise-enhetsägarenheter när de körs som dedikerade enheter i helskärmsläge för flera appar. I den här uppdateringen kan du tillåta slutanvändare att aktivera Bluetooth och parkoppla enheter via Bluetooth (**Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetens ägare, Enhetsbegränsningar** för profiltyp > **Dedikerade enheter** > **Helskärmsläge**: **Flera appar** > **Bluetooth-konfiguration**). 

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](device-restrictions-android-for-work.md).

Gäller för: Dedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Skapa och använda OEMConfig-profiler för enhetskonfiguration i Intune <!-- 3305883  -->
I den här uppdateringen stöder Intune konfiguration av Android Enterprise-enheter med OEMConfig. Mer specifikt kan du kan skapa en profil för enhetskonfiguration och använda inställningar för Android Enterprise-enheter med hjälp av OEMConfig (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform).

Stöd för OEM-tillverkare sker för närvarande per varje enskild OEM. Om en OEMConfig-app som du vill ha inte finns i listan över OEMConfig-appar kan du kontakta `IntuneOEMConfig@microsoft.com`.

Om du vill veta mer om den här funktionen kan du gå till [Använda och hantera Android Enterprise-enheter med OEMConfig i Microsoft Intune](android-oem-configuration-overview.md).

Gäller för: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows Update-meddelanden  <!-- 3316758, 3316782  -->
Vi har lagt till två *inställningar för användarupplevelse* i de konfigurationer av Windows Update-uppdateringsring som du kan hantera från Intune-konsolen. Nu kan du:
- Blockera eller tillåta användare att [söka efter Windows-uppdateringar](windows-update-settings.md#block-user-from-scanning-for-windows-updates).
- Hantera den [Windows Update-meddelandenivå](windows-update-settings.md#windows-update-notification-level) som användarna ser.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Nya inställningar för enhetsbegränsningar för enhetsägarbaserad Android Enterprise <!-- 3574254  -->
På Android Enterprise-enheter kan du skapa en profil för enhetsbegränsningar för att tillåta eller begränsa funktion, ange lösenordsregler och mer (**Enhetskonfiguration** > **Profiler** > **Skaoa profil** > välj **Android Enterprise** för plattform > **Endast enhetsägare > Enhetsbegränsningar** för profiltyp). 

Den här uppdateringen innehåller nya lösenordsinställningar, ger fullständig åtkomst till appar i Google Play Store för fullständigt hanterade enheter och mer. Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](device-restrictions-android-for-work.md). 

Gäller för: Fullständigt hanterade Android Enterprise-enheter

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Söka efter en TPM-kretsuppsättning i en efterlevnadsprincip för Windows 10-enheter <!-- 3617671 -->

Den här funktionen är försenad och planeras att släppas senare.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Uppdaterade ändringar av användargränssnittet för webbläsaren Microsoft Edge på enheter med Windows 10 och senare <!-- 3775833   -->
När du skapar en profil för enhetskonfiguration kan du tillåta eller begränsa Microsoft Edge-funktioner på enheter med Windows 10 och senare (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp >  **Microsoft Edge-webbläsaren**). I den här uppdateringen beskrivs Microsoft Edge-inställningar mer utförligt och är enklare att förstå. 

Om du vill se de här funktionerna går du till [inställningarna för enhetsbegränsningar i Microsoft Edge-webbläsaren](device-restrictions-windows-10.md#microsoft-edge-browser).

Gäller för: Windows 10 och senare

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Utökat stöd för fullständigt hanterade Android Enterprise-enheter (förhandsversion)  <!--   3903241, 3903244, 3903246   -->
Fullständigt hanterade Android Enterprise-enheter ([som först tillkännagavs i januari 2019](whats-new.md#week-of-january-14-2019) är fortfarande i offentlig förhandsversion, men vi har utökat stödet för dem till att omfatta följande: 

- På fullständigt hanterade och dedikerade enheter kan du skapa [efterlevnadsprinciper](compliance-policy-create-android-for-work.md) till att omfatta lösenordsregler och operativsystemkrav (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Android Enterprise** för plattform > **Enhetsägare** för profiltyp). 

  På dedikerade enheter kan enheten visas som **Inte kompatibel**. Villkorlig åtkomst är inte tillgängligt på dedikerade enheter. Se till att slutföra alla uppgifter eller åtgärder för att göra så att dedikerade enheter uppfyller dina tilldelade principer.

- [Villkorlig åtkomst](conditional-access.md) – principer för villkorlig åtkomst som gäller för Android gäller även för fullständigt hanterade Android Enterprise-enheter. Användare kan nu registrera sina fullständigt hanterade enheter i Azure Active Directory med hjälp av **Microsoft Intune-appen**. Sedan undersöker och åtgärdar du eventuella efterlevnadsproblem för att få åtkomst till organisationens resurser.

- Ny app för slutanvändare (Microsoft Intune-appen) – det finns en ny app för slutanvändare för fullständigt hanterade Android-enheter som heter **Microsoft Intune**. Den här nya appen är enkel och modern. Den har funktioner som liknar företagsportalappen men för fullständigt hanterade enheter. Mer information finns i [Microsoft Intune-appen på Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

För att konfigurera fullständigt hanterade Android-enheter, gå till **Enhetsregistrering** > **Android-registrering** > **Företagsägda, fullständigt hanterade användarenheter**. Stöd för fullständigt hanterade Android-enheter är fortfarande i förhandsversion, och vissa Intune-funktioner är kanske inte helt funktionella.  

Mer information om den här förhandsversionen finns på vår blogg, [Microsoft Intune – förhandsversion 2 för fullständigt hanterade Android Enterprise-enheter](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>Konfigurera profilen om du vill hoppa över vissa av skärmarna i installationsassistenten <!-- 2276470  wnstaged-->
När du skapar en macOS-registreringsprofil kan du konfigurera den till att hoppa över valfria följande skärmar när en användare går igenom installationsassistenten:
- Utseende
- Visningston
- iCloudStorage Om du skapar en ny profil eller redigerar en profil måste den valda överhoppningsskärmen synkroniseras med Apple MDM-servern.  Användare kan utfärda en manuell synkronisering av enheterna så att det inte sker någon fördröjning i att plocka upp profiländringarna.
Mer information finns i [Registrera macOS-enheter automatiskt med programmet för enhetsregistrering eller Apple School Manager](device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Massnamngivning av enheter vid registrering av iOS-företagsenheter<!--3566569  -->
Vid användning av någon av Apples metoder för företagsregistrering (DEP/ABM/ASM) kan du ange ett format för enhetsnamn till att automatiskt namnge inkommande iOS-enheter. Du kan ange ett format som innehåller enhetstyp och serienummer i mallen. Om du vill göra det väljer du **Intune** > **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtoken** > **Välj en token** >**Skapa profil** > **Format för enhetsnamngivning**. Du kan redigera befintliga profiler, men namnet tillämpas endast på nyligen synkroniserade enheter.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Uppdaterat standardmeddelande för tidsgräns på sidan Registreringsstatus <!-- 3959331 -->
Vi har uppdaterat det standardmeddelande för tidsgräns som användare ser när sidan Registreringsstatus (ESP, Enrollment Status Page) överskrider det tidsgränsvärde som angetts i ESP-profilen. Det nya standardmeddelandet är det som användarna ser. Det hjälper dem att ta reda på vilka åtgärder som därnäst ska vidtas med deras ESP-distribution.  

### <a name="device-management"></a>Enhetshantering

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Ta icke-kompatibla enheter ur bruk  <!-- 1827291   -->
Den här funktionen har försenats och kommer i en framtida version.


### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Ändringar i Intune Data Warehouse V1.0 återspeglas i betaversionen <!-- 4403765 -->
När V1.0 introducerades i 1808 skiljde den sig från beta-API:et på några betydande sätt. I 1903 återspeglas ändringarna tillbaka till beta-API-versionen. Om du har viktiga rapporter som använder beta-API-versionen rekommenderar vi starkt att du växlar de rapporterna till V1.0 för att undvika icke-bakåtkompatibla ändringar. Mer information finns i [ändringsloggen för Intune Data Warehouse API](reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Övervaka status för säkerhetsbaslinje (offentlig förhandsversion) <!-- 3082047 --> 
Vi har lagt till en [per kategori-vy](security-baselines-monitor.md#per-category-view) i övervakningen av säkerhetsbaslinjer. (Säkerhetsbaslinjer är fortfarande i förhandsversion). Per kategori-vyn visar varje kategori från baslinjen tillsammans med procentandelen enheter som hamnar i varje statusgrupp för respektive kategori. Nu kan du se hur många enheter som inte matchar de enskilda kategorierna, är felkonfigurerade eller inte kan användas.

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Omfångstaggar för Apple VPP-token <!--2371886  -->
Du kan nu lägga till omfångstaggar till Apple VPP-token. Endast användare som har tilldelats med samma omfångstagg får åtkomst till Apple VPP-token med den taggen. VPP-appar och e-böcker som köpts med den token ärver dess omfångstaggar. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Den vecka som börjar 1 april 2019

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Uppdaterade certifikatanslutningsappar  <!-- ICM 113304612 -->
Vi har släppt uppdateringar för både [Intune-certifikatanslutningsappen och PFX-certifikatanslutningsappen för Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors). De nya versionerna åtgärdar flera kända problem.  

### <a name="app-management"></a>Apphantering

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Uppdatering av användarupplevelsen för företagsportalappen för iOS <!-- 2536024 -->
Startsidan för företagsportalappen för iOS-enheter har fått en ny design. Med den här ändringen följer startsidan mönstren för iOS-användargränssnitt på ett bättre sätt och gör dessutom appar och e-böcker mer lätthittade.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Ändringar i företagsportalregistrering för iOS 12-enhetsanvändare <!--3448635 -->  
Registreringsskärmarna och stegen för företagsportalen för iOS har uppdaterats så att de överensstämmer med de ändringar av MDM-registrering som lanserades i Apple iOS 12.2. Det uppdaterade arbetsflödet uppmanar användaren att:  

* Tillåta att Safari öppnar webbplatsen för företagsportalen och laddar ned hanteringsprofilen innan den går tillbaka till företagsportalappen.  
* Öppna inställningsappen för att installera hanteringsprofilen på enheten.
* Gå tillbaka till företagsportalappen för att slutföra registreringen.  

Uppdaterade steg och skärmar för registrering finns i avsnittet om att [registrera iOS-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>Den vecka som börjar 25 mars 2019

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Stöd för Power BI-efterlevnadsapp från Data Warehouse-bladet i Microsoft Intune <!-- 4260871 -->
Tidigare laddade länken **Ladda ned Power BI-fil** på bladet **Intune Data Warehouse** ned en Intune Data Warehouse-rapport (.pbix-fil). Den här rapporten har ersatts med Power BI-efterlevnadsappen. Power BI-efterlevnadsappen kräver inte någon särskild inläsning eller konfiguration. Den öppnas direkt i Power BI-onlineportalen och visar data specifikt för din Intune-klientorganisation baserat på dina autentiseringsuppgifter. I Intune väljer du länken **Konfigurera Intune Data Warehouse** på höger sida av Intune-bladet. Klicka sedan på **Hämta Power BI-appen**. Mer information finns i [Ansluta till Data Warehouse med Power BI](reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Den vecka som börjar 18 mars 2019

### <a name="app-management"></a>Apphantering

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Distribuera Microsoft Visio och Microsoft Project <!-- 3725386  -->
Du kan nu distribuera Microsoft Visio Pro för Office 365 och skrivbordsklienten för Microsoft Project Online som oberoende appar till Windows 10-enheter som använder Microsoft Intune om du har licenser för dessa appar. I Intune väljer du **Klientappar** > **Appar** > **Lägg till** för att visa bladet **Lägg till app**. På bladet **Lägg till app** väljer du **Windows 10** som **Apptyp**. Välj sedan **Konfigurera appsvit** för att välja appar som ska installeras. Mer information om Office 365-appar för Windows 10-enheter finns i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Ändring av produktnamn för Microsoft Visio Pro för Office 365 <!-- 3593653  -->
**Microsoft Visio Pro för Office 365** kommer nu att kallas **Microsoft Visio Online, abonnemang 2**.  Mer information om Microsoft Visio finns i [Visio Online, abonnemang 2](https://products.office.com/visio/visio-online-plan-2). Mer information om Office 365-appar för Windows 10-enheter finns i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Inställning för teckengräns för Intune-appskyddsprincip (APP) <!-- 3291302  -->
Intune-administratörer kan ange ett undantag till principinställningen **Begränsa klipp ut, kopiera och klistra in med andra appar** för Intune APP.  Som administratör kan du ange det antal tecken som kan klippas ut eller kopieras från en hanterad app. Den här inställningen tillåter delning av det angivna antalet tecken till valfri app oavsett inställningen ”Begränsa klipp ut, kopiera och klistra in med andra appar”. Observera att versionen av Intune-företagsportalappen för Android kräver version 5.0.4364.0 eller senare. Mer information finns i [iOS-dataskydd](app-protection-policy-settings-ios.md#data-protection), [Android-dataskydd](app-protection-policy-settings-android.md#data-protection) och [Granska loggarna för klientappskydd](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>ODT-XML (Distributionsverktyg för Office) för Office ProPlus-distribution <!-- 3192477   -->
Du kommer att kunna tillhandahålla ODT-XML (Distributionsverktyg för Office) när du skapar en instans av Office Pro Plus i Intune-administratörskonsolen. Detta ger större anpassningsbarhet om de befintliga alternativen för användargränssnittet i Intune inte uppfyller dina behov. Mer information finns i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](https://docs.microsoft.com/intune/apps-add-office365) och [Konfigurationsalternativ för distributionsverktyget för Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Appikoner visas nu med en automatiskt genererad bakgrund <!-- 1429026  -->
I Windows-företagsportalappen visas appikoner nu med en automatiskt genererad bakgrund som baseras på ikonens huvudsakliga färg (om den kan identifieras). När så är tillämpligt ersätter den här bakgrunden den grå kantlinje som tidigare fanns på appanelerna. Användarna ser den här ändringen i versioner senare än 10.3.3451.0 av företagsportalen.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Installera tillgängliga appar med hjälp av företagsportalappen efter massregistrering för Windows <!-- 2751523   -->
Windows-enheter som registreras till Intune med hjälp av [massregistrering för Windows](windows-bulk-enroll.md) (etableringspaket) kommer att kunna använda företagsportalappen för att installera tillgängliga appar. Mer information om företagsportalappen finns i [Lägga till Windows 10-företagsportalen manuellt](store-apps-company-portal-app.md) och [Så konfigurerar du Microsoft Intune-företagsportalappen](company-portal-app.md).

> [!Note]
> Den här funktionen har ännu inte distribuerats fullständigt till alla kunder. Om du inte kan använda företagsportalen på massregistrerade enheter behöver du kanske vänta tills den här ändringen distribueras till ditt konto.

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Microsoft Teams-appen kan väljas som en del av Office-appsviten <!-- 3828932  -->
Microsoft Teams-appen kan inkluderas eller uteslutas som en del av installationen av Office Pro Plus-appsviten. Den här funktionen fungerar för Office Pro Plus, build-nummer 16.0.11328.20116+. Användaren måste logga ut och sedan logga in på enheten för att slutföra installationen. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. Välj en av **Office 365-svitapptyperna** och välj sedan **Konfigurera appsvit**.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Starta en app automatiskt när flera appar körs i helskärmsläge på enheter med Windows 10 och senare <!-- 2351390 -->

På enheter med Windows 10 och senare kan du köra en enhet i helskärmsläge och köra många appar. I den här uppdateringen finns en **AutoLaunch**-inställning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Helskärmsläge** för profiltyp > **Helskärmsläge för flera appar**). Använd den här inställningen för att starta en app automatiskt när användaren loggar in på enheten.

En lista och beskrivningar av alla inställningar för helskärmsläge finns i [Inställningar för enheter med Windows 10 (och senare) som ska köras med helskärmsläge i Intune](kiosk-settings-windows.md).

Gäller för: Windows 10 och senare

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Arbetsloggar visar även information om icke-kompatibla enheter <!-- 4063755  -->
När Intune-loggar dirigeras till Azure Monitor-funktioner kan du även dirigera arbetsloggarna. I den här uppdateringen ger arbetsloggarna även information om icke-kompatibla enheter. 

Mer information om den här funktionen finns i [Skicka loggdata till lagring, händelsehubbar eller logganalys i Intune](review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Dirigera loggar till Azure Monitor i fler Intune-arbetsbelastningar <!-- 3804627 -->
I Intune kan du dirigera granskningsloggar och arbetsloggar till händelsehubbar, lagring och logganalys i Azure Monitor (**Intune** > **Övervakning** > **Diagnostikinställningar**). I den här uppdateringen kan du dirigera loggarna i fler Intune-arbetsbelastningar, däribland efterlevnad, konfigurationer, klientappar och mer. 

Mer information om dirigering av loggar till Azure Monitor finns i [skicka data till lagring, händelsehubbar eller logganalys](review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Skapa och använda mobilitetstillägg på Android Zebra-enheter i Intune <!-- 3305880   -->
I den här uppdateringen stöder Intune konfiguration av Android Zebra-enheter. Mer specifikt kan du skapa en profil för enhetskonfiguration och tillämpa inställningar på Android Zebra enheter med hjälp av MX-profiler (Mobility Extensions) som genereras av StageNow (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android** för plattform > **MX-profil (endast Zebra)** för profiltyp).

Mer information om den här funktionen finns i [Använd och hantera Zebra-enheter med mobilitetstillägg i Intune](android-zebra-mx-overview.md).

Gäller för: Android

### <a name="device-management"></a>Enhetshantering

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Krypteringsrapport för Windows 10-enheter (i allmänt tillgänglig förhandsversion)<!-- 2351538 -->  
Använd den nya [krypteringsrapporten (förhandsversion)](encryption-monitor.md) till att visa information om krypteringsstatusen för dina Windows 10-enheter. Bland den tillgängliga informationen finns en enhets TPM-version, krypteringsberedskap och -status, felrapportering och mer.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Använd BitLocker-återställningsnycklar från Intune-portalen (i allmänt tillgänglig förhandsversion) <!-- 2351547   -->  
Du kan nu använda Intune för att [visa information](encryption-monitor.md) om BitLocker-nyckel-ID och BitLocker-återställningsnycklar från Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge-stöd för Intune-scenarier i iOS-enheter och Android-enheter <!-- 3411007 -->
Microsoft Edge kommer att stödja samma hanteringsscenarier som Intune Managed Browser samt förbättringar av användarupplevelsen. Microsoft Edge Enterprise-funktioner som aktiveras av Intune-principer inbegriper dubbel identitet, integrering med appskyddsprincip, integrering av Azure-programproxy samt hanterade favoriter och genvägar för startsidan. Mer information finns i [Microsoft Edge-support](app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Inaktuellt stöd för enheter med endast EAS för Exchange Online/Intune-anslutningsapp <!--3105122  -->
Intune-konsolen stöder inte längre visning och hantering av enheter med endast EAS som är anslutna till Exchange Online med Intune-anslutningsappen. I stället har du följande alternativ:
- Registrera enheter i hantering av mobilenheter (MDM)
- Använd Intunes appskyddsprinciper för att hantera dina enheter
- Använd Exchange-kontrollerna enligt beskrivningen i [Klienter och mobilt i Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Söka efter en exakt enhet med [namn] på sidan Alla enheter <!--4254930 -->
Du kan nu söka efter ett exakt enhetsnamn. Gå till **Intune** > **Enheter** > **Alla enheter** > i sökrutan omger du enhetsnamnet med {} för att söka efter en exakt matchning. Det kan till exempel vara **{Enhet12345}** .

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Stöd för ytterligare anslutningsappar på sidan Status för klientorganisation <!-- 3617202  -->
[Sidan Status för klientorganisation](tenant-status.md) visar nu statusinformation för ytterligare anslutningsappar, däribland *Windows Defender Advanced Threat Protection* (ATP) och andra Mobile Threat Defense-anslutningsappar.

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Bevilja Intune skrivskyddad åtkomst till vissa Azure Active Directory-roller <!-- 3637917  -->
Skrivskyddad åtkomst för Intune har givits till följande Azure AD-roller. Behörigheter som beviljas med Azure AD-roller ersätter behörigheter som beviljas med rollbaserad åtkomstkontroll (RBAC) för Intune.

Skrivskyddad åtkomst till Intune-granskningsdata:

- Efterlevnadsadministratör
- Efterlevnadsdataadministratör

Skrivskyddad åtkomst till alla Intune-data:

- Säkerhetsadministratör
- Säkerhetsoperatör
- Säkerhetsläsare

Mer information finns i [Rollbaserad åtkomstkontroll](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Omfångstaggar för iOS-appetableringsprofiler <!--2934430   -->
Du kan lägga till en omfångstagg till en iOS-appetableringsprofil så att endast personer med roller som också tilldelats den omfångstaggen har åtkomst till iOS-appetableringsprofilen. Mer information finns i [Använda RBAC och omfångstaggar](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Omfångstaggar för appkonfigurationsprinciper <!--2371891   -->
Du kan lägga till en omfångstagg till en appkonfigurationsprincip så att endast personer med roller som också tilldelats den omfångstaggen har åtkomst till appkonfigurationsprincipen. Appkonfigurationsprincipen kan endast riktas till eller associeras med appar som har tilldelats samma omfångstagg. Mer information finns i [Använda RBAC och omfångstaggar](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge-stöd för Intune-scenarier i iOS-enheter och Android-enheter <!-- 3411007 -->
Microsoft Edge kommer att stödja samma hanteringsscenarier som Intune Managed Browser samt förbättringar av användarupplevelsen. Microsoft Edge Enterprise-funktioner som aktiveras av Intune-principer inbegriper dubbel identitet, integrering med appskyddsprincip, integrering av Azure-programproxy samt hanterade favoriter och genvägar för startsidan. Mer information finns i [Microsoft Edge-support](app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Den vecka som börjar 25 februari 2019

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell-modul <!-- 951068  -->
Intune PowerShell-modulen, som ger stöd för Intune-API:et via Microsoft Graph, är nu tillgänglig i [Microsoft PowerShell-galleriet](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Information om hur du använder den här modulen](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Scenarioexempel där den här modulen används](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Förbättrat stöd för leveransoptimering  <!--3183757  -->
Vi har utökat stödet i Intune för konfiguration av leveransoptimering. Du kan nu konfigurera en utökad lista över [inställningar för leveransoptimering](delivery-optimization-settings.md) och rikta den till dina enheter direkt från Intune-konsolen.


## <a name="week-of-february-18-2019"></a>Den vecka som börjar 18 februari 2019

### <a name="app-management"></a>Apphantering

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune använder Google Play Protect-API:er på Android-enheter <!-- 2577355   -->
Vissa IT-administratörer hanterar en BYOD-miljö där slutanvändare kan rota eller jailbreaka sin mobiltelefon. Även om beteendet inte är illa menat blir resultatet att det kringgår många Intune-principer som har angetts för att skydda organisationens data och slutanvändarenheter. Därför har Intune rot- och jailbreak-identifiering för både registrerade och oregistrerade enheter. Med den här versionen använder Intune nu Google Play Protect-API:er som tillägg till våra befintliga rotidentifieringskontroller för oregistrerade enheter. Google delar inte alla rotidentifieringskontroller som sker men vi förväntar oss att dessa API:er kan identifiera användare som har rotat sina enheter av någon anledning från enhetsanpassning för att kunna få nyare OS-uppdateringar på äldre enheter. Dessa användare kan sedan blockeras från åtkomst till företagsdata eller så kan deras företagskonton rensas bort från deras principaktiverade appar. Ett ytterligare mervärde är att IT-administratören nu har flera rapporteringsuppdateringar på bladet Intune-appskydd – rapporten ”Flaggade användare” visar vilka användare som identifieras via SafetyNet API-genomsökningen från Google Play Protect, rapporten ”Potentiellt skadliga appar” visar vilka appar som identifieras via Googles Verify Apps API-genomsökning. Den här funktionen är tillgänglig på Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Win32-appinformation tillgänglig på bladet Felsökning <!-- 2617342   -->
Du kan nu samla in felloggfiler för en Win32-appinstallation från Intune-appens blad **Felsökning**. Mer information om felsökning av appinstallationer finns i [Felsöka appinstallationsproblem](troubleshoot-app-install.md) och [Felsöka problem med Win32-appar](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Appstatusinformation för iOS-appar <!-- 3761235   -->
Det finns nya felmeddelanden för appinstallationer som rör följande:
- Fel för VPP-appar vid installation på delad iPad
- Fel när App Store är inaktiverad
- Fel vid sökning efter VPP-licensen för appen
- Fel vid installation av systemappar med MDM-provider
- Fel vid installation av appar när enheten är i borttappat läge eller helskärmsläge
- Fel vid installation av app när användaren inte är inloggad i App Store

I Intune väljer du **Klientappar** > **Appar** > ”appens namn” > **Installationsstatus för enhet**. Nya felmeddelanden kommer att finnas i kolumnen **Statusinformation**.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Nya ny skärm för appkategorier i företagsportalappen för Windows 10<!-- 3834780  -->
En ny skärm som heter **Appkategorier** har lagts till i syfte att förbättra upplevelsen för bläddring och val av appar i företagsportalen för Windows 10. Användarna ser nu sina appar sorterade i kategorier som **Aktuella**, **Utbildning** och **Produktivitet**. Den här ändringen finns i versioner 10.3.3451.0 och senare av företagsportalen. Om du vill se den nya skärmen går du till [Nyheter i användargränssnittet för appen](https://docs.microsoft.com/intune/whats-new-app-ui). Mer information om appar i företagsportalen finns i [Installera och dela appar på din enhet](/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI-efterlevnadsapp <!-- 1455231 doc-work-item -->
Få åtkomst till ditt Intune-informationslager i Power BI Online med hjälp av [Intune-efterlevnadsappen (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Med den här Power BI-appen kan du nu komma åt och dela i förväg skapade rapporter utan någon konfiguration och utan att lämna webbläsaren. Mer information finns i [Ändringslogg – Power BI-efterlevnadsapp](reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>PowerShell-skript kan köras på en 64-bitarsvärd på 64-bitarsenheter <!-- 1862675   -->
När du lägger till ett PowerShell-skript i en enhetskonfigurationsprofil körs skriptet alltid i 32 bitar, även på 64-bitars operativsystem. Med den här uppdateringen kan en administratör köra skriptet på en 64-bitars PowerShell-värd på 64-bitarsenheter (**Enhetskonfiguration** > **PowerShell-skript** > **Lägg till** > **Konfigurera** > **Kör skript i 64-bitars PowerShell-värd**).

Mer information om användning av PowerShell finns i [PowerShell-skript i Intune](intune-management-extension.md).

Gäller för: Windows 10 och senare

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>macOS-användare uppmanas att uppdatera sitt lösenord <!-- 1873216 -->
Intune framtvingar inställningen **ChangeAtNextAuth** på macOS-enheter. Den här inställningen påverkar slutanvändare och enheter som har efterlevnadsprinciper för lösenord eller lösenordsprofiler för enhetsbegränsning. Slutanvändare uppmanas en gång att uppdatera sitt lösenord. Den här uppmaningen sker när en användare för första gången kör en uppgift som kräver autentisering, till exempel inloggning på enheten. Användare kan även uppmanas att uppdatera sitt lösenord när de gör något som kräver administratörsprivilegier, till exempel att begära nyckelringsåtkomst. 

Eventuella nya eller befintliga ändringar av lösenordsprinciper av administratören gör att användarna återigen uppmanas att uppdatera lösenordet.

Gäller för:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>Tilldela SCEP-certifikat till en användarlös macOS-enhet  <!-- 2340521  -->
Du kan tilldela SCEP-certifikat (Simple Certificate Enrollment Protocol ) med hjälp av enhetsattribut till macOS-enheter, inklusive enheter utan användartillhörighet, och koppla certifikatprofilen till Wi-Fi- eller VPN-profiler. Detta utökar det stöd som vi redan har för att [tilldela SCEP-certifikat till enheter med och utan användartillhörighet](certificates-scep-configure.md#create-a-scep-certificate-profile) som kör Windows, iOS eller Android.  Den här uppdateringen lägger till alternativet att välja certifikattypen *Enhet* när du konfigurerar en SCEP-certifikatprofil för macOS.

Gäller för: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Uppdatering av användargränssnittet i Intune för villkorlig åtkomst   <!-- 2432313   -->
Vi har gjort förbättringar av användargränssnittet för villkorlig åtkomst i Intune-konsolen. Dessa omfattar:
-  Intune-bladet *Villkorlig åtkomst* har ersatts med bladet från Azure Active Directory. På så sätt har du åtkomst till alla inställningar och konfigurationer för [villkorlig åtkomst](conditional-access.md) (som fortfarande är en Microsoft Azure AD-teknik) från Intune-konsolen. 
- Vi har bytt namn bladet *Lokal åtkomst* till *Exchange-åtkomst* och flyttat konfigurationen av *Exchange-tjänstens anslutningsapp* till det här bladet med nytt namn.  Ändringen konsoliderar det ställe där du [konfigurerar och övervakar information relaterad till onlinebaserad och lokal Exchange](exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Apparna Kiosk Browser och Microsoft Edge-webbläsaren kan köras på Windows 10-enheter i helskärmsläge <!-- 2935135   -->
Du kan använda Windows 10-enheter i helskärmsläge för att köra en app eller många appar. Den här uppdateringen omfattar flera ändringar av att använda webbläsare i helskärmsläge, inklusive:

- Lägg till webbläsaren Microsoft Edge eller Kiosk Browser att köras som appar på en helskärmsenhet (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **Windows 10 och senare** som plattform > **Helskärm** som profiltyp).
- Nya funktioner och inställningar är tillgängliga för att tillåta eller begränsa (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp), däribland:

  - Microsoft Edge-webbläsare:
  - Använda helskärmsläget i Microsoft Edge
  - Uppdatera webbläsaren efter inaktivitetstid

 - Favoriter och sökning:
  - Tillåta ändringar av sökmotorn

Se följande för en lista över dessa inställningar:

- [Inställningar för enheter med Windows 10 (och senare) som ska köras med helskärmsläge](kiosk-settings-windows.md)
- [Enhetsbegränsningar för Microsoft Edge-webbläsaren](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Enhetsbegränsningar för favoriter och sökning](device-restrictions-windows-10.md##favorites-and-search)

Gäller för: Windows 10 och senare

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Nya inställningar för enhetsbegränsning för iOS-enheter och macOS-enheter <!-- 3448774   -->
Du kan begränsa vissa inställningar och funktioner på enheter som kör iOS och macOS (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** eller **macOS** som plattform > **Enhetsbegränsningar** som profiltyp). Den här uppdateringen lägger till fler funktioner och inställningar som du kan kontrollera, till exempel ange skärmtid, ändra eSIM-inställningar och mobilabonnemang och mer på iOS-enheter. Det går även att fördröja programuppdateringars synlighet för användaren och blockera innehållscachelagring på macOS-enheter. 

Funktioner och inställningar som du kan begränsa finns här:

- [Inställningar för iOS-enhetsbegränsning](device-restrictions-ios.md)
- [Inställningar för macOS-enhetsbegränsning](device-restrictions-macos.md)

Gäller för:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>”Kioskenheter” kallas nu ”dedikerade enheter” på Android Enterprise-enheter <!-- 3598402   -->
För att stämma överens med Android-terminologi ändras **kioskenheter** till **dedikerade enheter** för Android Enterprise-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > ** Android Enterprise för plattform > **Endast enhetens ägare** > **Enhetsbegränsningar** > **Dedikerade enheter**).

Om du vill se de tillgängliga inställningarna går du till [Enhetsinställningar för att tillåta eller begränsa funktioner](device-restrictions-android-for-work.md#dedicated-device-settings).

Gäller för:  
Android enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari och iOS-inställningarna för att fördröja visning av programuppdateringar för användaren flyttas i Intune-användargränssnittet <!-- 3640850, 3803313   -->
För iOS-enheter kan du ange Safari-inställningar och konfigurera programuppdateringar. I den här uppdateringen flyttas dessa till olika delar av Intune-användargränssnittet:

- Safari-inställningarna flyttades från **Safari** (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** som plattform > **Enhetsbegränsningar** som profiltyp) till **[Inbyggda appar](device-restrictions-ios.md#built-in-apps)** .
- Inställningen för att **fördröja visning av programuppdateringar för användaren för övervakade iOS-enheter** (**Programuppdateringar** > **Uppdateringsprinciper för iOS**) flyttas till **Enhetsbegränsningar** >  **[Allmänt](device-restrictions-ios.md#general)** .  Information om påverkan på befintliga principer finns i [iOS-programuppdateringar](software-updates-ios.md#configure-the-policy). 

Se följande för en lista över inställningarna:

- [iOS-enhetsbegränsningar](device-restrictions-ios.md) 
- [iOS-programuppdateringar](software-updates-ios.md)

Den här funktionen gäller för: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>Aktivering av begränsningar i enhetsinställningarna byter namn till Skärmtid på iOS-enheter <!-- 3699164   -->
Du kan konfigurera **Aktivera begränsningar i enhetsinställningarna** på övervakade iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** som plattform > **Enhetsbegränsningar** som profiltyp > **Allmänt**). I den här uppdateringen har den här inställningen bytt namn till **Skärmtid (endast övervakat)** . 

Beteendet är samma. Specifikt: 

- iOS 11.4.1 och tidigare: **Blockera** förhindrar slutanvändare att ange egna begränsningar i enhetsinställningarna. 
- iOS 12.0 och senare: **Blockera** förhindrar slutanvändare att ange en egen **skärmtid** i enhetsinställningarna, som innehålls- och sekretessbegränsningar. Fliken för begränsningar visas inte längre på enheter uppgraderade till iOS 12.0. Dessa inställningar finns i **Skärmtid**. 

En lista över inställningarna finns i [iOS-enhetsbegränsningar](device-restrictions-ios.md#general).

Gäller för: 
- iOS


### <a name="device-management"></a>Enhetshantering

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Byta namn på en registrerad Windows-enhet <!-- 1911112  -->
Du kan nu byta namn på en registrerad Windows 10-enhet (RS4 eller senare). Det kan göra så här: välj **Intune** > **Enheter** > **Alla enheter** > välj en enhet > **Byt namn på enhet**. Den här funktionen stöder för närvarande inte namnbyte för Windows-hybridenheter för Azure AD.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Tilldela automatiskt omfångstaggar till resurser som skapats av en administratör med det omfånget <!-- 3173823  -->
När en administratör skapar en resurs tilldelas alla omfångstaggar som tilldelats till administratören automatiskt till dessa nya funktioner.

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Rapport över misslyckad registrering flyttas till bladet Enhetsregistrering <!-- 3560202  -->
Rapporten **Misslyckade registreringar** har flyttats till avsnittet **Övervaka** på bladet **Enhetsregistrering**. Två nya kolumner (Registreringsmetod och Operativsystemversion) har också lagts till.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Rapport över avbrutna i företagsportalen har bytt namn till Ofullständiga användarregistreringar <!--3815076 eemiss -->
Rapporten över **avbrutna i företagsportalen** har bytt namn till **Ofullständiga användarregistreringar**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Veckan för 4 februari 2019

### <a name="app-management"></a>Apphantering

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Mörkt läge i Intune macOS-företagsportalen <!-- 3300524  -->
Nu stöder Intune macOS-företagsportalen mörkt läge för macOS. När du aktiverar mörkt läge på en macOS 10.14 +-enhet kommer företagsportalen att justera dess utseende till färger som speglar detta läge.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Veckan som börjar den 21 januari 2019

### <a name="app-management"></a>Apphantering

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Popup-meddelanden för Win32-appar <!-- 3136566   -->
Du kan förhindra att popup-meddelanden per apptilldelning visas för slutanvändarna. Från Intune, väljer du **Klientappar** > **Appar** > välj appen > **Tilldelningar** > **Inkludera grupper**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Uppdatering av användargränssnitt för Intune-appskyddsprinciper <!-- 3251427  -->
Vi har ändrat etiketterna för inställningar och knappar i Intunes appskydd för att de ska bli lättare att förstå. Några av ändringarna omfattar:  
- Kontroller ändras från **ja** / **nej** till primärt **blockera** / **tillåt** och **inaktivera** / **aktivera** kontroller. Även etiketterna har uppdaterats.  
- Inställningarna formateras om så att inställningen och dess etikett är sida vid sida i kontrollen, vilket ger bättre navigering.   

Standardinställningar och antal inställningar förblir detsamma, men den här ändringen gör att användarna kan förstå, navigera och använda inställningar enklare för att tillämpa valda appskyddsprinciper. Mer information finns i [iOS-inställningar](app-protection-policy-settings-ios.md) och [Android-inställningar](app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Ytterligare inställningar för Outlook <!-- 3301182  -->
Nu kan du konfigurera följande ytterligare inställningar för Outlook för iOS och Android med hjälp av Intune:

- Tillåt bara arbets- eller skolkonton att användas i Outlook i iOS och Android
- Distribuera modern autentisering för Office 365 och lokala konton med modern hybridautentisering
- Använd `SAMAccountName` för användarnamnfältet i e-postprofilen när grundläggande autentisering väljs
- Tillåt att kontakter sparas
- Konfigurera e-posttips för externa mottagare
- Konfigurera **Prioriterad inkorg**
- Kräv biometri för åtkomst till Outlook för iOS
- Blockera externa bilder

> [!NOTE]
> Om du använder principer för Intune-appskydd till att hantera åtkomsten för företagsidentiteter bör du inte aktivera att **kräva biometri**. Mer information finns i **Kräva företagsautentiseringsuppgifter för åtkomst** för [iOS-åtkomstinställningar](app-protection-policy-settings-ios.md#access-requirements) och [Android-åtkomstinställningar](app-protection-policy-settings-android.md#access-requirements).

Mer information finns i [Konfigurationsinställningar för Microsoft Outlook](app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Ta bort Android Enterprise-appar <!-- 1352553 -->
Du kan ta bort hanterade Google Play-appar från Microsoft Intune. Om du vill ta bort en hanterad Google Play-app öppnar du Microsoft Intune i Azure-portalen och väljer **Klientappar** > **Appar**. Från listan över appar väljer du ellipserna (...) till höger om den hanterade Google Play-appen och väljer sedan **Ta bort** från den visade listan. När du tar bort en hanterad Google Play-app från applistan blir den hanterade Google Play-appen automatiskt ej godkänd.

#### <a name="managed-google-play-app-type----1352580---"></a>Hanterade Google Play-apptyper <!-- 1352580 -->
Den **hanterade Google Play**-apptypen gör att du kan lägga till mer specifikt [hanterade Google Play-appar](https://play.google.com/work/search?q=microsoft&c=apps) till Intune. Som Intune-administratör kan du bläddra, söka, godkänna, synkronisera och tilldela godkända hanterad Google Play-appar i Intune.  Du behöver inte längre bläddra till den hantera Google Play-konsolen separat och du behöver inte längre autentisera dig på nytt.  I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** väljer du **Hanterat Google Play-konto** som apptyp.

### <a name="default-android-pin-keyboard----3802457---"></a>Standardtangentbord för PIN-kod i Android <!-- 3802457 -->
För slutanvändare som har angett en PIN-kod för Intune-appskydd (APP) på sina Android-enheter med PIN-kodtypen ”Numerisk” visas nu standardtangentbordet för Android istället för det fasta Android-tangentbordsgränssnittet som utformats tidigare. Den här ändringen har gjorts för att vara konsekvent när standardtangentbord används på både Android och iOS, för båda PIN-typerna ”Numerisk” och/eller ”Lösenord”. Mer information om inställningar för slutanvändaråtkomst på Android, till exempel PIN-kod för APP finns i [Åtkomstkrav för Android](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Använda Microsofts rekommenderade inställningar med säkerhetsbaslinjer (allmänt tillgänglig förhandsversion) <!-- 2055484   -->

Intune integrerar med andra tjänster som fokuserar på säkerhet, inklusive Windows Defender ATP och Office 365 ATP. Kunder efterfrågar en gemensam strategi och en sammanhängande uppsättning säkerhetsarbetsflöden från slutpunkt till slutpunkt för alla Microsoft 365-tjänster. Vårt mål är att optimera strategier och skapa lösningar som kan hantera säkerhetsåtgärder och vanliga administratörsuppgifter. I Intune vill vi uppnå det här målet genom att publicera en uppsättning Microsoft-rekommenderade ”säkerhetsbaslinjer” (**Intune** > **Security baselines** ((Säkerhetsbaslinjer)).  En administratör kan skapa säkerhetsprinciper direkt från dessa baslinjer, och sedan distribuera dem till sina användare. Du kan också anpassa rekommendationerna om bästa praxis för att uppfylla behoven i organisationen. Intune kontrollerar att enheterna uppfyller baslinjerna och meddelar administratören om användare eller enheter inte uppfyller efterlevnadskraven.

Den här funktionen är en offentlig förhandsversion, så profiler som skapas nu flyttas inte över till säkerhetsbaslinjemallar som är allmänt tillgängliga. Du bör inte planera att använda dessa förhandsmallar i produktionsmiljö.

Läs mer om säkerhetsbaslinjer i [Skapa en säkerhetsbaslinje för Windows 10 i Intune](security-baselines-monitor.md).

Den här funktionen gäller för: Windows 10 och senare

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Icke-administratörer kan aktivera BitLocker på Windows 10-enheter som är anslutna till Azure AD<!-- 2147379   -->
När du aktiverar BitLocker-inställningar på Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10 och senare** för plattform > **Endpoint protection** för Profiltyp > **Windows-kryptering**), lägger du till BitLocker-inställningar. 

Den här uppdateringen innehåller en ny inställning för BitLocker för att låta standardanvändare (icke-administratörer) aktivera kryptering. 

De här inställningarna finns i [Inställningar för slutpunktsskydd för Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Kontrollera Configuration Manager-kompatibilitet <!-- 2192052  eepublished  -->
Den här uppdateringen innehåller en ny kompatibilitetsinställning för System Center Configuration Manager (**Enhetskompabilitet** > **Principer** > **Skapa princip** > **Windows 10 och senare** > **Configuration Manager-kompabilitet**). Configuration Manager skickar signaler till Intune-kompatibilitet. Med hjälp av inställningen kan du kräva att alla Configuration Manager-signaler returnerar ”kompatibel”.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd är enheten inte kompatibel i Intune.

[Configuration Manager-kompatibilitet](compliance-policy-create-windows.md#configuration-manager-compliance) beskriver den här inställningen.

Gäller för: Windows 10 och senare

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Anpassa bakgrund på övervakade iOS-enheter med hjälp av en profil för enhetskonfiguration <!-- 2809324   -->
När du skapar en profil för enhetskonfiguration för iOS-enheter kan du anpassa vissa inställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsfunktioner** för profiltypen). Den här uppdateringen innehåller nya inställningar för **Bakgrund** som gör att administratörer kan använda en .png-, .jpg- eller .jpeg-bild på startsidan eller låsskärmen. Inställningar för bakgrund gäller endast för övervakade enheter. 

En lista över de här inställningarna finns i [Funktionsinställningar för iOS-enheter](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Helskärmsläge för Windows 10 är allmänt tillgängligt <!-- 3594661  -->
I den här uppdateringen är funktionen helskärmsläge på Windows 10 och senare enheter allmänt tillgängligt (GA). Alla inställningar som du kan lägga till och konfigurera finns i [Inställningar för helskärmsläge för Windows 10 (och senare)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Kontaktdelning via Bluetooth har tagits bort i Enhetsbegränsningar > Enhetens ägare för Android Enterprise <!-- 3598396   -->
När du skapar en profil för enhetsbegränsningar för Android Enterprise-enheter finns inställningen **Dela kontakter via Bluetooth**. I den här uppdateringen tas inställningen **Dela kontakter via Bluetooth** bort (**Enhetskonfiguration** > **Profiler**  >  **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar > Enhetens ägare** för profiltyp > **Allmän**). 

Inställningen **Dela kontakter via Bluetooth** har inte stöd för hantering av Android Enterprise-enhetens ägare. Så när den här inställningen tas bort, påverkar det inga enheter eller klienter, även om den här inställningen är aktiverad och konfigurerad i din miljö.

Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](device-restrictions-android-for-work.md).

Gäller för: Ägare av Android Enterprise-enhet

### <a name="device-management"></a>Enhetshantering

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Stöd för selektiv rensning för WIP-WE-enheter <!-- 1434452 -->
Med WIP-WE (Windows Information Protection Without Enrollment) kan kunder skydda sina företagsdata på Windows 10-enheter utan att fullständig MDM-registrering krävs. När dokument skyddas med en WIP-WE-princip kan skyddade data rensas selektivt av en Intune-administratör. Genom att välja användaren och enheten, och skicka en rensningsbegäran, blir alla data som skyddades via WIP-WE-principen oanvändbara. Från Intune på Azure-portalen väljer du **Mobilapp** > **Selektiv radering av app**.

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Ny arbetsloggar och möjligheten att skicka loggar till Azure Monitor-tjänster <!-- 3762211  -->
Intune har inbyggd granskningsloggning som spårar händelser när de ändras. Den här uppdateringen innehåller nya loggningsfunktioner, inklusive: 
- Arbetsloggar (förhandsversion) som visar information om användare och enheter som registrerats, inklusive lyckade och misslyckade försök.
- Granskningsloggarna och arbetsloggarna kan skickas till Azure Monitor, inklusive lagringskonton, händelsehubbar och logganalyser. De här tjänsterna gör att du kan lagra och använda analyser som Splunk och QRadar samt få visualiseringar av dina loggningsdata.

[Skicka data till lagring, händelsehubbar eller logganalyser i Intune](review-logs-using-azure-monitor.md) har mer information om den här funktionen.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Hoppa över flera skärmar för installationsassistenten på en iOS DEP-enhet <!-- 2687509  -->
Förutom de skärmar som du kan hoppa över just nu kan du ange att iOS DEP-enheter hoppar över följande skärmar i installationsassistenten när en användare registrerar enheten: Skärmton, Sekretess, Android-migrering, Start-knapp, iMessage och FaceTime, Registrering, Bevaka migrering, Utseende, Skärmtid, Programuppdatering, SIM-installation.
Om du vill välja vilka skärmar som ska hoppas över, går du till **Enhetsregistrering** > **Apple-registrering** > **Tokens för registreringsprogram** > välj en token > **Profiler** > välj en profil > **Egenskaper** > **Anpassning av installationsassistenten** > välj **Dölj** för alla skärmar som du vill hoppa över > **OK**.
Om du skapar en ny profil eller redigerar en profil måste den valda överhoppningsskärmen synkroniseras med Apple MDM-servern. Användare kan utfärda en manuell synkronisering av enheterna så att det inte sker någon fördröjning i att plocka upp profiländringarna.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Appdistribution för Android Enterprise APP-WE <!-- 1171203 -->
För Android-enheter i ett distributionsscenario med en appskyddsprincip utan registrering (APP-WE) kan du nu använda hanterad Google Play för att distribuera store-appar och LOB-appar till användare. Mer specifikt kan du ge slutanvändarna en appkatalog och installationsfunktioner som inte längre kräver att slutanvändare lättar på säkerhetshållningen för sina enheter genom att tillåta installationer från okända källor. Dessutom kan det här distributionsscenariot ge en förbättrad slutanvändarupplevelse.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Veckan som börjar den 14 januari 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Förhandsgranskning av stöd för företagsägda, fullständigt hanterade Android-enheter <!-- 1574342  -->
Nu har Intune fullt stöd för hanterade Android-enheter, ett företagsägt scenario av ”enhetsägare” där enheter hanteras noggrant av IT och är kopplade till enskilda användare. Detta gör att administratörer kan hantera hela enheten, tillämpa en utökad uppsättning principkontroller som inte är tillgängliga för arbetsprofiler och begränsa användare från att installera appar från hanterad Google Play endast. Mer information finns i artiklarna om att [konfigurera Intune-registrering av fullständigt hanterade Android-enheter](android-fully-managed-enroll.md) och att [registrera dedikerade enheter eller fullständigt hanterade enheter](android-dedicated-devices-fully-managed-enroll.md).  Observera att den här funktionen är en förhandsversion. Vissa Intune-funktioner, till exempel certifikat, efterlevnad och villkorlig åtkomst, är inte tillgängliga med fullständigt hanterade Android-användarenheter.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Veckan som börjar med 7 januari 2019

### <a name="app-management"></a>Apphantering

#### <a name="intune-app-pin----2298397---"></a>Intune-appens PIN-kod <!-- 2298397 -->
Som IT-administratör kan du nu konfigurera hur många dagar en användare kan vänta tills Intune-appens PIN-kod måste ändras. Den nya inställningen är *Återställ PIN-kod efter antal dagar* och är tillgänglig i Azure-portalen genom att välja **Intune** > **Klientappar** > **Appskyddsprinciper** > **Skapa princip** > **Inställningar** > **Åtkomstbehörigheter**. Den här funktionen, som är tillgänglig för [iOS](app-protection-policy-settings-ios.md)- och [Android](app-protection-policy-settings-android.md)-enheter, stöder ett positivt heltalsvärde.


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune-enhetens rapportfält <!-- 2748738 -->
Intune ger ytterligare fält för enhetsrapportering inklusive appregistrerings-ID, Android-tillverkare, modell och version av säkerhetsuppdatering samt iOS-modell. I Intune är dessa fält tillgängliga genom att välja **Klientappar** > **Appskyddsstatus** och sedan välja **Appskyddsrapport: iOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodell (Android och iOS) och lägsta inställning för version av Android-säkerhetsuppdatering. 


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrativa mallar finns i offentlig förhandsversion och flyttas till sin egen konfigurationsprofil <!-- 3322847 -->

Administrativa mallar i Intune (**Enhetskonfiguration** > **Administrationsmallar**) är för tillfället i allmänt tillgänglig förhandsvisning. I denna uppdatering:

- De administrativa mallarna innehåller ungefär 300 inställningar som kan hanteras i Intune. De här inställningarna fanns tidigare endast i redigeraren.
- Administrativa mallar finns i offentlig förhandsversion.
- Administrativa mallar flyttar från **Enhetskonfiguration** > **Administrativa mallar** till **Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Windows 10 och senare** > i **Profiltyp**, välj **Administrativa mallar**.
- Rapportering är aktiverad

Mer information om den här funktionen finns i [Windows 10-mallar för att konfigurera grupprincipinställningar](administrative-templates-windows.md).

Gäller för: Windows 10 och senare

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Använda S/MIME för att kryptera och signera flera enheter för en användare  <!-- 1333642 -->
Den här uppdateringen innehåller S/MIME-e-postkryptering som använder en ny importerad certifikatprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj plattformen > profiltypen **PKCS-importerat certifikat**). Du kan importera certifikat i PFX-format i Intune. Intune kan sedan leverera samma certifikat till flera enheter som registrerats av en enda användare. Detta omfattar även följande:
- Den interna e-postprofilen för iOS har stöd för att aktivera S/MIME-kryptering med importerade certifikat i PFX-format.
- Den interna e-postappen på Windows Phone 10-enheter använder S/MIME-certifikatet automatiskt.
- Det privata certifikatet kan levereras över flera plattformar. Men alla e-postappar har inte stöd för S/MIME.
- På andra plattformar kan du behöva konfigurera e-postappen manuellt för att aktivera S/MIME.  
- E-postappar som har stöd för S/MIME-kryptering kan hantera hämtning av certifikat för S/MIME-kryptering av e-post på ett sätt som MDM inte stöder, till exempel genom att läsa från utgivarens certifikatarkiv.
Mer information om den här funktionen finns i [S/MIME-översikt för att signera och kryptera e-post](certificates-s-mime-encryption-sign.md).
Stöds på: Windows, Windows Phone 10, macOS, iOS och Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nya alternativ för att automatiskt ansluta och bevara regler vid användning av DNS-inställningarna på enheter med Windows 10 och senare <!-- 1333665, 2999078 -->
I Windows 10 och senare enheter kan du skapa en VPN-profil som innehåller en lista över DNS-servrar för att lösa domäner, som till exempel contoso.com. Den här uppdateringen omfattar nya inställningar för namnmatchning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **Windows 10 och senare** för plattform > välj **VPN** för Profiltyp > **DNS-inställningarna** >**Lägg till**): 
- **Anslut automatiskt**: När den är **Aktiverad**, ansluter enheten automatiskt till VPN-anslutningen när en enhet kontaktar en domän som du anger, t.ex contoso.com.
- **Beständig**: Som standard är alla NRPT-regler (principtabell för namnmatchning) aktiva så länge enheten är ansluten med hjälp av den här VPN-profilen. När inställningen är **Aktiverad** för en NRPT-regel förblir regeln aktiv på enheten, även om VPN-anslutningen kopplas bort. Regeln gäller tills VPN-profilen tas bort eller tills regeln tas bort manuellt, vilket kan göras med hjälp av PowerShell.
[Windows 10 VPN-inställningar](vpn-settings-windows-10.md) beskriver inställningarna. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Använda identifiering av betrott nätverk för VPN-profiler på Windows 10-enheter <!-- 1500165 -->
När du använder identifiering av betrott nätverk kan du förhindra VPN-profiler från att automatiskt skapa en VPN-anslutning när användaren redan är i ett betrott nätverk. Med den här uppdateringen kan du lägga till DNS-suffix om du vill aktivera identifiering av betrott nätverk på enheter som kör Windows 10 och senare (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **VPN** för profiltyp).
[Windows 10-VPN-inställningar](vpn-settings-windows-10.md) visar en lista över aktuella VPN-inställningar.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Hantera Windows Holographic for Business-enheter som används av flera användare <!-- 1907917, 1063203 -->
För närvarande kan du konfigurera delade datorinställningar på Windows 10- och Windows Holographic for Business-enheter med en anpassad OMA-URI-inställning. Med den här uppdateringen läggs en ny profil till för att konfigurera delade enhetsinställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** > **Delad enhet för flera användare**).
Mer information om den här funktionen finns i [Intune-inställningar för att hantera delade enheter](shared-user-device-settings.md).
Gäller för: Windows 10 och senare, Windows 10 Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nya Windows 10 Update-inställningar <!--2626030  2512994  -->
För dina [Windows 10-uppdateringsringar](windows-update-for-business-configure.md) kan du konfigurera:
- **Funktionssätt för automatisk uppdatering** – Använd ett nytt alternativ, *Återställ till standard*, för att återställa de ursprungliga inställningarna för automatisk uppdatering på Windows 10-datorer som kör *uppdateringen från oktober 2018*
- **Blockera användaren från att pausa Windows-uppdateringar** – Konfigurera en ny programuppdateringsinställning som gör att du kan blockera eller tillåta användarna att pausa uppdateringsinstallationen från *Inställningar* på deras datorer. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>E-postprofiler för iOS kan använda S/MIME-signering och kryptering <!-- 2662949 -->
Du kan skapa en e-postprofil som innehåller olika inställningar. Den här uppdateringen inkluderar S/MIME-inställningar som kan användas för signering och kryptering av e-postmeddelanden på iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > **E-post** för profiltyp).
[iOS e-postkonfigurationsinställningar](email-settings-ios.md) visar en lista över inställningarna.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Vissa BitLocker-inställningar har stöd för Windows 10 Pro-versionen<!-- 2727036 -->
Du kan skapa en konfigurationsprofil som anger inställningar för slutpunktsskydd för Windows 10-enheter, inklusive BitLocker. Den här uppdateringen lägger till stöd för Windows 10 Professional-versionen för vissa BitLocker-inställningar. De här skyddsinställningarna finns i [Inställningar för slutpunktsskydd för Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Konfiguration av delad enhet har bytt namn till Meddelande på låsskärm för iOS-enheter i Azure-portalen<!-- 2809362 -->
När du skapar en profil för iOS-enheter kan du lägga till inställningar för **Konfiguration för delad enhet** för att visa specifik text på låsskärmen. Den här uppdateringen innehåller följande ändringar: 
- Inställningarna **Konfiguration för delad enhet** i Azure-portalen har bytt namn till ”Meddelande på låsskärmen (endast övervakat)” (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > välj **Enhetsfunktioner** för Profiltyp > **Meddelande på låsskärmen**).
- När du lägger till meddelanden på låsskärmen kan du infoga ett serienummer, ett enhetsnamn eller ett annat enhetsspecifikt värde som en variabel i **Resurstagginformation** och **Fotnot på låsskärmen**. Du kan till exempel ange `Device name: {{devicename}}` eller `Serial number is {{serialnumber}}` med hjälp av klammerparenteser. [iOS-token](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) visar en lista över de tillgängliga token som kan användas.
[Inställningar för att visa meddelanden på låsskärmen](shared-device-settings-ios.md) visar en lista över inställningarna.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nya inställningar för enhetsbegränsning av App Store, dokumentvisning och spel har lagts till i iOS-enheter <!-- 2827760-->
I **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel** läggs följande inställningar till: Tillåt hanterade appar att skriva kontakter till ohanterade kontaktkonton Tillåt ohanterade appar att läsa från hanterade kontaktkonton Om du vill se de här inställningarna går du till [iOS-enhetsbegränsningar](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Inställningar för nytt meddelande, tips och keyguard för Android Enterprise-enhetsägarenheter <!-- 3201839 3201843 -->
Den här uppdateringen innehåller flera nya funktioner på Android Enterprise-enheter vid körning som enhetsägare. Om du vill använda dessa funktioner, gå till **Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Android Enterprise** > i **Profiltyp**, välj **Endast enhetens ägare** > **Enhetsbegränsningar**.

Nya funktioner som ingår: 

- Inaktivera systemmeddelanden till att inte visas, inklusive inkommande anrop, systemaviseringar, systemfel med mera.
- Föreslår hoppa över start av självstudier och tips för appar som öppnas för första gången.
- Inaktivera avancerade keyguard-inställningar, till exempel kamera, meddelanden, upplåsning med fingeravtryck med mera.


Om du vill visa inställningarna går du till avsnittet om [begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android Enterprise-enhetsägarenheter kan använda VPN-anslutningar med Always On <!-- 3202194 -->
I den här uppdateringen kan du använda VPN-anslutningar som alltid är aktiva på Android Enterprise-enheter. Ständiga VPN-anslutningar förblir anslutna eller återansluter omedelbart när användaren låser upp sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. Du kan också placera anslutningen i ”låst” läge, vilket blockerar all nätverkstrafik tills VPN-anslutningen aktiveras.
Du kan aktivera VPN-anslutningar som alltid är aktiva i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar** för enhetsägare endast > **Anslutningar**. Om du vill visa inställningarna går du till avsnittet om [begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Ny inställning för att avsluta processer i Aktivitetshanteraren på Windows 10-enheter <!-- 3285177 --> 
Den här uppdateringen innehåller en ny inställning för att avsluta processer med hjälp av Aktivitetshanteraren på Windows 10-enheter. Med hjälp av en profil för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Windows 10** > i **Profiltyp**, välj **Enhetsbegränsningar** > **Allmänna** inställningar), väljer du att tillåta eller förhindra den här inställningen.
Om du vill visa de här inställningarna går du till [Inställningar av begränsningar för Windows 10-enheter](device-restrictions-windows-10.md).
Gäller för: Windows 10 och senare


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Mer detaljerade felmeddelanden för registreringsbegränsning <!-- 3111564 -->
Mer detaljerade felmeddelanden är tillgängliga när registreringsbegränsningar inte har uppfyllts. Om du vill se dessa meddelanden går du till **Intune** > **Felsök** > och markerar tabellen Registreringsfel. Mer information finns i [listan över registreringsfel](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="tenant-status-dashboard-----1124854---"></a>Instrumentpanel för klientorganisationsstatus  <!-- 1124854 -->
Den nya [sidan Klientorganisationsstatus](tenant-status.md) utgör en enskild plats där du kan visa status och relaterad information för din klient.  Instrumentpanelen är uppdelad i fyra områden:
- **Information om klientorganisation** – Visar information som innefattar klientens namn och plats, MDM-utfärdare, totalt antal registrerade enheter i klientorganisationen och antal licenser. I det här avsnittet visas även den aktuella versionen av tjänsten för din klientorganisation.
- **Status för anslutningsprogrammet** – Visar information om tillgängliga anslutningsprogram du har konfigurerat och kan även visa dem som du inte har aktiverat ännu.  
   Baserat på det aktuella tillståndet för varje anslutningsprogram är de flaggade med Felfri, Varning eller Ej felfri. Välj ett anslutningsprogram för att visa detaljer och visa information eller konfigurera ytterligare information för det.
-  **Hälsotillstånd för Intune-tjänsten** – Visar information om aktiva incidenter eller avbrott i klientorganisationen. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office.
-  **Nytt i Intune** – Visar aktiva meddelanden för klientorganisationen. Meddelanden omfattar till exempel aviseringar när klientorganisationen får de senaste funktionerna för Intune.  Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Ny hjälp- och supportupplevelse i företagsportalen för Windows 10 <!-- 1488939-->
Den nya sidan Hjälp och support i Företagsportal hjälper användare att felsöka och be om hjälp med problem med appen och åtkomst. Från den nya sidan kan de skicka fel- och diagnostiklogginformation via e-post och hitta information om organisationens supportavdelning. De hittar också avsnittet Vanliga frågor och svar med länkar till relevant Intune-dokumentation. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Ny hjälp- och supportupplevelse för Intune   <!-- #3307080 -->
Vi lanserar den nya hjälp- och supportupplevelsen för alla klientorganisationer under de närmaste dagarna. Den här nya upplevelsen är tillgänglig för Intune och kan nås när du använder Intune-bladen på [Azure-portalen](https://portal.azure.com/).
Med den nya upplevelsen kan du beskriva problemet med egna ord och ta emot felsökningsinsikter och webbaserat åtgärdsinnehåll. De här lösningarna är tillgängliga via en regelbaserad maskininlärningsalgoritm som drivs av användarfrågor. Utöver problemspecifika rekommendationer använder du det nya arbetsflödet för att öppna ett supportärende via e-post eller telefon. Den här nya upplevelsen ersätter den tidigare hjälp- och supportupplevelsen av en statisk uppsättning förvalda alternativ som är baserade på området i konsolen du befinner dig i när du öppnar Hjälp och support. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-apps----1081941---"></a>Omfattningstaggar för appar <!-- 1081941 -->
Du kan skapa omfångstaggar som begränsar åtkomsten för roller och appar. Du kan lägga till en omfångstagg för en app så att endast personer med roller som också tilldelats den omfångstaggen har åtkomst till appen. För närvarande kan appar som har lagts till i Intune från hanterad Google Play eller appar som har köpts med hjälp av Apples volymköpsprogram (VPP) inte tilldelas omfångstaggar (men framtida stöd för detta planeras). Mer information finns i [Använda omfångstaggar för att filtrera principer](scope-tags.md).

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>Veckan som börjar med 10 december 2018

### <a name="app-management"></a>Apphantering

#### <a name="updates-for-application-transport-security----748318---"></a>Uppdateringar för Application Transport Security <!-- 748318 -->

Microsoft Intune har stöd för TLS 1.2+ (Transport Layer Security) i syfte att tillhandahålla förstklassig kryptering, göra Intune säkrare som standard och anpassa programmet till andra Microsoft-tjänster som t.ex. Microsoft Office 365. För att uppfylla detta krav framtvingar iOS- och macOS-företagsportalerna Apples uppdaterade ATS-krav (Application Transport Security), som även kräver TLS 1.2 +. ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS- och macOS-appar i företagsportalen. Mer information finns i [Intunes supportblogg](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK kommer att stödja 256-bitars krypteringsnycklar <!-- 1832174 -->
Intune App SDK för Android använder nu 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciperna. SDK fortsätter att stödja 128-bitars nycklar för kompatibilitet med innehåll och appar som använder äldre versioner av SDK.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>Microsofts version 4.5.0 för automatisk uppdatering krävs för macOS-enheter <!-- 3503442 -->
Om du vill fortsätta att få uppdateringar av företagsportalen och andra Office-program, måste de macOS-enheter som hanteras av Intune uppgraderas till Microsofts version 4.5.0 för automatisk uppdatering. Användarna kanske redan har den här versionen för sina Office-appar.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune kräver macOS 10.12 eller senare <!-- 2827778 -->
Intune kräver nu macOS version 10.12 eller senare. Enheter med tidigare macOS-versioner kan inte använda företagsportalen när de registrerar sig i Intune. För att fortsätta att få support och nya funktioner måste användarna uppgradera sina enheter till macOS 10.12 eller senare, samt uppgradera företagsportalen till den senaste versionen.

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>Veckan som börjar den 26 november 2018

### <a name="app-management"></a>Apphantering

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Avinstallera appar på företagsägda övervakade iOS-enheter <!-- 1281677 -->

Du kan ta bort alla appar på företagsägda övervakade iOS-enheter. Du kan ta bort en app genom att rikta antingen användar- eller enhetsgrupper med tilldelningstypen **avinstallera**. För personliga eller ej kontrollerade iOS-enheter kommer du fortsätta kunna ta bort appar som har installerats med hjälp av Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Ladda ned innehåll för Intune Win32-app <!-- 2617320 -->
Windows 10 RS3-klienter och högre hämtar Intune Win32-appinnehåll med en komponent för leveransoptimering på Windows 10-klienten. Leveransoptimering ger Peer-to-Peer-funktioner som är aktiverat som standard. För närvarande kan leveransoptimering konfigureras med en grupprincip. Mer information finns i [Leveransoptimering för Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Slutanvändarenhet och appinnehållsmenyn <!-- 2771453 -->
Slutanvändare kan nu använda snabbmenyn på enheter och appar för att utlösa vanliga åtgärder som att byta namn på en enhet eller kontrollera efterlevnad.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Ange en anpassad bakgrund den hanterade hemskärmsappen  <!-- 3041945 -->
Vi ska lägga till en inställning som låter dig anpassa bakgrundsutseendet på den hanterade hemskärmsappen på Android Enterprise, flera appar, enheter i helskärmsläge.  För att konfigurera **Anpassad URL-bakgrund** går du till Intune i Azure portal > Enhetskonfiguration. Välj en aktuell enhetskonfigurationsprofil eller skapa en ny om du vill redigera dess inställningar för helskärmsläge.
Mer information om inställningar för helskärmsläge finns i avsnittet om [Begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Spara och tillämpa tilldelning av appskyddsprincip <!-- 3104570 -->
Du har nu bättre kontroll över dina [Tilldelningar av appskyddsprinciper](app-protection-policies.md#deploy-a-policy-to-users). När du väljer *Tilldelningar* för att ange eller redigera en princips tilldelningar måste du **Spara** konfigurationen för att ändringen ska tillämpas. Använd **Ignorera** för att rensa alla ändringar du gör utan att spara dessa till listorna inkludera eller exkludera.  Genom att kräva Spara eller Ignorera tilldelas endast de användare som du avser en appskyddsprincip.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nya Microsoft Edge-webbläsarinställningar för Windows 10 och senare <!-- 3174639 -->
Den här uppdateringen innefattar en ny inställning för att styra och hantera Microsoft Edge-webbläsaren på dina enheter. En lista över dessa inställningar finns i [Enhetsbegränsning för Windows 10 (och senare)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Stöd för nya appar med appskyddsprinciper <!-- 3330037 -->
Du kan nu hantera följande appar med [Intune principer för appskydd](app-protection-policies.md):
- Stream (iOS)
- Att göra (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Använd appskyddsprinciper för att skydda företagsdata och kontrollera dataöverföring för dessa appar, så som andra principhanterade Intune-appar. Obs! Om Flow ännu inte syns i konsolen kan du lägga till det när du skapar eller redigerar principerna för appskydd. Du gör detta genom att använda alternativet **+ fler appar** och sedan ange *app-ID* för Flow i indatafältet. Använd *com.microsoft.flow* för Android och *com.microsoft.procsimo* för iOS.


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Versionsnummer och build-nummer för iOS och macOS visas <!-- 1892471 -->
I **Enhetsefterlevnad** > **Enhetsefterlevnad** visas operativsystemsversionerna iOS och macOS. De är tillgängliga för användning i efterlevnadsprinciper. Uppdateringen innefattar versionsnumret vilket kan konfigureras för båda plattformarna.
När säkerhetsuppdateringar lanseras låter Apple vanligtvis versionsnumret vara som det är men uppdaterar byggenumret. Genom att använda byggenumret i en efterlevnadsprincip kan du enkelt kontrollera om en säkerhetsriskuppdatering har installerats.
Se efterlevnadsprinciper för [iOS](compliance-policy-create-ios.md#device-health) och [macOS](compliance-policy-create-mac-os.md#device-properties) om du vill använda funktionen.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Uppdateringsringar ersätts med leveransoptimeringsinställningar för Windows 10 och senare <!-- 2753807 -->
Leveransoptimering är en ny konfigurationsprofil för Windows 10 och senare. Funktionen ger en smidigare upplevelse för att leverera programuppdateringar till enheter i din organisation. Uppdateringen hjälper dig även att leverera inställningarna till nya och befintliga uppdateringsringar med en konfigurationsprofil.
Se [leveransoptimeringsinställningar för Windows 10 (och senare)](delivery-optimization-windows.md) för att konfigurera en konfigurationsprofil för leveransoptimering.

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Nya inställningar för enhetsbegränsning har lagts till i iOS-enheter och macOS-enheter <!-- 2827760 -->
Den här uppdateringen innehåller nya inställningar för iOS- och macOS-enheter med iOS 12:

**Inställningar för iOS**: 
- Allmänt: Blockera borttagning av appar (endast övervakat)
- Allmänt: Blockera USB-begränsat läge (endast övervakat)
- Allmänt: Framtvinga automatiskt datum och tid (endast övervakat)
- Lösenord: Blockera automatisk ifyllning av lösenord (endast övervakat)
- Lösenord: Blockera förfrågningar om lösenordsnärhet (endast övervakat)
- Lösenord: Blockera lösenordsdelning (endast övervakat)

**Inställningar för macOS**: 
- Lösenord: Blockera automatisk ifyllning av lösenord
- Lösenord: Blockera förfrågningar om lösenordsnärhet
- Lösenord: Blockera lösenordsdelning

Mer information om dessa inställningar finns i inställningarna för enhetsbegränsning i [iOS](device-restrictions-ios.md) och [macOS](device-restrictions-macos.md).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Välj appar som spåras på sidan för registreringsstatus<!-- 2531007 -->
Du kan välja vilka appar som spåras på sidan för registreringsstatus. Användaren kan inte använda enheten förrän dessa appar har installerats. Mer information finns i [Konfigurera en sida för registreringsstatus](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Sök efter Autopilot-enheter med serienummer <!--2595788 -->
Du kan nu söka efter Autopilot-enheter med serienummer. Om du vill göra det väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter** > ange ett serienummer i rutan **Sök efter serienummer** > tryck på Retur.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Spåra installation av Office ProPlus <!--2620217 -->
Användare kan följa installationsförloppet för [Office ProPlus](apps-add-office365.md) med hjälp av sidan [Registreringsstatus](windows-enrollment-status.md). Mer information finns i [Konfigurera en sida för registreringsstatus](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Aviseringar om utgående VPP-token eller om att kvarvarande licenser för företagsportalen håller på att ta slut <!-- 2237572 -->
Om du använder Volume Purchase Program (VPP) för att företablera företagsportalen vid DEP-registrering visas en varning i Intune när en VPP-token håller på att upphöra och när licenserna för företagsportalen nästan är slut.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>macOS DEP-stöd för Apple School Manager-konton <!--3006133 -->
Intune stöder nu användning av programmet för enhetsregistrering (DEP) på macOS-enheter för Apple School Manager-konton.  Mer information finns i [Registrera macOS-enheter automatiskt med Apple School Manager eller programmet för enhetsregistrering](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Ny SKU för Intune-enhetsprenumeration <!--3312071-->
För att sänka kostnaderna för hantering av enheter i företag finns det nu en ny enhetsbaserad prenumerations-SKU. Den här SKU:n för Intune-enheter licensieras per enhet och månad. Priset varierar beroende på licensprogrammet. Den är tillgänglig direkt via Microsoft 365-administrationscentret och via [Enterprise-avtal](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), [Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA) [Microsofts öppna avtal ](https://partner.microsoft.com/licensing/licensing-agreements) och [Molnlösningsleverantör](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Enhetshantering

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Pausa tillfälligt helskärmsläge på Android-enheter för att göra ändringar <!-- 3041935 -->
När du använder Android-enheter i helskärmsläge för flera appar, kan en IT-administratör behöva göra ändringar i enheten. Den här uppdateringen innefattar nya inställningar för helskärmsläge för flera appar så att IT-administratörer tillfälligt kan pausa helskärmsläget med hjälp av en PIN-kod och få åtkomst till hela enheten.
Mer information om inställningar för helskärmsläge finns i avsnittet om [Begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Aktivera den virtuella hemknappen på Android Enterprise-enheter i helskärmsläge  <!-- 3042021 -->
En ny inställning låter användare trycka på en programstyrd knapp på sin enhet för att växla mellan den hanterade hemskärmsappen och andra tilldelade appar på sin enhet för helskärmsläget för flera appar. Den här inställningen är särskilt användbart i scenarier där en användares app för helskärmsläge inte svarar på rätt sätt på knappen ”Bakåt”. Du kommer att kunna konfigurera den här inställningen för företagsägda Android-enheter för enskild användning. För att aktivera eller inaktivera den **virtuella hemknappen**, går du till Intune i Azure Portal > enhetskonfiguration. Välj en aktuell enhetskonfigurationsprofil eller skapa en ny om du vill redigera dess inställningar för helskärmsläge.
Mer information om inställningar för helskärmsläge finns i avsnittet om [Begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>Veckan som börjar den 12 november 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Stöd för Network Access Control (NAC) för Citrix SSO för iOS <!-- 3259404 -->

Citrix släppte en uppdatering av Citrix Gateway som tillåter Network Access Control (NAC) för Citrix SSO för iOS i Intune. Du kan välja att inkludera ett enhets-ID i en VPN-profil i Intune och sedan skicka den här profilen till dina iOS-enheter. Du måste installera den senaste uppdateringen av Citrix Gateway för att kunna använda den här funktionen.

[Konfigurera VPN-inställningar på iOS-enheter](vpn-settings-ios.md#base-vpn-settings) innehåller mer information om hur du använder NAC, samt information om vissa ytterligare krav. 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>Veckan som börjar med 5 november 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Stöd för iOS 12 OAuth i iOS-e-postprofiler <!--2155106 -->

Intunes iOS-e-postprofiler stöder iOS 12 Open Authorization (OAuth). Om du vill se den här funktionen skapar du en ny profil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **E-post** för profiltyp) eller uppdaterar en befintlig iOS-e-postprofil. Om du aktiverar OAuth i en profil som redan har distribuerats till användare uppmanas användarna att autentisera på nytt och ladda ned sin e-post igen.

[iOS-e-postprofiler](email-settings-ios.md) innehåller mer information om hur du använder OAuth i en e-postprofil.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Autopilot-stöd för Azure Active Directory-anslutna hybridenheter (förhandsgranskning) <!-- 1048100-->
Du kan nu konfigurera Azure Active Directory-anslutna hybridenheter med hjälp av Autopilot. Enheterna måste vara anslutna till organisationens nätverk för att du ska kunna använda Autopilot-hybridfunktionen. Du hittar mer information under [Distribuera Hybrid Azure Active Directory-anslutna enheter med Intune och Autopilot för Windows](windows-autopilot-hybrid.md).
Den här funktionen kommer att lanseras till hela användarbasen under de närmaste dagarna. Därför kanske du inte kan följa stegen förrän funktionen har distribuerats till ditt konto.

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>Veckan då den 29 oktober 2018 infaller

### <a name="app-management"></a>Apphantering

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Kräv icke-biometrisk PIN-kod efter en angiven tidsgräns <!-- 1506985 -->
Genom att kräva en icke-biometrisk PIN-kod efter en tidsgräns angiven av en administratör förbättras säkerheten för appar som har aktiverats för hantering av mobilprogram (MAM) genom att användningen av biometrisk identifiering för åtkomst till företagets data begränsas av Intune. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Klientappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar. Läs om åtkomstinställningar i [Inställningar för iOS](app-protection-policy-settings-ios.md#access-requirements) och [Inställningar för Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter <!-- 2244713 -->
Du kan skilja kontroll över inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter från att ange identiteten för den registrerade användaren, även kända som UPN (User Principal Name). Administratörer som inte använder IntuneMAMUPN kommer inte att se någon funktionalitetsförändring. När den här funktionen är tillgänglig, bör administratörer som använder IntuneMAMUPN för att styra beteende för dataöverföring på registrerade enheter granska de nya inställningarna och uppdatera sina APP-inställningar efter behov.

#### <a name="windows-10-win32-apps----2617325---"></a>Win32-appar för Windows 10 <!-- 2617325 -->
Du kan konfigurera Win32-appar som ska installeras i användarkontext för enskilda användare och installera appen för alla användare på enheten.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Win32-appar för Windows och PowerShell-skript <!-- 2617330 -->
Slutanvändare behöver inte längre vara inloggade på enheten för att installera Win32-appar eller köra PowerShell-skript. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Felsöka klientappinstallationen <!-- 1363711 -->
Du kan felsöka installationen av klientappar genom att granska kolumnen **Appinstallation** i fönstret **Felsök**. För att visa fönstret **Felsök** i Intune-portalen väljer du **Felsök** under **Hjälp och support**.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Stöd för åtkomstkontroll på nätverk på VPN-klienter för iOS <!-- 1333693 -->
Med den här uppdateringen finns en ny inställning för att aktivera åtkomstkontroll på nätverk (NAC) när du skapar en VPN-profil för Cisco AnyConnect, F5-åtkomst och Citrix SSO för iOS. Den här inställningen tillåter att NAC-ID för enheten inkluderas i VPN-profilen. För närvarande finns det inte några VPN-klienter eller NAC-partnerlösningar som har stöd för detta nya NAC-ID, men vi håller dig informerad via vårt [supportblogginlägg](ttps://aka.ms/iOS12_and_vpn) när det finns.

Om du vill använda NAC, måste du:
1. Välja att tillåta att Intune inkluderar enhets-ID i VPN-profiler
2. Uppdatera din NAC-providers programvara/inbyggda programvara, enligt anvisningarna direkt från din NAC-provider

Information om den här inställningen i en iOS VPN-profil finns i [Lägga till VPN-inställningar på iOS-enheter i Microsoft Intune](vpn-settings-ios.md). Mer information om åtkomstkontrollen för nätverk finns i [Integrering av åtkomstkontroll för nätverk (NAC) med Intune](network-access-control-integrate.md). 

Gäller för: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Ta bort en e-postprofil från en enhet, även om det bara finns en e-postprofil <!-- 1818139 -->
Tidigare gick det inte att ta bort en e-postprofil från en enhet *om* det var den enda e-postprofilen. Detta beteende ändras i och med den här uppdateringen. Nu kan du ta bort en e-postprofil, även om det är den enda e-postprofilen på enheten. Läs mer i informationen om att [lägga till e-postinställningar för enheter med Intune](email-settings-configure.md).

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell-skript och Azure Active Directory <!-- 2309469 -->
PowerShell-skript i Intune kan riktas till säkerhetsgrupper för AAD-enheter.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Ny standardinställning för ”Krav på lösenordstyp” för Android, Android Enterprise<!-- 2649963 -->
När du skapar en ny efterlevnadsprincip (**Intune** > **enhetsefterlevnad** > **principer** > **skapa princip** > **Android** eller **Android Enterprise** för Plattform > Systemsäkerhet), ändras standardvärdet för **krav på lösenordstyp**:

Från: Standard för enheten Till: Minst numeriskt

Gäller för: Android, Android Enterprise

Om du vill se de här inställningarna går du till [Android](compliance-policy-create-android.md) och [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Använda en i förväg delad nyckel i en Wi-Fi-profil för Windows 10 <!-- 2662938 -->
Med den här uppdateringen kan du använda en i förväg delad nyckel (PSK) med säkerhetsprotokollet WPA/WPA2-Personal för att autentisera en Wi-Fi-konfigurationsprofil för Windows 10. Du kan också ange kostnadskonfigurationen för ett avgiftsbelagt nätverk av enheter i Windows-10 oktober 2018-uppdateringen.

För närvarande måste du importera en Wi-Fi-profil eller skapa en anpassad profil för att använda en i förväg delad nyckel. [Wi-Fi-inställningar för Windows 10](wi-fi-settings-windows.md) visar en lista över de aktuella inställningarna. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Ta bort PKCS- och SCEP-certifikat från dina enheter <!-- 3218390 -->
I vissa scenarier fanns PKCS- och SCEP-certifikaten kvar på enheterna, även om du tog bort en princip från en grupp, om du tog bort en konfiguration eller efterlevnadsdistribution eller om en administratör uppdaterade en befintlig SCEP- eller PKCS-profil. Detta beteende ändras i och med den här uppdateringen. Det finns vissa scenarier då PKCS- och SCEP-certifikat tas bort från enheter och vissa scenarier då certifikaten finns kvar på enheten. Mer information om dessa scenarier finns i [Ta bort SCEP- och PKCS-certifikat i Microsoft Intune](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Använda Gatekeeper på macOS-enheter för efterlevnad <!-- 2504381 -->
Den här uppdateringen innehåller macOS Gatekeeper för att utvärdera enheter för kompatibilitet. För att ställa in Gatekeeper-egenskaper, [Lägg till en enhetsefterlevnadsprincip för macOS-enheter](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="enrollment-abandonment-report----1382924---"></a>Rapport över avbrutna registreringar <!-- 1382924 -->
En ny rapport som innehåller information om övergivna registreringar finns tillgänglig under **Enhetsregistrering** > **Övervaka**. Mer information finns i [Företagsportalens lämningsrapport](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Ny funktion för Azure Active Directory-användningsvillkor <!-- 2870393 -->
Azure Active Directory har en funktion för användningsvillkor som du kan använda i stället för de befintliga Intune-villkoren. Funktionen för användningsvillkor i Azure AD ger större flexibilitet över vilka villkor som ska visas och när, bättre lokaliseringsstöd, bättre kontroll över hur villkoren återges och bättre rapportering. Funktionen för användningsvillkor i Azure AD kräver Azure Active Directory Premium P1 som också är en del av programsviten Enterprise Mobility + Security E3. Mer information finns i artikeln [Hantera företagets villkor för användaråtkomst](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Stöd för läget för Android-enhetens ägare <!--3188762-->
För registrering av Samsung Knox-registrering, stöder nu Intune registrering av enheter till läget för hantering av Android-enhetens ägare. Användarna på Wi-Fi eller mobila nätverk kan registrera sig med bara några få tryck när de aktiverar på sina enheter för första gången. Mer information finns i [Registrera Android-enheter automatiskt med hjälp av från Samsung Knox Mobile-registrering](android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Enhetshantering
#### <a name="new-settings-for-software-updates------1907869---"></a>Nya inställningar för programuppdateringar   <!-- 1907869 -->  
- Du kan nu konfigurera att vissa meddelanden aviserar slutanvändarna om de omstarter som krävs för att slutföra installationen av de senaste programuppdateringarna.   
- Du kan nu konfigurera en omstartsvarning vid omstarter som sker utanför arbetstid, vilket har stöd för BYOD-scenarier.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Gruppera Windows Autopilot-registrerade enheter efter korrelator-ID <!-- 2075110 -->
Intune stöder nu gruppering av Windows-enheter med ett korrelator-ID när de har registrerats med hjälp av [Autopilot för befintliga enheter](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) via Configuration Manager. Korrelator-ID:t är en parameter i Autopilot-konfigurationsfilen. Intune matchar automatiskt [Azure AD-enhetsattributet enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) med ”OfflineAutopilotprofile-<correlator ID>”. På så sätt kan godtyckligt dynamiska grupper i Azure AD skapas baserat på korrelator-ID via attributet enrollmentprofileName för Autopilot-offlineregistreringar. Mer information finns i [Windows Autopilot för befintliga enheter](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies----2984657---"></a>Appskyddsprinciper i Intune <!-- 2984657 -->
Med Intune-appskyddsprinciper kan du konfigurera olika dataskyddsinställningar för Intune-skyddade appar, till exempel Microsoft Outlook och Microsoft Word. Vi har ändrat utseendet och känslan för de här inställningarna för både [iOS](app-protection-policy-settings-ios.md) och [Android](app-protection-policy-settings-android.md) för att göra det enklare att hitta individuella inställningar. Det finns tre typer av principinställningar:
- **Dataflytt** – Den här gruppen innehåller kontroller för dataförlustskydd (DLP), såsom begränsningar för klipp ut, kopiera och klistra in och spara som. De här inställningarna avgör hur användarna samverkar med data i apparna.
- **Åtkomstbehörigheter** – Den här gruppen innehåller alternativ för PIN-kod per app som avgör hur slutanvändare får åtkomst till apparna i en arbetskontext.  
- **Villkorlig start** – Den här gruppen innehåller inställningar som lägsta OS-inställningar, uppbrytning och identifiera rotade enheter och offlinerespittid.  
  
Funktionerna i inställningarna ändras inte, men det är lättare att hitta dem när du arbetar i principen för redigering av flödet.

### <a name="intune-apps"></a>Intune-appar

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune kommer att stödja en maximal paketstorlek på 8 GB för verksamhetsspecifika appar <!-- 1727158 -->
Intune ökade den maximala paketstorleken till 8 GB för LOB-appar (Line-of-business). Du hittar mer information i [Lägg till appar i Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Lägga till en anpassad varumärkesbild för företagsportalappen <!-- 1916266 -->
Som Microsoft Intune-administratör kan du ladda upp en anpassad varumärkesbild som visas som bakgrundsbild på användarens profilsida i iOS-företagsportalappen. Mer information om hur du konfigurerar företagsportalappen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune bevarar det lokaliserade språket i Office när Office uppdateras på slutanvändarnas datorer <!-- 2971030 -->
När Intune installerar Office på slutanvändarnas datorer får användarna automatiskt samma språkpaket som de hade med tidigare .MSI Office-installationer. Du hittar mer information i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Ny Intune Support-upplevelse i Microsoft 365-enhetshanteringsportalen <!-- 3076965 -->
Vi lanserar en ny upplevelse för hjälp och support för Intune i [Microsoft 365-enhetshanteringsportalen]( http://devicemanagement.microsoft.com). Med den nya upplevelsen kan du beskriva problemet med egna ord och ta emot felsökningsinsikter och webbaserat åtgärdsinnehåll. De här lösningarna är tillgängliga via en regelbaserad maskininlärningsalgoritm som drivs av användarfrågor.  

Utöver problemspecifika rekommendationer kan du också använda det nya arbetsflödet för att öppna ett supportärende via e-post eller telefon.  

För kunder som är en del av distributionen, ersätter den här nya upplevelsen den aktuella hjälp- och supportupplevelsen av en statisk uppsättning förvalda alternativ som är baserade på området i konsolen du befinner dig i när du öppnar Hjälp och support.  

*Denna nya hjälp- och supportupplevelse distribueras till vissa men inte alla klienter och är tillgänglig i enhetshanteringsportalen. Deltagare i den här nya upplevelsen väljs ut slumpmässigt bland de tillgängliga Intune-klientorganisationerna. Nya klienter läggs till då vi expanderar distributionen.*  

Mer information finns i [Hjälp- och supportupplevelse](get-support.md#help-and-support-experience) i Ta reda på hur du kan få support för Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>PowerShell-modul för Intune – en förhandsversion är tillgänglig <!-- 951068 -->
Nu finns en ny PowerShell-modul, som har stöd för Intune-API:et via Microsoft Graph, tillgänglig som en förhandsversion på [GitHub]( https://aka.ms/intunepowershell). Mer information om hur du använder den här modulen finns i Viktigt-filen på den platsen. 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>Veckan då den 15 oktober 2018 infaller

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Ange PIN-kod när du ändrar fingeravtryck eller ansikts-ID på en iOS-enhet  <!-- 2637704  -->
Nu uppmanas användarna att ange en PIN-kod när de gör biometriska ändringar på sin iOS-enhet. Detta omfattar ändringar i registrerade fingeravtryck eller ansikts-ID. Tidsinställningen för uppmaningen beror på hur konfigurationen av *Kontrollera åtkomstkraven efter (minuter)* löper ut.  När ingen PIN-kod har angetts, uppmanas användaren att skapa en. 
 
Den här funktionen är endast tillgänglig för iOS och kräver medverkan av program som integrerar Intune APP SDK för iOS, version 9.0.1 eller senare. Integrering av SDK krävs så att beteendet kan tillämpas på de berörda programmen. Den här integreringen händer på löpande bas, och är beroende av specifika programteam. Vissa appar som deltar omfattar WXP, Outlook, Managed Browser och Yammer.


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>Veckan då den 1 oktober 2018 infaller

### <a name="app-management"></a>Apphantering

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Åtkomst till viktiga profilegenskaper med hjälp av företagsportalappen <!-- 772203 -->
Slutanvändare kan nu komma åt viktiga egenskaper och åtgärder, till exempel lösenordsåterställning, från företagsportalappen. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Tangentbord från tredje part kan blockeras via APP-inställningarna i iOS <!-- 1248481 -->
Intune-administratörer kan blockera användningen av tredjepartstangentbord på iOS-enheter vid åtkomst till organisationens data i skyddade appar. När APP (Application Protection Policy) är inställt på att blockera tredjepartstangentbord visas ett meddelande första gången användaren interagerar med företagsdata och använder ett tredjepartstangentbord. Alla alternativ förutom det interna tangentbordet är blockerade och visas inte för användaren. Enhetsanvändarna ser bara det här meddelandet en gång. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Åtkomst till användarkonto för Intune-appar på hanterade Android- och iOS-enheter <!-- 1248496 -->
Som Microsoft Intune-administratör kan du styra vilka användarkonton som läggs till i Microsoft Office-program på hanterade enheter. Du kan begränsa åtkomsten till endast tillåtna användarkonton i organisationen och blockera personliga konton på registrerade enheter. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Appkonfigurationsprincip för Outlook iOS och Android <!--1828527 -->
Du kan nu skapa en Outlook-iOS och Android-appkonfigurationsprincip för iOS och Android för lokala användare som använder grundläggande autentisering med ActiveSync-protokollet. Ytterligare konfigurationsinställningar läggs till vartefter de aktiveras för Outlook för iOS och Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Språkpaket för Office 365 Pro Plus <!-- 1833450 -->
Som Intune-administratör kan du distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Gå till Azure Portal och välj **Microsoft Intune** > **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** på bladet **Lägg till app** väljer du **Windows 10** under **Office 365 Suite**. Välj **Språk** på bladet **Inställningar för appsviten**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Filnamnstillägg för verksamhetsspecifika Windows-appar (LOB) <!-- 1884873 -->
Filnamnstillägg för verksamhetsspecifika Windows-appar omfattar nu *.msi*, *.appx*, *.appxbundle*, *.msix* och *.msixbundle*. Du kan lägga till en app i Microsoft Intune genom att välja **Klientappar** > **Appar** > **Lägg till**. Fönstret **Lägg till app** visas och där du kan välja **Apptyp**. För LOB-appar på Windows väljer du **Verksamhetsspecifik app** som apptyp, väljer **Appaketfil** och anger sedan en installationsfil med rätt filnamnstillägg.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Distribution av Windows 10-appar med hjälp av Intune <!-- 2309001 -->
Genom att bygga vidare på det befintliga stödet för verksamhetsspecifika appar och appar för Microsoft Store för företag kan administratörer använda Intune för att distribuera de flesta av organisationens befintliga program till slutanvändare på Windows 10-enheter. Administratörer kan lägga till, installera och avinstallera program för Windows 10-användare i flera olika format, till exempel MSI, Setup.exe eller MSP. Intune utvärderar regler för krav innan nedladdningen och installationen, och meddelar slutanvändarna om statusen eller krav på omstart via Åtgärdscenter för Windows 10. Den här funktionen hjälper organisationer som vill flytta den här arbetsbelastningen till Intune och molnet. Den här funktionen är för närvarande tillgänglig som en offentlig förhandsversion. Vi planerar att introducera många nyheter i funktionen under de kommande månaderna. 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>APP-inställningar (App Protection Policy) för webbdata <!-- 2662995 -->
Principinställningarna för webbinnehåll på både Android och iOS-enheter kommer att uppdateras så att de blir bättre på att hantera både http- och https-länkar liksom dataöverföring via universella iOS-länkar och Android App-länkar. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Slutanvändarenhet och appinnehållsmenyn <!-- 2771453 -->
Slutanvändare kan nu använda snabbmenyn på enheter och appar för att utlösa vanliga åtgärder som att byta namn på en enhet eller kontrollera efterlevnad. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Kortkommandon för Windows-företagsportalen <!-- 2771518 -->
Slutanvändare kan nu utlösa app- och enhetsåtgärder i Windows-företagsportalen med hjälp av kortkommandon (acceleratorer).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Skapa DNS-suffix i VPN-konfigurationsprofiler på enheter som kör Windows 10<!-- 1333668 -->
När du skapar en profil för VPN-enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  plattform: **Windows 10 och senare** > profiltyp: **VPN**), anger du vissa DNS-inställningar. Med den här uppdateringen kan du även ange flera **DNS-suffix** i Intune. När du använder DNS-suffix, kan du söka efter en nätverksresurs med dess korta namn i stället för det fullständiga domännamnet (FQDN). I och med den här uppdateringen kan du ändra ordningen på DNS-suffix i Intune.
[Windows 10-VPN-inställningar](vpn-settings-windows-10.md#dns-settings) visar en lista över aktuella DNS-inställningar.
Gäller för: Windows 10-enheter

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Stöd för AlwaysOn-VPN för Android Enterprise-arbetsprofiler <!-- 1333705 -->
I den här uppdateringen kan du använda VPN-anslutningar som alltid är aktiva på Android-företagsenheter med hanterade arbetsprofiler. Ständiga VPN-anslutningar förblir anslutna eller återansluter omedelbart när användaren låser upp sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. Du kan också placera anslutningen i ”låst” läge, vilket blockerar all nätverkstrafik tills VPN-anslutningen aktiveras.
Du kan aktivera VPN-anslutningar som alltid är aktiva i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android-företag** för plattform > **Enhetsbegränsningar** > **Anslutningar**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Utfärda SCEP-certifikat till användarlösa enheter <!-- 1744554 -->
För närvarande utfärdas certifikat till användare. Med den här uppdateringen kan SCEP-certifikat utfärdas till enheter, inklusive användarlösa enheter som informationsdatorer (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **SCEP-certifikat** för profil). Exempel på andra uppdateringar är:
- Egenskapen **Ämne** i en SCEP-profil är nu en anpassad textruta och kan innehålla nya variabler. 
- Egenskapen **Alternativt namn för certifikatmottagare (SAN)** i en SCEP-profil är nu i tabellformat och kan innehålla nya variabler. I tabellen kan en administratör lägga till ett attribut och fylla i värdet i en anpassad textruta. SAN stöder följande attribut: 
  - DNS
  - E-postadress
  - UPN

  Dessa nya variabler kan läggas till med statisk text i en textruta för anpassat värde. Till exempel DNS-attributet kan läggas till som `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Klammerparenteser { }, semikolon ; och vertikalstreck | fungerar inte i den statiska texten för SAN. Klammerparenteser får endast omfatta en av de nya variablerna för enhetscertifikat för antingen `Subject` eller `Subject alternative name`. 

Nya variabler för enhetscertifikat:  

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

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Fjärrlåsa enheter som inte är kompatibla <!-- 2064495 -->
När en enhet inte är kompatibel kan du skapa en åtgärd i efterlevnadsprincipen som fjärrlåser enheten. I Intune > **Enhetskompatibilitet** skapar du en ny princip eller väljer en befintlig princip > **Egenskaper**. Välj **Åtgärder vid inkompatibilitet** > **Lägg till** och välj att fjärrlåsa enheten.
Stöds på: 
- Android
- iOS
- macOS
- Windows 10 Mobil 
- Windows Phone 8.1 och senare 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Profilförbättringar för informationsdatorer med Windows 10 och senare i Azure-portalen <!-- 2748224 -->
Den här uppdateringen innehåller följande förbättringar i konfigurationsprofilen för Windows 10-informationsenheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Helskärm (förhandsgranskning)** för profiltyp): 
- För närvarande kan du skapa flera informationsdatorprofiler på samma enhet. I och med den här uppdateringen stöder Intune endast en informationsdatorprofil per enhet. Om du fortfarande behöver flera informationsdatorprofiler på en enskild enhet kan du använda en anpassad URI.
- I en profil för **informationsdator med flera appar** kan du välja programikonernas storlek och ordning i **Startmenylayout** i programrutnätet. Om du vill anpassa mera, kan du ladda upp en XML-fil.
- Inställningarna för webbläsare för informationsdator flyttas till inställningarna för **Informationsdator**. För närvarande har inställningarna för **Webbläsare för informationsdator** sin egen kategori i Azure Portal.
Gäller för: Windows 10 och senare




### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Tillämpa Autopilot-profil på registrerade Windows 10-enheter som inte redan har registrerats för Autopilot <!-- 1558983 -->
Du kan använda Autopilot-profiler för registrerade Windows 10-enheter som inte redan har registrerats för Autopilot. I Autopilot-profilen väljer du alternativet **Omvandla alla målenheter till Autopilot** för att automatiskt registrera andra än Autopilot-enheter med Autopilot-distributionstjänsten. Det kan ta upp till 48 timmar för registreringen att bearbetas. Autopilot konfigurerar enheten efter att den har avregistrerats och återställts.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Skapa flera profiler för sidan för registreringsstatus och tilldela dem till Azure AD-grupper <!-- 2526564 -->
Nu kan du [skapa](windows-enrollment-status.md) flera profiler för sidan för registreringsstatus och tilldela dem till Azure AD-grupper.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migrering från programmet för enhetsregistrering till Apple Business Manager i Intune <!--2748613-->
Apple Business Manager (ABM) fungerar i Intune och du kan uppgradera ditt konto från program för enhetsregistrering (DEP) till ABM. Processen i Intune är samma. Om du vill uppgradera ditt Apple-konto från DEP till ABM, gå till [ https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Statusflikar för avisering och registrering på översiktssidan för enhetsregistrering <!--2748656-->
Aviseringar och registreringsfel visas nu på separata flikar på översiktssidan för enhetsregistrering.

### <a name="device-management"></a>Enhetshantering

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Begränsa appar och blockera åtkomsten till företagsresurser på Android-enheter <!-- 2451462  -->  
I **Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Android**  >  **Systemsäkerhet** finns det en ny inställning under avsnittet *Enhetssäkerhet* med namnet **Begränsade appar**. Inställningen **Begränsade appar** använder en efterlevnadsprincip för att blockera åtkomsten till företagsresurser om vissa appar installeras på enheten. Enheten betraktas som icke-kompatibel tills de begränsade apparna tas bort från enheten.
Gäller för: 
- Android

<!-- ########################### -->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
