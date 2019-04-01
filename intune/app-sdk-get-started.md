---
title: Kom igång med Microsoft Intune App SDK
description: Aktivera snabbt din mobilapp för mobil programhantering (MAM) med Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/24/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 23c254094281c7591730b2972ec0de41f5243e66
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566394"
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Kom igång med Microsoft Intune App SDK

Den här guiden hjälper dig att snabbt aktivera din mobilapp för att stödja appskyddsprinciper med Microsoft Intune. Det kan vara bra att först förstå fördelarna med Intune App SDK:n som räknas upp i [Intune App SDK-översikt](app-sdk.md).

Intune App SDK:n stöder liknande scenarier över iOS och Android och är avsedd att ge IT-administratörer en enhetlig upplevelse över båda plattformarna. På grund av plattformsskillnader och -begränsningar förekommer dock smärre skillnader vad gäller stöd av vissa funktioner.

## <a name="register-your-store-app-with-microsoft"></a>Registrera din Store-app med Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Om din app är en intern app för din organisation som inte ska publiceras offentlig:

Du _**behöver inte**_ registrera din app. För interna [line-of-business (LOB) appar](apps-add.md#app-types-in-microsoft-intune) som har skrivits av eller för ditt företags IT-administratören distribuerar appen internt. Intune identifierar att appen har skapats med SDK:n och tillåter att IT-administratören tillämpar appskyddsprinciper på den. Du kan hoppa till avsnittet [Aktivera din iOS- eller Android-app för appskyddsprinciper](#enable-your-iOS-or-Android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Om din app kommer att publiceras på en offentlig appbutik som Apple App Store eller Google Play:

_**Måste**_ du först registrera din app med Microsoft Intune och samtycka med villkoren för registrering. Därefter kan IT-administratörer tillämpa en appskyddsprincip på den hanterade appen, som kommer att anges som en [Intune-skyddad partnerapp](apps-supported-intune-apps.md#partner-apps).

Intune administratörer kommer inte att ha möjlighet att tillämpa appskyddsprincipen på din apps djuplänk förrän registreringen har slutförts och bekräftats av Microsoft Intune-teamet. Microsoft kommer även att lägga till din app till sin [Microsoft Intune-partnersida](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Där kommer appikonen att visas för att visa att den stöder Intunes appskyddsprinciper.

### <a name="the-registration-process"></a>Registreringsprocessen
För att börja registreringen, och om du inte redan arbetar med en Microsoft-kontakt, fyller du i [frågeformuläret för Microsoft Intune-appartner](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR80SNPjnVA1KsGiZ89UxSdVUMEpZNUFEUzdENENOVEdRMjM5UEpWWjJFVi4u).

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

Om din app är en Xamarin-app använder du den här SDK-varianten:

* [Xamarin-bindningar för Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)

Det är en bra idé att registrera dig för ett GitHub-konto som du kan använda för att förgrena och använda pull i våra lagringsplatser. GitHub låter utvecklare kommunicera med vårt produktteam, öppna frågor och få snabba svar, se versionsanmärkningar och ge feedback till Microsoft. Kontakta msintuneappsdk@microsoft.com för frågor om Intune App SDK på GitHub.

## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Aktivera din iOS- eller Android-app för appskyddsprinciper

Du behöver en av följande utvecklarguider för att hjälpa dig att integrera Intune App SDK till din app:

* **[Utvecklarguide för Intune App SDK för iOS](app-sdk-ios.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din interna iOS-app med Intune App SDK.

* **[Utvecklarhandbok för Intune App SDK för Android](app-sdk-android.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din interna Android-app med Intune App SDK.

* **[Guide för Xamarin-bindningar för Intune App SDK](app-sdk-xamarin.md)**: Det här dokumentet hjälper dig att skapa iOS- och Android-appar med Xamarin för Intunes appskyddsprinciper.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Aktivera din iOS- eller Android-app för app-baserad villkorlig åtkomst
 
 Förutom att aktivera din app för app-skyddsprincip krävs följande för att din app ska fungera korrekt med Azure ActiveDirectory (AAD) app-baserad villkorlig åtkomst:
 
 * Appen har byggts med [Autentiseringsbibliotek för Azure ActiveDirectory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) och aktiverats för AAD broker-autentisering.
 
 * [Klient-ID för AAD](https://docs.microsoft.com/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#configure-a-native-client-application) för din app måste vara unikt i iOS- och Android-plattformar.
 
## <a name="configure-telemetry-for-your-app"></a>Konfigurera telemetri för din app

Microsoft Intune samlar in data för användningsstatistik för din app.

* **Intune App SDK för iOS**: SDK loggar SDK-telemetridata om användningshändelser som standard. Dessa data skickas till Microsoft Intune.

    * Om du väljer att inte skicka SDK-telemetridata till Microsoft Intune från din app måste du inaktivera telemetriöverföring genom att tilldela egenskapen `MAMTelemetryDisabled` värdet ”YES” i IntuneMAMSettings-ordlistan.

* **Intune App SDK för Android**: Intune App SDK för Android styr inte insamling av data från din app. Företagsportalprogrammet loggar telemetridata som standard. Dessa data skickas till Microsoft Intune. Enligt Microsofts policy samlar vi inte in någon personligt identifierbar information (PII). 

    * Om användare väljer att inte skicka dessa data så måste de inaktivera telemetri under inställningarna i företagsportalappen. Du kan läsa mer i [Inaktivera Microsofts insamling av användningsdata](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="line-of-business-app-version-numbers"></a>Versionsnummer för verksamhetsspecifika appar

Verksamhetsspecifika appar i Intune visar nu versionsnummer för iOS och Android-appar. Numret visas på Azure Portal i listan över appar och på bladet med översikt över appar. Slutanvändarna kan se appnumret i företagsportalappen och i webbportalen.

### <a name="full-version-number"></a>Fullständigt versionsnummer

Det fullständiga versionsnumret identifierar en specifik version av appen. Numret visas som _Version_(_Build_). Exempelvis, 2.2(2.2.17560800). 

Det fullständiga versionsnumret har två komponenter:

 - **Version**  
   Versionsnumret är det läsbara versionsnumret för appen. Det här numret används av slutanvändare för att identifiera olika versioner av appen.

 - **Build-nummer**  
    Build-numret är ett internt nummer som kan användas i appidentifiering och för att programmässigt hantera appen. Build-nummer refererar till en iteration av appen som refererar till ändringar i koden.

### <a name="version-and-build-number-in-android-and-ios"></a>Version- och build-nummer i Android och iOS

Både Android och iOS använder version- och build-nummer för appar. Men båda operativsystemen har betydelser som är OS-specifika. Följande tabell förklarar hur de här termerna är relaterade.

Kom ihåg att använda både version- och build-nummer när du utvecklar ett verksamhetsspecifikt program för användning i Intune. Apphantering i Intune har funktioner som förlitar sig på en meningsfull **CFBundleVersion** (för iOS) och **PackageVersionCode** (för Android). De här numren ingår i appmanifestet. 

Intune|iOS|Android|Beskrivning|
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

* **Microsoft Intune-testkonto**: Du behöver ett Microsoft Intune-konto för att kunna testa dina Intune-hanterade appar mot Intunes appskyddsfunktioner.

    * Om du är en ISV som aktiverar dina iOS eller Android store-appar för Intunes appskyddsprincip så får du en kampanjkod när du har slutfört registreringen med Microsoft Intune, enligt beskrivningen i registreringssteget. Kampanjkoden låter dig registrera dig för en utvärderingsversion av Microsoft Intune med ett års utökad användning.

    * Om du utvecklar en affärsspecifik app som inte ska publiceras i butiken, förväntas du ha åtkomst till Microsoft Intune genom din organisation. Du kan också registrera dig för en månads kostnadsfri utvärdering av [Microsoft Intune](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).
    
    * Om du testar din app på en mobil enhet med hjälp av ett slutanvändarkonto ska du ha gett det kontot en Intune-licens på Microsoft 365-administrationscentrets webbplats efter att ha loggat in med ett administratörskonto. Se [Tilldela Microsoft Intune-licens](https://docs.microsoft.com/en-ca/intune/licenses-assign).

* **Intunes appskyddsprinciper**: För att testa din app mot alla Intunes appskyddsprinciper bör du veta vad det förväntade beteendet för varje principinställning är. Se beskrivningarna för [iOS-appskyddsprinciper](app-protection-policy-settings-ios.md) och [Android-appskyddsprinciper](app-protection-policy-settings-android.md).

* **Felsökning**: Om du stöter på problem när du testar manuellt hur användarna installerar din app, kan du gå till [Felsöka appinstallationsproblem](troubleshoot-app-install.md). 

### <a name="give-your-app-access-to-the-intune-app-protection-service-optional"></a>Ge din app åtkomst till Intune-appskyddstjänsten (valfritt)

Om din app använder sina egna anpassade AAD-inställningar för autentisering, bör du vidta följande steg för såväl gemensamma arkivappar som interna verksamhetsspecifika appar. Du behöver inte genomföra stegen **om appen använder standardklient-ID:t för Intune SDK**. 

När du har registrerat din app i en Azure-klientorganisation, och den visas tenant under **Alla program** måste du ge appen åtkomst till Intune-appskyddstjänsten (tidigare känd som MAM-tjänsten). På Azure-portalen:

1.  Gå till bladet **Azure Active Directory**.
2.  Välj konfigurationen **Appregistrering** för programmet.
3.  I **Inställningar** och under rubriken **API-åtkomst** väljer du **Required permission** (Nödvändig behörighet). 
4.  Klicka på **+ Lägg till**.
5.  Klicka på **Välj ett API**. 
6.  I sökrutan anger du **Microsoft Mobile Application Management** (Microsofts hantering av mobilprogram).
7.  Välj **Microsoft Mobile Application Management** (Microsofts hantering av mobila program) i listan över API:er och klicka på Välj.
8.  Välj **Read and Write the User’s App Management Data** (Läs och skriv användarens apphanteringsdata).
9.  Klicka på **Klar**.
10. Klicka på **Bevilja** och klicka sedan på **Ja**. 

### <a name="badge-your-app-optional"></a>Ge din app en skylt (valfritt)

När du har validerat att Intunes appskyddsprinciper fungerar i din app kan du märka din appikon med en skylt i form av Intunes appskyddslogotyp.

Den här skylten talar om att din app fungerar med principer för Intune app för IT-administratörer, slutanvändare och potentiella Intune-kunder. Den uppmuntrar Intune-kunder att använda och införa din app.

Skylten är en ikon föreställande en portfölj och syns i exemplen nedan:

![Intune-appskyddsprinciper – Aktivitetsikon exempel 1](./media/badge-example-1.png) ![Intune-appskyddsprinciper – Aktivitetsikon exempel 2](./media/badge-example-2.png)

**Det här behöver du göra för att ge din app en skylt**:

* Ett bildhanteringsprogram som kan läsa **.eps**-filer eller ett Adobe-program som kan läsa **.ai**-filer.

* Du hittar [tillgångarna och riktlinjerna för Intunes appskyltar](https://github.com/msintuneappsdk/intune-app-partner-badge) på Microsoft Intune GitHub.
