---
title: Tidig utgåva
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99b1436fdf718b54f54f7e90835668d4a632b7ce
ms.sourcegitcommit: 390a4be5aa36007c36fb6a5abcfe8d20bc862a4b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="the-early-edition-for-microsoft-intune---march-2018"></a>Den tidiga utgåvan för Microsoft Intune – mars 2018

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

### <a name="enhanced-jailbreak-detection----846515---"></a>Förbättrad upplåsningsidentifiering <!-- 846515 -->

Förbättrad upplåsningsidentifiering är en ny efterlevnadsinställning som förbättrar hur Intune utvärderar jailbreakade enheter. Inställningen medför att enheten checkar in till Intune oftare, vilket använder enhetens platstjänster och kan påverka batterianvändningen.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Möjlighet att distribuera nödvändiga verksamhetsspecifika appar till alla användare på Windows 10 Desktop-enheter <!-- 1627835 RS4 -->
Kunderna kommer att kunna distribuera nödvändiga verksamhetsspecifika appar för Windows 10 som kan installeras i enhetens sammanhang. Detta innebär att apparna blir tillgängliga för alla användare på enheten. Detta gäller endast för Windows 10 Desktop-enheter.

### <a name="expiring-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Utöka verksamhetsspecifika appar för Microsoft Intune <!-- 748789 -->
Intune meddelar dig i Azure-portalen när dina verksamhetsspecifika appar är på väg att upphöra att gälla. När du laddar upp en ny version av en verksamhetsspecifik app, tar Intune bort förfalloaviseringen från applistan.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registreringen av företagsportalen har förbättrats <!-- 1874230-->
Användare som registrerar en enhet med hjälp av företagsportalen i Windows 10 version 1703 och senare, kommer att kunna slutföra det första steget i registreringen utan att lämna appen.

### <a name="new-management-name-column----1333586---"></a>Ny kolumn för hanteringsnamn <!-- 1333586 -->
En ny kolumn med namnet **Hanteringsnamn** kommer att läggas till på enhetsbladet. Detta är ett automatiskt genererat, icke-redigerbart namn som tilldelas per enhet, baserat på följande formel:
- Standardnamn för alla enheter: <username>_<devicetype>_<enrollmenttimestamp>
- För masstillagda enheter: <PackageId/ProfileId>_<DeviceType>_<EnrollmentTime>

Det här är en valfri kolumn på enhetsbladet. Det är inte tillgängligt som standard och du har bara åtkomst till det via kolumnväljaren. Namnet på enheten påverkas inte av den här nya kolumnen.

### <a name="new-settings-for-windows-defender-security-center-notifications-device-configuration-profile----1631906---"></a>Nya inställningar i enhetskonfigurationsprofilen för Windows Defender Security Center (WDSC) <!-- 1631906 -->

Tre nya inställningar har lagts till i enhetskonfigurationsprofilen för Windows Defender Security Center (WDSC).

Administratörer kommer att kunna:

- Dölja identitetspelaren
- Dölja pelaren för maskinvara och dess underinställningar
- Dölja pelaren för utpressningstrojaner (filåterställning i Onedrive för företag)

När du döljer dessa pelare från WDSC-appen, kommer slutanvändarna inte kunna konfigurera dessa inställningar. Det innebär att inga meddelanden som är associerade med de dolda komponenterna kommer att genereras.

### <a name="mam-policies-targeted-based-on-management-state----1665993---"></a>MAM-principer riktas utifrån hanteringsstatus <!-- 1665993 -->

Du kommer att kunna rikta MAM-principer baserat på hanteringsstatus för enheten:

- **iOS-enheter** – Du kommer att kunna rikta ohanterade enheter (endast MAM) eller Intune-hanterade enheter.
- **Android-enheter** – Du kommer att kunna rikta ohanterade enheter, Intune-hanterade enheter och Intune-hanterade Android Enterprise-profiler (tidigare Android for Work).

### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459--"></a>Konfigurera Gatekeeper till att styra macOS-appens nedladdningskälla <!-- 1690459-->

Du kommer att kunna konfigurera Gatekeeper till att skydda dina enheter från appar genom att styra var apparna kan laddas ned från. Du kommer att kunna konfigurera följande nedladdningskällor: **Mac App Store**, **Mac App Store och identifierade utvecklare**, eller **Valfri plats**. Du kommer även att kunna konfigurera om användarna ska kunna installera en app med CTRL-klick för att åsidosätta dessa Gatekeeper-kontroller.

Inställningarna finns i **Enhetskonfiguration** -> **Skapa profil** -> **macOS** -> **Slutpunktsskydd**.

### <a name="configure-the-mac-application-firewall----1690461---"></a>Konfigurera brandväggen för Mac-program <!-- 1690461 -->

Du kommer att kunna konfigurera brandväggen för Mac-program. Du kan använda den för att styra anslutningar per program i stället för per port. Det gör det lättare att utnyttja brandväggsskyddet och förhindrar att oönskade appar tar kontroll över nätverksportar som är öppna för legitima appar.

Den här funktionen finns i **Enhetskonfiguration** -> **Skapa profil** -> **macOS** -> **Slutpunktsskydd**.

När du har aktiverat brandväggsinställningen kan du konfigurera brandväggen med hjälp av två olika metoder:

- Blockera alla inkommande anslutningar

   Du kan blockera alla inkommande anslutningar för de aktuella enheterna. Om du väljer att göra detta kommer inkommande anslutningar att blockeras för alla appar.

- Tillåta eller blockera specifika appar

   Du kan tillåta eller blockera specifika appar från att ta emot inkommande anslutningar. Du kan också aktivera hemligt läge för att förhindra svar på avsökningsbegäranden.

#### <a name="more-information"></a>Mer information

- Blockera alla inkommande anslutningar

   Detta hindrar alla delade tjänster (till exempel fildelning och delning av skärmen) från att ta emot inkommande anslutningar. Systemtjänster som fortfarande kan ta emot inkommande anslutningar är:
   - configd – Implementerar DHCP- och andra tjänster för nätverkskonfiguration
   - mDNSResponder – Implementerar Bonjour
   - racoon – Implementerar IPSec

   Om du vill använda delade tjänster kontrollerar du att **Inkommande anslutningar** är inställd på **Inte konfigurerad** (inte **Blockera**).

- Hemligt läge

   Aktivera detta om du vill förhindra att datorn svarar på avsökningsbegäranden. Datorn svarar fortfarande på inkommande begäranden för behöriga appar. Oväntade begäranden, till exempel ICMP (ping) ignoreras.


### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Uppdatera Hjälp och Feedback i företagsportalappen för Android <!--1631531 -->

Vi kommer att uppdatera Hjälp och Feedback i företagsportalappen för Android för att följa standarden för Android-appar. Vi kommer att uppdatera företagsportalappen för Android under de kommande månaderna för att dela upp **Hjälp och Feedback** och skilja på menykommandona **Hjälp** och **Skicka feedback**. På sidan **Hjälp** kommer det finnas ett avsnitt med **Vanliga frågor och svar** och **E-postsupport** som visar slutanvändarna hur de laddar upp loggar till Microsoft samt skickar e-post till företagssupporten och beskriver problemet. **Skicka feedback** vägleder användaren via Microsofts standardfeedback, som uppmanar användaren att välja ”Jag gillar det”, ”Jag tycker inte om det” eller ”Jag har en idé”.

### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Anpassade bokkategorier för volyminköpsprogram för e-böcker. <!-- 1488911 -->
Du kommer att kunna skapa anpassade e-bokkategorier och sedan tilldela e-böcker i volyminköpsprogram till dessa anpassade e-bokkategorier. Slutanvändarna kan sedan se de nyligen skapade e-bokkategorierna och böcker som tilldelats i kategorierna.

### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868--"></a>HoloLens och Surface Hub visas nu i enhetslistor <!--1725868-->

Vi lägger till stöd för att visa Intune-registrerade HoloLens- och Surface Hub-enheter i företagsportalappen för Android.

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Edge-mobilstöd för Intune-appskyddsprinciper <!-- 1817882 -->

Microsoft Edge-webbläsaren för mobila enheter stöder appskyddsprinciper som definierats i Intune.

### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763-eeready--"></a>Använd ett fullständigt unikt namn som ämne för SCEP-certifikatet <!--2221763 eeready-->
När du skapar en profil för SCEP-certifikat, anger du certifikatets ämnesnamn. Du kommer att kunna använda det fullständiga unika namnet som ämne. För **Ämnesnamn** väljer du **Anpassad** och sedan `CN={{OnPrem_Distinguished_Name}}`. Om du vill använda variabeln `{{OnPrem_Distinguished_Name}}` måste du synkronisera användarattributet `onpremisesdistingishedname` med hjälp av [Azure Active Directory (AD) Anslut](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) till din Azure AD.

### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837-eeready--"></a>iOS-enheter uppmanas att ange en PIN-kod var 15:e minut <!--1550837 eeready-->
När en efterlevnads- eller konfigurationsprincip används på en iOS-enhet, uppmanas användarna att ange en PIN-kod var 15:e minut. Användarna uppmanas kontinuerligt tills en PIN-kod anges.

### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983-eeready--"></a>Aktivera kontaktdelning med Bluetooth – Android for Work <!--1098983 eeready-->
Som standard förhindrar Android att kontakter i arbetsprofilen synkroniseras med Bluetooth-enheter. Därför visas inte arbetsprofilkontakter i uppringarens ID för Bluetooth-enheter.

Det kommer att finnas en ny inställning i **Android for Work** > **Enhetsbegränsningar** > **Arbetsprofilinställningar**:
- Dela kontakter via Bluetooth

Intune-administratören kan konfigurera dessa inställningar för att aktivera delning. Detta är användbart när du parar ihop en enhet med en bilbaserad Bluetooth-enhet som visar uppringarens ID vid handsfree-användning. När den är aktiverad visas arbetsprofilens kontakter. När den är inaktiverad visas inte arbetsprofilens kontakter.

Gäller för: Androids arbetsprofilenheter på Android OS v6.0 och nyare.

### <a name="schedule-your-automatic-updates---1805514---"></a>Schemalägga automatiska uppdateringar <!--1805514 -->

Intune ger dig kontroll vid installation av automatiska uppdateringar med hjälp av [Inställningar för Windows 10-uppdateringsring](windows-update-for-business-configure.md). Du kommer att kunna schemalägga återkommande uppdateringar, inklusive vecka, dag och tid.

### <a name="disable-checks-on-device-restart---1805490---"></a>Inaktivera kontroller vid omstart av enheten <!--1805490 -->

Med Intune kan du styra [hanteringen av programuppdateringar](windows-update-for-business-configure.md). Egenskapen **Omstartskontroller** kommer att läggas till och aktiveras som standard. Om du vill hoppa över de vanliga kontroller som utförs när du startar om en enhet (till exempel aktiva användare, batterinivå och så vidare) väljer du **Hoppa över**.

<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nytt trenddiagram för registreringsfel och tabell över felorsaker <!-- 1471783 -->

På Registreringsöversiktssidan, kommer du att kunna se trenden för registreringsfel och de fem viktigaste felorsakerna. Genom att klicka på diagrammet eller tabellen, kan du gå in på detaljnivå för att hitta felsökningstips och åtgärdsförslag.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Anpassa teman för företagsportalen med hexkoder <!--1049561 -->

