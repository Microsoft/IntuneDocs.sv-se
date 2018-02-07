---
title: Skapa och distribuera en WIP-appskyddsprincip med Intune
titlesuffix: Azure portal
description: Skapa och distribuera WIP-appskyddsprinciper med Intune
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 97f9407c8ba93307059e44c8becf4f7a36c6861a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Skapa och distribuera en WIP-appskyddsprincip med Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Från och med version 1704 av Intune kan du använda appskyddsprinciper med Windows 10 för att skydda appar utan enhetsregistrering.

## <a name="before-you-begin"></a>Innan du börjar

Låt oss ta upp några grundläggande begrepp när du lägger till en WIP-princip.

### <a name="list-of-allowed-and-exempt-apps"></a>Lista över tillåtna och undantagna appar

-   **Tillåtna appar**: Dessa appar är de som måste följa den här principen.

-   **Undantagna appar**: De här apparna har undantagits från den här principen och har åtkomst till företagets data utan begränsningar.

### <a name="types-of-apps"></a>Apptyper

-   **Rekommenderade appar:** En i förväg ifylld lista med appar (huvudsakligen för Microsoft Office) som du enkelt kan importera till principen. <!---I really don't know what you mean by "easily import into policy"--->

-   **Store-appar:** Du kan lägga till valfri app från Windows Store i principen.

-   **Windows-skrivbordsappar:** Du kan lägga till valfria traditionella Windows-skrivbordsappar i principen (t.ex. exe, dll osv.)

## <a name="pre-requisites"></a>Förutsättningar

