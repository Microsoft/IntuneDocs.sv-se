---
title: Konfigurera inställningar av Windows Update för företag i Microsoft Intune
titleSuffix: ''
description: Läs om hur du kan konfigurera inställningarna för Windows Update för företag i Microsoft Intune, så att du kan styra uppdateringarna för Windows 10-enheter.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: ac26d0ac1855aa32ef0f00de6a4056bd57c07528
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/17/2018
---
# <a name="manage-software-updates"></a>Hantera programuppdateringar

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Windows som tjänst är ett sätt att uppdatera Windows 10-enheter. Med Windows 10 innehåller nya funktions- och kvalitetsuppdateringar även innehållet från alla tidigare uppdateringar. Det innebär att så länge som du har installerat den senaste uppdateringen så vet du att dina Windows 10-enheter är uppdaterade. Till skillnad från vad som var fallet i tidigare versioner av Windows måste du nu installera hela uppdateringen i stället för en del av en uppdatering.

Med hjälp av Windows Update för företag kan du förenkla hanteringen av uppdateringar så att du inte behöver godkänna varje enskild uppdatering för enhetsgrupperna. Du kan fortfarande hantera risker i dina miljöer genom att konfigurera en strategi för installation av uppdateringar och Windows Update ser till att uppdateringarna installeras vid rätt tidpunkt. Microsoft Intune ger dig möjlighet att konfigurera enheternas inställningar och att skjuta upp installationen av uppdateringar. Intune lagrar inte uppdateringar, utan enbart uppdateringarnas principtilldelning. Enheter får åtkomst till Windows Update direkt för uppdateringarna. Använd Intune för att konfigurera och hantera **Windows 10-uppdateringstestgrupper**. En uppdateringsring innehåller en grupp med inställningar som anger när och hur uppdateringar av Windows 10 updates installeras. Du kan t.ex. konfigurera följande:

- **Underhållskanal för Windows 10**: Välj om du vill att enhetsgrupper ska få uppdateringar från Halvårskanal (riktad) eller från Halvårskanal.  
- **Inställningar för uppskjutning**: Konfigurera inställningar för uppskjutning av uppdateringar om du vill fördröja uppdateringsinstallationer för grupper av enheter. Använd inställningarna för att få en mellanlagrad uppdateringsdistribution så att du kan granska förloppet medan det pågår.
- **Pausa**: Skjut upp installationen av uppdateringar om du upptäcker ett problem någon gång under uppdateringsförloppet.
- **Underhållsperiod**: Konfigurera under vilka timmar som uppdateringar ska kunna installeras.
- **Typer av uppdateringar**: Ange vilka typer av uppdateringar som ska kunna installeras. Exempel: kvalitetsuppdateringar, funktionsuppdateringar och drivrutiner.
- **Installationsbeteende**: Här anger du hur uppdateringen ska installeras. Det kan t.ex. vara om enheten ska startas om automatiskt efter installationen.
- **Peerhämtning**: Du kan ange om du vill konfigurera peerhämtning. Om konfigurerat det och en enhet har slutfört hämtningen av en uppdatering, så kan andra enheter hämta uppdateringen från enheten. Detta påskyndar hämtningen.

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

  Den klassiska portalen har också ett begränsat antal andra inställningar för Windows 10-uppdateringar i enhetens konfigurationsprofil. Om du har konfigurerat några av dessa inställningar i Intune-administratörskonsolen när du migrerade till Azure-portalen rekommenderar vi starkt att du gör följande:

1. Skapa uppdateringsringar för Windows 10 i Azure Portal med de inställningar som du behöver. Inställningen **Tillåt förhandsfunktioner** stöds inte i Azure Portal eftersom den inte kan tillämpas på de senaste Windows 10-versionerna. Du kan konfigurera de övriga tre inställningarna, såväl som andra uppdateringsinställningar för Windows 10, när du skapar uppdateringsringar.

  > [!NOTE]
  > Uppdateringsinställningar för Windows 10 som har skapats i den klassiska portalen visas inte i Azure-portalen efter migreringen. Dessa inställningar fortsätter dock att tillämpas. Om du har migrerat någon av dessa inställningar och redigerat den migrerade principen från Azure Portal, tas dessa inställningar bort från principen.

