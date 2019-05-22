---
title: Funktionsinställningar för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se alla inställningar för att konfigurera iOS-enheter för AirPrint, layout för startsidan, appmeddelanden, delad enhet, enkel inloggning och webbinnehållsfilter i Microsoft Intune. Använd dessa inställningar i en enhetskonfigurationsprofil när du konfigurerar iOS-enheter för att använda de olika Apple-funktionerna i din organisation.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1bcd3a5d0b9f7abc1aa2e0b4d96c30c956b6b4c7
ms.sourcegitcommit: b0cf661145ccc6e3518db620af199786a623a0d9
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64764893"
---
# <a name="ios-device-settings-to-use-common-ios-features-in-intune"></a>iOS-enhetsinställningar som används; vanliga iOS-funktioner i Intune

Intune innehåller vissa inbyggda inställningar för att tillåta iOS-användare att använda olika Apple-funktioner på sina enheter. Till exempel så kan administratörer styra hur iOS-användare använder AirPrint-skrivare, lägga till appar och mappar till dockan och sidor på startskärmen, visa meddelanden i appen, visa information om tillgångstagg på låsskärmen, använda enkel inloggning och autentisera användare med certifikat.

Du kan använda dessa funktioner för att styra iOS-enheter som en del av din MDM-lösning för hantering av mobilenheter.

