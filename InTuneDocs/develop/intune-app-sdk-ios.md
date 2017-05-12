---
title: "Utvecklarhandbok för Microsoft Intune App SDK | Microsoft Docs"
description: "Med Microsoft Intune App SDK för iOS kan du lägga till appskyddsprinciper i form av mobilappshantering (MAM, Mobile App Management) med Intune i iOS-appen."
keywords: 
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df54ac3a62b5ef21e8a32f3a282dd5299974a1b0
ms.openlocfilehash: 1d2cb0d4b9442262c562e559a675f5a4a28ee572
ms.contentlocale: sv-se
ms.lasthandoff: 05/03/2017


---

# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Utvecklarhandbok för Microsoft Intune App SDK för iOS

> [!NOTE]
> Börja gärna med att läsa guiden [Komma igång med Intune App SDK](intune-app-sdk-get-started.md), som förklarar hur du förbereder integreringen på de plattformar som stöds.

Med Microsoft Intune App SDK för iOS kan du lägga till appskyddsprinciper (kallas även **APP**- eller **MAM-principer**) med Intune i den inbyggda iOS-appen. Ett MAM-aktiverat program är ett program som är integrerat med Intune App SDK. IT-administratörer kan distribuera appskyddsprinciper till den mobila appen när Intune hanterar appen aktivt.

## <a name="prerequisites"></a>Krav

* Du behöver en Mac OS-dator som kör OS X 10.8.5 eller senare och har Xcode 8 eller senare installerat.

* Appen måste vara inriktad på iOS 9 eller senare.

* Granska [licensvillkoren för Intune App SDK för iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf). Skriv ut och behåll en kopia av licensvillkoren. Genom att ladda ned och använda Intune App SDK för iOS godkänner du licensvillkoren.  Om du inte godkänner dem ska du inte använda programvaran.

