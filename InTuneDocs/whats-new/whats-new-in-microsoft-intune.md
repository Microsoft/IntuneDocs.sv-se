---
title: "Vad är nytt | Microsoft Docs"
description: "Ta reda på vad som är nytt i den här månadens och i tidigare versioner av Microsoft Intune"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c473a1f05b0a7b0ce5205598b2b9a9b86bfe6c1d
ms.openlocfilehash: bddd8c0dc74835f74a71af1d900d43d84aab894c
ms.lasthandoff: 03/29/2017


---
# <a name="whats-new-in-microsoft-intune---march-2017"></a>Nyheter i Microsoft Intune – marsh 2017
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

> [!Note]
> Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nya funktioner

### <a name="support-for-skycure"></a>Stöd för Skycure

Du kan nu styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Skycure, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som kör Skycure och inkluderar:

- Fysiskt skydd
- Nätverksskydd
- Programskydd
- Skydd mot säkerhetsrisker

Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Skycures riskbedömning som aktiveras via Intunes principer för enhetsefterlevnad. Du kan använda dessa principer för att tillåta eller blockera inkompatibla enheters åtkomst till företagets resurser utifrån identifierade hot. Mer information finns i [Skycure Mobile Threat Defense-anslutningsprogram](/intune/deploy-use/skycure-mobile-threat-defense-connector).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622-->

Användargränssnittet för företagsportalappen för Android kommer att uppdateras för en mer modern känsla och bättre användarupplevelse. Viktiga uppdateringar är:

- Färger: Företagsportalens flikrubriker är färgade i enligt IT-område.
- Appar: På fliken **Appar** har knapparna **Aktuella appar** och **Alla appar** uppdaterats.
- Sökning: PÅ fliken **Sökning** är **Sökknappen** är nu flytande.
- Navigeringsappar: **Alla appar** visar en flikvy över **Aktuella**, **Alla** och **Kategorier** för att underlätta navigeringen.
- Support: Flikarna **Mina enheter** och **Kontakta IT** uppdateras för att göra dem mer läsbara.

