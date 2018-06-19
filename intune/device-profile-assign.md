---
title: Tilldela enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Använd Azure-portalen för att tilldela enhetsprofiler och principer till användare och enheter. Lär dig hur du undantar grupper från en profiltilldelning i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fa1a1b1085d196411a03a6228eefa808399397ea
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024812"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Tilldela användar- och enhetsprofiler i Microsoft Intune

När du har skapat en profil kan du tilldela profilen till Azure Active Directory-grupper (Azure AD).

## <a name="assign-a-device-profile"></a>Tilldela en enhetsprofil

1. I [Azure Portal](https://portal.azure.com) väljer du **Alla tjänster** och söker efter **Microsoft Intune**.
2. I **Microsoft Intune** väljer du **Enhetskonfiguration** och sedan **Profiler**.
3. Välj den profil som du vill tilldela i listan med profiler och välj sedan **Tilldelningar**.
4. Välj om du vill **inkludera** eller **exkludera** grupper och välj sedan grupper.  

    ![Skärmbild med alternativ för att inkludera eller exkludera grupper från en profiltilldelning](./media/group-include-exclude.png)

5. När du väljer dina grupper väljer du en Azure AD-grupp. Håll ned **Ctrl**-tangenten om du vill markera flera grupper.
6. När du är klar väljer du **Spara**.

## <a name="exclude-groups-from-a-profile-assignment"></a>Exkludera grupper från en profiltilldelning

Med hjälp av Intunes profiler för enhetskonfiguration kan du exkludera grupper från principtilldelningen. Du kan t.ex. tilldela en enhetsprofil till gruppen **Alla företagsanvändare**, men välja att exkludera alla användare som även är medlemmar i gruppen **Ledningsgrupp**.

När du exkluderar grupper från en tilldelning exkluderar du endast användare eller endast enhetsgrupper (inte en blandning av grupper). Intune tar inte hänsyn till relationer mellan användare och enheter. Om du väljer att inkludera användargrupper och samtidigt exkludera enhetsgrupper får du kanske inte önskat resultat. Om du blandar grupper, eller om någon annan konflikt skulle uppstå, äger inkludering företräde.

Säg att du t.ex. vill tilldela en profil till alla enheter i din organisation, med undantag för allmänt tillgängliga informationsdatorer (kiosker). Du inkluderar gruppen **Alla användare**, men exkluderar gruppen **Alla enheter**. Då tilldelas alla användare och deras enheter samma princip, även om användarens enhet ingår i gruppen **Alla enheter**.

Exkluderingsfunktionen tittar bara på direkta medlemmar av gruppen, ingen hänsyn tas till de enheter som eventuellt finns kopplade till användaren. Principen tilldelas inte till enheter som inte har någon användare. Det beror på att dessa enheter inte har någon relation till gruppen **Alla användare**.

Om du inkluderar **Alla enheter** och exkluderar **Alla användare**, tilldelas principen till alla enheter. I det här scenariot är avsikten att exkludera de enheter som har en associerad användare från den här principen. Men detta exkluderar inte enheterna eftersom exkluderingsfunktionen endast jämför direkta medlemmar av gruppen.

>[!TIP]
>Exkluderingsfunktionen kan för närvarande inte användas tillsammans med kompatibilitetsprinciper eller apptilldelningar. Om du vill exkludera medlemmar från en tilldelning kan du använda värdet **Tillgängligt** respektive **Inte tillämpligt**. Du kan t.ex. tilldela en app till **Alla företagsanvändare** genom att välja värdet **Tillgängligt** och därefter välja värdet **Ej tillämpligt** för **Ledningsgrupp**. Appen tilldelas till alla användare *utom* användarna i gruppen **Ledningsgrupp**. Om du tilldelar appen till **Alla företagsanvändare** med värdet **Obligatoriskt** inkluderas även gruppen **Ledningsgrupp**.

## <a name="next-steps"></a>Nästa steg
Se [Övervaka enhetsprofiler](device-profile-monitor.md) för vägledning i hur du övervakar tilldelningar av enhetsprofiler.
