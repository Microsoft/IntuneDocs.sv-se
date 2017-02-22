---
title: "Ange registreringsbegränsningar i Intune | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Begränsa registrering per plattform och ange en gräns för enhetsregistrering i Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 1bdefce35c20ce24b94ee701a2d13b5408f435ce

---

# <a name="set-enrollment-restrictions"></a>Ange registreringsbegränsningar 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Du kan begränsa vilka typer av enheter som ska kunna registreras i Intune genom att ange de tillåtna plattformarna. Du kan också ange det maximala antalet enheter en användare har behörighet att registrera.

## <a name="set-device-type-restrictions"></a>Ange begränsningar för enhetstyp

1. Välj **Fler tjänster** i Azure-portalen, skriv **Intune** i textrutan och välj sedan **Övrigt** > **Intune**

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Registreringsbegränsningar**.

3. Under **Begränsningar av enhetstyp** väljer du **Standard**.

4. På bladet **Alla användare** väljer du **Plattformar**.

5. För plattformar som ska kunna registreras i Intune väljer du **Tillåt**. För plattformar som du vill blockera från registrering väljer du **Blockera**.

6. Välj **Spara**.

7. Välj **Plattformskonfigurationer**.

8. Välja att Tillåta eller Blockera registrering av privatägda iOS-enheter.

9. Välj **Spara**.

## <a name="set-device-limit-restrictions"></a>Ange begränsningar för enhetsgräns

1. Välj **Registrera enheter** på Intune-bladet i Azure-portalen och välj sedan **Registreringsbegränsningar**.

2. Under **Begränsningar för enhetsgräns** väljer du **Standard**.

3. På bladet **Alla användare** väljer du **Enhetsgräns**.

4. Välj det maximala antalet enheter som en användare kan registrera och klicka sedan på **Spara**.



<!--HONumber=Feb17_HO1-->


