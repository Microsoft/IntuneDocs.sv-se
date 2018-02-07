---
title: "Enheten saknar ett certifikat som krävs | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 7c454584df4f0eb6b3a9dfe10ee7b887bcdee2ca
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="your-device-is-missing-a-required-certificate"></a>Enheten saknar ett certifikat som krävs

## <a name="whats-a-certificate"></a>Vad är ett certifikat?

[Kryptografi](https://technet.microsoft.com/library/cc962030.aspx) är läran om informationssäkerhet. Traditionellt har kryptografi använts för att överföra kodade meddelanden för att [säkerställa att kommunikation förblir hemlig](https://technet.microsoft.com/library/cc962019.aspx). I sin enklaste form ersätter eller flyttar kryptografi om bokstäver för att skapa ett meddelande som är kodat, oläsbart, förvrängt eller dolt. Endast användare med en avkodningsnyckel eller _certifikat_ kan omvandla det kodade meddelandet till sin ursprungliga, läsbara form. Din Android-enhet använder certifikat tillsammans med Intune för att se till att kommunikationen mellan enheten och din organisations resurser, t.ex e-post och dokument, hela tiden hålls säker när den överförs trådlöst.

## <a name="fixing-certificate-issues"></a>Åtgärda problem med certifikat

Om Android-enheten inte har registrerats i Intune och den saknar ett certifikat som krävs av företagets support kan du inte logga in på företagsportalappen. Följande meddelande visas när du försöker logga in:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Det första steget du ska ta är att se om enheten [saknar ett certifikat som vanligtvis är förinstallerat på den](your-device-is-missing-a-preinstalled-certificate-android.md).

Om detta inte fungerar kan företagets support [kräva att du installerar ett andra certifikat för ytterligare säkerhet](your-device-is-missing-an-IT-required-certificate-android.md).

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
