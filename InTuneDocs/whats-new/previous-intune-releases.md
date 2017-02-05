---
title: Tidigare versioner | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0e4d08c4fd66bb1ae3fe683db503915725bc3134
ms.openlocfilehash: 5f09c46e7dcd5aabc603838ce60a1e8e7fed694e


---

# <a name="previous-intune-releases"></a>Tidigare versioner av Intune

Den här sidan är en lista över de senaste meddelandena i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).

[!INCLUDE[wit_nextref](../includes/whats-new-last-six-months.md)]

## <a name="june-2016"></a>Juni 2016
### <a name="intune-service-health"></a>Hälsotillstånd för Intune-tjänsten
Information om Intune-tjänstens hälsotillstånd har nu flyttats till en central plats med andra Microsoft-tjänster. Nu finns den här informationen i under Tjänstens hälsa i Office 365-hanteringsportalen. Mer information finns i [det här blogginlägget](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Apphantering
- **Förbättrad konfigurationsmiljö för Windows 10-företagsdataprinciper.** Vi har gjort förbättringar i konfigurationsupplevelsen för Windows 10- företagsdatapolicyn när det gäller att skapa regler för program, specificera nätverksgränsdefinitioner och andra inställningar för företagsdataskydd. Läs mer i [Skapa en princip för företagsdataskydd (EDP) med Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### <a name="device-management"></a>Enhetshantering
- **Windows Defender-principinställning för att skydda mot potentiellt oönskade appar.** En ny Windows Defender-inställning som kallas **identifiering av potentiellt oönskade program** har lagts till i den allmänna konfigurationsprincipen för Windows 10 Desktop och Mobile. Du kan använda den här inställningen för att skydda registrerade stationära Windows-datorer från att köra program som Windows Defender har klassificerat som potentiellt oönskade. Du kan skydda dig mot att dessa program körs eller använda granskningsläget för att rapportera att ett potentiellt oönskat program har installerats. Mer information finns i [Principinställningar för Windows 10 i Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### <a name="conditional-access"></a>Villkorlig åtkomst
- **Cisco ISE-kontrollprinciper för nätverksåtkomst för Intune.**  Kunder som använder Cisco Identity Service Engine (ISE) 2.1 och även använder Microsoft Intune kan ange en princip för nätverksåtkomst i ISE.

    Med den här principen måste enheter som ansluter till nätverket med hjälp av Wi-Fi eller VPN uppfylla följande villkor innan de tillåts åtkomst:

    * Måste hanteras av Intune
    * Måste vara kompatibla med alla distribuerade efterlevnadsprinciper för Intune

 Användare med icke kompatibla enheter uppmanas att registrera sig och åtgärda eventuella efterlevnadsproblem för att få åtkomst.
- **Villkorlig åtkomst för webbläsare.** Du kan skapa en princip för villkorlig åtkomst för [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) och [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) så att programmen bara kan användas från webbläsare som stöds i hanterade och godkända iOS- och Android-enheter. Användare som försöker logga in till Outlook Web Access (OWA) och SharePoint-webbplatser med iOS- och Android-enheter uppmanas att registrera sina enheter med Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS 1175844--->

- **Dynamics CRM Online stöder villkorlig åtkomst.** Du kan skapa en princip för villkorlig åtkomst för [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) så att det bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Slutanvändare som försöker logga in i mobilappen för Dynamics CRM på iOS och Android uppmanas att registrera sig i Intune samt åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Uppdateringar av Intune-företagsportalen

__Android-företagsportalappen__

- När IT-administratörer använder den nya principen ”Kräv att enheter förhindrar installation av appar från okända källor (Android 4.0+)” visas meddelandet ”Installation från okända källor måste inaktiveras” i enheter med Android 4.0 eller senare. Användare måste välja **Inställningar** > **Säkerhet**, och inaktivera **Okända källor**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) om meddelandet och varför användaren måste inaktivera inställningen.

- När IT-administratörer använder den nya principen ”Kräv att ”Genomsök enhet efter säkerhetshot" (Android 4.0+) är aktiverat på enheter” visas meddelandet ”Genomsök enhet efter säkerhetshot” i enheter med Android 4.0 eller senare. Användarna måste välja **Inställningar** > **Google** > **Säkerhet** och aktivera **Genomsök enhet efter säkerhetshot**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) om meddelandet och varför användaren måste aktivera inställningen.

- När IT-administratörer använder den nya principen ”Kräv att USB-felsökning är inaktiverat (Android 4.2+)” visas meddelandet ”USB-felsökning måste inaktiveras” i enheter med Android 4.2 eller senare. Användarna måste välja **Inställningar** > **Utvecklaralternativ** och inaktivera **USB-felsökning**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) om meddelandet och varför användaren måste inaktivera inställningen.

- När IT-administratörer använda nya principen ”Lägsta Android-säkerhetskorrigeringsnivå (Android 6.0+)” visas meddelandet ”Den här enheten motsvarar inte miniminivån för Android-säkerhetskorrigering” i enheter med Android 6.0 eller senare. Användarna måste installera den nödvändiga säkerhetskorrigeringen. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) om hur den nödvändiga säkerhetskorrigeringen installeras och vilken säkerhetskorrigering som redan finns installerad.

