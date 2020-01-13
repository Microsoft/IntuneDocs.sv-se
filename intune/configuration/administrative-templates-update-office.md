---
title: Uppdatera Office 365 med administrativa mallar i Microsoft Intune – Azure | Microsoft Docs
description: Använd administrativa mallar i Microsoft Intune när du uppdaterar Office 365-appar till den senaste versionen och välj hur ofta Office ska söka efter uppdateringar. Se vilka enhetsregisternycklar som uppdateras när en Intune-princip tillämpas för Office Update.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63ebbc22c5452c99439d34813509b5652daef1f0
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548099"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>Använd inställningar för Uppdatera kanal och Målversion till att uppdatera Office 365 med Microsoft Intunes administrativa mallar

I Intune kan du använda [Windows 10-mallar till att konfigurera grupprincipinställningar](administrative-templates-windows.md). Den här artikeln visar hur du uppdaterar Office 365 med en administrativ mall i Intune. Du får också vägledning om hur du kontrollerar att dina principer fungerar. Informationen kan även vara till hjälp vid felsökning.

I det här scenariot skapar du en administrativ mall i Intune som uppdaterar Office 365 på dina enheter.

Mer information om administrativa mallar finns i [Windows 10-mallar för att konfigurera grupprincipinställningar](administrative-templates-windows.md).

Gäller för:

- Windows 10 och senare
- Office 365

## <a name="prerequisites"></a>Krav

Kom ihåg att [aktivera automatiska uppdateringar i Office 365 ProPlus](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus) för dina Office-appar. Du kan göra detta med hjälp av en grupprincip eller Intune Office 2016 ADMX-mallen:

