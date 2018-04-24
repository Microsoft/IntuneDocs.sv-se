---
title: Hantera webbåtkomst med Managed Browser-appen
titlesuffix: Microsoft Intune
description: Distribuera Managed Browser för att begränsa webbsurfning och överföring av webbdata till andra appar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 10278dd48552e280ebe7399a61033dfb04fbbd74
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Hantera Internetåtkomst med Managed Browser-principer med Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Managed Browser är en webbläsarapp som du kan ladda ned från offentliga appbutiker och använda i din organisation. När konfigurerad med Intune kan Managed Browser:
- Användas för att få åtkomst till företagets webbplatser och SaaS-program med enkel inloggning via tjänsten MyApps, samtidigt som webbdata skyddas.
- Vara förkonfigurerad med en lista över URL:er och domäner som begränsar vilka webbplatser användaren kan navigera till i företagets miljö.
- Vara förkonfigurerad med en startsida och de bokmärken som du anger.

Eftersom den här appen har integrering med Intune SDK kan du också använda appskyddsprinciper för den, inklusive:
- Styra användningen av klipp ut, kopiera och klistra in
- Förhindra skärmdumpar
- Se till att länkar till innehåll som användare väljer endast öppnas i andra hanterade appar.

Mer information finns i [Vad är appskyddsprinciper?](/intune/app-protection-policy.md)

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


