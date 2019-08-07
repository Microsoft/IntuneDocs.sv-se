---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 969e7bc4804e1f66230c76d742bec2c67c2fa006
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670921"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>Under utveckling för Microsoft Intune – Augusti 2019

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Dessutom:

- Om vi tror att du behöver vidta åtgärder innan en ändring genomförs, publicerar vi ett extra inlägg i meddelandecentret för Office.
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

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Apphantering

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>Kontroll av avinstallations beteende för iOS-app vid avregistrering av enhet <!-- 3504144 -->
Administratörer kommer att kunna hantera om en app tas bort eller sparas på en enhet när enheten avregistreras på en användare eller enhets grupp nivå. 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Kategorisera appar i Microsoft Store för företag <!-- 3926922 -->
Du kan kategorisera Microsoft Store för företags program. Om du vill göra det väljer du**appar** för **Intune** >  ****  > -appar > väljer en**kategori**för **program information** > för Microsoft Store för företag >. Tilldela en kategori på den nedrullningsbara menyn.
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurera program meddelande innehåll för organisations konton <!-- 2576686 -->
Med Intune App Protection-principer (APP) på Android-och iOS-enheter kan du styra appens meddelande innehåll för org-konton. Den här funktionen kommer att kräva stöd från program och är kanske inte tillgänglig för alla APP-aktiverade program. Mer information om APP finns i [Vad är appskyddsprinciper?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Tillgänglig Google Play-apprapportering för Android-arbetsprofiler <!-- 3041956  -->
Om du vill se tillgängliga appinstallationer på Androids arbetsprofilenheter, kan du visa appens installationsstatus samt den installerade versionen av hanterade Google Play-appar. Mer information finns i [Så här övervakar du appskyddsprinciper](app-protection-policies-monitor.md), [Hantera Android-arbetsprofilenheter med Intune](android-enterprise-overview.md) och [Hanterade Google Play-apptyper](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>Vissa begränsningar för iOS-enheter som inte övervakas kommer att bli övervakade – endast med iOS 13,0-versionen <!-- 4867809  -->
Vissa inställningar gäller endast övervakade enheter med iOS 13,0-versionen. Inställningarna omfattar:

- App Store, dokumentvisning, spel
  - Appbutik
  - Explicit iTunes-, musik-, poddsändning-eller nyhets innehåll
  - Lägga till Game Center-vänner
  - Spel för flera personer
- Inbyggda appar
  - Kamera
    - FaceTime
  - Safari
    - Autofyll
- Moln och lagring
  - Säkerhetskopiera till iCloud
  - Blockera iCloud-dokument synkronisering
  - Blockera synkronisering av iCloud-nyckelring

Om de här inställningarna konfigureras och tilldelas till ej övervakade enheter före iOS 13,0-versionen, tillämpas inställningarna fortfarande på de enheter som inte övervakas. De gäller även när enheterna har uppgraderat till iOS 13,0. Dessa begränsningar tas bort på ej övervakade enheter som säkerhets kopie ras och återställs. 

Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](device-restrictions-ios.md) för att se de aktuella inställningarna.

Gäller för:  
- iOS 13,0 och senare

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>Nya inställningar och ändringar i befintliga inställningar för att begränsa funktionerna på iOS-och macOS-enheter <!-- 4867699 4867709  -->
Du kan skapa profiler för att begränsa inställningar på enheter som kör iOS och MacOS (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS** eller **MacOS** för plattform Ange > **enhets begränsningar**). Följande funktioner kommer att läggas till:

- Använd den nya inställningen för att hindra användare från att starta **** arbete på en MacOS-enhet på en **MacOS** > -enhets**begränsningar** > och fortsätta att arbeta på en annan MacOS-eller iOS-enhet. ****
  Gå till [macOS-enhetsinställningar för att tillåta eller begränsa funktioner med Intune](device-restrictions-macos.md) för att se de aktuella inställningarna.
- På **iOS** > -**enhets begränsningar**finns det några ändringar:
  - **Inbyggda appar** > **hittar min iPhone (endast övervakat)** : ny inställning som blockerar den här funktionen i Hitta min app-funktion. 
  - **Inbyggda appar** > **hitta mina vänner (endast övervakat)** : en ny inställning som blockerar den här funktionen i Hitta min app-funktion. 
  - **** Trådlös > **ändring av Wi-Fi-tillstånd (endast övervakat)** : en ny inställning som förhindrar att användare aktiverar eller inaktiverar Wi-Fi på enheten.
  - **Tangent bord och ord lista** > **QuickPath (endast övervakat)** : en ny inställning som blockerar QuickPath-funktionen.
  - **Moln och lagring**: **aktivitets fortsättningen** har bytt namn till **** att skickas.

  Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](device-restrictions-ios.md) för att se de aktuella inställningarna.

