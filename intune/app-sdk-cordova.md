---
title: Microsoft Intune App SDK Cordova-plugin-programmet
description: 
keywords: sdk, Cordova, intune
author: oydang
manager: angrobe
ms.author: oydang
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 0329720b6f02c718ef27a59e6efc5f3a76eed1c5
ms.contentlocale: sv-se
ms.lasthandoff: 06/08/2017


---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Microsoft Intune App SDK Cordova-plugin-programmet

> [!NOTE]
> Börja gärna med att läsa artikeln [Komma igång med Intune App SDK](app-sdk-get-started.md). Den här guiden beskriver hur du förbereder dig för integreringen på de plattformar som stöds.

## <a name="overview"></a>Översikt

[Intune App SDK Cordova-plugin-programmet](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) i iOS- och Android-appar utvecklade med Cordova. Plugin-programmet gör att utvecklare kan integrera Intunes app- och dataskyddsfunktioner i sina Cordova-baserade appar.

Du kommer märka att du kan aktivera SDK-funktioner utan att ändra appens beteende. När du har skapat plugin-programmet i iOS- eller Android-appen, kommer Microsoft Intune-administratören att kunna distribuera Intunes appskyddsprincip, som består av olika dataskyddsfunktioner. Plugin-programmet är uppbyggt så att de flesta stegen utförs automatiskt i Cordova-skapandeprocessen. Därför är det enkelt att snabbt aktivera appen för Intunes appskydd. Börja genom att följa stegen nedan beroende på din målplattform.

## <a name="supported-platforms"></a>Plattformar som stöds

* Plugin-programmet fungerar i Windows, Mac- och Linux-operativsystem
* Plugin-programmet fungerar i Android-appar med `minSdkVersion` >= 14 och `targetSdkVersion` <= 24
* Plugin-programmet fungerar i iOS-appar som är riktade mot iOS 9.0 och senare.

## <a name="intune-mobile-application-management-scenarios"></a>Scenarion för Intune Mobile Application Management

* Intune MDM-registrerade enheter
* EMM-registrerade enheter från tredje part
* Icke-hanterade enheter (inte registrerade för hantering av mobilenheter)

Cordova-appar som skapats med Intune App SDK Cordova-pluginprogrammet kan nu ta emot Intunes appskyddsprinciper på både Intune MDM-registrerade enheter och oregistrerade enheter.

## <a name="prerequisites"></a>Förutsättningar

### <a name="android"></a>Android

* Den senaste appen för Microsoft Intune-företagsportalen måste alltid vara installerad på enheten.
* Minst Java 7 måste finnas i sökvägen där du ska köra Cordova-versionen när du använder plugin-programmet.

### <a name="ios"></a>iOS

* Den senaste appen för Microsoft Intune-företagsportalen måste vara installerad på enheten för MDM-funktioner. Detta krävs *inte* för Intunes appskyddsprincip utan registreringsfunktioner för enheter.

### <a name="both-platforms"></a>Båda plattformarna

