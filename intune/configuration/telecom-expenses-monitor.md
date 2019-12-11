---
title: Konfigurera en tjänst för kostnadsuppföljning av telekommunikation i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Integrera Microsoft Intune med Saaswedo-tjänsten för kostnadsuppföljning av telekommunikation för att övervaka dataanvändning och ange tröskelvärden eller begränsningar på Android- och iOS-enheter.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 340659adfa3bbd40f98ccec9d8d44e952f7ec9b9
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059929"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Konfigurera tjänsten för kostnadsuppföljning av telekommunikation i Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Med Intune kan du hantera telekomutgifter från dataanvändning på företagsägda mobilenheter. Intune kan integreras med Saaswedos [kostnadsuppföljningstjänst för telekommunikation Datalert](http://datalert.biz/get-started). Datalert är en programvara för kostnadsuppföljning av telekommunikation som låter dig hantera telekommunikationens dataanvändning. Den hjälper dig att undvika kostsam och oväntad överförbrukning av data och nätverksväxling för dina Intune-hanterade enheter.

Med Datalert kan du konfigurera, övervaka och tillämpa gränser för nätverksväxling och lokal dataanvändning. Automatiserade aviseringar utlöses när gränserna överskrider definierade tröskelvärden. Du kan också konfigurera tjänsten så att olika åtgärder tillämpas på enskilda personer eller grupper med slutanvändare (t.ex. inaktivering av nätverksväxling eller när tröskelvärdet överskrids). Rapporter med information om övervakning och dataanvändning är tillgängliga från Datalerts hanteringskonsol.

