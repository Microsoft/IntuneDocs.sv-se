---
title: Lägg till Office 365-appar i Windows 10-enheter med hjälp av Microsoft Intune
titleSuffix: ''
description: Lär dig hur du kan använda Microsoft Intune för installera Office 365-appar på Windows 10-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86d02ae1277ff2fd6dfce9bf206628f5dc1c2a84
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755346"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Lägg till Office 365-appar i Windows 10-enheter med Microsoft Intune

Innan du kan tilldela, övervaka, konfigurera eller skydda appar måste du lägga till dem till Intune. En av de tillgängliga [apptyperna](apps-add.md#app-types-in-microsoft-intune) är Office 365-appar för Windows 10-enheter. Genom att välja den här apptypen i Intune kan du tilldela och installera Office 365-appar på enheter som du hanterar och som kör Windows 10. Du kan även tilldela och installera appar för skrivbordsklienten för Microsoft Project Online och Microsoft Visio Online, abonnemang 2 om du har licenser för dessa. De tillgängliga Office 365-apparna visas som en enda post i listan med appar i Intune-konsolen i Azure.

> [!NOTE]
> Du måste använda Office 365 ProPlus-licenser för att kunna aktivera de Office 365 ProPlus-appar som distribueras via Microsoft Intune. Office 365 Business Edition stöds för närvarande inte av Intune.

## <a name="before-you-start"></a>Innan du börjar

> [!IMPORTANT]
> Om det finns .msi Office-appar på slutanvändarens enhet måste du använda funktionen **Ta bort MSI** för att avinstallera de här apparna på ett säkert sätt. Annars kommer det inte gå att installera de Office 365-appar som levereras via Intune.

- Enheterna måste köra Windows 10 Creators Update eller senare.
- Intune har endast stöd för att lägga till Office-appar från Office 365.
- Om alla Office-program är öppna när Intune installerar appen kan installationen misslyckas och användare kan förlora data från filer som inte sparats.
- Den här installationsmetoden stöds inte på Windows Home-, Windows Team-, Windows Holographic- eller Windows Holographic for Business-enheter.
- Intune stöder inte installation av Office 365-skrivbordsappar från Microsoft Store (kallas även Office Centennial-appar) på en enhet som du redan har distribuerat Office 365-appar till med Intune. Om du installerar den här konfigurationen kan det orsaka dataförlust eller skadade data.
- Många obligatoriska eller tillgängliga apptilldelningar är inte additiva. En senare tilldelning av en app överskriver de befintliga installerade apptilldelningarna. Om den första uppsättningen Office-program innehåller Word och den senare inte gör det så kommer exempelvis Word att avinstalleras. Detta tillstånd gäller inte för Visio- eller Project-program.
- Flera Office 365-distributioner stöds inte för närvarande. Endast en distribution kommer att levereras till enheten
- **Office-version** – Välj om du vill tilldela 32-bitars- eller 64-bitarsversionen av Office. Du kan installera 32-bitarsversionen på enheter med 32-bitar och 64-bitar, men du kan bara installera 64-bitarsversionen på 64-bitarsenheter.
- **Ta bort MSI från slutanvändarenheter** – Välj om du vill ta bort befintliga Office .MSI-appar från slutanvändarenheter. Installationen kommer inte lyckas om det finns redan befintliga .MSI-appar på slutanvändarenheter. Apparna som ska avinstalleras är inte begränsade till de appar som valts för installation i **Konfigurera appsviten**, utan alla Office-appar (MSI) tas bort från slutanvändarens enhet. Mer information finns i [Ta bort befintliga MSI-versioner av Office vid uppgradering till Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). När Intune installerar om Office på slutanvändarnas datorer får användarna automatiskt samma språkpaket som de hade med tidigare .MSI Office-installationer.

## <a name="select-the-office-365-suite-app-type"></a>Välj en app av Office 365-pakettyp

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj **Windows 10** i avsnittet **Office 365-paket** på fönstret **Välj apptyp**.
4. Klicka på **Välj**. Stegen **Lägga till Office 365-paket** visas.


## <a name="step-1---app-suite-information"></a>Steg 1 – Information om appsvit

I det här steget anger du information om appaketet. Den här informationen hjälper dig att identifiera appsviten i Intune och hjälper användarna att hitta appsviten det i företagsportalappen.

1. På sidan **Information om appsvit** kan du bekräfta eller ändra standardvärdena:
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
2. Klicka på **Nästa** för att visa sidan **Konfigurera appsviten**.

## <a name="step-2---option-1-configure-app-suite-using-the-configuration-designer"></a>Steg 2 – (**Alternativ 1**) Konfigurera appsviten med Configuration Designer 

Du kan välja en metod för att konfigurera appinställningen genom att välja ett **konfigurationsformat**. Alternativen för inställningsformat omfattar:
- Configuration Designer
- Ange XML-data

När du väljer **Configuration Designer** ändras fönstret **Lägg till app** så att ytterligare tre inställningsalternativ erbjuds:
- Konfigurera appsvit
- Information om appsvit
- Egenskaper

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

1. På sidan **Konfigurationsappsvit** väljer du **Configuration designer**.
   - **Välj Office-appar**: Välj de standard-Office-appar som du vill tilldela till enheter genom att välja apparna i listrutan.
   - **Välj andra Office-appar (licens krävs)** : Välj de övriga Office-appar som du vill tilldela till enheter och som du har licens för genom att välja apparna i listrutan. Dessa appar innehåller licensierade appar, till exempel Microsoft Project Online Desktop-klienten och Microsoft Visio Online Plan 2.
   - **Arkitektur**: Välj om du vill tilldela **32-bitars**- eller **64-bitarsversionen** av Office ProPlus. Du kan installera 32-bitarsversionen på enheter med 32-bitar och 64-bitar, men du kan bara installera 64-bitarsversionen på 64-bitarsenheter.
    - **Uppdatera kanal**: Välj hur Office uppdateras på enheter. Information om de olika uppdateringskanalerna finns i [Översikt över uppdateringskanaler för Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Välj mellan:
        - **Varje månad**
        - **Månadskanal (riktad)**
        - **Semi-Annual** (Varje halvår)
        - **Varje halvår (riktad)**

        När du har valt en kanal kan du välja följande:
        - **Ta bort andra versioner**: Välj **Ja** om du vill ta bort andra versioner av Office (MSI) från användarenheter. Välj om du vill ta bort befintliga Office .MSI-appar från slutanvändarenheter. Installationen kommer inte lyckas om det finns redan befintliga .MSI-appar på slutanvändarenheter. Apparna som ska avinstalleras är inte begränsade till de appar som valts för installation i **Konfigurera appsviten**, utan alla Office-appar (MSI) tas bort från slutanvändarens enhet. Mer information finns i [Ta bort befintliga MSI-versioner av Office vid uppgradering till Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). När Intune installerar om Office på slutanvändarnas datorer får användarna automatiskt samma språkpaket som de hade med tidigare .MSI Office-installationer. 
        - **Version som ska installeras**: Välj den version av Office som ska installeras.
        - **Specifik version**: Om du har valt **Specifik** som **Versionatt installera** i ovanstående inställning kan du välja att installera en viss version av Office för den valda kanalen på slutanvändarens enheter. 
            
            De versioner som är tillgängliga ändras över tid. När du skapar en ny distribution kan de versioner som är tillgängliga därför vara nyare och inte ha vissa äldre versioner tillgängliga. Befintliga distributioner fortsätter att distribuera den äldre versionen, men versionslistan uppdateras kontinuerligt per kanal.
            
            För enheter som uppdaterar sin fästa version (eller uppdaterar några andra egenskaper) och har distribuerats som tillgängliga visas rapporteringsstatusen som Installerad om de installerade den tidigare versionen innan enhetsincheckningen inträffar. När enhetsincheckningen inträffar ändras statusen tillfälligt till Okänd, men det visas inte för användaren. När användaren initierar installationen för den senare tillgängliga versionen ser användaren att statusen ändras till Installerad.
            
            Mer information finns i [Översikt över uppdateringskanaler för Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).
    - **Använd aktivering av delade datorer**: Välj det här alternativet när flera användare delar en dator. Mer information finns i [översikt över delad aktivering för Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Godkänn applicensavtalet för slutanvändare automatiskt**: Välj det här alternativet om slutanvändarna inte är tvungna att acceptera licensavtalet. Intune accepterar sedan avtalet automatiskt.
    - **Språk**: Office installeras automatiskt på alla språk som stöds och som är installerade med Windows på slutanvändarens enhet. Välj det här alternativet om du vill installera ytterligare språk med app-paketet. <p></p>
        Du kan distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Välj **Microsoft Intune** > **Appar** > **Alla appar** > **Lägg till** i Azure Portal. Välj **Windows 10** under **Office 365 Suite** i listan **Apptyp** i fönstret **Lägg till app**. Välj **Språk** i fönstret **Inställningar för appsvit**. Mer information finns i [översikten över språkdistribution i Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).
2. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.

## <a name="step-2---option-2-configure-app-suite-using-xml-data"></a>Steg 2 – (**alternativ 2**) Konfigurera appsviten med XML-data 

Om du har valt alternativet **Ange XML-data** i listrutan **Inställningsformat** på sidan **Konfigurera appsviten** kan du konfigurera Office-appsviten med hjälp av en anpassad konfigurationsfil.

![Lägga till Office 365 Configuration Designer](./media/apps-add-office365/apps-add-office365-01.png)

1. Din konfigurations-XML har lagts till.
2. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.

Mer information om att ange XML-data finns i [Konfigurationsalternativ för distributionsverktyget för Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="step-3---select-scope-tags-optional"></a>Step 3 – Select scope tags (optional)
Du kan använda omfångstaggar för att bestämma vem som kan se klientappsinformation i Intune. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).

1. Klicka på **Välj omfångstaggar** om du vill lägga till omfångstaggar för appsviten. 
2. Klicka på **Nästa** för att visa sidan **Tilldelningar**.

## <a name="step-4---assignments"></a>Steg 4 – Tilldelningar

1. Välj **Obligatorisk**, **Tillgängligt för registrerade enheter** eller **Avinstallera** som grupptilldelning för appsviten. Mer information finns i [Lägg till grupper för att organisera användare och enheter](~/fundamentals/groups-add.md) och [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).
2. Visa sidan **Granska och skapa** genom att klicka på **Nästa**. 

## <a name="step-5---review--create"></a>Steg 5 – Granska och skapa

1. Granska värdena och inställningarna som du har angett för appsviten.
2. När du är färdig klickar du på **Skapa** för att lägga till appen i Intune.

    **Översiktsbladet** för Office 365 Windows 10-appsviten som du har skapat visas i applistan.

## <a name="deployment-details"></a>Distributionsinformation

När distributionsprincipen från Intune har tilldelats till måldatorerna via [Office Configuration Service Provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/office-csp) hämtas installationspaketet automatiskt från *officecdn.microsoft.com* till målenheten. Två kataloger visas i katalogen *Programfiler*:

![Installationspaket för Office i katalogen Programfiler](./media/apps-add-office365/office-folder.png)

Under katalogen *Microsoft Office* skapas en ny mapp där installationsfilerna lagras:

![Ny mapp som skapats under Microsoft Office-katalogen](./media/apps-add-office365/created-folder.png)

Startfilerna för Office Klicka-och-kör-installationen lagras under *Microsoft Office 15*-katalogen. Installationen startar automatiskt om tilldelningstypen krävs:

![Klicka om du vill köra startfilerna för installation](./media/apps-add-office365/clicktorun-files.png)

Installationen körs i tyst läge om tilldelningen av O365-sviten är konfigurerad enligt krav. Installationsfilerna som hämtats tas bort när installationen är klar. Om tilldelningen konfigureras som **tillgänglig** visas Office-programmen i företagsportalappen så att slutanvändarna kan starta installationen manuellt.

## <a name="troubleshooting"></a>Felsökning
Intune använder [distributionsverktyget för Office](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) för att hämta och distribuera Office 365 ProPlus till dina klientdatorer med [Office 365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks). Hänvisa till bästa praxis i [hantera slutpunkter för Office 365](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) för att kontrollera att din nätverkskonfiguration tillåter att klienter får åtkomst till CDN direkt snarare än via routning av CDN-trafik genom centrala proxyservrar, så undviker du onödigt långa svarstider.

Kör [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com) på målenheter om du stöter på problem med installation eller körning.

### <a name="additional-troubleshooting-details"></a>Ytterligare felsökningsinformation

Om du inte kan installera O365-apparna på en enhet måste du ta reda på om problemet är relaterat till Intune eller OS/Office. Om mapparna *Microsoft Office* och *Microsoft Office 15* visas i katalogen *Programfiler* på enheten vet du att Intune har initierat distributionen. Om de två mapparna inte visas under *Programfiler* kontrollerar du följande:

- Att enheten har registrerats korrekt i Microsoft Intune. 
- Att det finns en aktiv nätverksanslutning på enheten. Om enheten är i flygplansläge, är inaktiverad eller är på en plats utan anslutning, gäller inte principen förrän nätverksanslutningen har upprättats.
- Om både nätverkskraven för Intune och Office 365 är uppfyllda och relaterade IP-intervall är tillgängliga utifrån följande artiklar:

  - [Krav för Intune-nätverkskonfiguration och bandbredd](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [Webbadresser och IP-adressintervall för Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- Rätt grupper har tilldelats O365-programsviten. 

Övervaka också storleken på katalogen *C:\Program Files\Microsoft Office\Updates\Download*. Här lagras installationspaketet som hämtas från Intune-molnet. Om storleken inte ökar eller ökar mycket långsamt, rekommenderar vi att du kontrollerar nätverksanslutningen och bandbredden.

När du vet att Intune och nätverksinfrastrukturen fungerar som förväntat går du vidare med att kontrollera operativsystemet. Tänk på följande:

- Målenheten måste köra Windows 10 Creators Update eller senare.
- Inga befintliga Office-appar får vara öppna medan Intune distribuerar programmen.
- Befintliga MSI-versioner av Office måste ha tagits bort korrekt från enheten. Intune använder Office Klicka-och-kör, vilket inte är kompatibelt med Office MSI. Det här beteendet beskrivs närmare i det här dokumentet:<br>
  [Office installerat med Klicka-och-kör och Windows Installer på samma dator stöds inte](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd)
- Den inloggade användaren måste ha behörighet att installera program på enheten.
- Bekräfta att det inte finns några problem baserat på Windows Loggboken-loggen **Windows-loggar** -> **Program**.
- Samla in utförliga loggfiler för Office-installationen under installationen. Det gör du genom att följa dessa steg:<br>
    1. Aktivera utförlig loggning för Office-installation på måldatorerna. Du gör detta genom att köra följande kommando för att ändra registret:<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. Distribuera Office 365-sviten till målenheterna igen.<br>
    3. Vänta i cirka 15 till 20 minuter och gå sedan till mappen **%temp%** och mappen **%windir%\temp**, sortera efter **Ändrad den** och välj *{Machine Name}-{TimeStamp}.log*-filerna som ändras enligt din reproduktionstid.<br>
    4. Kör följande kommando för att inaktivera utförlig loggning:<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        Utförliga loggfiler kan ge ytterligare detaljerad information om installationsprocessen.

## <a name="errors-during-installation-of-the-app-suite"></a>Fel under installationen av appsviten

Se [Så här aktiverar du loggning för Office 365 ProPlus ULS](/office/troubleshoot/diagnostic-logs/how-to-enable-office-365-proplus-uls-logging) för information om hur du visar utförliga installationsloggar.

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

- Information om hur du tilldelar appsviten till ytterligare grupper finns i [Tilldela appar till grupper](/intune-azure/manage-apps/deploy-apps).
