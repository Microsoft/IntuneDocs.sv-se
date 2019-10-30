---
title: Nyheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Ta reda på vad som är nytt i Intune Azure-portalen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: f32637173ec6cf5f7c284a87193eafffb6a16e6c
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72786134"
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune

Läs mer om varje veckas nyheter i Microsoft Intune. Du kan också hitta [viktiga meddelanden](#notices), [tidigare versioner](whats-new-archive.md) och information om [hur uppdateringar av Intune-tjänsten släpps](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728).

> [!Note]
> Varje [månadsuppdatering](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) kan ta upp till tre dagar att distribuera och sker i följande ordning:
>
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
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  


<!-- ########################## -->

## <a name="week-of-october-21-2019"></a>Veckan då den 21 oktober 2019 infaller

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073-idready-wnready---"></a>Ny gränssnittsprofil för konfiguration av enhetens inbyggda programvara för enheter med Windows 10 och senare <!-- 2266073 idready wnready -->

I Windows 10 och senare kan du skapa en enhetskonfigurationsprofil för att kontrollera inställningar och funktioner (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform). I den här uppdateringen finns en ny typ av gränssnittsprofil för konfiguration av enhetens inbyggda programvara som gör att Intune kan hantera UEFI-inställningar (BIOS).

Mer information om den här funktionen finns i avsnittet om att [använda DFCI-profiler på Windows-enheter i Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

Gäller för:

- Windows 10 RS5 (1809) och senare på inbyggd programvara som stöds

## <a name="week-of-october-14-2019"></a>Veckan då den 14 oktober 2019 infaller

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering 

#### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956-----"></a>Tillgänglig Google Play-apprapportering för Android-arbetsprofiler <!-- 3041956   -->
För tillgängliga appinstallationer på Android Enterprise-enheter för arbetsprofil samt dedikerade och fullständigt hanterade enheter kan du visa appens installationsstatus samt den installerade versionen av hanterade Google Play-appar. Mer information finns i [Så här övervakar du appskyddsprinciper](~/apps/app-protection-policies-monitor.md), [Hantera Android-arbetsprofilenheter med Intune](~/enrollment/android-enterprise-overview.md) och [Hanterade Google Play-apptyper](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview----3872025-4678761----"></a>Microsoft Edge version 77 och senare för Windows 10 och macOS (offentlig förhandsversion) <!-- 3872025, 4678761  -->
Microsoft Edge version 77 och senare är nu tillgänglig för distribution till datorer som kör Windows 10 och macOS. Den offentliga förhandsversionen erbjuder kanalerna **Dev** och **Beta** för Windows 10 och en **Beta-kanal** för macOS. Distributionen är bara på engelska (EN), men slutanvändarna kan ändra visningsspråket i webbläsaren under **Inställningar** > **Språk**. Microsoft Edge är en Win32-app som installeras i systemkontext och på samma arkitektur (x86-appen i x86-operativsystem och x64-appen i x64-operativsystem). Dessutom är automatiska uppdateringar av webbläsaren **På** som standard, och Microsoft Edge kan inte avinstalleras. Mer information finns i avsnittet om att [lägga till Microsoft Edge för Windows 10 till Microsoft Intune](~/apps/apps-windows-edge.md) och i [Microsoft Edge-dokumentationen](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029-----"></a>Uppdatering av användargränssnittet för appskydd och användargränssnittet för etablering av iOS-appar <!-- 4102027, 4102029   -->
Användargränssnittet för skapande och redigering av appskyddsprinciper samt etableringsprofiler för iOS-appar i Intune har uppdaterats. Gränssnittsändringarna omfattar:
- En förenklad upplevelse med hjälp av ett format i guidestil som komprimerats till ett enskilt blad. 
- En uppdatering av skapandeflödet så att tilldelningar inkluderas.
- En sammanfattningssida för alla saker som anges vid visning av egenskaper, innan en ny princip skapas eller när en egenskap redigeras. Vid redigering av egenskaper visar sammanfattningen dessutom bara en lista över objekt från kategorin med de egenskaper som redigeras.

Mer information finns i [Hur du skapar och tilldelar skyddsprinciper för appar](~/apps/app-protection-policies.md) och [Använd iOS-appetableringsprofiler](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios----4850318-4831296-3610611----"></a>Guidade Intune-scenarier <!-- 4850318, 4831296, 3610611  -->
Intune har nu guidade scenarier som hjälper dig att slutföra en specifik uppgift eller uppsättning med uppgifter i Intune. Ett guidat scenario är en anpassad serie med steg (arbetsflöde) som handlar om ett visst användningsfall från slutpunkt till slutpunkt. Vanliga scenarier definieras baserat på den roll som en administratör, användare eller enhet har i din organisation. Dessa arbetsflöden kräver vanligtvis en samling noggrant samordnade profiler, inställningar, program och säkerhetskontroller för att ge bästa möjliga användarupplevelse och säkerhet. Nya guidade scenarier omfattar:
- [Distribuera Microsoft Edge för mobil](~/fundamentals/guided-scenarios-edge.md)
- [Skydda Microsoft Office-mobilappar](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Molnhanterat modernt skrivbord](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

Mer information finns i [översikten av guidade Intune-scenarier](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available----4969237-----"></a>Ytterligare variabel för appkonfiguration är tillgänglig <!-- 4969237   -->
När du skapar en appkonfigurationsprincip kan du inkludera konfigurationsvariabeln `AAD Device ID` som en del av dina konfigurationsinställningar. Gå till Intune och välj **Klientappar** > **Appkonfigurationsprinciper** > **Lägg till**. Ange informationen om konfigurationsprincipen och välj **Konfigurationsinställningar** för att visa bladet **Konfigurationsinställningar**. Mer information finns i avsnittet om [appkonfigurationsprinciper för hanterade Android Enterprise-enheter – Använda Configuration Designer](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Skapa grupper av hanteringsobjekt som kallas principuppsättningar <!-- 3762880  -->
Med principuppsättningar kan du skapa ett paket med referenser till redan befintliga hanteringsenheter som behöver identifieras, riktas och övervakas som en enda begreppsmässig enhet. Principuppsättningar ersätter inte befintliga begrepp eller objekt. Du kan fortsätta att tilldela enskilda objekt i Intune, och du kan referera till enskilda objekt som en del av en principuppsättning. Det innebär att alla ändringar av de enskilda objekten avspeglas i principuppsättningen.  I Intune väljer du **Principuppsättningar** > **Skapa** för att skapa en ny principuppsättning. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089-----------"></a>Uppdatering av användargränssnittet för skapande och redigering av Windows 10-uppdateringsringar  <!-- 4099089         -->
Vi har uppdaterat gränssnittsupplevelsen för [skapande och redigering av Windows 10-uppdateringsringar](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) för Intune. Ändringar i användargränssnittet är följande:  
- Ett format i guidestil med en mall som är komprimerad till ett enda konsolblad så att du slipper mängden med blad när du konfigurerar uppdateringsringar.   
- Det ändrade arbetsflödet omfattar Tilldelningar före slutförandet av ringens första konfiguration.
- En sammanfattningssida där du kan granska alla konfigurationer som du har gjort innan du sparar och distribuerar en ny uppdateringsring. Vid redigering av en uppdateringsring visar sammanfattningen endast listan över objekt som har angetts i kategorin med egenskaper som du redigerade.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy-----4099090---------"></a>Uppdatering av användargränssnittet för skapande och redigering av iOS-programuppdateringsprinciper  <!-- 4099090       --> 
Vi har uppdaterat gränssnittsupplevelsen för [skapande](../protect/software-updates-ios.md#configure-the-policy) och [redigering](../protect/software-updates-ios.md#edit-a-policy) av iOS-programuppdateringsprinciper för Intune.  Ändringar i användargränssnittet är följande:  
- Ett format i guidestil med en mall som är komprimerad till ett enda konsolblad så att du slipper mängden med blad när du konfigurerar uppdateringsprinciper.   
- Det ändrade arbetsflödet omfattar Tilldelningar före slutförandet av principens första konfiguration.
- En sammanfattningssida där du kan granska alla konfigurationer som du har gjort innan du sparar och distribuerar en ny princip. Vid redigering av en princip visar sammanfattningen endast listan över objekt som har angetts i kategorin med egenskaper som du redigerade.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings------4464404---wnready-----"></a>Inställningarna för interaktiv omstart tas bort från Windows-uppdateringsringar  <!--  4464404   WNReady   -->
Som tidigare har meddelats har Intunes Windows 10-uppdateringsringar nu [stöd för inställningar för tidsgränser](../protect/windows-update-settings.md) och stöder inte längre *interaktiv omstart*. Inställningarna för *interaktiv omstart* är inte längre tillgängliga när du konfigurerar eller hanterar uppdateringsringar i Intune.  

Den här ändringen stämmer överens med nyliga [Windows Servicing-ändringar](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) och på enheter som kör Windows 10 1903 eller senare ersätter *tidsgränser* konfigurationer för *interaktiv omstart*.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices----4760025-----"></a>Förhindra installation av appar från okända källor på Android Enterprise-arbetsprofilenheter <!-- 4760025   -->
På Android Enterprise-arbetsprofilenheter kan användarna aldrig installera appar från okända källor. I den här uppdateringen finns det en ny inställning – **Förhindra appinstallationer från okända källor i den personliga profilen**. Som standard förhindrar den här inställningen att användare läser in appar från okända källor till den personliga profilen på enheten.

Om du vill se den inställning som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:
- Android Enterprise-arbetsprofil

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339-----"></a>Skapa en global HTTP-proxy på Android Enterprise-enhetsägarenheter <!-- 4816339   -->
På Android Enterprise-enheter kan du konfigurera en global HTTP-proxy som uppfyller organisationens webbläsarstandarder (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Enhetsägare > Enhetsbegränsningar** för profiltyp > **Anslutningar**). Efter konfiguration använder all HTTP-trafik denna proxy.

Om du vill konfigurera den här funktionen och se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:
- Android Enterprise-enhetsägare

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise----5021055-----"></a>Inställningen för automatisk anslutning tas bort från Wi-Fi-profiler på Android-enhetsadministratör och Android Enterprise <!-- 5021055   -->
På Android-enhetsadministratör och Android Enterprise-enheter kan du skapa en Wi-Fi-profil för att konfigurera olika inställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android-enhetsadministratör** eller **Android Enterprise** för plattform > **Wi-Fi** för profiltyp). I den här uppdateringen tas inställningen **Anslut automatiskt** bort eftersom den [inte stöds av Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Om du använder den här inställningen i en Wi-Fi-profil har du kanske märkt att **Anslut automatiskt** inte fungerar. Du behöver inte vidta några åtgärder, men tänk på att den här inställningen tas bort från användargränssnittet i Intune.

Om du vill se de aktuella inställningarna går du till [Wi-Fi-inställningar för Android](../configuration/wi-fi-settings-android.md) eller [Wi-Fi-inställningar för Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

Gäller för:
- Android-enhetsadministratör 
- Android enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328-----"></a>Nya enhetskonfigurationsinställningar för övervakade iOS- och iPadOS-enheter <!-- 5199328   -->
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

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697-----"></a>Ange vilka operativsystemversioner för Android-enheter som registreras via registrering med arbetsprofil eller enhetsadministratör <!-- 4350697   -->
Med hjälp av begränsningar för Intune-enhetstyp kan du använda enhetens OS-version för att ange vilka användarenheter som ska använda registrering med Android Enterprise-arbetsprofil eller registrering med Android-enhetsadministratör.  Mer information finns i [Konfigurera registreringsrestriktioner](../enrollment/enrollment-restrictions-set.md).

#### <a name="windows-autopilot-deployment-reports----3856172---"></a>Windows Autopilot-distributionsrapporter <!-- 3856172 -->
En ny rapport innehåller information om varje enhet som distribueras via Windows Autopilot. Mer information finns i [distributionsrapporten för Autopilot](../enrollment/enrollment-autopilot.md#autopilot-deployments-report). Vi håller på att lansera den här funktionen till alla kunder och förväntar oss att bli klara i slutet av nästa vecka.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="new-restrictions-for-renaming-windows-devices----3478938----"></a>Nya begränsningar för namnbyte av Windows-enheter <!-- 3478938  -->
När du byter namn på en Windows-enhet måste du följa nya regler:
- 15 tecken eller mindre (måste vara mindre än eller lika med 63 byte exklusive avslutande NULL)
- Inte null eller en tom sträng
- Tillåten ASCII: Bokstäver (a–z, A–Z), siffror (0–9) och bindestreck
- Tillåten Unicode: tecken > = 0x80, måste vara en giltig UTF8, måste vara IDN-mappningsbara (det vill säga att RtlIdnToNameprepUnicode lyckas; se RFC 3492)
- Namn får inte enbart innehålla siffror
- Inga blanksteg i namnet
- Förbjudna tecken: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 Mer information finns i [Ändra namn på en enhet i Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page----4924364---"></a>Ny Android-rapport på sidan med enhetsöversikt <!-- 4924364 -->
En ny rapport på sidan med enhetsöversikt visar hur många Android-enheter som har registrerats i varje enhetshanteringslösning. Det här diagrammet visar antal arbetsprofilenheter samt fullständigt hanterade, dedikerade och enhetsadministratörsregistrerade enheter. Om du vill se rapporten väljer du **Intune** > **Enheter** > **Översikt**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet 

#### <a name="pkcs-certificates-for-macos-----1333650---------"></a>PKCS-certifikat för macOS  <!-- 1333650       -->
Nu kan du [använda PKCS-certifikat med macOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). Du kan välja PKCS-certifikatet som en profiltyp för macOS och distribuera användar- och enhetscertifikat som har [anpassade ämnesnamnfält och alternativa ämnesnamnfält](../protect/certficates-pfx-configure.md#subject-name-format-for-macos).  

PKCS-certifikat för macOS har även stöd för en ny inställning, _Ge alla appar åtkomst_. Med den här inställningen kan du ge alla associerade appar åtkomst till den privata nyckeln för certifikatet.  Mer information om den här inställningen finns i Apple-dokumentationen på https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----------1736036-1736037-1772050-2777333-----------"></a>Härledda autentiseringsuppgifter för etablering av mobila iOS-enheter med certifikat      <!--  1736036, 1736037, 1772050, 2777333         -->  
Intune stöder användning av [härledda autentiseringsuppgifter](../protect/derived-credentials.md) som autentiseringsmetod samt för S/MIME-signering och -kryptering för iOS-enheter. Härledda autentiseringsuppgifter är en implementering av standarden *National Institute of Standards and Technology (NIST) 800-157* för distribution av certifikat till enheter.  

Härledda autentiseringsuppgifter är beroende av att ett PIV-kort (Personal Identity Verification) eller ett CAC-kort (Common Access Card) används, till exempel ett smartkort. För att få en härledd autentiseringsuppgift för sin mobila enhet börjar användare i Företagsportal-appen och följer ett registreringsarbetsflöde som är unikt för den provider som du använder.  Gemensamt för alla providrar är kravet på användning av ett smartkort på en dator för autentisering till providern för den härledda autentiseringsuppgiften. Providern utfärdar sedan ett certifikat till den enhet som härleds från användarens smartkort.  

Intune stöder följande providrar för härledda autentiseringsuppgifter:   
- DISA Purebred
- Entrust Datacard
- Intercede

Du använder härledda autentiseringsuppgifter som autentiseringsmetod för enhetskonfigurationsprofiler för VPN, Wi-Fi och e-post. Du kan även använda dem för appautentisering samt för S/MIME-signering och -kryptering.  

Mer information om standarden finns i [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) (Härledda PIV-autentiseringsuppgifter) på www.nccoe.nist.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates--------5437939----------"></a>Använd Graph API för att ange ett lokalt användarhuvudnamn som en variabel för SCEP-certifikat    <!--  5437939        -->  
När du använder [Intune-Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) kan du ange onPremisesUserPrincipalName som en variabel för SAN (alternativt namn för certifikatmottagare) för SCEP-certifikat.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Veckan då den 23 september 2019 infaller

#### <a name="ios-user-enrollment-in-preview----4817900---"></a>Användarregistrering i iOS i förhandsversion <!-- 4817900 -->
Lanseringen av Apples iOS 13.1 inkluderar användarregistrering, en ny form av lätt hantering av iOS-enheter. Den kan användas i stället för enhetsregistrering eller automatisk enhetsregistrering (tidigare Programmet för enhetsregistrering) för personliga enheter. Intunes förhandsversion har stöd för den här funktionen genom att låta dig göra följande:

- Målanvändarregistrering för användargrupper.
- Ge slutanvändarna möjlighet att välja mellan lättare användarregistrering eller starkare enhetsregistrering när de registrerar sina enheter.

Starting on 9/24/2019 with the release of iOS 13.1, we're in the process of rolling out these updates to all customers and expect to be completed by the end of next week.
Gäller för:

iOS 13.1 och senare

#### <a name="intune-support-for-ipados-and-ios-131-devices---5439574--"></a>Intune-stöd för enheter med iPadOS och iOS 13.1 <!--5439574-->
Intune har nu stöd för enheter med såväl iPadOS som iOS 13.1. Mer information finns i [det här blogginlägget](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>Veckan då den 16 september 2019 infaller

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering 

#### <a name="managed-google-play-private-lob-apps----1464182----"></a>Privata LOB-appar för Hanterat Google Play-konto <!-- 1464182  -->
Intune tillåter nu IT-administratörer att publicera privata Android LOB-appar till Hanterat Google Play-konto via en iframe inbäddad i Intune-konsolen.  Tidigare behövde IT-administratörer publicera LOB-appar direkt till Googles Play-publiceringskonsol, vilket krävde flera steg och tog lång tid. Med den här nya funktionen kan du enkelt publicera LOB-appar med en minimal uppsättning steg, utan att behöva lämna Intune-konsolen.  Administratörer behöver inte längre manuellt registrera sig som utvecklare hos Google och behöver inte längre betala Google-registreringsavgiften på 25 USD.  Alla Android Enterprise-hanteringsscenarier som använder Hanterat Google Play-konto kan dra nytta av den här funktionen (arbetsprofilenheter och dedikerade, fullständigt hanterade samt icke-registrerade enheter). I Intune väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **Hanterat Google Play-konto** i listan **Apptyp**. Mer information om Managed Google Play-appar finns i [Lägga till Managed Google Play-appar till Android Enterprise-enheter med Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience----1473353-3598357---"></a>Gränssnittet för Företagsportal i Windows <!-- 1473353, 3598357 -->
Företagsportal i Windows uppdateras. Du kommer att kunna använda flera filter på sidan Appar i Företagsportal i Windows. Sidan Enhetsinformation uppdateras också med ett förbättrat användargränssnitt. Vi håller på att lansera dessa uppdateringar för alla kunder och förväntar oss att blir klara i slutet av nästa vecka.

#### <a name="macos-support-for-web-apps----3174427---"></a>macOS-stöd för webbappar <!-- 3174427 -->
Webbappar, som gör att du kan lägga till en genväg till en URL på webben, kan installeras på Dock med hjälp av Företagsportal i macOS. Slutanvändare kan komma åt **installationsåtgärden** via appinformationssidan för en webbapp i Företagsportal i macOS. Mer information om apptypen **Webblänk** finns i [Lägga till appar i Microsoft Intune](../apps/apps-add.md) och [Lägga till webbappar i Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps----3173501----"></a>macOS-stöd för VPP-appar <!-- 3173501  -->
macOS-appar som köpts via Apple Business Manager visas i konsolen när Apple VPP-token synkroniseras i Intune. Du kan tilldela, återkalla och omtilldela enhets- och användarbaserade licenser för grupper med hjälp av Intune-konsolen. Med Microsoft Intune kan du hantera VPP-appar som köpts för användning i företaget genom att:

- Rapportera licensinformation från App Store.
- Spåra antalet använda licenser.
- Hjälpa dig att förhindra installation av fler exemplar av en app än du äger.

Mer information om Intune och VPP, finns i [Hantera volyminköpta appar och böcker med Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support----2871756----"></a>iframe-stöd för Hanterat Google Play-konto <!-- 2871756  -->
Intune har nu stöd för att lägga till och hantera webblänkar direkt i Intune-konsolen via iframe för Hanterat Google Play-konto.  Det här gör att IT-administratörer kan skicka en URL och ikonbild, och sedan distribuera dessa länkar till enheter precis som vanliga Android-appar. Alla Android Enterprise-hanteringsscenarier som använder Hanterat Google Play-konto kan dra nytta av den här funktionen (arbetsprofilenheter och dedikerade, fullständigt hanterade samt icke-registrerade enheter). I Intune väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **Hanterat Google Play-konto** i listan **Apptyp**. Mer information om appar för Hanterat Google Play-konto finns i [Lägga till appar för Google Play-konto till Android Enterprise-enheter med Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices----4252734----"></a>Installera Android LOB-appar obevakat på Zebra-enheter <!-- 4252734  -->
När du installerar verksamhetsspecifika (LOB) Android-appar på [Zebra-enheter](../configuration/android-zebra-mx-overview.md) kan du, i stället för att uppmanas att både ladda ned och installera LOB-appen, installera appen obevakat. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. I fönstret **Lägg till app** väljer du **Branschspecifik app**. Mer information finns i [Lägg till en verksamhetsspecifik app för Android i Microsoft Intune](../apps/lob-apps-android.md).

När LOB-appen har laddats ned visas ett meddelande om **utförd nedladdning** på användarens enhet. Meddelandet kan bara stängas genom att trycka på **Rensa alla** i meddelandeskuggan. Det här aviseringsproblemet kommer att åtgärdas i en kommande version och installationen kommer att vara helt obevakad utan några visuella indikatorer.

#### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Läsa och skriva Graph API-åtgärder för Intune-appar <!-- 5031704  -->
Appar kan anropa Intune Graph API med både läs- och skrivåtgärder med hjälp av appidentitet utan användarens autentiseringsuppgifter. Mer information om hur du kommer åt Microsoft Graph API för Intune finns i [Arbeta med Intune i Microsoft Graph.](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios----3586942----"></a>Delning och kryptering av skyddade data för Intune App SDK för iOS <!-- 3586942  -->
Intune App SDK för iOS använder 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciper. Alla appar måste vara i SDK-version 8.1.1 för att delning av skyddade data ska vara möjlig.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438-----"></a>Stöd för IKEv2 VPN-profiler för iOS <!-- 1943438   -->
I den här uppdateringen kan du skapa VPN-profiler för den iOS-inbyggda VPN-klienten med hjälp av IKEv2-protokoll. IKEv2 är en ny anslutningstyp i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **VPN** för profiltyp > **Anslutningstyp**.

Dessa VPN-profiler konfigurerar den inbyggda VPN-klienter, så att inga VPN-klientappar installeras på eller flyttas till hanterade enheter. Den här funktionen kräver att enheter registreras i Intune (MDM-registrering).

Om du vill se de aktuella VPN-inställningarna som du kan konfigurera går du till [Konfigurera VPN-inställningar på iOS-enheter](../configuration/vpn-settings-ios.md).

Gäller för:
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161-----"></a>Enhetsfunktioner, enhetsbegränsningar och tilläggsprofiler för iOS- och macOS-inställningar visas efter registreringstyp <!-- 4886161   -->

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

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835-----"></a>Nya röstkontrollinställningar för övervakade iOS-enheter som körs i helskärmsläge <!-- 4892835   -->
I Intune kan du skapa principer för att köra övervakade iOS-enheter som en kioskenhet eller dedikerad enhet (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Helskärm**). 

I den här uppdateringen finns det nya inställningar du kan styra:
- **Röststyrning**: Aktiverar röststyrning på enheten i helskärmsläge.
- **Ändring av röststyrning**: Tillåt användare att ändra inställningen för Röststyrning på enheten i helskärmsläge.

Om du vill se de aktuella inställningarna går du till [inställningar för iOS i helskärmsläge](../configuration/device-restrictions-ios.md#kiosk).

Gäller för:
- iOS 13.0 och senare

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175-----"></a>Använda enkel inloggning för appar och webbplatser på iOS- och macOS-enheter <!-- 4893175   -->
I den här uppdateringen finns det några inställningar för enkel inloggning för iOS- och macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **macOS** för plattform > **Enhetsfunktioner** för profiltyp).

Använd de här inställningarna till att konfigurera funktioner för enkel inloggning, särskilt för appar och webbplatser som använder Kerberos-autentisering. Du kan välja mellan ett tillägg för enkel inloggning med generiska autentiseringsuppgifter, och Apples inbyggda Kerberos-tillägg.

Om du vill se de aktuella enhetsfunktionerna du kan konfigurera går du till [iOS-enhetsfunktioner](../configuration/ios-device-features-settings.md) och [macOS-enhetsfunktioner](../configuration/macos-device-features-settings.md).

Gäller för:
- iOS 13.0 och senare
- macOS 10.15 och senare

#### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079-----"></a>Associera domäner med appar på macOS 10.15+-enheter <!-- 4898079   -->
På macOS-enheter kan du konfigurera olika funktioner, flytta funktionerna till dina enheter med hjälp av en princip (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsfunktioner** för profiltyp). I den här uppdateringen kan du associera domäner med dina appar. Den här funktioner hjälper till att dela autentiseringsuppgifter med webbplatser relaterade till din app och kan användas med Apples tillägg för enkel inloggning, universella länkar och automatisk ifyllning av lösenord. 

Om du vill visa de aktuella funktionerna du kan konfigurera går du till [Funktionsinställningar för macOS-enheter i Intune](../configuration/macos-device-features-settings.md).

Gäller för:
- macOS 10.15 och senare

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474-----"></a>Använd ”iTunes” och ”apps” i iTunes App Store-URL när du visar eller döljer appar på iOS-övervakade enheter <!-- 4928474   --> 
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

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access-------4092920---"></a>Uppdaterat användargränssnitt för att konfigurera åtkomst till Microsoft Exchange lokalt    <!-- 4092920 -->  
Vi har uppdaterat konsolen där du [konfigurerar åtkomst till Microsoft Exchange lokalt](../protect/conditional-access-exchange-create.md). Alla konfigurationer för åtkomst till Exchange lokalt är nu tillgängliga i samma fönster i konsolen där du *aktiverar åtkomstkontroll för Exchange lokalt*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices----1109650----"></a>Tillåta eller begränsa tillägg av appwidgetar på startskärmen på Android Enterprise-arbetsprofilenheter <!-- 1109650  --> 
På Android Enterprise-enheter kan du konfigurera funktioner i arbetsprofilen (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast arbetsprofil > Enhetsbegränsningar** för profiltyp). I den här uppdateringen kan du tillåta användare att lägga till widgetar exponerade av arbetsprofilappar till enhetens startskärm.

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:
- Android Enterprise-arbetsprofil

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790-----"></a>Nya klientorganisationer använder som standard inte Android-enhetsadministratörshantering <!-- 4869790   -->
Androids enhetsadministratörsfunktioner har ersatts av Android Enterprise. Vi rekommenderar därför att du använder Android Enterprise för nya registreringar i stället. I en framtida uppdatering måste nya klientorganisationer slutföra följande nödvändiga steg i Android-registrering för att använda enhetsadministratörshantering: Gå till **Intune** > **Enhetsregistrering** > **Android-registrering** > **Personal and corporate-owned devices with device administration privileges** (Personliga och företagsägda enheter med enhetsadministratörsbehörighet)  > **Use device administrator to manage devices** (Använd enhetsadministratör för att hantera enheter).

Befintliga klienter får ingen förändring i sina miljöer. 

Mer information om Android-enhetsadministratör i Intune finns i [Administratörsregistrering för Android-enhet](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile----5012045-idmiss---"></a>Lista över DEP-enheter associerade med en profil <!-- 5012045 idmiss -->
Du kan se en sidindelad lista över Apple DEP-enheter (programmet för enhetsregistrering) som är associerade med en profil. Du kan söka i listan från valfri sida i listan. Om du vill se listan går du till **Intune** > **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram** > välja en token > **Profiler** > välja en profil > **Tilldelade enheter** (under **Övervaka**). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="more-android-fully-managed-support----3464667-4631425-4631440-5227935-4062195-----"></a>Mer support för fullständigt hanterade Android-enheter <!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
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

#### <a name="send-custom-notifications-to-a-single-device-----4928910---"></a>Skicka meddelanden till en enskild enhet  <!-- 4928910 -->
Du kan nu välja en enskild enhet och sedan använda en fjärrenhetsåtgärd för att [skicka ett anpassat meddelande till bara den enheten](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment----4950491---"></a>Åtgärderna för rensning och lösenordsåterställning är inte tillgängliga för iOS-enheter som har registrerats med användarregistrering <!-- 4950491 -->
Användarregistrering är en ny typ av Apple-enhetsregistrering. När du registrerar enheter med användarregistrering är fjärråtgärderna för rensning och lösenordsåterställning inte tillgängliga för sådana enheter.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices----4665317---"></a>Intune-stöd för iOS 13- och macOS Catalina-enheter <!-- 4665317 -->
Intune stöder nu hantering av både iOS 13- och macOS Catalina-enheter. Mer information finns i [blogginlägget om Microsoft Intune-stöd iOS 13 och iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation-------3444125---"></a>BitLocker-stöd för klientbaserad rotering av återställningslösenord   <!--  3444125 -->
Använd Intune Endpoint Protection-inställningar för att konfigurera [Klientbaserad rotering av återställningslösenord](../protect/endpoint-protection-windows-10.md#windows-encryption) för BitLocker på enheter som kör Windows version 1909 eller senare.

Den här inställningen initierar en klientbaserad uppdatering av återställningslösenord efter återställning av en operativsystemenhet (med bootmgr eller WinRE) och upplåsning av återställningslösenord på en fast dataenhet. Den är inställningen uppdaterar det specifika återställningslösenordet som har använts och andra oanvända lösenord på volymen förblir oförändrade. Mer information finns i BitLocker CSP-dokumentationen för [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus-----4705448----------"></a>Manipulationsskydd för Windows Defender Antivirus  <!-- 4705448        -->
Använd Intune för att hantera *Manipulationsskydd* för Windows Defender Antivirus. Du hittar [inställningen för Manipulationsskydd](../protect/endpoint-protection-windows-10.md#windows-defender-security-center) i Microsoft Defender Säkerhetscenter-gruppen när du använder enhetskonfigurationsprofiler för Windows 10-slutpunktsskydd. Du kan ställa in manipulationsskydd på *Aktiverad* för att aktivera begränsningar för manipulationsskydd, *Inaktiverad* för att stänga av dem eller *Inte konfigurerad* för att lämna en enhetskonfiguration på plats.  

Mer information om Manipulationsskydd finns i [Prevent security settings changes with tamper protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) (Förhindara ändringar av säkerhetsinställningar med manipulationsskydd) i Windows-dokumentationen. 

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available-----5317392---------"></a>Avancerade inställningar för Windows Defender-brandväggen är nu allmänt tillgängliga <!--  5317392       -->  
De [anpassade brandväggsreglerna för slutpunktsskydd i Windows Defender](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), som du konfigurerar som en del av en enhetskonfigurationsprofil är inte längre en offentlig förhandsversion, utan är allmänt tillgängliga.  Du kan använda de här reglerna för att ange beteende för inkommande och utgående trafik till program, nätverksadresser och portar. Reglerna släpptes i juli som offentlig förhandsversion. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-now-support-terms-of-use-policies----2358863-idmiss---"></a>Omfångstaggar stöder nu principer för användningsvillkor <!-- 2358863 idmiss -->
Nu kan du tilldela [omfångstaggar](scope-tags.md) till principer för användningsvillkor. Det gör du genom att gå till **Intune** > **Enhetsregistrering** > **Villkor** > välj ett objekt i listan > **Egenskaper** > **Omgångstaggar** > välja en omfångstagg.

## <a name="week-of-september-9-2019"></a>Veckan då den 9 september 2019 infaller

### <a name="app-management"></a>Apphantering

#### <a name="updates-to-microsoft-intune-app----4997846---"></a>Uppdateringar av Microsoft Intune-appen <!-- 4997846 -->
Microsoft Intune-appen för Android har uppdaterats med följande förbättringar:
- Uppdaterad och förbättrad layout som inkluderar navigering i nederkant för de viktigaste åtgärderna.
- Ytterligare en sida har lagts till som visar användarens profil.
- Visning av interaktiva meddelanden i appen för användaren har lagts till, exempelvis om enhetsinställningarna behöver uppdateras.
- Visning av anpassade push-meddelanden har lagts till, vilket ger appen samma stöd som nyligen lagts till i företagsportalappen för iOS och Android. Du hittar mer information i [Skicka anpassade meddelanden i Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993---"></a>För iOS-enheter anpassar du registreringsprocessens sekretessida i Företagsportal <!-- 4394993 -->
Med Markdown kan du anpassa sekretessidan i Företagsportal som slutanvändare ser vid iOS-registrering. Mer specifikt kan du anpassa listan med saker som organisationen inte kan se eller göra på enheten. Mer information finns i [Så konfigurerar du appen Intune-företagsportal](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Veckan då den 2 september 2019 infaller

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="intune-user-interface-update--tenant-status-dashboard-----5273210----"></a>Uppdatering av Intunes användargränssnitt – Instrumentpanel för klientorganisationsstatus  <!-- 5273210  -->
Användargränssnittet för instrumentpanelen med klientorganisationsstatus har uppdaterats så att den överensstämmer med Azures användargränssnitt. Mer information finns i [Klientorganisationsstatus](../tenant-status.md).


## <a name="week-of-august-26-2019"></a>Den vecka som börjar 26 augusti 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer----5228061---"></a>Konfigurera Microsoft Edge-inställningar med hjälp av administrativa mallar för Windows 10 och senare <!-- 5228061 -->

På enheter med Windows 10 och senare kan du skapa administrativa mallar för att konfigurera grupprincipinställningar i Intune. I den här uppdateringen kan du konfigurera inställningar som gäller för Microsoft Edge version 77 och senare.

Mer information om administrativa mallar finns i [Använda Windows 10-mallar för att konfigurera grupprincipinställningar i Intune](../configuration/administrative-templates-windows.md).

Gäller för:

- Windows 10 och senare (Windows RS4 +)

## <a name="week-of-august-12-2019"></a>Veckan 12 augusti 2019

### <a name="app-management"></a>Apphantering

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144-----"></a>Kontroll av avinstallationsbeteende för iOS-app vid avregistrering av enhet <!-- 3504144   -->
Administratörer kan hantera om en app tas bort eller sparas på en enhet när enheten avregistreras på en användare- eller enhetsgruppnivå. 

#### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Kategorisera appar i Microsoft Store för företag <!-- 3926922 -->
Du kan kategorisera appar i Microsoft Store för företag. Om du vill göra det väljer du **Intune** > **Klientappar** > **Appar** > Välj en Microsoft Store för företag-app > **Appinformation** > **Kategori**. I den nedrullningsbara menyn tilldelar du en kategori.

#### <a name="customized-notifications-for-microsoft-intune-app-users----4843354----"></a>Anpassade meddelanden för Microsoft Intune-appanvändare <!-- 4843354  -->
Microsoft Intune-appen för Android har nu stöd för visning av anpassade push-meddelanden, tillsammans med stödet som nyligen lagts till i företagsportalappar för iOS och Android. Du hittar mer information i [Skicka anpassade meddelanden i Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946-----"></a>Nya funktioner för dedikerade Android Enterprise-enheter i läge för flera appar <!-- 3755304 3041943 3041946   -->

I Intune kan du styra funktioner och inställningar i ett helskärmsläge på dina dedikerade Android Enterprise-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetsägare, enhetsbegränsningar** för profiltyp).

I den här uppdateringen läggs följande funktioner till:

- **Dedikerade enheter** > **Multi-app**: Den **virtuella hemknappen** kan visas genom att svepa upp på enheten eller flyta på skärmen så att användarna kan flytta den.
- **Dedikerade enheter** > **Multi-app**: Med **Åtkomst till ficklampa** kan användare använda ficklampan. 
- **Dedikerade enheter** > **Multi-app**: **Kontroll av medievolym** gör att användare kan kontrollera enhetens medievolym med ett skjutreglage. 
- **Dedikerade enheter** > **Multi-app**:  **Aktivera en skärmsläckare**, ladda upp en anpassad avbildning och kontrollera när skärmsläckaren visas.

Om du vill se aktuella inställningar, går du till [Inställningar för Android Enterprise-enheter som tillåter eller begränsar funktioner med Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Gäller för:

- Dedikerade Android Enterprise-enheter

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215-3574238-3574235-3574232-----"></a>Ny app och konfigurationsprinciper för fullständigt hanterade Android Enterprise-enheter <!-- 3574215 3574238 3574235 3574232   -->
Med hjälp av profiler kan du konfigurera inställningar som tillämpar VPN-, e-post- och Wi-Fi-inställningar till dina ägare av Android Enterprise-enheter (fullständigt hanterade). I den här uppdateringen kan du:

- Använd [konfigurationsprinciper för appar](../apps/app-configuration-policies-use-android.md) för att distribuera Outlook, Gmail och nio e-postinställningar.
- Använd enhetskonfigurationsprofiler för att distribuera [inställningar för betrodda rotcertifikat](../protect/certificates-configure.md).
- Använd enhetskonfigurationsprofiler för att distribuera inställningar för [VPN](../configuration/vpn-settings-android-enterprise.md) och [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md).

> [!IMPORTANT]
> Med den här funktionen autentiseras användare med sitt användarnamn och lösenord för VPN-, Wi-Fi- och e-postprofiler. Certifikatbaserad autentisering är för närvarande inte tillgängligt.

Gäller för:  
- Ägare av Android Enterprise-enhet (helt hanterad)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices---3914202-----"></a>Kontrollera appar, filer, dokument och mappar som öppnas när användare loggar in på macOS-enheter <!--3914202   -->
Du kan aktivera och konfigurera funktioner på macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsfunktioner** för profiltyp). 

I den här uppdateringen har du en ny inställning för inloggningsobjekt som styr vilka appar, filer, dokument och mappar som öppnas när en användare loggar in till den registrerade enheten. 

Om du vill visa de aktuella inställningarna går du till [Funktionsinställningar för macOS-enheter i Intune](../configuration/macos-device-features-settings.md).

Gäller för:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings------4464404----------"></a>Tidsgränser ersätter inställningarna för interaktiv omstart för Windows-uppdateringsringar   <!-- 4464404        -->
För att justera med de senaste [ändringarna i Windows-underhåll](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing) har Intunes Windows 10-uppdateringsringar nu [stöd för inställningar för tidsgränser](../protect/windows-update-settings.md). *Tidsgränser* fastställer när en enhet installerar funktions- och säkerhetsuppdateringar.  På enheter som kör Windows 10 1903 eller senare ersätter *tidsgränser* konfigurationerna för *interaktiv omstart*.  I framtiden kommer *tidsgränser* att ersätta *interaktiv omstart* på tidigare versioner av Windows 10 också.  

När du inte konfigurerar *tidsgränser* fortsätter enheterna att använda sina inställningar för *interaktiv omstart*, men Intune kommer att ha stöd för inställningar för interaktiv omstart i en framtida uppdatering.  

Planera att använda *tidsgränser* för alla dina Windows 10-enheter. När inställningarna för *tidsgränser* är på plats kan du ändra Intune-konfigurationerna för *interaktiv omstart* till Inte konfigurerad. När den är inställd på Inte konfigurerad, slutar Intune att hantera inställningarna på enheter, men tar inte bort de senaste konfigurationerna för inställningen från enheten. Därför förblir de senaste konfigurationerna som ställts in för *interaktiv omstart* aktiva och används på enheter tills inställningarna har ändrats via en annan metod än Intune. Senare, när enhetsversionen av Windows ändras eller när Intune-stöd för *tidsgränser* expanderar till enhetens Windows-version, börjar enheten att använda de nya inställningarna, som redan finns på plats.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors--------4704642--------"></a>Stöd för flera Microsoft Intune Certificate Connectors   <!--   4704642      -->
Intune har nu stöd för installation och användning av flera [Microsoft Intune Certificate Connectors för PKCS-åtgärder](../protect/certficates-pfx-configure.md). Den här ändringen stöder belastningsutjämning och hög tillgänglighet för anslutningen. Varje anslutningsinstans kan bearbeta certifikatbegäranden från Intune.  Om en anslutning inte är tillgänglig fortsätter andra anslutningar att bearbeta begäranden. 

Om du vill använda flera anslutningar behöver du inte uppgradera till den senaste versionen av anslutningsprogrammet.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709-----"></a>Nya inställningar och ändringar i befintliga inställningar för att begränsa funktionerna på iOS-och macOS-enheter <!-- 4867699 4867709   -->
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

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809-----"></a>Vissa begränsningar för iOS-enheter som inte övervakas kommer att bli övervakade – endast med iOS 13.0-versionen <!-- 4867809   -->
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

#### <a name="improved-device-status-for-macos-filevault-encryption-----4944983-----------"></a>Förbättrad enhetsstatus för macOS FileVault-kryptering  <!-- 4944983         -->
Vi har uppdaterat flera [enhetsstatusmeddelanden](../protect/encryption-monitor.md#device-encryption-status) för FileVault-kryptering på MacOS-enheter.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status----5119229---"></a>Vissa inställningar för Windows Defender Antivirus-genomsökning i rapporten visar felaktig status <!-- 5119229 -->
I Intune kan du skapa principer för att använda Windows Defender Antivirus för att söka igenom dina Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp > **Windows Defender Antivirus**). Rapporter om **tid det tar att utföra en daglig snabbsökning** och **typ av systemgenomsökning som ska utföras** visar statusen Misslyckad, när det faktiskt är en lyckad status. 

I den här uppdateringen ändras detta beteende. Det innebär att inställningarna **tid det tar att utföra en daglig snabbsökning** och **typ av systemgenomsökning som ska utföras** visar statusen Genomförd när skanningen slutförs korrekt och visar Misslyckad när inställningarna inte tillämpas. 

Mer information om inställningarna för Windows Defender Antivirus finns i [Enhetsinställningar för Windows 10 (och senare) för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus). 

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="default-scope-tags----3702875----"></a>Standardomfångstaggar <!-- 3702875  -->
En nyinbyggd standardomfångstagg är nu tillgänglig. Alla icke-taggade Intune-objekt som stöder omfångstaggar tilldelas automatiskt till standardomfångstaggen. **Standardomfångstaggen** läggs till i alla befintliga rolltilldelningar för att upprätthålla paritet med administratörsupplevelsen idag. Om du inte vill att en administratör ska se Intune-objekt med standardomfångstaggen, tar du bort standardomfångstaggen från rolltilldelningen. Den här funktionen liknar funktionen säkerhetsomfattningar i System Center Configuration Manager. Mer information finns i [Använda RBAC och omfångstaggar för distribuerad IT](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support----4869749-----"></a>Stöd för registrering av Android-enhetens administratör <!-- 4869749   -->
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

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process----3823054---"></a>Lägg till en användarkolumn till CSV-överföringsprocessen för autopilotenheten <!-- 3823054 -->
Nu kan du lägga till en användarkolumn till CSV-överföringen för autopilotenheter. På så sätt kan du tilldela många användare på samma gång när du importerar CSV-filen. Du hittar mer information i [Registrera Windows-enheter i Intune med hjälp av Windows Autopilot](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Enhetshantering

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Konfigurera tidsgräns för automatisk rensning av enhet till 30 dagar <!--4231059  -->
Du kan ställa in den automatiska tidsgränsen för enhetsrensning så kort som 30 dagar (i stället för den tidigare gränsen på 90 dagar) efter den senaste inloggningen. Det gör du genom att gå till **Intune** > **Enheter** > **Installation** > **Regler för rensning av enhet**.

#### <a name="build-number-included-on-android-device-hardware-page----4461910-----"></a>Versionsnummer finns på Android-enhetens maskinvarusida <!-- 4461910   -->
En ny post på sidan Maskinvara för varje Android-enhet innehåller versionsnumret för enhetens operativsystem. Mer information finns i [Visa enhetsinformation i Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Veckan 5 augusti 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices-----4843713---"></a>Zebra Technologies är en OEM-tillverkare som stöds för OEMConfig på Android Enterprise-enheter  <!-- 4843713 -->

I Intune kan du kan skapa en profil för enhetskonfiguration och använda inställningar för Android Enterprise-enheter med hjälp av OEMConfig (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **OEMConfig** för profiltyp).

I den här uppdateringen är Zebra Technologies en OEM-tillverkare (Original Equipment Manufacturer) som stöds för OEMConfig. Mer information om OEMConfig hittar du i [Använda och hantera Android Enterprise-enheter med OEMConfig](../configuration/android-oem-configuration-overview.md).

Gäller för:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Veckan som inleds med den 22 juli 2019 

### <a name="app-management"></a>Apphantering

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>Anpassade meddelanden för användare och grupper    <!-- 16766574          -->
Skicka anpassade push-meddelanden från företagsportalprogrammet till användare på iOS- och Android-enheter som du hanterar med Intune. Dessa mobila push-meddelanden är mycket anpassningsbara med fri text och kan användas för alla ändamål. Du kan rikta dem till olika användargrupper i din organisation. Mer information finns i [anpassade meddelande](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app----3041950----"></a>Googles app för enhetspolicykontroll <!-- 3041950  -->
Nu ger Managed Home Screen-appen tillgång till Googles Android Device Policy-app. Managed Home Screen-appen är en anpassad startfunktion som används med enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som använder helskärmsläge för flera appar. Du kan komma åt Android Device Policy-appen, eller vägleda användare till Android Device Policy-appen, för support och felsökning. Den här startfunktionen är tillgänglig när enheten registreras och låses på startskärmen i Managed Home Screen. Inga ytterligare installationer behövs för att använda den här funktionen.

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>Outlook-skyddsinställningar för iOS- och Android-enheter <!-- 3212619 -->
Du kan nu konfigurera både allmänna konfigurationsinställningar för appar och dataskydd för Outlook för iOS och Android med hjälp av enkla Intune-administratörskontroller utan enhetsregistrering. Konfigurationsinställningarna för allmänna appar ger paritet med inställningar som administratörer kan aktivera när de hanterar Outlook för iOS och Android på registrerade enheter. Mer information om Outlook-inställningar finns i [appkonfigurationsinställningar för att distribuera Outlook för iOS och Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Använd ”tillämplighetsregler” när du skapar konfigurationsprofiler för Windows 10-enheter <!-- 2549910 eeready   idstaged -->

Du skapar konfigurationsprofiler för Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10** som plattform > **Tillämplighetsregler**). I den här uppdateringen kommer du att kunna skapa en **tillämpningsregel** så att profilen endast gäller för en viss utgåva eller en specifik version. Exempelvis kan du skapa en profil som aktiverar vissa BitLocker-inställningar. När du lägger till profilen använder du en tillämpningsregel så att profilen endast gäller för enheter som kör Windows 10 Enterprise.

Information om hur du lägger till en tillämplighetsregel finns i [Tillämplighetsregler](../configuration/device-profile-create.md#applicability-rules).

Gäller för: Windows 10 och senare

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>Använd tokens för att lägga till enhetsspecifik information i anpassade profiler för iOS-och macOS-enheter <!-- 3330008  -->
Du kan använda anpassade profiler på iOS- och MacOS-enheter för att konfigurera inställningar och funktioner som inte är inbyggda i Intune (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **MacOS** för plattform > **Anpassad** för profiltyp). I den här uppdateringen kan du lägga till tokens till dina `.mobileconfig`-filer för att lägga till enhetsspecifik information. Du kan till exempel lägga till `Serial Number: {{serialnumber}}` i konfigurationsfilen för att visa enhetens serienummer.

Du hittar information om att skapa en anpassad profil i [anpassade inställningar för iOS](../configuration/custom-settings-ios.md) eller [anpassade inställningar för MacOS](../configuration/custom-settings-macos.md).

Gäller för:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>Ny konfigurationsdesign när du skapar en OEMConfig-profil för Android Enterprise <!-- 3712769   -->
I Intune kan du skapa en enhetskonfigurationsprofil som använder en OEMConfig-app (enhetskonfiguration > Profiler > Skapa profil > Android Enterprise för plattform > OEMConfig för profiltyp). När du gör det öppnas en JSON-redigerare med en mall och de värden som du kan ändra. 

Den här uppdateringen innehåller en konfigurationsdesign med en förbättrad användarupplevelse som visar information som är inbäddad i appen, inklusive titlar, beskrivningar och mer. JSON-redigeraren är fortfarande tillgänglig och visar eventuella ändringar som du gör i Configuration Designer.

Om du vill se de aktuella inställningarna går du till [Använda och hantera Android Enterprise-enheter med OEMConfig](../configuration/android-oem-configuration-overview.md).

Gäller för: Android enterprise

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>Uppdaterat användargränssnitt för att konfigurera Windows Hello  <!-- 4089576            -->
Vi har uppdaterat konsolen där du [konfigurerar Intune för att använda Windows Hello för företag](../protect/windows-hello.md). Alla konfigurationsinställningar är nu tillgängliga i samma fönster i konsolen där du aktiverar stöd för Windows Hello. 


#### <a name="intune-powershell-sdk----4924113---"></a>Intune PowerShell SDK <!-- 4924113 --> 
Intune PowerShell SDK, som ger stöd för Intune API via Microsoft Graph, har uppdaterats till version 6.1907.1.0. SDK har nu stöd för följande:
- Fungerar med Azure Automation.
- Har stöd för läsåtgärder för app-only-autentisering. 
- Har stöd för egna korta namn som alias.
- Följer namnkonventioner för PowerShell. Mer specifikt har `PSCredential`-parametern (på `Connect-MSGraph`-cmdleten) bytt namn till `Credential`.
- Stöder manuell angivelse av värdet för `Content-Type`-sidhuvudet när du använder `Invoke-MSGraphRequest`-cmdleten.

Mer information finns i [PowerShell SDK för Microsoft Intune Graph API.](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>Uppdateringar för registreringsbegränsningar  <!-- 2871968 -->
Registreringsbegränsningar för nya klienter har uppdaterats så att Android Enterprise Work-profiler tillåts som standard. Befintliga klienter får ingen förändring. Om du vill använda Android Enterprise Work-profiler måste du fortfarande [ansluta ditt Intune-konto till ditt hanterade Google Play-konto](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>Användargränssnittsuppdateringar för Apple-registrering och registreringsbegränsningar <!--4089575, 4089579  -->
De två följande processerna använder ett användargränssnitt med en guide:
- Registrering av Apple-enhet. Mer information finns i [Registrera iOS-enheter automatiskt med Apples program för enhetsregistrering](../enrollment/device-enrollment-program-enroll-ios.md).
- Skapa registreringsbegränsningar. Mer information finns i [Konfigurera registreringsrestriktioner](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>Hantera förkonfigurering av enhetsidentifierare för företag för Android Q-enheter <!-- 4711509  idmiss -->
I Android Q (v10) tar Google bort möjligheten för MDM-agenter på tidigare hanterade Android-enheter (enhetsadministratör) för att samla in information om enhetsidentifieraren.  Intune har en funktion som gör det möjligt för IT-administratörer att [förkonfigurera en lista över enhetsserienummer eller IMEI](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) för att automatiskt tagga enheterna som företagsägda. Den här funktionen fungerar inte för Android Q-enheter som hanteras av enhetsadministratören.  Oavsett om serienumret eller IMEI för enheten har laddats upp anses det alltid vara personligt under Intune-registreringen.  Du kan manuellt växla ägarskap till företag efter registreringen.  Detta påverkar endast nya registreringar och befintliga registrerade enheter påverkas inte.  Android-enheter som hanteras med arbetsprofiler påverkas inte av den här ändringen och fortsätter att fungera som de gör i dag.  Dessutom kommer Android Q-enheter som registrerats som enhetsadministratör inte längre att kunna rapportera serienummer eller IMEI i Intune-konsolen som enhetsegenskaper.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>Ikoner har ändrats för Android Enterprise-registreringar (arbetsprofil, dedikerade enheter och fullständigt hanterade enheter) <!-- 4977730 -->
Ikonerna för Android Enterprise-registreringsprofiler har ändrats. Om du vill se de nya ikonerna går du till **Intune** > **Registrering** > **Android-registrering** > tittar under **Registreringsprofiler**.


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>Ändring av datainsamling i Windows-diagnostikdata <!-- 4113859 -->
Standardvärdet för insamling av diagnostikdata har ändrats för enheter som kör Windows 10, version 1903 och senare. Från och med Windows 10 1903 aktiveras insamling av diagnostikdata som standard. Windows-diagnostikdata är viktiga tekniska data från Windows-enheter om enheten och hur Windows och relaterad programvara fungerar. Mer information finns i [Konfigurera Windows-diagnostikdata i din organisation](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Autopilot-enheter anges också som ”fullständig” telemetri om inget annat anges i autopilotprofilen med [ System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Enhetshantering

#### <a name="improve-device-location---3855417----"></a>Förbättra enhetens plats<!-- 3855417  -->
Du kan zooma in till de exakta koordinaterna för en enhet med åtgärden **Hitta enhet**. Mer information om hur du hittar borttappade iOS- enheter finns i [Hitta borttappade iOS-enheter](../remote-actions/device-locate.md).


### <a name="device-security"></a>Enhetssäkerhet

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview------1311949-------"></a>Avancerade inställningar för Windows Defender-brandväggen (offentlig förhandsversion)  <!--  1311949     -->  
Använd Intune för att [hantera anpassade brandväggsregler som en del av en enhetskonfigurationsprofil](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) för Endpoint Protection på Windows 10. Regler kan ange beteende för inkommande och utgående trafik till program, nätverksadresser och portar. 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>Uppdaterat användargränssnitt för hantering av säkerhetsbaslinjer   <!-- 4091125     -->
Vi har uppdaterat [skapa och redigera-upplevelsen](../protect/security-baselines.md#create-the-profile) i Intune-konsolen för våra säkerhetsbaslinjer. Ändringarna omfattar:

Ett enklare guideformat som har komprimerats till ett enda blad. inom ett blad. Den här nya designen tar bort bladspridningen som kräver att IT-proffs måste öka detaljnivån till flera separata fönster.  
Nu kan du skapa tilldelningar som en del av skapa och redigera-upplevelsen, i stället för att behöva gå tillbaka senare för att tilldela baslinjer. Vi har lagt till en sammanfattning av de inställningar som du kan visa innan du skapar en ny baslinje och när du redigerar en befintlig. Vid redigering visar sammanfattningen bara listan över objekt som har angetts i kategorin med egenskaper som redigeras.



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Veckan som inleds med den 15 juli 2019 

### <a name="app-management"></a>Apphantering

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>Ikoner för hanterad hemskärm och hanterade inställningar <!-- 4918107 -->
Ikonen för appen för hanterad hemskärm och ikonen för **hanterade inställningar** har uppdaterats. Appen för hanterad hemskärm används bara av enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som kör i helskärmsläge för flera appar. Mer information om appen för hanterad hemskärm finns i [Konfigurera Microsoft-appen för hanterad hemskärm för Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Android-enhetspolicy på dedikerade Android Enterprise-enheter <!-- 4918136 -->
Du kan komma åt Android-enhetspolictprogrammet från felsökningsskärmen för den hanterade hemskärmsappen. Appen för hanterad hemskärm används bara av enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som kör i helskärmsläge för flera appar. Du hittar mer information i [Konfigurera Microsofts hanterade hemskärmsapp för Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates----3902931---"></a>Uppdateringar av iOS-företagsportalen <!-- 3902931 -->
Ditt företagsnamn vid begäranden om hantering av iOS-appar ersätter den aktuella ”i.manage.microsoft.com”-texten. Användare ser till exempel företagets namn i stället för ”i.manage.microsoft.com” när de försöker installera en iOS-app från Företagsportalen eller när de tillåter hantering av appen. Detta kommer att distribueras till alla kunder under de närmaste dagarna.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>Hantera FileVault för macOS   <!--  3858502 + 4557986 + 1210104  -->
Du kan använda Intune för att [hantera FileVault-krypteringsnyckel för MacOS-enheter](../protect/encrypt-devices.md). För att kryptera enheter kan du använda en enhetskonfigurationsprofil för slutpunktsskydd.

Vår support för FileVault omfattar kryptering av okrypterade enheter, deposition av enheters personliga återställningsnyckel, automatisk eller manuell rotation av personliga krypteringsnycklar och nyckelhämtning för företagsenheter. Slutanvändare kan också använda Företagsportalens webbplats för att hämta den personliga återställningsnyckeln för sina krypterade enheter. 

Vi har också expanderat krypteringsrapporten till att inkludera [information om FileVault](../protect/encryption-monitor.md) för BitLocker, så att du kan visa all din enhets krypteringsinformation på en och samma plats. 

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>Windows autopilot-återställning tar bort enhetens primära användare <!-- 4156123 -->
När autopilot-återställning används på en enhet tas enhetens primära användare bort. Nästa användare som loggar in efter återställningen kommer att anges som primär användare. Den här funktionen kommer att distribueras till alla kunder under de närmaste dagarna.

## <a name="week-of-july-8-2019"></a>Veckan som inleds med den 8 juli 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Nya Office-, Windows- och OneDrive-inställningar i administrativa mallar i Windows 10 <!-- 3510695 -->

Du kan skapa administrativa mallar i Intune som imiterar lokal grupprinciphantering (**enhetshantering** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Administrativ mall** för profiltyp).

Den här uppdateringen innehåller fler Office-, Windows- och OneDrive-inställningar som du kan lägga till i dina mallar. Med de här nya inställningarna kan du nu konfigurera över 2500-inställningar som är 10 0% molnbaserade.

Mer information om den här funktionen finns i [Använda Windows 10-mallar för att konfigurera grupprincipinställningar i Intune](../configuration/administrative-templates-windows.md).

Gäller för: Windows 10 och senare

## <a name="week-of-july-1-2019"></a>Veckan som inleds med den 1 juli 2019 

### <a name="app-management"></a>Apphantering

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>AAD och APP på Android Enterprise-enheter <!-- 3574267 -->
När du registrerar fullständigt hanterade Android Enterprise-enheter kommer användarna nu att registreras med Azure Active Directory (AAD) under den första installationen av den nya eller fabriksåterställda enheten. Innan installationen slutfördes tidigare var användaren tvungen att starta Microsoft Intune-appen manuellt för att starta AAD-registreringen efter att installationen slutförts. Nu när användaren kommer till enhetens startsida efter den första installationen, är enheten både ansluten och registrerad.

Förutom AAD-uppdateringar stöds nu Intune App Protection-principer (APP) på fullständigt hanterade Android Enterprise-enheter. Den här funktionen kommer att bli tillgänglig då vi distribuerar den. Du hittar mer information i [Lägg till hanterade Google Play-appar till Android enterprise-enheter med Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Veckan som inleds med 24 juni 2019 

### <a name="app-management"></a>Apphantering

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Konfigurera vilken webbläsare som ska ha tillåtelse att länka till organisationsdata <!-- 3145939 -->
Principer för Intune-appskydd (APP) på enheter med Android och iOS gör att du nu kan överföra organisationswebblänkar till en viss webbläsare utöver Intune Managed Browser eller Microsoft Edge.  Mer information om APP finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>Sidan Alla appar identifierar Microsoft Store för företagsappar online/offline<!--4089647 -->
Sidan **Alla appar** innehåller nu etiketter för att identifiera Microsoft Store-appar för företag (MSFB) som online- eller offline-appar. Varje MSFB-app innehåller nu ett suffix för **online** eller **offline**. Sidan med information om appen innehåller också **Licenstyp** och **stöder enhetskontextinstallation** (endast offline-licensierade appar).

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>Företagsportalappen på delade Windows-enheter <!--4393553 -->
Användare kan nu komma åt företagsportalappen på delade Windows-enheter. Slutanvändare ser en **Delad** etikett på enhetspanelen. Detta gäller version 10.3.45609.0 och senare av Windows företagsportalappen.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>Visa alla installerade appar från den nya webbplatsen för företagsportalen <!-- 4224326 -->
Företagsportalens webbplats har en ny sida för **Installerade appar** som visar alla hanterade appar, både nödvändiga och tillgängliga, som är installerade på en användares enhet. Förutom tilldelningstyp kan användare se appens utgivare, utgivningsdatum och aktuell installationsstatus. Om din organisation inte gör appar obligatoriska eller tillgängliga ser användarna ett meddelande som förklarar att inga företagsappar har installerats. Om du vill se den nya sidan på webben går du till den [företagsportalwebbplatsen](https://portal.manage.microsoft.com) och klickar på **Installerade appar**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>I nästa vy kan appanvändare se alla hanterade appar som har installerats på enheten <!-- 2352913 -->  
Företagsportalappen för Windows visar alla hanterade appar, både nödvändiga och tillgängliga, som är installerade på en användares enhet. Användare kommer att kunna visa installationsförsök och väntande installationer, och deras aktuella status. Om din organisation inte gör appar obligatoriska eller tillgängliga ser användarna ett meddelande som förklarar att inga företagsappar har installerats. Om du vill se den nya vyn, gå till företagsportalens navigeringsfönster och välj **Appar** > **Installerade appar**.    

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Konfigurera inställningar för kerneltillägg på macOS-enheter <!-- 2043024 -->
På macOS-enheter kan du skapa en enhetskonfigurationsprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **macOS** som plattform). Denna uppdatering inkluderar en ny grupp med inställningar som gör att du kan konfigurera och använda kerneltillägg på dina enheter. Du kan lägga till vissa tillägg eller tillåta alla tillägg från en speciell partner eller utvecklare.

Mer information om den här funktionen finns i [översikt över kerneltillägg](../configuration/kernel-extensions-overview-macos.md) och [inställningar för kerneltillägg](../configuration/kernel-extensions-settings-macos.md).

Gäller för: macOS 10.13.2 och senare

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>Appar från inställningen Endast Store för Windows 10-enheter innehåller fler konfigurationsalternativ <!-- 2697002 -->
När du skapar en enhetsbegränsningsprofil för Windows-enheter kan du använda inställningen **Appar endast från Store**. Det gör att användare endast installerar appar från Windows App Store (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp). I den här uppdateringen kommer inställningen att expanderas för att stödja fler alternativ. 

Gå till [Enhetsinställningar för Windows 10 (och senare) för att tillåta eller begränsa funktioner](../configuration/device-restrictions-windows-10.md#app-store) för att se den nya inställningen.

Gäller för: Windows 10 och senare

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Distribuera flera Zebra Mobility Extensions-enhetsprofiler till en enhet, samma användargrupp eller samma grupp av enheter <!-- 4089955 -->
I Intune kan du använda Zebra Mobility Extensions (MX) i en profil för enhetskonfiguration för att anpassa inställningar för Zebra-enheter som inte är inbyggda i Intune. För närvarande kan du distribuera en profil till en enskild enhet. I den här uppdateringen kan du distribuera flera profiler till:
- Samma användargrupp
- Samma enhetsgrupp
- En enskild enhet

[Använda och hantera Zebra-enheter med Zebra Mobility Extensions i Microsoft Intune](../configuration/android-zebra-mx-overview.md) visar hur du använder MX i Intune.

Gäller för: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Vissa inställningar för helskärmsläge på iOS-enheter är angivna till ”Blockera”, vilket ersätter ”Tillåt” <!-- 4404075  -->
När du skapar en enhetsbegränsningsprofil på iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Helskärmsläge**) ställer du in **Autolås**, **Ringsignalsknapp**, **Skärmrotation**, **Viloläge för skärm-knapp** och **Volymknappar**. 

I denna uppdatering är värdena **Blockera** (blockerar funktionen) och **Inte konfigurerat** (tillåter funktionen). Om du vill se inställningarna går du till [iOS-enhetsinställningar för att tillåta eller begränsa funktioner](../configuration/device-restrictions-ios.md#kiosk). 

Gäller för: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>Använd Face ID för lösenordsautentisering på iOS-enheter <!-- 4490704 -->
När du skapar en enhetsbegränsningsprofil för iOS-enheter kan du använda ett fingeravtryck som lösenord. Inställningarna för lösenord med fingeravtryck tillåter även ansiktsigenkänning i denna uppdatering (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Lösenord**). Därför ändras följande inställningar:

- **Upplåsning med fingeravtryck** är nu **Upplåsning av Touch ID och Face ID**.
- **Ändring av fingeravtryck (endast övervakat)** är nu **Ändring av Touch ID och Face ID (endast övervakat)** .

Face ID är tillgängligt i iOS 11.0 och senare. Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md#password) för att se inställningarna.

Gäller för: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>Begränsning av spel och App Store-funktioner på iOS-enheter är nu beroende av klassificeringsregion <!-- 4593948 -->
På iOS-enheter kan du tillåta eller begränsa funktioner för spel, App Store och dokumentvisning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel**). Du kan också välja klassificeringsregion, till exempel USA. 

I denna uppdatering är funktionen **Appar** underordnad **klassificeringsregion** och är beroende av **klassificeringsregion**. Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming) för att se inställningarna.

Gäller för: iOS

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>Windows autopilot-stöd för Hybrid Azure AD-anslutning <!-- 4809146-->
Windows autopilot för befintliga enheter stöder nu hybrid Azure AD-anslutning (förutom det befintliga stödet för Azure AD-anslutning). Gäller för Windows 10 version 1809 och senare enheter. Mer information finns i [Windows Autopilot för befintliga enheter](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).



### <a name="device-management"></a>Enhetshantering

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>Se säkerhetskorrigeringsnivå för Android-enheter <!-- 4461911 -->
Du kan nu se säkerhetskorrigeringsnivå för Android-enheter. Det gör du genom att välja **Intune** > **Enheter** > **Alla enheter** > välj en enhet > **Maskinvara**.
Korrigeringsnivån visas i avsnittet **Operativsystem**.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Tilldela omfångstaggar till alla hanterade enheter i en säkerhetsgrupp <!-- 3173810 -->
Du kan nu tilldela omfångstaggar till en säkerhetsgrupp, och alla enheter i säkerhetsgruppen kommer också att associeras med omfångstaggarna i en kommande uppdatering. Alla enheter i grupperna kommer också att tilldelas omfångstaggen. Omfångstaggar med den här funktionen skriver över omfångstaggar med det aktuella flödet för enhetens omfångstaggar. Mer information finns i [Använda RBAC och omfångstaggar för distribuerad IT](scope-tags.md).

### <a name="device-security"></a>Enhetssäkerhet

#### <a name="use-keyword-search-with-security-baselines-------"></a>Använd nyckelordssökning med säkerhetsbaslinjer <!--  -->
När du skapar eller redigerar [Profiler för säkerhetsbaslinje](../protect/security-baselines.md#create-the-profile) kan du ange nyckelord i det nya *Sök*-fältet för att filtrera tillgängliga grupper med inställningar till de som innehåller dina sökvillkor. 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>Funktionen säkerhetsbaslinjer är nu allmänt tillgänglig  <!-- 3785395 -->
Funktionen **Säkerhetsbaslinjer** är inte längre i förhandsversionen utan är allmänt tillgänglig.  Det innebär att funktionen är klar att användas i produktion. De enskilda baslinjemallarna kan dock bevaras i förhandsversionen och utvärderas och publiceras som allmänt tillgängliga enligt sina egna scheman.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>Mallen för MDM-säkerhetsbaslinjer är nu allmänt tillgänglig   <!-- 3794072, 4217151,  3534649 -->
Mallen för MDM-säkerhetsbaslinjer är inte längre i förhandsversionen utan är nu allmänt tillgänglig. Mallen för allmän tillgänglighet identifieras som **MDM-säkerhetsbaslinje för maj 2019**.  Det här är en ny mall och inte en uppgradering från förhandsversionen.  Som en ny mall måste du granska [inställningarna den innehåller](../protect/security-baseline-settings-mdm.md)och sedan skapa nya profiler för att distribuera mallen till din enhet. Andra säkerhetsbaslinjer kan finnas kvar i förhandsversionen. En lista över tillgängliga baslinjer finns i [tillgängliga säkerhetsbaslinjer](../protect/security-baselines.md#available-security-baselines).  

Förutom att vara en ny mall innehåller mallen *MDM-säkerhetsbaslinjen för maj 2019* de två inställningar som vi nyligen presenterade i vår utvecklingsartikel:  
- På låsskärmen: Röstaktivera appar från en låst skärm  
- DeviceGuard: Använd virtualiseringsbaserad säkerhet (VBS) vid nästa omstart av enheter.  

*MDM-säkerhetsbaslinjen för maj 2019* innehåller också tillägg av flera nya inställningar, borttagning av andra och granskning av standardvärdet för en inställning. En detaljerad lista över ändringarna från förhandsgranskning till allmänt tillgänglig finns i **Vad som har ändrats i den nya mallen**.

#### <a name="security-baseline-versioning-----3194322---"></a>Versioner av säkerhetsbaslinjer  <!-- 3194322 -->
Säkerhetsbaslinjer för version av Intune-support. Då nya versioner av varje säkerhetsbaslinje släpps med detta stöd kan du uppdatera dina befintliga säkerhetsbaslinjeprofiler till att använda den nya baslinjeversionen utan att behöva återskapa och distribuera en ny baslinje från grunden. I Intune-konsolen kan du också visa information om varje baslinje, till exempel antalet enskilda profiler som använder baslinjen, hur många av de olika baslinjeversionerna som dina profiler använder och när den senaste versionen av en viss säkerhetsbaslinje släpptes.  Mer information finns i **Säkerhetsbaslinjer**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>Inställningen Använd säkerhetsnycklar för inloggning har flyttats  <!-- 4501151 -->
Enhetskonfigurationsinställningen för identitetsskydd med namnet **Använd säkerhetsnycklar för inloggning** finns inte längre som en delinställning för att *Konfigurera Windows Hello för företag*. Nu är det en inställning på översta nivån som alltid är tillgänglig, även när du inte aktiverar användning av Windows Hello för företag. Mer information finns i [Identitetsskydd](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>Nya behörigheter för tilldelade gruppadministratörer   <!-- 4504437   -->
Intunes inbyggda skoladministratörsroll har nu behörighet att skapa, läsa, uppdatera och ta bort (CRUD) tillstånd för hanterade appar. Uppdateringen innebär att om du är tilldelad som gruppadministratör i Intune for Education kan du nu skapa, visa, uppdatera och ta bort iOS MDM-pushcertifikat, iOS MDM-tokens och iOS VPP-token tillsammans med [alla befintliga behörigheter som du har](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Om du vill vidta någon av dessa åtgärder går du till **Klientinställningar** > **iOS**Enhetshantering.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>Program kan använda Graph API för att anropa läsåtgärder utan användarautentiseringsuppgifter <!-- 4655885 -->
Program kan anropa Intune Graph API-läsåtgärder med appidentitet utan användarens autentiseringsuppgifter. Mer information om hur du kommer åt Microsoft Graph API för Intune finns i [Arbeta med Intune i Microsoft Graph.](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>Använda omfångstaggar för appar i Microsoft Store för företag <!-- 4392555 -->
Du kan nu använda omfångstaggar för appar i Microsoft Store för företag. Mer information om omfångstaggar finns i [Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT](scope-tags.md).

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
Windows-företagsportalappen har nu en ny sida med etiketten **Enheter**. På sidan **Enheter** ser slutanvändare alla sina registrerade enheter. Användarna ser den här ändringen i företagsportalen när de använder version 10.3.4291.0 och senare. Mer information om hur du konfigurerar företagsportalen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>OrderID-attributet på Autopilot-enheter har bytt namn till Grupptagg <!-- 4659453 -->

För att göra det mer intuitivt har **OrderID**-attributets namn på Autopilot-enheter ändrats till **Grupptagg**. När du använder CSV-filer för att ladda upp Autopilot-enhetsinformation måste du använda Grupptagg som kolumnrubrik, inte OrderID.  

## <a name="week-of-may-13-2019"></a>Den vecka som börjar 13 maj 2019 

### <a name="app-management"></a>Apphantering

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>Uppdatering av Intune-principers autentiseringsmetod och installation av företagsportalappen  <!-- 1927359  -->
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

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>PowerShell-skript i Intune-hanteringstillägget  <!-- 3734186  -->
Du kan konfigurera PowerShell-skript så att det körs med användarens administratörsprivilegier på enheten. Mer information finns i [Använda PowerShell-skript på Windows 10-enheter i Intune](../apps/intune-management-extension.md) och [Win 32-apphantering](../apps/app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Apphantering med Android Enterprise <!-- 4459905 -->
Intune lägger automatiskt till fyra vanliga Android Enterprise-relaterade appar till Intune-administratörskonsolen för att göra det enklare för IT-administratörer att konfigurera och använda Android Enterprise-hantering. Detta är de fyra Android Enterprise-apparna:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – Används för fullständigt hanterade Android Enterprise-scenarier.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – Hjälper dig att logga in på dina konton om du använder tvåfaktorautentisering.
- **[Intune-företagsportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – Används för appskyddsprinciper och scenarier med Android Enterprise-arbetsprofiler.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) – Används för dedikerade/helskärmslägesscenarier i Android Enterprise.

Tidigare var IT-administratörer tvungna att hitta och godkänna de här apparna manuellt i den [hanterade Google Play-butiken](https://play.google.com/store/apps) som en del av konfigurationen. Den här ändringen tar bort de tidigare manuella stegen för att göra det enklare och snabbare för kunder att använda Android Enterprise-hantering.

Administratörer kommer att se att dessa fyra appar läggs till i listan över appar i Intune automatiskt när de ansluter Intune-klienten till hanterade Google Play för första gången. Läs [Anslut ditt Intune-konto till ditt hanterade Google Play-konto](../enrollment/connect-intune-android-enterprise.md) för mer information. Administratörer behöver inte göra något för klienter som redan har anslutit sin klient eller som redan använder Android Enterprise. De fyra apparna visas automatiskt inom sju dagar efter slutförandet av tjänstlanseringen under maj 2019.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>Uppdaterat PFX-certifikatanslutningsprogram för Microsoft Intune  <!-- 1533038 -->
Vi har släppt en uppdatering för [PFX-certifikatanslutningsappen för Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) som löser problemet där befintliga PFX-certifikat fortsätter att bearbetas, vilket orsakar att anslutningsappen slutar att bearbeta nya begäranden.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Intune-säkerhetsuppgifter för Defender ATP (i allmänt tillgänglig förhandsversion)     <!-- 3208597 -->
Du kan använda Intune för att hantera [säkerhetsuppgifter för Microsoft Defender Advanced Threat Protection (ATP) i den allmänt tillgängliga förhandsversionen](../protect/atp-manage-vulnerabilities.md). Det här möjliggör integrering med ATP och lägger till en riskbaserad metod för att identifiera, prioritera och åtgärda säkerhetsrisker och felkonfigurationer på slutpunkter, samtidigt som det minskar tiden mellan identifiering till problemlösning.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Söka efter en TPM-kretsuppsättning i en efterlevnadsprincip för Windows 10-enheter <!-- 3617671   idstaged-->
Många Windows 10-enheter och senare enheter har TPM-kretsuppsättningar (Trusted Platform Module). Den här uppdateringen innehåller en ny efterlevnadsinställning som kontrollerar versionen på TPM-chippet i enheten. 

[Inställningar för kompatibilitetsprinciper i Windows 10 och senare](../protect/compliance-policy-create-windows.md#device-security) beskriver den här inställningen.

Gäller för: Windows 10 och senare

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Förhindra slutanvändare från att ändra sin Internetdelning och inaktivera Siri-serverloggning på iOS-enheter <!-- 4097904   -->  
Du kan skapa en enhetsbegränsningsprofil på en iOS-enhet (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp). Den här uppdateringen innehåller nya inställningar som du kan konfigurera:

- **Inbyggda appar**: Loggning på serversidan av Siri kommandon
- **Trådlöst**: Användarmodifiering av internetdelning (endast övervakat)

Om du vill se de här inställningarna går du till [inbyggda app-inställningar för iOS](../configuration/device-restrictions-ios.md#built-in-apps) och [trådlösa inställningar för iOS](../configuration/device-restrictions-ios.md#wireless).

Gäller för: iOS 12.2 och senare

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Nya inställningar för enhetsbegränsning i appen Klassrum för macOS-enheter <!-- 4097905   --> 
Du kan skapa profiler för enhetskonfiguration för macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsbegränsningar** för profiltyp). Den här uppdateringen innehåller nya inställningar för appen Klassrum, alternativet att blockera skärmbilder och inaktivera iCloud-bildbiblioteket.

Gå till [macOS-enhetsinställningar för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-macos.md) för att se de aktuella inställningarna.

Gäller för: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>iOS lösenordet för åtkomst till appbutiksinställningen har bytt namn<!-- 4557891  -->
Inställningen **Lösenord till appbutik** har bytt namn till **Kräv iTunes Store-lösenord för alla köp** (**Enhetskonfiguration**  >  **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel**).

Om du vill se de tillgängliga inställningarna går du till [iOS-inställningar för App Store, dokumentvisning, spel](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gäller för: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Baslinjer för Microsoft Defender Advanced Threat Protection (Förhandsversion)  <!--  3754134 -->
Vi har lagt till en förhandsversion med säkerhetsbaslinje för [Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md)-inställningar. Denna baslinje finns tillgänglig när din miljö uppfyller förhandskraven för att använda [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Windows registreringsstatussida (ESP) är nu allmänt tillgänglig <!-- 3605348 -->
Registreringsstatussidan är inte längre en förhandsversion. Mer information finns i [Konfigurera en sida för registreringsstatus](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Uppdatering av användargränssnittet i Intune – Skapa Autopilot-registreringsprofil  <!-- 4593669 -->
Användargränssnittet för att skapa en Autopilot-profil för registrering har uppdaterats så att den överensstämmer med Azures användargränssnitt. Mer information finns i [Skapa en Autopilot-registreringsprofil](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). Framöver kommer ytterligare Intune scenarier att uppdateras till det här nya användargränssnittet.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Aktivera Autopilot-återställning av alla Windows-enheter <!-- 4225665 -->
Autopilot-återställning fungerar nu för alla Windows-enheter, även de som inte har konfigurerats för att använda registreringsstatussidan. Om en registreringsstatussida inte har konfigurerats för enheten under den första enhetsregistreringen kommer enheten att gå direkt till skrivbordet efter inloggningen. Det kan ta upp till åtta timmar att synkroniseras och visas som kompatibel i Intune. Mer information finns i [Återställa enheter med fjärransluten Windows Autopilot-återställning](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Exakta IMEI-format krävs inte när du söker igenom alla enheter <!--30407680 -->
Du behöver inte ta med mellanslag i IMEI-nummer när du söker igenom **Alla enheter**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Om du tar bort en enhet i Apples portal visas ändringen även i Intune-portalen <!--2489996 -->
Om en enhet tas bort från Apples program för enhetsregistrering eller Apple Business Manager-portalen tas den även automatiskt bort från Intune vid nästa synkronisering.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>Registreringsstatussidan spårar nu Win32-appar <!-- 2714451 -->
Detta gäller endast enheter som kör Windows 10, version 1903 och senare. Mer information finns i [Konfigurera en sida för registreringsstatus](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Enhetshantering

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Återställa och rensa enheter i grupp med hjälp av Graph API <!-- 3295288 -->
Du kan nu återställa och rensa upp till 100 enheter i grupp med Graph API.


### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>Krypteringsrapport är inte längre en allmänt tillgänglig förhandsversion   <!-- 4587546      -->
[Rapporten för kryptering av BitLocker och enheter](../protect/encryption-monitor.md) är nu allmänt tillgänglig och inte längre en del av förhandsversionen. 

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

Om du vill se den tillgängliga inställningen går du till [Konfigurera VPN-inställningar på iOS-enheter](../configuration/vpn-settings-ios.md).

Gäller för: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>Uppdaterat PFX-certifikatanslutningsprogram för Microsoft Intune <!-- doc-vso 1521237  -->  
Vi har släppt en uppdatering till [PFX-certifikatanslutningsappen för Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) som utelämnar avsökningsintervallet från 5 minuter till 30 sekunder.

## <a name="week-of-april-22-2019"></a>Den vecka som börjar 22 april 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Använd Compliance Manager för att skapa utvärderingar för Microsoft Intune<!-- 4404750 -->

[Compliance Manager](https://servicetrust.microsoft.com/ComplianceManager) (öppnar en annan Microsoft-webbplats) är ett verktyg för arbetsflödesbaserad riskbedömning i Microsoft Service Trust Portal. Det gör att du kan spåra, tilldela och verifiera din organisations aktiviteter för regelefterlevnad aktiviteter relaterade till Microsoft-tjänster. Du kan skapa din egen efterlevnadsbedömning med Office 365, Azure, Dynamics, Professionella tjänster och Intune. Intune har två utvärderingar – FFIEC och GDPR.

Compliance Manager hjälper dig att fokusera arbetet genom att dela in kontroller – kontroller som hanteras av Microsoft samt kontroller som hanteras av din organisation. Du kan slutföra utvärderingarna och sedan exportera och skriva ut dem.

Efterlevnad med [Federal Financial Institutions Examination Council (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (öppnar en annan Microsoft-webbplats) är en uppsättning standarder för onlinebanktjänster som utfärdas av FFIEC. Det är den mest efterfrågade utvärderingen för finansiella institutioner som använder Intune. Det tolkar hur Intune hjälper dem att uppfylla FFIEC-riktlinjer för cybersäkerhet relaterade till arbetsbelastningar med offentligt moln. Intunes FFIEC-utvärdering är den andra FFIEC-utvärderingen i Compliance Manager.

I följande exempel visas en analys av FFIEC-kontrollerna. Microsoft hanterar 64 kontroller. Du ansvarar för de återstående 12 kontrollerna.

![Se ett exempel på Intune-utvärdering för FFIEC, inklusive kundåtgärderna och Microsofts åtgärder](./media/whats-new/intune-ffiec-assessment-status.png)

[Allmänna dataskyddsförordningen (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (öppnar en annan Microsoft-webbplats) är en EU-lag som hjälper till att skydda enskilda personers rättigheter och deras data. GDPR är mest efterfrågade utvärderingen för stöd med efterlevnad av sekretesskrav. 

I följande exempel visas en analys av GDPR-kontrollerna. Microsoft hanterar 49 kontroller. Du ansvarar för de återstående 66 kontrollerna.

![Se ett exempel på Intune-utvärdering för GDPR, inklusive kundåtgärderna och Microsofts åtgärder](./media/whats-new/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Den vecka som börjar 15 april 2019

### <a name="app-management"></a>Apphantering

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>OpenSSL-kryptering för Android-appskyddsprinciper <!-- 3747362 -->
Intune-appskyddsprinciper (APP) på Android-enheter använder nu ett OpenSSL-krypteringsbibliotek som är kompatibelt med FIPS 140-2. Mer information finns i avsnittet för [kryptering](../apps/app-protection-policy-settings-android.md#encryption) i [Inställningar för Android-appskyddsprinciper i Microsoft Intune](../apps/app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Aktivera Win32-appsamband <!-- 2617348  -->
Som administratör kan du kräva du att andra appar installeras som beroenden innan Win32-appen installeras. Mer specifikt måste enheten installera de beroende apparna innan den installerar Win32-appen. I Intune väljer du **Klientappar** > **Appar** > **Lägg till** för att visa bladet **Lägg till app**. Välj **Windows-app (Win32)** som **Apptyp**. När du har lagt till appen kan du välja **Beroenden** för att lägga till de beroende appar som måste installeras innan Win32-appen kan installeras. Mer information finns i [Fristående Intune – Win32-apphantering](./../apps/app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Installationsinformation om appversion för Microsoft Store för företagsprogram <!-- 3537391   -->
Rapporter för appinstallation innehåller information om appversion för Microsoft Store för företagsprogram. I Intune väljer du **Klientappar** > **Appar**. Välj en **Microsoft Store för företag-app** och välj sedan **Installationsstatus för enhet** i avsnittet **Övervaka**.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Tillägg till reglerna för krav för Win32-appar <!-- 3676883   -->
Du kan skapa kravregler baserat på PowerShell-skript, registervärden och filsysteminformation. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **Windows-app (Win32)** som **Apptyp** på bladet **Lägg till app**.  Välj **Krav** > **Lägg till** för att konfigurera ytterligare kravregler. Sedan väljer du antingen **Filtyp**, **Register** eller **Skript** som **Typ av krav**. Mer information finns i [Win32-apphantering](./../apps/app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Konfigurera Win32-appar att installeras på Intune-registrerade Azure AD-anslutna enheter <!-- 3695227  -->
Du kan konfigurera Win32-appar att installeras på Intune-registrerade Azure AD-anslutna enheter. Mer information om Win32-appar i Intune finns i [Win32-apphantering](./../apps/app-management.md).

#### <a name="device-overview-shows-primary-user---3794259----"></a>Enhetsöversikt som visar primär användare <!--3794259  -->
På sidan för enhetsöversikt visas den primära användaren, som även kallas användartillhörighetsanvändaren (UDA). Om du vill se den primära användaren för en enhet väljer du **Intune** > **Enheter** > **Alla enheter** > välj en enhet. Den primära användaren visas nästan längst upp på sidan **Översikt**.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Ytterligare rapportering för Managed Google Play-app för Android Enterprise-arbetsprofilenheter <!-- 4105925  -->
För Managed Google Play-appar som distribueras till Android Enterprise-arbetsprofilenheter kan du visa det specifika versionsnumret för den app som är installerad på en enhet. Det här gäller endast för obligatoriska appar.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>iOS-tangentbord från tredje part <!-- 4111843   -->
Stödet för Intunes appskyddsprincip (APP) för inställningen **Tangentbord från tredje part** för iOS kommer att tas bort på grund av en iOS-plattformsändring. Du kommer inte att kunna konfigurera den här inställningen i Intune-administratörskonsolen och den kommer inte att tillämpas på klienten i Intune App SDK.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Ange inställningarna för inloggning och kontrollera omstartsalternativ på macOS-enheter <!-- 1210083  -->
På macOS-enheter kan du skapa en profil för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **macOS** för plattformen > **Enhetsfunktioner** för profiltypen). Den här uppdateringen innehåller nya inställningar för inloggningsfönstret, till exempel att visa en anpassad banderoll, ändra hur användare loggar in, visa eller dölja energiinställningarna och mer.

Om du vill se de här inställningarna går du till [inställningarna för iOS-enhetsfunktioner](../configuration/macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Konfigurera Wi-Fi på enhetsägardedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar <!--3041940  -->
Du kan aktivera inställningar på Android Enterprise-enhetsägarenheter när de körs som dedikerade enheter i helskärmsläge för flera appar. I den här uppdateringen kan du ge användare möjlighet att konfigurera och ansluta till Wi-Fi-nätverk (**Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetens ägare, Enhetsbegränsningar** för profiltyp > **Dedikerade enheter** > **Helskärmsläge**: **Flera appar** > **WiFi-konfiguration**). 

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md).

Gäller för: Dedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Konfigurera Bluetooth och parkoppling på enhetsägardedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar <!-- 3041941  -->
Du kan aktivera inställningar på Android Enterprise-enhetsägarenheter när de körs som dedikerade enheter i helskärmsläge för flera appar. I den här uppdateringen kan du tillåta slutanvändare att aktivera Bluetooth och parkoppla enheter via Bluetooth (**Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetens ägare, Enhetsbegränsningar** för profiltyp > **Dedikerade enheter** > **Helskärmsläge**: **Flera appar** > **Bluetooth-konfiguration**). 

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md).

Gäller för: Dedikerade Android Enterprise-enheter som körs i helskärmsläge för flera appar

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Skapa och använda OEMConfig-profiler för enhetskonfiguration i Intune <!-- 3305883  -->
I den här uppdateringen stöder Intune konfiguration av Android Enterprise-enheter med OEMConfig. Mer specifikt kan du kan skapa en profil för enhetskonfiguration och använda inställningar för Android Enterprise-enheter med hjälp av OEMConfig (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform).

Stöd för OEM-tillverkare sker för närvarande per varje enskild OEM. Om en OEMConfig-app som du vill ha inte finns i listan över OEMConfig-appar kan du kontakta `IntuneOEMConfig@microsoft.com`.

Om du vill veta mer om den här funktionen kan du gå till [Använda och hantera Android Enterprise-enheter med OEMConfig i Microsoft Intune](../configuration/android-oem-configuration-overview.md).

Gäller för: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows Update-meddelanden  <!-- 3316758, 3316782  -->
Vi har lagt till två *inställningar för användarupplevelse* i de konfigurationer av Windows Update-uppdateringsring som du kan hantera från Intune-konsolen. Nu kan du:
- Blockera eller tillåta användare att [söka efter Windows-uppdateringar](../protect/windows-update-settings.md).
- Hantera den [Windows Update-meddelandenivå](../protect/windows-update-settings.md) som användarna ser.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Nya inställningar för enhetsbegränsningar för enhetsägarbaserad Android Enterprise <!-- 3574254  -->
På Android Enterprise-enheter kan du skapa en profil för enhetsbegränsningar för att tillåta eller begränsa funktion, ange lösenordsregler och mer (**Enhetskonfiguration** > **Profiler** > **Skaoa profil** > välj **Android Enterprise** för plattform > **Endast enhetsägare > Enhetsbegränsningar** för profiltyp). 

Den här uppdateringen innehåller nya lösenordsinställningar, ger fullständig åtkomst till appar i Google Play Store för fullständigt hanterade enheter och mer. Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md). 

Gäller för: Fullständigt hanterade Android Enterprise-enheter

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Söka efter en TPM-kretsuppsättning i en efterlevnadsprincip för Windows 10-enheter <!-- 3617671 -->

Den här funktionen är försenad och planeras att släppas senare.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Uppdaterade ändringar av användargränssnittet för webbläsaren Microsoft Edge på enheter med Windows 10 och senare <!-- 3775833   -->
När du skapar en profil för enhetskonfiguration kan du tillåta eller begränsa Microsoft Edge-funktioner på enheter med Windows 10 och senare (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp >  **Microsoft Edge-webbläsaren**). I den här uppdateringen beskrivs Microsoft Edge-inställningar mer utförligt och är enklare att förstå. 

Om du vill se de här funktionerna går du till [inställningarna för enhetsbegränsningar i Microsoft Edge-webbläsaren](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

Gäller för: Windows 10 och senare

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Utökat stöd för fullständigt hanterade Android Enterprise-enheter (förhandsversion)  <!--   3903241, 3903244, 3903246   -->
Fullständigt hanterade Android Enterprise-enheter ([som först tillkännagavs i januari 2019](whats-new.md#week-of-january-14-2019) är fortfarande i offentlig förhandsversion, men vi har utökat stödet för dem till att omfatta följande: 

- På fullständigt hanterade och dedikerade enheter kan du skapa [efterlevnadsprinciper](../protect/compliance-policy-create-android-for-work.md) till att omfatta lösenordsregler och operativsystemkrav (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Android Enterprise** för plattform > **Enhetsägare** för profiltyp). 

  På dedikerade enheter kan enheten visas som **Inte kompatibel**. Villkorlig åtkomst är inte tillgängligt på dedikerade enheter. Se till att slutföra alla uppgifter eller åtgärder för att göra så att dedikerade enheter uppfyller dina tilldelade principer.

- [Villkorlig åtkomst](../protect/conditional-access.md) – principer för villkorlig åtkomst som gäller för Android gäller även för fullständigt hanterade Android Enterprise-enheter. Användare kan nu registrera sina fullständigt hanterade enheter i Azure Active Directory med hjälp av **Microsoft Intune-appen**. Sedan undersöker och åtgärdar du eventuella efterlevnadsproblem för att få åtkomst till organisationens resurser.

- Ny app för slutanvändare (Microsoft Intune-appen) – det finns en ny app för slutanvändare för fullständigt hanterade Android-enheter som heter **Microsoft Intune**. Den här nya appen är enkel och modern. Den har funktioner som liknar företagsportalappen men för fullständigt hanterade enheter. Mer information finns i [Microsoft Intune-appen på Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

För att konfigurera fullständigt hanterade Android-enheter, gå till **Enhetsregistrering** > **Android-registrering** > **Företagsägda, fullständigt hanterade användarenheter**. Stöd för fullständigt hanterade Android-enheter är fortfarande i förhandsversion, och vissa Intune-funktioner är kanske inte helt funktionella.  

Mer information om den här förhandsversionen finns på vår blogg, [Microsoft Intune – förhandsversion 2 för fullständigt hanterade Android Enterprise-enheter](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Konfigurera profilen om du vill hoppa över vissa av skärmarna i installationsassistenten <!-- 2276470  -->
När du skapar en macOS-registreringsprofil kan du konfigurera den till att hoppa över valfria följande skärmar när en användare går igenom installationsassistenten:
- Utseende
- Visningston
- iCloudStorage Om du skapar en ny profil eller redigerar en profil måste den valda överhoppningsskärmen synkroniseras med Apple MDM-servern.  Användare kan utfärda en manuell synkronisering av enheterna så att det inte sker någon fördröjning i att plocka upp profiländringarna.
Mer information finns i [Registrera macOS-enheter automatiskt med programmet för enhetsregistrering eller Apple School Manager](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Massnamngivning av enheter vid registrering av iOS-företagsenheter<!--3566569  -->
Vid användning av någon av Apples metoder för företagsregistrering (DEP/ABM/ASM) kan du ange ett format för enhetsnamn till att automatiskt namnge inkommande iOS-enheter. Du kan ange ett format som innehåller enhetstyp och serienummer i mallen. Om du vill göra det väljer du **Intune** > **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtoken** > **Välj en token** >**Skapa profil** > **Format för enhetsnamngivning**. Du kan redigera befintliga profiler, men namnet tillämpas endast på nyligen synkroniserade enheter.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Uppdaterat standardmeddelande för tidsgräns på sidan Registreringsstatus <!-- 3959331 -->
Vi har uppdaterat det standardmeddelande för tidsgräns som användare ser när sidan Registreringsstatus (ESP, Enrollment Status Page) överskrider det tidsgränsvärde som angetts i ESP-profilen. Det nya standardmeddelandet är det som användarna ser. Det hjälper dem att ta reda på vilka åtgärder som därnäst ska vidtas med deras ESP-distribution.  

### <a name="device-management"></a>Enhetshantering

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Ta icke-kompatibla enheter ur bruk  <!-- 1827291   -->
Den här funktionen har försenats och kommer i en framtida version.


### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Ändringar i Intune Data Warehouse V1.0 återspeglas i betaversionen <!-- 4403765 -->
När V1.0 introducerades i 1808 skiljde den sig från beta-API:et på några betydande sätt. I 1903 återspeglas ändringarna tillbaka till beta-API-versionen. Om du har viktiga rapporter som använder beta-API-versionen rekommenderar vi starkt att du växlar de rapporterna till V1.0 för att undvika icke-bakåtkompatibla ändringar. Mer information finns i [ändringsloggen för Intune Data Warehouse API](../developer/reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Övervaka status för säkerhetsbaslinje (offentlig förhandsversion) <!-- 3082047 --> 
Vi har lagt till en [per kategori-vy](../protect/security-baselines-monitor.md#per-category-view) i övervakningen av säkerhetsbaslinjer. (Säkerhetsbaslinjer är fortfarande i förhandsversion). Per kategori-vyn visar varje kategori från baslinjen tillsammans med procentandelen enheter som hamnar i varje statusgrupp för respektive kategori. Nu kan du se hur många enheter som inte matchar de enskilda kategorierna, är felkonfigurerade eller inte kan användas.

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Omfångstaggar för Apple VPP-token <!--2371886  -->
Du kan nu lägga till omfångstaggar till Apple VPP-token. Endast användare som har tilldelats med samma omfångstagg får åtkomst till Apple VPP-token med den taggen. VPP-appar och e-böcker som köpts med den token ärver dess omfångstaggar. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Den vecka som börjar 1 april 2019

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Uppdaterade certifikatanslutningsappar  <!-- ICM 113304612 -->
Vi har släppt uppdateringar för både [Intune-certifikatanslutningsappen och PFX-certifikatanslutningsappen för Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors). De nya versionerna åtgärdar flera kända problem.  

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
Tidigare laddade länken **Ladda ned Power BI-fil** på bladet **Intune Data Warehouse** ned en Intune Data Warehouse-rapport (.pbix-fil). Den här rapporten har ersatts med Power BI-efterlevnadsappen. Power BI-efterlevnadsappen kräver inte någon särskild inläsning eller konfiguration. Den öppnas direkt i Power BI-onlineportalen och visar data specifikt för din Intune-klientorganisation baserat på dina autentiseringsuppgifter. I Intune väljer du länken **Konfigurera Intune Data Warehouse** på höger sida av Intune-bladet. Klicka sedan på **Hämta Power BI-appen**. Mer information finns i [Ansluta till Data Warehouse med Power BI](../developer/reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Den vecka som börjar 18 mars 2019

### <a name="app-management"></a>Apphantering

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Distribuera Microsoft Visio och Microsoft Project <!-- 3725386  -->
Du kan nu distribuera Microsoft Visio Pro för Office 365 och skrivbordsklienten för Microsoft Project Online som oberoende appar till Windows 10-enheter som använder Microsoft Intune om du har licenser för dessa appar. I Intune väljer du **Klientappar** > **Appar** > **Lägg till** för att visa bladet **Lägg till app**. På bladet **Lägg till app** väljer du **Windows 10** som **Apptyp**. Välj sedan **Konfigurera appsvit** för att välja appar som ska installeras. Mer information om Office 365-appar för Windows 10-enheter finns i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Ändring av produktnamn för Microsoft Visio Pro för Office 365 <!-- 3593653  -->
**Microsoft Visio Pro för Office 365** kommer nu att kallas **Microsoft Visio Online, abonnemang 2**.  Mer information om Microsoft Visio finns i [Visio Online, abonnemang 2](https://products.office.com/visio/visio-online-plan-2). Mer information om Office 365-appar för Windows 10-enheter finns i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Inställning för teckengräns för Intune-appskyddsprincip (APP) <!-- 3291302  -->
Intune-administratörer kan ange ett undantag till principinställningen **Begränsa klipp ut, kopiera och klistra in med andra appar** för Intune APP.  Som administratör kan du ange det antal tecken som kan klippas ut eller kopieras från en hanterad app. Den här inställningen tillåter delning av det angivna antalet tecken till valfri app oavsett inställningen ”Begränsa klipp ut, kopiera och klistra in med andra appar”. Observera att versionen av Intune-företagsportalappen för Android kräver version 5.0.4364.0 eller senare. Mer information finns i [iOS-dataskydd](../apps/app-protection-policy-settings-ios.md#data-protection), [Android-dataskydd](../apps/app-protection-policy-settings-android.md#data-protection) och [Granska loggarna för klientappskydd](../apps/app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>ODT-XML (Distributionsverktyg för Office) för Office ProPlus-distribution <!-- 3192477   -->
Du kommer att kunna tillhandahålla ODT-XML (Distributionsverktyg för Office) när du skapar en instans av Office Pro Plus i Intune-administratörskonsolen. Detta ger större anpassningsbarhet om de befintliga alternativen för användargränssnittet i Intune inte uppfyller dina behov. Mer information finns i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](../apps/apps-add-office365.md) och [Konfigurationsalternativ för distributionsverktyget för Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Appikoner visas nu med en automatiskt genererad bakgrund <!-- 1429026  -->
I Windows-företagsportalappen visas appikoner nu med en automatiskt genererad bakgrund som baseras på ikonens huvudsakliga färg (om den kan identifieras). När så är tillämpligt ersätter den här bakgrunden den grå kantlinje som tidigare fanns på appanelerna. Användarna ser den här ändringen i versioner senare än 10.3.3451.0 av företagsportalen.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Installera tillgängliga appar med hjälp av företagsportalappen efter massregistrering för Windows <!-- 2751523   -->
Windows-enheter som registreras till Intune med hjälp av [massregistrering för Windows](../enrollment/windows-bulk-enroll.md) (etableringspaket) kommer att kunna använda företagsportalappen för att installera tillgängliga appar. Mer information om företagsportalappen finns i [Lägga till Windows 10-företagsportalen manuellt](../apps/store-apps-company-portal-app.md) och [Så konfigurerar du Microsoft Intune-företagsportalappen](../apps/company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Microsoft Teams-appen kan väljas som en del av Office-appsviten <!-- 3828932  -->
Microsoft Teams-appen kan inkluderas eller uteslutas som en del av installationen av Office Pro Plus-appsviten. Den här funktionen fungerar för Office Pro Plus, build-nummer 16.0.11328.20116+. Användaren måste logga ut och sedan logga in på enheten för att slutföra installationen. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. Välj en av **Office 365-svitapptyperna** och välj sedan **Konfigurera appsvit**.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Starta en app automatiskt när flera appar körs i helskärmsläge på enheter med Windows 10 och senare <!-- 2351390 -->

På enheter med Windows 10 och senare kan du köra en enhet i helskärmsläge och köra många appar. I den här uppdateringen finns en **AutoLaunch**-inställning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Helskärmsläge** för profiltyp > **Helskärmsläge för flera appar**). Använd den här inställningen för att starta en app automatiskt när användaren loggar in på enheten.

En lista och beskrivningar av alla inställningar för helskärmsläge finns i [Inställningar för enheter med Windows 10 (och senare) som ska köras med helskärmsläge i Intune](../configuration/kiosk-settings-windows.md).

Gäller för: Windows 10 och senare

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Arbetsloggar visar även information om icke-kompatibla enheter <!-- 4063755  -->
När Intune-loggar dirigeras till Azure Monitor-funktioner kan du även dirigera arbetsloggarna. I den här uppdateringen ger arbetsloggarna även information om icke-kompatibla enheter. 

Mer information om den här funktionen finns i [Skicka loggdata till lagring, händelsehubbar eller logganalys i Intune](../review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Dirigera loggar till Azure Monitor i fler Intune-arbetsbelastningar <!-- 3804627 -->
I Intune kan du dirigera granskningsloggar och arbetsloggar till händelsehubbar, lagring och logganalys i Azure Monitor (**Intune** > **Övervakning** > **Diagnostikinställningar**). I den här uppdateringen kan du dirigera loggarna i fler Intune-arbetsbelastningar, däribland efterlevnad, konfigurationer, klientappar och mer. 

Mer information om dirigering av loggar till Azure Monitor finns i [skicka data till lagring, händelsehubbar eller logganalys](../review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Skapa och använda mobilitetstillägg på Android Zebra-enheter i Intune <!-- 3305880   -->
I den här uppdateringen stöder Intune konfiguration av Android Zebra-enheter. Mer specifikt kan du skapa en profil för enhetskonfiguration och tillämpa inställningar på Android Zebra enheter med hjälp av MX-profiler (Mobility Extensions) som genereras av StageNow (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android** för plattform > **MX-profil (endast Zebra)** för profiltyp).

Mer information om den här funktionen finns i [Använd och hantera Zebra-enheter med mobilitetstillägg i Intune](../configuration/android-zebra-mx-overview.md).

Gäller för: Android

### <a name="device-management"></a>Enhetshantering

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Krypteringsrapport för Windows 10-enheter (i allmänt tillgänglig förhandsversion)<!-- 2351538 -->  
Använd den nya [krypteringsrapporten (förhandsversion)](../protect/encryption-monitor.md) till att visa information om krypteringsstatusen för dina Windows 10-enheter. Bland den tillgängliga informationen finns en enhets TPM-version, krypteringsberedskap och -status, felrapportering och mer.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Använd BitLocker-återställningsnycklar från Intune-portalen (i allmänt tillgänglig förhandsversion) <!-- 2351547   -->  
Du kan nu använda Intune för att [visa information](../protect/encryption-monitor.md) om BitLocker-nyckel-ID och BitLocker-återställningsnycklar från Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge-stöd för Intune-scenarier i iOS-enheter och Android-enheter <!-- 3411007 -->
Microsoft Edge kommer att stödja samma hanteringsscenarier som Intune Managed Browser samt förbättringar av användarupplevelsen. Microsoft Edge Enterprise-funktioner som aktiveras av Intune-principer inbegriper dubbel identitet, integrering med appskyddsprincip, integrering av Azure-programproxy samt hanterade favoriter och genvägar för startsidan. Mer information finns i [Microsoft Edge-support](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Inaktuellt stöd för enheter med endast EAS för Exchange Online/Intune-anslutningsapp <!--3105122  -->
Intune-konsolen stöder inte längre visning och hantering av enheter med endast EAS som är anslutna till Exchange Online med Intune-anslutningsappen. I stället har du följande alternativ:
- Registrera enheter i hantering av mobilenheter (MDM)
- Använd Intunes appskyddsprinciper för att hantera dina enheter
- Använd Exchange-kontrollerna enligt beskrivningen i [Klienter och mobilt i Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Söka efter en exakt enhet med [namn] på sidan Alla enheter <!--4254930 -->
Du kan nu söka efter ett exakt enhetsnamn. Gå till **Intune** > **Enheter** > **Alla enheter** > i sökrutan omger du enhetsnamnet med {} för att söka efter en exakt matchning. Det kan till exempel vara **{Enhet12345}** .

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Stöd för ytterligare anslutningsappar på sidan Status för klientorganisation <!-- 3617202  -->
[Sidan Status för klientorganisation](../tenant-status.md) visar nu statusinformation för ytterligare anslutningsappar, däribland *Windows Defender Advanced Threat Protection* (ATP) och andra Mobile Threat Defense-anslutningsappar.

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
Microsoft Edge kommer att stödja samma hanteringsscenarier som Intune Managed Browser samt förbättringar av användarupplevelsen. Microsoft Edge Enterprise-funktioner som aktiveras av Intune-principer inbegriper dubbel identitet, integrering med appskyddsprincip, integrering av Azure-programproxy samt hanterade favoriter och genvägar för startsidan. Mer information finns i [Microsoft Edge-support](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Den vecka som börjar 25 februari 2019

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell-modul <!-- 951068  -->
Intune PowerShell-modulen, som ger stöd för Intune-API:et via Microsoft Graph, är nu tillgänglig i [Microsoft PowerShell-galleriet](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Information om hur du använder den här modulen](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Scenarioexempel där den här modulen används](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Förbättrat stöd för leveransoptimering  <!--3183757  -->
Vi har utökat stödet i Intune för konfiguration av leveransoptimering. Du kan nu konfigurera en utökad lista över [inställningar för leveransoptimering](../configuration/delivery-optimization-settings.md) och rikta den till dina enheter direkt från Intune-konsolen.


## <a name="week-of-february-18-2019"></a>Den vecka som börjar 18 februari 2019

### <a name="app-management"></a>Apphantering

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune använder Google Play Protect-API:er på Android-enheter <!-- 2577355   -->
Vissa IT-administratörer hanterar en BYOD-miljö där slutanvändare kan rota eller jailbreaka sin mobiltelefon. Även om beteendet inte är illa menat blir resultatet att det kringgår många Intune-principer som har angetts för att skydda organisationens data och slutanvändarenheter. Därför har Intune rot- och jailbreak-identifiering för både registrerade och oregistrerade enheter. Med den här versionen använder Intune nu Google Play Protect-API:er som tillägg till våra befintliga rotidentifieringskontroller för oregistrerade enheter. Google delar inte alla rotidentifieringskontroller som sker men vi förväntar oss att dessa API:er kan identifiera användare som har rotat sina enheter av någon anledning från enhetsanpassning för att kunna få nyare OS-uppdateringar på äldre enheter. Dessa användare kan sedan blockeras från åtkomst till företagsdata eller så kan deras företagskonton rensas bort från deras principaktiverade appar. Ett ytterligare mervärde är att IT-administratören nu har flera rapporteringsuppdateringar på bladet Intune-appskydd – rapporten ”Flaggade användare” visar vilka användare som identifieras via SafetyNet API-genomsökningen från Google Play Protect, rapporten ”Potentiellt skadliga appar” visar vilka appar som identifieras via Googles Verify Apps API-genomsökning. Den här funktionen är tillgänglig på Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Win32-appinformation tillgänglig på bladet Felsökning <!-- 2617342   -->
Du kan nu samla in felloggfiler för en Win32-appinstallation från Intune-appens blad **Felsökning**. Mer information om felsökning av appinstallationer finns i [Felsöka appinstallationsproblem](./../apps/troubleshoot-app-install.md) och [Felsöka problem med Win32-appar](./../apps/troubleshoot-app-install.md#win32-app-installation-troubleshooting).

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
En ny skärm som heter **Appkategorier** har lagts till i syfte att förbättra upplevelsen för bläddring och val av appar i företagsportalen för Windows 10. Användarna ser nu sina appar sorterade i kategorier som **Aktuella**, **Utbildning** och **Produktivitet**. Den här ändringen finns i versioner 10.3.3451.0 och senare av företagsportalen. Om du vill se den nya skärmen går du till [Nyheter i användargränssnittet för appen](whats-new-app-ui.md). Mer information om appar i företagsportalen finns i [Installera och dela appar på din enhet](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI-efterlevnadsapp <!-- 1455231 doc-work-item -->
Få åtkomst till ditt Intune-informationslager i Power BI Online med hjälp av [Intune-efterlevnadsappen (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Med den här Power BI-appen kan du nu komma åt och dela i förväg skapade rapporter utan någon konfiguration och utan att lämna webbläsaren. Mer information finns i [Ändringslogg – Power BI-efterlevnadsapp](../developer/reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>PowerShell-skript kan köras på en 64-bitarsvärd på 64-bitarsenheter <!-- 1862675   -->
När du lägger till ett PowerShell-skript i en enhetskonfigurationsprofil körs skriptet alltid i 32 bitar, även på 64-bitars operativsystem. Med den här uppdateringen kan en administratör köra skriptet på en 64-bitars PowerShell-värd på 64-bitarsenheter (**Enhetskonfiguration** > **PowerShell-skript** > **Lägg till** > **Konfigurera** > **Kör skript i 64-bitars PowerShell-värd**).

Mer information om användning av PowerShell finns i [PowerShell-skript i Intune](../apps/intune-management-extension.md).

Gäller för: Windows 10 och senare

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>macOS-användare uppmanas att uppdatera sitt lösenord <!-- 1873216 -->
Intune framtvingar inställningen **ChangeAtNextAuth** på macOS-enheter. Den här inställningen påverkar slutanvändare och enheter som har efterlevnadsprinciper för lösenord eller lösenordsprofiler för enhetsbegränsning. Slutanvändare uppmanas en gång att uppdatera sitt lösenord. Den här uppmaningen sker när en användare för första gången kör en uppgift som kräver autentisering, till exempel inloggning på enheten. Användare kan även uppmanas att uppdatera sitt lösenord när de gör något som kräver administratörsprivilegier, till exempel att begära nyckelringsåtkomst. 

Eventuella nya eller befintliga ändringar av lösenordsprinciper av administratören gör att användarna återigen uppmanas att uppdatera lösenordet.

Gäller för:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521------"></a>Tilldela SCEP-certifikat till en användarlös macOS-enhet    <!-- 2340521    -->
Du kan tilldela SCEP-certifikat (Simple Certificate Enrollment Protocol ) med hjälp av enhetsattribut till macOS-enheter, inklusive enheter utan användartillhörighet, och koppla certifikatprofilen till Wi-Fi- eller VPN-profiler. Detta utökar det stöd som vi redan har för att [tilldela SCEP-certifikat till enheter med och utan användartillhörighet](../protect/certificates-profile-scep.md) som kör Windows, iOS eller Android.  Den här uppdateringen lägger till alternativet att välja certifikattypen *Enhet* när du konfigurerar en SCEP-certifikatprofil för macOS.

Gäller för: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Uppdatering av användargränssnittet i Intune för villkorlig åtkomst   <!-- 2432313   -->
Vi har gjort förbättringar av användargränssnittet för villkorlig åtkomst i Intune-konsolen. Dessa omfattar:
- Intune-bladet *Villkorlig åtkomst* har ersatts med bladet från Azure Active Directory. På så sätt har du åtkomst till alla inställningar och konfigurationer för [villkorlig åtkomst](../protect/conditional-access.md) (som fortfarande är en Microsoft Azure AD-teknik) från Intune-konsolen. 
- Vi har bytt namn bladet *Lokal åtkomst* till *Exchange-åtkomst* och flyttat konfigurationen av *Exchange-tjänstens anslutningsapp* till det här bladet med nytt namn.  Ändringen konsoliderar det ställe där du [konfigurerar och övervakar information relaterad till onlinebaserad och lokal Exchange](../protect/exchange-connector-install.md).  

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

- [Inställningar för enheter med Windows 10 (och senare) som ska köras med helskärmsläge](../configuration/kiosk-settings-windows.md)
- [Enhetsbegränsningar för Microsoft Edge-webbläsaren](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)
- [Enhetsbegränsningar för favoriter och sökning](../configuration/device-restrictions-windows-10.md##favorites-and-search)

Gäller för: Windows 10 och senare

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Nya inställningar för enhetsbegränsning för iOS-enheter och macOS-enheter <!-- 3448774   -->
Du kan begränsa vissa inställningar och funktioner på enheter som kör iOS och macOS (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** eller **macOS** som plattform > **Enhetsbegränsningar** som profiltyp). Den här uppdateringen lägger till fler funktioner och inställningar som du kan kontrollera, till exempel ange skärmtid, ändra eSIM-inställningar och mobilabonnemang och mer på iOS-enheter. Det går även att fördröja programuppdateringars synlighet för användaren och blockera innehållscachelagring på macOS-enheter. 

Funktioner och inställningar som du kan begränsa finns här:

- [Inställningar för iOS-enhetsbegränsning](../configuration/device-restrictions-ios.md)
- [Inställningar för macOS-enhetsbegränsning](../configuration/device-restrictions-macos.md)

Gäller för:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>”Kioskenheter” kallas nu ”dedikerade enheter” på Android Enterprise-enheter <!-- 3598402   -->
För att stämma överens med Android-terminologi ändras **kioskenheter** till **dedikerade enheter** för Android Enterprise-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > ** Android Enterprise för plattform > **Endast enhetens ägare** > **Enhetsbegränsningar** > **Dedikerade enheter**).

Om du vill se de tillgängliga inställningarna går du till [Enhetsinställningar för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Gäller för:  
Android enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari och iOS-inställningarna för att fördröja visning av programuppdateringar för användaren flyttas i Intune-användargränssnittet <!-- 3640850, 3803313   -->
För iOS-enheter kan du ange Safari-inställningar och konfigurera programuppdateringar. I den här uppdateringen flyttas dessa till olika delar av Intune-användargränssnittet:

- Safari-inställningarna flyttades från **Safari** (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** som plattform > **Enhetsbegränsningar** som profiltyp) till **[Inbyggda appar](../configuration/device-restrictions-ios.md#built-in-apps)** .
- Inställningen för att **fördröja visning av programuppdateringar för användaren för övervakade iOS-enheter** (**Programuppdateringar** > **Uppdateringsprinciper för iOS**) flyttas till **Enhetsbegränsningar** >  **[Allmänt](../configuration/device-restrictions-ios.md#general)** .  Information om påverkan på befintliga principer finns i [iOS-programuppdateringar](../protect/software-updates-ios.md#configure-the-policy). 

Se följande för en lista över inställningarna:

- [iOS-enhetsbegränsningar](../configuration/device-restrictions-ios.md) 
- [iOS-programuppdateringar](../protect/software-updates-ios.md)

Den här funktionen gäller för: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>Aktivering av begränsningar i enhetsinställningarna byter namn till Skärmtid på iOS-enheter <!-- 3699164   -->
Du kan konfigurera **Aktivera begränsningar i enhetsinställningarna** på övervakade iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Ny profil** > **iOS** som plattform > **Enhetsbegränsningar** som profiltyp > **Allmänt**). I den här uppdateringen har den här inställningen bytt namn till **Skärmtid (endast övervakat)** . 

Beteendet är samma. Specifikt: 

- iOS 11.4.1 och tidigare: **Blockera** förhindrar slutanvändare att ange egna begränsningar i enhetsinställningarna. 
- iOS 12.0 och senare: **Blockera** förhindrar slutanvändare att ange en egen **skärmtid** i enhetsinställningarna, som innehålls- och sekretessbegränsningar. Fliken för begränsningar visas inte längre på enheter uppgraderade till iOS 12.0. Dessa inställningar finns i **Skärmtid**. 

En lista över inställningarna finns i [iOS-enhetsbegränsningar](../configuration/device-restrictions-ios.md#general).

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

Standardinställningar och antal inställningar förblir detsamma, men den här ändringen gör att användarna kan förstå, navigera och använda inställningar enklare för att tillämpa valda appskyddsprinciper. Mer information finns i [iOS-inställningar](../apps/app-protection-policy-settings-ios.md) och [Android-inställningar](../apps/app-protection-policy-settings-android.md).

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
> Om du använder principer för Intune-appskydd till att hantera åtkomsten för företagsidentiteter bör du inte aktivera att **kräva biometri**. Mer information finns i **Kräva företagsautentiseringsuppgifter för åtkomst** för [iOS-åtkomstinställningar](../apps/app-protection-policy-settings-ios.md#access-requirements) och [Android-åtkomstinställningar](../apps/app-protection-policy-settings-android.md#access-requirements).

Mer information finns i [Konfigurationsinställningar för Microsoft Outlook](../apps/app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Ta bort Android Enterprise-appar <!-- 1352553 -->
Du kan ta bort hanterade Google Play-appar från Microsoft Intune. Om du vill ta bort en hanterad Google Play-app öppnar du Microsoft Intune i Azure-portalen och väljer **Klientappar** > **Appar**. Från listan över appar väljer du ellipserna (...) till höger om den hanterade Google Play-appen och väljer sedan **Ta bort** från den visade listan. När du tar bort en hanterad Google Play-app från applistan blir den hanterade Google Play-appen automatiskt ej godkänd.

#### <a name="managed-google-play-app-type----1352580---"></a>Hanterade Google Play-apptyper <!-- 1352580 -->
Den **hanterade Google Play**-apptypen gör att du kan lägga till mer specifikt [hanterade Google Play-appar](https://play.google.com/work/search?q=microsoft&c=apps) till Intune. Som Intune-administratör kan du bläddra, söka, godkänna, synkronisera och tilldela godkända hanterad Google Play-appar i Intune.  Du behöver inte längre bläddra till den hantera Google Play-konsolen separat och du behöver inte längre autentisera dig på nytt.  I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** väljer du **Hanterat Google Play-konto** som apptyp.

### <a name="default-android-pin-keyboard----3802457---"></a>Standardtangentbord för PIN-kod i Android <!-- 3802457 -->
För slutanvändare som har angett en PIN-kod för Intune-appskydd (APP) på sina Android-enheter med PIN-kodtypen ”Numerisk” visas nu standardtangentbordet för Android istället för det fasta Android-tangentbordsgränssnittet som utformats tidigare. Den här ändringen har gjorts för att vara konsekvent när standardtangentbord används på både Android och iOS, för båda PIN-typerna ”Numerisk” och/eller ”Lösenord”. Mer information om inställningar för slutanvändaråtkomst på Android, till exempel PIN-kod för APP finns i [Åtkomstkrav för Android](../apps/app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Använda Microsofts rekommenderade inställningar med säkerhetsbaslinjer (allmänt tillgänglig förhandsversion) <!-- 2055484   -->

Intune integrerar med andra tjänster som fokuserar på säkerhet, inklusive Windows Defender ATP och Office 365 ATP. Kunder efterfrågar en gemensam strategi och en sammanhängande uppsättning säkerhetsarbetsflöden från slutpunkt till slutpunkt för alla Microsoft 365-tjänster. Vårt mål är att optimera strategier och skapa lösningar som kan hantera säkerhetsåtgärder och vanliga administratörsuppgifter. I Intune vill vi uppnå det här målet genom att publicera en uppsättning Microsoft-rekommenderade ”säkerhetsbaslinjer” (**Intune** > **Security baselines** ((Säkerhetsbaslinjer)).  En administratör kan skapa säkerhetsprinciper direkt från dessa baslinjer, och sedan distribuera dem till sina användare. Du kan också anpassa rekommendationerna om bästa praxis för att uppfylla behoven i organisationen. Intune kontrollerar att enheterna uppfyller baslinjerna och meddelar administratören om användare eller enheter inte uppfyller efterlevnadskraven.

Den här funktionen är en offentlig förhandsversion, så profiler som skapas nu flyttas inte över till säkerhetsbaslinjemallar som är allmänt tillgängliga. Du bör inte planera att använda dessa förhandsmallar i produktionsmiljö.

Läs mer om säkerhetsbaslinjer i [Skapa en säkerhetsbaslinje för Windows 10 i Intune](../protect/security-baselines-monitor.md).

Den här funktionen gäller för: Windows 10 och senare

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Icke-administratörer kan aktivera BitLocker på Windows 10-enheter som är anslutna till Azure AD<!-- 2147379   -->
När du aktiverar BitLocker-inställningar på Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10 och senare** för plattform > **Endpoint protection** för Profiltyp > **Windows-kryptering**), lägger du till BitLocker-inställningar. 

Den här uppdateringen innehåller en ny inställning för BitLocker för att låta standardanvändare (icke-administratörer) aktivera kryptering. 

De här inställningarna finns i [Inställningar för slutpunktsskydd för Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Kontrollera Configuration Manager-kompatibilitet <!-- 2192052  eepublished  -->
Den här uppdateringen innehåller en ny kompatibilitetsinställning för System Center Configuration Manager (**Enhetskompabilitet** > **Principer** > **Skapa princip** > **Windows 10 och senare** > **Configuration Manager-kompabilitet**). Configuration Manager skickar signaler till Intune-kompatibilitet. Med hjälp av inställningen kan du kräva att alla Configuration Manager-signaler returnerar ”kompatibel”.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd är enheten inte kompatibel i Intune.

[Configuration Manager-kompatibilitet](../protect/compliance-policy-create-windows.md#configuration-manager-compliance) beskriver den här inställningen.

Gäller för: Windows 10 och senare

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Anpassa bakgrund på övervakade iOS-enheter med hjälp av en profil för enhetskonfiguration <!-- 2809324   -->
När du skapar en profil för enhetskonfiguration för iOS-enheter kan du anpassa vissa inställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsfunktioner** för profiltypen). Den här uppdateringen innehåller nya inställningar för **Bakgrund** som gör att administratörer kan använda en .png-, .jpg- eller .jpeg-bild på startsidan eller låsskärmen. Inställningar för bakgrund gäller endast för övervakade enheter. 

En lista över de här inställningarna finns i [Funktionsinställningar för iOS-enheter](../configuration/ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Helskärmsläge för Windows 10 är allmänt tillgängligt <!-- 3594661  -->
I den här uppdateringen är funktionen helskärmsläge på Windows 10 och senare enheter allmänt tillgängligt (GA). Alla inställningar som du kan lägga till och konfigurera finns i [Inställningar för helskärmsläge för Windows 10 (och senare)](../configuration/kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Kontaktdelning via Bluetooth har tagits bort i Enhetsbegränsningar > Enhetens ägare för Android Enterprise <!-- 3598396   -->
När du skapar en profil för enhetsbegränsningar för Android Enterprise-enheter finns inställningen **Dela kontakter via Bluetooth**. I den här uppdateringen tas inställningen **Dela kontakter via Bluetooth** bort (**Enhetskonfiguration** > **Profiler**  >  **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar > Enhetens ägare** för profiltyp > **Allmän**). 

Inställningen **Dela kontakter via Bluetooth** har inte stöd för hantering av Android Enterprise-enhetens ägare. Så när den här inställningen tas bort, påverkar det inga enheter eller klienter, även om den här inställningen är aktiverad och konfigurerad i din miljö.

Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](../configuration/device-restrictions-android-for-work.md).

Gäller för: Ägare av Android Enterprise-enhet

### <a name="device-management"></a>Enhetshantering

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Stöd för selektiv rensning för WIP-WE-enheter <!-- 1434452 -->
Med WIP-WE (Windows Information Protection Without Enrollment) kan kunder skydda sina företagsdata på Windows 10-enheter utan att fullständig MDM-registrering krävs. När dokument skyddas med en WIP-WE-princip kan skyddade data rensas selektivt av en Intune-administratör. Genom att välja användaren och enheten, och skicka en rensningsbegäran, blir alla data som skyddades via WIP-WE-principen oanvändbara. Från Intune på Azure-portalen väljer du **Mobilapp** > **Selektiv radering av app**.

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Ny arbetsloggar och möjligheten att skicka loggar till Azure Monitor-tjänster <!-- 3762211  -->
Intune har inbyggd granskningsloggning som spårar händelser när de ändras. Den här uppdateringen innehåller nya loggningsfunktioner, inklusive: 
- Arbetsloggar (förhandsversion) som visar information om användare och enheter som registrerats, inklusive lyckade och misslyckade försök.
- Granskningsloggarna och arbetsloggarna kan skickas till Azure Monitor, inklusive lagringskonton, händelsehubbar och logganalyser. De här tjänsterna gör att du kan lagra och använda analyser som Splunk och QRadar samt få visualiseringar av dina loggningsdata.

[Skicka data till lagring, händelsehubbar eller logganalyser i Intune](../review-logs-using-azure-monitor.md) har mer information om den här funktionen.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Hoppa över flera skärmar för installationsassistenten på en iOS DEP-enhet <!-- 2687509  -->
Förutom de skärmar som du kan hoppa över just nu kan du ange att iOS DEP-enheter hoppar över följande skärmar i installationsassistenten när en användare registrerar enheten: Skärmton, Sekretess, Android-migrering, Start-knapp, iMessage och FaceTime, Registrering, Bevaka migrering, Utseende, Skärmtid, Programuppdatering, SIM-installation.
Om du vill välja vilka skärmar som ska hoppas över, går du till **Enhetsregistrering** > **Apple-registrering** > **Tokens för registreringsprogram** > välj en token > **Profiler** > välj en profil > **Egenskaper** > **Anpassning av installationsassistenten** > välj **Dölj** för alla skärmar som du vill hoppa över > **OK**.
Om du skapar en ny profil eller redigerar en profil måste den valda överhoppningsskärmen synkroniseras med Apple MDM-servern. Användare kan utfärda en manuell synkronisering av enheterna så att det inte sker någon fördröjning i att plocka upp profiländringarna.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Appdistribution för Android Enterprise APP-WE <!-- 1171203 -->
För Android-enheter i ett distributionsscenario med en appskyddsprincip utan registrering (APP-WE) kan du nu använda hanterad Google Play för att distribuera store-appar och LOB-appar till användare. Mer specifikt kan du ge slutanvändarna en appkatalog och installationsfunktioner som inte längre kräver att slutanvändare lättar på säkerhetshållningen för sina enheter genom att tillåta installationer från okända källor. Dessutom kan det här distributionsscenariot ge en förbättrad slutanvändarupplevelse.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Veckan som börjar den 14 januari 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Förhandsgranskning av stöd för företagsägda, fullständigt hanterade Android-enheter <!-- 1574342  -->
Nu har Intune fullt stöd för hanterade Android-enheter, ett företagsägt scenario av ”enhetsägare” där enheter hanteras noggrant av IT och är kopplade till enskilda användare. Detta gör att administratörer kan hantera hela enheten, tillämpa en utökad uppsättning principkontroller som inte är tillgängliga för arbetsprofiler och begränsa användare från att installera appar från hanterad Google Play endast. Mer information finns i artiklarna om att [konfigurera Intune-registrering av fullständigt hanterade Android-enheter](../enrollment/android-fully-managed-enroll.md) och att [registrera dedikerade enheter eller fullständigt hanterade enheter](../enrollment/android-dedicated-devices-fully-managed-enroll.md).  Observera att den här funktionen är en förhandsversion. Vissa Intune-funktioner, till exempel certifikat, efterlevnad och villkorlig åtkomst, är inte tillgängliga med fullständigt hanterade Android-användarenheter.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Veckan som börjar med 7 januari 2019

### <a name="app-management"></a>Apphantering

#### <a name="intune-app-pin----2298397---"></a>Intune-appens PIN-kod <!-- 2298397 -->
Som IT-administratör kan du nu konfigurera hur många dagar en användare kan vänta tills Intune-appens PIN-kod måste ändras. Den nya inställningen är *Återställ PIN-kod efter antal dagar* och är tillgänglig i Azure-portalen genom att välja **Intune** > **Klientappar** > **Appskyddsprinciper** > **Skapa princip** > **Inställningar** > **Åtkomstbehörigheter**. Den här funktionen, som är tillgänglig för [iOS](../apps/app-protection-policy-settings-ios.md)- och [Android](../apps/app-protection-policy-settings-android.md)-enheter, stöder ett positivt heltalsvärde.


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune-enhetens rapportfält <!-- 2748738 -->
Intune ger ytterligare fält för enhetsrapportering inklusive appregistrerings-ID, Android-tillverkare, modell och version av säkerhetsuppdatering samt iOS-modell. I Intune är dessa fält tillgängliga genom att välja **Klientappar** > **Appskyddsstatus** och sedan välja **Appskyddsrapport: iOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodell (Android och iOS) och lägsta inställning för version av Android-säkerhetsuppdatering. 


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrativa mallar finns i offentlig förhandsversion och flyttas till sin egen konfigurationsprofil <!-- 3322847 -->

Administrativa mallar i Intune (**Enhetskonfiguration** > **Administrationsmallar**) är för tillfället i allmänt tillgänglig förhandsvisning. I denna uppdatering:

- De administrativa mallarna innehåller ungefär 300 inställningar som kan hanteras i Intune. De här inställningarna fanns tidigare endast i redigeraren.
- Administrativa mallar finns i offentlig förhandsversion.
- Administrativa mallar flyttar från **Enhetskonfiguration** > **Administrativa mallar** till **Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Windows 10 och senare** > i **Profiltyp**, välj **Administrativa mallar**.
- Rapportering är aktiverad

Mer information om den här funktionen finns i [Windows 10-mallar för att konfigurera grupprincipinställningar](../configuration/administrative-templates-windows.md).

Gäller för: Windows 10 och senare

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Använda S/MIME för att kryptera och signera flera enheter för en användare  <!-- 1333642 -->
Den här uppdateringen innehåller S/MIME-e-postkryptering som använder en ny importerad certifikatprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj plattformen > profiltypen **PKCS-importerat certifikat**). Du kan importera certifikat i PFX-format i Intune. Intune kan sedan leverera samma certifikat till flera enheter som registrerats av en enda användare. Detta omfattar även följande:
- Den interna e-postprofilen för iOS har stöd för att aktivera S/MIME-kryptering med importerade certifikat i PFX-format.
- Den interna e-postappen på Windows Phone 10-enheter använder S/MIME-certifikatet automatiskt.
- Det privata certifikatet kan levereras över flera plattformar. Men alla e-postappar har inte stöd för S/MIME.
- På andra plattformar kan du behöva konfigurera e-postappen manuellt för att aktivera S/MIME.  
- E-postappar som har stöd för S/MIME-kryptering kan hantera hämtning av certifikat för S/MIME-kryptering av e-post på ett sätt som MDM inte stöder, till exempel genom att läsa från utgivarens certifikatarkiv.
Mer information om den här funktionen finns i [S/MIME-översikt för att signera och kryptera e-post](../protect/certificates-s-mime-encryption-sign.md).
Stöds på: Windows, Windows Phone 10, macOS, iOS och Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nya alternativ för att automatiskt ansluta och bevara regler vid användning av DNS-inställningarna på enheter med Windows 10 och senare <!-- 1333665, 2999078 -->
I Windows 10 och senare enheter kan du skapa en VPN-profil som innehåller en lista över DNS-servrar för att lösa domäner, som till exempel contoso.com. Den här uppdateringen omfattar nya inställningar för namnmatchning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **Windows 10 och senare** för plattform > välj **VPN** för Profiltyp > **DNS-inställningarna** >**Lägg till**): 
- **Anslut automatiskt**: När den är **Aktiverad**, ansluter enheten automatiskt till VPN-anslutningen när en enhet kontaktar en domän som du anger, t.ex contoso.com.
- **Beständig**: Som standard är alla NRPT-regler (principtabell för namnmatchning) aktiva så länge enheten är ansluten med hjälp av den här VPN-profilen. När inställningen är **Aktiverad** för en NRPT-regel förblir regeln aktiv på enheten, även om VPN-anslutningen kopplas bort. Regeln gäller tills VPN-profilen tas bort eller tills regeln tas bort manuellt, vilket kan göras med hjälp av PowerShell.
[Windows 10 VPN-inställningar](../configuration/vpn-settings-windows-10.md) beskriver inställningarna. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Använda identifiering av betrott nätverk för VPN-profiler på Windows 10-enheter <!-- 1500165 -->
När du använder identifiering av betrott nätverk kan du förhindra VPN-profiler från att automatiskt skapa en VPN-anslutning när användaren redan är i ett betrott nätverk. Med den här uppdateringen kan du lägga till DNS-suffix om du vill aktivera identifiering av betrott nätverk på enheter som kör Windows 10 och senare (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **VPN** för profiltyp).
[Windows 10-VPN-inställningar](../configuration/vpn-settings-windows-10.md) visar en lista över aktuella VPN-inställningar.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Hantera Windows Holographic for Business-enheter som används av flera användare <!-- 1907917, 1063203 -->
För närvarande kan du konfigurera delade datorinställningar på Windows 10- och Windows Holographic for Business-enheter med en anpassad OMA-URI-inställning. Med den här uppdateringen läggs en ny profil till för att konfigurera delade enhetsinställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** > **Delad enhet för flera användare**).
Mer information om den här funktionen finns i [Intune-inställningar för att hantera delade enheter](../configuration/shared-user-device-settings.md).
Gäller för: Windows 10 och senare, Windows 10 Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nya Windows 10 Update-inställningar <!--2626030  2512994  -->
För dina [Windows 10-uppdateringsringar](../protect/windows-update-for-business-configure.md) kan du konfigurera:
- **Funktionssätt för automatisk uppdatering** – Använd ett nytt alternativ, *Återställ till standard*, för att återställa de ursprungliga inställningarna för automatisk uppdatering på Windows 10-datorer som kör *uppdateringen från oktober 2018*
- **Blockera användaren från att pausa Windows-uppdateringar** – Konfigurera en ny programuppdateringsinställning som gör att du kan blockera eller tillåta användarna att pausa uppdateringsinstallationen från *Inställningar* på deras datorer. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>E-postprofiler för iOS kan använda S/MIME-signering och kryptering <!-- 2662949 -->
Du kan skapa en e-postprofil som innehåller olika inställningar. Den här uppdateringen inkluderar S/MIME-inställningar som kan användas för signering och kryptering av e-postmeddelanden på iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > **E-post** för profiltyp).
[iOS e-postkonfigurationsinställningar](../configuration/email-settings-ios.md) visar en lista över inställningarna.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Vissa BitLocker-inställningar har stöd för Windows 10 Pro-versionen<!-- 2727036 -->
Du kan skapa en konfigurationsprofil som anger inställningar för slutpunktsskydd för Windows 10-enheter, inklusive BitLocker. Den här uppdateringen lägger till stöd för Windows 10 Professional-versionen för vissa BitLocker-inställningar. De här skyddsinställningarna finns i [Inställningar för slutpunktsskydd för Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Konfiguration av delad enhet har bytt namn till Meddelande på låsskärm för iOS-enheter i Azure-portalen<!-- 2809362 -->
När du skapar en profil för iOS-enheter kan du lägga till inställningar för **Konfiguration för delad enhet** för att visa specifik text på låsskärmen. Den här uppdateringen innehåller följande ändringar: 
- Inställningarna **Konfiguration för delad enhet** i Azure-portalen har bytt namn till ”Meddelande på låsskärmen (endast övervakat)” (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > välj **Enhetsfunktioner** för Profiltyp > **Meddelande på låsskärmen**).
- När du lägger till meddelanden på låsskärmen kan du infoga ett serienummer, ett enhetsnamn eller ett annat enhetsspecifikt värde som en variabel i **Resurstagginformation** och **Fotnot på låsskärmen**. Du kan till exempel ange `Device name: {{devicename}}` eller `Serial number is {{serialnumber}}` med hjälp av klammerparenteser. [iOS-token](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) visar en lista över de tillgängliga token som kan användas.
[Inställningar för att visa meddelanden på låsskärmen](../configuration/ios-device-features-settings.md#lock-screen-message) visar en lista över inställningarna.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nya inställningar för enhetsbegränsning av App Store, dokumentvisning och spel har lagts till i iOS-enheter <!-- 2827760-->
I **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel** läggs följande inställningar till: Tillåt hanterade appar att skriva kontakter till ohanterade kontaktkonton Tillåt ohanterade appar att läsa från hanterade kontaktkonton Om du vill se de här inställningarna går du till [iOS-enhetsbegränsningar](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Inställningar för nytt meddelande, tips och keyguard för Android Enterprise-enhetsägarenheter <!-- 3201839 3201843 -->
Den här uppdateringen innehåller flera nya funktioner på Android Enterprise-enheter vid körning som enhetsägare. Om du vill använda dessa funktioner, gå till **Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Android Enterprise** > i **Profiltyp**, välj **Endast enhetens ägare** > **Enhetsbegränsningar**.

Nya funktioner som ingår: 

- Inaktivera systemmeddelanden till att inte visas, inklusive inkommande anrop, systemaviseringar, systemfel med mera.
- Föreslår hoppa över start av självstudier och tips för appar som öppnas för första gången.
- Inaktivera avancerade keyguard-inställningar, till exempel kamera, meddelanden, upplåsning med fingeravtryck med mera.


Om du vill visa inställningarna går du till avsnittet om [begränsningsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android Enterprise-enhetsägarenheter kan använda VPN-anslutningar med Always On <!-- 3202194 -->
I den här uppdateringen kan du använda VPN-anslutningar som alltid är aktiva på Android Enterprise-enheter. Ständiga VPN-anslutningar förblir anslutna eller återansluter omedelbart när användaren låser upp sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. Du kan också placera anslutningen i ”låst” läge, vilket blockerar all nätverkstrafik tills VPN-anslutningen aktiveras.
Du kan aktivera VPN-anslutningar som alltid är aktiva i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar** för enhetsägare endast > **Anslutningar**. Om du vill visa inställningarna går du till avsnittet om [begränsningsinställningar för Android Enterprise-enheter](../configuration/device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Ny inställning för att avsluta processer i Aktivitetshanteraren på Windows 10-enheter <!-- 3285177 --> 
Den här uppdateringen innehåller en ny inställning för att avsluta processer med hjälp av Aktivitetshanteraren på Windows 10-enheter. Med hjälp av en profil för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Windows 10** > i **Profiltyp**, välj **Enhetsbegränsningar** > **Allmänna** inställningar), väljer du att tillåta eller förhindra den här inställningen.
Om du vill visa de här inställningarna går du till [Inställningar av begränsningar för Windows 10-enheter](../configuration/device-restrictions-windows-10.md).
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
- **Hälsotillstånd för Intune-tjänsten** – Visar information om aktiva incidenter eller avbrott i klientorganisationen. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office.
- **Nytt i Intune** – Visar aktiva meddelanden för klientorganisationen. Meddelanden omfattar till exempel aviseringar när klientorganisationen får de senaste funktionerna för Intune.  Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Ny hjälp- och supportupplevelse i företagsportalen för Windows 10 <!-- 1488939-->
Den nya sidan Hjälp och support i Företagsportal hjälper användare att felsöka och be om hjälp med problem med appen och åtkomst. Från den nya sidan kan de skicka fel- och diagnostiklogginformation via e-post och hitta information om organisationens supportavdelning. De hittar också avsnittet Vanliga frågor och svar med länkar till relevant Intune-dokumentation. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Ny hjälp- och supportupplevelse för Intune   <!-- #3307080 -->
Vi lanserar den nya hjälp- och supportupplevelsen för alla klientorganisationer under de närmaste dagarna. Den här nya upplevelsen är tillgänglig för Intune och kan nås när du använder Intune-bladen på [Azure-portalen](https://portal.azure.com/).
Med den nya upplevelsen kan du beskriva problemet med egna ord och ta emot felsökningsinsikter och webbaserat åtgärdsinnehåll. De här lösningarna är tillgängliga via en regelbaserad maskininlärningsalgoritm som drivs av användarfrågor. Utöver problemspecifika rekommendationer använder du det nya arbetsflödet för att öppna ett supportärende via e-post eller telefon. Den här nya upplevelsen ersätter den tidigare hjälp- och supportupplevelsen av en statisk uppsättning förvalda alternativ som är baserade på området i konsolen du befinner dig i när du öppnar Hjälp och support. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-apps----1081941---"></a>Omfattningstaggar för appar <!-- 1081941 -->
Du kan skapa omfångstaggar som begränsar åtkomsten för roller och appar. Du kan lägga till en omfångstagg för en app så att endast personer med roller som också tilldelats den omfångstaggen har åtkomst till appen. För närvarande kan appar som har lagts till i Intune från hanterad Google Play eller appar som har köpts med hjälp av Apples volymköpsprogram (VPP) inte tilldelas omfångstaggar (men framtida stöd för detta planeras). Mer information finns i [Använda omfångstaggar för att filtrera principer](scope-tags.md).

## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
