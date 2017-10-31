<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Krav på Azure AD- och Intune-autentiseringsuppgifter

Autentisering och auktorisering bygger på Azure AD-autentiseringsuppgifter och Intune-rollbaserad åtkomstkontroll (RBAC). Alla globala administratörer och Intune-tjänstadministratörer för din klientorganisation har som standard åtkomst till informationslagerdatabasen. Använd Intune-roller för att ge fler användare åtkomst genom att ge dem tillgång till **rapporteringsresursen**.

Kraven för att få åtkomst till Intune-informationslagret (inklusive API) är:

  -  Användaren måste ha tilldelats en Intune-licens
  -  Användaren måste vara något av följande:
      -  Global Azure AD-administratör
      -  Intune-tjänstadministratör
      -  Användare med rollbaserad åtkomst till resursen **Rapporter**