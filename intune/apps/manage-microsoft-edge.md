---
title: Hantera Microsoft Edge för iOS och Android med Intune
titleSuffix: ''
description: Använd Intunes appskyddsprinciper med Microsoft Edge för att se till att åtkomsten till företagswebbplatser alltid är skyddad.
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
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9622eb33cb4e7732b573e8caf56acf4e3966badb
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609115"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Hantera webbåtkomst med Microsoft Edge med Microsoft Intune

Om du använder Intunes appskyddsprinciper med Microsoft Edge kan du se till att åtkomsten till företagswebbplatser alltid är skyddad. Nedanstående Microsoft Edge-företagsfunktioner som aktiveras med Intune-principer är tillgängliga:

- **Dubbel identitet.** Användarna kan lägga till ett arbetskonto och ett personligt konto för surfning. Det finns en fullständig uppdelning mellan de två identiteterna, vilket liknar arkitektur och funktioner i Office 365 och Outlook. Intune-administratörer kan ställa in de önskade principerna för en skyddad surfupplevelse på arbetskontot.
- **Appskyddsprincipintegration i Intune.** Eftersom Microsoft Edge har integrering med Intune SDK kan du använda appskyddsprinciper för att skydda dem mot dataförlust. De här funktionerna omfattar kontroll av klipp ut, kopiera och klistra in, hindrande av skärmdumpar och säkerställer att länkar som användare väljer endast öppnas i andra hanterade appar.
- **Integrering av en Azure-programproxy.** Du kan styra åtkomsten till programvara som en tjänst (SaaS)-appar och webbappar. Detta garanterar att webbläsarbaserade appar endast körs i den skyddade Microsoft Edge-webbläsaren, oavsett om användarna ansluter från företagets nätverk eller från Internet.
- **Konfiguration av program.** Du kan använda inställningar för programkonfiguration för att förbättra organisationens säkerhetsposition och konfigurera lättanvända funktioner för dina slutanvändare. Du kan till exempel definiera bokmärken, en genväg för startsidan, tillåtna/blockerade webbplatser och Azure Active Directory-programproxy.

Microsoft Intunes skyddsprinciper för Microsoft Edge hjälper till att skydda din organisations data och resurser. Om du använder de här principerna med Microsoft Edge säkerställer det att företagets resurser skyddas, inte bara i internt installerade appar, utan även när de öppnas via en webbläsare.

## <a name="getting-started"></a>Komma igång

Du och slutanvändarna kan ladda ned Microsoft Edge från offentliga appbutiker för användning i företaget. Operativsystemkraven för webbläsarprinciper är något av följande:
- Android 4 och senare
- iOS 8.0 och senare

## <a name="application-protection-policies-for-microsoft-edge"></a>Principer för programskydd för Microsoft Edge

Eftersom Microsoft Edge har integrering med Intune SDK kan du använda appskyddsprinciper för dem.

Du kan tillämpa inställningarna för att:
- Enheter som har registrerats med Intune.
- Enheter som hanteras av en annan lösning för Mobile Device Management.
- Ohanterade enheter.

Om Microsoft Edge inte riktar sig mot en Intune-princip kan inte användare använda det för att komma åt data från andra Intune-hanterade program som Office-appar. 

## <a name="conditional-access-for-microsoft-edge"></a>Villkorlig åtkomst för Microsoft Edge

