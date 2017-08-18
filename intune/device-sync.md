---
title: Synkronisera enheter med Intune
titleSuffix: Intune on Azure
description: "Läs om hur man synkroniserar enheter med Intune för att få de senaste principerna och åtgärderna.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 870eb3bf255cda92952a908596485d7b53259fb4
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/09/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>Synkronisera enheter med Intune för att få de senaste principerna och åtgärderna


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Enhetsåtgärden **Synkronisera** tvingar den valda enheten att omedelbart checka in med Intune. När en enhet checkar in tar den omedelbart emot eventuella väntande åtgärder eller principer som har tilldelats till den.  Den här åtgärden kan hjälpa dig att validera och felsöka principer som du har tilldelat utan att du behöver vänta på nästa schemalagda incheckning.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds
- Windows Phone – stöds
- iOS – stöds
- macOS – stöds
- Android – stöds

## <a name="how-to-sync-a-device"></a>Synkronisera en enhet

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Synkronisera**.
7. Bekräfta genom att klicka på **Ja** .

## <a name="next-steps"></a>Nästa steg

Välj **Enhetsåtgärder** att se status för synkroniseringsåtgärden. 
