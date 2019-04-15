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
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34ce3f34dbf3c060438a6b30abc9345687cdaf47
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569499"
---
# <a name="whats-conditional-access"></a>Vad är villkorlig åtkomst?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Villkorlig åtkomst syftar på olika sätt du kan styra enheterna och apparna som tillåts ansluta till dina e-post- och företagsresurser. I det här avsnittet får du veta mer som enhetsbaserad och appbaserad villkorlig åtkomst och hittar vanliga scenarier för att använda villkorlig åtkomst med Intune.

Villkorlig åtkomst i Enterprise Mobility + Security (EMS) är inte någon fristående produkt, utan en lösning som förekommer i alla tjänster och produkter som ingår i EMS. Den ger detaljerad åtkomstkontroll så att företagets data skyddas, samtidigt den gör det möjligt för användarna att utföra sitt arbete på bästa sätt från vilken enhet som helst och oavsett var de befinner sig.

Du kan definiera villkor som reglerar åtkomsten till företagets data baserat på plats, enhet och användare och programmets känslighet.

> [!NOTE] 
> Funktionerna för villkorlig åtkomst omfattar även [tjänster i Office 365](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/).

![Arkitekturdiagram för villkorlig åtkomst](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Villkorlig åtkomst med Intune

Villkorlig åtkomst är en funktion i Azure Active Directory som ingår i Azure Active Directory Premium-licenser. Intune utökar den här funktionen genom att lägga till efterlevnad för mobila enheter och hantering av mobilappar i lösningen. 

![Intune och villkorlig åtkomst vid användning av EMS](./media/intune-with-ca-1.png)

Olika sätt att använda villkorlig åtkomst på med Intune:

-   **Enhetsbaserad villkorlig åtkomst**

    -   Villkorlig åtkomst för Exchange lokalt

    -   Villkorlig åtkomst baserad på åtkomstkontroll för nätverk

    -   Villkorlig åtkomst baserad på enhetsrisk

    -   Villkorlig åtkomst för Windows-datorer

        -   Företagsägd

        -   BYOD (Bring Your Own Device)

-   **Appbaserad villkorlig åtkomst**

## <a name="next-steps"></a>Nästa steg

[Vanliga sätt att använda villkorlig åtkomst på med Intune](conditional-access-intune-common-ways-use.md)
