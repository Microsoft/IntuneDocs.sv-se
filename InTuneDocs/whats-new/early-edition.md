---
title: "Tidig utgåva | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/13/2017
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
ms.sourcegitcommit: 1ba0dab35e0da6cfe744314a4935221a206fcea7
ms.openlocfilehash: 3b355d43d4be05535f256d88a8648c2e67035882
ms.lasthandoff: 03/13/2017


---


# <a name="the-early-edition-for-microsoft-intune---march-2017"></a>Den tidiga utgåvan för Microsoft Intune – mars 2017

Den **tidiga utgåvan** innehåller en lista över funktioner som är planerade för kommande versioner av Microsoft Intune. Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
> Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nya funktioner

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622-->

Användargränssnittet för företagsportalappen för Android kommer att uppdateras för en mer modern känsla och bättre användarupplevelse. Viktiga uppdateringar är:

- Färger: Företagsportalens flikrubriker är färgade i enligt IT-område.
- Appar: På fliken **Appar** har knapparna **Aktuella appar** och **Alla appar** uppdaterats.
- Sökning: PÅ fliken **Sökning** är **Sökknappen** är nu flytande.
- Navigeringsappar: **Alla appar** visar en flikvy över **Aktuella**, **Alla** och **Kategorier** för att underlätta navigeringen.
- Support: Flikarna **Mina enheter** och **Kontakta IT** uppdateras för att göra dem mer läsbara.

Mer information om dessa ändringar finns på [app UI updates page](whats-new-in-intune-app-ui.md].

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Registrera skript för företagsportalen i Windows 10 <!--941642-->

För kunder som behöver hämta och läsa in Windows 10-företagsportalsappen separat kan du nu använda ett skript för att förenkla och effektivisera appsigneringsprocessen för din organisation.   Information om hur du hämtar skriptet och anvisningarna om hur du använder det finns i [Microsoft Intune-signeringsskript för företagsportalen i Windows 10](https://aka.ms/win10cpscript) i TechNet-galleriet. Mer information om det här meddelandet finns i [Uppdatera din Windows 10-företagsportalsapp](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) på Intune Support-teambloggen. 

## <a name="notices"></a>Meddelanden

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Förbättrat stöd för Android-användare i Kina <!--720444-->

På grund av avsaknad av Google Play-butik i Kina, måste Android-enheter hämta appar från kinesiska marknadsplatser. Företagsportalen kommer att stödja det här arbetsflödet genom att omdirigera Android-användare i Kina till att ladda ned appar för Företagsportalen och Outlook från lokala appbutiker. Detta förbättrar slutanvändarens upplevelse när principer för villkorlig åtkomst är tillämpliga, både för hantering av mobila enheter och för hantering av mobilappar. Appar för Företagsportalen och Outlook för Android är tillgängliga i följande kinesiska appbutiker:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->

Apple har tillkännagivit att de från och med våren 2017 kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen. Läs [Intunes supportblogg](https://aka.ms/compportalats) för mer information.

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Offentlig förhandsversion av den nya Intune-adminstratörsupplevelsen på Azure <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Icke-hanterade enheter kan komma åt tilldelade appar <!--664691-->

Som en del av designändringarna på företagsportalens webbplats ska iOS- och Android-användare kunna installera appar som har tilldelats dem som "tillgänglig utan registrering" på sina icke-hanterade enheter. Med sina Intune-autentiseringsuppgifter kan användare logga in på företagsportalens webbplats och se en lista över appar som tilldelats dem. App-paket för apparna som är "tillgängliga utan registrering" görs tillgängliga för hämtning via företagsportalens webbplats. Appar som kräver registrering för installation påverkas inte av den här ändringen, eftersom användarna uppmanas att registrera sina enheter om de vill installera apparna.

### <a name="improvements-to-device-actions-report---677150--"></a>Förbättringar av rapporten Enhetsåtgärder<!--677150-->

Vi har förbättrat rapporten Enhetsåtgärder för att förbättra dess prestanda. Nu kan du filtrera rapporten efter tillstånd. Exempelvis kan du filtrera rapporten för att endast visa enhetsåtgärder som har slutförts.

### <a name="actions-for-non-compliance---730266--"></a>Åtgärder vid inkompatibilitet <!--730266-->

**Åtgärder vid inkompatibilitet** är en ny funktion för efterlevnadsprinciper som gör det möjligt att vidta åtgärder för enheter som inte är kompatibla. Du kan ange en eller flera åtgärder och ange den tidsperiod då dessa åtgärder måste äga rum. Du kan till exempel meddela användare med inkompatibla enheter via e-post direkt efter att enheterna har blivit inkompatibla, eller så kan du blockera inkompatibla enheter från att få åtkomst till företagsresurser efter en respitperiod på tre dagar via villkorsstyrd åtkomst.

### <a name="custom-app-categories---748805--"></a>Anpassade appkategorier <!--748805-->

Du kan nu skapa, redigera och tilldela kategorier för appar som du lägger till i Intune. Kategorier kan för närvarande kan bara anges på engelska.
Läs [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Lägga till en app i Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Tilldela LOB-appar till användare med oregistrerade enheter <!--748823-->

Du kan nu tilldela branschspecifika appar och appar från butiken till användare, oavsett om deras enheter är registrerade i Intune eller inte. Om användarens enhet inte har registrerats i Intune måste användaren gå till företagsportalens webbplats, inte dess app, för att installera den.

### <a name="new-compliance-reports---846671--"></a>Nya efterlevnadsrapporter <!--846671-->

Nu har du efterlevnadsrapporter som ger ditt företags enheters efterlevnadsprofil och låter dig felsöka problem som berör efterlevnad snabbt efter hand som de upptäcks av dina användare. Du kan visa information om

- Övergripande efterlevnadstatus för enheter
- Efterlevnadstatus för en enskild inställning
- Efterlevnadstatus för en enskild princip

Du kan även använda dessa rapporter för att undersöka en individuell enhet på djupet för att se de inställningar och principer som påverkar enheten.

### <a name="additional-windows-10-upgrade-paths---903672--"></a>Ytterligare uppgraderingsvägar i Windows 10 <!--903672-->

Nu kan du skapa en uppgraderingsprincip för att uppgradera enheter till följande ytterligare Windows 10-utgåvor:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkt åtkomst till Apples registreringscenarier<!--951869-->

För Intune-konto som har skapats senare än januari 2017 har Intune möjliggjort direktåtkomst till Apples-registreringsscenarier med arbetsbelastningen Registrera enheter i Azure Preview-portalen. Tidigare var Apples förhandsregistrering enbart tillgänglig från länkar i den klassiska Intune-portalen. Intune-konton som skapats före januari 2017 behöver migreras vid ett tillfälle innan de här funktionerna finns tillgängliga i Azure. Schemat för migreringen har inte tillkännagivits än men informationen kommer att vara tillgänglig så snart som möjligt. Vi rekommenderar starkt att skapa ett utvärderingskonto för att testa den nya upplevelsen om ditt befintliga konto har inte åtkomst till förhandsversionen.

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).

