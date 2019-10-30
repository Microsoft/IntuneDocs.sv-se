---
title: Tilldela enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Använd Azure-portalen för att tilldela enhetsprofiler och principer till användare och enheter. Lär dig att undanta grupper från en profiltilldelning i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26ed23e4d9d267e37ba5088fa32234c27e3935b6
ms.sourcegitcommit: 9a2ddcec73b37a118908b63d8e5252835f257618
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72550801"
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

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler**. Alla profilerna visas i listan.
3. Välj den profil som du vill tilldela > **Tilldelningar**.
4. Välj om du vill **inkludera** eller **exkludera** grupper och välj sedan grupperna. När du väljer dina grupper väljer du en Azure AD-grupp. Håll ned **Ctrl**-tangenten om du vill markera flera grupper.

    ![Skärmbild med alternativ för att inkludera eller exkludera grupper från en profiltilldelning](./media/device-profile-assign/group-include-exclude.png)

5. **Spara** ändringarna.

### <a name="evaluate-how-many-users-are-targeted"></a>Utvärdera hur många användare som omfattas

När du tilldelar profilen kan du också **utvärdera** hur många användare som påverkas. Den här funktionen beräknar användare, den beräknar inte enheter.

1. Välj **Enhetskonfiguration** > **Profiler** i Intune.
2. Välj en profil > **Tilldelningar** > **Utvärdera**. Ett meddelande visas med hur många användare som omfattas av profilen.

Om knappen **Utvärdera** är nedtonad, kontrollerar du att profilen har tilldelats till en eller flera grupper.

## <a name="use-scope-tags-or-applicability-rules"></a>Använd omfångstaggar eller tillämpbarhetsregler

När du skapar eller uppdaterar en profil, kan du också lägga till omfångstaggar och tillämpbarhetsregler i profilen.

**Omfångstaggar** är ett bra sätt för att tilldela och filtrera principer till specifika grupper, till exempel Personal eller Alla amerikanska NC-anställda. Mer information finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).

På Windows 10-enheter kan du lägga till **tillämpbarhetsregler** så att profilen endast gäller för en speciell OS-version eller en speciell Windows-version. [Tillämpbarhetsregler](device-profile-create.md#applicability-rules) innehåller mer information.

## <a name="exclude-groups-from-a-profile-assignment"></a>Exkludera grupper från en profiltilldelning

Med hjälp av Intunes profiler för enhetskonfiguration kan du exkludera grupper från principtilldelningen.

Intune tittar inte på användar-till-enhets grupprelationer. Om du väljer att inkludera användargrupper och samtidigt exkludera enhetsgrupper får du kanske inte önskat resultat. I användargrupp-till-användargrupp-scenarier och enhetsgrupp-till-enhetsgrupp-scenarier har undantag företräde framför inkludering.

Du kan t.ex. tilldela en enhetsprofil till användargruppen **Alla företagsanvändare** men välja att exkludera medlemmar i användargruppen **Ledningsgrupp**. Eftersom båda grupperna är användargrupper undantas alla medlemmar i **Ledningsgrupp** från principen, även om de är medlemmar i gruppen **Alla företagsanvändare**.

Inkludering har företräde framför undantag när blandade grupper används, t. ex. användargrupp-till-enhetsgrupp eller enhetsgrupp-till-användargrupp.

Säg att du t.ex. vill tilldela en profil till alla användare i din organisation, med undantag för allmänt tillgängliga informationsdatorer (kiosker). Du inkluderar gruppen **Alla användare**, men exkluderar gruppen **Alla enheter**. I detta fall får alla användare och deras enheter principen, även om användarens enhet finns i gruppen **Alla enheter**.

Undantag avser bara direkta medlemmar i gruppen. De omfattar inte enheter som är associerade med en användare. Principen tilldelas inte till enheter som inte har någon användare. Det beror på att dessa enheter utan användare inte har någon relation till gruppen **Alla användare**.

Om du inkluderar **Alla enheter** och exkluderar **Alla användare**, tilldelas principen till alla enheter. I det här scenariot är avsikten att exkludera de enheter som har en associerad användare från den här principen. Men detta exkluderar inte enheterna eftersom exkluderingsfunktionen endast jämför direkta medlemmar av gruppen.

## <a name="next-steps"></a>Nästa steg

Se avsnittet om att [övervaka enhetsprofiler](device-profile-monitor.md) för anvisningar om hur du övervakar dina profiler och de enheter som kör dina profiler.
