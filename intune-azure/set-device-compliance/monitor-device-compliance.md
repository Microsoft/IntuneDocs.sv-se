---
title: "Hur du övervakar enhetsefterlevnad"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs om hur du kan övervaka enhetsefterlevnad."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 15415f9f31d520d66257df3a7e134e4b1de8467c
ms.openlocfilehash: d70b3bc82b528184b5cfb4d4cad19cb034093e94
ms.lasthandoff: 04/07/2017


---
# <a name="how-to-monitor-device-compliance-in-intune-azure-preview"></a>Övervaka enhetsefterlevnad i Intune Azure Preview

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Du kan visa en sammanfattning av statusen för dina **efterlevnadsprofiler** på bladet **Översikt**.
Du kan klicka dig igenom diagrammen interaktivt eller gå ner på detaljnivå. Om du har flera konfigurerade efterlevnadsprofiler kan du även visa statusen för varje enskild princip genom att gå till principbladet och välja **Rapporter** i avsnittet **Hantera**.  Information från rapporterna som är tillgängliga för förhandsgranskning listas nedan.

##  <a name="device-compliance"></a>Efterlevnad för enhet

Enhetsefterlevnadsrapportens sammanfattningsvy börjar med att visa dig samlad information om antalet enheter som rapporterar på något av följande sätt:

- **Kompatibel**: Enheten har nyligen utvärderats för efterlevnad och har fastställts uppfylla de efterlevnadsprofilsinställningar som du har angett.
- **Icke-kompatibel**: Enheten har utvärderats och fastställts vara icke-kompatibel.  Om det har angetts en respitperiod i profilen, så har den upphört att gälla och gett enheten en icke-kompatibel status.
- **Respitperiod**: Enheten har utvärderats och fastställts vara icke-kompatibel. Respittiden gäller dock fortfarande tills enheten faktiskt har markerats som inkompatibel.

Du kan öka detaljnivån i varje avsnitt om du vill ha mer information om enskilda enheter och användare.

## <a name="setting-compliance"></a>Ställa in efterlevnad

Inställningskompatibilitetsrapporten ger detaljerad information om de enskilda efterlevnadsinställningarna, t.ex.:

- Antalet enheter som inte är kompatibla med inställningen.
- Den plattform som inställningen gäller.

Du kan öka detaljnivån för varje inställning om du vill se mer information om de profiler som inställningarna har aktiverats för, samt inställningens värde.

