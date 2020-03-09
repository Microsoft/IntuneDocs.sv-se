---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e099537bce6327e9a8991bc42f406e4abd3dfd2e
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260239"
---
# <a name="in-development-for-microsoft-intune---march-2020"></a>Under utveckling för Microsoft Intune – mars 2020

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Förutom informationen på den här sidan: 

- Om vi tror att du behöver vidta åtgärder innan en ändring genomförs, publicerar vi ett extra inlägg i meddelandecentret för Office.
- När en funktion går in i produktion, oavsett om det är en förhandsversion eller en allmänt tillgänglig version, flyttas funktionsbeskrivningen från den här sidan till [Nyheter](whats-new.md).
- Den här sidan och sidan [Nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Information om planerade produktlanseringar och tidslinjer finns i [Microsoft 365-översikten](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS).

> [!NOTE]
> Den här informationen återspeglar våra planer gällande Intune-funktioner i kommande versioner. Datum och enskilda funktioner kan ändras. Den här sidan beskriver inte alla funktioner som utvecklas.

**RSS-feed**: Få reda på när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Apphantering

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Omdirigera webbklipp till Microsoft Edge på iOS/iPadOS-enheter<!-- 5455276 -->
Webbklipp, som fungerar som fästa webbappar på iOS/iPadOS-enheter, måste uppdateras. Nyligen distribuerade webbklipp öppnas i Microsoft Edge i stället för Intune Managed Browser om det behövs för att öppna i en skyddad webbläsare. Du måste omdirigera befintliga webbklipp för att se till att de öppnas i Microsoft Edge i stället för Managed Browser.

### <a name="macos-and-ios-company-portal-updates---5779439-5780234----"></a>Uppdateringar av företagsportalen för macOS och iOS<!-- 5779439, 5780234  -->
Profilfönstret i företagsportalen för macOS och iOS kommer att uppdateras så att det inkluderar utloggningsknappen. Uppdateringen innehåller dessutom förbättringar av användargränssnittet i profilfönstret i macOS-företagsportalen. Mer information om företagsportalen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](~/apps/company-portal-app.md).

### <a name="updates-to-branding-and-customization-pane---5236032---"></a>Uppdateringar av fönstret Anpassning<!-- 5236032 -->
Vi uppdaterar det Intune-fönster som för närvarande heter ”Anpassning” med förbättringar såsom följande:

- Byter namn på fönstret till **Anpassning**.
- Förbättrar organiseringen och utformningen av inställningar.
- Förbättrar text och knappbeskrivningar för inställningar.

Du hittar de här inställningarna i Intune genom att gå till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välja **Administration av klientorganisation** > **Anpassning**. Information om befintlig anpassning finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](~/apps/company-portal-app.md).

### <a name="configure-the-ios-microsoft-azure-ad-sso-app-extension---567534----"></a>Konfigurera Microsoft Azure AD-apptillägget för enkel inloggning för iOS<!-- 567534  -->
Microsoft Azure AD-teamet utvecklar en app för omdirigering med enkel inloggning som gör att användare med iOS eller iPadOS 13.0+ sömlöst kan få åtkomst till Microsofts appar och webbplatser med en enda inloggning. När AAD-apptillägget för enkel inloggning lanseras kommer du att kunna konfigurera tillägget för enkel inloggning med profilen för **Enhetsfunktioner** > **Apptillägg för enkel inloggning** i administratörskonsolen med några få klick. 

Mer information om iOS-apptillägg för enkel inloggning eller hur du konfigurerar enhetsfunktioner finns i [Apptillägg för enkel inloggning](~/configuration/device-features-configure.md#single-sign-on-app-extension).

### <a name="company-portal-for-ios-to-support-landscape-mode--6048329----"></a>Företagsportal för iOS för att stödja liggande läge<!--6048329  -->
Användare kommer att kunna registrera sina enheter, hitta appar och få IT-support med hjälp av valfri skärmorientering. Appen identifieras automatiskt och anpassar skärmen till stående eller liggande läge, såvida inte användaren låser skärmen i stående läge. 

### <a name="configure-if-enrollment-is-available-in-company-portal-for-android-and-ios---4260128-idready-idstaged---"></a>Konfigurera huruvida registrering är tillgänglig i Företagsportal för Android och iOS<!-- 4260128 idready idstaged -->
En ny inställning kommer att bli tillgänglig som gör att du kan konfigurera huruvida enhetsregistrering i Företagsportal på enheter med Android eller iOS är tillgänglig med prompter, tillgänglig utan prompter eller inte tillgänglig för användare. Du hittar de här inställningarna i Intune genom att gå till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välja **Administration av klientorganisation** > **Anpassning** > **Redigera** > **Enhetsregistrering**. Mer information om befintlig anpassning av Företagsportal finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](~/apps/company-portal-app.md).

