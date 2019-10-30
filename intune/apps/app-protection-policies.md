---
title: Skapa och distribuera appskyddsprinciper
titleSuffix: Microsoft Intune
description: Det här ämnet beskriver hur du skapar och tilldelar Microsoft Intunes appskyddsprinciper.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8e105dae43c4e7139c8e44a8c6535baebe31cc4
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585477"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Hur du skapar och tilldelar skyddsprinciper för appar

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Lär dig hur du skapar och tilldelar Microsoft Intune-appskyddsprinciper (APP) för användare i din organisation. Det här avsnittet beskriver också hur du ändrar befintliga principer.

## <a name="before-you-begin"></a>Innan du börjar

Appskyddsprinciper kan tillämpas på appar som körs på enheter som kan, men som inte nödvändigtvis, hanteras av Intune. En mer detaljerad beskrivning av hur appskyddsprinciper fungerar och scenarier som stöds av appskyddsprinciper i Intune finns i [Vad är appskyddsprinciper i Microsoft Intune?](app-protection-policy.md)

Om du söker efter en lista över appar med MAM-stöd, se [lista över MAM-appar](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Information om att lägga till organisationens affärsapplikationer i Microsoft Intune och förbereda för appskyddsprinciper finns i [Lägga till appar i Microsoft Intune](apps-add.md).

För närvarande skiljer sig processflödet för skapande av en appskyddsprincip baserat på plattform:
- Appskyddsprinciper för iOS/iPadOS-appar och Android-appar
- Appskyddsprinciper för Windows 10-appar

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>Appskyddsprinciper för iOS/iPadOS-appar och Android-appar

När du skapar en appskyddsprincip för iOS/iPad-appar och Android-appar följer du ett modernt Intune-processflöde som resulterar i en ny appskyddsprincip.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>Skapa en appskyddsprincip för iOS/iPadOS eller Android
1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. I Intune-portalen väljer du **Klientappar** > **Appskyddsprinciper**. Därmed öppnas **Principer för appskydd** där du kan skapa nya principer och redigera befintliga.
3. Välj **Skapa princip** och välj antingen **iOS/iPadOS** eller **Android**. Bladet **Skapa princip** visas.
4. På sidan **Grundläggande** lägger du till följande värden:

    | Värde | Beskrivning |
    |--------------|------------------------------------------------|
    | Namn | Namnet på den här appskyddsprincipen. |
    | Beskrivning | [Valfritt] Beskrivningen av den här appskyddsprincipen. |


    Värdet för **Plattform** anges baserat på ditt val ovan.

    ![Skärmbild av sidan Grundläggande på bladet Skapa princip](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. Klicka på **Nästa** för att visa sidan **Appar**.<br>
    På sidan **Appar** kan du välja hur du vill tillämpa den här principen på appar på olika enheter. Du måste lägga till minst en app.<p>
    
    | Värde/alternativ | Beskrivning |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Rikta till appar på alla enhetstyper | Använd det här alternativet om du vill att principen ska riktas mot appar på enheter i valfritt hanteringstillstånd. Välj **Nej** om du vill rikta till appar på specifika enhetstyper. |
    |     Enhetstyper | Använd det här alternativet för att ange huruvida den här principen gäller för MDM-hanterade enheter eller ohanterade enheter. För iOS APP-principer väljer du från **Ohanterade** och **Hanterade** enheter. För Android APP-principer väljer du från **Ohanterade**, **Android-enhetsadministratör** och **Android Enterprise**.  |
    | Offentliga appar | Klicka på **Välj offentliga appar** för att välja de appar som ska vara mål. |
    | Anpassade appar | Klicka på **Välj anpassade appar** för att välja anpassade appar som mål baserat på ett paket-ID. |
    
    Den app eller de appar som du har valt visas i listan över offentliga och anpassade appar. 
6. Klicka på **Nästa** för att visa sidan **Dataskydd**.<br>
    Den här sidan innehåller inställningar för DLP-kontroller (dataförlustskydd), däribland begränsningar för att klippa ut, kopiera, klistra in och spara som. De här inställningarna avgör hur användarna interagerar med data i de appar som den här appskyddsprincipen gäller för.

    **Inställningar för dataskydd**:<br>
    - **Dataskydd för iOS/iPadOS** – mer information finns i [Inställningar för iOS-appskyddsprincip – dataskydd](~/apps/app-protection-policy-settings-ios.md#data-protection).
    - **Dataskydd för Android** – mer information finns i [Inställningar för Android-appskyddsprincip – dataskydd](~/apps/app-protection-policy-settings-android.md#data-protection).

7. Klicka på **Nästa** för att visa sidan **Åtkomstkrav**.<br>
    Den här sidan innehåller inställningar som gör att du kan konfigurera de krav för PIN-kod och autentiseringsuppgifter som användarna måste uppfylla för att få åtkomst till appar i en arbetskontext. 
 
    **Inställningar för åtkomstkrav**:<br>
    - **Åtkomstkrav för iOS/iPadOS** – mer information finns i [Inställningar för iOS-appskyddsprincip – åtkomstkrav](~/apps/app-protection-policy-settings-ios.md#access-requirements).
    - **Åtkomstkrav för Android** – mer information finns i [Inställningar för Android-appskyddsprincip – åtkomstkrav](~/apps/app-protection-policy-settings-android.md#access-requirements).

8. Klicka på **Nästa** för att visa sidan **Villkorsstyrd start**.<br>
    Den här sidan innehåller inställningar med vilka du anger krav för inloggningssäkerhet för din appskyddsprincip. Välj en **inställning** och ange det **värde** som användare måste uppfylla för att logga in på företagsappen. Välj sedan den **Åtgärd** som du vill vidta om användarna inte uppfyller dina krav. I vissa fall kan flera åtgärder konfigureras för en och samma inställning.

    **Inställningar för villkorsstyrd start**:<br>
    - **Villkorsstyrd start för iOS/iPadOS** – mer information finns i [Inställningar för iOS-appskyddsprincip – villkorsstyrd start](~/apps/app-protection-policy-settings-ios.md#conditional-launch).
    - **Villkorsstyrd start för Android** – mer information finns i [Inställningar för Android-appskyddsprincip – villkorsstyrd start](~/apps/app-protection-policy-settings-android.md#conditional-launch).

7. Klicka på **Nästa** för att visa sidan **Tilldelningar**.<br>
   På sidan **Tilldelningar** kan du tilldela appskyddsprincipen till grupper av användare. 
8. Klicka på **Nästa: Granska och skapa** för att granska de värden och inställningar som du angav för den här appskyddsprincipen.
9. När du är klar klickar du på **Skapa** för att skapa appskyddsprincipen i Intune. 

## <a name="app-protection-policies-for-windows-10-apps"></a>Appskyddsprinciper för Windows 10-appar

När du skapar en appskyddsprincip för Windows 10-appar kommer du att följa ett klassiskt Intune-processflöde.

### <a name="create-a-windows-10-app-protection-policy"></a>Skapa en Windows 10-appskyddsprincip
1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. I Intune-portalen väljer du **Klientappar** > **Appskyddsprinciper**. Därmed öppnas **Principer för appskydd** där du kan skapa nya principer och redigera befintliga.
3. Välj **Skapa princip**.

    <img alt="Screenshot of the 'Create policy' blade for Windows 10" src="~/apps/media/app-protection-policies/app-protection-add-policy.png" width="350">

4. Ange ett namn för principen, lägg till en kort beskrivning och välj plattformstypen för principen. Du kan skapa mer än en princip för varje plattform.

4. Du kan välja att **Rikta mot alla typer av appar**. Med det här alternativet kan du rikta principen mot appar på enheter i valfritt hanteringstillstånd. Vid lösning av principkonflikt ersätts den här inställningen om en användare har en princip som är mål för ett specifikt hanteringstillstånd. Mer information finns i [Target app protection policies based on device management state](~/apps/app-protection-policies.md#target-app-protection-policies-based-on-device-management-state) (Ange mål för appskyddsprinciper utifrån enhetens hanteringsstatus).

5. Välj **Appar** för att öppna bladet **Appar** där en lista över tillgängliga appar visas. Välj en eller flera appar i listan som du vill associera med principen som du skapar. Välj minst en app för att skapa en princip.  

6. När du har valt apparna väljer du **Välj** för att spara ditt val.

7. I fönstret **Lägg till en princip** väljer du  **Konfigurera obligatoriska inställningar** för att öppna **Inställningar**.

   Det finns tre typer av principinställningar:
   - **Dataskydd** – Den här gruppen innehåller kontroller för dataförlustskydd, såsom begränsningar för klipp ut, kopiera, klistra in och spara som. De här inställningarna avgör hur användarna samverkar med data i apparna.
   - **Åtkomstbehörigheter** – Den här gruppen innehåller alternativ för PIN-kod per app som avgör hur slutanvändare får åtkomst till apparna i en arbetskontext.  
   - **Villkorlig start** – Den här gruppen innehåller inställningar som lägsta OS-inställningar, uppbrytning och identifiera rotade enheter och offlinerespittid.

   Du kan snabbt komma igång genom att använda principinställningarnas standardvärden. Du behöver inte göra några ändringar om standardvärdena uppfyller dina krav.

   > [!TIP]
   > Följande principinställningar används endast när du använder appar i arbetskontexten. När slutanvändarna använder appen för att utföra personliga uppgifter påverkas de inte av dessa principer. Observera att när du skapar en ny fil så betraktas den som en personlig fil. 

8. Spara konfigurationen genom att välja **OK**. Nu är du tillbaka på bladet **Lägg till en princip**.
9. Skapa principen och spara inställningarna genom att välja **Skapa**.

Nya Windows 10-principer som du skapar tilldelas inte till användare förrän du uttryckligen gör det. Information om hur du tilldelar en Windows 10-princip finns i [Tilldela en Windows 10-princip till användare](~/apps/app-protection-policies.md#assign-a-windows-10-policy-to-users)

### <a name="assign-a-windows-10-policy-to-users"></a>Tilldela en Windows 10-princip till användare 

1. Välj en princip i fönstret **Principer för appskydd**.

2. I ***Intune-appskydd** väljer du **Tilldelningar** för att öppna fönstret **Intune-appskydd – Tilldelningar**. På fliken *Inkludera* väljer du **Välj grupper att inkludera**. 

   ![Skärmbild av fönstret Tilldelningar med menyn Välj grupper att ta med](./media/app-protection-policies/app-protection-policy-add-users.png)

3. En lista över alla säkerhetsgrupper i **Azure Active Directory** visas. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj sedan **Välj**. 

    ![Skärmbild av fönstret Lägg till användargrupp med lista över Azure AD-användare](./media/app-protection-policies/azure-ad-user-group-list.png)

4. När du har inkluderat och exkluderat grupper sparar du konfigurationen genom att välja **Spara** och distribuera principen till användarna. Om du väljer **Ignorera** innan du sparar konfigurationen ignoreras alla ändringar som du har gjort på flikarna *Inkludera* och *Exkludera*.   
 
     ![Skärmbild som visar alternativen för att spara och ta bort](./media/app-protection-policies/save-assignment.png)
  
Nu har du skapat en princip och distribuerat den till användare.

Endast användare med tilldelade Microsoft Intune-licenser påverkas av principen. De användare i den valda säkerhetsgruppen som inte har en tilldelad Intune-licens påverkas inte.

>[!IMPORTANT]
> Om du använder Intune med Configuration Manager för att hantera enheter tillämpas principen endast på användarna direkt i den grupp du valt. Medlemmar i underordnade grupper som är kapslade i den grupp som du har valt påverkas inte.

Slutanvändarna kan hämta apparna från App Store eller Google Play. Mer information finns i:
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-android.md)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-ios.md)

### <a name="change-existing-windows-10-policies"></a>Ändra befintliga Windows 10-principer
Du kan redigera en befintlig princip och tillämpa den på inriktade användare. När du ändrar befintliga principer ser dock inte användare som redan är inloggade i apparna ändringarna förrän efter åtta timmar.

För att kunna se effekten av ändringarna direkt måste slutanvändaren logga ut ur appen och sedan logga in igen.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Ändra listan över appar som är associerade med principen

1. I fönstret **Appskyddsprinciper** väljer du den princip som du vill ändra.

2. I fönstret *Intune-appskydd* väljer du **Målappar** för att öppna listan över appar.

3. Ta bort eller lägg till appar i listan och spara ändringarna genom att välja ikonen **Spara**.

#### <a name="to-change-the-list-of-user-groups"></a>Ändra listan över användargrupper

1. I fönstret **Appskyddsprinciper** väljer du den princip som du vill ändra.

2. I fönstret *Intune-appskydd* väljer du **Tilldelningar** för att öppna fönstret **Intune-appskydd – Tilldelningar** som visar en lista med aktuella användargrupper som har den här principen.

3. Om du vill lägga till en ny användargrupp för principen väljer du **Välj grupper att ta med** på fliken *Inkludera* och sedan användargruppen. Lägg till gruppen genom att välja **Välj**. 

4. Om du vill exkludera en användargrupp väljer du **Välj grupper att exkludera** på fliken *Exkludera* och väljer sedan användargruppen. Välj **Välj** för att ta bort användargruppen.  

5. Om du vill ta bort grupper som har lagts till tidigare markerar du ellipsen (...) och väljer **Ta bort** på någon av flikarna *Inkludera* eller *Exkludera*. 

5. När dina ändringar av tilldelningarna är klar sparar du konfigurationen genom att välja **Spara** och distribuerar principen till den nya uppsättningen användare. Om du väljer **Ignorera** innan du sparar konfigurationen ignoreras alla ändringar som du har gjort på flikarna *Inkludera* och *Exkludera*.

### <a name="to-change-windows-10-policy-settings"></a>Så här ändrar du inställningar för Windows 10-principer

1. I fönstret **Appskyddsprinciper** väljer du den princip som du vill ändra.

2. I fönstret *Intune-appskydd* väljer du **Egenskaper** för att öppna listan över inställningsområden som du kan redigera. 

3. Välj inställningsområde med de inställningar som du vill ändra såsom **Dataflytt** eller **Åtkomstbehörigheter**. Ändra inställningarna till nya värden.

4. Välj ikonen **Spara** för att spara dina ändringar. Upprepa processen för att välja ett inställningsområde och ändra och spara sedan ändringarna, tills alla ändringar har slutförts. Därefter kan du stänga fönstret *Intune-appskydd – Egenskaper*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Ange mål för appskyddsprinciper utifrån enhetens hanteringsstatus
I många organisationer är det vanligt att tillåta användare att använda både enheter som hanteras av hantering av mobilenheter (MDM) i Intune, till exempel företagsägda enheter, och ohanterade enheter som endast är skyddade med Intune-appskyddsprinciper. Ohanterade enheter är ofta kända som BYOD-enheter (Bring Your Own Devices).

Eftersom Intune-appskyddsprinciper som är riktade till en användares identitet kan skyddsinställningarna för en användare gälla både för registrerade (MDM-hanterade) och icke-registrerade enheter (utan MDM). Därför kan du rikta en Intune-appskyddsprincip till antingen Intune-registrerade eller icke-registrerade iOS- och Android-enheter. Du kan ha en skyddsprincip för ohanterade enheter där ett strikt dataförlustskydd (DLP) används och en separat skyddsprincip för MDM-hanterade enheter, där du kan använda lite mindre strikta DLP-kontroller. Mer information om hur det här fungerar på personliga Android Enterprise-enheter finns i [Appskyddsprinciper och arbetsprofiler](android-deployment-scenarios-app-protection-work-profiles.md).

För att skapa de här principerna bläddrar du till **Klientappar** > **Appskyddsprinciper** i Intune-konsolen och välj **Skapa princip**. Du kan även redigera eller en befintlig princip. För att appskyddsprincipen ska gälla för både hanterade och ohanterade enheter går du till sidan **Appar** och bekräftar att **Rikta till appar på alla typer av enheter** är angett till **Ja**, som är standardvärdet. Om du vill tilldela detaljerat baserat på hanteringstillståndet anger du **Rikta till appar på alla typer av enheter** till **Nej**. 

![Skärmbild av bladet Lägg till en princip med alternativet Rikta till alla typer av appar](./media/app-protection-policies/app-protection-policies-target-all.png)

### <a name="app-types"></a>Apptyper

- **Appar på ohanterade enheter**: Ohanterade enheter är enheter där Intune MDM-hantering inte har identifierats. Detta inkluderar MDM-leverantörer från tredje part.
- **Appar på Intune-hanterade enheter**: Hanterade enheter hanteras av Intune MDM.
- **Android Work-profilappar**: Hanterade enheter som har registrerats som Android Enterprise Work Profile-enheter.

> Observera att Android-enheter kommer att uppmanas att installera Intune-företagsportalappen oavsett vilken typ av app som valts. Om du till exempel väljer appar på Intune-hanterade enheter kommer användare med ohanterade Android-enheter fortfarande att frågas.

För iOS-krävs ytterligare appkonfigurationsinställningar för att rikta in appinställningar (APP) till appar på Intune-registrerade enheter:

- **IntuneMAMUPN** måste konfigureras för alla MDM-hanterade program. Mer information finns i [Hantera dataöverföring mellan iOS-appar med Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** måste konfigureras för alla tredje parters LOB MDM-hanterade program. **IntuneMAMDeviceID** ska konfigureras till enhetens ID-token. Till exempel `key=IntuneMAMDeviceID, value={{deviceID}}`. Mer information finns i [Lägg till appkonfigurationsprinciper för hanterade iOS-enheter](app-configuration-policies-use-ios.md).
- Om bara **IntuneMAMDeviceID** är konfigurerat kan Intune App betrakta enheten som ohanterad.

> [!NOTE]
> Läs [MAM protection policies targeted based on management state](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-) (MAM-skyddsprinciper som riktas baserat på hanteringstillstånd) för att få specifik information om iOS-stöd och appskyddsprinciper som baseras på hanteringstillstånd.

## <a name="policy-settings"></a>Principinställningar
Välj någon av följande länkar om du vill se en fullständig lista med principinställningar för iOS och Android:

- [iOS-principer](app-protection-policy-settings-ios.md)
- [Android-principer](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Nästa steg
[Övervaka efterlevnad och användarstatus](app-protection-policies-monitor.md)

## <a name="see-also"></a>Se även
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-android.md)
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](../fundamentals/end-user-mam-apps-ios.md)