Intune Managed Browser stöder öppnande av webbinnehåll från [Microsoft Intunes programpartners](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="conditional-access-for-the-intune-managed-browser"></a>Villkorlig åtkomst för Intune Managed Browser

Managed Browser är nu en godkänd klientapp för villkorlig åtkomst. Det innebär att du kan begränsa mobil webbläsaråtkomst till Azure AD-anslutna webbappar där användarna bara kan använda Managed Browser, vilket blockerar åtkomsten från andra oskyddade webbläsare som Safari eller Chrome. Det här skyddet kan tillämpas på Azure-resurser som Exchange Online och SharePoint Online, Office-portalen och även lokala platser som du exponerar för externa användare via [Azure AD-programproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). 

Om du vill begränsa Azure AD-anslutna webbappars användning av Intune Managed Browser på mobila plattformar, kan du skapa en villkorlig Azure AD-åtkomstprincip som kräver godkända klientprogram. 

1. I Azure-portalen väljer du **Azure Active Directory** > **Företagsprogram** > **Villkorlig åtkomst** > **Ny princip**. 
2. Välj därefter **Bevilja** i avsnittet **Åtkomstkontroller** på bladet. 
3. Klicka på **Kräv godkänd klientapp**. 
4. Klicka på **Välj** på bladet **Bevilja**. Den här principen måste tilldelas till de molnappar som du vill ska vara tillgängliga enbart för appen Intune Managed Browser.

    ![Azure AD – villkorlig åtkomstprincip för Managed Browser](./media/managed-browser-conditional-access-01.png)

5. I avsnittet **Tilldelningar** väljer du **Villkor** > **Klientappar**. Bladet **Klientappar** visas.
6. Klicka på **Ja** under **Konfigurera** för att tillämpa principen på specifika klientappar.
7. Kontrollera att **Webbläsare** är valt som en klientapp.

    ![Azure AD – Managed Browser – Välj klientappar](./media/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Om du vill begränsa vilka interna appar (icke-webbläsarbaserade appar) som har åtkomst till dessa molnprogram kan du också välja **Mobilappar och skrivbordsklienter**.

8. I avsnittet **Tilldelningar** väljer du **Användare och grupper** och sedan de användare eller grupper som du vill tilldela den här principen till. 

    > [!NOTE]
    > Användarna måste också vara mål för Intunes appskyddsprincip. Mer information om att skapa Intune-appskyddsprinciper finns i [Vad är appskyddsprinciper?](app-protection-policy.md).

9. I avsnittet **Tilldelningar** går du till **Molnappar** och väljer vilka appar som ska skyddas med den här principen.

När du har konfigurerat principen ovan tvingas användarna använda Intune Managed Browser för att få åtkomst till de Azure AD-anslutna webbappar som du har skyddat med den här principen. Om användarna försöker använda en ohanterad webbläsare i det här scenariot, visas ett meddelande om att Intune Managed Browser måste användas i stället.

Managed Browser har inget stöd för klassiska principer för villkorlig åtkomst. Mer information finns i [Migrera klassiska principer i Azure Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration).

##  <a name="single-sign-on-to-azure-ad-connected-web-apps-in-the-intune-managed-browser"></a>Enkel inloggning till Azure AD-anslutna webbappar i Intune Managed Browser

Intune Managed Browser-programmet i iOS och Android kan nu dra nytta av enkel inloggning till alla webbappar (SaaS och lokala) som är Azure AD-anslutna. Om Microsoft Authenticator-appen finns på iOS eller Intune-företagsportalappen på Android, kommer användarna av Intune Managed Browser att ha åtkomst till Azure AD-anslutna webbprogram utan att behöva ange sina autentiseringsuppgifter på nytt.

Enkel inloggning i Intune Managed Browser kräver att enheten har registrerats av Microsoft Authenticator-appen på iOS eller Intunes företagsportal på Android. Användare med Authenticator-appen eller Intune-företagsportalen uppmanas att registrera sin enhet när de navigerar till en Azure AD-ansluten webbapp i Intune Managed Browser, om enheten inte redan har registrerats av ett annat program. När enheten är registrerad med kontot som hanteras av Intune, kommer detta konto ha enkel inloggning aktiverat för Azure AD-anslutna webbappar. 

> [!NOTE]
> Enhetsregistrering är en enkel incheckning med Azure AD-tjänsten. Det kräver inte fullständig enhetsregistrering och inte ger IT-avdelningen ytterligare behörighet på enheten.

## <a name="create-a-managed-browser-app-configuration"></a>Skapa en konfiguration för Managed Browser-programmet

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3.  På bladet **Mobilappar** i listan Hantera väljer du **Appkonfigurationsprinciper**.
4.  På bladet **Appkonfigurationsprinciper** väljer du **Lägg till**.
5.  På bladet **Lägg till konfigurationsprincip** anger du ett **Namn** och en valfri **Beskrivning** för appkonfigurationsinställningarna.
6.  För **Registreringstyp för enhet** väljer du **Hanterade appar**.
7.  Välj alternativet för att **välja den obligatoriska appen** och klicka sedan på bladet **Riktade appar**. Välj därefter **Managed Browser** för iOS och/eller Android.
8.  Välj **OK** för att återgå till bladet **Lägg till konfigurationsprincip**.
9.  Välj **Konfigurationsinställningar**. På bladet **Konfiguration** definierar du nyckel- och värdepar för konfigurationerna för Managed Browser. Använd avsnitten senare i den här artikeln för mer information om andra nyckel- och värdepar som du kan definiera.
10. När du är klar väljer du **OK**.
11. På bladet **Lägg till konfigurationsprincip** väljer du **Lägg till**.
12. Den nya konfigurationen skapas och visas på bladet **Appkonfiguration**.

>[!IMPORTANT]
>Managed Browser förlitar sig för närvarande på automatisk registrering. För att appkonfigurationer ska tillämpas så måste ett annat program på enheten redan hanteras av Intunes appskyddsprinciper.

## <a name="assign-the-configuration-settings-you-created"></a>Tilldela de konfigurationsinställningar som du har skapat

Du kan tilldela inställningarna till Azure AD-grupper med användare. Om användaren har installerat Managed Browser kommer appen hanteras med de inställningar som du har angett.

1. På bladet **Mobilappar** i instrumentpanelen för Intunes hantering av mobilprogram väljer du **Appkonfigurationsprinciper**.
2. Välj den du vill tilldela i listan med appkonfigurationer.
3. Välj **Tilldelningar** på nästa blad.
4. På bladet **Tilldelningar** väljer du den Azure AD-grupp som du vill tilldela appkonfigurationen till. Välj sedan **OK**.


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>Så här konfigurerar du programproxyinställningar för Managed Browser

Intune Managed Browser och [Azure AD-programproxy]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) kan användas tillsammans för att stödja följande scenarier för användare av iOS och Android-enheter:

- En användare laddar ned och loggar in på Microsoft Outlook-appen. Intunes appskyddsprinciper tillämpas automatiskt. De krypterar sparade data och blockerar användaren från att överföra företagets filer till ohanterade appar och platser på enheten. När användaren sedan klickar på en länk till en intranätplats i Outlook så kan du ställa in så att länken öppnas i Managed Browser-appen i stället för en annan webbläsare. Managed Browser identifierar att den här intranätsplatsen har gjorts tillgänglig för användaren med programproxyn. Användaren omdirigeras automatiskt via programproxyn för att autentisera med alla tillämpliga multifaktorautentiseringar och principer för villkorlig åtkomst innan de når intranätplatsen. Den här platsen, som tidigare inte hittades när användaren använde en fjärranslutning, kan nu öppnas och länken i Outlook fungerar som förväntat.
- En fjärranvändare öppnar Managed Browser-appen och navigerar till en intranätplats med den intern webbadressen. Managed Browser identifierar att den här intranätsplatsen har gjorts tillgänglig för användaren via programproxyn. Användaren omdirigeras automatiskt via programproxyn för att autentisera med alla tillämpliga multifaktorautentiseringar och principer för villkorlig åtkomst innan de når intranätplatsen. Den här platsen, som tidigare inte hittades när användaren använde en fjärranslutning, kan nu öppnas.

### <a name="before-you-start"></a>Innan du börjar

- Konfigurera dina interna program via Azure AD-programproxyn.
    - Se [installationsdokumentationen]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started) för att konfigurera programproxy och publicera program. 
