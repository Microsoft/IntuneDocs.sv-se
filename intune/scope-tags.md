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
ms.custom: intune-azure
ms.openlocfilehash: 000505df3c0898ed0939244dfe1b075c64097611
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329435"
---
# <a name="use-scope-tags-to-filter-policies"></a>Använd omfångstaggar för att filtrera principer

Omfångstaggar gör det möjligt att filtrera principer med anpassade taggar som du skapar.

Du kan till exempel skapa en omfångstagg med namnet ”Teknikavdelning” och tilldela den till konfigurationsprinciper som är relaterade till teknikavdelningen. Tilldela samma tagg till rollen ”Teknikadministratörer”. De ser bara principer med taggen ”Teknikavdelning”.

## <a name="to-create-a-scope-tag"></a>Skapa en omfångstagg

Välj **Roller** > **Omfång (taggar)** > **Skapa**.

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Lägga till en omfångstagg i en konfigurationsprofil

Välj **Enhetskonfiguration** > **Profiler** > välj en profil > **Egenskaper** > **Omfång (taggar)**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Tilldela en omfångstagg till en roll

Välj **Roller** > **Alla roller** > **Princip- och profilhanterare** > **Tilldelningar** > **Omfång (taggar)**.

## <a name="next-steps"></a>Nästa steg

Hantera dina [roller](role-based-access-control.md) och [profiler](device-profile-assign.md).

