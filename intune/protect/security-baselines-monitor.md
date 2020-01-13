---
title: Kontrollera framgångar eller misslyckanden med säkerhetsbaslinjer i Microsoft Intune – Azure | Microsoft Docs
description: Kontrollera status för fel, konflikter och framgångar när du distribuerar säkerhetsbaslinjer till användare och enheter i Microsoft Intune MDM. Se hur du felsöker med klientloggar och rapportfunktioner i Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbf82c0bef88e4a6d0e790f4b0ecdf73d2731d5d
ms.sourcegitcommit: 9bb1bcd9f1bdd53b470073da956bbd8b0935dfbc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556410"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>Övervaka säkerhetsbaslinje och profil i Microsoft Intune

Intune tillhandahåller flera alternativ för att övervaka dina säkerhetsbaslinjer. Du kan övervaka den profil för säkerhetsbaslinjer som gäller för dina användare och enheter. Du kan också övervaka den faktiska baslinjen och alla enheter som matchar (eller inte matchar) de rekommenderade värdena.

Den här artikeln beskriver båda övervakningsalternativen.

[Säkerhetsbaslinjer i Intune](../security-baselines.md) innehåller mer information om funktionen säkerhetsbaslinjer i Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Övervaka baslinjen och dina enheter

När du övervakar en baslinje kan få du inblick i säkerhetstillståndet för dina enheter baserat på Microsofts rekommendationer. Du kan visa de insikterna från översiktsfönstret för säkerhetsbaslinjen i Intune-konsolen.  Det tar upp till 24 timmar innan data visas när du först har tilldelat en baslinje. Senare ändringar tar upp till sex timmar att visas.

Om du vill se övervakningsdata för baslinjen och enheterna loggar du in på [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Sedan väljer du **Slutpunktssäkerhet** > **Säkerhetsbaslinjer**, en baslinje och öppnar fönstret **Översikt**.

I fönstret **Översikt** finns två metoder för att övervaka status:

- **Enhetsvy** – en sammanfattning av hur många enheter som finns i varje statuskategori för baslinjen.
- **Per kategori** – en vy som visar varje kategori i baslinjen och innehåller procentandelen enheter för varje statusgrupp för varje baslinjekategori.

Varje enhet visas med någon av följande statusar (som används i både *enhetsvyn* och *per kategori-vyerna*):

- **Matchar baslinjen** – alla inställningarna i baslinjen överensstämmer med de rekommenderade inställningarna.
- **Matchar inte baslinjen** – minst en inställning i baslinjen matchar inte den rekommenderade inställningen.

  > [!NOTE]
  > När du skapar eller redigerar en baslinjeprofil, gör alla ändringar av ett standardvärde eller en konfigurationsinställning att statusen "Matchar inte baslinjen" visas. Kontakta Microsoft Support om du vill ha hjälp med att avgöra vilka inställningar som har ändrats. 

- **Felkonfigurerad** – minst en inställning har inte konfigurerats korrekt. Denna status innebär att inställningen är i en konflikt, fel eller i ett väntande tillstånd.
- **Ej tillämpligt** – minst en inställning är inte tillämplig och används inte.

### <a name="device-view"></a>Enhetsvyn

I översiktsfönstret visas en diagrambaserad sammanfattning av hur många enheter som har en viss status för baslinjen: **Säkerhetsbaslinjeposition för tilldelade Windows 10-enheter**.

![Kontrollera enheternas status](./media/security-baselines-monitor/overview.png)

När en enhet har olika status från olika kategorier i baslinjen representeras enheten av en enda status. Den status som representerar enheten hämtas från följande prioritetsordning: **Felkonfigurerad**, **Matchar inte baslinjen**, **Ej tillämpligt**, **Matchar baslinjen**.

Om en enhet till exempel har en inställning klassificerad som *Felkonfigurerad* och en eller flera inställningar klassificerade som *Matchar inte baslinjen* så klassificeras enheten som *Felkonfigurerad*.

Du kan klicka på diagrammet för att visa detaljerad information och en lista över enheter med olika statusar. Sedan kan du välja enskilda enheter från den listan för att visa information om enskilda enheter. Exempel:

- Välj **Enhetskonfiguration** > Välj profilen med ett feltillstånd:

  ![Visa status för en profil](./media/security-baselines-monitor/device-configuration-profile-list.png)

- Välj felprofilen. En lista över alla inställningar i profilen, samt deras status visas. Du kan nu bläddra för att hitta den inställning som orsakar felet:

  ![Visa inställningen som orsakar felet](./media/security-baselines-monitor/profile-with-error-status.png)

Använd den här rapporteringen för att se alla inställningar i en profil som orsakar problem. Få även mer information om principer och profiler som distribuerats till enheter.

> [!NOTE]
> När en egenskap är inställd till **Inte konfigurerad** ignoreras inställningen i baslinjen och inga begränsningar tillämpas. Egenskapen visas inte i någon rapportering.

### <a name="per-category-view"></a>Per kategori-vy

I översiktsfönstret visas ett per kategori-diagram för baslinjen: **Säkerhetsbaslinjeposition efter kategori**.  Den här vyn visar varje kategori från baslinjen och identifierar procentandelen enheter som faller inom en statusklassificering för var och en av dessa kategorier.

![Per kategori-vy över status](./media/security-baselines-monitor/monitor-baseline-per-category.png)

Status för **Matchar baslinjen** visas inte förrän 100 % av enheterna rapporterar den statusen för kategorin.

Du kan sortera per kategori-vyn efter varje kolumn genom att välja uppåt-nedåt-pilikonen överst i kolumnen.

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
> - Loggboken kan också innehålla viss felinformation om den problematiska inställningen (**Loggboken** > **Applikationer och tjänsteloggar** >  **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**).

## <a name="next-steps"></a>Nästa steg

[Övervaka enhetsprofiler](../configuration/device-profile-monitor.md) och [visa vissa vanliga problem och lösningar](../configuration/device-profile-troubleshoot.md).
