---
# required metadata

title: Tidigare versioner | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Tidigare versioner av Intune
## Mars 2016
### Nyheter den 29 mars 2016
Med undantag av uppdateringen av den allmänna konfigurationsprincipen för Windows 10 stöds alla funktioner som släpps den 29 mars 2016 även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune). Hybridstöd för uppdateringen av den allmänna konfigurationsprincipen för Windows 10 kommer snart. Observera att vissa av dessa funktioner kan kräva den senaste versionen av Configuration Manager.

### Apphantering
- **MAM-kontroller för att förhindra att Outlook-kontakter synkroniseras (iOS).** En ny inställning är tillgänglig för hantering av mobilprogram utan registrering av enheter. Med den här inställningen kan du förhindra att ett program synkroniserar kontakter till den interna adressboken på iOS-enheter. När den här inställningen är aktiverad kan appen inte längre spara kontakter i den interna adressboken. När den här inställningen är inaktiverad kan appen spara kontakter i den interna adressboken. När du selektivt rensar en enhet tas alla kontakter som redan har sparats i den interna adressboken bort. Den här nya inställningen stöds av Outlook-programmet på iOS-enheter. Mer information om denna och andra inställningar finns i [Skapa och distribuera MAM-principer](https://technet.microsoft.com/en-us/library/dn292747.aspx)

### Åtkomstkontroll
- **Skype för företag – Online stöder villkorlig åtkomst.** Du kan skapa en princip för villkorlig åtkomst för Skype för företag – Online så att programmet bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Användare som försöker logga in i mobilappen för Skype för företag på iOS och Android uppmanas att registrera sig i Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in. Mer information finns i [Hantera åtkomsten till Skype för företag – Online](https://technet.microsoft.com/en-us/library/mt695297.aspx)

### Enhetshantering
- **Intune-stöd för iOS 9.3.** Måndagen den 21 mars meddelade Apple tillgängligheten för iOS 9.3. Vi har arbetat hårt med att säkerställa att Microsoft Intune är kompatibelt med den senaste versionen av Apples mobila operativsystem och [vi är glada över att kunna meddela att Intune stöder hantering av iOS 9.3-enheter](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/)

  Alla befintliga Intune-funktioner som för närvarande är tillgängliga för hantering av iOS-enheter fortsätter att fungera sömlöst när användare uppgraderar sina enheter till iOS 9.3. Dessutom stöds iOS 9.3 i dag även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune).

- **Den allmänna konfigurationsprincipen för Windows 10 innehåller nu inställningar för hantering av Windows Defender på registrerade Windows 10-datorer.** Mer information finns i [Inställningar för Windows 10-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/en-us/library/mt404697.aspx)


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

- Dra nytta av funktionen ”Öppna i” för iOS för enheter som registrerats i en MDM-lösning från tredje part Du kan använda en MDM-lösning (hantering av mobilenheter) från en annan leverantör om du vill dra nytta av funktionen ”Öppna i” för iOS.

     Du kan ange begränsningarna i inställningarna för konfigurationsprofilen och distribuera appen med [Hantera dataöverföring mellan iOS-appar](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

     1. Den här metoden har två huvudsakliga fördelar: Användarna måste logga in med sitt arbetskonto innan de får tillgång till företagsdata från molntjänster eller andra appar.

     2. Detta säkerställer att hanteringsprinciper för mobilappar (MAM) finns på plats när användaren kommer åt data.

- Hanterade e-postprofiler och andra hanterade appar som distribuerats via en tredje parts MDM-lösning kan dela filer och data med appar som har Intunes MAM-principer. Hantera Microsoft Outlook-appen med MAM-principer för enheter som inte har registrerats i Intune Nu kan du hantera Microsoft Outlook-appen på enheter som inte har registrerats i Intune med Intune-principen för hantering av mobilprogram.  


- Den uppdaterade Microsoft Outlook-appen med MAM-funktionerna är tillgänglig för både [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8)- och [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook)-enheter. Följ instruktionerna i avsnittet [Skapa och distribuera hanteringsprinciper för mobilappar](https://technet.microsoft.com/library/mt627829.aspx) om du vill skapa en MAM-princip. Med konfigurationsprinciper för mobilappar har du större flexibilitet att ange användarinformation för iOS-appar


- Du kan ange användarinställningar som en iOS-app behöver när den öppnas.

- Du kan till exempel ange en nätverksport eller ett användarnamn. Mer information finns i [Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md) Distribuera Adobe Reader för Microsoft Intune till Intune-hanterade iOS-enheter i företaget


- Nu kan Adobe Reader-appen för iOS hanteras på registrerade enheter med Intunes hanteringsprincip för mobilprogram. Se till att distribuerade webbklipp öppnas i den hanterade webbläsaren Du kan distribuera riktade webbklipp som bara kan öppnas i den hanterade webbläsaren på iOS- och Android-enheter. Exempelvis kan du distribuera länkar till företagets resurser via företagsportalen, och när användarna navigerar till länkarna öppnas de direkt i den hanterade webbläsaren där de kan skyddas av MAM-principen.


### Mer information finns i [Distribuera appar](deploy-apps.md)
- Hitta, hantera och distribuera Windows Store för företag-appar för Windows 10-enheter från Intune-administratörskonsolen Intune har stöd för Windows Store för företag så att du kan hitta, hantera och distribuera appar till Windows 10-enheter som du hanterar. Med Windows Store för företag kan du hantera distributions- och övervakningsprocessen för de här apparna från Intune-administratörskonsolen – samma konsol som du använder för att hantera dina andra appar.


- Mer specifikt hanterar Windows Store för företag innehållet och licensieringen av ”appar som licensierats online”. Mer information finns i [Hantera appar som du har köpt från Windows Store för företag](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md) Enhetshantering Distribution av PFX-certifikat för iOS-enheter

### Intune-administratörer kan skapa och distribuera iOS PFX-certifikat för Wi-Fi, e-post och VPN-autentisering på iOS-enheter.
Den här funktionen finns redan för Android- och Windows 10-enheter.

**Mer information finns i [Ge åtkomst till företagsresurser med hjälp av certifikatprofiler](secure-resource-access-with-certificate-profiles.md)**

* Använda appar och principer för olika enhetsgrupper baserat på val av användarkategori Nu kan Intune-administratörer definiera anpassade enhetskategorier som användarna kan välja bland under registreringen. Administratörer kanske exempelvis vill att användarna ska ange om de registrerar en enhet som används för ”kassahantering", "lastbilstransport" eller "inventering".
* Den valda kategorin gör att enheten blir medlem i en Intune-enhetsgrupp, som kan användas för att distribuera olika appar och principer till den registrerade enheten. Mer information finns i [Kategorisera enheter med gruppmappning av enheten](categorize-devices-with-device-group-mapping-in-microsoft-intune.md)
* Ändringar och uppdateringar i Microsofts företagsportal Följande ändringar har gjorts i företagsportalen i den här versionen. Android-företagsportalsapp


**När användarna startar en app som hanteras av MAM visas ett meddelande som anger att appen hanteras av deras företag.**
* Nu kan användare trycka på länken ”Lär dig mer” för att visa [mer information](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) som förklarar vad ”hanterade appar” är. De kan också trycka på ”Visa inte igen” så att meddelandet inte längre visas när de startar appen. Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter.
* Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc). Nu visas registreringsrelaterade felmeddelanden i företagsportalappen.
* Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika. iOS-företagsportalappen




## När användarna startar en app som hanteras av MAM visas ett meddelande som anger att appen hanteras av deras företag.
### Nu kan användare trycka på länken "Lär dig mer" för att visa [mer information](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) som förklarar vad ”hanterade appar” är.

De kan också trycka på ”Visa inte igen” så att meddelandet inte längre visas när de startar appen.

#### Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter.
- Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device). Nu visas registreringsrelaterade felmeddelanden i företagsportalappen.
- Tidigare visades dessa meddelanden på webbplatsen för företagsportalen. Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika. Februari 2016

#### Ändringar och uppdateringar i Microsofts företagsportal
 - Följande ändringar har gjorts i företagsportalen i den här versionen. Android-företagsportalsapp

 - Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc). Nu visas registreringsrelaterade felmeddelanden i företagsportalappen.


