---
title: Så här konfigurerar du företagsportalappen
titleSuffix: Microsoft Intune
description: Läs mer om hur du kan använda företagsspecifik anpassning i Intune-företagsportalsappen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aed2bec6e6fea40fdbd78bc487896d167d036f06
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Så här konfigurerar du Microsoft Intune-företagsportalappen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsofts företagsportal för Intune är den plats där användare kan komma åt företagets data och utföra vanliga aktiviteter som att registrera enheter, installera appar och hitta information för att få hjälp från IT-avdelningen.        

> [!Tip]        
> När du anpassar företagsportalen gäller konfigurationerna både företagsportalens webbplats och företagsportalens appar.       

Genom att anpassa företagsportalen kan du skapa en välbekant miljö för dina slutanvändare. Du gör det genom att välja **Installation** > **Anpassning av företagsportalen** på arbetsbelastningen **Mobila appar**  och konfigurera sedan de inställningar som krävs.      

## <a name="company-contact-information-and-privacy-statement"></a>Företagets kontaktinformation och sekretesspolicy        
Företagsnamnet visas som företagsportalens rubrik. Kontaktuppgifterna och informationen visas för användarna på skärmen **Kontakta IT** på företagsportalen. Sekretesspolicyn visas när användaren klickar på sekretesslänken.        


|                   Fältnamn                   | Högsta längd |                                                                                                 Mer information                                                                                                 |
|------------------------------------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         <strong>Företagsnamn</strong>          |     40     |                                                                            Det här namnet visas som företagsportalens rubrik.                                                                            |
|  <strong>IT-avdelningens kontaktperson</strong>   |     40     |                                                                         Det här namnet visas på sidan <strong>Kontakta IT-avdelningen</strong>.                                                                          |
|  <strong>IT-avdelningens telefonnummer</strong>   |     20     |                                                                    Det här numret visas på sidan <strong>Kontakta IT-avdelningen</strong>.                                                                     |
|  <strong>IT-avdelningens e-postadress</strong>  |     40     |                       Den här adressen visas på sidan <strong>Kontakta IT-avdelningen</strong>. Du måste ange en giltig e-postadress i formatet <strong>alias@domainname.com</strong>.                       |
|    <strong>Ytterligare information</strong>     |    120     |                                                                                Visas på sidan <strong>Kontakta IT-avdelningen</strong>.                                                                                |
| <strong>URL till företagets sekretesspolicy</strong> |     79     | Du kan ange en egen sekretesspolicy för ditt företag som visas när användaren klickar på en länk på företagsportalen. Du måste ange en giltig URL i formatet <strong><https://www.contoso.com></strong>. |

## <a name="support-contacts"></a>Supportkontakter     
Supportwebbplatsen visas för användarna på företagsportalen så att de kan få tillgång till onlinesupport.        



|Fältnamn|Högsta längd|Mer information|        
|-|-|-|     
|**URL till supportwebbplatsen**|150|Om du har en supportwebbplats som du vill att slutanvändarna ska använda, anger du webbadressen här. Webbadressen måste anges i formatet **https://www.contoso.com**. Om du inte anger någon webbadress kommer inget att visas på sidan **Kontakta IT** på företagsportalen.|        
|**Namn på supportwebbplatsen**|40|Det här är det egna namnet som visas för supportwebbplatsens URL. Om du bara anger URL:en till en supportwebbplats utan något eget namn, visas Gå till IT-webbplatsen på sidan **Kontakta IT** på företagsportalen.       

## <a name="company-branding-customization"></a>Varumärkesanpassning       
Du kan anpassa företagsportalen med företagets logotyp, företagets namn, temafärg och bakgrund.     



|Fältnamn|Mer information|       
|-|-|       
|**Temafärg**|Välj en temafärg som ska användas på företagsportalen. Du kan välja i färgväljaren eller ange en specifik hexkod.|      
|**Visa företagslogotyp**|Om du aktiverar det här alternativet kan du ladda upp företagets logotyp så att den visas på företagsportalen. Du kan ladda upp två logotyper: en logotyp som visas när företagsportalens bakgrund är vit och en logotyp som visas när företagsportalens bakgrund har din valda temafärg. En logotyp måste vara en PNG- eller JPG-fil med en högsta upplösning på 400 × 100 bildpunkter och en största storlek på 750 kB.<br>Du kan också visa det företagsnamn som du angav bredvid den uppladdade logotypen.|      

När du har sparat ändringarna kan du välja **Förhandsgranska inställningarna på Intunes webbportal** för att se hur dina konfigurationer kommer att se ut.
