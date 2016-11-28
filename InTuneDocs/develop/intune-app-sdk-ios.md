---
title: "Utvecklarhandbok för Microsoft Intune App SDK för iOS | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: angrobe
ms.author: oydang
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 018faada59819938d443605a454465a38600c9a4
ms.openlocfilehash: f44d2a43c6717c9b3adde9ba49a54e014f4e3528


---

# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Utvecklarhandbok för Microsoft Intune App SDK för iOS

> [!NOTE]
> Börja gärna med att läsa artikeln [Komma igång med Intune App SDK](intune-app-sdk-get-started.md). Den här guiden beskriver hur du förbereder dig för integreringen på de plattformar som stöds.

## <a name="overview"></a>Översikt

Med Microsoft Intune App SDK för iOS kan du lägga till Intune-apprinciper i din iOS-app. Ett MAM-aktiverat program är ett program som är integrerat i Intune App SDK och gör att IT-administratörer kan distribuera principer till mobilappen när den hanteras aktivt av Intune Mobile Application Management (MAM).


## <a name="prerequisites"></a>Förutsättningar

* Du behöver en Mac OS-dator som kör OS X 10.8.5 eller senare och som har XCode-verktygsuppsättningen version 5 eller senare installerad.

* Läs [licensvillkoren för Intune App SDK för iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf). Skriv ut och behåll en kopia av licensvillkoren för framtida referens. Genom att ladda ned och använda Intune App SDK för iOS samtycker du till dessa licensvillkor.  Om du inte accepterar villkoren har du inte rätt att använda programvaran.


## <a name="whats-in-the-sdk"></a>Vad innehåller SDK?

Intune App SDK för iOS innehåller ett statiskt bibliotek, resursfiler, API-rubriker, en plist-fil med inställningar för felsökning samt ett konfigurationsverktyg. Mobilappar kan bara innehålla resursfiler och statiskt länka till biblioteken i de flesta tillämpningarna av principer. Avancerade MAM-funktioner i Intune aktiveras via API:er.

I den här handboken beskrivs hur du använder följande komponenter i Intune App SDK för iOS:

* **libIntuneMAM.a**: Det statiska Intune App SDK-biblioteket. Om appen inte använder tillägg kan du länka detta bibliotek till projektet för att möjliggöra hantering av mobilprogram i Intune med appen. Anvisningar finns i avsnittet Skapa en app med Intune App SDK.

* **IntuneMAM.framework**: Intune App SDK-ramverket. Länka detta ramverk till projektet för att möjliggöra hantering av mobilprogram i Intune med appen. Använd ramverket i stället för det statiska biblioteket om appen använder tillägg, så att projektet inte skapar flera kopior av det statiska biblioteket.

* **IntuneMAMResources.Bundle**: ett resurspaket som innehåller resurser som SDK är beroende av.

* **Rubriker**: visar API:er för Intune App SDK. Om du använder ett API måste du inkludera huvudfilen som innehåller API:et. Följande rubrikfiler innehåller API-funktionsanrop som krävs för att aktivera funktionerna i Intune App SDK.

    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h


## <a name="how-the-intune-app-sdk-works"></a>Hur Intune App SDK fungerar

Målet med Intune App SDK för iOS är att lägga till hanteringsfunktioner i iOS-program med minimala kodändringar. Färre kodändringar innebär kortare tid innan produkten är klar, samtidigt som mobilappen blir mer konsekvent och stabil.

Programmet måste länkas till det statiska biblioteket och måste inkludera resurspaketet. Filen MAMDebugSettings.plist är valfri och kan tas med i paketet för att simulera MAM-principer som tillämpas på programmet utan att behöva distribuera programmet via Microsoft Intune. Dessutom kan principerna i filen MAMDebugSettings.plist tillämpas i felsökningsversioner genom att överföra filen till appens dokumentkatalog via iTunes fildelning.

## <a name="building-the-sdk-into-your-mobile-app"></a>Skapa SDK i mobilappen

Följ stegen nedan för att aktivera Intune App SDK:

