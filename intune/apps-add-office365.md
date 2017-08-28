---
title: "Installera Office 365 ProPlus-appar för Windows 10-enheter med Intune"
titleSuffix: Intune on Azure
description: "Så här använder du Intune för att underlätta installation av Office 365-appar på Windows 10-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 471b4dd524cea553af89acc3e158fd2a05cebe3d
ms.sourcegitcommit: c8fb42fcb8735af432c7e07c380d956171012bd4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/14/2017
---
# <a name="how-to-assign-office-365-proplus-2016-apps-to-windows-10-devices-with-microsoft-intune"></a>Så här tilldelar du Office 365 ProPlus 2016-appar till Windows 10-enheter med Microsoft Intune

Med den här apptypen kan du enkelt tilldela Office 365 ProPlus 2016-appar till enheter som du hanterar och som kör Windows 10. Du kan även installera appar för klientversionen av Microsoft Project Online och Microsoft Visio Pro för Office 365 om du har licenser för dessa. Appar som du vill använda visas som en enda app i listan med appar i Intune-konsolen.


## <a name="before-you-start"></a>Innan du börjar

>[!IMPORTANT]
>Den här metoden för att installera Office stöds endast om inga andra versioner av Microsoft Office är installerade på enheten.

- Enheterna måste köra Windows 10 Creators Update eller senare.
- Intune har endast stöd för att lägga till Office-appar från Office 365 ProPlus 2016.
- Om alla Office-program är öppna när Intune installerar appen kan slutanvändare förlora data från filer som inte sparats.
- Den här installationsmetoden stöds inte på Windows 10S-enheter.
- Intune stöder inte installation av Office 365-skrivbordsappar från Windows Store (kallas även Office Centennial-appar) på en enhet som du redan har distribuerat Office 365-appar till med Intune. Om du installerar den här konfigurationen kan det orsaka dataförlust eller skadade data.


## <a name="get-started"></a>Kom igång

1.  Logga in på Azure-portalen.
2.  Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3.  Välj **Mobilappar** på **Intune**-bladet.
4.  Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5.  Välj **Lägg till** ovanför applistan.
6.  På bladet **Lägg till App** väljer du **Office 365 ProPlus-paket (Windows 10)**.

## <a name="configure-the-app-suite"></a>Konfigurera app-paketet

Välj de Office-appar som du vill tilldela till enheter i det här steget.

1.  På bladet **Lägg till app** väljer du **Konfigurera appaket**.
2.  På bladet **Konfigurera appaket** väljer du de standard-Office-appar som du vill tilldela till enheter. Dessutom kan du också installera appar för klientversionen av Microsoft Project Online och Microsoft Visio Pro för Office 365 om du har licenser för dessa.
3.  När du är klar klickar du på **OK**.

>[!IMPORTANT]
> När du har skapat app-paketet kan du inte redigera dess egenskaper. För att konfigurera olika egenskaper måste du ta bort appaketet och skapa en ny.

## <a name="configure-app-information"></a>Konfigurera appinformation

I det här steget anger du information om appaketet. Den här informationen hjälper dig att identifiera appen i Intune-konsolen och även hjälpa slutanvändarna att hitta den i företagsportalappen.

1.  Välj **Appinformation** på bladet **Lägg till app**.
2.  Konfigurera följande information på bladet **Appinformation**: 
    - **Paketnamn** – Ange namnet på appaketet så som det visas på företagsportalen. Kontrollera att alla paketnamn du använder är unika. Om samma paketnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Paketbeskrivning** – Ange en beskrivning för appaketet. Exempelvis kan du visa de appar som ingår.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Kategori** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det blir det enklare för användarna att hitta appaketet när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appaketet på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Ladda upp ikon** - Ladda upp en ikon som visas med appen när användare söker i företagsportalen.
3.  När du är klar klickar du på **OK**.

## <a name="configure-app-settings"></a>Konfigurera appinställningar

Konfigurera installationsalternativ för app-paket i det här steget. Inställningarna tillämpas på alla appar som du har lagt till i serien.

