---
title: Under utveckling - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa38a684a32756d4f2c3be3b750f8e79b66e98f6
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587390"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>Under utveckling för Microsoft Intune – April 2019

För att hjälpa din beredskap och planering, den här sidan visar Intune UI-uppdateringar och funktioner som är under utveckling, men ännu inte släppts. Dessutom:

- Om vi tror att du måste vidta åtgärder innan en ändring, publicerar vi ett kompletterande meddelandecenter för Office-inlägg.
- När en funktion har startats i produktion, antingen som en förhandsversion eller allmänt tillgänglig, funktionsbeskrivningen och kommer att flyttas ut den här sidan till den [nyheter](whats-new.md).
- Den här sidan och [nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Referera till den [M365-översikt](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) för strategiska mål och tidslinjer.

> [!Note]
> Dessa objekt visas Microsofts aktuella förväntningar om Intune-funktioner som kommer i en framtida version. Datum och enskilda funktioner kan ändras. Inte alla objekt i utveckling har en funktionsbeskrivning på den här sidan.

**RSS-feed**: Håll dig informerad när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Ange inställningarna för inloggning och styra omstartsalternativ på macOS-enheter <!-- 1210083 -->
På macOS-enheter, kan du skapa en profil för enhetskonfiguration (**enhetskonfiguration** > **profiler** > **skapa profil** > Välj **macOS** för plattform > **enhetsfunktioner** för Profiltyp). Ny inloggning fönstret inställningar ingår objekt, till exempel som visar en anpassad banderoll, Välj hur användare logga in, visa eller dölja energiinställningarna och så vidare.

Om du vill visa de aktuella inställningarna går du till [macOS inställningar för enhetsfunktioner](macos-device-features-settings.md).

Gäller för: macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Avancerade inställningar för Windows Defender-brandväggen <!-- 1311949 -->
Du kommer snart att kunna använda Intune för att hantera anpassade brandväggsregler på klienter för Windows Defender. Regler kan ange beteendet för inkommande och utgående till program, adresser i nätverket och portar. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Kräv App Protection villkorlig åtkomst  <!--1634317 -->
Du kommer att kunna använda *kräver appskyddsprincip*, vilket bekräftar att principen tillämpas på en användares app innan inloggningen är klar för att hindra användare från att komma åt data som du skyddar med villkorlig åtkomst. När principen assurance kan sakta ned den första användning-upplevelsen, hjälper dig för att skydda mot nätverksproblem, administrativa felkonfigurationer eller avsiktligt arbete med att här principer för programskydd. 

### <a name="retire-noncompliant-devices----1827291---"></a>Ta bort icke-kompatibla enheter <!-- 1827291 -->
Vi ska lägga till en ny åtgärd för att dra tillbaka en inkompatibel enhet. Ta bort en inkompatibel enhet tar bort alla företagsdata från den och tar också bort enheten från att hanteras av Intune. Den här åtgärden körs när det konfigurerade värdet i dagar har uppnåtts. Minsta värde är 30 dagar. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Konfigurera inställningarna för kernel-tillägg på macOS-enheter <!-- 2043024 -->
På macOS-enheter, kan du skapa en profil för enhetskonfiguration (**enhetskonfiguration** > **profiler** > **skapa profil** > Välj **macOS** för plattform). En ny grupp med inställningar kan du konfigurera och använda kernel-tillägg på dina enheter.

Gäller för: macOS 10.13.2 och senare

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Konfigurera profilen om du vill hoppa över vissa av skärmarna i installationsassistenten <!-- 2276470 -->
När du skapar en macOS-registreringsprofil kommer du att kunna konfigurera den för att hoppa över valfria följande skärmar när en användare går igenom installationsassistenten:
- Android-migrering
- Visningston
- Sekretess
- iCloudStorage Om du skapar en ny profil eller redigerar en profil måste den valda överhoppningsskärmen synkroniseras med Apple MDM-servern. Användare kan utfärda en manuell synkronisering av enheterna så att det inte sker någon fördröjning i att plocka upp profiländringarna.
Mer information finns i [Registrera macOS-enheter automatiskt med programmet för enhetsregistrering eller Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Användare av enheter kan visa alla hanterade appar som de har installerats eller försökt att installera <!-- 2352913 -->
Företagets Portal för Windows visas en lista över alla hanterade appar&ndash; både nödvändig och tillgänglig&ndash; som är installerade på en användares enhet. Användare kommer att kunna visa försökt och väntande installationer av appar och deras aktuella status. Om din organisation inte gör appar obligatorisk eller tillgänglig, ser användarna ett meddelande som förklarar att inga appar har installerats. Användare kommer också att kunna sortera eller filtrera appar efter installationsstatus.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Omfångstaggar för Apple VPP-token <!--2371886 -->
Du kommer att kunna lägga till omfångstaggar i Apple VPP-token. Endast användare som har tilldelats med samma omfångstaggen får åtkomst till Apple VPP-token med taggen. Ärver dess omfångstaggar VPP-appar och e-böcker som köpts med denna token. Läs mer om omfångstaggar [RBAC för användning och omfång taggar](scope-tags.md).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Använd ”tillämplighetsregler” när skapa profiler för enhetskonfiguration för Windows 10-enhet <!-- 2549910 -->
Du skapar Windows 10-enhet konfigurationsprofiler (**enhetskonfiguration** > **profiler** > **skapa profil**  >  **Windows 10** för plattform). Du kommer att kunna skapa en **tillämpningsregel** så profilen gäller endast för en viss version eller en specifik version. Exempelvis kan skapa du en profil som gör att vissa BitLocker-inställningar. När du lägger till profilen som Använd en tillämpningsregel så profilen gäller endast för enheter som kör Windows 10 Enterprise.

Gäller för: 
- Windows 10 och senare

### <a name="enable-win32-app-dependencies----2617348---"></a>Aktivera Win32-programberoenden <!-- 2617348 -->
Offentlig förhandsversion – som administratör kan du kommer att kunna kräva att andra appar installeras som beroenden innan du installerar Win32-app. Mer specifikt måste installeras på enheten beroende appar innan den installerar Win32-app. Den här funktionen är tillgänglig endast när hanteringsagenten som Intune har uppgraderats till 1904-version (större än 1.18.120.0) som kan ta 1 eller 2 ytterligare veckor efter det att vi uppgradera tjänsten till 1904. I Intune, väljer **klientappar** > **appar** > **Lägg till** att visa den **Lägg till app** bladet. Välj **Windows-app (Win32)** som den **apptyp**. Mer information finns i [Intune Standalone - Win32-apphantering](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Ny enhet begränsningsinställningen för Android-företag, enhetens ägare: låter användarna att ansluta till Wi-Fi-nätverk på Android-företagsenheter dedikerade enheter som kör helskärmsläge för flera appar <!--3041940 -->
Administratörer kommer att kunna växla mellan en ny inställning som användarna kan konfigurera Bluetooth på sina Android-företagsenheter dedikerade enheter som kör helskärmsläge för flera appar. Om du vill se den här inställningen i Intune-konsolen, Välj **Intune** > **enhetskonfiguration** > **profiler**  >  **Skapa profil** > Välj **Android Enterprise** för plattform > **endast enhetens ägare, enhetsbegränsningar** för Profiltyp > **inställningar**   >  **Särskilda enheter** > Välj **flerappsläge** från den **helskärmsläge** inställningen nedrullningsbar listruta. Ett alternativ kallas **Wi-Fi konfiguration** kommer att kunna aktivera. 

Gäller för: Android Enterprise dedikerade enheter som kör helskärmsläge för flera appar. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Ny enhet begränsningsinställningen för Android-företag, enhetens ägare: låta användare konfigurera Bluetooth och koppla ihop på Android-företagsenheter dedikerade enheter <!--3041941 -->
Administratörer kommer att kunna växla mellan en ny inställning som användarna kan konfigurera Bluetooth på sina Android-företagsenheter dedikerade enheter som kör helskärmsläge för flera appar. Om du vill se den här inställningen i Intune-konsolen, Välj **Intune** > **enhetskonfiguration** > **profiler**  >  **Skapa profil** > Välj **Android Enterprise** för plattform > **endast enhetens ägare, enhetsbegränsningar** för Profiltyp > **inställningar**   >  **Särskilda enheter** > Välj **flerappsläge** från den **helskärmsläge** inställningen nedrullningsbar listruta. Ett alternativ kallas **Bluetooth configuration** kommer att kunna aktivera. 

Gäller för: Android Enterprise dedikerade enheter som kör helskärmsläge för flera appar. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Övervaka status för Säkerhetsbaslinje (offentlig förhandsversion) <!-- 3082047 --> 
När du övervakar den *Enhetsstatus* för baslinjer för säkerhet vyn ordnar status efter baslinje-kategorier som *låst*, *BitLocker*, och  *Webbläsaren*. Alla tillgängliga baslinje kategorier kommer att representeras. För varje kategori ser du hur många enheter inte matchar en specifik baslinje-kategori, är felkonfigurerad eller kan inte användas.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Intune säkerhetsuppgifter för Defender ATP (i allmänt tillgänglig förhandsversion) <!-- 3208597 -->
Kommer som en offentlig förhandsversion, Intune snart lägger till säkerhetsuppgifter för den nyss presenterade Microsoft Defender Threat & Sårbarhetshantering.  Säkerhetsadministratörer för operations i Windows Defender ATP (WDATP) med den här integreringen kan mer effektivt kommunicera rekommenderade reparationer för nya hot till Intune-administratörer. Tillägg av säkerhetsuppgifter lägger till en riskbaserad metod för att identifiera, prioritera och åtgärda säkerhetsproblem med slutpunkt och felkonfigurationer.

Mer information om säkerhetsuppgifter i Intune finns i blogginlägget om [använda Intune security uppgifter för att utöka Microsoft Defender ATP hot och hantering av sårbarhet](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Skapa och använda OEMConfig profiler för enhetskonfiguration i Intune <!-- 3305883 -->
Intune stöder konfigurera Android-företagsenheter med OEMConfig. Mer specifikt kan du kan skapa en profil för enhetskonfiguration och Använd inställningar för Android-företagsenheter med OEMConfig (**enhetskonfiguration** > **profiler**  >  **Skapa profil** > **Android enterprise** för plattform).

Stöd för OEM-tillverkare är för närvarande på basis av per OEM. Om en OEMConfig-app som du vill inte finns i listan över OEMConfig appar kan du kontakta `IntuneOEMConfig@microsoft.com`.

Gäller för: 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Inställningar för enhetsbegränsningar för Android-företag, enhetens ägare <!-- 3574254 -->
Du kan skapa en profil för enhetsbegränsningar för att tillåta eller begränsa funktioner och ange regler för lösenord på Android-företagsenheter (**enhetskonfiguration** > **profiler**  >  **Skapa profil** > Välj **Android Enterprise** för plattform > **endast enhetens ägare > enhetsbegränsningar** för Profiltyp). 

Nya inställningar, inklusive inställningar för lösenord, vilket gör att fullständig åtkomst till appar i Google Play Store för fullständigt hanterade enheter och information blir tillgänglig. 

Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](device-restrictions-android-for-work.md). 

Gäller för: Android Enterprise fullständigt hanterade enheter

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Sök efter en TPM-kretsuppsättning i en efterlevnadsprincip för Windows 10-enheter <!-- 3617671 -->
Många Windows 10 och senare enheter har kretsuppsättningar Trusted Platform Module (TPM). En ny efterlevnadsinställning kontrollerar om en TPM finns på enheten.

[Windows 10 och senare kompatibilitetsprincipinställningar](compliance-policy-create-windows.md) visar en lista över de aktuella inställningarna.

Gäller för: 
- Windows 10 och senare

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Konfigurera Win32-appar installeras på Intune-registrerade Azure AD-anslutna enheter <!-- 3695227 -->
Du kommer att kunna tilldela Win32-appar installeras på Intune-registrerade Azure AD-anslutna enheter. Mer information om Win32-appar i Intune finns i [Win32-apphantering](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Baslinje för Windows Defender Advanced Threat Protection <!-- 3754134 -->
Vi ska lägga till nya baslinjen för att hjälpa dig att konfigurera inställningarna för Windows Defender Avancerat skydd.

### <a name="device-overview-shows-primary-user---794259---"></a>Enhetsöversikt visar primär användare <!--794259 -->
På översiktssidan för enheten visas den primära användaren, även kallat användaren enheten mappning mellan användare (UDA). Om du vill se den primära användaren för en enhet, Välj **Intune** > **enheter** > **alla enheter** > väljer du en enhet. Den primära användaren visas i den övre delen av den **översikt** sidan.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Utökat stöd för Android-företagsenheter fullständigt hanterade enheter <!-- 3903241, 3903244, 3903246 -->
Vi kommer att expandera stödet för Android-företagsenheter fullständigt hanterade enheter ([meddelade i januari 2019](whats-new.md#week-of-january-14-2019) att inkludera följande:
- Efterlevnad
- Villkorlig åtkomst
- Ny slutanvändaren App

För att konfigurera fullständigt hanterade Android-enheter, gå till **Enhetsregistrering** > **Android-registrering** > **Företagsägda, fullständigt hanterade användarenheter**. Stöd för fullständigt hanterade Android-enheter är fortfarande i förhandsversion och vissa Intune-funktioner kanske inte är helt funktionella. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Ytterligare apprapportering för Android-företagsenheter arbetsprofilenheter i hanterat Google Play-konto <!-- 4105925 -->
För appar hanterat Google Play-konto som distribuerats till Android-företagsenheter arbetsprofilenheter, blir det möjligt att visa det specifika versionsnumret för appen är installerad på en enhet. Detta gäller endast obligatoriska appar. På samma sätt för tillgängliga appar kommer att aktiveras i en framtida version.

### <a name="ios-third-party-keyboards----4111843---"></a>iOS-tangentbord från tredje part <!-- 4111843 -->
Stöd för Intunes appskyddsprincip (APP) för den **från tredje part tangentbord** inställningen avslutas på grund av en ändring för iOS-plattformen. Du kan inte konfigurera den här inställningen i Intune-administratörskonsolen och den tillämpas inte på klienten i Intune App SDK.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Blockera användare från söker efter uppdateringar för Windows <!-- 3316758 -->
Vi lägger till en ny Windows update ring-inställning som du kan använda för att blockera användare från söker efter uppdateringar för Windows. Den här inställningen vara inte tillgänglig i portalen, men kan konfigureras med hjälp av Intune Graph API.

### <a name="windows-update-notifications----3316782---"></a>Meddelanden om uppdateringar för Windows <!-- 3316782 -->
Vi lägger till stöd för Windows Update ring konfigurationer så att du kan konfigurera Windows Update-meddelanden som användarna ser. Den här inställningen vara inte tillgänglig i portalen, men kan konfigureras med hjälp av Intune Graph API.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Enklare åtkomst till diagnostikinställningar <!-- 3804627 -->
Vi lägger till en ny möjlighet att den **granskningsloggar** -bladet i varje granskningsloggen arbetsbelastning i Intune-konsolen som du kan använda för att öppna direkt i *diagnostikinställningar* sidan.

## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