## Tidigare visades dessa meddelanden på webbplatsen för företagsportalen.

### Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.
* iOS-företagsportalappen Nya skärmar har lagts till som leder användarna genom registreringsprocessen och som ger mer information om varför de bör registrera sig och vad IT-administratörer kan se och inte kan se på deras registrerade enheter. Mer information finns i [registreringsanvisningarna](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device). Nu visas registreringsrelaterade felmeddelanden i företagsportalappen.
    * Tidigare visades dessa meddelanden på webbplatsen för företagsportalen.
    * Den här ändringen innebär att alla felmeddelanden nu visas på en plats i stället för på två olika.
    * Januari 2016
    * Dra nytta av funktionerna i Windows 10

    Villkorlig åtkomst med hälsoattesteringstjänsten Nu kan Intune-administratörer visa hälsoattesteringsstatus för Windows 10-enheter i Intune-administratörskonsolen.

* Med attestering av enhetens hälsotillstånd kan administratörer se till att klientdatorer har tillförlitliga konfigurationer av BIOS, TPM och startprogram. Klientenheter måste köra Windows 10 med TPM 2 aktiverat för att ha stöd för attestering av hälsotillstånd. Attesteringen av enhetens hälsotillstånd visar antalet enheter som aktiverats för var och en av följande:

