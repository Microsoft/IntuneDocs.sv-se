---
title: Tidigare versioner | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: 3080d23f464e96315ed9e5fd59774ba9f1b2dd86
ms.openlocfilehash: 65d582958d77150091880cce72e079b87308209f


---

# Tidigare versioner av Intune
## Maj 2016

Alla dessa funktioner stöds även för hybriddistributioner (Configuration Manager med Intune). Mer information om nya hybridfunktioner finns på sidan med [nyheter om hybridfunktioner](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Dokumentation
Välkommen till förhandsversionen av [docs.microsoft.com](https://docs.microsoft.com/en-us/intune)!
Det här är en helt ny modern innehållsplattform som har tagits fram för att göra det enklare för våra kunder att förstå och använda Intune.
Mer information om alla de nya funktionerna finns i [Introduktion till docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Hälsotillstånd för Intune-tjänsten
Information om Intune-tjänstens hälsotillstånd har nu flyttats till en central plats med andra Microsoft-tjänster. Nu hittar du den här informationen under **Tjänstens hälsa** i [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx).
Mer information finns i [det här blogginlägget](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Apphantering
- **MAM SDK: Stöd för konfiguration av PIN-kodens längd.** Du kan ange längden på PIN-koden för MAM-appar på samma sätt som PIN-koden för en enhet. Detta innebär att slutanvändaren måste uppfylla de nya begränsningar som du anger. Användaren ser en lite annorlunda PIN-skärm som är anpassad till den längre inmatningen. Mer information finns i [MAM-principinställningar för Android](/intune/deploy-use/android-mam-policy-settings) och [MAM-principinställningar för iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype för företag för iOS och Android.** Du kan nu välja att rikta in Skype för företag med [MAM utan registreringsprinciper](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). När användarna loggar in tillämpas MAM-principerna.

- **Nya appar tillgängliga för hantering med MAM-principer.** Microsoft Word-, Excel- och PowerPoint-appar för Android kan nu associeras med MAM-principer på enheter som inte har registrerats med Intune. Om du vill se en fullständig lista över appar som stöds kan du gå till Microsoft Intune-galleriet för mobilprogram på sidan för [Microsoft Intune-programpartner](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


### Uppdateringar av företagsportalen

#### Android-företagsportalsapp
- **Popup-meddelanden för slutanvändare**: Slutanvändarna ser nu popup-meddelandena från Android-företagsportalappen när de registrerar eller tar bort enheter från företagsportalen.

- **Ändringar i kontona för Enhetsregistreringshanterare i Android-företagsportalappen.** I syfte att förbättra prestanda och skalning visar Intune inte längre alla enheter i enhetsregistreringshanteraren i fönstret Mina enheter Android-företagsportalappen. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen.

#### Företagsportalens webbplats
- **Webbplatsen för företagsportalen: En banderoll för enhetsidentifikation visar mer information för slutanvändaren.** Slutanvändarna kan nu enkelt identifiera den enhet de har valt när de använder företagsportalens webbplats. Om fel enhet har valts kan de välja rätt enhet genom att trycka på länken **Tryck här** på banderollen på startsidan.

## Kommande nyheter
- **Introduktion till gränssnittet i Meddelandecenter**. Som en del av migreringen av Intune till [hanteringsportalen för Office 365](https://portal.office.com/) kommer vi att börja utnyttja Meddelandecenter för att informera om nya funktioner och annan kommunikation. Genom att installera den medföljande mobilappen för Office 365-administratör kan du också ta emot meddelanden på din mobiltelefon och enkelt vidarebefordra meddelanden till användare eller ett distributionsalias.
Från och med majutgåvan kommer vi att börja använda Meddelandecenter för att meddela dig när uppdateringar är färdiga och för att publicera information om nya och förbättrade Intune-funktioner. Ta en titt på Meddelandecentret redan nu genom att logga in till [hanteringsportalen för Office 365](https://portal.office.com/) och välja alternativet MEDDELANDECENTER i det vänstra navigeringsfönstret.

- **Ändringar av konton för enhetsregistreringshanterare**. I syfte att förbättra prestanda och skalning visar Intune inte längre **alla** enheter i enhetsregistreringshanteraren i fönstret **Mina enheter** i iOS-företagsportalappen. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen. Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter. Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt.

### Moln-översikt
Håll dig informerad om Intunes utveckling i [översikten över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Tjänstens utfasning
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


## April 2016
Alla dessa funktioner stöds även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune).
### Apphantering
- **MAM-efterlevnad.**
Nu kan du visa [statusen](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) för dina programhanteringsprinciper för alla användare i din Azure Active Directory-klientorganisation (AAD). Du måste bland annat:
   - Egenskaper
   - Appar på enheten

   Statusvärden:

   **Incheckad**: Anger att principen distribuerades till användaren, att appen har använts i arbetskontexten och att principen har tillämpats.

    **Inte incheckad**: Anger att principen distribuerades till användaren, men att appen inte har använts i arbetskontexten sedan dess.


- **MAM-kontroller för att förhindra att Outlook-kontakter synkroniseras (Android).**
En ny inställning är tillgänglig för [hantering av mobila program](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) utan enhetsregistrering. Med den här inställningen kan du förhindra att ett program synkroniserar kontakter till den interna adressboken på Android-enheter. Om den här inställningen är aktiverad kan berörda program inte längre spara kontakter i den interna adressboken. Om den här inställningen är inaktiverad kan berörda program spara kontakter i den interna adressboken. När du [fjärraderar en enhet eller app](wipe-managed-company-app-data-with-Microsoft-Intune.md) tas kontakter som redan har sparats i den interna adressboken bort. Den här nya inställningen stöds av Outlook på Android-enheter.

### Enhetshantering
- **Identifiering av telefonnummer för företagsägda enheter.** Telefoner kategoriserade som ”företagsägda” identifieras nu med sina fullständiga telefonnummer, t.ex. när du kör en inventeringsrapport för mobila enheter. BYOD-telefonnummer döljs fortfarande med ***, och bara de fyra sista siffrorna visas.


### Uppdateringar av företagsportalen
**Android-företagsportalappen** Användare som inte har registrerat sin enhet i Intune och som inte har rätt certifikat installerat kan inte logga in på företagsportalappen för Android och får se meddelandet ”Du kan inte logga in eftersom enheten saknar ett obligatoriskt certifikat”. Meddelandet innehåller länken ”Så här löser du problemet” som användarna kan trycka på för att visa installationsanvisningar för certifikatet. Om du vill se de steg som slutanvändarna går igenom för att lösa problemet, se [Enheten saknar ett nödvändigt certifikat](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

Stöd för **iOS-företagsportalappen** har lagts till för dra-för-att-uppdatera-uppdateringsåtgärden för att uppdatera innehållet på startsidan, vilket innefattar de listade apparna, listade enheter och IT-kontaktuppgifterna. Den här åtgärden kontrollerar inte kompatibiliteten eller principinformation, vilket du kan göra genom att välja panelen för din aktuella enhet och trycka på knappen **Synkronisera**.

**Företagsportalappen för Windows 10 Mobile och Windows Phone 8.1** När slutanvändarna installerar branschspecifika appar får du nu en förbättrad programinstallationsupplevelse. Om appinstallationen tar lång tid kan användarna synkronisera sina enheter manuellt för att tvinga synkroniseringen att fortsätta. Instruktioner för slutanvändaren finns i [Synkronisera enheten manuellt för att påskynda appinstallationer](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Webbplatsen Företagsportal** När Windows 10 Mobile- och Windows Phone 8.1-användare installerar branschspecifika appar ser de nu följande nya statusar där de får mer information om installationens status:

* **Väntar på att enheten ska synkroniseras** – användaren har tryckt på ”Installera” och nu försöker enheten synkronisera med Intune-infrastrukturen. Synkroniseringen krävs innan installationen kan slutföras. Meddelandet ”Väntar på att enheten ska synkroniseras” är också en länk som användarna kan trycka på för att visa [instruktioner](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) om hur de manuellt synkroniserar sina enheter med Intune om synkroniseringsprocessen tar lång tid eller fastnar.
* **Hämtar** – användarens hämtningsbegäran behandlas och enheten laddar ned och installerar appen.

Innan dessa statusar lades till var det förvirrande för användarna när en appinstallation tog lång tid eftersom de bara såg statusen ”Installerar”, som kan visas på skärmen i flera timmar. Med de nya statusarna kan användarna, i stället för att kontakta supportavdelningen, trycka på länken ”Väntar på att enheten ska synkroniseras” och följa anvisningarna för att tvinga synkroniseringen att fortsätta.


## Mars 2016
### Nyheter den 29 mars 2016
Med undantag av uppdateringen av den allmänna konfigurationsprincipen för Windows 10 stöds alla funktioner som släpps den 29 mars 2016 även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune). Hybridstöd för uppdateringen av den allmänna konfigurationsprincipen för Windows 10 kommer snart. Observera att vissa av dessa funktioner kan kräva den senaste versionen av Configuration Manager.

### Apphantering
- **MAM-kontroller för att förhindra att Outlook-kontakter synkroniseras (iOS).** En ny inställning är tillgänglig för hantering av mobilprogram utan registrering av enheter. Med den här inställningen kan du förhindra att ett program synkroniserar kontakter till den interna adressboken på iOS-enheter. När den här inställningen är aktiverad kan appen inte längre spara kontakter i den interna adressboken. När den här inställningen är inaktiverad kan appen spara kontakter i den interna adressboken. När du selektivt rensar en enhet tas alla kontakter som redan har sparats i den interna adressboken bort. Den här nya inställningen stöds av Outlook-programmet på iOS-enheter. Mer information om denna och andra inställningar finns i [Skapa och distribuera MAM-principer](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Åtkomstkontroll
- **Skype för företag – Online stöder villkorlig åtkomst.** Du kan skapa en princip för villkorlig åtkomst för Skype för företag – Online så att programmet bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Användare som försöker logga in i mobilappen för Skype för företag på iOS och Android uppmanas att registrera sig i Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in. Mer information finns i [Hantera åtkomst till Skype för företag – online](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Enhetshantering
- **Intune-stöd för iOS 9.3.** Måndagen den 21 mars meddelade Apple tillgängligheten för iOS 9.3. Vi har arbetat hårt med att säkerställa att Microsoft Intune är kompatibelt med den senaste versionen av Apples mobila operativsystem och [vi är glada över att kunna meddela att Intune stöder hantering av iOS 9.3-enheter](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/).

  Alla befintliga Intune-funktioner som för närvarande är tillgängliga för hantering av iOS-enheter fortsätter att fungera sömlöst när användare uppgraderar sina enheter till iOS 9.3. Dessutom stöds iOS 9.3 i dag även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune).

- **Den allmänna konfigurationsprincipen för Windows 10 innehåller nu inställningar för hantering av Windows Defender på registrerade Windows 10-datorer.** Mer information finns i [Inställningar för Windows 10-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Företagsportal

- **Windows-appaket är tillgängliga direkt från företagsportalens webbplats.** Användare av Windows 8-, Windows 8.1- och Windows RT-datorer kan nu installera Windows-appaket (med filtillägget .appx) direkt från företagsportalens webbplats. Tidigare var du tvungen att distribuera eller så var användarna tvungna att installera företagsportalappen på sina enheter för att installera appar.

- **Användarna kan fjärrlåsa sin enhet från företagsportalens webbplats.** Ett nytt alternativ för fjärrlåsning har lagts till på företagsportalens webbplats så att användarna kan fjärrlåsa sin enhet från portalen om de tappar bort enheten eller om den blir stulen. Se [instruktionerna för slutanvändaren](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). Följande tabell visar plattformsstödet för fjärrlåsning för fristående Intune och Intune med Configuration Manager.

|Plattform | Information om stöd|
|---------|----------------|
|Android |Stöds|
|iOS |Stöds|
|Windows 10 Mobil |Stöds endast om telefonen har ett konfigurerat lösenord|
|Windows 10 Desktop |Stöds inte|
|Windows Phone 8.1 |Stöds endast om telefonen har ett konfigurerat lösenord|
|Windows Phone 8.0 |Stöds inte|
|PC (Windows 8.0 eller tidigare) |Stöds inte|
|PC (Windows 8.1) |Stöds inte|

### Nyheter den 10 mars 2016

### Apphantering

- **Dra nytta av funktionen ”Öppna i” för iOS för enheter som har registrerats i en MDM-lösning från tredje part** Du kan använda en MDM-lösning (hantering av mobila enheter) från en annan leverantör om du vill dra nytta av funktionen ”Öppna i” för iOS. Du kan ange begränsningarna i inställningarna för konfigurationsprofilen och distribuera appen med [Hantera dataöverföring mellan iOS-appar](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

     Den här metoden har två huvudsakliga fördelar:

     1. Användarna måste logga in med sitt arbetskonto innan de får tillgång till företagsdata från molntjänster eller andra appar. Detta säkerställer att hanteringsprinciper för mobilappar (MAM) finns på plats när användaren kommer åt data.

     2. Hanterade e-postprofiler och andra hanterade appar som distribuerats via en tredje parts MDM-lösning kan dela filer och data med appar som har Intunes MAM-principer.

- **Hantera Microsoft Outlook-appen med MAM-principer för enheter som inte har registrerats i Intune** Nu kan du hantera Microsoft Outlook-appen på enheter som inte har registrerats i Intune med Intune-principen för hantering av mobilprogram. Den uppdaterade Microsoft Outlook-appen med MAM-funktionerna är tillgänglig för både [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8)- och [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook)-enheter. Följ instruktionerna i avsnittet [Skapa och distribuera hanteringsprinciper för mobilappar](https://technet.microsoft.com/library/mt627829.aspx) om du vill skapa en MAM-princip.  


- **Med konfigurationsprinciper för mobilappar har du större flexibilitet att ange användarinformation för iOS-appar** Du kan ange användarinställningar som en iOS-app kan behöva när den öppnas. Du kan till exempel ange en nätverksport eller ett användarnamn. Mer information finns i [Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Distribuera Adobe Reader för Microsoft Intune till Intune-hanterade iOS-enheter inom företaget** Nu kan Adobe Reader-appen för iOS hanteras på registrerade enheter med Intunes hanteringsprincip för mobilprogram.

- **Se till att distribuerade webbklipp öppnas i den hanterade webbläsaren** Du kan distribuera riktade webbklipp som bara kan öppnas i den hanterade webbläsaren på iOS- och Android-enheter. Exempelvis kan du distribuera länkar till företagets resurser via företagsportalen, och när användarna navigerar till länkarna öppnas de direkt i den hanterade webbläsaren där de kan skyddas av MAM-principen. Mer information finns i [Distribuera appar](deploy-apps.md).


- **Hitta, hantera och distribuera Windows Store för företag-appar för Windows 10-enheter från Intune-administratörskonsolen** Stöd för Windows Store för företag finns i Intune, där du får hjälp att hitta, hantera och distribuera appar till Windows 10-enheter som du hanterar. Med Windows Store för företag kan du hantera distributions- och övervakningsprocessen för de här apparna från Intune-administratörskonsolen – samma konsol som du använder för att hantera dina andra appar. Mer specifikt hanterar Windows Store för företag innehållet och licensieringen av ”appar som licensierats online”. Mer information finns i [Hantera appar som du har köpt från Windows Store för företag](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Enhetshantering
- **Distribution av PFX-certifikat för iOS-enheter** Intune-administratörer kan skapa och distribuera iOS PFX-certifikat för Wi-Fi, e-post och VPN-autentisering på iOS-enheter. Den här funktionen finns redan för Android- och Windows 10-enheter. Mer information finns i [Ge åtkomst till företagsresurser med hjälp av certifikatprofiler](secure-resource-access-with-certificate-profiles.md).


- **Använda appar och principer för olika enhetsgrupper baserat på val av användarkategori** Nu kan Intune-administratörer definiera anpassade enhetskategorier som användarna kan välja bland under registreringen. Administratörer kanske exempelvis vill att användarna ska ange om de registrerar en enhet som används för ”kassahantering", "lastbilstransport" eller "inventering". Den valda kategorin gör att enheten blir medlem i en Intune-enhetsgrupp, som kan användas för att distribuera olika appar och principer till den registrerade enheten. Mer information finns i [Kategorisera enheter med mappning av enhetsgruppen](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Ändringar och uppdateringar i Microsofts företagsportal
Följande ändringar har gjorts i företagsportalen i den här versionen.

**Android-företagsportalsapp**

* När användarna startar en app som hanteras av MAM visas ett meddelande som anger att appen hanteras av deras företag. Nu kan användare trycka på länken ”Lär dig mer” för att visa [mer information](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) som förklarar vad ”hanterade appar” är. De kan också trycka på ”Visa inte igen” så att meddelandet inte längre visas när de startar appen.
* Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
* Nu visas registreringsrelaterade felmeddelanden i företagsportalappen. Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.


**iOS-företagsportalappen**
* När användarna startar en app som hanteras av MAM visas ett meddelande som anger att appen hanteras av deras företag. Nu kan användare trycka på länken "Lär dig mer" för att visa [mer information](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) som förklarar vad ”hanterade appar” är. De kan också trycka på ”Visa inte igen” så att meddelandet inte längre visas när de startar appen.
* Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).
* Nu visas registreringsrelaterade felmeddelanden i företagsportalappen. Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.




## Februari 2016
### Ändringar och uppdateringar i Microsofts företagsportal

Följande ändringar har gjorts i företagsportalen i den här versionen.

#### Android-företagsportalsapp
- Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
- Nu visas registreringsrelaterade felmeddelanden i företagsportalappen. Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.

#### iOS-företagsportalappen
 - Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).

 - Nu visas registreringsrelaterade felmeddelanden i företagsportalappen. Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.


## Januari 2016

### Dra nytta av funktionerna i Windows 10
* **Villkorlig åtkomst med hälsoattesteringstjänsten** Intune-administratörerna kan nu visa status för Windows 10-enheternas hälsotillståndsattestering i Intune Admin-konsolen. Med attestering av enhetens hälsotillstånd kan administratörer se till att klientdatorer har tillförlitliga konfigurationer av BIOS, TPM och startprogram. Klientenheter måste köra Windows 10 med TPM 2 aktiverat för att ha stöd för attestering av hälsotillstånd. Attesteringen av enhetens hälsotillstånd visar antalet enheter som aktiverats för var och en av följande:
    * Tidig lansering av program mot skadlig kod
    * BitLocker
    * Säker start
    * Kodintegritet

    Läs [Introduktion till efterlevnadsprinciper för enheter för Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md) om du vill ha mer information om inställningen för enhetshälsa, insamlade datapunkter och hälsoattesteringsrapporten. [Information om hälsoattesteringstjänsten](https://msdn.microsoft.com/en-us/library/dn934876.aspx) förklarar tjänsten i mer detalj.

* **Windows 10 Passport för arbetsprincip- och certifikathantering** Med Intune kan du [integrera med Microsoft Passport för arbetsplats](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), vilket är en alternativ inloggningsmetod för Windows 10 som använder ett Active Directory- eller Azure Active Directory-konto för att ersätta lösenord, smartkort eller virtuella smartkort. Passport gör det möjligt att använda en användargest för att logga in i stället för ett lösenord. En användargest kan vara en enkel PIN-kod, biometrisk autentisering, t.ex. Windows Hello, eller en extern enhet, t.ex. en fingeravtrycksläsare.

* **VPN för specifika appar** Nu kan välja appar som automatiskt ska ansluta till företagsnätverket via VPN. Skapa listan med appar när du konfigurerar VPN-profilen. Anvisningar finns i Hjälp användarna att ansluta till sitt arbete med hjälp av VPN-profiler med Microsoft Intune.

* **Stöd för fullständig rensning i Windows 10** Nu kan du utfärda en fjärransluten fullständig rensning av Windows 10-skrivbordsenheter registrerade i Intune via Intune-administratörskonsolen. När du kör en fullständig Windows 10-rensning återställs enheten till fabriksinställningarna.


### Uppdatering för Apples volymköpsprogram (VPP, Volume Purchase Program)
Nu kan Intune hjälpa dig att [hantera appar som du har köpt via Apples volymköpsprogram för företag](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Detta innebär bland annat att licensinformation synkroniseras mellan Apple och Intune och att antalet kopior av varje app som du har distribuerat spåras.

### Använd IMEI-nummer för att identifiera företagsägda enheter
Nu kan du identifiera företagsägda mobila enheter genom att [importera IMEI-nummer (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) för plattformar för mobila enheter som har ett IMEI-nummer. När de har registrerats i Intune märks enheter med importerade IMEI-nummer som företagsenheter. Det gör att det går att använda andra principer för dessa enheter än för personliga enheter.

### Nu är fler appar kompatibla med MAM-principer i Intune
Nu är fler appar från Microsofts partner kompatibla med Intunes MAM-principer för hantering av mobilprogram (för enheter som hanteras av Intune):
* Box for EMM (från Box Inc) – endast iOS
* Adobe Reader (från Adobe) – endast Android
* Foxit PDF Reader (från Foxit Corporation) – iOS och Android


### Stödet för IE9 upphör i januari
Från och med februari 2016 kommer Internet Explorer 9 inte längre att stödjas som officiell webbläsare för att komma åt webbplatsen Microsoft Intune-företagsportalen, Intune-kontoportalen och Intune-administratörskonsolen. Du måste migrera till Internet Explorer 10 eller senare.

## December 2015
### Ändringar och uppdateringar i Microsofts företagsportal
Följande ändringar har gjorts i företagsportalen i den här versionen.

**Android-företagsportalsapp**

Följande ändringar har gjorts för att uppfylla nya krav från Google. Två nya meddelanden visas för användare på Android 6.0 och senare enheter:
* Tillåt att företagsportalen kan ringa och hantera telefonsamtal?
* Tillåt att företagsportalen kommer åt foton, media och filer på enheten?

Följande tabell innehåller information om dessa två meddelanden.



Meddelandetext  |Tillåt att företagsportalen kan ringa och hantera telefonsamtal?  
---------|---------
Meddelandets betydelse     |  Gör det möjligt att skicka användarens enhetstelefonnummer och IMEI till Intune-tjänsten och att visa dessa i administrationskonsolen på sidan Maskinvara.   </br></br>**Obs! Företagsportalappen ringer eller hanterar aldrig telefonsamtal!** Meddelandetexten styrs av Google och kan inte ändras. </br></br>Öppna sidan **Maskinvara** genom att gå till **Grupper** > **Alla mobila enheter** > **Enheter**. Välj användarens enhet och gå till **Visa egenskaper** > **Maskinvara**.    
Var och när meddelandet visas  | Meddelandet visas när användarna loggar in på företagsportalappen för första gången och börjar registrera sina enheter.|         
Vad händer om användarna tillåter åtkomst  |  Enhetens telefonnummer och IMEI visas på sidan Maskinvara i administrationskonsolen. |         
Vad händer om användarna nekar åtkomst     | De kan fortsätta att använda företagsportalappen och registrera sina enheter, men användarnas enhetstelefonnummer och IMEI är tomma på sidan Maskinvara i administrationskonsolen.       </br></br> Den andra gången användarna loggar in på företagsportalappen efter att de nekat åtkomst visas kryssrutan **Fråga inte igen** som de kan markera så att meddelandet inte visas igen.</br></br>Om användare tillåter men senare nekar åtkomst visas meddelandet nästa gång användaren loggar in på företagsportalappen efter registreringen.</br></br>Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Telefon** och aktivera behörigheten.
Mer information     |  För användarna: [Logga in på företagsportalappen](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)  </br></br>För IT-proffs: Informationen i den här tabellen finns också i [Hjälpa användarna att förstå meddelanden från företagsportalappen](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   

Meddelandetext  |Tillåt att företagsportalen kommer åt foton, media och filer på enheten?  
---------|---------
Meddelandets betydelse     |  Gör det möjligt för enheten att skriva dataloggar till enhetens SD-kort, vilket gör att loggar kan flyttas med hjälp av en USB-kabel.   </br></br>**Obs! Företagsportalappen skaffar sig aldrig åtkomst till användarnas foton, media och filer.** Meddelandetexten styrs av Google och kan inte ändras.     
Var och när meddelandet visas  | Meddelandet visas när användarna trycker på **Skicka data** för att skicka dataloggar till IT-administratören.|         
Vad händer om användarna tillåter åtkomst  |  Loggfilerna kopieras till SD-kortet. |         
Vad händer om användarna nekar åtkomst     | De kan fortfarande skicka loggar, men loggarna kopieras inte till enhetens SD-kort.       </br></br> Den andra gången användarna loggar in på företagsportalappen efter att de nekat åtkomst visas kryssrutan **Fråga inte igen** som de kan markera så att meddelandet inte visas igen.</br></br>Om användare tillåter men senare nekar åtkomst visas meddelandet nästa gång användaren försöker skicka loggar.</br></br>Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Lagring** och aktivera behörigheten.
Mer information     |  För användarna: [Skicka diagnostikdataloggar till IT-administratören via e-post](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)  </br></br>För IT-proffs: Informationen i den här tabellen finns också i [Hjälpa användarna att förstå meddelanden från företagsportalappen](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   


**iOS-företagsportalappen**
* Användare kan nu använda Microsoft Outlook eller andra e-postappar för att skicka diagnostikloggar till IT-administratören. Tidigare gick det endast att använda den inbyggda appen.
* Stödet har förbättrats för Apples DEP (Device Enrollment Program) och företagsregistrerade enheter. Mer information finns i [Du uppmanas att identifiera din enhet när du försöker registrera dig](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device).
* I användarens lista över registrerade enheter visas nu en grön bockmarkering bredvid den enhet som användaren använder för tillfället. Innan den här markeringen lades till kunde inte användarna avgöra vilken registrerad enhet de använde.

**Windows företagsportalapp**

Microsoft samlar automatiskt in anonymiserade data om prestanda och användning av företagsportalen för att kunna förbättra Microsofts produkter och tjänster. Slutanvändare kan inaktivera datainsamling med inställningen Användningsdata på sin enhet, men administratörer har ingen kontroll över datainsamlingen och kan inte ändra slutanvändarens val för den här inställningen.



## November 2015
### Apphantering
Intune stöder MAM-principer för hantering av mobilprogram som bidrar till att förhindra att företagsdata läcks till konsumentappar och konsumenttjänster. Tidigare tillämpades dessa principer endast på mobila appar som kördes på enheter som också hade registrerats för hantering av mobilenheter (MDM) i Intune.

Med den här månadens uppdatering utökar Intune sina MAM-funktioner till nya typer av enheter. Förutom enheter som registrerats i Intune kan du nu använda MAM-principer på
* enheter som hanteras av någon annan enhetshanteringslösning (MDM)
* enheter som inte har registrerats i något enhetshanteringssystem, vanligtvis BYOD-enheter (Bring Your Own Device).

Mer information om de nya MAM-funktionerna finns i följande blogginlägg:
* [Förbättra hanterad mobilproduktivitet](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Nya Microsoft Enterprise Mobility-funktioner](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

Här beskrivs några viktiga funktioner och ytterligare information om Intunes MAM-funktioner:
* Företagsdata isoleras från konsumentdata i appar som exponerats för Intune, inklusive Office Mobile-appar, tredjepartsappar som har integrerat Intune SDK eller affärsappar som finns i Intune.
* Företagsdata kan delas (**klipp ut/kopiera/klistra in**) mellan företagsappar samtidigt som delningen av företagsdata till personliga appar förhindras. Mer information finns i [Hur MAM-principer skyddar appdata](https://technet.microsoft.com/library/mt627825.aspx). Det här exemplet, [Använda Microsoft Word-appen för arbete och personliga uppgifter](https://technet.microsoft.com/library/mt627827.aspx), visar hur delning av företagets data till personliga appar förhindras.
* Principer som förebygger förlust av viktiga data, t.ex. en PIN-kod för varje app, ”spara som”-kontroller och hanterad datadelning mellan appar. En lista över alla principer finns i [Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Word, Excel, PowerPoint, Outlook, OneNote och OneDrive för företag innehåller de nya funktionerna och kan hanteras med och utan enhetsregistrering. Funktionerna som skyddar mot förlust av data är inbyggda i Office-standardapparna i Apple Store eller Google Play-butiken och kräver inte appomslutning eller separat inläsning.
* Information om hur du kommer igång finns i [Komma igång med principer för hantering av mobilappar i Azure Portal](https://technet.microsoft.com/library/mt627830.aspx). Information om hur du konfigurerar och distribuerar principer för hantering av mobilappar finns i [Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* När slutanvändarna autentiseras mot appen med sina företagsuppgifter konfigureras funktionerna mot dataförlust automatiskt. Avsnittet [Slutanvändarens upplevelse i appar som är associerade med Microsoft Itunes hanteringsprinciper för mobilappar](https://technet.microsoft.com/library/mt627827.aspx) innehåller vissa exempelscenarier som illustrerar hur användaren kommer åt OneDrive på iOS- och Android-enheter.
* Fungerar både på iOS- och Android-enheter.

Listan över [Microsoft-appar som du kan använda med Microsoft Intunes hanteringsprinciper för mobilprogram](https://technet.microsoft.com/library/dn708489.aspx) har uppdaterats så att de senaste apparna visas.

### Enhetshantering
 **Mac OS X-enhetshantering** Nu kan du registrera och hantera Mac OS X-enheter med Intune. Du kan göra följande med dina Mac OS X-enheter:
* Registrera enheter som ska hanteras av Intune. Läs [Konfigurera iOS-hantering med Microsoft Intune](https://technet.microsoft.com/library/dn408185.aspx).
* Kontrollera enhetsinställningar med en allmän konfigurationsprincip. Läs [Inställningar för Mac OS X-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx).
* Distribuera Mac OS X-inställningar som du skapat med Apple Configurator. Läs [Anpassade principinställningar för Mac OS X i Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx).
* Samla in maskin- och programvaruinventering från Mac OS X-enheter. Läs [Förstå dina enheter med inventering i Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx).
* Kör nya rapporter som visar information om de Mac OS X-enheter som du hanterar. Läs [Förstå Microsoft Intune-aktiviteter med hjälp av rapporter](https://technet.microsoft.com/library/dn646977.aspx).

**Nya inställningar för webbläsaren Edge för Windows 10-enheter** Nya inställningar har lagts till i den allmänna konfigurationsprincipen för Windows 10, och kan användas för att hantera inställningar och funktioner i Microsoft Edge-webbläsaren. Läs [Inställningar för Windows 10-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx).

**E-postprofiler** En ny princip för e-postprofiler har lagts till för Windows 10-skrivbordsenheter och Windows 10-mobilenheter. Läs [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](https://technet.microsoft.com/library/dn646984.aspx).

**Nya inställningar för efterlevnadsprinciper** Följande nya inställningar för säkerhets- och systemprinciper har lagts till i listan med efterlevnadsprinciper:
* Om du vill säkerställa att de senaste uppdateringarna är installerade på enheter med Windows 8.1 eller senare som har åtkomst till företagets resurser använder du inställningen **Kräv automatiska uppdateringar**. Du kan även ange vilken typ av uppdateringar som ska installeras automatiskt – antingen alla uppdateringar som har markerats som viktiga att installera, eller alla uppdateringar som har markerats som viktiga eller rekommenderade. En fullständig lista över inställningar för efterlevnadsprinciper finns i [Hantera efterlevnadsprinciper för enheter Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx).
* Med den nya inställningen **Kräv lösenord när enheten lämnar inaktivt läge** i kombination med den befintliga inställningen **Minuter av inaktivitet innan lösenord måste anges** kan du skapa en efterlevnadsinställning som kräver att slutanvändarna anger ett lösenord innan de kan använda en enhet som har varit inaktiv en viss tid.

**Nya alternativ för principer för villkorlig åtkomst** Du kan tillämpa principer för villkorlig åtkomst för **alla användare** i antingen nya eller befintliga villkorliga åtkomstprinciper. Alla användare med licens för Intune och Office 365 måste registrera sina enheter, och om enhetsplattformen inte stöds av Intune blockeras åtkomsten för klientprogram som använder [inloggning baserat på Active Directory-autentisering (modern autentisering)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/).

Du kan också ange att principen för villkorlig åtkomst gäller för **alla plattformar**.  Alla klientprogram som använder [inloggning baserat på Active Directory-autentisering (modern autentisering)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) styrs av principen för villkorlig åtkomst, och om plattformen inte stöds av Intune så blockeras åtkomsten.

### Ändringar och uppdateringar i Microsofts företagsportal
Följande ändringar har gjorts för företagsportalens appar i den här versionen:

* **Android**: En välkomstskärm har lagts till i Android-företagsportalappen som hjälper användare att förstå syftet med företagsportalappen. Den här skärmen är avsedd att minska nedladdningar av appen av användare vars företag inte är Intune-prenumeranter.

* **iOS**: Intune har nu stöd för registrering av Mac OS X-enheter via [företagsportalens webbplats](https://portal.manage.microsoft.com). Anvisningar finns i [Registrera din Mac OS X-enhet i Intune](https://technet.microsoft.com/library/mt598622.aspx).

* **Webbplatsen för företagsportalen**: Användare som har registrerat sina enheter i Intune kan nu återställa sina lösenord med hjälp av alternativet **Återställ lösenord** på företagsportalens webbplats. Tidigare kunde endast IT-administratörer återställa användarnas lösenord. Alternativet Återställ lösenord stöds inte för Windows 8.1- och Windows RT-enheter och alternativet visas endast när enheterna har registrerats i hantering av mobila enheter (MDM) eller MDM med Exchange ActiveSync. Användarinstruktioner finns i [Återställa lösenordet](https://technet.microsoft.com/library/mt590895.aspx).

### Licensieringsändringar för globala administratörer
I oktober meddelade vi att globala administratörer (kallas även innehavaradministratörer) kunde fortsätta att utföra dagliga administrationsuppgifter utan en separat Intune- eller EMS-licens (Enterprise Mobility Suite). Om globala administratörer vill använda tjänsten, t.ex. för att registrera sina egna enheter, företagsenheter eller för att använda Intunes företagsportal, behöver de dock en Intune- eller EMS-licens precis som andra användare. Nedan finns ytterligare information.
* Intune-företagsportalen är den plats där användare kan:
    * registrera sina enheter
    * visa statusen för sina enheter
    * ladda ned programvara som en global administratör har distribuerat till organisationen
    * hitta länkar som publicerats av den globala administratören som leder till information om hur användaren kontaktar sin IT-avdelning.

    [Lär dig mer om företagsportalen](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) och [hur du anpassar den](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal).
* Den person som registrerar sig för att köpa Intune eller EMS på uppdrag av en organisation blir automatiskt den första globala administratören i klientorganisationen. I höstas började Intune att automatiskt tilldela en Intune- eller EMS-licens till den första globala administratören som en del av migreringen till [Office 365-portalen](http://portal.office.com/) och utfasningen av [Intune-kontoportalen](http://account.manage.microsoft.com/). Ytterligare globala administratörer som läggs till kan fortsätta med den dagliga administrationen utan en separat Intune- eller EMS-licens. Men om de börjar agera som slutanvändare och registrera sina egna enheter (eller företagets) eller ladda ned programvara från företagsportalen behöver de en licens precis som alla andra användare.
* Ändringen kommer att implementeras i faser med början i januari 2016.
* För Microsoft-partner bör den här ändringen inte påverka din möjlighet att administrera tjänsten för dina kunders räkning. För slutanvändaråtgärder krävs en Intune- eller EMS-licens för att registrera enheten och komma åt eller ladda ned programvara från företagsportalen.

Om du har frågor om den här ändringen är du välkommen att kontakta Intunes supportteam:
* [Microsoft Intune-supportkanaler](https://technet.microsoft.com/library/jj839713.aspx)
* [Community-support](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

För allmän feedback om Microsoft Intune, inklusive förfrågningar om designändringar eller buggar, besöker du [webbplatsen för Intune-feedback](https://microsoftintune.uservoice.com/).


### Nyheter i Intune-dokumentation – november 2015
**Nytt innehåll**
* [Inställningar för Mac OS X-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx): Så här kontrollerar du inställningar för enheter och funktioner för Mac OS X-enheter.
* [Anpassade principinställningar för Mac OS X i Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx): Så här distribuerar du Mac OS X-enhetsinställningar som du skapat med hjälp av verktyget Apple Configurator.
* [Konfigurera apprinciper som förhindrar dataförlust med Microsoft Intune](https://technet.microsoft.com/library/mt627825.aspx): Innehåller information om scenarierna som principerna för mobilappshantering har stöd för och hur principerna fungerar för att skydda data.
* [Komma igång med principer för hantering av mobilappar i Azure Portal](https://technet.microsoft.com/library/mt627830.aspx): Vad du behöver för att komma igång med Azure Preview Portal för hanteringsprinciper för mobilappar.
* [Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx): Innehåller en stegvis genomgång av hur du skapar principer för hantering av mobilappar på Azure Preview Portal.
* [Övervaka hanteringsprinciper för mobilappar med Microsoft Intune](https://technet.microsoft.com/library/mt627824.aspx): Information om hur du kan övervaka dina principer för hantering av mobilappar med Azure Preview Portal.
* [Hanteringsprinciper för mobilappar och funktionen Öppna i för iOS i Microsoft Intune](https://technet.microsoft.com/library/mt627821.aspx): Information om hur hanteringsprinciper för mobilappar fungerar med funktionen Öppna i för iOS.
* [Slutanvändarens upplevelse i appar som är associerade med Microsoft Itunes hanteringsprinciper för mobilappar](https://technet.microsoft.com/library/mt627827.aspx): Slutanvändarnas upplevelse när de använder appar som är associerade med hanteringsprincipen för mobilappar.
* [Rensa hanterade företagsdata från appar med Microsoft Intune](https://technet.microsoft.com/library/mt627826.aspx): Hur du tar bort företagsdata från appar.

**Uppdaterat innehåll**
* [Inställningar för Windows 10-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx): Nya inställningar för Edge-webbläsaren har lagts till.
* [Konfigurera iOS-hantering med Microsoft Intune](http://technet.microsoft.com/library/dn408185.aspx): Information om hur du registrerar Mac OS X-enheter har lagts till.
* [Förstå dina enheter med inventering i Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx): Information om inventeringen som samlas in från Mac OS X-enheter har lagts till. Dessutom har avsnittet uppdaterats med den senaste informationen för alla enhetsplattformar.
* [Förstå Microsoft Intune-åtgärder med hjälp av rapporter](https://technet.microsoft.com/library/dn646977.aspx): Information har lagts till om de två nya rapporterna som används för att visa information om dina hanterade Mac OS X-enheter.
* [Hantera efterlevnadsprinciper för enheter för Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx): Information har lagts till om de nya efterlevnadsprinciperna som kräver automatiska uppdateringar och krav på lösenord när en enhet lämnar inaktivt läge.
* [Hantera email åtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx): Information har lagts till om möjligheten att använda principen för villkorlig åtkomst för alla plattformar och alla användare.
* [Hantera SharePoint onlineåtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx): Information har lagts till om möjligheten att använda principen för villkorlig åtkomst för alla plattformar och alla användare.

## Oktober 2015

### Uppdateringar för villkorlig lokal åtkomst till Exchange
**Nu kan du tillåta åtkomst till Exchange Active Sync-e-post för kompatibla enheter som registrerats i Intune när den globala Exchange-regeln ställts in att blockera eller sätta i karantän** Fram till nu var du tvungen att definiera den globala Exchange-standardregeln till **Tillåt** för att tillåta åtkomst till e-post på registrerade och kompatibla enheter.

Med den här uppdateringen av tjänsten är inställningen inte längre ett krav för villkorlig åtkomst. Om Exchange-miljön kräver att din globala standardregel ställs in till **Blockera/Karantän** markerar du bara kryssrutan **Åsidosätt standardregel** på den lokala sidan för principer för villkorlig åtkomst för Exchange. Avsnittet [Hantera email åtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) innehåller mer information om reglerna och meddelandena som visas för slutanvändaren.

**Ny karantänupplevelse med en enda klickning** Vi har förenklat karantänupplevelsen för e-post och lagt till stöd för registrering med en enda klickning. Med den här tjänsteuppdateringen kan slutanvändarna klicka på en enda länk i e-postmeddelandet om karantän för att slutföra registreringen i företagsportalappen.
### Uppdateringar för mobil enhet och apphantering
**Android** Nu stöder alla Intune-hanteringsfunktioner Android 6.0 (Marshmallow), vilket förklaras i det här blogginlägget: [Microsoft Intune tillhandahåller stöd från första dagen för Android Marshmallow](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx)

**iOS** Du kan inte längre skapa nya appdistributioner till iOS-enheter som kör en version som är tidigare än iOS 7.1. Alla befintliga appdistributioner till enheter som kör en tidigare version än iOS 7.1 fortsätter att fungera och hanteras av Intune.

**Windows 10** Nu stöder Intune distributionen av Windows 10 Universal-appar med hjälp av programinstallationstypen **Windows-programpaket**. Information och krav finns i [Kom igång med appdistribution i Microsoft Intune](http://technet.microsoft.com/en-US/library/dn646955.aspx).


### Ändringar och uppdateringar för appar i Microsofts företagsportal
Följande ändringar har gjorts för företagsportalens appar i den här versionen: **iOS** Nya knappar har lagts till i företagsportalappen för att göra det enklare för användarna att skicka diagnostiska loggar till sina IT-administratörer:

|Knappnamn|Var det visas|
|------------|---------------|
|Rapport|Varningsmeddelanden|
|Skicka diagnostikrapport|Företagsportalappens skärm Om|


>[!div class="step-by-step"]

>[&larr; **Nyheter i Intune**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Jun16_HO3-->


