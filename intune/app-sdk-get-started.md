---
title: "Kom igång med Microsoft Intune App SDK"
description: "Aktivera snabbt din mobilapp för mobil programhantering (MAM) med Microsoft Intune."
keywords: 
author: erikre
manager: angrobe
ms.author: erikre
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bd7d48a6511b1ae8ecf5a6f413ae2f682434244c
ms.sourcegitcommit: e76dbd0882526a86b6933ace2504f442e04de387
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/13/2018
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Kom igång med Microsoft Intune App SDK

Den här guiden hjälper dig att snabbt aktivera din mobilapp för appskyddsprinciper med Microsoft Intune. Det kan vara bra att först förstå fördelarna med Intune App SDK:n som räknas upp i [Intune App SDK-översikt](app-sdk.md).

Intune App SDK:n stöder liknande scenarier över iOS och Android och är avsedd att ge IT-administratörer en enhetlig upplevelse över båda plattformarna. På grund av plattformsbegränsningar förekommer dock smärre skillnader vad gäller stöd av vissa funktioner.

## <a name="register-your-store-app-with-microsoft"></a>Registrera din Store-app med Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Om din app är en intern app för din organisation som inte ska publiceras offentlig:

Du *behöver inte* att registrera din app. För interna affärsappar distribuerar IT-administratören appen internt. Intune identifierar att appen har skapats med SDK:n och tillåter att IT-administratören tillämpar appskyddsprinciper på den. Du kan hoppa till avsnittet [Aktivera din iOS- eller Android-app för appskyddsprinciper](#enable-your-iOS-or-Android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Om din app kommer att publiceras på en offentlig appbutik som Apple App Store eller Google Play:

_**Måste**_ du först registrera din app med Microsoft Intune och samtycka med villkoren för registrering. Därefter kan IT-administratörer tillämpa appskyddsprinciper för den upplysta appen, som listas som en Intune-appartner.

Intune administratörer kommer inte att ha möjlighet att tillämpa appskyddsprincipen på din apps djuplänk förrän registreringen har slutförts och bekräftats av Microsoft Intune-teamet. Microsoft kommer även att lägga till din app till sin [Microsoft Intune-partnersida](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Där kommer appikonen att visas för att visa att den stöder Intunes appskyddsprinciper.

Fyll i [Microsoft Intune-appartner frågeformuläret](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u) för att påbörja registreringsprocessen.

Vi använder e-postadresserna som står i frågeformulärets svar för att kontakta dig och fortsätta registreringsprocessen. Vi använder även din e-postadress från registreringen för att kontakta dig om vi har frågor.

> [!NOTE]
> All information som samlas in i formuläret ovan och via e-postkommunikation med Microsoft Intune-teamet följer [Microsofts sekretesspolicy](https://www.microsoft.com/privacystatement/default.aspx).

**Hur ser registreringsprocessen ut?**:

1. När du har skickat frågeformuläret kontaktar Microsoft dig på den e-postadress som du uppgav vid registreringen, antingen för att bekräfta att registreringen mottagits eller för att be om ytterligare information som krävs för att slutföra registreringen.

2. När vi har fått all nödvändig information från dig skickar vi avtalet för Microsoft Intune-appartner till dig för underskrift. Det här avtalet beskriver villkoren som ditt företag måste godkänna för att bli en Microsoft Intune-appartner.

3. Du meddelas när din app har registrerats med Microsoft Intune-tjänsten och när appen publiceras på webbplatsen för [Microsoft Intune-partner](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

4. Slutligen läggs djuplänken för din app till i nästa månatliga Intune Service-uppdatering. Om registreringsinformationen exempelvis slutfördes i juli, stöds appens djuplänk i mitten av augusti.

Om din apps djuplänk ändras i framtiden, måste du omregistrera din app.

> [!NOTE]
> Vänligen meddela oss om du uppdaterar appen med en ny version av Intune App SDK.



## <a name="download-the-sdk-files"></a>Hämta SDK-filerna

Intune App SDK:er för interna iOS- och Android-appar finns på ett Microsoft GitHub-konto. De här offentliga lagringsplatserna innehåller SDK-filer för intern iOS och Android:

* [Intune App SDK för iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Intune App SDK för Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Om din app är en Xamarin- eller Cordova-app använder du de här SDK-varianterna:

* [Intune App SDK Xamarin-komponenten](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Intune App SDK Cordova-insticksprogrammet](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Det är en bra idé att registrera dig för ett GitHub-konto som du kan använda för att förgrena och använda pull i våra lagringsplatser. GitHub låter utvecklare kommunicera med vårt produktteam, öppna frågor och få snabba svar, se versionsanmärkningar och ge feedback till Microsoft. Kontakta msintuneappsdk@microsoft.com för frågor om Intune App SDK på GitHub.





## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Aktivera din iOS- eller Android-app för appskyddsprinciper

Du behöver en av följande utvecklarguider för att hjälpa dig att integrera Intune App SDK till din app:

* **[Utvecklarguide för Intune App SDK för iOS](app-sdk-ios.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din interna iOS-app med Intune App SDK.

* **[Utvecklarhandbok för Intune App SDK för Android](app-sdk-android.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din interna Android-app med Intune App SDK.

* **[Guide för plugin-programmet Intune App SDK Cordova](app-sdk-cordova.md)**: Det här dokumentet hjälper dig att skapa iOS- och Android-appar med Cordova för Intunes appskyddsprinciper.

* **[Guide för Intune App SDK Xamarin-komponenten](app-sdk-xamarin.md)**: Det här dokumentet hjälper dig att skapa iOS- och Android-appar med Cordova för Intunes appskyddsprinciper.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Aktivera din iOS- eller Android-app för app-baserad villkorlig åtkomst
 
 Förutom att aktivera din app för app-skyddsprincip krävs följande för att din app ska fungera korrekt med Azure ActiveDirectory (AAD) app-baserad villkorlig åtkomst:
 
 * Appen har byggts med [Autentiseringsbibliotek för Azure ActiveDirectory](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-libraries) och aktiverats för AAD broker-autentisering.
 
 * [Klient-ID för AAD](https://docs.microsoft.com/en-us/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application) för din app måste vara unikt i iOS- och Android-plattformar.
 
 
 

## <a name="configure-telemetry-for-your-app"></a>Konfigurera telemetri för din app

Microsoft Intune samlar in data för användningsstatistik för din app.

* **Intune App SDK för iOS**: SDK loggar SDK-telemetridata om användningshändelser som standard. Dessa data skickas till Microsoft Intune.

    * Om du väljer att inte skicka SDK-telemetridata till Microsoft Intune från din app måste du inaktivera telemetriöverföring genom att tilldela egenskapen `MAMTelemetryDisabled` värdet ”YES” i IntuneMAMSettings-ordlistan.

* **Intune App SDK för Android**: Telemetridata loggas inte via SDK.

 Versionsnummer för verksamhetsspecifika iOS och Android-program är synliga <!-- 1380712 -->

## <a name="line-of-business-app-version-numbers"></a>Versionsnummer för verksamhetsspecifika appar

Verksamhetsspecifika appar i Intune visar nu versionsnummer för iOS och Android-appar. Numret visas på Azure Portal i listan över appar och på bladet med översikt över appar. Slutanvändarna kan se appnumret i företagsportalappen och i webbportalen.

### <a name="full-version-number"></a>Fullständigt versionsnummer

Det fullständiga versionsnumret identifierar en specifik version av appen. Numret visas som _Version_(_Build_). Exempelvis, 2.2(2.2.17560800)

Det fullständiga versionsnumret har två komponenter:

 - **Version**  
   Versionsnumret är det läsbara versionsnumret för appen. Det här numret används av slutanvändare för att identifiera olika versioner av appen.

 - **Build-nummer**  
    Build-numret är ett internt nummer som kan användas i appidentifiering och för att programmässigt hantera appen. Build-nummer refererar till en iteration av appen som refererar till ändringar i koden.

### <a name="version-and-build-number-in-android-and-ios"></a>Version- och build-nummer i Android och iOS

Både Android och iOS använder version- och build-nummer för appar. Men båda operativsystemen har betydelser som är OS-specifika. Följande tabell förklarar hur de här termerna är relaterade.

Kom ihåg att använda både version- och build-nummer när du utvecklar ett verksamhetsspecifikt program för användning i Intune. Apphantering i Intune har funktioner som förlitar sig på en meningsfull **CFBundleVersion** (för iOS) och **PackageVersionCode** (för Android). De här numren ingår i appmanifestet. 

Intune|iOS|Android|Description|
|---|---|---|---|
Versionsnummer|CFBundleShortVersionString|PackageVersionName |Det här numret anger en specifik version av appen för slutanvändare.|
Versionsnummer|CFBundleVersion|PackageVersionCode |Numret används för att indikera en iteration i appkoden.|

#### <a name="ios"></a>iOS

- **CFBundleShortVersionString**  
    Anger versionsnumret vid lansering för paketet. Numret identifierar en lanserad version av appen. Numret används av slutanvändare för att referera till appen.
 - **CFBundleVersion**  
    Build-versionen av paketet som identifierar en iteration av paketet. Numret kan identifiera en lanserad version eller ett outgivet paket. Numret används för appidentifiering.

#### <a name="android"></a>Android

 - **PackageVersionName**  
    Versionsnumret som visas för användare. Det här attributet kan anges som en rå sträng eller som en referens till en strängresurs. Strängen har inget annat syfte än att visas för användarna.
 - **PackageVersionCode**  
    Ett internt versionsnummer. Numret används endast för att avgöra om en version är nyare än en annan. Högre nummer indikerar senare versioner. Det här är inte versionen 

## <a name="next-steps-after-integration"></a>Nästa steg efter integrering

### <a name="test-your-app"></a>Testa appen
När du har slutfört de nödvändiga stegen för att integrera din iOS- eller Android-app med Intune App SDK så måste du se till att alla appskyddsprinciper är aktiverade och fungerar för användaren och IT-administratören. Du behöver följande för att testa din integrerade app:

* **Microsoft Intune-testkonto**: Du behöver ett Microsoft Intune-konto för att kunna testa dina Intune-upplysta appar mot Intunes appskyddsfunktioner.

    * Om du är en ISV som aktiverar dina iOS eller Android store-appar för Intunes appskyddsprincip så får du en kampanjkod när du har slutfört registreringen med Microsoft Intune, enligt beskrivningen i registreringssteget. Kampanjkoden låter dig registrera dig för en utvärderingsversion av Microsoft Intune med ett års utökad användning.

    * Om du utvecklar en affärsspecifik app som inte ska publiceras i butiken, förväntas du ha åtkomst till Microsoft Intune genom din organisation. Du kan också registrera dig för en månads kostnadsfri utvärdering av [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).

* **Intunes appskyddsprinciper**: För att testa din app mot alla Intunes appskyddsprinciper bör du veta vad det förväntade beteendet för varje principinställning är. Se beskrivningarna för [iOS-appskyddsprinciper](/intune-classic/deploy-use/ios-mam-policy-settings) och [Android-appskyddsprinciper](/intune-classic/deploy-use/android-mam-policy-settings).

* **Felsök**: Om du stöter på problem vid manuell testning av hur användare interagerar med din app kan du även läsa informationen om att [felsöka MAM](/intune-classic/troubleshoot/troubleshoot-mam). Den här artikeln hjälper dig med vanliga problem, dialogrutor och felmeddelanden som kan uppstå i Intune-upplysta appar. 

### <a name="badge-your-app-optional"></a>Ge din app en skylt (valfritt)

När du har validerat att Intunes appskyddsprinciper fungerar i din app kan du märka din appikon med en skylt i form av Intunes appskyddslogotyp.

Den här skylten talar om att din app fungerar med principer för Intune app för IT-administratörer, slutanvändare och potentiella Intune-kunder. Den uppmuntrar Intune-kunder att använda och införa din app.

Skylten är en ikon föreställande en portfölj och syns i exemplen nedan:

![Skyltexempel 1](./media/badge-example-1.png) ![Skyltexempel 2](./media/badge-example-2.png)

**Det här behöver du göra för att ge din app en skylt**:

* Ett bildhanteringsprogram som kan läsa **.eps**-filer eller ett Adobe-program som kan läsa **.ai**-filer.

* Du hittar [tillgångarna och riktlinjerna för Intunes appskyltar](https://github.com/msintuneappsdk/intune-app-partner-badge) på Microsoft Intune GitHub.
