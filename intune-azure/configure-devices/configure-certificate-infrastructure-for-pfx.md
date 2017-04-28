---
title: Konfigurera och hantera PKCS-certifikat med Intune
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs mer om hur du kan konfigurera din infrastruktur. Skapa och tilldela sedan PKCS-certifikat med Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e189ebd1-6ca1-4365-9d5d-fab313b7e979
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 11bb2cbcf14abe5966e0b203ba3466adc12bd4dd
ms.lasthandoff: 04/24/2017



---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>Konfigurera och hantera PKCS-certifikat med Intune
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

I det här avsnittet beskrivs hur du kan konfigurera din infrastruktur och sedan skapa och tilldela PKCS-certifikatprofiler med Intune.

Om du vill utföra certifikatbaserad autentisering i organisationen måste du ha en utfärdare av företagscertifikat.

Om du vill använda PKCS-certifikatprofiler, utöver utfärdaren av företagscertifikat, behöver du också:

-   En dator som kan kommunicera med certifikatutfärdaren; du kan även använda den dator som fungerar som certifikatutfärdare.

-  Intunes certifikat Connector, som körs på datorn som kan kommunicera med certifikatutfärdaren.

## <a name="important-terms"></a>Viktiga termer


-    **Active Directory-domän**: Alla servrar i det här avsnittet (förutom webbprogramsproxyservern) måste vara anslutna till Active Directory-domänen.

