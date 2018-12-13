---
title: Enheten saknar ett certifikat som krävs | Microsoft Docs
titlesuffix: Microsoft Intune
description: Android-enheten saknar ett certifikat som företagets support kräver.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser; seodec18
ms.openlocfilehash: e40ac2fd81375b84084dd229f4cb5a6ab3e9915f
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032222"
---
# <a name="your-device-is-missing-a-required-certificate"></a>Enheten saknar ett certifikat som krävs

## <a name="whats-a-certificate"></a>Vad är ett certifikat?

[Kryptografi](https://technet.microsoft.com/library/cc962030.aspx) är läran om informationssäkerhet. Traditionellt har kryptografi använts för att överföra kodade meddelanden för att [säkerställa att kommunikation förblir hemlig](https://technet.microsoft.com/library/cc962019.aspx). I sin enklaste form ersätter eller flyttar kryptografi om bokstäver för att skapa ett meddelande som är kodat, oläsbart, förvrängt eller dolt. Endast användare med en avkodningsnyckel eller _certifikat_ kan omvandla det kodade meddelandet till sin ursprungliga, läsbara form. Din Android-enhet använder certifikat tillsammans med Intune för att se till att kommunikationen mellan enheten och din organisations resurser, t.ex e-post och dokument, hela tiden hålls säker när den överförs trådlöst.

## <a name="fixing-certificate-issues"></a>Åtgärda problem med certifikat

Om Android-enheten inte har registrerats i Intune och den saknar ett certifikat som krävs av företagets support kan du inte logga in på företagsportalappen. Följande meddelande visas när du försöker logga in:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Det första steget du ska ta är att se om enheten [saknar ett certifikat som vanligtvis är förinstallerat på den](your-device-is-missing-a-preinstalled-certificate-android.md).

Om detta inte löser problemen med certifikat kan företagets support [kräva att du installerar ett certifikat till för ytterligare säkerhet](your-device-is-missing-an-IT-required-certificate-android.md).

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