1. **Alternativ 1**: Länka till `libIntuneMAM.a`-biblioteket på följande sätt:

    Dra och släpp `libIntuneMAM.a`-biblioteket till listan Linked Frameworks and Libraries (Länkade ramverk och bibliotek) i projektets målkatalog.

    ![Intune App SDK iOS – länkade ramverk och bibliotek](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    **Obs!** Om du planerar att lansera appen i App Store bör du använda den version av `libIntuneMAM.a` som skapats för lanseringen, alltså inte felsökningsversionen. Versionen ligger i versionsmappen. Felsökningsversionen innehåller utförliga data som hjälper till att felsöka problem med Intune App SDK.

    **Alternativ 2**: Länka `IntuneMAM.framework` till projektet. Dra och släpp `IntuneMAM.framework`-biblioteket till listan Linked Frameworks and Libraries (Länkade ramverk och bibliotek) i projektets målkatalog.

    **Obs**! Om du använder ramverket måste du rensa bort simuleringsarkitekturen manuellt från det universella ramverket innan du skickar in appen till App Store. Se avsnittet "Skicka in din app till App Store".

2. Lägg till följande iOS-ramverk i projektet:
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.dylib
    * libc++.dylib
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework

    **Obs**! Om programmet är avsett för iOS7 anger du attributet Status i `LocalAuthentication.framework` som Valfri. Om inget värde har angetts för Status kan inte programmet starta i iOS7.

    **Obs!**Xcode 7 har bytt `.dylib` -tilläggen till `.tbd`.

3. Lägg till `IntuneMAMResources.bundle`-resurspaketet i projektet genom att dra resurspaketet till Copy Bundle Resources (Kopiera paketresurser) i Build Phases (Versionsfaser).
![Intune App SDK iOS – kopiera paketresurser](../media/intune-app-sdk-ios-copy-bundle-resources.png)

4. Lägg till `-force_load {PATH_TO_LIB}/libIntuneMAM.a` i någon av följande och ersätt `{PATH_TO_LIB}` med platsen för Intune App SDK:
    * projektets konfigurationsinställning för `OTHER_LDFLAGS`
    * användargränssnitten Other Linker Flags (Andra länkarflaggor)<br>

    **Obs**! Leta reda på `PATH_TO_LIB` genom att välja filen `libIntuneMAM.a` och välja Get Info (Hämta information) från menyn Arkiv. Kopiera och klistra in sökvägen från avsnittet Allmänt i fönstret Information.

5. Om mobilappen definierar Main Nib eller Storyboard i filen Info.plist tar du bort fälten för filen Main Storyboard eller Main Nib. Lägg till värdena för Storyboard eller Nib som du tidigare tog bort under en ny ordlista som heter IntuneMAMSettings med följande namn, i tillämpliga fall:
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad

   **Obs**! Om mobilappen inte definierar något värde för Main Nib eller Storyboard i filen Info.plist är dessa inställningar **inte obligatoriska**.

    **Obs**! Du kan visa filen Info.plist i obearbetat format (för att visa nyckelnamnen) genom att högerklicka någonstans i dokumentets brödtext och ändra visningstypen till Show Raw Keys/Values (Visa obearbetade nycklar/värden).

6. Aktivera delning av nyckelringar (om det inte redan är aktiverat) genom att klicka på Funktioner i varje projektmål och aktivera reglaget för delning av nyckelringar. Delning av nyckelringar krävs för att kunna fortsätta till nästa steg.

    **Obs!**Etableringsprofilen måste ha stöd för nya värden för delning av nyckelringar. Åtkomstgrupper för nyckelringar ska ha stöd för jokertecken. Du kan bekräfta det genom att öppna filen .mobileprovision i en textredigerare, söka efter "keychain-access-groups" och se till att du har ett jokertecken, t.ex.:
    ```xml
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```
7. När du har aktiverat delning av nyckelringar följer du dessa steg för att skapa en separat åtkomstgrupp där data i Intune App SDK kommer att sparas. Du kan skapa en åtkomstgrupp för nyckelringar med hjälp av användargränssnittet eller med behörighetsfilen:

    Använda användargränssnittet för att skapa en åtkomstgrupp för nyckelringar:

    * Om mobilappen inte har definierat några åtkomstgrupper för nyckelringar lägger du till appens paket-ID som den första gruppen.
    * Lägg till den delade nyckelringsgruppen `com.microsoft.intune.mam`. Den här åtkomstgruppen används av Intune App SDK för att spara data.  
    * Lägg till `com.microsoft.adalcache` i dina befintliga åtkomstgrupper.

    ![Intune App SDK iOS – delning av nyckelringar](../media/intune-app-sdk-ios-keychain-sharing.png)

    Om du använder behörighetsfilen för att skapa en åtkomstgrupp för nyckelringar istället för det vanliga användargränssnittet måste du lägga till åtkomstgruppen för nyckelringar med `$(AppIdentifierPrefix)` i behörighetsfilen. Exempel:  
    * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
    * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    **Obs!**En behörighetsfil är en XML-fil som är unik för mobilappen som används för att ange särskilda behörigheter och funktioner i din iOS-app.

8. Om appen definierar URL-scheman i filen Info.plist lägger du till ytterligare ett schema med suffixet `-intunemam` för varje URL-schema.

9. För mobilappar som utvecklas för iOS 9 och senare måste du inkludera varje protokoll som appen skickar till `UIApplication canOpenURL` i matrisen `LSApplicationQueriesSchemes` i appens fil Info.plist. Dessutom måste ett nytt protokoll läggas till med `-intunemam`. Du måste även inkludera `http-intunemam`, `https-intunemam`och `ms-outlook-intunemam` i matrisen.

10. Om appen har definierade appgrupper i sina behörigheter lägger du till dessa grupper i ordlistan IntuneMAMSettings under nyckeln `AppGroupIdentitifiers` som en matris med strängar.

11. Länka mobilappen till Azure Directory Authentication Library (ADAL). ADAL-biblioteket för Objective C [finns på Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc).

    **Obs!**Intune App SDK har testats enligt ADAL-hanterarens kod från 19 juni 2015. Se till att du länkar till den senaste fungerande versionen av ADAL-biblioteket.

12. Inkludera resurspaketet `ADALiOSBundle.bundle` i projektet genom att dra resurspaketet till Copy Bundle Resources (Kopiera paketresurser) i Build Phases (Versionsfaser).

13. Använd länkaralternativet `-force_load PATH_TO_ADAL_LIBRARY` när du länkar till biblioteket.

    Lägg till `-force_load {PATH_TO_LIB}/libADALiOS.a` i projektets `OTHER_LDFLAGS`-konfigurationsinställning eller ”Other Linker Flags” (Andra länkarflaggor) i användargränssnittet. `PATH_TO_LIB` ska ersättas med platsen för ADAL-binärfilerna.

## <a name="configure-azure-directory-authentication-library-adal"></a>Konfigurera Azure Directory Authentication Library (ADAL)

Intune App SDK använder ADAL för autentiseringsscenarier och scenarier för villkorlig start. Den förlitar sig även på ADAL för att registrera användarens identitet i MAM-tjänsten för hantering utan enhetsregistreringsscenarier.

Normalt kräver ADAL att appar registreras med [Azure Active Directory] och erhåller ett unikt ID, även kallat ClientID, och andra identifierare, för att garantera säkerheten i de token som appen beviljats. Intune App SDK använder standardvärden för registrering vid kontakt med Azure Active Directory.  

Om själva appen använder ADAL för autentiseringsscenariot måste appen använda de befintliga registreringsvärdena och åsidosätta standardvärdet för Intune App SDK för att se till att slutanvändare inte behöver autentiseras två gånger (en gång av Intune App SDK och en gång av appen).

### <a name="adal-faqs"></a>Vanliga frågor och svar om ADAL

**Vilka ADAL-binärfiler ska jag använda?**

Intune App SDK använder för närvarande hanterardelen av [ADAL på GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-objc) för att ge stöd för appar som kräver villkorlig åtkomst (appar som därför förlitar sig på Microsoft Authenticator-appen). SDK är dock fortfarande är kompatibel med huvuddelen av ADAL. Använd den del som är lämplig för din app.

**Hur länkar jag till ADAL-binärfiler?**

Lägg till `-force_load {PATH_TO_LIB}/libADALiOS.a` i projektets `OTHER_LDFLAGS`-konfigurationsinställning eller ”Other Linker Flags” (Andra länkarflaggor) i användargränssnittet. `PATH_TO_LIB` ska ersättas med platsen för ADAL-binärfilerna. Tänk även på att kopiera ADAL-paketet till appen.  

Mer information finns i instruktionerna från [ADAL på Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc).


**Hur gör jag för att dela ADAL-cache med andra appar som signeras med samma etableringsprofil?**

Om appen inte har definierat några åtkomstgrupper för nyckelringar lägger du till appens paket-ID som den första gruppen.
Aktivera enkel inloggning med ADAL SSO genom att lägga till åtkomstgrupperna `com.microsoft.adalcache` och `com.microsoft.workplacejoin` i nyckelringens rättigheter.

Om du ställer in nyckelringsgruppen för ADAL-delad cache ser du till att den är inställd på `<app_id_prefix>.com.microsoft.adalcache`. ADAL ställer in detta åt dig förutsatt att du inte åsidosätter det. Om du vill ange en anpassad nyckelringsgrupp som ersätter `com.microsoft.adalcache` anger du det i Info.plist under "IntuneMAMSettings" med hjälp av nyckeln `ADALCacheKeychainGroupOverride`.

**Hur gör jag för att tvinga Intune App SDK att använda ADAL-inställningar som min app redan använder?**

Om appen redan använder ADAL kan du läsa avsnittet om IntuneMAMSettings nedan för att få information om att fylla i inställningarna nedan:  

* ADALClientId
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

**Hur växlar jag mellan produktionsmiljöer och interna testmiljöer i AAD?**

`AadAuthorityURI`-inställningen i `MAMPolicies.plist` kan användas för att ange den AAD-miljö som ska användas för ADAL-anrop. Den är för närvarande inställd på att använda AAD förproduktionsmiljö (PPE) som standard, om detta inte åsidosätts.

Du kan använda en kompileringstid eller körningsväxel för att testa mot PPE.

Vid en miljöväxel för kompileringstid i MAM-tjänstens URL och AAD anger du den booleska flaggan `UsePPE` på sant i MAMEnvironment.plist (**Obs**! Det finns inget stöd för att göra detta via Info.plist).

Vid en miljöväxel för körning anger du `com.microsoft.intune.mam.useppe` i användarstandard på ”1” för att använda PPE. Det här ersätter den befintliga `com.microsoft.intune.mam.AADAuthorityEnvironment`-inställningen.

**Hur åsidosätter jag AAD-auktoritetens URL med en klientspecifik URL som anges vid körning?**

Ställ in egenskapen `aadAuthorityUriOverride` på IntuneMAMPolicyManager-instansen.

**Obs**! Du behöver detta i MAM utan enhetsregistrering för att tillåta att SDK återanvänder ADAL-uppdateringstoken som hämtas av appen.

**Obs!** SDK fortsätter att använda denna utfärdar-URL för principuppdatering och eventuella efterföljande registreringsbegäranden såvida inte värdet rensas eller ändras.  Det är därför viktigt att rensa värdet när företagsanvändare loggar ut från appen och återställa det när en ny företagsanvändare loggar in igen.


**Vad gör jag om själva appen använder ADAL för autentisering?**

Stegen nedan krävs om appen redan använder ADAL för autentisering. Om appen inte använder ADAL bör du läsa avsnittet om registrering med Intune-tjänsten om appen inte använder ADAL.

* I filen Info.plist i projektet, under ordlistan IntuneMAMSettings med nyckelnamnet `ADALClientId`, anger du det ClientID som ska användas för ADAL-anrop.

* I filen Info.plist i projektet, under ordlistan IntuneMAMSettings med nyckelnamnet `ADALRedirectUri`, anger du den Redirect URI som ska användas för ADAL-anrop. Du kan även behöva ange `ADALRedirectScheme` beroende på formatet för appens omdirigerings-URI.



## <a name="register-your-app-with-intune-mam-service"></a>Registrera din app med Intune MAM-tjänsten

### <a name="use-the-apis"></a>Använda API:erna
Intune App SDK ger nu möjlighet för iOS-appar att ta emot MAM-principer från Intune utan att behöva vara MDM-registrerade med Intune. SDK innehåller nya API:er som gör det möjligt för appen att ta emot MAM-principer för att stödja den här nya funktionen. Utför följande steg för att kunna använda de nya API:erna:

1. Använd den senaste versionen av Intune App SDK som stöder hantering av appar med eller utan enhetsregistrering. Om appen har en äldre version av SDK utan den här funktionen måste du uppdatera Intune MAM-biblioteket, samt uppdatera rubrikmappen med rubrikerna från den senaste SDK-versionen.

2. Lägg till IntuneMAMEnrollment.h i alla filer som kommer att anropa API:erna

3. Du kan inkludera en kompileringstid eller körningsväxel för att testa mot PPE.

    Vid en miljöväxel för kompileringstid i MAM-tjänstens URL och AAD anger du den booleska flaggan `UsePPE` på sant i MAMEnvironment.plist (**Obs**! Det finns inget stöd för att göra detta via Info.plist).

    Vid en miljöväxel för körning anger du `com.microsoft.intune.mam.useppe` i användarstandard på ”1” för att använda PPE. Det här ersätter den befintliga `com.microsoft.intune.mam.AADAuthorityEnvironment`-inställningen.


### <a name="register-accounts"></a>Registrera konton

En app kan ta emot MAM-principer från Intune-tjänsten om appen registreras för ett angivet användarkonto.  Det är appens ansvar att registrera eventuella nyligen inloggade användare i Intune App SDK.  När det nya användarkontot har autentiserats måste appen anropa `registerAndEnrollAccount`-metoden i **Headers/IntuneMAMEnrollment.h**:

```objc
/**


 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;

```
Genom att anropa metoden ovan registrerar SDK användarkontot och försöker registrera appen för det här kontot.  Om registreringen misslyckas av någon anledning försöker SDK genomföra registreringen igen automatiskt 24 timmar senare.  Appen kan i felsökningssyfte ta emot aviseringar, via ett ombud, om resultaten av eventuella registreringsbegäranden (se information nedan).

När detta API har anropats kan programmet fortsätta att fungera som vanligt.  Om registreringen lyckas meddelar SDK användaren att appen behöver startas om.  Användaren kan då starta om appen omedelbart.


### <a name="de-register-accounts"></a>Avregistrera konton


Innan en användare loggas ut från en app bör appen avregistrera användaren från SDK.  Detta säkerställer följande:

1. Nya registreringsförsök sker inte längre för användarens konto.
2. Om användaren har registrerat programmet kommer användaren och appen att avregistreras från Intune MAM-tjänsten och MAM-principerna tas bort.
3. Det går också att starta en selektiv rensning för att se till att eventuella arbets- eller skolrelaterade data raderas.

Innan användaren loggas ut måste appen anropa följande API som finns i **Headers/IntuneMAMEnrollment.h**:

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

Den här metoden måste anropas innan användarkontots AAD-token tas bort.  SDK behöver användarens apptoken för att göra specifika begäranden till Intune MAM-tjänsten för användarens räkning.

Om appen ska ta bort användarens arbets- eller skolrelaterade data på egen hand ska `doWipe`-flaggan anges till falskt.  Annars kan appen göra så att SDK startar en selektiv rensning, vilket leder till ett anrop till appens selektiva rensningsombud).

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```


## <a name="enrolling-without-prior-sign-in"></a>Registrera utan tidigare inloggning

En app som inte loggar in användaren i Azure Active Directory kan fortfarande ta emot MAM-principer från Intune-tjänsten genom att anropa API nedan för att låta SDK hantera den autentiseringen. Appar bör använda detta när de inte har autentiserat en användare med AAD men ändå behöver hämta MAM-principer för att skydda data i appen, t.ex. om en annan autentiseringstjänst används för inloggning i appen eller om appen inte har stöd för inloggning över huvud taget. Programmet måste anropa `loginAndEnrollAccount`-metoden i **Headers/IntuneMAMEnrollment.h** för att göra detta:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;

```
Genom att anropa den här metoden frågar SDK användaren om autentiseringsuppgifter om ingen befintlig token kan hittas och försöker sedan registrera programmet för det här kontot. Metoden kan anropas med "nil" som identitet. I så fall registrerar SDK med befintlig MAM-användare på enheten eller frågar användaren om ett användarnamn om det inte går att hitta en befintlig användare.

