---
title: Omsluta iOS-appar med Intunes programhanteringsverktyg
description: Läs om hur du omsluter iOS-appar utan att ändra koden i själva appen. Förbered apparna så att du kan använda hanteringsprinciper för mobilprogram.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62ee300b7357132e6f9e18ef4528110dfc988dc3
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/03/2020
ms.locfileid: "75653673"
---
# <a name="prepare-ios-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Förbered iOS-appar för appskyddsprinciper med Intunes programhanteringsverktyg

Använd Microsoft Intunes programhanteringsverktyg för iOS för att aktivera appskyddsprinciper från Intune för interna iOS-appar utan att ändra koden i själva appen.

Verktyget är ett kommandoradsprogram för Mac OS som skapar en omslutning runt en app. När en app har behandlats kan du ändra dess funktioner genom att distribuera [appskyddsprinciper](../apps/app-protection-policies.md) till den.

Om du vill ladda ned verktyget går du till [Microsoft Intunes appomslutningsverktyg för iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) på GitHub.

## <a name="general-prerequisites-for-the-app-wrapping-tool"></a>Allmänna krav för programhanteringsverktyget

Innan du kör programhanteringsverktyget måste du uppfylla vissa allmänna krav:

* Ladda ned [Microsoft Intunes programhanteringsverktyg för iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) från GitHub.

* En Mac OS-dator som kör OS X 10.8.5 eller senare och som har Xcode-verktygsuppsättningen version 9 eller senare installerad.

