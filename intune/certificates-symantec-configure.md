---
title: Utfärda Symantec PKCS-certifikat med Microsoft Intune
titlesuffix: ''
description: Installera och konfigurera Intune Certificate Connector för att utfärda PKCS-certifikat från webbtjänsten Symantec PKI Manager till Intune-hanterade enheter.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1fbb0ccd21ff15cf86656d7badf08002f1e42bb3
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/17/2018
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>Konfigurera Intune Certificate Connector för webbtjänsten Symantec PKI Manager

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Den här artikeln visar hur du installerar och konfigurerar Intune Certificate Connector att utfärda PKCS-certifikat från webbtjänsten Symantec PKI Manager till Intune-hanterade enheter.

Webbtjänsten Symantec PKI Manager kallas Symantec CA i den här artikeln. Om du redan har konfigurerat Intune Certificate Connector för att utfärda PKCS-certifikat och SCEP-certifikat från Microsofts Certification Authority (CA), kan du använda samma anslutningsapp för att konfigurera och utfärda PKCS-certifikat från en Symantec CA. I det här fallet kan Intune Certificate Connector utfärda följande certifikat:

* PKCS-certifikat från en Microsoft CA
* SCEP-certifikat från en Microsoft CA
* PKCS-certifikat från en Symantec CA

Om du vill använda Intune Certificate Connector för Microsoft CA och Symantec CA så måste du först slutföra konfigurationen för Intune Certificate Connector för Microsoft CA och sedan följa de här stegen för att konfigurera den för Symantec CA:n.  Mer information om hur du konfigurerar Intune Certificate Connector för en Microsoft-certifikatutfärdare finns i [Så här konfigurerar du certifikat i Microsoft Intune](certificates-configure.md).

## <a name="prepare-to-install-intune-certificate-connector"></a>Förbered installation av Intune Certificate Connector

Om du redan använder Intune Certificate Connector för en befintlig Microsoft CA och vill lägga till stöd för Symantec CA, hoppar du över det här steget och fortsätter med stegen efter att du installerat den senaste Intune Certificate Connector från Intune Admin-portalen. Det här steget krävs bara när du vill använda Intune Certificate Connector för en fristående Symantec CA.

1. Välj någon av versionerna av Windows-operativsystemet från följande lista och installera det på en dator:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Skapa en användare med administratörsbehörighet och använd den för att slutföra följande steg.

3. Uppdatera för de senaste Windows-uppdateringarna och installera dem vid behov.

   > [!IMPORTANT]
   > Starta om datorn när du har installerat Windows-uppdateringarna.

4. Installera .NET Framework 3.5:

    a. Öppna **Kontrollpanelen** > **program och funktioner** > **aktivera eller inaktivera Windows-funktioner**

    b. Välj **.NET Framework 3.5** och installera det.

## <a name="install-the-symantec-registration-authorization-certificate"></a>Installera Symantecs certifikat för registreringsauktorisering

Använd följande steg för att få certifikatet för registreringsauktorisering (RA) från Symantec CA:n. Du måste ha en aktiv prenumeration på Symantec CA:n för att få RA-certifikatet.

1. Spara följande kodavsnitt som en fil med namnet **certreq.ini** och uppdatera efter behov (exempel: *ämnesnamnet i CN-format*).

   ```
    [Version] 
    Signature="$Windows NT$" 

    [NewRequest] 
    ;Change to your,country code, company name and common name 
    Subject = "Subject Name in CN format"

    KeySpec = 1 
    KeyLength = 2048 
    Exportable = TRUE 
    MachineKeySet = TRUE 
    SMIME = False 
    PrivateKeyArchive = FALSE 
    UserProtected = FALSE 
    UseExistingKeySet = FALSE 
    ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
    ProviderType = 12 
    RequestType = PKCS10 
    KeyUsage = 0xa0 

    [EnhancedKeyUsageExtension] 
    OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication

    ;----------------------------------------------- 
   ```

2. Öppna en upphöjd kommandotolk och skapa CSR-innehåll med följande kommando:

   `Certreq.exe -new certreq.ini request.csr`