Om registreringen misslyckas bör appen överväga att anropa detta API igen vid ett senare tillfälle, beroende på detaljerna kring felet. Appen kan ta emot aviseringar, via ett ombud, om resultaten av eventuella registreringsbegäranden (se information).

När detta API har anropats kan appen fortsätta att fungera som vanligt.  Om registreringen lyckas meddelar SDK användaren att en app behöver startas om, vilket visas i avsnittet ovan om att registrera konton.

## <a name="debug-information"></a>Felsökningsinformation

Appen kan ta emot felsökningsaviseringar om följande begäranden till Intune MAM-tjänsten:

 - Begäran om registrering
 - Begäran om principuppdatering
 - Begäran om avregistrering

Aviseringarna visas via delegeringsmetoder som finns i **Headers/IntuneMAMEnrollmentDelegate.h**:

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
- Statuskod som visar resultatet av begäran
- En felsträng med en beskrivning av statuskoden
- Ett NSError-objekt

Det här objektet definieras i **Headers/IntuneMAMEnrollmentStatus.h** tillsammans med de specifika statuskoder som kan returneras.

Det är viktigt att notera att den här informationen är avsedd för felsökning, och ingen app ska ha affärslogik som baseras på dessa aviseringar.  Tanken är att appen kan skicka den här informationen till en telemetritjänst för felsökning och övervakning.


