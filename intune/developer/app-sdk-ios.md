---
title: Utvecklarhandbok för Microsoft Intune App SDK för iOS
description: Med Microsoft Intune App SDK för iOS kan du lägga till Intune-appskyddsprinciper (även kallade APP- eller MAM-principer) i din ursprungliga iOS-app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/17/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93b48fd5f6482669da923e4c15dcb09c7d328197
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503448"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Utvecklarhandbok för Microsoft Intune App SDK för iOS

> [!NOTE]
> Börja gärna med att läsa artikeln [Kom igång med Intune App SDK Guide](app-sdk-get-started.md). Den här guiden beskriver hur du förbereder dig för integreringen på de plattformar som stöds.

Med Microsoft Intune App SDK för iOS kan du lägga till Intune-appskyddsprinciper (även kallade APP- eller MAM-principer) i din ursprungliga iOS-app. Ett MAM-aktiverat program är ett program som är integrerat med Intune App SDK. Det kan användas av IT-administratörer för att distribuera appskyddsprinciper till din mobilapp om Intune aktivt hanterar appen.

## <a name="prerequisites"></a>Krav

* Du behöver en Mac OS-dator som kör OS X 10.8.5 eller senare och som också har Xcode-version 9 eller senare installerad.

* Appen måste vara anpassad för iOS 11 eller senare.

* Läs [licensvillkoren för Intune App SDK för iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf). Skriv ut och behåll en kopia av licensvillkoren. Genom att ladda ned och använda Intune App SDK för iOS samtycker du till de här licensvillkoren.  Om du inte godkänner dem ska du inte använda programvaran.

