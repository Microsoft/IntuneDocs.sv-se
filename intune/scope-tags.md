---
title: Filtrera principer med omfångstaggar i Microsoft Intune – Azure | Microsoft Docs
description: Använd omfångstaggar för att filtrera konfigurationsprofiler för specifika roller.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb57ea2ef5c99c58968ee25b3a75b2165ece787a
ms.sourcegitcommit: 0adb41c0640743d5cb726e66ad2427e3ad6faf20
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658557"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerade IT

Rollbaserad åtkomst kontroll och omfång taggar kan användas för att se till att rätt administratörer har rätt åtkomst och synlighet till rätt Intune-objekt. Roller avgör vilken åtkomst administratörer har vilka objekt. Omfångstaggar avgör vilka objekt som administratörer kan se.

Anta exempelvis att en Seattle lokalkontor administratör tilldelas rollen princip- och profilhanterare. Du vill att den här administratören att se och hantera profiler och principer som gäller endast för Seattle-enheter. Om du vill göra detta måste utföra du följande:

1. Skapa en omfångstagg kallas Seattle.
2. Skapa en rolltilldelning för princip- och profilhanterare med: 
    - Medlemmar (grupper) = en säkerhetsgrupp med namnet Seattle IT-administratörer. Alla administratörer i den här gruppen har behörighet att hantera principer och profiler för användare/enheter i omfång (grupper).
    - Omfång (grupper) = en grupp med namnet Seattle användare. Alla användare/enheter i den här gruppen kan ha sina profiler och principer som hanteras av administratörer i medlemmar (grupper). 
    - Omfång (taggar) = Seattle. Administratörer i medlemmar (grupper) kan se de enheter som har också omfångstaggen Seattle.
3. Lägg till Seattle omfångstaggen principer och profiler som du vill att administratörer i medlemmar (grupper) för att kunna komma åt.
4. Lägga till Seattle omfångstaggen till enheter som ska visas för administratörer i medlemmar (grupper). 


## <a name="to-create-a-scope-tag"></a>Skapa en omfångstagg

1. I Intune väljer **roller** > **omfång (taggar)** > **skapa**.

    ![Skärmbild av taggen omfång.](./media/scope-tags/create-scope-tag.png)

2. Ange ett **namn** och en **beskrivning**.
3. Välj **Skapa**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Tilldela en omfångstagg till en roll

1. I Intune väljer **roller** > **alla roller** > Välj en roll > **tilldelningar** > **tilldela**.

    ![Skärmbild av tilldela omfång till en roll.](./media/scope-tags/assign-scope-to-role.png)

2. Ange en **tilldelningsnamn** och **beskrivning**.
3. Välj **medlemmar (grupper)** > **Lägg till** > Välj de grupper som du vill ha som en del av den här tilldelningen > **Välj**  >   **OK**. mUsers i den här gruppen har behörighet att hantera principer och profiler för användare/enheter i omfång (grupper).

    ![Skärmbild av väljer medlemsgrupper.](./media/scope-tags/select-member-groups.png)

4. Om du vill hantera användare/enheter i en specifik uppsättning grupper väljer **omfång (grupper)** > **valda grupper** > **Välj grupper att ta**> Välj grupperna > **Välj** > **OK**. Alla användare/enheter i den här gruppen kan ha sina profiler och principer som hanteras av administratörer i medlemmar (grupper).

    ![Skärmbild av väljer omfångsgrupper.](./media/scope-tags/select-scope-groups.png)

    Alternativt kan du välja **alla enheter**, **alla användare**, eller **alla användare och alla enheter**.

    ![Skärmbild av andra alternativ för väljer omfångsgrupper.](./media/scope-tags/scope-group-other-options.png)
    
5. Välj **omfång (taggar)** > **Lägg till** > Välj de taggar som du vill lägga till den här rollen > **Välj** > **OK**. Användare i medlemmar (grupper) får åtkomst till principer och profiler som också har samma omfattningstaggen.

    ![Skärmbild av väljer omfångstaggar.](./media/scope-tags/select-scope-tags.png)

6. Välj **OK**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Lägga till en omfångstagg i en konfigurationsprofil
1. I Intune väljer **enhetskonfiguration** > **profiler** > Välj en profil.

    ![Skärmbild av väljer profil.](./media/scope-tags/choose-profile.png)

2. Välj **egenskaper** > **omfång (taggar)** > **lägga till**.

    ![Skärmbild av Lägg till omfångstaggar.](./media/scope-tags/add-scope-tags.png)

3. Under **väljer taggar**, Välj de taggar som du vill lägga till profilen.
4. Välj **Välj** > **OK** > **spara**.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Tilldela en omfångstagg till en appkonfigurationsprincip
För enheter med **enhetsregistreringstyp** inställd **hanterade enheter**:
1. Välj **klientappar** > **appkonfigurationsprinciper** > Välj en appkonfigurationsprincip.
2. Välj **egenskaper** > **omfång (taggar)** > Välj de taggar som du vill tilldela till principen.

För enheter med **enhetsregistreringstyp** inställd **hanterade appar**:
1. Välj **klientappar** > **appkonfigurationsprinciper** > Välj en appkonfigurationsprincip.
2. Välj **omfång (taggar)** > Välj de taggar som du vill tilldela till principen.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Tilldela en omfångstagg till en iOS-app etableringsprofil
1. I Intune väljer **klientappar** > **iOS-appetableringsprofiler** > Välj en profil.
2. Välj **egenskaper** > **omfång (taggar)** > Välj de taggar som du vill tilldela till profilen.
3. Välj **Välj** > **OK** > **spara**.

## <a name="scope-tag-details"></a>Omfång tagginformation
När du arbetar med omfångstaggar kan du spara dessa uppgifter:

- För närvarande kan du tilldela omfångstaggar till:
    - Rolltilldelningar
    - Efterlevnadsprinciper för enheter
    - Enhetens konfigurationsprofiler
    - Windows 10 uppdateras ringar
    - Hanterade enheter
    - Appar
    - Konfigurationsprinciper för appar – hanterade enheter
    - PowerShell-skript
    - DEP-token
    - iOS-appetableringsprofil
- När en administratör skapar ett objekt i Intune, kommer alla omfångstaggar som tilldelats den administratören tilldelas automatiskt till det nya objektet.
- Intune RBAC gäller inte för Azure Active Directory-roller. Därför har rollerna Intune Service-administratörer och globala administratörer fullständig administratörsåtkomst till Intune oavsett vilken omfångstaggar som de har.
- Administratörer i en rolltilldelning med omfångstaggar kan också se Intune-objekt med inga omfångstaggar.
- Du kan endast tilldela en omfångstagg som du har i din rolltilldelningar.
- Du kan endast målgrupper som listas i omfång (grupper) för din rolltilldelning.
- Om du har en omfångstagg din roll kan du ta bort alla omfångstaggar på ett Intune-objekt. Minst en omfångstagg måste anges.

## <a name="next-steps"></a>Nästa steg

Hantera dina [roller](role-based-access-control.md) och [profiler](device-profile-assign.md).
