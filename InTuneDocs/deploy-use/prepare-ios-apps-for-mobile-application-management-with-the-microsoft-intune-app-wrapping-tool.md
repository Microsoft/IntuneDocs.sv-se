---
title: Omsluta iOS-appar med Intunes programhanteringsverktyg | Microsoft Intune
description: "Använd informationen i det här avsnittet om du vill lära dig hur du omsluter dina iOS-appar utan att ändra koden i själva appen. Förbered apparna så att du kan använda hanteringsprinciper för mobilprogram."
keywords: 
author: mtillman
ms.author: mtillman
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
ms.sourcegitcommit: ee7e0491c0635c45cbc0377a5de01d5eba851132
ms.openlocfilehash: 0eee40c3c3c6bdfc3da2e715ef7b46e8408ba319


---

# <a name="prepare-ios-apps-for-mobile-application-management-with-the-intune-app-wrapping-tool"></a>Förbereda iOS-appar för hantering av mobilprogram med Intunes programhanteringsverktyg

Använd Microsoft Intunes programhanteringsverktyg för iOS om du vill ändra beteendet för interna iOS-appar genom att möjliggöra skyddsfuntionerna för Intune-appar utan att ändra koden i själva appen.

Verktyget är ett kommandoradsprogram för Mac OS som skapar en omslutning runt en app. När en app har bearbetats kan du ändra appens funktioner med [Intunes hanteringsprinciper för mobilprogram](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) utvecklad av IT-administratören.

Om du vill ladda ned verktyget går du till [Microsoft Intunes appomslutningsverktyg för iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) på GitHub.



## <a name="fulfill-the-prerequisites-for-the-app-wrapping-tool"></a>Kontrollera att du uppfyller kraven för programhanteringsverktyget
Se blogginlägget om [Hur du skaffar förutsättningar för Intunes programhanteringsverktyg för iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/) för att lära dig mer om hur du skaffar förutsättningarna.