## <a name="sample-code"></a>Exempelkod

Följande är exempel på implementeringar av ombudsmetoderna:

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

När en app tar emot MAM-principer för första gången måste den startas om för att tillämpa obligatoriska hookar.  För att meddela appen att en omstart krävs tillhandahåller SDK en delegeringsmetod i **Headers/IntuneMAMPolicyDelegate.h**.
```objc
 - (BOOL) restartApplication
```
Returvärdet för den här metoden talar om för SDK om programmet ska hantera de omstarter som krävs.   

 - Om sant returneras ansvarar programmet för hantering av omstarten.   
 - Om falskt returneras startar SDK om programmet när den här metoden returneras.  SDK öppnar direkt en dialogruta som talar om för användaren att programmet måste startas om.

## <a name="implementing-save-as-controls"></a>Implementera ”Spara som”-kontroller

Med Intune kan IT-administratörer välja vilka lagringsplatser som en hanterad app kan spara data till. Appar kan fråga Intunes App SDK efter tillåtna lagringsplatser med hjälp av **isSaveToAllowedForLocation**-API:et.

Innan du sparar hanterade data i molnlagring eller på en lokal plats måste apparna kontrollera **isSaveToAllowedForLocation**-API:et för att se om IT-administratören tillåter att data sparas där.

