---
title: RBAC med Microsoft Intune
description: Läs hur du med rollbaserad åtkomstkontroll (RBAC) kan styra vem som får utföra åtgärder och göra ändringar i Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08e6c7657eeba7a41b9927e736fe7f4fc07e25e6
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848584"
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>Rollbaserad administrationskontroll (RBAC) med Microsoft Intune

RBAC hjälper dig att styra vem som kan utföra olika uppgifter för Intune i din organisation och vem aktiviteterna gäller för. Du kan antingen använda de inbyggda roller täcker vissa vanliga scenarier för Intune eller du kan skapa egna roller. En roll definieras av:

- **Rolldefinition**: Namnet på rollen, de resurser som den hanterar och behörigheterna för varje resurs.
- **Medlemmar**: De användargrupper som har behörigheterna.
- **Omfång**: Användar- eller enhetsgrupper som medlemmarna kan hantera.
- **Tilldelning**: När definitionen, medlemmar och omfång har konfigurerats är rollen tilldelad.

![Intune RBAC-exempel](./media/intune-rbac-1.PNG)

**Azure Active Directory (AD Azure)** innehåller två katalogroller som kan användas med Intune, med start i den nya Azure-portalen. Rollerna beviljas fullständig behörighet för att utföra alla aktiviteter i Intune:

- **Global administratör:** Användare med den här rollen har åtkomst till alla administrativa funktioner i Azure Active Directory, samt tjänster som är underordnade Azure Active Directory som Exchange Online, SharePoint Online och Skype för företag Online. Personen som registrerar sig för Azure AD-klient blir global administratör. Endast globala administratörer kan tilldela andra administratörsroller i Azure AD. Det kan finnas mer än en global administratör i din organisation. Globala administratörer kan återställa lösenordet för alla användare och alla andra administratörer.

- **Intune Service-administratör:** Användarna med den här rollen har globala behörigheter i Intune när tjänsten finns. Förutom eventuella ersättande Azure-begränsningar ger den här rollen möjlighet att hantera användare och enheter samt skapa och hantera Intune-grupper.

- **Administratör av villkorsstyrd åtkomst:** Användare med den här rollen har endast behörighet att visa, skapa, ändra och ta bort principer för villkorlig åtkomst.

    > [!IMPORTANT]
    > Rollen som Intune Service-administratör ger inte möjlighet att hantera inställningar för villkorlig åtkomst i Azure AD.
    > För att bli tilldelad en Intune-roll, måste användaren ha en Intune-licens.

    > [!TIP]
    > Intune visar också tre tillägg för Azure Active Directory: **Användare**, **Grupper** och **Villkorlig åtkomst**, som kontrolleras med hjälp av Azure Active Directory RBAC. Dessutom kan den **Användarkontoadministratören** endast utför aktiviteter för AAD-användare/-grupp och har inte fullständig behörighet att utföra alla aktiviteter i Intune. Mer information finns i [RBAC med Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).

## <a name="roles-created-in-the-intune-classic-portal"></a>Roller som skapas i den klassiska Intune-portalen

Endast Intunes **tjänstadministratörer** med fullständig behörighet migreras från den klassiska Intune-portalen till Intune i Azure-portalen. Du måste tilldela Intune **Service-administratörer** igen med åtkomsten ”skrivskyddad” eller ”supportavdelning” till Intune-roller i Azure-portalen och ta bort dem från den klassiska portalen.

> [!IMPORTANT]
> Du kan behöva behålla Intunes tjänstadministratörsåtkomst i den klassiska portalen om dina administratörer fortfarande behöver åtkomst till att hantera datorer med Intune.

## <a name="built-in-roles"></a>Inbyggda roller

Du kan tilldela inbyggda roller till grupper utan ytterligare konfiguration. Du kan inte ta bort eller redigera en inbyggd roll.

