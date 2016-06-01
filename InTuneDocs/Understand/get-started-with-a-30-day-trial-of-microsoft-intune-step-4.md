---
# required metadata

title: Skapa principer och publicera en app för utvärderingsanvändare | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Skapa principer och publicera en app för utvärderingsanvändare
Intune-principerna förser dig med inställningar som hjälper dig att kontrollera säkerhetsinställningarna på mobila enheter, underhålla Windows-brandväggen och Endpoint Protection-inställningarna för datorer, samt distribuera program. Om du planerar att använda Intune för enheter som du konfigurerar för produktion efter utvärderingsperioden är det mycket viktigt att du följer anvisningarna i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) och [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

Du kan utföra två typer av appinstallationer med Intune. Den första är en **obligatorisk installation**som automatiskt distribuerar appen till hanterade datorer. Den andra är en **tillgänglig installation**som distribuerar appen, eller en länk till appen, till Intune-företagsportalen så att användarna kan välja om de vill installera den på sina datorer eller på sina mobila enheter.

Innan du använder Intune för att distribuera appar kontrollerar du att du har rätt licenser för att publicera, distribuera och använda appen. Med arbetsytan **Licenser** kan du lägga till och hantera licensavtalsinformation för appar och programvara som köpts via Microsofts volymlicensavtal, samt för Microsoft-program, eller program från annan leverantör än Microsoft, som köpts på annat sätt. Du kan sedan skapa licensrapporter som visar hanterad licensanvändningsinformation i hela företaget, så att du håller dig informerad om licensanvändningsaktiviteten.

I följande steg ska du ställa in en konfigurationsprincip för en mobil enhet och en brandväggsprincip för en Windows-dator, samt konfigurera Skype som en tillgänglig installation för mobila enheter när de har registrerats. När du har lagt till och distribuerat en ny princip kommer alla användare eller enheter i gruppen som du har distribuerat principen till att ärva inställningarna som sin baslinjeprincip. Du kan alltid granska och redigera information om dessa principer senare från arbetsytan **Princip** i administrationskonsolen.

## Skapa och distribuera en konfigurationsprincip för mobila enheter

1.  Öppna [Intune-administrationskonsolen](https://manage.microsoft.com/)

2.  Välj ikonen **Princip** i det vänstra fönstret.

3.  Välj **Lägg till princip** i listan **Uppgifter** på sidan **Principöversikt**.

4.  I principlistan expanderar du den plattform som du vill skapa en princip för och väljer sedan **Allmän konfiguration**, **Skapa och distribuera en princip med de rekommenderade inställningarna**och väljer **Skapa princip**.

5.  När du får uppmaningen **Välj de grupper som du vill distribuera principen till** väljer du **Mina utvärderingsanvändare** i listan och väljer **Lägg till** &gt; **OK**

Din princip visas i listan över konfigurationsprinciper och har distribuerats till gruppen **Mina utvärderingsanvändare** . Visa principens egenskaper genom att dubbelklicka på den.

## Publicera Skype-appen för mobila enheter

1.  I [Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du ikonen **Appar** och väljer sedan **Appar** &gt; **Lägg till app**. Ange dina autentiseringsuppgifter för Intune om du uppmanas till detta.

    > När du startar **Intune Software Publisher** första gången inträffar en kort fördröjning medan programmet installeras.

2.  Granska säkerhetsvarningen och välj **Kör**.

3.  Välj **Nästa** på sidan **Innan du börjar**.

4.  På sidan **Programinstallation** i **Hur ska enheterna få tillgång till den här programvaran** väljer du **Extern länk**

5.  Ange programmets externa länk i **Ange URL:en** och välj sedan **Nästa**. URL:en måste börja med **https://**. För Skype-appen använder du länken nedan som matchar den mobilplattform som du använder:

    -   **iOS:** [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:** [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 eller Windows Phone 8.1:** [http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  Tillhandahåll den information som du vill att användarna ska se i företagsportalen för programmet på sidan **Programbeskrivning** och välj sedan **Nästa**. Följande inställningar är tillgängliga (det här exemplet refererar till Skype):

    -   **Utgivare:** Ange utgivarens namn, **Microsoft**

    -   **Namn:** Skriv **Skype**

    -   **Beskrivning:** Ge en beskrivning av programmet, t.ex. **Skype, kommunikationsapp**

    -   **Kategori:** Välj den kategori som passar bäst för det här programmet, t.ex. **Samarbete**

    -   **Visa den som aktuell app och markera den i företagsportalen:** Välj det här alternativet om du vill visa appen på en framträdande plats i företagsportalen på mobila enheter.

    -   **Ikon:**  (Valfritt) Välj om du vill koppla en ikon till programmet. Maximal ikonstorlek är 250 x 250 bildpunkter, men rekommenderad ikonstorlek är 32 x 32 bildpunkter.

7.  På sidan **Sammanfattning** kontrollerar du programinformationen och väljer sedan **Ladda upp**. Avsluta guiden genom att klicka på **Stäng**.

8.  I [Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du **Appar** &gt; **Appar** &gt; **Skype** &gt; **Hantera distribution**

9. Välj **Mina utvärderingsanvändare** på sidan **Välj grupper** om du vill distribuera programmet till den användargruppen och välj sedan **Lägg till** &gt; **Nästa**

10. Välj **Tillgänglig installation** i kolumnen **Godkännande** för din grupp på sidan **Distributionsåtgärd** .

11. Välj **Slutför**

Skype-appen är nu tillgänglig för installation på mobila enheter från företagsportalen, men du måste först installera Intune-programvaran på datorer och mobila enheter.

### Nästa steg
Gratulerar! Du har precis slutfört steg 4 i genomgången av *Microsoft Intune-utvärderingen*.

>[!div class="step-by-step"]

>[&larr; **Skapa grupper**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)     [**Registrera enheter** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md)  


<!--HONumber=May16_HO2-->


