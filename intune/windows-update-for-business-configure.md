---
title: Hantera programuppdateringar
titleSuffix: Configure Windows Update for Business settings - Intune
description: "Läs om hur du kan konfigurera inställningarna för Windows Update för företag i Intune, så att du kan kontrollera uppdateringarna för Windows 10-enheter.”"
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 08/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08f659cf-715e-4e10-9ab2-1bac3c6f2366
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: 6d88fd62b84c0cc7c3678692cef5ab547bfb8c5d
ms.sourcegitcommit: f9b01976c0fc479ac8bc3998eb55bbc517ed2d84
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/22/2017
---
# <a name="manage-software-updates"></a>Hantera programuppdateringar

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Windows som tjänst är ett sätt att uppdatera Windows 10-enheter. Med Windows 10 innehåller nya funktions- och kvalitetsuppdateringar även innehållet från alla tidigare uppdateringar. Det innebär att så länge som du har installerat den senaste uppdateringen så vet du att dina Windows 10-enheter är helt uppdaterade. Till skillnad från vad som var fallet i tidigare versioner av Windows måste du nu installera hela uppdateringen i stället för en del av en uppdatering.

Med hjälp av Windows Update för företag kan du förenkla hanteringen av uppdateringar så att du inte behöver godkänna varje enskild uppdatering för enhetsgrupperna. Du kan fortfarande hantera risker i dina miljöer genom att konfigurera en strategi för installation av uppdateringar och Windows Update ser till att uppdateringarna installeras vid rätt tidpunkt. Microsoft Intune ger dig möjlighet att konfigurera enheternas inställningar och att skjuta upp installationen av uppdateringar. Intune lagrar inte uppdateringar, utan enbart uppdateringarnas principtilldelning. Enheterna har direkt åtkomst till uppdateringarna via Windows Update. Använd Intune för att konfigurera och hantera **Windows 10-uppdateringsringar**. En uppdateringsring innehåller en grupp med inställningar som anger när och hur uppdateringar av Windows 10 updates installeras. Du kan t.ex. konfigurera följande:

- **Windows 10 Servicing Branch**: Ange om du vill grupper av enheter ska ta emot uppdateringar från Current Branch eller Current Branch for Business.  
- **Inställningar för uppskjutning**: Konfigurera inställningar för uppskjutning av uppdateringar om du vill fördröja uppdateringsinstallationer för grupper av enheter. Du kommer då att ha en mellanlagrad uppdateringsdistribution, så att du kan granska förloppet medan det pågår.
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

 Enheter som kör Windows 10 Mobile och Windows 10 Holographic stöds inte.

- På Windows-enheter måste du ställa in **Feedback och diagnostik** > **Diagnostik och användningsdata** på minst **Basic**.

    ![Windows-inställning för diagnostik och användningsdata](./media/telemetry-basic.png)

    Du kan konfigurera den här inställningen manuellt, eller så kan du använda en begränsningsprofil för Intune-enheter för Windows 10 och senare. Det gör du genom att ställa in **Allmänt** > **Diagnostikdata** på minst **Basic**. Mer information om enhetsprofiler finns i [Konfigurera inställningar för enhetsbegränsning](device-restrictions-configure.md).

- Den klassiska Intune-administrationskonsolen innehåller fyra inställningar som styr beteendet för programuppdateringar. De här inställningarna är en del av den allmänna konfigurationsprincipen för Windows 10 Desktop- och Mobile-enheter:
    - **Tillåt automatiska uppdateringar**
    - **Tillåt förhandsfunktioner**
    - **Schemalagd installationsdag**
    - **Schemalagd installationstid**

  Den klassiska konsolen har också ett begränsat antal andra inställningar för Windows 10-uppdateringar i enhetens konfigurationsprofil. Om du har konfigurerat några av dessa inställningar i den klassiska Intune-administratörskonsolen när du migrerar till Azure Portal rekommenderar vi att du gör följande:

