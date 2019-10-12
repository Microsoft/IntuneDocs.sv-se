---
title: Funktionsinställningar för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se alla inställningar för att konfigurera iOS-enheter för AirPrint, layout för startsidan, appmeddelanden, delad enhet, enkel inloggning och webbinnehållsfilter i Microsoft Intune. Använd dessa inställningar i en enhetskonfigurationsprofil när du konfigurerar iOS-enheter för att använda Apple-funktionerna i din organisation.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 341609afeec02c67b4ea0d85a541fca61345ced4
ms.sourcegitcommit: fca2670142c083d7562c0a36547a6a451863e315
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/08/2019
ms.locfileid: "72036487"
---
# <a name="ios-and-ipados-device-settings-to-use-common-ios-features-in-intune"></a>iOS- och iPadOS-enhetsinställningar som används; vanliga iOS-funktioner i Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune innehåller vissa inbyggda inställningar för att tillåta iOS-användare att använda olika Apple-funktioner på sina enheter. Till exempel så kan administratörer styra hur iOS-användare använder AirPrint-skrivare, lägga till appar och mappar till dockan och sidor på startskärmen, visa meddelanden i appen, visa information om tillgångstagg på låsskärmen, använda enkel inloggning och autentisera användare med certifikat.

Du kan använda dessa funktioner för att styra iOS-enheter som en del av din MDM-lösning för hantering av mobilenheter.

I den här artikeln visas inställningarna, tillsammans med en beskrivning av vad varje inställning gör. Mer information om dessa funktioner finns i lägga till [iOS-eller MacOS-enhetens funktions inställningar](../device-features-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en iOS-enhetskonfigurationsprofil](../device-features-configure.md).

