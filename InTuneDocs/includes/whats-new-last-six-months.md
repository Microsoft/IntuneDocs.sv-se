## <a name="november-2016"></a>November 2016

### <a name="new-capabilities"></a>Nya funktioner

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

__Nya Microsoft Intune-företagsportalen för Windows 10-enheter__ Microsoft har lanserat en ny [Microsoft Intune-företagsportalsapp för Windows 10-enheter](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Den här appen, som använder det nya Windows 10 Universal-formatet, ger en uppdaterad användarupplevelse i appen och identiska miljöer på alla Windows 10-enheter, både på datorer och mobila enheter, med samma funktioner som användarna redan använder.

Med den nya appen kan användarna dessutom dra nytta av ytterligare plattformsfunktioner som enkel inloggning (SSO) och certifikatbaserad autentisering på Windows 10-enheter. Appen kommer att vara tillgänglig som en uppgradering till de befintliga installationerna av Windows 8.1-företagsportalen och Windows Phone 8.1-företagsportalen från Windows Store. Mer information finns på [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).

<!--### Support for Windows Store for Business Apps Being Deployed as Available
You can now deploy apps you synchronized from the Windows Store for Business (WSfB) with a deployment action of __Available__ or __Required__. After syncing WSfB apps into Intune, administrators will be able to target those apps as available installs to groups of users. End users will see the deployed WSfB apps as available for install in the Universal Company Portal, where they can choose whether they would like to acquire the apps.

### Conditional Access for MAM with SharePoint Online

You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint online.  You can get started in Intune mobile app management via the Azure portal. Look for the  Conditional Access section in the “Settings” blade which now includes the option for SharePoint online.-->

> [!IMPORTANT]

> __En uppdatering av Intune och Android for Work__

> Även om du kan distribuera Android for Work-appar med åtgärden __Krävs__ kan du bara distribuera appar som __tillgängliga__ om Intune-grupper har migrerats till den nya Azure AD-gruppmiljön.

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

<!--Existing Intune customers can use this feature in production once their tenant has been migrated. Existing customers are welcome to create a trial Intune account to plan for and test this feature until their tenant has been migrated. Any questions on grouping and targeting timelines, please contact our [migration team](mailto:intunegrps@microsoft.com).-->

[Läs Microsofts tillkännagivande om Intune-stöd för Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Följande avsnitt för Intune är nya eller uppdaterade med information om Android for Work:

För IT-proffs:
- [Konfigurera Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
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

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

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

Slutanvändare med icke-kompatibla enheter kommer att uppmanas att registrera och måste installera Lookout for Work-appen på Android-enheter, aktivera appen och åtgärda hot som rapporteras i Lookout for Work-appen för att få åtkomst. Mer information finns i [Begränsa åtkomsten baserat på enhet, nätverk och programrisk](https://docs.microsoft.com/en-us/intune/deploy-use/restrict-access-based-on-device-network-app-risk).


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
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

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


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

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
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Ändringar i stödet för iOS-företagsportalappen**<br/>
I september krävs det av alla användare att de använder den senaste versionen av Microsoft Intune-företagsportalappen för iOS. Nya användare kommer bara att kunna hämta den senaste versionen och aktuella användare kommer att behöva uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.  

- **Den lägsta versionen för Managed Browser (iOS) har ändrats till 8.0**<br/>
I augusti släpper Intune en uppdaterad Microsoft Intune Managed Browser-app för iOS som bara stöder enheter som kör iOS 8.0 eller senare. Enheter som kör iOS 7.1 kan fortfarande använda Managed Browser-appen, men uppmana ändå användarna att uppdatera till iOS 8.0 eller senare så att de får åtkomst till och kan dra full nytta av de nya funktionerna i Managed Browser.  
<!---TFS 1313253--->

- **Företagsportalappar för Windows 8 och Windows Phone 8 blir inaktuella från september 2016** <br/>
Med början i september 2016 upphör Microsoft Intunes stöd för Microsoft Intune-företagsportalappar för Windows Phone 8- och Windows 8-plattformarna. Uppdatera enheter till Windows 8.1 och Windows Phone 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1 om du vill fortsätta att distribuera appar till dessa enheter.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## <a name="july-2016"></a>Juli 2016
### <a name="app-management"></a>Apphantering

__Förbättrad uppdateringsmiljö för appetableringsprofil__ Affärsspecifika Apple iOS-mobilappar skapas med en medföljande etableringsprofil och kod som signerats med ett certifikat. När appen körs på en iOS-enhet bekräftar iOS appens integritet och tillämpar de principer som definierats av etableringsprofilen.

Signeringscertifikatet du använder för att signera appar gäller normalt i 3 år. Däremot upphör etableringsprofilen att gälla efter ett år. Med den här uppdateringen tillhandahåller Intune verktyg för att distribuera en ny etableringsprofilprincip till enheter som har appar som snart slutar att gälla medan certifikatet fortfarande är giltigt. Mer information finns i [Använda etableringsprofilprinciper för iOS för att hålla verksamhetsspecifika appar uppdaterade](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->

__Xamarin SDK för Intune-appar är tillgängliga__ Med Intune App SDK Xamarin-komponenten kan du aktivera funktionerna för hantering av mobilappar i Intune i iOS- och Android-mobilappar som utvecklats med Xamarin. Komponenten hittar du i [Xamarin store](https://components.xamarin.com/view/Microsoft.Intune.MAM) eller på [Github-sidan för Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### <a name="device-management"></a>Enhetshantering
__Ökade enhetsregistreringsgränser__ Den högsta gränsen för konfigurerbar enhetsregistrering i Intune har ökats från 5 till 15 enheter per användare.
<!---TFS 1289896 --->

__TeamViewer-integrering för Windows-datorer som kör Intune-klientprogramvaran__
[TeamViewer](https://www.teamviewer.com)-integreringen för Windows-datorer som kör Intune-klienten gör att du kan upprätta fjärrhjälpsessioner med Windows-datorer för att hjälpa supportpersonal som betjänar slutanvändare. Detta gäller Windows 7, 8, 8.1 och Windows 10. Mer information finns i [Vanliga hanteringsuppgifter för Windows-datorer med Microsoft Intune-datorklienten](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>Uppdateringar av företagsportalen

__Företagsportalens webbplats__
- **Förbättrad användarupplevelse vid registrering av Windows-enheter**<br/>
När du använder villkorlig åtkomst har registreringsanvisningarna för Windows 8.1, Windows 10 Desktop och Windows 10 Mobile förenklats på företagsportalens webbplats. Nu visas separata steg för ”enhetsregistrering” och ”anslutning till arbetsplatsen”, vilket gör det lättare att se status för enheterna och slutföra processen om användarna inte lyckas ansluta till arbetsplatsen. De separata stegen förväntas också underlätta felsökningen för IT-administratörer. När slutanvändarna försökte registrera en enhet och alla steg lyckades utom anslutningen till arbetsplatsen visades inte den registrerade enheten i listan med enheter som användarna skulle identifiera, vilket orsakade förvirring för användarna.

__Android__
- **Android-företagsportalappen**<br/>
Om Android-användarna ser ett felmeddelande om att enheten saknar ett nödvändigt certifikat kan de trycka på ”Så här löser du problemet” och få [anvisningar](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) om hur de installerar certifikatet som saknas. Om användarna slutför stegen men får ett felmeddelande om att ”certifikat saknas” ombeds de kontakta IT-administratören och ange den här [länken](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues) som innehåller anvisningar som IT-administratörer kan använda för att åtgärda certifikatproblem.

- **Begränsa appinstallationer med separat inläsning till registrerade enheter**<br/>
Det går inte längre att installera program på Android-enheter via företagsportalens webbplats om de inte har registrerats i Intune via Intune-företagsportalappen för Android.
<!---TFS 1299082--->

__iOS__
- **Ändringar av konton för enhetsregistreringshanterare i iOS-företagsportalappen**<br/>
För att förbättra prestanda och skalning visar Intune inte längre alla enheter i Enhetsregistreringshanteraren (DEM) i fönstret **Mina enheter** i företagsportalappen för iOS. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen.

DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen. Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter.

Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt. Mer information finns i [Registrera företagsägda enheter med Enhetsregistreringshanteraren i Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Ändrade namn på Windows-funktioner
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) heter numera **Windows Hello för företag**.
- [Företagsdataskydd](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) kallas nu **Windows informationsskydd**.

## <a name="june-2016"></a>Juni 2016
### <a name="intune-service-health"></a>Hälsotillstånd för Intune-tjänsten
Information om Intune-tjänstens hälsotillstånd har nu flyttats till en central plats med andra Microsoft-tjänster. Nu finns den här informationen i under Tjänstens hälsa i Office 365-hanteringsportalen. Mer information finns i [det här blogginlägget](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Apphantering
- **Förbättrad konfigurationsmiljö för Windows 10-företagsdataprinciper.** Vi har gjort förbättringar i konfigurationsupplevelsen för Windows 10- företagsdatapolicyn när det gäller att skapa regler för program, specificera nätverksgränsdefinitioner och andra inställningar för företagsdataskydd. Läs mer i [Skapa en princip för företagsdataskydd (EDP) med Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### <a name="device-management"></a>Enhetshantering
- **Windows Defender-principinställning för att skydda mot potentiellt oönskade appar.** En ny Windows Defender-inställning som kallas **identifiering av potentiellt oönskade program** har lagts till i den allmänna konfigurationsprincipen för Windows 10 Desktop och Mobile. Du kan använda den här inställningen för att skydda registrerade stationära Windows-datorer från att köra program som Windows Defender har klassificerat som potentiellt oönskade. Du kan skydda dig mot att dessa program körs eller använda granskningsläget för att rapportera att ett potentiellt oönskat program har installerats. Mer information finns i [Principinställningar för Windows 10 i Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### <a name="conditional-access"></a>Villkorlig åtkomst
- **Cisco ISE-kontrollprinciper för nätverksåtkomst för Intune.**  Kunder som använder Cisco Identity Service Engine (ISE) 2.1 och även använder Microsoft Intune kan ange en princip för nätverksåtkomst i ISE.

    Med den här principen måste enheter som ansluter till nätverket med hjälp av Wi-Fi eller VPN uppfylla följande villkor innan de tillåts åtkomst:

    * Måste hanteras av Intune
    * Måste vara kompatibla med alla distribuerade efterlevnadsprinciper för Intune

 Användare med icke kompatibla enheter uppmanas att registrera sig och åtgärda eventuella efterlevnadsproblem för att få åtkomst.
- **Villkorlig åtkomst för webbläsare.** Du kan skapa en princip för villkorlig åtkomst för [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) och [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) så att programmen bara kan användas från webbläsare som stöds i hanterade och godkända iOS- och Android-enheter. Användare som försöker logga in till Outlook Web Access (OWA) och SharePoint-webbplatser med iOS- och Android-enheter uppmanas att registrera sina enheter med Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS 1175844--->

- **Dynamics CRM Online stöder villkorlig åtkomst.** Du kan skapa en princip för villkorlig åtkomst för [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) så att det bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Slutanvändare som försöker logga in i mobilappen för Dynamics CRM på iOS och Android uppmanas att registrera sig i Intune samt åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Uppdateringar av Intune-företagsportalen

__Android-företagsportalappen__

- När IT-administratörer använder den nya principen ”Kräv att enheter förhindrar installation av appar från okända källor (Android 4.0+)” visas meddelandet ”Installation från okända källor måste inaktiveras” i enheter med Android 4.0 eller senare. Användare måste välja **Inställningar** > **Säkerhet**, och inaktivera **Okända källor**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) om meddelandet och varför användaren måste inaktivera inställningen.

- När IT-administratörer använder den nya principen ”Kräv att ”Genomsök enhet efter säkerhetshot" (Android 4.0+) är aktiverat på enheter” visas meddelandet ”Genomsök enhet efter säkerhetshot” i enheter med Android 4.0 eller senare. Användarna måste välja **Inställningar** > **Google** > **Säkerhet** och aktivera **Genomsök enhet efter säkerhetshot**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) om meddelandet och varför användaren måste aktivera inställningen.

- När IT-administratörer använder den nya principen ”Kräv att USB-felsökning är inaktiverat (Android 4.2+)” visas meddelandet ”USB-felsökning måste inaktiveras” i enheter med Android 4.2 eller senare. Användarna måste välja **Inställningar** > **Utvecklaralternativ** och inaktivera **USB-felsökning**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) om meddelandet och varför användaren måste inaktivera inställningen.

- När IT-administratörer använda nya principen ”Lägsta Android-säkerhetskorrigeringsnivå (Android 6.0+)” visas meddelandet ”Den här enheten motsvarar inte miniminivån för Android-säkerhetskorrigering” i enheter med Android 6.0 eller senare. Användarna måste installera den nödvändiga säkerhetskorrigeringen. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) om hur den nödvändiga säkerhetskorrigeringen installeras och vilken säkerhetskorrigering som redan finns installerad.

__iOS-företagsportalappen__

- Appinstallationen har förbättrats för slutanvändare som installerar affärsspecifika appar. Om appinstallationen tar lång tid kan användarna synkronisera sina enheter manuellt för att tvinga synkroniseringen att fortsätta. Instruktioner för slutanvändaren finns i [Synkronisera din iOS-enhet manuellt](/Intune/EndUser/sync-your-device-manually-ios).

- Microsoft Intunes-företagsportalappen för iOS har uppdaterats med stöd till iOS version 8.0 och senare. Uppdateringen innebär att slutanvändare bara kan installera företagsportalappen och registrera nya enheter i Intune om enheten kör iOS version 8.0 eller senare. Användare som redan har registrerat enheter som körs på en iOS-version som inte stöds, kan fortsätta använda den företagsportalapp som finns på enheten.


<!--HONumber=Jan17_HO1-->


