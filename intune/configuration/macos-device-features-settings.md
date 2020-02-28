---
title: Funktionsinställningar för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se inställningarna för att konfigurera macOS-enheter för AirPrint och anpassa inloggningsfönstret för att visa eller dölja strömknappar i Microsoft Intune. Se även anvisningar för att hämta IP-adress, sökväg och portinställningar för en AirPrint-server i nätverket. Använd dessa inställningar i en enhetskonfigurationsprofil när du konfigurerar funktioner för macOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: df5b53be159fd082090e61fd736e4c9329644c85
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512746"
---
# <a name="macos-device-feature-settings-in-intune"></a>Funktionsinställningar för macOS-enheter i Intune

I Intune finns vissa inbyggda inställningar för att anpassa funktioner i dina macOS-enheter. Administratörer kan exempelvis lägga till AirPrint-skrivare, välja hur användare ska logga in, konfigurera energikontrollerna, använda autentisering med enkel inloggning och mycket annat.

Du kan använda dessa funktioner för att styra macOS-enheter som en del av din MDM-lösning för hantering av mobilenheter.

I den här artikeln visas inställningarna, tillsammans med en beskrivning av vad varje inställning gör. Här visas även anvisningar för att hämta IP-adress, sökväg och port för AirPrint-skrivare som använder Terminal-appen (emulator). Om du vill ha mer information om enhetsfunktionerna går du till [Lägg till funktionsinställningar för iOS/iPadOS- eller macOS-enhet](device-features-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en macOS-enhetskonfigurationsprofil](device-features-configure.md).

