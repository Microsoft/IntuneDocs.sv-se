---
title: Utvecklarhandbok för Microsoft Intune App SDK för Android
description: Med Microsoft Intune App SDK för Android kan du implementera hantering av mobila appar (MAM, Mobile App Management) med Intune i din Android-app.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5808a4b81fcc66d37e78c50cb5bcd2ae7bbe44e2
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049609"
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

### <a name="android-versions"></a>Android-versioner
SDK:n stöder Android API 19 (Android 4.4+) till och med Android API 28 (Android 9.0).

### <a name="company-portal-app"></a>Företagsportalappen
Intune App SDK för Android förutsätter att [företagsportalappen](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) finns på enheten för att appskyddsprinciperna ska kunna aktiveras. Företagsportalen hämtar appskyddsprinciper från Intune-tjänsten. När appen initieras läser den in principen och koden för att kunna aktivera principen från företagsportalen.

> [!NOTE]
> Om appen Företagsportal inte finns på enheten fungerar en Intune-hanterad app som en normal app som saknar stöd för Intunes appskyddsprinciper.

Vid appskydd utan enhetsregistrering behöver användaren _**inte**_ registrera enheten med företagsportalappen.

## <a name="sdk-integration"></a>SDK-integrering

### <a name="sample-app"></a>Exempelapp
Ett exempel på hur du integrerar korrekt med Intune App SDK finns på [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App). I det här exemplet används [plugin-programmet för Gradle-utveckling](#gradle-build-plugin).

### <a name="referencing-intune-app-libraries"></a>Referera till Intune App-bibliotek

Intune App SDK är ett Android-standardbibliotek utan externa beroenden. **Microsoft.Intune.MAM.SDK.aar** innehåller både de gränssnitt som krävs för att aktivera en appskyddsprincip och den kod som behövs för att interagera med Microsoft Intunes företagsportalappen.

**Microsoft.Intune.MAM.SDK.aar** måste anges som en Android-biblioteksreferens. Gör detta genom att öppna approjektet i Android Studio och gå till **Arkiv > Ny > Ny modul**. Välj **Importera .JAR/.AAR-paket**. Välj sedan Android-arkivpaketet Microsoft.Intune.MAM.SDK.aar för att skapa en modul för vår .AAR. Högerklicka på den modul eller de moduler som innehåller din appkod och gå till **Modulinställningar** > **fliken Beroenden** >  **+-ikonen** > **Modulberoende** > Välj den MAM SDK AAR-modul som du precis skapat > **OK**. På så sätt kan du vara säker på att modulen kompileras med MAM SDK när du skapar ditt projekt.

Dessutom kan **Microsoft.Intune.MAM.SDK.Support.XXX.jar**-biblioteken innehålla Intune-varianter av motsvarande `android.support.XXX`-bibliotek. De ingår inte i Microsoft.Intune.MAM.SDK.aar eftersom inte alla appar är beroende av stödbiblioteken.

#### <a name="proguard"></a>ProGuard

Om [ProGuard](http://proguard.sourceforge.net/) (eller någon annan krympande/döljande mekanism) används som ett utvecklingssteg har SDK:n ytterligare konfigurationsregler (MPR) som måste tas med. När du inkluderar .AAR i build-versionen läggs reglerna automatiskt till i ProGuard-steget, och de nödvändiga klassfilerna bevaras.

Azure ADAL (Active Directory Authentication Libraries) kan ha egna ProGuard-begränsningar. Om din app integrerar ADAL måste du följa ADAL-dokumentationen om dessa begränsningar.

### <a name="build-tooling"></a>Utvecklingsverktyg
Intune App SDK är ett Android-bibliotek som gör att din app stöder och kan tillämpa Intune-principer. Vissa principer kräver [att din app uttryckligen deltar i tillämpningen av principerna](#enable-features-that-require-app-participation), men de flesta tillämpas halvautomatiskt. Den här automatiska tillämpningen kräver att appar ersätter arv från flera Android-basklasser med arv från MAM-motsvarigheter, samt att de på motsvarande sätt ersätter anrop till vissa tjänstklasser för Android-system med anrop till MAM-motsvarigheter. De specifika ersättningar som krävs beskrivs [nedan](#class-and-method-replacements).

Det kan vara tidskrävande att utföra dessa ersättningar manuellt. Därför innehåller SDK:n utvecklingsverktyg (ett plugin-program för Gradle-utveckling och ett kommandoradsverktyg för annan utveckling) som utför ersättningarna automatiskt. Dessa verktyg omvandlar klassfilerna som genereras av Java-kompileringen och ändrar inte den ursprungliga källkoden.

Verktygen utför endast [direkta ersättningar](#class-and-method-replacements). De utför inte mer komplexa SDK-integrationer som [”spara som”-principer](#enable-features-that-require-app-participation), [multiidentitet](#multi-identity-optional), [App-WE-registrering](#app-protection-policy-without-device-enrollment), [AndroidManifest-ändringar](#manifest-replacements) eller [ADAL-konfiguration](#configure-azure-active-directory-authentication-library-adal). Dessa måste därför utföras innan din app är helt Intune-aktiverad. Läs noga igenom resten av den här dokumentationen för integreringsinformation som är relevant för din app.

> [!NOTE]
> Det går bra att köra verktygen för ett projekt som redan helt eller delvis har integrerat MAM SDK via manuella ersättningar. Ditt projekt måste fortfarande lista MAM SDK som ett beroende.

### <a name="gradle-build-plugin"></a>Plugin-program för Gradle-utveckling
Om din app inte utvecklas med gradle går du vidare till [Integrera med kommandoradsverktyget](#command-line-build-tool). 

Plugin-programmet för App SDK distribueras som en del av SDK:n som **GradlePlugin/com.microsoft.intune.mam.build.jar**. För att Gradle ska kunna hitta plugin-programmet måste det läggas till i buildscript-klassökvägen. Plugin-programmet är beroende av [Javassist](https://jboss-javassist.github.io/javassist/), som också måste läggas till. Du lägger till dem i klassökvägen genom att lägga till följande i din rot-`build.gradle`

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
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*", "!com.microsoft.qux*"]
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
* `com.microsoft.qux:foo:2.0` skrivs inte om trots att den matchar samma jokertecken som föregående objekt eftersom den uttryckligen exkluderas via ett negationsmönster.

#### <a name="usage-of-includeexternallibraries"></a>Användning av includeExternalLibraries

Eftersom plugin-programmet som standard endast fungerar med projektberoenden (som vanligtvis tillhandahålls av funktionen `project()`) måste eventuella beroenden som anges av `fileTree(...)` eller som hämtas från maven eller andra paketkällor (t.ex ”.`com.contoso.bar:baz:1.2.0`”) tillhandahållas till egenskapen `includeExternalLibraries` om MAM-bearbetning av dem krävs enligt de villkor som beskrivs nedan. Jokertecken (”*”) stöds. Ett objekt som börjar med `!` är en negation och kan användas för att undanta bibliotek som annars skulle inkluderas av ett jokertecken.

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

#### <a name="reporting"></a>Rapportering
Plugin-programmet för utveckling kan generera en HTML-rapport över de ändringar som det gör. Om du vill begära generering av den här rapporten anger du `report = true` i konfigurationsblocket `intunemam`. Om rapporten genereras skrivs den till `outputs/logs` i utvecklingskatalogen.

```groovy
intunemam {
    report = true
}
```

#### <a name="dependencies"></a>Beroenden

Gradle-plugin-programmet har ett beroende till [Javassist](https://jboss-javassist.github.io/javassist/), som måste vara tillgängligt för Gradles beroendematchning (se beskrivningarna ovan). Javassist används endast under apputvecklingen när plugin-programmet körs. Ingen Javassist-kod läggs till i din app.

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

> [!NOTE] 
> På Unix-liknande system är semikolon en kommandoavgränsare. För att undvika att gränssnittet delar kommandon bör du undanta varje semikolon med \' eller omsluta hela parametern med citattecken.

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
| android.app.Dialog | MAMDialog |
| android.app.AlertDialog.Builder | MAMAlertDialogBuilder |
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
| android.support.v7.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
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
I många fall har en metod som är tillgänglig i Android-klassen markerats som slutgiltig i MAM-ersättningsklassen. I detta fall tillhandahåller MAM-ersättningsklassen en metod med liknande namn (vanligtvis med suffixet `MAM`) som ska åsidosättas i stället. Om du härleder från `MAMActivity`, i stället för att åsidosätta `onCreate()` och anropa `super.onCreate()`, måste `Activity` åsidosätta `onMAMCreate()` och anropa `super.onMAMCreate()`. Java-kompilatorn ska framtvinga de slutliga begränsningarna för att förhindra oavsiktlig åsidosättning av den ursprungliga metoden i stället för motsvarande MAM.

### <a name="mamapplication"></a>MAMApplication
Om din app skapar en underklass av `android.app.Application` så **måste** du skapa en underklass av `com.microsoft.intune.mam.client.app.MAMApplication` i stället. Om din app inte skapar `android.app.Application` som en underklass **måste** du ange `"com.microsoft.intune.mam.client.app.MAMApplication"` som `"android:name"`-attribut i taggen `<application>` i AndroidManifest.xml.

### <a name="pendingintent"></a>PendingIntent
I stället för `PendingIntent.get*` måste du använda `MAMPendingIntent.get*`-metoden. Därefter kan du använda resulterande `PendingIntent` som vanligt.

### <a name="wrapped-system-services"></a>Adaptersystemtjänster
För vissa systemtjänstklasser är det nödvändigt att anropa en statisk metod för en MAM-adapterklass i stället för att direkt anropa den önskade metoden för tjänstinstansen. Till exempel måste ett anrop till `getSystemService(ClipboardManager.class).getPrimaryClip()` bli ett anrop till `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)`. Vi rekommenderar att du inte gör dessa ersättningar manuellt. Låt BuildPlugin göra dem i stället.

| Android-klass | Intune App SDK-motsvarighet |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.ContentProviderClient | MAMContentProviderClientManagement |
| android.content.ContentResolver | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| android.print.PrintManager | MAMPrintManagement |
| android.support.v4.print.PrintHelper | MAMPrintHelperManagement |
| android.view.View | MAMViewManagement |
| android.view.DragEvent | MAMDragEventManagement |

I vissa klasser är de flesta metoder omslutna, t.ex. `ClipboardManager`, `ContentProviderClient`, `ContentResolver` och `PackageManager`, medan det i andra klasser bara finns en eller två metoder som är omslutna, t.ex. `DownloadManager`, `PrintManager`, `PrintHelper`, `View` och `DragEvent`. Läs de API:er som görs tillgängliga av de MAM-motsvarande klasserna för att se de exakta metoderna om du inte använder plugin-programmet för utveckling. 

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

Ta emot MAM-loggar i din app genom att skapa en [Java-hanterare](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) och lägg till den i `MAMLogHandlerWrapper`. Detta anropar `publish()` i programhanteraren för varje loggmeddelande.

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
 * Checks whether any activities which could handle the given intent are allowed by policy. Returns false only if all
 * activities which could otherwise handle the intent are blocked. If there are no activities which could handle the intent
 * regardless of policy, returns true. If some activities are allowed and others blocked, returns true. Note that it is not
 * necessary to use this method for policy enforcement. If your app attempts to launch an intent for which there are no
 * allowed activities, MAM will display a dialog explaining the situation to the user.
 *
 * @param intent
 *         intent to check
 *
 * @return whether any activities which could handle this intent are allowed.
*/
boolean areIntentActivitiesAllowed(Intent intent);

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

Parametern `service` måste ha ett av följande `SaveLocation`-värden:


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

`username` bör vara det UPN/användarnamn/e-postmeddelande som associeras med den molntjänst som sparas till (*inte* nödvändigtvis samma som den användare som äger det dokument som sparas). Använd null om en mappning mellan AAD UPN och molntjänstens användarnamn inte finns eller om användarnamnet inte är känt.

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

* **WIPE_USER_AUXILIARY_DATA**: Appar kan registreras för det här meddelandet om man vill att Intune App SDK ska utföra standardbeteendet för selektiv rensning, men dessutom vill ta bort vissa ytterligare data när rensningen utförs. Det här meddelandet skickas inte till appar med en enda identitet – det skickas endast till appar med flera identiteter.

* **REFRESH_POLICY**: Det här meddelandet skickas i en `MAMUserNotification`. När det här meddelandet tas emot måste eventuella Intune-principbeslut som cachelagras av din app ogiltigförklaras och uppdateras. Om din app inte lagrar några principantaganden behöver den inte registrera för det här meddelandet.

* **REFRESH_APP_CONFIG**: Det här meddelandet skickas i en `MAMUserNotification`. När det här meddelandet tas emot måste cachelagrade programkonfigurationsdata ogiltigförklaras och uppdateras.

* **MANAGEMENT_REMOVED**: Det här meddelandet skickas i en `MAMUserNotification` och informerar appen att den håller på att blir ohanterad. När den är ohanterad kommer den inte längre kunna läsa krypterade filer, läsa data som krypterats med MAMDataProtectionManager, interagera med krypterade urklipp eller på annat sätt delta i ekosystemet för hanterade appar. Se ytterligare information nedan.

* **MAM_ENROLLMENT_RESULT**: Det här meddelandet skickas i en `MAMEnrollmentNotification` för att meddela appen att en APP-WE-registrering har slutförts samt för att ange statusen för det försöket.

* **COMPLIANCE_STATUS**: Det här meddelandet skickas i en `MAMComplianceNotification` för att meddela appen om resultatet av ett försök till efterlevnadsåtgärd.

> [!NOTE]
> Observera att en app aldrig ska registreras för både `WIPE_USER_DATA`- och `WIPE_USER_AUXILIARY_DATA`-meddelanden.

### <a name="managementremoved"></a>MANAGEMENT_REMOVED

`MANAGEMENT_REMOVED`-meddelandet indikerar att en tidigare principhanterad användare inte längre kommer att hanteras av Intunes MAM-princip. Detta kräver inte att användardata rensas eller att användaren loggas ut (om en rensning skulle krävas så skulle ett `WIPE_USER_DATA`-meddelande skickas). Många appar behöver kanske inte hantera det här meddelandet alls, men appar som använder `MAMDataProtectionManager` bör [särskilt beakta det här meddelandet](#data-protection).

När MAM anropar appens `MANAGEMENT_REMOVED`-mottagare kommer följande att vara sant:
* MAM har redan dekrypterat tidigare krypterade filer (men inte skyddat databuffertar) som hör till appen. Filer på offentliga platser på det SD-kort som inte hör direkt till appen (t.ex. mapparna Dokument eller Hämtade filer) dekrypteras inte.
* Nya filer eller skyddade databuffertar som skapas av mottagarmetoden (eller någon annan kod som körs efter att mottagaren börjar) krypteras inte.
* Appen har fortfarande åtkomst till krypteringsnycklar, så åtgärder såsom dekryptering av databuffertar lyckas.

När appens mottagare returneras har den inte längre åtkomst till krypteringsnycklar.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Konfigurera Azure Active Directory Authentication Library (ADAL)

Läs först riktlinjerna för ADAL-integrering som finns i [ADAL- lagringsplatsen på GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-android).

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

* **ClientID** är det AAD-ClientID (även kallat program-ID) som ska användas. Du bör använda din egen apps ClientID, om det är registrerat i Azure AD. Om detta värde saknas används ett Intune-standardvärde.

* **NonBrokerRedirectURI** är AAD:ns omdirigerings-URI som används när det inte finns någon asynkron meddelandekö. Om inget anges används standardvärdet för `urn:ietf:wg:oauth:2.0:oob`. Standardinställningen är lämplig för de flesta appar.

    * NonBrokerRedirectURI används endast när SkipBroker är ”sant”.

* **SkipBroker** används för att åsidosätta standardbeteendet för ADAL SSO-deltagande. SkipBroker bör endast anges för appar som specificerar ett ClientID **och** inte har stöd för asynkron autentisering/enhetsomfattande enkel inloggning. I det här fallet bör det ställas in på ”sant”. De flesta appar bör inte ange parametern SkipBroker.

    * Ett ClientID **måste** anges i manifestet för att ange ett SkipBroker-värde.

    * När ett ClientID anges är standardvärdet ”falskt”.

    * När SkipBroker är ”sant” används NonBrokerRedirectURI. Appar som inte integrerar ADAL (och därför inte har något ClientID) får också ”sant” som standard.

### <a name="common-adal-configurations"></a>Vanliga ADAL-konfigurationer

Nedan visas några vanliga sätt att konfigurera en app med ADAL. Hitta din appkonfiguration och ange ADAL-metadataparametrarna (förklaras ovan) till de värden som krävs. Om du vill kan du i samtliga fall ange auktoriteten för icke-förvalda miljöer. Om den inte anges används den offentliga AAD-produktionsauktoriteten.

#### <a name="1-app-does-not-integrate-adal"></a>1. Appen integrerar inte ADAL
ADAL-metadata **får inte** finnas i manifestet.

#### <a name="2-app-integrates-adal"></a>2. Appen integrerar ADAL

|ADAL-parameter som krävs| Värde |
|--|--|
| ClientID | Appens ClientID (genereras av Azure AD när appen registreras) |

Auktoriteten kan anges om det behövs.

Du måste registrera din app med Azure AD och ge appen åtkomst till appens tjänst för skyddsprincip:
* Information om hur du registrerar ett program med Azure AD finns [här](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).
* Se till att stegen som ger din Android appbehörigheter till APP-tjänsten följs. Följ instruktionerna i guiden [Komma igång med Intune-SDK:n](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) under ”Ge din app åtkomst till Intune-appskyddstjänsten (valfritt)”. 

Se även kraven för [villkorlig åtkomst](#conditional-access) nedan.


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. Appen integrerar ADAL men saknar stöd för asynkron autentisering/enhetsomfattande enkel inloggning

|ADAL-parameter som krävs| Värde |
|--|--|
| ClientID | Appens ClientID (genereras av Azure AD när appen registreras) |
| SkipBroker | **True** |

Authority och NonBrokerRedirectURI kan anges om det behövs.

### <a name="conditional-access"></a>Villkorlig åtkomst

Villkorlig åtkomst (CA) är en [funktion](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer) i Azure Active Directory som kan användas för att kontrollera åtkomsten till AAD-resurser. [Intune-administratörer kan definiera regler för villkorlig åtkomst](https://docs.microsoft.com/intune/conditional-access) som endast tillåter åtkomst till resurser från enheter eller appar som hanteras av Intune. Följ stegen nedan för att säkerställa att din app kan komma åt resurser när det behövs. Om din app inte använder AAD-åtkomsttoken, eller om den endast kommer åt resurser som inte kan skyddas med villkorlig åtkomst (CA), kan du hoppa över de här stegen.

1. Följ [riktlinjerna för ADAL-integration](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library). 
   Se särskilt steg 11 för Broker-användning.
2. [Registrera ditt program med Azure Active Directory] (https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). 
   Omdirigerings-URI finns i riktlinjerna för ADAL-integrering ovan.
3. Ange manifestets metadataparametrar enligt informationen under punkt 2 i avsnittet [Vanliga ADAL-konfigurationer](#common-adal-configurations) ovan.
4. Testa att allt är korrekt konfigurerat genom att aktivera [enhetsbaserad villkorlig åtkomst](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) på [Azure-portalen](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2) och bekräfta
    - att inloggningen i din app begär installation och registrering av Intune-företagsportalen
    - att inloggningen till appen fungerar korrekt efter registreringen.
5. När din app har skickat Intune APP SDK-integrering till produktion kontaktar du msintuneappsdk@microsoft.com så lägger vi till din app i listan med godkända appar för [appbaserad villkorlig åtkomst](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)
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

3. När ett användarkonto tas bort, bör appen anropa `unregisterAccountForMAM()` för att ta bort kontot från Intune-hanteringen.

    > [!NOTE]
    > Om en användare loggar ut från appen tillfälligt, behöver appen inte anropa `unregisterAccountForMAM()`. Anropet kan starta en rensning för att ta bort samtliga företagsdata för användaren.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

Alla nödvändiga autentiserings- och registrerings-API:er finns i `MAMEnrollmentManager`-gränssnittet. En referens till `MAMEnrollmentManager` kan hämtas på följande sätt:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

Den returnerade `MAMEnrollmentManager`-instansen kommer garanterat inte vara null. API-metoderna är indelade i två kategorier: **autentisering** och **kontoregistrering**.

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

    > [!NOTE]
    > Se till att din app använder de `resourceId`- och `aadId`-parametrar som skickas till `acquireToken()` så att rätt token hämtas.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
        return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. Om appen inte kan ange en token när SDK anropar `acquireToken()` – till exempel om tyst autentisering misslyckas och det är olämpligt att visa ett UI – kan appen hämta en token vid ett senare tillfälle genom att anropa `updateToken()`-metoden. Samma UPN, AAD-ID och resurs-ID som begärdes av föregående anrop till `acquireToken()` måste skickas till `updateToken()`, tillsammans med den token som slutligen anskaffades. Appen ska anropa den här metoden så snart som möjligt efter att ha returnerat null från motringningen.

    > [!NOTE]
    > SDK:n anropar `acquireToken()` regelbundet för att hämta denna token, så att anropa `updateToken()` är inte nödvändigt. Det rekommenderas dock starkt som hjälp vid registreringar och incheckningar till appskyddsprincipen för att de ska slutföras inom rimlig tid.


### <a name="account-registration"></a>Kontoregistrering

I det här avsnittet beskrivs kontoregistreringens API-metoder i `MAMEnrollmentManager` och hur de används.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Om du vill registrera ett hanteringskonto ska appen anropa `registerAccountForMAM()`. Ett användarkonto identifieras av både sitt UPN och sitt användar-ID för AAD. Klient-ID krävs dessutom för att associera registreringsdata med användarens AAD-klient. Användarens behörighet kan även anges för att tillåta registrering mot specifika nationella moln. Mer information finns i avsnittet [Registrering av nationella moln](#sovereign-cloud-registration).  SDK kan försöka registrera appen för angiven användare i MAM-tjänsten. Om registreringen misslyckas görs nya försök regelbundet tills kontot är avregistrerat. Återförsöksperioden är vanligtvis 12–24 timmar. SDK:n innehåller statusen för registreringsförsöken via meddelanden asynkront.

2. Eftersom AAD-autentisering krävs, är den bästa tiden att registrera användarkontot när användaren har loggat in i appen och har autentiserats med hjälp av ADAL. Användarens AAD-ID och klientorganisations-ID returneras från ADAL-autentiseringsanropet som en del av [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android)-objektet.
    * Klientens ID kommer från `AuthenticationResult.getTenantID()`-metoden.
    * Information om användaren finns i ett underobjekt av typen `UserInfo` som kommer från `AuthenticationResult.getUserInfo()`, och AAD-användarens ID hämtas från detta objekt genom att anropa `UserInfo.getUserId()`.

3. Om du vill avregistrera ett konto från Intune-hanteringen, ska appen anropa `unregisterAccountForMAM()`. Om kontot har registrerats och hanteras, avregistrerar SDK:n kontot och rensar dess data. Regelbundna återförsök att registrera kontot kommer att stoppas. SDK:n innehåller statusen för avregistreringsbegärandet via meddelanden asynkront.

### <a name="sovereign-cloud-registration"></a>Registrering av nationella moln

Program som är [kopplade till nationella moln](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) **måste** ange `authority` till `registerAccountForMAM()`.  Det gör du genom att ange `instance_aware=true` i ADAL:s [1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) acquireToken extraQueryParameters följt av ett anrop till `getAuthority()` på AuthenticationCallback AuthenticationResult.

```java
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
> Ange inte metadataobjektet `com.microsoft.intune.mam.aad.Authority` i AndroidManifest.xml.

> [!NOTE]
> Kontrollera att auktoriteten har angetts korrekt i `MAMServiceAuthenticationCallback::acquireToken()`-metoden.

#### <a name="currently-supported-sovereign-clouds"></a>Nationella moln som stöds för närvarande

1. Arlington

### <a name="important-implementation-notes"></a>Viktiga implementeringskommentarer

#### <a name="authentication"></a>Autentisering

* När appen anropar `registerAccountForMAM()` kan den få en motringning till sitt `MAMServiceAuthenticationCallback`-gränssnitt strax därefter i en annan tråd. Vi rekommenderar att appen hämtar sin egen token från ADAL innan kontot registreras för att påskynda hämtningen av den begärda token. Om appen returnerar en giltig token från motringningen fortsätter registreringen, och appen får slutresultatet via ett meddelande.

* Om programmet inte returnerar en giltig AAD-token, blir slutresultatet från registreringsförsöket `AUTHENTICATION_NEEDED`. Om appen tar emot resultatet via ett meddelande rekommenderas det starkt att registreringsprocessen påskyndas genom att token för användaren och den resurs som tidigare begärts från `acquireToken()` hämtas och metoden `updateToken()` anropas så att registreringsprocessen initieras igen.

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

Om appen registreras för meddelanden av typen **MAM_ENROLLMENT_RESULT** skickas ett `MAMEnrollmentNotification` för att informera appen om att registreringsbegärandet har slutförts. `MAMEnrollmentNotification` tas emot via `MAMNotificationReceiver`-gränssnittet enligt beskrivningen i avsnittet [Registrera för meddelanden från SDK:n](#register-for-notifications-from-the-sdk).

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

`getEnrollmentResult()`-metoden returnerar resultatet av registreringsbegäran.  Eftersom `MAMEnrollmentNotification` utökar `MAMUserNotification`, är identiteten för den användare som registreringen gjordes för också tillgänglig. Appen måste implementera `MAMNotificationReceiver`-gränssnittet för att kunna ta emot dessa meddelanden, enligt beskrivningen i [Registrera för meddelanden från SDK:n](#register-for-notifications-from-the-sdk).

Det registrerade användarkontots status kan ändras när ett registreringsmeddelande tas emot, men det är inte alltid som den ändras (t.ex. om meddelandet `AUTHORIZATION_NEEDED` har tagits emot efter ett mer informativt resultat som `WRONG_USER` kommer det mer informativa resultatet att behållas som kontots status).  När kontot har registrerats förblir statusen `ENROLLMENT_SUCCEEDED` tills kontot avregistreras eller rensas.

Det registrerade användarkontots status kan ändras när ett registreringsmeddelande tas emot, men det är inte alltid som den ändras (t.ex. om meddelandet `AUTHORIZATION_NEEDED` har tagits emot efter ett mer informativt resultat som `WRONG_USER` kommer det mer informativa resultatet att behållas som kontots status).  När kontot har registrerats förblir statusen `ENROLLMENT_SUCCEEDED` tills kontot avregistreras eller rensas.

## <a name="app-ca-with-policy-assurance"></a>APP CA med principbekräftelse

### <a name="overview"></a>Översikt
Med APP CA (villkorsstyrd åtkomst) med principbekräftelse villkoras åtkomst till resurser av tillämpningen av Intune-appskyddsprinciper.  AAD framtvingar detta genom att kräva att appen registreras och hanteras av APP innan en token ges för åtkomst till en APP CA med en resurs som skyddas av principbekräftelse.  Appen måste använda ADAL-hanteraren för tokenförvärv, och konfigurationen är densamma som ovanstående beskrivning i [Villkorsstyrd åtkomst](#conditional-access)

### <a name="adal-changes"></a>ADAL-ändringar
ADAL-biblioteket har en ny felkod som informerar appen om att misslyckandet med att hämta en token orsakades av bristande efterlevnad med APP-hantering.  Om appen får den här felkoden behöver den anropa SDK:n för att försöka åtgärda efterlevnad genom att registrera appen och tillämpa en princip. Ett undantag tas emot av metoden `onError()` i `AuthenticationCallback` för ADAL och har felkoden `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  I det här fallet kan undantaget typkonverteras till ett `IntuneAppProtectionPolicyRequiredException`, varifrån ytterligare parametrar kan extraheras för användning vid åtgärd av efterlevnad (se kodexemplet nedan). När åtgärden har genomförts kan appen på nytt försöka att hämta token via ADAL.

> [!NOTE]
> Den här nya felkoden och annat stöd för APP CA med principbekräftelse kräver version 1.15.0 (eller senare) av ADAL-biblioteket.

### <a name="mamcompliancemanager"></a>MAMComplianceManager

`MAMComplianceManager`-gränssnittet används när det fel som krävs av principen tas emot från ADAL.  Det innehåller den `remediateCompliance()`-metod som bör användas för att försöka placera appen i ett efterlevande tillstånd. En referens till `MAMComplianceManager` kan hämtas på följande sätt:

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

Den returnerade `MAMComplianceManager`-instansen kommer garanterat inte vara null.

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

Metoden `remediateCompliance()` anropas i ett försök att placera appen under hantering för att uppfylla kraven för att ADD ska bevilja den begärda token.  De första fyra parametrarna kan extraheras från det undantag som tas emot av metoden `AuthenticationCallback.onError()` i ADAL (se kodexemplet nedan).  Den sista parametern är ett booleskt värde som kontrollerar huruvida ett UX visas under efterlevnadsförsöket.  Det här är ett enkelt gränssnitt för förloppsblockering som tillhandahålls som standard för appar som inte behöver visa ett anpassat UX under den här åtgärden.  Det blockerar endast medan efterlevnadsåtgärden pågår och visar inte slutresultatet.  Appen bör registrera en meddelandemottagare för att hantera det lyckade eller misslyckade försöket till efterlevnadsåtgärd (se nedan).

Metoden `remediateCompliance()` kan utföra en MAM-registrering som en del av att upprätta efterlevnad.  Appen kan få ett registreringsmeddelande om den har registrerat en meddelandemottagare för registreringsmeddelanden.  Appens registrerade `MAMServiceAuthenticationCallback` får sin metod `acquireToken()` anropad för att hämta en token för MAM-registreringen. `acquireToken()` anropas innan appen har hämtat sin egen token. Därför kan det hända att eventuella uppgifter för bokföring eller kontoskapande som appen utför efter ett lyckat tokenförvärv inte är klara ännu.  Återanropet måste kunna hämta en token i det här fallet.  Om du inte kan returnera en token från `acquireToken()` misslyckas försöket till efterlevnadsåtgärd.  Om du anropar `updateToken()` senare med en giltig token för den begärda resursen görs ett nytt försök av efterlevnadsåtgärden omedelbart med den skickade token.

> [!NOTE]
> Tyst tokenförvärv är fortfarande möjligt i `acquireToken()` eftersom användaren redan kommer att ha vägletts att installera hanteraren och registrera enheten innan `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`-felet tas emot.  Detta resulterar i att hanteraren har en giltig uppdateringstoken i sin cache, vilket möjliggör att tyst förvärv av den begärda token kan lyckas.

Här följer ett exempel på mottagande av det fel som krävs av principen i metoden `AuthenticationCallback.onError()` och anrop till `MAMComplianceManager` för att hantera felet.

```java
public void onError(@Nullable Exception exc) {
    if (exc instanceof AuthenticationException && 
        ((AuthenticationException) exc).getCode() == ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED) {

        final IntuneAppProtectionPolicyRequiredException policyRequiredException = 
            (IntuneAppProtectionPolicyRequiredException) ex;

        final String upn = policyRequiredException.getAccountUpn();
        final String aadId = policyRequiredException.getAccountUserId();
        final String tenantId = policyRequiredException.getTenantId();
        final String authority = policyRequiredException.getAuthorityURL();

        MAMComplianceManager complianceManager = MAMComponents.get(MAMComplianceManager.class);
        complianceManager.remediateCompliance(upn, aadId, tenantId, authority, showUX);
    }
}
```

### <a name="status-notifications"></a>Statusmeddelanden

Om appen registreras för meddelanden av typen **COMPLIANCE_STATUS** skickas ett `MAMComplianceNotification` för att informera appen om den slutgiltiga statusen för försöket till efterlevnadsåtgärd. `MAMComplianceNotification` tas emot via `MAMNotificationReceiver`-gränssnittet enligt beskrivningen i avsnittet [Registrera för meddelanden från SDK:n](#register-for-notifications-from-the-sdk).

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

Metoden `getComplianceStatus()` returnerar resultatet av försöket till efterlevnadsåtgärd som ett värde från `MAMCAComplianceStatus`-uppräkningen.

|Statuskod | Förklaring |
| -- | -- |
| UNKNOWN | Statusen är okänd. Detta kan tyda på en oväntad felorsak. Mer information kan finnas i företagsportalens loggar. |
| COMPLIANT | Efterlevnadsåtgärden lyckades, och appen efterlever nu principen. ADAL-tokenförvärvet bör försökas igen. |
| NOT_COMPLIANT | Försöket till efterlevnadsåtgärd misslyckades.  Appen efterlever inte, och ADAL-tokenförvärvet bör inte försökas på nytt förrän feltillståndet har korrigerats.  Ytterligare felinformation skickas med MAMComplianceNotification. |
| SERVICE_FAILURE | Ett fel uppstod vid försök att hämta efterlevnadsdata från Intune-tjänsten. Mer information kan finnas i företagsportalens loggar. |
| NETWORK_FAILURE | Det uppstod ett fel vid anslutning till Intune-tjänsten. Appen bör försöka sitt tokenförvärv igen när nätverksanslutningen har återställts. |
| CLIENT_ERROR | Försöket till efterlevnadsåtgärd misslyckades av någon anledning som är relaterad till klienten.  Det kan till exempel handla om saknad token eller fel användare. Ytterligare felinformation skickas med MAMComplianceNotification. |
| PENDING | Försöket till efterlevnadsåtgärd misslyckades eftersom statussvaret inte ännu hade tagits emot från tjänsten när tidsgränsen nåddes. Appen bör försöka sitt tokenförvärv igen senare. |
| COMPANY_PORTAL_REQUIRED | Företagsportalen måste installeras på enheten för att efterlevnadsåtgärden ska lyckas.  Om företagsportalen redan är installerad på enheten behöver appen startas om.  I det här fallet visas en dialogruta där användaren uppmanas att starta om appen. |

Om efterlevnadsstatusen är `MAMCAComplianceStatus.COMPLIANT` bör appen återinitiera sitt ursprungliga tokenförvärv (för dess egen resurs). Om försöket till efterlevnadsåtgärd misslyckades returnerar metoderna `getComplianceErrorTitle()` och `getComplianceErrorMessage()` lokaliserade strängar som appen kan visa för slutanvändaren om den väljer att göra det.  De flesta fall av fel kan inte åtgärdas av appen. För det allmänna fallet kan det därför vara bäst att misslyckas med kontoskapandet och låt användaren försöka igen senare.  Om ett fel är beständigt kan MAM-loggarna vara till hjälp för att ta reda på orsaken.  Slutanvändaren kan skicka loggarna med hjälp av de anvisningar som finns [här](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "Skicka loggar till företagets support via e-post").

Eftersom `MAMComplianceNotification` utökar `MAMUserNotification` är identiteten för den användare som åtgärden försöktes för också tillgänglig.

Här är ett exempel på registrering av en mottagare med hjälp av en anonym klass för att implementera MAMNotificationReceiver-gränssnittet:

```java
final MAMNotificationReceiverRegistry notificationRegistry = MAMComponents.get(MAMNotificationReceiverRegistry.class);
// create a receiver
final MAMNotificationReceiver receiver = new MAMNotificationReceiver() {
    public boolean onReceive(MAMNotification notification) {
        if (notification.getType() == MAMNotificationType.COMPLIANCE_STATUS) {
            MAMComplianceNotification complianceNotification = (MAMComplianceNotification) notification;
            
            // take appropriate action based on complianceNotification.getComplianceStatus()
            
            // unregister this receiver if no longer needed
            notificationRegistry.unregisterReceiver(this, MAMNotificationType.COMPLIANCE_STATUS);
        }
        return true;
    }
};
// register the receiver
notificationRegistry.registerReceiver(receiver, MAMNotificationType.COMPLIANCE_STATUS);
```

> [!NOTE]
> Meddelandemottagaren måste registreras innan anrop sker till `remediateCompliance()` för att undvika ett konkurrenstillstånd som kan resultera i att meddelandet förbises.

### <a name="implementation-notes"></a>Implementeringsanteckningar

> [!NOTE]
> Appens `MAMServiceAuthenticationCallback.acquireToken()`-metod måste skicka *sant* för den nya `forceRefresh`-flaggan till `acquireTokenSilentSync()` för att framtvinga en uppdatering från hanteraren.  Detta görs för att undvika ett cachelagringsproblem med token i ADAL som kan påverka MAM-tjänsttoken. I allmänhet ser det ut så här:
```java
AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ true);
```

> [!NOTE]
> Om du vill visa ett UX för anpassad blockering under åtgärdsförsöket skickar du *falskt* för showUX-parametern till `remediateCompliance()`. Du måste se till att du visar ditt UX och registrerar meddelandeavlyssnaren först innan du anropar `remediateCompliance()`.  Detta förhindrar ett konkurrenstillstånd där meddelandet kan förbises om `remediateCompliance()` misslyckas mycket snabbt.  Till exempel är metoden `onCreate()` eller `onMAMCreate()` i en Activity-underklass det perfekta stället att registrera meddelandeavlyssnaren och sedan anropa `remediateCompliance()`.  Parametrarna för `remediateCompliance()` kan skickas till ditt UX som Intent-tillägg (avsikt).  När meddelandet om efterlevnadsstatus har tagits emot kan du visa resultatet eller helt enkelt slutföra aktiviteten.

> [!NOTE]
> `remediateCompliance()` registrerar kontot och försöker registrera.  När den huvudsakliga token förvärvas är det inte nödvändigt att anropa `registerAccountForMAM()`, men det skadar inte att göra det. Om appen å andra sidan misslyckas med att förvärva sin token och vill ta bort användarkontot måste den anropa `unregisterAccountForMAM()` för att ta bort kontot och förhindra återförsök av registreringar i bakgrunden.

## <a name="protecting-backup-data"></a>Skydda säkerhetskopierade data

Från och med Android Marshmallow (API-23) kan en app säkerhetskopiera data på två sätt. Alla alternativ är tillgängliga för din app och kräver olika steg för att säkerställa att Intune-dataskyddet har implementerats korrekt. Tabellen nedan innehåller information om relevanta åtgärder som krävs för korrekt dataskydd.  Du kan läsa mer om säkerhetskopieringsmetoderna i [Android API-guiden](https://developer.android.com/guide/topics/data/backup.html).

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
Som standard tillämpar Intune App SDK principer på appen i sin helhet. Flera identiteter är en valfri Intune-funktion för appskydd som kan aktiveras för att tillåta att principer tillämpas per identitet. Detta kräver mycket större appmedverkan än andra appskyddsfunktioner.

> [!NOTE]
>  Om appen inte deltar på rätt sätt kan det resultera i dataläckage och andra säkerhetsproblem.

När användaren registrerar enheten eller appen, registrerar SDK:n den identiteten och ser den som den primära Intune-hanterade identiteten. Andra användare i appen behandlas som ohanterade med obegränsade principinställningar.

> [!NOTE]
> För närvarande stöds endast en Intune-hanterad identitet per enhet.

En identitet definieras som en sträng. Identiteter är **skiftlägesokänsliga** och en begäran till SDK:n om en identitet kanske inte returnerar samma gemener och versaler som användes när identiteten skapades.

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
  2. Nivån `Context` (vanligtvis `Activity`)
  3. Processnivå

En identitet som anges på trådnivå åsidosätter en identitet som angetts på `Context`-nivå, som i sin tur åsidosätter en identitet som angetts på processnivå. En identitet som angetts för en `Context` används endast i lämpliga associerade scenarier. Exempelvis har filrelaterade I/O-åtgärder ingen associerad `Context`. Oftast anger appar `Context`-identiteten för en `Activity`. En app *måste* inte visa data för en hanterad identitet såvida inte `Activity`-identiteten är inställd på samma identitet. I allmänhet är processnivåidentiteten bara användbar om appen endast arbetar med en enskild användare åt gången på alla trådar. Många appar behöver kanske inte använda den.

Om din app använder `Application`-kontexten för att hämta systemtjänster bör du se till att tråden eller processidentiteten har angetts eller att du har angett UI-identiteten i din apps `Application`-kontext.

För hantering av specialfall vid uppdatering av UI-identiteten med `setUIPolicyIdentity` eller `switchMAMIdentity` kan båda metoderna skickas som en uppsättning `IdentitySwitchOption`-värden.

* `IGNORE_INTENT`: Använd om du begär en identitetsväxling som ska ignorera den avsikt som är associerad med den aktuella aktiviteten.
  Exempel:

  1. Appen tar emot en avsikt från en hanterad identitet som innehåller ett hanterat dokument, och appen visar dokumentet.
  2. Användaren växlar till sin personliga identitet, så appen begär en UI-identitetsväxling. I den personliga identiteten visar din app inte längre dokumentet, så du använder `IGNORE_INTENT` när du begär identitetsväxlingen.

  Om detta inte anges antar SDK:n att den senaste avsikten fortfarande används i appen. Detta gör att hämtningsprincipen för den nya identiteten behandlar avsikten som inkommande data och använder dess identitet.

>[!NOTE]
> Eftersom `CLIPBOARD_SERVICE` används för gränssnittsåtgärder använder SDK: förgrundsaktivitetens UI-identitet för `ClipboardManager`-åtgärder.
> Följande metoder i `MAMPolicyManager` kan användas för att ange identiteten och hämta de identitetsvärden som angavs tidigare.

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

Appen bör se till att en identitetsväxling har lyckats innan den visar eller använder företagsdata. Process- och identitetväxlingar lyckas för närvarande alltid för appar med flera identiteter, men vi förbehåller oss rätten att lägga till feltillstånd. Identitetsväxlingen i gränssnittet kan misslyckas på grund av ogiltiga argument, om den skulle hamna i konflikt med trådidentiteten eller om användaren avbryter på grund av villkorliga startkrav (t.ex. trycker på bakåtknappen på PIN-skärmen).


När en kontextidentitet anges rapporteras resultatet asynkront. Om kontexten är en aktivitet vet SDK:n inte om identitetsändringen lyckades förrän efter att en villkorlig start har utförts. Den kan kräva att användaren anger en PIN-kod eller företagets autentiseringsuppgifter. Appen förväntas implementera en `MAMSetUIIdentityCallback` för att ta emot det här resultatet och du kan skicka null för den här parametern.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

Du kan också ange identiteten för en aktivitet direkt via en metod i `MAMActivity`, i stället för att anropa `MAMPolicyManager.setUIPolicyIdentity`. Använd följande metod för att göra detta:

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

Du kan även åsidosätta en metod i `MAMActivity` om du vill att appen ska aviseras om resultatet vid försök att ändra identiteten för aktiviteten.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

Om du inte åsidosätter `onSwitchMAMIdentityComplete` (eller anropar metoden `super`) resulterar en misslyckad identitetsväxling i en aktivitet i att aktiviteten slutförs. Om du åsidosätter metoden måste du se till att företagsdata inte visas efter en misslyckad identitetsväxling.

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

    Där ```AppIdentitySwitchResult``` är antingen `SUCCESS` eller `FAILURE`.

Metoden `onMAMIdentitySwitchRequired` anropas för alla implicita identitetsändringar utom för de som görs via en Binder som returneras från `MAMService.onMAMBind`. Standardimplementeringar av omedelbart anrop för `onMAMIdentitySwitchRequired`:

* `reportIdentitySwitchResult(FAILURE)` när orsaken är `RESUME_CANCELLED`.

* `reportIdentitySwitchResult(SUCCESS)` i alla andra fall.

  De flesta appar behöver inte blockera eller fördröja en identitetsväxling på andra sätt, men om en app måste göra det är det viktigt att ha följande i åtanke:

  * Om en identitetsväxling blockeras är resultatet är samma som om delningsinställningar i `Receive` hade förbjudit inkommande data.

  * Om en tjänst körs på huvudtråden **måste** `reportIdentitySwitchResult` anropas synkront, annars låser sig UI-tråden.

  * För **`Activity`** -generering anropas `onMAMIdentitySwitchRequired` före `onMAMCreate`. Om appen måste visa ett användargränssnitt för att avgöra om identitetsväxlingen ska tillåtas eller inte, måste användargränssnittet visas med hjälp av en *annan* aktivitet.

  * I en **`Activity`** , om en växling till den tomma identiteten begärs med orsaken `RESUME_CANCELLED` måste appen ändra den återupptagna aktiviteten för att visa data som är konsekventa med identitetsväxlingen.  Om detta inte är möjligt bör appen avvisa växlingen och användaren uppmanas på nytt att följa principen för identiteten som ska återupptas (t.ex. genom att en skärm för inmatning av appens PIN-kod visas).

    > [!NOTE]
    > En app med flera identiteter tar alltid emot inkommande data från både hanterade och ohanterade appar. Det är appens ansvar att behandla data från hanterade identiteter på ett hanterat sätt.

  Om en begärd identitet hanteras (använd `MAMPolicyManager.getIsIdentityManaged` för att kontrollera), men appen inte kan använda det kontot (t.ex. eftersom bl.a. e-postkonton måste konfigureras i appen först), bör identitetsväxlingen avvisas.

#### <a name="build-plugin--tool-considerations"></a>Att tänka på när du använder plugin-programmet eller verktyget för utveckling
Om du inte uttryckligen ärver från `MAMActivity`, `MAMService`, eller `MAMContentProvider` (eftersom du tillåter att utvecklingsverktyg gör den ändringen), men fortfarande behöver bearbeta identitetsväxlingar kan du i stället implementera `MAMActivityIdentityRequirementListener` (för en `Activity`) eller `MAMIdentityRequirementListener` (för en `Service` eller `ContentProviders`).
Standardbeteendet för `MAMActivity.onMAMIdentitySwitchRequired` kan nås genom anrop till den statiska metoden `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)`.

Om du vill åsidosätta `MAMActivity.onSwitchMAMIdentityComplete` kan du på motsvarande sätt implementera `MAMActivityIdentitySwitchListener` utan att uttryckligen ärva från `MAMActivity`.

### <a name="preserving-identity-in-async-operations"></a>Bevara identitet i asynkrona åtgärder
Det är vanligt att åtgärder i UI-tråden skickar bakgrundsaktiviteter till en annan tråd. En app med flera identiteter vill se till att de här bakgrundsaktiviteterna fungerar med rätt identitet, vilken ofta är samma identitet som används av aktiviteten som skickade ut dem. MAM SDK:n innehåller `MAMAsyncTask` och `MAMIdentityExecutors` för att göra det enklare att bevara identiteten.
Dessa måste användas om den asynkrona åtgärden skulle kunna företagsdata till en fil eller kommunicera med andra appar.

#### <a name="mamasynctask"></a>MAMAsyncTask

Om du vill använda `MAMAsyncTask` kan du helt enkelt ärva från den i stället för `AsyncTask` och ersätta åsidosättningar av `doInBackground` och `onPreExecute` med `doInBackgroundMAM` respektive `onPreExecuteMAM`. Konstruktorn `MAMAsyncTask` tar ett aktivitetssammanhang. Exempel:

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
    * Protect a file or directory. This will synchronously trigger whatever protection is required for the file, and will tag the
    * file for future protection changes. If an identity is set on a directory, it is set recursively on all files and
    * subdirectories. New files or directories will inherit their parent directory's identity. If MAM is operating in offline mode,
    * this method will silently do nothing.
    *
    * @param identity
    *       Identity to set.
    * @param file
    *       File to protect.
    *
    * @throws IOException
    *       If the file cannot be protected.
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
  * Användaren väljer ett dokument att öppna i appen.
  * Under öppningsflödet innan läsning av data från disken, bekräftar appen identiteten som ska användas för att visa innehållet
    * MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
    * if(info)   MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback)
    * Appen väntar tills resultatet rapporteras till återanrop
    * Om det rapporterade resultatet är ett fel kommer appen inte att visa dokumentet.
  * Appen öppnar och renderar filen.
  
#### <a name="single-identity-to-multi-identity-transition"></a>Övergång från enskild identitet till flera identiteter
Om en app som tidigare lanserats med Intune-integrering med enskild entitet senare integrerar flera identiteter kommer tidigare installerade appar att genomgå en övergång (detta syns inte för användaren eftersom det inte finns något relaterat UX). Appen måste *inte* uttryckligen göra något för att hantera den här övergången. Alla filer som skapas före övergången fortsätter att betraktas som hanterade (därför förblir de krypterade om krypteringsprincipen är aktiv). Om du vill kan du identifiera uppgraderingen och använda `MAMFileProtectionManager.protect` för att tagga specifika filer eller kataloger med den tomma identiteten (vilket tar bort krypteringen om de var krypterade).

#### <a name="offline-scenarios"></a>Offline-scenarier

Filidentitetstaggningen känner av offlineläget. Ha följande i åtanke:

  * Om företagsportalen inte är installerad kan du inte tagga filer med identiteter.

  * Om företagsportalen är installerad, men appen saknar Intune MAM-principen, kan principerna inte taggas med identiteten på ett tillförlitligt sätt.

  * När filidentitetstaggning blir tillgängligt behandlas alla tidigare skapade filer som personliga/ohanterade (tillhör identiteten med en tom sträng), om inte appen redan har installerats som en hanterad app med en enda identitet. Då anses den tillhöra den registrerade användaren.

### <a name="directory-protection"></a>Katalogskydd

Kataloger kan skyddas med samma `protect`-metod som används för att skydda filer. Katalogskydd tillämpas rekursivt på alla filer och underkataloger i katalogen samt på nya filer som skapas i katalogen. Eftersom katalogskydd tillämpas rekursivt kan det ta en stund att slutföra `protect`-anropet för stora kataloger. Därför kan det vara bättre att appar som använder skydd på en katalog som innehåller ett stort antal filer, kör `protect` asynkront i en bakgrundstråd.

### <a name="data-protection"></a>Dataskydd

Det går inte att tagga en fil som om den tillhörde flera identiteter. Appar som måste lagra data som tillhör olika användare i samma fil, kan göra detta manuellt med hjälp av de funktioner som finns i `MAMDataProtectionManager`. På så sätt kan programmet kryptera data och koppla dem till en viss användare. Krypterade data är lämpligt för lagring till disk i en fil. Du kan köra frågor mot data som är associerade med identiteten, och dekryptera dessa data senare.

Appar som använder `MAMDataProtectionManager` bör implementera en mottagare av `MANAGEMENT_REMOVED`-meddelandet. När det här meddelandet är klart kan buffertar som skyddades via den här klassen inte längre läsas om filkryptering aktiverades när buffertarna skyddades. En app kan åtgärda detta genom att anropa `MAMDataProtectionManager.unprotect` på alla buffertar under meddelandet. Det är också säkert att anropa skyddet under det här meddelandet om man önskar bevara identitetsinformation – kryptering inaktiveras under meddelandet.


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

Om appen innehåller andra företagsdata än en `ParcelFileDescriptor` via en `ContentProvider` måste appen anropa metoden `isProvideContentAllowed(String)` i `MAMContentProvider` och skicka ägaridentitetens UPN (användarens huvudnamn) för innehållet. Om den här funktionen returnerar false *får inte* innehållet returneras till anroparen. Filbeskrivningar som returneras via en innehållsprovider hanteras automatiskt baserat på filidentiteten.

Om du inte explicit ärver `MAMContentProvider` och i stället låter utvecklingsverktyget göra den ändringen kan du anropa en statisk version av samma metod: `MAMContentProvider.isProvideContentAllowed(provider, contentIdentity)`.

### <a name="selective-wipe"></a>Selektiv rensning

Om en app med flera identiteter registreras för `WIPE_USER_DATA`-meddelandet är det appens ansvar att ta bort alla data för användaren som rensas, inklusive alla filer som har identitetsmärkts som tillhörande användaren i fråga. Om appen tar bort användardata från en fil, men vill lämna andra data i filen, *måste* identiteten för filen ändras (via `MAMFileProtectionManager.protect` till en personlig användare eller en tom identitet). Om krypteringsprincipen används dekrypteras inga eventuella återstående filer som hör till användare som tas bort, och de blir otillgängliga för appen efter rensningen.

En appregistrering för `WIPE_USER_DATA` kan inte dra nytta av standardbeteendet för selektiv rensning i SDK:n. För appar som kan hantera flera identiteter kan denna förlust vara mer betydelsefull, eftersom en selektiv standardrensning med MAM endast rensar filer vars identitet ska rensas. Om ett program som kan hantera flera identiteter önskar att MAM:s selektiva standardrensning ska göras _**och**_ vill utföra egna åtgärder för rensningen, måste det registrera sig för `WIPE_USER_AUXILIARY_DATA`-meddelanden. Det här meddelandet skickas omedelbart av SDK:n innan den utför MAM:s selektiva standardrensning. En app bör aldrig registreras för både `WIPE_USER_DATA` och `WIPE_USER_AUXILIARY_DATA`.

Den selektiva standardrensningen stänger appen korrekt, vilket avslutar aktiviteter och stänger av appens process. Om din app åsidosätter den selektiva standardrensningen bör du överväga att stänga appen manuellt för att förhindra att användaren kommer åt data i minnet efter att en rensning sker.


## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Aktivera MAM-riktad konfiguration för Android-appar (valfritt)
Programspecifika nyckel/värde-par kan konfigureras i Intune-konsolen för [MAM-WE](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) och [Android-arbetsprofilappar](https://docs.microsoft.com/intune/app-configuration-policies-use-android).
Dessa nyckel-/värdepar tolkas inte av Intune utan skickas till appen. Program som ska ta emot sådan konfiguration kan använda klasserna `MAMAppConfigManager` och `MAMAppConfig` för detta. Om flera principer är inriktade på samma app kan det finnas flera motstridiga värden för samma nyckel.

> [!NOTE] 
> Konfiguration för leverans via MAM-WE kan inte levereras i `offline`.  Endast Android Enterprise AppRestrictions levereras ett `MAMUserNotification` på en tom identitet i det här fallet.

### <a name="example"></a>Exempel
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
LOGGER.info("App Config Data = " + appConfig.getFullData());
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

### <a name="notification"></a>Meddelande
Programkonfiguration lägger till en ny meddelandetyp:
* **REFRESH_APP_CONFIG**: det här meddelandet skickas en `MAMUserNotification` och informerar appen att nya app config-data är tillgängliga.

### <a name="further-reading"></a>Mer information
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

Följande är vägledning för att kräva användaruppmaning vid start av appen för en automatisk APP-WE-tjänstregistrering (vi kallar detta **standardregistrering** i det här avsnittet), som kräver Intune-appskyddsprinciper för att endast tillåta att Intune-skyddade användare använder den SDK-integrerade Android LOB-appen. Det tar även upp hur du kan aktivera SSO för den SDK-integrerade Android LOB-appen. Detta stöds **inte** för Store-appar som kan användas av användare utan Intune.

> [!NOTE] 
> Fördelarna med **standardregistrering** omfattar en förenklad metod för att hämta en princip från APP-WE-tjänsten för en app på enheten.

> [!NOTE] 
> **Standardregistrering** är medveten om nationella moln.

Aktivera standardregistrering med följande steg:

1. Om din app integrerar ADAL eller om du behöver aktivera enkel inloggning [konfigurerar du ADAL](#configure-azure-active-directory-authentication-library-adal) enligt [vanlig ADAL-konfiguration](#common-adal-configurations) nummer 2. Annars kan du koppa över det här steget.
   
2. Aktivera standardregistrering genom att ange följande värde i manifestet:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```
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

* **Med hjälp av innehållsmatchare**: Överförings- eller mottagningsprincipen i Intune kan blockera eller delvis blockera användningen av en innehållsmatchare för att få åtkomst till innehållsleverantören i en annan app. Detta innebär att `ContentResolver`-metoder returnerar null eller genererar ett felvärde (t.ex. genererar `openOutputStream` felet `FileNotFoundException` om den blockeras). Appen kan avgöra om en misslyckad dataskrivning till en innehållsmatchare orsakades av en princip (eller kan orsakas av en princip) genom att göra anropet:
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

Intune App SDK för Android styr inte insamling av data från din app. Företagsportalprogrammet loggar systemgenererade data som standard. Dessa data skickas till Microsoft Intune. Enligt Microsofts policy samlar vi inte in några personliga data.

> [!NOTE]
> Om användare väljer att inte skicka dessa data så måste de inaktivera telemetri under inställningarna i företagsportalappen. Du kan läsa mer i [Inaktivera Microsofts insamling av användningsdata](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="recommended-android-best-practices"></a>Rekommenderade metoder för Android

* Om möjligt bör alla biblioteksprojekt dela samma android:package. Detta kommer inte att leda till sporadiska fel vid körning, eftersom det helt och hållet är ett problem som uppstår vid byggning. Nyare versioner av Intune App SDK tar bort en del av redundansen.

* Använd de senaste Android SDK-byggverktygen.

* Ta bort alla onödiga och oanvända bibliotek (t.ex. android.support.v4)