* Ladda ned filerna för Intune App SDK för iOS på [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk"></a>Vad innehåller SDK?

Intune App SDK för iOS innehåller ett statiskt bibliotek, resursfiler, API-rubriker, en .plist-fil med inställningar för felsökning samt ett konfigurationsverktyg. Mobilappar kan helt enkelt inkludera resursfilerna och statiskt länka till biblioteken i de flesta tillämpningarna av principer. Avancerade MAM-funktioner i Intune aktiveras via API:er.

Den här guiden beskriver användning av följande delar av Intune App SDK för iOS:

* **libIntuneMAM.a**: det statiska Intune App SDK-biblioteket. Om appen inte använder tillägg kan du länka det här biblioteket till projektet för att aktivera appen för hantering av mobila program i Intune.

* **IntuneMAM.framework**: ramverket för Intune App SDK. Länka det här ramverket till projektet för att aktivera appen för hantering av mobila program i Intune. Använd ramverket i stället för det statiska biblioteket om appen använder tillägg, så att projektet inte skapar flera kopior av det statiska biblioteket.

* **IntuneMAMResources.Bundle**: ett resurspaket som innehåller resurser som SDK är beroende av.

* **Rubriker**: visar API:er för Intune App SDK. Om du använder ett API måste du inkludera huvudfilen som innehåller API:et. Följande rubriker innehåller API-funktionsanrop som krävs för att aktivera funktionerna i Intune App SDK:

    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h


## <a name="how-the-intune-app-sdk-works"></a>Så fungerar Intune App SDK

Målet med Intune App SDK för iOS är att lägga till hanteringsfunktioner i iOS-program med minimala kodändringar. Ju färre kodändringar som görs, desto fortare blir appen klar, utan att påverka konsekvens och stabilitet i det mobila programmet.


## <a name="build-the-sdk-into-your-mobile-app"></a>Skapa SDK i den mobila appen

Följ anvisningarna nedan om du vill aktivera Intune App SDK:

1. **Alternativ 1 (rekommenderas)**: länka `IntuneMAM.framework` till projektet. Dra `IntuneMAM.framework` till listan **Linked Frameworks and Libraries** (Länkade ramverk och bibliotek) i projektets målkatalog.

    > [!NOTE]
    > Om du använder ramverket måste du ta bort simulatorarkitekturerna manuellt från det universella ramverket innan du skickar in appen till App Store. Mer information finns i [Skicka appen till App Store](#Submit-your-app-to-the-App-Store).

2. **Alternativ 2**: länka till `libIntuneMAM.a`-biblioteket. Dra `libIntuneMAM.a`-biblioteket till listan **Linked Frameworks and Libraries** (Länkade ramverk och bibliotek) i projektets målkatalog.

    ![Intune App SDK iOS: länkade ramverk och bibliotek](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    > [!NOTE]
    > Om du planerar att lansera appen i App Store bör du använda den version av `libIntuneMAM.a` som skapats för lanseringen, alltså inte felsökningsversionen. Lanseringsversionen ligger i mappen **publicering**. Felsökningsversionen har utförliga utdata som hjälper till att felsöka problem med Intune App SDK.

    Lägg till `-force_load {PATH_TO_LIB}/libIntuneMAM.a` i något av följande och ersätt `{PATH_TO_LIB}` med platsen för Intune App SDK:
      * Projektets konfigurationsinställning för versionen `OTHER_LDFLAGS`
      * Användargränssnitten **Other Linker Flags** (Andra länkarflaggor)

        > [!NOTE]
        > Hitta `PATH_TO_LIB` genom att markera filen `libIntuneMAM.a` och välja **Get Info** (Hämta info) på menyn **Arkiv**. Kopiera och klistra in informationen i **Where** (Var) (sökvägen) från avsnittet **Allmänt** i fönstret **Information**.

3. Lägg till dessa iOS-ramverk i projektet:
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.tbd
    * libc++.tbd
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework


4. Lägg till resurspaketet `IntuneMAMResources.bundle` i projektet genom att dra resurspaketet till **Copy Bundle Resources** (Kopiera paketresurser) i **Build Phases** (Versionsfaser).

    ![Intune App SDK iOS: kopiera paketresurser](../media/intune-app-sdk-ios-copy-bundle-resources.png)

5. Om mobilappen definierar en Main Nib- eller Storyboard-fil i filen Info.plist tar du bort fälten för **Main Storyboard** eller **Main Nib**. i Info.plist klistrar du in dessa fält och deras motsvarande värden under en ny ordlista som heter **IntuneMAMSettings** med följande namn, i tillämpliga fall:
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad
    > [!NOTE]
  > Om mobilappen inte definierar någon Main Nib- eller Storyboard-fil i filen Info.plist är dessa inställningar inte obligatoriska.

    Du kan visa filen Info.plist i obearbetat format (för att visa nyckelnamnen) genom att högerklicka någonstans i dokumentets brödtext och ändra visningstypen till **Show Raw Keys/Values** (Visa obearbetade nycklar/värden).

6. Aktivera delning av nyckelringar (om det inte redan är aktiverat) genom att klicka på **Funktioner** i varje projektmål och aktivera reglaget för **Nyckelringsdelning**. Delning av nyckelringar krävs för att kunna fortsätta till nästa steg.

  > [!NOTE]
    > Etableringsprofilen måste ha stöd för nya värden för delning av nyckelringar. Åtkomstgrupper för nyckelringar ska ha stöd för jokertecken. Du kan kontrollera det genom att öppna filen .mobileprovision i en textredigerare, söka efter **keychain-access-groups** och se till att du har ett jokertecken. Exempel:
    ```xml
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```

7. När du har aktiverat delning av nyckelringar följer du dessa steg för att skapa en separat åtkomstgrupp där Intune App SDK kommer att spara sina data. Du kan skapa en åtkomstgrupp för nyckelringar med hjälp av användargränssnittet eller med behörighetsfilen. Om du använder användargränssnittet för att skapa åtkomstgruppen för nyckelringar ser du till att följa stegen nedan:

    1. Om mobilappen inte har definierat några åtkomstgrupper för nyckelringar lägger du till appens paket-ID som den första gruppen.

    2. Lägg till den delade nyckelringsgruppen `com.microsoft.intune.mam` i dina befintliga åtkomstgrupper. Intune App SDK använder den här åtkomstgruppen för att lagra data.

    3. Lägg till `com.microsoft.adalcache` i dina befintliga åtkomstgrupper.

        4. Lägg till `com.microsoft.workplacejoin` i dina befintliga åtkomstgrupper.
            ![Intune App SDK iOS: delning av nyckelringar](../media/intune-app-sdk-ios-keychain-sharing.png)

      5. Om du använder behörighetsfilen för att skapa en åtkomstgrupp för nyckelringar lägger du till åtkomstgruppen för nyckelringar med `$(AppIdentifierPrefix)` i behörighetsfilen. Exempel:

            * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
            * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    > [!NOTE]
    > En behörighetsfil är en XML-fil som är unik för det mobila programmet. Den används för att ange särskilda behörigheter och funktioner i iOS-appen.

7. Om appen definierar URL-scheman i Info.plist-filen lägger du till ytterligare ett schema med suffixet `-intunemam` för varje URL-schema.

8. För mobila appar som utvecklas på iOS 9+ ska varje protokoll som appen godkänns för läggas till i `UIApplication canOpenURL` i `LSApplicationQueriesSchemes`-matrisen för appens Info.plist-fil. Lägg dessutom ett nytt protokoll och bifoga det med `-intunemam` för varje angivet protokoll. Du måste även inkludera `http-intunemam`, `https-intunemam` och `ms-outlook-intunemam` i matrisen.

9. Om appen har definierade appgrupper i sina behörigheter lägger du till dessa grupper i ordlistan **IntuneMAMSettings** under nyckeln `AppGroupIdentifiers` som en matris med strängar.



## <a name="configure-azure-active-directory-authentication-library-adal"></a>Konfigurera Azure Active Directory Authentication Library (ADAL)

Intune App SDK använder [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) för autentisering och scenarier för villkorlig start. Den använder även ADAL för att registrera användaridentiteten med MAM-tjänsten för hantering utan enhetsregistreringsscenarier.

Normalt kräver ADAL att appar registreras i Azure Active Directory (AAD) och får ett unikt ID (klient-ID) och andra identifierare, för att garantera säkerheten för de token som beviljats appen. Om inget annat anges använder Intune App SDK standardvärden för registrering när den kontaktar Azure AD.  

Om appen redan använder ADAL för att autentisera användare måste appen använda sina befintliga registreringsvärden och åsidosätta standardvärdena för Intune App SDK. Det säkerställer att användarna inte uppmanas att autentisera två gånger (en gång av Intune App SDK och en gång av appen).

### <a name="recommendations"></a>Rekommendationer

Vi rekommenderar att appen länkar till den [senaste versionen av ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) på sin huvudgren. Intune App SDK använder för närvarande broker-grenen av ADAL som stöd för appar som kräver villkorlig åtkomst. (De här apparna är därför beroende av Microsoft Authenticator-appen.) SDK är dock fortfarande kompatibel med huvudgrenen av ADAL. Använd den gren som är lämplig för din app.

### <a name="link-to-adal-binaries"></a>Länka till ADAL-binärfiler

Följ stegen nedan för att länka appen till ADAL-binärfilerna:

1. Ladda ned [Azure Active Directory Authentication Library (ADAL) for Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) från GitHub och följ sedan [anvisningarna](https://github.com/AzureAD/azure-activedirectory-library-for-objc/blob/master/README.md) för att ladda ned ADAL med Git-undermoduler eller CocoaPods.

2. Inkludera `ADALiOSBundle.bundle`-resurspaketet i projektet genom att dra resurspaketet till **Copy Bundle Resources** (Kopiera paketresurser) i **Build Phases** (Versionsfaser).

3. Lägg till `-force_load {PATH_TO_LIB}/libADALiOS.a` i projektets `OTHER_LDFLAGS` versionskonfigurationsinställning eller **Other Linker Flags** (Andra länkarflaggor) i användargränssnittet. `PATH_TO_LIB` ska ersättas med platsen för ADAL-binärfilerna.



### <a name="share-the-adal-token-cache-with-other-apps-signed-with-the-same-provisioning-profile"></a>Dela ADAL-tokencache med andra appar som är signerade med samma etableringsprofil?**

Följ anvisningarna nedan om du vill dela ADAL-token mellan appar som är signerade med samma etableringsprofil:

1. Om appen inte har definierat några åtkomstgrupper för nyckelringar lägger du till appens paket-ID som den första gruppen.

2. Aktivera enkel inloggning (SSO) i ADAL genom att lägga till åtkomstgrupperna `com.microsoft.adalcache` och `com.microsoft.workplacejoin` i nyckelringsrättigheterna.

3. Om du uttryckligen ställer in den ADAL-delade cache-nyckelringsgruppen ser du till att den är inställd på `<app_id_prefix>.com.microsoft.adalcache`. ADAL ställer in detta åt dig om du inte åsidosätter det. Om du vill ange en anpassad nyckelringsgrupp som ska ersätta `com.microsoft.adalcache` anger du det i Info.plist-filen under IntuneMAMSettings, med hjälp av nyckeln `ADALCacheKeychainGroupOverride`.

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Konfigurera ADAL-inställningar för Intune App SDK

Om appen redan använder ADAL för autentisering och har sina egna ADAL-inställningar kan du tvinga Intune App SDK att använda samma inställningar under autentisering mot Azure Active Directory. Detta säkerställer att appen inte kommer att uppmana användaren om autentisering flera gånger. Se [Konfigurera inställningar för Intune App SDK](#configure-settings-for-the-intune-app-sdk) om du vill ha information om att fylla i följande inställningar:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Om appen redan använder ADAL krävs följande konfigurationer:

1. I projektets Info.plist-fil anger du under ordlistan **IntuneMAMSettings** med nyckelnamnet `ADALClientId` det klient-ID som ska användas för ADAL-anrop.

2. Under ordlistan **IntuneMAMSettings** med nyckelnamnet `ADALAuthority` anger du även Azure AD-auktoritet.

3. Under ordlistan **IntuneMAMSettings** med nyckelnamnet `ADALRedirectUri` anger du även omdirigerings-URI som ska användas för ADAL-anrop. Du kan även behöva ange `ADALRedirectScheme` beroende på formatet för appens omdirigerings-URI.


Dessutom kan du åsidosätta utfärdar-URL för Azure AD med en klientspecifik URL vid körning. Det gör du genom att ange egenskapen `aadAuthorityUriOverride` i `IntuneMAMPolicyManager` instansen.

> [!NOTE]
> Det är nödvändigt att ange auktoritets-URL för AAD för [APP utan enhetsregistrering](#App-protection-policy-without-device-enrollment) om SDK ska kunna återanvända ADAL-uppdateringstoken som hämtas av appen.

SDK fortsätter att använda denna auktoritets-URL för principuppdatering och eventuella efterföljande registreringsförfrågningar, om inte värdet rensas eller ändras.  Det är därför viktigt att rensa värdet när en hanterad användare loggar ut från appen och att återställa värdet när en ny hanterad användare loggar in.

### <a name="if-your-app-does-not-use-adal"></a>Om appen inte använder ADAL

Om appen inte använder ADAL tillhandahåller Intune App SDK standardvärden för ADAL-parametrar och hanterar autentisering mot Azure AD. Du behöver inte ange några värden för ADAL-inställningarna ovan.

## <a name="app-protection-policy-without-device-enrollment"></a>Appskyddsprincip utan enhetsregistrering

### <a name="overview"></a>Översikt
Intunes appskyddsprincip utan enhetsregistrering, kallas även **APP-WE** eller MAM-WE, gör det möjligt att hantera appar med Intune utan att enheten måste vara registrerad i mobil enhetshantering med Intune (MDM). Appen måste delta i att registrera användarkonton för hantering för att ha stöd för denna nya funktion. Följ anvisningarna nedan om du vill använda de nya API:erna:

1. Använd den senaste versionen av Intune App SDK, som har stöd för hantering av appar med eller utan enhetsregistrering.

2. Lägg till IntuneMAMEnrollment.h i alla filer som ska anropa API:erna.

### <a name="register-user-accounts"></a>Registrera användarkonton

En app kan ta emot appskyddsprinciper från Intune-tjänsten om appen registreras i APP-WE-tjänsten för ett angivet användarkonto. Appen ansvarar för registrering av eventuella användare som nyligen har loggat in med SDK. När det nya användarkontot har autentiserats ska appen anropa metoden `registerAndEnrollAccount` i Headers/IntuneMAMEnrollment.h:

```objc
/**


 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;

```
Genom att anropa metoden `registerAndEnrollAccount` registrerar SDK användarkontot och försöker att registrera appen för detta konto. Om registreringen misslyckas av någon anledning försöker SDK automatiskt att registrera igen 24 timmar senare. Vid felsökning kan appen via ett ombud ta emot aviseringar om resultaten av eventuella registreringsförfrågningar.

När denna API har anropats kan appen fortsätta att fungera som normalt. Om registreringen lyckas meddelar SDK användaren att omstart av appen krävs. Vid detta tillfälle kan användaren starta om appen direkt.

### <a name="deregister-user-accounts"></a>Avregistrera användarkonton

Innan en användare loggas ut från en app bör appen avregistrera användaren från SDK. Detta säkerställer:

1. Nya registreringsförsök sker inte längre för användarens konto.

2. Appskyddsprincipen tas bort.

3. Om appen initierar en selektiv rensning (valfritt) raderas eventuella företagsdata.

Innan användaren loggas ut ska appen anropa följande API i `Headers/IntuneMAMEnrollment.h`:

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune MAM AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */

(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

Den här metoden måste anropas innan användarkontots Azure AD-token tas bort. SDK behöver användarkontots AAD-token för att göra specifika förfrågningar till APP-WE-tjänsten för användarens räkning.

Om appen tar bort användarens företagsdata på egen hand kan flaggan `doWipe` ställas in på falskt. Annars kan appen se till att SDK initierar en selektiv rensning. Det leder till ett anrop till appens ombud för selektiv rensning.

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

### <a name="apps-that-do-not-use-adal"></a>Appar som inte använder ADAL

Appar som inte loggar in användare med hjälp av ADAL kan ändå få appskyddsprincipen från Intune-tjänsten genom att anropa API så att SDK hanterar autentiseringen. Appar bör använda den här metoden när de inte har autentiserat en användare med Azure AD men ändå behöver hämta appskyddsprincipen för att hjälpa till att skydda data. Ett exempel är om en annan autentiseringstjänst används för appinloggning eller om appen inte alls har stöd för inloggning. För att göra detta ska programmet anropa metoden `loginAndEnrollAccount` i Headers/IntuneMAMEnrollment.h:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;

```

Genom att anropa den här metoden uppmanar SDK användaren att ange autentiseringsuppgifter om det inte går att hitta någon befintlig token. SDK försöker sedan registrera appen med APP-WE-tjänsten för det angivna användarkontot. Metoden kan anropas med "nil" som identitet. I så fall registreras SDK med den befintliga hanterade användaren på enheten eller så uppmanas användaren att ange ett användarnamn om ingen befintlig användare hittades.

Om registreringen misslyckas ska appen överväga att anropa detta API igen vid ett senare tillfälle, beroende på felets egenskaper. Appen kan via ett ombud ta emot [aviseringar](#Status-result-and-debug-notifications) om resultaten av eventuella registreringsförfrågningar.

När denna API har anropats kan appen fortsätta att fungera som normalt. Om registreringen lyckas meddelar SDK användaren att omstart av appen krävs.

## <a name="status-result-and-debug-notifications"></a>Aviseringar om status, resultat och felsökning

Appen kan ta emot aviseringar om status, resultat och felsökning gällande följande förfrågningar till Intune MAM-tjänsten:

 - Begäran om registrering
 - Begäran om principuppdatering
 - Begäran om avregistrering

Aviseringarna visas via ombudsmetoder i `Headers/IntuneMAMEnrollmentDelegate.h`:

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

```

Dessa ombudsmetoder returnerar ett `IntuneMAMEnrollmentStatus`-objekt med följande information:

- Identiteten för det konto som är kopplat till begäran
- En statuskod som visar resultatet av begäran
- En felsträng med en beskrivning av statuskoden
- Ett `NSError`-objekt

Det här objektet definieras i `IntuneMAMEnrollmentStatus.h`, tillsammans med de specifika statuskoder som kan returneras.


### <a name="sample-code"></a>Exempelkod

Det här är exempel på implementeringar av ombudsmetoderna:

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}


- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

```

## <a name="app-restart"></a>Starta om app

När en app tar emot appskyddsprinciper för första gången måste den startas om för att verkställa de hookar som krävs. För att meddela appen om att en omstart måste ske tillhandahåller SDK en ombudsmetod i Headers/IntuneMAMPolicyDelegate.h.

```objc
 - (BOOL) restartApplication
```
Returvärdet för den här metoden talar om för SDK om programmet måste hantera den omstart som krävs:   

 - Om sant returneras måste programmet hantera omstarten.   

 - Om falskt returneras startar SDK om programmet efter att denna metod har returnerats. SDK visar direkt en dialogruta som meddelar användaren att programmet ska startas om.

## <a name="customize-your-apps-behavior"></a>Anpassa appens beteende

Intune App SDK har flera API:er som du kan anropa för att få information om den appskyddsprincip från Intune som distribueras till appen. Du kan använda dessa data för att anpassa appens beteende. De flesta inställningar för appskyddsprinciper framtvingas automatiskt av SDK och inte programmet. Den enda inställning som appen ska implementera är kontrollen Save-as.

### <a name="get-app-protection-policy"></a>Hämta appskyddsprincip

#### <a name="intunemampolicymanagerh"></a>IntuneMAMPolicyManager.h
Klassen IntuneMAMPolicyManager visar den appskyddsprincip från Intune som distribueras till programmet. Tänk på att den visar API:er som är användbara för att [aktivera flera identiteter](#-enable-multi-identity-optional).

#### <a name="intunemampolicyh"></a>IntuneMAMPolicy.h
Klassen IntuneMAMPolicy visar den appskyddsprincip från Intune som distribueras till programmet. De flesta principinställningar som visas i denna klass tvingas fram av SDK, men du kan alltid anpassa appens beteende beroende på hur principinställningarna används.

Den här klassen visar vissa API:er som krävs för att implementera save-as-kontroller, vilket förklaras i nästa avsnitt.

### <a name="implement-save-as-controls"></a>Implementera save-as-kontroller

Med Intune kan IT-administratörer välja vilka lagringsplatser som en hanterad app kan spara data i. Appar kan fråga Intune App SDK om tillåtna lagringsplatser genom att använda API:n **isSaveToAllowedForLocation**, som definieras i **IntuneMAMPolicy.h**.

Innan appar kan spara hanterade data i molnlagring eller på en lokal plats måste de fråga API:n **isSaveToAllowedForLocation** för att veta om IT-administratören har tillåtit att data sparas där.

När appar använder API:n **isSaveToAllowedForLocation** måste de godkännas i UPN för lagringsplatsen, om tillgängligt.

#### <a name="supported-save-locations"></a>Platser som stöds för att spara

API:n **isSaveToAllowedForLocation** tillhandahåller konstanter för att kontrollera om IT-administratören tillåter att data sparas på följande platser som definieras i IntuneMAMPolicy.h:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Apparna bör använda konstanterna i API:n **isSaveToAllowedForLocation** för att kontrollera om data kan sparas till platser som anses vara "hanterade", t.ex. OneDrive for Business, eller "personliga". Dessutom ska API:n användas när appen inte kan kontrollera om en plats är "hanterad" eller "personlig".

Platser som är kända som "personliga" representeras av konstanten `IntuneMAMSaveLocationOther`.

Konstanten `IntuneMAMSaveLocationLocalDrive` ska användas när appen sparar data till valfri plats på den lokala enheten.

## <a name="configure-settings-for-the-intune-app-sdk"></a>Konfigurera inställningar för Intune App SDK

Du kan använda ordlistan **IntuneMAMSettings** i programmets Info.plist-fil för att konfigurera Intune App SDK. Om ordlistan IntuneMAMSettings inte syns i Info.plist-filen ska du skapa en ordlista i appens Info.plist med fältnamnet "IntuneMAMSettings."

Under ordlistan IntuneMAMSettings kan du lägga till nyckel-/värderader med konfigurationsinställningar för att konfigurera SDK. Tabellen nedan visar alla inställningar som stöds.

Några av de här inställningarna kan ha beskrivits i föregående avsnitt och vissa gäller inte för alla appar.

Inställningar  | Typ  | Definition | Obligatoriskt?
--       |  --   |   --       |  --
ADALClientId  | Sträng  | Appens Azure AD-klientidentifierare. | Krävs om appen använder ADAL. |
ADALAuthority | Sträng | Appens Azure AD-auktoritet som används. Du bör använda din egen miljö där AAD-konton har konfigurerats. | Krävs om appen använder ADAL. Om detta värde saknas används ett Intune-standardvärde.|
ADALRedirectUri  | Sträng  | Appens omdirigerings-URI för Azure AD. | ADALRedirectUri eller ADALRedirectScheme krävs om appen använder ADAL.  |
ADALRedirectScheme  | Sträng  | Appens omdirigeringsschema för Azure AD. Detta kan användas i stället för ADALRedirectUri om programmets omdirigerings-URI har formatet `scheme://bundle_id`. | ADALRedirectUri eller ADALRedirectScheme krävs om appen använder ADAL. |
ADALLogOverrideDisabled | Boolesk  | Anger om SDK dirigerar alla ADAL-loggar (inklusive eventuella ADAL-anrop från appen) till den egna loggfilen. Standardvärdet är NO (NEJ). Ange YES (JA) om appen ska ange egna återanrop i ADAL-loggen. | Valfritt. |
ADALCacheKeychainGroupOverride | Sträng  | Anger den nyckelringsgrupp som ska användas för ADAL-cache, i stället för “com.microsoft.adalcache." Observera att detta inte har prefixet app-id. Det föregår strängen som anges vid körning. | Valfritt. |
AppGroupIdentifiers | Strängmatris  | Matris med appgrupper från appens behörigheter i avsnittet com.apple.security.application-groups  | Krävs om appen använder programgrupper. |
ContainingAppBundleId | Sträng | Anger paket-ID för programmet som ingår i tillägget. | Krävs för iOS-tillägg. |
DebugSettingsEnabled| Boolesk | Om detta är inställt på YES (JA) kan testprinciper i inställningspaketet användas. Program bör *inte* levereras med den här inställningen aktiverad. | Valfritt. |
MainNibFile<br>MainNibFile~ipad  | Sträng  | Den här inställningen ska innehålla programmets namn på Main Nib-filen.  | Krävs om programmet definierar MainNibFile i Info.plist. |
MainStoryboardFile<br>MainStoryboardFile~ipad  | Sträng  | Den här inställningen ska programmets Main Storyboard-filnamn. | Krävs om programmet definierar UIMainStoryboardFile i Info.plist. |
MAMPolicyRequired| Boolesk| Anger om start av appen kommer att blockeras om appen inte har en appskyddsprincip för Intune. Standardvärdet är NO (NEJ). <br><br> Obs! Appar kan inte skickas till App Store med MAMPolicyRequired inställt på YES (JA). | Valfritt. |
MAMPolicyWarnAbsent | Boolesk| Anger om appen varnar användaren under start om appen inte har en appskyddsprincip för Intune. Tänk på att appar inte kan skickas till butiken med detta inställt på YES (JA). | Valfritt. |
MultiIdentity | Boolesk| Anger om appen hanterar flera identiteter. | Valfritt. |
SplashIconFile <br>SplashIconFile~ipad | Sträng  | Anger ikonfilen för Intunes välkomstskärm (start). | Valfritt. |
SplashDuration | Antal | Kortaste tid i sekunder som startskärmen för Intune visas när programmet startas. Standardvärdet är 1,5. | Valfritt. |
BackgroundColor| Sträng| Anger bakgrundsfärgen för start- och PIN-kodsskärmar. Godkänner en hexadecimal RGB-sträng i formatet #XXXXXX, där X kan vara ett värde mellan 0–9 eller A–F. Pundtecknet kan utelämnas.   | Valfritt. Standard är ljusgrå. |
ForegroundColor| Sträng| Anger förgrundsfärgen för start- och PIN-kodsskärmar, t.ex. textfärg. Godkänner en hexadecimal RGB-sträng i formatet #XXXXXX, där X kan vara ett värde mellan 0–9 eller A–F. Pundtecknet kan utelämnas.  | Valfritt. Standard är svart. |
AccentColor | Sträng| Anger accentfärgen för PIN-kodsskärmen, t.ex. textfärg och rutans markeringsfärg. Godkänner en hexadecimal RGB-sträng i formatet #XXXXXX, där X kan vara ett värde mellan 0–9 eller A–F. Pundtecknet kan utelämnas.| Valfritt. Standard är systemblå. |
MAMTelemetryDisabled| Boolesk| Anger om SDK inte skickar några telemetridata till backend-delen.| Valfritt. |

> [!NOTE]
> Om appen ska publiceras i App Store måste `MAMPolicyRequired` vara inställt på "NEJ", enligt standarder för App Store.

## <a name="telemetry"></a>Telemetri

Intune App SDK för iOS loggar som standard telemetridata om följande användningshändelser. Dessa data skickas till Microsoft Intune.

* **Appstart**: För att hjälpa Microsoft Intune att få veta mer om MAM-aktiverad appanvändning efter hanteringstyp (MAM med MDM, MAM utan MDM-registrering osv).

* **Registreringsanrop**: För att hjälpa Microsoft Intune att förstå lyckade resultat och annan resultatstatistik för registreringsanrop som initieras från klienten.

> [!NOTE]
> Om du väljer att inte skicka Intune App SDK-telemetridata till Microsoft Intune från mobilappen måste du inaktivera telemetriinsamlingen för Intune App SDK. Ange egenskapen `MAMTelemetryDisabled` på YES (JA) i ordlistan IntuneMAMSettings.

## <a name="enable-multi-identity-optional"></a>Aktivera flera identiteter (valfritt)

SDK tillämpar som standard en princip på appen som helhet. Flera identiteter är en MAM-funktion som du kan aktivera för att använda en princip på nivån per identitet. Detta kräver mer appdeltagande än andra MAM-funktioner.

Appen måste informera app-SDK när den har för avsikt att ändra den aktiva identiteten. SDK meddelar även appen när en identitetsändring krävs. För närvarande stöds endast en hanterad identitet. När användaren har registrerat enheten eller appen använder SDK den här identiteten och ser den som den primära hanterade identiteten. Andra användare i appen behandlas som ohanterade med obegränsade principinställningar.

Tänk på att en identitet helt enkelt definieras som en sträng. Identiteter är inte skiftlägeskänsliga. Begäranden till SDK om en identitet kanske inte returnerar samma skiftläge som användes ursprungligen när identiteten angavs.

### <a name="identity-overview"></a>Identitetsöversikt

En identitet är helt enkelt användarnamnet på ett konto (till exempel user@contoso.com). Utvecklare kan ange identiteten för appen på följande nivåer:

* **Processidentitet**: Anger den processomfattande identiteten och används främst för enstaka identitetsprogram. Den här identiteten påverkar alla aktiviteter, filer och användargränssnittet.

* **Gränssnittsidentitet**: Avgör vilka principer som används på gränssnittsaktiviteter i huvudtråden, t.ex. klipp ut/kopiera/klistra in, PIN-kod, autentisering och datadelning. Gränssnittsidentiteten påverkar inte filaktiviteter som kryptering och säkerhetskopiering.

* **Trådidentitet**: Påverkar vilka principer som används på den aktuella tråden. Den här identiteten påverkar alla aktiviteter, filer och användargränssnittet.

Appen ansvarar för att ange identiteterna på lämpligt sätt, oavsett om användaren är hanterad eller inte.

Vid varje tidpunkt har varje tråd har en effektiv identitet för gränssnittsaktiviteter och filaktiviteter. Det här är den identitet som används för att kontrollera vilka principer som ska användas, om några. Inga principer tillämpas om identiteten är "ingen identitet" eller om användaren inte hanteras. Diagrammen nedan visar hur effektiva identiteter fastställs.

  ![Intune App SDK iOS: länkade ramverk och bibliotek](../media/intune-app-sdk/ios-thread-identities.png)

### <a name="thread-queues"></a>Trådköer

Appar skickar ofta asynkrona och synkrona uppgifter till trådköer. SDK hindrar Grand Central Dispatch-anrop (GCD) och kopplar den aktuella trådidentiteten till de skickade uppgifterna. När uppgifterna är slutförda ändrar SDK tillfälligt trådidentiteten till den identitet som är kopplad till uppgifterna, avslutar uppgifterna och återställer sedan den ursprungliga trådidentiteten.


Eftersom `NSOperationQueue` är byggt ovanpå GCD körs `NSOperations` på trådens identitet vid den tidpunkt då uppgifterna läggs till i `NSOperationQueue`. `NSOperations` eller funktioner som skickas direkt via GCD kan också ändra den aktuella trådidentiteten när de körs. Den här identiteten åsidosätter den identitet som ärvs från den avsändande tråden.

### <a name="file-owner"></a>Filägare

SDK spårar identiteterna för lokala filägare och använder principer på lämpligt sätt. En filägare fastställs när en fil skapas eller när en fil öppnas i trunkerat läge. Ägaren anges som den gällande filuppgiftsidentiteten för den tråd som utför uppgiften.

Appar kan även ange filägaridentiteten explicit genom att använda `IntuneMAMFilePolicyManager`. Appar kan använda `IntuneMAMFilePolicyManager` för att hämta filägaren och ange gränssnittsidentiteten innan filens innehåll visas.

### <a name="shared-data"></a>Delade data

Om appen skapar filer med data från både hanterade och ohanterade användare ansvarar appen för att kryptera den hanterade användarens data. Du kan kryptera data med hjälp av API:erna `protect` och `unprotect` i `IntuneMAMDataProtectionManager`.

Metoden `protect` godkänner en identitet som kan vara en hanterad eller ohanterad användare. Om användaren är hanterad kommer data att krypteras. Om användaren är ohanterad kommer en rubrik att läggas till de data som kodar identiteten, men data krypteras inte. Du kan använda metoden `protectionInfo` för att hämta ägaren för data.

### <a name="share-extensions"></a>Delningstillägg

Om appen har ett delningstillägg går det att hämta ägaren av objektet som delas med hjälp av metoden `protectionInfoForItemProvider` i `IntuneMAMDataProtectionManager`. Om det delade objektet är en fil anger SDK filägaren. Om det delade objektet är data ansvarar appen för att ange filägaren om dessa data sparas i en fil, och för att anropa API:n `setUIPolicyIdentity` innan dessa data visas i gränssnittet.

### <a name="turning-on-multi-identity"></a>Aktivera flera identiteter

Appar anses som standard ha en enda identitet. SDK anger processidentiteten till den registrerade användaren. Aktivera stöd för flera identiteter genom att lägga till en boolesk inställning med namnet `MultiIdentity` och värdet YES (JA) i ordlistan IntuneMAMSettings i appens Info.plist-fil.

> [!NOTE]
> När flera identiteter aktiveras ställs processidentitet, gränssnittssidentitet och trådidentiteter på noll. Appen ansvarar för att ange dem på lämpligt sätt.

### <a name="switching-identities"></a>Växla identitet

* **Appinitierad identitetsväxling**:

    Vid start anses appar med flera identiteter som att de körs under ett okänt och ohanterat konto. Gränssnittet för villkorlig start körs inte och inga principer verkställs på appen. Appen ansvarar för att meddela SDK när identiteten ska ändras. Detta sker normalt när appen ska visa data för ett visst användarkonto.

    Ett exempel är om användaren försöker öppna ett dokument, en postlåda eller en flik i en bärbar dator. Appen måste meddela SDK innan filen, postlådan eller fliken öppnas. Detta görs via API:n `setUIPolicyIdentity` i `IntuneMAMPolicyManager`. Denna API ska anropas oavsett om användaren är hanterad eller inte. Om användaren är hanterad utför SDK kontrollerna för villkorlig start, t.ex. jailbreak-identifiering, PIN-kod och autentisering.

    Resultatet av identitetsväxlingen returneras till appen asynkront via en hanterare för slutförande. Appen ska vänta med att öppna dokumentet, postlådan eller fliken tills en kod om lyckat resultat returneras. Om identitetsväxlingen misslyckas ska appen avbryta uppgiften.

* **SDK-initierad identitetsväxling**:

    Ibland behöver SDK be programmet att växla till en viss identitet. Appar med flera identiteter måste implementera metoden `identitySwitchRequired` i `IntuneMAMPolicyDelegate` för att hantera denna begäran.

    När den här metoden anropas ska appen skicka `IntuneMAMAddIdentityResultSuccess` till hanteraren för slutförande om appen kan hantera begäran om att växla till den angivna identiteten. Om den inte kan hantera växling av identiteten ska appen skicka `IntuneMAMAddIdentityResultFailed` till hanteraren för slutförande.

    Appen behöver inte anropa `setUIPolicyIdentity` som svar på det här anropet. Om SDK behöver att appen växlar till ett ohanterat användarkonto skickas den tomma strängen till `identitySwitchRequired`-anropet.

* **Selektiv rensning**:

    När appen rensas selektivt anropar SDK metoden `wipeDataForAccount` i `IntuneMAMPolicyDelegate`. Appen ansvarar för att ta bort det angivna användarkontot och alla data som är kopplade till det. SDK kan ta bort alla filer som ägs av användaren och gör det om programmet returnerar FALSE från `wipeDataForAccount`-anropet.

    Tänk på att den här metoden anropas från en bakgrundstråd. Appen ska inte returnera något värde förrän alla data för användaren har tagits bort (med undantag för filer om appen returnerar FALSE).

## <a name="test-app-protection-policy-settings-in-xcode"></a>Testa inställningar för appskyddsprincip i Xcode

Innan du testar den Intune-aktiverade appen manuellt i produktion kan du använda en Settings.bundle-fil i Xcode. Då kan du ange appskyddsprinciper för att testa utan att det krävs en anslutning till Intune.

### <a name="enable-policy-testing"></a>Aktivera principtestning

Följ stegen nedan för att aktivera principtestning i Xcode:

1. Se till att vara i en felsökningsversion. Lägg till en Settings.bundle-fil genom att högerklicka på den översta mappen i projektet. Välj **Lägg till** > **Ny fil** på menyn. Under **Resurser** väljer du mallen **Settings Bundle** (Inställningspaket).

2.  Kopiera följande block till filen Settings.bundle/**Root.plist** för felsökningsversionen:
    ```xml
    <key>PreferenceSpecifiers</key>
    <array>
        <dict>
            <key>Type</key>
            <string>PSChildPaneSpecifier</string>
            <key>Title</key>
            <string>MDM Debug Settings</string>
            <key>Key</key>
            <string>MAMDebugSettings</string>
            <key>File</key>
            <string>MAMDebugSettings</string>
        </dict>
    </array>
    ```

3. I ordlistan **IntuneMAMSettings** i appens Info.plist lägger du till det booleska värdet "DebugSettingsEnabled." Ange värdet för DebugSettingsEnabled som "YES" (JA).



### <a name="app-protection-policy-settings"></a>Inställningar för appskyddsprincip

Tabellen nedan beskriver de inställningar för appskyddsprincip som du kan testa med MAMDebugSettings.plist. Lägg till en inställning i MAMDebugSettings.plist om du vill aktivera den.

| Principinställningsnamn | Beskrivning | Möjliga värden |
| -- | -- | -- |
| AccessRecheckOfflineTimeout | Hur lång tid i minuter som appen kan vara offline innan Intune blockerar appen från att startas eller återupptas om autentisering är aktiverat. | Ett heltal som är större än 0 |
|    AccessRecheckOnlineTimeout | Hur lång tid i minuter som appen kan köras innan användaren uppmanas att ange PIN-kod eller autentisering vid start eller återupptagning (om autentisering eller PIN-kod för åtkomst är aktiverat). | Ett heltal som är större än 0 |
| AppSharingFromLevel | Anger vilka appar den här appen kan ta emot data från. | 0 = |
## <a name="ios-best-practices"></a>Bästa metoder för iOS

Följande är rekommenderade metoder när du utvecklar för iOS:

* iOS-filsystemet är skiftlägeskänsligt. Kontrollera att skiftläget är korrekt för filnamn som `libIntuneMAM.a` och `IntuneMAMResources.bundle`.

* Om Xcode har problem med att hitta `libIntuneMAM.a` kan du åtgärda problemet genom att lägga till sökvägen till detta bibliotek i sökvägarna för länkare.

## <a name="faqs"></a>Vanliga frågor och svar


**Är alla API:erna adresserbara via inbyggd Swift eller samverkan mellan Objective-C och Swift?**

Intune App SDK API:erna finns endast i Objective-C och har inte stöd för **inbyggd** Swift. Swift-samverkan med Objective-C krävs.


**Måste alla användare av programmet registreras med APP-WE-tjänsten?**

Nej. Det är i själva verket bara arbets- eller skolkonton som ska registreras med Intune App SDK. Apparna ansvarar för att fastställa om ett konto används i arbets- eller skolsammanhang.   

**Hur är det med användare som redan har loggat in i programmet? Behöver de registreras?**

Programmet ansvarar för att registrera användare efter att de har autentiserats. Programmet ansvarar också för att registrera eventuella befintliga konton som kan ha funnits innan programmet hade MAM-funktioner utan MDM.   

Programmet ska använda metoden `registeredAccounts:` för att göra detta. Den här metoden returnerar en NSDictionary som innehåller alla konton som är registrerade i Intune MAM-tjänsten. Om några befintliga konton i programmet inte finns i listan ska programmet notera och registrera dessa konton via `registerAndEnrollAccount:`.

**Hur ofta gör SDK nya registreringsförsök?**

SDK gör automatiskt nya försök med 24-timmarsintervall för alla registreringar som tidigare har misslyckats. SDK gör detta för att säkerställa att om en användares organisation har aktiverat MAM efter att användaren loggade in i programmet kommer användaren att registreras och ta emot principer.

SDK slutar att försöka igen när det ser att en användare har registrerat programmet. Det beror på att bara en användare kan registrera ett program vid en viss tidpunkt. Om användaren avregistreras påbörjas nya försök igen med samma 24-timmarsintervall.

**Varför måste användaren vara avregistrerad?**

SDK ska utföra följande åtgärder i bakgrunden med jämna mellanrum:

 - Om programmet inte har registrerats än görs ett försök att registrera alla noterade konton var 24:e timme.
 - Om programmet har registrerats kontrollerar SDK om det finns uppdateringar av appskyddsprincipen var 8:e timme.

Om en användare avregistreras meddelas SDK att användaren inte längre kommer att använda programmet och SDK kan stoppa alla regelbundna händelser för det användarkontot. Det löser även ut avregistrering av appen och selektiv rensning, vid behov.

**Ska jag ställa in flaggan doWipe på sant i avregistreringsmetoden?**

Den här metoden ska anropas innan användaren loggas ut från programmet.  Om användarens data tas bort från programmet som en del av utloggningen kan `doWipe` ställas in på falskt. Men om programmet inte tar bort användarens data ska `doWipe` ställas in på sant så att SDK kan radera data.

**Finns det andra sätt att avregistrera ett program?**

Ja, IT-administratören kan skicka ett kommando för selektiv rensning till programmet. Då avregistreras användaren och användarens data rensas. SDK hanterar detta scenario automatiskt och skickar en avisering via ombudsmetoden för avregistrering.



## <a name="submit-your-app-to-the-app-store"></a>Skicka appen till App Store

Både de statiska biblioteks- och ramverksversionerna av Intune App SDK är universella binärfiler. Det innebär att de har kod för alla enhets- och simulatorarkitekturer. Apple avvisar appar som skickas till App Store om de innehåller simulatorkod. Vid kompilering mot det statiska biblioteket för enhetsspecifika versioner rensar länkaren automatiskt bort simulatorkoden. Följ stegen nedan för att se till att all simulatorkod tas bort innan du överför appen till App Store.

1. Kontrollera att `IntuneMAM.framework` finns på skrivbordet.

2. Kör dessa kommandon:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    Det första kommandot rensar bort simulatorarkitekturerna från ramverkets DYLIB-fil. Det andra kommandot kopierar den enhetsspecifika DYLIB-filen tillbaka till ramverkskatalogen.

