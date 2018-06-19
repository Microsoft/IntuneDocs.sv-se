---
title: Ange användarvillkor i Microsoft Intune
titlesuffix: ''
description: Ange allmänna villkor som användarna ser i företagsportalen för Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 550d9c457335f212f0b60c16249e45f22f5baaf5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31033308"
---
# <a name="manage-your-companys-terms-and-conditions-for-user-access"></a>Hantera företagets villkor för användaråtkomst

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du kräva att användarna måste godkänna företagets allmänna villkor innan de kan använda företagsportalen för att registrera sina enheter och få åtkomst till företagsresurser som appar och e-post. Konfigurationen av de allmänna villkoren är valfri.

Du kan skapa flera uppsättningar med villkor och tilldela dem till olika användargrupper, t.ex. med stöd för olika språk.

## <a name="create-terms-and-conditions"></a>Skapa allmänna villkor
Slutför stegen nedan för att skapa allmänna villkor. Namn och beskrivning som visas är för administrativa syften, medan villkorsegenskaperna visas för användarna i företagsportalen.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I **Intune-fönstret** väljer du **Enhetsregistrering** och sedan **Allmänna villkor**.
2. Välj **Skapa**.
![Skärmbild av Azure-portalen med knappen Skapa för villkor](media/terms-create-terms.png)
3. I det expanderade fönstret anger du följande information:

   - **Visningsnamn**: Namnet på villkoren i Azure-portalen. Användarna ser inte det här namnet.

   - **Beskrivning**: Valfri information som hjälper dig att identifiera den här uppsättningen med villkor i Azure-portalen.

4. Välj pilen bredvid **Definiera villkor för användning** för att öppna fönstret Villkor och ange därefter följande information:

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
2. Välj de allmänna villkor som du vill tilldela i listan med villkor. Välj sedan **Hantera** > **Tilldelningar**.
![Skärmbild av Azure-portalens fönster Tilldela grupp, som visar knappen Välj grupp och knappen Välj för tilldelning av villkoren](media/terms-assign-groups.png)
3. Klicka på **Välj grupper att ta med** och välj de grupper du vill tilldela villkoren till och klicka på **Välj**. Dynamiska grupper kan inte tilldelas användarvillkor.
4. I fönstret **Tilldelade grupper** klickar du på **Spara**.  Villkoren har nu tilldelats till användarna i de valda grupperna. Användarna kommer att uppmanas att godkänna villkoren nästa gång de öppnar företagsportalen. De användarvillkoren behöver bara godkännas en gång. Användare med flera enheter behöver inte godkänna på varje enhet.


## <a name="monitor-terms-and-conditions"></a>Övervaka användarvillkor

1. På Azure-portalen väljer du **Alla tjänster** > **Övervakning + hantering** > **Intune**. 
1. I Intune-fönstret väljer du **Enhetsregistrering** och sedan **Allmänna villkor**.
2. I listan med allmänna villkor väljer du de villkor som du vill se godkännanden för. Välj sedan **Rapportering av godkännande**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Arbeta med flera versioner av användarvillkor
Du kan redigera dina villkor och hantera deras versioner. Vi rekommenderar att du ökar versionsnumret och kräver godkännande varje gång du gör större ändringar i dina allmänna villkor. Behåll det nuvarande versionsnumret om du exempelvis bara korrigerar stavfel eller ändrar formateringen.

1. På Azure-portalen väljer du **Alla tjänster** > **Övervakning + hantering** > **Intune**.

2. I Intune-fönstret väljer du **Enhetsregistrering**, **Allmänna villkor**, de villkor som du vill ändra och sedan **Egenskaper**.

4. I fönstret **Egenskaper** väljer du **Allmänna villkor**. Ändra sedan **Rubrik**, **Sammanfattning av villkoren** och **Allmänna villkor** efter behov. Om ändringarna gör det nödvändigt att användarna måste godkänna de nya villkoren igen, klickar du på **Kräv att användarna godkänner på nytt och öka versionsnumret till**

4.  Välj **OK** och välj sedan **Spara**.

Användarna behöver bara godkänna uppdaterade villkor en gång. Användare med flera enheter behöver inte godkänna användarvillkoren på varje enhet.
