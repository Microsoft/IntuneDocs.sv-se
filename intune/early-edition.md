---
title: "Tidig utgåva"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 12f4a09fe10ec792abe8183369a21f53c23f5d1a
ms.sourcegitcommit: 53d272defd2ec061dfdfdae3668d1b676c8aa7c6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2018
---
# <a name="the-early-edition-for-microsoft-intune---january-2018"></a>Den tidiga utgåvan för Microsoft Intune – Januari 2018

Den **tidiga utgåvan** innehåller en lista med funktioner i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte denna information med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
>Följande ändringar är under utveckling för Intune. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->


## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546---"></a>Enklare lösning av efterlevnadsproblem för företagsportalappen för Windows 10 <!--676546 -->

Slutanvändare med Windows-enheter kan trycka på orsaken till bristande efterlevnad i företagsportalappen. Om möjligt kommer de då direkt till rätt plats i inställningsappen för att kunna åtgärda problemet.

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Nya alternativ för användarautentisering för Apple-massregistrering <!-- 747625 -->
Intune ger dig möjlighet att autentisera enheter med hjälp av företagsportalappen för följande registreringsmetoder:

- Apples DEP (Device Enrollment Program)
- Apple School Manager
- Registrera Apple Configurator

När du använder alternativet Företagsportalen, kan Azure Active Directory-multifaktorautentisering tillämpas utan att blockera dessa registreringsmetoder.

När du använder alternativet Företagsportalen, hoppar Intune över användarautentisering i iOS-installationsassistenten för registrering av användartillhörighet. Detta innebär att enheten först registreras som en användarlös enhet och därför inte tar emot konfigurationer eller principer från användargrupper. Den tar bara emot konfigurationer och principer för enhetsgrupper. Intune kommer dock automatiskt att installera företagsportalappen på enheten. Den första användaren som startar och loggar in på företagsportalappen kommer att associeras med enheten i Intune. Användaren får då konfigurationer och principer för sina användargrupper. Användarassociationen kan inte ändras utan omregistrering.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-stöd för flera Apple DEP/Apple School Manager-konton<!-- 747685 -->
Intune stöder registrering av enheter från upp till 100 olika Apple-program för enhetsregistrering (DEP) eller Apple School Manager-konton. Varje token som har överförts kan hanteras separat för registreringsprofiler och- enheter. En annan profil kan tilldelas automatiskt per DEP/School Manager-token som har överförts. Om flera School Manager-token har överförs, kan bara en åt gången delas med Microsoft School-datasynkronisering.

