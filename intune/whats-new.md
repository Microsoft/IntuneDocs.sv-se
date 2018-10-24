---
title: Nyheter i Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Ta reda på vad som är nytt i Intune Azure-portalen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 723e7584e1aaf22859b293a93ddbead56f6256e7
ms.sourcegitcommit: ca132d509e3c978d18e50eac89e1a1ed7ddb25c1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/08/2018
ms.locfileid: "48866447"
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

## <a name="week-of-october-1-2018"></a>Veckan då den 1 oktober 2018 infaller

### <a name="app-management"></a>Apphantering

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Åtkomst till användarkonto för Intune-appar på hanterade Android- och iOS-enheter <!-- 1248496 -->
Som Microsoft Intune-administratör kan du styra vilka användarkonton som läggs till i Microsoft Office-program på hanterade enheter. Du kan begränsa åtkomsten till endast tillåtna användarkonton i organisationen och blockera personliga konton på registrerade enheter. 

#### <a name="outlook-mobile-app-configuration-policy---1828527---"></a>Konfigurationsprincip för Outlook Mobile-appen <!--1828527 -->
Nu kan du skapa en konfigurationsprincip för Outlook Mobile-appar för iOS och Android. Ytterligare konfigurationsinställningar kommer att läggas till allteftersom de aktiveras för Outlook Mobile-appen.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Språkpaket för Office 365 Pro Plus <!-- 1833450 -->
Som Intune-administratör kan du distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Gå till Azure Portal och välj **Microsoft Intune** > **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** på bladet **Lägg till app** väljer du **Windows 10** under **Office 365 Suite**. Välj **Språk** på bladet **Inställningar för appsviten**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Filnamnstillägg för verksamhetsspecifika appar (LOB) för Windows <!-- 1884873 -->
Filnamnstillägg för LOB-appar på Windows omfattar nu *.msi*, *.appx*, *.appxbundle*, *.msix* och *.msixbundle*. Du kan lägga till en app i Microsoft Intune genom att välja **Klientappar** > **Appar** > **Lägg till**. Fönstret **Lägg till app** visas och där du kan välja **Apptyp**. För LOB-appar på Windows väljer du **Verksamhetsspecifik app** som apptyp, väljer **Appaketfil** och anger sedan en installationsfil med rätt filnamnstillägg.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Distribution av Windows 10-appar med Intune <!-- 2309001 -->
Genom att bygga vidare på det befintliga stödet för verksamhetsspecifika appar och appar för Microsoft Store för företag kan administratörer använda Intune för att distribuera de flesta av organisationens befintliga program till slutanvändare på Windows 10-enheter. Administratörer kan lägga till, installera och avinstallera program för Windows 10-användare i flera olika format, till exempel MSI, Setup.exe eller MSP. Intune utvärderar regler för krav innan nedladdningen och installationen, och meddelar slutanvändarna om statusen eller krav på omstart via Åtgärdscenter för Windows 10. Den här funktionen hjälper organisationer som vill flytta den här arbetsbelastningen till Intune och molnet. Den här funktionen är för närvarande tillgänglig som en offentlig förhandsversion. Vi planerar att introducera många nyheter i funktionen under de kommande månaderna. 


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Skapa DNS-suffix i VPN-konfigurationsprofiler på enheter som kör Windows 10<!-- 1333668 -->
När du skapar en profil för VPN-enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  plattform: **Windows 10 och senare** > profiltyp: **VPN**), anger du vissa DNS-inställningar. Med den här uppdateringen kan du även ange flera **DNS-suffix** i Intune. När du använder DNS-suffix, kan du söka efter en nätverksresurs med dess korta namn i stället för det fullständiga domännamnet (FQDN). I och med den här uppdateringen kan du ändra ordningen på DNS-suffix i Intune.
[Windows 10-VPN-inställningar](vpn-settings-windows-10.md#dns-settings) visar en lista över aktuella DNS-inställningar.
Gäller för: Windows 10-enheter

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Stöd för ständig VPN för Android-arbetsprofiler <!-- 1333705 -->
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

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Profilförbättringar för informationsdatorer med Windows 10 och senare i Azure Portal <!-- 2748224 -->
Den här uppdateringen innehåller följande förbättringar i konfigurationsprofilen för Windows 10-informationsenheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Helskärm (förhandsgranskning)** för profiltyp): 
- För närvarande kan du skapa flera informationsdatorprofiler på samma enhet. I och med den här uppdateringen stöder Intune endast en informationsdatorprofil per enhet. Om du fortfarande behöver flera informationsdatorprofiler på en enskild enhet kan du använda en anpassad URI.
- I en profil för **informationsdator med flera appar** kan du välja programikonernas storlek och ordning i **Startmenylayout** i programrutnätet. Om du vill anpassa mera, kan du ladda upp en XML-fil.
- Inställningarna för webbläsare för informationsdator flyttas till inställningarna för **Informationsdator**. För närvarande har inställningarna för **Webbläsare för informationsdator** sin egen kategori i Azure Portal.
Gäller: Windows 10 och senare




### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Använda Autopilot-profil för registrerade Windows 10-enheter som inte redan har registrerats för Autopilot <!-- 1558983 -->
Du kan använda Autopilot-profiler för registrerade Windows 10-enheter som inte redan har registrerats för Autopilot. I Autopilot-profilen väljer du alternativet **Omvandla alla målenheter till Autopilot** för att automatiskt registrera andra än Autopilot-enheter med Autopilot-distributionstjänsten. Det kan ta upp till 48 timmar för registreringen att bearbetas. Autopilot konfigurerar enheten efter att den har avregistrerats och återställts.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Skapa flera profiler för sidan för registreringsstatus och tilldela dem till Azure AD-grupper <!-- 2526564 -->
Nu kan du [skapa](windows-enrollment-status.md) flera profiler för sidan för registreringsstatus och tilldela dem till Azure AD-grupper.

### <a name="device-management"></a>Enhetshantering

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Begränsa appar och blockera åtkomsten till företagsresurser på Android-enheter <!-- 2451462  -->  
I **Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Android**  >  **Systemsäkerhet** finns det en ny inställning under avsnittet *Enhetssäkerhet* med namnet **Begränsade appar**. Inställningen **Begränsade appar** använder en efterlevnadsprincip för att blockera åtkomsten till företagsresurser om vissa appar installeras på enheten. Enheten betraktas som icke-kompatibel tills de begränsade apparna tas bort från enheten.
Gäller för: 
- Android