* Version 0.8.0+ av [Azure ADAL-plugin-programmet (Active Directory Authentication Libraries) för Cordova](https://github.com/AzureAD/azure-activedirectory-library-for-cordova) krävs.

> [!NOTE]
> På grund av en Apache Cordova-bugg som finns dokumenterad [här](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22) kommer inte appar som redan är beroende av plugin-programmet att automatiskt uppgradera plugin-programmet till den nödvändiga versionen.



## <a name="quick-start"></a>Snabbstart

1. Uppdatera din version av ADAL:

  ```shell
  cordova plugin remove cordova-plugin-ms-adal
  cordova plugin add cordova-plugin-ms-adal@0.8.x
  ```

2. Lägg till Intune App SDK for Cordova-plugin-programmet:

  ```shell
  cordova plugin add cordova-plugin-ms-intune-mam
  ```

## <a name="build-the-plugin-into-your-ios-app"></a>Skapa plugin-programmet i din iOS-app

Du måste slutföra några steg för att din app ska bli aktiverad för Intunes appskyddsprincip. För att underlätta för dig utförs dessa steg automatiskt i Cordova-genereringsprocessen som en fördefinierad hook. Det betyder att de automatiserade stegen ändrar dina `*.pbxproj`-, `*-Info.plist`- och `*.entitlements`-filer som är associerade med en projektkonfiguration. Om ditt projekt inte innehåller en rättighetsfil skapas en automatiskt av plugin-programmet.

Den här konfigurationen stöder bara ett enda mål och utför konfigurationen på det första målet som identifieras om det finns flera mål. Om processen misslyckas kontrollerar du att:

1. Appens Xcode-projekt är `[name].xcodeproj` där `[name]` är värdet som definierats i `config.xml`
2. Projektet använder [standardstrukturen för Cordova-appkataloger](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure).

## <a name="build-the-plugin-into-your-android-app"></a>Skapa plugin-programmet i din Android-app

1. Importera det här plugin-programmet med de senaste Cordova-verktygen. Plugin-programmet anropas automatiskt som ett `after_compile`-steg.

2. Plugin-programmet skapar en Intune-aktiverad version av en skapad apk (Android API 14+) i slutet av skapandeprocessen. Resultatet innehåller en `[Project]-intunewrapped-[Build_Configuration].apk` (t.ex. `helloWorld-intunewrapped-debug.apk`).

> [!NOTE]
> Plugin-programmet stöder endast gradle-genereringsprocesser.

På grund en Cordova-bugg som finns dokumenterad [här](https://issues.apache.org/jira/browse/CB-9434), som gör att vissa Cordova-hookar ignoreras med `cordova run`, måste du göra följande för att köra den omslutna appen från kommandoraden:

```shell
$ cordova build
$ cordova run --nobuild
```

## <a name="sign-your-android-app"></a>Signera din Android-app

Plugin-programmet identifierar automatiskt signeringsinformationen som du har angett för Cordova på följande platser:

* platforms/android/debug-signing.properties
* platforms/android/release-signing.properties
* res/native/android/ant.properties

Se [signeringsinformationen för Cordova-gradle](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#using-gradle) för mer information om det förväntade formatet.

Vi har för tillfället inte stöd för möjligheten att tillhandahålla signeringsinformation i `build.json` eller andra platser som tillhandahålls via parametrar till Cordova-versionen.

## <a name="debugging-from-visual-studio"></a>Felsöka från Visual Studio

Första gången du startar appen bör du se en dialogruta som meddelar dig att appen hanteras av Intune. Klicka på ”Visa inte igen” och klicka på felsökning/kör-knappen från VS för brytpunkter som påträffas.

## <a name="known-limitations"></a>Kända begränsningar

### <a name="android"></a>Android

* Stödet för MultiDex är ofullständigt.
* Appen måste ha `minSdkVersion` av 14 och `targetSdkVersion` av 24 eller mindre. Vi har för tillfället inte stöd för appar som är riktade mot API 25
* Vi kan inte signera appar på nytt som har signerats med V2-signaturschemat. När V2-signerade appar är omslutna av plugin-programmet, kommer omslutna .apk-utdata vara osignerade.
*
  * Du kan inaktivera Cordovas standardmässiga V2-signering genom att lägga till följande i filen `build-extras.gradle`:

  ```gradle
  android {
      signingConfigs {
          release {
              v2SigningEnabled false
          }
          debug {
              v2SigningEnabled false
          }
      }
      buildTypes {
          release {
              signingConfig signingConfigs.release
          }
          debug {
              signingConfig signingConfigs.debug
          }
      }
  }
  ```

### <a name="ios"></a>iOS

* När du ändrar UTI-listan under noden **CFBundleDocumentTypes** i filen **Info.plist**, måste du rensa Intunes UTI:er i avsnittet med importerade UTI:er i samma plist-fil (noden **UTImportedTypeDeclarations**) innan du skapar den igen. Alla Intunes UTI:er börjar med prefixet `com.microsoft.intune.mam`.

* Om du vill ta bort Intune App SDK för Cordova-pluginprogrammet från ditt Cordova-projekt, måste du också ta bort iOS-plattformen och lägga till den igen för att ta bort en del av Intune-konfigurationen i filerna .xcodeproj och .plist.

