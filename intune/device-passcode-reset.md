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
ms.openlocfilehash: dd743bdb0eaf2e00c50aab85c497dd00aac773ed
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905163"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Återställa eller ta bort ett enhetslösenord i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Om du vill skapa ett nytt lösenord för en enhet använder du åtgärden **Ta bort lösenkod**.

## <a name="supported-platforms"></a>Plattformar som stöds

- Android-enheter som registrerats med en arbetsprofil, version 8.0 och senare
- Android-enheter på version 6.0 eller tidigare
- Android-kioskenheter för företag
- iOS 
     
## <a name="unsupported-platforms"></a>Plattformar som inte stöds

- Android-enheter som registrerats med en arbetsprofil, version 7.0 och tidigare
- Android-enheter på version 7.0 eller senare
- macOS
- Windows

## <a name="reset-a-passcode"></a>Återställa ett lösenord

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj sedan **Microsoft Intune**.
3. Välj **Enheter** och sedan **Alla enheter**.
4. Välj en enhet från listan över enheter du hanterar och välj **...Mer**. Välj sedan fjärråtgärden **Ta bort lösenkod** för enheten.

## <a name="resetting-android-work-profile-passcodes"></a>Återställa lösenord för Android-arbetsprofiler

Android-arbetsprofilenheter som stöds får ett nytt lösenord för att låsa upp hanterade profiler, eller en kontrollfråga för hanterade profiler för slutanvändaren. För Android 8.0-arbetsprofilenheter uppmanas slutanvändarna att aktivera sina lösenord direkt efter registreringen. Meddelandet visas om ett lösenord för arbetsprofilen krävs och har ställts in. När de har angett lösenordet tas meddelandet bort.

## <a name="resetting-ios-passcodes"></a>Återställa iOS-lösenord

Lösenord tas bort från iOS-enheter. Om en efterlevnadsprincip för lösenord har angetts uppmanar enheten användaren att ange ett nytt lösenord i inställningarna. 

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du nyss vidtog väljer du **Enhetsåtgärder** i **Enheter**.