-  **Certifikatutfärdare**: En utfärdare av företagscertifikat som körs på en Enterprise-version av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. Instruktioner om hur du ställer in en certifikatutfärdare finns i [Install the Certification Authority](http://technet.microsoft.com/library/jj125375.aspx).
    Om certifikatutfärdaren kör Windows Server 2008 R2, måste du [installera snabbkorrigeringen från KB2483564](http://support.microsoft.com/kb/2483564/).

-  **En dator som kan kommunicera med certifikatutfärdaren**: Du kan också använda den dator som fungerar som certifikatutfärdare.
-  **Microsoft Intune Certificate Connector**: Från Azure-portalen kan du hämta installationsprogrammet för **Certificate Connector** (**ndesconnectorssetup.exe**). Sen kör du **ndesconnectorssetup.exe** på datorn där du vill installera Certifikat Connector. För PKCS-certifikatprofiler installerar du Certificate Connector på den dator som kommunicerar med certifikatutfärdaren.
-  **Webbprogramsproxyserver** (valfritt): Du kan använda en server som kör Windows Server 2012 R2 eller senare som en webbprogramproxyserver (WAP, Web Application Proxy). Den här konfigurationen:
    -  Tillåter enheter att ta emot certifikat med hjälp av en internetanslutning.
    -  Är en säkerhetsrekommendation när enheter ansluter via internet för att ta emot och förnya certifikat.

 > [!NOTE]           
> -    Servern som är värd för WAP [måste installera en uppdatering](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) som aktiverar stöd för de långa URL:er som används av registreringstjänsten för nätverksenheter (NDES). Uppdateringen finns med i [samlad uppdatering för december 2014](http://support.microsoft.com/kb/3013769), eller individuellt från [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Dessutom måste den server som är värd för WAP ha ett SSL-certifikat som överensstämmer med det namn som publiceras på externa klienter, samt lita på SSL-certifikatet som används på NDES-servern. Certifikaten gör det möjligt för WAP servern att avbryta SSL-anslutningen från klienter och skapa en ny SSL-anslutning till NDES-servern.
    Information om certifikat för WAP finns i sektionen **Planera certifikat** av [Installera och konfigurera webbprogramproxy för publicering av interna program](https://technet.microsoft.com/library/dn383650.aspx). Allmän information om WAP-servrar finns i [Arbeta med webbprogramsproxy](http://technet.microsoft.com/library/dn584113.aspx).|


## <a name="certificates-and-templates"></a>Certifikat och mallar

|Objekt|Information|
|----------|-----------|
|**Certifikatmall**|Du konfigurerar den här mallen på den utfärdande certifikatutfärdaren.|
|**Certifikat från betrodd rotcertifikatutfärdare**|Du exporterar detta som en **.cer**-fil från den utfärdande certifikatutfärdaren eller en enhet som litar på certifikatutfärdaren och tilldelar den till enheter med hjälp av certifikatprofilen för den betrodda certifikatutfärdaren.<br /><br />Du använder ett enstaka certifikat från en betrodd rotcertifikatutfärdare per operativsystemplattform och associerar det med varje betrodd rotcertifikatprofil som du skapar.<br /><br />Du kan använda ytterligare certifikat från betrodda rotcertifikatutfärdare när det behövs. Exempel: du kan göra detta för att ge ett förtroende till en certifikatutfärdare som signerar serverautentiseringscertifikaten för dina WiFi-åtkomstpunkter.|


## <a name="configure-your-infrastructure"></a>Konfigurera infrastrukturen
Innan du kan konfigurera certifikatprofiler måste du slutföra följande steg. Dessa steg kräver kunskaper om Windows Server 2012 R2 och Active Directory Certificate Services (ADCS):

- **Steg 1** – Konfigurera certifikatmallar hos certifikatutfärdaren.
- **Steg 2** – Aktivera, installera och konfigurera Intune Certificate Connector.

## <a name="step-1---configure-certificate-templates-on-the-certification-authority"></a>Steg 1 – Konfigurera certifikatmallar hos certifikatutfärdaren

### <a name="to-configure-the-certification-authority"></a>Så här konfigurerar du certifikatutfärdaren

1.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatmallar och skapar en ny anpassad mall eller kopierar och redigerar en befintlig mall (t.ex. mallen Användare) för användning med PKCS.

    Mallen måste innefatta följande:

    -   Ange ett eget **visningsnamn för mallen** .

    -   På fliken **Ämnesnamn** väljer du **Anges i begäran**. (Säkerhet tvingas av Intune-principmodulen för NDES).

    -   På fliken **Tillägg** kontrollerar du att **beskrivningen av användningsprinciper** omfattar **Klientautentisering**.

        > [!IMPORTANT]
        > För iOS- och macOS-certifikatmallar: Redigera **Nyckelanvändning** på fliken **Tillägg** och kontrollera att **Signaturen är bevis för ursprung** inte har markerats.

2.  Granska **Giltighetsperioden** på mallens flik **Allmänt** . Som standard använder Intune värdet som konfigurerats i mallen. Du kan dock välja att konfigurera certifikatutfärdaren att tillåta att den som begär anger ett annat värde, som du sedan kan ställa in i Intune-administratörskonsolen. Om du alltid vill använda värdet i mallen kan du hoppa över resten av det här steget.

    > [!IMPORTANT]
    > iOS och macOS använder alltid värdet i mallen, oavsett andra konfigurationer som du gör.

    Om du vill konfigurera certifikatutfärdaren att tillåta att beställaren anger giltighetsperioden, kör du följande kommandon på certifikatutfärdaren:

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatutfärdaren för att publicera certifikatmallen.

    a.  Välj noden **Certifikatmallar**, klicka på **Åtgärd**-&gt; **Ny** &gt; **Certifikatmall som ska utfärdas** och välj sedan den mall som du skapade i steg 2.

    b.  Kontrollera att mallen publicerats genom att se om den finns i mappen **Certifikatmallar** .

4.  På certifikatutfärdardatorn ser du till att den dator som har Intunes certifikatanslutningsapp har registreringsrättigheter, så att den kommer åt den mall som användes för att skapa PKCS-certifikatprofilen. Ställ in behörighet på **säkerhetsfliken** i datoregenskaper för Certifikatutfärdar-datorn.

## <a name="step-2---enable-install-and-configure-the-intune-certificate-connector"></a>Steg 2 – Aktivera, installera och konfigurera Intunes certifikatanslutningsapp
I det här steget kommer du att:

- Aktivera stöd för Certificate Connector
- Hämta, installera och konfigurera certifikatanslutningsappen.

### <a name="to-enable-support-for-the-certificate-connector"></a>Så här aktiverar du stöd för certifikatanslutningsappen

1.  Logga in på Azure-portalen.
2.  Välj **Fler tjänster** > **Övrigt** > **Intune**.
3.  Välj **Konfigurera enheter** på **Intune**-bladet.
2.  Välj **Installation** > **Certifikatutfärdare** på bladet **Enhetskonfiguration**.
2.  Under **Steg 1** väljer du **Aktivera**.

### <a name="to-download-install-and-configure-the-certificate-connector"></a>Så här hämtar, installerar och konfigurerar du certifikatanslutningsappen

1.  Välj **Installation** > **Certifikatutfärdare** på bladet **Enhetskonfiguration**.
2.  Välj **Ladda ned certifikatanslutningsappen**.
2.  När nedladdningen är klar så kör du det nedladdade installationsprogrammet (**ndesconnectorssetup.exe**).
  Kör installationsprogrammet på den dator som kan ansluta med certifikatutfärdaren. Välj PKCS (PFX)-distributionsalternativet och välj sedan **Installera**. När installationen har slutförts fortsätter du genom att skapa en certifikatprofil enligt beskrivningen i [Konfigurera certifikatprofiler](how-to-configure-certificates.md).

3.  När du tillfrågas om klientcertifikatet för certifikatanslutningsappen väljer du **Välj** och väljer det certifikat för **klientautentisering** som du installerade.

    När du har valt certifikatet för klientautentisering tas du tillbaka till ytan **Klientcertifikat för Microsoft Intune Certifikat Connector** . Även om certifikatet du valt inte visas väljer du **Nästa** för att visa egenskaperna för certifikatet. Välj **Nästa** och sedan **Installera**.

4.  När guiden slutförts klickar du på **Starta användargränssnittet för Certifikat Connectorn**innan du stänger guiden.

    > [!TIP]
    > Om du stängt guiden innan du startade användargränssnittet kan du öppna det genom att skriva följande kommando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  I användargränssnittet för **certifikat connectorn** :

    a. Välj **Logga in** och ange dina autentiseringsuppgifter som tjänstadministratör i Intune eller för en klientadministratör med behörighet för global administration.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    b. Välj fliken **Avancerat** och ange autentiseringsuppgifter för ett konto som har behörigheten **Utfärda och hantera certifikat** på den utfärdande certifikatutfärdaren.

    c. Välj **Använd**.

    Nu kan du stänga användargränssnittet för Certifikat Connectorn.

6.  Öppna en kommandotolk och skriv **services.msc**. Tryck på **Retur**, högerklicka på **Intune-anslutningstjänsten** och välj **Starta om**.

Kontrollera att tjänsten körs genom att öppna en webbläsare och ange följande URL, vilket borde returnera ett **403** -fel:

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**


### <a name="how-to-create-a-pkcs-certificate-profile"></a>Så här skapar du en PKCS-certifikatprofil

I Azure-portalen väljer du arbetsbelastningen **Konfigurera enheter**.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för den PKCS-certifikatprofilen.
5. Från listrutan **Plattform** väljer du enhetsplattformen för detta PKCS-certifikat från:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **Windows 10 och senare**
6. Från listrutan **Profil** väljer du **PKCS-certifikat**.
7. På bladet **PKCS-certifikat**, konfigurerar du följande inställningar:
    - **Tröskelvärde för förnyelse (%)** – Ange i procent hur mycket av certifikatets giltighetstid som får återstå innan förfrågningar om förnyat certifikat görs.
    - **Certifikatets giltighetsperiod** – Om du har kört kommandot **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** på certifikatutfärdaren, vilket gör att en anpassad giltighetsperiod kan användas, kan du ange hur lång tid som återstår innan certifikatet går ut.<br>Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i den angivna certifikatmallen. Om giltighetsperioden i certifikatmallen är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren.
    - **Nyckellagringsprovider (KSP)** (Windows 10) – Ange var nyckeln till certifikatet ska lagras. Välj något av följande värden:
        - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module) om TPM finns, annars till programvaruprovider för nyckellagring**
        - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module), rapportera annars fel**
        - **Registrera på Passport, rapportera annars fel (Windows 10 och senare)**
        - **Registrera till programvaruprovider för nyckellagring**
    - **Certifikatutfärdare** – En utfärdare av företagscertifikat som körs på en Enterprise Edition av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. Instruktioner om hur du ställer in en certifikatutfärdare finns i [Install the Certification Authority](http://technet.microsoft.com/library/jj125375.aspx). Om certifikatutfärdaren kör Windows Server 2008 R2, måste du [installera snabbkorrigeringen från KB2483564](http://support.microsoft.com/kb/2483564/).
    - **Namn på certifikatutfärdare** – Ange namnet på certifikatutfärdaren.
    - **Certifikatmallens namn** – Ange namnet på en certifikatmall som registreringstjänsten för nätverksenheter har konfigurerats att använda och som har lagts till i en certifikatutfärdare.
    Se till att namnet exakt matchar namnet på certifikatmallarna i listan i registret på den server som kör registreringstjänsten för nätverksenheter. Se till att du anger namnet på certifikatmallen och inte visningsnamnet på certifikatmallen. 
    Bläddra till följande nyckel om du vill söka efter namn på certifikatmallar: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. Certifikatmallarna visas i listan som värden för **EncryptionTemplate**, **GeneralPurposeTemplate**och **SignatureTemplate**. Värdet för alla tre certifikatmallar är som standard IPSECIntermediateOffline vilket mappar till mallvisningsnamnet **IPSec (Offline request)**. 
    - **Format för namn på certifikatmottagare** – Välj i listan hur mottagarnamnet i certifikatförfrågan ska skapas automatiskt i Intune. Om certifikatet avser en användare kan du ange användarens e-postadress i mottagarnamnet. Välj mellan:
        - **Inte konfigurerat**
        - **Allmänt namn**
        - **Eget namn, inklusive e-post**
        - **Eget namn som e-post**
    - **Alternativt namn för certifikatmottagare** – Ange hur värden för det alternativa certifikatmottagarnamnet i certifikatförfrågan ska skapas automatiskt i Intune. Om du exempelvis valde en användarcertifikattyp kan du ange användarens huvudnamn (UPN) i det alternativa certifikatmottagarnamnet. Om klientcertifikatet ska användas för att autentisera mot en nätverksprincipserver måste du ange användarens huvudnamn som alternativt mottagarnamn.
    - **Utökad nyckelanvändning** (Android) – Välj **Lägg till** om du vill lägga till värden för certifikatets avsedda syfte. I de flesta fall kräver certifikatet **Klientautentisering** så att användaren eller enheten kan autentisera till en server. Du kan dock lägga till alla andra nyckelanvändningar efter behov. 
    - **Rotcertifikat** (Android) – Välj en certifikatprofil från en rotcertifikatutfärdare som du tidigare har konfigurerat och tilldelat till användaren eller enheten. Detta CA-certifikat måste vara rotcertifikatet för den certifikatutfärdare som kommer att utfärda det certifikat som du konfigurerar i den här certifikatprofilen. Det här är den betrodda certifikatprofil som du skapade tidigare.
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.

## <a name="how-to-assign-the-certificate-profile"></a>Så här tilldelar du certifikatprofilen

Tänk på följande innan du tilldelar certifikatprofiler till grupper:

- När du tilldelar certifikatprofiler till grupper installeras certifikatfilen från certifikatprofilen för betrodd certifikatutfärdare på enheten. Enheten använder PKCS-certifikatprofilen för att skapa en certifikatbegäran från enheten.
- Certifikatprofiler installeras endast på enheter som kör den plattform som du använder när du skapade profilen.
- Du kan tilldela certifikatprofiler till användarsamlingar eller enhetssamlingar.
- Om du vill publicera certifikat till enheter kort efter att enheten registrerats, tilldelar du certifikatprofilen till en användargrupp i stället för en enhetsgrupp. Om du tilldelar till en enhetsgrupp krävs en fullständig enhetsregistrering innan enheten kan ta emot principer.
- Även om du tilldelar varje profil separat, måste du också tilldela den betrodda rotcertifikatutfärdaren och PKCS-profilen. Annars misslyckas PKCS-certifikatprincipen.

Du hittar allmän information om hur du tilldelar profiler i [Så här tilldelar du enhetsprofiler](how-to-assign-device-profiles.md).

