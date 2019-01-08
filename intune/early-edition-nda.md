---
title: Tidig utgåva – Microsoft Intune
titlesuffix: ''
description: Tidig utgåva av Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/3/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 21d89d97355430f071763391d69fe332cf3ef369
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642905"
---
# <a name="the-early-edition-for-microsoft-intune---december-2018"></a>Den tidiga utgåvan för Microsoft Intune – December 2018

> [!Note]
> Sekretessavtalsmeddelande: Följande ändringar är under utveckling för Intune. Den här informationen har mycket begränsad spridning, i enlighet med sekretessavtalet. Sprid inte den här informationen vidare på sociala medier eller offentliga webbplatser, till exempel Twitter, UserVoice, Reddit och så vidare. 

Den **tidiga utgåvan** innehåller en lista med funktioner, som delas i enlighet med sekretessavtalet, som ingår i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte den här informationen på Twitter, UserVoice eller på något annat sätt med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Appdistribution för Android Enterprise APP-WE <!-- 1171203 -->
För Android-enheter i ett distributionsscenario med en appskyddsprincip utan registrering (APP-WE) kommer du att kunna använda hanterade Google Play för att distribuera store-appar och LOB-appar till användare. Mer specifikt kan IT-avdelningen kan ge slutanvändarna en app-katalog och installationsupplevelse som inte längre kräver att slutanvändare minskar säkerhetspositionen för sina enheter genom att tillåta installationer från okända källor. Dessutom kan det här distributionsscenariot ge en förbättrad slutanvändarupplevelse.

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nya alternativ för att automatiskt ansluta och bevara regler när du använder DNS-inställningarna på Windows 10 och senare enheter <!-- 1333665, 2999078 -->
I Windows 10 och senare enheter kommer du att kunna skapa en VPN-profil som innehåller en lista över DNS-servrar för att lösa domäner, som till exempel contoso.com. Detta omfattar nya inställningar för namnmatchning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj  **Windows 10 och senare** för plattform > välj **VPN** för Profiltyp > **DNS-inställningarna** >**Lägg till**): 

- **Anslut automatiskt**: När den är **Aktiverad**, ansluter enheten automatiskt till VPN-anslutningen när en enhet kontaktar en domän som du anger, t.ex contoso.com.
- **Beständig**: Som standard är alla NRPT-regler (principtabell för namnmatchning) aktiva så länge enheten är ansluten med hjälp av den här VPN-profilen. När inställningen är **Aktiverad** för en NRPT-regel förblir regeln aktiv på enheten, även om VPN-anslutningen kopplas bort. Regeln gäller tills VPN-profilen tas bort eller tills regeln tas bort manuellt, vilket kan göras med hjälp av PowerShell.

[Windows 10 VPN-inställningar](vpn-settings-windows-10.md) beskriver den aktuella listan över inställningar. 

### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user----1333642-eeready---"></a>Använda S/MIME för att kryptera och signera flera enheter för en användare <!-- 1333642 eeready -->
S/MIME-krypteringen av e-post använder en ny importerad certifikatprofil som kommer att stödjas (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj plattform > profiltypen **PKCS-importerat certifikat**). Du kan importera certifikat i PFX-format i Intune. Intune kan sedan leverera samma certifikat till flera enheter som registrerats av en enda användare. Detta omfattar även följande:

- Den interna e-postprofilen för iOS har stöd för att aktivera S/MIME-kryptering med importerade certifikat i PFX-format.
- Den interna e-postappen på Windows Phone 10-enheter använder S/MIME-certifikatet automatiskt.
- Det privata certifikatet kan levereras över flera plattformar. Men alla e-postappar har inte stöd för S/MIME.
- På andra plattformar kan du behöva konfigurera e-postappen manuellt för att aktivera S/MIME.  
- E-postappar som har stöd för S/MIME-kryptering kan hantera hämtning av certifikat för S/MIME-kryptering av e-post på ett sätt som MDM inte stöder, till exempel genom att läsa från utgivarens certifikatarkiv.

