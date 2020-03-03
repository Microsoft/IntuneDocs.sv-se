---
title: Så här konfigurerar du företagsportalappen
titleSuffix: Microsoft Intune
description: Läs mer om hur du kan använda företagsspecifik anpassning i Intune-företagsportalsappen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c938aba7fde84536af2452f13f6ed030fa1d823
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576431"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Så här konfigurerar du Microsoft Intune-företagsportalappen

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsofts företagsportal för Intune är den plats där användare kan komma åt företagets data och utföra vanliga aktiviteter som att registrera enheter, installera appar och hitta information för att få hjälp från IT-avdelningen. Dessutom ger företagsportalappen användare säker åtkomst till företagets resurser. Företagsportalsappen innehåller flera olika sidor, till exempel hem, appar, appinformation, enheter och enhetsinformation. Om du snabbt vill hitta appar i företagsportalen kan du filtrera apparna på sidan appar.

> [!IMPORTANT]
> För att stödja Googles Firebase Cloud Messaging (FCM) måste du uppdatera din Android-företagsportalapp till den senaste versionen.  

> [!Tip]
> När du anpassar företagsportalen gäller konfigurationerna både företagsportalens webbplats och företagsportalens appar. Observera att användarna måste ha tilldelats en Intune-licens för att få åtkomst till webbplatsen Företagsportal.

Genom att anpassa företagsportalen kan du skapa en välbekant miljö för dina slutanvändare. Det gör du genom att navigera till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), välja **Innehavaradministratör** > **Anpassning** och sedan konfigurera de nödvändiga inställningarna.

När en användare installerar ett iOS/iPadOS-program från företagsportalen får de ett meddelande. Detta inträffar när iOS/iPadOS-appen är länkad till App Store, ett volymköpt program (VPP) eller en verksamhetsspecifik app (LOB). Användaren kan acceptera åtgärden eller tillåta hantering av appen. Meddelandet visar företagets namn. Om företagets namn inte är tillgängligt visas **företagsportalen**. 

> [!Note]
> Om du använder Azure Government har slutanvändarna tillgång till apploggar som hjälper dem att avgöra hur de ska dela när de inleder processen för att få hjälp med ett problem. Om du inte använder Azure Government skickar företagsportalen för Windows 10 apploggar direkt till Microsoft när användaren initierar processen för att få hjälp med ett problem. När apploggarna skickas till Microsoft blir det enklare att felsöka och lösa problem. 

## <a name="company-information-and-privacy-statement"></a>Företagsinformation och sekretesspolicy
Företagsnamnet visas som företagsportalens rubrik. Sekretesspolicyn visas när användaren klickar på sekretesslänken.

| Fältnamn | Högsta längd | Mer information |
|---|---|---|
|**Företagsnamn**| 40 | Det här namnet visas som rubrik i Företagsportalen och visas som text i hela Intune. |
| **URL för sekretesspolicy** |     79     | Du kan ange en egen sekretesspolicy för ditt företag som visas när användaren klickar på en länk på företagsportalen. Du måste ange en giltig URL i formatet `<https://www.contoso.com>`. |

> [!NOTE]
> I enlighet med Microsoft och Apples policy säljer vi inte några data som samlas in av vår tjänst till någon tredje part av någon anledning.

## <a name="support-information"></a>Supportinformation
Ange ditt företags supportinformation så att de anställda har kontaktuppgifter för Intune-relaterade frågor.

|Fältnamn|Högsta längd|Mer information|
|---|---|---|
|**Kontaktnamn** | 40 | Namnet visas på sidan **Hjälp och support**. |
|**Telefonnummer** | 20 | Det här numret visas på sidan **Hjälp och support** så att medarbetarna kan kontakta dig för support. |
|**E-postadress**| 40 | Företagsadressen visas på sidan **Hjälp och support**. Du måste ange en giltig e-postadress i formatet `alias@domainname.com`. |
|**Namn på webbplats**| 40 | Det här är det egna namnet som visas för supportwebbplatsens URL. Om du bara anger URL:en till en supportwebbplats utan något eget namn visas Gå till IT-webbplatsen på sidan **Hjälp och support** på företagsportalen. |
|**Webbplatsens URL**| 150 | Om du har en supportwebbplats som du vill att slutanvändarna ska använda, anger du webbadressen här. Webbadressen måste anges i formatet `https://www.contoso.com`. Om du inte anger någon webbadress kommer inget att visas på sidan **Hjälp och support** på företagsportalen. |
| **Ytterligare information**| 120 | Visas på sidan **Hjälp och support**. |