* Tidig lansering av program mot skadlig kod BitLocker

* Säker start Kodintegritet


### Läs [Introduktion till efterlevnadsprinciper för enheter för Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md) om du vill ha mer information om inställningen för enhetshälsa, insamlade datapunkter och hälsoattesteringsrapporten.
[Information om hälsoattesteringstjänsten](https://msdn.microsoft.com/en-us/library/dn934876.aspx) förklarar tjänsten i mer detalj. Windows 10 Passport för arbetsprincip- och certifikathantering

### Med Intune kan du [integrera med Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), som är en alternativ inloggningsmetod för Windows 10 som använder Active Directory eller ett Azure Active Directory-konto för att ersätta ett lösenord, smartkort eller virtuellt smartkort.
Passport gör det möjligt att använda en användargest för att logga in i stället för ett lösenord. En användargest kan vara en enkel PIN-kod, biometrisk autentisering, t.ex. Windows Hello, eller en extern enhet, t.ex. en fingeravtrycksläsare.

### VPN för specifika appar
Du kan välja appar som automatiskt ansluter till företagsnätverket via VPN.
* Skapa listan med appar när du konfigurerar VPN-profilen. Anvisningar finns i Hjälp användarna att ansluta till sitt arbete med hjälp av VPN-profiler med Microsoft Intune.
* Stöd för fullständig rensning i Windows 10
* Nu kan du köra en fullständig fjärrensning av Windows 10-skrivbordsenheter som är registrerade i Intune via Intune-administratörskonsolen.


### När du kör en fullständig Windows 10-rensning återställs enheten till fabriksinställningarna.
Uppdatering för Apples volymköpsprogram (VPP, Volume Purchase Program) Nu kan Intune hjälpa dig att [hantera appar som du har köpt via Apples volymköpsprogram för företag](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md).

## Detta innebär bland annat att licensinformation synkroniseras mellan Apple och Intune och att antalet kopior av varje app som du har distribuerat spåras.
### Använd IMEI-nummer för att identifiera företagsägda enheter
Nu kan du identifiera företagsägda mobila enheter genom att [importera IMEI-nummer (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) för plattformar för mobila enheter som har ett IMEI-nummer.

**När de har registrerats i Intune märks enheter med importerade IMEI-nummer som företagsenheter. Det gör att det går att använda andra principer för dessa enheter än för personliga enheter.**

Nu är fler appar kompatibla med MAM-principer i Intune Nu är fler appar från Microsofts partner kompatibla med Intunes MAM-principer för hantering av mobilprogram (för enheter som hanteras av Intune):
* Box for EMM (från Box Inc) – endast iOS
* Adobe Reader (från Adobe) – endast Android

Foxit PDF Reader (från Foxit Corporation) – iOS och Android



Stödet för IE9 upphör i januari  |Från och med februari 2016 kommer Internet Explorer 9 inte längre att stödjas som officiell webbläsare för att komma åt webbplatsen Microsoft Intune-företagsportalen, Intune-kontoportalen och Intune-administratörskonsolen.  
---------|---------
Du måste migrera till Internet Explorer 10 eller senare.     |  December 2015   </br></br>**Ändringar och uppdateringar i Microsofts företagsportal** Följande ändringar har gjorts i företagsportalen i den här versionen. </br></br>Android-företagsportalsapp Följande ändringar har gjorts för att uppfylla nya krav från Google.    
Två nya meddelanden visas för användare på Android 6.0 och senare enheter:  | Tillåt att företagsportalen kan ringa och hantera telefonsamtal?|         
Tillåt att företagsportalen kommer åt foton, media och filer på enheten?  |  Följande tabell innehåller information om dessa två meddelanden. |         
Meddelandetext     | Tillåt att företagsportalen kan ringa och hantera telefonsamtal?       </br></br> Meddelandets betydelse</br></br>Gör det möjligt att skicka användarens enhetstelefonnummer och IMEI till Intune-tjänsten och att visa dessa i administrationskonsolen på sidan Maskinvara.</br></br>Obs! Företagsportalappen ringer eller hanterar aldrig telefonsamtal!
Meddelandetexten styrs av Google och kan inte ändras.     |  Öppna sidan **Maskinvara** genom att gå till **Grupper** > **Alla mobila enheter** > **Enheter**.  </br></br>Välj användarens enhet och gå till **Visa egenskaper** > **Maskinvara**   

Var och när meddelandet visas  |Meddelandet visas när användarna loggar in på företagsportalappen för första gången och börjar registrera sina enheter.  
---------|---------
Vad händer om användarna tillåter åtkomst     |  Enhetens telefonnummer och IMEI visas på sidan Maskinvara i administrationskonsolen.   </br></br>**Vad händer om användarna nekar åtkomst** De kan fortsätta att använda företagsportalappen och registrera sina enheter, men användarnas enhetstelefonnummer och IMEI är tomma på sidan Maskinvara i administrationskonsolen.     
Den andra gången användarna loggar in på företagsportalappen efter att de nekat åtkomst visas kryssrutan **Fråga inte igen** som de kan markera så att meddelandet inte visas igen.  | Om användare tillåter men senare nekar åtkomst visas meddelandet nästa gång användaren loggar in på företagsportalappen efter registreringen.|         
Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Telefon** och aktivera behörigheten.  |  Mer information |         
För användarna: [Logga in på företagsportalappen](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)     | För IT-proffs: Informationen i den här tabellen finns också i [Hjälpa användarna att förstå meddelanden från företagsportalappen](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)       </br></br> Meddelandetext</br></br>Tillåt att företagsportalen kommer åt foton, media och filer på enheten?</br></br>Meddelandets betydelse
Gör det möjligt för enheten att skriva dataloggar till enhetens SD-kort, vilket gör att loggar kan flyttas med hjälp av en USB-kabel.     |  Obs! Företagsportalappen skaffar sig aldrig åtkomst till användarnas foton, media och filer.  </br></br>Meddelandetexten styrs av Google och kan inte ändras.   


**Var och när meddelandet visas**
* Meddelandet visas när användarna trycker på **Skicka data** för att skicka dataloggar till IT-administratören. Vad händer om användarna tillåter åtkomst
* Loggfilerna kopieras till SD-kortet. Vad händer om användarna nekar åtkomst
* De kan fortfarande skicka loggar, men loggarna kopieras inte till enhetens SD-kort. Den andra gången användarna loggar in på företagsportalappen efter att de nekat åtkomst visas kryssrutan **Fråga inte igen** som de kan markera så att meddelandet inte visas igen.

**Om användare tillåter men senare nekar åtkomst visas meddelandet nästa gång användaren försöker skicka loggar.**

Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Lagring** och aktivera behörigheten. Mer information



## För användarna: [Skicka diagnostikdataloggar till IT-administratören via e-post](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)
### För IT-proffs: Informationen i den här tabellen finns också i [Hjälpa användarna att förstå meddelanden från företagsportalappen](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)
iOS-företagsportalappen Användare kan nu använda Microsoft Outlook eller andra e-postappar för att skicka diagnostikloggar till IT-administratören.

Tidigare gick det endast att använda den inbyggda appen. Stödet har förbättrats för Apples DEP (Device Enrollment Program) och företagsregistrerade enheter.
* Mer information finns i [Du uppmanas att identifiera din enhet när du försöker registrera dig](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device)
* I användarens lista över registrerade enheter visas nu en grön bockmarkering bredvid den enhet som användaren använder för tillfället.

Innan den här markeringen lades till kunde inte användarna avgöra vilken registrerad enhet de använde.
* [Windows företagsportalapp](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Microsoft samlar automatiskt in anonymiserade data om prestanda och användning av företagsportalen för att kunna förbättra Microsofts produkter och tjänster.](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

Slutanvändare kan inaktivera datainsamling med inställningen Användningsdata på sin enhet, men administratörer har ingen kontroll över datainsamlingen och kan inte ändra slutanvändarens val för den här inställningen.
* November 2015
* Apphantering Intune stöder MAM-principer för hantering av mobilprogram som bidrar till att förhindra att företagsdata läcks till konsumentappar och konsumenttjänster. Tidigare tillämpades dessa principer endast på mobila appar som kördes på enheter som också hade registrerats för hantering av mobilenheter (MDM) i Intune.
* Med den här månadens uppdatering utökar Intune sina MAM-funktioner till nya typer av enheter. Förutom enheter som registrerats i Intune kan du nu använda MAM-principer på
* enheter som hanteras av någon annan enhetshanteringslösning (MDM) enheter som inte har registrerats i något enhetshanteringssystem, vanligtvis BYOD-enheter (Bring Your Own Device).
* Mer information om de nya MAM-funktionerna finns i följande blogginlägg: Förbättra hanterad mobilproduktivitet
* Nya Microsoft Enterprise Mobility-funktioner Här beskrivs några viktiga funktioner och ytterligare information om Intunes MAM-funktioner:
* Företagsdata isoleras från konsumentdata i appar som exponerats för Intune, inklusive Office Mobile-appar, tredjepartsappar som har integrerat Intune SDK eller affärsappar som finns i Intune.

Företagsdata kan delas (**klipp ut/kopiera/klistra in**) mellan företagsappar samtidigt som delningen av företagsdata till personliga appar förhindras.

### Mer information finns i [Hur MAM-principer skyddar appdata](https://technet.microsoft.com/library/mt627825.aspx).
 Det här exemplet, [Använda Microsoft Word-appen för arbete och personliga uppgifter](https://technet.microsoft.com/library/mt627827.aspx), visar hur delning av företagets data till personliga appar förhindras. Principer som förebygger förlust av viktiga data, t.ex. en PIN-kod för varje app, ”spara som”-kontroller och hanterad datadelning mellan appar.
* En lista över alla principer finns i [Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx). Word, Excel, PowerPoint, Outlook, OneNote och OneDrive för företag innehåller de nya funktionerna och kan hanteras med och utan enhetsregistrering.
* Funktionerna som skyddar mot förlust av data är inbyggda i Office-standardapparna i Apple Store eller Google Play-butiken och kräver inte appomslutning eller separat inläsning. Information om hur du kommer igång finns i [Komma igång med principer för hantering av mobilappar i Azure Portal](https://technet.microsoft.com/library/mt627830.aspx).
* Information om hur du konfigurerar och distribuerar principer för hantering av mobilappar finns i [Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx) När slutanvändarna autentiseras mot appen med sina företagsuppgifter konfigureras funktionerna mot dataförlust automatiskt.
* Avsnittet [Slutanvändarens upplevelse i appar som är associerade med Microsoft Itunes hanteringsprinciper för mobilappar](https://technet.microsoft.com/library/mt627827.aspx) innehåller vissa exempelscenarier som illustrerar hur användaren kommer åt OneDrive på iOS- och Android-enheter. Fungerar både på iOS- och Android-enheter.
* Listan över [Microsoft-appar som du kan använda med Microsoft Intunes hanteringsprinciper för mobilprogram](https://technet.microsoft.com/library/dn708489.aspx) har uppdaterats så att de senaste apparna visas. Enhetshantering

Mac OS X-enhetshantering Nu kan du registrera och hantera Mac OS X-enheter med Intune.

Du kan göra följande med dina Mac OS X-enheter: Registrera enheter som ska hanteras av Intune.

Läs [Konfigurera iOS- och Mac-hantering med Microsoft Intune](https://technet.microsoft.com/library/dn408185.aspx)
* Kontrollera enhetsinställningar med en allmän konfigurationsprincip. Läs [Inställningar för Mac OS X-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx) Distribuera Mac OS X-inställningar som du skapat med Apple Configurator.
* Läs [Anpassade principinställningar för Mac OS X i Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx)

Samla in maskin- och programvaruinventering från Mac OS X-enheter. Läs [Förstå dina enheter med inventering i Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx)

Kör nya rapporter som visar information om de Mac OS X-enheter som du hanterar.  Läs [Förstå Microsoft Intune-aktiviteter med hjälp av rapporter](https://technet.microsoft.com/library/dn646977.aspx)

### Nya inställningar för webbläsaren Edge för Windows 10 enheter
Nya inställningar har lagts till i den allmänna konfigurationsprincipen för Windows 10 som hjälper dig att hantera inställningar och funktioner i Microsoft Edge-webbläsaren.

* Läs [Inställningar för Windows 10-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx) E-postprofiler

* En ny e-postprofilprincip har lagts till för Windows 10-baserade datorer och mobilenheter. Läs [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](https://technet.microsoft.com/library/dn646984.aspx)

* Nya inställningar för efterlevnadsprinciper Följande nya inställningar för säkerhets- och systemprinciper har lagts till i listan med efterlevnadsprinciper: Om du vill säkerställa att de senaste uppdateringarna är installerade på enheter med Windows 8.1 eller senare som har åtkomst till företagets resurser använder du inställningen **Kräv automatiska uppdateringar**. Du kan även ange vilken typ av uppdateringar som ska installeras automatiskt – antingen alla uppdateringar som har markerats som viktiga att installera, eller alla uppdateringar som har markerats som viktiga eller rekommenderade.

### En fullständig lista över inställningar för efterlevnadsprinciper finns i [Hantera enheters efterlevnadsprinciper för Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx)
Med den nya inställningen **Kräv lösenord när enheten lämnar inaktivt läge** i kombination med den befintliga inställningen **Minuter av inaktivitet innan lösenord måste anges** kan du skapa en efterlevnadsinställning som kräver att slutanvändarna anger ett lösenord innan de kan använda en enhet som har varit inaktiv en viss tid. Nya alternativ för principer för villkorlig åtkomst Du kan tillämpa principer för villkorlig åtkomst för **alla användare** i antingen nya eller befintliga principer för villkorlig åtkomst.
* Alla användare med licens för Intune och Office 365 måste registrera sina enheter, och om enhetsplattformen inte stöds av Intune blockeras åtkomsten för klientprogram som använder [inloggning baserat på Active Directory-autentisering (modern autentisering)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/)
    * Du kan också ange att principen för villkorlig åtkomst gäller för **alla plattformar**.
    * Alla klientprogram som använder [inloggning baserat på Active Directory-autentisering (modern autentisering)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) styrs av principen för villkorlig åtkomst, och om plattformen inte stöds av Intune så blockeras åtkomsten.
    * Ändringar och uppdateringar i Microsofts företagsportal
    * Följande ändringar har gjorts för företagsportalens appar i den här versionen:

    **Android**: En välkomstskärm har lagts till i Android-företagsportalappen som hjälper användare att förstå syftet med företagsportalappen.
* Den här skärmen är avsedd att minska nedladdningar av appen av användare vars företag inte är Intune-prenumeranter. **iOS**: Intune har nu stöd för registrering av Mac OS X-enheter via [företagsportalens webbplats](https://portal.manage.microsoft.com). Anvisningar finns i [Registrera din Mac OS X-enhet i Intune](https://technet.microsoft.com/library/mt598622.aspx) **Webbplatsen för företagsportalen**: Användare som har registrerat sina enheter i Intune kan nu återställa sina lösenord med hjälp av alternativet **Återställ lösenord** på företagsportalens webbplats.
* Tidigare kunde endast IT-administratörer återställa användarnas lösenord.
* Alternativet Återställ lösenord stöds inte för Windows 8.1- och Windows RT-enheter och alternativet visas endast när enheterna har registrerats i hantering av mobila enheter (MDM) eller MDM med Exchange ActiveSync. Användarinstruktioner finns i [Återställa lösenordet](https://technet.microsoft.com/library/mt590895.aspx)

Licensieringsändringar för globala administratörer
* [I oktober meddelade vi att globala administratörer (kallas även innehavaradministratörer) kunde fortsätta att utföra dagliga administrationsuppgifter utan en separat Intune- eller EMS-licens (Enterprise Mobility Suite).](https://technet.microsoft.com/library/jj839713.aspx)
* [Om globala administratörer vill använda tjänsten, t.ex. för att registrera sina egna enheter, företagsenheter eller för att använda Intunes företagsportal, behöver de dock en Intune- eller EMS-licens precis som andra användare.](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

Nedan finns ytterligare information.


### Intune-företagsportalen är den plats där användare kan:
**registrera sina enheter**
* visa statusen för sina enheter
* ladda ned programvara som en global administratör har distribuerat till organisationen
* hitta länkar som publicerats av den globala administratören som leder till information om hur användaren kontaktar sin IT-avdelning.
* [Lär dig mer om företagsportalen](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) och [hur du anpassar den](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal)
* Den person som registrerar sig för att köpa Intune eller EMS på uppdrag av en organisation blir automatiskt den första globala administratören i klientorganisationen.
* I höstas började Intune att automatiskt tilldela en Intune- eller EMS-licens till den första globala administratören som en del av migreringen till [Office 365-portalen](http://portal.office.com/) och utfasningen av [Intune-kontoportalen](http://account.manage.microsoft.com/).
* Ytterligare globala administratörer som läggs till kan fortsätta med den dagliga administrationen utan en separat Intune- eller EMS-licens.
* Men om de börjar agera som slutanvändare och registrera sina egna enheter (eller företagets) eller ladda ned programvara från företagsportalen behöver de en licens precis som alla andra användare.
* Ändringen kommer att implementeras i faser med början i januari 2016.

**För Microsoft-partner bör den här ändringen inte påverka din möjlighet att administrera tjänsten för dina kunders räkning.**
* För slutanvändaråtgärder krävs en Intune- eller EMS-licens för att registrera enheten och komma åt eller ladda ned programvara från företagsportalen.
* Om du har frågor om den här ändringen är du välkommen att kontakta Intunes supportteam:
* Microsoft Intune-supportkanaler Community-support
* För allmän feedback om Microsoft Intune, inklusive förfrågningar om designändringar eller buggar, besöker du [webbplatsen för Intune-feedback](https://microsoftintune.uservoice.com/)
* Nyheter i Intune-dokumentation – november 2015
* Nytt innehåll
* [Inställningar för Mac OS X-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx): Så här kontrollerar du inställningar för enheter och funktioner för Mac OS X-enheter.

## [Anpassade principinställningar för Mac OS X i Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx): Så här distribuerar du Mac OS X-enhetsinställningar som du skapat med hjälp av verktyget Apple Configurator.

### [Konfigurera apprinciper som förhindrar dataförlust med Microsoft Intune](https://technet.microsoft.com/library/mt627825.aspx): Innehåller information om scenarierna som principerna för mobilappshantering har stöd för och hur principerna fungerar för att skydda data.
[Komma igång med principer för hantering av mobilappar i Azure Portal](https://technet.microsoft.com/library/mt627830.aspx): Vad du behöver för att komma igång med Azure Preview Portal för hanteringsprinciper för mobilappar.

[Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx): Innehåller en stegvis genomgång av hur du skapar principer för hantering av mobilappar på Azure Preview Portal. [Övervaka hanteringsprinciper för mobilappar med Microsoft Intune](https://technet.microsoft.com/library/mt627824.aspx): Information om hur du kan övervaka dina principer för hantering av mobilappar med Azure Preview Portal. [Hanteringsprinciper för mobilappar och funktionen Öppna i för iOS i Microsoft Intune](https://technet.microsoft.com/library/mt627821.aspx): Information om hur hanteringsprinciper för mobilappar fungerar med funktionen Öppna i för iOS.

[Slutanvändarens upplevelse i appar som är associerade med Microsoft Itunes hanteringsprinciper för mobilappar](https://technet.microsoft.com/library/mt627827.aspx): Slutanvändarnas upplevelse när de använder appar som är associerade med hanteringsprincipen för mobilappar. [Rensa hanterade företagsdata från appar med Microsoft Intune](https://technet.microsoft.com/library/mt627826.aspx): Hur du tar bort företagsdata från appar.
### Uppdaterat innehåll
[Inställningar för Windows 10-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx): Nya inställningar för Edge-webbläsaren har lagts till.

[Konfigurera iOS-hantering med Microsoft Intune](http://technet.microsoft.com/library/dn408185.aspx): Information om hur du registrerar Mac OS X-enheter har lagts till. [Förstå dina enheter med inventering i Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx): Information om inventeringen som samlas in från Mac OS X-enheter har lagts till.

Dessutom har avsnittet uppdaterats med den senaste informationen för alla enhetsplattformar. [Förstå Microsoft Intune-åtgärder med hjälp av rapporter](https://technet.microsoft.com/library/dn646977.aspx): Information har lagts till om de två nya rapporterna som används för att visa information om dina hanterade Mac OS X-enheter.


### [Hantera efterlevnadsprinciper för enheter för Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx): Information har lagts till om de nya efterlevnadsprinciperna som kräver automatiska uppdateringar och krav på lösenord när en enhet lämnar inaktivt läge.
[Hantera email åtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx): Information har lagts till om möjligheten att använda principen för villkorlig åtkomst för alla plattformar och alla användare.

|[Hantera SharePoint onlineåtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx): Information har lagts till om möjligheten att använda principen för villkorlig åtkomst för alla plattformar och alla användare.|Oktober 2015|
|------------|---------------|
|Uppdateringar för villkorlig lokal åtkomst till Exchange|**Nu kan du tillåta åtkomst till Exchange Active Sync-e-post för kompatibla enheter som registrerats i Intune när den globala Exchange-regeln ställts in att blockera eller sätta i karantän** Fram till nu var du tvungen att ställa in den globala Exchange-standardregeln på **Tillåt** för att tillåta åtkomst till e-post på registrerade och kompatibla enheter|
|Med den här uppdateringen av tjänsten är inställningen inte längre ett krav för villkorlig åtkomst.|Om Exchange-miljön kräver att din globala standardregel ställs in till **Blockera/Karantän** markerar du bara kryssrutan **Åsidosätt standardregel** på den lokala sidan för principer för villkorlig åtkomst för Exchange.|


>Avsnittet [Hantera email åtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) innehåller mer information om reglerna och meddelandena som visas för slutanvändaren.

>[&larr; ****Ny karantänupplevelse med en enda klickning** Vi har förenklat karantänupplevelsen för e-post och lagt till stöd för registrering med en enda klickning.**](whats-new-in-microsoft-intune.md)    


<!--HONumber=May16_HO2-->


