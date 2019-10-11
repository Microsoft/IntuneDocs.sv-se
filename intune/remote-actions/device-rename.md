---
title: Ändra namn på en enhet med Microsoft Intune – Azure | Microsoft Docs
description: Byt namn på en enhet med hjälp av Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35fae5ea1b3294772db4f4db51179892e08ed5d1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728513"
---
# <a name="rename-a-device-in-intune"></a>Ändra namn på en enhet i Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Med åtgärden **Byt namn på enhet** kan du byta namn på en enhet som har registrerats i Intune. Enhetens namn ändras i Intune och på enheten.

Du kan byta namn på följande enhetstyper:
- företagsägda Windows-enheter 
- iOS-övervakade enheter
- företagsägda MacOS 10-enheter

Den här funktionen stöder för närvarande inte namnbyte av Windows-hybridenheter för Azure AD.

## <a name="rename-a-device"></a>Byta namn på en enhet

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Enheter** > **Alla enheter** > välj en enhet > **Mer** > **Byt namn på enhet**.
4. På bladet **Byt namn på enhet** skriver du det nya namnet i textrutan. Du kan använda bokstäver, siffror och bindestreck. Namnet måste innehålla minst en bokstav eller bindestreck.
5. Om du vill starta om enheten efter namnbytet väljer du **Ja** bredvid **Starta om efter namnbyte**.
6. Välj **Byt namn**.



## <a name="next-steps"></a>Nästa steg

För att se status för enhetsåtgärden **Byt namn** kontrollerar du sidan **Översikt** för enheten.
