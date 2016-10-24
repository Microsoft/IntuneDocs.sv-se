---
title: Omsluta iOS-appar med apphanteringsverktyget | Microsoft Intune
description: "Använd informationen i det här avsnittet för att lära dig hur du omsluter iOS-appar utan att ändra koden i själva appen. Förbered apparna så att du kan använda hanteringsprinciper för mobilprogram."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c67a5042fd177a4c5bd897092e84281db0977f5e
ms.openlocfilehash: 2c187b61b8fe25b2870d0cbc62f8352494583fc2


---

# Förbereda iOS-appar för hantering av mobilprogram med Intunes programhanteringsverktyg
Använd **Microsoft Intunes programhanteringsverktyg för iOS** för att ändra funktionssättet för interna iOS-appar genom att begränsa funktionerna i appen utan att ändra koden för själva appen.

Verktyget är ett kommandoradsprogram för Mac OS som skapar en omslutning runt en app. När en app har bearbetats kan du ändra appens funktioner med [Intunes hanteringsprinciper för mobilprogram](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) som du konfigurerar.

Om du vill ladda ned verktyget går du till [Microsoft Intunes appomslutningsverktyg för iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).



## Steg 1. Uppfyll nödvändiga krav för att använda appens wrap-verktyg
Läs [det här blogginlägget](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) om du vill veta mer om krav och hur du anger dem.