3. Öppna filen request.csr i anteckningar och kopiera CSR-innehållet till följande format:

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. Logga in på Symantec CA:n och gå till **hämta ett RA-certifikat** från uppgifterna.

   a. Ange CSR-innehållet från steg 3 i den avsedda textrutan.

   b. Ange det egna certifikatnamnet i den avsedda textrutan.

   c. Klicka på **Fortsätt**.

      Då visas en nedladdningsbar länk för RA-certifikatet.

   d. Hämta RA-certifikatet till den lokala datorn.

5. Importera RA-certifikatet till Windows-certifikatarkivet:

    a. Öppna en MMC-konsol.

    b. Klicka på **fil** > **lägg till eller ta bort snapin-moduler** > **certifikat** > och klicka sedan på **lägg till**.

    c. Välj **datorkonto** > och klicka sedan på **nästa**.

    d. Välj **lokal dator** > och klicka på **slutför**.

    e. Klicka på **OK** i fönstret **lägg till eller ta bort snapin-moduler**. Expandera **certifikat (lokal dator)** > **personliga** > **certifikat**.

    f. Högerklicka på noden **certifikat** och välj **alla aktiviteter** > **importera**.

    g. Välj platsen för RA-certifikatet som du hämtade från Symantec CA:n och klicka på **nästa**.

    h. Välj **personligt certifikatarkiv** och sedan **nästa**.

    i. Klicka på **Slutför**. Det importerar RA-certifikatet till den lokala datorns personliga arkiv tillsammans med dess privata nyckel.  

6. Exportera och importera privat nyckelcertifikat:

    a. Expandera **certifikat (lokal dator)** > **personliga** > **certifikat**.

    b. Välj det certifikat som importerades i föregående steg.

    c. Högerklicka på certifikatet och välj **alla aktiviteter** > **exportera**.

    d. Klicka på **nästa** och ange lösenordet.

    e. Välj plats att exportera till och klicka på **slutför**.

    f. Följ samma procedur i steg 5 för att importera privata nyckelcertifikat till det personliga arkivet för den lokala datorn.

7. Kopiera tumavtrycket för RA-certifikatet utan blanksteg.  Följande är ett exempel på ett tumavtryck:

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > Om det uppstår några problem med att hämta RA-certifikatet från Symantec CA:n, kontaktar du Symantecs kundsupport.

## <a name="install-intune-certificate-connector"></a>Installera Intune Certificate Connector

