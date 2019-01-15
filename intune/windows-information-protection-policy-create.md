---
title: Skapa och distribuera en WIP-appskyddsprincip | Microsoft Intune
description: Skapa och distribuera en WIP-appskyddsprincip med Microsoft Intune
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f91f5b9779c3067a3120864eaf265346efd8a02
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297442"
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Skapa och distribuera en WIP-appskyddsprincip med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan använda appskyddsprinciper med Windows 10-appar för att skydda appar utan enhetsregistrering.

## <a name="before-you-begin"></a>Innan du börjar

Du måste känna till några grundläggande begrepp när du lägger till en WIP-princip:

### <a name="list-of-allowed-and-exempt-apps"></a>Lista över tillåtna och undantagna appar

-   **Skyddade appar:** Dessa appar måste följa den här principen.

-   **Undantagna appar:** De här apparna har undantagits från den här principen och har åtkomst till företagets data utan begränsningar.

### <a name="types-of-apps"></a>Apptyper

-   **Rekommenderade appar:** En i förväg ifylld lista med appar (huvudsakligen för Microsoft Office) som du enkelt kan importera till principen.
-   **Store-appar:** Du kan lägga till valfri app från Windows Store i principen.
-   **Windows-skrivbordsappar:** Du kan lägga till valfria traditionella Windows-skrivbordsappar i principen (t.ex. .exe, .dll osv.)

## <a name="prerequisites"></a>Krav

Du måste konfigurera MAM-providern innan du kan skapa en WIP-appskyddsprincip. Läs mer i [Konfigurera din MAM-provider med Intune](app-protection-policies-configure-windows-10.md).  

> [!IMPORTANT]
> RIA stöder inte multi-identitet. Det kan bara finnas en hanterad identitet åt gången.

Du måste dessutom ha följande licens och uppdatering:

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)-licens
-   [Windows Creators-uppdatering](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)





## <a name="to-add-a-wip-app-protection-policy"></a>Lägga till en WIP-appskyddsprincip

När du konfigurerar Intune i din organisation kan du skapa en WIP-specifik princip.

> [!TIP]  
> Mer information om hur du skapar WIP-principer för Intune, inklusive tillgängliga inställningar och hur du konfigurerar dem, finns i [Skapa en princip för Windows Information Protection (WIP) med MAM med hjälp av Azure-portalen för Microsoft Intune](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure) i dokumentationsbiblioteket för Windows-säkerhet. 


1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**.
3. Välj **Klientappar** på **Microsoft Intune**-bladet.
4. Välj **Appskyddsprinciper** på bladet **Klientappar**.
5. Välj **Lägg till en princip** så att bladet **Lägg till en princip** visas.
6. Lägg till följande värden:
    - **Namn:** Skriv ett namn (obligatoriskt) för den nya principen.
    - **Beskrivning:** (Valfritt) Ge en beskrivning.
    - **Plattform:** Välj **Windows 10** som den plattform som stöds för din appskyddsprincip.
    - **Registreringsstatus:** Välj **Utan registrering** som din princips registreringsstatus.
7.  Välj **Skapa**. Principen skapas och visas i tabellen på bladet **Appskyddsprinciper**.

## <a name="to-add-recommended-apps-to-your-protected-apps-list"></a>Lägga till rekommenderade appar i listan över skyddade appar

1. Välj **Klientappar** på **Microsoft Intune**-bladet.
2. Välj **Appskyddsprinciper** på bladet **Klientappar**.
3. På bladet **Appskyddsprinciper** väljer du den princip som du vill ändra. Bladet **Intune-appskydd** visas.
4. Välj **Skyddade appar** på bladet **Intune-appskydd**. Bladet **Skyddade appar** öppnas och visar alla appar som redan ingår i listan för den här appskyddsprincipen.
5. Välj **Lägg till appar**. I **Lägg till appar** visas en filtrerad lista med appar. I listan längst upp på bladet kan du ändra listfiltret.
6. Markera varje app som ska få åtkomst till företagets data.
7. Klicka på **OK**. Bladet **Skyddade appar** uppdateras och visar alla markerade appar.
8. Klicka på **Spara**.

## <a name="add-a-store-app-to-your-protected-apps-list"></a>Lägga till en Store-app i listan över skyddade appar

