---
title: Felsöka hanterad enhet för NDES-kommunikation i Microsoft Intune | Microsoft Docs
description: Felsök hanterad enhet för NDES-serverkommunikation när du använder SCEP-certifikatsprofiler för att distribuera certifikat med Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7945f1df3ddf1a6ff2c42a537e1071d1b5acff24
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514276"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>Felsök enhet för NDES-serverkommunikation för SCEP-certifikatsprofiler i Microsoft Intune

Använd följande information när du ska avgöra om en enhet som har tagit emot och bearbetat en certifikatsprofil för Intune SCEP (Simple Certificate Enrollment Protocol) kan kontakta registreringstjänsten för nätverksenheter (NDES) och presentera en utmaning. En privat nyckel genereras på enheten och certifikatsigneringsbegäran (CSR) och utmaningen skickas från enheten till NDES-servern. Enheten använder SCEP-certifikatsprofilens URI för att kontakta NDES-servern.

Den här artikeln hänvisar till steg 2 i [översikten över SCEP-kommunikationsflödet](troubleshoot-scep-certificate-profiles.md).

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>Sök i IIS-loggarna efter en anslutning från enheten

IIS-loggarna innehåller samma typ av poster för alla plattformar.


1. Öppna den senaste IIS-loggfilen som finns i följande mapp på NDES-servern: *%SystemDrive%\inetpub\logs\logfiles\w3svc1*

