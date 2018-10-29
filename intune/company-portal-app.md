---
title: Så här konfigurerar du företagsportalappen
titleSuffix: Microsoft Intune
description: Läs mer om hur du kan använda företagsspecifik anpassning i Intune-företagsportalsappen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 01de402a48362f04680c569c40a812b6a4b83cc6
ms.sourcegitcommit: 38afcff149f9c86e92e5f1eccaa927859c395926
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307414"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Så här konfigurerar du Microsoft Intune-företagsportalappen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsofts företagsportal för Intune är den plats där användare kan komma åt företagets data och utföra vanliga aktiviteter som att registrera enheter, installera appar och hitta information för att få hjälp från IT-avdelningen.        

> [!Tip]        
> När du anpassar företagsportalen gäller konfigurationerna både företagsportalens webbplats och företagsportalens appar.       

Genom att anpassa företagsportalen kan du skapa en välbekant miljö för dina slutanvändare. Du gör det genom att välja **Installation** > **Anpassning av företagsportalen** i arbetsbelastningen **Klientappar** och sedan konfigurera de inställningar som krävs.  

> [!Note]       
> Om du använder Azure Government har slutanvändarna tillgång till apploggar som hjälper dem att avgöra hur de ska dela när de inleder processen för att få hjälp med ett problem. Om du inte använder Azure Government skickar företagsportalen för Windows 10 apploggar direkt till Microsoft när användaren initierar processen för att få hjälp med ett problem. När apploggarna skickas till Microsoft blir det enklare att felsöka och lösa problem. 

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
Du kan anpassa företagsportalen med företagets logotyp, företagets namn, temafärg och bakgrund. För att snabbt förhandsgranska konfigurerad företagsanpassning utan en testenhet, kan du gå till [portal.manage.microsoft.com](https://portal.manage.microsoft.com). Observera att den logotyp du överför kommer att användas för e-postmallar.      

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

## <a name="windows-company-portal-keyboard-shortcuts"></a>Kortkommandon för Windows-företagsportalen

Slutanvändare kan utlösa app- och enhetsåtgärder i Windows-företagsportalen med hjälp av kortkommandon (acceleratorer).

Följande kortkommandon är tillgängliga i Windows-företagsportalappen.

| Område | Beskrivning | Kortkommando |
|:------------------:|:--------------:|:-----------------:|
| Navigeringsmenyn | Navigering | Alt + M |
|  | Hem | Alt + H |
|  | Alla appar | Alt + A |
|  | Installerade appar | Alt+I |
|  | Skicka feedback | Alt + F |
|  | Min profil | Alt + U |
|  | Inställningar | Alt + T |
| Start – Enhetspanel | Byt namn | F2 |
|  | Ta bort | CTRL + D eller ta bort |
|  | Kontrollera åtkomst | CTRL + M eller F9 |
| Information om enhet | Byt namn | F2 |
|  | Ta bort | CTRL + D eller ta bort |
|  | Kontrollera åtkomst | CTRL + M eller F9 |
| Appinformation | Installera | Ctrl + I |

## <a name="next-steps"></a>Nästa steg

- [Lägga till appen Företagsportal för Windows 10 manuellt med Microsoft Intune](store-apps-company-portal-app.md)