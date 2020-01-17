---
title: Funktionsinställningar för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se inställningarna för att konfigurera macOS-enheter för AirPrint och anpassa inloggningsfönstret för att visa eller dölja strömknappar i Microsoft Intune. Se även anvisningar för att hämta IP-adress, sökväg och portinställningar för en AirPrint-server i nätverket. Använd dessa inställningar i en enhetskonfigurationsprofil när du konfigurerar funktioner för macOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
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
ms.openlocfilehash: 791e2a1313480bdf1ad95988d48664d6620ba0b3
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206354"
---
# <a name="macos-device-feature-settings-in-intune"></a>Funktionsinställningar för macOS-enheter i Intune

I Intune finns vissa inbyggda inställningar för att anpassa funktioner i dina macOS-enheter. Administratörer kan till exempel lägga till skrivare för utskrift, välja hur användare loggar in, konfigurera energi kontrollerna, använda autentisering med enkel inloggning och mycket mer.

Du kan använda dessa funktioner för att styra macOS-enheter som en del av din MDM-lösning för hantering av mobilenheter.

I den här artikeln visas inställningarna, tillsammans med en beskrivning av vad varje inställning gör. Här visas även anvisningar för att hämta IP-adress, sökväg och port för AirPrint-skrivare som använder Terminal-appen (emulator). Mer information om enhets funktioner finns i [lägga till iOS-eller MacOS-enhetens funktions inställningar](device-features-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en macOS-enhetskonfigurationsprofil](device-features-configure.md).