När **isSaveToAllowedForLocation**-API:et används måste apparna ange lagringsplatsens UPN, om det är tillgängligt.

### <a name="supported-save-locations"></a>Lagringsplatser som stöds

**isSaveToAllowedForLocation**-API:et tillhandahåller konstanter för att kontrollera om IT-administratören tillåter att data sparas på följande platser:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationBox
* IntuneMAMSaveLocationDropbox
* IntuneMAMSaveLocationGoogleDrive
* IntuneMAMSaveLocationLocalDrive

Apparna bör använda konstanterna i **isSaveToAllowedForLocation**-API:et för att kontrollera om data kan sparas till platser som betraktas som ”hanterade”, till exempel OneDrive för företag, eller ”personliga”. API:et bör dessutom användas när appen inte kan avgöra om en plats är ”hanterad” eller ”personlig”.

När en plats har fastställts som ”personlig” bör apparna använda **IntuneMAMSaveLocationOther**-värdet.

**IntuneMAMSaveLocationLocalDrive**-konstanten bör användas när appen sparar data till en plats på den lokala enheten.



## <a name="configure-intune-app-sdk-settings"></a>Konfigurera inställningar för Intune App SDK

Ordlistan IntuneMAMSettings i filen Info.plist i programmet används för att konfigurera Intune App SDK. Följande är en lista över konfigurationer som stöds:

Några av de här inställningarna kan ha beskrivits i föregående avsnitt och vissa gäller inte för alla appar.

Inställningar  | Typ  | Definition | Obligatoriskt?
--       |  --   |   --       |  --
ADALClientId  | Sträng  | Appens klient-ID för AAD. | Krävs om appen använder ADAL.
ADALRedirectUri  | Sträng  | Appens omdirigerings-URI för AAD. | ADALRedirectUri eller ADALRedirectScheme krävs om appen använder ADAL.
ADALRedirectScheme  | Sträng  | Appens AAD-omdirigeringsschema. Detta kan användas i stället för ADALRedirectUri om programmets omdirigerings-URI har formatet `scheme://bundle_id`. | ADALRedirectUri eller ADALRedirectScheme krävs om appen använder ADAL.
ADALLogOverrideDisabled | Boolesk  | Anger om SDK:t dirigerar alla ADAL-loggar (inklusive eventuella ADAL-anrop från appen) till den egna loggfilen. Standardvärdet är NO (NEJ). Ange YES (JA) om appen ska ange egna återanrop i ADAL-loggen. | Valfritt.
ADALCacheKeychainGroupOverride | Sträng  | Anger nyckelringsgruppen som ska användas för ADAL-cache i stället för ”com.microsoft.adalcache”. Observera att detta inte innehåller app-id-prefixet. Det läggs till i den angivna strängen vid körning. | Valfritt.
AppGroupIdentifiers | Strängmatris  | Matris med appgrupper från appens behörigheter i avsnittet com.apple.security.application-groups  | Krävs om appen använder programgrupper.
ContainingAppBundleId | Sträng | Anger paket-id:t för programmet som ingår i tillägget. | Krävs för iOS-tillägg.
DebugSettingsEnabled| Boolesk | Om detta är inställt på JA kan testprinciper i inställningspaketet användas. Program bör **inte** levereras med den här inställningen aktiverad. | Valfritt.
MainNibFile<br>MainNibFile~ipad  | Sträng  | Den här inställningen ska innehålla programmets namn på filen för Main Nib.  | Krävs om programmet definierar MainNibFile i filen Info.plist.
MainStoryboardFile<br>MainStoryboardFile~ipad  | Sträng  | Den här inställningen ska innehålla programmets namn på filen för Main Storyboard. | Krävs om programmet definierar UIMainStoryboardFile i filen Info.plist
MAMPolicyRequired| Boolesk| Anger om appen kommer att blockeras från att starta om appen inte har Intune MAM-principen. Standardvärdet är "no" (nej).
MAMPolicyWarnAbsent | Boolesk| Anger om appen kommer att varna användaren under start om appen inte har Intune MAM-principen. Obs! Appar kan inte skickas till butiken med den här inställningen angiven som YES (JA) | Valfritt.
MultiIdentity | Boolesk| Anger om appen är multiidentitetsmedveten | Valfritt.
SplashIconFile <br>SplashIconFile~ipad | Sträng  | Anger filen för Intunes ikon för välkomstskärmen. I avsnittet Bildfiler vid start finns mer information. | Valfritt.
SplashDuration | Antal | Kortaste tid i sekunder som välkomstskärmen för Intune visas när programmet startas. Standardvärdet är 1,5. | Valfritt.
BackgroundColor| Sträng| Anger bakgrundsfärgen för välkomst- och PIN-kodsskärmarna. Godkänner en hexadecimal RGB-sträng med formatet ”#XXXXXX”, där ”X” kan vara 0–9 eller A–F. Pundtecknet kan utelämnas.   | Ljusgrått är standardinställningen.
ForegroundColor| Sträng| Anger förgrundsfärg för välkomst- och PIN-kodsskärmarna, till exempel textfärg. Godkänner en hexadecimal RGB-sträng med formatet ”#XXXXXX”, där ”X” kan vara 0–9 eller A–F. Pundtecknet kan utelämnas.  | Svart är standardinställningen.
AccentColor | Sträng| Anger accentfärg för PIN-kodsskärmen, till exempel textfärg på knappar och markeringsfärg för rutor.  Godkänner en hexadecimal RGB-sträng med formatet ”#XXXXXX”, där ”X” kan vara 0–9 eller A–F. Pundtecknet kan utelämnas.| Systemblått är standardinställningen.
MAMTelemetryDisabled| Boolesk| Anger om SDK inte ska skicka några telemetridata tillbaka till serverdelen| Valfritt.
MAMTelemetryUsePPE | Boolesk | Anger om SDK ska skicka data till förproduktionsmiljöns (PPE) serverdel. Använd det här när du testar dina appar med Intune-principen så att testets telemetridata inte blandas med kunddata. | Valfritt.