![I den administrativa Intune-mallen anger du inställningen Aktivera automatiska uppdateringar för Office](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>Ange uppdateringskanal i den administrativa Intune-mallen

1. I din [administrativa Intune-mall](administrative-templates-windows.md#create-a-template) går du till inställningen för **Uppdatera kanal** och anger den kanal som du vill använda. Välj till exempel `Semi-Annual Channel`:

    ![Ange inställningen Uppdatera kanal för Office i den administrativa Intune-mallen](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > Vi rekommenderar att du uppdaterar oftare. Varje halvår används endast som exempel.

2. Kom ihåg att [tilldela principen](device-profile-assign.md) till dina Windows 10-enheter. Om du vill testa principen tidigare kan du synkronisera principen:

    - [Synkronisera principen i Intune](../remote-actions/device-sync.md)
    - [Synkronisera principen manuellt på enheten](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>Kontrollera Intune-registernycklarna

När du har tilldelat principen och synkroniserat enheten, kan du kontrollera att principen tillämpas:

1. På enheten öppnar du appen **Registereditorn**.
2. Gå till Intune-principens sökväg: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.

    > [!TIP]
    > `<Provider ID>` i registernyckeln ändras. Om du vill hitta provider-ID:t för din enhet öppnar du appen **Registereditorn** och går till `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`. Providerns ID visas.

    När principen tillämpas visas följande registernycklar:

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    I följande exempel ser du att `L_UpdateBranch` har ett värde som liknar `<enabled /><data id="L_UpdateBranchID" value="Deferred" />`. Det här värdet innebär att den är inställd på Halvårskanal:

    ![Exempel på registernyckelns administrativa mall L_Updatebranch](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > I [Hantera Office 365 ProPlus med Configuration Manager](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) visas värdena och vad de innebär. Registervärdena baseras på den valda distributionskanalen:
    >
    >- Månadskanal                - value="Current"
    >- Månadskanal (riktad)     - value="Current"
    >- Halvårskanal            - value="Current"
    >- Halvårskanal (riktad) - value="FirstReleaseDeferred"
    >- Insider – snabbt                   - value="InsiderFast"

I det här läget har Intune-principen tillämpats på enheten.

## <a name="check-the-office-registry-keys"></a>Kontrollera Office-registernycklarna

1. På enheten öppnar du appen **Registereditorn**.
2. Gå till Office-principens sökväg: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`.

    Du ser följande registernycklar:

    - `UpdateChannel`: En dynamisk nyckel som ändras, beroende på de konfigurerade inställningarna.
    - `CDNBaseUrl`: Ange när Office 365 installeras på enheten.

3. Titta på värdet `UpdateChannel`. Värdet visar hur ofta Office uppdateras. I [Hantera Office 365 ProPlus med Configuration Manager](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) visas värdena och vad de är inställda på.

    I följande exempel visas att `UpdateChannel` har angetts till `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`, som är **månadsvis**:

    ![Exempel på registernyckelns administrativa mall UpdateChannel](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    Det här exemplet innebär att principen inte har tillämpats ännu, eftersom den fortfarande är inställd på **månadsvis**, i stället för **halvårsvis**.

Den här registernyckeln uppdateras när **Schemaläggaren** > **Automatiska Office-uppdateringar 2.0** körs, eller när en användare loggar in på enheten. Kontrollera genom att öppna uppgiften **Automatiska Office-uppdateringar 2.0** > **Utlösare**. Beroende på utlösarna kan det ta minst en dag innan `UpdateChannel`-registernyckeln uppdateras.

## <a name="force-office-automatic-updates-to-run"></a>Tvinga att automatiska Office-uppdateringar körs

Du kan forcera principinställningarna på enheten för att testa principen. Följande steg uppdaterar registret. Var alltid försiktig när du uppdaterar registret.

1. Rensa registernyckeln:

    1. Gå till `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates`.
    2. Dubbelklicka på `UpdateDetectionLastRunTime`-nyckeln, ta bort värdedata > **OK**.

2. Kör uppgiften för automatiska Office-uppdateringar:

    1. Öppna appen **Schemaläggaren** på enheten.
    2. Expandera **Bibliotek för Schemaläggaren** > **Microsoft** > **Office**.
    3. Välj **Automatiska Office-uppdateringar 2.0** > **Kör**:

        ![Öppna Schemaläggaren och kör automatiska Office-uppdateringar](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        Vänta tills uppgiften har slutförts, vilket kan ta flera minuter.

3. I appen **Registereditorn** går du till `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`. Kontrollera `UpdateChannel`-värdet.

    Det bör ha uppdaterats med värdet som anges i principen. I vårt exempel ska värdet vara inställt på `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`.

I det här läget har Office Update-kanalen ändrats på enheten. Du kan öppna en Office 365-app för en användare som tar emot uppdateringen för att kontrollera statusen.

## <a name="force-the-office-synchronization-to-update-account-information"></a>Tvinga Office-synkroniseringen att uppdatera kontoinformation  

Om du vill göra mer kan du tvinga Office att hämta den senaste versionsuppdateringen. Följande steg bör bara utföras som en kontroll, eller om enheterna behöver få den senaste versionsuppdateringen från kanalen snabbt. Annars kan du låta Office göra sitt jobb och uppdatera automatiskt.

### <a name="step-1-force-the-office-version-to-update"></a>Steg 1: Tvinga Office-versionen att uppdatera

1. Kontrollera att Office-versionen stöder den uppdateringskanal som du väljer. I [Uppdateringshistorik för Office 365 ProPlus](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date) visas de versionsnummer som stöder de olika uppdateringskanalerna.

2. I din [administrativa Intune-mall](administrative-templates-windows.md#create-a-template) går du till inställningen för **Målversion** och anger den version som du vill använda.

    Inställningen för **Målversion** ser ut ungefär så här:

    ![I den administrativa Intune-mallen anger du inställningen för Office i Målversion](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - Kom ihåg att tilldela principen.
> - Om du ändrar en befintlig princip påverkar ändringarna alla tilldelade användare.
> - Om du testar funktionen rekommenderar vi att du skapar en testprincip och tilldelar principen till en testgrupp med användare.

### <a name="step-2-check-the-office-version"></a>Steg 2: Kontrollera Office-versionen

Du kan använda de här stegen för att testa principen innan du distribuerar den till alla användare.

1. I appen **Registereditorn** går du till `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`

2. Titta på värdet `L_UpdateTargetVersion`. När principen har tillämpats anges värdet som den version du angav, till exempel `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`.

    I det här läget har Intune-principen tillämpats på enheten.

3. Nu kan du tvinga Office att uppdatera. Öppna en Office-app, till exempel Excel. Välj att uppdatera nu (förmodligen i menyn **Konto**).

    Uppdateringen tar flera minuter. Du kan kontrollera att Office försöker hämta den version som du anger:

      1. På enheten går du till `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`.
      2. Öppna filen `VersionDescriptor.xml` och gå till avsnittet `<Version>`. Den tillgängliga versionen ska vara samma version som du angav i Intune-principen, till exempel:

          ![Kontrollera versionsavsnittet i versionsbeskrivningens XML-fil för Office](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. När uppdateringen har installerats bör Office-appen visa den nya versionen (till exempel i menyn **Konto**)

## <a name="next-steps"></a>Nästa steg

[Uppdatera kanalvärden för Office 365-klienter](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel)

[Översikt över molnprinciptjänsten i Office för Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[Använda Windows 10-mallar till att konfigurera grupprincipinställningar (ADMX-mallar) i Microsoft Intune](administrative-templates-windows.md)