Du kan använda villkorlig åtkomst för Azure AD för att omdirigera användare så att de endast kommer åt företagets innehåll via Microsoft Edge. Detta begränsar mobil webbläsaråtkomst till Azure AD-anslutna webbappar till principskyddade Microsoft Edge. Detta blockerar åtkomst från andra oskyddade webbläsare, som Safari eller Chrome. Du kan tillämpa villkorlig åtkomst på Azure-resurser som Exchange Online och SharePoint Online, Administrationscenter för Microsoft 365 och även lokala platser som du exponerar för externa användare via [Azure AD-programproxyn](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Så här kan du begränsa Azure AD-anslutna webbappar för att använda Microsoft Edge i iOS och Android:
1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Under Intune-noden väljer du **Villkorlig åtkomst** > **Ny princip**.
3. Välj **Bevilja** i avsnittet **Åtkomstkontroller** i fönstret.
4. Välj **Kräv godkänd klientapp**.
5. Klicka på **Välj** i fönstret **Bevilja**. Den här principen måste tilldelas till de molnappar som du vill ska vara tillgängliga enbart för appen Intune Managed Browser.

    ![Skärmbild för princip för villkorlig åtkomst – Bevilja](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. Välj **Villkor** > **Appar** i avsnittet Tilldelningar. Fönstret **appar** visas.
7. Klicka på **Ja** under **Konfigurera** för att tillämpa principen på specifika klientappar.
8. Kontrollera att **Webbläsare** har valts som klientapp.

    ![Skärmbild på princip för villkorlig åtkomst – Välja klientappar](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Om du vill begränsa vilka interna appar (icke-webbläsarbaserade appar) som har åtkomst till dessa molnprogram kan du också välja **Mobilappar och skrivbordsklienter**.

9. I avsnittet **Tilldelningar** väljer du **Användare och grupper** och sedan de användare eller grupper som du vill tilldela den här principen till.

10. I avsnittet **Tilldelningar** går du till **Molnappar** och väljer vilka appar som ska skyddas med den här principen.

När du har konfigurerat principen ovan tvingas användarna använda Microsoft Edge för att få åtkomst till de Azure AD-anslutna webbappar som du har skyddat med den här principen. Om användarna försöker använda en ohanterad webbläsare i det här scenariot får de ett meddelande om att Microsoft Edge måste användas.

> [!TIP]
> Villkorsstyrd åtkomst är en Azure Active Directory-teknik. Noden för villkorsstyrd åtkomst som nås från Intune är samma nod som den som nås från Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Enkel inloggning till Azure AD-anslutna webbappar i principskyddade webbläsare

Microsoft Edge i iOS och Android kan dra nytta av enkel inloggning (SSO) till alla webbappar (SaaS och lokala) som är Azure AD-anslutna. Med enkel inloggning kan användare få åtkomst till Azure AD-anslutna webbappar via Microsoft Edge utan att behöva ange sina autentiseringsuppgifter på nytt.

Enkel inloggning kräver att din enhet har registrerats av antingen Microsoft Authenticator-appen för iOS-enheter eller på Intune-företagsportalen i Android. När användarna har något av dessa,uppmanas de att registrera sina enheter när de går till en Azure AD-ansluten webbapp i en principskyddad webbläsare. (Detta gäller endast om enheten inte har redan registrerats.) När enheten är registrerad med användarens konto som hanteras av Intune kommer kontot att ha enkel inloggning aktiverat för Azure AD-anslutna webbappar.

> [!NOTE]
> Enhetsregistrering är en enkel incheckning med Azure AD-tjänsten. Det kräver inte fullständig enhetsregistrering och inte ger IT-avdelningen ytterligare behörighet på enheten.

## <a name="create-a-protected-browser-app-configuration"></a>Skapa en appkonfiguration för en skyddad webbläsare

Skapa en appkonfiguration för Microsoft Edge:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Appkonfigurationsprinciper** > **Lägg till**.
3. Gå till fönstret **Lägg till konfigurationsprincip**, ange ett **Namn** och en valfri **Beskrivning** för appkonfigurationsinställningarna.
4. För **Registreringstyp för enhet** väljer du **Hanterade appar**.
5. Välj **Välj den obligatoriska appen**. Gå till fönstret **Målappar** välj **Hanterad webbläsare** eller **Edge** för iOS/iPadOS, Android eller båda.
6. Välj **OK** om du vill gå tillbaka till fönstret **Lägg till konfigurationsprincip**.
7. Välj **Konfigurationsinställningar**. Definiera nyckel- och värdepar för konfigurationerna för Microsoft Edge i fönstret **Konfiguration**. Använd avsnitten senare i den här artikeln för mer information om andra nyckel- och värdepar som du kan definiera.

    > [!NOTE]
    > Microsoft Edge använder samma nyckel/värde-par som Managed Browser. På Android måste appskyddsprinciper vara riktade mot Microsoft Edge för att appkonfigurationsprinciperna ska tillämpas.

8. När du är klar väljer du **OK**.
9. Välj **Lägg till** i fönstret **Lägg till konfigurationsprincip**.<br>
    Den nya konfigurationen skapas och visas i fönstret **Appkonfiguration**.

## <a name="assign-the-configuration-settings-you-created"></a>Tilldela de konfigurationsinställningar som du har skapat 

Du kan tilldela inställningarna till Azure AD-grupper med användare. Om användaren har den aktuella skyddade webbläsaren installerad så hanteras appen med de inställningar du har angett.

1. Välj **Appkonfigurationsprinciper** i fönstret **Appar** på Intunes instrumentpanel för hantering av mobilprogram.
2. Välj den du vill tilldela i listan med appkonfigurationer.
3. Välj **Tilldelningar** i nästa fönster.
4. Välj den Azure AD-grupp vilken du vill tilldela appkonfigurationen i fönstret **Tilldelningar** och välj sedan **OK**.

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Dirigera användarna till Microsoft Edge i stället för Intune Managed Browser 

Både Intune Managed Browser och Microsoft Edge kan nu användas av principskyddade webbläsare. För att säkerställa att dina användare använder rätt webbläsarapp ska du rikta alla Intune-hanterade appar (t.ex. Outlook, OneDrive och SharePoint) med följande konfigurationsinställning:

|    Tangent    |    Värde    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    Värdet `true` uppmanar användarna att hämta och använda Microsoft Edge.<br>Värdet `false` låter användarna att använda Intune Managed Browser.    |

Om den här appens konfigurationsvärde **inte** har angetts definierar följande logik vilken webbläsare som kommer att användas för att öppna företagets länkar.

I Android:
- Intune Managed Browser startas om användaren har både Intune Managed Browser och Microsoft Edge på sin enhet. 
- Microsoft Edge öppnas om enbart Microsoft Edge är nedladdat på enheten och är mål för Intune-principen.
- Managed Browser öppnas bara om det finns på enheten och är mål för Intune-principen.

I iOS/iPadOS, för appar som har integrerat Intune SDK för iOS med 9.0.9+:
- The Intune Managed Browser launches if both the Managed Browser and Microsoft Edge are on the device.  
- Microsoft Edge launches if only Microsoft Edge is on the device, and is targeted with Intune policy.
- Managed Browser öppnas bara om det finns på enheten och är mål för Intune-principen.

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>Konfigurera programproxyinställningar för Microsoft Edge

Microsoft Edge och [Azure AD-programproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) kan användas tillsammans för att ge användare åtkomst till intranätplatser på deras mobila enheter. 

Här är några exempel på scenarier som Azure AD-programproxyn aktiverar: 

- En användare använder Outlook-mobilappen som skyddas av Intune. Användaren klickar på en länk till en intranätplats i ett e-postmeddelande och Microsoft Edge identifierar att den här intranätsplatsen har gjorts tillgänglig för användaren via programproxyn. Användaren omdirigeras automatiskt via programproxyn för att autentisera med alla tillämpliga multifaktorautentiseringar och principer för villkorlig åtkomst innan de når intranätplatsen. Användaren kan nu komma åt interna webbplatser även på sina mobila enheter, och länken i Outlook fungerar som förväntat.
- En användare öppnar Microsoft Edge på sin iOS- eller Android-enhet. Om Microsoft Edge skyddas med Intune och programproxyn är aktiverad kan du gå till en intranätplats med den interna URL:en som brukar användas. Microsoft Edge identifierar att den här intranätsplatsen har gjorts tillgänglig för användaren med programproxyn. Användaren omdirigeras automatiskt via programproxyn för att autentisera innan de når intranätplatsen. 

### <a name="before-you-start"></a>Innan du börjar

- Konfigurera dina interna program via Azure AD-programproxyn.
  - Se [installationsdokumentationen](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) för att konfigurera programproxy och publicera program.
- Microsoft Edge-appen måste ha [Intunes appskyddsprincip](app-protection-policy.md) tilldelad.

> [!NOTE]
> Det kan ta upp till 24 timmar innan omdirigeringsdata för en uppdaterad programproxy börjar gälla i Managed Browser eller Microsoft Edge.

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>Steg 1: Aktivera automatisk omdirigering till Microsoft Edge från Outlook
Konfigurera Outlook med en appskyddsprincip som aktiverar inställningen **Dela webbinnehåll med principhanterade webbläsare**.

![Skärmbild på appskyddsprincip – Dela webbinnehåll med principhanterade webbläsare](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Steg 2: Ställ in appkonfigurationsinställningen för att aktivera programproxy
Rikta nyckel-/värdeparet nedan för Microsoft Edge för att aktivera programproxyn för Microsoft Edge:

|    Tangent    |    Värde    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Mer information om hur du kan använda Microsoft Edge och en Azure AD-programproxy tillsammans för sömlös (och skyddad) åtkomst till lokala webbappar finns i [Bättre tillsammans: Intune och Azure Active Directory samarbetar för att förbättra användaråtkomsten](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access). Det här blogginlägget hänvisar till Intune Managed Browser, men innehållet gäller även för Microsoft Edge.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>Konfigurera en genväg på startsidan för Microsoft Edge

Med den här inställningen kan du konfigurera en genväg på startsidan för Microsoft Edge. Genvägen till webbsidan som du konfigurerar visas som den första ikonen under sökfältet när du öppnar en ny flik i Microsoft Edge. Användaren kommer inte att kunna redigera eller ta bort den här genvägen i sin hanterade kontext. Genvägen till startsidan visar namnet på din organisation för att särskilja den. 

Använd nyckel-/värdeparet nedan för att konfigurera en genväg på startsidan:

|    Tangent    |    Värde    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Ange en giltig URL. Felaktiga URL:er är blockerade som en säkerhetsåtgärd.<br>**Exempel:**  <`https://www.bing.com`>

## <a name="configure-your-organizations-logo-and-brand-color-for-new-tab-pages-in-microsoft-edge"></a>Konfigurera din organisations logotyp och varumärkesfärg för nya flikar i Microsoft Edge

Med de här inställningarna kan du anpassa sidan Ny flik för Microsoft Edge och visa din organisations logotyp och varumärkesfärg som sidbakgrund.

För att ladda upp organisationens logotyp och färg utför du först följande steg:
- I Azure-portalen navigerar du till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) -> **Innehavaradministratör** -> **Anpassning** -> **Company Identity Branding** (Företagsanpassning).
- Om du vill ange ditt varumärkes logotyp, väljer du ”Enbart företagslogotyp”under ”Visa”. Transparenta bakgrundslogotyper rekommenderas. 
- Om du vill ange bakgrundsfärg för ditt varumärke väljer du ”Temafärg”under ”Visa”. Microsoft Edge använder en ljusare nyans av färgen på sidan Ny flik, vilket gör att sidan har hög läsbarhet. 

Använd sedan följande nyckel-/värdepar för att hämta dina organisationers varumärken till Microsoft Edge:

|    Tangent    |    Värde    |
|--------------------------------------------------------------------|------------|
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandLogo    |    Sant    |
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandColor    |    Sant    |

## <a name="display-relevant-industry-news-on-new-tab-pages"></a>Visa relevanta branschnyheter på sidan Ny flik

Du kan konfigurera upplevelsen på sidan Ny flik i Microsoft Edge Mobile så att den visar branschnyheter som är relevanta för din organisation. När du aktiverar den här funktionen använder Microsoft Edge Mobile din organisations domännamn för att samla nyheter från webben om din organisation, organisationens bransch och konkurrenter, så att användarna kan hitta relevanta externa nyheter från den centrala sidan Ny flik i Microsoft Edge. Branschnyheter är inaktiverat som standard och du kan välja till det alternativet för din organisation. 

|    Tangent    |    Värde    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.ShowIndustryNews    |    **Sant** visar branschnyheter på sidan Ny flik i Microsoft Edge Mobile.<p>**Falskt** (standard) döljer branschnyheter från sidan Ny flik.    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Konfigurera hanterade bokmärken för Microsoft Edge

För enkel åtkomst kan du konfigurera bokmärken som du vill att användarna har tillgängliga när de använder Microsoft Edge. 

Här följer lite information:

- De här bokmärkena visas endast för användare när de använder [företagsläget](https://docs.microsoft.com/intune/apps/app-configuration-managed-browser#how-to-configure-bookmarks-for-a-protected-browser) för Microsoft Edge. 
- De här bokmärkena kan inte tas bort eller ändras av användare.
- De här bokmärkena visas överst i listan. Alla bokmärken som användare skapar visas under de här bokmärkena.
- Om du har aktiverat omdirigering av Application Proxy kan du lägga till Application Proxy-webbappar med antingen deras interna eller externa URL-adress.
- Lägg till prefixet **http://** eller **https://** till alla URL:er när du lägger till dem i listan.

Använd följande nyckel/värde-par för att konfigurera hanterade bokmärken:

|    Tangent    |    Värde    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    Värdet för den här konfigurationen är en lista över bokmärken. Varje bokmärke består av bokmärkets rubrik och bokmärkets URL. Avgränsa rubriken och URL:en med tecknet `|`.      Exempel:<br>`Microsoft Bing|https://www.bing.com`<br>Om du vill konfigurera fler bokmärken avgränsar du varje par med två tecken `||`.<p>Exempel:<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>Visa MyApps i Microsoft Edge-bokmärken

Som standard får användarna se MyApps-platser som är konfigurerade för dem i en mapp i Microsoft Edge-bokmärkena. Mappen är märkt med namnet på din organisation.

|    Tangent    |    Värde    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **Sant** visar MyApps i Microsoft Edge-bokmärkena.<p>**Falskt** döljer MyApps i Microsoft Edge.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Ange listan med tillåtna eller blockerade platser för Microsoft Edge
Du kan använda appkonfiguration för att definiera vilka webbplatser användarna ska komma åt när de använder sin arbetsprofil. Om du använder en lista över tillåtna kan användarna bara komma åt webbplatserna som du uttryckligen har angett. Om du använder en lista över blockerade får användarna åtkomst till alla platser utom de platser som du uttryckligen har blockerat. Du bör endast införa antingen listan över tillåtna eller blockerade listan, inte båda. Om du inför båda kommer listan över tillåtna att respekteras.  

Använd nyckel/värde-paren nedan för att konfigurera en lista över tillåtna eller blockerade webbplatser för Microsoft Edge. 

|    Tangent    |    Värde    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Välj mellan:<p>1. Ange tillåtna URL:er (endast dessa URL:er tillåts, inga andra webbplatser kan nås):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Ange blockerade URL: er (alla andra platser kan nås):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    Motsvarande värde för nyckeln är en lista med URL:er. Du anger alla URL:er som du vill tillåta eller blockera som ett enda värde, avgränsade med ett vertikalstreck `|`.<br>**Exempel:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>URL-format för listan över tillåtna och blockerade webbplatser 
Du kan använda olika URL-format för att skapa dina webbplatslistor med tillåtna/blockerade. De här tillåtna mönstren beskrivs i tabellen nedan. Lite information innan du sätter igång: 
- Lägg till prefixet **http://** eller **https://** till alla URL:er när du lägger till dem i listan.
- Du kan använda jokertecknet (\*) enligt reglerna i följande lista med tillåtna mönster.
- Ett jokertecken kan endast motsvara hela värdnamnet (avgränsat med punkter) eller hela delar av sökvägen (avgränsade med snedstreck). `http://*contoso.com` och  **stöds till exempel inte**.
- Du kan ange portnummer i adressen. Om du inte anger ett portnummer, används följande värden:
  - Port 80 för http
  - Port 443 för http
- Jokertecken i portnummer stöds **inte**. `http://www.contoso.com:*` och `http://www.contoso.com:*/` stöds inte. 

    |    URL    |    Information    |    Matchar    |    Matchar inte    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Matchar en enstaka sida    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Matchar en enstaka sida    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/*;`   |    Matchar alla URL:er som börjar med `www.contoso.com`    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Matchar alla underordnade domäner under `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`
    |    `http://*contoso.com/*`    |    Matchar alla underordnade som slutar med `contoso.com/`    |    `http://news-contoso.com`<br>`http://news-contoso.com.com/daily`    |    `http://news-contoso.host.com`    |
    `http://www.contoso.com/images`    |    Matchar en enstaka mapp    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Matchar en enstaka sida, med ett portnummer    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    Matchar en enstaka, säker sida    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Matchar en enstaka mapp och alla undermappar    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- Följande är några exempel på indata som du inte kan ange:
  - `*.com`
  - `*.contoso/*`
  - `www.contoso.com/*images`
  - `www.contoso.com/*images*pigs`
  - `www.contoso.com/page*`
  - IP-adresser
  - `https://*`
  - `http://*`
  - `https://*contoso.com`
  - `http://www.contoso.com:*`
  - `http://www.contoso.com: /*`

## <a name="transition-users-to-their-personal-context-when-trying-to-access-a-blocked-site"></a>Överföra användare till deras personliga sammanhang när de försöker komma åt en blockerad webbplats

Du kan skapa en mer flexibel upplevelse för slutanvändarna som inte var möjligt med Intune Managed Browser med modellen med dubbla identiteter som är inbyggda i Microsoft Edge. När användare trycker på en plats som är blockerad i Microsoft Edge kan du uppmana dem att öppna länken i den personliga kontexten i stället för arbetskontexten. Därmed skyddas de och företagets resurser samtidigt. Till exempel om en användare får en länk till en nyhetsartikel via Outlook kan de öppna länken i sin personliga kontext eller i en InPrivate-flik. Arbetskontexten tillåter inte nyhetswebbplatser. Dessa övergångar tillåts som standard.

Använd nyckel-/värdeparet nedan för att konfigurera om dessa mjuka övergångar ska tillåtas:

|    Tangent    |    Värde    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    Värdet **true** (standard) tillåter att Microsoft Edge överför användare till deras personliga kontext för att öppna blockerade webbplatser.<p>**Falskt** förhindrar att Microsoft Edge överför användare. Användare får helt enkelt se ett meddelande om att webbplatsen de försöker besöka är blockerad.    |

## <a name="open-restricted-links-directly-in-inprivate-tab-pages"></a>Öppna begränsade länkar direkt på InPrivate-flikar

Du kan konfigurera så att begränsade länkar ska öppnas direkt med InPrivate-surfning, vilket ger användarna en smidigare webbupplevelse. Då slipper användarna steget med övergången till deras personliga sammanhang för att visa en webbplats. InPrivate-surfning betraktas som ohanterat, så användarna kan inte komma åt det när de använder läget för InPrivate-surfning.

|    Tangent    |    Värde    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.openInPrivateIfBlock`    |    Värdet **true** öppnar automatiskt webbplatser direkt i en InPrivate-flik, utan att uppmana användaren att växla till sitt personliga konto. <p> Värdet **false** (standard) blockerar webbplatsen i Microsoft Edge, och användaren uppmanas att växla till sitt personliga konto för att kunna visa den.    |

## <a name="disable-microsoft-edge-features-to-customize-the-end-user-experience-for-your-organizations-needs"></a>Inaktivera Microsoft Edge-funktioner för att anpassa slutanvändarens upplevelse till organisationens behov

### <a name="disable-prompts-to-share-usage-data-for-personalization"></a>Inaktivera frågor om delning av användningsdata för personanpassning 

Som standard frågar Microsoft Edge användare om insamling av användningsdata för att personanpassa deras surfupplevelse. Du kan inaktivera delning av dessa data genom att förhindra att denna fråga visas för slutanvändarna. 

|    Tangent    |    Värde    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.disableShareUsageData`    |     Värdet **true** inaktiverar frågan så att den inte visas för slutanvändarna.    |

### <a name="disable-prompts-to-share-browsing-history"></a>Inaktivera frågor om delning av webbhistorik 

Som standard frågar Microsoft Edge användare om insamling av webbhistorik för att personanpassa deras surfupplevelse. Du kan inaktivera delning av dessa data genom att förhindra att denna fråga visas för slutanvändarna.

|    Tangent    |    Värde    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     `com.microsoft.intune.man.managedbrowser.disableShareBrowsingHistory`    |     Värdet **true** inaktiverar frågan så att den inte visas för slutanvändarna.     |

### <a name="disable-prompts-that-offer-to-save-passwords"></a>Inaktivera frågor om att spara lösenord
Som standard erbjuder Microsoft Edge för iOS att spara dina användares lösenord i nyckelringen. Om du vill inaktivera frågan för din organisation konfigurerar du följande inställning:

|    Tangent    |    Värde    |
|-----------------------|-----------------------|
|    `com.microsoft.intune.mam.managedbrowser.disableFeatures`    |    Värdet **password** inaktiverar frågor om att spara lösenord åt slutanvändaren.    |

### <a name="disable-inprivate-browsing-and-microsoft-accounts-to-restrict-browsing-to-work-only-contexts"></a>Inaktivera InPrivate-surfning och Microsoft-konton för att begränsa surfningen till enbart arbetskontexter

Om din organisation arbetar inom en starkt reglerad bransch eller använder Per app-VPN för att ge användare åtkomst till arbetsresurser med Microsoft Edge, kan du välja att begränsa användningen av Microsoft Edge till endast en MAM-skyddad kontext. Den här funktionen tillhandahålls endast för MDM-registrerade enheter.

|    Tangent    |    Värde    |
|-----------|-------------|
|    `com.microsoft.intune.mam.managedbrowser.disableFeatures`    |    Värdet **inprivate** inaktiverar InPrivate-surfning. <br> Värdet **msa** blockerar användare från att lägga till sina personliga Microsoft-konton (MSA) i Microsoft Edge-apparna. <br> Om du vill inaktivera flera funktioner kan du separera värden med `|`. `inprivate|msa` blockerar till exempel både InPrivate och personliga konton.   |

### <a name="restrict-microsoft-edge-use-to-allowed-accounts-only"></a>Begränsa Microsoft Edge-användningen till endast tillåtna konton

Förutom att blockera InPrivate- och MSA-surfning kan du välja att endast tillåta användning av Microsoft Edge när användaren är inloggad med sitt AAD-konto. Den här funktionen är endast tillgänglig för MDM-registrerade enheter. Här kan du lära dig mer om hur du konfigurerar den här inställningen:

- [Android-inställning](~/apps/app-configuration-policies-use-android.md#allow-only-configured-organization-accounts-in-multi-identity-apps)
- [iOS-inställning](~/apps/app-configuration-policies-use-ios.md#allow-only-configured-organization-accounts-in-multi-identity-apps)


## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Använda Microsoft Edge i iOS för att komma åt loggar för hanterade appar 

Användare med Microsoft Edge installerat på sina iOS-enheter kan se hanteringsstatus för alla appar som har publicerats av Microsoft. De kan skicka loggar för felsökning av deras hanterade iOS-appar. Så här gör du:
1. Öppna Microsoft Edge på din iOS-enhet.
2. Skriv in `about:intunehelp` i adressrutan. 
3. Microsoft Edge startar felsökningsläget.

En lista över de inställningar som finns lagrade i apploggarna finns i [granska appskyddsloggarna i Managed Browser](app-protection-policy-settings-log.md).

Mer information om hur du visar loggar på Android-enheter finns i [Skicka loggar till IT-administratören via e-post](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Säkerhet och sekretess för Microsoft Edge

Följande är ytterligare överväganden för säkerhet och sekretess för Microsoft Edge:

- Microsoft Edge använder inte inställningar som användare anger för den inbyggda webbläsaren https://docs.microsoft.com/en-us/intune/apps/app-configuration-policies-use-android#allow-only-configured-organization-accounts-in-multi-identity-apps på sina enheter, eftersom Microsoft Edge inte har åtkomst till de här inställningarna.
- Du kan konfigurera alternativet **Kräv enkel PIN-kod för åtkomst** eller **Kräv företagets autentiseringsuppgifter för åtkomst** i en appskyddsprincip som är associerad med Microsoft Edge. Om en användare väljer hjälplänken på autentiseringssidan kan de besöka alla webbplatser, oavsett om de har lagts till i en lista över blockerade webbplatser i principen.
- Microsoft Edge kan endast blockera åtkomst till webbplatser när de öppnas direkt. Den blockerar inte åtkomst när användare använder mellanliggande tjänster (till exempel en översättningstjänst) för åtkomst till webbplatsen.
- För att tillåta autentisering och få åtkomst till Intune-dokumentationen är ***microsoft.com** undantaget från listan Tillåt eller blockera. Detta tillåts alltid.
- Användare kan inaktivera datainsamling. Microsoft samlar automatiskt in anonyma data om prestanda och användning av Managed Browser för att kunna förbättra Microsofts produkter och tjänster. Användare kan stänga av insamling av data med hjälp av inställningen **Användningsdata** på sina enheter. Du har ingen kontroll över insamlingen av dessa data. Webbplatser som har ett utgånget eller ej betrott certifikat kan inte öppnas på iOS-enheter.

## <a name="next-steps"></a>Nästa steg

- [Vad är appskyddsprinciper?](app-protection-policy.md) 
