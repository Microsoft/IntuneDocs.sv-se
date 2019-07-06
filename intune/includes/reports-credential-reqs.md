---
ms.openlocfilehash: 76706fb39c3c5a69cba4fbf3f57c0b58d92e4a27
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67560025"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Krav på Azure AD- och Intune-autentiseringsuppgifter

Autentisering och auktorisering bygger på Azure AD-autentiseringsuppgifter och Intune-rollbaserad åtkomstkontroll (RBAC). Alla globala administratörer och Intune-tjänstadministratörer för din klientorganisation har som standard åtkomst till informationslagerdatabasen. Använd Intune-roller till att ge fler användare åtkomst genom att de får tillgång till resursen **Intune-informationslager**.

Kraven för att få åtkomst till Intune-informationslagret (inklusive API) är:

  - Användaren måste vara något av följande:
      - Global Azure AD-administratör
      - Intune-tjänstadministratör
      - Användare med rollbaserad åtkomst till resursen **Intune-informationslager**
      - Användarlös autentisering med [enbart programautentisering](../data-warehouse-app-only-auth.md) 
