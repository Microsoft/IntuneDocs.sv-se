---
title: Microsoft Intune App SDK Xamarin-bindningar
description: Med Intune App SDK Xamarin-bindningar kan du använda Intunes appskyddsprincip i iOS- och Android-appar som skapats med Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: d8e9dd1e38fdc693bd30372f2961244e4e809771
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180348"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin-bindningar

> [!NOTE]
> Börja gärna med att läsa artikeln [Komma igång med Intune App SDK](app-sdk-get-started.md). Den här guiden beskriver hur du förbereder dig för integreringen på de plattformar som stöds.

## <a name="overview"></a>Översikt
Med [Intune App SDK Xamarin-bindningar](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) kan du använda [Intunes appskyddsprincip](app-protection-policy.md) i iOS- och Android-appar som skapats med Xamarin. Bindningarna hjälper utvecklare att enkelt bygga in appskyddsfunktioner för Intune i Xamarin-baserade appar.

Med Microsoft Intune App SDK Xamarin-bindningar kan du inkludera Intunes appskyddsprinciper (även kallade APP- eller MAM-principer) i dina appar som utvecklats med Xamarin. Ett MAM-aktiverat program är ett program som är integrerat med Intune App SDK. Det kan användas av IT-administratörer för att distribuera appskyddsprinciper till din mobilapp om Intune aktivt hanterar appen.

## <a name="whats-supported"></a>Vad stöds?

### <a name="developer-machines"></a>Datorer för utvecklare
* Windows (Visual Studio version 15.7+)
* macOS

### <a name="mobile-app-platforms"></a>Plattformar för mobilappar
* Android
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Scenarion för Intune Mobile Application Management

* Intune APP-WE (utan enhetsregistrering)
* Intune MDM-registrerade enheter
* EMM-registrerade enheter från tredje part

Xamarin-appar som skapats med Intune App SDK Xamarin-bindningar kan nu ta emot Intunes appskyddsprinciper på både MDM-registrerade Intune-enheter och oregistrerade enheter.

## <a name="prerequisites"></a>Krav

