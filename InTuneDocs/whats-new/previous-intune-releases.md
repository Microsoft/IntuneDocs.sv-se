---
title: Tidigare versioner | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d3305d9938244f0da769dc547cd7a42d7ef81ed
ms.openlocfilehash: 996198a2525dc830d229e7143afda3c71f4276b8


---

# Tidigare versioner av Intune
## Augusti 2016
## Augusti 2016
## Apphantering
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### Dolda och visade appar för iOS 9.3
För övervakade enheter som kör iOS 9.3 eller senare kan du använda listan över dolda och visade appar i den allmänna konfigurationsprincipen för iOS för att:
- Ange en lista över appar som ska vara dolda från användare. Användare kan inte visa eller starta dessa appar.
- Ange en lista över appar som användare kan visa och starta. Inga andra appar kan visas eller startas.

Appar som du kan ange omfattar både appar som du har distribuerat och inbyggda iOS-appar som Meddelanden och Anteckningar. Mer information finns i [Principinställningar för iOS i Microsoft Intune]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
### Princip för tillåtna och blockerade appar för Samsung KNOX-enheter
Nu kan du konfigurera en anpassad princip för Samsung KNOX-enheter som gör att du kan skapa något av följande:
- En lista över appar som blockeras från att köras på enheten. Även om den har installerats kan en app som definierats i listan över blockerade appar inte aktiveras på enheten.
- En lista över appar som enhetens användare tillåts att installera från Google Play Store. Inga andra appar kan installeras från butiken.

De här inställningarna kan endast användas av enheter som kör Samsung KNOX.
Mer information finns i [Använda anpassade principer för att tillåta och blockera appar för Samsung KNOX-enheter]( custom-policy-to-allow-and-block-samsung-knox-apps.md).
<!---TFS 1311629 checked --->
### Nya appar är kompatibla med hanteringsprinciper för mobilappar (MAM)
Yammer-appen för [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) och [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) är nu kompatibel med [hanteringsprinciper för mobilprogram (MAM) i Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), oavsett om enheten har registrerats eller inte.

