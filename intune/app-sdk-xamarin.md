---
title: Microsoft Intune App SDK Xamarin-bindningar
description: Med Intune App SDK Xamarin-bindningar kan du använda Intunes appskyddsprincip i iOS- och Android-appar som skapats med Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/16/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd162f6af256c104c04374290a695141cdcc26f6
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566207"
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

1. Lägg till [Microsoft.Intune.MAM.Xamarin.Android NuGet-paketet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) i ditt Xamarin.Android-projekt.
    1. För en Xamarin.Forms-app lägger du till den [Microsoft.Intune.MAM.Remapper.Tasks NuGet-paketet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) i ditt Xamarin.Android-projekt. 
2. Följ de allmänna steg som krävs för [integrera Intune App SDK](app-sdk-android.md) till en Android-mobilapp samtidigt som refererar till det här dokumentet för ytterligare information.

### <a name="xamarinandroid-integration"></a>Xamarin.Android integration

En fullständig översikt för att integrera Intune App SDK finns i den [Microsoft Intune App SDK för Android-utvecklarguiden](app-sdk-android.md). När du har läst igenom guiden och integrera Intune App SDK med Xamarin-appen i följande avsnitt är avsedda att markera skillnaderna mellan implementeringen för interna Android-app som har utvecklats i Java och en Xamarin-app som utvecklats i C#. De här avsnitten ska behandlas som kompletterande och kan inte fungera som en ersättning för att läsa guiden i sin helhet.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Metoder som fått nya namn](app-sdk-android.md#renamed-methods)
I många fall har en metod som är tillgänglig i Android-klassen markerats som slutgiltig i MAM-ersättningsklassen. I detta fall tillhandahåller MAM-ersättningsklassen en metod med liknande namn (med suffixet `MAM`) som ska åsidosättas i stället. Om du härleder från `MAMActivity`, i stället för att åsidosätta `OnCreate()` och anropa `base.OnCreate()`, måste `Activity` åsidosätta `OnMAMCreate()` och anropa `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[MAM-program](app-sdk-android.md#mamapplication)
Din app måste definiera ett `Android.App.Application` klass som ärver från `MAMApplication`. Se till att din underklass är korrekt dekorerad med attributet `[Application]` och åsidosätter konstruktorn `(IntPtr, JniHandleOwnership)`.
```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

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

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[MAM Registreringshanterare](app-sdk-android.md#mamenrollmentmanager)
```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms integration

För `Xamarin.Forms` program har vi lagt till den `Microsoft.Intune.MAM.Remapper` paketet för att utföra MAM klassersättningen automatiskt genom att placera `MAM` klasser i klasshierarkin av vanliga `Xamarin.Forms` klasser. 

> [!NOTE]
> Xamarin.Forms-integrering är också göras i Xamarin.Android-integrationen som beskrivs ovan.

När Remapper läggs till i ditt projekt måste du utföra MAM motsvarande ersättningar. Till exempel `FormsAppCompatActivity` och `FormsApplicationActivity` kan fortsätta att användas i dina program tillhandahålls åsidosättningar för `OnCreate` och `OnResume` ersätts med MAM-motsvarigheter `OnMAMCreate` och `OnMAMResume` respektive.

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
Om ersättningarna inte görs kan du får följande kompileringsfel förrän du gör ersättningarna:
* [Kompilatorfel CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). Det här felet hittas oftast i det här formatet ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Det här förväntas, eftersom när ommappningen ändrar arvet för Xamarin-klasser så blir vissa funktioner `sealed`, och en ny variant av MAM läggs i stället till som åsidosättning.
* [Kompilatorn fel CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): det här felet uppstår vanligen i det här formuläret ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. När ommappningen ändrar arvet för några av Xamarin-klasserna ändras vissa av medlemsfunktionerna till `public`. Om du åsidosätter någon av dessa funktioner kan du behöver ändra dem åtkomstmodifierare för de åsidosättningar för att vara `public` samt.

> [!NOTE]
> Remapper skriver ett beroende som Visual Studio använder för IntelliSense automatisk komplettering. Därför kan du behöva uppdatera och återskapa projektet när Remapper har lagts till för IntelliSense att korrekt identifiera ändringarna.

## <a name="support"></a>Stöd
Om organisationen är en befintlig Intune-kund kan du kontakta din representant från Microsofts support för att öppna en supportbegäran och skapa ett ärende [på sidan med GitHub-ärenden](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) så hjälper vi dig så snart vi kan. 
