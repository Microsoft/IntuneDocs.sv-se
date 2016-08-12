---
title: "Vad är nytt | Microsoft Intune"
description: "Ta reda på vad är nytt den här månaden och i tidigare versioner av Microsoft Intune"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 68af4d7f0b082f14e6f9c06f8739805f9590384e
ms.openlocfilehash: 64bd2e3c8e8da3949634a544eb2c582e889c8209


---

# Nyheter i Microsoft Intune
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Augusti 2016
## Uppdateringar av företagsportalen

### Android
- **Android-företagsportalsapp**<br/>
Intune-företagsportalappen för Android stödjer "day 0" för det kommande Android 7.0-operativsystemet för mobila enheter.  

- **Googles borttagning av funktionen för fjärråterställning av lösenord på Android 7.0-enheter**<br/>
På Android 7.0-enheter kan Intunes IT-administratörer och slutanvändare inte fjärråterställa enhetens lösenord eftersom Google har tagit bort den här funktionen för Android 7.0-enheter. För tidigare versioner än Android 7.0 kan IT-administratörer fortfarande fjärråterställa en användares lösenord, och slutanvändarna kan fortfarande återställa sina lösenord från företagsportalens webbplats.

## Juli 2016
## Apphantering
### Förbättra uppdateringsupplevelsen för appetableringsprofiler
Verksamhetsspecifika Apple iOS-appar skapas med en inbyggd etableringsprofil och kod som signeras med ett certifikat. När appen körs på en iOS-enhet bekräftar iOS appens integritet och tillämpar de principer som definierats av etableringsprofilen.

