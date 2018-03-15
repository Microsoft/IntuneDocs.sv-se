---
title: Visa Intunes enhetsinventering
titlesuffix: Azure portal
description: "Lär dig hur du visar de enheter som du hanterar med Intune, samt hur deras maskinvara och installerade appar fungerar.\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 772e2b1380626384d618e653b90b31a1f421eb72
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-view-intune-device-inventory"></a>Så här visar du Intunes enhetsinventering


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med arbetsbelastningen **Enheter** kan du få mer information om enheterna du hanterar, inklusive deras maskinvarukapacitet och de appar som är installerade på dem. 

Så här visar du enhetsinventeringen:

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enheter** på bladet **Intune**.

Välj nu något av följande alternativ:

- **Översikt** – Hämta information om enheter som du har registrerat och operativsystemen som körs för varje enhet.
- **Hantera** – Välj **Alla enheter** för att se en lista med alla enheter som du hanterar.
    Välj en av enheterna i listan för att öppna bladet <*enhetsnamn*> **Översikt** där du kan välja:
    - **Översikt** – Visa allmän information om enheten, inklusive dess namn, ägare, om det är en BYOD-enhet, om den är incheckad och mycket annat.
    - **Maskinvara** – Visa mer detaljerad information om enheten, inklusive dess lediga lagringsutrymme, modell, tillverkare och mycket annat.
    - **Identifierade appar** – Visar en lista över alla appar som Intune hittar installerade på enheten.
    - **Enhetsefterlevnad** – Visar kompatibilitetsstatus för alla efterlevnadsprinciper som tilldelats enheten.
    - **Enhetskonfiguration** – Visar kompatibilitetsstatus för alla enhetskonfigurationsprinciper som tilldelats enheten.
- **Övervaka**– Välj **Enhetsåtgärder** för att se en lista med enhetsåtgärder som har utförts på de enheter du hanterar, samt enheternas aktuella status.
- **Konfigurera** > **TeamViewer Connector** – Konfigurera fjärradministration på enheter med hjälp av programmet TeamViewer. Mer information finns i [Ge fjärrhjälp för Intune-hanterade Android-enheter](/intune/device-profile-android-teamviewer).

Intune samlar endast in appinformation från företagsägda enheter. Ingen appinformation samlas in från personliga enheter. För datorer med Windows 10 samlas endast modern appinformation in från företagsägda enheter. Intune samlar inte in information om Win32-appar på enheten. Beroende på vilken operatör du använder med enheterna, är det inte säkert att alla lagerobjekt kan samlas in.