- Du måste använda version 1.2.0 eller senare av Managed Browser-appen.
- Användare av Managed Browser-appen har en [princip för Intune-appskydd]( app-protection-policy.md) tilldelad till appen.

    > [!NOTE]
    > Det kan ta upp till 24 timmar innan omdirigeringsdata för en uppdaterad programproxy börjar gälla i Managed Browser.


#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>Steg 1: Aktivera automatisk omdirigering till Managed Browser från Outlook
Outlook måste konfigureras med en appskyddsprincip som aktiverar inställningen **Begränsa webbinnehåll till visning i Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>Steg 2: Tilldela en appkonfigurationsprincip som har tilldelats Managed Browser.
Den här proceduren konfigurerar Managed Browser-appen för att använda omdirigering av programproxy. Använd proceduren att skapa en appkonfiguration för Managed Browser till att ange följande nyckel- och värdepar:

|||
|-|-|
|Tangent|Värde|
|**com.microsoft.intune.mam.managedbrowser.AppProxyRedirection**|**true**|

Mer information om hur Managed Browser och Azure AD-programproxy kan användas tillsammans för sömlös (och skyddad) åtkomst till lokala webbappar finns på Enterprise Mobility + Security-blogginlägget [Bättre tillsammans: Intune och Azure Active Directory samarbetar för att förbättra användaråtkomsten](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access).

## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>Så här konfigurerar du startsidan för Managed Browser

Den här inställningen låter dig konfigurera den webbsida som användarna ser när de startar Managed Browser eller skapar en ny flik. Använd proceduren att skapa en appkonfiguration för Managed Browser till att ange följande nyckel- och värdepar:


|                                                                   |                                                                                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
|                                Tangent                                |                                                           Värde                                                            |
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Ange en giltig URL. Felaktiga URL:er är blockerade som en säkerhetsåtgärd.<br>Exempel: <strong><https://www.bing.com></strong> |

## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>Så här konfigurerar du bokmärken för Managed Browser

Den här inställningen låter dig konfigurera en uppsättning bokmärken som är tillgängliga för användare av Managed Browser.

- De här bokmärkena kan inte tas bort eller ändras av användare
- De här bokmärkena visas överst i listan. Alla bokmärken som användare skapar visas under de här bokmärkena.
- Om du har aktiverat omdirigering av App Proxy kan du lägga till App Proxy-webbappar med antingen deras interna eller externa URL-adress.

Använd proceduren att skapa en appkonfiguration för Managed Browser till att ange följande nyckel- och värdepar:


|                                                                    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                Tangent                                 |                                                                                                                                                                                                                                                         Värde                                                                                                                                                                                                                                                          |
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | Värdet för den här konfigurationen är en lista över bokmärken. Varje bokmärke består av bokmärkets rubrik och bokmärkets URL. Avgränsa rubriken och URL:en med tecknet <strong>&#124;</strong>.<br><br>Exempel: <strong>Microsoft Bing&#124;<https://www.bing.com></strong><br><br>Om du vill konfigurera fler bokmärken avgränsar du varje par med två tecken: <strong>&#124;&#124;</strong><br><br>Exempel: <strong>Bing&#124;https://www.bing.com&#124;&#124; Contoso&#124;<https://www.contoso.com></strong> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Så här anger du tillåtna och blockerade URL:er för Managed Browser

Använd proceduren att skapa en appkonfiguration för Managed Browser till att ange följande nyckel- och värdepar:


|                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                                             |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                               Tangent                                                                                                                                                                |                                                                                                                                                                                    Värde                                                                                                                                                                                    |
| Välj mellan:<br><br>– Ange tillåtna URL:er (endast dessa URL:er tillåts, inga andra webbplatser kan nås): <strong>com.microsoft.intune.mam.managedbrowser.AllowListURLs</strong><br><br>– Ange blockerade URL: er (alla andra platser kan nås): <br><br><strong>com.microsoft.intune.mam.managedbrowser.BlockListURLs</strong> | Motsvarande värde för nyckeln är en lista med URL:er. Du anger alla URL:er som du vill tillåta eller blockera som ett enda värde, avgränsade med ett vertikalstreck <strong>&#124;</strong>.<br><br>Exempel:<br><br><strong>URL1&#124;URL2&#124;URL3</strong><br><strong>http://<em>.contoso.com/</em>&#124;https://<em>.bing.com/</em>&#124;<https://expenses.contoso.com></strong> |