2. Ta bort uppdateringsinställningarna i den klassiska portalen. Efter det att du har migrerat till Azure Portal och lagt till samma inställningar i en uppdateringsring, så måste du ta bort inställningarna i den klassiska portalen, så att du undviker eventuella principkonflikter. När samma inställning t.ex. har konfigurerats med olika värden uppstår det en konflikt som är svår att upptäcka, eftersom inställningen som har konfigurerats i den klassiska portalen inte visas i Azure-portalen.

## <a name="how-to-create-and-assign-update-rings"></a>Skapa och tilldela uppdateringsringar

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Programuppdateringar** i **Intune**-fönstret.
4. Välj **Hantera** > **Windows 10-uppdateringsringar** i fönstret **Programuppdateringar**.
5. Välj **Skapa** i det fönster som visar listan med uppdateringsringar.
6. Ange ett namn och en valfri beskrivning av uppdateringsringen i fönstret **Skapa uppdateringsring** och välj sedan **Inställningar – Konfigurera**.
7. Konfigurera följande information i fönstret **Inställningar**:
    - **Underhållskanal**: Välj den kanal som enheten får Windows-uppdateringar från (Halvårskanal (riktad) eller Halvårskanal).
    - **Microsoft-produktuppdateringar**: Ange om du vill söka efter appuppdateringar från Microsoft Update.
    - **Windows-drivrutiner**: Ange om du vill exkludera Windows Update-drivrutiner under uppdateringar.
    - **Beteende för automatiska uppdateringar**: Ange hur du vill hantera automatiska uppdateringsbeteenden när det gäller att söka efter, hämta och installera uppdateringar. Mer information finns i [Uppdatera/AllowAutoUpdate](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate).
    - **Uppskjutningsperiod för kvalitetsuppdatering (dagar)** – Ange det antal dagar under vilka kvalitetsuppdateringar ska fördröjas. Du kan fördröja mottagandet av dessa kvalitetsuppdateringar under en period på upp till 30 dagar från det att de har släppts.  

    Kvalitetsuppdateringar utgörs vanligtvis av korrigeringar och förbättringar av befintliga Windows-funktioner, och publiceras vanligtvis den första tisdagen varje månad, men Microsoft kan publicera dem när som helst. Du kan ange om, och hur länge, du vill skjuta upp mottagandet av kvalitetsuppdateringar från det att de har gjorts tillgängliga.

    - **Uppskjutningsperiod för funktionsuppdatering (dagar)** – Ange det antal dagar under vilka funktionsuppdateringar ska fördröjas. Du kan fördröja mottagandet av dessa funktionsuppdateringar under en period på upp till 180 dagar från det att de har släppts.

    Funktionsuppdateringarna är för det mesta nya funktioner i Windows. När du har konfigurerat inställningen **Underhållskanal** (Halvårskanal (riktad) eller Halvårskanal) kan du definiera om, och hur länge, du vill fördröja mottagandet av funktionsuppdateringarna efter det att de gjorts tillgängliga av Microsoft på Windows Update.

    Till exempel: **Om Underhållskanal är inställd på Halvårskanal (riktad) och uppskjutningsperioden är 30 dagar**: Vi tänker oss att funktionsuppdateringen X först blir allmänt tillgänglig i Windows Update som en Halvårskanal (riktad) i januari. Enheten får inte uppdateringen förrän i februari – 30 dagar senare.

    **Om Underhållskanal är inställd på Halvårskanal och uppskjutningsperioden är 30 dagar**: Vi tänker oss att funktionsuppdateringen X först blir allmänt tillgänglig i Windows Update som en Halvårskanal (riktad) i januari. Fyra månader senare, i april, släpps funktionsuppdatering X till Halvårskanal. Enheten får funktionsuppdateringen 30 dagar efter det att den här Halvårskanal-versionen släppts, och den uppdateras i maj.

    - **Leveransoptimeringens nedladdningsläge** – Välj den metod som enheterna ska ladda ner Windows-uppdateringar med. Mer information finns i [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode).
1. När du är klar klickar du först på **OK**. Sedan går du till fönstret **Skapa uppdateringsring** och klickar på **Skapa**.

Den nya uppdateringsringen visas i listan över uppdateringsringar.

1. Om du vill tilldela ringen så markera den och välj **Tilldelningar** på fliken <*ringens namn*>.
2. På nästa flik markerar du först **Välj grupper att ta med** och sedan de grupper som du vill tilldela ringen till.
3. När du är klar slutför du tilldelningen genom att markera **Välj**.