- **Supportavdelningen**: Utför fjärråtgärder på användare och enheter och kan tilldela program eller principer till användare eller enheter.
- **Princip- och profilhanterare**: Hanterar principer för efterlevnad, konfigurationsprofiler, Apple-registrering och företagets enhetsidentifierare.
- **Användare med skrivskydd**: Visar information om användare, enhet, registrering, konfiguration och programmet. Kan inte göra ändringar i Intune.
- **Programhanterare**: Hanterar mobila och hanterade program, kan läsa enhetsinformation och kan visa enhetsinformationsprofiler.
- **Administratör för Intune-roll**: Hanterar anpassade Intune-roller och lägger till tilldelningar för inbyggda Intune-roller. Det är den enda Intune-rollen som kan tilldela behörigheter till administratörer.
- **Skoladministratör**: Hanterar Windows 10-enheter i [Intune for Education](introduction-intune-education.md) och kan vidta följande åtgärder: 

    |Behörigheter|Åtgärd|
    |---|---|
    |Granska data|Läs|
    |DeviceConfigurations|Tilldela, skapa, ta bort, läsa, uppdatera|
    |Hanterare av enhetsregistrering|Läsa, uppdatera|
    |Hanterade enheter|Läsa, uppdatera<!--, Delete [To be added in 1803]-->|
    |Mobilappar|Tilldela, skapa, ta bort, läsa, uppdatera|
    |Rapporter|Läs|
    |Fjärråtgärder|Rensa dator, starta om, fjärrlåsning, dra tillbaka, synkronisera enheter, rensa|
    |Organisation|Läs|

### <a name="to-assign-a-built-in-role"></a>Tilldela en inbyggd roll

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Roller** > **Alla roller**.
4. I fönstret **Intune-roller – Alla roller** väljer du den inbyggda rollen som du vill tilldela.

5. I fönstret <*rollnamn*> – fönstret **Översikt** väljer du **Hantera** och sedan **Tilldelningar**.

6. I fönstret för anpassad roll väljer du **Tilldela**.

7. I fönstret **Rolltilldelningar** anger du ett **Namn** och en valfri **Beskrivning** för tilldelningen.

8. För **Medlemmar**, välj en grupp som innehåller den användare som du vill ge behörighet.

9. För **Omfång**, välj en grupp som innehåller de användare som ovanstående medlem ska kunna hantera.
<br></br>
10. När du är klar väljer du **OK**. Den nya tilldelningen visas i listan över tilldelningar.

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

2. Välj **Alla tjänster** i den vänstra menyn och skriv sedan **Intune** i textrutans filter.

3. Välj **Intune** > **Roller** > **Alla roller** > **Lägg till anpassad**.

4. I fönstret **Lägg till anpassad roll** anger du namn och beskrivning för den nya rollen och klickar sedan på **Behörigheter**.

5. I fönstret **Behörigheter** väljer du de behörigheter som du vill använda med den här rollen. Använd [Intune RBAC-tabellen](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) för att avgöra vilka behörigheter som du vill använda.

6. När du är klar väljer du **OK**.

7. I fönstret **Lägg till anpassad roll** klickar du på **Skapa**. Den nya rollen visas i listan i fönstret **Intune-roller – Alla roller**.

### <a name="to-assign-a-custom-role"></a>Tilldela en anpassad roll

1. I fönstret **Intune-roller – Alla roller** väljer du den anpassade rollen som du vill tilldela.

2. I fönstret <*rollnamn*> – fönstret **Översikt** väljer du **Hantera** och sedan **Tilldelningar**. I det här fönstret kan du även redigera eller ta bort befintliga roller.

3. I fönstret för anpassad roll väljer du **Tilldela**.

4. I fönstret **Rolltilldelningar** anger du ett **Namn** och en valfri **Beskrivning** för tilldelningen.

5. För **Medlemmar**, välj en grupp som innehåller den användare som du vill ge behörighet.

6. För **Omfång**, välj en grupp som innehåller de användare som ovanstående medlem ska kunna hantera.

7. När du är klar väljer du **OK**. Den nya tilldelningen visas i listan över tilldelningar.

## <a name="next-steps"></a>Nästa steg

[Använda operatörsrollen för Intune-hjälpavdelningen med felsökningsportalen](help-desk-operators.md)

## <a name="see-also"></a>Se även

[Tilldela roller med hjälp av Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
