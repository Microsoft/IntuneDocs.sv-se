---
title: Visa Intunes enhetsinventering
titlesuffix: Azure portal
description: "Lär dig hur du visar de enheter som du hanterar med Intune, samt hur deras maskinvara och installerade appar fungerar.\""
keywords: 
author: arob98
ms.author: angrobe
nmanager: angrobe
ms.date: 11/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 17916d513b338716a62f165545bdf44a3216bbe9
ms.sourcegitcommit: ca10ab40fe40e5c9f4b6f6f4950b551eecf4aa03
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="how-to-view-intune-device-inventory"></a>Så här visar du Intunes enhetsinventering


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med arbetsbelastningen **Enheter** kan du få mer information om enheterna du hanterar, inklusive deras maskinvarukapacitet och de appar som är installerade på dem. 

Så här visar du enhetsinventeringen:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.

Välj nu något av följande alternativ:

- **Översikt** – Hämta information om enheter som du har registrerat och operativsystemen som körs för varje enhet.
- **Hantera** – Välj **Alla enheter** för att visa en lista över alla enheter som du hanterar.
    Välj en av enheterna i listan för att öppna bladet <*enhetsnamn*> **Översikt** där du kan välja:
    - **Översikt** – Visa allmän information om enheten, inklusive dess namn, ägare, om det är en BYOD-enhet, om den är incheckad och mycket annat.
    - **Maskinvara** – Visa mer detaljerad information om enheten, inklusive dess lediga lagringsutrymme, modell, tillverkare och mycket annat.
    - **Identifierade appar** – Visar en lista över alla appar som Intune hittar installerade på enheten.
    - **Enhetsefterlevnad** – Visar kompatibilitetsstatus för alla efterlevnadsprinciper som tilldelats enheten.
    - **Enhetskonfiguration** – Visar kompatibilitetsstatus för alla enhetskonfigurationsprinciper som tilldelats enheten.
- **Övervaka** Välj **Enhetsåtgärder** för att se en lista över enhetsåtgärder som har utförts på de enheter du hanterar och enheternas aktuella tillstånd.
- **Konfigurera** > **TeamViewer Connector** – Konfigurera fjärradministration på enheter med hjälp av programmet TeamViewer. Mer information finns i [Ge fjärrhjälp för Intune-hanterade Android-enheter](/intune/device-profile-android-teamviewer).

Intune samlar endast in appinformation från företagsägda enheter. Ingen appinformation samlas in från personliga enheter. För datorer med Windows 10 samlas endast modern appinformation in från företagsägda enheter. Intune samlar inte in information om Win32-appar på enheten. Beroende på vilken operatör du använder med enheterna, är det inte säkert att alla lagerobjekt kan samlas in.
