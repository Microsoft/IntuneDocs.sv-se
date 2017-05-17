---
title: "Ange användarvillkor i Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Ange allmänna villkor som användarna ser i företagsportalen för Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 2b064d14e8a46c19c0eafc3276b470dead114438
ms.openlocfilehash: 528aa8cb863b3168274298de7270cafff2502e61
ms.contentlocale: sv-se
ms.lasthandoff: 05/06/2017

---

# <a name="ensure-users-accept-company-terms-for-access"></a>Se till att användarna godkänner företagets åtkomstvillkor

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Som Intune-administratör kan du välja att kräva att användarna måste godkänna företagets allmänna villkor innan de kan använda företagsportalen för att registrera sina enheter och få åtkomst till företagsresurser som appar och e-post. Konfigurationen av de allmänna villkoren är valfri.

Du kan skapa flera uppsättningar med villkor och tilldela dem till olika användargrupper, t.ex. med stöd för olika språk.

## <a name="create-terms-and-conditions"></a>Skapa allmänna villkor
Slutför stegen nedan för att skapa allmänna villkor. Namn och beskrivning som visas är för administrativa syften, medan villkorsegenskaperna visas för användarna i företagsportalen.

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. På Intune-bladet väljer du **Enhetsregistrering** och sedan **Allmänna villkor**.

3. Välj **Skapa**.
![Skärmbild av Intune-portalen med knappen Skapa för allmänna villkor](media/terms-create-terms.png)

4. På det expanderade bladet anger du följande information:

   - **Visningsnamn**: Namnet på villkoren i Intune-portalen. Användarna ser inte det här namnet.

   - **Beskrivning**: Valfri information som hjälper dig att identifiera den här uppsättningen med villkor i Intune-portalen.

5. Välj pilen bredvid Definiera villkor för användning för att öppna bladet Villkor och ange därefter följande information:

   - **Rubrik**: Den rubrik som användarna ser i företagsportalen.

   - **Sammanfattning av villkoren**: Text som förklarar vad det innebär om användarna accepterar villkoren. T.ex. ”Genom att registrera din enhet accepterar du användningsvillkoren som anges av Contoso. Läs villkoren noggrant innan du fortsätter.”

   - **Allmänna villkor**: De villkor som användarna ser och antingen måste godkänna eller avvisa.

6. Välj **OK** och välj sedan **Skapa**.


## <a name="assign-terms-and-conditions"></a>Tilldela allmänna villkor

Du kan tilldela villkor till grupper av användare som måste godkänna dem innan de kan använda företagsportalen.

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. På Intune-bladet väljer du **Enhetsregistrering** och sedan **Allmänna villkor**.

3. Välj de allmänna villkor som du vill tilldela i listan med villkor. Välj sedan **Tilldelade grupper**.
![Skärmbild av Intune-portalens blad Tilldela grupp, som visar knappen Välj grupp och knappen Välj för tilldelning av allmänna villkor](media/terms-assign-groups.png)

4. Klicka på knappen **Välj grupp**. På bladet **Välj grupper** väljer du de grupper som du vill tilldela villkoren till. Klicka sedan på **Välj**.

5. På bladet **Tilldelade grupper** klickar du på **Spara**.  Villkoren har nu tilldelats till användarna i de valda grupperna. Användarna kommer att uppmanas att godkänna villkoren nästa gång de öppnar företagsportalen.

## <a name="monitor-a-terms-and-conditions"></a>Övervaka ett allmänt villkor

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. På Intune-bladet väljer du **Enhetsregistrering** och sedan **Allmänna villkor**.
2. I listan med allmänna villkor väljer du de villkor som du vill se godkännanden för. Välj sedan **Godkännandestatus**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Arbeta med flera versioner av användarvillkor
Du kan redigera dina villkor och hantera deras versioner. Vi rekommenderar att du ökar versionsnumret och kräver godkännande varje gång du gör större ändringar i dina allmänna villkor. Behåll det nuvarande versionsnumret om du exempelvis bara korrigerar stavfel eller ändrar formateringen.

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. På Intune-bladet väljer du **Enhetsregistrering**, **Allmänna villkor**, de villkor som du vill ändra och sedan **Egenskaper**.

4. På bladet **Egenskaper** väljer du **Allmänna villkor**. Ändra sedan **Rubrik**, **Sammanfattning av villkoren** och **Allmänna villkor** efter behov. Om ändringarna gör det nödvändigt att användarna måste godkänna de nya villkoren igen, klickar du på **Kräv att användarna godkänner på nytt och öka versionsnumret till**

4.  Välj **OK** och välj sedan **Spara**.

