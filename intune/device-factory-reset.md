---
title: "Återställa enheter till fabriksinställningar med Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du återställer enheter som du hanterar till deras fabriksinställningar med Intune.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8eff9b53-eef2-4c50-8aee-556bc49d69f2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 44f69179f76c8d5eeca1594485ca3a9c1b036188
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/09/2017
---
# <a name="reset-intune-managed-devices-to-factory-settings"></a>Återställa Intune-hanterade enheter till fabriksinställningarna


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**Fabriksåterställning** återställer enheten till standardinställningarna. Enheten hanteras inte längre av Intune och både företagsdata och personliga data tas bort. Du kan inte ångra den här åtgärden.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds på Windows 8.1 och senare (ej EAS-hanterade enheter)
- Windows Phone – stöds
- iOS – stöds
- macOS – stöds inte
- Android – stöds (Android for Work stöds inte)

## <a name="how-to-reset-a-device-to-factory-settings"></a>Återställa en enhet till fabriksinställningarna

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Fabriksåterställning**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.

