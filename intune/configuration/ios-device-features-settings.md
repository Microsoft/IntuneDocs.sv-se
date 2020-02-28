---
title: Funktionsinställningar för iOS/iPadOS i Microsoft Intune – Azure | Microsoft Docs
description: Se alla inställningar för att konfigurera iOS- och iPadOS-enheter för AirPrint, layout för startsidan, appmeddelanden, delad enhet, enkel inloggning och webbinnehållsfilter i Microsoft Intune.Se alla inställningar för att konfigurera iOS-enheter för AirPrint, layout för startsidan, appmeddelanden, delad enhet, enkel inloggning och webbinnehållsfilter i Microsoft Intune. Använd dessa inställningar i en enhetskonfigurationsprofil när du konfigurerar iOS- och iPadOS-enheter för att använda Apple-funktionerna i din organisation.
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
ms.openlocfilehash: 7f19ccfb6949dbfa0de62a8b711436ab9cde8c9c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512950"
---
# <a name="ios-and-ipados-device-settings-to-use-common-iosipados-features-in-intune"></a>iOS- och iPadOS-enhetsinställningar som används; vanliga iOS- och iPadOS-funktioner i Intune

Intune innehåller vissa inbyggda inställningar för att tillåta iOS- och iPadOS-användare att använda olika Apple-funktioner på sina enheter. Till exempel så kan administratörer styra hur iOS- och iPadOS-användare använder AirPrint-skrivare, lägga till appar och mappar till dockan och sidor på startskärmen, visa meddelanden i appen, visa information om tillgångstagg på låsskärmen, använda enkel inloggning och autentisera användare med certifikat.

Du kan använda dessa funktioner för att styra iOS- och iPadOS-enheter som en del av din MDM-lösning för hantering av mobilenheter.

I den här artikeln visas inställningarna, tillsammans med en beskrivning av vad varje inställning gör. Om du vill ha mer information om dessa funktioner går du till [lägga till iOS/iPadOS- eller MacOS-enhetens funktionsinställningar](../device-features-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en iOS- och iPadOS-enhetskonfigurationsprofil](../device-features-configure.md).

