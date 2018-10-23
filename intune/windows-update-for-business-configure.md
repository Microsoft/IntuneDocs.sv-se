---
title: Konfigurera inställningar av Windows Update för företag i Microsoft Intune – Azure | Microsoft Docs
description: Uppdatera inställningarna för programuppdateringar i en profil för att skapa en uppdateringsring, granska kompatibiliteten och pausa uppdateringar i Windows Update för företag-inställningarna med hjälp av Microsoft Intune på Windows 10-enheter.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 6/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: d709681519f2e68d38958d6ec2082b762e22cf60
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425163"
---
# <a name="manage-software-updates-in-intune"></a>Hantera programuppdateringar i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows som tjänst är ett sätt att uppdatera Windows 10-enheter. I Windows 10 innehåller nya funktions- och kvalitetsuppdateringar även innehållet från alla tidigare uppdateringar. Det innebär att om du har installerat den senaste uppdateringen kan du vara säker på att dina Windows 10-enheter är uppdaterade. Till skillnad från vad som var fallet i tidigare versioner av Windows måste du nu installera hela uppdateringen i stället för en del av en uppdatering.

Genom att använda Windows Update för företag förenklar du hanteringen av uppdateringar. Du behöver inte godkänna enskilda uppdateringar för grupper av enheter. Du kan hantera risker i dina miljöer genom att konfigurera en distributionsstrategi för uppdateringen. Med Windows Update blir dessutom uppdateringarna installerade vid rätt tidpunkt. I Microsoft Intune kan du konfigurera uppdateringsinställningar för enheterna och skjuta upp installationen av uppdateringar. Intune lagrar inte uppdateringar, utan enbart uppdateringarnas principtilldelning. Enheter får åtkomst till Windows Update direkt för uppdateringarna. Använd Intune för att konfigurera och hantera **Windows 10-uppdateringstestgrupper**. En uppdateringsring innehåller en grupp med inställningar som anger när och hur uppdateringar av Windows 10 ska installeras. Du kan till exempel konfigurera följande inställningar:

- **Windows 10-underhållskanal**: Välj den underhållskanal som du vill att grupper av enheter ska ta emot uppdateringar från. Följande kanaler är tillgängliga: 
  - Halvårskanal
  - Halvårskanal (riktad)
  - Windows Insider – snabb
  - Windows Insider – långsam
  - Windows Insider-version 
      
  Mer information om tillgängliga underhållskanaler finns i [Översikt för Windows som en tjänst](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels).
- **Inställningar för uppskjutning**: Konfigurera inställningar för uppskjutning av uppdateringar om du vill fördröja uppdateringsinstallationer för grupper av enheter. Använd inställningarna för att mellanlagra uppdateringsdistributionen, så att du kan granska förloppet medan det pågår.
- **Pausa**: Skjut upp installationen av uppdateringar om du upptäcker ett problem någon gång under uppdateringsförloppet.
- **Underhållsperiod**: Konfigurera under vilka timmar som uppdateringar ska kunna installeras.
- **Typer av uppdateringar**: Ange vilka typer av uppdateringar som ska kunna installeras. Exempel: kvalitetsuppdateringar, funktionsuppdateringar och drivrutiner.
- **Installationsbeteende**: Konfigurerar hur uppdateringen installeras. Det kan t.ex. vara om enheten ska startas om automatiskt efter installationen.
- **Peerhämtning**: Du kan välja om du vill konfigurera peerhämtning. Om konfigurerat det och en enhet har slutfört hämtningen av en uppdatering, så kan andra enheter hämta uppdateringen från enheten. Inställningen påskyndar hämtningsprocessen.

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

    Du kan konfigurera den här inställningen manuellt, eller så kan du använda en begränsningsprofil för Intune-enheter för Windows 10 och senare. Det gör du genom att ställa in **Allmänt** > **Diagnostikdata** på minst **Basic**. Mer information om enhetsprofiler finns i [Konfigurera inställningar för enhetsbegränsning](device-restrictions-configure.md).

- Intune-administrationskonsolen innehåller fyra inställningar som styr beteendet för programuppdateringar. De här inställningarna är en del av den allmänna konfigurationsprincipen för Windows 10 Desktop- och Mobile-enheter:
  - **Tillåt automatiska uppdateringar**
  - **Tillåt förhandsfunktioner**
  - **Schemalagd installationsdag**
  - **Schemalagd installationstid**

  Den klassiska Azure-portalen har också ett begränsat antal andra inställningar för Windows 10-uppdateringar i enhetens konfigurationsprofil. Om du har konfigurerat några av dessa inställningar när du migrerade till Azure Portal, rekommenderar vi starkt att du gör följande:

