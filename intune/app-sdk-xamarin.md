---
title: Microsoft Intune App SDK Xamarin-komponenten
description: Med Intune App SDK Xamarin-komponenten kan du använda Intunes appskyddsprincip i iOS- och Android-appar som skapats med Xamarin.
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
ms.openlocfilehash: b69cccca8c8be859de94ca8bdb50d6030439233a
ms.sourcegitcommit: 54fc806036f84a8667cf8f74086358bccd30aa7d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/20/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Microsoft Intune App SDK Xamarin-komponenten

> [!NOTE]
> Börja gärna med att läsa artikeln [Komma igång med Intune App SDK](app-sdk-get-started.md). Den här guiden beskriver hur du förbereder dig för integreringen på de plattformar som stöds.

## <a name="overview"></a>Översikt
[Intune App SDK Xamarin-komponenten](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) aktiverar [Intunes appskyddsprincip](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) i iOS- och Android-appar som skapats med Xamarin. Komponenten hjälper utvecklare att enkelt bygga in funktioner för appskydd med Intune i Xamarin-baserade appar.

> [!NOTE]
> Stöd för Intune SDK för Xamarin är tillgängligt i förhandsversionen. 

Med Xamarin-komponenten för Microsoft Intune App kan du lägga till Intune-appskyddsprinciper (även kallade APP- eller MAM-principer) i dina appar som utvecklats med Xamarin. Ett MAM-aktiverat program är ett program som är integrerat med Intune App SDK. Det kan användas av IT-administratörer för att distribuera appskyddsprinciper till din mobilapp om Intune aktivt hanterar appen.

## <a name="whats-supported"></a>Vad stöds?

### <a name="developer-machines"></a>Datorer för utvecklare
* macOS


### <a name="mobile-app-platforms"></a>Plattformar för mobilappar
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Scenarion för Intune Mobile Application Management

* Intune MDM-registrerade enheter
* EMM-registrerade enheter från tredje part
* Icke-hanterade enheter (inte registrerade för hantering av mobilenheter)

Xamarin-appar som skapats med Xamarin-komponenten för Intune App SDK kan nu ta emot Intunes appskyddsprinciper på både Intune MDM-registrerade enheter och oregistrerade enheter.

## <a name="prerequisites"></a>Krav

* **[Android]** Den senaste Microsoft Intune-företagsportalappen måste vara installerad på enheten.

## <a name="get-started"></a>Kom igång

1. Läs [licensvillkoren](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf) för Microsoft Intune MAM Xamarin-komponenten.

2.  Ladda ner Intune App SDK Xamarin-komponentens NuGet-paket från [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin). Dessa paket kommer snart att vara tillgängliga på Nuget.org.  

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Aktivera Intune-appskyddsprinciper i din iOS-mobilapp
1. Lägg till `Microsoft.Intune.MAM.Xamarin.iOS` NuGet-paket i ditt Xamarin.iOS-projekt.
2.  Följ de allmänna steg som krävs för att integrera Intune App SDK i en mobila iOS-app. Du kan börja med steg 3 av integrationsinstruktionerna från [Utvecklingsguide för Intune App SDK för iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Du kan hoppa över det sista steget i avsnittet om att köra IntuneMAMConfigurator, eftersom detta verktyg ingår i paketet Microsoft.Intune.MAM.Xamarin.iOS och körs automatiskt under byggtiden.
    **Viktigt**: Aktivering av nyckelringsdelning för en app skiljer sig något åt mellan Visual Studio och Xcode. Öppna appens .plist för rättigheter och kontrollera att alternativet ”Aktivera nyckelringar” är aktiverat och att lämpliga delningsgrupper för nyckelringar har lagts till i avsnittet. Kontrollera sedan att .plist för rättigheter har angetts i fältet ”anpassade rättigheter” i projektets alternativ ”iOS-paketsignering” för alla lämpliga kombinationer av konfiguration/plattform.
3.  När komponenten läggs till och appen är korrekt konfigurerad, kan din app börja använda Intune SDK:s API:er. Om du vill göra detta, måste du inkludera följande namnrymd:

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
Lägg till `Microsoft.Intune.MAM.Xamarin.Android` NuGet-paket i ditt Xamarin.Android-projekt.

För Xamarin-baserade Android-appar som inte använder ett UI-ramverk läser och följer du [utvecklarguiden för Intune App SDK för Android](app-sdk-android.md). För din Xamarin-baserade Android-app måste du ersätta klassen, metoder och aktiviteter med deras MAM-motsvarigheter baserat på [tabellen](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) som ingår i handboken. Om din app inte definierar en `android.app.Application`-klass måste du skapa en och se till att du ärver från `MAMApplication`.

För Xamarin Forms och andra UI-ramverk tillhandahåller vi verktyget `MAM.Remapper`. Verktyget utför klassersättningen åt dig. Men du måste utföra följande steg:

1.  Lägg till `Microsoft.Intune.MAM.Remapper.Tasks` NuGet-paket.

2.  Lägg till följande rad i din Android-csproj (Ersätt ”x.x.x.x” med den faktiska paketversionen):
  ```xml
 <Import Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.x.x.x.x\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  Ange build-åtgärden för den tillagda `remapping-config.json`-filen till **RemappingConfigFile**. Den `remapping-config.json`-fil som ingår fungerar endast med Xamarin.Forms. För andra UI-ramverk läser du Viktigt-filen som ingår i Remapper NuGet-paketet.

## <a name="next-steps"></a>Nästa steg

Du har slutfört stegen för att bygga in komponenten i din app. Nu kan du följa stegen i Xamarin Android-exempelappen. Vi tillhandahåller två exempel, ett för Xamarin.Forms och ett för Android.
