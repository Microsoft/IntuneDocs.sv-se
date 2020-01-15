---
title: Konfigurera infrastrukturen för att stödja SCEP-certifikatprofiler med Microsoft Intune – Azure | Microsoft Docs
description: Om du vill använda SCEP i Microsoft Intune konfigurerar du din lokala AD-domän, skapar en certifikatutfärdare, konfigurerar NDES-servern och installerar Intune Certificate Connector.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 501bfcbef0dd46f6021fc5db16cf3b9e2f2cd0c0
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885998"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Konfigurera infrastrukturen för att stödja SCEP med Intune

Intune stöder användning av Simple Certificate Enrollment Protocol (SCEP) för att [autentisera anslutningar till dina appar och företagsresurser](certificates-configure.md). SCEP använder certifikatutfärdarens (CA) certifikat för att skydda meddelandeutbytet för certifikatsigneringsförfrågan (CSR). När din infrastruktur stöder SCEP kan du använda *SCEP-certifikatprofiler* för Intune (en typ av enhetsprofil i Intune) för att distribuera certifikaten till dina enheter. Microsoft Intune Certificate Connector krävs för användning av SCEP-certifikatprofiler med Intune när du använder en certifikatutfärdare för Active Directory Certificate Services. Anslutningsprogrammet krävs inte vid användning av [certifikatutfärdare från tredje part](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration). 

Informationen i den här artikeln kan hjälpa dig att konfigurera din infrastruktur så att den stöder SCEP vid användning av Active Directory Certificate Services. När din infrastruktur har konfigurerats kan du [skapa och distribuera SCEP-certifikatprofiler](certificates-profile-scep.md) med Intune.

