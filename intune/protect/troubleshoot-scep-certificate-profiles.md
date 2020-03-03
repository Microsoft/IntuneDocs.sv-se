---
title: Felsöka användningen av SCEP-certifikatprofiler för att etablera certifikat till Microsoft Intune | Microsoft Docs
description: Felsök enheternas användning av SCEP för att begära certifikat för användning med Intune, inklusive kommunikation från enheter till NDES, NDES till certifikatutfärdare och från Intune Certificate Connector till Intune-tjänsten.
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
ms.openlocfilehash: 4496a5bbc6d5ee5134dc4e6a795494710ea6865d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515228"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>Översikt för felsökning av SCEP-certifikatprofiler i Microsoft Intune

Användning av certifikatprofiler för Simple Certificate Enrollment Protocol (SCEP) kan vara svårt att felsöka i Intune. Den här artikeln är en översikt som kan hjälpa dig att lösa problem genom att:

- Förklara arkitekturen och kommunikationsflödet för SCEP-processen
- Hjälpa dig att avgränsa var det finns ett problem i kommunikationsflödet
- Identifiera loggfiler som refereras till i efterföljande artiklar för felsökning av certifikatprofiler

Informationen i denna och relaterade artiklar om felsökning av SCEP-certifikatfel gäller användning av SCEP-certifikatprofiler med Android-, iOS- och iPad- och Windows-enheter. Liknande information för macOS är inte tillgänglig just nu.

Information om hur du felsöker registreringstjänsten för nätverksenheter (NDES) finns i följande artiklar från support.microsoft.com:

- [Verifiera NDES-konfiguration lokalt för SCEP-certifikat i Intune](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)
- [Felsökning av NDES-konfiguration för användning med Microsoft Intune-certifikatprofiler]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)

Innan du fortsätter bör du se till att du uppfyller [förutsättningarna för att använda SCEP-certifikatprofiler](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates), inklusive distribution av ett rotcertifikat via en betrodd certifikatprofil.

## <a name="scep-communication-flow-overview"></a>Översikt över SCEP-kommunikationsflöde

Följande bild visar en grundläggande översikt över SCEP-kommunikationsprocessen i Intune.

