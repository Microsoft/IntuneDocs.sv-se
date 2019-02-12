---
title: Tidig utgåva – Microsoft Intune
titlesuffix: ''
description: Tidig utgåva av Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: d50925d9f5422e1bfea01869233c63d6a2889109
ms.sourcegitcommit: 12f8b7f0bca1baa2c1f68dd6af4f16a4814daa11
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737510"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Den tidiga utgåvan för Microsoft Intune – Januari 2019

> [!Note]
> Sekretessavtalsmeddelande: Följande ändringar är under utveckling för Intune. Den här informationen har mycket begränsad spridning, i enlighet med sekretessavtalet. Sprid inte den här informationen vidare på sociala medier eller offentliga webbplatser, till exempel Twitter, UserVoice, Reddit och så vidare. 

Den **tidiga utgåvan** innehåller en lista med funktioner, som delas i enlighet med sekretessavtalet, som ingår i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte den här informationen på Twitter, UserVoice eller på något annat sätt med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>PowerShell-skript kan köras på en 64-bitarsvärd på 64-bitarsenheter <!-- 1862675  -->
När du lägger till ett PowerShell-skript i en enhetskonfigurationsprofil körs skriptet alltid i 32 bitar, även på 64-bitars operativsystem. Med den här uppdateringen kan en administratör köra skriptet på en 64-bitars PowerShell-värd på 64-bitarsenheter (**Enhetskonfiguration** > **PowerShell-skript** > **Lägg till** > **Konfigurera** > **Kör skript i 64-bitars PowerShell-värd**).
Mer information om användning av PowerShell finns i [PowerShell-skript i Intune](intune-management-extension.md).
Gäller för: Windows 10 och senare

