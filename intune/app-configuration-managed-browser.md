---
title: "Hantera webbåtkomst med Managed Browser-appen"
titlesuffix: Azure portal
description: "Distribuera Managed Browser för att begränsa webbsurfning och överföring av webbdata till andra appar.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 99b8b50dbbb2dc2e3d7e8cd5af2f95fa2bb3b861
ms.sourcegitcommit: 42a0e4c83e33c1a25506ca75d673e861e9206945
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/26/2017
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Hantera Internetåtkomst med Managed Browser-principer med Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Managed Browser är en webbläsarapp som du kan ladda ned från offentliga appbutiker och använda i din organisation. När konfigurerad med Intune kan Managed Browser:
- Användas för att få åtkomst till företagets webbplatser och SaaS-program med enkel inloggning via tjänsten MyApps, samtidigt som webbdata skyddas.
- Vara förkonfigurerad med en lista över URL:er och domäner som begränsar vilka webbplatser användaren kan navigera till i företagets miljö.
- Vara förkonfigurerad med en startsida och de bokmärken som du anger.

Eftersom den här appen har integrering med Intune SDK kan du också använda appskyddsprinciper för den, inklusive:
- Styra användningen av klipp ut, kopiera och klistra in
- Förhindra skärmdumpar
- Se till att länkar till innehåll som användare väljer endast öppnas i andra hanterade appar.

Mer information finns i [Vad är appskyddsprinciper?](/intune/app-protection-policy)

Du kan tillämpa inställningarna för att:

- Enheter som har registrerats med Intune
- Registrerade med en annan MDM-produkt
- Ohanterade enheter

Om användarna installerar Managed Browser från appbutiken och Intune inte hanterar den, kan den användas som en vanlig webbläsare med stöd för enkel inloggning via webbplatsen Microsoft MyApps. Användarna dirigeras direkt till webbplatsen MyApps där de kan se alla sina etablerade SaaS-program.
Eftersom Managed Browser inte hanteras av Intune har den inte åtkomst till några data från andra Intune-hanterade program. 

Managed Browser inte har stöd för det kryptografiska protokollet Secure Sockets Layer version 3 (SSLv3).

Du kan skapa Managed Browser-principer för följande enhetstyper:

-   Enheter som kör Android 4 och senare

-   Enheter som kör iOS 8.0 och senare

>[!IMPORTANT]
>Från och med oktober 2017 stöder Intune Managed Browser-appen på Android-appen endast enheter som körs på Android 4.4 och senare. Intune Managed Browser-appen på iOS har endast stöd för enheter som körs på iOS 9.0 eller senare.
>Tidigare versioner av Android och iOS kommer att kunna fortsätta att använda Managed Browser, men kommer inte att kunna installera nya versioner av appen och kanske inte använda alla funktioner. Vi rekommenderar att du uppdaterar de här enheterna till en version av operativsystemet som stöds.


Intune Managed Browser stöder öppnande av webbinnehåll från [Microsoft Intunes programpartners](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx).

## <a name="create-a-managed-browser-app-configuration"></a>Skapa en konfiguration för Managed Browser-programmet

1.  Logga in på Azure-portalen.
2.  Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3.  På bladet **Mobilappar** i listan Hantera väljer du **Appkonfigurationsprinciper**.
4.  På bladet **Appkonfigurationsprinciper** väljer du **Lägg till**.
5.  På bladet **Lägg till appkonfiguration** anger du ett **Namn** och en valfri **Beskrivning** för appkonfigurationsinställningarna.
6.  Vid **Enhetsregistrering** väljer du **Hanterade enheter** eller **Hanterade appar**.
7.  Välj **Välj obligatoriska appar** och klicka sedan på bladet **Målappar**, samt välj **Managed Browser** för iOS, Android eller båda.
8.  Välj **OK** för att återgå till bladet **Lägg till appkonfiguration**.
9.  Välj **Konfigurationsinställningar**. På bladet **Konfiguration** definierar du nyckel- och värdepar för konfigurationerna för Managed Browser. Använd avsnitten senare i den här artikeln för mer information om andra nyckel- och värdepar som du kan definiera.
10. När du är klar väljer du **OK**.
11. På bladet **Lägg till appkonfiguration** väljer du **Skapa**.
12. Den nya konfigurationen skapas och visas på bladet **Appkonfiguration**.

