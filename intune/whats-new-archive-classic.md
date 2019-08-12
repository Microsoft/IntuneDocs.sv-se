---
title: Nyheter i Microsoft Intunes klassiska portalarkiv
description: Arkiverade nyhetsmeddelanden för Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/08/2017
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d414295966580e0dd91ce2b94757509fd13bdfbe
ms.sourcegitcommit: e6edfbfd63dd7c2500ce1123205aa2af9a7e8e2e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68783134"
---
# <a name="whats-new-in-the-intune-classic-portal---previous-months"></a>Nyheter i den klassiska Intune-portalen – föregående månader

[!INCLUDE [classic-portal](./includes/classic-portal.md)]

Den här sidan visar nya funktioner och meddelanden som tidigare visats på sidan [Nyheter](whats-new.md) för den klassiska Intune-portalen.

## <a name="april-2017"></a>April 2017

### <a name="new-capabilities"></a>Nya funktioner

#### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps tillgängligt för Managed Browser <!--822308, 822303-->

Microsoft MyApps har nu bättre stöd i den hanterade webbläsaren. Användare av hanterad webbläsare som inte är mål för hantering flyttas direkt till tjänsten MyApps där de kan komma åt sina administratörsetablerade SaaS-appar. Användare som är mål för Intune-hantering har även i fortsättningen åtkomst till MyApps från det inbyggda bokmärket för hanterad webbläsare.

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Nya ikoner för Managed Browser och företagsportalen <!--918433, 918431, 971473-->

Den hanterade webbläsaren får uppdaterade ikoner för både Android- och iOS-versionerna av appen. Den nya ikonen innehåller det uppdaterade Intune-märket så att det blir mer konsekvent med andra appar i Enterprise Mobility + Security (EM+S). Du kan se den nya ikonen för Managed Browser på sidan med [nyheter i användargränssnittet i Intune-appen](whats-new-app-ui.md).

Företagsportalen får också uppdaterade ikoner för Android-, iOS- och Windows-versioner av appen för att förbättra enhetligheten med andra appar i EM+S. Dessa ikoner släpps gradvis till plattformarna från april till slutet av maj.

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Förloppsindikator för inloggning i Android-företagsportalen <!--953374-->

En uppdatering av Android-företagsportalappen visar en förloppsindikator för inloggning när användaren startar eller återupptar appen. Indikatorn går igenom nya statusmeddelanden, med början på "Ansluter...", sedan "Loggar in...", följt av "Kontrollerar säkerhetskrav..." innan användaren kommer åt appen. Du kan se de nya skärmarna för företagsportalsappen för Android på [sidan Nyheter i användargränssnittet i Intune-appen](whats-new-app-ui.md).

#### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Blockera appar från åtkomst till SharePoint Online <!-- 679339 -->

Nu kan du skapa en appbaserad princip för Villkorsstyrd åtkomst för att blockera appar som inte har fått appprinciperna tillämpade från åtkomst till [SharePoint Online](app-based-conditional-access-intune-create.md). Du kan ange de appar som du vill ska ha åtkomst till SharePoint Online med Azure-portalen i det appbaserade scenariot för Villkorsstyrd åtkomst.

#### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Stöd för enkel inloggning från företagsportalen för iOS till Outlook för iOS <!--834012-->
Användarna behöver inte längre logga in i Outlook-appen om de är inloggade på företagsportalappen för iOS på samma enhet med samma konto. När användarna startar Outlook-appen kan de välja sitt konto och logga in automatiskt. Vi arbetar också med att lägga till den här funktionen för andra Microsoft-appar.

#### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Förbättrade statusmeddelanden i företagsportalappen för iOS <!--744866-->
Nya och mer specifika felmeddelanden visas nu i Företagsportalappen för iOS för att ger mer tillgänglig information om vad som händer i enheter. Dessa felärenden inkluderades tidigare i ett allmänt felmeddelande med titeln "Företagsportalen är för tillfället otillgänglig". Om en användare startar Företagsportalen på iOS när det inte finns en internetanslutning visas dessutom ett permanent statusfält på startsidan med texten "Ingen internetanslutning".

#### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Förbättrade appinstallationsstatus för företagsportalappen för Windows 10 <!--676495-->

