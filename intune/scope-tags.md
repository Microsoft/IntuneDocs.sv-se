---
title: Filtrera principer med omfångstaggar i Microsoft Intune – Azure | Microsoft Docs
description: Använd omfångstaggar för att filtrera konfigurationsprofiler för specifika roller.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba1d7669e80fd91398f41c57ca2d27ce78a06041
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403807"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT

Du kan använda rollbaserad åtkomstkontroll och omfångstaggar för att se till att rätt administratörer har rätt åtkomst och synlighet för rätt Intune-objekt. Roller avgör vilken åtkomst administratörer har till vilka objekt. Omfångstaggar avgör vilka objekt administratörer kan se.

Anta exempelvis att en regional kontorsadministratör i Seattle tilldelas rollen Princip- och profilhanterare. Du vill att den här administratören endast ska se och hantera profiler och principer som gäller för Seattle-enheter. För att göra det här skulle du:

1. Skapa en omfångstagg som heter Seattle.
2. Skapa en rolltilldelning för rollen Princip- och profilhanterare med: 
    - Medlemmar (Grupper) = en säkerhetsgrupp som heter IT-administratörer i Seattle. Alla administratörer i den här gruppen får behörighet att hantera principer och profiler för användare/enheter i Omfånget (Grupper).
    - Omfång (Grupper) = en säkerhetsgrupp som heter Användare i Seattle. Profiler och principer för alla användare/enheter i den här gruppen kan hanteras av administratörerna i Medlemmar (Grupper). 
    - Omfång (Taggar) = Seattle. Administratörer i Medlemmar (Grupper) kan se de enheter som har också omfångstaggen Seattle.
3. Lägg till omfångstaggen Seattle i principer och profiler som du vill att administratörer i Medlemmar (Grupper) ska kunna komma åt.
4. Lägga till omfångstaggen Seattle till enheter som ska vara synliga för administratörer i Medlemmar (Grupper). 


## <a name="to-create-a-scope-tag"></a>Skapa en omfångstagg

1. I Intune väljer du **Roller** > **Omfång (taggar)**  > **Skapa**.

    ![Skärmbild av skapande av en omfångstagg.](./media/scope-tags/create-scope-tag.png)

3. Om du vill att alla enheter i specifika grupper, Välj **tilldelas alla enheter i valda grupper omfångstaggen**.
    1. I den **Välj grupper att ta** väljer du de grupper som innehåller de enheter som du vill tilldela den här omfångstaggen till.
    2. Välj **Välj**.
4. Välj **Skapa**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Tilldela en omfångstagg till en roll

1. I Intune väljer du **Roller** > **Alla roller** > välj en roll > **Tilldelningar** > **Tilldela**.

    ![Skärmbild av tilldelning av omfång till en roll.](./media/scope-tags/assign-scope-to-role.png)

2. Ange ett **Tilldelningsnamn** och en **Beskrivning**.
3. Välj **Medlemmar (Grupper)**  > **Lägg till** > välj de grupper som du vill ha som en del av tilldelningen > **Välj** > **OK**. Användare i den här gruppen får behörighet att hantera principer och profiler för användare/enheter i Omfånget (Grupper).

    ![Skärmbild av val av medlemsgrupper.](./media/scope-tags/select-member-groups.png)

4. Om du vill hantera användare/enheter i en specifik uppsättning grupper väljer du **Omfång (Grupper)**  > **Valda grupper** > **Välj grupper som ska inkluderas**> välj grupperna > **Välj** > **OK**. Profiler och principer för alla användare/enheter i den här gruppen kan hanteras av administratörerna i Medlemmar (Grupp).

    ![Skärmbild av val av omfångsgrupper.](./media/scope-tags/select-scope-groups.png)

    Alternativt kan du välja **Alla enheter**, **Alla användare** eller **Alla användare och alla enheter**.

    ![Skärmbild av andra alternativ för val av omfångsgrupper.](./media/scope-tags/scope-group-other-options.png)
    
