---
ms.openlocfilehash: 015e50d24149a6b6242eda86d5f3d62489e9955d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511352"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Krav på Azure AD- och Intune-autentiseringsuppgifter

Autentisering och auktorisering bygger på Azure AD-autentiseringsuppgifter och Intune-rollbaserad åtkomstkontroll (RBAC). Alla globala administratörer och Intune-tjänstadministratörer för din klientorganisation har som standard åtkomst till informationslagerdatabasen. Använd Intune-roller till att ge fler användare åtkomst genom att de får tillgång till resursen **Intune-informationslager**.

Kraven för att få åtkomst till Intune-informationslagret (inklusive API) är:

  -  Användaren måste vara något av följande:
      -  Global Azure AD-administratör
      -  Intune-tjänstadministratör
      -  Användare med rollbaserad åtkomst till resursen **Intune-informationslager**
      -  Användarlös autentisering med [enbart programautentisering](../data-warehouse-app-only-auth.md) 
