---
# required metadata

title: Förbereda iOS-appar för hantering med programhanteringsverktyget | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Förbereda iOS-appar för hantering av mobilprogram med Intunes programhanteringsverktyg
Använd **Microsoft Intunes programhanteringsverktyg för iOS** för att ändra funktionssättet för interna iOS-appar genom att begränsa funktionerna i appen utan att ändra koden för själva appen.

Verktyget är ett kommandoradsprogram för Mac OS som skapar en omslutning runt en app. När en app har bearbetats kan du ändra appens funktioner med [hanteringsprinciper för mobilprogram](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) som du konfigurerar.

För att ladda ned verktyget går du till [Microsoft Intunes programhanteringsverktyg för iOS](http://www.microsoft.com/en-us/download/details.aspx?id=45218)

## Steg 1 Uppfyll nödvändiga krav för att använda programhanteringsverktyget

|Krav|Mer information|
|---------------|--------------------------------|
|Operativsystem och verktygsuppsättning som stöds|Du måste köra app-wrapping-verktyget på en Mac-dator som kör OS X 10.8.5 eller senare och som har verktygsuppsättningen XCode version 5 eller senare installerad.|
|Signeringscertifikat och etableringsprofil|Du måste ha ett signeringscertifikat från Apple och en etableringsprofil. Mer information finns i [dokumentationen för Apple-utvecklare](https://developer.apple.com/)|
|Bearbeta en app med programhanteringsverktyget|Apparna måste vara utvecklade och signerade av ditt företag eller någon oberoende programvaruleverantör (ISV). Du kan inte använda verktyget för att bearbeta appar från Apple Store. Apparna måste vara skrivna för iOS 7.0 eller senare. Apparna måste också vara i formatet PIE (Position Independent Executable). Mer information om formatet PIE finns i dokumentationen för Apple-utvecklare. Slutligen måste appen ha filnamnstillägget **.app** eller **.ipa**.|
|Appar som programhanteringsverktyget inte kan bearbeta|Krypterade appar, osignerade appar och appar med utökade filattribut.|
|Appar som använder Azure Active Directory Library (ADAL)|Om appen använder sig av ADAL måste appen innehålla ADAL version 1.0.2 eller senare, och utvecklaren måste ge appen åtkomst till resursen för hantering av mobilprogram i Intune.<br /><br />Information om hur du använder ADAL finns i [Information om appar som använder Azure Active Directory Library](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#information-for-apps-that-use-the-azure-active-directory-library) i den här artikeln.|
|Ställa in rättigheter för din app|Du måste ställa in rättigheter, som ger appen ytterligare funktioner och behörigheter utöver de som vanligtvis beviljas, innan du omsluter appen. Anvisningar finns i [Ställa in apprättigheter](#setting-app-entitlements).|

## Steg 2 Installera programhanteringsverktyget

1.  På sidan för **Microsoft Intunes programhanteringsverktyg för iOS** i [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=45218) laddar du ned installationsfilen för programhanteringsverktyget till en Mac-dator.

2.  På Mac-datorn dubbelklickar du på installationsfilen **Microsoft Intune App Wrapping Tool for iOS.dmg**.

3.  Välj **Godkänn** för att godkänna licensavtalet för slutanvändare (EULA). Installationsprogrammet monteras och visas på Mac-datorn.

4.  Öppna installationsprogrammet och kopiera de visade filerna till en ny mapp på Mac-datorn. Nu kan du koppla ifrån den monterade installationsenheten.

    Nu kan du börja köra appomslutningsverktyget.

## Steg 3 Kör programhanteringsverktyget

1.  På Mac-datorn öppnar du ett terminalfönster och går till den mapp där du sparade filerna. Eftersom den körbara filen finns i paketet, måste du köra kommandot på följande sätt:
```
    ./IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -a <client ID of input app> -r <reply URI of input app> -v true
```
    > [!NOTE]
    > Some parameters are optional as shown in the table below.

    **Example:** The following example command runs the app wrapping tool on an app named **MyApp.ipa**. A provisioning profile and SHA-1 hash are specified. The processed app is created and stored in the **/users/myadmin/Documents** on the Mac computer.

    ```
    /users/myadmin/Downloads/IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager -i /users/myadmin/Downloads/MyApp.ipa -o /users/myadmin/Documents/MyApp_Wrapped.ipa -p /users/myadmin/Downloads/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB –a 20e1cd0d-268e-4308-9583-02ae97dd353e –r https://contoso/ -v true
    ```
    You can use the following command line properties with the app wrapping tool:

|Egenskap|Mer information|
  |------------|--------------------|
  |**-h**|Visar tillgängliga kommandoradsegenskaper för app-wrapping-verktyget.|
  |**-i**|Anger sökvägen och filnamnet för indataappen.|
  |**-o**|Anger sökvägen till den plats där du vill spara den bearbetade appen.|
  |**-p**|Anger sökvägen till etableringsprofilen för iOS-appar.|
  |**-c**|Anger SHA1-hashen för signeringscertifikatet.|
  |**-a**|Klient-ID för indataappen (i formatet GUID) om appen använder Azure Active Directory Libraries (valfritt).|
  |**-r**|Omdirigerings-URI för indataappen om appen använder Azure Active Directory Libraries (valfritt).|
  |**-v**|Skicka utförliga meddelanden till konsolen (valfritt).|

2. När bearbetningen är klar visas meddelandet **Appen har omslutits** .

    Om ett fel inträffar hittar du hjälp i [Felmeddelanden](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages).

3.  Den omslutna appen sparas i den utdatamapp du har angett tidigare. Du kan ladda upp appen till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och koppla den till en princip för hantering av mobila appar.

    > [!IMPORTANT]
    > Du måste ladda upp appen som en ny app. Du kan inte uppdatera en äldre, icke wrappad version av appen.

    Nu kan du distribuera appen till dina [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-grupper, så körs appen på enheten med de begränsningar som du anger.

## Felmeddelanden och loggfiler
Använd följande information för att felsöka problem med programhanteringsverktyget.

### Felmeddelanden
Om det inte går att slutföra app-wrapping-verktyget visas något av följande felmeddelanden:

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
|Ett ogiltigt signeringscertifikat har angetts. Ange ett giltigt signeringscertifikat för Apple.|Kontrollera att du har hämtat rätt signeringscertifikat från Apples utvecklarportal. Certifikatet kanske har löpt ut. Om ditt Apple-certifikat och din etableringsprofil kan användas för att logga in på en app i Xcode på rätt sätt, är de också giltiga för appomslutningsverktyget.|
|Indataappen du har angett är ogiltig. Ange en giltig app.|Kontrollera att du har en giltig iOS-app som är kompilerad som en APP- eller IPA-fil.|
|Indataappen du har angett är krypterad. Ange en giltig okrypterad app.|Appomslutningsverktyget stöder inte krypterade appar. Ange en okrypterad app.|
|Den indataapp du angav har inte formatet PIE. Ange en giltig app i PIE-format.|PIE-appar kan läsas in på en slumpmässig minnesadress när de körs, vilket kan vara bra ur säkerhetssynpunkt. Mer information finns i Dokumentation för Apple-utvecklare.|
|Indataappen som du angav har redan omslutits. Ange en giltig okrypterad app.|Du kan inte bearbeta en app som redan har behandlats av verktyget. Om du vill bearbeta en app igen kör du verktyget med den ursprungliga versionen av appen.|
|Indataappen du angav har inte signerats. Ange en giltig signerad app.|Appomslutningsverktyget kräver att apparna signeras. Läs utvecklardokumentationen om du vill veta hur du signerar en omsluten app.|
|Indataappen du har angett måste vara i formatet IPA eller APP.|Endast appar med filnamnstilläggen APP och IPA godkänns av appomslutningsverktyget. Kontrollera att indatafilen har ett giltigt filnamnstillägg och har kompilerats som en APP- eller IPA-fil.|
|Indataappen som du angav är redan omsluten och har den senaste versionen av principmallen.|Appomslutningsverktyget kommer inte att omsluta en befintlig omsluten app igen med den senaste versionen av principmallen.|
|Det angivna Azure Active Directory-klient-ID:t har inget giltigt GUID. Ange ett giltigt klient-ID.|När du använder klient-ID-parametern måste du kontrollera att du har angett ett giltigt klient-ID i GUID-format.|
|Den angivna svars-URI:n för Azure Active Directory-klient-ID:t har inget giltigt GUID. Ange en giltig URI.|När du använder kommandoradsegenskapen för svars-URI:n måste du kontrollera att du har angett en giltig svars-URI.|
|VARNING: Du har inte angett någon SHA1-certifikatshash. Kontrollera att den omslutna appen har signerats innan du distribuerar den.|Kontrollera att du har angett ett giltigt SHA-hash-värde (med hjälp av kommandoradsegenskapen **– c** ).|

### Loggfiler för appomslutningsverktyget
Appar som har varit omslutna med hjälp av appomslutningsverktyget genererar loggar som skrivs till iOS-klientenhetskonsolen. Den här informationen är användbar om du har problem med appen och behöver diagnostisera om problemet har att göra med appomslutningsverktyget. Använd följande steg för att hämta den här informationen:

1.  Återskapa problemet genom att köra appen.

2.  Samla in konsolens utdata genom att följa Apples instruktioner för att [felsöka distribuerade iOS-appar](https://developer.apple.com/library/ios/qa/qa1747/_index.html)

3.  Filtrera de sparade loggarna för utdata från appbegränsningarna genom att ange följande skript i konsolen:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Du kan skicka de filtrerade loggarna till Microsoft.

    > I loggfilen representerar objektet 'build-version' Xcode-versionen.

    Omslutna appar kommer också att erbjuda användarna möjlighet att skicka loggarna direkt från enheten via e-post när appen kraschar. Användarna kan skicka loggen till dig så att du kan undersöka den och vidarebefordra den till Microsoft om det behövs.

## Information om appar som använder Azure Active Directory Library
Informationen i det här avsnittet gäller enbart för appar som använder Azure Active Directory Library (ADAL). Om du är osäker på om din app använder det här biblioteket kan du kontakta apputvecklaren.

Appen måste innehålla ADAL version 1.0.2 eller högre

Följande villkor måste vara uppfyllda för appar som använder ADAL:

-   Appen måste innehålla ADAL version 1.0.2 eller högre

-   Utvecklare måste ge sin app åtkomst till resursen för hantering av mobilprogram i Intune, enligt beskrivningen i [Steg för appar som använder ADAL](#steps-to-follow-for-apps-that-use-adal)

### Översikt över identifierare som du behöver
Appar som använder ADAL måste registreras via Azures hanteringsportal för att erhålla två unika identifierare för appen:

|Identifierare|Mer information|Standardvärde|
|--------------|--------------------|-----------------|
|**Klient-ID**|En unik GUID-identifierare genereras för varje app när den registreras i Azure Active Directory.<br /><br />Om du känner till appens specifika klient-ID kan du ange det värdet. Annars måste standardvärdet användas.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**Omdirigerings-URI**|Ett URI-värde som utvecklare kan tillhandahålla när de registrerar appen med Azure Active Directory för att säkerställa att autentiseringstoken returneras till denna slutpunkt.<br /><br />Omdirigerings-URI:n är en valfri parameter för appomslutningsverktyget. Om inget anges används standard-URI:n.|urn:ietf:wg:oauth:2.0:oob|


### Steg för appar som använder ADAL

1.  Granska [Översikt över identifierare som du behöver](#overview-of-identifiers-you-need-to-get) för att identifiera de värden som du behöver.

2.  Du konfigurerar åtkomst till mobilapphantering i Azure Active Directory på följande sätt:

    1. Logga in på ett befintligt Azure Active Directory-konto i Azure-hanteringsportalen.

    2.  Klicka på **befintlig LOB-appregistrering** i Azure Active Directory.

    3.  I avsnittet konfigurera väljer du **Konfigurera åtkomst till webb-API:er i andra program**

    4.  I den första listrutan i avsnittet **Behörighet till andra program** väljer du **Hantering av mobilprogram i Intune**

        Du kan nu använda appens klient-ID i programhanteringsverktyget. Du hittar appens klient-ID i hanteringsportalen för Azure Active Directory enligt beskrivningen i avsnittet [Översikt över identifierare som du behöver](#overview-of-identifiers-you-need-to-get).

3.  Använd värdena för **Klient-ID** (med hjälp av egenskapen **–a**) och **Omdirigerings-URI** som kommandoradsegenskaper i programhanteringsverktyget. Om du inte har dessa värden används standardvärdena. Båda värdena måste anges, annars kan slutanvändaren inte autentisera den bearbetade appen.

### Certifikat, etableringsprofil och autentiseringskrav

|Krav|Information|
|---------------|-----------|
|Etableringsprofil|**Kontrollera att etableringsprofilen är giltig innan du lägger till den** – Programhanteringsverktyget kontrollerar inte om etableringsprofilen har upphört att gälla när en iOS-app bearbetas. Om en förfallen etableringsprofil har angetts tar programhanteringsverktyget med den förfallna etableringsprofilen och du märker inte att det är något problem förrän det visar sig att appen inte kan installeras på en iOS-enhet.|
|Certifikat|**Kontrollera att certifikatet är giltigt innan du anger det** – Verktyget kontrollerar inte om certifikatet har upphört att gälla när en iOS-app bearbetas. Om hash-värdet för ett utgånget certifikat anges, behandlar verktyget appen och signerar den, men kommer inte att kunna installera den på enheterna.<br /><br />**Kontrollera att certifikatet som angetts för signering av den paketerade appen har en motsvarighet i etableringsprofilen** – Verktyget verifierar inte om etableringsprofilen har en motsvarighet för det certifikat som angetts för signering av den omslutna appen.|
|Autentisering|En enhet måste ha en PIN-kod för att krypteringen ska fungera. På de enheter du har distribuerat omslutna appar till måste användaren återautentisera med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] om statusfältet vidrörs. Standardprincipen i ett omslutet program är *autentisering vid omstart*. När iOS identifierar externa aviseringar (t.ex. ett telefonsamtal) avslutas appen för att sedan startas om.<br /><br />Den första användare som loggar in på en omsluten app från samma utgivare cachelagras. Sedan tillåts endast denna användare att använda appen. Om du vill återställa användaren måste enheten avregistreras och sedan registreras igen.|

### Felsökning och teknisk information om ADAL

-   Om det inte finns några ADAL-resurser använder verktyget det dynamiska ADAL-biblioteket. Verktyget söker efter ADAL-biblioteket med namnet **ADALiOS.bundle** i rotmappen.

-   Verktyget söker inte efter ADAL-binärfiler (om det finns sådana) i appen. Om appen länkar till en inaktuell version, kan körningsfel uppstå vid inloggning om autentiseringsprinciper är aktiverade.

-   [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] hämtar AAD-token för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM-resurs-ID:t för autentisering. Den används dock inte i anrop som i sin tur skulle verifiera tokens giltighet. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] läser endast UPN för den inloggade användaren för att kontrollera appåtkomsten. AAD-token används inte för ytterligare tjänstanrop.

-   Autentiseringstoken delas mellan appar från samma utgivare eftersom de lagras i den delade nyckelringen. Om du vill isolera en viss app måste du använda ett annat signeringscertifikat och en annan etableringsprofil för appen.

-   Dubbla inloggningsprompter förhindras om du tillhandahåller din klientapps klient-ID och omdirigerings-URI. Detta klient-ID måste registreras för att få åtkomst till det publicerade [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM-resurs-ID:t i AAD-instrumentpanelen. Annars misslyckas inloggningen när programmet körs.

## Ställa in apprättigheter
Innan du omsluter appen kan du bevilja **rättigheter** för att ge appen ytterligare behörigheter och funktioner som överskrider vad en app vanligtvis kan.  En **rättighetsfil** används under kodsignering för att ange särskilda behörigheter i appen (till exempel åtkomst till en delad nyckelring). Vissa apptjänster, som kallas **funktioner**, aktiveras i Xcode under apputvecklingen. När dessa funktioner har aktiverats visas de i din i din rättighetsfil. Mer information om rättigheter och funktioner finns i [Lägga till funktioner](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) i iOS Developer Library. En fullständig lista över funktioner som stöds finns i [Funktioner som stöds](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html)

### Funktioner som stöds för programhanteringsverktyg för iOS

|Funktion|Beskrivning|Råd|
|--------------|---------------|------------------------|
|App-grupper|Använd appgrupper för att tillåta åtkomst för flera appar till delade behållare och tillåta ytterligare kommunikation mellan processer för olika appar.<br /><br />Om du vill aktivera appgrupper öppnar du fönstret **Funktioner** och klickar på växeln **PÅ** i avsnittet **App-grupper**. Du kan lägga till app-grupper eller välja befintliga.|Använd omvänd DNS-notering när du använder app-grupper:<br /><br />*group.com.companyName.AppGroup*|
|Bakgrundslägen|Genom att aktivera bakgrundslägen kan din iOS-app fortsätta köras i bakgrunden.||
|Dataskydd|Dataskydd lägger till en säkerhetsnivå för filer som lagras på disk av din iOS-app. Dataskydd utnyttjar den inbyggda krypteringsmaskinvarann som finns på vissa enheter för att lagra filer i krypterat format på disken. Din app behöver etableras om du vill använda dataskydd.||
|Köp via app|Köp i appen bäddar in en butik direkt i din app genom att göra det möjligt för dig att ansluta till butiken och på ett säkert sätt behandla betalningar från användaren. Du kan använda inköp i appen för att samla in betalning för utökad funktionalitet eller för ytterligare innehåll som kan användas med din app.||
|Nyckelringsdelning|Med aktivering av nyckelringsdelning kan din app dela lösenord i nyckelringen med andra appar som har utvecklats av ditt team.|Använd omvänd DNS-notering när du använder nyckelringsdelning:<br /><br />*com.companyName.KeychainGroup*|
|Personlig VPN|Du kan aktivera personlig VPN så att din app kan skapa och styra en anpassad system-VPN-konfiguration med hjälp av ramverket för nätverkstillägg||
|Push-meddelanden|Med hjälp av Apple Push Notification-tjänsten kan en app som inte körs i förgrunden meddela användaren om att den har information till användaren.|Du måste använda en app-specifik etableringsprofil för att push-meddelanden ska fungera.<br /><br />Följ stegen i [dokumentationen för Apple-utvecklare](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)|
|Konfiguration för trådlösa tillbehör|Konfigurationen för att aktivera trådlösa tillbehör lägger till ramverket för externa tillbehör till ditt projekt och gör möjligt att konfigurera MFi Wi-Fi-tillbehör med din app.||

### Steg för att aktivera rättigheter

1.  Aktivera funktioner i din app:

    1.  Navigera till målet för appen i Xcode och klicka på fönstret **Funktioner**.

    2.  Aktivera lämpliga funktioner. Detaljerad information om varje funktion och hur du fastställer rätt värden finns i [Lägga till funktioner](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) i iOS Developer Library.

    3.  Notera eventuella ID:n som du skapade under processen.

    4.  Skapa och registrera den app som ska omslutas.

2.  Aktivera rättigheter i din etableringsprofil:

    1.  Logga in till Apple Developer Member Center.

    2.  Skapa en etableringsprofil för din app. Instruktioner finns i [Skaffa förutsättningarna för Intune-programhanteringsverktyget för iOS](http://blogs.technet.com/b/microsoftintune/archive/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios.aspx)

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
./IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## Säkerhet och sekretess för appomslutningsverktyget
Använd följande metodtips för säkerhet och sekretess när du använder appomslutningsverktyget.

-   Signeringscertifikatet, etableringsprofilen och affärsområdesappen du anger måste finnas på samma Mac-dator som den du använder för att appomslutningsverktyget ska kunna köras. Om filerna finns på en UNC-sökväg, måste du kontrollera att de är tillgängliga från datorn. Sökvägen måste skyddas via IPsec- eller SMB-signering.

    Den omslutna appen importerats till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-konsolen bör vara på detsamma datorn som du körs verktyget på. Om filén finns på en UNC-sökväg, måste du kontrollera att det är tillgängligt på den dator som kör [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-konsolen. Sökvägen måste skyddas via IPsec- eller SMB-signering.

-   Miljön där appomslutningsverktyget har hämtats från Microsoft Download Center måste vara skyddad via IPsec eller SMB-signering.

-   Appen du bearbetar måste komma från en betrodd källa för att garantera skydd mot attacker.

-   Kontrollera att den utgående mappen du anger i appomslutningsverktyget är skyddad, särskilt om det är en fjärransluten mapp.

-   Med iOS-appar som innehåller en dialogruta för filöverföring kan användare kringgå de begränsningar för klipp ut, kopiera och klistra in som gäller för appen. En användare kan till exempel använda dialogrutan Överför för att överföra en skärmbild av appdata.

-   När användarna övervakar dokumentmappen på sina enheter inifrån appomslutningsverktyget, kan de se en mapp med namnet **.msftintuneapplauncher**. Om den här mappen ändras eller tas bort kan detta påverka funktionen hos appar med begränsningar.

### Se även
- [Förbereda appar för hantering av mobilprogram med Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Aktivera hantering av mobilprogram i appar med SDK](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO2-->


