---
title: "Tidig utgåva | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 33f3c8d91d5e4f17a4542d828d1883e33a339221
ms.openlocfilehash: afe06e523e7688cab2effeb6999be3193066add8
ms.contentlocale: sv-se
ms.lasthandoff: 05/05/2017


---

# <a name="the-early-edition-for-microsoft-intune---may-2017"></a>Den tidiga utgåvan för Microsoft Intune – maj 2017

Den **tidiga utgåvan** innehåller en lista över funktioner som är planerade för kommande versioner av Microsoft Intune. Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
> Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nya funktioner

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Stöd för enkel inloggning från företagsportalen för iOS till Outlook för iOS <!--834012-->

Användarna behöver inte längre logga in i Outlook-appen om de är inloggade på företagsportalappen för iOS på samma enhet med samma konto. När användarna startar Outlook-appen kan de välja sitt konto och logga in automatiskt. Vi arbetar också med att lägga till den här funktionen för andra Microsoft-appar.

### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Förbättrat meddelande för PIN-koder vid start av Samsung KNOX <!--1087143-->

När användarna måste ange en PIN-kod för start på Samsung KNOX-enheter för att bli kompatibla med kryptering, visas meddelandet för användarna. De kommer till rätt plats i appen Inställningar när de trycker på meddelandet.  Meddelandet tog tidigare användaren till skärmen där lösenord ändras.

### <a name="promoting-the-most-current-version-of-the-company-portal-for-android---1098661--"></a>Använda den senaste versionen i företagsportalen för Android <!--1098661-->

Användarna ser ett meddelande på appens meddelandeskärm när en ny rekommenderad version av företagsportalappen för Android har släppts. Meddelandet är ”En uppdatering av företagsportalen finns tillgänglig”. När de trycker på meddelandet öppnas en webbsida med en lista över de tillgängliga appbutiker där de kan hämta den uppdaterade versionen. 

### <a name="improvements-to-app-syncing-with-windows-10-creators-update----676505---"></a>Förbättringar av appsynkronisering med Windows 10 Creators Update <!-- 676505 -->

Företagsportalen för Windows 10 kommer automatiskt att initiera en synkronisering för appinstallationsbegäranden för enheter med Windows 10 Creators Update (1704). Detta minskar problemen där appen fastnar vid tillståndet ”Väntar på synkronisering” när installationer utförs. Dessutom kommer användare att kunna initiera en synkronisering från appen manuellt. 

Företagsportalen för Windows 10 kommer också att innehålla en uppdateringsknapp för att ge användarna möjlighet att uppdatera innehållet i appen vid behov. 

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

Detta påverkar inte någon av dina befintliga distributioner till enheter som hanteras via Intune PC-agenten. Efter migreringen kommer du dock inte att kunna distribuera dessa migrerade appx-versioner till nya enheter som hanteras via Intune PC-agenten och som inte utgjorde mål tidigare.

