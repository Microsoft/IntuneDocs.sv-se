---
title: Konfigurera appskyddsprinciper för Windows 10
titleSuffix: Microsoft Intune
description: Det här avsnittet beskriver hur du konfigurerar appskyddsprinciper för Windows 10-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
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
ms.openlocfilehash: 66cf454290903705d8500c2b1f9a07c9097351bf
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781745"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Förbered konfigurationen av appskyddsprinciper för Windows 10 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Aktivera hantering av mobilprogram (MAM) för Windows 10 genom att ange MAM-providern i Microsoft Azure Active Directory. Genom att ställa in MAM-providern i Microsoft Azure Active Directory kan du definiera registreringstillståndet när du skapar en ny Windows Information Protection-princip (WIP) med Intune. Registreringstillståndet kan vara MAM eller hantering av mobila enheter (MDM).

## <a name="to-configure-the-mam-provider"></a>Konfigurera MAM-providern

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Alla tjänster** och växla instrumentpaneler genom att välja **M365 Azure Active Directory**.
3. Välj **Azure Active Directory**.
4. Välj **Mobility (MDM och MAM)** i gruppen **Hantera**.
5. Klicka på **Microsoft Intune**.
6. Konfigurera inställningarna i gruppen **Återställ standard MAM-URL:er** i fönstret **Konfigurera**.

   **MAM-användaromfattning**  
   Använd MA- autoregistrering för att hantera företagsdata på Windows-enheter för dina anställda. MAM-autoregistrering kommer att konfigureras för Bring Your Own Device-scenarier.<ul><li>**Inga**<br>Välj om inga användare ska kunna registreras på MAM.</li><li>**Vissa**<br>Välj Microsoft Azure Active Directory-grupper som innehåller användare som ska registreras på MAM.</li><li>**Alla**<br>Välj om alla användare kan registreras på MAM.</li></ul>

   **Webbadress till MAM-användarvillkor**  
   Webbadress till MAM-användarvillkor stöds inte för Microsoft Intune. Den här textrutan måste vara tom för att skyddsprinciper ska gälla.

   **Webbadress till MAM-identifiering**  
   URL till slutpunkten för registrering av MAM-tjänsten. Registrering av slutpunkten används för att registrera enheter för hantering med MAM-tjänsten.

   **MAM kompatibilitets-URL**  
   MAM kompatibilitets-URL stöds inte för Microsoft Intune. Den här textrutan måste vara tom för att skyddsprinciper ska gälla. 

7. Klicka på **Spara**.

## <a name="next-steps"></a>Nästa steg

[Skapa en WIP-appskyddsprincip](windows-information-protection-policy-create.md)
