---
title: Nyheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Ta reda på vad som är nytt i Intune Azure-portalen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/07/2020
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
ms.openlocfilehash: 7018e2ab4290219c752f44b4b391822438461e8e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415098"
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune

Läs mer om varje veckas nyheter i Microsoft Intune. Du kan också hitta [viktiga meddelanden](#notices), [tidigare versioner](whats-new-archive.md) och information om [hur uppdateringar av Intune-tjänsten släpps](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> Varje [månadsuppdatering](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) kan ta upp till tre dagar att distribuera och sker i följande ordning:
>
> - Dag 1: Asien och stillahavsområdet
> - Dag 2: Europa, Mellanöstern och Afrika
> - Dag 3: Nordamerika
> - Dag 4+: Intune för myndigheter
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
## <a name="week-of-february-10-2020"></a>Den vecka som börjar den 10 februari 2020

### <a name="windows-7-ends-extended-support---3042987--"></a>Utökad support för Windows 7 avslutas <!--3042987-->
Utökad support för Windows 7 avslutades den 14 januari 2020. Inaktuella Intunes stöd för enheter som kör Windows 7 avslutas på samma gång. Teknisk hjälp och automatiska uppdateringar som hjälper till att skydda din dator är inte längre tillgängliga. Du bör uppgradera till Windows 10. Mer information finns i blogginlägget [Planera för förändring](https://aka.ms/Windows7_Intune).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="microsoft-edge-version-77-and-later-on-windows-10-devices---5843584---"></a>Microsoft Edge version 77 och senare på Windows 10-enheter<!-- 5843584 -->
Intune stöder nu avinstallation av Microsoft Edge version 77 och senare på Windows 10-enheter. Mer information finns i [Lägga till Microsoft Edge för Windows 10 till Microsoft Intune](~/apps/apps-windows-edge.md).

#### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>En skärm har tagits bort från registreringen av Android-arbetsprofiler i företagsportalen<!--6103987 -->
Skärmen **Vad händer nu?** har tagits bort från registreringsflödet för Android-arbetsprofiler i företagsportalen för att effektivisera användarupplevelsen. Gå till [Registrera med Android-arbetsprofilen](/intune-user-help/enroll-device-android-work-profile) om du vill se det uppdaterade registreringsflödet för Android-arbetsprofiler.  

#### <a name="company-portal-app-improved-performance---6178652---"></a>Förbättrade prestanda för Företagsportal-appen<!-- 6178652 -->
Företagsportal-appen har uppdaterats för att ge stöd för förbättrade prestanda för enheter som använder ARM64-processorer, t.ex. Surface Pro X. Tidigare använde Företagsportal ett emulerat ARM32-läge. Nu kompileras Företagsportal-appen, i version 10.4.7080.0 och senare, internt för ARM64. Mer information om Företagsportal-appen finns i [Så här konfigurerar du Microsoft Intune-företagsportalsappen](~/apps/company-portal-app.md).

<!-- ########################## -->
## <a name="week-of-january-27-2020"></a>Veckan som börjar den 27 januari 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="intune-support-for-additional-microsoft-edge-version-77-deployment-channel-for-macos---5983950----"></a>Intune-stöd för ytterligare en Microsoft Edge version 77-distributionskanal för macOS<!-- 5983950  -->
Microsoft Intune har nu stöd för ytterligare en **Stabil** distributionskanal för Microsoft Edge-appen för macOS. Kanalen **Stabil** är den rekommenderade kanalen för att brett distribuera Microsoft Edge i företagsmiljöer. Den uppdateras var sjätte vecka, och varje utgåva innehåller förbättringar från **beta**kanalen. Förutom kanalerna **Stabil** och **Beta** så stöder Intune en **Dev**-kanal. Den offentliga förhandsversionen tillhandahåller stabila kanaler och dev-kanaler för Microsoft Edge version 77 och senare för macOS. Automatiska uppdateringar av webbläsaren är aktiverade som standard. Mer information finns i [Lägga till Microsoft Edge till macOS-enheter med hjälp av Microsoft Intune](~/apps/apps-edge-macos.md).

#### <a name="retirement-of-intune-managed-browser--5728447---"></a>Tillbakadragande av Microsoft Intune Managed Browser<!--5728447 -->
Intune Managed Browser kommer att dras tillbaka. Skydda din Intune-webbläsarupplevelse genom att använda Microsoft Edge. Mer information finns i posten [Vidta åtgärd: Skydda din Intune-webbläsarupplevelse genom att använda Microsoft Edge](~/fundamentals/whats-new.md#take-action-use-microsoft-edge-for-your-protected-intune-browser-experience) i avsnittet [Meddelanden](~/fundamentals/whats-new.md#notices) nedan.

<!-- ########################## -->
## <a name="week-of-january-20-2020-2001-service-release"></a>Veckan den 20 juli 2020 (tjänstversionen 2001)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="user-experience-change-when-adding-apps-to-intune---4705829-----"></a>Användarupplevelsen ändras när appar läggs till i Intune<!-- 4705829   -->
Du ser en ny användarupplevelse när du lägger till appar via Intune. De här funktionerna tillhandahåller samma inställningar och information som du har använt tidigare, men de nya funktionerna följer en guideliknande process innan en app läggs till i Intune. Den här nya funktionen tillhandhåller också en granskningssida innan appen läggs till. Välj **Appar** > **Alla appar** > **Lägg till** i [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Du hittar mer information i [Lägg till appar i Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----5622282-----"></a>Kräv att Win32-appar startas om <!-- 5622282   -->
Du kan kräva att en Win32-app måste startas om efter det att den har installerats. Du kan också välja hur lång tid (respitperiod) det ska ta innan omstarten måste ske.

#### <a name="user-experience-change-when-configuring-apps-in-intune---4207990-----"></a>Användarupplevelsen ändras när appar konfigureras i Intune<!-- 4207990   -->
En ny användarupplevelse uppstår när du skapar appkonfigurationsprinciper i Intune. De här funktionerna tillhandahåller samma inställningar och information som du har använt tidigare, men de nya funktionerna följer en guideliknande process innan en policy läggs till i Intune. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Appar** > **Appkonfigurationsprinciper** > **Lägg till**. Mer information finns i [Appkonfigurationsprinciper för Microsoft Intune](~/apps/app-configuration-policies-overview.md). 

#### <a name="intune-support-for-additional-microsoft-edge-for-windows-10-deployment-channel---5861774---"></a>Intune-stöd för ytterligare en distributionskanal för Microsoft Edge för Windows 10<!-- 5861774 -->
Microsoft Intune har nu stöd för ytterligare en **Stabil** distributionskanal för Microsoft Edge-appen (version 77 och senare) för Windows 10. Kanalen **Stabil** är den rekommenderade kanalen för att brett distribuera Microsoft Edge för Windows 10 i företagsmiljöer. Den här kanalen uppdateras var sjätte vecka, och varje utgåva innehåller förbättringar från **Beta**-kanalen. Förutom kanalerna **Stabil** och **Beta** så stöder Intune en **Dev**-kanal. Mer information finns i [Microsoft Edge för Windows 10 – konfigurera appinställningar](~/apps/apps-windows-edge.md#configure-app-settings).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="improved-user-interface-experience-when-configuring-exchange-activesync-on-premises-connector-ui---5695492-----"></a>Förbättrad användargränssnittsupplevelse när användargränssnittet för den lokala Exchange ActiveSync-anslutningsappen konfigureras<!-- 5695492   -->
Vi har uppdaterat funktionen för att [konfigurera den lokala Exchange ActiveSync-anslutningsappen](../protect/exchange-connector-install.md). Den uppdaterade upplevelsen använder ett enda fönster för att konfigurera, redigera och sammanfatta information om dina lokala anslutningsappar. 

#### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-----"></a>Lägg till automatiska proxyinställningar i Wi-Fi-profiler för Android Enterprise-arbetsprofiler<!-- 4490822   -->
Du kan skapa Wi-Fi-profiler på Android Enterprise-arbetsprofilenheter. När du väljer Wi-Fi-företagstypen kan du också ange den EAP-typ (Extensible Authentication Protocol) som används i ditt Wi-Fi-nätverk.

Nu när du väljer företagstyp kan du också ange automatiska proxyinställningar, inklusive en proxyserver-URL, som exempelvis `proxy.contoso.com`.

Om du vill se vilka aktuella Wi-Fi-inställningar som du kan konfigurera, så gå till [Lägga till Wi-Fi-inställningar för enheter som kör Android Enterprise och Android Kiosk i Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Gäller för:
- Android Enterprise-arbetsprofil

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="block-android-enrollments-by-device-manufacturer--5197392----"></a>Blockera Android-registreringar efter enhetstillverkare<!--5197392  -->
Du kan blockera enheter från att registreras baserat på deras tillverkare. Detta gäller för Android-enhetsadministratörs- och Android Enterprise-arbetsprofilsenheter. Om du vill se registreringsbegränsningar, så gå till [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Enheter** > **Registreringsbegränsningar**.

#### <a name="improvements-to-the-iosipados-create-enrollment-type-profile-ui---6055005---"></a>Förbättringar av iOS/iPad-gränssnittet för att skapa registreringstypsprofil<!-- 6055005 -->
För användarregistrering i iOS/iPad så har sidan **Skapa registreringstypsprofil** **Inställningar** anpassats för att förbättra processen att välja **Registreringstyp** samtidigt som du behåller samma funktioner. Om du vill se det nya användargränssnittet går du till sidan [Administrationscenter för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Enheter** > **iOS** > **iOS-registrering** > **Registreringstyper** > **Skapa profil** > **Inställningar**. Mer information finns i [Skapa en Användarregistreringsprofil i Intune](../enrollment/ios-user-enrollment.md#create-a-user-enrollment-profile-in-intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Enhetshantering

#### <a name="new-information-in-device-details---4471759-5604099----"></a>Ny enhetsinformation<!-- 4471759 5604099  -->
Följande information finns nu på sidan **Översikt** för enheter:
- Minneskapacitet (mängden fysiskt minne på enheten)
- Minneskapacitet (mängden fysisk lagring på enheten) 
- CPU-arkitektur


#### <a name="ios-bypass-activation-lock-remote-action-renamed-to-disable-activation-lock---5904591----"></a>iOS-fjärråtgärden Kringå aktiveringslås har bytt namn till att Inaktivera aktiveringslås <!--5904591  -->
Fjärråtgärden **Kringå aktiveringslås** har bytt namn till **Inaktivera aktiveringslås**. Mer information finns i [Inaktivera iOS-aktiveringslås med Intune](../remote-actions/device-activation-lock-bypass.md).

#### <a name="windows-10-feature-update-deployment-support-for-autopilot-devices---5948137-----"></a>Stöd för distribution av funktionsuppdateringar i Windows 10 för Autopilot-enheter<!-- 5948137   -->
Intune har nu stöd för registrerade Autopilot-enheter genom [distribution av funktionsuppdateringar i Windows 10](../protect/windows-update-for-business-configure.md#windows-10-feature-updates).

Policyer för funktionsuppdateringar för Windows 10 kan inte tillämpas samtidigt som Autopilot-välkomstprogrammet körs och tillämpas endast vid den första Windows Update-genomsökningen när en enhet har etablerats färdigt (detta tar vanligtvis en dag).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="windows-autopilot-deployment-reports-preview----3856172-----"></a>Windows Autopilot-distributionsrapporter (förhandsversion) <!-- 3856172   -->
En ny rapport innehåller information om varje enhet som distribueras via Windows Autopilot. Mer information finns i [distributionsrapporten för Autopilot](../enrollment/enrollment-autopilot.md#autopilot-deployments-report).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-----"></a>Ny inbyggd roll i Intune för slutpunktssäkerhetshantering<!--4253397   -->
En ny inbyggd roll i Intune är tillgänglig: slutpunktssäkerhetshantering. Den här nya rollen ger administratörer fullständig åtkomst till slutpunktshanterarnoden i Intune och läsåtkomst till andra områden. Rollen är en utökning av rollen Säkerhetsadministratör från Azure AD. Om du för närvarande bara har globala administratörer som roller behövs inga ändringar. Om du använder roller och du vill ha den granularitet som Endpoint Security Manager tillhandahåller, tilldelar du sedan rollen när den är tillgänglig. Mer information om inbyggda roller finns i [Rollbaserad åtkomstkontroll](role-based-access-control.md).

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>Veckan som börjar den 6 januari 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>S/MIME-stöd för Microsoft Outlook för iOS<!-- 2669398 -->
Intune stöder leverans av S/MIME-signering och -krypteringscertifikat som kan användas med Outlook för iOS på iOS-enheter. Mer information finns i avsnittet om [känslighetsetiketter och skydd i Outlook för iOS och Android](https://aka.ms/omsmime).

#### <a name="cache-win32-app-content-using-microsoft-connected-cache-server---6030314---"></a>Cachelagra Win32-appinnehåll med en Microsoft-ansluten cacheserver<!-- 6030314 -->
Du kan installera en Microsoft-ansluten cacheserver på dina Configuration Manager-distributionsplatser om du ska cachelagra Intune Win32-appinnehåll. Mer information finns i [Microsoft-ansluten cache i Configuration Manager – Support för Intune Win32-appar](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="windows-10-administrative-templates-admx-profiles-now-support-scope-tags---5137390---"></a>Profiler för administrativa mallar för Windows 10 (ADMX) stöder nu omfångstaggar <!--5137390 -->
Nu kan du tilldela administrativa mallprofiler (ADMX) omfångstaggar. Det gör du genom att gå till **Intune** > **Enheter** > **Konfigurationsprofiler** > välja en profil för administrativa mallar i listan > **Egenskaper** > **Omfångstaggar**. Mer information om omfångstaggar finns i [Tilldela andra objekt omfångstaggar](../fundamentals/scope-tags.md#assign-scope-tags-to-other-objects).

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>Veckan som börjar med 30 december 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Apphantering

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Hämta personlig återställningsnyckel från MEM-krypterade macOS-enheter<!-- 4851745 -->
Slutanvändarna kan hämta sin personliga återställningsnyckel (FileVault Key) med hjälp av iOS-företagsportalappen. Den enhet som har den personliga återställningsnyckeln måste registreras med Intune och krypteras med FileVault via Intune. Med hjälp av iOS-företagsportalappen kan en slutanvändare hämta sin personliga återställningsnyckel på sin krypterade macOS-enhet genom att klicka på **Hämta återställningsnyckel**. Du kan också hämta återställningsnyckeln från Intune genom att välja **Enheter** > *den krypterade och registrerade macOS-enheten* > **Hämta återställningsnyckel**. Mer information om FileVault finns i [FileVault-kryptering för macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

#### <a name="ios-and-ipados-user-licensed-vpp-apps---5619268---"></a>Användarlicenserade VPP-appar för iOS och iPadOS<!-- 5619268 -->
För användarregistrerade iOS- och iPadOS-enheter visas inte längre nyskapade enhetslicenserade VPP-program som tillgängliga för slutanvändare. Slutanvändare kommer dock fortfarande att se alla användarlicensierade VPP-appar inom företagsportalen. Mer information om VPP-appar finns i [Så här hanterar du iOS- och macOS-appar som köpts genom ett Apples volymköpsprogram med Microsoft Intune](~/apps/vpp-apps-ios.md).

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

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352------"></a>Vi har uppdaterat två enhetsbegränsningsinställningar för iOS-och iPad-enheter för att åtgärda deras beteende<!-- 5701352    -->
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

> [!NOTE]
> PKCS-certifikatprofiler stöds inte med Wi-Fi-profiler. Använd i stället SCEP-certifikatsprofiler när du använder en [EAP-typ](../configuration/wi-fi-settings-windows.md#enterprise-profile).

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
Configuration Manager-kunder med Software Assurance kan få Intune-samhantering för Windows 10-datorer utan att behöva köpa ytterligare en Intune-licens för samhantering. Kunderna behöver inte längre tilldela enskilda Intune/EMS-licenser till sina slutanvändare för samhantering av Windows 10.
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

## <a name="whats-new-archive"></a>Nyhetsarkiv
Information om tidigare månader finns i [Nyhetsarkiv](whats-new-archive.md).

## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
