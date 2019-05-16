---
title: Tilldela enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Använd Azure-portalen för att tilldela enhetsprofiler och principer till användare och enheter. Lär dig att undanta grupper från en profiltilldelning i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c950efdd95fd8d856ec677385712a022dead870
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570513"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Tilldela användar- och enhetsprofiler i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du skapar en profil som innehåller alla inställningar som du har angett. Nästa steg är att distribuera eller ”tilldela” profilen till din användare eller dina enhetsgrupper i Azure Active Directory (Azure AD). När den är tilldelad får användarna och enheterna din profil och de inställningar som du har angett tillämpas.

Den här artikeln visar hur du tilldelar en profil, samt innehåller information om hur du använder omfångstaggar på dina profiler.

## <a name="assign-a-device-profile"></a>Tilldela en enhetsprofil

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Profiler**. Alla profilerna visas i listan.
3. Välj den profil som du vill tilldela > **Tilldelningar**.
4. Välj om du vill **inkludera** eller **exkludera** grupper och välj sedan grupperna. När du väljer dina grupper väljer du en Azure AD-grupp. Håll ned **Ctrl**-tangenten om du vill markera flera grupper.

    ![Skärmbild med alternativ för att inkludera eller exkludera grupper från en profiltilldelning](./media/group-include-exclude.png)

5. **Spara** ändringarna.

### <a name="evaluate-how-many-users-are-targeted"></a>Utvärdera hur många användare som omfattas

När du tilldelar profilen kan du också **utvärdera** hur många användare som påverkas. Den här funktionen beräknar användare, den beräknar inte enheter.

1. Välj **Enhetskonfiguration** > **Profiler** i Intune.
2. Välj en profil > **Tilldelningar** > **Utvärdera**. Ett meddelande visas med hur många användare som omfattas av profilen.

Om knappen **Utvärdera** är nedtonad, kontrollerar du att profilen har tilldelats till en eller flera grupper.


## <a name="use-scope-tags"></a>Använda omfångstaggar

När du skapar eller uppdaterar en profil, kan du också lägga till omfångstaggar i profilen.

**Omfångstaggar** är ett bra sätt för att tilldela och filtrera principer till specifika grupper, till exempel Personal eller Alla amerikanska NC-anställda. Mer information finns i [Använda RBAC och omfångstaggar för distribuerad IT](scope-tags.md).

## <a name="exclude-groups-from-a-profile-assignment"></a>Exkludera grupper från en profiltilldelning

Med hjälp av Intunes profiler för enhetskonfiguration kan du exkludera grupper från principtilldelningen. Du kan t.ex. tilldela en enhetsprofil till gruppen **Alla företagsanvändare**, men välja att exkludera medlemmar i gruppen **Ledningsgrupp**.

När du exkluderar grupper, enbart användare eller enbart enhetsgrupper (inte en blandning av grupper) från en tilldelning, tar Intune inte hänsyn till relationer mellan användare och enheter. Om du väljer att inkludera användargrupper och samtidigt exkludera enhetsgrupper får du kanske inte önskat resultat. Om du blandar grupper, eller om någon annan konflikt skulle uppstå, äger inkludering företräde över exkludering.

Säg att du t.ex. vill tilldela en profil till alla enheter i din organisation, med undantag för allmänt tillgängliga informationsdatorer (kiosker). Du inkluderar gruppen **Alla användare**, men exkluderar gruppen **Alla enheter**. I detta fall får alla användare och deras enheter principen, även om användarens enhet finns i gruppen **Alla enheter**.

Undantag avser bara direkta medlemmar i gruppen. De omfattar inte enheter som är associerade med en användare. Principen tilldelas inte till enheter som inte har någon användare. Det beror på att dessa enheter inte har någon relation till gruppen **Alla användare**.

Om du inkluderar **Alla enheter** och exkluderar **Alla användare**, tilldelas principen till alla enheter. I det här scenariot är avsikten att exkludera de enheter som har en associerad användare från den här principen. Men detta exkluderar inte enheterna eftersom exkluderingsfunktionen endast jämför direkta medlemmar av gruppen.

## <a name="next-steps"></a>Nästa steg

Se avsnittet om att [övervaka enhetsprofiler](device-profile-monitor.md) för anvisningar om hur du övervakar dina profiler och de enheter som kör dina profiler.