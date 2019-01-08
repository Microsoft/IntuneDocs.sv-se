---
title: Installera Office 365-appar på enheter med Microsoft Intune
titlesuffix: ''
description: Läs mer om att använda Microsoft Intune för att underlätta installationen av Office 365-appar på Windows 10-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e2958b536aa6603fc9cde14e679a05e4a9d5f4dd
ms.sourcegitcommit: 0f19bc5c76b7c0835bfd180459f2bbd128eec1c2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53266978"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune

Med den här apptypen kan du enkelt tilldela Office 365-appar till enheter som du hanterar och som kör Windows 10. Du kan även installera appar för klientversionen av Microsoft Project Online och Microsoft Visio Pro för Office 365 om du har licenser för dessa. Appar som du vill använda visas som en enda post i listan med appar i Intune-konsolen.

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

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** i **Intune**-fönstret.
4. I arbetsbelastningsfönstret **Klientappar** väljer du **Appar** under **Hantera**.
5. Välj **Lägg till**.
6. I fönstret **Lägg till appar** i listan **Apptyp** under **Office 365-paket** väljer du **Windows 10**.

Nu kan du konfigurera app-paketet.

## <a name="configure-the-app-suite"></a>Konfigurera app-paketet

Välj de Office-appar som du vill tilldela till enheter.

1. I fönstret **Lägg till app** väljer du **Konfigurera appsvit**.
2. I fönstret **Konfigurera appsvit** väljer du de standard-Office-appar som du vill tilldela till enheter.  
    Dessutom kan du också installera appar för klientversionen av Microsoft Project Online och Microsoft Visio Pro för Office 365 om du har licenser för dessa.
3. Välj **OK**.

## <a name="configure-app-information"></a>Konfigurera appinformation

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

## <a name="configure-app-settings"></a>Konfigurera appinställningar

Konfigurera installationsalternativ för app-paket i det här steget. Inställningarna tillämpas på alla appar som du har lagt till i serien.

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
