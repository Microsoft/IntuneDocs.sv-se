---
title: Inställningar i Windows Update för företag i Microsoft Intune – Azure | Microsoft Docs
description: Inställningar för Windows Update för företag på Windows 10-enheter som du kan distribuera med hjälp av Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ef626523898a8873bde9851664b4ade85c2b0a23
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566547"
---
# <a name="windows-update-settings-for-intune"></a>Windows Update-inställningar för Intune  

Se de Windows 10 Update-inställningar som du kan [konfigurera och hantera](windows-update-for-business-configure.md) med Microsoft Intune.  

När du konfigurerar inställningar för Windows 10-uppdateringsringar i Intune, konfigurerar du inställningar för Windows Update.  Om en uppdateringsinställning i Windows har ett beroende i Windows 10-versionen, kommer versionsberoendet att anges i inställningarnas information.  

## <a name="update-settings"></a>Uppdateringsinställningar  

Uppdateringsinställningarna styr vilka bitar som en enhet laddar ner och när detta görs. Se mer information i referensdokumentationen för Windows om beteendet för varje inställning.  

### <a name="servicing-channel"></a>Underhållskanal  

- **Standard**: Halvårskanal (riktad)  
- **Windows-referensdokumentation**: [uppdatering/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
Ange den kanal (förgrening) som enheten tar emot Windows-uppdateringar från. Olika kanaler kan använda olika uppskjutningsperioder innan uppdateringarna levereras.  

Till exempel har *Halvårskanal* en uppskjutningsperiod på sex månader. Det innebär att om du använder den här kanalen utan ytterligare uppskjutningar i inställningarna, installerar enheten uppdateringen sex månader efter att den har släppts.  

Uppdateringskanaler som stöds:  

- Halvårskanal  
- Halvårskanal (riktad)  
- Windows Insider – snabb  
- Windows Insider – långsam  
- Windows Insider-version  

Om du väljer en Insider-kanal konfigurerar Intune automatiskt Windows uppdateringsinställning [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) så att Insider-versionen kommer att fungera.  


> [!IMPORTANT]  
> Från och med Windows version 1903 har användningen av *Halvårskanal (riktad)* (SAC-T) dragits tillbaka. Den här ändringen innebär att SAC-T slås samman med *Halvårskanal*. Mer information om den här förändringen och hur den påverkar Windows Update för företag finns i blogginlägget från Windows IT Pro om [Windows Update för företag och tillbakadragning av SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523).
 


### <a name="microsoft-product-updates"></a>Uppdateringar av Microsoft-produkter  

- **Standard**: Tillåt
- **Windows-referensdokumentation**: [uppdatering/AllowMUUpdateService](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Välj *Tillåt* om du vill söka efter appuppdateringar i Microsoft Update.    

### <a name="windows-drivers"></a>Windows-drivrutiner  

- **Standard**: Tillåt
- **Windows-referensdokumentation**: [uppdatering/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

Välj *Tillåt* om du vill inkludera Windows Update-drivrutiner vid uppdateringarna

### <a name="quality-update-deferral-period-days"></a>Uppskjutningsperiod för kvalitetsuppdatering (dagar)  

- **Standard**: 0  
- **Windows-referensdokumentation**: [uppdatering/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

Ange i hur många dagar från 0 till 30 som kvalitetsuppdateringar ska skjutas upp. Den här perioden är utöver den eventuella uppskjutningsperiod som är en del av underhållskanalen som du valt. Uppskjutningsperioden påbörjas när principen tas emot av enheten.  

Kvalitetsuppdateringar utgörs vanligtvis av korrigeringar och förbättringar av befintliga Windows-funktioner.  

### <a name="feature-update-deferral-period-days"></a>Uppskjutningsperiod för funktionsuppdatering (dagar)  

- **Standard**: 0  
- **Windows-referensdokumentation**: [uppdatering/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

Ange i hur många dagar funktionsuppdateringar ska skjutas upp. Den här perioden är utöver den eventuella uppskjutningsperiod som är en del av underhållskanalen som du valt. Uppskjutningsperioden påbörjas när principen tas emot av enheten.  
Uppskjutningsperiod som stöds:  

- *Windows version 1709 eller senare*: 0 till 365 dagar  
- *Windows version 1703*: 0 till 180 dagar  

Funktionsuppdateringarna är för det mesta nya funktioner i Windows.  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>Konfigurera avinstallationsperiod för funktionsuppdatering (2–60 dagar)  

- **Standard**: 10  
- **Windows-referensdokumentation**: [uppdatering/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

Konfigurera en tid efter vilken funktionsuppdateringar inte längre kan avinstalleras.  

När perioden har löpt ut tas den tidigare uppdateringens bitar bort från enheten och det går inte längre att avinstallera till en tidigare uppdateringsversion.  

Anta exempelvis att en uppdateringsring har en funktionsuppdatering med en avinstallationsperiod på 20 dagar. Efter 25 dagar vill du återställa till den senaste funktionsuppdateringen och du använder alternativet Avinstallera.  Enheter som installerade funktionsuppdateringen för mer än 20 dagar sedan kan inte avinstallera den, eftersom de bitar som krävs har tagits bort vid underhållet. Men enheter som installerade funktionsuppdateringen för upp till 19 dagar sedan kan avinstallera uppdateringen, om de checkar in för att få avinstallationskommandot innan avinstallationsperioden på 20 dagar har löpt ut.  


## <a name="user-experience-settings"></a>Inställningar för användargränssnitt  

Inställningarna för användargränssnittet styr slutanvändarens upplevelse vid omstart av enheten och påminnelser. Se mer information i referensdokumentationen för Windows om beteendet för varje inställning.  

### <a name="automatic-update-behavior"></a>Funktionssätt för automatisk uppdatering  

- **Standard**: Automatisk installation och omstart vid en schemalagd tidpunkt  
- **Windows-referensdokumentation**: [uppdatera/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

Välj hur automatiska uppdateringar ska installeras, samt om datorn ska startas om.  

Se referensdokumentationen för Windows om du vill ha en fullständig beskrivning av följande alternativ som stöds:  

- **Meddela om nedladdning** – Meddela användaren innan uppdateringen laddas ned. Användaren väljer att ladda ned och installera uppdateringarna.  

- **Automatisk installation vid underhållstidpunkt** – Uppdateringar laddas ned automatiskt och installeras vid automatiskt underhåll när enheten inte används eller körs med batteridrift. Om omstart krävs uppmanas användarna att starta om i upp till sju dagar, därefter sker en tvingande omstart.  

  Det här alternativet kan starta om en enhet automatiskt när uppdateringen har installerats. Använd inställningarna för **Aktiva timmar** för att definiera en tidsperiod under vilken de automatiska omstarterna blockeras:  

  - **Aktiva timmar startar**: Ange en starttid för att förhindra omstarter på grund av uppdateringsinstallationer.  
    **Windows-referensdokumentation**: [uppdatering/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Standard**: 8 AM  
  
  - **Aktiva timmar slutar**: Ange en sluttid för att förhindra omstarter på grund av uppdateringsinstallationer.  
    **Windows-referensdokumentation**: [uppdatering/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Standard**: 17: 00  

- **Installera automatiskt och starta om vid underhåll** – Uppdateringar laddas ned automatiskt och installeras vid automatiskt underhåll när enheten inte används eller körs med batteridrift. När omstart krävs startas enheten om när den inte används. (Detta är standard för ohanterade enheter.)  

  Det här alternativet kan starta om en enhet automatiskt när uppdateringen har installerats. Användningen av inställningar för **Aktiva timmar** beskrivs inte i Windows Update-inställningarna, men används av Intune för att definiera en tidsperiod när de automatiska omstarterna blockeras:  

  - **Aktiva timmar startar**: Ange en starttid för att förhindra omstarter på grund av uppdateringsinstallationer.  
    **Windows-referensdokumentation**: [uppdatering/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Standard**: 8 AM  

  - **Aktiva timmar slutar**: Ange en sluttid för att förhindra omstarter på grund av uppdateringsinstallationer.  
    **Windows-referensdokumentation**: [uppdatering/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Standard**: 17: 00  

- **Automatisk installation och omstart vid schemalagd tid** – Ange dag och tidpunkt för installationen. Om inget anges körs installationen kl. 3.00 varje dag, följt av en 15 minuters nedräkning till en omstart. Inloggade användare kan fördröja nedräkningen och omstarten.  
  
  Det här alternativet stöder ytterligare inställningar.  
  **Windows-referensdokumentation**: [uppdatera/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **Frekvens för automatiska funktioner**: Använd den här inställningen om du vill schemalägga när uppdateringarna ska installeras, inklusive vecka, dag och tid.  
    **Standard**: varje vecka

  - **Schemalagd installationsdag**: Ange vilken dag i veckan som du vill att uppdateringar som installeras.  
    **Standard**: en dag  

  - **Schemalagd installationstid**: anger du tid på dagen då du vill att uppdateringar som installeras.  
    **Standard**: 3: 00  

- **Installera automatiskt och starta om utan slutanvändarkontroll** – Uppdateringar laddas ned automatiskt och installeras vid automatiskt underhåll när enheten inte används eller körs med batteridrift. När omstart krävs startas enheten om när den inte används. Det här alternativet innebär att slutanvändarnas kontrollpanel är skrivskyddad.  

- **Återställ till standard** – Återställer de ursprungliga inställningarna för automatisk uppdatering på Windows 10-datorer som kör uppdateringen från oktober 2018 eller senare.  


### <a name="restart-checks"></a>Omstartskontroller  

- **Standard**: Tillåt  
- **Windows-referensdokumentation**: [uppdatering/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

Den här inställningen ger olika resultat beroende på enhetens Windows-version:  

- Windows version 1703 och tidigare: När du startar om en enhet utförs vissa kontroller, exempelvis kontroll av aktiva användare, batterinivå, spel som körs och mycket mer. Om du vill hoppa över de här kontrollerna när du startar om en enhet väljer du **Hoppa över**.  
- Från och med Windows version 1709: Under aktiva timmar körs inte följande processer för uppdateringar: genomsöka, ladda ned, installera och starta om. Efter aktiva timmar körs uppdateringens processer och kan väcka enheten från strömsparläge, genomsöka, ladda ned, installera och starta om enheten så länge enheten har ström eller batteri. Mer information finns i [Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart).  

### <a name="block-user-from-pausing-windows-updates"></a>Blockera användare från att pausa Windows-uppdateringar  

- **Standard**: Tillåt  
- **Windows-referensdokumentation**: [uppdatering/SetDisablePauseUXAccess](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

Tillåt eller blockera en enhetsanvändare från att pausa installationen av en uppdatering.  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>Kräv användarens godkännande för att starta om utanför arbetstid  

- **Standard**: inte konfigurerat  
- **Windows-referensdokumentation**: [uppdatering/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
Välj *Obligatoriskt* för att kräva att användaren godkänner en omstart av enheten utanför arbetstid.  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>Påminn användaren innan automatisk omstart krävs med ignorerbar påminnelse (timmar)  

- **Standard**: *Detta är inte konfigurerat som standard, och ingen påminnelse visas för användarna*.  
- **Windows-referensdokumentation**: [uppdatering/ScheduleRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

Ange lång tid före en automatisk omstart ett ignorerbart meddelande ska visas för enhetsanvändaren om omstarten. Värdena **2**, **4**, **8**, **12** eller **24** timmar stöds.  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>Påminn användaren innan automatisk omstart krävs med permanent påminnelse (minuter)  

- **Standard**: *Detta är inte konfigurerat som standard, och ingen påminnelse visas för användarna*.  
- **Windows-referensdokumentation**: [uppdatering/ScheduleImminentRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

Ange hur lång tid före en automatisk omstart en icke-ignorerbar varning ska visas för enhetsanvändaren om omstarten. Värdena **15**, **30** eller **60** minuter stöds.  
 
### <a name="allow-user-to-restart-engaged-restart"></a>Tillåt användaren att starta om (interaktiv omstart)  

- **Standard**: inte konfigurerat  
- **Windows-referensdokumentation**: *ej tillämpligt*  
- **Windows-version**: stöd för Windows 10 version 1803 och senare  

  > [!NOTE]  
  > I Windows 10 version 1809 har ytterligare interaktiva omstartsinställningar införts, vilket gör att olika inställningar kan tillämpas på funktions- och kvalitetsuppdateringar. Dock tillämpas de inställningar som hanteras av Intune inte separat på de olika uppdateringstyperna. I stället använder Intune samma värden för både funktions- och kvalitetsuppdateringar.  

När värdet är **Obligatoriskt** kan du aktivera användningen av interaktiva omstartsalternativ för Windows 10-uppdateringar. Dessa alternativ hjälper enhetsanvändaren med hanteringen när en enhet ska startas om efter att en uppdatering har installerats som kräver en omstart.  

Mer information om det här alternativet finns i [Interaktiv omstart](https://docs.microsoft.com/en-us/windows/deployment/update/waas-restart#engaged-restart) i Windows 10-dokumentationen om att distribuera uppdateringar.  

Följande inställningar används för att styra när interaktiv omstart ska utföras.  

- **Övergång av användare till interaktiv omstart efter en automatisk omstart (dagar)**  
  - **Standard**: Som standard är detta inte konfigurerat, men det finns stöd för ett värde från **2** till **30**.  
  - **Windows-referensdokumentation**: [uppdatering/EngagedRestartTransitionSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  Ange hur lång tid det tar efter att uppdateringen har installerats tills enheten försätts i ett interaktivt omstartsbeteende. Användarna får en uppmaning om att starta om enheten efter det konfigurerade antalet dagar.  

- **Snooza påminnelse om interaktiv omstart (dagar)**  
  - **Standard**: Som standard är detta inte konfigurerat, men det finns stöd för ett värde från **1** till **3**.  
  - **Windows-referensdokumentation**: [uppdatering/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  Ange hur länge en omstartsfråga kan snoozas.  Efter snooze-perioden visas omstartsfrågan igen. Användaren kan fortsätta att snooza påminnelsen tills tidsgränsen har uppnåtts.  

- **Ställ in tidsgräns för väntande omstarter (dagar)**  
  - **Standard**: Som standard är detta inte konfigurerat, men det finns stöd för ett värde från **2** till **30**.  
  - **Windows-referensdokumentation**: [uppdatering/EngagedRestartDeadline](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  Ange maximalt antal dagar man kan vänta efter att ett interaktivt omstartsbeteende har påbörjats innan en enhet tvingas till en obligatorisk omstart. Omstarten uppmanar användarna att spara arbetet

### <a name="delivery-optimization-download-mode"></a>Leveransoptimering av nedladdningsläge  

- **Standard**: ej tillämpligt
- **Windows-referensdokumentation**: *ej tillämpligt*

Leveransoptimering konfigureras inte längre som en del av en Windows 10-uppdateringsring under Programuppdateringar. Leveransoptimering anges nu via enhetskonfiguration. Men tidigare konfigurationer finns kvar i konsolen. Du kan ta bort dessa tidigare konfigurationer genom att ändra dem till inställningen *Inte konfigurerad*, men de kan inte ändras på något annat sätt. 

Information om hur du undviker konflikter mellan ny och gammal princip finns i [Flytta från befintliga uppdateringsringar till leveransoptimering](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization). Flytta sedan dina inställningar till en leveransoptimeringsprofil.


