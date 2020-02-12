---
title: Lägga till och tilldela Win32-appar till Microsoft Intune
titleSuffix: ''
description: Lär dig hur du lägger till, tilldelar och hanterar Win32-appar med Microsoft Intune. Det här avsnittet innehåller en översikt över Intunes leverans- och hanteringsfunktioner för Win32-appar, samt felsökningsinformation för Win32-appar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbefd797fead7113045ee7e7655b715a0b4961fd
ms.sourcegitcommit: 32391f74241ee3289a76ccd5319fe700b800d427
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2020
ms.locfileid: "77075832"
---
# <a name="intune-standalone---win32-app-management"></a>Fristående Intune – Win32-apphantering

[Fristående Intune](../fundamentals/mdm-authority-set.md) ger nu bättre hanteringsfunktioner för Win32-appar. Molnanslutna kunder kan använda Configuration Manager för Win32-apphantering, men kunder med fristående Intune har tillgång till bättre hanteringsfunktioner för sina verksamhetsspecifika Win32-appar. Det här avsnittet innehåller en översikt över Intunes hanterings- och felsökningsfunktioner för Win32-appar.

> [!NOTE]
> Den här funktionen för apphantering har stöd för både 32-bitars och 64-bitars operativsystemarkitektur för Windows-program.

> [!IMPORTANT]
> När du distribuerar Win32-appar bör du överväga att endast använda [tillägget för Intune-hantering](../apps/intune-management-extension.md), särskilt om du har ett Win32-installationsprogram för flera filer. Om du blandar installationen av Win32-appar och verksamhetsspecifika appar under autopilotregistreringen, kan det hända att appen inte kan installeras.  

## <a name="prerequisites"></a>Krav

Om du vill använda Win32-apphantering ska du uppfylla följande kriterier:

- Windows 10 version 1607 eller senare (Enterprise- och Pro Education-versionerna)
- Windows 10-klienten måste vara: 
  - Enheterna måste vara anslutna till Azure AD och automatiskt registrerade. Intune-hanteringstillägget har stöd för Azure AD-anslutna, hybriddomänanslutna, grupprincipregistrerade enheter. 
  > [!NOTE]
  > För scenariot med grupprincipregistrering – slutanvändaren använder det lokala användarkontot till att AAD-ansluta sin Windows 10-enhet. Användaren måste logga in på enheten med sitt AAD-användarkonto och registrera till Intune. Intune installerar Intune-hanteringstillägget på enheten om ett PowerShell-skript eller en Win32-app riktas till användaren eller enheten.
- Storleken för Windows-program är högst 8 GB per app.

## <a name="prepare-the-win32-app-content-for-upload"></a>Förbereda Win32-appinnehållet för uppladdning

