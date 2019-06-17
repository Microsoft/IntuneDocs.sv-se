---
title: Hantera webbåtkomst med Microsoft Edge med Microsoft Intune
titleSuffix: ''
description: Använd Intunes appskyddsprinciper med Microsoft Edge för att se till att åtkomsten till företagswebbplatser alltid är skyddad.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c1a255391a2cf27a764da6122031fd0c9cbb64cf
ms.sourcegitcommit: cb76efd3db60a422a65478ebce83d3aea7b5eeed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751365"
---
# <a name="manage-web-access-using-microsoft-edge-with-microsoft-intune"></a>Hantera webbåtkomst med Microsoft Edge med Microsoft Intune

Om du använder Intunes appskyddsprinciper med Microsoft Edge kan du se till att åtkomsten till företagswebbplatser alltid är skyddad. Nedanstående Microsoft Edge-företagsfunktioner som aktiveras med Intune-principer är tillgängliga. Dessa företagsfunktioner är:

1.  **Dubbel identitet** – Användarna kan lägga till både ett arbetskonto och ett personligt konto för surfning. Det finns en fullständig uppdelning mellan de två identiteterna, vilket liknar arkitektur och funktioner i Office 365 och Outlook. Intune-administratörer kommer att kunna ställa in de önskade principerna för en skyddad surfupplevelse på arbetskontot.
2.  **Integrering med appskyddsprincip i Intune** – eftersom Microsoft Edge är integrerat med Intune SDK kan du rikta appskyddsprinciper för att garanterat få skydd mot dataförlust. De här funktionerna omfattar kontroll av klipp ut, kopiera och klistra in, hindrande av skärmdumpar och säkerställer att länkar som användare väljer endast öppnas i andra hanterade appar.
3.  **Integrering med Azure Application-proxy** – Du kan styra åtkomsten till SaaS-appar och webbappar, vilket garanterar att webbläsarbaserade appar endast körs i den skyddade Microsoft Edge-webbläsaren, oavsett om användarna ansluter från företagets nätverk eller från Internet.
4.  **Programkonfiguration** – Du kan använda inställningar för programkonfiguration för att förbättra organisationens säkerhetsposition och konfigurera lättanvända funktioner för dina slutanvändare. Du kan till exempel definiera bokmärken, en genväg för startsidan, tillåtna/blockerade webbplatser, Azure-programproxy med mera.
Microsoft Intunes skyddsprinciper för Microsoft Edge hjälper till att skydda din organisations data och resurser. Om du använder de här principerna med Microsoft Edge säkerställer det att företagets resurser skyddas, inte bara i internt installerade appar, utan även när de öppnas via en webbläsare.

## <a name="getting-started"></a>Komma igång

Du och slutanvändarna kan ladda ned Microsoft Edge från offentliga appbutiker för användning i företaget. Operativsystemkrav för webbläsarprinciper:
- Android 4 och senare eller
- iOS 8.0 och senare

## <a name="application-protection-policies-for-microsoft-edge"></a>Principer för programskydd för Microsoft Edge

Eftersom Microsoft Edge har integrering med Intune SDK kan du använda appskyddsprinciper för dem, som att:
- Styra användningen av klipp ut, kopiera och klistra in.
- Förhindra skärmdumpar.
- Säkerställa att företagets länkar bara öppnas i hanterade appar och webbläsare.

Mer information finns i Vad är appskyddsprinciper?
Du kan tillämpa inställningarna för att:
- Enheter som har registrerats med Intune
- Registrerade med en annan MDM-produkt
- Ohanterade enheter

Om Microsoft Edge inte riktar sig mot en Intune-princip kan inte användare använda det för att komma åt data från andra Intune-hanterade program som Office-appar. 

## <a name="conditional-access-for-microsoft-edge"></a>Villkorlig åtkomst för Microsoft Edge

