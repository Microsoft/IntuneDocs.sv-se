---
title: "Vad är nytt | Microsoft Docs"
description: "Ta reda på vad som är nytt i den här månadens och i tidigare versioner av Microsoft Intune"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2e6452a066aa7eaeb295a3b531d83dc3b632bcf5
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---
# <a name="whats-new-in-microsoft-intune---april-2017"></a>Nyheter i Microsoft Intune – April 2017
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

> [!Note]
> Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nya funktioner

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps tillgängligt för hanterad webbläsare <!--822308, 822303-->

Microsoft MyApps har nu bättre stöd i den hanterade webbläsaren. Användare av hanterad webbläsare som inte är mål för hantering flyttas direkt till tjänsten MyApps där de kan komma åt sina administratörsetablerade SaaS-appar. Användare som är mål för Intune-hantering har även i fortsättningen åtkomst till MyApps från det inbyggda bokmärket för hanterad webbläsare.

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Nya ikoner för den hanterade webbläsaren och företagsportalen <!--918433, 918431, 971473-->

Den hanterade webbläsaren får uppdaterade ikoner för både Android- och iOS-versionerna av appen. Den nya ikonen innehåller det uppdaterade Intune-märket så att det blir mer konsekvent med andra appar i Enterprise Mobility + Security (EM+S). Du kan se den nya ikonen för Managed Browser på sidan med [nyheter i användargränssnittet i Intune-appen](whats-new-in-intune-app-ui.md).

Företagsportalen får också uppdaterade ikoner för Android-, iOS- och Windows-versioner av appen för att förbättra enhetligheten med andra appar i EM+S. Dessa ikoner släpps gradvis till plattformarna från april till slutet av maj.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Förloppsindikator för inloggning i Android-företagsportalen <!--953374-->

En uppdatering av Android-företagsportalappen visar en förloppsindikator för inloggning när användaren startar eller återupptar appen. Indikatorn går igenom nya statusmeddelanden, med början på "Ansluter...", sedan "Loggar in...", följt av "Kontrollerar säkerhetskrav..." innan användaren kommer åt appen. Du kan se de nya skärmarna för företagsportalsappen för Android på [sidan Nyheter i användargränssnittet i Intune-appen](whats-new-in-intune-app-ui.md).

### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Blockera appar från åtkomst till SharePoint Online <!-- 679339 -->

Nu kan du skapa en appbaserad princip för villkorlig åtkomst för att blockera appar som inte har fått appprinciperna tillämpade från åtkomst till [SharePoint Online](/intune-classic/deploy-use/mam-ca-for-sharepoint-online). Du kan ange de appar som du vill ska ha åtkomst till SharePoint Online med Azure-portalen i det appbaserade scenariot för villkorlig åtkomst.

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Stöd för enkel inloggning från företagsportalen för iOS till Outlook för iOS <!--834012-->
Användarna behöver inte längre logga in i Outlook-appen om de är inloggade på företagsportalappen för iOS på samma enhet med samma konto. När användarna startar Outlook-appen kan de välja sitt konto och logga in automatiskt. Vi arbetar också med att lägga till den här funktionen för andra Microsoft-appar.

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Förbättrade statusmeddelanden i Företagsportalappen för iOS <!--744866-->
Nya och mer specifika felmeddelanden visas nu i Företagsportalappen för iOS för att ger mer tillgänglig information om vad som händer i enheter. Dessa felärenden inkluderades tidigare i ett allmänt felmeddelande med titeln "Företagsportalen är för tillfället otillgänglig". Om en användare startar Företagsportalen på iOS när det inte finns en internetanslutning visas dessutom ett permanent statusfält på startsidan med texten "Ingen internetanslutning".

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Appens installationsstatus har förbättrats för Företagsportalappen för Windows 10 <!--676495-->

Nya förbättringar för appinstallationer i företagsportalappen för Windows 10 är:
-    Snabbare rapportering av installationsförlopp för MSI-paket
-    Snabbare rapportering av installationsförlopp för moderna appar på enheter som kör Windows 10 Anniversary Update och nyare
-    Ny förloppsindikator vid installation av moderna appar på enheter som kör Windows 10 Anniversary Update och nyare

Du kan se den nya förloppsindikatorn på sidan [nyheter i användargränssnittet i Intune-appen](whats-new-in-intune-app-ui.md).

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Massregistrera Windows 10-enheter <!-- 747607 -->

