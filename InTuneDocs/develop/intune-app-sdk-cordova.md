---
title: Microsoft Intune App SDK Cordova-plugin-programmet | Microsoft Docs
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
translationtype: Human Translation
ms.sourcegitcommit: 613e293d9bd853d6de7cdc0d753cc8473afc180b
ms.openlocfilehash: 9ef09f43e6c878af689a500457bab578149de499


---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Microsoft Intune App SDK Cordova-plugin-programmet

> [!NOTE]
> Börja gärna med att läsa artikeln [Komma igång med Intune App SDK](intune-app-sdk-get-started.md). Den här guiden beskriver hur du förbereder dig för integreringen på de plattformar som stöds.


## <a name="overview"></a>Översikt

[Intune App SDK Cordova-plugin-programmet](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam) aktiverar [Intunes apphanteringsfunktioner](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) i iOS- och Android-appar som skapats med Cordova. Plugin-programmet gör att utvecklare kan integrera Intunes app- och dataskyddsfunktioner i sina Cordova-baserade appar.

Som du kommer märka kan du aktivera SDK-funktioner utan att ändra appens beteende. När du har byggt in plugin-programmet i din iOS- eller Android-mobilapp kan IT-administratören distribuera principer via Microsoft Intune Mobile Application Management (MAM), som stöder olika funktioner för dataskydd. Vi har byggt plugin-programmet så att de flesta stegen utförs automatiskt i Cordova-genereringsprocessen. Därför bör det vara enkelt för dig att snabbt aktivera appen för hantering. Börja genom att följa stegen nedan beroende på din målplattform.




## <a name="whats-supported"></a>Vad stöds?

### <a name="developer-machines"></a>Datorer för utvecklare
* Windows
* Mac OS


### <a name="mobile-app-platforms"></a>Plattformar för mobilappar
* Android 4.0+
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Scenarion för Intune Mobile Application Management

* Intune MDM-registrerade enheter
* EMM-registrerade enheter från tredje part
* Icke-hanterade enheter (inte registrerade för hantering av mobilenheter)

Nu stöder Cordova-appar som skapats med Intune App SDK Cordova plugin-programmet Intune MAM-principer för hantering av mobilprogram både på Intune MAM-registrerade enheter och oregistrerade enheter.



## <a name="prerequisites"></a>Förutsättningar

### <a name="technical-prerequisites"></a>Tekniska krav

* **[Android]** Den senaste Microsoft Intune-företagsportalappen måste alltid vara installerad på enheten.


