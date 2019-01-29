---
title: Ange användarvillkor i Microsoft Intune
titlesuffix: ''
description: Ange allmänna villkor som användarna ser i företagsportalen för Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 7283b728e519eb2ca5a9a0b7516774c8cfc26f9b
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831521"
---
# <a name="terms-and-conditions-for-user-access"></a>Allmänna villkor för användaråtkomst

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du kräva att användarna godkänner företagets allmänna villkor innan de använder företagsportalen för att:
- registrera enheter
- komma åt resurser som appar och e-post.    
Konfigurationen av de allmänna villkoren är valfri.

Du kan skapa flera uppsättningar med villkor och tilldela dem till olika användargrupper, t.ex. med stöd för olika språk.

Du kan skapa företagets allmänna villkor på två sätt:
- med hjälp av Intune, genom att följa anvisningarna i den här artikeln.
- med hjälp av [Azure Active Directory-funktionen för användningsvillkor](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou). Om du inte vet vilken metod som passar bäst för dig rekommenderar vi att du läser blogginlägget [Choosing the right Terms solution for your organization](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409) (Välja rätt lösning för användningsvillkor för din organisation). 

## <a name="create-terms-and-conditions"></a>Skapa allmänna villkor
Slutför stegen nedan för att skapa allmänna villkor. Namn och beskrivning som visas är för administrativa syften, medan villkorsegenskaperna visas för användarna i företagsportalen.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetsregistrering** > **Allmänna villkor**.
2. Välj **Skapa**.
![Skärmbild av Azure-portalen med knappen Skapa för villkor](media/terms-create-terms.png)
3. I det expanderade fönstret anger du följande information:

   - **Visningsnamn**: Namnet på villkoren i Azure-portalen. Användarna ser inte det här namnet.

   - **Beskrivning**: Valfri information som hjälper dig att identifiera den här uppsättningen med villkor i Azure-portalen.

4. Välj pilen bredvid **Definiera villkor för användning** för att öppna fönstret Allmänna villkor och ange därefter följande information:

   ![Skärmbild för att godkänna slutanvändarvillkor med en sammanfattning av villkoren](./media/terms-summary-create.png)

   - **Rubrik**: Namnet på dina villkor som användarna ser i företagsportalen ovanför **Sammanfattning**.
   - **Sammanfattning av villkoren**: Text som förklarar vad det innebär när användarna accepterar villkoren. Till exempel, ”Genom att registrera din enhet accepterar du användningsvillkoren som anges av Contoso. Läs villkoren noggrant innan du fortsätter.”
   - **Allmänna villkor**: De villkor som användarna ser och antingen måste godkänna eller avvisa.

5. Välj **OK** > **Skapa**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Se hur villkoren visas för användarna
I följande exempel visas **Rubrik** och **Sammanfattning av villkoren** i administratörskonsolen och företagsportalen.

![Skärmbild på Rubrik och Sammanfattning av villkoren i administratörskonsolen och företagsportalen.](./media/terms-summary-terms.png)

I följande exempel visas användarvillkoren i administratörskonsolen och företagsportalen.

![Skärmbild på användarvillkoren i administratörskonsolen och företagsportalen.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Tilldela allmänna villkor

Du kan tilldela villkor till grupper av användare som måste godkänna dem innan de kan använda företagsportalen.

1. I Azure-portalen väljer du **Enhetsregistrering** och sedan **Villkor**.
2. I listan med allmänna villkor väljer du de villkor du vill tilldela > **Hantera** > **Tilldelningar**.
![Skärmbild av Azure-portalens fönster Tilldela grupp, som visar knappen Välj grupp och knappen Välj för tilldelning av villkoren](media/terms-assign-groups.png)
3. Välj **Välj grupper att ta med** > välj de grupper som du vill tilldela villkoren > **Välj**. Dynamiska grupper kan inte tilldelas användarvillkor.
4. I fönstret **Tilldelade grupper** väljer du **Spara**.  Villkoren har nu tilldelats till användarna i de valda grupperna. Användarna kommer att uppmanas att godkänna villkoren nästa gång de öppnar företagsportalen. Användningsvillkoren behöver bara godkännas en gång. Användare med flera enheter behöver inte godkänna på varje enhet.


## <a name="monitor-terms-and-conditions"></a>Övervaka användarvillkor

1. På Azure-portalen väljer du **Alla tjänster** > **Övervakning + hantering** > **Intune**. 
1. I fönstret Intune väljer du **Enhetsregistrering** > **Allmänna villkor**.
2. I listan med allmänna villkor väljer du de villkor som du vill visa godkännande för > **Rapportering av godkännande**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Arbeta med flera versioner av användarvillkor
Du kan redigera dina villkor och hantera deras versioner. Varje gång du gör en betydande ändring i dina allmänna villkor bör du:
- öka versionsnumret
- kräva att användarna godkänner de nya allmänna villkoren. Behåll det nuvarande versionsnumret om du exempelvis bara korrigerar stavfel eller ändrar formateringen.

1. På Azure-portalen väljer du **Alla tjänster** > **Övervakning + hantering** > **Intune**.

2. I Intune-fönstret väljer du **Enhetsregistrering** > **Allmänna villkor** > välj de villkor som du vill ändra > **Egenskaper**.

4. I fönstret **Egenskaper** väljer du **Allmänna villkor**. Ändra sedan **Rubrik**, **Sammanfattning av villkoren** och **Allmänna villkor** efter behov. Om ändringarna gör det nödvändigt att användarna måste godkänna de nya villkoren igen, klickar du på **Kräv att användarna godkänner på nytt och öka versionsnumret till**

4.  Välj **OK** > **Spara**.

Användarna behöver bara godkänna uppdaterade villkor en gång. Användare med flera enheter behöver inte godkänna användarvillkoren på varje enhet.
