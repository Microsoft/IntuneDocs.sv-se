---
title: Felsöka Microsoft Intune Certificate Connector och händelse-ID:n | Microsoft Docs
titleSuffix: Microsoft Intune
description: Felsök Microsoft Intune Certificate Connector genom att granska händelse-ID:n och beskrivningar samt läsa diagnostikkoderna för Intune Connector-tjänsten.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d9556cc0357e76ee617ac0770a3efc2e3a1957f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508877"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Händelser och diagnostikkoder för Intune Certificate Connector

Från och med version 6.1806.x.x loggar Intune Connector Service händelser i **Loggboken** (**Program- och tjänstloggar** > **Microsoft Intune Connector**). Använd dessa händelser till att felsöka eventuella problem med konfigurationen av Intune-anslutningsappen. Händelserna loggar lyckade och misslyckade åtgärder, samt diagnostikkoder som hjälper IT-avdelningen med felsökningen.

> [!TIP]  
> För felsökning och verifiering av Intune Connector-konfigurationen läser du [exempelskripten för certifikatutfärdare](https://aka.ms/intuneconnectorverificationscript).

## <a name="event-ids-and-descriptions"></a>Händelse-id:n och beskrivningar

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

## <a name="diagnostic-codes"></a>Diagnostikkoder

| Diagnostikkod | Diagnostiknamn | Diagnostikmeddelande |
| -------------   | -------------   | -------------      |
| 0x00000000 | Klart  | Klart |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | Certifikatutfärdaren är inte giltig eller kan inte nås. Kontrollera att certifikatutfärdaren är tillgänglig och att servern kan kommunicera med den. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | Symantec Client Auth-certifikatet gick inte att hitta i det lokala certifikatarkivet. Läs mer i artikeln [Installera Symantecs certifikat för registreringsauktorisering](certificates-digicert-configure.md#install-the-digicert-ra-certificate).  |
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
Mer hjälp finns i guiden [Troubleshooting SCEP certificate profile deployment in Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune) (Felsökning av SCEP-certifikatprofildistribution i Microsoft Intune).