Följande bild visar hur Intune integrerar med Datalert:

  ![Diagram över Intunes integrering med Datalert](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

Om du vill använda Datalert-tjänsten med Intune finns det vissa konfigurationsinställningar i Datalert och Intune. Den här artikeln visar hur du:

- Konfigurera inställningarna i Datalert-konsolen för att ansluta Datalert-tjänsten till Intune.
- Bekräfta att den här anslutningen är aktiv och aktiverad i Intune.
- Använd Intune för att lägga till Datalert-appen till dina enheter.
- Stäng av Datalert-tjänsten och för Intune (valfritt).

## <a name="supported-platforms"></a>Plattformar som stöds

- Android 4.4 och nyare enheter som är Knox-kompatibla (Samsung)

  [Android-versioner som har stöd för Knox](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) (öppnar Samsung webbplats) visar en lista över de Knox-versioner som stöds.

- iOS 8.0 och senare

## <a name="prerequisites"></a>Krav

- En prenumeration på Microsoft Intune och åtkomst till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)
- En prenumeration på [Datalert](http://www.datalert.biz/) (öppnar Datalerts webbplats)

## <a name="telecom-expense-management-providers"></a>Leverantörer som erbjuder kostnadsuppföljning av telekommunikation

Intune kan integreras med följande leverantörer för kostnadsuppföljning av telekommunikation:

- [Saaswedos Datalert-tjänst för kostnadsuppföljning av telekommunikation](http://www.datalert.biz/) (öppnar Datalerts webbplats)

## <a name="deploy-the-intune-and-datalert-solution"></a>Distribuera Intune- och Datalert-lösningen

### <a name="step-1-connect-the-datalert-service-to-intune"></a>Steg 1: Ansluta Dataalert-tjänsten till Intune

1. Logga in på Datalert-hanteringskonsolen med dina administratörsautentiseringsuppgifter.

2. I-konsolen går du till fliken **Inställningar** > **MDM-konfiguration**.

3. Välj **Avblockera**. **Avblockera** gör att du kan ändra eller uppdatera inställningarna på sidan.

4. I **Intune/Datalert Connection** > **Server MDM** väljer du **Microsoft Intune**.

5. För **Azure AD-domän** anger du ID:t för din Azure-klientorganisation. Välj **Anslutning**.

    När du väljer **Anslutning** stämmer Datalert-tjänsten av med Intune. Den bekräftar att det inte finns några befintliga Datalert-anslutningar. Efter några ögonblick visas Microsofts inloggningssida, följt av Azure-autentiseringen för Datalert.

6. Välj **Godkänn** på Microsofts autentiseringssida.

    Du omdirigeras till en **Tack**-sida i Datalert som stängs efter några ögonblick. Datalert verifierar anslutningen och visar gröna bockmarkeringar bredvid de objekt som har verifierats. Om verifieringen misslyckas visas ett meddelande i rött. Kontakta supporten för Datalert.

    Följande bild visar den gröna bockmarkeringen när anslutningen lyckas:

      ![Datalert-sidan visar att anslutningen har lyckats](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. I **Datalert App/ADAL Consent** (Datalert-app / ADAL-medgivande) växlar du inställningen till **På**. Välj **Godkänn** på Microsofts autentiseringssida.

    Du omdirigeras till en **Tack**-sida i Datalert som stängs efter några ögonblick. Datalert verifierar anslutningen och visar gröna bockmarkeringar bredvid de objekt som har verifierats. Om verifieringen misslyckas visas ett meddelande i rött. Kontakta supporten för Datalert.

    Följande bild visar den gröna bockmarkeringen när anslutningen lyckas:

      ![Datalert-sidan visar att anslutningen har lyckats](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. In **MDM Profiles management (optional)** , set the switch to **On**. Med den här inställningen kan Datalert läsa tillgängliga profiler i Intune för att hjälpa dig att konfigurera principer. 

    Välj **Godkänn** på Microsofts autentiseringssida.

    Du omdirigeras till en **Tack**-sida i Datalert som stängs efter några ögonblick. Datalert verifierar anslutningen och visar gröna bockmarkeringar bredvid de objekt som har verifierats. Om verifieringen misslyckas visas ett meddelande i rött. Kontakta supporten för Datalert.

    Följande bild visar den gröna bockmarkeringen när anslutningen lyckas:

   ![Datalert-sidan visar att anslutningen har lyckats](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>Steg 2: Bekräfta att kostnadsuppföljning av telekommunikation är aktiv i Intune

När du har slutfört steg 1 aktiveras anslutningen automatiskt. I Intune visas anslutningsstatusen **Aktiv**. Gör så här för att kontrollera att statusen är aktiv:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Administration av klientorganisation** > **Anslutning och token** > **Kostnadsuppföljning av telekommunikation**. Leta efter anslutningsstatusen **Aktiv**:

   ![Intune-sidan visar att Datalerts anslutningsstatus är Aktiv](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>Steg 3: Distribuera Datalert-appen till enheter

Om du vill bekräfta att endast dataanvändning från organisationsägda serier samlas in ska du:

- skapa enhetskategorier i Intune.
- ange att Datalert-appen endast används för företagets telefoner.

Det här avsnittet innehåller de här stegen.

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>Skapa enhetskategorier och enhetsgrupper som hör till olika kategorier

Depending on your organizational needs, create at least two device categories, such as Corporate and Personal. Skapa sedan dynamiska enhetsgrupper för varje kategori. Du kan skapa fler kategorier för din organisation om det behövs.

Information om att skapa enhetskategorier finns i [Mappa enheter till grupper](../enrollment/device-group-mapping.md).

Dessa kategorier visas för användare under registreringen ([registrera Android-enheter](../enrollment/android-enroll.md)). Beroende på vilken kategori användarna väljer flyttas den registrerade enheten till motsvarande enhetsgrupp.

  ![Skärmbild av fönstret Lägg till en princip](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>Lägg till Datalert-appen i Intune

Följande steg lägger till Datalert-appen. I detta exempel används iOS. [Add apps](../apps/apps-add.md) and [use scope tags](../fundamentals/scope-tags.md) have more specific information on these steps.

1. Välj **Appar** > **Alla appar** > **Lägg till** i [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj din **Apptyp**. För iOS väljer du till exempel **Store-app – iOS**.

3. I **Sök App Store** skriver du **Datalert** för att hitta Datalert-appen.

4. Välj appen **Datalert** > **Välj**:

   ![Lägg till Datalert-appen från App Store i Intune-klientprogram](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. Ange ytterligare egenskaper, till exempel information om appar och omfångstaggar:

   ![Ange appens egenskaper, inklusive namn, beskrivning, operativsystem och andra inställningar för appen i Intune](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. Klicka på **OK** > **Lägg till** för att spara ändringarna. Datalert-appen visas i listan.

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Associera Datalert-appen med gruppen för företagsenheter

1. I **Appar** > **Alla appar** väljer du appen Datalert som du lade till i föregående steg.

2. Välj **Tilldelningar** > **Lägg till grupp**. Välj hur appen är tilldelad. [Tilldela appar till grupper i Intune](../apps/apps-deploy.md) har mer information om dessa inställningar.

    I dessa steg får du välja om du vill att appinstallationen ska vara obligatorisk eller valfri för gruppen. I följande exempel visas att installationen krävs. När installationen krävs måste användarna installera Datalert-appen efter att de har registrerat sin enhet.

   ![Skärmbild av fönstret Lägg till en princip](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>Steg 4: Lägga till företagets telefonlinjer i Datalert-konsolen

Intune- och Datalert-tjänsterna är nu konfigurerade så att de kommunicerar med varandra. Nu ska du lägga till organisationens betalda telefonlinjer i Datalert-konsolen. Och ange tröskelvärden och åtgärder för användning av mobildata eller minuter. Du kan lägga till företagets betalda telefonlinjer till Datalert-konsolen manuellt, eller låta dem läggas till automatiskt när enheten har registrerats i Intune.

Om du vill ange dessa objekt går du till [Datalert-installation för Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (öppnar Datalert webbplats). Gå till fliken **Inställningar** och följ stegen i installationsguiden.

  ![Skärmbild av fönstret Lägg till en princip](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

Tjänsten Datalert är nu aktiv. Den börjar övervaka dataanvändningen och inaktiverar roaming- och mobildata på enheter som överskrider de konfigurerade användningsbegränsningarna.

## <a name="end-user-enrollment"></a>Slutanvändarregistrering

För slutanvändarupplevelsen kan följande artiklar vara användbara:

- [Registrera iOS-enheten i kostnadsuppföljningen av telekommunikation](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [Registrera Android-enheten i kostnadsuppföljningen av telekommunikation](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>Stänga av tjänsten Datalert

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Innehavaradministratör** > **Anslutningar och token** > **Kostnadsuppföljning av telekommunikation**.
2. Ställ in **Enable kostnadsuppföljning av telekommunikation och blockera mobil- och roamingdata på enheter som överskrider de kvoter som du har angett** på **Inaktivera**.
3. **Spara** ändringarna.

> [!IMPORTANT]
> Om du inaktiverar Datalert-tjänsten i Intune:
>
> - Alla åtgärder som har tillämpats på enheter, på grund av tidigare överskridna användningsbegränsningar, återställs.
> - Användarna blockeras inte längre från dataåtkomst och roaming.
> - Intune kan fortfarande ta emot signaler från tjänsten, men ignorerar dem.

## <a name="next-steps"></a>Nästa steg

Dataanvändningsrapporter är endast tillgängliga i Saaswedos Datalert-hanteringskonsol.