Stöds på: Windows, Windows Phone 10, macOS, iOS och Android

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Hjälp- och supportsidan i företagsportalappen för Windows <!-- 1488939 -->
En ny sida läggs till i företagsportalappen för Windows. Sidan Hjälp och support ger kontaktinformation för support. Slutanvändarna kommer också att kunna skicka loggar från företagsportalen i händelse av att de har problem. Sidan innehåller också ett avsnitt med frågor och svar för att hjälpa slutanvändarna.

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Använd identifiering av betrott nätverk för VPN-profiler på Windows 10-enheter <!-- 1500165 -->
När du använder identifiering av betrott nätverk, kommer du att kunna förhindra VPN-profiler från att automatiskt skapa en VPN-anslutning när användaren redan är i ett betrott nätverk. Du kommer att kunna lägga till DNS-suffix om du vill aktivera identifiering av betrott nätverk på enheter som kör Windows 10 och senare (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **VPN** för profiltyp).
[Windows 10-VPN-inställningar](vpn-settings-windows-10.md) visar en lista över aktuella VPN-inställningar.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK stöder 256-bitars krypteringsnycklar <!-- 1832174 -->
Intune App SDK för Android använder 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciperna. SDK fortsätter att stödja 128-bitars nycklar för kompatibilitet med innehåll och appar som använder äldre versioner av SDK.

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917---"></a>Aktiverade delade datorinställningar i Intune-profil <!-- 1907917 -->
För närvarande kan du konfigurera delade datorinställningar på Windows 10 desktop-enheter som använder en anpassad OMA-URI-inställning. En ny profil kommer att läggas till i konfigurera delade datorinställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10 och senare** > **Delad fleranvändarenhet**).
Gäller för: Windows 10 och senare, Windows 10 Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Uppdatering av Intune-principers autentiseringsmetod och installation av företagsportalappen  <!-- 1927359 -->
På enheter som redan har registrerats via Installationsassistenten med någon av Apples metoder för registrering av företagsenheter, stöder Intune inte längre företagsportalen om den installeras manuellt av slutanvändarna från App Store. Den här ändringen gäller endast när du autentiserar med Apple-installationsassistenten under registreringen. Den här ändringen påverkar också bara iOS-enheter som registrerats via:  
* Apple configurator
* Apple Business Manager
* Apple School Manager
* Apples program för enhetsregistrering (DEP)

Om användare installerar företagsportalappen från App store och sedan försöker att registrera enheterna genom den, får de ett felmeddelande. Dessa enheter kommer förväntas att bara använda företagsportalen när den har skickats automatiskt av Intune under registreringen. Profiler för registrering i Intune i Azure-portalen kommer att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Om du vill att dina DEP-enhetsanvändare ska ha företagsportalen behöver du ange dina preferenser i en registreringsprofil. Dessutom kommer skärmen **Identifiera din enhet** i företagsportalappen snart att bli föråldrad.  
För att installera företagsportalen på redan registrerade DEP-enheter, måste du gå till Intune > Klientappar, och skicka den som en hanterad app med konfigurationsprinciper för appar. Information om hur du utför dessa steg kommer att ges i framtida dokument.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>Icke-administratörer kan aktivera BitLocker på Windows 10-enheter som är anslutna till Azure AD<!-- 2147379 -->
När du aktiverar BitLocker-inställningar på Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10 och senare** för plattform > **Endpoint protection** för Profiltyp > **Windows-kryptering**), lägger du till BitLocker-inställningar. Den här uppdateringen innehåller en ny inställning för BitLocker för att låta standardanvändare (icke-administratörer) aktivera kryptering. De aktuella inställningarna finns i [Endpoint protection-inställningar för Windows 10](endpoint-protection-windows-10.md#windows-encryption).

### <a name="intune-app-pin----2298397---"></a>Intune-appens PIN-kod <!-- 2298397 -->
Som IT-administratör kommer du att kunna konfigurera hur många dagar som en användare kan vänta tills Intune-appens PIN-kod måste ändras. Den nya inställningen är tillgänglig i Azure Portal genom att välja **Intune** > **Klientappar** > **Appskyddsprinciper** > **Skapa princip** > **Inställningar** > **Åtkomstbehörigheter**. Den här funktionen blir tillgänglig för iOS- och Android-enheter. Den här inställningen stöder ett positivt heltalsvärde.

### <a name="new-windows-10-update-settings----2626030-2512994---"></a>Nya Windows 10 Update-inställningar <!-- 2626030 2512994 -->
För dina Windows 10-uppdateringsringar, kommer du att kunna:
- återställa de ursprungliga inställningarna för automatisk uppdatering på en Windows 10-dator på datorer som kör *uppdateringen från oktober 2018*
- Konfigurera en ny programuppdateringsplats som gör att du kan blockera eller tillåta användarna att pausa uppdateringsinstallationen från *Inställningar* på deras datorer. 



### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS e-postprofiler kan använda S/MIME-signering och kryptering <!-- 2662949 -->
Du kommer att kunna skapa en e-postprofil som innehåller olika inställningar. Detta inkluderar S/MIME-inställningar som kan användas för signering och kryptering av e-postmeddelanden på iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > **E-post** för profiltyp).