1. Skapa uppdateringsringar för Windows 10 i Azure Portal med de inställningar som du behöver. Inställningen **Tillåt förhandsfunktioner** stöds inte i Azure Portal eftersom den inte kan tillämpas på de senaste Windows 10-versionerna. Du kan konfigurera de övriga tre inställningarna, såväl som andra uppdateringsinställningar för Windows 10, när du skapar uppdateringsringar.

   > [!NOTE]
   > Uppdateringsinställningar för Windows 10 som har skapats i den klassiska portalen visas inte i Azure-portalen efter migreringen. Dessa inställningar tillämpas dock. Om du har migrerat någon av dessa inställningar och redigerat den migrerade principen från Azure Portal, tas inställningarna bort från principen.

2. Ta bort uppdateringsinställningarna i den klassiska portalen. När du har migrerat till Azure Portal och lagt till samma inställningar i en uppdateringsring, måste du ta bort inställningarna i den klassiska portalen för att undvika eventuella principkonflikter. Exempelvis uppstår det en konflikt när samma inställning konfigureras med olika värden. Det finns inte något enkelt sätt att veta detta, eftersom inställningen som konfigureras i den klassiska portalen inte visas i Azure Portal.

## <a name="create-and-assign-update-rings"></a>Skapa och tilldela uppdateringsringar

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj sedan **Microsoft Intune**.
3. Välj **Programuppdateringar** > **Windows 10-uppdateringsringar** > **Skapa**.
4. Ange ett namn, en beskrivning (valfritt) och välj sedan **Konfigurera**.
5. Ange exempelvis följande information i **Inställningar**:

   - **Underhållskanal**: Ange den kanal som enheten tar emot Windows-uppdateringar från.
   - **Microsoft-produktuppdateringar**: Välj om du vill söka efter appuppdateringar i Microsoft Update.
   - **Windows-drivrutiner**: Välj om du vill undanta Windows Update-drivrutiner under uppdateringar.
   - **Funktionssätt för automatisk uppdatering**: Välj hur automatiska uppdateringar installeras, samt om datorn ska startas om. Mer information finns i [Uppdatera/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate).
     - **Frekvens för automatiska funktioner**: Om du väljer alternativet för **automatisk installation och omstart vid schemalagd tid** för uppdateringen så visas den här inställningen. Använd inställningen om du vill schemalägga när uppdateringarna ska installeras, inklusive vecka, dag och tid.

   - **Omstartskontroller**: Aktiverat som standard. När du startar om en enhet utförs vissa kontroller, exempelvis kontroll av aktiva användare, batterinivå, spel som körs och mycket mer. Om du vill hoppa över de här kontrollerna när du startar om en enhet väljer du **Hoppa över**.

   - **Uppskjutningsperiod för kvalitetsuppdatering (dagar)** – Ange i hur många dagar kvalitetsuppdateringar ska skjutas upp. Du kan fördröja mottagandet av dessa kvalitetsuppdateringar i upp till 30 dagar från att de har släppts.

     Kvalitetsuppdateringar utgörs vanligtvis av korrigeringar och förbättringar av befintliga Windows-funktioner och publiceras vanligtvis den första tisdagen varje månad. Men de kan släppas när som helst av Microsoft. Du kan definiera om och hur länge du vill skjuta upp att ta emot kvalitetsuppdateringar efter att de blivit tillgängliga i Windows Update.

   - **Uppskjutningsperiod för funktionsuppdatering (dagar)** – Ange i hur många dagar funktionsuppdateringar ska skjutas upp. Du kan fördröja mottagandet av dessa funktionsuppdateringar i upp till 180 dagar från att de har släppts.

     Funktionsuppdateringarna är för det mesta nya funktioner i Windows. När du har konfigurerat inställningen **Underhållskanal** kan du definiera om och hur lång tid du ska skjuta upp att ta emot funktionsuppdateringar efter att de blivit tillgängliga i Windows Update.

     Till exempel: **Underhållskanalen är inställd på Halvårskanal (riktad) och uppskjutningsperioden är 30 dagar**: Vi tänker oss att funktionsuppdateringen X först blir allmänt tillgänglig i Windows Update som en Halvårskanal (riktad) i januari. Enheten får inte uppdateringen förrän i februari – 30 dagar senare.

     **Underhållskanalen är inställd på Halvårskanal och uppskjutningsperioden är 30 dagar**: Vi tänker oss att funktionsuppdateringen X först blir allmänt tillgänglig i Windows Update som en Halvårskanal (riktad) i januari. Fyra månader senare, i april, släpps funktionsuppdatering X till Halvårskanal. Enheten får funktionsuppdateringen 30 dagar efter det att halvårskanalversionen har släppts och uppdateras därför i maj.

   - **Leveransoptimeringens nedladdningsläge** – Välj den metod som enheterna laddar ner Windows-uppdateringar med. Mer information finns i [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode).