En fullständig lista över MAM-kompatibla appar finns på webbplatsen för [Microsoft Intune-programpartner](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### Intune Viewer-appar
Vid lanseringen av den nya RMS-delningsappen tar vi bort följande Intune Viewer-appar, med början från augusti 2016:
- Intune AV Viewer
- Intune PDF Viewer
- Intune Image Viewer för Android från Google Play

I stället för att använda Intune Viewer-appar bör du använda den nya [Rights Management-appen (RMS-delning) för Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. När Intune Viewer-appen inte längre stöds tas den bort från Google Store och är inte längre tillgänglig för framtida bruk.

## Enhetshantering
### Stöd för Android 7.0
I augusti kommer Intune att stödja "day 0" för det kommande Android 7.0-operativsystemet för mobila enheter.
<!---TFS 1262053--->
### Googles borttagning av funktionen för fjärråterställning av lösenord på Android 7.0-enheter
Google tar bort möjligheten för IT-administratörer och slutanvändare att fjärråterställa lösenordet på Android 7.0-enheter. Tidigare kunde IT-administratörer fjärråterställa en användares lösenord, och slutanvändarna kunde återställa sina lösenord från företagsportalens webbplats.



## Uppdateringar av företagsportalen
### Företagsportalens webbplats
- **Feedbacklänk från företagsportalen till Microsoft** <br/>
På företagsportalens webbplats kan slutanvändare trycka på en ny "Feedback"-länk, längst ned på sidan, för att skicka feedback till Microsoft om sina erfarenheter av webbplatsen. Den insamlade, avidentifierade feedbacken hjälper Microsoft att förbättra företagsportalens webbplats för användare.
<!--- TFS 1313657 checked--->

### iOS
- **Lägsta version för Managed Browser (iOS) har ändrats till 8.0**<br/>
Microsoft Intune Managed Browser-appen för iOS har uppdaterats för att stödja enheter som kör iOS 8.0 eller senare. Enheter som kör iOS 7.1 kan fortfarande använda Managed Browser-appen, men uppmana ändå användarna att uppdatera till iOS 8.0 eller senare så att de får åtkomst till och kan dra full nytta av de nya funktionerna i Managed Browser.  
<!---TFS 1313253 checked--->

## Kommande nyheter

### Stöd för iOS 10
Intune kommer att stöda iOS 10 fullt ut. Mer information kommer att följa publiceringen av iOS 10.

### Intune-grupper övergår till Azure Active Directory-grupper i början av september 2016
Intune får en ny grupphanteringsupplevelse. ADD-säkerhetsgrupper (Azure Active Directory) kommer att användas som användargrupper och enhetsgrupper i Intune. Dessa grupper kommer att användas för all grupphantering, principdistribution och profildistribution **när vi introducerar den nya Azure-baserade Intune-administratörsportalen**.

Med den nya upplevelsen behöver du inte duplicera grupper i olika tjänster och **du får tillgång till nya AADP-gruppfunktioner (Azure Active Directory Premium)**. Dessutom får du möjlighet till utökning med PowerShell och Graph. Du får även en mer enhetlig grupphantering för mobilitetshanteringen i företaget.

Det kommer att göras en del ändringar i den **aktuella administratörskonsolen** i samband med övergången till säkerhetsgrupper. **Dessa ändringar, och användning av AAD-säkerhetsgrupper, kommer att läggas till i Intune-dokumentationen**.

Nya Intune-användare kommer att se **några av ändringarna före befintliga klienter**.

Förutom ändringarna i grupphantering kommer **följande funktion att bli inaktuell**:
- Exkludera medlemmar eller grupper när du skapar en ny grupp
- Grupperna **Användare utan grupp** och **Enheter utan grupp**
- **Hantera grupper** i rollen tjänstadministratör
- Anpassade gruppbaserade aviseringar för aviseringsregler
- Pivotering med grupper i rapporter
<!--- TFS 1295329--->

### Tillägg av Meddelanden på företagsportalen för Android
Vi publicerar en uppdatering av företagsportalen för Android i september där vi lägger till en ny **Meddelanden**-ikon på startsidan. När användaren trycker på ikonen visas sidan **Meddelanden**. På sidan visas alla objekt som kräver åtgärder i företagsportalappen, till exempel inkompatibla enheter, registreringsuppdatering och aktivering av registreringar. Om du också använder företagsportalappen för iOS kan du redan se dessa meddelanden. När sidan **Meddelanden** läggs till kommer sidan **Konfiguration av företagsåtkomst** inte att visas varje gång du startar eller återupptar företagsportalen för Android, förutsatt att enheten redan är registrerad. Vi vet att många av er har skapat instruktioner till användarna och uppskattar att få veta på förhand när era instruktioner/skärmbilder behöver uppdateras. Uppdatera din dokumentation med de kommande ändringarna. Om du behöver nya skärmbilder kan du gå till https://aka.ms/androidcpupdate.  

### Förbättringar i hur iOS-slutanvändare får sina appar
Följande ändringar av app-panelerna i företagsportalsappen för iOS görs i september så att användarna ska kunna få flera vyer på en och samma plats, nämligen företagsportalens webbplats för alla deras appar. Apples begränsningar förhindrar för närvarande att verksamhetsspecifika appar och hanterade App Store-appar listas i företagsportalsappen, och kräver att besöker olika vyer om de vill hitta alla sina appar.

- Panelen **Företagsappar** pekar för närvarande på en lista över alla program på fliken ALLA på företagsportalens webbplats, och den kommer att fortsätta fungera på samma sätt. Namnet på panelen ändras till **Alla appar**.
- Panelen **Andra appar** pekar för tillfället pekar på en vy i företagsportalsappen som visar alla appar som Apple tillåter att företagsportalsappen visar. Namnet på panelen ändras till **Aktuella appar**, och om du trycker på panelen öppnas fliken AKTUELLT på företagsportalens webbplats.
-  Panelen **Kategorier** pekar för tillfället på en vy i företagsportalsappen som listar appkategorier. Panelens namn kommer inte att ändras, men den kommer nu att peka på fliken KATEGORIER på företagsportalens webbplats. Du kan söka efter uppdaterade skärmbilder [här](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

### Moln-översikt
Håll dig informerad om Intunes utveckling i [översikten över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Tjänstens utfasning
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Ändringar i stödet för iOS-företagsportalappen**<br/>
I september krävs det av alla användare att de använder den senaste versionen av Microsoft Intune-företagsportalappen för iOS. Nya användare kommer bara att kunna hämta den senaste versionen och aktuella användare kommer att behöva uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.  

- **Lägsta version för Managed Browser (iOS) har ändrats till 8.0**<br/>
I augusti släpper Intune en uppdaterad Microsoft Intune Managed Browser-app för iOS som bara stöder enheter som kör iOS 8.0 eller senare. Enheter som kör iOS 7.1 kan fortfarande använda Managed Browser-appen, men uppmana ändå användarna att uppdatera till iOS 8.0 eller senare så att de får åtkomst till och kan dra full nytta av de nya funktionerna i Managed Browser.  
<!---TFS 1313253--->

- **Företagsportalappar för Windows 8 och Windows Phone 8 blir inaktuella** <br/>
Från och med oktober 2016 kommer Microsoft Intune inte längre stödja företagsportalappar för Windows 8 och Windows Phone 8. Microsoft Intunes stöd för Windows Phone 8-plattformen kommer också att upphöra. Följaktligen kommer du inte att kunna registrera eller uppdatera Windows Phone 8-enheter. Men du kan fortsätta att hantera Windows Phone 8- och Windows 8-enheter som redan har registrerats. Uppdatera enheter med Windows Phone 8 och Windows 8 till Windows Phone 8.1 respektive Windows 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1. På så sätt kan du fortsätta att distribuera appar till dessa enheter utan avbrott.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## Juli 2016
### Apphantering
#### Förbättra uppdateringsupplevelsen för appetableringsprofiler
Verksamhetsspecifika Apple iOS-appar skapas med en inbyggd etableringsprofil och kod som signeras med ett certifikat. När appen körs på en iOS-enhet bekräftar iOS appens integritet och tillämpar de principer som definierats av etableringsprofilen.

Signeringscertifikatet du använder för att signera appar gäller normalt i 3 år. Däremot upphör etableringsprofilen att gälla efter ett år. Med den här uppdateringen tillhandahåller Intune verktyg för att distribuera en ny etableringsprofilprincip till enheter som har appar som snart slutar att gälla medan certifikatet fortfarande är giltigt. Mer information finns i [Använda etableringsprofilprinciper för iOS för att hålla verksamhetsspecifika appar uppdaterade](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->
#### Xamarin SDK för Intune-appar är tillgängligt
Med komponenten Intune App SDK Xamarin kan du aktivera funktioner för hantering av mobilappar med Intune i iOS- och Android-appar som utvecklats med Xamarin. Komponenten hittar du i [Xamarin store](https://components.xamarin.com/view/Microsoft.Intune.MAM) eller på [Github-sidan för Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### Enhetshantering
#### Höjd gräns för enhetsregistrering
Intune har ökat maxgränsen för enhetsregistrering från 5 till 15 enheter per användare.
<!---TFS 1289896 --->

#### TeamViewer-integrering för Windows-datorer med Intune-klientprogramvaran
Med [TeamViewer](https://www.teamviewer.com)-integrering för Windows-datorer som kör Intune-klienten kan du etablera fjärrhjälpssessioner med Windows-datorer, vilket underlättar supportavdelningens arbete. Detta gäller Windows 7, 8, 8.1 och Windows 10. Mer information finns i [Vanliga hanteringsuppgifter för Windows-datorer med Microsoft Intune-datorklienten](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).
<!---TFS 1284856--->

### Uppdateringar av företagsportalen
#### Företagsportalens webbplats
- **Förbättrad användarupplevelse vid registrering av Windows-enheter**<br/>
När du använder villkorlig åtkomst har registreringsanvisningarna för Windows 8.1, Windows 10 Desktop och Windows 10 Mobile förenklats på företagsportalens webbplats. Nu visas separata steg för ”enhetsregistrering” och ”anslutning till arbetsplatsen”, vilket gör det lättare att se status för enheterna och slutföra processen om användarna inte lyckas ansluta till arbetsplatsen. De separata stegen förväntas också underlätta felsökningen för IT-administratörer. När slutanvändarna försökte registrera en enhet och alla steg lyckades utom anslutningen till arbetsplatsen visades inte den registrerade enheten i listan med enheter som användarna skulle identifiera, vilket orsakade förvirring för användarna.

#### Android
- **Android-företagsportalsapp**<br/>
Om Android-användarna ser ett felmeddelande om att enheten saknar ett nödvändigt certifikat kan de trycka på ”Så här löser du problemet” och få [anvisningar](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) om hur de installerar certifikatet som saknas. Om användarna slutför stegen men får ett felmeddelande om att ”certifikat saknas” ombeds de kontakta IT-administratören och ange den här [länken](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues) som innehåller anvisningar som IT-administratörer kan använda för att åtgärda certifikatproblem.

- **Begränsa appinstallation med separat inläsning till registrerade enheter**<br/>
Det går inte längre att installera program på Android-enheter via företagsportalens webbplats om de inte har registrerats i Intune via Intune-företagsportalappen för Android.
<!---TFS 1299082--->

#### iOS
- **Ändringar av konton för enhetsregistreringshanterare i iOS-företagsportalappen**<br/>
För att förbättra prestanda och skalning visar Intune inte längre alla enheter i Enhetsregistreringshanteraren (DEM) i fönstret **Mina enheter** i företagsportalappen för iOS. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen.

DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen. Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter.

Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt. Mer information finns i [Registrera företagsägda enheter med Enhetsregistreringshanteraren i Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### Ändrade namn på Windows-funktioner
- [Microsoft Passport for Windows](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) heter numera **Windows Hello för företag**.
- [Företagsdataskydd](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) kallas nu **Windows informationsskydd**.

## Juni 2016
### Hälsotillstånd för Intune-tjänsten
Information om Intune-tjänstens hälsotillstånd har nu flyttats till en central plats med andra Microsoft-tjänster. Nu finns den här informationen i under Tjänstens hälsa i Office 365-hanteringsportalen. Mer information finns i [det här blogginlägget](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### Apphantering
- **Förbättrad konfigurationsupplevelse för Windows 10-företagsdatapolicy.** Vi har gjort förbättringar i konfigurationsupplevelsen för Windows 10- företagsdatapolicyn när det gäller att skapa regler för program, specificera nätverksgränsdefinitioner och andra inställningar för företagsdataskydd. Läs mer i [Skapa en princip för företagsdataskydd (EDP) med Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### Enhetshantering
- **Windows Defender-principinställning för att skydda mot potentiellt oönskade appar.** En ny Windows Defender-inställning som kallas **identifiering av potentiellt oönskade program** har lagts till i den allmänna konfigurationsprincipen för Windows 10 Desktop och Mobile. Du kan använda den här inställningen för att skydda registrerade stationära Windows-datorer från att köra program som Windows Defender har klassificerat som potentiellt oönskade. Du kan skydda dig mot att dessa program körs eller använda granskningsläget för att rapportera att ett potentiellt oönskat program har installerats. Mer information finns i [Principinställningar för Windows 10 i Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### Villkorlig åtkomst
- **Cisco ISE-kontrollprinciper för nätverksåtkomst för Intune.**  Kunder som använder Cisco Identity Service Engine (ISE) 2.1 och även använder Microsoft Intune kan ange en princip för nätverksåtkomst i ISE.

    Med den här principen måste enheter som ansluter till nätverket med hjälp av Wi-Fi eller VPN uppfylla följande villkor innan de tillåts åtkomst:

    * Måste hanteras av Intune
    * Måste vara kompatibla med alla distribuerade efterlevnadsprinciper för Intune

 Användare med icke kompatibla enheter uppmanas att registrera sig och åtgärda eventuella efterlevnadsproblem för att få åtkomst.
- **Villkorlig åtkomst för webbläsare.** Du kan skapa en princip för villkorlig åtkomst för [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) och [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) så att programmen bara kan användas från webbläsare som stöds i hanterade och godkända iOS- och Android-enheter. Användare som försöker logga in till Outlook Web Access (OWA) och SharePoint-webbplatser med iOS- och Android-enheter uppmanas att registrera sina enheter med Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS 1175844--->

- **Dynamics CRM Online stöder villkorlig åtkomst.** Du kan skapa en princip för villkorlig åtkomst för [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) så att det bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Slutanvändare som försöker logga in i mobilappen för Dynamics CRM på iOS och Android uppmanas att registrera sig i Intune samt åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS1295358--->

##Uppdateringar av företagsportalen

#### Android-företagsportalsapp

- När IT-administratörer använder den nya principen ”Kräv att enheter förhindrar installation av appar från okända källor (Android 4.0+)” visas meddelandet ”Installation från okända källor måste inaktiveras” i enheter med Android 4.0 eller senare. Användare måste välja **Inställningar** > **Säkerhet**, och inaktivera **Okända källor**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) om meddelandet och varför användaren måste inaktivera inställningen.

- När IT-administratörer använder den nya principen ”Kräv att ”Genomsök enhet efter säkerhetshot" (Android 4.0+) är aktiverat på enheter” visas meddelandet ”Genomsök enhet efter säkerhetshot” i enheter med Android 4.0 eller senare. Användarna måste välja **Inställningar** > **Google** > **Säkerhet** och aktivera **Genomsök enhet efter säkerhetshot**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) om meddelandet och varför användaren måste aktivera inställningen.

- När IT-administratörer använder den nya principen ”Kräv att USB-felsökning är inaktiverat (Android 4.2+)” visas meddelandet ”USB-felsökning måste inaktiveras” i enheter med Android 4.2 eller senare. Användarna måste välja **Inställningar** > **Utvecklaralternativ** och inaktivera **USB-felsökning**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) om meddelandet och varför användaren måste inaktivera inställningen.

- När IT-administratörer använda nya principen ”Lägsta Android-säkerhetskorrigeringsnivå (Android 6.0+)” visas meddelandet ”Den här enheten motsvarar inte miniminivån för Android-säkerhetskorrigering” i enheter med Android 6.0 eller senare. Användarna måste installera den nödvändiga säkerhetskorrigeringen. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) om hur den nödvändiga säkerhetskorrigeringen installeras och vilken säkerhetskorrigering som redan finns installerad.

#### iOS-företagsportalappen

- Appinstallationen har förbättrats för slutanvändare som installerar affärsspecifika appar. Om appinstallationen tar lång tid kan användarna synkronisera sina enheter manuellt för att tvinga synkroniseringen att fortsätta. Instruktioner för slutanvändaren finns i [Synkronisera din iOS-enhet manuellt](/Intune/EndUser/sync-your-device-manually-ios).

- Microsoft Intunes-företagsportalappen för iOS har uppdaterats med stöd till iOS version 8.0 och senare. Uppdateringen innebär att slutanvändare bara kan installera företagsportalappen och registrera nya enheter i Intune om enheten kör iOS version 8.0 eller senare. Användare som redan har registrerat enheter som körs på en iOS-version som inte stöds, kan fortsätta använda den företagsportalapp som finns på enheten.


## Maj 2016

Alla dessa funktioner stöds även för hybriddistributioner (Configuration Manager med Intune). Mer information om nya hybridfunktioner finns på sidan med [nyheter om hybridfunktioner](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Dokumentation
Välkommen till förhandsversionen av [docs.microsoft.com](https://docs.microsoft.com/en-us/intune)!
Det här är en helt ny modern innehållsplattform som har tagits fram för att göra det enklare för våra kunder att förstå och använda Intune.
Mer information om alla de nya funktionerna finns i [Introduktion till docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Hälsotillstånd för Intune-tjänsten
Information om Intune-tjänstens hälsotillstånd har nu flyttats till en central plats med andra Microsoft-tjänster. Nu hittar du den här informationen under **Tjänstens hälsa** i [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx).
Mer information finns i [det här blogginlägget](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Apphantering
- **MAM SDK: Stöd för konfiguration av PIN-kodens längd.** Du kan ange längden på PIN-koden för MAM-appar på samma sätt som PIN-koden för en enhet. Detta innebär att slutanvändaren måste uppfylla de nya begränsningar som du anger. Användaren ser en lite annorlunda PIN-skärm som är anpassad till den längre inmatningen. Mer information finns i [MAM-principinställningar för Android](android-mam-policy-settings.md) och [MAM-principinställningar för iOS](ios-mam-policy-settings.md).

- **Skype för företag för iOS och Android.** Nu kan du använda Skype för företag med [MAM utan registreringsprinciper](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md). När användarna loggar in tillämpas MAM-principerna.

- **Nya appar tillgängliga för hantering med MAM-principer.** Microsoft Word-, Excel- och PowerPoint-appar för Android kan nu associeras med MAM-principer på enheter som inte har registrerats med Intune. Om du vill se en fullständig lista över appar som stöds kan du gå till Microsoft Intune-galleriet för mobilprogram på sidan för [Microsoft Intune-programpartner](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


### Uppdateringar av företagsportalen

#### Android-företagsportalsapp
- **Popup-meddelanden för slutanvändare**: Slutanvändarna ser nu popup-meddelandena från Android-företagsportalappen när de registrerar eller tar bort enheter från företagsportalen.

- **Ändringar i kontona för Enhetsregistreringshanterare i Android-företagsportalappen.** I syfte att förbättra prestanda och skalning visar Intune inte längre alla enheter i enhetsregistreringshanteraren i fönstret Mina enheter Android-företagsportalappen. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen.

#### Företagsportalens webbplats
- **Webbplatsen för företagsportalen: En banderoll för enhetsidentifikation visar mer information för slutanvändaren.** Slutanvändarna kan nu enkelt identifiera den enhet de har valt när de använder företagsportalens webbplats. Om fel enhet har valts kan de välja rätt enhet genom att trycka på länken **Tryck här** på banderollen på startsidan.

## Kommande nyheter
- **Introduktion till gränssnittet i Meddelandecenter**. Som en del av migreringen av Intune till [hanteringsportalen för Office 365](https://portal.office.com/) kommer vi att börja utnyttja Meddelandecenter för att informera om nya funktioner och annan kommunikation. Genom att installera den medföljande mobilappen för Office 365-administratör kan du också ta emot meddelanden på din mobiltelefon och enkelt vidarebefordra meddelanden till användare eller ett distributionsalias.
Från och med majutgåvan kommer vi att börja använda Meddelandecenter för att meddela dig när uppdateringar är färdiga och för att publicera information om nya och förbättrade Intune-funktioner. Ta en titt på Meddelandecentret redan nu genom att logga in till [hanteringsportalen för Office 365](https://portal.office.com/) och välja alternativet MEDDELANDECENTER i det vänstra navigeringsfönstret.

- **Ändringar av konton för enhetsregistreringshanterare**. I syfte att förbättra prestanda och skalning visar Intune inte längre **alla** enheter i enhetsregistreringshanteraren i fönstret **Mina enheter** i iOS-företagsportalappen. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen. Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter. Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt.

### Moln-översikt
Håll dig informerad om Intunes utveckling i [översikten över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Tjänstens utfasning
- **Intune Viewer-appar.** Med versionen av den nya RMS-delningsappen tar vi bort följande Intune Viewer-appar, med början från augusti 2016:
    - Intune AV Viewer
    - Intune PDF Viewer
    - Intune Image Viewer för Android från Google Play

  I stället för att använda Intune Viewer-appar bör du använda den nya Rights Management-appen (RMS-delning) för Android, där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. Läs mer om RMS-delningsappen (med länk till dokumentationen).

- **Borttagning av anpassade meddelanderegler för specifika grupper.**
Intune-meddelanderegler används för att definiera vem en e-postavisering ska skickas till från Intune. För närvarande kan du konfigurera meddelanderegler för att skicka e-post till alla användare av enheter i en Intune-enhetsgrupp som du har skapat. Från och med den 1 juni 2016 eller däromkring kommer det inte längre att finnas stöd för att rikta sig till användarskapade grupper.

    Om du vill rikta en meddelanderegel till en grupp som du har skapat via Microsoft Intune-administrationskonsolen skulle du i dag utföra följande steg:

    Gå till **Admin**-arbetsytan och klicka på **Meddelanderegler** > **Skapa ny regel**

    Välj de enhetsgrupper som regeln ska gälla för i steg två i guiden Skapa meddelanderegel. Det här steget, Välj enhetsgrupper, håller på att fasas ut från Intune-konsolen.

    Den preliminära tidslinjen för den här ändringen ser ut som följer:
    - Från och med juni 2016 kan nya klienter inte se steg två i guiden Skapa meddelanderegel. Befintliga klienter påverkas inte.
    - Runt augusti 2016 kommer vissa befintliga klienter inte att se kommandot för att välja enhetsgrupper i guiden.
    - Runt oktober 2016 planerar vi för att samtliga klienter inte kommer att se kommandot för att välja enhetsgrupper i guiden.


- **Ändringar i stödet för iOS-företagsportalappen**. Under de kommande månaderna kommer det en uppdatering för Microsoft Intune-företagsportalappen för iOS som bara har stöd för enheter som kör iOS 8.0 eller senare. Användarna kan inte registrera nya enheter som kör versioner under iOS 8.0. Registrerade enheter som kör versioner under iOS 8.0 fortsätter att hanteras och kommer under en begränsad tid att kunna fortsätta använda företagsportalappen. Enheterna måste dock ha version iOS 8.0 eller senare installerad för att få åtkomst till den senaste versionen av företagsportalappen. Vi rekommenderar att du meddelar användarna om att de bör uppdatera till iOS 8.0 eller senare för att kunna dra full nytta av nya funktioner i Intune.  


## April 2016
Alla dessa funktioner stöds även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune).
### Apphantering
- **MAM-efterlevnad.**
Nu kan du visa [statusen](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) för dina programhanteringsprinciper för alla användare i din Azure Active Directory-klientorganisation (AAD). Du måste bland annat:
   - Egenskaper
   - Appar på enheten

   Statusvärden:

   **Incheckad**: Anger att principen distribuerades till användaren, att appen har använts i arbetskontexten och att principen har tillämpats.

    **Inte incheckad**: Anger att principen distribuerades till användaren, men att appen inte har använts i arbetskontexten sedan dess.


- **MAM-kontroller för att förhindra att Outlook-kontakter synkroniseras (Android).**
En ny inställning är tillgänglig för [hantering av mobila program](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) utan enhetsregistrering. Med den här inställningen kan du förhindra att ett program synkroniserar kontakter till den interna adressboken på Android-enheter. Om den här inställningen är aktiverad kan berörda program inte längre spara kontakter i den interna adressboken. Om den här inställningen är inaktiverad kan berörda program spara kontakter i den interna adressboken. När du [fjärraderar en enhet eller app](wipe-managed-company-app-data-with-Microsoft-Intune.md) tas kontakter som redan har sparats i den interna adressboken bort. Den här nya inställningen stöds av Outlook på Android-enheter.

### Enhetshantering
- **Identifiering av telefonnummer för företagsägda enheter.** Telefoner kategoriserade som ”företagsägda” identifieras nu med sina fullständiga telefonnummer, t.ex. när du kör en inventeringsrapport för mobila enheter. BYOD-telefonnummer döljs fortfarande med ***, och bara de fyra sista siffrorna visas.


### Uppdateringar av företagsportalen
**Android-företagsportalappen** Användare som inte har registrerat sin enhet i Intune och som inte har rätt certifikat installerat kan inte logga in på företagsportalappen för Android och får se meddelandet ”Du kan inte logga in eftersom enheten saknar ett obligatoriskt certifikat”. Meddelandet innehåller länken ”Så här löser du problemet” som användarna kan trycka på för att visa installationsanvisningar för certifikatet. Om du vill se de steg som slutanvändarna går igenom för att lösa problemet, se [Enheten saknar ett nödvändigt certifikat](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

Stöd för **iOS-företagsportalappen** har lagts till för dra-för-att-uppdatera-uppdateringsåtgärden för att uppdatera innehållet på startsidan, vilket innefattar de listade apparna, listade enheter och IT-kontaktuppgifterna. Den här åtgärden kontrollerar inte kompatibiliteten eller principinformation, vilket du kan göra genom att välja panelen för din aktuella enhet och trycka på knappen **Synkronisera**.

**Företagsportalappen för Windows 10 Mobile och Windows Phone 8.1** När slutanvändarna installerar branschspecifika appar får du nu en förbättrad programinstallationsupplevelse. Om appinstallationen tar lång tid kan användarna synkronisera sina enheter manuellt för att tvinga synkroniseringen att fortsätta. Instruktioner för slutanvändaren finns i [Synkronisera enheten manuellt för att påskynda appinstallationer](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Webbplatsen Företagsportal** När Windows 10 Mobile- och Windows Phone 8.1-användare installerar branschspecifika appar ser de nu följande nya statusar där de får mer information om installationens status:

* **Väntar på att enheten ska synkroniseras** – användaren har tryckt på ”Installera” och nu försöker enheten synkronisera med Intune-infrastrukturen. Synkroniseringen krävs innan installationen kan slutföras. Meddelandet ”Väntar på att enheten ska synkroniseras” är också en länk som användarna kan trycka på för att visa [instruktioner](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) om hur de manuellt synkroniserar sina enheter med Intune om synkroniseringsprocessen tar lång tid eller fastnar.
* **Hämtar** – användarens hämtningsbegäran behandlas och enheten laddar ned och installerar appen.

Innan dessa statusar lades till var det förvirrande för användarna när en appinstallation tog lång tid eftersom de bara såg statusen ”Installerar”, som kan visas på skärmen i flera timmar. Med de nya statusarna kan användarna, i stället för att kontakta supportavdelningen, trycka på länken ”Väntar på att enheten ska synkroniseras” och följa anvisningarna för att tvinga synkroniseringen att fortsätta.


## Mars 2016
### Nyheter den 29 mars 2016
Med undantag av uppdateringen av den allmänna konfigurationsprincipen för Windows 10 stöds alla funktioner som släpps den 29 mars 2016 även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune). Hybridstöd för uppdateringen av den allmänna konfigurationsprincipen för Windows 10 kommer snart. Observera att vissa av dessa funktioner kan kräva den senaste versionen av Configuration Manager.

### Apphantering
- **MAM-kontroller för att förhindra att Outlook-kontakter synkroniseras (iOS).** En ny inställning är tillgänglig för hantering av mobilprogram utan registrering av enheter. Med den här inställningen kan du förhindra att ett program synkroniserar kontakter till den interna adressboken på iOS-enheter. När den här inställningen är aktiverad kan appen inte längre spara kontakter i den interna adressboken. När den här inställningen är inaktiverad kan appen spara kontakter i den interna adressboken. När du selektivt rensar en enhet tas alla kontakter som redan har sparats i den interna adressboken bort. Den här nya inställningen stöds av Outlook-programmet på iOS-enheter. Mer information om denna och andra inställningar finns i [Skapa och distribuera MAM-principer](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Åtkomstkontroll
- **Skype för företag – Online stöder villkorlig åtkomst.** Du kan skapa en princip för villkorlig åtkomst för Skype för företag – Online så att programmet bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Användare som försöker logga in i mobilappen för Skype för företag på iOS och Android uppmanas att registrera sig i Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in. Mer information finns i [Hantera åtkomst till Skype för företag – online](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Enhetshantering
- **Intune-stöd för iOS 9.3.** Måndagen den 21 mars meddelade Apple tillgängligheten för iOS 9.3. Vi har arbetat hårt med att säkerställa att Microsoft Intune är kompatibelt med den senaste versionen av Apples mobila operativsystem och [vi är glada över att kunna meddela att Intune stöder hantering av iOS 9.3-enheter](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/).

  Alla befintliga Intune-funktioner som för närvarande är tillgängliga för hantering av iOS-enheter fortsätter att fungera sömlöst när användare uppgraderar sina enheter till iOS 9.3. Dessutom stöds iOS 9.3 i dag även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune).

- **Den allmänna konfigurationsprincipen för Windows 10 innehåller nu inställningar för hantering av Windows Defender på registrerade Windows 10-datorer.** Mer information finns i [Inställningar för Windows 10-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Företagsportal

- **Windows-appaket är tillgängliga direkt från företagsportalens webbplats.** Användare av Windows 8-, Windows 8.1- och Windows RT-datorer kan nu installera Windows-appaket (med filtillägget .appx) direkt från företagsportalens webbplats. Tidigare var du tvungen att distribuera eller så var användarna tvungna att installera företagsportalappen på sina enheter för att installera appar.

- **Användarna kan fjärrlåsa sin enhet från företagsportalens webbplats.** Ett nytt alternativ för fjärrlåsning har lagts till på företagsportalens webbplats så att användarna kan fjärrlåsa sin enhet från portalen om de tappar bort enheten eller om den blir stulen. Se [instruktionerna för slutanvändaren](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). Följande tabell visar plattformsstödet för fjärrlåsning för fristående Intune och Intune med Configuration Manager.

|Plattform | Information om stöd|
|---------|----------------|
|Android |Stöds|
|iOS |Stöds|
|Windows 10 Mobil |Stöds endast om telefonen har ett konfigurerat lösenord|
|Windows 10 Desktop |Stöds inte|
|Windows Phone 8.1 |Stöds endast om telefonen har ett konfigurerat lösenord|
|Windows Phone 8.0 |Stöds inte|
|PC (Windows 8.0 eller tidigare) |Stöds inte|
|PC (Windows 8.1) |Stöds inte|

### Nyheter den 10 mars 2016

### Apphantering

- **Dra nytta av funktionen ”Öppna i” för iOS för enheter som har registrerats i en MDM-lösning från tredje part** Du kan använda en MDM-lösning (hantering av mobila enheter) från en annan leverantör om du vill dra nytta av funktionen ”Öppna i” för iOS. Du kan ange begränsningarna i inställningarna för konfigurationsprofilen och distribuera appen med [Hantera dataöverföring mellan iOS-appar](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

     Den här metoden har två huvudsakliga fördelar:

     1. Användarna måste logga in med sitt arbetskonto innan de får tillgång till företagsdata från molntjänster eller andra appar. Detta säkerställer att hanteringsprinciper för mobilappar (MAM) finns på plats när användaren kommer åt data.

     2. Hanterade e-postprofiler och andra hanterade appar som distribuerats via en tredje parts MDM-lösning kan dela filer och data med appar som har Intunes MAM-principer.

- **Hantera Microsoft Outlook-appen med MAM-principer för enheter som inte har registrerats i Intune** Nu kan du hantera Microsoft Outlook-appen på enheter som inte har registrerats i Intune med Intune-principen för hantering av mobilprogram. Den uppdaterade Microsoft Outlook-appen med MAM-funktionerna är tillgänglig för både [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8)- och [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook)-enheter. Följ instruktionerna i avsnittet [Skapa och distribuera hanteringsprinciper för mobilappar](https://technet.microsoft.com/library/mt627829.aspx) om du vill skapa en MAM-princip.  


- **Med konfigurationsprinciper för mobilappar har du större flexibilitet att ange användarinformation för iOS-appar** Du kan ange användarinställningar som en iOS-app kan behöva när den öppnas. Du kan till exempel ange en nätverksport eller ett användarnamn. Mer information finns i [Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Distribuera Adobe Reader för Microsoft Intune till Intune-hanterade iOS-enheter inom företaget** Nu kan Adobe Reader-appen för iOS hanteras på registrerade enheter med Intunes hanteringsprincip för mobilprogram.

- **Se till att distribuerade webbklipp öppnas i den hanterade webbläsaren** Du kan distribuera riktade webbklipp som bara kan öppnas i den hanterade webbläsaren på iOS- och Android-enheter. Exempelvis kan du distribuera länkar till företagets resurser via företagsportalen, och när användarna navigerar till länkarna öppnas de direkt i den hanterade webbläsaren där de kan skyddas av MAM-principen. Mer information finns i [Distribuera appar](deploy-apps.md).


- **Hitta, hantera och distribuera Windows Store för företag-appar för Windows 10-enheter från Intune-administratörskonsolen** Stöd för Windows Store för företag finns i Intune, där du får hjälp att hitta, hantera och distribuera appar till Windows 10-enheter som du hanterar. Med Windows Store för företag kan du hantera distributions- och övervakningsprocessen för de här apparna från Intune-administratörskonsolen – samma konsol som du använder för att hantera dina andra appar. Mer specifikt hanterar Windows Store för företag innehållet och licensieringen av ”appar som licensierats online”. Mer information finns i [Hantera appar som du har köpt från Windows Store för företag](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Enhetshantering
- **Distribution av PFX-certifikat för iOS-enheter** Intune-administratörer kan skapa och distribuera iOS PFX-certifikat för Wi-Fi, e-post och VPN-autentisering på iOS-enheter. Den här funktionen finns redan för Android- och Windows 10-enheter. Mer information finns i [Ge åtkomst till företagsresurser med hjälp av certifikatprofiler](secure-resource-access-with-certificate-profiles.md).


- **Använda appar och principer för olika enhetsgrupper baserat på val av användarkategori** Nu kan Intune-administratörer definiera anpassade enhetskategorier som användarna kan välja bland under registreringen. Administratörer kanske exempelvis vill att användarna ska ange om de registrerar en enhet som används för ”kassahantering", "lastbilstransport" eller "inventering". Den valda kategorin gör att enheten blir medlem i en Intune-enhetsgrupp, som kan användas för att distribuera olika appar och principer till den registrerade enheten. Mer information finns i [Kategorisera enheter med mappning av enhetsgruppen](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Ändringar och uppdateringar i Microsofts företagsportal
Följande ändringar har gjorts i företagsportalen i den här versionen.

**Android-företagsportalsapp**

* När användarna startar en app som hanteras av MAM visas ett meddelande som anger att appen hanteras av deras företag. Nu kan användare trycka på länken ”Lär dig mer” för att visa [mer information](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) som förklarar vad ”hanterade appar” är. De kan också trycka på ”Visa inte igen” så att meddelandet inte längre visas när de startar appen.
* Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
* Nu visas registreringsrelaterade felmeddelanden i företagsportalappen. Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.


**iOS-företagsportalappen**
* När användarna startar en app som hanteras av MAM visas ett meddelande som anger att appen hanteras av deras företag. Nu kan användare trycka på länken ”Lär dig mer” för att visa [mer information](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) som förklarar vad ”hanterade appar” är. De kan också trycka på ”Visa inte igen” så att meddelandet inte längre visas när de startar appen.
* Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).
* Nu visas registreringsrelaterade felmeddelanden i företagsportalappen. Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.




## Februari 2016
### Ändringar och uppdateringar i Microsofts företagsportal

Följande ändringar har gjorts i företagsportalen i den här versionen.

#### Android-företagsportalsapp
- Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
- Nu visas registreringsrelaterade felmeddelanden i företagsportalappen. Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.

#### iOS-företagsportalappen
 - Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).

 - Nu visas registreringsrelaterade felmeddelanden i företagsportalappen. Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.


## Januari 2016

### Dra nytta av funktionerna i Windows 10
* **Villkorlig åtkomst med hälsoattesteringstjänsten** Intune-administratörerna kan nu visa status för Windows 10-enheternas hälsotillståndsattestering i Intune Admin-konsolen. Med attestering av enhetens hälsotillstånd kan administratörer se till att klientdatorer har tillförlitliga konfigurationer av BIOS, TPM och startprogram. Klientenheter måste köra Windows 10 med TPM 2 aktiverat för att ha stöd för attestering av hälsotillstånd. Attesteringen av enhetens hälsotillstånd visar antalet enheter som aktiverats för var och en av följande:
    * Tidig lansering av program mot skadlig kod
    * BitLocker
    * Säker start
    * Kodintegritet

    Läs [Introduktion till efterlevnadsprinciper för enheter för Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md) om du vill ha mer information om inställningen för enhetshälsa, insamlade datapunkter och hälsoattesteringsrapporten. [Information om hälsoattesteringstjänsten](https://msdn.microsoft.com/en-us/library/dn934876.aspx) förklarar tjänsten i mer detalj.

* **Windows 10 Passport för arbetsprincip- och certifikathantering** Med Intune kan du [integrera med Microsoft Passport för arbetsplats](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), vilket är en alternativ inloggningsmetod för Windows 10 som använder ett Active Directory- eller Azure Active Directory-konto för att ersätta lösenord, smartkort eller virtuella smartkort. Passport gör det möjligt att använda en användargest för att logga in i stället för ett lösenord. En användargest kan vara en enkel PIN-kod, biometrisk autentisering, t.ex. Windows Hello, eller en extern enhet, t.ex. en fingeravtrycksläsare.

* **VPN för specifika appar** Nu kan välja appar som automatiskt ska ansluta till företagsnätverket via VPN. Skapa listan med appar när du konfigurerar VPN-profilen. Anvisningar finns i Hjälp användarna att ansluta till sitt arbete med hjälp av VPN-profiler med Microsoft Intune.

* **Stöd för fullständig rensning i Windows 10** Nu kan du utfärda en fjärransluten fullständig rensning av Windows 10-skrivbordsenheter registrerade i Intune via Intune-administratörskonsolen. När du kör en fullständig Windows 10-rensning återställs enheten till fabriksinställningarna.


### Uppdatering för Apples volymköpsprogram (VPP, Volume Purchase Program)
Nu kan Intune hjälpa dig att [hantera appar som du har köpt via Apples volymköpsprogram för företag](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Detta innebär bland annat att licensinformation synkroniseras mellan Apple och Intune och att antalet kopior av varje app som du har distribuerat spåras.

### Använd IMEI-nummer för att identifiera företagsägda enheter
Nu kan du identifiera företagsägda mobila enheter genom att [importera IMEI-nummer (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) för plattformar för mobila enheter som har ett IMEI-nummer. När de har registrerats i Intune märks enheter med importerade IMEI-nummer som företagsenheter. Det gör att det går att använda andra principer för dessa enheter än för personliga enheter.

### Nu är fler appar kompatibla med MAM-principer i Intune
Nu är fler appar från Microsofts partner kompatibla med Intunes MAM-principer för hantering av mobilprogram (för enheter som hanteras av Intune):
* Box for EMM (från Box Inc) – endast iOS
* Adobe Reader (från Adobe) – endast Android
* Foxit PDF Reader (från Foxit Corporation) – iOS och Android


### Stödet för IE9 upphör i januari
Från och med februari 2016 kommer Internet Explorer 9 inte längre att stödjas som officiell webbläsare för att komma åt webbplatsen Microsoft Intune-företagsportalen, Intune-kontoportalen och Intune-administratörskonsolen. Du måste migrera till Internet Explorer 10 eller senare.


>[!div class="step-by-step"]

>[&larr; **Nyheter i Intune**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Sep16_HO2-->