1. Skapa uppdateringsringar för Windows 10 i Azure Portal med de inställningar som du behöver. Inställningen **Tillåt förhandsfunktioner** stöds inte i Azure Portal eftersom den inte kan tillämpas på de senaste Windows 10-versionerna. Du kan konfigurera de övriga tre inställningarna, såväl som andra uppdateringsinställningar för Windows 10, när du skapar uppdateringsringar.

  > [!NOTE]
  > Uppdateringsinställningar för Windows 10 som har skapats i den klassiska konsolen visas inte i Azure Portal efter migreringen. Dessa inställningar fortsätter dock att tillämpas. Om du har migrerat någon av dessa inställningar och redigerat den migrerade principen från Azure Portal, tas dessa inställningar bort från principen.

2. Ta bort uppdateringsinställningarna i den klassiska konsolen. Efter det att du har migrerat till Azure Portal och lagt till samma inställningar i en uppdateringsring, så måste du ta bort inställningarna i den klassiska portalen, så att du undviker eventuella principkonflikter. När samma inställning t.ex. har konfigurerats med olika värden, så uppstår det en konflikt som är svår att upptäcka eftersom inställningen som konfigurerats i den klassiska konsolen inte visas i Azure Portal.

## <a name="how-to-create-and-assign-update-rings"></a>Skapa och tilldela uppdateringsringar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Programuppdateringar** på **Intune**-bladet.
4. Välj **Hantera** > **Windows 10-uppdateringsringar** på bladet **Programuppdateringar**.
5. Välj **Skapa** på det blad som visar listan över uppdateringsringar.
6. Ange ett namn och en valfri beskrivning av uppdateringsringen på bladet **Skapa uppdateringsring** och välj sedan **Inställningar**.
7. Konfigurera följande information på bladet **Inställningar**:
    - **Servicing Branch**: Konfigurera den gren för vilken enheten kommer att ta emot Windows-uppdateringar (Current Branch eller Current Branch for Business).
    - **Microsoft-uppdateringar**: Ange om du vill söka efter appuppdateringar från Microsoft Update.
    - **Windows-drivrutiner**: Ange om du vill exkludera Windows Update-drivrutiner under uppdateringar.
    - **Beteende för automatiska uppdateringar**: Ange hur du vill hantera automatiska uppdateringsbeteenden när det gäller att söka efter, hämta och installera uppdateringar. Mer information finns i [Uppdatera/AllowAutoUpdate](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate).
    - **Fördröjningsperiod för kvalitetsuppdateringar (dagar)** – Ange det antal dagar under vilka kvalitetsuppdateringar ska fördröjas. Du kan fördröja mottagandet av dessa kvalitetsuppdateringar under en period på upp till 30 dagar från det att de har släppts.  

    Kvalitetsuppdateringar utgörs vanligtvis av korrigeringar och förbättringar av befintliga Windows-funktioner, och publiceras vanligtvis den första tisdagen varje månad, men Microsoft kan publicera dem när som helst. Du kan ange om, och hur länge, du vill skjuta upp mottagandet av kvalitetsuppdateringar från det att de har gjorts tillgängliga.
    - **Fördröjningsperiod för funktionsuppdateringar (dagar)** – Ange det antal dagar under vilka funktionsuppdateringar ska fördröjas. Du kan fördröja mottagandet av dessa funktionsuppdateringar under en period på upp till 180 dagar från det att de har släppts.

    Funktionsuppdateringarna är för det mesta nya funktioner i Windows. När du har konfigurerat inställningen **Servicing Branch** (**CB** eller **CBB**), kan du definiera om, och hur länge, du vill fördröja mottagandet av funktionsuppdateringarna efter det att de gjorts tillgängliga av Microsoft på Windows Update.

    Exempel:  
    **Om Servicing Branch har ställts in på CB och fördröjningsperioden är 30 dagar**: Anta att funktionsuppdatering X först görs allmänt tillgänglig i Windows Update som en CB i januari. Enheten får inte uppdateringen förrän i februari – 30 dagar senare.

    **Om Servicing Branch har ställts in på CBB och fördröjningsperioden är 30 dagar**: Anta att funktionsuppdatering X först görs allmänt tillgänglig i Windows Update som en CB i januari. Fyra månader senare, i april, släpps funktionsuppdatering X till CBB. Enheten får funktionsuppdateringen 30 dagar efter det att den här CBB-versionen släppts, och den uppdateras i maj.

    - **Leveransoptimering** – Välj den metod för vilken enheterna ska hämta Windows-uppdateringar. Mer information finns i [DeliveryOptimization/DODownloadMode](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#deliveryoptimization-dodownloadmode).
8. När du är klar klickar du först på **OK**, sedan på bladet **Skapa uppdateringsring** och därefter på **Skapa**.

Den nya uppdateringsringen visas i listan över uppdateringsringar.

1. Om du vill tilldela ringen så markera den och välj **Tilldelningar** på fliken <*ringens namn*>.
2. På nästa flik markerar du **Välj grupper** och markerar sedan de grupper för vilka du vill tilldela den här ringen.
3. När du är klar slutför du tilldelningen genom att markera **Välj**.



## <a name="update-compliance-reporting"></a>Uppdatera efterlevnadsrapportering
Du kan övervaka uppdateringsdistributioner av Windows 10 genom att använda en kostnadsfria lösningen Update Compliance i Operations Management Suite (OMS). Mer information finns i [Övervaka Windows-uppdateringar med Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor). När du använder den här lösningen kan du distribuera ett kommersiellt ID till någon av dina Intune-hanterade Windows 10 enheter för vilken du vill rapportera uppdateringsefterlevnad.

I Intune-konsolen kan du konfigurera det kommersiella ID:t med hjälp av OMA-URI-inställningarna för en anpassad princip. Mer information finns i [Intune-principinställningar för Windows 10-enheter i Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

Den OMA-URI-sökväg (skiftlägeskänslig) du använder när du ska konfigurera det kommersiella ID:t är: ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID

Du kan t.ex. använda följande värden i **Lägga till eller redigera OMA-URI-inställningen**:

- **Inställningsnamn**: Windows Analytics Commercial ID
- **Beskrivning av inställning**: Konfigurera kommersiellt ID för Windows Analytics-lösning
- **Datatyp:** Sträng
- **OMA-URI** (skiftlägeskänsligt): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Värde**: *Använder det GUID som visas på fliken Windows-telemetri på din OMS-arbetsyta*>

![Windows-inställning för diagnostik och användningsdata](./media/commID.png)

<!--
1. Sign into the Azure portal.
2. Choose **More Services** > **Monitoring + Management** > **Intune**.
3. On the **Intune** blade, choose **Software Updates**.
4. On the **Software Updates** blade, choose **Overview**. From here you can see general information about the status of any update rings you assigned.
4. On the **Windows 10 Updates** blade, choose **Monitor** > **Update ring deployment for devices**, **Update ring deployment for users**, or **Per-setting deployment state** to view more detailed information about update ring assignments.
-->





## <a name="how-to-pause-updates"></a>Pausa uppdateringar
Du kan pausa en enhet från att ta emot funktions- eller kvalitetsuppdateringar i upp till 35 dagar från det att du pausar uppdateringarna. Efter det att det maximala antalet pausdagar har passerat upphör funktionen automatiskt och enheten söker efter tillämpliga uppdateringar på Windows Update. Efter den här sökningen kan du pausa uppdateringarna igen.
1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Programuppdateringar** på **Intune**-bladet.
4. Välj **Hantera** > **Windows 10-uppdateringsringar** på bladet **Programuppdateringar**.
5. På det blad där listan över uppdateringsringar visas markerar du den ring som du vill pausa och väljer sedan **...**   >  **Pausa kvalitet** > eller **Pausa funktion**, beroende på vilken typ av uppdateringar som du vill pausa.

> [!IMPORTANT]
> När du utfärdar ett pauskommando tar enheterna emot detta kommando nästa gång som de kontaktar tjänsten. Det är möjligt att de, innan de checkar in, installerar en schemalagd uppdatering.
> Om en målenhet har inaktiverats när du utfärdar pauskommandot kan det hända att den hämtar och installerar schemalagda uppdateringar innan den checkar in på Intune.
