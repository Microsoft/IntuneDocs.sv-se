---
title: Förbered konfigurationen av appskyddsprinciper för Windows 10
titleSuffix: Microsoft Intune
description: Konfigurera MAM-providern för hantering av mobilprogram i Azure AD.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a394b3b218613459d993b84fcb0ea7a37d4ac4dd
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/17/2018
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Förbered konfigurationen av appskyddsprinciper för Windows 10 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Aktivera hantering av mobilprogram (MAM) för Windows 10 genom att ange MAM-providern i Microsoft Azure Active Directory. Genom att ställa in MAM-providern i Microsoft Azure Active Directory kan du definiera registreringstillståndet när du skapar en ny Windows Information Protection-princip (WIP) med Intune. Registreringstillståndet kan vara MAM eller hantering av mobila enheter (MDM).

> [!NOTE]
> Enheter med tillståndet MAM-registrering måste vara anslutna till Azure AD.

## <a name="to-configure-the-mam-provider"></a>Konfigurera MAM-providern

1. Logga in på Azure Portal och välj **Azure Active Directory.**

2. Välj **Mobility (MDM och MAM)** i gruppen **Hantera**.

3. Klicka på **Microsoft Intune**.

4. Konfigurera inställningar i gruppen **Återställ standard MAM-URL:er** på bladet **Konfigurera**.

   **MAM-användaromfattning**  
   Använd MA- autoregistrering för att hantera företagsdata på Windows-enheter för dina anställda. MAM-autoregistrering kommer att konfigureras för Bring Your Own Device-scenarier.<ul><li>**Inga**<br>Välj om inga användare ska kunna registreras på MAM.</li><li>**Vissa**<br>Välj Microsoft Azure Active Directory-grupper som innehåller användare som ska registreras på MAM.</li><li>**Alla**<br>Välj om alla användare kan registreras på MAM.</li></ul>

   **Webbadress till MAM-användarvillkor**  
   Webbadress till MAM-användarvillkor stöds inte för Microsoft Intune. Den här textrutan måste vara tom för att skyddsprinciper ska gälla.

   **Webbadress till MAM-identifiering**  
   URL till slutpunkten för registrering av MAM-tjänsten. Registrering av slutpunkten används för att registrera enheter för hantering med MAM-tjänsten.

   **MAM kompatibilitets-URL**  
   MAM kompatibilitets-URL stöds inte för Microsoft Intune. Den här textrutan måste vara tom för att skyddsprinciper ska gälla. 

5.  Klicka på **Spara**.

## <a name="next-steps"></a>Nästa steg

[Skapa en WIP-appskyddsprincip](windows-information-protection-policy-create.md)
