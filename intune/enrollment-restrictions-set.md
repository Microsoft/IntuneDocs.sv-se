---
title: "Ange registreringsbegränsningar i Intune"
titleSuffix: Intune on Azure
description: "Begränsa registrering per plattform och ange en gräns för enhetsregistrering i Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2dfcba8c788f262ce816dcd23dc2921fd57f331b
ms.sourcegitcommit: d1ad84edf4f03cb4c11fe55131556b43fc3a4500
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/05/2017
---
# <a name="set-enrollment-restrictions"></a>Ange registreringsbegränsningar

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du bestämma vilka enheter som får registreras för Intune-hantering. Använd Intune-portalen och ange följande begränsningar för registrering av enheter:

- Högsta tillåtna antal registrerade enheter
- Enhetsplattformar som får registreras:
  - Android
  - iOS
  - macOS
  - Windows
- Begränsningar gentemot privatägda enheter (endast iOS och Android)

>[!NOTE]
>Begränsningar vid registrering ska inte betraktas som en säkerhetsfunktion. Komprometterade enheter kan ju utge sig för att vara en helt annan enhet. Det här är dock en bra barriär för att stänga ute användare utan skadliga avsikter.

## <a name="set-device-type-restrictions"></a>Ange begränsningar för enhetstyp
Standardbegränsningarna vid registrering gäller för alla användare som inte har tilldelats högre prioritet.  
1. Välj **Enhetsregistrering** på Intune-portalen och välj sedan **Registreringsbegränsningar**.
![Skärmbild av arbetsytan för enhetsbegränsningar med standardbegränsningar för enheten och enhetsbegränsningar.](media/device-restrictions-set-default.png)
2. Välj **Standard** under **Registreringsbegränsningar** > **Begränsningar av enhetstyp**.
3. Välj **Plattformar** under **Alla användare**. Välj **Tillåt** eller **Blockera** för varje plattform:
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  Klicka på **Spara**.
4. Under **Alla användare** väljer du **Plattformskonfigurationer** och väljer sedan följande konfigurationer:
  - **Personligt ägda** – Ange om du vill **tillåta** eller **blockera** för Android- och iOS-enheter.
  ![Skärmbild av arbetsytan för enhetsbegränsningar med standardkonfigurationer för enhetsplattformar visar inställningar för personligt ägda enheter.](media/device-restrictions-platform-configurations.png)
  Klicka på **Spara**.

>[!NOTE]
>Om du blockerar registrering av personligt ägda Android-enheter kan du ändå registrera Android for Work-enheter.

## <a name="set-device-limit-restrictions"></a>Ange begränsningar för enhetsgräns
Standardbegränsningarna vid registrering gäller för alla användare som inte har tilldelats högre prioritet.  
1. Välj **Enhetsregistrering** på Intune-portalen och välj sedan **Registreringsbegränsningar**.
2. Välj **Registreringsbegränsningar** > **Begränsningar för enhetsgräns**.
3. Under **Alla användare** väljer du **Enhetsgräns**. Ange högsta tillåtna antal registrerade enheter per användare.  
![Skärmbild av bladet med begränsningar för enhetsgränsen.](./media/device-restrictions-limit.png)

  Klicka på **Spara**.