>[!IMPORTANT]
>Managed Browser förlitar sig för närvarande på automatisk registrering. För att appkonfigurationer ska tillämpas så måste ett annat program på enheten redan hanteras av Intunes appskyddsprinciper.

## <a name="assign-the-configuration-settings-you-created"></a>Tilldela de konfigurationsinställningar som du har skapat

Du kan tilldela inställningarna till Azure AD-grupper med användare. Om användaren har installerat Managed Browser kommer appen hanteras med de inställningar som du har angett.

1. På bladet **Inställningar** på instrumentpanelen för Intunes hantering av mobilprogram väljer du **Appkonfiguration**.
2. Välj den du vill tilldela i listan med appkonfigurationer.
3. Välj **Användargrupper** på nästa blad.
4. På bladet **Användargrupper** väljer du den Azure AD-grupp som du vill tilldela appkonfigurationen till. Välj sedan **OK**.


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>Så här konfigurerar du programproxyinställningar för Managed Browser

Intune Managed Browser och [Azure AD-programproxy]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) kan användas tillsammans för att stödja följande scenarier för användare av iOS och Android-enheter:

- En användare laddar ned och loggar in på Microsoft Outlook-appen. Intunes appskyddsprinciper tillämpas automatiskt. De krypterar sparade data och blockerar användaren från att överföra företagets filer till ohanterade appar och platser på enheten. När användaren sedan klickar på en länk till en intranätplats i Outlook så kan du ställa in så att länken öppnas i Managed Browser-appen i stället för en annan webbläsare. Managed Browser identifierar att den här intranätsplatsen har gjorts tillgänglig för användaren med programproxyn. Användaren omdirigeras automatiskt via programproxyn för att autentisera med alla tillämpliga multifaktorautentiseringar och principer för villkorlig åtkomst innan de når intranätplatsen. Den här platsen, som tidigare inte hittades när användaren använde en fjärranslutning, kan nu öppnas och länken i Outlook fungerar som förväntat.
- En fjärranvändare öppnar Managed Browser-appen och navigerar till en intranätplats med den intern webbadressen. Managed Browser identifierar att den här intranätsplatsen har gjorts tillgänglig för användaren via programproxyn. Användaren omdirigeras automatiskt via programproxyn för att autentisera med alla tillämpliga multifaktorautentiseringar och principer för villkorlig åtkomst innan de når intranätplatsen. Den här platsen, som tidigare inte hittades när användaren använde en fjärranslutning, kan nu öppnas.

### <a name="before-you-start"></a>Innan du börjar

- Konfigurera dina interna program via Azure AD-programproxyn.
    - Se [installationsdokumentationen]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started) för att konfigurera programproxy och publicera program. 
    - Du måste använda version 1.2.0 eller senare av Managed Browser-appen.
    - Användare av Managed Browser-appen har en [princip för Intune-appskydd]( app-protection-policy.md) tilldelad till appen.

#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>Steg 1: Aktivera automatisk omdirigering till Managed Browser från Outlook
Outlook måste konfigureras med en appskyddsprincip som aktiverar inställningen **Begränsa webbinnehåll till visning i Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>Steg 2: Tilldela en appkonfigurationsprincip som har tilldelats Managed Browser.
Den här proceduren konfigurerar Managed Browser-appen för att använda omdirigering av programproxy. Använd proceduren att skapa en appkonfiguration för Managed Browser till att ange följande nyckel- och värdepar:

