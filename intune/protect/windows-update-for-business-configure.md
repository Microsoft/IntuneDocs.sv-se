---
title: Konfigurera inställningar av Windows Update för företag i Microsoft Intune – Azure | Microsoft Docs
description: Uppdatera inställningarna för programuppdateringar i en profil för att skapa en uppdateringsring, granska kompatibiliteten och pausa uppdateringar i Windows Update för företag-inställningarna med hjälp av Microsoft Intune på Windows 10-enheter.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d34e44c6e046ddbc9b47bbe90900f5992df9e85
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584565"
---
# <a name="manage-software-updates-in-intune"></a>Hantera programuppdateringar i Intune

Du kan använda Intune till att definiera uppdateringsringar som anger hur och när Windows som en tjänst ska uppdatera dina Windows 10-enheter. Uppdateringsringar är principer som du tilldelar till grupper av enheter. Genom att använda uppdateringsringar kan skapa du en uppdateringsstrategi som speglar dina affärsbehov. Mer information finns i [Hantera uppdateringar med hjälp av Windows Update för företag](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

I Windows 10 innehåller nya funktions- och kvalitetsuppdateringar även innehållet från alla tidigare uppdateringar. Det innebär att om du har installerat den senaste uppdateringen kan du vara säker på att dina Windows 10-enheter är uppdaterade. Till skillnad från vad som var fallet i tidigare versioner av Windows måste du nu installera hela uppdateringen i stället för en del av en uppdatering.


Genom att använda Windows Update för företag förenklar du hanteringen av uppdateringar. Du behöver inte godkänna enskilda uppdateringar för grupper av enheter. Du kan hantera risker i dina miljöer genom att konfigurera en distributionsstrategi för uppdateringen. I Intune kan du [konfigurera uppdateringsinställningar](../windows-update-settings.md) för enheterna och skjuta upp installationen av uppdateringar. Intune lagrar inte uppdateringar, utan enbart uppdateringarnas principtilldelning. Enheter får åtkomst till Windows Update direkt för uppdateringarna. Den här samlingen av inställningar som konfigurerar när Windows 10-uppdateringar ska installeras kallas en *Windows 10-uppdateringsring*.

Windows 10-uppdateringsringar har stöd för [omfångstaggar](../fundamentals/scope-tags.md). Du kan använda omfångstaggar med uppdateringsringar för att filtrera och hantera uppsättningar med konfigurationer som du använder.

## <a name="prerequisites"></a>Krav  

Följande krav måste uppfyllas för att Windows-uppdateringar för Windows 10-enheter i Intune ska kunna användas.  

- Windows 10-datorer måste köra Windows 10 Pro eller senare med Windows Anniversary-uppdateringen eller senare (version 1607 eller senare)
- Windows Update stöder följande Windows 10-utgåvor:
  - Windows 10
  - Windows 10 Team (för Surface Hub-enheter)
  - Windows 10 Holographic for Business  

    Windows Holographic for Business har stöd för en delmängd inställningar i Windows-uppdateringar, bland annat:
    - **Beteende för automatisk uppdatering**
    - **Uppdateringar för Microsoft-produkter**
    - **Underhållskanal**: Stöd för alternativen **Halvårskanal** och **Halvårskanal (riktad)** . Mer information finns i [Hantera Windows Holographic](../fundamentals/windows-holographic-for-business.md).  

    > [!NOTE]  
    > **Versioner och utgåvor som inte stöds**:
    > - Windows 10 Mobil  
    > - Windows 10 Enterprise LTSC. Windows Update for Business (WUfB) stöder för närvarande inte versioner av *Långsiktig servicekanal*. Planera att använda alternativa uppdateringsmetoder som WSUS eller Configuration Manager.  

- På Windows-enheter måste du **Feedback och diagnostik** > **Diagnostik och användningsdata** vara inställt på **Grundläggande**, **Utökad** eller **Fullständig**.  

  Du kan konfigurera den här inställningen *Diagnostik och användningsdata* för WIndows 10 manuellt eller använda en begränsningsprofil för Intune-enheter för Windows 10 och senare. Om du använder en enhetsbegränsningsprofil ställer du in [enhetsbegränsningsinställningen](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) för **Dela användningsdata** på minst **Grundläggande**. Den här inställningen finns under kategorin **Rapportering och telemetri** när du konfigurerar en princip för enhetsbegränsning för Windows 10 eller senare.

  Mer information om enhetsprofiler finns i [Konfigurera inställningar för enhetsbegränsning](../configuration/device-restrictions-configure.md).  

- Om du använder den klassiska Azure-portalen [migrerar du dina inställningar till Azure-portalen](#migrate-update-settings-to-the-azure-portal).  


## <a name="create-and-assign-update-rings"></a>Skapa och tilldela uppdateringsringar

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välj **Programuppdateringar** > **Windows 10-uppdateringsringar** > **Skapa**.  

2. På fliken Grundläggande anger du ett namn samt en beskrivning (valfritt) och väljer **Nästa**.  

   ![Skapa arbetsflöde för Windows 10-uppdateringsring](./media/windows-update-for-business-configure/basics-tab.png)

3. På fliken **Inställningar för uppdateringsring** konfigurerar du inställningar för dina företagsbehov. Information om de tillgängliga inställningarna finns i [Inställningar för Windows Update](windows-update-settings.md). När du har konfigurerat inställningar för *Uppdatering* och *Användarupplevelse* väljer du **Nästa**.  

4. På fliken **Omfångstaggar** väljer du **+ Välj omfångstaggar** för att öppna fönstret *Välj taggar* om du vill tillämpa dem på uppdateringsringen.  

   - I fönstret **Välj taggar** väljer du en eller fler taggar och klickar sedan på **Välj** för att lägga till dem i uppdateringsringen och återgå till fönstret *Omfångstaggar*.  

   När du är klar väljer du **Nästa** för att fortsätta till *Tilldelningar*. 

5. På fliken **Tilldelningar** väljer du **+ Välj grupper som ska inkluderas** och tilldelar sedan uppdateringsringen till en eller fler grupper. Använd **+ Välj grupper att utesluta** för att finjustera tilldelningen. Fortsätt genom att välja **Nästa**.  

6. På fliken **Granska och skapa** granskar du inställningarna och väljer **Skapa** när du är redo att spara din Windows 10-uppdateringsring. Din nya uppdateringsring visas i listan över uppdateringsringar.

## <a name="manage-your-windows-10-update-rings"></a>Hantera dina Windows 10-uppdateringsringar

I portalen kan du välja en Windows 10-uppdateringsring för att öppna fönstret **Översikt**. I fönstret kan du se tilldelningsstatus för ringen och vidta ytterligare åtgärder för att hantera den.

### <a name="to-view-an-updates-rings-overview-pane"></a>Visa uppdateringsringar i översiktsfönstret: 

1. Logga in på Azure-portalen.
2. Gå till **Intune** > **Programuppdateringar** > **Windows 10-uppdateringsringar**.
3. Välj den uppdateringsring som du vill visa eller hantera.  

Förutom att se tilldelningsstatus kan du längst upp i översiktsfönstret välja följande åtgärder för att hantera uppdateringsringen:  
- [Ta bort](#delete)  
- [Pausa](#pause)  
- [Återuppta](#resume)  
- [Utöka](#extend)  
- [Avinstallera](#uninstall)  

![Tillgängliga åtgärder](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>Ta bort  

Välj **Ta bort** för att sluta tillämpa inställningarna för den valda Windows 10-uppdateringsringen. När en ring tas bort tas även dess konfiguration bort från Intune, vilket innebär att Intune inte längre tillämpar dessa inställningar.  

Om en ring tas bort från Intune ändras inte inställningarna på enheter som har tilldelats uppdateringsringen.  I stället behåller enheten de aktuella inställningarna. Enheter har inte någon historik över de inställningar som de tidigare hade. Enheter kan också ta emot inställningar från fler uppdateringsringar som är aktiva.  

#### <a name="to-delete-a-ring"></a>Ta bort en ring  

1. När du ser översiktssidan för en uppdateringsring väljer du **Ta bort**.  
2. Välj **OK**.  

### <a name="pause"></a>Pausa  

Välj **Pausa** för att förhindra att tilldelade enheter tar emot funktions- eller kvalitetsuppdateringar i upp till 35 dagar från den tidpunkt då du pausade ringen. Efter det att det maximala antalet dagar har passerat upphör pausfunktionen automatiskt och enheten söker efter tillämpliga uppdateringar på Windows Update. Efter den här sökningen kan du pausa uppdateringarna igen. Om du återupptar en pausad uppdateringsring och pausar den igen, kommer pausperioden att återställas till 35 dagar.  

#### <a name="to-pause-a-ring"></a>Pausa en uppdateringsring  

1. När du ser översiktssidan för en uppdateringsring väljer du **Pausa**.  
2. Välj antingen **Funktion** eller **Kvalitet** för att pausa den typen av uppdatering och välj sedan **OK**.  
3. När du har pausat en uppdateringstyp, kan du välja Pausa igen för att pausa den andra uppdateringstypen.  

När en uppdateringstyp har pausats visar översiktsfönstret för den ringen hur många dagar som återstår innan uppdateringstypen återupptas.

> [!IMPORTANT]  
> När du utfärdar ett pauskommando får enheterna detta kommando nästa gång de checkar in på tjänsten. Det är möjligt att de, innan de checkar in, installerar en schemalagd uppdatering. Om en målenhet har inaktiverats när du utfärdar pauskommandot kan det hända att den hämtar och installerar schemalagda uppdateringar innan den checkar in på Intune.

### <a name="resume"></a>Resume  

När en uppdateringsring har pausats kan du välja **Återuppta** för att aktivera funktions- och kvalitetsuppdateringarna för den ringen. När du har återupptagit en uppdateringsring, kan du pausa den igen.  

#### <a name="to-resume-a-ring"></a>Återuppta en uppdateringsring  

1. När du ser översiktssidan för en pausad uppdateringsring väljer du **Återuppta**.  
2. Välj bland de tillgängliga alternativen för att antingen återuppta **funktions**- eller **kvalitets**uppdateringar och välj sedan **OK**.  
3. När du har återupptagit en uppdateringstyp, kan du välja Återuppta igen för att återuppta den andra uppdateringstypen.  

### <a name="extend"></a>Utöka  

När en uppdateringsring har pausats kan du välja **Utöka** för att återställa pausperioden för både funktions- och kvalitetsuppdateringar för uppdateringsringen till 35 dagar.  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>Utöka pausperioden för en uppdateringsring  

1. När du ser översiktssidan för en pausad uppdateringsring väljer du **Utöka**. 
2. Välj bland de tillgängliga alternativen för att antingen återuppta **funktions**- eller **kvalitets**uppdateringar och välj sedan **OK**.  
3. När du har utökat pausen för en uppdateringstyp kan du välja Utöka igen för att utöka den andra uppdateringstypen.  

### <a name="uninstall"></a>Avinstallera  

Intune-administratörer kan använda **Avinstallera** för att avinstallera (återställa) den senaste *funktions*- eller *kvalitets*uppdateringen för en aktiv eller pausad uppdateringsring. När du har avinstallerat en typ, kan du avinstallera den andra typen. Intune stöder eller hanterar inte användarnas möjlighet att avinstallera uppdateringar.  

> [!IMPORTANT] 
> När du använder alternativet *Avinstallera* skickar Intune denna begäran till enheterna omedelbart. 
> - Windows-enheterna börjar ta bort uppdateringar så snart de får ändringen i Intune-principen. Borttagning av uppdateringen är inte begränsad till underhållsscheman, även om de är konfigurerade som en del av uppdateringsringen. 
> - Om borttagningen av uppdateringen kräver en omstart av enheten, startas enheten om utan att enhetsanvändarna kan välja att senarelägga den.


För att avinstallationen ska lyckas:  
- En enhet måste köra Windows 10 april 2018-uppdateringen (version 1803) eller senare.  

En enhet måste ha installerat den senaste uppdateringen. Eftersom uppdateringar är kumulativa har enheter som installerar den senaste uppdateringen den senaste funktions- och kvalitetsuppdateringen. Ett exempel på när du kan använda det här alternativet för att återställa den senaste uppdateringen är om ett större problem uppstår på dina Windows 10-datorer.  

Tänk på följande när du ska använda Avinstallera:  
- Du kan bara avinstallera en funktions- eller kvalitetsuppdatering via enhetens underhållskanal.  

- Vid avinstallation av funktions- eller kvalitetsuppdateringar utlöses en princip som återställer den föregående uppdateringen på Windows 10-datorerna.  

- När en kvalitetsuppdatering har återställts på Windows 10-datorer, ser slutanvändarna fortfarande uppdateringen i listan **Windows-inställningar** > **Uppdateringar** > **Uppdateringshistorik**.  

- För funktionsuppdateringar specifikt är den tidsperiod då du kan avinstallera funktionsuppdateringen begränsad till mellan 2 och 60 dagar, vilket konfigureras i inställningarna för uppdateringsringarnas uppdatering **Ställ in avinstallationsperiod för funktionsuppdatering (2–60 dagar)** . Du kan inte återställa en funktionsuppdatering som installerades på en enhet längre tid tillbaka än den konfigurerade avinstallationsperioden.  

  Anta exempelvis att en uppdateringsring har en funktionsuppdatering med en avinstallationsperiod på 20 dagar. Efter 25 dagar vill du återställa till den senaste funktionsuppdateringen och du använder alternativet Avinstallera.  Enheter som installerade funktionsuppdateringen för mer än 20 dagar sedan kan inte avinstallera den, eftersom de bitar som krävs har tagits bort vid underhållet. Men enheter som installerade funktionsuppdateringen för upp till 19 dagar sedan kan avinstallera uppdateringen, om de checkar in för att få avinstallationskommandot innan avinstallationsperioden på 20 dagar har löpt ut.  

Mer information om Windows Update-principer finns i [Uppdatera CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) i dokumentationen för Windows-klienthantering.  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>Avinstallera den senaste uppdateringen av Windows 10  

1. När du ser översiktssidan för en pausad uppdateringsring väljer du **Avinstallera**.  
2. Välj bland de tillgängliga alternativen för att antingen avinstallera **funktions**- eller **kvalitets**uppdateringar och välj sedan **OK**.  
3. När du har utlöst avinstallationen för en uppdateringstyp kan du välja Avinstallera igen för att avinstallera den kvarvarande uppdateringstypen.  

## <a name="migrate-update-settings-to-the-azure-portal"></a>Migrera uppdateringsinställningar till Azure-portalen  

Den klassiska Azure-portalen har också ett begränsat antal andra inställningar för Windows 10-uppdateringar i enhetens konfigurationsprofil. Om du har konfigurerat några av dessa inställningar när du migrerade till Azure Portal, rekommenderar vi starkt att utför följande åtgärder:  

1. Skapa uppdateringsringar för Windows 10 i Azure Portal med de inställningar som du behöver. Inställningen **Tillåt förhandsfunktioner** stöds inte i Azure-portalen eftersom den inte längre gäller för senaste Windows 10-versionerna. Du kan konfigurera de övriga tre inställningarna samt de andra uppdateringsinställningar för Windows 10 när du skapar uppdateringsringar.  

   > [!NOTE]  
   > Uppdateringsinställningar för Windows 10 som har skapats i den klassiska portalen visas inte i Azure-portalen efter migreringen. Dessa inställningar tillämpas dock. Om du har migrerat någon av dessa inställningar och redigerat den migrerade principen från Azure Portal, tas inställningarna bort från principen.  

2. Ta bort uppdateringsinställningarna i den klassiska portalen. När du har migrerat till Azure Portal och lagt till samma inställningar i en uppdateringsring, måste du ta bort inställningarna i den klassiska portalen för att undvika eventuella principkonflikter. Exempelvis uppstår det en konflikt när samma inställning konfigureras med olika värden. Det finns inte något enkelt sätt att veta detta, eftersom inställningen som konfigurerats i den klassiska portalen inte visas i Azure-portalen.  

## <a name="next-steps"></a>Nästa steg

[Windows Update-inställningar som stöds av Intune](../windows-update-settings.md)  

[Intune-efterlevnadsrapporter för uppdateringar](../windows-update-compliance-reports.md)

[Felsöka Windows 10-uppdateringsringar](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