## <a name="update-compliance-reporting"></a>Uppdatera efterlevnadsrapportering
Du kan visa uppdateringsefterlevnad i Intune eller genom att använda en kostnadsfri lösning i Uppdateringsefterlevnad i Operations Management Suite (OMS).

### <a name="review-update-compliance-in-intune"></a>Granska uppdateringsefterlevnad i Intune 
<!-- 1352223 -->
Läs en principrapport för att se distributionsstatus för de Windows 10-uppdateringstestgrupper som du har konfigurerat. 
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Programuppdateringar** i **Intune**-fönstret.
4. I fönstret **Programuppdateringar** väljer du **Översikt**. Här kan du se allmän information om status för alla uppdateringsringar som du tilldelade.
5. Öppna någon av följande rapporter: 
     
   **För alla distributionstestgrupper:**
   1. I fönstret **Programuppdateringar** > **Windows 10-uppdateringsringar**. 
   2. I avsnittet om **övervakning** ska du välja **Distributionsstatus per uppdateringstestgrupp**.
                   
   **För specifika distributionstestgrupper:** 
   1. I fönstret **Programuppdateringar** > **Windows 10-uppdateringsringar** väljer du den distributionsring som du vill granska.
   2. I avsnittet om **övervakning** väljer du bland följande rapporter för att visa mer detaljerad information om uppdateringsringen:
      - **Enhetstillstånd**
      - **Användarstatus**

### <a name="review-update-compliance-using-oms"></a>Granska uppdateringsefterlevnad med OMS
Du kan övervaka uppdateringsdistributioner av Windows 10 genom att använda en kostnadsfria lösningen Update Compliance i Operations Management Suite (OMS). Mer information finns i [Övervaka Windows-uppdateringar med Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor). När du använder den här lösningen kan du distribuera ett kommersiellt ID till någon av dina Intune-hanterade Windows 10 enheter för vilken du vill rapportera uppdateringsefterlevnad.

I Intune-konsolen kan du konfigurera det kommersiella ID:t med hjälp av OMA-URI-inställningarna för en anpassad princip. Mer information finns i [Intune-principinställningar för Windows 10-enheter i Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

Den OMA-URI-sökväg (skiftlägeskänslig) du använder när du ska konfigurera det kommersiella ID:t är: ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID

Du kan t.ex. använda följande värden i **Lägga till eller redigera OMA-URI-inställningen**:

- **Inställningsnamn**: Windows Analytics Commercial ID
- **Inställningsbeskrivning**: Konfigurera kommersiellt ID för Windows Analytics-lösning
- **OMA-URI** (skiftlägeskänsligt): ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID
- **Datatyp:** Sträng
- **Värde**: *Använder det GUID som visas på fliken Windows-telemetri på din OMS-arbetsyta*>

![OMA-URI-inställning – Lägg till rad](./media/commID.png)

## <a name="how-to-pause-updates"></a>Pausa uppdateringar
Du kan pausa en enhet från att ta emot funktions- eller kvalitetsuppdateringar i upp till 35 dagar från det att du pausar uppdateringarna. Efter det att det maximala antalet pausdagar har passerat upphör funktionen automatiskt och enheten söker efter tillämpliga uppdateringar på Windows Update. Efter den här sökningen kan du pausa uppdateringarna igen.
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Programuppdateringar** i **Intune**-fönstret.
4. Välj **Hantera** > **Windows 10-uppdateringsringar** i fönstret **Programuppdateringar**.
5. I det fönster där listan med uppdateringsringar visas, markerar du den ring som du vill pausa. Välj sedan **...**   >  **Pausa kvalitet** > eller **Pausa funktion**, beroende på vilken typ av uppdateringar som du vill pausa.

> [!IMPORTANT]
> När du utfärdar ett pauskommando tar enheterna emot detta kommando nästa gång som de kontaktar tjänsten. Det är möjligt att de, innan de checkar in, installerar en schemalagd uppdatering.
> Om en målenhet har inaktiverats när du utfärdar pauskommandot kan det hända att den hämtar och installerar schemalagda uppdateringar innan den checkar in på Intune.

## <a name="windows-holographic-for-business-support"></a>Stöd för Windows Holographic for Business

Windows Holographic for Business har stöd för följande inställningar:

- **Beteende för automatisk uppdatering**
- **Uppdateringar för Microsoft-produkter**
- **Underhållskanal**