Efter migreringen behöver du överföra appx igen som en PC-appx om du vill göra nya PC-distributioner. Läs mer i [Appx-ändringar i Intune på Azure](https://aka.ms/appxchange) på Intune-supportteamets blogg.  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Offentlig förhandsversion av den nya Intune-adminstratörsupplevelsen på Azure <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Stöd för hanterade konfigurationsalternativ för Android-appar <!-- 621621 -->

Du kommer att kunna konfigurera Android-appar i Play Store som har stöd för hanterade konfigurationsalternativ.  Med hjälp av den här funktionen kan du se listan med konfigurationsvärden som stöds av en app, vilket ger ett tydligt gränssnitt som gör det möjligt att konfigurera dessa värden.

### <a name="remote-assistance-for-android-devices----675418---"></a>Fjärrhjälp för Android-enheter <!-- 675418 -->

Intune kommer att använda [TeamViewer](https://www.teamviewer.com)-programvaran, som köps separat, för att göra det möjligt för dig att ge fjärrhjälp till de användare som kör Android-enheter.

### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Förkonfigurera enhetsbehörigheter för Android for Work-appar <!-- 621614 -->

För appar som distribuerats till Android for Work-arbetsprofiler, kommer du att kunna konfigurera behörighetstillstånd för enskilda appar. Som standard kommer Android-appar som kräver enhetsbehörigheter, som t.ex. åtkomst till en plats eller enhetens kamera, att uppmana användarna att godkänna eller neka behörigheter.  Om till exempel en app ska använda enhetens mikrofon, ombeds användaren att bevilja appen behörighet att använda mikrofonen. Med den här funktionen kan du ange behörigheter åt användaren.  Administratören kan konfigurera behörigheter att

- Neka automatiskt utan att meddela användaren
- Godkänn automatiskt utan att meddela användaren
- Uppmana användaren att godkänna eller neka.

### <a name="define-app-specific-pin-for-android-for-work-devices---728976--"></a>Definiera en appspecifik PIN-kod för Android for Work-enheter <!--728976-->

Du kommer att kunna definiera en princip för lösenord som bara gäller för appar i arbetsprofilen för Android 7.0 och senare enheter som hanteras som en Android for Work-enhet.  Alternativen är:

- Definiera bara en enhetsomfattande lösenordsprincip. Detta är det lösenord som användaren måste använda för att låsa upp hela enheten
- Definiera bara en lösenordsprincip för arbetsprofilen. Användarna uppmanas att ange ett lösenord varje gång en app i arbetsprofilen öppnas.
- Definiera både en enhets- och en arbetsprofilprincip. IT-avdelningen kan välja att definiera både en lösenordsprincip för enheten och en lösenordsprincip för arbetsprofilen med olika styrkor (t.ex. en 4-siffrig PIN-kod för att låsa upp enheten, men en 6-siffrig PIN-kod för att öppna arbetsappar)

>[!NOTE]
> Det här är bara tillgängligt på Android 7.0 och högre.  Användaren kan som standard välja att använda två separat definierade PIN-koder, eller välja att kombinera de två definierade PIN-koderna till den starkaste av de två.

### <a name="manage-password-and-other-android-for-work-settings---1102534--"></a>Hantera lösenord och andra Android for Work-inställningar <!--1102534-->

Vi har lagt till en ny enhetsbegränsningsprincip för Android for Work som gör det möjligt att hantera inställningar för lösenord och arbetsprofil på Android for Work-enheter.

###  <a name="new-web-content-filter-policy-for-ios-devices----723832---"></a>Ny princip för webbinnehållsfilter på iOS-enheter <!-- 723832 -->

Du kommer att kunna styra vilka webbplatser iOS-enhetsanvändarna kan besöka, med hjälp av någon av följande två metoder:

  - Lägg till tillåtna och blockerade URL:er med hjälp av Apples inbyggda webbinnehållsfilter.
  - Tillåt endast åtkomst till angivna webbplatser från webbläsaren Safari. Bokmärken skapas i Safari för varje plats som du anger.

### <a name="apple-school-manager-asm-support---748864--"></a>Stöd för Apple School Manager (ASM) <!--748864-->

Intune stöder användning av Apple School Manager (ASM) för extern registrering av iOS-enheter, i stället för Apples program för enhetsregistrering. ASM-integrering krävs för att använda Classroom-appen på delade iPads, samt krävs för att aktivera datasynkronisering från ASM till Azure Active Directory via Microsoft School Data Sync (SDS).  

### <a name="shared-ipad-support---770395-1044681---"></a>Stöd för delad iPad <!--770395, 1044681 -->

Intune stöder konfiguration av delat iPad- läge i registreringsprofilen för Apples program för enhetsregistrering eller Apple School Manager. Med den här inställningen kan flera hanterade Apple-ID:n logga in på samma enhet.

Vi kommer även att expandera stödet för att hantera iOS Classroom-app, för att kunna inkludera elever som loggar in på delade iPads med sina hanterade Apple-ID:n.

### <a name="new-windows-device-restriction-settings---978585--"></a>Nya begränsningsinställningar för Windows-enheter <!--978585-->

Vi lägger till inställningar i begränsningsprofilen för Windows-enheter som styr funktioner som trådlösa skärmar, enhetsidentifiering, programväxling och felmeddelanden för SIM-kort.

### <a name="office-365-proplus-app-available-for-windows-10-devices---1121362--"></a>Office 365 ProPlus-appen är tillgänglig för Windows 10-enheter <!--1121362-->

Vi lägger till den nya Office 365 ProPlus-apptypen som gör det enkelt att tilldela Office 365 ProPlus-appar till Windows 10-enheter. Dessutom kommer du även att kunna installera Microsoft Project och Microsoft Visio om du har licenser för dem. Appar som du vill använda paketeras tillsammans och visas som en enda app i listan med appar i Intune-konsolen.

### <a name="new-allowblock-list-for-the-managed-browser---682960--"></a>Ny lista för Tillåt/blockera för Managed Browser <!--682960-->

Du kommer att kunna konfigurera listan Tillåt/blockera för domäner och webbadresser i Managed Browser med Intunes inställningar för programkonfiguration i Azure-portalen. Detta kan konfigureras för Managed Browser oavsett om den används på en hanterad eller ohanterad enhet.

### <a name="new-app-configuration-capabilities----677969---"></a>Nya funktioner för appkonfiguration <!-- 677969 -->

Den här funktionen kommer att motsvara appkonfigurationen för hantering av mobila enheter (MDM). Med denna funktion kan administratörer tillämpa fler appkonfigurationsvärden än de som bara är tillgängliga via appskyddsprinciperna i MAM utan registreringskanal.

### <a name="new-app-protection-policies-conditions-for-mam---679864--"></a>Nya villkor för appskyddsprinciper i MAM <!--679864-->

Du kommer att kunna ange ett krav för MAM utan att registrera användare via administratörskonsolen för följande:

- Lägsta programversion
- Lägsta operativsystemversion
- Lägsta Intune APP SDK-version i det aktuella programmet (endast iOS)

Den här funktionen kommer att vara tillgänglig för både Android och iOS. Intune stöder krav på minimiversion för operativsystemversioner, programversioner och Intune APP SDK. I iOS kan program som har integrerat SDK också ange ett lägsta versionskrav på SDK-nivå.

Användaren kommer inte att få åtkomst till det aktuella programmet om minimikraven via appskyddsprincipen inte uppfylls på de tre olika nivåer som nämns ovan. Nu kan användaren kan antingen ta bort sitt konto (för program med flera identiteter), stänga programmet och/eller uppdatera sitt operativsystem eller program för att uppfylla kravet.

Dessutom kan du också konfigurera ytterligare inställningar via administratörskonsolen för ett icke-blockerande meddelande som rekommenderar en uppgradering av operativsystemet eller programmet. Det här meddelandet kan stängas och programmet kan då användas som vanligt.

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Ändra din utfärdare för hantering av mobila enheter utan att avregistrera hanterade enheter <!--1103950-->

Du kommer att kunna ändra din utfärdare för hantering av mobila enheter utan att behöva kontakta Microsoft Support och utan att behöva avregistrera och omregistrera dina befintliga hanterade enheter. I Configuration Manager-konsolen kan du ändra utfärdare för hantering av mobila enheter från Ange till Configuration Manager (hybrid) till Microsoft Intune (fristående) eller vice versa.


### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).

