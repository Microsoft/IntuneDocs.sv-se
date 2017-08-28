---
title: "Komma igång med appar"
titleSuffix: Intune on Azure
description: "Hitta och lägg till appar på enheter så att dina anställda kan få arbete utfört."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7ac2a6f027a78c6b0093a0d299a7cae3265e5954
ms.sourcegitcommit: 45204e0fb8cb4cce449e65f2f1d7bb6f6ac4ccf5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/16/2017
---
# <a name="get-started-with-adding-apps"></a>Kom igång med att lägga till appar

Intune stöder ett antal olika sätt att distribuera appar till företagets enheter:

* **Installationsprogram för programvara**: för när du laddar upp en fil som sedan laddas ned till användarnas enheter
* __Externa länkar__: för när du har en app i en offentlig appbutik eller en webapp
* **Hanterade appar**: för iOS-enheter där ytterligare mobilapphantering ska tillämpas på appar som är tillgängliga i App Store

Du ska nu gå genom en av de snabbare distributionsmetoderna för appar genom att tilldela en offentlig butiksapp.

## <a name="how-do-i-assign-a-public-store-app"></a>Hur gör jag för att tilldela en offentlig butiksapp?

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Sök efter **Intune** med hjälp av **Sök resurser**.
3. Välj **Mobilappar** och välj sedan **appar**.
4. Välj **Lägg till** och välj sedan **iOS Store-app** som **apptyp**.
5. Sök efter en app att tilldela till enheten i textrutan. Välj appen och välj **OK**.
6. Välj **Appinformation** på bladet **Lägg till app**. Kontrollera sedan att all information om appen är ifylld. Du kan lägga till ytterligare information som hjälp vid organisation av den här appen, t.ex. **Ägare**, **Anteckningar**, **Utvecklare** och en **sekretesswebbadress** till företagets sekretesspolicy.
7. Kontrollera att du har markerat Ja för att visa appen som en aktuell app i företagsportalen och klicka sedan på OK.
8. Välj **Lägg till** för att lägga till appen. Du kommer nu till appens **översikt**. Välj **Tilldelningar** och klicka sedan på **Välj grupper** för att tilldela appen till din testgrupp. Gör appen **tillgänglig** för nedladdning. Appen ska nu visas som en **aktuell App** på testenheten.

## <a name="learn-more"></a>Läs mer

* [Vad är apphantering med Intune?](app-management.md)
* [Översikt över appens livscykel](app-lifecycle.md)
* [Vad är appskyddsprinciper?](app-protection-policy.md)
