---
title: Rollbaserad åtkomstkontroll (RBAC) med Microsoft Intune
description: Lär dig hur RBAC kan användas för att kontrollera vem som kan utföra åtgärder och göra ändringar i Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5372d079b08a3a324d8ef1d98d26c07073ccd45
ms.sourcegitcommit: 49f25efb9bc0f16f587f27878cf45de5e4e6a27f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71094664"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>Rollbaserad åtkomstkontroll (RBAC) med Microsoft Intune

Med rollbaserad åtkomstkontroll (RBAC) kan du hantera vem som har åtkomst till organisationens resurser och vad de kan göra med dessa resurser.  Genom att [tilldela roller](assign-role.md) till dina Intune-användare kan du begränsa vad de kan se och ändra. Varje roll har en uppsättning behörigheter som avgör vad användare med den rollen kan komma åt och ändra i din organisation.

För att kunna skapa, redigera eller tilldela roller måste ditt konto ha en av följande behörigheter i Azure AD:
- **Global administratör**
- **Intune-tjänstadministratör** (även kallat **Intune-administratör**)

Du kan titta på den här serien med fem videor med exempel och demonstrationer för råd och förslag om Intune RBAC: [1](https://www.youtube.com/watch?v=5deXLMLcnKY), [2](https://www.youtube.com/watch?v=38dnMBLuxbQ), [3](https://www.youtube.com/watch?v=6vqg9cAkMbY), [4](https://www.youtube.com/watch?v=5yOLajFFMHE), [5](https://www.youtube.com/watch?v=P5DDvsSF4Wk).

## <a name="roles"></a>Roller
En roll definierar en den uppsättning behörigheter som beviljas till användare som tilldelas den rollen.
Du kan använda både de inbyggda och de anpassade rollerna. Inbyggda roller omfattar några vanliga Intune-scenarier. Du kan [skapa dina egna anpassade roller](create-custom-role.md) med den exakt uppsättning behörigheter som du behöver. Flera Azure Active Directory-roller har behörigheter till Intune.
Om du vill se en roll väljer du **Intune** > **Roller** > **Alla roller** > välj en roll. Följande sidor visas:

- **Egenskaper**: Namn, beskrivning, typ, tilldelningar och omfångstaggar för rollen. 
- **Behörigheter**: Visar en lång uppsättning växlar som definierar vilka behörigheter rollen har.
- **Tilldelningar**: En lista över [rolltilldelningar]( assign-role.md) som definierar vilka användare som har åtkomst till vilka användare/enheter. En roll kan ha flera tilldelningar och en användare kan vara i flera tilldelningar.

### <a name="built-in-roles"></a>Inbyggda roller
Du kan tilldela inbyggda roller till grupper utan ytterligare konfiguration. Du kan inte ta bort eller redigera namn, beskrivning, typ eller behörigheter för en inbyggd roll.

- **Supportavdelningen**: Utför fjärråtgärder på användare och enheter och kan tilldela program eller principer till användare eller enheter.
- **Princip- och profilhanterare**: Hanterar principer för efterlevnad, konfigurationsprofiler, Apple-registrering, företagsenhetsidentifierare samt säkerhetsbaslinjer.
- **Användare med skrivskydd**: Visar information om användare, enhet, registrering, konfiguration och programmet. Kan inte göra ändringar i Intune.
- **Programhanterare**: Hanterar mobila och hanterade program, kan läsa enhetsinformation och kan visa enhetsinformationsprofiler.
- **Administratör för Intune-roll**: Hanterar anpassade Intune-roller och lägger till tilldelningar för inbyggda Intune-roller. Det är den enda Intune-rollen som kan tilldela behörigheter till administratörer.
- **Skoladministratör**: Hanterar Windows 10-enheter i [Intune for Education](introduction-intune-education.md).

### <a name="custom-roles"></a>Anpassade roller
Du kan skapa egna roller med anpassade behörigheter. Mer information om anpassade roller finns i [Skapa en anpassad roll](create-custom-role.md).

### <a name="azure-active-directory-roles-with-intune-access"></a>Azure Active Directory-roller med Intune-åtkomst
| Azure Active Directory-roll | Alla Intune-data | Intune-granskningsdata |
| --- | :---: | :---: |
| Global administratör | Läsning/skrivning | Läsning/skrivning |
| Intune Service-administratör | Läsning/skrivning | Läsning/skrivning |
| Administratör för villkorsstyrd åtkomst | Inga | Inga |
| Säkerhetsadministratör | Skrivskyddad | Skrivskyddad |
| Säkerhetsoperatör | Skrivskyddad | Skrivskyddad |
| Säkerhetsläsare | Skrivskyddad | Skrivskyddad |
| Efterlevnadsadministratör | Inga | Skrivskyddad |
| Efterlevnadsdataadministratör | Inga | Skrivskyddad |

> [!TIP]
> Intune visar också tre tillägg för Azure Active Directory: **Användare**, **Grupper** och **Villkorlig åtkomst**, som kontrolleras med hjälp av Azure Active Directory RBAC. Dessutom kan den **Användarkontoadministratören** endast utför aktiviteter för AAD-användare/-grupp och har inte fullständig behörighet att utföra alla aktiviteter i Intune. Mer information finns i [RBAC med Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).
### <a name="roles-created-in-the-intune-classic-portal"></a>Roller som skapas i den klassiska Intune-portalen
Endast Intunes **tjänstadministratörer** med fullständig behörighet migreras från den klassiska Intune-portalen till Intune i Azure-portalen. Du måste tilldela Intune **Service-administratörer** igen med åtkomsten ”skrivskyddad” eller ”supportavdelning” till Intune-roller i Azure-portalen och ta bort dem från den klassiska portalen.
> [!IMPORTANT]
> Du kan behöva behålla Intunes tjänstadministratörsåtkomst i den klassiska portalen om dina administratörer fortfarande behöver åtkomst till att hantera datorer med Intune.

## <a name="role-assignments"></a>Rolltilldelningar
En rolltilldelning definierar:

- vilka användare som har tilldelats rollen
- vilka resurser de kan se
- vilka resurser de kan ändra.

Du kan tilldela användarna både anpassade och inbyggda roller. För att bli tilldelad en Intune-roll, måste användaren ha en Intune-licens.
Om du vill se en rolltilldelning väljer du **Intune** > **Roller** > **Alla roller** > välj en roll > välj en tilldelning. Följande sidor visas:

- **Egenskaper**: Namn, beskrivning, roll, medlemmar, omfång och taggar för tilldelningen.
- **Medlemmar**: Alla användare i de angivna Azure-säkerhetsgrupperna har behörighet att hantera de användare/enheter som anges i Omfång (grupper).
- **Omfång (grupper)** : Alla användare/enheter i de här Azure- säkerhetsgrupperna kan hanteras av användarna i Medlemmar.
- **[Omfång (taggar)](scope-tags.md)** : Användare i Medlemmar kan se de resurser som har samma omfångstaggar.

### <a name="multiple-role-assignments"></a>Flera rolltilldelningar
Om en användare har flera rolltilldelningar, behörigheter och omfångstaggar, utökas dessa rolltilldelningarna till olika objekt på följande sätt:

- Tilldelningsbehörigheter och omfångstaggar gäller endast för objekten (till exempel principer eller appar) i den rollens tilldelningsomfång (grupper). Tilldelningsbehörigheter och omfångstaggar gäller inte för objekt i andra rolltilldelningar såvida inte den andra tilldelningen uttryckligen beviljar dem.
- Andra behörigheter (till exempel Skapa, Läsa, Uppdatera, Ta bort) och omfångstaggar gäller för alla objekt av samma typ (som alla principer eller alla appar) i alla tilldelningar för användaren.
- Behörigheter och omfångstaggar för olika typer av objekt (till exempel principer eller appar) gäller inte för varandra. Till exempel ger inte en läsningsbehörighet för en princip läsningsbehörighet till appar i användarens tilldelningar.

## <a name="next-steps"></a>Nästa steg
- [Tilldela en användare en roll](assign-role.md)
- [Skapa en anpassad roll](create-custom-role.md)
