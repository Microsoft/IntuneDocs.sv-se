---
title: Funktionsinställningar för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se alla inställningar för att konfigurera iOS-enheter för AirPrint, layout för startsidan, appmeddelanden, delad enhet, enkel inloggning och webbinnehållsfilter i Microsoft Intune. Använd dessa inställningar i en enhetskonfigurationsprofil när du konfigurerar iOS-enheter för att använda de olika Apple-funktionerna i din organisation.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/30/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a2acd4e54329dbfd43e468a3a0f3b1fa62eee44
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850113"
---
# <a name="ios-device-feature-settings-in-intune"></a>Funktionsinställningar för iOS-enheter i Intune

Intune innehåller vissa inbyggda inställningar för att tillåta iOS-användare att använda olika Apple-funktioner på sina enheter. Till exempel så kan administratörer styra hur iOS-användare använder AirPrint-skrivare, lägga till appar och mappar till dockan och sidor på startskärmen, visa meddelanden i appen, visa information om tillgångstagg på låsskärmen, använda enkel inloggning och autentisera användare med certifikat.

I den här artikeln visas inställningarna, tillsammans med en beskrivning av vad varje inställning gör.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en iOS-enhetskonfigurationsprofil](device-features-configure.md#create-a-device-profile).

## <a name="airprint-settings"></a>AirPrint-inställningar

Den här funktionen tillåter iOS-användare att skriva ut till kända AirPrint-skrivare.

1. I **Inställningar** väljer du **AirPrint**. Ange följande egenskaper för AirPrint-servern:

    - **IP-adress**: Ange skrivarens IPv4- eller IPv6-adress. Om du använder värdnamn till att identifiera skrivare, kan du hämta IP-adressen genom att pinga skrivaren i terminalen. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
    - **Sökväg**: Sökvägen är vanligtvis `ipp/print` för skrivare i nätverket. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
    - **Port**: Ange lyssningsporten för AirPrint-målet. Om du lämnar den här egenskapen tom, kommer AirPrint att använda standardporten. Tillgängligt i iOS 11.0 och senare.
    - **TLS**: Välj **Aktivera** för att skydda AirPrint-anslutningar med TLS (Transport Layer Security). Tillgängligt i iOS 11.0 och senare.

2. Välj **Lägg till**. AirPrint-servern läggs till i listan. Du kan lägga till flera AirPrint-servrar.

    Du kan också **Importera** en kommaavgränsad fil (CSV) med den här informationen. När du har skapat listan, kan du också **Exportera** din lista över AirPrint-servrar.

3. När du är klar väljer du **OK** för att spara listan.

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

1. I **Inställningar** väljer du **Hemskärmslayout (endast övervakat)** > **Docka** > **Lägg till**. Du kan lägga till upp till **sex** objekt (appar och mappar som kombineras) för enhetens docka.
2. I **Typ**, väljer du att lägga till en **App** eller en **Mapp**.

    - **Lägga till en app**: Välj det här alternativet för att lägga till appar i dockan på skärmen. Ange:

      - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
      - **Appsamlings-ID**: Ange appens samlings-ID. Se [Samlings-ID för inbyggda iOS-appar](#bundle-ids-for-built-in-ios-apps) (i den här artikeln) för några exempel.

      Klicka på **OK** för att spara ändringarna.

    - **Lägg till en mapp**: Välj det här alternativet för att lägga till en mapp i dockan på skärmen. 

      Apparna som du lägger till på en sida i en mapp ordnas från vänster till höger, och i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

      1. Ange ett **Mappnamn**. Namnet visas för användare på deras enhet.
      2. Välj **Lägg till** och ange följande egenskaper:

          - **Sidnamn**: Ange ett namn för sidan. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
          - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
          - **Appsamlings-ID**: Ange appens samlings-ID. Se [Samlings-ID för inbyggda iOS-appar](#bundle-ids-for-built-in-ios-apps) (i den här artikeln) för några exempel.

      3. Välj **Lägg till**. Du kan lägga till upp till **20** sidor för enhetsdockan.
      4. Klicka på **OK** för att spara ändringarna.

#### <a name="example"></a>Exempel

I följande exempel visar skärmen dock endast apparna Safari, Mail och Stocks. Mail-appen är markerad för att visa dess egenskaper:

![Exempel på iOS-dockningsinställningar](./media/FfFiUcP.png)

När du tilldelar principen till en iPhone liknar dockan följande bild:

![Exempel på iOS-dockningslayout i iPhone](./media/bAgCe8F.png)

### <a name="pages"></a>Sidor

Lägg till de sidor som du vill ska visas på startskärmen, samt de appar som du vill ska visas på varje sida. Apparna som du lägger till på en sida ordnas från vänster till höger, i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

> [!TIP]
> För att ändra om objekt på startskärmen och sidlistor kan du dra och släppa dem.

1. I **Inställningar** väljer du **Hemskärmslayout (endast övervakat)** > **Sidor** > **Lägg till**. Du kan lägga till upp till **40** sidor på en enhet.
2. Ange ett **Sidnamn**. Det här namnet används som din referens i Azure-portalen och visas *inte* på iOS-enheten. 

    Välj **Lägg till**. Du kan lägga till upp till **60** objekt (appar och mappar kombinerat) på en enhet.

3. I **Typ**, väljer du att lägga till en **App** eller en **Mapp**.

    - **Lägga till en app**: Välj det här alternativet för att lägga till appar på en sida på skärmen. Ange:

      - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
      - **Appsamlings-ID**: Ange appens samlings-ID. Se [Samlings-ID för inbyggda iOS-appar](#bundle-ids-for-built-in-ios-apps) (i den här artikeln) för några exempel.

      Klicka på **OK** för att spara ändringarna.

    - **Lägg till en mapp**: Välj det här alternativet för att lägga till en mapp i dockan på skärmen. 

      Apparna som du lägger till på en sida i en mapp ordnas från vänster till höger, och i samma ordning som i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en annan sida.

      1. Ange ett **Mappnamn**. Namnet visas för användare på deras enhet.
      2. Välj **Lägg till** och ange följande egenskaper:

          - **Sidnamn**: Ange ett namn för sidan. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
          - **Appnamn**: Ange ett namn för appen. Det här namnet används som din referens i Azure Portal. Det visas *inte* på iOS-enheten.
          - **Appsamlings-ID**: Ange appens samlings-ID. Se [Samlings-ID för inbyggda iOS-appar](#bundle-ids-for-built-in-ios-apps) (i den här artikeln) för några exempel.

      3. Välj **Lägg till**.
      4. Klicka på **OK** för att spara ändringarna.

#### <a name="example"></a>Exempel

I följande exempel har en ny sida med namnet **Contoso** lagts till. Sidan visar apparna Hitta vänner och Inställningar. Inställningsappen är markerad för att visa dess egenskaper:

![Exempel på inställningar på iOS-startskärmen](./media/Jc2OxyX.png)

När du tilldelar principen till en iPhone liknar sidan följande bild:

![iOS-enhet med ändrad startskärm](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>Inställningar för appmeddelanden

Välj hur installerade appar på iOS-enheter skickar meddelanden. Inställningarna har stöd för övervakade enheter som kör iOS 9.3 och senare.

1. I **Inställningar** väljer du **Appmeddelanden (endast övervakat)** > **Lägg till**:

    ![Lägg till appmeddelande i en iOS-profil i Intune](./media/ios-macos-app-notifications.png)

2. Ange följande egenskaper:

    - **Appsamlings-ID**: Ange **Appsamlings-ID** för den app som du vill lägga till. Se [Samlings-ID för inbyggda iOS-appar](#bundle-ids-for-built-in-ios-apps) (i den här artikeln) för några exempel.
    - **Appnamn**: Ange namnet på appen som du vill lägga till. Det här namnet används som din referens i Azure Portal. Det visas *inte* på enheten.
    - **Utgivare**: Ange utgivaren av den app som du vill lägga till. Det här namnet används som din referens i Azure Portal. Det visas *inte* på enheten.
    - **Meddelanden**: **Aktivera** eller **inaktivera** att appen kan skicka meddelanden till enheten.
       - **Visa i meddelandecenter**: **Aktivera** tillåter appen att visa meddelanden i enhetens meddelandecenter. **Inaktivera** förhindrar att appen visar meddelanden i meddelandecentret.
       - **Visa på Låsskärm**: Välj **Aktivera** för att visa aviseringar från appen på enhetens låsskärm. **Inaktivera** förhindrar att appen visar meddelanden på låsskärmen.
       - **Typ av avisering**: När enheten är upplåst kan du välja hur meddelandet visas. Alternativen är:
         - **Inga**: Inga meddelanden visas.
         - **Banderoll**: En banderoll visas en kort stund med meddelandet.
         - **Modal**: Meddelandet visas och användaren måste manuellt ta bort det innan hen fortsätter att använda enheten.
       - **Aktivitetsikon på appikon**: Välj **Aktivera** för att lägga till en aktivitetsikon på appikonen. Aktivitetsikonen innebär att appen skickat en avisering.
       - **Ljud**: Välj **Aktivera** för att spela upp ett ljud när en avisering tas emot.

3. Klicka på **OK** för att spara ändringarna. Fortsätt lägga till de appar du önskar. När du är klar väljer du **OK**.

## <a name="lock-screen-message-settings"></a>Inställningar för meddelande på låsskärm

Använd de här inställningarna för att visa ett anpassat meddelande eller text i inloggningsfönstret och på låsskärmen. Du kan till exempel skriva ett meddelande av typen ”Upphittad enhet återlämnas till...” och resurstagginformation. 

Den här funktionen stöder övervakade enheter som kör:

- iOS 9.3 och senare

1. I **Inställningar** väljer du **Meddelande på låsskärm (endast övervakat)**.
2. Ange följande inställningar:

    - **Resurstagginformation**: Ange information om resurstaggen för enheten. Ange till exempel `Owned by Contoso Corp` eller `Serial Number: {{serialnumber}}`. 

      Den text du anger visas i inloggningsfönstret och på låsskärmen på enheten.

    - **Fotnot på låsskärmen**: Ange en kommentar som kan hjälpa dig att få tillbaka enheten om den tappas bort eller blir stulen. Du kan ange valfri text. Ange något i stil med `If found, call Contoso at ...`.

    Enhetstoken kan också användas för att lägga till enhetsspecifik information i de här fälten. Ange till exempel `Serial Number: {{serialnumber}}` om du vill visa serienumret. På låsskärmen visas texten ungefär som `Serial Number 123456789ABC`. När du anger variabler ska du använda klammerparenteser `{{ }}`. [Token för appkonfiguration](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) innehåller en lista över variabler som kan användas. Du kan också använda `deviceName` eller andra enhetsspecifika värden.

    > [!NOTE]
    > Variabler verifieras inte i användargränssnittet. Därför kan du se profiler sparade med felaktiga indata. Om du till exempel anger `{{Devicename}}` istället för `{{devicename}}` visas litteralsträngen istället för enhetens unika namn.

3. När du är klar väljer du **OK** för att spara ändringarna.

## <a name="single-sign-on-settings"></a>Inställningar för enkel inloggning

De flesta verksamhetsspecifika appar kräver av säkerhetsskäl någon nivå av användarautentisering. I många fall kräver den här autentiseringen att användaren anger samma autentiseringsuppgifter upprepade gånger, vilket är frustrerande för användaren. För att förbättra användarupplevelsen kan utvecklare skapa appar som använder enkel inloggning (SSO). Med enkel inloggning minskar antalet gånger som en användare måste ange autentiseringsuppgifter.

Om du vill använda enkel inloggning, måste du ha:

- En app som är kodad för att leta efter användarens autentiseringsuppgifter lagrade i enkel inloggning på enheten.
- Intune måste ha konfigurerats för enkel inloggning för iOS-enheter.

1. I **Inställningar** väljer du **Enkel inloggning**:

   ![Fönstret Enkel inloggning](./media/sso-blade.png)

2. Ange följande inställningar:

    - **Användarnamnattribut från AAD**: Intune söker efter det här attributet för varje användare i Azure Active Directory. Intune fyller sedan i respektive fält (till exempel UPN) innan XML som installeras på enheten genereras. Alternativen är:

      - **Användarens huvudnamn (UPN)**: UPN parsas på följande sätt:

        ![Användarnamnattribut](media/User-name-attribute.png)

        Du kan också skriva över området med texten som du anger i textrutan **Område**.

        Contoso har exempelvis flera regioner, inklusive Europa, Asien och Nordamerika. Contoso vill att Asien-användarna ska använda enkel inloggning och appen kräver UPN i `username@asia.contoso.com`-formatet. När du väljer **UPN**, tas sfären för varje användare från Azure Active Directory, som är `contoso.com`. För användare i Asien, markerar du **UPN** och anger `asia.contoso.com`. Nu blir slutanvändarens UPN `username@asia.contoso.com` i stället för `username@contoso.com`.

      - **ID för Intune-enhet**: Intune väljer automatiskt ID:t för Intune-enheten.

        Som standard behöver appar bara använda enhets-ID. Men om din app använder sfären och enhets-ID:t kan du skriva sfären i textrutan Sfär.

        > [!NOTE]
        > Som standard bör du lämna området tomt om du använder enhets-ID.

      - **Enhets-ID för Azure Active Directory**

    - **Sfär**: Ange domändelen av URL:en. Ange till exempel `contoso.com`.
    - **URL-prefix som används för enkel inloggning**: **Lägg till** URL:er i din organisation som kräver användarautentisering med enkel inloggning.

        När en användare exempelvis ansluter till någon av dessa platser använder iOS-enheten autentiseringsuppgifterna för enkel inloggning. Användaren behöver inte ange ytterligare autentiseringsuppgifter. Om multifaktorautentisering är aktiverat måste användarna ange en autentisering till.

        > [!NOTE]
        > Dessa URL:er måste vara ett fullständigt domännamn i korrekt format. Apple kräver att dessa ska vara i formatet `http://<yourURL.domain>`.

        Mönster för URL-matchning måste börja med antingen `http://` eller `https://`. En enkel strängmatchning körs, så URL-prefixet `http://www.contoso.com/` matchar inte `http://www.contoso.com:80/`. Om du har iOS 10.0 eller senare kan ett enskilt jokertecken \* användas för att ange alla matchande värden. `http://*.contoso.com/` matchar till exempel både `http://store.contoso.com/` och `http://www.contoso.com`.

        Mönstren `http://.com` och `https://.com` matchar alla HTTP- respektive HTTPS-adresser.

    - **Appar som ska använda enkel inloggning**: **Lägg till** appar på slutanvändarnas enheter som kan använda enkel inloggning.

        Matrisen `AppIdentifierMatches` måste innehålla strängar som matchar appsamlings-ID:n. Dessa strängar kan vara exakta matchningar, till exempel `com.contoso.myapp`, eller så anger du en prefixmatchning för paket-ID:t med jokertecknet \*. Jokertecknet måste komma efter en punkt (.), och får bara förekomma en gång, i slutet av strängen såsom `com.contoso.*`. När ett jokertecken används beviljas alla appar vars samlings-ID börjar med prefixet åtkomst till kontot.

        Använd **appnamn** för att ange ett användarvänligt namn som hjälper dig att identifiera paket-ID:t.

    - **Förnyelsecertifikat för autentiseringsuppgifter**: Om du använder certifikat för autentisering (inte lösenord), väljer du det befintliga SCEP- eller PFX-certifikatet som autentiseringscertifikat. Vanligtvis är det här certifikatet samma certifikat som distribueras till användaren för andra profiler, till exempel VPN, WiFi eller e-post.

3. När du är klar väljer du **OK** för att spara ändringarna.

## <a name="web-content-filter-settings"></a>Inställningar för webbinnehållsfilter

Dessa inställningar styr webbläsarens URL-åtkomst på iOS-enheter.

1. I **Inställningar** väljer du **Webbinnehållsfilter (endast övervakat)**.
2. Välj **Filtertyp**. Alternativen är:

    - **Konfigurera webbadresser**: Använd Apples inbyggda webbfilter som söker efter innehåll som är olämpligt för barn, inklusive svordomar och sexuellt explicit språk. Den här funktionen utvärderar varje webbsida som den har lästs in, och identifierar och blockerar olämpligt innehåll. Du kan också lägga till URL:er som du inte vill ska kontrolleras av filtret. Eller blockera specifika URL:er, oavsett inställningarna för Apple-filtret.

      - **Tillåtna webbadresser**: **Lägg till** URL:er som du vill tillåta. Dessa URL:er kringgår Apple-webbfiltret.

        > [!NOTE]
        > URL:er som du anger är de URL:er som du inte vill ska utvärderas av Apple-webbfiltret. Dessa URL:er är inte en lista över tillåtna webbplatser. För att skapa en lista över tillåtna webbplatser ställer du in **Filtertyp** till **Endast vissa webbplatser**.

        Klicka på **OK** för att spara ändringarna.

      - **Blockerade URL:er**: **Lägg till** URL:er som du vill stoppa från att öppnas, oavsett inställningarna i Apple-webbfiltret.

        Klicka på **OK** för att spara ändringarna.

    - **Endast vissa webbplatser** (för Safari-webbläsaren endast): Dessa URL:er har lagts till i Safari-webbläsarens bokmärken. Användaren är **endast** tillåten att besöka dessa webbplatser, inga andra platser kan öppnas. Använd bara det här alternativet om du vet den exakta listan över webbadresser som kan nås av användarna.

      - **URL**: Ange URL:en till den webbplats som du vill tillåta. Ange till exempel `https://www.contoso.com`.
      - **Bokmärkessökväg**: Ange sökvägen för att lagra bokmärket. Ange till exempel `/Contoso/Business Apps`. Om du inte lägger till någon sökväg läggs bokmärket till i standardmappen för bokmärken på enheten.
      - **Rubrik**: Ange en beskrivande rubrik för bokmärket.

      Om du inte anger några URL:er kommer användarna inte att komma åt några webbplatser förutom för `microsoft.com`, `microsoft.net` och `apple.com`. Dessa URL:er tillåts automatiskt av Intune.

      Klicka på **OK** för att spara ändringarna.

## <a name="wallpaper-settings"></a>Inställningar för bakgrundsbild

Lägg till en anpassad PNG-, JPG- eller JPEG-bild till övervakade iOS-enheter. Till exempel kan du använda en företagslogotyp på låsskärmen.

Ett oväntat beteende kan uppstå när en profil utan bild tilldelas till enheter med en befintlig bild. Exempel: Du skapar en profil utan någon bild. Profilen tilldelas till enheter som redan har en bild. I det här scenariot kan bilden ändras till enhetens standardinställda eller så kan den ursprungliga bilden stanna kvar på enheten. Det här beteendet styrs och begränsas av Apples MDM-plattform.

- **Plats för visning av bakgrundsbild**: Välj en plats på enheten för att visa bilden. Alternativen är:
  - **Inte konfigurerad**: En anpassad bild inte har lagts till på enheten. Enheten använder standardoperativsystemet.
  - **Låsskärm**: Lägger till bilden till låsskärmen.
  - **Startsida**: Lägger till bilden till startsidan.
  - **Låsskärm och startskärm**: Använder samma bild på låsskärmen och startskärmen.
- **Bakgrundsbild**: Ladda upp en befintlig PNG-, JPG- eller JPEG-bild som du vill använda. Var noga med att filstorleken är mindre än 750 KB. Du kan också **ta bort** en bild som du har lagt till.

> [!TIP]
> För att visa olika bilder på låsskärmen och startsidan, skapa en profil med bilden för låsskärmen. Skapa en annan profil med bilden för startsidan. Tilldela båda profilerna till din iOS-användare eller dina enhetsgrupper.

## <a name="bundle-ids-for-built-in-ios-apps"></a>Samlings-ID för inbyggda iOS-appar

I följande lista visas appsamlings-ID:n för några vanliga inbyggda iOS-appar. Kontakta programvaruleverantören för att hitta appsamlings-ID:n för andra appar.

|||
|-|-|
|Appnamn|Appsamlings-ID|
|Appbutik|com.apple.AppStore|
|Kalkylator|com.apple.calculator|
|Kalender|com.apple.mobilecal|
|Kamera|com.apple.camera|
|Klocka|com.apple.mobiletimer|
|Kompass|com.apple.compass|
|Kontakter|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Hitta vänner|com.apple.mobileme.fmf1|
|Hitta iPhone|com.apple.mobileme.fmip1|
|Spelcenter|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Hälsa|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|E-post|com.apple.mobilemail|
|Kartor|com.apple.Maps|
|Meddelanden|com.apple.MobileSMS|
|Musik|com.apple.Music|
|Nyheter|com.apple.news|
|Obs!|com.apple.mobilenotes|
|Siffror|com.apple.Numbers|
|Sidor|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Foton|com.apple.mobileslideshow|
|Poddsändningar|com.apple.podcasts|
|Påminnelser|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Inställningar|com.apple.Preferences|
|Aktier|com.apple.stocks|
|Tips|com.apple.tips|
|Videor|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Plånbok|com.apple.Passbook|
|Titta på|com.apple.Bridge|
|Väder|com.apple.weather|

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa enhetsprofiler för [macOS](macos-device-features-settings.md)-enheter.
