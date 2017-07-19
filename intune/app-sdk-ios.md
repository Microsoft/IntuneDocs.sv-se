---
title: "Utvecklarhandbok för Microsoft Intune App SDK för iOS"
description: "Med Microsoft Intune App SDK för iOS kan du lägga till principer för appskydd i form av hantering av mobilappar(MAM) med Intune i din iOS-app."
keywords: 
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0fb1d52a97a03609ddefb94caf707bd8cbee8f12
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Utvecklarhandbok för Microsoft Intune App SDK för iOS

> [!NOTE]
> Börja gärna med att läsa artikeln [Get Started with Intune App SDK Guide](app-sdk-get-started.md) (Kom igång med Intune App SDK). Den här guiden beskriver hur du förbereder dig för integreringen på de plattformar som stöds.

Med Microsoft Intune App SDK för iOS kan du lägga till Intune-appskyddsprinciper (även kallade **APP**- eller **MAM**-principer) i din iOS-app. Ett MAM-aktiverat program är ett program som är integrerat med Intune App SDK. Det kan användas av IT-administratörer för att distribuera appskyddsprinciper till din mobilapp om Intune aktivt hanterar appen.

## <a name="prerequisites"></a>Krav

* Du behöver en Mac OS-dator som kör OS X 10.8.5 eller senare och som har Xcode-version 8 eller senare installerad.

* Din app måste vara anpassad för iOS 9 eller senare.

* Läs [licensvillkoren för Intune App SDK för iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf). Skriv ut och behåll en kopia av licensvillkoren för framtida referens. Genom att ladda ned och använda Intune App SDK för iOS samtycker du till de här licensvillkoren.  Om du inte accepterar villkoren har du inte rätt att använda programvaran.

