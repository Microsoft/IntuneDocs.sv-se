---
title: Felsöka rapportering av lyckad certifikatdistribution till enheter när du använder SCEP med Microsoft Intune | Microsoft Docs
description: Felsöka NDES-rapportering och anslutningsprogrammet till Intune om en lyckad certifikatsdistribution som har etablerats med SCEP-certifikatsprofiler.
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
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916025"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>Felsöka NDES-rapportering av certifikatsdistributioner i Microsoft Intune

Använd följande information när du ska bekräfta att NDES och Microsoft Intune Certificate Connector har rapporterat till Intune att certifikatet har levererats till en enhet. Att rapportera till Intune är den sista fasen i användningen av SCEP-certifikatsprofiler för att etablera Windows-enheter med ett certifikat.

Den här artikeln gäller steg 6 i [SCEP-kommunikationsarbetsflödet](troubleshoot-scep-certificate-profiles.md).

## <a name="review-for-signs-of-successful-reporting"></a>Söka efter tecken på lyckad rapportering

Om rapporteringen lyckades, så kommer du att hitta poster som liknar följande exempel på NDES-servern:

- **IIS-logg**:

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log**:

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  ![Logg för Intune-certifikatanslutningsappen](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog**:

  ![Logg för Intune-certifikatanslutningsappen](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus**:

  Gå till mappen *%program%\Microsoft Intune\CertificateRequestStatus* som innehåller mapparna **Misslyckade**, **Bearbetning** och **Lyckade**, vilka innehåller statusfiler för certifikatbegäran.

  Om certifikatbegäran har bearbetats visas nya filer i mappen **Lyckade**. Du kan använda *Notepad.exe* för att öppna filerna och visa de data som överförs till Intune-tjänsten av Intune-certifikatanslutningsappen. Data som överförs innehåller information som **CertificateSerialNumber**, **UserID**, **DeviceID**och **Tumavtryck**.

### <a name="troubleshoot-stuck-files"></a>Felsöka låsta filer

Om du inte ser att några nya filer har skapats i mappen *Lyckade*, så kontrollera om det finns några filer som fastnat i mappen *Bearbetning*.

Verifiera att Intune-anslutningsappstjänsten har startats på NDES-servern, och att det inte finns några fel i Ndesconnector.svclog.

## <a name="next-steps"></a>Nästa steg

[Så kan du få support för Microsoft Intune](../fundamentals/get-support.md)
