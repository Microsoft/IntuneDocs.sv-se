---
title: Lägga till Win32-appar i Microsoft Intune
titlesuffix: ''
description: Lär dig hur du lägger till, distribuerar och hanterar Win32-appar med Microsoft Intune. Det här avsnittet innehåller en översikt över Intunes leverans- och hanteringsfunktioner för Win32-appar, samt felsökningsinformation för Win32-appar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: ba77c14e470ed75a87f44adcaf0ba9b98cd06438
ms.sourcegitcommit: e0d55bdda1a818ffe4cfc0ef0592833e22f65a89
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290765"
---
# <a name="intune-standalone---win32-app-management"></a>Fristående Intune – Win32-apphantering

Fristående Intune ger tillgång till bättre hanteringsfunktioner för Win32-appar. Molnanslutna kunder kan använda Configuration Manager för Win32-apphantering, men kunder med fristående Intune har tillgång till bättre hanteringsfunktioner för sina verksamhetsspecifika Win32-appar. Det här avsnittet innehåller en översikt över Intunes hanterings- och felsökningsfunktioner för Win32-appar.

## <a name="prerequisites"></a>Krav

- Windows 10 version 1607 eller senare (Enterprise- och Pro Education-versionerna)
- Windows 10-klienten måste vara: 
    - ansluten till Azure Active Directory (AAD) eller Hybrid Azure Active Directory och
    - registrerad i Intune (MDM-hanterad)
- Storleken för Windows-program är högst 8 GB per app

## <a name="prepare-the-win32-app-content-for-upload"></a>Förbereda Win32-appinnehållet för uppladdning

