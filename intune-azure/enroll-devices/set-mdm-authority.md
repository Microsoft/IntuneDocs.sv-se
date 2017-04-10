---
title: "Ange utfärdare för hantering av mobila enheter"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig ange hantering av mobila enheter i Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 9d7a1a934188f0a40553d3c6b8b567ba8f6af034
ms.lasthandoff: 02/18/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Ange utfärdare för hantering av mobila enheter 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Inställningen av hantering av mobil enhet bestämmer hur du ska hantera dina enheter. De möjliga konfigurationerna är:

- **Fristående Intune** – Endast molnbaserad hantering, som du konfigurerar med hjälp av Azure-portalen. Innehåller den fullständiga uppsättning funktioner som Intune erbjuder.

- **Intune-hybrid** – Integrering av Intunes molnlösning med System Center Configuration Manager. Du kan konfigurera Intune med hjälp av Configuration Manager-konsolen.

- **Hantering av mobilenheter i Office 365** – Integrering av Office 365 med Intunes molnlösning. Du kan konfigurera Intune från administrationscentret för Office 365. Innehåller en delmängd av de funktioner som är tillgängliga i Fristående Intune.

>[!IMPORTANT]
>När du har angett hanteringen av mobila enheter måste du kontakta [Microsoft Support](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) för att ändra, så var omsorgsfull när du gör dina val.

**Konfigurera hanteringsauktoriteten för mobila enheter:**

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Översikt**.

3. På bladet **Börja hantera enheter** väljer du **Ange Intune som utfärdare för hantering av mobilenheter**. Ett meddelande indikerar att du har angett MDM-utfärdare till Intune.