|Krav|Mer information|
|---------------|--------------------------------|
|Operativsystem och verktygsuppsättning som stöds | Du måste köra programhanteringsverktyget på en Mac OS-dator som kör OS X 10.8.5 eller senare och som har verktygsuppsättningen XCode version 5 eller senare installerad.|
|Signeringscertifikat och etableringsprofil | Du måste ha ett signeringscertifikat från Apple och en etableringsprofil. Mer information finns i [dokumentationen för Apple-utvecklare](https://developer.apple.com/).|
|Bearbeta en app med programhanteringsverktyget  |Apparna måste vara utvecklade och signerade av ditt företag eller en oberoende programvaruleverantör (ISV). Du kan inte använda verktyget för att bearbeta appar från Apple Store. Apparna måste vara skrivna för iOS 8.0 eller senare. Apparna måste också vara i formatet PIE (Position Independent Executable). Mer information om PIE-formatet finns i dokumentationen för Apple-utvecklare. Slutligen måste appen ha filnamnstillägget **.app** eller **.ipa**.|
|Appar som verktyget inte kan bearbeta | Krypterade appar, osignerade appar och appar med utökade filattribut.|
|Ställa in rättigheter för din app|Innan du omsluter appen måste du ställa in rättigheter, som ger appen ytterligare funktioner och behörigheter utöver de som vanligtvis beviljas. Anvisningar finns i [Ställa in apprättigheter](#setting-app-entitlements).|

## <a name="install-the-app-wrapping-tool"></a>Installera App-Wrapping-verktyget

1.  Hämta filerna för programhanteringsverktyget från [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) till en macOS-dator.

2.  Dubbelklicka på **Microsoft Intune App Wrapping Tool for iOS.dmg**. Ett fönster med licensavtalet för slutanvändare (EULA) visas. Läs igenom dokumentet noggrant.

3. Välj **Godkänn** för att godkänna licensavtalet och montera paketet på datorn.

4.  Öppna mappen **IntuneMAMPackager** och spara innehållet på macOS-datorn. Nu kan du börja köra programhanteringsverktyget.

## <a name="run-the-app-wrapping-tool"></a>Kör App-Wrapping-verktyget

### <a name="use-terminal"></a>Använd terminal

Öppna macOS-terminalprogrammet och navigera till mappen där du sparade programhanteringsverktygets filer. Det körbara verktyget heter IntuneMAMPackager och finns i IntuneMAMPackager/Contents/MacOS. Kör kommandot så här:

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> Vissa parametrar är valfria, som du ser i följande tabell.

**Exempel:** Följande exempelkommando kör programhanteringsverktyget i appen MyApp.ipa. En etableringsprofil och en SHA-1-hash för signeringscertifikatet anges och används för att signera den omslutna appen. Utdata-appen (MyApp_Wrapped.ipa) skapas och lagras i mappen Skrivbord.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true
```

### <a name="command-line-parameters"></a>Kommandoradsparametrar
Du kan använda följande kommandoradsparametrar med programhanteringsverktyget:

|Egenskap|Använd så här|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`. Filnamnet måste sluta med .app eller .ipa. |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**|Visar detaljerad användningsinformation om tillgängliga kommandoradsegenskaper för programhanteringsverktyget.|
|**-v**|(Valfri) Returnerar utförliga meddelanden till konsolen.|
|**-e**| (Valfri) Använd den här flaggan om du vill att programhanteringsverktyget ska ta bort rättigheter som saknas när appen bearbetas. Mer information finns i Ställa in apprättigheter.|
|**-xe**| (Valfri) Skriver ut information om iOS-tilläggen i appen och vilka rättigheter som krävs för att använda dem. Mer information finns i Ställa in apprättigheter. |
|**-x**| (Valfritt) `<An array of paths to extension provisioning profiles>`. Använd det här alternativet om appen behöver tilläggsetableringsprofiler.|
|**-f**|(Valfri) `<Path to a plist file specifying arguments.>` Använd den här flaggan framför [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html)-filen om du väljer att använda plist-mallen för att ange resten av IntuneMAMPackager-egenskaperna, t.ex. -i, -o och -p. Mer information finns i Använda en plist för att ange argument. |
|**-b**|(Valfritt) Använd -b utan argument om du vill att den omslutna utdataappen ska ha samma paketversion som indataappen (rekommenderas inte). <br/><br/> Använd `-b <custom bundle version>` om du vill att den omslutna appen ska ha en anpassad CFBundleVersion. Om du väljer att ange en anpassad CFBundleVersion rekommenderar vi att du ökar den inbyggda appens CFBundleVersion med den minst viktiga komponenten, t.ex. 1.0.0 -> 1.0.1. |

### <a name="use-a-plist-to-input-arguments"></a>Använda en plist för att ange argument
Ett enkelt sätt att köra appomslutningsverktyget är att placera alla kommandoradsargument i en [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html)-fil. Plist är ett filformat som liknar XML som du kan använda för att ange kommandoradsargument med hjälp av ett formulärgränssnitt.

I mappen IntuneMAMPackager/Contents/MacOS öppnar du `Parameters.plist` (en tom plist-mall) med en textredigerare eller Xcode. Ange argumenten för följande nycklar:

| Plist-nyckel |  Standardvärde| Obs! |
|------------------|--------------|-----|
| Paketsökväg för indataapp  |tomt| Samma som -i|
| Paketsökväg för utdataapp |tomt| Samma som -o|
| Sökväg för etableringsprofil |tomt| Samma som -p|
| SHA-1-certifikatets hash |tomt| Samma som -c|
| Utförlig aktiverad |falskt| Samma som -v|
| Ta bort rättigheter som saknas | falskt| Samma som -c|
| Förhindra standardversion |falskt | Likvärdigt med att använda -b utan argument|
|Åsidosättning av versionssträng | tomt| Anpassad CFBundleVersion för den omslutna utdataappen |
|Sökvägar för tilläggsetableringsprofil | tomt| En uppsättning med tilläggsetableringsprofiler för appen.


Kör IntuneMAMPackager med plist som enda argument:

```bash
./IntuneMAMPackager –f Parameters.plist
```

### <a name="post-wrapping"></a>Efter omslutning

När omslutningen är klar visas meddelandet ”Appen har omslutits”. Om ett fel inträffar hittar du hjälp i [Felmeddelanden](#error-messages-and-log-files).

Den omslutna appen sparas i den utdatamapp du har angett tidigare. Du kan ladda upp appen till Intune-administratörskonsol och koppla den till en princip för hantering av mobila appar.

> [!IMPORTANT]
> När du överför en omsluten app kan du försöka att uppdatera en äldre version av appen om en äldre version (omsluten eller intern) redan har distribuerats till Intune. Om det uppstår ett fel kan du ladda upp appen som en ny app och ta bort den äldre versionen.

Du kan nu distribuera appen till användargrupper och ange programskyddsprinciper till appen. Appen körs på enheten med de programskyddsprinciper som du har angett.

## <a name="error-messages-and-log-files"></a>Felmeddelanden och loggfiler
Använd följande information för att felsöka problem med programhanteringsverktyget.

### <a name="error-messages"></a>Felmeddelanden
Om det inte går att slutföra programhanteringsverktyget visas något av följande felmeddelanden i konsolen:

|Felmeddelande|Mer information|
|-----------------|--------------------|
|Du måste ange en giltig iOS-etableringsprofil.|Etableringsprofilen kanske inte är giltig. Kontrollera att du har rätt behörigheter för enheterna och att profilen är korrekt inställd på utveckling eller distribution. Etableringsprofilen kanske har löpt ut.|
|Ange ett giltigt namn för indataappen.|Kontrollera att namnet du har angett för indataappen är korrekt.|
|Ange en giltig sökväg till utdataappen.|Kontrollera att den sökväg till utdataappen du har angett verkligen finns och att den är korrekt.|
|Ange en giltig indataetableringsprofil.|Kontrollera att du har angett ett giltigt namn och filnamnstillägg för etableringsprofilen. Etableringsprofilen kanske saknar rättigheter eller så kanske du inte har lagt till kommandoradsalternativet -p.|
|Indataappen du angav hittades inte. Ange ett giltigt namn och giltig sökväg för indataappen.|Kontrollera att sökvägen till indataappen är giltig och finns. Kontrollera att indataappen finns där.|
|Den etableringsprofil du angav för indataappen hittades inte. Ange en giltig fil för indataetableringsprofilen.|Kontrollera att sökvägen till filen för indataetableringsprofilen är giltig och att den angivna filen finns.|
|Programmappen för den utdataapp du angav hittades inte. Ange en giltig sökväg till utdataappen.|Kontrollera att sökvägen för utdata är giltig och finns.|
|Utdataappen har inte filnamnstillägget **.ipa**.|Endast appar med filnamnstillägget **.app** och **.ipa** godkänns av programhanteringsverktyget. Kontrollera att utdatafilen har ett giltigt filnamnstillägg.|
|Ett ogiltigt signeringscertifikat har angetts. Ange ett giltigt signeringscertifikat för Apple.|Kontrollera att du har hämtat rätt signeringscertifikat från Apples utvecklarportal. Certifikatet kanske har löpt ut eller kanske saknar en offentlig eller privat nyckel. Om ditt Apple-certifikat och etableringsprofilen kan användas för att signera en app i Xcode, så kan de också användas med programhanteringsverktyget.|
|Indataappen du har angett är ogiltig. Ange en giltig app.|Kontrollera att du har en giltig iOS-app som är kompilerad som en APP- eller IPA-fil.|
|Indataappen du har angett är krypterad. Ange en giltig okrypterad app.|Programhanteringsverktyget stöder inte krypterade appar. Ange en okrypterad app.|
|Den indataapp du angav har inte formatet PIE. Ange en giltig app i PIE-format.|PIE-appar (Position Independent Executable) kan läsas in på en slumpmässig minnesadress när de körs. Detta kan ha fördelar ur säkerhetssynpunkt. Mer information om säkerhetsrelaterade fördelar finns i dokumentationen för Apple-utvecklare.|
|Indataappen som du angav har redan omslutits. Ange en giltig okrypterad app.|Du kan inte bearbeta en app som redan har behandlats av verktyget. Om du vill bearbeta en app igen kör du verktyget med den ursprungliga versionen av appen.|
|Indataappen du angav har inte signerats. Ange en giltig signerad app.|Appomslutningsverktyget kräver att apparna signeras. Läs utvecklardokumentationen om du vill veta hur du signerar en omsluten app.|
|Indataappen du har angett måste vara i formatet IPA eller APP.|Endast appar med filnamnstilläggen APP och IPA godkänns av appomslutningsverktyget. Kontrollera att indatafilen har ett giltigt filnamnstillägg och har kompilerats som en APP- eller IPA-fil.|
|Indataappen som du angav är redan omsluten och har den senaste versionen av principmallen.|Programhanteringsverktyget omsluter inte en befintlig omsluten app igen med den senaste versionen av principmallen.|
|VARNING: Du har inte angett någon SHA1-certifikatshash. Kontrollera att den omslutna appen har signerats innan du distribuerar den.|Kontrollera att du har angett ett giltigt SHA1-hashvärde efter kommandoradsflaggan -c. |

### <a name="log-files-for-the-app-wrapping-tool"></a>Loggfiler för programhanteringsverktyget
Appar som har omslutits med hjälp av programhanteringsverktyget genererar loggar som skrivs till iOS-klientenhetskonsolen. Den här informationen är användbar om du har problem med appen och behöver fastställa om problemet har att göra med programhanteringsverktyget. Använd följande steg för att hämta den här informationen:

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


### <a name="certificate-provisioning-profile-and-authentication-requirements"></a>Certifikat, etableringsprofil och autentiseringskrav

Programhanteringsverktyget för iOS har vissa krav som måste uppfyllas för att säkerställa fullständig funktionalitet.

|Krav|Information|
|---------------|-----------|
|iOS-etableringsprofil|Kontrollera att etableringsprofilen är giltig innan du lägger till den. Programhanteringsverktyget kontrollerar inte om etableringsprofilen har gått ut när en iOS-app bearbetas. Om en förfallen etableringsprofil har angetts tar programhanteringsverktyget med den förfallna etableringsprofilen och du märker inte att det är något problem förrän det visar sig att appen inte kan installeras på en iOS-enhet.|
|iOS-signeringscertifikat|Kontrollera att signeringscertifikatet är giltigt innan du anger det. Verktyget kontrollerar inte om ett certifikat har upphört att gälla när iOS-appar bearbetas. Om hash-värdet för ett utgånget certifikat anges, behandlar verktyget appen och signerar den, men kommer inte att kunna installera den på enheterna.<br /><br />Kontrollera att certifikatet som angavs för signering av den omslutna appen har en motsvarighet i etableringsprofilen. Verktyget validerar inte om etableringsprofilen har en motsvarighet för det certifikat som angavs för signering av den omslutna appen.|
|Autentisering|En enhet måste ha en PIN-kod för att krypteringen ska fungera. På enheter där du har distribuerat en omsluten app måste användaren loggar in igen med ett arbets- eller skolkonto när hen trycker i statusfältet på enheten. Standardprincipen i en omsluten app är *autentisering vid omstart*. iOS hanterar externa meddelanden (till exempel ett telefonsamtal) genom att avsluta appen och sedan starta om den.


## <a name="setting-app-entitlements"></a>Ställa in apprättigheter
Innan du omsluter appen kan du bevilja *rättigheter* som ger appen ytterligare behörigheter och funktioner utöver vad en app vanligtvis kan göra. En *rättighetsfil* används under kodsignering för att ange särskilda behörigheter i appen (till exempel åtkomst till en delad nyckelring). Vissa apptjänster, kallade *funktioner*, aktiveras i Xcode under apputvecklingen. När dessa funktioner har aktiverats visas de i din i din rättighetsfil. Mer information om rättigheter och funktioner finns i [Lägga till funktioner](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) i iOS Developer Library. En fullständig lista över funktioner som stöds finns i [Funktioner som stöds](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### <a name="supported-capabilities-for-the-app-wrapping-tool-for-ios"></a>Funktioner som stöds för programhanteringsverktyg för iOS

|Funktion|Beskrivning|Råd|
|--------------|---------------|------------------------|
|Appgrupper|Använd appgrupper om du vill ge flera appar åtkomst till delade behållare och tillåta ytterligare kommunikation mellan processer för olika appar.<br /><br />Om du vill aktivera appgrupper öppnar du rutan **Funktioner** och klickar på **PÅ** i **Appgrupper**. Du kan lägga till app-grupper eller välja befintliga.|Använd omvänd DNS-notering när du använder app-grupper:<br /><br />*group.com.companyName.AppGroup*|
|Bakgrundslägen|Om du aktiverar bakgrundslägen kan din iOS-app fortsätta att köras i bakgrunden.||
|Dataskydd|Dataskydd lägger till en säkerhetsnivå för filer som lagras på disk av din iOS-app. Dataskydd utnyttjar den inbyggda krypteringsmaskinvarann som finns på vissa enheter för att lagra filer i krypterat format på disken. Din app behöver etableras om du vill använda dataskydd.||
|Köp via app|Köp via app bäddar in en butik direkt i din app på ett sätt som gör att du kan ansluta till butiken och behandla betalningar från användaren med hög säkerhet. Du kan använda funktionen Köp via app för att ta betalt för utökade funktioner eller för ytterligare innehåll som kan användas med din app.||
|Nyckelringsdelning|Om du aktiverar nyckelringsdelning kan din app dela lösenord i nyckelringen med andra appar som har utvecklats av ditt team.|Använd omvänd DNS-notering när du använder nyckelringsdelning:<br /><br />*com.companyName.KeychainGroup*|
|Personlig VPN|Du kan aktivera personlig VPN så att din app kan skapa och styra en anpassad system-VPN-konfiguration med hjälp av ramverket för nätverkstillägg||
|Push-meddelanden|Med hjälp av Apple Push Notification Service (APNS) kan en app som inte körs i förgrunden meddela användaren att den har information till användaren.|Du måste använda en app-specifik etableringsprofil för att push-meddelanden ska fungera.<br /><br />Följ anvisningarna i [dokumentationen för Apple-utvecklare](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Konfiguration för trådlösa tillbehör|Om du aktiverar konfiguration för trådlösa tillbehör läggs ramverket för externa tillbehör till i ditt projekt så att du kan konfigurera MFi Wi-Fi-tillbehör med din app.||

### <a name="steps-to-enable-entitlements"></a>Steg för att aktivera rättigheter

1.  Aktivera funktioner i din app:

    a.  Gå till målet för din app i Xcode och klicka på **Funktioner**.

    b.  Aktivera lämpliga funktioner. Detaljerad information om varje funktion och hur du fastställer rätt värden finns i [Lägga till funktioner](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) i iOS Developer Library.

    c.  Notera eventuella ID:n som du skapade under processen.

    d.  Skapa och registrera den app som ska omslutas.

2.  Aktivera rättigheter i din etableringsprofil:

    a.  Logga in på Apple Developer Member Center.

    b.  Skapa en etableringsprofil för din app. Instruktioner finns i [Skaffa förutsättningarna för Intune-apphanteringsverktyget för iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/).

    c.  Aktivera samma rättigheter som du har i din app i din etableringsprofil. Du måste ange samma ID:n som du angav under utvecklingen av din app.

    d.  Slutför guiden för etableringsprofiler och ladda ner filen.

3.  Kontrollera att du har uppfyllt alla krav och omslut därefter appen.

### <a name="troubleshoot-common-errors-with-entitlements"></a>Felsökning av vanliga fel med rättigheter
Prova följande felsökningssteg om programhanteringsverktyget för iOS rapporterar ett rättighetsfel.

|Problem|Orsak|Lösning|
|---------|---------|--------------|
|Det gick inte att parsa rättigheter som genererats av indataappen.|Programhanteringsverktyget kan inte läsa rättighetsfilen som har extraherats från appen. Rättighetsfilen kan vara felaktig.|Kontrollera rättighetsfilen för din app. Följande anvisningar beskriver hur du gör. Sök efter felaktig syntax vid kontroll av rättighetsfilen. Filen bör vara i XML-format.|
|Rättigheter saknas i etableringsprofilen (saknade rättigheter anges i listan). Paketera om appen med en etableringsprofil som har dessa rättigheter.|Det finns ett matchningsfel mellan rättigheter aktiverade i etableringsprofilen och de funktioner som aktiverats i appen. Denna felmatchning gäller även de ID:n som associeras med specifika funktioner (som appgrupper och nyckelringsåtkomst).|I allmänhet kan du skapa en ny etableringsprofil som möjliggör samma funktioner som appen. När ID:n mellan profilen och appen inte matchar ersätter programhanteringsverktyget dessa ID:n om så är möjligt. Om felet fortfarande visas när du har skapat en ny etableringsprofil kan du prova att ta bort rättigheter från appen med hjälp av parametern -e (se avsnittet Använda parametern -e för att ta bort rättigheter från en app).|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>Hitta befintliga rättigheter för en signerad app
Granska befintliga rättigheter för en signerad app och en etableringsprofil:

1.  Hitta .ipa-filen och ändra dess tillägg till .zip.

2.  Expandera .zip-filen. Detta genererar en nyttolast-mapp som innehåller ditt .app-paket.

3.  Använd codesign-verktyget för att kontrollera rättigheterna för .app-paketet, där `YourApp.app` är namnet på .app-paketet:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4.  Använd säkerhetsverktyget för att kontrollera rättigheterna för appens inbäddade etableringsprofil, där `YourApp.app` är namnet på .app-paketet.

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>Ta bort rättigheter från en app med hjälp av parametern -e
Det här kommandot tar bort alla aktiverade funktioner i appen som inte ingår i rättighetsfilen. Om du tar bort funktioner som används av appen kan appen skadas. Ett exempel på när du kan ta bort funktioner som saknas är om du har en leverantörsutvecklad app där alla funktioner är standard.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>Säkerhet och sekretess för programhanteringsverktyget
Använd följande riktlinjer för säkerhet och sekretess när du använder programhanteringsverktyget.

-   Signeringscertifikatet, etableringsprofilen och affärsappen som du anger måste finnas på samma Mac OS-dator som den som du använder för att köra programhanteringsverktyget. Om filerna finns på en UNC-sökväg kontrollerar du att de är tillgängliga från Mac OS-datorn. Sökvägen måste skyddas via IPsec- eller SMB-signering.

    Den omslutna appen importerats till administratörskonsolen bör vara på detsamma datorn som du körs verktyget på. Om filén finns på en UNC-sökväg, måste du kontrollera att det är tillgängligt på den dator som kör administratörskonsolen. Sökvägen måste skyddas via IPsec- eller SMB-signering.

-   Miljön där programhanteringsverktyget hämtas från GitHub-databasen måste vara skyddad med IPsec eller SMB-signering.

-   Appen du bearbetar måste komma från en betrodd källa för att garantera skydd mot attacker.

-   Kontrollera att den utgående mappen som du anger i programhanteringsverktyget är skyddad, särskilt om det är en fjärransluten mapp.

-   Med iOS-appar som innehåller en dialogruta för filöverföring kan användarna kringgå de begränsningar för klipp ut, kopiera och klistra in som gäller för appen. En användare kan till exempel använda dialogrutan Överför för att överföra en skärmbild av appdata.

-   När du övervakar dokumentmappen på enheten från en omsluten app kan du se en mapp med namnet .msftintuneapplauncher. Om du ändrar eller tar bort den här filen kan det resulterade i att begränsade appar inte fungerar som de ska.

### <a name="see-also"></a>Se även
- [Förbereda appar för hantering av mobilprogram med Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Aktivera hantering av mobilprogram i appar med SDK](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Dec16_HO2-->


