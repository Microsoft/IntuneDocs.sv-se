---
title: "Tidig utgåva"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 973408b292261b86f0a49bfaf4c786d6a6dacf28
ms.sourcegitcommit: b8d3f8da6d8c2bd5d6140d538193a02d5875aefb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2017
---
# <a name="the-early-edition-for-microsoft-intune---october-2017"></a>Den tidiga utgåvan för Microsoft Intune – Oktober 2017

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

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-webbplatser kan kräva appen Intune Managed Browser och ha stöd för enkel inloggning för Managed Browser (allmänt tillgänglig förhandsversion) <!-- 710595 -->   
Med Azure Active Directory (Azure AD) kan du begränsa åtkomst till webbplatser på mobila enheter till appen Intune Managed Browser. I Managed Browser förblir webbplatsdata säkra och separata från slutanvändarens personliga data. Dessutom stöder Managed Browser funktioner för enkel inloggning för webbplatser som stöds av Azure AD. När du loggar in på Managed Browser eller använder Managed Browser på en enhet med en annan app som hanteras av Intune, tillåts Managed Browser att få åtkomst till företagswebbplatser som skyddas av Azure AD utan att användaren måste ange sina autentiseringsuppgifter. Den här funktionen gäller för webbplatser som Outlook Web Access (OWA) och SharePoint Online, samt andra företags webbplatser som resurser i intranätet som nås via Azure App Proxy.

### <a name="troubleshoot-enrollment-issues------746324----"></a>Felsöka problem med registreringen  <!--- 746324 --->  
Felsökningsarbetsytan visar problem med användarregistreringen. Information om problemet och förslagna lösningar kan hjälpa administratörer och medarbetare på supportavdelningen att felsöka problem. Vissa problem med registreringen inte fångas upp, och vissa fel kanske inte har några reparationsförslag.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Administratörer kan nu konfigurera brandväggsinställningar på en enhet med en profil för konfiguration av enheter <!-- 951708 -->   
Administratörer kan aktivera brandvägg för enheter och konfigurera olika protokoll för domän-, privata och offentliga nätverk.  Brandväggsinställningarna finns i profilen för slutpunktsskydd.

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard skyddar enheter mot ej betrodda webbplatser enligt organisationens definition <!-- 958257 -->   
Administratörer kan definiera platser som ”betrodda” eller ”företagsdata” med hjälp av Windows Information Protection-arbetsflödet eller den nya profilen "Nätverksgräns" under enhetskonfigurationer. Webbplatser som inte är angivna i en 64-bitars Windows 10-enhets betrodda nätverk och som öppnas med Microsoft Edge öppnas istället i en webbläsare i en virtuell Hyper-V-dator.

Application Guard finns i profilerna för enhetskonfiguration i profilen ”Endpoint protection”. Därifrån kan administratörer konfigurera interaktion mellan den virtualiserade webbläsaren och värddatorn, ej betrodda och betrodda webbplatser och lagra data som genererats i den virtualiserade webbläsaren. Om du vill använda Application Guard på en enhet måste du först konfigurera en nätverksgräns. Det är viktigt att endast definiera en nätverksgräns för en enhet.  

### <a name="windows-defender-application-guard-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows Defender Application Guard på Windows 10 Enterprise tillhandahåller ett läge för att enbart lita på godkända appar <!-- 1031096 -->    
Tusentals nya skadliga filer skapas varje dag, och användningen av signaturbaserat antivirusskydd för att bekämpa skadlig programvara kanske inte längre ger ett tillräckligt försvar mot nya attacker. Om du använder Windows Defender Application Guard på Windows 10 Enterprise kan du ändra enhetskonfiguration från ett läge där appar är betrodda och annars blockeras av en antivirus- eller en annan säkerhetslösning till ett läge där operativsystemet enbart litar på appar som företaget har godkänt. Du tilldelar förtroende till appar i Windows Defender Application Guard.

