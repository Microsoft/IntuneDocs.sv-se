---
title: "Ange utfärdare för hantering av mobila enheter"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig ange hantering av mobila enheter i Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c36ddef7e53d6f4f15c82c97dc6d18863e6859f1
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Ange utfärdare för hantering av mobila enheter

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Inställningen av hantering av mobil enhet bestämmer hur du ska hantera dina enheter. Som IT-administratör måste du ange en utfärdare för hantering av mobila enheter innan användarna kan registrera enheter för hantering.

Möjliga konfigurationerna är:

- **Fristående Intune** – Endast molnbaserad hantering, som du konfigurerar med hjälp av Azure-portalen. Innehåller den fullständiga uppsättning funktioner som Intune erbjuder. [Ange utfärdare för hantering av mobila enheter i Intune-konsolen](#mdm-authority-set-to-intune).

- **Intune-hybrid** – Integrering av Intunes molnlösning med System Center Configuration Manager. Du kan konfigurera Intune med hjälp av Configuration Manager-konsolen. [Ange utfärdare för hantering av mobila enheter till Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Hantering av mobilenheter i Office 365** – Integrering av Office 365 med Intunes molnlösning. Du kan konfigurera Intune från administrationscentret för Office 365. Innehåller en delmängd av de funktioner som är tillgängliga i Fristående Intune. Ange utfärdare för hantering av mobila enheter i administrationscentret för Office 365.

>[!IMPORTANT]
>När du har angett hanteringen av mobila enheter måste du kontakta [Microsoft Support](https://docs.microsoft.com/intune-classic/troubleshoot/get-support) för att ändra, så var omsorgsfull när du gör dina val.

## <a name="set-mdm-authority-to-intune"></a>Ange Intune som utfärdare för hantering av mobila enheter

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.
  ![Skärmbild av Intunes arbetsbelastning för felsökning med länken Välj användare](media/set-mdm-auth.png)
2. Välj **Enhetsregistrering** på Intune-bladet och välj sedan **Översikt**.

3. På bladet **Börja hantera enheter** väljer du **Ange Intune som utfärdare för hantering av mobilenheter**. Ett meddelande indikerar att du har angett MDM-utfärdare till Intune.

