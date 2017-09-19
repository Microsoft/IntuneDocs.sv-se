---
title: "Återställa ett lösenord för enheten med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du återställer lösenordet på enheter som du hanterar med Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3defec3624944918d14b9c4527487c368c487dd6
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="reset-the-passcode-on-intune-managed-devices"></a>Återställa lösenordet på Intune-hanterade enheter


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Åtgärden **Återställ lösenord** genererar ett nytt lösenord för enheten som visas på bladet <*enhetsnamn*> **Översikt**.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds på Windows Phone 8.1 till Windows 10 Creators Update som ej är ansluten till Azure AD, Windows 10 Creators Update och senare
- iOS – stöds
- macOS – stöds inte
- Android – stöds på versioner tidigare än Android 7. Android for Work stöds inte.

## <a name="how-to-reset-a-passcode"></a>Återställa ett lösenord

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Återställ lösenord**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
