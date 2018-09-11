---
title: Nyheter i Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Ta reda på vad som är nytt i Intune Azure-portalen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 0205715a8e35d009401886af4bd0bf88fb9cf662
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347295"
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Läs mer om varje veckas nyheter i Microsoft Intune. Du kan också läsa mer om [kommande ändringar](#whats-coming), [viktiga meddelanden](#notices) om tjänsten och information om [tidigare versioner](whats-new-archive.md). Vissa funktioner kan distribueras över flera veckor och kanske inte är tillgängliga för alla kunder den första veckan.

> [!Note]
> På [hybridsidan med senaste nytt](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) finns mer information om nya funktioner för hybridhantering av mobilenheter (MDM).


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

## <a name="week-of-august-27-2018"></a>Veckan 27 augusti 2018

### <a name="app-management"></a>Apphantering

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Stöd för pakettunnel för per app-VPN-profiler i iOS för anpassade anslutningstyper och Pulse Secure-anslutningstyper <!-- 1520957 -->
När du använder per app-VPN-profiler i iOS kan du välja att använda händelsedirigering nedåt på appnivå (app-proxy) eller på paketnivå (paket-tunnel). Dessa alternativ är tillgängliga med följande anslutningstyper:
- Anpassat VPN
- Pulse Secure om du inte är säker på vilket värde du ska använda läser du VPN-leverantörens dokumentation.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Fördröjning när iOS-programuppdateringar visas på enheten <!-- 1949583 -->
I Intune > **Programuppdateringar** > **Uppdateringsprinciper för iOS** kan du konfigurera dagar och tider då du inte vill att enheter installerar uppdateringar. I en kommande uppdatering kommer du kunna fördröja tidpunkten då en programuppdatering visas på enheten från 1–90 dagar. 
[Konfigurera uppdateringsprinciper för iOS i Microsoft Intune](software-updates-ios.md) visar en lista över aktuella inställningar.

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 ProPlus version <!-- 2213968 -->
När du tilldelar Office 365 ProPlus-appar till Windows 10-enheter med Intune kommer du att kunna välja version av Office. I Azure-portalen väljer du **Microsoft Intune** > **Appar** > **Lägg till app**. Välj sedan **Office 365 ProPlus-paket (Windows 10)** från listrutan **Typ**. Välj **Inställningar för appsvit** för att visa det associerade bladet. Ange **Uppdateringskanalen** till ett värde såsom **Varje månad**. Du kan även ta bort andra versioner av Office (msi) från slutanvändarenheter genom att välja **Ja**. Välj **Specifik** för att installera en specifik version av Office för den valda kanalen på slutanvändarenheter. Nu kan du välja den **specifika version** av Office som ska användas. De versioner som är tillgängliga ändras över tid. När du skapar en ny distribution kan de versioner som är tillgängliga därför vara nyare och inte ha vissa äldre versioner tillgängliga. Befintliga distributioner fortsätter att distribuera den äldre versionen, men versionslistan uppdateras kontinuerligt per kanal. Mer information finns i [Översikt över uppdateringskanaler för Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Stöd för inställningen Registrera DNS för Windows 10-VPN <!-- 2282852 -->
Med den här uppdateringen kan du konfigurera Windows 10-VPN-profiler så att de dynamiskt registrerar de IP-adresser som tilldelas till VPN-gränssnittet med intern DNS, utan behov av anpassade profiler.
Information om de aktuella VPN-profilinställningar som är tillgängliga finns i [Windows 10-VPN-inställningar](vpn-settings-windows-10.md). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>Installationsprogrammet för macOS-företagsportalen innehåller nu versionsnumret i filnamnet för installationsprogrammet <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759-wnready---"></a>Automatiska appuppdateringar i iOS <!-- 2729759 wnready -->
Automatiska appuppdateringar fungerar för både enhets- och användarlicensierade appar för iOS version 11.0 och senare.




### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello riktar in sig på användare och enheter <!-- 1106609 -->
När du skapar en [Windows Hello för företag](windows-hello.md)-princip gäller den för alla användare i organisationen (i hela klientorganisationen). Med den här uppdateringen kan principen även tillämpas på specifika användare eller specifika enheter med hjälp av en princip för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Identity Protection (Identitetsskydd)** > **Windows Hello för företag**).
I Intune i Azure-portalen finns konfiguration och inställningar för Windows Hello nu i både **Enhetsregistrering** och **Enhetskonfiguration**. **Enhetsregistrering** riktar sig till hela organisationen (i hela klientorganisationen) och har stöd för Windows AutoPilot (OOBE). **Enhetskonfiguration** riktar sig mot enheter och användare som använder en princip som tillämpas under incheckning.
Den här funktionen gäller för:  
- Windows 10 och senare
- Windows 10 Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler är en tillgänglig anslutning för VPN-profiler i iOS <!-- 1769858 eeready -->
När du skapar en VPN-profil för enhetskonfiguration i iOS (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS**-plattform > **VPN**-profiltyp) finns det flera anslutningstyper, inklusive Cisco, Citrix och mer. Den här uppdateringen lägger till Zscaler som anslutningstyp. 
[VPN-inställningar för enheter som kör iOS](vpn-settings-ios.md) visar en lista över tillgängliga anslutningstyper.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077-eeready---"></a>FIPS-läge för företagets Wi-Fi-profiler för Windows 10 <!-- 1879077 eeready -->
Du kan nu aktivera FIPS-läge (Federal Information Processing Standards) för företagets Wi-Fi-profiler för Windows 10 i Intune Azure-portalen. Se till att FIPS-läge är aktiverat i Wi-Fi-infrastrukturen om du aktiverar det i Wi-Fi-profilerna.
[Wi-Fi-inställningar för Windows 10 och senare enheter i Intune](wi-fi-settings-windows.md) visar hur du skapar en Wi-Fi-profil.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Kontrollera S-läge på Windows 10-enheter och senare enheter – förhandsversion <!-- 1958649 -->
Med den här funktionsuppdateringen kan du skapa en profil för enhetskonfiguration som växlar en Windows 10-enhet ut ur S-läge, eller förhindra att användare växlar enheten ut ur S-läge. Den här funktionen finns i Intune > **Enhetskonfiguration** > **Profiler** >  **Windows 10 och senare** > **Edition upgrade and mode switch** (Versionsuppgradering och lägesväxling).
[Introduktion till Windows 10 i S-läge](https://www.microsoft.com/windows/s-mode) innehåller mer information om S-läge.
Gäller för: Windows 10 och senare (1809 och senare)

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Konfigurationspaketet för Windows Defender ATP läggs automatiskt till i konfigurationsprofilen <!-- 2144658 -->
När du använder enheter med [Advanced Threat Protection och registrering](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) i Intune behövde du tidigare ladda ned ett konfigurationspaket och lägga till det i din konfigurationsprofil. Med den här uppdateringen hämtar Intune paketet automatiskt från Windows Defender Säkerhetscenter och lägger till det i din profil.
Gäller för Windows 10 och senare.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Kräv att användare ansluter under enhetskonfiguration <!--2311457-->
Du kan nu ange enhetsprofiler som kräver att enheten ansluter till ett nätverk innan den går vidare förbi sidan Nätverk under Windows 10-installationen. När den här funktionen är i förhandsversion krävs Windows Insider-version 1809 eller senare för att använda den här inställningen.

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Begränsa appar och blockera åtkomst till företagsresurser på iOS- och Android Enterprise-enheter <!-- 2451462 -->
I **Enhetsefterlevnad** > **Principer** > **Skapa princip** > **iOS** > **Systemsäkerhet** finns det en ny inställning för **Begränsade program**. Den här nya inställningen använder en policy för efterlevnad för att blockera åtkomst till företagsresurser om vissa appar är installerade på enheten. Enheten betraktas som icke-kompatibel tills de begränsade apparna tas bort från enheten.
Gäller för: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Uppdateringar med stöd för modernt VPN för iOS <!-- 2459928, 1819876, and 2650856 -->
Den här uppdateringen har stöd för följande VPN-klienter för iOS: 
- F5 Access (version 3.0.1 och senare)
- Citrix SSO
- Palo Alto Networks GlobalProtect version 5.0 och senare även i den här uppdateringen:
- Den befintliga anslutningstypen **F5 Access** byter namn till **F5 Access Legacy** för iOS.
- Den befintliga anslutningstypen **Palo Alto Networks GlobalProtect** byter namn till **Legacy Palo Alto Networks GlobalProtect** för iOS.
Befintliga profiler med de här anslutningstyperna fortsätter att fungera med sina respektive äldre VPN-klienter. Om du använder Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN eller Palo Alto Networks GlobalProtect version 4.1 och tidigare med iOS bör du gå över till de nya apparna. Gör det så snart som möjligt för att säkerställa att VPN-åtkomst är tillgänglig för iOS-enheter när de uppdaterar till iOS 12.
Mer information om iOS 12 och VPN-profiler finns i [Microsoft Intune-supportteamets blogg](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Exportera efterlevnadsprinciper för den klassiska Azure-portalen för att återskapa dessa principer i Intune Azure-portalen <!-- 2469637 -->
Principer för enhetsefterlevnad som skapats i den klassiska Azure-portalen upphör att gälla. Du kan granska och ta bort alla befintliga principer, men du kan inte uppdatera dem. Om du behöver migrera några efterlevnadsprinciper till den befintliga Intune Azure-portalen kan du exportera principerna som en kommaavgränsad fil (*.csv*-fil). Använd sedan informationen i filen för att återskapa dessa principer i Intune Azure-portalen.

> [!IMPORTANT]
> När den klassiska Azure-portalen upphör kommer du inte längre att kunna komma åt eller visa dina efterlevnadsprinciper. Tänk därför på att exportera dina principer och återskapa dem i Azure-portalen innan den klassiska Azure-portalen upphör.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile – ny partner för skydd mot mobilhot <!-- 22662717 -->
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Better Mobile, en lösning med skydd mot mobilhot som är integrerad i Microsoft Intune.

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Lås företagsportalen i enkelt appläge tills användaren loggar in <!--1067692 --> 
Du kan nu välja att köra företagsportalen i enkelt appläge om du autentiserar en användare via företagsportalen i stället för installationsassistenten vid DEP-registrering. Det här alternativet låser enheten omedelbart efter att installationsassistenten är klar så att en användare måste logga in för att komma åt enheten. Den här processen ser till att enheten slutför registrering inte frånkopplas i ett tillstånd utan någon kopplad användare.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Tilldela en användare och ett eget namn till en Autopilot-enhet <!--1346521 -->
Du kan nu [tilldela en användare till en specifik Autopilot-enhet](enrollment-autopilot.md). Administratörer kommer även att kunna ge egna namn som möter användaren vid konfiguration av enheten med Autopilot.
Gäller för: Windows Insider 1809 eller senare versioner (medan den är i förhandsversion).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Använda VPP enhetslicenser för att företablera företagsportalen vid DEP-registrering <!-- 1608345 -->
Nu kan du använda VPP-enhetslicenser (volyminköpsprogram) till att företablera företagsportalen under registreringar med Programmet för enhetsregistrering (DEP). Detta gör du genom att ange den VPP-token du vill använda för att installera företagsportalen när du [skapar eller redigerar en registreringsprofil](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Se till att din token inte upphör att gälla och att du har tillräckligt många licenser för företagsportalappen. Om token upphör att gälla eller om licenserna tar slut kan Intune push-överföra företagsportalen från App Store istället (då krävs ett Apple-ID).

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Blockera personliga enhetsregistreringar i Windows <!-- 1849498 -->
Du kan [blockera personliga Windows-enheter](enrollment-restrictions-set.md#set-device-type-restrictions) från att registrera med [hantering av mobilenheter](windows-enroll.md) i Intune. Enheter som registreras med [Intune PC-agenten](manage-windows-pcs-with-microsoft-intune.md) kan inte blockeras med den här funktionen.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Ange mönster för datornamn i en Autopilot-profil <!--1849855-->
Du kan [ange en mall för datornamn](enrollment-autopilot.md#create-an-autopilot-deployment-profile) för att generera och ange [datornamnet](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) under Autopilot-registreringen.

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>För Windows Autopilot-profiler döljer du alternativen för att ändra konto på företagets inloggningssida och sidan för domänfel <!--1901669 -->
Det finns [nya Windows Autopilot-profilalternativ](enrollment-autopilot.md#create-an-autopilot-deployment-profile) som administratörer kan använda för att dölja ändra alternativ för att ändra konto på företagets inloggningssida och sidorna för domänfel. För att dölja de här alternativen krävs att företagsanpassning konfigureras i Azure Active Directory. Gäller för: Windows Insider 1809 eller senare versioner (medan den är i förhandsversion).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Använda VPP enhetslicenser för att företablera företagsportalen vid DEP-registrering <!-- 1608345 -->
Nu kan du använda VPP-enhetslicenser (volyminköpsprogram) till att företablera företagsportalen under registreringar med Programmet för enhetsregistrering (DEP). Detta gör du genom att ange den VPP-token du vill använda för att installera företagsportalen när du [skapar eller redigerar en registreringsprofil](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Se till att din token inte upphör att gälla och att du har tillräckligt många licenser för företagsportalappen. Om token upphör att gälla eller om licenserna tar slut kan Intune push-överföra företagsportalen från App Store istället (då krävs ett Apple-ID).

### <a name="device-management"></a>Enhetshantering

#### <a name="delete-jamf-devices----2653306--"></a>Ta bort Jamf-enheter <!-- 2653306-->
Du kan ta bort JAMF-hanterade enheter genom att gå till **Enheter** > välj Jamf-enheten > **Ta bort**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Ändra terminologin till ”dra tillbaka” och ”rensa” <!-- 2175759 -->
För att överensstämma med Graph API har följande termer för Intune-användargränssnittet och dokumentationen ändrats:
- **Ta bort företagsinformation** ändras till ”Dra tillbaka”
- **Fabriksåterställning** ändras till **Rensa**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Bekräftelsedialogruta om administratören försöker ta bort MDM-pushcertifikat <!-- 297909500-->
Om någon försöker ta bort ett Apple MDM-pushcertifikat visar en bekräftelsedialogruta antalet relaterade iOS- och macOS-enheter. Dessa enheter måste registreras igen om certifikatet tas bort.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Ytterligare säkerhetsinställningar för Windows Installer <!-- 2282430 -->
Du kan tillåta användarna att styra appinstallationer. Om den här inställningen är aktiverad tillåts installationer som i annat fall skulle stoppats på grund av en säkerhetsöverträdelse. Du kan ange att Windows Installer ska använda förhöjd behörighet när program installeras i ett system. Du kan också ange att WIP-objekt (Windows Information Protection) ska indexeras och att deras metadata ska lagras på en okrypterad plats. När principen är inaktiverad indexeras inte Windows informationsskyddade objekt och resultaten visas inte i Cortana eller Utforskaren. Funktionerna för dessa alternativ är inaktiverade som standard. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Ny uppdatering av användarupplevelse för företagsportalens webbsida <!--2000968 -->
Vi har lagt till nya funktioner på företagsportalen baserat på våra kunders synpunkter. Du kommer att se tydliga förbättringar av befintliga funktioner och användbarheten för dina enheter. Delar av webbplatsen, som enhetsinformation, feedback och support samt enhetsöversikten, har fått en ny och modern design. Andra nyheter:

- Effektiva arbetsflöden mellan olika plattformar
- Bättre flöden för identifiering och registrering av enheter
- Fler användbara felmeddelanden
- Mer användarvänligt språk, mindre teknisk jargong
- Möjlighet att dela direktlänkar till appar
- Förbättrad prestanda för stora app-kataloger
- Bättre tillgänglighet för alla användare  

[Dokumentationen till Intune-företagsportalens webbplats](https://docs.microsoft.com/en-us/intune-user-help/using-the-intune-company-portal-website) har uppdaterats för att återspegla dessa ändringar. Om du vill se ett exempel på appförbättringarna kan du se [Uppdateringar i användargränssnittet för Intunes slutanvändarappar](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Förbättrad upplåsningsidentifiering i efterlevnadsrapportering<!-- 2198738 -->
Inställningsstatus för förbättrad upplåsningsidentifiering visas nu i all efterlevnadsrapportering i administrationskonsolen.

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-policies---1081974-eeready--"></a>Omfångstaggar för principer <!--1081974 eeready-->
Du kan [skapa omfångstaggar](scope-tags.md) som begränsar åtkomsten till Intune-resurser. Lägg till en omfångstagg till en rolltilldelning och lägg sedan till omfångstaggen i en konfigurationsprofil. Rollen får endast åtkomst till resurser med konfigurationsprofiler som har matchande omfångstaggar (eller inga omfångstaggar).

## <a name="week-of-august-14-2018"></a>Veckan 14 augusti 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS-stöd för Apples program för enhetsregistrering (Device Enrollment Program) <!-- 747651 -->
Intune har nu stöd för registrering av macOS-enheter i Apples program för enhetsregistrering (DEP). Mer information finns i [Registrera macOS-enheter automatiskt med Apples program för enhetsregistrering](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Veckan som inleds den 23 juli 2018

### <a name="app-management"></a>Apphantering

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Stöd för verksamhetsspecifika appar (LOB) för macOS <!-- 1895847 -->
I Microsoft Intune kan verksamhetsspecifika macOS-appar distribueras med inställningen **Obligatorisk** eller **Tillgänglig med registrering**. Slutanvändarna kan hämta appar som har distribuerats som **tillgängliga** via företagsportalen för macOS eller [företagsportalwebbplatsen](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Stöd för inbyggda iOS-appar i helskärmsläge <!-- 2051098 -->
Utöver Store-appar och hanterade appar kan du nu välja en inbyggd App (till exempel Safari) som körs i helskärmsläge på en iOS-enhet.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Redigera dina distributioner av Office 365 Pro Plus-appar <!-- 2150145 -->
Som Microsoft Intune-administratör har du större möjlighet att redigera distributioner av Office 365 Pro Plus-appar. Dessutom behöver du inte längre ta bort dina distributioner för att ändra svitens egenskaper. I Azure Portal väljer du **Microsoft Intune** > **Klientappar** > **Appar**. Välj Office 365 Pro Plus Suite i listan med appar.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>Uppdaterad Intune App SDK för Android är nu tillgänglig <!-- 2744271-->

En uppdaterad version av Intune App SDK för Android är tillgänglig som stöd för Android P-versionen. Om du är en apputvecklare och använder Intune SDK för Android, måste du installera den uppdaterade versionen av Intune App SDK för att säkerställa att Intune-funktionerna i dina Android-appar fortsätter att fungera som förväntat på Android P-enheter. Den här versionen av Intune App SDK innehåller ett inbyggt plugin-program som utför SDK-uppdateringarna. Du behöver inte skriva om någon befintlig kod som ingår. Mer information finns i [Intune SDK för Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Om du använder den gamla badging-stilen för Intune, rekommenderar vi att du använder portföljikonen. Mer information relaterad till olika varumärken finns i [den här GitHub-lagringsplatsen](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Använda S/MIME för att kryptera och signera en användares enheter <!-- 1333642 -->
Den här uppdateringen innehåller S/MIME-e-postkryptering som använder en ny importerad certifikatprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj plattformen > profiltypen **PKCS-importerat certifikat**). Du kan importera certifikat i PFX-format i Intune. Intune kan sedan leverera samma certifikat till flera enheter som registrerats av en enda användare. Detta omfattar även följande:

- Den interna e-postprofilen för iOS har stöd för att aktivera S/MIME-kryptering med importerade certifikat i PFX-format.
- Den interna e-postappen på Windows Phone 10-enheter använder S/MIME-certifikatet automatiskt.
- Det privata certifikatet kan levereras över flera plattformar. Men alla e-postappar har inte stöd för S/MIME.
- På andra plattformar kan du behöva konfigurera e-postappen manuellt för att aktivera S/MIME.  
- E-postappar som har stöd för S/MIME-kryptering kan hantera hämtning av certifikat för S/MIME-kryptering av e-post på ett sätt som MDM inte stöder, till exempel genom att läsa från utgivarens certifikatarkiv.

Stöds på: Windows, Windows Phone 10, macOS, iOS och Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Skapa en princip för enhetskompatibilitet med hjälp av brandväggsinställningar på macOS-enheter <!-- 1497640 -->
När du skapar en ny efterlevnadsprincip i macOS (**Enhetsefterlevnad** > **Principer** > **skapa princip** > **Plattform: macOS** > **Systemsäkerhet**) finns det några nya **brandväggsinställningar** tillgängliga: 

- **Brandvägg**: konfigurera hur inkommande anslutningar ska hanteras i din miljö.
- **Inkommande anslutningar**: **Blockera** alla inkommande anslutningar utom de som behövs för grundläggande internettjänster, som DHCP, Bonjour och IPSec. Den här inställningen blockerar också alla delningstjänster.
- **Stealthläge**: **Aktivera** stealthläget om du vill förhindra att enheten svarar på avsökningsförfrågningar. Enheten fortsätter att besvara inkommande begäranden för godkända appar.

Gäller: macOS 10.12 och senare

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Ny enhetskonfigurationsprofil för Wi-Fi för Windows 10 och senare <!-- 1879077 -->
För närvarande kan du importera och exportera Wi-Fi-profiler med hjälp av XML-filer. Med den här uppdateringen kan du skapa en enhetskonfigurationsprofil för Wi-Fi direkt i Intune, precis som på vissa andra plattformar.

Om du vill skapa profilen öppnar du **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** > **Wi-Fi**. 

Gäller för Windows 10 och senare.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998-eeready---"></a>Helskärmsläge – inaktuell är nedtonad och kan inte ändras <!-- 2149998 eeready -->
Funktionen [Helskärmsläge](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10 och senare** > **Enhetsbegränsningar**) är inaktuell och ersätts med [Inställningar för helskärmsläge för Windows 10 och senare](kiosk-settings.md). Med den här uppdateringen är funktionen **Helskärmsläge – inaktuell** nedtonad och användargränssnittet kan inte ändras eller uppdateras. 

Om du vill aktivera helskärmsläge kan du läsa mer i [Inställningar för helskärmsläge för Windows 10 och senare](kiosk-settings.md).

Gäller för Windows 10 och senare, Windows 10 Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API:erna använder tredjeparts certifikatutfärdare <!-- 2184013 -->
I den här uppdateringen finns det ett Java-API som gör det möjligt för tredjeparts certifikatutfärdare att integrera med Intune och SCEP. Sedan kan användarna lägga till SCEP-certifikatet till en profil och tillämpa det på enheter med hjälp av MDM.

Intune stöder för närvarande [SCEP-förfrågningar med hjälp av Active Directory Certificate Services](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Växla för att visa eller dölja knappen Avsluta session i en webbläsare i helskärmsläge <!-- 2455253 -->
Du kan nu konfigurera om webbläsare i helskärmsläge ska visa knappen Avsluta session. Du kan se kontrollen under **Enhetskonfiguration** > **Helskärmsläge (förhandsgranskning)** > **Webbläsare i helskärmsläge**. När en användare klickar på knappen när den är aktiverad frågar appen om du verkligen vill avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata och går tillbaka till den webbadress som är standard.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Skapa en konfigurationsprofil för eSIM-mobilnät <!-- 2564077 -->
I **Enhetskonfiguration** kan du skapa en profil för eSIM-mobilnät. Du kan importera en fil som innehåller aktiveringskoder för mobilnät som tillhandahålls av din mobiloperatör. Du kan sedan distribuera de här profilerna till dina Windows 10-enheter som aktiverat eSIM LTE, till exempel Surface Pro LTE och andra eSIM-kompatibla enheter.

Kontrollera om dina [enheter stöder eSIM-profiler](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Gäller för Windows 10 och senare. 




### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Markera automatiskt Android-enheter som registrerats med hjälp av Samsung Knox Mobile-registrering som ”företagsägda”. <!-- 2404851 -->
Som standard markeras Android-enheter som registrerats med Samsung Knox Mobile-registrering nu som **företagsägda** under **Ägarskap för enhet**. Du behöver inte identifiera företagets enheter manuellt med hjälp av IMEI- eller serienummer innan du registrerar med Samsung Knox Mobile-registrering.

### <a name="device-management"></a>Enhetshantering

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Massborttagning av enheter på enhetsbladet <!-- 1793693 -->

Du kan nu ta bort flera enheter samtidigt på enhetsbladet. Välj **Enheter** > **Alla enheter** > välj de enheter som du vill ta bort > **Ta bort**. En avisering visas för enheter som inte kan tas bort.

## <a name="week-of-july-16-2018"></a>Veckan som inleds den 16 juli 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Fler möjligheter att synkronisera i företagsportalappen för Windows  
Med företagsportalappen för Windows kan du nu initiera en synkronisering direkt från Windows-aktivitetsfältet och Start-menyn. Den här funktionen är särskilt användbart om din enda uppgift är att synkronisera enheter och få åtkomst till företagsresurser. För att komma åt den nya funktionen högerklickar du på ikonen för företagsportalen som har fästs till verktygsfältet eller Start-menyn. I menyalternativen (kallas även en snabblista) väljer du **Sync this device** (Synkronisera den här enheten). Företagsportalen öppnas till sidan **inställningar** och initierar synkroniseringen. En titt på de nya funktionerna finns på sidan om [nyheter i användargränssnittet](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nya bläddringsfunktioner i företagsportalappen för Windows  

När du bläddrar eller söker efter appar i företagsportalappen för Windows kan du nu växla mellan den befintliga vyn **Paneler** och den nyligen tillagda vyn **Information**. Den nya vyn visar information om programmet, som namn, utgivare, publiceringsdatum och installationsstatus.  

På sidan **Appar** kan du använda vyn **Installerade** för att se information om slutförda och pågående appinstallationer. Du kan se hur den nya vyn ser ut på sidan om [nyheter i användargränssnittet](whats-new-app-ui.md).  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Förbättrade funktioner i företagsportalappen för enhetsregistreringshanterare  
När en enhetsregistreringshanterare (DEM) loggar in på företagsportalappen för Windows visar appen nu endast DEM:ens aktuella enhet som körs. Den här förbättringen minskar uppnådda tidsgränser som tidigare förekom när appen försökte visa alla DEM-registrerade enheter.  


## <a name="week-of-july-9-2018"></a>Veckan som inleds med den 9 juli 2018

### <a name="app-management"></a>Apphantering

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Blockera åtkomst till appen baserat på icke-godkända enhetsleverantörer och modeller  <!-- 1425689 ! -->
Intune IT-administratören kan tillämpa en angiven lista över Android-tillverkare och/eller iOS-modeller via Intune App Protection-principer. IT-administratören kan ange en semikolonavgränsad lista över tillverkare för Android-principer och enhetsmodeller för iOS-principer. Intune App Protection-principer gäller endast för Android och iOS. Det finns två separata åtgärder som kan utföras på den angivna listan:
- En blockering från åtkomst till appen på enheter som inte har angetts.
- Eller en selektiv rensning av företagets data på enheter som inte har angetts. 

Användaren kommer inte att få åtkomst till det aktuella programmet om principkraven inte uppfylls. Baserat på inställningarna kan användaren bli blockerad eller rensas selektivt på sina företagsdata i appen. På iOS-enheter kräver den här funktionen att program deltar (t.ex. WXP, Outlook, Managed Browser, Yammer) för att integrera Intune APP SDK:n för att funktionen ska framtvingas i berörda program. Den här integreringen händer på löpande bas, och är beroende av specifika programteam. På Android kräver funktionen den senaste företagsportalen. 

På slutanvändarens enheter utför Intune-klienten åtgärder baserat på en enkel matchning av strängar som angetts i Intune-bladet för programskyddsprinciper. Detta beror helt på värdet som enheten rapporterar. IT-administratören rekommenderas därför att säkerställa att det avsedda funktionssättet är korrekt. Detta kan åstadkommas genom att testa den här inställningen baserat på en rad olika enhetstillverkare och modeller som är riktade till en liten användargrupp. I Microsoft Intune väljer du **Klientappar** > **Appskyddsprinciper** för att visa och lägga till appskyddsprinciper. Mer information om att appskyddsprinciper finns i [Vad är appskyddsprinciper](app-protection-policy.md) och [Selektiv rensning av data med åtkomståtgärder för appskyddsprinciper i Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Åtkomst till förhandsversionen av företagsportalen på macOS <!-- 1734766 -->
Du kan registrera dig för att ta emot versioner tidigt genom att gå med i Insider-programmet med hjälp av Microsoft AutoUpdate. När du registrerat dig kan du använda den uppdaterade företagsportalen innan den är tillgänglig för dina slutanvändare. Mer information finns i [Microsoft Intune-bloggen](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Veckan som inleds med den 2 juli 2018

### <a name="app-management"></a>Apphantering

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Övervaka konfigurationsstatus för iOS-appar per enhet <!-- 880037 -->
Som administratör för Microsoft Intune kan du övervaka konfigurationsstatusen för iOS-appar för varje hanterad enhet. Gå till **Microsoft Intune** i Azure Portal och välj **Enheter** > **Alla enheter**. Välj en specifik enhet från listan med hanterade enheter för att visa ett blad för enheten. Välj **Appkonfiguration** på enhetsbladet.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Åtkomståtgärder för appskyddsprinciper <!-- 1483510 -->
Du kan konfigurera appskyddsprinciper för att uttryckligen rensa, blockera eller varna icke-kompatibla enheter. Åtgärden *Rensa* tar bort företagets företagsdata från en enhet. Om en rensning utförs meddelas enhetens användare om både orsaken till rensningen och reparationsstegen. För vissa inställningar som lägsta version av operativsystemet, kommer du att kunna använda flera åtgärder, till exempel blockering och rensa. Observera att de här åtgärderna utlöses när appen startas.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Selektiv rensning av organisations appdata <!-- 1507030 -->
Nu kan administratörer konfigurera en selektiv rensning av organisationens data som en ny åtgärd när villkoren i APP-åtkomstinställningarna inte uppfylls.  Den här funktionen gör att administratörer kan skydda och ta bort känsliga organisationsdata från appar baserat på förkonfigurerade kriterier.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Återkalla en iOS-app som köpts via VPP <!-- 1777384 -->
Som Microsoft Intune-administratör kan du återkalla alla licenser för en iOS-app som köpts via volyminköpsprogrammet (VPP). Du kan meddela användarna när en användarlicensierad app inte längre är tilldelad till dem. Om du återkallar en applicens så avinstalleras inte den relaterade VPP-appen från enheten. Om du vill avinstallera en VPP-app, måste du ändra tilldelningsåtgärden till **avinstallera**. Du kan se antalet återkallade licenser vid noden **Licensierade appar** i arbetsbelastningen **App** i Intune. Mer information om VPP-appar i iOS finns i [Så här hanterar du iOS-appar som köpts genom ett volyminköpsprogram med Microsoft Intune](vpp-apps-ios.md).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Uppdateringar till meddelanden om brist på efterlevnad i företagsportalappen <!-- 1832222 -->
Vi har uppdaterat meddelandena som visas för enhetsanvändarna när en enhet inte är kompatibel. Meddelandena behåller sina ursprungliga betydelser men har uppdaterats med mer användarvänligt språk och mindre teknisk jargong. Vi har även uppdaterat länkar till dokumentation och reparationssteg så att de är uppdaterade.
Följande text är ett exempel på de förbättrade meddelandena som du kommer att se:
- **Före**: *Den här enheten har inte kontaktat Intune-tjänsten inom den tidsperiod som krävs av din IT-administratör. Du kan lösa det här problemet genom att öppna företagsportalappen på enheten och klicka på knappen Kontrollera efterlevnad.*
- **Efter**: *Din enhet har inte checkat in med organisationen på ett tag. Återupprätta anslutningen genom att öppna företagsportalappen på enheten och trycka på Kontrollera inställningar för enheten.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Återkalla VPP-applicenser i iOS <!-- 1863797 -->
Som administratör kan du frigöra en iOS VPP-applicens som har tilldelats en användare eller enhet. När du avinstallerar en VPP-app i iOS kan du också återkalla applicensen. Innan du avinstallerar appen måste användaren eller enheten tas bort från gruppen som är appens mål. Om användaren eller enheten tas bort från gruppen behöver inte appen installeras om. När dessa steg har slutförts kan du välja att tilldela applicensen till en annan användare eller enhet. Mer information om licenser för VPP-appar i iOS finns i [Hantera volyminköpta iOS-appar i Microsoft Intune](vpp-apps-ios.md).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Välj enhetskategorier med hjälp av inställningarna för åtkomst till arbete eller skola <!-- 1058963 eenotready --> 
Om du har aktiverat [mappning av enhetsgrupp](https://docs.microsoft.com/en-us/intune/device-group-mapping), uppmanas Windows 10-användare nu att välja en enhetskategori efter registreringen via knappen **Anslut** i **Inställningar** > **Konton** > **Åtkomst till arbete eller skola**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Använd sAMAccountName som användarnamn för e-postprofiler <!-- 1500307 -->
Du kan använda det lokala **sAMAccountName** som kontonamn för e-postprofiler för Android, iOS och Windows 10. Du kan även hämta domänen från attributet `domain` eller `ntdomain` i Azure Active Directory (Azure AD). Eller ange en anpassad statisk domän.

Om du vill använda den här funktionen måste du synkronisera attributet `sAMAccountName` från din lokala Active Directory-miljö till Azure AD.

Gäller [Andoid](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 och senare](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Se enhetskonfigurationsprofiler som har konflikter <!-- 1556983 -->
I **Enhetskonfiguration** visas en lista över de befintliga profilerna. I och med den här uppdateringen läggs en ny kolumn till som innehåller information om de profiler som står i konflikt. Du kan välja en rad med en konflikt för att se den inställning och den profil som orsakar konflikten. 

Mer om [hantering av konfigurationsprofiler](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Ny status för enheter i enhetsefterlevnad <!-- 2308882 -->
Följande nya tillstånd har lagts till i **Enhetskonfiguration** > **Principer** > välj en princip > **Översikt**:
- lyckades
- fel
- konflikt
- Väntar
- inte tillämpligt En bild med antalet enheter på andra plattformar visas också. Om du till exempel tittar på en iOS-profil visas antalet enheter med andra system än iOS som också har tilldelats till den här profilen. Se [Efterlevnadsprinciper för enheter](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Enhetsefterlevnaden får stöd för antiviruslösningar från tredje part <!-- 2325484 -->
När du skapar en ny princip för enhetsefterlevnad (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Plattform: Windows 10 eller senare** > **Inställningar** > **Systemsäkerhet**) är några nya alternativ för **[Enhetssäkerhet](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)** tillgängliga: 
- **Antivirus**: När **Kräv** har valts kan du kontrollera efterlevnaden med antivirusprogram som är registrerade i Windows Security Center, t.ex. Symantec och Windows Defender. 
- **Antispionprogram**: När **Kräv** har valts kan du kontrollera efterlevnaden med antispionprogram som har registrerats med Windows Security Center, t.ex. Symantec och Windows Defender. 

Gäller: Windows 10 och senare 

### <a name="device-enrollment"></a>Enhetsregistrering

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Enheter utan profilkolumn i listan med token för registreringsprogram <!-- 1853904 -->
Det finns en ny kolumn i listan med token för registreringsprogram som visar antalet enheter som inte har någon tilldelad profil. På så sätt kan administratörer tilldela profiler till dessa enheter innan användarna får dem. Om du vill se den nya kolumnen går du till **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram**.

### <a name="device-management"></a>Enhetshantering

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Googla namnändringar för Android for Work och Play for Work <!--842873 -->
Intune har uppdaterat ”Android for Work”-terminologin med Googles namnändringar. Termerna ”Android for Work” och ”Play for Work” används inte längre. Annan terminologi används beroende på kontext:
- ”Android enterprise” syftar på den moderna programserien för Android-hantering som helhet.
- ”Arbetsprofil” eller ”profilägare” syftar på BYOD-enheter som hanteras med arbetsprofiler.
- ”Managed Google Play” syftar på Googles appbutik.

#### <a name="rules-for-removing-devices----1609459---"></a>Regler för att ta bort enheter <!-- 1609459 -->
Det finns nya regler som gör att du automatiskt kan ta bort enheter som inte har checkats in under ett visst antal dagar som du anger. Om du vill se den nya regeln går du till fönstret **Intune**, väljer **Enheter** och sedan **Regler för rensning av enhet**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>COSU-stöd (Corporate Owned, Single Use) för Android-enheter <!-- 1630973 -->

Nu har Intune stöd för strikt hanterade och låsta Android-enheter i helskärmsläge. Det här gör att administratörer får fler verktyg när det gäller att begränsa användningen på en enhet till en enda upp eller en grupp av appar, så att användarna inte kan starta andra appar eller utföra andra åtgärder på enheten. Du konfigurerar Android-kioskenheter genom att gå till Intune > **Enhetsregistrering** > **Android-registrering** > **Registreringar av kiosk- och aktivitetsenheter**. Läs mer i informationen om att [konfigurera registrering av Android-kioskenheter för företag](android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Radgranskning av dubbletter av uppladdade företagsenhets-id:n <!-- 2203794-->
När du laddar upp företags-ID:n får du nu en lista med eventuella dubbletter i Intune, och du kan välja mellan att ta bort eller behålla den befintliga informationen. Rapporten visas om det finns dubbletter när du har valt **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till id:n**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Lägga till företagsenhets-id:n manuellt <!-- 2203803 -->
Nu kan du lägga till ID:n för företagsenheter manuellt. Välj **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till**. 

## <a name="week-of-june-25-2018"></a>Veckan som inleds med 25 juni, 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo – ny partner för skydd mot mobilhot <!-- 1169249 -->

Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Pradeo, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune.

## <a name="week-of-june-18-2018"></a>Veckan som inleds med 18 juni, 2018

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Edge-mobilstöd för Intune-appskyddsprinciper <!-- 1817882 -->

Microsoft Edge-webbläsaren för mobila enheter stödjer nu appskyddsprinciper som definieras i Intune.

## <a name="week-of-june-11-2018"></a>Veckan som inleds med 11 juni, 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Använd FIPS-läge med NDES-certifikatanslutningsappen <!-- 1333688 -->
När du installerar NDES-certifikatanslutningsappen på en dator med FIPS-läget (Federal Information Processing Standard) aktiverat fungerade inte utfärdande och återkallande av certifikat som förväntat. I och med den här uppdateringen ingår stöd för FIPS i NDES-certifikatanslutningsappen. 

Den här uppdateringen innehåller även:

- För NDES-certifikatanslutningsappen krävs .NET 4.5 Framework, som automatiskt ingår i Windows Server 2016 och Windows Server 2012 R2. Tidigare var .NET 3.5 Framework den minimiversion som krävdes.
- Stöd för TSL 1.2 ingår i NDES-certifikatanslutningsappen. Om servern med NDES-certifikatanslutningsappen installerat stödjer TLS 1.2 används därmed TLS 1.2. Om servern inte stödjer TLS 1.2 används TLS 1.1. För närvarande används TLS 1.1 för autentisering mellan enheter och servern.

Mer information finns på sidorna om att [konfigurera och använda SCEP-certifikat](certificates-scep-configure.md) och [konfigurera och använda PKCS-certifikat](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Vecka 4 juni 2018

### <a name="app-management"></a>Apphantering

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Hämta den kopplade appanvändarens modell-ID (AUMID) för Microsoft Store för företagsappar i helskärmsläge <!-- 1560077 ! -->
Intune kan nu hämta appanvändarens modell-ID:n (AUMID:er) för Microsoft Store för företagsappar (WSfB) för bättre konfiguration av helskärmslägesprofilen.

Mer information om Microsoft Store för företagsappar finns i [Hantera appar från Microsoft Store för företag](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Ny sida för företagsportalanpassning <!-- 1916370 -->
Sidan för företagsportalanpassning har en ny layout, nya meddelanden och beskrivningar.


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Stöd för Palo Alto Networks GlobalProtect VPN-profiler <!-- 1333680 eeready ! -->
Med den här uppdateringen kan du välja Palo Alto Networks GlobalProtect som VPN-anslutningstyp för VPN-profiler i Intune (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Profiltyp** > **VPN**). I den här versionen stöds följande plattformar: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Tillägg till inställningar av säkerhetsalternativ för lokal enhet <!-- 1403702 -->
Nu kan du konfigurera ytterligare inställningar av säkerhetsalternativ för lokala Windows 10-enheter. Det finns fler inställningar i Microsoft-nätverksklienten, Microsoft-nätverksservern, för nätverksåtkomst och säkerhet, samt för interaktiv inloggning. Inställningarna finns i kategorin Endpoint Protection när du skapar en princip för Windows 10-enhetskonfiguration.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Aktivera helskärmsläge på Windows 10-enheter <!-- 1560072 ! -->
På Windows 10-enheter kan du skapa en konfigurationsfil och aktivera helskärmsläge (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10** > **Enhetsbegränsningar** > **Helskärmsläge**). I den här uppdateringen av **Helskärmsläge (förhandsgranskning)** döps inställningen om till **Helskärmsläge (föråldrad)**. **Helskärmsläge (föråldrad)** rekommenderas inte längre för användning, men fortsätter att fungera fram till juli-uppdateringen. **Helskärmsläge (föråldrad)** ersätts av den nya profiltypen **Helskärmsläge** (**Skapa profil** > **Windows 10**  >  **Helskärmsläge (förhandsgranskning)**), som innehåller inställningar för att konfigurera helskärmslägen på Windows 10 RS4 och senare.

Gäller för Windows 10 och senare.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Enhetsprofilens grafiska användardiagram är tillbaka <!-- 2160133 -->
För att förbättra det numeriska antal som visas på enhetsprofilens grafiska diagram (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**), togs det grafiska diagrammet tillfälligt bort.

Med den här uppdateringen är det grafiska användardiagrammet tillbaka och visas i Azure Portal.

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>Stöd för Windows Autopilot-registrering utan användarautentisering <!-- 1165118 wnready -->
Nu finns det stöd i Intune för Windows Autopilot-registrering utan användarautentisering. Det här är ett nytt alternativ i distributionsprofilen för Windows Autopilot där ”Distributionsläge för Autopilot” får värdet ”Automatisk distribution”.  Enheten måste köra Windows 10 Insider Preview-version 17672 eller senare och ha ett TPM 2.0-chip för att slutföra den här typen av registrering. Eftersom det inte krävs någon användarautentisering bör du bara tilldela det här alternativet för enheter du har fysisk kontroll över.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>Ny språk-/regionsinställning när du konfigurerar OOBE för Autopilot <!-- 1821766 eeready -->
En ny konfigurationsinställning kan ange språk och region för Autopilot-profiler från första början. Du ser den nya inställningen om du väljer **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil** > **Distributionsläge** = **Självdistribuerande** > **Standardkonfiguration**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Ny inställning för att konfigurera enhetstangentbord <!-- 1821768 -->
En ny inställning kommer att kunna konfigurera tangentbordet för Autopilot-profiler under Out of Box-upplevelsen. Du ser den nya inställningen om du väljer **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil** > **Distributionsläge** = **Självdistribuerande** > **Standardkonfiguration**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-profiler flyttas till en grupp som är riktad mot <!-- 1877935 -->
AutoPilot-distributionsprofiler kan tilldelas till Azure AD-grupper som innehåller AutoPilot-enheter.

### <a name="device-management"></a>Enhetshantering

#### <a name="set-compliance-by-device-location----851881----"></a>Ange efterlevnad enligt enhetsplats <!-- 851881 ! -->
I vissa fall kanske du vill begränsa åtkomsten till företagets resurser till en specifik plats som definierats av en nätverksanslutning. Nu kan du skapa en efterlevnadsprincip (**Enhetsefterlevnad** > **Platser**) baserat på IP-adressen till enheten. Om enheten flyttas utanför IP-intervallet kan enheten inte komma åt företagets resurser.

Gäller: Android-enheter 6.0 och senare med den uppdaterade företagsportalappen

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Förhindra konsumentappar och funktioner för anpassad upplevelse i Windows 10 Enterprise RS4 AutoPilot-enheter<!-- 1621980 -->
Du kommer att kunna förhindra installationen av konsumentappar och funktioner för anpassad upplevelse på dina Windows 10 Enterprise RS4 AutoPilot-enheter. Du ser den här funktionen om du går till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Plattform** = **Windows 10 eller senare** > **Profiltyp** = **Enhetsbegränsningar** > **Konfigurera** > **Windows Spotlight** > **Konsumentfunktioner**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>Avinstallera den senaste programuppdateringen för Windows 10 <!-- 1732948 eeready -->
Om du upptäcker ett allvarligt problem på dina Windows 10-datorer kan du avinstallera den senaste funktionsuppdateringen eller den senaste kvalitetsuppdateringen. Du kan bara avinstallera en funktions- eller kvalitetsuppdatering via enhetens underhållskanal. Vid avinstallationen utlöses en princip för att återställa den tidigare uppdateringen på Windows 10-datorerna. För funktionsuppdateringar specifikt kan du begränsa tiden från 2–60 dagar som en avinstallation av den senaste versionen kan tillämpas. Om du vill ange alternativ för avinstallation av programuppdateringar väljer du **Programuppdateringar** från bladet **Microsoft Intune** i Azure Portal. Välj sedan **Windows 10-uppdateringsringar** på bladet **Programuppdateringar**. Du kan sedan välja alternativet **Avinstallera** i avsnittet **Översikt**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Söka alla enheters IMEI och serienummer <!-- 1793685 -->
Du kan nu söka efter IMEI och serienummer på bladet Alla enheter (e-post, UPN, enhetsnamn och hanteringsnamn finns kvar). Välj **Enheter** > **Alla enheter** i Intune och ange dina sökvillkor i sökrutan.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Hanteringsnamnfältet kan redigeras <!-- 1875989 -->
Nu kan du redigera hanteringsnamnfältet på bladet **Egenskaper** för en enhet. Om du vill redigera det här fältet väljer du **Enheter** > **Alla enheter** > välj enheten > **Egenskaper**. Du kan använda hanteringsnamnfältet för att unikt identifiera en enhet.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nytt filter för Alla enheter: Enhetskategori <!-- 1878520 -->
Nu kan du filtrera listan **Alla enheter** efter enhetskategori. Om du vill göra det väljer du **Enheter** > **Alla enheter** > **Filter** > **Enhetskategori**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Använd TeamViewer för att skärmdela iOS- och MacOS-enheter <!-- 1985547 -->
Nu kan administratörer ansluta till [TeamViewer](device-profile-android-teamviewer.md) och börja skärmdela en session med iOS- och macOS-enheter. iPhone-, iPad- och macOS-användare kan dela sina skärmar live med andra stationära och mobila enheter. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Stöd för flera Exchange Connector <!-- 2070451 -->
Du är inte längre begränsad till en Exchange-anslutningsapp per klientorganisation i Microsoft Intune. Intune har nu stöd för flera Exchange-anslutningsappar, så att du kan ställa in villkorlig åtkomst i Intune med flera lokala Exchange-organisationer.

Med en lokal Exchange Connector för Intune kan du hantera enhetsåtkomst till dina lokala Exchange-postlådor, baserat på om en enhet har registrerats i Intune och uppfyller Intunes enhetsefterlevnadsprinciper. Om du vill konfigurera ett anslutningsprogram laddar du ned den lokala Exchange Connector för Intune från Azure-portalen och installerar den på en server i Exchange-organisationen. På Microsoft Intune-instrumentpanelen väljer du **Lokal åtkomst** och under **Installation** väljer du sedan **Exchange ActiveSync Connector**. Ladda ned det lokala Exchange-anslutningsprogrammet och installera det på en server i din Exchange-organisation. Nu när du är inte längre begränsad till ett Exchange-anslutningsprogram per klient, och om du har ytterligare Exchange-organisationer, kan du följa samma process för att ladda ned och installera ett anslutningsprogram för varje ytterligare Exchange-organisation.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Ny detalj i enhetens maskinvara: CCID <!-- 2156657 -->
Nu ingår CCID-informationen (Chip Card Interface Device) för varje enhet. Om du vill se den väljer du **Enheter** > **Alla enheter** > välj en enhet > **Maskinvara**> leta under **Nätverksinformation**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Tilldela alla användare och alla enheter som omfångsgrupper <!-- 2196803 -->
Nu kan du tilldela alla användare, alla enheter samt alla användare och alla enheter i omfångsgrupper. Om du vill göra det väljer du **Intune-roller** > **Alla roller** > **Policy and profile manager** > **Tilldelningar** > välj en tilldelning > **Omfång (grupper)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>Nu ingår UDID-information för iOS- och macOS-enheter <!-- 2219806 wnready-->
Om du vill se UDID (Unique Device Identifier) för iOS- och macOS-enheter går du till **Enheter** > **Alla enheter** > välj en enhet > **Maskinvara**. UDID är endast tillgängligt för företagsenheter (anges under **Enheter** > **Alla enheter** > välj en enhet > **Egenskaper** > **Ägarskap för enhet**).

### <a name="intune-apps"></a>Intune-appar

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Förbättrad felsökning för appinstallationen <!-- 928990 -->
På Microsoft Intune MDM-hanterade enheter kan ibland appinstallationer misslyckas. När dessa appinstallationer misslyckas, kan det vara en utmaning att förstå felorsaken eller felsöka problemet. Vi levererar en allmänt tillgänglig förhandsversion av våra appfelsökningsfunktioner. Du ser en ny nod under varje enskild enhet som kallas **Hanterade appar**. Den visar en lista med appar som har levererats via Intune MDM. I noden visas en lista över installeringstillstånd för appar. Om du väljer en enskild app visas vyn felsökning för den specifika appen. I felsökningsvyn visas slutpunkt till slutpunkt-livscykeln för appen, till exempel när appen har skapats, ändrats, riktats och levererats till en enhet. Dessutom, om inte appinstallationen lyckades visas felkoden och ett användbart meddelande om orsaken till felet. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Skyddsprinciper för Intune-appen och Microsoft Edge <!-- 1818968 -->
Microsoft Edge-webbläsaren för mobila enheter (iOS och Android) har nu stöd för skyddsprinciper i Microsoft Intune-appen. Användare med iOS- och Android-enheter som loggar in med företagets Azure AD-konto i Edge kommer att skyddas av Intune. På iOS-enheter gör principen **Kräver hanterad webbläsare för webbinnehåll** att användarna kan öppna länkar i Edge när det hanteras.

## <a name="week-of-may-14-2018"></a>Vecka 14 maj 2018

### <a name="app-management"></a>Apphantering

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Kräv installation av principer, appar, certifikat och nätverksprofiler <!-- 1553555 -->

Administratörer kan blockera slutanvändarna från att komma åt skrivbordet i Windows 10 RS4 tills Intune har installerat principer, appar, certifikat och nätverksprofiler under etableringen av AutoPilot-enheter. Mer information finns i [Konfigurera en sida för registreringsstatus](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Konfigurera dina appskyddsprinciper <!-- 2144597 Part 2 -->

I stället för att gå till bladet för Intunes appskyddstjänst på Azure Portal går du bara till Intune nu. Nu finns det bara en plats för appskyddsprinciper i Intune. Observera att alla dina appskyddsprinciper finns på bladet **Mobilapp** i Intune under **Appskyddsprinciper**. Den här integrationen gör det enklare att administrera molnhanteringen. Alla appskyddsprinciper finns redan i Intune och du kan ändra redan konfigurerade principer. Intunes apprincipskydd (APP) och principer för villkorlig åtkomst (CA) finns nu under **Villkorlig åtkomst**, som du hittar under avsnittet **Hantera** på bladet **Microsoft Intune** under avsnittet **Säkerhet** på bladet **Azure Active Directory**. Mer information om hur du ändrar principer för villkorlig åtkomst finns [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Ytterligare information finns i [Vad är appskyddsprinciper?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Vecka 7 maj 2018

### <a name="app-management"></a>Apphantering

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Stöd för Samsung Knox Mobile-registrering <!--1112863-->

När du använder Intune med Samsung Knox Mobile-registrering (KME), kan du registrera ett stort antal företagsägda Android-enheter. Användarna på Wi-Fi eller mobila nätverk kan registrera sig med bara några få tryck när de aktiverar på sina enheter för första gången. När du använder Knox-distributionsprogrammet kan enheter registreras med hjälp av Bluetooth eller NFC. Mer information finns i [Registrera Android-enheter automatiskt med hjälp av från Samsung Knox Mobile-registrering](android-samsung-knox-mobile-enroll.md).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Be om hjälp i företagsportalen för Windows 10 <!-- 1874137 -->

Företagsportalen för Windows 10 kommer nu att skicka apploggar direkt till Microsoft när användaren startar arbetsflödet för att få hjälp med problemet. Detta gör det enklare att felsöka och lösa problem som tas upp till Microsoft.

## <a name="week-of-april-23-2018"></a>Veckan 23 april 2018

### <a name="app-management"></a>Apphantering

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Lösenordsstöd för MAM PIN-kod på Android<!-- 1438086 -->

Intune-administratörer kan ange ett programstartskrav för att framtvinga ett lösenord i stället för en numerisk MAM PIN-kod. Om det har konfigurerats måste användaren vid uppmaning ställa in och använda ett lösenord innan användaren får åtkomst till MAM-integrerade program. Ett lösenord definieras som en numerisk PIN-kod med minst ett specialtecken eller en gemen/versal. Intune stöder lösenord på liknande sätt som numeriska PIN-koder. En minsta längd kan anges, vilket tillåter upprepning av tecken och sekvenser via administratörskonsolen. Den här funktionen kräver den senaste versionen av företagsportalen för Android. Funktionen finns redan tillgänglig för iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Stöd för verksamhetsspecifika appar (LOB) för macOS <!-- 1473977 -->
I Microsoft Intune går det att installera branschspecifika macOS-appar från Azure Portal. Du kommer att kunna lägga till en branschspecifik macOS-app i Intune som redan har förbehandlats av verktyget i GitHub. I Azure Portal väljer du **Klientappar** på bladet **Intune**. På bladet **Klientappar** väljer du **Appar** > **Lägg till**. På bladet **Lägg till app** väljer du **Branschspecifik app**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Inbyggd apptilldelning av gruppen Alla användare och Alla enheter för Android for Work (AFW) <!-- 1813073 -->
Du kan använda de inbyggda grupperna **Alla användare** och **Alla enheter** vid AFW-apptilldelning. Mer information finns i [Inkludera och exkludera apptilldelningar i Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune kommer att installera om obligatoriska appar som avinstalleras av användare <!-- 1947010 -->
Om en slutanvändare avinstallerar en obligatorisk app, installerar Intune automatiskt om appen igen inom 24 timmar i stället för att vänta på omvärderingscykeln på 7 dagar.

### <a name="device-configuration"></a>Enhetskonfiguration

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Enhetens profildiagram och statuslista visar alla enheter i en grupp <!-- 1449153 eeready -->
När du konfigurerar en enhetsprofil (**Enhetskonfiguration** > **Profiler**) väljer du enhetsprofil, till exempel iOS. Du tilldelar profilen till en grupp med både iOS-enheter och enheter som inte är iOS. Antalet i det grafiska diagrammet visar att profilen tillämpas på både iOS-enheter *och* enheter som inte är iOS (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**). När du väljer det grafiska diagrammet på fliken **Översikt** visar **Enhetsstatus** alla enheterna i gruppen, i stället för enbart iOS-enheterna. 

Med den här uppdateringen visar det grafiska diagrammet (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**) endast antalet för den specifika enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för iOS-enheter, visar diagrammet endast antal iOS-enheter. Om du väljer det grafiska diagrammet och öppnar **Enhetsstatus**, visas endast iOS-enheterna.

När uppdateringen gjorts har det grafiska diagrammet tillfälligt tagits bort. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>AlwaysOn-VPN för Windows 10 <!--1333666 -->

För närvarande kan [AlwaysOn](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) användas på Windows 10-enheter med hjälp av en anpassad VPN-profil (virtuellt privat nätverk) som skapats med OMA-URI.

Med den här uppdateringen kan administratörer aktivera AlwaysOn för VPN-profiler i Windows 10 direkt i Intune i Azure-portalen. VPN-profiler med AlwaysOn ansluts automatiskt när:

- Användarna loggar in på sina enheter
- Nätverket på enheten ändras
- Skärmen på enheten sätts på efter att ha varit avstängd

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nya skrivarinställningar för utbildningsprofiler <!-- 1308900 -->

För utbildningsprofiler finns nya inställningar under kategorin **Skrivare**: **Skrivare**, **Standardskrivare**, **Lägg till nya skrivare**.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Visa nummerpresentation i personlig profil – Android for Work <!--1098984 -->
När du använder en personlig profil på en enhet, kan slutanvändare inte se nummerpresentation för en arbetskontakt. 

I och med uppdateringen finns en ny inställning i **Android for Work** > **Enhetsbegränsningar** > **Arbetsprofilinställningar**:
- Visa arbetskontaktens nummerpresentation i personlig profil

När aktiverat (inte konfigurerat), visas arbetskontaktens nummerpresentation i den personliga profilen. När blockerad, visas inte arbetskontaktens nummerpresentation i den personliga profilen. 

Gäller för: Androids arbetsprofilenheter på Android OS v6.0 och senare

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nya Windows Defender Credential Guard-inställningar har lagts till i inställningarna för slutpunktsskydd<!--1102252 --><!--from 1802 and 1804-->

Med denna uppdatering, inkluderar [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Enhetskonfiguration** > **Profiler** > **Slutpunktsskydd**) följande inställningar: 

- **Windows Defender Credential Guard**: Aktiverar Credential Guard med virtualiseringsbaserad säkerhet. Aktivering av den här funktionen hjälper till att skydda autentiseringsuppgifterna vid nästa omstart när både **Säker start för Säkerhetsnivå för plattform** och **Virtualiseringsbaserad säkerhet** är aktiverade. Alternativen är:
  - **Inaktiverad**: Om Credential Guard tidigare slagits på med alternativet**Aktiverat utan lås**, slås Credential Guard av på distans.

  - **Aktiverat med UEFI-lås**: Ser till att Credential Guard inte kan inaktiveras med registernyckel eller via en grupprincip. Om du vill inaktivera Credential Guard när du använder den här inställningen måste du ställa in Grupprincip som ”Inaktiverad”. Ta sedan bort säkerhetsfunktionen från varje dator med en användare fysiskt närvarande. De här stegen rensar den kvarstående konfigurationen i UEFI. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.

  - **Aktiverat utan lås**: Medför att Credential Guard kan inaktiveras via fjärranslutning med grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 eller senare (version 1511).

Följande beroende tekniker aktiveras automatiskt när du konfigurerar Credential Guard: 

  - **Aktivera virtualiseringsbaserad säkerhet (VBS)**: Aktiverar virtualiseringsbaserad säkerhet (VBS) vid nästa omstart. Virtualiseringsbaserad säkerhet använder Windows Hypervisor för att ge stöd för säkerhetstjänster och kräver Säker start.
  - **Säker start med Direkt minnesåtkomst**: Aktiverar VBS med Säker start och Direkt minnesåtkomst. DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Använda ett anpassat certifikatmottagarnamn på SCEP-certifikat <!-- 2064190 -->
Du kan använda det egna namnet **OnPremisesSamAccountName** i en anpassad certifikatmottagare för en SCEP-certifikatprofil. Du kan till exempel använda `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Blockera kamera och skärmbilder i Android for Work <!-- 1098977 eeready-->
Två nya egenskaper kan blockeras när du konfigurerar enhetsbegränsningar för Android-enheter: 
- Kamera: Blockerar åtkomsten till alla kameror på enheten
- Skärmbild: Blockerar skärmbildtagning och förhindrar också att innehållet visas på enheter som inte har en säker videoutgång

Gäller Android for Work.


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nya registreringssteg för användarna på enheter med macOS High Sierra 10.13.2+ <!--1734567 -->
I macOS High Sierra 10.13.2 finns nu begreppet ”Användargodkänd” MDM-registrering. Godkända registreringar tillåter Intune att hanterar vissa säkerhetskänsliga inställningar. Mer information finns i Apples supportdokumentation här: https://support.apple.com/HT208019.

Enheter som registreras med macOS-företagsportalen betraktas som ”Inte användargodkända” tills användaren öppnar systeminställningarna och ger sitt manuella godkännande. Därför dirigerar macOS-företagsportalen nu användare av macOS 10.13.2 och senare till att manuellt godkänna registreringen i slutet av registreringsprocessen. Intune-administratörskonsolen rapporterar om en registrerad enhet är användargodkänd.



### <a name="device-management"></a>Enhetshantering

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>Advanced Threat Protection (ATP) och Intune är helt integrerade <!-- EEready 1629303 -->

[Avancerat skydd (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) visar risknivån för Windows 10-enheter. I Windows Defender Security Center (ATP-portal), kan du skapa en anslutning till Microsoft Intune. När du skapat anslutningen används en efterlevnadsprincip av Intune för att fastställa en godtagbar hotnivå. Om hotnivån överskrids kan sedan en villkorlig åtkomstprincip för Azure Active Directory (AD) blockera åtkomst till olika appar i din organisation.

Den här funktionen tillåter ATP att söka igenom filer, identifiera hot och rapportera eventuella risker på Windows 10-enheter.

Se [Aktivera ATP med villkorlig åtkomst i Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Stöd för användarlösa enheter <!-- 1637553 -->
Intune stöder möjligheten att utvärdera efterlevnaden på en användarlös enhet som exempelvis Microsoft Surface Hub. Policyer för efterlevnad kan riktas mot specifika enheter. Det innebär att efterlevnad (och inkompatibilitet) kan fastställas för enheter som inte har någon associerad användare.

#### <a name="delete-autopilot-devices----1713650---"></a>Ta bort AutoPilot-enheter <!-- 1713650 -->
Intune-administratörer kan [ta bort AutoPilot-enheter](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Förbättrad enhetsborttagning <!--1832333 -->
Du kommer inte längre behöva ta bort företagets data eller fabriksåterställa en enhet innan du [tar bort enheten från Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Om du vill se den nya funktionen loggar du in på Intune och väljer **Enheter** > **Alla enheter** > namnet på enheten > **Ta bort**.

Om du fortfarande vill att rensningen ska utföras kan du använda standardenhetens livscykel med hjälp av **Ta bort företagsinformation** och **Fabriksåterställning** innan du väljer **Ta bort**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Spela upp ljud på iOS när den befinner sig i Borttappat läge <!-- 1947769 -->
När övervakade iOS-enheter är i hanteringen av mobilenheters (MDM) [Borttappat läge](device-lost-mode.md), kan du [spela upp ett ljud](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Enheter** > **Alla enheter** > välj en iOS-enhet > **Översikt** > **Mer**). Ljudet fortsätter att spelas upp tills enheten tas bort från Borttappat läge, eller en användare stänger av ljudet. Gäller för iOS-enheter 9.3 och nyare.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Blockera eller tillåta webbresultat i sökningar på en Intune-enhet <!--1972804-->

Administratörer kan nu blockera webbresultat från sökningar gjorda på en enhet.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Förbättrade felmeddelanden när Apple MDM-pushcertifikat inte kan överföras <!-- 2172331 -->

Felmeddelandet förklarar att samma Apple-ID måste användas när du förnyar ett befintligt MDM-certifikat.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Testa företagsportalen för macOS på virtuella datorer <!-- 2216679 -->

Vi har publicerat vägledning som hjälper IT-administratörer testa företagsportalappen för macOS i Parallels Desktop och VMware Fusion. Du hittar mer information i avsnittet om att [registrera virtuella macOS-datorer för testning](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Användargränssnitt

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Förbättrade enhetspaneler i företagsportalen för Windows 10 <!--2213364 -->

Panelerna har uppdaterats för att blir lättillgängligare för användare med sämre syn och för att fungera bättre tillsammans med skärmläsningsverktyg.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Skicka diagnostikrapporter i företagsportalappen för macOS <!-- 2216677 -->
Företagsportalappen för macOS-enheter har uppdaterats för att förbättra hur användarna rapporterar Intune-relaterade fel. Från företagsportalappen kan dina anställda:

- Ladda upp diagnostikrapporter direkt till Microsofts utvecklingsteam.
- E-posta ett incident-ID till ditt företags IT-supportteam.

Mer information finns i [Skicka fel till rätt personer för din hanterade macOS-enhet](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune anpassar sig efter Fluent Design System i företagsportalappen för Windows 10 <!-- 1195010 WNready -->
Intunes företagsportalapp för Windows 10 har uppdaterats med [Fluent Design Systems navigeringsvy](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics). Längs appen ser du en statisk, lodrät lista över alla sidor på översta nivån. Klicka på en länk för att snabbt visa och växla mellan sidor. Det här är den första av flera uppdateringar som visas som en del av vårt pågående arbete för att skapa en mer anpassningsbar, empatisk och bekant upplevelse i Intune. Gå till avsnittet om [nyheter i appgränssnittet](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Veckan 16 april 2018

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>Använda Cisco AnyConnect klienten för iOS <!-- EEready 1333708 -->

När du skapar en ny VPN-profil för iOS finns nu två alternativ: **Cisco AnyConnect** och **Cisco Legacy AnyConnect**. Cisco AnyConnect-profiler stöder 4.0.7x och nyare versioner. Befintliga iOS Cisco AnyConnect VPN-profiler är märkta **Cisco Legacy AnyConnect** och kommer fortsatt att fungera med Cisco AnyConnect 4.0.5x och äldre versioner som de gör i dag.

> [!NOTE]
> Den här ändringen gäller bara för iOS. Det finns fortfarande ett enda Cisco AnyConnect-alternativ för Android-, Android for Work- och macOS-plattformar.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>MacOS Jamf-registrerade enheter kan nu registreras med Intune <!-- 2370684 -->

Version 1.3 och 1.4 av macOS-företagsportal registrerades inte Jamf-enheter med Intune korrekt. Version 1.4.2 av macOS-portalen åtgärdar det här problemet.


## <a name="week-of-april-9-2018"></a>Veckan som börjar med 9 april 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Uppdaterad hjälpfunktion i företagsportalappen för Android <!-- 1631531 -->

Vi har uppdaterat hjälpfunktionen i Android-versionen av företagsportalappen och anpassat den till bästa praxis för Android-plattformen. När användarna stöter på ett problem i appen kan de nu trycka på **Menu (Meny)** > **Help (Hjälp)** och:
- Skicka diagnostikloggar till Microsoft.
- Skicka ett e-postmeddelande som beskriver problemet och incident-ID till företagets supportavdelning.  

Om du vill kolla in den uppdaterade hjälpfunktionen går du till [Send logs using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) (Skicka loggar via e-post) och [Send errors to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (Skicka fel till Microsoft).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nytt trenddiagram för registreringsfel och tabell över felorsaker <!-- 1471783 -->

På registreringsöversiktssidan kan du se trenden för registreringsfel och de fem viktigaste felorsakerna. Genom att klicka på diagrammet eller tabellen kan du gå in på detaljnivå för att hitta felsökningstips och åtgärdsförslag.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Uppdatera var du konfigurerar dina appskyddsprinciper <!-- 2144597 -->

I tjänsten Microsoft Intune i Azure Portal kommer vi att tillfälligt dirigera om dig från bladet för tjänsten **Intune-appskydd** till bladet **Mobilapp**. Alla dina appskyddsprinciper finns redan på bladet **Mobilapp** i Intune under appkonfigurationen. I stället för att gå till Intune-appskydd går du bara till Intune. I april 2018 stoppar vi omdirigeringen och tar helt bort bladet för tjänsten **Intune-appskydd** så att det bara finns en plats för appskyddsprinciper i Intune. 

**Hur påverkar det här mig?**
Den här förändringen påverkar både kunder som har fristående Intune och hybridkunder (Intune med Configuration Manager). Den här integreringen hjälper till att förenkla administrationen av molnhanteringen.

**Vad kan jag göra för att förbereda mig för den här ändringen?**
Lägg till **Intune** som favorit i stället för bladet för tjänsten **Intune-appskydd**, och se till att du känner till arbetsflödet för appskyddsprinciper på bladet **Mobilapp** i Intune. Vi omdirigerar under en kort tidsperiod och tar sedan bort **appskyddsbladet**. Tänk på att alla appskyddsprinciper redan finns i Intune och att du kan ändra dina villkorliga åtkomstprinciper. Mer information om hur du ändrar principer för villkorlig åtkomst finns [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Ytterligare information finns i [Vad är appskyddsprinciper?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Veckan 2 april 2018

### <a name="intune-apps"></a>Intune-appar

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Uppdatering av användarupplevelsen för appen Företagsportal för iOS <!--1412866 -->
Vi har släppt en större uppdatering av användarupplevelsen i företagsportalappen för iOS. Uppdateringen är en fullständig visuell omarbetning som ger appen en modernare design. Vi har bevarat appens funktionalitet men förbättrat användarvänligheten och tillgängligheten.  

Andra nyheter:
- Stöd för iPhone X.
- Snabbare appstart och inläsning som sparar tid för användarna.
- Fler förloppsindikatorer som ger användarna den senaste statusinformationen.
- Sättet att skicka loggar har förbättrats och det har blivit enklare att rapportera om något går fel.  

Gå till avsnittet om [nyheter i appgränssnittet](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Skydda lokala Exchange-data med hjälp av Intune APP och CA <!-- 1056954 -->
Du kan nu använda Intunes appskyddsprincip (APP) och villkorlig åtkomst (CA) för att skydda åtkomsten till lokala Exchange-data med Outlook Mobile. Om du vill lägga till eller ändra en appskyddsprincip i Azure Portal väljer du **Microsoft Intune** > **Klientappar** > **Appskyddsprinciper**. Innan du använder den här funktionen måste du se till att du uppfyller [kraven för Outlook för iOS och Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="week-of-march-26-2018"></a>Veckan som börjar med 26 mars 2018

### <a name="app-management"></a>Apphantering

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Aviseringar för utgående verksamhetsspecifika appar för Microsoft Intune <!-- 748789 -->

Du får ett meddelande från Intune i Azure Portal om verksamhetsspecifika iOS-appar som snart förfaller. När du laddar upp en ny version av en verksamhetsspecifik iOS-app tar Intune bort förfalloaviseringen från applistan. Förfalloaviseringen är endast aktiv för nyligen överförda verksamhetsspecifika iOS-appar. En varning visas 30 dagar innan etableringsprofilen för den verksamhetsspecifika iOS-appen upphör att gälla. När den upphör ändras aviseringen till Upphört.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Anpassa teman för företagsportalen med hexkoder <!--1049561 -->

Du kan anpassa temafärgen i företagsportalens appar med hexkoder. När du anger en hexkod kan Intune bestämma vilken textkod som ger den högsta kontrastnivån mellan textfärgen och bakgrundsfärgen. Du kan förhandsgranska både textfärgen och företagets logotyp mot färgen i **Klientappar** > **Företagsportal**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inklusive och exklusive apptilldelning baserat på grupperna för Android Enterprise <!-- 1813081 -->

Android Enterprise (tidigare Android for Work) stöder inkludering och exkludering av grupper, men stöder inte de inbyggda grupperna **Alla användare** och **Alla enheter**. Mer information finns i [Inkludera och exkludera apptilldelningar i Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Enhetshantering

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Nya säkerhetsförbättringar i Intune-tjänsten <!-- 1637539 -->   

Vi har introducerat en växlingsknapp i Intune på Azure som de som använder fristående Intune kan använda för att hantera enheter utan tilldelad princip som **kompatibla** (säkerhetsfunktionen av) eller som **inte kompatibla** (säkerhetsfunktionen på). Detta gör att det endast går att komma åt resurser efter att enhetskompatibiliteten har utvärderats.

Den här funktionen påverkar dig på olika sätt beroende på om du redan har tilldelats policyer för efterlevnad eller inte.

- Om du har ett nytt eller befintligt konto och inte har några efterlevnadsprinciper tilldelade till enheterna ställs växlingsknappen automatiskt in på **kompatibel**. Funktionen är inaktiverad som standard i konsolen. Slutanvändaren påverkas inte.
- Om du har ett befintligt konto och har enheter med en tilldelad policy för efterlevnad är växlingsknappen automatiskt inställd på **inte kompatibel**. När marsuppdateringen distribueras är den här funktionen på som standard.

Om du använder policyer för efterlevnad med villkorlig åtkomst (CA) och funktionen är aktiverad blockeras nu eventuella enheter utan minst en tilldelad policy för efterlevnad av CA. Slutanvändarna som är kopplade till dessa enheter, och som tidigare kunde komma åt e-post, förlorar sin åtkomst om du inte tilldelar minst en policy för efterlevnad till alla enheter.   

Observera att även om standardväxlingsstatus visas direkt i användargränssnittet med marsuppdateringarna av Intune-tjänsten tillämpas inte växlingsstatusen omedelbart. Ändringarna du gör med växlingsknappen påverkar inte enhetsefterlevnaden förrän vi har förhandstestat ditt konto och du har en fungerande växling. Vi informerar dig via meddelandecentret när vi är klara med att förhandsversionstesta ditt konto. Detta kan ta upp till ett par dagar efter marsuppdateringarna av Intune-tjänsten.

**Ytterligare information**:[https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Förbättrad upplåsningsidentifiering <!-- 846515 -->

Förbättrad upplåsningsidentifiering är en ny efterlevnadsinställning som förbättrar hur Intune utvärderar jailbreakade enheter. Inställningen gör att enheten checkar in till Intune oftare. Detta innebär att enhetens platstjänster används, vilket påverkar batterianvändningen.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Återställa lösenord för Android O-enheter <!-- 1238299 -->
Du kan återställa lösenorden för registrerade Android 8.0-enheter med arbetsprofiler. När du skickar en begäran om att återställa ett lösenord till en Android 8.0-enhet ställer den in ett nytt lösenord för upplåsning av enheten eller en hanterad profilutmaning för den aktuella användaren. Lösenordet eller kontrollfrågan skickas och träder i kraft omedelbart.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ange mål för efterlevnadsprinciper för enheter i enhetsgrupperna <!--1307012 -->

Du kan ange mål för efterlevnadsprinciper för användare i användargrupperna. Med den här uppdateringen kan du ange mål för efterlevnadsprinciper för enheter i användargrupper. Målenheter som ingår i enhetsgrupper får inte några efterlevnadsåtgärder.

#### <a name="new-management-name-column----1333586---"></a>Ny kolumn för hanteringsnamn <!-- 1333586 -->
 En ny kolumn med namnet **Hanteringsnamn** finns på enhetsbladet. Detta är ett automatiskt genererat, icke-redigerbart namn som tilldelas per enhet, baserat på följande formel:
- Standardnamn för alla enheter: <username><em><devicetype></em><enrollmenttimestamp>
- För masstillagda enheter: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

Det här är en valfri kolumn på enhetsbladet. Den är inte tillgänglig som standard och du har bara åtkomst till den via kolumnväljaren. Namnet på enheten påverkas inte av den här nya kolumnen.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>iOS-enheter uppmanas att ange en PIN-kod var 15:e minut <!--1550837 -->
När en policy för efterlevnad eller konfiguration används på en iOS-enhet, uppmanas användarna att ange en PIN-kod var 15:e minut. Användarna uppmanas kontinuerligt tills en PIN-kod anges.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Schemalägga automatiska uppdateringar <!--1805514 -->
Intune ger dig kontroll vid installation av automatiska uppdateringar med hjälp av [Inställningar för Windows 10-uppdateringsring](windows-update-for-business-configure.md). Med den här uppdateringen kan du schemalägga återkommande uppdateringar, inklusive vecka, dag och tid.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Använd ett fullständigt unikt namn som ämne för SCEP-certifikatet <!--2221763 -->
När du skapar en profil för SCEP-certifikat, anger du certifikatets ämnesnamn. Med den här uppdateringen kan du använda det fullständiga unika namnet som ämne. För **Ämnesnamn** väljer du **Anpassad** och sedan `CN={{OnPrem_Distinguished_Name}}`. Om du vill använda variabeln `{{OnPrem_Distinguished_Name}}` måste du synkronisera användarattributet `onpremisesdistingishedname` med hjälp av [Azure Active Directory (AD) Anslut](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) till din Azure AD.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Aktivera kontaktdelning med Bluetooth – Android for Work <!--1098983 -->
Som standard förhindrar Android att kontakter i arbetsprofilen synkroniseras med Bluetooth-enheter. Därför visas inte arbetsprofilkontakter i uppringarens ID för Bluetooth-enheter.

I och med uppdateringen finns en ny inställning i **Android for Work** > **Enhetsbegränsningar** > **Arbetsprofilinställningar**:
- Dela kontakter via Bluetooth

Intune-administratören kan konfigurera dessa inställningar för att aktivera delning. Detta är användbart när du parar ihop en enhet med en bilbaserad Bluetooth-enhet som visar uppringarens ID vid handsfree-användning. När den är aktiverad visas arbetsprofilens kontakter. När den är inaktiverad visas inte arbetsprofilens kontakter.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Konfigurera Gatekeeper till att styra macOS-appens nedladdningskälla <!-- 1690459 -->

Du kan konfigurera Gatekeeper till att skydda dina enheter från appar genom att styra var apparna kan laddas ned från. Du kan konfigurera följande nedladdningskällor: **Mac App Store**, **Mac App Store och identifierade utvecklare**, eller **Valfri plats**. Du kan även konfigurera om användarna ska kunna installera en app med CTRL-klick för att åsidosätta dessa Gatekeeper-kontroller.

Inställningarna finns i **Enhetskonfiguration** -> **Skapa profil** -> **macOS** -> **Slutpunktsskydd**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Konfigurera brandväggen för Mac-program <!-- 1690461 -->

Du kan konfigurera brandväggen för Mac-program. Du kan använda den för att styra anslutningar per program i stället för per port. Det gör det lättare att utnyttja brandväggsskyddet och förhindrar att oönskade appar tar kontroll över nätverksportar som är öppna för legitima appar.

Den här funktionen finns i **Enhetskonfiguration** -> **Skapa profil** -> **macOS** -> **Slutpunktsskydd**.

När du har aktiverat brandväggsinställningen kan du konfigurera brandväggen med hjälp av två olika metoder:

- Blockera alla inkommande anslutningar

   Du kan blockera alla inkommande anslutningar för de aktuella enheterna. Om du väljer att göra detta blockeras inkommande anslutningar för alla appar.

- Tillåta eller blockera specifika appar

   Du kan tillåta eller blockera specifika appar från att ta emot inkommande anslutningar. Du kan också aktivera hemligt läge för att förhindra svar på avsökningsbegäranden.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>Detaljerade felkoder och meddelanden <!-- 1376342 -->

I din enhetskonfiguration finns mer detaljerade felkoder och felmeddelanden. Den här förbättrade rapporteringen visar inställningarna, status för dessa inställningar och information om felsökning.

##### <a name="more-information"></a>Mer information

- Blockera alla inkommande anslutningar

   Detta hindrar alla delade tjänster (till exempel fildelning och delning av skärmen) från att ta emot inkommande anslutningar. Systemtjänster som fortfarande kan ta emot inkommande anslutningar är:
  - configd – Implementerar DHCP- och andra tjänster för nätverkskonfiguration
  - mDNSResponder – Implementerar Bonjour
  - racoon – Implementerar IPSec

    Om du vill använda delade tjänster kontrollerar du att **Inkommande anslutningar** är inställd på **Inte konfigurerad** (inte **Blockera**).

- Hemligt läge

   Aktivera detta om du vill förhindra att datorn svarar på avsökningsbegäranden. Datorn svarar fortfarande på inkommande begäranden för behöriga appar. Oväntade begäranden, till exempel ICMP (ping) ignoreras.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Inaktivera kontroller vid omstart av enheten <!--1805490 -->
Med Intune får du kontroller för att [hantera programuppdateringar]](windows-update-for-business-configure.md). Med den här uppdateringen är egenskapen <strong>Omstartskontroller</strong> tillgänglig och aktiverad som standard. Om du vill hoppa över de vanliga kontroller som utförs när du startar om en enhet (till exempel aktiva användare, batterinivå och så vidare) väljer du <strong>Hoppa över</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Nya Windows 10 Insider Preview-kanaler är tillgängliga för testgrupper för distribution <!-- 1746293 -->
Nu kan du välja följande Windows 10 Insider Preview-underhållskanaler när du skapar en Windows 10-testgrupp för distribution:
- Windows Insider-version &#8208; snabb
- Windows Insider-version &#8208; långsam
- Windows Insider-slutversion 

Mer information om dessa kanaler finns [Manage Insider Preview Builds](https://insider.windows.com/en-us/for-business-organization-admin/) (Hantera Insider Preview-versioner).   
Mer information om hur du skapar distributionskanaler i Intune finns i [Hantera programuppdateringar](windows-update-for-business-configure.md).

### <a name="intune-apps"></a>Intune-appar

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Registreringen av företagsportalen har förbättrats <!-- 1874230 eeready-->
Användare som registrerar en enhet med hjälp av företagsportalen i Windows 10 version 1703 och senare, kan slutföra det första steget i registreringen utan att lämna appen.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens och Surface Hub visas nu i enhetslistor <!--1725868 -->
Vi har lagt till stöd för att visa Intune-registrerade HoloLens- och Surface Hub-enheter i företagsportalappen för Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Anpassade bokkategorier för volyminköpsprogram för e-böcker. <!-- 1488911 -->
Du kan skapa anpassade e-bokkategorier och sedan tilldela e-böcker i volyminköpsprogram till dessa anpassade e-bokkategorier. Slutanvändarna kan sedan se de nyligen skapade e-bokkategorierna och böcker som tilldelats i kategorierna. Mer information finns i [Hantera volyminköpta appar och böcker med Microsoft Intune](vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Alternativet skicka feedback som stöd för ändringar i företagsportalappen för Windows <!-- 2070166 -->
Med start den 30 april 2018, kommer alternativet **Skicka feedback** i företagsportalappen för Windows bara att fungera på enheter som kör Windows 10 Anniversary-uppdateringen (1607) och senare. Alternativet att skicka feedback stöds inte längre när du använder företagsportalappen för Windows med:  
- Windows 10, version 1507  
- Windows 10, version 1511  
- Windows Phone 8.1 

Om enheten körs på Windows 10 RS1 eller senare, kan du hämta den senaste versionen av Windows-företagsportalappen från Store. Om du kör en version som inte stöds, fortsätt att skicka feedback via följande kanaler: 
- Feedbackhubben i Windows 10
- E-post WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nya Windows Defender Application Guard-inställningar <!-- 1631890 -->

- **Aktivera grafikacceleration**: Administratörer kan aktivera en virtuell grafikprocessor för Windows Defender Application Guard. Med den här inställningen kan processorn avlasta grafikåtergivning till vGPU. Detta kan förbättra prestanda när du arbetar med grafikintensiva webbplatser eller tittar på videor inuti containern.

- **SaveFilestoHost**: Administratörer kan aktivera att filer kan skickas från Microsoft Edge som körs i containern till värdfilsystemet. Det gör att användare kan ladda ned filer från Microsoft Edge i containern till värdfilsystemet.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>MAM-skyddsprinciper riktas utifrån hanteringsstatus <!-- 1665993 -->
Du kan rikta MAM-principer baserat på hanteringsstatus för enheten:
- **Android-enheter** – Du kan ange ohanterade enheter, Intune-hanterade enheter och Intune-hanterade Android Enterprise-profiler (tidigare Android for Work) som mål.
- **iOS-enheter** – Du kan ange ohanterade enheter (endast MAM) eller Intune-hanterade enheter som mål.

    > [!NOTE]
    > - iOS-stöd för den här funktionen införs i april 2018.

Mer information finns i [Target app protection policies based on device management state](app-protection-policies.md) (Ange mål för appskyddsprinciper utifrån enhetens hanteringsstatus).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Förbättringar av språket i företagsportalappen för Windows <!-- 1683758 -->
Vi har förbättrat språket i företagsportalen för att Windows 10 ska vara mer användarvänlig och specifik för ditt företag. Du kan se några bildexempel på sidan om [nyheter i appens gränssnitt](whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Nya tillägg till vår dokumentation om användarsekretess <!-- 1440709 -->
Som en del i vårt arbete att ge användarna mer kontroll över sina data och sin sekretess har vi publicerat uppdateringar i vår dokumentation som förklarar hur du visar och tar bort data som lagras lokalt av företagsportalappar. Du hittar uppdateringarna på:

- **Android**: [Så här avregistrerar du en Android-enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, om användaren har avböjt användningsvillkoren** : [Ta bort enhetshantering om du har avböjt användningsvillkoren](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**: [Ta bort en iOS-enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**: [Ta bort en Windows-enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>Veckan som börjar med 19 mars 2018

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Exportera alla enheter till CSV-filer i Internet Explorer, Edge eller Chrome <!-- 2258071 -->
I **Enheter** > **Alla enheter** kan du **exportera** enheterna till en CSV-formaterad lista. Internet Explorer-användare med fler än 10 000 enheter kan exportera enheterna till flera filer. Varje fil kan ha upp till 10 000 enheter.

Edge- och Chrome-användare med fler än 30 000 enheter kan exportera enheterna till flera filer. Varje fil kan ha upp till 30 000 enheter.

I [Hantera enheter](device-management.md) finns mer information om vad du kan göra med de enheter som du hanterar.

## <a name="week-of-march-12-2018"></a>Vecka 12 i mars 2018

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-webbplatser kan kräva appen Intune Managed Browser och ha stöd för enkel inloggning för Managed Browser (allmänt tillgänglig förhandsversion) <!-- 710595 -->

Med Azure Active Directory (Azure AD) kan du nu begränsa åtkomsten till webbplatser på mobila enheter till appen Intune Managed Browser. I Managed Browser förblir webbplatsdata säkra och separata från slutanvändarens personliga data. Dessutom stöder Managed Browser funktioner för enkel inloggning för webbplatser som stöds av Azure AD. När du loggar in på Managed Browser eller använder Managed Browser på en enhet med en annan app som hanteras av Intune, tillåts Managed Browser att få åtkomst till företagswebbplatser som skyddas av Azure AD utan att användaren måste ange sina autentiseringsuppgifter. Den här funktionen gäller för webbplatser som Outlook Web Access (OWA) och SharePoint Online, samt andra företags webbplatser som resurser i intranätet som nås via Azure App Proxy. Mer information finns i avsnittet om [åtkomstkontroller för villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Visuella uppdateringar i företagsportalappen för Android <!--976944 -->

Vi har uppdaterat företagsportalappen för Android så att den följer Androids riktlinjer för [Materialdesign](https://material.io/). Du kan se bilder av de nya ikonerna i artikeln [Nyheter i appens gränssnitt](whats-new-app-ui.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Nya inställningar för Windows Defender Exploit Guard-princip <!-- 1631893 -->

Sex nya inställningar för <strong>minskning av attackytan</strong> och utökade funktioner för <strong>Reglerad mappåtkomst: Mappskydd</strong> är nu tillgängliga. Inställningarna finns här: Device configuration\Profiles\
Create profile\Endpoint protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Minska attackytan

|Inställningsnamn  |Inställningsalternativ  |Description  |
|---------|---------|---------|
|Avancerat skydd för utpressningstrojan|Aktiverad, granskad, inte konfigurerad|Använd aggressivt skydd mot utpressningstrojan.|
|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem|Aktiverad, granskad, inte konfigurerad|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem (lsass.exe).|
|Skapa process från PSExec- och WMI-kommandon|Blockera, Granska, Inte konfigurerat|Blockera skapande av processer från PSExec- och WMI-kommandon.|
|Obetrodda och osignerade processer som körs via USB|Blockera, Granska, Inte konfigurerat|Blockera obetrodda och osignerade processer som körs via USB.|
|Körbara filer som inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista|Blockera, Granska, Inte konfigurerat|Blockera körbara filer från att köras om de inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista.|

#### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

|              Inställningsnamn               |                                                              Inställningsalternativ                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Mappskydd (redan implementerat) | Inte konfigurerad, Aktivera, Endast granskning (redan implementerat)<br><br> <strong>Nytt</strong><br>Blockera diskändring, Granska diskändring |             |

Skydda filer och mappar från obehöriga ändringar av oönskade appar.<br><br>**Aktivera**: Förhindra att obetrodda appar ändrar eller tar bort filer i skyddade mappar och skriver till disksektorer.<br><br>
**Blockera endast diskändring**:<br>Blockera obetrodda appar från att skriva till disksektorer. Obetrodda appar kan fortfarande ändra eller ta bort filer i skyddade mappar.|

## <a name="week-of-february-19-2018"></a>Veckan för 19 februari 2018

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-stöd för flera Apple DEP/Apple School Manager-konton<!-- 747685 -->

Intune stöder nu registrering av enheter från upp till 100 olika [Apple-program för enhetsregistrering (DEP)](device-enrollment-program-enroll-ios.md) eller [Apple School Manager](apple-school-manager-set-up-ios.md)-konton. Varje token som har överförts kan hanteras separat för registreringsprofiler och- enheter. En annan profil kan tilldelas automatiskt per DEP/School Manager-token som har överförts. Om flera School Manager-token har överförs, kan bara en åt gången delas med Microsoft School-datasynkronisering.

Efter migreringen fungerar inte beta-Graph API:er och publicerade skript för att hantera Apple DEP eller ASM över Graph längre. Nya beta-Graph API:er är under utveckling och kommer att släppas efter migreringen.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Visa registreringsbegränsningar per användare <!-- 1634444 eeready wnready -->
På bladet **Felsök** kan du nu se de [registreringsbegränsningar](enrollment-restrictions-set.md) som gäller för varje användare genom att välja **Registreringsbegränsningar** i listan **Tilldelningar**.

### <a name="device-management"></a>Enhetshantering
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Stöd för hälsostatus och hotstatusrapporter i Windows Defender<!--854704 -->

Det är viktigt att förstå Windows Defenders hälsa och status för att hantera Windows-datorer.  Med denna uppdatering lägger Intune till nya rapporter och åtgärder till Windows Defender-agentens status och hälsa. Med hjälp av en statussammanfattningsrapport i [arbetsbelastningen för enhetsefterlevnad](compliance-policy-monitor.md) kan du se de enheter som behöver något av följande:
- signaturuppdatering
- Starta om
- manuella åtgärder
- fullständig genomsökning
- övriga agenttillstånd som kräver åtgärder

En detaljerad rapport för varje statuskategori visar de enskilda datorer som behöver åtgärdas eller vilka som rapporteras som **Rengör**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nya inställningar för enhetsbegränsningar <!--1308926 -->
[Två nya sekretessinställningar](device-restrictions-windows-10.md#privacy) är nu tillgängliga för enheter:
- **Publicera användaraktiviteter**: Ställ in den här på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen.
- **Endast lokala aktiviteter**: Ställ in det här alternativet på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen baserat på lokala aktiviteter.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nya inställningar för Microsoft Edge-webbläsaren <!--1469166 -->
[Två nya inställningar](device-restrictions-windows-10.md#edge-browser) är nu tillgängliga för enheter med Microsoft Edge-webbläsaren: **Sökväg till favoritfil** och **Ändringar i favoriter**.

### <a name="app-management"></a>Apphantering
#### <a name="protocol-exceptions-for-applications---1035509---"></a>Protokollundantag för program<!--1035509 -->

Du kan nu skapa undantag till principen för MAM-dataöverföring (Mobile Application Management) i Intune för att kunna öppna vissa ohanterade program. Sådana program måste vara betrodda av IT-avdelningen. Utöver de undantag som du skapar är dataöverföringen ändå begränsad till program som hanteras av Intune när din dataöverföringsprincip är inställd på **Endast hanterade appar**. Du kan skapa begränsningarna med protokoll (iOS) eller paket (Android).

Du kan exempelvis lägga till Webex-paketet som ett undantag till MAM-dataöverföringsprincipen. Det innebär att Webex-länkar i ett hanterat e-postmeddelande i Outlook kan öppnas direkt i Webex-programmet. Dataöverföringen är fortfarande begränsad i andra ohanterade program. Mer information finns i [Undantag för dataöverföringsprinciper i appar](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows Information Protection (PIA)-krypterad data i Windows-sökresultat <!-- 1469193 -->
En inställning i principen för Windows informationsskydd innebär att du nu kan kontrollera om krypterade data i Windows informationsskydd ingår i Windows-sökresultaten. Ange den här appens skyddsprincipalternativ genom att välja **Tillåt att Windows Search-indexeraren söker efter krypterade objekt**  i **Avancerade inställningar** för Windows informationsskyddsprincip. Appens skyddsprincip måste anges för *Windows 10*-plattformen och apprincipen **Registreringsstatus** måste anges som **Med registrering**. Mer information finns i [Tillåt att Windows Search-indexeraren söker efter krypterade objekt](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Konfigurera en MSI-mobilapp med automatisk uppdatering<!-- 1740840 -->
Du kan konfigurera att en känd MSI-mobilapp med automatisk uppdatering ignorerar versionskontrollen. Den här funktionen är användbar för att undvika konkurrenstillstånd. Den här typen av konkurrenstillstånd kan exempelvis uppstå när appen uppdateras automatiskt av apputvecklaren och även uppdateras av Intune. Båda två kan försöka framtvinga en version av appen på Windows-klienten, vilket kan skapa en konflikt. För dessa automatiskt uppdaterade MSI-appar kan du konfigurera inställningen **Ignore app version** (Ignorera appversion) på bladet **Appinformation**. När den här inställningen växlas till **Ja** kommer Microsoft Intune ignorera den appversion som är installerad på Windows-klienten.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Relaterade uppsättningar applicenser som stöds i Intune <!-- 1864117 -->
Intune i Azure-portalen stöder nu relaterade uppsättningar med applicenser som ett enskilt appobjekt i användargränssnittet. Dessutom konsolideras alla offlinelicensierade appar från Microsoft Store för företag till en enda appinmatning och eventuella distributionsuppgifter från de enskilda paketen migreras över till den enda inmatningen. Om du vill se relaterade uppsättningar applicenser i Azure-portalen väljer du **Applicenser** på bladet **Klientappar**.

### <a name="device-configuration"></a>Enhetskonfiguration
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Filnamnstillägg i Windows informationsskydd för automatisk kryptering <!-- 1463582 -->
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


|Inställningsnamn  |Inställningsalternativ  |Description  |
|---------|---------|---------|
|Körning av lösenordsskyddat körbart innehåll från e-post|Blockera, Granska, Inte konfigurerat|Förhindra körning av körbara filer som skyddas av lösenord och som hämtats via e-post.|
|Avancerat skydd för utpressningstrojan|Aktiverad, granskad, inte konfigurerad|Använd aggressivt skydd mot utpressningstrojan.|
|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem|Aktiverad, granskad, inte konfigurerad|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem (lsass.exe).|
|Skapa process från PSExec- och WMI-kommandon|Blockera, Granska, Inte konfigurerat|Blockera skapande av processer från PSExec- och WMI-kommandon.|
|Obetrodda och osignerade processer som körs via USB|Blockera, Granska, Inte konfigurerat|Blockera obetrodda och osignerade processer som körs via USB.|
|Körbara filer som inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista|Blockera, Granska, Inte konfigurerat|Blockera körbara filer från att köras om de inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista.|

##### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

|              Inställningsnamn               |                                                              Inställningsalternativ                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Mappskydd (redan implementerat) | Inte konfigurerad, Aktivera, Endast granskning (redan implementerat)<br><br> <strong>Nytt</strong><br>Blockera diskändring, Granska diskändring |             |

Skydda filer och mappar från obehöriga ändringar av oönskade appar.<br><br>**Aktivera**: Förhindra att obetrodda appar ändrar eller tar bort filer i skyddade mappar och skriver till disksektorer.<br><br>
**Blockera endast diskändring**:<br>Blockera obetrodda appar från att skriva till disksektorer. Obetrodda appar kan fortfarande ändra eller ta bort filer i skyddade mappar.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Tillägg till efterlevnadsprinciper för inställningar för systemsäkerhet för Windows 10 och senare <!--1704133-->

Tillägg till efterlevnadsinställningar för Windows 10 är nu tillgängliga, däribland krav på brandvägg och Windows Defender Antivirus.


### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll
### <a name="intune-apps"></a>Intune-appar
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Stöd för offline-appar från Microsoft Store för företag <!--1222672-->
Offline-appar som du har köpt från Microsoft Store för företag synkroniseras nu med Azure-portalen. Du kan distribuera apparna till enhetsgrupper eller användargrupper. Offline-appar installeras av Intune och inte av butiken.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Förhindra slutanvändare från att lägga till eller ta bort konton manuellt i arbetsprofilen <!-- 1728700 -->

När du distribuerar Gmail-appen till en Android for Work-profil kan du nu förhindra att användare lägger till eller tar bort konton i arbetsprofilen manuellt genom att använda inställningen **Lägg till och ta bort konton** i profilen för enhetsbegränsningar i Android for Work.

## <a name="week-of-february-5-2018"></a>Veckan för 5 februari 2018

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nya alternativ för användarautentisering för Apple-massregistrering <!-- 747625 eeready -->

> [!NOTE]
> Nya klienter ser det här direkt. Den här funktionen distribueras under april för befintliga klienter. Du kanske inte har åtkomst till de här nya funktionerna förrän den här distributionen är slutförd.

Intune ger dig nu möjlighet att autentisera enheter med hjälp av företagsportalappen för följande registreringsmetoder:

- Apples DEP (Device Enrollment Program)
- Apple School Manager
- Registrera Apple Configurator

När du använder alternativet Företagsportalen, kan Azure Active Directory-multifaktorautentisering tillämpas utan att blockera dessa registreringsmetoder.

När du använder alternativet Företagsportalen, hoppar Intune över användarautentisering i iOS-installationsassistenten för registrering av användartillhörighet. Detta innebär att enheten först registreras som en användarlös enhet och därför inte tar emot konfigurationer eller principer från användargrupper. Den tar bara emot konfigurationer och principer för enhetsgrupper. Intune kommer dock automatiskt att installera företagsportalappen på enheten. Den första användaren som startar och loggar in på företagsportalappen kommer att associeras med enheten i Intune. Användaren får då konfigurationer och principer för sina användargrupper. Användarassociationen kan inte ändras utan omregistrering.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Intune-stöd för flera Apple DEP/Apple School Manager-konton<!-- 747685 eeready -->

Intune stöder nu registrering av enheter från upp till 100 olika Apple-program för enhetsregistrering (DEP) eller Apple School Manager-konton. Varje token som har överförts kan hanteras separat för registreringsprofiler och- enheter. En annan profil kan tilldelas automatiskt per DEP/School Manager-token som har överförts. Om flera School Manager-token har överförs, kan bara en åt gången delas med Microsoft School-datasynkronisering.

Efter migreringen fungerar inte beta-Graph API:er och publicerade skript för att hantera Apple DEP eller ASM över Graph längre. Nya beta-Graph API:er är under utveckling och kommer att släppas efter migreringen.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Fjärrutskrift via ett säkert nätverk <!-- 1709994  -->
PrinterOn:s trådlösa mobila lösningar gör att användare via fjärranslutning kan skriva ut var och när som helst via ett säkert nätverk. PrinterOn kan integreras med Intune APP SDK för både iOS och Android. Du kommer att kunna ange mål för appskyddsprinciper för den här appen via bladet Intune **Appskyddsprinciper** i administrationskonsolen. Användarna kommer att kunna ladda ner appen PrinterOn for Microsoft via Play Store eller iTunes för att använda i sina Intune-ekosystem.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Stöd för macOS-företagsportal för registreringar som använder Enhetsregistreringshanteraren <!-- 1352411 -->

Användarna kan nu använda enhetsregistreringshanteraren när de registrerar sig i macOS-företagsportalen.

## <a name="week-of-january-29-2018"></a>Veckan som börjar med 29 januari 2018

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Aviseringar om att token har upphört att gälla och om att token snart upphör att gälla <!-- 1639263 -->
På översiktssidan visas nu aviseringar om att token har upphört att gälla och om att token snart upphör att gälla. När du klickar på en avisering för en enskild token fortsätter du till denna tokens informationssida.  Om du klickar på avisering för flera token kommer du till en lista över alla token med deras status. Administratörer bör förnya sina tokens innan förfallodatumet.

### <a name="device-management"></a>Enhetshantering

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Stöd för fjärråtkomst till kommandot ”Radera” för macOS-enheter <!-- 1438084 -->

Administratörer kan utfärda ett Radera-kommando via fjärranslutning för macOS-enheter.

> [!IMPORTANT]
> Raderingskommandot kan inte ångras och bör användas med försiktighet.

Raderingskommandot tar bort alla data, inklusive operativsystemet från en enhet. Det tar också bort enheten från Intune-hantering. Ingen varning utfärdas till användaren och raderingen sker omedelbart efter kommandot.

Du måste konfigurera en 6-siffrig PIN-kod för återställning. Den här PIN-kod kan användas för att låsa upp enheten som raderats, då ominstallation av operativsystemet börjar. När raderingen har startats visas PIN-koden i ett statusfält på enhetens översiktsblad i Intune. PIN-koden kommer att finnas kvar så länge raderingen pågår. När raderingen är klar försvinner enheten helt från Intune-hanteringen. Tänk på att notera PIN-koden så att den som återställer enheten kan använda den.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Återkalla licenser för en token för iOS-volyminköpsprogram <!-- 820870 -->
Du kan återkalla licensen för alla iOS-appar för volyminköpsprogram (VPP) för en given VPP-Token.

### <a name="app-management"></a>Apphantering

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Återkallande av iOS-appar från volyminköpsprogram  <!-- 820863 -->
Du kan återkalla associerade enhetsbaserade applicenser för enheten för en given enhet som har en eller flera iOS-appar för volyminköpsprogram (VPP). Om du återkallar en applicens så avinstalleras inte den relaterade VPP-appen från enheten. Om du vill avinstallera en VPP-app, måste du ändra tilldelningsåtgärden till **avinstallera**. Mer information finns i [så här hanterar du iOS-appar som köpts genom ett volyminköpsprogram med Microsoft Intune](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Tilldela Office 365-mobilappar till iOS och Android-enheter med den inbyggda apptypen <!-- 1332318 -->
Den **inbyggda** apptypen gör det enklare att skapa och tilldela Office 365-appar till iOS- och Android-enheter som du hanterar. De här apparna inkluderar 365-appar som Word, Excel, PowerPoint och OneDrive. Du kan tilldela specifika appar till apptypen och redigera konfigurationen för appinformationen.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inklusive och exklusive apptilldelning baserat på grupperna <!-- 1406920 -->

Under apptilldelning och när du har valt en tilldelningstyp kan du välja de grupper som ska inkluderas, samt de grupper som ska undantas.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Du kan tilldela en programkonfigurationsprincip till grupper genom att inkludera och exkludera tilldelningar <!-- 1480316 -->

Du kan tilldela en programkonfigurationsprincip till en grupp användare och enheter genom att använda en kombination av tilldelningar som inkluderar och exkluderar. Tilldelningar kan väljas som ett anpassat urval av grupper eller som en virtuell grupp. En virtuell grupp kan inkludera **Alla användare**, **Alla enheter** eller **Alla användare + Alla enheter**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Stöd för uppgraderingsprincip i Windows 10-utgåvan <!-- 903672(archived), 1119689 -->  
Du kan skapa en uppgraderingsprincip för Windows 10-utgåvan som uppgraderar Windows 10-enheter till Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education och Windows 10 Professional Education N. Mer information om Windows 10-uppgraderingar finns i [Så här konfigurerar du Windows 10-uppgraderingar](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Principer för villkorlig åtkomst för Intune är endast tillgängliga från Azure Portal <!-- 1737088 1634311 -->

Från och med den här versionen måste du konfigurera och hantera dina principer för villkorlig åtkomst på [Azure Portal](https://portal.azure.com) från **Azure Active Directory** > **Villkorlig åtkomst**. Du kan även komma åt det här bladet från Intune på Azure Portal på **Intune** > **Villkorlig åtkomst**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Uppdateringar till efterlevnads-e-post <!--1637547 -->

När ett e-postmeddelande skickas för att rapportera om en inkompatibel enhet inkluderas även information om den inkompatibla enheten.


## <a name="week-of-january-22-2018"></a>Vecka 22 januari 2018

### <a name="intune-apps"></a>Intune-appar

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>En ny funktion för åtgärden ”Lös” för Android-enheter <!--1583480-->

Företagsportalappen för Android utökar ”Lös”-åtgärden för **Uppdatera enhetsinställningar** för att lösa [device encryption issues](/intune-user-help/encrypt-your-device-android) (problem med enhetskryptering).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Fjärrlås är tillgängligt i företagsportalappen för Windows 10 <!--676506-->
Slutanvändare kan nu fjärrlåsa sina enheter från företagsportalappen för Windows 10. Detta visas inte för den lokala enheten som används.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Enklare lösning av efterlevnadsproblem för företagsportalappen för Windows 10 <!--676546-->
Slutanvändare med Windows-enheter kan trycka på orsaken för bristande efterlevnad i företagsportalappen. Om möjligt kommer de då direkt till rätt plats i inställningsappen för att kunna åtgärda problemet.

## <a name="week-of-december-11-2017"></a>Veckan som börjar med 11 December 2017

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Ny inställning för automatisk omdistribution <!-- 1469168 -->
Inställningen **Automatisk omdistribution** låter användare med administrativ behörighet ta bort alla användardata och inställningar med hjälp av **Ctrl + Win + R** på enhetens låsskärm. Enheten omkonfigureras automatiskt och omregistreras för hantering. Den här inställningen finns under Windows 10 > Enhetsbegränsningar > Allmänt -> Automatisk omdistribution. Mer information finns i [Inställningar för begränsningar i Intune-enheter för Windows 10](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Stöd för ytterligare källutgåvor i Windows 10 med principen för versionsuppgradering<!-- 903672,  1119689 -->
Du kan nu använda uppgraderingsprincipen för Windows 10 för att uppgradera från ytterligare Windows 10-versioner (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud, o.s.v.). Innan den här versionen var de uppgraderingsvägar som stöddes för utgåvan mer begränsade. Du hittar mer information i [Så här konfigurerar du uppgraderingar av Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Profilinställningar för enhetskonfiguration för Nya Windows Defender Security Center (WDSC) <!-- 1335507 -->

Intune lägger till ett nytt avsnitt med profilinställningar för enhetskonfiguration under Endpoint Protection som heter **Windows Defender Security Center**. IT-administratörer kan konfigurera vilka pelare i Windows Defender Security Center-appen som slutanvändare kan komma åt. Om IT-administratör döljer en pelare i Windows Defender Security Center-appen, döljs alla meddelanden som rör den dolda pelare på användarens enhet.

Dessa är de pelare som administratörer kan dölja från profilinställningarna för enhetskonfiguration för Windows Defender Security Center:
- Skydd mot virus och hot
- Enhetsprestanda och hälsa
- Brandväggs- och nätverksskydd
- App- och webbläsarkontroll
- Familjealternativ

IT-administratörer kan också anpassa de meddelanden som användare tar emot. Du kan till exempel konfigurera om användarna får alla meddelanden som skapas av synliga pelare i WDSC, eller enbart viktiga meddelanden. Meddelanden som är mindre viktiga inkluderar periodiska sammanfattningar av Windows Defender Antivirus-aktivitet och meddelanden när genomsökningar har slutförts. Alla andra meddelanden anses viktiga. Dessutom kan du kan också anpassa själva meddelandeinnehållet, du kan till exempel ange IT-kontaktinformation att bädda in i meddelanden som visas på användarnas enheter.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Stöd för flera anslutningsappar för hantering av SCEP- och PFX-certifikat <!-- 1361755 -->

Kunder som använder den lokala NDES-anslutningsappen för att leverera certifikat till enheter kan nu konfigurera flera anslutningsappar i en enda klient.

Den här nya funktionen stöder följande scenarion:

- **Hög tillgänglighet**

Varje NDES-anslutningsapp tar emot certifikatbegäranden från Intune.  Om en NDES-anslutningsapp kopplas från, kan den andra anslutningsappen fortsätta att bearbeta begäranden.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Ämnesnamnet för kunden kan använda variabeln AAD_DEVICE_ID <!-- 1468599 -->

När du skapar en profil för SCEP-certifikatet i Intune kan du nu använda variabeln AAD_DEVICE_ID när du skapar det anpassade ämnesnamnet.   När certifikatet har begärts med hjälp av den här SCEP-profilen, ersätts variabeln med ADD-enhetens ID för den enhet som gör certifikatbegäran.


### <a name="device-management"></a>Enhetshantering

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Hantera Jamf-registrerade macOS-enheter med Intunes motor för enhetsefterlevnad <!-- 1592747 -->
Du kan nu använda Jamf statusinformation för macOS-enheter till Intune, som sedan utvärderar den för efterlevnad av de principer som definierats i Intune-konsolen. Baserat på enhetens efterlevnadsstatus samt andra villkor (till exempel plats, användarrisk osv.), framtvingar villkorsstyrd åtkomst efterlevnad för macOS-enheter som har åtkomst till molnet och lokala program som är anslutna till Azure AD, inklusive Office 365. Lär dig mer om att [ställa in Jamf-integration](conditional-access-integrate-jamf.md) och [tillämpa kompatibilitet för enheter som hanteras av Jamf](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Ny iOS-enhetsåtgärd   <!-- 1424701 -->

Du kan nu stänga av iOS 10.3-övervakade enheter. Den här åtgärden stänger av enheten omedelbart utan varning till slutanvändaren. Åtgärden **stäng ner (endast övervakat)** finns i enhetsegenskaperna när du väljer en enhet i arbetsbelastningen **enhet**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Tillåt inte ändringar av datum/tid för Samsung Knox-enheter<!-- 1468103 -->

Vi har lagt till en ny funktion som gör det möjligt att blockera datum- och tidändringar på Samsung Knox-enheter. Du hittar den i **Profiler för enhetskonfiguration** > **Enhetsbegränsningar (Android)** > **Allmänt**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Stöd för Surface Hub-resurskonto <!-- 1566442  -->

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

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Installera Office-appar på macOS-enheter<!-- 1494311 -->
Du kommer nu att kunna installera Office-appar på macOS-enheter. Den här nya apptypen låter dig installera Word, Excel, PowerPoint, Outlook och OneNote. De här apparna inkluderar även Microsoft AutoUpdater (MAU), för att hålla dina appar säkra och uppdaterade.

### <a name="app-management"></a>Apphantering

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Ta bort en iOS-token för volyminköpsprogram <!-- 820879 -->
Du kan ta bort token för iOS-volyminköpsprogram (VPP) med hjälp av konsolen. Detta kan vara nödvändigt när du har dubblettinstanser av en VPP-token.

### <a name="intune-apps"></a>Intune-appar


### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>En ny entitetssamling med namnet aktuell användare, är begränsad till aktuell aktiv användardata <!-- 1667026 -->

Entitetssamlingen **Användare** innehåller alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i ditt företag. En användare kan till exempel läggas till i Intune och sedan tas bort under den senaste månaden. Användaren är då inte tillgänglig vid tidpunkten för rapporten, men användaren och tillståndet finns i data. Du kan skapa en rapport som visar varaktigheten för användarens historiska förekomst i dina data.

Den nya entitetssamlingen **aktuell användare** innehåller däremot bara användare som inte har tagits bort. Entitetssamlingen **aktuell användare** innehåller bara användare som är aktiva för tillfället. Mer information om entitetssamlingen **aktuell användare** finns i [referens för den aktuella användarentiteten](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>Uppdaterade Graph API:er<!-- 1736360 -->

Vi har uppdaterat några av Graph API:erna för Intune i den här betaversionen. Kontrollera den månatliga [Ändringsloggen för Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog) för mer information.

## <a name="week-of-december-4-2017"></a>Veckan som börjar med 4 December 2017

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune har stöd för appar som nekats av Windows informationsskydd (WIP) <!-- 1479103 -->
Du kan ange nekade appar i Intune. Om en app nekas blockeras den från att komma åt företagsinformation. Detta är i praktiken motsatsen till listan över tillåtna appar. Mer information finns i [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Rekommenderad neka-lista för Windows Information Protection).



## <a name="notices"></a>Meddelanden

### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Vidta åtgärd: Uppdatera Android-lösenordsinställningarna för enhetsbegränsning och efterlevnadsprinciper i Intune
Intune kommer att ta bort den tillgängliga lösenordstypen ”Standard för enheten” för enheter med Android 4.4 eller senare. På grund av skillnader mellan Android-plattformar och enhetsstandarder behandlas principen ofta som valfri av enheten. Vi kommer att ta bort den här inställningen från användargränssnittet i en kommande version i syfte att undvika förvirring kring när inställningen genomdrivs i Android. 
#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
- Om din avsikt är att kräva ett lösenord på enheterna rekommenderar vi att du redigerar dina Android-plattformsprofiler och tydligt anger vilken lösenordstyp som krävs, istället för att använda ”Standard för enheten”.
- Om din avsikt är att låta användarna själva välja om de vill skapa ett lösenord väljer du knappen ”Inte konfigurerad”. Om inställningen fortfarande är konfigurerad när vi tar bort den från användargränssnittet uppmanas du att välja ett annat värde än ”Standard för enheten” nästa gång du redigerar profilen.
Vad kan jag göra för att förbereda mig för den här ändringen?
Granska lösenordsinställningarna för enhetsbegränsning och efterlevnadsprinciper för Android och Android enterprise. Du hittar dem under Systemsäkerhet för efterlevnadsprinciper och under antingen Enhetslösenord eller Arbetsprofilinställningar för enhetsbegränsningar. Under Ytterligare information finns en länk till mer information och skärmdumpar som visar var du gör de här inställningarna.
####<a name="additional-information"></a>Ytterligare information
https://aka.ms/PasswordSettings 

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>Planera för förändring: Change Password at Next Auth (Ändra lösenord vid nästa autentisering) har lagts till i Intune<!-- 1873216 -->
I och med lanseringen av tjänsten i september planerar Intune att integrera Apples nyligen utgivna inställning **Change Password at Next Auth** (Ändra lösenord vid nästa autentisering) för enheter som kör macOS versioner 10.13 och senare. Före den här inställningen kan MDM-leverantörer inte verifiera att enhetens lösenord har ändrats för att vara kompatibelt. Intunes principer för konfiguration och efterlevnad verifierar endast att ett enhetslösenord markeras som verifierat nästa gång det ändras. När den här nya Apple-funktionen läggs till får dina macOS-användare en begäran om att uppdatera sina lösenord även om lösenorden är kompatibla.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Detta påverkar miljöer med en macOS-princip som använder Intune eller hybrid-MDM. Nu när Apple har inställningen **Change Password at New Auth** (Ändra lösenord vid ny autentisering) kan Intune tvinga användare att uppdatera sina lösenord när en lösenordsprincip skickas. Om du blockerar företagsresurser tills enheten har markerats som kompatibel kan slutanvändarna blockeras från att komma åt företagsresurser som e-post och SharePoint-webbplatser tills de återställer sina lösenord. I framtiden kommer alla uppdateringar av principer för konfiguration och lösenordskompatibilitet tvinga användarna att uppdatera sina lösenord.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Kontakta supportavdelningen. Om du inte vill framtvinga den här macOS-enhetsprincipen rekommenderar vi att du tar bort tilldelningen av din befintliga macOS-princip eller tar bort den helt. Kundreferensinformation indikerar att de flesta kunder inte påverkas av den här ändringen. De flesta slutanvändare uppdaterar sina lösenord när de får en begäran om att registrera med ett lösenord eller återställa sitt lösenord för att fortsätta vara kompatibla.


### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september----2454656---"></a>Planera för förändring: Intune går över till iOS 10 och senare i september <!-- 2454656 -->
Apple förväntas släppa iOS 12 i september. Strax därefter går Intune, inklusive Intune-registreringen, företagsportalen och den hanterade webbläsaren, över till iOS 10 och senare.  

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?  
Office 365-mobilappar stöds på iOS 10 och senare, så du kanske redan har uppgraderat ditt operativsystem eller dina enheter. I så fall påverkas du inte av den här förändringen.  

Om du däremot har någon av enheterna som anges nedan, eller om du vill registrera någon av enheterna som anges nedan, bör du vara medveten om att de endast stöder iOS 9 och tidigare.  För att även fortsättningsvis ha åtkomst till Intune-företagsportalen måste du uppgradera dessa enheter innan september till enheter som stöder iOS 10 eller senare:  

* iPhone 4S  
* iPod Touch  
* iPad 2  
* iPad (tredje generationen)  
* iPad Mini (första generationen)  

Med början i juli får MDM-registrerade enheter med både iOS 9 och företagsportalen en uppmaning om att uppgradera operativsystemet eller enheten. Om du använder appskyddsprinciper kan du även konfigurera åtkomstinställningen ”Kräv lägsta iOS-operativsystem (endast varning)”.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?   
Sök efter enheter eller användare som påverkas i din organisation. I Intune på Azure Portal går du till Enheter > Alla enheter och filtrerar efter operativsystem.  Klicka på Kolumner för att visa information som exempelvis operativsystemversion. Uppmana dina användare att uppgradera sina enheter till en operativsystemversion som stöds innan september.  

### <a name="plan-for-change-intune-moving-to-tls-12"></a>Planera för förändring: Intune går över till TLS 1.2
Från och med 31 oktober 2018 kommer Intune att stödja version 1.2 av TLS-protokollet (Transport Layer Security) i syfte att tillhandahålla förstklassig kryptering, göra tjänsten säkrare som standard och anpassa den till andra Microsoft-tjänster som Microsoft Office 365. Office meddelade om den här ändringen i MC128929.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Från och med den 31 oktober 2018 stödjer Intune inte längre versionerna 1.0 och 1.1 av TLS-protokollet. Alla kombinationer av klient-server och webbläsare-server bör använda TLS-version 1.2 för att säkerställa problemfri anslutning till Intune. Observera att den här ändringen påverkar slutanvändarens enheter som inte längre stöds av Intune men fortfarande tar emot princip via Intune och inte kan använda TLS-version 1.2. Detta inkluderar enheter som kör Android 4.3 och tidigare. En lista över berörda enheter och webbläsare finns i Ytterligare information nedan.

Om det efter den 31 oktober 2018 uppstår ett problem som rör användning av en gammal TLS-version kommer du att behöva uppdatera till TLS 1.2 eller till en enhet som stödjer TLS 1.2 som en del av lösningen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Vi rekommenderar att du proaktivt ta bort TLS 1.0- och 1.1-beroenden i dina miljöer och inaktiverar TLS 1.0 och 1.1 på operativsystemnivån där det är möjligt. Börja planera din migrering till TLS 1.2 i dag. Läs supportblogginlägget nedan för att få en lista över enheter som inte stöds av Intune i dag men som kanske fortfarande tar emot princip och som inte kommer att kunna kommunicera via TLS-version 1.2. Du kan behöva meddela dessa slutanvändare om att de kommer att förlora åtkomst till företagets resurser.

**Ytterligare Information**: [Intune går över till TLS 1.2 för kryptering](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)


### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Planera för förändring: Ändra i stödet för Microsoft Intune App SDK för Cordova-pluginprogrammet
Microsoft avslutar stödet för [Microsoft Intune App SDK Cordova-pluginprogrammet](app-sdk-cordova.md) 1 maj 2018. Vi rekommenderar att du använder Intunes programhanteringsverktyg i stället, för att förbereda dina Cordova-baserade appar för hantering och tillgänglighet i Intune. När den här ändringen träder i kraft kommer Microsoft Intune APP SDK för Cordova-pluginprogrammet inte längre att hanteras eller bli uppdaterat. Utvecklare av program kommer inte att kunna använda det här pluginprogrammet. Intune planerar att fortsätta att tillhandahålla stöd för appar som utvecklats med Cordova. Alla appar som utvecklats med Microsoft Intune APP SDK för Cordova-pluginprogrammet får dock nedsatt funktionalitet i Intune. Efter att du omslutit en app med Intunes programhanteringsverktyg kan den distribueras till slutanvändare som normalt. För Cordova-baserade Android-appar som publiceras till Google Play-butiken:
- Slutanvändarna uppmanas att ange sina autentiseringsuppgifter för att ta emot Intune-principen vid första start.
- Appar som ska publiceras på appbutiken för Intune-användare, till exempel ”Contoso-appen för Intune”.

Mer information om programhanteringsverktyget finns i [Programhanteringsverktyget för iOS](app-wrapper-prepare-ios.md) och [Programhanteringsverktyget för Android](app-wrapper-prepare-android.md). Om du har problem eller frågor kan du kontakta [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com).

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Planera för förändring: Använd Intune på Azure för MDM-hanteringen <!-- 1227338 -->
För över ett år sedan tillkännagav vi en [allmänt tillgänglig förhandsversion av Intune på Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) och för sex månader sedan följde vi upp med [allmän tillgänglighet för den nya administratörsupplevelsen](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) för Intune. Från och med 31 augusti 2018 inaktiverar vi MDM (hantering av mobilenheter) i den klassiska Silverlight-konsolen för de kunder som använder fristående Intune. Du kan istället använda [Intune på Azure](https://aka.ms/Intune_on_Azure) för MDM-behoven. Om du fortfarande använder den klassiska konsolen för MDM rekommenderar vi att du ägnar en stund åt att bekanta dig med Intune på Azure. Vi förväntar oss inte att slutanvändarna ska påverkas av denna förändring. Klassisk datorhantering kommer att finnas kvar i Silverlight. Du kan läsa mer om den här förändringen och hur den påverkar dig [här](https://aka.ms/Intune_on_Azure_mdm).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->
För Intune-konton som skapades efter januari 2017 har Intune aktiverat direktåtkomst till registreringsscenarier i Apple med arbetsflödet Registrera enheter i Azure-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i den klassiska Intune-portalen. Intune-konton som skapades före januari 2017 måste migreras en gång innan dessa funktioner är tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto inte har åtkomst till Azure-portalen.

## <a name="whats-coming"></a>Kommande nyheter

### <a name="local-device-security-option-settings----1251887---"></a>Inställningar för säkerhetsalternativ för lokal enhet <!-- 1251887 -->
Du kan aktivera säkerhetsinställningarna på Windows 10-enheter med de nya inställningarna för säkerhetsalternativ för den lokala enheten. Inställningarna finns i kategorin Endpoint Protection när du skapar en princip för Windows 10-enhetskonfiguration.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>Ny uppdatering av användarupplevelse för företagsportalens webbsida <!--2000968-->

Vi presenterar en ny webbplats för företagsportalen i augusti, med uppdateringar av användargränssnittet, effektiva arbetsflöden och åtkomstförbättringar. Detta inkluderar kundefterfrågade förbättringar som appdelning och förbättrad övergripande prestanda för att få en mer användarvänlig upplevelse.
Vi har lagt till några nya funktioner, baserat på feedback från kunder som du, som förbättrar befintliga funktioner och användbarhet:

* Förbättringar i användargränssnittet på hela webbplatsen
* Möjlighet att dela direktlänkar till appar
* Förbättrad prestanda för stora app-kataloger

Du behöver inte göra några förberedelser inför den här ändringen. Vi meddelar dig när den uppdaterade webbplatsen för företagsportalen blir tillgänglig för dig. Du kan behöva uppdatera slutanvändardokument med uppdaterade skärmbilder. Observera att du också kan behöva uppdatera dokumentationen för företagsportalappen på iOS då webbplatsen startar avsnittet **Appar** i iOS-app. Du kan se en exempelbild för detta på sidan [vad är nytt i appens användargränssnitt](whats-new-app-ui.md).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->
Apple har tillkännagivit att de kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen. Vi lägger till information i [Intunes supportblogg](https://aka.ms/compportalats).



## <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/cloud-platform/roadmap)
* [Nyheter i företagsportalens gränssnitt](whats-new-app-ui.md)
* [Nyheter från föregående månad](whats-new-archive.md)
