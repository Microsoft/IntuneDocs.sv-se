---
title: Felsöka Microsoft Intune Certificate Connector och principmodul | Microsoft Docs
description: Felsök åtgärden i NDES-principmodulen när modulen bearbetar en certifikatförfrågan när du använder SCEP-certifikatprofiler för att distribuera certifikat med Intune.
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
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915843"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>Felsöka NDES-principmodulen i Microsoft Intune

Informationen i den här artikeln kan hjälpa dig att kontrollera driften av principmodulen för registreringstjänsten för nätverksenheter (NDES) som installeras med Microsoft Intune Certificate Connector. När NDES tar emot en begäran om ett certifikat, vidarebefordrar den begäran till principmodulen som validerar begäran som giltig för enheten. Efter verifieringen kontaktar NDES certifikatutfärdaren (CA) för att begära certifikatet för enhetens räkning.

Den här artikeln gäller steg 3 och 4 i [SCEP-kommunikationsarbetsflödet](troubleshoot-scep-certificate-profiles.md).

## <a name="ndes-communication-to-the-policy-module"></a>NDES-kommunikation till principmodulen

När du har tagit emot en certifikatbegäran från en enhet verifierar NDES begäran med Intune genom den principmodul som installeras med Microsoft Intune Certificate Connector. Dessa poster avser *certifikatets registreringsplats*.

**Loggposter som visar lyckade**:

För att bekräfta att verifieringsförfrågan skickas till modulen söker du efter en post som liknar följande exempel i loggar på NDES-servern:

- **IIS-loggar**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **NDESPlugin-logg**:

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  Följande exempel visar en lyckad verifiering av enhetens kontrollförfrågan och att NDES nu kan kontakta certifikatutfärdaren:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**När det inte finns några indikatorer för lyckade**:

Om du inte hittar dessa poster börjar du med att granska felsökningsvägledningen för [kommunikation mellan enhet och NDES-server](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors).

Om informationen i den artikeln inte hjälper dig att lösa problemet är följande ytterligare poster som kan tyda på problem.

### <a name="ndespluginlog-contains-an-error-12175"></a>NDESPlugin.log innehåller ett fel 12175

När loggen innehåller ett fel 12175 som liknar följande kan det bero på ett problem med SSL-certifikatet:

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

Moderna webbläsare och webbläsare på mobila enheter ignorerar *vanliga namn* på ett SSL-certifikat om det finns *Alternativt namn för certifikatmottagare*.

**Lösning**:  Utfärda SSL-certifikatet för webbservern med följande attribut för *Eget namn* och *Alternativt namn för certifikatmottagare* och bind det sedan till port 443 i IIS:

  - **Ämnesnamn**  
    CN = externt servernamn
  - **Alternativt namn för certifikatmottagare**  
     Namn = externt servernamn  
     DNS-namn = internt servernamn

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>NDESPlugin.log innehåller ett fel 403 – Förbjuden: Åtkomst nekas”

När följande loggar innehåller ett fel 403 som liknar följande kan klientcertifikatet vara ej betrott eller ogiltigt:

**NDESPlugin.log**:

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**IIS-logg**:

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

Felet uppstår om det finns mellanliggande CA-certifikat i NDES-serverns certifikatarkiv för betrodda rotcertifikatsutfärdare.

Ett certifikat som har samma värden för *Utfärdat till* och *Utfärdat av* är ett rotcertifikat. I annat fall är det ett mellanliggande certifikat.

**Lösning**: För att åtgärda problemet, identifiera och bort mellanliggande CA-certifikat från certifikatarkivet för betrodda rotcertifikatsutfärdare.

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>NDESPlugin.log anger att anropet returnerar värdet falskt

När resultatet av utmaningen returnerar **falskt** kontrollerar du om *CertificateRegistrationPoint.svclog* innehåller fel. Du kan till exempel se felmeddelandet "Signeringscertifikat kunde inte hämtas"som liknar följande post:

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**Lösning**: På den server där anslutningen är installerad öppnar du Registereditorn. Identifiera registernyckeln `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector` och kontrollerar om värdet för SigningCertificate finns.

Om det här värdet inte finns startar du om Intune Connector-tjänsten i Services.msc och kontrollerar sedan om värdet visas i registret. Om värdet fortfarande saknas beror det ofta på problem med nätverksanslutningen mellan servern som NDES och Intune-tjänsten.

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES skickar begäran om att utfärda certifikatet

Efter en lyckad verifiering av certifikatregistreringsplatsen (principmodulen) skickar NDES certifikatbegäran till certifikatutfärdaren för enhetens räkning.

**Loggposter som visar lyckade**:

- **NDESPlugin-logg**:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **IIS-loggar**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**När det inte finns några indikatorer för lyckade**:

Följ dessa steg om det inte finns poster som indikerar lyckade:

1. Leta efter problem som är loggade i *CertificateRegistrationPoint. svclog* när certifikatregistreringsplatsen verifierar kontrollen. Leta efter posterna mellan följande rader:

   - VerifyRequest startades.
   - VerifyRequest har avslutats med statusen falskt

2. Öppna certifikatutfärdaren MMC på CA:et och välj **Misslyckade begäranden** för att leta efter felmeddelanden som hjälper dig att identifiera problemet. Följande bild är ett exempel:

   ![Exempel på en misslyckad begäran](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. Granska programhändelseloggen på CA:et för fel. Vanligtvis kan du se fel som matchar det du ser i **Misslyckade begäranden** från föregående steg. Följande bild är ett exempel:

   ![Granska programloggen](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>Nästa steg

Om NDES-principmodulen validerar begäran och begäran vidarebefordras till certifikatutfärdaren är nästa steg att granska [certifikatleverans till enheten](troubleshoot-scep-certificate-delivery.md).
