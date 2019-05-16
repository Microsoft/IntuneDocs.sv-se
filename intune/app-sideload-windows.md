---
title: Separat inläsning av appar för Windows och Windows Phone
titleSuffix: Microsoft Intune
description: Lär dig hur du signerar verksamhetsspecifika appar, så att du kan använda Intune för att distribuera dem.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8652d260849537d1e0b504f5d309a3ab2708e5cd
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587526"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Signera verksamhetsspecifika appar så att de kan distribueras till Windows-enheter med Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Som Intune-administratör kan du distribuera verksamhetsspecifika (LOB) appar till Windows- och Windows 10 Mobile-enheter, inklusive företagsportalappen. För att distribuera .appx- eller .xap-appar till Windows 10- och Windows 10 Mobile-enheter eller för att distribuera LOB-app till Windows 8.1 eller Windows Phone 8.1-enheter, måste du få ett **Symantec-företagscertifikat för kodsignering**. Endast Symantec-certifikatet är betrott för dessa appar för respektive Windows-enhet. Du kan använda en egen certifikatutfärdare för Windows 10-appar och "universella" appar. Detta certifikat krävs för att:

-   Signera företagsportalappen för distribution till datorer med Windows, Windows 10 Mobile-enheter och Windows Phone-enheter

-   Signera verksamhetsspecifika appar så att Intune kan distribuera dem till Windows-enheter

Stegen nedan hjälper dig att få nödvändiga certifikat och signera appen. Du måste registrera dig som Microsoft-utvecklare och sedan köpa ett Symantec-certifikat.


