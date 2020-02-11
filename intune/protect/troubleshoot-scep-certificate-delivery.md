---
title: Felsöka leverans av certifikat till enheter när du använder SCEP med Microsoft Intune | Microsoft Docs
description: Felsöka leverans av ett certifikat till en enhet från certifikatutfärdaren när du distribuerar certifikat med hjälp av SCEP-certifikatprofiler med Intune.
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
ms.openlocfilehash: 77be59d126dc7e73bee468ca938938c6bb1b2e1a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915882"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>Felsöka leverans av certifikat som tillhandahålls av SCEP till enheter i Microsoft Intune

Ta hjälp av informationen i den här artikeln när du ska undersöka leveransen av certifikat till enheter när du använder SCEP (Simple Certificate Enrollment Protocol) för att etablera certifikat i Intune. Efter det att NDES-servern tagit emot det begärda certifikatet för en enhet från certifikatutfärdaren (CA), så skickar den tillbaka certifikatet till enheten.

Den här artikeln avser steg 5 i arbetsflödet för [SCEP-kommunikation](troubleshoot-scep-certificate-profiles.md) – leverans av certifikatet till enheten som skickade certifikatbegäran.

## <a name="review-the-certification-authority"></a>Granska certifikatutfärdaren

När certifikatutfärdaren har utfärdat certifikatet visar certifikatutfärdaren en post som liknar den i följande exempel:

![Exempel på utfärdade certifikat](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>Granska enheten

### <a name="android"></a>Android

För enhetsadministratörsregistrerade enheter visas ett meddelande som liknande det på följande bild, där du uppmanas att installera certifikatet:

![Android-meddelande](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

För Android Enterprise eller Samsung Knox sker certifikatinstallationen automatisk och tyst.

Om du vill visa ett installerat certifikat på Android, så använd en certifikatvisningsapp från tredje part.

Du kan också kontrollera enhetens [OMADM-logg](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Leta efter poster som liknar följande, och som loggas när certifikaten installeras:

**Rotcertifikat**:

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**Certifikat etablerade via SCEP**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="ios-and-ipados"></a>iOS- och iPad-enheter

På iOS- eller iPad-enheten kan du visa certifikatet under enhetshanteringsprofilen. Öka detaljnivån om du vill se information om de installerade certifikaten.

![iOS-certifikat](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

Du kan också hitta poster som liknar följande i [iOS-felsökningsloggen](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices):

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

Verifiera att certifikatet levererades på Windows-enheten:

- Öppna Loggboken genom att köra **eventvwr.msc**. Gå till **Program- och tjänstloggar** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Administratör** och sök efter **Händelse 39**. Den här händelsen bör ha en allmän beskrivning av: **SCEP: Certifikatet har installerats.**

   ![Händelse 39 i Windows programlogg](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

Om du vill visa certifikatet på enheten, så kör **certmgr.msc** för att öppna certifikat-MMC:n och kontrollera att rot- och SCEP-certifikaten har installerats korrekt på enheten i det personliga arkivet:

   1. Gå till **Certifikat (lokal dator)**  > **Betrodda rotcertifikatsutfärdare** > **Certifikat** och kontrollera att rotcertifikatet från certifikatutfärdaren finns där. Värdena för *Utfärdat till* och *Utfärdat av* är desamma.
   2. Gå till **Certifikat – aktuell användare** > **Personliga** > **certifikat** i certifikat-MMC:n och kontrollera att det begärda certifikatet finns, och att *Utfärdat av* är detsamma som certifikatutfärdarens namn.

## <a name="troubleshoot-failures"></a>Felsökning

### <a name="android"></a>Android

Om du vill felsöka det här steget, så granska de fel som har loggats i OMA DM-loggen.

### <a name="ios-and-ipados"></a>iOS- och iPad-enheter

Om du vill felsöka det här steget, så granska de fel som har loggats i enhetens felsökningslogg.

### <a name="windows"></a>Windows

Om du vill felsöka problem med certifikatet inte installeras på enheten, så gå till Windows-händelseloggen och sök efter fel som kan indikera typen av problem:

- Öppna Loggboken genom att köra **eventvwr.msc** på enheten, och gå sedan till **Program- och tjänstloggar** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**.

Fel med leverans och installation av certifikatet på enheten beror vanligtvis på Windows-åtgärder och inte på Intune.

## <a name="next-steps"></a>Nästa steg

När certifikatet har distribuerats till enheten, men Intune inte rapporterar detta, så beror det på fel i rapporteringen. Information om detta finns i [NDES-rapportering till Intune](troubleshoot-scep-certificate-reporting.md).