> [!NOTE]
> Dessa inställningar gäller för olika registreringstyper. Vissa inställningar gäller för alla registreringsalternativ. Mer information om de olika registreringstyperna finns i [macOS-registrering](../enrollment/macos-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: Enhetsregistrering och automatisk enhetsregistrering 

- **IP-adress**: Ange skrivarens IPv4- eller IPv6-adress. Om du använder värdnamn till att identifiera skrivare, kan du hämta IP-adressen genom att pinga skrivaren i Terminal-appen. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
- **Sökväg**: Ange sökvägen till skrivaren. Sökvägen är vanligtvis `ipp/print` för skrivare i nätverket. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
- **Port** (iOS 11.0+, iPadOS 13.0+): Ange lyssningsporten för AirPrint-målet. Om du lämnar den här egenskapen tom, kommer AirPrint att använda standardporten.
- **TLS** (iOS 11.0+, iPadOS 13.0+): Välj **Aktivera** för att skydda AirPrint-anslutningar med TLS (Transport Layer Security).

- **Lägg till** AirPrint-servern. Du kan lägga till flera AirPrint-servrar.

Du kan också **Importera** en kommaavgränsad fil (.csv) med en lista över AirPrint-skrivare. När du har lagt till AirPrint-skrivarna i Intune, kan du också **Exportera** listan.

### <a name="get-the-ip-address-and-path"></a>Hämta IP-adress och sökväg

Om du vill lägga till AirPrinter-servrar, behöver du ha skrivarens IP-adress, resurssökväg och port. Följande steg visar hur du hämtar den här informationen.

1. Öppna **Terminal** (från **/Program/Verktyg**) på en Mac som är ansluten till samma lokala nätverk (undernät) som AirPrint-skrivarna.
2. I Terminal-appen skriver du `ippfind` och väljer Retur.

    Observera skrivarinformationen. Du kan exempelvis ange något i stil med `ipp://myprinter.local.:631/ipp/port1`. Den första delen är namnet på skrivaren. Den sista delen (`ipp/port1`) är resurssökvägen.

3. I Terminal skriver du `ping myprinter.local` och väljer Retur.

   Observera IP-adressen. Den visar något i stil med `PING myprinter.local (10.50.25.21)`.

4. Använd värdena för IP-adressen och resurssökvägen. I det här exemplet är IP-adressen `10.50.25.21` och resurssökvägen är `/ipp/port1`.

## <a name="login-items"></a>Inloggningsobjekt

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: Alla registreringstyper

- **Filer, mappar och anpassade appar**: **Lägg till** sökvägen för en fil, mapp, anpassad app eller systemapp som du vill ska öppnas när en användare loggar in på enheten. Systemappar eller appar som har skapats eller anpassats för din organisation finns vanligtvis i `Applications`-mappen, med en sökväg liknande `/Applications/AppName.app`. 

  Du kan lägga till många filer, mappar och appar. Ange till exempel:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  När du lägger till en app, mapp eller fil måste du ange rätt sökväg. Alla objekt finns inte i `Applications`-mappen. Om en användare flyttar ett objekt från en plats till en annan ändras sökvägen. Det här flyttade objektet öppnas inte när användaren loggar in.

## <a name="login-window"></a>Inloggningsfönstret

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: Enhetsregistrering och automatisk enhetsregistrering

#### <a name="window-layout"></a>Fönsterlayout

- **Visa ytterligare information i menyfältet**: När du väljer tidsområdet på menyraden visas värdnamnet och macOS-versionen om **Tillåt** är valt. **Inte konfigurerad** (standard) innebär att den här informationen inte visas på menyraden.
- **Banderoll**: Ange ett meddelande som visas på inloggningsskärmen på enheten. Du kan till exempel ange organisationsinformation, ett välkomstmeddelande eller information för Upphittat.
- **Välj inloggningsformat**: Välj hur användare loggar in på enheten. Alternativen är:
  - **Fråga efter användarnamn och lösenord** (standard): Kräver att användarna anger ett användarnamn och lösenord.
  - **Lista alla användare, fråga efter lösenord**: Kräver att användarna väljer sitt användarnamn från en användarlista och sedan anger sitt lösenord. Konfigurera också:

    - **Lokala användare**: Om du väljer **Dölj** visas inte lokala användarkonton i användarlistan, som kan innehålla standardkonton och administratörskonton. Endast nätverks- och systemanvändarkonton visas. **Inte konfigurerad** (standard) visar de lokala användarkontona i användarlistan.
    - **Mobilkonton**: Om du väljer **Dölj** visas inte mobilkonton i användarlistan. **Inte konfigurerad** (standard) visar mobilkontona i användarlistan. Vissa mobilkonton kan visas som nätverksanvändare.
    - **Nätverksanvändare**: Välj **Visa** om du vill visa nätverksanvändare i användarlistan. **Inte konfigurerad** (standard) visar nätverksanvändarkontona i användarlistan.
    - **Administratörer**: Om du väljer **Dölj** visas inte administratörskonton i användarlistan. **Inte konfigurerad** (standard) visar administratörskontona i användarlistan.
    - **Andra användare**: Välj **Visa** om du vill visa **Andra...** användare i användarlistan. **Inte konfigurerad** (standard) visar konton för andra användare i användarlistan.

#### <a name="login-screen-power-settings"></a>Strömsparinställningar på inloggningsskärmen

- **Stäng av**: Om du väljer **Dölj** visas inte avstängningsknappen på inloggningsskärmen. **Inte konfigurerad** (standard) visar avstängningsknappen.
- **Starta om**: Om du väljer **Dölj** visas inte omstartsknappen på inloggningsskärmen. **Inte konfigurerad** (standard) visar omstartsknappen.
- **Vila**: Om du väljer **Dölj** visas inte Vila-knappen på inloggningsskärmen. **Inte konfigurerad** (standard) visar Vila-knappen.

#### <a name="other"></a>Andra

- **Inaktivera användarinloggning från konsol**: Om du väljer **Inaktivera** döljs macOS-kommandoraden som används för att logga in. Vanliga användare kan **inaktivera** den här inställningen. **Inte konfigurerad** (standard) gör att avancerade användare kan logga in med macOS-kommandoraden. För att gå till konsolläget anger användarna `>console` i fältet Användarnamn. Användarna måste sedan autentiseras i konsolfönstret.

#### <a name="apple-menu"></a>Apple-menyn

När användarna loggar in på enheterna påverkar följande inställningar vad de kan göra.

- **Inaktivera Stäng av**: Om du väljer **Inaktivera** kan användarna inte använda alternativet **Stäng av** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Stäng av** på enheten.
- **Inaktivera omstart** : Om du väljer **Inaktivera** kan användarna inte välja alternativet **Starta om** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Starta om** på enheten.
- **Inaktivera Ström av**: Om du väljer **Inaktivera** kan användarna inte välja alternativet **Ström av** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Ström av** på enheten.
- **Inaktivera Logga ut** (macOS 10.13 och senare): Om du väljer **Inaktivera** kan användarna inte välja alternativet **Logga ut** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Logga ut** på enheten.
- **Inaktivera Lås skärm** (macOS 10.13 och senare): Om du väljer **Inaktivera** kan användarna inte välja alternativet **Lås skärm** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Lås skärm** på enheten.

## <a name="single-sign-on-app-extension"></a>Tillägg för enkel inloggning

Den här funktionen gäller för:

- macOS 10.15 och senare

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: Alla registreringstyper 

- **Typ av SSO-apptillägg**: Välj typ av autentiseringsuppgifter för SSO-apptillägget. Alternativen är:

  - **Inte konfigurerad**: apptilläggen används inte. Om du vill inaktivera ett apptillägg, så ändra SSO-apptilläggstypen till **Inte konfigurerad**.
  - **Omdirigera**: Använd ett allmänt, anpassningsbart omdirigeringsapptillägg om du vill utföra SSO med moderna autentiseringsflöden. Försäkra dig om att du känner till tillägget och grupp-ID:t för din organisations apptillägg.
  - **Autentiseringsuppgift**: Använd ett generiskt, anpassningsbart apptillägg för autentiseringsuppgifter om du vill utföra SSO med autentiserings flöden med anrop och svar. Försäkra dig om att du känner till tilläggs-ID och grupp-ID för din organisations SSO-apptillägg.  
  - **Kerberos**: Använd Apples inbyggda Kerberos-tillägg, som ingår i macOS Catalina 10.15 och senare. Det här alternativet är en Kerberos-specifik version av apptillägget **Autentiseringsuppgifter**.

  > [!TIP]
  > Gå igenom tillägget genom att lägga till dina egna konfigurationsvärden med hjälp av typerna **Omdirigering** och **Autentiseringsuppgifter**. Om du använder **autentiseringsuppgifter**bör du överväga att använda inbyggda konfigurationsinställningar från Apple i **Kerberos**-typen.

- **Tilläggs-ID** (omdirigering och autentiseringsuppgifter): Ange det paket-ID som identifierar ditt SSO apptillägg, exempelvis `com.apple.ssoexample`.
- **Team-ID** (omdirigering och autentiseringsuppgifter): Ange SSO-apptilläggets team-ID. Ett team-ID är en sträng med 10 tecken (siffror och bokstäver) som genereras av Apple, t. ex. `ABCDE12345`. 

  [Leta upp ditt team-ID](https://help.apple.com/developer-account/#/dev55c3c710c) (öppna Apples webbplats) om du vill ha mer information.

- **Sfär** (autentiseringsuppgifter och Kerberos): Ange din autentiseringssfärs namn. Sfärnamnet måste skrivas med versaler, t. ex. `CONTOSO.COM`. Vanligtvis är sfärnamnet detsamma som ditt DNS-domännamn, men skrivet enbart med versaler.

- **Domäner** (autentiseringsuppgifter och Kerberos): ange domän- eller värdnamnen för de platser som kan autentiseras via SSO. Om din webbplats exempelvis är `mysite.contoso.com`, så är `mysite` värdnamnet och `contoso.com` domännamnet. När användarna ansluter till någon av dessa platser så hanterar apptillägget autentiseringsutmaningen. Med den här autentiseringen kan användarna logga in med hjälp av Ansiktsigenkänning-ID, Touch ID eller PIN-kod/lösenord för Apple.

  - Alla domäner i Intune-profiltilläggen för enkel inloggning måste vara unika. Du kan inte upprepa en domän i vilken apptilläggsprofil för enkel inloggning som helst, även om du använder olika typer av SSO-apptillägg.
  - Dessa domäner är inte skiftlägeskänsliga.

- **URL:er** (endast omdirigering): Ange URL-prefixen för dina identitetsleverantörer, å vilkas vägnar omdirigeringstillägget utför SSO. När en användare omdirigeras till dessa URL:er ingriper SSO-apptillägget att och framtvingar SSO.

  - Alla URL:er i Intune-apptilläggsprofilerna för enkel inloggning måste vara unika. Du kan inte upprepa en domän i vilken SSO-apptilläggsprofil som helst, även om du använder olika typer av SSO-tillägg.
  - URL:erna måste inledas med http://eller https://.

- **Ytterligare konfiguration** (omdirigering och autentiseringsuppgifter): Ange ytterligare tilläggsspecifika data som ska skickas till SSO-apptillägget:
  - **Nyckel**: Ange namnet på det objekt som du vill lägga till, t. ex. `user name`.
  - **Typ**: Ange datatyp. Alternativen är:

    - Sträng
    - Boolean: Ange `True` eller `False` i **Konfigurationsvärde**.
    - Heltal: Ange ett tal i **Konfigurationsvärde**.
    
  - **Värde**: Ange data.
  
  - **Lägg till**: Välj om du vill lägga till dina konfigurationsnycklar.

- **Använda nyckelringar** (endast Kerberos): Förhindra att lösenord sparas och lagras i nyckelringen genom att välja **Blockera**. **Inte konfigurerad** (standard) tillåter att lösenord sparas och lagras i nyckelringen.  
- **Ansiktsigenkänning-ID, Touch-ID eller lösenord** (endast Kerberos): Med **Kräv** måste användarna ange sitt Face ID, Touch ID eller Apple-lösenord för att kunna logga in på de domäner som du har lagt till. **Inte konfigurerad** (standard) kräver inte att användare använder biometrik eller lösenord för att logga in.
- **Standarddomän** (endast Kerberos): Välj **Aktivera** om du vill ange det **Sfär**-värde som du angav som standardsfär. **Inte konfigurerad** (standard) anger inte någon standardsfär.

  > [!TIP]
  > - **Aktivera** den här inställningen om du konfigurerar flera Kerberos SSO-ap-tillägg i din organisation.
  > - **Aktivera** den här inställningen om du använder flera sfärer. Den anger det **Sfär**-värde som du angav som standardsfär.
  > - Om du bara har en sfär så låt inställningen vara **Inte konfigurerad** (standard).

- **Identifiera automatiskt** (endast Kerberos): När värdet ställts in på **Blockera** så använder Kerberos-tillägget inte LDAP eller DNS automatiskt för att fastställa Active Directory-platsens namn. **Inte konfigurerad** (standard) tillåter att tillägget automatiskt hittar Active Directory-platsens namn.
- **Ändringar av lösenord** (endast Kerberos): **Blockera** förhindrar att användana ändrar de lösenord som de använder för att logga in på de domäner som du har angett. **Inte konfigurerad** (standard) tillåter att lösenord ändras.  
- **Lösenordssynkronisering** (endast Kerberos): Välj **Aktivera** om du vill synkronisera dina användares lokala lösenord med Azure AD. **Inte konfigurerad** (standard) inaktiverar synkronisering av lösenord med Azure AD. Använd den här inställningen som alternativ till eller säkerhetskopia för SSO. Den här inställningen fungerar inte om användarna är inloggade med ett Apple-mobilkonto.
- **Windows Server Active Directory-lösenordskomplexitet** (endast Kerberos): Välj **Kräv** om du vill framtvinga att användarlösenorden uppfyller kraven på Active Directory-lösenordkomplexitet. Mer information finns i [Lösenord måste uppfylla komplexitetskraven](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) . **Inte konfigurerad** (standard) kräver inte att användarna uppfyller Active Directory-lösenordskraven.
- **Minsta lösenordslängd**: Ange det minsta antal tecken som användarens lösenord måste innehålla. **Inte konfigurerad** (standard) framtvingar inte någon minsta längd för användarens lösenord.
- **Gräns för återanvändning av lösenord** (endast Kerberos): Ange det antal nya lösenord, från 1 till 24, som måste användas innan ett tidigare lösenord kan återanvändas på domänen. **Inte konfigurerad** (standard) framtivingar inte någon gräns för återanvändning av lösenord.
- **Lägsta ålder för lösenord** (endast Kerberos): Ange det antal dagar som ett lösenord måste användas på domänen innan användaren kan ändra det. **Inte konfigurerad** (standard) framtvingar inte någon lägsta ålder på lösenord innan de kan ändras.
- **Meddelande om förfallodatum för lösenord** (endast Kerberos): Ange hur många dagar innan ett lösenord upphör att gälla som användaren får ett meddelande om detta. **Inte konfigurerad** (standard) använder `15` dagar.
- **Lösenordets giltighetstid** (endast Kerberos): Ange antalet dagar innan lösenordet måste ändras. **Inte konfigurerat** (standard) innebär att användarlösenorden aldrig upphör att gälla.
- **URL för ändring av lösenord** (endast Kerberos): Ange den URL som startar när användaren initierar en ändring av Kerberos-lösenordet.
- **Huvudkontonamn** (endast Kerberos): Ange användarnamnet för Kerberos-huvudkontot. Du behöver inte inkludera sfärnamnet. I `user@contoso.com` är t.ex. `user` huvudkontots namn och `contoso.com` är sfärens namn.

  > [!TIP]
  > - Du kan också använda variabler i huvudkontots namn genom inom klammerparenteser `{{ }}`. Om du t.ex. vill visa användarnamnet anger du `Username: {{username}}`. 
  > - Var dock försiktig med variabel ersättning eftersom variablerna inte verifieras i användargränssnittet och är skiftlägeskänsliga. Se till att du anger rätt information.
  
- **Active Directory-platskod** (endast Kerberos): Ange namnet på den Active Directory-plats som Kerberos-tillägget ska använda. Du kanske inte behöver ändra det här värdet eftersom Kerberos-tillägget kan hitta Active Directory-platskoden automatiskt.
- **Cachenamn** (endast Kerberos): Ange GSS-namnet (Generic Security Services) för Kerberos-cachen. Du behöver förmodligen inte ange det här värdet.  
- **Meddelande om lösenordskrav** (endast Kerberos): Ange en textversion av organisationens lösenordskrav som ska visas för användarna. Meddelandet visas om du inte har några krav på Active Directory-lösenordskomplexitet eller på minsta längd för lösenord.  
- **Programpakets-ID:n** (endast Kerberos): **Lägg till** de appsamlings-ID:n som ska använda enkel inloggning på dina enheter. De här apparna beviljas åtkomst till en Kerberos Ticket Granting-biljett, autentiseringsbiljetten och autentiserar användarna till de tjänster för vilka de har åtkomstbehörighet.
- **Domänsfärsmappning** (endast Kerberos): **Lägg till** DNS-suffixet för den domän som ska mappas till din sfär. Använd den här inställningen när värdarnas DNS-namn inte matchar sfärnamnet. Du behöver förmodligen inte skapa den här anpassade domän-till-sfär-mappningen.
- **PKINIT-certifikat** (endast Kerberos): **Välj** den kryptering för offentlig nyckel för inledande autentisering (PKINIT) som kan användas för Kerberos-autentisering. Du kan välja mellan [PKCS](../protect/certficates-pfx-configure.md)- eller [SCEP](../protect/certificates-scep-configure.md) -certifikat som du har lagt till i Intune. Mer information om certifikat finns i [Använda certifikat för autentisering i Microsoft Intune](../protect/certificates-configure.md).

## <a name="associated-domains"></a>Tillhörande domäner

Med Intune kan du:

- Lägg till många app-till-domän-associationer.
- Associera många domäner med samma app.

Den här funktionen gäller för:

- macOS 10.15 och senare

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: Alla registreringstyper

- **App-ID**: Ange app-ID:t för den app som ska associeras med en webbplats. App-ID:t innehåller team-ID:t och ett bunt-ID: `TeamID.BundleID`.

  Team-ID:t är en sträng med 10 tecken (bokstäver och siffror) som genereras av Apple för dina apputvecklare, t.ex. `ABCDE12345`. [Leta upp ditt team-ID](https://help.apple.com/developer-account/#/dev55c3c710c) (öppnar Apples webbplats) innehåller mer information.

  Bunt-ID:t identifierar appen unikt och är vanligtvis formaterat i omvänd domännamnsnotation. Bunt-ID:t för Finder är t.ex. `com.apple.finder`. Om du vill hitta bunt-ID:t, så använd AppleScript i Terminal:

  `osascript -e 'id of app "ExampleApp"'`

- **Domän**: Ange den webbplatsdomän som ska associeras med en app. Domänen innehåller en tjänsttyp och ett fullständigt kvalificerat värdnamn, t. ex. `webcredentials:www.contoso.com`.

  Du kan matcha alla underdomäner i en associerad domän genom att ange `*.` (en asterisk som jokertecken och en punkt) framför domänens början. Du måste ange perioden. Exakta domäner har högre prioritet än domäner med jokertecken. Därför matchas mönster från överordnade domäner *om* någon matchning inte finns i den fullständigt kvalificerade underdomänen.

  Tjänsttypen kan vara:

  - **authsrv**: Tillägg för enkel inloggning
  - **applink**: Universell länk
  - **webcredentials**: Autofyll av lösenord

- **Lägg till**: Välj om du vill lägga till dina appar och associerade domäner.

> [!TIP]
> Du kan felsöka på din macOS-enhet genom att öppna **Systeminställningar** > **Profiler**. Bekräfta att profilen du skapade finns i enhetens profillista. Om den finns med i listan, såse till att **Associerad domänkonfiguration** finns i profilen och att den innehåller rätt app-ID och domäner.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också konfigurera enhetsfunktioner på [iOS/iPadOS](ios-device-features-settings.md).
