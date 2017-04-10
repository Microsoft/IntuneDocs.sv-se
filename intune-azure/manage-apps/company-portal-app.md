---
title: "Så här konfigurerar du företagsportalappen"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs mer om hur du kan använda företagsspecifik anpassning i företagsportalappen. "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 9ebfadd945916b6be8225b9e07d67100e3f91222
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Så här konfigurerar du Microsoft Intune-företagsportalappen

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsofts företagsportal för Intune är den plats där användare kan komma åt företagets data och utföra vanliga aktiviteter som att registrera enheter, installera appar och hitta information för att få hjälp från IT-avdelningen.

> [!Tip]
> När du anpassar företagsportalen gäller konfigurationerna både företagsportalens webbplats och företagsportalens appar.

Genom att anpassa företagsportalen kan du skapa en välbekant miljö för dina slutanvändare. För att göra det från arbetsbelastningen **Hantera appar** väljer du **Installation** > **Företagsspecifik anpassning i företagsportalappen** och konfigurerar därefter de inställningar som krävs.

## <a name="company-contact-information-and-privacy-statement"></a>Företagets kontaktinformation och sekretesspolicy
Företagsnamnet visas som företagsportalens rubrik. Kontaktuppgifterna och informationen visas för användarna på skärmen **Kontakta IT** på företagsportalen. Sekretesspolicyn visas när användaren klickar på sekretesslänken.


|Fältnamn|Högsta längd|Mer information|
|-|-|-|
|**Företagsnamn**|40|Det här namnet visas som företagsportalens rubrik.|
|**IT-avdelningens kontaktperson**|40|Det här namnet visas på sidan **Kontakta IT-avdelningen**.|
|**IT-avdelningens telefonnummer**|20|Det här numret visas på sidan **Kontakta IT-avdelningen**.|
|IT-avdelningens e-postadress|40|Den här adressen visas på sidan **Kontakta IT-avdelningen**. Du måste ange en giltig e-postadress i formatet **alias@domainname.com**.|
|**Ytterligare information**|120|Visas på sidan **Kontakta IT-avdelningen**.|
|**URL till företagets sekretesspolicy**|79|Du kan ange en egen sekretesspolicy för ditt företag som visas när användaren klickar på en länk på företagsportalen. Du måste ange en giltig URL i formatet **https://www.contoso.com**.|

## <a name="support-contacts"></a>Supportkontakter
Supportwebbplatsen visas för användarna på företagsportalen så att de kan få tillgång till onlinesupport.



|Fältnamn|Högsta längd|Mer information|
|-|-|-|
|**URL till supportwebbplatsen**|150|Om du har en supportwebbplats som du vill att slutanvändarna ska använda, anger du webbadressen här. Den måste anges i formatet **https://www.contoso.com**. Om du inte anger någon webbadress kommer inget att visas på sidan **Kontakta IT** på företagsportalen.|
|**Namn på supportwebbplatsen**|40|Det här är det egna namnet som visas för supportwebbplatsens URL. Om du bara anger URL:en till en supportwebbplats utan något eget namn, visas Gå till IT-webbplatsen på sidan **Kontakta IT** på företagsportalen.

## <a name="company-branding-customization"></a>Varumärkesanpassning
Du kan anpassa företagsportalen med företagets logotyp, företagets namn, temafärg och bakgrund.



|Fältnamn|Mer information|
|-|-|
|**Temafärg**|Välj en temafärg som ska användas på företagsportalen.|
|**Visa företagslogotyp**|Om du aktiverar det här alternativet kan du ladda upp företagets logotyp så att den visas på företagsportalen. Du kan ladda upp två logotyper: en logotyp som visas när företagsportalens bakgrund är vit och en logotyp som visas när företagsportalens bakgrund har din valda temafärg. En logotyp måste vara en PNG- eller JPG-fil med en högsta upplösning på 400 × 100 bildpunkter och en största storlek på 750 kB.<br>Du kan också visa det företagsnamn som du angav bredvid den uppladdade logotypen.|

När du har sparat ändringarna kan du välja **Förhandsgranska inställningarna på Intunes webbportal** för att se hur dina konfigurationer kommer att se ut.