>[!IMPORTANT]
>Ange inte båda nycklarna. Om båda nycklarna används för samma användare tillämpas den tillåtna nyckeln eftersom det är det mest restriktiva alternativet.
>Se även till att du inte blockerar viktiga sidor som t.ex. företagets webbplatser.

### <a name="url-format-for-allowed-and-blocked-urls"></a>URL-format för tillåtna och blockerade URL:er
Använd följande information för att lära dig om tillåtna format och jokertecken som du kan använda när du anger URL:er i listorna för tillåtna och blockerade webbplatser:

- Du kan använda jokertecknet (**&#42;**) enligt reglerna i följande lista med tillåtna mönster:

- Kontrollera att du lägger till prefixet **http** eller **https** till alla URL:er när du lägger till dem i listan.

- Du kan ange portnummer i adressen. Om du inte anger ett portnummer, används följande värden:

  -   Port 80 för http

  -   Port 443 för http

  Jokertecken i portnummer stöds inte. Till exempel stöds inte <strong>http&colon;//www&period;contoso&period;com:*;</strong> och <strong>http&colon;//www&period;contoso&period;com: /*;</strong>.

- Lär dig mer om de tillåtna mönster du kan använda när du anger URL:er med hjälp av följande tabell:

|                  URL                  |                     Information                      |                                                Matchar                                                |                                Matchar inte                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        http://www.contoso.com         |              Matchar en enstaka sida               |                                            www.contoso.com                                            |  host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/   |
|          http://contoso.com           |              Matchar en enstaka sida               |                                             contoso.com/                                              | host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com |
|    <http://www.contoso.com/&#42>;     | Matchar alla URL:er som börjar med www.contoso.com |      www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows      |              host.contoso.com<br /><br />host.contoso.com/images              |
|    http://&#42;.contoso.com/&#42;     |     Matchar alla underordnade domäner under contoso.com     | developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos |                               contoso.host.com                                |
|     http://www.contoso.com/images     |             Matchar en enstaka mapp              |                                        www.contoso.com/images                                         |                          www.contoso.com/images/dogs                          |
|       http://www.contoso.com:80       |  Matchar en enstaka sida, med ett portnummer   |                                       http://www.contoso.com:80                                       |                                                                               |
|        https://www.contoso.com        |          Matchar en enstaka, säker sida           |                                        https://www.contoso.com                                        |                            http://www.contoso.com                             |
| <http://www.contoso.com/images/&#42>; |    Matchar en enstaka mapp och alla undermappar    |                  www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats                   |                            www.contoso.com/videos                             |

- Följande är några exempel på indata som du inte kan ange:

  - &#42;.com

  - &#42;.contoso/&#42;

  - www.contoso.com/&#42;images

  - www.contoso.com/&#42;images&#42;pigs

  - www.contoso.com/page&#42;

  - IP-adresser

  - https://&#42;

  - http://&#42;

  - http://www.contoso.com:&#42;

  - http://www.contoso.com: /&#42;

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>Komma åt loggar för hanterade appar med Managed Browser i iOS

Slutanvändare med Managed Browser installerade på sina iOS-enheter kan se hanteringsstatus för alla appar som har publicerats av Microsoft. De kan skicka loggar för felsökning av deras hanterade iOS-appar.

1. Öppna iOS **Inställningar**.
2. Välj programinställningar för hanterad **Webbläsare**.
3. Växla **Aktivera Intune-diagnostik** för att ställa in webbläsaren på felsökningsläge.
4. Öppna den hanterade **webbläsaren**. Klicka på **Visa status för Intune-app** om du vill granska enskilda programprincipinställningar.
5. Tryck på **Kom igång** och **Dela loggar** eller **Skicka loggar till Microsoft** om du vill skicka felsökningsloggarna till IT-administratören eller Microsoft.

Du kan också öppna webbläsaren i felsökningsläge från appen.

1. Öppna Managed Browser.
2. Skriv in `about:intunehelp` i adressrutan.
Webbläsaren startar felsökningsläget.

En lista över de inställningar som finns lagrade i apploggarna finns i [granska appskyddsloggarna i Managed Browser](app-protection-policy-settings-log.md).

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

## <a name="next-steps"></a>Nästa steg

- [Vad är appskyddsprinciper?](app-protection-policy.md)