Använd [Microsofts förberedelseverktyg för Win32-innehåll](https://go.microsoft.com/fwlink/?linkid=2065730) för att förbearbeta Windows Classic-appar (Win32). Verktyget konverterar programinstallationsfilerna till formatet *.intunewin*. Verktyget identifierar även vissa av de attribut som krävs av Intune för att fastställa programmets installationstillstånd. När du har använt det här verktyget med appinstallationsmappen kan du skapa en Win32-app i Intune-konsolen.

> [!IMPORTANT]
> [Microsofts förberedelseverktyg för Win32-innehåll](https://go.microsoft.com/fwlink/?linkid=2065730) zippar ihop alla filer och undermappar när det skapar *.intunewin*-filen. Se till att hålla Microsofts förberedelseverktyg för Win32-innehåll separat från installationsprogrammets filer och mappar, så att du inte inkluderar verktyget eller andra onödiga filer och mappar i *.intunewin*-filen.

Du kan ladda ned [Microsofts förberedelseverktyg för Win32-innehåll](https://go.microsoft.com/fwlink/?linkid=2065730) som en zip-fil från GitHub. Zip-filen innehåller en mapp som heter **Microsoft-Win32-Content-Prep-Tool-master**. Mappen innehåller förberedelseverktyget, licensen, en readme-fil samt viktig information. 

### <a name="process-flow-to-create-intunewin-file"></a>Processflöde för att skapa .intunewin-fil

   <img alt="Process flow to create a .intunewin file" src="./media/apps-win32-app-management/prepare-win32-app.svg" width="700">

### <a name="run-the-microsoft-win32-content-prep-tool"></a>Köra Microsofts förberedelseverktyg för Win32-innehåll

Om du kör `IntuneWinAppUtil.exe` från kommandofönstret utan parametrar vägleder verktyget dig att ange de obligatoriska parametrarna steg för steg. Eller så kan du lägga till parametrarna i kommandot baserat på följande tillgängliga kommandoradsparametrar.

### <a name="available-command-line-parameters"></a>Tillgängliga kommandoradsparametrar 

|    **Kommandoradsparameter**    |    **Beskrivning**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Hjälp    |
|    `-c <setup_folder>`     |    Mapp för alla installationsfiler. Alla filer i den här mappen komprimeras till en *.intunewin*-fil.    |
|    `-s <setup_file>`     |    Installationsfil (till exempel *setup.exe* eller *setup.msi*).    |
|    `-o <output_folder>`     |    Utdatamapp för den genererade *.intunewin*-filen.    |
|    `-q`       |    Tyst läge    |

### <a name="example-commands"></a>Exempelkommandon

|    **Exempelkommando**    |    **Beskrivning**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Det här kommandot visar användningsinformation för verktyget.    |
|    `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q`    |    Det här kommandot genererar `.intunewin`-filen från den angivna källmappen och installationsfilen. För MSI-installationsfilen hämtar det här verktyget nödvändig information för Intune. Om `-q` anges körs kommandot i tyst läge och om utdatafilen redan finns skrivs den över. Om utdatamappen inte finns, skapas den automatiskt.    |

När du genererar en *.intunewin*-fil placerar du alla de filer som du behöver referera till i en undermapp i installationsmappen. Referera sedan till den specifika fil du behöver med en relativ sökväg. Exempel:

**Installationens källmapp:** *c:\testapp\v1.0*<br>
**Licensfil:** *c:\testapp\v1.0\licenses\license.txt*

Referera till filen *license.txt* med hjälp av den relativa sökvägen *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Skapa, tilldela och övervaka en Win32-app

Precis som med en verksamhetsspecifik app kan du lägga till en Win32-app i Microsoft Intune. Den här typen av app skrivs vanligtvis internt på företaget eller av en tredje part. 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>Processflöde för att lägga till en Win32-app till Intune

<img alt="Process flow to add a Win32 app to Intune" src="./media/apps-win32-app-management/add-win32-app.svg" width="500">

### <a name="add-a-win32-app-to-intune"></a>Lägga till en Win32-app till Intune

Följande steg beskriver riktlinjer som hjälper dig att lägga till en Windows-app i Intune.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj **Windows-app (Win32)** under **Övriga** apptyper i fönstret **Välj apptyp**.

    > [!IMPORTANT]
    > Se till att ha den senaste versionen av förberedelseverktyget för Microsoft Win32-innehåll. Om du inte använder den senaste versionen visas en varning om att appen har paketerats med en äldre version av förberedelseverktyget för Microsoft Win32-innehåll. 

4. Klicka på **Välj**. Stegen **Lägg till app** visas.

## <a name="step-1---app-information"></a>Steg 1 – Appinformation

### <a name="select-the-app-package-file"></a>Välj appaketfilen

1. I fönstret **Lägg till app** klickar du på **Välj appaketfil**. 
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en Windows-installationsfil med tillägget *.intunewin*.
   Appinformationen visas.
3. När du är klar väljer du **OK** i fönstret **Appaketfil**.

### <a name="set-app-information"></a>Konfigurera appinformation

1. Lägg till information om appen i fönstret **Appinformation**. Beroende på vilken app väljer kan det hända att några av värdena i det här fönstret fylls i automatiskt.
    - **Namn**: Ange namnet på appen så som det visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna på företagsportalen.
    - **Beskrivning**: Ange beskrivningen av appen. Beskrivningen visas i företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller välj en kategori som du har skapat. Kategorier gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Visa appen tydligt på huvudsidan för företagsportalen när användare söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas i företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas i företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appägaren. Ett exempel är **Personalavdelningen**.
    - **Kommentarer**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp**: Ladda upp en ikon som är associerad med appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
2. Visa sidan **Program** genom att klicka på **Nästa**.

## <a name="step-2-program"></a>Steg 2: Program

1. Konfigurera appinstallationen och borttagningskommandona för appen på sidan **Program**:
    - **Installationskommando**: Lägg till den fullständig kommandoraden för installationen för att installera appen. 

        Om appfilnamnet exempelvis är **MyApp123** lägger du till följande:<br>
        `msiexec /p “MyApp123.msp”`<p>
        Och om programmet är `ApplicationName.exe` skulle kommandot vara programmets namn följt av de kommandoargument (växlar) som stöds av paketet. <br>Exempel:<br>
        `ApplicationName.exe /quiet`<br>
        I kommandot ovan stöder paketet `ApplicationName.exe` kommandoargumentet `/quiet`.<p> 
        Kontakta leverantören av programmet för de specifika argument som stöds av programpaketet.

    - **Avinstallationskommando**: Lägg till den fullständiga kommandoraden för avinstallation av appen baserat på appens GUID. 

        Exempel: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    - **Installationsbeteende**: Ange **System** eller **Användare** som installationsbeteende.

        > [!NOTE]
        > Du kan konfigurera att en Win32-app installeras i kontexten **Användare** eller **System**. Kontexten **Användare** avser bara en viss användare. Kontexten **System** avser alla användare av en Windows 10-enhet.
        >
        > Slutanvändare behöver inte vara inloggade på enheten för att installera Win32-appar.
        > 
        > Installationen och avinstallationen av Win32-appen körs med administratörsbehörighet (som standard) när appen är inställd på att installeras i användarkontext och slutanvändaren på enheten har administratörsbehörighet.
    
    - **Beteende för omstart av enhet**: Välj något av följande alternativ:
        - **Bestäm beteende baserat på returkoder**: Välj det här alternativet om du vill starta om enheten utifrån returkoderna.
        - **Ingen specifik åtgärd**: Välj det här alternativet om du inte vill att enheten ska startas om när MSI-baserade appar installeras.
        - **Appinstallation kan tvinga fram omstart av enhet**: Välj det här alternativet om du vill att appinstallationen ska slutföras utan att åsidosätta omstart.
        - **Intune tvingar fram obligatorisk omstart av enhet**: Välj det här alternativet om du vill att enheten alltid ska startas om efter en lyckad appinstallation.

    - **Ange returkoder för att visa på funktionssätt efter installationen**: Lägg till de returkoder som används för att ange antingen hur appinstallationen hanterar återförsök eller beteendet efter installationen. Poster för returkoder läggs till som standard när appen skapas. Du kan dock lägga till ytterligare returkoder eller ändra befintliga returkoder.
        1. Ställ in **Kodtyp** i kolumnen **Kodtyp** på något av följande:
            - **Misslyckades** – Returvärdet som anger ett appinstallationsfel.
            - **Hård omstart** – Returkoden för hård omstart tillåter inte att nästa Win32-app installeras på klienten utan omstart. 
            - **Mjuk omstart** – Returkoden för mjuk omstart tillåter att nästa Win32-app installeras utan att klienten måste startas om. Omstart krävs för att slutföra installationen av det aktuella programmet.
            - **Försök igen** – Agenten för returkoden för återförsök försöker installera appen tre gånger. Den väntar fem minuter mellan varje försök. 
            - **Lyckades** – Returvärdet som anger att appen installerades.
        2. Klicka, om så behövs, på **Lägg till** om du vill lägga till ytterligare returkoder eller ändra befintliga returkoder.
2. Visa sidan **Åtkomstkrav** genom att klicka på **Nästa**.        

## <a name="step-3-requirements"></a>Steg 3: Krav

1. Ange de krav som enheterna måste uppfylla innan appen kan installeras på sidan **Krav**:
    - **Operativsystemarkitektur**: Välj de arkitekturer som krävs för att installera appen.
    - **Lägsta operativsystemversion**: Välj det lägsta operativsystem som krävs för att installera appen.
    - **Diskutrymme som krävs (MB)** : Om du vill kan du lägga till mängden ledigt diskutrymme som krävs på systemenheten för att installera appen.
    - **Fysiskt minne som krävs (MB)** : Om du vill kan du lägga till mängden fysiskt minne (RAM) som krävs för att installera appen.
    - **Lägsta antal logiska processorer som krävs**: Om du vill kan du lägga till det lägsta antal logiska processorer som krävs för att installera appen.
    - **Lägsta processorhastighet som krävs (MHz)** : Om du vill kan du lägga till den lägsta processorhastighet som krävs för att installera appen.
    - **Konfigurera ytterligare kravregler**: 
        1. Klicka på **Lägg till** om du vill visa fönstret **Lägg till en kravregel** och konfigurera ytterligare kravregler. Välj **typen av krav** för att välja vilken typ av regel som du använder för att avgöra hur ett krav ska valideras. Kravregler kan baseras på information om filsystem, registervärden eller PowerShell-skript. 
            - **Fil**: När du väljer **Fil** som **Typ av krav** måste kravregeln identifiera en fil eller en mapp, ett datum, en version eller en storlek. 
                - **Sökväg** – Den fullständiga sökvägen till mappen som innehåller filen eller mappen som ska identifieras.
                - **Fil eller mapp** – Filen eller mappen som ska identifieras.
                - **Egenskap** – Välj vilken typ av regel som ska användas för att validera förekomsten av appen.
                - **Kopplat till en 32-bitarsapp på 64-bitarsklienter** – Välj **Ja** om du vill expandera miljövariabler för sökvägar i 32-bitarskontexten på 64-bitarsklienter. Välj **Nej** (standard) om du vill expandera sökvägsvariabler i 64-bitarskontexten på 64-bitarsklienter. 32-bitarsklienter använder alltid 32-bitarskontexten.
            - **Register**: När du väljer **Register** som **Typ av krav** måste kravregeln identifiera en registerinställning baserat på värde, sträng, heltal eller version.
                - **Nyckelsökväg** – Den fullständiga sökvägen till registerposten som innehåller värdet som ska identifieras.
                - **Värdenamn** – Namnet på registervärdet som ska identifieras. Om det här värdet är tomt sker identifieringen mot nyckeln. (Det förvalda) värdet för en nyckel används som identifieringsvärde om identifieringsmetoden är en annan än den som identifierar förekomsten av filen eller mappen.
                - **Registernyckelkrav** – Välj den typ av registernyckeljämförelse som används för att avgöra hur kravregeln ska valideras.
                - **Kopplat till en 32-bitarsapp på 64-bitarsklienter** – Välj **Ja** om du vill söka i 32-bitarsregistret på 64-bitarsklienter. Välj **Nej** (standard) om du vill söka i 64-bitarsregistret på 64-bitarsklienter. 32-bitarsklienter söker alltid i 32-bitarsregistret.
            - **Skript**: Välj **Skript** som **Typ av krav** när du inte kan skapa en kravregel baserat på fil, register eller någon annan metod som är tillgänglig i Intune-konsolen.
                - **Skriptfil** – För en PowerShell-skriptbaserad kravregel gäller att om slutkoden är 0 så identifierar vi STDOUT med större detaljnivå. Vi kan till exempel identifiera STDOUT som ett heltal som har värdet 1.
                - **Kör skript som 32-bitarsprocess på 64-bitarsklienter** – Välj **Ja** om du vill köra skriptet i en 32-bitarsprocess på 64-bitarsklienter. Välj **Nej** (standard) för att köra skriptet i en 64-bitarsprocess på 64-bitarsklienter. 32-bitarsklienter kör skriptet i en 32-bitarsprocess.
                - **Kör det här skriptet med inloggade autentiseringsuppgifter**: Välj **Ja** för att köra skriptet med hjälp av den inloggade enhetens autentiseringsuppgifter**.
                - **Framtvinga signaturkontroll av skript** – Välj **Ja** om du vill kontrollera att skriptet har signerats av en betrodd utgivare, vilket innebär att skriptet kan köras utan att varningar eller uppmaningar visas. Skriptet körs oblockerat. Välj **Nej** (standard) om du vill köra skriptet med slutanvändarens bekräftelse utan signaturverifiering.
                - **Välja datatyp för utdata**: Välj den datatyp som används när en kravregelmatchning ska fastställas.
        2. När du har konfigurerat klart kravreglerna väljer du **OK**.
2. Visa sidan **Identifieringsregler** genom att klicka på **Nästa**.   

## <a name="step-4-detection-rules"></a>Steg 4: Identifieringsregler

1. Konfigurera de regler som ska identifiera förekomsten av appen på sidan **Identifieringsregler**:
    
    **Regelformat**: Välj hur förekomsten av appen ska identifieras. Du kan välja att antingen konfigurera identifieringsreglerna manuellt eller använda ett anpassat skript för att identifiera förekomsten av appen. Du måste välja minst en identifieringsregel. 

    > [!NOTE]
    > I fönstret **Identifieringsregler** kan du välja att lägga till flera regler. Villkoren för **alla** regler måste vara uppfyllda för att appen ska identifieras.
    >
    > Om Intune identifierar att appen inte finns på enheten erbjuder Intune appen igen efter 24 timmar. Det här sker bara för appar med den avsikt som krävs.

    - **Ställ in identifieringsregler manuellt** – Du kan välja någon av följande regeltyper:
        1. **MSI** – Verifiera baserat på MSI-versionskontroll. Det här alternativet kan endast läggas till en gång. När du väljer den här regeltypen visas två inställningar:
            - **MSI-produktkod** – Lägg till en giltig MSI-produktkod för appen.
            - **Kontroll av MSI-produktversion** – Välj **Ja** om du vill kontrollera MSI-produktversionen förutom MSI-produktkoden.
        2. **Fil** – Verifiera baserat på fil- eller mappidentifiering, datum, version eller storlek.
            - **Sökväg** – Den fullständiga sökvägen till mappen som innehåller filen eller mappen som ska identifieras.
            - **Fil eller mapp** – Filen eller mappen som ska identifieras.
            - **Identifieringsmetod** – Välj vilken typ av identifieringsmetod som ska användas för att verifiera förekomsten av appen.
            - **Kopplat till en 32-bitarsapp på 64-bitarsklienter** – Välj **Ja** om du vill expandera miljövariabler för sökvägar i 32-bitarskontexten på 64-bitarsklienter. Välj **Nej** (standard) om du vill expandera sökvägsvariabler i 64-bitarskontexten på 64-bitarsklienter. 32-bitarsklienter använder alltid 32-bitarskontexten.
            
            **Exempel på filbaserad identifiering**
            1. Kontrollera om filen finns.
         
                ![Skärmbild av fönstret för identifieringsregel – filen finns](./media/apps-win32-app-management/apps-win32-app-03.png)
        
            2. Kontrollera om mappen finns.
         
                ![Skärmbild av fönstret för identifieringsregel – mappen finns](./media/apps-win32-app-management/apps-win32-app-04.png)
        
        3. **Register** – Verifiera baserat på värde, sträng, heltal eller version.
            - **Nyckelsökväg** – Den fullständiga sökvägen till registerposten som innehåller värdet som ska identifieras.
            - **Värdenamn** – Namnet på registervärdet som ska identifieras. Om det här värdet är tomt sker identifieringen mot nyckeln. (Det förvalda) värdet för en nyckel används som identifieringsvärde om identifieringsmetoden är en annan än den som identifierar förekomsten av filen eller mappen.
            - **Identifieringsmetod** – Välj vilken typ av identifieringsmetod som ska användas för att verifiera förekomsten av appen.
            - **Kopplat till en 32-bitarsapp på 64-bitarsklienter** – Välj **Ja** om du vill söka i 32-bitarsregistret på 64-bitarsklienter. Välj **Nej** (standard) om du vill söka i 64-bitarsregistret på 64-bitarsklienter. 32-bitarsklienter söker alltid i 32-bitarsregistret.
            
            **Exempel för registerbaserad identifiering**
            1. Sök baserat på om registernyckeln finns.
            
                ![Skärmbild av fönstret för identifieringsregel – registernyckeln finns](./media/apps-win32-app-management/apps-win32-app-05.png)    
            
            2. Kontrollera om det finns något registervärde.
        
                ![Skärmbild av fönstret för identifieringsregel – registervärdet finns](./media/apps-win32-app-management/apps-win32-app-06.png)    
        
            3. Sök baserat på registervärdesträng.
        
                ![Skärmbild av fönstret för identifieringsregel – registervärdesträng är lika med](./media/apps-win32-app-management/apps-win32-app-07.png)    
     
    - **Använd ett anpassat identifieringsskript** – Ange PowerShell-skriptet som ska användas för att identifiera den här appen. 
    
       1. **Skriptfil** – Välj ett PowerShell-skript som ska identifiera förekomsten av appen på klienten. Appen kommer att identifieras när skriptet både returnerar en slutkod med värdet 0 och skriver ett strängvärde till STDOUT.

       2. **Kör skript som 32-bitarsprocess på 64-bitarsklienter** – Välj **Ja** om du vill köra skriptet i en 32-bitarsprocess på 64-bitarsklienter. Välj **Nej** (standard) för att köra skriptet i en 64-bitarsprocess på 64-bitarsklienter. 32-bitarsklienter kör skriptet i en 32-bitarsprocess.

       3. **Framtvinga signaturkontroll av skript** – Välj **Ja** om du vill kontrollera att skriptet har signerats av en betrodd utgivare, vilket innebär att skriptet kan köras utan att varningar eller uppmaningar visas. Skriptet körs oblockerat. Välj **Nej** (standard) om du vill köra skriptet med slutanvändarens bekräftelse utan signaturverifiering.
    
            Intune-agenten kontrollerar resultaten från skriptet. och läser de värden som skrivits av skriptet till standardutdataströmmen (STDOUT), standardfelströmmen (STDERR) och slutkoden. Om skriptet avslutas med ett annat värde än noll misslyckas skriptet och programidentifieringsstatusen är Inte installerad. Om slutkoden är noll och STDOUT innehåller data är programidentifieringsstatus Installerad. 

            > [!NOTE]
            > Microsoft rekommenderar att du kodar skriptet som UTF-8. När skriptet avslutas med värdet 0 betyder det att skriptkörningen lyckades. Den andra utdatakanalen anger att appen identifierades – STDOUT-data anger att appen hittades på klienten. Vi letar inte efter en viss sträng från STDOUT.

2. När du har lagt till din eller dina regler visar du sidan **Beroenden** genom att välja **Nästa**.

## <a name="step-5-dependencies"></a>Steg 5: Beroenden

Appsamband är program som måste installeras innan du kan installera Win32-appen. Du kan kräva att andra appar installeras som beroenden. Mer specifikt måste enheten installera de beroende apparna innan den installerar Win32-appen. Det finns upp till 100 beroenden, vilket innefattar beroenden för eventuella inkluderade beroenden samt själva appen. Du kan lägga till Win32-appsamband först efter att Win32-appen har lagts till och laddats upp till Intune. När Win32-appen har lagts till visas alternativet **Beroenden** i din Win32-apps fönster. 

Alla Win32-programberoenden måste också vara en Win32-app. Den har inte stöd för beroende på andra typer av appar, till exempel enkla MSI LOB- eller Store-appar.

När du lägger till ett appsamband kan du söka baserat på appens namn och utgivare. Dessutom kan du sortera dina tillagda beroenden baserat på appens namn och utgivare. Appsamband som lagts till tidigare kan inte väljas i listan över appsamband. 

Du kan välja huruvida varje oberoende app ska installeras automatiskt. Som standard är alternativet **Installera automatiskt** inställt på **Ja** för varje beroende. Genom att automatiskt installera en beroende app installerar Intune appen på enheten för att uppfylla beroendet innan din Win32-app installeras, även om den beroende appen inte riktas till användaren eller enheten. Observera att ett beroende kan ha rekursiva underordnade beroenden och att varje underordnat beroende installeras innan det huvudsakliga beroendet installeras. Dessutom följer inte installation av beroenden någon installationsordning vid en given beroendenivå.

### <a name="select-the-dependencies"></a>Välj beroenden

Välj de program som måste installeras innan du kan installera Win32-appen på sidan **Beroenden**:
1. Visa fönstret **Lägg till beroende** genom att klicka på **Lägg till**.
3. När du har lagt till beroende appar klickar du på **Välj**.
4. Välj om du vill installera den beroende appen automatiskt genom att välja **Ja** eller **Nej** under kolumnen **Installera automatiskt**.
5. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.

### <a name="understand-additional-dependency-details"></a>Mer information om att förstå beroenden

Slutanvändaren ser Windows-popup-meddelanden som indikerar att beroende appar laddas ned och installeras som en del av installationsprocessen för Win32-app. När en beroende app inte är installerad ser slutanvändaren dessutom vanligtvis något av följande meddelanden:
- Det gick inte att installera 1 eller flera beroende appar
- Kraven för 1 eller flera beroende appar uppfylldes inte
- 1 eller flera beroende appar väntar på enhetsomstart

Om du väljer att inte **automatiskt installera** ett beroende görs inget försök att installera Win32-appen. Dessutom visar då apprapportering att beroendet flaggades som `failed` och anger även en orsak till felet. Du kan visa beroendeinstallationsfelet genom att klicka på ett fel (eller en varning) som anges i Win32-appens [installationsinformation](troubleshoot-app-install.md#win32-app-installation-troubleshooting). 

Varje beroende följer Intune-appåterförsökslogiken för Win32-app (installationsförsök 3 gånger efter en väntetid på 5 minuter) samt det globala omprövningsschemat. Dessutom gäller beroenden endast vid tidpunkten för installation av Win32-appen på enheten. Beroenden gäller inte för avinstallation av en Win32-app. Om du vill ta bort ett beroende måste du klicka på ellipsen (tre punkter) till vänster om den beroende app som finns i slutet av raden i beroendelistan. 

## <a name="step-6---select-scope-tags-optional"></a>Steg 6 – Välj omfångstaggar (valfritt)
Du kan använda omfångstaggar för att bestämma vem som kan se klientappsinformation i Intune. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).

1. Klicka på **Välj omfångstaggar** om du vill lägga till omfångstaggar för appen. 
2. Klicka på **Nästa** för att visa sidan **Tilldelningar**.

## <a name="step-7---assignments"></a>Steg 7 – Tilldelningar

Du kan välja **Obligatorisk**, **Tillgängligt för registrerade enheter** eller **Avinstallera** som grupptilldelning för appen. Mer information finns i [Lägg till grupper för att organisera användare och enheter](~/fundamentals/groups-add.md) och [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

1. Välj en tilldelningstyp för den specifika appen:
    - **Obligatoriskt**: Appen installeras på enheter i de valda grupperna.
    - **Tillgänglig för registrerade enheter**: Användarna installerar appen från företagsportalappen eller företagsportalens webbplats.
    - **Avinstallera**: Appen avinstalleras från enheter i de valda grupperna.
2. Klicka på **Lägg till grupp** och tilldela de grupper som ska använda den här appen.
3. Välj tilldelning baserat på användare och enheter i fönstret **Välj grupper**. 
4. När du har valt dina grupper kan du också ange **Slutanvändaraviseringar**, **Tillgänglighet** och **Tidsgräns för installation**. Mer information finns i [Ange tillgänglighet och meddelanden för Win32-appen](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).
5. Välj **Inkluderade** under **MODE**-kolumnen om du vill undanta grupper av användare så att de inte påverkas av den här apptilldelningen. Fönstret **Redigera tilldelning** visas. Du kan konfigurera **Läge** från att ha varit **Inkluderat** till att bli **Exkluderat**. Stäng dialogrutan **Redigera tilldelning** genom att klicka på **OK**.
6. När du har konfigurerat klart apparnas tilldelningar, så klicka på **Nästa**, så visas sidan **Granska och skapa**.

## <a name="step-8---review--create"></a>Steg 8 – Granska och skapa

1. Granska värdena och inställningarna som du har angett för appen. Verifiera att appinformationen har konfigurerats korrekt.
2. När du är färdig klickar du på **Skapa** för att lägga till appen i Intune.

    Bladet **Översikt** för den branschspecifika appen visas.

Du har nu slutfört stegen för att lägga till en Win32-app i Intune. Information om tilldelning och övervakning av appar finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md) och [Övervaka appinformation och tilldelningar med Microsoft Intune](apps-monitor.md).

## <a name="delivery-optimization"></a>Leveransoptimering

Windows 10 1709-klienter och senare laddar ned Intune Win32-appinnehåll med en komponent för leveransoptimering på Windows 10-klienten. Leveransoptimering ger Peer-to-Peer-funktioner som är aktiverat som standard. Leveransoptimering kan konfigureras av en grupprincip och via Intune-enhetskonfiguration. Mer information finns i [Leveransoptimering för Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

> [!NOTE]
> Du kan också installera en Microsoft-ansluten cacheserver på Configuration Managers distributionsplatser för att cachelagra Intune Win32-AppData. Mer information finns i [Microsoft-ansluten cache i Configuration Manager – Support för Intune Win32-appar](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

## <a name="install-required-and-available-apps-on-devices"></a>Installera nödvändiga och tillgängliga appar på enheter

Slutanvändaren ser popup-meddelanden i Windows för nödvändiga och tillgängliga appinstallationer. Följande bild visar ett exempel på ett popup-meddelande där appinstallationen inte är klar förrän enheten har startats om. 

![Skärmbild som visar popup-meddelanden för en appinstallation i Windows](./media/apps-win32-app-management/apps-win32-app-08.png)    

Följande bild meddelar slutanvändaren att appändringar görs på enheten.

![Skärmbild som meddelar användaren att appändringar görs](./media/apps-win32-app-management/apps-win32-app-09.png)    

## <a name="set-win32-app-availability-and-notifications"></a>Ange tillgänglighet och meddelanden för Win32-appen
Du kan konfigurera starttid och tidsgräns för en Win32-app. Vid starttiden börjar Intune-hanteringstillägget ladda ned och cachelagra appinnehållet för den avsikt som krävs. Appen installeras vid tiden för tidsgränsen. För tillgängliga appar anger starttiden när appen är synlig i företagsportalen och innehållet laddas ned när slutanvändaren begär appen från företagsportalen. Du kan också aktivera en respitperiod för omstart. 

Så här anger du appens tillgänglighet baserat på datum och tid för en app som krävs:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar**.
3. Välj en befintlig **Windows-app (Win32)** i listan. 
4. Välj **Egenskaper** > **Redigera** intill avsnittet **Tilldelning** i appfönstret > **Lägg till grupp** under tilldelningstypen **Obligatorisk**. 
   Observera att apptillgängligheten kan ställas in baserat på tilldelningstypen. **Tilldelningstyp** kan vara **Obligatorisk**, **Tillgängligt för registrerade enheter** eller **Avinstallera**.
5. Ange vilken grupp av användare som ska tilldelas appen genom att välja en grupp i rutan **Välj grupp**. 

    > [!NOTE]
    > Följande ingick i alternativen för **Tilldelningstyp**:<br>
    > - **Obligatoriskt**: Du kan välja att **göra den här appen obligatorisk för alla användare** och/eller att **göra den här appen obligatorisk på alla enheter**.<br>
    > - **Tillgänglig för registrerade enheter**: Du kan välja att **göra appen tillgänglig för alla användare med registrerade enheter**.<br>
    > - **Avinstallera**: Du kan välja att ***avinstallera den här appen för alla användare** och/eller **avinstallera den här appen för alla enheter**.

6. Om du vill ändra alternativ för **Slutanvändarmeddelande** väljer du **Visa alla popup-meddelanden**.
7. Ställ in **Slutanvändarmeddelanden** på **Visa alla popup-meddelanden** i fönstret **Redigera tilldelning**. Observera att du kan ange **Visa alla popup-meddelanden**, **Visa popup-meddelanden om omstart av dator** eller **Dölj alla popup-meddelanden** för **Slutanvändarmeddelanden**.
8. Ange **Ett visst datum och tid** för **Apptillgänglighet** och välj datum och tid. Datumet och tiden anger när appen laddas ned till slutanvändarens enhet. 
9. Ange **Ett visst datum och tid** för **Tidsgräns för appinstallation** och välj datum och tid. Datumet och tiden anger när appen installeras på slutanvändarens enhet. Om fler än en tilldelning har gjorts för samma användare eller enhet väljs den tidigaste tidsgränsen för appinstallation.

10. Klicka på **Aktiverad** bredvid **Respitperiod för omstart**. Respitperioden för omstart startar så snart appen har installerats på enheten. När den är inaktiverad kan enheten startas om utan varning. <br>Du kan anpassa följande alternativ:
    - **Respitperiod för omstart av enhet (minuter)** : Standardvärdet är 1440 minuter (24 timmar). Det här värdet kan vara högst 2 veckor.
    - **Välj när dialogrutan för nedräkning till omstart ska visas innan omstart sker (minuter)** : Standardvärdet är 15 minuter.
    - **Tillåt användaren att snooza omstartsmeddelande**: Du kan välja **Ja** eller **Nej**.
        - **Välj snooze-tid (minuter)** : Standardvärdet är 240 minuter (4 timmar). Snooze-tiden får inte vara större än respitperioden för omstart.

11. Klicka på **Granska och spara**.

## <a name="toast-notifications-for-win32-apps"></a>Popup-meddelanden för Win32-appar 
Om det behövs kan du förhindra att popup-meddelanden per apptilldelning visas för slutanvändarna. Gå till Intune, välj **Appar** > **Alla appar** > välj appen > **Tilldelningar** > **Inkludera grupper**. 

> [!NOTE]
> Win32-appar som installerats via Intune-hanteringstillägget avinstalleras inte på oregistrerade enheter. Administratörer kan använda tilldelningsundantag för att inte erbjuda Win32-appar till BYOD-enheter.

## <a name="troubleshoot-win32-app-issues"></a>Felsöka problem med Win32-appar
Agentloggar på klientdatorn finns vanligtvis i `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Du kan använda `CMTrace.exe` för att visa dessa loggfiler. Mer information finns i [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace).

![Skärmbild av agentloggar på klientdatorn](./media/apps-win32-app-management/apps-win32-app-10.png)    

> [!IMPORTANT]
> För att tillåta korrekt installation och körning av verksamhetsspecifika Win32-appar bör inställningar för program mot skadlig kod undanta följande kataloger från att genomsökas:<p>
> **På X64-klientdatorer**:<br>
> *C:\Program Files (x86)\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **På X86-klientdatorer**:<br>
> *C:\Program Files\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="detecting-the-win32-app-file-version-using-powershell"></a>Identifiera versionen för Win32-appfilen med hjälp av PowerShell

Om du har svårt att identifiera versionen för Win32-appfilen kan du använda eller ändra följande PowerShell-kommando:

``` PowerShell

$FileVersion = [System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion
#The below line trims the spaces before and after the version name
$FileVersion = $FileVersion.Trim();
if ("<file version of successfully detected file>" -eq $FileVersion)
{
#Write the version to STDOUT by default
$FileVersion
exit 0
}
else
{
#Exit with non-zero failure code
exit 1
}
```

I kommandot ovan ersätter PowerShell strängen `<path to binary file>` med sökvägen till Win32-appfilen. Ett exempel på en sökväg skulle se ut ungefär så här:<br>
`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

Dessutom måste du ersätta strängen `<file version of successfully detected file>` med filversionen som du vill identifiera. Ett exempel på en filversionssträng skulle se ut ungefär så här:<br>
`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

Om du vill hämta versionsinformation om Win32-appen kan du använda följande PowerShell-kommando:

``` PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

I PowerShell-kommandot ovan ska du ersätta `<path to binary file>` med din sökväg till filen.

### <a name="additional-troubleshooting-areas-to-consider"></a>Ytterligare felsökningsområden att tänka på
- Kontrollera målet och att agenten är installerad på enheten – En Win32-app som riktas mot en grupp eller ett PowerShell-skript som riktas mot en grupp skapar agentinstallationsprinciper för säkerhetsgruppen.
- Kontrollera operativsystemversionen – Windows 10 1607 och senare.  
- Kontrollera Windows 10 SKU – Windows 10 S eller Windows-versioner som körs med S-läge aktiverat har inte stöd för MSI-installation.

Mer information om felsökning av Win32-appar finns i [Felsökning av Win32-appinstallation](troubleshoot-app-install.md#win32-app-installation-troubleshooting).

## <a name="next-steps"></a>Nästa steg

- Mer information om hur du lägger till appar i Intune finns i [Lägga till appar i Microsoft Intune](apps-add.md).
