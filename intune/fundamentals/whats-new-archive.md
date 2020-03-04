---
title: Nyheter de senaste månaderna i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Granska äldre meddelanden från Intunes sida med nyheter
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/28/2020
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c0cfe99f022a5e5448bdee453fb0210f6b7195fc
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181829"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Nyheter i Microsoft Intune – föregående månader

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


<!-- ########################## -->
## <a name="october-2019"></a>Oktober 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Förbättrad utformning av checklistan i företagsportalappen för Android<!-- 5550857 -->  
Checklistan för inställningar i företagsportalappen för Android har uppdaterats med en enklare design och nya ikoner. Ändringarna ligger i linje med de senaste uppdateringarna som gjorts i företagsportalappen för iOS. En jämförelse av ändringar sida vid sida finns i [Nyheter i användargränssnittet för appen](whats-new-app-ui.md). De uppdaterade registreringsstegen finns i [Registrera med Android-arbetsprofilen](/intune-user-help/enroll-device-android-work-profile) och [Registrera din Android-enhet](/intune-user-help/enroll-device-android-company-portal).  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Win32-appar på enheter med Windows 10 i S-läge<!-- 3747604 --> 
Du kan installera och köra Win32-appar på hanterade enheter med Windows 10 i S-läge. Det gör du genom att skapa en eller flera tilläggsprinciper för S-läge med PowerShell-verktygen i Windows Defender-programreglering (WDAC). Signera tilläggsprinciperna med Device Guard-signeringsportalen och ladda sedan upp och distribuera principerna via Intune. I Intune hittar du den här funktionen genom att välja **Klientappar** > **Tilläggsprinciper för Windows 10 S**. Mer information finns i [Aktivera Win32-appar i S-lägesenheter](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Ange tillgänglighet för Win32-appen baserat på datum och tid<!-- 3510685 -->
Som administratör kan du konfigurera starttid och tidsgräns för en Win32-app som krävs. Vid starttiden börjar Intune-hanteringstillägget ladda ned och cachelagra appinnehållet. Appen installeras vid tiden för tidsgränsen. För tillgängliga appar anger starttiden när appen är synlig i företagsportalen. Mer information finns i [Intune Win32-apphantering](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Kräv omstart av enheten baserat på respitperioden efter installationen av Win32-appen<!-- 3136567 -->
Du kan kräva att en enhet måste startas om efter att en Win32-app har installerats. Mer information finns i [Win32-apphantering](~/apps/apps-win32-app-management.md).

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Mörkt läge för iOS-företagsportalen<!-- 4911422 -->
Mörkt läge är tillgängligt för iOS-företagsportalen. Användarna kan ladda ned företagsappar, hantera sina enheter och få IT-support i valfritt färgschema baserat på enhetsinställningarna. iOS-företagsportalen matchar automatiskt slutanvändarens enhetsinställningar för mörkt eller ljust läge. Mer information finns i [Lansering av mörkt läge i Microsoft Intunes företagsportal för iOS](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453). Mer information om hur du IOS-företagsportalen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Obligatorisk lägsta appversion för Android-företagsportalen<!-- 2378776 -->
Genom att använda inställningen **Lägsta företagsportalversion** för en appskyddsprincip, kan du ange en specifik definierad minimiversion för företagsportalen som ska finnas på slutanvändarens enhet. Med den här inställningen för villkorlig start kan du använda **Blockera åtkomst**, **Rensa data** och **Varna** som möjliga åtgärder när värdet inte uppfylls. De möjliga formaten för det här värdet följer mönstret *[Major].[Minor]* , *[Major].[Minor].[Build]* , eller *[Major].[Minor].[Build].[Revision]* .

Om inställningen **Lägsta företagsportalversion** har konfigurerats, kommer det att påverka slutanvändare som hämtar version 5.0.4560.0 och eventuella framtida versioner av företagsportalen. Den här inställningen har ingen påverkan på användare som använder en version av företagsportalen som är äldre än den version som funktionen lanseras med. Slutanvändare som använder automatiska appuppdateringar kommer troligen inte att se några dialogrutor från den här funktionen, eftersom de sannolikt har den senaste företagsportalversionen. Den här inställningen gäller endast för Android med appskydd för registrerade och oregistrerade enheter. Mer information finns i [Inställningar för Android-appskyddsprinciper – Villkorlig start](~/apps/app-protection-policy-settings-android.md#conditional-launch).

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Lägga till Mobile Threat Defense-appar till oregistrerade enheter<!-- 3005337 -->
Du kan skapa en appskyddsprincip i Intune som kan blockera eller selektivt rensa användarnas företagsdata baserat på enhetens hälsa. Enhetens hälsotillstånd bestäms med hjälp av din valda MTD-lösning (Mobile Threat Defense). Den här funktionen finns i dag i Intune-registrerade enheter som en inställning för enhetsefterlevnad. Med den här nya funktionen utökar vi hotidentifieringen från en MTD-leverantör så att den nu även fungerar på oregistrerade enheter. På Android kräver funktionen att den senaste företagsportalen finns på enheten. På iOS är funktionen tillgänglig för användning när apparna integrerar den senaste Intune SDK:n (v 12.0.15+). Vi uppdaterar ämnet Nyheter när den första appen börjar använda den senaste Intune SDK:n. De återstående apparna blir tillgängliga löpande. Mer information finns i [Skapa en Mobile Threat Defense-appskyddsprincip med Intune](~/protect/mtd-app-protection-policy.md).

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Tillgänglig Google Play-apprapportering för Android-arbetsprofiler<!-- 3041956   -->
För tillgängliga appinstallationer på Android Enterprise-enheter för arbetsprofil samt dedikerade och fullständigt hanterade enheter kan du visa appens installationsstatus samt den installerade versionen av hanterade Google Play-appar. Mer information finns i [Så här övervakar du appskyddsprinciper](~/apps/app-protection-policies-monitor.md), [Hantera Android-arbetsprofilenheter med Intune](~/enrollment/android-enterprise-overview.md) och [Hanterade Google Play-apptyper](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Microsoft Edge version 77 och senare för Windows 10 och macOS (offentlig förhandsversion)<!-- 3872025, 4678761  -->
Microsoft Edge version 77 och senare kommer att göras tillgänglig för distribution till datorer som kör Windows 10 och macOS. 

Den offentliga förhandsversionen erbjuder kanalerna **Dev** och **Beta** för Windows 10 och en **Beta-kanal** för macOS. Distributionen är bara på engelska (EN), men slutanvändarna kan ändra visningsspråket i webbläsaren under **Inställningar** > **Språk**. Microsoft Edge är en Win32-app som installeras i systemkontext och på samma arkitektur (x86-appen i x86-operativsystem och x64-appen i x64-operativsystem). Dessutom är automatiska uppdateringar av webbläsaren **På** som standard, och Microsoft Edge kan inte avinstalleras. Mer information finns i avsnittet om att [lägga till Microsoft Edge för Windows 10 till Microsoft Intune](~/apps/apps-windows-edge.md) och i [Microsoft Edge-dokumentationen](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>Uppdatering av användargränssnittet för appskydd och användargränssnittet för etablering av iOS-appar<!-- 4102027, 4102029   -->
Användargränssnittet för skapande och redigering av appskyddsprinciper samt etableringsprofiler för iOS-appar i Intune har uppdaterats. Gränssnittsändringarna omfattar:
- En förenklad upplevelse med hjälp av ett format i guidestil som komprimerats till ett enskilt blad. 
- En uppdatering av skapandeflödet så att tilldelningar inkluderas.
- En sammanfattningssida för alla saker som anges vid visning av egenskaper, innan en ny princip skapas eller när en egenskap redigeras. Vid redigering av egenskaper visar sammanfattningen dessutom bara en lista över objekt från kategorin med de egenskaper som redigeras.

Mer information finns i [Hur du skapar och tilldelar skyddsprinciper för appar](~/apps/app-protection-policies.md) och [Använd iOS-appetableringsprofiler](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Guidade Intune-scenarier<!-- 4850318, 4831296, 3610611  -->
Intune har nu guidade scenarier som hjälper dig att slutföra en specifik uppgift eller uppsättning med uppgifter i Intune. Ett guidat scenario är en anpassad serie med steg (arbetsflöde) som handlar om ett visst användningsfall från slutpunkt till slutpunkt. Vanliga scenarier definieras baserat på den roll som en administratör, användare eller enhet har i din organisation. Dessa arbetsflöden kräver vanligtvis en samling noggrant samordnade profiler, inställningar, program och säkerhetskontroller för att ge bästa möjliga användarupplevelse och säkerhet. Nya guidade scenarier omfattar:
- [Distribuera Microsoft Edge för mobil](~/fundamentals/guided-scenarios-edge.md)
- [Skydda Microsoft Office-mobilappar](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Molnhanterat modernt skrivbord](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

Mer information finns i [översikten av guidade Intune-scenarier](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>Ytterligare variabel för appkonfiguration är tillgänglig<!-- 4969237   -->
När du skapar en appkonfigurationsprincip kan du inkludera konfigurationsvariabeln `AAD Device ID` som en del av dina konfigurationsinställningar. Gå till Intune och välj **Klientappar** > **Appkonfigurationsprinciper** > **Lägg till**. Ange informationen om konfigurationsprincipen och välj **Konfigurationsinställningar** för att visa bladet **Konfigurationsinställningar**. Mer information finns i avsnittet om [appkonfigurationsprinciper för hanterade Android Enterprise-enheter – Använda Configuration Designer](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).

#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>Skapa grupper av hanteringsobjekt som kallas principuppsättningar<!-- 3762880  -->
Med principuppsättningar kan du skapa ett paket med referenser till redan befintliga hanteringsenheter som behöver identifieras, riktas och övervakas som en enda begreppsmässig enhet. Principuppsättningar ersätter inte befintliga begrepp eller objekt. Du kan fortsätta att tilldela enskilda objekt i Intune, och du kan referera till enskilda objekt som en del av en principuppsättning. Det innebär att alla ändringar av de enskilda objekten avspeglas i principuppsättningen.  I Intune väljer du **Principuppsättningar** > **Skapa** för att skapa en ny principuppsättning. 


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>Ny gränssnittsprofil för konfiguration av enhetens inbyggda programvara för enheter med Windows 10 och senare (offentlig förhandsversion)<!-- 2266073  -->
I Windows 10 och senare kan du skapa en enhetskonfigurationsprofil för att kontrollera inställningar och funktioner (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform). I den här uppdateringen finns en ny typ av gränssnittsprofil för konfiguration av enhetens inbyggda programvara som gör att Intune kan hantera UEFI-inställningar (BIOS).

Mer information om den här funktionen finns i avsnittet om att [använda DFCI-profiler på Windows-enheter i Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

Gäller för:

- Windows 10 RS5 (1809) och senare på inbyggd programvara som stöds

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Uppdatering av användargränssnittet för skapande och redigering av Windows 10-uppdateringsringar<!-- 4099089         -->
Vi har uppdaterat gränssnittsupplevelsen för [skapande och redigering av Windows 10-uppdateringsringar](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) för Intune. Ändringar i användargränssnittet är följande:  
- Ett format i guidestil med en mall som är komprimerad till ett enda konsolblad så att du slipper mängden med blad när du konfigurerar uppdateringsringar.   
- Det ändrade arbetsflödet omfattar Tilldelningar före slutförandet av ringens första konfiguration.
- En sammanfattningssida där du kan granska alla konfigurationer som du har gjort innan du sparar och distribuerar en ny uppdateringsring. Vid redigering av en uppdateringsring visar sammanfattningen endast listan över objekt som har angetts i kategorin med egenskaper som du redigerade.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>Uppdatering av användargränssnittet för skapande och redigering av iOS-programuppdateringsprinciper<!-- 4099090       --> 
Vi har uppdaterat gränssnittsupplevelsen för [skapande](../protect/software-updates-ios.md#configure-the-policy) och [redigering](../protect/software-updates-ios.md#edit-a-policy) av iOS-programuppdateringsprinciper för Intune.  Ändringar i användargränssnittet är följande:  
- Ett format i guidestil med en mall som är komprimerad till ett enda konsolblad så att du slipper mängden med blad när du konfigurerar uppdateringsprinciper.   
- Det ändrade arbetsflödet omfattar Tilldelningar före slutförandet av principens första konfiguration.
- En sammanfattningssida där du kan granska alla konfigurationer som du har gjort innan du sparar och distribuerar en ny princip. Vid redigering av en princip visar sammanfattningen endast listan över objekt som har angetts i kategorin med egenskaper som du redigerade.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404--------"></a>Inställningarna för interaktiv omstart tas bort från Windows-uppdateringsringar<!--  4464404      -->
Som tidigare har meddelats har Intunes Windows 10-uppdateringsringar nu [stöd för inställningar för tidsgränser](../protect/windows-update-settings.md) och stöder inte längre *interaktiv omstart*. Inställningarna för *interaktiv omstart* är inte längre tillgängliga när du konfigurerar eller hanterar uppdateringsringar i Intune.  

Den här ändringen stämmer överens med nyliga [Windows Servicing-ändringar](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) och på enheter som kör Windows 10 1903 eller senare ersätter *tidsgränser* konfigurationer för *interaktiv omstart*.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Förhindra installation av appar från okända källor på Android Enterprise-arbetsprofilenheter<!-- 4760025   -->
På Android Enterprise-arbetsprofilenheter kan användarna aldrig installera appar från okända källor. I den här uppdateringen finns det en ny inställning – **Förhindra appinstallationer från okända källor i den personliga profilen**. Som standard förhindrar den här inställningen att användare läser in appar från okända källor till den personliga profilen på enheten.

Om du vill se den inställning som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:

- Android Enterprise-arbetsprofil

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Skapa en global HTTP-proxy på Android Enterprise-enhetsägarenheter<!-- 4816339   -->
På Android Enterprise-enheter kan du konfigurera en global HTTP-proxy som uppfyller organisationens webbläsarstandarder (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Enhetsägare > Enhetsbegränsningar** för profiltyp > **Anslutningar**). Efter konfigurationen använder all HTTP-trafik denna proxy.

Om du vill konfigurera den här funktionen och se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:

- Android Enterprise-enhetsägare

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Inställningen för automatisk anslutning tas bort från Wi-Fi-profiler på Android-enhetsadministratör och Android Enterprise<!-- 5021055   -->
På Android-enhetsadministratör och Android Enterprise-enheter kan du skapa en Wi-Fi-profil för att konfigurera olika inställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android-enhetsadministratör** eller **Android Enterprise** för plattform > **Wi-Fi** för profiltyp). I den här uppdateringen tas inställningen **Anslut automatiskt** bort eftersom den [inte stöds av Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Om du använder den här inställningen i en Wi-Fi-profil har du kanske märkt att **Anslut automatiskt** inte fungerar. Du behöver inte vidta några åtgärder, men tänk på att den här inställningen tas bort från användargränssnittet i Intune.

Om du vill se de aktuella inställningarna går du till [Wi-Fi-inställningar för Android](../configuration/wi-fi-settings-android.md) eller [Wi-Fi-inställningar för Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

Gäller för:

- Android-enhetsadministratör 
- Android enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>Nya enhetskonfigurationsinställningar för övervakade iOS- och iPadOS-enheter<!-- 5199328   -->
På iOS- och iPadOS-enheter kan du skapa en profil för att begränsa funktioner och inställningar på enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPadOS** för plattform > **Enhetsbegränsningar** för profiltyp). I den här uppdateringen finns det nya inställningar du kan styra: 
- Åtkomst till nätverksenheten i appen Filer  
- Åtkomst till USB-enheten i appen Filer 
- Wi-Fi är alltid aktiverat 

Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md) för att se de här inställningarna.

Gäller för:

- iOS 13.0 och senare
- iPadOS 13.0 och senare

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Växla till att endast visa sidan Registreringsstatus på enheter som har etablerats med ett välkomstprogram<!--3959566-->
Du kan nu välja att endast visa sidan Registreringsstatus på enheter som har etablerats med välkomstprogrammet för Autopilot.

Om du vill se den nya växlingsfunktionen väljer du **Intune** > **Enhetsregistrering** > **Windows-registrering** > **sidan Registreringsstatus** > **Skapa profil** > **Inställningar** > **Visa bara sidan för enheter som har etablerats via välkomstprogrammet**.

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Ange vilka operativsystemversioner för Android-enheter som registreras via registrering med arbetsprofil eller enhetsadministratör<!-- 4350697   -->
Med hjälp av begränsningar för Intune-enhetstyp kan du använda enhetens OS-version för att ange vilka användarenheter som ska använda registrering med Android Enterprise-arbetsprofil eller registrering med Android-enhetsadministratör.  Mer information finns i [Konfigurera registreringsrestriktioner](../enrollment/enrollment-restrictions-set.md).



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune har stöd för iOS 11 och senare<!-- 4665324  -->
Intune-registreringen och företagsportalen har nu stöd för iOS-versionerna 11 och senare. Äldre versioner stöds inte.

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Nya begränsningar för namnbyte av Windows-enheter<!-- 3478938  -->
När du byter namn på en Windows-enhet måste du följa nya regler:
- 15 tecken eller mindre (måste vara mindre än eller lika med 63 byte exklusive avslutande NULL)
- Inte null eller en tom sträng
- Tillåten ASCII: Bokstäver (a–z, A–Z), siffror (0–9) och bindestreck
- Tillåten Unicode: tecken > = 0x80, måste vara en giltig UTF8, måste vara IDN-mappningsbara (det vill säga att RtlIdnToNameprepUnicode lyckas; se RFC 3492)
- Namn får inte enbart innehålla siffror
- Inga blanksteg i namnet
- Förbjudna tecken: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 Mer information finns i [Ändra namn på en enhet i Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>Ny Android-rapport på sidan med enhetsöversikt<!-- 4924364 -->
En ny rapport på sidan med enhetsöversikt visar hur många Android-enheter som har registrerats i varje enhetshanteringslösning. Det här diagrammet visar antal arbetsprofilenheter samt fullständigt hanterade, dedikerade och enhetsadministratörsregistrerade enheter. Om du vill se rapporten väljer du **Intune** > **Enheter** > **Översikt**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge-baslinje (förhandsversion)<!--  3787164  -->
Vi har lagt till en förhandsversion med säkerhetsbaslinje för [Microsoft Edge-inställningar](../protect/security-baseline-settings-edge.md). 

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>PKCS-certifikat för macOS<!-- 1333650       -->
Nu kan du [använda PKCS-certifikat med macOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). Du kan välja PKCS-certifikatet som en profiltyp för macOS och distribuera användar- och enhetscertifikat som har [anpassade ämnesnamnfält och alternativa ämnesnamnfält](../protect/certficates-pfx-configure.md#subject-name-format).  

PKCS-certifikat för macOS har även stöd för en ny inställning, _Ge alla appar åtkomst_. Med den här inställningen kan du ge alla associerade appar åtkomst till den privata nyckeln för certifikatet.  Mer information om den här inställningen finns i Apple-dokumentationen på https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>Härledda autentiseringsuppgifter för etablering av mobila iOS-enheter med certifikat<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune stöder användning av [härledda autentiseringsuppgifter](../protect/derived-credentials.md) som autentiseringsmetod samt för S/MIME-signering och -kryptering för iOS-enheter. Härledda autentiseringsuppgifter är en implementering av standarden *National Institute of Standards and Technology (NIST) 800-157* för distribution av certifikat till enheter.  

Härledda autentiseringsuppgifter är beroende av att ett PIV-kort (Personal Identity Verification) eller ett CAC-kort (Common Access Card) används, till exempel ett smartkort. För att få en härledd autentiseringsuppgift för sin mobila enhet börjar användare i Företagsportal-appen och följer ett registreringsarbetsflöde som är unikt för den provider som du använder.  Gemensamt för alla providrar är kravet på användning av ett smartkort på en dator för autentisering till providern för den härledda autentiseringsuppgiften. Providern utfärdar sedan ett certifikat till den enhet som härleds från användarens smartkort.  

Intune stöder följande providrar för härledda autentiseringsuppgifter:
- DISA Purebred
- Entrust Datacard
- Intercede

Du använder härledda autentiseringsuppgifter som autentiseringsmetod för enhetskonfigurationsprofiler för VPN, Wi-Fi och e-post. Du kan även använda dem för appautentisering samt för S/MIME-signering och -kryptering.  

Mer information om standarden finns i [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) (Härledda PIV-autentiseringsuppgifter) på www.nccoe.nist.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Använd Graph API för att ange ett lokalt användarhuvudnamn som en variabel för SCEP-certifikat<!--  5437939        -->  
När du använder [Intune-Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) kan du ange onPremisesUserPrincipalName som en variabel för SAN (alternativt namn för certifikatmottagare) för SCEP-certifikat.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Microsoft 365 Enhetshantering

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Förbättrad administrationsupplevelse i Microsoft 365 Enhetshantering<!-- 5551239 -->
En uppdaterad och förbättrad administrationsupplevelse är nu allmänt tillgänglig i specialistarbetsytan för Microsoft 365 Enhetshantering på [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com), inklusive:

- **Uppdaterad navigering**: Du hittar en förenklad navigering på hög nivå som logiskt grupperar funktioner.
- **Nya plattformsfilter**: Du kan välja en enda plattform som bara visar principer och appar för den valda plattformen på sidorna Enheter och Appar.
- **Ny startsida**: Se snabbt tjänstens hälsa, status för din klientorganisation, nyheter osv. på den nya startsidan.

Mer information om dessa förbättringar finns i [blogginlägget Enterprise Mobility + Security](https://go.microsoft.com/fwlink/?linkid=2109094) på webbplatsen för Microsoft Tech Community.

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Introduktion till noden för slutpunktssäkerhet i Microsoft 365 Enhetshantering<!-- 5630102 -->

Noden **Slutpunktssäkerhet** finns nu allmänt tillgänglig i specialistarbetsytan för Microsoft 365 Enhetshantering på https://devicemanagement.microsoft.com, som grupperar funktionerna för att skydda slutpunkter som exempelvis:

- Säkerhetsbaslinjer:  En förkonfigurerad grupp med inställningar som hjälper dig att tillämpa kända inställningsgrupper och standardvärden som rekommenderas av Microsoft.
- Säkerhetsaktiviteter: Dra nytta av hot- och sårbarhetshanteringen i Microsoft Defender ATP och använd Intune till att åtgärda svagheter i slutpunkterna.
- Microsoft Defender ATP: Microsoft Defender Avancerat skydd är integrerat för att förhindra säkerhetsöverträdelser.

Inställningarna kommer fortsatt att vara tillgängliga från andra tillämpliga noder, till exempel enheter, och det aktuella konfigurerade tillståndet är detsamma oavsett var du öppnar eller aktiverar funktionerna.

Mer information om dessa förbättringar finns i [blogginlägget Kundframgång för Intune](https://aka.ms/Endpoint_security_node) på webbplatsen för Microsoft Tech Community.

<!-- ########################## -->
## <a name="september-2019"></a>September 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>Privata LOB-appar för Hanterat Google Play-konto<!-- 1464182  -->
Intune tillåter nu IT-administratörer att publicera privata Android LOB-appar till Hanterat Google Play-konto via en iframe inbäddad i Intune-konsolen.  Tidigare behövde IT-administratörer publicera LOB-appar direkt till Googles Play-publiceringskonsol, vilket krävde flera steg och tog lång tid. Med den här nya funktionen kan du enkelt publicera LOB-appar med en minimal uppsättning steg, utan att behöva lämna Intune-konsolen.  Administratörer behöver inte längre manuellt registrera sig som utvecklare hos Google och behöver inte längre betala Google-registreringsavgiften på 25 USD.  Alla Android Enterprise-hanteringsscenarier som använder Hanterat Google Play-konto kan dra nytta av den här funktionen (arbetsprofilenheter och dedikerade, fullständigt hanterade samt icke-registrerade enheter). I Intune väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **Hanterat Google Play-konto** i listan **Apptyp**. Mer information om Managed Google Play-appar finns i [Lägga till Managed Google Play-appar till Android Enterprise-enheter med Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Gränssnittet för Företagsportal i Windows<!-- 1473353, 3598357 -->
Företagsportal i Windows uppdateras. Du kommer att kunna använda flera filter på sidan Appar i Företagsportal i Windows. Sidan Enhetsinformation uppdateras också med ett förbättrat användargränssnitt. Vi håller på att lansera dessa uppdateringar för alla kunder och förväntar oss att blir klara i slutet av nästa vecka.

#### <a name="macos-support-for-web-apps---3174427---"></a>macOS-stöd för webbappar<!-- 3174427 -->
Webbappar, som gör att du kan lägga till en genväg till en URL på webben, kan installeras på Dock med hjälp av Företagsportal i macOS. Slutanvändare kan komma åt **installationsåtgärden** via appinformationssidan för en webbapp i Företagsportal i macOS. Mer information om apptypen **Webblänk** finns i [Lägga till appar i Microsoft Intune](../apps/apps-add.md) och [Lägga till webbappar i Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps---3173501----"></a>macOS-stöd för VPP-appar<!-- 3173501  -->
macOS-appar som köpts via Apple Business Manager visas i konsolen när Apple VPP-token synkroniseras i Intune. Du kan tilldela, återkalla och omtilldela enhets- och användarbaserade licenser för grupper med hjälp av Intune-konsolen. Med Microsoft Intune kan du hantera VPP-appar som köpts för användning i företaget genom att:

- Rapportera licensinformation från App Store.
- Spåra antalet använda licenser.
- Hjälpa dig att förhindra installation av fler exemplar av en app än du äger.

Mer information om Intune och VPP, finns i [Hantera volyminköpta appar och böcker med Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support---2871756----"></a>iframe-stöd för Hanterat Google Play-konto<!-- 2871756  -->
Intune har nu stöd för att lägga till och hantera webblänkar direkt i Intune-konsolen via iframe för Hanterat Google Play-konto.  Det här gör att IT-administratörer kan skicka en URL och ikonbild, och sedan distribuera dessa länkar till enheter precis som vanliga Android-appar. Alla Android Enterprise-hanteringsscenarier som använder Hanterat Google Play-konto kan dra nytta av den här funktionen (arbetsprofilenheter och dedikerade, fullständigt hanterade samt icke-registrerade enheter). I Intune väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **Hanterat Google Play-konto** i listan **Apptyp**. Mer information om appar för Hanterat Google Play-konto finns i [Lägga till appar för Google Play-konto till Android Enterprise-enheter med Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Installera Android LOB-appar obevakat på Zebra-enheter<!-- 4252734  -->
När du installerar verksamhetsspecifika (LOB) Android-appar på [Zebra-enheter](../configuration/android-zebra-mx-overview.md) kan du, i stället för att uppmanas att både ladda ned och installera LOB-appen, installera appen obevakat. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. I fönstret **Välj apptyp** väljer du **Branschspecifik app**. Mer information finns i [Lägg till en verksamhetsspecifik app för Android i Microsoft Intune](../apps/lob-apps-android.md).

När LOB-appen har laddats ned visas ett meddelande om **utförd nedladdning** på användarens enhet. Meddelandet kan bara stängas genom att trycka på **Rensa alla** i meddelandeskuggan. Det här aviseringsproblemet kommer att åtgärdas i en kommande version och installationen kommer att vara helt obevakad utan några visuella indikatorer.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Läsa och skriva Graph API-åtgärder för Intune-appar<!-- 5031704  -->
Appar kan anropa Intune Graph API med både läs- och skrivåtgärder med hjälp av appidentitet utan användarens autentiseringsuppgifter. Mer information om hur du kommer åt Microsoft Graph API för Intune finns i [Arbeta med Intune i Microsoft Graph.](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Delning och kryptering av skyddade data för Intune App SDK för iOS<!-- 3586942  -->
Intune App SDK för iOS använder 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciper. Alla appar måste vara i SDK-version 8.1.1 för att delning av skyddade data ska vara möjlig.

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Uppdateringar av Microsoft Intune-appen<!-- 4997846 -->
Microsoft Intune-appen för Android har uppdaterats med följande förbättringar:
- Uppdaterad och förbättrad layout som inkluderar navigering i nederkant för de viktigaste åtgärderna.
- Ytterligare en sida har lagts till som visar användarens profil.
- Visning av interaktiva meddelanden i appen för användaren har lagts till, exempelvis om enhetsinställningarna behöver uppdateras.
- Visning av anpassade push-meddelanden har lagts till, vilket ger appen samma stöd som nyligen lagts till i företagsportalappen för iOS och Android. Du hittar mer information i [Skicka anpassade meddelanden i Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>För iOS-enheter anpassar du registreringsprocessens sekretessida i Företagsportal<!-- 4394993 -->
Med Markdown kan du anpassa sekretessidan i Företagsportal som slutanvändare ser vid iOS-registrering. Mer specifikt kan du anpassa listan med saker som organisationen inte kan se eller göra på enheten. Mer information finns i [Så konfigurerar du appen Intune-företagsportal](../apps/company-portal-app.md#privacy-statement-customization).



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Stöd för IKEv2 VPN-profiler för iOS<!-- 1943438   -->
I den här uppdateringen kan du skapa VPN-profiler för den iOS-inbyggda VPN-klienten med hjälp av IKEv2-protokoll. IKEv2 är en ny anslutningstyp i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **VPN** för profiltyp > **Anslutningstyp**.

Dessa VPN-profiler konfigurerar den inbyggda VPN-klienter, så att inga VPN-klientappar installeras på eller flyttas till hanterade enheter. Den här funktionen kräver att enheter registreras i Intune (MDM-registrering).

Om du vill se de aktuella VPN-inställningarna som du kan konfigurera går du till [Konfigurera VPN-inställningar på iOS-enheter](../configuration/vpn-settings-ios.md).

Gäller för:

- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>Enhetsfunktioner, enhetsbegränsningar och tilläggsprofiler för iOS- och macOS-inställningar visas efter registreringstyp<!-- 4886161   -->

I Intune skapar du profiler för iOS- och macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **macOS** för plattform > **Enhetsfunktioner**, **Enhetsbegränsningar** eller **Tillägg** för profiltyp). 

I den här uppdateringen kategoriseras de tillgängliga inställningarna i Intune-portalen efter vilken registreringstyp de gäller för:

- iOS
  - Användarregistrering
  - Enhetsregistrering
  - Automatisk enhetsregistrering (övervakad)
  - Alla registreringstyper

- macOS
  - Godkänd av användare
  - Enhetsregistrering
  - Automatisk enhetsregistrering
  - Alla registreringstyper

Gäller för:

- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>Nya röstkontrollinställningar för övervakade iOS-enheter som körs i helskärmsläge<!-- 4892835   -->
I Intune kan du skapa principer för att köra övervakade iOS-enheter som en kioskenhet eller dedikerad enhet (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Helskärm**).

I den här uppdateringen finns det nya inställningar du kan styra:
- **Röststyrning**: Aktiverar röststyrning på enheten i helskärmsläge.
- **Ändring av röststyrning**: Tillåt användare att ändra inställningen för Röststyrning på enheten i helskärmsläge.

Om du vill se de aktuella inställningarna går du till [inställningar för iOS i helskärmsläge](../configuration/device-restrictions-ios.md#kiosk).

Gäller för:

- iOS 13.0 och senare

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Använda enkel inloggning för appar och webbplatser på iOS- och macOS-enheter<!-- 4893175   -->
I den här uppdateringen finns det några inställningar för enkel inloggning för iOS- och macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **macOS** för plattform > **Enhetsfunktioner** för profiltyp).

Använd de här inställningarna till att konfigurera funktioner för enkel inloggning, särskilt för appar och webbplatser som använder Kerberos-autentisering. Du kan välja mellan ett tillägg för enkel inloggning med generiska autentiseringsuppgifter, och Apples inbyggda Kerberos-tillägg.

Om du vill se de aktuella enhetsfunktionerna du kan konfigurera går du till [iOS-enhetsfunktioner](../configuration/ios-device-features-settings.md) och [macOS-enhetsfunktioner](../configuration/macos-device-features-settings.md).

Gäller för:

- iOS 13.0 och senare
- macOS 10.15 och senare

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Associera domäner med appar på macOS 10.15+-enheter<!-- 4898079   -->
På macOS-enheter kan du konfigurera olika funktioner, flytta funktionerna till dina enheter med hjälp av en princip (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsfunktioner** för profiltyp). I den här uppdateringen kan du associera domäner med dina appar. Den här funktioner hjälper till att dela autentiseringsuppgifter med webbplatser relaterade till din app och kan användas med Apples tillägg för enkel inloggning, universella länkar och automatisk ifyllning av lösenord. 

Om du vill visa de aktuella funktionerna du kan konfigurera går du till [Funktionsinställningar för macOS-enheter i Intune](../configuration/macos-device-features-settings.md).

Gäller för:

- macOS 10.15 och senare

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Använd ”iTunes” och ”apps” i iTunes App Store-URL när du visar eller döljer appar på iOS-övervakade enheter<!-- 4928474   --> 
I Intune kan du skapa principer för att visa eller dölja appar på dina övervakade iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Visa eller dölj appar**). 

Du kan ange iTunes App Store-URL:en, till exempel `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. I den här uppdateringen kan både `apps` och `itunes` användas i URL:en, till exempel:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Mer information om de här inställningarna finns i [Visa eller dölja appar](../configuration/device-restrictions-ios.md#show-or-hide-apps).

Gäller för:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Lösenordstypvärden för Windows 10-efterlevnadsprincip är tydligare och matchar CSP<!-- 5138985 -->
På Windows 10-enheter kan du skapa en efterlevnadsprincip som kräver särskilda lösenordsfunktioner (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Windows 10 och senare** för plattform > **Systemsäkerhet**). I den här uppdateringen:
- Värden för**Lösenordstyp** är tydligare och uppdaterade för att matcha [CSP:n DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- Inställningen **Förfallotid för lösenord (dagar)** har uppdaterats till att tillåta värden från 1 till 730 dagar. 

Mer information om Windows 10-efterlevnadsinställningar finns i [Inställningar för Windows 10 och senare för att markera enheter som att de följer standard eller inte följer standard](../protect/compliance-policy-create-windows.md). 

Gäller för:
- Windows 10 och senare

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Uppdaterat användargränssnitt för att konfigurera åtkomst till Microsoft Exchange lokalt<!-- 4092920 -->  
Vi har uppdaterat konsolen där du [konfigurerar åtkomst till Microsoft Exchange lokalt](../protect/conditional-access-exchange-create.md). Alla konfigurationer för åtkomst till Exchange lokalt är nu tillgängliga i samma fönster i konsolen där du *aktiverar åtkomstkontroll för Exchange lokalt*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Tillåta eller begränsa tillägg av appwidgetar på startskärmen på Android Enterprise-arbetsprofilenheter<!-- 1109650  --> 
På Android Enterprise-enheter kan du konfigurera funktioner i arbetsprofilen (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast arbetsprofil > Enhetsbegränsningar** för profiltyp). I den här uppdateringen kan du tillåta användare att lägga till widgetar exponerade av arbetsprofilappar till enhetens startskärm.

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:
- Android Enterprise-arbetsprofil

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Nya klientorganisationer använder som standard inte Android-enhetsadministratörshantering<!-- 4869790   -->
Androids enhetsadministratörsfunktioner har ersatts av Android Enterprise. Vi rekommenderar därför att du använder Android Enterprise för nya registreringar i stället. I en framtida uppdatering måste nya klientorganisationer slutföra följande nödvändiga steg i Android-registrering för att använda enhetsadministratörshantering: Gå till **Intune** > **Enhetsregistrering** > **Android-registrering** > **Personal and corporate-owned devices with device administration privileges** (Personliga och företagsägda enheter med enhetsadministratörsbehörighet)  > **Use device administrator to manage devices** (Använd enhetsadministratör för att hantera enheter).

Befintliga klienter får ingen förändring i sina miljöer.

Mer information om Android-enhetsadministratör i Intune finns i [Administratörsregistrering för Android-enhet](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045----"></a>Lista över DEP-enheter associerade med en profil<!-- 5012045  -->
Du kan se en sidindelad lista över Apple DEP-enheter (programmet för enhetsregistrering) som är associerade med en profil. Du kan söka i listan från valfri sida i listan. Om du vill se listan går du till **Intune** > **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram** > välja en token > **Profiler** > välja en profil > **Tilldelade enheter** (under **Övervaka**).

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>Användarregistrering i iOS i förhandsversion<!-- 4817900 -->
Lanseringen av Apples iOS 13.1 inkluderar användarregistrering, en ny form av lätt hantering av iOS-enheter. Den kan användas i stället för enhetsregistrering eller automatisk enhetsregistrering (tidigare Programmet för enhetsregistrering) för personliga enheter. Intunes förhandsversion har stöd för den här funktionen genom att låta dig göra följande:

- Målanvändarregistrering för användargrupper.
- Ge slutanvändarna möjlighet att välja mellan lättare användarregistrering eller starkare enhetsregistrering när de registrerar sina enheter.

Starting on 9/24/2019 with the release of iOS 13.1, we're in the process of rolling out these updates to all customers and expect to be completed by the end of next week.

Gäller för:

- iOS 13.1 och senare

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>Mer support för fullständigt hanterade Android-enheter<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Vi har lagt till följande support för fullständigt hanterade Android-enheter:

- SCEP-certifikat för fullständigt hanterad Android är tillgängliga för certifikatautentisering på enheter som hanteras som enhetsägare. SCEP-certifikat stöds redan på arbetsprofilenheter.  Med SCEP-certifikat för enhetsägare kan du: <!-- 5227935 -->
    - skapa SCEP-profil under avsnittet DO i Android Enterprise
    - länka SCEP-certifikat till DO Wi-Fi-profil för autentisering
    - länka SCEP-certifikat till DO VPN-profiler för autentisering
    - länka SCEP-certifikat till DO VPN-profiler för autentisering
- Systemappar stöds på Android Enterprise-enheter. I Intune lägger du till en Android Enterprise-systemapp genom att välja **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** väljer du **Android Enterprise-systemapp**. Du hittar mer information i [Lägg till Android Enterprise-systemappar i Microsoft Intune](../apps/apps-ae-system.md). <!-- 4062195 -->
- I **Enhetsefterlevnad** > **Android Enterprise** > **Enhetsägare** kan du skapa en efterlevnadsprincip som ställer in Google SafetyNet-attesteringsnivån.   <!-- 4631425 -->
- På fullständigt hanterade Android Enterprise-enheter stöds providers för skydd mot mobilhot. I **Enhetsefterlevnad** > **Android Enterprise** > **Enhetsägare** kan du välja en acceptabel hotnivå. <!-- 4631440 --> [Android Enterprise-inställningar för att markera enheter som kompatibla eller icke-kompatibla med Intune](../protect/compliance-policy-create-android-for-work.md#device-owner) listar de aktuella inställningarna.
- På fullständigt hanterade Android Enterprise-enheter kan Microsoft Launcher-appen nu konfigureras via appkonfigurationsprinciper för att tillåta en standardiserad slutanvändarupplevelse på den fullständigt hanterade enheten. Appen Microsoft Launcher kan användas till att anpassa Android-enheten. Med hjälp av appen tillsammans med ett Microsoft-konto eller ett arbets-/skolkonto kan du komma åt din kalender, dina dokument och senaste aktiviteter i det personliga flödet. <!-- 5334044 -->

Med den här uppdateringen är Intune-stödet för Android Enterprise fullständigt hanterad nu allmänt tillgängligt.

Gäller för:

- Fullständigt hanterade Android Enterprise-enheter

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>Skicka meddelanden till en enskild enhet<!-- 4928910 -->
Du kan nu välja en enskild enhet och sedan använda en fjärrenhetsåtgärd för att [skicka ett anpassat meddelande till bara den enheten](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>Åtgärderna för rensning och lösenordsåterställning är inte tillgängliga för iOS-enheter som har registrerats med användarregistrering<!-- 4950491 -->
Användarregistrering är en ny typ av Apple-enhetsregistrering. När du registrerar enheter med användarregistrering är fjärråtgärderna för rensning och lösenordsåterställning inte tillgängliga för sådana enheter.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Intune-stöd för iOS 13- och macOS Catalina-enheter<!-- 4665317 -->
Intune stöder nu hantering av både iOS 13- och macOS Catalina-enheter.
Mer information finns i [blogginlägget om Microsoft Intune-stöd iOS 13 och iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Intune-stöd för enheter med iPadOS och iOS 13.1<!--5439574-->
Intune har nu stöd för enheter med såväl iPadOS som iOS 13.1. Mer information finns i [det här blogginlägget](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>BitLocker-stöd för klientbaserad rotering av återställningslösenord<!--  3444125 -->
Använd Intune Endpoint Protection-inställningar för att konfigurera [Klientbaserad rotering av återställningslösenord](../protect/endpoint-protection-windows-10.md#windows-encryption) för BitLocker på enheter som kör Windows version 1909 eller senare.

Den här inställningen initierar en klientbaserad uppdatering av återställningslösenord efter återställning av en operativsystemenhet (med bootmgr eller WinRE) och upplåsning av återställningslösenord på en fast dataenhet. Den är inställningen uppdaterar det specifika återställningslösenordet som har använts och andra oanvända lösenord på volymen förblir oförändrade. Mer information finns i BitLocker CSP-dokumentationen för [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Manipulationsskydd för Windows Defender Antivirus<!-- 4705448        -->
Använd Intune för att hantera *Manipulationsskydd* för Windows Defender Antivirus. Du hittar [inställningen för Manipulationsskydd](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center) i Microsoft Defender Säkerhetscenter-gruppen när du använder enhetskonfigurationsprofiler för Windows 10-slutpunktsskydd. Du kan ställa in manipulationsskydd på *Aktiverad* för att aktivera begränsningar för manipulationsskydd, *Inaktiverad* för att stänga av dem eller *Inte konfigurerad* för att lämna en enhetskonfiguration på plats.  

Mer information om Manipulationsskydd finns i [Prevent security settings changes with tamper protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) (Förhindara ändringar av säkerhetsinställningar med manipulationsskydd) i Windows-dokumentationen.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Avancerade inställningar för Windows Defender-brandväggen är nu allmänt tillgängliga<!--  5317392       -->  
De [anpassade brandväggsreglerna för slutpunktsskydd i Windows Defender](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), som du konfigurerar som en del av en enhetskonfigurationsprofil är inte längre en offentlig förhandsversion, utan är allmänt tillgängliga.  Du kan använda de här reglerna för att ange beteende för inkommande och utgående trafik till program, nätverksadresser och portar. Reglerna släpptes i juli som offentlig förhandsversion. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Uppdatering av Intunes användargränssnitt – Instrumentpanel för klientorganisationsstatus<!-- 5273210  -->
Användargränssnittet för instrumentpanelen med klientorganisationsstatus har uppdaterats så att den överensstämmer med Azures användargränssnitt. Mer information finns i [Klientorganisationsstatus](../tenant-status.md).


### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863----"></a>Omfångstaggar stöder nu principer för användningsvillkor<!-- 2358863  -->
Nu kan du tilldela [omfångstaggar](scope-tags.md) till principer för användningsvillkor. Det gör du genom att gå till **Intune** > **Enhetsregistrering** > **Villkor** > välj ett objekt i listan > **Egenskaper** > **Omgångstaggar** > välja en omfångstagg.

<!-- ########################## -->
## <a name="august-2019"></a>Augusti 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>Kontroll av avinstallationsbeteende för iOS-app vid avregistrering av enhet<!-- 3504144   -->
Administratörer kan hantera om en app tas bort eller sparas på en enhet när enheten avregistreras på en användare- eller enhetsgruppnivå. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Kategorisera appar i Microsoft Store för företag<!-- 3926922 -->
Du kan kategorisera appar i Microsoft Store för företag. Om du vill göra det väljer du **Intune** > **Klientappar** > **Appar** > Välj en Microsoft Store för företag-app > **Appinformation** > **Kategori**. I den nedrullningsbara menyn tilldelar du en kategori.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Anpassade meddelanden för Microsoft Intune-appanvändare<!-- 4843354  -->
Microsoft Intune-appen för Android har nu stöd för visning av anpassade push-meddelanden, tillsammans med stödet som nyligen lagts till i företagsportalappar för iOS och Android. Du hittar mer information i [Skicka anpassade meddelanden i Intune](../remote-actions/custom-notifications.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Konfigurera Microsoft Edge-inställningar med hjälp av administrativa mallar för Windows 10 och senare<!-- 5228061 -->
På enheter med Windows 10 och senare kan du skapa administrativa mallar för att konfigurera grupprincipinställningar i Intune. I den här uppdateringen kan du konfigurera inställningar som gäller för Microsoft Edge version 77 och senare.

Mer information om administrativa mallar finns i [Använda Windows 10-mallar för att konfigurera grupprincipinställningar i Intune](../configuration/administrative-templates-windows.md).

Gäller för:

- Windows 10 och senare (Windows RS4 +)

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>Nya funktioner för dedikerade Android Enterprise-enheter i läge för flera appar<!-- 3755304 3041943 3041946   -->

I Intune kan du styra funktioner och inställningar i ett helskärmsläge på dina dedikerade Android Enterprise-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetsägare, enhetsbegränsningar** för profiltyp).

I den här uppdateringen läggs följande funktioner till:

- **Dedikerade enheter** > **Multi-app**: Den **virtuella hemknappen** kan visas genom att svepa upp på enheten eller flyta på skärmen så att användarna kan flytta den.
- **Dedikerade enheter** > **Multi-app**: Med **Åtkomst till ficklampa** kan användare använda ficklampan. 
- **Dedikerade enheter** > **Multi-app**: **Kontroll av medievolym** gör att användare kan kontrollera enhetens medievolym med ett skjutreglage. 
- **Dedikerade enheter** > **Multi-app**:  **Aktivera en skärmsläckare**, ladda upp en anpassad avbildning och kontrollera när skärmsläckaren visas.

Om du vill se aktuella inställningar, går du till [Inställningar för Android Enterprise-enheter som tillåter eller begränsar funktioner med Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Gäller för:

- Dedikerade Android Enterprise-enheter

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Ny app och konfigurationsprinciper för fullständigt hanterade Android Enterprise-enheter<!-- 3574215 3574238 3574235 3574232   -->
Med hjälp av profiler kan du konfigurera inställningar som tillämpar VPN-, e-post- och Wi-Fi-inställningar till dina ägare av Android Enterprise-enheter (fullständigt hanterade). I den här uppdateringen kan du:

- Använd [konfigurationsprinciper för appar](../apps/app-configuration-policies-use-android.md) för att distribuera Outlook, Gmail och nio e-postinställningar.
- Använd enhetskonfigurationsprofiler för att distribuera [inställningar för betrodda rotcertifikat](../protect/certificates-configure.md).
- Använd enhetskonfigurationsprofiler för att distribuera inställningar för [VPN](../configuration/vpn-settings-android-enterprise.md) och [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md).

> [!IMPORTANT]
> Med den här funktionen autentiseras användare med sitt användarnamn och lösenord för VPN-, Wi-Fi- och e-postprofiler. Certifikatbaserad autentisering är för närvarande inte tillgängligt.

Gäller för:  
- Ägare av Android Enterprise-enhet (helt hanterad)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>Kontrollera appar, filer, dokument och mappar som öppnas när användare loggar in på macOS-enheter<!--3914202   -->
Du kan aktivera och konfigurera funktioner på macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsfunktioner** för profiltyp). 

I den här uppdateringen har du en ny inställning för inloggningsobjekt som styr vilka appar, filer, dokument och mappar som öppnas när en användare loggar in till den registrerade enheten. 

Om du vill visa de aktuella inställningarna går du till [Funktionsinställningar för macOS-enheter i Intune](../configuration/macos-device-features-settings.md).

Gäller för:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Tidsgränser ersätter inställningarna för interaktiv omstart för Windows-uppdateringsringar<!-- 4464404        -->
För att justera med de senaste [ändringarna i Windows-underhåll](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing) har Intunes Windows 10-uppdateringsringar nu [stöd för inställningar för tidsgränser](../protect/windows-update-settings.md). *Tidsgränser* fastställer när en enhet installerar funktions- och säkerhetsuppdateringar.  På enheter som kör Windows 10 1903 eller senare ersätter *tidsgränser* konfigurationerna för *interaktiv omstart*.  I framtiden kommer *tidsgränser* att ersätta *interaktiv omstart* på tidigare versioner av Windows 10 också.  

När du inte konfigurerar *tidsgränser* fortsätter enheterna att använda sina inställningar för *interaktiv omstart*, men Intune kommer att ha stöd för inställningar för interaktiv omstart i en framtida uppdatering.  

Planera att använda *tidsgränser* för alla dina Windows 10-enheter. När inställningarna för *tidsgränser* är på plats kan du ändra Intune-konfigurationerna för *interaktiv omstart* till Inte konfigurerad. När den är inställd på Inte konfigurerad, slutar Intune att hantera inställningarna på enheter, men tar inte bort de senaste konfigurationerna för inställningen från enheten. Därför förblir de senaste konfigurationerna som ställts in för *interaktiv omstart* aktiva och används på enheter tills inställningarna har ändrats via en annan metod än Intune. Senare, när enhetsversionen av Windows ändras eller när Intune-stöd för *tidsgränser* expanderar till enhetens Windows-version, börjar enheten att använda de nya inställningarna, som redan finns på plats.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>Stöd för flera Microsoft Intune Certificate Connectors<!--   4704642      -->
Intune har nu stöd för installation och användning av flera [Microsoft Intune Certificate Connectors för PKCS-åtgärder](../protect/certficates-pfx-configure.md). Den här ändringen stöder belastningsutjämning och hög tillgänglighet för anslutningen. Varje anslutningsinstans kan bearbeta certifikatbegäranden från Intune.  Om en anslutning inte är tillgänglig fortsätter andra anslutningar att bearbeta begäranden.

Om du vill använda flera anslutningar behöver du inte uppgradera till den senaste versionen av anslutningsprogrammet.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>Nya inställningar och ändringar i befintliga inställningar för att begränsa funktionerna på iOS-och macOS-enheter<!-- 4867699 4867709   -->
Du kan skapa profiler för att begränsa inställningar på enheter som kör iOS och macOS (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **macOS** för plattformstyp > **Enhetsbegränsningar**). Den här uppdateringen innehåller följande funktioner:

- På **macOS** > **Enhetsbegränsningar** > **Moln och lagring**, använder du den nya inställningen **Handoff** för att blockera användare från att starta arbetet på en macOS-enhet och fortsätta att arbeta på en annan macOS-eller iOS-enhet.

  Gå till [macOS-enhetsinställningar för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-macos.md) för att se de aktuella inställningarna.

- På **iOS** > **Enhetsbegränsningar** finns det vissa ändringar:

  - **Inbyggda appar** > **Hitta min iPhone (endast övervakat)** : Ny inställning som blockerar den här funktionen i funktionen Hitta min app. 
  - **Inbyggda appar** > **Hitta mina vänner (endast övervakat)** : Ny inställning som blockerar den här funktionen i funktionen Hitta min app. 
  - **Trådlös** > **Ändring av Wi-Fi-tillstånd (endast övervakat)** : Ny inställning som förhindrar att användare aktiverar eller inaktiverar Wi-Fi på enheten.
  - **Tangentbord och ordlista** > **QuickPath (endast övervakat)** : Ny inställning som blockerar QuickPath-funktionen.
  - **Moln och lagring**: **Aktivitetsfortsättning** har bytt namn till **Handoff**.

  Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md) för att se de aktuella inställningarna.

Gäller för:  
- macOS 10.15 och senare
- iOS 13 och senare

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Vissa begränsningar för iOS-enheter som inte övervakas kommer att bli övervakade – endast med iOS 13.0-versionen<!-- 4867809   -->
I den här uppdateringen gäller vissa inställningar endast övervakade enheter med iOS 13.0-versionen. Om de här inställningarna konfigureras och tilldelas till ej övervakade enheter före iOS 13.0-versionen, tillämpas inställningarna fortfarande på de enheter som inte övervakas. De gäller även när enheterna har uppgraderat till iOS 13.0. Dessa begränsningar tas bort på ej övervakade enheter som säkerhetskopieras och återställs.

Inställningarna omfattar:

- App Store, dokumentvisning, spel
  - Appbutik
  - Stötande innehåll i iTunes-musik, podcast eller nyheter
  - Lägga till Game Center-vänner
  - Spel för flera personer
- Inbyggda appar
  - Kamera
    - FaceTime
  - Safari
    - Autofyll
- Moln och lagring
  - Säkerhetskopiera till iCloud
  - Blockera synkronisering av iCloud-dokument
  - Blockera synkronisering av iCloud-nyckelring

Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md) för att se de aktuella inställningarna.

Gäller för:  
- iOS 13.0 och senare

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>Förbättrad enhetsstatus för macOS FileVault-kryptering<!-- 4944983         -->
Vi har uppdaterat flera [enhetsstatusmeddelanden](../protect/encryption-monitor.md#device-encryption-status) för FileVault-kryptering på MacOS-enheter.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>Vissa inställningar för Windows Defender Antivirus-genomsökning i rapporten visar felaktig status<!-- 5119229 -->
I Intune kan du skapa principer för att använda Windows Defender Antivirus för att söka igenom dina Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp > **Windows Defender Antivirus**). Rapporter om **tid det tar att utföra en daglig snabbsökning** och **typ av systemgenomsökning som ska utföras** visar statusen Misslyckad, när det faktiskt är en lyckad status. 

I den här uppdateringen ändras detta beteende. Det innebär att inställningarna **tid det tar att utföra en daglig snabbsökning** och **typ av systemgenomsökning som ska utföras** visar statusen Genomförd när skanningen slutförs korrekt och visar Misslyckad när inställningarna inte tillämpas.

Mer information om inställningarna för Windows Defender Antivirus finns i [Enhetsinställningar för Windows 10 (och senare) för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies är en OEM-tillverkare som stöds för OEMConfig på Android Enterprise-enheter<!-- 4843713 -->
I Intune kan du kan skapa en profil för enhetskonfiguration och använda inställningar för Android Enterprise-enheter med hjälp av OEMConfig (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **OEMConfig** för profiltyp).

I den här uppdateringen är Zebra Technologies en OEM-tillverkare (Original Equipment Manufacturer) som stöds för OEMConfig. Mer information om OEMConfig hittar du i [Använda och hantera Android Enterprise-enheter med OEMConfig](../configuration/android-oem-configuration-overview.md).

Gäller för:  
- Android Enterprise


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="default-scope-tags---3702875----"></a>Standardomfångstaggar<!-- 3702875  -->
En nyinbyggd standardomfångstagg är nu tillgänglig. Alla icke-taggade Intune-objekt som stöder omfångstaggar tilldelas automatiskt till standardomfångstaggen. **Standardomfångstaggen** läggs till i alla befintliga rolltilldelningar för att upprätthålla paritet med administratörsupplevelsen idag. Om du inte vill att en administratör ska se Intune-objekt med standardomfångstaggen, tar du bort standardomfångstaggen från rolltilldelningen. Den här funktionen liknar funktionen säkerhetsomfattningar i Configuration Manager. Mer information finns i [Använda RBAC och omfångstaggar för distribuerad IT](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Stöd för registrering av Android-enhetens administratör<!-- 4869749   -->
Alternativet för registrering av Android-enhetens administratör har lagts till på sidan Android-registrering (**Intune** > **Enhetsregistrering** > **Android-registrering)** . Android-enhetens administratör är fortfarande aktiverad som standard för alla klienter.  Du hittar mer information i [Registrering av Android-enhetens administratör](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Hoppa över fler skärmar i installationsassistenten <!--4877451  -->
Du kan ställa in att programprofiler för enhetsregistrering hoppar över följande installationsassistentskärmar:
- För iOS
    - Utseende
    - Express-språk
    - Önskat språk
    - Migrering av enhet till enhet
- För macOS
    - Skärmtid
    - Installation av Touch-ID

Mer information om anpassning av installationsassistenten finns i [Skapa en Apple-registreringsprofil för iOS](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) och [Skapa en Apple-registreringsprofil för MacOS](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Lägg till en användarkolumn till CSV-överföringsprocessen för autopilotenheten<!-- 3823054 -->
Nu kan du lägga till en användarkolumn till CSV-överföringen för autopilotenheter. På så sätt kan du tilldela många användare på samma gång när du importerar CSV-filen. Du hittar mer information i [Registrera Windows-enheter i Intune med hjälp av Windows Autopilot](../enrollment/enrollment-autopilot.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Konfigurera tidsgräns för automatisk rensning av enhet till 30 dagar<!--4231059  -->
Du kan ställa in den automatiska tidsgränsen för enhetsrensning så kort som 30 dagar (i stället för den tidigare gränsen på 90 dagar) efter den senaste inloggningen. Det gör du genom att gå till **Intune** > **Enheter** > **Installation** > **Regler för rensning av enhet**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Versionsnummer finns på Android-enhetens maskinvarusida<!-- 4461910   -->
En ny post på sidan Maskinvara för varje Android-enhet innehåller versionsnumret för enhetens operativsystem. Mer information finns i [Visa enhetsinformation i Intune](../remote-actions/device-inventory.md).

<!-- ########################## -->
## <a name="july-2019"></a>Juli 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Anpassade meddelanden för användare och grupper<!-- 16766574          -->
Skicka anpassade push-meddelanden från företagsportalprogrammet till användare på iOS- och Android-enheter som du hanterar med Intune. Dessa mobila push-meddelanden är mycket anpassningsbara med fri text och kan användas för alla ändamål. Du kan rikta dem till olika användargrupper i din organisation. Mer information finns i [anpassade meddelande](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>Googles app för enhetspolicykontroll<!-- 3041950  -->
Nu ger Managed Home Screen-appen tillgång till Googles Android Device Policy-app. Managed Home Screen-appen är en anpassad startfunktion som används med enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som använder helskärmsläge för flera appar. Du kan komma åt Android Device Policy-appen, eller vägleda användare till Android Device Policy-appen, för support och felsökning. Den här startfunktionen är tillgänglig när enheten registreras och låses på startskärmen i Managed Home Screen. Inga ytterligare installationer behövs för att använda den här funktionen.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Outlook-skyddsinställningar för iOS- och Android-enheter<!-- 3212619 -->
Du kan nu konfigurera både allmänna konfigurationsinställningar för appar och dataskydd för Outlook för iOS och Android med hjälp av enkla Intune-administratörskontroller utan enhetsregistrering. Konfigurationsinställningarna för allmänna appar ger paritet med inställningar som administratörer kan aktivera när de hanterar Outlook för iOS och Android på registrerade enheter. Mer information om Outlook-inställningar finns i [appkonfigurationsinställningar för att distribuera Outlook för iOS och Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).


#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Ikoner för hanterad hemskärm och hanterade inställningar<!-- 4918107 -->
Ikonen för appen för hanterad hemskärm och ikonen för **hanterade inställningar** har uppdaterats. Appen för hanterad hemskärm används bara av enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som kör i helskärmsläge för flera appar. Mer information om appen för hanterad hemskärm finns i [Konfigurera Microsoft-appen för hanterad hemskärm för Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android-enhetspolicy på dedikerade Android Enterprise-enheter<!-- 4918136 -->
Du kan komma åt Android-enhetspolictprogrammet från felsökningsskärmen för den hanterade hemskärmsappen. Appen för hanterad hemskärm används bara av enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som kör i helskärmsläge för flera appar. Du hittar mer information i [Konfigurera Microsofts hanterade hemskärmsapp för Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>Uppdateringar av iOS-företagsportalen<!-- 3902931 -->
Ditt företagsnamn vid begäranden om hantering av iOS-appar ersätter den aktuella ”i.manage.microsoft.com”-texten. Användare ser till exempel företagets namn i stället för ”i.manage.microsoft.com” när de försöker installera en iOS-app från Företagsportalen eller när de tillåter hantering av appen. Detta kommer att distribueras till alla kunder under de närmaste dagarna.

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>AAD och APP på Android Enterprise-enheter<!-- 3574267 -->
När du registrerar fullständigt hanterade Android Enterprise-enheter kommer användarna nu att registreras med Azure Active Directory (AAD) under den första installationen av den nya eller fabriksåterställda enheten. Innan installationen slutfördes tidigare var användaren tvungen att starta Microsoft Intune-appen manuellt för att starta AAD-registreringen efter att installationen slutförts. Nu när användaren kommer till enhetens startsida efter den första installationen, är enheten både ansluten och registrerad.

Förutom AAD-uppdateringar stöds nu Intune App Protection-principer (APP) på fullständigt hanterade Android Enterprise-enheter. Den här funktionen kommer att bli tillgänglig då vi distribuerar den. Du hittar mer information i [Lägg till hanterade Google Play-appar till Android enterprise-enheter med Intune](../apps/apps-add-android-for-work.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready------"></a>Använd ”tillämplighetsregler” när du skapar konfigurationsprofiler för Windows 10-enheter <!-- 2549910 eeready    -->

Du skapar konfigurationsprofiler för Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10** som plattform > **Tillämplighetsregler**). I den här uppdateringen kommer du att kunna skapa en **tillämpningsregel** så att profilen endast gäller för en viss utgåva eller en specifik version. Exempelvis kan du skapa en profil som aktiverar vissa BitLocker-inställningar. När du lägger till profilen använder du en tillämpningsregel så att profilen endast gäller för enheter som kör Windows 10 Enterprise.

Information om hur du lägger till en tillämplighetsregel finns i [Tillämplighetsregler](../configuration/device-profile-create.md#applicability-rules).

Gäller för: Windows 10 och senare

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>Använd tokens för att lägga till enhetsspecifik information i anpassade profiler för iOS-och macOS-enheter<!-- 3330008  -->
Du kan använda anpassade profiler på iOS- och MacOS-enheter för att konfigurera inställningar och funktioner som inte är inbyggda i Intune (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **MacOS** för plattform > **Anpassad** för profiltyp). I den här uppdateringen kan du lägga till tokens till dina `.mobileconfig`-filer för att lägga till enhetsspecifik information. Du kan till exempel lägga till `Serial Number: {{serialnumber}}` i konfigurationsfilen för att visa enhetens serienummer.

Du hittar information om att skapa en anpassad profil i [anpassade inställningar för iOS](../configuration/custom-settings-ios.md) eller [anpassade inställningar för MacOS](../configuration/custom-settings-macos.md).

Gäller för:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Ny konfigurationsdesign när du skapar en OEMConfig-profil för Android Enterprise<!-- 3712769   -->
I Intune kan du skapa en enhetskonfigurationsprofil som använder en OEMConfig-app (enhetskonfiguration > Profiler > Skapa profil > Android Enterprise för plattform > OEMConfig för profiltyp). När du gör det öppnas en JSON-redigerare med en mall och de värden som du kan ändra. 

Den här uppdateringen innehåller en konfigurationsdesign med en förbättrad användarupplevelse som visar information som är inbäddad i appen, inklusive titlar, beskrivningar och mer. JSON-redigeraren är fortfarande tillgänglig och visar eventuella ändringar som du gör i Configuration Designer.

Om du vill se de aktuella inställningarna går du till [Använda och hantera Android Enterprise-enheter med OEMConfig](../configuration/android-oem-configuration-overview.md).

Gäller för: Android enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Uppdaterat användargränssnitt för att konfigurera Windows Hello<!-- 4089576            -->
Vi har uppdaterat konsolen där du [konfigurerar Intune för att använda Windows Hello för företag](../protect/windows-hello.md). Alla konfigurationsinställningar är nu tillgängliga i samma fönster i konsolen där du aktiverar stöd för Windows Hello.

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
Intune PowerShell SDK, som ger stöd för Intune API via Microsoft Graph, har uppdaterats till version 6.1907.1.0. SDK har nu stöd för följande:
- Fungerar med Azure Automation.
- Har stöd för läsåtgärder för app-only-autentisering. 
- Har stöd för egna korta namn som alias.
- Följer namnkonventioner för PowerShell. Mer specifikt har `PSCredential`-parametern (på `Connect-MSGraph`-cmdleten) bytt namn till `Credential`.
- Stöder manuell angivelse av värdet för `Content-Type`-sidhuvudet när du använder `Invoke-MSGraphRequest`-cmdleten.

Mer information finns i [PowerShell SDK för Microsoft Intune Graph API.](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>Hantera FileVault för macOS<!--  3858502 + 4557986 + 1210104  -->
Du kan använda Intune för att [hantera FileVault-krypteringsnyckel för MacOS-enheter](../protect/encrypt-devices.md). För att kryptera enheter kan du använda en enhetskonfigurationsprofil för slutpunktsskydd.

Vår support för FileVault omfattar kryptering av okrypterade enheter, deposition av enheters personliga återställningsnyckel, automatisk eller manuell rotation av personliga krypteringsnycklar och nyckelhämtning för företagsenheter. Slutanvändare kan också använda Företagsportalens webbplats för att hämta den personliga återställningsnyckeln för sina krypterade enheter.

Vi har också expanderat krypteringsrapporten till att inkludera [information om FileVault](../protect/encryption-monitor.md) för BitLocker, så att du kan visa all din enhets krypteringsinformation på en och samma plats.

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Nya Office-, Windows- och OneDrive-inställningar i administrativa mallar i Windows 10 <!-- 3510695 -->

Du kan skapa administrativa mallar i Intune som imiterar lokal grupprinciphantering (**enhetshantering** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Administrativ mall** för profiltyp).

Den här uppdateringen innehåller fler Office-, Windows- och OneDrive-inställningar som du kan lägga till i dina mallar. Med de här nya inställningarna kan du nu konfigurera över 2500-inställningar som är 10 0% molnbaserade.

Mer information om den här funktionen finns i [Använda Windows 10-mallar för att konfigurera grupprincipinställningar i Intune](../configuration/administrative-templates-windows.md).

Gäller för: Windows 10 och senare

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Uppdateringar för registreringsbegränsningar<!-- 2871968 -->
Registreringsbegränsningar för nya klienter har uppdaterats så att Android Enterprise Work-profiler tillåts som standard. Befintliga klienter får ingen förändring. Om du vill använda Android Enterprise Work-profiler måste du fortfarande [ansluta ditt Intune-konto till ditt hanterade Google Play-konto](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Användargränssnittsuppdateringar för Apple-registrering och registreringsbegränsningar<!--4089575, 4089579  -->
De två följande processerna använder ett användargränssnitt med en guide:
- Registrering av Apple-enhet. Mer information finns i [Registrera iOS-enheter automatiskt med Apples program för enhetsregistrering](../enrollment/device-enrollment-program-enroll-ios.md).
- Skapa registreringsbegränsningar. Mer information finns i [Konfigurera registreringsrestriktioner](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509-----"></a>Hantera förkonfigurering av enhetsidentifierare för företag för Android Q-enheter<!-- 4711509   -->
I Android Q (v10) tar Google bort möjligheten för MDM-agenter på tidigare hanterade Android-enheter (enhetsadministratör) för att samla in information om enhetsidentifieraren.  Intune har en funktion som gör det möjligt för IT-administratörer att [förkonfigurera en lista över enhetsserienummer eller IMEI](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) för att automatiskt tagga enheterna som företagsägda. Den här funktionen fungerar inte för Android Q-enheter som hanteras av enhetsadministratören.  Oavsett om serienumret eller IMEI för enheten har laddats upp anses det alltid vara personligt under Intune-registreringen.  Du kan manuellt växla ägarskap till företag efter registreringen.  Detta påverkar endast nya registreringar och befintliga registrerade enheter påverkas inte.  Android-enheter som hanteras med arbetsprofiler påverkas inte av den här ändringen och fortsätter att fungera som de gör i dag.  Dessutom kommer Android Q-enheter som registrerats som enhetsadministratör inte längre att kunna rapportera serienummer eller IMEI i Intune-konsolen som enhetsegenskaper.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Ikoner har ändrats för Android Enterprise-registreringar (arbetsprofil, dedikerade enheter och fullständigt hanterade enheter)<!-- 4977730 -->
Ikonerna för Android Enterprise-registreringsprofiler har ändrats. Om du vill se de nya ikonerna går du till **Intune** > **Registrering** > **Android-registrering** > tittar under **Registreringsprofiler**.

#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Ändring av datainsamling i Windows-diagnostikdata<!-- 4113859 -->
Standardvärdet för insamling av diagnostikdata har ändrats för enheter som kör Windows 10, version 1903 och senare. Från och med Windows 10 1903 aktiveras insamling av diagnostikdata som standard. Windows-diagnostikdata är viktiga tekniska data från Windows-enheter om enheten och hur Windows och relaterad programvara fungerar. Mer information finns i [Konfigurera Windows-diagnostikdata i din organisation](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Autopilot-enheter anges också som ”fullständig” telemetri om inget annat anges i autopilotprofilen med [ System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>Windows autopilot-återställning tar bort enhetens primära användare<!-- 4156123 -->
När autopilot-återställning används på en enhet tas enhetens primära användare bort. Nästa användare som loggar in efter återställningen kommer att anges som primär användare. Den här funktionen kommer att distribueras till alla kunder under de närmaste dagarna.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="improve-device-location---3855417----"></a>Förbättra enhetens plats<!-- 3855417  -->
Du kan zooma in till de exakta koordinaterna för en enhet med åtgärden **Hitta enhet**. Mer information om hur du hittar borttappade iOS- enheter finns i [Hitta borttappade iOS-enheter](../remote-actions/device-locate.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Avancerade inställningar för Windows Defender-brandväggen (offentlig förhandsversion)<!--  1311949     -->  
Använd Intune för att [hantera anpassade brandväggsregler som en del av en enhetskonfigurationsprofil](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) för Endpoint Protection på Windows 10. Regler kan ange beteende för inkommande och utgående trafik till program, nätverksadresser och portar. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Uppdaterat användargränssnitt för hantering av säkerhetsbaslinjer<!-- 4091125     -->
Vi har uppdaterat [skapa och redigera-upplevelsen](../protect/security-baselines.md#create-the-profile) i Intune-konsolen för våra säkerhetsbaslinjer. Ändringarna omfattar:

Ett enklare guideformat som har komprimerats till ett enda blad. inom ett blad. Den här nya designen tar bort bladspridningen som kräver att IT-proffs måste öka detaljnivån till flera separata fönster.  
Nu kan du skapa tilldelningar som en del av skapa och redigera-upplevelsen, i stället för att behöva gå tillbaka senare för att tilldela baslinjer. Vi har lagt till en sammanfattning av de inställningar som du kan visa innan du skapar en ny baslinje och när du redigerar en befintlig. Vid redigering visar sammanfattningen bara listan över objekt som har angetts i kategorin med egenskaper som redigeras.

<!-- ########################## -->
## <a name="june-2019"></a>Juni 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>Konfigurera vilken webbläsare som ska ha tillåtelse att länka till organisationsdata<!-- 3145939 -->
Principer för Intune-appskydd (APP) på enheter med Android och iOS gör att du nu kan överföra organisationswebblänkar till en viss webbläsare utöver Intune Managed Browser eller Microsoft Edge.  Mer information om APP finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>Sidan Alla appar identifierar Microsoft Store för företagsappar online/offline<!--4089647 -->
Sidan **Alla appar** innehåller nu etiketter för att identifiera Microsoft Store-appar för företag (MSFB) som online- eller offline-appar. Varje MSFB-app innehåller nu ett suffix för **online** eller **offline**. Sidan med information om appen innehåller också **Licenstyp** och **stöder enhetskontextinstallation** (endast offline-licensierade appar).

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Företagsportalappen på delade Windows-enheter<!--4393553 -->
Användare kan nu komma åt företagsportalappen på delade Windows-enheter. Slutanvändare ser en **Delad** etikett på enhetspanelen. Detta gäller version 10.3.45609.0 och senare av Windows företagsportalappen.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>Visa alla installerade appar från den nya webbplatsen för företagsportalen<!-- 4224326 -->
Företagsportalens webbplats har en ny sida för **Installerade appar** som visar alla hanterade appar, både nödvändiga och tillgängliga, som är installerade på en användares enhet. Förutom tilldelningstyp kan användare se appens utgivare, utgivningsdatum och aktuell installationsstatus. Om din organisation inte gör appar obligatoriska eller tillgängliga ser användarna ett meddelande som förklarar att inga företagsappar har installerats. Om du vill se den nya sidan på webben går du till den [företagsportalwebbplatsen](https://portal.manage.microsoft.com) och klickar på **Installerade appar**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>I nästa vy kan appanvändare se alla hanterade appar som har installerats på enheten<!-- 2352913 -->  
Företagsportalappen för Windows visar alla hanterade appar, både nödvändiga och tillgängliga, som är installerade på en användares enhet. Användare kommer att kunna visa installationsförsök och väntande installationer, och deras aktuella status. Om din organisation inte gör appar obligatoriska eller tillgängliga ser användarna ett meddelande som förklarar att inga företagsappar har installerats. Om du vill se den nya vyn, gå till företagsportalens navigeringsfönster och välj **Appar** > **Installerade appar**.

#### <a name="new-features-in-microsoft-intune-app"></a>Nya funktioner i Microsofts Intune-app
Vi har lagt till nya funktioner i Microsoft Intune-appen (förhandsversion) för Android. Användare på fullständigt hanterade Android-enheter kan nu  

* visa och hantera enheterna som de har registrerat genom Intune-företagsportalen eller Microsoft Intune-appen
* kontakta sin organisation för support
* skicka feedback till Microsoft
* visa villkor och bestämmelser, om sådana har angetts av deras organisation.

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>Nya exempelappar som visar Intune SDK-integrering tillgänglig på GitHub<!-- 2653471 -->
GitHub-kontot msintuneappsdk har lagt till nya exempelprogram för iOS (Swift), Android, Xamarin.iOS, Xamarin Forms och Xamarin.Android. De här apparna är avsedda som komplement till vår befintliga dokumentation och visar hur du integrerar Intune APP SDK i dina egna mobilappar. Om du är apputvecklare och behöver ytterligare hjälp med Intune SDK hittar du fler exempel i de här länkarna:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) – en snabbmeddelandeapp för ursprungligt iOS-system (Swift) som använder Azure Active Directory Authentication Library (ADAL) för asynkron autentisering.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) – en att-göra-lista-app för ursprungligt Android-system som använder ADAL för asynkron autentisering.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) – en att-göra-lista-app för Xamarin.Android som använder ADAL för asynkron autentisering, den här lagringsplatsen har också Xamarin.Forms-appen.
- [Xamarin.iOS-exempelapp](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) – en Xamarin.iOS-exempelapp för barebonedatorer.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Konfigurera inställningar för kerneltillägg på macOS-enheter<!-- 2043024 -->
På macOS-enheter kan du skapa en enhetskonfigurationsprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **macOS** som plattform). Denna uppdatering inkluderar en ny grupp med inställningar som gör att du kan konfigurera och använda kerneltillägg på dina enheter. Du kan lägga till vissa tillägg eller tillåta alla tillägg från en speciell partner eller utvecklare.

Mer information om den här funktionen finns i [översikt över kerneltillägg](../configuration/kernel-extensions-overview-macos.md) och [inställningar för kerneltillägg](../configuration/kernel-extensions-settings-macos.md).

Gäller för: macOS 10.13.2 och senare

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Appar från inställningen Endast Store för Windows 10-enheter innehåller fler konfigurationsalternativ<!-- 2697002 -->
När du skapar en enhetsbegränsningsprofil för Windows-enheter kan du använda inställningen **Appar endast från Store**. Det gör att användare endast installerar appar från Windows App Store (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp). I den här uppdateringen kommer inställningen att expanderas för att stödja fler alternativ.

Gå till [Enhetsinställningar för Windows 10 (och senare) för att tillåta eller begränsa funktioner](../configuration/device-restrictions-windows-10.md#app-store) för att se den nya inställningen.

Gäller för: Windows 10 och senare

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>Distribuera flera Zebra Mobility Extensions-enhetsprofiler till en enhet, samma användargrupp eller samma grupp av enheter<!-- 4089955 -->
I Intune kan du använda Zebra Mobility Extensions (MX) i en profil för enhetskonfiguration för att anpassa inställningar för Zebra-enheter som inte är inbyggda i Intune. För närvarande kan du distribuera en profil till en enskild enhet. I den här uppdateringen kan du distribuera flera profiler till:
- Samma användargrupp
- Samma enhetsgrupp
- En enskild enhet

[Använda och hantera Zebra-enheter med Zebra Mobility Extensions i Microsoft Intune](../configuration/android-zebra-mx-overview.md) visar hur du använder MX i Intune.

Gäller för: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>Vissa inställningar för helskärmsläge på iOS-enheter är angivna till ”Blockera”, vilket ersätter ”Tillåt”<!-- 4404075  -->
När du skapar en enhetsbegränsningsprofil på iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Helskärmsläge**) ställer du in **Autolås**, **Ringsignalsknapp**, **Skärmrotation**, **Viloläge för skärm-knapp** och **Volymknappar**.

I denna uppdatering är värdena **Blockera** (blockerar funktionen) och **Inte konfigurerat** (tillåter funktionen). Om du vill se inställningarna går du till [iOS-enhetsinställningar för att tillåta eller begränsa funktioner](../configuration/device-restrictions-ios.md#kiosk).

Gäller för: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>Använd Face ID för lösenordsautentisering på iOS-enheter<!-- 4490704 -->
När du skapar en enhetsbegränsningsprofil för iOS-enheter kan du använda ett fingeravtryck som lösenord. Inställningarna för lösenord med fingeravtryck tillåter även ansiktsigenkänning i denna uppdatering (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Lösenord**). Därför ändras följande inställningar:

- **Upplåsning med fingeravtryck** är nu **Upplåsning av Touch ID och Face ID**.
- **Ändring av fingeravtryck (endast övervakat)** är nu **Ändring av Touch ID och Face ID (endast övervakat)** .

Face ID är tillgängligt i iOS 11.0 och senare. Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md#password) för att se inställningarna.

Gäller för: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>Begränsning av spel och App Store-funktioner på iOS-enheter är nu beroende av klassificeringsregion<!-- 4593948 -->
På iOS-enheter kan du tillåta eller begränsa funktioner för spel, App Store och dokumentvisning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel**). Du kan också välja klassificeringsregion, till exempel USA.

I denna uppdatering är funktionen **Appar** underordnad **klassificeringsregion** och är beroende av **klassificeringsregion**. Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming) för att se inställningarna.

Gäller för: iOS

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Windows autopilot-stöd för Hybrid Azure AD-anslutning<!-- 4809146-->
Windows autopilot för befintliga enheter stöder nu hybrid Azure AD-anslutning (förutom det befintliga stödet för Azure AD-anslutning). Gäller för Windows 10 version 1809 och senare enheter. Mer information finns i [Windows Autopilot för befintliga enheter](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Se säkerhetskorrigeringsnivå för Android-enheter<!-- 4461911 -->
Du kan nu se säkerhetskorrigeringsnivå för Android-enheter. Det gör du genom att välja **Intune** > **Enheter** > **Alla enheter** > välj en enhet > **Maskinvara**.
Korrigeringsnivån visas i avsnittet **Operativsystem**.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Tilldela omfångstaggar till alla hanterade enheter i en säkerhetsgrupp<!-- 3173810 -->
Du kan nu tilldela omfångstaggar till en säkerhetsgrupp, och alla enheter i säkerhetsgruppen kommer också att associeras med omfångstaggarna i en kommande uppdatering. Alla enheter i grupperna kommer också att tilldelas omfångstaggen. Omfångstaggar med den här funktionen skriver över omfångstaggar med det aktuella flödet för enhetens omfångstaggar. Mer information finns i [Använda RBAC och omfångstaggar för distribuerad IT](scope-tags.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="use-keyword-search-with-security-baselines------"></a>Använd nyckelordssökning med säkerhetsbaslinjer<!--  -->
När du skapar eller redigerar [Profiler för säkerhetsbaslinje](../protect/security-baselines.md#create-the-profile) kan du ange nyckelord i det nya *Sök*-fältet för att filtrera tillgängliga grupper med inställningar till de som innehåller dina sökvillkor.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>Funktionen säkerhetsbaslinjer är nu allmänt tillgänglig<!-- 3785395 -->
Funktionen **Säkerhetsbaslinjer** är inte längre i förhandsversionen utan är allmänt tillgänglig.  Det innebär att funktionen är klar att användas i produktion. De enskilda baslinjemallarna kan dock bevaras i förhandsversionen och utvärderas och publiceras som allmänt tillgängliga enligt sina egna scheman.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>Mallen för MDM-säkerhetsbaslinjer är nu allmänt tillgänglig<!-- 3794072, 4217151,  3534649 -->
Mallen för MDM-säkerhetsbaslinjer är inte längre i förhandsversionen utan är nu allmänt tillgänglig. Mallen för allmän tillgänglighet identifieras som **MDM-säkerhetsbaslinje för maj 2019**.  Det här är en ny mall och inte en uppgradering från förhandsversionen.  Som en ny mall måste du granska [inställningarna den innehåller](../protect/security-baseline-settings-mdm.md)och sedan skapa nya profiler för att distribuera mallen till din enhet. Andra säkerhetsbaslinjer kan finnas kvar i förhandsversionen. En lista över tillgängliga baslinjer finns i [tillgängliga säkerhetsbaslinjer](../protect/security-baselines.md#available-security-baselines).  

Förutom att vara en ny mall innehåller mallen *MDM-säkerhetsbaslinjen för maj 2019* de två inställningar som vi nyligen presenterade i vår utvecklingsartikel:  
- På låsskärmen: Röstaktivera appar från en låst skärm  
- DeviceGuard: Använd virtualiseringsbaserad säkerhet (VBS) vid nästa omstart av enheter.  

*MDM-säkerhetsbaslinjen för maj 2019* innehåller också tillägg av flera nya inställningar, borttagning av andra och granskning av standardvärdet för en inställning. En detaljerad lista över ändringarna från förhandsgranskning till allmänt tillgänglig finns i **Vad som har ändrats i den nya mallen**.

#### <a name="security-baseline-versioning---3194322---"></a>Versioner av säkerhetsbaslinjer<!-- 3194322 -->
Säkerhetsbaslinjer för version av Intune-support. Då nya versioner av varje säkerhetsbaslinje släpps med detta stöd kan du uppdatera dina befintliga säkerhetsbaslinjeprofiler till att använda den nya baslinjeversionen utan att behöva återskapa och distribuera en ny baslinje från grunden. I Intune-konsolen kan du också visa information om varje baslinje, till exempel antalet enskilda profiler som använder baslinjen, hur många av de olika baslinjeversionerna som dina profiler använder och när den senaste versionen av en viss säkerhetsbaslinje släpptes.  Mer information finns i **Säkerhetsbaslinjer**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>Inställningen Använd säkerhetsnycklar för inloggning har flyttats<!-- 4501151 -->
Enhetskonfigurationsinställningen för identitetsskydd med namnet **Använd säkerhetsnycklar för inloggning** finns inte längre som en delinställning för att *Konfigurera Windows Hello för företag*. Nu är det en inställning på översta nivån som alltid är tillgänglig, även när du inte aktiverar användning av Windows Hello för företag. Mer information finns i [Identitetsskydd](../protect/identity-protection-windows-settings.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>Nya behörigheter för tilldelade gruppadministratörer<!-- 4504437   -->
Intunes inbyggda skoladministratörsroll har nu behörighet att skapa, läsa, uppdatera och ta bort (CRUD) tillstånd för hanterade appar. Uppdateringen innebär att om du är tilldelad som gruppadministratör i Intune for Education kan du nu skapa, visa, uppdatera och ta bort iOS MDM-pushcertifikat, iOS MDM-tokens och iOS VPP-token tillsammans med [alla befintliga behörigheter som du har](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Om du vill vidta någon av dessa åtgärder går du till **Klientinställningar** > **iOS**Enhetshantering.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Program kan använda Graph API för att anropa läsåtgärder utan användarautentiseringsuppgifter<!-- 4655885 -->
Program kan anropa Intune Graph API-läsåtgärder med appidentitet utan användarens autentiseringsuppgifter. Mer information om hur du kommer åt Microsoft Graph API för Intune finns i [Arbeta med Intune i Microsoft Graph.](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Använda omfångstaggar för appar i Microsoft Store för företag<!-- 4392555 -->
Du kan nu använda omfångstaggar för appar i Microsoft Store för företag. Mer information om omfångstaggar finns i [Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT](scope-tags.md).

<!-- ########################## -->
## <a name="may-2019"></a>Maj 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Rapportering för potentiellt skadliga appar på Android-enheter<!-- 4223162 -->
Intune tillhandahåller nu ytterligare rapporteringsinformation om potentiellt skadliga appar på Android-enheter. 

#### <a name="windows-company-portal-app---3316993---"></a>Windows företagsportalapp<!-- 3316993 -->
Windows-företagsportalappen har nu en ny sida med etiketten **Enheter**. På sidan **Enheter** ser slutanvändare alla sina registrerade enheter. Användarna ser den här ändringen i företagsportalen när de använder version 10.3.4291.0 och senare. Mer information om hur du konfigurerar företagsportalen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](../apps/company-portal-app.md).

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Uppdatering av Intune-principers autentiseringsmetod och installation av företagsportalappen<!-- 1927359  -->
På enheter som redan har registrerats via Installationsassistenten med någon av Apples metoder för registrering av företagsenheter, stöder Intune inte längre företagsportalen om den installeras manuellt av slutanvändarna från App Store. Den här ändringen gäller endast när du autentiserar med Apple-installationsassistenten under registreringen. Den här ändringen påverkar också bara iOS-enheter som registrerats via:  
* Apple configurator
* Apple Business Manager
* Apple School Manager
* Apples program för enhetsregistrering (DEP)

Om användare installerar företagsportalappen från App store och sedan försöker att registrera enheterna genom den, får de ett felmeddelande. Dessa enheter kommer förväntas att bara använda företagsportalen när den har skickats automatiskt av Intune under registreringen. Profiler för registrering i Intune i Azure-portalen kommer att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Om du vill att dina DEP-enhetsanvändare ska ha företagsportalen behöver du ange dina preferenser i en registreringsprofil. 

Dessutom håller skärmen **Identifiera din enhet** i iOS-företagsportalen på att tas bort. Administratörer som vill aktivera villkorlig åtkomst eller distribuera företagsappar måste därför uppdatera profilen för DEP-registrering. Det här kravet gäller endast om DEP-registrering har verifierats med Installationsassistenten. I så fall måste du installera företagsportalen på enheten. För att göra det ska du välja **Intune** > **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram** > välja en token > **Profiler** > välja en profil > **Egenskaper** > och ställa in **Installera företagsportal** på **Ja**.

För att installera företagsportalen på redan registrerade DEP-enheter måste du gå till Intune > Klientappar och installera den som en hanterad app med konfigurationsprinciper för appar. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>Konfigurera hur användarna uppdaterar en affärsapplikation (LOB)-app med hjälp av en appskyddsprincip<!-- 3568384 -->
Du kan nu konfigurera var användarna kan få en uppdaterad version av en affärsapplikation (LOB). Slutanvändarna ser den här funktionen i dialogen för villkorlig start **Lägsta appversion**, där slutanvändarna uppmanas att uppdatera till en lägsta version av LOB-appen. Du måste ange denna uppdateringsinformation som en del av din LOB-appskyddsprincip (APP). Den här funktionen är tillgänglig för iOS och Android. På iOS kräver den här funktionen att appen integreras (eller packas in med hjälp av programhanteringsverktyget) med Intune SDK för iOS v. 10.0.7 eller senare. På Android kräver funktionen den senaste företagsportalen. Om du vill konfigurera hur en slutanvändare uppdaterar en LOB-app behöver appen en hanterad appkonfigurationspolicy som skickas till den med nyckeln, `com.microsoft.intune.myappstore`. Det skickade värdet anger vilket lager som slutanvändaren laddar ner appen från. Om appen distribueras via företagsportalen måste värdet vara `CompanyPortal`. Du måste ange en fullständig URL för andra lager.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>PowerShell-skript i Intune-hanteringstillägget<!-- 3734186  -->
Du kan konfigurera PowerShell-skript så att det körs med användarens administratörsprivilegier på enheten. Mer information finns i [Använda PowerShell-skript på Windows 10-enheter i Intune](../apps/intune-management-extension.md) och [Win 32-apphantering](../apps/app-management.md).

#### <a name="android-enterprise-app-management---4459905---"></a>Apphantering med Android Enterprise<!-- 4459905 -->
Intune lägger automatiskt till fyra vanliga Android Enterprise-relaterade appar till Intune-administratörskonsolen för att göra det enklare för IT-administratörer att konfigurera och använda Android Enterprise-hantering. Detta är de fyra Android Enterprise-apparna:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – Används för fullständigt hanterade Android Enterprise-scenarier.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – Hjälper dig att logga in på dina konton om du använder tvåfaktorautentisering.
- **[Intune-företagsportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – Används för appskyddsprinciper och scenarier med Android Enterprise-arbetsprofiler.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) – Används för dedikerade/helskärmslägesscenarier i Android Enterprise.

Tidigare var IT-administratörer tvungna att hitta och godkänna de här apparna manuellt i den [hanterade Google Play-butiken](https://play.google.com/store/apps) som en del av konfigurationen. Den här ändringen tar bort de tidigare manuella stegen för att göra det enklare och snabbare för kunder att använda Android Enterprise-hantering.

Administratörer kommer att se att dessa fyra appar läggs till i listan över appar i Intune automatiskt när de ansluter Intune-klienten till hanterade Google Play för första gången. Läs [Anslut ditt Intune-konto till ditt hanterade Google Play-konto](../enrollment/connect-intune-android-enterprise.md) för mer information. Administratörer behöver inte göra något för klienter som redan har anslutit sin klient eller som redan använder Android Enterprise. De fyra apparna visas automatiskt inom sju dagar efter slutförandet av tjänstlanseringen under maj 2019.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>Uppdaterat PFX-certifikatanslutningsprogram för Microsoft Intune<!-- 1533038 -->
Vi har släppt en uppdatering för [PFX-certifikatanslutningsappen för Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) som löser problemet där befintliga PFX-certifikat fortsätter att bearbetas, vilket orsakar att anslutningsappen slutar att bearbeta nya begäranden.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Intune-säkerhetsuppgifter för Defender ATP (i allmänt tillgänglig förhandsversion)<!-- 3208597 -->
Du kan använda Intune för att hantera [säkerhetsuppgifter för Microsoft Defender Advanced Threat Protection (ATP) i den allmänt tillgängliga förhandsversionen](../protect/atp-manage-vulnerabilities.md). Det här möjliggör integrering med ATP och lägger till en riskbaserad metod för att identifiera, prioritera och åtgärda säkerhetsrisker och felkonfigurationer på slutpunkter, samtidigt som det minskar tiden mellan identifiering till problemlösning.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671-----"></a>Söka efter en TPM-kretsuppsättning i en efterlevnadsprincip för Windows 10-enheter<!-- 3617671   -->
Många Windows 10-enheter och senare enheter har TPM-kretsuppsättningar (Trusted Platform Module). Den här uppdateringen innehåller en ny efterlevnadsinställning som kontrollerar versionen på TPM-chippet i enheten.

[Inställningar för kompatibilitetsprinciper i Windows 10 och senare](../protect/compliance-policy-create-windows.md#device-security) beskriver den här inställningen.

Gäller för: Windows 10 och senare

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>Förhindra slutanvändare från att ändra sin Internetdelning och inaktivera Siri-serverloggning på iOS-enheter<!-- 4097904   -->  
Du kan skapa en enhetsbegränsningsprofil på en iOS-enhet (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp). Den här uppdateringen innehåller nya inställningar som du kan konfigurera:

- **Inbyggda appar**: Loggning på serversidan av Siri kommandon
- **Trådlöst**: Användarmodifiering av internetdelning (endast övervakat)

Om du vill se de här inställningarna går du till [inbyggda app-inställningar för iOS](../configuration/device-restrictions-ios.md#built-in-apps) och [trådlösa inställningar för iOS](../configuration/device-restrictions-ios.md#wireless).

Gäller för: iOS 12.2 och senare

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>Nya inställningar för enhetsbegränsning i appen Klassrum för macOS-enheter<!-- 4097905   --> 
Du kan skapa profiler för enhetskonfiguration för macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsbegränsningar** för profiltyp). Den här uppdateringen innehåller nya inställningar för appen Klassrum, alternativet att blockera skärmbilder och inaktivera iCloud-bildbiblioteket.

Gå till [macOS-enhetsinställningar för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-macos.md) för att se de aktuella inställningarna.

Gäller för: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>iOS lösenordet för åtkomst till appbutiksinställningen har bytt namn<!-- 4557891  -->
Inställningen **Lösenord till appbutik** har bytt namn till **Kräv iTunes Store-lösenord för alla köp** (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel**).

Om du vill se de tillgängliga inställningarna går du till [iOS-inställningar för App Store, dokumentvisning, spel](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gäller för: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Baslinjer för Microsoft Defender Advanced Threat Protection (Förhandsversion)<!--  3754134 -->
Vi har lagt till en förhandsversion med säkerhetsbaslinje för [Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md)-inställningar. Denna baslinje finns tillgänglig när din miljö uppfyller förhandskraven för att använda [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites).

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Outlook-signatur och biometriska inställningar för iOS och Android-enheter<!-- 4050557 -->
Du kan nu ange om standardsignaturen är aktiverad i Outlook för iOS och Android-enheter. Dessutom kan du välja om du vill tillåta användare att ändra den biometriska inställningen i Outlook för iOS.

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>Stöd för Network Access Control (NAC) för F5 Access för iOS-enheter<!-- 4500808 -->
F5 släppte en uppdatering för BIG-IP-13 som tillåter NAC-funktioner för F5 Access på iOS i Intune. Gör så här för att använda funktionen:

- Uppdatera BIG-IP till 13.1.1.5. BIG-IP 14 stöds inte.
- Integrera BIG-IP med Intune för NAC. Stegen i [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html) (Översikt: Konfigurera APM för enhetsstatuskontroller med slutpunktshanteringssystem).
- Aktivera inställningen **Aktivera nätverksåtkomstkontroll** i VPN-profilen i Intune.

Om du vill se den tillgängliga inställningen går du till [Konfigurera VPN-inställningar på iOS-enheter](../configuration/vpn-settings-ios.md).

Gäller för: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>Uppdaterat PFX-certifikatanslutningsprogram för Microsoft Intune<!-- doc-vso 1521237  -->  
Vi har släppt en uppdatering till [PFX-certifikatanslutningsappen för Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) som utelämnar avsökningsintervallet från 5 minuter till 30 sekunder.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>OrderID-attributet på Autopilot-enheter har bytt namn till Grupptagg <!-- 4659453 -->

För att göra det mer intuitivt har **OrderID**-attributets namn på Autopilot-enheter ändrats till **Grupptagg**. När du använder CSV-filer för att ladda upp Autopilot-enhetsinformation måste du använda Grupptagg som kolumnrubrik, inte OrderID.  

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Windows registreringsstatussida (ESP) är nu allmänt tillgänglig<!-- 3605348 -->
Registreringsstatussidan är inte längre en förhandsversion. Mer information finns i [Konfigurera en sida för registreringsstatus](../enrollment/windows-enrollment-status.md).

#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Uppdatering av användargränssnittet i Intune – Skapa Autopilot-registreringsprofil<!-- 4593669 -->
Användargränssnittet för att skapa en Autopilot-profil för registrering har uppdaterats så att den överensstämmer med Azures användargränssnitt. Mer information finns i [Skapa en Autopilot-registreringsprofil](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). Framöver kommer ytterligare Intune scenarier att uppdateras till det här nya användargränssnittet.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>Aktivera Autopilot-återställning av alla Windows-enheter<!-- 4225665 -->
Autopilot-återställning fungerar nu för alla Windows-enheter, även de som inte har konfigurerats för att använda registreringsstatussidan. Om en registreringsstatussida inte har konfigurerats för enheten under den första enhetsregistreringen kommer enheten att gå direkt till skrivbordet efter inloggningen. Det kan ta upp till åtta timmar att synkroniseras och visas som kompatibel i Intune. Mer information finns i [Återställa enheter med fjärransluten Windows Autopilot-återställning](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>Exakta IMEI-format krävs inte när du söker igenom alla enheter<!--30407680 -->
Du behöver inte ta med mellanslag i IMEI-nummer när du söker igenom **Alla enheter**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>Om du tar bort en enhet i Apples portal visas ändringen även i Intune-portalen<!--2489996 -->
Om en enhet tas bort från Apples program för enhetsregistrering eller Apple Business Manager-portalen tas den även automatiskt bort från Intune vid nästa synkronisering.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>Registreringsstatussidan spårar nu Win32-appar<!-- 2714451 -->
Detta gäller endast enheter som kör Windows 10, version 1903 och senare. Mer information finns i [Konfigurera en sida för registreringsstatus](../enrollment/windows-enrollment-status.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Återställa och rensa enheter i grupp med hjälp av Graph API<!-- 3295288 -->
Du kan nu återställa och rensa upp till 100 enheter i grupp med Graph API.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>Krypteringsrapport är inte längre en allmänt tillgänglig förhandsversion<!-- 4587546      -->
[Rapporten för kryptering av BitLocker och enheter](../protect/encryption-monitor.md) är nu allmänt tillgänglig och inte längre en del av förhandsversionen.


<!-- ########################## -->
## <a name="april-2019"></a>April 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering
#### <a name="user-experience-update-for-the-company-portal-app-for-ios---2536024---"></a>Uppdatering av användarupplevelsen för företagsportalappen för iOS<!-- 2536024 -->
Startsidan för företagsportalappen för iOS-enheter har fått en ny design. Med den här ändringen följer startsidan mönstren för iOS-användargränssnitt på ett bättre sätt och gör dessutom appar och e-böcker mer lätthittade.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users--3448635---"></a>Ändringar i företagsportalregistrering för iOS 12-enhetsanvändare<!--3448635 -->
Registreringsskärmarna och stegen för företagsportalen för iOS har uppdaterats så att de överensstämmer med de ändringar av MDM-registrering som lanserades i Apple iOS 12.2. Det uppdaterade arbetsflödet uppmanar användaren att:  

* Tillåta att Safari öppnar webbplatsen för företagsportalen och laddar ned hanteringsprofilen innan den går tillbaka till företagsportalappen.  
* Öppna inställningsappen för att installera hanteringsprofilen på enheten.
* Gå tillbaka till företagsportalappen för att slutföra registreringen.  

Uppdaterade steg och skärmar för registrering finns i avsnittet om att [registrera iOS-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).

#### <a name="openssl-encryption-for-android-app-protection-policies---3747362---"></a>OpenSSL-kryptering för Android-appskyddsprinciper<!-- 3747362 -->
Intune-appskyddsprinciper (APP) på Android-enheter använder nu ett OpenSSL-krypteringsbibliotek som är kompatibelt med FIPS 140-2. Mer information finns i avsnittet för [kryptering](../apps/app-protection-policy-settings-android.md#encryption) i [Inställningar för Android-appskyddsprinciper i Microsoft Intune](../apps/app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies---2617348----"></a>Aktivera Win32-appsamband<!-- 2617348  -->
Som administratör kan du kräva du att andra appar installeras som beroenden innan Win32-appen installeras. Mer specifikt måste enheten installera de beroende apparna innan den installerar Win32-appen. I Intune väljer du **Klientappar** > **Appar** > **Lägg till** för att visa bladet **Lägg till app**. Välj **Windows-app (Win32)** som **Apptyp**. När du har lagt till appen kan du välja **Beroenden** för att lägga till de beroende appar som måste installeras innan Win32-appen kan installeras. Mer information finns i [Fristående Intune – Win32-apphantering](./../apps/app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps---3537391-----"></a>Installationsinformation om appversion för Microsoft Store för företagsprogram<!-- 3537391   -->
Rapporter för appinstallation innehåller information om appversion för Microsoft Store för företagsprogram. I Intune väljer du **Klientappar** > **Appar**. Välj en **Microsoft Store för företag-app** och välj sedan **Installationsstatus för enhet** i avsnittet **Övervaka**.

#### <a name="additions-to-win32-apps-requirement-rules---3676883-----"></a>Tillägg till reglerna för krav för Win32-appar<!-- 3676883   -->
Du kan skapa kravregler baserat på PowerShell-skript, registervärden och filsysteminformation. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **Windows-app (Win32)** som **Apptyp** på bladet **Lägg till app**.  Välj **Krav** > **Lägg till** för att konfigurera ytterligare kravregler. Sedan väljer du antingen **Filtyp**, **Register** eller **Skript** som **Typ av krav**. Mer information finns i [Win32-apphantering](./../apps/app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices---3695227----"></a>Konfigurera Win32-appar att installeras på Intune-registrerade Azure AD-anslutna enheter<!-- 3695227  -->
Du kan konfigurera Win32-appar att installeras på Intune-registrerade Azure AD-anslutna enheter. Mer information om Win32-appar i Intune finns i [Win32-apphantering](./../apps/app-management.md).

#### <a name="device-overview-shows-primary-user--3794259----"></a>Enhetsöversikt som visar primär användare<!--3794259  -->
På sidan för enhetsöversikt visas den primära användaren, som även kallas användartillhörighetsanvändaren (UDA). Om du vill se den primära användaren för en enhet väljer du **Intune** > **Enheter** > **Alla enheter** > välj en enhet. Den primära användaren visas nästan längst upp på sidan **Översikt**.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices---4105925----"></a>Ytterligare rapportering för Managed Google Play-app för Android Enterprise-arbetsprofilenheter<!-- 4105925  -->
För Managed Google Play-appar som distribueras till Android Enterprise-arbetsprofilenheter kan du visa det specifika versionsnumret för den app som är installerad på en enhet. Det här gäller endast för obligatoriska appar.  

#### <a name="ios-third-party-keyboards---4111843-----"></a>iOS-tangentbord från tredje part<!-- 4111843   -->
Stödet för Intunes appskyddsprincip (APP) för inställningen **Tangentbord från tredje part** för iOS kommer att tas bort på grund av en iOS-plattformsändring. Du kommer inte att kunna konfigurera den här inställningen i Intune-administratörskonsolen och den kommer inte att tillämpas på klienten i Intune App SDK.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="updated-certificate-connectors---icm-113304612---"></a>Uppdaterade certifikatanslutningsappar<!-- ICM 113304612 -->
Vi har släppt uppdateringar för både [Intune-certifikatanslutningsappen och PFX-certifikatanslutningsappen för Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors). De nya versionerna åtgärdar flera kända problem.

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices---1210083----"></a>Ange inställningarna för inloggning och kontrollera omstartsalternativ på macOS-enheter<!-- 1210083  -->
På macOS-enheter kan du skapa en profil för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **macOS** för plattformen > **Enhetsfunktioner** för profiltypen). Den här uppdateringen innehåller nya inställningar för inloggningsfönstret, till exempel att visa en anpassad banderoll, ändra hur användare loggar in, visa eller dölja energiinställningarna och mer.

Om du vill se de här inställningarna går du till [inställningarna för iOS-enhetsfunktioner](../configuration/macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode--3041940----"></a>Konfigurera Wi-Fi på enhetsägardedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar<!--3041940  -->
Du kan aktivera inställningar på Android Enterprise-enhetsägarenheter när de körs som dedikerade enheter i helskärmsläge för flera appar. I den här uppdateringen kan du ge användare möjlighet att konfigurera och ansluta till Wi-Fi-nätverk (**Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetens ägare, Enhetsbegränsningar** för profiltyp > **Dedikerade enheter** > **Helskärmsläge**: **Flera appar** > **WiFi-konfiguration**).

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md).

Gäller för: Dedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar

#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041941----"></a>Konfigurera Bluetooth och parkoppling på enhetsägardedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar<!-- 3041941  -->
Du kan aktivera inställningar på Android Enterprise-enhetsägarenheter när de körs som dedikerade enheter i helskärmsläge för flera appar. I den här uppdateringen kan du tillåta slutanvändare att aktivera Bluetooth och parkoppla enheter via Bluetooth (**Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetens ägare, Enhetsbegränsningar** för profiltyp > **Dedikerade enheter** > **Helskärmsläge**: **Flera appar** > **Bluetooth-konfiguration**).

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md).

Gäller för: Dedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune---3305883----"></a>Skapa och använda OEMConfig-profiler för enhetskonfiguration i Intune<!-- 3305883  -->
I den här uppdateringen stöder Intune konfiguration av Android Enterprise-enheter med OEMConfig. Mer specifikt kan du kan skapa en profil för enhetskonfiguration och använda inställningar för Android Enterprise-enheter med hjälp av OEMConfig (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform).

Stöd för OEM-tillverkare sker för närvarande per varje enskild OEM. Om en OEMConfig-app som du vill ha inte finns i listan över OEMConfig-appar kan du kontakta `IntuneOEMConfig@microsoft.com`.

Om du vill veta mer om den här funktionen kan du gå till [Använda och hantera Android Enterprise-enheter med OEMConfig i Microsoft Intune](../configuration/android-oem-configuration-overview.md).

Gäller för: Android Enterprise

#### <a name="windows-update-notifications---3316758-3316782----"></a>Windows Update-meddelanden<!-- 3316758, 3316782  -->
Vi har lagt till två *inställningar för användarupplevelse* i de konfigurationer av Windows Update-uppdateringsring som du kan hantera från Intune-konsolen. Nu kan du:
- Blockera eller tillåta användare att [söka efter Windows-uppdateringar](../protect/windows-update-settings.md).
- Hantera den [Windows Update-meddelandenivå](../protect/windows-update-settings.md) som användarna ser.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner---3574254----"></a>Nya inställningar för enhetsbegränsningar för enhetsägarbaserad Android Enterprise<!-- 3574254  -->
På Android Enterprise-enheter kan du skapa en profil för enhetsbegränsningar för att tillåta eller begränsa funktion, ange lösenordsregler och mer (**Enhetskonfiguration** > **Profiler** > **Skaoa profil** > välj **Android Enterprise** för plattform > **Endast enhetsägare > Enhetsbegränsningar** för profiltyp). 

Den här uppdateringen innehåller nya lösenordsinställningar, ger fullständig åtkomst till appar i Google Play Store för fullständigt hanterade enheter och mer. Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md). 

Gäller för: Fullständigt hanterade Android Enterprise-enheter

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---"></a>Söka efter en TPM-kretsuppsättning i en efterlevnadsprincip för Windows 10-enheter<!-- 3617671 -->

Den här funktionen är försenad och planeras att släppas senare.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices---3775833-----"></a>Uppdaterade ändringar av användargränssnittet för webbläsaren Microsoft Edge på enheter med Windows 10 och senare<!-- 3775833   -->
När du skapar en profil för enhetskonfiguration kan du tillåta eller begränsa Microsoft Edge-funktioner på enheter med Windows 10 och senare (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp >  **Microsoft Edge-webbläsaren**). I den här uppdateringen beskrivs Microsoft Edge-inställningar mer utförligt och är enklare att förstå.

Om du vill se de här funktionerna går du till [inställningarna för enhetsbegränsningar i Microsoft Edge-webbläsaren](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

Gäller för: Windows 10 och senare

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-----3903241-3903244-3903246-----"></a>Utökat stöd för fullständigt hanterade Android Enterprise-enheter (förhandsversion)<!--   3903241, 3903244, 3903246   -->
Fullständigt hanterade Android Enterprise-enheter som först tillkännagavs i januari 2019 är fortfarande i offentlig förhandsversion, men vi har utökat stödet för dem till att omfatta följande:

- På fullständigt hanterade och dedikerade enheter kan du skapa [efterlevnadsprinciper](../protect/compliance-policy-create-android-for-work.md) till att omfatta lösenordsregler och operativsystemkrav (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Android Enterprise** för plattform > **Enhetsägare** för profiltyp).

  På dedikerade enheter kan enheten visas som **Inte kompatibel**. Villkorlig åtkomst är inte tillgängligt på dedikerade enheter. Se till att slutföra alla uppgifter eller åtgärder för att göra så att dedikerade enheter uppfyller dina tilldelade principer.

- [Villkorlig åtkomst](../protect/conditional-access.md) – principer för villkorlig åtkomst som gäller för Android gäller även för fullständigt hanterade Android Enterprise-enheter. Användare kan nu registrera sina fullständigt hanterade enheter i Azure Active Directory med hjälp av **Microsoft Intune-appen**. Sedan undersöker och åtgärdar du eventuella efterlevnadsproblem för att få åtkomst till organisationens resurser.

- Ny app för slutanvändare (Microsoft Intune-appen) – det finns en ny app för slutanvändare för fullständigt hanterade Android-enheter som heter **Microsoft Intune**. Den här nya appen är enkel och modern. Den har funktioner som liknar företagsportalappen men för fullständigt hanterade enheter. Mer information finns i [Microsoft Intune-appen på Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

För att konfigurera fullständigt hanterade Android-enheter, gå till **Enhetsregistrering** > **Android-registrering** > **Företagsägda, fullständigt hanterade användarenheter**. Stöd för fullständigt hanterade Android-enheter är fortfarande i förhandsversion, och vissa Intune-funktioner är kanske inte helt funktionella.  

Mer information om den här förhandsversionen finns på vår blogg, [Microsoft Intune – förhandsversion 2 för fullständigt hanterade Android Enterprise-enheter](https://aka.ms/preview2_AE_fullymanaged).

#### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Använd Compliance Manager för att skapa utvärderingar för Microsoft Intune<!-- 4404750 -->

[Compliance Manager](https://servicetrust.microsoft.com/ComplianceManager) (öppnar en annan Microsoft-webbplats) är ett verktyg för arbetsflödesbaserad riskbedömning i Microsoft Service Trust Portal. Det gör att du kan spåra, tilldela och verifiera din organisations aktiviteter för regelefterlevnad aktiviteter relaterade till Microsoft-tjänster. Du kan skapa din egen efterlevnadsbedömning med Office 365, Azure, Dynamics, Professionella tjänster och Intune. Intune har två utvärderingar – FFIEC och GDPR.

Compliance Manager hjälper dig att fokusera arbetet genom att dela in kontroller – kontroller som hanteras av Microsoft samt kontroller som hanteras av din organisation. Du kan slutföra utvärderingarna och sedan exportera och skriva ut dem.

Efterlevnad med [Federal Financial Institutions Examination Council (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (öppnar en annan Microsoft-webbplats) är en uppsättning standarder för onlinebanktjänster som utfärdas av FFIEC. Det är den mest efterfrågade utvärderingen för finansiella institutioner som använder Intune. Det tolkar hur Intune hjälper dem att uppfylla FFIEC-riktlinjer för cybersäkerhet relaterade till arbetsbelastningar med offentligt moln. Intunes FFIEC-utvärdering är den andra FFIEC-utvärderingen i Compliance Manager.

I följande exempel visas en analys av FFIEC-kontrollerna. Microsoft hanterar 64 kontroller. Du ansvarar för de återstående 12 kontrollerna.

![Se ett exempel på Intune-utvärdering för FFIEC, inklusive kundåtgärderna och Microsofts åtgärder](./media/whats-new/intune-ffiec-assessment-status.png)

[Allmänna dataskyddsförordningen (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (öppnar en annan Microsoft-webbplats) är en EU-lag som hjälper till att skydda enskilda personers rättigheter och deras data. GDPR är mest efterfrågade utvärderingen för stöd med efterlevnad av sekretesskrav. 

I följande exempel visas en analys av GDPR-kontrollerna. Microsoft hanterar 49 kontroller. Du ansvarar för de återstående 66 kontrollerna.

![Se ett exempel på Intune-utvärdering för GDPR, inklusive kundåtgärderna och Microsofts åtgärder](./media/whats-new/intune-assessment-status.png)


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant---2276470----"></a>Konfigurera profilen om du vill hoppa över vissa av skärmarna i installationsassistenten<!-- 2276470  -->
När du skapar en macOS-registreringsprofil kan du konfigurera den till att hoppa över valfria följande skärmar när en användare går igenom installationsassistenten:
- Utseende
- Visningston
- iCloudStorage Om du skapar en ny profil eller redigerar en profil måste den valda överhoppningsskärmen synkroniseras med Apple MDM-servern.  Användare kan utfärda en manuell synkronisering av enheterna så att det inte sker någon fördröjning i att plocka upp profiländringarna.
Mer information finns i [Registrera macOS-enheter automatiskt med programmet för enhetsregistrering eller Apple School Manager](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Massnamngivning av enheter vid registrering av iOS-företagsenheter<!--3566569  -->
Vid användning av någon av Apples metoder för företagsregistrering (DEP/ABM/ASM) kan du ange ett format för enhetsnamn till att automatiskt namnge inkommande iOS-enheter. Du kan ange ett format som innehåller enhetstyp och serienummer i mallen. Om du vill göra det väljer du **Intune** > **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtoken** > **Välj en token** >**Skapa profil** > **Format för enhetsnamngivning**. Du kan redigera befintliga profiler, men namnet tillämpas endast på nyligen synkroniserade enheter.

#### <a name="updated-default-timeout-message-on-enrollment-status-page---3959331---"></a>Uppdaterat standardmeddelande för tidsgräns på sidan Registreringsstatus<!-- 3959331 -->
Vi har uppdaterat det standardmeddelande för tidsgräns som användare ser när sidan Registreringsstatus (ESP, Enrollment Status Page) överskrider det tidsgränsvärde som angetts i ESP-profilen. Det nya standardmeddelandet är det som användarna ser. Det hjälper dem att ta reda på vilka åtgärder som därnäst ska vidtas med deras ESP-distribution.  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="retire-noncompliant-devices---1827291-----"></a>Ta icke-kompatibla enheter ur bruk<!-- 1827291   -->
Den här funktionen har försenats och kommer i en framtida version.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta---4403765---"></a>Ändringar i Intune Data Warehouse V1.0 återspeglas i betaversionen<!-- 4403765 -->
När V1.0 introducerades i 1808 skiljde den sig från beta-API:et på några betydande sätt. I 1903 återspeglas ändringarna tillbaka till beta-API-versionen. Om du har viktiga rapporter som använder beta-API-versionen rekommenderar vi starkt att du växlar de rapporterna till V1.0 för att undvika icke-bakåtkompatibla ändringar. Mer information finns i [ändringsloggen för Intune Data Warehouse API](../developer/reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Övervaka status för säkerhetsbaslinje (offentlig förhandsversion) <!-- 3082047 --> 
Vi har lagt till en [per kategori-vy](../protect/security-baselines-monitor.md#per-category-view) i övervakningen av säkerhetsbaslinjer. (Säkerhetsbaslinjer är fortfarande i förhandsversion). Per kategori-vyn visar varje kategori från baslinjen tillsammans med procentandelen enheter som hamnar i varje statusgrupp för respektive kategori. Nu kan du se hur många enheter som inte matchar de enskilda kategorierna, är felkonfigurerade eller inte kan användas.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-apple-vpp-tokens--2371886----"></a>Omfångstaggar för Apple VPP-token<!--2371886  -->
Du kan nu lägga till omfångstaggar till Apple VPP-token. Endast användare som har tilldelats med samma omfångstagg får åtkomst till Apple VPP-token med den taggen. VPP-appar och e-böcker som köpts med den token ärver dess omfångstaggar. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar](scope-tags.md).

<!-- ########################## -->
## <a name="march-2019"></a>Mars 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering
#### <a name="deploy-microsoft-visio-and-microsoft-project---3725386----"></a>Distribuera Microsoft Visio och Microsoft Project<!-- 3725386  -->
Du kan nu distribuera Microsoft Visio Pro för Office 365 och skrivbordsklienten för Microsoft Project Online som oberoende appar till Windows 10-enheter som använder Microsoft Intune om du har licenser för dessa appar. I Intune väljer du **Klientappar** > **Appar** > **Lägg till** för att visa bladet **Lägg till app**. På bladet **Lägg till app** väljer du **Windows 10** som **Apptyp**. Välj sedan **Konfigurera appsvit** för att välja appar som ska installeras. Mer information om Office 365-appar för Windows 10-enheter finns i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change---3593653----"></a>Ändring av produktnamn för Microsoft Visio Pro för Office 365<!-- 3593653  -->
**Microsoft Visio Pro för Office 365** kommer nu att kallas **Microsoft Visio Online, abonnemang 2**.  Mer information om Microsoft Visio finns i [Visio Online, abonnemang 2](https://products.office.com/visio/visio-online-plan-2). Mer information om Office 365-appar för Windows 10-enheter finns i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting---3291302----"></a>Inställning för teckengräns för Intune-appskyddsprincip (APP)<!-- 3291302  -->
Intune-administratörer kan ange ett undantag till principinställningen **Begränsa klipp ut, kopiera och klistra in med andra appar** för Intune APP.  Som administratör kan du ange det antal tecken som kan klippas ut eller kopieras från en hanterad app. Den här inställningen tillåter delning av det angivna antalet tecken till valfri app oavsett inställningen ”Begränsa klipp ut, kopiera och klistra in med andra appar”. Observera att versionen av Intune-företagsportalappen för Android kräver version 5.0.4364.0 eller senare. Mer information finns i [iOS-dataskydd](../apps/app-protection-policy-settings-ios.md#data-protection), [Android-dataskydd](../apps/app-protection-policy-settings-android.md#data-protection) och [Granska loggarna för klientappskydd](../apps/app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment---3192477-----"></a>ODT-XML (Distributionsverktyg för Office) för Office ProPlus-distribution<!-- 3192477   -->
Du kommer att kunna tillhandahålla ODT-XML (Distributionsverktyg för Office) när du skapar en instans av Office Pro Plus i Intune-administratörskonsolen. Detta ger större anpassningsbarhet om de befintliga alternativen för användargränssnittet i Intune inte uppfyller dina behov. Mer information finns i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](../apps/apps-add-office365.md) och [Konfigurationsalternativ för distributionsverktyget för Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background---1429026----"></a>Appikoner visas nu med en automatiskt genererad bakgrund<!-- 1429026  -->
I Windows-företagsportalappen visas appikoner nu med en automatiskt genererad bakgrund som baseras på ikonens huvudsakliga färg (om den kan identifieras). När så är tillämpligt ersätter den här bakgrunden den grå kantlinje som tidigare fanns på appanelerna. Användarna ser den här ändringen i versioner senare än 10.3.3451.0 av företagsportalen.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment---2751523-----"></a>Installera tillgängliga appar med hjälp av företagsportalappen efter massregistrering för Windows<!-- 2751523   -->
Windows-enheter som registreras till Intune med hjälp av [massregistrering för Windows](../enrollment/windows-bulk-enroll.md) (etableringspaket) kommer att kunna använda företagsportalappen för att installera tillgängliga appar. Mer information om företagsportalappen finns i [Lägga till Windows 10-företagsportalen manuellt](../apps/store-apps-company-portal-app.md) och [Så konfigurerar du Microsoft Intune-företagsportalappen](../apps/company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite---3828932----"></a>Microsoft Teams-appen kan väljas som en del av Office-appsviten<!-- 3828932  -->
Microsoft Teams-appen kan inkluderas eller uteslutas som en del av installationen av Office Pro Plus-appsviten. Den här funktionen fungerar för Office Pro Plus, build-nummer 16.0.11328.20116+. Användaren måste logga ut och sedan logga in på enheten för att slutföra installationen. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. Välj en av **Office 365-svitapptyperna** och välj sedan **Konfigurera appsvit**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices---2351390---"></a>Starta en app automatiskt när flera appar körs i helskärmsläge på enheter med Windows 10 och senare<!-- 2351390 -->

På enheter med Windows 10 och senare kan du köra en enhet i helskärmsläge och köra många appar. I den här uppdateringen finns en **AutoLaunch**-inställning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Helskärmsläge** för profiltyp > **Helskärmsläge för flera appar**). Använd den här inställningen för att starta en app automatiskt när användaren loggar in på enheten.

En lista och beskrivningar av alla inställningar för helskärmsläge finns i [Inställningar för enheter med Windows 10 (och senare) som ska köras med helskärmsläge i Intune](../configuration/kiosk-settings-windows.md).

Gäller för: Windows 10 och senare

#### <a name="operational-logs-also-show-details-on-non-compliant-devices---4063755----"></a>Arbetsloggar visar även information om icke-kompatibla enheter<!-- 4063755  -->
När Intune-loggar dirigeras till Azure Monitor-funktioner kan du även dirigera arbetsloggarna. I den här uppdateringen ger arbetsloggarna även information om icke-kompatibla enheter.

Mer information om den här funktionen finns i [Skicka loggdata till lagring, händelsehubbar eller logganalys i Intune](../review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads---3804627---"></a>Dirigera loggar till Azure Monitor i fler Intune-arbetsbelastningar<!-- 3804627 -->
I Intune kan du dirigera granskningsloggar och arbetsloggar till händelsehubbar, lagring och logganalys i Azure Monitor (**Intune** > **Övervakning** > **Diagnostikinställningar**). I den här uppdateringen kan du dirigera loggarna i fler Intune-arbetsbelastningar, däribland efterlevnad, konfigurationer, klientappar och mer.

Mer information om dirigering av loggar till Azure Monitor finns i [skicka data till lagring, händelsehubbar eller logganalys](../review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune---3305880-----"></a>Skapa och använda mobilitetstillägg på Android Zebra-enheter i Intune<!-- 3305880   -->
I den här uppdateringen stöder Intune konfiguration av Android Zebra-enheter. Mer specifikt kan du skapa en profil för enhetskonfiguration och tillämpa inställningar på Android Zebra enheter med hjälp av MX-profiler (Mobility Extensions) som genereras av StageNow (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android** för plattform > **MX-profil (endast Zebra)** för profiltyp).

Mer information om den här funktionen finns i [Använd och hantera Zebra-enheter med mobilitetstillägg i Intune](../configuration/android-zebra-mx-overview.md).

Gäller för: Android

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering
#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Krypteringsrapport för Windows 10-enheter (i allmänt tillgänglig förhandsversion)<!-- 2351538 -->
Använd den nya [krypteringsrapporten (förhandsversion)](../protect/encryption-monitor.md) till att visa information om krypteringsstatusen för dina Windows 10-enheter. Bland den tillgängliga informationen finns en enhets TPM-version, krypteringsberedskap och -status, felrapportering och mer.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview---2351547-----"></a>Använd BitLocker-återställningsnycklar från Intune-portalen (i allmänt tillgänglig förhandsversion)<!-- 2351547   -->
Du kan nu använda Intune för att [visa information](../protect/encryption-monitor.md) om BitLocker-nyckel-ID och BitLocker-återställningsnycklar från Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>Microsoft Edge-stöd för Intune-scenarier i iOS-enheter och Android-enheter<!-- 3411007 -->
Microsoft Edge kommer att stödja samma hanteringsscenarier som Intune Managed Browser samt förbättringar av användarupplevelsen. Microsoft Edge Enterprise-funktioner som aktiveras av Intune-principer inbegriper dubbel identitet, integrering med appskyddsprincip, integrering av Azure-programproxy samt hanterade favoriter och genvägar för startsidan. Mer information finns i [Microsoft Edge-support](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices--3105122----"></a>Inaktuellt stöd för enheter med endast EAS för Exchange Online/Intune-anslutningsapp<!--3105122  -->
Intune-konsolen stöder inte längre visning och hantering av enheter med endast EAS som är anslutna till Exchange Online med Intune-anslutningsappen. I stället har du följande alternativ:
- Registrera enheter i hantering av mobilenheter (MDM)
- Använd Intunes appskyddsprinciper för att hantera dina enheter
- Använd Exchange-kontrollerna enligt beskrivningen i [Klienter och mobilt i Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

#### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name--4254930---"></a>Söka efter en exakt enhet med [namn] på sidan Alla enheter<!--4254930 -->
Du kan nu söka efter ett exakt enhetsnamn. Gå till **Intune** > **Enheter** > **Alla enheter** > i sökrutan omger du enhetsnamnet med {} för att söka efter en exakt matchning. Det kan till exempel vara **{Enhet12345}** .

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="support-for-additional-connectors-on-the-tenant-status-page---3617202----"></a>Stöd för ytterligare anslutningsappar på sidan Status för klientorganisation<!-- 3617202  -->
[Sidan Status för klientorganisation](../tenant-status.md) visar nu statusinformation för ytterligare anslutningsappar, däribland *Windows Defender Advanced Threat Protection* (ATP) och andra Mobile Threat Defense-anslutningsappar.

#### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune---4260871---"></a>Stöd för Power BI-efterlevnadsapp från Data Warehouse-bladet i Microsoft Intune<!-- 4260871 -->
Tidigare laddade länken **Ladda ned Power BI-fil** på bladet **Intune Data Warehouse** ned en Intune Data Warehouse-rapport (.pbix-fil). Den här rapporten har ersatts med Power BI-efterlevnadsappen. Power BI-efterlevnadsappen kräver inte någon särskild inläsning eller konfiguration. Den öppnas direkt i Power BI-onlineportalen och visar data specifikt för din Intune-klientorganisation baserat på dina autentiseringsuppgifter. I Intune väljer du länken **Konfigurera Intune Data Warehouse** på höger sida av Intune-bladet. Klicka sedan på **Hämta Power BI-appen**. Mer information finns i [Ansluta till Data Warehouse med Power BI](../developer/reports-proc-get-a-link-powerbi.md).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles---3637917----"></a>Bevilja Intune skrivskyddad åtkomst till vissa Azure Active Directory-roller<!-- 3637917  -->
Skrivskyddad åtkomst för Intune har givits till följande Azure AD-roller. Behörigheter som beviljas med Azure AD-roller ersätter behörigheter som beviljas med rollbaserad åtkomstkontroll (RBAC) för Intune.

Skrivskyddad åtkomst till Intune-granskningsdata:

- Efterlevnadsadministratör
- Efterlevnadsdataadministratör

Skrivskyddad åtkomst till alla Intune-data:

- Säkerhetsadministratör
- Säkerhetsoperatör
- Säkerhetsläsare

Mer information finns i [Rollbaserad åtkomstkontroll](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles--2934430-----"></a>Omfångstaggar för iOS-appetableringsprofiler<!--2934430   -->
Du kan lägga till en omfångstagg till en iOS-appetableringsprofil så att endast personer med roller som också tilldelats den omfångstaggen har åtkomst till iOS-appetableringsprofilen. Mer information finns i [Använda RBAC och omfångstaggar](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies--2371891-----"></a>Omfångstaggar för appkonfigurationsprinciper<!--2371891   -->
Du kan lägga till en omfångstagg till en appkonfigurationsprincip så att endast personer med roller som också tilldelats den omfångstaggen har åtkomst till appkonfigurationsprincipen. Appkonfigurationsprincipen kan endast riktas till eller associeras med appar som har tilldelats samma omfångstagg. Mer information finns i [Använda RBAC och omfångstaggar](scope-tags.md).

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>Microsoft Edge-stöd för Intune-scenarier i iOS-enheter och Android-enheter<!-- 3411007 -->
Microsoft Edge kommer att stödja samma hanteringsscenarier som Intune Managed Browser samt förbättringar av användarupplevelsen. Microsoft Edge Enterprise-funktioner som aktiveras av Intune-principer inbegriper dubbel identitet, integrering med appskyddsprincip, integrering av Azure-programproxy samt hanterade favoriter och genvägar för startsidan. Mer information finns i [Microsoft Edge-support](../apps/app-configuration-managed-browser.md#microsoft-edge-support).




<!-- ########################## -->
## <a name="february-2019"></a>Februari 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering
#### <a name="intune-macos-company-portal-dark-mode---3300524----"></a>Mörkt läge i Intune macOS-företagsportalen<!-- 3300524  -->
Nu stöder Intune macOS-företagsportalen mörkt läge för macOS. När du aktiverar mörkt läge på en macOS 10.14 +-enhet kommer företagsportalen att justera dess utseende till färger som speglar detta läge.

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices---2577355-----"></a>Intune använder Google Play Protect-API:er på Android-enheter<!-- 2577355   -->
Vissa IT-administratörer hanterar en BYOD-miljö där slutanvändare kan rota eller jailbreaka sin mobiltelefon. Även om beteendet inte är illa menat blir resultatet att det kringgår många Intune-principer som har angetts för att skydda organisationens data och slutanvändarenheter. Därför har Intune rot- och jailbreak-identifiering för både registrerade och oregistrerade enheter. Med den här versionen använder Intune nu Google Play Protect-API:er som tillägg till våra befintliga rotidentifieringskontroller för oregistrerade enheter. Google delar inte alla rotidentifieringskontroller som sker men vi förväntar oss att dessa API:er kan identifiera användare som har rotat sina enheter av någon anledning från enhetsanpassning för att kunna få nyare OS-uppdateringar på äldre enheter. Dessa användare kan sedan blockeras från åtkomst till företagsdata eller så kan deras företagskonton rensas bort från deras principaktiverade appar. Ett ytterligare mervärde är att IT-administratören nu har flera rapporteringsuppdateringar på bladet Intune-appskydd – rapporten ”Flaggade användare” visar vilka användare som identifieras via SafetyNet API-genomsökningen från Google Play Protect, rapporten ”Potentiellt skadliga appar” visar vilka appar som identifieras via Googles Verify Apps API-genomsökning. Den här funktionen är tillgänglig på Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade---2617342-----"></a>Win32-appinformation tillgänglig på bladet Felsökning<!-- 2617342   -->
Du kan nu samla in felloggfiler för en Win32-appinstallation från Intune-appens blad **Felsökning**. Mer information om felsökning av appinstallationer finns i [Felsöka appinstallationsproblem](./../apps/troubleshoot-app-install.md) och [Felsöka problem med Win32-appar](./../apps/troubleshoot-app-install.md#win32-app-installation-troubleshooting).

#### <a name="app-status-details-for-ios-apps---3761235-----"></a>Appstatusinformation för iOS-appar<!-- 3761235   -->
Det finns nya felmeddelanden för appinstallationer som rör följande:
- Fel för VPP-appar vid installation på delad iPad
- Fel när App Store är inaktiverad
- Fel vid sökning efter VPP-licensen för appen
- Fel vid installation av systemappar med MDM-provider
- Fel vid installation av appar när enheten är i borttappat läge eller helskärmsläge
- Fel vid installation av app när användaren inte är inloggad i App Store

I Intune väljer du **Klientappar** > **Appar** > ”appens namn” > **Installationsstatus för enhet**. Nya felmeddelanden kommer att finnas i kolumnen **Statusinformation**.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Nya ny skärm för appkategorier i företagsportalappen för Windows 10<!-- 3834780  -->
En ny skärm som heter **Appkategorier** har lagts till i syfte att förbättra upplevelsen för bläddring och val av appar i företagsportalen för Windows 10. Användarna ser nu sina appar sorterade i kategorier som **Aktuella**, **Utbildning** och **Produktivitet**. Den här ändringen finns i versioner 10.3.3451.0 och senare av företagsportalen. Om du vill se den nya skärmen går du till [Nyheter i användargränssnittet för appen](whats-new-app-ui.md). Mer information om appar i företagsportalen finns i [Installera och dela appar på din enhet](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app---1455231-doc-work-item---"></a>Power BI-efterlevnadsapp<!-- 1455231 doc-work-item -->
Få åtkomst till ditt Intune-informationslager i Power BI Online med hjälp av [Intune-efterlevnadsappen (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Med den här Power BI-appen kan du nu komma åt och dela i förväg skapade rapporter utan någon konfiguration och utan att lämna webbläsaren. Mer information finns i [Ändringslogg – Power BI-efterlevnadsapp](../developer/reports-changelog.md#power-bi-compliance-app).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices---1862675-----"></a>PowerShell-skript kan köras på en 64-bitarsvärd på 64-bitarsenheter<!-- 1862675   -->
När du lägger till ett PowerShell-skript i en enhetskonfigurationsprofil körs skriptet alltid i 32 bitar, även på 64-bitars operativsystem. Med den här uppdateringen kan en administratör köra skriptet på en 64-bitars PowerShell-värd på 64-bitarsenheter (**Enhetskonfiguration** > **PowerShell-skript** > **Lägg till** > **Konfigurera** > **Kör skript i 64-bitars PowerShell-värd**).

Mer information om användning av PowerShell finns i [PowerShell-skript i Intune](../apps/intune-management-extension.md).

Gäller för: Windows 10 och senare

#### <a name="macos-users-are-prompted-to-update-their-password---1873216---"></a>macOS-användare uppmanas att uppdatera sitt lösenord<!-- 1873216 -->
Intune framtvingar inställningen **ChangeAtNextAuth** på macOS-enheter. Den här inställningen påverkar slutanvändare och enheter som har efterlevnadsprinciper för lösenord eller lösenordsprofiler för enhetsbegränsning. Slutanvändare uppmanas en gång att uppdatera sitt lösenord. Den här uppmaningen sker när en användare för första gången kör en uppgift som kräver autentisering, till exempel inloggning på enheten. Användare kan även uppmanas att uppdatera sitt lösenord när de gör något som kräver administratörsprivilegier, till exempel att begära nyckelringsåtkomst.

Eventuella nya eller befintliga ändringar av lösenordsprinciper av administratören gör att användarna återigen uppmanas att uppdatera lösenordet.

Gäller för:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device---2340521------"></a>Tilldela SCEP-certifikat till en användarlös macOS-enhet<!-- 2340521    -->
Du kan tilldela SCEP-certifikat (Simple Certificate Enrollment Protocol ) med hjälp av enhetsattribut till macOS-enheter, inklusive enheter utan användartillhörighet, och koppla certifikatprofilen till Wi-Fi- eller VPN-profiler. Detta utökar det stöd som vi redan har för att [tilldela SCEP-certifikat till enheter med och utan användartillhörighet](../protect/certificates-profile-scep.md) som kör Windows, iOS eller Android.  Den här uppdateringen lägger till alternativet att välja certifikattypen *Enhet* när du konfigurerar en SCEP-certifikatprofil för macOS.

Gäller för:
- macOS

#### <a name="intune-conditional-access-ui-update---2432313-----"></a>Uppdatering av användargränssnittet i Intune för villkorlig åtkomst<!-- 2432313   -->
Vi har gjort förbättringar av användargränssnittet för villkorlig åtkomst i Intune-konsolen. Dessa omfattar:
- Intune-bladet *Villkorlig åtkomst* har ersatts med bladet från Azure Active Directory. På så sätt har du åtkomst till alla inställningar och konfigurationer för [villkorlig åtkomst](../protect/conditional-access.md) (som fortfarande är en Microsoft Azure AD-teknik) från Intune-konsolen. 
- Vi har bytt namn bladet *Lokal åtkomst* till *Exchange-åtkomst* och flyttat konfigurationen av *Exchange-tjänstens anslutningsapp* till det här bladet med nytt namn.  Ändringen konsoliderar det ställe där du [konfigurerar och övervakar information relaterad till onlinebaserad och lokal Exchange](../protect/exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode---2935135-----"></a>Apparna Kiosk Browser och Microsoft Edge-webbläsaren kan köras på Windows 10-enheter i helskärmsläge<!-- 2935135   -->
Du kan använda Windows 10-enheter i helskärmsläge för att köra en app eller många appar. Den här uppdateringen omfattar flera ändringar av att använda webbläsare i helskärmsläge, inklusive:

- Lägg till webbläsaren Microsoft Edge eller Kiosk Browser att köras som appar på en helskärmsenhet (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **Windows 10 och senare** som plattform > **Helskärm** som profiltyp).
- Nya funktioner och inställningar är tillgängliga för att tillåta eller begränsa (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp), däribland:

- Microsoft Edge-webbläsare:
  - Använda helskärmsläget i Microsoft Edge
  - Uppdatera webbläsaren efter inaktivitetstid

- Favoriter och sökning:
  - Tillåta ändringar av sökmotorn

Se följande för en lista över dessa inställningar:

- [Inställningar för enheter med Windows 10 (och senare) som ska köras med helskärmsläge](../configuration/kiosk-settings-windows.md)
- [Enhetsbegränsningar för Microsoft Edge-webbläsaren](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)
- [Enhetsbegränsningar för favoriter och sökning](../configuration/device-restrictions-windows-10.md#favorites-and-search)

Gäller för: Windows 10 och senare

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices---3448774-----"></a>Nya inställningar för enhetsbegränsning för iOS-enheter och macOS-enheter<!-- 3448774   -->
Du kan begränsa vissa inställningar och funktioner på enheter som kör iOS och macOS (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** eller **macOS** som plattform > **Enhetsbegränsningar** som profiltyp). Den här uppdateringen lägger till fler funktioner och inställningar som du kan kontrollera, till exempel ange skärmtid, ändra eSIM-inställningar och mobilabonnemang och mer på iOS-enheter. Det går även att fördröja programuppdateringars synlighet för användaren och blockera innehållscachelagring på macOS-enheter.

Funktioner och inställningar som du kan begränsa finns här:

- [Inställningar för iOS-enhetsbegränsning](../configuration/device-restrictions-ios.md)
- [Inställningar för macOS-enhetsbegränsning](../configuration/device-restrictions-macos.md)

Gäller för:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices---3598402-----"></a>”Kioskenheter” kallas nu ”dedikerade enheter” på Android Enterprise-enheter<!-- 3598402   -->
För att stämma överens med Android-terminologi ändras **kioskenheter** till **dedikerade enheter** för Android Enterprise-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > ** Android Enterprise för plattform > **Endast enhetens ägare** > **Enhetsbegränsningar** > **Dedikerade enheter**).

Om du vill se de tillgängliga inställningarna går du till [Enhetsinställningar för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Gäller för:  
Android enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui---3640850-3803313-----"></a>Safari och iOS-inställningarna för att fördröja visning av programuppdateringar för användaren flyttas i Intune-användargränssnittet<!-- 3640850, 3803313   -->
För iOS-enheter kan du ange Safari-inställningar och konfigurera programuppdateringar. I den här uppdateringen flyttas dessa till olika delar av Intune-användargränssnittet:

- Safari-inställningarna flyttades från **Safari** (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** som plattform > **Enhetsbegränsningar** som profiltyp) till **[Inbyggda appar](../configuration/device-restrictions-ios.md#built-in-apps)** .
- Inställningen för att **fördröja visning av programuppdateringar för användaren för övervakade iOS-enheter** (**Programuppdateringar** > **Uppdateringsprinciper för iOS**) flyttas till **Enhetsbegränsningar** >  **[Allmänt](../configuration/device-restrictions-ios.md#general)** .  Information om påverkan på befintliga principer finns i [iOS-programuppdateringar](../protect/software-updates-ios.md#configure-the-policy).

Se följande för en lista över inställningarna:

- [iOS-enhetsbegränsningar](../configuration/device-restrictions-ios.md) 
- [iOS-programuppdateringar](../protect/software-updates-ios.md)

Den här funktionen gäller för:

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices---3699164-----"></a>Aktivering av begränsningar i enhetsinställningarna byter namn till Skärmtid på iOS-enheter<!-- 3699164   -->
Du kan konfigurera **Aktivera begränsningar i enhetsinställningarna** på övervakade iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** som plattform > **Enhetsbegränsningar** som profiltyp > **Allmänt**). I den här uppdateringen har den här inställningen bytt namn till **Skärmtid (endast övervakat)** .

Beteendet är samma. Specifikt:

- iOS 11.4.1 och tidigare: **Blockera** förhindrar slutanvändare att ange egna begränsningar i enhetsinställningarna. 
- iOS 12.0 och senare: **Blockera** förhindrar slutanvändare att ange en egen **skärmtid** i enhetsinställningarna, som innehålls- och sekretessbegränsningar. Fliken för begränsningar visas inte längre på enheter uppgraderade till iOS 12.0. Dessa inställningar finns i **Skärmtid**. 

En lista över inställningarna finns i [iOS-enhetsbegränsningar](../configuration/device-restrictions-ios.md#general).

Gäller för:
- iOS


#### <a name="intune-powershell-module---951068----"></a>Intune PowerShell-modul<!-- 951068  -->
Intune PowerShell-modulen, som ger stöd för Intune-API:et via Microsoft Graph, är nu tillgänglig i [Microsoft PowerShell-galleriet](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Information om hur du använder den här modulen](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Scenarioexempel där den här modulen används](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization--3183757----"></a>Förbättrat stöd för leveransoptimering<!--3183757  -->
Vi har utökat stödet i Intune för konfiguration av leveransoptimering. Du kan nu konfigurera en utökad lista över [inställningar för leveransoptimering](../configuration/delivery-optimization-settings.md) och rikta den till dina enheter direkt från Intune-konsolen.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="rename-an-enrolled-windows-device---1911112----"></a>Byta namn på en registrerad Windows-enhet<!-- 1911112  -->
Du kan nu byta namn på en registrerad Windows 10-enhet (RS4 eller senare). Det kan göra så här: välj **Intune** > **Enheter** > **Alla enheter** > välj en enhet > **Byt namn på enhet**. Den här funktionen stöder för närvarande inte namnbyte för Windows-hybridenheter för Azure AD.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope---3173823----"></a>Tilldela automatiskt omfångstaggar till resurser som skapats av en administratör med det omfånget<!-- 3173823  -->
När en administratör skapar en resurs tilldelas alla omfångstaggar som tilldelats till administratören automatiskt till dessa nya funktioner.

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade---3560202----"></a>Rapport över misslyckad registrering flyttas till bladet Enhetsregistrering<!-- 3560202  -->
Rapporten **Misslyckade registreringar** har flyttats till avsnittet **Övervaka** på bladet **Enhetsregistrering**. Två nya kolumner (Registreringsmetod och Operativsystemversion) har också lagts till.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments--3815076-eemiss---"></a>Rapport över avbrutna i företagsportalen har bytt namn till Ofullständiga användarregistreringar<!--3815076 eemiss -->
Rapporten över **avbrutna i företagsportalen** har bytt namn till **Ofullständiga användarregistreringar**.






<!-- ########################## -->
## <a name="january-2019"></a>Januari 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="intune-app-pin---2298397---"></a>Intune-appens PIN-kod<!-- 2298397 -->
Som IT-administratör kan du nu konfigurera hur många dagar en användare kan vänta tills Intune-appens PIN-kod måste ändras. Den nya inställningen är *Återställ PIN-kod efter antal dagar* och är tillgänglig i Azure-portalen genom att välja **Intune** > **Klientappar** > **Appskyddsprinciper** > **Skapa princip** > **Inställningar** > **Åtkomstbehörigheter**. Den här funktionen, som är tillgänglig för [iOS](../apps/app-protection-policy-settings-ios.md)- och [Android](../apps/app-protection-policy-settings-android.md)-enheter, stöder ett positivt heltalsvärde.

#### <a name="intune-device-reporting-fields---2748738---"></a>Intune-enhetens rapportfält<!-- 2748738 -->
Intune ger ytterligare fält för enhetsrapportering inklusive appregistrerings-ID, Android-tillverkare, modell och version av säkerhetsuppdatering samt iOS-modell. I Intune är dessa fält tillgängliga genom att välja **Klientappar** > **Appskyddsstatus** och sedan välja **Appskyddsrapport: iOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodell (Android och iOS) och lägsta inställning för version av Android-säkerhetsuppdatering.

#### <a name="toast-notifications-for-win32-apps---3136566-----"></a>Popup-meddelanden för Win32-appar<!-- 3136566   -->
Du kan förhindra att popup-meddelanden per apptilldelning visas för slutanvändarna. Från Intune, väljer du **Klientappar** > **Appar** > välj appen > **Tilldelningar** > **Inkludera grupper**.

#### <a name="intune-app-protection-policies-ui-update---3251427----"></a>Uppdatering av användargränssnitt för Intune-appskyddsprinciper<!-- 3251427  -->
Vi har ändrat etiketterna för inställningar och knappar i Intunes appskydd för att de ska bli lättare att förstå. Några av ändringarna omfattar:  
- Kontroller ändras från **ja** / **nej** till primärt **blockera** / **tillåt** och **inaktivera** / **aktivera** kontroller. Även etiketterna har uppdaterats.  
- Inställningarna formateras om så att inställningen och dess etikett är sida vid sida i kontrollen, vilket ger bättre navigering.

Standardinställningar och antal inställningar förblir detsamma, men den här ändringen gör att användarna kan förstå, navigera och använda inställningar enklare för att tillämpa valda appskyddsprinciper. Mer information finns i [iOS-inställningar](../apps/app-protection-policy-settings-ios.md) och [Android-inställningar](../apps/app-protection-policy-settings-android.md).

#### <a name="additional-settings-for-outlook---3301182----"></a>Ytterligare inställningar för Outlook<!-- 3301182  -->
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
> Om du använder principer för Intune-appskydd till att hantera åtkomsten för företagsidentiteter bör du inte aktivera att **kräva biometri**. Mer information finns i **Kräva företagsautentiseringsuppgifter för åtkomst** för [iOS-åtkomstinställningar](../apps/app-protection-policy-settings-ios.md#access-requirements) och [Android-åtkomstinställningar](../apps/app-protection-policy-settings-android.md#access-requirements).

Mer information finns i [Konfigurationsinställningar för Microsoft Outlook](../apps/app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps---1352553---"></a>Ta bort Android Enterprise-appar<!-- 1352553 -->
Du kan ta bort hanterade Google Play-appar från Microsoft Intune. Om du vill ta bort en hanterad Google Play-app öppnar du Microsoft Intune i Azure-portalen och väljer **Klientappar** > **Appar**. Från listan över appar väljer du ellipserna (...) till höger om den hanterade Google Play-appen och väljer sedan **Ta bort** från den visade listan. När du tar bort en hanterad Google Play-app från applistan blir den hanterade Google Play-appen automatiskt ej godkänd.

#### <a name="managed-google-play-app-type---1352580---"></a>Hanterade Google Play-apptyper<!-- 1352580 -->
Den **hanterade Google Play**-apptypen gör att du kan lägga till mer specifikt [hanterade Google Play-appar](https://play.google.com/work/search?q=microsoft&c=apps) till Intune. Som Intune-administratör kan du bläddra, söka, godkänna, synkronisera och tilldela godkända hanterad Google Play-appar i Intune.  Du behöver inte längre bläddra till den hantera Google Play-konsolen separat och du behöver inte längre autentisera dig på nytt.  I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** väljer du **Hanterat Google Play-konto** som apptyp.

#### <a name="default-android-pin-keyboard---3802457---"></a>Standardtangentbord för PIN-kod i Android<!-- 3802457 -->
För slutanvändare som har angett en PIN-kod för Intune-appskydd (APP) på sina Android-enheter med PIN-kodtypen ”Numerisk” visas nu standardtangentbordet för Android istället för det fasta Android-tangentbordsgränssnittet som utformats tidigare. Den här ändringen har gjorts för att vara konsekvent när standardtangentbord används på både Android och iOS, för båda PIN-typerna ”Numerisk” och/eller ”Lösenord”. Mer information om inställningar för slutanvändaråtkomst på Android, till exempel PIN-kod för APP finns i [Åtkomstkrav för Android](../apps/app-protection-policy-settings-android.md#access-requirements).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrativa mallar finns i offentlig förhandsversion och flyttas till sin egen konfigurationsprofil <!-- 3322847 -->

Administrativa mallar i Intune (**Enhetskonfiguration** > **Administrationsmallar**) är för tillfället i allmänt tillgänglig förhandsvisning. I denna uppdatering:

- De administrativa mallarna innehåller ungefär 300 inställningar som kan hanteras i Intune. De här inställningarna fanns tidigare endast i redigeraren.
- Administrativa mallar finns i offentlig förhandsversion.
- Administrativa mallar flyttar från **Enhetskonfiguration** > **Administrativa mallar** till **Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Windows 10 och senare** > i **Profiltyp**, välj **Administrativa mallar**.
- Rapportering är aktiverad

Mer information om den här funktionen finns i [Windows 10-mallar för att konfigurera grupprincipinställningar](../configuration/administrative-templates-windows.md).

Gäller för: Windows 10 och senare

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user---1333642---"></a>Använda S/MIME för att kryptera och signera flera enheter för en användare<!-- 1333642 -->
Den här uppdateringen innehåller S/MIME-e-postkryptering som använder en ny importerad certifikatprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj plattformen > profiltypen **PKCS-importerat certifikat**). Du kan importera certifikat i PFX-format i Intune. Intune kan sedan leverera samma certifikat till flera enheter som registrerats av en enda användare. Detta omfattar även följande:
- Den interna e-postprofilen för iOS har stöd för att aktivera S/MIME-kryptering med importerade certifikat i PFX-format.
- Den interna e-postappen på Windows Phone 10-enheter använder S/MIME-certifikatet automatiskt.
- Det privata certifikatet kan levereras över flera plattformar. Men alla e-postappar har inte stöd för S/MIME.
- På andra plattformar kan du behöva konfigurera e-postappen manuellt för att aktivera S/MIME.  
- E-postappar som har stöd för S/MIME-kryptering kan hantera hämtning av certifikat för S/MIME-kryptering av e-post på ett sätt som MDM inte stöder, till exempel genom att läsa från utgivarens certifikatarkiv.
Mer information om den här funktionen finns i [S/MIME-översikt för att signera och kryptera e-post](../protect/certificates-s-mime-encryption-sign.md).
Stöds på: Windows, Windows Phone 10, macOS, iOS och Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices---1333665-2999078---"></a>Nya alternativ för att automatiskt ansluta och bevara regler vid användning av DNS-inställningarna på enheter med Windows 10 och senare<!-- 1333665, 2999078 -->
I Windows 10 och senare enheter kan du skapa en VPN-profil som innehåller en lista över DNS-servrar för att lösa domäner, som till exempel contoso.com. Den här uppdateringen omfattar nya inställningar för namnmatchning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **Windows 10 och senare** för plattform > välj **VPN** för Profiltyp > **DNS-inställningarna** >**Lägg till**): 
- **Anslut automatiskt**: När den är **Aktiverad**, ansluter enheten automatiskt till VPN-anslutningen när en enhet kontaktar en domän som du anger, t.ex contoso.com.
- **Beständig**: Som standard är alla NRPT-regler (principtabell för namnmatchning) aktiva så länge enheten är ansluten med hjälp av den här VPN-profilen. När inställningen är **Aktiverad** för en NRPT-regel förblir regeln aktiv på enheten, även om VPN-anslutningen kopplas bort. Regeln gäller tills VPN-profilen tas bort eller tills regeln tas bort manuellt, vilket kan göras med hjälp av PowerShell.
[Windows 10 VPN-inställningar](../configuration/vpn-settings-windows-10.md) beskriver inställningarna.

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices---1500165---"></a>Använda identifiering av betrott nätverk för VPN-profiler på Windows 10-enheter<!-- 1500165 -->
När du använder identifiering av betrott nätverk kan du förhindra VPN-profiler från att automatiskt skapa en VPN-anslutning när användaren redan är i ett betrott nätverk. Med den här uppdateringen kan du lägga till DNS-suffix om du vill aktivera identifiering av betrott nätverk på enheter som kör Windows 10 och senare (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **VPN** för profiltyp).
[Windows 10-VPN-inställningar](../configuration/vpn-settings-windows-10.md) visar en lista över aktuella VPN-inställningar.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users---1907917-1063203---"></a>Hantera Windows Holographic for Business-enheter som används av flera användare<!-- 1907917, 1063203 -->
För närvarande kan du konfigurera delade datorinställningar på Windows 10- och Windows Holographic for Business-enheter med en anpassad OMA-URI-inställning. Med den här uppdateringen läggs en ny profil till för att konfigurera delade enhetsinställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** > **Delad enhet för flera användare**).
Mer information om den här funktionen finns i [Intune-inställningar för att hantera delade enheter](../configuration/shared-user-device-settings.md).
Gäller för: Windows 10 och senare, Windows 10 Holographic for Business

#### <a name="new-windows-10-update-settings--2626030--2512994----"></a>Nya Windows 10 Update-inställningar<!--2626030  2512994  -->
För dina [Windows 10-uppdateringsringar](../protect/windows-update-for-business-configure.md) kan du konfigurera:
- **Funktionssätt för automatisk uppdatering** – Använd ett nytt alternativ, *Återställ till standard*, för att återställa de ursprungliga inställningarna för automatisk uppdatering på Windows 10-datorer som kör *uppdateringen från oktober 2018*
- **Blockera användaren från att pausa Windows-uppdateringar** – Konfigurera en ny programuppdateringsinställning som gör att du kan blockera eller tillåta användarna att pausa uppdateringsinstallationen från *Inställningar* på deras datorer.

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption---2662949---"></a>E-postprofiler för iOS kan använda S/MIME-signering och kryptering<!-- 2662949 -->
Du kan skapa en e-postprofil som innehåller olika inställningar. Den här uppdateringen inkluderar S/MIME-inställningar som kan användas för signering och kryptering av e-postmeddelanden på iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > **E-post** för profiltyp).
[iOS e-postkonfigurationsinställningar](../configuration/email-settings-ios.md) visar en lista över inställningarna.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Vissa BitLocker-inställningar har stöd för Windows 10 Pro-versionen<!-- 2727036 -->
Du kan skapa en konfigurationsprofil som anger inställningar för slutpunktsskydd för Windows 10-enheter, inklusive BitLocker. Den här uppdateringen lägger till stöd för Windows 10 Professional-versionen för vissa BitLocker-inställningar.
De här skyddsinställningarna finns i [Inställningar för slutpunktsskydd för Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Konfiguration av delad enhet har bytt namn till Meddelande på låsskärm för iOS-enheter i Azure-portalen<!-- 2809362 -->
När du skapar en profil för iOS-enheter kan du lägga till inställningar för **Konfiguration för delad enhet** för att visa specifik text på låsskärmen. Den här uppdateringen innehåller följande ändringar: 
- Inställningarna **Konfiguration för delad enhet** i Azure-portalen har bytt namn till ”Meddelande på låsskärmen (endast övervakat)” (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > välj **Enhetsfunktioner** för Profiltyp > **Meddelande på låsskärmen**).
- När du lägger till meddelanden på låsskärmen kan du infoga ett serienummer, ett enhetsnamn eller ett annat enhetsspecifikt värde som en variabel i **Resurstagginformation** och **Fotnot på låsskärmen**. Du kan till exempel ange `Device name: {{devicename}}` eller `Serial number is {{serialnumber}}` med hjälp av klammerparenteser. [iOS-token](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) visar en lista över de tillgängliga token som kan användas.
[Inställningar för att visa meddelanden på låsskärmen](../configuration/ios-device-features-settings.md#lock-screen-message) visar en lista över inställningarna.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices---2827760--"></a>Nya inställningar för enhetsbegränsning av App Store, dokumentvisning och spel har lagts till i iOS-enheter<!-- 2827760-->
I **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel** läggs följande inställningar till: Tillåt hanterade appar att skriva kontakter till ohanterade kontaktkonton Tillåt ohanterade appar att läsa från hanterade kontaktkonton Om du vill se de här inställningarna går du till [iOS-enhetsbegränsningar](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices---3201839-3201843---"></a>Inställningar för nytt meddelande, tips och keyguard för Android Enterprise-enhetsägarenheter<!-- 3201839 3201843 -->
Den här uppdateringen innehåller flera nya funktioner på Android Enterprise-enheter vid körning som enhetsägare. Om du vill använda dessa funktioner, gå till **Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Android Enterprise** > i **Profiltyp**, välj **Endast enhetens ägare** > **Enhetsbegränsningar**.

Nya funktioner som ingår:

- Inaktivera systemmeddelanden till att inte visas, inklusive inkommande anrop, systemaviseringar, systemfel med mera.
- Föreslår hoppa över start av självstudier och tips för appar som öppnas för första gången.
- Inaktivera avancerade keyguard-inställningar, till exempel kamera, meddelanden, upplåsning med fingeravtryck med mera.

Om du vill visa inställningarna går du till avsnittet om [begränsningsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections---3202194---"></a>Android Enterprise-enhetsägarenheter kan använda VPN-anslutningar med Always On<!-- 3202194 -->
I den här uppdateringen kan du använda VPN-anslutningar som alltid är aktiva på Android Enterprise-enheter. Ständiga VPN-anslutningar förblir anslutna eller återansluter omedelbart när användaren låser upp sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. Du kan också placera anslutningen i ”låst” läge, vilket blockerar all nätverkstrafik tills VPN-anslutningen aktiveras.
Du kan aktivera VPN-anslutningar som alltid är aktiva i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar** för enhetsägare endast > **Anslutningar**. Om du vill visa inställningarna går du till avsnittet om [begränsningsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices---3285177---"></a>Ny inställning för att avsluta processer i Aktivitetshanteraren på Windows 10-enheter<!-- 3285177 --> 
Den här uppdateringen innehåller en ny inställning för att avsluta processer med hjälp av Aktivitetshanteraren på Windows 10-enheter. Med hjälp av en profil för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Windows 10** > i **Profiltyp**, välj **Enhetsbegränsningar** > **Allmänna** inställningar), väljer du att tillåta eller förhindra den här inställningen.
Om du vill visa de här inställningarna går du till [Inställningar av begränsningar för Windows 10-enheter](../configuration/device-restrictions-windows-10.md).
Gäller för: Windows 10 och senare

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview---2055484-----"></a>Använda Microsofts rekommenderade inställningar med säkerhetsbaslinjer (allmänt tillgänglig förhandsversion)<!-- 2055484   -->

Intune integrerar med andra tjänster som fokuserar på säkerhet, inklusive Windows Defender ATP och Office 365 ATP. Kunder efterfrågar en gemensam strategi och en sammanhängande uppsättning säkerhetsarbetsflöden från slutpunkt till slutpunkt för alla Microsoft 365-tjänster. Vårt mål är att optimera strategier och skapa lösningar som kan hantera säkerhetsåtgärder och vanliga administratörsuppgifter. I Intune vill vi uppnå det här målet genom att publicera en uppsättning Microsoft-rekommenderade ”säkerhetsbaslinjer” (**Intune** > **Security baselines** ((Säkerhetsbaslinjer)).  En administratör kan skapa säkerhetsprinciper direkt från dessa baslinjer, och sedan distribuera dem till sina användare. Du kan också anpassa rekommendationerna om bästa praxis för att uppfylla behoven i organisationen. Intune kontrollerar att enheterna uppfyller baslinjerna och meddelar administratören om användare eller enheter inte uppfyller efterlevnadskraven.

Den här funktionen är en offentlig förhandsversion, så profiler som skapas nu flyttas inte över till säkerhetsbaslinjemallar som är allmänt tillgängliga. Du bör inte planera att använda dessa förhandsmallar i produktionsmiljö.

Läs mer om säkerhetsbaslinjer i [Skapa en säkerhetsbaslinje för Windows 10 i Intune](../protect/security-baselines-monitor.md).

Den här funktionen gäller för: Windows 10 och senare

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Icke-administratörer kan aktivera BitLocker på Windows 10-enheter som är anslutna till Azure AD<!-- 2147379   -->
När du aktiverar BitLocker-inställningar på Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Endpoint protection** för Profiltyp > **Windows-kryptering**), lägger du till BitLocker-inställningar.

Den här uppdateringen innehåller en ny inställning för BitLocker för att låta standardanvändare (icke-administratörer) aktivera kryptering.

De här inställningarna finns i [Inställningar för slutpunktsskydd för Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance---2192052--eepublished----"></a>Kontrollera Configuration Manager-kompatibilitet<!-- 2192052  eepublished  -->
Den här uppdateringen innehåller en ny kompatibilitetsinställning för Configuration Manager (**Enhetskompabilitet** > **Principer** > **Skapa princip** > **Windows 10 och senare** > **Configuration Manager-kompabilitet**). Configuration Manager skickar signaler till Intune-kompatibilitet. Med hjälp av inställningen kan du kräva att alla Configuration Manager-signaler returnerar ”kompatibel”.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd är enheten inte kompatibel i Intune.

[Configuration Manager-kompatibilitet](../protect/compliance-policy-create-windows.md#configuration-manager-compliance) beskriver den här inställningen.

Gäller för: Windows 10 och senare

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile---2809324-----"></a>Anpassa bakgrund på övervakade iOS-enheter med hjälp av en profil för enhetskonfiguration<!-- 2809324   -->
När du skapar en profil för enhetskonfiguration för iOS-enheter kan du anpassa vissa inställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsfunktioner** för profiltypen). Den här uppdateringen innehåller nya inställningar för **Bakgrund** som gör att administratörer kan använda en .png-, .jpg- eller .jpeg-bild på startsidan eller låsskärmen. Inställningar för bakgrund gäller endast för övervakade enheter. 

En lista över de här inställningarna finns i [Funktionsinställningar för iOS-enheter](../configuration/ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available---3594661----"></a>Helskärmsläge för Windows 10 är allmänt tillgängligt<!-- 3594661  -->
I den här uppdateringen är funktionen helskärmsläge på Windows 10 och senare enheter allmänt tillgängligt (GA). Alla inställningar som du kan lägga till och konfigurera finns i [Inställningar för helskärmsläge för Windows 10 (och senare)](../configuration/kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise---3598396-----"></a>Kontaktdelning via Bluetooth har tagits bort i Enhetsbegränsningar > Enhetens ägare för Android Enterprise<!-- 3598396   -->
När du skapar en profil för enhetsbegränsningar för Android Enterprise-enheter finns inställningen **Dela kontakter via Bluetooth**. I den här uppdateringen tas inställningen **Dela kontakter via Bluetooth** bort (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar > Enhetens ägare** för profiltyp > **Allmän**).

Inställningen **Dela kontakter via Bluetooth** har inte stöd för hantering av Android Enterprise-enhetens ägare. Så när den här inställningen tas bort, påverkar det inga enheter eller klienter, även om den här inställningen är aktiverad och konfigurerad i din miljö.

Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md).

Gäller för: Ägare av Android Enterprise-enhet


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="more-detailed-enrollment-restriction-failure-messaging---3111564---"></a>Mer detaljerade felmeddelanden för registreringsbegränsning<!-- 3111564 -->
Mer detaljerade felmeddelanden är tillgängliga när registreringsbegränsningar inte har uppfyllts. Om du vill se dessa meddelanden går du till **Intune** > **Felsök** > och markerar tabellen Registreringsfel. Mer information finns i [listan över registreringsfel](help-desk-operators.md#enrollment-failure-reference).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering
#### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices---1574342----"></a>Förhandsgranskning av stöd för företagsägda, fullständigt hanterade Android-enheter<!-- 1574342  -->
Nu har Intune fullt stöd för hanterade Android-enheter, ett företagsägt scenario av ”enhetsägare” där enheter hanteras noggrant av IT och är kopplade till enskilda användare. Detta gör att administratörer kan hantera hela enheten, tillämpa en utökad uppsättning principkontroller som inte är tillgängliga för arbetsprofiler och begränsa användare från att installera appar från hanterad Google Play endast. Mer information finns i artiklarna om att [konfigurera Intune-registrering av fullständigt hanterade Android-enheter](../enrollment/android-fully-managed-enroll.md) och att [registrera dedikerade enheter eller fullständigt hanterade enheter](../enrollment/android-dedicated-devices-fully-managed-enroll.md).  Observera att den här funktionen är en förhandsversion. Vissa Intune-funktioner, till exempel certifikat, efterlevnad och villkorlig åtkomst, är inte tillgängliga med fullständigt hanterade Android-användarenheter.

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices---1434452---"></a>Stöd för selektiv rensning för WIP-WE-enheter<!-- 1434452 -->
Med WIP-WE (Windows Information Protection Without Enrollment) kan kunder skydda sina företagsdata på Windows 10-enheter utan att fullständig MDM-registrering krävs. När dokument skyddas med en WIP-WE-princip kan skyddade data rensas selektivt av en Intune-administratör. Genom att välja användaren och enheten, och skicka en rensningsbegäran, blir alla data som skyddades via WIP-WE-principen oanvändbara. Från Intune på Azure-portalen väljer du **Mobilapp** > **Selektiv radering av app**.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="tenant-status-dashboard---1124854---"></a>Instrumentpanel för klientorganisationsstatus<!-- 1124854 -->
Den nya [sidan Klientorganisationsstatus](tenant-status.md) utgör en enskild plats där du kan visa status och relaterad information för din klient.  Instrumentpanelen är uppdelad i fyra områden:
- **Information om klientorganisation** – Visar information som innefattar klientens namn och plats, MDM-utfärdare, totalt antal registrerade enheter i klientorganisationen och antal licenser. I det här avsnittet visas även den aktuella versionen av tjänsten för din klientorganisation.
- **Status för anslutningsprogrammet** – Visar information om tillgängliga anslutningsprogram du har konfigurerat och kan även visa dem som du inte har aktiverat ännu.  
   Baserat på det aktuella tillståndet för varje anslutningsprogram är de flaggade med Felfri, Varning eller Ej felfri. Välj ett anslutningsprogram för att visa detaljer och visa information eller konfigurera ytterligare information för det.
- **Hälsotillstånd för Intune-tjänsten** – Visar information om aktiva incidenter eller avbrott i klientorganisationen. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office.
- **Nytt i Intune** – Visar aktiva meddelanden för klientorganisationen. Meddelanden omfattar till exempel aviseringar när klientorganisationen får de senaste funktionerna för Intune.  Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10---1488939--"></a>Ny hjälp- och supportupplevelse i företagsportalen för Windows 10<!-- 1488939-->
Den nya sidan Hjälp och support i Företagsportal hjälper användare att felsöka och be om hjälp med problem med appen och åtkomst. Från den nya sidan kan de skicka fel- och diagnostiklogginformation via e-post och hitta information om organisationens supportavdelning. De hittar också avsnittet Vanliga frågor och svar med länkar till relevant Intune-dokumentation.

#### <a name="new-help-and-support-experience-for-intune---3307080---"></a>Ny hjälp- och supportupplevelse för Intune<!-- #3307080 -->
Vi lanserar den nya hjälp- och supportupplevelsen för alla klientorganisationer under de närmaste dagarna. Den här nya upplevelsen är tillgänglig för Intune och kan nås när du använder Intune-bladen på [Azure-portalen](https://portal.azure.com/).
Med den nya upplevelsen kan du beskriva problemet med egna ord och ta emot felsökningsinsikter och webbaserat åtgärdsinnehåll. De här lösningarna är tillgängliga via en regelbaserad maskininlärningsalgoritm som drivs av användarfrågor. Utöver problemspecifika rekommendationer använder du det nya arbetsflödet för att öppna ett supportärende via e-post eller telefon. Den här nya upplevelsen ersätter den tidigare hjälp- och supportupplevelsen av en statisk uppsättning förvalda alternativ som är baserade på området i konsolen du befinner dig i när du öppnar Hjälp och support.
Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services---3762211----"></a>Ny arbetsloggar och möjligheten att skicka loggar till Azure Monitor-tjänster<!-- 3762211  -->
Intune har inbyggd granskningsloggning som spårar händelser när de ändras. Den här uppdateringen innehåller nya loggningsfunktioner, inklusive: 
- Arbetsloggar (förhandsversion) som visar information om användare och enheter som registrerats, inklusive lyckade och misslyckade försök.
- Granskningsloggarna och arbetsloggarna kan skickas till Azure Monitor, inklusive lagringskonton, händelsehubbar och logganalyser. De här tjänsterna gör att du kan lagra och använda analyser som Splunk och QRadar samt få visualiseringar av dina loggningsdata.

[Skicka data till lagring, händelsehubbar eller logganalyser i Intune](../review-logs-using-azure-monitor.md) har mer information om den här funktionen.

#### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device---2687509----"></a>Hoppa över flera skärmar för installationsassistenten på en iOS DEP-enhet<!-- 2687509  -->
Förutom de skärmar som du kan hoppa över just nu kan du ange att iOS DEP-enheter hoppar över följande skärmar i installationsassistenten när en användare registrerar enheten: Skärmton, Sekretess, Android-migrering, Start-knapp, iMessage och FaceTime, Registrering, Bevaka migrering, Utseende, Skärmtid, Programuppdatering, SIM-installation.
Om du vill välja vilka skärmar som ska hoppas över, går du till **Enhetsregistrering** > **Apple-registrering** > **Tokens för registreringsprogram** > välj en token > **Profiler** > välj en profil > **Egenskaper** > **Anpassning av installationsassistenten** > välj **Dölj** för alla skärmar som du vill hoppa över > **OK**.
Om du skapar en ny profil eller redigerar en profil måste den valda överhoppningsskärmen synkroniseras med Apple MDM-servern. Användare kan utfärda en manuell synkronisering av enheterna så att det inte sker någon fördröjning i att plocka upp profiländringarna.

#### <a name="android-enterprise-app-we-app-deployment---1171203---"></a>Appdistribution för Android Enterprise APP-WE<!-- 1171203 -->
För Android-enheter i ett distributionsscenario med en appskyddsprincip utan registrering (APP-WE) kan du nu använda hanterad Google Play för att distribuera store-appar och LOB-appar till användare. Mer specifikt kan du ge slutanvändarna en appkatalog och installationsfunktioner som inte längre kräver att slutanvändare lättar på säkerhetshållningen för sina enheter genom att tillåta installationer från okända källor. Dessutom kan det här distributionsscenariot ge en förbättrad slutanvändarupplevelse.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-apps---1081941---"></a>Omfattningstaggar för appar<!-- 1081941 -->
Du kan skapa omfångstaggar som begränsar åtkomsten för roller och appar. Du kan lägga till en omfångstagg för en app så att endast personer med roller som också tilldelats den omfångstaggen har åtkomst till appen. För närvarande kan appar som har lagts till i Intune från hanterad Google Play eller appar som har köpts med hjälp av Apples volymköpsprogram (VPP) inte tilldelas omfångstaggar (men framtida stöd för detta planeras). Mer information finns i [Använda omfångstaggar för att filtrera principer](scope-tags.md).




<!-- ########################## -->
## <a name="december-2018"></a>December 2018

### <a name="app-management"></a>Apphantering

#### <a name="updates-for-application-transport-security---748318---"></a>Uppdateringar för Application Transport Security<!-- 748318 -->

Microsoft Intune har stöd för TLS 1.2+ (Transport Layer Security) i syfte att tillhandahålla förstklassig kryptering, göra Intune säkrare som standard och anpassa programmet till andra Microsoft-tjänster som t.ex. Microsoft Office 365. För att uppfylla detta krav framtvingar iOS- och macOS-företagsportalerna Apples uppdaterade ATS-krav (Application Transport Security), som även kräver TLS 1.2 +. ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS- och macOS-appar i företagsportalen. Mer information finns i [Intunes supportblogg](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys---1832174---"></a>Intune App SDK kommer att stödja 256-bitars krypteringsnycklar<!-- 1832174 -->
Intune App SDK för Android använder nu 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciperna. SDK fortsätter att stödja 128-bitars nycklar för kompatibilitet med innehåll och appar som använder äldre versioner av SDK.

#### <a name="microsoft-auto-update-version-450-required-for-macos-devices---3503442---"></a>Microsofts version 4.5.0 för automatisk uppdatering krävs för macOS-enheter<!-- 3503442 -->
Om du vill fortsätta att få uppdateringar av företagsportalen och andra Office-program, måste de macOS-enheter som hanteras av Intune uppgraderas till Microsofts version 4.5.0 för automatisk uppdatering. Användarna kanske redan har den här versionen för sina Office-appar.

### <a name="device-management"></a>Enhetshantering

#### <a name="intune-requires-macos-1012-or-later---2827778---"></a>Intune kräver macOS 10.12 eller senare<!-- 2827778 -->
Intune kräver nu macOS version 10.12 eller senare. Enheter med tidigare macOS-versioner kan inte använda företagsportalen när de registrerar sig i Intune. För att fortsätta att få support och nya funktioner måste användarna uppgradera sina enheter till macOS 10.12 eller senare, samt uppgradera företagsportalen till den senaste versionen.

<!-- ########################## -->
## <a name="november-2018"></a>November 2018

### <a name="app-management"></a>Apphantering

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices---1281677---"></a>Avinstallera appar på företagsägda övervakade iOS-enheter<!-- 1281677 -->
Du kan ta bort alla appar på företagsägda övervakade iOS-enheter. Du kan ta bort en app genom att rikta antingen användar- eller enhetsgrupper med tilldelningstypen **avinstallera**. För personliga eller ej kontrollerade iOS-enheter kommer du fortsätta kunna ta bort appar som har installerats med hjälp av Intune.

#### <a name="downloading-intune-win32-app-content---2617320---"></a>Ladda ned innehåll för Intune Win32-app<!-- 2617320 -->
Windows 10 RS3-klienter och högre hämtar Intune Win32-appinnehåll med en komponent för leveransoptimering på Windows 10-klienten. Leveransoptimering ger Peer-to-Peer-funktioner som är aktiverat som standard. För närvarande kan leveransoptimering konfigureras med en grupprincip. Mer information finns i [Leveransoptimering för Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization).

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>Slutanvändarenhet och appinnehållsmenyn<!-- 2771453 -->
Slutanvändare kan nu använda snabbmenyn på enheter och appar för att utlösa vanliga åtgärder som att byta namn på en enhet eller kontrollera efterlevnad.

#### <a name="set-custom-background-in-managed-home-screen-app----3041945---"></a>Ange en anpassad bakgrund den hanterade hemskärmsappen <!-- 3041945 -->
Vi ska lägga till en inställning som låter dig anpassa bakgrundsutseendet på den hanterade hemskärmsappen på Android Enterprise, flera appar, enheter i helskärmsläge.  För att konfigurera **Anpassad URL-bakgrund** går du till Intune i Azure portal > Enhetskonfiguration. Välj en aktuell enhetskonfigurationsprofil eller skapa en ny om du vill redigera dess inställningar för helskärmsläge.
Mer information om inställningar för helskärmsläge finns i avsnittet om [Begränsningsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply---3104570---"></a>Spara och tillämpa tilldelning av appskyddsprincip<!-- 3104570 -->
Du har nu bättre kontroll över dina [Tilldelningar av appskyddsprinciper](../apps/app-protection-policies.md). När du väljer *Tilldelningar* för att ange eller redigera en princips tilldelningar måste du **Spara** konfigurationen för att ändringen ska tillämpas. Använd **Ignorera** för att rensa alla ändringar du gör utan att spara dessa till listorna inkludera eller exkludera.  Genom att kräva Spara eller Ignorera tilldelas endast de användare som du avser en appskyddsprincip.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later---3174639---"></a>Nya Microsoft Edge-webbläsarinställningar för Windows 10 och senare<!-- 3174639 -->
Den här uppdateringen innefattar en ny inställning för att styra och hantera Microsoft Edge-webbläsaren på dina enheter. En lista över dessa inställningar finns i [Enhetsbegränsning för Windows 10 (och senare)](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies---3330037---"></a>Stöd för nya appar med appskyddsprinciper<!-- 3330037 -->
Du kan nu hantera följande appar med [Intune principer för appskydd](../apps/app-protection-policies.md):
- Stream (iOS)
- Att göra (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Använd appskyddsprinciper för att skydda företagsdata och kontrollera dataöverföring för dessa appar, så som andra principhanterade Intune-appar. Obs! Om Flow ännu inte syns i konsolen kan du lägga till det när du skapar eller redigerar principerna för appskydd. Du gör detta genom att använda alternativet **+ fler appar** och sedan ange *app-ID* för Flow i indatafältet. Använd *com.microsoft.flow* för Android och *com.microsoft.procsimo* för iOS.


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="support-for-ios-12-oauth-in-ios-email-profiles--2155106---"></a>Stöd för iOS 12 OAuth i iOS-e-postprofiler<!--2155106 -->
Intunes iOS-e-postprofiler stöder iOS 12 Open Authorization (OAuth). Om du vill se den här funktionen skapar du en ny profil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **E-post** för profiltyp) eller uppdaterar en befintlig iOS-e-postprofil. Om du aktiverar OAuth i en profil som redan har distribuerats till användare uppmanas användarna att autentisera på nytt och ladda ned sin e-post igen.

[iOS-e-postprofiler](../configuration/email-settings-ios.md) innehåller mer information om hur du använder OAuth i en e-postprofil.

#### <a name="network-access-control-nac-support-for-citrix-sso-for-ios---3259404---"></a>Stöd för Network Access Control (NAC) för Citrix SSO för iOS<!-- 3259404 -->
Citrix släppte en uppdatering av Citrix Gateway som tillåter Network Access Control (NAC) för Citrix SSO för iOS i Intune. Du kan välja att inkludera ett enhets-ID i en VPN-profil i Intune och sedan skicka den här profilen till dina iOS-enheter. Du måste installera den senaste uppdateringen av Citrix Gateway för att kunna använda den här funktionen.

[Konfigurera VPN-inställningar på iOS-enheter](../configuration/vpn-settings-ios.md#base-vpn-settings) innehåller mer information om hur du använder NAC, samt information om vissa ytterligare krav. 

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown---1892471---"></a>Versionsnummer och build-nummer för iOS och macOS visas<!-- 1892471 -->
I **Enhetsefterlevnad** > **Enhetsefterlevnad** visas operativsystemsversionerna iOS och macOS. De är tillgängliga för användning i efterlevnadsprinciper. Uppdateringen innefattar versionsnumret vilket kan konfigureras för båda plattformarna.
När säkerhetsuppdateringar lanseras låter Apple vanligtvis versionsnumret vara som det är men uppdaterar byggenumret. Genom att använda byggenumret i en efterlevnadsprincip kan du enkelt kontrollera om en säkerhetsriskuppdatering har installerats.
Se efterlevnadsprinciper för [iOS](../protect/compliance-policy-create-ios.md#device-health) och [macOS](../protect/compliance-policy-create-mac-os.md#device-properties) om du vill använda funktionen.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later---2753807---"></a>Uppdateringsringar ersätts med leveransoptimeringsinställningar för Windows 10 och senare<!-- 2753807 -->
Leveransoptimering är en ny konfigurationsprofil för Windows 10 och senare. Funktionen ger en smidigare upplevelse för att leverera programuppdateringar till enheter i din organisation. Uppdateringen hjälper dig även att leverera inställningarna till nya och befintliga uppdateringsringar med en konfigurationsprofil.
Se [leveransoptimeringsinställningar för Windows 10 (och senare)](../configuration/delivery-optimization-windows.md) för att konfigurera en konfigurationsprofil för leveransoptimering.

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices---2827760---"></a>Nya inställningar för enhetsbegränsning har lagts till i iOS-enheter och macOS-enheter<!-- 2827760 -->
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

Mer information om dessa inställningar finns i inställningarna för enhetsbegränsning i [iOS](../configuration/device-restrictions-ios.md) och [macOS](../configuration/device-restrictions-macos.md).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview---1048100--"></a>Autopilot-stöd för Azure Active Directory-anslutna hybridenheter (förhandsgranskning)<!-- 1048100-->
Du kan nu konfigurera Azure Active Directory-anslutna hybridenheter med hjälp av Autopilot. Enheterna måste vara anslutna till organisationens nätverk för att du ska kunna använda Autopilot-hybridfunktionen. Du hittar mer information under [Distribuera Hybrid Azure Active Directory-anslutna enheter med Intune och Autopilot för Windows](../enrollment/windows-autopilot-hybrid.md).
Den här funktionen kommer att lanseras till hela användarbasen under de närmaste dagarna. Därför kanske du inte kan följa stegen förrän funktionen har distribuerats till ditt konto.

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Välj appar som spåras på sidan för registreringsstatus<!-- 2531007 -->
Du kan välja vilka appar som spåras på sidan för registreringsstatus. Användaren kan inte använda enheten förrän dessa appar har installerats. Mer information finns i [Konfigurera en sida för registreringsstatus](../enrollment/windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number--2595788---"></a>Sök efter Autopilot-enheter med serienummer<!--2595788 -->
Du kan nu söka efter Autopilot-enheter med serienummer. Om du vill göra det väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter** > ange ett serienummer i rutan **Sök efter serienummer** > tryck på Retur.

#### <a name="track-installation-of-office-proplus--2620217---"></a>Spåra installation av Office ProPlus<!--2620217 -->
Användare kan följa installationsförloppet för [Office ProPlus](../apps/apps-add-office365.md) med hjälp av sidan [Registreringsstatus](../enrollment/windows-enrollment-status.md). Mer information finns i [Konfigurera en sida för registreringsstatus](../enrollment/windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low---2237572---"></a>Aviseringar om utgående VPP-token eller om att kvarvarande licenser för företagsportalen håller på att ta slut<!-- 2237572 -->
Om du använder Volume Purchase Program (VPP) för att företablera företagsportalen vid DEP-registrering visas en varning i Intune när en VPP-token håller på att upphöra och när licenserna för företagsportalen nästan är slut.

#### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts--3006133---"></a>macOS DEP-stöd för Apple School Manager-konton<!--3006133 -->
Intune stöder nu användning av programmet för enhetsregistrering (DEP) på macOS-enheter för Apple School Manager-konton.  Mer information finns i [Registrera macOS-enheter automatiskt med Apple School Manager eller programmet för enhetsregistrering](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="new-intune-device-subscription-sku--3312071--"></a>Ny SKU för Intune-enhetsprenumeration<!--3312071-->
För att sänka kostnaderna för hantering av enheter i företag finns det nu en ny enhetsbaserad prenumerations-SKU. Den här SKU:n för Intune-enheter licensieras per enhet och månad. Priset varierar beroende på licensprogrammet. Den är tillgänglig direkt via Microsoft 365-administrationscentret och via [Enterprise-avtal](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), [Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA) [Microsofts öppna avtal ](https://partner.microsoft.com/licensing/licensing-agreements) och [Molnlösningsleverantör](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Enhetshantering

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes---3041935---"></a>Pausa tillfälligt helskärmsläge på Android-enheter för att göra ändringar<!-- 3041935 -->
När du använder Android-enheter i helskärmsläge för flera appar, kan en IT-administratör behöva göra ändringar i enheten. Den här uppdateringen innefattar nya inställningar för helskärmsläge för flera appar så att IT-administratörer tillfälligt kan pausa helskärmsläget med hjälp av en PIN-kod och få åtkomst till hela enheten.
Mer information om inställningar för helskärmsläge finns i avsnittet om [Begränsningsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices----3042021---"></a>Aktivera den virtuella hemknappen på Android Enterprise-enheter i helskärmsläge <!-- 3042021 -->
En ny inställning låter användare trycka på en programstyrd knapp på sin enhet för att växla mellan den hanterade hemskärmsappen och andra tilldelade appar på sin enhet för helskärmsläget för flera appar. Den här inställningen är särskilt användbart i scenarier där en användares app för helskärmsläge inte svarar på rätt sätt på knappen ”Bakåt”. Du kommer att kunna konfigurera den här inställningen för företagsägda Android-enheter för enskild användning. För att aktivera eller inaktivera den **virtuella hemknappen**, går du till Intune i Azure Portal > enhetskonfiguration. Välj en aktuell enhetskonfigurationsprofil eller skapa en ny om du vill redigera dess inställningar för helskärmsläge.
Mer information om inställningar för helskärmsläge finns i avsnittet om [Begränsningsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).




<!-- ########################## -->
## <a name="october-2018"></a>Oktober 2018

### <a name="app-management"></a>Apphantering

#### <a name="access-to-key-profile-properties-using-the-company-portal-app---772203---"></a>Åtkomst till viktiga profilegenskaper med hjälp av företagsportalappen<!-- 772203 -->
Slutanvändare kan nu komma åt viktiga egenskaper och åtgärder, till exempel lösenordsåterställning, från företagsportalappen. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios---1248481---"></a>Tangentbord från tredje part kan blockeras via APP-inställningarna i iOS<!-- 1248481 -->
Intune-administratörer kan blockera användningen av tredjepartstangentbord på iOS-enheter vid åtkomst till organisationens data i skyddade appar. När APP (Application Protection Policy) är inställt på att blockera tredjepartstangentbord visas ett meddelande första gången användaren interagerar med företagsdata och använder ett tredjepartstangentbord. Alla alternativ förutom det interna tangentbordet är blockerade och visas inte för användaren. Enhetsanvändarna ser bara det här meddelandet en gång. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices---1248496---"></a>Åtkomst till användarkonto för Intune-appar på hanterade Android- och iOS-enheter<!-- 1248496 -->
Som Microsoft Intune-administratör kan du styra vilka användarkonton som läggs till i Microsoft Office-program på hanterade enheter. Du kan begränsa åtkomsten till endast tillåtna användarkonton i organisationen och blockera personliga konton på registrerade enheter. 

#### <a name="outlook-ios-and-android-app-configuration-policy--1828527---"></a>Appkonfigurationsprincip för Outlook iOS och Android<!--1828527 -->
Du kan nu skapa en Outlook-iOS och Android-appkonfigurationsprincip för iOS och Android för lokala användare som använder grundläggande autentisering med ActiveSync-protokollet. Ytterligare konfigurationsinställningar läggs till vartefter de aktiveras för Outlook för iOS och Android.

#### <a name="office-365-pro-plus-language-packs---1833450---"></a>Språkpaket för Office 365 Pro Plus<!-- 1833450 -->
Som Intune-administratör kan du distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Gå till Azure Portal och välj **Microsoft Intune** > **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** på bladet **Lägg till app** väljer du **Windows 10** under **Office 365 Suite**. Välj **Språk** på bladet **Inställningar för appsviten**.

#### <a name="windows-line-of-business-lob-apps-file-extensions---1884873---"></a>Filnamnstillägg för verksamhetsspecifika Windows-appar (LOB)<!-- 1884873 -->
Filnamnstillägg för verksamhetsspecifika Windows-appar omfattar nu *.msi*, *.appx*, *.appxbundle*, *.msix* och *.msixbundle*. Du kan lägga till en app i Microsoft Intune genom att välja **Klientappar** > **Appar** > **Lägg till**. Fönstret **Lägg till app** visas och där du kan välja **Apptyp**. För LOB-appar på Windows väljer du **Verksamhetsspecifik app** som apptyp, väljer **Appaketfil** och anger sedan en installationsfil med rätt filnamnstillägg.

#### <a name="windows-10-app-deployment-using-intune---2309001---"></a>Distribution av Windows 10-appar med hjälp av Intune<!-- 2309001 -->
Genom att bygga vidare på det befintliga stödet för verksamhetsspecifika appar och appar för Microsoft Store för företag kan administratörer använda Intune för att distribuera de flesta av organisationens befintliga program till slutanvändare på Windows 10-enheter. Administratörer kan lägga till, installera och avinstallera program för Windows 10-användare i flera olika format, till exempel MSI, Setup.exe eller MSP. Intune utvärderar regler för krav innan nedladdningen och installationen, och meddelar slutanvändarna om statusen eller krav på omstart via Åtgärdscenter för Windows 10. Den här funktionen hjälper organisationer som vill flytta den här arbetsbelastningen till Intune och molnet. Den här funktionen är för närvarande tillgänglig som en offentlig förhandsversion. Vi planerar att introducera många nyheter i funktionen under de kommande månaderna. 

#### <a name="app-protection-policy-app-settings-for-web-data---2662995---"></a>APP-inställningar (App Protection Policy) för webbdata<!-- 2662995 -->
Principinställningarna för webbinnehåll på både Android och iOS-enheter kommer att uppdateras så att de blir bättre på att hantera både http- och https-länkar liksom dataöverföring via universella iOS-länkar och Android App-länkar. 

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>Slutanvändarenhet och appinnehållsmenyn<!-- 2771453 -->
Slutanvändare kan nu använda snabbmenyn på enheter och appar för att utlösa vanliga åtgärder som att byta namn på en enhet eller kontrollera efterlevnad. 

#### <a name="windows-company-portal-keyboard-shortcuts---2771518---"></a>Kortkommandon för Windows-företagsportalen<!-- 2771518 -->
Slutanvändare kan nu utlösa app- och enhetsåtgärder i Windows-företagsportalen med hjälp av kortkommandon (acceleratorer).

#### <a name="require-non-biometric-pin-after-a-specified-timeout---1506985---"></a>Kräv icke-biometrisk PIN-kod efter en angiven tidsgräns<!-- 1506985 -->
Genom att kräva en icke-biometrisk PIN-kod efter en tidsgräns angiven av en administratör förbättras säkerheten för appar som har aktiverats för hantering av mobilprogram (MAM) genom att användningen av biometrisk identifiering för åtkomst till företagets data begränsas av Intune. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Klientappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar. Läs om åtkomstinställningar i [Inställningar för iOS](../apps/app-protection-policy-settings-ios.md#access-requirements) och [Inställningar för Android](../apps/app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices---2244713---"></a>Inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter<!-- 2244713 -->
Du kan skilja kontroll över inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter från att ange identiteten för den registrerade användaren, även kända som UPN (User Principal Name). Administratörer som inte använder IntuneMAMUPN kommer inte att se någon funktionalitetsförändring. När den här funktionen är tillgänglig, bör administratörer som använder IntuneMAMUPN för att styra beteende för dataöverföring på registrerade enheter granska de nya inställningarna och uppdatera sina APP-inställningar efter behov.

#### <a name="windows-10-win32-apps---2617325---"></a>Win32-appar för Windows 10<!-- 2617325 -->
Du kan konfigurera Win32-appar som ska installeras i användarkontext för enskilda användare och installera appen för alla användare på enheten.

#### <a name="windows-win32-apps-and-powershell-scripts---2617330---"></a>Win32-appar för Windows och PowerShell-skript<!-- 2617330 -->
Slutanvändare behöver inte längre vara inloggade på enheten för att installera Win32-appar eller köra PowerShell-skript. 

#### <a name="troubleshooting-client-app-installation---1363711---"></a>Felsöka klientappinstallationen<!-- 1363711 -->
Du kan felsöka installationen av klientappar genom att granska kolumnen **Appinstallation** i fönstret **Felsök**. För att visa fönstret **Felsök** i Intune-portalen väljer du **Felsök** under **Hjälp och support**.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Skapa DNS-suffix i VPN-konfigurationsprofiler på enheter som kör Windows 10<!-- 1333668 -->
När du skapar en profil för VPN-enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** >  plattform: **Windows 10 och senare** > profiltyp: **VPN**), anger du vissa DNS-inställningar. Med den här uppdateringen kan du även ange flera **DNS-suffix** i Intune. När du använder DNS-suffix, kan du söka efter en nätverksresurs med dess korta namn i stället för det fullständiga domännamnet (FQDN). I och med den här uppdateringen kan du ändra ordningen på DNS-suffix i Intune.
[Windows 10-VPN-inställningar](../configuration/vpn-settings-windows-10.md#dns-settings) visar en lista över aktuella DNS-inställningar.
Gäller för: Windows 10-enheter

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles---1333705---"></a>Stöd för AlwaysOn-VPN för Android Enterprise-arbetsprofiler<!-- 1333705 -->
I den här uppdateringen kan du använda VPN-anslutningar som alltid är aktiva på Android-företagsenheter med hanterade arbetsprofiler. Ständiga VPN-anslutningar förblir anslutna eller återansluter omedelbart när användaren låser upp sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. Du kan också placera anslutningen i ”låst” läge, vilket blockerar all nätverkstrafik tills VPN-anslutningen aktiveras.
Du kan aktivera VPN-anslutningar som alltid är aktiva i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android-företag** för plattform > **Enhetsbegränsningar** > **Anslutningar**.

#### <a name="issue-scep-certificates-to-user-less-devices---1744554---"></a>Utfärda SCEP-certifikat till användarlösa enheter<!-- 1744554 -->
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
> - `{{FullyQualifiedDomainName}}` fungerar endast för Windows-enheter och domänanslutna enheter. 
> - När du anger enhetsegenskaper som IMEI, serienummer och fullständigt domännamn i ämnet eller SAN för ett certifikat, tänk på att de här egenskaperna kan förfalskas av en person med åtkomst till enheten. 

[Skapa en SCEP-certifikatprofil](../protect/certificates-profile-scep.md#create-a-scep-certificate-profile) visar en lista över aktuella variabler när du skapar en konfigurationsprofil för SCEP. 

Gäller för: Windows 10 och senare samt iOS, stöds för Wi-Fi

#### <a name="remotely-lock-uncompliant-devices---2064495---"></a>Fjärrlåsa enheter som inte är kompatibla<!-- 2064495 -->
När en enhet inte är kompatibel kan du skapa en åtgärd i efterlevnadsprincipen som fjärrlåser enheten. I Intune > **Enhetskompatibilitet** skapar du en ny princip eller väljer en befintlig princip > **Egenskaper**. Välj **Åtgärder vid inkompatibilitet** > **Lägg till** och välj att fjärrlåsa enheten.
Stöds på: 
- Android
- iOS
- macOS
- Windows 10 Mobil 
- Windows Phone 8.1 och senare 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal---2748224---"></a>Profilförbättringar för informationsdatorer med Windows 10 och senare i Azure-portalen<!-- 2748224 -->
Den här uppdateringen innehåller följande förbättringar i konfigurationsprofilen för Windows 10-informationsenheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Helskärm (förhandsgranskning)** för profiltyp): 
- För närvarande kan du skapa flera informationsdatorprofiler på samma enhet. I och med den här uppdateringen stöder Intune endast en informationsdatorprofil per enhet. Om du fortfarande behöver flera informationsdatorprofiler på en enskild enhet kan du använda en anpassad URI.
- I en profil för **informationsdator med flera appar** kan du välja programikonernas storlek och ordning i **Startmenylayout** i programrutnätet. Om du vill anpassa mera, kan du ladda upp en XML-fil.
- Inställningarna för webbläsare för informationsdator flyttas till inställningarna för **Informationsdator**. För närvarande har inställningarna för **Webbläsare för informationsdator** sin egen kategori i Azure Portal.
Gäller för: Windows 10 och senare

#### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device----2637704----"></a>Ange PIN-kod när du ändrar fingeravtryck eller ansikts-ID på en iOS-enhet <!-- 2637704  -->
Nu uppmanas användarna att ange en PIN-kod när de gör biometriska ändringar på sin iOS-enhet. Detta omfattar ändringar i registrerade fingeravtryck eller ansikts-ID. Tidsinställningen för uppmaningen beror på hur konfigurationen av *Kontrollera åtkomstkraven efter (minuter)* löper ut.  När ingen PIN-kod har angetts, uppmanas användaren att skapa en. 
 
Den här funktionen är endast tillgänglig för iOS och kräver medverkan av program som integrerar Intune APP SDK för iOS, version 9.0.1 eller senare. Integrering av SDK krävs så att beteendet kan tillämpas på de berörda programmen. Den här integreringen händer på löpande bas, och är beroende av specifika programteam. Vissa appar som deltar omfattar WXP, Outlook, Managed Browser och Yammer.

#### <a name="network-access-control-support-on-ios-vpn-clients---1333693---"></a>Stöd för åtkomstkontroll på nätverk på VPN-klienter för iOS<!-- 1333693 -->
Med den här uppdateringen finns en ny inställning för att aktivera åtkomstkontroll på nätverk (NAC) när du skapar en VPN-profil för Cisco AnyConnect, F5-åtkomst och Citrix SSO för iOS. Den här inställningen tillåter att NAC-ID för enheten inkluderas i VPN-profilen. För närvarande finns det inte några VPN-klienter eller NAC-partnerlösningar som har stöd för detta nya NAC-ID, men vi håller dig informerad via vårt [supportblogginlägg](ttps://aka.ms/iOS12_and_vpn) när det finns.

Om du vill använda NAC, måste du:
1. Välja att tillåta att Intune inkluderar enhets-ID i VPN-profiler
2. Uppdatera din NAC-providers programvara/inbyggda programvara, enligt anvisningarna direkt från din NAC-provider

Information om den här inställningen i en iOS VPN-profil finns i [Lägga till VPN-inställningar på iOS-enheter i Microsoft Intune](../configuration/vpn-settings-ios.md). Mer information om åtkomstkontrollen för nätverk finns i [Integrering av åtkomstkontroll för nätverk (NAC) med Intune](../protect/network-access-control-integrate.md). 

Gäller för: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile---1818139---"></a>Ta bort en e-postprofil från en enhet, även om det bara finns en e-postprofil<!-- 1818139 -->
Tidigare gick det inte att ta bort en e-postprofil från en enhet *om* det var den enda e-postprofilen. Detta beteende ändras i och med den här uppdateringen. Nu kan du ta bort en e-postprofil, även om det är den enda e-postprofilen på enheten. Läs mer i informationen om att [lägga till e-postinställningar för enheter med Intune](../configuration/email-settings-configure.md).

#### <a name="powershell-scripts-and-aad---2309469---"></a>PowerShell-skript och Azure Active Directory<!-- 2309469 -->
PowerShell-skript i Intune kan riktas till säkerhetsgrupper för AAD-enheter.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Ny standardinställning för ”Krav på lösenordstyp” för Android, Android Enterprise<!-- 2649963 -->
När du skapar en ny efterlevnadsprincip (**Intune** > **enhetsefterlevnad** > **principer** > **skapa princip** > **Android** eller **Android Enterprise** för Plattform > Systemsäkerhet), ändras standardvärdet för **krav på lösenordstyp**:

Från: Standard för enheten Till: Minst numeriskt

Gäller för: Android, Android Enterprise

Om du vill se de här inställningarna går du till [Android](../protect/compliance-policy-create-android.md) och [Android Enterprise](../protect/compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile---2662938---"></a>Använda en i förväg delad nyckel i en Wi-Fi-profil för Windows 10<!-- 2662938 -->
Med den här uppdateringen kan du använda en i förväg delad nyckel (PSK) med säkerhetsprotokollet WPA/WPA2-Personal för att autentisera en Wi-Fi-konfigurationsprofil för Windows 10. Du kan också ange kostnadskonfigurationen för ett avgiftsbelagt nätverk av enheter i Windows-10 oktober 2018-uppdateringen.

För närvarande måste du importera en Wi-Fi-profil eller skapa en anpassad profil för att använda en i förväg delad nyckel. [Wi-Fi-inställningar för Windows 10](../configuration/wi-fi-settings-windows.md) visar en lista över de aktuella inställningarna. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices---3218390---"></a>Ta bort PKCS- och SCEP-certifikat från dina enheter<!-- 3218390 -->
I vissa scenarier fanns PKCS- och SCEP-certifikaten kvar på enheterna, även om du tog bort en princip från en grupp, om du tog bort en konfiguration eller efterlevnadsdistribution eller om en administratör uppdaterade en befintlig SCEP- eller PKCS-profil. Detta beteende ändras i och med den här uppdateringen. Det finns vissa scenarier då PKCS- och SCEP-certifikat tas bort från enheter och vissa scenarier då certifikaten finns kvar på enheten. Mer information om dessa scenarier finns i [Ta bort SCEP- och PKCS-certifikat i Microsoft Intune](../protect/remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance---2504381---"></a>Använda Gatekeeper på macOS-enheter för efterlevnad<!-- 2504381 -->
Den här uppdateringen innehåller macOS Gatekeeper för att utvärdera enheter för kompatibilitet. För att ställa in Gatekeeper-egenskaper, [Lägg till en enhetsefterlevnadsprincip för macOS-enheter](../protect/compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot---1558983---"></a>Tillämpa Autopilot-profil på registrerade Windows 10-enheter som inte redan har registrerats för Autopilot<!-- 1558983 -->
Du kan använda Autopilot-profiler för registrerade Windows 10-enheter som inte redan har registrerats för Autopilot. I Autopilot-profilen väljer du alternativet **Omvandla alla målenheter till Autopilot** för att automatiskt registrera andra än Autopilot-enheter med Autopilot-distributionstjänsten. Det kan ta upp till 48 timmar för registreringen att bearbetas. Autopilot konfigurerar enheten efter att den har avregistrerats och återställts.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups---2526564---"></a>Skapa flera profiler för sidan för registreringsstatus och tilldela dem till Azure AD-grupper<!-- 2526564 -->
Nu kan du [skapa](../enrollment/windows-enrollment-status.md) flera profiler för sidan för registreringsstatus och tilldela dem till Azure AD-grupper.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune--2748613--"></a>Migrering från programmet för enhetsregistrering till Apple Business Manager i Intune<!--2748613-->
Apple Business Manager (ABM) fungerar i Intune och du kan uppgradera ditt konto från program för enhetsregistrering (DEP) till ABM. Processen i Intune är samma. Om du vill uppgradera ditt Apple-konto från DEP till ABM, gå till [https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

#### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page--2748656--"></a>Statusflikar för avisering och registrering på översiktssidan för enhetsregistrering<!--2748656-->
Aviseringar och registreringsfel visas nu på separata flikar på översiktssidan för enhetsregistrering.

#### <a name="enrollment-abandonment-report---1382924---"></a>Rapport över avbrutna registreringar<!-- 1382924 -->
En ny rapport som innehåller information om övergivna registreringar finns tillgänglig under **Enhetsregistrering** > **Övervaka**. Mer information finns i [Företagsportalens lämningsrapport](../enrollment/enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature---2870393---"></a>Ny funktion för Azure Active Directory-användningsvillkor<!-- 2870393 -->
Azure Active Directory har en funktion för användningsvillkor som du kan använda i stället för de befintliga Intune-villkoren. Funktionen för användningsvillkor i Azure AD ger större flexibilitet över vilka villkor som ska visas och när, bättre lokaliseringsstöd, bättre kontroll över hur villkoren återges och bättre rapportering. Funktionen för användningsvillkor i Azure AD kräver Azure Active Directory Premium P1 som också är en del av programsviten Enterprise Mobility + Security E3. Mer information finns i artikeln [Hantera företagets villkor för användaråtkomst](../enrollment/terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support--3188762--"></a>Stöd för läget för Android-enhetens ägare<!--3188762-->
För registrering av Samsung Knox-registrering, stöder nu Intune registrering av enheter till läget för hantering av Android-enhetens ägare. Användarna på Wi-Fi eller mobila nätverk kan registrera sig med bara några få tryck när de aktiverar på sina enheter för första gången. Mer information finns i [Registrera Android-enheter automatiskt med hjälp av från Samsung Knox Mobile-registrering](../enrollment/android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Enhetshantering
#### <a name="new-settings-for-software-updates-----1907869---"></a>Nya inställningar för programuppdateringar  <!-- 1907869 -->  
- Du kan nu konfigurera att vissa meddelanden aviserar slutanvändarna om de omstarter som krävs för att slutföra installationen av de senaste programuppdateringarna.   
- Du kan nu konfigurera en omstartsvarning vid omstarter som sker utanför arbetstid, vilket har stöd för BYOD-scenarier.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id---2075110---"></a>Gruppera Windows Autopilot-registrerade enheter efter korrelator-ID<!-- 2075110 -->
Intune stöder nu gruppering av Windows-enheter med ett korrelator-ID när de har registrerats med hjälp av [Autopilot för befintliga enheter](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) via Configuration Manager. Korrelator-ID:t är en parameter i Autopilot-konfigurationsfilen. Intune matchar automatiskt [Azure AD-enhetsattributet enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) med ”OfflineAutopilotprofile-<correlator ID>”. På så sätt kan godtyckligt dynamiska grupper i Azure AD skapas baserat på korrelator-ID via attributet enrollmentprofileName för Autopilot-offlineregistreringar. Mer information finns i [Windows Autopilot för befintliga enheter](../enrollment/enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies---2984657---"></a>Appskyddsprinciper i Intune<!-- 2984657 -->
Med Intune-appskyddsprinciper kan du konfigurera olika dataskyddsinställningar för Intune-skyddade appar, till exempel Microsoft Outlook och Microsoft Word. Vi har ändrat utseendet och känslan för de här inställningarna för både [iOS](../apps/app-protection-policy-settings-ios.md) och [Android](../apps/app-protection-policy-settings-android.md) för att göra det enklare att hitta individuella inställningar. Det finns tre typer av principinställningar:
- **Dataflytt** – Den här gruppen innehåller kontroller för dataförlustskydd (DLP), såsom begränsningar för klipp ut, kopiera och klistra in och spara som. De här inställningarna avgör hur användarna samverkar med data i apparna.
- **Åtkomstbehörigheter** – Den här gruppen innehåller alternativ för PIN-kod per app som avgör hur slutanvändare får åtkomst till apparna i en arbetskontext.  
- **Villkorlig start** – Den här gruppen innehåller inställningar som lägsta OS-inställningar, uppbrytning och identifiera rotade enheter och offlinerespittid.  
  
Funktionerna i inställningarna ändras inte, men det är lättare att hitta dem när du arbetar i principen för redigering av flödet.

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices---2451462----"></a>Begränsa appar och blockera åtkomsten till företagsresurser på Android-enheter<!-- 2451462  -->  
I **Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Android** > **Systemsäkerhet** finns det en ny inställning under avsnittet *Enhetssäkerhet* med namnet **Begränsade appar**. Inställningen **Begränsade appar** använder en efterlevnadsprincip för att blockera åtkomsten till företagsresurser om vissa appar installeras på enheten. Enheten betraktas som icke-kompatibel tills de begränsade apparna tas bort från enheten.
Gäller för: 
- Android

### <a name="intune-apps"></a>Intune-appar

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps---1727158---"></a>Intune kommer att stödja en maximal paketstorlek på 8 GB för verksamhetsspecifika appar<!-- 1727158 -->
Intune ökade den maximala paketstorleken till 8 GB för LOB-appar (Line-of-business). Du hittar mer information i [Lägg till appar i Microsoft Intune](../apps/apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app---1916266---"></a>Lägga till en anpassad varumärkesbild för företagsportalappen<!-- 1916266 -->
Som Microsoft Intune-administratör kan du ladda upp en anpassad varumärkesbild som visas som bakgrundsbild på användarens profilsida i iOS-företagsportalappen. Mer information om hur du konfigurerar företagsportalappen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](../apps/company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines---2971030---"></a>Intune bevarar det lokaliserade språket i Office när Office uppdateras på slutanvändarnas datorer<!-- 2971030 -->
När Intune installerar Office på slutanvändarnas datorer får användarna automatiskt samma språkpaket som de hade med tidigare .MSI Office-installationer. Du hittar mer information i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](../apps/apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal---3076965---"></a>Ny Intune Support-upplevelse i Microsoft 365-enhetshanteringsportalen<!-- 3076965 -->
Vi lanserar en ny upplevelse för hjälp och support för Intune i [Microsoft 365-enhetshanteringsportalen]( https://devicemanagement.microsoft.com). Med den nya upplevelsen kan du beskriva problemet med egna ord och ta emot felsökningsinsikter och webbaserat åtgärdsinnehåll. De här lösningarna är tillgängliga via en regelbaserad maskininlärningsalgoritm som drivs av användarfrågor.  

Utöver problemspecifika rekommendationer kan du också använda det nya arbetsflödet för att öppna ett supportärende via e-post eller telefon.  

För kunder som är en del av distributionen, ersätter den här nya upplevelsen den aktuella hjälp- och supportupplevelsen av en statisk uppsättning förvalda alternativ som är baserade på området i konsolen du befinner dig i när du öppnar Hjälp och support.  

*Denna nya hjälp- och supportupplevelse distribueras till vissa men inte alla klienter och är tillgänglig i enhetshanteringsportalen. Deltagare i den här nya upplevelsen väljs ut slumpmässigt bland de tillgängliga Intune-klientorganisationerna. Nya klienter läggs till då vi expanderar distributionen.*  

Mer information finns i [Hjälp- och supportupplevelse](get-support.md#help-and-support-experience) i Ta reda på hur du kan få support för Microsoft Intune.  

#### <a name="powershell-module-for-intune--preview-available---951068---"></a>PowerShell-modul för Intune – en förhandsversion är tillgänglig<!-- 951068 -->
Nu finns en ny PowerShell-modul, som har stöd för Intune-API:et via Microsoft Graph, tillgänglig som en förhandsversion på [GitHub](https://aka.ms/intunepowershell). Mer information om hur du använder den här modulen finns i Viktigt-filen på den platsen.

<!-- ########################## -->
## <a name="september-2018"></a>September 2018

### <a name="app-management"></a>Apphantering

#### <a name="remove-duplication-of-app-protection-status-tiles---3083391---"></a>Ta bort duplicering av statuspaneler för appskydd<!-- 3083391 -->
Panelerna **användarstatus för iOS** och **användarstatus för Android** fanns både på sidan **Klientappar – översikt** samt sidan **Klientappar – Appskyddsstatus**. Statuspanelerna har tagits bort från sidan **Klientappar – översikt** för att undvika duplicering. 

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="support-for-more-third-party-certification-authorities-ca---3093107---"></a>Stöd för fler tredjeparts certifikatutfärdare (CA)<!-- 3093107 -->
Genom att använda Simple Certificate Enrollment Protocol (SCEP) så kan du nu utfärda nya certifikat och förnya certifikat på mobila enheter med Windows, iOS, Android och macOS.

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="intune-moves-to-support-ios-10-and-later---2454656---"></a>Intune går över till stöd för iOS 10 och senare<!-- 2454656 -->  
Nu stöder Intune-registrering, företagsportalen och den hanterade webbläsaren endast iOS-enheter som kör iOS 10 och senare. Om du vill söka efter enheter eller användare som påverkas i din organisation går du till Intune på Azure-portalen > **Enheter** > **Alla enheter**. Filtrera efter operativsystem och klicka sedan på **Kolumner** för att visa information om operativsystemversionen. Be användarna att uppgradera sina enheter till en operativsystemversion som stöds.  

Om du har någon av enheterna som anges nedan, eller om du vill registrera någon av enheterna som anges nedan, bör du vara medveten om att de endast stöder iOS 9 och tidigare.  För att även fortsättningsvis ha åtkomst till Intune-företagsportalen måste du uppgradera dessa enheter till enheter som stöder iOS 10 eller senare:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (tredje generationen) 
* iPad Mini (första generationen)  

### <a name="device-management"></a>Enhetshantering

#### <a name="microsoft-365-device-management-administration-center---3078424---"></a>Administrationscenter för Microsoft 365-enhetshantering<!-- 3078424 -->
En av löftena för Microsoft 365 är förenklad administration och under åren har vi integrerat Microsoft 365-tjänsterna i serverdelen för att leverera scenarier från början till slut, till exempel Intune och Azure AD villkorsstyrd åtkomst. Den nya [Administrationscentret för Microsoft 365](https://devicemanagement.microsoft.com) låter dig konsolidera, förenkla och integrera administratörsupplevelsen. Specialist-arbetsytan för enhetshantering ger enkel åtkomst till all den enhets- och apphanteringsinformation och uppgifter som din organisation behöver. Vi förväntar oss att det här blir den primära molnarbetsytan för enterprise-slutanvändares databehandlingsteam.


<!-- ########################## -->
## <a name="august-2018"></a>Augusti 2018

### <a name="app-management"></a>Apphantering

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types---1520957---"></a>Stöd för pakettunnel för VPN-profiler per app i iOS för anpassade anslutningstyper och Pulse Secure-anslutningstyper<!-- 1520957 -->
När du använder per app-VPN-profiler i iOS kan du välja att använda händelsedirigering nedåt på appnivå (app-proxy) eller på paketnivå (paket-tunnel). Dessa alternativ är tillgängliga med följande anslutningstyper:
- Anpassat VPN
- Pulse Secure om du inte är säker på vilket värde du ska använda läser du VPN-leverantörens dokumentation.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device---1949583---"></a>Fördröjning när iOS-programuppdateringar visas på enheten<!-- 1949583 -->
I Intune > **Programuppdateringar** > **Uppdateringsprinciper för iOS** kan du konfigurera dagar och tider då du inte vill att enheter installerar uppdateringar. I en kommande uppdatering kommer du kunna fördröja tidpunkten då en programuppdatering visas på enheten från 1–90 dagar. 
[Konfigurera uppdateringsprinciper för iOS i Microsoft Intune](../protect/software-updates-ios.md) visar en lista över aktuella inställningar.

#### <a name="office-365-proplus-version---2213968---"></a>Office 365 ProPlus-version<!-- 2213968 -->
När du tilldelar Office 365 ProPlus-appar till Windows 10-enheter med Intune kommer du att kunna välja version av Office. I Azure-portalen väljer du **Microsoft Intune** > **Appar** > **Lägg till app**. Välj sedan **Office 365 ProPlus-paket (Windows 10)** från listrutan **Typ**. Välj **Inställningar för appsvit** för att visa det associerade bladet. Ange **Uppdateringskanalen** till ett värde såsom **Varje månad**. Du kan även ta bort andra versioner av Office (msi) från slutanvändarenheter genom att välja **Ja**. Välj **Specifik** för att installera en specifik version av Office för den valda kanalen på slutanvändarenheter. Nu kan du välja den **specifika version** av Office som ska användas. De versioner som är tillgängliga ändras över tid. När du skapar en ny distribution kan de versioner som är tillgängliga därför vara nyare och inte ha vissa äldre versioner tillgängliga. Befintliga distributioner fortsätter att distribuera den äldre versionen, men versionslistan uppdateras kontinuerligt per kanal. Mer information finns i [Översikt över uppdateringskanaler för Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn---2282852---"></a>Stöd för inställningen Registrera DNS för Windows 10-VPN<!-- 2282852 -->
Med den här uppdateringen kan du konfigurera Windows 10-VPN-profiler så att de dynamiskt registrerar de IP-adresser som tilldelas till VPN-gränssnittet med intern DNS, utan behov av anpassade profiler.
Information om de aktuella VPN-profilinställningar som är tillgängliga finns i [Windows 10-VPN-inställningar](../configuration/vpn-settings-windows-10.md).

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name--2652728--"></a>Installationsprogrammet för macOS-företagsportalen innehåller nu versionsnumret i filnamnet för installationsprogrammet<!--2652728-->

#### <a name="ios-automatic-app-updates---2729759---"></a>Automatiska appuppdateringar i iOS<!-- 2729759 -->
Automatiska appuppdateringar fungerar för både enhets- och användarlicensierade appar för iOS version 11.0 och senare.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="windows-hello-will-target-users-and-devices---1106609---"></a>Windows Hello riktar in sig på användare och enheter<!-- 1106609 -->
När du skapar en [Windows Hello för företag](../protect/windows-hello.md)-princip gäller den för alla användare i organisationen (i hela klientorganisationen). Med den här uppdateringen kan principen även tillämpas på specifika användare eller specifika enheter med hjälp av en princip för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Identity Protection (Identitetsskydd)**  > **Windows Hello för företag**).
I Intune i Azure-portalen finns konfiguration och inställningar för Windows Hello nu i både **Enhetsregistrering** och **Enhetskonfiguration**. **Enhetsregistrering** riktar sig till hela organisationen (i hela klientorganisationen) och har stöd för Windows AutoPilot (OOBE). **Enhetskonfiguration** riktar sig mot enheter och användare som använder en princip som tillämpas under incheckning.
Den här funktionen gäller för:  
- Windows 10 och senare
- Windows 10 Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios---1769858---"></a>Zscaler är en tillgänglig anslutning för VPN-profiler i iOS<!-- 1769858 -->
När du skapar en VPN-profil för enhetskonfiguration i iOS (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS**-plattform > **VPN**-profiltyp) finns det flera anslutningstyper, inklusive Cisco, Citrix och mer. Den här uppdateringen lägger till Zscaler som anslutningstyp. 
[VPN-inställningar för enheter som kör iOS](../configuration/vpn-settings-ios.md) visar en lista över tillgängliga anslutningstyper.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10---1879077---"></a>FIPS-läge för Wi-Fi-företagsprofiler för Windows 10<!-- 1879077 -->
Du kan nu aktivera FIPS-läge (Federal Information Processing Standards) för företagets Wi-Fi-profiler för Windows 10 i Intune Azure-portalen. Se till att FIPS-läge är aktiverat i Wi-Fi-infrastrukturen om du aktiverar det i Wi-Fi-profilerna.
[Wi-Fi-inställningar för Windows 10 och senare enheter i Intune](../configuration/wi-fi-settings-windows.md) visar hur du skapar en Wi-Fi-profil.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview---1958649---"></a>Kontrollera S-läge på Windows 10-enheter och senare enheter – förhandsversion<!-- 1958649 -->
Med den här funktionsuppdateringen kan du skapa en profil för enhetskonfiguration som växlar en Windows 10-enhet ut ur S-läge, eller förhindra att användare växlar enheten ut ur S-läge. Den här funktionen finns i Intune > **Enhetskonfiguration** > **Profiler** >  **Windows 10 och senare** > **Edition upgrade and mode switch** (Versionsuppgradering och lägesväxling).
[Introduktion till Windows 10 i S-läge](https://www.microsoft.com/windows/s-mode) innehåller mer information om S-läge.
Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile---2144658---"></a>ATP-konfigurationspaketet för Windows Defender läggs automatiskt till i konfigurationsprofilen<!-- 2144658 -->
När du använder enheter med [Advanced Threat Protection och registrering](../protect/advanced-threat-protection.md#onboard-devices-by-using-a-configuration-profile) i Intune behövde du tidigare ladda ned ett konfigurationspaket och lägga till det i din konfigurationsprofil. Med den här uppdateringen hämtar Intune paketet automatiskt från Windows Defender Säkerhetscenter och lägger till det i din profil.
Gäller för Windows 10 och senare.

#### <a name="require-users-to-connect-during-device-setup--2311457--"></a>Kräv att användare ansluter under enhetskonfiguration<!--2311457-->
Du kan nu ange enhetsprofiler som kräver att enheten ansluter till ett nätverk innan den går vidare förbi sidan Nätverk under Windows 10-installationen. När den här funktionen är i förhandsversion krävs Windows Insider-version 1809 eller senare för att använda den här inställningen.
Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices---2451462---"></a>Begränsa appar och blockera åtkomst till företagsresurser på iOS- och Android-företagsenheter<!-- 2451462 -->
I **Enhetsefterlevnad** > **Principer** > **Skapa princip** > **iOS** > **Systemsäkerhet** finns det en ny inställning för **Begränsade program**. Den här nya inställningen använder en policy för efterlevnad för att blockera åtkomst till företagsresurser om vissa appar är installerade på enheten. Enheten betraktas som icke-kompatibel tills de begränsade apparna tas bort från enheten.
Gäller för: iOS

#### <a name="modern-vpn-support-updates-for-ios---2459928-1819876-and-2650856---"></a>Uppdateringar med stöd för modernt VPN för iOS<!-- 2459928, 1819876, and 2650856 -->
Den här uppdateringen har stöd för följande VPN-klienter för iOS:
- F5 Access (version 3.0.1 och senare)
- Citrix SSO
- Palo Alto Networks GlobalProtect version 5.0 och senare även i den här uppdateringen:
- Den befintliga anslutningstypen **F5 Access** byter namn till **F5 Access Legacy** för iOS.
- Den befintliga anslutningstypen **Palo Alto Networks GlobalProtect** byter namn till **Legacy Palo Alto Networks GlobalProtect** för iOS.
Befintliga profiler med de här anslutningstyperna fortsätter att fungera med sina respektive äldre VPN-klienter. Om du använder Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN eller Palo Alto Networks GlobalProtect version 4.1 och tidigare med iOS bör du gå över till de nya apparna. Gör det så snart som möjligt för att säkerställa att VPN-åtkomst är tillgänglig för iOS-enheter när de uppdaterar till iOS 12.
Mer information om iOS 12 och VPN-profiler finns i [Microsoft Intune-supportteamets blogg](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal---2469637---"></a>Exportera efterlevnadsprinciper för den klassiska Azure-portalen för att återskapa dessa principer i Intune Azure-portalen<!-- 2469637 -->
Principer för enhetsefterlevnad som skapats i den klassiska Azure-portalen upphör att gälla. Du kan granska och ta bort alla befintliga principer, men du kan inte uppdatera dem. Om du behöver migrera några efterlevnadsprinciper till den befintliga Intune Azure-portalen kan du exportera principerna som en kommaavgränsad fil ( *.csv*-fil). Använd sedan informationen i filen för att återskapa dessa principer i Intune Azure-portalen.

> [!IMPORTANT]
> När den klassiska Azure-portalen upphör kommer du inte längre att kunna komma åt eller visa dina efterlevnadsprinciper. Tänk därför på att exportera dina principer och återskapa dem i Azure-portalen innan den klassiska Azure-portalen upphör.

#### <a name="better-mobile---new-mobile-threat-defense-partner---22662717---"></a>Better Mobile – ny partner för skydd mot mobilhot<!-- 22662717 -->
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Better Mobile, en lösning med skydd mot mobilhot som är integrerad i Microsoft Intune.

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in--1067692---"></a>Lås företagsportalen i enkelt appläge tills användaren loggar in<!--1067692 --> 
Du kan nu välja att köra företagsportalen i enkelt appläge om du autentiserar en användare via företagsportalen i stället för installationsassistenten vid DEP-registrering. Det här alternativet låser enheten omedelbart efter att installationsassistenten är klar så att en användare måste logga in för att komma åt enheten. Den här processen ser till att enheten slutför registrering inte frånkopplas i ett tillstånd utan någon kopplad användare.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device--1346521---"></a>Tilldela en användare och ett eget namn till en Autopilot-enhet<!--1346521 -->
Du kan nu [tilldela en användare till en specifik Autopilot-enhet](../enrollment/enrollment-autopilot.md). Administratörer kommer även att kunna ge egna namn som möter användaren vid konfiguration av enheten med Autopilot.
Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment---1608345---"></a>Använda VPP enhetslicenser till att företablera företagsportalen vid DEP-registrering<!-- 1608345 -->
Nu kan du använda VPP-enhetslicenser (volyminköpsprogram) till att företablera företagsportalen under registreringar med Programmet för enhetsregistrering (DEP). Detta gör du genom att ange den VPP-token du vill använda för att installera företagsportalen när du [skapar eller redigerar en registreringsprofil](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Se till att din token inte upphör att gälla och att du har tillräckligt många licenser för företagsportalappen. Om token upphör att gälla eller om licenserna tar slut kan Intune push-överföra företagsportalen från App Store istället (då krävs ett Apple-ID).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning---2237634---"></a>Bekräftelse krävs för att ta bort VPP-token som används för företablering av företagsportalen<!-- 2237634 -->
En bekräftelse krävs nu för att ta bort en token för volymköpsprogram (VPP) om den används för att företablera företagsportalen vid DEP-registrering.

#### <a name="block-windows-personal-device-enrollments---1849498---"></a>Blockera registrering av personliga Windows-enheter<!-- 1849498 -->
Du kan [blockera personliga Windows-enheter](../enrollment/enrollment-restrictions-set.md) från att registrera med [hantering av mobilenheter](../enrollment/windows-enroll.md) i Intune. Enheter som registreras med [Intune PC-agenten](../manage-windows-pcs-with-microsoft-intune.md) kan inte blockeras med den här funktionen. Den här funktionen tas i bruk inom de närmaste veckorna, så den syns kanske inte direkt i användargränssnittet.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile--1849855--"></a>Ange mönster för datornamn i en Autopilot-profil<!--1849855-->
Du kan [ange en mall för datornamn](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) för att generera och ange [datornamnet](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) under Autopilot-registreringen. Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page--1901669---"></a>Dölja alternativen för att ändra konto på företagets inloggningssida och sidan för domänfel för Windows Autopilot-profiler<!--1901669 -->
Det finns [nya Windows Autopilot-profilalternativ](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) som administratörer kan använda för att dölja ändra alternativ för att ändra konto på företagets inloggningssida och sidorna för domänfel. För att dölja de här alternativen krävs att företagsanpassning konfigureras i Azure Active Directory. Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).

### <a name="macos-support-for-apple-device-enrollment-program---747651---"></a>macOS-stöd för Apples program för enhetsregistrering (Device Enrollment Program)<!-- 747651 -->
Intune har nu stöd för registrering av macOS-enheter i Apples program för enhetsregistrering (DEP). Mer information finns i [Registrera macOS-enheter automatiskt med Apples program för enhetsregistrering](../enrollment/device-enrollment-program-enroll-macos.md).

### <a name="device-management"></a>Enhetshantering

#### <a name="delete-jamf-devices---2653306--"></a>Ta bort Jamf-enheter<!-- 2653306-->
Du kan ta bort JAMF-hanterade enheter genom att gå till **Enheter** > välj Jamf-enheten > **Ta bort**.

#### <a name="change-terminology-to-retire-and-wipe---2175759---"></a>Ändra terminologin till ”dra tillbaka” och ”rensa”<!-- 2175759 -->
För att överensstämma med Graph API har följande termer för Intune-användargränssnittet och dokumentationen ändrats:
- **Ta bort företagsinformation** ändras till ”Dra tillbaka”
- **Fabriksåterställning** ändras till **Rensa**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate---297909500--"></a>Bekräftelsedialogruta om administratören försöker ta bort MDM-pushcertifikat<!-- 297909500-->
Om någon försöker ta bort ett Apple MDM-pushcertifikat visar en bekräftelsedialogruta antalet relaterade iOS- och macOS-enheter. Dessa enheter måste registreras igen om certifikatet tas bort.

#### <a name="additional-security-settings-for-windows-installer---2282430---"></a>Ytterligare säkerhetsinställningar för Windows Installer<!-- 2282430 -->
Du kan tillåta användarna att styra appinstallationer. Om den här inställningen är aktiverad tillåts installationer som i annat fall skulle stoppats på grund av en säkerhetsöverträdelse. Du kan ange att Windows Installer ska använda förhöjd behörighet när program installeras i ett system. Du kan också ange att WIP-objekt (Windows Information Protection) ska indexeras och att deras metadata ska lagras på en okrypterad plats. När principen är inaktiverad indexeras inte Windows informationsskyddade objekt och resultaten visas inte i Cortana eller Utforskaren. Funktionerna för dessa alternativ är inaktiverade som standard. 

#### <a name="new-user-experience-update-for-the-company-portal-website--2000968---"></a>Ny uppdatering av användarupplevelse för företagsportalens webbplats<!--2000968 -->
Vi har lagt till nya funktioner på företagsportalen baserat på våra kunders synpunkter. Du kommer att se tydliga förbättringar av befintliga funktioner och användbarheten för dina enheter. Delar av webbplatsen, som enhetsinformation, feedback och support samt enhetsöversikten, har fått en ny och modern design. Andra nyheter:

- Effektiva arbetsflöden mellan olika plattformar
- Bättre flöden för identifiering och registrering av enheter
- Fler användbara felmeddelanden
- Mer användarvänligt språk, mindre teknisk jargong
- Möjlighet att dela direktlänkar till appar
- Förbättrad prestanda för stora app-kataloger
- Bättre tillgänglighet för alla användare  

[Dokumentationen till Intune-företagsportalens webbplats](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) har uppdaterats för att återspegla dessa ändringar. Om du vill se ett exempel på appförbättringarna kan du se [Uppdateringar i användargränssnittet för Intunes slutanvändarappar](../whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Förbättrad upplåsningsidentifiering i efterlevnadsrapportering<!-- 2198738 -->
Inställningsstatus för förbättrad upplåsningsidentifiering visas nu i all efterlevnadsrapportering i administrationskonsolen.

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-policies--1081974---"></a>Omfångstaggar för principer<!--1081974 -->
Du kan [skapa omfångstaggar](scope-tags.md) som begränsar åtkomsten till Intune-resurser. Lägg till en omfångstagg till en rolltilldelning och lägg sedan till omfångstaggen i en konfigurationsprofil. Rollen får endast åtkomst till resurser med konfigurationsprofiler som har matchande omfångstaggar (eller inga omfångstaggar).





<!-- ########################## -->
## <a name="july-2018"></a>Juli 2018

### <a name="app-management"></a>Apphantering

#### <a name="line-of-business-lob-app-support-for-macos---1895847---"></a>Stöd för verksamhetsspecifika appar (LOB) för macOS<!-- 1895847 -->
I Microsoft Intune kan verksamhetsspecifika macOS-appar distribueras med inställningen **Obligatorisk** eller **Tillgänglig med registrering**. Slutanvändarna kan hämta appar som har distribuerats som **tillgängliga** via företagsportalen för macOS eller [företagsportalwebbplatsen](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode---2051098---"></a>Stöd för inbyggda iOS-appar i helskärmsläge<!-- 2051098 -->
Utöver Store-appar och hanterade appar kan du nu välja en inbyggd App (till exempel Safari) som körs i helskärmsläge på en iOS-enhet.

#### <a name="edit-your-office-365-pro-plus-app-deployments---2150145---"></a>Redigera dina distributioner av Office 365 Pro Plus-appar<!-- 2150145 -->
Som Microsoft Intune-administratör har du större möjlighet att redigera distributioner av Office 365 Pro Plus-appar. Dessutom behöver du inte längre ta bort dina distributioner för att ändra svitens egenskaper. I Azure Portal väljer du **Microsoft Intune** > **Klientappar** > **Appar**. Välj Office 365 Pro Plus Suite i listan med appar.  

#### <a name="updated-intune-app-sdk-for-android-is-now-available---2744271--"></a>Uppdaterad Intune App-SDK för Android är nu tillgänglig<!-- 2744271-->
En uppdaterad version av Intune App SDK för Android är tillgänglig som stöd för Android P-versionen. Om du är en apputvecklare och använder Intune SDK för Android, måste du installera den uppdaterade versionen av Intune App SDK för att säkerställa att Intune-funktionerna i dina Android-appar fortsätter att fungera som förväntat på Android P-enheter. Den här versionen av Intune App SDK innehåller ett inbyggt plugin-program som utför SDK-uppdateringarna. Du behöver inte skriva om någon befintlig kod som ingår. Mer information finns i [Intune SDK för Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Om du använder den gamla badging-stilen för Intune, rekommenderar vi att du använder portföljikonen. Mer information relaterad till olika varumärken finns i [den här GitHub-lagringsplatsen](https://github.com/msintuneappsdk/intune-app-partner-badge).

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Fler möjligheter att synkronisera i företagsportalappen för Windows  
Med företagsportalappen för Windows kan du nu initiera en synkronisering direkt från Windows-aktivitetsfältet och Start-menyn. Den här funktionen är särskilt användbart om din enda uppgift är att synkronisera enheter och få åtkomst till företagsresurser. För att komma åt den nya funktionen högerklickar du på ikonen för företagsportalen som har fästs till verktygsfältet eller Start-menyn. I menyalternativen (kallas även en snabblista) väljer du **Sync this device** (Synkronisera den här enheten). Företagsportalen öppnas till sidan **inställningar** och initierar synkroniseringen. En titt på de nya funktionerna finns på sidan om [nyheter i användargränssnittet](../whats-new-app-ui.md).   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nya bläddringsfunktioner i företagsportalappen för Windows  
När du bläddrar eller söker efter appar i företagsportalappen för Windows kan du nu växla mellan den befintliga vyn **Paneler** och den nyligen tillagda vyn **Information**. Den nya vyn visar information om programmet, som namn, utgivare, publiceringsdatum och installationsstatus.  

På sidan **Appar** kan du använda vyn **Installerade** för att se information om slutförda och pågående appinstallationer. Du kan se hur den nya vyn ser ut på sidan om [nyheter i användargränssnittet](../whats-new-app-ui.md).  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Förbättrade funktioner i företagsportalappen för enhetsregistreringshanterare  
När en enhetsregistreringshanterare (DEM) loggar in på företagsportalappen för Windows visar appen nu endast DEM:ens aktuella enhet som körs. Den här förbättringen minskar uppnådda tidsgränser som tidigare förekom när appen försökte visa alla DEM-registrerade enheter.  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models----1425689----"></a>Blockera appåtkomst baserat på ej godkända enhetsleverantörer och -modeller <!-- 1425689 ! -->
Intune IT-administratören kan tillämpa en angiven lista över Android-tillverkare och/eller iOS-modeller via Intune App Protection-principer. IT-administratören kan ange en semikolonavgränsad lista över tillverkare för Android-principer och enhetsmodeller för iOS-principer. Intune App Protection-principer gäller endast för Android och iOS. Det finns två separata åtgärder som kan utföras på den angivna listan:
- En blockering från åtkomst till appen på enheter som inte har angetts.
- Eller en selektiv rensning av företagets data på enheter som inte har angetts. 

Användaren kommer inte att få åtkomst till det aktuella programmet om principkraven inte uppfylls. Baserat på inställningarna kan användaren bli blockerad eller rensas selektivt på sina företagsdata i appen. På iOS-enheter kräver den här funktionen att program deltar (t.ex. WXP, Outlook, Managed Browser, Yammer) för att integrera Intune APP SDK:n för att funktionen ska framtvingas i berörda program. Den här integreringen händer på löpande bas, och är beroende av specifika programteam. På Android kräver funktionen den senaste företagsportalen. 

På slutanvändarens enheter utför Intune-klienten åtgärder baserat på en enkel matchning av strängar som angetts i Intune-bladet för programskyddsprinciper. Detta beror helt på värdet som enheten rapporterar. IT-administratören rekommenderas därför att säkerställa att det avsedda funktionssättet är korrekt. Detta kan åstadkommas genom att testa den här inställningen baserat på en rad olika enhetstillverkare och modeller som är riktade till en liten användargrupp. I Microsoft Intune väljer du **Klientappar** > **Appskyddsprinciper** för att visa och lägga till appskyddsprinciper. Mer information om att appskyddsprinciper finns i [Vad är appskyddsprinciper](../apps/app-protection-policy.md) och [Selektiv rensning av data med åtkomståtgärder för appskyddsprinciper i Intune](../apps/app-protection-policies-access-actions.md).

#### <a name="access-to-macos-company-portal-pre-release-build---1734766---"></a>Åtkomst till förhandsversionen av företagsportalen på macOS<!-- 1734766 -->
Du kan registrera dig för att ta emot versioner tidigt genom att gå med i Insider-programmet med hjälp av Microsoft AutoUpdate. När du registrerat dig kan du använda den uppdaterade företagsportalen innan den är tillgänglig för dina slutanvändare. Mer information finns i [Microsoft Intune-bloggen](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices---1497640---"></a>Skapa en princip för enhetsefterlevnad med hjälp av brandväggsinställningar på macOS-enheter<!-- 1497640 -->
När du skapar en ny efterlevnadsprincip i macOS (**Enhetsefterlevnad** > **Principer** > **skapa princip** > **Plattform: macOS** > **Systemsäkerhet**) finns det några nya **brandväggsinställningar** tillgängliga: 

- **Brandvägg**: Konfigurera hur inkommande anslutningar ska hanteras i din miljö.
- **Inkommande anslutningar**: **Blockera** alla inkommande anslutningar, förutom de som behövs för grundläggande Internettjänster som DHCP, Bonjour och IPSec. Den här inställningen blockerar också alla delningstjänster.
- **Dolt läge**: **Aktivera** dolt läge om du vill förhindra att enheten svarar på avsökningsförfrågningar. Enheten fortsätter att besvara inkommande begäranden för godkända appar.

Gäller: macOS 10.12 och senare

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later---1879077---"></a>Ny enhetskonfigurationsprofil för Wi-Fi för Windows 10 och senare<!-- 1879077 -->
För närvarande kan du importera och exportera Wi-Fi-profiler med hjälp av XML-filer. Med den här uppdateringen kan du skapa en enhetskonfigurationsprofil för Wi-Fi direkt i Intune, precis som på vissa andra plattformar.

Om du vill skapa profilen öppnar du **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** > **Wi-Fi**. 

Gäller för Windows 10 och senare.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed---2149998---"></a>Helskärmsläge – inaktuell är nedtonad och kan inte ändras<!-- 2149998 -->
Funktionen Helskärmsläge (förhandsversion) (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** > **Enhetsbegränsningar**) är inaktuell och ersätts med [Inställningar för helskärmsläge för Windows 10 och senare](../configuration/kiosk-settings.md). Med den här uppdateringen är funktionen **Helskärmsläge – inaktuell** nedtonad och användargränssnittet kan inte ändras eller uppdateras. 

Om du vill aktivera helskärmsläge kan du läsa mer i [Inställningar för helskärmsläge för Windows 10 och senare](../configuration/kiosk-settings.md).

Gäller för Windows 10 och senare, Windows 10 Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities---2184013---"></a>API:erna använder tredjeparts certifikatutfärdare<!-- 2184013 -->
I den här uppdateringen finns det ett Java-API som gör det möjligt för tredjeparts certifikatutfärdare att integrera med Intune och SCEP. Sedan kan användarna lägga till SCEP-certifikatet till en profil och tillämpa det på enheter med hjälp av MDM.

Intune stöder för närvarande [SCEP-förfrågningar med hjälp av Active Directory Certificate Services](../protect/certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser---2455253---"></a>Växla att visa eller dölja knappen Avsluta session i en webbläsare i helskärmsläge<!-- 2455253 -->
Du kan nu konfigurera om webbläsare i helskärmsläge ska visa knappen Avsluta session. Du kan se kontrollen under **Enhetskonfiguration** > **Helskärmsläge (förhandsgranskning)**  > **Webbläsare i helskärmsläge**. När en användare klickar på knappen när den är aktiverad frågar appen om du verkligen vill avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata och går tillbaka till den webbadress som är standard.

#### <a name="create-an-esim-cellular-configuration-profile---2564077---"></a>Skapa en konfigurationsprofil för eSIM-mobilnät<!-- 2564077 -->
I **Enhetskonfiguration** kan du skapa en profil för eSIM-mobilnät. Du kan importera en fil som innehåller aktiveringskoder för mobilnät som tillhandahålls av din mobiloperatör. Du kan sedan distribuera de här profilerna till dina Windows 10-enheter som aktiverat eSIM LTE, till exempel Surface Pro LTE och andra eSIM-kompatibla enheter.

Kontrollera om dina [enheter stöder eSIM-profiler](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Gäller för Windows 10 och senare.

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings---1058963-eenotready---"></a>Välja enhetskategorier med hjälp av inställningarna för åtkomst till arbete eller skola<!-- 1058963 eenotready --> 
Om du har aktiverat [mappning av enhetsgrupp](../enrollment/device-group-mapping.md), uppmanas Windows 10-användare nu att välja en enhetskategori efter registreringen via knappen **Anslut** i **Inställningar** > **Konton** > **Åtkomst till arbete eller skola**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles---1500307---"></a>Använda sAMAccountName som kontots användarnamn för e-postprofiler<!-- 1500307 -->
Du kan använda det lokala **sAMAccountName** som kontonamn för e-postprofiler för Android, iOS och Windows 10. Du kan även hämta domänen från attributet `domain` eller `ntdomain` i Azure Active Directory (Azure AD). Eller ange en anpassad statisk domän.

Om du vill använda den här funktionen måste du synkronisera attributet `sAMAccountName` från din lokala Active Directory-miljö till Azure AD.

Gäller [Android](../configuration/email-settings-android.md), [iOS](../configuration/email-settings-ios.md) samt [Windows 10 och senare](../configuration/email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict---1556983---"></a>Visa enhetskonfigurationsprofiler som har konflikter<!-- 1556983 -->
I **Enhetskonfiguration** visas en lista över de befintliga profilerna. I och med den här uppdateringen läggs en ny kolumn till som innehåller information om de profiler som står i konflikt. Du kan välja en rad med en konflikt för att se den inställning och den profil som orsakar konflikten. 

Mer om [hantering av konfigurationsprofiler](../configuration/device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance---2308882---"></a>Ny status för enheter i enhetsefterlevnad<!-- 2308882 -->
Följande nya tillstånd har lagts till i **Enhetskonfiguration** > **Principer** > välj en princip > **Översikt**:
- lyckades
- fel
- konflikt
- Väntar
- inte tillämpligt En bild med antalet enheter på andra plattformar visas också. Om du till exempel tittar på en iOS-profil visas antalet enheter med andra system än iOS som också har tilldelats till den här profilen. Se [Efterlevnadsprinciper för enheter](../protect/compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions---2325484---"></a>Enhetsefterlevnaden stöder antiviruslösningar från tredje part<!-- 2325484 -->
När du skapar en princip för enhetsefterlevnad (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Plattform: Windows 10 och senare** > **Inställningar** > **Systemsäkerhet**), finns det nya alternativ för **[Enhetssäkerhet](../protect/compliance-policy-create-windows.md)** : 
- **Antivirus**: När **Kräv** har valts kan du kontrollera efterlevnaden med antivirusprogram som är registrerade i Windows Security Center, t.ex. Symantec eller Windows Defender. 
- **AntiSpyware**: När **Kräv** har valts kan du kontrollera efterlevnaden med något av de antispionprogram som har registrerats med Windows Security Center, t.ex. Symantec eller Windows Defender. 

Gäller för: Windows 10 och senare 

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate---2404851---"></a>Markera automatiskt Android-enheter som registrerats med hjälp av Samsung Knox Mobile-registrering som ”företagsägda”.<!-- 2404851 -->
Som standard markeras Android-enheter som registrerats med Samsung Knox Mobile-registrering nu som **företagsägda** under **Ägarskap för enhet**. Du behöver inte identifiera företagets enheter manuellt med hjälp av IMEI- eller serienummer innan du registrerar med Samsung Knox Mobile-registrering.

#### <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens---1853904---"></a>Enheter utan profilkolumn i listan över token för registreringsprogram<!-- 1853904 -->
Det finns en ny kolumn i listan med token för registreringsprogram som visar antalet enheter som inte har någon tilldelad profil. På så sätt kan administratörer tilldela profiler till dessa enheter innan användarna får dem. Om du vill se den nya kolumnen går du till **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram**.

### <a name="device-management"></a>Enhetshantering

#### <a name="bulk-delete-devices-on-devices-blade---1793693---"></a>Massborttagning av enheter på enhetsbladet<!-- 1793693 -->
Du kan nu ta bort flera enheter samtidigt på enhetsbladet. Välj **Enheter** > **Alla enheter** > välj de enheter som du vill ta bort > **Ta bort**. En avisering visas för enheter som inte kan tas bort.

#### <a name="google-name-changes-for-android-for-work-and-play-for-work--842873---"></a>Namnändringar hos Google för Android for Work och Play for Work<!--842873 -->
Intune har uppdaterat ”Android for Work”-terminologin med Googles namnändringar. Termerna ”Android for Work” och ”Play for Work” används inte längre. Annan terminologi används beroende på kontext:
- ”Android enterprise” syftar på den moderna programserien för Android-hantering som helhet.
- ”Arbetsprofil” eller ”profilägare” syftar på BYOD-enheter som hanteras med arbetsprofiler.
- ”Managed Google Play” syftar på Googles appbutik.

#### <a name="rules-for-removing-devices---1609459---"></a>Regler för att ta bort enheter<!-- 1609459 -->
Det finns nya regler som gör att du automatiskt kan ta bort enheter som inte har checkats in under ett visst antal dagar som du anger. Om du vill se den nya regeln går du till fönstret **Intune**, väljer **Enheter** och sedan **Regler för rensning av enhet**.

#### <a name="corporate-owned-single-use-support-for-android-devices---1630973---"></a>COSU-stöd (Corporate Owned, Single Use) för Android-enheter<!-- 1630973 -->

Nu har Intune stöd för strikt hanterade och låsta Android-enheter i helskärmsläge. Det här gör att administratörer får fler verktyg när det gäller att begränsa användningen på en enhet till en enda upp eller en grupp av appar, så att användarna inte kan starta andra appar eller utföra andra åtgärder på enheten. Du konfigurerar Android-kioskenheter genom att gå till Intune > **Enhetsregistrering** > **Android-registrering** > **Registreringar av kiosk- och aktivitetsenheter**. Läs mer i informationen om att [konfigurera registrering av Android-kioskenheter för företag](../enrollment/android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded---2203794--"></a>Granskning per rad av dubbletter av uppladdade företagsenhets-ID:n<!-- 2203794-->
När du laddar upp företags-ID:n får du nu en lista med eventuella dubbletter i Intune, och du kan välja mellan att ta bort eller behålla den befintliga informationen. Rapporten visas om det finns dubbletter när du har valt **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till id:n**. 

#### <a name="manually-add-corporate-device-identifiers---2203803---"></a>Lägga till företagsenhets-ID:n manuellt<!-- 2203803 -->
Nu kan du lägga till ID:n för företagsenheter manuellt. Välj **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till**. 


<!-- ########################## -->
## <a name="june-2018"></a>Juni 2018

### <a name="app-management"></a>Apphantering

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies---1817882---"></a>Microsoft Edge-mobilstöd för Intune-appskyddsprinciper<!-- 1817882 -->
Microsoft Edge-webbläsaren för mobila enheter stödjer nu appskyddsprinciper som definieras i Intune.

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode---1560077----"></a>Hämta den kopplade appanvändarens modell-ID (AUMID) för Microsoft Store för företagsappar i helskärmsläge<!-- 1560077 ! -->
Nu kan Intune hämta appanvändarens modell-ID:n (AUMID:n) för Microsoft Store för företag-appar (WSfB) för enklare konfiguration av profilen för helskärmsläge.

Mer information om Microsoft Store för företagsappar finns i [Hantera appar från Microsoft Store för företag](../apps/windows-store-for-business.md).

#### <a name="new-company-portal-branding-page---1916370---"></a>Ny sida för företagsportalanpassning<!-- 1916370 -->
Sidan för företagsportalanpassning har en ny layout, nya meddelanden och beskrivningar.


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="pradeo---new-mobile-threat-defense-partner---1169249---"></a>Pradeo – ny partner för skydd mot mobilhot<!-- 1169249 -->
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Pradeo, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune.

#### <a name="use-fips-mode-with-the-ndes-certificate-connector---1333688---"></a>Använda FIPS-läge med NDES-certifikatanslutningsappen<!-- 1333688 -->
När du installerar NDES-certifikatanslutningsappen på en dator med FIPS-läget (Federal Information Processing Standard) aktiverat fungerade inte utfärdande och återkallande av certifikat som förväntat. I och med den här uppdateringen ingår stöd för FIPS i NDES-certifikatanslutningsappen. 

Den här uppdateringen innehåller även:

- För NDES-certifikatanslutningsappen krävs .NET 4.5 Framework, som automatiskt ingår i Windows Server 2016 och Windows Server 2012 R2. Tidigare var .NET 3.5 Framework den minimiversion som krävdes.
- Stöd för TSL 1.2 ingår i NDES-certifikatanslutningsappen. Om servern med NDES-certifikatanslutningsappen installerat stödjer TLS 1.2 används därmed TLS 1.2. Om servern inte stödjer TLS 1.2 används TLS 1.1. För närvarande används TLS 1.1 för autentisering mellan enheter och servern.

Mer information finns på sidorna om att [konfigurera och använda SCEP-certifikat](../protect/certificates-scep-configure.md) och [konfigurera och använda PKCS-certifikat](../protect/certficates-pfx-configure.md).

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles---1333680----"></a>Stöd för Palo Alto Networks GlobalProtect VPN-profiler<!-- 1333680 ! -->
Med den här uppdateringen kan du välja Palo Alto Networks GlobalProtect som VPN-anslutningstyp för VPN-profiler i Intune (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Profiltyp** > **VPN**). I den här versionen stöds följande plattformar: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings---1403702---"></a>Tillägg till inställningar av säkerhetsalternativ för lokal enhet<!-- 1403702 -->
Nu kan du konfigurera ytterligare inställningar av säkerhetsalternativ för lokala Windows 10-enheter. Det finns fler inställningar i Microsoft-nätverksklienten, Microsoft-nätverksservern, för nätverksåtkomst och säkerhet, samt för interaktiv inloggning. Inställningarna finns i kategorin Endpoint Protection när du skapar en princip för Windows 10-enhetskonfiguration.

#### <a name="enable-kiosk-mode-on-windows-10-devices---1560072----"></a>Aktivera helskärmsläge på Windows 10-enheter<!-- 1560072 ! -->
På Windows 10-enheter kan du skapa en konfigurationsfil och aktivera helskärmsläge (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10** > **Enhetsbegränsningar** > **Helskärmsläge**). I den här uppdateringen av **Helskärmsläge (förhandsgranskning)** döps inställningen om till **Helskärmsläge (föråldrad)** . **Helskärmsläge (föråldrad)** rekommenderas inte längre för användning, men fortsätter att fungera fram till juli-uppdateringen. **Helskärmsläge (föråldrad)** ersätts av den nya profiltypen **Helskärmsläge** (**Skapa profil** > **Windows 10** > **Helskärmsläge (förhandsgranskning)** ), som innehåller inställningar för att konfigurera helskärmslägen på Windows 10 RS4 och senare.

Gäller för Windows 10 och senare.

#### <a name="device-profile-graphical-user-chart-is-back---2160133---"></a>Enhetsprofilens grafiska användardiagram är tillbaka<!-- 2160133 -->
För att förbättra det numeriska antal som visas på enhetsprofilens grafiska diagram (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**), togs det grafiska diagrammet tillfälligt bort.

Med den här uppdateringen är det grafiska användardiagrammet tillbaka och visas i Azure Portal.

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication---1165118---"></a>Stöd för Windows Autopilot-registrering utan användarautentisering<!-- 1165118 -->
Nu finns det stöd i Intune för Windows Autopilot-registrering utan användarautentisering. Det här är ett nytt alternativ i distributionsprofilen för Windows Autopilot där ”Distributionsläge för Autopilot” får värdet ”Automatisk distribution”.  Enheten måste köra Windows 10 Insider Preview-version 17672 eller senare och ha ett TPM 2.0-chip för att slutföra den här typen av registrering. Eftersom det inte krävs någon användarautentisering bör du bara tilldela det här alternativet för enheter du har fysisk kontroll över.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot---1821766---"></a>Ny språk-/regionsinställning vid konfiguration av OOBE för Autopilot<!-- 1821766 -->
En ny konfigurationsinställning kan ange språk och region för Autopilot-profiler från första början. Du ser den nya inställningen om du väljer **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil** > **Distributionsläge** = **Självdistribuerande** > **Standardkonfiguration**.

#### <a name="new-setting-for-configuring-device-keyboard---1821768---"></a>Ny inställning för konfiguration av enhetstangentbord<!-- 1821768 -->
En ny inställning kommer att kunna konfigurera tangentbordet för Autopilot-profiler under Out of Box-upplevelsen. Du ser den nya inställningen om du väljer **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil** > **Distributionsläge** = **Självdistribuerande** > **Standardkonfiguration**.

#### <a name="autopilot-profiles-moving-to-group-targeting---1877935---"></a>AutoPilot-profiler flyttas till gruppinriktning<!-- 1877935 -->
AutoPilot-distributionsprofiler kan tilldelas till Azure AD-grupper som innehåller AutoPilot-enheter.

### <a name="device-management"></a>Enhetshantering

#### <a name="set-compliance-by-device-location---851881----"></a>Ange efterlevnad enligt enhetsplats<!-- 851881 ! -->
I vissa fall kanske du vill begränsa åtkomsten till företagets resurser till en specifik plats som definierats av en nätverksanslutning. Nu kan du skapa en efterlevnadsprincip (**Enhetsefterlevnad** > **Platser**) baserat på IP-adressen till enheten. Om enheten flyttas utanför IP-intervallet kan enheten inte komma åt företagets resurser.

Gäller för: Android-enheter med version 6.0 och senare, med den uppdaterade företagsportalappen

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Förhindra konsumentappar och funktioner för anpassad upplevelse i Windows 10 Enterprise RS4 AutoPilot-enheter<!-- 1621980 -->
Du kommer att kunna förhindra installationen av konsumentappar och funktioner för anpassad upplevelse på dina Windows 10 Enterprise RS4 AutoPilot-enheter. Du ser den här funktionen om du går till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Plattform** = **Windows 10 eller senare** > **Profiltyp** = **Enhetsbegränsningar** > **Konfigurera** > **Windows Spotlight** > **Konsumentfunktioner**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates---1732948---"></a>Avinstallera den senaste versionen från programuppdateringar för Windows 10<!-- 1732948 -->
Om du upptäcker ett allvarligt problem på dina Windows 10-datorer kan du avinstallera den senaste funktionsuppdateringen eller den senaste kvalitetsuppdateringen. Du kan bara avinstallera en funktions- eller kvalitetsuppdatering via enhetens underhållskanal. Vid avinstallationen utlöses en princip för att återställa den tidigare uppdateringen på Windows 10-datorerna. För funktionsuppdateringar specifikt kan du begränsa tiden från 2–60 dagar som en avinstallation av den senaste versionen kan tillämpas. Om du vill ange alternativ för avinstallation av programuppdateringar väljer du **Programuppdateringar** från bladet **Microsoft Intune** i Azure Portal. Välj sedan **Windows 10-uppdateringsringar** på bladet **Programuppdateringar**. Du kan sedan välja alternativet **Avinstallera** i avsnittet **Översikt**.

#### <a name="search-all-devices-for-imei-and-serial-number---1793685---"></a>Söka alla enheters IMEI och serienummer<!-- 1793685 -->
Du kan nu söka efter IMEI och serienummer på bladet Alla enheter (e-post, UPN, enhetsnamn och hanteringsnamn finns kvar). Välj **Enheter** > **Alla enheter** i Intune och ange dina sökvillkor i sökrutan.

#### <a name="management-name-field-will-be-editable---1875989---"></a>Hanteringsnamnfältet kan redigeras<!-- 1875989 -->
Nu kan du redigera hanteringsnamnfältet på bladet **Egenskaper** för en enhet. Om du vill redigera det här fältet väljer du **Enheter** > **Alla enheter** > välj enheten > **Egenskaper**. Du kan använda hanteringsnamnfältet för att unikt identifiera en enhet.

#### <a name="new-all-devices-filter-device-category---1878520---"></a>Nytt filter för Alla enheter: Enhetskategori<!-- 1878520 -->
Nu kan du filtrera listan **Alla enheter** efter enhetskategori. Om du vill göra det väljer du **Enheter** > **Alla enheter** > **Filter** > **Enhetskategori**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices---1985547---"></a>Använda TeamViewer för att skärmdela iOS- och MacOS-enheter<!-- 1985547 -->
Nu kan administratörer ansluta till [TeamViewer](../remote-actions/teamviewer-support.md) och börja skärmdela en session med iOS- och macOS-enheter. iPhone-, iPad- och macOS-användare kan dela sina skärmar live med andra stationära och mobila enheter. 

#### <a name="multiple-exchange-connector-support---2070451---"></a>Stöd för flera Exchange-anslutningsappar<!-- 2070451 -->
Du är inte längre begränsad till en Exchange-anslutningsapp per klientorganisation i Microsoft Intune. Intune har nu stöd för flera Exchange-anslutningsappar, så att du kan ställa in villkorlig åtkomst i Intune med flera lokala Exchange-organisationer.

Med en lokal Exchange Connector för Intune kan du hantera enhetsåtkomst till dina lokala Exchange-postlådor, baserat på om en enhet har registrerats i Intune och uppfyller Intunes enhetsefterlevnadsprinciper. Om du vill konfigurera ett anslutningsprogram laddar du ned den lokala Exchange Connector för Intune från Azure-portalen och installerar den på en server i Exchange-organisationen. På Microsoft Intune-instrumentpanelen väljer du **Lokal åtkomst** och under **Installation** väljer du sedan **Exchange ActiveSync Connector**. Ladda ned det lokala Exchange-anslutningsprogrammet och installera det på en server i din Exchange-organisation. Nu när du är inte längre begränsad till ett Exchange-anslutningsprogram per klient, och om du har ytterligare Exchange-organisationer, kan du följa samma process för att ladda ned och installera ett anslutningsprogram för varje ytterligare Exchange-organisation.

#### <a name="new-device-hardware-detail-ccid---2156657---"></a>Ny detalj i enhetens maskinvara: CCID<!-- 2156657 -->
Nu ingår CCID-informationen (Chip Card Interface Device) för varje enhet. Om du vill se den väljer du **Enheter** > **Alla enheter** > välj en enhet > **Maskinvara**> leta under **Nätverksinformation**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups---2196803---"></a>Tilldela alla användare och alla enheter som omfångsgrupper<!-- 2196803 -->
Nu kan du tilldela alla användare, alla enheter samt alla användare och alla enheter i omfångsgrupper. Om du vill göra det väljer du **Intune-roller** > **Alla roller** > **Policy and profile manager** > **Tilldelningar** > välj en tilldelning > **Omfång (grupper)** .

#### <a name="udid-information-now-included-for-ios-and-macos-devices---2219806---"></a>Nu ingår UDID-information för iOS- och macOS-enheter<!-- 2219806 -->
Om du vill se UDID (Unique Device Identifier) för iOS- och macOS-enheter går du till **Enheter** > **Alla enheter** > välj en enhet > **Maskinvara**. UDID är endast tillgängligt för företagsenheter (anges under **Enheter** > **Alla enheter** > välj en enhet > **Egenskaper** > **Ägarskap för enhet**).

### <a name="intune-apps"></a>Intune-appar

#### <a name="improved-troubleshooting-for-app-installation---928990---"></a>Förbättrad felsökning för appinstallation<!-- 928990 -->
På Microsoft Intune MDM-hanterade enheter kan ibland appinstallationer misslyckas. När dessa appinstallationer misslyckas, kan det vara en utmaning att förstå felorsaken eller felsöka problemet. Vi levererar en allmänt tillgänglig förhandsversion av våra appfelsökningsfunktioner. Du ser en ny nod under varje enskild enhet som kallas **Hanterade appar**. Den visar en lista med appar som har levererats via Intune MDM. I noden visas en lista över installeringstillstånd för appar. Om du väljer en enskild app visas vyn felsökning för den specifika appen. I felsökningsvyn visas slutpunkt till slutpunkt-livscykeln för appen, till exempel när appen har skapats, ändrats, riktats och levererats till en enhet. Dessutom, om inte appinstallationen lyckades visas felkoden och ett användbart meddelande om orsaken till felet. 

#### <a name="intune-app-protection-policies-and-microsoft-edge---1818968---"></a>Intune-appskyddsprinciper och Microsoft Edge<!-- 1818968 -->
Microsoft Edge-webbläsaren för mobila enheter (iOS och Android) har nu stöd för skyddsprinciper i Microsoft Intune-appen. Användare med iOS- och Android-enheter som loggar in med företagets Azure AD-konto i Microsoft Edge skyddas av Intune. På iOS-enheter gör principen **Kräver hanterad webbläsare för webbinnehåll** att användarna kan öppna länkar i Microsoft Edge när det hanteras.

<!-- ########################## -->
## <a name="may-2018"></a>Maj 2018

### <a name="app-management"></a>Apphantering

#### <a name="configuring-your-app-protection-policies---2144597-part-2---"></a>Konfigurera dina appskyddsprinciper<!-- 2144597 Part 2 -->

I stället för att gå till bladet för Intunes appskyddstjänst på Azure Portal går du bara till Intune nu. Nu finns det bara en plats för appskyddsprinciper i Intune. Observera att alla dina appskyddsprinciper finns på bladet **Mobilapp** i Intune under **Appskyddsprinciper**. Den här integrationen gör det enklare att administrera molnhanteringen. Alla appskyddsprinciper finns redan i Intune och du kan ändra redan konfigurerade principer. Intunes apprincipskydd (APP) och principer för villkorlig åtkomst (CA) finns nu under **Villkorlig åtkomst**, som du hittar under avsnittet **Hantera** på bladet **Microsoft Intune** under avsnittet **Säkerhet** på bladet **Azure Active Directory**. Mer information om hur du ändrar principer för villkorlig åtkomst finns [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Ytterligare information finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md)

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles---1553555---"></a>Kräv installation av principer, appar, certifikat och nätverksprofiler<!-- 1553555 -->
Administratörer kan blockera slutanvändarna från att komma åt skrivbordet i Windows 10 RS4 tills Intune har installerat principer, appar, certifikat och nätverksprofiler under etableringen av AutoPilot-enheter. Mer information finns i [Konfigurera en sida för registreringsstatus](../enrollment/windows-enrollment-status.md).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="samsung-knox-mobile-enrollment-support--1112863--"></a>Stöd för Samsung Knox Mobile Enrollment<!--1112863-->
När du använder Intune med Samsung Knox Mobile-registrering (KME), kan du registrera ett stort antal företagsägda Android-enheter. Användarna på Wi-Fi eller mobila nätverk kan registrera sig med bara några få tryck när de aktiverar på sina enheter för första gången. När du använder Knox-distributionsprogrammet kan enheter registreras med hjälp av Bluetooth eller NFC. Mer information finns i [Registrera Android-enheter automatiskt med hjälp av från Samsung Knox Mobile-registrering](../enrollment/android-samsung-knox-mobile-enroll.md).

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka 

#### <a name="requesting-help-in-the-company-portal-for-windows-10---1874137---"></a>Begära hjälp i företagsportalen för Windows 10<!-- 1874137 -->
Företagsportalen för Windows 10 kommer nu att skicka apploggar direkt till Microsoft när användaren startar arbetsflödet för att få hjälp med problemet. Detta gör det enklare att felsöka och lösa problem som tas upp till Microsoft.

<!-- ########################## -->
## <a name="april-2018"></a>April 2018

### <a name="app-management"></a>Apphantering

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Lösenordsstöd för MAM PIN-kod på Android<!-- 1438086 -->

Intune-administratörer kan ange ett programstartskrav för att framtvinga ett lösenord i stället för en numerisk MAM PIN-kod. Om det har konfigurerats måste användaren vid uppmaning ställa in och använda ett lösenord innan användaren får åtkomst till MAM-integrerade program. Ett lösenord definieras som en numerisk PIN-kod med minst ett specialtecken eller en gemen/versal. Intune stöder lösenord på liknande sätt som numeriska PIN-koder. En minsta längd kan anges, vilket tillåter upprepning av tecken och sekvenser via administratörskonsolen. Den här funktionen kräver den senaste versionen av företagsportalen för Android. Funktionen finns redan tillgänglig för iOS.

#### <a name="line-of-business-lob-app-support-for-macos---1473977---"></a>Stöd för verksamhetsspecifika appar (LOB) för macOS<!-- 1473977 -->
I Microsoft Intune går det att installera branschspecifika macOS-appar från Azure Portal. Du kommer att kunna lägga till en branschspecifik macOS-app i Intune som redan har förbehandlats av verktyget i GitHub. I Azure Portal väljer du **Klientappar** på bladet **Intune**. På bladet **Klientappar** väljer du **Appar** > **Lägg till**. På bladet **Lägg till app** väljer du **Branschspecifik app**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment---1813073---"></a>Inbyggda grupper för Alla användare och Alla enheter för apptilldelning för Android Enterprise-arbetsprofiler<!-- 1813073 -->
Du kan använda de inbyggda grupperna **Alla användare** och **Alla enheter** vid apptilldelning för Android enterprise-arbetsprofil. Mer information finns i [Inkludera och exkludera apptilldelningar i Microsoft Intune](../apps/apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users---1947010---"></a>Intune kommer att installera om obligatoriska appar som avinstalleras av användare<!-- 1947010 -->
Om en slutanvändare avinstallerar en obligatorisk app, installerar Intune automatiskt om appen igen inom 24 timmar i stället för att vänta på omvärderingscykeln på 7 dagar.

#### <a name="update-where-to-configure-your-app-protection-policies---2144597---"></a>Uppdatera var dina appskyddsprinciper konfigureras<!-- 2144597 -->

I tjänsten Microsoft Intune i Azure Portal kommer vi att tillfälligt dirigera om dig från bladet för tjänsten **Intune-appskydd** till bladet **Mobilapp**. Alla dina appskyddsprinciper finns redan på bladet **Mobilapp** i Intune under appkonfigurationen. I stället för att gå till Intune-appskydd går du bara till Intune. I april 2018 stoppar vi omdirigeringen och tar helt bort bladet för tjänsten **Intune-appskydd** så att det bara finns en plats för appskyddsprinciper i Intune. 

**Hur påverkar det här mig?**
Den här förändringen påverkar både kunder som har fristående Intune och hybridkunder (Intune med Configuration Manager). Den här integreringen hjälper till att förenkla administrationen av molnhanteringen.

**Vad kan jag göra för att förbereda mig för den här ändringen?**
Lägg till **Intune** som favorit i stället för bladet för tjänsten **Intune-appskydd**, och se till att du känner till arbetsflödet för appskyddsprinciper på bladet **Mobilapp** i Intune. Vi omdirigerar under en kort tidsperiod och tar sedan bort **appskyddsbladet**. Tänk på att alla appskyddsprinciper redan finns i Intune och att du kan ändra dina villkorliga åtkomstprinciper. Mer information om hur du ändrar principer för villkorlig åtkomst finns [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Ytterligare information finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md) 

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group---1449153---"></a>Enhetsprofildiagram och -statuslista visar alla enheter i en grupp<!-- 1449153 -->
När du konfigurerar en enhetsprofil (**Enhetskonfiguration** > **Profiler**) väljer du enhetsprofil, till exempel iOS. Du tilldelar profilen till en grupp med både iOS-enheter och enheter som inte är iOS. Antalet i det grafiska diagrammet visar att profilen tillämpas på både iOS-enheter *och* enheter som inte är iOS (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**). När du väljer det grafiska diagrammet på fliken **Översikt** visar **Enhetsstatus** alla enheterna i gruppen, i stället för enbart iOS-enheterna. 

Med den här uppdateringen visar det grafiska diagrammet (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**) endast antalet för den specifika enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för iOS-enheter, visar diagrammet endast antal iOS-enheter. Om du väljer det grafiska diagrammet och öppnar **Enhetsstatus**, visas endast iOS-enheterna.

När uppdateringen gjorts har det grafiska diagrammet tillfälligt tagits bort. 

#### <a name="always-on-vpn-for-windows-10--1333666---"></a>AlwaysOn-VPN för Windows 10<!--1333666 -->

För närvarande kan [AlwaysOn](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) användas på Windows 10-enheter med hjälp av en anpassad VPN-profil (virtuellt privat nätverk) som skapats med OMA-URI.

Med den här uppdateringen kan administratörer aktivera AlwaysOn för VPN-profiler i Windows 10 direkt i Intune i Azure-portalen. VPN-profiler med AlwaysOn ansluts automatiskt när:

- Användarna loggar in på sina enheter
- Nätverket på enheten ändras
- Skärmen på enheten sätts på efter att ha varit avstängd

#### <a name="new-printer-settings-for-education-profiles---1308900---"></a>Nya skrivarinställningar för utbildningsprofiler<!-- 1308900 -->

Det finns nya inställningar för utbildningsprofiler under kategorin **Skrivare**: **Skrivare**, **Standardskrivare**, **Lägg till nya skrivare**.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile--1098984---"></a>Visa nummerpresentation i personlig profil – Android Enterprise-arbetsprofil<!--1098984 -->
När du använder en personlig profil på en enhet, kan slutanvändare inte se nummerpresentation för en arbetskontakt. 

I och med uppdateringen finns en ny inställning i **Android Enterprise** > **Enhetsbegränsningar** > **Arbetsprofilinställningar**:
- Visa arbetskontaktens nummerpresentation i personlig profil

När aktiverat (inte konfigurerat), visas arbetskontaktens nummerpresentation i den personliga profilen. När blockerad, visas inte arbetskontaktens nummerpresentation i den personliga profilen. 

Gäller för: Androids arbetsprofilenheter på Android OS v6.0 och senare

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings--1102252-----from-1802-and-1804--"></a>Nya Windows Defender Credential Guard-inställningar har lagts till i inställningarna för slutpunktsskydd<!--1102252 --><!--from 1802 and 1804-->

Med denna uppdatering, inkluderar [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Enhetskonfiguration** > **Profiler** > **Slutpunktsskydd**) följande inställningar: 

- **Windows Defender Credential Guard**: Aktiverar Credential Guard med virtualiseringsbaserad säkerhet. Aktivering av den här funktionen hjälper till att skydda autentiseringsuppgifterna vid nästa omstart när både **Säker start för Säkerhetsnivå för plattform** och **Virtualiseringsbaserad säkerhet** är aktiverade. Alternativen är:
  - **Inaktiverad**: Om Credential Guard har aktiverats tidigare med alternativet**Aktiverat utan lås**, slås Credential Guard av på distans.

  - **Aktiverat med UEFI-lås**: Ser till att Credential Guard inte kan inaktiveras med en registernyckel eller via en grupprincip. Om du vill inaktivera Credential Guard när du använder den här inställningen måste du ställa in Grupprincip som ”Inaktiverad”. Ta sedan bort säkerhetsfunktionen från varje dator med en användare fysiskt närvarande. De här stegen rensar den kvarstående konfigurationen i UEFI. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.

  - **Aktiverat utan lås**: Innebär att Credential Guard kan inaktiveras på distans med grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 eller senare (version 1511).

Följande beroende tekniker aktiveras automatiskt när du konfigurerar Credential Guard: 

- **Aktivera virtualiseringsbaserad säkerhet (VBS)** : Aktiverar virtualiseringsbaserad säkerhet (VBS) vid nästa omstart. Virtualiseringsbaserad säkerhet använder Windows Hypervisor för att ge stöd för säkerhetstjänster och kräver Säker start.
- **Säker start med direkt minnesåtkomst (DMA)** : Aktiverar VBS med säker start och direkt minnesåtkomst. DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade. 

#### <a name="use-a-custom-subject-name-on-scep-certificate---2064190---"></a>Använda ett anpassat certifikatmottagarnamn på SCEP-certifikat<!-- 2064190 -->
Du kan använda det egna namnet **OnPremisesSamAccountName** i en anpassad certifikatmottagare för en SCEP-certifikatprofil. Du kan till exempel använda `CN={OnPremisesSamAccountName})`.

#### <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles---1098977---"></a>Blockera kamera- och skärmbilder i Android Enterprise-arbetsprofiler<!-- 1098977 -->
Två nya egenskaper kan blockeras när du konfigurerar enhetsbegränsningar för Android-enheter: 
- Kamera: Blockerar åtkomsten till alla kameror på enheten
- Skärmbild: Blockerar skärmbildtagning och förhindrar också att innehållet visas på enheter som inte har någon säker videoutgång

Gäller för Android Enterprise-arbetsprofiler.

#### <a name="use-cisco-anyconnect-client-for-ios---1333708---"></a>Använda Cisco AnyConnect-klienten för iOS<!-- 1333708 -->

Det finns nu två alternativ när du skapar en ny VPN-profil för iOS: **Cisco AnyConnect** och **Cisco Legacy AnyConnect**. Cisco AnyConnect-profiler stöder 4.0.7x och nyare versioner. Befintliga iOS Cisco AnyConnect VPN-profiler är märkta **Cisco Legacy AnyConnect** och kommer fortsatt att fungera med Cisco AnyConnect 4.0.5x och äldre versioner som de gör i dag.

> [!NOTE]
> Den här ändringen gäller bara för iOS. Det finns fortfarande ett enda Cisco AnyConnect-alternativ för Android-, Android Enterprise-arbetsprofiler- och macOS-plattformar.


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132--1734567---"></a>Nya registreringssteg för användare på enheter med macOS High Sierra 10.13.2+<!--1734567 -->
I macOS High Sierra 10.13.2 finns nu begreppet ”Användargodkänd” MDM-registrering. Godkända registreringar tillåter Intune att hanterar vissa säkerhetskänsliga inställningar. Mer information finns i Apples supportdokumentation här: https://support.apple.com/HT208019.

Enheter som registreras med macOS-företagsportalen betraktas som ”Inte användargodkända” tills användaren öppnar systeminställningarna och ger sitt manuella godkännande. Därför dirigerar macOS-företagsportalen nu användare av macOS 10.13.2 och senare till att manuellt godkänna registreringen i slutet av registreringsprocessen. Intune-administratörskonsolen rapporterar om en registrerad enhet är användargodkänd.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune---2370684---"></a>Jamf-registrerade macOS-enheter kan nu registreras med Intune<!-- 2370684 -->
Version 1.3 och 1.4 av macOS-företagsportal registrerades inte Jamf-enheter med Intune korrekt. Version 1.4.2 av macOS-portalen åtgärdar det här problemet.

#### <a name="updated-help-experience-in-company-portal-app-for-android---1631531---"></a>Uppdaterad hjälpfunktion i företagsportalappen för Android<!-- 1631531 -->
Vi har uppdaterat hjälpfunktionen i Android-versionen av företagsportalappen och anpassat den till bästa praxis för Android-plattformen. När användarna stöter på ett problem i appen kan de nu trycka på **Menu (Meny)**  > **Help (Hjälp)** och:
- Skicka diagnostikloggar till Microsoft.
- Skicka ett e-postmeddelande som beskriver problemet och incident-ID till företagets supportavdelning.  

Om du vill kolla in den uppdaterade hjälpfunktionen går du till [Send logs using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) (Skicka loggar via e-post) och [Send errors to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (Skicka fel till Microsoft).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table---1471783---"></a>Nytt trenddiagram för registreringsfel och tabell över felorsaker<!-- 1471783 -->
På registreringsöversiktssidan kan du se trenden för registreringsfel och de fem viktigaste felorsakerna. Genom att klicka på diagrammet eller tabellen kan du gå in på detaljnivå för att hitta felsökningstips och åtgärdsförslag.


### <a name="device-management"></a>Enhetshantering

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated---1629303---"></a>Advanced Threat Protection (ATP) och Intune är helt integrerade<!-- 1629303 -->

[Avancerat skydd (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) visar risknivån för Windows 10-enheter. I Windows Defender Security Center (ATP-portal), kan du skapa en anslutning till Microsoft Intune. När du skapat anslutningen används en efterlevnadsprincip av Intune för att fastställa en godtagbar hotnivå. Om hotnivån överskrids kan sedan en villkorlig åtkomstprincip för Azure Active Directory (AD) blockera åtkomst till olika appar i din organisation.

Den här funktionen tillåter ATP att söka igenom filer, identifiera hot och rapportera eventuella risker på Windows 10-enheter.

Se [Aktivera ATP med villkorlig åtkomst i Intune](../protect/advanced-threat-protection.md).

#### <a name="support-for-user-less-devices---1637553---"></a>Stöd för användarlösa enheter<!-- 1637553 -->
Intune stöder möjligheten att utvärdera efterlevnaden på en användarlös enhet som exempelvis Microsoft Surface Hub. Policyer för efterlevnad kan riktas mot specifika enheter. Det innebär att efterlevnad (och inkompatibilitet) kan fastställas för enheter som inte har någon associerad användare.

#### <a name="delete-autopilot-devices---1713650---"></a>Ta bort Autopilot-enheter<!-- 1713650 -->
Intune-administratörer kan [ta bort AutoPilot-enheter](../enrollment/enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience--1832333---"></a>Förbättrad funktion för enhetsborttagning<!--1832333 -->
Du kommer inte längre behöva ta bort företagets data eller fabriksåterställa en enhet innan du [tar bort enheten från Intune](../remote-actions/devices-wipe.md#delete-devices-from-the-intune-portal).

Om du vill se den nya funktionen loggar du in på Intune och väljer **Enheter** > **Alla enheter** > namnet på enheten > **Ta bort**.

Om du fortfarande vill att rensningen ska utföras kan du använda standardenhetens livscykel med hjälp av **Ta bort företagsinformation** och **Fabriksåterställning** innan du väljer **Ta bort**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode---1947769---"></a>Spela upp ljud på iOS när enheten befinner sig i Borttappat läge<!-- 1947769 -->
När övervakade iOS-enheter är i hanteringen av mobilenheters (MDM) [Borttappat läge](../remote-actions/device-lost-mode.md), kan du [spela upp ett ljud](../remote-actions/device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Enheter** > **Alla enheter** > välj en iOS-enhet > **Översikt** > **Mer**). Ljudet fortsätter att spelas upp tills enheten tas bort från Borttappat läge, eller en användare stänger av ljudet. Gäller för iOS-enheter 9.3 och nyare.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device--1972804--"></a>Blockera eller tillåta webbresultat i sökningar som utförs på en Intune-enhet<!--1972804-->

Administratörer kan nu blockera webbresultat från sökningar gjorda på en enhet.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure---2172331---"></a>Förbättrade felmeddelanden när Apple MDM-pushcertifikat inte kan laddas upp<!-- 2172331 -->

Felmeddelandet förklarar att samma Apple-ID måste användas när du förnyar ett befintligt MDM-certifikat.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines---2216679---"></a>Testa företagsportalen för macOS på virtuella datorer<!-- 2216679 -->

Vi har publicerat vägledning som hjälper IT-administratörer testa företagsportalappen för macOS i Parallels Desktop och VMware Fusion. Du hittar mer information i avsnittet om att [registrera virtuella macOS-datorer för testning](../enrollment/macos-enroll.md#enroll-virtual-macos-machines-for-testing).

### <a name="intune-apps"></a>Intune-appar

#### <a name="user-experience-update-for-the-company-portal-app-for-ios--1412866---"></a>Uppdatering av användarupplevelsen för företagsportalappen för iOS<!--1412866 -->
Vi har släppt en större uppdatering av användarupplevelsen i företagsportalappen för iOS. Uppdateringen är en fullständig visuell omarbetning som ger appen en modernare design. Vi har bevarat appens funktionalitet men förbättrat användarvänligheten och tillgängligheten.  

Andra nyheter:
- Stöd för iPhone X.
- Snabbare appstart och inläsning som sparar tid för användarna.
- Fler förloppsindikatorer som ger användarna den senaste statusinformationen.
- Sättet att skicka loggar har förbättrats och det har blivit enklare att rapportera om något går fel.  

Gå till avsnittet om [nyheter i appgränssnittet](../whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca---1056954---"></a>Skydda lokala Exchange-data med hjälp av Intune APP och CA<!-- 1056954 -->
Du kan nu använda Intunes appskyddsprincip (APP) och villkorlig åtkomst (CA) för att skydda åtkomsten till lokala Exchange-data med Outlook Mobile. Om du vill lägga till eller ändra en appskyddsprincip i Azure Portal väljer du **Microsoft Intune** > **Klientappar** > **Appskyddsprinciper**. Innan du använder den här funktionen måste du se till att du uppfyller [kraven för Outlook för iOS och Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx).


### <a name="user-interface"></a>Användargränssnitt

#### <a name="improved-device-tiles-in-the-windows-10-company-portal--2213364---"></a>Förbättrade enhetspaneler i Windows 10-företagsportalen<!--2213364 -->

Panelerna har uppdaterats för att blir lättillgängligare för användare med sämre syn och för att fungera bättre tillsammans med skärmläsningsverktyg.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos---2216677---"></a>Skicka diagnostikrapporter i macOS-företagsportalappen<!-- 2216677 -->
Företagsportalappen för macOS-enheter har uppdaterats för att förbättra hur användarna rapporterar Intune-relaterade fel. Från företagsportalappen kan dina anställda:

- Ladda upp diagnostikrapporter direkt till Microsofts utvecklingsteam.
- E-posta ett incident-ID till ditt företags IT-supportteam.

Mer information finns i [Skicka fel till rätt personer för din hanterade macOS-enhet](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10---1195010---"></a>Intune anpassar sig efter Fluent Design System i Windows 10-företagsportalappen<!-- 1195010 -->
Intunes företagsportalapp för Windows 10 har uppdaterats med [Fluent Design-systemets navigeringsvy](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). Längs appen ser du en statisk, lodrät lista över alla sidor på översta nivån. Klicka på en länk för att snabbt visa och växla mellan sidor. Det här är den första av flera uppdateringar som visas som en del av vårt pågående arbete för att skapa en mer anpassningsbar, empatisk och bekant upplevelse i Intune. Gå till avsnittet om [nyheter i appgränssnittet](../whats-new-app-ui.md).

<!-- ########################## -->
## <a name="march-2018"></a>Mars 2018

### <a name="app-management"></a>Apphantering

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune---748789---"></a>Aviseringar om utgående verksamhetsspecifika appar i iOS för Microsoft Intune<!-- 748789 -->

Du får ett meddelande från Intune i Azure Portal om verksamhetsspecifika iOS-appar som snart förfaller. När du laddar upp en ny version av en verksamhetsspecifik iOS-app tar Intune bort förfalloaviseringen från applistan. Förfalloaviseringen är endast aktiv för nyligen överförda verksamhetsspecifika iOS-appar. En varning visas 30 dagar innan etableringsprofilen för den verksamhetsspecifika iOS-appen upphör att gälla. När den upphör ändras aviseringen till Upphört.

#### <a name="customize-your-company-portal-themes-with-hex-codes--1049561---"></a>Anpassa teman för företagsportalen med hexkoder<!--1049561 -->

Du kan anpassa temafärgen i företagsportalens appar med hexkoder. När du anger en hexkod kan Intune bestämma vilken textkod som ger den högsta kontrastnivån mellan textfärgen och bakgrundsfärgen. Du kan förhandsgranska både textfärgen och företagets logotyp mot färgen i **Klientappar** > **Företagsportal**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise---1813081---"></a>Inkludera och exkludera apptilldelning baserat på grupper för Android Enterprise<!-- 1813081 -->

Android Enterprise (tidigare Android for Work) stöder inkludering och exkludering av grupper, men stöder inte de inbyggda grupperna **Alla användare** och **Alla enheter**. Mer information finns i [Inkludera och exkludera apptilldelningar i Microsoft Intune](../apps/apps-inc-exl-assignments.md).


### <a name="device-management"></a>Enhetshantering

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome---2258071---"></a>Exportera alla enheter till CSV-filer i Internet Explorer, Microsoft Edge eller Chrome<!-- 2258071 -->
I **Enheter** > **Alla enheter** kan du **exportera** enheterna till en CSV-formaterad lista. Internet Explorer-användare med fler än 10 000 enheter kan exportera enheterna till flera filer. Varje fil kan ha upp till 10 000 enheter.

Microsoft Edge- och Chrome-användare med fler än 30 000 enheter kan exportera enheterna till flera filer. Varje fil kan ha upp till 30 000 enheter.

I [Hantera enheter](../remote-actions/device-management.md) finns mer information om vad du kan göra med de enheter som du hanterar.

#### <a name="new-security-enhancements-in-the-intune-service----1637539---"></a>Nya säkerhetsförbättringar i Intune-tjänsten <!-- 1637539 -->   

Vi har introducerat en växlingsknapp i Intune på Azure som de som använder fristående Intune kan använda för att hantera enheter utan tilldelad princip som **kompatibla** (säkerhetsfunktionen av) eller som **inte kompatibla** (säkerhetsfunktionen på). Detta gör att det endast går att komma åt resurser efter att enhetskompatibiliteten har utvärderats.

Den här funktionen påverkar dig på olika sätt beroende på om du redan har tilldelats policyer för efterlevnad eller inte.

- Om du har ett nytt eller befintligt konto och inte har några efterlevnadsprinciper tilldelade till enheterna ställs växlingsknappen automatiskt in på **kompatibel**. Funktionen är inaktiverad som standard i konsolen. Slutanvändaren påverkas inte.
- Om du har ett befintligt konto och har enheter med en tilldelad policy för efterlevnad är växlingsknappen automatiskt inställd på **inte kompatibel**. När marsuppdateringen distribueras är den här funktionen på som standard.

Om du använder policyer för efterlevnad med villkorlig åtkomst (CA) och funktionen är aktiverad blockeras nu eventuella enheter utan minst en tilldelad policy för efterlevnad av CA. Slutanvändarna som är kopplade till dessa enheter, och som tidigare kunde komma åt e-post, förlorar sin åtkomst om du inte tilldelar minst en policy för efterlevnad till alla enheter.   

Observera att även om standardväxlingsstatus visas direkt i användargränssnittet med marsuppdateringarna av Intune-tjänsten tillämpas inte växlingsstatusen omedelbart. Ändringarna du gör med växlingsknappen påverkar inte enhetsefterlevnaden förrän vi har förhandstestat ditt konto och du har en fungerande växling. Vi informerar dig via meddelandecentret när vi är klara med att förhandsversionstesta ditt konto. Detta kan ta upp till ett par dagar efter marsuppdateringarna av Intune-tjänsten.

**Ytterligare information**:[https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection---846515---"></a>Förbättrad upplåsningsidentifiering<!-- 846515 -->

Förbättrad upplåsningsidentifiering är en ny efterlevnadsinställning som förbättrar hur Intune utvärderar jailbreakade enheter. Inställningen gör att enheten checkar in till Intune oftare. Detta innebär att enhetens platstjänster används, vilket påverkar batterianvändningen.

#### <a name="reset-passwords-for-android-o-devices---1238299---"></a>Återställa lösenord för Android O-enheter<!-- 1238299 -->
Du kan återställa lösenorden för registrerade Android 8.0-enheter med arbetsprofiler. När du skickar en begäran om att återställa ett lösenord till en Android 8.0-enhet ställer den in ett nytt lösenord för upplåsning av enheten eller en hanterad profilutmaning för den aktuella användaren. Lösenordet eller kontrollfrågan skickas och träder i kraft omedelbart.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups--1307012---"></a>Ange enheter som mål för efterlevnadsprinciper i enhetsgrupper<!--1307012 -->

Du kan ange mål för efterlevnadsprinciper för användare i användargrupperna. Med den här uppdateringen kan du ange mål för efterlevnadsprinciper för enheter i användargrupper. Målenheter som ingår i enhetsgrupper får inte några efterlevnadsåtgärder.

#### <a name="new-management-name-column---1333586---"></a>Ny kolumn för hanteringsnamn<!-- 1333586 -->
 En ny kolumn med namnet **Hanteringsnamn** finns på enhetsbladet. Detta är ett automatiskt genererat, icke-redigerbart namn som tilldelas per enhet, baserat på följande formel:
- Standardnamn för alla enheter: <username><em><devicetype></em><enrollmenttimestamp>
- För masstillagda enheter: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

Det här är en valfri kolumn på enhetsbladet. Den är inte tillgänglig som standard och du har bara åtkomst till den via kolumnväljaren. Namnet på enheten påverkas inte av den här nya kolumnen.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes--1550837---"></a>iOS-enheter uppmanas att ange en PIN-kod var 15:e minut<!--1550837 -->
När en policy för efterlevnad eller konfiguration används på en iOS-enhet, uppmanas användarna att ange en PIN-kod var 15:e minut. Användarna uppmanas kontinuerligt tills en PIN-kod anges.

#### <a name="schedule-your-automatic-updates--1805514---"></a>Schemalägga automatiska uppdateringar<!--1805514 -->
Intune ger dig kontroll vid installation av automatiska uppdateringar med hjälp av [Inställningar för Windows 10-uppdateringsring](../protect/windows-update-for-business-configure.md). Med den här uppdateringen kan du schemalägga återkommande uppdateringar, inklusive vecka, dag och tid.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate--2221763---"></a>Använda ett fullständigt unikt namn som ämne för SCEP-certifikat<!--2221763 -->
När du skapar en profil för SCEP-certifikat, anger du certifikatets ämnesnamn. Med den här uppdateringen kan du använda det fullständiga unika namnet som ämne. För **Ämnesnamn** väljer du **Anpassad** och sedan `CN={{OnPrem_Distinguished_Name}}`. Om du vill använda variabeln `{{OnPrem_Distinguished_Name}}` måste du synkronisera användarattributet `onpremisesdistingishedname` med hjälp av [Azure Active Directory (AD) Anslut](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) till din Azure AD.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="enable-bluetooth-contact-sharing---android-for-work--1098983---"></a>Aktivera kontaktdelning med Bluetooth – Android for Work<!--1098983 -->
Som standard förhindrar Android att kontakter i arbetsprofilen synkroniseras med Bluetooth-enheter. Därför visas inte arbetsprofilkontakter i uppringarens ID för Bluetooth-enheter.

I och med uppdateringen finns en ny inställning i **Android for Work** > **Enhetsbegränsningar** > **Arbetsprofilinställningar**:
- Dela kontakter via Bluetooth

Intune-administratören kan konfigurera dessa inställningar för att aktivera delning. Detta är användbart när du parar ihop en enhet med en bilbaserad Bluetooth-enhet som visar uppringarens ID vid handsfree-användning. När den är aktiverad visas arbetsprofilens kontakter. När den är inaktiverad visas inte arbetsprofilens kontakter.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source---1690459---"></a>Konfigurera Gatekeeper för att styra nedladdningskälla för appar i macOS<!-- 1690459 -->

Du kan konfigurera Gatekeeper till att skydda dina enheter från appar genom att styra var apparna kan laddas ned från. Du kan konfigurera följande hämtningskällor: **Mac App Store**, **Mac App Store och identifierade utvecklare** eller **Var som helst**. Du kan även konfigurera om användarna ska kunna installera en app med CTRL-klick för att åsidosätta dessa Gatekeeper-kontroller.

Inställningarna finns i **Enhetskonfiguration** -> **Skapa profil** -> **macOS** -> **Slutpunktsskydd**.

#### <a name="configure-the-mac-application-firewall---1690461---"></a>Konfigurera programbrandväggen för Mac<!-- 1690461 -->

Du kan konfigurera brandväggen för Mac-program. Du kan använda den för att styra anslutningar per program i stället för per port. Det gör det lättare att utnyttja brandväggsskyddet och förhindrar att oönskade appar tar kontroll över nätverksportar som är öppna för legitima appar.

Den här funktionen finns i **Enhetskonfiguration** -> **Skapa profil** -> **macOS** -> **Slutpunktsskydd**.

När du har aktiverat brandväggsinställningen kan du konfigurera brandväggen med hjälp av två olika metoder:

- Blockera alla inkommande anslutningar

   Du kan blockera alla inkommande anslutningar för de aktuella enheterna. Om du väljer att göra detta blockeras inkommande anslutningar för alla appar.

- Tillåta eller blockera specifika appar

   Du kan tillåta eller blockera specifika appar från att ta emot inkommande anslutningar. Du kan också aktivera hemligt läge för att förhindra svar på avsökningsbegäranden.

#### <a name="detailed-error-codes-and-messages---1376342---"></a>Detaljerade felkoder och meddelanden<!-- 1376342 -->

I din enhetskonfiguration finns mer detaljerade felkoder och felmeddelanden. Den här förbättrade rapporteringen visar inställningarna, status för dessa inställningar och information om felsökning.

##### <a name="more-information"></a>Mer information

- Blockera alla inkommande anslutningar

   Detta hindrar alla delade tjänster (till exempel fildelning och delning av skärmen) från att ta emot inkommande anslutningar. Systemtjänster som fortfarande kan ta emot inkommande anslutningar är:
  - configd – Implementerar DHCP- och andra tjänster för nätverkskonfiguration
  - mDNSResponder – Implementerar Bonjour
  - racoon – implementerar IPSec

    Om du vill använda delade tjänster kontrollerar du att **Inkommande anslutningar** är inställd på **Inte konfigurerad** (inte **Blockera**).

- Hemligt läge

   Aktivera detta om du vill förhindra att datorn svarar på avsökningsbegäranden. Datorn svarar fortfarande på inkommande begäranden för behöriga appar. Oväntade begäranden, till exempel ICMP (ping) ignoreras.

#### <a name="disable-checks-on-device-restart--1805490---"></a>Inaktivera kontroller vid omstart av enheten<!--1805490 -->
Med Intune kan du styra [hanteringen av programuppdateringar](../protect/windows-update-for-business-configure.md). Med den här uppdateringen är egenskapen <strong>Omstartskontroller</strong> tillgänglig och aktiverad som standard. Om du vill hoppa över de vanliga kontroller som utförs när du startar om en enhet (till exempel aktiva användare, batterinivå och så vidare) väljer du <strong>Hoppa över</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings---1746293---"></a>Nya Windows 10 Insider Preview-kanaler är tillgängliga för testgrupper för distribution<!-- 1746293 -->
Nu kan du välja följande Windows 10 Insider Preview-underhållskanaler när du skapar en Windows 10-testgrupp för distribution:
- Windows Insider-version &#8208; snabb
- Windows Insider-version &#8208; långsam
- Windows Insider-slutversion 

Mer information om dessa kanaler finns [Manage Insider Preview Builds](https://insider.windows.com/for-business-organization-admin/) (Hantera Insider Preview-versioner).   
Mer information om hur du skapar distributionskanaler i Intune finns i [Hantera programuppdateringar](../protect/windows-update-for-business-configure.md).

### <a name="new-windows-defender-exploit-guard-settings---1631893---"></a>Nya inställningar för Windows Defender Exploit Guard<!-- 1631893 -->

Sex nya inställningar för <strong>minskning av attackytan</strong> och utökade funktioner för <strong>reglerad mappåtkomst: Det finns nu funktioner för mappskydd</strong> tillgängliga. De här inställningarna finns på: Device configuration\Profiles\
Create profile\Endpoint protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Minska attackytan

|Inställningsnamn  |Inställningsalternativ  |Beskrivning  |
|---------|---------|---------|
|Avancerat skydd för utpressningstrojan|Aktiverad, granskad, inte konfigurerad|Använd aggressivt skydd mot utpressningstrojan.|
|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem|Aktiverad, granskad, inte konfigurerad|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem (lsass.exe).|
|Skapa process från PSExec- och WMI-kommandon|Blockera, Granska, Inte konfigurerat|Blockera skapande av processer från PSExec- och WMI-kommandon.|
|Obetrodda och osignerade processer som körs via USB|Blockera, Granska, Inte konfigurerat|Blockera obetrodda och osignerade processer som körs via USB.|
|Körbara filer som inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista|Blockera, Granska, Inte konfigurerat|Blockera körbara filer från att köras om de inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista.|

#### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

|              Inställningsnamn               |                                                              Inställningsalternativ                                                              | Beskrivning |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Mappskydd (redan implementerat) | Inte konfigurerad, Aktivera, Endast granskning (redan implementerat)<br><br> <strong>Nytt</strong><br>Blockera diskändring, Granska diskändring |             |

Skydda filer och mappar från obehöriga ändringar av oönskade appar.<br><br>**Aktivera**: Förhindra att obetrodda appar ändrar eller tar bort filer i skyddade mappar och skriver till disksektorer.<br><br>
**Blockera endast diskändring**:<br>Blockera obetrodda appar från att skriva till disksektorer. Obetrodda appar kan fortfarande ändra eller ta bort filer i skyddade mappar.|

### <a name="intune-apps"></a>Intune-appar

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview---710595---"></a>Azure Active Directory-webbplatser kan kräva appen Intune Managed Browser och ha stöd för enkel inloggning för Managed Browser (allmänt tillgänglig förhandsversion)<!-- 710595 -->

Med Azure Active Directory (Azure AD) kan du nu begränsa åtkomsten till webbplatser på mobila enheter till appen Intune Managed Browser. I Managed Browser förblir webbplatsdata säkra och separata från slutanvändarens personliga data. Dessutom stöder Managed Browser funktioner för enkel inloggning för webbplatser som stöds av Azure AD. När du loggar in på Managed Browser eller använder Managed Browser på en enhet med en annan app som hanteras av Intune, tillåts Managed Browser att få åtkomst till företagswebbplatser som skyddas av Azure AD utan att användaren måste ange sina autentiseringsuppgifter. Den här funktionen gäller för webbplatser som Outlook Web Access (OWA) och SharePoint Online, samt andra företags webbplatser som resurser i intranätet som nås via Azure App Proxy. Mer information finns i avsnittet om [åtkomstkontroller för villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates--976944---"></a>Visuella uppdateringar i företagsportalappen för Android<!--976944 -->

Vi har uppdaterat företagsportalappen för Android så att den följer Androids riktlinjer för [Materialdesign](https://material.io/). Du kan se bilder av de nya ikonerna i artikeln [Nyheter i appens gränssnitt](../whats-new-app-ui.md).

#### <a name="company-portal-enrollment-improved---1874230-eeready--"></a>Registrering i företagsportalen har förbättrats<!-- 1874230 eeready-->
Användare som registrerar en enhet med hjälp av företagsportalen i Windows 10 version 1703 och senare, kan slutföra det första steget i registreringen utan att lämna appen.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists--1725868---"></a>HoloLens och Surface Hub visas nu i enhetslistor<!--1725868 -->
Vi har lagt till stöd för att visa Intune-registrerade HoloLens- och Surface Hub-enheter i företagsportalappen för Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks---1488911---"></a>Anpassade bokkategorier för VPP-e-böcker (volyminköpsprogram)<!-- 1488911 -->
Du kan skapa anpassade e-bokkategorier och sedan tilldela e-böcker i volyminköpsprogram till dessa anpassade e-bokkategorier. Slutanvändarna kan sedan se de nyligen skapade e-bokkategorierna och böcker som tilldelats i kategorierna. Mer information finns i [Hantera volyminköpta appar och böcker med Microsoft Intune](../apps/vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option---2070166---"></a>Ändringar i stödet för alternativet att skicka feedback i företagsportalappen för Windows<!-- 2070166 -->
Med start den 30 april 2018, kommer alternativet **Skicka feedback** i företagsportalappen för Windows bara att fungera på enheter som kör Windows 10 Anniversary-uppdateringen (1607) och senare. Alternativet att skicka feedback stöds inte längre när du använder företagsportalappen för Windows med:  
- Windows 10, version 1507  
- Windows 10, version 1511  
- Windows Phone 8.1 

Om enheten körs på Windows 10 RS1 eller senare, kan du hämta den senaste versionen av Windows-företagsportalappen från Store. Om du kör en version som inte stöds, fortsätt att skicka feedback via följande kanaler: 
- Feedbackhubben i Windows 10
- E-post WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings---1631890---"></a>Nya Windows Defender Application Guard-inställningar<!-- 1631890 -->

- **Aktivera grafikacceleration**: Administratörer kan aktivera en virtuell grafikprocessor för Windows Defender Application Guard. Med den här inställningen kan processorn avlasta grafikåtergivning till vGPU. Detta kan förbättra prestanda när du arbetar med grafikintensiva webbplatser eller tittar på videor inuti containern.

- **SaveFilestoHost**: Administratörer kan aktivera att filer skickas från Microsoft Edge som körs i containern till värdfilsystemet. Det gör att användare kan ladda ned filer från Microsoft Edge i containern till värdfilsystemet.

#### <a name="mam-protection-policies-targeted-based-on-management-state---1665993---"></a>MAM-skyddsprinciper riktas utifrån hanteringsstatus<!-- 1665993 -->
Du kan rikta MAM-principer baserat på hanteringsstatus för enheten:
- **Android-enheter** – Du kan ange ohanterade enheter, Intune-hanterade enheter och Intune-hanterade Android Enterprise-profiler (tidigare Android for Work) som mål.
- **iOS-enheter** – Du kan ange ohanterade enheter (endast MAM) eller Intune-hanterade enheter som mål.

    > [!NOTE]
    > - iOS-stöd för den här funktionen införs i april 2018.

Mer information finns i [Target app protection policies based on device management state](../apps/app-protection-policies.md) (Ange mål för appskyddsprinciper utifrån enhetens hanteringsstatus).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows---1683758---"></a>Språkförbättringar i företagsportalappen för Windows<!-- 1683758 -->
Vi har förbättrat språket i företagsportalen för att Windows 10 ska vara mer användarvänligt och specifikt för ditt företag. Du kan se några bildexempel på sidan om [nyheter i appens gränssnitt](../whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy---1440709---"></a>Nya tillägg till vår dokumentation om användarsekretess<!-- 1440709 -->
Som en del i vårt arbete att ge användarna mer kontroll över sina data och sin sekretess har vi publicerat uppdateringar i vår dokumentation som förklarar hur du visar och tar bort data som lagras lokalt av företagsportalappar. Du hittar uppdateringarna på:

- **Android**: [Så här tar du bort en Android-enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android, om användaren har avvisat användningsvillkoren**: [Ta bort enhetshanteringen om du inte godkände våra ”Användningsvillkor”](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS**: [Ta bort din iOS-enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows**: [Ta bort din Windows-enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>Februari 2018

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685---"></a>Intune-stöd för flera Apple DEP-/Apple School Manager-konton<!-- 747685 -->

Intune stöder nu registrering av enheter från upp till 100 olika [Apple-program för enhetsregistrering (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) eller [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md)-konton. Varje token som har överförts kan hanteras separat för registreringsprofiler och- enheter. En annan profil kan tilldelas automatiskt per DEP/School Manager-token som har överförts. Om flera School Manager-token har överförs, kan bara en åt gången delas med Microsoft School-datasynkronisering.

Efter migreringen fungerar inte beta-Graph API:er och publicerade skript för att hantera Apple DEP eller ASM över Graph längre. Nya beta-Graph API:er är under utveckling och kommer att släppas efter migreringen.

#### <a name="see-enrollment-restrictions-per-user---1634444-eeready-wnready---"></a>Visa registreringsbegränsningar per användare<!-- 1634444 eeready wnready -->
På bladet **Felsök** kan du nu se de [registreringsbegränsningar](../enrollment/enrollment-restrictions-set.md) som gäller för varje användare genom att välja **Registreringsbegränsningar** i listan **Tilldelningar**.

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment---747625-eeready---"></a>Nya alternativ för användarautentisering för Apple-massregistrering<!-- 747625 eeready -->

> [!NOTE]
> Nya klienter ser det här direkt. Den här funktionen distribueras under april för befintliga klienter. Du kanske inte har åtkomst till de här nya funktionerna förrän den här distributionen är slutförd.

Intune ger dig nu möjlighet att autentisera enheter med hjälp av företagsportalappen för följande registreringsmetoder:

- Apples DEP (Device Enrollment Program)
- Apple School Manager
- Registrera Apple Configurator

När du använder alternativet Företagsportalen, kan Azure Active Directory-multifaktorautentisering tillämpas utan att blockera dessa registreringsmetoder.

När du använder alternativet Företagsportalen, hoppar Intune över användarautentisering i iOS-installationsassistenten för registrering av användartillhörighet. Detta innebär att enheten först registreras som en användarlös enhet och därför inte tar emot konfigurationer eller principer från användargrupper. Den tar bara emot konfigurationer och principer för enhetsgrupper. Intune kommer dock automatiskt att installera företagsportalappen på enheten. Den första användaren som startar och loggar in på företagsportalappen kommer att associeras med enheten i Intune. Användaren får då konfigurationer och principer för sina användargrupper. Användarassociationen kan inte ändras utan omregistrering.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685-eeready---"></a>Intune-stöd för flera Apple DEP-/Apple School Manager-konton<!-- 747685 eeready -->

Intune stöder nu registrering av enheter från upp till 100 olika Apple-program för enhetsregistrering (DEP) eller Apple School Manager-konton. Varje token som har överförts kan hanteras separat för registreringsprofiler och- enheter. En annan profil kan tilldelas automatiskt per DEP/School Manager-token som har överförts. Om flera School Manager-token har överförs, kan bara en åt gången delas med Microsoft School-datasynkronisering.

Efter migreringen fungerar inte beta-Graph API:er och publicerade skript för att hantera Apple DEP eller ASM över Graph längre. Nya beta-Graph API:er är under utveckling och kommer att släppas efter migreringen.

### <a name="remote-printing-over-a-secure-network---1709994----"></a>Fjärrutskrift via ett säkert nätverk<!-- 1709994  -->
PrinterOn:s trådlösa mobila lösningar gör att användare via fjärranslutning kan skriva ut var och när som helst via ett säkert nätverk. PrinterOn kan integreras med Intune APP SDK för både iOS och Android. Du kommer att kunna ange mål för appskyddsprinciper för den här appen via bladet Intune **Appskyddsprinciper** i administrationskonsolen. Användarna kommer att kunna ladda ner appen PrinterOn for Microsoft via Play Store eller iTunes för att använda i sina Intune-ekosystem.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager---1352411---"></a>Stöd i macOS-företagsportalen för registreringar som använder enhetsregistreringshanteraren<!-- 1352411 -->

Användarna kan nu använda enhetsregistreringshanteraren när de registrerar sig i macOS-företagsportalen.

### <a name="device-management"></a>Enhetshantering

#### <a name="windows-defender-health-status-and-threat-status-reports--854704---"></a>Rapporter om hälsostatus och hotstatus i Windows Defender<!--854704 -->

Det är viktigt att förstå Windows Defenders hälsa och status för att hantera Windows-datorer.  Med denna uppdatering lägger Intune till nya rapporter och åtgärder till Windows Defender-agentens status och hälsa. Med hjälp av en statussammanfattningsrapport i [arbetsbelastningen för enhetsefterlevnad](../protect/compliance-policy-monitor.md) kan du se de enheter som behöver något av följande:
- signaturuppdatering
- Starta om
- manuella åtgärder
- fullständig genomsökning
- övriga agenttillstånd som kräver åtgärder

En detaljerad rapport för varje statuskategori visar de enskilda datorer som behöver åtgärdas eller vilka som rapporteras som **Rengör**.

#### <a name="new-privacy-settings-for-device-restrictions--1308926---"></a>Nya sekretessinställningar för enhetsbegränsningar<!--1308926 -->
[Två nya sekretessinställningar](../configuration/device-restrictions-windows-10.md#privacy) är nu tillgängliga för enheter:
- **Publicera användaraktiviteter**: Ställ in den här på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen.
- **Endast lokala aktiviteter**: Ställ in det här alternativet på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen baserat på lokala aktiviteter.

#### <a name="new-settings-for-the-microsoft-edge-browser--1469166---"></a>Nya inställningar för webbläsaren Microsoft Edge<!--1469166 -->
Det finns nu [två nya inställningar](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser) tillgängliga för enheter med Microsoft Edge-webbläsaren: **Sökväg till favoritfil** och **Ändringar i favoriter**.

### <a name="app-management"></a>Apphantering

#### <a name="protocol-exceptions-for-applications--1035509---"></a>Protokollundantag för program<!--1035509 -->

Du kan nu skapa undantag till principen för MAM-dataöverföring (Mobile Application Management) i Intune för att kunna öppna vissa ohanterade program. Sådana program måste vara betrodda av IT-avdelningen. Utöver de undantag som du skapar är dataöverföringen ändå begränsad till program som hanteras av Intune när din dataöverföringsprincip är inställd på **Endast hanterade appar**. Du kan skapa begränsningarna med protokoll (iOS) eller paket (Android).

Du kan exempelvis lägga till Webex-paketet som ett undantag till MAM-dataöverföringsprincipen. Det innebär att Webex-länkar i ett hanterat e-postmeddelande i Outlook kan öppnas direkt i Webex-programmet. Dataöverföringen är fortfarande begränsad i andra ohanterade program. Mer information finns i [Undantag för dataöverföringsprinciper i appar](../apps/app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results---1469193---"></a>Windows Information Protection (WIP)-krypterad data i Windows-sökresultat<!-- 1469193 -->
En inställning i principen för Windows informationsskydd innebär att du nu kan kontrollera om krypterade data i Windows informationsskydd ingår i Windows-sökresultaten. Ange den här appens skyddsprincipalternativ genom att välja **Tillåt att Windows Search-indexeraren söker efter krypterade objekt**  i **Avancerade inställningar** för Windows informationsskyddsprincip. Appens skyddsprincip måste anges för *Windows 10*-plattformen och apprincipen **Registreringsstatus** måste anges som **Med registrering**. Mer information finns i [Tillåt att Windows Search-indexeraren söker efter krypterade objekt](../apps/windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app---1740840---"></a>Konfigurera en MSI-mobilapp med automatisk uppdatering<!-- 1740840 -->
Du kan konfigurera att en känd MSI-mobilapp med automatisk uppdatering ignorerar versionskontrollen. Den här funktionen är användbar för att undvika konkurrenstillstånd. Den här typen av konkurrenstillstånd kan exempelvis uppstå när appen uppdateras automatiskt av apputvecklaren och även uppdateras av Intune. Båda två kan försöka framtvinga en version av appen på Windows-klienten, vilket kan skapa en konflikt. För dessa automatiskt uppdaterade MSI-appar kan du konfigurera inställningen **Ignorera appversion** på bladet **Appinformation**. När den här inställningen växlas till **Ja** kommer Microsoft Intune ignorera den appversion som är installerad på Windows-klienten.

#### <a name="related-sets-of-app-licenses-supported-in-intune---1864117---"></a>Relaterade uppsättningar med applicenser stöds i Intune<!-- 1864117 -->
Intune i Azure-portalen stöder nu relaterade uppsättningar med applicenser som ett enskilt appobjekt i användargränssnittet. Dessutom konsolideras alla offlinelicensierade appar från Microsoft Store för företag till en enda appinmatning och eventuella distributionsuppgifter från de enskilda paketen migreras över till den enda inmatningen. Om du vill se relaterade uppsättningar applicenser i Azure-portalen väljer du **Applicenser** på bladet **Klientappar**.

### <a name="device-configuration"></a>Enhetskonfiguration
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption---1463582---"></a>WIP-filnamnstillägg (Windows Information Protection) för automatisk kryptering<!-- 1463582 -->
Med en inställning i principen för Windows informationsskydd kan du nu ange vilka filnamnstillägg som krypteras automatiskt vid kopiering från en SMB-resurs (Server Message Block) inom företagets gräns som definierats i Windows informationsskyddsprincip.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Konfigurera resursens kontoinställningar för Surface Hub

Du kan nu fjärrkonfigurera resurskontoinställningar för Surface Hub.

Resurskontot används av en Surface Hub för att autentisera med Skype/Exchange så att den kan ansluta till ett möte.
Du kan skapa ett unikt resurskonto så att Surface Hub visas i mötet som konferensrummet.
Resurskontot kan till exempel visas som **konferensrum B41/6233**.

> [!NOTE]
> - Om du låter fält vara tomma åsidosätter du tidigare konfigurerade attribut på enheten.
>
> - Egenskaper för resurskonto kan ändras dynamiskt på Surface Hub. Exempelvis om lösenordsrotation är på. Det är alltså möjligt att värdena i Azure-konsolen tar lite tid på sig att återspegla enhetens verklighet.
>
>   För att förstå vad som för närvarande konfigureras på Surface Hub kan resurskontoinformationen inkluderas i maskinvaruinventeringen (som redan har en intervall på 7 dagar) eller som skrivskyddade egenskaper. För att förbättra noggrannheten när en fjärråtgärd har vidtagits kan du genast hämta parametrarnas tillstånd när du har kört åtgärden för att uppdatera kontot/parametrarna på Surface Hub.

##### <a name="attack-surface-reduction"></a>Minska attackytan

|Inställningsnamn  |Inställningsalternativ  |Beskrivning  |
|---------|---------|---------|
|Körning av lösenordsskyddat körbart innehåll från e-post|Blockera, Granska, Inte konfigurerat|Förhindra körning av körbara filer som skyddas av lösenord och som hämtats via e-post.|
|Avancerat skydd för utpressningstrojan|Aktiverad, granskad, inte konfigurerad|Använd aggressivt skydd mot utpressningstrojan.|
|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem|Aktiverad, granskad, inte konfigurerad|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem (lsass.exe).|
|Skapa process från PSExec- och WMI-kommandon|Blockera, Granska, Inte konfigurerat|Blockera skapande av processer från PSExec- och WMI-kommandon.|
|Obetrodda och osignerade processer som körs via USB|Blockera, Granska, Inte konfigurerat|Blockera obetrodda och osignerade processer som körs via USB.|
|Körbara filer som inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista|Blockera, Granska, Inte konfigurerat|Blockera körbara filer från att köras om de inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista.|

##### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

|              Inställningsnamn               |                                                              Inställningsalternativ                                                              | Beskrivning |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Mappskydd (redan implementerat) | Inte konfigurerad, Aktivera, Endast granskning (redan implementerat)<br><br> <strong>Nytt</strong><br>Blockera diskändring, Granska diskändring |             |

Skydda filer och mappar från obehöriga ändringar av oönskade appar.<br><br>**Aktivera**: Förhindra att obetrodda appar ändrar eller tar bort filer i skyddade mappar och skriver till disksektorer.<br><br>
**Blockera endast diskändring**:<br>Blockera obetrodda appar från att skriva till disksektorer. Obetrodda appar kan fortfarande ändra eller ta bort filer i skyddade mappar.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies--1704133--"></a>Tillägg till efterlevnadsprinciper för systemsäkerhetsinställningar för Windows 10 och senare<!--1704133-->

Tillägg till efterlevnadsinställningar för Windows 10 är nu tillgängliga, däribland krav på brandvägg och Windows Defender Antivirus.

### <a name="intune-apps"></a>Intune-appar

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business--1222672--"></a>Stöd för offline-appar från Microsoft Store för företag<!--1222672-->
Offline-appar som du har köpt från Microsoft Store för företag synkroniseras nu med Azure-portalen. Du kan distribuera apparna till enhetsgrupper eller användargrupper. Offline-appar installeras av Intune och inte av butiken.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile---1728700---"></a>Förhindra slutanvändare från att lägga till eller ta bort konton manuellt i arbetsprofilen<!-- 1728700 -->

När du distribuerar Gmail-appen till en Android for Work-profil kan du nu förhindra att användare lägger till eller tar bort konton i arbetsprofilen manuellt genom att använda inställningen **Lägg till och ta bort konton** i profilen för enhetsbegränsningar i Android for Work.

<!-- ########################## -->
## <a name="january-2018"></a>Januari 2018

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire---1639263---"></a>Aviseringar om upphörda token och om token som snart upphör<!-- 1639263 -->
På översiktssidan visas nu aviseringar om att token har upphört att gälla och om att token snart upphör att gälla. När du klickar på en avisering för en enskild token fortsätter du till denna tokens informationssida.  Om du klickar på avisering för flera token kommer du till en lista över alla token med deras status. Administratörer bör förnya sina tokens innan förfallodatumet.

### <a name="device-management"></a>Enhetshantering

#### <a name="remote-erase-command-support-for-macos-devices---1438084---"></a>Stöd för fjärrkommandot ”Radera” för macOS-enheter<!-- 1438084 -->

Administratörer kan utfärda ett Radera-kommando via fjärranslutning för macOS-enheter.

> [!IMPORTANT]
> Raderingskommandot kan inte ångras och bör användas med försiktighet.

Raderingskommandot tar bort alla data, inklusive operativsystemet från en enhet. Det tar också bort enheten från Intune-hantering. Ingen varning utfärdas till användaren och raderingen sker omedelbart efter kommandot.

Du måste konfigurera en 6-siffrig PIN-kod för återställning. Den här PIN-kod kan användas för att låsa upp enheten som raderats, då ominstallation av operativsystemet börjar. När raderingen har startats visas PIN-koden i ett statusfält på enhetens översiktsblad i Intune. PIN-koden kommer att finnas kvar så länge raderingen pågår. När raderingen är klar försvinner enheten helt från Intune-hanteringen. Tänk på att notera PIN-koden så att den som återställer enheten kan använda den.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token---820870---"></a>Återkalla licenser för en token för iOS-volyminköpsprogram<!-- 820870 -->
Du kan återkalla licensen för alla iOS-appar för volyminköpsprogram (VPP) för en given VPP-Token.

### <a name="app-management"></a>Apphantering

#### <a name="revoking-ios-volume-purchase-program-apps----820863---"></a>Återkalla iOS-appar från volyminköpsprogram <!-- 820863 -->
Du kan återkalla associerade enhetsbaserade applicenser för enheten för en given enhet som har en eller flera iOS-appar för volyminköpsprogram (VPP). Om du återkallar en applicens så avinstalleras inte den relaterade VPP-appen från enheten. Om du vill avinstallera en VPP-app, måste du ändra tilldelningsåtgärden till **avinstallera**. Mer information finns i [så här hanterar du iOS-appar som köpts genom ett volyminköpsprogram med Microsoft Intune](../apps/vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type---1332318---"></a>Tilldela Office 365-mobilappar till iOS- och Android-enheter med hjälp av inbyggd apptyp<!-- 1332318 -->
Den **inbyggda** apptypen gör det enklare att skapa och tilldela Office 365-appar till iOS- och Android-enheter som du hanterar. De här apparna inkluderar 365-appar som Word, Excel, PowerPoint och OneDrive. Du kan tilldela specifika appar till apptypen och redigera konfigurationen för appinformationen.

#### <a name="including-and-excluding-app-assignment-based-on-groups---1406920---"></a>Inkludera och exkludera apptilldelning baserat på grupper<!-- 1406920 -->

Under apptilldelning och när du har valt en tilldelningstyp kan du välja de grupper som ska inkluderas, samt de grupper som ska undantas.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments----1480316---"></a>Du kan tilldela en programkonfigurationsprincip till grupper genom att inkludera och exkludera tilldelningar <!-- 1480316 -->

Du kan tilldela en programkonfigurationsprincip till en grupp användare och enheter genom att använda en kombination av tilldelningar som inkluderar och exkluderar. Tilldelningar kan väljas som ett anpassat urval av grupper eller som en virtuell grupp. En virtuell grupp kan inkludera **Alla användare**, **Alla enheter** eller **Alla användare + Alla enheter**.

#### <a name="support-for-windows-10-edition-upgrade-policy-----903672archived-1119689---"></a>Stöd för uppgraderingsprincip i Windows 10-utgåva  <!-- 903672(archived), 1119689 -->  
Du kan skapa en uppgraderingsprincip för Windows 10-utgåvan som uppgraderar Windows 10-enheter till Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education och Windows 10 Professional Education N. Mer information om Windows 10-uppgraderingar finns i [Så här konfigurerar du Windows 10-uppgraderingar](../configuration/edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal----1737088-1634311---"></a>Principer för villkorlig åtkomst för Intune är endast tillgängliga från Azure-portalen <!-- 1737088 1634311 -->

Från och med den här versionen måste du konfigurera och hantera dina principer för villkorlig åtkomst på [Azure Portal](https://portal.azure.com) från **Azure Active Directory** > **Villkorlig åtkomst**. Du kan även komma åt det här bladet från Intune på Azure Portal på **Intune** > **Villkorlig åtkomst**.

#### <a name="updates-to-compliance-emails--1637547---"></a>Uppdateringar av e-postmeddelande för efterlevnad<!--1637547 -->

När ett e-postmeddelande skickas för att rapportera om en inkompatibel enhet inkluderas även information om den inkompatibla enheten.

### <a name="intune-apps"></a>Intune-appar

#### <a name="new-functionality-for-the-resolve-action-for-android-devices--1583480--"></a>Ny funktion för åtgärden ”Lös” för Android-enheter<!--1583480-->

Företagsportalappen för Android utökar ”Lös”-åtgärden för **Uppdatera enhetsinställningar** för att lösa [device encryption issues](/intune-user-help/encrypt-your-device-android) (problem med enhetskryptering).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10--676506--"></a>Fjärrlås är tillgängligt i företagsportalappen för Windows 10<!--676506-->
Slutanvändare kan nu fjärrlåsa sina enheter från företagsportalappen för Windows 10. Detta visas inte för den lokala enheten som används.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10--676546--"></a>Enklare lösning av efterlevnadsproblem för företagsportalappen för Windows 10<!--676546-->
Slutanvändare med Windows-enheter kan trycka på orsaken för bristande efterlevnad i företagsportalappen. Om möjligt kommer de då direkt till rätt plats i inställningsappen för att kunna åtgärda problemet.

<!-- ########################## -->
## <a name="december-2017"></a>December 2017

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="new-automatic-redeployment-setting---1469168---"></a>Ny inställning för automatisk omdistribution<!-- 1469168 -->
Inställningen **Automatisk omdistribution** låter användare med administrativ behörighet ta bort alla användardata och inställningar med hjälp av **Ctrl + Win + R** på enhetens låsskärm. Enheten omkonfigureras automatiskt och omregistreras för hantering. Den här inställningen finns under Windows 10 > Enhetsbegränsningar > Allmänt -> Automatisk omdistribution. Mer information finns i [Inställningar för begränsningar i Intune-enheter för Windows 10](../configuration/device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy----903672--1119689---"></a>Stöd för ytterligare källutgåvor i uppgraderingsprincipen för Windows 10-utgåva <!-- 903672,  1119689 -->
Du kan nu använda uppgraderingsprincipen för Windows 10 för att uppgradera från ytterligare Windows 10-versioner (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud, o.s.v.). Innan den här versionen var de uppgraderingsvägar som stöddes för utgåvan mer begränsade. Du hittar mer information i [Så här konfigurerar du uppgraderingar av Windows 10](../configuration/edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings---1335507---"></a>Nya profilinställningar för enhetskonfiguration för Windows Defender Security Center (WDSC)<!-- 1335507 -->

Intune lägger till ett nytt avsnitt med profilinställningar för enhetskonfiguration under Endpoint Protection som heter **Windows Defender Security Center**. IT-administratörer kan konfigurera vilka pelare i Windows Defender Security Center-appen som slutanvändare kan komma åt. Om IT-administratör döljer en pelare i Windows Defender Security Center-appen, döljs alla meddelanden som rör den dolda pelare på användarens enhet.

Dessa är de pelare som administratörer kan dölja från profilinställningarna för enhetskonfiguration för Windows Defender Security Center:
- Skydd mot virus och hot
- Enhetsprestanda och hälsa
- Brandväggs- och nätverksskydd
- App- och webbläsarkontroll
- Familjealternativ

IT-administratörer kan också anpassa de meddelanden som användare tar emot. Du kan till exempel konfigurera om användarna får alla meddelanden som skapas av synliga pelare i WDSC, eller enbart viktiga meddelanden. Meddelanden som är mindre viktiga inkluderar periodiska sammanfattningar av Windows Defender Antivirus-aktivitet och meddelanden när genomsökningar har slutförts. Alla andra meddelanden anses viktiga. Dessutom kan du kan också anpassa själva meddelandeinnehållet, du kan till exempel ange IT-kontaktinformation att bädda in i meddelanden som visas på användarnas enheter.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling---1361755---"></a>Stöd för flera anslutningsappar för hantering av SCEP- och PFX-certifikat<!-- 1361755 -->

Kunder som använder den lokala NDES-anslutningsappen för att leverera certifikat till enheter kan nu konfigurera flera anslutningsappar i en enda klient.

Den här nya funktionen stöder följande scenarion:

- **Hög tillgänglighet**

Varje NDES-anslutningsapp tar emot certifikatbegäranden från Intune.  Om en NDES-anslutningsapp kopplas från, kan den andra anslutningsappen fortsätta att bearbeta begäranden.

#### <a name="customer-subject-name-can-use-aad_device_id-variable----1468599---"></a>Ämnesnamnet för kunden kan använda variabeln AAD_DEVICE_ID <!-- 1468599 -->

När du skapar en profil för SCEP-certifikatet i Intune kan du nu använda variabeln AAD_DEVICE_ID när du skapar det anpassade ämnesnamnet.   När certifikatet har begärts med hjälp av den här SCEP-profilen, ersätts variabeln med ADD-enhetens ID för den enhet som gör certifikatbegäran.


### <a name="device-management"></a>Enhetshantering

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747---"></a>Hantera Jamf-registrerade macOS-enheter med Intunes motor för enhetsefterlevnad<!-- 1592747 -->
Du kan nu använda Jamf statusinformation för macOS-enheter till Intune, som sedan utvärderar den för efterlevnad av de principer som definierats i Intune-konsolen. Baserat på enhetens efterlevnadsstatus samt andra villkor (till exempel plats, användarrisk osv.), framtvingar villkorsstyrd åtkomst efterlevnad för macOS-enheter som har åtkomst till molnet och lokala program som är anslutna till Azure AD, inklusive Office 365. Lär dig mer om att [ställa in Jamf-integration](../protect/conditional-access-integrate-jamf.md) och [tillämpa kompatibilitet för enheter som hanteras av Jamf](../protect/conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action-----1424701---"></a>Ny iOS-enhetsåtgärd  <!-- 1424701 -->

Du kan nu stänga av iOS 10.3-övervakade enheter. Den här åtgärden stänger av enheten omedelbart utan varning till slutanvändaren. Åtgärden **stäng ner (endast övervakat)** finns i enhetsegenskaperna när du väljer en enhet i arbetsbelastningen **enhet**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices---1468103---"></a>Förbjuda ändringar av datum/tid för Samsung Knox-enheter<!-- 1468103 -->

Vi har lagt till en ny funktion som gör det möjligt att blockera datum- och tidändringar på Samsung Knox-enheter. Du hittar den i **Profiler för enhetskonfiguration** > **Enhetsbegränsningar (Android)**  > **Allmänt**.

#### <a name="surface-hub-resource-account-supported---1566442----"></a>Stöd för Surface Hub-resurskonto<!-- 1566442  -->

En ny enhetsåtgärd har lagts till så att administratörer kan definiera och uppdatera resurskonton som är associerade med en Surface Hub.

Resurskontot används av en Surface Hub för att autentisera med Skype/Exchange så att den kan ansluta till ett möte. Du kan skapa ett unikt resurskonto så att Surface Hub visas i mötet som konferensrummet. Resurskontot kan till exempel visas som *konferensrum B41/6233*. Resurskontot (kallas även enhetskontot) för Surface Hub måste vanligtvis konfigureras för konferensrumsplatsen och när andra parametrar för resurskontot måste ändras.

När administratörer vill uppdatera resurskontot på en enhet, måste de ange de aktuella autentiseringsuppgifterna för Active Directory/Azure Active Directory som är kopplade till enheten. Om lösenordsrotation är aktiverat för enheten, måste administratörer gå till Azure Active Directory för att hitta lösenordet.

> [!NOTE]
> Alla fält skickas i ett paket och skriver över alla fält som tidigare var konfigurerade. Tomma fält skriver också över befintliga fält.

Följande är de inställningar som administratörer kan konfigurera:

- **Resurskonto**
  - **Active Directory-användare**

    Domännamn\användarnamn eller användarens huvudnamn (UPN):user@domainname.com

  - **Lösenord**

- **Valfria parametrar för resurskontot** (måste anges med det angivna resurskontot)

  - **Intervall för lösenordsrotation**

    Garanterar att kontolösenordet uppdateras automatiskt av Surface Hub varje vecka av säkerhetsskäl. Om du vill konfigurera parametrar efter att det här har aktiverats, måste kontot i Azure Active Directory få lösenordet nollställt.

  - **SIP-adress (Session Initiation Protocol)**

    Används endast när automatisk identifiering misslyckas.

  - **E-post**

    E-postadress för enhets-/resurskontot.

  - **Exchange-server**

    Krävs endast om automatisk identifiering misslyckas.

  - **Kalendersynkronisering**

    Anger om kalendersynkronisering och andra Exchange-servertjänster är aktiverade. Till exempel: mötessynkronisering.

#### <a name="install-office-apps-on-macos-devices---1494311---"></a>Installera Office-appar på macOS-enheter<!-- 1494311 -->
Du kommer nu att kunna installera Office-appar på macOS-enheter. Den här nya apptypen låter dig installera Word, Excel, PowerPoint, Outlook och OneNote. De här apparna inkluderar även Microsoft AutoUpdater (MAU), för att hålla dina appar säkra och uppdaterade.

### <a name="app-management"></a>Apphantering

#### <a name="delete-an-ios--volume-purchasing-program-token---820879---"></a>Ta bort en token för iOS-volyminköpsprogram<!-- 820879 -->
Du kan ta bort token för iOS-volyminköpsprogram (VPP) med hjälp av konsolen. Detta kan vara nödvändigt när du har dubblettinstanser av en VPP-token.

### <a name="intune-apps"></a>Intune-appar


### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data---1667026---"></a>En ny entitetssamling med namnet Aktuell användare är begränsad till för närvarande aktiva användardata<!-- 1667026 -->

Entitetssamlingen **Användare** innehåller alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i ditt företag. En användare kan till exempel läggas till i Intune och sedan tas bort under den senaste månaden. Användaren är då inte tillgänglig vid tidpunkten för rapporten, men användaren och tillståndet finns i data. Du kan skapa en rapport som visar varaktigheten för användarens historiska förekomst i dina data.

Den nya entitetssamlingen **aktuell användare** innehåller däremot bara användare som inte har tagits bort. Entitetssamlingen **aktuell användare** innehåller bara användare som är aktiva för tillfället. Mer information om entitetssamlingen **aktuell användare** finns i [referens för den aktuella användarentiteten](../developer/reports-ref-data-model.md).

### <a name="updated-graph-apis---1736360---"></a>Uppdaterade Graph-API:er<!-- 1736360 -->

Vi har uppdaterat några av Graph API:erna för Intune i den här betaversionen. Kontrollera den månatliga [Ändringsloggen för Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog) för mer information.

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="intune-supports-windows-information-protection-wip-denied-apps---1479103---"></a>Intune stöder appar som nekats av Windows Information Protection (WIP)<!-- 1479103 -->
Du kan ange nekade appar i Intune. Om en app nekas blockeras den från att komma åt företagsinformation. Detta är i praktiken motsatsen till listan över tillåtna appar. Mer information finns i [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Rekommenderad neka-lista för Windows Information Protection).

<!-- ########################## -->
## <a name="november-2017"></a>November 2017

### <a name="troubleshoot-enrollment-issues----746324---"></a>Felsöka registreringsproblem <!-- 746324 -->

I **felsökningsarbetsytan** visas nu problem med användarregistreringen. Information om problemet och förslagna lösningar kan hjälpa administratörer och medarbetare på supportavdelningen att felsöka problem. Vissa problem med registreringen inte fångas upp, och vissa fel kanske inte har några reparationsförslag.

### <a name="group-assigned-enrollment-restrictions---747598---"></a>Grupptilldelade registreringsbegränsningar<!-- 747598 -->

Som Intune-administratör kan du nu [skapa anpassade registreringsbegränsningar för enhetstyp och enhetsgräns för användargrupper](../enrollment/enrollment-restrictions-set.md).

Du kan skapa upp till 25 instanser av varje begränsningstyp med Intune Azure Portal som du sedan kan tilldela till användargrupper. Grupptilldelade begränsningar åsidosätter standardbegränsningarna.

Alla instanser av en begränsningstyp lagras i ett strikt sorterad lista. Den här ordningen definierar prioritetsvärden för konfliktlösning. En användare som påverkas av mer än en begränsningsinstans begränsas endast av instansen med det högsta prioritetsvärdet. Du kan ändra prioriteten för en viss instans genom att dra den till en annan plats i listan.

Den här funktionen kommer att lanseras med migreringen av Android for Work-inställningar från registreringsmenyn för Android for Work till menyn för registreringsbegränsningar. Den här migreringen kan ta flera dagar. Ditt konto kan uppgraderas för andra delar av novemberversionen innan grupptilldelning aktiveras för registreringsbegränsningar.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors---1528104---"></a>Stöd för flera anslutningsprogram för registreringstjänster för nätverksenheter (NDES)<!-- 1528104 -->

Registreringstjänsten för nätverksenheter (NDES) gör det möjligt för mobilenheter som körs utan domänautentiseringsuppgifter att hämta certifikat baserade på SCEP-tillägg (Simple Certificate Enrollment Protocol).
Med den här uppdateringen stöds flera NDES-anslutningsprogram.

### <a name="manage-android-for-work-devices-independently-from-android-devices---1490731-eeready--"></a>Hantera Android for Work-enheter oberoende av Android-enheter<!-- 1490731 EEready-->

Intune stöder registrering av hantering av Android for Work-enheter oberoende av Android-plattformen. De här inställningarna hanteras under **Enhetsregistrering** > **Registreringsbegränsningar** > **Begränsningar för enhetstyper**. (De fanns tidigare **Enhetsregistrering** > **Android for Work-registrering** > **Registreringsinställningar för Android for Work**.)

Som standard är dina Android for Work-enhetsinställningar samma som inställningarna för dina Android-enheter. Men när du har ändrat dina Android for Work-inställningar kommer det här inte längre att vara fallet.

Om du blockerar registrering av personligt ägda Android for Work-enheter så kan endast företagsägda Android-enheter att registrera Android for Work.

Tänk på följande när du konfigurerar nya inställningar:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Om du aldrig tidigare har publicerat Android for Work-registrering

Den nya Android for Work-plattformen blockeras av standardbegränsningarna för enhetstyper. När du har publicerat funktionen kan du tillåta enheter att registreras med Android for Work. För att göra detta ändrar du på standardvärdena eller skapar en ny begränsning för enhetstyp för att ersätta begränsningen för enhetstyp som är standard.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Om du har publicerat Android for Work-registrering

Om du har publicerat tidigare så beror din situation på de inställningar du väljer:

| Inställningen | Statusen för Android for Work under begränsningar för enhetstyper | Obs! |
| --- | --- | --- |
| **Hantera alla enheter som Android** | Blockerad | Alla Android-enheter måste registreras utan Android for Work. |
| **Hantera enheter som stöds som Android for Work** | Tillåts | Alla Android-enheter som har stöd för Android for Work måste registreras med Android for Work. |
| **Hantera endast enheter som stöds i de här grupperna som Android for Work för användare** | Blockerad | En separat princip för begränsningar för enhetstyper skapades för att åsidosätta standardinställningen. Den här principen definierar de grupper som du tidigare valde för att tillåta Android for Work-registrering. Användare i de valda grupperna fortsätter att kunna registrera sina Android for Work-enheter. Alla andra användare är begränsade från att registrera med Android for Work. |

I samtliga fall bevaras din avsedda regler. Ingen åtgärd krävs från din sida för att underhålla den globala begränsningen eller per grupp-begränsningen för Android for Work i din miljö.

### <a name="google-play-protect-support-on-android---908720---"></a>Stöd för Google Play Protect på Android<!-- 908720 -->

Med versionen Android Oreo introducerar Google en uppsättning säkerhetsfunktioner med namnet Google Play Protect, där användare och organisationer kan köra skyddade appar och Android-bilder. Intune stöder nu Google Play Protect-funktionerna, inklusive SafetyNets fjärrattestering. Administratörer kan ange efterlevnadsprincipkrav som kräver att Google Play Protect är konfigurerat och felfritt.
Inställningen **SafetyNets enhetsattestering** kräver att enheten ansluter med en Google-tjänst för att kontrollera att enheten är felfri och inte har komprometterats. Administratörer kan också ange en konfigurationsprofilinställning för Android for Work som kräver att installerade program verifieras av Google Play-tjänsterna. Villkorlig åtkomst kan blockera användare från att komma åt företagets resurser om en enhet inte är kompatibel med Google Play Protect-kraven.

- Lär dig [hur du skapar en princip för enhetsefterlevnad om du vill aktivera Google Play-skydd](../protect/compliance-policy-create-android.md).

### <a name="text-protocol-allowed-from-managed-apps---1414050----"></a>Textprotokoll tillåts från hanterade appar<!-- 1414050  -->

Appar som hanteras av Intune App SDK kan skicka SMS-meddelanden.


### <a name="app-install-report-updated-to-include-install-pending-status---1249446---"></a>Rapporten om appinstallation har uppdaterats till att omfattar statusen Installation väntar<!-- 1249446 -->  

Rapporten **Status för appinstallation** som är tillgänglig för varje app via listan **Appar** i arbetsbelastningen **Klientappar** innehåller nu en sammanräkning av antalet **Installation väntar** för användare och enheter.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection---1391759---"></a>Appinventerings-API för iOS 11 för mobil hotidentifiering<!-- 1391759 -->

Intune samlar in information om appinventering från både personliga och företagsägda enheter och gör den tillgänglig för leverantörer av mobil hotidentifiering (MTD) att hämta, till exempel Lookout for Work. Du kan samla in en appinventering från användare av enheter med iOS 11+.

**Appinventering**  
Inventeringar från både företagsägda iOS 11+ och personligt ägda enheter skickas till MTD-leverantören. Data i appinventeringen omfattar:

- App-ID
- Appversion
- Kort appversion
- Appnamn
- Storlek på appsamling
- Dynamisk appstorlek
- Om appen har verifierats eller inte
- Om appen är hanterad eller inte

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone---1463747-wnready---"></a>Migrera användare och enheter med hybrid MDM till fristående Intune<!-- 1463747 wnready -->
Det finns nu nya processer och verktyg för att flytta användare och deras enheter från hybrid MDM till Intune på Azure Portal. Nu kan du göra följande:
- Kopiera principer och profiler från Configuration Manager-konsolen till Intune på Azure Portal
- Flytta en del av användarna till Intune på Azure Portal medan resten fortsätter att använda hybrid MDM
- Migrera enheter till Intune på Azure Portal utan att behöva registrera dem på nytt

### <a name="on-premises-exchange-connector-high-availability-support----676614---"></a>Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram <!-- 676614 -->
När Exchange-anslutningsappen skapar en anslutning till Exchange med angiven klientåtkomstserver (CAS) har anslutningsappen nu möjlighet att identifiera andra CAS. Om den primära certifikatutfärdaren blir otillgänglig, kommer anslutningsappen att växla till en annan certifikatutfärdare, om tillgänglig, tills den primära certifikatutfärdaren blir tillgänglig. Du hittar mer information i [Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram](../protect/exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only---1424595---"></a>Starta om iOS-enheter via fjärranslutning (endast övervakade)<!-- 1424595 -->

Du kan nu få en övervakad iOS 10.3 +-enhet att starta om med en enhetsåtgärd. Mer information om hur du använder åtgärden för omstart av enhet finns i [Starta om enheter med Intune med en fjärråtgärd](../remote-actions/device-restart.md).

> [!Note]
> Det här kommandot kräver en övervakad enhet och behörighet till **Enhetslås**. Enheten startas om direkt. iOS-enheter låsta med lösenord kommer inte återansluta till ett Wi-Fi-nätverk efter omstarten. Efter omstart kanske de inte kan kommunicera med servern.

### <a name="single-sign-on-support-for-ios---1333645---"></a>Stöd för enkel inloggning för iOS<!-- 1333645 -->  

Du kan använda enkel inloggning för iOS-användare. iOS-appar som är kodade för att leta efter användares autentiseringsuppgifter i nyttolasten för enkel inloggning fungerar med den här uppdateringen av nyttolastkonfigurationen. Du kan även använda UPN och Intune-enhets-ID för att konfigurera huvudnamn och sfär. Mer information finns i [Konfigurera enkel inloggning för Intune för iOS-enheter](../configuration/ios-device-features-settings.md#single-sign-on).

### <a name="add-find-my-iphone-for-personal-devices--1427287--"></a>Lägga till ”Hitta min iPhone” för personliga enheter<!--1427287-->
Du kan nu se om iOS-enheter har aktiveringslåset aktiverat. Den här funktionen kunde tidigare hittas i den klassiska Intune-portalen.

### <a name="remotely-lock-managed-macos-device-with-intune---1437691---"></a>Fjärrlåsa hanterade macOS-enheter med Intune<!-- 1437691 -->

Du kan låsa en förlorad macOS-enhet och ange en PIN-kod för återställning på 6 siffror. När enheten är låst visar bladet **Enhetsöversikt** PIN-koden tills en annan enhetsåtgärd skickas.

Mer information finns i [Fjärrlåsa hanterade enheter med Intune](../remote-actions/device-remote-lock.md).

### <a name="new-scep-profile-details-supported---1559808---"></a>Ny SCEP-profilinformation stöds<!-- 1559808 -->

Administratörer kan nu ange fler inställningar när de skapar en SCEP-profil på Windows-, iOS-, macOS- och Android-plattformar.  Administratörer kan ange IMEI, serienummer eller eget namn inklusive e-post i ämnesnamnets format.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset---1588489---"></a>Behålla data under en fabriksåterställning <!--1588489 -->
En ny funktion är tillgänglig när du återställer Windows 10 version 1709 och senare till fabriksinställningarna. Administratörer kan ange om enhetsregistrering och andra etablerade data ska finnas kvar på en enhet efter att en fabriksåterställning har utförts.

Följande data behålls efter en fabriksåterställning:
- Användarkonton kopplade till enheten
- Datortillstånd (domänansluten, ansluten till Azure Active Directory)
- MDM-registrering
- Installerade OEM-appar (store och Win32-appar)
- Användarprofil
- Användardata utanför användarprofilen
- Automatisk inloggning för användare

Följande data bevaras inte:
- Användarfiler
- Användarinstallerade appar (store och Win32-appar)
- Enhetsinställningar som inte är standard


### <a name="window-10-update-ring-assignments-are-displayed---1621837---"></a>Tilldelningar till Windows 10-uppdateringstestgrupper visas<!-- 1621837 -->
Du kan se alla tilldelningar till Windows 10-uppdateringstestgrupper för den användare du visar när du **felsöker**.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings----1455974----"></a>Inställningar för rapporteringsfrekvens för Windows Defender Avancerat skydd <!-- 1455974  -->
Tjänsten Windows Defender Avancerat skydd (WDATP) låter administratörer hantera rapporteringsfrekvensen för hanterade enheter. Med det nya alternativet **Skicka frekvensvärde för telemetrirapportering** samlar WDATP in data och utvärderar risker oftare. Standardvärdet för rapporteringsfrekvensen optimerar hastighet och prestanda. Att öka frekvensen för rapportering kan vara användbart för högriskenheter. Den här inställningen finns i profilen **Windows Defender ATP** i **Enhetskonfigurationer**.

### <a name="audit-updates---1412961---"></a>Granskningsuppdateringar<!-- 1412961 -->  
Intune-granskning tillhandahåller en post med förändringsåtgärder relaterade till Intune.  Alla åtgärder för att skapa, uppdatera och ta bort, samt fjärruppgifter, sparas och lagras i ett år.  Azure Portal visar granskningsdata i varje arbetsbelastning för de senaste 30 dagarna. Det går även att filtrera bland dessa data.  En motsvarande Graph API gör det möjligt att hämta granskningsdata som lagrats under det senaste året.

Granskning hittas under gruppen **ÖVERVAKA**. Det finns ett menyalternativ för **Granskningsloggar** för varje arbetsbelastning.

### <a name="company-portal-app-for-macos-is-available--1541700--"></a>Företagsportalappen för macOS finns tillgänglig<!--1541700-->
Intunes företagsportal på macOS har en uppdaterad upplevelse som har optimerats för att visa all information och de efterlevnadsmeddelanden som användare behöver för alla enheter som de har registrerat. När Intunes företagsportal har distribuerats till en enhet, kommer Microsoft AutoUpdate för macOS att ge den uppdateringar. Du kan hämta den nya Intune-företagsportalen för macOS genom att logga in på webbplatsen för Intune-företagsportalen från en macOS-enhet.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps----1248473---"></a>Microsoft Planner är nu en del av MAM-listan (hantering av mobilappar) över godkända appar <!-- 1248473 -->
Microsoft Planner-appen för iOS och Android är nu del av de godkända apparna för hantering av mobilappar (MAM). Appen kan konfigureras via bladet för Intune-appskydd i Azure-portalen för alla klienter.
- Läs mer i [MAM-listan över godkända appar](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices-----1547061---"></a>Uppdateringsfrekvens för per app-VPN-krav på iOS-enheter  <!-- 1547061 -->  
Administratörer kan nu ta bort per App-VPN-kravet för appar på iOS-enheter. Berörda enheter kommer efter deras nästa Intune-incheckning, vilket vanligtvis sker inom 15 minuter.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector---885457---"></a>Stöd för System Center Operations Manager-hanteringspaket för Exchange-anslutningsapp<!-- 885457 -->
Nu är SCOM-hanteringspaketet (System Center Operations Manager) för Exchange-anslutningsappen tillgängligt och hjälper dig att parsa Exchange-anslutningsloggarna. Den här funktionen ger dig flera olika sätt att övervaka tjänsten när du behöver felsöka problem.

### <a name="co-management-for-windows-10-devices----1243445---"></a>Samhantering för Windows 10-enheter <!-- 1243445 -->
Samhantering är en lösning som erbjuder en brygga från traditionell till modern hantering, och det ger dig en sökväg för att göra övergången stegvis. I grund och botten är samhantering en lösning där Windows 10-enheter samtidigt hanteras av Configuration Manager och Microsoft Intune, som är anslutna till Active Directory (AD) och Azure Active Directory (Azure AD).  Den här konfigurationen ger dig en sökväg för att modernisera med tiden i den takt som passar din organisation om du inte kan flytta allt på samma gång.  

### <a name="restrict-windows-enrollment-by-os-version---245498---"></a>Begränsa Windows-registrering efter OS-version<!-- 245498 -->
Som Intune-administratör kan du nu ange en lägsta och högsta version av Windows 10 för enhetsregistrering. Du kan ange begränsningarna på bladet **Plattformskonfigurationer**.

Intune fortsätter att stödja registrering av datorer och telefoner med Windows 8.1. Endast Windows 10-versioner kan dock konfigureras med lägsta och högsta gränser. Låt den lägsta gränsen vara tom om du vill tillåta registrering av 8.1-enheter.

### <a name="alerts-for-windows-autopilot-unassigned-devices----1631236---"></a>Aviseringar för otilldelade Windows Autopilot-enheter <!-- 1631236 -->
En ny avisering är tillgänglig för otilldelade Windows AutoPilot-enheter på sidan **Microsoft Intune** > **Enhetsregistrering** > **Översikt**. Den här aviseringen visar hur många enheter från AutoPilot-programmet som inte har tilldelade AutoPilot-distributionsprofiler. Använd informationen i aviseringen för att skapa profiler och tilldela dem till de otilldelade enheterna. När du klickar på aviseringen visas en fullständig lista över Windows AutoPilot-enheter och detaljerad information om dem. Läs mer i informationen om att [registrera Windows-enheter med Windows AutoPilot-distributionsprogrammet](../enrollment/enrollment-autopilot.md).


### <a name="refresh-button-for-devices-list------1333581---"></a>Uppdateringsknapp för enhetslista   <!-- 1333581 -->
Eftersom enhetslistan inte uppdateras automatiskt kan du använda den nya uppdateringsknappen för att uppdatera vilka enheter som visas i listan.

### <a name="support-for-symantec-cloud-certification-authority-ca----1333638---"></a>Stöd för Symantec Cloud-certifikatutfärdare (CA) <!-- 1333638 -->    
Intune stöder nu Symantec Cloud CA, som tillåter att Intune Certificate Connector utfärdar PKCS-certifikat från Symantec Cloud CA till hanterade Intune-enheter. Om du redan använder Intune Certificate Connector med Microsoft Certification Authority (CA) kan du använda den befintliga Intune Certificate Connector-konfigurationen för att lägga till Symantec CA-stöd.

### <a name="new-items-added-to-device-inventory----1404455---"></a>Nya objekt har lagts till i enhetsinventering  <!--1404455 -->
Följande nya objekt är nu tillgängliga i den [inventering som görs av registrerade enheter](../remote-actions/device-inventory.md):

- Wi-Fi MAC-adress
- Totalt lagringsutrymme
- Totalt ledigt utrymme
- MEID
- Abonnentens operatör

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Ange åtkomst för appar baserat på den lägsta Android-säkerhetskorrigeringen på enheten<!-- 1278463 -->   
En administratör kan definiera den lägsta Android-säkerhetskorrigering som måste vara installerad på enheten för beviljad åtkomst till ett hanterat program under ett hanterat konto.

> [!Note]  
> Den här funktionen begränsar endast säkerhetsuppdateringar som ges ut av Google på Android 6.0+-enheter.

### <a name="app-conditional-launch-support---1193313---"></a>Stöd för appvillkorlig start<!-- 1193313 -->
IT-administratörer kan nu ange ett krav via Azure-administrationsportalen på att framtvinga ett lösenord i stället för en numerisk PIN-kod via mobilapphantering (MAM) när programmet startas. Om det har konfigurerats måste användaren vid uppmaning ställa in och använda ett lösenord innan användaren får åtkomst till MAM-integrerade program. Ett lösenord definieras som en numerisk PIN-kod med minst ett specialtecken eller en gemen/versal. Den här versionen av Intune kommer att aktivera den här funktionen **enbart på iOS**. Intune stöder lösenord på liknande sätt som numeriska PIN-koder. En minsta längd krävs och upprepning av tecken och sekvenser tillåts. Den här funktionen kräver att program deltar (dvs. WXP, Outlook, Managed Browser, Yammer) för att integrera Intune APP SDK:n med koden för funktionen på plats för att lösenordsinställningarna ska framtvingas i berörda program.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report---1233999---"></a>App-versionsnumret för verksamhetsspecifika rapporter för installationsstatus för enhet<!-- 1233999 -->
I den här versionen visar rapporten för installationsstatus för enhet appversionsnumret för verksamhetsspecifika appar för iOS och Android. Du kan använda den här informationen för att felsöka dina appar och hitta enheter som kör gamla appversioner.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile---951708---"></a>Administratörer kan nu konfigurera brandväggsinställningar på en enhet med hjälp av en enhetskonfigurationsprofil<!-- 951708 -->   
Administratörer kan aktivera brandvägg för enheter och konfigurera olika protokoll för domän-, privata och offentliga nätverk.  Brandväggsinställningarna finns i profilen för slutpunktsskydd.

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization---958257---"></a>Windows Defender Application Guard skyddar enheter mot ej betrodda webbplatser enligt organisationens definition<!-- 958257 -->   
Administratörer kan definiera platser som ”betrodda” eller ”företagsdata” med hjälp av Windows Information Protection-arbetsflödet eller den nya profilen "Nätverksgräns" under enhetskonfigurationer. Webbplatser som inte är angivna i en 64-bitars Windows 10-enhets betrodda nätverk och som öppnas med Microsoft Edge öppnas istället i en webbläsare i en virtuell Hyper-V-dator.

Application Guard finns i profilerna för enhetskonfiguration i profilen ”Endpoint protection”. Därifrån kan administratörer konfigurera interaktion mellan den virtualiserade webbläsaren och värddatorn, ej betrodda och betrodda webbplatser och lagra data som genererats i den virtualiserade webbläsaren. Om du vill använda Application Guard på en enhet måste du först konfigurera en nätverksgräns. Det är viktigt att endast definiera en nätverksgräns för en enhet.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps---1031096---"></a>I Windows Defender Application Control på Windows 10 Enterprise finns ett läge för att enbart lita på godkända appar<!-- 1031096 -->    
Tusentals nya skadliga filer skapas varje dag, och användningen av signaturbaserat antivirusskydd för att bekämpa skadlig programvara kanske inte längre ger ett tillräckligt försvar mot nya attacker. Om du använder Windows Defender Application Control på Windows 10 Enterprise kan du ändra enhetskonfiguration från ett läge där appar är betrodda och annars blockeras av en antiviruslösning eller en annan säkerhetslösning till ett läge där operativsystemet enbart litar på appar som företaget har godkänt. Du tilldelar förtroende till appar i Windows Defender Application Control.

Med Intune kan du konfigurera principer för programkontroll i läget för ”endast granskning” eller i tvingande läge. Appar blockeras inte i läget för ”endast granskning”. Läget för ”endast granskning” loggar alla händelser i lokala klientloggar. Du kan också konfigurera om enbart Microsoft-komponenter och Windows Store-appar ska tillåtas att köras eller om ytterligare appar med gott rykte enligt Intelligent Security Graphs definition också ska tillåtas.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10---1063615---"></a>Window Defender Exploit Guard är en ny uppsättning intrångsförebyggande funktioner för Windows 10<!-- 1063615 -->   
Window Defender Exploit Guard innehåller anpassade regler för att minska sårbarheter i program, förhindra makro- och skripthot, automatiskt blockera nätverksanslutningar till IP-adresser med dåligt rykte och kan skydda data mot utpressningstrojaner och okända hot. Windows Defender Exploit Guard består av följande komponenter:

- **Attack Surface Reduction (ASR)** tillhandahåller regler som hjälper dig att förhindra hot via makron, skript och e-post.
- **Reglerad mappåtkomst** blockerar automatiskt åtkomst till innehåll i skyddade mappar.
- **Nätverksfilter** blockerar utgående anslutning från valfri app för IP/domän med dåligt rykte
- **Sårbarhetsskydd** erbjuder begränsningar för minne, kontrollflöde och principer som kan användas för att skydda ett program mot sårbarheter.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices---790537---"></a>Hantera PowerShell-skript i Intune för Windows 10-enheter<!-- 790537 -->

Intunes hanteringstillägg gör det möjligt att ladda upp PowerShell-skript i Intune för att köra Windows 10-enheter. Tillägget kompletterar funktioner för hantering av mobilenheter (MDM) i Windows 10 och gör det enklare för dig att flytta till modern hantering. Mer information finns i [Hantera PowerShell-skript i Intune för Windows 10-enheter](../apps/intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10--------1308850---"></a>Inställningar för enhetsbegränsningar för Windows 10     <!-- 1308850 -->
- Meddelandefunktion (endast mobil) – inaktivera testning eller MMS-meddelanden
- Lösenord – inställningar för att aktivera FIPS och användning av sekundära Windows Hello-enheter för autentisering 
- Skärm – inställningar för att slå på eller stänga av GDI-skalning för äldre appar

### <a name="windows-10-kiosk-mode-device-restrictions---1308872---"></a>Begränsningar för helskärmsläge för Windows 10-enheter<!-- 1308872 -->   
Du kan begränsa användare av Windows 10-enheter till helskärmsläge, vilket begränsar användarna till en uppsättning fördefinierade appar.  Det gör du genom att skapa en begränsningsprofil för Windows 10-enheter och ange inställningar för helskärmsläge.

Helskärmsläge stöder två lägen: **en enda app** (gör att användaren endast kan köra en enda app) eller **flerappsläge** (tillåter åtkomst till en uppsättning appar).  Du definierar användarkontot och enhetens namn, vilket avgör vilka appar som stöds).  Inloggade användare är begränsade till definierade appar.  Mer information finns i [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (Begränsad CSP-åtkomst). 

Krav för helskärmsläge:

- Intune måste vara MDM-författare.
- Apparna måste redan vara installerade på målenheten.
- Enheten måste vara [rätt etablerad](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries---1311967---"></a>Ny enhetskonfigurationsprofil för att skapa nätverksgränser<!-- 1311967 -->   
En profil för enhetskonfiguration som heter **Nätverksgräns** finns bland dina övriga enhetskonfigurationsprofiler. Använd den här profilen till att definiera onlineresurser som du anser är företagets och betrodda. Du måste definiera en nätverksgräns för en enhet *innan* funktioner som Windows Defender Application Guard och Windows informationsskydd kan användas på enheten. Det är viktigt att endast definiera en nätverksgräns för varje enhet.

Du kan definiera företagets molnresurser, IP-adressintervall och interna proxyservrar som du anser är betrodda. När en nätverksgräns är definierad kan den användas av andra funktioner som Windows Defender Application Guard och Windows informationsskydd.

### <a name="two-additional-settings-for-windows-defender-antivirus---1338409---"></a>Ytterligare två inställningar för Windows Defender Antivirus<!-- 1338409 -->  
**Filblockeringsnivå**

| | |
|---|---|
| Inte konfigurerat | **Ej konfigurerad** använder standardnivån för Windows Defender Antivirus-blockering och ger ett starkt skydd utan att öka risken för att upptäcka legitima filer. |
| Hög | **Hög** tillämpar en hög skyddsnivå.
| Hög +  | **Hög +** erbjuder Hög-nivån med extra skyddsåtgärder som kan påverka klientprestanda.
| Nolltolerans  | **Nolltolerans** blockerar alla okända körbara filer. |

Inställningen **Hög** kan orsaka att vissa legitima filer upptäcks, men det är osannolikt.
Vi rekommenderar att du ställer in filblockeringsnivån på standardläget **Ej konfigurerad**.

**Tidsgränstillägg för filgenomsökning av molnet**  

| | |
|--|--|
| Antal sekunder (0–50) | Ange den längsta tid som Windows Defender Antivirus ska blockera en fil under väntan på ett resultat från molnet. Standardvärdet är 10 sekunder: ytterligare tid som anges här (upp till 50 sekunder) läggs på för de 10 sekunderna. I de flesta fall går genomsökningen mycket snabbare än maxvärdet. En utökning av tiden gör att molnet kan undersöka misstänkta filer noggrant. Vi rekommenderar att du aktiverar den här inställningen och anger minst 20 ytterligare sekunder. |

### <a name="citrix-vpn-added-for-windows-10-devices---1512457---"></a>Citrix VPN tillagt för Windows 10-enheter<!-- 1512457 -->  
Du kan konfigurera Citrix VPN för Windows 10-enheter. Du kan välja Citrix VPN i listan *Välj en anslutningstyp* på bladet **Bas-VPN** när du konfigurerar en VPN för Windows 10 och senare.

> [!Note]
> Det fanns Citrix-konfiguration för iOS och Android.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios---1550823---"></a>Wi-Fi-anslutningar stöder i förväg delade nycklar på iOS<!-- 1550823 -->
Kunder kan konfigurera Wi-Fi-profiler för att använda i förväg delade nycklar (PSK) för personliga WPA/WPA2-anslutningar på iOS-enheter. De här profilerna pushas till användarens enhet när enheten registreras i Intune.

När profilen har pushats till enheten beror nästa steg på profilkonfigurationen.  Om automatisk anslutning är konfigurerad sker det när nätverket behövs härnäst.  Om profilen ska anslutas manuellt måste användaren aktivera anslutningen manuellt.  

### <a name="access-to-managed-app-logs-for-ios---1469920---"></a>Åtkomst till loggar för hanterade appar för iOS<!-- 1469920 -->
Slutanvändare med Managed Browser installerad kan nu se hanteringsstatus för alla appar som har publicerats av Microsoft och kan skicka loggar för felsökning av hanterade iOS-appar.

Om du vill lära dig att aktivera felsökningsläget i Managed Browser på en iOS-enhet kan du läsa [Komma åt loggar för hanterade appar med Managed Browser i iOS](../apps/app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290---1417174---"></a>Förbättringar av arbetsflödet för enhetskonfiguration i företagsportalen för iOS i version 2.9.0<!-- 1417174 -->

Arbetsflödet för enhetskonfiguration har förbättrats i företagsportalappen för iOS. Språket är mer användarvänligt och vi har kombinerat skärmar där det är möjligt. Språket är mer specifikt för ditt företag genom att företagsnamnet används genomgående i installationstexten. Du kan se det uppdaterade arbetsflödet på  [sidan nyheter i appgränssnittet](../whats-new-app-ui.md).


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model---1544273---"></a>Användarentiteten innehåller senaste användardata i datamodellen för informationslagret<!-- 1544273 -->
Den första versionen av datamodellen för Intune-informationslagret innehöll endast de senaste historiska Intune-data. Rapportskaparna kunde inte identifiera det aktuella tillståndet för en användare. I den här uppdateringen fylls **användarentiteten** i med senaste användardata.

<!-- ########################## -->
## <a name="october-2017"></a>Oktober 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible---1380712---"></a>Versionsnummer för verksamhetsspecifika iOS- och Android-appar är synligt<!-- 1380712 -->

Appar i Intune visar nu versionsnumret för verksamhetsspecifika iOS och Android-appar. Numret visas på Azure Portal i listan över appar och på bladet med översikt över appar. Slutanvändarna kan se appnumret i företagsportalappen och i webbportalen.

__Fullständigt versionsnummer__ Det fullständiga versionsnumret identifierar en specifik version av appen. Numret visas som _Version_(_Build_). Exempelvis, 2.2(2.2.17560800)

Det fullständiga versionsnumret har två komponenter:

- **Version**  
  Versionsnumret är det läsbara versionsnumret för appen. Det här numret används av slutanvändare för att identifiera olika versioner av appen.

- **Build-nummer**  
  Build-numret är ett internt nummer som kan användas i appidentifiering och för att programmässigt hantera appen. Build-nummer refererar till en iteration av appen som refererar till ändringar i koden.

Mer information om versionsnummer och utveckling av verksamhetsspecifika appar finns i [Get started with the Microsoft Intune App SDK](../developer/app-sdk-get-started.md#line-of-business-app-version-numbers) (Kom igång med Microsoft Intune App SDK).

### <a name="device-and-app-management-integration---677972---"></a>Integrering av enhets- och apphantering<!-- 677972 -->   
Nu när Intunes hantering av mobila enheter (MDM) och hantering av mobilprogram (MAM) båda är åtkomliga från Azure-portalen har Intune börjat integrera IT-adminstratörsupplevelsen kring program- och enhetshantering. De här ändringarna är avsedda att förenkla enhets- och apphanteringen.

Läs mer om ändringarna i MDM och MAM som presenteras i [Intune-supportteamets blogg](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices---1471790---"></a>Nya registreringsaviseringar för Apple-enheter<!-- 1471790 -->
Översiktssidan för registrering visar användbara aviseringar för IT-administratörer som gäller hantering av Apple-enheter. Aviseringar visas på översiktssidan när Apple MDM-push-certifikatet upphör att gälla eller redan har gått ut; när DEP-token upphör att gälla eller redan har gått ut eller när det finns enheter i programmet för enhetsregistrering som inte är tilldelade.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment---1080364---"></a>Stöd för tokenersättning för appkonfiguration utan enhetsregistrering<!-- 1080364 -->

Du kan använda token för dynamiska värden i appkonfigurationer för appar på enheter som inte har registrerats. Mer information finns i [Add app configuration policies for managed apps without device enrollment](../apps/app-configuration-policies-managed-app.md) (Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering).

### <a name="updates-to-the-company-portal-app-for-windows-10--1299474--"></a>Uppdateringar av företagsportalappen för Windows 10<!--1299474-->
Inställningssidan i företagsportalappen för Windows 10 har uppdaterats för att inställningar och avsedda användaråtgärder ska vara mer konsekventa över alla inställningar. Den har också uppdaterats så att den matchar layouten för andra Windows-appar. Du hittar före-/efter-bilder på sidan [nyheter i appgränssnittet](../whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices--1337920--"></a>Informera slutanvändarna om vilken enhetsinformation som kan visas för Windows 10-enheter<!--1337920-->
Vi har lagt till **ägarskapstyp** till skärmen enhetsinformation i företagsportalappen för Windows 10. På så sätt kan användarna få mer information om sekretess direkt från den här sidan från Intunes slutanvändardokumentation. De kommer även att kunna hitta den här informationen på **Om**-skärmen.

### <a name="feedback-prompts-for-the-company-portal-app-for-android--1165249--"></a>Feedbackfrågor för företagsportalappen för Android<!--1165249-->
Företagsportalappen för Android ber nu om feedback från slutanvändare. Denna feedback skickas direkt till Microsoft och ger slutanvändarna en möjlighet att recensera appen i den offentliga Google Play-butiken. Feedback är inte obligatoriskt och kan enkelt ignoreras så att användarna kan fortsätta att använda appen.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android---1573324-1573150-1558616-1564878---"></a>Hjälpa dina användare att hjälpa sig själva med företagsportalsappen för Android<!-- 1573324, 1573150, 1558616, 1564878 -->

Företagsportalappen för Android har lagt till anvisningar för slutanvändare för att hjälpa dem att förstå och om möjligt, själva lösa nya problem.
- Slutanvändare dirigeras till [Azure Active Directory-portalen](https://account.activedirectory.windowsazure.com/r/#/profile) för att ta bort en enhet om de har nått det högsta antalet enheter som de tillåts ha.
- Slutanvändare rekommenderas åtgärder att vidta för att hjälpa dem att [åtgärda aktiveringsfel på Samsung Knox-enheter](https://go.microsoft.com/fwlink/?linkid=859718) eller för att [inaktivera energisparläge](/intune-user-help/power-saving-mode-android). Om ingen av dessa lösningar löser problemet tillhandahåller vi en förklaring om hur du [submit logs to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (skickar loggar till Microsoft).

### <a name="new-resolve-action-available-for-android-devices---1583480---"></a>Den nya funktion ”Lös” är tillgänglig för Android-enheter<!-- 1583480 -->

Företagsportalappen för Android presenterar en ”Lös”-åtgärd på sidan _Uppdatera enhetsinställningar_. Det här alternativet tar slutanvändaren direkt till inställningen som gör att enheten är icke-kompatibel. Företagsportalappen för Android stöder för närvarande den här åtgärden för inställningarna [enhetens lösenord](/intune-user-help/set-your-pin-or-password-android), [USB-felsökning](/intune-user-help/you-need-to-turn-off-usb-debugging-android) och [Okända källor](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal---1565657---"></a>Förloppsindikator för enhetsinstallation i Android-företagsportalen<!-- 1565657 -->
Företagsportalappen för Android visar en förloppsindikator för installationen av enheten när en användare registrerar sin enhet. Indikatorn visas nya statusar, som börjar med ”ställer in din enhet...” och sedan ”registrerar din enhet...”, därefter ”slutför registrering av din enhet...” och ”slutför konfigurationen av din enhet...”.

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios--1029830--"></a>Stöd för certifikatbaserad autentisering på företagsportalen för iOS<!--1029830-->
Vi har lagt till stöd för certifikatbaserad autentisering (CBA) i företagsportalappen för iOS. Användare med CBA anger sitt användarnamn och trycker på länken ”Signera med ett digitalt certifikat”. CBA stöds redan på företagsportalappar för Android och Windows. Du kan läsa mer på sidan [Logga in på företagsportal-appen](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment---1334712---"></a>Program som är tillgängliga med eller utan registrering kan nu installeras utan att först uppmanas till registrering.<!-- 1334712 -->

Företagsprogram som har gjorts tillgängliga med eller utan registreringen i Androids företagsportalapp kan nu installeras utan någon uppmaning att registrera.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617----"></a>Stöd för Windows AutoPilot-distributionsprogram i Microsoft Intune <!-- 747617  -->
Nu kan du använda Microsoft Intune med Windows AutoPilot-distributionsprogrammet och ge dina användare möjlighet att etablera sina företagsenheter utan hjälp från IT-avdelningen. Du kan anpassa OOBE-åtgärderna (Out-of-Box Experience) och vägleda användarna när de ska ansluta sina enheter till Azure AD och registrera sig i Intune. Microsoft Intune och Windows AutoPilot samarbetar för att eliminera behovet av att distribuera, underhålla och hantera operativsystemavbildningar. Läs mer i informationen om att [registrera Windows-enheter med Windows AutoPilot-distributionsprogrammet](../enrollment/enrollment-autopilot.md).

### <a name="quickstart-for-device-enrollment----1425655---"></a>Snabbstart för enhetsregistrering <!-- 1425655 --> 
Nu finns en snabbstart tillgänglig i **Enhetsregistrering** med en tabell med referenser som hjälper dig att hantera plattformar och att konfigurera registreringsprocessen. Via en kort beskrivning av varje objekt och länkar till dokumentation med stegvisa instruktioner får du användbar dokumentation för att enklare komma igång.

### <a name="device-categorization---1427491---"></a>Enhetskategorisering<!-- 1427491 -->
De registrerade enheternas plattformsdiagram på bladet **Enheter > Översikt** ordnar enheter efter plattform, inklusive Android, iOS, macOS, Windows och Windows Mobile.  Enheter som kör andra operativsystem är grupperade i ”Övrigt”.  Detta inkluderar enheter som har tillverkats av Blackberry och NOKIA.  

Om du vill veta vilka enheter som påverkas i din klientorganisation väljer du **Hantera> Alla enheter** och använder sedan **Filter** för att begränsa **OS**-fältet.

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium – Ny partner för skydd mot mobilhot  <!-- 954681 -->  
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Zimperium, en Mobile Threat Defense-lösning som är integrerad med Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Så här fungerar integrering med Intune
Risken bedöms utifrån telemetri som samlas in från enheter som kör Zimperium. Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Zimperiums riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera icke-kompatibla enheter för företagets resurser baserat på de hot som har identifierats.

### <a name="new-settings-for-windows-10-device-restriction-profile-----978575-1308849---"></a>Nya inställningar för enhetsbegränsningsprofilen i Windows 10 <!--- 978575, 1308849, -->  
Vi lägger till nya inställningar i enhetsbegränsningsprofilen i Windows 10 i kategorin Windows Defender SmartScreen.

Mer information om enhetsbegränsningsprofilen för Windows 10 finns i [Inställningar för enhetsbegränsning i Windows 10 och senare](../configuration/device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Fjärrsupport för Windows- och Windows Mobile-enheter  <!-- 1070473 -->  
Intune kan nu använda [TeamViewer](https://www.teamviewer.com)-programvaran (säljs separat) för att du ska kunna ge fjärrhjälp till de användare som kör Windows- och Windows Mobile-enheter.

### <a name="scan-devices-with-windows-defender---1280988--1280990-----"></a>Genomsöka enheter med Windows Defender<!-- 1280988  1280990   -->
Du kan nu även köra en **snabbsökning**, **fullständig genomsökning** och **uppdatering av signaturer** med Windows Defender Antivirus på hanterade Windows 10-enheter. På enhetens översiktsblad väljer du den åtgärd som ska köras på enheten. Du uppmanas att bekräfta åtgärden innan kommandot skickas till enheten. 

**Snabbsökning**: En snabbsökning genomsöker platser där skadliga register startas, till exempel registernycklar och kända startmappar i Windows. En snabbsökning tar i genomsnitt fem minuter. I kombination med inställningen **Realtidsskydd alltid på** som söker igenom filer när de öppnas, stängs och när användaren navigerar till en mapp, ger snabbsökningen skydd mot skadlig kod som kan finnas i systemet eller kärnan. Användarna ser resultatet av genomsökningen på sina enheter när den är klar. 

**Fullständig genomsökning**: En fullständig genomsökning kan användas på enheter med ett skadligt hot, för att se om det finns några inaktiva komponenter som kräver en mer omfattande rensning. Den är även användbar för att köra genomsökningar på begäran. En fullständig genomsökning kan ta en timme att köra. Användarna ser resultatet av genomsökningen på sina enheter när den är klar. 

**Uppdatering av signaturer**: Kommandot för att uppdatera signaturer uppdaterar Windows Defender Antivirus-definitionerna för skadlig kod och signaturer. På så sätt kan du vara säker på att Windows Defender Antivirus fungerar när det gäller att identifiera skadlig kod. Den här funktionen finns endast för Windows 10-enheter och väntar på att enheten ska ansluta till Internet. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal----1400455---"></a>Knappen för att aktivera/inaktivera har tagits bort från sidan med Intune-certifikatutfärdare i Intune Azure-portalen <!-- 1400455 -->
 Vi tar bort ett extra steg vid konfigurationen av certifikatanslutningen i Intune. För närvarande laddar du ned certifikatanslutningen och aktiverar den sedan i Intune-konsolen. Om du emellertid inaktiverar anslutningsprogrammet i Intune-konsolen fortsätter anslutningsprogrammet att utfärda certifikat.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Från oktober finns inte längre knappen för att aktivera/inaktivera på sidan Intune Certificate Authority (Intune-certifikatutfärdare) i Intune Azure-portalen. Anslutningsfunktionen förblir densamma. Certifikat distribueras fortfarande för enheter som har registrerats i Intune. Du kan fortsätta att ladda ned och installera certifikatanslutningen. Om du vill stoppa att certifikat utfärdas avinstallerar du nu certifikatanslutningen istället för att inaktivera den.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Om du för närvarande har certifikatanslutningen inaktiverad bör du avinstallera den.

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838---"></a>Nya inställningar för profiler för Windows 10 Team-enhetsbegränsning  <!--- 1308838 -->
I den här versionen har vi lagt till många nya inställningar för Windows 10 Team-enhetens begränsningsprofil som hjälper dig att styra Surface Hub-enheter.

Mer information om profilen finns i [Begränsningsinställningar för Windows 10 Team-enheter](../configuration/device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>Förhindra att användare av Android-enheter ändrar sin enhets datum och tid <!-- 1333292 -->
Du kan använda en [anpassad Android-enhetsprincip](../configuration/custom-settings-android.md) för att förhindra att Android-enhetsanvändarna ändrar enhetens datum och tid.

Gör detta genom att konfigurera en anpassad Android-princip med inställnings-URI:n ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange Ange den till **TRUE** och tilldela den sedan till de grupper som krävs.

### <a name="bitlocker-device-configuration---1397398---"></a>BitLocker-enhetskonfiguration<!-- 1397398 -->
**Windows-kryptering > Grundinställningar** innehåller en ny inställning för **Varning för annan hårddiskkryptering**, där du kan inaktivera [varningen](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption) för annan diskkryptering som kanske används på användarens enhet.  Varningen kräver slutanvändarens medgivande innan BitLocker konfigureras på enheten och blockerar installationen av BitLocker tills den har bekräftats av slutanvändaren.  Den nya inställningen inaktiverar varningen till slutanvändaren.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant---800882---"></a>Volyminköpsprogram för företagsprogram synkroniseras nu till din Intune-klientorganisation<!-- 800882 -->  
Tredjepartsutvecklare kan även distribuera appar privat till auktoriserade medlemmar i volyminköpsprogram (VPP) för företag som anges i iTunes Connect. Dessa medlemmar i volyminköpsprogram för företag kan logga in i appbutiken för volyminköpsprogram och köpa sina appar.

Med den här versionen synkroniseras appar för volyminköpsprogram för företag som slutanvändaren köper med Intune-klienterna.

### <a name="select-apple-countryregion-store-to-sync-vpp-apps----1332311---"></a>Välj landet/regionens Apple Store för att synkronisera VPP-appar <!-- 1332311 -->  
Du kan konfigurera volymköpsprogrammets land/region när du laddar upp din VPP-token. Intune synkroniserar VPP-appar för alla språk från det angivna VPP-landet/-regionens App Store.

> [!NOTE]  
> I dag synkroniserar Intune endast VPP-appar från VPP-landet/-regionen som matchar det Intune-språk som Intune-klienten skapades i.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work---1098994---"></a>Blockera att kopiera och klistra in mellan arbetsprofiler och personliga profiler i Android for Work<!-- 1098994 -->
I den här versionen kan du konfigurera arbetsprofilen för Android for Work till att blockera kopiering och inklistring mellan arbetsappar och privata appar. Du hittar den här nya inställningen i profilen **Enhetsbegränsningar** för **Android for Work**-plattformen i **Arbetsprofilinställningar**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores---1281692---"></a>Skapa iOS-appar som är begränsade till specifika regionala Apple App Stores<!-- 1281692 -->
Du kommer att kunna ange en språkinställning för landet/regionen när du skapar en hanterad app i Apple App Store.

> [!Note]  
> För närvarande kan du bara skapa hanterade appar för Apple App Store som finns i landet/regionen USA.

### <a name="update-ios-vpp-user-and-device-licensed-apps----1305564---"></a>Uppdatera VPP-användare och licensierade appar på iOS-enheter <!-- 1305564 -->  
Du kommer att kunna konfigurera iOS VPP-token för att uppdatera alla appar som köpts för den token via Intune-tjänsten. Intune identifierar VPP-appuppdateringar i appbutiken och push-installerar dem automatiskt på enheten när den checkas in.

Instruktioner om hur du konfigurerar en VPP-token och aktiverar automatiska uppdateringar finns i [Så här hanterar du iOS-appar som har köpts via ett volyminköpsprogram med Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model---1187917---"></a>Användarenhetens associationsentitetssamling lades till i datamodellen för Intunes informationslager<!-- 1187917 -->
Du kan nu skapa rapporter och datavisualiseringar med hjälp av enhetens associationsinformation som associerar användaren och enhetens entitetssamlingar. Datamodellen kan nås via Power BI-filen (PBIX) som hämtas från Intune-sidan Informationslager via OData-slutpunkten, eller genom att utveckla en anpassad klient.

### <a name="review-policy-compliance-for-windows-10-update-rings---1067886---"></a>Granska principefterlevnad för Windows 10-uppdateringstestgrupper<!-- 1067886 -->
Du kommer att kunna granska en principrapport för din Windows 10-uppdateringstestgrupp i Programuppdateringar > Distributionsstatus per uppdateringstestgrupp. Principrapporten innehåller distributionsstatus för de uppdateringstestgrupper som du har konfigurerat. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions-----1352223---"></a>Ny rapport som visar en lista över iOS-enheter med äldre iOS-versioner  <!-- 1352223 -->
Rapporten **Out-of-date iOS Devices** (Gamla iOS-enheter) är tillgänglig i arbetsytan **Programuppdateringar**. I rapporten kan du visa en lista över alla övervakade iOS-enheter som har varit mål för en iOS-uppdateringsprincip och som har tillgängliga uppdateringar. Du kan se en status för varje enhet och se varför enheten inte har uppdaterats automatiskt. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>Visa tilldelningar av appskyddsprincip för felsökning<!--  1475003 -->
I den här kommande versionen kommer alternativet **Appskyddsprincip** att läggas till i listrutan **Tilldelningar** på bladet för felsökning. Nu kan du välja programskyddsprinciper för att se de programskyddsprinciper som tilldelats de valda användarna.



### <a name="improvements-to-device-setup-workflow-in-company-portal--1490692--"></a>Förbättringar av arbetsflödet för enhetskonfiguration i företagsportalen<!--1490692-->
Vi har förbättrat arbetsflödet för enhetskonfiguration i företagsportalappen för Android. Språket är mer användarvänligt och specifikt för ditt företag, och vi har kombinerat skärmar där det är möjligt. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices--1484985--"></a>Förbättrade riktlinjer för begäran om åtkomst till kontakter på Android-enheter<!--1484985-->

Företagsportalappen för Android kräver ofta att slutanvändaren godkänner behörighet för Kontakter. Om en slutanvändare nekar denna åtkomst kommer det nu att visas en avisering i appen som uppmanar till att godkänna det för villkorlig åtkomst. 

### <a name="secure-startup-remediation-for-android--1490712--"></a>Åtgärd för säker start för Android<!--1490712-->

Slutanvändare med Android-enheter kan trycka på orsaken till bristande efterlevnad i företagsportalappen. Om möjligt kommer de då direkt till rätt plats i inställningsappen för att kunna åtgärda problemet. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo--1475932--"></a>Ytterligare push-meddelanden för slutanvändare i företagsportalappen för Android Oreo<!--1475932-->

Slutanvändarna ser ytterligare meddelanden som anger när företagsportalen för Android Oreo utför bakgrundsaktiviteter, till exempel när principer hämtas från Intune-tjänsten. Detta ger bättre transparens för slutanvändarna eftersom de ser när företagsportalen utför administrativa uppgifter på deras enheter. Det här är en del av [optimeringen av företagsportalens användargränssnitt](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) för företagsportalappen för Android Oreo. 

Det finns ytterligare optimeringar för nya UI-element som är aktiverade i Android Oreo.  Slutanvändarna ser ytterligare meddelanden som anger när företagsportalen utför bakgrundsaktiviteter, till exempel när principer hämtas från Intune-tjänsten.  Detta ger bättre transparens för slutanvändarna eftersom de ser när företagsportalen utför administrativa uppgifter på deras enheter.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles---1485783---"></a>Nya funktioner i företagsportalappen för Android med arbetsprofiler<!-- 1485783 -->

När du registrerar en Android for Work-enhet med en arbetsprofil, är det företagsportalappen i arbetsprofilen som utför hanteringsuppgifterna på enheten. 

Såvida du inte använder en MAM-aktiverad app i den personliga profilen, har du inte längre någon användning av företagsportalappen för Android. För att förbättra användningen av arbetsprofilen kommer Intune automatiskt dölja den personliga företagsportalappen efter en lyckad arbetsprofilregistrering.

Företagsportalappen för Android kan aktiveras när som helst i den personliga profilen genom att du bläddrar efter [Företagsportal i Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) och sedan trycker på **Aktivera**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode--1428681--"></a>Företagsportal för Windows 8.1 och Windows Phone 8.1 flyttas till hanteringsläget<!--1428681-->

Från oktober 2017 flyttas företagsportalapparna för Windows 8.1 och Windows Phone 8.1 till hanteringsläget. Det innebär att program och befintliga scenarier, till exempel registrering och kompatibilitet, fortsätter att ha stöd för dessa plattformar. De här programmen fortsätter att vara tillgängliga för hämtning via den befintliga versionens kanaler, till exempel Microsoft Store. 

När programmen finns i hanteringsläget kommer de endast kunna ta emot kritiska säkerhetsuppdateringar. Inga ytterligare uppdateringar eller funktioner kommer att släppas för dessa program. Om du vill ha nya funktioner rekommenderar vi att du uppdaterar enheterna till Windows 10 eller Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>Blockera registrering av Samsung Knox-enheter som inte stöds <!-- 1490695 -->

Företagsportalappen försöker endast att registrera Samsung Knox-enheter som stöds. För att undvika Knox-aktiveringsfel som förhindrar MDM-registrering görs försök att genomföra enhetsregistrering endast om enheten syns i [listan över enheter som har publicerats av Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Samsung-enheter kan ha modellnummer som har stöd för Knox medan andra inte stöds. Kontrollera att Knox är kompatibelt med enhetsåterförsäljaren innan du köper och distribuerar. En fullständig lista över verifierade enheter finns i [Inställningar för Android- och Samsung Knox Standard-principer](supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower---1171126-1326920---"></a>Stöd för Android 4.3 och lägre upphör<!-- 1171126, 1326920 -->
Hanterade appar och företagsportalappen för Android kräver Android 4.4 och högre för åtkomst till företagets resurser. I december kommer alla registrerade enheter att tvingas att dras tillbaka, vilket innebär att de förlorar åtkomst till företagets resurser. Om du använder principer för appskydd utan MDM kommer appar inte ta emot uppdateringar och kvaliteten på användningsupplevelsen minskar över tid.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices--1165314--"></a>Informera slutanvändarna om vilken enhetsinformation som kan visas på registrerade enheter<!--1165314-->
Vi lägger till **Typ av ägarskap** på skärmen Enhetsinformation i alla företagsportalappar. På så sätt kan användarna få mer information om sekretess direkt från artikeln [Vilken information kan företaget se?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Det här kommer snart att lanseras i alla företagsportalappar. Vi tillkännagav detta för iOS under [september](#september-2017).

<!-- ########################## -->
## <a name="september-2017"></a>September 2017

### <a name="intune-supports-ios-11--1428975--"></a>Intune stöder iOS 11<!--1428975-->
Intune stöder iOS 11. Det här meddelades tidigare på [Intunes supportblogg](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80---1164477---"></a>Stöd för iOS 8.0 upphör<!-- 1164477 -->
Hanterade appar och företagsportalappen för iOS kräver iOS 9.0 och högre för åtkomst till företagets resurser. Enheter som inte är uppdaterade innan september kommer inte längre att ha åtkomst till Företagsportalen eller apparna. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10--1132468--"></a>Uppdateringsåtgärden lades till i företagsportalappen för Windows 10<!--1132468-->
Företagsportalappen för Windows 10 tillåter att användarna uppdaterar data i appen genom att antingen dra för att uppdatera eller trycka på F5 på stationära datorer.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios--739894--"></a>Informera användarna om vilken enhetsinformation som kan visas för iOS<!--739894-->

Vi har lagt till **Typ av ägarskap** på skärmen Enhetsinformation i företagsportalappen för iOS. På så sätt kan användarna få mer information om sekretess direkt från den här sidan från Intunes slutanvändardokumentation. De kan även hitta denna information på skärmen Om.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment---1169910---"></a>Tillåt att slutanvändare får åtkomst till företagsportalappen för Android utan registrering<!---1169910--->

Slutanvändare behöver snart inte att registrera sina enheter för att komma åt företagsportalappen för Android. Slutanvändare i organisationer som använder principer för appskydd får inte längre uppmaningar att registrera sina enheter när de öppnar företagsportalen. Slutanvändarna kommer också att kunna installera appar från företagsportalen utan att registrera sina enheter. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android---1396349---"></a>Enklare formuleringar i företagsportalappen för Android<!---1396349--->  

Registreringen av företagsportalappen för Android har förenklats med ny text för att göra det enklare för slutanvändarna att registrera. Om du har anpassad registreringsdokumentation bör du uppdatera den så att den återspeglar de nya skärmarna. Du hittar exempelbilder på sidan om [uppdateringar i användargränssnittet för Intunes slutanvändarappar](whats-new-app-ui.md#week-of-september-11-2017) page.

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy---677129---"></a>Windows 10-företagsportalappen lades till i Windows Information Protection-tillåtelseprincipen<!-- 677129 -->

Företagsportalappen för Windows 10 har uppdaterats så att den stöder Windows Information Protection (WIP). Programmet kan läggas till i den tillåtna WIP-principen. Med den här ändringen behöver programmet inte längre läggas till i listan **Undantag**.


<!-- ########################## -->
## <a name="august-2017"></a>Augusti 2017

### <a name="improvements-to-device-overview---1404453---"></a>Förbättringar av enhetsöversikt<!-- 1404453 -->  
Förbättringar av enhetsöversikt visar nu registrerade enheter, men inte enheter som hanteras av Exchange ActiveSync. Exchange ActiveSync-enheter har inte samma hanteringsalternativ som registrerade enheter. Om du vill se antalet registrerade enheter och antalet registrerade enheter efter plattform går du till **enheter** > **översikt** i Intune i Azure Portal.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Förbättringar av enhetsinventering som samlas in av Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
I den här versionen har vi gjort följande förbättringar i inventeringsinformationen som samlas in av de enheter som du hanterar:
 
- För Android-enheter kan du nu lägga till en kolumn i enhetsinventeringen som visar den senaste korrigeringsnivån för varje enhet. Lägg till kolumnen med **säkerhetskorrigeringsnivån** i enhetslistan för att se detta.
- När du filtrerar enhetsvyn kan du nu filtrera enheter efter deras registreringsdatum. Du kan till exempel endast visa de enheter som har registrerats efter ett angivet datum.
- Vi har gjort förbättringar för filter som används av objektet **Last Check-in Date** (Senaste incheckningsdatum).
- I enhetslistan kan du nu visa telefonnummer för företagsägda enheter.
Du kan dessutom använda filterfönstret för att söka efter enheter efter telefonnummer.

Mer information om enhetsinventering finns i [Så här visar du Intunes enhetsinventering](../remote-actions/device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Stöd för villkorlig åtkomst på macOS-enheter 
<!-- 720172 -->
Nu kan du skapa en princip för villkorlig åtkomst som kräver att Mac-enheter ska vara registrerade i Intune och kompatibla med dess efterlevnadsprinciper för enheter. Användarna kan till exempel ladda ned appen för Intune-företagsportalen på macOS och registrera sina Mac-enheter i Intune. Intune utvärderar om Mac-enheten följer standard eller inte med krav som PIN, kryptering, OS-version och systemintegritet.

- Läs mer om [stöd för villkorlig åtkomst på macOS-enheter](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview---1484796---"></a>Företagsportalappen för macOS är i offentlig förhandsversion<!---1484796--->
Företagsportalappen för macOS är nu tillgänglig som en del av den allmänt tillgängliga förhandsversionen för villkorlig åtkomst i Enterprise Mobility + Security. Den här versionen stöder macOS 10.11 och högre. Hämta den på [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Inställningar för enhetsbegränsningar för Windows 10    
<!--1063965, 1308850  -->
I den här versionen har vi lagt till nya inställningar för [begränsningsprofilen för Windows 10-enheter](/intune/device-restrictions-windows-10). Nyheterna finns i följande kategorier:

- Windows Defender SmartScreen
- Appbutik

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Uppdateringar för BitLocker-inställningar för enhetsprofiler för Windows 10 Endpoint Protection
<!--1459533 -->    
I den här versionen har vi gjort följande förbättringar för hur BitLocker-inställningar fungerar i en enhetsprofil för Windows 10 Endpoint Protection:
 
- När du tidigare valde **Blockera** för inställningen **BitLocker med icke kompatibelt TPM-chip** under **Inställningar för BitLocker-operativsystemenhet** gjorde detta tidigare att BitLocker ändå tilläts. Vi har nu löst problemet och BitLocker blockeras nu när det är markerat.
- För inställningen **certifikatbaserad dataåterställningsagent** under **Inställningar för BitLocker-operativsystemenhet** kan du nu uttryckligen blockera den certifikatbaserade dataåterställningsagenten. Som standard tillåts agenten.
- För inställningen **Dataåterställningsagent** under **Inställningar för fast BitLocker-dataenhet** kan du nu uttryckligen blockera dataåterställningsagenten.
Mer information finns i [Endpoint Protection-inställningar för Windows 10 och senare](../protect/endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users---621669---"></a>Ny inloggad upplevelse för användare av Android-företagsportalen och appskyddsprincip<!-- 621669 -->
Slutanvändarna kan nu bläddra bland appar, hantera enheter och visa it-kontaktinformation med hjälp av Android-företagsportalappen utan att registrera sina Android-enheter. Om en användare dessutom redan använder en app som skyddas av principer för Intune-appskydd och startar Android-företagsportalen får slutanvändaren inte längre någon uppmaning att registrera enheten.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization--1405990--"></a>Ny inställning i Android-företagsportalappen för att växla batterioptimering<!--1405990-->
Sidan **Inställningar** i företagsportalappen för Android har en ny inställning som gör det enkelt för användarna att stänga av batterioptimering för företagsportalen och Microsoft Authenticator-appar. Appnamnet som visas i inställningen beror på vilken app som hanterar arbetskontot. Vi rekommenderar att användarna stänger av batterioptimering för att få bättre prestanda med arbetsappar som synkroniserar e-post och data. 

### <a name="multi-identity-support-for-onenote-for-ios--------1234281---"></a>Stöd för flera identiteter med OneNote för iOS     <!-- 1234281 -->
Slutanvändare kan nu använda olika konton (arbete och personliga) med Microsoft OneNote för iOS. Programskyddsprinciper kan tillämpas på företagsdata i arbetsanteckningsböcker utan att de personliga anteckningsböckerna påverkas. En princip kan till exempel tillåta en användare att söka efter information i anteckningsböcker för arbete, men användaren kan inte kopiera och klistra in företagets data från anteckningsboken för arbete till en personlig anteckningsbok.
 
- Mer information om appar som stöder [appskydd och multiidentitet](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) med Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nya inställningar för att tillåta och blockera appar på Samsung Knox Standard-enheter
<!-- 1305423 822899-->  
Den här versionen innehåller nya [inställningar för enhetsbegränsning](../configuration/device-restrictions-android.md) som du kan använda för att ange följande applistor:
 
- Appar som användare tillåts att installera
- Appar som användare är blockerade från att installera
- Appar som är dolda från användaren på enheten
 
Du kan ange appen med hjälp av URL, paketnamn eller från listan över appar som du hanterar.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Ny gränssnittslänk för princip för appbaserad villkorlig åtkomst för Azure AD från Intune
<!-- 1016201 -->
IT-administratörer kan nu ange appbaserade villkorsprinciper via det nya gränssnittet för villkorlig åtkomstprincip i Azure AD-arbetsbelastningen. Den appbaserade villkorliga åtkomsten som finns i avsnittet Intune-appskydd i Azure Portal finns kvar där för tillfället och tillämpas sida vid sida. Det finns även en praktisk länk till det nya gränssnittet för villkorlig åtkomstprincip i Intune-arbetsbelastningen.

- Läs mer om [appbaserad villkorlig åtkomst i Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

<!-- ########################## -->
## <a name="july-2017"></a>Juli 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256--1245463----"></a>Begränsa Android- och iOS-enhetsregistrering per OS-version <!--- 1333256,  1245463 --->
Intune har nu stöd för att begränsa iOS- och Android-registrering efter operativsystemets versionsnummer. Under **Begränsning för enhetstyp** kan IT-administratören nu konfigurera en plattformskonfiguration som begränsar registrering mellan ett lägsta och högsta operativsystemsvärde. Versionerna för Android-operativsystemet måste anges som Major.Minor.Build.Rev, där Minor, Build och Rev är valfria. iOS-versionerna måste anges som Major.Minor.Build, där Minor och Build är valfria. Läs mer om [enhetsregistreringsbegränsningar](../enrollment/enrollment-restrictions-set.md).

>[!NOTE]
>Begränsar inte registrering via Apples registreringsprogram eller Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272--1333275-1245709----"></a>Begränsa registrering av personligt ägda Android-, iOS- och macOS-enheter <!--- 1333272,  1333275, 1245709 --->
Intune kan begränsa registrering av personliga enheter genom att skapa en lista över tillåtna IMEI-nummer för företagsenheter. Intune har nu expanderat den här funktionen till iOS, Android och macOS med hjälp av enhetsserienummer. Genom att ladda upp serienumren till Intune kan du fördeklarera enheter som företagsägda. Med begränsningar för registrering kan du blockera personligt ägda enheter (BYOD) och endast tillåta registrering av företagsägda enheter. Läs mer om [enhetsregistreringsbegränsningar](../enrollment/enrollment-restrictions-set.md).

Om du vill importera serienummer går du till **Enhetsregistrering** > **ID:n för företagsenheter** och klickar på **Lägg till**. Sedan laddar du upp en. CSV-fil (ingen rubrik, två kolumner för serienummer och detaljer som IMEI-nummer). Om du vill begränsa personligt ägda enheter, går du till **Enhetsregistrering** > **Registreringsbegränsningar**. Under **Begränsningar av enhetstyp** väljer du **Standard** och sedan **Plattformskonfigurationer**. Du kan **Tillåta** eller **Blockera** personligt ägda iOS-, Android- och macOS-enheter.


### <a name="new-device-action-to-force-devices-to-sync-with-intune---711369---"></a>Ny enhetsåtgärd för att tvinga enheter att synkronisera med Intune<!-- 711369 -->
I den här versionen har vi lagt till en ny enhetsåtgärd som tvingar den valda enheten att omedelbart checka in med Intune. När en enhet checkar in tar den omedelbart emot eventuella väntande åtgärder eller principer som har tilldelats till den.  Den här åtgärden kan hjälpa dig att validera och felsöka principer som du har tilldelat utan att du behöver vänta på nästa schemalagda incheckning.
Mer information finns i [Synkronisera enheten](../remote-actions/device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update---777100---"></a>Tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen<!-- 777100 -->
En ny princip är tillgänglig från arbetsytan Programuppdateringar där du kan tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga programuppdateringen. Mer information finns i [Konfigurera iOS-uppdateringsprinciper](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile – Ny partner för skydd mot mobilhot <!-- 954651, 1172027 -->
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst baserat på riskbedömning som utförs av Checkpoint SandBlast Mobile, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Hur fungerar integrering med Intune?
Risken bedöms utifrån telemetri som samlas in från enheter som kör Checkpoint SandBlast Mobile. Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Checkpoint SandBlast Mobiles riskbedömning som aktiveras via Intunes principer för enhetsefterlevnad. Du kan tillåta eller blockera inkompatibla enheters åtkomst till företagets resurser utifrån identifierade hot.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business---748101---"></a>Distribuera en app som tillgänglig i Microsoft Store för företag<!-- 748101 -->
Med den här versionen kan administratörer nu ställa in Microsoft-Store för företag som tillgänglig. Slutanvändarna kan installera appen från företagsportalappen eller webbplatsen utan att dirigeras om till Microsoft-Store när den är inställd som tillgänglig.

### <a name="ui-updates-to-the-company-portal-website--1313244-part-1--"></a>Gränssnittsuppdateringar på företagsportalswebbplatsen<!--1313244 part 1-->
Vi har gjort flera uppdateringar i gränssnittet för [företagsportalswebbplatsen](https://portal.manage.microsoft.com) för att förbättra användarupplevelsen.

- __Förbättringar av appaneler__:  Appikoner visas nu med en automatiskt genererad bakgrund som baseras på ikonens huvudsakliga färg (om den kan identifieras). När tillämpligt ersätter den här bakgrunden den grå kantlinje som tidigare fanns på appanelerna.

    Företagsportalens webbplats visar stora ikoner när det är möjligt i en kommande version. Vi rekommenderar att IT-administratörer publicerar appar med högupplösta ikoner som har en storlek på minst 120 x120 pixlar. 

- __Navigeringsändringar__: Objekt i navigeringsfältet har flyttats till Hamburger-menyn längst upp till vänster. Sidan Kategorier har tagits bort. Användarna kan nu filtrera innehåll efter kategori när de bläddrar.

- __Uppdateringar av aktuella appar__: Vi har lagt till en särskild sida på webbplatsen där användarna kan bläddra bland appar som du har valt att presentera och vi har gjort några gränssnittsförändringar på avsnittet Aktuella på startsidan.

### <a name="ibooks-support-for-the-company-portal-website--1231841--"></a>Stöd för iBooks på företagsportalens webbplats<!--1231841-->
Vi har lagt till en särskild sida på Företagsportalens webbplats där användare kan bläddra och hämta iBooks. 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>Ytterligare information om felsökning för supportavdelningen<!---  Applies to 1263399, 1326964, 1341642 --->
Intune har uppdaterat felsökningsskärmen och lagt till information för administratörer och supportpersonal. Nu visas tabellen **Tilldelningar** med en sammanfattning av alla användarens tilldelningar baserat på gruppmedlemskap. Listan innehåller:
- Mobilappar
- Efterlevnadsprinciper
- Konfigurationsprofiler

Tabellen **Enheter** innehåller nu även kolumnerna **Azure AD-anslutningstyp** och **Azure AD-kompatibel**. Mer information finns i [hjälpa användare att felsöka problem](../help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Intune-informationslager (Allmänt tillgänglig förhandsversion)
Intune-informationslagret samplar data dagligen och visar historik över din klient. Du kan komma åt data med en Power BI-fil (PBIX), en OData-länk som är kompatibel med många analytiska verktyg eller genom att interagera med REST API. Mer information finns i [Använd Intune-informationslagret](../developer/reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10---676547---"></a>Ljust läge och mörkt läge är tillgängliga för företagsportalappen för Windows 10<!---676547--->
Slutanvändare kan anpassa färgläget för företagsportalappen för Windows 10. Användaren kan göra ändringarna i avsnittet Inställningar i företagsportalappen. Ändringen tillämpas när användaren har startat om appen. För Windows 10 version 1607 och senare kommer standardläget för appen bero på systeminställningen. För Windows 10 version 1511 och tidigare kommer standardläget för appen vara det ljusa läget.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10---807046--"></a>Gör det möjligt för slutanvändare att tagga sin enhetsgrupp i företagsportalappen för Windows 10<!---807046-->
Slutanvändare kan nu välja vilken grupp deras enhet tillhör genom att tagga den direkt från företagsportalappen för Windows 10.

<!-- ########################## -->
## <a name="june-2017"></a>Juni 2017

### <a name="new-role-based-administration-access-for-intune-admins-----1099990---"></a>Ny rollbaserad administrationsåtkomst för Intune-administratörer  <!-- 1099990 -->  
En ny administratörsroll för villkorlig åtkomst läggs till för att kunna visa, skapa, ändra och ta bort Azure AD:s villkorliga åtkomstprinciper. Tidigare hade endast globala administratörer och säkerhetsadministratörer den här behörigheten. Intune-administratörer kan tilldelas den här rollbehörigheten så att de får åtkomst till principer för villkorlig åtkomst.


### <a name="tag-corporate-owned-devices-with-serial-number---1215070---"></a>Tagga företagsägda enheter med serienummer<!-- 1215070 -->  
Intune stöder nu uppladdning av iOS-, macOS- och Android-serienummer som identifierare för företagsägda enheter. Du kan inte använda serienummer för att blockera personliga enheter från registrering än, eftersom serienummer inte verifieras under registreringen. Blockering av personliga enheter med serienummer kommer att kunna göras inom en snar framtid.


### <a name="new-remote-actions-for-ios-devices---854689---"></a>Nya fjärråtgärder för iOS-enheter<!-- 854689 -->
I den här versionen har vi lagt till två nya fjärråtgärder som hanterar Apple Classroom-appen på delade iPad-enheter:

- [Logga ut aktuell användare](../remote-actions/device-logout-user.md) – Loggar ut den aktuella användaren för den valda iOS-enheten.
- [Ta bort användare](../remote-actions/device-remove-user.md) – Tar bort en vald användare från den lokala cachen på en iOS-enhet.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app---1044681---"></a>Stöd för delade iPad-enheter med iOS Klassrum-appen<!-- 1044681 -->
Från och med den här versionen har vi utökat stödet för hantering av Klassrum-appen i iOS, så att vi kan inkludera elever som loggar in på delade iPad-enheter med sina hanterade Apple-ID:n.


### <a name="changes-to-intune-built-in-apps---1332306---"></a>Ändringar i Intunes inbyggda appar<!-- 1332306 -->
Tidigare innehöll Intune ett antal inbyggda appar för snabb tilldelning. Efter feedback från användarna har vi beslutat oss för att ta bort listan och dess inbyggda appar visas inte längre.
Om du har redan har tilldelat några inbyggda appar kommer dessa även i fortsättningen att finnas kvar i listan över appar. Du kan fortsätta att tilldela dessa appar vid behov.
I en senare version planerar vi att lägga till en enklare metod för att välja och tilldela inbyggda program från Azure-portalen.

### <a name="easier-installation-of-office-365-apps----1121362----"></a>Enklare installation av Office 365-appar<!--- 1121362 --->
Med den nya **Office 365 ProPlus**-appen kan du enkelt tilldela Office 365 ProPlus 2016-appar till enheter som du hanterar och som kör den senaste versionen av Windows 10. Dessutom kan du installera Microsoft Project och Microsoft Visio om du har licenser för dem. Appar som du vill använda paketeras tillsammans och visas som en enda app i listan med appar i Intune-konsolen.
Läs mer i informationen om [hur du lägger till Office 365-appar för Windows 10](../apps/apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business----777044----"></a>Stöd för offline-appar från Microsoft Store för företag<!--- 777044 --->
Offline-program som du köpt från Microsoft Store för företag kommer nu att synkroniseras med Azure-portalen. Du kommer sedan att kunna distribuera apparna till enhetsgrupper eller användargrupper. Offline-appar installeras av Intune och inte av butiken.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps-----1257019---"></a>Microsoft Teams finns nu på den appbaserade certifikatutfärdarlistan över godkända appar  <!-- 1257019 -->
Microsoft Teams-appen för iOS och Android finns nu på listan över godkända appar för appbaserade villkorliga åtkomstprinciper för Exchange och SharePoint Online. Appen kan konfigureras via bladet för Intune-appskydd i Azure-portalen för alla klienter som för tillfället använder appbaserad villkorlig åtkomst.

### <a name="managed-browser-and-app-proxy-integration---1287310---"></a>Integrering av Managed Browser och programproxy<!-- 1287310 -->
Intune Managed Browser kan nu integreras med programproxy för Azure AD, så att användarna kan komma åt interna webbplatser även när de arbetar på distans. Användarna anger webbadressen i webbläsaren precis som vanligt. Managed Browser skickar begäran via programproxyns webbgateway. Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper](../apps/app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser---682951---"></a>Nya appkonfigurationsinställningar för Intune Managed Browser<!-- 682951 -->
I den här versionen har vi lagt till fler konfigurationer för Intune Managed Browser-appen för iOS och Android. Du kan nu använda en appkonfigurationsprincip för att konfigurera standardstartsidan och bokmärken i webbläsaren.
Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper](../apps/app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10----951707---"></a>BitLocker-inställningar för Windows 10 <!-- 951707 -->
Du kan nu konfigurera BitLocker-inställningar för Windows 10-enheter med hjälp av en ny enhetsprofil i Intune. Du kan t.ex. kräva att enheter krypteras och även ange ytterligare inställningar som ska användas när BitLocker är aktiverat.
Mer information finns i [Endpoint Protection-inställningar för Windows 10 och senare](../protect/endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile----978527--978550-978569-1050031-1058611-----"></a>Nya inställningar för enhetsbegränsningsprofilen i Windows 10<!--- 978527,  978550, 978569, 1050031, 1058611,  --->
I den här versionen har vi lagt till nya inställningar för begränsningsprofilen för Windows 10-enheter. Nyheterna finns i följande kategorier:

- Windows Defender
- Mobilnät och anslutning
- Låsskärm
- Sekretess
- Sök
- Windows Spotlight
- Microsoft Edge-webbläsare

Mer information om inställningar för Windows 10 finns i [Begränsningsinställningar för enheter med Windows 10 och senare](../configuration/device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies--1305217--"></a>Företagsportalappen för Android har nu ett nytt användargränssnitt för appskyddsprinciper<!--1305217-->
Baserat på feedback från våra kunder har vi ändrat företagsportalappen för Android så att den visar knappen **Åtkomst till företagsinnehåll**. Avsikten är att förhindra användare från att i onödan gå genom registreringsprocessen när de bara behöver åtkomst till appar som stöder appskyddsprinciper, en funktion i Intune för hantering av mobilappar. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal--1164569--"></a>Ny menyåtgärd för att enkelt ta bort företagsportalen<!--1164569-->
Baserat på användarfeedback har vi lagt till en ny menyåtgärd i företagsportalen för Android för att ta bort den från din enhet. Den här åtgärden tar bort enheten från Intune-hanteringen så att användaren kan ta bort appen från enheten. Du kan se dessa ändringar på sidan [Vad är nytt i appens gränssnitt](whats-new-app-ui.md) och i [bruksanvisningen för din Android-enhet](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update--676505--"></a>Förbättringar av appsynkronisering med Windows 10 Creators Update<!--676505-->
Företagsportalen för Windows 10 kommer automatiskt att initiera en synkronisering för appinstallationsbegäranden för enheter med Windows 10 Creators Update (1703). Detta minskar problemen där appen fastnar vid tillståndet ”Väntar på synkronisering” när installationer utförs. Dessutom kommer användare att kunna initiera en synkronisering från appen manuellt. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal---1058938---"></a>Ny guidad upplevelse för Windows 10-företagsportalen<!---1058938--->
Företagsportalappen för Windows 10 kommer att innehålla en guidad Intune-genomgång för enheter som inte har identifierats eller registrerats. Den nya guiden innehåller stegvisa anvisningar som hjälper användaren att utföra AAD-registrering (krävs för villkorliga åtkomstfunktioner) och MDM-registrering (krävs för enhetshanteringsfunktioner). Guiden kommer att vara tillgänglig på företagsportalens startsida. Användarna kan fortsätta att använda appen även om de inte slutför registreringen, men de får begränsad funktionalitet.

Den här uppdateringen visas bara på enheter som kör Windows 10 Anniversary Update (version 1607) eller senare. Du kan se dessa ändringar på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Administratörskonsoler till Microsoft Intune och villkorlig åtkomst är allmänt tillgängliga
Vi kommer att göra nya Intune i Azure-administrationskonsolen och administrationskonsolen för villkorlig åtkomst allmänt tillgängliga. Via Intune i Azure-portalen kan du nu hantera alla Intune MAM- och MDM-funktioner i en konsoliderad administratörsmiljö och använda Azure AD-gruppering och -mål. Villkorlig åtkomst i Azure ger de avancerade funktionerna i Azure AD och Intune tillsammans i en enhetlig konsol. Och från ett administrativt perspektiv innebär övergången till Azure-plattformen att du kan använda moderna webbläsare.

Intune visas nu utan etiketten **preview** i Azure-portalen på portal.azure.com.

Det krävs ingen åtgärd för befintliga kunder just nu, om du inte har tagit emot en av en serie meddelanden i meddelandecentret om att vidta åtgärder så att vi kan migrera dina grupper. Du kan också ha fått ett meddelande i meddelandecentret som informerar dig om att migreringen tar längre tid på grund av programfel på vår sida. Vi arbetar hårt på att migrera alla berörda kunder.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Förbättringar av appaneler i företagsportalappen för iOS
Vi har uppdaterat designen av appaneler på startsidan så att de återspeglar anpassningsfärgen som du angett för Företagsportalen. Mer information finns i [nyheter i appgränssnittet](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Kontoväljaren finns nu tillgänglig för företagsportalappen för iOS
Användare av iOS-enheter kan se vår nya kontoväljare när de loggar in på företagsportalen om de använder sitt arbets- eller skolkonto för att logga in på andra Microsoft-appar. Mer information finns i [nyheter i appgränssnittet](whats-new-app-ui.md).

<!-- ########################## -->
## <a name="may-2017"></a>Maj 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices--1103950--"></a>Ändra din utfärdare för hantering av mobila enheter utan att avregistrera hanterade enheter<!--1103950-->
Du kommer att kunna ändra din utfärdare för hantering av mobila enheter utan att behöva kontakta Microsoft Support och utan att behöva avregistrera och omregistrera dina befintliga hanterade enheter. I Configuration Manager-konsolen kan du ändra utfärdare för hantering av mobila enheter från Ange till Configuration Manager (hybrid) till Microsoft Intune (fristående) eller vice versa.


### <a name="improved-notification-for-samsung-knox-startup-pins--1087143--"></a>Förbättrat meddelande för PIN-koder för start av Samsung Knox<!--1087143-->
När användarna måste ange en PIN-kod för start på Samsung Knox-enheter för att bli kompatibla med kryptering, visas meddelandet för användarna. De kommer till rätt plats i appen Inställningar när de trycker på meddelandet.  Meddelandet tog tidigare användaren till skärmen där lösenord ändras.

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="apple-school-manager-asm-support-with-shared-ipad---748864-770395--"></a>Stöd för Apple School Manager (ASM) med delad iPad<!-- 748864, 770395-->

Intune stöder användning av Apple School Manager (ASM) för extern registrering av iOS-enheter, i stället för Apples program för enhetsregistrering. ASM-integrering krävs för att använda Classroom-appen på delade iPads, samt krävs för att aktivera datasynkronisering från ASM till Azure Active Directory via Microsoft School Data Sync (SDS). Mer information finns i [Aktivera registrering av iOS-enheter med Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md).

> [!NOTE]
> För att konfigurera delade iPad-enheter så att de fungerar med klassrumsappen behövs iOS Education i Azure som ännu inte är tillgänglig.  Den här funktionen läggs snart till.

### <a name="device-management"></a>Enhetshantering

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer---675418---"></a>Ge fjärrhjälp till Android-enheter med hjälp av TeamViewer<!-- 675418 -->

Intune kan använda [TeamViewer](https://www.teamviewer.com)-programmet (köps separat) för att ge fjärrhjälp till användare med Android-enheter. För mer information, se [Ge fjärrhjälp för Intune-hanterade Android-enheter](../remote-actions/teamviewer-support.md).

### <a name="app-management"></a>Apphantering

#### <a name="new-app-protection-policies-conditions-for-mam---679864---"></a>Nya villkor för appskyddsprinciper i MAM<!-- 679864 -->

Du kommer att kunna ange ett krav för MAM utan att registrera användare för följande principer:

- Lägsta programversion
- Lägsta operativsystemversion
- Lägsta Intune APP SDK-version i det aktuella programmet (endast iOS)

Den här funktionen är tillgänglig för både Android och iOS. Intune stöder krav på minimiversion för operativsystemversioner, programversioner och Intune APP SDK. I iOS kan program som har integrerat SDK också ange ett lägsta versionskrav på SDK-nivå. Användaren kommer inte att få åtkomst till det aktuella programmet om minimikraven via appskyddsprincipen inte uppfylls på de tre olika nivåer som nämns ovan. Nu kan användaren kan antingen ta bort sitt konto (för program med flera identiteter), stänga programmet och/eller uppdatera sitt operativsystem eller program.

Dessutom kan du också konfigurera ytterligare inställningar för ett icke-blockerande meddelande som rekommenderar en uppgradering av operativsystemet eller programmet. Det här meddelandet kan stängas och programmet kan då användas som vanligt.

Mer information finns i [Principinställningar för iOS-appskydd](../apps/app-protection-policy-settings-ios.md) och [Principinställningar för Android-appskydd](../apps/app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work---621621---"></a>Konfigurera appkonfigurationer för Android for Work<!-- 621621 -->
Vissa Android-appar från webbutiken stöder hanterade konfigurationsalternativ som gör att en IT-administratör kan kontrollera hur appen körs i en arbetsprofil. Med Intune kan du nu se de konfigurationer som stöds av ett program och konfigurera dem från Azure-portalen med en konfigurationsdesigner eller en JSON-redigerare. Mer information finns i [Använda appkonfigurationer för Android for Work](../apps/app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment---677969---"></a>Ny konfigurationsfunktion för appar för MAM utan registrering<!-- 677969 -->
Du kan nu skapa appkonfigurationsprinciper via MAM utan registrering. Den här funktionen motsvarar appkonfigurationsprinciper som är tillgängliga i appkonfigurationen för mobil enhetshantering (MDM). Ett exempel på konfiguration av en mobilapp med hjälp av MAM utan registrering finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](../apps/app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser---682960---"></a>Konfigurera listor över tillåtna och blockerade URL:er för Managed Browser<!-- 682960 -->
Du kan nu konfigurera en lista över tillåtna och blockerade domäner och webbadresser för Intune Managed Browser med konfigurationsinställningarna i Azure-portalen. Detta kan konfigureras oavsett om den används på en hanterad eller ohanterad enhet. Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](../apps/app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view---1069473---"></a>Supportvy för appskyddsprinciper<!-- 1069473 -->
Användare från IT-supportavdelningen kan nu kontrollera licensstatusen för användaren och status för principer för appskydd som är tilldelade till användare i felsökningsbladet. Se [felsökning](./help-desk-operators.md) för mer information.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="control-website-visits-on-ios-devices---723832---"></a>Kontrollera webbplatsbesök på iOS-enheter<!-- 723832 -->
Du kommer att kunna styra vilka webbplatser iOS-enhetsanvändarna kan besöka, med hjälp av någon av följande två metoder:

- Lägg till tillåtna och blockerade URL:er med hjälp av Apples inbyggda webbinnehållsfilter.

- Tillåt endast åtkomst till angivna webbplatser från webbläsaren Safari. Bokmärken skapas i Safari för varje plats som du anger.

För mer information, se [Inställningar för Intunes webbinnehållsfilter för iOS-enheter](../configuration/ios-device-features-settings.md#web-content-filter).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps---621614---"></a>Förkonfigurera enhetsbehörigheter för Android for Work-appar<!-- 621614 -->
För appar som distribuerats till Android for Work-arbetsprofiler, kommer du att kunna konfigurera behörighetstillstånd för enskilda appar.  Som standard kommer Android-appar som kräver enhetsbehörigheter, som t.ex. åtkomst till en plats eller enhetens kamera, att uppmana användarna att godkänna eller neka behörigheter.  Om till exempel en app ska använda enhetens mikrofon, ombeds användaren att bevilja appen behörighet att använda mikrofonen. Med den här funktionen kan du ange behörigheter åt användaren.  Du kan konfigurera behörigheter för att a) automatiskt neka utan att meddela användaren, b) automatiskt godkänna utan att meddela användaren eller c) uppmana användaren att godkänna eller neka. Mer information finns i [Enhetsbegränsningar i Microsoft Intune med Android for Work](../configuration/device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices---728976-1102534---"></a>Definiera en appspecifik PIN-kod för Android for Work-enheter<!-- 728976, 1102534 -->
Enheter med Android 7.0 eller senare med en arbetsprofil som hanteras som Android for Work-enheter låter administratören definiera en lösenordspolicy som endast tillämpas på appar i arbetsprofilen.  Alternativen är:

- Definiera bara en enhetsomfattande lösenordsprincip – Detta är det lösenord som användaren måste använda för att låsa upp hela enheten.
- Definiera bara en lösenordsprincip för arbetsprofilen. Användarna uppmanas att ange ett lösenord varje gång en app i arbetsprofilen öppnas.
- Definiera både en enhets- och en arbetsprofilprincip. IT-administratören kan välja att definiera både en lösenordsprincip för enheten och en lösenordsprincip för arbetsprofilen med olika styrkor (t.ex. en 4-siffrig PIN-kod för att låsa upp enheten, men en 6-siffrig PIN-kod för att öppna arbetsappar).

Mer information finns i [Enhetsbegränsningar i Microsoft Intune med Android for Work](../configuration/device-restrictions-android-for-work.md).

> [!NOTE]
> Det här är bara tillgängligt på Android 7.0 och högre.  Användaren kan som standard välja att använda två separat definierade PIN-koder, eller välja att kombinera de två definierade PIN-koderna till den starkaste av de två.

#### <a name="new-settings-for-windows-10-devices---978585---"></a>Nya inställningar för Windows 10-enheter<!-- 978585 -->
Vi lägger till nya [inställningar i begränsningsprofilen för Windows-enheter](../configuration/device-restrictions-windows-10.md) som styr funktioner som trådlösa skärmar, enhetsidentifiering, programväxling och felmeddelanden för SIM-kort.

#### <a name="updates-to-certificate-configuration---918991-and-823198---"></a>Uppdatering av certifikatkonfiguration<!-- 918991 and 823198 -->
När skapar en SCEP certifikatet profil för <strong>Ämnesnamnets format</strong>, <strong>Anpassad</strong> alternativet är tillgängligt för iOS, Android och Windows-enheter. Innan den här uppdateringen var fältet <strong>Anpassad</strong> endast tillgängligt för iOS-enheter. Mer information finns i [Skapa en SCEP-certifikatprofil](../protect/certificates-profile-scep.md).

När du skapar en PKCS-certifikatprofil för **Alternativt ämnesnamn** är **attributet anpassad Azure AD** tillgängligt. Alternativet **Avdelning** är tillgängligt när du väljer **attributet anpassad Azure AD**. Mer information finns i [skapa en PKCS-certifikatprofil](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode---662059---"></a>Konfigurera flera appar som kan köras när en Android-enhet är i helskärmsläge<!-- 662059 -->
När en Android-enhet är i helskärmsläge, kunde du tidigare endast konfigurera en app som hade tillstånd att köras. Nu kan du konfigurera flera appar med hjälp av app-ID, lagrings-URL eller genom att välja en Android-app som du redan hanterar. Mer information finns i [helskärmsinställningar](../configuration/device-restrictions-android.md#kiosk).

<!-- ########################## -->
## <a name="april-2017"></a>April 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Stöd för hantering av Apples Klassrum-app
Du kan nu hantera iOS Klassrum-app på iPad-enheter. Konfigurera Klassrum-appen på lärarens iPad med rätt klass- och elevinformation, konfigurera sedan elevernas iPad-enheter som är registrerade till en klass, så att du kan kontrollera dem med hjälp av appen.
Mer information finns i [Konfigurera utbildningsinställningar för iOS](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps---621621---"></a>Stöd för hanterade konfigurationsalternativ för Android-appar<!-- 621621 -->
Android-appar i Play Store som har stöd för hanterade konfigurationsalternativ kan nu konfigureras av Intune.  Med hjälp av den här funktionen kan IT-personal visa listan över konfigurationsvärden som stöds av en app, vilket ger ett tydligt gränssnitt som gör det möjligt att konfigurera dessa värden.

### <a name="new-android-policy-for-complex-pins---722069---"></a>Ny Android-princip för komplexa PIN-koder<!-- 722069 -->
Du kan ange den obligatoriska [lösenords](../configuration/device-restrictions-android.md#password)typen Numeriskt avancerat i en Android-enhetsprofil för enheter som kör Android 5.0 och senare.  Använd den här inställningen för att hindra att enhetsanvändare skapar en PIN-kod som innehåller upprepande eller efterföljande siffror, t.ex. 1111 eller 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Ytterligare stöd för Android for Work-enheter
- **Hantera inställningar för lösenord och arbetsprofil**<!-- 612808 -->

  Med den här nya enhetsbegränsningsprincipen för Android for Work kan du nu hantera inställningar för lösenord och arbetsprofil på de Android for Work-enheter som du hanterar.

- **Tillåt datadelning mellan arbetsprofiler och personliga profiler**<!-- 1045102 -->

Den här enhetsbegränsningsprofilen för Android for Work har nu nya alternativ som hjälper dig att konfigurera datadelning mellan arbetsprofiler och personliga profiler.

- **Begränsa kopiera och klistra in mellan arbetsprofiler och personliga profiler**<!-- 1046094 -->

  En ny anpassad enhetsprofil för Android for Work-enheter gör det nu möjligt att begränsa om åtgärderna för att kopiera och klistra in mellan arbetsappar och personliga appar ska vara tillåtna.

Mer information finns i [Enhetsbegränsningar för Android for Work](../configuration/device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices---1057568---"></a>Tilldela branschspecifika appar till iOS- och Android-enheter<!-- 1057568 -->
Du kan nu tilldela branschspecifika appar för [iOS](../apps/lob-apps-ios.md) (.ipa-filer) och [Android](../apps/lob-apps-android.md) (.apk-filer) till användare eller enheter.


### <a name="new-device-policies-for-ios---723774-723815-723826-723830---"></a>Nya enhetsprinciper för iOS<!-- 723774, 723815, 723826, 723830 -->
- **Appar på startskärmen** – Styr vilka appar användarna ser på [startskärmen på sina iOS-enheter](../configuration/ios-device-features-settings.md#home-screen-layout). Den här principen ändrar layouten på startsidan, men distribuerar inga appar.

- **Anslutningar till AirPrint-enheter** – Styr vilka [AirPrint-enheter](../configuration/ios-device-features-settings.md#airprint) (nätverksskrivare) som användarna av iOS-enheter kan ansluta till.

- **Anslutningar till AirPlay-enheter** – Styr vilka [AirPlay-enheter](../configuration/ios-device-features-settings.md) (t.ex. Apple TV) som användarna av iOS-enheter kan ansluta till.

- **Anpassat meddelande på låsskärmen** – Konfigurerar ett anpassat meddelande som ersätter det standardmeddelande som användarna ser på låsskärmen på sina iOS-enheter. Mer information finns i [Aktivera borttappat läge på iOS-enheter](../remote-actions/device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps---723767---"></a>Begränsa push-meddelanden för iOS-appar<!-- 723767 -->
Du kan nu konfigurera följande [aviseringsinställningar](../configuration/ios-device-features-settings.md#app-notifications) för iOS-enheter i en begränsningsprofil för Intune-enheter:

- Aktivera eller inaktivera aviseringar helt för en angiven app.
- Aktivera eller inaktivera aviseringar i aviseringscentret för en angiven app.
- Ange aviseringstypen, antingen **Ingen**, **Banderoll** eller **Modal avisering**.
- Ange om aktivitetsikoner tillåts för den här appen.
- Ange om aviseringsljud tillåts.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously---737837---"></a>Konfigurera iOS-appar för att köras i autonomt enkelappsläge<!-- 737837 -->
Du kan nu använda en Intune-enhetsprofil för att konfigurera iOS-enheter till att köra angivna appar i [autonomt enkelt appläge](../configuration/device-restrictions-ios.md#autonomous-single-app-mode). När det här läget är konfigurerat och appen körs kommer enheten att låsas så att den endast kan köra den appen. Ett exempel på detta är när du konfigurerar en app som gör att användarna kan genomföra ett test på enheten. När appens åtgärder har slutförts, eller om du tar bort principen, återgår enheten till sitt normala tillstånd.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices---723765---"></a>Konfigurera betrodda domäner för e-post och webbläsare på iOS-enheter<!-- 723765 -->
Du kan nu konfigurera följande [domäninställningar](../configuration/device-restrictions-ios.md#domains) i en begränsningsprofil för iOS-enheter:

- **Omarkerade e-postdomäner** – E-postmeddelanden som användaren skickar eller tar emot och som inte matchar de domäner du anger här, markeras som icke tillförlitliga.

- **Hanterade webbdomäner** – Dokument som laddats ned från de webbadresser du anger här betraktas som hanterade (endast Safari).  

- **Fyll i lösenord automatiskt för Safari-domäner** – Användare kan spara lösenord endast i Safari från URL:er som matchar de mönster du anger här. Om du vill använda den här inställningen måste enheten vara i övervakat läge och får inte vara konfigurerad för flera användare. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal---748782---"></a>VPP-appar tillgängliga i iOS-företagsportalen<!-- 748782 -->
Du kan nu tilldela volyminköpsappar för iOS som **Tillgängliga** installationer till användarna. Användarna behöver ett Apple Store-konto för att installera appen.

### <a name="synchronize-ebooks-from-apple-vpp-store---800878---"></a>Synkronisera e-böcker från Apple VPP Store<!-- 800878 -->
Du kan nu [synkronisera böcker](../apps/vpp-apps-ios.md) som du har köpt från Apples butik för volyminköpsappar med Intune och tilldela dem till användarna.

### <a name="multi-user-management-for-samsung-knox-standard-devices---971988---"></a>Hantering av flera användare för Samsung Knox Standard-enheter<!-- 971988 -->
Enheter som kör Samsung Knox Standard har nu stöd för [hantering av flera användare](../enrollment/android-enroll.md) i Intune. Det innebär att slutanvändarna kan logga in och ut från enheten med sina autentiseringsuppgifter för Azure Active Directory, och enheten hanteras centralt oavsett om den används eller inte.  När slutanvändare loggar in så får de tillgång till appar och eventuella principer tillämpas på dem. Alla appdata rensas när användaren loggar ut.

### <a name="additional-windows-device-restriction-settings---818566---"></a>Ytterligare begränsningsinställningar för Windows-enheter<!-- 818566 -->
Vi har lagt till stöd för fler [begränsningsinställningar för Windows-enheter](../configuration/device-restrictions-windows-10.md), t.ex. ytterligare Microsoft Edge-webbläsarstöd, anpassning av enhetens låsskärm, anpassning av startmenyn, bakgrund för Windows Spotlight-sökning och proxyinställningar.

### <a name="multi-user-support-for-windows-10-creators-update---822547---"></a>Stöd för flera användare för Windows 10 Creators Update<!-- 822547 -->
Vi har lagt till stöd för [hantering av flera användare](../enrollment/windows-enroll.md) för enheter som kör Windows 10 Creators-uppdateringen och som är domänanslutna med Azure Active Directory. Det innebär att när olika standardanvändare loggar in på enheten med sina autentiseringsuppgifter för Azure AD, får de alla appar och principer som har tilldelats till deras användarnamn. Användare kan för närvarande inte använda Företagsportalen för självbetjäningsscenarier som att installera appar.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start för Windows 10-datorer<!-- 1004830 -->
En ny [Fresh Start-enhetsåtgärd](../remote-actions/device-fresh-start.md) för Windows 10-datorer finns nu tillgänglig.  När du kör den här åtgärden tas alla appar som har installerats på datorn bort, och datorn uppdateras automatiskt till den senaste Windows-versionen. Detta kan användas för att ta bort förinstallerade OEM-appar som ofta levereras med en ny dator. Du kan konfigurera om användardata ska behållas när den här enhetsåtgärden utförs.

### <a name="additional-windows-10-upgrade-paths---903672---"></a>Ytterligare uppgraderingsvägar i Windows 10<!-- 903672 -->
Nu kan du skapa en [uppgraderingsprincip för utgåvor för att uppgradera enheter](../configuration/edition-upgrade-configure-windows-10.md) till följande Windows 10-utgåvor:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices---747607---"></a>Massregistrera Windows 10-enheter<!-- 747607 -->
Nu kan du ansluta ett stort antal enheter som kör Windows 10 Creators-uppdateringen till Azure Active Directory och Intune med Windows Configuration Designer (WCD). Aktivera [MDM-massregistrering](../enrollment/windows-bulk-enroll.md) för din Azure AD-klient genom att skapa ett konfigurationspaket som ansluter enheter till din Azure AD-klient med hjälp av Windows Configuration Designer. Tillämpa sedan paketet på de företagsägda enheter som du vill massregistrera och hantera. När paketet har tillämpats på dina enheter ansluts de till Azure AD, registreras i Intune och är redo för inloggning av Azure AD-användarna.  Azure AD-användare är standardanvändare på de här enheterna och tar emot tilldelade principer och nödvändiga appar. Självbetjäning och företagsportalscenarier stöds inte för närvarande.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations---581122-736644---"></a>Nya MAM-inställningar för PIN-kod och hanterade lagringsplatser<!-- 581122, 736644 -->
Det finns nu två nya appinställningar som hjälper dig med scenarier för hantering av mobilprogram (MAM):

- **Inaktivera app-PIN när enhets-PIN är hanterad** – Identifierar om det finns en enhets-PIN på den registrerade enheten och förbigår i så fall den app-PIN som utlöses av appskyddsprinciperna. Den här inställningen minskar antalet gånger en PIN-uppmaning visas för användare som öppnar ett MAM-aktiverat program på en registrerad enhet. Den här funktionen är tillgänglig för både Android och iOS.

- **Välj med vilka lagringstjänster företagsdata ska sparas** – Gör det möjligt att ange de lagringsplatser där företagsdata ska sparas. Användare kan spara i valda lagringsplatstjänster, vilket innebär att alla lagringsplatstjänster som inte anges kommer att blockeras.

  Lista över lagringsplatstjänster som stöds:

  - OneDrive
  - Business SharePoint Online
  - Lokal lagring

### <a name="help-desk-troubleshooting-portal---907448---"></a>Supportavdelningens felsökningsportal<!-- 907448 -->
Med den nya [felsökningsportalen](../help-desk-operators.md) kan supportansvariga och Intune-administratörer se användarna och deras enheter, samt utföra åtgärder för att lösa tekniska problem i Intune.

<!-- ########################## -->
## <a name="march-2017"></a>Mars 2017

### <a name="support-for-ios-lost-mode--431695--"></a>Stöd för borttappat läge i iOS<!--431695-->
För iOS 9.3-enheter och senare har Intune lagt till stöd för **Borttappat läge**. Nu kan du låsa en enhet för att förhindra all användning och visa ett meddelande och ett telefonnummer på enhetens låsskärm.

Användaren kommer inte att kunna låsa upp enheten förrän en administratör har inaktiverat borttappat läge. När Borttappat läge har aktiverats kan du använda åtgärden **Hitta enhet** för att visa enhetens geografiska plats på en karta i Intune-konsolen.

Enheten måste vara en företagsägd iOS-enhet, registrerad med DEP, som är i övervakat läge.

Mer information finns i [Vad är Microsoft Intune-enhetshantering](../remote-actions/device-management.md)?

### <a name="improvements-to-device-actions-report--677150--"></a>Förbättringar av rapporten Enhetsåtgärder<!--677150-->
Vi har förbättrat rapporten Enhetsåtgärder för att förbättra dess prestanda. Nu kan du filtrera rapporten efter tillstånd. Exempelvis kan du filtrera rapporten för att endast visa enhetsåtgärder som har slutförts.

### <a name="custom-app-categories--748805--"></a>Anpassade appkategorier<!--748805-->
Du kan nu skapa, redigera och tilldela kategorier för appar som du lägger till i Intune. Kategorier kan för närvarande kan bara anges på engelska.
Läs [How to add an app to Intune](../apps/apps-add.md) (Lägga till en app i Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices--748823--"></a>Tilldela verksamhetsspecifika appar till användare med ej registrerade enheter<!--748823-->
Du kan nu tilldela branschspecifika appar och appar från butiken till användare, oavsett om deras enheter är registrerade i Intune eller inte. Om användarens enhet inte har registrerats i Intune måste användaren gå till företagsportalens webbplats, inte dess app, för att installera den.

### <a name="new-compliance-reports--846671--"></a>Nya efterlevnadsrapporter<!--846671-->
Nu har du efterlevnadsrapporter som ger ditt företags enheters efterlevnadsprofil och låter dig felsöka problem som berör efterlevnad snabbt efter hand som de upptäcks av dina användare. Du kan visa information om

- Övergripande efterlevnadstatus för enheter
- Efterlevnadstatus för en enskild inställning
- Efterlevnadstatus för en enskild princip

Du kan även använda dessa rapporter för att undersöka en individuell enhet på djupet för att se de inställningar och principer som påverkar enheten.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios--951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->
För Intune-konton som skapades efter januari 2017 har Intune aktiverat direktåtkomst till registreringsscenarier i Apple med arbetsflödet Registrera enheter i Azure-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i Azure-portalen. Intune-konton som skapats före januari 2017 behöver migreras vid ett tillfälle innan de här funktionerna finns tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till förhandsversionen.


<!-- ########################## -->
## <a name="february-2017"></a>Februari 2017

### <a name="ability-to-restrict-mobile-device-enrollment--747600-795782--"></a>Möjlighet att begränsa registrering av mobila enheter<!--747600, 795782-->
Intune lägger till nya registreringsbegränsningar som avgör vilka plattformar som mobila enheter ska kunna registrera. Intune skiljer mellan mobilplattformar som iOS, macOS, Android, Windows och Windows Mobile.

- Begränsningen av registrering av mobila enheter begränsar inte registreringen av datorklienter.  
- För iOS och Android finns det ytterligare ett alternativ för att blockera registrering av personligt ägda enheter.

Intune markerar alla nya enheter som personliga såvida inte IT-administratören vidtar åtgärder för att markera dem som företagsägda, vilket beskrivs i [den här artikeln](../enrollment/device-enrollment.md).

### <a name="view-all-actions-on-managed-devices--677150--"></a>Visa alla åtgärder på hanterade enheter<!--677150-->
En ny rapport om __enhetsåtgärder__ visar vem som har utfört fjärråtgärder som fabriksåterställning på enheter, och dessutom visas status för åtgärden. Se [Vad är enhetshantering?](../remote-actions/device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps--664691--"></a>Icke-hanterade enheter kan komma åt tilldelade appar<!--664691-->
Som en del av designändringarna på företagsportalens webbplats ska iOS- och Android-användare kunna installera appar som har tilldelats dem som "tillgänglig utan registrering" på sina icke-hanterade enheter. Med sina Intune-autentiseringsuppgifter kan användare logga in på företagsportalens webbplats och se en lista över appar som tilldelats dem. App-paket för apparna som är "tillgängliga utan registrering" görs tillgängliga för hämtning via företagsportalens webbplats. Appar som kräver registrering för installation påverkas inte av den här ändringen, eftersom användarna uppmanas att registrera sina enheter om de vill installera apparna.

### <a name="custom-app-categories--748805--"></a>Anpassade appkategorier<!--748805-->
Du kan nu skapa, redigera och tilldela kategorier för appar som du lägger till i Intune. Kategorier kan för närvarande kan bara anges på engelska.
Läs [How to add an app to Intune](../apps/apps-add.md) (Lägga till en app i Intune).

### <a name="display-device-categories--814654--"></a>Visa enhetskategorier<!--814654-->
Du kan nu visa enhetskategorin som en kolumn i listan över enheter. Du kan också redigera kategorin från avsnittet med egenskaper på bladet Enhetsegenskaper. Läs [How to add an app to Intune](../apps/apps-add.md) (Lägga till en app i Intune).

### <a name="configure-windows-update-for-business-settings--776716--"></a>Konfigurera inställningar för Windows Update för företag<!--776716-->

Windows som en tjänst är det nya sättet för att tillhandahålla uppdateringar för Windows 10. Från och med Windows 10 innehåller alla nya funktions- och kvalitets även innehållet från alla tidigare uppdateringar. Det innebär att så länge som du har installerat den senaste uppdateringen så vet du att dina Windows 10-enheter är helt uppdaterade. Till skillnad från vad som var fallet i tidigare versioner av Windows måste du nu installera hela uppdateringen i stället för en del av en uppdatering.

Med hjälp av Windows Update för företag kan du förenkla hanteringen av uppdateringar så att du inte behöver godkänna varje enskild uppdatering för enhetsgrupperna. Du kan fortfarande hantera risker i din miljö genom att konfigurera en strategi för uppdateringarna installeras, och Windows Update ser till att uppdateringarna installeras vid rätt tidpunkt. Microsoft Intune ger dig möjlighet att konfigurera enheternas inställningar och att skjuta upp installationen av uppdateringar. Intune lagrar inte uppdateringar, utan enbart uppdateringarnas principtilldelning. Enheterna har direkt åtkomst till uppdateringarna via Windows Update. Använd Intune för att konfigurera och hantera **Windows 10-uppdateringsringar**. En uppdateringsring innehåller en grupp med inställningar som anger när och hur uppdateringar av Windows 10 updates installeras. Mer information finns i [Konfigurera inställningar för Windows Update för företag](../protect/windows-update-for-business-configure.md).
