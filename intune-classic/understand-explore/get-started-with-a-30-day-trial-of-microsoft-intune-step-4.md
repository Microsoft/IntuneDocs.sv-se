---
title: "Skapa principer och publicera en app för användare | Microsoft Docs"
description: "Så här skapar du principer och publicerar en app när du registrerar dig för en kostnadsfri 30-dagars utvärderingsversion av Intune"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 12/12/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 0e836571b869e7a32b19968da1d78035a6bae7f2
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---


# <a name="create-policies-and-publish-an-app-to-evaluation-users"></a>Skapa principer och publicera en app för utvärderingsanvändare

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune-principerna förser dig med inställningar som hjälper dig att kontrollera säkerhetsinställningarna på mobila enheter, underhålla Windows-brandväggen och Endpoint Protection-inställningarna för datorer, samt distribuera program. Om du planerar att använda Intune för enheter som du konfigurerar för användning i produktionsmiljön efter utvärderingen är det ytterst viktigt att du följer anvisningarna i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).

Du kan utföra två typer av appinstallationer med Intune. Den första är en **obligatorisk installation** som automatiskt distribuerar appen till hanterade enheter. Den andra är en **tillgänglig installation**som distribuerar appen, eller en länk till appen, till Intune-företagsportalen så att användarna kan välja om de vill installera den på sina datorer eller på sina mobila enheter.

Innan du använder Intune för att distribuera appar kontrollerar du att du har rätt licenser för att publicera, distribuera och använda appen. Med arbetsytan **Licenser** kan du lägga till och hantera licensavtalsinformation för appar och programvara som köpts via Microsofts volymlicensavtal, samt för Microsoft-program, eller program från annan leverantör än Microsoft, som köpts på annat sätt. Du kan sedan skapa licensrapporter som visar hanterad licensanvändningsinformation i hela företaget, så att du håller dig informerad om licensanvändningsaktiviteten.

I följande steg ska du ställa in en konfigurationsprincip för en mobil enhet och en brandväggsprincip för en Windows-dator, samt konfigurera Skype som en tillgänglig installation för mobila enheter när de har registrerats. När du har lagt till och distribuerat en ny princip kommer alla användare eller enheter i gruppen som du har distribuerat principen till att ärva inställningarna som sin baslinjeprincip. Du kan alltid granska och redigera information om dessa principer senare från arbetsytan **Princip** i administrationskonsolen.

## <a name="create-and-deploy-a-mobile-device-configuration-policy"></a>Skapa och distribuera en konfigurationsprincip för mobila enheter

1.  Öppna [Intune-administrationskonsolen](https://manage.microsoft.com/).

2.  Välj ikonen **Princip** i det vänstra fönstret.

3.  Välj du **Lägg till princip** i listan **Uppgifter** på sidan **Översikt över princip** .

4.  I principlistan expanderar du den plattform som du vill skapa en princip för och väljer sedan **Allmän konfiguration**, **Skapa och distribuera en anpassad princip** och väljer sedan **Skapa princip**.

5.  När du får uppmaningen **Välj de grupper som du vill distribuera principen till** väljer du **Mina utvärderingsanvändare** i listan och väljer **Lägg till** &gt; **OK**.

Din princip visas i listan över konfigurationsprinciper och har distribuerats till gruppen **Mina utvärderingsanvändare** . Visa principens egenskaper genom att dubbelklicka på den.

## <a name="publish-the-skype-app-for-mobile-devices"></a>Publicera Skype-appen för mobila enheter

1.  I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du ikonen **Appar** och väljer sedan **Appar** &gt; **Lägg till app**. Ange dina autentiseringsuppgifter för Intune om du uppmanas till detta.

    > [!NOTE]
    > När du startar **Intune Software Publisher** första gången inträffar en kort fördröjning medan programmet installeras.

2.  Läs säkerhetsvarningen och välj **Kör**.

3.  Välj **Nästa** på sidan **Innan du börjar**.

4.  På sidan **Programinstallation** i **Hur ska enheterna få tillgång till den här programvaran**väljer du **Extern länk**.

5.  Ange programmets externa länk i **Ange URL:en** och välj sedan **Nästa**. URL:en måste börja med **https://**. För Skype-appen använder du länken nedan som matchar den mobilplattform som du använder:

    -   **iOS:** [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:** [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8.1:** [http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  Tillhandahåll den information som du vill att användarna ska se i företagsportalen för programmet på sidan **Programbeskrivning** och välj sedan **Nästa**. Följande inställningar är tillgängliga (det här exemplet refererar till Skype):

    -   **Utgivare:** Ange utgivarens namn, **Microsoft**

    -   **Namn:** Skriv **Skype**

    -   **Beskrivning:** Ge en beskrivning av programmet, t.ex. **Skype, kommunikationsapp**

    -   **Kategori:** Välj den kategori som passar bäst för det här programmet, t.ex. **Samarbete**

    -   **Visa den som aktuell app och markera den i företagsportalen:** Välj det här alternativet om du vill visa appen på en framträdande plats i företagsportalen på mobila enheter.

    -   **Ikon:**  (Valfritt) Välj om du vill koppla en ikon till programmet. Maximal ikonstorlek är 250 x 250 bildpunkter, men rekommenderad ikonstorlek är 32 x 32 bildpunkter.

7.  På sidan **Sammanfattning** kontrollerar du programinformationen och väljer sedan **Ladda upp**. Avsluta guiden genom att klicka på **Stäng**.

8.  I [Intune-administratörskonsolen](https://manage.microsoft.com/) klickar du på **Appar** &gt; **Appar** &gt; **Skype** &gt; **Hantera distribution**.

9. Välj **Mina utvärderingsanvändare** på sidan **Välj grupper** om du vill distribuera programmet till den användargruppen och välj sedan **Lägg till** &gt; **Nästa**.

10. Välj **Tillgänglig installation** i kolumnen **Godkännande** för din grupp på sidan **Distributionsåtgärd** .

11. Välj **Slutför**.

## <a name="install-the-skype-app"></a>Installera Skype-appen
Öppna företagsportalen på den mobila enheten, välj **Appar**och installera sedan Microsoft Skype.

Härmed avslutas guiden för mobila Intune-enheter, men du kan läsa mer om Intune genom att följa länkarna under Nästa steg.
## <a name="next-steps"></a>Nästa steg
Läs mer om andra [Intune-funktioner](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)

Läs om de [vanligaste sätten att använda Intune på](common-ways-to-use-intune.md)

Konvertera till en [betald prenumeration](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md)