5. Välj **Omfång (Taggar)**  > **Lägg till** > välj de taggar som du vill lägga i den här rollen > **Välj** > **OK**. Användare i Medlemmar (Grupper) får åtkomst till de principer och profiler som också har samma omfångstagg.

    ![Skärmbild av val av omfångstaggar.](./media/scope-tags/select-scope-tags.png)

6. Välj **OK**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Lägga till en omfångstagg i en konfigurationsprofil
1. I Intune väljer du **Enhetskonfiguration** > **Profiler** > välj en profil.

    ![Skärmbild av val av profil.](./media/scope-tags/choose-profile.png)

2. Välj **Egenskaper** > **Omfång (Taggar)**  > **Lägg till**.

    ![Skärmbild av tillägg av omfångstaggar.](./media/scope-tags/add-scope-tags.png)

3. Under **Välj taggar** väljer du de taggar som du vill lägga till i profilen.
4. Välj **Välj** > **OK** > **Spara**.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Tilldela en omfångstagg till en appkonfigurationsprincip
För enheter med **Enhetsregistreringstyp** inställd på **Hanterade enheter**:
1. Välj **Klientappar** > **Appkonfigurationsprinciper** > välj en appkonfigurationsprincip.
2. Välj **Egenskaper** > **Omfång (Taggar)** > välj de taggar som du vill tilldela till principen.

För enheter med **Enhetsregistreringstyp** inställd på **Hanterade appar**:
1. Välj **Klientappar** > **Appkonfigurationsprinciper** > välj en appkonfigurationsprincip.
2. Välj **Omfång (Taggar)** > välj de taggar som du vill tilldela till principen.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Tilldela en omfångstagg till en etableringsprofil för iOS-app
1. I Intune väljer du **Klientappar** > **iOS-appetableringsprofiler** > välj en profil.
2. Välj **Egenskaper** > **Omfång (Taggar)** > välj de taggar som du vill tilldela till profilen.
3. Välj **Välj** > **OK** > **Spara**.

## <a name="to-assign-a-scope-tag-to-an-apple-volume-purchase-program-vpp-token"></a>Tilldela en omfångstagg till en VPP-token (Apples volymköpsprogram)
1. I Intune väljer du **Klientappar** > **Apple VPP-token** > välj en VPP-token.
2. Välj **Omfång (Taggar)** > välj de taggar som du vill tilldela till profilen. De VPP-appar och e-böcker som är associerade med VPP-token ärver de tilldelade taggarna.
3. Välj **Välj** > **OK** > **Spara**.

## <a name="scope-tag-details"></a>Information om omfångstaggar
När du arbetar med omfångstaggar bör du beakta följande:

- För närvarande kan du tilldela omfångstaggar till:
    - Rolltilldelningar
    - Efterlevnadsprinciper för enheter
    - Enhetens konfigurationsprofiler
    - Windows 10-uppdateringsringar
    - Hanterade enheter
    - Appar
    - Appkonfigurationsprinciper – hanterade enheter
    - PowerShell-skript
    - DEP-token
    - iOS-appetableringsprofil
    - VPP-token (volyminköpsprogram)
- När en administratör skapar ett objekt i Intune tilldelas alla omfångstaggar som tilldelats till den administratören automatiskt till det nya objektet.
- Intune RBAC gäller inte för Azure Active Directory-roller. Därför har rollerna Intune-tjänstadministratörer och Globala administratörer fullständig administratörsåtkomst till Intune oavsett vilka omfångstaggar de har.
- Administratörer i en rolltilldelning med omfångstaggar kan även se Intune-objekt utan omfångstaggar.
- Du kan endast tilldela en omfångstagg som du har i dina rolltilldelningar.
- Du kan endast ange grupper som visas i Omfång (Grupper) för din rolltilldelning som mål.
- Om du har en omfångstagg tilldelad till din roll kan du inte ta bort alla omfångstaggar på ett Intune-objekt. Det krävs minst en omfångstagg.

## <a name="next-steps"></a>Nästa steg

Hantera dina [roller](role-based-access-control.md) och [profiler](device-profile-assign.md).