Nya förbättringar för appinstallationer i företagsportalappen för Windows 10 är:
- Snabbare rapportering av installationsförlopp för MSI-paket
- Snabbare rapportering av installationsförlopp för moderna appar på enheter som kör Windows 10 Anniversary Update och nyare
- Ny förloppsindikator vid installation av moderna appar på enheter som kör Windows 10 Anniversary Update och nyare

Du kan se den nya förloppsindikatorn på sidan [nyheter i användargränssnittet i Intune-appen](whats-new-app-ui.md).

#### <a name="bulk-enroll-windows-10-devices----747607---"></a>Massregistrera Windows 10-enheter <!-- 747607 -->

Nu kan du ansluta ett stort antal enheter som kör Windows 10 Creators-uppdateringen till Azure Active Directory och Intune med Windows Configuration Designer (WCD). Aktivera [MDM-massregistrering](windows-bulk-enroll.md) för din Azure AD-klient genom att skapa ett konfigurationspaket som ansluter enheter till din Azure AD-klient med hjälp av Windows Configuration Designer. Tillämpa sedan paketet på de företagsägda enheter som du vill massregistrera och hantera. När paketet har tillämpats på dina enheter kommer Azure AD att anslutas, registreras i Intune och vara redo för att Azure AD-användarna ska logga in.  Azure AD-användare är standardanvändare på de här enheterna och tar emot tilldelade principer och nödvändiga appar. Självbetjäning och företagsportalscenarier stöds inte för närvarande.

### <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal--736542--"></a>Nyheter i den allmänt tillgängliga förhandsversionen av Intune i Azure-portalen<!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](whats-new.md).

Du kan se vad som är nytt i Intunes förhandsversion i Azure [här](whats-new.md).

### <a name="notices"></a>Meddelanden

#### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier <!--951869-->

För Intune-konto som har skapats senare än januari 2017 har Intune möjliggjort direktåtkomst till Apples-registreringsscenarier med arbetsbelastningen Registrera enheter i Azure Preview-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i Azure-portalen. Intune-konton som skapats före januari 2017 behöver migreras vid ett tillfälle innan de här funktionerna finns tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till förhandsversionen.

#### <a name="whats-coming-for-appx-in-intune-in-the-azure-portal----1000270---"></a>Nyheter för AppX i Intune på Azure-portalen <!-- 1000270 -->

Som en del av migreringen till Intune på Azure-portalen gör vi tre AppX-ändringar:

1. Vi lägger till en ny AppX-programtyp i Intune-konsolen som bara kan distribueras till MDM-registrerade enheter.
2. Vi ändrar syfte för den befintliga appx-apptypen så att den endast kan riktas mot datorer som hanteras via Intune PC-agenten.
3. Vi konverterar alla befintliga appx till MDM appx med migreringen.

##### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?

Detta påverkar inte någon av dina befintliga distributioner till enheter som hanteras via Intune PC-agenten. Efter migreringen kommer du dock inte att kunna distribuera dessa migrerade appx-versioner till nya enheter som hanteras via Intune PC-agenten och som inte utgjorde mål tidigare.

##### <a name="what-action-do-i-need-to-take"></a>Vad behöver jag göra