1.  Välj **Appaketinformation** på bladet **Lägg till app**.
2.  Konfigurera följande information på bladet **Appaketinformation**: 
    - **Office-version** -Välj om du vill tilldela 32-bitars eller 64-bitars version av Office. Du kan installera 32-bitarsversionen på enheter med 32-bitar och 64-bitar, men du kan bara installera 64-bitarsversionen på 64-bitarsenheter.
    - **Uppdatera kanal** – Välj hur office uppdateras på enheter. Information om andra uppdateringskanaler finns i översikten över uppdateringskanaler för Office 365 ProPlus. Välj mellan: 
        - **Nuvarande**
        - **Uppskjutna**
        - **Den första aktuella versionen**
        - **Den första uppskjutna versionen**
    - **Godkänn applicensavtalet för slutanvändare** – Välj det här alternativet om användare inte behöver godkänna licensavtalet. Intune accepterar sedan avtalet automatiskt.
    - **Använd aktivering på delad dator** – Aktivering på delad dator används när flera användare delar en dator. Mer information finns i översikt över delad aktivering för Office 365 ProPlus.
    - **Språk** - Office installeras automatiskt på alla språk som stöds som är installerade med Windows på slutanvändarens enhet. Välj det här alternativet om du vill installera ytterligare språk med app-paketet.

>[!IMPORTANT]
> När du har skapat app-paketet kan du inte redigera dess egenskaper. För att konfigurera olika egenskaper måste du ta bort appaketet och skapa en ny.

## <a name="finish-up"></a>Slutför

När du är klar väljer du **Spara** på bladet **Lägg till app**. Appen som du har skapat visas i applistan.

## <a name="error-codes-when-installing-the-app-suite"></a>Felkoder vid installation av app-paket

I följande tabell visas vanliga felkoder som kan uppstå och deras innebörd.

### <a name="status-for-office-csp"></a>Status för Office CSP: 

||||
|-|-|-|
|Status|Fas|Beskrivning|
|1460 (ERROR_TIMEOUT)|Hämta|Det gick inte att hämta distributionsverktyget för Office|    
|13 (ERROR_INVALID_DATA)|-|Det går inte att verifiera signaturen för det hämtade distributionsverktyget för Office| 
|Felkod från CertVerifyCertificateChainPolicy|-|Kontroll av certifikatutfärdare för det hämtade distributionsverktyget för Office|    
|997|PÅGÅENDE ARBETE|Installerar| 
|0|Efter installation|Installationen lyckades|    
|1603 (ERROR_INSTALL_FAILURE)|-|Kravkontrollen misslyckades, till exempel:<br>-SxS (försökte installera när 2016 MSI är installerat)<br>- versionsmatchningsfel<br>-osv.|     
|0x8000ffff (E_UNEXPECTED)|-|Försökte avinstallera när det inte finns någon Klicka och kör Office på datorn.|    
|17002|-|Det gick inte att slutföra scenariot (installation). Möjlig orsak:<br>- Installationen avbröts av användaren<br>- Installationen avbröts av en annan installation<br>- Slut på diskutrymme under installationen<br>- Okänt språk-ID| 
|17004|-|Okända SKU:er|   


### <a name="office-deployment-tool-error-codes"></a>Felkoder för distributionsverktyget för Office

|||||
|-|-|-|-|
|Scenario|Returkod|UI|Obs!| 
|Avinstallera när det inte finns några aktiva Klicka och kör-installationer|-2147418113, 0x8000ffff eller 2147549183|Felkod: 30088-1008<br>Felkod: 30125-1011 (404)|Office-distributionsverktyg| 
|Installera om det finns en installerad MSI-version|1603|-|Office-distributionsverktyg| 
|Installationen avbröts av användaren eller av en annan installation|17002|-|Klicka och kör| 
|Om du försökte installera 64-bitars på en enhet som har installerat 32-bitars.|1603|-|Returkod för distributionsverktyget för Office| 
|Försök att installera en okänd SKU (inte ett giltig användningsfall för Office CSP eftersom vi bara ska skicka giltiga SKU: er)|17004|-|Klicka och kör| 
|Brist på utrymme|17002|-|Klicka och kör| 
|Klicka och kör-klienten kunde inte starta (oväntat)|17000|-|Klicka och kör| 
|Klicka och kör-klienten kunde inte ställa scenariot i kö (oväntat)|17001|-|Klicka och kör| 

## <a name="next-steps"></a>Nästa steg

Nu kan du tilldela apparna till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](/intune-azure/manage-apps/deploy-apps).

             


