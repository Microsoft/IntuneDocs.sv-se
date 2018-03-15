---
title: Skapa och distribuera appskyddsprinciper
titleSuffix: Microsoft Intune
description: "Lär dig hur du skapar och tilldelar skyddsprinciper för appar i Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c7ad60a27e32aaab49e77789364aecdc5ea7fc60
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Hur du skapar och tilldelar skyddsprinciper för appar

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Lär dig hur du skapar och tilldelar skyddsprinciper för appar till dina användare i Microsoft Intune. Det här avsnittet beskriver också hur du ändrar befintliga principer.

## <a name="before-you-begin"></a>Innan du börjar

Anvisningar i den klassiska Intune-portalen finns i [Så här skapar du programskyddsprinciper](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune).

Appskyddsprinciper kan tillämpas på appar som körs på enheter som kan, men som inte nödvändigtvis, hanteras av Intune. En mer detaljerad beskrivning av hur appskyddsprinciper fungerar och scenarier som stöds av appskyddsprinciper i Intune finns i [Vad är appskyddsprinciper i Microsoft Intune](app-protection-policy.md).

Om du söker efter en lista över appar med MAM-stöd, se [lista över MAM-appar](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

##  <a name="create-an-app-protection-policy"></a>Skapa en appskyddsprincip
1.  Välj **Principer för appskydd** i **Hantera** i arbetsbelastningen **Mobilappar**. Därmed öppnas **Principer för appskydd** där du kan skapa nya principer och redigera befintliga.
2. Välj **Lägg till en princip**.

  ![Skärmbild av bladet Lägg till en princip](./media/app-protection-add-policy.png)

3.  Skriv ett namn för principen, lägg till en kort beskrivning och välj plattformstypen för principen. Du kan skapa mer än en princip för varje plattform, om det behövs.

4.  Välj **Appar** för att öppna bladet **Appar** där en lista över tillgängliga appar visas. Välj en eller flera appar i listan som du vill associera med principen som du skapar.
5. När du har valt apparna väljer du **Välj** för att spara ditt val.

    > [!IMPORTANT]
    > Du måste välja minst en app för att skapa en princip.

6.  Välj **Konfigurera obligatoriska inställningar** på bladet **Lägg till en princip** för att öppna **Inställningar**.

    Det finns två typer av principinställningar, **Dataflytt** och **Åtkomst**.  Principer för dataflytt tillämpas för data som flyttas in och ut ur appar. Åtkomstprinciper avgör hur slutanvändare får åtkomst till apparna i en arbetskontext.
    Du kan snabbt komma igång genom att använda principinställningarnas standardvärden. Du behöver inte göra några ändringar om standardvärdena uppfyller dina krav.

    > [!TIP]
    > Följande principinställningar används endast när du använder appar i arbetskontexten. När slutanvändarna använder appen för att utföra personliga uppgifter påverkas de inte av dessa principer.

7.  Spara konfigurationen genom att välja **OK**. Nu är du tillbaka i fönstret **Lägg till en princip** . Skapa principen och spara inställningarna genom att välja **Skapa**.
8. Spara konfigurationen genom att välja **OK**. Nu är du tillbaka på bladet **Lägg till en princip**.
9. Skapa principen och spara inställningarna genom att välja **Skapa**.

När du har skapat en princip genom att följa stegen i föregående procedur distribueras den inte till några användare. Information om hur du distribuerar en princip finns i [Distribuera en princip till användare](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Distribuera en princip för användare


1. Välj en princip i fönstret **Principer för appskydd**.

1. I fönstret **Princip** väljer du **Tilldelningar** så att fönstret **Intune-appskydd – Tilldelningar** öppnas. Välj **Välj grupper att ta med** i fönstret **Tilldelningar** så att fönstret **Välj grupper att ta med** öppnas.

   ![Skärmbild av fönstret Tilldelningar med menyalternativet Välj grupper att ta med markerat](./media/app-protection-policy-add-users.png)

2.  En lista med användargrupper visas i fönstret **Lägg till användargrupp** . Den här listan visar alla säkerhetsgrupper i **Azure Active Directory**. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj sedan **Välj**. När du väljer **Välj** distribueras principen till användarna.

    ![Skärmbild av fönstret Lägg till användargrupp som visar listan med Azure Active Directory-användare](./media/azure-ad-user-group-list.png)

Nu har du skapat en princip och distribuerat den till användare.

Endast användare med tilldelade Microsoft Intune-licenser påverkas av principen. De användare i den valda säkerhetsgruppen som inte har en tilldelad Intune-licens påverkas inte.

>[!IMPORTANT]
> Om du använder Intune med Configuration Manager för att hantera enheter tillämpas principen endast på användarna direkt i den grupp du valt. Medlemmar i underordnade grupper som är kapslade i den grupp som du har valt påverkas inte.

Slutanvändarna kan hämta apparna från App Store eller Google Play. Mer information finns i:
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-apps-android.md)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>Ändra befintliga principer
Du kan redigera en befintlig princip och tillämpa den på inriktade användare. När du ändrar befintliga principer ser dock inte användare som redan är inloggade i apparna ändringarna förrän efter åtta timmar.

För att kunna se effekten av ändringarna direkt måste slutanvändaren logga ut ur appen och sedan logga in igen.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Ändra listan över appar som är associerade med principen

1.  I fönstret **Principer för appskydd** väljer du den princip som du vill ändra. Därmed öppnas ett fönster som är specifikt för den princip som du precis valde.

2.  I principfönstret väljer du **Målappar** för att öppna listan med appar.

3.  Ta bort eller lägg till appar i listan och spara ändringarna genom att välja ikonen **Spara**.

### <a name="to-change-the-list-of-user-groups"></a>Ändra listan över användargrupper


1.  I fönstret **Principer för appskydd** väljer du den princip som du vill ändra. Därmed öppnas ett fönster som är specifikt för den princip som du valde.

2.  I principfönstret väljer du **Tilldelningar** för att öppna fönstret **Intune-appskydd – Tilldelningar** som visar en lista med aktuella användargrupper som har den här principen.

3.  Om du vill lägga till en ny användargrupp för principen väljer du **Välj grupper att ta med** på fliken **Inkludera** och sedan användargruppen. Välj **Välj** om du vill distribuera principen till den grupp du valt.

4.  Om du vill ta bort en användargrupp väljer du **Välj grupper att utesluta** på fliken **Undanta** och sedan användargruppen. Välj **Välj** för att ta bort användargruppen.

### <a name="to-change-policy-settings"></a>Ändra principinställningar

1.  I fönstret **Principer för appskydd** väljer du den princip som du vill ändra. Därmed öppnas ett fönster som är specifikt för den princip som du precis valde.

2.  Välj **Principinställningar** så att fönstret **Principinställningar** öppnas.

3.  Ändra inställningarna och spara ändringarna genom att klicka på ikonen **Spara**.

## <a name="policy-settings"></a>Principinställningar
Välj någon av följande länkar om du vill se en fullständig lista med principinställningar för iOS och Android:

- [iOS-principer](app-protection-policy-settings-ios.md)
- [Android-principer](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Nästa steg
[Övervaka efterlevnad och användarstatus](app-protection-policies-monitor.md)

### <a name="see-also"></a>Se även
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-apps-android.md)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-apps-ios.md)