Med Intune kan du konfigurera principer för programkontroll i läget för ”endast granskning” eller i tvingande läge. Appar blockeras inte i läget för ”endast granskning”. Läget för ”endast granskning” loggar alla händelser i lokala klientloggar. Du kan också konfigurera om enbart Windows-komponenter och Windows Store-appar ska tillåtas att köras eller om ytterligare appar med gott rykte enligt Intelligent Security Graphs definition.

### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Ny registreringsstatussida för Windows 10-registreringar <!--1063201-->    
Nu kan du konfigurera en hälsning som visas när dina användare registrerar Windows 10-enheter. Använd **registreringsstatusskärmen** för att konfigurera ett anpassat meddelande och en hyperlänk som ska visas för dina slutanvändare när de registrerar sina Windows 10-enheter.  **Registreringsstatusskärmen** ger också slutanvändarna en översikt över förloppet för policyinställningar som används för deras enhet.  

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Window Defender Exploit Guard är en ny uppsättning intrångsförebyggande funktioner för Windows 10 <!-- 1063615 -->   
Window Defender Exploit Guard innehåller anpassade regler för att minska sårbarheter i program, förhindra makro- och skripthot, automatiskt blockera nätverksanslutningar till IP-adresser med dåligt rykte och kan skydda data mot utpressningstrojaner och okända hot. Windows Defender Exploit Guard består av följande komponenter:

- **Attack Surface Reduction (ASR)** tillhandahåller regler som tillåter dig att förhindra hot via makron, skript och e-post.
- **Reglerad mappåtkomst** blockerar automatiskt åtkomst till innehåll i skyddade mappar.
- **Nätverksfilter** blockerar utgående anslutning från valfri app för IP/domän med dåligt rykte
- **Sårbarhetsskydd** erbjuder begränsningar för minne, kontrollflöde och principer som kan användas för att skydda ett program mot sårbarheter.

### <a name="app-conditional-launch-support----1193313---"></a>Stöd för appvillkorlig start <!-- 1193313 -->
IT-administratörer kan nu ange ett krav via Azure-administrationsportalen på att framtvinga ett lösenord i stället för en numerisk PIN-kod via mobilapphantering (MAM) när programmet startas. Om det har konfigurerats behöver användaren ställa in och använda ett lösenord när han/hon uppmanas att göra det innan han/hon får åtkomst till MAM-integrerade program. Ett lösenord definieras som en numerisk PIN-kod med minst ett specialtecken eller en gemen/versal. Den här versionen av Intune kommer att aktivera den här funktionen **enbart på iOS**. Intune stöder lösenord på liknande sätt som numeriska PIN-koder. En minsta längd krävs och upprepning av tecken och sekvenser tillåts. Den här funktionen kräver medverkan av program (dvs. WXP, Outlook, Managed Browser, Yammer) för att integrera Intune APP SDK med koden för funktionen för att lösenordsinställningarna ska framtvingas i berörda program.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>App-versionsnumret för verksamhetsspecifika rapporter för installationsstatus för enhet <!-- 1233999 -->  
Rapporten för installationsstatus för enhet visar appversionsnumret för verksamhetsspecifika appar för iOS och Android. Du kan använda den här informationen för att felsöka dina appar och hitta enheter som kör gamla appversioner.

### <a name="co-management-for-windows-10-devices-----124445---"></a>Samhantering för Windows 10-enheter  <!-- 124445 -->
Samhantering är en lösning som erbjuder en brygga från traditionell till modern hantering, och det ger dig en sökväg för att göra övergången stegvis. I grund och botten är samhantering en lösning där Windows 10-enheter samtidigt hanteras av Configuration Manager och Microsoft Intune, som är anslutna till Active Directory (AD) och Azure Active Directory (Azure AD).  Den här konfigurationen ger dig en sökväg för att modernisera med tiden i den takt som passar din organisation om du inte kan flytta allt på samma gång.  

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Ange åtkomst för appar med den lägsta Android-säkerhetskorrigeringen på enheten<!-- 1278463 -->   
En administratör kommer att kunna definiera den lägsta Android-säkerhetskorrigering som måste vara installerad på enheten för att få åtkomst till ett hanterat program under ett hanterat konto.