Efter migreringen behöver du överföra appx igen som en PC-appx om du vill göra nya PC-distributioner. Läs mer i [AppX-ändringar i Intune på Azure-portalen](https://aka.ms/appxchange) på Intune-supportteamets blogg.  

#### <a name="administration-roles-being-replaced-in-azure-portal"></a>Administratörsroller ersätts i Azure Portal

De befintliga MAM-administratörsrollerna (deltagare, ägare och skrivskyddat) som används i den klassiska Intune-portalen (Silverlight) ersätts med en helt ny uppsättning rollbaserade administratörskontroller (RBAC) i Intune Azure Portal. När du har migrerat till Azure Portal måste du tilldela dina administratörer dessa nya administratörsroller. Mer information om RBAC och nya de nya rollerna finns i [Rollbaserad åtkomstkontroll för Microsoft Intune](role-based-access-control.md).

### <a name="whats-coming"></a>Kommande nyheter

#### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Förbättrad inloggningsfunktion i företagsportalappar för alla plattformar <!--User Story 1132123-->

Vi informerar om en förändring som kommer under de kommande månaderna som kommer att förbättra inloggningen för Intune-företagsappar för Android, iOS och Windows. Det nya användargränssnittet visas automatiskt på alla plattformar för företagsportalappen när Azure AD genomför ändringen. Dessutom kan användarna nu logga in på företagsportalen från en annan enhet med en engångskod som genereras. Detta är särskilt användbart när användarna måste logga in utan autentiseringsuppgifter.

Du hittar skärmdumpar av föregående inloggning, den nya inloggningen med autentiseringsuppgifter och den nya inloggningen från en annan enhet på sidan [Nyheter i appens användargränssnitt](whats-new-app-ui.md).

#### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan för ändringar: Intune ändrar Intune-partnerportalens funktion <!-- 1050016 -->

Vi tar bort sidan Intune-Partner från manage.microsoft.com från och med tjänstuppdateringen i mitten på maj 2017.  

Om du är partneradministratör, kommer du inte längre att kunna visa och vidta åtgärder åt dina kunder från sidan Intune Partner. I stället måste du logga in på en av två andra partnerportaler hos Microsoft.

Både [Microsoft Partner Center](https://partnercenter.microsoft.com/) och [Microsoft 365-administrationscentret](https://admin.microsoft.com/) gör att du kan logga in på de kundkonton som du hanterar. I framtiden kan du som partner använda en av dessa webbplatser för att hantera dina kunder.


#### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->

Apple har tillkännagivit att de kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen.

Vi har gjort en version av företagsportalens app tillgänglig för iOS genom Apple TestFlight-programmet som genomdriver de nya ATS-kraven. Om du vill prova, så att du kan testa din ATS-kompatibilitet, kan du skicka ett e-post-meddelande till <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app"> CompanyPortalBeta@microsoft.com </a> med ditt förnamn, efternamn, din e-postadress och företagets namn. Läs [Intunes supportblogg](https://aka.ms/compportalats) för mer information.

## <a name="march-2017"></a>Mars 2017

### <a name="new-capabilities"></a>Nya funktioner

#### <a name="support-for-skycure"></a>Stöd för Skycure

Du kan nu styra åtkomsten från mobila enheter till företagsresurser med Villkorsstyrd åtkomst. Den baseras på riskbedömning som utförs av Skycure, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som kör Skycure och inkluderar:

- Fysiskt skydd
- Nätverksskydd
- Programskydd
- Skydd mot säkerhetsrisker

Du kan konfigurera EMS-principer för Villkorsstyrd åtkomst baserat på riskbedömningen i Symantec Endpoint Protection Mobile (Skycure), som aktiveras via Intunes principer för enhetsefterlevnad. Du kan använda dessa principer för att tillåta eller blockera inkompatibla enheters åtkomst till företagets resurser utifrån identifierade hot. Mer information finns i [Symantec Endpoint Protection Mobile-anslutningsprogram](skycure-mobile-threat-defense-connector.md).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622-->

Användargränssnittet för företagsportalappen för Android kommer att uppdateras för en mer modern känsla och bättre användarupplevelse. Viktiga uppdateringar är:

- Färger: Företagsportalens flikrubriker är färgade i enligt IT-område.
- Appar: På fliken **Appar** har knapparna **Aktuella appar** och **Alla appar** uppdaterats.
- Sökning: PÅ fliken **Sökning** är **Sökknappen** är nu flytande.
- Navigeringsappar: **Alla appar** visar en flikvy över **Aktuella**, **Alla** och **Kategorier** för att underlätta navigeringen.
- Support: Flikarna **Mina enheter** och **Kontakta IT** uppdateras för att göra dem mer läsbara.

Mer information om dessa ändringar finns i [UI-uppdateringar för Intunes slutanvändarappar](whats-new-app-ui.md).

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Icke-hanterade enheter kan komma åt tilldelade appar <!--664691-->

Som en del av designändringarna på företagsportalens webbplats ska iOS- och Android-användare kunna installera appar som har tilldelats dem som "tillgänglig utan registrering" på sina icke-hanterade enheter. Med sina Intune-autentiseringsuppgifter kan användare logga in på företagsportalens webbplats och se en lista över appar som tilldelats dem. App-paket för apparna som är "tillgängliga utan registrering" görs tillgängliga för hämtning via företagsportalens webbplats. Appar som kräver registrering för installation påverkas inte av den här ändringen, eftersom användarna uppmanas att registrera sina enheter om de vill installera apparna.

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Registrera skript för Windows 10-företagsportalen <!--941642-->

Om du behöver hämta och läsa in Windows 10-företagsportalsappen separat kan du nu använda ett skript för att förenkla och effektivisera appsigneringsprocessen för din organisation.   Information om hur du hämtar skriptet och anvisningarna om hur du använder det finns i [Microsoft Intune-signeringsskript för företagsportalen i Windows 10](https://aka.ms/win10cpscript) i TechNet-galleriet. Mer information om det här meddelandet finns i [Uppdatera din Windows 10-företagsportalsapp](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) på Intune Support-teambloggen.


### <a name="notices"></a>Meddelanden

#### <a name="support-for-ios-103"></a>Stöd för iOS 10.3

Version 10.3 av iOS började distribueras till iOS-användare den 27 mars 2017. Alla befintliga Intune MDM- och MAM-scenarion är kompatibla med senaste versionen av Apples operativsystem. Vi utgår från att alla befintliga Intune-funktioner som för närvarande är tillgängliga för hantering av iOS-enheter även kommer att fungera efter det att dina användare har uppgraderat sina enheter och appar till iOS 10.3.

Det finns för närvarande inga kända problem att rapportera. Om du stöter på problem med iOS 10.3 så kontakta gärna [Intunes supportgrupp](get-support.md).

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Förbättrade stödet för Android-användare i Kina <!--720444-->

På grund av avsaknad av Google Play-butik i Kina, måste Android-enheter hämta appar från kinesiska marknadsplatser. Företagsportalen kommer att stödja det här arbetsflödet genom att omdirigera Android-användare i Kina till att ladda ned appar för Företagsportalen och Outlook från lokala appbutiker. Detta förbättrar slutanvändarens upplevelse när principer för villkorlig åtkomst är tillämpliga, både för hantering av mobila enheter och för hantering av mobilappar. Appar för Företagsportalen och Outlook för Android är tillgängliga i följande kinesiska appbutiker:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](http://en.miui.com/thread-469541-1-1.html)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Bästa praxis: Se till att dina företagsportalsappar är aktuella <!--879465-->

I December 2016 släppte vi en uppdatering som framtvingande multifaktorautentisering (MFA) för en grupp användare när de registrerar en iOS-, Android-, Windows 8.1+- eller Windows Phone 8.1+-enhet. Den här funktionen fungerar inte utan vissa grundversioner av företagsportalsappen för Android (v5.0.3419.0+) och iOS (v2.1.17+).

Microsoft förbättrar kontinuerligt Intune genom att lägga till nya funktioner i både konsolen och företagsportalsapparna på alla de plattformar som stöds. Microsoft släpper därför bara korrigeringar för problem som vi hittar i den aktuella versionen av företagsportalsappen. Därför rekommenderar vi att du använder de senaste versionerna av företagsportalsapparna.

>[!Tip]
> Se till att användarna konfigurerar sina enheter så att de uppdaterar sina appar automatiskt från rätt appbutik. Om du har gjort en Android-företagsportalsapp tillgänglig på en nätverksresurs, så kan du hämta den senaste versionen från [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49140).

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>Microsoft Teams har nu aktiverats för MAM på iOS och Android

Microsoft har tillkännagivit Microsoft Teams är allmänt tillgängligt. De uppdaterade Microsoft Teams-apparna för iOS och Android har nu aktiverats med Intune MAM-funktioner, så du kan underlätta för dina grupper att arbeta fritt på olika enheter, samtidigt som skyddet för konversationer och företagsdata säkerställs i varje situation. Mer information finns i [Microsoft Teams-tillkänngagivandet](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) på bloggen Enterprise Mobility and Security.


## <a name="february-2017"></a>Februari 2017

### <a name="new-capabilities"></a>Nya funktioner

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisera företagsportalswebbplatsen <!--753980-->
Företagsportalens webbplats kommer att ha stöd för appar som är avsedda för användare som inte har några hanterade enheter. Webbplatsen anpassas med andra Microsoft-produkter och tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny", ![En liten bild på hamburgarmenyn som nu är tillagd i det övre vänstra hörnet på företagsportalens webbplats](./media/CP_hamburger_menu.png).

### <a name="notices"></a>Meddelanden

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>Gruppmigrering kräver inte några uppdateringar för grupper eller principer för iOS-enheter <!--898837-->
För varje Intune-enhetsgrupp som tilldelas i förväg av en profil för registrering av företagsenhet skapas en motsvarande dynamisk enhetsgrupp i AAD. Det görs baserat på namnet på profilen för registrering av företagsenhet under migreringen till Azure Active Directory-enhetsgrupper. Detta säkerställer att enheter automatiskt grupperas och tar emot samma principer och appar som den ursprungliga Intune-gruppen när de registreras.

När en klient startar migreringsprocessen för att gruppera och ange mål skapar Intune automatiskt en dynamisk AAD-grupp som motsvarar en Intune-grupp som är mål för en profil för registrering av företagsenheter. Om Intune-administratören tar bort Intune-målgruppen tas inte motsvarande dynamiska AAD-grupp bort. Gruppens medlemmar och den dynamiska frågan kommer att tas bort, men själva gruppen finns kvar tills IT-administratören tar bort den via AAD-portalen.

Och om IT-administratören ändrar vilken grupp Intune riktas mot av en profil för registrering av företagsenheter skapar Intune en ny dynamisk grupp som avspeglar den nya profiltilldelningen. Den nya dynamiska gruppen som har skapats för den gamla tilldelningen tas inte bort.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Standardbeteendet för hantering av Windows-skrivbordsenheter via Windows-inställningar <!--663050-->
Standardbeteendet för att registrera Windows 10-datorer ändras. Nya registreringar följer det normala MDM-agentregistreringsflödet i stället för via datoragenten. Webbplatsen för företagsportalen ger Windows 10 Desktop-användare registreringsanvisningar som leder dem genom processen med att lägga till Windows 10 Desktop-datorer som mobila enheter. Detta påverkar inte datorer som är registrerade och företaget kan fortfarande hantera Windows 10-datorer med datoragenten [om så önskas](manage-windows-pcs-with-microsoft-intune.md).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Förbättra stöd i hantering av mobila appar för selektiv rensning <!--581242-->
Slutanvändare får ytterligare vägledning om hur de kan återfå åtkomsten till arbets- eller skoldata som tas bort automatiskt till följd av principen "Offlineintervall innan appdata rensas".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Länkar till företagsportalen för iOS öppnas i appen <!--665954-->
Länkar i företagsportalappen för iOS, inklusive sådana som leder till dokumentation och appar, öppnas direkt i företagsportalappen med en Safari-vy i appen. Den här uppdateringen skickas separat från tjänstuppdateringen i januari.

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Ny MDM-serveradress för Windows-enheter <!--893007-->
Windows och Windows Phone-användare som försöker registrera en enhet misslyckas om de anger __manage.microsoft.com__ som MDM-serveradressen (om de uppmanas till det). MDM-serveradressen ändras från __manage.microsoft.com__ till __enrollment.manage.microsoft.com__ . Meddela användarna att de ska använda adressen __enrollment.manage.microsoft.com__ som MDM-serveradress om de tillfrågas om den under registreringen av en Windows- eller och Windows Phone-enhet. Inga ändringar krävs för din CNAME-installation. Mer information om den här ändringen finns på [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622-->
Från och med mars följer företagsportalsappen för Android [riktlinjer för materialdesign](https://material.io/guidelines/material-design/introduction.html) för att skapa en modernare känsla och ett modernare utseende. Den här förbättrade användarupplevelsen innehåller:

* __Färger__ : Flikrubriken kan färgas enligt din anpassade färgpalett.
* __Gränssnitt__ : Knapparna Aktuella appar och Alla appar har uppdaterats på fliken. Sökknappen är nu flytande.
* __Navigering__ : Alla appar visar en flikvy över Aktuella, Alla och Kategorier för att underlätta navigeringen.
* __Tjänst__ : Flikarna Mina enheter och Kontakta IT har förbättrad läsbarhet.

Du kan hitta före och efter-bilder på [sidan med UI-uppdateringar](whats-new-app-ui.md).

### <a name="associate-multiple-management-tools-with-the-microsoft-store-for-business---926135--"></a>Koppla flera hanteringsverktyg till Microsoft Store för företag <!--926135-->
Om du använder fler än ett hanteringsverktyg för att distribuera appar från Microsoft Store för företag kunde du tidigare bara koppla ett av dem till Microsoft Store för företag. Du kan nu koppla flera hanteringsverktyg till butiken, exempelvis Intune och Configuration Manager. Mer information finns i [Hantera appar som du har köpt från Microsoft Store för företag med Microsoft Intune](windows-store-for-business.md).

## <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal---736542--"></a>Nyheter i den allmänt tillgängliga förhandsversionen av Intune i Azure-portalen <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](whats-new.md).

Du kan se vad som är nytt i Intunes förhandsversion i Azure [här](whats-new.md).

## <a name="january-2017"></a>Januari 2017

### <a name="new-capabilities"></a>Nya funktioner

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Rapporter i konsolen för MAM utan registrering <!--677961-->
Nya rapporter för appskydd har lagts till för både registrerade enheter och enheter som inte har registrerats. Ta reda på mer om hur du kan [övervaka hanteringsprinciper för mobilappar med Intune](app-protection-policies-monitor.md).

#### <a name="android-711-support---694397--"></a>Stöd för Android 7.1.1 <!--694397-->
Intune har nu fullständigt stöd för och hantering av Android 7.1.1.

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Lös problemet med att iOS-enheterna är inaktiva eller att administratörskonsolen inte kan kommunicera med dem <!--unknown-->
När användarnas enheter förlorar kontakt med Intune kan du ge dem nya felsökningssteg för att hjälpa dem att återfå åtkomst till företagets resurser. Se [Enheterna är inaktiva eller så kan administratörskonsolen inte kommunicera med dem](troubleshoot-device-enrollment-in-intune.md#devices-are-inactive-or-the-admin-console-cant-communicate-with-them).

### <a name="notices"></a>Meddelanden

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Standardbeteendet för hantering av Windows-skrivbordsenheter via Windows-inställningar <!--663050-->
Standardbeteendet för att registrera Windows 10-datorer ändras. Nya registreringar följer det normala MDM-agentregistreringsflödet i stället för via datoragenten.

Webbplatsen för företagsportalen ger Windows 10 Desktop-användare registreringsanvisningar som leder dem genom processen med att lägga till Windows 10 Desktop-datorer som mobila enheter. Detta påverkar inte datorer som är registrerade och företaget kan fortfarande hantera Windows 10-datorer med datoragenten [om så önskas](manage-windows-pcs-with-microsoft-intune.md).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Förbättra stöd i hantering av mobila appar för selektiv rensning <!--581242-->
Slutanvändare får ytterligare vägledning om hur de kan återfå åtkomsten till arbets- eller skoldata som tas bort automatiskt till följd av principen "Offlineintervall innan appdata rensas".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Länkar till företagsportalen för iOS öppnas i appen <!--665954-->
Länkar i företagsportalappen för iOS, inklusive sådana som leder till dokumentation och appar, öppnas direkt i företagsportalappen med en Safari-vy i appen. Den här uppdateringen skickas separat från tjänstuppdateringen i januari.

#### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisera företagsportalswebbplatsen <!--753980-->
Från och med februari kommer företagsportalens webbplats att ha stöd för appar som är avsedda för användare som inte har några hanterade enheter. Webbplatsen anpassas med andra Microsoft-produkter och tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny", ![Hamburgarmeny på företagsportalens webbplats](./media/CP_hamburger_menu.png).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>Ny dokumentation för appskyddsprinciper <!--583398-->
Vi har uppdaterat dokumentationen för administratörer och apputvecklare som vill aktivera appskyddsprinciper (kallas MAM-principer) i sina iOS- och Android-appar med Intune programhanteringsverktyg eller Intune App SDK.

Följande artiklar har uppdaterats:

* [Förbereda appar för hantering av mobilprogram med Microsoft Intune](apps-prepare-mobile-application-management.md)
* [Förbereda iOS-appar för hantering av mobilprogram med Intunes programhanteringsverktyg](app-wrapper-prepare-ios.md)
* [Kom igång med Microsoft Intune App SDK](app-sdk-get-started.md)
* [Utvecklarhandbok för Intune App SDK för iOS](app-sdk-ios.md)

Följande artiklar har nya tillägg i dokumentbiblioteket:

* [Intune App SDK Cordova-insticksprogrammet](app-sdk-cordova.md)
* [Intune App SDK Xamarin-komponenten](app-sdk-xamarin.md)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Förloppsindikator när företagsportalappen startas i iOS <!--665978-->
Företagsportalen för iOS lanserar en förloppsindikator på startskärmen som ger användaren information om de inläsningsprocesser som sker. Det kommer att ske ett stegvist införande av förloppsindikatorn som ersätter rotationsrutan. Det innebär att vissa av användarna ser den nya förloppsindikatorn medan andra kommer att fortsätta se rotationsrutan.

## <a name="december-2016"></a>December 2016

### <a name="public-preview-of-intune-in-the-azure-portal--736542--"></a>Den allmänt tillgängliga förhandsversionen av Intune i Azure-portalen<!--736542-->
Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er. Innan den här portalen får allmän tillgång för alla klienter i Intune, är vi glada att kunna meddela att vi ska börja lansera en förhandsversion av den här nya administratörupplevelsen senare denna månad för att välja klienter.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Under tiden kan du ta reda på mer om vad vi har på lager för Microsoft Intune i Azure-portalen i vår [nya dokumentation](/intune/what-is-intune).

__Integrering av hantering av telekomkostnad i den offentliga förhandsversionen av Azure-portalen__ <!--747605-->
Vi börjar nu att förhandsgranska integrering med tredje parters hantering av telekomkostnad (TEM) i Azure-portalen. Du kan använda Intune för att tvinga gränser för nationell och central dataanvändning. Vi börjar de här integreringarna med [Saaswedo](http://www.saaswedo.com/). Om du vill aktivera den här funktionen i utvärderingsversionen av klienten kan du [kontakta Microsoft Support](get-support.md).

### <a name="new-capabilities"></a>Nya funktioner

__Multifaktorautentisering på alla plattformar__ <!--747590-->
Du kan nu använda multifaktorautentisering (MFA) på en grupp av användare när de registrerar en iOS-, Android-, Windows 8.1+- eller Windows Phone 8.1+-enhet från Azure-hanteringsportalen genom att konfigurera MFA på registreringsprogrammet för Microsoft Intune i Azure Active Directory.

__Möjlighet att begränsa registrering av mobila enheter__ <!--747596-->
Intune lägger till nya registreringsbegränsningar som avgör vilka plattformar som mobila enheter ska kunna registrera. Intune skiljer mellan mobilplattformar som iOS, macOS, Android, Windows och Windows Mobile.
* Begränsningen av registrering av mobila enheter begränsar inte registreringen av datorklienter.
* För iOS finns det ytterligare ett alternativ för att blockera registrering av personligt ägda enheter.

Intune markerar alla nya enheter som personliga såvida inte IT-administratören vidtar åtgärder för att markera dem som företagsägda, vilket beskrivs i [den här artikeln](device-enrollment.md).

### <a name="notices"></a>Meddelanden

__Multifaktorautentisering vid registrering flyttar till Azure-portalen__ <!--VSO 750545-->
Administratörer gick tidigare till Intune-konsolen eller konsolen Konfigurationshanteraren (tidigare än versionen oktober 2016) för att ange MFA för Intune-registreringar. Med den här uppdaterade funktionen kommer du nu att logga in på [Microsoft Azure-portalen](https://manage.windowsazure.com) med dina Intune-autentiseringsuppgifter och konfigurera MFA-inställningar via Azure AD. Mer information om detta finns [här](https://aka.ms/mfa_ad).

__Företagsportalappen för Android är nu tillgänglig i Kina__  <!--VSO 658093-->
Vi publicerar företagsportalappen för Android för hämtning i Kina. På grund av avsaknad av Google Play-butik i Kina, måste Android-enheter hämta appar från kinesiska appmarknadsplatser. Företagsportalappen för Android blir tillgänglig för hämtning på följande platser:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](http://en.miui.com/thread-469541-1-1.html)

Företagsportalappen för Android använder Google Play-tjänster för att kommunicera med Microsoft Intune-tjänsten. Eftersom Google Play-tjänster ännu inte är tillgängliga i Kina, kan utförandet av någon av följande aktiviteter ta upp till 8 timmar att slutföra. 

|Administrationskonsolen för Intune| Intune-företagsportalsapp för Android |Intune-företagsportalens webbplats|   
|---|---|---|
|Fullständig rensning| Ta bort en fjärransluten enhet| Ta bort enhet (lokal och fjärransluten)|
|Selektiv rensning| Återställ enhet| Återställ enhet|
|Nya eller uppdaterade appdistributioner| Installera tillgängliga branschspecifika appar| Återställning av enhetens lösenord|
|Fjärrlåsning|||
|Återställning av lösenord|||

### <a name="deprecations"></a>Föråldringar

__Firefox har inte längre stöd för Silverlight__ <!--VSO TBA-->
Mozilla tar bort sitt stöd för Silverlight i version 52 av [webbläsaren Firefox](https://www.mozilla.org/firefox), sker i mars 2017. Därför kommer du inte längre att kunna logga in på den befintliga Intune-konsolen med Firefox-versioner som är större än 51. Vi rekommenderar att du använder Internet Explorer 10 eller 11 för att komma åt administrationskonsolen, eller en [version av Firefox före version 52](https://ftp.mozilla.org/pub/firefox/releases/). Intunes övergång till Azure-portalen gör att den stöder ett antal [moderna webbläsare](/azure/azure-preview-portal-supported-browsers-devices) utan att vara beroende av Silverlight.

__Borttagning av principer för den mobila inkorgen i Exchange Online__ <!--770687-->
Från och med december kommer administratörer inte längre att kunna visa eller konfigurera principer för mobila postlådor för Exchange Online (EAS) i Intune-konsolen. Den här ändringen kommer att lanseras till alla klienter i Intune under december och januari. Alla befintliga principer kommer att förbli såsom konfigurerade. Använd Exchange Management Shell för att konfigurera nya principer. Ta reda på mer [här](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx).

__Apparna Intune AV Player, Image Viewer och PDF Viewer stöds inte längre på Android__ <!--747553-->
Från mitten av december 2016 och framåt kommer användarna inte längre att kunna använda apparna Intune AV Player, Image Viewer och PDF Viewer. De här apparna har ersatts med appen Azure Information Protection. Lär dig mer om appen Azure Information Protection [här](/information-protection/rms-client/mobile-app-faq).

## <a name="november-2016"></a>November 2016

### <a name="new-capabilities"></a>Nya funktioner

__Nya Microsoft Intune-företagsportalen för Windows 10-enheter__ Microsoft har lanserat en ny [Microsoft Intune-företagsportalsapp för Windows 10-enheter](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Den här appen, som använder det nya Windows 10 Universal-formatet, ger en uppdaterad användarupplevelse i appen och identiska miljöer på alla Windows 10-enheter, både på datorer och mobila enheter, med samma funktioner som användarna redan använder.

Med den nya appen kan användarna dessutom dra nytta av ytterligare plattformsfunktioner som enkel inloggning (SSO) och certifikatbaserad autentisering på Windows 10-enheter. Appen kommer att vara tillgänglig som en uppgradering till de befintliga installationerna av Windows 8.1-företagsportalen och Windows Phone 8.1-företagsportalen från Microsoft Store. Mer information finns på [aka.ms/intunecp_universalapp](https://aka.ms/intunecp_universalapp).

> [!IMPORTANT]
> __En uppdatering om Intune och Android for Work__ Även om du kan distribuera Android for Work-appar med åtgärden __Krävs__ kan du bara distribuera appar som __Tillgängliga__ om dina Intune-grupper har migrerats till den nya Azure AD-gruppmiljön.

__Intune App SDK för Cordova-plugin har nu stöd för MAM utan registrering__ Nu kan apputvecklare använda Intune App SDK för Cordova-plugin-programmet för att aktivera MAM-funktioner utan enhetsregistrering i deras Cordova-baserade appar för Android och iOS. Intune App SDK för Cordova-plugin-programmet finns [här](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

__Intune App SDK Xamarin-komponenten har nu stöd för MAM utan registrering__ Nu kan apputvecklare använda Intune App SDK Xamarin-komponenten för att aktivera MAM-funktioner utan enhetsregistrering i deras Xamarin-baserade appar för Android och iOS. Intune App SDK Xamarin-komponenten finns [här](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

### <a name="notices"></a>Meddelanden

__Symantec signeringscertifikat kräver inte längre signerad Windows Phone 8-företagsportal för överföring__ Överföring av Symantec signeringscertifikat kommer inte längre att behöva en signerad företagsportalapp för Windows Phone 8. Certifikatet kan överföras fristående.

### <a name="deprecations"></a>Föråldringar

__Stöd för Windows Phone 8-företagsportalen__ Stöd för Windows Phone 8-företagsportalen kommer att upphöra. Stöd för Windows Phone 8- och WinRT-plattformarna upphörde oktober 2016. Stöd för Windows Phone 8-företagsportalen upphörde också det oktober 2016.


## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).
