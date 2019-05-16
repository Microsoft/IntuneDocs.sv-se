---
title: Skapa och distribuera appskyddsprinciper
titleSuffix: Microsoft Intune
description: Det här ämnet beskriver hur du skapar och tilldelar Microsoft Intunes appskyddsprinciper.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7d7834719b42a1aaa6240510a951733a96f6add
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569798"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Hur du skapar och tilldelar skyddsprinciper för appar

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Lär dig hur du skapar och tilldelar skyddsprinciper för appar till dina användare i Microsoft Intune. Det här avsnittet beskriver också hur du ändrar befintliga principer.

## <a name="before-you-begin"></a>Innan du börjar

Appskyddsprinciper kan tillämpas på appar som körs på enheter som kan, men som inte nödvändigtvis, hanteras av Intune. En mer detaljerad beskrivning av hur appskyddsprinciper fungerar och scenarier som stöds av appskyddsprinciper i Intune finns i [Vad är appskyddsprinciper i Microsoft Intune?](app-protection-policy.md)

Om du söker efter en lista över appar med MAM-stöd, se [lista över MAM-appar](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Information om att lägga till organisationens affärsapplikationer i Microsoft Intune och förbereda för appskyddsprinciper finns i [Lägga till appar i Microsoft Intune](apps-add.md).

##  <a name="create-an-app-protection-policy"></a>Skapa en appskyddsprincip
1. I Intune-portalen går du till **klientappar** > **appskyddsprinciper**. Därmed öppnas **Principer för appskydd** där du kan skapa nya principer och redigera befintliga.
2. Välj **skapa princip**.

   ![Skärmbild av bladet Lägg till en princip](./media/app-protection-add-policy.png)

3. Ange ett namn för principen, lägg till en kort beskrivning och välj plattformstypen för principen. Du kan skapa mer än en princip för varje plattform.

4. Välj **Appar** för att öppna bladet **Appar** där en lista över tillgängliga appar visas. Välj en eller flera appar i listan som du vill associera med principen som du skapar. Välj minst en app för att skapa en princip.  

5. När du har valt apparna väljer du **Välj** för att spara ditt val.

6. I fönstret **Lägg till en princip** väljer du  **Konfigurera obligatoriska inställningar** för att öppna **Inställningar**.

   Det finns tre typer av principinställningar:
   - **Dataskydd** – Den här gruppen innehåller kontroller för dataförlustskydd, såsom begränsningar för klipp ut, kopiera, klistra in och spara som. De här inställningarna avgör hur användarna samverkar med data i apparna.
   - **Åtkomstbehörigheter** – Den här gruppen innehåller alternativ för PIN-kod per app som avgör hur slutanvändare får åtkomst till apparna i en arbetskontext.  
   - **Villkorlig start** – Den här gruppen innehåller inställningar som lägsta OS-inställningar, uppbrytning och identifiera rotade enheter och offlinerespittid.

   Du kan snabbt komma igång genom att använda principinställningarnas standardvärden. Du behöver inte göra några ändringar om standardvärdena uppfyller dina krav.

   > [!TIP]
   > Följande principinställningar används endast när du använder appar i arbetskontexten. När slutanvändarna använder appen för att utföra personliga uppgifter påverkas de inte av dessa principer. Observera att när du skapar en ny fil så betraktas den som en personlig fil. 

7. Spara konfigurationen genom att välja **OK**. Nu är du tillbaka på bladet **Lägg till en princip**.
8. Skapa principen och spara inställningarna genom att välja **Skapa**.

Nya principer som du skapar distribueras inte till alla användare förrän du uttryckligen gör det. Information om hur du distribuerar en princip finns i [Distribuera en princip till användare](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Distribuera en princip för användare

1. Välj en princip i fönstret **Principer för appskydd**.

2. I ***Intune-appskydd** väljer du **Tilldelningar** för att öppna fönstret **Intune-appskydd – Tilldelningar**. På fliken *Inkludera* väljer du **Välj grupper att inkludera**. 

   ![Skärmbild av fönstret Tilldelningar med menyn Välj grupper att ta med](./media/app-protection-policy-add-users.png)

3.  En lista över alla säkerhetsgrupper i **Azure Active Directory** visas. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj sedan **Välj**. 

    ![Skärmbild av fönstret Lägg till användargrupp med lista över Azure AD-användare](./media/azure-ad-user-group-list.png)

4.  När du har inkluderat och exkluderat grupper sparar du konfigurationen genom att välja **Spara** och distribuera principen till användarna. Om du väljer **Ignorera** innan du sparar konfigurationen ignoreras alla ändringar som du har gjort på flikarna *Inkludera* och *Exkludera*.   
 
     ![Skärmbild som visar alternativen för att spara och ta bort](./media/save-assignment.png)
  
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

1.  I fönstret **Appskyddsprinciper** väljer du den princip som du vill ändra.

2.  I fönstret *Intune-appskydd* väljer du **Målappar** för att öppna listan över appar.

3.  Ta bort eller lägg till appar i listan och spara ändringarna genom att välja ikonen **Spara**.

### <a name="to-change-the-list-of-user-groups"></a>Ändra listan över användargrupper


1.  I fönstret **Appskyddsprinciper** väljer du den princip som du vill ändra.

2.  I fönstret *Intune-appskydd* väljer du **Tilldelningar** för att öppna fönstret **Intune-appskydd – Tilldelningar** som visar en lista med aktuella användargrupper som har den här principen.

3.  Om du vill lägga till en ny användargrupp för principen väljer du **Välj grupper att ta med** på fliken *Inkludera* och sedan användargruppen. Lägg till gruppen genom att välja **Välj**. 

4.  Om du vill exkludera en användargrupp väljer du **Välj grupper att exkludera** på fliken *Exkludera* och väljer sedan användargruppen. Välj **Välj** för att ta bort användargruppen.  

5.  Om du vill ta bort grupper som har lagts till tidigare markerar du ellipsen (...) och väljer **Ta bort** på någon av flikarna *Inkludera* eller *Exkludera*. 

5.  När dina ändringar av tilldelningarna är klar sparar du konfigurationen genom att välja **Spara** och distribuerar principen till den nya uppsättningen användare. Om du väljer **Ignorera** innan du sparar konfigurationen ignoreras alla ändringar som du har gjort på flikarna *Inkludera* och *Exkludera*.

### <a name="to-change-policy-settings"></a>Ändra principinställningar

1.  I fönstret **Appskyddsprinciper** väljer du den princip som du vill ändra.

2.  I fönstret *Intune-appskydd* väljer du **Egenskaper** för att öppna listan över inställningsområden som du kan redigera. 

3.  Välj inställningsområde med de inställningar som du vill ändra såsom **Dataflytt** eller **Åtkomstbehörigheter**. Ändra inställningarna till nya värden.

4.  Välj ikonen **Spara** för att spara dina ändringar. Upprepa processen för att välja ett inställningsområde och ändra och spara sedan ändringarna, tills alla ändringar har slutförts. Därefter kan du stänga fönstret *Intune-appskydd – Egenskaper*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Ange mål för appskyddsprinciper utifrån enhetens hanteringsstatus
I många organisationer är det vanligt att tillåta användare att använda både enheter som hanteras av hantering av mobilenheter (MDM) i Intune, till exempel företagsägda enheter, och ohanterade enheter som endast är skyddade med Intune-appskyddsprinciper. Ohanterade enheter är ofta kända som BYOD-enheter (Bring Your Own Devices).

Eftersom Intune-appskyddsprinciper som är riktade till en användares identitet kan skyddsinställningarna för en användare gälla både för registrerade (MDM-hanterade) och icke-registrerade enheter (utan MDM). Därför kan du rikta en Intune-appskyddsprincip till antingen Intune-registrerade eller icke-registrerade iOS- och Android-enheter. Du kan ha en skyddsprincip för ohanterade enheter där ett strikt dataförlustskydd (DLP) används och en separat skyddsprincip för MDM-hanterade enheter, där du kan använda lite mindre strikta DLP-kontroller. 

För att skapa de här principerna bläddrar du till **Klientappar** > **Appskyddsprinciper** i Intune-konsolen och välj **Skapa princip**. Du kan även redigera eller en befintlig princip. För att appskyddsprincipen ska gälla för både hanterade och ohanterade enheter bekräftar du att inställningen **Target to all app types** (Gäller för alla apptyper) är inställd på standardvärdet **Ja**. Om du vill tilldela detaljerade inställningar baserat på hanteringstillståndet ställer du in **Gäller för alla apptyper** till **Nej**. 

![Skärmbild av bladet Lägg till en princip med alternativet Rikta till alla typer av appar](./media/app-protection-policies-target-all.png)

För iOS-krävs ytterligare appkonfigurationsinställningar för att rikta in appinställningar till appar på Intune-registrerade enheter:
- **IntuneMAMUPN** måste konfigureras för alla MDM-hanterade program. Mer information finns i [Hantera dataöverföring mellan iOS-appar med Microsoft Intune](https://docs.microsoft.com/intune/data-transfer-between-apps-manage-ios#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** måste konfigureras för alla tredje parters LOB MDM-hanterade program. **IntuneMAMDeviceID** ska konfigureras till enhetens ID-token. Till exempel `key=IntuneMAMDeviceID, value={{deviceID}}`. Mer information finns i [Lägg till appkonfigurationsprinciper för hanterade iOS-enheter](https://docs.microsoft.com/intune/app-configuration-policies-use-ios).
- Om bara **IntuneMAMDeviceID** är konfigurerat kan Intune App betrakta enheten som ohanterad.  

> [!NOTE]
> Läs [MAM protection policies targeted based on management state](whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-) (MAM-skyddsprinciper som riktas baserat på hanteringstillstånd) för att få specifik information om iOS-stöd och appskyddsprinciper som baseras på hanteringstillstånd.

## <a name="policy-settings"></a>Principinställningar
Välj någon av följande länkar om du vill se en fullständig lista med principinställningar för iOS och Android:

- [iOS-principer](app-protection-policy-settings-ios.md)
- [Android-principer](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Nästa steg
[Övervaka efterlevnad och användarstatus](app-protection-policies-monitor.md)

### <a name="see-also"></a>Se även
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-apps-android.md)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-apps-ios.md)
