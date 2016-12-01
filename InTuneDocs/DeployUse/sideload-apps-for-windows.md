---
title: "Separat inläsning av appar för Windows och Windows Phone | Microsoft Intune"
description: "Lär dig hur du signerar branschspecifika appar, så att du kan använda Intune för att distribuera dem."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 11/16/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
translationtype: Human Translation
ms.sourcegitcommit: 6fcdacc4746e780dcd9a988a46a4153929516449
ms.openlocfilehash: 5debf013e4ff6c9f72eb59e31f256e00fd6f9540


---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Signera verksamhetsspecifika appar så att de kan distribueras till Windows-enheter med Intune

Som Intune-administratör kan du distribuera verksamhetsspecifika (LOB) appar till Windows- och Windows 10 Mobile-enheter, inklusive företagsportalappen. För att distribuera .appx- eller .xap-appar till Windows 10- och Windows 10 Mobile-enheter eller för att distribuera LOB-app till Windows 8.1 eller Windows Phone 8.1-enheter, måste du få ett **Symantec-företagscertifikat för kodsignering**. Endast Symantec-certifikatet är betrott för dessa appar för respektive Windows-enhet. Du kan använda en egen certifikatutfärdare för Windows 10-appar och "universella" appar. Detta certifikat krävs för att:

-   Signera företagsportalappen för distribution till datorer med Windows, Windows 10 Mobile-enheter och Windows Phone-enheter

-   Signera verksamhetsspecifika appar så att Intune kan distribuera dem till Windows-enheter

Stegen nedan hjälper dig att få nödvändiga certifikat och signera appen. Du behöver ett Windows Phone Dev Center-konto och du behöver köpa ett Symantec-certifikat.