**Lägga till en Store-app**
1. Välj **Klientappar** på **Microsoft Intune**-bladet.
2. Välj **Appskyddsprinciper** på bladet **Klientappar**.
3. På bladet **Appskyddsprinciper** väljer du den princip som du vill ändra. Bladet **Intune-appskydd** visas.
4. Välj **Skyddade appar** på bladet **Intune-appskydd**. Bladet **Skyddade appar** öppnas och visar alla appar som redan ingår i listan för den här appskyddsprincipen.
5. Välj **Lägg till appar**. I **Lägg till appar** visas en filtrerad lista med appar. I listan längst upp på bladet kan du ändra listfiltret.
6. Välj **Store-appar** i listan.
7. Ange värden för **Namn**, **Utgivare**, **Produktnamn** och **Åtgärd**. Se till att ange värdet för **Åtgärd** till **Tillåt** så att appen får åtkomst till företagets data.
9. Klicka på **OK**. Bladet **Skyddade appar** uppdateras och visar alla markerade appar.
10. Klicka på **Spara**.

## <a name="add-a-desktop-app-to-your-protected-apps-list"></a>Lägga till en skrivbordsapp i listan över skyddade appar

**Lägga till en skrivbordsapp**
1. Välj **Klientappar** på **Microsoft Intune**-bladet.
2. Välj **Appskyddsprinciper** på bladet **Klientappar**.
3. På bladet **Appskyddsprinciper** väljer du den princip som du vill ändra. Bladet **Intune-appskydd** visas.
4. Välj **Skyddade appar** på bladet **Intune-appskydd**. Bladet **Skyddade appar** öppnas och visar alla appar som redan ingår i listan för den här appskyddsprincipen.
5. Välj **Lägg till appar**. I **Lägg till appar** visas en filtrerad lista med appar. I listan längst upp på bladet kan du ändra listfiltret.
6. Välj **Skrivbordsappar** i listan.
7. Ange värden för **Namn**, **Utgivare**, **Produktnamn**, **Fil**, **Lägsta version**, **Högsta version** och **Åtgärd**. Se till att ange värdet för **Åtgärd** till **Tillåt** så att appen får åtkomst till företagets data.
9. Klicka på **OK**. Bladet **Skyddade appar** uppdateras och visar alla markerade appar.
10. Klicka på **Spara**.

## <a name="wip-learning"></a>WIP-utbildning
När du lägger till de appar som du vill skydda med RIA måste du använda ett skyddsläge med hjälp av **WIP-utbildning**.

### <a name="before-you-begin"></a>Innan du börjar

WIP-utbildning är en rapport som gör det möjligt att övervaka WIP-aktiverade appar och okända WIP-appar. De okända apparna är de som inte distribueras av organisationens IT-avdelning. Du kan exportera de här apparna från rapporten och lägga till dem i dina WIP-principer för att undvika avbrott i produktivitet innan de framtvingar WIP i blockeringsläge.

<!-- 1631908 --> Förutom att visa information om WIP-aktiverade appar kan du visa en sammanfattning av de enheter som har delat arbetsdata med webbplatser. Med den här informationen kan du bestämma vilka webbplatser som ska läggas till i gruppernas och användarnas PIA-principer. I sammanfattningen visas vilka webbplatsadresser som används av WIP-aktiverade appar.

När du arbetar med WIP-aktiverade appar och okända WIP-appar rekommenderar vi att du börjar med **Tyst** eller **Tillåt åsidosättningar** medan du verifierar med en liten grupp att du har rätt appar på listan över skyddade appar. När du är klar kan du ändra till din slutliga framtvingandeprincip, **blockera**.

### <a name="what-are-the-protection-modes"></a>Vad är skyddslägen?

#### <a name="block"></a>Blockera
WIP söker efter olämpliga datadelningsmetoder och stoppar från att utföra åtgärden. Exempel på blockerade åtgärder kan vara delning av information till appar som inte skyddas av företaget, och delning av företagsdata mellan andra personer och enheter utanför organisationen.

#### <a name="allow-overrides"></a>Tillåt åsidosättningar
Windows informationsskydd söker efter olämplig delning av data och varnar användarna om de gör något som kan vara potentiellt osäkert. I det här läget kan dock användaren åsidosätta principen och dela data genom att logga åtgärden i din granskningslogg.

