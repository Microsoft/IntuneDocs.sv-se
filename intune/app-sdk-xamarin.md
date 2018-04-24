---
title: Microsoft Intune App SDK Xamarin-bindningar
description: Med Intune App SDK Xamarin-bindningar kan du använda Intunes appskyddsprincip i iOS- och Android-appar som skapats med Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9f9cc117925f59c9fb7c55d0ff10aedf09d26f93
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/06/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin-bindningar

> [!NOTE]
> Börja gärna med att läsa artikeln [Komma igång med Intune App SDK](app-sdk-get-started.md). Den här guiden beskriver hur du förbereder dig för integreringen på de plattformar som stöds.

## <a name="overview"></a>Översikt
Med [Intune App SDK Xamarin-bindningar](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) kan du använda [Intunes appskyddsprincip](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) i iOS- och Android-appar som skapats med Xamarin. Bindningarna hjälper utvecklare att enkelt bygga in appskyddsfunktioner för Intune i Xamarin-baserade appar.

Med Microsoft Intune App SDK Xamarin-bindningar kan du inkludera Intunes appskyddsprinciper (även kallade APP- eller MAM-principer) i dina appar som utvecklats med Xamarin. Ett MAM-aktiverat program är ett program som är integrerat med Intune App SDK. IT-administratörer kan distribuera appskyddsprinciper till den mobila appen när Intune hanterar appen aktivt.

## <a name="whats-supported"></a>Vad stöds?

### <a name="developer-machines"></a>Datorer för utvecklare
* Windows
* macOS


### <a name="mobile-app-platforms"></a>Plattformar för mobilappar
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Scenarion för Intune Mobile Application Management

* Intune APP-WE (utan enhetsregistrering)
* Intune MDM-registrerade enheter
* EMM-registrerade enheter från tredje part

Xamarin-appar som skapats med Intune App SDK Xamarin-bindningar kan nu ta emot Intunes appskyddsprinciper på både MDM-registrerade Intune-enheter och oregistrerade enheter.

## <a name="prerequisites"></a>Förutsättningar