1. **Gå med i Windows Phone Dev Center**<br>
   Gå med i [Windows Phone Dev Center](http://go.microsoft.com/fwlink/?LinkId=268442) genom att använda företagskontots information när du loggar in för att köpa ditt företagskonto. Den här begäran måste godkännas av en företagsrepresentant innan du får ett signeringscertifikat med kod.

2. **Få ett företagskonto från Symantec**<br>
  Köpa ett certifikat från [Symantec-webbplatsen](http://go.microsoft.com/fwlink/?LinkId=268441) med hjälp av ditt Symantec-ID. När du har köpt certifikatet får den företagsgodkännare som du angav i ditt Windows Phone Dev Center-konto ett e-postmeddelande där personen ombeds godkänna certifikatförfrågan. Du hittar mer information om kraven för Symantec-certifikat under [Varför Windows Phone kräver ett Symantec-certifikat](https://technet.microsoft.com/en-us/library/dn764959.aspx#BKMK_Symantec) Vanliga frågor och svar om registrering av Windows-enhet.

3.  **Importera certifikat**<br>
    När din begäran har godkänts, kommer du att få ett e-postmeddelande som innehåller instruktioner om hur du importerar certifikat. Följ anvisningarna i e-postmeddelandet för att importera certifikaten.

4.  **Verifiera importerade certifikat**<br>
    Du kan kontrollera att certifikaten har importerats genom att gå till snapin-modulen **Certifikat**, högerklicka på **Certifikat** och välja **Sök efter certifikat**. I fältet **Innehåller** skriver du ”Symantec” och klickar på **Sök nu**. De certifikat som du har importerat ska visas i resultaten.

    ![Hitta Symantec-certifikatet](../media/wit.gif)

5. **Exportera ett signeringscertifikat**<br>
    När du har kontrollerat att certifikaten finns kan du exportera .pfx-filen så att du kan signera företagsportalen. Välj Symantec-certifikatet med kodsigneringen **avsett syfte**. Högerklicka på det kodsignerade certifikatet och välj **Exportera**.

    ![Exportera signeringscertifikatet](../media/wit-walk-cert2.gif)

    I **Guiden Exportera certifikat**väljer du **Ja, exportera den privata nyckeln** och klickar sedan på **Nästa**. Välj **Personal Information Exchange –PKCS #12 (.PFX)** och markera **Inkludera om möjligt alla certifikat i certifieringssökvägen**. Slutför guiden. Mer information finns i [Exportera certifikat med privat nyckel](http://go.microsoft.com/fwlink/?LinkID=203031).

6.  **Överför appen till Intune**<br>
    Överför den signerade appfilen och ditt kodsigneringscertifikat för att göra appen tillgänglig för dina slutanvändare.

    1.  Gå till [Intune-administrationskonsolen](http://manage.microsoft.com) och klicka på **Administration** &gt; **Windows Phone**.

    2.  Klicka på **Överför signerad appfil** och logga in med ditt administratörs-ID för Intune.

    3.  Lägg till certifikatfilen (.pfx) som du exporterade till **Kodsigneringscertifikat** och skapa ett lösenord för certifikatet.

    4.  Slutför guiden.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>Exempel: Hämta, signera och distribuera företagsportalappen för Windows-enheter

Du kan distribuera företagsportalappen till Windows-enheter, inklusive Windows Phone- och Windows 10 Mobile-enheter med Intune istället för att installera från Windows Store. Du måste ladda ned företagsportalappen och signera den med ditt certifikat.  Detta är bara nödvändigt om användarna inte kommer att använda företagsbutiken och du vill distribuera företagsportalen till Windows Phone 8.1-enheter.


1.  **Ladda ned företagsportalen**

    För att distribuera företagsportalappen med Intune, kan du hämta [Microsoft Intune-företagsportalappen för Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) från Download Center och kör den självuppackande filen(.exe). Denna fil innehåller två filer:

    -   CompanyPortal.appx – Installationsappen för företagsportalen för Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1 – Ett Powershell-skript som du kan använda för att signera företagsportalappfilen så att den kan användas för Windows Phone 8.1-enheter

    Alternativt kan du hämta Windows Phone 8.1-företagsportalen (offline-licensierat paket) från [Windows Store för företag](http://businessstore.microsoft.com/). Företagsportalappen måste anskaffas med en offline-licens och lämpligt paket hämtas för användning offline. Listor med plattformar för Windows 8- och Windows Phone 8 i urvalet avser deras 8.1-motsvarigheter.

2.  **Hämta Windows Phone SDK** Hämta Windows Phone SDK 8.0 (http://go.microsoft.com/fwlink/?LinkId=615570) och installera SDK:n på datorn. Detta SDK behövs för att generera en token för programregistrering.

3.  **Generera en AETX-fil** Generera en tokenfil (.aetx) för programregistrering från Symantec PFX-filen med AETGenerator.exe, en del av Windows Phone SDK 8.0. Instruktioner om hur du skapar en AETX-fil hittar du på [Hur man genererar en tokenfil för programregistrering för Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx)

4.  **Hämta Windows SDK för Windows 8.1**Hämta och installera [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=613525) (http://go.microsoft.com/fwlink/?LinkId=613525). Observera att det Powershell-skript som medföljer företagsportalappen använder standardinstallationsplatsen, `${env:ProgramFiles(x86)}\Windows Kits\8.1`. Om du installerar någon annanstans måste du inkludera platsen i en cmdlet-parameter.

5.  **Kodsignera appen med Powershell** Öppna **Windows Powershell** som administratör på värddatorn där Windows SDK och Symantec-certifikatet med mobil kodsignering för företag har installerats, navigera till Sign-WinPhoneCompanyPortal.ps1-filen och kör skriptet.

    **Exempel 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    Detta exempel signerar CompanyPortal.appx i C:\temp\ och skapar CompanyPortalEnterpriseSigned.appx. Det skulle använda PFX-lösenordet 1234 och läsa publicerings-ID:t från PFX-filen. Det läser även företags-ID:t från cert.aetx-filen.

    **Exempel 2**

    ```
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

6.  Distribuera Windows Phone 8.1-företagsportalappen (SSP.appx). Vägledning finns i [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Så här förnyar du Symantec-företagscertifikatet för kodsignering

Symantec-certifikatet som används för att distribuera Windows- och Windows Phone-mobilappar måste förnyas regelbundet.

1.  Ett e-postmeddelande om förnyelsen skickas från Symantec ungefär 14 dagar innan certifikatet upphör att gälla. E-postmeddelandet innehåller anvisningar från Symantec om att du bör förnya ditt företagscertifikat.

    Mer information om Symantec-certifikat finns på [www.symantec.com](http://www.symantec.com). Du kan också ringa 1-877-438-8776 eller 1-650-426-3400.

2.  Gå till webbplatsen (exempel: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) och logga in med Symantec Publisher ID och e-postadressen som är associerade med certifikatet. Kom ihåg att använda samma dator för att starta förnyelsen som du använde för att hämta certifikatet.

3.  När förnyelsen är godkänd och betald kan du hämta certifikatet.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Hur du installerar det uppdaterade certifikatet för verksamhetsspecifika (LOB) appar

1.  Signera den senaste versionen av din verksamhetsspecifika app.

2.  Öppna din [Intune-administratörskonsol](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com) och välj **Admin** &gt; **Hantering av mobila enheter** &gt; **Windows Phone** och klicka på **Överför signerad app**.

3.  Överför den nyligen signerade företagsportalen. Du behöver den nyligen signerade SSP.xap och den nya PFX-filen som du har fått från Symantec eller den programregistreringstoken som har skapats med den nya PFX-filen.

4.  När uppladdningen är klar tar du bort den gamla företagsportalversionen i arbetsytan **Programvara**  .

5.  Signera alla nya och uppdaterade branschspecifika företagsappar med det nya certifikatet. Befintliga program behöver inte vara signeras på nytt eller omdistribueras.



<!--HONumber=Nov16_HO3-->


