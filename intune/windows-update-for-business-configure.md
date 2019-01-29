---
title: Konfigurera inställningar av Windows Update för företag i Microsoft Intune – Azure | Microsoft Docs
description: Uppdatera inställningarna för programuppdateringar i en profil för att skapa en uppdateringsring, granska kompatibiliteten och pausa uppdateringar i Windows Update för företag-inställningarna med hjälp av Microsoft Intune på Windows 10-enheter.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: d0fcb021545d96fe8f5bfdf742dd4d181c91fb1a
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831572"
---
# <a name="manage-software-updates-in-intune"></a>Hantera programuppdateringar i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows som tjänst är ett sätt att uppdatera Windows 10-enheter. I Windows 10 innehåller nya funktions- och kvalitetsuppdateringar även innehållet från alla tidigare uppdateringar. Det innebär att om du har installerat den senaste uppdateringen kan du vara säker på att dina Windows 10-enheter är uppdaterade. Till skillnad från vad som var fallet i tidigare versioner av Windows måste du nu installera hela uppdateringen i stället för en del av en uppdatering.

Genom att använda Windows Update för företag förenklar du hanteringen av uppdateringar. Du behöver inte godkänna enskilda uppdateringar för grupper av enheter. Du kan hantera risker i dina miljöer genom att konfigurera en distributionsstrategi för uppdateringen. Med Windows Update blir dessutom uppdateringarna installerade vid rätt tidpunkt. I Microsoft Intune kan du konfigurera uppdateringsinställningar för enheterna och skjuta upp installationen av uppdateringar. Intune lagrar inte uppdateringar, utan enbart uppdateringarnas principtilldelning. Enheter får åtkomst till Windows Update direkt för uppdateringarna. Använd Intune för att konfigurera och hantera **Windows 10-uppdateringstestgrupper**. En uppdateringsring innehåller en grupp med inställningar som anger när och hur uppdateringar av Windows 10 ska installeras. Du kan till exempel konfigurera följande inställningar:

- **Underhållskanal för Windows 10**: Välj den underhållskanal som du vill att grupper av enheter ska ta emot uppdateringar från. Följande kanaler är tillgängliga: 
  - Halvårskanal
  - Halvårskanal (riktad)
  - Windows Insider – snabb
  - Windows Insider – långsam
  - Windows Insider-version 
      
  Mer information om tillgängliga underhållskanaler finns i [Översikt för Windows som en tjänst](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels).
- **Inställningar för uppskjutning**: Konfigurera inställningar för uppskjutning av uppdateringar om du vill fördröja uppdateringsinstallationer för grupper av enheter. Använd inställningarna för att mellanlagra uppdateringsdistributionen, så att du kan granska förloppet medan det pågår.
- **Pausa**: Om det inträffar ett problem under uppdateringsdistributionen, kan du senarelägga installationen av uppdateringen. 
- **Underhållsperiod**: Konfigurera under vilka timmar uppdateringar ska kunna installeras.
- **Uppdateringstyp**: Ange vilka typer av uppdateringar som ska kunna installeras. Exempel: kvalitetsuppdateringar, funktionsuppdateringar och drivrutiner.
- **Installationsbeteende**: Konfigurerar hur uppdateringen installeras. Det kan t.ex. vara om enheten ska startas om automatiskt efter installationen.
- **Peer-hämtning**: Du kan välja om du vill konfigurera peer-hämtning. Om konfigurerat det och en enhet har slutfört hämtningen av en uppdatering, så kan andra enheter hämta uppdateringen från enheten. Inställningen påskyndar hämtningsprocessen.