### <a name="rename-an-enrolled-windows-device----1911112----"></a>Byta namn på en Windows-enhet <!-- 1911112  -->
Du kan byta namn på en registrerad Windows 10-enhet (RS4 eller senare). Det kan göra så här: välj **Intune** > **Enheter** > **Alla enheter** > välj en enhet > **Byt namn på enhet**.

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>Tilldela SCEP-certifikat till en användarlös macOS-enhet    <!-- 2340521   -->
Du kan tilldela SCEP-certifikat (Simple Certificate Enrollment Protocol) till en användarlös macOS-enhet och associera certifikatet med Wi-Fi- eller VPN-profiler. Detta är en utökning av den befintliga support vi redan har för att [tilldela certifikat till användarlösa enheter som kör Windows, iOS och Android](certificates-scep-configure.md#create-a-scep-certificate-profile).

### <a name="intune-conditional-access-ui-update------2432313----"></a>Uppdatering av användargränssnittet i Intune för villkorlig åtkomst   <!-- 2432313  -->
Vi gör förbättringar av användargränssnittet för villkorlig åtkomst i Intune-konsolen. Dessa omfattar:
- Ersätt bladet *Villkorlig åtkomst* i Intune med bladet från Azure Active Directory. På så sätt har du åtkomst till alla inställningar och konfigurationer för villkorlig åtkomst som fortfarande är en Azure AD-teknik.
- Byta plats på inställningen *Exchange-tjänstanslutning* till det som nu är bladet *Lokal åtkomst*. Vi byter även namn på det bladet till *Exchange-åtkomst*. Ändringen konsoliderar där du konfigurerar och övervakar information relaterad till Exchange online och lokalt.

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Intune använder Google Play Protect-API:er på Android-enheter <!-- 2577355  -->
Vissa IT-administratörer hanterar en BYOD-miljö där slutanvändare kan rota eller jailbreaka sin mobiltelefon. Även om beteendet inte är illa menat blir resultatet att det kringgår många Intune-principer som har angetts för att skydda organisationens data och slutanvändarenheter. Därför har Intune rot- och jailbreak-identifiering för både registrerade och oregistrerade enheter. Med den här versionen använder Intune nu Google Play Protect-API:er som tillägg till våra befintliga rotidentifieringskontroller för oregistrerade enheter. Google delar inte alla rotidentifieringskontroller som sker men vi förväntar oss att dessa API:er kan identifiera användare som har rotat sina enheter av någon anledning från enhetsanpassning för att kunna få nyare OS-uppdateringar på äldre enheter. Dessa användare kan sedan blockeras från åtkomst till företagsdata eller så kan deras företagskonton rensas bort från deras principaktiverade appar. Ett ytterligare mervärde är att IT-administratören nu har flera rapporteringsuppdateringar på bladet Intune-appskydd – rapporten ”Flaggade användare” visar vilka användare som identifieras via SafetyNet API-genomsökningen från Google Play Protect, rapporten ”Potentiellt skadliga appar” visar vilka appar som identifieras via Googles Verify Apps API-genomsökning. Den här funktionen är tillgänglig på Android. 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>Win32-appinformation tillgänglig på bladet Felsökning <!-- 2617342    -->
Du kan samla in felloggfiler för en Win32-appinstallation från Intune-appens blad **Felsökning**. Mer information om felsökning av appinstallationer finns i [Felsöka appinstallationsproblem](troubleshoot-app-install.md).

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>Kiosk Browser och Microsoft Edge-webbläsaren kan köras på Windows 10-enheter i helskärmsläge <!-- 2935135  -->
Du kan använda Windows 10-enheter i helskärmsläge för att köra en app eller flera appar. Den här uppdateringen omfattar flera ändringar av att använda webbläsare i helskärmsläge, inklusive:

- Lägg till webbläsaren Microsoft Edge eller Kiosk Browser att köras som appar på en helskärmsenhet (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **Windows 10 och senare** som plattform > **Helskärm** som profiltyp).
- Begränsa Microsoft Edge så att den kan (eller inte kan) köras i helskärmsläge (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **Windows 10 och senare** som plattform > **Enhetsbegränsningar** som profiltyp > **Microsoft Edge-webbläsare**). När Microsoft Edge inte körs i helskärmsläge kan inställningarna ändras av slutanvändare.

Se följande för en lista över aktuella inställningar:

- [Inställningar för enheter med Windows 10 (och senare) som ska köras med helskärmsläge](kiosk-settings-windows.md)
- [Enhetsbegränsningar för Microsoft Edge-webbläsaren](device-restrictions-windows-10.md#microsoft-edge-browser)

Gäller för: Windows 10 och senare

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Tilldela automatiskt omfångstaggar till resurser skapade av en administratör med det omfånget <!-- 3173823  -->
När en administratör skapar en resurs tilldelas alla omfångstaggar som tilldelats till administratören automatiskt till dessa nya funktioner.

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>Nya inställningar för enhetsbegränsning för iOS- och macOS-enheter <!-- 3448774 -->
Du kan begränsa vissa inställningar och funktioner på enheter som kör iOS och macOS (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** eller **macOS** som plattform > **Enhetsbegränsningar** som profiltyp). Den här uppdateringen lägger till fler funktioner och inställningar som du kan kontrollera, till exempel ange skärmtid, ändra eSIM-inställningar och mobilabonnemang, fördröja användarens visning av programuppdateringar, blockera innehållscachelagring med mera.
Aktuella funktioner och inställningar du kan begränsa finns här:
- [Inställningar för iOS-enhetsbegränsning](device-restrictions-ios.md)
- [Inställningar för macOS-enhetsbegränsning](device-restrictions-macos.md)

Gäller för:
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>Rapport över misslyckad registrering flyttas till bladet Enhetsregistrering <!-- 3560202 -->
Rapporten **Misslyckade registreringar** flyttas till avsnittet **Övervaka** på bladet **Enhetsregistrering**. Två nya kolumner (Registreringsmetod och Operativsystemversion) läggs också till.

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>Ändra ”Helskärm” till ”Särskilda enheter” <!-- 3598402  -->
För att anpassa terminologin efter Android ändras **Helskärm** till **Särskilda enheter** under Profiler för enhetskonfigurationer, **Android enterprise** > **Enhetens ägare** > **Enhetsbegränsningar**.

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>Safari och iOS-inställningarna för att fördröja visning av programuppdateringar för användaren flyttas i Intune-användargränssnittet <!-- 3640850, , 3803313  -->
För iOS-enheter kan du ange Safari-inställningar och konfigurera programuppdateringar. I den här uppdateringen flyttas dessa till olika delar av Intune-användargränssnittet:

- Safari-inställningarna flyttas från **Safari** (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** som plattform > **Enhetsbegränsningar** som profiltyp) till **Inbyggda appar**. 
- Inställningen för att **fördröja visning av programuppdateringar för användaren för övervakade iOS-enheter** (**Programuppdateringar** > **Uppdatera principer för iOS**) flyttas till **Enhetsbegränsningar** > **Allmänt**.

En lista över de aktuella inställningarna finns i [Enhetsbegränsningar för iOS](device-restrictions-ios.md) och [Programuppdateringar för iOS](software-updates-ios.md).

Gäller för: 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>Aktivera begränsningar i enhetsinställningarna byter namn till Skärmtid på iOS-enhet <!-- 3699164  -->
Du kan konfigurera **Aktivera begränsningar i enhetsinställningarna** på övervakade iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** som plattform > **Enhetsbegränsningar** som profiltyp > **Allmänt**). I den här uppdateringen har den här inställningen bytt namn till **Skärmtid (endast övervakat)**. Beteendet är samma. Specifikt: 

- iOS 11.4.1 och tidigare: **Blockera** förhindrar slutanvändare att ange egna begränsningar i enhetsinställningarna. 
- iOS 12.0 och senare: **Blockera** förhindrar slutanvändare att ange en egen **skärmtid** i enhetsinställningarna, som innehålls- och sekretessbegränsningar. Fliken för begränsningar visas inte längre på enheter uppgraderade till iOS 12.0. Dessa inställningar finns i **Skärmtid**. 

En lista över de aktuella inställningarna finns i [Enhetsbegränsningar för iOS](device-restrictions-ios.md).

Gäller för: 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>Appstatusinformation för iOS-appar <!-- 3761235  -->
Det blir nya felmeddelanden för appinstallationer som rör följande:
- Fel för VPP-appar vid installation på delad iPad
- Fel när App Store är inaktiverad
- Fel vid sökning efter VPP-licensen för appen
- Fel vid installation av systemappar med MDM-provider
- Fel vid installation av appar när enheten är i borttappat läge eller helskärmsläge
- Fel vid installation av app när användaren inte är inloggad i App Store

I Intune väljer du **Klientappar** > **Appar** > ”appens namn” > **Installationsstatus för enhet**. Nya felmeddelanden kommer att finnas i kolumnen **Statusinformation**.

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Distribution av online-licensierade Microsoft Store för företag-appar <!-- 1672660  -->
Du kommer att kunna tilldela nödvändiga online-licensierade Microsoft Store för företag-appar i kontexten för enheten. Genom att distribuera en Microsoft Store för företag-app på detta sätt, kan appen installeras för alla användare på enheten. Detta gäller endast för Windows 10 RS4+ desktop-enheter. Alternativet att installera i kontexten för enheten finns på sidan Tilldelning av klientappar för MSFB Online-licensierade appar.

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Appdistribution för Android Enterprise APP-WE <!-- 1171203 -->
För Android-enheter i ett distributionsscenario med en appskyddsprincip utan registrering (APP-WE) kommer du att kunna använda hanterade Google Play för att distribuera store-appar och LOB-appar till användare. Mer specifikt kan IT-avdelningen kan ge slutanvändarna en app-katalog och installationsupplevelse som inte längre kräver att slutanvändare minskar säkerhetspositionen för sina enheter genom att tillåta installationer från okända källor. Dessutom kan det här distributionsscenariot ge en förbättrad slutanvändarupplevelse.

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Uppdatering av Intune-principers autentiseringsmetod och installation av företagsportalappen  <!-- 1927359 -->
På enheter som redan har registrerats via Installationsassistenten med någon av Apples metoder för registrering av företagsenheter, stöder Intune inte längre företagsportalen om den installeras manuellt av slutanvändarna från App Store. Den här ändringen gäller endast när du autentiserar med Apple-installationsassistenten under registreringen. Den här ändringen påverkar också bara iOS-enheter som registrerats via:  
* Apple configurator
* Apple Business Manager
* Apple School Manager
* Apples program för enhetsregistrering (DEP)

Om användare installerar företagsportalappen från App store och sedan försöker att registrera enheterna genom den, får de ett felmeddelande. Dessa enheter kommer förväntas att bara använda företagsportalen när den har skickats automatiskt av Intune under registreringen. Profiler för registrering i Intune i Azure-portalen kommer att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Om du vill att dina DEP-enhetsanvändare ska ha företagsportalen behöver du ange dina preferenser i en registreringsprofil. Dessutom kommer skärmen **Identifiera din enhet** i företagsportalappen snart att bli föråldrad.  
För att installera företagsportalen på redan registrerade DEP-enheter, måste du gå till Intune > Klientappar, och skicka den som en hanterad app med konfigurationsprinciper för appar. Information om hur du utför dessa steg kommer att ges i framtida dokument.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrativa mallar finns i offentlig förhandsversion och flyttas till deras egna konfigurationsprofil <!-- 3322847 -->
Administrativa mallar i Intune (**Enhetskonfiguration** > **Administrationsmallar**) är för tillfället i privat förhandsvisning. I denna uppdatering: De administrativa mallarna innehåller ungefär 300 inställningar som kan hanteras i Intune. De här inställningarna fanns tidigare endast i redigeraren.
Administrativa mallar finns i offentlig förhandsversion, administrativa mallar flyttar från **Enhetskonfiguration** > **Administrationsmallar** till **Enhetskonfiguration** > **Profiler** >**Skapa profil** > i **Plattform**, välj **Windows 10 och senare**i **Profiltyp**, välj **Administrationsmallar**.
Rapportering är aktiverad och gäller för: Windows 10 och senare

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Mörkt läge i Intune macOS-företagsportalen <!-- 3300524 -->
Nu stöder Intune macOS-företagsportalen mörkt läge för macOS. När du aktiverar mörkt läge på en macOS 10.14 +-enhet kommer företagsportalen att justera dess utseende till färger som speglar detta läge.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>APP-inställningar (App Protection Policy) för webbdata <!-- 2662995 -->
Principinställningarna för webbinnehåll på både Android och iOS-enheter kommer att uppdateras så att de blir bättre på att hantera både http- och https-länkar liksom dataöverföring via universella iOS-länkar och Android App-länkar.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-token som används av en annan MDM <!-- 1488946 -->
Intune identifierar och visar information om en token för volyminköpt Apple-program (VPP) används av både Intune och en annan MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Tillbakadragna enheter i instrumentpanelen för enhetsefterlevnad <!-- 1981119 -->
I en kommande uppdatering tas tillbakadragna enheter bort från instrumentpanelen för enhetsefterlevnad. Detta ändrar dina efterlevnadsnummer.

## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).