__iOS-företagsportalappen__

- Appinstallationen har förbättrats för slutanvändare som installerar affärsspecifika appar. Om appinstallationen tar lång tid kan användarna synkronisera sina enheter manuellt för att tvinga synkroniseringen att fortsätta. Instruktioner för slutanvändaren finns i [Synkronisera din iOS-enhet manuellt](/Intune/EndUser/sync-your-device-manually-ios).

- Microsoft Intunes-företagsportalappen för iOS har uppdaterats med stöd till iOS version 8.0 och senare. Uppdateringen innebär att slutanvändare bara kan installera företagsportalappen och registrera nya enheter i Intune om enheten kör iOS version 8.0 eller senare. Användare som redan har registrerat enheter som körs på en iOS-version som inte stöds, kan fortsätta använda den företagsportalapp som finns på enheten.

## <a name="may-2016"></a>Maj 2016
Alla dessa funktioner stöds även för hybriddistributioner (Configuration Manager med Intune). Mer information om nya hybridfunktioner finns på sidan med [nyheter om hybridfunktioner](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### <a name="documentation"></a>Dokumentation
Välkommen till förhandsversionen av [docs.microsoft.com](https://docs.microsoft.com/en-us/intune)!
Det här är en helt ny modern innehållsplattform som har tagits fram för att göra det enklare för våra kunder att förstå och använda Intune.
Mer information om alla de nya funktionerna finns i [Introduktion till docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### <a name="intune-service-health"></a>Hälsotillstånd för Intune-tjänsten
Information om Intune-tjänstens hälsotillstånd har nu flyttats till en central plats med andra Microsoft-tjänster. Nu hittar du den här informationen under **Tjänstens hälsa** i [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx).
Mer information finns i [det här blogginlägget](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Apphantering
- **MAM SDK: Stöd för konfiguration av PIN-kodens längd.** Du kan ange längden på PIN-koden för MAM-appar på samma sätt som PIN-koden för en enhet. Detta innebär att slutanvändaren måste uppfylla de nya begränsningar som du anger. Användaren ser en lite annorlunda PIN-skärm som är anpassad till den längre inmatningen. Mer information finns i [MAM-principinställningar för Android](/intune/deploy-use/android-mam-policy-settings) och [MAM-principinställningar för iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype för företag för iOS och Android.** Nu kan du använda Skype för företag med [MAM utan registreringsprinciper](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). När användarna loggar in tillämpas MAM-principerna.

- **Nya appar är tillgängliga för hantering med MAM-principer.** Microsoft Word-, Excel- och PowerPoint-appar för Android kan nu associeras med MAM-principer på enheter som inte har registrerats med Intune. Om du vill se en fullständig lista över appar som stöds kan du gå till Microsoft Intune-galleriet för mobilprogram på sidan för [Microsoft Intune-programpartner](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


### <a name="company-portal-updates"></a>Uppdateringar av företagsportalen

#### <a name="android-company-portal-app"></a>Android-företagsportalsapp
- **Popup-meddelanden för slutanvändare**: Slutanvändarna ser nu popup-meddelandena från Android-företagsportalappen när de registrerar eller tar bort enheter från företagsportalen.

- **Ändringar i kontona för Enhetsregistreringshanterare i Android-företagsportalappen.** I syfte att förbättra prestanda och skalning visar Intune inte längre alla enheter i enhetsregistreringshanteraren i fönstret Mina enheter Android-företagsportalappen. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen.

#### <a name="company-portal-website"></a>Företagsportalens webbplats
- **Webbplatsen för företagsportalen: En banderoll för enhetsidentifikation visar mer information för slutanvändaren.** Slutanvändarna kan nu enkelt identifiera den enhet de har valt när de använder företagsportalens webbplats. Om fel enhet har valts kan de välja rätt enhet genom att trycka på länken **Tryck här** på banderollen på startsidan.

### <a name="service-deprecation"></a>Tjänstens utfasning
- **Intune Viewer-appar.** Med versionen av den nya RMS-delningsappen tar vi bort följande Intune Viewer-appar, med början från augusti 2016:
    - Intune AV Viewer
    - Intune PDF Viewer
    - Intune Image Viewer för Android från Google Play

  I stället för att använda Intune Viewer-appar bör du använda den nya Rights Management-appen (RMS-delning) för Android, där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. Läs mer om RMS-delningsappen (med länk till dokumentationen).

- **Borttagning av anpassade meddelanderegler för specifika grupper.**
Intune-meddelanderegler används för att definiera vem en e-postavisering ska skickas till från Intune. För närvarande kan du konfigurera meddelanderegler för att skicka e-post till alla användare av enheter i en Intune-enhetsgrupp som du har skapat. Från och med den 1 juni 2016 eller däromkring kommer det inte längre att finnas stöd för att rikta sig till användarskapade grupper.

    Om du vill rikta en meddelanderegel till en grupp som du har skapat via Microsoft Intune-administrationskonsolen skulle du i dag utföra följande steg:

    Gå till **Admin**-arbetsytan och klicka på **Meddelanderegler** > **Skapa ny regel**

    Välj de enhetsgrupper som regeln ska gälla för i steg två i guiden Skapa meddelanderegel. Det här steget, Välj enhetsgrupper, håller på att fasas ut från Intune-konsolen.

    Den preliminära tidslinjen för den här ändringen ser ut som följer:
    - Från och med juni 2016 kan nya klienter inte se steg två i guiden Skapa meddelanderegel. Befintliga klienter påverkas inte.
    - Runt augusti 2016 kommer vissa befintliga klienter inte att se kommandot för att välja enhetsgrupper i guiden.
    - Runt oktober 2016 planerar vi för att samtliga klienter inte kommer att se kommandot för att välja enhetsgrupper i guiden.


- **Ändringar i stödet för iOS-företagsportalappen**. Under de kommande månaderna kommer det en uppdatering för Microsoft Intune-företagsportalappen för iOS som bara har stöd för enheter som kör iOS 8.0 eller senare. Användarna kan inte registrera nya enheter som kör versioner under iOS 8.0. Registrerade enheter som kör versioner under iOS 8.0 fortsätter att hanteras och kommer under en begränsad tid att kunna fortsätta använda företagsportalappen. Enheterna måste dock ha version iOS 8.0 eller senare installerad för att få åtkomst till den senaste versionen av företagsportalappen. Vi rekommenderar att du meddelar användarna om att de bör uppdatera till iOS 8.0 eller senare för att kunna dra full nytta av nya funktioner i Intune.  


## <a name="april-2016"></a>April 2016
Alla dessa funktioner stöds även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune).

### <a name="app-management"></a>Apphantering
- **MAM-efterlevnad.**
Nu kan du visa [statusen](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune) för dina programhanteringsprinciper för alla användare i din Azure Active Directory-klientorganisation (AAD). Du måste bland annat:
   - Egenskaper
   - Appar på enheten

   Statusvärden:

   **Incheckad**: Anger att principen distribuerades till användaren, att appen har använts i arbetskontexten och att principen har tillämpats.

    **Inte incheckad**: Anger att principen distribuerades till användaren, men att appen inte har använts i arbetskontexten sedan dess.


- **MAM-kontroller för att förhindra att Outlook-kontakter synkroniseras (Android).**
En ny inställning är tillgänglig för [hantering av mobila program](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) utan enhetsregistrering. Med den här inställningen kan du förhindra att ett program synkroniserar kontakter till den interna adressboken på Android-enheter. Om den här inställningen är aktiverad kan berörda program inte längre spara kontakter i den interna adressboken. Om den här inställningen är inaktiverad kan berörda program spara kontakter i den interna adressboken. När du [fjärraderar en enhet eller app](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune) tas kontakter som redan har sparats i den interna adressboken bort. Den här nya inställningen stöds av Outlook på Android-enheter.

### <a name="device-management"></a>Enhetshantering
- **Identifiering av telefonnummer för företagsägda enheter.** Telefoner kategoriserade som ”företagsägda” identifieras nu med sina fullständiga telefonnummer, t.ex. när du kör en inventeringsrapport för mobila enheter. BYOD-telefonnummer döljs fortfarande med ***, och bara de fyra sista siffrorna visas.


### <a name="company-portal-updates"></a>Uppdateringar av företagsportalen
**Android-företagsportalappen** Användare som inte har registrerat sin enhet i Intune och som inte har rätt certifikat installerat kan inte logga in på företagsportalappen för Android och får se meddelandet ”Du kan inte logga in eftersom enheten saknar ett obligatoriskt certifikat”. Meddelandet innehåller länken ”Så här löser du problemet” som användarna kan trycka på för att visa installationsanvisningar för certifikatet. Om du vill se de steg som slutanvändarna går igenom för att lösa problemet, se [Enheten saknar ett nödvändigt certifikat](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

Stöd för **iOS-företagsportalappen** har lagts till för dra-för-att-uppdatera-uppdateringsåtgärden för att uppdatera innehållet på startsidan, vilket innefattar de listade apparna, listade enheter och IT-kontaktuppgifterna. Den här åtgärden kontrollerar inte kompatibiliteten eller principinformation, vilket du kan göra genom att välja panelen för din aktuella enhet och trycka på knappen **Synkronisera**.

**Företagsportalappen för Windows 10 Mobile och Windows Phone 8.1** När slutanvändarna installerar branschspecifika appar får du nu en förbättrad programinstallationsupplevelse. Om appinstallationen tar lång tid kan användarna synkronisera sina enheter manuellt för att tvinga synkroniseringen att fortsätta. Instruktioner för slutanvändaren finns i [Synkronisera enheten manuellt för att påskynda appinstallationer](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Webbplatsen Företagsportal** När Windows 10 Mobile- och Windows Phone 8.1-användare installerar branschspecifika appar ser de nu följande nya statusar där de får mer information om installationens status:

* **Väntar på att enheten ska synkroniseras** – användaren har tryckt på ”Installera” och nu försöker enheten synkronisera med Intune-infrastrukturen. Synkroniseringen krävs innan installationen kan slutföras. Meddelandet ”Väntar på att enheten ska synkroniseras” är också en länk som användarna kan trycka på för att visa [instruktioner](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) om hur de manuellt synkroniserar sina enheter med Intune om synkroniseringsprocessen tar lång tid eller fastnar.
* **Hämtar** – användarens hämtningsbegäran behandlas och enheten laddar ned och installerar appen.

Innan dessa statusar lades till var det förvirrande för användarna när en appinstallation tog lång tid eftersom de bara såg statusen ”Installerar”, som kan visas på skärmen i flera timmar. Med de nya statusarna kan användarna, i stället för att kontakta supportavdelningen, trycka på länken ”Väntar på att enheten ska synkroniseras” och följa anvisningarna för att tvinga synkroniseringen att fortsätta.

>[!div class="step-by-step"]

>[&larr; **Nyheter i Intune**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Feb17_HO1-->