### <a name="improved-sign-in-experience-in-company-portal-for-android---6103997----"></a>Förbättrad inloggningsupplevelse i Företagsportal för Android<!-- 6103997  -->
Vi uppdaterar layouten för flera inloggningsskärmar i företagsportalappen för Android så att upplevelsen blir modernare, enklare och tydligare för användare.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Enhetskonfigurationsprofiler för fast nätverk för macOS-enheter<!-- 3508686  -->
En ny konfigurationsprofil för macOS-enheter kommer att bli tillgänglig, som konfigurerar kabelanslutna nätverk (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattformen > **Kabelanslutet nätverk** för profiltypen). Använd den här funktionen för att skapa 802.1 x-profiler för att hantera kabelanslutna nätverk och distribuera dessa kabelanslutna nätverk till dina macOS-enheter.

Gäller för:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932----"></a>VPN-profiler med IKEv2 VPN-anslutningar kan använda Alltid på med iOS/iPadOS-enheter <!-- 1947932  -->
På iOS/iPadOS-enheter kan du skapa en VPN-profil som använder en IKEv2-anslutning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPadOS** för plattformen > **VPN** för profiltypen). I en framtida uppdatering kan du konfigurera Alltid på med IKEv2. När IKEv2 VPN-profiler har konfigurerats ansluter de automatiskt och förblir anslutna (eller återansluter snabbt) till VPN-anslutningen. Den förblir ansluten även när du flyttar mellan nätverk eller startar om enheter.

På iOS/iPadOS är Alltid på för VPN begränsat till IKEv2-profiler.

