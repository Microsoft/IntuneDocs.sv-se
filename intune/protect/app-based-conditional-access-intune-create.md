---
title: Konfigurera en appbaserad villkorlig åtkomstprincip med Intune
titleSuffix: Microsoft Intune
description: Läs mer om att skapa en appbaserad villkorlig åtkomstprincip med Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94e9fcc77f8260c4a63150b5d0aef033677c524a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509669"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Konfigurera appbaserade villkorliga åtkomstprinciper med Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Konfigurera appbaserade principer för villkorlig åtkomst för appar som finns med i listan över godkända appar. Listan över godkända appar består av appar som har testats av Microsoft.

> [!IMPORTANT]
> Den här artikeln innehåller stegvisa anvisningar som beskriver hur du lägger till en princip för appbaserad villkorlig åtkomst. Du kan följa samma steg när du lägger till appar som SharePoint Online, Microsoft Teams och Microsoft Exchange Online från listan över godkända appar.

## <a name="create-app-based-conditional-access-policies"></a>Skapa principer för appbaserad villkorsstyrd åtkomst
Villkorsstyrd åtkomst är en Azure Active Directory-teknik (Azure AD). Den nod för villkorsstyrd åtkomst som nås från *Intune* är samma nod som den som nås från *Azure AD*. Det innebär att du inte behöver växla mellan Intune och Azure AD för att konfigurera principer.

> [!IMPORTANT]
> Du måste ha en Azure AD Premium-licens för att kunna skapa principer för villkorlig åtkomst från Intune-portalen.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Så här skapar du en appbaserad princip för villkorlig åtkomst

> [!IMPORTANT]
> [Intune-appskyddsprinciper](../apps/app-protection-policies.md) måste tillämpas på apparna innan du använder appbaserade principer för villkorlig åtkomst.

1. Välj **Villkorsstyrd åtkomst** på **Intune-instrumentpanelen**.

2. I fönstret **Principer** väljer du **Ny princip** om du vill skapa en ny appbaserad villkorlig åtkomstprincip.

4. Ange ett principnamn och konfigurera inställningarna i avsnittet **Tilldelningar** och välj sedan **Bevilja** under avsnittet **Åtkomstkontroller**.

5. Välj **Kräv godkänd klientapp** följt av **Välj** och sedan **Skapa** för att spara den nya principen.

## <a name="next-steps"></a>Nästa steg
[Blockera appar som inte har modern autentisering](app-modern-authentication-block.md)

## <a name="see-also"></a>Se även

[Skydda appdata med appskyddsprinciper](../apps/app-protection-policies.md)
[Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