När du har skapat uppdateringsringar tilldelar du dem till enhetsgrupper. Genom att använda uppdateringsringar kan skapa du en uppdateringsstrategi som speglar dina affärsbehov. Mer information finns i [Hantera uppdateringar med hjälp av Windows Update för företag](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="before-you-start"></a>Innan du börjar

- Om du vill uppdatera Windows 10-datorer, måste de köra Windows 10 Pro eller senare med Windows Anniversary-uppdateringen.

- Windows Update stöder följande Windows 10-versioner:
  - Windows 10
  - Windows 10 Team (för Surface Hub-enheter)
  - [Windows Holographic for Business](#windows-holographic-for-business-support)

  Enheter som kör Windows 10 Mobile stöds inte.

- På Windows-enheter måste du ställa in **Feedback och diagnostik** > **Diagnostik och användningsdata** på minst **Basic**.

    ![Windows-inställning för diagnostik och användningsdata](./media/telemetry-basic.png)

    Du kan konfigurera den här inställningen manuellt eller använda en Intune-profil för Windows 10 och senare (**Enhetsbegränsningar** > **Rapportering och telemetri** > Ange **Dela användningsdata** till minst **Grundläggande**). Mer information om enhetsprofiler finns i [Konfigurera inställningar för enhetsbegränsning](device-restrictions-configure.md).

- Den klassiska Azure-portalen har också ett begränsat antal andra inställningar för Windows 10-uppdateringar i enhetens konfigurationsprofil. Om några av dessa inställningar har konfigurerats när du migrerar till Azure-portalen rekommenderar vi starkt att du gör följande:

  1. Skapa uppdateringsringar för Windows 10 i Azure Portal med de inställningar som du behöver. Inställningen **Tillåt förhandsfunktioner** stöds inte i Azure-portalen eftersom den inte längre gäller för senaste Windows 10-versionerna. Du kan konfigurera de övriga inställningarna samt andra uppdateringsinställningar för Windows 10 när du skapar uppdateringsringar.

   > [!NOTE]
   > Uppdateringsinställningar för Windows 10 som har skapats i den klassiska portalen visas inte i Azure-portalen efter migreringen. Dessa inställningar tillämpas dock. Om du har migrerat någon av dessa inställningar och redigerat den migrerade principen från Azure Portal, tas inställningarna bort från principen.

  2. Ta bort uppdateringsinställningarna i den klassiska portalen. När du har migrerat till Azure-portalen och lagt till samma inställningar i en uppdateringsring tar du bort inställningarna i den klassiska portalen för att undvika eventuella principkonflikter. Exempelvis uppstår det en konflikt när samma inställning konfigureras med olika värden. Det finns inte något enkelt sätt att veta detta, eftersom den inställning som konfigureras i den klassiska portalen inte finns i Azure-portalen.

## <a name="create-and-assign-update-rings"></a>Skapa och tilldela uppdateringsringar

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster**, filtrerar på **Intune** och väljer sedan **Microsoft Intune**.
2. Välj **Programuppdateringar** > **Windows 10-uppdateringsringar** > **Skapa**.
3. Ange ett namn, en beskrivning (valfritt) och välj sedan **Konfigurera**.
4. Ange exempelvis följande information i **Inställningar**:  

   **Uppdatera inställningar**  
   - **Underhållskanal**: Ange den kanal som enheten tar emot Windows-uppdateringar från.
   - **Uppdateringar av Microsoft-produkter**: Välj om du vill söka efter appuppdateringar i Microsoft Update.
   - **Windows-drivrutiner**: Välj om du vill undanta Windows Update-drivrutiner under uppdateringarna.
   - **Uppskjutningsperiod för kvalitetsuppdatering (dagar)**: Ange i hur många dagar kvalitetsuppdateringar ska skjutas upp. Du kan fördröja mottagandet av dessa kvalitetsuppdateringar i upp till 30 dagar från att de har släppts.

     Kvalitetsuppdateringar utgörs vanligtvis av korrigeringar och förbättringar av befintliga Windows-funktioner och publiceras vanligtvis den andra tisdagen varje månad. Kvalitetsuppdateringar via Windows Update endast för företag får endast dessa uppdateringar (”B”-versionen), men andra uppdateringar kan släppas när som helst av Microsoft. Du kan definiera om och hur länge du senarelägger mottagandet av kvalitetsuppdateringar efter att de blivit tillgängliga i Windows Update. Mer information finns i [Distribuera uppdateringar med hjälp av Windows Update för företag](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb).

   - **Uppskjutningsperiod för funktionsuppdatering (dagar)**: Ange i hur många dagar funktionsuppdateringar ska skjutas upp. Du kan fördröja mottagandet av dessa funktionsuppdateringar i upp till 180 dagar från att de har släppts.

     Funktionsuppdateringarna är för det mesta nya funktioner i Windows. När du har konfigurerat inställningen **Underhållskanal** definierar du om och hur lång tid du ska senarelägga mottagandet av funktionsuppdateringar efter att de blivit tillgängliga i Windows Update.

     Exempel: **Om underhållskanalen är inställd på Halvårskanal (riktad) och uppskjutningsperioden är 30 dagar**: Vi tänker oss att Funktionsuppdatering X först blir allmänt tillgänglig i Windows Update som en Halvårskanal (riktad) i januari. Enheten får inte uppdateringen förrän i februari – 30 dagar senare.

     **Om underhållskanalen är inställd på Halvårskanal och uppskjutningsperioden är 30 dagar**: Vi tänker oss att Funktionsuppdatering X först blir allmänt tillgänglig i Windows Update som en Halvårskanal (riktad) i januari. Fyra månader senare, i april, släpps funktionsuppdatering X till Halvårskanal. Enheten får funktionsuppdateringen 30 dagar efter det att halvårskanalversionen har släppts och uppdateras därför i maj.  

   **Inställningar för användargränssnitt**
   
   - **Funktionssätt för automatisk uppdatering**: Välj hur automatiska uppdateringar installeras, samt om datorn ska startas om. Mer information finns i [Uppdatera/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate).

     Inställningen *Återställ till standard* återställer de ursprungliga inställningarna för automatisk uppdatering på Windows 10-datorer som kör *oktober 2018-uppdateringen* eller senare.  

     - **Frekvens för automatiska funktioner**: Om du väljer alternativet för **automatisk installation och omstart vid schemalagd tid** för uppdateringen så visas den här inställningen. Använd inställningen om du vill schemalägga när uppdateringarna ska installeras, inklusive vecka, dag och tid.

   - **Omstartskontroller**: Aktiverat som standard. När du startar om en enhet utförs vissa kontroller, exempelvis kontroll av aktiva användare, batterinivå, spel som körs och mycket mer. Om du vill hoppa över de här kontrollerna när du startar om en enhet väljer du **Hoppa över**.

   - **Blockera användare från att pausa Windows-uppdateringar**: Tillåts som standard. Använd den här inställningen för att blockera eller tillåta dina användare att pausa installation av uppdateringar från *inställningarna* på deras datorer. 
      
   - **Leveransoptimering av nedladdningsläge**: Leveransoptimering konfigureras inte längre som en del av en Windows 10-uppdateringsring under Programuppdateringar. Leveransoptimering anges nu via enhetskonfiguration. Men tidigare konfigurationer finns kvar i konsolen. Du kan ta bort dessa tidigare konfigurationer genom att ändra dem till inställningen *Inte konfigurerad*, men de kan inte ändras på något annat sätt. Information om hur du undviker konflikter mellan ny och gammal princip finns i [Flytta från befintliga uppdateringsringar till leveransoptimering](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization). Flytta sedan dina inställningar till en leveransoptimeringsprofil. 

5. När du är klar väljer du **OK**. I **Skapa uppdateringsring** väljer du **Skapa**.

Den nya uppdateringsringen visas i listan över uppdateringsringar.

1. Om du vill tilldela ringen så markera den och välj **Tilldelningar** på fliken <*ringens namn*>.
2. På nästa flik markerar du först **Välj grupper att ta med** och sedan de grupper som du vill tilldela ringen till.
3. När det är klart slutför du tilldelningen genom att välja **Välj**.

## <a name="update-compliance-reporting"></a>Uppdatera efterlevnadsrapportering
Du kan visa uppdateringsefterlevnad i Intune, eller genom att använda en kostnadsfri lösning med namnet Uppdateringsefterlevnad.

### <a name="review-update-compliance-in-intune"></a>Granska uppdateringsefterlevnad i Intune 
<!-- 1352223 --> Granska en principrapport för att se distributionsstatus för de Windows 10-uppdateringstestgrupper du har konfigurerat.

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster**, filtrerar på **Intune** och väljer sedan **Microsoft Intune**.
2. Välj **Programuppdateringar** > **Översikt**. Här kan du se allmän information om status för alla uppdateringsringar som du tilldelade.
3. Öppna någon av följande rapporter:

   **För alla testgrupper för distribution**:  
   1. I **Programuppdateringar** > **Windows 10-uppdateringsringar**
   2. I avsnittet om **övervakning** ska du välja **Distributionsstatus per uppdateringstestgrupp**.

   **För specifika testgrupper för distribution**:  
   1. I **Programuppdateringar** > **Windows 10-uppdateringsringar** väljer du den testgrupp för distribution som du vill granska.
   2. I avsnittet om **övervakning** väljer du bland följande rapporter för att visa mer detaljerad information om uppdateringsringen:
      - **Enhetstillstånd**
      - **Användarstatus**

### <a name="review-update-compliance-using-oms"></a>Granska uppdateringsefterlevnad med OMS
Du kan övervaka uppdateringsdistributioner av Windows 10 genom att använda den kostnadsfria lösningen Uppdateringsefterlevnad. Mer information finns i [Övervaka Windows-uppdateringar med Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor). När du använder den här lösningen kan du distribuera ett kommersiellt ID till någon av dina Intune-hanterade Windows 10 enheter för vilken du vill rapportera uppdateringsefterlevnad.

I Intune kan du konfigurera det kommersiella ID:t med hjälp av OMA-URI-inställningarna för en anpassad princip. Mer information finns i [Intune-principinställningar för Windows 10-enheter i Microsoft Intune](custom-settings-windows-10.md).   

Den OMA-URI-sökväg (skiftlägeskänslig) du använder när du ska konfigurera det kommersiella ID:t är: ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

Du kan t.ex. använda följande värden i **Lägga till eller redigera OMA-URI-inställningen**:

- **Inställningsnamn**: Kommersiellt ID för Windows Analytics
- **Beskrivning av inställning**: Konfigurera kommersiellt ID för Windows Analytics-lösningar
- **OMA-URI** (skiftlägeskänsligt): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Datatyp**: Sträng
- **Värde**: *Använder det GUID som visas på fliken Windows-telemetri på din OMS-arbetsyta*>

![OMA-URI-inställning – Redigera rad](./media/commID-edit.png)

> [!NOTE]
> Mer information om MS DM-server finns i [DMClient-konfigurationsprovider](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="pause-updates"></a>Pausa uppdateringar
Du kan pausa en enhet från att ta emot funktions- eller kvalitetsuppdateringar i upp till 35 dagar från det att du pausar uppdateringarna. Efter det att det maximala antalet dagar har passerat upphör pausfunktionen automatiskt och enheten söker efter tillämpliga uppdateringar på Windows Update. Efter den här sökningen kan du pausa uppdateringarna igen.

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster**, filtrerar på **Intune** och väljer sedan **Microsoft Intune**.
2. Välj **Programuppdateringar** > **Windows 10-uppdateringsringar**.
3. I listan med uppdateringsringar väljer du den ring som du vill pausa. Välj sedan **...** > **Pausa kvalitet** > eller **Pausa funktion**, beroende på vilken typ av uppdateringar som du vill pausa.

> [!IMPORTANT]
> När du utfärdar ett pauskommando får enheterna detta kommando nästa gång de checkar in på tjänsten. Det är möjligt att de, innan de checkar in, installerar en schemalagd uppdatering.
> Om en målenhet har inaktiverats när du utfärdar pauskommandot kan det hända att den hämtar och installerar schemalagda uppdateringar innan den checkar in på Intune.

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>Avinstallera den senaste versionen från programuppdateringar för Windows 10 
Om det inträffar ett allvarligt problem på dina Windows 10-datorer kan du avinstallera den senaste funktionsuppdateringen eller den senaste kvalitetsuppdateringen. Du kan bara avinstallera en funktions- eller kvalitetsuppdatering via enhetens underhållskanal. Vid avinstallation utlöses en princip för att återställa den tidigare uppdateringen på Windows 10-datorerna. För funktionsuppdateringar specifikt kan du begränsa tiden från 2–60 dagar som en avinstallation av den senaste versionen kan tillämpas. Så här ställer du in alternativ för avinstallation av programvaruuppdatering:

1. I Intune väljer du **Programuppdateringar**.
2. Välj **Windows 10-uppdateringsringar** > välj en befintlig uppdateringsring > **Avinstallera**.

> [!NOTE]
> När kvalitetsuppdateringen har ångrats på Windows 10-datorer fortsätter slutanvändare att se uppdateringen listad i **Windows-inställningar** > **Uppdateringar** > **Uppdateringshistorik**.

## <a name="windows-holographic-for-business-support"></a>Stöd för Windows Holographic for Business

Windows Holographic for Business har stöd för följande inställningar:

- **Beteende för automatisk uppdatering**
- **Uppdateringar för Microsoft-produkter**
- **Underhållskanal**: Stöd för alternativen **Halvårskanal** och **Halvårskanal (riktad)**
