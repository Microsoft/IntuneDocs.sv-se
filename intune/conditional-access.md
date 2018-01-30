---
title: "Villkorlig åtkomst med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du anger de villkor som användare och enheter måste uppfylla för att få åtkomst till företagets resurser i Microsoft Intune.\""
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 05/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4d3d84f8010b72b9595f3ff54924d6c3fe245702
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="whats-conditional-access"></a>Vad är villkorlig åtkomst?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I det här avsnittet beskrivs villkorlig åtkomst så som den fungerar i Enterprise Mobility + Security (EMS). Därefter följer några vanliga scenarion för villkorlig åtkomst i Intune.

Villkorlig åtkomst i Enterprise Mobility + Security (EMS) är inte någon fristående produkt, utan en lösning som förekommer i alla tjänster och produkter som ingår i EMS. Den ger detaljerad åtkomstkontroll så att företagets data skyddas, samtidigt den gör det möjligt för användarna att utföra sitt arbete på bästa sätt från vilken enhet som helst och oavsett var de befinner sig.

Du kan definiera villkor som reglerar åtkomsten till företagets data baserat på plats, enhet och användare och programmets känslighet.

> [!NOTE] 
> Funktionerna för villkorlig åtkomst omfattar även [tjänster i Office 365](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/).

![Arkitekturdiagram för villkorlig åtkomst](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Villkorlig åtkomst med Intune

I Intune finns nu efterlevnad för mobila enheter och principer för hantering av appar, vilket stöder lösningen för villkorlig åtkomst i EMS.

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
