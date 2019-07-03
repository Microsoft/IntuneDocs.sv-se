---
title: Tilldela Office 365-appar till Windows 10-enheter med hjälp av Microsoft Intune
titleSuffix: ''
description: Lär dig hur du kan använda Microsoft Intune för installera Office 365-appar på Windows 10-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 095c2ee0aba0680de0c5fc55c1406dba41111b92
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67527439"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune

Innan du kan tilldela, övervaka, konfigurera eller skydda appar måste du lägga till dem till Intune. En av de tillgängliga [apptyperna](apps-add.md#app-types-in-microsoft-intune) är Office 365-appar för Windows 10-enheter. Genom att välja den här apptypen i Intune kan du tilldela och installera Office 365-appar på enheter som du hanterar och som kör Windows 10. Du kan även tilldela och installera appar för skrivbordsklienten för Microsoft Project Online och Microsoft Visio Online, abonnemang 2 om du har licenser för dessa. De tillgängliga Office 365-apparna visas som en enda post i listan med appar i Intune-konsolen i Azure.

> [!NOTE]
> Du måste använda Office 365 ProPlus-licenser för att kunna aktivera de Office 365 ProPlus-appar som distribueras via Microsoft Intune. Office 365 Business Edition stöds för närvarande inte av Intune.

## <a name="before-you-start"></a>Innan du börjar

> [!IMPORTANT]
> Om det finns .msi Office-appar på slutanvändarens enhet måste du använda funktionen **Ta bort MSI** för att avinstallera de här apparna på ett säkert sätt. Annars kommer det inte gå att installera de Office 365-appar som levereras via Intune.

- Enheterna måste köra Windows 10 Creators Update eller senare.
- Intune har endast stöd för att lägga till Office-appar från Office 365.
- Om alla Office-program är öppna när Intune installerar appen kan installationen misslyckas och användare kan förlora data från filer som inte sparats.
- Den här installationsmetoden stöds inte på Windows 10S-, Windows Home-, Windows Team-, Windows Holographic- eller Windows Holographic for Business-enheter.
- Intune stöder inte installation av Office 365-skrivbordsappar från Microsoft Store (kallas även Office Centennial-appar) på en enhet som du redan har distribuerat Office 365-appar till med Intune. Om du installerar den här konfigurationen kan det orsaka dataförlust eller skadade data.
- Många obligatoriska eller tillgängliga apptilldelningar är inte additiva. En senare tilldelning av en app överskriver de befintliga installerade apptilldelningarna. Om den första uppsättningen Office-program innehåller Word och den senare inte gör det så kommer exempelvis Word att avinstalleras. Detta tillstånd gäller inte för Visio- eller Project-program.
- **Office-version** – Välj om du vill tilldela 32-bitars- eller 64-bitarsversionen av Office. Du kan installera 32-bitarsversionen på enheter med 32-bitar och 64-bitar, men du kan bara installera 64-bitarsversionen på 64-bitarsenheter.
- **Ta bort MSI från slutanvändarenheter** – Välj om du vill ta bort befintliga Office .MSI-appar från slutanvändarenheter. Installationen kommer inte lyckas om det finns redan befintliga .MSI-appar på slutanvändarenheter. Apparna som ska avinstalleras är inte begränsade till de appar som valts för installation i **Konfigurera appsviten**, utan alla Office-appar (MSI) tas bort från slutanvändarens enhet. Mer information finns i [Ta bort befintliga MSI-versioner av Office vid uppgradering till Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). När Intune installerar om Office på slutanvändarnas datorer får användarna automatiskt samma språkpaket som de hade med tidigare .MSI Office-installationer.

## <a name="get-started"></a>Kom igång

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Klientappar** i **Intune**-fönstret.
4. I arbetsbelastningsfönstret **Klientappar** väljer du **Appar** under **Hantera**.
5. Välj **Lägg till**.
6. I fönstret **Lägg till appar** i listan **Apptyp** under **Office 365-paket** väljer du **Windows 10**.

## <a name="select-settings-format"></a>Välja inställningsformat

Du kan välja en metod för att konfigurera appinställningen genom att välja ett **inställningsformat**. Alternativen för inställningsformat omfattar:
- Configuration Designer
- Ange XML-data

När du väljer **Configuration Designer** ändras bladet **Lägg till app** till att erbjuda ytterligare två alternativ för inställningar:
- Konfigurera appsvit
- Inställningar för appsvit

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

När du väljer **Ange XML-data** visar bladet **Lägg till app** alternativet **Ange XML-data**. Välj det här om du vill visa bladet **Konfigurationsfil**. 

![Lägga till Office 365 Configuration Designer](./media/apps-add-office365/apps-add-office365-01.png)
    
Mer information om alternativet **Ange XML-data** finns i [Ange XML-data](apps-add-office365.md#enter-xml-format) nedan.

## <a name="configure-app-suite-information"></a>Information om att konfigurera appsvit

I det här steget anger du information om appaketet. Den här informationen hjälper dig att identifiera appsviten i Intune och hjälper användarna att hitta appsviten det i företagsportalappen.

1. Välj **Information om appsvit** i fönstret **Lägg till app**.
2. I fönstret **Information om appsvit** gör du följande:
    - **Namn på programsvit**: Ange namnet på appsviten så som det visas i företagsportalen. Kontrollera att alla svitnamn du använder är unika. Om samma paketnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Beskrivning av programsvit**: Ange en beskrivning av appsviten. Exempelvis kan du visa de appar som ingår.
    - **Utgivare**: Microsoft visas som utgivare.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Inställningen gör det enklare för användarna att hitta appaketet när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Välj det här alternativet för att tydligt visa appsviten på företagsportalens huvudsida när användarna söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Microsoft visas som utvecklare.
    - **Ägare**: Microsoft visas som ägare.
    - **Kommentarer**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp**: Office 365-logotypen visas med appen när användarna söker på företagsportalen.
3. Välj **OK**.

## <a name="configure-app-suite"></a>Konfigurera appsvit

Om du valde alternativet **Configuration Designer** i listrutan **Inställningsformat** visas alternativet **Konfigurera appsvit** på bladet **Lägg till app**. Välj de Office-appar som du vill tilldela till enheter.

1. I fönstret **Lägg till app** väljer du **Konfigurera appsvit**.
2. I fönstret **Konfigurera appsvit** väljer du de standard-Office-appar som du vill tilldela till enheter.  
    Dessutom kan du installera appar för skrivbordsklienten för Microsoft Project Online och Microsoft Visio Online, abonnemang 2 om du har licenser för dessa.
3. Välj **OK**.

## <a name="configure-app-suite-settings"></a>Konfigurera inställningar för appsvit

Om du valde alternativet **Configuration Designer** i listrutan **Inställningsformat** visas alternativet **Inställningar för appsvit** på bladet **Lägg till app**. Konfigurera installationsalternativ för app-paket i det här steget. Inställningarna tillämpas på alla appar som du har lagt till i serien.

1. Välj **Inställningar för appsvit** i fönstret **Lägg till app**.
2. I fönstret **Inställningar för appsvit** gör du följande:
    - **Office-version**: Välj om du vill tilldela 32-bitars- eller 64-bitarsversionen av Office. Du kan installera 32-bitarsversionen på enheter med 32-bitar och 64-bitar, men du kan bara installera 64-bitarsversionen på 64-bitarsenheter.
    - **Uppdatera kanal**: Välj hur Office uppdateras på enheter. Information om de olika uppdateringskanalerna finns i [Översikt över uppdateringskanaler för Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Välj mellan:
        - **Varje månad**
        - **Månadskanal (riktad)**
        - **Semi-Annual** (Varje halvår)
        - **Varje halvår (riktad)**

        När du har valt en kanal finns alternativet att välja **Specifik** för att installera en specifik version av Office för den valda kanalen på slutanvändarenheter. Välj sedan den **specifika version** av Office som ska användas.
        
        De versioner som är tillgängliga ändras över tid. När du skapar en ny distribution kan de versioner som är tillgängliga därför vara nyare och inte ha vissa äldre versioner tillgängliga. Befintliga distributioner fortsätter att distribuera den äldre versionen, men versionslistan uppdateras kontinuerligt per kanal.
        
        För enheter som uppdaterar sin fästa version (eller uppdaterar några andra egenskaper) och har distribuerats som tillgängliga visas rapporteringsstatusen som Installerad om de installerade den tidigare versionen innan enhetsincheckningen inträffar. När enhetsincheckningen inträffar ändras statusen tillfälligt till Okänd, men det visas inte för användaren. När användaren initierar installationen för den senare tillgängliga versionen ser användaren att statusen ändras till Installerad.
        
        Mer information finns i [Översikt över uppdateringskanaler för Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

    - **Ta bort MSI från slutanvändarenheter** – Välj om du vill ta bort befintliga Office .MSI-appar från slutanvändarenheter. Installationen kommer inte lyckas om det finns redan befintliga .MSI-appar på slutanvändarenheter. Apparna som ska avinstalleras är inte begränsade till de appar som valts för installation i **Konfigurera appsviten**, utan alla Office-appar (MSI) tas bort från slutanvändarens enhet. Mer information finns i [Ta bort befintliga MSI-versioner av Office vid uppgradering till Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). När Intune installerar om Office på slutanvändarnas datorer får användarna automatiskt samma språkpaket som de hade med tidigare .MSI Office-installationer. 
    - **Godkänn applicensavtalet för slutanvändare automatiskt**: Välj det här alternativet om slutanvändarna inte är tvungna att acceptera licensavtalet. Intune accepterar sedan avtalet automatiskt.
    - **Använd aktivering av delade datorer**: Välj det här alternativet när flera användare delar en dator. Mer information finns i [översikt över delad aktivering för Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Språk**: Office installeras automatiskt på alla språk som stöds och som är installerade med Windows på slutanvändarens enhet. Välj det här alternativet om du vill installera ytterligare språk med app-paketet. <p></p>
    Du kan distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Gå till Azure Portal och välj **Microsoft Intune** > **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** på bladet **Lägg till app** väljer du **Windows 10** under **Office 365 Suite**. Välj **Språk** på bladet **Inställningar för appsviten**. Mer information finns i [översikten över språkdistribution i Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Välj omfångstaggar (valfritt)
Du kan använda omfångstaggar för att bestämma vem som kan se klientappsinformation i Intune. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar för distribuerad IT](scope-tags.md).

1. Välj **Omfång (taggar)**  > **Lägg till**.
2. Använd rutan **Välj** för att söka efter omfångstaggar.
3. Markera kryssrutan bredvid de omfångstaggar som du vill tilldela till den här appen.
4. Välj **Välj** > **OK**.

## <a name="enter-xml-format"></a>Ange XML-format

Om du valde alternativet **Ange XML-format** i listrutan **Inställningsformat** visas alternativet **Ange XML-format** på bladet **Lägg till app**. Mer information finns i [Konfigurationsalternativ för distributionsverktyget för Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Slutför

I fönstret **Lägg till app** väljer du **Lägg till** när du är klar. Appen som du har skapat visas i applistan.

## <a name="errors-during-installation-of-the-app-suite"></a>Fel under installationen av appsviten

I följande tabeller visas vanliga felkoder som kan uppstå och deras innebörd.

### <a name="status-for-office-csp"></a>Status för Office CSP

| Status | Fas | Beskrivning |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Hämta | Det gick inte att hämta distributionsverktyget för Office |
| 13 (ERROR_INVALID_DATA) | - | Det går inte att verifiera signaturen för det hämtade distributionsverktyget för Office |
| Felkod från CertVerifyCertificateChainPolicy | - | Kontroll av certifikatutfärdare för det hämtade distributionsverktyget för Office |
| 997 | PÅGÅENDE ARBETE | Installerar |
| 0 | Efter installation | Installationen lyckades |
| 1603 (ERROR_INSTALL_FAILURE) | - | Kravkontrollen misslyckades, t.ex. SxS (Försökte installera när 2016 MSI är installerat) Version stämmer inteÖvrigt |
| 0x8000ffff (E_UNEXPECTED) | - | Försökte avinstallera när det inte finns någon Klicka och kör Office på datorn |
| 17002 | - | Det gick inte att slutföra scenariot (installation). Möjliga orsaker:Installationen avbröts av användarenInstallationen avbröts av en annan installationDiskutrymmet tog slut under installationenOkänt språk-ID |
| 17004 | - | Okända SKU:er |


### <a name="office-deployment-tool-error-codes"></a>Felkoder för distributionsverktyget för Office

| Scenario | Returkod | UI | Obs! |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| Avinstallera när det inte finns några aktiva Klicka och kör-installationer | -2147418113, 0x8000ffff eller 2147549183 | Felkod: 30088 1008Felkod: 30125–1011 (404) | Office-distributionsverktyg |
| Installera om det finns en installerad MSI-version | 1603 | - | Office-distributionsverktyg |
| Installationen avbröts av användaren eller av en annan installation | 17002 | - | Klicka och kör |
| Om du försökte installera 64-bitars på en enhet som har installerat 32-bitars. | 1603 | - | Returkod för distributionsverktyget för Office |
| Försök att installera en okänd SKU (inte ett giltig användningsfall för Office CSP eftersom vi bara ska skicka giltiga SKU: er) | 17004 | - | Klicka och kör |
| Brist på utrymme | 17002 | - | Klicka och kör |
| Klicka och kör-klienten kunde inte starta (oväntat) | 17000 | - | Klicka och kör |
| Klicka och kör-klienten kunde inte ställa scenariot i kö (oväntat) | 17001 | - | Klicka och kör |

## <a name="next-steps"></a>Nästa steg

- Information om hur du tilldelar apparna till de grupper du väljer finns i [Tilldela appar till grupper](/intune-azure/manage-apps/deploy-apps).