Om du vill se de aktuella IKEv2-inställningarna som du kan konfigurera går du till [Lägg till VPN-inställningar på iOS/iPadOS-enheter i Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Gäller för:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984----"></a>Förbättrat användargränssnitt när du skapar konfigurationsprofiler på iOS/iPadOS- och macOS-enheter<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984  -->
När du skapar en profil för iOS/iPadOS- eller macOS-enheter uppdateras funktionen i administrationscentret för slutpunktshantering. Den här ändringen påverkar följande enhetskonfigurationsprofiler (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** > **iOS** eller **macOS** för plattformen):

- Anpassad: iOS/iPadOS, macOS
- Enhetsfunktioner: iOS/iPadOS, macOS
- Enhetsbegränsningar: iOS/iPadOS, macOS
- Slutpunktsskydd: macOS
- Tillägg: macOS
- Inställningsfil: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-----"></a>Förbättrat användargränssnitt när du skapar OEMConfig-konfigurationsprofiler på Android Enterprise-enheter<!-- 5568645   -->
När du skapar eller redigerar en OEMConfig-profil för Android Enterprise-enheter uppdateras funktionen i administrationscentret för slutpunktshantering. Den uppdaterade funktionen ger en snabb översikt över inställningar som du har konfigurerat. Den här ändringen påverkar OEMConfig-profilen för enhetskonfigurationen (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** > **Android Enterprise** för plattformen > **OEMConfig** för profiltypen).

Den här funktionen gäller för:
- Android enterprise 

### <a name="enterprise-app-trust-settings-modification-setting-will-be-removed-from-iosipados-device-restriction-profiles---6225131----"></a>Inställningen Ändringar av inställningar för att lita på företagsappar kommer att tas bort från profiler för iOS-/iPadOS-enhetsbegränsningar<!-- 6225131  -->
På enheter med iOS/iPadOS skapar du en enhetsbegränsningsprofil (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** > **iOS/iPadOS** för plattform > **Enhetsbegränsningar** för profiltyp). Inställningen **Ändringar av inställningar för att lita på företagsappar** kommer att tas bort av Apple och tas bort från Intune. Om du för närvarande använder den här inställningen i en profil har den ingen påverkan och kommer att finnas kvar i din profil tills du skapar en ny profil. Den här inställningen kommer även att tas bort från all rapportering i Intune.

Gäller för:
- iOS/iPadOS

Om du vill se de inställningar som du kan begränsa går du till [Inställningar för iOS- och iPadOS-enheter för att tillåta eller begränsa funktioner](../configuration/device-restrictions-ios.md).

### <a name="device-configuration-profile-settings-and-values-will-be-updated-for-windows-platforms---4091122---"></a>Inställningar och värden för enhetskonfigurationsprofiler kommer att uppdateras för Windows-plattformar<!-- 4091122 -->
När du skapar enhetskonfigurationsprofiler för Windows-plattformar (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** > valfritt **Windows**-alternativ för plattform) kommer vissa inställningar och deras värden att skilja sig från molnlösningsleverantören och kan vara svåra att förstå. Inställningarnas namn och värden kommer att uppdateras så att de blir tydligare.

Gäller för:

- Enhetskonfigurationsprofiler för Windows 10 och senare
- Enhetskonfigurationsprofiler för Windows Holographic for Business
- Enhetskonfigurationsprofiler för Windows 8.1
- Enhetskonfigurationsprofiler för Windows Phone 8.1

### <a name="improved-user-interface-experience-when-creating-device-restrictions-profiles-on-android-and-android-enterprise-devices---5841361---"></a>Förbättrat användargränssnitt när vid skapande av enhetskonfigurationsprofiler på enheter med Android eller Android Enterprise<!-- 5841361 -->
När du skapar en profil för enheter med Android eller Android Enterprise kommer upplevelsen i administrationscentret för slutpunktshantering att vara uppdaterad. Den här ändringen påverkar följande enhetskonfigurationsprofiler (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** > **Android-enhetsadministratör** eller **Android Enterprise** för plattformen):

- Enhetsbegränsningar: Android-enhetsadministratör
- Enhetsbegränsningar: Android Enterprise-enhetsägare
- Enhetsbegränsningar: Android Enterprise-arbetsprofil

Mer information om enhetsbegränsningar som du kan konfigurera finns i [Android-enhetsadministratör](../configuration/device-restrictions-android.md) och [Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="delete-bundles-and-bundle-arrays-in-oemconfig-device-configuration-profiles-on-android-enterprise-devices---5550355----"></a>Ta bort paket och paketmatriser i OEMConfig-enhetskonfigurationsprofiler på Android Enterprise-enheter<!-- 5550355  -->
På Android Enterprise-enheter skapar och uppdaterar du OEMConfig-profiler. Användare kommer att kunna ta bort paket och paketmatriser med hjälp av **Configuration Designer** i Intune.

Mer information om OEMConfig-profiler finns i [Använda och hantera Android Enterprise-enheter med OEMConfig i Microsoft Intune](../configuration/android-oem-configuration-overview.md).

Den här funktionen gäller för:
- Android enterprise

### <a name="support-for-wpa-and-wpa2-in-ios-enterprise-wi-fi-profiles--6215273-----"></a>Stöd för WPA och WPA2 i iOS Enterprise Wi-Fi-profiler<!--6215273   -->
Vi lägger till fältet *Säkerhetstyp* i [Enterprise Wi-Fi-profil för iOS](../configuration/wi-fi-settings-ios.md) (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** och välj **iOS/iPadOS** för *Plattform* och sedan **Wi-Fi** för *Profil* ). Detta liknar de alternativ som finns tillgängliga för en grundläggande Wi-Fi-profil för iOS. Med den här ändringen kommer du att kunna skapa nya profiler som anger säkerhetstypen **WPA-Enterprise** eller **WPA/WPA2-Enterprise** och sedan ange ett val för *EAP-typ*.

### <a name="new-user-experience-for-certificate-email-vpn-and-wi-fi-profiles---5615208-----"></a>Ny användarupplevelse för certifikat, e-post, VPN och Wi-Fi-profiler<!-- 5615208   -->
Vi uppdaterar [användarupplevelsen](../configuration/device-profile-create.md) i administrationscentret för slutpunktshantering (**Enheter** > **Konfigurationsprofiler** > **Skapa profil**) för skapande och ändring av följande profiltyper. Den nya upplevelsen kommer att visa samma inställningar som tidigare men använder en guideliknande upplevelse som inte kräver lika mycket horisontell rullning. Du behöver inte ändra befintliga konfigurationer med den nya upplevelsen.
- Härledd autentiseringsuppgift
- E-post
- PKCS-certifikat
- PKCS-importerat certifikat
- SCEP-certifikat
- Betrott certifikat
- VPN
- Wi-Fi

(**Enheter** > **Konfigurationsprofiler** > **Skapa profil** och för *Profiltyp* väljer du sedan någon av de föregående profilerna.)

### <a name="configure-the-microsoft-defender-atp-app-for-macos-----5520115----"></a>Konfigurera Microsoft Defender ATP-appen för macOS  <!-- 5520115  -->
Du kommer snart att kunna konfigurera [inställningar](../protect/endpoint-protection-macos.md) för Microsoft Defender ATP-appen för enheter som kör macOS som en del av en enhetskonfigurationsprofilen för slutpunktsskydd (**Enheter** > **Konfigurationsprofiler** > **Skapa profil**, välj **macOS** för *Plattform* och sedan **Slutpunktsskydd** för *Profiltyp*). Det kommer att finnas åtta inställningar för macOS-enhetskonfiguration. 

Defender ATP stöds på macOS 10.13 (High Sierra) och senare, och [Microsoft Defender ATP](../apps/apps-advanced-threat-protection-macos.md)-appen måste distribueras till enheten *efter* att dessa inställningar tillämpas. Inställningarna ska skickas till enheten innan appen distribueras. Betaversioner av macOS stöds inte.

### <a name="new-filevault-setting-for-macos-endpoint-protection-device-configuration-policy---5459801-----"></a>Ny FileVault-inställning för macOS-enhetskonfigurationsprincip för slutpunktsskydd<!-- 5459801   -->
Vi lägger till en ny inställning i FileVault-kategorin i mallen [macOS-slutpunktsskydd](../protect/endpoint-protection-macos.md): Dölj återställningsnyckel. (**Enheter** > **Konfigurationsprofiler** > **Skapa profil**, välj **macOS** för *Plattform* och sedan **Slutpunktsskydd** för *Profiltyp*). Den här inställningen döljer den personliga nyckeln från slutanvändaren under FileVault 2-kryptering. Enhetsanvändare kan visa sin personliga återställningsnyckel när som helst från iOS-företagsportalappen eller från företagsportalens webbplats för den krypterade macOS-enheten. De kan visa den personliga återställningsnyckeln genom att gå till enhetsinformation och klicka på *hämta återställningsnyckel*.

Den här inställningen kommer inte att vara tillgänglig i tidigare skapade principer. Du behöver återskapa FileVault-principer för att konfigurera den här inställningen och använda den. 

###  <a name="ui-update-when-configuring-compliance-policy----3961639----"></a>Uppdatering av användargränssnittet vid konfiguration av efterlevnadsprinciper <!-- 3961639  -->
Vi uppdaterar gränssnittet för konfiguration av efterlevnadsprinciper i Microsoft Endpoint Manager (**Enheter** > **Efterlevnadsprinciper** > **Principer** > **Skapa princip**). Du kommer att se en ny användarupplevelse som har samma inställningar och information som du har använt tidigare. Den nya upplevelsen följer en guideliknande process för skapande av efterlevnadsprincip och innehåller den sida där du lägger till *Tilldelningar* för principen och sedan sidan *Sammanfattning*, där du kan granska konfigurationen innan du skapar principen. 

### <a name="configure-delivery-optimization-agent-when-downloading-win32-app-content---5410945----"></a>Konfigurera leveransoptimeringsagent vid nedladdning av Win32-appinnehåll<!-- 5410945  -->
Du kommer att kunna konfigurera leveransoptimeringsagenten att ladda ned Win32-appinnehåll antingen i bakgrunds- eller förgrundsläge baserat på tilldelning. För befintliga Win32-appar fortsätter innehållet att laddas ned i bakgrundsläge. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Konfigurationsprofiler** > **Skapa profil**. Välj **Windows 10 och senare** som **Plattform**. Under **Profiltyp** väljer du **Leveransoptimering**. Mer information om leveransoptimering finns i [Win32-apphantering – Leveransoptimering](~/apps/apps-win32-app-management.md#delivery-optimization).


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Enhetshantering

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Ändra primär användare för Windows-enheter <!-- 3794742 -->
Du kommer att kunna ändra den primära användaren för Windows-hybridanslutna och Azure AD-anslutna enheter. Om du vill göra det går du till **Intune** > - **Enheter** > **Alla enheter** > väljer en enhet > **Egenskaper** > **Primär användare**. 

### <a name="new-android-report-on-android-devices-overview-page---5435435---"></a>Ny Android-rapport på översiktssidan för Android-enheter<!-- 5435435 -->
Vi kommer att lägga till en rapport i Microsoft Endpoint Manager-administratörskonsolen på översiktssidan för Android-enheter. Där visas hur många Android-enheter som har registrerats i varje lösning för enhetshantering. Det här diagrammet (liksom samma diagram som redan finns i Azure-konsolen) visar antal arbetsprofilenheter samt fullständigt hanterade, dedikerade och enhetsadministratörsregistrerade enheter. Om du vill se rapporten väljer du **Enheter** > **Android** > **Översikt**.

### <a name="powershell-scripts-support-for-byod-devices---1862833----"></a>Stöd för PowerShell-skript för BYOD-enheter<!-- 1862833  -->
PowerShell-skript kommer att stödja Azure AD-registrerade enheter i Intune. Mer information om PowerShell finns i [Använda PowerShell-skript på Windows 10-enheter i Intune](~/apps/intune-management-extension.md). Den här funktionen stöder inte enheter som kör Windows 10 Home Edition.

### <a name="additional-data-warehouse-device-inventory-properties---6125732----"></a>Ytterligare egenskaper för Data Warehouse-enhetsinventering<!-- 6125732  -->
Ytterligare egenskaper för enhetsinventering kommer att bli tillgängliga via Intune Data Warehouse. Följande egenskaper kommer att göras tillgängliga via samlingen [enheter](~/developer/intune-data-warehouse-collections.md#devices):
- Lagringskapacitet 
- Minneskapacitet
- Office 365-version
- Enhetsmodell

Mer information om Data Warehouse finns i [Microsoft Intune Data Warehouse API](~/developer/reports-nav-intune-data-warehouse.md).

### <a name="guide-users-from-android-device-administrator-management-to-work-profile-management--5857738--"></a>Vägled användare från administratörshantering av Android-enheter till arbetsprofilhantering<!--5857738-->
Vi släpper en ny efterlevnadsinställning för administratörsplattformen för Android-enheter. Med den här inställningen kan du göra en enhet icke-kompatibel om den hanteras med enhetsadministratör.

På dessa icke-kompatibla enheter kommer användare att på sidan **Uppdatera enhetsinställningar** se meddelandet **Flytta till konfiguration av enhetshantering**. Om de trycker på knappen **Lös** vägleds de genom:

1. Avregistrering från enhetsadministratörshantering
2. Registrering i arbetsprofilhantering
3. Lösa efterlevnadsproblem 
 
Google minskar stödet för enhetsadministration i nya versioner av Android för att kunna övergå till en modern, mer omfattande och säkrare enhetshantering med Android Enterprise.  Intune kan endast erbjuda fullt stöd för enhetsadministratörshanterade Android-enheter som kör Android 10 och senare till och med andra kvartalet 2020. Enhetsadministratörshanterade enheter (förutom Samsung) som kör Android 10 eller senare efter denna tidpunkt kommer inte längre att kunna hanteras fullt ut. Det innebär exempelvis att berörda enheter inte får de nya lösenordskraven. Mer information finns i [det här meddelandet](#decreasing-support-for-android-device-administrator).

### <a name="retire-noncompliant-devices---1827291---"></a>Ta icke-kompatibla enheter ur bruk<!-- 1827291 -->
Vi lägger till en ny valfri efterlevnadsåtgärd för att dra tillbaka en icke-kompatibel enhet (**Enheter** > **Efterlevnadsprinciper** > **Principer** > **Skapa princip** och visa sedan tillgängliga *Åtgärder* på sidan *Åtgärder för inkompatibilitet*).  När en inkompatibel enhet tas bort tas alla företagsdata bort från enheten, och enheten hanteras inte längre i Intune. Den här åtgärden körs när det konfigurerade antalet dagar har uppnåtts. Minsta värde är 30 dagar.  Explicit IT-administratörsgodkännande kommer att krävas för att dra tillbaka enheterna med hjälp av avsnittet *Dra tillbaka icke-kompatibla enheter*, där administratörer kan dra tillbaka alla berättigade enheter.

### <a name="new-information-in-device-details---5604099---"></a>Ny enhetsinformation<!-- 5604099 -->
Följande information kommer att finnas på sidan **Översikt** för enheter:
- Lagringskapacitet (mängden fysisk lagring på enheten)
- Minneskapacitet (mängden fysiskt minne på enheten)

### <a name="script-support-for-macos-devices---4280361----"></a>Skriptstöd för macOS-enheter<!-- 4280361  -->
Du kommer att kunna lägga till och distribuera skript till macOS-enheter. Det här stödet utökar din möjlighet att konfigurera macOS-enheter utöver vad som är möjligt med hjälp av interna MDM-funktioner på macOS-enheter. 

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
## <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

### <a name="help-and-support-workflow-update-to-support-additional-services---5654170---"></a>Uppdatering av arbetsflöde för hjälp och support för att stödja ytterligare tjänster<!-- 5654170 -->
Vi uppdaterar sidan Hjälp och support i administrationscentret för Microsoft Endpoint Manager så att du kan välja den hanteringstyp du använder för att bättre tillhandahålla specifik support (**Felsökning + support** >  **Hjälp och support**). Med den här ändringen kommer du att kunna välja bland följande hanteringstyper:
- Configuration Manager (inkluderar Desktop Analytics)
- Intune
- Samhantering

<!-- ***********************************************-->
<!--
## Role-based access control
-->

<!-- ***********************************************-->
## <a name="security"></a>Säkerhet

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Stöd för härledda autentiseringsuppgifter på Android COBO-enheter<!--4839592-->
Du kommer att kunna använda härledda autentiseringsuppgifter på fullständigt hanterade Android Enterprise-enheter. Support kommer att inkluderas för att hämta en härledd autentiseringsuppgift för Entrust Datacard, Intercede och DISA Purebred. Du kan använda en härledd autentiseringsuppgift för appautentisering, Wi-Fi, VPN eller S/MIME-signering och/eller kryptering med appar som stöder det.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Använda antivirusprincipen för att hantera inställningar för Microsoft Defender Antivirus och Windows-säkerhetsupplevelsen<!--6131401 -->
Från noden *Slutpunktsskydd* kommer du att kunna konfigurera inställningar för **Antivirus**. När du konfigurerar en princip för Antivirus kommer du att definiera inställningar för dina Windows 10-enheter via två profiltyper:

- Microsoft Defender Antivirus: Hantera inställningar för molnskydd, antivirusundantag, reparation, genomsökningsalternativ och mycket annat.
- Windows-säkerhetsfunktion: Hantera hur användare upplever Windows säkerhetsinställningar på sina enheter. Du kommer att kunna konfigurera vad slutanvändare kan visa i Microsoft Defender Security Center och vilka meddelanden de får.

### <a name="users-personal-encrypted-recovery-key---6273943---"></a>Användarens personliga krypterade återställningsnyckel<!-- 6273943 -->
En ny Intune-funktion kommer att bli tillgänglig som gör att användare kan hämta sin personliga krypterade **FileVault**-återställningsnyckel för Mac-enheter via Android-företagsportalappen eller via Android Intune-programmet. Det kommer att finnas en länk i både företagsportalappen och Intune-programmet som öppnar en Chrome-webbläsare till webbföretagsportalen, där användaren kan se den **FileVault**-återställningsnyckel som krävs för åtkomst till Mac-enheterna. Mer information om kryptering finns i [Använda enhetskryptering med Intune](~/protect/encrypt-devices.md).

### <a name="privacy-preferences-settings-for-macos-devices---2934232---"></a>Sekretessinställningar för macOS-enheter<!-- 2934232 --> 
Med lanseringen av macOS Catalina 10.15 har Apple lagt till nya förbättringar av säkerhet och sekretess. Som standard kan program och processer inte komma åt specifika data utan användarmedgivande. Om användarna inte ger medgivande kan det hända att programmen och processerna inte fungerar. Intune lägger till stöd för inställningar som gör att IT-administratörer kan tillåta eller neka medgivande för dataåtkomst åt slutanvändare på enheter som kör macOS 10.14 och senare. De här inställningarna ser till att program och processer fortsätter att fungera korrekt och minskar det antal meddelanden som slutanvändarna får. 

### <a name="updated-ui-text-and-labels-for-windows-10-endpoint-protection-profile-settings---5983747---"></a>Uppdatering av text och etiketter för användargränssnittet i inställningarna för Windows 10-slutpunktsskyddsprofil<!-- 5983747 -->
Vi uppdaterar texten för olika inställningar som du konfigurerar som Windows 10-enhetskonfigurationsprofiler så att det blir enklare att förstå avsedd användning och avsett syfte med inställningarna. 

De inställningar som vi uppdaterar inkluderar Windows 10-enhetskonfigurationsprofiler för: 
- [Enhetsbegränsningar](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) > Microsoft Defender Antivirus  
- [Endpoint Protection](../protect/endpoint-protection-windows-10.md) > Microsoft Defender Antivirus

De inställningar som stöds med Intune ändras inte. Detta är endast en uppdatering av texten i användargränssnittet i administrationscentret för Microsoft-slutpunktshantering. 


<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).



