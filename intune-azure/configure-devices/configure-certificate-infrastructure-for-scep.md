---
title: Konfigurera och hantera SCEP-certifikat med Intune
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs om hur du kan konfigurera din infrastruktur. Skapa och tilldela sedan Intune SCEP-certifikatprofiler."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d567d85f-e4ee-458e-bef7-6e275467efce
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 7a2ab1e64fd1ca37f4d086624321201896a989ac
ms.contentlocale: sv-se
ms.lasthandoff: 05/10/2017

---
# <a name="configure-and-manage-scep-certificates-with-intune"></a>Konfigurera och hantera SCEP-certifikat med Intune
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

I det här avsnittet beskrivs hur du kan konfigurera din infrastruktur och sedan skapa och tilldela SCEP-certifikatprofiler (Simple Certificate Enrollment Protocol) med Intune.

## <a name="configure-on-premises-infrastructure"></a>Konfigurera den lokala infrastrukturen

-    **Active Directory-domän**: Alla servrar i det här avsnittet (förutom webbprogramsproxyservern) måste vara anslutna till Active Directory-domänen.

-  **Certifikatutfärdare** (CA): En utfärdare av företagscertifikat som körs på en Enterprise-version av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. Mer information finns i [Installera certifikatutfärdare](http://technet.microsoft.com/library/jj125375.aspx).
    Om certifikatutfärdaren kör Windows Server 2008 R2, måste du [installera snabbkorrigeringen från KB2483564](http://support.microsoft.com/kb/2483564/).

-  **NDES-server**: På en server som kör Windows Server 2012 R2 eller senare måste du konfigurera registreringstjänsten för nätverksenheter (NDES, Network Device Enrollment Service). Intune stöder inte användning av registreringstjänsten för nätverksenheter när den körs på en server som också kör företagscertifikatutfärdaren. Se [Vägledning för registreringstjänsten för nätverksenheter](http://technet.microsoft.com/library/hh831498.aspx) för anvisningar om hur du konfigurerar Windows Server 2012 R2 som värd för registreringstjänsten för nätverksenheter.
NDES-servern måste vara ansluten till den domän där certifikatutfärdaren finns och får inte finnas på samma server som certifikatutfärdaren. Mer information om hur du distribuerar NDES-servern i en separat skog, ett isolerat nätverk eller en intern domän återfinns i [Använda en principmodul med registreringstjänsten för nätverksenheter](https://technet.microsoft.com/library/dn473016.aspx).

-  **Microsoft Intune Certificate Connector**: Använd Intune-portalen för att hämta installationsprogrammet för **Certificate Connector** (**ndesconnectorssetup.exe**). Sen kör du **ndesconnectorssetup.exe** på datorn där du vill installera Certifikat Connector. 
-  **Web Application Proxy-server** (valfritt): Använd en server som kör Windows Server 2012 R2 eller senare som en Web Application Proxy-server (WAP). Den här konfigurationen:
    -  Tillåter enheter att ta emot certifikat med hjälp av en internetanslutning.
    -  Är en säkerhetsrekommendation när enheter ansluter via internet för att ta emot och förnya certifikat.

 > [!NOTE]           
> -    Servern som är värd för WAP [måste installera en uppdatering](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) som aktiverar stöd för de långa URL:er som används av registreringstjänsten för nätverksenheter. Uppdateringen finns med i [samlad uppdatering för december 2014](http://support.microsoft.com/kb/3013769), eller individuellt från [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Dessutom måste den server som är värd för WAP ha ett SSL-certifikat som överensstämmer med det namn som publiceras på externa klienter, samt lita på SSL-certifikatet som används på NDES-servern. Certifikaten gör det möjligt för WAP servern att avbryta SSL-anslutningen från klienter och skapa en ny SSL-anslutning till NDES-servern.
    Information om certifikat för WAP finns i sektionen **Planera certifikat** av [Installera och konfigurera webbprogramproxy för publicering av interna program](https://technet.microsoft.com/library/dn383650.aspx). Allmän information om WAP-servrar finns i [Arbeta med webbprogramsproxy](http://technet.microsoft.com/library/dn584113.aspx).|

### <a name="network-requirements"></a>Nätverkskrav

Tillåt port 443 från Internet till perimeternätverk från alla värdar/IP-adresser på Internet till NDES-servern.

Tillåt alla portar och protokoll som behövs för åtkomst till domänen på den domänanslutna NDES-servern från perimeternätverket till det betrodda nätverket. NDES-servern måste ha åtkomst till certifikatservrar, DNS-servrar, Configuration Manager-servrar och domänkontrollanter.

Vi rekommenderar att du publicerar NDES-servern via en proxyserver, till exempel [Azure AD-programproxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), [Web Access-proxy](https://technet.microsoft.com/library/dn584107.aspx) eller en proxy från en annan leverantör.


### <a name="certificates-and-templates"></a>Certifikat och mallar

|Objekt|Information|
|----------|-----------|
|**Certifikatmall**|Konfigurera den här mallen hos den utfärdande certifikatutfärdaren.|
|**Certifikat för klientautentisering**|Begärs från den utfärdande certifikatutfärdaren eller från en offentlig certifikatutfärdare. Du installerar certifikatet på NDES-servern.|
|**Certifikat för serverautentisering**|Begärs från den utfärdande certifikatutfärdaren eller från en offentlig certifikatutfärdare. Du installerar och binder SSL-certifikatet i IIS på NDES-servern.|
|**Certifikat från betrodd rotcertifikatutfärdare**|Du exporterar detta som en **.cer**-fil från rotcertifikatutfärdaren eller en enhet som litar på rotcertifikatutfärdaren. Tilldela det till enheterna med hjälp av certifikatprofilen för den betrodda certifikatutfärdaren.<br /><br />Du använder ett enstaka certifikat från en betrodd rotcertifikatutfärdare per operativsystemplattform och associerar det med varje betrodd rotcertifikatprofil som du skapar.<br /><br />Du kan använda ytterligare certifikat från betrodda rotcertifikatutfärdare när det behövs. Exempel: du kan göra detta för att ge ett förtroende till en certifikatutfärdare som signerar serverautentiseringscertifikaten för dina WiFi-åtkomstpunkter.|

### <a name="accounts"></a>Konton

|Namn|Information|
|--------|-----------|
|**NDES-tjänstkonto**|Ange ett domänanvändarkonto som ska användas som NDES-tjänstkonto.|

## <a name="configure-your-infrastructure"></a>Konfigurera infrastrukturen
Innan du kan konfigurera certifikatprofiler måste du utföra följande åtgärder, som kräver kunskaper om Windows Server 2012 R2 och Active Directory-certifikattjänster (ADCS):

**Steg 1** – Skapa ett NDES-tjänstkonto

**Steg 2** – Konfigurera certifikatmallar hos certifikatutfärdaren

**Steg 3** – Konfigurera krav på NDES-servern

**Steg 4** – Konfigurera NDES för användning med Intune

**Steg 5** – Aktivera, installera och konfigurera Intune Certificate Connector

#### <a name="step-1---create-an-ndes-service-account"></a>Steg 1 – Skapa ett NDES-tjänstkonto

Skapa domänanvändarkonto som används som NDES-tjänstkontot Du anger det här kontot när du konfigurerar mallar på den utfärdande certifikatutfärdaren innan du installerar och konfigurerar NDES. Kontrollera att användaren har behörigheten standard **Inloggning lokalt**, **Inloggning som tjänst** och **Inloggning som batchjobb**. En del organisationer har härdningsprinciper som inaktiverar dessa rättigheter.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Steg 2 – Konfigurera certifikatmallar hos certifikatutfärdaren
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
        > För iOS- och macOS-certifikatmallar: På fliken **Tillägg** redigerar du **Nyckelanvändning** och ser till att **Signaturen är bevis för ursprung** inte är markerat.

    -   På fliken **Säkerhet** lägger du till NDES-tjänstekontot och ger det **Registreringsrättigheter** för mallen. Intune-administratörer som ska skapa SCEP-profiler behöver **läsrättigheter** så att de kan bläddra till mallen när de skapar SCEP-profiler.

    > [!NOTE]
    > Om du vill återkalla certifikat behöver NDES-tjänstkontot rättigheter för att *Utfärda och hantera certifikat* för varje certifikatmall som används av en certifikatprofil.

3.  Granska **Giltighetsperioden** på mallens flik **Allmänt** . Som standard använder Intune värdet som konfigurerats i mallen. Du kan dock välja att konfigurera certifikatutfärdaren att tillåta att den som begär anger ett annat värde, som du sedan kan ställa in i Intune-administratörskonsolen. Om du alltid vill använda värdet i mallen kan du hoppa över resten av det här steget.

    > [!IMPORTANT]
    > iOS och macOS använder alltid värdet i mallen, oavsett andra konfigurationer som du gör.

Här följer skärmdumpar av en exempelkonfiguration av mallen.

![Mall, fliken för hantering av begäran](.\media\scep_ndes_request_handling.png)

![Mall, fliken för ämnesrad](.\media\scep_ndes_subject_name.jpg)

![Mall, fliken för säkerhet](.\media\scep_ndes_security.jpg)

![Mall, fliken för tillägg](.\media\scep_ndes_extensions.jpg)

![Mall, fliken för utfärdandekrav](.\media\scep_ndes_issuance_reqs.jpg)

>   [!IMPORTANT]
    > I Användningsprinciper lägger du endast till de användningsprinciper som krävs. Bekräfta dina val med säkerhetsadministratörerna.



Så här konfigurerar du att certifikatutfärdaren tillåter att beställaren anger giltighetsperioden:

1. Kör följande kommandon hos certifikatutfärdaren:
    - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
    - **net stop certsvc**
    - **net start certsvc**
2. På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatutfärdaren för att publicera certifikatmallen.
    Välj noden **Certifikatmallar**, klicka på **Åtgärd** -&gt;**Ny** &gt; **Certifikatmall som ska utfärdas** och välj sedan den mall som du skapade i steg 2.
3. Kontrollera att mallen publicerats genom att se om den finns i mappen **Certifikatmallar** .


#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Steg 3 – Konfigurera krav på NDES-servern
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

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Steg 4 – Konfigurera NDES för användning med Intune
I det här steget kommer du att:

-   Konfigurera NDES för användning med den utfärdande certifikatutfärdaren

-   Binda serverautentiseringscertifikatet (SSL) i IIS

-   Konfigurera begäransfiltrering i IIS


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

    ![Maxlängd för URL och fråga i IIS](.\media\SCEP_IIS_max_URL.png)

5.  Starta om servern. Det räcker inte att köra **iisreset** på servern för att genomföra de här ändringarna.
6. Bläddra till http://*FQDN*/certsrv/mscep/mscep.dll. Du bör se en NDES-sida som ser ur ungefär så här:

    ![Testa NDES](.\media\SCEP_NDES_URL.png)

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

##### <a name="to-configure-iis-request-filtering"></a>Så här konfigurerar du IIS-begärandefiltrering

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

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>Steg 5 – Aktivera, installera och konfigurera Intunes certifikatanslutningsapp
I det här steget kommer du att:

Aktivera stöd för NDES i Intune.

Hämta, installera och konfigurera en Certificate Connector på NDES-servern.

##### <a name="to-enable-support-for-the-certificate-connector"></a>Så här aktiverar du stöd för certifikatanslutningsappen

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
4. Välj **Certifikatutfärdare** på bladet **Enhetskonfiguration**.
5.  Välj **Aktivera certifikatanslutningsapp**.

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>Så här hämtar, installerar och konfigurerar du certifikatanslutningsappen

> [!NOTE]
> På grund av ett känt problem måste du hämta, installera och konfigurera certifikatanslutningsappen på följande sätt: [Konfigurera infrastruktur för certifikat för SCEP -> Konfigurera din infrastruktur -> Uppgift 5](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep#a-namebkmkconfigureinfrastructureaconfigure-your-infrastructure)

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
4. Välj **Certifikatutfärdare** på bladet **Enhetskonfiguration**.
5. Välj **Ladda ned certifikatanslutningsappen**.
6.  När hämtningen är klar kör du det hämtade installationsprogrammet (**ndesconnectorssetup.exe**) på en Windows Server 2012 R2-server. Principmodulen för NDES och CRP-webbtjänsten installeras också samtidigt. (CRP-webbtjänsten, CertificateRegistrationSvc, körs som ett program i IIS).

    > [!NOTE]
    > När du installerar NDES för fristående Intune installeras CRP-tjänsten automatiskt med certifikatanslutningsappen. När du använder Intune med Configuration Manager installerar du certifikatregistreringsplatsen som en separat platssystemroll.

3.  När du tillfrågas om klientcertifikatet för certifikatanslutningsappen, väljer du **Välj**och väljer det certifikat för **klientautentisering** som du installerat på NDES-servern i Uppgift 3.

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

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

## <a name="how-to-create-a-scep-certificate-profile"></a>Så här skapar du en SCEP-certifikatprofil

1. I Azure-portalen väljer du arbetsbelastningen **Konfigurera enheter**.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för SCEP-certifikatprofilen.
5. Från listrutan **Plattform** väljer du enhetsplattformen för detta SCEP-certifikat. För närvarande kan du välja någon av följande plattformar för inställning av enhetsbegränsningar:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**
6. Från listrutan **Profil** väljer du **SCEP-certifikat**.
7. På bladet **SCEP-certifikat**, konfigurerar du följande inställningar:
    - **Certifikatets giltighetsperiod** – Om du har kört kommandot **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** på certifikatutfärdaren, vilket gör att en anpassad giltighetsperiod kan användas, kan du ange hur lång tid som återstår innan certifikatet går ut.<br>Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i den angivna certifikatmallen. Om giltighetsperioden i certifikatmallen är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren. 
    - **Nyckellagringsprovider (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10) – Ange var nyckeln till certifikatet ska lagras. Välj något av följande värden:
        - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module) om TPM finns, annars till programvaruprovider för nyckellagring**
        - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module), rapportera annars fel**
        - **Registrera på Passport, rapportera annars fel (Windows 10 och senare)**
        - **Registrera till programvaruprovider för nyckellagring**
    - **Format för namn på certifikatmottagare** – Välj i listan hur mottagarnamnet i certifikatförfrågan ska skapas automatiskt i Intune. Om certifikatet avser en användare kan du ange användarens e-postadress i mottagarnamnet. Välj mellan:
        - **Inte konfigurerat**
        - **Allmänt namn**
        - **Eget namn, inklusive e-post**
        - **Eget namn som e-post**
    - **Alternativt namn för certifikatmottagare** – Ange hur värden för det alternativa certifikatmottagarnamnet i certifikatförfrågan ska skapas automatiskt i Intune. Om du exempelvis valde en användarcertifikattyp kan du ange användarens huvudnamn (UPN) i det alternativa certifikatmottagarnamnet. Om klientcertifikatet ska användas för att autentisera mot en nätverksprincipserver måste du ange användarens huvudnamn som alternativt mottagarnamn. 
    - **Nyckelanvändning** – Ange alternativ för nyckelanvändning för certifikatet. Du kan välja bland följande alternativ: 
        - **Nyckelchiffrering:** Tillåt bara nyckelutbyte när nyckeln är krypterad. 
        - **Digital signatur:** Tillåt bara nyckelutbyte när en digital signatur skyddar nyckeln. 
    - **Nyckelstorlek (bitar)** – Välj antalet bitar som ska finnas i nyckeln. 
    - **Hash-algoritm** (Android, Windows Phone 8.1, Windows 8.1, Windows 10) – Välj en av de tillgängliga typerna av hash-algoritmer som ska användas med det här certifikatet. Välj den högsta säkerhetsnivå som de anslutande enheterna har stöd för. 
    - **Rotcertifikat** – Välj en certifikatprofil från en rotcertifikatutfärdare som du tidigare har konfigurerat och tilldelat till användaren eller enheten. Detta CA-certifikat måste vara rotcertifikatet för den certifikatutfärdare som kommer att utfärda det certifikat som du konfigurerar i den här certifikatprofilen. 
    - **Utökad nyckelanvändning** – Välj **Lägg till** om du vill lägga till värden för certifikatets avsedda syfte. I de flesta fall kräver certifikatet **Klientautentisering** så att användaren eller enheten kan autentisera till en server. Du kan dock lägga till alla andra nyckelanvändningar efter behov. 
    - **Registreringsinställningar**
        - **Tröskelvärde för förnyelse (%)** – Ange i procent hur mycket av certifikatets giltighetstid som får återstå innan förfrågningar om förnyat certifikat görs.
        - **Webbadresser för SCEP-server** – Ange en eller flera webbadresser för NDES-servrar som ska utfärda certifikat via SCEP. 
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.

>[!Note]
> Endast för iOS-enheter: Välj Anpassad under Format för namn på certifikatmottagare om du vill ange ett eget format för namn på certifikatmottagare.
> De två variabler som stöds för närvarande för det anpassade formatet är **Nätverksnamn (cn)** och **E-post (e)**. Genom att använda en kombination av dessa variabler och statiska strängar kan du skapa ett eget format för namn på certifikatmottagare som det här: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US** I det här exemplet har du skapat ett format för namn som, utöver CN- och E-variabler, använder strängar för värden för organisationsenhet, organisation, plats, stat och land. [Det här avsnittet](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) visar funktionen **CertStrToName** och dess strängar som stöds.

## <a name="how-to-assign-the-certificate-profile"></a>Så här tilldelar du certifikatprofilen

Tänk på följande innan du tilldelar certifikatprofiler till grupper:

- När du tilldelar certifikatprofiler till grupper installeras certifikatfilen från certifikatprofilen för betrodd certifikatutfärdare på enheten. Enheten använder SCEP-certifikatprofilen för att skapa en certifikatbegäran från enheten.
- Certifikatprofiler installeras endast på enheter som kör den plattform som du använder när du skapade profilen.
- Du kan tilldela certifikatprofiler till användarsamlingar eller enhetssamlingar.
- Om du vill publicera certifikat till enheter kort efter att enheten registrerats, tilldelar du certifikatprofilen till en användargrupp i stället för en enhetsgrupp. Om du tilldelar till en enhetsgrupp krävs en fullständig enhetsregistrering innan enheten kan ta emot principer.
- Även om du tilldelar varje profil separat, måste du också tilldela den betrodda rotcertifikatutfärdaren och SCEP- eller PKCS-profilen. Annars misslyckas SCEP- eller PKCS-certifikatprincipen.

Du hittar allmän information om hur du tilldelar profiler i [Så här tilldelar du enhetsprofiler](how-to-assign-device-profiles.md).