|||
|-|-|
|Tangent|Värde|
|**com.microsoft.intune.mam.managedbrowser.AppProxyRedirection**|**true**|


## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>Så här konfigurerar du startsidan för Managed Browser

Den här inställningen låter dig konfigurera den webbsida som användarna ser när de startar Managed Browser eller skapar en ny flik. Använd proceduren att skapa en appkonfiguration för Managed Browser till att ange följande nyckel- och värdepar:

|||
|-|-|
|Tangent|Värde|
|**com.microsoft.intune.mam.managedbrowser.homepage**|Ange en giltig URL. Felaktiga URL:er är blockerade som en säkerhetsåtgärd.<br>Exempel: **https://www.bing.com**|


## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>Så här konfigurerar du bokmärken för Managed Browser

Den här inställningen låter dig konfigurera en uppsättning bokmärken som är tillgängliga för användare av Managed Browser.

- De här bokmärkena kan inte tas bort eller ändras av användare
- De här bokmärkena visas överst i listan. Alla bokmärken som användare skapar visas under de här bokmärkena.
- Om du har aktiverat omdirigering av App Proxy kan du lägga till App Proxy-webbappar med antingen deras interna eller externa URL-adress.

Använd proceduren att skapa en appkonfiguration för Managed Browser till att ange följande nyckel- och värdepar:

|||
|-|-|
|Tangent|Värde|
|**com.microsoft.intune.mam.managedbrowser.bookmarks**|Värdet för den här konfigurationen är en lista över bokmärken. Varje bokmärke består av bokmärkets rubrik och bokmärkets URL. Avgränsa rubriken och URL:en med tecknet **&#124;**.<br><br>Exempel: **Microsoft Bing&#124;https://www.bing.com**<br><br>Om du vill konfigurera fler bokmärken avgränsar du varje par med två tecken: **&#124;&#124;**<br><br>Exempel: **Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com**|

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Så här anger du tillåtna och blockerade URL:er för Managed Browser

Använd proceduren att skapa en appkonfiguration för Managed Browser till att ange följande nyckel- och värdepar:

|||
|-|-|
|Tangent|Värde|
|Välj mellan:<br><br>– Ange tillåtna URL:er (endast dessa URL:er tillåts, inga andra webbplatser kan nås): **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br>– Ange blockerade URL: er (alla andra platser kan nås): <br><br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**|Motsvarande värde för nyckeln är en lista med URL:er. Du anger alla URL:er som du vill tillåta eller blockera som ett enda värde, avgränsade med ett vertikalstreck **&#124;**.<br><br>Exempel:<br><br>**URL1&#124;URL2&#124;URL3**<br>**http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com**|

>[!IMPORTANT]
>Ange inte båda nycklarna. Om båda nycklarna används för samma användare tillämpas den tillåtna nyckeln eftersom det är det mest restriktiva alternativet.
>Se även till att du inte blockerar viktiga sidor som t.ex. företagets webbplatser.

### <a name="url-format-for-allowed-and-blocked-urls"></a>URL-format för tillåtna och blockerade URL:er
Använd följande information för att lära dig om tillåtna format och jokertecken som du kan använda när du anger URL:er i listorna för tillåtna och blockerade webbplatser:

