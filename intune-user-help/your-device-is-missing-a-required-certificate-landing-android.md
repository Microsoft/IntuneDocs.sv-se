---
title: "Enheten saknar ett certifikat som krävs | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 910fe2bc4e616c3b60d351efaffe173f58c04bc6
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="your-device-is-missing-a-required-certificate"></a>Enheten saknar ett certifikat som krävs

## <a name="whats-a-certificate"></a>Vad är ett certifikat?

[Kryptografi](https://technet.microsoft.com/library/cc962030.aspx) är läran om informationssäkerhet. Traditionellt har kryptografi använts för att överföra kodade meddelanden för att [säkerställa att kommunikation förblir hemlig](https://technet.microsoft.com/library/cc962019.aspx). I sin enklaste form ersätter eller flyttar kryptografi om bokstäver för att skapa ett meddelande som är kodat, oläsbart, förvrängt eller dolt. Endast användare med en avkodningsnyckel eller _certifikat_ kan omvandla det kodade meddelandet till sin ursprungliga, läsbara form. Din Android-enhet använder certifikat tillsammans med Intune för att se till att kommunikationen mellan enheten och din organisations resurser, t.ex e-post och dokument, hela tiden hålls säker när den överförs trådlöst.

## <a name="fixing-certificate-issues"></a>Åtgärda problem med certifikat

Om Android-enheten inte har registrerats i Intune och den saknar ett certifikat som krävs av IT-administratören kan du inte logga in på företagsportalappen. Följande meddelande visas när du försöker logga in:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Det första steget du ska ta är att se om enheten [saknar ett certifikat som vanligtvis är förinstallerat på den](your-device-is-missing-a-preinstalled-certificate-android.md).

Om detta inte fungerar kan IT-administratören [kräva att du måste installera ett andra certifikat för ytterligare säkerhet](your-device-is-missing-an-IT-required-certificate-android.md).

Behöver du fortfarande hjälp? Kontakta IT-administratören. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).
