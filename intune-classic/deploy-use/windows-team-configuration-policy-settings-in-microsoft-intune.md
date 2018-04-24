---
title: Inställningar för Windows Team-konfigurationsprincip
description: Använd Microsoft Intunes **allmänna Windows 10 Team-konfigurationsprincip** om du vill konfigurera inställningar för registrerade Windows 10 Team-enheter som Microsoft Surface Hub.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 70b1091cd58439b7d42eab1a612b0b63ca39103d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Inställningar för Windows Team-konfigurationsprincip i Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Använd Microsoft Intunes **allmänna Windows 10 Team-konfigurationsprincip** om du vill konfigurera inställningar för registrerade Windows 10 Team-enheter som Microsoft Surface Hub.


|                                  Inställningsnamn                                   |                                                                                                                                                                Information                                                                                                                                                                |
|---------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <strong>Låt skärmen aktiveras automatiskt när någon är i rummet</strong>   |                                                                                                                         Tillåter att enheten aktiveras automatiskt när dess sensor känner av att någon är i rummet.                                                                                                                          |
|              <strong>Kräv PIN-kod för trådlös projektion</strong>               |                                                                                                             Anger om du måste ange en PIN-kod innan du kan använda funktionerna för trådlös projektion för enheten.                                                                                                             |
|          <strong>Ange en underhållsperiod för enhetsuppdateringar</strong>           |                                                                                          Konfigurerar tidsperioden då uppdateringar till enheten kan göras. Du kan konfigurera starttiden och varaktigheten (mellan 1–5 timmar).                                                                                           |
|               
  <strong>Aktivera Operational Insights i Azure</strong>                |                  Operational Insights i Azure är en del av Microsoft Operations Manager-programsviten och samlar in, lagrar och analyserar loggfilsdata från Windows 10 Team-enheter.<br /><br />Om du vill kunna ansluta till Azure Operational Insights måste du ange ett <strong>Arbetsyte-ID</strong> och en <strong>Arbetsytenyckel</strong>.                   |
|              <strong>Aktivera trådlös Miracast-projektion</strong>               |                                          Aktivera det här alternativet om du vill att Windows 10 Team-enheten ska kunna använda Miracast-aktiverade enheter för att projicera innehåll.<br /><br />Om du aktiverar det här alternativet från <strong>Välj Miracast-kanal</strong> väljer du den Miracast-kanal som används för att projicera innehåll.                                           |
| <strong>Välj den mötesinformation som ska visas på välkomstskärmen</strong> | Om du aktiverar det här alternativet kan du välja den information som ska visas i rutan <strong>Möten</strong> på <strong>välkomstskärmen</strong>. Du kan:<br /><br />-   <strong>Visa endast kalender och tid</strong><br />-   <strong>Visa kalender, tid och ämne (ämnet är dolt för privata möten)</strong> |
|                <strong>Webbadress till bakgrundsbild för låsskärm</strong>                 |                                           Aktivera den här inställningen om du vill visa en anpassad bakgrund på <strong>välkomstskärmen</strong> på Windows 10 Team-enheter från den webbadress som du anger.<br /><br />Bilden måste vara i PNG-format och webbadressen måste börja med <strong>https://</strong>.                                            |

### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

