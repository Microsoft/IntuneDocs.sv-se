---
title: Ändra namn på en Windows-enhet med Microsoft Intune – Azure | Microsoft Docs
description: Byt namn på en Windows-enhet med hjälp av Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dfdc3641d583fc045346034ee8543feff1e7cbf
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/28/2019
ms.locfileid: "59567107"
---
# <a name="rename-a-windows-device-in-intune"></a>Byta namn på en Windows-enhet i Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Med åtgärden **Byt namn på enhet** kan du byta namn på en företagsägd Windows-enhet som har registrerats i Intune. Enhetens namn ändras i Intune och på enheten. 

Den här funktionen stöder för närvarande inte namnbyte av Windows-hybridenheter för Azure AD.

## <a name="rename-a-device"></a>Byta namn på en enhet

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enheter** > **Alla enheter** > välj en Windows-enhet > **Mer** > **Byt namn på enhet**.
4. På bladet **Byt namn på enhet** skriver du det nya namnet i textrutan. Du kan använda bokstäver, siffror och bindestreck. Namnet måste innehålla minst en bokstav eller bindestreck.
5. Om du vill starta om enheten efter namnbytet väljer du **Ja** bredvid **Starta om efter namnbyte**.
6. Välj **Byt namn**.



## <a name="next-steps"></a>Nästa steg

För att se status för enhetsåtgärden **Byt namn** kontrollerar du sidan **Översikt** för enheten.
