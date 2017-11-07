---
title: "Konfigurera tjänsten för kostnadsuppföljning av telekommunikation"
titleSuffix: Azure portal
description: "Konfigurera Saaswedos tjänst för kostnadsuppföljning av telekommunikation för integrering med Intune.”"
keywords: Saaswedo
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e3f97cebe411b191f2bf0b13fb756c705613c46a
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2017
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Konfigurera tjänsten för kostnadsuppföljning av telekommunikation i Intune
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med Intune kan du hantera telekomkostnader för dataanvändning på företagsägda mobila enheter. Intune implementerar den här funktionen genom integrering med tredjepartsprogramutvecklaren Saaswedos lösning för kostnadsuppföljning av telekommunikation, Datalert. Datalert är ett program för kostnadsuppföljning av telekommunikation i realtid, som hjälper dig att hantera dataanvändningen och undvika kostsam och oväntad överförbrukning av data och roaming på Intune-hanterade enheter.

Med Intunes Datalert-integrering kan du centralt konfigurera, övervaka och upprätthålla begränsningar för roaming och inrikes dataanvändning genom att definiera automatiska varningar när fastställda tröskelvärden överskrids. Du kan konfigurera tjänsten så att olika åtgärder tillämpas på enskilda individer eller grupper med slutanvändare, t.ex. inaktivering av roaming, när tröskelvärdet överskrids. Rapporter med information om övervakning och dataanvändning är tillgängliga från Datalerts hanteringskonsol.

Följande diagram visar hur Intune integrerar med Datalert.

  ![Diagram över Intunes integrering med Datalert](./media/tem-datalert-intune-solution-diagram.png)

Innan du kan använda Datalert med Intune måste du konfigurera inställningar i Datalert-konsolen och i Intune. Anslutningen måste vara aktiverad för Datalert-tjänsten och för Intune. Om anslutningen är aktiverad i Datalert men inte i Intune, tar Intune emot kommunikationen men ignorerar den.

## <a name="supported-platforms"></a>Plattformar som stöds

- Samsung Knox
- iOS 8.0 och senare

## <a name="prerequisites"></a>Förutsättningar

- En prenumeration på Microsoft Intune och åtkomst till Azure-portalen.
- En prenumeration på Datalert-tjänsten för kostnadsuppföljning av telekommunikation

## <a name="list-of-telecom-expense-management-providers"></a>Lista med leverantörer som erbjuder kostnadsuppföljning av telekommunikation

Intune kan för närvarande integreras med följande leverantörer för kostnadsuppföljning av telekommunikation:

