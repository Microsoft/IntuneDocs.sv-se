---
title: Visa enheter med Microsoft Intune – Azure | Microsoft Docs
description: Visa information om din enhet, till exempel operativsystem, lagringsutrymme, tillverkare och modell. Hämta en lista över installerade appar, kontrollera efterlevnadsprinciper och konfigurera TeamViewer med Microsoft Intune i Azure. Det fungerar ungefär som när du visar en inventering av de enheter som du hanterar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: eaaf3e9807a8eab66c24f4d1bb3c3c5ea9f4cfe0
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="see-device-details-in-intune"></a>Visa enhetsinformation i Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Funktionen **Enheter** tillhandahåller ytterligare information om de enheter som du hanterar, inklusive deras maskinvara och installerade appar. 

Den här artikeln beskriver hur du visar alla dina enheter och deras egenskaper i Azure Portal.

## <a name="view-your-device-details"></a>Visa enhetsinformation

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enheter**. I Enheter finns flera alternativ:

   - **Översikt**: Hämta information om enheter som du har registrerat och operativsystemen som körs för varje enhet.
   - **Hantera**: Välj **Alla enheter** eller **Azure AD-enheter** för att se en lista med alla enheter som du hanterar.
    Välj en av enheterna i listan. Det här steget öppnar <*enhetsnamn*> **Översikt**, där du kan välja följande:
     - **Översikt**: Visar enhetens namn och ägare, om det är en BYOD-enhet (Bring Your Own Device), när den checkades in och annan information.
     - **Maskinvara**: Visar ledigt lagringsutrymme, modell, tillverkare och annan information om enheten.
     - **Identifierade appar**: Visar en lista över alla appar som Intune hittar installerade på enheten.
     - **Enhetsefterlevnad**: Visar status för alla efterlevnadsprinciper som tilldelats enheten.
     - **Enhetskonfiguration**: Visar kompatibilitetsstatus för alla enhetskonfigurationsprinciper som tilldelats enheten.
   - **Övervaka**: Välj **Enhetsåtgärder** för att se en lista med åtgärder som utförs på de enheter som du hanterar, samt enheternas aktuella status. **Granskningsloggar** – Visar status för olika uppgifter.
   - **Installation** > **TeamViewer Connector**: Konfigurera fjärradministration på enheter med hjälp av programmet TeamViewer. Mer information finns i [Ge fjärrhjälp för Intune-hanterade Android-enheter](device-profile-android-teamviewer.md).

Intune samlar endast in en applista från företagsägda enheter. Appar på personliga enheter kontrolleras inte. För datorer med Windows 10 visas bara moderna appar för företagsägda enheter. Intune samlar inte in information om Win32-appar på enheten. Alla appar kan inte samlas in, beroende på vilken operatör som används för enheterna.

## <a name="next-steps"></a>Nästa steg
Se vad mer du kan göra för att [hantera dina enheter](device-management.md) med Intune.
