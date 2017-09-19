---
title: "Inställningar för Windows Team-konfigurationsprincip"
description: "Använd Microsoft Intunes **allmänna Windows 10 Team-konfigurationsprincip** om du vill konfigurera inställningar för registrerade Windows 10 Team-enheter som Microsoft Surface Hub."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d8d0ec02fccd7aff391d794f4db4c5c2db03c4dd
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Inställningar för Windows Team-konfigurationsprincip i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Använd Microsoft Intunes **allmänna Windows 10 Team-konfigurationsprincip** om du vill konfigurera inställningar för registrerade Windows 10 Team-enheter som Microsoft Surface Hub.

|Inställningsnamn|Information|
|----------------|-----------|
|**Låt skärmen aktiveras automatiskt när någon är i rummet**|Tillåter att enheten aktiveras automatiskt när dess sensor känner av att någon är i rummet.|
|**Kräv PIN-kod för trådlös projektion**|Anger om du måste ange en PIN-kod innan du kan använda funktionerna för trådlös projektion för enheten.|
|**Ange en underhållsperiod för enhetsuppdateringar**|Konfigurerar tidsperioden då uppdateringar till enheten kan göras. Du kan konfigurera starttiden och varaktigheten (mellan 1–5 timmar).|
|**Aktivera Åtgärdsinformation i Azure**|Azure Operational Insights är en del av Microsoft Operations Manager-programsviten och samlar in, lagrar och analyserar loggfilsdata från Windows 10 Team-enheter.<br /><br />Om du vill kunna ansluta till Azure-åtgärdsinformationen måste du ange ett **Arbetsyte-ID** och en **Arbetsytenyckel**.|
|**Aktivera trådlös Miracast-projektion**|Aktivera det här alternativet om du vill att Windows 10 Team-enheten ska kunna använda Miracast-aktiverade enheter för att projicera innehåll.<br /><br />Om du aktiverar det här alternativet från **Välj Miracast-kanal** väljer du den Miracast-kanal som används för att projicera innehåll.|
|**Välj den mötesinformation som ska visas på välkomstskärmen**|Om du aktiverar det här alternativet kan du välja den information som ska visas i rutan **Möten** på **välkomstskärmen**. Du kan:<br /><br />-   **Visa endast kalender och tid**<br />-   **Visa kalender, tid och ämne (ämnet är dolt för privata möten)**|
|**Webbadress till bakgrundsbild för låsskärm**|Aktivera den här inställningen om du vill visa en anpassad bakgrund på **välkomstskärmen** på Windows 10 Team-enheter från den webbadress som du anger.<br /><br />Bilden måste vara i PNG-format och webbadressen måste börja med **https://**.|


### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

