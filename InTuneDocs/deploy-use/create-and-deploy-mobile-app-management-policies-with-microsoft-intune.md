---
title: Skapa och distribuera MAM-principer | Microsoft Docs
description: "Följ instruktionerna i det här avsnittet om du vill skapa och distribuera hanteringsprinciper för mobilappar."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9e208608d50c9b5f7fe66743de0d3c7e741dbfbd
ms.openlocfilehash: 3e077bfa8a03526b9472b4e9fdd4a75da22c28c8


---

# <a name="create-and-deploy-mobile-app-management-policies-with-microsoft-intune"></a>Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Hanteringsprinciper för mobilappar (MAM) kan tillämpas på appar som körs på enheter som kan, men som inte måste, hanteras av Intune. En detaljerad beskrivning av hur MAM-principer fungerar och de scenarier som stöds av Intunes MAM-principer finns i [Skydda appdata med hanteringsprinciper för mobilappar](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

Det här avsnittet beskriver processen för att skapa en MAM-princip i **Azure Portal**. Azure Portal är en ny administratörskonsol som används för att skapa MAM-principer och vi rekommenderar att du använder den här portalen när MAM-principerna skapas. Azure Portal har stöd för följande MAM-scenarier:
- Enheter som har registrerats i Intune.
- Enheter som hanteras av en MDM-lösning från tredje part.
- Enheter som inte hanteras av någon MDM-lösning (BYOD).

>[!IMPORTANT]
Tänk på följande om du hanterar dina enheter med **Intune-administratörskonsolen**:

> * Du kan skapa en MAM-princip som stöder appar för enheter som registrerats i Intune med hjälp av [Intune-administratörskonsolen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).
> * MAM-principer som skapas i Intune-administratörskonsolen kan inte importeras till Azure Portal.  MAM-principer måste återskapas i Azure Portal.

> * Du kanske inte kan se alla MAM-principinställningar i Intune-administratörskonsolen. Azure Portal är den nya administratörskonsolen för att skapa MAM-principer.

> * För att kunna distribuera hanterade appar måste du skapa en MAM-princip i Intune-administratörskonsolen. Du kanske vill skapa MAM-principer i både Intune-administratörskonsolen och på Azure Portal: I Intune-administratörskonsolen så att du kan distribuera hanterade appar och på Azure Portal eftersom det är den nya administratörskonsolen där alla MAM-principinställningar finns.

> * Om du skapar MAM-principer i både Intune-administratörskonsolen och i Azure Portal tillämpas de principer som skapas i Azure Portal för apparna.

Om du vill se en lista över principinställningar som stöds för Android- och iOS-plattformar kan du välja något av följande:

> [!div class="op_single_selector"]
- [iOS-principer](ios-mam-policy-settings.md)
- [Android-principer](android-mam-policy-settings.md)

##  <a name="create-a-mam-policy"></a>Skapa en MAM-princip
Innan du skapar en MAM-princip granskar du informationen om [krav och support](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md).
1.  Välj **Hantering av mobilprogram i Intune &gt; Inställningar** för att öppna bladet **Inställningar**.

    ![Skärmbild av bladet Hantering av mobilprogram i Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Om det är första gången du använder Azure Portal läser du först [Azure Portal för Microsoft Intune MAM-principer](azure-portal-for-microsoft-intune-mam-policies.md) för att bekanta dig med portalen.

2.  På bladet **Inställningar** väljer du **Apprincip**. När du gör det öppnas bladet **Apprincip** där du kan skapa nya principer och redigera befintliga. Välj **Lägg till en princip**.

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
> Om du skapar en MAM-princip för en app med Intune-administratörskonsolen och MAM-principen med Azure Portal har principen som du skapade med Azure Portal företräde. I Intune- eller Configuration Manager-konsolen rapporteras dock principinställningarna som skapats från Intune-administrationskonsolen. Exempel:
>
> -   Du har skapat en MAM-princip i Intune-administrationskonsolen som blockerar kopiering från en app.
> -   Du har skapat en MAM-princip i Azure-konsolen som tillåter kopiering från en app.
> -   Du associerar båda principerna med samma app.
> -   Den princip som du skapade från Azure-konsolen prioriteras och kopiering tillåts.
> -   Dock indikerar statusen och rapporterna i Intune-konsolen felaktigt att kopiering är blockerat.

## <a name="deploy-a-policy-to-users"></a>Distribuera en princip för användare

1.  På bladet **Princip** väljer du **Användargrupper**, vilket öppnar bladet **Användargrupper**. Öppna bladet **Lägg till användargrupp** genom att välja **Lägg till användargrupp** på bladet **Användargrupper**.

    ![Skärmbild av bladet Användargrupper med menyalternativet Lägg till användargrupp markerat](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  En lista med användargrupper visas i bladet **Lägg till användargrupp** . Det här är en lista över alla säkerhetsgrupper i **Azure Active Directory**. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj sedan **Välj**. När du väljer **Välj** distribueras principen till användarna.

    ![Skärmbild av bladet Lägg till användargrupp som visar listan med Azure Active Directory-användare](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    Nu har du skapat en princip och distribuerat den till användare.

Endast användare med tilldelade [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licenser påverkas av principen. Användare som ingår i säkerhetsgruppen som du valde och som inte har tilldelats någon [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-licens påverkas inte.

>[!IMPORTANT]
> Om du använder Intune med Configuration Manager för att hantera iOS- och Android-enheter tillämpas principen endast på användarna direkt i den grupp du valt. Medlemmar i underordnade grupper som är kapslade i den grupp som du har valt påverkas inte.

Slutanvändarna kan hämta apparna från App Store eller Google Play. Mer information finns i:
* [Vad som händer när din Android-app hanteras med MAM-principer](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [Vad som händer när din iOS-app hanteras med MAM-principer](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

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
- [iOS-principer](ios-mam-policy-settings.md)
- [Android-principer](android-mam-policy-settings.md)

## <a name="next-steps"></a>Nästa steg
[Övervaka efterlevnad och användarstatus](monitor-mobile-app-management-policies-with-microsoft-intune.md)

### <a name="see-also"></a>Se även
* [Vad som händer när din Android-app hanteras med MAM-principer](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [Vad som händer när din iOS-app hanteras med MAM-principer](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