![SCEP-certifikatprofilflöde](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [Distribuera en SCEP-certifikatprofil](troubleshoot-scep-certificate-profile-deployment.md). Intune genererar en utmaningssträng, som kräver en speciell användare, certifikatsyfte och certifikattyp.

2. [Kommunikation mellan enheter och NDES-server](troubleshoot-scep-certificate-device-to-ndes.md). Enheten använder URI för NDES från profilen för att kontakta NDES-servern så att den kan presentera en utmaning.

3. [Kommunikation från NDES till principmodulen](troubleshoot-scep-certificate-ndes-policy-module.md). NDES vidarebefordrar utmaningen till Intune Certificate Connector-principmodulen på servern, som validerar begäran.

4. [NDES till certifikatutfärdaren](troubleshoot-scep-certificate-ndes-policy-module.md). NDES skickar giltiga begäranden för att utfärda ett certifikat till certifikatutfärdaren (CA).

5. [Leverera certifikat till enheter](troubleshoot-scep-certificate-delivery.md). Certifikatet levereras till enheten.

6. [Rapportering av distribution till Intune](troubleshoot-scep-certificate-reporting.md). Intune Certificate Connector rapporterar händelsen när certifikatet utfärdas till Intune.

## <a name="log-files"></a>Loggfiler

Om du vill identifiera problem med arbetsflödet för kommunikation och certifikatsetablering granskar du loggfilerna från både serverinfrastrukturen och från enheter. Senare avsnitt för felsökning av SCEP-certifikatprofiler avser de loggfiler som avses i det här avsnittet.

- [Infrastruktur- och serverloggar](#logs-for-on-premises-infrastructure)

Enhetsloggar är beroende av enhetsplattformen:  

- [iOS- och iPadOS](#logs-for-ios-and-ipados-devices)
- [Android](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>Loggar för den lokala infrastrukturen
  
Den lokala infrastrukturen som stöder användning av SCEP-certifikatprofiler för certifikatdistributioner innehåller Microsoft Intune Certificate Connector, NDES som körs på en Windows-Server och certifikatutfärdaren.

Loggfilerna för dessa roller omfattar Windows-loggboken, certifikatkonsoler och olika loggfiler som är speciella för Intune Certificate Connector, NDES eller andra roller och åtgärder som ingår i den lokala infrastrukturen.

Följande lista innehåller loggar eller konsoler som refereras till i följande SCEP-felsökningsartiklar. 

- **NDESConnector_date_time.svclog**:

  Den här loggen visar kommunikation från Microsoft Intune Certificate Connector till Intune-molnet. Du kan använda [visningsverktyget för tjänstspårning](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) för att visa den här loggfilen.

  Relaterad registernyckel: *HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  Plats: På servern som är värd för NDES på *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **CertificateRegistrationPoint_date_time.svclog**:

  I den här loggen visas NDES-principmodulen som tar emot och verifierar certifikatbegäranden. Du kan använda [visningsverktyget för tjänstspårning](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) för att visa den här loggfilen.

  Plats: På servern som är värd för NDES på *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **NDESPlugin.log**:

  I den här loggen visas överföring av certifikatbegäranden till certifikatregistreringsplatsen och den resulterande verifieringen av dessa begäranden.

  Plats: På den server som är värd för NDES på *%program_files%\Microsoft Intune\NDESPolicyModule\logs*

- **IIS-loggar**:

  IIS-loggar visar certifikatförfrågningar från mobila enheter som anropar NDES.

  Plats: På den server som är värd för NDES på *c:\inetpub\logs\LogFiles\W3SVC1*

- **Windows-programlogg**:

  Den här loggen är användbar när du undersöker IIS-problem, t. ex. SCEP-programpoolen.

  Plats: På den server som är värd för NDES: Öppna Loggboken i Windows genom att köra **eventvwr.msc**




### <a name="logs-for-android-devices"></a>Loggar för Android-enheter

För enheter som kör Android använder du programloggfilen **OMADM.log** i **Företagsportalen för Android**. Innan du samlar in och granskar loggar måste [utförlig loggning](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) vara aktiverad. Återskapa sedan problemet.

Om du vill samla in OMADM.logs från en enhet, se [Ladda upp och skicka e-postloggar med en USB-kabel](/intune-user-help/send-logs-to-your-it-admin-using-cable-android).

Du kan också [Ladda upp och skicka loggarna med e-post](/intune-user-help/send-logs-to-your-it-admin-by-email-android#upload-and-email-logs-from-microsoft-intune-app) som stöd.

### <a name="logs-for-ios-and-ipados-devices"></a>Loggar för iOS- och iPadOS-enheter

För enheter som kör iOS/iPadOS använder du felsökningsloggar och **Xcode** som körs på en Mac-dator:

1. Anslut iOS/iPadOS-enheten till Mac och gå sedan till **Program** > **Verktyg** för att öppna konsolprogrammet. 

2. Under **Åtgärd** väljer du **Inkludera informationsmeddelanden** och **Inkludera felsökningsmeddelanden**.

   ![Välj loggalternativ](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. Återskapa problemet och spara loggarna i en textfil:
   1. Välj **Redigera** > **Välj alla** för att markera alla meddelanden på den aktuella skärmen. Välj sedan **Redigera** > **Kopiera** för att kopiera meddelandena till urklipp. 
   2. Öppna TextEdit-programmet, klistra in de kopierade loggarna i en ny textfil och spara sedan filen.


Företagsportalloggen för iOS- och iPad-enheter innehåller inte information om SCEP-certifikatprofiler.

### <a name="logs-for-windows-devices"></a>Loggar för Windows-enheter

För enheter som kör Windows använder du händelseloggarna i Windows för att diagnosticera problem med registrering eller enhetshantering för enheter som du hanterar med Intune.

Öppna **Loggboken** > på enheten och gå sedan till **Program- och tjänstloggar** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider**

![Windows-händelseloggar](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>Nästa steg

Granska [distribution av SCEP-certifikatprofiler](troubleshoot-scep-certificate-profile-deployment.md) 