Du kan använda villkorlig åtkomst för Azure AD för att omdirigera användare så att de endast kommer åt företagets innehåll via Microsoft Edge. Det begränsar mobil webbläsaråtkomst till Azure AD-anslutna webbappar till principskyddade Microsoft Edge, vilket blockerar åtkomsten från andra oskyddade webbläsare som Safari eller Chrome. Villkorlig åtkomst kan tillämpas på Azure-resurser som Exchange Online och SharePoint Online, Administrationscenter för Microsoft 365 och även lokala platser som du exponerar för externa användare via [Azure AD-programproxyn](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Om du vill begränsa Azure AD-anslutna webbappar för att använda Microsoft Edge i iOS och Android följer du stegen nedan:
1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Under Intune-noden väljer du **Villkorsstyrd åtkomst** > **Ny princip**.
3. Välj därefter **Bevilja** i avsnittet **Åtkomstkontroller** på bladet.
4. Klicka på **Kräv godkänd klientapp**.
5. Klicka på **Välj** på bladet **Bevilja**. Den här principen måste tilldelas till de molnappar som du vill ska vara tillgängliga enbart för appen Intune Managed Browser.

    ![Princip för villkorlig åtkomst – Bevilja](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. I avsnittet Tilldelningar väljer du Villkor > Klientappar. Bladet Klientappar visas.
7. Klicka på Ja under Konfigurera för att tillämpa principen på specifika klientappar.
8. Kontrollera att Webbläsare har valts som klientapp.

    ![Princip för villkorlig åtkomst – Välja klientappar](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Om du vill begränsa vilka interna appar (icke-webbläsarbaserade appar) som har åtkomst till dessa molnprogram kan du också välja **Mobilappar och skrivbordsklienter**.

9. I avsnittet **Tilldelningar** väljer du **Användare och grupper** och sedan de användare eller grupper som du vill tilldela den här principen till.

    > [!NOTE]
    > Användarna måste också använda principen Intune-appskydd för att kunna ta emot principer för appkonfiguration. Mer information om att skapa Intune-appskyddsprinciper finns i [Vad är appskyddsprinciper?](app-protection-policy.md)

10. I avsnittet **Tilldelningar** går du till **Molnappar** och väljer vilka appar som ska skyddas med den här principen.

När du har konfigurerat principen ovan tvingas användarna använda Microsoft Edge för att få åtkomst till de Azure AD-anslutna webbappar som du har skyddat med den här principen. Om användarna försöker använda en ohanterad webbläsare i det här scenariot visas ett meddelande om att Microsoft Edge måste användas.

> [!TIP]
> Villkorsstyrd åtkomst är en Azure Active Directory-teknik (Azure AD). Noden för villkorsstyrd åtkomst som nås från Intune är samma nod som den som nås från Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Enkel inloggning till Azure AD-anslutna webbappar i principskyddade webbläsare

Microsoft Edge i iOS och Android kan dra nytta av enkel inloggning till alla webbappar (SaaS och lokala) som är Azure AD-anslutna. Med enkel inloggning kan användare få åtkomst till Azure AD-anslutna webbappar via Microsoft Edge utan att behöva ange sina autentiseringsuppgifter på nytt.

Enkel inloggning kräver att din enhet har registrerats av antingen Microsoft Authenticator-appen för iOS-enheter eller på Intune-företagsportalen i Android. När användare har Authenticator-appen eller Intune-företagsportalen uppmanas de att registrera sin enhet när de navigerar till en Azure AD-ansluten webbapp i en principskyddad webbläsare, om enheten inte redan har registrerats. När enheten är registrerad med användarens konto som hanteras av Intune kommer kontot att ha enkel inloggning aktiverat för Azure AD-anslutna webbappar.

> [!NOTE]
> Enhetsregistrering är en enkel incheckning med Azure AD-tjänsten. Det kräver inte fullständig enhetsregistrering och inte ger IT-avdelningen ytterligare behörighet på enheten.

## <a name="create-a-protected-browser-app-configuration"></a>Skapa en appkonfiguration för en skyddad webbläsare

För att appkonfigurationer ska tillämpas så måste den användarskyddade webbläsaren eller en annan app på enheten redan hanteras av [Intunes appskyddsprincip](app-protection-policy.md).

Följande steg används för att skapa en konfiguration av skyddade webbläsare:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Klientappar** > **Appkonfigurationsprinciper** > **Lägg till**.
3. På bladet **Lägg till konfigurationsprincip** anger du ett **Namn** och en valfri **Beskrivning** för appkonfigurationsinställningarna.
4. För **Registreringstyp för enhet** väljer du **Hanterade appar**.
5. Välj alternativet **Välj den obligatoriska appen** och klicka på bladet **Riktade appar**. Välj sedan **Managed Browser** och/eller **Edge** för iOS, Android eller båda.
6. Välj **OK** för att återgå till bladet **Lägg till konfigurationsprincip**.
7. Välj **Konfigurationsinställningar**. På bladet **Konfiguration** definierar du nyckel- och värdepar för konfigurationerna för Microsoft Edge. Använd avsnitten senare i den här artikeln för mer information om andra nyckel- och värdepar som du kan definiera.

    > [!NOTE]
    > Microsoft Edge använder samma nyckel/värde-par som Managed Browser. 

8.  När du är klar klickar du på **OK**.
9.  På bladet **Lägg till konfigurationsprincip** väljer du **Lägg till**.<br>
    Den nya konfigurationen skapas och visas på bladet **Appkonfiguration**.

## <a name="assign-the-configuration-settings-you-created"></a>Tilldela de konfigurationsinställningar som du har skapat 

Du kan tilldela inställningarna till Azure AD-grupper med användare. Om användaren har den aktuella skyddade webbläsaren installerad så hanteras appen med de inställningar du har angett.

1. På bladet **Klientappar** i instrumentpanelen för Intunes hantering av mobilprogram väljer du **Appkonfigurationsprinciper**.
2. Välj den du vill tilldela i listan med appkonfigurationer.
3. Välj **Tilldelningar** på nästa blad.
4. På bladet **Tilldelningar** väljer du den Azure AD-grupp som du vill tilldela appkonfigurationen till. Välj sedan **OK**.

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Så här konfigurerar du programproxyinställningar för skyddade webbläsare

Microsoft Edge och [Azure AD-programproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) kan användas tillsammans för att ge användare åtkomst till intranätplatser på deras mobila enheter. 

Här är några exempel på scenarier som AD-programproxyn aktiverar: 

- En användare använder Outlook-mobilappen som skyddas av Intune. Användaren klickar på en länk till en intranätplats i ett e-postmeddelande och Microsoft Edge identifierar att den här intranätsplatsen har gjorts tillgänglig för användaren via programproxyn. Användaren omdirigeras automatiskt via programproxyn för att autentisera med alla tillämpliga multifaktorautentiseringar och principer för villkorlig åtkomst innan de når intranätplatsen. Användare kan nu komma åt interna webbplatser även på sina mobila enheter, och länken i Outlook fungerar som förväntat.
- En användare öppnar Microsoft Edge på sin iOS- eller Android-enhet. Om Microsoft Edge skyddas med Intune och programproxyn är aktiverad kan du navigera till en intranätplats med den interna URL:en som brukar användas. Microsoft Edge identifierar att den här intranätsplatsen har gjorts tillgänglig för användaren via programproxyn, och användaren omdirigeras automatiskt via programproxyn för att autentisera innan användaren når intranätplatsen. 

### <a name="before-you-start"></a>Innan du börjar

- Konfigurera dina interna program via Azure AD-programproxyn.
    - Se [installationsdokumentationen](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) för att konfigurera programproxy och publicera program.
- Microsoft Edge-appen måste ha [Intunes appskyddsprincip](app-protection-policy.md) tilldelad.

> [!NOTE]
> Det kan ta upp till 24 timmar innan omdirigeringsdata för en uppdaterad programproxy börjar gälla i Managed Browser eller Microsoft Edge.

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Steg 1: Aktivera automatisk omdirigering till en skyddad webbläsare från Outlook
Outlook måste konfigureras med en appskyddsprincip som aktiverar inställningen **Dela webbinnehåll med principhanterade webbläsare**.

![Appskyddsprincip – Dela webbinnehåll med principhanterade webbläsare](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Steg 2: Ställ in appkonfigurationsinställningen för att aktivera programproxy
Rikta nyckel/värde-paret nedan för Microsoft Edge för att aktivera programproxyn för Microsoft Edge:

|    Tangent    |    Värde    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Mer information om hur du kan använda Microsoft Edge och en Azure AD-programproxy tillsammans för sömlös (och skyddad) åtkomst till lokala webbappar finns i Enterprise Mobility + Security-blogginlägget [Bättre tillsammans: Intune och Azure Active Directory samarbetar för att förbättra användaråtkomsten](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access). Det här blogginlägget hänvisar till Intune Managed Browser, men innehållet gäller även för Microsoft Edge.

## <a name="how-to-configure-a-homepage-shortcut-for-microsoft-edge"></a>Så här konfigurerar du en genväg på startsidan för Microsoft Edge

Med den här inställningen kan du konfigurera en genväg på startsidan för Microsoft Edge.  Genvägen till webbsidan som du konfigurerar visas som den första ikonen under sökfältet när du öppnar en ny flik i Microsoft Edge. Användaren kommer inte att kunna redigera eller ta bort den här genvägen i sin hanterade kontext. Genvägen till startsidan visar namnet på din organisation för att särskilja den. 

Använd nyckel/värde-paret nedan för att konfigurera en genväg på startsidan:

|    Tangent    |    Värde    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Ange en giltig URL. Felaktiga URL:er är blockerade som en säkerhetsåtgärd.<br>**Exempel:** `<https://www.bing.com`>
    |

## <a name="how-to-configure-managed-bookmarks-for-microsoft-edge"></a>Så här konfigurerar du hanterade bokmärken för Microsoft Edge

För enkel åtkomst kan du konfigurera bokmärken som du vill att användarna har tillgängliga när de använder Microsoft Edge. Här följer lite information:

- De här bokmärkena visas endast för användare när de använder företagsläget för Microsoft Edge. 
- De här bokmärkena kan inte tas bort eller ändras av användare.
- De här bokmärkena visas överst i listan. Alla bokmärken som användare skapar visas under de här bokmärkena.
- Om du har aktiverat omdirigering av App Proxy kan du lägga till App Proxy-webbappar med antingen deras interna eller externa URL-adress.

Använd följande nyckel/värde-par för att konfigurera hanterade bokmärken:

|    Tangent    |    Värde    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    Värdet för den här konfigurationen är en lista över bokmärken. Varje bokmärke består av bokmärkets rubrik och bokmärkets URL. Avgränsa rubriken och URL:en med tecknet `|`.      **Exempel:**<br>`Microsoft Bing|https://www.bing.com`<p>Om du vill konfigurera fler bokmärken avgränsar du varje par med två tecken `||`.<p>**Exempel:**<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="how-to-display-myapps-within-microsoft-edge-bookmarks"></a>Så här visar du MyApps i Microsoft Edge-bokmärken

Som standard får användarna se MyApps-platser som är konfigurerade för dem i en mapp i Microsoft Edge-bokmärkena. Mappen är märkt med namnet på din organisation.

|    Tangent    |    Värde    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **Sant** visar MyApps i Microsoft Edge-bokmärkena.<p>**Falskt** döljer MyApps i Microsoft Edge.    |

## <a name="how-to-specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Så här anger du listan med tillåtna eller blockerade platser för Microsoft Edge
Du kan använda appkonfiguration för att definiera vilka webbplatser användarna ska komma åt när de använder sin arbetsprofil. Om du använder en lista över tillåtna kan användarna bara komma åt webbplatserna som du uttryckligen har angett. Om du använder en lista över blockerade får användarna åtkomst till alla platser utom de platser som du uttryckligen har blockerat. Du bör endast införa antingen listan över tillåtna eller blockerade listan, inte båda. Om båda är riktade mot enheten ska listan över tillåtna användas.  

Du kan använda nyckel/värde-paren nedan för att konfigurera en lista över tillåtna eller blockerade webbplatser för Microsoft Edge. Läs vidare för mer information om giltiga URL-format. 

|    Tangent    |    Värde    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Välj mellan:<p>1. Ange tillåtna URL:er (endast dessa URL:er tillåts, inga andra webbplatser kan nås):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Ange blockerade URL: er (alla andra platser kan nås):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    Motsvarande värde för nyckeln är en lista med URL:er. Du anger alla URL:er som du vill tillåta eller blockera som ett enda värde, avgränsade med ett vertikalstreck `|`.<p>**Exempel:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>URL-format för listan över tillåtna och blockerade webbplatser 
Du kan använda olika URL-format för att skapa dina webbplatslistor med tillåtna/blockerade. De här tillåtna mönstren beskrivs i tabellen nedan. Lite information innan du sätter igång: 
- Kontrollera att du lägger till prefixet **http** eller **https** till alla URL:er när du lägger till dem i listan.
- Du kan använda jokertecknet (*) enligt reglerna i följande lista med tillåtna mönster.
- Du kan ange portnummer i adressen. Om du inte anger ett portnummer, används följande värden:
    - Port 80 för http
    - Port 443 för http
- Jokertecken i portnummer stöds **inte**. `http://www.contoso.com:*` och `http://www.contoso.com:*/` stöds inte.

    |    URL    |    Information    |    Matchar    |    Matchar inte    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Matchar en enstaka sida    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Matchar en enstaka sida    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/&#42;`   |    Matchar alla URL:er som börjar med `www.contoso.com`    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Matchar alla underordnade domäner under `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |
    |    `http://www.contoso.com/images`    |    Matchar en enstaka mapp    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Matchar en enstaka sida, med ett portnummer    |    http://www.contoso.com:80    |         |
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
    - `http://www.contoso.com:*`
    - `http://www.contoso.com: /*`
  
## <a name="defining-behavior-when-users-try-to-access-a-blocked-site"></a>Definiera beteendet när användare försöker komma åt en blockerad webbplats

Du kan skapa en mer flexibel upplevelse för slutanvändarna som inte var möjligt med Intune Managed Browser med modellen med dubbla identiteter som är inbyggda i Microsoft Edge. När användare kommer till en blockerad webbplats i Microsoft Edge kan de uppmanas att öppna länken i sin privata kontext istället för arbetskontexten, vilket gör att de kan skyddas samtidigt som företagets resurser är säkra. Om exempelvis en användare får en länk till en nyhetsartikel via Outlook kan han/hon öppna länken i sin privata kontext eller på en InPrivate-flik i stället för sin arbetskontext, som inte tillåter nyhetswebbplatser. Dessa övergångar tillåts som standard.

Använd nyckel/värde-paret nedan för att konfigurera om dessa mjuka övergångar ska tillåtas:

|    Tangent    |    Värde    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **Sant** tillåter att Microsoft Edge flyttar användare till sina privata kontexter för att öppna blockerade webbplatser<p>**Blockera** förhindrar att Microsoft Edge flyttar användarna, och användarna ser bara ett meddelande om de försöker komma åt den blockerade webbplatsen.    |

## <a name="directing-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Dirigera användarna till Microsoft Edge i stället för Intune Managed Browser 

Både Intune Managed Browser och Microsoft Edge kan nu användas av principskyddade webbläsare. För att säkerställa att dina användare använder rätt webbläsarapp ska du rikta alla Intune-hanterade appar (t.ex. Outlook och OneDrive) med följande konfigurationsinställning:

|    Tangent    |    Värde    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    Värdet `true` uppmanar användarna att använda Microsoft Edge.<p>Värdet `false` uppmanar användarna att använda Intune Managed Browser.    |

Om den här appens konfigurationsvärde inte har angetts definierar följande logik vilken webbläsare som kommer att användas för att öppna företagets länkar.

I Android:
- Intune Managed Browser startas om användaren har både Intune Managed Browser och Microsoft Edge på sin enhet. 
- Microsoft Edge öppnas om enbart Microsoft Edge är nedladdat på enheten och är mål för Intune-principen.
- Managed Browser öppnas bara om det finns på enheten och är mål för Intune-principen.

I iOS, för appar som har integrerat Intune SDK för iOS med 9.0.9+:
- Intune Managed Browser startas om både Managed Browser och Microsoft Edge finns på enheten.  
- Microsoft Edge startas enbart om det finns på enheten och är mål för Intune-principen.
- Managed Browser öppnas bara om det finns på enheten och är mål för Intune-principen.

## <a name="using-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Använda Microsoft Edge i iOS för att komma åt loggar för hanterade appar 

Slutanvändare med Microsoft Edge installerat på sina iOS-enheter kan se hanteringsstatus för alla appar som har publicerats av Microsoft. De kan skicka loggar för felsökning av deras hanterade iOS-appar.
1. Öppna Microsoft Edge på din iOS-enhet.
2. Skriv in `about:intunehelp` i adressrutan. 
3. Felsökningsläget startas från Microsoft Edge.

En lista över de inställningar som finns lagrade i apploggarna finns i [granska appskyddsloggarna i Managed Browser](app-protection-policy-settings-log.md).

Mer information om hur du visar loggar på Android-enheter finns i [Skicka loggar till IT-administratören via e-post](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Säkerhet och sekretess för Microsoft Edge

Ytterligare överväganden för säkerhet och sekretess för Microsoft Edge:

- Microsoft Edge använder inte inställningar som användare anger för den inbyggda webbläsaren på sina enheter, eftersom Microsoft Edge inte har åtkomst till de här inställningarna.
- Om du konfigurerar alternativet **Kräv enkel PIN-kod för åtkomst** eller **Kräv företagets autentiseringsuppgifter för åtkomst** i en appskyddsprincip som är associerad med Microsoft Edge och en användare väljer hjälplänken på autentiseringssidan kan användaren bläddra på alla webbplatser, oavsett om de har lagts till i en blockeringslista i principen.
- Microsoft Edge kan endast blockera åtkomst till webbplatser när de öppnas direkt. Den blockerar inte åtkomst när mellanliggande tjänster (till exempel en översättningstjänst) används för åtkomst till webbplatsen.
- För att tillåta autentisering och få åtkomst till Intune-dokumentationen är ***microsoft.com** undantaget från listan Tillåt eller blockera. Den tillåts alltid.
Stäng av användningsdata Microsoft samlar automatiskt in anonymiserade data om prestanda och användning av den hanterade webbläsaren för att kunna förbättra Microsofts produkter och tjänster. Användare kan stänga av insamling av data med hjälp av inställningen **Användningsdata** på sina enheter. Du har ingen kontroll över insamlingen av dessa data. Webbplatser som har ett utgånget eller ej betrott certifikat kan inte öppnas på iOS-enheter.

## <a name="next-steps"></a>Nästa steg

- [Vad är appskyddsprinciper?](app-protection-policy.md) 
