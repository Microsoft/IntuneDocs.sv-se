---
title: "Ta bort företagsinformation från enheter med Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du endast tar bort företagsinformation från enheter som du hanterar med Intune.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39acd12333e9685f94d23416fb1a61ce93f45476
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Ta bort företagsinformation från Intune-hanterade enheter


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**Ta bort företagsinformation** tar endast bort företagsinformation från enheter som hanteras med Intune. Personliga data tas inte bort från enheten. Enheten kommer inte längre att hanteras av Intune och kommer inte längre att kunna komma åt företagets resurser (stöds inte för Windows-enheter som är anslutna till Azure Active Directory).

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Ta bort företagsinformation**.

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.
