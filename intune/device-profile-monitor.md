---
title: Visa enhetsprofiler med Microsoft Intune – Azure | Microsoft Docs
description: Visa och hantera konfigurationsprofilen för enheter i Microsoft Intune, visa en grafisk karta över antalet enheter som är tilldelade till en profil och se vilka enheter som har profiler tilldelade eller distribuerade. Kan även felsöka profiler som har inställningar i konflikt.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: dc3a9620532951bd78e545e87b0d43dd6be3efe5
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186604"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Övervaka enhetsprofiler i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune innehåller några funktioner i Azure Portal för att övervaka och hantera din enhets konfigurationsprofiler. Du kan exempelvis kontrollera statusen för en profil, se vilka enheter som är tilldelade och uppdatera egenskaperna för en profil.

## <a name="view-existing-profiles"></a>Visa befintliga profiler

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** > **Profiler**.

Alla dina befintliga profiler visas, innehåller information såsom plattform och visar om profilen har tilldelats till några enheter.

## <a name="view-details-on-a-profile"></a>Visa information om en profil

När du har skapat din enhetsprofil tillhandahåller Intune grafiska diagram. Dessa diagram visar status för en profil, som t.ex. om den har tilldelats till enheter korrekt eller om profilen visar en konflikt.

1. Välj en befintlig profil. Välj till exempel en macOS-profil.
2. Välj fliken **Översikt**.

    Det övre diagrammet visar antalet enheter som är tilldelade till den specifika enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för macOS-enheter, visar diagrammet antal macOS-enheter.

    Det visar även antalet enheter för andra plattformar som tilldelats samma enhetsprofil. Till exempel visar det antalet enheter som inte är macOS-enheter.

    ![Visa antalet enheter som tilldelats enhetsprofilen](./media/device-configuration-profile-graphical-chart.png)

    Det under diagrammet visar antalet användare som är tilldelade till den specifika enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för macOS-användare visar diagrammet antalet macOS-användare.

3. Välj cirkeln i det övre grafiska diagrammet. **Enhetstillstånd** öppnas.

    Enheter som är tilldelade till profilen visas samt om profilen har distribuerats korrekt. Tänk också på att bara enheterna med den specifika plattformen visas (till exempel macOS).

    Stäng **statusinformationen** för enheten.

4. Välj cirkeln i det undre grafiska diagrammet. **Användarstatus** öppnas. 

    Användare som är tilldelade till profilen visas samt om profilen har distribuerats korrekt. Tänk också på att bara användarna med den specifika plattformen visas (till exempel macOS).

    Stäng **statusinformationen** för användarna.

5. Välj en profil i listan **Profiler**. Du kan också ändra befintliga egenskaper:
  - **Egenskaper**: Ändra namnet eller uppdatera befintliga inställningar.
  - **Tilldelningar**: Inkludera eller exkludera enheter som principen ska gälla. Välj **Valda grupper** för att välja särskilda enhetsgrupper.
  - **Enhetsstatus**: Enheter som är tilldelade till profilen visas samt om profilen har distribuerats korrekt. Du kan välja en specifik enhet för att få ytterligare information, inklusive installerade appar.
  - **Användarstatus**: Visar en lista över användarnamn som påverkas av den här profilen och om profilen distribuerats korrekt. Du kan välja en specifik användare för att få ytterligare information.
  - **Status per inställning**: Filtrerar resultatet genom att visa de enskilda inställningarna i profilen och visar om inställningen har tillämpats korrekt.

## <a name="view-conflicts"></a>Visa konflikter

I **Enheter** > **Alla enheter** kan du se alla inställningar som orsakar en konflikt. När det finns en konflikt visas även alla konfigurationsprofiler som innehåller inställningen. Administratörer kan använda funktionen till att felsöka och åtgärda avvikelser med profilerna.

1. Välj i Intune **Enheter** > **Alla enheter** > välj en befintlig enhet i listan. Slutanvändare kan få enhetsnamnet från appen Företagsportal.
2. Välj **Enhetskonfiguration**. Alla konfigurationsprinciper som gäller för enheten listas.
3. Välj principen. Här visas alla inställningar i den principen som gäller för enheten. Om en enhet är i **konflikt** väljer du den raden. I det nya fönstret visas alla profiler och namnen på de profiler som har inställningen som orsakar konflikten.

Nu när du känner till inställningen som orsakar konflikten och vilka principer som innehåller den inställningen bör det vara lättare att lösa konflikten. 

## <a name="next-steps"></a>Nästa steg
[Tilldela användar- och enhetsprofiler](device-profile-assign.md)  
[Vanliga problem och lösningar med enhetsprofiler](device-profile-troubleshoot.md)