* Hämta filerna för Intune App SDK för iOS på [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk-repository"></a>Vad finns i SDK-lagringsplatsen

Följande filer är relevanta för appar/tillägg som inte innehåller någon SWIFT-kod eller som kompileras med en version av Xcode före 10,2:

* **IntuneMAM.framework**: Intune App SDK-ramverket. Vi rekommenderar att du länkar det här ramverket till appen/tilläggen för att aktivera hantering av klient program i Intune. Vissa utvecklare kan dock föredra prestanda fördelarna i det statiska biblioteket. Se följande.

* **libIntuneMAM.a**: Det statiska Intune App SDK-biblioteket. Utvecklare kan välja att länka det statiska biblioteket i stället för ramverket. Eftersom statiska bibliotek bäddas in direkt i appens/tilläggets binärfil vid Bygg tiden, finns det några fördelar med att starta tid för att använda det statiska biblioteket. Att integrera den i din app är dock en mer komplicerad process. Om din app innehåller tillägg och länkar det statiska biblioteket till appen och tilläggen resulterar i en större samlings paket storlek, eftersom det statiska biblioteket bäddas in i varje app/tillägg-binärfil. När du använder ramverket kan appar och tillägg dela samma Intune SDK-binärfil, vilket resulterar i en mindre app-storlek.

* **IntuneMAMResources.Bundle**: ett resurspaket som innehåller resurser som SDK är beroende av. Resurs samlingen krävs endast för appar som integrerar det statiska biblioteket (libIntuneMAM. a).

Följande filer är relevanta för appar/tillägg som innehåller SWIFT-kod och kompileras med Xcode 10.2 +:

* **IntuneMAMSwift. Framework**: INTUNE app SDK Swift-ramverket. Det här ramverket innehåller alla sidhuvuden för API: er som din app kommer att anropa. Länka det här ramverket till appen/tilläggen för att aktivera hantering av klient program i Intune.

* **IntuneMAMSwiftStub. Framework**: INTUNE app SDK Swift stub-ramverket. Detta är ett obligatoriskt beroende av IntuneMAMSwift. Framework som Apps/extensions måste länka till.


Följande filer är relevanta för alla appar/omfattningar:

* **IntuneMAMConfigurator**: ett verktyg som används för att konfigurera appen eller tilläggets info. plist med minsta antal ändringar som krävs för Intune-hantering. Beroende på funktionerna i appen eller tillägget kan du behöva göra ytterligare manuella ändringar i filen info. plist.

* **Rubriker**: visar offentliga API:er för Intune App SDK. De här rubrikerna ingår i ramverken för IntuneMAM/IntuneMAMSwift, så utvecklare som använder något av ramverken behöver inte lägga till huvuden till sitt projekt manuellt. Utvecklare som väljer att länka till det statiska biblioteket (libIntuneMAM. a) måste ta med dessa huvuden manuellt i projektet.

Följande huvudfiler innehåller API:er, datatyper och protokoll som Intune App SDK tillgängliggör för utvecklare:

-  IntuneMAMAppConfig.h
-  IntuneMAMAppConfigManager.h
-  IntuneMAMDataProtectionInfo.h
-  IntuneMAMDataProtectionManager.h
-  IntuneMAMDefs.h
-  IntuneMAMDiagnosticConsole.h
-  IntuneMAMEnrollmentDelegate.h
-  IntuneMAMEnrollmentManager.h
-  IntuneMAMEnrollmentStatus.h
-  IntuneMAMFileProtectionInfo.h
-  IntuneMAMFileProtectionManager.h
-  IntuneMAMLogger.h
-  IntuneMAMPolicy.h
-  IntuneMAMPolicyDelegate.h
-  IntuneMAMPolicyManager.h
-  IntuneMAMVersionInfo.h

Utvecklare kan tillgängliggöra innehållet i alla föregående huvudfiler genom att helt enkelt importera IntuneMAM.h


## <a name="how-the-intune-app-sdk-works"></a>Hur Intune App SDK fungerar

Målet med Intune App SDK för iOS är att lägga till hanteringsfunktioner i iOS-program med minimala kodändringar. Färre kodändringar innebär kortare tid innan produkten är klar, samtidigt som mobilappen blir mer konsekvent och stabil.


## <a name="build-the-sdk-into-your-mobile-app"></a>Skapa SDK i din mobilapp

Följ dessa steg för att aktivera Intune App SDK:

1. **Alternativ 1 – Framework (rekommenderas)** : om du använder Xcode 10,2 + och din app/Extension innehåller SWIFT-kod, länkar `IntuneMAMSwift.framework` och `IntuneMAMSwiftStub.framework` till målet: dra `IntuneMAMSwift.framework` och `IntuneMAMSwiftStub.framework` till listan med **inbäddade binärfiler** för projekt målet.

    Annars kan du länka `IntuneMAM.framework` till målet: dra `IntuneMAM.framework` till listan **inbäddade binärfiler** för projekt målet.

   > [!NOTE]
   > Om du använder ramverket måste du ta bort simuleringsarkitekturen manuellt från det universella ramverket innan du skickar in appen till App Store. Se [Skicka in din app till App Store](#submit-your-app-to-the-app-store) för mer information.

   **Alternativ 2 – statiskt bibliotek**: det här alternativet är endast tillgängligt för appar/tillägg som innehåller ingen SWIFT-kod eller som har skapats med Xcode < 10,2. Länk till `libIntuneMAM.a`-biblioteket. Dra `libIntuneMAM.a`-biblioteket till listan med **länkade ramverk och bibliotek** i projektets målkatalog.

    ![Intune App SDK iOS: länkade ramverk och bibliotek](./media/app-sdk-ios/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Lägg till `-force_load {PATH_TO_LIB}/libIntuneMAM.a` i någon av följande och ersätt `{PATH_TO_LIB}` med platsen för Intune App SDK:
   * Projektets `OTHER_LDFLAGS` konfigurationsinställning för kompilering.
   * Xcode-användargränssnittets **Andra länkarflaggor**.

     > [!NOTE]
     > Leta reda på `PATH_TO_LIB` genom att välja filen `libIntuneMAM.a` och välja **Get Info** (Hämta information) från menyn **Arkiv**. Kopiera och klistra in informationen om **Var** (sökvägen) från avsnittet **Allmänt** i fönstret **Information**.

     Lägg till `IntuneMAMResources.bundle`-resurspaketet i projektet genom att dra resurspaketet till **Copy Bundle Resources** (Kopiera paketresurser) i **Build Phases** (Versionsfaser).

     ![Intune App SDK iOS: kopiera paketresurser](./media/app-sdk-ios/intune-app-sdk-ios-copy-bundle-resources.png)
         
2. Lägg till dessa iOS-ramverk i projektet:  
-  MessageUI.framework  
-  Security.framework  
-  MobileCoreServices.framework  
-  SystemConfiguration.framework  
-  libsqlite3.TBD  
-  libc ++ .tbd  
-  ImageIO.framework  
-  LocalAuthentication.framework  
-  AudioToolbox.framework  
-  QuartzCore.framework  
-  WebKit.framework

3. Aktivera delning av nyckelringar (om det inte redan är aktiverat) genom att välja **Funktioner** i varje projektmål och aktivera reglaget för **delning av nyckelringar**. Delning av nyckelringar krävs för att du ska kunna fortsätta till nästa steg.

   > [!NOTE]
   > Etableringsprofilen måste ha stöd för nya värden för delning av nyckelringar. Åtkomstgrupper för nyckelringar ska ha stöd för jokertecken. Du kan bekräfta detta genom att öppna filen .mobileprovision i en textredigerare, söka efter **keychain-access-groups** och se till att du har ett jokertecken. Exempel:
   >
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

4. När du har aktiverat delning av nyckelringar följer du dessa steg för att skapa en separat åtkomstgrupp där data i Intune App SDK kommer att sparas. Du kan skapa en åtkomstgrupp för nyckelringar med hjälp av användargränssnittet eller med behörighetsfilen. Om du använder användargränssnittet för att skapa gruppen med nyckelhanterare, följer du dessa steg:

     a. Om mobilappen inte har definierat några åtkomstgrupper för nyckelringar lägger du till appens paket-ID som den **första** gruppen.
    
    b. Lägg till den delade gruppen med nyckelhanterare `com.microsoft.intune.mam` till dina befintliga åtkomstgrupper. Intune App SDK använder den här åtkomstgruppen för att lagra data.
    
    c. Lägg till `com.microsoft.adalcache` i dina befintliga åtkomstgrupper.
    
      ![Intune App SDK iOS: delning av nyckelringar](./media/app-sdk-ios/intune-app-sdk-ios-keychain-sharing.png)
    
    d. Om du redigerar behörighetsfilen direkt, i stället för att använda det Xcode-användargränssnitt som visas ovan för att skapa åtkomstgrupperna för nyckelringen, ska du lägga till åtkomstgrupperna för nyckelringen med `$(AppIdentifierPrefix)` (Xcode hanterar detta automatiskt). Exempel:
    
      - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
      - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
      > [!NOTE]
      > En rättighetsfil är en XML-fil som är unik för ditt mobila program. Den används för att ange särskilda behörigheter och funktioner i din iOS-app. Om din app inte tidigare har en behörighetsfil bör aktiveringen av nyckelringsdelning (steg 3) ha fått Xcode att generera en för din app. Kontrollera att appens paket-ID är den första posten i listan.

5. Inkludera varje protokoll som appen skickar till `UIApplication canOpenURL` i matrisen `LSApplicationQueriesSchemes` i appens Info.plist-fil. Glöm inte att spara ändringarna innan du fortsätter till nästa steg.

6. Om din app inte redan använder FaceID redan bör du se till att [NSFaceIDUsageDescription Info.plist-nyckeln](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75) har konfigurerats med ett standardmeddelande. Detta krävs så att iOS meddelar användaren om hur appen har för avsikt att använda FaceID. En inställning för Intune-appskyddsprincip gör att FaceID kan användas som en åtkomstmetod till appen när den konfigurerats av IT-administratören.

7. Använd verktyget IntuneMAMConfigurator som ingår i [SDK-lagringsplatsen](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) för att slutföra konfigurationen av din apps Info.plist. Verktyget har tre parametrar:

   |Egenskap|Använd så här|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (Valfritt) `<Path to the output plist>` |

Om parametern -o inte anges, kommer indatafilen att ändras på plats. Verktyget är idempotent och ska köras igen när det har gjorts ändringar i appens Info.plist eller rättigheter. Du bör också hämta och köra den senaste versionen av verktyget när du uppdaterar Intune SDK, om konfigurationskraven för Info.plist har ändrats i den senaste versionen.

## <a name="configure-adalmsal"></a>Konfigurera ADAL/MSAL

Intune App SDK kan använda antingen [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) eller [Microsoft Authentication Library](https://github.com/AzureAD/microsoft-authentication-library-for-objc) för autentisering och villkorliga start scenarier. Den förlitar sig även på ADAL/MSAL för att registrera användarens identitet i MAM-tjänsten för hantering utan enhetsregistreringsscenarier.

Normalt kräver ADAL/MSAL att appar registreras med Azure Active Directory (AAD) och erhåller ett unikt klient-ID och omdirigerings-URL, för att garantera säkerheten i de token som appen beviljats. Om appen redan använder ADAL eller MSAL för att autentisera användare, måste appen använda befintliga registreringsvärden och åsidosätta standardvärdena för Intune App SDK. Detta garanterar att användare inte uppmanas att autentisera sig två gånger (en gång av Intune App SDK och en gång av appen).

Om din app inte redan använder ADAL eller MSAL och du inte behöver komma åt någon AAD-resurs, behöver du inte konfigurera en klient program registrering i AAD om du väljer att integrera ADAL. Om du väljer att integrera MSAL måste du konfigurera en app-registrering och åsidosätta standardvärdet för Intune-klienten och omdirigerings-URI.  

Vi rekommenderar att din app länkar till den senaste versionen av [ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) eller [MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-objc/releases).

### <a name="link-to-adal-or-msal-binaries"></a>Länk till ADAL-eller MSAL-binärfiler

**Alternativ 1 –** Följ [de här stegen](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download) för att länka din app till ADAL-binärfilerna.

**Alternativ 2-** Alternativt kan du följa [de här anvisningarna](https://github.com/AzureAD/microsoft-authentication-library-for-objc#installation) för att länka din app till MSAL-binärfilerna.

1. Om appen inte har definierat några åtkomstgrupper för nyckelringar lägger du till appens paket-ID som den första gruppen.

2. Aktivera enkel inloggning (SSO) med ADAL/MSAL genom att lägga till `com.microsoft.adalcache` i nyckelringens åtkomstgrupper.

3. Om du uttryckligen ställer in nyckelringsgruppen för ADAL-delad cache ser du till att den är inställd på `<appidprefix>.com.microsoft.adalcache`. ADAL ställer in detta åt dig förutsatt att du inte åsidosätter det. Om du vill ange en anpassad nyckelringsgrupp som ersätter `com.microsoft.adalcache` anger du det i Info.plist-filen under IntuneMAMSettings med hjälp av nyckeln `ADALCacheKeychainGroupOverride`.

### <a name="configure-adalmsal-settings-for-the-intune-app-sdk"></a>Konfigurera ADAL/MSAL-inställningar för Intune App SDK

Om din app redan använder ADAL eller MSAL för autentisering och har egna Azure Active Directory-inställningar, kan du tvinga Intune App SDK att använda samma inställningar under autentiseringen mot Azure Active Directory. Detta garanterar att appen inte frågar användaren om autentisering två gånger. Se [Konfigurera inställningar för Intune App SDK](#configure-settings-for-the-intune-app-sdk) för information om hur du fyller i följande inställningar:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Om din app redan använder ADAL eller MSAL, krävs följande konfigurationer:

1. I Info.plist-filen i projektet, under ordlistan **IntuneMAMSettings** med nyckelnamnet `ADALClientId`, anger du det klient-ID som ska användas för ADAL-anrop.

2. Ange också Azure AD-utfärdare under ordlistan **IntuneMAMSettings** med nyckelnamnet `ADALAuthority`.

3. Under ordlistan **IntuneMAMSettings** med nyckelnamnet `ADALRedirectUri` anger du också den omdirigerings-URI som ska användas för ADAL-anrop. Du kan också ange `ADALRedirectScheme` i stället om programmets omdirigerings-URI är i formatet `scheme://bundle_id`.

Dessutom kan appar åsidosätta de här Azure AD-inställningarna under körning. Gör detta genom att ange egenskaperna `aadAuthorityUriOverride`, `aadClientIdOverride` och `aadRedirectUriOverride` på instansen `IntuneMAMPolicyManager`.

4. Se till att stegen som ger din iOS appbehörigheter till APP-tjänsten följs. Använd instruktionerna i [Kom igång med Intune SDK-guiden](app-sdk-get-started.md#next-steps-after-integration) under [Ge din app åtkomst till Intune-appskyddstjänsten (valfritt)](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional).  

> [!NOTE]
> Metoden Info.plist rekommenderas för alla inställningar som är statiska och behöver inte fastställas vid körning. Värden som tilldelats egenskaperna `IntuneMAMPolicyManager` har företräde framför alla motsvarande värden som anges i Info.plist och behålls även när appen startas om. SDK fortsätter att använda dem för principkontroller tills användaren har avregistrerats eller värdena har rensats eller ändrats.

### <a name="if-your-app-does-not-use-adal-or-msal"></a>Om din app inte använder ADAL eller MSAL

Som tidigare nämnts kan Intune App SDK antingen använda biblioteket för [Azure Active Directory autentisering](https://github.com/AzureAD/azure-activedirectory-library-for-objc) eller [Microsoft Authentication Library](https://github.com/AzureAD/microsoft-authentication-library-for-objc) för autentisering och villkorliga start scenarier. Den förlitar sig även på ADAL/MSAL för att registrera användarens identitet i MAM-tjänsten för hantering utan enhetsregistreringsscenarier. Om **din app inte använder ADAL eller MSAL för en egen autentiseringsmekanism**kan du behöva konfigurera anpassade AAD-inställningar, beroende på vilket autentiseringspaket du väljer att integrera:   

ADAL – Intune App SDK tillhandahåller standardvärden för ADAL-parametrar och hanterar autentisering mot Azure AD. Utvecklare behöver inte ange några värden för de ADAL-inställningar som tidigare nämnts. 

MSAL – utvecklare behöver skapa en app-registrering i AAD med en anpassad omdirigerings-URI i det format som anges [här](https://github.com/AzureAD/microsoft-authentication-library-for-objc/wiki/Migrating-from-ADAL-Objective-C-to-MSAL-Objective-C#app-registration-migration). Utvecklare bör ange `ADALClientID` och `ADALRedirectUri` inställningar som tidigare nämnts, eller motsvarande `aadClientIdOverride`-och `aadRedirectUriOverride` egenskaper på `IntuneMAMPolicyManager`-instansen. Utvecklare bör också se till att de följer steg 4 i föregående avsnitt för att ge appens registrerings åtkomst till Intune App Protection-tjänsten.

### <a name="special-considerations-when-using-msal"></a>Särskilda överväganden vid användning av MSAL 

1. **Kontrol lera din webbvy** – vi rekommenderar att program inte använder SFSafariViewController, SFAuthSession eller ASWebAuthSession som sin webbvy för appar som initieras av MSAL interaktiva auth-åtgärder. Om din app av någon anledning måste använda någon av dessa webvyer för interaktiva MSAL auth-åtgärder, måste du också ange `SafariViewControllerBlockedOverride` `true` under ord listan `IntuneMAMSettings` i programmets info. plist. Varning! Intunes SafariViewController-hookar kommer att inaktive ras för att aktivera auth-sessionen. Detta medför risk för att data läcker någon annan stans i appen om programmet använder SafariViewController för att Visa företags data, så att programmet inte ska Visa företags data i någon av dessa typer av WebView-typer.
2. Att **Länka både ADAL och MSAL** -utvecklare måste välja om de vill att Intune ska föredra MSAL över ADAL i det här scenariot. Som standard föredrar Intune ADAL-versioner som stöds för MSAL-versioner, om båda är länkade vid körning. Intune kommer bara att föredra en MSAL-version som stöds när den första autentiseringen i Intune `IntuneMAMUseMSALOnNextLaunch` `true` i `NSUserDefaults`. Om `IntuneMAMUseMSALOnNextLaunch` är `false` eller inte har angetts, kommer Intune att återgå till standard beteendet. Som namnet antyder börjar ändringen i `IntuneMAMUseMSALOnNextLaunch` gälla vid nästa start.


## <a name="configure-settings-for-the-intune-app-sdk"></a>Konfigurera inställningar för Intune App SDK

Du kan använda ordlistan **IntuneMAMSettings** i filen Info.plist i programmet för att installera och konfigurera Intune App SDK. Om ordlistan IntuneMAMSettings inte visas i din Info.plist-fil bör du skapa den.

Under ordlistan IntuneMAMSettings kan du lägga till följande inställningar med stöd för att konfigurera Intune App SDK.

Några av de här inställningarna kan ha beskrivits i föregående avsnitt och vissa gäller inte för alla appar.

Inställningen  | Typ  | Definition | Obligatoriskt?
--       |  --   |   --       |  --
ADALClientId  | Sträng  | Appens klient-ID för Azure AD. | Krävs för alla appar som använder MSAL och alla ADAL-appar som har åtkomst till en AAD-resurs som inte är Intune. |
ADALAuthority | Sträng | Appens Azure AD-auktoritet används. Du bör använda din egen miljö där AAD-konton har konfigurerats. | Krävs om appen använder ADAL eller MSAL för att komma åt en AAD-resurs som inte är Intune. Om detta värde saknas används ett Intune-standardvärde.|
ADALRedirectUri  | Sträng  | Appens omdirigerings-URI för Azure AD. | ADALRedirectUri eller ADALRedirectScheme krävs för alla appar som använder MSAL och alla ADAL-appar som har åtkomst till en AAD-resurs som inte är Intune.  |
ADALRedirectScheme  | Sträng  | Appens omdirigeringsschema för Azure AD. Detta kan användas i stället för ADALRedirectUri om programmets omdirigerings-URI har formatet `scheme://bundle_id`. | ADALRedirectUri eller ADALRedirectScheme krävs för alla appar som använder MSAL och alla ADAL-appar som har åtkomst till en AAD-resurs som inte är Intune. |
ADALLogOverrideDisabled | Boolesk  | Anger om SDK dirigerar alla ADAL/MSAL-loggar (inklusive eventuella ADAL-anrop från appen) till den egna loggfilen. Standardvärdet är NO (NEJ). Ange YES (JA) om appen ska ange egna återanrop i ADAL/MSAL-loggen. | Valfritt. |
ADALCacheKeychainGroupOverride | Sträng  | Anger nyckelringsgruppen som ska användas för ADAL/MSAL-cache i stället för ”com.microsoft.adalcache”. Observera att detta inte har app-id-prefixet. Det föregår strängen som anges vid körning. | Valfritt. |
AppGroupIdentifiers | Strängmatris  | Matris med appgrupper från appens behörigheter i avsnittet com.apple.security.application-groups | Krävs om appen använder programgrupper. |
ContainingAppBundleId | Sträng | Anger paket-ID:t för programmet som ingår i tillägget. | Krävs för iOS-tillägg. |
DebugSettingsEnabled| Boolesk | Om detta är inställt på JA kan testprinciper i inställningspaketet användas. Program bör *inte* levereras med den här inställningen aktiverad. | Valfritt. Standardvärdet är no (nej). |
AutoEnrollOnLaunch| Boolesk| Anger om programmet ska försöka registrera sig automatiskt vid start om en befintlig hanterad identitet identifieras och den inte redan har gjort det. Standardvärdet är NO (NEJ). <br><br> Kommentarer: Om ingen hanterad identitet hittas eller om det inte finns en tillgänglig giltig token för identiteten i ADAL/MSAL-cachen, misslyckas registreringsförsöket utan att användaren uppmanas att ange autentiseringsuppgifter, om inte MAMPolicyRequired också är inställt på YES (JA) för appen. | Valfritt. Standardvärdet är no (nej). |
MAMPolicyRequired| Boolesk| Anger om appen kommer att blockeras från att starta om appen inte har en Intune-appskyddsprincip. Standardvärdet är NO (NEJ). <br><br> Obs! Appar kan inte skickas till App Store om MAMPolicyRequired är inställt på YES (JA). Om du ställer in MAMPolicyRequired till YES (JA) bör även AutoEnrollOnLaunch ha värdet YES (JA). | Valfritt. Standardvärdet är no (nej). |
MAMPolicyWarnAbsent | Boolesk| Anger om appen kommer att varna användaren under start om appen inte har en Intune-appskyddsprincip. <br><br> Obs! Användare kommer fortfarande att kunna använda appen utan en princip när varningen har ignorerats. | Valfritt. Standardvärdet är no (nej). |
MultiIdentity | Boolesk| Anger om appen är multiidentitetsmedveten. | Valfritt. Standardvärdet är no (nej). |
SafariViewControllerBlockedOverride | Boolesk| Inaktiverar Intunes SafariViewController-hookar för att aktivera MSAL-autentisering via SFSafariViewController, SFAuthSession eller ASWebAuthSession. | Valfritt. Standardvärdet är no (nej). Varning: kan leda till data läckage om det används felaktigt. Aktivera endast om det är absolut nödvändigt. Se [särskilda överväganden när du använder MSAL](#special-considerations-when-using-msal) för mer information.  |
SplashIconFile <br>SplashIconFile~ipad | Sträng  | Anger filen för Intunes ikon för välkomstskärmen (startskärm). | Valfritt. |
SplashDuration | Antal | Kortaste tid i sekunder som startskärmen för Intune visas när programmet startas. Standardvärdet är 1,5. | Valfritt. |
BackgroundColor| Sträng| Anger bakgrunds färgen för Intune SDK: s UI-komponenter. Godkänner en hexadecimal RGB-sträng med formatet #XXXXXX, där X kan vara något mellan 0–9 eller A–F. Pundtecknet kan utelämnas.   | Valfritt. Standardvärdet för systemets bakgrunds färg, som kan variera mellan olika versioner av iOS och enligt inställningen iOS-mörkt läge. |
ForegroundColor| Sträng| Anger förgrunds färgen för Intune SDK: s UI-komponenter, till exempel textfärg. Godkänner en hexadecimal RGB-sträng med formatet #XXXXXX, där X kan vara något mellan 0–9 eller A–F. Pundtecknet kan utelämnas.  | Valfritt. Standardvärdet för system etiketts färgen, som kan variera mellan olika versioner av iOS och enligt inställningen iOS-mörkt läge. |
AccentColor | Sträng| Anger accentfärg för Intune SDK: s UI-komponenter, t. ex. knapp text färg och färg markerings färg. Godkänner en hexadecimal RGB-sträng med formatet #XXXXXX, där X kan vara något mellan 0–9 eller A–F. Pundtecknet kan utelämnas.| Valfritt. Standardinställningen är systemblått. |
SupportsDarkMode| Boolesk | Anger om Intune SDK: s färg schema ska Observera inställningen system mörk läge, om inget uttryckligt värde har angetts för BackgroundColor/ForegroundColor/AccentColor | Valfritt. Standardvärdet är ja. |
MAMTelemetryDisabled| Boolesk| Anger om SDK inte ska skicka några telemetridata till serverdelen.| Valfritt. Standardvärdet är no (nej). |
MAMTelemetryUsePPE | Boolesk | Anger om MAM SDK ska skicka data till PPE-telemetriserverdelen. Använd det här när du testar dina appar med Intune-principen så att testets telemetridata inte blandas med kunddata. | Valfritt. Standardvärdet är no (nej). |
MaxFileProtectionLevel | Sträng | Valfritt. Tillåter appen att ange maximal `NSFileProtectionType` som den stöder. Det här värdet åsidosätter den princip som skickas av tjänsten om nivån är högre än vad programmet stöder. Möjliga värden: `NSFileProtectionComplete`, `NSFileProtectionCompleteUnlessOpen`, `NSFileProtectionCompleteUntilFirstUserAuthentication`, `NSFileProtectionNone`.|
OpenInActionExtension | Boolesk | Inställt på YES (JA) för Open in Action-tillägg. Mer information finns i avsnittet Sharing Data via UIActivityViewController (Dela data via UIActivityViewController). |
WebViewHandledURLSchemes | Strängmatris | Anger de URL-scheman som appens WebView hanterar. | Krävs om appen använder en WebView som hanterar URL:er via länkar och/eller javascript. |

## <a name="receive-app-protection-policy"></a>Ta emot appskyddsprincip

### <a name="overview"></a>Översikt

För att få appskyddsprincipen för Intune måste apparna starta en registreringsbegäran med Intune MAM-tjänsten. Appar kan konfigureras i Intune-konsolen för att ta emot appskyddsprincipen med eller utan enhetsregistrering. Med appskyddsprincip utan registrering, så kallad **APP-WE** eller MAM-WE, kan appar hanteras av Intune utan att enheten behöver registreras i Intunes hantering av mobila enheter (MDM). I båda fallen krävs registrering med Intune MAM-tjänsten för att ta emot principen.

> [!Important]
> Intune App SDK för iOS använder 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciper. Alla appar måste ha den aktuella SDK-versionen för att delning av skyddade data ska vara möjlig.

### <a name="apps-that-already-use-adal-or-msal"></a>Appar som redan använder ADAL eller MSAL

Appar som redan använder ADAL eller MSAL ska anropa `registerAndEnrollAccount`-metoden i `IntuneMAMEnrollmentManager`-instansen när användaren har autentiserats:

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

Genom att anropa `registerAndEnrollAccount`-metoden registrerar SDK användarkontot och försöker registrera appen för det här kontot. Om registreringen misslyckas av någon anledning försöker SDK genomföra registreringen igen automatiskt 24 timmar senare. Appen kan i felsökningssyfte ta emot [aviseringar](#status-result-and-debug-notifications) om resultaten av eventuella registreringsbegäranden via ett ombud.

När detta API har anropats kan appen fortsätta att fungera som vanligt. Om registreringen lyckas meddelar SDK användaren att appen behöver startas om. Användaren kan då starta om appen omedelbart.

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal-or-msal"></a>Appar som inte använder ADAL eller MSAL

En app som inte loggar in användaren med ADAL eller MSAL kan fortfarande ta emot appskyddsprinciper från Intune MAM-tjänsten genom att anropa API:t och låta SDK:n hantera den autentiseringen. Appar bör använda den här metoden när de inte har autentiserat en användare med Azure AD men ändå måste hämta appskyddsprinciper för att skydda data. Ett exempel är om en annan autentiseringstjänst används för inloggning i en app, eller om appen inte stöder inloggning över huvud taget. För att göra detta kan programmet anropa `loginAndEnrollAccount`-metoden på `IntuneMAMEnrollmentManager`-instansen:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

Genom att anropa den här metoden frågar SDK användaren om autentiseringsuppgifter om ingen befintlig token kan hittas. SDK:n försöker därefter registrera appen med Intune MAM-tjänsten för det angivna användarkontot. Metoden kan anropas med "noll" som identitet. I sådant fall registrerar SDK med den befintliga hanterade användaren på enheten (vid MDM) eller frågar användaren om ett användarnamn om det inte går att hitta en befintlig användare.

Om registreringen misslyckas bör appen överväga att anropa detta API igen vid ett senare tillfälle, beroende på detaljerna kring felet. Appen kan ta emot [aviseringar](#status-result-and-debug-notifications) om resultaten av eventuella registreringsbegäranden via ett ombud.

När detta API har anropats kan appen fortsätta att fungera som vanligt. Om registreringen lyckas meddelar SDK användaren att appen behöver startas om.

Exempel:

```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>Låta Intune hantera autentisering och registrering vid start

Om du vill att Intune SDK ska hantera all autentisering med hjälp av ADAL/MSAL och registrering innan din app har startats helt, och din app alltid kräver APP-princip, behöver du inte använda `loginAndEnrollAccount`-API. Du behöver bara ställa in de två inställningarna nedan som YES (JA) i ordlistan IntuneMAMSettings i appens Info.plist.

Inställningen  | Typ  | Definition |
--       |  --   |   --       |  
AutoEnrollOnLaunch| Boolesk| Anger om programmet ska försöka registrera sig automatiskt vid start om en befintlig hanterad identitet identifieras och den inte redan har gjort det. Standardvärdet är NO (NEJ). <br><br> Kommentar: Om ingen hanterad identitet hittas eller om det inte finns en tillgänglig giltig token för identiteten i ADAL/MSAL-cachen, misslyckas registreringsförsöket utan att användaren uppmanas att ange autentiseringsuppgifter, om inte MAMPolicyRequired också är inställt på YES (JA) för appen. |
MAMPolicyRequired| Boolesk| Anger om appen kommer att blockeras från att starta om appen inte har en Intune-appskyddsprincip. Standardvärdet är NO (NEJ). <br><br> Obs! Appar kan inte skickas till App Store med MAMPolicyRequired angiven som YES (JA). Om du ställer in MAMPolicyRequired till YES (JA) bör även AutoEnrollOnLaunch ha värdet YES (JA). |

Om du väljer det här alternativet för din app behöver du inte hantera omstart av appen efter registreringen.

### <a name="deregister-user-accounts"></a>Avregistrera användarkonton

Innan en användare loggas ut från en app bör appen avregistrera användaren från SDK. Detta säkerställer:

1. Nya registreringsförsök sker inte längre för användarens konto.

2. Appskyddsprincipen tas bort.

3. Om appen startar en selektiv rensning (valfritt) raderas eventuella företagsdata.

Innan användaren loggas ut måste appen anropa följande metod i `IntuneMAMEnrollmentManager`-instansen:

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

Den här metoden måste anropas innan användarkontots Azure AD-token tas bort. SDK:n behöver användarens ADD-token för att göra specifika begäranden till Intune MAM-tjänsten för användarens räkning.

Om appen ska ta bort användarens företagsdata på egen hand ska `doWipe`-flaggan anges till falskt. Annars kan appen se till att SDK initierar en selektiv rensning. Detta resulterar i ett anrop till appens ombud för selektiv rensning.

Exempel:

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>Status-, resultat- och felsökningsmeddelanden

Appen kan ta emot status-, resultat- och felsökningsmeddelanden om följande begäranden till Intunes MAM-tjänst:

* Begäran om registrering
* Begäran om principuppdatering
* Begäran om avregistrering

Meddelanden visas via delegerade metoder i `IntuneMAMEnrollmentDelegate.h`:

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

* Identiteten för det konto som är kopplat till begäran
* En statuskod som visar resultatet av begäran
* En felsträng med en beskrivning av statuskoden
* Ett `NSError`-objekt. Det här objektet definieras i `IntuneMAMEnrollmentStatus.h`, tillsammans med de specifika statuskoder som kan returneras.

### <a name="sample-code"></a>Exempelkod

Det här är exempel på implementeringar av ombudsmetoderna:

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>Omstart av program

När en app tar emot MAM-principer för första gången måste den startas om för att tillämpa obligatoriska hookar. För att meddela appen att en omstart krävs tillhandahåller SDK en delegeringsmetod i `IntuneMAMPolicyDelegate.h`.

```objc
 - (BOOL) restartApplication
```

Returvärdet för den här metoden talar om för SDK om programmet ska hantera den omstart som krävs:

* Om sant returneras måste programmet hantera omstarten.

* Om falskt returneras startar SDK om programmet efter att denna metod har returnerats. SDK visar direkt en dialogruta som ber användaren att starta om programmet.

## <a name="customize-your-apps-behavior-with-apis"></a>Anpassa appens beteende med API:er

Intune App SDK har flera API: er som du kan använda för att hämta information om den Intune APP-princip som distribueras till appen. Du kan använda informationen för att ändra appens beteende. Tabellen nedan innehåller information om vissa grundläggande Intune-klasser som du kommer att använda.

Klass | Beskrivning
----- | -----------
IntuneMAMPolicyManager.h | Klassen IntuneMAMPolicyManager visar den Intune APP-princip som distribueras till programmet. Klassen visar främst de API: er som är användbara för att [aktivera flera identiteter](app-sdk-ios.md#enable-multi-identity-optional). |
IntuneMAMPolicy.h | Klassen IntuneMAMPolicy tillgängliggör vissa MAM-principinställningar som tillämpas på appen. De här principinställningarna blir tillgängliga så att appen kan anpassa sitt användargränssnitt. De flesta principinställningar tillämpas av SDK och inte appen. Den enda som appen ska implementera är Spara som-kontrollen. Den här klassen tillgängliggör vissa API:er som krävs för att implementera Spara som. |
IntuneMAMFileProtectionManager.h | Klassen IntuneMAMFileProtectionManager tillgängliggör API:er som appen kan använda för att uttryckligen skydda filer och kataloger baserat på en tillhandahållen identitet. Identiteten kan hanteras av Intune eller vara ohanterad, och SDK tillämpar lämplig MAM-princip. Användning av den här klassen är valfritt. |
IntuneMAMDataProtectionManager.h | Klassen IntuneMAMDataProtectionManager tillgängliggör API:er som appen kan använda för att skydda databuffertar baserat på en tillhandahållen identitet. Identiteten kan hanteras av Intune eller vara ohanterad, och SDK tillämpar lämplig kryptering. |

## <a name="implement-save-as-controls"></a>Implementera spara som-kontroller

Intune låter IT-administratörer välja vilka lagringsplatser som en hanterad app kan spara data till. Appar kan köra frågor mot Intune App SDK för tillåtna lagringsplatser med hjälp av `isSaveToAllowedForLocation`-API:et, som definieras i `IntuneMAMPolicy.h`.

Innan appar kan spara hanterade data i molnlagring eller på en lokal plats måste de kontrollera med `isSaveToAllowedForLocation`-API:et för att se om IT-administratören tillåter att data sparas där.

När appar använder `isSaveToAllowedForLocation`-API:et måste de ange lagringsplatsens UPN, om det är tillgängligt.

### <a name="supported-save-locations"></a>Lagringsplatser som stöds

`isSaveToAllowedForLocation`-API:et tillhandahåller konstanter för att kontrollera om IT-administratören tillåter att data sparas på följande platser som definieras i `IntuneMAMPolicy.h`:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Apparna bör använda konstanterna i `isSaveToAllowedForLocation` för att kontrollera om data kan sparas till platser som betraktas som ”hanterade”, som till exempel OneDrive för företag, eller platser som är ”personliga”. API:et bör dessutom användas när appen inte kan kontrollera om en plats är ”hanterad” eller ”personlig”.

Platser som är "personliga" representeras av `IntuneMAMSaveLocationOther`-konstanten.

`IntuneMAMSaveLocationLocalDrive`-konstanten bör användas när appen sparar data till en plats på den lokala enheten.

## <a name="share-data-via-uiactivityviewcontroller"></a>Dela data via UIActivityViewController

Från och med version 8.0.2 kan Intune App SDK filtrera `UIActivityViewController`-åtgärder så att bara Intune-hanterade resursplatser är tillgängliga att välja. Detta beteende kommer att kontrolleras av överföringsprincipen för programdata.

### <a name="copy-to-actions"></a>Kopiera till-åtgärder

När du delar dokument via `UIActivityViewController` och `UIDocumentInteractionController` visar iOS ”Kopiera till”-åtgärderna för varje program som stöder att det dokument som delas öppnas. Programmen anger de dokumenttyper som de stöder via `CFBundleDocumentTypes`-inställningen i sin Info.plist. Den här typen av delning kommer inte längre att vara tillgängligt om principen förbjuder delning till ohanterade program. Som en ersättning kommer användarna att behöva lägga till ett icke-UI-åtgärdstillägg för sina program och länka det till Intune App SDK. Åtgärdstillägget är bara en stub. SDK implementerar fildelningsbeteendet. Följ stegen nedan:

1. Programmet måste ha minst en schemeURL som definierats under dess Info.plist `CFBundleURLTypes`.

2. Dina program och åtgärdstillägget måste dela minst en app-grupp, och app-gruppen måste anges under `AppGroupIdentifiers`-matrisen under appens och tilläggets IntuneMAMSettings-ordlistor.

3. Döp åtgärdstillägget ”Öppnat i” följt av programnamnet. Lokalisera Info.plist efter behov.

4. Ange en mallikon för tillägget enligt beskrivningen i [Apples utvecklardokumentation](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/). Alternativt kan du använda IntuneMAMConfigurator-verktyget för att generera dessa avbildningar från programmets .app-katalog. För att göra detta kör du:

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. Under IntuneMAMSettings i tilläggets Info.plist lägger du till en boolesk inställning med namnet `OpenInActionExtension` med värdet YES (JA).

6. Konfigurera `NSExtensionActivationRule` för att stödja en enskild fil och alla typer från programmets `CFBundleDocumentTypes` med prefixet `com.microsoft.intune.mam`. Till exempel om programmet stöder public.text och public.image, skulle aktiveringsregeln vara:

    ```objc
    SUBQUERY (
        extensionItems,
        $extensionItem,
        SUBQUERY (
            $extensionItem.attachments,
            $attachment,
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” ||
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1
    ).@count == 1
    ```

### <a name="update-existing-share-and-action-extensions"></a>Uppdatera befintliga resurs- och åtgärdstillägg

Om appen redan innehåller resurs- eller åtgärdstillägg måste deras `NSExtensionActivationRule` ändras till att tillåta Intune-typerna. För varje typ som stöds av tillägget lägger du till ytterligare en typ med prefixet `com.microsoft.intune.mam`. Till exempel om den befintliga aktiveringsregeln är:  

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data"
    ).@count > 0
).@count > 0
```

Den bör ändras till:

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data
    ).@count > 0
).@count > 0
```

> [!NOTE]
> Verktyget IntuneMAMConfigurator kan användas för att lägga till Intune-typer i aktiveringsregeln. Om din befintliga aktiveringsregel använder fördefinierade strängkonstanter (t.ex. NSExtensionActivationSupportsFileWithMaxCount, NSExtensionActivationSupportsText osv.), kan predikatsyntaxet bli ganska komplext. Verktyget IntuneMAMConfigurator kan också användas för att konvertera aktiveringsregeln från strängkonstanter till en predikatsträng när du lägger till Intune-typerna.

### <a name="what-the-ui-should-look-like"></a>Hur användargränssnittet ska se ut

Gammalt användargränssnitt:

![Delning av data – iOS gamla användargränssnitt för delning](./media/app-sdk-ios/sharing-UI-old.png)

Nytt användargränssnitt:

![Delning av data – iOS nya användargränssnitt för delning](./media/app-sdk-ios/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>Aktivera riktad konfiguration (APP/MAM-appkonfiguration) för dina iOS-program

Med MAM-riktad konfiguration (kallas även MAM-appkonfiguration) kan en app ta emot konfigurationsdata via Intune SDK. Dataformat och eventuella varianter av dessa data måste definieras och kommuniceras till Intune-kunderna av appens ägare/utvecklare.

Intune-administratörerna kan rikta in och distribuera konfigurationsdata via Intune Azure-portalen och Intune Graph API. Appar som deltar i MAM-riktad konfiguration kan tillhandahållas MAM-riktade konfigurationsdata via MAM-tjänsten fr.o.m. version 7.0.1 av Intune App SDK för iOS. Programmets konfigurationsdata push-överförs med vår MAM-tjänst direkt till appen i stället för via MDM-kanalen. Intune App SDK tillhandahåller en klass för att komma åt data som hämtats från dessa konsoler. Följande objekt är förutsättningar:

* Appen måste vara registrerad i Intune MAM-tjänsten innan du kan komma åt användargränssnittet för MAM-riktad konfiguration. Mer information finns i [Ta emot appskyddsprincip](#receive-app-protection-policy).

* Inkludera `IntuneMAMAppConfigManager.h` i appens källfil.

* Anropa `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` för åtkomst till App Config-objektet.

* Anropa lämplig väljare för `IntuneMAMAppConfig`-objektet. Om appnyckeln är en sträng t.ex. ska du använda `stringValueForKey` eller `allStringsForKey`. Se `IntuneMAMAppConfig.h` för en detaljerad beskrivning av returvärden och felvillkor.

Mer information om funktionerna i Graph API finns i [Graph API-referens](https://developer.microsoft.com/graph/docs/concepts/overview).

Mer information om hur du skapar en MAM-riktad appkonfigurationsprincip i iOS finns i avsnittet om MAM-riktad appkonfiguration i [How to use Microsoft Intune app configuration policies for iOS](../apps/app-configuration-policies-use-ios.md) (använda Microsoft Intune-appkonfigurationsprinciper för iOS).

## <a name="telemetry"></a>Telemetri

Som standard samlar Intune App SDK för iOS in telemetri vid följande typer av händelser:

* **Appstart**: För att hjälpa Microsoft Intune att få veta mer om MAM-aktiverad appanvändning efter hanteringstyp (MAM med MDM, MAM utan MDM-registrering osv.).

* **Registreringsanrop**: För att hjälpa Microsoft Intune att förstå lyckade resultat och andra typer av resultatstatistik för registreringsanrop som initierats från klienten.

* **Intune-åtgärder**: För att hjälpa till att diagnostisera problem och se till att Intune-funktioner fungerar samlar vi in information om Intune SDK-åtgärder.

> [!NOTE]
> Om du väljer att inte skicka Intune App SDK-telemetridata till Microsoft Intune från din mobilapp måste du inaktivera Intune App SDK-telemetriinsamlingen. Ställ in egenskapen `MAMTelemetryDisabled` på Ja i IntuneMAMSettings-ordlistan.

## <a name="enable-multi-identity-optional"></a>Aktivera flera identiteter (valfritt)

Som standard tillämpar SDK en princip på appen som helhet. Multiidentitet är en MAM-funktion som du kan aktivera för att tillämpa en princip på nivån per identitet. Detta kräver mer appdeltagande än andra MAM-funktioner.

Appen måste meddela app-SDK när den har för avsikt att ändra den aktiva identiteten. SDK meddelar även appen när en identitetsändring krävs. För närvarande stöds endast en hanterad identitet. När användaren registrerar enheten eller appen använder SDK den här identiteten och ser den som primär hanterad identitet. Andra användare i appen behandlas som ej hanterade med obegränsade principinställningar.

Tänk på att en identitet helt enkelt definieras som en sträng. Identiteter är skiftlägeskänsliga. Begäranden till SDK om en identitet kanske inte returnerar samma gemener och versaler som användes när identiteten skapades.

### <a name="identity-overview"></a>Identitetsöversikt

En identitet är helt enkelt användarnamnet för ett konto (t.ex. user@contoso.com). Utvecklare kan ange identiteten för appen på följande nivåer:

* **Processidentitet**: Anger identiteten för hela processen och används främst för program med endast en identitet. Den här identiteten påverkar alla aktiviteter, filer och användargränssnittet.

* **Gränssnittsidentitet**: Avgör vilka principer som används för gränssnittsåtgärder på huvudtråden, t.ex. klipp ut/kopiera/klistra in, PIN-kod, autentisering och datadelning. Gränssnittsidentiteten påverkar inte filåtgärder som kryptering och säkerhetskopiering osv.

* **Trådidentitet**: Påverkar vilka principer som används på den aktuella tråden. Den här identiteten påverkar alla åtgärder, filer och användargränssnittet.

Det är appens ansvar att ange identiteterna korrekt, oavsett om användaren hanteras eller inte.

Alla trådar har alltid en effektiv identitet för gränssnittsåtgärder och filåtgärder. Detta är den identitet som används för att kontrollera vilka principer, om några, som ska användas. Om identiteten är "ingen identitet" eller om användaren inte hanteras tillämpas inga principer. Diagrammen nedan visar hur effektiva identiteter bestäms.

  ![Intune App SDK iOS: Process för identitetsbestämning](./media/app-sdk-ios/ios-thread-identities.png)

### <a name="thread-queues"></a>Trådköer

Appar skickar ofta asynkrona och synkrona uppgifter till trådköer. SDK hindrar Grand Central Dispatch-anrop (GCD) och kopplar den aktuella trådidentiteten till de skickade uppgifterna. När åtgärderna har utförts ändrar SDK tillfälligt trådidentiteten till den identitet som är kopplad till åtgärden, utför åtgärden, och återställer sedan den ursprungliga trådidentiteten.


Eftersom `NSOperationQueue` har byggts på GCD kommer `NSOperations` att köras på trådens identitet när åtgärderna läggs till i `NSOperationQueue`. `NSOperations` eller funktionerna som skickas direkt med GCD kan också ändra den befintliga trådidentiteten när de körs. Den här identiteten åsidosätter den identitet som ärvs från den avsändande tråden.

### <a name="file-owner"></a>Filägare

SDK spårar identiteterna av lokala filägare och tillämpar principer på lämpligt sätt. En filägare upprättas när en fil skapas eller när en fil öppnas i trunkeringsläge. Ägaren anges som den effektiva filåtgärdsidentiteten för tråden som utför åtgärden.

Appar kan också definiera filägaridentitet uttryckligen med hjälp av `IntuneMAMFilePolicyManager`. Appar kan använda `IntuneMAMFilePolicyManager` för att hämta filägaren och ange gränssnittsidentiteten innan filinnehållet visas.

### <a name="shared-data"></a>Delade data

Om appen skapar filer som har data från både hanterade och icke-hanterade användare är det appens ansvar att kryptera den hanterade användarens data. Du kan kryptera data med hjälp av `protect` och `unprotect`-API:erna i `IntuneMAMDataProtectionManager`.

`protect`-metoden godkänner en identitet som kan vara en hanterad eller icke-hanterad användare. Data krypteras om användaren är hanterad. Om användaren inte är hanterad läggs en rubrik till i data som kodar identiteten, men data krypteras inte. Du kan använda `protectionInfo`-metoden för att hämta dataägaren.

### <a name="share-extensions"></a>Resurstillägg

Om appen har ett resurstillägg kan ägaren av objektet som delas hämtas genom `protectionInfoForItemProvider`-metoden i `IntuneMAMDataProtectionManager`. Om det delade objektet är en fil anger SDK filägaren. Om det delade objektet är data är det appens ansvar att ange filägaren om dessa data har gjorts beständiga i en fil, och att anropa `setUIPolicyIdentity`-API:et innan dessa data visas i gränssnittet.

### <a name="turn-on-multi-identity"></a>Aktivera flera identiteter

Som standard betraktas alla appar som appar med endast en identitet. SDK anger processidentiteten till den registrerade användaren. Lägg till en boolesk inställning med namnet `MultiIdentity` och värdet JA i IntuneMAMSettings-ordlistan i appens Info.plist-fil om du vill aktivera stöd för flera identiteter.

> [!NOTE]
> När flera identiteter är aktiverade är processidentiteten, UI-identiteten och trådidentiteterna inställda på noll. Det är appens ansvar att ange dem på lämpligt sätt.

### <a name="switch-identities"></a>Växla identiteter

* **Appinitierad identitetsväxling**:

    Vid start anses att multiidentitetsappar körs under ett okänt ej hanterat konto. Gränssnittet för villkorlig start körs inte och inga principer verkställs på appen. Det är appens ansvar att meddela SDK om identiteten ändras. Detta sker vanligtvis när appen är på väg att visa data för ett visst användarkonto.

    Ett exempel är om användaren försöker öppna ett dokument, en postlåda eller en flik på en bärbar dator. Appen måste meddela SDK innan filen, postlådan eller fliken öppnas. Detta görs via `setUIPolicyIdentity` API i `IntuneMAMPolicyManager`. Denna API ska anropas oavsett om användaren är hanterad eller inte. Om användaren är hanterad utför SDK kontrollerna för villkorlig start, till exempel kontrollerna för upplåsningsidentifiering, PIN-kod och autentisering.

    Resultatet av identitetsväxlingen returneras till appen asynkront via en hanterare för slutförande. Appen skjuter upp öppning av dokumentet, postlådan eller fliken till en lyckad resultatkod returneras. Om identitetsväxlingen misslyckades avbryter appen åtgärden.

* **SDK-initierad identitetsväxling**:

    I vissa fall måste SDK be appen att växla till en viss identitet. Appar med flera identiteter måste implementera metoden `identitySwitchRequired` i `IntuneMAMPolicyDelegate` för att hantera denna begäran.

    När den här metoden anropas överförs `IntuneMAMAddIdentityResultSuccess` till hanteraren för slutförande om appen kan hantera begäran om att växla till angiven identitet. Om den inte kan hantera växling av identiteten bör appen överföra `IntuneMAMAddIdentityResultFailed` till hanteraren för slutförande.

    Appen behöver inte anropa `setUIPolicyIdentity` som svar på det här anropet. Om SDK kräver att appen växlar till ett ej hanterat användarkonto kommer den tomma strängen att överföras till `identitySwitchRequired`-anropet.

* **Selektiv rensning**:

    När appen rensas selektivt anropar SDK metoden `wipeDataForAccount` i `IntuneMAMPolicyDelegate`. Det är appens ansvar att ta bort det angivna användarkontot och eventuella data som är kopplade till det. SDK kan ta bort alla filer som ägs av användaren och gör det om programmet returnerar FALSKT från `wipeDataForAccount`-anropet.

    Observera att den här metoden anropas från en bakgrundstråd. Appen bör inte returnera något värde förrän alla data för användaren har tagits bort (med undantag för filer om appen returnerar FALSKT).

## <a name="ios-best-practices"></a>Metodtips för iOS

Här är några rekommenderade metodtips för att utveckla med iOS:

* iOS-filsystemet är skiftlägeskänsligt. Se till att versaler och gemener stämmer för filnamn som `libIntuneMAM.a` och `IntuneMAMResources.bundle`.

* Om Xcode har problem med att hitta `libIntuneMAM.a` så kan du åtgärda problemet genom att lägga till sökvägen till biblioteket i sökvägarna för länkare.

## <a name="faqs"></a>Vanliga frågor och svar

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>Är alla API:erna adresserbara via samverkan med intern Swift eller Objective-C och Swift?

Intune App SDK-API:er finns endast i Objective-C och har inte stöd för **intern** Swift. Snabb samverkan med Objective-C krävs.

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>Måste alla användare av mitt program registreras med APP-WE-tjänsten?

Nej. I själva verket är det bara arbets- eller skolkonton som ska registreras med Intune App SDK. Appar ansvarar för att fastställa om ett konto används i ett arbets- eller skolsammanhang.

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>Vad gäller för användare som redan har loggat in i programmet? Behöver de registreras?

Det är appens ansvar att registrera användare när de har autentiserats. Programmet ansvarar även för att registrera eventuella befintliga konton som kan ha funnits innan programmet hade MAM-funktioner utan MDM.

Programmet ska använda metoden `registeredAccounts:` för att göra detta. Den här metoden returnerar ett NSDictionary som har alla konton som är registrerade i Intune MAM-tjänsten. Om några befintliga konton i programmet inte finns i listan bör programmet registrera dessa konton via `registerAndEnrollAccount:`.

### <a name="how-often-does-the-sdk-retry-enrollments"></a>Hur ofta gör SDK nya registreringsförsök?

SDK försöker automatiskt igen om 24 timmar med alla registreringar som har misslyckats tidigare. SDK gör detta för att säkerställa att en användare registreras och tar emot principer även om användarens organisation aktiverar MAM efter att användaren loggar in i programmet.

SDK slutar att försöka när det upptäcker att en användare har lyckats registrera programmet. Det beror på att endast en användare kan registrera ett program vid en given tidpunkt. Om användaren har avregistrerats påbörjas nya försök med samma 24-timmarsintervall.

### <a name="why-does-the-user-need-to-be-deregistered"></a>Varför måste användaren avregistreras?

SDK vidtar regelbundet följande åtgärder i bakgrunden:

* Om programmet inte har registrerats ännu försöker det att registrera alla registrerade konton var 24:e timme.
* Om programmet har registrerats kontrollerar SDK om det finns MAM-principuppdateringar var 8:e timme.

Om en användare avregistreras meddelas SDK att användaren inte längre använder programmet och SDK kan då stänga av de ovanstående regelbundna händelserna för det användarkontot. Det utlöser även avregistrering av appen och selektiv rensning vid behov.

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>Bör jag ställa in flaggan doWipe på sant i avregistreringsmetoden?

Den här metoden ska anropas innan användaren loggas ut från programmet.  Om användarens data raderas från programmet som en del av utloggningen kan `doWipe` vara inställt på falskt. Men om programmet inte tar bort användarens data bör `doWipe` ställas in på sant så att SDK kan ta bort dessa data själv.

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>Finns det andra sätt att avregistrera ett program?

Ja, IT-administratören kan skicka ett kommando för selektiv rensning till programmet. Detta avregistrerar användaren och raderar användarens data. SDK hanterar det här scenariot automatiskt och skickar en avisering via ombudsmetoden för avregistrering.

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>Finns det en exempelapp som visar hur man integrerar SDK?

Ja! Vi har nyligen gjort om vår exempelapp med öppen källkod: [Wagr för iOS](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App). Wagr har nu aktiverats för appskyddsprincip med hjälp av Intune App SDK.

### <a name="how-can-i-troubleshoot-my-app"></a>Hur kan jag felsöka min app?

Intune SDK för iOS 9.0.3 + har stöd för möjligheten att lägga till en diagnostisk konsol i mobilappen för att testa principer och loggnings fel. `IntuneMAMDiagnosticConsole.h` definierar `IntuneMAMDiagnosticConsole` klass gränssnittet, som utvecklare kan använda för att Visa Intune-diagnostiken. På så sätt kan slutanvändare eller utvecklare under testningen samla in och dela Intune-loggar för att hjälpa till att diagnostisera eventuella problem som de kan ha. Detta API är valfritt för integrerare.

## <a name="submit-your-app-to-the-app-store"></a>Skicka in din app till App Store

Både det statiska biblioteket och ramverksversionerna av Intune App SDK är universella binärfiler. Detta innebär att de innehåller kod för alla enhets- och simuleringsarkitekturer. Apple avvisar appar som skickas till App Store om de innehåller simuleringskod. Vid kompilering mot det statiska biblioteket för enhetsspecifika versioner rensar länkaren automatiskt bort simulatorkoden. Följ stegen nedan för att se till att all simuleringskod tas bort innan du laddar upp din app till App Store.

1. Kontrollera att `IntuneMAM.framework` finns på skrivbordet.

2. Kör dessa kommandon:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```

    Det första kommandot rensar simuleringsarkitektur från ramverkets DYLIB-fil. Det andra kommandot kopierar DYLIB-filen som endast är för enheten tillbaka till ramverkskatalogen.