Du kan anpassa temafärgen i företagsportalens appar med hexkoder. När du anger en hexkod kan Intune bestämma vilken textkod som ger den högsta kontrastnivån mellan textfärgen och bakgrundsfärgen per [WCAG 2.0-standarder](http://www.w3.org/TR/WCAG20). Du kan förhandsgranska både textfärgen och företagets logotyp mot färgen i **Mobilappar** > **Företagsportal**.

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Nya Windows Defender Credential Guard-inställningar har lagts till i inställningarna för skydd av slutpunkter<!--1102252 -->

Nya [Windows Defender Credential Guard] (https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] inställningar kommer att läggas till i **Enhetskonfiguration** > **Profiler** > **Slutpunktsskydd**. Följande inställningar läggs till:

- Säkerhetsnivå för plattform: ange om säkerhetsnivå för plattform är aktiverat vid nästa omstart. Virtualiseringsbaserad säkerhet kräver Säker start. Virtualiseringsbaserad säkerhet kan också aktiveras med DMA-skydd (direkt minnesåtkomst). DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade.
- Virtualiseringsbaserad säkerhet: ange om virtualiseringsbaserad säkerhet är aktiverat vid nästa omstart.
- Windows Defender Credential Guard: slå på Credential Guard med virtualiseringsbaserad säkerhet för att skydda autentiseringsuppgifter vid nästa omstart när både säkerhetsnivå för plattform med säker start och virtualiseringsbaserad säkerhet är aktiverat. Bland de tillgängliga alternativen finns **Inaktiverad**, **Aktiverat med UEFI-lås**, **Aktiverat utan lås** och **Inte konfigurerad**.
  - Alternativet ”Inaktiverad” stänger av Credential Guard via fjärranslutning om det tidigare har slagits på med alternativet ”Aktiverat utan lås”.

  - Alternativet ”Aktiverat med UEFI-lås” ser till att Credential Guard inte kan inaktiveras med registernyckel eller via en grupprincip. Om du vill inaktivera Credential Guard när du har använt den här inställningen måste du ställa in gruppolicy på ”Inaktiverad” och ta bort säkerhetsfunktionerna från varje dator med en fysiskt närvarande användare för att rensa konfigurationen som finns kvar i UEFI. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.

  - Med alternativet ”Aktiverat utan lås” kan Credential Guard inaktiveras via fjärranslutning med grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 eller senare (version 1511).

  - Alternativet ”Inte konfigurerad” låter principinställningen vara odefinierad. Grupprincip skriver inte inställningar för principen till registret, så den har ingen påverkan på datorer eller användare. Om det finns en aktuell inställning i registret ändras den inte.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Återställa lösenord för Android O-enheter <!-- 1238299 -->
Du kan återställa lösenorden för registrerade Android O-enheter. När du skickar en förfrågan om att ”återställa lösenord” till en Android O-enhet ställer den in ett nytt lösenord för upplåsning av enheten eller en hanterad profilutmaning till den aktuella användaren. Lösenordet eller utmaningen skickas baserat på om enheten har en profilägare eller enhetsägare, och träder i kraft omedelbart.

### <a name="local-device-security-option-settings----1251887---"></a>Inställningar för säkerhetsalternativ för lokal enhet <!-- 1251887 -->
Du kan aktivera säkerhetsinställningarna på Windows 10-enheter med de nya inställningarna för säkerhetsalternativ för den lokala enheten. Inställningarna finns i kategorin Endpoint Protection när du skapar en princip för Windows 10-enhetskonfiguration.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nya skrivarinställningar för utbildningsprofiler <!-- 1308900 -->

Fr utbildningsprofiler finns nya inställningar under kategorin **Skrivare**: **Skrivare**, **Standardskrivare**, **Lägg till nya skrivare**.

### <a name="ios-app-provisioning-configuration----1581650---"></a>Etableringskonfiguration för iOS-app <!-- 1581650 -->
Du kan tilldela iOS-apparetableringsprofiler för att förhindra att dina appar upphör genom att inkludera eller exkludera säkerhetsgrupper.

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nya Windows Defender Application Guard-inställningar <!-- 1631890 -->

- **Aktivera grafikacceleration**

Administratörer kan aktivera en virtuell grafikprocessor för Windows Defender Application Guard. Med den här inställningen kan processorn avlasta grafikåtergivning till vGPU. Detta kan förbättra prestanda när du arbetar med grafikintensiva webbplatser eller tittar på videor inuti behållaren.

- **SaveFilestoHost**

Administratörer kan aktivera att filer ska kunna skickas från Microsoft Edge som körs i behållaren så att de kan vara värdar för filsystem. Om du slår på det här kan användare ladda ned filer från Microsoft Edge i behållaren för att vara värd för filsystemet.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inklusive och exklusive apptilldelning baserat på grupperna för Android Enterprise <!-- 1813081 -->
Under apptilldelning och när du har valt tilldelningstyp stöder Android Enterprise (tidigare Android for Work) funktioner för undantag.

<!-- the following are present prior to 1802 -->

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ange mål för efterlevnadsprinciper för enheter i enhetsgrupperna <!--1307012 -->

Du kommer att kunna ange mål för efterlevnadsprinciper för användare i användargrupperna. Du kommer att kunna ange mål för efterlevnadsprinciper för enheter i användargrupperna.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Appskyddsprinciper  <!-- 679615 -->
Intunes appskyddsprinciper ger dig möjligheten att skapa globala standardprinciper för att snabbt aktivera skydd för alla användare i hela klientorganisationen.

### <a name="configure-an-ios-app-pin----1586774---"></a>Konfigurera PIN-kod för en iOS-app <!-- 1586774 -->
Du kommer snart att kunna kräva en PIN-kod för iOS-appar. Du kan konfigurera kravet på PIN-kod och förfallodatum i dagar via Azure Portal. När kravet är gäller måste en användare konfigurera och använda en ny PIN-kod innan de får åtkomst till en iOS-app. Endast iOS-appar som har appskydd aktiverat med Intune App SDK har stöd för den här funktionen.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-webbplatser kan kräva appen Intune Managed Browser och ha stöd för enkel inloggning för Managed Browser (allmänt tillgänglig förhandsversion) <!-- 710595 -->   
Med Azure Active Directory (Azure AD) kan du begränsa åtkomst till webbplatser på mobila enheter till appen Intune Managed Browser. I Managed Browser förblir webbplatsdata säkra och separata från slutanvändarens personliga data. Dessutom stöder Managed Browser funktioner för enkel inloggning för webbplatser som stöds av Azure AD. När du loggar in på Managed Browser eller använder Managed Browser på en enhet med en annan app som hanteras av Intune, tillåts Managed Browser att få åtkomst till företagswebbplatser som skyddas av Azure AD utan att användaren måste ange sina autentiseringsuppgifter. Den här funktionen gäller för webbplatser som Outlook Web Access (OWA) och SharePoint Online, samt andra företags webbplatser som resurser i intranätet som nås via Azure App Proxy.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>Omdirigera macOS-användare till den nya företagsportalappen <!--1380728-->   
När en slutanvändare loggar in på företagsportalens webbplats för att registrera sin macOS-enhet dirigeras de för att ladda ned den nya företagsportalappen för macOS och på så sätt slutföra processen. Det inträffar för macOS-enheter som använder OS X El Capitan 10.11 eller senare. 

<!-- the following are present prior to 1709 -->

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Förbättrat felmeddelande när en användare når det högsta antalet enheter som tillåts för registrering <!-- 1270370 -->
I stället för ett allmänt felmeddelande ser slutanvändare med Android-enheter ett vänligt felmeddelande med en åtgärd: ”You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin.” (Du har registrerat det högsta antalet enheter som IT-administratören tillåter. Ta bort en registrerad enhet eller be IT-administratören om hjälp.)



## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.



### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).