#### <a name="silent"></a>Tyst
WIP körs i bakgrunden och loggar olämplig datadelning utan att blockera något som skulle kräva interaktion av medarbetarna i läget Tillåt åsidosättning. Ej tillåtna åtgärder, t.ex. appar som på felaktigt sätt försöker få åtkomst till en nätverksresurs eller WIP-skyddade data, stoppas dock.

#### <a name="off-not-recommended"></a>Av (rekommenderas inte)
WIP har stängts av och bidrar inte till att skydda eller granska dina data.

När du stänger av WIP görs ett försök att dekryptera eventuella WIP-taggade filer på de lokalt anslutna enheterna. Observera att tidigare dekrypterings- och principinformation inte automatiskt tillämpas på nytt om du aktiverar Windows informationsskydd igen.

### <a name="add-a-protection-mode"></a>Lägga till ett skyddsläge

1.  Välj principens namn på bladet **Apprincip** och välj sedan **Nödvändiga inställningar**.

    ![Skärmbild av fönstret Inlärningsläge](./media/learning-mode-sc1.png)

1.  Välj en inställning och välj sedan **Spara**.

### <a name="use-wip-learning"></a>Använda WIP-utbildning

1. Öppna [Azure Portal](https://portal.azure.com). Välj **Alla tjänster**. Skriv **Intune** i textrutefiltret.

3. Välj **Intune** > **Klientappar**.

4. Välj **Appskyddsstatus** > **Rapporter** > **Windows informationsskydd-inlärning**.  

    När apparna väl visas i loggningsrapporten för WIP-utbildning kan du lägga till dem i appskyddsprinciperna.

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>Tillåt att Windows Search-indexeraren söker efter krypterade objekt
Tillåter eller nekar indexering av objekt. Den här växeln används för Windows Search-indexeraren och styr om objekt som är krypterade indexeras, till exempel Windows informationsskyddade filer.

Alternativ för den här appens skyddsprincip finns i **Avancerade inställningar** i Windows informationsskyddsprincip. Appens skyddsprincip måste anges för *Windows 10*-plattformen och apprincipen **Registreringsstatus** måste anges som **Med registrering**.

När principen är aktiverad indexeras Windows informationsskyddade objekt och deras metadata lagras på en okrypterad plats. Dessa metadata innehåller exempelvis ändrade sökvägar och datum.

När principen är inaktiverad indexeras inte Windows informationsskyddade objekt och resultaten visas inte i Cortana eller Utforskaren. Det kan också förekomma en prestandapåverkan på foton och Groove-appar om det finns många Windows informationsskyddade mediefiler på enheten.

## <a name="add-encrypted-file-extensions"></a>Lägga till filnamnstillägg för krypterade filer

Förutom att ställa in alternativet **Tillåt att Windows Search-indexeraren söker efter krypterade objekt** kan du ange en lista med filnamnstillägg. Filer med dessa filnamnstillägg krypteras när du kopierar från en SMB-resurs (Server Message Block) inom den företagsgräns som definierats i listan med nätverksplatser. Om den här principen inte anges används den befintliga funktionen för automatisk kryptering. När principen är konfigurerad krypteras endast filer med dessa filnamnstillägg i listan.

## <a name="deploy-your-wip-app-protection-policy"></a>Distribuera WIP-appskyddsprincipen

> [!IMPORTANT]
> Denna information gäller för Windows informationsskydd utan enhetsregistrering.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

När du har skapat din WIP-appskyddsprincip måste du distribuera den till din organisation med hjälp av hantering av mobila program.

1.  Välj den appskyddsprincip du precis skapade på bladet **Apprincip**, välj **Användargrupper** > **Lägg till användargrupp**.

    En lista med användargrupper, som består av alla säkerhetsgrupper i Azure Active Directory, öppnas på bladet **Lägg till användargrupp**.

2.  Välj den grupp du vill att principen ska tillämpas på och distribuera sedan principen genom att välja **Välj**.

## <a name="next-steps"></a>Nästa steg

Mer information om Windows informationsskydd finns i [Skydda företagsdata med Windows informationsskydd](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).
