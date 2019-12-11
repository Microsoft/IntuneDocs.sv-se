---
title: Villkorlig åtkomst med Microsoft Intune
titleSuffix: Microsoft Intune
description: Lär dig hur du anger de villkor som användare, enheter och appar måste uppfylla för att få åtkomst till företagets resurser i Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 179d135ee8e216495cd7435bf38d8087e5c990e8
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188280"
---
# <a name="learn-about-conditional-access-and-intune"></a>Läs om villkorlig åtkomst och Intune

Med villkorlig åtkomst kan du styra vilka enheter och appar som kan ansluta till dina e-post- och företagsresurser. 

Enterprise Mobility + Security (EMS) är inte en fristående produkt. Det är en lösning som involverar alla tjänster och produkter som ingår i EMS. Villkorlig åtkomst ger detaljerad åtkomstkontroll så att företagets data skyddas, samtidigt den gör det möjligt för användarna att utföra sitt arbete på bästa sätt från vilken enhet som helst och oavsett var de befinner sig.

Du kan definiera villkor som reglerar åtkomsten till företagets data baserat på plats, enhet och användare och programmets känslighet.

> [!NOTE]
> Funktionerna för villkorlig åtkomst omfattar även [tjänster i Office 365](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access).

![Diagram över villkorlig åtkomst](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>Använda villkorlig åtkomst med Intune

Villkorlig åtkomst är en funktion i Azure Active Directory som ingår i Azure Active Directory Premium-licenser. Intune utökar den här funktionen genom att lägga till efterlevnad för mobila enheter och hantering av mobilappar i lösningen. 

![Intune och villkorlig åtkomst vid användning av EMS](./media/conditional-access/intune-with-ca-1.png)

Olika sätt att använda villkorlig åtkomst på med Intune:

- **Enhetsbaserad villkorlig åtkomst**

  - Villkorlig åtkomst för Exchange lokalt

  - Villkorlig åtkomst baserad på åtkomstkontroll för nätverk

  - Villkorlig åtkomst baserad på enhetsrisk

  - Villkorlig åtkomst för Windows-datorer

    - Företagsägd

    - BYOD (Bring Your Own Device)

- **Appbaserad villkorlig åtkomst**

## <a name="next-steps"></a>Nästa steg

[Vanliga sätt att använda villkorlig åtkomst på med Intune](conditional-access-intune-common-ways-use.md)
