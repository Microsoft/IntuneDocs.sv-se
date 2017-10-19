---
title: Microsoft Intune App SDK Xamarin-komponenten
description: 
keywords: sdk, Xamarin, intune
author: mattbriggs
manager: angrobe
ms.author: mabriggs
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8ab9807d22aa1a5c232b595df2bd999c0c178b16
ms.sourcegitcommit: f3b8fb8c47fd2c9941ebbe2c047b7d0a093e5a83
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2017
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Microsoft Intune App SDK Xamarin-komponenten

> [!NOTE]
> Börja gärna med att läsa artikeln [Komma igång med Intune App SDK](app-sdk-get-started.md). Den här guiden beskriver hur du förbereder dig för integreringen på de plattformar som stöds.



## <a name="overview"></a>Översikt
[Intune App SDK Xamarin-komponenten](https://components.xamarin.com/view/microsoft.intune.mam) aktiverar [Intunes appskyddsprincip](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) i iOS- och Android-appar som skapats med Xamarin. Komponenten hjälper utvecklare att enkelt bygga in funktioner för appskydd med Intune i Xamarin-baserade appar.

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

## <a name="prerequisites"></a>Förutsättningar

* **[Android]** Den senaste Microsoft Intune-företagsportalappen måste vara installerad på enheten.

## <a name="get-started"></a>Kom igång

1.  Ladda ned **Xamarin-component.exe** [här](https://components.xamarin.com/submit/xpkg) och extrahera den.

2. Läs [licensvillkoren](https://components.xamarin.com/license/microsoft.intune.mam) för Microsoft Intune MAM Xamarin-komponenten.

3.  Ladda ned mappen med Intune App SDK Xamarin-komponenten från [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) eller [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) och extrahera den. Båda filerna som du laddade ned i steg 1 och steg 3 bör ligga på samma katalognivå.

4.  Kör `Xamarin.Component.exe install <.xam> file` som administratör på kommandoraden.

5.  I Visual Studio högerklickar du på **komponenter** i Xamarin-projektet som du skapat tidigare.

6.  Välj **Redigera komponenter** och lägg till Intune App-SDK-komponenten som du har laddat ned lokalt till datorn.



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Aktivera Intune-appskyddsprinciper i din iOS-mobilapp
1.  För att initiera Intune App SDK behöver du anropa API:er i `AppDelegate.cs`-klassen. Exempel:

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  Nu när komponenten har lagts till och initierats kan du följa de allmänna stegen som krävs för att skapa App SDK i en iOS-mobilapp. Du kan hitta den fullständiga dokumentationen för att aktivera interna iOS-appar i [utvecklarhandboken för Intune App SDK för iOS](app-sdk-ios.md).
3. **Viktig!** Det finns flera ändringar som är specifika för Xamarin-baserade iOS-appar. Till exempel måste du när du aktiverar nyckelringsgrupper lägga till följande om du vill ta med Xamarin-exempelappen som vi har lagt till i komponenten. Nedan ser du ett exempel på de grupper som måste finnas i dina nyckelhanterargrupper:

      ```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
      <plist version="1.0">
            <dict>
                  <key>keychain-access-groups</key>
                  <array>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample</string>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample.intunemam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.intune.mam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.adalcache</string>
                  </array>
            </dict>
      </plist>
      ```

Du har slutfört stegen som krävs för att bygga in komponenten i din Xamarin-baserade iOS-app. Om du använder Xcode för att skapa projektet kan du använda `Intune App SDK Settings.bundle`. På så sätt kan du aktivera och inaktivera Intune-principinställningar när du skapar ditt projekt för att testa och felsöka. Om du vill utnyttja det här paketet följer du stegen i [utvecklarguiden för Intune App SDK för iOS](app-sdk-ios.md) och läser avsnittet om [felsökning i Xcode](app-sdk-ios.md#status-result-and-debug-notifications).

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Aktivera appskyddsprinciper i din Android-mobilapp
För Xamarin-baserade Android-appar som inte använder ett UI-ramverk läser och följer du [utvecklarguiden för Intune App SDK för Android](app-sdk-android.md). För din Xamarin-baserade Android-app måste du ersätta klassen, metoder och aktiviteter med deras MAM-motsvarigheter baserat på [tabellen](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) som ingår i handboken. Om din app inte definierar en `android.app.Application`-klass måste du skapa en och se till att du ärver från `MAMApplication`.

För Xamarin Forms och andra UI-ramverk tillhandahåller vi verktyget `MAM.Remapper`. Verktyget utför klassersättningen åt dig. Men du måste utföra följande steg:

1.  Lägg till en referens till `Microsoft.Intune.MAM.Remapper.Tasks` NuGet paketversion 0.1.0.0 eller senare.

2.  Lägg till följande rad i Android csproj:
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  Ange build-åtgärden för den tillagda `remapping-config.json`-filen till **RemappingConfigFile**. Den `remapping-config.json`-fil som ingår fungerar endast med Xamarin.Forms. För andra UI-ramverk läser du Viktigt-filen som ingår i Remapper NuGet-paketet.

## <a name="next-steps"></a>Nästa steg

Du har slutfört stegen för att bygga in komponenten i din app. Nu kan du följa stegen i Xamarin Android-exempelappen. Vi tillhandahåller två exempel, ett för Xamarin.Forms och ett för Android.