Du kan du ansluta till ett stort antal enheter som kör Windows 10 Creators-uppdateringen till Azure Active Directory och Intune med Windows Configuration Designer /intune-classic/deploy-use/bulk-enroll-windows) för din Azure AD-klient, skapa ett etableringspaket som ansluter enheter till din Azure AD-klient med Windows Configuration Designer, samt använda paketet för företagsägda enheter som du vill massregistrera och masshantera. När paketet har tillämpats på dina enheter kommer Azure AD att anslutas, registreras i Intune och vara redo för att Azure AD-användarna ska logga in.  Azure AD-användare är standardanvändare på de här enheterna och tar emot tilldelade principer och nödvändiga appar. Självbetjäning och företagsportalscenarier stöds inte för närvarande.

## <a name="notices"></a>Meddelanden

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

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Vad är nytt i den offentliga förhandsversion av Intunes adminstratörsupplevelse på Azure <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](/intune/whats-new).

> [!Note]
> För Azure Portal Preview lanserar vi uppdateringarna för den här månaden. Det kan dock vara så att ändringarna inte är tillgängliga direkt pga hur Intune-tjänsten distribueras.  Flera av tjänstens komponenter måste uppdateras sekventiellt innan de nya portalfunktionerna blir tillgängliga. Sök efter ändringar i Azure Portal Preview i takt med att de lanseras senare under månaden. Den fullständiga listan med ändringar finns i [Nyheter i Microsoft Intune Preview](/intune/whats-new).

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Administratörsroller ersätts i Azure Portal

De befintliga MAM-administratörsrollerna (deltagare, ägare och skrivskyddat) som används i den klassiska Intune-portalen (Silverlight) ersätts med en helt ny uppsättning rollbaserade administratörskontroller (RBAC) i Intune Azure Portal. När du har migrerat till Azure Portal måste du tilldela dina administratörer dessa nya administratörsroller. Mer information om RBAC och nya de nya rollerna finns i [Rollbaserad åtkomstkontroll för Microsoft Intune](/intune/role-based-access-control).

## <a name="whats-coming"></a>Kommande nyheter

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Förbättrad inloggning i företagsportalens appar för alla plattformar <!--User Story 1132123-->

Vi presenterar en ändring under de kommande månaderna som förbättrar inloggningen för Intune-företagsportalens appar för Android, iOS och Windows. Det nya användargränssnittet visas automatiskt på alla plattformar för företagsportalappen när Azure AD genomför ändringen. Dessutom kan användarna nu logga in på företagsportalen från en annan enhet med en engångskod som genereras. Detta är särskilt användbart när användarna måste logga in utan autentiseringsuppgifter.

Du hittar skärmdumpar av föregående inloggning, den nya inloggningen med autentiseringsuppgifter och den nya inloggningen från en annan enhet på sidan [Nyheter i appens användargränssnitt](whats-new-in-intune-app-ui.md).

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan för ändringar: Intune ändrar Intune-partnerportalens gränssnitt<!-- 1050016 -->

Vi tar bort sidan Intune-Partner från manage.microsoft.com från och med tjänstuppdateringen i mitten på maj 2017.  

Om du är partneradministratör, kommer du inte längre att kunna visa och vidta åtgärder åt dina kunder från sidan Intune Partner. I stället måste du logga in på en av två andra partnerportaler hos Microsoft.

Både [Microsoft Partner Center](https://partnercenter.microsoft.com/) och [Administrationscenter för Microsoft Office 365 Partner](https://portal.office.com/) gör att du kan logga in på kundkonton som du hanterar. I framtiden kan du som partner använda en av dessa webbplatser för att hantera dina kunder.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->

Apple har tillkännagivit att de kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen.

Vi har gjort en version av företagsportalens app tillgänglig för iOS genom Apple TestFlight-programmet som genomdriver de nya ATS-kraven. Om du vill prova, så att du kan testa din ATS-kompatibilitet, kan du skicka ett e-post-meddelande till <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app"> CompanyPortalBeta@microsoft.com </a> med ditt förnamn, efternamn, din e-postadress och företagets namn. Läs [Intunes supportblogg](https://aka.ms/compportalats) för mer information.

### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Vad är nytt i förhandsversionen av Azure](https://docs.microsoft.com/intune/whats-new)
* [Nyheter i företagsportalens gränssnitt](/intune-classic/whats-new/whats-new-in-company-portal-ui)
* [Nyhetsarkiv](whats-new-archive.md)