Efter migreringen fungerar inte beta-Graph API:er och publicerade skript för att hantera Apple DEP eller ASM över Graph längre. Nya beta-Graph API:er är under utveckling och kommer att släppas efter migreringen.

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eeready---"></a>Välj enhetskategorier med hjälp av inställningarna för åtkomst till arbete eller skola <!-- 1058963 eeready -->
Om du har aktiverat [mappning av enhetsgrupp](https://docs.microsoft.com/en-us/intune/device-group-mapping), uppmanas Windows 10-användare att välja en enhetskategori efter registreringen via knappen **Anslut** i **Inställningar** > **Konton** > **Åtkomst till arbete eller skola** eller under välkomstprogrammet.

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ange mål för efterlevnadsprinciper för enheter i enhetsgrupperna <!--1307012 -->

Du kommer att kunna ange mål för efterlevnadsprinciper för användare i användargrupperna. Du kommer att kunna ange mål för efterlevnadsprinciper för enheter i användargrupperna.

### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inklusive och exklusive apptilldelning baserat på grupperna <!-- 1406920 -->

Under apptilldelning och när du har valt en tilldelningstyp kommer du att kunna välja de grupper som ska inkluderas, samt de grupper som ska undantas.

### <a name="remote-erase-command-support----1438084---"></a>Fjärråtkomst till kommandostöd ”Radera” <!-- 1438084 -->

Administratörer kommer att kunna utfärda ett Radera-kommando via fjärranslutning.

> [!IMPORTANT]
> Raderingskommandot kan inte ångras och bör användas med försiktighet.

Raderingskommandot tar bort alla data, inklusive operativsystemet från en enhet. Det tar också bort enheten från Intune-hantering. Ingen varning utfärdas till användaren och raderingen sker omedelbart efter kommandot.

Du kommer att kunna konfigurera en 6-siffrig PIN-kod. Den här PIN-kod kan användas för att låsa upp enheten som raderats, då ominstallation av operativsystemet börjar. När raderingen har startats visas PIN-koden i ett statusfält på enhetens översiktsblad i Intune. PIN-koden kommer att finnas kvar så länge raderingen pågår. När raderingen är klar försvinner enheten helt från Intune-hanteringen. Tänk på att notera PIN-koden så att den som återställer enheten kan använda den.

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows Information Protection (PIA)-krypterad data i Windows-sökresultat <!-- 1469193 -->

En ny inställning i principen för Windows Information Protection (PIA) gör att du kan kontrollera om PIA-krypterade data ingår i Windows-sökresultaten.

### <a name="website-learning-mode----1631908---"></a>Inlärningsläge för webbplats <!-- 1631908 -->

Intune ger dig ett tillägg för Windows Information Protection (PIA)-inlärningsläget. Förutom att visa information om PIA-aktiverade appar, kommer du att kunna visa en sammanfattning av de enheter som har delat arbetsdata med webbplatser. Med den här informationen kan du bestämma vilka webbplatser som ska läggas till i gruppernas och användarnas PIA-principer.

### <a name="updates-to-compliance-emails---1637547---"></a>Uppdateringar till efterlevnads-e-post <!--1637547 -->

När ett e-postmeddelande skickas för att rapportera om en inkompatibel enhet, tas information om den inkompatibla enheten med. Följande artikel kommer att uppdateras för att ange detta faktum: [Automatisera åtgärder för inkompatibilitet](#actions-for-noncompliance).

### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Principer för villkorlig åtkomst för Intune är endast tillgängliga från Azure Portal <!-- 1737088 1634311 -->
Vi gör det enklare för dig att konfigurera och hantera villkorlig åtkomst. Du konfigurerar och hanterar dina principer på [Azure Portal](https://portal.azure.com) från **Azure Active Directory** > **Villkorlig åtkomst**. Du kan även komma åt det här bladet från Intune på Azure Portal på **Intune** > **Villkorlig åtkomst**.

###  <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Aviseringar om att token har upphört att gälla och om att token snart upphör att gälla <!-- 1639263 -->
På översiktssidan visas aviseringar om att token har upphört att gälla och om att token snart upphör att gälla. När du klickar på en avisering för en enskild token fortsätter du till denna tokens informationssida.  Om du klickar på avisering för flera token kommer du till en lista över alla token med deras status. Administratörer bör förnya sina tokens innan förfallodatumet.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Fjärrutskrift via ett säkert nätverk <!-- 1709994  -->
PrinterOn:s trådlösa mobila lösningar gör att användare via fjärranslutning kan skriva ut var och när som helst via ett säkert nätverk. PrinterOn kan integreras med Intune APP SDK för både iOS och Android. Du kommer att kunna ange mål för appskyddsprinciper för den här appen via bladet Intune **Appskyddsprinciper** i administrationskonsolen. Användarna kommer att kunna ladda ner appen PrinterOn for Microsoft via Play Store eller iTunes för att använda i sina Intune-ekosystem.

### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>Godkänn företagsportalappen för Android for Work <!--1797090 -->
Om din organisation använder Android for Work, måste du manuellt godkänna företagsportalappen för Android så att den fortsätter att ta emot automatiska uppdateringar från den hanterade Google Play-butiken.

### <a name="faceid-on-ios-devices----1807377---"></a>FaceID på iOS-enheter <!-- 1807377 -->
Intune-appskyddsprinciper har nu stöd för en inställning som styr FaceID på iOS-enheter. Den här inställningen är avsedd för enheter som har stöd för FaceID-funktionen (för närvarande endast iPhone X). Den här inställningen är separat från de TouchID-kontroller som stöds för närvarande. Organisationer kan välja om de vill lita på FaceID som en giltig PIN-uppmaning som ett alternativ till TouchID-kontrollerna.

### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>Microsoft Graph API för Intune – allmän tillgänglighet <!-- 1833289 -->
Intune API:er i Microsoft Graph ger programmatisk åtkomst till data och metoder för att automatisera administrativa åtgärder för Intune-tjänsten.  Med **Allmän tillgänglighet** kommer dessa API:er, kunder, partners och utvecklare att kunna utnyttja API:erna för att integrera med interna eller externa lösningar som gäller för eller som kräver stöd för Intune eller andra Microsoft-tjänster som är tillgängliga via Microsoft Graph.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Appskyddsprinciper  <!-- 679615 -->
Intunes appskyddsprinciper ger dig möjligheten att skapa globala standardprinciper för att snabbt aktivera skydd för alla användare i hela klientorganisationen.

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Återkallande av iOS-appar från volyminköpsprogram  <!-- 820863 -->
Du kommer att kunna återkalla associerade enhetsbaserade applicenser för enheten för en given enhet som har en eller flera iOS-appar för volyminköpsprogram (VPP). Om du återkallar en applicens så avinstalleras inte den relaterade VPP-appen från enheten. Om du vill avinstallera en VPP-app, måste du ändra tilldelningsåtgärden till **avinstallera**. Mer information finns i [så här hanterar du iOS-appar som köpts genom ett volyminköpsprogram med Microsoft Intune](vpp-apps-ios.md).

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Återkalla licenser för en token för iOS-volyminköpsprogram <!-- 820870 -->
Du kommer att kunna återkalla licensen för alla iOS-appar för volyminköpsprogram (VPP) för en given VPP-Token.

### <a name="new-ios-device-action------1244701---"></a>Ny iOS-enhetsåtgärd   <!-- 1244701 -->
Du kan stänga av iOS 10.3-övervakade enheter. Den här åtgärden stänger av enheten omedelbart utan varning till slutanvändaren. Åtgärden **stäng ner (endast övervakat)** finns i enhetsegenskaperna när du väljer en enhet i arbetsbelastningen **enhet**.


### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune erbjuder nu åtgärden flytta kontot <!-- 1573558, 1579830 -->
**Flytta kontot** migrerar en klient från en Azure-skalenhet (ASU) till en annan. **Flytta kontot** kan användas för både kundinitierade scenarier, när du anropar Intunes supportteam som begär det och det kan vara ett Microsoft-drivet scenario där Microsoft behöver göra justeringar i tjänsten i serverdelen. Vid **flytta kontot**, går klienten in i skrivskyddat läge (ROM). Tjänståtgärder som registrering, byta namn på enheter, uppdatering av efterlevnadsstatus misslyckas under ROM-perioden.




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Tilldela Office 365-mobilappar till iOS och Android-enheter med den inbyggda apptypen <!-- 1332318 -->
Den **inbyggda** apptypen gör det enklare att skapa och tilldela Office 365-appar till iOS- och Android-enheter som du hanterar. De här apparna inkluderar 365-appar som Word, Excel, PowerPoint och OneDrive. Du kan tilldela specifika appar till apptypen och redigera konfigurationen för appinformationen.


### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>Konfliktlösning för tilldelning har ändrats för iOS Store-appar<!-- 1480316 -->
Slutanvändare kan uppleva att tillgängligheten för iOS Store-appar har ändrats. En app som har tilldelats till två grupper med en konflikt mellan **Nödvändig och Tillgänglig** och **Ej tillämpligt** ger för närvarande prioritet till **Nödvändig och Tillgänglig**. I och med ändringen ger en app med den här konflikten prioritet till **Ej tillämpligt** istället.

Ändringen löser problemet som uppstår när en app har tilldelats till flera grupper med olika avsikter.

Om du vill att din app ska vara tillgänglig i portalen för informationsanställda och företagsportalen innan lanseringen av versionen i november så har du två alternativ:

1. Ta bort tilldelningen **Ej tillämpligt** för din grupp.
2. Skapa en ny grupp som inte innehåller medlemmar med avsikten **Nödvändig och Tillgänglig** och tilldela gruppen som **Ej tillämpligt**.

Mer information finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

> [!Note]
> Efter utgivningen kommer du inte längre att kunna visa eller ändra apptilldelningar för hantering av mobilenheter (MDM) i den klassiska Intune-konsolen. Du kan dock använda Azure-konsolen eller Intune Graph API för att utföra dina apptilldelningar.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Hantera Android for Work-enheter oberoende av Android-enheter <!-- 1490731 -->
Intune stöder registrering av hantering för Android for Work-enheter oberoende av Android-plattformen. De här inställningarna hanteras under **Enhetsregistrering** > **Registreringsbegränsningar** > **Begränsningar för enhetstyper**. (De fanns tidigare **Enhetsregistrering** > **Android for Work-registrering** > **Registreringsinställningar för Android for Work**.)

Som standard är dina Android for Work-enhetsinställningar samma som dina inställningar för Android-enheter. Men när du har ändrat dina Android for Work-inställningar kommer det här inte längre att vara fallet.
 
Om du blockerar registrering av personligt ägda Android for Work-enheter så kan endast företagsägda Android-enheter att registrera Android for Work.

Tänk på följande när du konfigurerar nya inställningar:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Om du aldrig tidigare har publicerat Android for Work-registrering
Den nya Android for Work-plattformen blockeras av standardbegränsningarna för enhetstyper. När du har publicerat funktionen kan du tillåta enheter att registreras med Android for Work. För att göra detta ändrar du på standardvärdena eller skapar en ny begränsning för enhetstyp för att ersätta begränsningen för enhetstyp som är standard.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Om du har publicerat Android for Work-registrering
Om du har publicerat tidigare så beror din situation på de inställningar du väljer:

| Inställningen | Statusen för Android for Work under begränsningar för enhetstyper | Obs! |
| --- | --- | --- |
| **Hantera alla enheter som Android** | Blockerad | Alla Android-enheter måste registreras utan Android for Work. |
| **Hantera enheter som stöds som Android for Work** | Tillåts | Alla Android-enheter som har stöd för Android for Work måste registreras med Android for Work. |
| **Hantera endast enheter som stöds i de här grupperna som Android for Work för användare** | Blockerad | En separat princip för begränsningar för enhetstyper skapades för att åsidosätta standardinställningen. Den här principen definierar de grupper som du tidigare valde för att tillåta Android for Work-registrering. Användare i de valda grupperna fortsätter att kunna registrera sina Android for Work-enheter. Alla andra användare är begränsade från att registrera med Android for Work. |

I samtliga fall bevaras din avsedda regler. Ingen åtgärd krävs från din sida för att underhålla den globala begränsningen eller per grupp-begränsningen för Android for Work i din miljö.

De här ändringarna börjar publiceras med novemberuppdateringen, men det kan ta tid innan de appliceras på ditt konto. Du får ett bekräftelsemeddelande i Office 365-portalen när ändringarna är applicerade på ditt konto.


### <a name="configure-an-ios-app-pin----1586774---"></a>Konfigurera PIN-kod för en iOS-app <!-- 1586774 -->
Du kommer snart att kunna kräva en PIN-kod för iOS-appar. Du kan konfigurera kravet på PIN-kod och förfallodatum i dagar via Azure Portal. När kravet är gäller måste en användare konfigurera och använda en ny PIN-kod innan de får åtkomst till en iOS-app. Endast iOS-appar som har appskydd aktiverat med Intune App SDK har stöd för den här funktionen.

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Uppdatering av användarupplevelsen för appen Företagsportal för iOS <!--1412866-->

Vi kommer att släppa en större uppdatering av användarupplevelsen i appen Företagsportal för iOS. Uppdateringen medför en komplett visuell uppfräschning, vilket omfattar ett modernare utseende med bättre användbarhet och tillgänglighet. Alla befintliga funktioner i företagsportalen för iOS kommer att finnas kvar.

Vi har en förhandsversion av den uppdaterade appen Företagsportal för iOS som är tillgänglig via Apple TestFlight-programmet, som du kan använda och lämna feedback på. Registrera dig på https://aka.ms/intune_ios_cp_testflight för att få åtkomst till TestFlight. 

![marknadsföringsbilder för den nya ios-appen Företagsportal](./media/ios-cp-app-redesign-1801-teaser.png)


<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-webbplatser kan kräva appen Intune Managed Browser och ha stöd för enkel inloggning för Managed Browser (allmänt tillgänglig förhandsversion) <!-- 710595 -->   
Med Azure Active Directory (Azure AD) kan du begränsa åtkomst till webbplatser på mobila enheter till appen Intune Managed Browser. I Managed Browser förblir webbplatsdata säkra och separata från slutanvändarens personliga data. Dessutom stöder Managed Browser funktioner för enkel inloggning för webbplatser som stöds av Azure AD. När du loggar in på Managed Browser eller använder Managed Browser på en enhet med en annan app som hanteras av Intune, tillåts Managed Browser att få åtkomst till företagswebbplatser som skyddas av Azure AD utan att användaren måste ange sina autentiseringsuppgifter. Den här funktionen gäller för webbplatser som Outlook Web Access (OWA) och SharePoint Online, samt andra företags webbplatser som resurser i intranätet som nås via Azure App Proxy.


<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Stöd för uppgraderingsprincip i Windows 10-utgåvan <!-- 903672(archived), 1119689 -->  
Du kommer att kunna skapa en uppgraderingsprincip för Windows 10-utgåvan som uppgraderar Windows 10-enheter till Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education och Windows 10 Professional Education N. Mer information om Windows 10-uppgraderingar finns i [Så här konfigurerar du Windows 10-uppgraderingar](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->


### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Appskydd i Intune och Citrix MDX-utvecklingsverktyg <!-- 709185 -->
Du kan hantera enheter och appar med en kombination av Citrix XenMobile MDX och Microsoft Intune. Det gör det möjligt att hantera appar med Intunes appskyddsprincip samtidigt som du använder Citrix mVPN-teknik.

Du kan hitta ett kodcentrallager som innehåller Intune Apphanteringsverktyg och Intune App SDK för iOS och Android, som integreras med Citrix MDX mVPN-teknik.




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Omdirigera macOS-användare till vår nya företagsportalapp <!--1380728-->   
När en slutanvändare loggar in på företagsportalens webbplats för att registrera sin macOS-enhet dirigeras de för att ladda ned den nya företagsportalappen för macOS och på så sätt slutföra processen. Det inträffar för macOS-enheter som använder OS X El Capitan 10.11 eller senare. 



<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Intune Managed Browser har stöd för iOS och Android <!-- 1374196 -->
Från och med oktober 2017 stöder Intune Managed Browser-appen på Android-appen endast enheter som körs på Android 4.4 och senare. Intune Managed Browser-appen på iOS har endast stöd för enheter som körs på iOS 9.0 eller senare. Tidigare versioner av Android och iOS kommer att kunna fortsätta att använda Managed Browser, men kommer inte att kunna installera nya versioner av appen och kanske inte använda alla funktioner. Vi rekommenderar att du uppdaterar de här enheterna till en version av operativsystemet som stöds.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Förbättrat felmeddelande när en användare når det högsta antalet enheter som tillåts för registrering <!-- 1270370 -->
I stället för ett allmänt felmeddelande ser slutanvändare med Android-enheter ett vänligt felmeddelande med en åtgärd: ”You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin.” (Du har registrerat det högsta antalet enheter som IT-administratören tillåter. Ta bort en registrerad enhet eller be IT-administratören om hjälp.)




## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.




### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).
