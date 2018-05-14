---
title: Visa enhetsprofiler med Microsoft Intune – Azure | Microsoft Docs
description: Visa och hantera konfigurationsprofilen för enheter i Microsoft Intune och visa en grafisk karta över antalet enheter som är tilldelade till en profil och se vilka enheter som har profiler tilldelade eller distribuerade.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1c2eb08db58940ed575b3dea011395edd6711fc
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2018
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Övervaka enhetsprofiler i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune innehåller några funktioner i Azure Portal för att övervaka och hantera din enhets konfigurationsprofiler. Du kan exempelvis kontrollera statusen för en profil, se vilka enheter som är tilldelade och uppdatera egenskaperna för en profil.

## <a name="view-existing-profiles"></a>Visa befintliga profiler

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** > **Profiler**.

Alla dina befintliga profiler visas och innehåller information såsom plattform samt om profilen har tilldelats till några enheter.

## <a name="view-details-on-a-profile"></a>Visa information om en profil

När du har skapat din enhetsprofil tillhandahåller Intune grafiska diagram. Dessa diagram visar status för en profil, som t.ex. om den har tilldelats till enheter korrekt eller om profilen visar en konflikt.

1. Välj en befintlig profil. Välj till exempel en macOS-profil.
2. Välj fliken **Översikt**.

    Det grafiska diagrammet visar antalet enheter som är tilldelade till den specifika enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för macOS-enheter, visar diagrammet antal macOS-enheter.

    Det visar även antalet enheter för andra plattformar som tilldelats samma enhetsprofil. Till exempel visar det antalet enheter som inte är macOS-enheter.

    ![Visa antalet enheter som tilldelats enhetsprofilen](./media/device-configuration-profile-graphical-chart.png)

3. Välj cirkeln i det grafiska diagrammet. **Enhetstillstånd** öppnas.

    Enheter som är tilldelade till profilen visas samt om profilen har distribuerats korrekt. Tänk också på att bara enheterna med den specifika plattformen visas (till exempel macOS).

    Stäng statusinformation för enheten.

4. I egenskaperna för profilen (**Profiler** > Välj en specifik profil), du kan också ändra befintliga egenskaper:
  - **Egenskaper**: Ändra namnet eller uppdatera befintliga inställningar.
  - **Tilldelningar**: Inkludera eller exkludera enheter som principen ska gälla. Välj **Valda grupper** för att välja särskilda enhetsgrupper.
  - **Enhetsstatus**: Enheter som är tilldelade till profilen visas samt om profilen har distribuerats korrekt. Du kan välja en specifik enhet för att få ytterligare information, inklusive installerade appar.
  - **Användarstatus**: Visar en lista över användarnamn som påverkas av den här profilen och om profilen distribuerats korrekt. Du kan välja en specifik användare för att få ytterligare information.
  - **Status per inställning**: Filtrerar resultatet genom att visa de enskilda inställningarna i profilen och visar om inställningen har tillämpats korrekt.

## <a name="next-steps"></a>Nästa steg
[Tilldela användar- och enhetsprofiler](device-profile-assign.md)  
[Vanliga problem och lösningar med enhetsprofiler](device-profile-troubleshoot.md)