|Krav|Mer information|
|---------------|--------------------------------|
|Operativsystem och verktygsuppsättning som stöds|Du måste köra appomslutningsverktyget på en Mac OS-dator som kör OS X 10.8.5 eller senare och som har verktygsuppsättningen XCode version 5 eller senare installerad.|
|Signeringscertifikat och etableringsprofil|Du måste ha ett signeringscertifikat från Apple och en etableringsprofil. Mer information finns i [dokumentationen för Apple-utvecklare](https://developer.apple.com/).|
|Bearbeta en app med programhanteringsverktyget|Apparna måste vara utvecklade och signerade av ditt företag eller någon oberoende programvaruleverantör (ISV). Du kan inte använda verktyget för att bearbeta appar från Apple Store. Apparna måste vara skrivna för iOS 8.0 eller senare. Apparna måste också vara i formatet PIE (Position Independent Executable). Mer information om formatet PIE finns i dokumentationen för Apple-utvecklare. Slutligen måste appen ha filnamnstillägget **.app** eller **.ipa**.|
|Appar som programhanteringsverktyget inte kan bearbeta|Krypterade appar, osignerade appar och appar med utökade filattribut.|
|Ställa in rättigheter för din app|Du måste ställa in rättigheter, som ger appen ytterligare funktioner och behörigheter utöver de som vanligtvis beviljas, innan du omsluter appen. Anvisningar finns i [Ställa in apprättigheter](#setting-app-entitlements).|

## Steg 2. Installera app-wrapping-verktyget

1.  Från databasen **Microsoft Intunes appomslutningsverktyg för iOS** [på GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) hämtar du filerna för appomslutningsverktyget lokalt till en Mac OS-dator.

2.  Dubbelklicka på installationsfilen **Microsoft Intune App Wrapping Tool for iOS.dmg**. Ett fönster med licensavtalet för slutanvändare (EULA) visas. Läs igenom dokumentet noggrant.

3. Välj **Godkänn** för att godkänna licensavtalet och montera paketet på datorn.

4.  Öppna paketet **IntuneMAMPackager** och spara filerna till en lokal mapp på Mac OS-datorn. Nu kan du börja köra appomslutningsverktyget.

## Steg 3. Kör app-wrapping-verktyget
* På Mac OS-datorn öppnar du ett terminalfönster och går till den mapp där du sparade filerna för appomslutningsverktyget. Det körbara verktyget heter **IntuneMAMPackager** och finns i **IntuneMAMPackager/Contents/MacOS**. Du måste köra kommandot på följande sätt:

    ```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]

    ```

    > [!NOTE]
    > Vissa parametrar är valfria, vilket visas i tabellen nedan.

    **Exempel:** Följande exempelkommando kör programhanteringsverktyget i appen **MyApp.ipa**. En etableringsprofil och en SHA-1-hash anges. Den bearbetade appen skapas med namnet **MyApp_Wrapped.ipa** och lagras i användarens skrivbordsmapp.

    ```
    ./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true
    ```
    Du kan använda följande kommandoradsegenskaper med appen-wrapping-verktyget:

    |Egenskap|Använd så här|
  |------------|--------------------|
  |**-i**|`<Path of the input native iOS application file>`. Filnamnet måste sluta med .app eller .ipa. |
  |**-o**|`<Path of the wrapped output application>` |
  |**-p**|`<Path of your provisioning profile for iOS apps>`|
  |**-c**|`<SHA1 hash of the signing certificate>`|
    |-h|Visar detaljerad användningsinformation om tillgängliga kommandoradsegenskaper för appomslutningsverktyget.|
  |-v|(Valfritt men praktiskt) Skapar utförliga meddelanden för konsolen.|
  |-e | (Valfritt) Använd den här flaggan om du vill att appomslutningsverktyget ska ta bort rättigheter som saknas när den behandlar appen. Mer information finns i avsnittet "Ställa in apprättigheter".|
  |-xe| (Valfritt) Skriver ut information om iOS-tilläggen i programmet och vilka rättigheter som krävs för att använda dem. Mer information finns i avsnittet "Ställa in apprättigheter". |
  |-x| (Valfritt) `<An array of paths to extension provisioning profiles>`. Använd det här alternativet om appen behöver tilläggsetableringsprofiler.|
  |-f |(Valfritt) `<Path to a plist file specifying arguments.>` Använd den här flaggan framför filen [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) om du väljer att använda plist-mallen för att ange resten av IntuneMAMPackager-egenskaperna: -i, -o, -p osv. Mer information finns i avsnittet "Använda en plist för att ange argument". |
  |-b|(Valfritt) Använd -b utan argument om du vill att den omslutna utdataappen ska ha samma paketversion som indataappen (rekommenderas inte). <br/><br/> Använd `-b <custom bundle version>` om du vill att den omslutna appen ska ha en anpassad CFBundleVersion. Om du väljer att ange en anpassad CFBundleVersion rekommenderar vi att du ökar den inbyggda appens CFBundleVersion med den minst viktiga komponenten, t.ex. 1.0.0 -> 1.0.1. |


###Använda en plist för att ange argument
Ett enkelt sätt att köra appomslutningsverktyget är att placera alla kommandoradsargument i en [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html)-fil. Plist är ett filformat som liknar XML och det går att använda för att ange kommandoradsargument med ett formulärgränssnitt.

I mappen **IntuneMAMPackager/Contents/MacOS** öppnar du `Parameters.plist`, en tom plist-mall, med en textredigerare eller Xcode. Ange argumenten för följande nycklar:

| Plist-nyckel |  Standardvärde| Obs! |
|------------------|--------------|-----|
| Paketsökväg för indataapp  |tomt| Samma som -i. |
| Paketsökväg för utdataapp |tomt| Samma som -o.|
| Sökväg för etableringsprofil |tomt| Samma som -p. |
| SHA-1-certifikatets hash |tomt| Samma som -c. |
| Utförlig aktiverad |falskt| Samma som -v. |
| Ta bort rättigheter som saknas | falskt| Samma som -c.|
| Förhindra standardversion |falskt | Motsvarar att använda -b utan argument. |
|Åsidosättning av versionssträng | tomt| Anpassad CFBundleVersion för den omslutna utdataappen |
|Sökvägar för tilläggsetableringsprofil | tomt| En uppsättning med tilläggsetableringsprofiler för appen.
  

Kör slutligen IntuneMAMPackager med plist som enda argument:

```
./IntuneMAMPackager –f Parameters.plist
```

* När bearbetningen är klar visas meddelandet ”**Appen har omslutits**”.

    Om ett fel inträffar hittar du hjälp i [Felmeddelanden](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages).

*   Den omslutna appen sparas i den utdatamapp du har angett tidigare. Du kan ladda upp appen till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och koppla den till en princip för hantering av mobila appar.

    > [!IMPORTANT]
    > När du överför en omsluten app kan du försöka att uppdatera en äldre version av appen om en äldre version (omsluten eller intern) redan har distribuerats till Intune. Om det uppstår ett fel kan du ladda upp appen som en ny app och ta bort den äldre versionen.

    Nu kan du distribuera appen till dina [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-grupper, så körs appen på enheten med de begränsningar som du anger.

## Felmeddelanden och loggfiler
Använd följande information för att felsöka problem med programhanteringsverktyget.

### Felmeddelanden
Om det inte går att slutföra appomslutningsverktyget visas något av följande felmeddelanden i konsolen:

|Felmeddelande|Mer information|
|-----------------|--------------------|
|Du måste ange en giltig iOS-etableringsprofil.|Etableringsprofilen kanske inte är giltig. Kontrollera att du har rätt behörigheter för enheterna och att profilen är korrekt inställd på utveckling eller distribution. Etableringsprofilen kanske har löpt ut.|
|Ange ett giltigt namn för indataappen.|Kontrollera att namnet du har angett för indataappen är korrekt.|
|Ange en giltig sökväg till utdataappen.|Kontrollera att den sökväg till utdataappen du har angett verkligen finns och att den är korrekt.|
|Ange en giltig indataetableringsprofil.|Kontrollera att du har angett ett giltigt namn och filnamnstillägg för etableringsprofilen. Etableringsprofilen kanske saknar rättigheter eller så kanske du inte har lagt till kommandoradsalternativet **– p**.|
|Indataappen du angav hittades inte. Ange ett giltigt namn och giltig sökväg för indataappen.|Kontrollera att sökvägen till indataappen är giltig och finns. Kontrollera att indataappen finns där.|
|Den etableringsprofil du angav för indataappen hittades inte. Ange en giltig fil för indataetableringsprofilen.|Kontrollera att sökvägen till filen för indataetableringsprofilen är giltig och att den angivna filen finns.|
|Programmappen för den utdataapp du angav hittades inte. Ange en giltig sökväg till utdataappen.|Kontrollera att sökvägen för utdata är giltig och finns.|
|Utdataappen har inte filnamnstillägget .ipa.|Endast appar med filnamnstillägget **.app** och **.ipa** godkänns av appomslutningsverktyget. Kontrollera att utdatafilen har ett giltigt filnamnstillägg.|
|Ett ogiltigt signeringscertifikat har angetts. Ange ett giltigt signeringscertifikat för Apple.|Kontrollera att du har hämtat rätt signeringscertifikat från Apples utvecklarportal. Certifikatet kanske har löpt ut eller kanske saknar en offentlig eller privat nyckel. Om ditt Apple-certifikat och din etableringsprofil kan användas för att logga in på en app i Xcode på rätt sätt, är de också giltiga för appomslutningsverktyget.|
|Indataappen du har angett är ogiltig. Ange en giltig app.|Kontrollera att du har en giltig iOS-app som är kompilerad som en APP- eller IPA-fil.|
|Indataappen du har angett är krypterad. Ange en giltig okrypterad app.|Appomslutningsverktyget stöder inte krypterade appar. Ange en okrypterad app.|
|Den indataapp du angav har inte formatet PIE. Ange en giltig app i PIE-format.|PIE-appar kan läsas in på en slumpmässig minnesadress när de körs, vilket kan vara bra ur säkerhetssynpunkt. Mer information finns i Dokumentation för Apple-utvecklare.|
|Indataappen som du angav har redan omslutits. Ange en giltig okrypterad app.|Du kan inte bearbeta en app som redan har behandlats av verktyget. Om du vill bearbeta en app igen kör du verktyget med den ursprungliga versionen av appen.|
|Indataappen du angav har inte signerats. Ange en giltig signerad app.|Appomslutningsverktyget kräver att apparna signeras. Läs utvecklardokumentationen om du vill veta hur du signerar en omsluten app.|
|Indataappen du har angett måste vara i formatet IPA eller APP.|Endast appar med filnamnstilläggen APP och IPA godkänns av appomslutningsverktyget. Kontrollera att indatafilen har ett giltigt filnamnstillägg och har kompilerats som en APP- eller IPA-fil.|
|Indataappen som du angav är redan omsluten och har den senaste versionen av principmallen.|Appomslutningsverktyget kommer inte att omsluta en befintlig omsluten app igen med den senaste versionen av principmallen.|
|VARNING: Du har inte angett någon SHA1-certifikatshash. Kontrollera att den omslutna appen har signerats innan du distribuerar den.|Kontrollera att du har angett ett giltigt SHA1-hash-värde efter kommandoradsflaggan **–c**. |

### Loggfiler för appomslutningsverktyget
Appar som har varit omslutna med hjälp av appomslutningsverktyget genererar loggar som skrivs till iOS-klientenhetskonsolen. Den här informationen är användbar om du har problem med appen och behöver diagnostisera om problemet har att göra med appomslutningsverktyget. Använd följande steg för att hämta den här informationen:

1.  Återskapa problemet genom att köra appen.

2.  Samla in konsolens utdata genom att följa Apples instruktioner för att [felsöka distribuerade iOS-appar](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

3.  Filtrera de sparade loggarna för utdata från appbegränsningarna genom att ange följande skript i konsolen:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Du kan skicka de filtrerade loggarna till Microsoft.

    > [!NOTE]
    > I loggfilen representerar objektet 'build-version' Xcode-versionen.

    Omslutna appar kommer också att erbjuda användarna möjlighet att skicka loggarna direkt från enheten via e-post när appen kraschar. Användarna kan skicka loggar till dig så att du kan undersöka dem och vidarebefordra dem till Microsoft om det behövs.


### Certifikat, etableringsprofil och autentiseringskrav

Appomslutningsverktyget har vissa krav som måste uppfyllas för att garantera fullständiga funktioner.

|Krav|Information|
|---------------|-----------|
|Etableringsprofil|**Kontrollera att etableringsprofilen är giltig innan du lägger till den**. Appomslutningsverktyget kontrollerar inte om etableringsprofilen har upphört att gälla när en iOS-app bearbetas. Om en förfallen etableringsprofil har angetts tar programhanteringsverktyget med den förfallna etableringsprofilen och du märker inte att det är något problem förrän det visar sig att appen inte kan installeras på en iOS-enhet.|
|Certifikat|**Kontrollera att certifikatet är giltigt innan du anger det**. Verktyget kontrollerar inte om ett certifikat har upphört att gälla när iOS-appar bearbetas. Om hash-värdet för ett utgånget certifikat anges, behandlar verktyget appen och signerar den, men kommer inte att kunna installera den på enheterna.<br /><br />**Kontrollera att certifikatet som angavs för signering av den paketerade appen har en motsvarighet i etableringsprofilen**. Verktyget validerar inte om etableringsprofilen har en motsvarighet för det certifikat som angavs för signering av den omslutna appen.|
|Autentisering|En enhet måste ha en PIN-kod för att krypteringen ska fungera. På de enheter där du har distribuerat omslutna appar till måste användaren återautentisera med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] om statusfältet vidrörs. Standardprincipen i en omsluten app är *autentisering vid omstart*. iOS hanterar eventuella externa meddelanden (t.ex. ett telefonsamtal) genom att stänga appen och sedan starta om den.


## Ställa in apprättigheter
Innan du omsluter appen kan du bevilja **rättigheter** för att ge appen ytterligare behörigheter och funktioner som överskrider vad en app vanligtvis kan.  En **rättighetsfil** används under kodsignering för att ange särskilda behörigheter i appen (till exempel åtkomst till en delad nyckelring). Vissa apptjänster, som kallas **funktioner**, aktiveras i Xcode under apputvecklingen. När dessa funktioner har aktiverats visas de i din i din rättighetsfil. Mer information om rättigheter och funktioner finns i [Lägga till funktioner](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) i iOS Developer Library. En fullständig lista över funktioner som stöds finns i [Funktioner som stöds](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### Funktioner som stöds för programhanteringsverktyg för iOS

|Funktion|Beskrivning|Råd|
|--------------|---------------|------------------------|
|App-grupper|Använd appgrupper för att tillåta åtkomst för flera appar till delade behållare och tillåta ytterligare kommunikation mellan processer för olika appar.<br /><br />Om du vill aktivera appgrupper öppnar du fönstret **Funktioner** och klickar på växeln **PÅ** i avsnittet **App-grupper**. Du kan lägga till app-grupper eller välja befintliga.|Använd omvänd DNS-notering när du använder app-grupper:<br /><br />*group.com.companyName.AppGroup*|
|Bakgrundslägen|Genom att aktivera bakgrundslägen kan din iOS-app fortsätta köras i bakgrunden.||
|Dataskydd|Dataskydd lägger till en säkerhetsnivå för filer som lagras på disk av din iOS-app. Dataskydd utnyttjar den inbyggda krypteringsmaskinvarann som finns på vissa enheter för att lagra filer i krypterat format på disken. Din app behöver etableras om du vill använda dataskydd.||
|Köp via app|Köp i appen bäddar in en butik direkt i din app genom att göra det möjligt för dig att ansluta till butiken och på ett säkert sätt behandla betalningar från användaren. Du kan använda inköp i appen för att samla in betalning för utökad funktionalitet eller för ytterligare innehåll som kan användas med din app.||
|Nyckelringsdelning|Med aktivering av nyckelringsdelning kan din app dela lösenord i nyckelringen med andra appar som har utvecklats av ditt team.|Använd omvänd DNS-notering när du använder nyckelringsdelning:<br /><br />*com.companyName.KeychainGroup*|
|Personlig VPN|Du kan aktivera personlig VPN så att din app kan skapa och styra en anpassad system-VPN-konfiguration med hjälp av ramverket för nätverkstillägg||
|Push-meddelanden|Med hjälp av Apple Push Notification-tjänsten kan en app som inte körs i förgrunden meddela användaren om att den har information till användaren.|Du måste använda en app-specifik etableringsprofil för att push-meddelanden ska fungera.<br /><br />Följ anvisningarna i [dokumentationen för Apple-utvecklare](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Konfiguration för trådlösa tillbehör|Konfigurationen för att aktivera trådlösa tillbehör lägger till ramverket för externa tillbehör till ditt projekt och gör möjligt att konfigurera MFi Wi-Fi-tillbehör med din app.||

### Steg för att aktivera rättigheter

1.  Aktivera funktioner i din app:

    1.  Navigera till målet för appen i Xcode och klicka på fönstret **Funktioner**.

    2.  Aktivera lämpliga funktioner. Detaljerad information om varje funktion och hur du fastställer rätt värden finns i [Lägga till funktioner](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) i iOS Developer Library.

    3.  Notera eventuella ID:n som du skapade under processen.

    4.  Skapa och registrera den app som ska omslutas.

2.  Aktivera rättigheter i din etableringsprofil:

    1.  Logga in till Apple Developer Member Center.

    2.  Skapa en etableringsprofil för din app. Instruktioner finns i [Skaffa förutsättningarna för Intune-apphanteringsverktyget för iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/).

    3.  Aktivera samma rättigheter som du har i din app i din etableringsprofil. Du måste ange samma ID:n som du angav under utvecklingen av din app.

    4.  Slutför guiden för etableringsprofil och ladda ner filen.

3.  Kontrollera att du har uppfyllt alla krav och omslut därefter appen.

### Felsökning av vanliga fel med rättigheter
Prova följande felsökningssteg om programhanteringsverktyget för iOS rapporterar ett rättighetsfel.

|Problem|Orsak|Lösning|
|---------|---------|--------------|
|Det gick inte att parsa rättigheter som genererats av indataappen.|Programhanteringsverktyget kan inte läsa rättighetsfilen som har extraherats från appen. Rättighetsfilen kan vara felaktig.|Kontrollera rättighetsfilen för din app. Följ instruktionerna nedan. Sök efter felaktig syntax vid kontroll av rättighetsfilen. Filen bör vara i XML-format.|
|Rättigheter saknas i etableringsprofilen (saknade rättigheter anges i listan). Paketera om appen med en etableringsprofil som har dessa rättigheter.|Det finns ett matchningsfel mellan rättigheter aktiverade i etableringsprofilen och de funktioner som aktiverats i appen. Denna felmatchning gäller även de ID:n som  associeras med specifika funktioner (som appgrupper, nyckelringsåtkomst osv.).|I allmänhet kan du skapa en ny etableringsprofil som möjliggör samma funktioner som appen. När ID:n mellan profilen och appen inte matchar ersätter programhanteringsverktyget dessa ID:n om så är möjligt. Om det här felet fortfarande visas när du har skapat en ny etableringsprofil kan du prova att ta bort rättigheter från appen med hjälp av parametern **–e** (se avsnittet Använda parametern -e för att ta bort rättigheter från en app nedan).|

### Hitta befintliga rättigheter för en signerad app
Granska befintliga rättigheter för en signerad app och en etableringsprofil:

1.  Hitta .ipa-filen och ändra dess tillägg till .zip.

2.  Expandera .zip-filen. Detta genererar en nyttolast-mapp som innehåller ditt .app-paket.

3.  Använd codesign-verktyget  för att kontrollera rättigheterna i .app-paketet enligt följande:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```
    där `YourApp.app` är det faktiska namnet på .app-paketet.

4.  Använd säkerhetsverktyget för att kontrollera rättigheterna för appens inbäddade etableringsprofil:

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```
    där `YourApp.app` är det faktiska namnet på .app-paketet.

### Använda parametern -e för att ta bort rättigheter från en app)
Det här kommandot tar bort alla aktiverade funktioner i appen som inte ingår i rättighetsfilen. Om du tar bort funktioner som används av appen kan appen skadas. Ett exempel på då du kan ta bort funktioner som saknas är om du har en leverantörsutvecklad app där alla funktioner är standard.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## Säkerhet och sekretess för appomslutningsverktyget
Använd följande metodtips för säkerhet och sekretess när du använder appomslutningsverktyget.

-   Signeringscertifikatet, etableringsprofilen och affärsområdesappen du anger måste finnas på samma Mac OS-dator som den du använder för att appomslutningsverktyget ska kunna köras. Om filerna finns på en UNC-sökväg måste du kontrollera att de är tillgängliga från Mac OS-datorn. Sökvägen måste skyddas via IPsec- eller SMB-signering.

    Den omslutna appen importerats till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-konsolen bör vara på detsamma datorn som du körs verktyget på. Om filén finns på en UNC-sökväg, måste du kontrollera att det är tillgängligt på den dator som kör [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-konsolen. Sökvägen måste skyddas via IPsec- eller SMB-signering.

-   Miljön där appomslutningsverktyget hämtas från GitHub-databasen måste vara skyddad via IPsec eller SMB-signering.

-   Appen du bearbetar måste komma från en betrodd källa för att garantera skydd mot attacker.

-   Kontrollera att den utgående mappen du anger i appomslutningsverktyget är skyddad, särskilt om det är en fjärransluten mapp.

-   Med iOS-appar som innehåller en dialogruta för filöverföring kan användare kringgå de begränsningar för klipp ut, kopiera och klistra in som gäller för appen. En användare kan till exempel använda dialogrutan Överför för att överföra en skärmbild av appdata.

-   När användarna övervakar dokumentmappen på sina enheter inifrån appomslutningsverktyget, kan de se en mapp med namnet **.msftintuneapplauncher**. Om den här mappen ändras eller tas bort kan detta påverka funktionen hos appar med begränsningar.

### Se även
- [Förbereda appar för hantering av mobilprogram med Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Aktivera hantering av mobilprogram i appar med SDK](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Oct16_HO2-->


