---
title: Inställningar i Windows Update för företag i Microsoft Intune – Azure | Microsoft Docs
description: Inställningar för Windows Update för företag på Windows 10-enheter som du kan distribuera med hjälp av Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f3359bc5544b3a353271ea17083c8c3acb49742
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584457"
---
# <a name="windows-update-settings-for-intune"></a>Windows Update-inställningar för Intune  

Se de Windows 10 Update-inställningar som du kan [konfigurera och hantera](windows-update-for-business-configure.md) med Microsoft Intune.  

När du konfigurerar inställningar för Windows 10-uppdateringsringar i Intune, konfigurerar du inställningar för Windows Update. Om en uppdateringsinställning i Windows har ett beroende i Windows 10-versionen kommer versionsberoendet att anges i inställningarnas information.  

## <a name="update-settings"></a>Uppdateringsinställningar  

Uppdateringsinställningarna styr vilka bitar som en enhet laddar ner och när detta görs. Mer information om beteendet för varje inställning finns i referensdokumentationen för Windows.  

- **Underhållskanal**  
  **Standard**: Halvårskanal  
  Windows Update CSP: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

  Ange den kanal (förgrening) som enheten tar emot Windows-uppdateringar från. Olika kanaler kan använda olika uppskjutningsperioder innan uppdateringarna levereras.  

  Till exempel har *Halvårskanal* en uppskjutningsperiod på sex månader. Om du använder den här kanalen utan ytterligare uppskjutningar i inställningarna installerar enheten uppdateringen sex månader efter att den har släppts.  

  Uppdateringskanaler som stöds:  

  - Halvårskanal  
  - Halvårskanal (riktad)  
  - Windows Insider – snabb  
  - Windows Insider – långsam  
  - Windows Insider-version  

  Om du väljer en Insider-kanal konfigurerar Intune automatiskt Windows uppdateringsinställning [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) så att Insider-versionen kommer att fungera.  


  > [!IMPORTANT]  
  > Från och med Windows version 1903 har användningen av *Halvårskanal (riktad)* (SAC-T) dragits tillbaka. Den här ändringen innebär att SAC-T slås samman med *Halvårskanal*. Mer information om den här förändringen och hur den påverkar Windows Update för företag finns i blogginlägget från Windows IT Pro om [Windows Update för företag och tillbakadragning av SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523).  
 
- **Uppdateringar för Microsoft-produkter**  
  **Standard**: Tillåt  
  Windows Update CSP: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **Tillåt** – Välj *Tillåt* för att söka efter uppdateringar av appen från Microsoft Update.  
  - **Blockera** – Välj block för att förhindra sökning efter uppdateringar av appar.  

- **Windows-drivrutiner**  
  **Standard**: Tillåt  
  Windows Update CSP: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **Tillåt** – Välj *tillåt att* inkludera Windows Update driv rutiner under uppdateringar.  
  - **Blockera** – Välj block för att förhindra genomsökning av driv rutiner.  

- **Uppskjutningsperiod för kvalitetsuppdatering (dagar)**  
  **Standard**: 0  
  Windows Update CSP: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  Ange i hur många dagar från 0 till 30 som kvalitetsuppdateringar ska skjutas upp. Den här perioden är utöver den eventuella uppskjutningsperiod som är en del av underhållskanalen som du valt. Uppskjutningsperioden påbörjas när principen tas emot av enheten.  

  Kvalitetsuppdateringar utgörs vanligtvis av korrigeringar och förbättringar av befintliga Windows-funktioner.  

- **Uppskjutningsperiod för funktionsuppdatering (dagar)**  
  **Standard**: 0  
  Windows Update CSP: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  Ange i hur många dagar funktionsuppdateringar ska skjutas upp. Den här perioden är utöver den eventuella uppskjutningsperiod som är en del av underhållskanalen som du valt. Uppskjutningsperioden påbörjas när principen tas emot av enheten.  

  Uppskjutningsperiod som stöds:  

  - *Windows version 1709 och senare* – 0 till 365 dagar  
  - *Windows version 1703* – 0 till 180 dagar  

  Funktionsuppdateringarna är för det mesta nya funktioner i Windows.  