[Saaswedos Datalert-tjänst för kostnadsuppföljning av telekommunikation](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>Distribuera den integrerade Intune- och Datalert-lösningen

Innan du börjar kontrollerar du att du har en Intune-prenumeration och en prenumeration på Datalert-tjänsten för kostnadsuppföljning av telekommunikation.

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>Steg 1: Ansluta Dataalert till Microsoft Intune

1. Logga in på Datalert-hanteringskonsolen med dina administratörsautentiseringsuppgifter.

2. I Datalert-hanteringskonsolen går du till fliken **Settings** (Inställningar) och sedan till **MDM configuration** (MDM-konfiguration).

3. Välj **Unblock** (Lås upp) så att du kan ange inställningarna på sidan.

4. För **Server MDM** (Server-MDM) väljer du **Microsoft Intune**.

5. För **Azure AD Domain** (Azure AD-domän) anger du ditt Azure-klient-ID och väljer **Connection** (Anslutning).

    När du väljer **Connection** (Anslutning) kontrollerar Datalert att det inte finns några befintliga Datalert-anslutningar med Intune. Efter några sekunder visas Microsofts inloggningssida, följt av Azure-autentiseringen för Datalert.

6. Välj **Godkänn** på Microsofts autentiseringssida. Du omdirigeras till Datalerts ”Tack”-sida som stängs efter några sekunder. Datalert verifierar anslutningen och visar gröna bockmarkeringar bredvid listan med objekt som har verifierats. Om verifieringen misslyckas visas ett meddelande i rött. Om detta händer kontaktar du supporten för Datalert.

    I följande skärmbild ser du de gröna bockmarkeringar som visas när anslutningen har upprättats.

  ![Datalert-sida som visar att anslutningen har lyckats](./media/tem-mdm-configuration-mdm-server-page.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>Steg 2: Kontrollera att funktionen för kostnadsuppföljning av telekommunikation är aktiv i Intune

När du har slutfört steg 1 ovan bör anslutningen aktiveras automatiskt, och anslutningsstatusen **Aktiv** bör visas på Azure-portalen. Dessa steg beskriver var du ser statusen **Aktiv**.

1. Logga in på Azure-portalen.

2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.

3. Välj **Enhetskonfiguration** på **Intune**-bladet.

4. På bladet **Enhetskonfigurationen** väljer du **Konfiguration** > **Kostnadsuppföljning av telekommunikation**.

   Anslutningsstatusen **Aktiv** bör visas längst upp på sidan.

  ![Azure-portalen som visar Datalert-anslutningsstatusen Aktiv](./media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>Steg 3: Distribuera Datalert-appen till företagets registrerade enheter

För att säkerställa att dataanvändning endast samlas in från företagsägda telefonlinjer måste du skapa enhetskategorier i Intune och sedan rikta Datalert-appen till endast företagstelefoner. Följ anvisningarna i följande underavsnitt.

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>Definiera enhetskategorier och enhetsgrupper som hör till olika kategorier

Beroende på organisationens behov måste du skapa minst två enhetskategorier (till exempel Företag och Personliga) och skapa dynamiska enhetsgrupper för varje kategori. Du kan skapa fler kategorier för din organisation om det behövs.

Dessa kategorier visas för användarna under registreringen. Beroende på vilken kategori användarna väljer flyttas den registrerade enheten till motsvarande enhetsgrupp. Steg som beskriver hur du skapar enhetskategorier finns i [Mappa enheter till grupper](device-group-mapping.md).

  ![Skärmbild av bladet Lägg till en princip](./media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Skapa Datalert-appen i Intune

Följ dessa steg för att skapa Datalert-appen i Intune för varje plattform. iOS används som exempel i dessa steg.

1. På bladet **Intune** på Azure-portalen väljer du **Mobilappar**.

2. På bladet **Mobilappar** väljer du **Hantera** > **Appar**.

3. Välj **Lägg till** för att lägga till en app.

4. Välj typ av app. Till exempel väljer du **iOS Store-app** för iOS.

5. I **Sök i App Store** letar du upp Datalert-appen genom att skriva **Datalert** i fönstret.

6. Välj **Datalert**-appen och sedan **OK**.

  ![Skärmbild av bladet Lägg till en princip](./media/tem-select-app-from-apple-app-store.png)

7. Slutför de återstående stegen för att skapa en app för iOS.

  ![Skärmbild av bladet Lägg till en princip](./media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Associera Datalert-appen med gruppen för företagsenheter

1. Välj Datalert-appen för iOS som du skapade i föregående steg.

2. På bladet **Appar** går du till **Hantera** > **Tilldelningar**.

3. Välj **Välj grupper** och följ anvisningarna för att välja gruppen med företagsenheter.

4. Välj om du vill att appinstallationen ska vara obligatorisk eller valfri för gruppen. I följande exempelskärmbilder visas installationen som obligatorisk, vilket innebär att användarna måste installera Datalert-appen när de har registrerat sina enheter.

  ![Skärmbild av bladet Lägg till en princip](./media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>Steg 4: Lägga till företagsägda telefonlinjer i Datalert-konsolen

Du har konfigurerat Intune- och Datalert-tjänsterna så att de kommunicerar med varandra. Nu måste du lägga till företagets telefonlinjer i Datalert-konsolen och definiera tröskelvärden och åtgärder för överträdelser av roaming- eller mobiltelefonanvändning. Du kan antingen lägga till företagets betalda telefonlinjer till Datalert-konsolen manuellt, eller låta dem läggas till automatiskt när enheten registreras i Intune.

Du konfigurerar dessa objekt genom att gå till sidan för [Datalert-konfiguration för Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (http://www.datalert.fr/microsoft-intune/intune-setup). Följ sedan anvisningarna i installationsguiden på fliken **Inställningar**.

  ![Skärmbild av bladet Lägg till en princip](./media/tem-add-phone-lines-to-datalert-console.png)


Nu är Datalert-tjänsten aktiv och övervakar dataanvändningen och inaktiverar roaming- och mobildata på enheter som överskrider de konfigurerade användningsbegränsningarna.

## <a name="client-enrollment-experience"></a>Klientregistrering
Läs följande om registrering av klienten:
-   [Registrera iOS-enheten i kostnadsuppföljningen av telekommunikation](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-   [Registrera Android-enheten i kostnadsuppföljningen av telekommunikation](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>Stänga av Datalert

Om du inaktiverar Datalert-tjänsten på Azure-portalen:

- Alla åtgärder som har tillämpats på enheter, på grund av tidigare överskridna användningsbegränsningar, återställs.
- Användarna blockeras inte längre från dataåtkomst och roaming.
- Intune kan fortfarande ta emot signaler från tjänsten, men ignorerar dem.

**Så här stänger du av tjänsten**

1. På bladet **Kostnadsuppföljning av telekommunikation** på Azure-portalen väljer du **Inaktivera**.

2. Välj **Spara**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Visa roaming- och dataanvändningsrapporter

För tillfället är dataanvändningsrapporter endast tillgängliga i Saaswedos Datalert-hanteringskonsol.

Anvisningarna som dina slutanvändarna följer för att installera Datalert-appen kommer snart.