> [!Note]  
> Den här funktionen begränsar endast säkerhetsuppdateringar som ges ut av Google på Android 6.0+-enheter.

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Inställningar för enhetsbegränsningar för Windows 10      <!-- 1308850 -->
-    Meddelandefunktion (endast mobil) – inaktivera testning eller MMS-meddelanden
-    Lösenord – inställningar för att aktivera FIPS och användning av sekundära Windows Hello-enheter för autentisering 
-    Skärm – inställningar för att slå på eller stänga av GDI-skalning för äldre appar


### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Begränsningar för fullskärmsläge för Windows 10-enheter <!-- 1308872 -->   
Du kommer att kunna begränsa användare av Windows 10-enheter till helskärmsläge, vilket begränsar användarna till en uppsättning fördefinierade appar.  Det gör du genom att skapa en begränsningsprofil för Windows 10-enheter och ange inställningar för helskärmsläge.

Helskärmsläge stöder två lägen: **en enda app** (gör att användaren endast kan köra en enda app) eller **flerappsläge** (tillåter åtkomst till en uppsättning appar).  Du definierar användarkontot och enhetens namn, vilket avgör vilka appar som stöds).  Inloggade användare är begränsade till definierade appar.  Mer information finns i [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (Begränsad CSP-åtkomst). 

Krav för helskärmsläge:

- Intune måste vara MDM-författare.
- Apparna måste redan vara installerade på målenheten.
- Enheten måste vara [rätt etablerad](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Ny profil för enhetskonfiguration för att skapa nätverksgränser<!-- 1311967 -->   
Vi har skapat en profil för enhetskonfiguration som heter **Nätverksgräns** som finns bland dina övriga enhetskonfigurationsprofiler. Använd den här profilen till att definiera onlineresurser som du anser är företagets och betrodda. Du måste definiera en nätverksgräns för en enhet *innan* funktioner som Windows Defender Application Guard och Windows informationsskydd kan användas på enheten. Det är viktigt att endast definiera en nätverksgräns för varje enhet.

Du kan definiera företagets molnresurser, IP-adressintervall och interna proxyservrar som du anser är betrodda. När en nätverksgräns är definierad kan den användas av andra funktioner som Windows Defender Application Guard och Windows informationsskydd.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Två ytterligare inställningar för Windows Defender Antivirus <!-- 1338409 -->  
**Filblockeringsnivå**

| | |
|---|---|
| Inte konfigurerat | **Ej konfigurerad** använder standardnivån för Windows Defender Antivirus-blockering och ger ett starkt skydd utan att öka risken för att upptäcka legitima filer. |
| Hög | **Hög** tillämpar en hög skyddsnivå.
| Hög +  | **Hög +** erbjuder Hög-nivån med extra skyddsåtgärder som kan påverka klientprestanda.
| Nolltolerans  | **Nolltolerans** blockerar alla okända körbara filer. |

Inställningen **Hög** kan orsaka att vissa legitima filer upptäcks, men det är osannolikt.
Vi rekommenderar att du ställer in filblockeringsnivån på standardläget **Ej konfigurerad**.

**Tidsgränstillägg för filgenomsökning av molnet**  

| | |
|--|--|
| Antal sekunder (0–50) | Ange den längsta tid som Windows Defender Antivirus ska blockera en fil under väntan på ett resultat från molnet. Standardvärdet är 10 sekunder: ytterligare tid som anges här (upp till 50 sekunder) läggs på för de 10 sekunderna. I de flesta fall går genomsökningen mycket snabbare än maxvärdet. En utökning av tiden gör att molnet kan undersöka misstänkta filer noggrant. Vi rekommenderar att du aktiverar den här inställningen och anger minst 20 ytterligare sekunder. |


### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Stöd för Symantec Cloud Certification Authority (CA)  <!-- 1333638 -->    
Intune stöder nu Symantec Cloud CA, som tillåter att Intune Certificate Connector utfärdar PKCS-certifikat från Symantec Cloud CA till hanterade Intune-enheter. Om du redan använder Intune Certificate Connector med Microsoft Certification Authority (CA) kan du utnyttja den befintliga Intune Certificate Connector-konfigurationen för att lägga till Symantec CA-stöd.



### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Citrix VPN tillagt för Windows 10-enheter <!-- 1512457 -->  
Kunden kommer att kunna konfigurera Citrix VPN för sina Windows 10-enheter. Du kan välja Citrix VPN i listan *Välj en anslutningstyp* på bladet **Bas-VPN** när du konfigurerar en VPN för Windows 10 och senare.

> [!Note]
> Det fanns Citrix-konfiguration för iOS och Android.





<!-- the following are present prior to 1710 -->

### <a name="google-play-protect-support-on-android----908720----"></a>Stöd för Google Play Protect på Android <!-- 908720  -->  
Med versionen Android Oreo introducerar Google en uppsättning säkerhetsfunktioner med namnet Google Play Protect, där användare och organisationer kan köra skyddade appar och Android-bilder. Intune stöder Google Play Protect-funktionerna, inklusive SafetyNets fjärrattestering.  Administratörer kan ange efterlevnadsprincipkrav som kräver att Google Play Protect är konfigurerat och felfritt. Inställningen **SafetyNets enhetsattestering** kräver att enheten ansluter med en Google-tjänst för att kontrollera att enheten är felfri och inte har komprometterats. Administratörer kan också ange en konfigurationsprofilinställning för Android for Work som kräver att installerade program verifieras av Google Play-tjänsterna.  Villkorlig åtkomst kan blockera användare från att komma åt företagets resurser om en enhet inte är kompatibel med Google Play Protect-kraven. 


### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Stöd för uppgraderingsprincip i Windows 10-utgåvan <!-- 903672(archived), 1119689 -->  
Du kommer att kunna skapa en uppgraderingsprincip för Windows 10-utgåvan som uppgraderar Windows 10-enheter till Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education och Windows 10 Professional Education N. Mer information om Windows 10-uppgraderingar finns i [Så här konfigurerar du Windows 10-uppgraderingar](edition-upgrade-configure-windows-10.md).





<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--846515---"></a>Åtgärder vid inkompatibilitet <!--730266  846515 -->     
*Åtgärder vid inkompatibilitet* är en ny funktion för efterlevnadsprinciper som gör det möjligt att vidta åtgärder för enheter som inte är kompatibla. Du kan ange en eller flera åtgärder och ange den tidsperiod då dessa åtgärder måste äga rum. Du kan till exempel meddela användare med inkompatibla enheter via e-post direkt efter att enheterna har blivit inkompatibla, eller så kan du blockera inkompatibla enheter från att få åtkomst till företagsresurser efter en respitperiod på tre dagar via villkorsstyrd åtkomst.

### <a name="android-for-work-support-for-lookout----1087312---"></a>Android for Work-stöd för Lookout <!-- 1087312 -->   
Intune-anslutningsprogrammet med Lookout stöder Android for Work-enheter när du använder Lookout for Work-appen. Du kan distribuera Lookout-appen innanför eller utanför behållaren.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Appskydd i Intune och Citrix MDX-utvecklingsverktyg <!-- 709185 -->
Du kan hantera enheter och appar med en kombination av Citrix XenMobile MDX och Microsoft Intune. Det gör det möjligt att hantera appar med Intunes appskyddsprincip samtidigt som du använder Citrix mVPN-teknik.

Du kan hitta ett kodcentrallager som innehåller Intune Apphanteringsverktyg och Intune App SDK för iOS och Android, som integreras med Citrix MDX mVPN-teknik.

#### <a name="how-integration-with-intune-works"></a>Så här fungerar integrering med Intune
Risken bedöms utifrån telemetri som samlas in från enheter som kör Zimperium. Du kan konfigurera EMS-principer för villkorlig åtkomst baserat på Zimperiums riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera icke-kompatibla enheter för företagets resurser baserat på de hot som har identifierats.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram <!-- 676614 -->   
Du kan ha fler roller för klientåtkomstservrar (CAS) för lokala Exchange-anslutningsprogram. Om de viktigaste klientåtkomstservrarna misslyckas till exempel, så tar Exchange-anslutningsprogrammet emot en fråga för att gå över till andra klientåtkomstservrar. Den här funktionen ser till att tjänsten inte avbryts.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Hanteringspaket för Exchange-anslutningsprogram i System Center Operations Manager <!-- 885457 -->   
Med System Center Operations Manager-hanteringspaketet för Exchange-anslutningsprogrammet kommer du att kunna tolka Exchange-anslutningsloggarna. Det här hanteringspaketet ger dig flera olika sätt att övervaka Intune när du behöver felsöka problem.


## <a name="intune-apps"></a>Intune-appar


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Omdirigera macOS-användare till vår nya företagsportalapp <!--1380728-->   
När en slutanvändare loggar in på företagsportalens webbplats för att registrera sin macOS-enhet dirigeras de för att ladda ned den nya företagsportalappen för macOS och på så sätt slutföra processen. Det inträffar för macOS-enheter som använder OS X El Capitan 10.11 eller senare. 

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Stöd för certifikatbaserad autentisering på företagsportalen för iOS <!--1029830-->
Vi har lagt till stöd för certifikatbaserad autentisering (CBA) i företagsportalappen för iOS. Användare med CBA anger sitt användarnamn och trycker på länken ”Signera med ett digitalt certifikat”. CBA stöds redan på företagsportalappar för Android och Windows. Du kan läsa mer på sidan [Logga in på företagsportal-appen](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Program som är tillgängliga med eller utan registrering kan nu installeras utan att först uppmanas till registrering. <!-- 1334712 -->
Företagsprogram som har gjorts tillgängliga med eller utan registreringen i Androids företagsportalapp kan installeras utan någon uppmaning att registrera.


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Intune Managed Browser har stöd för iOS och Android <!-- 1374196 -->
Från och med oktober 2017 stöder Intune Managed Browser-appen på Android-appen endast enheter som körs på Android 4.4 och senare. Intune Managed Browser-appen på iOS har endast stöd för enheter som körs på iOS 9.0 eller senare. Tidigare versioner av Android och iOS kommer att kunna fortsätta att använda Managed Browser, men kommer inte att kunna installera nya versioner av appen och kanske inte använda alla funktioner. Vi rekommenderar att du uppdaterar de här enheterna till en version av operativsystemet som stöds.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Förbättrat felmeddelande när en användare når det högsta antalet enheter som tillåts för registrering <!-- 1270370 -->
I stället för ett allmänt felmeddelande ser slutanvändarna ett vänligt felmeddelande med en åtgärd: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin.” (Du har registrerat det högsta antalet enheter som IT-administratören tillåter. Ta bort en registrerad enhet eller be IT-administratören om hjälp.)




## <a name="notices"></a>Meddelanden

### <a name="device-and-app-management-integration----677972---"></a>Integrering av enhets- och apphantering <!-- 677972 -->   
Nu när Intunes hantering av mobila enheter (MDM) och hantering av mobilprogram (MAM) båda är åtkomliga från Azure-portalen har Intune börjat integrera IT-adminstratörsupplevelsen kring program- och enhetshantering. De här ändringarna är avsedda att förenkla enhets- och apphanteringen.

Läs mer om ändringarna i MDM och MAM som presenteras i [Intune-supportteamets blogg](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).




### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).
