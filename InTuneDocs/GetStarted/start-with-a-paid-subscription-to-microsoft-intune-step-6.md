---
title: Skapa principer och publicera en app | Microsoft Intune
description: "Beskriver hur du skapar principer och publicerar en exempelapp för din Intune-prenumeration"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 539df37b239f61ab31e5994db00b46a9d5b6310c


---

# Skapa principer och publicera en app
Intune-principerna förser dig med inställningar som hjälper dig att kontrollera säkerhetsinställningarna på mobila enheter, underhålla Windows-brandväggen och Endpoint Protection-inställningarna för datorer, samt distribuera program. Du kan lära dig mer i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](/Intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) och [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](/Intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).

Du kan utföra två typer av appinstallationer med Intune. Den första är en **obligatorisk installation**som automatiskt distribuerar appen till hanterade datorer. Den andra är en **tillgänglig installation**som distribuerar appen, eller en länk till appen, till Intune-företagsportalen så att användarna kan välja om de vill installera den på sina datorer eller på sina mobila enheter.

Följande steg förklarar hur du skapar en konfigurationsprincip för mobila enheter, hur du skapar en brandväggsprincip för Windows-datorer och hur du konfigurerar Skype som en tillgänglig installation för mobila enheter när de har registrerats.

> [!TIP]
> När du har lagt till och distribuerat en ny princip kommer alla användare eller enheter i gruppen som du har distribuerat principen till att ärva inställningarna som sin baslinjeprincip. Du kan alltid granska och redigera information om dessa principer senare från principarbetsytan.


## Skapa och distribuera en konfigurationsprincip för mobila enheter

1.  Öppna [Intune-administrationskonsolen](https://manage.microsoft.com/).

2.  Välj ikonen **Princip** i det vänstra fönstret.

    ![admin-console-policy-workspace](./media/policy.png)

3.  Välj du **Lägg till princip** i listan **Uppgifter** på sidan **Översikt över princip** .

4.  Expandera den plattform som du vill skapa en princip för i principlistan och välj **Allmän konfiguration** > **Skapa och distribuera en princip med de rekommenderade inställningarna** > **Skapa princip**.

> [!NOTE]
> Det finns inga rekommenderade inställningar för enhetskonfigurationsprinciper eftersom det finns så många alternativ att välja bland. Du måste skapa en anpassad enhetskonfigurationsprincip.


5.  När du uppmanas med **Välj de grupper som du vill distribuera principen till** väljer du en grupp i listan över tillgängliga grupper och väljer **Lägg till** > **OK**.

Din princip visas i listan över konfigurationsprinciper och har distribuerats till gruppen **Intune-användare** . Visa principens egenskaper genom att dubbelklicka på den.

## Publicera Skype-appen för mobila enheter

1.  I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du ikonen **Appar** och väljer sedan **Appar** > **Lägg till app**. Ange dina [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] autentiseringsuppgifter om du uppmanas till detta.

    ![admin-console-apps-workspace](./media/apps.png)

    > [!NOTE]
    > När du startar **Intune Software Publisher** första gången inträffar en kort fördröjning medan programmet installeras.

2.  Läs säkerhetsvarningen och välj **Kör**.

3.  Välj **Nästa** på sidan **Innan du börjar**.

4.  På sidan **Programinstallation** går du till **Hur ska enheterna få tillgång till den här programvaran** och väljer **Extern länk**.

5.  Ange programmets externa länk i **Ange URL:en** och välj sedan **Nästa**. URL:en måste börja med **http://**. För Skype-appen använder du länken nedan som matchar den mobilplattform som du använder:

    -   **iOS:** [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:** [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 eller Windows Phone 8.1:** [http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  Tillhandahåll den information som du vill att användarna ska se i företagsportalen för programmet på sidan **Programbeskrivning** och välj sedan **Nästa**. Följande inställningar är tillgängliga (det här exemplet refererar till Skype):

    -   **Utgivare:** Ange utgivarens namn, ”Microsoft”

    -   **Namn:** Skriv **Skype**

    -   **Beskrivning:** Ge en beskrivning av programmet, t.ex. **Skype, kommunikationsapp**

    -   **Kategori:** Välj den kategori som passar bäst för det här programmet, t.ex. **Samarbete**

    -   **Visa den som aktuell app och markera den i företagsportalen:** Välj det här alternativet om du vill visa appen på en framträdande plats i företagsportalen på mobila enheter.

    -   **Ikon:** Välj om du vill koppla en ikon till programmet. Den valfria ikonens högsta storlek är 250 × 250 bildpunkter och den rekommenderade storleken är 32 × 32 bildpunkter.

7.  På sidan **Sammanfattning** kontrollerar du programinformationen och väljer sedan **Ladda upp**. Avsluta guiden genom att klicka på **Stäng**.

8.  I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Appar** > **Appar** > **Skype** > **Hantera distribution**.

9. Välj **Intune-användare** på sidan **Välj grupper** om du vill distribuera programmet till användargruppen och välj sedan **Lägg till** > **Nästa**

10. Välj **Tillgänglig installation** i kolumnen **Godkännande** för din grupp på sidan **Distributionsåtgärd** .

11. Välj **Slutför**.

Skype-appen är nu tillgänglig för installation på mobila enheter från företagsportalen, men du måste först installera [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-programvaran på datorer och mobila enheter.


### Nästa steg
Gratulerar! Du är klar med steg 6 i *snabbstartsguiden för Intune*.

>[!div class="step-by-step"]

>[&larr; **Ordna användare och enheter**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md) [**Anpassa företagsportalen** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  



<!--HONumber=Jul16_HO4-->