> [!NOTE]
> Dessa inställningar gäller för olika registreringstyper. Vissa inställningar gäller för alla registreringsalternativ. Mer information om de olika registreringstyperna finns i [iOS/iPadOS-registrering](../ios-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: Alla registreringstyper

> [!NOTE]
> Se till att lägga till alla skrivare i samma profil. Apple förhindrar att flera skrivare skriver ut på samma enhet.

- **IP-adress**: Ange skrivarens IPv4- eller IPv6-adress. Om du använder värdnamn till att identifiera skrivare, kan du hämta IP-adressen genom att pinga skrivaren i terminalen. Det finns mer information i Hämta IP-adress och sökväg (i den här artikeln).
- **Sökväg**: Sökvägen är vanligtvis `ipp/print` för skrivare i nätverket. Det finns mer information i Hämta IP-adress och sökväg (i den här artikeln).
- **Port**: Ange lyssningsporten för AirPrint-målet. Om du lämnar den här egenskapen tom, kommer AirPrint att använda standardporten. Tillgängligt i iOS 11.0 och iPadOS 13.0 och senare.
- **TLS**: Välj **Aktivera** för att skydda AirPrint-anslutningar med TLS (Transport Layer Security). Tillgängligt i iOS 11.0 och iPadOS 13.0 och senare.

Om du vill lägga till AirPrint-servrar kan du:

- **Lägg till** lägger till AirPrint-servern i listan. Det går att lägga till många olika AirPrint-servrar.
- **Importera** en kommaavgränsad fil (CSV) med den här informationen. Eller **Exportera** för att skapa en lista med de skrivarservrar som du har lagt till.

### <a name="get-server-ip-address-resource-path-and-port"></a>Hämta IP-adress för server, resurssökväg och port

Om du vill lägga till AirPrinter-servrar, behöver du ha skrivarens IP-adress, resurssökväg och port. Följande steg visar hur du hämtar den här informationen.

1. Öppna **Terminal** (från **/Program/Verktyg**) på en Mac som är ansluten till samma lokala nätverk (undernät) som AirPrint-skrivarna.
2. I Terminal skriver du `ippfind` och väljer Retur.

    Observera skrivarinformationen. Du kan exempelvis ange något i stil med `ipp://myprinter.local.:631/ipp/port1`. Den första delen är namnet på skrivaren. Den sista delen (`ipp/port1`) är resurssökvägen.

3. I Terminal skriver du `ping myprinter.local` och väljer Retur.

   Observera IP-adressen. Den visar något i stil med `PING myprinter.local (10.50.25.21)`.

4. Använd värdena för IP-adressen och resurssökvägen. I det här exemplet är IP-adressen `10.50.25.21` och resurssökvägen är `/ipp/port1`.

## <a name="home-screen-layout"></a>Startsideslayout

Den här funktionen gäller för:

- iOS 9.3 eller senare
- iPadOS 13.0 och senare

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: Automatisk enhetsregistrering (övervakad)

### <a name="dock"></a>Docka

Använd inställningarna **Docka** för att lägga till upp till sex objekt eller mappar till dockan på iOS-/iPadOS-skärmen. Många enheter stöder färre objekt. Till exempel stöder iPhone-enheter upp till fyra objekt. I det här fallet visas endast de första fyra objekt som du har lagt till på enheten.

Du kan lägga till upp till **sex** objekt (appar och mappar som kombineras) för enhetens docka.

- **Lägg till**: Lägger till appar eller mappar till dockan på enheten.
- **Typ**: Lägger till en **app** eller en **mapp**:

  - **App**: Välj det här alternativet för att lägga till appar i dockan på skärmen. Ange:

    - **Appnamn**: Ange ett namn för appen. Det här namnet används för din referens i administrationscentret för Microsoft Endpoint Manager. Det visas *inte* på iOS-/iPadOS-enheten.
    - **Appsamlings-ID**: Ange appens samlings-ID. Se [Samlings-ID för inbyggda iOS-/iPadOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

  - **Mapp**: Välj det här alternativet för att lägga till en mapp i dockan på skärmen.

    Apparna som du lägger till på en sida i en mapp ordnas från vänster till höger, och i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

    - **Mappnamn**: Ange namnet på mappen. Namnet visas för användare på deras enhet.
    - **Lista över sidor**: **Lägg till** en sida och ange följande egenskaper:

      - **Sidnamn**: Ange ett namn för sidan. Det här namnet används för din referens i administrationscentret för Microsoft Endpoint Manager. Det visas *inte* på iOS-/iPadOS-enheten.
      - **Appnamn**: Ange ett namn för appen. Det här namnet används för din referens i administrationscentret för Microsoft Endpoint Manager. Det visas *inte* på iOS-/iPadOS-enheten.
      - **Appsamlings-ID**: Ange appens samlings-ID. Se [Samlings-ID för inbyggda iOS-/iPadOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

      Du kan lägga till upp till **20** sidor för enhetsdockan.

> [!NOTE]
> När du lägger till ikoner med hjälp av dockningsinställningarna låser du ikonerna på startsidan och andra sidor så att de inte kan flyttas. Detta kan vara standardinställningen för MDM-principer med iOS/iPadOS och Apple.

#### <a name="example"></a>Exempel

I följande exempel visar skärmen dock endast apparna Safari, Mail och Stocks. Mail-appen är markerad för att visa dess egenskaper:

![Exempel på Inställningar för iOS/iPadOS dock](./media/ios-device-features-settings/FfFiUcP.png)

När du tilldelar principen till en iPhone liknar dockan följande bild:

![Exempel på iOS-/iPadOS-dockningslayout i iPhone](./media/ios-device-features-settings/bAgCe8F.png)

### <a name="pages"></a>Sidor

Lägg till de sidor som du vill ska visas på startskärmen, samt de appar som du vill ska visas på varje sida. Apparna som du lägger till på en sida ordnas från vänster till höger, i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

> [!TIP]
> För att ändra om objekt på startskärmen och sidlistor kan du dra och släppa dem.

Du kan lägga till upp till **40** sidor på en enhet.

- **Lista över sidor**: **Lägg till** en sida och ange följande egenskaper:

  - **Sidnamn**: Ange ett namn för sidan. Det här namnet används för din referens i administrationscentret för Microsoft Endpoint Manager och visas *inte* på iOS-/iPadOS-enheten.

  Du kan lägga till upp till **60** objekt (appar och mappar kombinerat) på en enhet.

  - **Lägg till**: Lägger till appar eller mappar till dockan på enheten.

    - **Typ**: Lägger till en **app** eller en **mapp**:

      - **App**: Välj det här alternativet för att lägga till appar på en sida på skärmen. Ange även:

        - **Appnamn**: Ange ett namn för appen. Det här namnet används för din referens i administrationscentret för Microsoft Endpoint Manager. Det visas *inte* på iOS-/iPadOS-enheten.
        - **Appsamlings-ID**: Ange appens samlings-ID. Se [Samlings-ID för inbyggda iOS-/iPadOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

      - **Mapp**: Välj det här alternativet för att lägga till en mapp i dockan på skärmen.

        Apparna som du lägger till på en sida i en mapp ordnas från vänster till höger, och i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

        - **Mappnamn**: Ange ett namn på mappen. Namnet visas för användare på enheten.
        - **Lägg till**: Lägger till sidor i mappen. Ange även följande egenskaper:

          - **Sidnamn**: Ange ett namn för sidan. Det här namnet används för din referens i administrationscentret för Microsoft Endpoint Manager. Det visas *inte* på iOS-/iPadOS-enheten.
          - **Appnamn**: Ange ett namn för appen. Det här namnet används för din referens i administrationscentret för Microsoft Endpoint Manager. Det visas *inte* på iOS-/iPadOS-enheten.
          - **Appsamlings-ID**: Ange appens samlings-ID. Se [Samlings-ID för inbyggda iOS-/iPadOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

#### <a name="example"></a>Exempel

I följande exempel har en ny sida med namnet **Contoso** lagts till. Sidan visar apparna Hitta vänner och Inställningar. Inställningsappen är markerad för att visa dess egenskaper:

![Exempel på startskärmsinställningar för iOS-/iPadOS i Intune](./media/ios-device-features-settings/Jc2OxyX.png)

När du tilldelar principen till en iPhone liknar sidan följande bild:

![iOS-/iPadOS-enhet med modifierad startskärm i Intune](./media/ios-device-features-settings/Bd37PHa.png)

## <a name="app-notifications"></a>Appmeddelanden

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: Automatisk enhetsregistrering (övervakad)

- **Lägg till**: Lägg till meddelanden för appar:

    ![Lägg till appmeddelande i en iOS-/iPadOS-profil i Intune](./media/ios-device-features-settings/ios-macos-app-notifications.png)

  - **Appsamlings-ID**: Ange **Appsamlings-ID** för den app som du vill lägga till. Se [Samlings-ID för inbyggda iOS-/iPadOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.
  - **Appnamn**: Ange namnet på appen som du vill lägga till. Det här namnet används för din referens i administrationscentret för Microsoft Endpoint Manager. Det visas *inte* på enheten.
  - **Utgivare**: Ange utgivaren av den app som du vill lägga till. Det här namnet används för din referens i administrationscentret för Microsoft Endpoint Manager. Det visas *inte* på enheten.
  - **Meddelanden**: **Aktivera** eller **inaktivera** att appen kan skicka meddelanden till enheten.
    - **Visa i meddelandecenter**: **Aktivera** tillåter appen att visa meddelanden i enhetens meddelandecenter. **Inaktivera** förhindrar att appen visar meddelanden i meddelandecentret.
    - **Visa på Låsskärm**: Välj **Aktivera** för att visa aviseringar från appen på enhetens låsskärm. **Inaktivera** förhindrar att appen visar meddelanden på låsskärmen.
    - **Typ av avisering**: När enheten är upplåst kan du välja hur meddelandet visas. Alternativen är:
      - **Inga**: Inga meddelanden visas.
      - **Banderoll**: En banderoll visas en kort stund med meddelandet.
      - **Modal**: Meddelandet visas och användaren måste manuellt ta bort det innan hen fortsätter att använda enheten.
    - **Aktivitetsikon på appikon**: Välj **Aktivera** för att lägga till en aktivitetsikon på appikonen. Aktivitetsikonen innebär att appen skickat en avisering.
    - **Ljud**: Välj **Aktivera** för att spela upp ett ljud när en avisering tas emot.

## <a name="lock-screen-message"></a>Meddelande på låsskärm

Den här funktionen gäller för:

- iOS 9.3 och senare
- iPadOS 13.0 och senare

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: Automatisk enhetsregistrering (övervakad)

- **Resurstagginformation**: Ange information om resurstaggen för enheten. Ange till exempel `Owned by Contoso Corp` eller `Serial Number: {{serialnumber}}`.

  Den text du anger visas i inloggningsfönstret och på låsskärmen på enheten.

- **Fotnot på låsskärmen**: Ange en kommentar som kan hjälpa dig att få tillbaka enheten om den tappas bort eller blir stulen. Du kan ange valfri text. Ange något i stil med `If found, call Contoso at ...`.

  Enhetstoken kan också användas för att lägga till enhetsspecifik information i de här fälten. Ange till exempel `Serial Number: {{serialnumber}}` om du vill visa serienumret. På låsskärmen visas texten ungefär som `Serial Number 123456789ABC`. När du anger variabler ska du använda klammerparenteser `{{ }}`. [Token för appkonfiguration](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) innehåller en lista över variabler som kan användas. Du kan också använda `deviceName` eller andra enhetsspecifika värden.

  > [!NOTE]
  > Variablerna är inte validerade i användargränssnittet och är skiftlägeskänsliga. Därför kan du se profiler sparade med felaktiga indata. Om du till exempel anger `{{DeviceID}}` istället för `{{deviceid}}` visas litteralsträngen istället för enhetens unika ID. Se till att du anger rätt information.

## <a name="single-sign-on"></a>Enkel inloggning

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: Enhetsregistrering, automatisk enhetsregistrering (övervakad)

- **Användarnamnattribut från AAD**: Intune söker efter det här attributet för varje användare i Azure Active Directory. Intune fyller sedan i respektive fält (till exempel UPN) innan XML som installeras på enheten genereras. Alternativen är:

  - **Användarens huvudnamn (UPN)** : UPN parsas på följande sätt:

    ![Attributet SSO för iOS-/iPadOS-användarnamn i Intune](./media/ios-device-features-settings/User-name-attribute.png)

    Du kan också skriva över området med texten som du anger i textrutan **Område**.

    Contoso har exempelvis flera regioner, inklusive Europa, Asien och Nordamerika. Contoso vill att Asien-användarna ska använda enkel inloggning och appen kräver UPN i `username@asia.contoso.com`-formatet. När du väljer **UPN**, tas sfären för varje användare från Azure Active Directory, som är `contoso.com`. För användare i Asien, markerar du **UPN** och anger `asia.contoso.com`. Nu blir slutanvändarens UPN `username@asia.contoso.com` i stället för `username@contoso.com`.

  - **ID för Intune-enhet**: Intune väljer automatiskt ID:t för Intune-enheten.

    Som standard behöver appar bara använda enhets-ID. Men om din app använder sfären och enhets-ID:t kan du skriva sfären i textrutan Sfär.

    > [!NOTE]
    > Som standard bör du lämna området tomt om du använder enhets-ID.

  - **Enhets-ID för Azure Active Directory**

- **Sfär**: Ange domändelen av URL:en. Ange till exempel `contoso.com`.
- **URL-prefix som används för enkel inloggning**: **Lägg till** URL:er i din organisation som kräver användarautentisering med enkel inloggning.

  När en användare exempelvis ansluter till någon av dessa platser använder iOS-/iPadOS-enheten autentiseringsuppgifterna för enkel inloggning. Användaren behöver inte ange ytterligare autentiseringsuppgifter. Om multifaktorautentisering är aktiverat måste användarna ange en autentisering till.

  > [!NOTE]
  > Dessa URL:er måste vara ett fullständigt domännamn i korrekt format. Apple kräver att dessa ska vara i formatet `http://<yourURL.domain>`.

  Mönster för URL-matchning måste börja med antingen `http://` eller `https://`. En enkel strängmatchning körs, så URL-prefixet `http://www.contoso.com/` matchar inte `http://www.contoso.com:80/`. Om du har iOS 10.0 eller iPadOS 13.0 eller senare kan ett enskilt jokertecken \* användas för att ange alla matchande värden. `http://*.contoso.com/` matchar till exempel både `http://store.contoso.com/` och `http://www.contoso.com`.

  Mönstren `http://.com` och `https://.com` matchar alla HTTP- respektive HTTPS-adresser.

- **Appar som ska använda enkel inloggning**: **Lägg till** appar på slutanvändarnas enheter som kan använda enkel inloggning.

  Matrisen `AppIdentifierMatches` måste innehålla strängar som matchar appsamlings-ID:n. Dessa strängar kan vara exakta matchningar, till exempel `com.contoso.myapp`, eller så anger du en prefixmatchning för paket-ID:t med jokertecknet \*. Jokertecknet måste komma efter en punkt (.), och får bara förekomma en gång, i slutet av strängen såsom `com.contoso.*`. När ett jokertecken används beviljas alla appar vars samlings-ID börjar med prefixet åtkomst till kontot.

  Använd **appnamn** för att ange ett användarvänligt namn som hjälper dig att identifiera paket-ID:t.

- **Förnyelsecertifikat för autentiseringsuppgifter**: Om du använder certifikat för autentisering (inte lösenord), väljer du det befintliga SCEP- eller PFX-certifikatet som autentiseringscertifikat. Vanligtvis är det här certifikatet samma certifikat som distribueras till användaren för andra profiler, till exempel VPN, WiFi eller e-post.

## <a name="web-content-filter"></a>Webbinnehållsfilter

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: Automatisk enhetsregistrering (övervakad)

- **Filtertyp**: Välj att tillåta vissa webbplatser. Alternativen är:

  - **Konfigurera webbadresser**: Använd Apples inbyggda webbfilter som söker efter innehåll som är olämpligt för barn, inklusive svordomar och sexuellt explicit språk. Den här funktionen utvärderar varje webbsida som den har lästs in, och identifierar och blockerar olämpligt innehåll. Du kan också lägga till URL:er som du inte vill ska kontrolleras av filtret. Eller blockera specifika URL:er, oavsett inställningarna för Apple-filtret.

    - **Tillåtna webbadresser**: **Lägg till** URL:er som du vill tillåta. Dessa URL:er kringgår Apple-webbfiltret.

        > [!NOTE]
        > URL:er som du anger är de URL:er som du inte vill ska utvärderas av Apple-webbfiltret. Dessa URL:er är inte en lista över tillåtna webbplatser. För att skapa en lista över tillåtna webbplatser ställer du in **Filtertyp** till **Endast vissa webbplatser**.

    - **Blockerade URL:er**: **Lägg till** URL:er som du vill stoppa från att öppnas, oavsett inställningarna i Apple-webbfiltret.

  - **Endast vissa webbplatser** (för Safari-webbläsaren endast): Dessa URL:er har lagts till i Safari-webbläsarens bokmärken. Användaren är **endast** tillåten att besöka dessa webbplatser, inga andra platser kan öppnas. Använd bara det här alternativet om du vet den exakta listan över webbadresser som kan nås av användarna.

    - **URL**: Ange URL:en till den webbplats som du vill tillåta. Ange till exempel `https://www.contoso.com`.
    - **Sökväg till bokmärke**: Apple ändrade den här inställningen. Alla bokmärken går till mappen **Godkända platser**. Bokmärken går inte in på sökvägen för bokmärket som du angav.
    - **Rubrik**: Ange en beskrivande rubrik för bokmärket.

    Om du inte anger några URL:er kommer användarna inte att komma åt några webbplatser förutom för `microsoft.com`, `microsoft.net` och `apple.com`. Dessa URL:er tillåts automatiskt av Intune.

## <a name="single-sign-on-app-extension"></a>Tillägg för enkel inloggning

Den här funktionen gäller för:

- iOS 13.0 och senare
- iPad iOS 13.0 och senare

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: Alla registreringstyper

- **Typ av SSO-apptillägg**: Välj typ av SSO-apptillägg. Alternativen är:

  - **Inte konfigurerad**: Apptillägg används inte. Om du vill inaktivera ett apptillägg kan du byta typ av SSO-tillägg till **Inte konfigurerad**.
  - **Omdirigera**: Använd ett allmänt, anpassningsbart omdirigeringsapptillägg för att utföra SSO med moderna autentiseringsflöden. Se till att du känner till tilläggs-ID:t för din organisations apptillägg.
  - **Autentiseringsuppgift**: Använd ett generiskt, anpassningsbart apptillägg för autentiseringsuppgifter för att utföra SSO med autentiseringsflöden med anrop och svar. Se till att du känner till tilläggs-ID:t för din organisations apptillägg.
  - **Kerberos**: Använd Apples inbyggda Kerberos-tillägg som ingår i iOS 13.0 och iPadOS 13.0 eller senare. Det här alternativet är en Kerberosspecifik version av appen för **Autentiseringsuppgifter**.

  > [!TIP]
  > Med hjälp av typerna **Omdirigering** och **Autentiseringsuppgifter** lägger du till dina egna konfigurationsvärden för att gå igenom tillägget. Om du använder **Autentiseringsuppgifter** bör du överväga att använda inbyggda konfigurationsinställningar från Apple i **Kerberos**-typen.

- **Tilläggs-ID** (omdirigering och autentiseringsuppgift): Ange det paket-ID som identifierar ditt SSO apptillägg, till exempel `com.apple.extensiblesso`.

- **Team-ID** (omdirigering och autentiseringsuppgift): Ange Team-ID för SSO-apptillägget. Ett team-ID är en sträng med 10 tecken (siffror och bokstäver) som genereras av Apple, t. ex. `ABCDE12345`. Team-ID är inte obligatoriskt.

  [Leta upp ditt team-ID](https://help.apple.com/developer-account/#/dev55c3c710c) (öppna Apples webbplats) om du vill ha mer information.

- **Sfär** (autentiseringsuppgift och Kerberos): Ange namnet på din autentiseringssfär. Sfärnamnet ska skrivas med versaler, t. ex. `CONTOSO.COM`. Vanligtvis är ditt sfärnamn detsamma som ditt DNS-domännamn, men skrivet i versaler.

- **Domäner** (autentiseringsuppgift och Kerberos): ange domän- eller värdnamnen för de platser som kan autentisera via SSO. Om din webbplats till exempel är `mysite.contoso.com`, är värdnamnet `mysite` och domännamnet `contoso.com`. När användarna ansluter till någon av dessa platser hanterar apptillägget verifieringsutmaningen. Med den här autentiseringen kan användare använda ansikts-ID, Touch-ID eller Apple-pinkod/-lösenord för att logga in.

  - Alla domäner i Intune-tilläggen för enkel inloggning måste vara unika. Du kan inte upprepa en domän i en inloggningsprofil för apptillägg, även om du använder olika typer av SSO-tillägg.
  - Dessa domäner är inte skiftlägeskänsliga.

- **URL:er** (endast omdirigering): Ange URL-prefixen för dina identitetsleverantörer i vars ställe som omdirigeringstillägget utför SSO. När en användare omdirigeras till dessa URL:er kommer SSO apptillägget att ingripa och uppmana SSO.

  - Alla webbadresser i Intune-tilläggen för enkel inloggning på Intune måste vara unika. Du kan inte upprepa en domän i en SSO-profil även om du använder olika typer av SSO-tillägg.
  - URL:erna måste börja med http:// eller https://.

- **Ytterligare konfiguration** (omdirigering och autentiseringsuppgift): ange ytterligare tilläggsinformation som ska skickas till SSO-apptillägget:
  - **Nyckel**: Ange namnet på det objekt som du vill lägga till, t. ex. `user name`.
  - **Typ**: ange typ av data. Alternativen är:

    - Sträng
    - Boolesk: Ange `True` eller `False` som **Konfigurationsvärde**.
    - Heltal: Ange ett tal som **Konfigurationsvärde**.
    
  - **Värde**: Ange data.

  - **Lägg till**: Välj om du vill lägga till dina konfigurationsnycklar.

- **Användning av nyckelringar** (endast Kerberos): Välj **blockera** för att förhindra att lösenord sparas och lagras i nyckelringen. **Inte konfigurerad** (standard) tillåter att lösenord sparas och lagras i nyckelringen.
- **Ansikts-ID, Touch-ID eller lösenord** (endast Kerberos): **Kräv** att användarna anger sitt ansikts-ID, Touch ID eller Apple-lösenord för att logga in på de domäner som du har lagt till. **Inte konfigurerad** (standard) kräver inte att användare använder biometrik eller lösenord för att logga in.
- **Standarddomän** (endast Kerberos): Välj **Aktivera** för att angedet **Sfärvärde** som du angav som standardsfär. **Inte konfigurerad** (standard) anger inte en standardsfär.

  > [!TIP]
  > - **Aktivera** den här inställningen om du konfigurerar flera Kerberos SSO-apptillägg i din organisation.
  > - **Aktivera** den här inställningen om du använder flera sfärer. Den anger det **Sfärvärde** som du angav som standardsfär.
  > - Lämna det **Okonfigurerat** (standard) om du bara har en sfär.

- **Huvud namn** (endast Kerberos): Ange användarnamnet för Kerberos-huvudobjektet. Du behöver inte inkludera sfärnamnet. Till exempel, i `user@contoso.com` är `user` huvudnamnet och sfärnamnet är `contoso.com`.

  > [!TIP]
  > - Du kan också använda variabler i huvudnamnet genom att ange klammerparenteser `{{ }}`. Om du till exempel vill visa användarnamnet anger du `Username: {{username}}`. 
  > - Var dock försiktig med variabelersättning eftersom variablerna inte verifieras i användargränssnittet och är shiftlägeskänsliga. Se till att du anger rätt information.

- **Active Directory-platskod** (endast Kerberos): Ange namnet på den Active Directory-plats som Kerberos-tillägget ska använda. Du kanske inte behöver ändra det här värdet eftersom Kerberos-tillägget automatiskt kan hitta Active Directory-platskoden.
- **Cachenamn** (endast Kerberos): Ange GSS-namnet (Generic Security Services) för Kerberos-cachen. Du behöver förmodligen inte ange det här värdet.
- **Programpaket-ID:n** (endast Kerberos): **Lägg till** de appsamlings-ID:n som ska använda enkel inloggning på dina enheter. De här apparna beviljas åtkomst till en Kerberos Ticket Granting-biljett, autentiseringsbiljetten och autentiserar användare till de tjänster som de har behörighet att komma åt.
- **Domänsfärmappning** (endast Kerberos): **Lägg till** DNS-suffixet för domänen som ska mappas till din sfär. Använd den här inställningen när DNS-namnen på värdarna inte matchar sfärnamnet. Du behöver förmodligen inte skapa den här anpassade domän-till-sfär-mappningen.
- **PKINIT-certifikat** (endast Kerberos): **Välj** den kryptering för offentlig nyckel för inledande autentisering (PKINIT) som kan användas för Kerberos-autentisering. Du kan välja mellan [PKCS](../protect/certficates-pfx-configure.md)- eller [SCEP](../protect/certificates-scep-configure.md) -certifikat som du har lagt till i Intune. Mer information om certifikat finns i [Använda certifikat för autentisering i Microsoft Intune](../protect/certificates-configure.md).

## <a name="wallpaper"></a>Skrivbordsunderlägg

Ett oväntat beteende kan uppstå när en profil utan bild tilldelas till enheter med en befintlig bild. Exempel: Du skapar en profil utan någon bild. Profilen tilldelas till enheter som redan har en bild. I det här scenariot kan bilden ändras till enhetens standardinställda eller så kan den ursprungliga bilden stanna kvar på enheten. Det här beteendet styrs och begränsas av Apples MDM-plattform.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: Automatisk enhetsregistrering (övervakad)

- **Plats för visning av bakgrundsbild**: Välj en plats på enheten för att visa bilden. Alternativen är:
  - **Inte konfigurerad**: En anpassad bild inte har lagts till på enheten. Enheten använder standardoperativsystemet.
  - **Låsskärm**: Lägger till bilden till låsskärmen.
  - **Startsida**: Lägger till bilden till startsidan.
  - **Låsskärm och startskärm**: Använder samma bild på låsskärmen och startskärmen.
- **Bakgrundsbild**: Ladda upp en befintlig PNG-, JPG- eller JPEG-bild som du vill använda. Var noga med att filstorleken är mindre än 750 KB. Du kan också **ta bort** en bild som du har lagt till.

> [!TIP]
> För att visa olika bilder på låsskärmen och startsidan, skapa en profil med bilden för låsskärmen. Skapa en annan profil med bilden för startsidan. Tilldela båda profilerna till din iOS-/iPadOS-användare eller dina enhetsgrupper.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

Du kan också skapa enhetsprofiler för [macOS](macos-device-features-settings.md)-enheter.
