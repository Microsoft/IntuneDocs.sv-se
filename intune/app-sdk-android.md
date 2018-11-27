---
title: Utvecklarhandbok för Microsoft Intune App SDK för Android
description: Med Microsoft Intune App SDK för Android kan du implementera hantering av mobila appar (MAM, Mobile App Management) med Intune i din Android-app.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 12c48a00e4b755409b698d5f2ee6182403802f23
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190412"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Utvecklarhandbok för Microsoft Intune App SDK för Android

> [!NOTE]
> Börja gärna med att läsa [Översikt över Intune App SDK](app-sdk.md). Den beskriver funktionerna i SDK, samt visar hur du förbereder integreringen på de plattformar som stöds.

Med Microsoft Intune App SDK för Android kan du lägga till Intune-appskyddsprinciper (även kallade **APP**- eller MAM-principer) i din Android-app. Ett Intune-hanterat program är ett program som är integrerat med Intune App SDK. Intune-administratörer kan enkelt distribuera appskyddsprinciper till din Intune-hanterade app när Intune aktivt hanterar appen.


## <a name="whats-in-the-sdk"></a>Vad innehåller SDK?

Intune App SDK består av följande filer:

* **Microsoft.Intune.MAM.SDK.aar**: SDK-komponenterna, med undantag för JAR-filerna för stödbiblioteket.
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: De klasser som behövs för att aktivera MAM i appar som använder Androids v4-stödbiblioteket.
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: De klasser som behövs för att aktivera MAM i appar som använder Androids v7-stödbiblioteket.
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**: De klasser som behövs för att aktivera MAM i appar som använder Androids v17-stödbiblioteket. 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**: De klasser som behövs för att aktivera MAM i appar som använder Android-stödbiblioteksklasser i paketet `android.support.text`.
* **Microsoft.Intune.MDM.SDK.DownlevelStubs.jar**: Den här JAR-filen innehåller stub-rutiner för Android-systemklasser som endast finns på nya enheter men som refereras till av metoder i MAMActivity. Nya enheter ignorerar de här stub-klasserna. Den här JAR-filen krävs endast om din app utför reflektion på klasser härledda från MAMActivity. För de flesta appar behövs den inte. Var noga med att utesluta klasser från ProGuard om du använder JAR-filen. De finns under rotpaketet ”android”
* **com.microsoft.Intune.mam.build.JAR**: Ett Gradle-plugin-program som [underlättar integreringen av SDK](#build-tooling).
* **CHANGELOG.txt**: Innehåller en post med ändringar som gjorts i varje SDK-version.
* **THIRDPARTYNOTICES.TXT**: Information om tredjeparts- och/eller OSS-kod som ingår i appen.

## <a name="requirements"></a>Krav

SDK:n stöder Android API 19 (Android 4.4+) till och med Android API 28 (Android 8.0).


### <a name="company-portal-app"></a>Företagsportalappen
Intune App SDK för Android förutsätter att [företagsportalappen](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) finns på enheten för att appskyddsprinciperna ska kunna aktiveras. Företagsportalen hämtar appskyddsprinciper från Intune-tjänsten. När appen initieras läser den in principen och koden för att kunna aktivera principen från företagsportalen.

> [!NOTE]
> Om appen Företagsportal inte finns på enheten fungerar en Intune-hanterad app som en normal app som saknar stöd för Intunes appskyddsprinciper.

Vid appskydd utan enhetsregistrering behöver användaren _**inte**_ registrera enheten med företagsportalappen.

## <a name="sdk-integration"></a>SDK-integrering

### <a name="referencing-intune-app-libraries"></a>Referera till Intune App-bibliotek

Intune App SDK är ett Android-standardbibliotek utan externa beroenden. **Microsoft.Intune.MAM.SDK.aar** innehåller både de gränssnitt som krävs för att aktivera en appskyddsprincip och den kod som behövs för att interagera med Microsoft Intunes företagsportalappen.

**Microsoft.Intune.MAM.SDK.aar** måste anges som en Android-biblioteksreferens. Gör detta genom att öppna approjektet i Android Studio och gå till **Arkiv > Ny > Ny modul**. Välj **Importera .JAR/.AAR-paket**. Välj sedan Android-arkivpaketet Microsoft.Intune.MAM.SDK.aar för att skapa en modul för vår .AAR. Högerklicka på den modul eller de moduler som innehåller din appkod och gå till **Modulinställningar** > **fliken Beroenden** > **+-ikonen** > **Modulberoende** > Välj den MAM SDK AAR-modul som du precis skapat > **OK**. På så sätt kan du vara säker på att modulen kompileras med MAM SDK när du skapar ditt projekt.

Dessutom kan **Microsoft.Intune.MAM.SDK.Support.XXX.jar**-biblioteken innehålla Intune-varianter av motsvarande `android.support.XXX`-bibliotek. De ingår inte i Microsoft.Intune.MAM.SDK.aar eftersom inte alla appar är beroende av stödbiblioteken.

#### <a name="proguard"></a>ProGuard

Om [ProGuard](http://proguard.sourceforge.net/) (eller någon annan krympande/döljande mekanism) används som ett utvecklingssteg har SDK:n ytterligare konfigurationsregler (MPR) som måste tas med. När du inkluderar .aar i build-versionen läggs reglerna automatiskt till i ProGuard-steget och de nödvändiga klassfilerna bevaras.

Azure ADAL (Active Directory Authentication Libraries) kan ha egna ProGuard-begränsningar. Om din app integrerar ADAL måste du följa ADAL-dokumentationen om dessa begränsningar.

### <a name="build-tooling"></a>Utvecklingsverktyg
Intune App SDK är ett Android-bibliotek som gör att din app stöder och kan tillämpa Intune-principer. Vissa principer kräver [att din app uttryckligen deltar i tillämpningen av principerna](#enable-features-that-require-app-participation), men de flesta tillämpas halvautomatiskt. Den här automatiska tillämpningen kräver att appar ersätter arv från flera Android-basklasser med arv från MAM-motsvarigheter, samt att de på motsvarande sätt ersätter anrop till vissa tjänstklasser för Android-system med anrop till MAM-motsvarigheter. De specifika ersättningar som krävs beskrivs [nedan](#class-and-method-replacements).

Det kan vara tidskrävande att utföra dessa ersättningar manuellt. Därför innehåller SDK:n utvecklingsverktyg (ett plugin-program för Gradle-utveckling och ett kommandoradsverktyg för annan utveckling) som utför ersättningarna automatiskt. Dessa verktyg omvandlar klassfilerna som genereras av Java-kompileringen och ändrar inte den ursprungliga källkoden.

Verktygen utför endast [direkta ersättningar](#class-and-method-replacements). De utför inte mer komplexa SDK-integrationer som [”spara som”-principer](#enable-features-that-require-app-participation), [multiidentitet](#multi-identity-optional), [App-WE-registrering](#app-protection-policy-without-device-enrollment), [AndroidManifest-ändringar](#manifest-replacements) eller [ADAL-konfiguration](#configure-azure-active-directory-authentication-library-adal). Dessa måste därför utföras innan din app är helt Intune-aktiverad. Läs noga igenom resten av den här dokumentationen för integreringsinformation som är relevant för din app.

> [!NOTE]
> Det går bra att köra verktygen för ett projekt som redan helt eller delvis har integrerat MAM SDK via manuella ersättningar. Ditt projekt måste fortfarande lista MAM SDK som ett beroende.

### <a name="gradle-build-plugin"></a>Plugin-program för Gradle-utveckling
Om din app inte utvecklas med gradle går du vidare till [Integrera med kommandoradsverktyget](#command-line-build-tool). 

Plugin-programmet för App SDK distribueras som en del av SDK:n som **GradlePlugin/com.microsoft.intune.mam.build.jar**. För att Gradle ska kunna hitta plugin-programmet måste det läggas till i buildscript-klassökvägen. Plugin-programmet är beroende av [Javassist](http://jboss-javassist.github.io/javassist/), som också måste läggas till. Du lägger till dem i klassökvägen genom att lägga till följande i din rot-`build.gradle`

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

Sedan tillämpar du bara plugin-programmet i `build.gradle`-filen för ditt APK-projekt som
```groovy
apply plugin: 'com.microsoft.intune.mam'
```

Som standard fungerar plugin-programmet **endast** på `project`-beroenden.
Testa att kompileringen inte påverkas. Konfiguration kan anges för att visa
*  Projekt som ska undantas
*  [Externa beroenden som ska tas med](#usage-of-includeexternallibraries) 
*  Särskilda klasser som ska undantas från bearbetning
*  Varianter som ska undantas från bearbetning. Dessa kan referera till ett fullständigt variantnamn eller till en enda variant. Till exempel
     * Om din app har versionstyperna `debug` och `release` med varianterna {`savory`, `sweet`} och {`vanilla`, `chocolate`} kan du ange
     * `savory` för att undanta alla varianter med smaken Savory eller `savoryVanillaRelease` för att undanta endast den exakta varianten.

#### <a name="example-partial-buildgradle"></a>Exempel på partiell build.gradle

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}

```
Detta skulle ha följande effekter:
* `:product:FooLib` skrivs inte om eftersom den ingår i `excludeProjects`
* `:product:foo-project` skrivs om, förutom för `com.contoso.SplashActivity` som ignoreras eftersom den finns i `excludeClasses`
* `bar.jar` skrivs om eftersom den ingår i `includeExternalLibraries`
* `zap.jar` skrivs **inte** om eftersom den inte är ett projekt och inte ingår i `includeExternalLibraries`
* `com.contoso.foo:zap-artifact:1.0.0` skrivs om eftersom den ingår i `includeExternalLibraries`
* `com.microsoft.bar:baz:1.0.0` skrivs om eftersom den ingår i `includeExternalLibraries` via ett jokertecken (`com.microsoft.*`).

#### <a name="usage-of-includeexternallibraries"></a>Användning av includeExternalLibraries

Eftersom plugin-programmet som standard endast fungerar med projektberoenden (som vanligtvis tillhandahålls av funktionen `project()`) måste eventuella beroenden som anges av `fileTree(...)` eller som hämtas från maven eller andra paketkällor (t.ex ”.`com.contoso.bar:baz:1.2.0`”) tillhandahållas till egenskapen `includeExternalLibraries` om MAM-bearbetning av dem krävs enligt de villkor som beskrivs nedan. Jokertecken (”*”) stöds.

När du anger externa beroenden i artefaktformat rekommenderar vi att du utelämnar versionskomponenten i `includeExternalLibraries`-värdet. Om du tar med versionen måste det vara en exakt version. Det går inte att ange dynamiska versioner (t.ex. `1.+`).

Den allmänna regeln för att avgöra om du behöver ta med bibliotek i `includeExternalLibraries` beror på hur du besvarar följande två frågor:
1. Innehåller biblioteket klasser som det finns MAM-motsvarigheter för? Exempel: `Activity`, `Fragment`, `ContentProvider`, `Service` osv.
2. Om Ja, använder din app dessa klasser?

Om du svarar ”Ja” på båda dessa frågor måste du ta med biblioteket i `includeExternalLibraries`. 

| Scenario | Bör det tas med? |
|--|--|
| Du inkluderar ett PDF-visningsbibliotek i din app och använder visningsprogrammet `Activity` när användare visar PDF-filer | Ja |
| Du inkluderar ett HTTP-bibliotek i din app för bättre webbprestanda | Nej |
| Du inkluderar ett bibliotek som React Native som innehåller klasser härledda från `Activity`, `Application` och `Fragment` och använder eller härleder dessa klasser ytterligare i din app | Ja |
| Du inkluderar ett bibliotek som React Native som innehåller klasser härledda från `Activity`, `Application` och `Fragment`, men du använder endast statiska hjälpverktyg eller verktygsklasser | Nej |
| Du inkluderar ett bibliotek som innehåller visningsklasser härledda från `TextView` och använder eller härleder dessa klasser ytterligare i din app | Ja |


#### <a name="dependencies"></a>Beroenden

Gradle-plugin-programmet har ett beroende till [Javassist](http://jboss-javassist.github.io/javassist/), som måste vara tillgängligt för Gradles beroendematchning (se beskrivningarna ovan). Javassist används endast under apputvecklingen när plugin-programmet körs. Ingen Javassist-kod läggs till i din app.

> [!NOTE]
> Du måste använda version 3.0 eller senare av Gradle-plugin-programmet för Android och Gradle 4.1 eller senare.

### <a name="command-line-build-tool"></a>Kommandoradsverktyg
Om du använder Gradle går du vidare till [nästa avsnitt](#class-and-method-replacements).

Kommandoradsverktyget är tillgängligt i `BuildTool`-mappen för SDK:n. Det utför samma funktion som Gradle-plugin-programmet som beskrivs ovan, men kan integreras i anpassade utvecklingssystem eller med andra utvecklingssystem än Gradle. Eftersom det är mer allmänt är det mer komplext att anropa. Därför bör Gradle-plugin-programmet användas när det är möjligt.

#### <a name="using-the-command-line-tool"></a>Använda kommandoradsverktyget

Kommandoradsverktyget kan anropas med hjälp av hjälpskripten som finns i katalogen `BuildTool\bin`.

Verktyget förväntar sig följande parametrar.
| Parameter | Beskrivning |
| -- | -- |
| `--input` | En semikolonavgränsad lista över JAR-filer och JAR-kataloger med klassfiler som ska ändra. Detta bör omfatta alla JAR-filer och JAR-kataloger som du planerar att skriva om. |
| `--output` | En semikolonavgränsad lista över JAR-filer och JAR-kataloger som de ändrade klasserna ska sparas i. Det bör finnas en utdatapost per indatapost och de bör visas i ordning. |
| `--classpath` | Klassökvägen för versionen. Detta kan innehålla både JAR-filer och klasskataloger. |
| `--excludeClasses`| En semikolonavgränsad lista som innehåller namnen på de klasser som ska undantas från omskrivning. |

Alla parametrar är obligatoriska förutom för `--excludeClasses` som är valfritt.

#### <a name="example-command-line-tool-invocation"></a>Exempelanrop med kommandoradsverktyget

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

Detta skulle ha följande effekter:

* `product-foo-project`-katalogen skrivs om till `mam-build\product-foo-project`
* `bar.jar` skrivs om till `mam-build\libs\bar.jar`
* `zap.jar` skrivs **inte** om eftersom den endast visas i `--classpath`
* `com.contoso.SplashActivity`-klassen skrivs **inte** om även om den finns i `--input`

> [!NOTE] 
> Utvecklingsverktyget stöder för närvarande inte AAR-filer. Om ditt utvecklingssystem inte redan extraherar `classes.jar` när AAR-filer hanteras, måste du göra det innan du anropar utvecklingsverktyget.


## <a name="class-and-method-replacements"></a>Klass- och metodersättningar

Android-basklasser måste ersättas med deras respektive MAM-motsvarigheter för att aktivera Intune-hantering. SDK-klasserna finns mellan Android-basklassen och appens egen härledda version av den klassen. Exempelvis kan en appaktivitet få en arvshierarki som ser ut så här: `Activity` > `MAMActivity` >
`AppSpecificActivity`. MAM-lagret filtrerar anrop till systemåtgärder för att ge din app en sömlös och heltäckande hanterad vy.

Förutom basklasserna har vissa klasser som din app kanske använder utan härledning (t.ex. `MediaPlayer`) obligatoriska MAM-motsvarigheter, och [vissa metodanrop måste också ersättas](#wrapped-system-services). Mer information finns nedan.

Alla ersättningar som beskrivs i det här avsnittet kan genomföras automatiskt av SDK-[utvecklingsverktyget](#build-tooling). 



| Android-basklass | Intune App SDK-motsvarighet |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent (se [Väntande avsikt](#pendingintent)) |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder (krävs endast om Binder inte genereras från ett AIDL-gränssnitt (Android Interface Definition Language)) |
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.CheckedTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> Även om programmet inte har behov av en egen härledd `Application` klass, [ se `MAMApplication` nedan](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar:

| Android-klass | Intune App SDK-motsvarighet |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar:

|Android-klass | Intune App SDK-motsvarighet |
|--|--|
|android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Android-klass | Intune App SDK-motsvarighet |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Android-klass | Intune App SDK-motsvarighet |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>Nytt namn på metoder
I många fall har en metod som är tillgänglig i Android-klassen markerats som slutgiltig i MAM-ersättningsklassen. I detta fall tillhandahåller MAM-ersättningsklassen en metod med liknande namn (med suffixet `MAM`) som ska åsidosättas i stället. Om du härleder från `MAMActivity`, i stället för att åsidosätta `onCreate()` och anropa `super.onCreate()`, måste `Activity` åsidosätta `onMAMCreate()` och anropa `super.onMAMCreate()`. Java-kompilatorn ska framtvinga de slutliga begränsningarna för att förhindra oavsiktlig åsidosättning av den ursprungliga metoden i stället för motsvarande MAM.

### <a name="mamapplication"></a>MAMApplication
Om din app skapar en underklass av `android.app.Application` så **måste** du skapa en underklass av `com.microsoft.intune.mam.client.app.MAMApplication` i stället. Om din app inte skapar `android.app.Application` som en underklass **måste** du ange `"com.microsoft.intune.mam.client.app.MAMApplication"` som `"android:name"`-attribut i taggen `<application>` i AndroidManifest.xml.
### <a name="pendingintent"></a>PendingIntent
I stället för `PendingIntent.get*` måste du använda `MAMPendingIntent.get*`-metoden. Därefter kan du använda resulterande `PendingIntent` som vanligt.

### <a name="wrapped-system-services"></a>Adaptersystemtjänster
För vissa systemtjänstklasser är det nödvändigt att anropa en statisk metod för en MAM-adapterklass i stället för att direkt anropa den önskade metoden för tjänstinstansen. Till exempel måste ett anrop till `getSystemService(ClipboardManager.class).getPrimaryClip()` bli ett anrop till `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)`. Vi rekommenderar att du inte gör dessa ersättningar manuellt. Låt BuildPlugin göra dem i stället.

| Android-klass | Intune App SDK-motsvarighet |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
### <a name="manifest-replacements"></a>Manifestersättningar
Det kan vara nödvändigt att utföra några av ovanstående klassersättningar i manifestet och i Java-koden. Observera särskilt:
* Manifestreferenser till `android.support.v4.content.FileProvider` måste ersättas med `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.

## <a name="androidx-libraries"></a>AndroidX-bibliotek
Med Android P lanserade Google en ny uppsättning (omdöpt) stödbibliotek med namnet AndroidX, och version 28 är den senaste större utgåvan av de befintliga android.support-biblioteken.

Till skillnad från Android-stödbiblioteken tillhandahåller inte vi några MAM-varianter av AndroidX-biblioteken. I stället bör AndroidX behandlas som andra externa bibliotek och konfigureras för att skrivas om med plugin-programmet eller kommandoradsverktyget. För Gradle kan detta göras genom att `androidx.*` läggs till i fältet `includeExternalLibraries` i plugin-programmets konfigurationsfil. Anrop med kommandoradsverktyget måste uttryckligen lista alla JAR-filer.
## <a name="sdk-permissions"></a>SDK-behörigheter

Intune App SDK kräver tre [Android-systembehörigheter](https://developer.android.com/guide/topics/security/permissions.html) för apparna som integrerar det:

* `android.permission.GET_ACCOUNTS` (begärs vid behov vid körning)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

Dessa behörigheter krävs av Azures autentiseringsbibliotek för Active Directory ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) för att kunna utföra asynkron autentisering. Om dessa behörigheter inte beviljas till appen eller om de återkallas av användaren så inaktiveras autentiseringsflöden som kräver koordinering (av företagsportalappen).

## <a name="logging"></a>Loggning

Loggning ska initieras tidigt för att få ut det mesta från loggade data. `Application.onMAMCreate()` är vanligtvis den bästa platsen för att initiera loggning.

Ta emot MAM-loggar i din app genom att skapa en [Java-hanterare](http://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) och lägg till den i `MAMLogHandlerWrapper`. Detta anropar `publish()` i programhanteraren för varje loggmeddelande.

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```



## <a name="enable-features-that-require-app-participation"></a>Aktivera funktioner som kräver appmedverkan

Det finns flera appskyddsprinciper som SDK inte kan implementera själv. Appen kan styra sitt beteende och använda dessa funktioner med hjälp av flera API:er som du hittar i följande `AppPolicy`-gränssnitt. För att hämta en `AppPolicy`-instans använder du `MAMPolicyManager.getPolicy`.

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * This function is now deprecated. Please use getIsSaveToLocationAllowed(SaveLocation, String) instead
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 *
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 *
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether
 * file encryption is in use. File encryption is transparent to the app, and the app should not need
 * to make any business logic decisions based on this.
 * 
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}
```

> [!NOTE]
> `MAMPolicyManager.getPolicy` returnerar alltid en apprincip som inte är null, även om enheten eller appen inte hanteras av en Intune-hanteringsprincip.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Exempel: Bestäm om en PIN-kod ska krävas för appen

Om appen har en egen PIN-kod för användaren kan du inaktivera detta, om IT-administratören har konfigurerat att SDK:n ska fråga efter appens PIN-kod. Anropa följande metod för att se om IT-administratören har distribuerat appens PIN-princip till den här appen för den aktuella användaren:

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Exempel: Fastställa den primära Intune-användaren

Förutom de API:er som exponeras i AppPolicy, visas också användarens huvudnamn (**UPN**) även av den `getPrimaryUser()` API som definierats i `MAMUserInfo`-gränssnittet. Hämta användarens huvudnamn genom att anropa följande:

```java
MAMUserInfo info = MAMComponents.get(MAMUserInfo.class);
if (info != null) return info.getPrimaryUser();
```

Den fullständiga definitionen av MAMUserInfo-gränssnittet nedan:

```java
/**
 * External facing user informations.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if the device is not enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Exempel: Bestäm om det ska vara tillåtet att spara till enheten eller lagra i molnet

Många appar implementerar funktioner som gör att slutanvändaren kan spara filer lokalt eller till en molnlagringstjänst. Med Intune App SDK kan IT-administratörer skydda mot dataläckage genom att tillämpa principbegränsningar som passar behoven i deras organisation.  En av principerna som IT kan kontrollera är huruvida användaren kan spara filer i ett ”personligt”, ohanterat datalager. Användaren kan i så fall till exempel spara till en lokal plats, ett SD-kort eller i säkerhetskopieringstjänster från tredje part.

**Appens medverkan krävs för att aktivera funktionen.** Om din app tillåter att användaren sparar filer på personliga eller molnbaserade platser direkt från appen måste du implementera den här funktionen så att IT-administratören kan styra huruvida det går att spara eller inte på en viss plats. Med API:et nedan kan appen kontrollera om Intune-administratörens princip tillåter att användaren sparar till ett personligt arkiv. Appen kan sedan framtvinga tillämpningen av principen eftersom den vet vilket personligt datalager som är tillgängligt för slutanvändaren via appen.  

Gör följande anrop för att se om principen tillämpas:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

... där `service` är en av följande SaveLocations:


    * SaveLocation.ONEDRIVE_FOR_BUSINESS
    * SaveLocation.LOCAL
    * SaveLocation.SHAREPOINT

Den tidigare metoden att bestämma om en användarprincip tillät dem att spara data till olika platser, var `getIsSaveToPersonalAllowed()` inom samma **AppPolicy**-klass. Den här funktionen är nu **inaktuell** och bör inte användas. Följande anrop motsvarar `getIsSaveToPersonalAllowed()`:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> Använd `SaveLocation.OTHER` om den aktuella platsen inte visas i **SaveLocations**-uppräkningen.


## <a name="register-for-notifications-from-the-sdk"></a>Registrera för meddelanden från SDK:n

### <a name="overview"></a>Översikt
Din app kan använda Intune App SDK till att styra beteendet för vissa principer, till exempel en selektiv rensning, när de har distribuerats av IT-administratören. När en IT-administratör distribuerar den här typen av princip skickar Intune-tjänsten ett meddelande till SDK.

Appen måste först registreras för meddelanden från SDK:n genom att skapa en `MAMNotificationReceiver` och registrera den med `MAMNotificationReceiverRegistry`. Du gör detta genom att ange mottagaren och typen av meddelande i  `App.onCreate`, vilket illustreras i exemplet nedan:

```java
@Override
public void onCreate() {
  super.onCreate();
  MAMComponents.get(MAMNotificationReceiverRegistry.class)
    .registerReceiver(
      new ToastNotificationReceiver(),
      MAMNotificationType.WIPE_USER_DATA);
  }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

`MAMNotificationReceiver`-gränssnittet tar bara emot meddelanden från Intune-tjänsten. Vissa meddelanden hanteras av SDK direkt, medan andra kräver appens medverkan. En app **måste** returnera true eller false från ett meddelande. Den måste alltid returnera true förutom om en åtgärd som den försökte utföra till följd av meddelandet misslyckas.

* Det här felet kan rapporteras till Intune-tjänsten. Ett exempel på ett scenario som bör rapporteras är om appen inte kan rensa användardata när IT-administratören har initierat en rensning.

>[!NOTE]
> Det är säkert att blockera i `MAMNotificationReceiver.onReceive` eftersom dess motanrop inte körs i UI-tråden.

`MAMNotificationReceiver`-gränssnittet som definieras i SDK finns nedan:

```java
/**
 * The SDK is signaling that a MAM event has occurred.
 *
 */
public interface MAMNotificationReceiver {

    /**
     * A notification was received.
     *
     * @param notification
     *            The notification that was received.
     * @return The receiver should return true if it handled the
     *   notification without error (or if it decided to ignore the
     *   notification). If the receiver tried to take some action in
     *   response to the notification but failed to complete that
     *   action it should return false.
     */
    boolean onReceive(MAMNotification notification);
}
```

### <a name="types-of-notifications"></a>Typer av meddelanden

Följande meddelanden skickas till appen och några av dem kan kräva appens medverkan:

* **WIPE_USER_DATA**: Det här meddelandet skickas i en `MAMUserNotification`-klass. När meddelandet tas emot förväntas appen ta bort alla data som är associerade med företagsidentiteten som skickades med `MAMUserNotification`. För närvarande skickas det här meddelandet när APP-WE-tjänsten avregistreras. Användarens primära namn anges normalt under registreringen. Om du registrerar dig för det här meddelandet måste appen kontrollera att alla användarens data har tagits bort. Om du inte registrerar dig för det här meddelandet utförs det fördefinierade beteendet för selektiv rensning.

* **WIPE_USER_AUXILIARY_DATA**: Appar kan registreras för det här meddelandet om man vill att Intune App SDK ska utföra standardbeteendet för selektiv rensning, men dessutom vill ta bort vissa ytterligare data när rensningen utförs. Det här meddelandet skickas inte till appar med en enda identitet. Det skickas endast till appar med flera identiteter.

* **REFRESH_POLICY**: Det här meddelandet skickas i en `MAMUserNotification`. När det här meddelandet tas emot måste cachelagrade Intune-principer ogiltigförklaras och uppdateras. Detta hanteras vanligtvis av SDK, men bör hanteras av appen om principen används permanent.

* **MANAGEMENT_REMOVED**: Det här meddelandet skickas i en `MAMUserNotification` och informerar appen att den håller på att blir ohanterad. När den är ohanterad kommer den inte längre kunna läsa krypterade filer, läsa data som krypterats med MAMDataProtectionManager, interagera med krypterade urklipp eller på annat sätt delta i ekosystemet för hanterade appar.


> [!NOTE]
> Observera att en app aldrig ska registreras för både `WIPE_USER_DATA`- och `WIPE_USER_AUXILIARY_DATA`-meddelanden.


## <a name="configure-azure-active-directory-authentication-library-adal"></a>Konfigurera Azure Active Directory Authentication Library (ADAL)

Läs först riktlinjerna för ADAL-integrering som finns på [ADAL- lagringsplatsen på GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-android).

SDK använder [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) för [autentisering](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) och villkorsstyrda startscenarier som kräver att apparna är konfigurerade med [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). Konfigurationsvärdena förmedlas till SDK via AndroidManifest-metadata.

Om du vill konfigurera din app och aktivera lämplig autentisering, lägger du till följande till appnoden i AndroidManifest.xml. Vissa av de här konfigurationerna krävs endast om din app använder ADAL generellt för autentisering. I så fall behöver du de specifika värden som din app använder för att registrera sig med AAD. Avsikten med detta är att användaren inte ska uppmanas att autentisera sig två gånger på grund av att AAD upptäcker två separata registreringsvärden: en från appen och en från SDK:n.

```xml
<meta-data
    android:name="com.microsoft.intune.mam.aad.Authority"
    android:value="https://AAD authority/" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.ClientID"
    android:value="your-client-ID-GUID" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
    android:value="your-redirect-URI" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.SkipBroker"
    android:value="[true | false]" />
```

### <a name="adal-metadata"></a>ADAL-metadata

* **Authority** är den AAD-auktoritet som används. Om det här värdet saknas används den offentliga AAD-miljön.
> [!NOTE]
> Ange inte det här fältet om ditt program har koppling till nationella moln.

* **ClientID** är det AAD-ClientID som ska användas. Du bör använda din egen apps ClientID, om det är registrerat i Azure AD. Om detta värde saknas används ett Intune-standardvärde.

* **NonBrokerRedirectURI** är AAD:ns omdirigerings-URI som används när det inte finns någon asynkron meddelandekö. Om inget anges används standardvärdet för `urn:ietf:wg:oauth:2.0:oob`. Standardinställningen är lämplig för de flesta appar.

* **SkipBroker** används om ClientID inte har konfigurerats till att använda omdirigerings-URI:n för den asynkrona meddelandekön. Standardvärdet är ”false”.
    * För appar som **inte integrerar ADAL** och **inte vill delta i enhetsomfattande asynkron autentisering/enkel inloggning**, bör detta vara inställt på ”true”. När det här värdet är ”true”, är den enda omdirigerings-URI som används NonBrokerRedirectURI.

    * För appar som stöder enhetsomfattande enkel inloggning ska detta vara ”false”. När värdet är ”false” väljer SDK:n en asynkron meddelandekö mellan resultatet av [`com.microsoft.aad.adal.AuthenticationContext.getRedirectUriForBroker()`](https://github.com/AzureAD/azure-activedirectory-library-for-android) och NonBrokerRedirectURI, baserat på tillgängligheten för den asynkrona meddelandekön i systemet. I allmänhet blir den asynkrona meddelandekön tillgänglig från företagsportalappen eller Azure Authenticator-appen.

### <a name="common-adal-configurations"></a>Vanliga ADAL-konfigurationer

Nedan visas några vanliga sätt att konfigurera en app med ADAL. Hitta din appkonfiguration och ange ADAL-metadataparametrarna (förklaras ovan) till de värden som krävs. Om du vill kan du i samtliga fall ange auktoriteten för icke-förvalda miljöer, men normalt behövs det inte.

1. **Appen integrerar inte ADAL:**

Inga ytterligare manifestvärden behöver konfigureras.

2. **Appen integrerar ADAL:**

    |ADAL-parameter som krävs| Värde |
    |--|--|
    | ClientID | Appens ClientID (genereras av Azure AD när appen registreras) |
    | SkipBroker | Falskt |

Authority och NonBrokerRedirectURI kan anges om det behövs.

Registrera din app med Azure AD med hjälp av följande steg.

På Azure-portalen:
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

Information om hur du registrerar ett program med Azure AD finns [här](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications). 

Se även kraven för [villkorlig åtkomst](#conditional-access) nedan.

3. **Appen integrerar ADAL, men saknar stöd för asynkron autentisering/enhetsomfattande enkel inloggning:**

    |ADAL-parameter som krävs| Värde |
    |--|--|
    | ClientID | Appens ClientID (genereras av Azure AD när appen registreras) |
    | SkipBroker | **True** |
    
    Authority och NonBrokerRedirectURI kan anges om det behövs.


### <a name="conditional-access"></a>Villkorlig åtkomst
Villkorlig åtkomst (CA) är en [funktion](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer) i Azure Active Directory som kan användas för att kontrollera åtkomsten till AAD-resurser.  [Intune-administratörer kan definiera regler för villkorlig åtkomst](https://docs.microsoft.com/intune/conditional-access) som endast tillåter åtkomst till resurser från enheter eller appar som hanteras av Intune. Följ stegen nedan för att säkerställa att din app kan komma åt resurser när det behövs. Om din app inte använder AAD-åtkomsttoken, eller om den endast kommer åt resurser som inte kan skyddas med villkorlig åtkomst (CA), kan du hoppa över de här stegen.
1. Följ [riktlinjerna för ADAL-integration](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library). 
   Se särskilt steg 11 för Broker-användning.

2. [Registrera ditt program med Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). Omdirigerings-URI finns i riktlinjerna för ADAL-integrering ovan.

3. Ange manifestets metadataparametrar enligt informationen under punkt 2 i avsnittet [Vanliga ADAL-konfigurationer](#common-adal-configurations) ovan.

4. Testa att allt är korrekt konfigurerat genom att aktivera [enhetsbaserad villkorlig åtkomst](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) på [Azure-portalen](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2) och bekräfta
* att inloggningen i appen begär installation och registrering av Intune-företagsportalen
* att inloggningen i appen fungerar korrekt efter registreringen.

5. När appen har skickat Intune APP SDK-integrering till produktion kontaktar du msintuneappsdk@microsoft.com så lägger vi till din app i listan med godkända appar för [appbaserad villkorlig åtkomst](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access).

6. När din app har lagts till i listan med godkända appar bekräftar du detta genom att [konfigurera appbaserad villkorlig åtkomst](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create) och kontrollera att inloggningen till din app fungerar korrekt.


## <a name="app-protection-policy-without-device-enrollment"></a>Appskyddsprincip utan enhetsregistrering

### <a name="overview"></a>Översikt
Med Intunes appskyddsprincip utan enhetsregistrering, så kallad APP-WE eller MAM-WE, kan appar hanteras av Intune utan att enheten behöver registreras i Intune MDM. APP-WE fungerar med eller utan enhetsregistrering. Företagsportalen måste fortfarande installeras på enheten, men användaren behöver inte logga in på företagsportalen och registrera enheten.

> [!NOTE]
> Alla appar måste ha stöd för appskyddsprincipen utan enhetsregistrering.

### <a name="workflow"></a>Arbetsflöde

När en app skapar ett nytt användarkonto, bör den registrera kontot för hantering med Intune App SDK. SDK:n hanterar information om registrering av appen i APP-WE-tjänsten. Om det behövs kommer den att försöka med alla registreringar på nytt med lämpliga tidsintervall om fel inträffar.

Appen kan också fråga Intune App SDK om status för en registrerad användare för att avgöra om användaren ska blockeras från åtkomst till företagets innehåll. Flera konton kan registreras för hantering, men för närvarande kan endast ett konto i taget registreras aktivt med APP-WE-tjänsten. Det innebär att endast ett konto i taget kan ta emot appskyddsprincipen i appen.

Appen krävs för att kunna göra en motringning och hämta lämplig åtkomsttoken från Azure ADAL (Active Directory Authentication Library) åt SDK:n. Det förutsätts att appen redan använder ADAL för användarautentisering och för att kunna hämta sina egna åtkomsttokens.

När appen tar bort ett konto helt, bör kontot avregistreras för att visa att appen inte längre ska tillämpa principen för den användaren. Om användaren har registrerats i MAM-tjänsten, kommer användaren att avregistreras och appen kommer att rensas.


### <a name="overview-of-app-requirements"></a>Översikt över appkrav

För att kunna implementera APP-WE-integrationen, måste din app registrera användarkontot med MAM SDK:

1. Appen _måste_ implementera och registrera en instans av `MAMServiceAuthenticationCallback`-gränssnittet. Motringningsinstansen ska registreras så snart som möjligt i appens livscykel (vanligtvis i `onMAMCreate()`-metoden i programklassen).

2. När ett användarkonto skapas och användaren har loggat in med ADAL _måste_ appen anropa `registerAccountForMAM()`.

3. När ett användarkonto tas bort helt, ska appen anropa `unregisterAccountForMAM()` för att ta bort kontot från Intune-hanteringen.

    > [!NOTE]
    > Om en användare loggar ut från appen tillfälligt, behöver appen inte anropa `unregisterAccountForMAM()`. Anropet kan starta en rensning för att ta bort samtliga företagsdata för användaren.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

Alla nödvändiga autentiserings- och registrerings-API:er finns i `MAMEnrollmentManager`-gränssnittet. En referens till `MAMEnrollmentManager` kan hämtas på följande sätt:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

Den returnerade `MAMEnrollmentManager`-instansen kommer garanterat inte vara null. API-metoderna är indelade i två kategorier: **autentisering** och **kontoregistrering**.

> [!NOTE]
> `MAMEnrollmentManager` innehåller vissa API-metoder som snart kommer att vara inaktuella. Endast de relevanta metoderna och resultatkoderna visas i kodblocket nedan.

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>Kontoautentisering

I det här avsnittet beskrivs autentiseringens API-metoder i `MAMEnrollmentManager` och hur de används.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. Appen måste implementera `MAMServiceAuthenticationCallback`-gränssnittet för att tillåta SDK att begära en ADAL-token för angiven användare och resurs-ID. Motringningsinstansen måste anges för `MAMEnrollmentManager` genom att anropa dess `registerAuthenticationCallback()`-metod. En token kan behövas mycket tidigt i appens livscykel för registreringsåterförsök eller uppdatering av incheckningar till appens skyddsprincip, så det bästa stället att registrera motringningen är i `onMAMCreate()`-metoden för appens `MAMApplication`-underklass.

2. `acquireToken()`-metoden ska hämta åtkomsttoken för begärd resurs-ID för den angivna användaren. Om det inte går att hämta begärd token returnerar den null.

3. Om appen inte kan ange en token när SDK anropar `acquireToken()` – till exempel om tyst autentisering misslyckas och det är olämpligt att visa ett UI – kan appen hämta en token vid ett senare tillfälle genom att anropa `updateToken()`-metoden. Samma UPN, AAD-ID och resurs-ID som begärdes av föregående anrop till `acquireToken()` måste skickas till `updateToken()`, tillsammans med den token som slutligen anskaffades. Appen ska anropa den här metoden så snart som möjligt efter att ha returnerat null från motringningen.

> [!NOTE]
> SDK:n anropar `acquireToken()` regelbundet för att hämta denna token, så att anropa `updateToken()` är inte nödvändigt. Det rekommenderas dock som hjälp vid registreringar och incheckningar till appskyddsprincipen för att de ska slutföras inom rimlig tid.


### <a name="account-registration"></a>Kontoregistrering

I det här avsnittet beskrivs kontoregistreringens API-metoder i `MAMEnrollmentManager` och hur de används.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Om du vill registrera ett hanteringskonto ska appen anropa `registerAccountForMAM()`. Ett användarkonto identifieras av både sitt UPN och sitt användar-ID för AAD. Klient-ID krävs dessutom för att associera registreringsdata med användarens AAD-klient. Användarens behörighet kan även anges för att tillåta registrering mot specifika nationella moln. Mer information finns i avsnittet [Registrering av nationella moln](#sovereign-cloud-registration).  SDK kan försöka registrera appen för angiven användare i MAM-tjänsten. Om registreringen misslyckas görs nya försök regelbundet tills kontot är avregistrerat. Återförsöksperioden är vanligtvis 12–24 timmar. SDK:n innehåller statusen för registreringsförsöken via meddelanden asynkront.

2. Eftersom AAD-autentisering krävs, är den bästa tiden att registrera användarkontot när användaren har loggat in i appen och har autentiserats med hjälp av ADAL.
    * Användarens AAD-ID och klient-ID returneras från ADAL-autentiseringens anrop som en del av [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android)-objektet. Klientens ID kommer från `AuthenticationResult.getTenantID()`-metoden.
    * Information om användaren finns i ett underobjekt av typen `UserInfo` som kommer från `AuthenticationResult.getUserInfo()`, och AAD-användarens ID hämtas från detta objekt genom att anropa `UserInfo.getUserId()`.

3. Om du vill avregistrera ett konto från Intune-hanteringen, ska appen anropa `unregisterAccountForMAM()`. Om kontot har registrerats och hanteras, avregistrerar SDK:n kontot och rensar dess data. Regelbundna återförsök att registrera kontot kommer att stoppas. SDK:n innehåller statusen för avregistreringsbegärandet via meddelanden asynkront.

### <a name="sovereign-cloud-registration"></a>Registrering av nationella moln

Program som är [kopplade till nationella moln](https://www.microsoft.com/en-us/trustcenter/cloudservices/nationalcloud) **måste** ange `authority` till `registerAccountForMAM()`.  Det gör du genom att ange `instance_aware=true` i ADAL:s [1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) acquireToken extraQueryParameters följt av ett anrop till `getAuthority()` på AuthenticationCallback AuthenticationResult.

```
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> Ange inte AndroidManifest.xml-metadataauktoriteten.
<br/>
```
<meta-data
    android:name="com.microsoft.intune.mam.aad.Authority"
    android:value="https://AAD authority/" />
```

> [!NOTE]
> Kontrollera att auktoriteten har angetts korrekt i `MAMServiceAuthenticationCallback::acquireToken()`-metoden.


#### <a name="currently-supported-sovereign-clouds"></a>Nationella moln som stöds för närvarande

1. Arlington

### <a name="important-implementation-notes"></a>Viktiga implementeringskommentarer

#### <a name="authentication"></a>Autentisering

* När appen anropar `registerAccountForMAM()` kan den få en motringning till sitt `MAMServiceAuthenticationCallback`-gränssnitt strax därefter i en annan tråd. Vi rekommenderar att appen hämtar sin egen token från ADAL innan kontot registreras för att påskynda hämtningen av en **MAMService-token**. Om appen returnerar en giltig token från motringningen, fortsätter registreringen och appen får slutresultatet via ett meddelande.

* Om programmet inte returnerar en giltig AAD-token, blir slutresultatet från registreringsförsöket `AUTHENTICATION_NEEDED`. Om appen tar emot resultatet via ett meddelande, kan den påskynda registreringen genom att skaffa en **MAMService-token** och anropa `updateToken()`-metoden för att starta registreringen på nytt. Detta är _inte_ ett absolut krav, men eftersom SDK:n försöker att registrera med jämna mellanrum och anropar motringningen krävs denna token.

* Appens registrerade `MAMServiceAuthenticationCallback` anropas också för att hämta en token för uppdateringen av regelbundna incheckningar till appskyddsprincipen. Om appen inte kan erbjuda en token vid begäran, kommer den inte att få något meddelande. Den bör dock försöka att hämta en token och anropa `updateToken()` vid nästa tillfälle för att påskynda incheckningen. Om det inte finns någon token, anropas motringningen fortfarande vid nästa incheckningsförsök.

* Stöd för nationella moln kräver att auktoriteten anges.
#### <a name="registration"></a>Registrering

* Metoderna för registreringen är idempotenta. Det innebär exempelvis att `registerAccountForMAM()` endast kommer att registrera ett konto och försöka registrera appen om kontot inte är redan registrerat, och `unregisterAccountForMAM()` kommer bara att avregistrera ett konto om det är registrerat. Efterföljande anrop blir inte några åtgärder, så det gör inget om man anropar metoderna mer än en gång. Förhållandet mellan anrop till dessa metoder och meddelanden om resultat är inte garanterat: dvs. om `registerAccountForMAM` anropas för en identitet som redan har registrerats, kommer meddelandet kanske inte att skickas igen för den identiteten. Det är möjligt att meddelanden skickas som inte motsvarar något anrop till dessa metoder, eftersom SDK:n regelbundet kan försöka registrera i bakgrunden och avregistreringar kan utlösas av rensningsbegäranden från Intune-tjänsten.

* Registreringsmetoderna kan anropas för valfritt antal olika identiteter, men för närvarande kan bara ett användarkonto registreras. Om flera användarkonton som har licens för Intune och ska ha appskyddsprincipen har registrerats samtidigt, går det inte att förutse vilket konto som ”vinner”.

* Slutligen kan du söka i `MAMEnrollmentManager` för att se om ett visst konto har registrerats och för att få dess aktuella status med hjälp av `getRegisteredAccountStatus`-metoden. Om det angivna kontot inte är registrerat, returnerar den här metoden **null**. Om kontot är registrerat, returnerar den här metoden kontots status som en av medlemmarna i `MAMEnrollmentManager.Result`-uppräkningen.

### <a name="result-and-status-codes"></a>Resultat och statuskoder

När ett konto registreras första gången är det i ett `PENDING`-tillstånd, vilket visar att det första registreringsförsöket för MAM-tjänsten är ofullständigt. När registreringsförsöket är klart, skickas ett meddelande med en av resultatkoderna i tabellen nedan. Dessutom returnerar `getRegisteredAccountStatus()`-metoden kontots status för att appen alltid ska kunna se om åtkomst till företagets innehåll har blockerats för användaren. Om registreringen misslyckas kan kontots status ändras efter ett tag, eftersom SDK:n gör nya försök att registrera i bakgrunden.

|Resultatkod | Förklaring |
| -- | -- |
|AUTHORIZATION_NEEDED | Resultatet visar att någon token inte angavs av appens registrerade `MAMServiceAuthenticationCallback`-instans eller att angiven token var ogiltig.  Appen ska hämta en giltig token och anropa `updateToken()` om möjligt. |
| NOT_LICENSED | Användaren är inte licensierad för Intune, eller det gick inte att kontakta Intune MAM-tjänsten.  Appen ska fortsätta i ett ohanterat (normalt) tillstånd och användaren ska inte blockeras.  Registreringar görs regelbundet för att se om användaren blir licensierad i framtiden. |
| ENROLLMENT_SUCCEEDED | Registreringen är klar, eller användaren är redan registrerad.  Om det registreringen lyckades skickas ett principuppdateringsmeddelande före det här meddelandet.  Åtkomst till företagets data ska tillåtas. |
| ENROLLMENT_FAILED | Registreringen misslyckades.  Mer information finns i loggarna för enheten.  Appen bör inte tillåta åtkomst till företaget i det här tillståndet, eftersom det tidigare har fastställts att användaren är licensierad för Intune.|
| WRONG_USER | Bara en användare per enhet kan registrera en app med MAM-tjänsten.  För att kunna registrera som en annan användare, måste registreringen för alla appar tas bort först.  Annars måste den här appen registreras som den primära användaren.  Den här kontrollen inträffar efter licenskontrollen, så användaren ska blockeras från att komma åt företagets data tills appen har registrerats.|
| UNENROLLMENT_SUCCEEDED | Avregistreringen har slutförts.|
| UNENROLLMENT_FAILED | Avregistreringen misslyckades.  Mer information finns i loggarna för enheten. |
| PENDING | Det första registreringsförsöket för användaren pågår.  Appen kan blockera åtkomst till företagets data tills registreringsresultatet är känt, men måste inte göra detta. |
| COMPANY_PORTAL_REQUIRED | Användaren är licensierad för Intune, men appen kan inte registreras förrän företagsportalappen är installerad på enheten. Intune App SDK kommer att försöka blockera åtkomst till appen för användarna och uppmana dem att installera företagsportalappen (se nedan för information). |


### <a name="company-portal-requirement-prompt-override-optional"></a>Åsidosätt uppmaning om krav på företagsportal (valfritt)

Om ett `COMPANY_PORTAL_REQUIRED`-resultat tas emot, blockerar SDK:n användningen av aktiviteter med den identitet för vilken registrering begärdes. I stället kommer SDK:n göra så att dessa aktiviteter visar en uppmaning om att ladda ned företagsportalen. Om du vill förhindra detta i din app, kan aktiviteterna implementera `MAMActivity.onMAMCompanyPortalRequired`.

Den här metoden anropas innan SDK:n visar sitt standardblockerings-UI. Om appen ändrar aktivitetsidentitet eller avregistrerar den användare som försökte registrera, blockeras inte aktiviteten av SDK:n. I det här fallet är det upp till appen att undvika att företagets data sprids. Observera att endast appar med flera identiteter (beskrivs senare) kan ändra aktivitetsidentiteten.

Om du inte uttryckligen ärver `MAMActivity` (eftersom utvecklingsverktyget ändrar det), men fortfarande behöver hantera det här meddelandet kan du i stället implementera `MAMActivityBlockingListener`.

### <a name="notifications"></a>Meddelanden

En ny typ av `MAMNotification` har lagts till för att informera appen om att registreringsbegärandet har slutförts.  `MAMEnrollmentNotification` tas emot via `MAMNotificationReceiver`-gränssnittet enligt beskrivningen i avsnittet [Registrera för meddelanden från SDK:n](#register-for-notifications-from-the-sdk).

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

`getEnrollmentResult()`-metoden returnerar resultatet av registreringsbegäran.  Eftersom `MAMEnrollmentNotification` utökar `MAMUserNotification`, är identiteten för den användare som registreringen gjordes för också tillgänglig. Appen måste implementera `MAMNotificationReceiver`-gränssnittet för att kunna ta emot dessa meddelanden, enligt beskrivningen i [Registrera för meddelanden från SDK:n](#register-for-notifications-from-the-sdk).

Den registrerade användarens kontostatus kan ändras när ett registreringsmeddelande tas emot, men den ändras inte i vissa fall (t.ex. om `AUTHORIZATION_NEEDED` har tagits emot efter ett mer informativt resultat som `WRONG_USER`, kommer fler informativa resultat att behållas som kontots status)


## <a name="protecting-backup-data"></a>Skydda säkerhetskopierade data

Från och med Android Marshmallow (API-23) kan en app säkerhetskopiera data på två sätt. Alla alternativ är tillgängliga för din app och kräver olika steg för att säkerställa att Intune-dataskyddet har implementerats korrekt. Tabellen nedan innehåller information om relevanta åtgärder som krävs för korrekt dataskydd.  Du kan läsa mer om säkerhetskopieringsmetoderna i [Android API-guiden](http://developer.android.com/guide/topics/data/backup.html).

### <a name="auto-backup-for-apps"></a>Automatisk säkerhetskopiering för appar

Android har börjat erbjuda [automatiska fullständiga säkerhetskopieringar](https://developer.android.com/guide/topics/data/autobackup.html) av appar på Google Drive på Android Marshmallow-enheter, oavsett appens mål-API. Om du uttryckligen anger `android:allowBackup` till **false** i AndroidManifest.xml placeras din app aldrig i kö för säkerhetskopiering av Android och ”företagsdata” bevaras i appen. Ingen ytterligare åtgärd krävs i detta fall.

Som standard har attributet `android:allowBackup` dock värdet true, även om `android:allowBackup` inte har angetts i manifestfilen. Detta innebär att alla appdata säkerhetskopieras automatiskt till användarens Google Drive-konto, ett standardbeteende som medför **risk för dataläckage**. Därför kräver SDK de ändringar som beskrivs nedan för att säkerställa att dataskyddet tillämpas.  Det är viktigt att du följer riktlinjerna nedan för att skydda kunddata om du vill att din app ska köras på Android Marshmallow-enheter.  

Med Intune kan du använda alla tillgängliga [funktioner för automatisk säkerhetskopiering](https://developer.android.com/guide/topics/data/autobackup.html) från Android, inklusive möjligheten att definiera anpassade regler i XML, men du måste följa stegen nedan för att skydda dina data:

1. Om din app **inte** använder sin egna anpassade BackupAgent, använder du den förvalda MAMBackupAgent för att få automatiska fullständiga säkerhetskopieringar som är kompatibla med Intune-principer. Placera följande i appmanifestet:

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```


2. **[Valfritt]**  Om du har implementerat en valfri anpassad BackupAgent, måste du använda MAMBackupAgent eller MAMBackupAgentHelper. Se följande avsnitt. Överväg att byta till Intunes **MAMDefaultFullBackupAgent** (beskrivs i steg 1), som ger enkel säkerhetskopiering av Android M och senare.

3. När du har bestämt vilken typ av fullständig säkerhetskopiering som din app ska använda (ofiltrerad, filtrerad eller ingen) ska du ange attributet `android:fullBackupContent` som sant, falskt eller till en XML-resurs i appen.

4. Därefter _**måste**_ du kopiera allt som du placerar i `android:fullBackupContent` i en metadatatagg med namnet `com.microsoft.intune.mam.FullBackupContent` i manifestet.

    **Exempel 1**: Om du vill att din app ska ha fullständiga säkerhetskopior utan undantag, anger du både `android:fullBackupContent`-attributet och `com.microsoft.intune.mam.FullBackupContent`-metadatataggen till **true**:

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **Exempel 2**: Om du vill att din app ska använda sin anpassade BackupAgent och välja bort fullständiga Intune-principkompatibla, automatiska säkerhetskopieringar, måste du ange attributet och metadatataggen till **false**:

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **Exempel 3**: Om du vill att din app ska göra fullständiga säkerhetskopieringar enligt dina anpassade regler i en XML-fil, anger du attributet och metadatataggen till samma XML-resurs:

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```


### <a name="keyvalue-backup"></a>Nyckel-/värdesäkerhetskopiering

Alternativet [Nyckel-/värdesäkerhetskopiering](https://developer.android.com/guide/topics/data/keyvaluebackup.html) är tillgängligt för alla API:er 8+ och överför appdata till [Android Backup Service](https://developer.android.com/google/backup/index.html). Mängden data per användare av din app är begränsad till 5 MB. Om du använder nyckel-/värdesäkerhetskopiering måste du använda en **BackupAgentHelper** eller en **BackupAgent**.

### <a name="backupagenthelper"></a>BackupAgentHelper

BackupAgentHelper är enklare att implementera än BackupAgent, både vad gäller inbyggda Android-funktioner och Intune MAM-integrering. Med BackupAgentHelper kan utvecklare registrera hela filer och delade inställningar, antingen till en **FileBackupHelper** eller till en **SharedPreferencesBackupHelper**, som sedan läggs till i BackupAgentHelper när de skapas. Följ stegen nedan om du vill använda en BackupAgentHelper med Intune MAM:

1. Om du vill använda säkerhetskopiering för flera identiteter med en BackupAgentHelper, följer du Android-guiden till [Utöka BackupAgentHelper](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper).

2. Utöka klassen till MAM-motsvarigheten för BackupAgentHelper, FileBackupHelper och SharedPreferencesBackupHelper.

|Android-klass | MAM-motsvarighet |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

Dessa anvisningar visar säkerhetskopiering och återställning med flera identiteter.

### <a name="backupagent"></a>BackupAgent

Med en BackupAgent kan du vara mycket tydligare om vilka data som ska säkerhetskopieras. Eftersom utvecklaren är ansvarig för implementeringen, finns det fler steg som krävs för att säkerställa rätt dataskydd från Intune. Eftersom det mesta av arbetet läggs över på utvecklaren, är Intune-integreringen något mer komplicerad.

**Integrera MAM:**

1. Läs noggrant igenom Android-guiden för [Nyckel-/värdesäkerhetskopiering](https://developer.android.com/guide/topics/data/keyvaluebackup.html), särskilt [Utöka BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent), för att kontrollera att din BackupAgent-implementering följer riktlinjerna för Android.

2. Låt klassen utöka `MAMBackupAgent`.

**Säkerhetskopiering med flera identiteter:**

1. Innan du påbörjar säkerhetskopieringen bör du kontrollera att de filer eller databuffertar som du ska säkerhetskopiera verkligen är **tillåtna av IT-administratören att säkerhetskopieras** i scenarier med flera identiteter. Vi har lagt till en `isBackupAllowed`-funktion i `MAMFileProtectionManager` och `MAMDataProtectionManager` för att ta reda på detta. Om filen eller databufferten inte får säkerhetskopieras, bör du inte ta med den i säkerhetskopieringen.

2. Om du någon gång under säkerhetskopieringen vill säkerhetskopiera identiteterna för de filer du markerade i steg 1, måste du anropa `backupMAMFileIdentity(BackupDataOutput data, File … files)` med de filer som du vill extrahera data från. När du gör det skapas automatiskt nya säkerhetskopieringsenheter som skrivs till `BackupDataOutput` . Dessa enheter används automatiskt vid en återställning.

**Återställning med flera identiteter:**

Guiden Säkerhetskopiering av data anger en allmän algoritm för att återställa dina programdata och ger ett kodexempel i avsnittet [Utöka BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent). För att få en lyckad återställning med flera identiteter, måste du följa den allmänna strukturen som anges i detta kodexempel med särskild uppmärksamhet på följande:

1. Du måste använda en `while(data.readNextHeader())`*-slinga som går igenom säkerhetskopieringens entiteter.

2. Du måste anropa `data.skipEntityData()`* om `data.getKey()`* inte matchar nyckeln som du skrev i `onBackup`. Om du inte utför det här steget kan dina återställningar komma att misslyckas.

3. Undvik att återgå medan säkerhetskopieringsentiteter används i `while(data.readNextHeader())`*-konstruktionen, eftersom de entiteter som vi automatiskt skriver till går förlorade i så fall.

* Där `data` är det lokala variabelnamnet för den **MAMBackupDataInput** som skickas till din app vid återställning.

## <a name="multi-identity-optional"></a>Flera identiteter (valfritt)

### <a name="overview"></a>Översikt
Som standard tillämpar Intune App SDK principer på appen i sin helhet. Flera identiteter är en valfri Intune-appskyddsfunktion som kan aktiveras för att tillåta att principen tillämpas per identitet. Detta kräver mycket större appmedverkan än andra appskyddsfunktioner.
> [!NOTE]
>  Om appen inte deltar på rätt sätt kan det resultera i dataläckage och andra säkerhetsproblem.

När användaren registrerar enheten eller appen, registrerar SDK:n den identiteten och ser den som den primära Intune-hanterade identiteten. Andra användare i appen behandlas som ohanterade med obegränsade principinställningar.

> [!NOTE]
> För närvarande stöds endast en Intune-hanterad identitet per enhet.

En identitet definieras bara som en sträng. Identiteter är **skiftlägesokänsliga** och en begäran till SDK:n om en identitet kanske inte returnerar samma gemener och versaler som användes när identiteten skapades.

Appen *måste* meddela SDK när den har för avsikt att ändra den aktiva identiteten. SDK meddelar även appen i vissa fall när en identitetsändring krävs. I de flesta fall vet MAM inte vilka data som visas i användargränssnittet eller används på en tråd vid en given tidpunkt och förlitar sig på att appen anger rätt identitet för att undvika dataläckage. I avsnitten som följer kommer vi att visa specifika scenarier som kräver att appåtgärden anropas.
### <a name="enabling-multi-identity"></a>Aktivera flera identiteter

Som standard betraktas alla appar som appar med en enda identitet. Du kan ange att en app ska kunna hantera flera identiteter genom att följande metadata placeras i AndroidManifest.xml.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Ange identiteten

Utvecklare kan ange appens identitet på följande nivåer i fallande ordning:

  1. Trådnivå
  2. Kontextnivå (vanligtvis aktivitet)
  3. Processnivå

En identitet som anges på trådnivå åsidosätter en identitet som angetts på kontextnivå, som i sin tur åsidosätter en identitet som angetts på processnivå. En identitet som angetts för en kontext används endast i lämpliga scenarier. Exempelvis har filrelaterade I/O-åtgärder ingen associerad kontext. Oftast anger appar kontextidentiteten för en aktivitet. En app *måste* inte visa data för en hanterad identitet om inte aktivitetidentiteten är inställd på samma identitet. I allmänhet är processnivåidentiteten bara användbar om appen endast arbetar med en enskild användare åt gången på alla trådar. Många appar behöver kanske inte använda den.

Följande metoder i `MAMPolicyManager` kan användas för att ange identiteten och hämta de identitetsvärden som angavs tidigare.

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);
  ```

>[!NOTE]
> Du kan radera identiteten för appen genom att ange den till null.
>
> Den tomma strängen kan användas som en identitet som alltid saknar en appskyddsprincip.

#### <a name="results"></a>Resultat
Alla metoder som används för att ange identiteten rapporterar tillbaka resultatvärden via `MAMIdentitySwitchResult`. Det finns fyra värden som kan returneras:

| Returvärde | Scenario |
|--|--|
| SUCCEEDED | Identitetsändringen är klar. |
| NOT_ALLOWED  | Identitetsändringen tillåts inte. Det inträffar också vid försök att ange UI-identiteten (kontext) när en annan identitet har angetts för den aktuella tråden. |
| CANCELLED | Användaren avbröt identitetsändringen, vanligtvis genom att klicka på bakåtknappen vid en uppmaning om att ange PIN-kod/autentiseringsuppgifter. |
| FAILED | Identitetsändringen misslyckades av okänd anledning.|

Appen *måste* se till att en identitetsväxling har lyckats innan den visar eller använder företagsdata. Process- och identitetväxlingar lyckas för närvarande alltid för appar med flera identiteter, men vi förbehåller oss rätten att lägga till feltillstånd. Identitetsväxlingen i gränssnittet kan misslyckas på grund av ogiltiga argument, om den skulle hamna i konflikt med trådidentiteten eller om användaren avbryter på grund av villkorliga startkrav (t.ex. trycker på bakåtknappen på PIN-skärmen).


När en kontextidentitet anges rapporteras resultatet asynkront. Om kontexten är en aktivitet vet SDK:n inte om identitetsändringen lyckades förrän efter att en villkorlig start har utförts. Den kan kräva att användaren anger en PIN-kod eller företagets autentiseringsuppgifter. Appen förväntas implementera en `MAMSetUIIdentityCallback` för att ta emot det här resultatet och du kan skicka null för den här parametern.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

Du kan också ange identiteten för en aktivitet direkt via en metod i `MAMActivity`, i stället för att anropa `MAMPolicyManager.setUIPolicyIdentity`. Använd följande metod för att göra detta:

```java
     public final void switchMAMIdentity(final String newIdentity);
```

Du kan även åsidosätta en metod i `MAMActivity` om du vill att appen ska aviseras om resultatet vid försök att ändra identiteten för aktiviteten.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

>[!NOTE]
> Identitetsväxlingar kan kräva att aktiviteten återskapas. I detta fall skickas `onSwitchMAMIdentityComplete`-motanropet till den nya instansen av aktiviteten.


### <a name="implicit-identity-changes"></a>Implicita identitetsändringar

Förutom appens möjlighet att ange identiteten kan en tråd eller identiteten för ett sammanhang ändras baserat på inkommande data från en annan Intune-hanterad app med en appskyddsprincip.

#### <a name="examples"></a>Exempel

  1. Om en aktivitet startas via en `Intent` som skickas av en annan MAM-app, anges aktivitetens identitet baserat på den effektiva identiteten i den andra appen vid tidpunkten då denna `Intent` skickades.

  2.  För tjänster anges trådens identitet på liknande sätt för varaktigheten i ett `onStart`- eller `onBind`-anrop. Anrop till `Binder` som returneras från `onBind` anger också tillfälligt trådens identitet.

  3. Anrop till en `ContentProvider` anger på liknande sätt trådens identitet för deras varaktighet.


  Dessutom kan användarinteraktion med en aktivitet orsaka en implicit identitetsväxling.

  **Exempel:** Om en användare avbryter en auktoriseringsuppmaning under `Resume`, resulterar det i en implicit växling till en tom identitet.

  Appen kan välja att bli meddelad om dessa ändringar, och kan förbjuda dem om det behövs. `MAMService` och `MAMContentProvider` exponerar följande metod som kan åsidosättas av underklasser:

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
  ```

  `MAMActivity`-klassen omfattar en extra parameter i metoden:

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
  ```

  * `AppIdentitySwitchReason` registrerar källan för den implicita växlingen och kan acceptera värdena `CREATE`, `RESUME_CANCELLED` och `NEW_INTENT`.  `RESUME_CANCELLED`-orsaken används när en aktivitetsåterställning resulterar i att användargränssnittet för PIN-koder, autentiseringsuppgifter eller andra efterlevnadsprinciper visas och användaren försöker avbryta användargränssnittet, vanligtvis genom att använda Bakåt-knappen.


  * `AppIdentitySwitchResultCallback` är följande:

    ```java
    public interface AppIdentitySwitchResultCallback {
        /**
         * @param result
         *            whether the identity switch can proceed.
         */
        void reportIdentitySwitchResult(AppIdentitySwitchResult result);
    }
    ```

    Där ```AppIdentitySwitchResult``` är antingen SUCCESS eller FAILURE.

Metoden `onMAMIdentitySwitchRequired` anropas för alla implicita identitetsändringar utom för de som görs via en Binder som returneras från `MAMService.onMAMBind`. Standardimplementeringar av omedelbart anrop för `onMAMIdentitySwitchRequired`:

* `reportIdentitySwitchResult(FAILURE)` när orsaken är RESUME_CANCELLED.

* `reportIdentitySwitchResult(SUCCESS)` i alla andra fall.

  De flesta appar behöver inte blockera eller fördröja en identitetsväxling på andra sätt, men om en app måste göra det är det viktigt att ha följande i åtanke:

  * Om en identitetsväxling blockeras är resultatet är samma som om delningsinställningar i `Receive` hade förbjudit inkommande data.

  * Om en tjänst körs på huvudtråden **måste** `reportIdentitySwitchResult` anropas synkront, annars låser sig UI-tråden.

  * När en **aktivitet** ska skapas kommer `onMAMIdentitySwitchRequired` anropas före `onMAMCreate`. Om appen måste visa ett användargränssnitt för att avgöra om identitetsväxlingen ska tillåtas eller inte, måste användargränssnittet visas med hjälp av en *annan* aktivitet.

  * Om en växling till den tomma identiteten begärs med orsaken RESUME_CANCELLED i en **aktivitet**, måste appen ändra den återupptagna aktiviteten för att visa data som överensstämmer med identitetsväxlingen.  Om detta inte är möjligt bör appen avvisa växlingen och användaren uppmanas på nytt att följa principen för identiteten som ska återupptas (t.ex. genom att en skärm för inmatning av appens PIN-kod visas).

    > [!NOTE]
    > En app med flera identiteter tar alltid emot inkommande data från både hanterade och ohanterade appar. Det är appens ansvar att behandla data från hanterade identiteter på ett hanterat sätt.

  Om en begärd identitet hanteras (använd `MAMPolicyManager.getIsIdentityManaged` för att kontrollera), men appen inte kan använda det kontot (t.ex. eftersom bl.a. e-postkonton måste konfigureras i appen först), bör identitetsväxlingen avvisas.
#### <a name="build-plugin--tool-considerations"></a>Att tänka på när du använder plugin-programmet eller verktyget för utveckling
Om du inte uttryckligen ärver från `MAMActivity`, `MAMService`, eller `MAMContentProvider` (eftersom du tillåter att utvecklingsverktyg gör den ändringen), men fortfarande behöver bearbeta identitetsväxlingar, kan du i stället implementera `MAMActivityIdentityRequirementListener` (för aktiviteter) eller `MAMIdentityRequirementListener` (för tjänster och ContentProviders). Standardbeteendet för `MAMActivity.onMAMIdentitySwitchRequired` kan nås genom anrop till den statiska metoden `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)`.

Om du vill åsidosätta `MAMActivity.onSwitchMAMIdentityComplete` kan du på motsvarande sätt implementera `MAMActivityIdentitySwitchListener` utan att uttryckligen ärva från `MAMActivity`.

### <a name="preserving-identity-in-async-operations"></a>Bevara identitet i asynkrona åtgärder
Det är vanligt att åtgärder i UI-tråden skickar bakgrundsaktiviteter till en annan tråd. En app med flera identiteter vill se till att de här bakgrundsaktiviteterna fungerar med rätt identitet, vilken ofta är samma identitet som används av aktiviteten som skickade ut dem. MAM SDK:n innehåller `MAMAsyncTask` och `MAMIdentityExecutors` för att göra det enklare att bevara identiteten.
#### <a name="mamasynctask"></a>MAMAsyncTask

Om du vill använda `MAMAsyncTask` kan du helt enkelt ärva från den i stället för AsyncTask och ersätta åsidosättningar av `doInBackground` och `onPreExecute` med `doInBackgroundMAM` respektive `onPreExecuteMAM`. Konstruktorn `MAMAsyncTask` tar ett aktivitetssammanhang. Exempel:

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
Med `MAMIdentityExecutors` kan du omsluta en befintlig instans av `Executor` eller `ExecutorService` som en `Executor`/`ExecutorService` som bevarar identiteter med metoderna `wrapExecutor` och `wrapExecutorService`. Till exempel

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```
### <a name="file-protection"></a>Filskydd

Alla filer har en associerad identitet när de skapas, baserat på tråd- och processidentiteten. Den här identiteten används för både filkryptering och selektiv rensning. Endast filer vars identitet är hanterad och som har en princip som kräver kryptering krypteras. Med SDK:s förvalda selektiva funktionsrensning rensas endast filer som är associerade med den hanterade identitet som en rensning har begärts för. Appen kan fråga efter eller ändra en fils identitet med hjälp av `MAMFileProtectionManager`-klassen.

  ```java
    public final class MAMFileProtectionManager {

        /**
         * Protect a file. This will synchronously trigger whatever protection is required for the 
         * file, and will tag the file for future protection changes.
         *
         * @param identity
         *            Identity to set.
         * @param file
         *            File to protect.
         * @throws IOException
         *             If the file cannot be changed.
         */
        public static void protect(final File file, final String identity) throws IOException;

       /**
         * Protect a file obtained from a content provider. This is intended to be used for
         * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
         * It may also be used with descriptors referring to private files owned by this app.
         * It is not intended to be used for files owned by other apps and such usage will fail. If
         * creating a new file via a content provider exposed by another MAM-integrated app, the new
         * file identity will automatically be set correctly if the ContentResolver in use was
         * obtained via a Context with an identity or if the thread identity is set.
         *
         * This will synchronously trigger whatever protection is required for the file, and will tag
         * the file for future protection changes. If an identity is set on a directory, it is set
         * recursively on all files and subdirectories. If MAM is operating in offline mode, this
         * method will silently do nothing.
         *
         * @param identity
         *            Identity to set.
         * @param file
         *            File to protect.
         *
         * @throws IOException
         *             If the file cannot be protected.
         */
        public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

       /**
        * Get the protection info on a file.
        *
        * @param file
        *            File or directory to get information on.
        * @return File protection info, or null if there is no protection info.
        * @throws IOException
        *             If the file cannot be read or opened.
        */
        public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;

       /**
        * Get the protection info on a file.
        *
        * @param file
        *            File or directory to get information on.
        * @return File protection info, or null if there is no protection info.
        * @throws IOException
        *             If the file cannot be read or opened.
        */
        public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

    }

    public interface MAMFileProtectionInfo {
        String getIdentity();
    }
  ```
#### <a name="app-responsibility"></a>Appansvar
MAM kan inte automatiskt härleda en relation mellan lästa filer och data som visas i en `Activity`. Appar *måste* ange en korrekt gränssnittsidentitet innan de visar företagsdata. Detta inkluderar data från filer. Om en fil som kommer från utanför appen (antingen från en `ContentProvider` eller från en offentligt skrivbar plats) *måste* appen försöka fastställa identiteten för filen (med `MAMFileProtectionManager.getProtectionInfo`) innan informationen från filen visas. Om `getProtectionInfo` rapporterar en icke-null, icke-tom identitet, *måste* gränssnittsidentiteten anges så att den matchar den här identiteten (med hjälp av `MAMActivity.switchMAMIdentity` eller `MAMPolicyManager.setUIPolicyIdentity`). Om identitetväxlingen misslyckas får data från filen *inte* visas.

Ett exempelflöde kan se ut ungefär som nedan:
  * Användaren väljer ett dokument att öppna i appen
  * Under öppningsflödet innan läsning av data från disken, bekräftar appen identiteten som ska användas för att visa innehållet
    * MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
    * if(info)   MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback)
    * Appen väntar tills resultatet rapporteras till återanrop
    * Om det rapporterade resultatet är ett fel kommer appen inte att visa dokumentet.
  * Appen öppnar och återger filen

#### <a name="offline-scenarios"></a>Offline-scenarier

Filidentitetstaggningen känner av offlineläget. Ha följande i åtanke:

  * Om företagsportalen inte är installerad kan du inte tagga filer med identiteter.

  * Om företagsportalen är installerad, men appen saknar Intune MAM-principen, kan principerna inte taggas med identiteten på ett tillförlitligt sätt.

  * När filidentitetstaggning blir tillgängligt behandlas alla tidigare skapade filer som personliga/ohanterade (tillhör identiteten med en tom sträng), om inte appen redan har installerats som en hanterad app med en enda identitet. Då anses den tillhöra den registrerade användaren.

### <a name="directory-protection"></a>Katalogskydd

Kataloger kan skyddas med samma `protect`-metod som används för att skydda filer. Katalogskydd tillämpas rekursivt på alla filer och underkataloger i katalogen samt på nya filer som skapas i katalogen. Eftersom katalogskydd tillämpas rekursivt kan det ta en stund att slutföra `protect`-anropet för stora kataloger. Därför kan det vara bättre att appar som använder skydd på en katalog som innehåller ett stort antal filer, kör `protect` asynkront i en bakgrundstråd.

### <a name="data-protection"></a>Dataskydd

Det går inte att tagga en fil som om den tillhörde flera identiteter. Appar som måste lagra data som tillhör olika användare i samma fil, kan göra detta manuellt med hjälp av de funktioner som finns i `MAMDataProtectionManager`. På så sätt kan programmet kryptera data och koppla dem till en viss användare. Krypterade data är lämpligt för lagring till disk i en fil. Du kan köra frågor mot data som är associerade med identiteten, och dekryptera dessa data senare.

Appar som använder `MAMDataProtectionManager` bör implementera en mottagare av `MANAGEMENT_REMOVED`-meddelandet. När det här meddelandet är klart kan buffertar som skyddades via den här klassen inte längre läsas, om filkryptering aktiverades när buffertarna skyddades. Appen kan åtgärda detta genom att anropa MAMDataProtectionManager.unprotect på alla buffertar under meddelandet. Observera att det också är säkert att anropa skyddet under det här meddelandet om man önskar bevara identitetsinformation – krypteringen kommer att inaktiveras under meddelandet.

```java

public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected
     * input.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function
     *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The
     *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original
     *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method.
     *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the
     * unprotected input.
     *
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     *
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input stream to get information on. Either this input
     *            stream must have been returned by a previous call to
     *            protect OR input.markSupported() must return true.
     *            Otherwise it will be impossible to get protection info
     *            without advancing the stream position. The stream must be
     *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input bytes to get information on. These must be bytes
     *            returned by a previous call to protect() or a copy of
     *            such bytes.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```

### <a name="content-providers"></a>Innehållsproviders

Om appen innehåller andra företagsdata än en **ParcelFileDescriptor** via en **ContentProvider**, måste appen anropa metoden `isProvideContentAllowed(String)` i `MAMContentProvider` och skicka ägaridentitetens UPN (användarens huvudnamn) för innehållet. Om den här funktionen returnerar false *får inte* innehållet returneras till anroparen. Filbeskrivningar som returneras via en innehållsprovider hanteras automatiskt baserat på filidentiteten.

### <a name="selective-wipe"></a>Selektiv rensning

Om en app med flera identiteter registreras för `WIPE_USER_DATA`-meddelandet är det appens ansvar att ta bort alla data för användaren som rensas, inklusive alla filer som har identitetsmärkts som tillhörande användaren i fråga. Om appen tar bort användardata från en fil, men vill lämna andra data i filen, *måste* identiteten för filen ändras (via `MAMFileProtectionManager.protect` till en personlig användare eller en tom identitet). Om krypteringsprincipen används dekrypteras inga eventuella återstående filer som hör till användare som tas bort, och de blir otillgängliga för appen efter rensningen.

En appregistrering för `WIPE_USER_DATA` kan inte dra nytta av standardbeteendet för selektiv rensning i SDK:n. För appar som kan hantera flera identiteter kan denna förlust vara mer betydelsefull, eftersom en selektiv standardrensning med MAM endast rensar filer vars identitet ska rensas. Om ett program som kan hantera flera identiteter önskar att MAM:s selektiva standardrensning ska göras _**och**_ vill utföra egna åtgärder för rensningen, måste det registrera sig för `WIPE_USER_AUXILIARY_DATA`-meddelanden. Det här meddelandet skickas omedelbart av SDK:n innan den utför MAM:s selektiva standardrensning. En app bör aldrig registreras för både WIPE_USER_DATA och WIPE_USER_AUXILIARY_DATA.


## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Aktivera MAM-riktad konfiguration för Android-appar (valfritt)
Programspecifika nyckelvärdepar kan konfigureras i Intune-konsolen. Dessa nyckel-värdepar tolkas inte av Intune utan de skickas till appen. Program som ska ta emot sådan konfiguration kan använda klasserna `MAMAppConfigManager` och `MAMAppConfig` för detta. Om flera principer är inriktade på samma app kan det finnas flera motstridiga värden för samma nyckel.

### <a name="example"></a>Exempel
```
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
LOGGER.info("App Config Data = " + (appConfig == null ? "null" : appConfig.getFullData()));
String valueToUse = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    for (String value : values) {
        if (isCorrectValue(value)) {
            valueToUse = value;
        }
    }
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
LOGGER.info("Found value " + valueToUse);
```

### <a name="mamappconfig-reference"></a>MAMAppConfig Reference

```
public interface MAMAppConfig {
    /**
     * Conflict resolution types for Boolean values.
     */
    enum BooleanQueryType {
        /**
         * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
         */
        Any,
        /**
         * In case of conflict, returns true if any of the values are true.
         */
        Or,
        /**
         * In case of conflict, returns false if any of the values are false.
         */
        And
    }

    /**
     * Conflict resolution types for integer and double values.
     */
    enum NumberQueryType {
        /**
         * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
         */
        Any,
        /**
         * In case of conflict, returns the minimum Integer.
         */
        Min,
        /**
         * In case of conflict, returns the maximum Integer.
         */
        Max
    }

    /**
     * Conflict resolution types for Strings.
     */
    enum StringQueryType {
        /**
         * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
         */
        Any,
        /**
         * In case of conflict, returns the first result ordered alphabetically.
         */
        Min,
        /**
         * In case of conflict, returns the last result ordered alphabetically.
         */
        Max
    }

    /**
     * Retrieve the List of Dictionaries containing all the custom
     *  config data sent by the MAMService. This will return every
     * Application Configuration setting available for this user, one
     *  mapping for each policy applied to the user.
     */
    List<Map<String, String>> getFullData();

    /**
     * Returns true if there is more than one targeted custom config setting for the key provided. 
     */
    boolean hasConflict(String key);

    /**
     * @return a Boolean value for the given key if it can be coerced into a Boolean, or 
     * null if none exists or it cannot be coerced.
     */
    Boolean getBooleanForKey(String key, BooleanQueryType queryType);

    /**
     * @return a Long value for the given key if it can be coerced into a Long, or null if none exists or it cannot be coerced.
     */
    Long getIntegerForKey(String key, NumberQueryType queryType);

    /**
     * @return a Double value for the given key if it can be coerced into a Double, or null if none exists or it cannot be coerced.
     */
    Double getDoubleForKey(String key, NumberQueryType queryType);

    /**
     * @return a String value for the given key, or null if none exists.
     */
    String getStringForKey(String key, StringQueryType queryType);

    /**
     * Like getBooleanForKey except returns all values if multiple are present.
     */
    List<Boolean> getAllBooleansForKey(String key);

    /**
     * Like getIntegerForKey except returns all values if multiple are present.
     */
    List<Long> getAllIntegersForKey(String key);

    /**
     * Like getDoubleForKey except returns all values if multiple are present.
     */
    List<Double> getAllDoublesForKey(String key);

    /**
     * Like getStringForKey except returns all values if multiple are present.
     */
    List<String> getAllStringsForKey(String key);
}
```

### <a name="notification"></a>Meddelande
Programkonfiguration lägger till en ny meddelandetyp:
* **REFRESH_APP_CONFIG**: det här meddelandet skickas en `MAMUserNotification` och informerar appen att nya app config-data är tillgängliga.

Mer information om funktionerna i Graph API finns i [Graph API-referens](https://developer.microsoft.com/graph/docs/concepts/overview). <br>

Mer information om hur du skapar en MAM-riktad appkonfigurationsprincip i Android finns i avsnittet om MAM-riktad appkonfiguration i [How to use Microsoft Intune app configuration policies for Android](https://docs.microsoft.com/intune/app-configuration-policies-use-android) (använda Microsoft Intune-appkonfigurationsprinciper för Android).

## <a name="style-customization-optional"></a>Formatanpassning (valfritt)

Vyer som genererats av MAM SDK kan anpassas visuellt för att bättre matcha appen som den ingår i. Du kan anpassa primära färger, sekundära färger och bakgrundsfärger, samt storleken på applogotypen. Formatanpassningen är valfri och standardvärden används om inget anpassat format har konfigurerats.


### <a name="how-to-customize"></a>Så här anpassar du
För att kunna tillämpa formatändringarna på Intunes MAM-vyer måste du först skapa en XML-fil som åsidosätter formatet. Den här filen placeras i katalogen ”/res/xml” i din app och du kan döpa den till vad du vill. Nedan visas ett exempel på det format som den här filen måste följa.
```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>
```

Du måste återanvända resurser som redan finns i din app. Du måste till exempel definiera färgen grönt i filen colors.xml och referera till den här. Du kan inte använda Hex-koden ”#0000ff”. Den maximala storleken för applogotypen är 110 dip (dp). Du kan använda en mindre logotypbild, men maxstorleken ger det bästa resultatet. Om du överskrider gränsen 110 dip kommer bilden att skalas ner och kan då bli suddig.

Nedan visas den fullständiga listan med tillåtna attribut, UI-element som de styr, XML-attributens objektnamn och typ av resurs som förväntas för dem.

|Formatattribut | UI-element som påverkas | Attributets objektnamn | Förväntad resurstyp |
| -- | -- | -- | -- |
| Bakgrundsfärg | Bakgrundsfärg för PIN-kodskärmen <Br>PIN-kodrutans fyllningsfärg | background_color | Färg |
| Förgrundsfärg | Förgrundens textfärg <br> PIN-kodrutans standardkantlinje <br> Tecken (inklusive dolda tecken) i PIN-kodrutan när användaren anger sin PIN-kod| foreground_color | Färg|
| Accentfärg | PIN-kodrutans kantlinje när den är markerad <br> Hyperlänkar |accent_color | Färg |
| Applogotyp | Stor ikon som visas på Intune-appens PIN-kodskärm | logo_image | Ritbar |

## <a name="default-enrollment-optional"></a>Standardregistrering (valfritt)
<!-- Requiring user login prompt for an automatic APP-WE service enrollment, requiring Intune app protection policies in order to use your SDK-integrated Android LOB app, and enabling ADAL SSO (optional) -->

Följande är vägledning för att kräva användaruppmaning vid start av appen för en automatisk APP-WE-tjänstregistrering (vi kallar detta **standardregistrering** i det här avsnittet), som kräver Intune-appskyddsprinciper för att endast tillåta att Intune-skyddade användare använder den SDK-integrerade Android LOB-appen. Det tar även upp hur du kan aktivera SSO för den SDK-integrerade Android LOB-appen. Detta stöds **inte** för Store-appar som kan användas av användare utan Intune.

> [!NOTE] 
> Fördelarna med **standardregistrering** omfattar en förenklad metod för att hämta en princip från APP-WE-tjänsten för en app på enheten.

### <a name="general-requirements"></a>Allmänna krav
* Se till att din app registreras med Intune Mobile Application Management-tjänsten genom att följa stegen i [Vanliga ADAL-konfigurationer #2](https://docs.microsoft.com/intune/app-sdk-android#common-adal-configurations).

### <a name="working-with-the-intune-sdk"></a>Arbeta med Intune SDK
De här anvisningarna är specifika för alla Android- och Xamarin-apputvecklare som vill kräva Intune-appskyddsprinciper för användning av appen på en slutanvändarenhet.

1. Konfigurera ADAL med hjälp av stegen som beskrivs i [handboken för Intune SDK för Android](https://docs.microsoft.com/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal).
   > [!NOTE] 
   > Termen "klient-id" som är kopplad till din app är samma som termen "program-id" från Azure Portal. 
2. Du behöver "Vanlig ADAL-konfiguration" nummer 2 för att aktivera SSO.

3. Aktivera standardregistrering genom att ange följande värde i manifestet: ```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
   > [!NOTE] 
   > Det får inte finnas några fler MAM-WE-integreringar i appen. Det kan uppstå konflikter om det finns några andra försök att anropa MAMEnrollmentManager API:er.

4. Aktivera MAM-principen som krävs genom att ange följande värde i manifestet: ```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
   > [!NOTE] 
   > Det gör att användaren måste ladda ned företagsportalen till enheten och slutföra flödet för standardregistrering före användning.

> [!NOTE]
    > Det får inte finnas några fler MAM-WE-integreringar i appen. Det kan uppstå konflikter om det görs andra försök att anropa MAMEnrollmentManager-API:er.

3. Aktivera MAM-principen som krävs genom att ange följande värde i manifestet:
```xml
<meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
```

> [!NOTE] 
> Det gör att användaren måste ladda ned företagsportalen till enheten och slutföra flödet för standardregistrering före användning.

## <a name="limitations"></a>Begränsningar

### <a name="file-size-limitations"></a>Filstorleksbegränsningar

För stora kodbaser som körs utan [ProGuard](http://proguard.sourceforge.net/), kan begränsningarna i formatet Dalvik för körbara filer bli ett problem. Mer specifikt kan följande begränsningar förekomma:

1.  Gräns på 65 000 för fält.
2.  Gräns på 65 000 för metoder.

### <a name="policy-enforcement-limitations"></a>Principtillämpningsgränser

* **Skärmdump**: SDK kan inte framtvinga ett nytt värde för skärmdumpsinställningen i aktiviteter som redan har gått igenom Activity.onCreate. Detta kan resultera i en viss tidsperiod då appen är konfigurerad att inaktivera skärmdumpar men då skärmdumpar fortfarande kan tas.

* **Med hjälp av innehållsmatchare**: Överförings- eller mottagningsprincipen i Intune kan blockera eller delvis blockera användningen av en innehållsmatchare för att få åtkomst till innehållsleverantören i en annan app. Detta innebär att ContentResolver-metoder returnerar null eller genererar ett felvärde (t.ex. genererar `openOutputStream` felet `FileNotFoundException` om den blockeras). Appen kan avgöra om en misslyckad dataskrivning till en innehållsmatchare orsakades av en princip (eller kan orsakas av en princip) genom att göra anropet:
    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```
    eller om det inte finns någon tillhörande aktivitet

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    I det andra fallet måste appar med flera identiteter vara noga med att ange rätt tråd-ID (eller skicka en explicit identitet till anropet `getPolicy`).

### <a name="exported-services"></a>Exporterade tjänster

 Filen AndroidManifest.xml i Intune App SDK innehåller **MAMNotificationReceiverService**, som måste vara en exporterad tjänst för att företagsportalen ska kunna skicka meddelanden till en hanterad app. Tjänsten kontrollerar anroparen för att säkerställa att bara Företagsportal har tillåtelse att skicka meddelanden.

### <a name="reflection-limitations"></a>Reflektionsbegränsningar
Vissa MAM-grundklasser (t.ex. MAMActivity, MAMDocumentsProvider) innehåller metoder (baserade på de ursprungliga Android-grundklasserna) som använder typer av parametrar eller returer som endast finns ovanför vissa API-nivåer. Därför kanske det inte alltid är möjligt att använda reflektion för att räkna upp alla metoder för appkomponenter. Den här begränsningen är inte begränsad till MAM. Det är samma begränsning som skulle gälla om appen själv implementerat metoderna från Android-grundklasserna.

### <a name="robolectric"></a>Robolectric
Det går inte att testa MAM SDK-funktionalitet i Robolectric. Det finns kända problem med att köra MAM SDK i Roboelectric på grund av speciell funktionalitet i Robelectric som inte exakt efterliknar den på verkliga enheter eller emulatorer.

Om du behöver testa ditt program i Roboelectric rekommenderar vi att du flyttar din programklasslogik till en stödprocess och skapar ditt enhetstestnings-apk med en programklass som inte ärver från MAMApplication.
## <a name="expectations-of-the-sdk-consumer"></a>Förväntningar på SDK-konsumenten

Intune SDK använder kontraktet som tillhandahålls av Android-API:et, även om feltillstånd kan utlösas oftare på grund av principtillämpning. Följande Android-rekommendationer minskar risken för fel:

* Android SDK-funktioner som kan returnera null har högre sannolikhet att vara null nu.  Se till att null-kontrollerna körs på rätt plats för att minimera risken för problem.

* Funktioner som kan kontrolleras måste kontrolleras genom sina MAM-ersatta API:er.

* Eventuella härledda funktioner måste göra anrop upp till sina överordnade klassversioner.

* Undvik att använda API:er på ett tvetydigt sätt. Till exempel resulterar `Activity.startActivityForResult` utan att requestCode kontrolleras i ett onormalt beteende.

## <a name="telemetry"></a>Telemetri

Intune App SDK för Android styr inte insamling av data från din app. Företagsportalprogrammet loggar telemetridata som standard. Dessa data skickas till Microsoft Intune. Enligt Microsofts policy samlar vi inte in någon personligt identifierbar information (PII).

> [!NOTE]
> Om användare väljer att inte skicka dessa data så måste de inaktivera telemetri under inställningarna i företagsportalappen. Du kan läsa mer i [Inaktivera Microsofts insamling av användningsdata](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="recommended-android-best-practices"></a>Rekommenderade metoder för Android

* Om möjligt bör alla biblioteksprojekt dela samma android:package. Detta kommer inte att leda till sporadiska fel vid körning, eftersom det helt och hållet är ett problem som uppstår vid byggning. Nyare versioner av Intune App SDK tar bort en del av redundansen.

* Använd de senaste Android SDK-byggverktygen.

* Ta bort alla onödiga och oanvända bibliotek (t.ex. android.support.v4)
