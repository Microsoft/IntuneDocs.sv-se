---
title: Datasäkerhet och delning i Intune
description: Lär dig hur personliga data skyddas och delas i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 631d76aca2c393be3c81cb8b6f532605664f4ce4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721961"
---
# <a name="data-security-and-sharing-in-intune"></a>Datasäkerhet och delning i Intune


## <a name="data-security"></a>Datasäkerhet

Microsoft Intune är en viktig del av Microsoft Enterprise Mobility och molntjänsterbjudandet Security Suite. För att stödja [datastyrningsstrategin](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx) utvecklas alla molntjänster från Microsoft med metoderna [Microsoft Privacy](https://www.microsoft.com/en-us/trustcenter/privacy) och [Microsoft Security](https://www.microsoft.com/en-us/trustcenter/security/).  

Microsoft Intune följer samma tekniska och organisatoriska åtgärder som Microsoft Azure-tjänstteamen vidtar för att skydda mot dataintrångsprocesser.

Mer information finns i [Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp).

Intune använder dataminimeringstekniker som

- aggregering
- valfri datainsamling för vissa funktioner
- data som görs mindre exakta eller känsliga

Intune använder även tekniker som RBAC och JiT-säkerhet för supportärenden för att säkerställa dataskydd som standard. 

### <a name="data-breach-reporting"></a>Rapportering av dataintrång

När en CRSI (Customer-Reportable Security Incident) identifieras meddelas kunderna. I den här processen ingår arbete med Microsoft O365-teamet för att skicka meddelande om intrång till alla Microsoft O365-kunder som använder Intune.

## <a name="data-sharing"></a>Datadelning

När klientorganisationsadministratörer aktiverar vissa funktioner (till exempel Apple Device Enrollment Program) hämtar Microsoft Intune administratörens godkännande för att dela data med lämpliga tredje parter. I sådana fall kan Intune dela personliga data med:

- Tredje parter som agerar som Microsofts agenter.
- Tredje parter som inte agerar som Microsofts agenter, men bara när klientorganisationsadministratörerna uttryckligen ger Intune tillstånd att göra detta.

Alla tredje parter som agerar som Microsoft-agenter ingår i [listan över underleverantörer för Online Services](https://aka.ms/Online_Serv_Subcontractor_List).

Data delas med sådana entiteter för att hjälpa kunden och underlätta teknisk support, serverunderhåll och andra åtgärder.

En klientorganisations kontrakt med tredje part styr de personliga Intune-data som lagras i tjänsten från tredje part. Det ger även Intune behörighet att överföra data till tjänsten från tredje part.  

Information om data som delas med vissa tredje parter finns i följande artiklar:
- [Data som Intune skickar till Apple](data-intune-sends-to-apple.md)
- [Data som Intune skickar till Google](data-intune-sends-to-google.md)
- [Data som Apple skickar till Intune](data-apple-sends-to-intune.md)
- [Data som Google skickar till Intune](data-google-sends-to-intune.md)
- [Data som Jamf Pro skickar till Intune](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>System Center Configuration Manager-datadelning

Microsoft Intune delar inte data med System Center Configuration Manager. System Center Configuration Manager är en lokal produkt som distribueras, hanteras och drivs direkt av kunden. Diagnostik och användningsdata som samlas in av Configuration Manager används endast för att förbättra installationsproceduren, kvaliteten och säkerheten i framtida versioner.

Mer information finns i [Diagnostik och användningsdata för SCCM](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data). 


## <a name="next-steps"></a>Nästa steg

Ta reda på hur du [visar och korrigerar](privacy-data-view-correct.md) personliga data i Intune.
