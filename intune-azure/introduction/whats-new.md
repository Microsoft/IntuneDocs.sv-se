---
title: "Nyheter i Microsoft Intune-förhandsversionen"
titleSuffix: Intune Azure preview
description: "Ta reda på vad som är nytt i förhandsversionen av Intune Azure"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: f209429bbafe50530e90bbaf133f780f448a8c57
ms.contentlocale: sv-se
ms.lasthandoff: 05/10/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Nyheter i Microsoft Intune-förhandsversionen

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

I takt med att den offentliga förhandsversionen utvecklas och fler funktioner läggs till, meddelar vi dig om dem här.

> [!Note]
> Vi lansera ändringarna på den här sidan för Azure Portal Preview. Det kan dock vara så att ändringarna inte är tillgängliga direkt pga hur Intune-tjänsten uppdateras.  Flera av tjänstens komponenter måste uppdateras sekventiellt innan de nya portalfunktionerna blir tillgängliga. Sök efter dessa ändringar i takt med att de lanseras senare under månaden.

## <a name="april-2017"></a>April 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Stöd för hantering av Apples Klassrum-app

Du kan nu hantera iOS Klassrum-app på iPad-enheter. Konfigurera Klassrum-appen på lärarens iPad med rätt klass- och elevinformation, konfigurera sedan elevernas iPad-enheter som är registrerade till en klass, så att du kan kontrollera dem med hjälp av appen.
Mer information finns i [Konfigurera utbildningsinställningar för iOS](../configure-devices/how-to-configure-ios-edu-settings.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Stöd för hanterade konfigurationsalternativ för Android-appar <!-- 621621 -->

Android-appar i Play Store som har stöd för hanterade konfigurationsalternativ kan nu konfigureras av Intune.  Med hjälp av den här funktionen kan IT-personal visa listan över konfigurationsvärden som stöds av en app, vilket ger ett tydligt gränssnitt som gör det möjligt att konfigurera dessa värden.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Ny Android-princip för komplexa PIN-koder <!-- 722069 -->

Du kan ange den obligatoriska [lösenords](../configure-devices/device-restrictions-for-android.md#password)typen Numeriskt avancerat i en Android-enhetsprofil för enheter som kör Android 5.0 och senare.  Använd den här inställningen för att hindra att enhetsanvändare skapar en PIN-kod som innehåller upprepande eller efterföljande siffror, t.ex. 1111 eller 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Ytterligare stöd för Android for Work-enheter

- **Hantera inställningar för lösenord och arbetsprofil** <!-- 612808 -->

  Med den här nya enhetsbegränsningsprincipen för Android for Work kan du nu hantera inställningar för lösenord och arbetsprofil på de Android for Work-enheter som du hanterar.

- **Tillåt datadelning mellan arbetsprofiler och personliga profiler** <!-- 1045102 -->

Den här enhetsbegränsningsprofilen för Android for Work har nu nya alternativ som hjälper dig att konfigurera datadelning mellan arbetsprofiler och personliga profiler.

- **Begränsa kopiera och klistra in mellan arbetsprofiler och personliga profiler** <!-- 1046094 -->

  En ny anpassad enhetsprofil för Android for Work-enheter gör det nu möjligt att begränsa om åtgärderna för att kopiera och klistra in mellan arbetsappar och personliga appar ska vara tillåtna.

Mer information finns i [Enhetsbegränsningar för Android for Work](../configure-devices/device-restrictions-for-afw.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Tilldela branschspecifika appar till iOS- och Android-enheter <!-- 1057568 -->

Du kan nu tilldela branschspecifika appar för [iOS](../manage-apps/ios-lob-app.md) (.ipa-filer) och [Android](../manage-apps/android-lob-app.md) (.apk-filer) till användare eller enheter.

###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nya enhetsprinciper för iOS <!-- 723774, 723815, 723826, 723830 -->

- **Appar på startskärmen** – Styr vilka appar användarna ser på [startskärmen på sina iOS-enheter](../configure-devices/home-screen-settings-for-ios.md). Den här principen ändrar layouten på startskärmen, men distribuerar inte några appar som du har angett som inte är installerade.

- **Anslutningar till AirPrint-enheter** – Styr vilka [AirPrint-enheter](../configure-devices/air-print-settings-for-ios-and-macos.md) (nätverksskrivare) som användarna av iOS-enheter kan ansluta till.

- **Anslutningar till AirPlay-enheter** – Styr vilka [AirPlay-enheter](../configure-devices/airplay-settings-for-ios-devices.md) (t.ex. Apple TV) som användarna av iOS-enheter kan ansluta till.

- **Anpassat meddelande på låsskärmen** – Konfigurerar ett anpassat meddelande som ersätter det standardmeddelande som användarna ser på låsskärmen på sina iOS-enheter. Mer information finns i [Tillgängliga enhetsåtgärder](../manage-devices/what-is.md#available-device-actions)


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Begränsa push-meddelanden för iOS-appar <!-- 723767 -->

Du kan nu konfigurera följande [aviseringsinställningar](../configure-devices/app-notification-settings-for-ios.md) för iOS-enheter i en begränsningsprofil för Intune-enheter:

- Aktivera eller inaktivera aviseringar helt för en angiven app.
- Aktivera eller inaktivera aviseringar i aviseringscentret för en angiven app.
- Ange aviseringstypen, antingen **Ingen**, **Banderoll** eller **Modal avisering**.
- Ange om aktivitetsikoner tillåts för den här appen.
- Ange om aviseringsljud tillåts.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Konfigurera iOS-appar för att köras i autonomt enkelappsläge <!-- 737837 -->

Du kan nu använda en Intune-enhetsprofil för att konfigurera iOS-enheter till att köra angivna appar i [autonomt enkelt appläge](../configure-devices/device-restrictions-for-ios.md#autonomous-single-app-mode-supervised-only). När det här läget är konfigurerat och appen körs kommer enheten att låsas så att den endast kan köra den appen. Ett exempel på detta är när du konfigurerar en app som gör att användarna kan genomföra ett test på enheten. När appens åtgärder har slutförts, eller om du tar bort principen, återgår enheten till sitt normala tillstånd.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Konfigurera betrodda domäner för e-post och webbläsare på iOS-enheter <!-- 723765 -->

Du kan nu konfigurera följande [domäninställningar](../configure-devices/device-restrictions-for-ios.md#domains) i en begränsningsprofil för iOS-enheter:

- **Omarkerade e-postdomäner** – E-postmeddelanden som användaren skickar eller tar emot och som inte matchar de domäner du anger här, markeras som icke tillförlitliga.

- **Hanterade webbdomäner** – Dokument som laddats ned från de webbadresser du anger här betraktas som hanterade (endast Safari).  

- **Fyll i lösenord automatiskt för Safari-domäner** – Användare kan spara lösenord endast i Safari från URL:er som matchar de mönster du anger här. Om du vill använda den här inställningen måste enheten vara i övervakat läge och får inte vara konfigurerad för flera användare. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>VPP-appar som är tillgängliga i iOS-företagsportalen <!-- 748782 -->

Du kan nu tilldela volyminköpsappar för iOS som **Tillgängliga** installationer till användarna. Användarna behöver ett Apple Store-konto för att installera appen.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Synkronisera e-böcker från Apple VPP Store <!-- 800878 -->

Du kan nu [synkronisera böcker](../manage-apps/ios-vpp-apps.md) som du har köpt från Apples butik för volyminköpsappar med Intune och tilldela dem till användarna.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Hantering av flera användare för Samsung KNOX Standard-enheter <!-- 971988 -->

Enheter som kör Samsung KNOX Standard har nu stöd för [hantering av flera användare](../enroll-devices/enroll-android-and-knox-standard-devices.md) i Intune. Det innebär att slutanvändarna kan logga in och ut från enheten med sina autentiseringsuppgifter för Azure Active Directory, och enheten hanteras centralt oavsett om den används eller inte.  När användarna loggar in får de tillgång till appar och dessutom verkställs eventuella principer som gäller för dem. Alla appdata rensas när användaren loggar ut.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Ytterligare begränsningsinställningar för Windows-enheter <!-- 818566 -->

Vi har lagt till stöd för fler [begränsningsinställningar för Windows-enheter](../configure-devices/device-restrictions-for-windows-10.md), t.ex. ytterligare Edge-webbläsarstöd, anpassning av enhetens låsskärm, anpassning av startmenyn, bakgrund för Windows Spotlight-sökning och proxyinställningar.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Stöd för flera användare för Windows 10 Creators Update <!-- 822547 -->

Vi har lagt till stöd för [hantering av flera användare](../enroll-devices/enroll-windows-devices.md) för enheter som kör Windows 10 Creators-uppdateringen och som är domänanslutna med Azure Active Directory. Det innebär att när olika standardanvändare loggar in på enheten med sina autentiseringsuppgifter för Azure AD, får de alla appar och principer som har tilldelats till deras användarnamn. Användare kan för närvarande inte använda Företagsportalen för självbetjäningsscenarier som att installera appar.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start för Windows 10-datorer<!-- 1004830 -->

En ny [Fresh Start-enhetsåtgärd](../manage-devices/what-is.md#available-device-actions) för Windows 10-datorer finns nu tillgänglig.  När du kör den här åtgärden tas alla appar som har installerats på datorn bort, och datorn uppdateras automatiskt till den senaste Windows-versionen. Detta kan användas för att ta bort förinstallerade OEM-appar som ofta levereras med en ny dator. Du kan konfigurera om användardata ska behållas när den här enhetsåtgärden utförs.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Ytterligare uppgraderingsvägar i Windows 10 <!-- 903672 -->

Nu kan du skapa en [uppgraderingsprincip för utgåvor för att uppgradera enheter](../configure-devices/how-to-configure-windows-10-edition-upgrade.md) till följande Windows 10-utgåvor:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Massregistrera Windows 10-enheter <!-- 747607 -->

Nu kan du ansluta ett stort antal enheter som kör Windows 10 Creators-uppdateringen till Azure Active Directory och Intune med Windows Configuration Designer (WCD). Aktivera [MDM-massregistrering](../enroll-devices/bulk-enroll-windows.md) för din Azure AD-klient genom att skapa ett konfigurationspaket som ansluter enheter till din Azure AD-klient med hjälp av Windows Configuration Designer. Tillämpa sedan paketet på de företagsägda enheter som du vill massregistrera och hantera. När paketet har tillämpats på dina enheter kommer Azure AD att anslutas, registreras i Intune och vara redo för att Azure AD-användarna ska logga in.  Azure AD-användare är standardanvändare på de här enheterna och tar emot tilldelade principer och nödvändiga appar. Självbetjäning och företagsportalscenarier stöds inte för närvarande.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nya MAM-inställningar för PIN-kod och hanterade lagringsplatser <!-- 581122, 736644 -->

Det finns nu två nya appinställningar som hjälper dig med scenarier för hantering av mobilprogram (MAM):

- **Inaktivera app-PIN när enhets-PIN är hanterad** – Identifierar om det finns en enhets-PIN på den registrerade enheten och förbigår i så fall den app-PIN som utlöses av appskyddsprinciperna. Den här inställningen minskar antalet gånger en PIN-uppmaning visas för användare som öppnar ett MAM-aktiverat program på en registrerad enhet. Den här funktionen är tillgänglig för både Android och iOS.

- **Välj med vilka lagringstjänster företagsdata ska sparas** – Gör det möjligt att ange de lagringsplatser där företagsdata ska sparas. Användare kan spara i valda lagringsplatstjänster, vilket innebär att alla lagringsplatstjänster som inte anges kommer att blockeras.

  Lista över lagringsplatstjänster som stöds:

  - OneDrive
  - Business SharePoint Online
  - Lokal lagring

### <a name="help-desk-troubleshooting-portal----907448---"></a>Supportavdelningens felsökningsportal <!-- 907448 -->

Med den nya [felsökningsportalen](../manage-users/help-desk.md) kan supportansvariga och Intune-administratörer se användarna och deras enheter, samt utföra åtgärder för att lösa tekniska problem i Intune.

## <a name="march-2017"></a>Mars 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Stöd för iOS borttappat läge <!--431695-->

För iOS 9.3-enheter och senare har Intune lagt till stöd för **Borttappat läge**. Nu kan du låsa en enhet för att förhindra all användning och visa ett meddelande och ett telefonnummer på enhetens låsskärm.

Användaren kommer inte att kunna låsa upp enheten förrän en administratör har inaktiverat borttappat läge. När Borttappat läge har aktiverats kan du använda åtgärden **Hitta enhet** för att visa enhetens geografiska plats på en karta i Intune-konsolen.

Enheten måste vara en företagsägd iOS-enhet, registrerad med DEP, som är i övervakat läge.

Mer information finns i [Vad är Microsoft Intune-enhetshantering](../manage-devices/what-is.md)?

### <a name="improvements-to-device-actions-report---677150--"></a>Förbättringar av rapporten Enhetsåtgärder<!--677150-->

Vi har förbättrat rapporten Enhetsåtgärder för att förbättra dess prestanda. Nu kan du filtrera rapporten efter tillstånd. Exempelvis kan du filtrera rapporten för att endast visa enhetsåtgärder som har slutförts.

### <a name="actions-for-non-compliance---730266--"></a>Åtgärder vid inkompatibilitet <!--730266-->

**Åtgärder vid inkompatibilitet** är en ny funktion för efterlevnadsprinciper som gör det möjligt att vidta åtgärder för enheter som inte är kompatibla. Du kan ange en eller flera åtgärder och ange den tidsperiod då dessa åtgärder måste äga rum. Du kan till exempel meddela användare med inkompatibla enheter via e-post direkt efter att enheterna har blivit inkompatibla, eller så kan du blockera inkompatibla enheter från att få åtkomst till företagsresurser efter en respitperiod på tre dagar via villkorsstyrd åtkomst.

### <a name="custom-app-categories---748805--"></a>Anpassade appkategorier <!--748805-->

Du kan nu skapa, redigera och tilldela kategorier för appar som du lägger till i Intune. Kategorier kan för närvarande kan bara anges på engelska.
Läs [How to add an app to Intune](../manage-apps/add-apps.md) (Lägga till en app i Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Tilldela LOB-appar till användare med oregistrerade enheter <!--748823-->

Du kan nu tilldela branschspecifika appar och appar från butiken till användare, oavsett om deras enheter är registrerade i Intune eller inte. Om användarens enhet inte har registrerats i Intune måste användaren gå till företagsportalens webbplats, inte dess app, för att installera den.

### <a name="new-compliance-reports---846671--"></a>Nya efterlevnadsrapporter <!--846671-->

Nu har du efterlevnadsrapporter som ger ditt företags enheters efterlevnadsprofil och låter dig felsöka problem som berör efterlevnad snabbt efter hand som de upptäcks av dina användare. Du kan visa information om

- Övergripande efterlevnadstatus för enheter
- Efterlevnadstatus för en enskild inställning
- Efterlevnadstatus för en enskild princip

Du kan även använda dessa rapporter för att undersöka en individuell enhet på djupet för att se de inställningar och principer som påverkar enheten.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->

För Intune-konto som har skapats senare än januari 2017 har Intune möjliggjort direktåtkomst till Apples-registreringsscenarier med arbetsbelastningen Registrera enheter i Azure Preview-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i den klassiska Intune-portalen. Intune-konton som skapats före januari 2017 behöver migreras vid ett tillfälle innan de här funktionerna finns tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till förhandsversionen.


## <a name="february-2017"></a>Februari 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Möjlighet att begränsa registrering av mobila enheter <!--747600, 795782-->
Intune lägger till nya registreringsbegränsningar som avgör vilka plattformar som mobila enheter ska kunna registrera. Intune skiljer mellan mobilplattformar som iOS, macOS, Android, Windows och Windows Mobile.

* Begränsningen av registrering av mobila enheter begränsar inte registreringen av datorklienter.  
* För iOS och Android finns det ytterligare ett alternativ för att blockera registrering av personligt ägda enheter.

Intune markerar alla nya enheter som personliga såvida inte IT-administratören vidtar åtgärder för att markera dem som företagsägda, vilket beskrivs i [den här artikeln](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Visa alla åtgärder på hanterade enheter <!--677150-->
En ny rapport om __enhetsåtgärder__ visar vem som har utfört fjärråtgärder som fabriksåterställning på enheter, och dessutom visas status för åtgärden. Se [Vad är enhetshantering?](https://docs.microsoft.com../manage-devices/what-is.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Icke-hanterade enheter kan komma åt tilldelade appar <!--664691-->
Som en del av designändringarna på företagsportalens webbplats ska iOS- och Android-användare kunna installera appar som har tilldelats dem som "tillgänglig utan registrering" på sina icke-hanterade enheter. Med sina Intune-autentiseringsuppgifter kan användare logga in på företagsportalens webbplats och se en lista över appar som tilldelats dem. App-paket för apparna som är "tillgängliga utan registrering" görs tillgängliga för hämtning via företagsportalens webbplats. Appar som kräver registrering för installation påverkas inte av den här ändringen, eftersom användarna uppmanas att registrera sina enheter om de vill installera apparna.

### <a name="custom-app-categories---748805--"></a>Anpassade appkategorier <!--748805-->
Du kan nu skapa, redigera och tilldela kategorier för appar som du lägger till i Intune. Kategorier kan för närvarande kan bara anges på engelska.
Läs [How to add an app to Intune](../manage-apps/add-apps.md) (Lägga till en app i Intune).

### <a name="display-device-categories---814654--"></a>Visa enhetskategorier <!--814654-->
Du kan nu visa enhetskategorin som en kolumn i listan över enheter. Du kan också redigera kategorin från avsnittet med egenskaper på bladet Enhetsegenskaper. Läs [How to add an app to Intune](../manage-apps/add-apps.md) (Lägga till en app i Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Konfigurera inställningar för Windows Update för företag <!--776716-->

Windows som en tjänst är det nya sättet för att tillhandahålla uppdateringar för Windows 10. Från och med Windows 10 innehåller alla nya funktions- och kvalitets även innehållet från alla tidigare uppdateringar. Det innebär att så länge som du har installerat den senaste uppdateringen så vet du att dina Windows 10-enheter är helt uppdaterade. Till skillnad från vad som var fallet i tidigare versioner av Windows måste du nu installera hela uppdateringen i stället för en del av en uppdatering.

Med hjälp av Windows Update för företag kan du förenkla hanteringen av uppdateringar så att du inte behöver godkänna varje enskild uppdatering för enhetsgrupperna. Du kan fortfarande hantera risker i din miljö genom att konfigurera en strategi för uppdateringarna installeras, och Windows Update ser till att uppdateringarna installeras vid rätt tidpunkt. Microsoft Intune ger dig möjlighet att konfigurera enheternas inställningar och att skjuta upp installationen av uppdateringar. Intune lagrar inte uppdateringar, utan enbart uppdateringarnas principtilldelning. Enheterna har direkt åtkomst till uppdateringarna via Windows Update. Använd Intune för att konfigurera och hantera **Windows 10-uppdateringsringar**. En uppdateringsring innehåller en grupp med inställningar som anger när och hur uppdateringar av Windows 10 updates installeras. Mer information finns i [Konfigurera inställningar för Windows Update för företag](../configure-devices/how-to-configure-windows-update-for-business.md).

## <a name="january-2017"></a>Januari 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Tilldela branschspecifika appar oavsett om enheterna har registrerats eller inte <!--748823-->
Du kan nu tilldela branschspecifika appar och appar från butiken till användare, oavsett om deras enheter är registrerade i Intune eller inte. Om användarens enhet inte har registrerats i Intune måste användaren gå till webbplatsen för företagsportalen för att installera den, i stället för företagsportalappen. Se [Vad är apphantering](../manage-apps/what-is-app-management.md)?

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Lös problemet med att iOS-enheterna är inaktiva eller att administratörskonsolen inte kan kommunicera med dem
När användarnas enheter förlorar kontakt med Intune kan du ge dem nya felsökningssteg för att hjälpa dem att återfå åtkomst till företagets resurser. Se [Enheterna är inaktiva eller så kan administratörskonsolen inte kommunicera med dem](../enroll-devices/troubleshoot-device-enrollment.md#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>December 2016 (ursprunglig version)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Hantering av telekomkostnad i förhandsversionen av Azure-portalen<!--747605-->
Vi börjar nu att förhandsgranska integrering med tredje parters hantering av telekomkostnad (TEM) i Azure-portalen. Du kan använda Intune för att tvinga gränser för nationell och central dataanvändning. Vi börjar de här integreringarna med [Saaswedo](http://www.saaswedo.com). Om du vill aktivera den här funktionen i utvärderingsversionen av klienten kan du [kontakta Microsoft support](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

- Distribuera och hantera appar från en butik till iOS-, Android- och Windows-enheter
- Distribuera och hantera branschspecifika (LOB) appar till iOS-, Android- och Windows-enheter
- Distribuera och hantera volyminköpta appar till iOS- och Windows-enheter
- Distribuera och hantera webbappar till Android-, iOS- och Windows-enheter
- Konfigurationsprofiler för iOS-hanterade appar
- Konfigurera appskyddsprinciper och distribuera branschspecifika appar till enheter som inte har registrerats med Intune
- VPN-profiler, per-app VPN, Wi-Fi, e-post och certifikatprofiler
- Efterlevnadsprinciper
- Villkorlig åtkomst för Azure AD
- Villkorlig åtkomst för lokal Exchange
- Enhetsregistrering
- Rollbaserad åtkomstkontroll

## <a name="deprecated-features-in-the-azure-portal"></a>Inaktuella funktioner i Azure-portalen

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Stöd för rad för rad-granskning av maskinvaruidentifierare
Azure-portalen stöder inte granskning rad för rad av maskinvaruidentifierare för IMEI-nummer och Apple-serienummer. I den klassiska Intune-konsolen kan du importera information från en fil med kommateckenavgränsade fält (.csv) och skriva över den befintliga informationen för enskilda maskinvaruidentifierare. Azure-portalen har ett enda, effektiviserat alternativ som automatiskt skriver över informationen för alla maskinvaruidentifierare eller ignorerar ny information för befintliga identifierare.

#### <a name="how-this-affects-you"></a>Hur detta påverkar dig
I Azure-portalen kan du inte bestämma rad för rad vilka IMEI-enheter (International Mobile Equipment Identity) som ska uppdateras. Den klassiska Intune-konsolen fortsätter att stödja den här funktionen.

#### <a name="how-to-get-ready-for-this-change"></a>Hur du förbereder för ändringen
Vi meddelar den här informationen i förväg så att du, om den påverkar dig, kan göra dina supportadministratörer medvetna om den här ändringen. Den här ändringen kommer sammanfalla med flytten till Azure-portalen som förväntas äga rum under första halvan av 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Stöd för standardprofiler för företagsenhetsregistrering i Apples DEP
Azure-portalen stöder inte standardprofilen för företagsenhetsregistrering för enhetsserienumren i Apples enhetsregistreringsprogram DEP. Den här funktionen, som finns tillgänglig i den klassiska Intune-konsolen, kommer upphöra för att förhindra oavsiktligt tilldelade profiler. i Azure-portalen kommer serienummer som synkroniserats från ett Apple DEP-konto inledningsvis inte ha någon profil för företagsenhetsregistrering tilldelad.

#### <a name="how-this-affects-you"></a>Hur detta påverkar dig
I Azure-portalen kommer du inte att kunna ställa in en standardprofilprincip för alla Apple-enheter. Den klassiska Intune-konsolen fortsätter att stödja den här funktionen.

#### <a name="how-to-get-ready-for-this-change"></a>Hur du förbereder för ändringen
Vi meddelar den här informationen i förväg så att du, om den påverkar dig, kan göra dina supportadministratörer medvetna om den här ändringen. Den kommer sammanfalla med flytten till Azure-portalen som förväntas äga rum under första halvan av 2017.

