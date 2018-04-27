---
title: Återställa enhetslösenord med Microsoft Intune – Azure | Microsoft Docs
description: Ta bort eller återställ lösenordet med åtgärden Ta bort lösenkod på enheter som du hanterar eller övervakar med Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 905c51dcbc5b7731be207c25ffd368b339dbec57
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Återställa eller ta bort ett enhetslösenord i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Om du vill skapa ett nytt lösenord för en enhet använder du åtgärden **Ta bort lösenkod**.

## <a name="supported-platforms"></a>Plattformar som stöds

- Android-enheter som registrerats med en arbetsprofil, version 7.0 och senare
- Android-enheter på version 6.0 eller tidigare
- iOS 
     
## <a name="unsupported-platforms"></a>Plattformar som inte stöds

- Android-enheter som registrerats med en arbetsprofil, version 6.0 och tidigare
- Android-enheter på version 7.0 eller senare
- macOS
- Windows

## <a name="reset-a-passcode"></a>Återställa ett lösenord

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj sedan **Microsoft Intune**.
3. Välj **Enheter** och sedan **Alla enheter**.
4. Välj en enhet från listan över enheter du hanterar och välj **...Mer**. Välj sedan fjärråtgärden **Ta bort lösenkod** för enheten.

## <a name="resetting-android-for-work-passcodes"></a>Återställa Android for Work-lösenord

Android for Work-enheter som stöds får ett nytt lösenord för att låsa upp enheter, eller en kontrollfråga för hanterade profiler för slutanvändaren. För enheter på Android 7.0 eller senare med arbetsprofiler får slutanvändarna ett meddelande om att aktivera sin token för återställning av lösenord direkt när registreringen är klar. Meddelandet visas om ett lösenord för arbetsprofilen krävs och har ställts in. När de har angett lösenordet tas meddelandet bort.

## <a name="resetting-ios-passcodes"></a>Återställa iOS-lösenord

Lösenord tas bort från iOS-enheter. Om en policy för efterlevnad för lösenord har angetts kommer enheten uppmana användaren att ange ett nytt lösenord i inställningarna. 

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du nyss vidtog väljer du **Enhetsåtgärder** i **Enheter**.
