---
title: Konfigurera en appbaserad villkorlig åtkomstprincip med Intune
titlesuffix: Microsoft Intune
description: Läs mer om att skapa en appbaserad villkorlig åtkomstprincip med Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2026a446ffef3bd845affe45a7732ef3ab8ec24
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842925"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Konfigurera appbaserade villkorliga åtkomstprinciper med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Konfigurera appbaserade principer för villkorlig åtkomst för appar som finns med i listan över godkända appar. Listan över godkända appar består av appar som har testats av Microsoft.

> [!IMPORTANT]
> Den här artikeln innehåller stegvisa anvisningar som beskriver hur du lägger till en princip för appbaserad villkorlig åtkomst. Du kan följa samma steg när du lägger till appar som SharePoint Online, Microsoft Teams och Microsoft Exchange Online från listan över godkända appar.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Skapa appbaserade principer för villkorlig åtkomst i Azure AD-arbetsbelastning

IT-administratörer kan skapa principer för appbaserad villkorlig åtkomst från Azure Active Directory-arbetsbelastningen. Den här åtkomsten innebär att du inte behöver växla mellan Azure- och Intune-arbetsbelastningar.

> [!IMPORTANT]
> Du måste ha en Azure AD Premium-licens för att kunna skapa Azure AD-principer för villkorlig åtkomst från Intune Azure Portal.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Så här skapar du en appbaserad princip för villkorlig åtkomst

> [!IMPORTANT]
> [Intune-appskyddsprinciper](app-protection-policies.md) måste tillämpas på apparna innan du använder appbaserade principer för villkorlig åtkomst.

1. Välj **villkorlig åtkomst** på **Intune-instrumentpanelen**.

2. I fönstret **Principer** väljer du **Ny princip** om du vill skapa en ny appbaserad villkorlig åtkomstprincip.

4. Ange ett principnamn och konfigurera inställningarna i avsnittet **Tilldelningar** och välj sedan **Bevilja** under avsnittet **Åtkomstkontroller**.

5. Välj **Kräv godkänd klientapp** följt av **Välj** och sedan **Skapa** för att spara den nya principen.

## <a name="next-steps"></a>Nästa steg
[Blockera appar som inte har modern autentisering](app-modern-authentication-block.md)

### <a name="see-also"></a>Se även

[Skydda appdata med appskyddsprinciper](app-protection-policies.md)
[Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