## <a name="telemetry"></a>Telemetri

Intune App SDK för iOS loggar telemetridata vid användningshändelser som standard och skickar dem till Microsoft Intune. Data loggas på följande användningshändelser:

1. **Appstart**: för att hjälpa Microsoft Intune att få veta mer om MAM-aktiverad appanvändning efter hanteringstyp (MAM med MDM, MAM utan MDM-registrering osv.).

2. **Anropa EnrollApplication API**: för att hjälpa Microsoft Intune att förstå lyckade resultat och andra typer av resultatstatistik för `enrollApplication`-anrop från klienten.

**Obs**! Om du väljer att inte skicka Intune App SDK-telemetridata till Microsoft Intune från mobilappen måste du inaktivera Intune App SDK-telemetriinsamlingen genom att ge egenskapen `MAMTelemetryDisabled` värdet YES (JA) i ordlistan IntuneMAMSettings.





## <a name="enable-multi-identity-optional"></a>Aktivera flera identiteter (valfritt)

Som standard använder SDK principen på appen som helhet. Multiidentitet är en MAM-funktion som kan aktiveras för att tillåta att en princip tillämpas på nivån per identitet.  Detta kräver mer appdeltagande än andra MAM-funktioner.

Appen krävs för att meddela app-SDK när den har för avsikt att ändra den aktiva identiteten. SDK meddelar även appen när en identitetsändring krävs. För närvarande stöds endast en hanterad identitet. När användaren registrerar enheten eller appen använder SDK den här identiteten och ser den som primär hanterad identitet. Andra användare i appen behandlas som ej hanterade med obegränsade principinställningar.

Tänk på att en identitet endast definieras som en sträng. Identiteter är skiftlägeskänsliga och begäran till SDK om en identitet kanske inte returnerar samma gemener och versaler som användes när identiteten skapades.


### <a name="overview"></a>Översikt

En identitet är bara användarnamnet för ett konto (t.ex. user@contoso.com). Utvecklare kan ställa in appens identitet på följande nivåer:

* **Processidentitet**: processidentiteten anger identiteten för hela processen och används främst för program med endast en identitet. Den här identiteten påverkar alla åtgärder, filer och användargränssnittet.
* **Gränssnittsidentitet**: avgör vilka principer som används för gränssnittsåtgärder på huvudtråden, t.ex. klipp ut/kopiera/klistra in, PIN-kod, autentisering, datadelning osv. Gränssnittsidentiteten påverkar inte filåtgärder (kryptering, säkerhetskopiering osv.).
* **Trådidentitet**: trådidentiteten påverkar vilka principer som används på den aktuella tråden. Detta påverkar alla åtgärder, filer och användargränssnittet.

Det är appens ansvar att ange identiteterna korrekt, oavsett om användaren hanteras eller inte.

Alla trådar har alltid en effektiv identitet för gränssnittsåtgärder och filåtgärder. Detta är den identitet som används för att fastställa vilka principer, om några, som ska användas. Om identiteten är ”ingen identitet” eller om användaren inte hanteras tillämpas inga principer.



### <a name="thread-queues"></a>Trådköer