[iOS e-konfigurationsinställningar](email-settings-ios.md) visar en lista över de aktuella inställningarna.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>Hoppa över flera skärmar för installationsassistenten på en iOS DEP-enhet <!-- 2687509 -->
Förutom de skärmar som du kan hoppa över just nu, kommer du att kunna ange att iOS DEP-enheter hoppar över följande skärmar i installationsassistenten när en användare registrerar enheten: Skärmton, Sekretess, Android-migrering, Start-knapp, iMessage och FaceTime, Registrering, Bevaka migrering, Utseende, Skärmtid, Programuppdatering, SIM-installation.
Om du vill välja vilka skärmar som ska hoppas över, går du till **Enhetsregistrering** > **Apple-registrering** > **Tokens för registreringsprogram** > välj en token > **Profiler** > välj en profil > **Egenskaper** > **Anpassning av installationsassistenten** > välj **Dölj** för alla skärmar som du vill hoppa över > **OK**.

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Vissa inställningar för BitLocker har stöd för Windows 10 Pro-versionen <!-- 2727036 -->
Du kommer att kunna skapa en konfigurationsprofil som anger endpoint protection-inställningar för Windows 10-enheter, inklusive BitLocker. Detta lägger till stöd för Windows 10 Professional-versionen för vissa BitLocker-inställningar. De aktuella Windows 10-inställningarna finns i [Endpoint protection-inställningar för Windows 10](endpoint-protection-windows-10.md#windows-encryption).


### <a name="intune-device-reporting-fields----2748738---"></a>Intune-enhetens rapportfält <!-- 2748738 -->
Intune ger ytterligare fält för enhetsrapportering inklusive Android-tillverkare, modell och version av säkerhetsppdatering samt iOS-modell. I Intune, är dessa fält tillgängliga genom att välja **Klientappar** > **Appskyddsstatus** och sedan välja **Appskyddsrapport: iOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodell (Android och iOS) och lägsta inställning för version av Android-säkerhetsuppdatering. 

### <a name="intune-device-reporting-fields----2748738---"></a>Intune-enhetens rapportfält <!-- 2748738 -->
Intune ger ytterligare fält för enhetsrapportering inklusive Android-tillverkare, modell och version av säkerhetsppdatering samt iOS-modell. I Intune, är dessa fält tillgängliga genom att välja **Klientappar** > **Appskyddsstatus** och sedan välja **Appskyddsrapport: iOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodell (Android och iOS) och lägsta inställning för version av Android-säkerhetsuppdatering. 

### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal----2809362---"></a>Konfiguration av delad enhet har bytt namn till Meddelande på låsskärmen för iOS-enheter i Azure Portal <!-- 2809362 -->
När du skapar en profil för iOS-enheter ska du kunna lägga till inställningar för **Konfiguration för delad enhet** för att visa specifik text på låsskärmen. Det här innehåller följande ändringar: 

- Inställningarna **Konfiguration för delad enhet** i Azure-portalen har bytt namn till ”Meddelande på låsskärmen (endast övervakat)” (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > välj **Enhetsfunktioner** för Profiltyp > **Meddelande på låsskärmen**).
- När du lägger till meddelande på låsskärmen, kan du infoga ett serienummer, ett enhetsnamn eller ett annat enhetsspecifikt värde som en variabel i **resurstagginformation**. Du kan till exempel ange `Device name: {{device name}}` eller `Serial number is {{serial number}}` med hjälp av klammerparenteser. [iOS-token](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) visar en lista över de tillgängliga token som kan användas.

[Inställningar för att visa meddelanden på låsskärmen](shared-device-settings-ios.md) visar en lista över de aktuella inställningarna.

### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564--"></a>Mer detaljerade felmeddelanden för registreringsbegränsning <!-- 3111564-->
Mer detaljerade felmeddelanden blir tillgängliga när registreringsbegränsningar inte har uppfyllts. Om du vill se dessa meddelanden går du till **Intune** > **Felsök** > och markerar tabellen Registreringsfel.

### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Inställningar för nytt meddelande, tips och keyguard för enhetsägare av Android Enterprise-enheter <!-- 3201839 3201843 -->
Den här uppdateringen innehåller flera nya funktioner på Android Enterprise-enheter vid körning som enhetsägare. Om du vill använda dessa funktioner, gå till **Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Android Enterprise** > i **Profiltyp**, välj **Endast enhetens ägare** > **Enhetsbegränsningar**.
Nya funktioner som ingår: 
- Inaktivera systemmeddelanden till att inte visas, inklusive inkommande anrop, systemaviseringar, systemfel och mer
- Föreslår hoppa över start av självstudier och tips för appar som öppnas för första gången
- Inaktivera avancerad keyguard-inställningar, till exempel kamera, meddelanden, upplåsning med fingeravtryck med mera

Om du vill visa de aktuella inställningarna går du till [Enhetsbegränsningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Enhetsägda Android Enterprise-enheter kan använda Always On VPN-anslutningar <!-- 3202194 -->
I den här uppdateringen kan du använda VPN-anslutningar som alltid är aktiva på Android Enterprise-enheter. Ständiga VPN-anslutningar förblir anslutna eller återansluter omedelbart när användaren låser upp sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. Du kan också placera anslutningen i ”låst” läge, vilket blockerar all nätverkstrafik tills VPN-anslutningen aktiveras.
Du kan aktivera VPN-anslutningar som alltid är aktiva i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar** för enhetsägare endast > **Anslutningar**. Om du vill visa de aktuella inställningarna går du till [Enhetsbegränsningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Ny inställning för slutprocesser i Aktivitetshanteraren på Windows 10-enheter <!-- 3285177 --> 
Den här uppdateringen innehåller en ny inställning för att avsluta processer med hjälp av Aktivitetshanteraren på Windows 10-enheter. Med hjälp av en profil för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform** , välj **Windows 10** > i **Profiltyp**, välj **Enhetsbegränsningar** > **Allmänna** inställningar), väljer du att tillåta eller förhindra den här inställningen.
Om du vill visa de aktuella inställningarna går du till [Inställningar av begränsningar för Windows 10-enheter](device-restrictions-windows-10.md).
Gäller för: Windows 10 och senare

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrativa mallar finns i offentlig förhandsversion och flyttas till deras egna konfigurationsprofil <!-- 3322847 -->
Administrativa mallar i Intune (**Enhetskonfiguration** > **Administrationsmallar**) är för tillfället i privat förhandsvisning. I denna uppdatering: De administrativa mallarna innehåller ungefär 300 inställningar som kan hanteras i Intune. De här inställningarna fanns tidigare endast i redigeraren.
Administrativa mallar finns i offentlig förhandsversion, administrativa mallar flyttar från **Enhetskonfiguration** > **Administrationsmallar** till **Enhetskonfiguration** > **Profiler** >**Skapa profil** > i **Plattform**, välj  **Windows 10 och senare**i **Profiltyp**, välj **Administrationsmallar**.
Rapportering är aktiverad och gäller för: Windows 10 och senare


<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Använd Microsofts rekommenderade inställningar med säkerhetsbaslinjer <!-- 2055484 -->
Intune integrerar med andra tjänster som fokuserar på säkerhet, inklusive Windows Defender ATP och Office 365 ATP. Kunder efterfrågar en gemensam strategi och en sammanhängande uppsättning säkerhetsarbetsflöden från slutpunkt till slutpunkt för alla Microsoft 365-tjänster. Vårt mål är att optimera strategier och skapa lösningar som kan hantera säkerhetsåtgärder och vanliga administratörsuppgifter. I Intune vill vi uppnå det här målet genom att publicera en uppsättning Microsoft-rekommenderade ”säkerhetsbaslinjer” (**Intune** > **Security baselines** ((Säkerhetsbaslinjer)).  En administratör kommer att kunna skapa säkerhetsprinciper direkt från dessa baslinjer, och sedan distribuera dem till sina användare. De kan också anpassa rekommendationerna om bästa praxis för att uppfylla behoven i deras organisation. Intune kontrollerar att enheterna uppfyller baslinjerna och meddelar administratören om användare eller enheter inte uppfyller efterlevnadskraven.

### <a name="scope-tags-for-apps---1081941---"></a>Omfattningstaggar för appar <!--1081941 -->
Du kommer att kunna skapa omfångstaggar som begränsar åtkomsten till Intune-resurser. Lägg till en omfångstagg till en rolltilldelning och lägg sedan till omfångstaggen i en konfigurationsprofil. Rollen får endast åtkomst till resurser med konfigurationsprofiler som har matchande omfångstaggar (eller inga omfångstaggar).
Om du vill skapa en omfångstagg väljer du **Intune-roller** > **Scope (Tags) (Omfång (taggar))** > **Skapa**.
För att lägga till en omfångstagg till en rolltilldelning väljer du **Intune-roller** > **Alla roller** > **Princip- och profilhanterare** > **Tilldelningar** > **Scope (Tags)** (Omfång (taggar)).
För att lägga till en omfångstagg till en konfigurationsprofil väljer du **Enhetskonfiguration** > **Profiler** > välj en profil > **Egenskaper** > **Scope (Tags)** (Omfång (taggar)).

### <a name="tenant-health-dashboard----1124854---"></a>Instrumentpanelen Hälsa för klientorganisation <!-- 1124854 -->
På sidan med klientorganisationens status i Intune hittar du information om klientorganisationens status på ett och samma ställe. Sidan är uppdelad i fyra delar:  
- **Information om klientorganisationen**: Innehåller information, till exempel MDM-utfärdare, totalt antal registrerade enheter i klientorganisationen och antal licenser. I det här avsnittet visas även den aktuella versionen av tjänsten för din klientorganisation.
- **Status för anslutningsprogrammet**: Innehåller information om konfigurerade anslutningsprogram, till exempel Apple VPP, Microsoft Store för företag och certifikatanslutningar. Baserat på deras aktuella tillstånd är anslutningsapparna flaggade med *Felfri*, *Varning* eller *Ej felfri*.
- **Hälsotillstånd för Intune-tjänsten**: Innehåller aktiva incidenter eller avbrott i klientorganisationen. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office ([https://portal.office.com](https://portal.office.com)).
- **Nytt i Intune**: Innehåller aktiva meddelanden för din klientorganisation, t.ex. aviseringar om att klientorganisationen har fått de senaste funktionerna för Intune. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Distribuerade WIP-principer utan användarregistrering <!-- 1434452 -->
WIP-principer (Windows Information Protection) kommer att kunna distribueras utan att MDM-användare behöver registrera sina Windows 10-enheter. Med den här konfigurationen kan företag skydda sina företagsdokument baserat på WIP-konfigurationen, samtidigt som användarna kan fortsätta att hantera sina egna Windows-enheter. När dokument skyddas med en WIP-princip kan skyddade data rensas selektivt av en Intune-administratör. Genom att välja användaren och enheten, och skicka en rensningsbegäran, blir alla data som skyddades via WIP-principen oanvändbara. Från Intune på Azure-portalen väljer du **Mobilapp** > **Selektiv radering av app**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>APP-inställningar (App Protection Policy) för webbdata <!-- 2662995 -->
Principinställningarna för webbinnehåll på både Android och iOS-enheter kommer att uppdateras så att de blir bättre på att hantera både http- och https-länkar liksom dataöverföring via universella iOS-länkar och Android App-länkar.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-token som används av en annan MDM <!-- 1488946 -->
Intune identifierar och visar information om en token för volyminköpt Apple-program (VPP) används av både Intune och en annan MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Tillbakadragna enheter i instrumentpanelen för enhetsefterlevnad <!-- 1981119 -->
I en kommande uppdatering tas tillbakadragna enheter bort från instrumentpanelen för enhetsefterlevnad. Detta ändrar dina efterlevnadsnummer.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Ändra i uppdateringsprocessen för lokala anslutningsappar <!-- 2277554 -->
Baserat på feedback från kunder kommer det sätt som uppdateringar av lokala anslutningsappar sker på att ändras. När du först installerar en lokal anslutningsapp sker uppdateringar automatiskt. Den här ändringen börjar i och med den nya PFX-certifikatanslutningsappen för Microsoft Intune och kommer därefter att distribueras till andra typer av lokala anslutningsappar. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Kontrollera Configuration Manager-kompatibilitet <!-- 2192052 -->
En kommande uppdatering innehåller en ny kompatibilitetsinställning för System Center Configuration Manager (**Enhetskompatibilitet** > **Principer** > **Skapa princip** > **Windows 10**). Configuration Manager skickar signaler till Intune-kompatibilitet. Med hjälp av Intune-inställningen kan du kräva att alla Configuration Manager-signaler returnerar ”kompatibel”.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd kommer enheten inte att vara kompatibel i Intune.

Gäller för Windows 10 och senare



## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).