2. Sök i loggen efter poster liknande dem i följande exempel. Båda exemplen innehåller en status **200**, som visas nära slutet:

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   Och

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. När enheten kontaktar IIS loggas en HTTP GET-begäran för mscep.dll.

   Granska statuskoden nära slutet av den här begäran:
   - **Statuskod 200**: Denna status anger att anslutningen till NDES-servern har slutförts.
   - **Statuskod 500**: Gruppen IIS_IURS kanske saknar eventuellt rätt behörigheter. Mer information finns i [Statuskod 500](#status-code-500)längre fram i den här artikeln.
   - Om statuskoden inte är 200 eller 500:

     - Information om hur du kan validera konfigurationen finns i [Testa SCEP-serverns URL](#test-the-scep-server-url) längre fram i den här artikeln.

     - Information om mindre vanliga felkoder finns i [HTTP-statuskod i IIS 7 och senare versioner](https://support.microsoft.com/help/943891).

   Om anslutningsbegäran inte loggas alls kan kontakten från enheten blockeras i nätverket mellan enheten och NDES-servern.

## <a name="review-device-logs-for-connections-to-ndes"></a>Sök i enhetsloggarna efter anslutningar till NDES

### <a name="android-devices"></a>Android-enheter:

Granska [ enheternas OMADM-logg](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Leta efter poster som liknar följande, och som loggas när enheten ansluter till NDES:

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

Nyckelposterna innehåller följande exempeltextsträngar:

- Det finns 1 begäran
- "200 OK" togs emot när GetCACaps(ca) skickades till https://\<Server >.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
- Signerar pkiMessage med nyckeln som tillhör [dn=CN=\<username>; serial=1]


Anslutningen loggas också av IIS i NDES-serverns mapp %SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ på NDES-servern. Följande är ett exempel:

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="iosipados-devices"></a>iOS-/iPadOS-enheter

Granska [felsökningsloggen för enheter](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices). Leta efter poster som liknar följande, och som loggas när enheten ansluter till NDES:

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

Nyckelposterna innehåller följande exempeltextsträngar:

- operation=GetCACert
- Försöker hämta utfärdat certifikat
- Skickar CSR via GET
- operation=PKIOperation

### <a name="windows-devices"></a>Windows-enheter

På en Windows-enhet som upprättar en anslutning till NDES kan du ta fram Loggboken i Windows och söka efter indikationer på en lyckad anslutning. Anslutningarna loggas som händelse-ID **36** i enhetens logg *DeviceManagement-Enterprise-Diagnostics-Provide* > **Admin**.

Så här öppnar du loggen:

1. Öppna Loggboken i Windows genom att köra **eventvwr.msc** på enheten.

2. Expandera **Program- och tjänstloggar** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Administratör**.

3. Sök efter händelse **36**, liknande följande exempel, med nyckelraden för **SCEP: Certifikatsbegäran har genererats**:

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>Felsöka vanliga fel

I följande avsnitt får du hjälp med vanliga anslutningsproblem från olika enhetsplattformar till NDES.

### <a name="status-code-500"></a>Statuskod 500

Anslutningar, liknande dem i exemplet nedan, med statuskoden 500, visar att användarrättigheten *Personifiera en klient efter autentisering* inte har tilldelats till IIS_IURS-gruppen på NDES-servern. Statusvärdet för **500** visas i slutet:

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**Så här åtgärdar du felet**:

1. Öppna den lokala säkerhetsprincipen genom att köra **secpol.msc** på NDES-servern.

2. Utöka **Lokala principer** och klicka sedan på **Tilldelning av användarrättigheter**.

3. Dubbelklicka på **Personifiera en klient efter autentisering** i den högra rutan.

4. Klicka på **Lägg till användare eller grupp...** , ange **IIS_IURS** i rutan **Ange de objektnamn som ska väljas**och klicka sedan på **OK**.

5. Klicka på **OK**.

6. Starta om datorn och försök sedan ansluta från enheten igen.

### <a name="test-the-scep-server-url"></a>Testa SCEP-serverns URL

Testa den URL som anges i SCEP-certifikatsprofilen i följande steg.

1. Redigera SCEP-certifikatsprofilen och kopiera server-URL:en i Intune. URL:en bör likna *https://contoso.com/certsrv/mscep/msecp.dll* .

2. Öppna en webbläsare och gå sedan till SCEP-serverns URL. Resultatet bör vara: **HTTP-fel 403.0 – Förbjudet**. Resultatet indikerar att URL:en fungerar korrekt.

   Om du inte får det här felmeddelandet, så välj den länk som liknar det fel du ser, så att du kan få ärendespecifik vägledning:
   - [Jag får ett allmänt meddelande från registreringstjänsten för nätverksenheter](#general-ndes-message)
   - [Jag får meddelandet ”HTTP-fel 503. Tjänsten är inte tillgänglig”](#http-error-503)
   - [Jag får felmeddelandet "GatewayTimeout"](#gatewaytimeout)
   - [Jag får meddelandet "HTTP 414 Begärans-URI är för lång"](#http-414-request-uri-too-long)
   - [Jag får meddelandet "Det går inte att visa den här sidan"](#this-page-cant-be-displayed)
   - [Jag får meddelandet "500 – Internt serverfel"](#internal-server-error)

#### <a name="general-ndes-message"></a>Allmänt NDES-meddelande

När du bläddrar till SCEP-serverns URL får du följande meddelande om registreringstjänsten för nätverksenheter:

![SCEP-serveradress](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **Orsak**: Det här problemet beror vanligtvis på installationen av Microsoft Intune Connector.

  Mscep. dll är ett ISAPI-tillägg som fångar upp en inkommande begäran och visar felet HTTP 403 om installationen inte genomförs korrekt.
  
  **Lösning**: Undersök filen *SetupMsi.log* och ta reda på om Microsoft Intune Connector har installerats. I följande exempel indikerar *Installationen slutförts* och *Installationen lyckades eller felstatus: 0* att installationen har lyckats:

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  Om installationen misslyckas, så ta bort Microsoft Intune Connector och installera sedan om den.

#### <a name="http-error-503"></a>HTTP-fel 503

När du bläddrar till SCEP-serverns URL får du följande felmeddelande:

![HTTP-fel 503. Tjänsten är inte tillgänglig](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

Det här problemet beror vanligtvis på att **SCEP**-programpoolen i IIS inte har startats. Öppna **IIS-hanteraren** på NDES-servern och gå till **Programpooler**. Leta upp **SCEP**-programpoolen och bekräfta att den har startats.

Om SCEP-programpoolen inte har startats, så kontrollera serverns programhändelselogg:

1. Kör **eventvwr.msc** på enheten för att öppna **Loggboken** och gå till **Windows-loggar** > **Program**.

2. Leta efter en händelse som liknar följande exempel, vilket innebär att programpoolen kraschar när en begäran tas emot:

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**Vanliga orsaker till att en programpool kraschar**:

- **Orsak 1**: Det finns mellanliggande CA-certifikat (inte självsignerade) i NDES-serverns certifikatarkiv för betrodda rotcertifikatsutfärdare.

  **Lösning**: Ta bort mellanliggande certifikat från certifikatarkivet för betrodda rotcertifikatsutfärdare och starta sedan om NDES-servern.
  
  Om du vill identifiera alla mellanliggande certifikat i certifikatarkivet för betrodda rotcertifikatsutfärdare, så kör följande PowerShell-cmdlet: `Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  Ett certifikat som har samma värden för **Utfärdat till** och **Utfärdat av** är ett rotcertifikat. I annat fall är det ett mellanliggande certifikat.

  När du har tagit bort certifikaten och startat om servern, så kör PowerShell-cmdleten igen och bekräfta att det inte finns några mellanliggande certifikat. Om det finns mellanliggande certifikat, så kontrollera om en grupprincip pushar mellanliggande certifikat till NDES-servern. Om så är fallet, så exkludera NDES-servern från grupprincipen och ta bort de mellanliggande certifikaten igen.

- **Orsak 2**: URL:erna i listan över återkallade certifikat (CRL) är blockerade eller inte tillgängliga för de certifikat som används av Intune Certificate Connector.

  **Lösning**: Aktivera ytterligare loggning så att du kan samla in mer information:
  1. Öppna Loggboken, klicka på **Visa**, kontrollera att **Visa analytiska loggar och felsökningsloggar** har markerats.
  2. Gå till **Program- och tjänstloggar** > **Microsoft** > **Windows** > **CAPI2** > **Drift**, högerklicka på **Drift** och klicka sedan på **Aktivera logg**.
  3. När CAPI2-loggning har aktiverats kan du återskapa problemet och felsök problemet genom att kontrollera händelseloggen.

- **Orsak 3**: IIS-behörigheten för **CertificateRegistrationSvc** har aktiverat **Windows-autentisering**.

  **Lösning**: Aktivera **Anonym autentisering**, inaktivera **Windows-autentisering** och starta sedan om NDES-servern.

  ![IIS-behörigheter](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

När du bläddrar till SCEP-serverns URL får du följande felmeddelande:

![GatewayTimeout-fel](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **Orsak**: **Microsoft AAD Application Proxy Connector**-tjänsten har inte startats.

  **Lösning**:  Kör **services.msc** och kontrollera sedan att **Microsoft AAD Application Proxy Connector**-tjänsten körs och **Starttyp** har ställts in på **Automatisk**.

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 Begärans-URI:n är för lång

När du bläddrar till SCEP-serverns URL får du följande felmeddelande: `HTTP 414 Request-URI Too Long`

- **Orsak**: Filtrering av IIS-begäranden har inte konfigurerats för att stödja långa URL:er (frågor) som NDES-tjänsten tar emot. Det här stödet konfigureras när du [konfigurerar NDES-tjänsten](certificates-scep-configure.md#configure-the-ndes-service) för användning med din SCEP-infrastruktur.

- **Lösning**: Konfigurera stöd för långa URL:er.

  1. Öppna IIS-hanteraren på NDES-servern, välj **Standardwebbplats** > **Begärandefiltrering** > **Redigera funktionsinställning** så att sidan **Redigera inställningar för begärandefiltrering** öppnas.

  2. Konfigurera följande inställningar:
     - **Maximal URL-längd (byte)** = 65534
     - **Maximal frågesträng (byte)** = 65534

  3. Spara konfigurationen och stäng ISS-hanteraren genom att välja **OK**.

  4. Verifiera konfigurationen genom att lokalisera följande registernyckel och bekräfta att den har de angivna värdena:

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     Följande värden anges som DWORD-poster:
     - Namn: **MaxFieldLength**, med decimalvärdet **65534**
     - Namn: **MaxRequestBytes**, med decimalvärdet **65534**

  5. Starta om NDES-servern.

#### <a name="this-page-cant-be-displayed"></a>Det går inte att visa den här sidan

Du har konfigurerat Azure-AD-programproxyn. När du bläddrar till SCEP-serverns URL får du följande felmeddelande:

`This page can't be displayed`

- **Orsak**: Det här problemet uppstår när den externa SCEP-URL:en i Application Proxy-konfigurationen är inkorrekt. Ett exempel på denna URL är https://contoso.com/certsrv/mscep/mscep.dll.

  **Lösning**: Använd standarddomänen för *yourtenant.msappproxy.net* för den externa SCEP-URL:en i programproxykonfigurationen.

#### <a name="internal-server-error"></a>500 – Internt serverfel

När du bläddrar till SCEP-serverns URL får du följande felmeddelande:

![500 – Internt serverfel](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **Orsak 1**: NDES-tjänstkontot är låst eller så har lösenordet upphört att gälla.

  **Lösning**: Lås upp kontot eller återställ lösenordet.

- **Orsak 2**: MSCEP-RA-certifikaten har upphört att gälla.

  **Lösning**: Om MSCEP-RA-certifikaten har upphört att gälla så installera om NDES-rollen eller begär nya certifikat för CEP-krypterings-och Exchange-registreringsagent (offlinebegäran).

  Följ dessa steg om du vill begära nya certifikat:

  1. Öppna certifikatmallens MMC hos certifikatutfärdaren. Kontrollera att den inloggade användaren och NDES-servern har **läs-** och **registrerings**behörigheter certifikatmallarna för CEP-krypterings- och Exchange-registreringsagenten (offlinebegäran).

  2. Kontrollera de utgångna certifikaten på NDES-servern och kopiera **ämnes**information från certifikatet.

  3. Öppna certifikats-MMC för **datorkontot**.

  4. Expandera **Personligt**, högerklicka på **Certifikat** och välj **Alla uppgifter** > **Begär nytt certifikat**.

  5. Välj **CEP-kryptering** på sidan **Begär certifikat** och klicka sedan på **Mer information krävs för att registrera det här certifikatet. Konfigurera inställningarna genom att klicka här**.

     ![Välj CEP-kryptering](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. Klicka på fliken **Ämne** i **Certifikategenskaper**, fyll i **Ämnesnamn** med den information som du samlade in under steg 2, klicka på **Lägg till**och sedan på **OK**.

  7. Slutför certifikatregistreringen.

  8. Öppna certifikats-MMC för **Mitt användarkonto**.

     När du registrerar dig för certifikatet för Exchange-registreringsagenten (offlinebegäran) måste det göras i användarens kontext. Eftersom **Ämnestyp** för den här certifikatmallen är inställd på **Användare**.

  9. Expandera **Personligt**, högerklicka på **Certifikat** och välj **Alla uppgifter** > **Begär nytt certifikat**.

  10. Välj **Exchange-registreringsagent (onlinebegäran)** på sidan **Begär certifikat** och klicka sedan på **Mer information krävs för att registrera det här certifikatet. Konfigurera inställningarna genom att klicka här**.

      ![Välj Exchange-registreringsagent](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. Klicka på fliken **Ämne** i **Certifikategenskaper**, fyll i **Ämnesnamn** med den information som du samlade in under steg 2 och klicka på **Lägg till**.

      ![Certifikategenskaper](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      Välj fliken **Privat nyckel**, välj sedan **Gör privat nyckel exporterbar** och klicka därefter på **OK**.

      ![Privat nyckel](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. Slutför certifikatregistreringen.

  13. Exportera certifikatet för Exchange-registreringsagenten (offlinebegäran) från den aktuella användarens certifikatarkiv. I Guiden Exportera certifikat väljer du **Ja, exportera den privata nyckeln**.

  14. Importera certifikatet till den lokala datorns certifikatarkiv.

  15. Utför följande åtgärder i certifikat-MMC:n för varje nytt certifikat:

      Högerklicka på certifikatet, klicka på **Alla uppgifter** > **Hantera privata nycklar**, lägg till **läs**behörighet till NDES-tjänstkontot.

  16. Starta om IIS genom att köra kommandot **iisreset**.

## <a name="next-steps"></a>Nästa steg

Om enheten lyckas nå NDES-servern och presentera certifikatbegäran, så är nästa steg att granska [Intune Certificate Connectors-policymodulen](troubleshoot-scep-certificate-ndes-policy-module.md).