## <a name="week-of-september-24-2018"></a>Veckan då den 24 september 2018 infaller

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Administrationscenter för Microsoft 365-enhetshantering <!-- 3078424 -->
En av löftena för Microsoft 365 är förenklad administration och under åren har vi integrerat Microsoft 365-tjänsterna i serverdelen för att leverera scenarier från början till slut, till exempel Intune och Azure AD villkorsstyrd åtkomst. Den nya [Administrationscentret för Microsoft 365](http://devicemanagement.microsoft.com) låter dig konsolidera, förenkla och integrera administratörsupplevelsen. Specialist-arbetsytan för enhetshantering ger enkel åtkomst till all den enhets- och apphanteringsinformation och uppgifter som din organisation behöver. Vi förväntar oss att det här blir den primära molnarbetsytan för enterprise-slutanvändares databehandlingsteam.

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Stöd för fler tredjeparts certifikatutfärdare (CA) <!-- 3093107 -->
Genom att använda Simple Certificate Enrollment Protocol (SCEP) så kan du nu utfärda nya certifikat och förnya certifikat på mobila enheter med Windows, iOS, Android och macOS.

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune går över till stöd för iOS 10 och senare <!-- 2454656 -->  
Nu stöder Intune-registrering, företagsportalen och den hanterade webbläsaren endast iOS-enheter som kör iOS 10 och senare. Om du vill söka efter enheter eller användare som påverkas i din organisation går du till Intune på Azure-portalen > **Enheter** > **Alla enheter**. Filtrera efter operativsystem och klicka sedan på **Kolumner** för att visa information om operativsystemversionen. Be användarna att uppgradera sina enheter till en operativsystemversion som stöds.  

Om du har någon av enheterna som anges nedan, eller om du vill registrera någon av enheterna som anges nedan, bör du vara medveten om att de endast stöder iOS 9 och tidigare.  För att även fortsättningsvis ha åtkomst till Intune-företagsportalen måste du uppgradera dessa enheter till enheter som stöder iOS 10 eller senare:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (tredje generationen) 
* iPad Mini (första generationen)  

## <a name="week-of-september-17-2018"></a>Veckan då den 17 september 2018 infaller

### <a name="app-management"></a>Apphantering

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Ta bort duplicering av statuspaneler för appskydd <!-- 3083391 -->
Panelerna **användarstatus för iOS** och **användarstatus för Android** fanns både på sidan **Klientappar – översikt** samt sidan **Klientappar – Appskyddsstatus**. Statuspanelerna har tagits bort från sidan **Klientappar – översikt** för att undvika duplicering. 

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

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler är en tillgänglig anslutning för VPN-profiler i iOS <!-- 1769858 -->
När du skapar en VPN-profil för enhetskonfiguration i iOS (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS**-plattform > **VPN**-profiltyp) finns det flera anslutningstyper, inklusive Cisco, Citrix och mer. Den här uppdateringen lägger till Zscaler som anslutningstyp. 
[VPN-inställningar för enheter som kör iOS](vpn-settings-ios.md) visar en lista över tillgängliga anslutningstyper.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>FIPS-läge för företagets Wi-Fi-profiler för Windows 10 <!-- 1879077 -->
Du kan nu aktivera FIPS-läge (Federal Information Processing Standards) för företagets Wi-Fi-profiler för Windows 10 i Intune Azure-portalen. Se till att FIPS-läge är aktiverat i Wi-Fi-infrastrukturen om du aktiverar det i Wi-Fi-profilerna.
[Wi-Fi-inställningar för Windows 10 och senare enheter i Intune](wi-fi-settings-windows.md) visar hur du skapar en Wi-Fi-profil.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Kontrollera S-läge på Windows 10-enheter och senare enheter – förhandsversion <!-- 1958649 -->
Med den här funktionsuppdateringen kan du skapa en profil för enhetskonfiguration som växlar en Windows 10-enhet ut ur S-läge, eller förhindra att användare växlar enheten ut ur S-läge. Den här funktionen finns i Intune > **Enhetskonfiguration** > **Profiler** >  **Windows 10 och senare** > **Edition upgrade and mode switch** (Versionsuppgradering och lägesväxling).
[Introduktion till Windows 10 i S-läge](https://www.microsoft.com/windows/s-mode) innehåller mer information om S-läge.
Gäller för: senaste [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/)-version (medan förhandsversion används).


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Konfigurationspaketet för Windows Defender ATP läggs automatiskt till i konfigurationsprofilen <!-- 2144658 -->
När du använder enheter med [Advanced Threat Protection och registrering](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) i Intune behövde du tidigare ladda ned ett konfigurationspaket och lägga till det i din konfigurationsprofil. Med den här uppdateringen hämtar Intune paketet automatiskt från Windows Defender Säkerhetscenter och lägger till det i din profil.
Gäller för Windows 10 och senare.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Kräv att användare ansluter under enhetskonfiguration <!--2311457-->
Du kan nu ange enhetsprofiler som kräver att enheten ansluter till ett nätverk innan den går vidare förbi sidan Nätverk under Windows 10-installationen. När den här funktionen är i förhandsversion krävs Windows Insider-version 1809 eller senare för att använda den här inställningen.
Gäller för: senaste [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/)-version (medan förhandsversion används).


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
Gäller för: senaste [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/)-version (medan förhandsversion används).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Använda VPP enhetslicenser för att företablera företagsportalen vid DEP-registrering <!-- 1608345 -->
Nu kan du använda VPP-enhetslicenser (volyminköpsprogram) till att företablera företagsportalen under registreringar med Programmet för enhetsregistrering (DEP). Detta gör du genom att ange den VPP-token du vill använda för att installera företagsportalen när du [skapar eller redigerar en registreringsprofil](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Se till att din token inte upphör att gälla och att du har tillräckligt många licenser för företagsportalappen. Om token upphör att gälla eller om licenserna tar slut kan Intune push-överföra företagsportalen från App Store istället (då krävs ett Apple-ID).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Om du vill ta bort en VPP-token som används för företablering av företagsportalen krävs en bekräftelse <!-- 2237634 -->
En bekräftelse krävs nu för att ta bort en token för volymköpsprogram (VPP) om den används för att företablera företagsportalen vid DEP-registrering.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Blockera personliga enhetsregistreringar i Windows <!-- 1849498 -->
Du kan [blockera personliga Windows-enheter](enrollment-restrictions-set.md#set-device-type-restrictions) från att registrera med [hantering av mobilenheter](windows-enroll.md) i Intune. Enheter som registreras med [Intune PC-agenten](manage-windows-pcs-with-microsoft-intune.md) kan inte blockeras med den här funktionen. Den här funktionen tas i bruk inom de närmaste veckorna, så den syns kanske inte direkt i användargränssnittet.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Ange mönster för datornamn i en Autopilot-profil <!--1849855-->
Du kan [ange en mall för datornamn](enrollment-autopilot.md#create-an-autopilot-deployment-profile) för att generera och ange [datornamnet](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) under Autopilot-registreringen. Gäller för: senaste [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/)-version (medan förhandsversion används).


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>För Windows Autopilot-profiler döljer du alternativen för att ändra konto på företagets inloggningssida och sidan för domänfel <!--1901669 -->
Det finns [nya Windows Autopilot-profilalternativ](enrollment-autopilot.md#create-an-autopilot-deployment-profile) som administratörer kan använda för att dölja ändra alternativ för att ändra konto på företagets inloggningssida och sidorna för domänfel. För att dölja de här alternativen krävs att företagsanpassning konfigureras i Azure Active Directory. Gäller för: senaste [Windows Insider](https://docs.microsoft.com/en-us/windows-insider/at-work-pro/)-version (medan förhandsversion används).



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

#### <a name="scope-tags-for-policies---1081974---"></a>Omfångstaggar för principer <!--1081974 -->
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

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Helskärmsläge – inaktuell är nedtonad och kan inte ändras <!-- 2149998 -->
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

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Stöd för Palo Alto Networks GlobalProtect VPN-profiler <!-- 1333680 ! -->
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

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Ny språk-/regionsinställning när du konfigurerar OOBE för Autopilot <!-- 1821766 -->
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

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Avinstallera den senaste programuppdateringen för Windows 10 <!-- 1732948 -->
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

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>Enhetens profildiagram och statuslista visar alla enheter i en grupp <!-- 1449153 -->
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

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977---"></a>Blockera kamera och skärmbilder i Android for Work <!-- 1098977 -->
Två nya egenskaper kan blockeras när du konfigurerar enhetsbegränsningar för Android-enheter: 
- Kamera: Blockerar åtkomsten till alla kameror på enheten
- Skärmbild: Blockerar skärmbildtagning och förhindrar också att innehållet visas på enheter som inte har en säker videoutgång

Gäller Android for Work.


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nya registreringssteg för användarna på enheter med macOS High Sierra 10.13.2+ <!--1734567 -->
I macOS High Sierra 10.13.2 finns nu begreppet ”Användargodkänd” MDM-registrering. Godkända registreringar tillåter Intune att hanterar vissa säkerhetskänsliga inställningar. Mer information finns i Apples supportdokumentation här: https://support.apple.com/HT208019.

Enheter som registreras med macOS-företagsportalen betraktas som ”Inte användargodkända” tills användaren öppnar systeminställningarna och ger sitt manuella godkännande. Därför dirigerar macOS-företagsportalen nu användare av macOS 10.13.2 och senare till att manuellt godkänna registreringen i slutet av registreringsprocessen. Intune-administratörskonsolen rapporterar om en registrerad enhet är användargodkänd.



### <a name="device-management"></a>Enhetshantering

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>Advanced Threat Protection (ATP) och Intune är helt integrerade <!-- 1629303 -->

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

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Använda Cisco AnyConnect klienten för iOS <!-- 1333708 -->

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

## <a name="notices"></a>Meddelanden

### <a name="plan-for-change-intune-will-move-to-support-macos-1012-and-higher-in-december---2970975--"></a>Planera för förändring: Intune kommer att börja stödja macOS 10.12 och högre i December <!--2970975--> 

Apple har precis släppt macOS 10.14. Därmed kommer Intune att börja stödja macOS 10.12 och högre i December 2018. 

### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?

Från och med December kommer slutanvändare på enheter med macOS 10.11 och tidigare inte att kunna använda Företagsportalen för att registrera i Intune. De behöver uppgradera sin enhet till macOS 10.12 eller senare och uppgradera företagsportalappen till den senaste versionen för att fortsätta att få support och nya funktioner. 

macOS versioner 10.12 och högre stöds för närvarande på: 
- MacBook (sent 2009 eller nyare). 
- iMac (sent 2009 eller nyare)
- MacBook Air (sent 2010 eller nyare).  
- MacBook Pro (sent 2010 eller nyare). 
- Mac Mini (sent 2010 eller nyare). 
- Mac Pro (sent 2010 eller nyare). 

Efter December, kommer slutanvändare som har andra enheter än de som listas ovan inte komma åt den senaste versionen av företagsportalappen för macOS. Befintliga registrerade enheter som kör versioner som inte stöds tidigare än macOS 10.12 kommer fortsätta att hanteras och listas i Intune-administratörskonsolen.

### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?

Uppmana dina slutanvändare att uppgradera sina enheter till en operativsystemversion som stöds innan december 2018. 
- Kontrollera din Intune-rapportering i Intune på Azure-konsolen för att se vilka enheter eller användare som kan påverkas. Gå till Enheter > Alla enheter och filtrera efter operativsystem. Du kan lägga till fler kolumner för att hjälpa att identifiera vem i din organisation som har enheter som kör macOS 10.11. 
- Om du använder hantering av mobila hybridenheter (MDM), går du till Tillgångar och kompatibilitet > Enheter i Configuration Manager-konsolen, högerklickar på kolumnerna för att lägga till kolumnerna Operativsystem och Klientversion och sortera efter operativsystem. Observera att hybrid-MDM nu är inaktuellt och du flytta till Intune i Azure så snart som möjligt. 
 
Ytterligare information [https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp)
 

### <a name="plan-for-change-new-intune-support-experience-for-premier-customers"></a>Ändringsplan: Ny Intune-supportupplevelse för Premier-kunder 
Som Microsoft Premier-kund kan du för närvarande använda Microsoft Premier Online-portalen (MPO) (premier.microsoft.com) och Intune i Azure (portal.azure.com) för att skapa supportbegäranden för Intune. Som en del av förbättringen av Premier-supportupplevelsen, kommer du från och med 3 december 2018 att kunna skapa supportbegäranden endast i Intune i Azure.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Efter den 3 december kan du inte längre skapa supportbegäranden i MPO.  Om du försöker göra detta, visas ett meddelande (som inte kan stängas) om omdirigering till Intune i Azure. Här kan du skapa en supportbegäran som dirigeras till Intune-dedikerade Microsoft Support för felsökning och problemlösning. Supportbegäranden som har skapats i MPO-portalen kan inte granskas i Azure Portal, så du bör sluta skapa supportbegäranden i MPO.  

Om du använder hybridhantering av mobilenheter (hybrid-MDM) eller samhantering, kan du fortsätta att använda MPO för att skapa supportbegäranden för ConfigMgr och börja använda Azure Portal för att skapa supportbegäranden för Intune. Vi påminner att hybrid-MDM är inaktuell, och du bör planera att övergå till Intune i Azure så snart som möjligt. Mer information finns i Flytt från hybridhantering av mobilenheter till Intune i Azure.

Observera att endast användare med rollen Global administratör, Intune-tjänstadministratör och Tjänstsupportadministratör kan skapa supportbegäranden i Azure Portal.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
- Sluta använda MPO och börja använda Intune i Azure för att skapa och hantera alla dina Intune-supportbegäranden.  
- Meddela din supportavdelning och uppdatera dokumentation enligt behov.
- Om du har användare utan rollen Global administratör eller Intune-tjänstadministratör som för närvarande skapar supportärenden i MPO, tilldelar du dem rollen Tjänstsupportadministratör i Azure Active Directory så att de kan fortsätta att skapa supportbegäranden i Azure Portalen.
- Klicka på Ytterligare information för mer information och användbara länkar.

#### <a name="additional-information"></a>Ytterligare information
[https://aka.ms/IntuneSupport_MPO_to_Azure](https://aka.ms/IntuneSupport_MPO_to_Azure)

### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Vidta åtgärd: Uppdatera Android-lösenordsinställningarna för enhetsbegränsning och efterlevnadsprinciper i Intune
Intune kommer att ta bort den tillgängliga lösenordstypen ”Standard för enheten” för enheter med Android 4.4 eller senare. På grund av skillnader mellan Android-plattformar och enhetsstandarder behandlas principen ofta som valfri av enheten. Vi kommer att ta bort den här inställningen från användargränssnittet i en kommande version i syfte att undvika förvirring kring när inställningen genomdrivs i Android. 
#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
- Om din avsikt är att kräva ett lösenord på enheterna rekommenderar vi att du redigerar dina Android-plattformsprofiler och tydligt anger vilken lösenordstyp som krävs, istället för att använda ”Standard för enheten”.
- Om din avsikt är att låta användarna själva välja om de vill skapa ett lösenord väljer du knappen ”Inte konfigurerad”. Om inställningen fortfarande är konfigurerad när vi tar bort den från användargränssnittet uppmanas du att välja ett annat värde än ”Standard för enheten” nästa gång du redigerar profilen.
Vad kan jag göra för att förbereda mig för den här ändringen?
Granska lösenordsinställningarna för enhetsbegränsning och efterlevnadsprinciper för Android och Android enterprise. Du hittar dem under Systemsäkerhet för efterlevnadsprinciper och under antingen Enhetslösenord eller Arbetsprofilinställningar för enhetsbegränsningar. Under Ytterligare information finns en länk till mer information och skärmdumpar som visar var du gör de här inställningarna.
#### <a name="additional-information"></a>Ytterligare information
https://aka.ms/PasswordSettings 

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>Planera för förändring: Change Password at Next Auth (Ändra lösenord vid nästa autentisering) har lagts till i Intune<!-- 1873216 -->
I och med lanseringen av tjänsten i september planerar Intune att integrera Apples nyligen utgivna inställning **Change Password at Next Auth** (Ändra lösenord vid nästa autentisering) för enheter som kör macOS versioner 10.13 och senare. Före den här inställningen kan MDM-leverantörer inte verifiera att enhetens lösenord har ändrats för att vara kompatibelt. Intunes principer för konfiguration och efterlevnad verifierar endast att ett enhetslösenord markeras som verifierat nästa gång det ändras. När den här nya Apple-funktionen läggs till får dina macOS-användare en begäran om att uppdatera sina lösenord även om lösenorden är kompatibla.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Detta påverkar miljöer med en macOS-princip som använder Intune eller hybrid-MDM. Nu när Apple har inställningen **Change Password at New Auth** (Ändra lösenord vid ny autentisering) kan Intune tvinga användare att uppdatera sina lösenord när en lösenordsprincip skickas. Om du blockerar företagsresurser tills enheten har markerats som kompatibel kan slutanvändarna blockeras från att komma åt företagsresurser som e-post och SharePoint-webbplatser tills de återställer sina lösenord. I framtiden kommer alla uppdateringar av principer för konfiguration och lösenordskompatibilitet tvinga användarna att uppdatera sina lösenord.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Kontakta supportavdelningen. Om du inte vill framtvinga den här macOS-enhetsprincipen rekommenderar vi att du tar bort tilldelningen av din befintliga macOS-princip eller tar bort den helt. Kundreferensinformation indikerar att de flesta kunder inte påverkas av den här ändringen. De flesta slutanvändare uppdaterar sina lösenord när de får en begäran om att registrera med ett lösenord eller återställa sitt lösenord för att fortsätta vara kompatibla.

### <a name="plan-for-change-intune-moving-to-tls-12"></a>Planera för förändring: Intune går över till TLS 1.2
Från och med 31 oktober 2018 kommer Intune att stödja version 1.2 av TLS-protokollet (Transport Layer Security) i syfte att tillhandahålla förstklassig kryptering, göra tjänsten säkrare som standard och anpassa den till andra Microsoft-tjänster som Microsoft Office 365. Office meddelade om den här ändringen i MC128929.

Företagsportalen kommer också att börja stödja TLS 1.2 den 31 oktober 2018.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Från och med den 31 oktober 2018 stödjer Intune inte längre versionerna 1.0 och 1.1 av TLS-protokollet. Alla kombinationer av klient-server och webbläsare-server bör använda TLS-version 1.2 för att säkerställa problemfri anslutning till Intune. Observera att den här ändringen påverkar slutanvändarens enheter som inte längre stöds av Intune men fortfarande tar emot princip via Intune och inte kan använda TLS-version 1.2. Detta inkluderar enheter som kör Android 4.3 och tidigare. En lista över berörda enheter och webbläsare finns i Ytterligare information nedan.

Om det efter den 31 oktober 2018 uppstår ett problem som rör användning av en gammal TLS-version kommer du att behöva uppdatera till TLS 1.2 eller till en enhet som stödjer TLS 1.2 som en del av lösningen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Vi rekommenderar att du proaktivt ta bort TLS 1.0- och 1.1-beroenden i dina miljöer och inaktiverar TLS 1.0 och 1.1 på operativsystemnivån där det är möjligt. Börja planera din migrering till TLS 1.2 i dag. Läs supportblogginlägget nedan för att få en lista över enheter som inte stöds av Intune i dag men som kanske fortfarande tar emot princip och som inte kommer att kunna kommunicera via TLS-version 1.2. Du kan behöva meddela dessa slutanvändare om att de kommer att förlora åtkomst till företagets resurser.

**Ytterligare Information**: [Intune går över till TLS 1.2 för kryptering](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)


### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Planera för förändring: Använd Intune på Azure för MDM-hanteringen <!-- 1227338 -->
För över ett år sedan tillkännagav vi en [allmänt tillgänglig förhandsversion av Intune på Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) och för sex månader sedan följde vi upp med [allmän tillgänglighet för den nya administratörsupplevelsen](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) för Intune. Från och med 31 augusti 2018 inaktiverar vi MDM (hantering av mobilenheter) i den klassiska Silverlight-konsolen för de kunder som använder fristående Intune. Du kan istället använda [Intune på Azure](https://aka.ms/Intune_on_Azure) för MDM-behoven. Om du fortfarande använder den klassiska konsolen för MDM rekommenderar vi att du ägnar en stund åt att bekanta dig med Intune på Azure. Vi förväntar oss inte att slutanvändarna ska påverkas av denna förändring. Klassisk datorhantering kommer att finnas kvar i Silverlight. Du kan läsa mer om den här förändringen och hur den påverkar dig [här](https://aka.ms/Intune_on_Azure_mdm).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->
Apple har tillkännagivit att de kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen. Vi lägger till information i [Intunes supportblogg](https://aka.ms/compportalats).



## <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/cloud-platform/roadmap)
* [Nyheter i företagsportalens gränssnitt](whats-new-app-ui.md)
* [Nyheter från föregående månad](whats-new-archive.md)
