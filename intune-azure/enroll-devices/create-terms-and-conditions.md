---
title: "Ställa in villkor i Microsoft Intune |Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Ställa in villkor som användarna ser i företagsportalen för Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: f7d6ebc9d71a077492ab615a3bc5397e092b1deb
ms.lasthandoff: 02/15/2017

---

# <a name="set-terms-and-conditions"></a>Ställa in villkor 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Du kan distribuera de allmänna villkoren för Intune till användargrupper och förklara hur registrering, åtkomst till arbetsresurser och företagsportalappen påverkar enheter och användare. Användare måste godkänna de allmänna villkoren innan de kan använda företagsportalen för att registrera sig och komma åt sina arbeten.

Du kan skapa och distribuera flera policys med olika användarvillkor. Du kan också skapa versioner av samma användarvillkor på olika språk och sen distribuera dessa till relevanta grupper.

**Skapa villkor**:

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Villkor**.

3. Välj **Skapa**.

4. På bladet **Skapa allmänna villkor** anger du följande information:

   - **Visningsnamn**: Namn att använda för villkoren. Användarna ser det här namnet i företagsportalen.

   - **Beskrivning**: Valfria detaljer som hjälper dig att identifiera principen i Azure-portalen.

5. Välj pilen bredvid Definiera villkor för användning för att öppna bladet Villkor och ange därefter följande information:

   - **Rubrik**: Rubriken som användarna ser på företagsportalen.

   - **Sammanfattning av villkoren**: Text som förklarar vad det innebär om användarna accepterar villkoren.

   - **Villkor**: Den juridiska text som användarna ser och måste godkänna eller avvisa med till exempel: ”Jag godkänner villkoren”.

6. Välj **OK**.