1. **Registrera dig som Microsoft-utvecklare**<br>
   [Registrera dig som Microsoft-utvecklare](https://go.microsoft.com/fwlink/?LinkId=268442) med hjälp av företagets kontoinformation som du använde när du loggade in för att köpa ditt företagskonto. Den här begäran måste godkännas av en företagsrepresentant innan du får ett signeringscertifikat med kod.

2. **Få ett företagskonto från Symantec**<br>
  Köpa ett certifikat från [Symantec-webbplatsen](https://go.microsoft.com/fwlink/?LinkId=268441) med hjälp av ditt Symantec-ID. När du har köpt certifikatet får företagets godkännare, som du angav när du registrerade dig som Microsoft-utvecklare, ett e-postmeddelande där personen ombeds godkänna certifikatbegäran. Du hittar mer information om kraven för Symantec-certifikat under [Varför Windows Phone kräver ett Symantec-certifikat](https://technet.microsoft.com/library/dn764959.aspx#BKMK_Symantec) Vanliga frågor och svar om registrering av Windows-enhet.

3.  **Importera certifikat**<br>
    När din begäran har godkänts, kommer du att få ett e-postmeddelande som innehåller instruktioner om hur du importerar certifikat. Följ anvisningarna i e-postmeddelandet för att importera certifikaten.

4.  **Verifiera importerade certifikat**<br>
    Du kan kontrollera att certifikaten har importerats genom att gå till snapin-modulen **Certifikat**, högerklicka på **Certifikat** och välja **Sök efter certifikat**. I fältet **Innehåller** skriver du ”Symantec” och klickar på **Sök nu**. De certifikat som du har importerat ska visas i resultaten.

    ![Certifikatresultaten visas i listan i dialogrutan Sök efter certifikat](./media/wit.gif)

5. **Exportera ett signeringscertifikat**<br>
    När du har kontrollerat att certifikaten finns kan du exportera .pfx-filen så att du kan signera företagsportalen. Välj Symantec-certifikatet med **avsett syfte** ”kodsignering.” Högerklicka på det kodsignerade certifikatet och välj **Exportera**.

    ![Exportera signeringscertifikatet](./media/wit-walk-cert2.gif)

    I **Guiden Exportera certifikat**väljer du **Ja, exportera den privata nyckeln** och klickar sedan på **Nästa**. Välj **Personal Information Exchange –PKCS #12 (.PFX)** och markera **Inkludera om möjligt alla certifikat i certifieringssökvägen**. Slutför guiden. Mer information finns i [Exportera certifikat med privat nyckel](https://go.microsoft.com/fwlink/?LinkID=203031).

6.  **Överför appen till Intune**<br>
    Överför den signerade appfilen och ditt kodsigneringscertifikat för att göra appen tillgänglig för dina slutanvändare.

    1.  I Azure-portalen klickar du på **Administration** &gt; **Windows Phone**.

    2.  Klicka på **Överför signerad appfil** och logga in med ditt administratörs-ID för Intune.

    3.  Lägg till certifikatfilen (.pfx) som du exporterade till **Kodsigneringscertifikat** och skapa ett lösenord för certifikatet.

    4.  Slutför guiden.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>Exempel: Hämta, signera och distribuera företagsportalappen för Windows-enheter

Du kan distribuera företagsportalappen till Windows-enheter, inklusive Windows Phone- och Windows 10 Mobile-enheter med Intune istället för att installera från Microsoft Store. Du måste ladda ned företagsportalappen och signera den med ditt certifikat.  Detta är bara nödvändigt om användarna inte kommer att använda företagsbutiken och du vill distribuera företagsportalen till Windows Phone 8.1-enheter.


1.  **Ladda ned företagsportalen**

    För att distribuera företagsportalappen med Intune, kan du hämta [Microsoft Intune-företagsportalappen för Windows Phone 8.1](https://go.microsoft.com/fwlink/?LinkId=615799) från Download Center och kör den självuppackande filen(.exe). Denna fil innehåller två filer:

    -   CompanyPortal.appx – Installationsappen för företagsportalen för Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1 – Ett Powershell-skript som du kan använda för att signera företagsportalappfilen så att den kan användas för Windows Phone 8.1-enheter

    Du kan också hämta Windows Phone 8.1-företagsportalen (offline-licensierat paket) eller Windows 10-företagsportalen (offline-licensierat paket) från [Microsoft Store för företag](https://businessstore.microsoft.com/). Företagsportalappen måste anskaffas med en offline-licens och lämpligt paket hämtas för användning offline. Listor med plattformar för Windows 8 och Windows Phone 8 i urvalet avser deras 8.1-motsvarigheter. Mer information om hur du gör detta med Intune finns i [Hantera appar som du har köpt från Microsoft Store för företag](windows-store-for-business.md).

2.  **Hämta Windows Phone SDK** Hämta Windows Phone SDK 8.0](https://go.microsoft.com/fwlink/?LinkId=615570) och installera SDK:n på datorn. Detta SDK behövs för att generera en token för programregistrering.

3.  **Generera en AETX-fil** Generera en tokenfil (.aetx) för programregistrering från Symantec PFX-filen med AETGenerator.exe, en del av Windows Phone SDK 8.0. Instruktioner om hur du skapar en AETX-fil hittar du på [Hur man genererar en tokenfil för programregistrering för Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx)

4.  **Hämta Windows SDK för Windows 8.1**Hämta och installera [Windows Phone SDK](https://go.microsoft.com/fwlink/?LinkId=613525) (https://go.microsoft.com/fwlink/?LinkId=613525). Observera att det Powershell-skript som medföljer företagsportalappen använder standardinstallationsplatsen, `${env:ProgramFiles(x86)}\Windows Kits\8.1`. Om du installerar någon annanstans måste du inkludera platsen i en cmdlet-parameter.

5.  **Kodsignera appen med Powershell** Öppna **Windows Powershell** som administratör på värddatorn där Windows SDK och Symantec-certifikatet med mobil kodsignering för företag har installerats, navigera till Sign-WinPhoneCompanyPortal.ps1-filen och kör skriptet.

    **Exempel 1**

    ```PowerShell
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    Detta exempel signerar CompanyPortal.appx i C:\temp\ och skapar CompanyPortalEnterpriseSigned.appx. Det skulle använda PFX-lösenordet 1234 och läsa publicerings-ID:t från PFX-filen. Det läser även företags-ID:t från cert.aetx-filen.

    **Exempel 2**

    ```PowerShell
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    Detta exempel signerar CompanyPortal.appx i C:\temp\ och skapar CompanyPortalEnterpriseSigned.appx. Det skulle använda PFX-lösenordet 1234 och använda det angivna publicerings-ID:t.

    **Parametrar:**

    -   `-InputAppx` – Den lokala sökvägen till CompanyPortal.appx-filen med enkla citattecken. Till exempel 'C:\temp\CompanyPortal.appx'

    -   `-OutputAppx` – Den lokala sökvägen och filnamnet för den signerade företagsportalappen med enkla citattecken. Till exempel 'C:\temp\CompanyPortalEnterpriseSigned.appx'

    -   `-PfxFilePath` – Den lokala sökvägen och filnamnet för den exporterade PFX-filen för Symantec-certifikatet. Till exempel 'C:\signing\cert.pfx'

    -   `-PfxPassword` – Det lösenord som används för att signera PFX-filen med enkla citattecken. Till exempel '1234'

    -   `-AetxPath` – Den lokala sökvägen till .aetx-filen som används för att läsa företags-ID:t om företagsargumentet inte har definierats. Antingen detta argument eller företags-ID måste tillhandahållas. Till exempel 'C:\signing\cert.aetx'

    -   `-PublisherId` – Publicerings-ID för företaget. Om det ej finns, används ämnes-fältet i Symantec-certifikatet med mobil kodsignering för företag. Till exempel 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1'

    -   `-SdkPath` – Sökvägen till rotkatalogen på Windows SDK för Windows 8.1. Detta argument är frivilligt och är som standard ${env:ProgramFiles(x86)}\Windows Kits\8.1.

    -   `-EnterpriseId` – Företags-ID. Antingen detta argument eller 'AetxPath' måste tillhandahållas. Om det här argumentet inte anges, läses företags-ID:t från AETX-filen. Till exempel, 1000000001

6.  Distribuera Windows Phone 8.1-företagsportalappen (SSP.appx). Om du behöver hjälp kan du läsa [Så här lägger du till verksamhetsspecifika Windows Phone-appar (LOB)](lob-apps-windows-phone.md).

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Så här förnyar du Symantec-företagscertifikatet för kodsignering

Symantec-certifikatet som används för att distribuera Windows- och Windows Phone-mobilappar måste förnyas regelbundet.

1.  Ett e-postmeddelande om förnyelsen skickas från Symantec ungefär 14 dagar innan certifikatet upphör att gälla. E-postmeddelandet innehåller anvisningar från Symantec om att du bör förnya ditt företagscertifikat.

    Mer information om Symantec-certifikat finns på [www.symantec.com](https://www.symantec.com). Du kan också ringa 1-877-438-8776 eller 1-650-426-3400.

2.  Gå till webbplatsen (till exempel [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) och logga in med utgivar-ID:t för Symantec och e-postadressen som är associerad med certifikatet. Kom ihåg att använda samma dator för att starta förnyelsen som du använde för att hämta certifikatet.

3.  När förnyelsen är godkänd och betald kan du hämta certifikatet.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Hur du installerar det uppdaterade certifikatet för verksamhetsspecifika (LOB) appar

1.  Signera den senaste versionen av din verksamhetsspecifika app.

2.  Öppna Azure-portalen och gå till **Administratör** &gt; **Hantering av mobilenheter** &gt; **Windows Phone** och klicka på **Överför signerad app**.

3.  Överför den nyligen signerade företagsportalen. Du behöver den nyligen signerade SSP.xap och den nya PFX-filen som du har fått från Symantec eller den programregistreringstoken som har skapats med den nya PFX-filen.

4.  När uppladdningen är klar tar du bort den gamla företagsportalversionen i arbetsytan **Programvara**  .

5.  Signera alla nya och uppdaterade branschspecifika företagsappar med det nya certifikatet. Befintliga program behöver inte vara signeras på nytt eller omdistribueras.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Distribuera Windows 10-företagsportalsappen
Du kan distribuera Windows 10 företagsportalappen manuellt direkt från Intune, även om du inte har integrerat Intune med Microsoft Store för företag.

 > [!NOTE]
 > Det här alternativet kräver att du distribuerar manuella uppdateringar varje gång som en appuppdatering släpps.

1. Logga in på kontot i [Microsoft Store för företag](https://www.microsoft.com/business-store) och hämta **offline-licensversionen** av företagsportalappen.  
2. När du har införskaffat appen markerar du den på sidan **Inventering**.  
3. Välj **Windows 10 – alla enheter** som **plattform**, sedan lämplig **arkitektur** och ladda ned. Det behövs inte någon applicensfil för den här appen.
![Bild av Windows 10 X86-paketinformation för nedladdning](./media/Win10CP-all-devices.png)
4. Hämta alla paket under Nödvändiga ramverk. Detta måste göras för x86-, x64- och ARM-arkitekturer – vilket ger totalt 9 paket så som visas nedan.

![Bild av beroendefiler att hämta ](./media/Win10CP-dependent-files.png)
5. Innan du skickar företagsportalappen till Intune så skapa en mapp (t.ex. C:\Company Portal) med paketen strukturerade på följande sätt:
   1. Placera företagsportalspaketet i C:\Company Portal. Skapa även en undermapp för beroenden på den här platsen.  
   ![Bild av beroendemappen sparad med APPXBUN-filen](./media/Win10CP-Dependencies-save.png)
   2. Placera de nio beroendepaketen i mappen Dependencies.  
   Om beroendena inte placeras i det här formatet kommer Intune inte att kunna känna igen och överföra dem under paketöverföringen, vilket innebär att överföringen kommer att misslyckas med följande fel.  
   ![Felmeddelande – Windows-appberoendet måste anges.](./media/Win10CP-error-message.png)
6. Gå tillbaka till Intune och överför företagsportalsappen som en ny app. Distribuera den som en obligatorisk app för den önskade uppsättningen målanvändare.  

Mer information om hur Intune hanterar beroenden för universella appar finns i [Distribuera ett appxbundle med beroenden via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Hur uppdaterar jag företagsportalen på mina användaress enheter om de redan har installerat de äldre apparna?
Om användarna redan har installerat företagsportalsapparna för Windows 8.1 eller Windows Phone 8.1 från Store, så borde de sedan uppdateras automatiskt till den nya versionen, utan att det krävs några åtgärder från dig eller användaren. Om uppdateringen inte genomförs, så be dina användare att kontrollera om de har aktiverat automatiska uppdateringar för Store-appar på sina enheter.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min separat inlästa företagsportalsapp för Windows 8.1 till företagsportalsappen för Windows 10?
Våra rekommenderade migreringssökväg är att ta bort distributionen för Windows 8.1-företagsportalappen genom att ange distributionsåtgärden till Avinstallera. När detta är gjort kan du distribuera företagsportalappen för Windows 10 distribueras med hjälp av något av ovanstående alternativ.  

Om du behöver läsa in appen separat och distribuera Windows 8.1-företagsportalsappen utan signera den med Symantec-certifikatet, så slutför uppgraderingen genom att följa stegen i avsnittet Distribuera direkt via Intune ovan.

Om du behöver läsa in appen separat och du har signerat och distribuerat företagsportalen för Windows 8.1 med Symantec-kodsigneringscertifikat, så följ stegen i avsnittet nedan.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Hur uppgraderar jag min signerade och separat inlästa företagsportalsapp för Windows Phone 8.1 eller Windows 8.1 till företagsportalsappen för Windows 10?
Våra rekommenderade migreringssökväg är att ta bort den befintliga distributionen av företagsportalsappen för Windows 8.1 Phone eller Windows 8.1 genom att ange distributionsåtgärden till Avinstallera. När detta är gjort kan du distribuera företagsportalappen för Windows 10 distribueras normalt.  

I annat fall måste företagsportalappen för Windows 10 uppdateras på rätt sätt och signeras så att uppgraderingsvägen följs.  

Om Windows 10-företagsportalappen signeras och distribueras på det här sättet måste du upprepa proceduren för varje ny appuppdatering när den är tillgänglig i lagret. Appen uppdateras inte automatiskt när lagret uppdateras.  

Så här registrerar och distribuerar du appen:

1. Ladda ner signeringsskriptet för Microsoft Intune Windows 10-företagsportalappen på [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Det här skriptet kräver att Windows SDK för Windows 10 har installerats på värddatorn. Ladda ner Windows SDK för Windows 10 genom att gå till [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Hämta Windows 10-företagsportalappen från Microsoft Store för företag så som beskrivs ovan.  
3. Kör skriptet med de indataparametrar som beskrivs i skripthuvudet, så att Windows 10-företagsportalsappen signeras (se utdrag nedan). Beroenden behöver inte överföras till skriptet. Detta krävs enbart om appen överförs till Intune-aministratörskonsolen.

|       Parameter       |                                                                    Beskrivning                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             Sökvägen till platsen där appxbundle-källfilen finns.                                              |
| OutputWin10AppxBundle |                                                  Sökvägen för utdata för den signerade appxbundle-filen.                                                  |
|       Win81Appx       |                          Sökvägen till den plats där företagsportalsappen för Windows 8.1 eller Windows Phone 8.1 (. APPX) finns.                           |
|      PfxFilePath      |                                   Sökvägen till filen för Symantec Enterprise Mobile Code Signing Certificate (.PFX).                                    |
|      PfxPassword      |                                     Lösenordet för Symantec Enterprise Mobile Code Signing Certificate.                                      |
|      PublisherId      |      Företagets publicerings-ID. Om det ej finns, används ämnes-fältet i Symantec-certifikatet med mobil kodsignering för företag.       |
|        SdkPath        | Sökvägen till rotkatalogen på Windows SDK för Windows 10. Det här argumentet är valfritt och är som standard ${env:ProgramFiles(x86)}\Windows Kits\10 |

Skriptets utdata är den signerade versioneb av företagsportalsappen för Windows 10. Du kan sedan distribuera den signerade versionen av appen som en LOB-app via Intune, som kommer att uppgraderas till de för tillfället distribuerade versionerna av den nya appen.  
