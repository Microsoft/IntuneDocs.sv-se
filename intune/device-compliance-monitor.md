---
title: "Övervaka enhetsefterlevnad"
titlesuffix: Microsoft Intune
description: "Läs hur du övervakar enhetsefterlevnad.”"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 708ed5a335d3475c213a536da9072afb1ad32ef9
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2018
---
# <a name="monitor-device-compliance-in-intune"></a>Övervaka enhetsefterlevnad i Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Du kan visa en sammanfattning av statusen för dina **efterlevnadsprofiler** på bladet **Översikt**.
Du kan klicka dig igenom diagrammen interaktivt eller gå ner på detaljnivå. Om du har konfigurerat flera efterlevnadsprofiler kan du se principstatusen på principbladet under **Hantera** > **Rapporter**.

##  <a name="device-compliance"></a>Efterlevnad för enhet

Den sammanfattade vyn för enhetsefterlevnadsrapporten visar den samlade informationen om antalet enheter som rapporterar med någon av följande statusar:

- **Kompatibel**: Enheten har nyligen utvärderats och uppfyller de efterlevnadsprofilinställningar som du angav.
- **Icke-kompatibel**: Enheten har utvärderats och fastställts vara icke-kompatibel.  Om det har angetts en respitperiod i profilen, så har den upphört att gälla och gett enheten en icke-kompatibel status.
- **Respitperiod**: Enheten har utvärderats och fastställts vara icke-kompatibel. Respittiden gäller dock fortfarande tills enheten har markerats som inkompatibel.

Du kan öka detaljnivån i varje avsnitt om du vill ha mer information om enskilda enheter och användare.

## <a name="setting-compliance"></a>Ställa in efterlevnad

Rapporten om inställningsefterlevnad ger detaljerad information för varje efterlevnadsinställning, exempelvis:

- Antalet enheter som inte är kompatibla med inställningen.
- Den plattform som inställningen gäller.

Du kan öka detaljnivån för varje inställning om du vill se mer information om de profiler som inställningarna har aktiverats för, samt inställningens värde.
