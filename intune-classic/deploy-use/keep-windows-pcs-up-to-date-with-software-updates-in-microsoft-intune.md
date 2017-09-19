---
title: "Programuppdateringar för Windows-datorer"
description: "Intune håller dina hanterade datorer uppdaterade genom att snabbt installera de senaste korrigeringarna och programvaruuppdateringarna."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 48e9c41a-d2de-424e-9610-cfd1ad514210
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fc9ff89294e0b9ba6050be9724a78eb504b1f51a
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune"></a>Hålla datorerna uppdaterade med programvaruuppdateringar i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune hjälper dig att skydda dina hanterade datorer på flera sätt, t.ex. med hantering av programvaruuppdateringar som håller datorerna uppdaterade genom att se till att de senaste korrigeringarna och programvaruuppdateringarna snabbt installeras.

Om du ännu inte har installerat Intune-klienten på dina datorer, se [Installera Windows PC-klienten med Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

När det finns nya uppdateringar från Microsoft Update eller om du har skapat en uppdatering från tredje part och de är tillämpliga på hanterade datorer, visas ett meddelande på sidan **Översikt** i arbetsytan **Uppdateringar**. När du har valt den här länken kan du utföra olika åtgärder som att visa mer information om uppdateringen, godkänna eller avböja uppdateringen och visa de datorer som ska installera uppdateringen om den godkänns.

> [!IMPORTANT]
> Arbetsytan **Uppdateringar** visas inte i administratörskonsolen förrän du har installerat klienten på och hanterar minst en datorklient.

När uppdateringar har godkänts och installerats kan du se om installationen har lyckats eller misslyckats i arbetsytan **Uppdateringar** i Intune-konsolen.

Följande avsnitt hjälper dig att hålla program uppdaterade på hanterade datorer.

## <a name="before-you-start"></a>Innan du börjar
Innan du börjar skapa och godkänna programuppdateringar kan du konfigurera och distribuera principer för datorerna som styr hur och när uppdateringarna installeras.

### <a name="to-configure-update-policy-settings"></a>Så här konfigurerar du principinställningar för uppdateringar

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du **Princip** &gt; **Översikt** &gt; **Lägg till princip**.

2.  Konfigurera och distribuera en inställningsprincip för **Microsoft Intune-agenten** för inställningar för uppdateringar. Du kan använda rekommenderade inställningar eller anpassa inställningarna. Om du behöver mer information om hur du skapar och distribuerar principer läser du [Vanliga hanteringsuppgifter för Windows-datorer med Microsoft Intune-datorklienten](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

I följande tabell visar värdena som du kan konfigurera i principen och rekommenderade värden som ska användas om du inte anpassar principen. Du hittar de här inställningarna i avsnittet **Uppdateringar** .

  |Principinställningar|Information|
    |------------------|--------------------|
    |**Frekvens för uppdatering och identifiering av program (timmar)** |Anger hur ofta (8–22 timmar) som Intune söker efter nya uppdateringar och program.<br /><br />Rekommenderat värde: **8** timmar.|
    |**Automatisk eller begärd installation av uppdateringar och program** |Anger om uppdateringar installeras automatiskt eller om användaren uppmanas att installera. Dessutom gör inställningen att du kan schemalägga installationen av uppdateringar och program.<br /><br />**Installera uppdateringar och program automatiskt enligt schema** installerar uppdateringar och program med hjälp av det angivna schemat.<br /><br />**Använd Automatiskt underhåll för Windows-datorer**  är en beroende principinställning som ser till att uppdateringar och program installeras i samband med automatiskt underhåll i Windows.<br /><br />**Fråga användare om installation** uppmanar användaren att installera uppdateringar när de är klara.<br /><br />Rekommenderade värden:<br /><br />**Installera uppdateringar och program automatiskt som schemalagda** vald<br /><br />**Schemalagd dag: Varje dag**<br /><br />**Schemalagd tid: 03:00**<br /><br />**Använd automatiskt underhåll för Windows-datorer** vald|
    |**Tillåt omedelbar installation av uppdateringar som inte avbryter Windows** |**Tillåt** installerar uppdateringar direkt när de har hämtats, med undantag av uppdateringar som avbryter eller startar om Windows. Uppdateringarna har installerats enligt konfigurationen av inställningen **Automatisk eller ange installation av uppdateringar och program** .<br /><br />**Tillåt inte** installerar uppdateringar enligt konfigurationen av inställningen **Automatisk eller ange installation av uppdateringar och program**.<br /><br />Rekommenderat värde: **Tillåt** |
    |**Fördröjning att starta om Windows efter installationen av schemalagda uppdateringar och program (minuter)** |Anger (1–30 minuter) väntetiden för att starta om Windows efter installationen av schemalagda uppdateringar och program.<br /><br />Rekommenderat värde: **15 minuter** |
    |**Fördröjning efter omstart av Windows om du vill börja installera missade schemalagda uppdateringar och program (minuter)** |Anger (1–60 minuter) väntetiden för att starta installationen av uppdateringar och program när Windows startas om efter att en schemalagd uppdatering missades.<br /><br />Rekommenderat värde: **5 minuter**|
    |**Tillåt inloggade användaren att styra omstart av Windows efter installationen av schemalagda uppdateringar och program** |Anger om den inloggade användaren kan vänta med att starta om Windows (om inställningen är **Ja**) eller bli meddelad om automatisk omstart av Windows (om inställningen är **Nej**). Om ingen användare är inloggad när schemalagd installation av uppdateringar och program har slutförts startas Windows automatiskt om vid behov. När inställningen är **Nej**startar Windows om efter 5 minuter.<br /><br />Rekommenderat värde: **Ja**|
    |**Uppmana användaren att starta om Windows under obligatoriska uppdateringar för Intune-klientagenten** |Anger om de inloggade användarna uppmanas att starta om Windows när en obligatorisk Intune-klientuppdatering kräver att Windows startar om.<br /><br />Rekommenderat värde: **Ja**|
    |**Schema för installation av obligatoriska Microsoft Intune-klientagentuppdateringar** |Schemalägger när installationen av klientuppdateringar sker.<br /><br />Rekommenderat värde: inte konfigurerat|
    |**Fördröjning mellan uppmaningar att starta om Windows efter installationen av schemalagda uppdateringar och program (minuter)** |Anger hur ofta (1–1 440 minuter) användaren uppmanas att starta om Windows när en schemalagd uppdatering eller ett program som kräver att Windows startas om är installerat och användaren försenar omstarten.<br /><br />Rekommenderat värde: **30 minuter** |

## <a name="update-software-made-by-microsoft"></a>Uppdatera programvara som tillverkats av Microsoft
Uppdatering av programvara från Microsoft kräver mycket lite av dig. Men innan du börjar finns det två saker du ska konfigurera:

-   **Produktkategorier och klassificeringar för uppdatering** – definierar kategorier och klassificeringar av uppdateringar som du vill göra tillgängliga för datorer. Du kan till exempel bestämma att du bara vill att kritiska uppdateringar för Microsoft Office ska installeras.

-   **Regler för automatiskt godkännande** – dessa regler godkänner automatiskt angivna typer av uppdateringar och minskar de administrativa omkostnaderna. Till exempel kanske du vill godkänna alla viktiga uppdateringar automatiskt.

Använd följande två procedurer för att bli redo att använda programvaruuppdateringar:

### <a name="configure-the-product-categories-and-update-classifications-you-want-to-make-available-to-managed-computers"></a>Konfigurera produktkategorierna och uppdatera klassificeringarna som du vill göra tillgängliga för hanterade datorer

1.  Klicka på **Admin** &gt; **Uppdateringar** i [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/).

2.  På sidan **Tjänstinställningar: Uppdateringar** väljer du de uppdateringskategorier som du vill göra tillgängliga för datorer i listan **Produktkategori** . Observera att de vanligaste uppdateringarna är markerade som standard.

    > [!IMPORTANT]
    > Om du vill säkerställa att datorer får de uppdateringar som har godkänts av administratören ska inte WSUS-grupprincipinställningen (WSUS = Windows Server Update Services) **Ange sökväg till tjänsten Microsoft Update på intranätet** tillämpas på datorer som har registrerats med Intune.

3.  I listan **Uppdatera klassificering** väljer du de uppdateringsklasser som du vill göra tillgängliga för hanterade datorer. De vanligaste alternativen är markerade som standard.

4.  Välj **Spara** för att spara dina val.

### <a name="to-configure-automatic-approval-rules-for-software-updates"></a>Så här konfigurerar du automatiska godkännanderegler för programvaruuppdateringar

1.  Klicka på **Admin** &gt; **Uppdateringar** i [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/).

2.  I ämnet **Regler för automatiska godkännanden** på sidan **Serverinställningar: Uppdateringar** väljer du **Ny**.

3.  På sidan **Allmänt** i guiden Skapa regler för automatiskt godkännande anger du ett namn för och en valfri beskrivning av regeln.

4.  På sidan **Produktkategorier** markerar du alla produkter som du vill godkänna uppdateringar automatiskt för.

5.  På sidan **Uppdatera klassificeringar** anger du de uppdateringsklassificeringar som du vill ska godkännas automatiskt.

6.  På sidan **Distribution** gör du följande:

    -   Markera de datorgrupper som du vill distribuera den nya regeln till, och välj sedan **Lägg till**.

    -   Om du vill ange en tidsgräns för installation för uppdateringarna markerar du kryssrutan **Framtvinga en tidsgräns för installation för dessa uppdateringar** och väljer sedan tidsgräns för installation i listan **Tidsgräns för installation** .

        > [!NOTE]
        > Om du anger en tidsgräns för installation kan den hanterade datorn behöva startas om en eller flera gånger när tidsgränsen har överskridits.

    -   Välj **Nästa**när du är klar.

7.  På sidan **Sammanfattning** granskar du inställningarna för den nya regeln och väljer sedan **Slutför**.

Den nya regeln visas i ämnet **Regler för automatiska godkännanden** på sidan **Tjänstinställningar: Uppdateringar** .

> [!NOTE]
> När du skapar en regel för automatiskt godkännande godkänner den bara framtida uppdateringar och godkänner inte automatiskt tidigare uppdateringar som redan finns i Intune. Om du vill godkänna dessa uppdateringar behöver du köra regeln för automatiskt godkännande.


### <a name="to-edit-run-or-delete-an-automatically-approved-update-rule"></a>Så här redigerar du, kör eller tar bort en automatiskt godkänd uppdateringsregel

1.  Klicka på **Admin** &gt; **Uppdateringar** i [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/).

2.  I avsnittet **Regler för automatiskt godkännande** markerar du en regel och gör sedan något av följande:

    -   Om du vill redigera regeln väljer du **Redigera** och ändrar sedan regelns parametrar i **guiden Uppdatera regler för automatiskt godkännande**.

    -   Om du vill köra regeln väljer du **Kör valda**.

    -   Om du vill ta bort regeln väljer du **Ta bort**.

        > [!NOTE]
        > Om du tar bort en regel påverkas inte tidigare uppdateringar som har godkänts av den borttagna regeln.

## <a name="update-software-not-made-by-microsoft"></a>Uppdatera programvara som inte tillverkats av Microsoft
Du kan distribuera uppdateringar för programvara som inte tillverkas av Microsoft. Du kan göra detta med hjälp av guiden **Överför uppdatering** för att hämta uppdateringen till lagringsutrymmet i molnet. Sedan kan du godkänna eller neka uppdateringen precis som med Microsoft-programvara.

### <a name="to-upload-and-configure-a-third-party-update"></a>Så här överför och konfigurerar du en uppdatering från tredje part

1.  Klicka på**Uppdateringar** &gt; **Översikt** &gt; **Överför** i [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/).

2.  På sidan **Uppdatera filer** väljer du **Bläddra** för att välja de installationsfiler som krävs för att installera uppdateringspaketet. Filen kan vara en Windows Installer-fil (.msi), en Windows Installer-korrigeringsfil (.msp) eller en .exe-fil. Du kan även inkludera eventuella ytterligare filer och mappar som finns i samma mapp som installationsfilen.

    Den totala storleken på de markerade filerna som ska överföras visas. Observera att den här storleken inte inkluderar okomprimerade eller expanderade storlekar på installationsfiler.

3.  När du har angett installationsfilerna visar sidan **Uppdatera beskrivning** namn, beskrivning och klassificering för information om programvara som Intune extraherat från installationsfilerna för programvara. Du kan välja en klassificering som anger vilken typ av uppdatering som du distribuerar (uppdateringar, viktiga uppdateringar, säkerhetsuppdateringar, samlade uppdateringar eller Service Packs). Välj **Nästa** när du är klar.

4.  På sidan **Krav** i guiden väljer du arkitektur (32-bitars, 64-bitars eller båda) och operativsystem för de hanterade datorer som uppdateringen ska användas för.

5.  På sidan **Regler för identifiering** anger du hur Intune avgör om uppdateringen redan finns på hanterade datorer. Om du använder standardalternativet **Använd standardregler för identifiering** installerar Intune alltid uppdateringspaketet på varje måldator en gång.

    > [!NOTE]
    > Om installationsfilen för uppdateringen som du angav är en Windows Installer-fil eller en MSP-fil visas inte sidan **Regler för identifiering** i guiden. Det beror på att Windows Installer och MSP-filer innehåller egna instruktioner för att upptäcka tidigare uppdateringsinstallationer.

    Välj en eller flera av följande regler för att fastställa om uppdateringen redan är installerad på hanterade datorer:

    -   **Filen finns**

    -   **MSI-produktkod finns**

    -   **Registernyckeln finns**

6.  Ange ytterligare information som krävs för att konfigurera identifieringsregeln, till exempel en sökväg och ett namn, produktkod för Windows Installer eller en registernyckel, och välj sedan **Nästa**.

7.  På sidan **Krav** i guiden anger du all programvara som måste vara installerad innan den här uppdateringen kan installeras. Du kan ange **Ingen**, välja ett programpaket som redan har lagts till och hanteras av Intune eller ange en av följande regler som beskriver programvaran:

    -   **Filen finns**

    -   **MSI-produktkod finns**

    -   **Registernyckeln finns**

8.  Ange ytterligare information som krävs för att konfigurera identifieringsregeln, till exempel en sökväg och ett namn, produktkod för Windows Installer eller en registernyckel, och välj sedan **Nästa**.

9. På sidan **Kommandoradsargument** i guiden kan du lägga till alla installationsegenskaper som krävs på kommandoraden för att ändra funktionen för installationsfilen. Till exempel stöder vissa program egenskapen **/q** för att möjliggöra tyst installation. I dokumentationen för programpaketet kan du lära dig mer om alla kommandoradsargument som stöds. Ange de kommandoradsargument du behöver och välj sedan **Nästa**.

    > [!NOTE]
    > Om uppdateringen inte har stöd för tyst installation kan du inte installera uppdateringen med hjälp av Intune.

10. På sidan **Returkoder** i guiden kan du ange hur returkoderna från uppdateringsinstallationen tolkas. Som standard använder Intune standardmässiga returkoder för att rapportera en misslyckad eller lyckad installation av ett uppdateringspaketet. Returkoder:

|Returkod|Information|
|---------------|------------------|
|**0**|Klart|
|**3010**|Lyckas med omstart|

11. Returkoder som inte listas anses vara fel.
Vissa uppdateringar är icke-standardmässiga tolkningar för returkoder. I dessa fall kan du ange egna tolkningar av returkoder.

12. Ange eller redigera önskade returkoder, och välj sedan **Nästa**.

13. På sidan **Sammanfattning** i guiden granskar du de åtgärder som kommer att vidtas och väljer sedan **Överför** för att slutföra guiden.

Överförd uppdatering lagras i molnarkivet för Intune. Om du inte har tillräckligt mycket ledigt utrymme för att ladda upp uppdateringspaketet får du ett meddelande om detta under överföringsprocessen. Intune kan inte fastställa om det finns tillräckligt mycket ledigt utrymme förrän överföringen av uppdateringen har börjat eftersom komprimerade konfigurations- och installationsfiler kräver mer utrymme när de dekomprimeras.

När paketet har överförts till Intune visas en uppdatering från tredje part i arbetsytan **Uppdateringar** i fönstret **Alla uppdateringar**. Du kan sedan godkänna och distribuera uppdateringen. Mer information finns i avsnittet "Godkänna och neka uppdateringar".

## <a name="approve-and-decline-updates"></a>Godkänna och neka uppdateringar
När uppdateringar är redo att installeras visas ett meddelande på sidan **Översikt över uppdateringar** i arbetsytan **Uppdateringar** under **Uppdateringsstatus**. Välj det här meddelandet för att öppna sidan **Alla uppdateringar** och se vilka uppdateringar som är klara för godkännande.

Du kan använda listan **Filter** om du vill göra det lättare att söka efter uppdateringar. Du kan till exempel visa endast uppdateringar som misslyckats eller uppdateringar som ersätts.

När du väljer en uppdatering från listan blir ytterligare kommandon tillgängliga som gör att du kan hantera uppdateringar på det sätt som visas i följande tabell:

|Aktivitet|Information|
|--------|--------------------|
|**Visa egenskaper**|Visar detaljerad information om uppdateringen inklusive hur många datorer som den är tillämpbar för.|
|**Redigera**|Endast för uppdateringar för program som inte kommer från Microsoft. Gör att du kan redigera egenskaperna för uppdateringen.|
|**Godkänn**|Godkänner den markerade uppdateringen och gör att du kan konfigurera vilka grupper den distribueras till. Mer information finns i proceduren **Så här godkänner du uppdateringar** i det här avsnittet.|
|**Neka**|Tar bort alla tidigare godkännanden för uppdateringen och döljer uppdateringen från standardvyer. Dessutom tas alla rapportdata för uppdateringen bort.<br /><br />Om du vill hitta en nekad uppdatering anger du filtret på sidan **Alla uppdateringar** till **Avböjt**. Du kan sedan godkänna denna uppdatering.<br /><br />Om en uppdatering har nekats eftersom uppdateringen har upphört att gälla i Microsoft Update kan inte uppdateringen godkännas i administrationskonsolen för Intune.<br /><br />Om du tar bort en uppdateringsprincip som distribueras till datorer återställs värdena för dessa principinställningar för uppdateringar till standardläget för operativsystemet som har installerats på datorerna.|
|**Ta bort**|Endast för uppdateringar för program som inte kommer från Microsoft. Tar bort den markerade uppdateringen.|
|**Överför**|Startar guiden **Överför uppdatering** som gör det möjligt att överföra uppdateringar från andra tillverkare än Microsoft som du vill distribuera.|

### <a name="to-approve-updates"></a>Så här godkänner du uppdateringar

1.  Klicka på **Uppdateringar** &gt; **Översikt** &gt; **Nya uppdateringar att godkänna** i [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/).

    Välj **Översikt** &gt; **Nya uppdateringar att godkänna** på arbetsytan **Uppdateringar**.

    > [!NOTE]
    > Länken **Nya uppdateringar att godkänna** visas bara i området **Uppdateringsstatus** när det finns minst en hanterad dator där en uppdatering behöver godkännas.

2.  Välj en uppdatering, granska uppdateringsegenskaperna längst ned på sidan för att säkerställa att du vill godkänna uppdateringen, och välj **Godkänn**. Du kan välja flera uppdateringar genom att hålla ned tangenten **CTRL** när du markerar varje objekt.

3.  På sidan **Välj grupper** markerar du en grupp som du vill distribuera uppdateringar till och väljer sedan **Lägg till**. När du är klar väljer du **Nästa**.

4.  På sidan **Distributionsåtgärd** gör du följande för varje grupp i listan:

    -   I listan **Godkännande** väljer du något av följande:

        -   **Installation krävs** – installerar uppdateringen på datorer i den angivna gruppen.

        -   **Installera inte** – rapporterar bara tillämpbarhet och installerar inte uppdateringen.

        -   **Tillgänglig installation** – användaren kan installera programmet på begäran från företagsportalen.

        -   **Avinstallera** – tar bort uppdateringar från datorer i målgruppen.

            > [!IMPORTANT]
            > Uppdateringen tas bort även om den inte har installerats av Intune.

    -   I listan **Tidsgräns** väljer du något av följande:

        -   **Ingen** – anger att ingen tidsgräns framtvingas för installationen av uppdateringen och användare kan neka uppdateringen kontinuerligt.

        -   **Så snart som möjligt** – installerar uppdateringen vid nästa tillfälle på måldatorerna.

        -   **Anpassad** – anger datum och tid då godkända uppdateringar installeras.

        -   **En vecka**, **två veckor**, **en månad** – installerar uppdateringen inom den angivna tidsperioden.

5.  Välj **Slutför** för att spara inställningarna eller välj **Avbryt** för att ignorera inställningen och återgå till listan med uppdateringar.

    > [!IMPORTANT]
    > Om inte åtgärden **Installera inte**, **Installation krävs**eller **Avinstallera** uttryckligen har konfigurerats för en underordnad grupp ärvs en åtgärd som konfigurerats för en överordnad grupp av alla underordnade.

6.  Du kan kontrollera informationsfönstret längst ned på sidan **Alla uppdateringar** för påminnelsemeddelanden om uppdateringen.


### <a name="see-also"></a>Se även
[Principer för att skydda Windows-datorer](policies-to-protect-windows-pcs-in-microsoft-intune.md)
