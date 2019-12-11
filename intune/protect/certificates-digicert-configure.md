---
title: Utfärda DigiCert PKCS-certifikat med Microsoft Intune
titleSuffix: Microsoft Intune
description: Installera och konfigurera Intune Certificate Connector för att utfärda PKCS-certifikat från plattformen DigiCert PKI till Intune-hanterade enheter.
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
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca76ffe0c8fa42f1c2cf24fcdefd287140231220
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801631"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>Konfigurera Intune Certificate Connector för DigiCert PKI-plattformen

Använd Intune Certificate Connector för att utfärda PKCS-certifikat från plattformen DigiCert PKI till Intune-hanterade enheter. Du kan bara använda anslutningen med en DigiCert-certifikatutfärdare (CA) eller med både en DigiCert CA och en Microsoft CA.

> [!TIP]
> DigiCert har köpt Symantecs webbplatssäkerhet och relaterade PKI-lösningar. Mer information om den här ändringen finns i [Symantecs tekniska supportartikel](https://support.symantec.com/en_US/article.INFO4722.html).

Om du redan använder Intune Certificate Connector för att utfärda certifikat från en Microsoft CA med hjälp av PKCS eller System Center Endpoint Protection kan du använda samma anslutning för att konfigurera och utfärda PKCS-certifikat från en DigiCert CA. När du har slutfört konfigurationen för att stödja DigiCert-CA kan Intune Certificate Connector utfärda följande certifikat:

* PKCS-certifikat från en Microsoft CA
* PKCS-certifikat från en DigiCert CA
* Endpoint Protection-certifikat från en Microsoft CA

Om du inte har installerat anslutningsprogrammet men planerar att använda det för såväl en Microsoft CA som en DigiCert-CA ska du först slutföra anslutnings konfigurationen för Microsoft CA:n. Gå sedan tillbaka till den här artikeln för att konfigurera den så att den också stöder DigiCert. Mer information om certifikatprofiler och anslutningsprogrammet finns i [Konfigurera en certifikatprofil för dina enheter i Microsoft Intune](certificates-configure.md).  

Om du använder anslutningsprogrammet med endast DigiCert-CA kan du använda instruktionerna i den här artikeln för att installera och konfigurera anslutningen.

## <a name="prerequisites"></a>Krav

- **En aktiv prenumeration på DigiCert CA**: Prenumerationen krävs för att hämta ett registreringsutfärdarcertifikat (RA) från DigiCert CA:n.

## <a name="install-the-digicert-ra-certificate"></a>Installera DigiCert RA-certifikatet

1. Spara följande kodfragment som en fil med namnet **certreq.ini** och uppdatera om det behövs (till exempel: *Ämnesnamnet i CN-format*).

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

2. Öppna en upphöjd kommandotolk och skapa CSR-innehåll (certifikatsigneringsförfrågan) med följande kommando:

   `Certreq.exe -new certreq.ini request.csr`

3. Öppna filen request.csr i anteckningar och kopiera CSR-innehållet till följande format:

        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. Logga in på DigiCert CA och bläddra till **Hämta ett RA-certifikat** från aktiviteterna.

   a. Ange CSR-innehållet från steg 3 i textrutan.

   b. Ange ett eget namn för certifikatet.

   c. Välj **Fortsätt**.

   d. Använd den tillhandahållna länken för att ladda ned RA-certifikatet till den lokala datorn.

5. Importera RA-certifikatet till Windows-certifikatarkivet:

   a. Öppna en MMC-konsol.

   b. Klicka på **Arkiv** > **Lägg till eller ta bort snapin-moduler** > **Certifikat** > **Lägg till**.

   c. Välj **Datorkonto** > **Nästa**.

   d. Välj **Lokal dator** > **Avsluta**.

   e. I fönstret **Lägg till/ta bort snapin-moduler** klickar du på **OK**. Expandera **certifikat (lokal dator)**  > **personliga** > **certifikat**.

   f. Högerklicka på noden **certifikat** och välj **alla aktiviteter** > **importera**.

   g. Välj platsen för RA-certifikatet som du hämtade från DigiCert CA:n och välj **nästa**.

   h. Välj **Personligt certifikatarkiv** > **Nästa**.

   i. Välj **Avsluta** för att importera RA-certifikatet till den **lokala datorns personliga** arkiv tillsammans med dess privata nyckel.

6. Exportera och importera privat nyckelcertifikat:

   a. Expandera **certifikat (lokal dator)**  > **personliga** > **certifikat**.

   b. Välj det certifikat som importerades i föregående steg.

   c. Högerklicka på certifikatet och välj **alla aktiviteter** > **exportera**.

   d. Välj **Nästa** och ange sedan lösenordet.

   e. Välj plats att exportera till och välj sedan **slutför**.

   f. Use the procedure from step 5 to import the private key certificate into the **Local Computer-Personal** store.

   g. Kopiera tumavtrycket för RA-certifikatet utan blanksteg. Följande är ett exempel på ett tumavtryck:

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”

    > [!NOTE]
    > Kontakta [kundsupporten för DigiCert](mailto:enterprise-pkisupport@digicert.com) om du behöver hjälp med att hämta RA-certifikatet från DigiCert CA:n.

## <a name="prepare-to-install-intune-certificate-connector"></a>Förbered installation av Intune Certificate Connector

> [!TIP]
> Det här avsnittet gäller om du använder Intune Certificate Connector med endast en DigiCert CA. Om du använder Intune Certificate Connector med en Microsoft-certifikatutfärdare och vill lägga till DigiCert CA-stöd, kan du gå vidare till [Konfigurera för att stödja DigiCert](#configure-the-connector-to-support-digicert).

1. Välj någon av versionerna av Windows-operativsystemet från följande lista och installera det på en dator:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Skapa en användare med administratörsbehörighet och använd den för att slutföra följande steg.

3. Kontrollera de senaste Windows-uppdateringarna och installera dem vid behov. Starta om datorn när du har installerat Windows-uppdateringarna.

4. Installera .NET Framework 3.5:

   a. Öppna **Kontrollpanelen** > **program och funktioner** > **aktivera eller inaktivera Windows-funktioner**.

   b. Välj **.NET Framework 3.5** och installera det.

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>Installera Intune Certificate Connector för användning med DigiCert

> [!TIP]
> Om du använder Intune Certificate Connector med en Microsoft-certifikatutfärdare och vill lägga till DigiCert CA-stöd, kan du gå vidare till [Konfigurera för att stödja DigiCert](#configure-the-connector-to-support-digicert).

Hämta den senaste versionen av Intune Certificate Connector från Intune-administrationsportalen och följer de här anvisningarna.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Administration av klientorganisation** > **Anslutning och token** > **Certifikatanslutningsprogram** >  **+ Lägg till**.

3. Klicka på *Ladda ned programvara för certifikatanslutningsapp* för anslutningsprogrammet för PKCS #12 och spara filen på en plats som du kan komma åt från servern där du ska installera anslutningsprogrammet.

   ![Ladda ner anslutningsprogrammet](./media/certificates-digicert-configure/connector-download.png)

4. Kör **NDESConnectorSetup.exe** med utökade privilegier på servern där du vill installera anslutningsprogrammet.

5. På sidan **Installationsalternativ** väljer du **PFX-distribution**.

   ![Välj PFX-distribution](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Om du vill använda Intune Certificate Connector till att utfärda certifikat från en Microsoft CA och en DigiCert CA, väljer du **SCEP- och PFX-profildistribution**.

6. Använd standardvalen för att slutföra konfigurationen av anslutningen.

## <a name="configure-the-connector-to-support-digicert"></a>Konfigurera anslutningen så att den stöder DigiCert

Som standard installeras Intune Certificate Connector i **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc**.

1. I mappen **NDESConnectorSvc** öppnar du filen **NDESConnector.exe.config** i anteckningar.

   a. Uppdatera värdet för `RACertThumbprint`-nyckeln med certifikatets tumavtrycksvärde som du kopierade i föregående avsnitt. Exempel:

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>

   b. Spara och stäng filen.

2. Öppna **services.msc**:

   a. Välj **Intune Connector-tjänsten**.

   b. Stoppa tjänsten och starta den igen.

   c. Stäng tjänstens fönster.

## <a name="set-up-the-intune-administrator-account"></a>Konfigurera Intune-administratörskontot  

> [!TIP]
> Om du använder Intune Certificate Connector med en Microsoft-certifikatutfärdare och vill lägga till DigiCert CA-stöd, kan du gå vidare till [Skapa en betrodd certifikatprofil](#create-a-trusted-certificate-profile).
 
1. Öppna användargränssnittet för NDES Connector från **% ProgramFiles% \ Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**.

2. På fliken **Registrering** väljer du **Logga in**.

3. Ange dina autentiseringsuppgifter som Intune-klientadministratör.

4. Välj **Logga in** och välj sedan **OK** för att bekräfta en lyckad registrering. Stäng sedan användargränssnittet för NDES Connector.

   ![NDES Connector-gränssnitt med meddelandet "Registrerad"](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)

## <a name="create-a-trusted-certificate-profile"></a>Skapa en betrodd certifikatprofil

PKCS-certifikaten som distribueras för Intune-hanterade enheter måste kopplas till ett betrott rotcertifikat. För att skapa den här kedjan måste du skapa en Intune-betrodd certifikatprofil med rotcertifikatet från DigiCert CA:n.

1. Hämta ett betrott rotcertifikat från DigiCert CA:n:

   a. Logga in på administratörsportalen för DigiCert CA.

   b. Klicka på **Hantera certifikatutfärdare** från **aktiviteter**.

   c. Välja rätt certikatutfärdare från listan.

   d. Klicka på **hämta rotcertifikat** för att hämta det betrodda rotcertifikatet.

2. Skapa en betrodd certifikatprofil i Intune-portalen:

   a. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

   b. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.

   c. Ange följande egenskaper:

      - **Namnet** på profilen
      - Om du vill kan du ange en **beskrivning**
      - **Plattform** att distribuera profilen till
      - Ange **profiltypen** som **betrott certifikat**

   d. Välj **Inställningar** och bläddra till den betrodda .CER-filen för rotcertifikatutfärdarens certifikat som du exporterade för användning med den här certifikatprofilen och välj sedan **OK**.

   e. För Windows 8.1- och Windows 10-enheter, väjer du **Målarkiv** för det betrodda certifikatet från:
      - **Datorcertifikatarkiv – rot**
      - **Datorcertifikatarkiv – mellannivå**
      - **Användarcertifikatarkiv – mellannivå**

   f. När du är klar väljer du **OK**, går tillbaka till fönstret **Skapa profil** och väljer **Skapa**.  

  Profilen visas i listan över profiler i visningsfönstret **Enhetskonfiguration – Profiler**, med profiltypen **Betrott certifikat**.  Se till att tilldela den här profilen till enheter som ska ta emot certifikat. Om du vill tilldela profilen till grupper kan du läsa [Tilldela enhetsprofiler](../configuration/device-profile-assign.md).


## <a name="get-the-certificate-profile-oid"></a>Hämta certifikatprofilens OID  

Certifikatprofilens OID är associerad med en certifikatprofilsmall i DigiCert CA:n. Om du vill skapa en PKCS-certifikatprofil i Intune måste du ange namnet på certifikatmallen i form av ett certifikatprofil-OID som är kopplat till en certifikatmall i DigiCert CA:n.

1. Logga in på administratörsportalen för DigiCert CA.
2. Välj **hantera certifikatprofiler**.
3. Välj den certifikatprofil som du vill använda.
4. Kopiera certifikatprofilens OID. Den liknar följande exempel:

       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 

> [!NOTE]
> Kontakta [DigiCerts kundsupport](mailto:enterprise-pkisupport@digicert.com) om du behöver hjälp med att hämta certifikatprofilens OID.

## <a name="create-a-pkcs-certificate-profile"></a>Skapa en PKCS-certifikatprofil

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.

3. Ange följande egenskaper:

   - **Namnet** på profilen
   - Om du vill kan du ange en **beskrivning**
   - **Plattform** att distribuera profilen till
   - Ange **profiltypen** som **PKCS-certifikat**

4. I fönstret **PKCS-certifikat** konfigurerar du parametrar med värdena från följande tabell. Dessa värden krävs för att utfärda PKCS-certifikat från en DigiCert CA, via Intune Certificate Connector.

   |PKCS-certifikatparameter | Värde | Beskrivning |
   | --- | --- | --- |
   | Certifikatutfärdare | pki-ws.symauth.com | Det här värdet måste vara bastjänst-FQDN för DigiCert-certifikatutfärdaren utan avslutande snedstreck. Om du inte är säker på om det här är rätt bastjänst-FQDN för din DigiCert CA-prenumeration så kan du kontakta DigiCert kundsupport. <br><br>*Med ändringen från Symantec till DigiCert, förblir denna URL oförändrad*. <br><br> Om detta FQDN är felaktigt så utfärdar inte Intune Certificate Connector PKCS-certifikat från DigiCert-certifikatutfärdaren.| 
   | Namn på certifikatutfärdare | Symantec | Det här värdet måste vara strängen **Symantec**. <br><br> Om det här värdet ändras, kommer Intune Certificate Connector inte att utfärda PKCS-certifikat från DigiCert CA:n.|
   | Certifikatmallens namn | Certifikatprofil-OID från DigiCert CA:n. Exempel: **2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| Det här värdet måste vara ett certifikatprofils-OID som [hämtats i det föregående avsnittet](#get-the-certificate-profile-oid) från DigiCert CA-certifikatprofilmallen. <br><br> Om Intune Certificate Connector inte kan hitta en certifikatmall som är associerad med det här certifikatprofils-OID:n i DigiCertt CA:n, utfärdar den inga PKCS-certifikat från DigiCert CA:n.|

   ![Val för certifikatutfärdare och certifikatmall](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)

   > [!NOTE]
   > PKCS-certifikatprofiler för Windows-plattformar behöver inte associeras med en betrodd certifikatprofil. Men det krävs för icke-Windows-plattformprofiler, till exempel Android.

5. Slutför konfigurationen av profilen baserat på dina affärsbehov och välj sedan **Skapa** för att spara profilen.

6. På sidan *Översikt* i den nya profilen väljer du **Tilldelningar** och konfigurerar en lämplig grupp som ska använda den här profilen. Minst en användare eller enhet måste vara en del av den tilldelade gruppen.
 
När du har slutfört föregående steg, utfärdar Intune Certificate Connector PKCS-certifikat från DigiCert CA:n till Intune-hanterade enheter i den tilldelade gruppen. De här certifikaten blir tillgängliga i det **personliga** arkivet för den **aktuella användarens** certifikatarkiv på den Intune-hanterade enheten.

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>Attribut som stöds av PKCS-certifikatprofilen

|Attribut | Format som stöds av Intune | Format som stöds av DigiCert Cloud CA | resultat |
| --- | --- | --- | --- |
| Mottagarnamn |Intune stöder enbart ämnesnamnet i följande tre format: <br><br> 1. Allmänt namn <br> 2. Eget namn som inkluderar e-post <br> 3. Eget namn som e-post <br><br> Exempel: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | DigiCert CA har stöd för fler attribut.  Om du vill välja ytterligare attribut måste de ha definierats med fasta värden i DigiCert-certifikatprofilmallen.| Vi använder egna namn eller e-post från PKCS-certifikatbegäran. <br><br> Alla matchningsfel i attributval mellan Intune-certifikatprofilen och DigiCert-certifikatprofilmallen resulterar i att inga certifikat utfärdas av DigiCert CA:n.|
| SAN | Intune stöder endast följande SAN fältvärden: <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (kodat värde) | DigiCert Cloud CA:n har också stöd för dessa parametrar. Om du vill välja ytterligare attribut måste de ha definierats med fasta värden i DigiCert-certifikatprofilmallen. <br><br> **AltNameTypeEmail**: Om den här typen inte finns i SAN använder Intune Certificate Connector värdet från **AltNameTypeUpn**.  Om **AltNameTypeUpn** inte heller hittades i SAN använder Intune Certificate Connector värdet från ämnesnamnet om det är i e-postformat.  Om typen fortfarande inte hittas kan inte Intune Certificate Connector utfärda certifikaten. <br><br> Exempel: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn:** Om den här typen inte finns i SAN använder Intune Certificate Connector värdet från **AltNameTypeEmail**. Om **AltNameTypeEmail** inte heller hittas i SAN, används värdet från ämnesnamnet om det är i e-postformat. Om typen fortfarande inte hittas kan inte Intune Certificate Connector utfärda certifikaten.  <br><br> Exempel: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**: Om den här typen inte finns i SAN kan inte Intune Certificate Connector utfärda certifikaten. <br><br> Exempel: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  Värdet i det här fältet stöds endast i kodat format (hexadecimalt värde) av DigiCert-certifikatutfärdaren. För alla värden i det här fältet konverterar Intune Certificate Connector det till base64-kodat innan den skickar certifikatbegäran. *Intune Certificate Connector verifierar inte om det här värdet redan är kodat eller inte.* | Inga |

## <a name="troubleshooting"></a>Felsökning

Tjänstloggar för Intune Certificate Connector är tillgängliga i **% ProgramFiles% \ Microsoft Intune\NDESConnectorSvc\Logs\Logs** på NDES Connector-datorn. Öppna loggarna i [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) och sök efter undantag eller felmeddelanden.

| Problem/felmeddelande | Steg |
| --- | --- |
| Det går inte att logga in med Intune-klientadministratörskontot på användargränssnittet för NDES Connector. | Detta kan inträffa när det lokala certifikatanslutningsprogrammet inte är aktiverat i administrationscentret för Microsoft Endpoint Manager. Så här löser du det här problemet: <br><br> 1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). <br> 2. Välj **Administration av klientorganisation** > **Anslutning och token** > **Certifikatanslutningsprogram**. <br> 3. Leta reda på certifikatanslutningsprogrammet och kontrollera att det är aktiverat. <br><br> När du har slutfört de föregående stegen provar du att logga in med samma administratörskontot för Intune-klientorganisationen i användargränssnittet för NDES Connector. |
| NDES Connector-certifikatet hittades inte. <br><br> System.ArgumentNullException: Värdet får inte vara noll. | Intune Certificate Connector visar det här felet om Intune-klientadministratörskontot aldrig har loggat in till användargränssnittet för NDES Connector. <br><br> Om felet kvarstår startar du om Intune Service Connector. <br><br> 1. Öppna **services.msc**. <br> 2. Välj **Intune Connector-tjänsten**. <br> 3. Högerklicka och välj **starta om**.|
| NDES Connector – IssuePfx – allmänt undantag: <br> System.NullReferenceException: Objektreferensen är inte en instans av ett objekt. | Det här felet är tillfälligt. Starta om Intune Service Connector. <br><br> 1. Öppna **services.msc**. <br> 2. Välj **Intune Connector-tjänsten**. <br> 3. Högerklicka och välj **starta om**. |
| DigiCert Provider – Det gick inte att hämta DigiCert-principen. <br><br>”Åtgärden har nått sin tidsgräns." | Intune Certificate Connector tog emot ett timeout-fel för åtgärden vid kommunikation med DigiCert CA:n. Om felet kvarstår kan du öka anslutningens timeout-värde och försöka igen. <br><br> Om du vill öka anslutningens timeout-värde: <br> 1. Gå till datorn med NDES-anslutningsprogrammet. <br>2. Öppna **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config**-filen i anteckningar. <br> 3. Öka värdet för tidsgränsen för följande parameter: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Starta om tjänsten Intune Certificate Connector. <br><br> Kontakta DigiCerts kundsupport om problemet kvarstår. |
| DigiCert Provider – det gick inte att hämta klientcertifikatet. | Intune Certificate Connector kunde inte hämta certifikatet för resursauktorisering från den lokala datorns personliga certifikatarkiv. Lös problemet genom att se till att installera certifikatet för resursauktorisering i den lokala datorns personliga certifikatarkiv tillsammans med dess privata nyckel. <br><br> Certifikatet för resursauktorisering måste hämtas från DigiCert-certifikatutfärdaren. Kontakta DigiCerts kundsupport för mer information. | 
| DigiCert Provider – Det gick inte att hämta DigiCert-principen. <br><br>”Förfrågan avbröts: Det gick inte att skapa en säker SSL/TLS-kanal.” | Det här felet uppstår under följande scenarier: <br><br> 1. Intunes Certificate Connector-tjänst har inte behörighet för att läsa certifikatet för resursauktoriseringen tillsammans med dess privata nyckel från den lokala datorns personliga certifikatarkiv. Lös problemet genom att kontrollera Connector-tjänsten som kör kontextkontot i services.msc. Connector-tjänsten måste köras under kontexten NT AUTHORITY\SYSTEM. <br><br> 2. PKCS-certifikatprofilen i Intune-administrationsportalen kan vara konfigurerad med en ogiltig DigiCert CA bastjänst-FQDN. FQDN liknar **pki-ws.symauth.com**. Lös problemet genom att kontrollera med DigiCert kundtjänst om URL:en stämmer för din prenumeration. <br><br> 3. Intune Certificate Connector kan inte autentisera med DigiCert CA:n med hjälp av certifikatet för resurstillstånd eftersom det inte kan hämta dess privata nyckel. Lös problemet genom att se till att installera certifikatet för resursauktorisering i den lokala datorns personliga certifikatarkiv tillsammans med dess privata nyckel. <br><br> Kontakta DigiCerts kundsupport om problemet kvarstår. |
| DigiCert Provider – Det gick inte att hämta DigiCert-principen. <br><br>"En del av begäran kan inte tolkas." | Intune Certificate Connector kunde inte hämta DigiCert-certifikatprofilmallen eftersom klientprofils-OID:n inte matchar Intune-certifikatprofilen. I ett annat fall kan Intune Certificate Connector inte hitta certifikatprofilmallen som associeras med den givna klientprofils-OID:n i DigiCert CA:n. <br><br> Lös problemet genom att se till att hämta rätt klientprofils-OID från DigiCert-certifikatmallen i DigiCert-certifikatutfärdaren. Uppdatera sedan PKCS-certifikatprofilen i Intunes administrationsportal. <br><br> Hämta certifikatprofilens OID från DigiCert CA:n: <br> 1. Logga in på administratörsportalen för DigiCert CA. <br> 2. Välj **hantera certifikatprofiler**. <br> 3. Välj den certifikatprofil som du vill använda. <br> 4. Hämta certifikatprofilens OID. Den liknar följande exempel: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Uppdatera PKCS-certifikatprofilen med rätt certifikatprofils-OID: <br>1. Logga in på Intune-administratörsportalen. <br> 2. Gå till PKCS-certifikatprofilen och klicka på **redigera**. <br> 3. Uppdatera certifikatprofils-OID:n i uppdatera i namnfältet för certifikatmallen. <br> 4. Spara PKCS-certifikatprofilen. |
| DigiCert Provider – principverifieringen misslyckades. <br><br> Attributet finns inte i attributlistan med certifikatmallar som stöds av DigiCert. | DigiCert CA:n visar det här meddelandet när det finns en skillnad mellan DigiCert-certifikatprofilmallen och Intune-certifikatprofilen. Det här problemet hände troligen på grund av matchningsfel av attribut i **SubjectName** eller **SubjectAltName**. <br><br> Lös problemet genom att välja attribut som stöds av Intune för **SubjectName** och **SubjectAltName** i DigiCert-certifikatprofilmallen. Mer information finns i attribut som stöds av Intune i avsnittet **certifikatparametrar**. |
| Vissa användarenheter tar inte emot PKCS-certifikat från DigiCert CA:n. | Det här problemet inträffar när användarens-UPN innehåller specialtecken som understreck (exempel: `global_admin@intune.onmicrosoft.com`). <br><br> DigiCert CA:n stöder inte specialtecken i **mail_firstname** och **mail_lastname**. <br><br> Du löser problemet genom att utföra följande steg: <br><br> 1. Logga in på administratörsportalen för DigiCert CA. <br> 2. Gå till **hantera certifikatprofiler**. <br> 3. Välj certifikatprofilen som används för Intune. <br> 4. Välj länken **Anpassa alternativ**. <br> 5. Välj knappen **Avancerade alternativ**. <br> 6. Under **certifikatfält – ämne DN**, lägger du till fältet **eget namn (CN)** och tar bort det befintliga **eget namn (CN)** -fältet. Lägg till och ta bort måste utföras tillsammans. <br> 7. Välj **Spara**. <br><br> Med den föregående ändringen, kommer DigiCert-certifikatprofilen att begära **”CN =<upn>”** istället för **mail_firstname** och **mail_lastname**. |
| Användaren har manuellt tagit bort ett redan distribuerat certifikat från enheten. | Intune återdistribuerar samma certifikat vid nästa incheckning eller principtillämpning. I det här fallet tar inte NDES Connector emot en PKCS-certifikatbegäran. |

## <a name="next-steps"></a>Nästa steg

Använd informationen i den här artikeln utöver informationen i [vad är Microsoft Intune-enhetsprofiler?](../configuration/device-profiles.md) för att hantera din organisations enheter och certifikaten på dem.
