---
title: "Inställningar för Windows Team-konfigurationsprincip| Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: b08d52289b94429b1328a7470469a7efdf4d46a7


---

# Inställningar för Windows Team-konfigurationsprincip i Microsoft Intune
Använd Microsoft Intunes **allmänna Windows 10 Team-konfigurationsprincip** om du vill konfigurera inställningar för registrerade Windows 10 Team-enheter som Microsoft Surface Hub.

|Inställningsnamn|Information|
|----------------|-----------|
|**Låt skärmen aktiveras automatiskt när någon är i rummet**|Tillåter att enheten aktiveras automatiskt när dess sensor känner av att någon är i rummet.|
|**Kräv PIN-kod för trådlös projektion**|Anger om du måste ange en PIN-kod innan du kan använda funktionerna för trådlös projektion för enheten.|
|**Ange en underhållsperiod för enhetsuppdateringar**|Konfigurerar tidsperioden då uppdateringar till enheten kan göras. Du kan konfigurera starttiden och varaktigheten (mellan 1–5 timmar).|
|**Aktivera Åtgärdsinformation i Azure**|Åtgärdsinformation i Azure är en del av Microsoft Operations Manager-programsviten och samlar in, lagrar och analyserar loggfilsdata från Windows 10 Team-enheter.<br /><br />Om du vill kunna ansluta till Azure-åtgärdsinformationen måste du ange ett **Arbetsyte-ID** och en **Arbetsytenyckel**.|
|**Aktivera trådlös Miracast-projektion**|Aktivera det här alternativet om du vill att Windows 10 Team-enheten ska kunna använda Miracast-aktiverade enheter för att projicera innehåll.<br /><br />Om du aktiverar det här alternativet från **Välj Miracast-kanal** väljer du den Miracast-kanal som används för att projicera innehåll.|
|**Välj den mötesinformation som ska visas på välkomstskärmen**|Om du aktiverar det här alternativet kan du välja den information som ska visas i rutan **Möten** på **välkomstskärmen**. Du kan:<br /><br />-   **Visa endast kalender och tid**<br />-   **Visa kalender, tid och ämne (ämnet är dolt för privata möten)**|
|**Webbadress till bakgrundsbild för låsskärm**|Aktivera den här inställningen om du vill visa en anpassad bakgrund på **välkomstskärmen** på Windows 10 Team-enheter från den webbadress som du anger.<br /><br />Bilden måste vara i PNG-format och webbadressen måste börja med **https://**.|


### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


