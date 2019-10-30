---
title: Visa enhetsprofiler med Microsoft Intune – Azure | Microsoft Docs
description: Visa och hantera konfigurationsprofilen för enheter i Microsoft Intune, visa en grafisk karta över antalet enheter som är tilldelade till en profil och se vilka enheter som har profiler tilldelade eller distribuerade. Kan även felsöka profiler som har inställningar i konflikt.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1c68421bf7c5dea0d93d45e0cbb748204d0f66b
ms.sourcegitcommit: c2e62f1ebdf75599c8e544287123c602f0f15f2b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72749411"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Övervaka enhetsprofiler i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune innehåller några funktioner som hjälper dig att övervaka och hantera dina enhetskonfigurationsprofiler. Du kan exempelvis kontrollera statusen för en profil, se vilka enheter som är tilldelade och uppdatera egenskaperna för en profil.

## <a name="view-existing-profiles"></a>Visa befintliga profiler

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler**.

Alla dina befintliga profiler visas, innehåller information såsom plattform och visar om profilen har tilldelats till några enheter.

## <a name="view-details-on-a-profile"></a>Visa information om en profil

När du har skapat din enhetsprofil tillhandahåller Intune grafiska diagram. Dessa diagram visar status för en profil, som t.ex. om den har tilldelats till enheter korrekt eller om profilen visar en konflikt.

1. Välj en befintlig profil. Välj till exempel en macOS-profil.
2. Välj fliken **Översikt**.

    Det övre diagrammet visar det antal enheter som är tilldelade till enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för macOS-enheter, visar diagrammet antal macOS-enheter.

    Det visar även antalet enheter för andra plattformar som tilldelats samma enhetsprofil. Till exempel visar det antalet enheter som inte är macOS-enheter.

    ![Visa antalet enheter som tilldelats enhetsprofilen](./media/device-profile-monitor/device-configuration-profile-graphical-chart.png)

    Det nedre diagrammet visar det antal användare som är tilldelade till enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för macOS-användare visar diagrammet antalet macOS-användare.

3. Välj cirkeln i det övre grafiska diagrammet. **Enhetstillstånd** öppnas.

    Enheter som är tilldelade till profilen visas samt om profilen har distribuerats korrekt. Tänk också på att bara enheterna med den specifika plattformen visas (till exempel macOS).

    Stäng **statusinformationen** för enheten.

4. Välj cirkeln i det undre grafiska diagrammet. **Användarstatus** öppnas. 

    Användare som är tilldelade till profilen visas samt om profilen har distribuerats korrekt. Tänk också på att bara användarna med den specifika plattformen visas (till exempel macOS).

    Stäng **statusinformationen** för användarna.

5. Välj en profil i listan **Profiler**. Du kan också ändra befintliga egenskaper:
    - **Egenskaper**: Ändra namnet eller uppdatera befintliga inställningar.
    - **Tilldelningar**: Inkludera eller undanta enheter som principen ska gälla för. Välj **Valda grupper** för att välja särskilda enhetsgrupper.
    - **Enhetsstatus**: Enheter som är tilldelade till profilen visas samt om profilen har distribuerats korrekt. Du kan välja en specifik enhet för att få ytterligare information, inklusive installerade appar.
    - **Användarstatus**: Visar de användarnamn med enheter som påverkas av den här profilen samt huruvida profilen har distribuerats. Du kan välja en specifik användare för att få ytterligare information.
    - **Status per inställning**: Filtrerar resultatet genom att visa de enskilda inställningarna i profilen, samt om inställningen har tillämpats.

## <a name="view-conflicts"></a>Visa konflikter

I **Enheter** > **Alla enheter** kan du se alla inställningar som orsakar en konflikt. När det finns en konflikt ser du även alla konfigurationsprofiler som innehåller den här inställningen. Administratörer kan använda funktionen till att felsöka och åtgärda avvikelser med profilerna.

1. Välj i Intune **Enheter** > **Alla enheter** > välj en befintlig enhet i listan. Slutanvändare kan få enhetsnamnet från appen Företagsportal.
2. Välj **Enhetskonfiguration**. Alla konfigurationsprinciper som gäller för enheten listas.
3. Välj principen. Här visas alla inställningar i den principen som gäller för enheten. Om en enhet är i **konflikt** väljer du den raden. I det nya fönstret visas alla profiler och namnen på de profiler som har inställningen som orsakar konflikten.

Nu när du känner till inställningen som orsakar konflikten och vilka principer som innehåller den inställningen bör det vara lättare att lösa konflikten. 

## <a name="device-firmware-configuration-interface-profile-reporting"></a>Rapportering för konfigurationsgränssnittsprofil för enhetens inbyggda programvara

> [!WARNING]
> Övervakning av DFCI-profiler håller just nu på att skapas. Medan DFCI är i offentlig förhandsversion kan övervakningsdata saknas eller vara ofullständiga.

DFCI-profiler rapporteras per inställning, precis som andra enhetskonfigurationsprofiler. Beroende på tillverkarens stöd för DFCI gäller kanske inte vissa inställningar.

Med dina DFCI-profilinställningar visas kanske följande tillstånd:

- **Kompatibel**: Det här tillståndet visar när ett inställningsvärde i profilen matchar inställningen på enheten. Det här tillståndet kan inträffa i följande scenarier:

  - DFCI-profilen har konfigurerat inställningen i profilen.
  - Enheten har inte den maskinvarufunktion som styrs av inställningen, och profilinställningen är **Inaktiverad**.
  - UEFI tillåter inte att DFCI inaktiverar funktionen, och profilinställningen är **Aktiverad**.
  - Enheten saknar maskinvara för att inaktivera funktionen, och profilinställningen är **Aktiverad**.

- **Inte tillämpligt**: Det här tillståndet visar när ett inställningsvärde i profilen är **Aktiverat** och den matchande inställningen på enheten inte hittas. Detta tillstånd kan inträffa om enhetens maskinvara inte har funktionen.

- **Inkompatibel**: Det här tillståndet visar när ett inställningsvärde i profilen inte matchar inställningen på enheten. Det här tillståndet kan inträffa i följande scenarier:

  - UEFI tillåter inte att DFCI inaktiverar en inställning, och profilinställningen är **Inaktiverad**.
  - Enheten saknar maskinvara för att inaktivera funktionen, och profilinställningen är **Inaktiverad**.
  - Enheten har inte den senaste versionen av den inbyggda DFCI-programvaran.
  - DFCI inaktiverades innan det registrerades i Intune med hjälp av en lokal ”bortvals”-kontroll i UEFI-menyn.
  - Enheten registrerades till Intune utanför Autopilot-registreringen.
  - Enheten registrerades inte till Autopilot av en Microsoft-CSP, eller registrerades direkt av OEM-tillverkaren.

## <a name="next-steps"></a>Nästa steg

[Vanliga frågor, problem och lösningar med enhetsprofiler](device-profile-troubleshoot.md)  
[Felsöka principer och profiler i Intune](troubleshoot-policies-in-microsoft-intune.md)