6. När du är klar väljer du **OK**. I **Skapa uppdateringsring** väljer du **Skapa**.

Den nya uppdateringsringen visas i listan över uppdateringsringar.

1. Om du vill tilldela ringen så markera den och välj **Tilldelningar** på fliken <*ringens namn*>.
2. På nästa flik markerar du först **Välj grupper att ta med** och sedan de grupper som du vill tilldela ringen till.
3. När du är klar slutför du tilldelningen genom att markera **Välj**.

## <a name="update-compliance-reporting"></a>Uppdatera efterlevnadsrapportering
Du kan visa uppdateringsefterlevnad i Intune, eller genom att använda en kostnadsfri lösning med namnet Uppdateringsefterlevnad.

### <a name="review-update-compliance-in-intune"></a>Granska uppdateringsefterlevnad i Intune 
<!-- 1352223 --> Granska en principrapport för att se distributionsstatus för de Windows 10-uppdateringstestgrupper du har konfigurerat.

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Programuppdateringar** > **Översikt**. Här kan du se allmän information om status för alla uppdateringsringar som du tilldelade.
4. Öppna någon av följande rapporter:

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

I Intune-konsolen kan du konfigurera det kommersiella ID:t med hjälp av OMA-URI-inställningarna för en anpassad princip. Mer information finns i [Intune-principinställningar för Windows 10-enheter i Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

Den OMA-URI-sökväg (skiftlägeskänslig) du använder när du ska konfigurera det kommersiella ID:t är: ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

Du kan t.ex. använda följande värden i **Lägga till eller redigera OMA-URI-inställningen**:

- **Inställningsnamn**: Windows Analytics Commercial ID
- **Inställningsbeskrivning**: Konfigurera kommersiellt ID för Windows Analytics-lösning
- **OMA-URI** (skiftlägeskänsligt): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Datatyp:** Sträng
- **Värde**: *Använder det GUID som visas på fliken Windows-telemetri på din OMS-arbetsyta*>

![OMA-URI-inställning – Redigera rad](./media/commID-edit.png)

> [!NOTE]
> Mer information om MS DM-server finns i [DMClient-konfigurationsprovider](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="pause-updates"></a>Pausa uppdateringar
Du kan pausa en enhet från att ta emot funktions- eller kvalitetsuppdateringar i upp till 35 dagar från det att du pausar uppdateringarna. Efter det att det maximala antalet dagar har passerat upphör pausfunktionen automatiskt och enheten söker efter tillämpliga uppdateringar på Windows Update. Efter den här sökningen kan du pausa uppdateringarna igen.

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Programuppdateringar** > **Windows 10-uppdateringsringar**.
4. I listan med uppdateringsringar väljer du den ring som du vill pausa. Välj sedan **...** > **Pausa kvalitet** > eller **Pausa funktion**, beroende på vilken typ av uppdateringar som du vill pausa.

> [!IMPORTANT]
> När du utfärdar ett pauskommando får enheterna detta kommando nästa gång de checkar in på tjänsten. Det är möjligt att de, innan de checkar in, installerar en schemalagd uppdatering.
> Om en målenhet har inaktiverats när du utfärdar pauskommandot kan det hända att den hämtar och installerar schemalagda uppdateringar innan den checkar in på Intune.

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>Avinstallera den senaste versionen från programuppdateringar för Windows 10 
Om du upptäcker ett allvarligt problem på dina Windows 10-datorer kan du avinstallera den senaste funktionsuppdateringen eller den senaste kvalitetsuppdateringen. Du kan bara avinstallera en funktions- eller kvalitetsuppdatering via enhetens underhållskanal. Vid avinstallation utlöses en princip för att återställa den tidigare uppdateringen på Windows 10-datorerna. För funktionsuppdateringar specifikt kan du begränsa tiden från 2–60 dagar som en avinstallation av den senaste versionen kan tillämpas. Så här ställer du in alternativ för avinstallation av programvaruuppdatering:

1. I Intune väljer du **Programuppdateringar**.
2. Välj **Windows 10-uppdateringsringar** > välj en befintlig uppdateringsring > **Avinstallera**.

> [!NOTE]
> När kvalitetsuppdateringen har ångrats på Windows 10-datorer fortsätter slutanvändare att se uppdateringen listad i **Windows-inställningar** > **Uppdateringar** > **Uppdateringshistorik**.

## <a name="windows-holographic-for-business-support"></a>Stöd för Windows Holographic for Business

Windows Holographic for Business har stöd för följande inställningar:

- **Beteende för automatisk uppdatering**
- **Uppdateringar för Microsoft-produkter**
- **Underhållskanal**: Stöd för alternativen **Halvårskanal** och **Halvårskanal (riktad)**