Använd [förberedelseverktyget för Win32-innehåll](https://go.microsoft.com/fwlink/?linkid=2065730) för att förbearbeta Win32-appar. Verktyget konverterar programinstallationsfilerna till formatet *.intunewin*. Verktyget identifierar även vissa av de attribut som krävs av Intune för att fastställa programmets installationstillstånd. När du har använt det här verktyget med appinstallationsmappen kan du skapa en Win32-app i Intune-konsolen.

Du kan ladda ned [förberedelseverktyget för Win32-innehåll](https://go.microsoft.com/fwlink/?linkid=2065730) från GitHub.

### <a name="available-command-line-parameters"></a>Tillgängliga kommandoradsparametrar 

|    **Kommandoradsparameter**    |    **Beskrivning**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Hjälp    |
|    `-c <setup_folder>`     |    Installationsmapp för alla installationsfiler.    |
|   ` -s <setup_file>`     |    Installationsfil (till exempel *setup.exe* eller *setup.msi*).    |
|    `-o <output_folder>`     |    Utdatamapp för den genererade *.intunewin*-filen.    |
|    `-q`       |    Tyst läge    |

### <a name="example-commands"></a>Exempelkommandon

|    **Exempelkommando**    |    **Beskrivning**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Det här kommandot visar användningsinformation för verktyget.    |
|    `IntuneWinAppUtil -c <setup_folder> -s <source_setup_file> -o <output_folder> <-q>`    |    Det här kommandot genererar `.intunewin`-filen från den angivna källmappen och installationsfilen. För MSI-installationsfilen hämtar det här verktyget nödvändig information för Intune. Om `-q` anges körs kommandot i tyst läge och om utdatafilen redan finns skrivs den över. Om utdatamappen inte finns, skapas den automatiskt.    |

När du genererar en *.intunewin*-fil placerar du alla de filer som du måste referera till i en undermapp i installationsmappen. Referera sedan till den specifika fil du behöver med en relativ sökväg. Exempel:

**Installationens källmapp:** *c:\testapp\v1.0*<br>
**Licensfil:** *c:\testapp\v1.0\licenses\license.txt*

Referera till filen *license.txt* med hjälp av den relativa sökvägen *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Skapa, tilldela och övervaka en Win32-app

Precis som med en verksamhetsspecifik app kan du lägga till en Win32-app i Microsoft Intune. Den här typen av app skrivs vanligtvis internt på företaget eller av en tredje part. Följande steg beskriver riktlinjer som hjälper dig att lägga till en Windows-app i Intune.

### <a name="step-1-specify-the-software-setup-file"></a>Steg 1: Ange programinstallationsfilen

1.  Logga in på [Azure Portal](https://portal.azure.com/).
2.  Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3.  I fönstret **Intune** väljer du **Klientappar** > **Appar** > **Lägg till**.
4.  I appfönstret **Lägg till** väljer du **Windows-app (Win32)** från den nedrullningsbara listan.

    ![Skärmbild av bladet Lägg till app – Listrutan Lägg till typ](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>Steg 2: Ladda upp appaketfilen

1.  I fönstret **Lägg till app** väljer du **Appaketfil** för att välja en fil. Fönstret Appaketfil visas.

    ![Skärmbild av bladet Appaketfil](./media/apps-win32-app-02.png)

2.  I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en Windows-installationsfil med tillägget *.intunewin*.

    > [!IMPORTANT]
    > Se till att ha den senaste versionen av förberedelseverktyget för Microsoft Win32-innehåll. Om du inte använder den senaste versionen visas en varning om att appen har paketerats med en äldre version av förberedelseverktyget för Microsoft Win32-innehåll. 

3.  Välj **OK** när du är klar.

### <a name="step-3-configure-app-information"></a>Steg 3: Konfigurera appinformation

1.  I fönstret **Lägg till app** väljer du **Appinformation** för att konfigurera appen.
2.  Konfigurera följande information i fönstret **Appinformation**. Vissa värden i det här fönstret kan fyllas i automatiskt.
    - **Namn**: Ange namnet på appen så som det visas i företagsportalen. Om samma appnamn förekommer två gånger visas varje app på företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas i företagsportalen.
    - **Utgivar**e: Ange namnet på appens utgivare.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller välj en kategori som du har skapat. Kategorier gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Visa appen tydligt på huvudsidan för företagsportalen när användare söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om appen. Webbadressen visas i företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation om appen. Webbadressen visas i företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appägaren. Ett exempel är **Personalavdelningen**.
    - **Kommentarer**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp**: Ladda upp en ikon som är associerad med appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
3.  Välj **OK** när du är klar.

### <a name="step-4-configure-app-installation-details"></a>Steg 4: Konfigurera information om appinstallationen
1.  I **Lägg till app** väljer du **Program** för att konfigurera appinstallationen och borttagningskommandona för appen.
2.  Lägg till den fullständig kommandoraden för installationen för att installera appen. 

    Om appfilnamnet exempelvis är **MyApp123** lägger du till följande: `msiexec /i “MyApp123.msi”`

3.  Lägg till den fullständiga kommandoraden för avinstallation av appen baserat på appens GUID. 

    Exempelvis: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > Du kan konfigurera att en Win32-app installeras i kontexten **Användare** eller **System**. Kontexten **Användare** avser bara en viss användare. Kontexten **System** avser alla användare av en Windows 10-enhet.
    >
    > Slutanvändare behöver inte vara inloggade på enheten för att installera Win32-appar.

4.  Välj **OK** när du är klar.

### <a name="step-5-configure-app-requirements"></a>Steg 5: Konfigurera appkrav

1.  I fönstret **Lägg till app** väljer du **Krav** för att konfigurera de krav som enheter måste uppfylla innan appen installeras.
2.  I fönstret **Krav** konfigurerar du följande information. Vissa värden i det här fönstret kan fyllas i automatiskt.
    - **Operativsystemarkitektur**: Välj de arkitekturer som krävs för att installera appen.
    - **Lägsta operativsystemversion**: Välj det lägsta operativsystem som krävs för att installera appen.
    - **Diskutrymme som krävs (MB)**: Om du vill kan du lägga till mängden ledigt diskutrymme som krävs på systemenheten för att installera appen.
    - **Fysiskt minne som krävs (MB)**: Om du vill kan du lägga till mängden fysiskt minne (RAM) som krävs för att installera appen.
    - **Lägsta antal logiska processorer som krävs**: Om du vill kan du lägga till det lägsta antal logiska processorer som krävs för att installera appen.
    - **Lägsta processorhastighet som krävs (MHz)**: Om du vill kan du lägga till den lägsta processorhastighet som krävs för att installera appen.
3.  Välj **OK** när du är klar.

### <a name="step-6-configure-app-detection-rules"></a>Steg 6: Konfigurera appidentifieringsregler

1.  I fönstret **Lägg till app** väljer du **Identifieringsregler** för att konfigurera regler som identifierar förekomsten av appen.
2.  I **Regelformat** väljer du hur förekomsten av appen ska identifieras. Du kan välja att antingen konfigurera identifieringsreglerna manuellt eller använda ett anpassat skript för att identifiera förekomsten av appen. Du måste välja minst en identifieringsregel. 

    > [!NOTE]
    > I fönstret **Identifieringsregler** kan du välja att lägga till flera regler. Villkoren för **alla** regler måste vara uppfyllda för att appen ska identifieras.

    - **Ställ in identifieringsregler manuellt** – Du kan välja någon av följande regeltyper:
        1.  **MSI** – Verifiera baserat på MSI-versionskontroll. Det här alternativet kan endast läggas till en gång. När du väljer den här regeltypen visas två inställningar:
            - **MSI-produktkod** – Lägg till en giltig MSI-produktkod för appen.
            - **Kontroll av MSI-produktversion** – Välj **Ja** om du vill kontrollera MSI-produktversionen förutom MSI-produktkoden.
        2.  **Fil** – Verifiera baserat på fil- eller mappidentifiering, datum, version eller storlek.
            - **Sökväg** – Den fullständiga sökvägen till mappen som innehåller filen eller mappen som ska identifieras.
            - **Fil eller mapp** – Filen eller mappen som ska identifieras.
            - **Identifieringsmetod** – Välj vilken typ av identifieringsmetod som ska användas för att verifiera förekomsten av appen.
            - **Kopplat till en 32-bitarsapp på 64-bitarsklienter** – Välj **Ja** om du vill expandera miljövariabler för sökvägar i 32-bitarskontexten på 64-bitarsklienter. Välj **Nej** (standard) om du vill expandera sökvägsvariabler i 64-bitarskontexten på 64-bitarsklienter. 32-bitarsklienter använder alltid 32-bitarskontexten.
            
            **Exempel på filbaserad identifiering**
            1.  Kontrollera om filen finns.
         
                ![Skärmbild av fönstret för identifieringsregel – filen finns](./media/apps-win32-app-03.png)
        
            2.  Kontrollera om mappen finns.
         
                ![Skärmbild av fönstret för identifieringsregel – mappen finns](./media/apps-win32-app-04.png)
        
        3. **Register** – Verifiera baserat på värde, sträng, heltal eller version.
            - **Nyckelsökväg** – Den fullständiga sökvägen till registerposten som innehåller värdet som ska identifieras.
            - **Värdenamn** – Namnet på registervärdet som ska identifieras. Om det här värdet är tomt sker identifieringen mot nyckeln. (Det förvalda) värdet för en nyckel används som identifieringsvärde om identifieringsmetoden är en annan än den som identifierar förekomsten av filen eller mappen.
            - **Identifieringsmetod** – Välj vilken typ av identifieringsmetod som ska användas för att verifiera förekomsten av appen.
            - **Kopplat till en 32-bitarsapp på 64-bitarsklienter** – Välj **Ja** om du vill söka i 32-bitarsregistret på 64-bitarsklienter. Välj **Nej** (standard) om du vill söka i 64-bitarsregistret på 64-bitarsklienter. 32-bitarsklienter söker alltid i 32-bitarsregistret.
            
            **Exempel för registerbaserad identifiering**
            1.  Sök baserat på om registernyckeln finns.
            
                ![Skärmbild av fönstret för identifieringsregel – registernyckeln finns](./media/apps-win32-app-05.png)    
            
            2.  Kontrollera om det finns något registervärde.
        
                ![Skärmbild av fönstret för identifieringsregel – registervärdet finns](./media/apps-win32-app-06.png)    
        
            3.  Sök baserat på registervärdesträng.
        
                ![Skärmbild av fönstret för identifieringsregel – registervärdesträng är lika med](./media/apps-win32-app-07.png)    
     
    - **Använd ett anpassat identifieringsskript** – Ange PowerShell-skriptet som ska användas för att identifiera den här appen. 
    
        1.  **Skriptfil** – Välj ett PowerShell-skript som ska identifiera förekomsten av appen på klienten. Appen kommer att identifieras när skriptet både returnerar en slutkod med värdet 0 och skriver ett strängvärde till STDOUT.

        2.  **Kör skript som 32-bitarsprocess på 64-bitarsklienter** – Välj **Ja** om du vill köra skriptet i en 32-bitarsprocess på 64-bitarsklienter. Välj **Nej** (standard) för att köra skriptet i en 64-bitarsprocess på 64-bitarsklienter. 32-bitarsklienter kör skriptet i en 32-bitarsprocess.

        3.  **Framtvinga signaturkontroll av skript** – Välj **Ja** om du vill kontrollera att skriptet har signerats av en betrodd utgivare, vilket innebär att skriptet kan köras utan att varningar eller uppmaningar visas. Skriptet körs oblockerat. Välj **Nej** (standard) om du vill köra skriptet med slutanvändarens bekräftelse utan signaturverifiering.
    
            Intune-agenten kontrollerar resultaten från skriptet. och läser de värden som skrivits av skriptet till standardutdataströmmen (STDOUT), standardfelströmmen (STDERR) och slutkoden. Om skriptet avslutas med ett annat värde än noll misslyckas skriptet och programidentifieringsstatusen är Inte installerad. Om slutkoden är noll och STDOUT innehåller data är programidentifieringsstatus Installerad. 

            > [!NOTE]
            > När skriptet avslutas med värdet 0 betyder det att skriptkörningen lyckades. Den andra utdatakanalen anger att appen identifierades – STDOUT-data anger att appen hittades på klienten. Vi letar inte efter en viss sträng från STDOUT.

        4.  När du har lagt till dina regler väljer du **Lägg till** > **OK**.

### <a name="step-7-configure-app-return-codes"></a>Steg 7: Konfigurera appreturkoder

1.  I fönstret **Lägg till app** väljer du **Returkoder** för att lägga till returkoderna som används för att ange antingen hur appinstallationen hanterar återförsök eller beteendet efter installationen. Poster för returkoder läggs till som standard när appen skapas. Du kan dock lägga till ytterligare returkoder eller ändra befintliga returkoder. 
2.  I fönstret **Returkoder** lägger du till ytterligare returkoder eller ändrar befintliga returkoder.
    - **Misslyckades** – Returvärdet som anger ett appinstallationsfel.
    - **Hård omstart** – Returkoden för hård omstart tillåter inte att nästa Win32-app installeras på klienten utan omstart. 
    - **Mjuk omstart** – Returkoden för mjuk omstart tillåter att nästa Win32-app installeras utan att klienten måste startas om. Omstart krävs för att slutföra installationen av det aktuella programmet.
    - **Försök igen** – Agenten för returkoden för återförsök försöker installera appen tre gånger. Den väntar fem minuter mellan varje försök. 
    - **Lyckades** – Returvärdet som anger att appen installerades.
3.  Välj **OK** när du har lagt till eller ändrat listan över returkoder.

### <a name="step-8-add-the-app"></a>Steg 8: Lägg till appen

1.  I fönstret **Lägg till app** kontrollerar du att appinformationen är rätt konfigurerad.
2.  Välj **Lägg till** för att ladda upp appen till Intune.

### <a name="step-9-assign-the-app"></a>Steg 9: Tilldela appen

1.  I appfönstret väljer du **Tilldelningar**.
2.  Välj **Lägg till grupp** för att öppna fönstret **Lägg till grupp** som är relaterat till appen.
3.  Välj en **Tilldelningstyp** för den specifika appen:
    - **Tillgänglig för registrerade enheter**: Användarna installerar appen från företagsportalappen eller företagsportalens webbplats.
    - **Obligatoriskt**: Appen installeras på enheter i de valda grupperna.
    - **Avinstallera**: Appen avinstalleras från enheter i de valda grupperna.
4.  Välj **Grupper som omfattas** och tilldela de grupper som ska använda den här appen.
5.  Klicka på **OK** i fönstret **Tilldela** för att slutföra valet av inkluderade grupper.
6.  Välj **Exkludera grupper** om du vill undanta grupper av användare så att de inte påverkas av den här apptilldelningen.
7.  I fönstret **Lägg till grupp** väljer du **OK**.
8.  I appfönstret **Tilldelningar** väljer du **Spara**.

Du har nu slutfört stegen för att lägga till en Win32-app i Intune. Information om tilldelning och övervakning av appar finns i [Tilldela appar till grupper med Microsoft Intune](https://docs.microsoft.com/intune/apps-deploy) och [Övervaka appinformation och tilldelningar med Microsoft Intune](https://docs.microsoft.com/intune/apps-monitor).

## <a name="delivery-optimization"></a>Leveransoptimering

Windows 10 RS3 och högre klienter hämtar Intune Win32-appinnehåll med en komponent för leveransoptimering på Windows 10-klienten. Leveransoptimering ger Peer-to-Peer-funktioner som är aktiverat som standard. Leveransoptimering kan konfigureras av en grupprincip och i framtiden via Intune MDM. Mer information finns i [leveransoptimering för Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Installera nödvändiga och tillgängliga appar på enheter

Slutanvändaren ser popup-meddelanden i Windows för nödvändiga och tillgängliga appinstallationer. Följande bild visar ett exempel på ett popup-meddelande där appinstallationen inte är klar förrän enheten har startats om. 

![Skärmbild som visar popup-meddelanden för en appinstallation i Windows](./media/apps-win32-app-08.png)    

Följande bild meddelar slutanvändaren att appändringar görs på enheten.

![Skärmbild som meddelar användaren att appändringar görs](./media/apps-win32-app-09.png)    

## <a name="toast-notifications-for-win32-apps"></a>Popup-meddelanden för Win32-appar 
Om det behövs kan du förhindra att popup-meddelanden per apptilldelning visas för slutanvändarna. Från Intune, väljer du **Klientappar** > **Appar** > välj appen > **Tilldelningar** > **Inkludera grupper**. 

## <a name="troubleshoot-win32-app-issues"></a>Felsöka problem med Win32-appar
Agentloggar på klientdatorn finns vanligtvis i `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Du kan använda `CMTrace.exe` för att visa dessa loggfiler. *CMTrace.exe* kan laddas ned från [SCCM-klientverktygen](https://docs.microsoft.com/sccm/core/support/tools). 

![Skärmbild av agentloggar på klientdatorn](./media/apps-win32-app-10.png)    

### <a name="troubleshooting-areas-to-consider"></a>Felsökningsområden att tänka på
- Kontrollera målet och att agenten är installerad på enheten – En Win32-app som riktas mot en grupp eller ett PowerShell-skript som riktas mot en grupp skapar agentinstallationsprinciper för säkerhetsgruppen.
- Kontrollera operativsystemversionen – Windows 10 1607 och senare.  
- Kontrollera Windows 10 SKU – Windows 10 S eller Windows-versioner som körs med S-läge aktiverat har inte stöd för MSI-installation.

## <a name="next-steps"></a>Nästa steg

- Mer information om hur du lägger till appar i Intune finns i [Lägga till appar i Microsoft Intune](apps-add.md).
