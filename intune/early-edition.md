---
title: Tidig utgåva
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b6ca8108924c6c062da0d0ef56ab5b68635dd9ca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>Den tidiga utgåvan för Microsoft Intune – april 2018

Den **tidiga utgåvan** innehåller en lista med funktioner i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte denna information med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
>Följande ändringar är under utveckling för Intune. Mer information om nya hybridfunktioner finns på sidan med [nyheter om hybridfunktioner](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1804 start -->

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802--"></a>Nya Windows Defender Credential Guard-inställningar har lagts till i inställningarna för slutpunktsskydd<!--1102252 --><!--from 1802-->

Nya [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard)-inställningar kommer att läggas till i **Enhetskonfiguration** > **Profiler** > **Slutpunktsskydd**. Följande inställningar läggs till:

- Säkerhetsnivå för plattform: ange om säkerhetsnivå för plattform är aktiverat vid nästa omstart. Virtualiseringsbaserad säkerhet kräver Säker start. Virtualiseringsbaserad säkerhet kan också aktiveras med DMA-skydd (direkt minnesåtkomst). DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade.
- Virtualiseringsbaserad säkerhet: ange om virtualiseringsbaserad säkerhet är aktiverat vid nästa omstart.
- Windows Defender Credential Guard: slå på Credential Guard med virtualiseringsbaserad säkerhet för att skydda autentiseringsuppgifter vid nästa omstart när både säkerhetsnivå för plattform med säker start och virtualiseringsbaserad säkerhet är aktiverat. Bland de tillgängliga alternativen finns **Inaktiverad**, **Aktiverat med UEFI-lås**, **Aktiverat utan lås** och **Inte konfigurerad**.
  - Alternativet ”Inaktiverad” stänger av Credential Guard via fjärranslutning om det tidigare har slagits på med alternativet ”Aktiverat utan lås”.

  - Alternativet ”Aktiverat med UEFI-lås” ser till att Credential Guard inte kan inaktiveras med registernyckel eller via en grupprincip. Om du vill inaktivera Credential Guard när du har använt den här inställningen måste du ställa in gruppolicy på ”Inaktiverad” och ta bort säkerhetsfunktionerna från varje dator med en fysiskt närvarande användare för att rensa konfigurationen som finns kvar i UEFI. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.

  - Med alternativet ”Aktiverat utan lås” kan Credential Guard inaktiveras via fjärranslutning med grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 eller senare (version 1511).

  - Alternativet ”Inte konfigurerad” låter principinställningen vara odefinierad. Grupprincip skriver inte inställningar för principen till registret, så den har ingen påverkan på datorer eller användare. Om det finns en aktuell inställning i registret ändras den inte.

### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Lösenordsstöd för MAM PIN-kod på Android<!-- 1438086 -->

Intune-administratörer kommer att kunna ange ett programstartskrav för att framtvinga ett lösenord i stället för en numerisk MAM PIN-kod. Om det har konfigurerats behöver användaren ställa in och använda ett lösenord när han/hon uppmanas att göra det innan han/hon får åtkomst till MAM-integrerade program. Ett lösenord definieras som en numerisk PIN-kod med minst ett specialtecken eller en gemen/versal. Intune stöder lösenord på liknande sätt som numeriska PIN-koder. En minsta längd kan anges, vilket tillåter upprepning av tecken och sekvenser via administratörskonsolen. Den här funktionen kräver den senaste versionen av företagsportalen för Android. Funktionen finns redan tillgänglig för iOS.

###  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Blockera kamera och skärmbilder i Android for Work <!-- 1098977 eeready-->
Två nya egenskaper kommer att kunna blockeras när du konfigurerar enhetsbegränsningar för Android-enheter: 
- Kamera: Blockerar åtkomsten till alla kameror på enheten
- Skärmbild: Blockerar skärmbildtagning och förhindrar också att innehållet visas på enheter som inte har en säker videoutgång

Gäller Android for Work.

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Stöd för verksamhetsspecifika appar (LOB) för macOS <!-- 1473977 -->
I Microsoft Intune går det att installera branschspecifika macOS-appar från Azure Portal. Du kommer att kunna lägga till en branschspecifik macOS-app i Intune som redan har förbehandlats av verktyget i GitHub. I Azure Portal väljer du **Mobilappar** på bladet **Intune**. På bladet **Mobilappar** väljer du **Appar** > **Lägg till**. På bladet **Lägg till app** väljer du **Branschspecifik app**. 

### <a name="support-for-user-less-devices----1637553---"></a>Stöd för användarlösa enheter <!-- 1637553 -->
Intune stöder möjligheten att utvärdera efterlevnaden på en användarlös enhet som exempelvis Microsoft Surface Hub. Policyer för efterlevnad kan riktas mot specifika enheter. Det innebär att efterlevnad (och inkompatibilitet) kan fastställas för enheter som inte har någon associerad användare.

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Tillägg till inställningar av säkerhetsalternativ för lokal enhet <!-- 1403702 -->
Du kommer att kunna konfigurera ytterligare inställningar av säkerhetsalternativ för lokala Windows 10-enheter. Det kommer att finnas fler inställningar i Microsoft-nätverksklienten, Microsoft-nätverksservern, nätverksåtkomst och säkerhet, samt interaktiv inloggning. Inställningarna finns i kategorin Endpoint Protection när du skapar en princip för Windows 10-enhetskonfiguration.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Kräv installation av principer, appar, certifikat och nätverksprofiler <!-- 1553555 -->
Administratörer kommer att kunna blockera slutanvändarna från att komma åt skrivbordet i Windows 10 RS4 tills Intune har installerat principer, appar, certifikat och nätverksprofiler under etableringen av AutoPilot-enheter.

### <a name="rules-for-removing-devices----1609459---"></a>Regler för att ta bort enheter <!-- 1609459 -->
Det kommer att finnas nya regler som gör att du automatiskt kan ta bort enheter som inte har checkats in under ett visst antal dagar som du anger. Om du vill se den nya regeln går du till fönstret **Intune**, väljer **Enheter** och sedan **Regler för borttagning av enheter**.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Förhindra konsumentappar och funktioner för anpassad upplevelse i Windows 10 Enterprise RS4 AutoPilot-enheter<!-- 1621980 -->
Du kommer att kunna förhindra installationen av konsumentappar och funktioner för anpassad upplevelse på dina Windows 10 Enterprise RS4 AutoPilot-enheter. Om du vill se den här funktionen går du till **Intune** > **Enhetsregistrering** > **Windows-registrering** > **Windows AutoPilot-profiler** > **Skapa nytt** > **Registreringsinställningar**. 

### <a name="advanced-threat-protection-integrated-with-intune----1629303---"></a>Avancerat skydd har integrerats med Intune <!-- 1629303 -->
[Avancerat skydd (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) visar risknivån för Windows 10-enheter. När Intune utvärderar kompatibiliteten i Windows 10-enheter, ingår ATP-riskpoäng i utvärderingen. Du kan använda ATP med villkorlig åtkomst för att skydda ditt nätverk.

### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nya registreringssteg för användarna på enheter med macOS High Sierra 10.13.2+ <!--1734567 -->
I macOS High Sierra 10.13.2 finns nu begreppet ”Användargodkänd” MDM-registrering. I framtiden kan godkända registreringar tillåta att Intune hanterar vissa säkerhetskänsliga inställningar. Mer information finns i Apples supportdokumentation här: https://support.apple.com/HT208019.

Enheter som registreras med macOS-företagsportalen betraktas som ”Inte användargodkända” tills användaren öppnar systeminställningarna och ger sitt manuella godkännande. Därför dirigerar macOS-företagsportalen nu användare av macOS 10.13.2 och senare till att manuellt godkänna registreringen i slutet av registreringsprocessen. Intune-administratörskonsolen rapporterar om en registrerad enhet är användargodkänd.

### <a name="delete-autopilot-devices----1713650---"></a>Ta bort AutoPilot-enheter <!-- 1713650 -->
Intune-administratörer kommer att kunna ta bort AutoPilot-enheter.

### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Inbyggd apptilldelning av gruppen Alla användare och Alla enheter för Android for Work (AFW) <!-- 1813073 -->
Du kommer att kunna använda de inbyggda grupperna **Alla användare** och **Alla enheter** vid AFW-apptilldelning. Mer information finns i [Inkludera och exkludera apptilldelningar i Microsoft Intune](apps-inc-exl-assignments.md).

### <a name="improved-device-deletion-experience---1832333---"></a>Förbättrad enhetsborttagning <!--1832333 -->
Du kommer inte längre behöva ta bort företagets data eller fabriksåterställa en enhet innan du tar bort enheten från Intune.

Om du vill se den nya funktionen loggar du in på Intune och väljer **Enheter** > **Alla enheter** > namnet på enheten > **Ta bort**.

 Om du fortfarande vill att rensningen ska utföras kan du använda standardenhetens livscykel med hjälp av **Ta bort företagsinformation** och **Fabriksåterställning** innan du väljer **Ta bort**. 

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-profiler flyttas till en grupp som är riktad mot <!-- 1877935 -->
För närvarande kan AutoPilot-distributionsprofiler tilldelas till valda enheter. Fram till slutet av april gör du så här för att tilldela dessa profiler:
- Skapa grupper (Azure AD) som innehåller AutoPilot-enheter
- Tilldela önskade profiler till en Azure AD-grupp. AutoPilot-profilen kommer nu att tilldelas till AutoPilot-enheter i gruppen.

### <a name="play-sounds-on-ios-when-in-lost-mode----1629303---"></a>Spela upp ljud på iOS när den befinner sig i Borttappat läge <!-- 1629303 -->
När övervakade iOS-enheter är i hanteringen av mobilenheters (MDM) [Borttappat läge](device-lost-mode.md), kan du spela upp ett ljud (**Enheter** > **Alla enheter** > välj en iOS-enhet > **Översikt** > **Mer**). Ljudet fortsätter att spelas upp tills enheten tas bort från Borttappat läge, eller en användare stänger av ljudet. Gäller för iOS-enheter 9.3 och nyare.

### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Använda ett anpassat certifikatmottagarnamn på SCEP-certifikat <!-- 2064190 -->
Du kommer att kunna använda det egna namnet **OnPremisesSamAccountName** i en anpassad certifikatmottagare för en SCEP-certifikatprofil. Du kan till exempel använda `CN={OnPremisesSamAccountName})`.

### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Skicka diagnostikrapporter i företagsportalappen för macOS <!-- 2216677 -->
Företagsportalappen för macOS-enheter kommer att uppdateras, vilket ger en förbättring av hur användarna rapporterar Intune-relaterade fel. Från företagsportalappen kommer dina anställda kunna:
- Ladda upp diagnostikrapporter direkt till Microsofts utvecklingsteam.
- E-posta ett incident-ID till ditt företags IT-supportteam.

### <a name="always-on-vpn-for-windows-10---1333666---"></a>AlwaysOn-VPN för Windows 10 <!--1333666 -->

För närvarande kan [AlwaysOn](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) användas på Windows 10-enheter med hjälp av en anpassad VPN-profil (virtuellt privat nätverk) som skapats med OMA-URI.

Med den här uppdateringen kan administratörer aktivera AlwaysOn för VPN-profiler i Windows 10 direkt i Intune i Azure-portalen. VPN-profiler med AlwaysOn ansluts automatiskt när:

- Användarna loggar in på sina enheter
- Nätverket på enheten ändras
- Skärmen på enheten sätts på efter att ha varit avstängd

### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Förbättrade felmeddelanden när Apple MDM-pushcertifikat inte kan överföras <!-- 2172331 -->

Felmeddelandet säger att samma Apple-ID måste användas när du förnyar ett befintligt MDM-certifikat.

###  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Enhetens profildiagram och statuslista visar alla enheter i en grupp <!-- 1449153 eeready -->
När du konfigurerar en enhetsprofil (**Enhetskonfiguration** > **Profiler**) väljer du enhetsprofil, till exempel iOS. Du tilldelar profilen till en grupp med både iOS-enheter och enheter som inte är iOS. Antalet i det grafiska diagrammet visar att profilen tillämpas på både iOS-enheter *och* enheter som inte är iOS (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**). När du väljer det grafiska diagrammet på fliken **Översikt** visar **Enhetsstatus** alla enheterna i gruppen, i stället för enbart iOS-enheterna. 

Med den här uppdateringen visar det grafiska diagrammet (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**) endast antalet för den specifika enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för iOS-enheter, visar diagrammet endast antal iOS-enheter. Om du väljer det grafiska diagrammet och öppnar **Enhetsstatus**, visas endast iOS-enheterna.

När uppdateringen gjorts har det grafiska diagrammet tillfälligt tagits bort. 


<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Stöd för flera Exchange Connector <!-- 2070451 -->

Du kommer inte längre vara begränsad till en Exchange Connector per klient i Microsoft Intune. Intune stöder flera Exchange Connector, så du kan ställa in villkorlig åtkomst i Intune med flera lokala Exchange-organisationer.

Med en lokal Exchange Connector för Intune kan du hantera enhetsåtkomst till dina lokala Exchange-postlådor, baserat på om en enhet har registrerats i Intune och uppfyller Intunes enhetsefterlevnadsprinciper. Om du vill konfigurera ett anslutningsprogram laddar du ned den lokala Exchange Connector för Intune från Azure-portalen och installerar den på en server i Exchange-organisationen. På Microsoft Intune-instrumentpanelen väljer du **Lokal åtkomst** och under **Installation** väljer du sedan **Exchange ActiveSync Connector**. Ladda ned det lokala Exchange-anslutningsprogrammet och installera det på en server i din Exchange-organisation. Nu när du är inte längre begränsad till ett Exchange-anslutningsprogram per klient, och om du har ytterligare Exchange-organisationer, kan du följa samma process för att ladda ned och installera ett anslutningsprogram för varje ytterligare Exchange-organisation.

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>Stöd kommer för den nya Cisco AnyConnect-klienten för iOS <!-- 1333708 -->

Nya VPN-profiler som skapas för Cisco AnyConnect för iOS kommer att kunna användas med Cisco AnyConnect 4.0.7x och högre. Befintliga iOS Cisco AnyConnect VPN-profiler är märkta **Cisco Legacy AnyConnect** och kommer fortsatt att fungera med Cisco AnyConnect 4.0.5x som de gör i dag.

> [!NOTE]
> Den här ändringen gäller bara för iOS. Det finns fortfarande ett enda Cisco AnyConnect-alternativ för Android, Android for Work och macOS.

#### <a name="more-information"></a>Mer information

Du måste skapa en ny Cisco AnyConnect VPN-profil för iOS som stöd för den nya appen, eftersom de nya Cisco AnyConnect- och Cisco Legacy AnyConnect-apparna är olika appar. Om du hanterar AnyConnect-klienten i din miljö måste du även distribuera den nya Cisco AnyConnect-appen. När du slutför en uppgradering måste du också ta bort VPN-profilen Cisco Legacy AnyConnect och appen Cisco Legacy AnyConnect.

NAC-integration fungerar inte i den nya AnyConnect-klienten i den första utgåvan. Vi samarbetar med Cisco för att kunna erbjuda NAC-integration i en framtida version av Intune.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Möjlighet att distribuera nödvändiga verksamhetsspecifika appar till alla användare på Windows 10 Desktop-enheter <!-- 1627835 RS4 -->
Kunderna kommer att kunna distribuera nödvändiga verksamhetsspecifika appar för Windows 10 som kan installeras i enhetens sammanhang. Detta innebär att apparna blir tillgängliga för alla användare på enheten. Detta gäller endast för Windows 10 Desktop-enheter.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registreringen av företagsportalen har förbättrats <!-- 1874230-->
Användare som registrerar en enhet med hjälp av företagsportalen i Windows 10 version 1703 och senare, kommer att kunna slutföra det första steget i registreringen utan att lämna appen.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Uppdatera Hjälp och Feedback i företagsportalappen för Android <!--1631531 -->

Vi kommer att uppdatera Hjälp och Feedback i företagsportalappen för Android för att följa standarden för Android-appar. Vi kommer att uppdatera företagsportalappen för Android under de kommande månaderna för att dela upp **Hjälp och Feedback** och skilja på menykommandona **Hjälp** och **Skicka feedback**. På sidan **Hjälp** kommer det finnas ett avsnitt med **Vanliga frågor och svar** och **E-postsupport** som visar slutanvändarna hur de laddar upp loggar till Microsoft samt skickar e-post till företagssupporten och beskriver problemet. **Skicka feedback** vägleder användaren via Microsofts standardfeedback, som uppmanar användaren att välja ”Jag gillar det”, ”Jag tycker inte om det” eller ”Jag har en idé”.

<!-- 1802 start -->

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nya skrivarinställningar för utbildningsprofiler <!-- 1308900 -->

Fr utbildningsprofiler finns nya inställningar under kategorin **Skrivare**: **Skrivare**, **Standardskrivare**, **Lägg till nya skrivare**.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Appskyddsprinciper  <!-- 679615 -->
Intunes appskyddsprinciper ger dig möjligheten att skapa globala standardprinciper för att snabbt aktivera skydd för alla användare i hela klientorganisationen.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-webbplatser kan kräva appen Intune Managed Browser och ha stöd för enkel inloggning för Managed Browser (allmänt tillgänglig förhandsversion) <!-- 710595 -->   
Med Azure Active Directory (Azure AD) kan du begränsa åtkomst till webbplatser på mobila enheter till appen Intune Managed Browser. I Managed Browser förblir webbplatsdata säkra och separata från slutanvändarens personliga data. Dessutom stöder Managed Browser funktioner för enkel inloggning för webbplatser som stöds av Azure AD. När du loggar in på Managed Browser eller använder Managed Browser på en enhet med en annan app som hanteras av Intune, tillåts Managed Browser att få åtkomst till företagswebbplatser som skyddas av Azure AD utan att användaren måste ange sina autentiseringsuppgifter. Den här funktionen gäller för webbplatser som Outlook Web Access (OWA) och SharePoint Online, samt andra företags webbplatser som resurser i intranätet som nås via Azure App Proxy.




## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.


### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


