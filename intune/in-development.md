---
title: Under utveckling – Microsoft Intune
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
# <a name="in-development-for-microsoft-intune---april-2019"></a>Under utveckling för Microsoft Intune – april 2019

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Dessutom:

- Om vi tror att du måste vidta åtgärder innan en ändring genomförs publicerar vi ett extra inlägg i Meddelandecenter för Office.
- När en funktion distribueras i produktionsmiljön, antingen som en förhandsversion eller som en allmänt tillgänglig version, flyttas funktionsbeskrivningen från den här sida till [sidan Nyheter](whats-new.md).
- Den här sidan och [sidan Nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Information om planerade produktlanseringar och tidslinjer finns i [M365-översikten](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS).

> [!Note]
> Den här informationen återspeglar Microsofts planer gällande Intune-funktioner i kommande versioner. Datum och enskilda funktioner kan ändras. Alla komponenter som är under utveckling har inte en funktionsbeskrivning på den här sidan.

**RSS-feed**: Håll dig informerad när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Ange inställningarna för inloggning och kontrollera omstartsalternativ på macOS-enheter <!-- 1210083 -->
På macOS-enheter kan du skapa en profil för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **macOS** för plattformen > **Enhetsfunktioner** för profiltypen). Med de nya inställningarna för inloggningsfönstret kommer du till exempel att kunna visa en anpassad banderoll, ändra hur användare loggar in, visa eller dölja energiinställningarna och mer.

Om du vill visa de aktuella inställningarna går du till avsnittet om [inställningar för funktioner på macOS-enheter](macos-device-features-settings.md).

Gäller för: macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Avancerade inställningar för Windows Defender-brandväggen <!-- 1311949 -->
Snart kommer du att kunna använda Intune för att hantera anpassade brandväggsregler på klienter för Windows Defender. Regler kan ange beteende för inkommande och utgående trafik till program, nätverksadresser och portar. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Kräv villkorlig åtkomst med appskydd  <!--1634317 -->
Du kommer att kunna använda *Kräv appskyddsprincip*, som bekräftar att principen tillämpas på en användares app innan inloggningen slutförs för att hindra användare från att komma åt data som du skyddar med villkorlig åtkomst. Även om den här typen av principbekräftelse tar lite tid skyddar den mot nätverksproblem, administrativa felkonfigurationer och avsiktliga försök att komma runt appskyddsprinciper. 

### <a name="retire-noncompliant-devices----1827291---"></a>Ta icke-kompatibla enheter ur bruk <!-- 1827291 -->
Vi kommer att lägga till en ny kompatibilitetsåtgärd för att dra tillbaka en inkompatibel enhet. När en inkompatibel enhet tas bort tas alla företagsdata bort från enheten, och enheten hanteras inte längre i Intune. Den här åtgärden körs när det konfigurerade antalet dagar har uppnåtts. Minsta värde är 30 dagar. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Konfigurera inställningar för kerneltillägg på macOS-enheter <!-- 2043024 -->
På macOS-enheter kan du skapa en enhetskonfigurationsprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **macOS** som plattform). En ny grupp med inställningar gör att du kan konfigurera och använda kerneltillägg på dina enheter.

Gäller för: macOS 10.13.2 och senare

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Konfigurera profilen om du vill hoppa över vissa av skärmarna i installationsassistenten <!-- 2276470 -->
När du skapar en macOS-registreringsprofil kommer du att kunna konfigurera den för att hoppa över valfria följande skärmar när en användare går igenom installationsassistenten:
- Android-migrering
- Visningston
- Sekretess
- iCloudStorage Om du skapar en ny profil eller redigerar en profil måste den valda överhoppningsskärmen synkroniseras med Apple MDM-servern. Användare kan utfärda en manuell synkronisering av enheterna så att det inte sker någon fördröjning i att plocka upp profiländringarna.
Mer information finns i [Registrera macOS-enheter automatiskt med programmet för enhetsregistrering eller Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Enhetsanvändare kan visa alla hanterade appar som de har installerat eller försökt att installera <!-- 2352913 -->
Företagsportalen för Windows visar alla hanterade appar, både nödvändiga och tillgängliga, som är installerade på en användares enhet. Användare kommer att kunna visa installationsförsök och väntande installationer, och deras aktuella status. Om din organisation inte gör appar obligatoriska eller tillgängliga ser användarna ett meddelande som förklarar att inga företagsappar har installerats. Användarna kommer också att kunna sortera eller filtrera appar baserat på installationsstatus.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Omfångstaggar för Apple VPP-token <!--2371886 -->
Du kommer att kunna lägga till omfångstaggar i Apple VPP-token. Endast användare som har tilldelats med samma omfångstagg får åtkomst till Apple VPP-token med den taggen. VPP-appar och e-böcker som köpts med den token ärver dess omfångstaggar. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar](scope-tags.md).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Använd ”tillämplighetsregler” när du skapar konfigurationsprofiler för Windows 10-enheter <!-- 2549910 -->
Du skapar konfigurationsprofiler för Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10** som plattform). Du kommer att kunna skapa en **tillämpningsregel** så att profilen endast gäller för en viss utgåva eller en specifik version. Exempelvis kan du skapa en profil som aktiverar vissa BitLocker-inställningar. När du lägger till profilen använder du en tillämpningsregel så att profilen endast gäller för enheter som kör Windows 10 Enterprise.

