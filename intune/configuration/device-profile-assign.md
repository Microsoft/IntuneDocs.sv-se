---
title: Tilldela enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Använd Azure-portalen för att tilldela enhetsprofiler och principer till användare och enheter. Lär dig att undanta grupper från en profiltilldelning i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50b91251572e45669f197df7ac4e5ff94caf47a1
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755329"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Tilldela användar- och enhetsprofiler i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Du skapar en profil som innehåller alla inställningar som du har angett. Nästa steg är att distribuera eller ”tilldela” profilen till din användare eller dina enhetsgrupper i Azure Active Directory (Azure AD). När den är tilldelad får användarna och enheterna din profil och de inställningar som du har angett tillämpas.

Den här artikeln visar hur du tilldelar en profil, samt innehåller information om hur du använder omfångstaggar på dina profiler.

> [!NOTE]  
> När en princip tas bort eller inte längre är tilldelad till någon enhet kan det hända att inställningen har kvar det befintliga värdet. Inställningen återgår inte till standardvärdet. Om du vill ändra inställningen till ett annat värde skapar du en ny princip och tilldelar den.

## <a name="before-you-begin"></a>Innan du börjar

Se till att du har rätt roll för att tilldela principer. Mer information finns i [Rollbaserad åtkomstkontroll (RBAC) med Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="assign-a-device-profile"></a>Tilldela en enhetsprofil

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler**. Alla profilerna visas i listan.
3. Välj den profil som du vill tilldela > **Tilldelningar**.
4. Välj om du vill **inkludera** eller **exkludera** grupper och välj sedan grupperna. När du väljer dina grupper väljer du en Azure AD-grupp. Håll ned **Ctrl**-tangenten om du vill markera flera grupper.

    ![Skärmbild med alternativ för att inkludera eller exkludera grupper från en profiltilldelning](./media/device-profile-assign/group-include-exclude.png)

5. **Spara** ändringarna.

### <a name="evaluate-how-many-users-are-targeted"></a>Utvärdera hur många användare som omfattas

När du tilldelar profilen kan du också **utvärdera** hur många användare som påverkas. Den här funktionen beräknar användare, den beräknar inte enheter.

1. I administrationscentret väljer du **Enheter** > **Konfigurationsprofiler**.
2. Välj en profil > **Tilldelningar** > **Utvärdera**. Ett meddelande visas med hur många användare som omfattas av profilen.

Om knappen **Utvärdera** är nedtonad, kontrollerar du att profilen har tilldelats till en eller flera grupper.

## <a name="use-scope-tags-or-applicability-rules"></a>Använd omfångstaggar eller tillämpbarhetsregler

När du skapar eller uppdaterar en profil, kan du också lägga till omfångstaggar och tillämpbarhetsregler i profilen.

**Omfångstaggar** är ett bra sätt för att tilldela och filtrera principer till specifika grupper, till exempel Personal eller Alla amerikanska NC-anställda. Mer information finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).

På Windows 10-enheter kan du lägga till **tillämpbarhetsregler** så att profilen endast gäller för en speciell OS-version eller en speciell Windows-version. [Tillämpbarhetsregler](device-profile-create.md#applicability-rules) innehåller mer information.

## <a name="exclude-groups-from-a-profile-assignment"></a>Exkludera grupper från en profiltilldelning

Med hjälp av Intunes profiler för enhetskonfiguration kan du inkludera och exkludera grupper från principtilldelningen.

Vi rekommenderar att du skapar och tilldelar principer som är specifika för dina användargrupper. Du kan även skapa och tilldela olika principer specifikt för dina enhetsgrupper. Mer information om grupper finns i [Lägga till grupper för att organisera användare och enheter](../fundamentals/groups-add.md).

När du tilldelar principerna använder du följande tabell till att inkludera och exkludera grupper. En bockmarkering innebär att tilldelningen stöds:

![Alternativ som stöds för att inkludera eller exkludera grupper från en profiltilldelning](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>Det här bör du veta

- Undantag har företräde framför inkludering i följande scenarier för grupptyper:

  - Inkludera och exkludera användargrupper
  - Inkludera och exkludera enhetsgrupper

  Du kan t.ex. tilldela en enhetsprofil till användargruppen **Alla företagsanvändare** men välja att exkludera medlemmar i användargruppen **Ledningsgrupp**. Eftersom båda grupperna är användargrupper får **Alla företagsanvändare** förutom **Ledningsgrupp** principen.

- Intune utvärderar inte grupprelationer från användare till enhet. Om du tilldelar principer till blandade grupper, kanske resultatet inte blir det du vill ha eller förväntar dig.

  Du kan till exempel tilldela en enhetsprofil till användargruppen **Alla användare**, men undanta enhetsgruppen **Alla personliga enheter**. I den här blandade grupprinciptilldelningen får **Alla användare** principen. Undantaget tillämpas inte.

  Därför rekommenderar vi inte att du tilldelar principer till blandade grupper.

## <a name="next-steps"></a>Nästa steg

Se avsnittet om att [övervaka enhetsprofiler](device-profile-monitor.md) för anvisningar om hur du övervakar dina profiler och de enheter som kör dina profiler.