Signeringscertifikatet du använder för att signera appar gäller normalt i 3 år. Däremot upphör etableringsprofilen att gälla efter ett år. Med den här uppdateringen tillhandahåller Intune verktyg för att distribuera en ny etableringsprofilprincip till enheter som har appar som snart slutar att gälla medan certifikatet fortfarande är giltigt. Mer information finns i [Använda etableringsprofilprinciper för iOS för att hålla verksamhetsspecifika appar uppdaterade](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->
### Xamarin SDK för Intune-appar är tillgängligt
Med komponenten Intune App SDK Xamarin kan du aktivera funktioner för hantering av mobilappar med Intune i iOS- och Android-appar som utvecklats med Xamarin. Komponenten hittar du i [Xamarin store](https://components.xamarin.com/view/Microsoft.Intune.MAM) eller på [Github-sidan för Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

## Enhetshantering
### Höjd gräns för enhetsregistrering
Intune har ökat maxgränsen för enhetsregistrering från 5 till 15 enheter per användare.
<!---TFS 1289896 --->

### TeamViewer-integrering för Windows-datorer med Intune-klientprogramvaran
Med [TeamViewer](https://www.teamviewer.com)-integrering för Windows-datorer som kör Intune-klienten kan du etablera fjärrhjälpssessioner med Windows-datorer, vilket underlättar supportavdelningens arbete. Detta gäller Windows 7, 8, 8.1 och Windows 10. Mer information finns i [Vanliga hanteringsuppgifter för Windows-datorer med Microsoft Intune-datorklienten](intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

## Uppdateringar av företagsportalen
### Företagsportalens webbplats
- **Förbättrad användarupplevelse vid registrering av Windows-enheter**<br/>
När du använder villkorlig åtkomst har registreringsanvisningarna för Windows 8.1, Windows 10 Desktop och Windows 10 Mobile förenklats på företagsportalens webbplats. Nu visas separata steg för ”enhetsregistrering” och ”anslutning till arbetsplatsen”, vilket gör det lättare att se status för enheterna och slutföra processen om användarna inte lyckas ansluta till arbetsplatsen. De separata stegen förväntas också underlätta felsökningen för IT-administratörer. När slutanvändarna försökte registrera en enhet och alla steg lyckades utom anslutningen till arbetsplatsen visades inte den registrerade enheten i listan med enheter som användarna skulle identifiera, vilket orsakade förvirring för användarna.

### Android
- **Android-företagsportalsapp**<br/>
Om Android-användarna ser ett felmeddelande om att enheten saknar ett nödvändigt certifikat kan de trycka på ”Så här löser du problemet” och få [anvisningar](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) om hur de installerar certifikatet som saknas. Om användarna slutför stegen men får ett felmeddelande om att ”certifikat saknas” ombeds de kontakta IT-administratören och ange den här [länken](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues) som innehåller anvisningar som IT-administratörer kan använda för att åtgärda certifikatproblem.

- **Begränsa appinstallation med separat inläsning till registrerade enheter**<br/>
Det går inte längre att installera program på Android-enheter via företagsportalens webbplats om de inte har registrerats i Intune via Intune-företagsportalappen för Android.
<!---TFS 1299082--->

### iOS
- **Ändringar av konton för enhetsregistreringshanterare i iOS-företagsportalappen**<br/>
För att förbättra prestanda och skalning visar Intune inte längre alla enheter i Enhetsregistreringshanteraren (DEM) i fönstret **Mina enheter** i företagsportalappen för iOS. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen.

    DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen. Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter.

    Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt. Mer information finns i [Registrera företagsägda enheter med Enhetsregistreringshanteraren i Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

## Ändrade namn på Windows-funktioner
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) heter numera **Windows Hello för företag**.
- [Företagsdataskydd](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) kallas nu **Windows informationsskydd**.

## Kommande nyheter
### Intune-grupper övergår till Azure Active Directory-grupper i början av augusti 2016
Intune får en ny grupphantering med ADD-säkerhetsgrupper (Azure Active Directory). Dessa grupper kan innehålla både användare och enheter och kommer att användas för all grupphantering, principdistribution och profildistribution när vi introducerar den nya Azure-baserade Intune-administratörsportalen.

Den nya hanteringen gör att:
- du inte behöver duplicera grupper mellan tjänster
- du får tillgång till AADP-gruppfunktioner (Azure Active Directory Premium)
- du kan utöka med PowerShell och Graph
- du får en mer enhetlig grupphantering för mobilitetshanteringen i företaget.

För att kunna övergå till säkerhetsgrupper krävs några ändringar i den aktuella administratörskonsolen. Information om dessa ändringar, och användning av Azure AD-säkerhetsgrupper, kommer att läggas till i Intune-dokumentationen.

Nya Intune-användare kommer att se vissa av ändringarna före befintliga klienter.

Förutom ändringarna i grupphantering kommer följande funktion att bli inaktuell:
- Exkludera medlemmar eller grupper när du skapar en ny grupp
- Grupperna **Användare utan grupp** och **Enheter utan grupp**
- **Hantera grupper** i rollen tjänstadministratör
- Anpassade gruppbaserade aviseringar för aviseringsregler
- Pivotering med grupper i rapporter

Mer information om hur dessa utfasningar kan hanteras släpps i augusti.

### Tillägg av Meddelanden på företagsportalen för Android
Vi publicerar en uppdatering av företagsportalen för Android i september där vi lägger till en ny **Meddelanden**-ikon på startsidan. När användaren trycker på ikonen visas sidan **Meddelanden**. På sidan visas alla objekt som kräver åtgärder i företagsportalappen, till exempel inkompatibla enheter, registreringsuppdatering och aktivering av registreringar. Om du också använder företagsportalappen för iOS kan du redan se dessa meddelanden. När sidan **Meddelanden** läggs till kommer sidan **Konfiguration av företagsåtkomst** inte att visas varje gång du startar eller återupptar företagsportalen för Android, förutsatt att enheten redan är registrerad. Vi vet att många av er har skapat instruktioner till användarna och uppskattar att få veta på förhand när era instruktioner/skärmbilder behöver uppdateras. Uppdatera din dokumentation med de kommande ändringarna. Om du behöver nya skärmbilder kan du gå till https://aka.ms/androidcpupdate.  



### Moln-översikt
Håll dig informerad om Intunes utveckling i [översikten över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Tjänstens utfasning
- **Ändringar i stödet för iOS-företagsportalappen**<br/>
I september krävs det av alla användare att de använder den senaste versionen av Microsoft Intune-företagsportalappen för iOS. Nya användare kommer bara att kunna hämta den senaste versionen och aktuella användare kommer att behöva uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.  

- **Lägsta version för Managed Browser (iOS) har ändrats till 8.0**<br/>
I augusti släpper Intune en uppdaterad Microsoft Intune Managed Browser-app för iOS som bara stöder enheter som kör iOS 8.0 eller senare. Enheter som kör iOS 7.1 kan fortfarande använda Managed Browser-appen, men uppmana ändå användarna att uppdatera till iOS 8.0 eller senare så att de får åtkomst till och kan dra full nytta av de nya funktionerna i Managed Browser.  
<!---TFS 1313253--->

- **Företagsportalappar för Windows 8 och Windows Phone 8 blir inaktuella från september 2016** <br/>
Med början i september 2016 upphör Microsoft Intunes stöd för appar i Microsoft Intune-företagsportalappen för Windows Phone 8- och Windows 8-plattformarna. Uppdatera enheter till Windows 8.1 och Windows Phone 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1 om du vill fortsätta att distribuera appar till dessa enheter.
<!---TFS 1255391--->

- **Intune Viewer-appar** <br/>
Med versionen av den nya RMS-delningsappen tar vi bort följande Intune Viewer-appar, med början från augusti 2016:
    - Intune AV Viewer
    - Intune PDF Viewer
    - Intune Image Viewer för Android från Google Play

  I stället för att använda Intune Viewer-appar bör du använda den nya [Rights Management-appen (RMS-delning) för Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. När Intune Viewer-appen inte längre stöds tas den bort från Google Store och är inte längre tillgänglig för framtida bruk.

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



## Tidigare versioner av Intune
Information om det senaste halvårets nyheter i Intune finns i artikeln [Tidigare Intune-versioner](previous-intune-releases.md).

### Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Aug16_HO2-->


