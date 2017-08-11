---
title: RBAC med Intune
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig hur RBAC kan kontrollera vem som ska kunna utföra åtgärder och göra ändringar."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3aff61f6201d6569e35aa9d556aa655d28775d2f
ms.sourcegitcommit: 18cdbdc226f64368de892a8c5cff157c37986c57
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="role-based-administration-control-rbac-with-intune"></a>Rollbaserad administrationskontroll (RBAC) med Intune

RBAC hjälper dig att styra vem som kan utföra olika uppgifter för Intune i din organisation och vem aktiviteterna gäller för. Du kan antingen använda de inbyggda roller täcker vissa vanliga scenarier för Intune eller du kan skapa egna roller. En roll definieras av:

- **Rolldefinition**: namnet på rollen, de resurser som den hanterar och behörigheterna för varje resurs.
- **Medlemmar**: de användargrupper som har behörigheten.
- **Omfång**: användar- eller enhetsgrupper som medlemmarna kan hantera.
- **Tilldelning** – När definitionen, medlemmar och omfång har konfigurerats är rollen tilldelad.

![Intune RBAC-exempel](./media/intune-rbac-1.PNG)

**Azure Active Directory (AD Azure)** innehåller två Directory roller som kan användas med Intune, som börjar med den nya Intune-portalen. Rollerna beviljas fullständig behörighet för att utföra alla aktiviteter i Intune:

- **Global administratör:** användare med den här rollen har åtkomst till alla administrativa funktioner i Azure AD, samt tjänster som är underordnade Azure AD som Exchange Online, SharePoint Online och Skype för företag – Online. Personen som registrerar sig för Azure AD-klient blir global administratör. Endast globala administratörer kan tilldela andra administratörsroller i Azure AD. Det kan finnas mer än en global administratör i din organisation. Globala administratörer kan återställa lösenordet för alla användare och alla andra administratörer.

- **Intune Service-administratör:** användarna med den här rollen har globala behörigheter i Intune när tjänsten finns. Dessutom kan ger den här rollen möjlighet att hantera användare och enheter, samt skapa och hantera grupper.

- **Conditional Access Administrator (Administratör för villkorlig åtkomst):** Användare med den här rollen har endast behörighet att visa, skapa, ändra och ta bort principer för villkorlig åtkomst.

    > [!IMPORTANT]
    > Rollen som Intune Service-administratör ger inte möjlighet att hantera inställningar för villkorlig åtkomst i Azure AD.

    > [!TIP]
    > Intune visar också tre Azure AD-tillägg: **Användare**, **Grupper** och **Villkorlig åtkomst** som kontrolleras med hjälp av Azure AD RBAC. Dessutom kan den **Användarkontoadministratören** endast utför aktiviteter för AAD-användare/-grupp och har inte fullständig behörighet att utföra alla aktiviteter i Intune. Se [RBAC med Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) för mer information.

## <a name="roles-created-in-the-intune-classic-console"></a>Roller som skapas i den klassiska Intune-konsolen

Endast Intune **Service-administratörer** med ”Full” behörighet migreras från den klassiska Intune-konsolen till Intune i Azure. Du måste tilldela Intune **Service-administratörer** med åtkomsten ”skrivskyddad” eller ”supportavdelning” till Intune-roller i Azure portalen och ta bort dem från den klassiska portalen.

> [!IMPORTANT]
> Du kan behöva bevara Intune Service-administratörsåtkomsten i den klassiska konsolen om dina administratörer fortfarande behöver åtkomst till att hantera datorer med Intune.

## <a name="built-in-roles"></a>Inbyggda roller

Följande roller är inbyggda i Intune och du kan tilldela dem till grupper utan någon ytterligare konfiguration:

- **Supportavdelning**: Utför fjärråtgärder på användare och enheter och kan tilldela program eller principer till användare eller enheter.
- **Princip- och profilhanterare**: Hanterar principer för efterlevnad, konfigurationsprofiler, Apple-registrering och företagets enhetsidentifierare.
- **Användare med skrivskydd**: Visar information om användare, enhet, registrering, konfiguration och programmet. Kan inte göra ändringar i Intune.
- **Programhanterare**: hanterar mobila och hanterade program och kan läsa enhetsinformation.