> [!NOTE]
> Dessa inställningar gäller för olika registrerings typer, med vissa inställningar som gäller för alla registrerings alternativ. Mer information om de olika registrerings typerna finns i [MacOS-registrering](../enrollment/macos-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: enhets registrering och automatisk enhets registrering 

- **IP-adress**: Ange skrivarens IPv4- eller IPv6-adress. Om du använder värdnamn till att identifiera skrivare, kan du hämta IP-adressen genom att pinga skrivaren i Terminal-appen. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
- **Sökväg**: Ange sökvägen till skrivaren. Sökvägen är vanligtvis `ipp/print` för skrivare i nätverket. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
- **Port** (iOS 11.0 och senare): Ange lyssningsporten för AirPrint-målet. Om du lämnar den här egenskapen tom, kommer AirPrint att använda standardporten.
- **TLS** (iOS 11.0 och senare): Välj **Aktivera** för att skydda AirPrint-anslutningar med TLS (Transport Layer Security).

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

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **Filer, mappar och anpassade appar**: **Lägg till** sökvägen till en fil, mapp, anpassad app eller systemappen som du vill öppna när en användare loggar in på enheten. Systemappar eller appar som har skapats eller anpassats för din organisation är vanligt vis i `Applications` mapp, med en sökväg som liknar `/Applications/AppName.app`. 

  Du kan lägga till många filer, mappar och appar. Ange till exempel:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  När du lägger till en app, mapp eller fil måste du ange rätt sökväg. Alla objekt finns inte i `Applications`-mappen. Om en användare flyttar ett objekt från en plats till en annan ändras sökvägen. Det här flyttade objektet öppnas inte när användaren loggar in.

## <a name="login-window"></a>Inloggningsfönstret

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: enhets registrering och automatisk enhets registrering

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

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer 

- **Typ av SSO-app-tillägg**: Välj typ av AUTENTISERINGSUPPGIFTER för SSO-appen. Alternativen är:

  - **Inte konfigurerad**: app-tillägg används inte. Om du vill inaktivera ett app-tillägg byter du typ av SSO-appaket till **inte konfigurerad**.
  - **Omdirigera**: Använd ett allmänt, anpassningsbart omdirigerings-app-tillägg för att utföra SSO med moderna autentiserings flöden. Se till att du känner till tillägget och Team-ID: t för din organisations app-tillägg.
  - **Autentiseringsuppgift**: Använd ett generiskt, anpassningsbart program tillägg för autentiseringsuppgifter för att utföra SSO med autentiserings flöden med anrop och svar. Se till att du känner till tilläggs-ID: t och Team-ID: t för din organisations SSO app-tillägg.  
  - **Kerberos**: Använd Apples inbyggda Kerberos-tillägg, som ingår i macOS Catalina 10,15 och senare. Det här alternativet är en Kerberos-speciell version av appen för **autentiseringsuppgifter** .

  > [!TIP]
  > Med hjälp av typerna **omdirigering** och **autentiseringsuppgifter** lägger du till dina egna konfigurations värden för att gå igenom tillägget. Om du använder **autentiseringsuppgifter**bör du överväga att använda inbyggda konfigurations inställningar från Apple i **Kerberos** -typen.

- **Tilläggs-ID** (omdirigering och autentiseringsuppgift): Ange det paket-ID som identifierar ditt SSO app-tillägg, till exempel `com.apple.ssoexample`.
- **Team-ID** (omdirigering och autentiseringsuppgift): Ange Team-ID för SSO-appens tillägg. Ett team-ID är en sträng med 10 tecken (siffror och bokstäver) som genereras av Apple, t. ex. `ABCDE12345`. 

  [Leta upp ditt team-ID](https://help.apple.com/developer-account/#/dev55c3c710c) (öppna Apples webbplats) om du vill ha mer information.

- **Sfär** (autentiseringsuppgift och Kerberos): Ange namnet på din autentiserings-sfär. Sfär namnet ska vara kapitaliserat, t. ex. `CONTOSO.COM`. Vanligt vis är ditt sfär namn detsamma som ditt DNS-domännamn, men i alla versaler.

- **Domäner** (autentiseringsuppgift och Kerberos): ange domän-eller värd namnen för de platser som kan AUTENTISERA via SSO. Om din webbplats till exempel är `mysite.contoso.com`, `mysite` är värd namnet och `contoso.com` är domän namnet. När användarna ansluter till någon av dessa platser hanterar app-tillägget verifierings utmaningen. Med den här autentiseringen kan användare använda ansikts-ID, Touch-ID eller Apple-Pincode/lösen ord för att logga in.

  - Alla domäner i Intune-tilläggen för enkel inloggning måste vara unika. Du kan inte upprepa en domän i valfri inloggnings profil för program tillägg, även om du använder olika typer av SSO-tillägg.
  - Dessa domäner är inte Skift läges känsliga.

- **URL: er** (endast omdirigering): Ange URL-prefixen för dina identitets leverantörer i vars ställe som omdirigerings-tillägget utför SSO. När en användare omdirigeras till dessa URL: er kommer SSO app Extension att ingripa och uppmana SSO.

  - Alla webb adresser i Intune-tilläggen för enkel inloggning i Intune måste vara unika. Du kan inte upprepa en domän i valfri SSO-profil, även om du använder olika typer av SSO-tillägg.
  - URL: erna måste börja med http://eller https://.

- **Ytterligare konfiguration** (omdirigering och autentiseringsuppgift): ange ytterligare tilläggs information som ska skickas till SSO-appens tillägg:
  - **Nyckel**: Ange namnet på det objekt som du vill lägga till, t. ex. `user name`.
  - **Typ**: ange typ av data. Alternativen är:

    - Sträng
    - Boolean: Ange `True` eller `False`i **konfiguration svärdet**.
    - Heltal: Ange ett tal i **konfiguration svärdet**.
    
  - **Värde**: ange data.
  
  - **Lägg till**: Välj om du vill lägga till dina konfigurations nycklar.

- **Användning av nyckel ringar** (endast Kerberos): Välj **blockera** för att förhindra att lösen ord sparas och lagras i nyckel ringen. **Inte konfigurerad** (standard) tillåter att lösen ord sparas och lagras i nyckel ringen.  
- **Ansikts-ID, Touch-ID eller lösen ord** (endast Kerberos): **Kräv** att användarna anger sitt ansikts-ID, Touch ID eller Apple-lösenord för att logga in på de domäner som du har lagt till. **Inte konfigurerad** (standard) kräver inte att användare använder biometrik eller lösen ord för att logga in.
- **Standard domän** (endast Kerberos): Välj **Aktivera** för att ange det **sfär** värde som du angav som standard sfär. **Inte konfigurerad** (standard) anger inte en standard sfär.

  > [!TIP]
  > - **Aktivera** den här inställningen om du konfigurerar flera Kerberos SSO app-tillägg i din organisation.
  > - **Aktivera** den här inställningen om du använder flera sfärer. Den anger det **sfär** värde som du angav som standard sfär.
  > - Lämna det **inte konfigurerat** (standard) om du bara har en sfär.

- **Identifiera** automatiskt (endast Kerberos): när värdet är **blockerat**använder KERBEROS-tillägget inte LDAP och DNS för att fastställa Active Directory plats namn. **Inte konfigurerad** (standard) tillåter att tillägget automatiskt hittar Active Directoryens plats namn.
- **Lösen ords ändringar** (endast Kerberos): **blockera** förhindrar att användare ändrar lösen ord som de använder för att logga in på de domäner som du har angett. **Inte konfigurerad** (standard) tillåter lösen ords ändringar.  
- **Lösenordssynkronisering** (endast Kerberos): Välj **Aktivera** för att synkronisera dina användares lokala lösen ord till Azure AD. **Inte konfigurerad** (standard) inaktiverar synkronisering av lösen ord till Azure AD. Använd den här inställningen som ett alternativ eller en säkerhets kopia till SSO. Den här inställningen fungerar inte om användarna är inloggade med ett Apple Mobile-konto.
- **Windows Server Active Directory lösen ords komplexitet** (endast Kerberos): Välj **Kräv** för att tvinga användar lösen ord att uppfylla Active Directory lösen ords komplexitets krav. Mer information finns i [lösen ordet måste uppfylla komplexitets kraven](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) . **Inte konfigurerad** (standard) kräver inte att användare uppfyller Active Directory lösen ords krav.
- **Minsta längd på lösen ord** (endast Kerberos): Ange det minsta antalet tecken som kan vara en användares lösen ord. **Inte konfigurerad** (standard) framtvingar inte användarens minsta längd på lösen ord.
- **Återanvändnings gräns för lösen ord** (endast Kerberos): Ange antalet nya lösen ord, från 1-24, som måste användas tills ett tidigare lösen ord kan återanvändas på domänen. **Inte konfigurerad** (standard) upprätthåller inte en gräns för lösen ords åter användning.
- **Lägsta ålder för lösen ord** (endast Kerberos): Ange antalet dagar som ett lösen ord måste användas på domänen innan användaren kan ändra det. **Inte konfigurerad** (standard) upprätthåller inte en minsta ålder på lösen ord innan de kan ändras.
- **Meddelande om förfallo datum för lösen ord** (endast Kerberos): Ange antalet dagar innan ett lösen ord upphör att gälla som användare får ett meddelande om att lösen ordet upphör att gälla. **Inte konfigurerad** (standard) använder `15` dagar.
- **Lösenordets giltighetstid** (endast Kerberos): Ange antalet dagar innan lösenordet måste ändras. **Inte konfigurerat** (standard) innebär att användar lösen ord aldrig upphör att gälla.
- **URL för lösen ords ändring** (endast Kerberos): Ange URL: en som startar när användaren initierar en ändring av Kerberos-lösenordet.
- **Huvud namn** (endast Kerberos): Ange användar namnet för Kerberos-huvudobjektet. Du behöver inte inkludera sfär namnet. I `user@contoso.com`är `user` till exempel huvud namnet och `contoso.com` är sfär namnet.

  > [!TIP]
  > - Du kan också använda variabler i huvud namnet genom att ange klammerparenteser `{{ }}`. Om du till exempel vill visa användar namnet anger du `Username: {{username}}`. 
  > - Var dock försiktig med variabel ersättning eftersom variablerna inte verifieras i användar gränssnittet och är Skift läges känsliga. Se till att ange rätt information.
  
- **Active Directory platskod** (endast Kerberos): Ange namnet på den Active Directory plats som Kerberos-tillägget ska använda. Du kanske inte behöver ändra det här värdet eftersom Kerberos-tillägget automatiskt kan hitta Active Directory platskod.
- **Cache-namn** (endast Kerberos): Ange GSS-namnet (Generic Security Services) för Kerberos-cachen. Du behöver förmodligen inte ange det här värdet.  
- **Meddelande krav för lösen ord** (endast Kerberos): Ange en text version av organisationens lösen ords krav som visas för användarna. Meddelandet visas om du inte behöver Active Directory krav på lösen ords komplexitet eller inte anger en minsta längd på lösen ord.  
- **Programpaket-ID: n** (endast Kerberos): **Lägg till** de ID: n för appen som ska använda enkel inloggning på dina enheter. De här apparna beviljas åtkomst till biljett beviljande biljetten i Kerberos, autentiserings biljetten och autentisera användare till tjänster som de har behörighet att komma åt.
- **Domän sfär mappning** (endast Kerberos): **Lägg till** DNS-suffixet för domänen som ska mappas till din sfär. Använd den här inställningen när DNS-namnen på värdarna inte matchar sfär namnet. Du behöver förmodligen inte skapa den här anpassade domän-till-sfär-mappningen.
- **PKINIT-certifikat** (endast Kerberos): **Välj** kryptering för offentlig nyckel för inledande autentisering (PKINIT) som kan användas för Kerberos-autentisering. Du kan välja mellan [PKCS](../protect/certficates-pfx-configure.md) -eller [SCEP](../protect/certificates-scep-configure.md) -certifikat som du har lagt till i Intune. Mer information om certifikat finns [i använda certifikat för autentisering i Microsoft Intune](../protect/certificates-configure.md).

## <a name="associated-domains"></a>Tillhörande domäner

Med Intune kan du:

- Lägg till många app-to-Domain-associationer.
- Associera många domäner med samma app.

Den här funktionen gäller för:

- macOS 10.15 och senare

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **App-ID**: Ange appens ID för den app som ska associeras med en webbplats. App-ID: t innehåller Team-ID: t och ett paket-ID: `TeamID.BundleID`.

  Team-ID: t är en sträng med 10 tecken (bokstäver och siffror) som genereras av Apple för dina Apps-utvecklare, till exempel `ABCDE12345`. [Leta upp ditt team-ID](https://help.apple.com/developer-account/#/dev55c3c710c) (öppna Apples webbplats) innehåller mer information.

  Bunt-ID: t identifierar appen unikt och är vanligt vis formaterad i omvänd domän namns notation. Till exempel är paket-ID: t för Finder `com.apple.finder`. Om du vill hitta paket-ID: t använder du Apple script i Terminal:

  `osascript -e 'id of app "ExampleApp"'`

- **Domän**: Ange den webbplats domän som ska associeras med en app. Domänen innehåller en tjänst typ och ett fullständigt kvalificerat värdnamn, t. ex. `webcredentials:www.contoso.com`.

  Du kan matcha alla under domäner i en associerad domän genom att ange `*.` (en asterisk med jokertecken och en punkt) innan domänen börjar. Perioden måste anges. Exakta domäner har högre prioritet än domäner med jokertecken. Därför matchas mönster från överordnade domäner *om* en matchning inte finns i den fullständigt kvalificerade under domänen.

  Tjänst typen kan vara:

  - **authsrv**: Tillägg för enkel inloggning
  - **AppLink**: Universal Link
  - **webcredentials**: lösen ord Autofyll

- **Lägg till**: Välj om du vill lägga till dina appar och associerade domäner.

> [!TIP]
> Du kan felsöka på din macOS-enhet genom att öppna **system inställningar** > **profiler**. Bekräfta att profilen du skapade är i listan enhets profiler. Om den finns med i listan, se till att **konfigurationen för tillhör ande domäner** finns i profilen och att den innehåller rätt app-ID och domäner.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också konfigurera enhets funktioner på [iOS](ios-device-features-settings.md).
