---
title: Skapa och distribuera MAM-principer
description: Följ instruktionerna i det här avsnittet om du vill skapa och distribuera hanteringsprinciper för mobilappar.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cc133071f4d6c0d1a3bbb3acc7c0bd5cb45b6cef
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="create-and-deploy-app-protection-policies-with-microsoft-intune"></a>Skapa och distribuera appskyddsprinciper med Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Det här avsnittet beskriver hur du skapar en appskyddsprincip på **Azure-portalen**. Azure-portalen är den nya administratörskonsolen för att skapa appskyddsprinciper och vi rekommenderar att du använder den här portalen när du skapar appskyddsprinciper. Azure Portal har stöd för följande MAM-scenarier:

- Enheter som har registrerats i Intune.
- Enheter som hanteras av en MDM-lösning från tredje part.
- Enheter som inte hanteras av någon MDM-lösning (BYOD).

> [!IMPORTANT]
> Tänk på följande om du hanterar dina enheter med **Intune-administratörskonsolen**:
> 
> * Du kan skapa en appskyddsprincip som stöder appar för enheter som registrerats i Intune med hjälp av [Intune-administratörskonsolen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).
> * Appskyddsprinciper som skapats i Intune-administratörskonsolen kan inte importeras till Azure-portalen.  Appskyddsprinciperna måste återskapas på Azure-portalen.
> 
> * Du kanske inte ser alla inställningar för appskyddsprinciper i Intune-administratörskonsolen. Azure-portalen är den nya administratörskonsolen för att skapa appskyddsprinciper.
> 
> * För att distribuera hanterade appar måste du skapa en appskyddsprincip i Intune-administratörskonsolen. I detta fall kanske du vill skapa appskyddsprinciper i både Intune-administratörskonsolen och på Azure-portalen: I Intune-administratörskonsolen så att du kan distribuera hanterade appar och på Azure-portalen eftersom det är den nya administratörskonsolen där alla inställningar för appskyddsprinciper finns.
> 
> * Om du skapar appskyddsprinciper i både Intune-administratörskonsolen och på Azure-portalen används de principer som du skapar på Azure-portalen för apparna.

Om du vill se en lista över principinställningar som stöds för Android- och iOS-plattformar kan du välja något av följande:

> [!div class="op_single_selector"]
> - [iOS-principer](ios-mam-policy-settings.md)
> - [Android-principer](android-mam-policy-settings.md)

