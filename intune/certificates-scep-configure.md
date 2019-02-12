---
title: Använda SCEP-certifikat med Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera ditt lokala AD-domän, skapa en certifikatutfärdare, konfigurera NDES-servern och installera Intune Certificate Connector om du vill använda SCEP-certifikat i Microsoft Intune. Sedan skapar du en SCEP-certifikatprofil och tilldelar den till grupper. Se även olika händelse-id:n och deras beskrivningar, samt diagnostikkoderna för Intune-anslutningsappen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 1/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50235e4e21e738081dc1b41d8e6a8b6210430064
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838146"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>Konfigurera och använda SCEP-certifikat med Intune

I den här artikeln beskrivs hur du kan konfigurera din infrastruktur och sedan skapa och tilldela SCEP-certifikatprofiler (Simple Certificate Enrollment Protocol) med Intune.

## <a name="configure-on-premises-infrastructure"></a>Konfigurera den lokala infrastrukturen

- **Active Directory-domän**: Alla servrar i det här avsnittet (förutom webbprogramsproxyservern) måste vara anslutna till Active Directory-domänen.

- **Certifikatutfärdare**: Måste vara en Microsoft-utfärdare av företagscertifikat som körs på en Enterprise-version av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. Mer information finns i [Installera certifikatutfärdare](http://technet.microsoft.com/library/jj125375.aspx).
    Om certifikatutfärdaren kör Windows Server 2008 R2, måste du [installera snabbkorrigeringen från KB2483564](http://support.microsoft.com/kb/2483564/).

- **NDES-server**: På en Windows Server 2012 R2 eller senare konfigurerar du serverrollen Registreringstjänst för nätverksenheter (NDES). Intune stöder inte användning av registreringstjänsten för nätverksenheter på en server som även kör företagscertifikatutfärdaren. Se [Vägledning för registreringstjänsten för nätverksenheter](http://technet.microsoft.com/library/hh831498.aspx) för anvisningar om hur du konfigurerar Windows Server 2012 R2 som värd för NDES.
NDES-servern måste vara ansluten till en domän i samma skog som företagscertifikatutfärdaren. Mer information om hur du distribuerar NDES-servern i en separat skog, ett isolerat nätverk eller en intern domän finns i [Använda en principmodul med registreringstjänsten för nätverksenheter](https://technet.microsoft.com/library/dn473016.aspx).

- **Microsoft Intune Certificate Connector**: Ladda ned installationsprogrammet för **Certificate Connector** (**NDESConnectorSetup.exe**) från Intune-administrationsportalen. Du kör installationsprogrammet på servern med NDES-rollen.  

  - NDES-certifikatanslutningsappen har även stöd för FIPS-läge (Federal Information Processing Standard). FIPS krävs inte, men du kan utfärda och återkalla certifikat när det är aktiverat.

- **Web Application Proxy-server** (valfritt): Använd en server som kör Windows Server 2012 R2 eller senare som WAP-server (Web Application Proxy). Den här konfigurationen:
  - Tillåter enheter att ta emot certifikat med hjälp av en internetanslutning.
  - Är en säkerhetsrekommendation när enheter ansluter via internet för att ta emot och förnya certifikat.
  
- **Azure AD-programproxy** (valfritt): Azure AD-programproxyn kan användas i stället för en dedikerad WAP-server när NDES-servern ska publiceras på Internet. Mer information finns i [Så här tillhandahåller du säker fjärråtkomst till lokala program](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### <a name="additional"></a>Mer information

- Servern som är värd för WAP [måste installera en uppdatering](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) som aktiverar stöd för de långa URL:er som används av registreringstjänsten för nätverksenheter. Uppdateringen finns med i [samlad uppdatering för december 2014](http://support.microsoft.com/kb/3013769), eller individuellt från [KB3011135](http://support.microsoft.com/kb/3011135).
- WAP-servern måste ha ett SSL-certifikat som överensstämmer med det namn som publiceras på externa klienter och ha förtroende för de SSL-certifikatet som används på NDES-servern. Certifikaten gör det möjligt för WAP servern att avbryta SSL-anslutningen från klienter och skapa en ny SSL-anslutning till NDES-servern.

Mer information finns i [Planera certifikat för WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) och [allmän information om WAP-servrar](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="network-requirements"></a>Nätverkskrav

Om du inte använder en omvänd proxy, till exempel WAP eller Azure AD App Proxy, tillåter du TCP-trafik på port 443 från alla värdar/IP-adresser på Internet till NDES-servern.

Tillåt alla portar och protokoll som behövs mellan NDES-servern och alla stöttande infrastruktur. Till exempel behöver NDES-servern kommunicera med certifikatutfärdaren, DNS-servrar, Configuration Manager-servrar, domänkontrollanter och eventuellt andra tjänster i din miljö.

Vi rekommenderar starkt att du publicerar NDES-servern via en omvänd proxy, till exempel [Azure AD Application Proxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), [Web Access Proxy](https://technet.microsoft.com/library/dn584107.aspx) eller en proxy från tredje part.

### <a name="certificates-and-templates"></a>Certifikat och mallar  

|Objekt|Information|
|----------|-----------|
|**Certifikatmall**|Konfigurera den här mallen hos den utfärdande certifikatutfärdaren.|
|**Certifikat för klientautentisering**|Begärs från den utfärdande certifikatutfärdaren eller från en offentlig certifikatutfärdare. Du installerar certifikatet på NDES-servern.|
|**Certifikat för serverautentisering**|Begärs från den utfärdande certifikatutfärdaren eller från en offentlig certifikatutfärdare. Du installerar och binder SSL-certifikatet i IIS på NDES-servern. Om certifikatet har användningarna av klientens och serverns autentiseringsnycklar inställt på (**Förbättrad nyckelanvändning**) kan du använda samma certifikat.|
|**Certifikat från betrodd rotcertifikatutfärdare**|Du exporterar detta certifikat som en **.cer**-fil från rotcertifikatutfärdaren eller en enhet som litar på rotcertifikatutfärdaren. Sedan tilldelar du den till användare, enheter eller båda med hjälp av certifikatprofilen för betrodd certifikatutfärdare.<br /><b>Obs!<b /> När en profil för SCEP-certifikatet har tilldelats så måste du tilldela den betrodda rotcertifikatsprofil som refereras i SCEP-certifikatprofilen till samma användare eller enhetsgrupp.<br /><br />Du använder ett enstaka certifikat från en betrodd rotcertifikatutfärdare per operativsystemplattform och associerar det med varje betrodd rotcertifikatprofil som du skapar.<br /><br />Du kan använda ytterligare certifikat från betrodda rotcertifikatutfärdare när det behövs. Exempel: du kan göra detta för att ge ett förtroende till en certifikatutfärdare som signerar serverautentiseringscertifikaten för dina WiFi-åtkomstpunkter.|

### <a name="accounts"></a>Konton

|Namn|Information|
|--------|-----------|
|**NDES-tjänstkonto**|Ange ett domänanvändarkonto som används som NDES-tjänstkontot. |

## <a name="configure-your-infrastructure"></a>Konfigurera infrastrukturen
Du måste slutföra följande steg innan du kan konfigurera certifikatprofiler. Dessa steg kräver kunskaper om Windows Server 2012 R2 eller senare om Active Directory Certificate Services (ADCS):

#### <a name="step-1---create-an-ndes-service-account"></a>Steg 1 – Skapa ett NDES-tjänstkonto

Skapa domänanvändarkonto som används som NDES-tjänstkontot Du anger det här kontot när du konfigurerar mallar på den utfärdande certifikatutfärdaren innan du installerar och konfigurerar NDES. Kontrollera att användaren har standardrättigheterna, **logga in lokalt**, **logga in som en tjänst** och **logga in som ett batchjobb**. En del organisationer har härdningsprinciper som inaktiverar dessa rättigheter.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Steg 2 – Konfigurera certifikatmallar hos certifikatutfärdaren
I det här steget kommer du att:

- Konfigurera en certifikatmall för NDES
- Publicera certifikatmallen för NDES

##### <a name="configure-the-certification-authority"></a>Konfigurera certifikatutfärdaren

1. Logga in som företagsadministratör.

2. På den utfärdande certifikatutfärdaren använder du snapin-modulen Certificate Templates för att skapa en ny anpassad mall. Kan du även kopiera en befintlig mall och sedan uppdatera den befintliga mallen (t. ex. användarmallen) för användning med NDES.

   >[!NOTE]
   > NDES-certifikatmallen måste baseras på en v2-certifikatmall (med Windows 2003-kompatibilitet).

   Mallen måste ha följande konfigurationer:

   - I **allmänhet**:
   
       - Bekräfta att egenskapen **Publicera certifikatet i Active Directory** **inte** är markerad.
       - Ange ett eget **visningsnamn för mallen**.

   - I **Ämnesnamn** väljer du **Anges i begäran**. (Säkerhet tvingas av Intune-principmodulen för NDES).

   - Under **Tillägg** bekräftar du att **beskrivningen av användningsprinciper** omfattar **Klientautentisering**.

     > [!IMPORTANT]
     > För iOS- och macOS-certifikatmallar: På fliken **Tillägg** redigerar du **Nyckelanvändning** och bekräftar att **Signaturen är bevis för ursprung** inte är markerat.

   - Under **Säkerhet** lägger du till NDES-tjänstekontot och ger det **Registreringsrättigheter** för mallen. Intune-administratörer som skapar SCEP-profiler behöver **läsrättigheter** så att de kan bläddra till mallen när de skapar SCEP-profiler.

     > [!NOTE]
     > Om du vill återkalla certifikat behöver NDES-tjänstkontot rättigheter för att *Utfärda och hantera certifikat* för varje certifikatmall som används av en certifikatprofil.

3. Granska **Giltighetsperioden** på mallens flik **Allmänt** . Som standard använder Intune värdet som konfigurerats i mallen. Du kan dock konfigurera certifikatutfärdaren så att den tillåter att beställaren anger ett annat värde som du sedan kan ställa in i Intune-administratörskonsolen. Om du alltid vill använda värdet i mallen kan du hoppa över resten av det här steget.

   > [!IMPORTANT]
   > iOS och macOS använder alltid värdet i mallen, oavsett andra konfigurationer som du gör.

Exempelkonfiguration för mallar:

![Mall, fliken för hantering av begäran](./media/scep_ndes_request_handling.png)

![Mall, fliken för ämnesrad](./media/scep_ndes_subject_name.jpg)

![Mall, fliken för säkerhet](./media/scep_ndes_security.jpg)

![Mall, fliken för tillägg](./media/scep_ndes_extensions.jpg)

![Mall, fliken för utfärdandekrav](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> I Användningsprinciper lägger du endast till de användningsprinciper som krävs. Bekräfta dina val med säkerhetsadministratörerna.

Konfigurera så att certifikatutfärdaren tillåter att beställaren anger giltighetsperioden:

1. Kör följande kommandon hos certifikatutfärdaren:
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatutfärdaren för att publicera certifikatmallen.
   Välj noden **Certifikatmallar**, klicka på **Åtgärd** > **Ny** > **Certifikatmall som ska utfärdas**. Välj sedan den mall du skapade i steg 2.

3. Kontrollera att mallen publicerats genom att se om den finns i mappen **Certifikatmallar** .

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Steg 3 – Konfigurera krav på NDES-servern
I det här steget kommer du att:

- Lägga till NDES till en Windows Server och konfigurera IIS för att stöda NDES
- Lägga till NDES-tjänstkontot i gruppen IIS_IUSR
- Ange tjänstens huvudnamn (SPN) för NDES-tjänstkontot

1. Logga in som **företagsadministratör** på servern som står värd för NDES och använd sedan [guiden Lägg till roller och funktioner](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) för att installera NDES:

   1. I guiden väljer du **Active Directory-certifikattjänster** för att få tillgång till AD CS-rolltjänsterna. Välj **Registreringstjänsten för nätverksenheten**, avmarkera **Certifikatutfärdare**och slutför guiden.

      > [!TIP]
      > Markera inte **Stäng** i **Installationsförlopp**. Markera i stället länken **Konfigurera Active Directory-certifikattjänster på målservern**. Då öppnas guiden **AD CS-konfiguration** som du använder för nästa steg. När AD CS-konfiguration öppnats stänger du guiden Lägg till roller och funktioner.

   2. När NDES läggs till på servern installerar guiden även IIS. Bekräfta att IIS har följande konfiguration:

       - **Webbserver** > **Säkerhet** > **Begäransfiltrering**

       - **Webbserver** > **Programutveckling** > **ASP.NET 3.5** 

            Om du installerar ASP.NET 3.5 installeras även .NET Framework 3.5. När du installerar .NET Framework 3.5, installera både kärnfunktionen **.NET Framework 3.5** och **HTTP-aktivering**.

       - **Webbserver** > **Programutveckling** > **ASP.NET 4.5** 

            Om du installerar ASP.NET 4.5 installeras även .NET Framework 4.5. När du installerar .NET Framework 4.5 installerar du kärnfunktionen **.NET Framework 4.5**, **ASP.NET 4.5** och funktionen **WCF-tjänster** > **HTTP-aktivering**.

       - **Hanteringsverktyg** > **IIS 6-kompatibilitetshantering** > **IIS 6-metabaskompatibilitet**

       - **Hanteringsverktyg** > **IIS 6-kompatibilitetshantering** > **IIS 6 WMI-kompatibilitet**

       - På servern lägger du till NDES-tjänstkontot som medlem i den lokala gruppen **IIS_IUSR**.

2. Kör följande kommando i en upphöjd kommandotolk och ange SPN för NDES-tjänstkontot:

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    Exempel: om NDES-serverns namn är **Server01**, domänen är **Contoso.com**och tjänstkontot är **NDESService**, använd:

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Steg 4 – Konfigurera NDES för användning med Intune
I det här steget kommer du att:

- Konfigurera NDES för användning med den utfärdande certifikatutfärdaren
- Binda serverautentiseringscertifikatet (SSL) i IIS
- Konfigurera begäransfiltrering i IIS

1. Öppna AD CS-konfigurationsguiden och utför följande uppdateringar på NDES-servern:

    > [!TIP]
    > Om du klickade på länken i föregående steg är guiden redan öppen. Annars öppnar du Serverhanteraren för att komma åt konfigurationen efter distribution för Active Directory-certifikattjänster.

   - Under **Rolltjänster** väljer du **registreringstjänsten för nätverksenheter**
   - Under **Tjänstkonto för NDES** anger du NDES-tjänstkontot
   - Under **Certifikatutfärdare för NDES** klickar du på **Välj**och sedan väljer du den utfärdande certifikatutfärdaren där du konfigurerade certifikatmallen
   - Under **Kryptografi för NDES** ställer du in nyckellängden enligt företagets krav.
   - Under **Bekräftelse** väljer du **Konfigurera** för att slutföra guiden.

2. När guiden är slutförd uppdaterar du följande registernyckel på NDES-servern:

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    Identifiera certifikatmallens **Syfte** (finns på fliken **Hantering av begäranden**) för att uppdatera nyckeln. Sedan uppdaterar du den motsvarande posten i registret genom att ersätta den befintliga informationen med namnet på den certifikatmall (inte mallens visningsnamn) som du angav i steg 2. I följande tabell visas certifikatmallens syfte för värdena i registret:

    |Certifikatmallens syfte (på fliken Hantering av begäranden)|Registervärde som redigeras|Värde som visas i Intune-administratörskonsolen för SCEP-profilen|
    |---|---|---|
    |Signatur|SignatureTemplate|Digital signatur|
    |Kryptering|EncryptionTemplate|Nyckelchiffrering|
    |Signatur och kryptering|GeneralPurposeTemplate|Nyckelchiffrering<br/>Digital signatur|

    Exempel: Om syftet för certifikatmallen är **Kryptering**, ersätter du värdet **EncryptionTemplate** värdet med namnet på certifikatmallen.

3. NDES-servern tar emot långa URL:er (frågor) som kräver att du lägger till två registerposter:


   |                        Plats                        |      Värde      | Typ  |      Data       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534 (decimal) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534 (decimal) |

4. I IIS-hanteraren väljer du **Standardwebbplats** > **Förfrågningsfiltrering** > **Redigera inställningen**. Ändra **Högsta URL-längd** och **Maximal frågesträng** till *65534* enligt exemplet:

    ![Maxlängd för URL och fråga i IIS](./media/SCEP_IIS_max_URL.png)

5. Starta om servern. Använd inte **iisreset**; den genomför inte de här ändringarna.
6. Bläddra till `http://*FQDN*/certsrv/mscep/mscep.dll`. Du bör se en NDES-sida som ser ur ungefär så här:

    ![Testa NDES](./media/SCEP_NDES_URL.png)

    Om du får ett **503 tjänsten ej tillgänglig**, kontrollerar du loggboken. Det är troligt att programpoolen har stoppats på grund av en saknad behörighet för NDES-användaren. Dessa rättigheter beskrivs i steg 1.

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>Installera och bind certifikat på NDES-servern

1. På NDES-servern: begär och installera ett certifikat för **serverautentisering** från den interna certifikatutfärdaren eller en offentlig certifikatutfärdare. Bind sedan SSL-certifikatet i IIS.

    > [!TIP]
    > När du bundit SSL-certifikatet i IIS installerar du ett certifikat för klientautentisering. Det här certifikatet kan utfärdas av vilken certifikatutfärdare som helst som är betrodd av NDES-servern. Samma certifikat kan användas om certifikatet har användningarna av klientens och serverns autentiseringsnycklar inställt på (**Förbättrad nyckelanvändning**). Granska följande steg för information om dessa certifikat för autentisering.

   1. När du har hämtat ett certifikat för serverautentisering öppnar du **IIS-hanteraren** och väljer **standardwebbplatsen**. I fönstret **Åtgärder** väljer du **Bindningar**.

   2. Välj **Lägg till**, ställ in **Typ** till **https**och kontrollera att porten är **443**. Endast port 443 stöds för fristående Intune.

   3. För **SSL-certifikat** anger du certifikatet för serverautentisering.

      > [!NOTE]
      > Om NDES-servern använder ett externt och internt namn för en enda nätverksadress måste certifikatet för serverautentisering ha:
      > - Ett **Ämnesnamn** med ett externt offentligt servernamn
      > - Ett **Alternativt ämnesnamn** som innehåller det interna namnet på servern

2. På NDES-servern: begär och installera ett certifikat för **klientautentisering** från den interna certifikatutfärdaren eller en offentlig certifikatutfärdare. Detta certifikat kan vara samma certifikat som certifikatet för serverautentisering om certifikatet har båda funktioner.

    Certifikatet för klientautentisering måste ha följande egenskaper:

    - **Förbättrad nyckelanvändning**: Värdet måste innehålla **Klientautentisering**

    - **Ämnesnamn**: Värdet måste vara samma som DNS-namnet på servern där du installerar certifikatet (NDES-servern)

##### <a name="configure-iis-request-filtering"></a>Konfigurera IIS-begäransfiltrering

1. På NDES-servern öppnar du **IIS-hanteraren**, väljer **Standardwebbplats** i rutan **Anslutningar** och öppnar **Begäransfiltrering**.

2. Välj **Redigera funktionsinställningar** och ställ in följande värden:

    - **frågesträng (byte)** = **65534**
    - **Maximal URL-längd (byte)** = **65534**

3. Granska följande registernyckel:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    Bekräfta att följande värden har angetts som DWORD-poster:

    - Namn: **MaxFieldLength**, med decimalvärdet **65534**
    - Namn: **MaxRequestBytes**, med decimalvärdet **65534**

4. Starta om NDES-servern. Servern är nu klar att stödja Certifikat Connectorn.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>Steg 5 – Aktivera, installera och konfigurera Intunes certifikatanslutningsapp
I det här steget kommer du att:

- Aktivera stöd för NDES i Intune.
- Ladda ned, installera och konfigurera en Certificate Connector på servern som är värd för rollen för registreringstjänsten för nätverksenheter (NDES) på en server i din miljö. Du kan installera flera NDES-servrar med en Microsoft Intune Certificate Connector-komponent på varje NDES-server för att öka skalan för NDES-implementering i din organisation.

##### <a name="download-install-and-configure-the-certificate-connector"></a>Ladda ned, installera och konfigurera certifikatanslutningsappen

> [!IMPORTANT] 
> Microsoft Intune Certificate Connector **måste** installeras på en separat Windows-server. Den kan inte installeras på den utfärdande certifikatutfärdaren (CA). Den **måste** också installeras på samma server som rollen Network Device Enrollment Service (NDES).

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Certifikatutfärdare** > **Lägg till**
3. Hämta och spara anslutningsfilen. Spara den på en plats som är tillgänglig från servern där du ska installera anslutningsappen.

    ![ConnectorDownload](./media/certificates-download-connector.png)

4. När nedladdningen är klar går du till den server som är värd för rollen Network Device Enrollment Service (NDES) (Registreringstjänst för nätverksenheter). Efter det:

    1. Se till att .NET 4.5 Framework är installerat, eftersom det krävs av NDES-certifikatanslutningsappen. .NET 4.5 framework ingår automatiskt i Windows Server 2012 R2 och senare versioner.
    2. Kör installationsprogrammet (**NDESConnectorSetup.exe**). Principmodulen för NDES och CRP-webbtjänsten installeras också samtidigt. CRP-webbtjänsten, CertificateRegistrationSvc, körs som ett program i IIS.

    > [!NOTE]
    > När du installerar NDES för fristående Intune installeras CRP-tjänsten automatiskt med certifikatanslutningsappen. När du använder Intune med Configuration Manager installerar du certifikatregistreringsplatsen som en separat platssystemroll.

5. När du tillfrågas om klientcertifikatet för certifikatanslutningsappen, väljer du **Välj**och väljer det certifikat för **klientautentisering** som du installerat på NDES-servern i steg 4.

    När du har valt certifikatet för klientautentisering tas du tillbaka till ytan **Klientcertifikat för Microsoft Intune Certifikat Connector** . Även om certifikatet du valt inte visas väljer du **Nästa** för att visa egenskaperna för certifikatet. Välj **Nästa** och sedan **Installera**.

    > [!IMPORTANT]
    > Internet Explorer Enhanced Security Configuration [måste vara inaktiverat på den NDES-server](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) som är värd för Intune Certificate Connector.

6. När guiden slutförts väljer du **Starta användargränssnittet för Certificate Connector** innan du stänger guiden.

    > [!TIP]
    > Om du stängt guiden innan du startade användargränssnittet kan du öppna det genom att skriva följande kommando:
    >
    > <installationssökväg>\NDESConnectorUI\NDESConnectorUI.exe

7. I användargränssnittet för **certifikat connectorn** :

    Välj **Logga in** och ange autentiseringsuppgifter för en tjänstadministratör i Intune eller för en klientadministratör med behörighet för global administration. När du har loggat in laddar Intune Certificate Connector ned ett certifikat från Intune. Det här certifikatet används för autentisering mellan anslutningsappen och Intune.

    > [!IMPORTANT]
    > Användarkontot måste tilldelas en giltig Intune-licens. NDESConnectorUI.exe misslyckas om användarkontot inte har en giltig Intune-licens.

    Om din organisation använder en proxyserver och proxyn krävs för att NDES-servern ska få åtkomst till Internet, välj **Använd proxyserver**. Ange sedan proxyservernamn, port och autentiseringsuppgifter för att ansluta.

    Välj fliken **Avancerat** och ange autentiseringsuppgifter för ett konto som har behörigheten **Utfärda och hantera certifikat** på den utfärdande certifikatutfärdaren. **Spara** ändringarna.

    Nu kan du stänga användargränssnittet för Certifikat Connectorn.

8. Öppna en kommandotolk, skriv **services.msc** och tryck på **retur**. Högerklicka på **Intune-anslutningstjänsten** > **Starta om**.

Kontrollera att tjänsten körs genom att öppna en webbläsare och ange följande URL. Det borde returnera ett **403**-fel:

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> Stöd för TSL 1.2 ingår i NDES-certifikatanslutningsappen. Om servern med NDES-certifikatanslutningsappen installerat stödjer TLS 1.2 används därmed TLS 1.2. Om servern inte stödjer TLS 1.2 används TLS 1.1. För närvarande används TLS 1.1 för autentisering mellan enheter och servern.

## <a name="create-a-scep-certificate-profile"></a>Skapa en SCEP-certifikatprofil

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange ett **namn** och en **beskrivning** för SCEP-certifikatprofilen.
4. Från listrutan **Plattform** väljer du enhetsplattformen för detta SCEP-certifikat. För närvarande kan du välja någon av följande plattformar för inställning av enhetsbegränsningar:
   - **Android**
   - **Android enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 och senare**
   - **Windows 10 och senare**
5. Från listrutan **Profil** väljer du **SCEP-certifikat**.
6. Ange följande inställningar:

   - **Certifikattyp**: Välj **Användare** för användarcertifikat. Välj **Enhet** för användarlösa enheter, till exempel informationsdatorer. **Enhetscertifikat** är tillgängliga för följande plattformar:  
     - iOS
     - Windows 8.1 och senare
     - Windows 10 och senare
     - Android enterprise

   - **Ämnesnamnets format**: Välj hur ämnesnamnet i certifikatbegäran ska skapas automatiskt av Intune. Alternativen ändras beroende på om du väljer certifikattypen **Användare** eller certifikattypen **Enhet**. 

        **Certifikattypen Användare**  

        Du kan ta med användarens e-postadress i ämnesnamnet. Välj mellan:

        - **Inte konfigurerat**
        - **Allmänt namn**
        - **Eget namn, inklusive e-post**
        - **Eget namn som e-post**
        - **IMEI (International Mobile Equipment Identity)**
        - **Serienummer**
        - **Anpassad**: När du väljer det här alternativet visas även textrutan **Anpassad**. Använd det här fältet om du vill ange ett anpassat format för ämnesnamnet, inklusive variabler. Anpassat format stöder två variabler: **Eget namn (CN)** och **E-postadress (E)**. **Eget namn (cn)** kan ställas in till någon av följande variabler:

            - **CN={{UserName}}**: Användarens huvudnamn, t.ex. janedoe@contoso.com
            - **CN={{AAD_Device_ID}}**: Ett ID som tilldelas när du registrerar en enhet i Azure Active Directory (AD). Detta ID används vanligtvis för att autentisera med Azure AD.
            - **CN={{SERIALNUMBER}}**: Det unika serienumret (SN) som vanligtvis används av tillverkaren för att identifiera en enhet
            - **CN={{IMEINumber}}**: Det unika IMEI-numret (International Mobile Equipment Identity) som används för att identifiera en mobiltelefon
            - **CN={{OnPrem_Distinguished_Name}}**: En serie relativa unika namn som är avgränsade med kommatecken, till exempel `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

                Om du vill använda variabeln `{{OnPrem_Distinguished_Name}}` måste du synkronisera användarattributet `onpremisesdistingishedname` med hjälp av [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) till din Azure AD.

            - **CN={{onPremisesSamAccountName}}**: Administratörer kan synkronisera samAccountName-attributet från Active Directory till Azure AD genom att Azure AD kopplas till ett attribut med namnet `onPremisesSamAccountName`. Intune kan ersätta denna variabel som en del av en begäran om certifikatutfärdande i ämnet på ett SCEP-certifikat.  Attributet samAccountName är användarens inloggningsnamn som används för att stödja klienter och servrar från en tidigare version av Windows (före Windows 2000). Formatet på användarens inloggningsnamn är: `DomainName\testUser`, eller endast `testUser`.

                Om du vill använda variabeln `{{onPremisesSamAccountName}}` måste du synkronisera användarattributet `onPremisesSamAccountName` med hjälp av [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) till din Azure AD.

            Genom att kombinera en eller flera av dessa variabler och statiska strängar kan du skapa ett anpassat format för ämnesnamnet, till exempel:  

            **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

            I det här exemplet skapade du ett format som utöver variablerna CN och E använder strängar för värdena organisationsenhet, organisation, plats, delstat och land. [CertStrToName-funktionen](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) beskriver den här funktionen och dess strängar som stöds.

        **Certifikattypen Enhet**  

        När du använder certifikattypen **Enhet** kan du också använda följande enhetscertifikatsvariabler för värdet:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Dessa variabler kan läggas till med statisk text i en textruta för anpassat värde. Till exempel kan det allmänna namnet läggas till som `CN = {{DeviceName}}text`.

        > [!IMPORTANT]
        >  - I den statiska texten för ämnet omvandlas hakparenteser **{}** som inte omsluter en variabel till ett fel. 
        >  - När du använder en variabel för enhetscertifikat omger du variabeln med klammerparenteser **{}**.
        >  - `{{FullyQualifiedDomainName}}` fungerar endast för Windows-enheter och domänanslutna enheter. 
        >  -  När du använder enhetsegenskaper som IMEI, serienummer och fullständigt domännamn i ämnet eller SAN för ett certifikat, måste du tänka på att de här egenskaperna kan förfalskas av en person med åtkomst till enheten.
        >  - Profilen kan inte installeras på enheten om de angivna enhetsvariablerna inte stöds. Om {{IMEI}} t.ex. används i ämnesnamnet för SCEP-profilen som tilldelats till en enhet som inte har ett IMEI-nummer, misslyckas profilinstallationen. 


   - **Alternativt namn för certifikatmottagare**: Ange hur Intune automatiskt ska skapa värden för det alternativa certifikatmottagarnamnet i certifikatförfrågan. Alternativen ändras beroende på om du väljer certifikattypen **Användare** eller certifikattypen **Enhet**. 

        **Certifikattypen Användare**  

        Följande attribut är tillgängliga:

        - E-postadress
        - UPN (User Principal Name)

            Om du exempelvis valde en användarcertifikattyp kan du ange användarens huvudnamn (UPN) i det alternativa certifikatmottagarnamnet. Om ett klientcertifikat används för att autentisera mot en nätverksprincipserver, måste du ange alternativt mottagarnamn som UPN. 

        **Certifikattypen Enhet**  

        En textruta för tabellformat som du kan anpassa. Följande attribut är tillgängliga:

        - DNS

        Med certifikattypen **Enhet** kan du använda följande variabler för enhetscertifikat för värdet:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Dessa variabler kan läggas till med statisk text i textrutan för anpassat värde. Till exempel DNS-attributet kan läggas till som `DNS name = {{AzureADDeviceId}}.domain.com`.

        > [!IMPORTANT]
        >  - I den statiska texten för SAN fungerar inte klammerparenteser **{}**, pipe-symboler **|** eller semikolon **;**. 
        >  - När du använder en variabel för enhetscertifikat omger du variabeln med klammerparenteser **{}**.
        >  - `{{FullyQualifiedDomainName}}` fungerar endast för Windows-enheter och domänanslutna enheter. 
        >  -  När du använder enhetsegenskaper som IMEI, serienummer och fullständigt domännamn i ämnet eller SAN för ett certifikat, måste du tänka på att de här egenskaperna kan förfalskas av en person med åtkomst till enheten.
        >  - Profilen kan inte installeras på enheten om de angivna enhetsvariablerna inte stöds. Om {{IMEI}} t.ex. används i alternativt namn för certifikatmottagare för SCEP-profilen som tilldelats till en enhet som inte har ett IMEI-nummer, misslyckas profilinstallationen.  

   - **Certifikatets giltighetsperiod**: Om du körde kommandot `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` på certifikatutfärdaren, vilket gör att en anpassad giltighetsperiod kan användas, kan du ange hur lång tid som återstår innan certifikatet går ut.<br>Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i certifikatmallen. Om giltighetsperioden i certifikatmallen till exempel är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren. 
   - **Nyckellagringsprovider (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): Ange var nyckeln till certifikatet lagras. Välj något av följande värden:
     - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module) om TPM finns, annars till programvaruprovider för nyckellagring**
     - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module), rapportera annars fel**
     - **Registrera på Passport, rapportera annars fel (Windows 10 och senare)**
     - **Registrera till programvaruprovider för nyckellagring**

   - **Nyckelanvändning**: Ange nyckelanvändningsalternativen för certifikatet. Alternativen är:
     - **Nyckelchiffrering**: Tillåt bara nyckelutbyte när nyckeln är krypterad
     - **Digital signatur**: Tillåt bara nyckelutbyte när en digital signatur skyddar nyckeln
   - **Nyckelstorlek (bitar)**: Välj antalet bitar i nyckeln
   - **Hash-algoritm** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): Välj en av de tillgängliga typerna av hash-algoritmer som ska användas med det här certifikatet. Välj den högsta säkerhetsnivå som de anslutande enheterna har stöd för.
   - **Rotcertifikat**: Välj en certifikatprofil från en rotcertifikatutfärdare som du tidigare har konfigurerat och tilldelat till användaren och/eller enheten. Detta CA-certifikat måste vara rotcertifikatet för den certifikatutfärdare som utfärdar det certifikat som du konfigurerar i den här certifikatprofilen. Glöm inte att tilldela den här betrodda rotcertifikatprofilen till samma grupp som tilldelats i SCEP-certifikatprofilen.
   - **Förbättrad nyckelanvändning**: **Lägg till** värden för certifikatets avsedda syfte. I de flesta fall kräver certifikatet **Klientautentisering** så att användaren eller enheten kan autentisera till en server. Du kan dock lägga till alla andra nyckelanvändningar efter behov.
   - **Registreringsinställningar**
     - **Tröskelvärde för förnyelse (%)**: Ange i procent hur mycket av certifikatets giltighetstid som får återstå innan förfrågningar om förnyat certifikat görs.
     - **Webbadresser för SCEP-server**: Ange en eller flera webbadresser för de NDES-servrar som utfärdar certifikat via SCEP. Ange exempelvis något i stil med `https://ndes.contoso.com/certsrv/mscep/mscep.dll`.
     - Välj **OK** och **Skapa** sedan din profil.

Profilen skapas och visas i fönstret med profillistan.

## <a name="assign-the-certificate-profile"></a>Tilldela certifikatprofilen

Tänk på följande innan du tilldelar certifikatprofiler till grupper:

- När du tilldelar certifikatprofiler till grupper installeras certifikatfilen från certifikatprofilen för betrodd certifikatutfärdare på enheten. Enheten använder SCEP-certifikatprofilen för att skapa en certifikatbegäran från enheten.
- Certifikatprofiler installeras endast på enheter som kör den plattform som du använder när du skapade profilen.
- Du kan tilldela certifikatprofiler till användarsamlingar eller enhetssamlingar.
- Om du vill publicera certifikat till enheter kort efter att enheten registrerats, tilldelar du certifikatprofilen till en användargrupp i stället för en enhetsgrupp. Om du tilldelar till en enhetsgrupp krävs en fullständig enhetsregistrering innan enheten kan ta emot principer.
- Även om du tilldelar varje profil separat, måste du också tilldela den betrodda rotcertifikatutfärdaren och SCEP- eller PKCS-profilen. Annars misslyckas SCEP- eller PKCS-certifikatprincipen.

    > [!NOTE]
    > Du bör förvänta dig att se flera kopior av certifikaten i hanteringsprofilen för iOS om du distribuerar flera resursprofiler som använder samma certifikatprofil.

Du hittar allmän information om hur du tilldelar profiler i [tilldela enhetsprofiler](device-profile-assign.md).

## <a name="intune-connector-setup-verification-and-troubleshooting"></a>Konfigurationsverifiering och felsökning för Intune-anslutningsappen

För att felsöka och verifiera konfigurationen av Intune-anslutningsappen läser du [Exempelskript för certifikatutfärdare](https://aka.ms/intuneconnectorverificationscript)

## <a name="intune-connector-events-and-diagnostic-codes"></a>Händelser och diagnostikkoder för Intune-anslutningsappen

Från och med version 6.1806.x.x loggar Intune Connector Service händelser i **Loggboken** (**Program- och tjänstloggar** > **Microsoft Intune Connector**). Använd dessa händelser till att felsöka eventuella problem med konfigurationen av Intune-anslutningsappen. Händelserna loggar lyckade och misslyckade åtgärder, samt diagnostikkoder som hjälper IT-avdelningen med felsökningen.

### <a name="event-ids-and-descriptions"></a>Händelse-id:n och beskrivningar

> [!NOTE]
> Mer information om relaterade diagnostiska koder för varje händelse finns i tabellen **Diagnostikkoder** (i den här artikeln).

| Händelse-ID      | Händelsenamn    | Händelsebeskrivning | Relaterade diagnostikkoder |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Anslutningstjänsten startade | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Anslutningstjänsten stoppade | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Anslutningsappens registreringscertifikat förnyades | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Det gick inte att förnya anslutningsappens registreringscertifikat. Installera om anslutningsappen. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Det gick inte att hämta anslutningsappens registreringscertifikat från registret. Granska händelseinformationen för tumavtrycket för certifikatet som rör denna händelse. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Kontrollera den diagnostiska information i händelsedetaljerna. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Ett PKCS-certifikat har utfärdats. Du hittar enhets-id, användar-id, certifikatutfärdarnamn, namnet på certifikatmallen samt certifikatavtrycket för händelsen i händelsedetaljerna. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Det gick inte att utfärda ett PKCS-certifikat. Du hittar enhets-id, användar-id, certifikatutfärdarnamn, namnet på certifikatmallen samt certifikatavtrycket för händelsen i händelsedetaljerna. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Certifikatet återkallades. Du hittar enhets-id, användar-id, certifikatutfärdarnamn och serienumret för certifikatet som gäller händelsen i händelsedetaljerna. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Det gick inte att återkalla certifikatet. Du hittar enhets-id, användar-id, certifikatutfärdarnamn och serienumret för certifikatet som gäller händelsen i händelsedetaljerna. Mer information finns i NDES SVC-loggarna.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Laddade upp certifikatets förfrågans- eller återkallandeinformation. Uppladdningsinformationen står i händelsedetaljerna. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Det gick inte att ladda upp certifikatets förfrågans- eller återkallandeinformation. Granska händelsedetaljerna > Uppladdningstillstånd för att fastställa tidpunkten för felet.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Laddade ned en förfrågan om att signera ett certifikat, hämta ett klientcertifikat eller återkalla ett certifikat. Nedladdningsinformationen står i händelsedetaljerna.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Det gick inte att ladda ned en förfrågan om att signera ett certifikat, hämta ett klientcertifikat eller återkalla ett certifikat. Nedladdningsinformationen står i händelsedetaljerna. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | Certifikatregistreringsplatsen verifierade en utmaning för klienten | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | Certifikatregistreringsplatsen slutfördes men avvisade begäran. Mer information finns i diagnostikkoden och i meddelandet. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Certifikatregistreringsplatsen kunde inte verifiera en utmaning för klienten. Mer information finns i diagnostikkoden och i meddelandet. Visa händelseinformation för det enhets-id som motsvarar utmaningen. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | Certifikatregistreringsplatsen slutförde aviseringsporocessen och har skickat certifikatet till klientenheten. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | Certifikatregistreringsplatsen kunde inte slutföra aviseringsprocessen. Mer information om förfrågningen finns i händelseinformationen. Kontrollera anslutningen mellan NDES-servern och certifikatutfärdaren. | 0x00000000, 0x0FFFFFFF |

### <a name="diagnostic-codes"></a>Diagnostikkoder

| Diagnostikkod | Diagnostiknamn | Diagnostikmeddelande |
| -------------   | -------------   | -------------      |
| 0x00000000 | Klart  | Klart |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | Certifikatutfärdaren är inte giltig eller kan inte nås. Kontrollera att certifikatutfärdaren är tillgänglig och att servern kan kommunicera med den. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | Symantec Client Auth-certifikatet gick inte att hitta i det lokala certifikatarkivet. Läs mer i artikeln [Installera Symantecs certifikat för registreringsauktorisering](https://docs.microsoft.com/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate).  |
| 0x00000402 | RevokeCert_AccessDenied  | Det angivna kontot har inte behörighet att återkalla ett certifikat från certifikatutfärdaren. Du ser utfärdande certifikatmyndighet i motsvarande fält i händelsemeddelandet.  |
| 0x00000403 | CertThumbprint_NotFound  | Det gick inte att hitta något certifikat som matchar dina indata. Registrera certifikatanslutningen och försök igen. |
| 0x00000404 | Certificate_NotFound  | Det gick inte att hitta något certifikat som matchar angivna indata. Registrera om certifikatanslutningen och försök igen. |
| 0x00000405 | Certificate_Expired  | Ett certifikat har gått ut. Registrera om certifikatanslutningen för att förnya certifikatet och försök igen. |
| 0x00000408 | CRPSCEPCert_NotFound  | Det gick inte att hitta CRP Encryption-certifikatet. Kontrollera att NDES och Intune-anslutningsappen har konfigurerats korrekt. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Det gick inte att hämta signeringscertifikatet. Kontrollera att Intune Connector-tjänsten är konfigurerad på rätt sätt och att Intune Connector-tjänsten körs. Kontrollera också att certifikatets hämtningshändelser utfördes utan fel. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Det gick inte att deserialisera förfrågningen om SCEP-utmaningen. Kontrollera att NDES och Intune-anslutningsappen har konfigurerats på rätt sätt. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Förfrågan nekades på grund av en certifikatutmaning som upphört att gälla. Klientenheten kan försöka igen när du har fått en ny utmaning från hanteringsservern. |
| 0x0FFFFFFFF | Unknown_Error  | Vi kan inte utföra din förfrågan eftersom det uppstod ett fel på serversidan. Försök igen. |

## <a name="next-steps"></a>Nästa steg

- [Använda PKCS-certifikat](certficates-pfx-configure.md) eller [utfärda PKCS-certifikat från en Symantec PKI-hanterad webbtjänst](certificates-symantec-configure.md)
- [Lägg till en tredjeparts-CA för att använda SCEP med Intune](certificate-authority-add-scep-overview.md)
- Mer hjälp finns i guiden [Troubleshooting SCEP certificate profile deployment in Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune) (Felsökning av SCEP-certifikatprofildistribution i Microsoft Intune).