* Version 0.8.0+ av [Azure ADAL-plugin-programmet (Active Directory Authentication Libraries) för Cordova](https://github.com/AzureAD/azure-activedirectory-library-for-cordova) krävs.
  * **Viktigt:** På grund av en Apache Cordova-bugg som finns dokumenterad [här](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22) kommer inte appar som redan är beroende av plugin-programmet att automatiskt uppgradera plugin-programmet till den nödvändiga versionen.


### <a name="before-you-install-and-use-microsoft-intune-app-sdk-cordova-plugin-you-must"></a>Innan du installerar och använder Microsoft Intune App SDK Cordova-plugin-programmet **måste** du:

* Läsa [licensvillkoren för Intune App SDK Cordova-plugin-programmet](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam/blob/master/Intune_App_SDK_Cordova_plugin_RTM_license.pdf).

* Skriv ut och behåll en kopia av licensvillkoren för framtida referens. Genom att hämta och använda Intune App SDK Cordova-plugin-programmet samtycker du till dessa licensvillkor.  Om du inte accepterar villkoren har du inte rätt att använda programvaran.


## <a name="quick-start"></a>Snabbstart

1. Uppdatera din version av ADAL:

    ```
    cordova plugin remove cordova-plugin-ms-adal
    cordova plugin add cordova-plugin-ms-adal@0.8.x
    ```

2. Lägg till Intune App SDK for Cordova-plugin-programmet:

    ```
    cordova plugin add cordova-plugin-ms-intune-mam
    ```

## <a name="how-to-build-the-plugin-into-your-ios-app"></a>Bygga in plugin-programmet i din iOS-app

Du måste du utföra några steg för att aktivera din app för Intune MAM. För att underlätta för dig utförs dessa steg automatiskt i Cordova-genereringsprocessen som en fördefinierad hook. Det betyder att de automatiserade stegen ändrar dina `*.pbxproj`-, `*-Info.plist`- och `*.entitlements`-filer som är associerade med en projektkonfiguration. Om ditt projekt inte innehåller en rättighetsfil skapas en automatiskt av plugin-programmet.

Den här konfigurationen stöder bara ett enda mål och utför konfigurationen på det första målet som identifieras om det finns flera mål. Om processen misslyckas kontrollerar du att:

1. Appens Xcode-projekt är `[name].xcodeproj` där `[name]` är värdet som definierats i `config.xml`
2. Projektet använder [standardstrukturen för Cordova-appkataloger](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure).

## <a name="how-to-build-the-plugin-into-your-android-app"></a>Skapa plugin-programmet i din Android-app

1. Importera det här plugin-programmet med de senaste Cordova-verktygen. Plugin-programmet anropas automatiskt som ett `after_compile`-steg.

2. Plugin-programmet skapar en MAM-aktiverad version av en skapad apk (Android API 14+) i slutet av genereringsprocessen. Resultatet innehåller en `[Project]-intunewrapped-[Build_Configuration].apk` (t.ex. `helloWorld-intunewrapped-debug.apk`).

Plugin-programmet stöder endast gradle-genereringsprocesser.

På grund en Cordova-bugg som finns dokumenterad [här](https://issues.apache.org/jira/browse/CB-9434), som gör att vissa Cordova-hookar ignoreras med `cordova run`, måste du göra följande för att köra den omslutna appen från kommandoraden:

```
$ cordova build
$ cordova run --nobuild
```


### <a name="signing-your-android-app"></a>Signera din Android-app
Om du vill lägga till signeringsinformation till den omslutna apk:n ändrar du `build.json` som vanligt för att lägga till signeringsinformation. Exempel:
```json
{
  "android": {
    "release": {
      "keystore": "your.keystore",
      "storePassword": "yourpassword",
      "alias": "youralias",
      "password" : "yourpassword",
      "keystoreType": ""
    }
  }
}
```

### <a name="build-for-android-test-only"></a>Generering för Android-testning

1. Lägg till `android:testOnly="true"` i programnoden i `AndroidManifest.xml`-filen.


2. **Cordova 6.x.x:** I `[PROJECT_ROOT]/platforms/android/cordova/lib/Adb.js` ändrar du rad 60 från

    ```javascript
    var args = ['-s', target, 'install'];
    ```
    på
    ```javascript
    var args = ['-s', target, 'install', '-t'];
    ```

Effekten av detta är att du kör `adb install` med ”-t”-flaggan eftersom `testOnly`-appar inte kan installeras utan den.

### <a name="debugging-from-visual-studio"></a>Felsöka från Visual Studio
Första gången du startar appen bör du se en dialogruta som meddelar dig att appen hanteras av Intune. Klicka på ”Visa inte igen” och klicka på felsökning/kör-knappen från VS för brytpunkter som påträffas.

## <a name="known-limitations"></a>Kända begränsningar
### <a name="android"></a>Android
* Stödet för MultiDex är ofullständigt.
* Appens mål måste vara Android 4.0 (Android API 14) eller senare.

### <a name="ios"></a>iOS
* När du ändrar UTI-listan under **CFBundleDocumentTypes**-noden i **Info.plist**-filen måste du rensa Intunes UTI:er i avsnittet med importerade UTI:er i samma plist-fil (**UTImportedTypeDeclarations**-noden) innan du skapar den igen. Alla Intunes UTI:er börjar med prefixet `com.microsoft.intune.mam`.

* Om du vill ta bort Intune-plugin-programmet från ditt Cordova-projekt måste du också ta bort iOS-plattformen och lägg till den igen för att ångra en del av Intune-konfigurationen i .xcodeproj- och .plist-filerna.



<!--HONumber=Dec16_HO2-->