- **Konfigurera avinstallationsperiod för funktionsuppdatering (2–60 dagar)**  
  **Standard**: 10  
  Windows Update CSP: [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  Konfigurera en tid efter vilken funktionsuppdateringar inte längre kan avinstalleras.  

  När perioden har löpt ut tas den tidigare uppdateringens bitar bort från enheten och det går inte längre att avinstallera till en tidigare uppdateringsversion.  

  Anta exempelvis att en uppdateringsring har en funktionsuppdatering med en avinstallationsperiod på 20 dagar. Efter 25 dagar vill du återställa till den senaste funktionsuppdateringen och du använder alternativet Avinstallera.  Enheter som installerade funktionsuppdateringen för mer än 20 dagar sedan kan inte avinstallera den, eftersom de bitar som krävs har tagits bort vid underhållet. Men enheter som installerade funktionsuppdateringen för upp till 19 dagar sedan kan avinstallera uppdateringen, om de checkar in för att få avinstallationskommandot innan avinstallationsperioden på 20 dagar har löpt ut.  

## <a name="user-experience-settings"></a>Inställningar för användargränssnitt  

Inställningarna för användargränssnittet styr slutanvändarens upplevelse vid omstart av enheten och påminnelser. Mer information om beteendet för varje inställning finns i dokumentationen för Windows Update CSP.  

- **Beteende för automatisk uppdatering**  
  **Standard**: Automatisk installation vid underhållstidpunkt  
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  Välj hur automatiska uppdateringar ska installeras, samt om datorn ska startas om.  

  Alternativ som stöds:  

  - **Meddela om nedladdning** – Meddela användaren innan uppdateringen laddas ned. Användaren väljer att ladda ned och installera uppdateringarna.  

  - **Automatisk installation vid underhållstidpunkt** – Uppdateringar laddas ned automatiskt och installeras vid automatiskt underhåll när enheten inte används eller körs med batteridrift. Om omstart krävs uppmanas användarna att starta om i upp till sju dagar, därefter sker en tvingande omstart.  

    Det här alternativet kan starta om en enhet automatiskt när uppdateringen har installerats. Använd inställningarna för **Aktiva timmar** för att definiera en tidsperiod under vilken de automatiska omstarterna blockeras:  

    - **Aktiva timmar startar**: Ange en starttid för att förhindra omstarter på grund av uppdateringsinstallationer.  
      **Standard**: kl. 08:00  
      Windows Update CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Aktiva timmar slutar**: Ange en sluttid för att förhindra omstarter på grund av uppdateringsinstallationer.  
      **Standard**: kl. 17:00  
      Windows Update CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Installera automatiskt och starta om vid underhåll** – Uppdateringar laddas ned automatiskt och installeras vid automatiskt underhåll när enheten inte används eller körs med batteridrift. När omstart krävs startas enheten om när den inte används. (Detta är standard för ohanterade enheter.)  

    Det här alternativet kan starta om en enhet automatiskt när uppdateringen har installerats. Användningen av inställningar för **Aktiva timmar** beskrivs inte i Windows Update-inställningarna, men används av Intune för att definiera en tidsperiod när de automatiska omstarterna blockeras:  

    - **Aktiva timmar startar**: Ange en starttid för att förhindra omstarter på grund av uppdateringsinstallationer.  
      **Standard**: kl. 08:00  
      Windows Update CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Aktiva timmar slutar**: Ange en sluttid för att förhindra omstarter på grund av uppdateringsinstallationer.  
      **Standard**: kl. 17:00  
      Windows Update CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Automatisk installation och omstart vid schemalagd tid** – Ange dag och tidpunkt för installationen. Om inget anges körs installationen kl. 3.00 varje dag, följt av en 15 minuters nedräkning till en omstart. Inloggade användare kan fördröja nedräkningen och omstarten.   
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    Det här alternativet stöder ytterligare inställningar.  

    - **Frekvens för automatiska funktioner** – Använd den här inställningen om du vill schemalägga när uppdateringarna ska installeras, inklusive vecka, dag och tid.  
      **Standard**: Varje vecka

    - **Schemalagd installationsdag** – Ange den dag i veckan då du vill att uppdateringar ska installeras.  
      **Standard**: Vilken dag som helst  

    - **Schemalagd installationstid** – Ange den tid på dagen då du vill att uppdateringar ska installeras.  
      **Standard**: kl. 03:00  

  - **Installera automatiskt och starta om utan slutanvändarkontroll** – Uppdateringar laddas ned automatiskt och installeras vid automatiskt underhåll när enheten inte används eller körs med batteridrift. När omstart krävs startas enheten om när den inte används. Det här alternativet innebär att slutanvändarnas kontrollpanel är skrivskyddad.  

  - **Återställ till standard** – Återställer de ursprungliga inställningarna för automatisk uppdatering på Windows 10-datorer som kör uppdateringen från oktober 2018 eller senare.  


- **Omstartskontroller**  
  **Standard**: Tillåt  
  Windows Update CSP: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  Om du vill hoppa över de här kontrollerna när du startar om en enhet väljer du **Hoppa över**. 
  
  Den här inställningen ger olika resultat beroende på enhetens Windows-version:  
 
  - *Windows version 1703 och tidigare* – När du startar om en enhet utförs vissa kontroller, exempelvis kontroll av aktiva användare, batterinivå, spel som körs och mycket mer.  
  
  - *Windows version 1709 och senare* – Under aktiva timmar körs inte följande processer för uppdateringar: genomsöka, ladda ned, installera och starta om. Efter aktiva timmar körs uppdateringens processer och kan väcka enheten från strömsparläge, genomsöka, ladda ned, installera och starta om enheten så länge enheten har ström eller batteri. 

- **Blockera användare från att pausa Windows-uppdateringar**  
  **Standard**: Tillåt  
  Windows Update CSP: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **Tillåt** – Tillåt att enhets användare pausar installationen av en uppdatering.  
  - **Blockera** – förhindra att enhets användare pausar installationen av en uppdatering.  

- **Hindra användare från att söka efter Windows-uppdateringar**  
  **Standard**: Tillåt  
  Windows Update CSP: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **Tillåt** – Tillåt att enhets användare använder Windows Update sökning för att hitta och hämta uppdateringar och installera funktioner.
  - **Blockera** – förhindra att enhets användare får åtkomst till Windows Update genomsökning, hämta uppdateringar och installera funktioner.  

- **Kräv användarens godkännande för att starta om utanför arbetstid**  
  **Standard**: Inte konfigurerat  
  Windows Update CSP: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - **Inte konfigurerat**  
  - **Obligatoriskt** – Kräv att användaren godkänner en omstart av enheten utanför arbetstid.  
   
- **Påminn användaren innan automatisk omstart krävs med ignorerbar påminnelse (timmar)**  
  **Standard**: 4  
  Windows Update CSP: [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  Ange lång tid före en automatisk omstart ett ignorerbart meddelande ska visas för enhetsanvändaren om omstarten. Värdena **2**, **4**, **8**, **12** eller **24** timmar stöds.  
  
  När du rensar standardvärdet är den här inställningen *inte konfigurerad*.  

- **Påminn användaren innan automatisk omstart krävs med permanent påminnelse (minuter)**  
  **Standard**: 15  
  Windows Update CSP: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  Ange hur lång tid före en automatisk omstart en icke-ignorerbar varning ska visas för enhetsanvändaren om omstarten. Värdena **15**, **30** eller **60** minuter stöds.  

  När du rensar standardvärdet är den här inställningen *inte konfigurerad*.  

- **Ändra meddelandenivå för uppdatering**  
  **Standard**: Använd standardmässiga Windows Update-meddelanden  
  Windows Update CSP: [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  Ange vilken nivå av Windows Update-meddelanden som användare ser. Den här inställningen styr inte hur och när uppdateringarna laddas ned och installeras.  

  Alternativ som stöds:
  - **Inte konfigurerat**
  - **Använd Windows Update-standardmeddelanden**
  - **Stäng av alla meddelanden, förutom omstarts varningar**
  - **Stäng av alla meddelanden, inklusive omstarts varningar**  

- **Använd inställningar för tids gräns**  
  **Standard**: Inte konfigurerat  
 
  Tillåter att användare använder tids gräns inställningar.  

  - **Inte konfigurerat**
  - **Tillåt**

  När inställningen *tillåts*kan du konfigurera följande inställningar för tids gränser:

  - **Tids gräns för funktions uppdateringar**  
    **Standard**: *Inte konfigurerat*  
    Windows Update CSP: [Update/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    Anger antalet dagar som en användare har innan funktions uppdateringar installeras på deras enheter automatiskt (2-30).

  - **Tids gräns för kvalitets uppdateringar**  
    **Standard**: *Inte konfigurerat*  
    Windows Update CSP: [Update/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    Anger antalet dagar som en användare har innan kvalitets uppdateringar installeras på deras enheter automatiskt (2-30).

  - **Respitperiod**  
    **Standard**: *inte konfigurerat* Windows Update CSP: [Update/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    Anger ett minsta antal dagar efter deadline tills omstarter sker automatiskt (2-7).

  - **Automatisk omstart före deadline**  
    **Standard**: Ja Windows Update CSP: [Update/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    Anger om enheten ska starta om automatiskt före tids gränsen.
    - **Ja**
    - **Nej**

### <a name="delivery-optimization-download-mode"></a>Leveransoptimering av nedladdningsläge  

Leveransoptimering konfigureras inte längre som en del av en Windows 10-uppdateringsring under Programuppdateringar. Leveransoptimering anges nu via enhetskonfiguration. Men tidigare konfigurationer finns kvar i konsolen. Du kan ta bort dessa tidigare konfigurationer genom att ändra dem till inställningen *Inte konfigurerat*, men de kan inte ändras på något annat sätt. 

Information om hur du undviker konflikter mellan ny och gammal princip finns i [Flytta från befintliga uppdateringsringar till leveransoptimering](../configuration/delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization). Flytta sedan dina inställningar till en leveransoptimeringsprofil.
