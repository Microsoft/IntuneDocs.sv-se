---
title: Konfigurera appskyddsprinciper för Windows 10
titleSuffix: Microsoft Intune
description: Det här avsnittet beskriver hur du konfigurerar appskyddsprinciper för Windows 10-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0e1ff8fd39d301bd685e9806c319f49e9189d7f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507414"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Förbered konfigurationen av appskyddsprinciper för Windows 10 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Aktivera hantering av mobilprogram (MAM) för Windows 10 genom att ange MAM-providern i Microsoft Azure Active Directory. Genom att ställa in MAM-providern i Microsoft Azure Active Directory kan du definiera registreringstillståndet när du skapar en ny Windows Information Protection-princip (WIP) med Intune. Registreringstillståndet kan vara MAM eller hantering av mobila enheter (MDM).

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

5. Klicka på **Spara**.

## <a name="next-steps"></a>Nästa steg

[Skapa en WIP-appskyddsprincip](windows-information-protection-policy-create.md)
