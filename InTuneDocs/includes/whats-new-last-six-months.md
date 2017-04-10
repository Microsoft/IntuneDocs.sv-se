# <a name="february-2017"></a>Februari 2017

## <a name="new-capabilities"></a>Nya funktioner

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisera företagsportalswebbplatsen <!--753980-->
Företagsportalens webbplats kommer att ha stöd för appar som är avsedda för användare som inte har några hanterade enheter. Webbplatsen anpassas med andra Microsoft-produkter och -tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny" ![Liten bild på hamburgarmenyn som nu är tillagd i det övre vänstra hörnet på företagsportalens webbplats](/intune/whats-new/media/CP_hamburger_menu.png) som innehåller kontaktinformation till supportavdelningen och information om befintliga hanterade enheter. Landningssidan ordnas om för att betona appar som är tillgängliga för användare med karuseller för aktuella och nyligen uppdaterade appar. Du kan hitta före och efter-bilder som är tillgängliga på [sidan med UI-uppdateringar](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

## <a name="notices"></a>Meddelanden

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>Gruppmigrering kräver inte några uppdateringar för grupper eller principer för iOS-enheter<!--898837-->
För varje Intune-enhetsgrupp som tilldelas i förväg av en profil för registrering av företagsenhet skapas en motsvarande dynamisk enhetsgrupp i AAD. Det görs baserat på namnet på profilen för registrering av företagsenhet under migreringen till Azure Active Directory-enhetsgrupper. Detta säkerställer att enheter automatiskt grupperas och tar emot samma principer och appar som den ursprungliga Intune-gruppen när de registreras.

När en klient startar migreringsprocessen för att gruppera och ange mål skapar Intune automatiskt en dynamisk AAD-grupp som motsvarar en Intune-grupp som är mål för en profil för registrering av företagsenheter. Om Intune-administratören tar bort Intune-målgruppen tas inte motsvarande dynamiska AAD-grupp bort. Gruppens medlemmar och den dynamiska frågan kommer att tas bort, men själva gruppen finns kvar tills IT-administratören tar bort den via AAD-portalen.

