---
title: Filtrera principer med omfångstaggar i Microsoft Intune – Azure | Microsoft Docs
description: Använd omfångstaggar för att filtrera konfigurationsprofiler för specifika roller.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0da6861b6c49fc37691b8c6e464a506670643fa3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203339"
---
# <a name="use-scope-tags-to-filter-policies"></a>Använd omfångstaggar för att filtrera principer

Omfångstaggar gör det möjligt att filtrera principer med anpassade taggar som du skapar. Du kan använda omfångstaggar för roller och appar.

Du kan till exempel skapa en omfångstagg med namnet ”Teknikavdelning” och tilldela den till konfigurationsprinciper som är relaterade till teknikavdelningen. Tilldela samma tagg till rollen ”Teknikadministratörer”. De ser bara principer med taggen ”Teknikavdelning”.

## <a name="to-create-a-scope-tag"></a>Skapa en omfångstagg

Välj **Roller** > **Omfång (taggar)** > **Skapa**.

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Lägga till en omfångstagg i en konfigurationsprofil

Välj **Enhetskonfiguration** > **Profiler** > välj en profil > **Egenskaper** > **Omfång (taggar)**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Tilldela en omfångstagg till en roll

Välj **Roller** > **Alla roller** > **Princip- och profilhanterare** > **Tilldelningar** > **Omfång (taggar)**.

## <a name="to-assign-a-scope-tag-to-an-app"></a>Tilldela en omfångstagg till en app

Välj **Klientappar** > **Appar** > välj en app > **Egenskaper** > **Omfång (taggar)** > **Lägg till** > välj taggarna > **Välj** > **OK** > **Spara**.


## <a name="next-steps"></a>Nästa steg

Hantera dina [roller](role-based-access-control.md) och [profiler](device-profile-assign.md).