## <a name="company-identity-branding-customization"></a>Varumärkesanpassning för företagsidentitet
Du kan anpassa företagsportalen med företagets logotyp, företagets namn, temafärg och bakgrund.

### <a name="theme-color-and-logo-in-the-company-portal"></a>Temafärg och logotyp på företagsportalen
Välj en temafärg för företagsportalen. Välj en standardfärg eller ange en hexadecimal sexsiffrig kod för en egen färg.

|Fältnamn|Mer information|
|---|---|
|**Välj en standardfärg eller ange en sexsiffrig hexadecimal kod**| Välj **Standard** om du vill välja en färg genom att klicka på den. Välj **Anpassad** om du vill välja en specifik färg baserat på en hexadecimal kod.|
|**Välj temafärg**| Välj en temafärg som ska användas på företagsportalen. Du kan välja en standardfärg eller ange en specifik hexadecimal kod. |
|**Visning**| Välj om du vill visa **företagslogotypen och företagsnamnet**, **endast företagslogotypen** eller **endast företagsnamnet**. |
|**Ladda upp företagslogotypen**|Du kan överföra företagslogotypen så att den visas på företagsportalen. Observera att textfärgen väljs automatiskt för optimal kontrast. För bäst resultat rekommenderar vi att du laddar upp en logotyp med genomskinlig bakgrund.<p><ul><li>Maximal bildstorlek: 400 x 400 bildpunkter</li><li>Maximal filstorlek: 750 KB</li><li>Filtyp: PNG, JPG eller JPEG</li></ul>|

När du har överfört logotypen visas den med temafärgen i förhandsgranskningsområdet. Om du valde att visa ditt företagsnamn visas det i svart eller vitt på företagsportalen, beroende på vad som ger bäst kontrast baserat på din temafärg. Ditt företagsnamn visas inte i förhandsgranskningsområdet på skärmen. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logotyp som ska användas på vita eller ljusa bakgrunder
Välj en logotyp som ser bäst ut på vita eller ljusa bakgrunder.

|Fältnamn|Mer information|
|---|---|
|**Ladda upp din logotyp**| Det här alternativet är tillgängligt om du har valt att visa företagets logotyp. För bäst resultat rekommenderar vi att du laddar upp en logotyp med genomskinlig bakgrund.<p><ul><li>Maximal bildstorlek: 400 x 400 bildpunkter</li><li>Maximal filstorlek: 750 KB</li><li>Filtyp: PNG, JPG eller JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Varumärkesbild för företagsportalen

Visa en varumärkesbild som återspeglar ditt företags varumärke. När du har sparat ändringarna kan du se hur dina konfigurationer kommer att se ut genom att välja **Förhandsgranska inställningarna** högst upp i fönstret i Intune-portalen. Observera att du bara kan förhandsgranska varumärkesbilden på en iOS/iPadOS-enhet, inte på Intune-webbportalen. 

|Fältnamn|Mer information|
|---|---|
|**Ladda upp din varumärkesbild**| Med det här alternativet kan du visa en bild på ditt varumärke. I företagsportalen för iOS/iPadOS visas den som en bakgrundsbild på användarens profilsida.<p><ul><li>Rekommenderad bildbredd: Större än 1125 pkt (måste vara minst 650 pkt)</li><li>Maximal bildstorlek: 1,3 MB</li><li>Filtyp: PNG, JPG eller JPEG</li></ul>|

Rätt bild kan skapa förtroende och ge en bra bild av ditt varumärke på företagsportalen. Här följer några tips på hur du kan hitta, välja ut och optimera bilden för företagsportalen. 

- Kontakta företagets marknadsförings- eller designavdelning. De kanske redan har en godkänd uppsättning företagsanpassade varumärkesbilder. De kanske också kan hjälpa dig att optimera bilderna om det behövs. 

- Överväg både stående och liggande bilder. Det bör finnas tillräckligt med bakgrund runt bildens mittpunkt. Bilden kan beskäras på olika sätt beroende på enhetens storlek, orientering och plattform. 

- Undvik att använda en generisk bild. Bilden bör återspegla ditt företags varumärke och vara välbekant för användarna. Om du inte har någon bild är det bättre att inte använda någon bild över huvud taget än att använda vilken bild som helst som inte är meningsfull för dina användare. 

- Ta bort onödiga metadata. Bildfilen kan innehålla metadata, till exempel kameraprofil, geografisk plats, rubrik, beskrivning och så vidare. Ta bort den här informationen med hjälp av ett bildoptimeringsverktyg för att upprätthålla kvaliteten och uppfylla storleksgränsen för filer. 

