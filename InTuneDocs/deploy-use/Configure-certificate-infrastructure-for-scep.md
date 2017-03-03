---
title: "Konfigurera certifikatinfrastrukturen för SCEP | Microsoft Docs"
description: "Infrastruktur för att skapa och distribuera SCEP-certifikatprofiler."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4ae137ae-34e5-4a45-950c-983de831270f
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 4140c310bb14faf1731e3c316e1dafae5dc0f97a
ms.lasthandoff: 12/10/2016

---
# <a name="configure-certificate-infrastructure-for-scep"></a>Konfigurera certifikatinfrastruktur för SCEP

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet beskriver vilken infrastruktur du behöver för att kunna skapa och distribuera SCEP-certifikatprofiler.

### <a name="on-premises-infrastructure"></a>Lokal infrastruktur

-    **Active Directory-domän**: Alla servrar i det här avsnittet (förutom webbprogramsproxyservern) måste vara anslutna till Active Directory-domänen.

-  **Certifikatutfärdare** (CA): En utfärdare av företagscertifikat som körs på en Enterprise-version av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. Instruktioner om hur du ställer in en certifikatutfärdare finns i [Install the Certification Authority](http://technet.microsoft.com/library/jj125375.aspx).
    Om certifikatutfärdaren kör Windows Server 2008 R2, måste du [installera snabbkorrigeringen från KB2483564](http://support.microsoft.com/kb/2483564/).
I
-  **NDES-server**: På en server som kör Windows Server 2012 R2 eller senare måste du konfigurera registreringstjänsten för nätverksenheter (NDES, Network Device Enrollment Service). Intune stöder inte användning av registreringstjänsten för nätverksenheter när den körs på en server som också kör företagscertifikatutfärdaren. Se [Vägledning för registreringstjänsten för nätverksenheter](http://technet.microsoft.com/library/hh831498.aspx) för anvisningar om hur du konfigurerar Windows Server 2012 R2 som värd för registreringstjänsten för nätverksenheter. NDES-servern måste vara ansluten till den domän där certifikatutfärdaren finns och får inte finnas på samma server som certifikatutfärdaren. Mer information om hur du distribuerar NDES-servern i en separat skog, ett isolerat nätverk eller en intern domän återfinns i [Använda en principmodul med registreringstjänsten för nätverksenheter](https://technet.microsoft.com/en-us/library/dn473016.aspx).

-  **Microsoft Intune-certifikatanslutningsapp**: Använd Intune-administratörskonsolen för att hämta installationsprogrammet för **Certifikatanslutningsapp** (**ndesconnectorssetup.exe**). Sen kör du **ndesconnectorssetup.exe** på datorn där du vill installera Certifikat Connector.
-  **Webbprogramsproxyserver** (valfritt): Du kan använda en server som kör Windows Server 2012 R2 eller senare som en webbprogramsproxyserver (WAP, Web Application Proxy). Den här konfigurationen:
    -  Tillåter enheter att ta emot certifikat med hjälp av en internetanslutning.
    -  Är en säkerhetsrekommendation när enheter ansluter via internet för att ta emot och förnya certifikat.

 > [!NOTE]           
> -    Servern som är värd för WAP [måste installera en uppdatering](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) som aktiverar stöd för de långa URL:er som används av registreringstjänsten för nätverksenheter. Uppdateringen finns med i [samlad uppdatering för december 2014](http://support.microsoft.com/kb/3013769), eller individuellt från [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Dessutom måste den server som är värd för WAP ha ett SSL-certifikat som överensstämmer med det namn som publiceras på externa klienter, samt lita på SSL-certifikatet som används på NDES-servern. Certifikaten gör det möjligt för WAP servern att avbryta SSL-anslutningen från klienter och skapa en ny SSL-anslutning till NDES-servern.
    Information om certifikat för WAP finns i sektionen **Planera certifikat** av [Installera och konfigurera webbprogramproxy för publicering av interna program](https://technet.microsoft.com/library/dn383650.aspx). Allmän information om WAP-servrar finns i [Arbeta med webbprogramsproxy](http://technet.microsoft.com/library/dn584113.aspx).|

### <a name="network-requirements"></a>Nätverkskrav

Tillåt port 443 från Internet till perimeternätverk från alla värdar/IP-adresser på Internet till NDES-servern.

Tillåt alla portar och protokoll som behövs för åtkomst till domänen på den domänanslutna NDES-servern från perimeternätverket till det betrodda nätverket. NDES-servern måste ha åtkomst till certifikatservrar, DNS-servrar, Configuration Manager-servrar och domänkontrollanter.

Vi rekommenderar att du publicerar NDES-servern via en proxyserver, till exempel [Azure AD-programproxy](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-publish/), [Web Access-proxy](https://technet.microsoft.com/en-us/library/dn584107.aspx) eller en proxy från en annan leverantör.


### <a name="a-namebkmkcertsandtemplatesacertificates-and-templates"></a><a name="BKMK_CertsAndTemplates"></a>Certifikat och mallar

|Objekt|Information|
|----------|-----------|
|**Certifikatmall**|Du konfigurerar den här mallen på den utfärdande certifikatutfärdaren.|
|**Certifikat för klientautentisering**|Begärs från den utfärdande certifikatutfärdaren eller från offentlig certifikatutfärdare, du installerar certifikatet på NDES-servern.|
|**Certifikat för serverautentisering**|Begärs från den utfärdande certifikatutfärdaren eller från offentlig certifikatutfärdare, du installerar och binder SSL-certifikatet i IIS på NDES-servern.|
|**Certifikat från betrodd rotcertifikatutfärdare**|Du exporterar detta som en **.cer**-fil från rotcertifikatutfärdaren eller en enhet som litar på rotcertifikatutfärdaren och distribuerar den till enheterna med hjälp av certifikatprofilen för den betrodda certifikatutfärdaren.<br /><br />Du använder ett enstaka certifikat från en betrodd rotcertifikatutfärdare per operativsystemplattform och associerar det med varje betrodd rotcertifikatprofil som du skapar.<br /><br />Du kan använda ytterligare certifikat från betrodda rotcertifikatutfärdare när det behövs. Exempel: du kan göra detta för att ge ett förtroende till en certifikatutfärdare som signerar serverautentiseringscertifikaten för dina WiFi-åtkomstpunkter.|

### <a name="a-namebkmkaccountsaaccounts"></a><a name="BKMK_Accounts"></a>Konton

|Namn|Information|
|--------|-----------|
|**NDES-tjänstkonto**|Du anger ett domänanvändarkonto som används som NDES-tjänstkontot|

## <a name="a-namebkmkconfigureinfrastructureaconfigure-your-infrastructure"></a><a name="BKMK_ConfigureInfrastructure"></a>Konfigurera infrastrukturen
Innan du kan konfigurera certifikatprofiler måste du utföra följande åtgärder, som kräver kunskaper om Windows Server 2012 R2 och Active Directory-certifikattjänster (ADCS):

**Uppgift 1**: Skapa ett NDES-tjänstkonto

**Uppgift 2**: Konfigurera certifikatmallar på certifikatutfärdaren

**Uppgift 3**: Konfigurera förhandskrav på NDES-servern

**Uppgift 4**: Konfigurera NDES för användning med Intune

**Uppgift 5**: Aktivera, installera och konfigurera Intune Certificate Connector

### <a name="task-1---create-an-ndes-service-account"></a>Uppgift 1 – Skapa ett NDES-tjänstkonto

Skapa domänanvändarkonto som används som NDES-tjänstkontot Du anger det här kontot när du konfigurerar mallar på den utfärdande certifikatutfärdaren innan du installerar och konfigurerar NDES. Kontrollera att användaren har behörigheten standard **Inloggning lokalt**, **Inloggning som tjänst** och **Inloggning som batchjobb**. En del organisationer har härdningsprinciper som inaktiverar dessa rättigheter.




### <a name="task-2---configure-certificate-templates-on-the-certification-authority"></a>Uppgift 2 – Konfigurera certifikatmallar för certifikatutfärdaren
I det här steget kommer du att:

-   Konfigurera en certifikatmall för NDES

-   Publicera certifikatmallen för NDES

##### <a name="to-configure-the-certification-authority"></a>Så här konfigurerar du certifikatutfärdaren

1.  Logga in som företagsadministratör.

2.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatmallar för att skapa en ny anpassad mall eller kopiera en befintlig mall och sedan redigera en befintlig mall (t.ex. mallen Användare) för användning med NDES.

    Mallen måste ha följande konfigurationer:

    -   Ange ett eget **visningsnamn för mallen** .

    -   På fliken **Ämnesnamn** väljer du **Anges i begäran**. (Säkerhet tvingas av Intune-principmodulen för NDES).

    -   På fliken **Tillägg** kontrollerar du att **beskrivningen av användningsprinciper** omfattar **Klientautentisering**.

        > [!IMPORTANT]
        > För iOS- och Mac OS X-certifikatmallar: På fliken **Tillägg** redigerar du **Nyckelanvändning** och ser till att **Signaturen är bevis för ursprung** inte är markerat.

    -   På fliken **Säkerhet** lägger du till NDES-tjänstekontot och ger det **Registreringsrättigheter** för mallen. Intune-administratörer som ska skapa SCEP-profiler behöver **läsrättigheter** så att de kan bläddra till mallen när de skapar SCEP-profiler.

    > [!NOTE]
    > Om du vill återkalla certifikat behöver NDES-tjänstkontot rättigheter för att *Utfärda och hantera certifikat* för varje certifikatmall som används av en certifikatprofil.

3.  Granska **Giltighetsperioden** på mallens flik **Allmänt** . Som standard använder Intune värdet som konfigurerats i mallen. Du kan dock välja att konfigurera certifikatutfärdaren att tillåta att den som begär anger ett annat värde, som du sedan kan ställa in i Intune-administratörskonsolen. Om du alltid vill använda värdet i mallen kan du hoppa över resten av det här steget.

    > [!IMPORTANT]
    > iOS- och Mac OS X-plattformen använder alltid värdet i mallen, oavsett andra konfigurationer som du gör.

Här följer skärmdumpar av en exempelkonfiguration av mallen.

![Mall, fliken för hantering av begäran](..\media\scep_ndes_request_handling.png)

![Mall, fliken för ämnesrad](..\media\scep_ndes_subject_name.jpg)

![Mall, fliken för säkerhet](..\media\scep_ndes_security.jpg)

![Mall, fliken för tillägg](..\media\scep_ndes_extensions.jpg)

![Mall, fliken för utfärdandekrav](..\media\scep_ndes_issuance_reqs.jpg)

>   [!IMPORTANT]
    > För Användningsprinciper (på den fjärde skärmbilden) lägger du endast till de användningsprinciper som krävs. Bekräfta dina val med säkerhetsadministratörerna.



Om du vill konfigurera certifikatutfärdaren att tillåta att den som begär anger giltighetsperioden, kör du följande kommandon på certifikatutfärdaren:

   1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   2.  **net stop certsvc**

   3.  **net start certsvc**

4.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatutfärdaren för att publicera certifikatmallen.

    1.  Välj noden **Certifikatmallar**, klicka på **Åtgärd** -&gt;**Ny** &gt; **Certifikatmall som ska utfärdas** och välj sedan den mall som du skapade i steg 2.

    2.  Kontrollera att mallen publicerats genom att se om den finns i mappen **Certifikatmallar** .


### <a name="task-3---configure-prerequisites-on-the-ndes-server"></a>Uppgift 3 – Konfigurera förhandskrav på NDES-servern
I det här steget kommer du att:

-   Lägga till NDES till en Windows Server och konfigurera IIS för att stöda NDES

-   Lägga till NDES-tjänstkontot i gruppen IIS_IUSR

-   Ange SPN för NDES-tjänstkontot




   1.  DU måste logga in som en **Företagsadministratör**på servern som står värd för NDES och sedan använda [guiden Lägg till roller och funktioner](https://technet.microsoft.com/library/hh831809.aspx) för att installera NDES:

    1.  I guiden väljer du **Active Directory-certifikattjänster** för att få tillgång till AD CS-rolltjänsterna. Välj **Registreringstjänsten för nätverksenheten**, avmarkera **Certifikatutfärdare**och slutför guiden.

        > [!TIP]
        > Klicka inte på **Stäng** på sidan **Installationsförlopp**i guiden. Klicka istället på länken **Konfigurera Active Directory-certifikattjänster på målservern**. Då öppnas guiden **AD CS-konfiguration** som du använder för nästa åtgärd. När AD CS-konfiguration öppnats stänger du guiden Lägg till roller och funktioner.

    2.  När NDES läggs till på servern installerar guiden även IIS. Kontrollera att IIS har följande konfigurationer:

        -   **Webbserver** &gt; **Säkerhet** &gt; **Begärandefiltrering**

        -   **Webbserver** &gt; **Programutveckling** &gt; **ASP.NET 3.5**. Om du installerar ASP.NET 3.5 installeras även .NET Framework 3.5. När du installerar .NET Framework 3.5, installera både kärnfunktionen **.NET Framework 3.5** och **HTTP-aktivering**.

        -   **Webbserver** &gt; **Programutveckling** &gt; **ASP.NET 4.5**. Om du installerar ASP.NET 4,5 installeras även .NET Framework 4,5. När du installerar .NET Framework 4.5 installerar du kärnfunktionen **.NET Framework 4.5**, **ASP.NET 4.5** och **WCF Services** &gt; **HTTP-aktivering**.

        -   **Hanteringsverktyg** &gt; **IIS 6-hanteringskompatibilitet** &gt; **IIS 6-metabaskompatibilitet**

        -   **Hanteringsverktyg** &gt; **IIS 6-hanteringskompatibilitet** &gt; **IIS 6 WMI-kompatibilitet**

  2.  Lägg till NDES-tjänstkontot som en medlem i gruppen **IIS_IUSR** på servern.

   3.  Kör följande kommando i en upphöjd kommandotolk och ange SPN för NDES-tjänstkontot:

`**setspn -s http/&lt;DNS name of NDES Server&gt; &lt;Domain name&gt;\&lt;NDES Service account name&gt;**`

   Exempel: om NDES-serverns namn är **Server01**, domänen är **Contoso.com**och tjänstkontot är **NDESService**, använd:

`**setspn –s http/Server01.contoso.com contoso\NDESService**`

### <a name="task-4---configure-ndes-for-use-with-intune"></a>Uppgift 4 – Konfigurera NDES för användning med Intune
I det här steget kommer du att:

-   Konfigurera NDES för användning med den utfärdande certifikatutfärdaren

-   Binda serverautentiseringscertifikatet (SSL) i IIS

-   Konfigurera begäransfiltrering i IIS

##### <a name="to-configure-ndes-for-use-with-intune"></a>Konfigurera NDES för användning med Intune

1.  Öppna guiden AD CS-konfiguration och gör följande konfigurationer på NDES-servern.

    > [!TIP]
    > Om du klickade på länken i föregående åtgärd är guiden redan öppen. Annars öppnar du Serverhanteraren för att komma åt konfigurationen efter distribution för Active Directory-certifikattjänster.

    -   På sidan **Rolltjänster** väljer du **registreringstjänsten för nätverksenheter**.

    -   På sidan **Tjänstkonto för NDES** anger du NDES-tjänstkontot.

    -   På sidan **Certifikatutfärdare för NDES** klickar du på **Välj**och väljer sedan den utfärdande certifikatutfärdaren där du konfigurerade certifikatmallen.

    -   På sidan **Kryptografi för NDES** ställer du in nyckellängden enligt företagets krav.

    Klicka på **Konfigurera** på sidan **Bekräftelse** för att slutföra guiden.

2.  När guiden är slutförd redigerar du följande registernyckel på NDES-servern:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\**

    När du ska redigera den här nyckeln identifierar du certifikatmallarnas **Syfte**, som finns under fliken **Hantering av begäranden** och redigerar sedan motsvarande post i registret genom att ersätta den befintliga informationen med namnet på den certifikatmall (inte mallens visningsnamn) som du angav i Uppgift 1. I följande tabell visas certifikatmallens syfte för värdena i registret:

    |Certifikatmallens syfte (på fliken Hantering av begäranden)|Registervärde som redigeras|Värde som visas i Intune-administratörskonsolen för SCEP-profilen|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Signatur|SignatureTemplate|Digital signatur|
    |Kryptering|EncryptionTemplate|Nyckelchiffrering|
    |Signatur och kryptering|GeneralPurposeTemplate|Nyckelchiffrering<br /><br />Digital signatur|
    Exempel: Om syftet för certifikatmallen är **Kryptering**, ersätter du värdet **EncryptionTemplate** värdet med namnet på certifikatmallen.

3. NDES-servern kommer att få mycket långa URL: er (frågor), som kräver att du lägger till två registerposter:

    |Plats|Värde|Typ|Data|
    |-------|-----|----|----|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxFieldLength|DWORD|65534 (decimal)|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxRequestBytes|DWORD|65534 (decimal)|


4. I IIS-hanteraren väljer du **Standardwebbplats** -> **Förfrågningsfiltrering** -> **Redigera inställningen** och ändrar **Högsta URL-längd** och **Maximal frågesträng** till *65534*, som exemplet visar.

    ![Maxlängd för URL och fråga i IIS](..\media\SCEP_IIS_max_URL.png)

5.  Starta om servern. Det räcker inte att köra **iisreset** på servern för att genomföra de här ändringarna.
6. Bläddra till http://*FQDN*/certsrv/mscep/mscep.dll. Du bör se en NDES-sida som ser ur ungefär så här:

    ![Testa NDES](..\media\SCEP_NDES_URL.png)

    Om meddelandet **503 Tjänsten ej tillgänglig** visas kontrollerar du händelsespåraren. Det är troligt att programpoolen har stoppats på grund av en saknad behörighet för NDES-användaren. Dessa rättigheter beskrivs i uppgift 1.

##### <a name="to-install-and-bind-certificates-on-the-ndes-server"></a>Så här installerar och binder du certifikat på NDES-servern

1.  På NDES-servern: begär och installera ett certifikat för **serverautentisering** från den interna certifikatutfärdaren eller en offentlig certifikatutfärdare. Bind sedan SSL-certifikatet i IIS.

    > [!TIP]
    > När du bundit SSL-certifikatet i IIS installerar du ett certifikat för klientautentisering. Det här certifikatet kan utfärdas av vilken certifikatutfärdare som helst som är betrodd av NDES-servern. Även om det inte rekommenderas, kan du använda samma certifikat för både server- och klientautentisering så länge som certifikatet har båda förbättrade nyckelanvändningar (EKU). Granska följande steg för information om dessa certifikat för autentisering.

    1.  När du har fått certifikat för serverautentisering, öppnar du **IIS-hanteraren**, väljer **Standardwebbplats** i rutan **Anslutningar** och klickar sedan på **Bindningar** i rutan **Åtgärder** .

    2.  Klicka på **Lägg till**, ställ in **Typ** till **https**och kontrollera att porten är **443**. (Endast port 443 stöds för fristående Intune.

    3.  För **SSL-certifikat**anger du certifikatet för serverautentiserning.

        > [!NOTE]
        > Om NDES-servern använder både ett externt och ett internt namn för en enda nätverksadress, måste certifikatet för serverautentisering ha ett **Ämnesnamn** med ett externt offentligt servernamn och ett **Alternativt ämnesnamn** som innehåller namnet på den interna servern.

2.  På NDES-servern: begär och installera ett certifikat för **klientautentisering** från den interna certifikatutfärdaren eller en offentlig certifikatutfärdare. Detta kan vara samma certifikat som certifikatet för serverautentisering om certifikatet har båda funktioner.

    Certifikatet för klientautentisering måste ha följande egenskaper:

    **Förbättrad nyckelanvändning** – Måste innehålla **Klientautentisering**.

    **Ämnesnamn** – Måste vara samma som DNS-namnet på servern där du installerar certifikatet (NDES-servern).

##### <a name="to-configure-iis-request-filtering"></a>Så här konfigurerar du IIS-begäransfiltrering

1.  På NDES-servern: öppna **IIS-hanteraren**, välj **Standardwebbplats** i rutan **Anslutningar** och öppna **Begäransfiltrering**.

2.  Klicka på **Redigera funktionsinställningar**och ställ in följande:

    **frågesträng (byte)** = **65534**

    **Maximal URL-längd (byte)** = **65534**

3.  Granska följande registernyckel:

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Kontrollera att följande värden anges som DWORD-poster:

    Namn: **MaxFieldLength**, med decimalvärdet **65534**

    Namn: **MaxRequestBytes**, med decimalvärdet **65534**

4.  Starta om NDES-servern. Servern är nu klar att stödja Certifikat Connectorn.

### <a name="task-5---enable-install-and-configure-the-intune-certificate-connector"></a>Uppgift 5 – Aktivera, installera och konfigurera Intunes certifikatanslutningsapp
I det här steget kommer du att:

Aktivera stöd för NDES i Intune.

Hämta, installera och konfigurera en Certificate Connector på NDES-servern.

##### <a name="to-enable-support-for-the-certificate-connector"></a>Så här aktiverar du stöd för Certifikat Connectorn

1.  Öppna [administrationskonsolen för Intune](https://manage.microsoft.com), klicka på **Admin** &gt; **Certifikatanslutningsapp**.

2.  Klicka på **Konfigurera lokal certifikatanslutningsapp**.

3.  Välj **Aktivera Certifikat Connector**och klicka sedan på **OK**.

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>Så här laddar du ner, installerar och konfigurerar Certifikat Connectorn

1.  Öppna [administratörskonsolen i Intune](https://manage.microsoft.com) och klicka sedan på **Admin** &gt; **Hantering av mobila enheter** &gt; **Certifikatanslutningsapp** &gt; **Ladda ned certifikatanslutningsappen**.

2.  När hämtningen är klar kör du det hämtade installationsprogrammet (**ndesconnectorssetup.exe**) på en Windows Server 2012 R2-server. Principmodulen för NDES och CRP-webbtjänsten installeras också samtidigt. (CRP-webbtjänsten, CertificateRegistrationSvc, körs som ett program i IIS).

    > [!NOTE]
    > När du installerar NDES för fristående Intune installeras CRP-tjänsten automatiskt med certifikatanslutningsappen. När du använder Intune med Configuration Manager installerar du certifikatregistreringsplatsen som en separat platssystemroll.

3.  När du tillfrågas om klientcertifikatet för Certifikat Connectorn så klickar du på **Välj**och väljer det certifikat för **klientautentisering** som du installerat på NDES-servern i Uppgift 3.

    När du har valt certifikatet för klientautentisering tas du tillbaka till ytan **Klientcertifikat för Microsoft Intune Certifikat Connector** . Även om certifikatet du valt inte visas, klicka på **Nästa** för att visa egenskaperna för certifikatet. Klicka sedan på **Nästa**och på **Installera**.

4.  När guiden slutförts klickar du på **Starta användargränssnittet för Certifikat Connectorn**innan du stänger guiden.

    > [!TIP]
    > Om du stängt guiden innan du startade användargränssnittet kan du öppna det genom att skriva följande kommando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  I användargränssnittet för **certifikat connectorn** :

    Klicka på **Logga in** och ange autentiseringsuppgifter för en tjänstadministratör i Intune eller för en klientadministratör med behörighet för global administration.

    Om organisationen använder en proxyserver och proxyn krävs för att NDES-servern ska få tillgång till Internet klickar du på **Använd proxyserver** och anger proxyservernamn, port och autentiseringsuppgifter för att ansluta.

    Välj fliken **Avancerat** och ange autentiseringsuppgifter för ett konto som har behörigheten **Utfärda och hantera certifikat** på den utfärdande certifikatutfärdaren. Klicka sedan på **Använd**.

    Nu kan du stänga användargränssnittet för Certifikat Connectorn.

6.  Öppna kommandotolken och skriv **services.msc**. Tryck sedan på **Retur**, högerklicka på **Intune-anslutningstjänsten** och klicka sedan på **Starta om**.

Kontrollera att tjänsten körs genom att öppna en webbläsare och ange följande URL, vilket borde returnera ett **403** -fel:

**https:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

## <a name="next-steps"></a>Nästa steg
Du är nu redo att konfigurera certifikatprofiler enligt beskrivningen i [Konfigurera certifikatprofiler](Configure-Intune-certificate-profiles.md).