Och om IT-administratören ändrar vilken grupp Intune riktas mot av en profil för registrering av företagsenheter skapar Intune en ny dynamisk grupp som avspeglar den nya profiltilldelningen. Den nya dynamiska gruppen som har skapats för den gamla tilldelningen tas inte bort.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Standardvärde för hantering av Windows Desktop-enheter via Windows-inställningar <!--663050-->
Standardbeteendet för att registrera Windows 10-datorer ändras. Nya registreringar följer det normala MDM-agentregistreringsflödet i stället för via datoragenten. Webbplatsen för företagsportalen ger Windows 10 Desktop-användare registreringsanvisningar som leder dem genom processen med att lägga till Windows 10 Desktop-datorer som mobila enheter. Detta påverkar inte datorer som är registrerade och företaget kan fortfarande hantera Windows 10-datorer med datoragenten [om så önskas](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Förbättra stöd i hantering av mobila appar för selektiv rensning <!--581242-->
Slutanvändare får ytterligare vägledning för hur de kan återfå åtkomsten till arbets- eller skoldata som tas bort automatiskt till följd av principen "Offlineintervall innan appdata rensas".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Länkar till företagsportalen för iOS öppnas i appen <!--665954-->
Länkar i företagsportalappen för iOS, inklusive sådana som leder till dokumentation och appar, öppnas direkt i företagsportalappen med en Safari-vy i appen. Den här uppdateringen skickas separat från tjänstuppdateringen i januari.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Ny MDM-serveradress för Windows-enheter <!--893007-->
Windows och Windows Phone-användare som försöker registrera en enhet misslyckas om de anger __manage.microsoft.com__ som MDM-serveradressen (om de uppmanas till det). MDM-serveradressen ändras från __manage.microsoft.com__ till __enrollment.manage.microsoft.com__. Meddela användarna att de ska använda adressen __enrollment.manage.microsoft.com__ som MDM-serveradress om de tillfrågas om den under registreringen av en Windows- eller och Windows Phone-enhet. Inga ändringar krävs för din CNAME-installation. Mer information om den här ändringen finns på [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622-->
Från och med mars följer företagsportalsappen för Android [riktlinjer för materialdesign](https://material.io/guidelines/material-design/introduction.html) för att skapa en modernare känsla och ett modernare utseende. Den här förbättrade användarupplevelsen innehåller:

* __Färger__: Flikrubriken kan färgas enligt din anpassade färgpalett.
* __Gränssnitt__: Knapparna Aktuella appar och Alla appar har uppdaterats på fliken. Sökknappen är nu flytande.
* __Navigering__: Alla appar visar en flikvy över Aktuella, Alla och Kategorier för att underlätta navigeringen.
* __Tjänst__: Flikarna Mina enheter och Kontakta IT har förbättrad läsbarhet.

Du kan hitta före och efter-bilder på [sidan med UI-uppdateringar](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Koppla flera hanteringsverktyg till Windows Store för företag<!--926135-->
Om du använder fler än ett hanteringsverktyg för att distribuera Windows Store för affärsappar kunde du tidigare bara koppla ett av dem till Windows Store för företag. Du kan nu koppla flera hanteringsverktyg till butiken, exempelvis Intune och Configuration Manager. Mer information finns i [Hantera appar som du har köpt från Windows Store för företag med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Vad är nytt i den offentliga förhandsversion av Intunes adminstratörsupplevelse på Azure <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](https://docs.microsoft.com/intune-azure/introduction/whats-new).

Du kan se vad som är nytt i Intunes förhandsversion i Azure [här](https://docs.microsoft.com/intune-azure/introduction/whats-new).

## <a name="january-2017"></a>Januari 2017

### <a name="new-capabilities"></a>Nya funktioner

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Rapporter i konsolen för MAM utan registrering <!--677961-->
Nya rapporter för appskydd har lagts till för både registrerade enheter och enheter som inte har registrerats. Lär dig mer om hur du kan [övervaka hanteringsprinciper för mobilappar med Intune här](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

#### <a name="android-711-support---694397--"></a>Stöd för Android 7.1.1 <!--694397-->
Intune har nu fullständigt stöd för och hantering av Android 7.1.1.

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Lös problemet med att iOS-enheterna är inaktiva eller att administratörskonsolen inte kan kommunicera med dem <!--unknown-->
När användarnas enheter förlorar kontakt med Intune kan du ge dem nya felsökningssteg för att hjälpa dem att återfå åtkomst till företagets resurser. Se [Enheterna är inaktiva eller så kan administratörskonsolen inte kommunicera med dem](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="notices"></a>Meddelanden

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Standardvärde för hantering av Windows Desktop-enheter via Windows-inställningar <!--663050-->
Standardbeteendet för att registrera Windows 10-datorer ändras. Nya registreringar följer det normala MDM-agentregistreringsflödet i stället för via datoragenten.

Webbplatsen för företagsportalen ger Windows 10 Desktop-användare registreringsanvisningar som leder dem genom processen med att lägga till Windows 10 Desktop-datorer som mobila enheter. Detta påverkar inte datorer som är registrerade och företaget kan fortfarande hantera Windows 10-datorer med datoragenten [om så önskas](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Förbättra stöd i hantering av mobila appar för selektiv rensning <!--581242-->
Slutanvändare får ytterligare vägledning för hur de kan återfå åtkomsten till arbets- eller skoldata som tas bort automatiskt till följd av principen "Offlineintervall innan appdata rensas".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Länkar till företagsportalen för iOS öppnas i appen <!--665954-->
Länkar i företagsportalappen för iOS, inklusive sådana som leder till dokumentation och appar, öppnas direkt i företagsportalappen med en Safari-vy i appen. Den här uppdateringen skickas separat från tjänstuppdateringen i januari.

#### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisera företagsportalswebbplatsen <!--753980-->
Från och med februari kommer företagsportalens webbplats att ha stöd för appar som är avsedda för användare som inte har några hanterade enheter. Webbplatsen anpassas med andra Microsoft-produkter och tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny" ![Hamburgarmenyn på företagsportalens webbplats](/Intune/whats-new/media/CP_hamburger_menu.png) som innehåller kontaktinformation till supportavdelningen och information om befintliga hanterade enheter. Landningssidan ordnas om för att betona appar som är tillgängliga för användare med karuseller för aktuella och nyligen uppdaterade appar. Före- och efterbilder finns på [sidan med information om nyheter i Intune-appens användargränssnitt](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>Ny dokumentationen för appskyddsprinciper<!--583398-->
Vi har uppdaterat dokumentationen för administratörer och apputvecklare som vill aktivera appskyddsprinciper (kallas MAM-principer) i sina iOS- och Android-appar med Intune programhanteringsverktyg eller Intune App SDK.

Följande artiklar har uppdaterats:

* [Förbereda appar för hantering av mobilprogram med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Förbereda iOS-appar för hantering av mobilprogram med Intunes programhanteringsverktyg](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Kom igång med Microsoft Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Utvecklarhandbok för Intune App SDK för iOS](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

Följande artiklar har nya tillägg i dokumentbiblioteket:

* [Intune App SDK Cordova-insticksprogrammet](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Intune App SDK Xamarin-komponenten](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Förloppsindikator när företagsportalappen startas i iOS <!--665978-->
Företagsportalen för iOS lanserar en förloppsindikator på startskärmen som ger användaren information om de inläsningsprocesser som sker. Det kommer att ske ett stegvist införande av förloppsindikatorn som ersätter rotationsrutan. Det innebär att vissa av användarna ser den nya förloppsindikatorn medan andra kommer att fortsätta se rotationsrutan.

## <a name="december-2016"></a>December 2016

### <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Offentlig förhandsversion av den nya Intune-adminstratörsupplevelsen på Azure <!--736542-->
Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er. Innan den här portalen får allmän tillgång för alla klienter i Intune, är vi glada att kunna meddela att vi ska börja lansera en förhandsversion av den här nya administratörupplevelsen senare denna månad för att välja klienter.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Under tiden kan du ta reda på mer om vad vi har på lager för Microsoft Intune i Azure-portalen i vår [nya dokumentation](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

__Integrering av telekomkostnadshantering i förhandsversionen av Azure-portalen__ <!--747605-->Vi börjar nu att förhandsgranska integrering med tredje parters hantering av telekomkostnad (TEM) i Azure-portalen. Du kan använda Intune för att tvinga gränser för nationell och central dataanvändning. Vi börjar de här integreringarna med [Saaswedo](http://www.saaswedo.com). Om du vill aktivera den här funktionen i utvärderingsversionen av klienten kan du [kontakta Microsoft Support](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="new-capabilities"></a>Nya funktioner

__Multifaktorautentisering på alla plattformar__ <!--747590--> Du kan nu använda multifaktorautentisering (MFA) på en grupp av användare när de registrerar en iOS-, Android-, Windows 8.1+- eller Windows Phone 8.1+-enhet från Azure-hanteringsportalen genom att konfigurera MFA på registreringsprogrammet för Microsoft Intune i Azure Active Directory.

__Möjlighet att begränsa registrering av mobila enheter__ <!--747596--> Intune lägger till nya registreringsbegränsningar som avgör vilka plattformar som mobila enheter ska kunna registrera. Intune skiljer mellan mobilplattformar som iOS, macOS, Android, Windows och Windows Mobile.
* Begränsningen av registrering av mobila enheter begränsar inte registreringen av datorklienter.
* För iOS finns det ytterligare ett alternativ för att blockera registrering av personligt ägda enheter.

Intune markerar alla nya enheter som personliga såvida inte IT-administratören vidtar åtgärder för att markera dem som företagsägda, vilket beskrivs i [den här artikeln](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

### <a name="notices"></a>Meddelanden

__Multifaktorautentisering vid registrering flyttar till Azure-portalen__ <!--VSO 750545--> Administratörer gick tidigare till Intune-konsolen eller konsolen Konfigurationshanteraren (tidigare än versionen oktober 2016) för att ange MFA för Intune-registreringar. Med den här uppdaterade funktionen kommer du nu att logga in på [Microsoft Azure-portalen](https://manage.windowsazure.com) med dina Intune-autentiseringsuppgifter och konfigurera MFA-inställningar via Azure AD. Mer information om detta finns [här](https://aka.ms/mfa_ad).

__Företagsportalappen för Android är nu tillgänglig i Kina__ <!--VSO 658093--> Vi publicerar företagsportalappen för Android för hämtning i Kina. På grund av avsaknad av Google Play-butik i Kina, måste Android-enheter hämta appar från kinesiska appmarknadsplatser. Företagsportalappen för Android blir tillgänglig för hämtning på följande platser:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

Företagsportalappen för Android använder Google Play-tjänster för att kommunicera med Microsoft Intune-tjänsten. Eftersom Google Play-tjänster ännu inte är tillgängliga i Kina, kan utförandet av någon av följande aktiviteter ta upp till 8 timmar att slutföra. 

|Administrationskonsolen för Intune| Intune-företagsportalsapp för Android |Intune-företagsportalens webbplats|   
|---|---|---|
|Fullständig rensning| Ta bort en fjärransluten enhet| Ta bort enhet (lokal och fjärransluten)|
|Selektiv rensning| Återställ enhet| Återställ enhet|
|Nya eller uppdaterade appdistributioner| Installera tillgängliga branschspecifika appar| Återställning av enhetens lösenord|
|Fjärrlåsning|||
|Återställning av lösenord|||

### <a name="deprecations"></a>Föråldringar

__Firefox ska inte längre ha stöd för Silverlight__ <!--VSO TBA--> Mozilla tar bort sitt stöd för Silverlight i version 52 av [webbläsaren Firefox](https://www.mozilla.org/firefox), sker i mars 2017. Därför kommer du inte längre att kunna logga in på den befintliga Intune-konsolen med Firefox-versioner som är större än 51. Vi rekommenderar att du använder Internet Explorer 10 eller 11 för att komma åt administrationskonsolen, eller en [version av Firefox före version 52](https://ftp.mozilla.org/pub/firefox/releases/). Intunes övergång till Azure-portalen gör att den stöder ett antal [moderna webbläsare](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices) utan att vara beroende av Silverlight.

__Borttagning av principer för Exchange Online mobila inkorgar__ <!--770687--> Från och med december kommer administratörer inte längre att kunna visa eller konfigurera principer för mobila postlådor för Exchange Online (EAS) i Intune-konsolen. Den här ändringen kommer att lanseras till alla klienter i Intune under december och januari. Alla befintliga principer kommer att förbli såsom konfigurerade. Använd Exchange Management Shell för att konfigurera nya principer. Ta reda på mer [här](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

__Apparna Intune AV Player, Image Viewer och PDF Viewer stöds inte längre på Android__ <!--747553--> Från mitten av december 2016 och framåt kommer användarna inte längre att kunna använda apparna Intune AV Player, Image Viewer och PDF Viewer. De här apparna har ersatts med appen Azure Information Protection. Lär dig mer om appen Azure Information Protection [här](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

## <a name="november-2016"></a>November 2016

### <a name="new-capabilities"></a>Nya funktioner

__Nya Microsoft Intune-företagsportalen för Windows 10-enheter__ Microsoft har lanserat en ny [Microsoft Intune-företagsportalsapp för Windows 10-enheter](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Den här appen, som använder det nya Windows 10 Universal-formatet, ger en uppdaterad användarupplevelse i appen och identiska miljöer på alla Windows 10-enheter, både på datorer och mobila enheter, med samma funktioner som användarna redan använder.

Med den nya appen kan användarna dessutom dra nytta av ytterligare plattformsfunktioner som enkel inloggning (SSO) och certifikatbaserad autentisering på Windows 10-enheter. Appen kommer att vara tillgänglig som en uppgradering till de befintliga installationerna av Windows 8.1-företagsportalen och Windows Phone 8.1-företagsportalen från Windows Store. Mer information finns på [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).

> [!IMPORTANT]
> __En uppdatering om Intune och Android for Work__ Även om du kan distribuera Android for Work-appar med åtgärden __Krävs__ kan du bara distribuera appar som __Tillgängliga__ om dina Intune-grupper har migrerats till den nya Azure AD-gruppmiljön.

__Intune App SDK för Cordova-plugin har nu stöd för MAM utan registrering__ Nu kan apputvecklare använda Intune App SDK för Cordova-plugin-programmet för att aktivera MAM-funktioner utan enhetsregistrering i deras Cordova-baserade appar för Android och iOS. Intune App SDK för Cordova-plugin-programmet finns [här](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

__Intune App SDK Xamarin-komponenten har nu stöd för MAM utan registrering__ Nu kan apputvecklare använda Intune App SDK Xamarin-komponenten för att aktivera MAM-funktioner utan enhetsregistrering i deras Xamarin-baserade appar för Android och iOS. Intune App SDK Xamarin-komponenten finns [här](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

### <a name="notices"></a>Meddelanden

__Symantec signeringscertifikat kräver inte längre signerad Windows Phone 8-företagsportal för överföring__ Överföring av Symantec signeringscertifikat kommer inte längre att behöva en signerad företagsportalapp för Windows Phone 8. Certifikatet kan överföras fristående.

###<a name="deprecations"></a>Föråldringar

__Stöd för Windows Phone 8-företagsportalen__ Stöd för Windows Phone 8-företagsportalen kommer att upphöra. Stöd för Windows Phone 8- och WinRT-plattformarna upphörde oktober 2016. Stöd för Windows Phone 8-företagsportalen upphörde också det oktober 2016.

## <a name="october-2016"></a>Oktober 2016

### <a name="conditional-access-for-mobile-application-management"></a>Villkorlig åtkomst för hantering av mobila program
Du kommer att kunna begränsa åtkomsten till Exchange Online så att åtkomst endast kan ges genom appar som stöder Intunes hanteringsprinciper för mobilprogram, som till exempel Outlook. [Den här nya funktionen](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) passar perfekt ihop med Intune MAM-principer (mobile app management) eftersom du kan blockera åtkomst till inbyggda e-postklienter eller andra appar som inte har konfigurerats med Intune MAM-principerna. Detta garanterar att dina användare har åtkomst till din organisations data med appar som kan skyddas med Intune MAM. Du kan komma igång med hantering av mobilappar i Intune via Azure Portal. Leta efter det nya avsnittet om villkorlig åtkomst i bladet ”Inställningar”.

### <a name="conditional-access-for-windows-pcs"></a>Villkorlig åtkomst för Windows-datorer
Nu kan du skapa principer för villkorlig åtkomst via Intune-administratörskonsolen om du vill blockera Windows-datorer från att få åtkomst till [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) och [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune). Du kan även skapa principer för villkorlig åtkomst för att blockera åtkomst till stationära och universella Office-program.

### <a name="android-for-work-support"></a>Stöd för Android for Work

> [!IMPORTANT]

> Även om du kan distribuera Android for Work-appar med åtgärden __Krävs__ kan du bara distribuera appar som __tillgängliga__ om Intune-grupper har migrerats till den nya Azure AD-gruppmiljön.

Intune är nu en del av Android for Work-programmet (AfW). Vi kommer att börja att implementera stöd för AfW-funktioner den här månaden och fortsätta under de kommande månaderna. Observera att den tillgängliga appdistributionen för AfW utnyttjar den nya grupperings- och målmiljön. Nyligen etablerade Intune Service-konton kan använda den här funktionen när AfW är tillgängligt för dem.

[Läs Microsofts tillkännagivande om Intune-stöd för Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Följande avsnitt för Intune är nya eller uppdaterade med information om Android for Work:

För IT-proffs:
- [Konfigurera Android for Work](/intune/deploy-use/set-up-android-for-work)
- [Begränsa åtkomsten för e-post till Exchange Online och nya Exchange Online Dedicated med Microsoft Intune](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Begränsa e-poståtkomsten till Exchange On-premises och äldre Exchange Online Dedicated med Microsoft Intune](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Inställningar för policy för efterlevnad för Android for Work](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Så här distribuerar du Android for Work-appar](/intune/deploy-use/android-for-work-apps)
- [Konfigurera Android for Work-appar med konfigurationsprinciper för mobilappar](/intune/deploy-use/afw-app-configuration-policy)
- [Principinställningar för Android for Work](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

För slutanvändare:
- [Vad händer när du skapar en arbetsprofil](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Skapa en arbetsprofil och registrera din enhet i Intune](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>Lookout-integration för att skydda iOS-enheter
Från och med oktober integrerar Microsoft med Lookouts lösning för skydd mot mobilhot för att skydda mobila Android-enheter genom att exempelvis identifiera skadlig kod och riskfyllda appar på enheter. Lookouts lösning hjälper dig att bestämma hotnivån, vilken kan konfigureras. Du kan skapa en regel för policy för efterlevnad i Intune för att fastställa enhetens efterlevnad baserat på riskbedömningen av Lookout. Genom att använda åtkomstprinciper kan du tillåta eller blockera åtkomst till företagsresurser utifrån enhetens efterlevnadsstatus.

Slutanvändare med icke-kompatibla iOS-enheter uppmanas att registrera sig och måste installera Lookout for Work-appen på sina enheter, aktivera appen och åtgärda hot som rapporteras i Lookout for Work-appen för att få åtkomst. Lär dig hur du [konfigurerar och distribuerar Lookout for work-appar](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

### <a name="intune-app-wrapping-tool-for-android"></a>Intunes programhanteringsverktyg för Android
Du kan konfigurera dina appar att använda Intune MAM-principer för hantering av mobilprogram med hjälp av Intunes programhanteringsverktyg. Nu finns stöd för Intune MAM-principer utan krav på enhetsregistrering.

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>Hantera utskrifter från appar som hanteras med hjälp av MAM-principer
Nu kan du förhindra utskrift av företagsdata från appar som har MAM-principer. Den här inställningen är tillgänglig på [Azure-portalen](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) och stöds på både [iOS](/Intune/deploy-use/ios-mam-policy-settings)- och [Android](/Intune/deploy-use/android-mam-policy-settings)-enheter.
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Stöd för fingeravtryck på Android-enheter
Nu ger hanteringsprinciper för mobila Android-appar (MAM) användare åtkomst till en app med deras fingeravtryck i stället för med en PIN-kod. Se den här och andra [MAM-principinställningar för Android här](/Intune/deploy-use/android-mam-policy-settings).

### <a name="notices"></a>Meddelanden

__Android Samsung KNOX-kompatibilitet med Intune__ Vissa modeller av Samsung Galaxy Ace-telefonen kan inte hanteras av Intune som Samsung KNOX-enheter. När du registrerar dessa enheter med Intune hanteras de i stället som Android-standardenheter.

Följande modellnummer påverkas:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Du och dina slutanvändare behöver inte vidta någon ytterligare åtgärd. Mer information finns på webbplatsen för [Samsung KNOX](https://www.samsungknox.com).

__Företagsportalappen för Windows 8 är föråldrad; stödet för Windows Phone 8- och Windows RT-plattformarna upphör snart__ Från och med oktober 2016 kommer Microsoft Intune att dra in stödet för företagsportalen för Windows 8. Microsoft Intunes stöd för Windows Phone 8- och Windows RT-plattformarna upphör också snart. Det betyder att du inte kommer att kunna registrera eller uppdatera Windows Phone 8- eller Windows RT-enheter.

Men du kan fortsätta att hantera Windows Phone 8-, Windows RT- och Windows 8-enheter som redan har registrerats. Uppdatera enheter med Windows Phone 8 och Windows 8 till Windows Phone 8.1 respektive Windows 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1. På så sätt kan du fortsätta att distribuera appar till dessa enheter utan avbrott.

Från och med november 2016 upphör stödet för Windows Phone 8-företagsportalappen.
<!--TFS 1255391-->

### <a name="whats-coming"></a>Kommande nyheter

__Nya Microsoft Intune-företagsportalen för Windows 10-enheter__ Microsoft lanserar en ny Microsoft Intune-företagsportal för Windows 10-enheter. Den här appen, som använder det nya Windows 10 Universal-formatet, ger en uppdaterad användarupplevelse i appen och identiska miljöer på alla Windows 10-enheter, både på datorer och mobila enheter, med samma funktioner som användarna redan använder.

Med den nya appen kan användarna dessutom dra nytta av ytterligare plattformsfunktioner som enkel inloggning (SSO) och certifikatbaserad autentisering på Windows 10-enheter. Appen kommer att vara tillgänglig som en uppgradering till de befintliga installationerna av Windows 8.1-företagsportalen och Windows Phone 8.1-företagsportalen från Windows Store. Mer information finns på [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

## <a name="september-2016"></a>September 2016
### <a name="new-features-announcements-and-information"></a>Nya funktioner, meddelanden och information
* [Villkorlig åtkomst till Windows](#windows-conditional-access)
* [Stöd för iOS 10](#ios-10-support)
* [Programhanteringsverktyget stöder MAM utan enhetsregistrering för Android och iOS](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Intune-grupper påbörjar övergången till Azure Active Directory i september](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Lookout-integrering för att skydda Android-enheter](#lookout-integration-to-protect-android-devices)
* [Uppdateringar av företagsportalen för Android, iOS och Windows](#company-portal-updates)
* [Intune-ordlista](#intune-glossary)
* [Kommande nyheter](#whats-coming)

### <a name="windows-conditional-access"></a>Villkorlig åtkomst till Windows
Nu kan du skapa principer för villkorlig åtkomst via Intune-administratörskonsolen om du vill blockera Windows-datorer från att få åtkomst till Exchange Online och SharePoint Online. Du kan även skapa principer för villkorlig åtkomst för att blockera åtkomst till stationära och universella Office-program.

### <a name="ios-10-support"></a>Stöd för iOS 10
Befintliga Intune MDM- och MAM-scenarier är kompatibla med iOS 10. Om du vill få tips kan du läsa [Intune-supportteamets blogg](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>Programhanteringsverktyget stöder MAM utan enhetsregistrering för Android och iOS
Intunes programhanteringsverktyg är ett kommandoradsverktyg som används för att aktivera Intune MAM på verksamhetsspecifika appar för iOS och Android. Det är det enklaste sättet att införliva SDK:n för Intune MAM i appen, så att appen kan verkställa MAM-principer som distribueras genom Intune. Med MAM-principer kan du:

1. Kryptera appens data.
2. Kräva att informationsanställda anger en PIN-kod när appen startas.
3. Tillåta att appen överför data endast till andra hanterade appar.
4. Förhindra att appen säkerhetskopierar data till Android, iTunes och iCloud.
5. Endast tillåta åtgärderna att klippa ut, kopiera och klistra in för andra hanterade appar.

Förhandsversion av den uppdaterade versionen av Intunes programhanteringsverktyg stöder nu MAM utan enhetsregistrering på interna verksamhetsspecifika appar för iOS och Android. Det innebär att slutanvändarna inte behöver registrera sina enheter med Intune för att kunna använda MAM-aktiverade verksamhetsspecifika appar.

Alla kan testa den allmänna förhandsversionen av programvaran och läsa användbar dokumentation som finns i GitHub för msintuneappsdk:

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Innan du installerar och använder förhandsversionen av Microsoft Intune-programhanteringsverktyget för Android och iOS måste du:

* Granska Microsofts licensvillkor för förhandsversionen av Microsoft Intune-programhanteringsverktyget för Android och iOS
* Skriv ut och behåll en kopia av licensvillkoren för framtida referens. Genom att ladda ned och använda förhandsversionen av Microsoft Intune-programhanteringsverktyget för Android godkänner du licensvillkoren. Om du inte accepterar villkoren har du inte rätt att använda programvaran.
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>Intune-grupper påbörjar övergången till Azure Active Directory i september
Vissa nya Intune-konton kommer att använda Azure Active Directory-säkerhetsgrupper i stället för Intune-användargrupper. Du kommer att veta att du arbetar med säkerhetsgrupper, eftersom sidan för Intune-portalgrupper har en länk som dirigerar dig till Azure-hanteringsportalen.

### <a name="lookout-integration-to-protect-android-devices"></a>Lookout-integrering för att skydda Android-enheter
Microsoft integrerar med Lookouts lösning för mobilhotsskydd för att skydda mobila Android-enheter genom att identifiera skadlig kod, riskfyllda appar med mera, på enheter. Lookouts lösning hjälper dig att bestämma hotnivån, vilken kan konfigureras. Du kan skapa en regel för policy för efterlevnad i Intune för att fastställa enhetens efterlevnad baserat på riskbedömningen av Lookout. Genom att använda åtkomstprinciper kan du tillåta eller blockera åtkomst till företagsresurser utifrån enhetens efterlevnadsstatus.

Slutanvändare med icke-kompatibla enheter kommer att uppmanas att registrera och måste installera Lookout for Work-appen på Android-enheter, aktivera appen och åtgärda hot som rapporteras i Lookout for Work-appen för att få åtkomst. Mer information finns i [Begränsa åtkomsten baserat på enhet, nätverk och programrisk](https://docs.microsoft.com/en-us/intune/deploy-use/device-threat-protection).


### <a name="company-portal-updates"></a>Uppdateringar av företagsportalen

__Android__

<p style="margin-left: 40px">**Tillägg av "Meddelanden" på företagsportalen för Android**<br/>
<p style="margin-left: 40px">En ny ikon för meddelanden har lagts till på företagsportalen för Android på startsidan. När användaren trycker på ikonen visas sidan Meddelanden. På sidan visas alla objekt som kräver åtgärder i företagsportalappen, till exempel inkompatibla enheter, registreringsuppdatering och aktivering av registreringar. Om du använder företagsportalappen för iOS kan du redan se dessa meddelanden. Den nya sidan Meddelanden innebär att användarna inte kommer att se sidan Konfiguration av företagsåtkomst varje gång de startar eller återupptar företagsportalen, förutsatt att enheten redan är registrerad. Om du skapar din egen vägledning för slutanvändare kanske du vill uppdatera din dokumentation för den här ändringen. Sök efter uppdaterade skärmbilder [här](https://aka.ms/androidcpupdate).  

__iOS__
<p style="margin-left: 40px">**Ändringar i stödet för iOS-företagsportalappen**<br/>
<p style="margin-left: 40px">Alla användare av Microsoft Intune-företagsportalappen för iOS måste nu använda den senaste versionen. Nya användare kan endast ladda ned den senaste versionen och aktuella användare måste uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalsappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.
<!---TFS 1283165--->

<p style="margin-left: 40px">**Förbättringar i hur iOS-slutanvändare får sina appar**<br/>
<p style="margin-left: 40px">Följande ändringar har gjorts av appanelerna i företagsportalsappen för iOS så att användarna ska kunna få flera vyer på en och samma plats, nämligen företagsportalens webbplats för alla deras appar. Apples begränsningar förhindrar att verksamhetsspecifika appar och hanterade App Store-appar listas i företagsportalsappen, och kräver att användarna besöker olika vyer om de vill hitta alla sina appar.

<p style="margin-left: 40px">Panelen **Företagsappar** visade tidigare en lista över alla program under fliken ALLA på företagsportalens webbplats, och den kommer att fortsätta fungera på samma sätt. Namnet på panelen har ändrats till **Alla appar**.

<p style="margin-left: 40px">Panelen **Andra appar** visade tidigare en vy i företagsportalsappen som visar alla appar som Apple tillåter att företagsportalsappen visar. Namnet på panelen har ändrats till **Aktuella appar**, och om du trycker på panelen öppnas fliken AKTUELLT på företagsportalens webbplats.

<p style="margin-left: 40px">Panelen **Kategorier** visade tidigare en vy i företagsportalsappen som listar appkategorier. Panelens namn har inte ändrats, men den pekar nu på fliken KATEGORIER på företagsportalens webbplats. Du kan söka efter uppdaterade skärmbilder [här](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
  <!---TFS 1317133--->

<p style="margin-left: 40px">**Uppmanar till installation av appen iOS Managed Browser om IT Pro anger detta krav för en app**<br/>
<p style="margin-left: 40px">Enhetens företagsportalsapp uppmanar dig till att installera den hanterade webbläsaren innan ett webbklipp kan installeras, om du har konfigurerat detta webbklipp så att det bara kan öppnas i den hanterade webbläsaren och om du ännu inte har installerat den hanterade webbläsaren.
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**En feedback-knapp har lagts till i Windows Phone 8.1-företagsportalappen**<br/>
<p style="margin-left: 40px">I företagsportalappen för Windows Phone 8.1 kan slutanvändarna skicka feedback om appen med hjälp av en ny "skicka feedback"-knapp. För att hitta knappen trycker användare på "trepunkts"-menyn längst ned till höger på skärmen Företagsportalapp och sedan på **skicka feedback**. Den insamlade, avidentifierade feedbacken hjälper Microsoft att förbättra företagsportalappen för användare.
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Intune-ordlista</br>
Vi har lagt till ett nytt [ordlisteavsnitt](https://docs.microsoft.com/intune/understand-explore/intune-glossary) i biblioteket som hjälper dig att förstå några av de termer som används i Intune-produkten.

## <a name="august-2016"></a>Augusti 2016
### <a name="app-management"></a>Apphantering

__Dolda appar och appar som visas för iOS 9.3__ För enheter som kör iOS 9.3 eller senare kan du använda listan över dolda appar och appar som visas i den allmänna konfigurationsprincipen för iOS om du vill:
- Ange en lista över appar som ska vara dolda från användare. Användare kan inte visa eller starta dessa appar.
- Ange en lista över appar som användare kan visa och starta. Inga andra appar kan visas eller startas.

Appar som du kan ange omfattar både appar som du har distribuerat och inbyggda iOS-appar som Meddelanden och Anteckningar. Mer information finns i [Principinställningar för iOS i Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
__Princip för tillåtna och blockerade appar för Samsung KNOX-enheter__ Nu kan du konfigurera en anpassad princip för Samsung KNOX-enheter som du kan använda för att skapa något av följande:
- En lista över appar som blockeras från att köras på enheten. Även om den har installerats kan en app som definierats i listan över blockerade appar inte aktiveras på enheten.
- En lista över appar som enhetens användare tillåts att installera från Google Play Store. Inga andra appar kan installeras från butiken.

De här inställningarna kan endast användas av enheter som kör Samsung KNOX.
Mer information finns i [Använda anpassade principer för att tillåta och blockera appar för Samsung KNOX-enheter](https://docs.microsoft.com/en-us/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps).
<!---TFS 1311629 checked --->

__Nya appar är kompatibla med principer för hantering av mobilappar (MAM)__ Nu är Yammer-appen för [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) och [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) kompatibel med [principer för hantering av mobilappar (MAM) i Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), oavsett om enheten har registrerats eller inte.

En fullständig lista över MAM-kompatibla appar finns på webbplatsen för [Microsoft Intune-programpartner](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->

__Intune Viewer-appar__ I och med lanseringen av den nya RMS-delningsappen tas följande Intune Viewer-appar bort, med början från augusti 2016:
- Intune AV Viewer
- Intune PDF Viewer
- Intune Image Viewer för Android från Google Play

I stället för att använda Intune Viewer-appar bör du använda den nya [Rights Management-appen (RMS-delning) för Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. När Intune Viewer-appen inte längre stöds tas den bort från Google Store och är inte längre tillgänglig för framtida bruk.

### <a name="device-management"></a>Enhetshantering
__Android 7.0-stöd__ Intune har ”day 0”-stöd för det kommande Android 7.0-operativsystemet för mobila enheter.
<!---TFS 1262053--->
### <a name="google-removal-of-remote-passcode-reset-capability-on-android-70-devices"></a>Googles borttagning av funktionen för fjärråterställning av lösenord på Android 7.0-enheter
Google tar bort möjligheten för IT-administratörer och slutanvändare att fjärråterställa lösenordet på Android 7.0-enheter. Tidigare kunde IT-administratörer fjärråterställa en användares lösenord, och slutanvändarna kunde återställa sina lösenord från företagsportalens webbplats.



### <a name="company-portal-updates"></a>Uppdateringar av företagsportalen
__Företagsportalens webbplats__
- **Feedbacklänk från företagsportalen till Microsoft** <br/>
På företagsportalens webbplats kan slutanvändare trycka på en ny "Feedback"-länk, längst ned på sidan, för att skicka feedback till Microsoft om sina erfarenheter av webbplatsen. Den insamlade, avidentifierade feedbacken hjälper Microsoft att förbättra företagsportalens webbplats för användare.
<!--- TFS 1313657 checked--->

__iOS__
- **Den lägsta versionen för Managed Browser (iOS) har ändrats till 8.0**<br/>
Microsoft Intune Managed Browser-appen för iOS har uppdaterats för att stödja enheter som kör iOS 8.0 eller senare. Enheter som kör iOS 7.1 kan fortfarande använda Managed Browser-appen, men uppmana ändå användarna att uppdatera till iOS 8.0 eller senare så att de får åtkomst till och kan dra full nytta av de nya funktionerna i Managed Browser.  
<!---TFS 1313253 checked--->

### <a name="whats-coming"></a>Kommande nyheter
__Intune-grupper övergår till Azure Active Directory-grupper med börjar i september 2016__ Intune skapar en ny grupphanteringsmiljö som använder ADD-säkerhetsgrupper (Azure Active Directory) som användar- och enhetsgrupper i Intune. Dessa grupper kommer att användas för all grupphantering, principdistribution och profildistribution **när vi introducerar den nya Azure-baserade Intune-administratörsportalen**.

Med den nya upplevelsen behöver du inte duplicera grupper i olika tjänster och **du får tillgång till nya AADP-gruppfunktioner (Azure Active Directory Premium)**. Dessutom får du möjlighet till utökning med PowerShell och Graph. Du får även en mer enhetlig grupphantering för mobilitetshanteringen i företaget.

Det kommer att göras en del ändringar i den **aktuella administratörskonsolen** i samband med övergången till säkerhetsgrupper. **Dessa ändringar, och användning av AAD-säkerhetsgrupper, kommer att läggas till i Intune-dokumentationen**.

Nya Intune-användare kommer att se **några av ändringarna före befintliga klienter**.

Förutom ändringarna i grupphantering kommer **följande funktion att bli inaktuell**:
- Exkludera medlemmar eller grupper när du skapar en ny grupp
- Grupperna **Användare utan grupp** och **Enheter utan grupp**
- **Hantera grupper** i rollen tjänstadministratör
- Anpassade gruppbaserade aviseringar för aviseringsregler
- Pivotering med grupper i rapporter
<!--- TFS 1295329--->

__Tillägg för ”meddelanden” på företagsportalen för Android__ Vi ger ut en uppdatering av företagsportalen för Android i september som introducerar en ny **meddelandeikon** på startsidan. När användaren trycker på ikonen visas sidan **Meddelanden**. På sidan visas alla objekt som kräver åtgärder i företagsportalappen, till exempel inkompatibla enheter, registreringsuppdatering och aktivering av registreringar. Om du också använder företagsportalappen för iOS kan du redan se dessa meddelanden. När sidan **Meddelanden** läggs till kommer sidan **Konfiguration av företagsåtkomst** inte att visas varje gång du startar eller återupptar företagsportalen för Android, förutsatt att enheten redan är registrerad. Vi vet att många av er har skapat instruktioner till användarna och uppskattar att få veta på förhand när era instruktioner/skärmbilder behöver uppdateras. Uppdatera din dokumentation med de kommande ändringarna. Om du behöver nya skärmbilder kan du gå till https://aka.ms/androidcpupdate.  

### <a name="service-deprecation"></a>Tjänstens utfasning

- **Ändringar i stödet för iOS-företagsportalappen**<br/>
I september krävs det av alla användare att de använder den senaste versionen av Microsoft Intune-företagsportalappen för iOS. Nya användare kommer bara att kunna hämta den senaste versionen och aktuella användare kommer att behöva uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.  

- **Den lägsta versionen för Managed Browser (iOS) har ändrats till 8.0**<br/>
I augusti släpper Intune en uppdaterad Microsoft Intune Managed Browser-app för iOS som bara stöder enheter som kör iOS 8.0 eller senare. Enheter som kör iOS 7.1 kan fortfarande använda Managed Browser-appen, men uppmana ändå användarna att uppdatera till iOS 8.0 eller senare så att de får åtkomst till och kan dra full nytta av de nya funktionerna i Managed Browser.  
<!---TFS 1313253--->

- **Företagsportalappar för Windows 8 och Windows Phone 8 blir inaktuella från september 2016** <br/>
Med början i september 2016 upphör Microsoft Intunes stöd för Microsoft Intune-företagsportalappar för Windows Phone 8- och Windows 8-plattformarna. Uppdatera enheter till Windows 8.1 och Windows Phone 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1 om du vill fortsätta att distribuera appar till dessa enheter.
<!---TFS 1255391--->