Mer information om dessa ändringar finns i [UI-uppdateringar för Intunes slutanvändarappar](whats-new-in-intune-app-ui.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Icke-hanterade enheter kan komma åt tilldelade appar <!--664691-->

Som en del av designändringarna på företagsportalens webbplats ska iOS- och Android-användare kunna installera appar som har tilldelats dem som "tillgänglig utan registrering" på sina icke-hanterade enheter. Med sina Intune-autentiseringsuppgifter kan användare logga in på företagsportalens webbplats och se en lista över appar som tilldelats dem. App-paket för apparna som är "tillgängliga utan registrering" görs tillgängliga för hämtning via företagsportalens webbplats. Appar som kräver registrering för installation påverkas inte av den här ändringen, eftersom användarna uppmanas att registrera sina enheter om de vill installera apparna.

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Registrera skript för företagsportalen i Windows 10 <!--941642-->

Om du behöver hämta och läsa in Windows 10-företagsportalsappen separat kan du nu använda ett skript för att förenkla och effektivisera appsigneringsprocessen för din organisation.   Information om hur du hämtar skriptet och anvisningarna om hur du använder det finns i [Microsoft Intune-signeringsskript för företagsportalen i Windows 10](https://aka.ms/win10cpscript) i TechNet-galleriet. Mer information om det här meddelandet finns i [Uppdatera din Windows 10-företagsportalsapp](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) på Intune Support-teambloggen.


## <a name="notices"></a>Meddelanden

### <a name="support-for-ios-103"></a>Stöd för iOS 10.3

Version 10.3 av iOS började distribueras till iOS-användare den 27 mars 2017. Alla befintliga Intune MDM- och MAM-scenarion är kompatibla med senaste versionen av Apples operativsystem. Vi utgår från att alla befintliga Intune-funktioner som för närvarande är tillgängliga för hantering av iOS-enheter även kommer att fungera efter det att dina användare har uppgraderat sina enheter och appar till iOS 10.3.

Det finns för närvarande inga kända problem att rapportera. Om du stöter på problem med iOS 10.3 så kontakta gärna [Intunes supportgrupp](/intune/troubleshoot/contact-assisted-phone-support-for-microsoft-intune).

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Förbättrat stöd för Android-användare i Kina <!--720444-->

På grund av avsaknad av Google Play-butik i Kina, måste Android-enheter hämta appar från kinesiska marknadsplatser. Företagsportalen kommer att stödja det här arbetsflödet genom att omdirigera Android-användare i Kina till att ladda ned appar för Företagsportalen och Outlook från lokala appbutiker. Detta förbättrar slutanvändarens upplevelse när principer för villkorlig åtkomst är tillämpliga, både för hantering av mobila enheter och för hantering av mobilappar. Appar för Företagsportalen och Outlook för Android är tillgängliga i följande kinesiska appbutiker:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Bästa praxis: Kontrollera att dina företagsportalsappar är aktuella<!--879465-->

I December 2016 släppte vi en uppdatering som framtvingande multifaktorautentisering (MFA) för en grupp användare när de registrerar en iOS-, Android-, Windows 8.1+- eller Windows Phone 8.1+-enhet. Den här funktionen fungerar inte utan vissa grundversioner av företagsportalsappen för Android (v5.0.3419.0+) och iOS (v2.1.17+).

Microsoft förbättrar kontinuerligt Intune genom att lägga till nya funktioner i både konsolen och företagsportalsapparna på alla de plattformar som stöds. Microsoft släpper därför bara korrigeringar för problem som vi hittar i den aktuella versionen av företagsportalsappen. Därför rekommenderar vi att du använder de senaste versionerna av företagsportalsapparna.

>[!Tip]
> Se till att användarna konfigurerar sina enheter så att de uppdaterar sina appar automatiskt från rätt appbutik. Om du har gjort en Android-företagsportalsapp tillgänglig på en nätverksresurs, så kan du hämta den senaste versionen från [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49140).

### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>Microsoft Teams har nu aktiverats för MAM på iOS och Android

Microsoft har tillkännagivit Microsoft Teams är allmänt tillgängligt. De uppdaterade Microsoft Teams-apparna för iOS och Android har nu aktiverats med Intune MAM-funktioner, så du kan underlätta för dina grupper att arbeta fritt på olika enheter, samtidigt som skyddet för konversationer och företagsdata säkerställs i varje situation. Mer information finns i [Microsoft Teams-tillkänngagivandet](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) på bloggen Enterprise Mobility and Security.


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Vad är nytt i den offentliga förhandsversion av Intunes adminstratörsupplevelse på Azure <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](/intune-azure/introduction/whats-new).

> [!Note]
> För Azure Portal Preview lanserar vi uppdateringarna för den här månaden. Det kan dock vara så att ändringarna inte är tillgängliga direkt pga hur Intune-tjänsten distribueras.  Flera av tjänstens komponenter måste uppdateras sekventiellt innan de nya portalfunktionerna blir tillgängliga. Sök efter ändringar i Azure Portal Preview i takt med att de lanseras senare under månaden. Den fullständiga listan med ändringar finns i [Nyheter i Microsoft Intune Preview](/intune-azure/introduction/whats-new).

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Administratörsroller ersätts i Azure Portal

De befintliga MAM-administratörsrollerna (deltagare, ägare och skrivskyddat) som används i den klassiska Intune-portalen (Silverlight) ersätts med en helt ny uppsättning rollbaserade administratörskontroller (RBAC) i Intune Azure Portal. När du har migrerat till Azure Portal måste du tilldela dina administratörer dessa nya administratörsroller. Mer information om RBAC och nya de nya rollerna finns i [Rollbaserad åtkomstkontroll för Microsoft Intune](/intune-azure/access-control/role-based-access-control).


## <a name="whats-coming"></a>Kommande nyheter

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->

Apple har tillkännagivit att de från och med våren 2017 kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen. Läs [Intunes supportblogg](https://aka.ms/compportalats) för mer information.

### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Vad är nytt i förhandsversionen av Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Nyheter i företagsportalens gränssnitt](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Nyhetsarkiv](whats-new-archive.md)