Om du redan använder den senaste Intune Certificate Connector för en befintlig Microsoft CA och vill lägga till stöd för en Symantec CA, hoppar du över detta steg. Annars hämtar du den senaste Intune Certificate Connector från Intune-administrationsportalen och följer de här anvisningarna.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enhetskonfiguration** i **Intune**-fönstret.
4. Välj **Certifikatutfärdare** i fönstret **Enhetskonfiguration**.
5. Klicka på **Lägg till** och välj **Download the connector file** (Ladda ned anslutningsfil). Spara den på en plats där du kan komma åt den från den server där du kommer att installera den. 
3. Kör NDESConnectorSetup.exe med upphöjda behörigheter.

    a. På sidan **installationsalternativ** väljer du **PFX-distribution** som visas i följande skärmbild.  Slutför konfigurationen med standardalternativ.

   > [!IMPORTANT]
   > Om du vill konfigurera Intune Certificate Connector till att utfärda certifikat från en Microsoft CA och en Symantec CA, väljer du **SCEP- och PFX-profildistribution**. Slutför konfigurationen med standardalternativ.

   ![InstallConnector][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>Konfigurera Microsoft Intune Certificate Connector

Intune Certificate Connector installeras på `%ProgramFiles%\Microsoft Intune` som standard.

1. Öppna %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config-filen i anteckningar.

    a. Uppdatera värdet för RACertThumbprint-nyckeln med certifikatets tumavtrycksvärde som du kopierade i föregående avsnitt.  Följande är ett exempel:

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. Spara och stäng filen.

2. Öppna services.msc.

    a. Välj **Intune Connector-tjänsten**.

    b. Stoppa tjänsten och starta den igen.

    c. Stäng tjänster-fönstret.

## <a name="setup-the-intune-administrator-account"></a>Konfigurera Intune-administratörskontot

Om du redan använder Intune Certificate Connector för en befintlig Microsoft CA och vill lägga till stöd för en Symantec CA, hoppar du över detta steg och fortsätter med de efterföljande. 

1. Starta användargränssnittet för NDES Connector från ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe `

    a. Klicka på fliken **registrering** och klicka sedan på **logga In**.

    b. Ange dina autentiseringsuppgifter som Intune-klientadministratör i de avsedda textrutorna.

    c. Klicka på **Logga in**.  Det visas en bekräftelseruta som säger **registrerades** som det visas i följande skärmbild.
2. Stäng användargränssnittet för NDES Connector.

![ConfigureConnector][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>Skapa en betrodd certifikatprofil

PKCS-certifikaten som distribueras för Intune-hanterade enheter måste vara härledda med ett betrott rotcertifikat. Det gör att du måste skapa en Intune-betrodd certifikatprofil med rotcertifikatet från Symantec CA:n.

1. Hämta ett betrott rotcertifikat från Symantec CA:n:

    a. Logga in på administrationsportalen för Symantec CA:n.

    b. Klicka på Hantera certifikatutfärdare från aktiviteter:

    c. Välja rätt CA från listan.

    d. Klicka på hämta rotcertifikat för att hämta det betrodda rotcertifikatet.

2. Skapa en betrodd certifikatprofil i Intune-administrationsportalen:

    a. Logga in på [Azure-portalen](https://portal.azure.com) med dina autentiseringsuppgifter som Intune-klientadministratör och sök efter Intune-resurser.

    b. Skapa en betrodd certifikatprofil från **Microsoft Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil**.

    c. Ange nödvändig information i fälten **namn** och **beskrivning** och välj sedan målplattform. 

    d. Välj den betrodda certifikatprofilen från listmenyn profiltyp.

    e. Överför det betrodda rotcertifikatet som du fick från Symantec CA:n i föregående steg.

    f. Slutför de kvarvarande stegen för att skapa profilen. 

    g. Klicka på **tilldelningar** och välj lämplig grupp.  Minst en användare eller enhet måste vara en del av den tilldelade gruppen.

## <a name="get-the-certificate-profile-oid"></a>Hämta certifikatprofilens OID

Certifikatprofil-OID:n är associerad med en certifikatprofilsmall i Symantec CA:n.  Om du vill skapa en PKCS-certifikatprofil i Intune-administrationsportalen, måste du ange namnet på certifikatmallen i form av ett certifikatprofil-OID som är kopplat till en certifikatmall i Symantec CA:n.

1. Logga in på administrationsportalen för Symantec CA:n.
2. Klicka på hantera certifikatprofiler.
3. Välj den certifikatprofil som du vill använda.
4. Kopiera certifikatprofilens OID. Den liknar följande exempel:

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > Om det uppstår några problem med att hämta certifikatprofilens OID, kontaktar du Symantecs kundtjänst.

## <a name="create-a-pkcs-certificate-profile"></a>Skapa en PKCS-certifikatprofil

1. Logga in på [Azure-portalen](https://portal.azure.com) med dina autentiseringsuppgifter som Intune-klientadministratör och sök efter Intune-resurser.
2. Skapa en PKCS-certifikatprofil från **Microsoft Intune** > **Enhetskonfiguration > Profiler** > **Skapa profil**.

    a. Ange nödvändig information i fälten **namn** och **beskrivning** och välj sedan målplattform.

    b. Välj **PKCS-certifikatprofilen** från listmenyn **profiltyp**.  

    c. Slutför de återstående stegen för att skapa profilen.

   ![ConfigureProfile][ConfigureProfile]

   > [!IMPORTANT]
   > Följande parametrar för PKCS-certifikatprofilen måste konfigureras med angivna värden i följande tabellen som det visas i skärmbilden för att utfärda PKCS-certifikat via Intune Certificate Connector från Symantec CA:n. 

    |PKCS-certifikatparameter | Värde | Description |
    | --- | --- | --- |
    | Certifikatutfärdare | pki-ws.symauth.com | Det här värdet måste vara bastjänst-FQDN för Symantec-certifikatutfärdaren utan avslutande snedstreck.  Om du inte är säker på om det här är rätt bastjänst-FQDN för din Symantec CA-prenumeration så kan du kontakta Symantecs kundsupport. <br><br> Om detta FQDN är felaktigt så utfärdar inte Intune Certificate Connector PKCS-certifikat från Symantec-certifikatutfärdaren.| 
    | Namn på certifikatutfärdare | Symantec | Det här värdet måste vara strängen **Symantec**. <br><br> Om det här värdet ändras, kommer Intune Certificate Connector inte att utfärda PKCS-certifikat från Symantec CA:n.|
    | Certifikatmallens namn | Certifikatprofil-OID från Symantec CA:n. <br><br> Ex: `2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| Det här värdet måste vara ett certifikatprofils-OID som hämtats i det föregående avsnitt från Symantec CA-certifikatprofilmallen. <br><br> Om Intune Certificate Connector inte kan hitta en certifikatmall som är associerad med det här certifikatprofils-OID:n i Symantec CA:n, utfärdar den inga PKCS-certifikat från Symantec CA:n.|

   > [!NOTE]
   > PKCS-certifikatprofiler för Windows-plattformar behöver inte associeras med en betrodd certifikatprofil. Men det krävs för icke-Windows-plattformprofiler, till exempel Android.

3. Klicka på **tilldelningar** och välj lämplig grupp.  Minst en användare eller enhet måste vara en del av den tilldelade gruppen.
 
När du har slutfört föregående steg, utfärdar Intune Certificate Connector PKCS-certifikat från Symantec CA:n till Intune-hanterade enheter i den tilldelade gruppen. De här certifikaten blir tillgängliga i det personliga arkivet för den aktuella användarens certifikatarkiv på den Intune-hanterade enheten.

### <a name="pkcs-certificate-profile-supported-attributes"></a>Attribut som stöds av PKCS-certifikatprofilen

|Attribut | Format som stöds av Intune | Format som stöds av Symantec Cloud CA | Result |
| --- | --- | --- | --- |
| Ämnesnamn |Intune stöder enbart ämnesnamnet i följande tre format: <br><br> 1. Tilltalsnamn <br> 2. Eget namn inkluderar e-post <br> 3. Eget namn som e-post <br><br> Följande är ett exempel: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | Symantec-CA stöder ytterligare attribut.  Om du vill välja ytterligare attribut, måste de ha definierats med fasta värden i Symantec-certifikatprofilmallen.| Vi använder egna namn eller e-post från PKCS-certifikatbegäran. <br><br> Alla matchningsfel i attributval mellan Intune-certifikatprofilen och Symantec-certifikatprofilmallen resulterar i att inga certifikat utfärdas av Symantec CA:n.|
| SAN | Intune stöder endast följande SAN fältvärden: <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName (kodad värde) | Symantec Cloud CA:n har också stöd för dessa parametrar. Om du vill välja ytterligare attribut, måste de ha definierats med fasta värden i Symantec-certifikatprofilmallen. <br><br> AltNameTypeEmail: Om den här typen inte finns i SAN, används värdet från AltNameTypeUpn.  Om AltNameTypeUpn inte heller hittades i SAN, används värdet från ämnesnamnet om det är i e-postformat.  Om det fortfarande inte hittas, kan inte Intune Certificate Connector utfärda certifikaten. <br><br> Ex: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn: Om den här typen inte finns i SAN, används värdet från AltNameTypeEmail. Om AltNameTypeEmail inte heller hittas i SAN, används värdet från ämnesnamnet om det är i e-postformat.  Om det fortfarande inte hittas, kan inte Intune Certificate Connector utfärda certifikaten.  <br><br> Ex: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName: Om den här typen inte finns i SAN, kan inte Intune Certificate Manager utfärda certifikaten. <br><br> Ex: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **Obs!** Värdet för det här fältet stöds bara i kodat format (hexadecimalt värde) av Symantec CA:n. Så för alla värden i det här fältet, konverterar Intune Certificate Connector det till base 64-kodat innan den skickar certifikatbegäran. **Intune Certificate Connector verifierar inte om det här värdet redan är kodat eller inte.** | Inga |

## <a name="troubleshooting"></a>Felsökning

Intune Certificate Connector-tjänstens loggar finns tillgängliga i `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` på NDES Connector-datorn. Öppna loggarna i [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) och sök efter undantag eller felmeddelanden.

| Problem/felmeddelande | Steg |
| --- | --- |
| Det går inte att logga in med Intune-klientadministratörskontot på användargränssnittet för NDES Connector | Detta kan hända när den lokala Certificate Connectorn inte är aktiverad i Intune-administrationsportalen. Du löser problemet genom att utföra följande steg: <br><br> Från Silver Light-gränssnittet: <br> 1. Logga in på [Intune-administratörsportalen](https://admin.manage.microsoft.com) <br> 2. Klicka på admin <br> 3. Välj hantering av mobila enheter > Certificate Connector <br> 4. Klicka på **konfigurera lokal Certificate Connector** <br> 5. Markera kryssrutan **aktivera Certificate Connector** <br> 6. Klicka på **OK**. <br><br>Eller <br><br> Från Azure-portalens användargränssnitt: <br> 1. Logga in på [Azure-portalen](https://portal.azure.com) <br> 2. Gå till Microsoft Intune <br> 3. Välj **enhetskonfiguration** > **certifikatutfärdare** <br> 4. Klicka på **Aktivera**. <br><br> När du har utfört de föregående stegen antingen från Silver Light-gränssnittet eller Azure-portalen, försöker du att logga in med samma Intune-klientadministratörskonto i användargränssnittet för NDES Connector. |
| NDES Connector-certifikatet hittades inte. <br><br> System.ArgumentNullException: värdet får inte vara null. | Intune Certificate Connector visar det här felet om Intune-klientadministratörskontot aldrig har loggat in till användargränssnittet för NDES Connector. <br><br> Om felet kvarstår, startar du om Intune Service Connector. <br><br> 1. Öppna services.msc <br> 2. Välj **Intune Connector-tjänsten**. <br> 3. Högerklicka och välj **starta om**.|
| NDES Connector – IssuePfx – allmänt undantag: <br> System.NullReferenceException: objektreferensen är inte satt till en instans av ett objekt. | Det här felet är tillfälligt. Starta om Intune Service Connector. <br><br> 1. Öppna services.msc <br> 2. Välj **Intune Connector-tjänsten** <br> 3. Högerklicka och välj **starta om**. |
| Symantec-providern – det gick inte att hämta Symantec-principen åtgärden tog för lång tid | Intune Certificate Connector tog emot ett timeout-fel för åtgärden vid kommunikation med Symantec CA:n. Om felet kvarstår kan du öka anslutningens timeout-värde och försöka igen. <br><br> Om du vill öka anslutningens timeout-värde: <br> 1. Gå till datorn med NDES-anslutningsprogrammet. <br>2. Öppna filen `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` i Anteckningar. <br> 3. Öka värdet för tidsgränsen för följande parameter: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Starta om Intune Connector-tjänsten. <br><br> Kontakta Symantecs kundsupport om problemet kvarstår. |
| Symantec-providern – det gick inte att hämta klientcertifikatet | Intune Certificate Connector kunde inte hämta certifikatet för resursauktorisering från den lokala datorns personliga certifikatarkiv. Lös problemet genom att se till att installera certifikatet för resursauktorisering i den lokala datorns personliga certifikatarkiv tillsammans med dess privata nyckel. <br><br> **Obs:** Certifikatet för resursauktorisering måste hämtas från Symantec CA:n. Kontakta Symantecs kundsupport för mer information. | 
| Symantec-providern – det gick inte att hämta Symantec-principen begäran avbröts: det gick inte att skapa en säker SSL-/TLS-kanal. | Det här felet uppstår under följande scenarier: <br><br> 1. Intunes Certificate Connector-tjänst har inte tillräcklig behörighet för att läsa certifikatet för resursauktoriseringen tillsammans med dess privata nyckel från den lokala datorns personliga certifikatarkiv. Lös problemet genom att kontrollera Connector-tjänsten som kör kontextkontot i services.msc. Connector-tjänsten måste köras under kontexten NT AUTHORITY\SYSTEM. <br><br> 2. PKCS-certifikatprofilen i Intune-administrationsportalen kan vara konfigurerad med en ogiltig Symantec CA bastjänst-FQDN. FQDN liknar `pki-ws.symauth.com`. Lös problemet genom att kontrollera med Symantecs kundtjänst om URL:en stämmer för din prenumeration. <br><br> 3. Intune Certificate Connector kan inte autentisera med Symantec CA:n med hjälp av certifikatet för resurstillstånd eftersom det inte kan hämta dess privata nyckel. Lös problemet genom att se till att installera certifikatet för resursauktorisering tillsammans med dess privata nyckel i den lokala datorns personliga certifikatarkiv. <br><br> Kontakta Symantecs kundsupport om problemet kvarstår. |
| Symantec-providern – det gick inte att hämta Symantec-principen ett nödvändigt element kunde inte tolkas. | Intune Certificate Connector kunde inte hämta Symantec-certifikatprofilmallen eftersom klientprofils-OID:n inte matchar Intune-certifikatprofilen. I ett annat fall kan Intune Certificate Connector inte hitta certifikatprofilmallen som associeras med den givna klientprofils-OID:n i Symantec CA:n. <br><br> Lös problemet genom att se till att hämta rätt klientprofils-OID från Symantec-certifikatmallen i Symantec-certifikatutfärdaren. Uppdatera sedan PKCS-certifikatprofilen i Intunes administrationsportal. <br><br> Hämta klientprofil-OID från Symantec CA:n: <br> 1. Logga in på administratörsportalen för Symantec CA:n. <br> 2. Klicka på hantera certifikatprofiler <br> 3. Välj den certifikatprofil som du vill använda. <br> 4. Hämta certifikatprofilens OID. Den liknar följande exempel: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Uppdatera PKCS-certifikatprofilen med rätt certifikatprofils-OID: <br>1. Logga in på Intune-administratörsportalen <br> 2. Gå till PKCS-certifikatprofilen och klicka på **redigera**. <br> 3. Uppdatera certifikatprofils-OID:n i uppdatera i namnfältet för certifikatmallen. <br> 4. Spara PKCS-certifikatprofilen. |
| Symantec-providern – principverifieringen misslyckades. <br><br> Attributet finns inte i attributlistan med certifikatmallar som stöds av Symantec | Symantec CA:n visar det här meddelandet när det finns en skillnad mellan Symantec-certifikatprofilmallen och Intune-certifikatprofilen. Det här problemet hände troligen på grund av matchningsfel av attribut i SubjectName eller SubjectAltName. <br><br> Lös problemet genom att se till att välja attribut som stöds av Intune för SubjectName och SubjectAltName i Symantec-certifikatprofilmallen. Mer information finns i attribut som stöds av Intune i avsnittet certifikatparametrar. |
| Vissa användarenheter tar inte emot PKCS-certifikat från Symantec CA:n. | Det här problemet inträffar när användarens-UPN innehåller specialtecken som understreck (exempel: `global_admin@intune.onmicrosoft.com`). <br><br> Symantec CA:n stöder inte specialtecken i mail_firstname och mail_lastname. <br><br> Du löser problemet genom att utföra följande steg: <br><br> 1.   Logga in på administratörsportalen för Symantec CA:n. <br> 2. Gå till hantera certifikatprofiler. <br> 3.   Klicka på Certifikatprofilen som används för Intune. <br> 4.  Klicka på länken anpassa alternativ. <br> 5.   Klicka på knappen avancerade alternativ. <br> 6.  Under certifikatfält – ämne DN, lägger du till fältet eget namn (CN) och tar bort det befintliga eget namn (CN)-fältet. Lägg till och ta bort måste utföras tillsammans. <br> 7.    Klicka på Spara. <br><br> Med den föregående ändringen, kommer Symantec-certifikatprofilen att begära CN =<upn> istället för mail_firstname och mail_lastname. |
| Användaren har manuellt tagit bort ett redan distribuerat certifikat från enheten. | Intune återdistribuerar samma certifikat vid nästa incheckning eller principtillämpning. I det här fallet tar inte NDES Connector emot en PKCS-certifikatbegäran. |

## <a name="next-steps"></a>Nästa steg

- Använd informationen i den här artikeln utöver informationen i [vad är Microsoft Intune-enhetsprofiler?](device-profiles.md) för att hantera din organisations enheter och certifikaten på dem.

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "Installera Intune Certificate Connector och välj PFX-distribution"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "Konfigurera Intune Certificate Connector"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "Skapa PKCS-certifikatprofilen i Azure-portalen"
