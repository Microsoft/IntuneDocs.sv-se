---
title: Microsoft Intune App SDK Xamarin-bindningar
description: Med Intune App SDK Xamarin-bindningar kan du använda Intunes appskyddsprincip i iOS- och Android-appar som skapats med Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7525971f9ab48b92c3274f56cb1046a6fde948a5
ms.sourcegitcommit: 2614d1b08b8a78cd792aebd2ca9848f391df8550
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67794358"
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

Om programmet redan har konfigurerats för att använda ADAL eller MSAL, och har ett eget anpassat klient-ID som används för att autentisera med Azure Active Directory, ser du till att stegen för att ge Xamarin-appen behörigheter till Intune MAM-tjänsten (hantering av mobilprogram) följs. Följ instruktionerna i avsnittet [Ge din app åtkomst till Intune-appskyddstjänsten](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional) i [guiden Komma igång med Intune-SDK:n](app-sdk-get-started.md).

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Aktivera Intune-appskyddsprinciper i din iOS-mobilapp
1. Lägg till [Microsoft.Intune.MAM.Xamarin.iOS NuGet-paketet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) i ditt Xamarin.iOS-projekt.
2. Följ de allmänna steg som krävs för att integrera Intune App SDK i en mobila iOS-app. Du kan börja med steg 3 av integrationsinstruktionerna från [Utvecklingsguide för Intune App SDK för iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Du kan hoppa över det sista steget i avsnittet om att köra IntuneMAMConfigurator, eftersom detta verktyg ingår i paketet Microsoft.Intune.MAM.Xamarin.iOS och körs automatiskt under byggtiden.
    **Viktigt**: Aktivering av nyckelringsdelning för en app skiljer sig något åt mellan Visual Studio och Xcode. Öppna appens .plist för rättigheter och kontrollera att alternativet ”Aktivera nyckelringar” är aktiverat och att lämpliga delningsgrupper för nyckelringar har lagts till i avsnittet. Kontrollera sedan att .plist för rättigheter har angetts i fältet ”anpassade rättigheter” i projektets alternativ ”iOS-paketsignering” för alla lämpliga kombinationer av konfiguration/plattform.
3. När bindningarna har lagts till och appen är korrekt konfigurerad, kan din app börja använda Intune SDK:s API:er. Om du vill göra detta, måste du inkludera följande namnrymd:

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. För att kunna ta emot skyddsprinciper, måste appen registreras i Intune MAM-tjänsten. Om din app inte använder [Azure Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) eller [Microsoft Authentication Library](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) för att autentisera användare, och du vill att Intune SDK ska hantera autentisering, bör din app tillhandahålla användarens UPN för IntuneMAMEnrollmentManagers LoginAndEnrollAccount-metod:

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      Appar kan skicka null om användarens UPN är okänt vid tidpunkten för anropet. I det här fallet uppmanas användare att ange sin e-postadress och sitt lösenord.
      
      Om appen redan använder ADAL eller MSAL för att autentisera användare kan du konfigurera en upplevelse med enkel inloggning (SSO) mellan din app och Intune SDK. Du måste först konfigurera ADAL/MSAL att lagra token i samma åtkomstgrupp för nyckelringar som används av Intune Xamarin-bindningar för iOS (com.microsoft.adalcache). För ADAL kan du göra detta genom att [konfigurera egenskapen iOSKeychainSecurityGroup för AuthenticationContext](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/iOS-Keychain-Access). För MSAL måste du [ange egenskapen iOSKeychainSecurityGroup för PublicClientApplication](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Xamarin-iOS-specifics#enable-keychain-access). Därefter behöver du åsidosätta de AAD-standardinställningar som används av Intune SDK med inställningarna för din app. Du kan göra detta via i ordlistan IntuneMAMSettings i appens Info.plist, såsom anges i [Intune App SDK för iOS Developer Guide](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), eller så kan du använda AAD-åsidosättningsegenskaper för IntuneMAMPolicyManager-instansen. Metoden Info.plist rekommenderas för program vars ADAL-inställningar är statiska medan egenskaper för åsidosättning rekommenderas för program som fastställer dessa värden vid körning. När alla inställningar för enkel inloggning har konfigurerats bör din app tillhandahålla användarens UPN för IntuneMAMEnrollmentManagers RegisterAndEnrollAccount-metod när den har autentiserats:

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
1. Lägg till [Microsoft.Intune.MAM.Xamarin.Android NuGet-paketet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) i ditt Xamarin.Android-projekt.
    1. För en Xamarin.Forms-app lägger du även till [Microsoft.Intune.MAM.Remapper.Tasks NuGet-paketet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) i Xamarin.Android-projektet. 
2. Följ de allmänna stegen som krävs för att [integrera Intune App SDK](app-sdk-android.md) med en Android-mobilapp och läs det här dokumentet för ytterligare information.

### <a name="xamarinandroid-integration"></a>Xamarin.Android integration

En fullständig översikt över integreringen av Intune App SDK finns i [utvecklarhandboken för Microsoft Intune App SDK för Android](app-sdk-android.md). När du läser handboken och integrerar Intune App SDK med Xamarin-appen beskriver följande avsnitt skillnaderna mellan implementeringen av en intern Android-app som utvecklas i Java och en Xamarin-app som utvecklas i C#. De här avsnitten kompletterar men ersätter inte resten av handboken.

#### <a name="remapper"></a>Remapper
Från och med 1.4428.1- `Microsoft.Intune.MAM.Remapper` versionen kan paketet läggas till i en Xamarin. Android-app som [build-verktyg](app-sdk-android.md#build-tooling) för att utföra Mam klass-, metod-och system tjänster. Om remapper ingår, utförs MAM motsvarande ersättnings delar av de metoder som har bytt namn och MAM program automatiskt när programmet har skapats.

Om du vill undanta en klass från Mam-ppdateringar av Remapping kan du lägga till följande egenskap i `.csproj` projekt filen.

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Metoder som fått nya namn](app-sdk-android.md#renamed-methods)
I många fall har en metod som är tillgänglig i Android-klassen markerats som slutgiltig i MAM-ersättningsklassen. I detta fall tillhandahåller MAM-ersättningsklassen en metod med liknande namn (med suffixet `MAM`) som ska åsidosättas i stället. Om du härleder från `MAMActivity`, i stället för att åsidosätta `OnCreate()` och anropa `base.OnCreate()`, måste `Activity` åsidosätta `OnMAMCreate()` och anropa `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[MAM-program](app-sdk-android.md#mamapplication)
Din app måste definiera en `Android.App.Application` klass. Om du manuellt integrerar MAM måste det ärva `MAMApplication`från. Se till att din underklass är korrekt dekorerad med attributet `[Application]` och åsidosätter konstruktorn `(IntPtr, JniHandleOwnership)`.

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> Ett problem med MAM Xamarin-bindningar kan göra att programmet kraschar när det distribueras i felsökningsläge. För att komma runt problemet måste du lägga till `Debuggable=false`-attributet i `Application`-klassen och ta bort `android:debuggable="true"`-flaggan från manifestet om den angetts manuellt.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Aktivera funktioner som kräver appmedverkan](app-sdk-android.md#enable-features-that-require-app-participation)
Exempel: Bestäm om en PIN-kod ska krävas för appen

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

Exempel: Fastställa den primära Intune-användaren

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

Exempel: Bestäm om det ska vara tillåtet att spara till enheten eller lagra i molnet

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[Registrera för meddelanden från SDK:n](app-sdk-android.md#register-for-notifications-from-the-sdk)
Appen måste först registreras för meddelanden från SDK:n genom att en `MAMNotificationReceiver` skapas och registreras med `MAMNotificationReceiverRegistry`. Du gör detta genom att ange önskad mottagare och typ av meddelande i `App.OnMAMCreate`, vilket illustreras i exemplet nedan:

```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
        registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[MAM-registreringshanterare](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms integration

För `Xamarin.Forms`-program utför `Microsoft.Intune.MAM.Remapper`-paketet MAM-klassersättning automatiskt genom att injicera `MAM`-klasser i klasshierarkin för vanliga `Xamarin.Forms`-klasser. 

> [!NOTE]
> Xamarin.Forms-integrationen ska göras utöver Xamarin.Android-integreringen som beskrivs ovan.

När ommappningen har lagts till i ditt projekt måste du utföra motsvarande MAM-ersättningar. Exempelvis kan `FormsAppCompatActivity` och `FormsApplicationActivity` fortsätta att användas i dina program förutsatt att `OnCreate`- och `OnResume`-åsidosättningar ersätts med MAM-motsvarigheterna `OnMAMCreate` respektive `OnMAMResume`.

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```

Om ersättningarna inte görs kan du få följande kompileringsfel tills du gör ersättningarna:
* [Kompilatorfel CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). Det här felet hittas oftast i det här formatet ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Det här förväntas, eftersom när ommappningen ändrar arvet för Xamarin-klasser så blir vissa funktioner `sealed`, och en ny variant av MAM läggs i stället till som åsidosättning.
* [Kompilatorfel CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): Det här felet uppstår ofta i följande form: ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. När ommappningen ändrar arvet för några av Xamarin-klasserna ändras vissa av medlemsfunktionerna till `public`. Om du åsidosätter någon av dessa funktioner måste du ändra åtkomstmodifierarna för dessa åsidosättningar till `public`.

> [!NOTE]
> Ommappningen skriver om ett beroende som Visual Studio använder för automatisk komplettering med IntelliSense. Därför kan du behöva återskapa och läsa in projektet igen när ommappningen läggs till för att IntelliSense ska identifiera ändringarna korrekt.

### <a name="company-portal-app"></a>Företagsportalappen
Intune SDK Xamarin-bindningar använder sig av den [företagsportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android-appen på enheten för att aktivera skydds principer för appar. Företagsportalen hämtar appskyddsprinciper från Intune-tjänsten. När appen initieras läser den in principen och koden för att kunna aktivera principen från företagsportalen. Användaren behöver inte vara inloggad.

> [!NOTE]
> Om Företagsportalsappen inte finns på **Android**-enheten fungerar en Intune-hanterad app som en normal app som saknar stöd för Intunes appskyddsprinciper.

Vid appskydd utan enhetsregistrering behöver användaren _**inte**_ registrera enheten med företagsportalappen.

### <a name="sample-applications"></a>Exempel program
Exempel program som markerar MAM-funktioner i Xamarin. Android-och Xamarin-formulär appar finns på [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps).

## <a name="support"></a>Stöd
Om din organisation är en befintlig Intune-kund kan du kontakta din representant på Microsofts support för att öppna en supportbegäran och skapa ett ärende [på sidan med GitHub-ärenden](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) så hjälper vi dig så snart vi kan. 