Gäller för: 
- Windows 10 och senare

### <a name="enable-win32-app-dependencies----2617348---"></a>Aktivera Win32-appsamband <!-- 2617348 -->
Offentlig förhandsversion – Som administratör kommer du att kunna kräva att andra appar installeras som beroenden innan Win32-appen installeras. Mer specifikt måste enheten installera de beroende apparna innan den installerar Win32-appen. Den här funktionen kommer att bli tillgänglig när Intune-hanteringsagenten har uppgraderats till version 1904 (senare än 1.18.120.0), vilket kan ta en eller två veckor till efter att vi uppgraderar tjänsten till 1904. I Intune väljer du **Klientappar** > **Appar** > **Lägg till** för att visa bladet **Lägg till app**. Välj **Windows-app (Win32)** som **Apptyp**. Mer information finns i [Fristående Intune – Win32-apphantering](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Ny inställning för enhetsbegränsning för Android Enterprise, Enhetens ägare: Gör det möjligt för användarna att ansluta till Wi-Fi-nätverk på Android Enterprise-dedikerade enheter som körs i helskärmsläge för flera appar <!--3041940 -->
Administratörer kommer att kunna aktivera och inaktivera en ny inställning som gör att användarna kan konfigurera Bluetooth på sina Android Enterprise-dedikerade enheter som körs i helskärmsläge för flera appar. Så här visar du den här inställningen i Intune-konsolen: välj **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **Android Enterprise** som plattform > **Endast enhetens ägare, Enhetsbegränsningar** som profiltyp > **Inställningar** > **Särskilda enheter** > välj **Flera appar** i listrutan för inställningen **Kioskläge**. Ett alternativ med namnet **Wi-Fi-konfiguration** kommer att vara tillgängligt. 

Gäller för: Dedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Ny inställning för enhetsbegränsning för Android Enterprise, Enhetens ägare: Gör det möjligt för användare att konfigurera Bluetooth och parkoppling på Android Enterprise-dedikerade enheter <!--3041941 -->
Administratörer kommer att kunna aktivera och inaktivera en ny inställning som gör att användarna kan konfigurera Bluetooth på sina Android Enterprise-dedikerade enheter som körs i helskärmsläge för flera appar. Så här visar du den här inställningen i Intune-konsolen: välj **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **Android Enterprise** som plattform > **Endast enhetens ägare, Enhetsbegränsningar** som profiltyp > **Inställningar** > **Särskilda enheter** > välj **Flera appar** i listrutan för inställningen **Kioskläge**. Ett alternativ med namnet **Bluetooth-konfiguration** kommer att vara tillgängligt. 

Gäller för: Dedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Övervaka status för säkerhetsbaslinje (offentlig förhandsversion) <!-- 3082047 --> 
När du övervakar *enhetsstatusen* för dina säkerhetsbaslinjer visas statusen baserat på baslinjekategori, t.ex. *På låsskärmen*, *BitLocker* och *Webbläsaren*. Alla tillgängliga baslinjekategorier kommer att finnas representerade. För varje kategori ser du hur många enheter som inte matchar en specifik baslinjekategori, som är felkonfigurerade eller som inte kan användas.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Intune-säkerhetsuppgifter för Defender ATP (i allmänt tillgänglig förhandsversion) <!-- 3208597 -->
Snart introducerar Intune en offentlig förhandsversion för säkerhetsuppgifter i den nya TVM-komponenten (Microsoft Defender Threat & Vulnerability Management).  Med den här integrationen kan säkerhetsadministratörer i Windows Defender ATP (WDATP) effektivt kommunicera rekommenderade avhjälpningsåtgärder mot nya hot till Intune-administratörer. Tillägget av säkerhetsuppgifter är en riskbaserad metod för att identifiera, prioritera och åtgärda säkerhetsproblem och felkonfigurationer på slutpunkterna.

Mer information om säkerhetsuppgifter i Intune finns i blogginlägget om att [använda Intune-säkerhetsuppgifter för att utöka hot- och sårbarhetshanteringen i Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Skapa och använda OEMConfig-profiler för enhetskonfiguration i Intune <!-- 3305883 -->
Intune kommer att ha stöd för konfiguration av Android Enterprise-enheter med OEMConfig. Mer specifikt kan du kan skapa en profil för enhetskonfiguration och använda inställningar för Android Enterprise-enheter med hjälp av OEMConfig (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform).

Stöd för OEM-tillverkare sker för närvarande per varje enskild OEM. Om en OEMConfig-app som du vill ha inte finns i listan över OEMConfig-appar kan du kontakta `IntuneOEMConfig@microsoft.com`.

Gäller för: 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Nya inställningar för enhetsbegränsningar för enhetsägarbaserad Android Enterprise <!-- 3574254 -->
På Android Enterprise-enheter kan du skapa en profil för enhetsbegränsningar för att tillåta eller begränsa funktion, ange lösenordsregler och mer (**Enhetskonfiguration** > **Profiler** > **Skaoa profil** > välj **Android Enterprise** för plattform > **Endast enhetsägare > Enhetsbegränsningar** för profiltyp). 

Nya inställningar, inklusive lösenordsinställningar, som ger fullständig åtkomst till appar i Google Play Store för fullständigt hanterade enheter, och mycket mer, kommer att finnas tillgängligt. 

Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](device-restrictions-android-for-work.md). 

Gäller för: Fullständigt hanterade Android Enterprise-enheter

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Söka efter en TPM-kretsuppsättning i en efterlevnadsprincip för Windows 10-enheter <!-- 3617671 -->
Många Windows 10-enheter och senare enheter har TPM-kretsuppsättningar (Trusted Platform Module). En ny kompatibilitetsinställning kontrollerar om en TPM finns på enheten.

[Inställningar för kompatibilitetsprinciper i Windows 10 och senare](compliance-policy-create-windows.md) innehåller en lista över de aktuella inställningarna.

Gäller för: 
- Windows 10 och senare

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Konfigurera Win32-appar att installeras på Intune-registrerade Azure AD-anslutna enheter <!-- 3695227 -->
Du kommer att kunna konfigurera Win32-appar för installation på Intune-registrerade Azure AD-anslutna enheter. Mer information om Win32-appar i Intune finns i [Win32-apphantering](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Baslinje för Windows Defender Advanced Threat Protection <!-- 3754134 -->
Vi kommer att lägga till en ny baslinje så att det blir enklare att konfigurera inställningar för Windows Defender Advanced Threat Protection.

### <a name="device-overview-shows-primary-user---794259---"></a>Enhetsöversikt som visar primär användare <!--794259 -->
På sidan för enhetsöversikt visas den primära användaren, som även kallas användartillhörighetsanvändaren (UDA). Om du vill se den primära användaren för en enhet väljer du **Intune** > **Enheter** > **Alla enheter** > välj en enhet. Den primära användaren visas nästan längst upp på sidan **Översikt**.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Utökat stöd för fullständigt hanterade Android Enterprise-enheter <!-- 3903241, 3903244, 3903246 -->
Vi kommer att utöka stödet för fullständigt hanterade Android Enterprise-enheter ([meddelades i januari 2019](whats-new.md#week-of-january-14-2019)) så att följande ingår:
- Efterlevnad
- Villkorlig åtkomst
- Ny slutanvändarapp

För att konfigurera fullständigt hanterade Android-enheter, gå till **Enhetsregistrering** > **Android-registrering** > **Företagsägda, fullständigt hanterade användarenheter**. Stöd för fullständigt hanterade Android-enheter är fortfarande i förhandsversion, och vissa Intune-funktioner är kanske inte helt funktionella. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Ytterligare rapportering för Managed Google Play-app för Android Enterprise-arbetsprofilenheter <!-- 4105925 -->
För hanterade Google Play-appar som distribueras till Android Enterprise-arbetsprofilenheter kommer du att kunna visa det specifika versionsnumret för den app som är installerad på en enhet. Det här gäller endast för obligatoriska appar. Samma funktion för tillgängliga appar kommer att bli tillgänglig i en framtida version.

### <a name="ios-third-party-keyboards----4111843---"></a>iOS-tangentbord från tredje part <!-- 4111843 -->
Stödet för Intunes appskyddsprincip (APP) för inställningen **Tangentbord från tredje part** kommer att tas bort på grund av en iOS-plattformsändring. Du kommer inte att kunna konfigurera den här inställningen i Intune-administratörskonsolen och den kommer inte att tillämpas på klienten i Intune App SDK.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Hindra användare från att söka efter Windows-uppdateringar <!-- 3316758 -->
Vi lägger till en ny inställning för Windows-uppdateringsringen som du kan använda för att förhindra att användare söker efter Windows-uppdateringar. Den här inställningen är inte tillgänglig på portalen, men kan konfigureras med hjälp av Intune Graph API.

### <a name="windows-update-notifications----3316782---"></a>Windows Update-meddelanden <!-- 3316782 -->
Vi lägger till stöd för konfigurationerna av Windows Update-ringen så att du kan konfigurera Windows Update-meddelanden som användarna ser. Den här inställningen är inte tillgänglig på portalen, men kan konfigureras med hjälp av Intune Graph API.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Enklare åtkomst till diagnostikinställningar <!-- 3804627 -->
Vi lägger till ett nytt alternativ på bladet **Granskningsloggar** i alla arbetsbelastningar för granskningsloggar i Intune-konsolen som du kan använda för att öppna sidan *Diagnostikinställningar* direkt.

## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


