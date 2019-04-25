---
title: Bearbetning och lagring av data i Intune
description: Lär dig hur personliga data lagras och bearbetas i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b499f3171910f28a2d190d28e8ab6e945fa463a
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511276"
---
# <a name="data-storage-and-processing-in-intune"></a>Bearbetning och lagring av data i Intune

När Intune [samlar in data](privacy-data-collect.md) sker lagring och bearbetning av dessa data enligt beskrivningen nedan.

## <a name="storing-personal-data"></a>Lagring av personliga data

Alla data som inte är telemetridata bearbetas via Intune-tjänsten och lagras i en eller flera av följande lagringsplatser: 

- SQLAzure 
- Pålitliga samlingar (Service Fabric)  
- Azure-lagring 

Telemetri (tjänstloggar, prestandaloggar, fel och så vidare) som är viktiga för övervakning och för att tillhandahålla en stabil tjänst skickas till Microsofts telemetridatalager.

### <a name="storage-locations"></a>Lagringsplatser

Microsoft erbjuder och driver Intune-tjänster i många regioner över hela världen. Intune respekterar de val av lagringsplatser som görs av administratören för kunddata.

Mer information finns i [Microsoft Intune Where is my customer data?](For more information, see Microsoft Intune Where is my customer data?) (Var är mina kunddata?)

### <a name="personal-data-retention"></a>Kvarhållning av personliga data

I allmänhet bevaras personliga data av Intune fram till trettio dagar efter att användaren har tagits bort från Intune-hanteringen.

Telemetridata som samlas in som en del av Intune-användningen bevaras i högst trettio dagar.

Spårningsloggar bevaras i upp till ett år.

## <a name="processing-personal-data"></a>Bearbetning av personliga data

Intune bearbetar personliga data med ISO-certifierade system. Mer information finns i [Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp).

### <a name="profiling-and-marketing"></a>Profilering och marknadsföring

Microsoft Intune använder inte personliga data som samlas in i samband med tillhandahållandet av tjänsten i profilerings- eller marknadsföringssyfte. 

### <a name="restrict-processing-of-personal-data"></a>Begränsa bearbetning av personliga data

Om du vill begränsa bearbetningen av en användares personliga data kan du ta bort användarens konto genom att:
1. exportera en elektronisk kopia av användarens personliga data inklusive
    - konton
    - tjänstdata
    - associerade loggar
2. ta bort användarens konto och associerade data från Intune.

## <a name="next-steps"></a>Nästa steg

Lär dig mer om hur Intune [skyddar och delar](privacy-data-secure-share.md) personliga data. 
