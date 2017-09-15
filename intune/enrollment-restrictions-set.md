---
title: "Ange registreringsbegränsningar i Intune"
titlesuffix: Azure portal
description: "Begränsa registrering per plattform och ange en gräns för enhetsregistrering i Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06c0c58992a2119aff7fd5be54ae90be886d2a53
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="set-enrollment-restrictions"></a>Ange registreringsbegränsningar

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du bestämma vilka enheter som får registreras för Intune-hantering. Använd Azure-portalen och ange följande begränsningar för registrering av enheter:

- Högsta tillåtna antal registrerade enheter
- Enhetsplattformar som får registreras:
  - Android
  - iOS
  - macOS
  - Windows
- Plattformens operativsystemversion (endast iOS och Android)
  - Lägsta version
  - Högsta version
- Begränsningar gentemot privatägda enheter (endast iOS, Android och macOS)

>[!NOTE]
>Begränsningar vid registrering ska inte betraktas som säkerhetsfunktioner. Komprometterade enheter kan ju utge sig för att vara en helt annan enhet. Det här är dock en bra barriär för att stänga ute användare utan skadliga avsikter.

## <a name="set-device-type-restrictions"></a>Ange begränsningar för enhetstyp
Standardregistreringsbegränsningarna gäller för alla användare och användarlösa registreringar.
1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Välj **Standard** under **Registreringsbegränsningar** > **Begränsningar av enhetstyp**.
5. Välj **Plattformar** under **Alla användare**. Välj **Tillåt** eller **Blockera** för varje plattform:
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  Klicka på **Spara**.
6. Under **Alla användare** väljer du **Plattformskonfigurationer** och väljer sedan följande konfigurationer. Du kan konfigurera följande alternativ för varje plattform som tillåts:
  - **Versioner** – Ange **Min** och **Max** för plattformens operativsystemsversioner för Android- och iOS-enheter. Operativsystemversionerna gäller inte för enheter som registreras med programmet för enhetsregistrering, Apple School Manager eller Apple Configurator-appen.
  - **Personligt ägda** – Ange om du vill **tillåta** eller **blockera** för Android-, iOS- och macOS-enheter.
  ![Skärmbild av arbetsytan för enhetsbegränsningar med standardkonfigurationer för enhetsplattformar visar inställningar för personligt ägda enheter.](media/device-restrictions-platform-configurations.png)
  Klicka på **Spara**.

>[!NOTE]
>Om du blockerar registrering av personligt ägda Android-enheter kan du ändå registrera personligt ägda Android for Work-enheter.

## <a name="set-device-limit-restrictions"></a>Ange begränsningar för enhetsgräns
Standardregistreringsbegränsningarna gäller för alla användare.
1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Välj **Enhetsregistrering** i Azure-portalen och välj sedan **Registreringsbegränsningar**.
5. Välj **Registreringsbegränsningar** > **Begränsningar för enhetsgräns**.
6. Under **Alla användare** väljer du **Enhetsgräns**. Ange högsta tillåtna antal registrerade enheter per användare.  
![Skärmbild av bladet med begränsningar för enhetsgränsen.](./media/device-restrictions-limit.png)

  Klicka på **Spara**.
