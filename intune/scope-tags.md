---
title: Använd rollbaserad åtkomst kontroll (RBAC) och omfångs etiketter för distribuerat den i Intune | Microsoft Docs
description: Använd omfångstaggar för att filtrera konfigurationsprofiler för specifika roller.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2fb82b02057e1e028755da16a05755b0b8ddb93a
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163807"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT

Du kan använda rollbaserad åtkomstkontroll och omfångstaggar för att se till att rätt administratörer har rätt åtkomst och synlighet för rätt Intune-objekt. Roller avgör vilken åtkomst administratörer har till vilka objekt. Omfångstaggar avgör vilka objekt administratörer kan se.

Anta exempelvis att administratören på regionkontoret i Seattle har rollen som princip- och profilhanterare. Du vill att den här administratören endast ska se och hantera profiler och principer som gäller för Seattle-enheter. Om du vill konfigurera den här åtkomsten gör du följande:

1. Skapa en omfångstagg som heter Seattle.
2. Skapa en rolltilldelning för rollen Princip- och profilhanterare med: 
    - Medlemmar (Grupper) = en säkerhetsgrupp som heter IT-administratörer i Seattle. Alla administratörer i den här gruppen får behörighet att hantera principer och profiler för användare/enheter i Omfånget (Grupper).
    - Omfång (Grupper) = en säkerhetsgrupp som heter Användare i Seattle. Profiler och principer för alla användare/enheter i den här gruppen kan hanteras av administratörerna i Medlemmar (Grupper). 
    - Omfång (Taggar) = Seattle. Administratörer i Medlemmar (Grupper) kan se Intune-objekt som även har omfångstaggen Seattle.
3. Lägg till omfångstaggen Seattle i principer och profiler som du vill att administratörer i Medlemmar (Grupper) ska kunna komma åt.
4. Lägga till omfångstaggen Seattle till enheter som ska vara synliga för administratörer i Medlemmar (Grupper). 

## <a name="default-scope-tag"></a>Standardomfångstagg
Standard omfångs tag gen läggs automatiskt till i alla otaggade objekt som stöder omfångs taggar.

Funktionen för standardomfångstaggar liknar funktionen för säkerhetsomfång i System Center Configuration Manager. 

## <a name="to-create-a-scope-tag"></a>Skapa en omfångstagg

1. I Intune väljer du **Roller** > **Omfång (taggar)**  > **Skapa**.

    ![Skärmbild av skapande av en omfångstagg.](./media/scope-tags/create-scope-tag.png)

3. Om du vill använda alla enheter i vissa grupper väljer du **tilldela scope-tagg till alla enheter i valda grupper**.
    1. På sidan **Välj grupper att inkludera** väljer du de grupper som innehåller de enheter som du vill tilldela den här omfångs tag gen till.
    2. Välj **Välj**.
4. Välj **Skapa**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Tilldela en omfångstagg till en roll

1. I Intune väljer du **Roller** > **Alla roller** > välj en roll > **Tilldelningar** > **Tilldela**.

    ![Skärmbild av tilldelning av omfång till en roll.](./media/scope-tags/assign-scope-to-role.png)

2. Ange ett **Tilldelningsnamn** och en **Beskrivning**.
3. Välj **Medlemmar (Grupper)**  > **Lägg till** > välj de grupper som du vill ha som en del av tilldelningen > **Välj** > **OK**. Användare i den här gruppen har behörighet att hantera användare/enheter i omfånget (grupper).

    ![Skärmbild av val av medlemsgrupper.](./media/scope-tags/select-member-groups.png)

4. Om du vill hantera användare/enheter i en specifik uppsättning grupper väljer du **Omfång (Grupper)**  > **Valda grupper** > **Välj grupper som ska inkluderas**> välj grupperna > **Välj** > **OK**. Alla användare/enheter i den här gruppen hanteras av administratörerna i medlemmarna (gruppen).

    ![Skärmbild av val av omfångsgrupper.](./media/scope-tags/select-scope-groups.png)

    Alternativt kan du välja **Alla enheter**, **Alla användare** eller **Alla användare och alla enheter**.

    ![Skärmbild av andra alternativ för val av omfångsgrupper.](./media/scope-tags/scope-group-other-options.png)
    
5. Välj **Omfång (Taggar)**  > **Lägg till** > välj de taggar som du vill lägga i den här rollen > **Välj** > **OK**. Användare i medlemmar (grupper) har åtkomst till Intune-objekt som också har samma scope-tagg.

    ![Skärmbild av val av omfångstaggar.](./media/scope-tags/select-scope-tags.png)

6. Välj **OK**. 

## <a name="assign-scope-tags-to-other-objects"></a>Tilldela omfångs etiketter till andra objekt

För objekt som stöder omfångs taggar visas omfångs Taggar vanligt vis under **Egenskaper**. Om du till exempel vill tilldela en scope-tagg till en konfigurations profil följer du dessa steg:

1. I Intune väljer du **Enhetskonfiguration** > **Profiler** > välj en profil.

    ![Skärmbild av val av profil.](./media/scope-tags/choose-profile.png)

2. Välj **Egenskaper** > **Omfång (Taggar)**  > **Lägg till**.

    ![Skärmbild av tillägg av omfångstaggar.](./media/scope-tags/add-scope-tags.png)

3. Under **Välj taggar** väljer du de taggar som du vill lägga till i profilen.
4. Välj **Välj** > **OK** > **Spara**.


## <a name="scope-tag-details"></a>Information om omfångstaggar
När du arbetar med omfångstaggar bör du beakta följande: 

- Du kan tilldela omfångs koder till en Intune-objekttyp om klienten kan ha flera versioner av objektet (till exempel roll tilldelningar eller appar).
  Följande Intune-objekt är undantag till den här regeln och stöder för närvarande inte omfångs Taggar:
    - Windows ESP-profiler
    - Enhetskategorier
    - Registreringsbegränsningar
    - Företags enhets identifierare
    - Autopilot-enheter
    - Platser för enhetskompatibilitet
    - JAMF-enheter
- VPP-appar och e-böcker som är kopplade till VPP-token ärver de omfångs koder som tilldelats den associerade VPP-token
- Programmet för enhetsregistrering (DEP) enheter och DEP-profiler som är associerade med DEP-token ärver omfångs koderna som tilldelats till den associerade DEP-token.
- När en administratör skapar ett objekt i Intune tilldelas alla omfångstaggar som tilldelats till den administratören automatiskt till det nya objektet.
- Intune RBAC gäller inte för Azure Active Directory-roller. Därför har rollerna Intune-tjänstadministratörer och Globala administratörer fullständig administratörsåtkomst till Intune oavsett vilka omfångstaggar de har.
- Om en roll tilldelning saknar omfångs tagg kan IT-administratören se alla objekt baserat på IT-administratörernas behörigheter. Administratörer som inte har några omfångs etiketter har huvudsakligen alla omfångs koder.
- Du kan endast tilldela en omfångstagg som du har i dina rolltilldelningar.
- Du kan endast ange grupper som visas i Omfång (Grupper) för din rolltilldelning som mål.
- Om du har en omfångstagg tilldelad till din roll kan du inte ta bort alla omfångstaggar på ett Intune-objekt. Det krävs minst en omfångstagg.

## <a name="next-steps"></a>Nästa steg

Lär dig hur omfångs Taggar fungerar när det finns [flera roll tilldelningar](role-based-access-control.md#multiple-role-assignments).
Hantera dina [roller](role-based-access-control.md) och [profiler](device-profile-assign.md).
