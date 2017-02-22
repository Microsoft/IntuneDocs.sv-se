---
title: "Begränsningar i Intune-enheter för Windows 10 Team | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Lär dig mer om enhetsbegränsningar som är tillgängliga för Windows 10 Team-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6e0540acd5488077ae5217f8862e3bc5462ed71
ms.openlocfilehash: 342681922944fd1ea4be6aa4ddcb0725f6cfd42b


---

# <a name="windows-10-team-device-restriction-settings-in-intune-azure-preview"></a>Inställning av enhetsbegränsningar för Windows 10 Team-enheter i förhandsversionen av Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

- **Aktivera skärm när någon är i rummet** – Tillåter att enheten aktiveras automatiskt när dess sensor känner av att någon är i rummet.
- **PIN-kod för trådlös projektion** – Anger om du måste ange en PIN-kod innan du kan använda funktionerna för trådlös projektion för enheten.
- **Trådlös Miracast-projektion** – Aktivera det här alternativet om du vill att Windows 10 Team-enheten ska kunna använda Miracast-aktiverade enheter för att projicera innehåll.
- **Mötesinformation som visas på välkomstskärmen** – Aktivera det här alternativet för att välja den information som ska visas i rutan Möten på välkomstskärmen. Du kan:
    - **Visa endast kalender och tid**
    - **Visa kalender, tid och ämne (ämnet är dolt för privata möten)**
- **Webbadress till bakgrundsbild för välkomstskärm** – Aktivera den här inställningen om du vill visa en anpassad bakgrund på **välkomstskärmen** på Windows 10 Team-enheter från den webbadress som du anger.<br>Bilden måste vara i PNG-format och webbadressen måste börja med **https://**.
- **Underhållsperiod för programuppdateringar ** – Konfigurerar tidsperioden då uppdateringar till enheten kan göras. Du kan konfigurera starttiden och varaktigheten (mellan 1–5 timmar).
- **Åtgärdsinformation i Azure** – Åtgärdsinformation i Azure är en del av Microsoft Operations Manager-programsviten och samlar in, lagrar och analyserar loggfilsdata från Windows 10 Team-enheter.<br>Om du vill kunna ansluta till Azure-åtgärdsinformationen måste du ange ett **Arbetsyte-ID** och en **Arbetsytenyckel**.



<!--HONumber=Feb17_HO1-->


