---
title: "Enhetsbegränsningar för Windows 10 Team-enheter i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig mer om enhetsbegränsningar som är tillgängliga för Windows 10 Team-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 4df8afe50912912e42e03b6b9bc1c397fff2d6db
ms.contentlocale: sv-se
ms.lasthandoff: 02/18/2017


---

# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Inställningar för begränsningar för Windows 10 Team-enheter i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

- **Aktivera skärm när någon är i rummet** – Tillåter att enheten aktiveras automatiskt när dess sensor känner av att någon är i rummet.
- **PIN-kod för trådlös projektion** – Anger om du måste ange en PIN-kod innan du kan använda funktionerna för trådlös projektion för enheten.
- **Trådlös Miracast-projektion** – Aktivera det här alternativet om du vill att Windows 10 Team-enheten ska kunna använda Miracast-aktiverade enheter för att projicera innehåll.
- **Mötesinformation som visas på välkomstskärmen** – Aktivera det här alternativet för att välja den information som ska visas i rutan Möten på välkomstskärmen. Du kan:
    - **Visa endast kalender och tid**
    - **Visa kalender, tid och ämne (ämnet är dolt för privata möten)**
- **Webbadress till bakgrundsbild för välkomstskärm** – Aktivera den här inställningen om du vill visa en anpassad bakgrund på **välkomstskärmen** på Windows 10 Team-enheter från den webbadress som du anger.<br>Bilden måste vara i PNG-format och webbadressen måste börja med **https://**.
- **Underhållsperiod för programuppdateringar** – Konfigurerar tidsperioden då uppdateringar till enheten kan göras. Du kan konfigurera starttiden och varaktigheten (mellan 1–5 timmar).
- **Åtgärdsinformation i Azure** – Åtgärdsinformation i Azure är en del av Microsoft Operations Manager-programsviten och samlar in, lagrar och analyserar loggfilsdata från Windows 10 Team-enheter.<br>Om du vill kunna ansluta till Azure-åtgärdsinformationen måste du ange ett **Arbetsyte-ID** och en **Arbetsytenyckel**.

