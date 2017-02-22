---
title: "Skapa och distribuera appskyddsprinciper | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Se hur Intunes skyddsprinciper för appar kan hjälpa dig att skydda företagets data som används av appar som du hanterar."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 424fae862592c1ab5b4221fb5ad40a52c39f6760
ms.openlocfilehash: 5112c6641577f3faefb85650dd06bd1634542019

---

# <a name="how-to-create-and-assign-app-protection-policies"></a>Hur du skapar och tilldelar skyddsprinciper för appar

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

**Om du inte är i Intune-tjänsten i förhandsversionen av Azure-portalen**, förklarar det här avsnittet [hur du skapar app-principer](https://docs.microsoft.com/en-us/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) i den klassiska Intune-konsolen.

Appskyddsprinciper kan tillämpas på appar som körs på enheter som kan, men som inte nödvändigtvis, hanteras av Intune. En mer detaljerad beskrivning av hur appskyddsprinciper fungerar och scenarier som stöds av appskyddsprinciper i Intune finns i [Vad är appskyddsprinciper i Microsoft Intune](what-is-app-protection-policy.md).

##  <a name="create-an-app-protection-policy"></a>Skapa en appskyddsprincip
1.  I arbetsbelastningen **Hantera appar** väljer du **Hantera** > **Appskyddsprinciper**.

2.  När du gör det öppnas bladet **Appskyddsprinciper** där du kan skapa nya principer och redigera befintliga. Välj **Lägg till en princip**.

  ![Skärmbild av bladet Lägg till en princip](../media/app-protection-add-policy.png)

3.  Skriv ett namn för principen, lägg till en kort beskrivning och välj plattformstypen för att skapa en princip för iOS eller Android. Du kan skapa mer än en princip för varje plattform.

4.  Välj **Appar** för att öppna bladet **Appar** där en lista över tillgängliga appar visas. Välj en eller flera appar i listan som du vill associera med principen som du skapar. När du har valt apparna väljer du **Välj** längst ned på bladet **Appar** för att spara ditt val.

    > [!IMPORTANT]
    > Du måste välja minst en app för att skapa en princip.

5.  Öppna principinställningsbladet genom att välja **Konfigurera nödvändiga inställningar** på bladet **Lägg till en princip**.

    Det finns två typer av principinställningar, **Dataflytt** och **Åtkomst**.  Principer för dataflytt tillämpas när data flyttas till och från appar, medan åtkomstprinciper avgör hur slutanvändare får åtkomst till apparna i en arbetskontext.
    Du kan snabbt komma igång genom att använda principinställningarnas standardvärden. Du behöver inte göra några ändringar om standardvärdena uppfyller dina krav.

    > [!TIP]
    > Följande principinställningar används endast när du använder appar i arbetskontexten.  När slutanvändarna använder appen för att utföra personliga uppgifter påverkas de inte av dessa principer.



6.  Spara konfigurationen genom att välja **OK**. Nu är du tillbaka i bladet **Lägg till en princip** . Skapa principen och spara inställningarna genom att välja **Skapa**.


När du har skapat en princip genom att följa stegen i föregående procedur distribueras den inte till några användare. Information om hur du distribuerar en princip finns i avsnittet ”Distribuera en princip till användare” nedan.

## <a name="deploy-a-policy-to-users"></a>Distribuera en princip för användare

1.  På bladet **Princip** väljer du **Användargrupper**, vilket öppnar bladet **Användargrupper**. Öppna bladet **Lägg till användargrupp** genom att välja **Lägg till användargrupp** på bladet **Användargrupper**.

  ![Skärmbild av bladet Användargrupper med menyalternativet Lägg till användargrupp markerat](../media/app-protection-policy-add-users.png)

2.  En lista med användargrupper visas i bladet **Lägg till användargrupp** . Det här är en lista över alla säkerhetsgrupper i **Azure Active Directory**. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj sedan **Välj**. När du väljer **Välj** distribueras principen till användarna.
  ![Skärmbild av bladet Lägg till användargrupp som visar listan med Azure Active Directory-användare](../media/azure-ad-user-group-list.png)

Nu har du skapat en princip och distribuerat den till användare.

Endast användare med tilldelade Microsoft Intune-licenser påverkas av principen. Användare som ingår i säkerhetsgruppen som du valde och som inte har tilldelats någon Microsoft Intune-licens påverkas inte.

>[!IMPORTANT]
> Om du använder Intune med Configuration Manager för att hantera iOS- och Android-enheter tillämpas principen endast på användarna direkt i den grupp du valt. Medlemmar i underordnade grupper som är kapslade i den grupp som du har valt påverkas inte.

Slutanvändarna kan hämta apparna från App Store eller Google Play. Mer information finns i:
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-android-apps.md)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-ios-apps.md)

##  <a name="change-existing-policies"></a>Ändra befintliga principer
Du kan redigera en befintlig princip och tillämpa den på inriktade användare. När du ändrar befintliga principer ser dock inte användare som redan är inloggade i apparna ändringarna förrän efter åtta timmar.

Om användaren ska kunna se effekten av ändringarna direkt måste användaren logga ut ur appen och sedan logga in igen.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Ändra listan över appar som är associerade med principen

1.  Välj den princip som du vill ändra på bladet **Apprincip**. När du gör det öppnas ett blad som är specifikt för den princip du valt.

2.  Öppna listan med appar genom att välja **Målappar** på principbladet.

3.  Ta bort eller lägg till appar i listan och spara ändringarna genom att välja ikonen **Spara**.

### <a name="to-change-the-list-of-user-groups"></a>Ändra listan över användargrupper

1.  Välj den princip som du vill ändra på bladet **Apprincip**. När du gör det öppnas bladet som är specifikt för den princip du valt.

2.  Välj **Användargrupper** för att öppna bladet **Användargrupp** som innehåller en lista över aktuella användargrupper som omfattas av den här principen.

3.  Om du vill lägga till en ny användargrupp till principen väljer du **Lägg till användargrupp** och väljer användargruppen. Välj **Välj** om du vill distribuera principen till den grupp du valt.

4.  Om du vill ta bort en användargrupp markerar du den användargrupp som du vill ta bort. Sedan väljer du punkterna (...) och **Ta bort** för att ta bort användargruppen.
  ![Skärmbild som visar alternativet Ta bort](../media/app-protection-policy-delete-user.png)

### <a name="to-change-policy-settings"></a>Ändra principinställningar

1.  Välj den princip som du vill ändra på bladet **Apprincip**. När du gör det öppnas ett blad som är specifikt för den princip du valt.


2.  Öppna bladet **Principinställningar** genom att välja **Principinställningar**.

3.  Ändra inställningarna och spara ändringarna genom att klicka på ikonen **Spara**.

## <a name="policy-settings"></a>Principinställningar
Välj något av följande om du vill se en fullständig lista med principinställningar för iOS och Android:

> [!div class="op_single_selector"]
- [iOS-principer](ios-app-protection-policy-settings.md)
- [Android-principer](android-app-protection-policy-settings.md)

## <a name="next-steps"></a>Nästa steg
[Övervaka efterlevnad och användarstatus](monitor-app-protection-policies-with-microsoft-intune.md)

### <a name="see-also"></a>Se även
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-android-apps.md)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-ios-apps.md)



<!--HONumber=Feb17_HO1-->