* iOS-appen för indata måste vara utvecklad och signerad av ditt företag eller en oberoende programvaruleverantör (ISV).

  * App-filen för indata måste ha filnamnstillägget **.ipa** eller **.app**.

  * Indataappen måste kompileras för iOS 11 eller senare.

  * Indataappen kan vara krypterad.

  * Indataappen kan inte ha utökade filattribut.

  * Indataappen måste ha angivna rättigheter innan den bearbetas av Intunes programhanteringsverktyg. [Rättigheterna](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html) ger appen ytterligare funktioner och behörigheter utöver de som vanligtvis beviljas. Anvisningar finns i [Ställa in apprättigheter](#setting-app-entitlements).

## <a name="apple-developer-prerequisites-for-the-app-wrapping-tool"></a>Apple Developer-krav för programhanteringsverktyget

För att exklusivt distribuera omslutna appar till användare i organisationen behöver du ett konto med [Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/) och flera entiteter för signering av appar som är länkade till ditt Apple Developer-konto.

Om du vill veta mer om att distribuera iOS-appar internt till användare i organisationen kan du läsa den officiella guiden för att [distribuera appar med Apple Developer Enterprise Program](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1).

Du behöver följande för att distribuera appar som är omslutna av Intune:

* Ett utvecklarkonto med Apple Developer Enterprise Program.

* Interna och ad hoc-distributionssigneringscertifikat med giltiga gruppidentifierare.

  * Du behöver SHA1-hashen för signeringscertifikatet som en parameter för Intunes programhanteringsverktyg.


* Etableringsprofil för intern distribution.

### <a name="steps-to-create-an-apple-developer-enterprise-account"></a>Steg för att skapa ett Apple Developer Enterprise-konto

1. Gå till [webbplatsen för Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/).

2. Klicka på **Registrera** i övre högra hörnet av sidan.

3. Läs checklistan över vad du behöver för att registrera. Klicka på **Start Your Enrollment** (Påbörja din registrering) längst ned på sidan.

4. **Logga in** med din organisations Apple-ID. Om du inte har något ID klickar du på **Skapa Apple-ID**.

5. Välj din **Enhetstyp** och klicka på **Fortsätt**.

6. Fyll i formuläret med information om din organisation. Klicka på **Fortsätt**. Efter detta kontaktar Apple dig för att kontrollera att du har behörighet att registrera din organisation.

7. När kontrollen är klar klickar du på **Agree to License** (Godkänn licens).

8. När du godkänt licensen slutför du genom att **köpa och aktivera programmet**.

9. Om du är gruppagenten (den person som ansluter till Apple Developer Enterprise Program för din organisations räkning) kan du skapa din grupp genom att bjuda in gruppmedlemmar och tilldela dem roller. För att lära dig om hur du hanterar din grupp kan du läsa Apple-dokumentationen i [Managing Your Developer Account Team](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1) (Hantera din Developer-kontogrupp).

### <a name="steps-to-create-an-apple-signing-certificate"></a>Steg för att skapa ett Apple-signeringscertifikat

1. Gå till [Apple Developer-portalen](https://developer.apple.com/).

2. Klicka på **Konto** i övre högra hörnet av sidan.

3. **Logga in** med din organisations Apple-ID.

4. Klicka på **Certifikat, ID och profiler**.

   ![Apple Developer-portalen – Certifikat, ID:n och profiler](./media/app-wrapper-prepare-ios/iOS-signing-cert-1.png)

5. Klicka på ![plustecknet i övre högra hörnet av](./media/app-wrapper-prepare-ios/iOS-signing-cert-2.png) Apple Developer-portalen för att lägga till ett iOS-certifikat.

6. Välj att skapa ett **In-House and Ad Hoc** (internt och ad hoc)-certifikat under **Produktion**.

   ![Välj internt och ad hoc-certifikat](./media/app-wrapper-prepare-ios/iOS-signing-cert-3.png)

   >[!NOTE]
   >Om du inte planerar att distribuera appen och endast vill testa den internt kan du använda ett iOS-apputvecklingscertifikat i stället för ett certifikat för produktion. Om du använder ett utvecklingscertifikat kontrollerar du att den mobila etableringsprofilen hänvisar till de enheter där appen ska installeras.

7. Klicka på **Nästa** längst ner på sidan.

8. Läs anvisningarna om hur du skapar en **certifikatsigneringsförfrågan** med hjälp av nyckelhanterarprogrammet på din Mac OS-dator.

   ![Läs anvisningarna för att skapa en CSR](./media/app-wrapper-prepare-ios/iOS-signing-cert-4.png)

9. Följ anvisningarna ovan för att skapa en signeringsbegäran för certifikat. Starta **Nyckelhanterar**-programmet på din Mac OS-dator.

10. Gå till **Nyckelhanterare > Certificate Assistant (Certifikatassistent) > Request a Certificate From a Certificate Authority (Begär ett certifikat från en certifikatutfärdare)** i Mac OS-menyn överst på skärmen.  

    ![Begär ett certifikat från en certifikatutfärdare i Nyckelhanteraren](./media/app-wrapper-prepare-ios/iOS-signing-cert-5.png)

11. Följ instruktionerna från Apple-utvecklarwebbplatsen ovanför om hur du skapar en CSR-fil. Spara CSR-filen på din Mac OS-dator.

    ![Ange information för det certifikat som du begär](./media/app-wrapper-prepare-ios/iOS-signing-cert-6.png)

12. Gå tillbaka till Apple-utvecklarwebbplatsen. Klicka på **Fortsätt**. Ladda sedan upp CSR-filen.

13. Apple skapar ett signeringscertifikat åt dig. Hämta och spara den till en plats som är lätt att komma ihåg på din Mac OS-dator.

    ![Hämta ditt signeringscertifikat](./media/app-wrapper-prepare-ios/iOS-signing-cert-7.png)

14. Dubbelklicka på certifikatfilen som du precis laddade ned för att lägga till certifikatet i en nyckelring.

15. Öppna **Nyckelhanteraren** igen. Leta upp certifikatet genom att söka efter dess namn i det övre högra sökfältet. Högerklicka på objektet för att visa menyn och klicka på **Hämta information**. På exempelbilderna använder vi ett utvecklingscertifikat i stället för ett produktionscertifikat.

    ![Lägg till certifikatet i en nyckelring](./media/app-wrapper-prepare-ios/iOS-signing-cert-8.png)

16. Ett informationsfönster visas. Bläddra till slutet och titta under etiketten **Fingeravtryck**. Kopiera strängen **SHA1** (har gjorts suddig) för att använda den som argument för "-c" för programhanteringsverktyget.

    ![iPhone-information – SHA1-sträng för fingeravtryck](./media/app-wrapper-prepare-ios/iOS-signing-cert-9.png)

### <a name="steps-to-create-an-in-house-distribution-provisioning-profile"></a>Steg för att skapa en etableringsprofil för intern distribution

1. Gå tillbaka till [Apple Developer-kontoportalen](https://developer.apple.com/account/) och **logga in** med din organisations Apple-ID.

2. Klicka på **Certifikat, ID och profiler**.

3. Klicka på ![plustecknet i övre högra hörnet av](./media/app-wrapper-prepare-ios/iOS-signing-cert-2.png) Apple Developer-portalen för att lägga till en iOS-etableringsprofil.

4. Välj att skapa en **intern** etableringsprofil under **Distribution**.

   ![Välj intern etableringsprofil](./media/app-wrapper-prepare-ios/iOS-provisioning-profile-1.png)

5. Klicka på **Fortsätt**. Se till att länka det tidigare skapade signeringscertifikatet till etableringsprofilen.

6. Följ stegen för att hämta din profil (med filtillägget .mobileprovision) till din Mac OS-dator.

7. Spara filen på en plats som är lätt att komma ihåg. Den här filen kommer att användas för -p-parametern när du använder programhanteringsverktyget.

## <a name="download-the-app-wrapping-tool"></a>Hämta programhanteringsverktyget

1. Hämta filerna för programhanteringsverktyget från [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) till en macOS-dator.

2. Dubbelklicka på **Microsoft Intune App Wrapping Tool for iOS.dmg**. Ett fönster med licensavtalet för slutanvändare (EULA) visas. Läs igenom dokumentet noggrant.

3. Välj **Godkänn** för att godkänna licensavtalet och montera paketet på datorn.

## <a name="run-the-app-wrapping-tool"></a>Kör App-Wrapping-verktyget

### <a name="use-terminal"></a>Använd terminal

Öppna macOS-terminalen och kör följande kommando:

```bash
/Volumes/IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> Vissa parametrar är valfria, som du ser i följande tabell.

**Exempel:** Följande exempelkommando kör programhanteringsverktyget i appen MyApp.ipa. En etableringsprofil och en SHA-1-hash för signeringscertifikatet anges och används för att signera den omslutna appen. Utdata-appen (MyApp_Wrapped.ipa) skapas och lagras i mappen Skrivbord.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c "12 A3 BC 45 D6 7E F8 90 1A 2B 3C DE F4 AB C5 D6 E7 89 0F AB"  -v true
```

### <a name="command-line-parameters"></a>Kommandoradsparametrar

Du kan använda följande kommandoradsparametrar med programhanteringsverktyget:

|Egenskap|Använd så här|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`. Filnamnet måste sluta med .app eller .ipa. |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**| Visar detaljerad användningsinformation om tillgängliga kommandoradsegenskaper för programhanteringsverktyget. |
|**-aa**|(Valfritt) `<Authority URI of the input app if the app uses the Azure Active Directory Authentication Library>`, dvs. `login.windows.net/common` |
|**-ac**|(Valfritt) `<Client ID of the input app if the app uses the Azure Active Directory Authentication Library>` detta är det GUID i fältet klient-ID från appens lista i bladet app-registrering. |
|**-ar**|(Valfritt) `<Redirect/Reply URI of the input app if the app uses the Azure Active Directory Authentication Library>` det här är omdirigerings-URI: n som kon figurer ATS i appens registrering. Detta är vanligt vis URL-protokollet för programmet som Microsoft Authenticator-appen kommer tillbaka till efter att ha tillämpat autentisering. |
|**-v**| (Valfri) Returnerar utförliga meddelanden till konsolen. Vi rekommenderar att du använder den här flaggan för att felsöka eventuella fel. |
|**-e**| (Valfri) Använd den här flaggan om du vill att programhanteringsverktyget ska ta bort rättigheter som saknas när appen bearbetas. Mer information finns i [Ställa in apprättigheter](#setting-app-entitlements).|
|**-xe**| (Valfri) Skriver ut information om iOS-tilläggen i appen och vilka rättigheter som krävs för att använda dem. Mer information finns i [Ställa in apprättigheter](#setting-app-entitlements). |
|**-x**| (Valfritt) `<An array of paths to extension provisioning profiles>`. Använd det här alternativet om appen behöver tilläggsetableringsprofiler.|
|**-b**|(Valfritt) Använd -b utan argument om du vill att den omslutna utdataappen ska ha samma paketversion som indataappen (rekommenderas inte). <br/><br/> Använd `-b <custom bundle version>` om du vill att den omslutna appen ska ha en anpassad CFBundleVersion. Om du väljer att ange en anpassad CFBundleVersion rekommenderar vi att du ökar den inbyggda appens CFBundleVersion med den minst viktiga komponenten, t.ex. 1.0.0 -> 1.0.1. |
|**-citrix**|Valfritt Ta med Citrix XenMobile app SDK (endast nätverks-variant). Du måste ha [Citrix MDX Toolkit](https://docs.citrix.com/en-us/mdx-toolkit/about-mdx-toolkit.html) installerat för att kunna använda det här alternativet. |
|**-f**|(Valfri) `<Path to a plist file specifying arguments.>` Använd den här flaggan framför [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html)-filen om du väljer att använda plist-mallen för att ange resten av IntuneMAMPackager-egenskaperna, t.ex. -i, -o och -p. Mer information finns i Använda en plist för att ange argument. |

### <a name="use-a-plist-to-input-arguments"></a>Använda en plist för att ange argument

Ett enkelt sätt att köra appomslutningsverktyget är att placera alla kommandoradsargument i en [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html)-fil. Plist är ett filformat som liknar XML som du kan använda för att ange kommandoradsargument med hjälp av ett formulärgränssnitt.

I mappen IntuneMAMPackager/Contents/MacOS öppnar du `Parameters.plist` (en tom plist-mall) med en textredigerare eller Xcode. Ange argumenten för följande nycklar:

| Plist-nyckel | Typ |  Standardvärde | Obs! |
|------------------|-----|--------------|-----|
| Paketsökväg för indataapp |Sträng|tomt| Samma som -i|
| Paketsökväg för utdataapp |Sträng|tomt| Samma som -o|
| Sökväg för etableringsprofil |Sträng|tomt| Samma som -p|
| SHA-1-certifikatets hash |Sträng|tomt| Samma som -c|
| ADAL-utfärdare |Sträng|tomt| Samma som -aa|
| ADAL-klient-ID |Sträng|tomt| Samma som -ac|
| ADAL svars-URI |Sträng|tomt| Samma som -ar|
| Utförlig aktiverad |Boolesk|falskt| Samma som -v|
| Ta bort rättigheter som saknas |Boolesk|falskt| Samma som -c|
| Förhindra uppdatering av standardversion |Bool|falskt| Likvärdigt med att använda -b utan argument|
| Åsidosättning av versionssträng |Sträng|tomt| Anpassad CFBundleVersion för den omslutna utdataappen|
| Inkludera Citrix XenMobile app SDK (endast nätverks-variant)|Boolesk|falskt| Samma som-Citrix|
| Sökvägar för tilläggsetableringsprofil |Strängmatris|tomt| En uppsättning med tilläggsetableringsprofiler för appen.

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

## <a name="how-often-should-i-rewrap-my-ios-application-with-the-intune-app-wrapping-tool"></a>Hur ofta ska jag omsluta mitt iOS-program på nytt med Intunes programhanteringsverktyg?

Huvudscenarierna när du måste omsluta dina program på nytt är följande:

* Programmet har publicerat en ny version. Den tidigare versionen av appen har omslutits och överförts till Intune-konsolen.
* Intunes programhanteringsverktyg för iOS har publicerat en ny version som möjliggör viktiga felkorrigeringar, eller nya, specifika principfunktioner för skydd av Intune-program. Detta sker efter 6–8 veckor via GitHub-lagringsplatsen för [Microsoft Intunes programhanteringsverktyg för iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).

Även om det är möjligt för iOS att omsluta med en annan certifierings-/etableringsprofil än den som ursprungligen användes för att signera appen kommer omslutningen att misslyckas om de berättiganden som specificeras i appen inte inkluderas i den nya etableringsprofilen. Om du använder kommandoradsalternativet ”-e”, som tar bort eventuella berättiganden som saknas från appen för att tvinga omslutningen att inte misslyckas i detta scenario kan det leda till att appen inte fungerar som den ska.

Här är några metodtips för omslutning på nytt:

* Se till att en annan etableringsprofil har alla berättiganden som krävs som fanns i eventuell tidigare etableringsprofil. 

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
|Varning! Du har inte angett någon SHA1-certifikatshash. Kontrollera att den omslutna appen har signerats innan du distribuerar den.|Kontrollera att du har angett ett giltigt SHA1-hashvärde efter kommandoradsflaggan -c. |

### <a name="collecting-logs-for-your-wrapped-applications-from-the-device"></a>Samlar in loggar för dina omslutna program från enheten
Använd följande steg för att hämta loggar för dina omslutna program under felsökningen.

1. Gå till inställningar för iOS-appen på enheten och välj LOB-appen.
2. Växla **Diagnostikkonsolen** till **På**.
3. Starta LOB-programmet.
4. Klicka på länken ”Kom igång”.
5. Du kan nu dela loggar via e-post eller kopiera dem till en plats i OneDrive.

> [!NOTE]
> Loggningsfunktionen är aktiverad för appar som har omslutits med Intunes programhanteringsverktyg version 7.1.13 eller senare.

### <a name="collecting-crash-logs-from-the-system"></a>Samla in krasch loggar från systemet

Din app kan logga värdefull information i iOS-konsolen för klient enheter. Den här informationen är användbar om du har problem med appen och behöver fastställa om problemet har att göra med programhanteringsverktyget eller själva appen. Använd följande steg för att hämta den här informationen:

1. Återskapa problemet genom att köra appen.

2. Samla in konsolens utdata genom att följa Apples instruktioner för att [felsöka distribuerade iOS-appar](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

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
|Appgrupper|Använd appgrupper om du vill ge flera appar åtkomst till delade container och tillåta ytterligare kommunikation mellan processer för olika appar.<br /><br />Om du vill aktivera appgrupper öppnar du rutan **Funktioner** och klickar på **PÅ** i **Appgrupper**. Du kan lägga till app-grupper eller välja befintliga.|Använd omvänd DNS-notering när du använder app-grupper:<br /><br />*group.com.companyName.AppGroup*|
|Bakgrundslägen|Om du aktiverar bakgrundslägen kan din iOS-app fortsätta att köras i bakgrunden.||
|Dataskydd|Dataskydd lägger till en säkerhetsnivå för filer som lagras på disk av din iOS-app. Dataskydd utnyttjar den inbyggda krypteringsmaskinvarann som finns på vissa enheter för att lagra filer i krypterat format på disken. Din app behöver etableras om du vill använda dataskydd.||
|Köp via app|Köp via app bäddar in en butik direkt i din app på ett sätt som gör att du kan ansluta till butiken och behandla betalningar från användaren med hög säkerhet. Du kan använda funktionen Köp via app för att ta betalt för utökade funktioner eller för ytterligare innehåll som kan användas med din app.||
|Nyckelringsdelning|Om du aktiverar nyckelringsdelning kan din app dela lösenord i nyckelringen med andra appar som har utvecklats av ditt team.|Använd omvänd DNS-notering när du använder nyckelringsdelning:<br /><br />*com.companyName.KeychainGroup*|
|Personlig VPN|Du kan aktivera personlig VPN så att din app kan skapa och styra en anpassad system-VPN-konfiguration med hjälp av ramverket för nätverkstillägg||
|Push-meddelanden|Med hjälp av Apple Push Notification Service (APNS) kan en app som inte körs i förgrunden meddela användaren att den har information till användaren.|Du måste använda en app-specifik etableringsprofil för att push-meddelanden ska fungera.<br /><br />Följ anvisningarna i [dokumentationen för Apple-utvecklare](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Konfiguration för trådlösa tillbehör|Om du aktiverar konfiguration för trådlösa tillbehör läggs ramverket för externa tillbehör till i ditt projekt så att du kan konfigurera MFi Wi-Fi-tillbehör med din app.||

### <a name="steps-to-enable-entitlements"></a>Steg för att aktivera rättigheter

1. Aktivera funktioner i din app:

    a.  Gå till målet för din app i Xcode och klicka på **Funktioner**.

    b.  Aktivera lämpliga funktioner. Detaljerad information om varje funktion och hur du fastställer rätt värden finns i [Lägga till funktioner](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) i iOS Developer Library.

    c.  Notera eventuella ID:n som du skapade under processen. Dessa kan även för `AppIdentifierPrefix`-värdena.

    d.  Skapa och registrera den app som ska omslutas.

2. Aktivera rättigheter i din etableringsprofil:

    a.  Logga in på Apple Developer Member Center.

    b.  Skapa en etableringsprofil för din app. Instruktioner finns i [Skaffa förutsättningarna för Intune-apphanteringsverktyget för iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/).

    c.  Aktivera samma rättigheter som du har i din app i din etableringsprofil. Du måste ange samma ID:n (`AppIdentifierPrefix`-värdena) som du angav under utvecklingen av din app. 

    d.  Slutför guiden för etableringsprofiler och ladda ner filen.

3. Kontrollera att du har uppfyllt alla krav och omslut därefter appen.

### <a name="troubleshoot-common-errors-with-entitlements"></a>Felsökning av vanliga fel med rättigheter

Prova följande felsökningssteg om programhanteringsverktyget för iOS rapporterar ett rättighetsfel.

|Problem|Orsak|Lösning|
|---------|---------|--------------|
|Det gick inte att parsa rättigheter som genererats av indataappen.|Programhanteringsverktyget kan inte läsa rättighetsfilen som har extraherats från appen. Rättighetsfilen kan vara felaktig.|Kontrollera rättighetsfilen för din app. Följande anvisningar beskriver hur du gör. Sök efter felaktig syntax vid kontroll av rättighetsfilen. Filen bör vara i XML-format.|
|Rättigheter saknas i etableringsprofilen (saknade rättigheter anges i listan). Paketera om appen med en etableringsprofil som har dessa rättigheter.|Det finns ett matchningsfel mellan rättigheter aktiverade i etableringsprofilen och de funktioner som aktiverats i appen. Denna felmatchning gäller även de ID:n som associeras med specifika funktioner (som appgrupper och nyckelringsåtkomst).|I allmänhet kan du skapa en ny etableringsprofil som möjliggör samma funktioner som appen. När ID:n mellan profilen och appen inte matchar ersätter programhanteringsverktyget dessa ID:n om så är möjligt. Om felet fortfarande visas när du har skapat en ny etableringsprofil kan du prova att ta bort rättigheter från appen med hjälp av parametern -e (se avsnittet Använda parametern -e för att ta bort rättigheter från en app).|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>Hitta befintliga rättigheter för en signerad app

Granska befintliga rättigheter för en signerad app och en etableringsprofil:

1. Hitta .ipa-filen och ändra dess tillägg till .zip.

2. Expandera .zip-filen. Detta genererar en nyttolast-mapp som innehåller ditt .app-paket.

3. Använd codesign-verktyget för att kontrollera rättigheterna för .app-paketet, där `YourApp.app` är namnet på .app-paketet:

    ```bash
    codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4. Använd säkerhetsverktyget för att kontrollera rättigheterna för appens inbäddade etableringsprofil, där `YourApp.app` är namnet på .app-paketet.

    ```bash
    security cms -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>Ta bort rättigheter från en app med hjälp av parametern -e

Det här kommandot tar bort alla aktiverade funktioner i appen som inte ingår i rättighetsfilen. Om du tar bort funktioner som används av appen kan appen skadas. Ett exempel på när du kan ta bort funktioner som saknas är om du har en leverantörsutvecklad app där alla funktioner är standard.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>Säkerhet och sekretess för programhanteringsverktyget

Använd följande riktlinjer för säkerhet och sekretess när du använder programhanteringsverktyget.

- Signeringscertifikatet, etableringsprofilen och affärsappen som du anger måste finnas på samma Mac OS-dator som den som du använder för att köra programhanteringsverktyget. Om filerna finns på en UNC-sökväg kontrollerar du att de är tillgängliga från Mac OS-datorn. Sökvägen måste skyddas via IPsec- eller SMB-signering.

    Den omslutna appen importerats till administratörskonsolen bör vara på detsamma datorn som du körs verktyget på. Om filén finns på en UNC-sökväg, måste du kontrollera att det är tillgängligt på den dator som kör administratörskonsolen. Sökvägen måste skyddas via IPsec- eller SMB-signering.

- Miljön där programhanteringsverktyget hämtas från GitHub-databasen måste vara skyddad med IPsec eller SMB-signering.

- Appen du bearbetar måste komma från en betrodd källa för att garantera skydd mot attacker.

- Kontrollera att den utgående mappen som du anger i programhanteringsverktyget är skyddad, särskilt om det är en fjärransluten mapp.

- Med iOS-appar som innehåller en dialogruta för filöverföring kan användarna kringgå de begränsningar för klipp ut, kopiera och klistra in som gäller för appen. En användare kan till exempel använda dialogrutan Överför för att överföra en skärmbild av appdata.

- När du övervakar dokumentmappen på enheten från en omsluten app kan du se en mapp med namnet .msftintuneapplauncher. Om du ändrar eller tar bort den här filen kan det resulterade i att begränsade appar inte fungerar som de ska.

## <a name="intune-app-wrapping-tool-for-ios-with-citrix-mdx-mvpn"></a>Intunes programhanteringsverktyg för iOS med Citrix MDX mVPN

Den här funktionen är en integrering med Citrix MDX-programhanteringsverktyget för iOS. Integrationen är helt enkelt en extra valfri flagga på kommandoraden, `-citrix`, för Intunes allmänna programhanteringsverktyg.

### <a name="requirements"></a>Krav

Om du vill använda flaggan `-citrix` måste du även installera [Citrix MDX-programhanteringsverktyget för iOS](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) på samma macOS-dator. Du kan hämta filerna från [webbplatsen för Citrix XenMobile](https://www.citrix.com/downloads/xenmobile/), och du måste först logga in som Citrix-kund. Se till att verktyget installeras på standardplatsen: `/Applications/Citrix/MDXToolkit`. 

> [!NOTE] 
> Integreringen av Intune och Citrix stöds bara på enheter med iOS 10 eller senare.

### <a name="use-the--citrix-flag"></a>Använda flaggan `-citrix`

Kör helt enkelt ditt vanliga programhanteringskommando med flaggan `-citrix` på slutet. Flaggan `-citrix` har för närvarande inte några argument.

**Användningsformat**:

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioing profile paths>] [-citrix]
```

**Exempelkommando**:

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true -citrix
```

## <a name="see-also"></a>Se även

- [Förbereda appar för hantering av mobilprogram med Microsoft Intune](apps-prepare-mobile-application-management.md)
- [Common questions, issues, and resolutions with device policies and profiles](../configuration/device-profile-troubleshoot.md)
- [Aktivera hantering av mobilprogram i appar med SDK](app-sdk.md)
