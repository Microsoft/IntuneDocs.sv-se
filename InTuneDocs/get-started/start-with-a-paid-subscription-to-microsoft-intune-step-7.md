---
title: "Anpassa företagsportalen | Microsoft Docs"
description: "Med Intune företagsportal kan användarna utföra vanliga aktiviteter som att registrera enheter, installera appar och hitta information om IT-avdelningen."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ad13897fe7bbe4fe13167bb4ce7f558b436a7a90
ms.openlocfilehash: 2191295407e0c1bb2c3861b8a8d168dd3697da45


---

# <a name="customize-the-company-portal"></a>Anpassa företagsportalen.

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet beskriver hur administratörer kan anpassa Intunes företagsportalapp och företagsportalwebbplats.

Intune-företagsportalen är den plats där användare kan komma åt företagets data och utföra vanliga aktiviteter som att registrera enheter, installera appar och hitta information för att få hjälp från IT-avdelningen.

Intunes företagsportal ger användare åtkomst till företagsdata och appar. Företagsportalen finns tillgänglig på två sätt:

-   **Företagsportalappen**: En app som är tillgänglig på enheter som du hanterar med Intune. Läs mer om företagsportalapparna för [Android](/Intune/EndUser/using-your-android-device-with-intune), [iOS](/Intune/EndUser/using-your-iOS-or-macOS-device-with-intune) och [Windows](/Intune/EndUser/using-your-windows-device-with-intune).


- **Företagsportalens webbplats**: En webbplats där användarna kan utföra de flesta uppgifter de kan göra från företagsportalappen. Intune-företagetsportalens webbplats är [http://portal.manage.microsoft.com](http://portal.manage.microsoft.com). Läs mer om webbplatsen på [Använda Intune-företagsportalens webbplats](/Intune/EndUser/using-the-intune-company-portal-website).

> [!TIP]
> När du anpassar företagsportalen gäller konfigurationerna både företagsportalens webbplats och företagsportalens appar.

Några uppgifter som användarna kan utföra i företagsportalen:

-   Registrera enheter
-   Visa status för sina enheter
-   Återställa sin enhet
-   Återställa sitt lösenord
-   Låsa sin enhet via fjärranslutning
-   Hämta programvara som distribueras av din organisation
-   Kontakta IT-avdelningen för support

## <a name="customize-company-portal-settings"></a>Anpassa inställningar för företagsportalen
Genom att anpassa företagsportalen kan du skapa en välbekant miljö för dina slutanvändare. Logga in på [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) som klient eller tjänstadministratör, välj **Admin** &gt; **Företagsportal** och konfigurera inställningarna för företagsportalen.

![admin-console-admin-workspace-comp-portal-settings](./media/companyportal.png)

## <a name="company-contact-information-and-privacy-statement"></a>Företagets kontaktinformation och sekretesspolicy
Företagsnamnet visas som företagsportalens rubrik. Kontaktuppgifterna och informationen visas för användarna på skärmen Kontakta IT på företagsportalen. Sekretesspolicyn visas när användaren klickar på sekretesslänken.

|Fältnamn|Högsta längd|Mer information|
    |----------|------------------------|----------------|
    |Företag|40|Det här namnet visas som företagsportalens rubrik.|
    |IT-avdelningens kontaktperson|40|Det här namnet visas på sidan **Kontakta IT-avdelningen**.|
    |IT-avdelningens telefonnummer|20|Det här numret visas på sidan **Kontakta IT-avdelningen**.|
    |IT-avdelningens e-postadress|40|Den här adressen visas på sidan **Kontakta IT-avdelningen**. Du måste ange en giltig e-postadress i formatet **alias@domainname.com**.|
    |Ytterligare information|120|Visas på sidan **Kontakta IT-avdelningen**.|
    |URL till företagets sekretesspolicy|79|Du kan ange en egen sekretesspolicy för ditt företag som visas när användaren klickar på en länk på företagsportalen. Du måste ange en giltig URL i formatet https://www.contoso.com.|

## <a name="support-contacts"></a>Supportkontakter
Supportwebbplatsen visas för användarna på företagsportalen så att de kan få tillgång till onlinesupport.

|Fältnamn|Högsta längd|Mer information|
    |----------|------------------------|----------------|
    |URL till supportwebbplatsen|150|Om du har en supportwebbplats som du vill att slutanvändarna ska använda, anger du webbadressen här. URL:en måste ha formatet https://www.contoso.com. Om du inte anger någon webbadress kommer inget att visas på sidan **Kontakta IT** på företagsportalen.|
    |Namn på webbplats|40|Det här är det egna namnet som visas för supportwebbplatsens URL. Om du bara anger URL:en till en supportwebbplats utan något eget namn visas **Gå till IT-webbplatsen** på sidan **Kontakta IT** på företagsportalen.|

## <a name="company-branding-customization"></a>Varumärkesanpassning
Du kan anpassa företagsportalen med företagets logotyp, företagets namn, temafärg och bakgrund.

|Fältnamn|Mer information|
    |----------|----------------|
    |Temafärg|Välj en temafärg som ska användas på företagsportalen.|
    |Infoga företagslogotyp|Om du aktiverar det här alternativet kan du ladda upp företagets logotyp så att den visas på företagsportalen. Du kan ladda upp två logotyper: en logotyp som visas när företagsportalens bakgrund är vit och en logotyp som visas när företagsportalens bakgrund har din valda temafärg. En logotyp måste vara en PNG- eller JPG-fil med en högsta upplösning på 400 × 100 bildpunkter och en största storlek på 750 kB.|
    |Välj en bakgrund för företagsportalappen i [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]|Den här inställningen påverkar bara bakgrunden i [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]-företagsportalappen.|


När du har sparat ändringarna kan du använda länkarna längst ned på sidan **Företagsportal** i administrationskonsolen för att gå till företagsportalen. Dessa länkar kan inte ändras. När en användare loggar in visar dessa länkar dina prenumerationer på företagsportalen.

>[!div class="step-by-step"]

>[&larr; **Skapa principer och appar**](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)       [**Registrera enheter** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)  



<!--HONumber=Feb17_HO3-->


