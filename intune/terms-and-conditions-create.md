---
title: "Ange användarvillkor i Microsoft Intune"
titlesuffix: Azure portal
description: "Ange allmänna villkor som användarna ser i företagsportalen för Intune. "
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fa35cb7b08f0bbf677dd7d8b5122b8b286c49b72
ms.sourcegitcommit: 5004b9564915712b41860df20324f39fac3dc27d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/03/2018
---
# <a name="ensure-users-accept-company-terms-for-access"></a>Se till att användarna godkänner företagets åtkomstvillkor

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du kräva att användarna måste godkänna företagets allmänna villkor innan de kan använda företagsportalen för att registrera sina enheter och få åtkomst till företagsresurser som appar och e-post. Konfigurationen av de allmänna villkoren är valfri.

Du kan skapa flera uppsättningar med villkor och tilldela dem till olika användargrupper, t.ex. med stöd för olika språk.

## <a name="create-terms-and-conditions"></a>Skapa allmänna villkor
Slutför stegen nedan för att skapa allmänna villkor. Namn och beskrivning som visas är för administrativa syften, medan villkorsegenskaperna visas för användarna i företagsportalen.

1. I Azure-portalen väljer du **Enhetsregistrering** och sedan **Villkor**.
2. Välj **Skapa**.
![Skärmbild av Azure-portalen med knappen Skapa för villkor](media/terms-create-terms.png)
3. På det expanderade bladet anger du följande information:

   - **Visningsnamn**: Namnet på villkoren i Azure-portalen. Användarna ser inte det här namnet.

   - **Beskrivning**: Valfri information som hjälper dig att identifiera den här uppsättningen med villkor i Azure-portalen.

4. Välj pilen bredvid Definiera villkor för användning för att öppna bladet Villkor och ange därefter följande information:

   ![Skärmbild för att godkänna slutanvändarvillkor med en sammanfattning av villkoren](./media/terms-summary-create.png)

   - **Rubrik**: namnet på dina villkor som användarna ser i företagsportalen ovanför **sammanfattningen**.
   - **Sammanfattning av villkoren**: Text som förklarar vad det innebär om användarna accepterar villkoren. Till exempel, ”Genom att registrera din enhet accepterar du användningsvillkoren som anges av Contoso. Läs villkoren noggrant innan du fortsätter.”
   - **Allmänna villkor**: De villkor som användarna ser och antingen måste godkänna eller avvisa.

5. Välj **OK** och välj sedan **Skapa**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Se hur villkoren visas för användarna
I följande exempel visas **Rubrik** och **Sammanfattning av villkoren** i administratörskonsolen och företagsportalen.

![Skärmbild på Rubrik och Sammanfattning av villkoren i administratörskonsolen och företagsportalen.](./media/terms-summary-terms.png)

I följande exempel visas användarvillkoren i administratörskonsolen och företagsportalen.

![Skärmbild på användarvillkoren i administratörskonsolen och företagsportalen.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Tilldela allmänna villkor

Du kan tilldela villkor till grupper av användare som måste godkänna dem innan de kan använda företagsportalen.

1. I Azure-portalen väljer du **Enhetsregistrering** och sedan **Villkor**.
2. Välj de allmänna villkor som du vill tilldela i listan med villkor. Välj sedan **Tilldelade grupper**.
![Skärmbild av Azure-portalens blad Tilldela grupp, som visar knappen Välj grupp och knappen Välj för tilldelning av villkoren](media/terms-assign-groups.png)
3. Klicka på knappen **Välj grupp**. På bladet **Välj grupper** väljer du de grupper som du vill tilldela villkoren till. Klicka sedan på **Välj**. Dynamiska grupper kan inte tilldelas användarvillkor.
4. På bladet **Tilldelade grupper** klickar du på **Spara**.  Villkoren har nu tilldelats till användarna i de valda grupperna. Användarna kommer att uppmanas att godkänna villkoren nästa gång de öppnar företagsportalen. De användarvillkoren behöver bara godkännas en gång. Användare med flera enheter behöver inte godkänna på varje enhet.


## <a name="monitor-terms-and-conditions"></a>Övervaka användarvillkor

1. På Azure-portalen väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. På Intune-bladet väljer du **Enhetsregistrering** och sedan **Allmänna villkor**.
2. I listan med allmänna villkor väljer du de villkor som du vill se godkännanden för. Välj sedan **Godkännandestatus**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Arbeta med flera versioner av användarvillkor
Du kan redigera dina villkor och hantera deras versioner. Vi rekommenderar att du ökar versionsnumret och kräver godkännande varje gång du gör större ändringar i dina allmänna villkor. Behåll det nuvarande versionsnumret om du exempelvis bara korrigerar stavfel eller ändrar formateringen.

1. På Azure-portalen väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. På Intune-bladet väljer du **Enhetsregistrering**, **Allmänna villkor**, de villkor som du vill ändra och sedan **Egenskaper**.

4. På bladet **Egenskaper** väljer du **Allmänna villkor**. Ändra sedan **Rubrik**, **Sammanfattning av villkoren** och **Allmänna villkor** efter behov. Om ändringarna gör det nödvändigt att användarna måste godkänna de nya villkoren igen, klickar du på **Kräv att användarna godkänner på nytt och öka versionsnumret till**

4.  Välj **OK** och välj sedan **Spara**.

Användarna behöver bara godkänna uppdaterade villkor en gång. Användare med flera enheter behöver inte godkänna användarvillkoren på varje enhet.
