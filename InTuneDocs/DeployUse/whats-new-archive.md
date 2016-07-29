---
title: Nyhetsarkiv | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 458ee268d0c6a8fa6cbe6cc23ad07f0e45eff3e5


---
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



## September 2015
### Uppdateringar för mobil enhet och apphantering
**Alla iOS-hanteringsfunktioner har nu stöd för iOS 9** Mer information om hanteringsfunktioner för iOS 9 finns i [det här blogginlägget](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx).

**Ny mobilappskonfigurationsprincip för iOS** Använd den nya mobilappskonfigurationsprincipen för att automatiskt ange inställningar som en iOS-app kan behöva under körning. Du kan till exempel ange en nätverksport eller ett användarnamn. Mer information finns i [Konfigurera appar med konfigurationsprinciper för mobilappar i Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx).

**Enklare apphantering för iOS 9-användare**
 I den här versionen kan du placera redan distribuerade appar under Intune-hantering för iOS 9-användare. När det gäller tidigare versioner av iOS måste du fortfarande be användaren att avinstallera appen manuellt innan den hanterade appen kan installeras i Intune om du distribuerar en app och det redan finns en ohanterad version av appen på enheten.

 Men från och med den här versionen av Intune kan du be användare av iOS 9-enheter att tillåta att Intune tar över hanteringen av appen och tillämpar relevanta hanteringsprinciper för mobilprogram.

 **Windows 10-hantering** Använd den nya [allmänna konfigurationsprincipen för Windows 10](https://technet.microsoft.com/library/mt404697.aspx) för att konfigurera lösenord, enhet, webbläsare och andra inställningar för registrerade enheter som kör Windows 10 och Windows 10 Mobile.

 **Skapa och distribuera appar till registrerade Windows 10-enheter** Med den nya programinstallationstypen Windows Installer via MDM (&#42;.msi) kan du skapa och distribuera Windows Installer-appar till registrerade enheter som kör Windows 10. Mer information finns i [Kom igång med appdistribution i Microsoft Intune](https://technet.microsoft.com/library/dn646955.aspx).

### Ändringar och uppdateringar för appar i Microsofts företagsportal
Följande ändringar har gjorts för företagsportalens appar i den här versionen:

**iOS**
* Microsoft samlar automatiskt in anonymiserade data om prestanda och användning av företagsportalen för att kunna förbättra Microsofts produkter och tjänster. Slutanvändare kan inaktivera datainsamling med inställningen Användningsdata på sin enhet, men administratörer har ingen kontroll över datainsamlingen och kan inte ändra slutanvändarens val för den här inställningen.
* Fullständig skärmupplösningsstöd på iPhone 6 och 6 Plus
* Felkorrigeringar för ökad säkerhet

### Nyheter i Intune-dokumentation – september 2015
**Nya frågor**

|Namn|Information|
|----|--------|
|[Inställningar för Windows 10-konfigurationsprinciper i Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx)|Det här är en ny konfigurationsprincip med vilken du kan hantera inställningar och funktioner på enheter som kör Windows 10 och Windows 10 Mobile.
| [Konfigurera appar med konfigurationsprinciper för mobilappar i Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx)|Detta är en ny principtyp som medför att du automatiskt kan tillhandahålla inställningar  som kan krävas när användaren kör en iOS-app. |

**Uppdaterade avsnitt**

|Namn|Information|
|----|-------|
|[Använda principer för att hantera datorer och mobila enheter med Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx)|Uppdaterad med den senaste informationen för att hjälpa dig att förstå och skapa principer.|

## Augusti 2015
### Uppdateringar för mobil enhet och apphantering
* **Villkor** för Intune-registrering och företagsåtkomst hanteras [nu med principer](https://technet.microsoft.com/library/mt405893.aspx). Du kan ha olika uppsättningar med villkor för att uppfylla specifika användargruppskrav. Du kan till exempel distribuera villkor på olika språk till geografiskt definierade användargrupper. Du kan också [redigera dina villkor](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) och ange om du vill öka versionsnumren, vilket kräver att användarna accepterar de nya villkoren innan de kan använda företagsportalen.
* **Flera Intune-principer har döpts om** så att de blir mer konsekventa i produkten och enklare att hitta. En lista över alla tillgängliga Intune-principer finns i [Använda principer för att hantera datorer och mobila enheter med Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx).
* **PKCS #12-certifikatprofiler (.PFX)** finns för Android 4.0 eller nyare och Windows 10 (Desktop och Mobile) och senare. .PFX kräver inte en NDES-server. Lär dig hur du använder PFX-certifikatprofiler i [Ge åtkomst till företagsresurser med hjälp av certifikatprofiler med Microsoft Intune](http://technet.microsoft.com/library/dn818904.aspx)
* **Inställningar för Företagsgränser för Windows 10 Desktop och Mobile** stöder detaljerade VPN-inställningar, vilket förklaras i [Hjälp användarna att ansluta till sitt arbete med hjälp av VPN-profiler](https://technet.microsoft.com/library/dn818905.aspx)
* **OneDrive-appen för Android stöder nu flera identiteter**. Denna och andra uppdateringar av mobilappens hanteringsprinciper beskrivs i [listan över Microsoft-program som du kan hantera](https://technet.microsoft.com/library/dn708489.aspx).
* **Kringgå iOS-aktiveringslåset**. Om företagsägda iOS-enheter skyddas av aktiveringslås, måste du fylla i användarens Apple-ID och -lösenord innan du kan radera eller återaktivera enheten. Det kan skapa utmaningar om en medarbetare lämnar företaget och lämnar in en företagsägd enhet utan att slå av aktiveringslåset. Du kan åtgärda det här problemet genom att använda [förbikoppling av aktiveringslås i Intune](https://technet.microsoft.com/library/mt414176.aspx).

### Villkorlig åtkomst för datorer
Du kan nu konfigurera villkorliga åtkomstprinciper för datorer. Detta medför att Offices skrivbordsappar kan få åtkomst till Exchange Online- och SharePoint Online-tjänster.
Om du vill aktivera en villkorlig åtkomstprincip för datorer, måste datorn vara domänansluten eller följa reglerna.
* Den fullständiga listan med krav för att aktivera villkorlig åtkomst för PC-datorer finns i avsnittet **Komma igång** i [Hantera åtkomst till e-post och SharePoint med Microsoft Intune](http://technet.microsoft.com/library/dn818907).aspx).
* Information om vilka alternativ du kan välja om du vill aktivera villkorlig åtkomst för e-post finns i [Hantera email åtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx).
* Information om vilka alternativ du kan välja om du vill aktivera villkorlig åtkomst för SharePoint Online finns i [Hantera SharePoint onlineåtkomst med Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx).

### Ändringar och uppdateringar för appar i Microsofts företagsportal
Följande ändringar har gjorts för företagsportalens appar i den här versionen:

**Android**

Användarna visas nu anvisningar för enhetsregistrering efter att du har loggat in, om de inte ännu har registrerat sin enhet för hantering.

### Nyheter i Intune-dokumentationen – augusti 2015
**Nya frågor**

|Titel|Information|
|-----|-------|
|[Skydda iOS-enheter med Kringgå Aktiveringslås för Microsoft Intune](https://technet.microsoft.com/library/mt414176.aspx)|Läs mer om hur du kan använda Intune för att kringgå iOS-aktiveringslås när en användare lämnar företaget och returnerar en låst enhet.|

**Uppdaterade avsnitt**

|Titel|Information|
|-----|-------|
|[Microsoft-appar som du kan använda med Microsoft Intunes hanteringsprinciper för mobilprogram](https://technet.microsoft.com/library/dn708489.aspx)|Uppdaterad med den senaste informationen om appar som du kan hantera med hanteringsprinciper för mobilappar.
|[Använda principer för att hantera datorer och mobila enheter med Microsoft Intune](http://technet.microsoft.com/library/dn743712.aspx)|Uppdateras med de senaste principerna som lagts till i Intune.|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Jul16_HO4-->