Granska [licensvillkoren](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Skriv ut och behåll en kopia av licensvillkoren för framtida referens. Genom att ladda ned och använda Intune App SDK Xamarin-bindningar godkänner du licensvillkoren. Om du inte accepterar villkoren har du inte rätt att använda programvaran.

SDK använder [Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) för [autentisering](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) och villkorsstyrda startscenarier som kräver att apparna har konfigurerats med [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Aktivera Intune-appskyddsprinciper i din iOS-mobilapp
1. Lägg till [Microsoft.Intune.MAM.Xamarin.iOS NuGet-paketet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) i ditt Xamarin.iOS-projekt.
2.  Följ de allmänna steg som krävs för att integrera Intune App SDK i en mobila iOS-app. Du kan börja med steg 3 av integrationsinstruktionerna från [Utvecklingsguide för Intune App SDK för iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Du kan hoppa över det sista steget i avsnittet om att köra IntuneMAMConfigurator, eftersom detta verktyg ingår i paketet Microsoft.Intune.MAM.Xamarin.iOS och körs automatiskt under byggtiden.
    **Viktigt**: Aktivering av nyckelringsdelning för en app skiljer sig något åt mellan Visual Studio och Xcode. Öppna appens .plist för rättigheter och kontrollera att alternativet ”Aktivera nyckelringar” är aktiverat och att lämpliga delningsgrupper för nyckelringar har lagts till i avsnittet. Kontrollera sedan att .plist för rättigheter har angetts i fältet ”anpassade rättigheter” i projektets alternativ ”iOS-paketsignering” för alla lämpliga kombinationer av konfiguration/plattform.
3.  När bindningarna har lagts till och appen är korrekt konfigurerad, kan din app börja använda Intune SDK:s API:er. Om du vill göra detta, måste du inkludera följande namnrymd:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. För att kunna ta emot skyddsprinciper, måste appen registreras i Intune MAM-tjänsten. Om din app inte använder [Azure Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) eller [Microsoft Authentication Library](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) för att autentisera användare, och du vill att Intune SDK ska hantera autentisering, bör din app tillhandahålla användarens UPN för IntuneMAMEnrollmentManagers LoginAndEnrollAccount-metod:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      Appar kan skicka null om användarens UPN är okänt vid tidpunkten för anropet. I det här fallet uppmanas användare att ange sin e-postadress och sitt lösenord.
      
      Om appen redan använder ADAL eller MSAL för att autentisera användare kan du konfigurera en upplevelse med enkel inloggning (SSO) mellan din app och Intune SDK. Du måste först konfigurera ADAL/MSAL att lagra token i samma åtkomstgrupp för nyckelringar som används av Intune Xamarin-bindningar för iOS (com.microsoft.adalcache). För ADAL kan du göra detta genom att [konfigurera egenskapen KeychainSecurityGroup för AuthenticationContext](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Token-cache-serialization#enable-token-cache-sharing-across-ios-applications). För MSAL måste du [ange egenskapen KeychainSecurityGroup för PublicClientApplication](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/msal-net-2-released#you-can-now-enable-sso-between-adal-and-msal-apps-on-xamarinios). Därefter behöver du åsidosätta de AAD-standardinställningar som används av Intune SDK med inställningarna för din app. Du kan göra detta via i ordlistan IntuneMAMSettings i appens Info.plist, såsom anges i [Intune App SDK för iOS Developer Guide](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), eller så kan du använda AAD-åsidosättningsegenskaper för IntuneMAMPolicyManager-instansen. Metoden Info.plist rekommenderas för program vars ADAL-inställningar är statiska medan egenskaper för åsidosättning rekommenderas för program som fastställer dessa värden vid körning. När alla inställningar för enkel inloggning har konfigurerats bör din app tillhandahålla användarens UPN för IntuneMAMEnrollmentManagers RegisterAndEnrollAccount-metod när den har autentiserats:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      Appar kan fastställa resultatet av ett registreringsförsök genom att implementera metoden EnrollmentRequestWithStatus i en underklass av IntuneMAMEnrollmentDelegate och ange IntuneMAMEnrollmentManagers Delegate-egenskap till en instans av den klassen. Ett exempel finns i vårt [Xamarin.iOS-exempelprogram](https://github.com/msintuneappsdk/sample-intune-xamarin-ios).

      Vid en lyckad registrering kan appar fastställa UPN för det registrerade kontot (om det tidigare var okänt) genom att köra frågor mot följande egenskap: 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> Det finns ingen ommappning för iOS. Integrering i en Xamarin.Forms-app bör vara samma som för ett vanligt Xamarin.iOS-projekt. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Aktivera skyddsprinciper för Intune-appar i din Android-mobilapp

För Xamarin-baserade Android-appar som inte använder ett UI-ramverk läser och följer du [utvecklarguiden för Intune App SDK för Android](app-sdk-android.md). För din Xamarin-baserade Android-app måste du ersätta klassen, metoder och aktiviteter med deras MAM-motsvarigheter baserat på [tabellen för klass- och metodersättningar](app-sdk-android.md#class-and-method-replacements) som ingår i handboken. Om din app inte definierar en `android.app.Application`-klass måste du skapa en och se till att du ärver från `MAMApplication`. ADAL-konfigurationsvärdena förmedlas till SDK via AndroidManifest-metadata. Läs vår dokumentation om att [Konfigurera ADAL för din app](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).

### <a name="xamarinandroid-integration"></a>Xamarin.Android integration

1. Lägg till den senaste versionen av [Microsoft.Intune.MAM.Xamarin.Android NuGet-paketet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) i ditt Xamarin.Android-projekt. Då har du de nödvändiga referenserna för att aktivera Intune för appen.

2. Läs och följ [Utvecklarhandbok för Intune App SDK för Android](app-sdk-android.md) fullständigt, och var särskilt uppmärksam på följande:

    1. [Hela avsnittet om klass- och metodersättningar](app-sdk-android.md#class-and-method-replacements). 
    2. [Avsnittet MAMApplication](app-sdk-android.md#mamapplication). Se till att din underklass är korrekt dekorerad med attributet `[Application]` och åsidosätter konstruktorn `(IntPtr, JniHandleOwnership)`.
    3. [Avsnittet om ADAL-integrering](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) om din app utför autentisering mot AAD. 
    4. [Avsnittet om MAM-WE-registrering](app-sdk-android.md#app-protection-policy-without-device-enrollment) om du planerar att hämta principen från MAM-tjänsten i din app.

> [!NOTE]
> När du försöker hitta motsvarande API:er i [Utvecklarhandbok för Intune App SDK för Android](app-sdk-android.md) i `Microsoft.Intune.MAM.Xamarin.Android`-bindningar eller konvertera kodavsnitt från handboken, bör du tänka på att Xamarin-bindningarnas generator ändrar Android-API:er på följande sätt:
> * Alla identifierare konverteras till Pascal-versaler (com.foo.bar -> Com.Foo.Bar)
> * Alla get/set-åtgärder konverteras till egenskapsåtgärder (t.ex. Foo.getBar() -> Foo.Bar, Foo.setBar("zap") -> Foo.Bar = "zap")
> * Alla gränssnitt har tecknet "I" före namnet (FooInterface -> IFooInterface)

### <a name="xamarinforms-integration"></a>Xamarin.Forms integration

**Förutom att utföra alla steg ovan**, tillhandahåller vi `Microsoft.Intune.MAM.Remapper`-paketet för `Xamarin.Forms`-program. Det här paketet genomför klassersättning åt dig genom att införa `MAM`-klasser i klasshierarkin av vanliga `Xamarin.Forms`-klasser som `FormsAppCompatActivity` och `FormsApplicationActivity` så att du kan fortsätta att använda dessa klasser genom att tillhandahålla åsidosättningar för motsvarande MAM-funktioner som `OnMAMCreate` och `OnMAMResume`. Om du vill använda det gör du följande:

1.  Lägg till NuGet-paketet [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) i projektet. Då läggs Intune APP SDK Xamarin-bindningarna till automatisk om du inte redan har inkluderat dem.

2.  Lägg till ett anrop till `Xamarin.Forms.Forms.Init(Context, Bundle)` i funktionen `OnMAMCreate` för `MAMApplication`-klassen som du skapade i steg 2.2 ovan. Det behövs eftersom programmet kan startas i bakgrunden med Intune-hantering.

> [!NOTE]
> Eftersom den här åtgärden skriver om ett beroende som Visual Studio använder för Intellisense (automatisk komplettering), kan du behöva starta om Visual Studio efter första ommappningen så att Intellisense korrekt identifierar ändringarna. 

Du har slutfört stegen för att bygga in komponenten i din app. Nu kan du följa stegen i Xamarin Android-exempelappen. Vi tillhandahåller två exempel, ett för Xamarin.Forms och ett för Android.

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>Kräva Intune-appskyddsprinciper för att använda en Xamarin-baserad verksamhetsspecifik Android-app (valfritt) 

Följande steg beskriver hur du säkerställer att Xamarin-baserade verksamhetsspecifika Android-appar endast kan användas av Intune-skyddade användare på deras enheter. 

### <a name="general-requirements"></a>Allmänna krav
* Se till att stegen som ger din Xamarin appbehörigheter till APP-tjänsten följs. Följ instruktionerna i guiden [Komma igång med Intune-SDK:n](app-sdk-get-started.md#next-steps-after-integration) under ”Ge din app åtkomst till Intune-appskyddstjänsten (valfritt)”. 
    
### <a name="working-with-the-intune-sdk"></a>Arbeta med Intune SDK
De här anvisningarna är specifika för alla Android- och Xamarin-appar som vill kräva Intune-appskyddsprinciper som ska användas på en slutanvändarenhet.

1. Konfigurera ADAL med hjälp av stegen som beskrivs i [handboken för Intune SDK för Android](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).
> [!NOTE] 
> Termen ”klient-id” är samma som termen ”program-id” från Azure-portalen som är kopplad till din app. 
* Du behöver "Vanlig ADAL-konfiguration" nummer 2 för att aktivera SSO.

2. Aktivera standardregistrering genom att ange följande värde i manifestet: ```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
> [!NOTE] 
> Det får inte finnas några fler MAM-WE-integreringar i appen. Det kan uppstå konflikter om det finns några andra försök att anropa MAMEnrollmentManager API:er.

3. Aktivera MAM-principen som krävs genom att ange följande värde i manifestet: ```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
> [!NOTE] 
> Det gör att apparna måste ladda ned företagsportalen till enheten och slutföra flödet för standardregistrering före användning.

### <a name="working-with-adal"></a>Arbeta med ADAL
Dessa instruktioner är ett krav för .NET/Xamarin-appar som kräver Intune-appskyddsprinciper för användning på en slutanvändarenhet.

1. Följ alla steg i ADAL-dokumentationen under [Brokered Authentication for Android](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/tree/dev/adal#brokered-authentication-for-android) (Koordinerad autentisering för Android).
> [!NOTE] 
> Nästa version av .NET ADAL (3.17.4) förväntas innehålla den korrigering som krävs för att detta ska fungera.

## <a name="support"></a>Stöd
Om organisationen är en befintlig Intune-kund kan du kontakta din representant från Microsofts support för att öppna en supportbegäran och skapa ett ärende [på sidan med GitHub-ärenden](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) så hjälper vi dig så snart vi kan. 