* Hämta filerna för Intune App SDK för iOS på [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk"></a>Vad innehåller SDK?

Intune App SDK för iOS innehåller ett statiskt bibliotek, resursfiler, API-rubriker, en plist-fil med inställningar för felsökning samt ett konfigurationsverktyg. Mobilappar kan ibland endast innehålla resursfiler och statiskt länka till biblioteken för att tillämpa principer. Avancerade MAM-funktioner i Intune aktiveras via API:er.

Den här guiden beskriver hur du använder följande komponenter i Intune App SDK för iOS:

* **libIntuneMAM.a**: Det statiska Intune App SDK-biblioteket. Om appen inte använder tillägg kan du länka detta bibliotek till projektet för att möjliggöra hantering av mobilprogram i Intune med appen.

* **IntuneMAM.framework**: Intune App SDK-ramverket. Länka detta ramverk till projektet för att möjliggöra hantering av mobilprogram i Intune med appen. Använd ramverket i stället för det statiska biblioteket om appen använder tillägg, så att projektet inte skapar flera kopior av det statiska biblioteket.

* **IntuneMAMResources.Bundle**: Ett resurspaket som har resurser som SDK är beroende av.

* **Rubriker**: visar API:er för Intune App SDK. Om du använder ett API måste du inkludera huvudfilen som innehåller API:et. Följande rubrikfiler innehåller API-funktionsanrop som krävs för att aktivera funktionerna i Intune App SDK:

    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h


## <a name="how-the-intune-app-sdk-works"></a>Hur Intune App SDK fungerar

Målet med Intune App SDK för iOS är att lägga till hanteringsfunktioner i iOS-program med minimala kodändringar. Färre kodändringar innebär kortare tid innan produkten är klar, samtidigt som mobilappen blir mer konsekvent och stabil.


## <a name="build-the-sdk-into-your-mobile-app"></a>Skapa SDK i din mobilapp

Följ dessa steg för att aktivera Intune App SDK:

1. **Alternativ 1 (rekommenderas)**: Länken `IntuneMAM.framework` till projektet. Dra `IntuneMAM.framework` till listan **inbäddade binära** i projektmålet.

    > [!NOTE]
    > Om du använder ramverket måste du ta bort simuleringsarkitekturen manuellt från det universella ramverket innan du skickar in appen till App Store. Se [Skicka in din app till App Store](#Submit-your-app-to-the-App-Store) för mer information.

2. **Alternativ 2**: Länk till biblioteket `libIntuneMAM.a`. Dra `libIntuneMAM.a`-biblioteket till listan med **länkade ramverk och bibliotek** i projektets målkatalog.

    ![Intune App SDK iOS: länkade ramverk och bibliotek](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    > [!NOTE]
    > Om du planerar att lansera appen i App Store bör du använda den version av `libIntuneMAM.a` som skapats för lanseringen, alltså inte felsökningsversionen. Slutversionen ligger i **slutversionsmappen**. Felsökningsversionen innehåller utförliga data som hjälper till att felsöka problem med Intune App SDK.

    Lägg till `-force_load {PATH_TO_LIB}/libIntuneMAM.a` i någon av följande och ersätt `{PATH_TO_LIB}` med platsen för Intune App SDK:
      * Projektets konfigurationsinställning för `OTHER_LDFLAGS`
      * Användargränssnittets **Other Linker Flags** (Andra länkarflaggor)

        > [!NOTE]
        > Leta reda på `PATH_TO_LIB` genom att välja filen `libIntuneMAM.a` och välja **Get Info** (Hämta information) från menyn **Arkiv**. Kopiera och klistra in informationen om **Var** (sökvägen) från avsnittet **Allmänt** i fönstret **Information**.

3. Lägg till dessa iOS-ramverk i projektet:
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.TBD
    * libc ++ .tbd
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework


4. Lägg till `IntuneMAMResources.bundle`-resurspaketet i projektet genom att dra resurspaketet till **Copy Bundle Resources** (Kopiera paketresurser) i **Build Phases** (Versionsfaser).

    ![Intune App SDK iOS: kopiera paketresurser](./media/intune-app-sdk-ios-copy-bundle-resources.png)

5. Om mobilappen definierar en main nib- eller storyboard-fil i Info.plist-filen tar du bort fältet eller fälten för **Main Storyboard** eller **Main Nib**. Gå till Info-plist och klistra in dessa fält samt deras motsvarande värden under en ny ordlista som heter **IntuneMAMSettings** med följande namn, i tillämpliga fall:
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad
    > [!NOTE]
  > Om mobilappen inte definierar någon main nib eller storyboard-fil i Info.plist-filen är dessa inställningar inte obligatoriska.

    Du kan visa filen Info.plist i obearbetat format (för att visa nyckelnamnen) genom att högerklicka någonstans i dokumentets brödtext och ändra visningstypen till **Show Raw Keys/Values** (Visa obearbetade nycklar/värden).

6. Aktivera delning av nyckelringar (om det inte redan är aktiverat) genom att välja **Funktioner** i varje projektmål och aktivera reglaget för **delning av nyckelringar**. Delning av nyckelringar krävs för att du ska kunna fortsätta till nästa steg.

  > [!NOTE]
    > Etableringsprofilen måste ha stöd för nya värden för delning av nyckelringar. Åtkomstgrupper för nyckelringar ska ha stöd för jokertecken. Du kan bekräfta detta genom att öppna filen .mobileprovision i en textredigerare, söka efter **keychain-access-groups** och se till att du har ett jokertecken. Exempel:
    ```xml
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```

7. När du har aktiverat delning av nyckelringar följer du dessa steg för att skapa en separat åtkomstgrupp där data i Intune App SDK kommer att sparas. Du kan skapa en åtkomstgrupp för nyckelringar med hjälp av användargränssnittet eller med behörighetsfilen. Om du använder användargränssnittet för att skapa gruppen med nyckelhanterare, följer du stegen nedan:

    1. Om mobilappen inte har definierat några åtkomstgrupper för nyckelringar lägger du till appens paket-ID som den första gruppen.

    2. Lägg till den delade gruppen med nyckelhanterare `com.microsoft.intune.mam` till dina befintliga åtkomstgrupper. Intune App SDK använder den här åtkomstgruppen för att lagra data.

    3. Lägg till `com.microsoft.adalcache` i dina befintliga åtkomstgrupper.

        4. Lägg till `com.microsoft.workplacejoin` i dina befintliga åtkomstgrupper.
            ![Intune App SDK iOS: delning av nyckelhanterare](./media/intune-app-sdk-ios-keychain-sharing.png)

    5. Lägg till åtkomstgruppen för nyckelhanterare med `$(AppIdentifierPrefix)` i behörighetsfilen om du använder behörighetsfilen för att skapa en åtkomstgrupp för nyckelhanterare. Exempel:

            * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
            * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    > [!NOTE]
    > En behörighetsfil är en XML-fil som är unik för ditt mobila program. Den används för att ange särskilda behörigheter och funktioner i din iOS-app.

7. Om appen definierar URL-scheman i filen Info.plist lägger du till ytterligare ett schema med suffixet `-intunemam` för varje URL-schema.

8. Mobilappar som utvecklas för iOS 9 och senare måste inkludera varje protokoll som appen skickar till `UIApplication canOpenURL` i matrisen `LSApplicationQueriesSchemes` i appens Info.plist-fil. Lägg dessutom till ett nytt protokoll med `-intunemam` för varje nytt protokoll som listas. Du måste även inkludera `http-intunemam`, `https-intunemam`och `ms-outlook-intunemam` i matrisen.

9. Om appen har definierade appgrupper i sina behörigheter, lägger du till dessa grupper i ordlistan **IntuneMAMSettings** under nyckeln `AppGroupIdentifiers` som en matris med strängar.



## <a name="configure-azure-active-directory-authentication-library-adal"></a>Konfigurera Azure Active Directory Authentication Library (ADAL)

Intune App SDK använder [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) för autentisering och villkorliga startscenarier. Den förlitar sig även på ADAL för att registrera användarens identitet i MAM-tjänsten för hantering utan enhetsregistreringsscenarier.

Normalt kräver ADAL att appar registreras med Azure Active Directory (AAD) och erhåller ett unikt ID (klient-ID) och andra identifierare, för att garantera säkerheten i de token som appen beviljats. Såvida inget annat anges, använder Intune App SDK standardvärden för registrering när Azure AD kontaktas.  

Om appen redan använder ADAL för att autentisera användare, måste appen använda befintliga registreringsvärden och åsidosätta standardvärdena för Intune App SDK. Detta garanterar att användare inte uppmanas att autentisera sig två gånger (en gång av Intune App SDK och en gång av appen).

### <a name="recommendations"></a>Rekommendationer

Vi rekommenderar att din app länkar till den [senaste versionen av ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) på sin mastergren. Intune App SDK använder för närvarande hanterardelen av ADAL för att ge stöd för appar som kräver villkorlig åtkomst. (De här apparna förlitar sig därför på Microsoft Authenticator-appen.) Men SDK är fortfarande kompatibel med huvuddelen av ADAL. Använd den del som är lämplig för din app.

### <a name="link-to-adal-binaries"></a>Länk till ADAL-binärfiler

Följ stegen nedan för att länka din app till ADAL-binärfilerna:

1. Hämta [Azure Active Directory Authentication Library (ADAL) för Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) från GitHub. Följ sedan [instruktionerna](https://github.com/AzureAD/azure-activedirectory-library-for-objc/blob/master/README.md) om hur du hämtar ADAL med Git-undermoduler eller CocoaPods.

2. Inkludera resurspaketet `ADALiOSBundle.bundle` i projektet genom att dra resurspaketet till **Copy Bundle Resources** (Kopiera paketresurser) i **Build Phases** (Versionsfaser).

3. Lägg till `-force_load {PATH_TO_LIB}/libADALiOS.a` i projektets `OTHER_LDFLAGS`-konfigurationsinställning eller **Other Linker Flags** (Andra länkarflaggor) i användargränssnittet. `PATH_TO_LIB` ska ersättas med platsen för ADAL-binärfilerna.



### <a name="share-the-adal-token-cache-with-other-apps-signed-with-the-same-provisioning-profile"></a>Vill du dela ADAL-tokencache med andra appar som signerats med samma etableringsprofil?**

Följ anvisningarna nedan om du vill dela ADAL-tokens mellan appar som signerats med samma etableringsprofil:

1. Om appen inte har definierat några åtkomstgrupper för nyckelringar lägger du till appens paket-ID som den första gruppen.

2. Aktivera enkel inloggning (SSO) med ADAL genom att lägga till åtkomstgrupperna `com.microsoft.adalcache` och `com.microsoft.workplacejoin` i nyckelringens rättigheter.

3. Om du ställer in nyckelringsgruppen för ADAL-delad cache ser du till att den är inställd på `<app_id_prefix>.com.microsoft.adalcache`. ADAL ställer in detta åt dig förutsatt att du inte åsidosätter det. Om du vill ange en anpassad nyckelringsgrupp som ersätter `com.microsoft.adalcache` anger du det i Info.plist-filen under IntuneMAMSettings med hjälp av nyckeln `ADALCacheKeychainGroupOverride`.

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Konfigurera ADAL-inställningar för Intune App SDK

Om din app redan använder ADAL för autentisering och har egna ADAL-inställningar, kan du tvinga Intune App SDK att använda samma inställningar under autentiseringen mot Azure Active Directory. Detta garanterar att appen inte frågar användaren om autentisering två gånger. Se [Konfigurera inställningar för Intune App SDK](#configure-settings-for-the-intune-app-sdk) för information om hur du fyller i följande inställningar:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Om din app redan använder ADAL, krävs följande konfigurationer:

1. I Info.plist-filen i projektet, under ordlistan **IntuneMAMSettings** med nyckelnamnet `ADALClientId`, anger du det klient-ID som ska användas för ADAL-anrop.

2. Ange också Azure AD-utfärdare under ordlistan **IntuneMAMSettings** med nyckelnamnet `ADALAuthority`.

3. Under ordlistan **IntuneMAMSettings** med nyckelnamnet `ADALRedirectUri` anger du också den omdirigerings-URI som ska användas för ADAL-anrop. Du kan även behöva ange `ADALRedirectScheme` beroende på formatet för appens omdirigerings-URI.


Du kan dessutom åsidosätta Azure AD-utfärdarens URL med en klientspecifik URL som anges vid körning. Gör detta genom att ange egenskapen `aadAuthorityUriOverride` på instansen `IntuneMAMPolicyManager`.

> [!NOTE]
> Inställning av AAD-utfärdarens URL krävs för [APP utan enhetsregistrering](#App-protection-policy-without-device-enrollment) för att tillåta att SDK återanvänder den ADAL-uppdateringstoken som hämtas av appen.

SDK fortsätter att använda denna utfärdar-URL för principuppdatering och eventuella efterföljande registreringsbegäranden såvida inte värdet rensas eller ändras.  Det är därför viktigt att rensa värdet när en hanterad användare loggar ut från appen och återställa det när en ny hanterad användare loggar in.

### <a name="if-your-app-does-not-use-adal"></a>Om din app inte använder ADAL

Intune App SDK tillhandahåller standardvärden för ADAL-parametrar och hanterar autentisering mot Azure AD om din app inte använder ADAL. Du behöver inte ange några värden för ADAL-inställningarna ovan.

## <a name="app-protection-policy-without-device-enrollment"></a>Appskyddsprincip utan enhetsregistrering

### <a name="overview"></a>Översikt
Med Intune-appskyddsprincip utan enhetsregistrering, så kallad **APP-WE** eller MAM-WE, kan appar hanteras av Intune utan att enheten behöver registreras i Intunes hantering av mobila enheter (MDM). För att stödja den här nya funktionerna, måste appen registrera användarkonton som ska hanteras. Följ dessa steg för att använda de nya API:erna:

1. Använd den senaste versionen av Intune App SDK som stöder hantering av appar med eller utan enhetsregistrering.

2. Lägg till IntuneMAMEnrollment.h i alla filer som kommer att anropa API:erna.

### <a name="register-user-accounts"></a>Registrera användarkonton

En app kan ta emot appskyddsprinciper från Intune-tjänsten om appen registreras med tjänsten APP-WE för ett angivet användarkonto. Det är appens ansvar att registrera eventuella nyligen inloggade användare i SDK. När det nya användarkontot har autentiserats måste appen anropa `registerAndEnrollAccount`-metoden i Headers/IntuneMAMEnrollment.h:

```objc
/**


 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;

```
Genom att anropa `registerAndEnrollAccount`-metoden registrerar SDK användarkontot och försöker registrera appen för det här kontot. Om registreringen misslyckas av någon anledning försöker SDK genomföra registreringen igen automatiskt 24 timmar senare. Appen kan i felsökningssyfte ta emot aviseringar om resultaten av eventuella registreringsbegäranden via ett ombud.

När detta API har anropats kan appen fortsätta att fungera som vanligt. Om registreringen lyckas meddelar SDK användaren att appen behöver startas om. Användaren kan då starta om appen omedelbart.

### <a name="deregister-user-accounts"></a>Avregistrera användarkonton

Innan en användare loggas ut från en app bör appen avregistrera användaren från SDK. Detta säkerställer följande:

1. Nya registreringsförsök sker inte längre för användarens konto.

2. Appskyddsprincipen tas bort.

3. Om appen startar en selektiv rensning (valfritt) raderas eventuella företagsdata.

Innan användaren loggas ut måste appen anropa följande API i `Headers/IntuneMAMEnrollment.h`:

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

Den här metoden måste anropas innan användarkontots Azure AD-token tas bort. SDK behöver användarens ADD-token för att göra specifika begäranden till APP-WE-tjänsten för användarens räkning.

Om appen ska ta bort användarens företagsdata på egen hand ska `doWipe`-flaggan anges till falskt. Annars kan appen få SDK att initiera en selektiv rensning. Detta resulterar i ett anrop till appens ombud för selektiv rensning.

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

### <a name="apps-that-do-not-use-adal"></a>Appar som inte använder ADAL

En app som inte loggar in användaren med ADAL kan fortfarande ta emot appskyddsprinciper från Intune-tjänsten genom att anropa API:t och låta SDK hantera den autentiseringen. Appar bör använda den här metoden när de inte har autentiserat en användare med Azure AD men ändå måste hämta appskyddsprinciper för att skydda data. Ett exempel är om en annan autentiseringstjänst används för inloggning i en app, eller om appen inte stöder inloggning över huvud taget. Programmet måste anropa `loginAndEnrollAccount`-metoden i Headers/IntuneMAMEnrollment.h för att göra detta:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;

```

Genom att anropa den här metoden frågar SDK användaren om autentiseringsuppgifter om ingen befintlig token kan hittas. SDK försöker därefter registrera appen med APP-WE-tjänsten för det angivna användarkontot. Metoden kan anropas med "noll" som identitet. I sådant fall registrerar SDK med den befintliga hanterade användaren på enheten eller frågar användaren om ett användarnamn om det inte går att hitta en befintlig användare.

Om registreringen misslyckas bör appen överväga att anropa detta API igen vid ett senare tillfälle, beroende på detaljerna kring felet. Appen kan ta emot [aviseringar](#Status-result-and-debug-notifications) om resultaten av eventuella registreringsbegäranden via ett ombud.

När detta API har anropats kan appen fortsätta att fungera som vanligt. Om registreringen lyckas meddelar SDK användaren att appen behöver startas om.

## <a name="status-result-and-debug-notifications"></a>Status-, resultat- och felsökningsmeddelanden

Appen kan ta emot status-, resultat- och felsökningsmeddelanden om följande begäranden till Intunes MAM-tjänst:

 - Begäran om registrering
 - Begäran om principuppdatering
 - Begäran om avregistrering

Meddelanden visas via delegerade metoder i `Headers/IntuneMAMEnrollmentDelegate.h`:

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

Dessa ombudsmetoder returnerar ett `IntuneMAMEnrollmentStatus`-objekt som innehåller följande information:

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

## <a name="app-restart"></a>Omstart av app

När en app tar emot appskyddsprinciper för första gången måste den startas om för att tillämpa obligatoriska hookar. För att meddela appen att en omstart krävs tillhandahåller SDK en delegeringsmetod i Headers/IntuneMAMPolicyDelegate.h.

```objc
 - (BOOL) restartApplication
```
Returvärdet för den här metoden talar om för SDK om programmet ska hantera den omstart som krävs:   

 - Om sant returneras måste programmet hantera omstarten.   

 - Om falskt returneras startar SDK om programmet när den här metoden returneras. SDK visar direkt en dialogruta som ber användaren att starta om programmet.

## <a name="customize-your-apps-behavior"></a>Ändra appens beteende

Intune App SDK har flera API: er som du kan använda för att hämta information om den Intune-appskyddsprincip som distribueras till appen. Du kan använda informationen för att ändra appens beteende. De flesta inställningar för appskyddsprinciper tillämpas automatiskt av SDK och inte av appen. Den enda inställning som appen ska implementera är Spara som-kontrollen.

### <a name="get-app-protection-policy"></a>Hämta appskyddsprincipen

#### <a name="intunemampolicymanagerh"></a>IntuneMAMPolicyManager.h
Klassen IntuneMAMPolicyManager visar Intune-appskyddsprincipen som distribuerats till programmet. Klassen visar främst de API: er som är användbara för att [aktivera flera identiteter](#-enable-multi-identity-optional).

#### <a name="intunemampolicyh"></a>IntuneMAMPolicy.h
Klassen IntuneMAMPolicy visar Intune-appskyddsprincipen som distribuerats till programmet. De flesta principinställningar som visas i den här klassen tillämpas av SDK, men du kan alltid anpassa din apps beteende baserat på hur principinställningarna tillämpas.

Den här klassen visar vissa API: er som krävs för att implementera spara som-kontroller. Detta beskrivs i nästa avsnitt.

### <a name="implement-save-as-controls"></a>Implementera spara som-kontroller

Intune låter IT-administratörer välja vilka lagringsplatser som en hanterad app kan spara data till. Appar kan fråga Intune App SDK efter tillåtna lagringsplatser med hjälp av **isSaveToAllowedForLocation**-API:et, som definieras i **IntuneMAMPolicy.h**.

Innan appar kan spara hanterade data i molnlagring eller på en lokal plats måste de kontrollera med **isSaveToAllowedForLocation**-API:et för att se om IT-administratören tillåter att data sparas där.

När appar använder **isSaveToAllowedForLocation**-API:et måste de ange lagringsplatsens UPN, om det är tillgängligt.

#### <a name="supported-save-locations"></a>Lagringsplatser som stöds

**isSaveToAllowedForLocation**-API:et tillhandahåller konstanter för att kontrollera om IT-administratören tillåter att data sparas på följande platser (som definieras i IntuneMAMPolicy.h):

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Apparna bör använda konstanterna i **isSaveToAllowedForLocation**-API:et för att kontrollera om data kan sparas till platser som betraktas som ”hanterade”, som till exempel OneDrive för företag, eller platser som är ”personliga”. API:et bör dessutom användas när appen inte kan kontrollera om en plats är ”hanterad” eller ”personlig”.

Platser som är "personliga" representeras av `IntuneMAMSaveLocationOther`-konstanten.

`IntuneMAMSaveLocationLocalDrive`-konstanten bör användas när appen sparar data till en plats på den lokala enheten.

## <a name="configure-settings-for-the-intune-app-sdk"></a>Konfigurera inställningar för Intune App SDK

Du kan använda ordlistan **IntuneMAMSettings** i filen Info.plist i programmet för att installera och konfigurera Intune App SDK. Om ordlistan IntuneMAMSettings inte visas i filen Info.plist bör du skapa en ordlista i din app Info.plist med fältnamnet "IntuneMAMSettings."

Du kan lägga till nyckel-/värde-rader för konfigurationsinställningar för att konfigurera SDK under ordlistan IntuneMAMSettings. Följande tabell är en lista över konfigurationer som stöds.

Några av de här inställningarna kan ha beskrivits i föregående avsnitt och vissa gäller inte för alla appar.

Inställningar  | Typ  | Definition | Obligatoriskt?
--       |  --   |   --       |  --
ADALClientId  | Sträng  | Appens klient-ID för Azure AD. | Krävs om appen använder ADAL. |
ADALAuthority | Sträng | Appens Azure AD-auktoritet används. Du bör använda din egen miljö där AAD-konton har konfigurerats. | Krävs om appen använder ADAL. Om detta värde saknas används ett Intune-standardvärde.|
ADALRedirectUri  | Sträng  | Appens omdirigerings-URI för Azure AD. | ADALRedirectUri eller ADALRedirectScheme krävs om appen använder ADAL.  |
ADALRedirectScheme  | Sträng  | Appens omdirigeringsschema för Azure AD. Detta kan användas i stället för ADALRedirectUri om programmets omdirigerings-URI har formatet `scheme://bundle_id`. | ADALRedirectUri eller ADALRedirectScheme krävs om appen använder ADAL. |
ADALLogOverrideDisabled | Boolesk  | Anger om SDK dirigerar alla ADAL-loggar (inklusive eventuella ADAL-anrop från appen) till den egna loggfilen. Standardvärdet är NO (NEJ). Ange YES (JA) om appen ska ange egna återanrop i ADAL-loggen. | Valfritt. |
ADALCacheKeychainGroupOverride | Sträng  | Anger nyckelringsgruppen som ska användas för ADAL-cache i stället för ”com.microsoft.adalcache”. Observera att detta inte har app-id-prefixet. Det läggs till i den angivna strängen vid körning. | Valfritt. |
AppGroupIdentifiers | Strängmatris  | Matris med appgrupper från appens behörigheter i avsnittet com.apple.security.application-groups  | Krävs om appen använder programgrupper. |
ContainingAppBundleId | Sträng | Anger paket-ID:t för programmet som ingår i tillägget. | Krävs för iOS-tillägg. |
DebugSettingsEnabled| Boolesk | Om detta är inställt på JA kan testprinciper i inställningspaketet användas. Program bör *inte* levereras med den här inställningen aktiverad. | Valfritt. |
MainNibFile<br>MainNibFile~ipad  | Sträng  | Den här inställningen ska ha programmets namn på filen för Main Nib.  | Krävs om programmet definierar MainNibFile i filen Info.plist. |
MainStoryboardFile<br>MainStoryboardFile~ipad  | Sträng  | Den här inställningen ska ha programmets namn på filen för Main Storyboard. | Krävs om programmet definierar UIMainStoryboardFile i filen Info.plist. |
AutoEnrollOnLaunch| Boolesk| Anger om programmet ska försöka registrera sig automatiskt vid start om en befintlig hanterad identitet identifieras och den inte redan har gjort det. Standardvärdet är NO (NEJ). <br><br> Kommentarer: Om ingen hanterad identitet hittas eller om det inte finns en tillgänglig giltig token för identiteten i ADAL-cachen, misslyckas registreringsförsöket utan att användaren uppmanas att ange autentiseringsuppgifter, om inte MAMPolicyRequired också är inställt på YES (JA) för appen. | Valfritt. |
MAMPolicyRequired| Boolesk| Anger om appen kommer att blockeras från att starta om appen inte har en Intune-appskyddsprincip. Standardvärdet är NO (NEJ). <br><br> Obs! Appar kan inte skickas till App Store om MAMPolicyRequired är inställt på YES (JA). Om du ställer in MAMPolicyRequired till YES (JA) bör även AutoEnrollOnLaunch ha värdet YES (JA). | Valfritt. |
MAMPolicyWarnAbsent | Boolesk| Anger om appen kommer att varna användaren under start om appen inte har en Intune-appskyddsprincip. <br><br> Obs! Användare kommer fortfarande att kunna använda appen utan en princip när varningen har ignorerats. | Valfritt. |
MultiIdentity | Boolesk| Anger om appen är multiidentitetsmedveten. | Valfritt. |
SplashIconFile <br>SplashIconFile~ipad | Sträng  | Anger filen för Intunes ikon för välkomstskärmen (startskärm). | Valfritt. |
SplashDuration | Antal | Kortaste tid i sekunder som startskärmen för Intune visas när programmet startas. Standardvärdet är 1,5. | Valfritt. |
BackgroundColor| Sträng| Anger bakgrundsfärgen för start- och PIN-kodsskärmarna. Godkänner en hexadecimal RGB-sträng med formatet #XXXXXX, där X kan vara något mellan 0–9 eller A–F. Pundtecknet kan utelämnas.   | Valfritt. Standardinställningen är ljusgrått. |
ForegroundColor| Sträng| Anger förgrundsfärgen för start- och PIN-kodsskärmarna, till exempel textfärg. Godkänner en hexadecimal RGB-sträng med formatet #XXXXXX, där X kan vara något mellan 0–9 eller A–F. Pundtecknet kan utelämnas.  | Valfritt. Standardinställningen är svart. |
AccentColor | Sträng| Anger accentfärgen för PIN-kodsskärmen, till exempel textfärg på knappar och markeringsfärg för rutor. Godkänner en hexadecimal RGB-sträng med formatet #XXXXXX, där X kan vara något mellan 0–9 eller A–F. Pundtecknet kan utelämnas.| Valfritt. Standardinställningen är systemblått. |
MAMTelemetryDisabled| Boolesk| Anger om SDK inte ska skicka några telemetridata till serverdelen.| Valfritt. |

> [!NOTE]
> Om din app ska lanseras på App Store måste `MAMPolicyRequired` anges till "NO" enligt App Stores standarder.

## <a name="enabling-mam-targeted-configuration-for-your-ios-applications"></a>Aktivera MAM-riktad konfiguration för iOS-appar
Med hjälp av en MAM-riktad konfiguration kan en app att ta emot konfigurationsdata via Intune App SDK. Dataformat och eventuella varianter av dessa data måste definieras och kommuniceras till Intune-kunderna av ägaren/programutvecklaren. Intune-administratörerna kan rikta in och distribuera konfigurationsdata via Intune Azure-konsolen. Appar som deltar i MAM-riktad konfiguration kan tillhandahållas MAM-riktade konfigurationsdata via MAM-tjänsten fr.o.m. Intune App SDK för iOS (v 7.0.1). Programmets konfigurationsdata push-överförs med vår MAM-tjänst direkt till appen i stället för via MDM-kanalen. Intune App SDK tillhandahåller en klass för att komma åt data som hämtats från dessa konsoler. Överväg att ha följande som förutsättningar: <br>
* Appen måste vara MAM-WE-registrerad innan du kan komma åt användargränssnittet för MAM-riktad konfiguration. Mer information om MAM-WE finns i[App protection policy without device enrollment in the Intune App SDK guide](https://docs.microsoft.com/en-us/intune/app-sdk-ios#app-protection-policy-without-device-enrollment) (appskyddsprincip utan enhetsregistrering i Intune App SDK-guiden).
* Inkludera ```IntuneMAMAppConfigManager.h``` i appens källfil.
* Anropa ```[[IntuneMAMAppConfig instance] appConfigForIdentity:]``` för åtkomst till App Config-objektet.
* Anropa lämplig väljare för ```IntuneMAMAppConfig```-objektet. Om appnyckeln är en sträng t.ex. ska du använda ```stringValueForKey``` eller ```allStringsForKey```. Filen ```IntuneMAMAppConfig.h header``` innehåller information om returvärden/felvillkor.

Mer information om funktionerna i Graph API med avseende på MAM-riktade konfigurationsvärden, finns i [Graph API-referens för MAM-riktad konfiguration](https://graph.microsoft.io/en-us/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create). <br>

Mer information om hur du skapar en MAM-riktad appkonfigurationsprincip i iOS finns i avsnittet om MAM-riktad appkonfiguration i [How to use Microsoft Intune app configuration policies for iOS](https://docs.microsoft.com/en-us/intune/app-configuration-policies-use-ios) (använda Microsoft Intune-appkonfigurationsprinciper för iOS).

## <a name="telemetry"></a>Telemetri

Som standard loggar Intune App SDK för iOS telemetridata vid följande användningshändelser. Dessa data skickas till Microsoft Intune.

* **Appstart**: För att hjälpa Microsoft Intune att få veta mer om MAM-aktiverad appanvändning efter hanteringstyp (MAM med MDM, MAM utan MDM-registrering osv.).

* **Registreringsanrop**: För att hjälpa Microsoft Intune att förstå lyckade resultat och andra typer av resultatstatistik för registreringsanrop som initierats från klienten.

> [!NOTE]
> Om du väljer att inte skicka Intune App SDK-telemetridata till Microsoft Intune från din mobilapp måste du inaktivera Intune App SDK-telemetriinsamlingen. Ställ in egenskapen `MAMTelemetryDisabled` på Ja i IntuneMAMSettings-ordlistan.

## <a name="enable-multi-identity-optional"></a>Aktivera flera identiteter (valfritt)

Som standard tillämpar SDK en princip på appen som helhet. Multiidentitet är en MAM-funktion som du kan aktivera för att tillämpa en princip på nivån per identitet. Detta kräver mer appdeltagande än andra MAM-funktioner.

Appen måste meddela app-SDK när den har för avsikt att ändra den aktiva identiteten. SDK meddelar även appen när en identitetsändring krävs. För närvarande stöds endast en hanterad identitet. När användaren registrerar enheten eller appen använder SDK den här identiteten och ser den som primär hanterad identitet. Andra användare i appen behandlas som ej hanterade med obegränsade principinställningar.

Tänk på att en identitet endast definieras som en sträng. Identiteter är skiftlägeskänsliga. Begäranden till SDK om en identitet kanske inte returnerar samma gemener och versaler som användes när identiteten skapades.

### <a name="identity-overview"></a>Översikt över identitet

En identitet är helt enkelt användarnamnet för ett konto (t.ex. user@contoso.com). Utvecklare kan ange appens identitet på följande nivåer:

* **Processidentitet**: Anger identiteten för hela processen och används främst för program med endast en identitet. Den här identiteten påverkar alla åtgärder, filer och användargränssnittet.

* **Gränssnittsidentitet**: Avgör vilka principer som används för gränssnittsåtgärder på huvudtråden, t.ex. klipp ut/kopiera/klistra in, PIN-kod, autentisering och datadelning. Gränssnittsidentiteten påverkar inte filåtgärder som kryptering och säkerhetskopiering osv.

* **Trådidentitet**: Påverkar vilka principer som används på den aktuella tråden. Den här identiteten påverkar alla åtgärder, filer och användargränssnittet.

Det är appens ansvar att ange identiteterna korrekt, oavsett om användaren hanteras eller inte.

Alla trådar har alltid en effektiv identitet för gränssnittsåtgärder och filåtgärder. Detta är den identitet som används för att kontrollera vilka principer, om några, som ska användas. Om identiteten är "ingen identitet" eller om användaren inte hanteras tillämpas inga principer. Diagrammen nedan visar hur effektiva identiteter bestäms.

  ![Intune App SDK iOS: länkade ramverk och bibliotek](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>Trådköer

Appar skickar ofta asynkrona och synkrona uppgifter till trådköer. SDK fångar upp GCD-anrop (Grand Central Dispatch) och kopplar den aktuella trådidentiteten till uppgifter som skickas. När åtgärderna har utförts ändrar SDK tillfälligt trådidentiteten till den identitet som är kopplad till åtgärden, utför åtgärden, och återställer sedan den ursprungliga trådidentiteten.


Eftersom `NSOperationQueue` har byggts på GCD kommer `NSOperations` att köras på trådens identitet när åtgärderna läggs till i `NSOperationQueue`. `NSOperations` eller funktionerna som skickas direkt med GCD kan också ändra den befintliga trådidentiteten när de körs. Den här identiteten åsidosätter identiteten som ärvs från den avsändande tråden.

### <a name="file-owner"></a>Filägare

SDK spårar identiteterna av lokala filägare och tillämpar principer på lämpligt sätt. En filägare upprättas när en fil skapas eller när en fil öppnas i trunkeringsläge. Ägaren anges som den effektiva filåtgärdsidentiteten för tråden som utför åtgärden.

Appar kan också definiera filägaridentitet uttryckligen med hjälp av `IntuneMAMFilePolicyManager`. Appar kan använda `IntuneMAMFilePolicyManager` för att hämta filägaren och ange gränssnittsidentiteten innan filinnehållet visas.

### <a name="shared-data"></a>Delade data

Om appen skapar filer som har data från både hanterade och icke-hanterade användare är det appens ansvar att kryptera den hanterade användarens data. Du kan kryptera data med hjälp av `protect` och `unprotect`-API:erna i `IntuneMAMDataProtectionManager`.

`protect`-metoden godkänner en identitet som kan vara en hanterad eller icke-hanterad användare. Data krypteras om användaren är hanterad. Om användaren inte är hanterad läggs en rubrik till i data som kodar identiteten, men data krypteras inte. Du kan använda `protectionInfo`-metoden för att hämta dataägaren.

### <a name="share-extensions"></a>Resurstillägg

Om appen har ett resurstillägg kan ägaren av objektet som delas hämtas genom `protectionInfoForItemProvider`-metoden i `IntuneMAMDataProtectionManager`. Om det delade objektet är en fil hanterar SDK inställning av filägaren. Om det delade objektet är data är det appens ansvar att ange filägaren om dessa data har gjorts beständiga i en fil, och att anropa `setUIPolicyIdentity`-API:et innan dessa data visas i gränssnittet.

### <a name="turning-on-multi-identity"></a>Aktivera flera identiteter

Som standard betraktas alla appar som appar med endast en identitet. SDK anger processidentiteten till den registrerade användaren. Lägg till en boolesk inställning med namnet `MultiIdentity` och värdet JA i IntuneMAMSettings-ordlistan i appens Info.plist-fil om du vill aktivera stöd för flera identiteter.

> [!NOTE]
> När flera identiteter är aktiverade är processidentiteten, UI-identiteten och trådidentiteterna inställda på noll. Det är appens ansvar att ange dem på lämpligt sätt.

### <a name="switching-identities"></a>Växla identitet

* **Appinitierad identitetsväxling**:

    Vid start anses att multiidentitetsappar körs under ett okänt ej hanterat konto. Gränssnittet för villkorlig start körs inte och inga principer tvingas på appen. Det är appens ansvar att meddela SDK om identiteten ändras. Detta sker vanligtvis när appen är på väg att visa data för ett visst användarkonto.

    Ett exempel är om användaren försöker öppna ett dokument, en postlåda eller en flik på en bärbar dator. Appen måste meddela SDK innan filen, postlådan eller fliken öppnas. Detta görs via `setUIPolicyIdentity` API i `IntuneMAMPolicyManager`. Detta API ska anropas oavsett om användaren hanteras eller inte. Om användaren är hanterad utför SDK kontrollerna för villkorlig start, till exempel kontrollerna för upplåsningsidentifiering, PIN-kod och autentisering.

    Resultatet av identitetsväxlingen returneras till appen asynkront via en hanterare för slutförande. Appen skjuter upp öppning av dokumentet, postlådan eller fliken till en lyckad resultatkod returneras. Om identitetsväxlingen misslyckades avbryter appen åtgärden.

* **SDK-initierad identitetsväxling**:

    I vissa fall måste SDK be appen att växla till en viss identitet. Appar med multiidentitet måste implementera `identitySwitchRequired`-metoden i `IntuneMAMPolicyDelegate` för att hantera denna begäran.

    När den här metoden anropas överförs `IntuneMAMAddIdentityResultSuccess` till hanteraren för slutförande om appen kan hantera begäran om att växla till angiven identitet. Om den inte kan hantera växling av identiteten bör appen överföra `IntuneMAMAddIdentityResultFailed` till hanteraren för slutförande.

    Appen behöver inte anropa `setUIPolicyIdentity` som svar på detta anrop. Om SDK kräver att appen växlar till ett ej hanterat användarkonto kommer den tomma strängen att överföras till `identitySwitchRequired`-anropet.

* **Selektiv rensning**:

    När appen rensas selektivt anropar SDK `wipeDataForAccount`-metoden i `IntuneMAMPolicyDelegate`. Det är appens ansvar att ta bort det angivna användarkontot och eventuella data som är kopplade till det. SDK kan ta bort alla filer som ägs av användaren och gör det om programmet returnerar FALSKT från `wipeDataForAccount`-anropet.

    Observera att den här metoden anropas från en bakgrundstråd. Appen bör inte returnera något värde förrän alla data för användaren har tagits bort (med undantag för filer om appen returnerar FALSKT).

## <a name="test-app-protection-policy-settings-in-xcode"></a>Testa principinställningar för appskydd i Xcode

Innan du testar Intune-appen manuellt i produktion, kan du använda filen Settings.bundle i Xcode. Detta gör det möjligt för dig att ange appskyddsprinciper utan att det krävs någon anslutning till Intune.

### <a name="enable-policy-testing"></a>Aktivera principtestning

Följ stegen nedan för att aktivera principtestning i Xcode:

1. Se till att du är i en felsökningsversion. Lägg till filen Settings.bundle genom att högerklicka på den översta mappen i projektet. Välj **Lägg till** > **Ny fil** i menyn. Välj mallen **Inställningspaket** under **Resurser** för att lägga till den.

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

3. I ordlistan **IntuneMAMSettings** i appens Info.plist, lägger du till ett booleskt värde med namnet ”DebugSettingsEnabled”. Ange värdet för DebugSettingsEnabled till ”YES”.



### <a name="app-protection-policy-settings"></a>Principinställningar för appskydd

Tabellen nedan beskriver principinställningarna för appskydd som du kan testa med MAMDebugSettings.plist. Aktivera en inställning genom att lägga till den i MAMDebugSettings.plist.

| Principinställningsnamn | Beskrivning | Möjliga värden |
| -- | -- | -- |
| AccessRecheckOfflineTimeout | Hur lång tid i minuter appen kan vara offline innan Intune blockerar appen från att starta eller återupptas om autentisering är aktiverad. | Ett heltal som är större än 0 |
|   AccessRecheckOnlineTimeout | Hur lång tid i minuter appen kan köras innan användaren uppmanas att ange PIN-kod eller autentisering vid start eller återupptagande (om autentisering eller PIN-kod för åtkomst har aktiverats). | Ett heltal som är större än 0 |
| AppSharingFromLevel | Anger vilka appar den här appen kan ta emot data från. | 0 = |
## <a name="ios-best-practices"></a>Metodtips för iOS

Här är några rekommenderade metodtips för att utveckla med iOS:

* iOS-filsystemet är skiftlägeskänsligt. Se till att versaler och gemener stämmer för filnamn som `libIntuneMAM.a` och `IntuneMAMResources.bundle`.

* Om Xcode har problem med att hitta `libIntuneMAM.a` så kan du åtgärda problemet genom att lägga till sökvägen till biblioteket i sökvägarna för länkare.

## <a name="faqs"></a>Vanliga frågor och svar


**Är alla API:erna adresserbara via samverkan med intern Swift eller Objective-C och Swift?**

Intune App SDK-API:er finns endast i Objective-C och har inte stöd för **intern** Swift. Snabb samverkan med Objective-C krävs.


**Måste alla användare av mitt program registreras med APP-WE-tjänsten?**

Nej. I själva verket är det bara arbets- eller skolkonton som ska registreras med Intune App SDK. Appar ansvarar för att fastställa om ett konto används i ett arbets- eller skolsammanhang.   

**Vad gäller för användare som redan har loggat in i programmet? Behöver de registreras?**

Det är appens ansvar att registrera användare när de har autentiserats. Programmet ansvarar även för att registrera eventuella befintliga konton som kan ha funnits innan programmet hade MAM-funktioner utan MDM.   

Programmet ska använda `registeredAccounts:`-metoden för att göra detta. Den här metoden returnerar ett NSDictionary som har alla konton som är registrerade i Intune MAM-tjänsten. Om några befintliga konton i programmet inte finns i listan bör programmet registrera dessa konton via `registerAndEnrollAccount:`.

**Hur ofta gör SDK nya registreringsförsök?**

SDK försöker automatiskt igen om 24 timmar med alla registreringar som har misslyckats tidigare. SDK gör detta för att säkerställa att en användare registreras och tar emot principer även om användarens organisation aktiverar MAM efter att användaren loggar in i programmet.

SDK slutar att försöka när det upptäcker att en användare har lyckats registrera programmet. Det beror på att endast en användare kan registrera ett program vid en given tidpunkt. Om användaren har avregistrerats påbörjas nya försök med samma 24-timmarsintervall.

**Varför måste användaren avregistreras?**

SDK vidtar regelbundet följande åtgärder i bakgrunden:

 - Om programmet inte har registrerats ännu försöker det att registrera alla registrerade konton var 24:e timme.
 - Om programmet har registrerats kontrollerar SDK var 8:e timme om det finns uppdateringar för appskyddsprinciper.

Om en användare avregistreras meddelas SDK att användaren inte längre använder programmet och SDK kan då stänga av de ovanstående regelbundna händelserna för det användarkontot. Det utlöser även avregistrering av appen och selektiv rensning vid behov.

**Ska jag ställa in flaggan doWipe till true i avregistreringsmetoden?**

Den här metoden ska anropas innan användaren loggas ut från programmet.  Om användarens data raderas från programmet som en del av utloggningen kan `doWipe` vara inställt på falskt. Men om programmet inte tar bort användarens data bör `doWipe` ställas in på sant så att SDK kan ta bort dessa data själv.

**Finns det andra sätt att avregistrera ett program?**

Ja, IT-administratören kan skicka ett kommando för selektiv rensning till programmet. Detta avregistrerar användaren och raderar användarens data. SDK hanterar det här scenariot automatiskt och skickar en avisering via ombudsmetoden för avregistrering.



## <a name="submit-your-app-to-the-app-store"></a>Skicka in din app till App Store

Både det statiska biblioteket och ramverksversionerna av Intune App SDK är universella binärfiler. Detta innebär att de innehåller kod för alla enhets- och simuleringsarkitekturer. Apple avvisar appar som skickas till App Store om de innehåller simuleringskod. Vid kompileringen mot det statiska biblioteket för versioner för endast enheten kommer länkaren att ta bort simuleringskoden automatiskt. Följ stegen nedan för att se till att all simuleringskod tas bort innan du laddar upp din app till App Store.

1. Kontrollera att `IntuneMAM.framework` finns på skrivbordet.

2. Kör dessa kommandon:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    Det första kommandot rensar simuleringsarkitektur från ramverkets DYLIB-fil. Det andra kommandot kopierar DYLIB-filen som endast är för enheten tillbaka till ramverkskatalogen.