Gäller för:  
- macOS 10,15 och senare
- iOS 13 och senare

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>Kontrol lera appar, filer, dokument och mappar som öppnas när användaren loggar in på macOS-enheter <!--3914202  -->
Du kan aktivera och konfigurera funktioner på MacOS-enheter (enhets**konfigurations** > **profiler** > **Skapa profil** > **MacOS** för plattform > **enhets funktioner** för profil typ). 

Det finns nya inställningar för inloggnings objekt som styr vilka appar, filer, dokument och mappar som öppnas när en användare loggar in till den registrerade enheten. 

Om du vill visa de aktuella inställningarna går du till [Funktionsinställningar för macOS-enheter i Intune](macos-device-features-settings.md).

Gäller för:  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>Nya funktioner för Android Enterprise-dedikerade enheter i multi-app-läge <!-- 3755304 3041943 3041946  -->
Du kan kontrol lera funktioner och inställningar i en hel skärms stil i dina Android Enterprise-dedikerade enheter. Om du vill göra det väljer du **enhets konfiguration** > **profiler** > **Skapa profil** > **Android Enterprise** för plattform > **endast enhets ägare, enhets begränsningar** för profil typ.

Följande funktioner kommer att läggas till:
- **Dedikerade enheter** > **multi-app**: **knappen** för den virtuella datorn kan visas genom att svepa på enheten eller flytande på skärmen så att användarna kan flytta den.
- **Dedikerade enheter** > **multi-app**: **strålkastare Access** gör att användarna kan använda strålkastare. 
- **Dedikerade enheter** > **multi-app**: **medie volym kontroll** gör det möjligt för användare att kontrol lera enhetens medie volym med hjälp av ett skjutreglage. 
- **Dedikerade enheter** > **multi-app**: Aktivera en skärmsläckare, ladda upp en anpassad avbildning och kontrol lera när skärmsläckaren visas.