> [!NOTE]
> Dessa inställningar gäller för olika registrerings typer, med vissa inställningar som gäller för alla registrerings alternativ. Mer information om de olika registrerings typerna finns i [iOS-registrering](../ios-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

> [!NOTE]
> Se till att lägga till alla skrivare till samma profil. Apple förhindrar flera profiler för att skriva ut på samma enhet.

- **IP-adress**: Ange skrivarens IPv4- eller IPv6-adress. Om du använder värdnamn till att identifiera skrivare, kan du hämta IP-adressen genom att pinga skrivaren i terminalen. Det finns mer information i Hämta IP-adress och sökväg (i den här artikeln).
- **Sökväg**: Sökvägen är vanligtvis `ipp/print` för skrivare i nätverket. Det finns mer information i Hämta IP-adress och sökväg (i den här artikeln).
- **Port**: Ange lyssningsporten för AirPrint-målet. Om du lämnar den här egenskapen tom, kommer AirPrint att använda standardporten. Tillgängligt i iOS 11.0 och senare.
- **TLS**: Välj **Aktivera** för att skydda AirPrint-anslutningar med TLS (Transport Layer Security). Tillgängligt i iOS 11.0 och senare.

Om du vill lägga till luftutskrifts servrar kan du:

- **Lägg till** lägger till AirPrint-servern i listan. Det går att lägga till många olika luftutskrifts servrar.
- **Importera** en kommaavgränsad fil (CSV) med den här informationen. Eller **Exportera** för att skapa en lista med de de skrivar servrar som du har lagt till.

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

- iOS 9,3 eller senare

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

### <a name="dock"></a>Docka

Använd inställningarna **Docka** för att lägga till upp till sex objekt eller mappar till dockan på iOS-skärmen. Många enheter stöder färre objekt. Till exempel stöder iPhone-enheter upp till fyra objekt. I det här fallet visas endast de första fyra objekt som du har lagt till på enheten.

Du kan lägga till upp till **sex** objekt (appar och mappar som kombineras) för enhetens docka.

- **Lägg till**: Lägger till appar eller mappar till dockan på enheten.
- **Typ**: Lägger till en **app** eller en **mapp**:

  - **App**: Välj det här alternativet för att lägga till appar i dockan på skärmen. Ange:

    - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
    - **Appsamlings-ID**: Ange samlings-ID för appen. Se [Samlings-ID för inbyggda iOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

  - **Mapp**: Välj det här alternativet för att lägga till en mapp i dockan på skärmen.

    Apparna som du lägger till på en sida i en mapp ordnas från vänster till höger, och i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

    - **Mappnamn**: Ange namnet på mappen. Namnet visas för användare på deras enhet.
    - **Lista över sidor**: **Lägg till** en sida och ange följande egenskaper:

      - **Sidnamn**: Ange ett namn för sidan. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
      - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
      - **Appsamlings-ID**: Ange samlings-ID för appen. Se [Samlings-ID för inbyggda iOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

      Du kan lägga till upp till **20** sidor för enhetsdockan.

> [!NOTE]
> När du lägger till ikoner med hjälp av dockningsinställningarna låser du ikonerna på startsidan och andra sidor så att de inte kan flyttas. Detta kan vara standardinställningen för MDM-principer med iOS och Apple.

#### <a name="example"></a>Exempel

I följande exempel visar skärmen dock endast apparna Safari, Mail och Stocks. Mail-appen är markerad för att visa dess egenskaper:

![Exempel på iOS-dockningsinställningar](./media/ios-device-features-settings/FfFiUcP.png)

När du tilldelar principen till en iPhone liknar dockan följande bild:

![Exempel på iOS-dockningslayout i iPhone](./media/ios-device-features-settings/bAgCe8F.png)

### <a name="pages"></a>Sidor

Lägg till de sidor som du vill ska visas på startskärmen, samt de appar som du vill ska visas på varje sida. Apparna som du lägger till på en sida ordnas från vänster till höger, i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

> [!TIP]
> För att ändra om objekt på startskärmen och sidlistor kan du dra och släppa dem.

Du kan lägga till upp till **40** sidor på en enhet.

- **Lista över sidor**: **Lägg till** en sida och ange följande egenskaper:

  - **Sidnamn**: Ange ett namn för sidan. Det här namnet används som din referens i Azure-portalen och visas *inte* på iOS-enheten.

  Du kan lägga till upp till **60** objekt (appar och mappar kombinerat) på en enhet.

  - **Lägg till**: Lägger till appar eller mappar till dockan på enheten.

    - **Typ**: Lägger till en **app** eller en **mapp**:

      - **App**: Välj det här alternativet för att lägga till appar på en sida på skärmen. Ange även:

        - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
        - **Appsamlings-ID**: Ange samlings-ID för appen. Se [Samlings-ID för inbyggda iOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

      - **Mapp**: Välj det här alternativet för att lägga till en mapp i dockan på skärmen.

        Apparna som du lägger till på en sida i en mapp ordnas från vänster till höger, och i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

        - **Mappnamn**: Ange ett namn på mappen. Namnet visas för användare på enheten.
        - **Lägg till**: Lägger till sidor i mappen. Ange även följande egenskaper:

          - **Sidnamn**: Ange ett namn för sidan. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
          - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
          - **Appsamlings-ID**: Ange samlings-ID för appen. Se [Samlings-ID för inbyggda iOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

#### <a name="example"></a>Exempel

I följande exempel har en ny sida med namnet **Contoso** lagts till. Sidan visar apparna Hitta vänner och Inställningar. Inställningsappen är markerad för att visa dess egenskaper:

![Exempel på inställningar på iOS-startskärmen](./media/ios-device-features-settings/Jc2OxyX.png)

När du tilldelar principen till en iPhone liknar sidan följande bild:

![iOS-enhet med ändrad startskärm](./media/ios-device-features-settings/Bd37PHa.png)

## <a name="app-notifications"></a>Appmeddelanden

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Lägg till**: Lägg till meddelanden för appar:

    ![Lägg till appmeddelande i en iOS-profil i Intune](./media/ios-device-features-settings/ios-macos-app-notifications.png)

  - **Appsamlings-ID** – Ange **Appsamlings-ID** för den app som du vill lägga till. Se [Samlings-ID för inbyggda iOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.
  - **Appnamn**: Ange namnet på den app som du vill lägga till. Det här namnet används som din referens i Azure Portal. Det visas *inte* på enheten.
  - **Utgivare**: Ange utgivaren av den app som du lägger till. Det här namnet används som din referens i Azure Portal. Det visas *inte* på enheten.
  - **Meddelanden**: **Aktivera** eller **Inaktivera** att appen kan skicka meddelanden till enheten.
    - **Visa i Meddelandecenter**: **Aktivera** tillåter att appen visar aviseringar i enhetens meddelandecenter. **Inaktivera** förhindrar att appen visar meddelanden i meddelandecentret.
    - **Visa på låsskärm**: Välj **Aktivera** för att visa aviseringar från appen på enhetens låsskärm. **Inaktivera** förhindrar att appen visar meddelanden på låsskärmen.
    - **Aviseringstyp**: När enheten är upplåst kan du välja hur meddelandet visas. Alternativen är:
      - **Ingen**: Inga meddelanden visas.
      - **Banderoll**: En banderoll visas en kort stund med meddelandet.
      - **Modal**: Meddelandet visas och användaren måste manuellt ta bort det innan hen fortsätter att använda enheten.
    - **Bricka på appikon**: Välj **Aktivera** om du vill lägga till en aktivitetssymbol till appikonen. Aktivitetsikonen innebär att appen skickat en avisering.
    - **Ljud**: Välj **Aktivera** för att spela upp ett ljud när en avisering tas emot.

## <a name="lock-screen-message"></a>Meddelande på låsskärm

Den här funktionen gäller för:

- iOS 9.3 och senare

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Resurstagginformation**: Ange information om resurstaggen för enheten. Ange till exempel `Owned by Contoso Corp` eller `Serial Number: {{serialnumber}}`.

  Den text du anger visas i inloggningsfönstret och på låsskärmen på enheten.

- **Fotnot på låsskärmen**: Ange en kommentar som kan hjälpa dig att få tillbaka enheten om den tappas bort eller blir stulen. Du kan ange valfri text. Ange något i stil med `If found, call Contoso at ...`.

  Enhetstoken kan också användas för att lägga till enhetsspecifik information i de här fälten. Ange till exempel `Serial Number: {{serialnumber}}` om du vill visa serienumret. På låsskärmen visas texten ungefär som `Serial Number 123456789ABC`. När du anger variabler ska du använda klammerparenteser `{{ }}`. [Token för appkonfiguration](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) innehåller en lista över variabler som kan användas. Du kan också använda `deviceName` eller andra enhetsspecifika värden.

  > [!NOTE]
  > Variablerna är inte validerade i användar gränssnittet och är Skift läges känsliga. Därför kan du se profiler sparade med felaktiga indata. Om du till exempel anger `{{DeviceID}}` istället för `{{deviceid}}` visas litteralsträngen istället för enhetens unika ID. Se till att ange rätt information.

## <a name="single-sign-on"></a>Enkel inloggning

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Inställningarna gäller för: enhets registrering, automatisk enhets registrering (övervakad)

- **Användarnamnattribut från AAD**: Intune söker efter det här attributet för varje användare i Azure AD. Intune fyller sedan i respektive fält (till exempel UPN) innan XML som installeras på enheten genereras. Alternativen är:

  - **User Principal Name**: UPN parsas på följande sätt:

    ![Användarnamnattribut](./media/ios-device-features-settings/User-name-attribute.png)

    Du kan också skriva över området med texten som du anger i textrutan **Område**.

    Contoso har exempelvis flera regioner, inklusive Europa, Asien och Nordamerika. Contoso vill att Asien-användarna ska använda enkel inloggning och appen kräver UPN i `username@asia.contoso.com`-formatet. När du väljer **UPN**, tas sfären för varje användare från Azure Active Directory, som är `contoso.com`. För användare i Asien, markerar du **UPN** och anger `asia.contoso.com`. Nu blir slutanvändarens UPN `username@asia.contoso.com` i stället för `username@contoso.com`.

  - **ID för Intune-enhet**: Intune väljer automatiskt ID:t för Intune-enheten.

    Som standard behöver appar bara använda enhets-ID. Men om din app använder sfären och enhets-ID:t kan du skriva sfären i textrutan Sfär.

    > [!NOTE]
    > Som standard bör du lämna området tomt om du använder enhets-ID.

  - **Enhets-ID för Azure Active Directory**

- **Sfär**: Ange domändelen av URL:en. Ange till exempel `contoso.com`.
- **URL-prefix som används för enkel inloggning**: **Lägg till** alla URL:er i din organisation som kräver användarautentisering via enkel inloggning.

  När en användare exempelvis ansluter till någon av dessa platser använder iOS-enheten autentiseringsuppgifterna för enkel inloggning. Användaren behöver inte ange ytterligare autentiseringsuppgifter. Om multifaktorautentisering är aktiverat måste användarna ange en autentisering till.

  > [!NOTE]
  > Dessa URL:er måste vara ett fullständigt domännamn i korrekt format. Apple kräver att dessa ska vara i formatet `http://<yourURL.domain>`.

  Mönster för URL-matchning måste börja med antingen `http://` eller `https://`. En enkel strängmatchning körs, så URL-prefixet `http://www.contoso.com/` matchar inte `http://www.contoso.com:80/`. Om du har iOS 10.0 eller senare kan ett enskilt jokertecken \* användas för att ange alla matchande värden. `http://*.contoso.com/` matchar till exempel både `http://store.contoso.com/` och `http://www.contoso.com`.

  Mönstren `http://.com` och `https://.com` matchar alla HTTP- respektive HTTPS-adresser.

- **Appar som ska använda enkel inloggning**: **Lägg till** appar på slutanvändarnas enheter som kan använda enkel inloggning.

  Matrisen `AppIdentifierMatches` måste innehålla strängar som matchar appsamlings-ID:n. Dessa strängar kan vara exakta matchningar, till exempel `com.contoso.myapp`, eller så anger du en prefixmatchning för paket-ID:t med jokertecknet \*. Jokertecknet måste komma efter en punkt (.), och får bara förekomma en gång, i slutet av strängen såsom `com.contoso.*`. När ett jokertecken används beviljas alla appar vars samlings-ID börjar med prefixet åtkomst till kontot.

  Använd **appnamn** för att ange ett användarvänligt namn som hjälper dig att identifiera paket-ID:t.

- **Certifikat för förnyelse av autentiseringsuppgifter**: Om du använder certifikat för autentisering (inte lösenord), väljer du det befintliga SCEP- eller PFX-certifikatet som autentiseringscertifikat. Vanligtvis är det här certifikatet samma certifikat som distribueras till användaren för andra profiler, till exempel VPN, WiFi eller e-post.

## <a name="web-content-filter"></a>Webbinnehållsfilter

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Filtertyp**: Välj att tillåta vissa webbplatser. Alternativen är:

  - **Konfigurera URL:er**: Använd Apples inbyggda webbfilter som söker efter innehåll som är olämpligt för barn, inklusive svordomar och sexuellt explicit språk. Den här funktionen utvärderar varje webbsida som den har lästs in, och identifierar och blockerar olämpligt innehåll. Du kan också lägga till URL:er som du inte vill ska kontrolleras av filtret. Eller blockera specifika URL:er, oavsett inställningarna för Apple-filtret.

    - **Tillåtna webbadresser**: **Lägg till** de URL:er som du vill tillåta. Dessa URL:er kringgår Apple-webbfiltret.

        > [!NOTE]
        > URL:er som du anger är de URL:er som du inte vill ska utvärderas av Apple-webbfiltret. Dessa URL:er är inte en lista över tillåtna webbplatser. För att skapa en lista över tillåtna webbplatser ställer du in **Filtertyp** till **Endast vissa webbplatser**.

    - **Blockerade URL:er**: **Lägg till** URL:er som du vill hindra från att öppnas, oavsett inställningarna i Apple-webbfiltret.

  - **Endast vissa webbplatser** (endast för Safari-webbläsaren): Dessa webbadresser läggs till i Safari-webbläsarens bokmärken. Användaren är **endast** tillåten att besöka dessa webbplatser, inga andra platser kan öppnas. Använd bara det här alternativet om du vet den exakta listan över webbadresser som kan nås av användarna.

    - **URL**: Ange URL:en till den webbplats som du vill tillåta. Ange till exempel `https://www.contoso.com`.
    - **Bokmärkessökväg**: Ange sökvägen där du vill lagra bokmärket. Ange till exempel `/Contoso/Business Apps`. Om du inte lägger till någon sökväg läggs bokmärket till i standardmappen för bokmärken på enheten.
    - **Rubrik**: Ange en beskrivande rubrik för bokmärket.

    Om du inte anger några URL:er kommer användarna inte att komma åt några webbplatser förutom för `microsoft.com`, `microsoft.net` och `apple.com`. Dessa URL:er tillåts automatiskt av Intune.

## <a name="single-sign-on-app-extension"></a>Tillägg för enkel inloggning

Den här funktionen gäller för:

- iOS 13.0 och senare
- iPad 13,0 och senare

### <a name="settings-apply-to-all-enrollment-types"></a>Inställningarna gäller för: alla registrerings typer

- **Typ av SSO-app-tillägg**: Välj typ av AUTENTISERINGSUPPGIFTER för SSO-appen. När du sparar tilläggs profilen för SSO-appen kan du inte ändra tillägget för SSO-appen. Alternativen är:

  - **Inte konfigurerad**: app-tillägg används inte. Om du vill inaktivera ett app-tillägg kan du byta namn på SSO-appen från **Kerberos** eller **Credential** till **inte konfigurerad**.
  - **Autentiseringsuppgift**: Använd ett allmänt, anpassningsbart app-tillägg för autentiseringsuppgifter för att utföra SSO. Se till att du känner till tilläggs-ID: t för din organisations SSO app-tillägg.
  - **Kerberos**: Använd Apples inbyggda Kerberos-tillägg, som ingår i iOS 13,0 (och senare) och iPad 13,0 (och senare). Det här alternativet är en Kerberos-speciell version av appen för **autentiseringsuppgifter** .

  > [!TIP]
  > Med typen **autentiseringsuppgift** lägger du till dina egna konfigurations värden för att gå igenom tillägget. Överväg i stället att använda inbyggda konfigurations inställningar från Apple i **Kerberos** -typen.

- **Tilläggs-ID** (endast autentiseringsuppgift): Ange paket-ID: t som identifierar ditt SSO app-tillägg, till exempel `com.apple.extensiblesso`.
- **Team-ID** (endast autentiseringsuppgift): Ange Team-ID för SSO-appens tillägg. Ett team-ID är en sträng med 10 tecken (siffror och bokstäver) som genereras av Apple, till exempel `ABCDE12345`. Grupp-ID: t är inte obligatoriskt.

  [Leta upp ditt team-ID](https://help.apple.com/developer-account/#/dev55c3c710c) (öppna Apples webbplats) om du vill ha mer information.

- **Sfär**: Ange namnet på din Kerberos-sfär. Sfär namnet ska vara kapitaliserat, t. ex. `CONTOSO.COM`. Vanligt vis är ditt sfär namn detsamma som ditt DNS-domännamn, men i alla versaler.

- **Domäner**: ange domän-eller värd namnen för de platser som kan AUTENTISERA via SSO. Om din webbplats till exempel är `mysite.contoso.com`, är `mysite` värd namnet och `contoso.com` är domän namnet. När användarna ansluter till någon av dessa platser hanterar app-tillägget verifierings utmaningen. Med den här autentiseringen kan användare använda ansikts-ID, Touch-ID eller Apple-Pincode/lösen ord för att logga in.

  - Alla domäner i Intune-tilläggen för enkel inloggning måste vara unika. Du kan inte upprepa en domän i valfri inloggnings profil för program tillägg, även om du använder olika typer av SSO-tillägg.
  - Dessa domäner är inte Skift läges känsliga.

- **Ytterligare konfiguration** (endast autentiseringsuppgift): ange ytterligare tilläggs information som ska skickas till SSO-appens tillägg:
  - **Konfigurations nyckel**: Ange namnet på det objekt som du vill lägga till, till exempel `user name`.
  - **Värdetyp**: ange typ av data. Alternativen är:

    - Sträng
    - Booleskt värde: Ange `True` eller `False` i **konfiguration svärdet**.
    - Heltal: Ange ett tal i **konfiguration svärdet**.
    
  - **Konfigurations värde**: ange data.

  - **Lägg till**: Välj om du vill lägga till dina konfigurations nycklar.

- **Användning av nyckel ringar** (endast Kerberos): Välj **blockera** för att förhindra att lösen ord sparas och lagras i nyckel ringen. **Inte konfigurerad** (standard) tillåter att lösen ord sparas och lagras i nyckel ringen.
- **Ansikts-ID, Touch-ID eller lösen ord** (endast Kerberos): **Kräv** att användarna anger sitt ansikts-ID, Touch ID eller Apple-lösenord för att logga in på de domäner som du har lagt till. **Inte konfigurerad** (standard) kräver inte att användare använder biometrik eller lösen ord för att logga in.
- **Standard domän** (endast Kerberos): Välj **Aktivera** för att ange det **sfär** värde som du angav som standard sfär. **Inte konfigurerad** (standard) anger inte en standard sfär.

  > [!TIP]
  > - **Aktivera** den här inställningen om du konfigurerar flera Kerberos SSO app-tillägg i din organisation.
  > - **Aktivera** den här inställningen om du använder flera sfärer. Den anger det **sfär** värde som du angav som standard sfär.
  > - Lämna det **inte konfigurerat** (standard) om du bara har en sfär.

- **Huvud namn** (endast Kerberos): Ange användar namnet för Kerberos-huvudobjektet. Du behöver inte inkludera sfär namnet. I `user@contoso.com` är `user` till exempel huvud namnet och `contoso.com` är sfär namnet.
- **Active Directory platskod** (endast Kerberos): Ange namnet på den Active Directory plats som Kerberos-tillägget ska använda. Du kanske inte behöver ändra det här värdet eftersom Kerberos-tillägget automatiskt kan hitta Active Directory platskod.
- **Cache-namn** (endast Kerberos): Ange GSS-namnet (Generic Security Services) för Kerberos-cachen. Du behöver förmodligen inte ange det här värdet.
- **Programpaket-ID: n** (endast Kerberos): **Lägg till** de ID: n för appen som ska använda enkel inloggning på dina enheter. De här apparna beviljas åtkomst till biljett beviljande biljetten i Kerberos, autentiserings biljetten och autentisera användare till tjänster som de har behörighet att komma åt.
- **Domän sfär mappning** (endast Kerberos): **Lägg till** DNS-suffixet för domänen som ska mappas till din sfär. Använd den här inställningen när DNS-namnen på värdarna inte matchar sfär namnet. Du behöver förmodligen inte skapa den här anpassade domän-till-sfär-mappningen.

## <a name="wallpaper"></a>Skrivbordsunderlägg

Ett oväntat beteende kan uppstå när en profil utan bild tilldelas till enheter med en befintlig bild. Exempel: Du skapar en profil utan någon bild. Profilen tilldelas till enheter som redan har en bild. I det här scenariot kan bilden ändras till enhetens standardinställda eller så kan den ursprungliga bilden stanna kvar på enheten. Det här beteendet styrs och begränsas av Apples MDM-plattform.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Inställningarna gäller för: automatisk enhets registrering (övervakad)

- **Plats för visning av bakgrundsbild**: Välj var på enheten som bilden ska visas. Alternativen är:
  - **Inte konfigurerad**: Ingen anpassad bild läggs till på enheten. Enheten använder standardoperativsystemet.
  - **Låsskärm**: Bilden läggs till på låsskärmen.
  - **Startsida**: Bilden läggs till på startsidan.
  - **Låsskärm och hemskärm**: Samma bild används på låsskärmen och startskärmen.
- **Bakgrundsbild**: Ladda upp en befintlig PNG-, JPG- eller JPEG-bild som du vill använda. Var noga med att filstorleken är mindre än 750 KB. Du kan också **ta bort** en bild som du har lagt till.

> [!TIP]
> För att visa olika bilder på låsskärmen och startsidan, skapa en profil med bilden för låsskärmen. Skapa en annan profil med bilden för startsidan. Tilldela båda profilerna till din iOS-användare eller dina enhetsgrupper.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

Du kan också skapa enhetsprofiler för [macOS](macos-device-features-settings.md)-enheter.
