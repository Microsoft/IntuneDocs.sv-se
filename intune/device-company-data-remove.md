---
title: "Ta bort företagsinformation från enheter med Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du endast tar bort företagsinformation från enheter som du hanterar med Intune.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8074d6e7cc0a061a6708f8c8bfae1a4dfcb6daa3
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/02/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Ta bort företagsinformation från Intune-hanterade enheter


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Enhetsåtgärden **Ta bort företagsinformation** tar endast bort företagsinformation från enheter som hanteras med Intune. Åtgärden tar inte bort personliga data från enheten. Efter borttagningen är enheten inte längre hanterad av Intune och kan inte längre komma åt företagsresurser.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds (stöds inte för Windows-enheter som är anslutna till Azure Active Directory)
- Windows Phone – stöds
- iOS – stöds
- macOS – stöds
- Android – stöds

## <a name="how-to-remove-company-data"></a>Ta bort företagsdata

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Ta bort företagsinformation**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
