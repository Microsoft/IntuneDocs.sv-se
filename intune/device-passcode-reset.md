---
title: "Återställa och ta bort enhetslösenord med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du återställer och tar bort lösenordet på enheter som du hanterar med Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3fdbb2fe6d52eaff8844ccfe14cef6c15a31cdff
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/12/2018
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

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Ta bort lösenord**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