Granska [licensvillkoren](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Skriv ut och behåll en kopia av licensvillkoren. Genom att ladda ned och använda Intune App SDK Xamarin-bindningar godkänner du licensvillkoren. Om du inte accepterar villkoren har du inte rätt att använda programvaran.

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Aktivera Intune-appskyddsprinciper i din iOS-mobilapp
1. Lägg till [Microsoft.Intune.MAM.Xamarin.iOS NuGet-paketet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) i ditt Xamarin.iOS-projekt.
2.  Följ de allmänna steg som krävs för att integrera Intune App SDK i en mobila iOS-app. Du kan börja med steg 3 av integrationsinstruktionerna från [Utvecklingsguide för Intune App SDK för iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Du kan hoppa över det sista steget i avsnittet om att köra IntuneMAMConfigurator, eftersom detta verktyg ingår i paketet Microsoft.Intune.MAM.Xamarin.iOS och körs automatiskt under byggtiden.
    **Viktigt**: Aktivering av nyckelringsdelning för en app skiljer sig något åt mellan Visual Studio och Xcode. Öppna appens .plist för rättigheter och kontrollera att alternativet ”Aktivera nyckelringar” är aktiverat och att lämpliga delningsgrupper för nyckelringar har lagts till i avsnittet. Kontrollera sedan att .plist för rättigheter har angetts i fältet ”anpassade rättigheter” i projektets alternativ ”iOS-paketsignering” för alla lämpliga kombinationer av konfiguration/plattform.
3.  När bindningarna har lagts till och appen är korrekt konfigurerad, kan din app börja använda Intune SDK:s API:er. Om du vill göra detta, måste du inkludera följande namnrymd:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. För att kunna ta emot skyddsprinciper, måste appen registreras i Intune MAM-tjänsten. Om din app redan använder Azure Active Directory Authentication Library (ADAL) för att autentisera användare, bör din app tillhandahålla användarens UPN för IntuneMAMEnrollmentManager registerAndEnrollAccount-metoden när den har autentiserats:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **Viktigt**: Se till att åsidosätta Intune App SDK:ens standardinställningar för ADAL med appens. Du kan göra detta via i ordlistan IntuneMAMSettings i appens Info.plist, såsom anges i [Intune App SDK för iOS Developer Guide](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), eller så kan du använda AAD-åsidosättningsegenskaper för IntuneMAMPolicyManager-instansen. Metoden Info.plist rekommenderas för program vars ADAL-inställningar är statiska medan egenskaper för åsidosättning rekommenderas för program som fastställer dessa värden vid körning. 
      
      Om din app inte använder ADAL, och du vill att Intune SDK ska hantera autentisering, bör din app anropa IntuneMAMEnrollmentManager loginAndEnrollAccount-metoden:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Aktivera appskyddsprinciper i din Android-mobilapp
Lägg till [Microsoft.Intune.MAM.Xamarin.Android NuGet-paketet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) i ditt Xamarin.Android-projekt.

För Xamarin.Android-appar måste du läsa och följa [Utvecklarhandbok för Intune App SDK för Android](app-sdk-android.md) fullständigt, inklusive att ersätta klass, metoder och aktiviteter med deras MAM-motsvarighet baserat på [tabellen](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) i handboken. 

> [!NOTE]
> Om din app inte definierar en `android.app.Application`-klass måste du skapa en och se till att du ärver från `MAMApplication`.

> [!NOTE]
> När du försöker hitta motsvarande API:er i [Utvecklarhandbok för Intune App SDK för Android](app-sdk-android.md) i `Microsoft.Intune.MAM.Xamarin.Android`-bindningar eller konvertera kodavsnitt från handboken, bör du tänka på att Xamarin-bindningarnas generator ändrar Android-API:er på följande sätt:
> * Alla identifierare konverteras till Pascale-skiftläge (com.microsoft.foo -> Com.Microsoft.Foo)
> * Alla get/set-åtgärder konverteras till egenskapsåtgärder (t.ex. Foo.getBar() -> Foo.Bar, Foo.setBar("zap") -> Foo.Bar = "zap")
> * Alla gränssnitt har tecknet "I" före namnet (FooInterface -> IFooInterface)

För appar som använder Xamarin.Forms och andra UI-ramverk finns verktyget `Microsoft.Intune.MAM.Remapper`. Verktyget utför klassersättningen åt dig. Om du vill använda det gör du följande:

1.  Lägg till NuGet-paketet [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) i projektet.

2.  Ange byggåtgärd för den `remapping-config.json`-fil som ingår i Nuget-paketet till **RemappingConfigFile**. Den `remapping-config.json`-fil som ingår fungerar endast med Xamarin.Forms. För andra UI-ramverk läser du Viktigt-filen som ingår i Remapper NuGet-paketet.

3.  Lägg till ett anrop till Xamarin.Forms.Forms.Init(Context, Bundle) i din OnMAMCreate-funktion för MAMApplication, eftersom med Intune-hanteringen kan programmet startas i bakgrunden.

4.  Utför resten av de steg i [Utvecklarhandbok för Intune App SDK för Android](app-sdk-android.md) som gäller för din app.

> [!NOTE]
> Byggåtgärden för remapping-config.json kan ibland återställas när du uppdaterar paketet Microsoft.Intune.MAM.Remapper.Tasks, vilket medför att dina byggåtgärder misslyckas.

## <a name="next-steps"></a>Nästa steg

Du har slutfört de grundläggande stegen för att konfigurera din app för Intune-hantering. Nu kan du följa stegen i integreringsguiderna för de plattformar som anges ovan.

Om organisationen är en befintlig Intune-kund kan du kontakta din representant från Microsofts support för att öppna en supportbegäran och skapa ett ärende [på sidan med GitHub-ärenden](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) så hjälper vi dig så snart vi kan. 