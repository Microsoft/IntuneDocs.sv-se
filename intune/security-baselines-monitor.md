---
title: Kontrollera framgångar eller misslyckanden med säkerhetsbaslinjer i Microsoft Intune – Azure | Microsoft Docs
description: Kontrollera status för fel, konflikter och framgångar när du distribuerar säkerhetsbaslinjer till användare och enheter i Microsoft Intune MDM. Se hur du felsöker med klientloggar och rapportfunktioner i Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfbdad6d98065a691528d4cdada0b6f9377e1109
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848244"
---
# <a name="monitor-the-security-baseline-and-profile-in-microsoft-intune"></a>Övervaka säkerhetsbaslinje och profil i Microsoft Intune

Det finns olika alternativ för övervakning när du använder säkerhetsbaslinjer. Du kan övervaka den profil för säkerhetsbaslinjer som gäller för dina användare och enheter. Du kan också övervaka den faktiska baslinjen och alla enheter som matchar (eller inte matchar) de rekommenderade värdena.

Den här artikeln beskriver båda övervakningsalternativen.

[Säkerhetsbaslinjer i Intune](security-baselines.md) innehåller mer information om funktionen säkerhetsbaslinjer i Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Övervaka baslinjen och dina enheter

När du övervakar baslinjen kan få du inblick i säkerhetstillståndet för dina enheter baserat på Microsofts rekommendationer.

> [!NOTE]
> När en baslinje har tilldelats första gången kan rapporter ta upp till 24 timmar att uppdatera. Därefter kan de ta upp till 6 timmar att uppdatera.

1. I [Azure-portalen](https://portal.azure.com/) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Säkerhetsbaslinjer (förhandsversion)** > välj en baslinje.
3. I **Översikt**, visar diagrammet hur många enheter som påverkas av den baslinje som du har valt, och de olika statuslägena:

    ![Kontrollera enheternas status](./media/security-baselines-monitor/overview.png)

    Följande statusar är tillgängliga:

    - **Matchar baslinjen**: Alla inställningarna i baslinjen överensstämmer med de rekommenderade inställningarna.
    - **Matchar inte baslinjen**: Minst en inställning i baslinjen matchar inte de rekommenderade inställningarna.
    - **Felkonfigurerad**: Minst en inställning har inte konfigurerats korrekt. Denna status innebär att inställningen är i en konflikt, fel eller i ett väntande tillstånd.
    - **Ej tillämpligt**: Minst en inställning är inte tillämplig och används inte.

4. Välj en av de statusar som har enheter. Välj till exempel statusen **Felkonfigurerad**.

5. En lista över alla enheter med denna status visas. Välj en specifik enhet för att få mer information. 

    I följande exempel väljer du **Enhetskonfiguration** > Välj profilen med ett feltillstånd:

    ![Kontrollera enheternas status](./media/security-baselines-monitor/device-configuration-profile-list.png)

    Välj felprofilen. En lista över alla inställningar i profilen, samt deras status visas. Du kan nu bläddra för att hitta den inställning som orsakar felet:

    ![Visa inställningen som orsakar felet](./media/security-baselines-monitor/profile-with-error-status.png)

Använd den här rapporteringen för att se alla inställningar i en profil som orsakar problem. Få även mer information om principer och profiler som distribuerats till enheter.

> [!NOTE]
> När en egenskap är inställd till **Inte konfigurerad** ignoreras inställningen i baslinjen och inga begränsningar tillämpas. Egenskapen visas inte i någon rapportering.

## <a name="monitor-the-profile"></a>Övervaka profilen

Övervakning av profilen ger dig insikt i distributionsstatusen för dina enheter, men inte säkerhetsstatusen baserad på baslinjerekommendationerna.

1. I Intune väljer du **Säkerhetsbaslinjer** > välj en baslinje > **Profiler skapade**.

2. Välj en profil. I **Översikt** visar bilden hur många enheter och användare som har den här profilen tilldelad:

    ![Se hur många enheter och användare som är tilldelade profilen för säkerhetsbaslinjer](./media/security-baselines-monitor/existing-profile-overview.png)

3. Under **Hantera** > **Egenskaper**, visas en lista över alla inställningar i baslinjen. Du kan också ändra någon av dessa inställningar:

    ![Visa och uppdatera inställningarna i profilen för säkerhetsbaslinjer](./media/security-baselines-monitor/manage-settings.png)

4. I **Övervakare**, kan du se distributionsstatusen för profilen på enskilda enheter, status för varje användare och status för varje inställning i baslinjen:

    ![Se de olika alternativen för övervakare för en profil för säkerhetsbaslinjer](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>Felsök med hjälp av status per inställning

Du har distribuerat en säkerhetsbaslinje, men distributionsstatusen visar ett fel. I följande steg får du vägledning om hur du felsöker felet.

1. I Intune väljer du **Säkerhetsbaslinjer** > välj en baslinje > **Profiler skapade**.
2. Välj en profil > under **Övervakare** > **Status per inställning**.
3. Tabellen visar alla inställningar och status för varje inställning. Välj kolumnen **Fel** eller **Konflikt** för att se inställningen som orsakar felet.

### <a name="mdm-diagnostic-information"></a>MDM-diagnostikinformation

Nu vet du vilken den problematiska inställningen är. Nästa steg är att ta reda på varför den här inställningen orsakar ett fel eller en konflikt. 

På Windows 10-enheter finns det en inbyggd rapport för MDM-diagnostikinformation. Den här rapporten innehåller standardvärden, aktuella värden, visar en lista över principen, visar om den har distribuerats till enheten eller användaren och mycket mer. Använd den här rapporten för att avgöra varför inställningen orsakar en konflikt eller ett fel.

1. På enheten, gå till **Inställningar** > **Konton** > **Åtkomst till arbete eller skola**.
2. Välj kontot > **Info** > **Avancerad diagnostikrapport** > **Skapa rapport**.
3. Välj **Exportera** och öppna den genererade filen.
4. I rapporten kan du leta efter fel- eller konfliktinställningen i de olika avsnitten i rapporten.

  Titta till exempel i avsnittet **Registrerade konfigurationskällor och målresurser** eller **Ohanterade principer**. Du kan få en uppfattning om varför den orsakar ett fel eller en konflikt.

[Diagnostisera fel i MDM i Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) ger mer information om den här inbyggda rapporten.

> [!TIP]
> - Vissa inställningar visar även GUID. Du kan söka efter detta GUID i det lokala registret (regedit) för alla inställda värden.
> - Loggboken kan också innehålla viss felinformation om den problematiska inställningen (**Loggboken** > **Applikationer och tjänsteloggar**  >   **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**).

## <a name="next-steps"></a>Nästa steg

[Övervaka enhetsprofiler](device-profile-monitor.md) och [visa vissa vanliga problem och lösningar](device-profile-troubleshoot.md).
