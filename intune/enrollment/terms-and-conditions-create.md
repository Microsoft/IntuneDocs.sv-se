---
title: Ange användarvillkor i Microsoft Intune
titleSuffix: ''
description: Ange allmänna villkor som användarna ser i företagsportalen för Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fb5818609763753878fec7a84fd8c19eb154f88
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955447"
---
# <a name="terms-and-conditions-for-user-access"></a>Allmänna villkor för användaråtkomst

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Som Intune-administratör kan du kräva att användarna godkänner företagets allmänna villkor innan de använder företagsportalen för att:
- registrera enheter
- komma åt resurser som appar och e-post.

Konfigurationen av de allmänna villkoren är valfri.

Du kan skapa flera uppsättningar med villkor och tilldela dem till olika användargrupper, t.ex. med stöd för olika språk.

Du kan skapa företagets allmänna villkor på två sätt:
- med hjälp av Intune, genom att följa anvisningarna i den här artikeln.
- med hjälp av [funktionen Azure Active Directory-användningsvillkor](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou)

Om du inte vet vilken metod som passar bäst för dig rekommenderar vi att du läser blogginlägget [Choosing the right Terms solution for your organization](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409) (Välja rätt lösning för användningsvillkor för din organisation). 

## <a name="create-terms-and-conditions"></a>Skapa allmänna villkor
Slutför stegen nedan för att skapa allmänna villkor. Namn och beskrivning som visas är för administrativa syften, medan villkorsegenskaperna visas för användarna i företagsportalen.

1. Logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Administration av klientorganisation** > **Allmänna villkor**.
2. Välj **Skapa**.
3. På sidan **Grundläggande** anger du följande information:

   - **Namn**: Namnet på villkoren i Azure-portalen. Användarna ser inte det här namnet.
   - **Beskrivning**: Valfri information som hjälper dig att identifiera den här uppsättningen med villkor i Azure-portalen.

    ![Skärmbild av Azure-portalen som visar den grundläggande sidan för villkor](./media/terms-and-conditions-create/terms-basics-page.png)

4. Välj **Nästa** för att gå till sidan **Villkor** och ange följande information:

   - **Rubrik**: Namnet på dina villkor som användarna ser i företagsportalen ovanför **Sammanfattning**.
   - **Allmänna villkor**: De villkor som användarna ser och antingen måste godkänna eller avvisa.
   - **Sammanfattning av villkoren**: Text som förklarar vad det innebär när användarna accepterar villkoren. Till exempel, ”Genom att registrera din enhet accepterar du användningsvillkoren som anges av Contoso. Läs villkoren noggrant innan du fortsätter.”

5. Välj **Nästa** för att gå till sidan **Omfångskoder**.

6. Markera **Välj omfångskoder**, välj de omfångskoder som du vill tilldela till dessa avtalsvillkor och välj sedan **Välj**. 

7. Välj **Nästa** för att gå till sidan **Tilldelningar** och välj ett av följande alternativ för **Tilldela till**:
    - **Alla användare**: Välj det här alternativet om du vill tilldela de här villkoren till alla användare.
    - **Välj grupper**: Välj det här alternativet om du vill tilldela de här villkoren till alla i de grupper som du identifierar genom att välja **Välj grupper som ska inkluderas**.

8. Välj **Nästa** > **Skapa**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Se hur villkoren visas för användarna
I följande exempel visas **Rubrik** och **Sammanfattning av villkoren** i administratörskonsolen och företagsportalen.

![Skärmbild på Rubrik och Sammanfattning av villkoren i administratörskonsolen och företagsportalen.](./media/terms-and-conditions-create/terms-summary-terms.png)

I följande exempel visas användarvillkoren i administratörskonsolen och företagsportalen.

![Skärmbild på användarvillkoren i administratörskonsolen och företagsportalen.](./media/terms-and-conditions-create/terms-properties-terms.png)


## <a name="monitor-terms-and-conditions"></a>Övervaka användarvillkor

1. Logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Administration av klientorganisation** > **Allmänna villkor**.
2. I listan med allmänna villkor väljer du de villkor som du vill visa godkännande för > **Rapportering av godkännande**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Arbeta med flera versioner av användarvillkor
Du kan redigera dina villkor och hantera deras versioner. Varje gång du gör en betydande ändring i dina allmänna villkor bör du:
- öka versionsnumret
- Kräv att användarna godkänner de nya allmänna villkoren

Behåll det nuvarande versionsnumret om du exempelvis korrigerar stavfel eller ändrar formateringen.

1. Logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Administration av klientorganisation** > **Allmänna villkor** > välj de villkor som du vill ändra > **Egenskaper**.

2. I fönstret **Egenskaper** väljer du **Allmänna villkor**. Ändra sedan **Rubrik**, **Sammanfattning av villkoren** och **Allmänna villkor** efter behov. Om ändringarna gör det nödvändigt att användarna måste godkänna de nya villkoren igen, klickar du på **Kräv att användarna godkänner på nytt och öka versionsnumret till**

3. Välj **OK** > **Spara**.

Användarna behöver bara godkänna uppdaterade villkor en gång. Användare med flera enheter behöver inte godkänna användarvillkoren på varje enhet.