Om du vill se aktuella inställningar, går du till [Inställningar för Android Enterprise-enheter som tillåter eller begränsar funktioner med Intune](device-restrictions-android-for-work.md#dedicated-device-settings).

Gäller för:  
- Dedikerade Android Enterprise-enheter

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>Nya app-och konfigurations profiler för Android Enterprise fullständigt hanterade enheter <!-- 3574215  -->
Med hjälp av profiler kan du konfigurera inställningar som tillämpar VPN-, e-post-och Wi-Fi-inställningar på dina fullständigt hanterade Android Enterprise-enheter. Du kommer att kunna:
- Använd app-profiler för att distribuera Outlook, Gmail och nio e-postinställningar.
- Använd enhets konfigurations profiler för att distribuera betrodda rot certifikat inställningar.
- Använd enhets konfigurations profiler för att distribuera VPN-och Wi-Fi-inställningar.

Användarna autentiseras med sitt användar namn och lösen ord för VPN-, Wi-Fi-och e-postprofiler. Certifikatbaserad autentisering är för närvarande inte tillgängligt. 

Gäller för:  
- Fullständigt hanterad Android Enterprise

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Stöd för IKEv2 VPN-profiler för iOS <!-- 1943438 -->
Du kommer att kunna skapa VPN-profiler för den iOS-inbyggda VPN-klienten med hjälp av IKEv2-protokoll. IKEv2 är en ny anslutningstyp i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **VPN** för profiltyp > **Inställningar**.

De här VPN-profilerna konfigurerar den inbyggda VPN-klienten. Därför installeras eller skickas inga VPN-klientappar till hanterade enheter. Den här funktionen kräver att enheter registreras i Intune (MDM-registrering).

Om du vill se de aktuella VPN-inställningarna som du kan konfigurera går du till [Konfigurera VPN-inställningar på iOS-enheter i Microsoft Intune](vpn-settings-ios.md).

Gäller för: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Enhetsregistrering

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>Hoppa över fler skärmar i installations assistenten <!--4877451 -->
Du kommer att kunna ange Programmet för enhetsregistrering profiler som hoppar över följande installations assistents skärmar: 
- Skärmtid
- Installation av Touch-ID

Det gör du genom att gå **till enhets registrering** > **Apple-registrering** > token för**registrerings program** > välja en token > **profiler** > Välj en profil > **egenskaperna** > **Redigera** bredvid **anpassning av installations assistenten**.
Mer information om anpassning av installations assistenten finns i [skapa en Apple-registrerings profil ](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Administratörs stöd för Android-registrering <!-- 4869749  -->
Alternativet för registrering av Android-enhets administratörer läggs till på sidan Android- ****  > registrering (**registrering av Android**-**enhets** > registrering). Android-enhetens administratör är fortfarande aktive rad som standard för alla klienter.  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>För iOS-enheter anpassar du registrerings processens sekretess sida på Företagsportal <!-- 4394993  -->
Med hjälp av markdown kan du anpassa Företagsportalens sekretess skärm som slutanvändarna ser under iOS-registreringen. Mer specifikt kan du anpassa listan över saker som din organisation inte kan se eller göra på enheten.

<!-- ***********************************************-->
## <a name="device-management"></a>Enhetshantering

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Build-nummer som finns på Android-enhetens maskin varu sida <!-- 4461910  -->
En ny post på sidan maskin vara för varje Android-enhet innehåller versions numret för enhetens operativ system.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Konfigurera automatisk rensning av enhetens tids gräns till 30 dagar <!--4231059  -->
Du kan ställa in den automatiska tids gränsen för enhets rensning så kort som 30 dagar (i stället för den aktuella gränsen på 90 dagar) efter den senaste inloggningen. Det gör du genom att gå till **Intune** > -**enheter** > **Konfigurera** > **enhet rensa regler**.

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

### <a name="default-scope-tag----3702875---"></a>Standard omfattnings tag gen <!-- 3702875 -->
En ny inbyggd standard omfattnings tagg är tillgänglig. Alla otaggade Intune-objekt som stöder omfångs Taggar tilldelas automatiskt till standard omfångs tag gen. **Standard** omfångs tag gen läggs till i alla befintliga roll tilldelningar för att upprätthålla paritet med administratörs upplevelsen idag. Om du inte vill att en administratör ska se Intune-objekt med standard omfångs taggar, tar du bort standard omfångs tag gen från roll tilldelningen. Den här funktionen liknar funktionen säkerhets omfattningar i System Center Configuration Manager.

<!-- ***********************************************-->
## <a name="security"></a>Säkerhet

### <a name="import-and-export-security-baselines------3408610------------"></a>Importera och exportera säkerhets bas linjer    <!--3408610          -->  
Vi lägger till möjligheten att exportera och importera säkerhets bas linjer. Med den här funktionen kan du ta dina anpassningar med dig och dela dem mellan Intune-miljöer.

<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).




