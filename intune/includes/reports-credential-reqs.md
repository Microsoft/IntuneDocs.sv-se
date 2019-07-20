---
ms.openlocfilehash: 6ec8f8a613d3b0a0b17f2615de634e70fa282fd7
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68229342"
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
