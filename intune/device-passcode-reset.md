---
title: "Återställa enhetslösenord med Microsoft Intune – Azure | Microsoft Docs"
description: "Ta bort eller återställ lösenordet med åtgärden Ta bort lösenkod på enheter som du hanterar eller övervakar med Intune."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f23a79bbe72d12750ef642226aefd1e11dcac24
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Återställa eller ta bort ett enhetslösenord i Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Om du vill skapa ett nytt lösenord för en enhet använder du åtgärden **Ta bort lösenkod**.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows Phone 8.1 till Windows 10 Creators Update som inte är ansluten till Azure AD och Windows 10 Creators Update och senare
- iOS
- Tidigare Android-versioner än Android 7

Den här funktionen stöds **inte** för följande system:

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>Återställa ett lösenord

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj sedan **Microsoft Intune**.
3. Välj **Enheter** och sedan **Alla enheter**.
4. I listan med enheter som du hanterar väljer du en enhet, **...Mer** och sedan fjärråtgärden **Ta bort lösenord**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du nyss vidtog väljer du **Enhetsåtgärder** i **Enheter**.
