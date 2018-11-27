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
ms.openlocfilehash: 080205e601b857d4765eb6b97eeeeeb8f4e6fc1b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187165"
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