> [!TIP]
> Intune stöder även användning av [certifikat med kryptografistandard #12 med offentlig nyckel](certficates-pfx-configure.md).

## <a name="prerequisites-for-using-scep-for-certificates"></a>Krav för användning av SCEP för certifikat

Innan du fortsätter ska du ha [skapat och distribuerat en *betrodd certifikatprofil*](certificates-configure.md#export-the-trusted-root-ca-certificate) till enheter som kommer att använda SCEP-certifikatprofiler. SCEP-certifikatprofiler refererar direkt till den betrodda certifikatprofil som du använder för att etablera enheter med ett betrott rotcertifikatutfärdarcertifikat.

### <a name="servers-and-server-roles"></a>Servrar och serverroller

Följande lokala infrastruktur måste köras på servrar som är domänanslutna till din Active Directory, med undantag för webbprogramproxyservern.

- **Certifikatutfärdare** – använd en Microsoft Active Directory Certificate Services-certifikatutfärdare (CA) som körs på en Enterprise-version av Windows Server 2008 R2 med service pack 1 eller senare. Den version av Windows Server som du använder måste ha fortsatt support från Microsoft. En fristående certifikatutfärdare stöds inte. Mer information finns i [Installera certifikatutfärdaren](https://technet.microsoft.com/library/jj125375.aspx). Om din certifikatutfärdare kör Windows Server 2008 R2 SP1 måste du [installera snabbkorrigeringen från KB2483564](https://support.microsoft.com/kb/2483564/).

- **NDES-serverroll** – du måste konfigurera en NDES-serverroll (registreringstjänst för nätverksenheter) på Windows Server 2012 R2 eller senare. I ett senare avsnitt av den här artikeln vägleder vi dig genom [installationen av NDES](#set-up-ndes).

  - Den server som är värd för NDES måste vara domänansluten och i samma skog som din företagscertifikatutfärdare.
  - Du kan inte använda NDES som är installerad på den server som är värd för företagscertifikatutfärdaren.
  - Du installerar Microsoft Intune Certificate Connector på samma server som är värd för NDES.

  Mer information om NDES finns i [vägledningen för registreringstjänsten för nätverksenheter](https://technet.microsoft.com/library/hh831498.aspx) i Windows Server-dokumentationen samt [Använda en principmodul med registreringstjänsten för nätverksenheter](https://technet.microsoft.com/library/dn473016.aspx).

- **Microsoft Intune Certificate Connector** – Microsoft Intune Certificate Connector krävs för användning av SCEP-certifikatprofiler med Intune. Den här artikeln vägleder dig genom [installationen av det här anslutningsprogrammet](#install-the-intune-certificate-connector).

  Anslutningsprogrammet har stöd för FIPS-läge (Federal Information Processing Standard). FIPS krävs inte, men när det är aktiverat kan du utfärda och återkalla certifikat.
  - Anslutningsprogrammet måste köras på samma server som NDES-serverrollen, en server som kör Windows Server 2012 R2 eller senare.
  - .NET 4.5 Framework krävs av anslutningsprogrammet och ingår automatiskt i Windows Server 2012 R2.
  - Internet Explorer Enhanced Security Configuration [måste vara inaktiverat på den server som är värd för NDES](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) samt Microsoft Intune Certificate Connector.

Följande lokala infrastruktur är valfri:

Om du vill tillåta enheter på Internet att hämta certifikat behöver du publicera din NDES-URL externt till ditt företagsnätverk. Du kan använda antingen Azure-AD-programproxy, webbprogramproxyservern eller en annan omvänd proxy.

- **Azure Active Directory-programproxy** (valfritt) – du kan använda Azure AD-programproxy i stället för en dedikerad webbprogramproxy (WAP)-server för att publicera NDES-URL:en till Internet. Detta gör att både intranät- och Internetriktade enheter kan hämta certifikat. Mer information finns i [Så här tillhandahåller du säker fjärråtkomst till lokala program](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

- **Web Application Proxy-server** (valfritt) – använd en server som kör Windows Server 2012 R2 eller senare som en webbprogramproxyserver (WAP) för att publicera NDES-URL:en till Internet.  Detta gör att både intranät- och Internetriktade enheter kan hämta certifikat.

  Servern som är värd för WAP [måste installera en uppdatering](https://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) som aktiverar stöd för de långa URL:er som används av registreringstjänsten för nätverksenheter. Uppdateringen finns med i [samlad uppdatering för december 2014](https://support.microsoft.com/kb/3013769), eller individuellt från [KB3011135](https://support.microsoft.com/kb/3011135).

  WAP-servern måste ha ett SSL-certifikat som överensstämmer med det namn som publiceras på externa klienter och lita på det SSL-certifikat som används på den dator som är värd för NDES-tjänsten. De här certifikaten gör det möjligt för WAP-servern att avbryta SSL-anslutningen från klienter och skapa en ny SSL-anslutning till NDES-tjänsten.

  Mer information finns i [Planera certifikat för WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) och [allmän information om WAP-servrar](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="accounts"></a>Konton

- **NDES-tjänstkonto** – innan du konfigurerar NDES ska du identifiera ett domänanvändarkonto som ska användas som NDES-tjänstkontot. Du anger det här kontot när du konfigurerar mallar på den utfärdande certifikatutfärdaren innan du konfigurerar NDES.

  Det här kontot måste ha följande rättigheter på den server som är värd för NDES:

  - **Logga in lokalt**
  - **Logga in som en tjänst**
  - **Logga in som ett batchjobb**

  Mer information finns i [Skapa ett domänanvändarkonto för att fungera som NDES-tjänstkonto](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account).

- **Åtkomst till den dator som är värd för NDES-tjänsten** – du behöver ett domänanvändarkonto med behörighet att installera och konfigurera Windows-serverroller på den server där du installerar NDES.

- **Åtkomst till certifikatutfärdaren** – du behöver ett domänanvändarkonto som har behörighet att hantera din certifikatutfärdare.

### <a name="network-requirements"></a>Nätverkskrav

Vi rekommenderar att du publicerar NDES-tjänsten via en omvänd proxy, till exempel [Azure AD-programproxy, webbåtkomstproxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/) eller en proxy från tredje part. Om du inte använder en omvänd proxy ska du tillåta TCP-trafik på port 443 från alla värdar och IP-adresser på Internet till NDES-tjänsten.

Tillåt alla portar och protokoll som behövs för kommunikation mellan NDES-tjänsten och alla stödinfrastruktur i din miljö. Till exempel behöver den dator som är värd för NDES-tjänsten kommunicera med certifikatutfärdaren, DNS-servrar, domänkontrollanter och eventuellt andra tjänster eller servrar i din miljö, till exempel Configuration Manager.

### <a name="certificates-and-templates"></a>Certifikat och mallar

Följande certifikat och mallar används när du använder SCEP.

|Objekt    |Information    |
|----------|-----------|
|**SCEP-certifikatmall**         |En mall som du konfigurerar på den utfärdande certifikatutfärdaren för att uppfylla enheternas SCEP-begäranden. |
|**Certifikat för klientautentisering** |Begärt från din utfärdande certifikatutfärdare eller offentliga certifikatutfärdare.<br /> Du installerar det här certifikatet på den dator som är värd för NDES-tjänsten, och det används av Intune Certificate Connector.<br /> Om certifikatet har användningarna av *klientens* och *serverns* autentiseringsnycklar inställt på (**Förbättrad nyckelanvändning**) i den certifikatutfärdarmall som du använder för att utfärda det här certifikatet. Då kan du använda samma certifikat för server- och klientautentisering. |
|**Certifikat för serverautentisering** |Webbservercertifikat som begärs från din utfärdande certifikatutfärdare eller offentliga certifikatutfärdare.<br /> Du installerar och binder det här SSL-certifikatet i IIS på den dator som är värd för NDES.<br />Om certifikatet har användningarna av *klientens* och *serverns* autentiseringsnycklar inställt på (**Förbättrad nyckelanvändning**) i den certifikatutfärdarmall som du använder för att utfärda det här certifikatet. Då kan du använda samma certifikat för server- och klientautentisering. |
|**Certifikat från betrodd rotcertifikatutfärdare**       |För att kunna använda en SCEP-certifikatprofil måste enheter lita på din betrodda rotcertifikatutfärdare (CA). Använd en *betrodd certifikatprofil* i Intune för att etablera det betrodda rotcertifikatutfärdarcertifikatet till användare och enheter. <br/><br/> **-**  Använd ett enskilt betrott rotcertifikatutfärdarcertifikat per operativsystemplattform och associera det certifikatet med varje betrodd certifikatprofil som du skapar. <br /><br /> **-**  Du kan använda ytterligare certifikat från betrodda rotcertifikatutfärdarcertifikat när det behövs. Till exempel kan du använda ytterligare certifikat för att ge ett förtroende till en certifikatutfärdare som signerar serverautentiseringscertifikaten för dina Wi-Fi-åtkomstpunkter. Skapa ytterligare betrodda rotcertifikatutfärdarcertifikat för utfärdande certifikatutfärdare.  I den SCEP-certifikatprofil som du skapar i Intune ska du ange den betrodda rotcertifikatutfärdarprofilen för den utfärdande certifikatutfärdaren.<br/><br/> Information om den betrodda certifikatprofilen finns i [Exportera det betrodda rotcertifikatutfärdarcertifikatet](certificates-configure.md#export-the-trusted-root-ca-certificate) och [Skapa betrodda certifikatprofiler](certificates-configure.md#create-trusted-certificate-profiles) i *Använda certifikat för autentisering i Intune*. |

## <a name="configure-the-certification-authority"></a>Konfigurera certifikatutfärdaren

I följande avsnitt gör du detta:

- Konfigurera och publicera den mall som krävs för NDES
- Ange de behörigheter som krävs för återkallning av certifikat.

Följande avsnitt kräver kunskaper om Windows Server 2012 R2 eller senare samt om Active Directory Certificate Services (AD CS).

### <a name="access-your-issuing-ca"></a>Få åtkomst till din utfärdande certifikatutfärdare

1. Logga in på den utfärdande certifikatutfärdaren med ett domänkonto som har rätt behörighet för att hantera certifikatutfärdaren.

2. Öppna Certification Authority Microsoft Management Console (MMC). Använd **Kör** i ”certsrv.msc” eller gå till **Serverhanteraren**, klicka på **Verktyg** och klicka sedan på **Certifikatutfärdare**.

3. Välj noden **Certifikatmallar** och klicka på **Åtgärd** > **Hantera**.

### <a name="create-the-scep-certificate-template"></a>Skapa SCEP-certifikatmallen

1. Skapa en v2-certifikatmall (med Windows 2003-kompatibilitet) för användning som SCEP-certifikatmall. Du kan:

   - Använda snapin-modulen *Certifikatmallar* för att skapa en ny anpassad mall.
   - Kopiera en befintlig mall (till exempel mallen Användare) och sedan uppdatera kopian för användning som NDES-mall.

2. Konfigurera följande inställningar på de angivna flikarna i mallen:

   - **Allmänt**:

     - Avmarkera **Publicera certifikat i Active Directory**.
     - Ange ett eget **visningsnamn för mallen** så att du kan identifiera mallen senare.

   - **Ämnesnamn**:

     - Välj **Anges i begäran**. Säkerhet framtvingas av Intune-principmodulen för NDES.

       ![Mall, fliken för ämnesrad](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)

   - **Tillägg**:

     - Se till att **Beskrivning av programprinciper** inkluderar **Klientautentisering**.

       > [!IMPORTANT]
       > Lägg endast till de programprinciper som du behöver. Bekräfta dina val med säkerhetsadministratörerna.

     - För iOS- och macOS-certifikatmallar redigerar du även **Nyckelanvändning** och ser till att **Signaturen är bevis för ursprung** inte är markerat.

     ![Mall, fliken för tillägg](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **Säkerhet**:

     - Lägg till **NDES-tjänstkontot**. Detta konto kräver behörigheter att **Läsa** och **Registrera** i den här mallen.

     - Lägg till ytterligare konton för Intune-administratörer som kommer att skapa SCEP-profiler. Dessa konton kräver behörighet att **Läsa** i mallen för att de här administratörerna ska kunna bläddra till mallen när de skapar SCEP-profiler.

     ![Mall, fliken för säkerhet](./media/certificates-scep-configure/scep-ndes-security.jpg)

   - **Hantering av begäranden**:

     Följande bild är ett exempel. Din konfiguration kan vara annorlunda.  

     ![Mall, fliken för hantering av begäran](./media/certificates-scep-configure/scep-ndes-request-handling.png)

   - **Krav för utfärdande**:

     Följande bild är ett exempel. Din konfiguration kan vara annorlunda.

     ![Mall, fliken för utfärdandekrav](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)

3. Spara certifikatmallen.

### <a name="create-the-client-certificate-template"></a>Skapa klientcertifikatmallen

Intune Certificate Connector kräver ett certifikat där förbättrad nyckelanvändning och certifikatmottagarens namn för *Klientautentisering* är samma som FQDN för den dator där anslutningsprogrammet är installerat. En mall med följande egenskaper krävs:

- **Tillägg** > **Programprinciper** måste innehålla **Klientautentisering**
- **Certifikatmottagarens namn** > **Anges i begäran**.

Om du redan har en mall som innehåller dessa egenskaper kan du återanvända den. Annars skapar du en ny mall genom att antingen duplicera en befintlig eller skapa en anpassad mall.

### <a name="create-the-server-certificate-template"></a>Skapa servercertifikatmallen

Kommunikation mellan hanterade enheter och IIS på NDES-servern använder HTTPS, vilket kräver att ett certifikat används. Du kan använda certifikatmallen **Webbserver** för att utfärda det här certifikatet. Eller om du föredrar att ha en dedikerad mall så krävs följande egenskaper:

- **Tillägg** > **Programprinciper** måste innehålla **Serverautentisering**
- **Certifikatmottagarens namn** > **Anges i begäran**.

> [!NOTE]
> Om du har ett certifikat som uppfyller båda kraven från klient- och servercertifikatmallarna kan du använda ett enskilt certifikat för både IIS och Intune Certificate Connector.

### <a name="grant-permissions-for-certificate-revocation"></a>Bevilja behörighet för certifikatåterkallande

För att Intune ska kunna återkalla certifikat som inte längre krävs måste du bevilja behörigheter i certifikatutfärdaren.

I Intune Certificate Connector kan du antingen använda NDES-serverns **systemkonto** eller ett specifikt konto såsom **NDES-tjänstkontot**.

1. I konsolen för certifikatutfärdare högerklickar du på certifikatutfärdarens namn och väljer **Egenskaper**.

2. På fliken **Säkerhet** klickar du på **Lägg till**.

3. Bevilja behörigheten **Utfärda och hantera certifikat**:

   - Om du väljer att använda NDES-serverns **systemkonto** anger du behörigheterna till NDES-servern.
   - Om du väljer att använda **NDES-tjänstkontot** anger du behörigheter för det kontot i stället.

### <a name="modify-the-validity-period-of-the-certificate-template"></a>Ändra giltighetsperioden för certifikatmallen

Det är valfritt att ändra giltighetsperioden för certifikatmallen.  

När du har [skapat SCEP-certifikatmallen](#create-the-scep-certificate-template) kan du redigera mallen för att granska **giltighetsperioden** på fliken **Allmänt**.

Som standard använder Intune värdet som konfigurerats i mallen. Du kan dock konfigurera certifikatutfärdaren så att den tillåter att beställaren anger ett annat värde, och det värdet kan anges från Intune-konsolen.

> [!IMPORTANT]
> För iOS och macOS ska du alltid använda ett värde som anges i mallen.

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Så konfigurerar du ett värde som kan anges i Intune-konsolen

1. Kör följande kommandon hos certifikatutfärdaren:

   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   -**net stop certsvc**
   -**net start certsvc**

2. På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatutfärdaren för att publicera certifikatmallen. Välj noden **Certifikatmallar** följt av **Åtgärd** > **Ny** > **Certifikatmall som ska utfärdas**. Välj sedan den certifikatmall som du skapade i föregående avsnitt.

3. Kontrollera att mallen publicerats genom att titta på den i mappen **Certifikatmallar**.

## <a name="set-up-ndes"></a>Konfigurera NDES

Följande procedurer kan hjälpa dig att konfigurera registreringstjänsten för nätverksenheter (NDES) för användning med Intune. Mer information om NDES finns i [vägledningen för registreringstjänsten för nätverksenheter](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11)).

### <a name="install-the-ndes-service"></a>Installera NDES-tjänsten

1. På den server som kommer att vara värd för din NDES-tjänst loggar du in som **företagsadministratör** och använder sedan [guiden Lägg till roller och funktioner](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) för att installera NDES:

   1. I guiden väljer du **Active Directory-certifikattjänster** för att få tillgång till AD CS-rolltjänsterna. Välj **Registreringstjänsten för nätverksenheter**, avmarkera **Certifikatutfärdare**och slutför sedan guiden.

      > [!TIP]
      > I **Installationsförlopp** väljer du inte **Stäng**. Markera i stället länken **Konfigurera Active Directory-certifikattjänster på målservern**. Guiden **AD CS-konfiguration** öppnas, som du använder för nästa procedur i den här artikeln, *Konfigurera NDES-tjänsten*. När AD CS-konfiguration öppnats stänger du guiden Lägg till roller och funktioner.

   2. När NDES läggs till på servern installerar guiden även IIS. Bekräfta att IIS har följande konfigurationer:

      - **Webbserver** > **Säkerhet** > **Begäransfiltrering**
      - **Webbserver** > **Programutveckling** > **ASP.NET 3.5**

        Om du installerar ASP.NET 3.5 installeras även .NET Framework 3.5. När du installerar .NET Framework 3.5, installera både kärnfunktionen **.NET Framework 3.5** och **HTTP-aktivering**.

      - **Webbserver** > **Programutveckling** > **ASP.NET 4.5**

        Om du installerar ASP.NET 4.5 installeras även .NET Framework 4.5. När du installerar .NET Framework 4.5 installerar du kärnfunktionen **.NET Framework 4.5**, **ASP.NET 4.5** och funktionen **WCF-tjänster** > **HTTP-aktivering**.

      - **Hanteringsverktyg** > **IIS 6-kompatibilitetshantering** > **IIS 6-metabaskompatibilitet**
      - **Hanteringsverktyg** > **IIS 6-kompatibilitetshantering** > **IIS 6 WMI-kompatibilitet**
      - På servern lägger du till NDES-tjänstkontot som medlem i den lokala gruppen **IIS_IUSR**.

2. På den dator som är värd för NDES-tjänsten kör du följande kommando i en upphöjd kommandotolk. Följande kommando anger SPN för NDES-tjänstkontot:

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`

   Om den dator som är värd för NDES-tjänsten till exempel har namnet **Server01**, din domän är **Contoso.com** och tjänstkontot är **NDESService** så använder du:

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>Konfigurera NDES-tjänsten

1. På den dator som är värd för NDES-tjänsten öppnar du guiden **AD CS-konfiguration** och gör följande uppdateringar:

   > [!TIP]
   > Om du fortsätter från den senaste proceduren och klickade på länken **Konfigurera Active Directory Certificate Services på målservern** bör den här guiden redan vara öppen. Annars öppnar du Serverhanteraren för att komma åt konfigurationen efter distribution för Active Directory-certifikattjänster.

   - I **Rolltjänster** väljer du **registreringstjänsten för nätverksenheter**.
   - Under **Tjänstkonto för NDES** anger du NDES-tjänstkontot.
   - Under **Certifikatutfärdare för NDES** klickar du på **Välj** väljer sedan den utfärdande certifikatutfärdare där du konfigurerade certifikatmallen.
   - Under **Kryptografi för NDES** ställer du in nyckellängden enligt företagets krav.
   - Under **Bekräftelse** väljer du **Konfigurera** för att slutföra guiden.

2. När guiden är slutförd uppdaterar du följande registernyckel på den dator som är värd för NDES-tjänsten:

   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

   Du uppdaterar den här nyckeln genom att identifiera certifikatmallarnas **Syfte** (som finns på fliken **Hantering av begäranden**). Sedan uppdaterar du den motsvarande posten i registret genom att ersätta den befintliga informationen med namnet på den certifikatmall (inte mallens visningsnamn) som du angav när du [skapade certifikatmallen](#create-the-scep-certificate-template).

   I följande tabell visas certifikatmallens syfte för värdena i registret:

   |Certifikatmallens syfte (på fliken Hantering av begäranden)|Registervärde som redigeras|Värde som visas i Intune-administratörskonsolen för SCEP-profilen|
   |------------------------|-------------------------|---|
   |Signatur               |SignatureTemplate        |Digital signatur |
   |Kryptering              |EncryptionTemplate       |Nyckelchiffrering  |
   |Signatur och kryptering|GeneralPurposeTemplate   |Nyckelchiffrering <br/> Digital signatur |

   Exempel: Om syftet för certifikatmallen är **Kryptering**, ersätter du värdet **EncryptionTemplate** värdet med namnet på certifikatmallen.

3. Konfigurera filtrering av IIS-begäranden för att lägga till stöd i IIS för långa URL:er (frågor) som NDES-tjänsten tar emot.

   1. I IIS-hanteraren väljer du **Standardwebbplats** > **Begärandefiltrering** > **Redigera funktionsinställning** för att öppna sidan **Redigera inställningar för begärandefiltrering**.

   2. Konfigurera följande inställningar:

      - **Maximal URL-längd (byte)** = 65534
      - **Maximal frågesträng (byte)** = 65534

   3. Spara konfigurationen och stäng ISS-hanteraren genom att välja **OK**.

   4. Verifiera konfigurationen genom att titta på följande registernyckel för att bekräfta att den har de angivna värdena:

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

      Följande värden anges som DWORD-poster:

      - Namn: **MaxFieldLength**, med decimalvärdet **65534**
      - Namn: **MaxRequestBytes**, med decimalvärdet **65534**

4. Starta om den server som är värd för NDES-tjänsten. Använd inte **iisreset** eftersom det inte slutför de ändringar som krävs.

5. Bläddra till *http://* Server_FQDN */certsrv/mscep/mscep.dll*. Du bör se en NDES-sida som ser ut ungefär som följande bild:

   ![Testa NDES](./media/certificates-scep-configure/scep-ndes-url.png)

   Om webbadressen returnerar **503 Tjänsten ej tillgänglig** kontrollerar du datorns loggbok. Det här felet uppstår vanligtvis när programpoolen stoppas på grund av att [en behörighet saknas för NDES-tjänstkontot](#accounts).
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>Installera och binda certifikat på den server som är värd för NDES

> [!TIP]
> I följande procedur kan du använda ett enda certifikat för både *serverautentisering* och *klientautentisering* när certifikatet konfigureras för att uppfylla kriterierna för båda användningarna. Kriterierna för varje användning beskrivs i steg 1 och 3 i följande procedur.

1. Begär ett certifikat för **serverautentisering** från din interna certifikatutfärdare eller offentliga certifikatutfärdare, och installera därefter certifikatet på servern.

   Om servern använder ett externt och internt namn för en enda nätverksadress måste certifikatet för serverautentisering ha:

   - Ett **Ämnesnamn** med ett externt offentligt servernamn.
   - Ett **Alternativt ämnesnamn** som innehåller det interna servernamnet.

2. Binda serverautentiseringscertifikatet i IIS:

   1. När du har installerat certifikatet för serverautentisering öppnar du **IIS-hanteraren** och väljer **standardwebbplatsen**. I fönstret **Åtgärder** väljer du **Bindningar**.

   1. Välj **Lägg till**, ställ in **Typ** till **https**och kontrollera att porten är **443**.
   
   1. För **SSL-certifikat**anger du certifikatet för serverautentiserning.

3. På NDES-servern: begär och installera ett certifikat för **klientautentisering** från den interna certifikatutfärdaren eller en offentlig certifikatutfärdare.

   Certifikatet för klientautentisering måste ha följande egenskaper:

   - **Förbättrad nyckelanvändning**: Värdet måste innehålla **Klientautentisering**.
   - **Ämnesnamn**: Värdet måste vara samma som DNS-namnet på servern där du installerar certifikatet (NDES-servern).

4. Den server som är värd för NDES-tjänsten är nu redo att stödja Intune Certificate Connector.

## <a name="install-the-intune-certificate-connector"></a>Installera Intune Certificate Connector

Microsoft Intune Certificate Connector installeras på den server som kör din NDES-tjänst. Det finns inte stöd för användning av NDES eller Intune Certificate Connector på samma server som din utfärdande certifikatutfärdare (CA).

### <a name="to-install-the-certificate-connector"></a>Så här installerar du Certifikatanslutningsapp

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Administration av klientorganisation** > **Anslutning och token** > **Certifikatanslutningsprogram** > **Lägg till**.

3. Ladda ned och spara anslutningsappen för SCEP-filen. Spara den på en plats som är tillgänglig från servern där du ska installera anslutningsappen.

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. När nedladdningen är klar går du till den server som är värd för rollen Network Device Enrollment Service (NDES) (Registreringstjänst för nätverksenheter). Efter det:

   1. Kontrollera att .NET 4.5 Framework är installerat, eftersom det krävs av Intune Certificate Connector. .NET 4.5 Framework ingår automatiskt i Windows Server 2012 R2 och senare versioner.

   2. Kör installationsprogrammet (**NDESConnectorSetup.exe**). Installationsprogrammet installerar även policymodulen för NDES och IIS-certifikatregistreringsplatsens (CRP) webbtjänst. CRP-webbtjänsten, *CertificateRegistrationSvc*, körs som ett program i IIS.

      När du installerar NDES för fristående Intune installeras CRP-tjänsten automatiskt med certifikatanslutningsappen.

5. När du tillfrågas om klientcertifikatet för certifikatanslutningsappen väljer du **Välj** och väljer det certifikat för **klientautentisering** som du installerade på NDES-servern under steg 3 i proceduren [Installera och binda certifikat på den server som är värd för NDES](#install-and-bind-certificates-on-the-server-that-hosts-ndes) tidigare i den här artikeln.

   När du har valt certifikatet för klientautentisering tas du tillbaka till ytan **Klientcertifikat för Microsoft Intune Certifikat Connector**. Även om det certifikat som du valde inte visas väljer du **Nästa** för att visa egenskaperna för certifikatet. Välj **Nästa** och sedan **Installera**.

6. När guiden slutförts väljer du **Starta användargränssnittet för Certificate Connector** innan du stänger guiden.

   Om du stänger guiden innan du startar användargränssnittet för Certifikatanslutningsapp kan du öppna det genom att skriva följande kommando:

   *<install_Path>\NDESConnectorUI\NDESConnectorUI.exe*

7. I användargränssnittet för **certifikat connectorn** :

   1. Välj **Logga in** och ange autentiseringsuppgifter för en tjänstadministratör i Intune eller för en klientadministratör med behörighet för global administration.

   2. Det konto som du använder måste tilldelas en giltig Intune-licens.

   3. När du har loggat in laddar Intune Certificate Connector ned ett certifikat från Intune. Det här certifikatet används för autentisering mellan anslutningsappen och Intune. Om det konto som du använde inte har någon Intune-licens kan inte anslutningsprogrammet (NDESConnectorUI.exe) hämta certifikatet från Intune.  

      Om din organisation använder en proxyserver och proxyn krävs för att NDES-servern ska få åtkomst till Internet, välj **Använd proxyserver**. Ange sedan proxyservernamn, port och autentiseringsuppgifter för att ansluta.

   4. Välj fliken **Avancerat** och ange autentiseringsuppgifter för ett konto som har behörigheten **Utfärda och hantera certifikat** på den utfärdande certifikatutfärdaren. **Spara** ändringarna.  

    5. Nu kan du stänga användargränssnittet för Certifikat Connectorn.

8. Öppna en kommandotolk, skriv **services.msc** och tryck på **retur**. Högerklicka på **Intune-anslutningstjänsten** > **Starta om**.

Kontrollera att tjänsten körs genom att öppna en webbläsare och ange följande URL. Det bör returnera ett **403**-fel: `https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> Intune Certificate Connector har stöd för TLS 1.2. Om den server som är värd för anslutningsprogrammet har stöd för TLS 1.2 används TLS 1.2. Om servern inte stödjer TLS 1.2 används TLS 1.1. För närvarande används TLS 1.1 för autentisering mellan enheter och servern.

## <a name="next-steps"></a>Nästa steg

[Skapa en SCEP-certifikatprofil](certificates-profile-scep.md)  
[Felsöka problem med Intune Certificate Connector](troubleshoot-certificate-connector-events.md)
