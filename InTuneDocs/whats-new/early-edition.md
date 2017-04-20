---
title: "Tidig utgåva | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f051d8366ba9c6ca2183b5661c64087eb4cce9f0
ms.openlocfilehash: 682545af10a7dc1f66158f95f871b889e9f85c4a
ms.lasthandoff: 04/06/2017


---


# <a name="the-early-edition-for-microsoft-intune---april-2017"></a>Den tidiga utgåvan för Microsoft Intune – april 2017

Den **tidiga utgåvan** innehåller en lista över funktioner som är planerade för kommande versioner av Microsoft Intune. Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
> Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nya funktioner

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Appens installationsstatus har förbättrats för Företagsportalappen för Windows 10 <!--676495-->

Företagsportalappen för Windows 10 har nu en förloppsindikatorn vid installation för alla moderna appinstallationer som startas från Företagsportalen.

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Förbättrade statusmeddelanden i Företagsportalappen för iOS <!--744866-->

Nya och mer specifika felmeddelanden visas nu i Företagsportalappen för iOS för att ger mer tillgänglig information om vad som händer i enheter. Dessa felärenden inkluderades tidigare i ett allmänt felmeddelande med titeln "Företagsportalen är för tillfället otillgänglig". Om en användare startar Företagsportalen på iOS när det inte finns en internetanslutning visas dessutom ett permanent statusfält på startsidan med texten "Ingen internetanslutning".

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps tillgängligt för hanterad webbläsare <!--822308, 822303-->

Microsoft MyApps har nu bättre stöd i den hanterade webbläsaren. Användare av hanterad webbläsare som inte är mål för hantering flyttas direkt till tjänsten MyApps där de kan komma åt sina administratörsetablerade SaaS-appar. Användare som är mål för Intune-hantering har även i fortsättningen åtkomst till MyApps från det inbyggda bokmärket för hanterad webbläsare.

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nya ikoner för den hanterade webbläsaren och företagsportalen <!--918433, 918431-->

Den hanterade webbläsaren får uppdaterade ikoner för både Android- och iOS-versionerna av appen. Den nya ikonen innehåller det uppdaterade Intune-märket så att det blir mer konsekvent med andra appar i Enterprise Mobility + Security (EM+S).

Företagsportalen får också uppdaterade ikoner för Android-, iOS- och Windows-versioner av appen för att förbättra enhetligheten med andra appar i EM+S. Dessa ikoner släpps gradvis över plattformar från april till slutet av maj.

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Stöd för enkel inloggning från företagsportalen för iOS till Outlook för iOS <!--834012-->

Användarna behöver inte längre logga in i Outlook-appen om de är inloggade på företagsportalappen för iOS på samma enhet med samma konto. När användarna startar Outlook-appen kan de välja sitt konto och logga in automatiskt. Vi arbetar också med att lägga till den här funktionen för andra Microsoft-appar.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Förloppsindikator för inloggning i Android-företagsportalen <!--953374-->

En uppdatering av Android-företagsportalappen visar en förloppsindikator för inloggning när användaren startar eller återupptar appen. Indikatorn går igenom nya statusmeddelanden, med början på "Ansluter...", sedan "Loggar in...", följt av "Kontrollerar säkerhetskrav..." innan användaren kommer åt appen.


## <a name="notices"></a>Meddelanden

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->

