---
title: Så här konfigurerar du företagsportalappen
titleSuffix: Microsoft Intune
description: Läs mer om hur du kan använda företagsspecifik anpassning i Intune-företagsportalsappen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bd388131445715a4037cc0480c194d338212dbb0
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329981"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Så här konfigurerar du Microsoft Intune-företagsportalappen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsofts företagsportal för Intune är den plats där användare kan komma åt företagets data och utföra vanliga aktiviteter som att registrera enheter, installera appar och hitta information för att få hjälp från IT-avdelningen.        

> [!Tip]        
> När du anpassar företagsportalen gäller konfigurationerna både företagsportalens webbplats och företagsportalens appar.       

Genom att anpassa företagsportalen kan du skapa en välbekant miljö för dina slutanvändare. Du gör det genom att välja **Installation** > **Anpassning av företagsportalen** i arbetsbelastningen **Klientappar** och sedan konfigurera de inställningar som krävs.  

> [!Note]       
> Företagsportalen för Windows 10 kommer nu att skicka apploggar direkt till Microsoft när användaren startar arbetsflödet för att få hjälp med problemet. Detta gör det enklare att felsöka och lösa problem som tas upp till Microsoft.  

## <a name="company-information-and-privacy-statement"></a>Företagsinformation och sekretesspolicy        
Företagsnamnet visas som företagsportalens rubrik. Sekretesspolicyn visas när användaren klickar på sekretesslänken.

Fält som har markerats med en asterisk (*) är obligatoriska.       


| Fältnamn | Högsta längd | Mer information |
|---|---|---|
|**Företagsnamn**| 40 | Det här namnet visas som rubrik i Företagsportalen och visas som text i hela Intune. |
| **URL för sekretesspolicy** |     79     | Du kan ange en egen sekretesspolicy för ditt företag som visas när användaren klickar på en länk på företagsportalen. Du måste ange en giltig URL i formatet `<https://www.contoso.com>`. |

## <a name="support-information"></a>Supportinformation      
Ange ditt företags supportinformation så att de anställda har kontaktuppgifter för Intune-relaterade frågor.       

|Fältnamn|Högsta längd|Mer information|
|---|---|---|
|**Kontaktnamn** | 40 | Det här namnet visas på sidan **Kontakta IT-avdelningen**. |
|**Telefonnummer** | 20 | Det här numret visas på sidan **Kontakta IT** så att medarbetarna kan kontakta dig för support. |
|**E-postadress**| 40 | Den här adressen visas på sidan **Kontakta IT-avdelningen**. Du måste ange en giltig e-postadress i formatet `alias@domainname.com`. |
|**Namn på webbplats**| 40 | Det här är det egna namnet som visas för supportwebbplatsens URL. Om du bara anger URL:en till en supportwebbplats utan något eget namn, visas Gå till IT-webbplatsen på sidan **Kontakta IT** på företagsportalen. |
|**Webbplatsens URL**| 150 | Om du har en supportwebbplats som du vill att slutanvändarna ska använda, anger du webbadressen här. Webbadressen måste anges i formatet `https://www.contoso.com`. Om du inte anger någon webbadress kommer inget att visas på sidan **Kontakta IT** på företagsportalen. |
| **Ytterligare information**| 120 | Visas på sidan **Kontakta IT-avdelningen**. |


## <a name="company-branding-customization"></a>Varumärkesanpassning       
Du kan anpassa företagsportalen med företagets logotyp, företagets namn, temafärg och bakgrund.     

### <a name="theme-color"></a>Temafärg
Välj en temafärg för företagsportalen. Välj en standardfärg eller ange en hexadecimal sexsiffrig kod för en egen färg.

|Fältnamn|Mer information|
|---|---|
|**Färgtyp**| Välj en temafärg som ska användas på företagsportalen. Du kan välja en standardfärg eller ange en specifik hexadecimal kod. |
|**Välj färg** eller **Hexadecimal färgkod**| Välj en temafärg som ska användas på företagsportalen. Du kan välja en standardfärg eller ange en specifik hexadecimal kod. Dessa alternativ är tillgängliga baserat på den **färgtyp** du väljer.  |

### <a name="company-logo"></a>Företagslogotyp
Ladda upp företagets logotyp så att den blir synlig för användarna i Intune.

|Fältnamn|Mer information|
|---|---|
|**Visa företagslogotyp**|Om du aktiverar det här alternativet kan du ladda upp företagets logotyp så att den visas på företagsportalen. Du kan ladda upp två logotyper: en logotyp som visas när företagsportalens bakgrund är vit och en logotyp som visas när företagsportalens bakgrund har din valda temafärg. |
|**Ladda upp en logotyp att använda i bakgrunder med temafärger**| Det här alternativet är tillgängligt om du har valt att visa företagets logotyp. En logotyp måste vara en .png- eller .jpg-fil med en högsta upplösning på 400 × 400 bildpunkter och en största storlek på 750 kB. |
|**Ladda upp en logotyp att använda i ljusa bakgrunder**| Det här alternativet är tillgängligt om du har valt att visa företagets logotyp. En logotyp måste vara en .png- eller .jpg-fil med en högsta upplösning på 400 × 400 bildpunkter och en största storlek på 750 kB. |
|**Visa företagets namn bredvid logotypen**| Välj det här alternativet om du vill visa företagsnamnet du angav bredvid den uppladdade logotypen. |

När du har sparat ändringarna kan du välja **Förhandsgranska inställningarna på Intune Web-portalen** längst upp för att se hur konfigurationen kommer att se ut.