När en varumärkesavbildning läggs till eller ändras i Intune ser slutanvändaren eventuellt inte ändringen på iOS/iPadOS-enheter förrän företagsportalen har identifierat ändringen vid start, och sedan har startats om för att kunna visa varumärkesavbildningen. 

### <a name="brand-image-examples"></a>Exempel på varumärkesavbildning

Följande bild visar ett exempel på en iPad-varumärkesavbildning:

![Skärmbild av en iPhone-varumärkesavbildning](./media/company-portal-app/company-portal-app-03.png)

Följande bild visar ett exempel på en iPhone-varumärkesavbildning:

![Skärmbild av en iPad-varumärkesavbildning](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>Anpassning av sekretesspolicy

Du kan anpassa sekretesspolicyn som visas för din organisation på hanterade iOS/iPadOS-enheter. Det här meddelandet visar de objekt som din organisation inte kan visa eller använda på hanterade iOS/iPadOS-enheter.

Under **Anpassning av företagsportalen** > **Enhetshantering och sekretessaviseringar** kan du:

- Godkänn **Standardinställningen** om du vill använda listan som visas eller
- Välja **Anpassa** om du vill anpassa listan med de objekt som din organisation inte kan visa eller använda på hanterade iOS/iPadOS-enheter. Du kan använda [markdown](https://daringfireball.net/projects/markdown/) för att lägga till punkter, fet stil, kursiv stil och länkar.

## <a name="company-portal-derived-credentials-for-ios-devices"></a>Företagsportal-härledda autentiseringsuppgifter för iOS-enheter
Intune stöder PIV- (Personal Identity Verification) och CAC-härledda (Common Access Card) autentiseringsuppgifter i partnerskap med autentiseringsuppgiftsprovidrarna DISA Purebred, Entrust Datacard och Intercede. Slutanvändare går igenom ytterligare steg efter registreringen av sin iOS/iPadOS-enhet för att verifiera sin identitet i företagsportalappen. Härledda autentiseringsuppgifter aktiveras för användare genom att en autentiseringsuppgiftsprovider först konfigureras för din klientorganisation. Därefter anges en profil som mål som använder härledda autentiseringsuppgifter till användare eller enheter.

> [!NOTE]
> Användaren får instruktioner om härledda autentiseringsuppgifter baserat på den länk som du har angett via Intune.

Mer information om härledda autentiseringsuppgifter för iOS/iPadOS-enheter finns i [Använda härledda autentiseringsuppgifter i Microsoft Intune](~/protect/derived-credentials.md).

## <a name="dark-mode-for-ios-company-portal"></a>Mörkt läge för iOS-företagsportalen

Mörkt läge är tillgängligt för iOS-företagsportalen. Användarna kan ladda ned företagsappar, hantera sina enheter och få IT-support i valfritt färgschema baserat på enhetsinställningarna. iOS-företagsportalen matchar automatiskt slutanvändarens enhetsinställningar för mörkt eller ljust läge. 

## <a name="windows-company-portal-keyboard-shortcuts"></a>Kortkommandon för Windows-företagsportalen

Slutanvändare kan utlösa navigerings-, app- och enhetsåtgärder i Windows-företagsportalen med hjälp av kortkommandon (acceleratorer).

Följande kortkommandon är tillgängliga i Windows-företagsportalappen.

| Område | Beskrivning | Kortkommando |
|:------------------:|:--------------:|:-----------------:|
| Navigeringsmenyn | Navigering | Alt+M |
|  | Hem | Alt+H |
|  | Alla appar | Alt+A |
|  | Installerade appar | Alt+I |
|  | Skicka feedback | Alt+F |
|  | Min profil | Alt+U |
|  | Inställningar | Alt+T |
| Start – Enhetspanel | Byt namn | F2 |
|  | Ta bort | CTRL + D eller ta bort |
|  | Kontrollera åtkomst | CTRL + M eller F9 |
| Information om enhet | Byt namn | F2 |
|  | Ta bort | CTRL + D eller ta bort |
|  | Kontrollera åtkomst | CTRL + M eller F9 |
| Appinformation | Installera | Ctrl + I |
| Egenskaper | Tillgänglig | Ctrl+D |

Slutanvändarna kommer också att kunna se tillgängliga genvägar i Windows-företagsportalens app.

![Skärmbild av tillgängliga genvägar i Windows-företagsportalen](./media/company-portal-app/company-portal-app-01.png)

## <a name="user-self-service-device-actions-from-the-company-portal"></a>Åtgärder för självbetjäningsenhet för användare från företagsportalen

Användare kan utföra åtgärder på sina lokala eller fjärranslutna enheter via företagsportalappen eller -webbplatsen. De åtgärder som en användare kan utföra varierar beroende på enhetens plattform och konfiguration. I samtliga fall kan fjärrenhetsåtgärder endast utföras av enhetens primära användare.
- **Dra tillbaka** – tar bort enheten från Intune-hantering. I appen och webbplatsen för företagsportalen visas detta som **Ta bort**.
- **Rensa** – den här åtgärden startar en återställning av enheten. På företagsportalens webbplats visas detta som **Återställ** eller **Återställ till fabriksinställningar** i företagsportalappen för iOS.
- **Byt namn** – den här åtgärden ändrar enhetsnamnet som användaren kan se i företagsportalen. Namnet ändras inte på den lokala enheten utan endast i företagsportalen.
- **Synkronisera** – den här åtgärden startar en enhetsincheckning med Intune-tjänsten. Detta visas som **Kontrollera status** i företagsportalen.
- **Fjärrlåsning** – detta låser enheten och kräver en PIN-kod för att låsa upp den.
- **Återställ lösenord** – den här åtgärden används för att återställa enhetens lösenord. På iOS/iPadOS-enheter tas lösenordet bort och slutanvändaren måste ange ett nytt lösenord i inställningarna. På Android-enheter som stöds skapas ett nytt lösenord av Intune som visas tillfälligt i företagsportalen.
- **Nyckelåterställning** – Den här åtgärden används för att återställa en personlig återställningsnyckel för krypterade macOS-enheter från företagsportalens webbplats. 

### <a name="self-service-actions"></a>Självbetjäningsåtgärder

Vissa plattformar och konfigurationer tillåter inte självbetjäning av enhetsåtgärder. I tabellen nedan finns mer information om självbetjäningsåtgärder:

|  | Windows 10<sup>(3)</sup> | iOS/iPadOS<sup>(3)</sup> | MacOS<sup>(3)</sup> | Android<sup>(3)</sup> |
|----------------------|--------------------------|-------------------|-----------------------------------|-------------------------|
| Pensionera | Tillgängligt<sup>(1)</sup> | Tillgänglig | Tillgänglig | Tillgängligt<sup>(7)</sup> |
| Rensning | Tillgänglig | Tillgänglig<sup>(5)</sup> | NA | Tillgängligt<sup>(7)</sup> |
| Byt namn <sup>(4)</sup> | Tillgänglig | Tillgänglig | Tillgänglig | Tillgänglig |
| Synkronisera | Tillgänglig | Tillgänglig | Tillgänglig | Tillgänglig |
| Fjärrlåsning | Endast på Windows Phone | Tillgänglig | Tillgänglig | Tillgänglig |
| Återställ lösenord | Endast på Windows Phone | Tillgängligt<sup>(8)</sup> | NA | Tillgängligt<sup>(6)</sup> |
| Nyckelåterställning | NA | NA | Tillgängligt<sup>(2)</sup> | NA |

<sup>(1) </sup> **Dra tillbaka** är alltid blockerat på Azure AD-anslutna Windows-enheter.<br>
<sup>(2) </sup> **Nyckelåterställning** för MacOS är endast tillgängligt via webbportalen.<br>
<sup>(3) </sup> Alla fjärråtgärder inaktiveras om du registrerar med en enhetsregistreringshanterare.<br>
<sup>(4)</sup> **Byt namn** ändrar endast enhetsnamnet i företagsportalappen eller i webbportalen, inte på enheten.<br>
<sup>(5)</sup> **Rensa** är inte tillgängligt på användarregistrerade iOS-enheter.<br>
<sup>(6) </sup> **Återställ lösenord** stöds inte på vissa Android- och Android Enterprise-konfigurationer. För mer information, se [Återställa eller ta bort ett enhetslösenord i Intune](../remote-actions/device-passcode-reset.md).<br>
<sup>(7) </sup> **Dra tillbaka** och **Rensa** är inte tillgängliga i scenarier för Android Enterprise-enhetsägare (COPE, COBO, COSU).<br> 
<sup>(8)</sup> **Återställ lösenord** stöds inte på användarregistrerade iOS-enheter.

## <a name="next-steps"></a>Nästa steg

- [Lägga till appen Företagsportal för Windows 10 manuellt med Microsoft Intune](company-portal-app.md)