Du måste konfigurera MAM-providern innan du kan skapa en WIP-appskyddsprincip. Läs mer i [Konfigurera din MAM-provider med Intune](https://docs.microsoft.com/app-protection-policies-configure-windows-10.md).

Du måste dessutom ha följande:

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)-licens.
-   [Windows Creators-uppdatering](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> RIA stöder inte multi-identitet. Det kan bara finnas en hanterad identitet åt gången.
<!---Should you be linking to a topic that explains what multi-identity is?--->

## <a name="to-add-a-wip-policy"></a>Lägga till en RIA-princip

När du konfigurerar Intune i din organisation kan du skapa en RIA-specifik princip via [Azure Portal](https://docs.microsoft.com/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies). <!---Is there an azure topic you can use instead of a classic? if not, should this topic be moved into the azure docset?--->

1.  Gå till **Intune-instrumentpanelen för hantering av mobila program**, välj **Alla inställningar** > **App-princip**.

2.  Välj **Lägg till en princip** på bladet **App-princip**, och ange sedan följande värden:

    a.  **Namn:** Skriv ett namn (obligatoriskt) för den nya principen.

    b.  **Beskrivning:** Ge en valfri beskrivning.

    c.  **Plattform:** Välj **Windows 10** som den plattform som stöds för din appskyddsprincip.

    d.  **Registreringstillstånd:** Välj **Utan registrering** som din princips registreringstillstånd.

3.  Välj **Skapa**. Principen skapas och visas i tabellen på bladet **App-princip**.

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>Lägga till rekommenderade appar i listan över tillåtna appar

1.  Välj din princips namn på bladet **App-princip**, och välj sedan **Tillåtna appar** på bladet **Lägg till en princip**. Bladet **Tillåtna appar** öppnas och visar alla appar som redan ingår i listan för den här appskyddsprincipen.

2.  Välj **Lägg till appar** på bladet **Tillåtna appar**. Bladet **Lägg till appar** öppnas och visar alla appar som ingår i den här listan.

3.  Markera varje app för vilken du vill komma åt företagets data och välj sedan **OK**. Bladet **Tillåtna appar** uppdateras och visar alla markerade appar.

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>Lägg till en Store-app i listan över tillåtna appar

**Lägga till en Store-app**

1.  Välj namnet på din princip på bladet **App-princip** och välj sedan **Tillåtna appar** på menyn som visas med alla de appar som redan ingår i appskyddsprincipens lista.

2.  Välj **Lägg till appar** på bladet **Tillåtna appar**.

3.  Välj **Store-appar** i listrutan på bladet **Lägg till appar**. På bladet visas nu två kryssrutor där du kan lägga till en **utgivare** och **namn** för appen.

4.  Skriv appens och utgivarens namn och välj sedan **OK**.

    > [!TIP]
    > Här är ett app-exempel där **utgivaren** är *CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S Washington, C = = US* och produktens **namn** är *Microsoft.MicrosoftAppForWindows*.

5.  När du har fyllt i informationen i fälten, lägger du till appen i listan **Tillåtna appar** genom att välja **OK**.

> [!NOTE]
> Om du vill lägga till flera Store-appar samtidigt kan du klicka på menyn **(...)**  i slutet av appraden och sedan fortsätta att lägga till flera appar. Klicka på **OK** när du är klar.

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>Lägg till en skrivbordsapp i listan över tillåtna appar

**Lägga till en skrivbordsapp**

1.  Välj din princips namn på bladet **App-princip** och välj sedan **Tillåtna appar.** Bladet **Tillåtna appar** öppnas och visar alla appar som redan ingår i listan för den här appskyddsprincipen.

2.  Välj **Lägg till appar** på bladet **Tillåtna appar**.

3.  Välj **Skrivbordsappar** i listrutan på bladet **Lägg till appar**.

4.  När du har fyllt i informationen i fälten, lägger du till appen i listan **Tillåtna appar** genom att välja **OK**.

> [!NOTE]
> Om du vill lägga till flera **skrivbordsappar** samtidigt kan du klicka på menyn **(…)** i slutet av appraden och sedan fortsätta att lägga till flera appar. Klicka på **OK** när du är klar.

## <a name="wip-learning"></a>WIP-utbildning
<!---You've already defined WIP earlier in the topic. You don't need to keep doing so. --->
När du lägger till de appar som du vill skydda med RIA måste du använda ett skyddsläge med hjälp av **WIP-utbildning**.

### <a name="before-you-begin"></a>Innan du börjar

WIP-utbildning är en rapport som gör det möjligt att övervaka okända WIP-appar. De okända apparna är de som inte distribueras av organisationens IT-avdelning. Du kan exportera de här apparna från rapporten och lägga till dem i dina WIP-principer för att undvika avbrott i produktivitet innan de framtvingar WIP i blockeringsläge.

Vi rekommenderar att du börjar med **Tyst** eller **Tillåt åsidosättningar** medan du verifierar med en liten grupp att du har rätt appar på listan över tillåtna appar. När du är klar kan du ändra till din slutliga framtvingandeprincip, **blockera**.

### <a name="what-are-the-protection-modes"></a>Vad är skyddslägen?

#### <a name="block"></a>Blockera
WIP söker efter olämpliga datadelningsmetoder och stoppar från att utföra åtgärden. Detta kan inkludera delning av information till appar som inte skyddas av företaget, och delning av företagsdata mellan andra personer och enheter utanför organisationen.

#### <a name="allow-overrides"></a>Tillåt åsidosättningar
WIP söker efter olämplig delning av data och varnar användarna om de gör något som kan vara potentiellt osäkert. I det här läget kan dock användaren åsidosätta principen och dela data genom att logga åtgärden i din granskningslogg.

#### <a name="silent"></a>Tyst
WIP körs i bakgrunden och loggar olämplig datadelning utan att blockera något som skulle kräva interaktion av medarbetarna i läget Tillåt åsidosättning. Ej tillåtna åtgärder, t.ex. appar som på felaktigt sätt försöker få åtkomst till en nätverksresurs eller WIP-skyddade data, stoppas dock.

#### <a name="off-not-recommended"></a>Av (rekommenderas inte)
WIP har stängts av och bidrar inte till att skydda eller granska dina data.

När du stänger av WIP görs ett försök att dekryptera eventuella WIP-taggade filer på de lokalt anslutna enheterna. Tänk på att tidigare dekrypterings- och principinformation inte automatiskt tillämpas på nytt om du aktiverar WIP-skyddet igen.

### <a name="add-a-protection-mode"></a>Lägga till ett skyddsläge

1.  Välj principens namn på bladet **App-princip** och välj sedan **Nödvändiga inställningar**.

    ![Skärmdump av utbildningsläge](./media/learning-mode-sc1.png)

1.  Välj **Spara**.

### <a name="use-wip-learning"></a>Använda WIP-utbildning

1. Öppna Azure-portalen. Välj **Fler tjänster**. Skriv **Intune** i textrutefiltret.

3. Välj **Intune** > **Mobilappar**.

4. Välj **Appskyddsstatus** > **Rapporter** > **Windows informationsskydd-inlärning**.  
 
    När apparna väl visas i loggningsrapporten för WIP-utbildning kan du lägga till dem i appskyddsprinciperna.

## <a name="deploy-your-wip-app-protection-policy"></a>Distribuera WIP-appskyddsprincipen

> [!IMPORTANT]
> Detta gäller för WIP utan enhetsregistrering.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

När du har skapat din WIP-appskyddsprincip måste du distribuera den till din organisation med hjälp av hantering av mobila program.

1.  Välj den appskyddsprincip du precis skapade på bladet **Apprincip**, välj **Användargrupper** > **Lägg till användargrupp**.

    En lista med användargrupper, som består av alla säkerhetsgrupper i Azure Active Directory, öppnas på bladet **Lägg till användargrupp**.

1.  Välj den grupp du vill att principen ska tillämpas på och distribuera sedan principen genom att välja **Välj**.