Appar skickar ofta asynkrona och synkrona uppgifter till trådköer. SDK fångar upp GCD-anrop (Grand Central Dispatch) och kopplar den aktuella trådidentiteten till uppgifter som skickas. När uppgifterna körs ändrar SDK tillfälligt trådidentiteten till den identitet som är kopplad till uppgiften, kör uppgiften och återställer sedan den ursprungliga trådidentiteten. Eftersom `NSOperationQueue` har byggts på GCD kommer `NSOperations` att köras på trådens identitet när de läggs till i `NSOperationQueue`. `NSOperations` eller funktionerna som skickas direkt med GCD kan också ändra den befintliga trådidentiteten när de körs. Den här identiteten åsidosätter identiteten som ärvs från den avsändande tråden.

### <a name="file-owner"></a>Filägare

SDK håller reda på lokal filägaridentitet och använder principer på lämpligt sätt. Filägaren upprättas när filen skapas eller när filen öppnas i trunkeringsläge. Ägaren anges som den effektiva filåtgärdsidentiteten för tråden som utför åtgärden. Appar kan också definiera filägaridentitet uttryckligen med hjälp av `IntuneMAMFilePolicyManager`. Appar kan använda `IntuneMAMFilePolicyManager` för att hämta filägaren och ange gränssnittsidentiteten innan filinnehållet visas.


### <a name="shared-data"></a>Delade data

Om appen skapar filer som innehåller data från både hanterade och ej hanterade användare är det appens ansvar att kryptera den hanterade användarens data. Data kan krypteras med hjälp av API:erna `protect` och `unprotect` i `IntuneMAMDataProtectionManager`. `protect`-metoden godkänner en identitet som kan vara en hanterad eller ej hanterad användare. Data krypteras om användaren är hanterad. Om användaren inte är hanterad läggs en rubrik till i data som kodar identiteten, men data krypteras inte.  `protectionInfo`-metoden kan användas för att hämta dataägaren.

### <a name="share-extensions"></a>Resurstillägg

Om appen innehåller ett resurstillägg kan ägaren av objektet som delas hämtas med hjälp av `protectionInfoForItemProvider`-metoden i `IntuneMAMDataProtectionManager`. Om det delade objektet är en fil hanterar SDK inställning av filägaren. Om det delade objektet är data är det appens ansvar att ange filägaren om dessa data har gjorts beständiga i en fil, och att anropa `setUIPolicyIdentity` API (beskrivs nedan) innan dessa data visas i gränssnittet.

### <a name="turn-on-multi-identity"></a>Aktivera flera identiteter

Som standard betraktas appar som en enda identitet och SDK anger processidentiteten till den registrerade användaren. Om du vill aktivera stöd för flera identiteter måste du lägga till en boolesk inställning med namnet `MultiIdentity` och värdet ”Ja” i **IntuneMAMSettings**-ordlistan i appens Info.plist.

> [!NOTE]
> När flera identiteter aktiveras anges processidentiteten, UI-identiteten och trådidentiteterna till noll. Appen ansvarar för att ställa in dem på rätt sätt.


### <a name="switching-identities"></a>Växla identitet

* **Appinitierad identitetsväxling**:

    Vid start anses att multiidentitetsappar körs under ett okänt ej hanterat konto. Gränssnittet för villkorlig start körs inte och inga principer tvingas på appen. Det är appens ansvar att meddela SDK när identiteten ska ändras. Detta sker vanligtvis när appen är på väg att visa data för ett visst användarkonto.

    Ett exempel är om användaren försöker öppna ett dokument, en postlåda eller en flik på en bärbar dator. Appen måste meddela SDK innan filen, postlådan eller fliken öppnas. Detta görs via `setUIPolicyIdentity` API i `IntuneMAMPolicyManager`. Detta API ska anropas oavsett om användaren hanteras eller inte. Om användaren är hanterad utför SDK kontrollerna för villkorlig start (upplåsningsidentifiering, PIN-kod, autentisering osv.). Resultatet av identitetsväxlingen returneras till appen asynkront via en hanterare för slutförande. Appen ska skjuta upp öppning av dokumentet, postlådan, fliken osv. till en lyckad resultatkod returneras. Om identitetsväxlingen misslyckades ska appen avbryta åtgärden.

* **SDK-initierad identitetsväxling**:

    Det finns fall där SDK måste be appen att växla till en viss identitet. Appar med multiidentitet måste implementera `identitySwitchRequired`-metoden i `IntuneMAMPolicyDelegate` för att hantera denna begäran. När den anropas ska `IntuneMAMAddIdentityResultSuccess` överföras till hanteraren för slutförande om appen kan hantera begäran om att växla till angiven identitet. Om den inte kan hantera växling av identiteten ska appen överföra `IntuneMAMAddIdentityResultFailed` till hanteraren för slutförande. Appen behöver inte anropa `setUIPolicyIdentity` som svar på detta anrop. Om SDK kräver att appen växlar till ett ej hanterat användarkonto kommer den tomma strängen att överföras till `identitySwitchRequired`-anropet.

* **Selektiv rensning**:

    När appen rensas selektivt anropar SDK `wipeDataForAccount`-metoden i `IntuneMAMPolicyDelegate`. Det är appens ansvar att ta bort det angivna användarkontot och eventuella data som är kopplade till det. SDK kan ta bort alla filer som ägs av användaren och gör det om programmet returnerar "FALSKT" från `wipeDataForAccount`-anropet. Tänk på att den här metoden anropas från en bakgrundstråd och appen ska inte returnera förrän alla data för användaren har tagits bort (med undantag för filer om appen returnerar "FALSKT").

## <a name="debug-the-intune-app-sdk-in-xcode"></a>Felsöka Intunes App SDK i Xcode

