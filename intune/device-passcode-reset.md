---
title: "Återställa och ta bort enhetslösenord med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du återställer och tar bort lösenordet på enheter som du hanterar med Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e1496d24fd9d3bb636a4eab00c254b753210f63
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/23/2018
---
# <a name="reset-and-remove-the-passcode-on-intune-managed-devices"></a>Återställa och ta bort lösenordet på Intune-hanterade enheter


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Termerna *ta bort* och *återställa* används synonymt i den här artikeln.

Åtgärden **Ta bort lösenord** genererar ett nytt lösenord för enheten som visas på bladet <*enhetsnamn*> **Översikt**.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds på Windows Phone 8.1 till Windows 10 Creators Update som ej är ansluten till Azure AD, Windows 10 Creators Update och senare
- iOS – stöds
- macOS – stöds inte
- Android – stöds på versioner tidigare än Android 7. Android for Work stöds inte.

## <a name="how-to-reset-a-passcode"></a>Återställa ett lösenord

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning + hantering**.
3. Välj **Enheter** på bladet **Intune**.
4. Välj **Alla enheter** på bladet **Enheter**.
5. I listan med enheter som du hanterar väljer du en enhet, **...Mer** och sedan fjärråtgärden **Ta bort lösenord**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd du precis vidtagit väljer du **Enhetsåtgärder** på bladet **Enheter**.