Apple har tillkännagivit att de från och med våren 2017 kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen. Läs [Intunes supportblogg](https://aka.ms/compportalats) för mer information.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->

För Intune-konto som har skapats senare än januari 2017 har Intune möjliggjort direktåtkomst till Apples-registreringsscenarier med arbetsbelastningen Registrera enheter i Azure Preview-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i den klassiska Intune-portalen. Intune-konton som skapats före januari 2017 behöver migreras vid ett tillfälle innan de här funktionerna finns tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till förhandsversionen.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Nyheter för Appx i Intune på Azure <!-- 1000270 -->

Som en del av migreringen till Intune på Azure gör vi tre appx-ändringar:

1. Vi lägger till en ny appx-apptyp i den klassiska Intune-konsolen som bara kan distribueras till MDM-registrerade enheter.
2. Vi ändrar syfte för den befintliga appx-apptypen så att den endast kan riktas mot datorer som hanteras via Intune PC-agenten.
3. Vi konverterar alla befintliga appx till MDM appx med migreringen.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?

Detta påverkar inte någon av dina befintliga distributioner till enheter som hanteras via Intune PC-agenten. Efter migreringen kommer du dock inte att kunna distribuera dessa migrerade appx-versioner till nya enheter som hanteras via Intune PC-agenten och som inte utgjorde mål tidigare.

#### <a name="what-action-do-i-need-to-take"></a>Vad behöver jag göra

Efter migreringen behöver du överföra appx igen som en PC-appx om du vill göra nya PC-distributioner. Läs mer i [Appx-ändringar i Intune på Azure](https://aka.ms/appxchange) på Intune-supportteamets blogg.  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Offentlig förhandsversion av den nya Intune-adminstratörsupplevelsen på Azure <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Stöd för hanterade konfigurationsalternativ för Android-appar <!-- 621621 -->

Android-appar i Play Store som har stöd för hanterade konfigurationsalternativ kan endast konfigureras av Intune.  Med hjälp av den här funktionen kan IT-personal visa listan över konfigurationsvärden som stöds av en app, vilket ger ett tydligt gränssnitt som gör det möjligt att konfigurera dessa värden.

### <a name="remote-assistance-for-android-devices----675418---"></a>Fjärrhjälp för Android-enheter <!-- 675418 -->

Intune kommer att använda [TeamViewer](https://www.teamviewer.com)-programvaran, som köps separat, för att göra det möjligt för dig att ge fjärrhjälp till de användare som kör Android-enheter.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Ny Android-princip för komplexa PIN-koder <!-- 722069 -->

Du kan ange den obligatoriska lösenordstypen Numerisk komplex i en Android-enhetsprofil för enheter som kör Android 5.0 och senare.  Använd den här inställningen för att hindra att enhetsanvändare skapar en PIN-kod som innehåller upprepande eller efterföljande siffror, t.ex. 1111 eller 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Ytterligare stöd för Android for Work-enheter

- **Hantera inställningar för lösenord och arbetsprofil** <!-- 612808 -->

  Vi har lagt till en ny enhetsbegränsningsprincip för Android for Work som gör det möjligt att hantera inställningar för lösenord och arbetsprofil på Android for Work-enheter som du hanterar.

- **Tillåt datadelning mellan arbetsprofiler och personliga profiler** <!-- 1045102 -->

  Vi har uppdaterat inställningen **Datadelning mellan arbetsprofiler och personliga profiler** i en begränsningsprofil för Android for Work-enheter med nya alternativ för att konfigurera datadelning mellan arbetsprofiler och personliga profiler.

- **Begränsa kopiera och klistra in mellan arbetsprofiler och personliga profiler** <!-- 1046094 -->

  När du hanterar Android for Work-enheter med Intune tillåts kopiera och klistra in mellan arbetsappar och personliga appar. Vi har nu lagt till en anpassad enhetsprofil för Android for Work-enheter som gör det möjligt att begränsa om åtgärderna kopiera och klistra in mellan arbetsappar och personliga appar är tillåtet.

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Tilldela branschspecifika appar till iOS- och Android-enheter <!-- 1057568 -->

Du kan tilldela branschspecifika appar för iOS (.ipa-filer) och Android (.apk-filer) till användare eller enheter.

###  <a name="new-policies-for-ios-devices----723774-723815-723826-723830-723832---"></a>Nya principer för iOS-enheter <!-- 723774, 723815, 723826, 723830, 723832 -->

- **Appar på startskärmen** – Du kan använda en enhetsprincip för att styra vilka appar användare ser på startskärmen på sina iOS-enheter. Den här principen ändrar layouten på startskärmen, men distribuerar inte några appar som du har angett som inte är installerade.

- **Anslutningar till AirPrint-enheter** – Du kan använda en Intune-enhetsprincip för att styra vilka AirPrint-enheter (nätverksskrivare) som användare av iOS-enheter kan ansluta till.

- **Anslutningar till AirPlay-enheter** – Du kan använda en Intune-enhetsprincip för att styra vilka AirPlay-enheter (t.ex. Apple TV) som användare av iOS-enheter kan ansluta till.

- **Anpassat meddelande på låsskärmen** – Du kan konfigurera ett anpassat meddelande som användarna ser på låsskärmen på sina iOS-enheter, som ersätter standardmeddelandet på låsskärmen.

- **Webbinnehållsfilter** – Du kan styra vilka webbplatser iOS-enhetsanvändare kan besöka, med hjälp av någon av följande två metoder:

  - Lägg till tillåtna och blockerade URL:er med hjälp av Apples inbyggda webbinnehållsfilter.
  - Tillåt endast åtkomst till angivna webbplatser från webbläsaren Safari. Bokmärken skapas i Safari för varje plats som du anger.


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Begränsa push-meddelanden för iOS-appar <!-- 723767 -->

Du kan konfigurera följande meddelandeinställningar för iOS-enheter i en begränsningsprofil för Intune-enheter:

- Aktivera eller inaktivera aviseringar helt för en angiven app.
- Aktivera eller inaktivera aviseringar i aviseringscentret för en angiven app.
- Ange aviseringstypen, antingen **Ingen**, **Banderoll** eller **Modal avisering**.
- Ange om aktivitetsikoner tillåts för den här appen.
- Ange om aviseringsljud tillåts.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Konfigurera iOS-appar för att köras i autonomt enkelappsläge <!-- 737837 -->

Du kan använda en Intune-enhetsprofil för att konfigurera iOS-enheter så att de kör angivna appar i autonomt enkelappsläge. När det här läget är konfigurerat och appen körs kommer enheten att låsas så att den endast kan köra den appen. Ett exempel på detta är när du konfigurerar en app som gör att användarna kan genomföra ett test på enheten. När appens åtgärder har slutförts, eller om du tar bort principen, återgår enheten till sitt normala tillstånd.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Konfigurera betrodda domäner för e-post och webbläsare på iOS-enheter <!-- 723765 -->

Du kan konfigurera följande domäninställningar i en begränsningsprofil för iOS-enheter:

- **Omarkerade e-postdomäner** – E-postmeddelanden som användaren skickar eller tar emot och som inte matchar de domäner du anger här, markeras som icke tillförlitliga.

- **Hanterade webbdomäner** – Dokument som laddats ned från de webbadresser du anger här betraktas som hanterade (endast Safari).  

- **Fyll i lösenord automatiskt för Safari-domäner** – Användare kan spara lösenord endast i Safari från URL:er som matchar de mönster du anger här. Om du vill använda den här inställningen måste enheten vara i övervakat läge och får inte vara konfigurerad för flera användare. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>VPP-appar som är tillgängliga i iOS-företagsportalen <!-- 748782 -->

Du kan tilldela volyminköpta (VPP) appar i iOS som **Tillgängliga** installationer för slutanvändare. Användarna behöver ett Apple Store-konto för att installera appen.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Synkronisera e-böcker från Apple VPP Store <!-- 800878 -->

Du kan synkronisera böcker som du har köpt från Apples butik för volyminköpta program med Intune och tilldela dem till användarna.

### <a name="shared-shift-worker-devices-for-samsung-knox-standard-devices----773753---"></a>Delade skiftarbetarenheter för Samsung KNOX Standard-enheter <!-- 773753 -->

Du kan konfigurera en Samsung KNOX Standard-enhet som en delad skiftarbetarenhet i Intune-portalen. När enheten är i delat läge kopplas appar, principer och e-post på den enheten till identiteten för den användare som loggar in på företagsportalen.
Användare kan logga in på företagsportalappen med sina autentiseringsuppgifter för Azure Active Directory, så verkställs deras appar, principer och e-postanställningar i enheten automatiskt.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Hantering av flera användare för Samsung KNOX Standard-enheter <!-- 971988 -->

Enheter som kör Samsung KNOX Standard stöds nu för hantering av flera användare i Intune. Det innebär att slutanvändarna kan logga in och ut från enheten med sina autentiseringsuppgifter för Azure Active Directory, och enheten hanteras centralt oavsett om den används eller inte.  När användarna loggar in får de tillgång till appar och dessutom verkställs eventuella principer som gäller för dem. Alla appdata rensas när användaren loggar ut.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Ytterligare begränsningsinställningar för Windows-enheter <!-- 818566 -->

Vi har lagt till stöd för ytterligare begränsningsinställningar för Windows-enheter, t.ex. ytterligare Edge-webbläsarstöd, anpassning av enhetens låsskärm, anpassning av startmenyn, bakgrund för Windows Spotlight-sökning och proxyinställningar.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Stöd för flera användare för Windows 10 Creators Update <!-- 822547 -->

Vi har lagt till stöd för hantering av flera användare för enheter som kör Windows 10 Creators Update och är domänanslutna med Azure Active Directory. Det innebär att när olika användare loggar in på enheten med sina autentiseringsuppgifter för AAD får de alla appar och principer som har tilldelats till deras användarnamn.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start för Windows 10-datorer<!-- 1004830 -->

I den här versionen har vi lagt till en ny Fresh Start-enhetsåtgärd för Windows 10-datorer.  När du kör den här åtgärden tas alla appar som har installerats på datorn bort, och datorn uppdateras automatiskt till den senaste Windows-versionen. Detta kan användas för att ta bort förinstallerade OEM-appar som ofta levereras med en ny dator. Du kan konfigurera om användardata ska behållas när den här enhetsåtgärden utförs.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Ytterligare uppgraderingsvägar i Windows 10 <!-- 903672 -->

Nu kan du skapa en uppgraderingsprincip för att uppgradera enheter till följande ytterligare Windows 10-utgåvor:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Massregistrera Windows 10-enheter <!-- 747607 -->

Du kan koppla ett stort antal Windows 10-enheter till Azure Active Directory och Intune med IT-automatiseringsverktyg. Om du vill aktivera automatisk MDM-registrering för Azure AD-klienten kan du skapa ett etableringspaket som kopplar enheten till Azure AD-klienten med hjälp av Windows Configuration Designer. Använd det paketet på företagsägda enheter som du vill massregistrera och hantera.  När paketet har verkställts ansluter enheterna till Azure AD, registreras i Intune och är redo för att Azure AD-användarna ska logga in.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----58112-736644---"></a>Nya MAM-inställningar för PIN-kod och hanterade lagringsplatser <!-- 58112, 736644 -->

Det finns två nya appinställningar som hjälper dig med scenarier för hantering av mobila program (MAM):

- **Inaktivera app-PIN när enhets-PIN är hanterad** – Identifierar om det finns en enhets-PIN på den registrerade enheten och förbigår i så fall den app-PIN som utlöses av appskyddsprinciperna. Den här inställningen minskar antalet gånger en PIN-uppmaning visas för användare som öppnar ett MAM-aktiverat program på en registrerad enhet. Den här funktionen är tillgänglig för både Android och iOS.

- **Välj med vilka lagringstjänster företagsdata ska sparas** – Gör det möjligt att ange de lagringsplatser där företagsdata ska sparas. Användare kan spara i valda lagringsplatstjänster, vilket innebär att alla lagringsplatstjänster som inte anges kommer att blockeras.

  Lista över lagringsplatstjänster som stöds:

  - OneDrive
  - Business SharePoint Online
  - Lokal lagring


### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).