Innan du testar den MAM-aktiverade appen manuellt med Microsoft Intune kan du använda filen **Settings.bundle** i Xcode. På så sätt kan du ange testprinciper utan att det krävs någon anslutning till Intune. Så här aktiverar du det:

* Lägg till filen Settings.bundle genom att högerklicka på den översta mappen i projektet. Välj Lägg till -> Ny fil i menyn. Välj mallen Settings Bundle (Inställningspaket) under Resurser för att lägga till den.

* I felsökningsversioner kopierar du MAMDebugSettings.plist till Settings.bundle.

* I Root.plist (som finns i Settings.bundle) lägger du till en inställning med "Type" = Child Pane och "FileName" = MAMDebugSettings.

* Under **Inställningar -> Appens namn** aktiverar du Enable Test Policies (Aktivera testprinciper).

* Starta appen (antingen i eller utanför Xcode).

* Under **Inställningar -> Appens namn -> Enable Test Policies (Aktivera testprinciper)** aktiverar du en princip, t.ex. "PIN".

* Starta appen (antingen i eller utanför Xcode). Kontrollera att PIN-koden fungerar som väntat.

> [!NOTE]
> Nu kan du använda **Inställningar -> Appens namn -> Aktivera testprinciper** för att aktivera och växla mellan inställningar.

## <a name="recommended-ios-best-practices"></a>Rekommenderade metoder för iOS

Följande är några rekommenderade metoder när du utvecklar för iOS:

iOS-filsystemet är skiftlägeskänsligt. Se till att versaler och gemener stämmer för filnamn som `libIntuneMAM.a` och `IntuneMAMResources.bundle`.

Om Xcode har problem med att hitta `libIntuneMAM.a`kan du åtgärda problemet genom att lägga till sökvägen till biblioteket i sökvägarna för länkare.



## <a name="faq"></a>Vanliga frågor

 **Måste alla användare av mitt program registreras med MAM-tjänsten?**

Nej.  I själva verket är det bara arbets- eller skolkonton som ska registreras med Intune App SDK.  Appar ansvarar för att fastställa om ett konto används i ett arbets- eller skolsammanhang.   

**Vad gäller för användare som redan har loggat in i programmet?  Behöver de registreras?**

När programmet ansvarar för att registrera användare efter att de har autentiserats ansvarar programmet även för att registrera eventuella befintliga konton som kan ha funnits innan programmet hade MAM-funktioner utan MDM.   


Programmet ska använda `registeredAccounts:`-metoden för att göra detta.  Den här metoden returnerar ett NSDictionary som innehåller alla konton som är registrerade i Intune MAM-tjänsten.  Om några befintliga konton i programmet inte finns i listan ska programmet registrera dessa konton via `registerAndEnrollAccount:`.




**Hur ofta gör SDK nya registreringsförsök?**

SDK försöker automatiskt igen om 24 timmar med alla registreringar som har misslyckats tidigare.  SDK gör detta för att säkerställa att en användare registreras och ta emot principer om användarens organisation har aktiverat MAM efter att användaren loggade in i programmet.

SDK slutar att försöka när det upptäcker att en användare har lyckats registrera programmet.  Det beror på att endast en användare kan registrera ett program vid en viss tidpunkt. Om användaren har avregistrerats påbörjas nya försök med samma 24-timmarsintervall.


**Varför måste användaren avregistreras?**

SDK vidtar regelbundet följande åtgärder i bakgrunden:

 - Om programmet inte har registrerats ännu försöker det att registrera alla registrerade konton var 24:e timme.
 - Om programmet har registrerats kontrollerar SDK om det finns MAM-principuppdateringar var 8:e timme.

Om en användare avregistreras meddelas SDK att användaren inte längre ska använda programmet och kan pausa de ovanstående regelbundna händelserna för det användarkontot.  Det utlöser även avregistrering av appen och selektiv rensning vid behov.

**Ska jag ställa in flaggan doWipe till true i avregistreringsmetoden?**
Den här metoden ska anropas innan användaren loggas ut från programmet.  Om användarens data raderas från programmet som en del av utloggningen kan `doWipe` vara inställt på falskt.  Om programmet däremot inte faktiskt tar bort användarens data ska detta ställas in på sant så att SDK kan radera dessa data manuellt själv.

**Finns det andra sätt att avregistrera ett program?**
Ja, IT-administratören kan skicka ett kommando för selektiv rensning till programmet, vilket gör att användaren avregistreras och användarens data rensas.  SDK hanterar det här scenariot automatiskt och skickar en avisering via ombudsmetoden för avregistrering.

## <a name="submitting-your-app-to-the-app-store"></a>Skicka in din app till App Store
Både det statiska biblioteket och ramverksversioner av Intune App SDK är universella binärfiler, vilket innebär att de innehåller kod för alla enhets- och simuleringsarkitekturer. Apple avvisar appar som skickas till App Store om de innehåller simuleringskod. Vid kompileringen mot det statiska biblioteket för versioner för endast enheten kommer länkaren att ta bort simuleringskoden automatiskt.

Om appen använder **ramverksversionen** av Intune App SDK måste du rensa bort simuleringsarkitekturen manuellt från det universella ramverket innan du skickar in appen till App Store. Anvisningarna nedan hjälper dig att göra detta:

1. Kontrollera att `IntuneMAM.framework` finns på skrivbordet.
2. Kör följande kommandon:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```
    Det första kommandot rensar simuleringsarkitektur från ramverkets dylib.
    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    Det andra kommandot kopierar dylib för endast enheten tillbaka till ramverkskatalogen.



<!--HONumber=Nov16_HO3-->


