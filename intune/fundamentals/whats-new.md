---
title: Nyheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Ta reda på vad som är nytt i Intune Azure-portalen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2bb9d921f30e343b309be60438f5318d7c66518
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692266"
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune

Läs mer om varje veckas nyheter i Microsoft Intune. Du kan också hitta [viktiga meddelanden](#notices), [tidigare versioner](whats-new-archive.md) och information om [hur uppdateringar av Intune-tjänsten släpps](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> Varje [månadsuppdatering](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) kan ta upp till tre dagar att distribuera och sker i följande ordning:
>
> - Dag 1: Asien och stillahavsområdet
> - Dag 2: Europa, Mellanöstern och Afrika
> - Dag 3: Nordamerika
>
> Vissa funktioner kan distribueras över flera veckor och kanske inte är tillgängliga för alla kunder den första veckan.
>
> Titta närmare på sidan [Under utveckling ](in-development.md) för en lista över kommande funktioner i en version.

**RSS-feed**: Håll dig informerad när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>Veckan som börjar den 6 januari 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>S/MIME-stöd för Microsoft Outlook för iOS<!-- 2669398 -->
Intune stöder leverans av S/MIME-signering och -krypteringscertifikat som kan användas med Outlook för iOS på iOS-enheter. Mer information finns i avsnittet om [känslighetsetiketter och skydd i Outlook för iOS och Android](https://aka.ms/omsmime).

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>Veckan som börjar med 30 december 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Hämta personlig återställningsnyckel från MEM-krypterade macOS-enheter<!-- 4851745 -->
Slutanvändarna kan hämta sin personliga återställningsnyckel (FileVault Key) med hjälp av iOS-företagsportalappen. Den enhet som har den personliga återställningsnyckeln måste registreras med Intune och krypteras med FileVault via Intune. Med hjälp av iOS-företagsportalappen kan en slutanvändare hämta sin personliga återställningsnyckel på sin krypterade macOS-enhet genom att klicka på **Hämta återställningsnyckel**. Du kan också hämta återställningsnyckeln från Intune genom att välja **Enheter** > *den krypterade och registrerade macOS-enheten* > **Hämta återställningsnyckel**. Mer information om FileVault finns i [FileVault-kryptering för macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

#### <a name="ios-user-licensed-vpp-apps---5619268---"></a>iOS-användarlicenserade VPP-appar<!-- 5619268 -->
För användarregistrerade iOS-enheter visas inte längre distribuerade enhetslicenserade VPP-appar som tillgängliga för slutanvändare. Slutanvändare kommer dock fortfarande att se alla användarlicensierade VPP-appar inom företagsportalen. Mer information om VPP-appar finns i [Så här hanterar du iOS- och macOS-appar som köpts genom ett Apples volymköpsprogram med Microsoft Intune](~/apps/vpp-apps-ios.md).

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>Veckan som börjar med 23 december 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>Meddelande – Windows 10 1703 (RS2) kommer att tas bort från supporten <!-- 5026679 -->
Från och med 9 oktober 2018 togs Windows 10 1703 (RS2) bort från Microsofts plattformssupport for Home-, Pro- och Pro for Workstations-versionerna. För Windows 10 Enterprise-och Education-versionerna togs Windows 10 1703 (RS2) bort från plattformssupporten den 8 oktober 2019. Från den 26 december 2019 kommer vi att uppdatera den lägsta versionen av Windows Företagsportal-programmet till Windows 10 1709 (RS3). Datorer som kör tidigare versioner än 1709 kommer inte längre att ta emot uppdaterade versioner för programmet från Microsoft Store. Vi har tidigare informerat om den här ändringen till kunder som hanterar äldre versioner av Windows 10 via meddelandecentret. Mer information finns i [faktabladet om Windows livscykel](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>Veckan som börjar med 16 december 2019

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Uppdateringar till administrativa mallar för Windows 10-enheter <!-- 5941568 -->

Du kan använda ADMX-mallar i Microsoft Intune för att kontrollera och hantera inställningar för Microsoft Edge, Office och Windows. Administrativa mallar i Intune har gjort följande uppdateringar av principinställningen:

- Stöd har lagts till för Microsoft Edge-versionerna 78 och 79.
- Innehåller 2019 ADMX-filerna från den 11 november i [Administrativa mallfiler (ADMX/ADML) och Office-anpassnings verktyg för Office 365 ProPlus, Office 2019 och Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

Mer information om ADMX-mallar i Intune finns i [Använda Windows 10-mallar till att konfigurera grupprincipinställningar i Microsoft Intune](../configuration/administrative-templates-windows.md).

Gäller för:

- Windows 10 och senare

## <a name="week-of-december-9-2019-1912-service-release"></a>Veckan som börjar med den 9 december 2019 (1912 tjänstversion)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>Migrera till Microsoft Edge för scenarier med hanterade webbläsare<!-- 5173762 -->
Nu när vi närmar oss tillbakadragningen av Intune Managed Browser, har vi gjort ändringar i appskyddsprinciperna för att förenkla de steg som krävs för att flytta användare till Edge. Vi har uppdaterat alternativen i inställningen av appskyddsprincipen **Begränsa överföring av webbinnehåll till andra appar** till att vara något av följande:

- Alla appar
- Intune Managed Browser
- Microsoft Edge
- Ohanterad webbläsare 

När du väljer **Microsoft Edge** visas ett meddelande om villkorsstyrd åtkomst för användarna som informerar om att Microsoft Edge krävs för hanterad webbsökning. De uppmanas att ladda ned och logga in på Microsoft Edge med sina AAD-konton, om de inte redan har gjort det.  Detta motsvarar när du har riktat dina MAM-aktiverade appar med appens konfigurationsinställning `com.microsoft.intune.useEdge` inställd på **Sant**. Befintliga appskyddsprinciper som använde inställningen **Principhanterade webbläsare** har nu **Intune Managed Browser** valt och du upplever inte någon ändring av funktionerna. Det innebär att användarna kommer att se meddelanden om att använda Microsoft Edge om du har angett appkonfigurationsinställningen **useEdge** som **Sant**. Vi uppmuntrar alla kunder som använder scenarier med hanterad webbsökning till att uppdatera sina appskyddsprinciper med **Begränsa överföring av webbinnehåll till andra appar** att säkerställa att användarna ser rätt vägledning för övergången till Microsoft Edge, oavsett vilken app de öppnar länkarna från. 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>Konfigurera innehåll i appmeddelande för organisationskonton<!-- 2576686  -->
Med Intunes appskyddsprinciper (APP) på Android- och iOS-enheter kan du styra appens meddelandeinnehåll för organisationskonton. Du kan välja ett alternativ (Tillåt, Blockera organisationsdata eller Blockerade) för att ange hur meddelanden för organisationskonton ska visas för den valda appen. Den här funktionen kräver programstöd och är kanske inte tillgänglig för alla APP-aktiverade program. Outlook för iOS-version 4.15.0 (eller senare) och Outlook för Android 4.83.0 (eller senare) kommer att ha stöd för den här inställningen. Inställningen är tillgänglig i-konsolen, men funktionen börjar gälla efter 16 december 2019. Mer information om APP finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md).

#### <a name="microsoft-app-icons-update--4677605----"></a>Uppdatering av Microsofts appikoner<!--4677605  -->
Ikonerna som används för Microsoft-appar i appens målfönster för appskyddsprinciper och appkonfigurationsprinciper har uppdaterats.

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>Kräv användning av godkända tangentbord på Android<!--4761794  -->
Som en del av en appskyddsprincip kan du ange inställningen [**Godkända tangentbord**](../apps/app-protection-policy-settings-android.md#data-protection) för att hantera vilka Android-tangentbord som kan användas med hanterade Android-appar. När en användare öppnar den hanterade appen och inte redan använder tangentbord som är godkänt för den appen, uppmanas de att byta till ett av de godkända tangentbord som redan har installerats på enheten. Vid behov visas en länk för att ladda ner ett godkänt tangentbord från Google Play Store, som användaren kan installera och konfigurera. Om användarens aktiva tangentbord inte är ett av de godkända tangentborden kan användaren bara redigera textfält i en hanterad app.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>Uppdaterad enkel inloggning för appar och webbplatser på iOS-, iPadOS- och macOS-enheter<!-- 4999578  -->
Intune har lagt till fler SSO-inställningar för iOS-, iPadOS-och macOS-enheter. Nu kan du konfigurera och omdirigera SSO-apptillägg som skrivits av din organisation eller av din identitetsleverantör. Använd de här inställningarna för att konfigurera en smidig och enkel inloggning till appar och webbplatser som använder moderna autentiseringsmetoder, till exempel OAuth och SAML2. 

De nya inställningarna utökar de tidigare inställningarna för SSO-apptillägg och Apples inbyggda Kerberos-tillägg (**Enheter** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPad** eller **macOS** för plattformstyp > **Enhetsfunktioner** för profiltyp). 

Om du vill se en fullständig uppsättning inställningar för SSO-tillägg som du kan konfigurera går du till [SSO på iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) och [SSO på macOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Gäller för:

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352-wnready-----"></a>Vi har uppdaterat två enhetsbegränsningsinställningar för iOS-och iPad-enheter för att åtgärda deras beteende<!-- 5701352 WNReady   -->
För iOS-enheter kan du skapa enhetsbegränsningsprofiler som **tillåter trådlösa PKI-uppdateringar** och **blockerar USB-begränsat läge** (**Enheter** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPad** för plattform > **Enhetsbegränsningar** för profiltyp). Före den här versionen var användargränssnittsinställningar och beskrivningar för följande inställningar felaktiga och de har nu korrigerats. Från och med den här versionen är inställningsbeteendet följande:

**Blockera trådlösa PKI-uppdateringar**: **Blockera** hindrar användarna från att ta emot programuppdateringar om inte enheten är ansluten till en dator. **Inte konfigurerad** (standard): tillåter att en enhet tar emot programuppdateringar utan att vara ansluten till en dator.
- Tidigare kunde den här inställningen konfigureras som: **Tillåt**, vilket lät användarna ta emot programuppdateringar utan att ansluta sina enheter till en dator.
**Tillåt USB-tillbehör när enheten är låst**: **Tillåt** låter USB-tillbehör utbyta data med en enhet som har varit låst i över en timme. **Inte konfigurerad** (standard) uppdaterar inte USB-begränsat läge på enheten och USB-tillbehören kommer att blockeras från att överföra data från enheten om den är låst i mer än en timme.
- Tidigare kunde den här inställningen konfigureras som: **Blockera** för att inaktivera USB-begränsat läge på övervakade enheter.

Mer information om den inställning som du kan konfigurera finns i [Inställningar för iOS- och IPadOS-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-ios.md).

Den här funktionen gäller för:

- iOS/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Enhetskonfigurationsprofiler för fast nätverk för macOS-enheter<!-- 3508686  -->
   > [!NOTE]
   > Den här funktionen är försenad, men kommer snart att lanseras.

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>Blockera användare från att konfigurera autentiseringsuppgifter för certifikat i det hanterade nyckellagret på Android Enterprise-enhetsägarenheter<!-- 3311998 -->
På Android Enterprise-enhetsägarenheter kan du konfigurera en ny inställning som blockerar användare från att konfigurera sina certifikatsuppgifter i det hanterade nyckellagret (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetens ägare > Enhetsbegränsningar** för profiltypen > **Användare och konton**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="protected-wipe-action-now-available--51150000---"></a>Åtgärden för skyddad rensning är nu tillgänglig<!--51150000 -->
Nu har du möjlighet att använda åtgärden Rensa enhet för att utföra en skyddad rensning av en enhet. Skyddade rensningar är desamma som standardrensningar, förutom att de inte kan kringgås genom att stänga av enheten. En skyddad rensning försöker återställa enheten tills den har lyckats. I vissa konfigurationer kan den här åtgärden medföra att enheten inte kan startas om. Mer information finns i [Dra tillbaka eller rensa enheter](../remote-actions/devices-wipe.md).

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>Enhetens Ethernet MAC-adress har lagts till på enhetens översiktssida<!--5562275 -->
Nu kan du se en enhets Ethernet MAC-adress på sidan med enhetsinformation (**Enheter** > **Alla enheter** > Välj en enhet > **Översikt**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>Förbättrad upplevelse på en delad enhet när enhetbaserade principer för villkorlig åtkomst är aktiverade<!-- 1734096  -->
Vi har förbättrat upplevelsen på en delad enhet med flera användare som är riktade till enhetsbaserade villkorliga åtkomstprinciper genom att kontrollera den senaste utvärderingen av kompatibilitet för användaren när principen tillämpas. Mer information finns i följande översiktsartiklar:
- [Azure-översikt för villkorsstyrd åtkomst](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Översikt över enhetskompatibilitet för Intune](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>Använd PKCS-certifikatsprofiler för att etablera enheter med certifikat<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
Du kan nu använda PKCS-certifikatprofiler för att utfärda certifikat till *enheter* som kör Android for Work, iOS och Windows, när de är kopplade till profiler som till exempel Wi-Fi och VPN. Tidigare har de tre plattformarna endast haft stöd för användarbaserade certifikat, med enhetsbaserad support som är begränsad till macOS.

Om du vill använda ett enhetsbaserat certifikat medan du [skapar en PKCS-certifikatfil](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile) för de plattformar som stöds ska du välja **Inställningar**. Du ser nu inställningen för **Certifikattyp**, som stöder alternativen för Enhet eller Användare.



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="centralized-audit-logs--5603185-5697164---"></a>Centraliserade granskningsloggar<!--5603185, 5697164 -->
En ny centraliserad upplevelse av granskningsloggen samlar nu in granskningsloggar för alla kategorier på en sida. Du kan filtrera loggarna för att hämta de data du söker. Om du vill se granskningsloggarna går du till **Klientadministration** > **Granskningsloggar**. 

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>Information om omfångstaggar som ingår i granskningsloggens aktivitetsinformation<!--5763534 -->
Granskningsloggens aktivitetsinformation innehåller nu information om omfångstaggar (för Intune-objekt som stöder omfångstaggar). Mer information om gransknings loggar finns [Använda granskningsloggar för att spåra och övervaka händelser](monitor-audit-logs.md).


<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>Veckan som börjar med 2 december 2019

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>Ny licensiering av samhantering i Microsoft Endpoint Configuration Manager<!--5027281-->
Nu finns en ny licens där Configuration Manager-kunder med Software Assurance kan få Intune-samhantering för Windows 10-datorer utan att behöva köpa ytterligare en Intune-licens för samhantering. Kunderna behöver inte längre tilldela enskilda Intune/EMS-licenser till sina slutanvändare för samhantering av Windows 10.
- Enheter som hanteras i Configuration Manager och registreras för samhantering har nästan samma rättigheter som fristående MDM-hanterade datorer i Intune. När du har återställt dem kan du dock inte etablera dem igen med hjälp av Autopilot.
- Windows 10-enheter som har registrerats i Intune med hjälp av andra metoder kräver fullständiga Intune-licenser.
- Enheter på andra plattformar kräver fortfarande fullständiga Intune-licenser.

Mer information finns i [Licensvillkor](https://www.microsoft.com/en-us/Licensing/product-licensing/products).


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>Veckan den 18 november 2019 (1911 Service Release)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>Uppdaterat gränssnitt för selektiv rensning av appdata<!-- 4102028 -->
Gränssnittet för att selektivt rensa appdata i Intune har uppdaterats. Gränssnittsändringarna omfattar:
- En förenklad upplevelse med hjälp av ett format i guidestil som komprimerats till ett enskilt blad.
- En uppdatering av skapandeflödet så att tilldelningar inkluderas.
- En sammanfattningssida för alla saker som anges vid visning av egenskaper, innan en ny princip skapas eller när en egenskap redigeras. Vid redigering av egenskaper visar sammanfattningen dessutom bara en lista över objekt från kategorin med de egenskaper som redigeras.

Mer information finns i [Hur du rensar endast företagsdata från Intune-hanterade appar](~/apps/apps-selective-wipe.md).

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>Stöd för tangentbord från tredje part för iOS och iPad<!-- 4922950 -->
I mars 2019 informerade vi om att supporten för iOS-appens skyddsprincipinställning "tangentbord från tredje part" upphör. Funktionen återkommer till Intune med stöd för både iOS och iPad. Om du vill aktivera den här inställningen går du till fliken **Dataskydds** i en ny eller befintlig iOS/iPad-appskyddsprincip och hittar inställningen **Tredje parts tangentbord** under **Dataöverföring**.

Beteendet för den här inställningen skiljer sig något från föregående implementering. I appar med flera identiteter som använder SDK-version 12.0.16 och senare som omfattas av skyddsprinciper för appar där den här inställningen är konfigurerad som **Blockera** kan slutanvändare inte välja att använda tangentbord från tredje part i både organisationens och personliga konton. Appar som använder SDK-versioner 12.0.12 och tidigare kommer att fortsätta att följa det beteende som dokumenteras i blogginlägget [Känt problem: Tangentbord från tredje part blockeras inte i iOS för personliga konton](https://aka.ms/3rdparty_iOS_Intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Välj att användargrupper med macOS ska kräva JAMF-hantering<!-- 4061739  --> 
Du kan rikta in specifika grupper av användare vars [macOS-enheter hanteras av JAMF](../protect/conditional-access-integrate-jamf.md). På så sätt kan du använda JAMF-efterlevnadsintegreringen för en delmängd av macOS-enheter medan andra enheter hanteras av Intune. Om du redan använder JAMF-integreringen är omfattas alla användare av integreringen som standard.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>Nya Exchange ActiveSync-inställningar när du skapar en profil för e-postenhetskonfiguration på iOS-enheter<!-- 4892824   --> 
På iOS/iPad-enheter kan du konfigurera e-postanslutningen i en enhetskonfigurationsprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPad** för plattform > **E-post** för profiltyp). 

Det finns nya Exchange ActiveSync-inställningar, inklusive:
- **Exchange-data att synkronisera**: Välj vilka Exchange-tjänster som ska synkroniseras (eller blockera synkronisering) för kalender, kontakter, påminnelser, anteckningar och e-post.
- **Tillåt användare att ändra inställningar för synkronisering**: Tillåt (eller blockera) användare att ändra synkroniseringsinställningarna för dessa tjänster på sina enheter.  

Mer information om den här inställningen finns i [E-postprofilinställningar för iOS-enheter i Intune](../configuration/email-settings-ios.md). 

Gäller för:

- iOS 13.0 och senare
- iPadOS 13.0 och senare

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Hindra användare från att lägga till personliga Google-konton i fullständigt hanterade och dedikerade Android Enterprise-enheter<!-- 5353228   -->
På fullständigt hanterade och dedikerade Android Enterprise-enheter finns det en ny inställning som hindrar användare från att skapa personliga Google-konton (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetens ägare > Enhetsbegränsningar** för profiltypen > **Användar- och kontoinställningar** > **Personliga Google-konton**).

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:

- Fullständigt hanterade Android Enterprise-enheter
- Dedikerade Android Enterprise-enheter

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>Loggning på serversidan för Siri-kommandon tas bort från enhetsbegränsningsprofilen för iOS/iPadOS <!-- 5468501   -->
På iOS- och iPad-enheter tas inställningen **Loggning på serversidan för Siri-kommandon** bort från administratörskonsolen för Microsoft Endpoint Manager (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPadOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Inbyggda appar**). 

Den här inställningen har ingen påverkan på enheter. Om du vill ta bort inställningen från befintliga profiler öppnar du profilen, gör eventuella ändringar och sparar sedan profilen. Profilen uppdateras och inställningen tas bort från enheterna.

Om du vill se alla de inställningar som du kan konfigurera går du till [Inställningar för iOS- och IPadOS-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-ios.md).

Gäller för:

- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Funktionsuppdateringar för Windows 10 (offentlig förhandsversion)<!-- 2384877 -->
Nu kan du distribuera [Windows 10-funktionsuppdateringar](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) till Windows 10-enheter. Windows 10-funktionsuppdateringar är en ny programuppdateringsprincip som gör det möjligt att fastställa den version av Windows 10 som du vill installera på enheterna och sedan stanna på. Du kan använda den här nya principtypen tillsammans med dina befintliga Windows 10-uppdateringsringar.

Enheter som tar emot en princip för Windows 10-funktionsuppdateringar får den fastställda versionen av Windows installerad. Enheterna stannar sedan kvar på den fastställda versionen tills principen redigeras eller tas bort. Enheter med en senare version av Windows stannar kvar på sina respektive aktuella versioner. Enheter som stannar kvar på en fastställd version av Windows kan fortfarande installera kvalitets- och säkerhetsuppdateringar för den versionen via Windows 10-uppdateringsringarna.

Den här nya principtypen börjar distribueras till klientorganisationer nu i veckan. Om principen inte är tillgänglig för din klientorganisation än, kommer den att bli det inom kort.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>Lägga till och ändra nyckelinformation i PLIST-filer för macOS-program<!-- 4736278 -->
På macOS-enheter kan du nu skapa en enhetskonfigurationsprofil som laddar upp en fil med egenskapslistan (. plist) som är associerad med en app eller med enheten (**Enheter** > **Konfigurationsprofiler** > **Skapa profil** > **macOS** för plattform > **Inställningsfil** för profiltyp).

Endast vissa appar har stöd för hanterade inställningar och de här apparna kanske inte tillåter att du hanterar alla inställningar. Se till att ladda upp en fil med en egenskapslista som konfigurerar enhetskanalinställningarna och inte användarkanalinställningarna.

Mer information om den här funktionen finns i [Lägga till en fil med en egenskapslista i macOS-enheter med Microsoft Intune](../configuration/preference-file-settings-macos.md).

Gäller för:

- macOS-enheter som kör 10.7 och senare

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Redigera enhetsnamnvärde för Autopilot-enheter<!-- 2640074 -->
Du kan redigera enhetsnamnsvärdet för Azure AD-anslutna Autopilot-enheter.  Mer information finns i [Redigera attribut för Autopilot-enheter](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Redigera grupptaggvärde för Autopilot-enheter<!-- 4816775   -->
Du kan redigera grupptaggvärdet för Autopilot-enheter. Mer information finns i [Redigera attribut för Autopilot-enheter](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="updated-support-experience---5012398---"></a>Uppdaterad supportupplevelse<!-- 5012398 -->

Från och med idag distribueras en uppdaterad och strömlinjeformad konsolupplevelse för att få [hjälp och support](get-support.md). Om den nya upplevelsen inte är tillgänglig för dig än, kommer den att bli det inom kort.

Vi har förbättrat sökning och feedback i konsolen för vanliga problem, samt det arbetsflöde som du använder för att kontakta supporten. När du öppnar ett supportärende kan du se beräkningar i realtid för när du kan förvänta dig ett telefonsamtal eller e-postsvar. Premier och Unified Support-kunder kan dessutom ange en allvarlighetsgrad för problemet för att få hjälp snabbare.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>Förbättrad rapporterings upplevelse i Intune (offentlig förhandsversion) <!-- 3791418 -->
Intune har nu en förbättrad rapporteringsupplevelse, inklusive nya rapporttyper, bättre rapportorganisation, mer fokuserade vyer, förbättrade rapportfunktioner samt mer konsekventa och tidsrelevanta data. De nya rapporttyperna fokuserar på följande:
- **Drift** – tillhandahåller färska poster med fokus på driftproblem. 
- **Organisation** – innehåller en bred sammanfattning av det övergripande läget.
- **Historisk** – visar mönster och trender under en viss tidsperiod.
- **Specialist** – låter dig använda rådata för att skapa dina egna anpassade rapporter.

Den första uppsättningen nya rapporter fokuserar på enhetsefterlevnad. Mer information finns i [Blogg – Rapporteringsramverk i Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) och [Intune-rapporter](~/fundamentals/reports.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>Duplicera anpassade eller inbyggda roller <!-- 1081938   -->
Du kan nu kopiera de inbyggda och de anpassade rollerna. För mer information, se [Kopiera en roll](../fundamentals/create-custom-role.md#copy-a-role).

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>Nya behörigheter för skoladministratörsrollen <!-- 5621805  -->  
Två nya behörigheter, **Tilldela profil** och **Synkronisera enhet**, har lagts till i skoladministratörsrollen > **Behörigheter** > **Registreringsprogram**. Med behörigheten synkroniseraprofil kan gruppadministratörer synkronisera Windows Autopilot-enheter. Med behörigheten tilldela profil kan de ta bort användarinitierade Apple-registreringsprofiler. De har också behörighet att hantera tilldelningar av Autopilot-enheter och distributionsprofiler för Autopilot. En lista över alla behörigheter för skoladministratör/gruppadministratör finns i [Tilldela gruppadministratörer](https://docs.microsoft.com/intune-education/group-admin-delegate). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>Säkerhet

#### <a name="bitlocker-key-rotation---2564951----"></a>BitLocker-nyckel-ID<!-- 2564951  -->
Du kan använda en enhetsåtgärd i Intune för att [fjärrrotera återställningsnycklar för BitLocker](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) för hanterade enheter som kör Windows-version 1909 eller senare. För att kunna rotera återställningsnycklar måste enheterna konfigureras för att stödja rotation av återställningsnycklar.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>Uppdateringar av dedikerad enhetsregistrering för att stödja distribution av SCEP-enhetscertifikat <!-- 5198878  -->
Intune har nu stöd för distribution av SCEP-enhetscertifikat till dedikerade Android Enterprise-enheter för att möjliggöra certifikatbaserad åtkomst till Wi-Fi-profiler. Microsoft Intune appen måste finnas på enheten för att distributionen ska fungera. Därför har vi uppdaterat registreringsupplevelsen för dedikerade Android Enterprise-enheter. Nya registreringar är fortfarande samma (med QR, NFC, Zero-Touch eller Device Identifier) men har nu ett steg som kräver att användare installerar Intune-appen. På befintliga enheter kommer appen att installeras på löpande basis.

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>Granskningsloggar i Intune för samarbete mellan företag<!--5670211 -->
Samarbete mellan företag (B2B) gör att du på ett säkert sätt kan dela ditt företags program och tjänster med gästanvändare från en annan organisation, samtidigt som du behåller kontrollen över dina egna företagsdata. Intune stöder nu granskningsloggar för B2B-gästanvändare. Till exempel, när gästanvändare gör ändringar kommer Intune att kunna fånga dessa data via granskningsloggar. Mer information finns i [Vad är gästanvändaråtkomst i Azure Active Directory B2B?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>Veckan som börjar den 11 november 2019  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Förbättrad macOS-registrering i företagsportalen <!-- 5074349  -->  
Företagsportalen för macOS-registrering har en enklare registreringsprocess som stämmer bättre överens med företagsportalen för iOS-registrering. Enhetsanvändarna ser nu följande:  

* Ett mer elegant användargränssnitt.  
* En förbättrad checklista för registrering.  
* Tydligare instruktioner för hur man registrerar sina enheter.  
* Förbättrade felsökningsalternativ.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Webbappar som startas från Windows företagsportalapp<!-- 5030972 -->
Slutanvändare kan nu starta webbappar direkt från Windows företagsportalapp. Slutanvändare kan välja webbappen och sedan välja alternativet **Öppna i webbläsare**. Den publicerade webbadressen öppnas direkt i webbläsaren. Den här funktionen kommer att distribueras under nästa vecka. Mer information om hur du lägger till webbappar finns i [Lägga till webbappar i Microsoft Intune](~/apps/web-app.md).  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>Tilldelningstyp – ny kolumn i Företagsportal för Windows 10 <!-- 5459950  -->
Kolumnen Företagsportal > **Installerade appar** > **Tilldelningstyp** har bytt namn till **Krävs av din organisation**.  I denna kolumn visas värdet **Ja** eller **Nej** för att indikera om organisationen klassat en app som obligatorisk eller valfri. Förändringarna föranleddes av att många enhetsanvändare uttryckte förvirring kring apparnas natur. Dina användare hittar mer information om hur man installerar appar från företagsportalen i [Installera och dela appar på din enhet](/intune-user-help/install-apps-cpapp-windows). Mer information om hur du konfigurerar företagsportalappen för dina användare finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>Veckan som börjar den 4 november 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Microsoft Azure Government stöder säkerhetsbaslinjer<!-- 4062552 -->

Nu kan instanser av Intune som finns i *Microsoft Azure Government* använda [säkerhetsbaslinjer](../protect/security-baselines.md) för att skydda användare och enheter.

<!-- ########################## -->
## <a name="week-of-october-28-2019"></a>Veckan då den 28 oktober 2019 infaller

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Förbättrad utformning av checklistan i företagsportalappen för Android<!-- 5550857 -->  
Checklistan för inställningar i företagsportalappen för Android har uppdaterats med en enklare design och nya ikoner. Ändringarna ligger i linje med de senaste uppdateringarna som gjorts i företagsportalappen för iOS. En jämförelse av ändringar sida vid sida finns i [Nyheter i användargränssnittet för appen](whats-new-app-ui.md). De uppdaterade registreringsstegen finns i [Registrera med Android-arbetsprofilen](/intune-user-help/enroll-device-android-work-profile) och [Registrera din Android-enhet](/intune-user-help/enroll-device-android-company-portal).  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Win32-appar på enheter med Windows 10 i S-läge<!-- 3747604 --> 
Du kan installera och köra Win32-appar på hanterade enheter med Windows 10 i S-läge. Det gör du genom att skapa en eller flera tilläggsprinciper för S-läge med PowerShell-verktygen i Windows Defender-programreglering (WDAC). Signera tilläggsprinciperna med Device Guard-signeringsportalen och ladda sedan upp och distribuera principerna via Intune. I Intune hittar du den här funktionen genom att välja **Klientappar** > **Tilläggsprinciper för Windows 10 S**. Mer information finns i [Aktivera Win32-appar i S-lägesenheter](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Ange tillgänglighet för Win32-appen baserat på datum och tid<!-- 3510685 -->
Som administratör kan du konfigurera starttid och tidsgräns för en Win32-app som krävs. Vid starttiden börjar Intune-hanteringstillägget ladda ned och cachelagra appinnehållet. Appen installeras vid tiden för tidsgränsen. För tillgängliga appar anger starttiden när appen är synlig i företagsportalen. Mer information finns i [Intune Win32-apphantering](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Kräv omstart av enheten baserat på respitperioden efter installationen av Win32-appen<!-- 3136567 -->
Du kan kräva att en enhet måste startas om efter att en Win32-app har installerats. Mer information finns i [Win32-apphantering – Konfigurera information om appinstallationen](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details).

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Mörkt läge för iOS-företagsportalen<!-- 4911422 -->
Mörkt läge är tillgängligt för iOS-företagsportalen. Användarna kan ladda ned företagsappar, hantera sina enheter och få IT-support i valfritt färgschema baserat på enhetsinställningarna. iOS-företagsportalen matchar automatiskt slutanvändarens enhetsinställningar för mörkt eller ljust läge. Mer information finns i [Lansering av mörkt läge i Microsoft Intunes företagsportal för iOS](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453). Mer information om hur du IOS-företagsportalen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Obligatorisk lägsta appversion för Android-företagsportalen<!-- 2378776 -->
Genom att använda inställningen **Lägsta företagsportalversion** för en appskyddsprincip, kan du ange en specifik definierad minimiversion för företagsportalen som ska finnas på slutanvändarens enhet. Med den här inställningen för villkorlig start kan du använda **Blockera åtkomst**, **Rensa data** och **Varna** som möjliga åtgärder när värdet inte uppfylls. De möjliga formaten för det här värdet följer mönstret *[Major].[Minor]* , *[Major].[Minor].[Build]* , eller *[Major].[Minor].[Build].[Revision]* .

Om inställningen **Lägsta företagsportalversion** har konfigurerats, kommer det att påverka slutanvändare som hämtar version 5.0.4560.0 och eventuella framtida versioner av företagsportalen. Den här inställningen har ingen påverkan på användare som använder en version av företagsportalen som är äldre än den version som funktionen lanseras med. Slutanvändare som använder automatiska appuppdateringar kommer troligen inte att se några dialogrutor från den här funktionen, eftersom de sannolikt har den senaste företagsportalversionen. Den här inställningen gäller endast för Android med appskydd för registrerade och oregistrerade enheter. Mer information finns i [Inställningar för Android-appskyddsprinciper – Villkorlig start](~/apps/app-protection-policy-settings-android.md#conditional-launch).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Microsoft 365 Enhetshantering

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Introduktion till noden för slutpunktssäkerhet i Microsoft 365 Enhetshantering<!-- 5630102 -->

Noden **Slutpunktssäkerhet** finns nu allmänt tillgänglig i specialistarbetsytan för Microsoft 365 Enhetshantering på https://devicemanagement.microsoft.com, som grupperar funktionerna för att skydda slutpunkter som exempelvis:

- Säkerhetsbaslinjer:  En förkonfigurerad grupp med inställningar som hjälper dig att tillämpa kända inställningsgrupper och standardvärden som rekommenderas av Microsoft.

- Säkerhetsaktiviteter: Dra nytta av hot- och sårbarhetshanteringen i Microsoft Defender ATP och använd Intune till att åtgärda svagheter i slutpunkterna.

- Microsoft Defender ATP: Microsoft Defender Avancerat skydd är integrerat för att förhindra säkerhetsöverträdelser.

Inställningarna kommer fortsatt att vara tillgängliga från andra tillämpliga noder, till exempel enheter, och det aktuella konfigurerade tillståndet är detsamma oavsett var du öppnar eller aktiverar funktionerna.

Mer information om dessa förbättringar finns i [blogginlägget Kundframgång för Intune](https://aka.ms/Endpoint_security_node) på webbplatsen för Microsoft Tech Community.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune har stöd för iOS 11 och senare<!-- 4665324  -->

Intune-registreringen och företagsportalen har nu stöd för iOS-versionerna 11 och senare. Äldre versioner stöds inte.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge-baslinje (förhandsversion)<!--  3787164  -->

Vi har lagt till en förhandsversion med säkerhetsbaslinje för [Microsoft Edge-inställningar](../protect/security-baseline-settings-edge.md). 

<!-- ########################## -->
## <a name="week-of-october-21-2019-1910-service-release"></a>Veckan den 21 oktober 2019 (1910 Service Release)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Microsoft 365 Enhetshantering

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Förbättrad administrationsupplevelse i Microsoft 365 Enhetshantering<!-- 5551239 -->

En uppdaterad och förbättrad administrationsupplevelse är nu allmänt tillgänglig i specialistarbetsytan för Microsoft 365 Enhetshantering på [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com), inklusive:

- **Uppdaterad navigering**: Du hittar en förenklad navigering på hög nivå som logiskt grupperar funktioner.
- **Nya plattformsfilter**: Du kan välja en enda plattform som bara visar principer och appar för den valda plattformen på sidorna Enheter och Appar.
- **Ny startsida**: Se snabbt tjänstens hälsa, status för din klientorganisation, nyheter osv. på den nya startsidan.

Mer information om dessa förbättringar finns i [blogginlägget Enterprise Mobility + Security](https://go.microsoft.com/fwlink/?linkid=2109094) på webbplatsen för Microsoft Tech Community.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Lägga till Mobile Threat Defense-appar till oregistrerade enheter<!-- 3005337 -->
Du kan skapa en appskyddsprincip i Intune som kan blockera eller selektivt rensa användarnas företagsdata baserat på enhetens hälsa. Enhetens hälsotillstånd bestäms med hjälp av din valda MTD-lösning (Mobile Threat Defense). Den här funktionen finns i dag i Intune-registrerade enheter som en inställning för enhetsefterlevnad. Med den här nya funktionen utökar vi hotidentifieringen från en MTD-leverantör så att den nu även fungerar på oregistrerade enheter. På Android kräver funktionen att den senaste företagsportalen finns på enheten. På iOS är funktionen tillgänglig för användning när apparna integrerar den senaste Intune SDK:n (v 12.0.15+). Vi uppdaterar ämnet Nyheter när den första appen börjar använda den senaste Intune SDK:n. De återstående apparna blir tillgängliga löpande. Mer information finns i [Skapa en Mobile Threat Defense-appskyddsprincip med Intune](~/protect/mtd-app-protection-policy.md).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>Ny gränssnittsprofil för konfiguration av enhetens inbyggda programvara för enheter med Windows 10 och senare (offentlig förhandsversion)<!-- 2266073  -->

I Windows 10 och senare kan du skapa en enhetskonfigurationsprofil för att kontrollera inställningar och funktioner (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform). I den här uppdateringen finns en ny typ av gränssnittsprofil för konfiguration av enhetens inbyggda programvara som gör att Intune kan hantera UEFI-inställningar (BIOS).

Mer information om den här funktionen finns i avsnittet om att [använda DFCI-profiler på Windows-enheter i Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

Gäller för:

- Windows 10 RS5 (1809) och senare på inbyggd programvara som stöds

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Växla till att endast visa sidan Registreringsstatus på enheter som har etablerats med ett välkomstprogram<!--3959566-->
Du kan nu välja att endast visa sidan Registreringsstatus på enheter som har etablerats med välkomstprogrammet för Autopilot.

Om du vill se den nya växlingsfunktionen väljer du **Intune** > **Enhetsregistrering** > **Windows-registrering** > **sidan Registreringsstatus** > **Skapa profil** > **Inställningar** > **Visa bara sidan för enheter som har etablerats via välkomstprogrammet**.


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>Veckan då den 14 oktober 2019 infaller

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Tillgänglig Google Play-apprapportering för Android-arbetsprofiler<!-- 3041956   -->
För tillgängliga appinstallationer på Android Enterprise-enheter för arbetsprofil samt dedikerade och fullständigt hanterade enheter kan du visa appens installationsstatus samt den installerade versionen av hanterade Google Play-appar. Mer information finns i [Så här övervakar du appskyddsprinciper](~/apps/app-protection-policies-monitor.md), [Hantera Android-arbetsprofilenheter med Intune](~/enrollment/android-enterprise-overview.md) och [Hanterade Google Play-apptyper](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Microsoft Edge version 77 och senare för Windows 10 och macOS (offentlig förhandsversion)<!-- 3872025, 4678761  -->
Microsoft Edge version 77 och senare kommer att göras tillgänglig för distribution till datorer som kör Windows 10 och macOS. 

Den offentliga förhandsversionen erbjuder kanalerna **Dev** och **Beta** för Windows 10 och en **Beta-kanal** för macOS. Distributionen är bara på engelska (EN), men slutanvändarna kan ändra visningsspråket i webbläsaren under **Inställningar** > **Språk**. Microsoft Edge är en Win32-app som installeras i systemkontext och på samma arkitektur (x86-appen i x86-operativsystem och x64-appen i x64-operativsystem). Dessutom är automatiska uppdateringar av webbläsaren **På** som standard, och Microsoft Edge kan inte avinstalleras. Mer information finns i avsnittet om att [lägga till Microsoft Edge för Windows 10 till Microsoft Intune](~/apps/apps-windows-edge.md) och i [Microsoft Edge-dokumentationen](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>Uppdatering av användargränssnittet för appskydd och användargränssnittet för etablering av iOS-appar<!-- 4102027, 4102029   -->
Användargränssnittet för skapande och redigering av appskyddsprinciper samt etableringsprofiler för iOS-appar i Intune har uppdaterats. Gränssnittsändringarna omfattar:
- En förenklad upplevelse med hjälp av ett format i guidestil som komprimerats till ett enskilt blad. 
- En uppdatering av skapandeflödet så att tilldelningar inkluderas.
- En sammanfattningssida för alla saker som anges vid visning av egenskaper, innan en ny princip skapas eller när en egenskap redigeras. Vid redigering av egenskaper visar sammanfattningen dessutom bara en lista över objekt från kategorin med de egenskaper som redigeras.

Mer information finns i [Hur du skapar och tilldelar skyddsprinciper för appar](~/apps/app-protection-policies.md) och [Använd iOS-appetableringsprofiler](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Guidade Intune-scenarier<!-- 4850318, 4831296, 3610611  -->
Intune har nu guidade scenarier som hjälper dig att slutföra en specifik uppgift eller uppsättning med uppgifter i Intune. Ett guidat scenario är en anpassad serie med steg (arbetsflöde) som handlar om ett visst användningsfall från slutpunkt till slutpunkt. Vanliga scenarier definieras baserat på den roll som en administratör, användare eller enhet har i din organisation. Dessa arbetsflöden kräver vanligtvis en samling noggrant samordnade profiler, inställningar, program och säkerhetskontroller för att ge bästa möjliga användarupplevelse och säkerhet. Nya guidade scenarier omfattar:
- [Distribuera Microsoft Edge för mobil](~/fundamentals/guided-scenarios-edge.md)
- [Skydda Microsoft Office-mobilappar](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Molnhanterat modernt skrivbord](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

Mer information finns i [översikten av guidade Intune-scenarier](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>Ytterligare variabel för appkonfiguration är tillgänglig<!-- 4969237   -->
När du skapar en appkonfigurationsprincip kan du inkludera konfigurationsvariabeln `AAD Device ID` som en del av dina konfigurationsinställningar. Gå till Intune och välj **Klientappar** > **Appkonfigurationsprinciper** > **Lägg till**. Ange informationen om konfigurationsprincipen och välj **Konfigurationsinställningar** för att visa bladet **Konfigurationsinställningar**. Mer information finns i avsnittet om [appkonfigurationsprinciper för hanterade Android Enterprise-enheter – Använda Configuration Designer](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>Skapa grupper av hanteringsobjekt som kallas principuppsättningar<!-- 3762880  -->
Med principuppsättningar kan du skapa ett paket med referenser till redan befintliga hanteringsenheter som behöver identifieras, riktas och övervakas som en enda begreppsmässig enhet. Principuppsättningar ersätter inte befintliga begrepp eller objekt. Du kan fortsätta att tilldela enskilda objekt i Intune, och du kan referera till enskilda objekt som en del av en principuppsättning. Det innebär att alla ändringar av de enskilda objekten avspeglas i principuppsättningen.  I Intune väljer du **Principuppsättningar** > **Skapa** för att skapa en ny principuppsättning. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Uppdatering av användargränssnittet för skapande och redigering av Windows 10-uppdateringsringar<!-- 4099089         -->
Vi har uppdaterat gränssnittsupplevelsen för [skapande och redigering av Windows 10-uppdateringsringar](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) för Intune. Ändringar i användargränssnittet är följande:  
- Ett format i guidestil med en mall som är komprimerad till ett enda konsolblad så att du slipper mängden med blad när du konfigurerar uppdateringsringar.   
- Det ändrade arbetsflödet omfattar Tilldelningar före slutförandet av ringens första konfiguration.
- En sammanfattningssida där du kan granska alla konfigurationer som du har gjort innan du sparar och distribuerar en ny uppdateringsring. Vid redigering av en uppdateringsring visar sammanfattningen endast listan över objekt som har angetts i kategorin med egenskaper som du redigerade.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>Uppdatering av användargränssnittet för skapande och redigering av iOS-programuppdateringsprinciper<!-- 4099090       --> 
Vi har uppdaterat gränssnittsupplevelsen för [skapande](../protect/software-updates-ios.md#configure-the-policy) och [redigering](../protect/software-updates-ios.md#edit-a-policy) av iOS-programuppdateringsprinciper för Intune.  Ändringar i användargränssnittet är följande:  
- Ett format i guidestil med en mall som är komprimerad till ett enda konsolblad så att du slipper mängden med blad när du konfigurerar uppdateringsprinciper.   
- Det ändrade arbetsflödet omfattar Tilldelningar före slutförandet av principens första konfiguration.
- En sammanfattningssida där du kan granska alla konfigurationer som du har gjort innan du sparar och distribuerar en ny princip. Vid redigering av en princip visar sammanfattningen endast listan över objekt som har angetts i kategorin med egenskaper som du redigerade.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404--------"></a>Inställningarna för interaktiv omstart tas bort från Windows-uppdateringsringar<!--  4464404      -->
Som tidigare har meddelats har Intunes Windows 10-uppdateringsringar nu [stöd för inställningar för tidsgränser](../protect/windows-update-settings.md) och stöder inte längre *interaktiv omstart*. Inställningarna för *interaktiv omstart* är inte längre tillgängliga när du konfigurerar eller hanterar uppdateringsringar i Intune.  

Den här ändringen stämmer överens med nyliga [Windows Servicing-ändringar](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) och på enheter som kör Windows 10 1903 eller senare ersätter *tidsgränser* konfigurationer för *interaktiv omstart*.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Förhindra installation av appar från okända källor på Android Enterprise-arbetsprofilenheter<!-- 4760025   -->
På Android Enterprise-arbetsprofilenheter kan användarna aldrig installera appar från okända källor. I den här uppdateringen finns det en ny inställning – **Förhindra appinstallationer från okända källor i den personliga profilen**. Som standard förhindrar den här inställningen att användare läser in appar från okända källor till den personliga profilen på enheten.

Om du vill se den inställning som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:

- Android Enterprise-arbetsprofil

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Skapa en global HTTP-proxy på Android Enterprise-enhetsägarenheter<!-- 4816339   -->
På Android Enterprise-enheter kan du konfigurera en global HTTP-proxy som uppfyller organisationens webbläsarstandarder (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Enhetsägare > Enhetsbegränsningar** för profiltyp > **Anslutningar**). Efter konfigurationen använder all HTTP-trafik denna proxy.

Om du vill konfigurera den här funktionen och se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:

- Android Enterprise-enhetsägare

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Inställningen för automatisk anslutning tas bort från Wi-Fi-profiler på Android-enhetsadministratör och Android Enterprise<!-- 5021055   -->
På Android-enhetsadministratör och Android Enterprise-enheter kan du skapa en Wi-Fi-profil för att konfigurera olika inställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android-enhetsadministratör** eller **Android Enterprise** för plattform > **Wi-Fi** för profiltyp). I den här uppdateringen tas inställningen **Anslut automatiskt** bort eftersom den [inte stöds av Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Om du använder den här inställningen i en Wi-Fi-profil har du kanske märkt att **Anslut automatiskt** inte fungerar. Du behöver inte vidta några åtgärder, men tänk på att den här inställningen tas bort från användargränssnittet i Intune.

Om du vill se de aktuella inställningarna går du till [Wi-Fi-inställningar för Android](../configuration/wi-fi-settings-android.md) eller [Wi-Fi-inställningar för Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

Gäller för:

- Android-enhetsadministratör 
- Android enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>Nya enhetskonfigurationsinställningar för övervakade iOS- och iPadOS-enheter<!-- 5199328   -->
På iOS- och iPadOS-enheter kan du skapa en profil för att begränsa funktioner och inställningar på enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPadOS** för plattform > **Enhetsbegränsningar** för profiltyp). I den här uppdateringen finns det nya inställningar du kan styra: 
- Åtkomst till nätverksenheten i appen Filer  
- Åtkomst till USB-enheten i appen Filer 
- Wi-Fi är alltid aktiverat 

Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md) för att se de här inställningarna.

Gäller för:

- iOS 13.0 och senare
- iPadOS 13.0 och senare

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Ange vilka operativsystemversioner för Android-enheter som registreras via registrering med arbetsprofil eller enhetsadministratör<!-- 4350697   -->
Med hjälp av begränsningar för Intune-enhetstyp kan du använda enhetens OS-version för att ange vilka användarenheter som ska använda registrering med Android Enterprise-arbetsprofil eller registrering med Android-enhetsadministratör.  Mer information finns i [Konfigurera registreringsrestriktioner](../enrollment/enrollment-restrictions-set.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Nya begränsningar för namnbyte av Windows-enheter<!-- 3478938  -->
När du byter namn på en Windows-enhet måste du följa nya regler:
- 15 tecken eller mindre (måste vara mindre än eller lika med 63 byte exklusive avslutande NULL)
- Inte null eller en tom sträng
- Tillåten ASCII: Bokstäver (a–z, A–Z), siffror (0–9) och bindestreck
- Tillåten Unicode: tecken > = 0x80, måste vara en giltig UTF8, måste vara IDN-mappningsbara (det vill säga att RtlIdnToNameprepUnicode lyckas; se RFC 3492)
- Namn får inte enbart innehålla siffror
- Inga blanksteg i namnet
- Förbjudna tecken: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 Mer information finns i [Ändra namn på en enhet i Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>Ny Android-rapport på sidan med enhetsöversikt<!-- 4924364 -->
En ny rapport på sidan med enhetsöversikt visar hur många Android-enheter som har registrerats i varje enhetshanteringslösning. Det här diagrammet visar antal arbetsprofilenheter samt fullständigt hanterade, dedikerade och enhetsadministratörsregistrerade enheter. Om du vill se rapporten väljer du **Intune** > **Enheter** > **Översikt**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>PKCS-certifikat för macOS<!-- 1333650       -->
Nu kan du [använda PKCS-certifikat med macOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). Du kan välja PKCS-certifikatet som en profiltyp för macOS och distribuera användar- och enhetscertifikat som har [anpassade ämnesnamnfält och alternativa ämnesnamnfält](../protect/certficates-pfx-configure.md#subject-name-format).  

PKCS-certifikat för macOS har även stöd för en ny inställning, _Ge alla appar åtkomst_. Med den här inställningen kan du ge alla associerade appar åtkomst till den privata nyckeln för certifikatet.  Mer information om den här inställningen finns i Apple-dokumentationen på https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>Härledda autentiseringsuppgifter för etablering av mobila iOS-enheter med certifikat<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune stöder användning av [härledda autentiseringsuppgifter](../protect/derived-credentials.md) som autentiseringsmetod samt för S/MIME-signering och -kryptering för iOS-enheter. Härledda autentiseringsuppgifter är en implementering av standarden *National Institute of Standards and Technology (NIST) 800-157* för distribution av certifikat till enheter.  

Härledda autentiseringsuppgifter är beroende av att ett PIV-kort (Personal Identity Verification) eller ett CAC-kort (Common Access Card) används, till exempel ett smartkort. För att få en härledd autentiseringsuppgift för sin mobila enhet börjar användare i Företagsportal-appen och följer ett registreringsarbetsflöde som är unikt för den provider som du använder.  Gemensamt för alla providrar är kravet på användning av ett smartkort på en dator för autentisering till providern för den härledda autentiseringsuppgiften. Providern utfärdar sedan ett certifikat till den enhet som härleds från användarens smartkort.  

Intune stöder följande providrar för härledda autentiseringsuppgifter:
- DISA Purebred
- Entrust Datacard
- Intercede

Du använder härledda autentiseringsuppgifter som autentiseringsmetod för enhetskonfigurationsprofiler för VPN, Wi-Fi och e-post. Du kan även använda dem för appautentisering samt för S/MIME-signering och -kryptering.  

Mer information om standarden finns i [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) (Härledda PIV-autentiseringsuppgifter) på www.nccoe.nist.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Använd Graph API för att ange ett lokalt användarhuvudnamn som en variabel för SCEP-certifikat<!--  5437939        -->  
När du använder [Intune-Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) kan du ange onPremisesUserPrincipalName som en variabel för SAN (alternativt namn för certifikatmottagare) för SCEP-certifikat.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Veckan då den 23 september 2019 infaller

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>Användarregistrering i iOS i förhandsversion<!-- 4817900 -->
Lanseringen av Apples iOS 13.1 inkluderar användarregistrering, en ny form av lätt hantering av iOS-enheter. Den kan användas i stället för enhetsregistrering eller automatisk enhetsregistrering (tidigare Programmet för enhetsregistrering) för personliga enheter. Intunes förhandsversion har stöd för den här funktionen genom att låta dig göra följande:

- Målanvändarregistrering för användargrupper.
- Ge slutanvändarna möjlighet att välja mellan lättare användarregistrering eller starkare enhetsregistrering när de registrerar sina enheter.

Starting on 9/24/2019 with the release of iOS 13.1, we're in the process of rolling out these updates to all customers and expect to be completed by the end of next week.

Gäller för:

- iOS 13.1 och senare

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Intune-stöd för enheter med iPadOS och iOS 13.1<!--5439574-->
Intune har nu stöd för enheter med såväl iPadOS som iOS 13.1. Mer information finns i [det här blogginlägget](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019-1909-service-release"></a>Veckan den 16 september 2019 (1909 Service Release)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>Privata LOB-appar för Hanterat Google Play-konto<!-- 1464182  -->
Intune tillåter nu IT-administratörer att publicera privata Android LOB-appar till Hanterat Google Play-konto via en iframe inbäddad i Intune-konsolen.  Tidigare behövde IT-administratörer publicera LOB-appar direkt till Googles Play-publiceringskonsol, vilket krävde flera steg och tog lång tid. Med den här nya funktionen kan du enkelt publicera LOB-appar med en minimal uppsättning steg, utan att behöva lämna Intune-konsolen.  Administratörer behöver inte längre manuellt registrera sig som utvecklare hos Google och behöver inte längre betala Google-registreringsavgiften på 25 USD.  Alla Android Enterprise-hanteringsscenarier som använder Hanterat Google Play-konto kan dra nytta av den här funktionen (arbetsprofilenheter och dedikerade, fullständigt hanterade samt icke-registrerade enheter). I Intune väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **Hanterat Google Play-konto** i listan **Apptyp**. Mer information om Managed Google Play-appar finns i [Lägga till Managed Google Play-appar till Android Enterprise-enheter med Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Gränssnittet för Företagsportal i Windows<!-- 1473353, 3598357 -->
Företagsportal i Windows uppdateras. Du kommer att kunna använda flera filter på sidan Appar i Företagsportal i Windows. Sidan Enhetsinformation uppdateras också med ett förbättrat användargränssnitt. Vi håller på att lansera dessa uppdateringar för alla kunder och förväntar oss att blir klara i slutet av nästa vecka.

#### <a name="macos-support-for-web-apps---3174427---"></a>macOS-stöd för webbappar<!-- 3174427 -->
Webbappar, som gör att du kan lägga till en genväg till en URL på webben, kan installeras på Dock med hjälp av Företagsportal i macOS. Slutanvändare kan komma åt **installationsåtgärden** via appinformationssidan för en webbapp i Företagsportal i macOS. Mer information om apptypen **Webblänk** finns i [Lägga till appar i Microsoft Intune](../apps/apps-add.md) och [Lägga till webbappar i Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps---3173501----"></a>macOS-stöd för VPP-appar<!-- 3173501  -->
macOS-appar som köpts via Apple Business Manager visas i konsolen när Apple VPP-token synkroniseras i Intune. Du kan tilldela, återkalla och omtilldela enhets- och användarbaserade licenser för grupper med hjälp av Intune-konsolen. Med Microsoft Intune kan du hantera VPP-appar som köpts för användning i företaget genom att:

- Rapportera licensinformation från App Store.
- Spåra antalet använda licenser.
- Hjälpa dig att förhindra installation av fler exemplar av en app än du äger.

Mer information om Intune och VPP, finns i [Hantera volyminköpta appar och böcker med Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support---2871756----"></a>iframe-stöd för Hanterat Google Play-konto<!-- 2871756  -->
Intune har nu stöd för att lägga till och hantera webblänkar direkt i Intune-konsolen via iframe för Hanterat Google Play-konto.  Det här gör att IT-administratörer kan skicka en URL och ikonbild, och sedan distribuera dessa länkar till enheter precis som vanliga Android-appar. Alla Android Enterprise-hanteringsscenarier som använder Hanterat Google Play-konto kan dra nytta av den här funktionen (arbetsprofilenheter och dedikerade, fullständigt hanterade samt icke-registrerade enheter). I Intune väljer du **Klientappar** > **Appar** > **Lägg till**. Välj sedan **Hanterat Google Play-konto** i listan **Apptyp**. Mer information om appar för Hanterat Google Play-konto finns i [Lägga till appar för Google Play-konto till Android Enterprise-enheter med Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Installera Android LOB-appar obevakat på Zebra-enheter<!-- 4252734  -->
När du installerar verksamhetsspecifika (LOB) Android-appar på [Zebra-enheter](../configuration/android-zebra-mx-overview.md) kan du, i stället för att uppmanas att både ladda ned och installera LOB-appen, installera appen obevakat. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. I fönstret **Lägg till app** väljer du **Branschspecifik app**. Mer information finns i [Lägg till en verksamhetsspecifik app för Android i Microsoft Intune](../apps/lob-apps-android.md).

När LOB-appen har laddats ned visas ett meddelande om **utförd nedladdning** på användarens enhet. Meddelandet kan bara stängas genom att trycka på **Rensa alla** i meddelandeskuggan. Det här aviseringsproblemet kommer att åtgärdas i en kommande version och installationen kommer att vara helt obevakad utan några visuella indikatorer.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Läsa och skriva Graph API-åtgärder för Intune-appar<!-- 5031704  -->
Appar kan anropa Intune Graph API med både läs- och skrivåtgärder med hjälp av appidentitet utan användarens autentiseringsuppgifter. Mer information om hur du kommer åt Microsoft Graph API för Intune finns i [Arbeta med Intune i Microsoft Graph.](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Delning och kryptering av skyddade data för Intune App SDK för iOS<!-- 3586942  -->
Intune App SDK för iOS använder 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciper. Alla appar måste vara i SDK-version 8.1.1 för att delning av skyddade data ska vara möjlig.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Stöd för IKEv2 VPN-profiler för iOS<!-- 1943438   -->
I den här uppdateringen kan du skapa VPN-profiler för den iOS-inbyggda VPN-klienten med hjälp av IKEv2-protokoll. IKEv2 är en ny anslutningstyp i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **VPN** för profiltyp > **Anslutningstyp**.

Dessa VPN-profiler konfigurerar den inbyggda VPN-klienter, så att inga VPN-klientappar installeras på eller flyttas till hanterade enheter. Den här funktionen kräver att enheter registreras i Intune (MDM-registrering).

Om du vill se de aktuella VPN-inställningarna som du kan konfigurera går du till [Konfigurera VPN-inställningar på iOS-enheter](../configuration/vpn-settings-ios.md).

Gäller för:

- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>Enhetsfunktioner, enhetsbegränsningar och tilläggsprofiler för iOS- och macOS-inställningar visas efter registreringstyp<!-- 4886161   -->

I Intune skapar du profiler för iOS- och macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **macOS** för plattform > **Enhetsfunktioner**, **Enhetsbegränsningar** eller **Tillägg** för profiltyp). 

I den här uppdateringen kategoriseras de tillgängliga inställningarna i Intune-portalen efter vilken registreringstyp de gäller för:

- iOS
  - Användarregistrering
  - Enhetsregistrering
  - Automatisk enhetsregistrering (övervakad)
  - Alla registreringstyper

- macOS
  - Godkänd av användare
  - Enhetsregistrering
  - Automatisk enhetsregistrering
  - Alla registreringstyper

Gäller för:

- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>Nya röstkontrollinställningar för övervakade iOS-enheter som körs i helskärmsläge<!-- 4892835   -->
I Intune kan du skapa principer för att köra övervakade iOS-enheter som en kioskenhet eller dedikerad enhet (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Helskärm**).

I den här uppdateringen finns det nya inställningar du kan styra:
- **Röststyrning**: Aktiverar röststyrning på enheten i helskärmsläge.
- **Ändring av röststyrning**: Tillåt användare att ändra inställningen för Röststyrning på enheten i helskärmsläge.

Om du vill se de aktuella inställningarna går du till [inställningar för iOS i helskärmsläge](../configuration/device-restrictions-ios.md#kiosk).

Gäller för:

- iOS 13.0 och senare

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Använda enkel inloggning för appar och webbplatser på iOS- och macOS-enheter<!-- 4893175   -->
I den här uppdateringen finns det några inställningar för enkel inloggning för iOS- och macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **macOS** för plattform > **Enhetsfunktioner** för profiltyp).

Använd de här inställningarna till att konfigurera funktioner för enkel inloggning, särskilt för appar och webbplatser som använder Kerberos-autentisering. Du kan välja mellan ett tillägg för enkel inloggning med generiska autentiseringsuppgifter, och Apples inbyggda Kerberos-tillägg.

Om du vill se de aktuella enhetsfunktionerna du kan konfigurera går du till [iOS-enhetsfunktioner](../configuration/ios-device-features-settings.md) och [macOS-enhetsfunktioner](../configuration/macos-device-features-settings.md).

Gäller för:

- iOS 13.0 och senare
- macOS 10.15 och senare

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Associera domäner med appar på macOS 10.15+-enheter<!-- 4898079   -->
På macOS-enheter kan du konfigurera olika funktioner, flytta funktionerna till dina enheter med hjälp av en princip (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsfunktioner** för profiltyp). I den här uppdateringen kan du associera domäner med dina appar. Den här funktioner hjälper till att dela autentiseringsuppgifter med webbplatser relaterade till din app och kan användas med Apples tillägg för enkel inloggning, universella länkar och automatisk ifyllning av lösenord. 

Om du vill visa de aktuella funktionerna du kan konfigurera går du till [Funktionsinställningar för macOS-enheter i Intune](../configuration/macos-device-features-settings.md).

Gäller för:

- macOS 10.15 och senare

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Använd ”iTunes” och ”apps” i iTunes App Store-URL när du visar eller döljer appar på iOS-övervakade enheter<!-- 4928474   --> 
I Intune kan du skapa principer för att visa eller dölja appar på dina övervakade iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Visa eller dölj appar**). 

Du kan ange iTunes App Store-URL:en, till exempel `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. I den här uppdateringen kan både `apps` och `itunes` användas i URL:en, till exempel:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Mer information om de här inställningarna finns i [Visa eller dölja appar](../configuration/device-restrictions-ios.md#show-or-hide-apps).

Gäller för:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Lösenordstypvärden för Windows 10-efterlevnadsprincip är tydligare och matchar CSP<!-- 5138985 -->
På Windows 10-enheter kan du skapa en efterlevnadsprincip som kräver särskilda lösenordsfunktioner (**Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Windows 10 och senare** för plattform > **Systemsäkerhet**). I den här uppdateringen:
- Värden för**Lösenordstyp** är tydligare och uppdaterade för att matcha [CSP:n DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- Inställningen **Förfallotid för lösenord (dagar)** har uppdaterats till att tillåta värden från 1 till 730 dagar. 

Mer information om Windows 10-efterlevnadsinställningar finns i [Inställningar för Windows 10 och senare för att markera enheter som att de följer standard eller inte följer standard](../protect/compliance-policy-create-windows.md). 

Gäller för:
- Windows 10 och senare

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Uppdaterat användargränssnitt för att konfigurera åtkomst till Microsoft Exchange lokalt<!-- 4092920 -->  
Vi har uppdaterat konsolen där du [konfigurerar åtkomst till Microsoft Exchange lokalt](../protect/conditional-access-exchange-create.md). Alla konfigurationer för åtkomst till Exchange lokalt är nu tillgängliga i samma fönster i konsolen där du *aktiverar åtkomstkontroll för Exchange lokalt*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Tillåta eller begränsa tillägg av appwidgetar på startskärmen på Android Enterprise-arbetsprofilenheter<!-- 1109650  --> 
På Android Enterprise-enheter kan du konfigurera funktioner i arbetsprofilen (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast arbetsprofil > Enhetsbegränsningar** för profiltyp). I den här uppdateringen kan du tillåta användare att lägga till widgetar exponerade av arbetsprofilappar till enhetens startskärm.

Om du vill se alla inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:
- Android Enterprise-arbetsprofil

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Nya klientorganisationer använder som standard inte Android-enhetsadministratörshantering<!-- 4869790   -->
Androids enhetsadministratörsfunktioner har ersatts av Android Enterprise. Vi rekommenderar därför att du använder Android Enterprise för nya registreringar i stället. I en framtida uppdatering måste nya klientorganisationer slutföra följande nödvändiga steg i Android-registrering för att använda enhetsadministratörshantering: Gå till **Intune** > **Enhetsregistrering** > **Android-registrering** > **Personal and corporate-owned devices with device administration privileges** (Personliga och företagsägda enheter med enhetsadministratörsbehörighet)  > **Use device administrator to manage devices** (Använd enhetsadministratör för att hantera enheter).

Befintliga klienter får ingen förändring i sina miljöer.

Mer information om Android-enhetsadministratör i Intune finns i [Administratörsregistrering för Android-enhet](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>Lista över DEP-enheter associerade med en profil<!-- 5012045 idmiss -->
Du kan se en sidindelad lista över Apple DEP-enheter (programmet för enhetsregistrering) som är associerade med en profil. Du kan söka i listan från valfri sida i listan. Om du vill se listan går du till **Intune** > **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram** > välja en token > **Profiler** > välja en profil > **Tilldelade enheter** (under **Övervaka**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>Mer support för fullständigt hanterade Android-enheter<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Vi har lagt till följande support för fullständigt hanterade Android-enheter:

- SCEP-certifikat för fullständigt hanterad Android är tillgängliga för certifikatautentisering på enheter som hanteras som enhetsägare. SCEP-certifikat stöds redan på arbetsprofilenheter.  Med SCEP-certifikat för enhetsägare kan du: <!-- 5227935 -->
    - skapa SCEP-profil under avsnittet DO i Android Enterprise
    - länka SCEP-certifikat till DO Wi-Fi-profil för autentisering
    - länka SCEP-certifikat till DO VPN-profiler för autentisering
    - länka SCEP-certifikat till DO VPN-profiler för autentisering
- Systemappar stöds på Android Enterprise-enheter. I Intune lägger du till en Android Enterprise-systemapp genom att välja **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** väljer du **Android Enterprise-systemapp**. Du hittar mer information i [Lägg till Android Enterprise-systemappar i Microsoft Intune](../apps/apps-ae-system.md). <!-- 4062195 -->
- I **Enhetsefterlevnad** > **Android Enterprise** > **Enhetsägare** kan du skapa en efterlevnadsprincip som ställer in Google SafetyNet-attesteringsnivån.   <!-- 4631425 -->
- På fullständigt hanterade Android Enterprise-enheter stöds providers för skydd mot mobilhot. I **Enhetsefterlevnad** > **Android Enterprise** > **Enhetsägare** kan du välja en acceptabel hotnivå. <!-- 4631440 --> [Android Enterprise-inställningar för att markera enheter som kompatibla eller icke-kompatibla med Intune](../protect/compliance-policy-create-android-for-work.md#device-owner) listar de aktuella inställningarna.
- På fullständigt hanterade Android Enterprise-enheter kan Microsoft Launcher-appen nu konfigureras via appkonfigurationsprinciper för att tillåta en standardiserad slutanvändarupplevelse på den fullständigt hanterade enheten. Appen Microsoft Launcher kan användas till att anpassa Android-enheten. Med hjälp av appen tillsammans med ett Microsoft-konto eller ett arbets-/skolkonto kan du komma åt din kalender, dina dokument och senaste aktiviteter i det personliga flödet. <!-- 5334044 -->

Med den här uppdateringen är Intune-stödet för Android Enterprise fullständigt hanterad nu allmänt tillgängligt.

Gäller för:

- Fullständigt hanterade Android Enterprise-enheter

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>Skicka meddelanden till en enskild enhet<!-- 4928910 -->
Du kan nu välja en enskild enhet och sedan använda en fjärrenhetsåtgärd för att [skicka ett anpassat meddelande till bara den enheten](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>Åtgärderna för rensning och lösenordsåterställning är inte tillgängliga för iOS-enheter som har registrerats med användarregistrering<!-- 4950491 -->
Användarregistrering är en ny typ av Apple-enhetsregistrering. När du registrerar enheter med användarregistrering är fjärråtgärderna för rensning och lösenordsåterställning inte tillgängliga för sådana enheter.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Intune-stöd för iOS 13- och macOS Catalina-enheter<!-- 4665317 -->
Intune stöder nu hantering av både iOS 13- och macOS Catalina-enheter.
Mer information finns i [blogginlägget om Microsoft Intune-stöd iOS 13 och iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Enhetssäkerhet

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>BitLocker-stöd för klientbaserad rotering av återställningslösenord<!--  3444125 -->
Använd Intune Endpoint Protection-inställningar för att konfigurera [Klientbaserad rotering av återställningslösenord](../protect/endpoint-protection-windows-10.md#windows-encryption) för BitLocker på enheter som kör Windows version 1909 eller senare.

Den här inställningen initierar en klientbaserad uppdatering av återställningslösenord efter återställning av en operativsystemenhet (med bootmgr eller WinRE) och upplåsning av återställningslösenord på en fast dataenhet. Den är inställningen uppdaterar det specifika återställningslösenordet som har använts och andra oanvända lösenord på volymen förblir oförändrade. Mer information finns i BitLocker CSP-dokumentationen för [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Manipulationsskydd för Windows Defender Antivirus<!-- 4705448        -->
Använd Intune för att hantera *Manipulationsskydd* för Windows Defender Antivirus. Du hittar [inställningen för Manipulationsskydd](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center) i Microsoft Defender Säkerhetscenter-gruppen när du använder enhetskonfigurationsprofiler för Windows 10-slutpunktsskydd. Du kan ställa in manipulationsskydd på *Aktiverad* för att aktivera begränsningar för manipulationsskydd, *Inaktiverad* för att stänga av dem eller *Inte konfigurerad* för att lämna en enhetskonfiguration på plats.  

Mer information om Manipulationsskydd finns i [Prevent security settings changes with tamper protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) (Förhindara ändringar av säkerhetsinställningar med manipulationsskydd) i Windows-dokumentationen.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Avancerade inställningar för Windows Defender-brandväggen är nu allmänt tillgängliga<!--  5317392       -->  
De [anpassade brandväggsreglerna för slutpunktsskydd i Windows Defender](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), som du konfigurerar som en del av en enhetskonfigurationsprofil är inte längre en offentlig förhandsversion, utan är allmänt tillgängliga.  Du kan använda de här reglerna för att ange beteende för inkommande och utgående trafik till program, nätverksadresser och portar. Reglerna släpptes i juli som offentlig förhandsversion. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>Omfångstaggar stöder nu principer för användningsvillkor<!-- 2358863 idmiss -->
Nu kan du tilldela [omfångstaggar](scope-tags.md) till principer för användningsvillkor. Det gör du genom att gå till **Intune** > **Enhetsregistrering** > **Villkor** > välj ett objekt i listan > **Egenskaper** > **Omgångstaggar** > välja en omfångstagg.

## <a name="week-of-september-9-2019"></a>Veckan då den 9 september 2019 infaller

### <a name="app-management"></a>Apphantering

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Uppdateringar av Microsoft Intune-appen<!-- 4997846 -->
Microsoft Intune-appen för Android har uppdaterats med följande förbättringar:
- Uppdaterad och förbättrad layout som inkluderar navigering i nederkant för de viktigaste åtgärderna.
- Ytterligare en sida har lagts till som visar användarens profil.
- Visning av interaktiva meddelanden i appen för användaren har lagts till, exempelvis om enhetsinställningarna behöver uppdateras.
- Visning av anpassade push-meddelanden har lagts till, vilket ger appen samma stöd som nyligen lagts till i företagsportalappen för iOS och Android. Du hittar mer information i [Skicka anpassade meddelanden i Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>För iOS-enheter anpassar du registreringsprocessens sekretessida i Företagsportal<!-- 4394993 -->
Med Markdown kan du anpassa sekretessidan i Företagsportal som slutanvändare ser vid iOS-registrering. Mer specifikt kan du anpassa listan med saker som organisationen inte kan se eller göra på enheten. Mer information finns i [Så konfigurerar du appen Intune-företagsportal](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Veckan då den 2 september 2019 infaller

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Uppdatering av Intunes användargränssnitt – Instrumentpanel för klientorganisationsstatus<!-- 5273210  -->
Användargränssnittet för instrumentpanelen med klientorganisationsstatus har uppdaterats så att den överensstämmer med Azures användargränssnitt. Mer information finns i [Klientorganisationsstatus](../tenant-status.md).

## <a name="week-of-august-26-2019"></a>Den vecka som börjar 26 augusti 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Konfigurera Microsoft Edge-inställningar med hjälp av administrativa mallar för Windows 10 och senare<!-- 5228061 -->

På enheter med Windows 10 och senare kan du skapa administrativa mallar för att konfigurera grupprincipinställningar i Intune. I den här uppdateringen kan du konfigurera inställningar som gäller för Microsoft Edge version 77 och senare.

Mer information om administrativa mallar finns i [Använda Windows 10-mallar för att konfigurera grupprincipinställningar i Intune](../configuration/administrative-templates-windows.md).

Gäller för:

- Windows 10 och senare (Windows RS4 +)

## <a name="week-of-august-12-2019-1908-service-release"></a>Veckan den 12 augusti 2019 (1908 Service Release)

### <a name="app-management"></a>Apphantering

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>Kontroll av avinstallationsbeteende för iOS-app vid avregistrering av enhet<!-- 3504144   -->
Administratörer kan hantera om en app tas bort eller sparas på en enhet när enheten avregistreras på en användare- eller enhetsgruppnivå. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Kategorisera appar i Microsoft Store för företag<!-- 3926922 -->
Du kan kategorisera appar i Microsoft Store för företag. Om du vill göra det väljer du **Intune** > **Klientappar** > **Appar** > Välj en Microsoft Store för företag-app > **Appinformation** > **Kategori**. I den nedrullningsbara menyn tilldelar du en kategori.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Anpassade meddelanden för Microsoft Intune-appanvändare<!-- 4843354  -->
Microsoft Intune-appen för Android har nu stöd för visning av anpassade push-meddelanden, tillsammans med stödet som nyligen lagts till i företagsportalappar för iOS och Android. Du hittar mer information i [Skicka anpassade meddelanden i Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>Nya funktioner för dedikerade Android Enterprise-enheter i läge för flera appar<!-- 3755304 3041943 3041946   -->

I Intune kan du styra funktioner och inställningar i ett helskärmsläge på dina dedikerade Android Enterprise-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetsägare, enhetsbegränsningar** för profiltyp).

I den här uppdateringen läggs följande funktioner till:

- **Dedikerade enheter** > **Multi-app**: Den **virtuella hemknappen** kan visas genom att svepa upp på enheten eller flyta på skärmen så att användarna kan flytta den.
- **Dedikerade enheter** > **Multi-app**: Med **Åtkomst till ficklampa** kan användare använda ficklampan. 
- **Dedikerade enheter** > **Multi-app**: **Kontroll av medievolym** gör att användare kan kontrollera enhetens medievolym med ett skjutreglage. 
- **Dedikerade enheter** > **Multi-app**:  **Aktivera en skärmsläckare**, ladda upp en anpassad avbildning och kontrollera när skärmsläckaren visas.

Om du vill se aktuella inställningar, går du till [Inställningar för Android Enterprise-enheter som tillåter eller begränsar funktioner med Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Gäller för:

- Dedikerade Android Enterprise-enheter

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Ny app och konfigurationsprinciper för fullständigt hanterade Android Enterprise-enheter<!-- 3574215 3574238 3574235 3574232   -->
Med hjälp av profiler kan du konfigurera inställningar som tillämpar VPN-, e-post- och Wi-Fi-inställningar till dina ägare av Android Enterprise-enheter (fullständigt hanterade). I den här uppdateringen kan du:

- Använd [konfigurationsprinciper för appar](../apps/app-configuration-policies-use-android.md) för att distribuera Outlook, Gmail och nio e-postinställningar.
- Använd enhetskonfigurationsprofiler för att distribuera [inställningar för betrodda rotcertifikat](../protect/certificates-configure.md).
- Använd enhetskonfigurationsprofiler för att distribuera inställningar för [VPN](../configuration/vpn-settings-android-enterprise.md) och [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md).

> [!IMPORTANT]
> Med den här funktionen autentiseras användare med sitt användarnamn och lösenord för VPN-, Wi-Fi- och e-postprofiler. Certifikatbaserad autentisering är för närvarande inte tillgängligt.

Gäller för:  
- Ägare av Android Enterprise-enhet (helt hanterad)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>Kontrollera appar, filer, dokument och mappar som öppnas när användare loggar in på macOS-enheter<!--3914202   -->
Du kan aktivera och konfigurera funktioner på macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsfunktioner** för profiltyp). 

I den här uppdateringen har du en ny inställning för inloggningsobjekt som styr vilka appar, filer, dokument och mappar som öppnas när en användare loggar in till den registrerade enheten. 

Om du vill visa de aktuella inställningarna går du till [Funktionsinställningar för macOS-enheter i Intune](../configuration/macos-device-features-settings.md).

Gäller för:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Tidsgränser ersätter inställningarna för interaktiv omstart för Windows-uppdateringsringar<!-- 4464404        -->
För att justera med de senaste [ändringarna i Windows-underhåll](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing) har Intunes Windows 10-uppdateringsringar nu [stöd för inställningar för tidsgränser](../protect/windows-update-settings.md). *Tidsgränser* fastställer när en enhet installerar funktions- och säkerhetsuppdateringar.  På enheter som kör Windows 10 1903 eller senare ersätter *tidsgränser* konfigurationerna för *interaktiv omstart*.  I framtiden kommer *tidsgränser* att ersätta *interaktiv omstart* på tidigare versioner av Windows 10 också.  

När du inte konfigurerar *tidsgränser* fortsätter enheterna att använda sina inställningar för *interaktiv omstart*, men Intune kommer att ha stöd för inställningar för interaktiv omstart i en framtida uppdatering.  

Planera att använda *tidsgränser* för alla dina Windows 10-enheter. När inställningarna för *tidsgränser* är på plats kan du ändra Intune-konfigurationerna för *interaktiv omstart* till Inte konfigurerad. När den är inställd på Inte konfigurerad, slutar Intune att hantera inställningarna på enheter, men tar inte bort de senaste konfigurationerna för inställningen från enheten. Därför förblir de senaste konfigurationerna som ställts in för *interaktiv omstart* aktiva och används på enheter tills inställningarna har ändrats via en annan metod än Intune. Senare, när enhetsversionen av Windows ändras eller när Intune-stöd för *tidsgränser* expanderar till enhetens Windows-version, börjar enheten att använda de nya inställningarna, som redan finns på plats.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>Stöd för flera Microsoft Intune Certificate Connectors<!--   4704642      -->
Intune har nu stöd för installation och användning av flera [Microsoft Intune Certificate Connectors för PKCS-åtgärder](../protect/certficates-pfx-configure.md). Den här ändringen stöder belastningsutjämning och hög tillgänglighet för anslutningen. Varje anslutningsinstans kan bearbeta certifikatbegäranden från Intune.  Om en anslutning inte är tillgänglig fortsätter andra anslutningar att bearbeta begäranden.

Om du vill använda flera anslutningar behöver du inte uppgradera till den senaste versionen av anslutningsprogrammet.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>Nya inställningar och ändringar i befintliga inställningar för att begränsa funktionerna på iOS-och macOS-enheter<!-- 4867699 4867709   -->
Du kan skapa profiler för att begränsa inställningar på enheter som kör iOS och macOS (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **macOS** för plattformstyp > **Enhetsbegränsningar**). Den här uppdateringen innehåller följande funktioner:

- På **macOS** > **Enhetsbegränsningar** > **Moln och lagring**, använder du den nya inställningen **Handoff** för att blockera användare från att starta arbetet på en macOS-enhet och fortsätta att arbeta på en annan macOS-eller iOS-enhet.

  Gå till [macOS-enhetsinställningar för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-macos.md) för att se de aktuella inställningarna.

- På **iOS** > **Enhetsbegränsningar** finns det vissa ändringar:

  - **Inbyggda appar** > **Hitta min iPhone (endast övervakat)** : Ny inställning som blockerar den här funktionen i funktionen Hitta min app. 
  - **Inbyggda appar** > **Hitta mina vänner (endast övervakat)** : Ny inställning som blockerar den här funktionen i funktionen Hitta min app. 
  - **Trådlös** > **Ändring av Wi-Fi-tillstånd (endast övervakat)** : Ny inställning som förhindrar att användare aktiverar eller inaktiverar Wi-Fi på enheten.
  - **Tangentbord och ordlista** > **QuickPath (endast övervakat)** : Ny inställning som blockerar QuickPath-funktionen.
  - **Moln och lagring**: **Aktivitetsfortsättning** har bytt namn till **Handoff**.

  Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md) för att se de aktuella inställningarna.

Gäller för:  
- macOS 10.15 och senare
- iOS 13 och senare

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Vissa begränsningar för iOS-enheter som inte övervakas kommer att bli övervakade – endast med iOS 13.0-versionen<!-- 4867809   -->
I den här uppdateringen gäller vissa inställningar endast övervakade enheter med iOS 13.0-versionen. Om de här inställningarna konfigureras och tilldelas till ej övervakade enheter före iOS 13.0-versionen, tillämpas inställningarna fortfarande på de enheter som inte övervakas. De gäller även när enheterna har uppgraderat till iOS 13.0. Dessa begränsningar tas bort på ej övervakade enheter som säkerhetskopieras och återställs.

Inställningarna omfattar:

- App Store, dokumentvisning, spel
  - Appbutik
  - Stötande innehåll i iTunes-musik, podcast eller nyheter
  - Lägga till Game Center-vänner
  - Spel för flera personer
- Inbyggda appar
  - Kamera
    - FaceTime
  - Safari
    - Autofyll
- Moln och lagring
  - Säkerhetskopiera till iCloud
  - Blockera synkronisering av iCloud-dokument
  - Blockera synkronisering av iCloud-nyckelring

Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md) för att se de aktuella inställningarna.

Gäller för:  
- iOS 13.0 och senare

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>Förbättrad enhetsstatus för macOS FileVault-kryptering<!-- 4944983         -->
Vi har uppdaterat flera [enhetsstatusmeddelanden](../protect/encryption-monitor.md#device-encryption-status) för FileVault-kryptering på MacOS-enheter.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>Vissa inställningar för Windows Defender Antivirus-genomsökning i rapporten visar felaktig status<!-- 5119229 -->
I Intune kan du skapa principer för att använda Windows Defender Antivirus för att söka igenom dina Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp > **Windows Defender Antivirus**). Rapporter om **tid det tar att utföra en daglig snabbsökning** och **typ av systemgenomsökning som ska utföras** visar statusen Misslyckad, när det faktiskt är en lyckad status. 

I den här uppdateringen ändras detta beteende. Det innebär att inställningarna **tid det tar att utföra en daglig snabbsökning** och **typ av systemgenomsökning som ska utföras** visar statusen Genomförd när skanningen slutförs korrekt och visar Misslyckad när inställningarna inte tillämpas.

Mer information om inställningarna för Windows Defender Antivirus finns i [Enhetsinställningar för Windows 10 (och senare) för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="default-scope-tags---3702875----"></a>Standardomfångstaggar<!-- 3702875  -->
En nyinbyggd standardomfångstagg är nu tillgänglig. Alla icke-taggade Intune-objekt som stöder omfångstaggar tilldelas automatiskt till standardomfångstaggen. **Standardomfångstaggen** läggs till i alla befintliga rolltilldelningar för att upprätthålla paritet med administratörsupplevelsen idag. Om du inte vill att en administratör ska se Intune-objekt med standardomfångstaggen, tar du bort standardomfångstaggen från rolltilldelningen. Den här funktionen liknar funktionen säkerhetsomfattningar i Configuration Manager. Mer information finns i [Använda RBAC och omfångstaggar för distribuerad IT](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Stöd för registrering av Android-enhetens administratör<!-- 4869749   -->
Alternativet för registrering av Android-enhetens administratör har lagts till på sidan Android-registrering (**Intune** > **Enhetsregistrering** > **Android-registrering)** . Android-enhetens administratör är fortfarande aktiverad som standard för alla klienter.  Du hittar mer information i [Registrering av Android-enhetens administratör](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Hoppa över fler skärmar i installationsassistenten <!--4877451  -->
Du kan ställa in att programprofiler för enhetsregistrering hoppar över följande installationsassistentskärmar:
- För iOS
    - Utseende
    - Express-språk
    - Önskat språk
    - Migrering av enhet till enhet
- För macOS
    - Skärmtid
    - Installation av Touch-ID

Mer information om anpassning av installationsassistenten finns i [Skapa en Apple-registreringsprofil för iOS](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) och [Skapa en Apple-registreringsprofil för MacOS](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Lägg till en användarkolumn till CSV-överföringsprocessen för autopilotenheten<!-- 3823054 -->
Nu kan du lägga till en användarkolumn till CSV-överföringen för autopilotenheter. På så sätt kan du tilldela många användare på samma gång när du importerar CSV-filen. Du hittar mer information i [Registrera Windows-enheter i Intune med hjälp av Windows Autopilot](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Enhetshantering

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Konfigurera tidsgräns för automatisk rensning av enhet till 30 dagar<!--4231059  -->
Du kan ställa in den automatiska tidsgränsen för enhetsrensning så kort som 30 dagar (i stället för den tidigare gränsen på 90 dagar) efter den senaste inloggningen. Det gör du genom att gå till **Intune** > **Enheter** > **Installation** > **Regler för rensning av enhet**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Versionsnummer finns på Android-enhetens maskinvarusida<!-- 4461910   -->
En ny post på sidan Maskinvara för varje Android-enhet innehåller versionsnumret för enhetens operativsystem. Mer information finns i [Visa enhetsinformation i Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Veckan 5 augusti 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies är en OEM-tillverkare som stöds för OEMConfig på Android Enterprise-enheter<!-- 4843713 -->

I Intune kan du kan skapa en profil för enhetskonfiguration och använda inställningar för Android Enterprise-enheter med hjälp av OEMConfig (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **OEMConfig** för profiltyp).

I den här uppdateringen är Zebra Technologies en OEM-tillverkare (Original Equipment Manufacturer) som stöds för OEMConfig. Mer information om OEMConfig hittar du i [Använda och hantera Android Enterprise-enheter med OEMConfig](../configuration/android-oem-configuration-overview.md).

Gäller för:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019-1907-service-release"></a>Veckan den 22 juli 2019 (1907 Service Release)

### <a name="app-management"></a>Apphantering

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Anpassade meddelanden för användare och grupper<!-- 16766574          -->
Skicka anpassade push-meddelanden från företagsportalprogrammet till användare på iOS- och Android-enheter som du hanterar med Intune. Dessa mobila push-meddelanden är mycket anpassningsbara med fri text och kan användas för alla ändamål. Du kan rikta dem till olika användargrupper i din organisation. Mer information finns i [anpassade meddelande](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>Googles app för enhetspolicykontroll<!-- 3041950  -->
Nu ger Managed Home Screen-appen tillgång till Googles Android Device Policy-app. Managed Home Screen-appen är en anpassad startfunktion som används med enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som använder helskärmsläge för flera appar. Du kan komma åt Android Device Policy-appen, eller vägleda användare till Android Device Policy-appen, för support och felsökning. Den här startfunktionen är tillgänglig när enheten registreras och låses på startskärmen i Managed Home Screen. Inga ytterligare installationer behövs för att använda den här funktionen.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Outlook-skyddsinställningar för iOS- och Android-enheter<!-- 3212619 -->
Du kan nu konfigurera både allmänna konfigurationsinställningar för appar och dataskydd för Outlook för iOS och Android med hjälp av enkla Intune-administratörskontroller utan enhetsregistrering. Konfigurationsinställningarna för allmänna appar ger paritet med inställningar som administratörer kan aktivera när de hanterar Outlook för iOS och Android på registrerade enheter. Mer information om Outlook-inställningar finns i [appkonfigurationsinställningar för att distribuera Outlook för iOS och Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready------"></a>Använd ”tillämplighetsregler” när du skapar konfigurationsprofiler för Windows 10-enheter <!-- 2549910 eeready    -->

Du skapar konfigurationsprofiler för Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10** som plattform > **Tillämplighetsregler**). I den här uppdateringen kommer du att kunna skapa en **tillämpningsregel** så att profilen endast gäller för en viss utgåva eller en specifik version. Exempelvis kan du skapa en profil som aktiverar vissa BitLocker-inställningar. När du lägger till profilen använder du en tillämpningsregel så att profilen endast gäller för enheter som kör Windows 10 Enterprise.

Information om hur du lägger till en tillämplighetsregel finns i [Tillämplighetsregler](../configuration/device-profile-create.md#applicability-rules).

Gäller för: Windows 10 och senare

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>Använd tokens för att lägga till enhetsspecifik information i anpassade profiler för iOS-och macOS-enheter<!-- 3330008  -->
Du kan använda anpassade profiler på iOS- och MacOS-enheter för att konfigurera inställningar och funktioner som inte är inbyggda i Intune (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** eller **MacOS** för plattform > **Anpassad** för profiltyp). I den här uppdateringen kan du lägga till tokens till dina `.mobileconfig`-filer för att lägga till enhetsspecifik information. Du kan till exempel lägga till `Serial Number: {{serialnumber}}` i konfigurationsfilen för att visa enhetens serienummer.

Du hittar information om att skapa en anpassad profil i [anpassade inställningar för iOS](../configuration/custom-settings-ios.md) eller [anpassade inställningar för MacOS](../configuration/custom-settings-macos.md).

Gäller för:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Ny konfigurationsdesign när du skapar en OEMConfig-profil för Android Enterprise<!-- 3712769   -->
I Intune kan du skapa en enhetskonfigurationsprofil som använder en OEMConfig-app (enhetskonfiguration > Profiler > Skapa profil > Android Enterprise för plattform > OEMConfig för profiltyp). När du gör det öppnas en JSON-redigerare med en mall och de värden som du kan ändra. 

Den här uppdateringen innehåller en konfigurationsdesign med en förbättrad användarupplevelse som visar information som är inbäddad i appen, inklusive titlar, beskrivningar och mer. JSON-redigeraren är fortfarande tillgänglig och visar eventuella ändringar som du gör i Configuration Designer.

Om du vill se de aktuella inställningarna går du till [Använda och hantera Android Enterprise-enheter med OEMConfig](../configuration/android-oem-configuration-overview.md).

Gäller för: Android enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Uppdaterat användargränssnitt för att konfigurera Windows Hello<!-- 4089576            -->
Vi har uppdaterat konsolen där du [konfigurerar Intune för att använda Windows Hello för företag](../protect/windows-hello.md). Alla konfigurationsinställningar är nu tillgängliga i samma fönster i konsolen där du aktiverar stöd för Windows Hello.

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
Intune PowerShell SDK, som ger stöd för Intune API via Microsoft Graph, har uppdaterats till version 6.1907.1.0. SDK har nu stöd för följande:
- Fungerar med Azure Automation.
- Har stöd för läsåtgärder för app-only-autentisering. 
- Har stöd för egna korta namn som alias.
- Följer namnkonventioner för PowerShell. Mer specifikt har `PSCredential`-parametern (på `Connect-MSGraph`-cmdleten) bytt namn till `Credential`.
- Stöder manuell angivelse av värdet för `Content-Type`-sidhuvudet när du använder `Invoke-MSGraphRequest`-cmdleten.

Mer information finns i [PowerShell SDK för Microsoft Intune Graph API.](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Uppdateringar för registreringsbegränsningar<!-- 2871968 -->
Registreringsbegränsningar för nya klienter har uppdaterats så att Android Enterprise Work-profiler tillåts som standard. Befintliga klienter får ingen förändring. Om du vill använda Android Enterprise Work-profiler måste du fortfarande [ansluta ditt Intune-konto till ditt hanterade Google Play-konto](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Användargränssnittsuppdateringar för Apple-registrering och registreringsbegränsningar<!--4089575, 4089579  -->
De två följande processerna använder ett användargränssnitt med en guide:
- Registrering av Apple-enhet. Mer information finns i [Registrera iOS-enheter automatiskt med Apples program för enhetsregistrering](../enrollment/device-enrollment-program-enroll-ios.md).
- Skapa registreringsbegränsningar. Mer information finns i [Konfigurera registreringsrestriktioner](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>Hantera förkonfigurering av enhetsidentifierare för företag för Android Q-enheter<!-- 4711509  idmiss -->
I Android Q (v10) tar Google bort möjligheten för MDM-agenter på tidigare hanterade Android-enheter (enhetsadministratör) för att samla in information om enhetsidentifieraren.  Intune har en funktion som gör det möjligt för IT-administratörer att [förkonfigurera en lista över enhetsserienummer eller IMEI](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) för att automatiskt tagga enheterna som företagsägda. Den här funktionen fungerar inte för Android Q-enheter som hanteras av enhetsadministratören.  Oavsett om serienumret eller IMEI för enheten har laddats upp anses det alltid vara personligt under Intune-registreringen.  Du kan manuellt växla ägarskap till företag efter registreringen.  Detta påverkar endast nya registreringar och befintliga registrerade enheter påverkas inte.  Android-enheter som hanteras med arbetsprofiler påverkas inte av den här ändringen och fortsätter att fungera som de gör i dag.  Dessutom kommer Android Q-enheter som registrerats som enhetsadministratör inte längre att kunna rapportera serienummer eller IMEI i Intune-konsolen som enhetsegenskaper.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Ikoner har ändrats för Android Enterprise-registreringar (arbetsprofil, dedikerade enheter och fullständigt hanterade enheter)<!-- 4977730 -->
Ikonerna för Android Enterprise-registreringsprofiler har ändrats. Om du vill se de nya ikonerna går du till **Intune** > **Registrering** > **Android-registrering** > tittar under **Registreringsprofiler**.


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Ändring av datainsamling i Windows-diagnostikdata<!-- 4113859 -->
Standardvärdet för insamling av diagnostikdata har ändrats för enheter som kör Windows 10, version 1903 och senare. Från och med Windows 10 1903 aktiveras insamling av diagnostikdata som standard. Windows-diagnostikdata är viktiga tekniska data från Windows-enheter om enheten och hur Windows och relaterad programvara fungerar. Mer information finns i [Konfigurera Windows-diagnostikdata i din organisation](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Autopilot-enheter anges också som ”fullständig” telemetri om inget annat anges i autopilotprofilen med [ System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Enhetshantering

#### <a name="improve-device-location---3855417----"></a>Förbättra enhetens plats<!-- 3855417  -->
Du kan zooma in till de exakta koordinaterna för en enhet med åtgärden **Hitta enhet**. Mer information om hur du hittar borttappade iOS- enheter finns i [Hitta borttappade iOS-enheter](../remote-actions/device-locate.md).

### <a name="device-security"></a>Enhetssäkerhet

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Avancerade inställningar för Windows Defender-brandväggen (offentlig förhandsversion)<!--  1311949     -->  
Använd Intune för att [hantera anpassade brandväggsregler som en del av en enhetskonfigurationsprofil](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) för Endpoint Protection på Windows 10. Regler kan ange beteende för inkommande och utgående trafik till program, nätverksadresser och portar. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Uppdaterat användargränssnitt för hantering av säkerhetsbaslinjer<!-- 4091125     -->
Vi har uppdaterat [skapa och redigera-upplevelsen](../protect/security-baselines.md#create-the-profile) i Intune-konsolen för våra säkerhetsbaslinjer. Ändringarna omfattar:

Ett enklare guideformat som har komprimerats till ett enda blad. inom ett blad. Den här nya designen tar bort bladspridningen som kräver att IT-proffs måste öka detaljnivån till flera separata fönster.  
Nu kan du skapa tilldelningar som en del av skapa och redigera-upplevelsen, i stället för att behöva gå tillbaka senare för att tilldela baslinjer. Vi har lagt till en sammanfattning av de inställningar som du kan visa innan du skapar en ny baslinje och när du redigerar en befintlig. Vid redigering visar sammanfattningen bara listan över objekt som har angetts i kategorin med egenskaper som redigeras.

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Veckan som inleds med den 15 juli 2019 

### <a name="app-management"></a>Apphantering

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Ikoner för hanterad hemskärm och hanterade inställningar<!-- 4918107 -->
Ikonen för appen för hanterad hemskärm och ikonen för **hanterade inställningar** har uppdaterats. Appen för hanterad hemskärm används bara av enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som kör i helskärmsläge för flera appar. Mer information om appen för hanterad hemskärm finns i [Konfigurera Microsoft-appen för hanterad hemskärm för Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android-enhetspolicy på dedikerade Android Enterprise-enheter<!-- 4918136 -->
Du kan komma åt Android-enhetspolictprogrammet från felsökningsskärmen för den hanterade hemskärmsappen. Appen för hanterad hemskärm används bara av enheter som har registrerats i Intune som AE-dedikerade (Android Enterprise) enheter som kör i helskärmsläge för flera appar. Du hittar mer information i [Konfigurera Microsofts hanterade hemskärmsapp för Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>Uppdateringar av iOS-företagsportalen<!-- 3902931 -->
Ditt företagsnamn vid begäranden om hantering av iOS-appar ersätter den aktuella ”i.manage.microsoft.com”-texten. Användare ser till exempel företagets namn i stället för ”i.manage.microsoft.com” när de försöker installera en iOS-app från Företagsportalen eller när de tillåter hantering av appen. Detta kommer att distribueras till alla kunder under de närmaste dagarna.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>Hantera FileVault för macOS<!--  3858502 + 4557986 + 1210104  -->
Du kan använda Intune för att [hantera FileVault-krypteringsnyckel för MacOS-enheter](../protect/encrypt-devices.md). För att kryptera enheter kan du använda en enhetskonfigurationsprofil för slutpunktsskydd.

Vår support för FileVault omfattar kryptering av okrypterade enheter, deposition av enheters personliga återställningsnyckel, automatisk eller manuell rotation av personliga krypteringsnycklar och nyckelhämtning för företagsenheter. Slutanvändare kan också använda Företagsportalens webbplats för att hämta den personliga återställningsnyckeln för sina krypterade enheter.

Vi har också expanderat krypteringsrapporten till att inkludera [information om FileVault](../protect/encryption-monitor.md) för BitLocker, så att du kan visa all din enhets krypteringsinformation på en och samma plats.

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>Windows autopilot-återställning tar bort enhetens primära användare<!-- 4156123 -->
När autopilot-återställning används på en enhet tas enhetens primära användare bort. Nästa användare som loggar in efter återställningen kommer att anges som primär användare. Den här funktionen kommer att distribueras till alla kunder under de närmaste dagarna.

## <a name="week-of-july-8-2019"></a>Veckan som inleds med den 8 juli 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Nya Office-, Windows- och OneDrive-inställningar i administrativa mallar i Windows 10 <!-- 3510695 -->

Du kan skapa administrativa mallar i Intune som imiterar lokal grupprinciphantering (**enhetshantering** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Administrativ mall** för profiltyp).

Den här uppdateringen innehåller fler Office-, Windows- och OneDrive-inställningar som du kan lägga till i dina mallar. Med de här nya inställningarna kan du nu konfigurera över 2500-inställningar som är 10 0% molnbaserade.

Mer information om den här funktionen finns i [Använda Windows 10-mallar för att konfigurera grupprincipinställningar i Intune](../configuration/administrative-templates-windows.md).

Gäller för: Windows 10 och senare

## <a name="week-of-july-1-2019"></a>Veckan som inleds med den 1 juli 2019 

### <a name="app-management"></a>Apphantering

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>AAD och APP på Android Enterprise-enheter<!-- 3574267 -->
När du registrerar fullständigt hanterade Android Enterprise-enheter kommer användarna nu att registreras med Azure Active Directory (AAD) under den första installationen av den nya eller fabriksåterställda enheten. Innan installationen slutfördes tidigare var användaren tvungen att starta Microsoft Intune-appen manuellt för att starta AAD-registreringen efter att installationen slutförts. Nu när användaren kommer till enhetens startsida efter den första installationen, är enheten både ansluten och registrerad.

Förutom AAD-uppdateringar stöds nu Intune App Protection-principer (APP) på fullständigt hanterade Android Enterprise-enheter. Den här funktionen kommer att bli tillgänglig då vi distribuerar den. Du hittar mer information i [Lägg till hanterade Google Play-appar till Android enterprise-enheter med Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019-1906-service-release"></a>Veckan den 24 juni 2019 (1906 Service Release)

### <a name="app-management"></a>Apphantering

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>Konfigurera vilken webbläsare som ska ha tillåtelse att länka till organisationsdata<!-- 3145939 -->
Principer för Intune-appskydd (APP) på enheter med Android och iOS gör att du nu kan överföra organisationswebblänkar till en viss webbläsare utöver Intune Managed Browser eller Microsoft Edge.  Mer information om APP finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>Sidan Alla appar identifierar Microsoft Store för företagsappar online/offline<!--4089647 -->
Sidan **Alla appar** innehåller nu etiketter för att identifiera Microsoft Store-appar för företag (MSFB) som online- eller offline-appar. Varje MSFB-app innehåller nu ett suffix för **online** eller **offline**. Sidan med information om appen innehåller också **Licenstyp** och **stöder enhetskontextinstallation** (endast offline-licensierade appar).

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Företagsportalappen på delade Windows-enheter<!--4393553 -->
Användare kan nu komma åt företagsportalappen på delade Windows-enheter. Slutanvändare ser en **Delad** etikett på enhetspanelen. Detta gäller version 10.3.45609.0 och senare av Windows företagsportalappen.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>Visa alla installerade appar från den nya webbplatsen för företagsportalen<!-- 4224326 -->
Företagsportalens webbplats har en ny sida för **Installerade appar** som visar alla hanterade appar, både nödvändiga och tillgängliga, som är installerade på en användares enhet. Förutom tilldelningstyp kan användare se appens utgivare, utgivningsdatum och aktuell installationsstatus. Om din organisation inte gör appar obligatoriska eller tillgängliga ser användarna ett meddelande som förklarar att inga företagsappar har installerats. Om du vill se den nya sidan på webben går du till den [företagsportalwebbplatsen](https://portal.manage.microsoft.com) och klickar på **Installerade appar**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>I nästa vy kan appanvändare se alla hanterade appar som har installerats på enheten<!-- 2352913 -->  
Företagsportalappen för Windows visar alla hanterade appar, både nödvändiga och tillgängliga, som är installerade på en användares enhet. Användare kommer att kunna visa installationsförsök och väntande installationer, och deras aktuella status. Om din organisation inte gör appar obligatoriska eller tillgängliga ser användarna ett meddelande som förklarar att inga företagsappar har installerats. Om du vill se den nya vyn, gå till företagsportalens navigeringsfönster och välj **Appar** > **Installerade appar**.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Konfigurera inställningar för kerneltillägg på macOS-enheter<!-- 2043024 -->
På macOS-enheter kan du skapa en enhetskonfigurationsprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **macOS** som plattform). Denna uppdatering inkluderar en ny grupp med inställningar som gör att du kan konfigurera och använda kerneltillägg på dina enheter. Du kan lägga till vissa tillägg eller tillåta alla tillägg från en speciell partner eller utvecklare.

Mer information om den här funktionen finns i [översikt över kerneltillägg](../configuration/kernel-extensions-overview-macos.md) och [inställningar för kerneltillägg](../configuration/kernel-extensions-settings-macos.md).

Gäller för: macOS 10.13.2 och senare

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Appar från inställningen Endast Store för Windows 10-enheter innehåller fler konfigurationsalternativ<!-- 2697002 -->
När du skapar en enhetsbegränsningsprofil för Windows-enheter kan du använda inställningen **Appar endast från Store**. Det gör att användare endast installerar appar från Windows App Store (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Enhetsbegränsningar** för profiltyp). I den här uppdateringen kommer inställningen att expanderas för att stödja fler alternativ.

Gå till [Enhetsinställningar för Windows 10 (och senare) för att tillåta eller begränsa funktioner](../configuration/device-restrictions-windows-10.md#app-store) för att se den nya inställningen.

Gäller för: Windows 10 och senare

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>Distribuera flera Zebra Mobility Extensions-enhetsprofiler till en enhet, samma användargrupp eller samma grupp av enheter<!-- 4089955 -->
I Intune kan du använda Zebra Mobility Extensions (MX) i en profil för enhetskonfiguration för att anpassa inställningar för Zebra-enheter som inte är inbyggda i Intune. För närvarande kan du distribuera en profil till en enskild enhet. I den här uppdateringen kan du distribuera flera profiler till:
- Samma användargrupp
- Samma enhetsgrupp
- En enskild enhet

[Använda och hantera Zebra-enheter med Zebra Mobility Extensions i Microsoft Intune](../configuration/android-zebra-mx-overview.md) visar hur du använder MX i Intune.

Gäller för: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>Vissa inställningar för helskärmsläge på iOS-enheter är angivna till ”Blockera”, vilket ersätter ”Tillåt”<!-- 4404075  -->
När du skapar en enhetsbegränsningsprofil på iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Helskärmsläge**) ställer du in **Autolås**, **Ringsignalsknapp**, **Skärmrotation**, **Viloläge för skärm-knapp** och **Volymknappar**.

I denna uppdatering är värdena **Blockera** (blockerar funktionen) och **Inte konfigurerat** (tillåter funktionen). Om du vill se inställningarna går du till [iOS-enhetsinställningar för att tillåta eller begränsa funktioner](../configuration/device-restrictions-ios.md#kiosk).

Gäller för: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>Använd Face ID för lösenordsautentisering på iOS-enheter<!-- 4490704 -->
När du skapar en enhetsbegränsningsprofil för iOS-enheter kan du använda ett fingeravtryck som lösenord. Inställningarna för lösenord med fingeravtryck tillåter även ansiktsigenkänning i denna uppdatering (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **Lösenord**). Därför ändras följande inställningar:

- **Upplåsning med fingeravtryck** är nu **Upplåsning av Touch ID och Face ID**.
- **Ändring av fingeravtryck (endast övervakat)** är nu **Ändring av Touch ID och Face ID (endast övervakat)** .

Face ID är tillgängligt i iOS 11.0 och senare. Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md#password) för att se inställningarna.

Gäller för: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>Begränsning av spel och App Store-funktioner på iOS-enheter är nu beroende av klassificeringsregion<!-- 4593948 -->
På iOS-enheter kan du tillåta eller begränsa funktioner för spel, App Store och dokumentvisning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel**). Du kan också välja klassificeringsregion, till exempel USA.

I denna uppdatering är funktionen **Appar** underordnad **klassificeringsregion** och är beroende av **klassificeringsregion**. Gå till [Enhetsinställningarna för iOS tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming) för att se inställningarna.

Gäller för: iOS

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Windows autopilot-stöd för Hybrid Azure AD-anslutning<!-- 4809146-->
Windows autopilot för befintliga enheter stöder nu hybrid Azure AD-anslutning (förutom det befintliga stödet för Azure AD-anslutning). Gäller för Windows 10 version 1809 och senare enheter. Mer information finns i [Windows Autopilot för befintliga enheter](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

### <a name="device-management"></a>Enhetshantering

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Se säkerhetskorrigeringsnivå för Android-enheter<!-- 4461911 -->
Du kan nu se säkerhetskorrigeringsnivå för Android-enheter. Det gör du genom att välja **Intune** > **Enheter** > **Alla enheter** > välj en enhet > **Maskinvara**.
Korrigeringsnivån visas i avsnittet **Operativsystem**.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Tilldela omfångstaggar till alla hanterade enheter i en säkerhetsgrupp<!-- 3173810 -->
Du kan nu tilldela omfångstaggar till en säkerhetsgrupp, och alla enheter i säkerhetsgruppen kommer också att associeras med omfångstaggarna i en kommande uppdatering. Alla enheter i grupperna kommer också att tilldelas omfångstaggen. Omfångstaggar med den här funktionen skriver över omfångstaggar med det aktuella flödet för enhetens omfångstaggar. Mer information finns i [Använda RBAC och omfångstaggar för distribuerad IT](scope-tags.md).

### <a name="device-security"></a>Enhetssäkerhet

#### <a name="use-keyword-search-with-security-baselines------"></a>Använd nyckelordssökning med säkerhetsbaslinjer<!--  -->
När du skapar eller redigerar [Profiler för säkerhetsbaslinje](../protect/security-baselines.md#create-the-profile) kan du ange nyckelord i det nya *Sök*-fältet för att filtrera tillgängliga grupper med inställningar till de som innehåller dina sökvillkor.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>Funktionen säkerhetsbaslinjer är nu allmänt tillgänglig<!-- 3785395 -->
Funktionen **Säkerhetsbaslinjer** är inte längre i förhandsversionen utan är allmänt tillgänglig.  Det innebär att funktionen är klar att användas i produktion. De enskilda baslinjemallarna kan dock bevaras i förhandsversionen och utvärderas och publiceras som allmänt tillgängliga enligt sina egna scheman.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>Mallen för MDM-säkerhetsbaslinjer är nu allmänt tillgänglig<!-- 3794072, 4217151,  3534649 -->
Mallen för MDM-säkerhetsbaslinjer är inte längre i förhandsversionen utan är nu allmänt tillgänglig. Mallen för allmän tillgänglighet identifieras som **MDM-säkerhetsbaslinje för maj 2019**.  Det här är en ny mall och inte en uppgradering från förhandsversionen.  Som en ny mall måste du granska [inställningarna den innehåller](../protect/security-baseline-settings-mdm.md)och sedan skapa nya profiler för att distribuera mallen till din enhet. Andra säkerhetsbaslinjer kan finnas kvar i förhandsversionen. En lista över tillgängliga baslinjer finns i [tillgängliga säkerhetsbaslinjer](../protect/security-baselines.md#available-security-baselines).  

Förutom att vara en ny mall innehåller mallen *MDM-säkerhetsbaslinjen för maj 2019* de två inställningar som vi nyligen presenterade i vår utvecklingsartikel:  
- På låsskärmen: Röstaktivera appar från en låst skärm  
- DeviceGuard: Använd virtualiseringsbaserad säkerhet (VBS) vid nästa omstart av enheter.  

*MDM-säkerhetsbaslinjen för maj 2019* innehåller också tillägg av flera nya inställningar, borttagning av andra och granskning av standardvärdet för en inställning. En detaljerad lista över ändringarna från förhandsgranskning till allmänt tillgänglig finns i **Vad som har ändrats i den nya mallen**.

#### <a name="security-baseline-versioning---3194322---"></a>Versioner av säkerhetsbaslinjer<!-- 3194322 -->
Säkerhetsbaslinjer för version av Intune-support. Då nya versioner av varje säkerhetsbaslinje släpps med detta stöd kan du uppdatera dina befintliga säkerhetsbaslinjeprofiler till att använda den nya baslinjeversionen utan att behöva återskapa och distribuera en ny baslinje från grunden. I Intune-konsolen kan du också visa information om varje baslinje, till exempel antalet enskilda profiler som använder baslinjen, hur många av de olika baslinjeversionerna som dina profiler använder och när den senaste versionen av en viss säkerhetsbaslinje släpptes.  Mer information finns i **Säkerhetsbaslinjer**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>Inställningen Använd säkerhetsnycklar för inloggning har flyttats<!-- 4501151 -->
Enhetskonfigurationsinställningen för identitetsskydd med namnet **Använd säkerhetsnycklar för inloggning** finns inte längre som en delinställning för att *Konfigurera Windows Hello för företag*. Nu är det en inställning på översta nivån som alltid är tillgänglig, även när du inte aktiverar användning av Windows Hello för företag. Mer information finns i [Identitetsskydd](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>Nya behörigheter för tilldelade gruppadministratörer<!-- 4504437   -->
Intunes inbyggda skoladministratörsroll har nu behörighet att skapa, läsa, uppdatera och ta bort (CRUD) tillstånd för hanterade appar. Uppdateringen innebär att om du är tilldelad som gruppadministratör i Intune for Education kan du nu skapa, visa, uppdatera och ta bort iOS MDM-pushcertifikat, iOS MDM-tokens och iOS VPP-token tillsammans med [alla befintliga behörigheter som du har](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Om du vill vidta någon av dessa åtgärder går du till **Klientinställningar** > **iOS**Enhetshantering.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Program kan använda Graph API för att anropa läsåtgärder utan användarautentiseringsuppgifter<!-- 4655885 -->
Program kan anropa Intune Graph API-läsåtgärder med appidentitet utan användarens autentiseringsuppgifter. Mer information om hur du kommer åt Microsoft Graph API för Intune finns i [Arbeta med Intune i Microsoft Graph.](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Använda omfångstaggar för appar i Microsoft Store för företag<!-- 4392555 -->
Du kan nu använda omfångstaggar för appar i Microsoft Store för företag. Mer information om omfångstaggar finns i [Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT](scope-tags.md).

## <a name="week-of-june-17-2019"></a>Veckan som inleds med 17 juni 2019

### <a name="app-management"></a>Apphantering

#### <a name="new-features-in-microsoft-intune-app"></a>Nya funktioner i Microsofts Intune-app
Vi har lagt till nya funktioner i Microsoft Intune-appen (förhandsversion) för Android. Användare på fullständigt hanterade Android-enheter kan nu  

* visa och hantera enheterna som de har registrerat genom Intune-företagsportalen eller Microsoft Intune-appen
* kontakta sin organisation för support
* skicka feedback till Microsoft
* visa villkor och bestämmelser, om sådana har angetts av deras organisation.

## <a name="week-of-june-10-2019"></a>Veckan som inleds med 10 juni 2019

### <a name="app-management"></a>Apphantering

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>Nya exempelappar som visar Intune SDK-integrering tillgänglig på GitHub<!-- 2653471 -->
GitHub-kontot msintuneappsdk har lagt till nya exempelprogram för iOS (Swift), Android, Xamarin.iOS, Xamarin Forms och Xamarin.Android. De här apparna är avsedda som komplement till vår befintliga dokumentation och visar hur du integrerar Intune APP SDK i dina egna mobilappar. Om du är apputvecklare och behöver ytterligare hjälp med Intune SDK hittar du fler exempel i de här länkarna:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) – en snabbmeddelandeapp för ursprungligt iOS-system (Swift) som använder Azure Active Directory Authentication Library (ADAL) för asynkron autentisering.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) – en att-göra-lista-app för ursprungligt Android-system som använder ADAL för asynkron autentisering.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) – en att-göra-lista-app för Xamarin.Android som använder ADAL för asynkron autentisering, den här lagringsplatsen har också Xamarin.Forms-appen.
- [Xamarin.iOS-exempelapp](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) – en Xamarin.iOS-exempelapp för barebonedatorer.

## <a name="week-of-may-27-2019"></a>Den vecka som börjar 27 maj 2019

### <a name="app-management"></a>Apphantering

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Rapportering för potentiellt skadliga appar på Android-enheter<!-- 4223162 -->
Intune tillhandahåller nu ytterligare rapporteringsinformation om potentiellt skadliga appar på Android-enheter. 

## <a name="week-of-may-20-2019"></a>Den vecka som börjar 20 maj 2019

### <a name="app-management"></a>Apphantering

#### <a name="windows-company-portal-app---3316993---"></a>Windows företagsportalapp<!-- 3316993 -->
Windows-företagsportalappen har nu en ny sida med etiketten **Enheter**. På sidan **Enheter** ser slutanvändare alla sina registrerade enheter. Användarna ser den här ändringen i företagsportalen när de använder version 10.3.4291.0 och senare. Mer information om hur du konfigurerar företagsportalen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>OrderID-attributet på Autopilot-enheter har bytt namn till Grupptagg <!-- 4659453 -->

För att göra det mer intuitivt har **OrderID**-attributets namn på Autopilot-enheter ändrats till **Grupptagg**. När du använder CSV-filer för att ladda upp Autopilot-enhetsinformation måste du använda Grupptagg som kolumnrubrik, inte OrderID.  

## <a name="week-of-may-13-2019-1905-service-release"></a>Veckan den 13 maj 2019 (1905 Service Release)

### <a name="app-management"></a>Apphantering

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Uppdatering av Intune-principers autentiseringsmetod och installation av företagsportalappen<!-- 1927359  -->
På enheter som redan har registrerats via Installationsassistenten med någon av Apples metoder för registrering av företagsenheter, stöder Intune inte längre företagsportalen om den installeras manuellt av slutanvändarna från App Store. Den här ändringen gäller endast när du autentiserar med Apple-installationsassistenten under registreringen. Den här ändringen påverkar också bara iOS-enheter som registrerats via:  
* Apple configurator

* Apple Business Manager

* Apple School Manager

* Apples program för enhetsregistrering (DEP)

Om användare installerar företagsportalappen från App store och sedan försöker att registrera enheterna genom den, får de ett felmeddelande. Dessa enheter kommer förväntas att bara använda företagsportalen när den har skickats automatiskt av Intune under registreringen. Profiler för registrering i Intune i Azure-portalen kommer att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Om du vill att dina DEP-enhetsanvändare ska ha företagsportalen behöver du ange dina preferenser i en registreringsprofil. 

Dessutom håller skärmen **Identifiera din enhet** i iOS-företagsportalen på att tas bort. Administratörer som vill aktivera villkorlig åtkomst eller distribuera företagsappar måste därför uppdatera profilen för DEP-registrering. Det här kravet gäller endast om DEP-registrering har verifierats med Installationsassistenten. I så fall måste du installera företagsportalen på enheten. För att göra det ska du välja **Intune** > **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram** > välja en token > **Profiler** > välja en profil > **Egenskaper** > och ställa in **Installera företagsportal** på **Ja**.

För att installera företagsportalen på redan registrerade DEP-enheter måste du gå till Intune > Klientappar och installera den som en hanterad app med konfigurationsprinciper för appar. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>Konfigurera hur användarna uppdaterar en affärsapplikation (LOB)-app med hjälp av en appskyddsprincip<!-- 3568384 -->
Du kan nu konfigurera var användarna kan få en uppdaterad version av en affärsapplikation (LOB). Slutanvändarna ser den här funktionen i dialogen för villkorlig start **Lägsta appversion**, där slutanvändarna uppmanas att uppdatera till en lägsta version av LOB-appen. Du måste ange denna uppdateringsinformation som en del av din LOB-appskyddsprincip (APP). Den här funktionen är tillgänglig för iOS och Android. På iOS kräver den här funktionen att appen integreras (eller packas in med hjälp av programhanteringsverktyget) med Intune SDK för iOS v. 10.0.7 eller senare. På Android kräver funktionen den senaste företagsportalen. Om du vill konfigurera hur en slutanvändare uppdaterar en LOB-app behöver appen en hanterad appkonfigurationspolicy som skickas till den med nyckeln, `com.microsoft.intune.myappstore`. Det skickade värdet anger vilket lager som slutanvändaren laddar ner appen från. Om appen distribueras via företagsportalen måste värdet vara `CompanyPortal`. Du måste ange en fullständig URL för andra lager.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>PowerShell-skript i Intune-hanteringstillägget<!-- 3734186  -->
Du kan konfigurera PowerShell-skript så att det körs med användarens administratörsprivilegier på enheten. Mer information finns i [Använda PowerShell-skript på Windows 10-enheter i Intune](../apps/intune-management-extension.md) och [Win 32-apphantering](../apps/app-management.md).

#### <a name="android-enterprise-app-management---4459905---"></a>Apphantering med Android Enterprise<!-- 4459905 -->
Intune lägger automatiskt till fyra vanliga Android Enterprise-relaterade appar till Intune-administratörskonsolen för att göra det enklare för IT-administratörer att konfigurera och använda Android Enterprise-hantering. Detta är de fyra Android Enterprise-apparna:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – Används för fullständigt hanterade Android Enterprise-scenarier.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – Hjälper dig att logga in på dina konton om du använder tvåfaktorautentisering.
- **[Intune-företagsportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – Används för appskyddsprinciper och scenarier med Android Enterprise-arbetsprofiler.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) – Används för dedikerade/helskärmslägesscenarier i Android Enterprise.

Tidigare var IT-administratörer tvungna att hitta och godkänna de här apparna manuellt i den [hanterade Google Play-butiken](https://play.google.com/store/apps) som en del av konfigurationen. Den här ändringen tar bort de tidigare manuella stegen för att göra det enklare och snabbare för kunder att använda Android Enterprise-hantering.

Administratörer kommer att se att dessa fyra appar läggs till i listan över appar i Intune automatiskt när de ansluter Intune-klienten till hanterade Google Play för första gången. Läs [Anslut ditt Intune-konto till ditt hanterade Google Play-konto](../enrollment/connect-intune-android-enterprise.md) för mer information. Administratörer behöver inte göra något för klienter som redan har anslutit sin klient eller som redan använder Android Enterprise. De fyra apparna visas automatiskt inom sju dagar efter slutförandet av tjänstlanseringen under maj 2019.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>Uppdaterat PFX-certifikatanslutningsprogram för Microsoft Intune<!-- 1533038 -->
Vi har släppt en uppdatering för [PFX-certifikatanslutningsappen för Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) som löser problemet där befintliga PFX-certifikat fortsätter att bearbetas, vilket orsakar att anslutningsappen slutar att bearbeta nya begäranden.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Intune-säkerhetsuppgifter för Defender ATP (i allmänt tillgänglig förhandsversion)<!-- 3208597 -->
Du kan använda Intune för att hantera [säkerhetsuppgifter för Microsoft Defender Advanced Threat Protection (ATP) i den allmänt tillgängliga förhandsversionen](../protect/atp-manage-vulnerabilities.md). Det här möjliggör integrering med ATP och lägger till en riskbaserad metod för att identifiera, prioritera och åtgärda säkerhetsrisker och felkonfigurationer på slutpunkter, samtidigt som det minskar tiden mellan identifiering till problemlösning.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671-----"></a>Söka efter en TPM-kretsuppsättning i en efterlevnadsprincip för Windows 10-enheter<!-- 3617671   -->
Många Windows 10-enheter och senare enheter har TPM-kretsuppsättningar (Trusted Platform Module). Den här uppdateringen innehåller en ny efterlevnadsinställning som kontrollerar versionen på TPM-chippet i enheten.

[Inställningar för kompatibilitetsprinciper i Windows 10 och senare](../protect/compliance-policy-create-windows.md#device-security) beskriver den här inställningen.

Gäller för: Windows 10 och senare

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>Förhindra slutanvändare från att ändra sin Internetdelning och inaktivera Siri-serverloggning på iOS-enheter<!-- 4097904   -->  
Du kan skapa en enhetsbegränsningsprofil på en iOS-enhet (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp). Den här uppdateringen innehåller nya inställningar som du kan konfigurera:

- **Inbyggda appar**: Loggning på serversidan av Siri kommandon
- **Trådlöst**: Användarmodifiering av internetdelning (endast övervakat)

Om du vill se de här inställningarna går du till [inbyggda app-inställningar för iOS](../configuration/device-restrictions-ios.md#built-in-apps) och [trådlösa inställningar för iOS](../configuration/device-restrictions-ios.md#wireless).

Gäller för: iOS 12.2 och senare

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>Nya inställningar för enhetsbegränsning i appen Klassrum för macOS-enheter<!-- 4097905   --> 
Du kan skapa profiler för enhetskonfiguration för macOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **macOS** för plattform > **Enhetsbegränsningar** för profiltyp). Den här uppdateringen innehåller nya inställningar för appen Klassrum, alternativet att blockera skärmbilder och inaktivera iCloud-bildbiblioteket.

Gå till [macOS-enhetsinställningar för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-macos.md) för att se de aktuella inställningarna.

Gäller för: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>iOS lösenordet för åtkomst till appbutiksinställningen har bytt namn<!-- 4557891  -->
Inställningen **Lösenord till appbutik** har bytt namn till **Kräv iTunes Store-lösenord för alla köp** (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel**).

Om du vill se de tillgängliga inställningarna går du till [iOS-inställningar för App Store, dokumentvisning, spel](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gäller för: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Baslinjer för Microsoft Defender Advanced Threat Protection (Förhandsversion)<!--  3754134 -->
Vi har lagt till en förhandsversion med säkerhetsbaslinje för [Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md)-inställningar. Denna baslinje finns tillgänglig när din miljö uppfyller förhandskraven för att använda [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Windows registreringsstatussida (ESP) är nu allmänt tillgänglig<!-- 3605348 -->
Registreringsstatussidan är inte längre en förhandsversion. Mer information finns i [Konfigurera en sida för registreringsstatus](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Uppdatering av användargränssnittet i Intune – Skapa Autopilot-registreringsprofil<!-- 4593669 -->
Användargränssnittet för att skapa en Autopilot-profil för registrering har uppdaterats så att den överensstämmer med Azures användargränssnitt. Mer information finns i [Skapa en Autopilot-registreringsprofil](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). Framöver kommer ytterligare Intune scenarier att uppdateras till det här nya användargränssnittet.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>Aktivera Autopilot-återställning av alla Windows-enheter<!-- 4225665 -->
Autopilot-återställning fungerar nu för alla Windows-enheter, även de som inte har konfigurerats för att använda registreringsstatussidan. Om en registreringsstatussida inte har konfigurerats för enheten under den första enhetsregistreringen kommer enheten att gå direkt till skrivbordet efter inloggningen. Det kan ta upp till åtta timmar att synkroniseras och visas som kompatibel i Intune. Mer information finns i [Återställa enheter med fjärransluten Windows Autopilot-återställning](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>Exakta IMEI-format krävs inte när du söker igenom alla enheter<!--30407680 -->
Du behöver inte ta med mellanslag i IMEI-nummer när du söker igenom **Alla enheter**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>Om du tar bort en enhet i Apples portal visas ändringen även i Intune-portalen<!--2489996 -->
Om en enhet tas bort från Apples program för enhetsregistrering eller Apple Business Manager-portalen tas den även automatiskt bort från Intune vid nästa synkronisering.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>Registreringsstatussidan spårar nu Win32-appar<!-- 2714451 -->
Detta gäller endast enheter som kör Windows 10, version 1903 och senare. Mer information finns i [Konfigurera en sida för registreringsstatus](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Enhetshantering

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Återställa och rensa enheter i grupp med hjälp av Graph API<!-- 3295288 -->
Du kan nu återställa och rensa upp till 100 enheter i grupp med Graph API.

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>Krypteringsrapport är inte längre en allmänt tillgänglig förhandsversion<!-- 4587546      -->
[Rapporten för kryptering av BitLocker och enheter](../protect/encryption-monitor.md) är nu allmänt tillgänglig och inte längre en del av förhandsversionen.

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Outlook-signatur och biometriska inställningar för iOS och Android-enheter<!-- 4050557 -->
Du kan nu ange om standardsignaturen är aktiverad i Outlook för iOS och Android-enheter. Dessutom kan du välja om du vill tillåta användare att ändra den biometriska inställningen i Outlook för iOS.

## <a name="week-of-may-6-2019"></a>Den vecka som börjar 6 maj 2019

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>Stöd för Network Access Control (NAC) för F5 Access för iOS-enheter<!-- 4500808 -->

F5 släppte en uppdatering för BIG-IP-13 som tillåter NAC-funktioner för F5 Access på iOS i Intune. Gör så här för att använda funktionen:

- Uppdatera BIG-IP till 13.1.1.5. BIG-IP 14 stöds inte.
- Integrera BIG-IP med Intune för NAC. Stegen i [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html) (Översikt: Konfigurera APM för enhetsstatuskontroller med slutpunktshanteringssystem).
- Aktivera inställningen **Aktivera nätverksåtkomstkontroll** i VPN-profilen i Intune.

Om du vill se den tillgängliga inställningen går du till [Konfigurera VPN-inställningar på iOS-enheter](../configuration/vpn-settings-ios.md).

Gäller för: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>Uppdaterat PFX-certifikatanslutningsprogram för Microsoft Intune<!-- doc-vso 1521237  -->  
Vi har släppt en uppdatering till [PFX-certifikatanslutningsappen för Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) som utelämnar avsökningsintervallet från 5 minuter till 30 sekunder.




## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