-   Du kan använda jokertecknet (**&#42;**) enligt reglerna i följande lista med tillåtna mönster:

-   Kontrollera att du lägger till prefixet **http** eller **https** till alla URL:er när du lägger till dem i listan.

-   Du kan ange portnummer i adressen. Om du inte anger ett portnummer, används följande värden:

    -   Port 80 för http

    -   Port 443 för http

    Jokertecken i portnummer stöds inte. Till exempel stöds inte **http&colon;//www&period;contoso&period;com:*;** och **http&colon;//www&period;contoso&period;com: /*;**.

-   Lär dig mer om de tillåtna mönster du kan använda när du anger URL:er med hjälp av följande tabell:

|URL|Information|Matchar|Matchar inte|
|-------|---------------|-----------|------------------|
|http://www.contoso.com|Matchar en enstaka sida|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
|http://contoso.com|Matchar en enstaka sida|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
|http://www.contoso.com/&#42;|Matchar alla URL:er som börjar med www.contoso.com|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
|http://&#42;.contoso.com/&#42;|Matchar alla underordnade domäner under contoso.com|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
|http://www.contoso.com/images|Matchar en enstaka mapp|www.contoso.com/images|www.contoso.com/images/dogs|
|http://www.contoso.com:80|Matchar en enstaka sida, med ett portnummer|http://www.contoso.com:80|
|https://www.contoso.com|Matchar en enstaka, säker sida|https://www.contoso.com|http://www.contoso.com|
|http://www.contoso.com/images/&#42;|Matchar en enstaka mapp och alla undermappar|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   Följande är några exempel på indata som du inte kan ange:

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   IP-adresser

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

## <a name="security-and-privacy-for-the-managed-browser"></a>Säkerhet och sekretess för Managed Browser

-   Managed Browser använder inte inställningar som användare gör i den inbyggda webbläsaren på sina enheter. Managed Browser har inte åtkomst till de här inställningarna.

-   Om du konfigurerar alternativet **Kräv enkel PIN-kod för åtkomst** eller **Kräv företagets autentiseringsuppgifter för åtkomst** i en appskyddsprincip som är associerad med Managed Browser och en användare väljer hjälplänken på autentiseringssidan så kan användaren bläddra på alla webbplatser, oavsett om de har lagts till i en blockeringslista i principen.

-   Managed Browser kan endast blockera åtkomst till webbplatser när de öppnas direkt. Den blockerar inte åtkomst när mellanliggande tjänster (till exempel en översättningstjänst) används för åtkomst till webbplatsen.

-   För att tillåta autentisering och få åtkomst till Intune-dokumentationen är **&#42;.microsoft.com** undantaget från listan Tillåt eller blockera. Den tillåts alltid.

### <a name="turn-off-usage-data"></a>Stäng av användningsdata
Microsoft samlar automatiskt in anonyma data om prestanda och användning av Managed Browser för att kunna förbättra Microsofts produkter och tjänster. Användare kan stänga av insamling av data med hjälp av inställningen **Användningsdata** på sina enheter. Du har ingen kontroll över insamlingen av dessa data.


-   Webbplatser som har ett utgånget eller ej betrott certifikat kan inte öppnas på iOS-enheter.
-   Managed Browser använder inte inställningar som användare gör i den inbyggda webbläsaren på sina enheter. Managed Browser har inte åtkomst till de här inställningarna.

-   Om du konfigurerar alternativet **Kräv enkel PIN-kod för åtkomst** eller **Kräv företagets autentiseringsuppgifter för åtkomst** i en appskyddsprincip som är associerad med Managed Browser och en användare väljer hjälplänken på autentiseringssidan så kan användaren bläddra på alla webbplatser, oavsett om de har lagts till i en blockeringslista i principen.

-   Managed Browser kan endast blockera åtkomst till webbplatser när de öppnas direkt. Den blockerar inte åtkomst när mellanliggande tjänster (till exempel en översättningstjänst) används för åtkomst till webbplatsen.

-   För att tillåta autentisering och få åtkomst till Intune-dokumentationen är **&#42;.microsoft.com** undantaget från listan Tillåt eller blockera. Den tillåts alltid.

### <a name="turn-off-usage-data"></a>Stäng av användningsdata
Microsoft samlar automatiskt in anonyma data om prestanda och användning av Managed Browser för att kunna förbättra Microsofts produkter och tjänster. Användare kan stänga av insamling av data med hjälp av inställningen **Användningsdata** på sina enheter. Du har ingen kontroll över insamlingen av dessa data.