### <a name="to-assign-a-built-in-role"></a>Tilldela en inbyggd roll

1. På **Intune-roller** väljer du den inbyggda rollen som du vill tilldela.

2. På bladet <*rollnamn*> – **Egenskaper** väljer du **Hantera** och därefter **Tilldelningar**.

    > [!NOTE]
    > Du kan inte ta bort eller redigera inbyggda roller

3. På bladet anpassad roll väljer du **Tilldela**.

4. På bladet **Rolltilldelningar** anger du ett **Namn** och en valfri **Beskrivning** för tilldelningen och väljer sedan följande:
    - **Medlemmar** – Välj en grupp som innehåller den användare som du vill ge behörighet.
    - **Omfång** – Välj en grupp som innehåller de användare som ovanstående medlem ska kunna hantera.
<br></br>
5. När du är klar klickar du på **OK**. Den nya tilldelningen visas i listan över tilldelningar.

### <a name="intune-rbac-table"></a>Intune RBAC-tabell

- Hämta [Intune RBA-tabellen](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) för att visa mer information om vad varje roll kan göra.

## <a name="custom-roles"></a>Anpassade roller

Du kan skapa en anpassad roll som innehåller alla behörigheter som krävs för en viss arbetsfunktion. Till exempel, om en IT-avdelningsgrupp hanterar applikationer, principer och konfigurationsprofiler kan du lägga till alla dessa behörigheter i en enda anpassad roll.

> [!IMPORTANT]
> För att kunna skapa, redigera eller tilldela roller måste ditt konto ha en av följande behörigheter i Azure AD:
> - **Global administratör**
> - **Intune Service-administratör**

### <a name="to-create-a-custom-role"></a>Skapa en anpassad roll

1. Logga in i [Azure-portalen](https://portal.azure.com) med dina inloggningsuppgifter för Intune.

2. Välj **Fler tjänster** på den vänstra menyn och skriv sedan **Intune** i textrutefiltret.

3. Välj **Intune** Kontrollpanelen för Intune öppnas. Välj **Intune-roller**.

4. Välj **Intune-roller** på **Intune-bladet** och välj **Lägg till anpassad**.

5. På bladet **Lägg till anpassad roll** anger du namn och beskrivning för den nya rollen och klickar sedan på **Behörigheter**.

3. På bladet **Behörigheter** väljer du de behörigheter som du vill använda med den här rollen. Använd [Intune RBAC-tabellen](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) för att avgöra vilka behörigheter som du vill använda.

4. När du är klar väljer du **OK**.

5. På bladet **Lägg till anpassad roll** klickar du på **Skapa**. Den nya rollen visas i listan på bladet **Intune-roller**.

### <a name="to-assign-a-custom-role"></a>Tilldela en anpassad roll

1. På **Intune-roller** väljer du den anpassade rollen som du vill tilldela.

2. På bladet <*rollnamn*> – **Egenskaper** väljer du **Hantera** och därefter **Tilldelningar**. På det här bladet kan du även redigera eller ta bort befintliga roller.

3. På bladet anpassad roll väljer du **Tilldela**.

4. På bladet **Rolltilldelningar** anger du ett **Namn** och en valfri **Beskrivning** för tilldelningen och väljer sedan följande:
    - **Medlemmar** – Välj en grupp som innehåller den användare som du vill ge behörighet.
    - **Omfång** – Välj en grupp som innehåller de användare som ovanstående medlem ska kunna hantera.
<br></br>
5. När du är klar klickar du på **OK**. Den nya tilldelningen visas i listan över tilldelningar.

## <a name="next-steps"></a>Nästa steg

[Använda operatörsrollen för Intune-hjälpavdelningen med felsökningsportalen](help-desk-operators.md)

## <a name="see-also"></a>Se även

[Tilldela roller med hjälp av Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