I den här artikeln visas inställningarna, tillsammans med en beskrivning av vad varje inställning gör.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en iOS-enhetskonfigurationsprofil](device-features-configure.md#create-a-device-profile).

## <a name="airprint"></a>AirPrint

- **IP-adress**: Ange skrivarens IPv4- eller IPv6-adress. Om du använder värdnamn till att identifiera skrivare, kan du hämta IP-adressen genom att pinga skrivaren i terminalen. Det finns mer information i Hämta IP-adress och sökväg (i den här artikeln).
- **Sökväg**: Sökvägen är vanligtvis `ipp/print` för skrivare i nätverket. Det finns mer information i Hämta IP-adress och sökväg (i den här artikeln).
- **Port**: Ange lyssningsporten för AirPrint-målet. Om du lämnar den här egenskapen tom, kommer AirPrint att använda standardporten. Tillgängligt i iOS 11.0 och senare.
- **TLS**: Välj **Aktivera** för att skydda AirPrint-anslutningar med TLS (Transport Layer Security). Tillgängligt i iOS 11.0 och senare.

**Lägg till** lägger till AirPrint-servern i listan. Du kan lägga till flera AirPrint-servrar. Du kan också **Importera** en kommaavgränsad fil (CSV) med den här informationen. När du har skapat listan, kan du också **Exportera** din lista över AirPrint-servrar.

Klicka på **OK** för att spara listan.

### <a name="get-server-ip-address-resource-path-and-port"></a>Hämta IP-adress för server, resurssökväg och port

Om du vill lägga till AirPrinter-servrar, behöver du ha skrivarens IP-adress, resurssökväg och port. Följande steg visar hur du hämtar den här informationen.

1. Öppna **Terminal** (från **/Program/Verktyg**) på en Mac som är ansluten till samma lokala nätverk (undernät) som AirPrint-skrivarna.
2. I Terminal skriver du `ippfind` och väljer Retur.

    Observera skrivarinformationen. Du kan exempelvis ange något i stil med `ipp://myprinter.local.:631/ipp/port1`. Den första delen är namnet på skrivaren. Den sista delen (`ipp/port1`) är resurssökvägen.

3. I Terminal skriver du `ping myprinter.local` och väljer Retur.

   Observera IP-adressen. Den visar något i stil med `PING myprinter.local (10.50.25.21)`.

4. Använd värdena för IP-adressen och resurssökvägen. I det här exemplet är IP-adressen `10.50.25.21` och resurssökvägen är `/ipp/port1`.

## <a name="home-screen-layout-settings"></a>Layoutinställningar för startskärm

Dessa inställningar konfigurerar applayouten och mappar på dockan och startskärmen på iOS-enheter. Om du vill använda den här funktionen, måste iOS-enheter vara i övervakat läge och köra iOS 9.3 eller senare.

### <a name="dock"></a>Docka

Använd inställningarna **Docka** för att lägga till upp till sex objekt eller mappar till dockan på iOS-skärmen. Många enheter stöder färre objekt. Till exempel stöder iPhone-enheter upp till fyra objekt. I det här fallet visas endast de första fyra objekt som du har lagt till på enheten.

Du kan lägga till upp till **sex** objekt (appar och mappar som kombineras) för enhetens docka.

- **Lägg till**: Lägger till appar eller mappar till dockan på enheten.
- **Typ**: Lägger till en **app** eller en **mapp**:

  - **App**: Välj det här alternativet för att lägga till appar i dockan på skärmen. Ange:

    - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
    - **Appsamlings-ID**: Ange samlings-ID för appen. Se [Samlings-ID för inbyggda iOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

    Klicka på **OK** för att spara ändringarna.

  - **Mapp**: Välj det här alternativet för att lägga till en mapp i dockan på skärmen.

    Apparna som du lägger till på en sida i en mapp ordnas från vänster till höger, och i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

    - **Mappnamn**: Ange namnet på mappen. Namnet visas för användare på deras enhet.
    - **Lista över sidor**: **Lägg till** en sida och ange följande egenskaper:

      - **Sidnamn**: Ange ett namn för sidan. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
      - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
      - **Appsamlings-ID**: Ange samlings-ID för appen. Se [Samlings-ID för inbyggda iOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

      Du kan lägga till upp till **20** sidor för enhetsdockan.

    Klicka på **OK** för att spara ändringarna.

> [!NOTE]
> När du lägger till ikoner med hjälp av dockningsinställningarna låser du ikonerna på startsidan och andra sidor så att de inte kan flyttas. Detta kan vara standardinställningen för MDM-principer med iOS och Apple.

#### <a name="example"></a>Exempel

I följande exempel visar skärmen dock endast apparna Safari, Mail och Stocks. Mail-appen är markerad för att visa dess egenskaper:

![Exempel på iOS-dockningsinställningar](./media/FfFiUcP.png)

När du tilldelar principen till en iPhone liknar dockan följande bild:

![Exempel på iOS-dockningslayout i iPhone](./media/bAgCe8F.png)

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

      Klicka på **OK** för att spara ändringarna.

      - **Mapp**: Välj det här alternativet för att lägga till en mapp i dockan på skärmen.

        Apparna som du lägger till på en sida i en mapp ordnas från vänster till höger, och i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

        - **Mappnamn**: Ange ett namn på mappen. Namnet visas för användare på enheten.
        - **Lägg till**: Lägger till sidor i mappen. Ange även följande egenskaper:

          - **Sidnamn**: Ange ett namn för sidan. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
          - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
          - **Appsamlings-ID**: Ange samlings-ID för appen. Se [Samlings-ID för inbyggda iOS-appar](bundle-ids-built-in-ios-apps.md) för några exempel.

      Klicka på **OK** för att spara ändringarna.

#### <a name="example"></a>Exempel

I följande exempel har en ny sida med namnet **Contoso** lagts till. Sidan visar apparna Hitta vänner och Inställningar. Inställningsappen är markerad för att visa dess egenskaper:

![Exempel på inställningar på iOS-startskärmen](./media/Jc2OxyX.png)

När du tilldelar principen till en iPhone liknar sidan följande bild:

![iOS-enhet med ändrad startskärm](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>Inställningar för appmeddelanden

Välj hur installerade appar på iOS-enheter skickar meddelanden. Inställningarna har stöd för övervakade enheter som kör iOS 9.3 och senare.

- **Lägg till**: Lägg till meddelanden för appar:

    ![Lägg till appmeddelande i en iOS-profil i Intune](./media/ios-macos-app-notifications.png)

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

Klicka på **OK** för att spara ändringarna.

## <a name="lock-screen-message-settings"></a>Inställningar för meddelande på låsskärm

Använd de här inställningarna för att visa ett anpassat meddelande eller text i inloggningsfönstret och på låsskärmen. Du kan till exempel skriva ett meddelande av typen ”Upphittad enhet återlämnas till...” och resurstagginformation. 

Den här funktionen har stöd för övervakade enheter som kör iOS 9.3 och senare.

- **Resurstagginformation**: Ange information om resurstaggen för enheten. Ange till exempel `Owned by Contoso Corp` eller `Serial Number: {{serialnumber}}`.

  Den text du anger visas i inloggningsfönstret och på låsskärmen på enheten.

- **Fotnot på låsskärmen**: Ange en kommentar som kan hjälpa dig att få tillbaka enheten om den tappas bort eller blir stulen. Du kan ange valfri text. Ange något i stil med `If found, call Contoso at ...`.

  Enhetstoken kan också användas för att lägga till enhetsspecifik information i de här fälten. Ange till exempel `Serial Number: {{serialnumber}}` om du vill visa serienumret. På låsskärmen visas texten ungefär som `Serial Number 123456789ABC`. När du anger variabler ska du använda klammerparenteser `{{ }}`. [Token för appkonfiguration](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) innehåller en lista över variabler som kan användas. Du kan också använda `deviceName` eller andra enhetsspecifika värden.

  > [!NOTE]
  > Variabler verifieras inte i användargränssnittet. Därför kan du se profiler sparade med felaktiga indata. Om du till exempel anger `{{Devicename}}` istället för `{{devicename}}` visas litteralsträngen istället för enhetens unika namn.

Klicka på **OK** för att spara ändringarna.

## <a name="single-sign-on-settings"></a>Inställningar för enkel inloggning

De flesta verksamhetsspecifika appar kräver av säkerhetsskäl någon nivå av användarautentisering. I många fall kräver den här autentiseringen att användaren anger samma autentiseringsuppgifter upprepade gånger, vilket är frustrerande för användaren. För att förbättra användarupplevelsen kan utvecklare skapa appar som använder enkel inloggning (SSO). Med enkel inloggning minskar antalet gånger som en användare måste ange autentiseringsuppgifter.

Om du vill använda enkel inloggning, måste du ha:

- En app som är kodad för att leta efter användarens autentiseringsuppgifter lagrade i enkel inloggning på enheten.
- Intune måste ha konfigurerats för enkel inloggning för iOS-enheter.

![Fönstret Enkel inloggning](./media/sso-blade.png)

- **Användarnamnattribut från AAD**: Intune söker efter det här attributet för varje användare i Azure AD. Intune fyller sedan i respektive fält (till exempel UPN) innan XML som installeras på enheten genereras. Alternativen är:

  - **User Principal Name**: UPN parsas på följande sätt:

    ![Användarnamnattribut](media/User-name-attribute.png)

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

Klicka på **OK** för att spara ändringarna.

## <a name="web-content-filter-settings"></a>Inställningar för webbinnehållsfilter

Dessa inställningar styr webbläsarens URL-åtkomst på iOS-enheter.

- **Filtertyp**: Välj att tillåta vissa webbplatser. Alternativen är:

  - **Konfigurera URL:er**: Använd Apples inbyggda webbfilter som söker efter innehåll som är olämpligt för barn, inklusive svordomar och sexuellt explicit språk. Den här funktionen utvärderar varje webbsida som den har lästs in, och identifierar och blockerar olämpligt innehåll. Du kan också lägga till URL:er som du inte vill ska kontrolleras av filtret. Eller blockera specifika URL:er, oavsett inställningarna för Apple-filtret.

    - **Tillåtna webbadresser**: **Lägg till** de URL:er som du vill tillåta. Dessa URL:er kringgår Apple-webbfiltret.

      > [!NOTE]
        > URL:er som du anger är de URL:er som du inte vill ska utvärderas av Apple-webbfiltret. Dessa URL:er är inte en lista över tillåtna webbplatser. För att skapa en lista över tillåtna webbplatser ställer du in **Filtertyp** till **Endast vissa webbplatser**.

      Klicka på **OK** för att spara ändringarna.

    - **Blockerade URL:er**: **Lägg till** URL:er som du vill hindra från att öppnas, oavsett inställningarna i Apple-webbfiltret.

      Klicka på **OK** för att spara ändringarna.

  - **Endast vissa webbplatser** (endast för Safari-webbläsaren): Dessa webbadresser läggs till i Safari-webbläsarens bokmärken. Användaren är **endast** tillåten att besöka dessa webbplatser, inga andra platser kan öppnas. Använd bara det här alternativet om du vet den exakta listan över webbadresser som kan nås av användarna.

    - **URL**: Ange URL:en till den webbplats som du vill tillåta. Ange till exempel `https://www.contoso.com`.
    - **Bokmärkessökväg**: Ange sökvägen där du vill lagra bokmärket. Ange till exempel `/Contoso/Business Apps`. Om du inte lägger till någon sökväg läggs bokmärket till i standardmappen för bokmärken på enheten.
    - **Rubrik**: Ange en beskrivande rubrik för bokmärket.

    Om du inte anger några URL:er kommer användarna inte att komma åt några webbplatser förutom för `microsoft.com`, `microsoft.net` och `apple.com`. Dessa URL:er tillåts automatiskt av Intune.

    Klicka på **OK** för att spara ändringarna.

## <a name="wallpaper-settings"></a>Inställningar för bakgrundsbild

Lägg till en anpassad PNG-, JPG- eller JPEG-bild till övervakade iOS-enheter. Till exempel kan du använda en företagslogotyp på låsskärmen.

Ett oväntat beteende kan uppstå när en profil utan bild tilldelas till enheter med en befintlig bild. Exempel: Du skapar en profil utan någon bild. Profilen tilldelas till enheter som redan har en bild. I det här scenariot kan bilden ändras till enhetens standardinställda eller så kan den ursprungliga bilden stanna kvar på enheten. Det här beteendet styrs och begränsas av Apples MDM-plattform.

- **Plats för visning av bakgrundsbild**: Välj var på enheten som bilden ska visas. Alternativen är:
  - **Inte konfigurerad**: Ingen anpassad bild läggs till på enheten. Enheten använder standardoperativsystemet.
  - **Låsskärm**: Bilden läggs till på låsskärmen.
  - **Startsida**: Bilden läggs till på startsidan.
  - **Låsskärm och hemskärm**: Samma bild används på låsskärmen och startskärmen.
- **Bakgrundsbild**: Ladda upp en befintlig PNG-, JPG- eller JPEG-bild som du vill använda. Var noga med att filstorleken är mindre än 750 KB. Du kan också **ta bort** en bild som du har lagt till.

> [!TIP]
> För att visa olika bilder på låsskärmen och startsidan, skapa en profil med bilden för låsskärmen. Skapa en annan profil med bilden för startsidan. Tilldela båda profilerna till din iOS-användare eller dina enhetsgrupper.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa enhetsprofiler för [macOS](macos-device-features-settings.md)-enheter.