- En mer detaljerad beskrivning av hur appskyddsprinciper fungerar och scenarier som stöds av appskyddsprinciper i Intune finns i avsnittet om [hur du skyddar appdata med hjälp av appskyddsprinciper](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

##  <a name="create-an-app-protection-policy"></a>Skapa en appskyddsprincip
Appskyddsprinciper skapas på Azure-portalen. Om det är första gången du använder Azure-portalen läser du avsnittet om [Azure-portalen för appskyddsprinciper i Microsoft Intune](azure-portal-for-microsoft-intune-mam-policies.md) för att bekanta dig med portalen. Läs avsnittet om [krav och support](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md) innan du skapar en appskyddsprincip.

Du skapar appskyddsprinciper genom att följa stegen nedan:

1. Gå till [Azure Portal](https://portal.azure.com) och logga in med dina autentiseringsuppgifter.

2. Välj **Fler tjänster** och ange "Intune".

3. Välj **Intune App Protection**.

4. Välj **Hantering av mobilprogram i Intune &gt; Inställningar** för att öppna bladet **Alla inställningar**.

    ![Skärmbild av bladet Hantering av mobilprogram i Intune](../media/AppManagement/AzurePortal_MAM_Mainblade-2.png)

2.  På bladet **Alla inställningar** väljer du **Apprincip**. När du gör det öppnas bladet **Apprincip** där du kan skapa nya principer och redigera befintliga. Välj **Lägg till en princip**.

    ![Skärmbild av bladet Apprincip med menyalternativet Lägg till en princip markerat ](../media/AppManagement/AzurePortal_MAM_AddPolicy.png)

3.  Skriv ett namn för principen, lägg till en kort beskrivning och välj plattformstypen för att skapa en princip för iOS eller Android. Du kan skapa mer än en princip för varje plattform.

    ![Skärmbild av bladet Lägg till en princip](../media/AppManagement/AzurePortal_MAM_AddPolicy_only.png)

4.  Välj **Appar** för att öppna bladet **Appar** där en lista över tillgängliga appar visas. Välj en eller flera appar i listan som du vill associera med principen som du skapar. När du har valt apparna väljer du **Välj** längst ned på bladet **Appar** för att spara ditt val.

    > [!IMPORTANT]
    > Du måste välja minst en app för att skapa en princip.

5.  Öppna principinställningsbladet genom att välja **Konfigurera nödvändiga inställningar** på bladet **Lägg till en princip**.

    Det finns två typer av principinställningar, **Dataflytt** och **Åtkomst**.  Principer för dataflytt tillämpas när data flyttas till och från appar, medan åtkomstprinciper avgör hur slutanvändare får åtkomst till apparna i en arbetskontext.
    Du kan snabbt komma igång genom att använda principinställningarnas standardvärden. Du behöver inte göra några ändringar om standardvärdena uppfyller dina krav.

    > [!TIP]
    > Följande principinställningar används endast när du använder appar i arbetskontexten.  När slutanvändarna använder appen för att utföra personliga uppgifter påverkas de inte av dessa principer.

    ![Skärmbild av inställningsbladet tillsammans med bladet Lägg till en princip](../media/AppManagement/AzurePortal_MAM_PolicySettings.png)

6.  Spara konfigurationen genom att välja **OK**. Nu är du tillbaka i bladet **Lägg till en princip** . Skapa principen och spara inställningarna genom att välja **Skapa**.

    ![Skärmbild av bladet Lägg till en princip som visar att appar och inställningar har konfigurerats](../media/AppManagement/AzurePortal_MAM_CreatePolicy.png)

När du har skapat en princip genom att följa stegen i föregående procedur distribueras den inte till några användare. Information om hur du distribuerar en princip finns i avsnittet ”Distribuera en princip till användare” nedan.

> [!IMPORTANT]
> Om du skapar en appskyddsprincip för en app med hjälp av Intune-administratörskonsolen och en appskyddsprincip med hjälp av Azure-portalen prioriteras principen som du skapade med Azure-portalen. I Intune- eller Configuration Manager-konsolen rapporteras dock principinställningarna som skapats från Intune-administrationskonsolen. Exempel:
>
> -   Du har skapat en appskyddsprincip i Intune-administratörskonsolen som blockerar kopiering från en app.
> -   Du har skapat en appskyddsprincip i Azure-konsolen som tillåter kopiering från en app.
> -   Du associerar båda principerna med samma app.
> -   Den princip som du skapade från Azure-konsolen prioriteras och kopiering tillåts.
> -   Dock indikerar statusen och rapporterna i Intune-konsolen felaktigt att kopiering är blockerat.

## <a name="line-of-business-lob-apps-optional"></a>Branschspecifika appar (LOB) (valfritt)

Från och med Intune version 1703 kan du välja att allmänt lägga till branschspecifika appar i Intune när du skapar en ny appskyddsprincip. Det ger dig möjlighet att definiera appskyddsprinciper för LOB-appar med hjälp av MAM SDK utan att fullständiga appdistributionsbehörigheter krävs.
/intune/app-sdk-get-started
> [!TIP]
> Du kan också lägga till branschspecifika appar i Intune med hjälp av arbetsflödet för [Intune App SDK](/intune/app-sdk-get-started).

> [!IMPORTANT]
> Om användarna bara har specifik behörighet för distribution av MAM-appar och inte fullständiga appdistributionsbehörigheter, som skulle tillåta att de distribuerar valfria appar i Intune, kan de inte gå igenom arbetsflödet för Intune SDK, men de kan ändå lägga till sina branschspecifika appar via arbetsflödet för att skapa skyddsprinciper för MAM-appar.

### <a name="to-add-lob-apps-ios-and-android"></a>Lägga till branschspecifika appar (iOS och Android)

1.  På bladet Lägg till en princip väljer du Konfigurera **appar** för att öppna bladet Appar.

    ![MAM-bladet Lägg till en princip](../media/AppManagement/mam-lob-apps-1.png)

2.  Klicka på **Fler appar**, ange sedan **ID för programpaket** (för iOS), **Paket-ID** (för Android), och klicka sedan på Välj för att lägga till de branschspecifika apparna.

    ![MAM-bladet Fler appar](../media/AppManagement/mam-lob-apps-2.png)

### <a name="to-add-lob-apps-windows"></a>Lägga till branschspecifika appar (Windows)

> [!IMPORTANT]
> Du måste välja Windows 10 i listrutan för plattform när du skapar en ny appskyddsprincip.

1. På bladet Lägg till en princip väljer du **Tillåtna appar** eller **Undanta appar** för att öppna något av bladen för tillåtna eller undantagna appar.

   > [!NOTE]
   > 
   > - **Tillåtna appar**: detta är de appar som måste följa den här principen.
   > - **Undanta appar**: de här apparna är undantagna från denna princip och kan komma åt företagets data utan begränsningar.
   > <br></br>
2. Klicka på **Lägg till appar** på bladet för tillåtna eller undantagna appar. Du kan lägga till rekommenderade Microsoft-appar, butiks- eller skrivbordsappar.

    a.  **Rekommenderade appar:** en förifylld lista med appar (huvudsakligen för Office) som administratörer enkelt kan importera till principen.

    b.  **Store-appar:** administratören kan lägga till valfri app från Windows Store i principen.

    c.  **Windows-skrivbordsappar:** administratören kan lägga till valfria traditionella Windows-skrivbordsappar i principen (t.ex. exe, dll osv.)

## <a name="deploy-a-policy-to-users"></a>Distribuera en princip för användare

1.  På bladet **Princip** väljer du **Användargrupper**, vilket öppnar bladet **Användargrupper**. Öppna bladet **Lägg till användargrupp** genom att välja **Lägg till användargrupp** på bladet **Användargrupper**.

    ![Skärmbild av bladet Användargrupper med menyalternativet Lägg till användargrupp markerat](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  En lista med användargrupper visas i bladet **Lägg till användargrupp** . Det här är en lista över alla säkerhetsgrupper i **Azure Active Directory**. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj sedan **Välj**. När du väljer **Välj** distribueras principen till användarna.

    ![Skärmbild av bladet Lägg till användargrupp som visar listan med Azure Active Directory-användare](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    Nu har du skapat en princip och distribuerat den till användare.

Endast användare med tilldelade Intune-licenser påverkas av principen. Användare som ingår i den säkerhetsgrupp som du valde och som inte har tilldelats någon Intune-licens påverkas inte.

>[!IMPORTANT]
> Om du använder Intune med Configuration Manager för att hantera iOS- och Android-enheter tillämpas principen endast på användarna direkt i den grupp du valt. Medlemmar i underordnade grupper som är kapslade i den grupp som du har valt påverkas inte.

Slutanvändarna kan hämta apparna från App Store eller Google Play. Mer information finns i:
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](/intune/end-user-mam-apps-android)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](/intune/end-user-mam-apps-ios)

##  <a name="change-existing-policies"></a>Ändra befintliga principer
Du kan redigera en befintlig princip och tillämpa den på inriktade användare. När du ändrar befintliga principer ser dock inte användare som redan är inloggade i apparna ändringarna förrän efter åtta timmar.

Om användaren ska kunna se effekten av ändringarna direkt måste användaren logga ut ur appen och sedan logga in igen.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Ändra listan över appar som är associerade med principen

1.  Välj den princip som du vill ändra på bladet **Apprincip**. När du gör det öppnas ett blad som är specifikt för den princip du valt.

    ![Skärmbild av en befintlig princip som har öppnats på ett separat blad](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  Öppna listan med appar genom att välja **Målappar** på principbladet.

3.  Ta bort eller lägg till appar i listan och spara ändringarna genom att välja ikonen **Spara**.

### <a name="to-change-the-list-of-user-groups"></a>Ändra listan över användargrupper

1.  Välj den princip som du vill ändra på bladet **Apprincip**. När du gör det öppnas bladet som är specifikt för den princip du valt.

2.  Välj **Användargrupper** för att öppna bladet **Användargrupp** som innehåller en lista över aktuella användargrupper som omfattas av den här principen.

3.  Om du vill lägga till en ny användargrupp till principen väljer du **Lägg till användargrupp** och väljer användargruppen. Välj **Välj** om du vill distribuera principen till den grupp du valt.

    ![Skärmbild av bladet Lägg till användargrupp med två valda användargrupper](../media/AppManagement/AzurePortal_MAM_ChangePolicy_SelectUser.png)

4.  Om du vill ta bort en användargrupp markerar du den användargrupp som du vill ta bort. Sedan väljer du punkterna (...) och **Ta bort** för att ta bort användargruppen.

    ![Skärmbild som visar alternativet Ta bort ](../media/AppManagement/AzurePortal_MAM_ChangePolicy_DeleteUser.png)

### <a name="to-change-policy-settings"></a>Ändra principinställningar

1.  Välj den princip som du vill ändra på bladet **Apprincip**. När du gör det öppnas ett blad som är specifikt för den princip du valt.

    ![Skärmbild av en befintlig princip som har öppnats på ett separat blad ](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  Öppna bladet **Principinställningar** genom att välja **Principinställningar**.

3.  Ändra inställningarna och spara ändringarna genom att klicka på ikonen **Spara**.

    ![Skärmbild av bladet Principinställningar som visar menyalternativet Spara överst](../media/AppManagement/AzurePortal_MAM_ChangePolicy_ChangeSettings.png)

## <a name="policy-settings"></a>Principinställningar
Välj något av följande om du vill se en fullständig lista med principinställningar för iOS och Android:

> [!div class="op_single_selector"]
> - [iOS-principer](ios-mam-policy-settings.md)
> - [Android-principer](android-mam-policy-settings.md)

## <a name="next-steps"></a>Nästa steg
[Övervaka efterlevnad och användarstatus](monitor-mobile-app-management-policies-with-microsoft-intune.md)

### <a name="see-also"></a>Se även
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](/intune/end-user-mam-apps-android)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](/intune/end-user-mam-apps-ios)
