---
title: "Ange registreringsbegränsningar i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Begränsa registrering per plattform och ange en gräns för enhetsregistrering i Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 56996592febf0be5ab74b158a70404728fe17a4d
ms.lasthandoff: 02/18/2017

---

# <a name="set-enrollment-restrictions"></a>Ange registreringsbegränsningar 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Du kan ange vilka typer av enheter du vill registrera och maximalt antal enheter. På bladet Registreringsbegränsningar kan du ange:

- De plattformar som får registreras och om registrering av privatägda enheter ska blockeras för Android och iOS.

- Det maximala antalet enheter som en användare får registrera.

## <a name="set-device-type-restrictions"></a>Ange begränsningar för enhetstyp

1. På Azure-portalen väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Registreringsbegränsningar**.

3. Under **Begränsningar av enhetstyp** väljer du **Standard**.

4. På bladet **Alla användare** väljer du **Plattformar**.

5. För plattformar som ska kunna registreras i Intune väljer du **Tillåt**. För plattformar som du vill blockera från registrering väljer du **Blockera**. Värdet för plattformar är **Tillåt** som standard. 

    >[!NOTE]
    >Dessa inställningar gäller inte för, och blockerar inte, Windows-registreringar som använder Intune-klientprogrammet. De här inställningarna påverkar endast registrering med hantering av mobila enheter. 

6. Välj **Spara**.

7. Välj **Plattformskonfigurationer**.

8. Välj om du vill **Tillåta** eller **Blockera** registrering av privatägda iOS- och Android-enheter.

9. Välj **Spara**.

## <a name="set-device-limit-restrictions"></a>Ange begränsningar för enhetsgräns

1. På Azure-portalen väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Registreringsbegränsningar**.

3. Under **Begränsningar för enhetsgräns** väljer du **Standard**.

4. På bladet **Alla användare** väljer du **Enhetsgräns**.

5. Välj det maximala antalet enheter som en användare kan registrera och klicka sedan på **Spara**.

