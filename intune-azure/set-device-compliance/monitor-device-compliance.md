---
title: "Övervaka enhetsefterlevnad | Förhandsversion av Intune Azure | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: 7693d49e2f0fa6e4aa40b6bb71433a7eaab8dd15
ms.openlocfilehash: eb27002f449b3bbebb2a9b4ed780350c71eda881


---
# <a name="how-to-monitor-compliance-in-intune-azure-preview"></a>Övervaka efterlevnad i förhandsversionen av Intune Azure

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

Du kan öka detaljnivån för varje inställning om du vill se mer information om de profiler för vilka dessa inställningar har aktiverats, och inställningens konfigurerade värde.



<!--HONumber=Feb17_HO1-->


