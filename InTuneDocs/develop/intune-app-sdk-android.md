---
title: "Utvecklarhandbok för Microsoft Intune App SDK för Android | Microsoft Docs"
description: "Med Microsoft Intune App SDK för Android kan du implementera hantering av mobila appar (MAM, Mobile App Management) med Intune i din Android-app."
keywords: SDK
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 905be6a926dc5bab8e9b1016ba82751ee47313e5
ms.openlocfilehash: 178fbaeb1d3235a81cb4da49b7a955f6999c49a2
ms.lasthandoff: 02/18/2017


---


# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Utvecklarhandbok för Microsoft Intune App SDK för Android

> [!NOTE]
> Börja gärna med att läsa [Översikt över Intune App SDK](intune-app-sdk.md). Den beskriver funktionerna i SDK, samt visar hur du förbereder integreringen på de plattformar som stöds.

Med Microsoft Intune App SDK för Android kan du implementera hantering av mobila appar (MAM, Mobile App Management) med Intune i din Android-app. Ett MAM-aktiverat program är ett program som är integrerat med Intune App SDK. Det kan användas av IT-administratörer för att distribuera principer till din mobila app om Intune aktivt hanterar appen.

## <a name="whats-in-the-sdk"></a>Vad innehåller SDK?

Intune App SDK för Android är ett Android-standardbibliotek utan externa beroenden. SDK:n består av:  

* **Microsoft.Intune.MAM.SDK.jar**: De gränssnitt som behövs för att aktivera MAM och samverkan med Intune-företagsportalappen. Appar måste ange den som en Android-biblioteksreferens.

* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: De gränssnitt som behövs för att aktivera MAM i appar som använder Androids v4-stödbibliotek. Appar som behöver den här typen av stöd måste referera till JAR-filen direkt.

* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: De gränssnitt som behövs för att aktivera MAM i appar som använder Androids v7-stödbibliotek. Appar som behöver den här typen av stöd måste referera till JAR-filen direkt.

* **Resursbiblioteket**: De resurser (t.ex. strängar) som SDK:n behöver.

* **Microsoft.Intune.MAM.SDK.aar**: SDK-komponenterna, med undantag för JAR-filerna Support.V4 och Support.V7. Den här filen kan användas i stället för de enskilda komponenterna om ditt system stöder AAR-filer.

* **AndroidManifest.xml**: Ytterligare startpunkter och bibliotekskrav.

* **THIRDPARTYNOTICES.TXT**: Information om tredjeparts- och/eller OSS-kod som ingår i appen.

## <a name="requirements"></a>Krav

Intune App SDK kompileras som ett Android-projekt. Det betyder att den inte är särskilt beroende av vilken version av Android som appen använder för sina minsta API-versioner eller mål-API-versioner. SDK stöder Android API 14 (Android 4.0+) till och med Android API 24.

Intune App SDK för Android förutsätter att [företagsportalappen](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) finns på enheten för att MAM-principer ska kunna aktiveras. Vid MAM utan enhetsregistrering behöver användaren *inte* registrera enheten med företagsportalappen.


## <a name="how-the-intune-app-sdk-works"></a>Hur Intune App SDK fungerar

###<a name="entry-points"></a>Startpunkter

Intune App SDK kräver ändringar i appens källkod för att Intune-apphanteringsprinciper ska kunna användas. Detta gör du genom att ersätta Android-basklasserna med motsvarande Intune-basklasser, vars namn har prefixet `MAM`. SDK-klasserna finns mellan Android-basklassen och appens egen härledda version av den klassen. Om vi tar en aktivitet som exempel blir resultatet en arvshierarki som ser ut så här: `Activity` > `MAMActivity` > `AppSpecificActivity`.

När till exempel `AppSpecificActivity` samverkar med sin överordnade (till exempel anropar `super.onCreate()`), är `MAMActivity` den överordnade klassen.

Typiska Android-appar har ett enda läge och har åtkomst till systemet genom deras [Context](https://developer.android.com/reference/android/content/Context.html)-objekt. Appar som integrerar Intune App SDK har däremot dubbla lägen. De här apparna fortsätter att få åtkomst till systemet via `Context`-objektet. Beroende på vilken grundläggande `Activity` som används kommer `Context`-objektet att tillhandahållas av Android, eller med en intelligent multiplexering mellan en begränsad vy över systemet och Android-angiven `Context`.

Om du använder en Android-[startpunkt](https://developer.android.com/guide/components/fundamentals.html) som har åsidosatts av sin MAM-motsvarighet, måste MAM-versionen för startpunktens livscykel användas (med undantag för klassen `MAMApplication`).

Om du härleder från `MAMActivity`, i stället för att åsidosätta `onCreate` och anropa `super.onCreate`, måste `Activity` åsidosätta `onMAMCreate` och anropa `super.onMAMCreate`. Detta innebär att Intune begränsar `Activity`-start (bland annat) i vissa fall.


###<a name="sdk-permissions"></a>SDK-behörigheter

Intune App SDK kräver tre [Android-systembehörigheter](https://developer.android.com/guide/topics/security/permissions.html) för apparna som integrerar det:

* `android.permission.GET_ACCOUNTS` (begärs vid körningen om det behövs)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

Dessa behörigheter krävs av Azures autentiseringsbibliotek för Active Directory ([ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/)) för att kunna utföra asynkron autentisering. Om dessa behörigheter inte beviljas till appen eller om de återkallas av användaren så inaktiveras autentiseringsflöden som kräver koordinering (av företagsportalappen).


###<a name="company-portal-app"></a>Företagsportalappen

Varför behövs företagsportalappen? När företagsportalappen har installerats på enheten och har hämtat en programbegränsningsprincip för användaren från Intune-tjänsten, initieras SDK-startpunkterna asynkront. Initiering krävs endast när Android skapar processen från början. Under initieringen upprättas en anslutning med företagsportalappen och principen hämtas från appen.  

> [!NOTE]
> Om företagsportalappen inte finns på enheten ändras inte den Intune-aktiverade appens beteende, utan den beter sig som en vanlig app.


## <a name="how-to-integrate-with-the-intune-app-sdk"></a>Integrera med Intune App SDK

Som vi nämnt tidigare kräver SDK ändringar i appens källkod för att apphanteringsprinciper ska kunna användas. Här är de nödvändiga stegen för att aktivera MAM i din app.

### <a name="replace-classes-methods-and-activities-with-their-mam-equivalent-required"></a>Ersätt klasser, metoder och aktiviteter med deras MAM-motsvarighet (obligatoriskt)

Android-basklasser måste ersättas med deras respektive MAM-motsvarigheter. Du gör detta genom att leta upp alla instanser av klasserna i följande tabell och ersätta dem med deras Intune App SDK-motsvarighet.

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
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent* |
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
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |


**Microsoft.Intune.MAM.SDK.Suppeller till ent.v4.jar**:

| Android-klass för Intune MAM | Intune App SDK-motsvarighet |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider

**Microsoft.Intune.MAM.SDK.Suppeller till ent.v7.jar**:

|Android-klass | Intune App SDK-motsvarighet |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |

>[!NOTE]
>Kom ihåg att om du använder en Android-[startpunkt](https://developer.android.com/guide/components/fundamentals.html) som har åsidosatts av sin MAM-motsvarighet, måste MAM-versionen för startpunktens livscykel användas (med undantag för klassen `MAMApplication`).
>
>Om du härleder från `MAMActivity`, i stället för att åsidosätta `onCreate` och anropa `super.onCreate`, måste `Activity` åsidosätta `onMAMCreate` och anropa `super.onMAMCreate`. Detta innebär att Intune begränsar `Activity`-start (bland annat) i vissa fall.

#### <a name="pendingintent-classes-and-renamed-methods"></a>PendingIntent-klasser och metoder som bytt namn

När du härleder från en av MAM-startpunkterna är det säkert att använda `Context` på vanligt sätt, till exempel att starta `Activity`-klasser och använda `PackageManager`.  

`PendingIntent`-klasser är ett undantag från den här regeln. Du måste ändra klassnamnet när dessa klasser anropas. I stället för `PendingIntent.get*` måste du t.ex. använda `MAMPendingIntent.get*`-metoden. Därefter kan du använda resulterande `PendingIntent` som vanligt.

I vissa fall har en metod som är tillgänglig i Android-klassen markerats som slutgiltig i MAM-ersättningsklassen. I detta fall tillhandahåller MAM-ersättningsklassen en metod med liknande namn (vanligtvis med suffixet `MAM`) som ska åsidosättas i stället. Exempelvis åsidosätter du `ContentProvider.query`i stället för `MAMContentProvider.queryMAM`. Java-kompilatorn ska framtvinga de slutliga begränsningarna för att förhindra oavsiktlig åsidosättning av den ursprungliga metoden i stället för motsvarande MAM.

###<a name="enable-features-that-require-app-participation"></a>Aktivera funktioner som kräver appmedverkan

Det finns vissa principer som SDK inte kan implementera själv. Appen kan styra sitt beteende och använda dessa funktioner med hjälp av flera API:er som du hittar i följande `AppPolicy`-gränssnitt.

```
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * <strong>This function is now deprecated. Please use {@link #getIsSaveToLocationAllowed(SaveLocation, String)} instead</strong>
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
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between the AAD username and the cloud service username does not exist or the username is not known.
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
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();


}

```

### <a name="enable-it-control-over-app-saving-behavior"></a>Aktivera IT-kontroll över hur appar sparar filer

Många appar implementerar funktioner som gör att användaren kan spara filer lokalt eller till en molnlagringstjänst. Med Intune App SDK kan IT-administratörer skydda mot dataläckage genom att tillämpa principbegränsningar som passar behoven i deras organisation.  En av principerna som IT kan kontrollera är huruvida användaren kan spara filer i ett ”personligt” och ohanterat datalager. Användaren kan i så fall spara till en lokal plats, ett SD-kort eller i säkerhetskopieringstjänster från tredje part.

Appens medverkan krävs för att aktivera funktionen. Om din app tillåter att användaren sparar filer på personliga eller molnbaserade platser direkt från appen, måste du implementera den här funktionen så att IT-administratören kan styra möjligheten att spara på en viss plats.   

Appen kan göra följande anrop för att se om principen tillämpas. Med det här anropet vet appen om den aktuella Intune-administratörens princip tillåter att man sparar till ett personligt arkiv. Appen kan sedan framtvinga tillämpningen av principen, eftersom den vet vilket personligt datalager som är tillgängligt för användaren via appen.

```
MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();
```

> [!NOTE]
> `MAMComponents.get(AppPolicy.class)` returnerar alltid en apprincip som inte är null, även om enheten eller appen inte hanteras av en Intune-hanteringsprincip.

### <a name="let-the-app-detect-if-a-pin-policy-is-required"></a>Låt appen känna av om en PIN-princip krävs

I vissa Intune-appbegränsningar kan appen inaktivera några av sina funktioner för att undvika duplicering av funktioner i Intune App SDK. Om appen till exempel har en egen PIN-användarmiljö, kan du inaktivera den om SDK:n har konfigurerats så att användaren måste ange en PIN-kod.

För att se om en PIN-princip för Intune har konfigurerats så att en PIN-kod krävs för att starta appen, kan appen göra följande anrop:

```
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

### <a name="register-for-notifications-from-the-sdk"></a>Registrera för meddelanden från SDK:n  

Din app kan använda Intune App SDK för att styra beteendet för vissa principer, till exempel en selektiv rensning, när de har distribuerats av IT-administratören. När en IT-administratör distribuerar den här typen av princip, skickar Intune-tjänsten ett meddelande till SDK:n.

Din app måste först registreras för meddelanden från SDK:n genom att skapa en `MAMNotificationReceiver`-klass och registrera den med `MAMNotificationReceiverRegistry`. Du gör detta genom att ange mottagaren och typen av meddelande i `App.onCreate`, vilket visas i exemplet nedan:

```
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
.registerReceiver(
                new ToastNotificationReceiver(),
MAMNotificationType.WIPE_USER_DATA);
    }
```

`MAMNotificationReceiver` tar bara emot meddelanden från Intune-tjänsten. SDK:n hanterar vissa meddelanden direkt. Andra meddelanden kräver appens deltagande.

En app *måste* returnera true eller false från ett meddelande. Den måste alltid returnera true förutom om en åtgärd som den försökte utföra till följd av meddelandet misslyckas. Det här felet kan rapporteras till Intune-tjänsten. Ett exempel på ett scenario som bör rapporteras är om appen inte kan rensa användardata när IT-administratören har initierat en rensning.

Det är säkert att blockera i `MAMNotificationReceiver.onReceive` eftersom dess motanrop inte körs i UI-tråden.

Följande `MAMNotificationReceiver`-gränssnitt definieras i SDK:

```
/**
 * The SDK is signaling that a WG event has occurred.
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

###<a name="types-of-notifications"></a>Typer av meddelanden

Följande meddelanden skickas till appen. Några av dem kan kräva appdeltagande.

* **`WIPE_USER_DATA`**: Det här meddelandet skickas i en `MAMUserNotification`-klass. När meddelandet tas emot förväntas appen ta bort alla data som är associerade med ”corporate”-identiteten som skickades med `MAMUserNotification`. För närvarande skickas det här meddelandet när Intune-tjänsten avregistreras. Användarens primära namn anges normalt under registreringen. Om du registrerar dig för det här meddelandet måste appen kontrollera att alla användarens data har tagits bort. Om du inte registrerar dig för det, utför appen standardbeteendet för selektiv rensning.

* **`WIPE_USER_AUXILIARY_DATA`**: Appar kan registreras för det här meddelandet om de vill att Intune App SDK ska använda standardbeteendet för selektiv rensning, men fortfarande vill ta bort vissa extra data när rensningen utförs.  

* **`REFRESH_POLICY`**: Det här meddelandet skickas i `MAMUserNotification`. När det här meddelandet tas emot måste cachelagrade Intune-principer ogiltigförklaras och uppdateras. SDK:n hanterar vanligtvis den här uppgiften. Men appen ska hantera den här uppgiften om principen används permanent.



### <a name="protection-of-backup-data"></a>Skydd av säkerhetskopierade data

Från och med Android Marshmallow (API-23) kan en app säkerhetskopiera data på två sätt. Alla alternativ är tillgängliga för din app och kräver olika steg för att säkerställa att Intune-dataskyddet har implementerats korrekt. Du kan läsa mer om säkerhetskopieringsmetoderna i [Android API-guiden](http://developer.android.com/guide/topics/data/backup.html).

#### <a name="automatic-backup-for-apps"></a>Automatisk säkerhetskopiering för appar

Android började erbjuda [automatiska fullständiga säkerhetskopieringar](https://developer.android.com/guide/topics/data/autobackup.html) för appar på Android Marshmallow-enheter, oavsett appens mål-API. Om du uttryckligen anger `android:allowBackup` till false i filen AndroidManifest.xml, placeras din app aldrig i kö för säkerhetskopiering av Android och ”corporate”-data bevaras i appen. Ingen ytterligare åtgärd krävs i detta fall.

Som standard har attributet `android:allowBackup` värdet true, även om `android:allowBackup` inte har angetts i manifestfilen. Detta innebär att alla appdata säkerhetskopieras automatiskt till användarens Google Drive-konto, ett standardbeteende som medför *risk för dataläckage*. SDK:n kräver följande ändringar för att säkerställa att dataskyddet tillämpas. Det är viktigt att du följer riktlinjerna för att skydda kunddata om du vill att din app ska köras på Android Marshmallow-enheter.  

Om du inte har skapat någon säkerhetskopieringsagent som ska säkerhetskopiera din app med hjälp av `MAMBackupAgent` eller `MAMBackupAgentHelper`, måste du styra hur den automatiska säkerhetskopieringen ska överföra dina appdata. Med Intune kan du använda alla [automatiska säkerhetskopieringsfunktioner](https://developer.android.com/guide/topics/data/autobackup.html) från Android, inklusive möjligheten att definiera anpassade regler i XML. Men du måste följa stegen för att skydda dina data:

1. Använd den förvalda `MAMBackupAgent` för automatiska fullständiga säkerhetskopieringar som är kompatibla med Intune-principer. Placera `android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"` i ditt appmanifest.

2. När du bestämmer vilken typ av fullständig säkerhetskopiering som din app ska använda (ofiltrerad, filtrerad eller ingen), anger du attributet `android:fullBackupContent` till true, false eller till en XML-resurs i appen. Kopiera allt som du placerar i `android:fullBackupContent` till en metadatatagg med namnet `com.microsoft.intune.mam.FullBackupContent`.

    Om du t.ex. vill att din app ska använda fullständiga säkerhetskopieringar enligt dina anpassade regler i en XML-fil, anger du en resurs under metadatataggen `com.microsoft.intune.mam.FullBackupContent` i ditt manifest så här:
    ```
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```



#### <a name="keyvalue-backup"></a>Nyckel-/värdesäkerhetskopiering

Det här alternativet för nyckel-/värdesäkerhetskopiering är tillgängligt för alla API:er samt använder `BackupAgentHelper` och `BackupAgent`.

##### <a name="backupagenthelper"></a>BackupAgentHelper

`BackupAgentHelper` är mycket enklare att implementera än `BackupAgent`, både vad gäller inbyggda Android-funktioner och MAM-integration. Med `BackupAgentHelper` kan du registrera hela filer och delade inställningar, antingen `FileBackupHelper` eller `SharedPreferencesBackupHelper`. Dessa läggs sedan till i `BackupAgentHelper` när den skapas.

##### <a name="backupagent"></a>BackupAgent

Med `BackupAgent` kan du vara mycket mer detaljerad om vilka data som säkerhetskopieras. Det här alternativet innebär dock att du inte kan utnyttja ramverket för Android-säkerhetskopiering. Eftersom du är ansvarig för implementeringen, finns det fler steg som krävs för att säkerställa rätt dataskydd från MAM. Eftersom det mesta av arbetet utförs av utvecklaren, är MAM-integreringen något mer komplicerad.

###### <a name="app-does-not-have-a-backup-agent"></a>Appen har ingen säkerhetskopieringsagent

Utvecklaralternativen när `android:allowBackup =true`.

####### <a name="full-backup-according-to-a-configuration-file"></a>Fullständig säkerhetskopiering enligt en konfigurationsfil

Ange en resurs under metadatataggen `com.microsoft.intune.mam.FullBackupContent` i ditt manifest. Exempelvis:     `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

Lägg till följande attribut i taggen `<application>` : `android:fullBackupContent="@xml/my_scheme"`, där `my_scheme` är en XML-resurs i din app.

####### <a name="full-backup-without-exclusions"></a>Fullständig säkerhetskopiering utan undantag

Ange en tagg i manifestet, t.ex `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />`.

Lägg till följande attribut i taggen `<application>` :`android:fullBackupContent="true"`.

###### <a name="app-has-a-backup-agent"></a>Appen har en säkerhetskopieringsagent

Följ anvisningarna tidigare i den här handboken för `BackupAgent` och `BackupAgentHelper`.

Överväg att byta till `MAMDefaultFullBackupAgent`, som tillhandahåller enkel säkerhetskopiering med Android Marshmallow.

##### <a name="before-your-backup"></a>Innan du säkerhetskopierar

Innan du påbörjar säkerhetskopieringen måste du kontrollera att filerna eller databuffertarna som du planerar att säkerhetskopiera har tillstånd att säkerhetskopieras. Vi har lagt till en `isBackupAllowed`-funktion i `MAMFileProtectionManager` och `MAMDataProtectionManager` som kontrollerar det här. Om filen eller databufferten inte får säkerhetskopieras, bör du inte försöka använda den i säkerhetskopieringen.

Om du någon gång under säkerhetskopieringen vill säkerhetskopiera identiteterna för filerna som du markerade i steg 1, måste du anropa `backupMAMFileIdentity(BackupDataOutput data, File … files)` med de filer som du vill extrahera data från. När du gör det skapas automatiskt nya säkerhetskopieringsenheter som skrivs till `BackupDataOutput`. Dessa enheter används automatiskt vid en återställning.

#### <a name="azure-directory-authentication-library-setup"></a>Konfigurera Azures Active Directory-autentiseringsbibliotek  

SDK:n använder Active Directory-autentiseringsbiblioteket för autentisering och villkorliga startscenarier. De här scenarierna kräver att apparna åtminstone delvis har konfigurerats med Azure AD (Azure Active Directory). Konfigurationsvärdena förmedlas till SDK via `AndroidManifest` -metadata.

Om du vill konfigurera din app och aktivera lämplig autentisering, lägger du till följande appnod i `AndroidManifest`. Några av de här konfigurationerna krävs endast om din app använder ADAL för autentisering i allmänhet. I så fall behöver du de specifika värden som din app använder för att registrera sig själv med Azure AD. Avsikten med detta är att användaren inte ska uppmanas att autentisera sig två gånger när Azure AD upptäcker två separata registreringsvärden: ett från appen och ett från SDK:n.

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

GUID förväntas inte ha inledande eller efterföljande klammerparenteser.

##### <a name="common-adal-configurations"></a>Vanliga ADAL-konfigurationer

Följande är exempel på vanliga konfigurationer för de värden som beskrevs tidigare.

###### <a name="app-does-not-integrate-adal"></a>Appen integrerar inte ADAL

* Behörigheten måste konfigureras för önskad miljö där Azure AD-konton har konfigurerats.

* SkipBroker måste tilldelas värdet true.

###### <a name="app-integrates-adal"></a>Appen integrerar ADAL

* Behörigheten måste konfigureras för önskad miljö där Azure AD-konton har konfigurerats.

* Klient-ID:t måste anges till appens klient-ID.

* `NonBrokerRedirectURI` måste konfigureras med en giltig omdirigerings-URI för appen. Annars måste `urn:ietf:wg:oauth:2.0:oob` ställas in som en giltig omdirigerings-URI för Azure AD.

* SkipBroker måste konfigureras som false (eller inte finnas).

* Azure AD måste ställas in att godkänna omdirigerings-URI:n för den asynkrona meddelandekön.

###### <a name="app-integrates-adal-but-does-not-support-the-azure-ad-authenticator-app"></a>Appen integrerar ADAL, men saknar stöd för Azure AD-autentiseringsappen

* Behörigheten måste konfigureras för önskad miljö där Azure AD-konton har konfigurerats.

* Klient-ID:t måste anges till appens klient-ID.

* `NonBrokerRedirectURI` måste konfigureras med en giltig omdirigerings-URI för appen. Annars bör `urn:ietf:wg:oauth:2.0:oob` ställas in som en giltig omdirigerings-URI för Azure AD.

#### <a name="logging-in-the-sdk"></a>Logga in på SDK:n

Loggning görs via `java.util.logging` -ramverket. För att ta emot loggarna konfigurerar du globala loggning genom att följa anvisningarna i [Javas tekniska guide](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html). Beroende på app är `App.onCreate` vanligtvis den bästa platsen för att initiera loggning. Observera att loggmeddelanden baseras på klassnamnet, som kan vara dolt.

###<a name="multi-identity"></a>Flera identiteter

Som standard tillämpar Intune App SDK en princip på appen som helhet. Multiidentitet är en MAM-funktion som du kan aktivera för att tillämpa en princip på nivån per identitet. Detta kräver mycket större appmedverkan än andra MAM-funktioner. Appen krävs för att meddela app-SDK när den har för avsikt att ändra den aktiva identiteten. SDK meddelar även appen när en identitetsändring krävs.

För närvarande stöds endast en hanterad identitet. När användaren registrerar enheten eller appen använder SDK den här identiteten och ser den som primär hanterad identitet. Andra användare i appen behandlas som ej hanterade med obegränsade principinställningar.

Tänk på att en identitet endast definieras som en sträng. Identiteter är skiftlägeskänsliga. Begäranden till SDK om en identitet kanske inte returnerar samma gemener och versaler som användes när identiteten skapades.

####<a name="enabling-multi-identity"></a>Aktivera flera identiteter

Som standard betraktas alla appar som appar med en enda identitet. En app visar att den kan hantera flera identiteter genom att följande metadata placeras i Android-manifestet.

```
<meta-data
            android:name="com.microsoft.intune.mam.MAMMultiIdentity"
            android:value="true" />
```
####<a name="setting-the-identity"></a>Ställa in identiteten

Du kan ställa in appens identitet på följande nivåer:

1. Processnivå

2. Kontextnivå (vanligtvis `Activity`)

3. Trådnivå

En identitet som anges på trådnivå åsidosätter en identitet som angetts på `Context`-nivå, som i sin tur åsidosätter en identitet som angetts på processnivå. En identitet på `Context` används endast när det är lämpligt. Exempelvis har filrelaterade I/O-åtgärder inte någon associerad `Context`. Du kan använda följande metoder i `MAMPolicyManager` för att ange identiteten och hämta de identitetsvärden som angavs tidigare.

```
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

public static String getUIPolicyIdentity(final Context context);

public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

public static String getProcessIdentity();

public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

public static String getCurrentThreadIdentity();

/**
 * Get the currently applicable app policy. Same as MAMComponents.get(AppPolicy.class). This method does
    not take the context identity into account.
 */
public static AppPolicy getPolicy();

/**
 * Get the currently applicable app policy, taking the context
 * identity into account.
 */
public static AppPolicy getPolicy(final Context context);


public static AppPolicy getPolicyForIdentity(final String identity);

public static boolean getIsIdentityManaged(final String identity);

```
Du kan även radera identiteten för appen genom att ange den till null. Den tomma strängen kan användas som en identitet som aldrig har några begränsningar. Alla metoder som används för att ange identiteten rapporterar tillbaka resultatvärden via ``` MAMIdentitySwitchResult```. Fyra värden kan returneras:

* **SUCCEEDED**: Identitetsändringen lyckades.

* **NOT_ALLOWED**: Identitetsändringen tillåts inte. Detta inträffar vid försök att växla till en annan företagsanvändare, som tillhör samma företag som den registrerade användaren. Det inträffar också vid försök att ange UI-identiteten (`Context`) när en annan identitet har angetts för den aktuella tråden.

* **CANCELLED**: Användaren avbröt identitetsändringen, vanligtvis genom att klicka på bakåtknappen vid en uppmaning om att ange PIN-kod/autentiseringsuppgifter.

* **FAILED**: Identitetsändringen misslyckades av okänd anledning.

När en `Context`-identitet anges rapporteras resultatet asynkront. Om `Context` är en `Activity`-klass visas den inte om identitetsändringen lyckades förrän efter en villkorlig start. En villkorlig start kan kräva att användaren anger en PIN-kod eller sin fullständiga företagsinloggning. Appen förväntas implementera ett ```MAMSetUIIdentityCallback``` för att ta emot det här resultatet, även om det är möjligt att skicka null för den här parametern.

```
public interface MAMSetUIIdentityCallback {
    void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
}
```

Du kan också ange identiteten för en aktivitet direkt via en metod i `MAMActivity`, i stället för att anropa ```MAMPolicyManager.setUIPolicyIdentity```. Du kan göra det med hjälp av följande metod:

 ```public final void switchMAMIdentity(final String newIdentity);```

Appar kan även åsidosätta en metod i `MAMActivity` för att aviseras om resultatet vid försök att ändra identiteten för aktiviteten.

```public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);```

> [!NOTE]
> Identitetsväxlingar kan kräva att aktiviteten återskapas. I detta fall skickas ```onSwitchMAMIdentityComplete```-motanropet till den nya instansen av aktiviteten.


####<a name="implicit-identity-changes"></a>Implicita identitetsändringar

Förutom appens möjlighet att ange identiteten kan en tråd eller en kontexts identitet ändras, baserat på inkommande data från en annan MAM-aktiverad app. Om en aktivitet till exempel startas via en `Intent`-klass som skickas av en annan MAM-app, anges aktivitetens identitet baserat på den effektiva identiteten i den andra appen vid tidpunkten då denna `Intent`-klass skickades.

För tjänster anges trådens identitet på liknande sätt för varaktigheten i ett `onStart`- eller `onBind`-anrop. Anrop till `Binder` som returneras från `onBind` anger också tillfälligt trådens identitet. Anrop till en ```ContentProvider``` anger på liknande sätt trådens identitet för deras varaktighet.

Dessutom kan användarinteraktion med en aktivitet orsaka en implicit identitetsväxling. Om en användare till exempel avbryter en auktoriseringsuppmaning under ```Resume``` så resulterar det i en implicit växling till en tom identitet.
Appen kan välja att bli meddelad om dessa ändringar och i vissa fall förbjuda dem om det behövs. ```MAMService``` och ```MAMContentProvider``` exponerar följande metod som kan åsidosättas av underklasser:

```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
```
När det gäller ```MAMActivity``` finns det en extra parameter i metoden:
```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
```
```AppIdentitySwitchReason```-delen hämtar källan för den implicita växlingen. Den kan acceptera värdena ```CREATE```, ```RESUME_CANCELLED``` och ```NEW_INTENT```.  ```RESUME_CANCELLED```-orsaken används när en aktivitet som återupptas resulterar i att PIN-koder, autentiseringsuppgifter eller andra efterlevnadsprinciper visas och användaren försöker avbryta användargränssnittet, vanligtvis genom att använda bakåtknappen.
```AppIdentitySwitchResultCallback``` är som följer:
```
public interface AppIdentitySwitchResultCallback {
    /**
     * @param result
     *            whether the identity switch can proceed.
     */
    void reportIdentitySwitchResult(AppIdentitySwitchResult result);
}
```
```AppIdentitySwitchResult``` är antingen ```SUCCESS``` eller ```FAILURE```.

Metoden ```onMAMIdentitySwitchRequired``` anropas för alla implicita identitetsändringar, utom för de som görs via en `Binder`-klass som returneras från ```MAMService.onMAMBind```. Standardimplementering av ```onMAMIdentitySwitchRequired``` anropar ```reportIdentitySwitchResult(FAILURE)``` direkt när orsaken är ```RESUME_CANCELLED```, och ```reportIdentitySwitchResult(SUCCESS)``` i alla andra fall.

De flesta appar behöver förmodligen inte blockera eller fördröja en identitetsväxling på annat sätt. Men om en app måste göra det bör du tänka på följande:

* Om en identitetsväxling blockeras är resultatet är samma som om delningsinställningar i ```Receive``` hade förbjudit inkommande data.

* Om en tjänst körs på huvudtråden *måste* ```reportIdentitySwitchResult``` anropas synkront. Annars låser sig UI-tråden.

* För ```Activity```-generering anropas ```onMAMIdentitySwitchRequired``` före ```onMAMCreate```. Om appen måste visa ett användargränssnitt för att kontrollera om identitetsväxlingen ska tillåtas eller inte, måste användargränssnittet visas med hjälp av en annan aktivitet.

* Om en växling i ```Activity``` till den tomma identiteten begärs med en orsak motsvarande ```RESUME_CANCELLED```, måste appen ändra den återupptagna aktiviteten till att visa data som är konsekventa med identitetsväxlingen. Om det inte är möjligt bör appen vägra växeln. Användaren uppmanas att följa principen för identiteten som ska återupptas (t.ex. genom att en skärm för inmatning av en PIN-kod visas).

> [!NOTE]
> En app med flera identiteter tar alltid emot inkommande data från både hanterade och ohanterade appar. Det är appens ansvar att behandla data från hanterade identiteter på ett hanterat sätt. Om en begärd identitet hanteras ```(MAMPolicyManager.getIsIdentityManaged)```, men appen inte kan använda det kontot (t.ex. eftersom konton som e-postkonton måste konfigureras i appen först) bör identitetsväxlingen avvisas.

###<a name="file-protection"></a>Filskydd

Alla filer har en associerad identitet när de skapas, baserat på tråd- och processidentiteten. Den här identiteten används för både filkryptering och selektiv rensning. Endast filer vars identitet har en princip som kräver kryptering krypteras. Med SDK:ns förvalda selektiva rensning rensas endast filer som är associerade med den identitet som en rensning har begärts för. Appen kan fråga efter eller ändra en fils identitet med hjälp av ```MAMFileProtectionManager```.
```
public final class MAMFileProtectionManager {

    /**
     * Protect a file. This will synchronously trigger whatever protection is required for the file, and will tag the file for
     * future protection changes.
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
     * Get the protection info on a file.
     *
     * @param file
     *            File or directory to get information on.
     * @return File protection info, or null if there is no protection info.
     * @throws IOException
     *             If the file cannot be read or opened.
     */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;
}

public interface MAMFileProtectionInfo {
String getIdentity();
}
```

> [!NOTE]
> Filidentitetstaggningen känner av offlineläget. Beakta följande:
> * Om företagsportalappen inte är installerad kan du inte tagga filer med identiteter.
>
> * Om företagsportalappen är installerad, men appen inte har någon princip, är identitetstaggningen för filer inte tillförlitlig.
>
> * När filidentitetstaggning blir tillgängligt behandlas alla tidigare skapade filer som personliga (tillhör identiteten med en tom sträng), om inte appen redan har installerats som en hanterad app med en enda identitet. I så fall hanteras de som om de tillhör den registrerade användaren.

####<a name="data-protection"></a>Dataskydd

Det går inte att tagga en fil som om den tillhörde flera identiteter. Appar som måste lagra data som tillhör olika användare i samma fil, kan göra det manuellt med hjälp av de funktioner som tillhandahålls av ```MAMDataProtectionManager```. På så sätt kan appen kryptera data och koppla dem till en viss användare. Krypterade data är lämpligt för lagring till disk i en fil. Du kan köra frågor mot data som är associerade med identiteten och informationen kan dekrypteras senare.

```
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
###<a name="content-providers"></a>Innehållsleverantörer

Om appen skulle kunna tillhandahålla andra företagsdata än ```ParcelFileDescriptor``` genom ```ContentProvider```, måste appen anropa ```MAMContentProvider```-metoden ```isProvideContentAllowed(String)``` och skicka ägarens ```UPN``` för innehållet. Om den här funktionen returnerar false, returneras inte innehållet till anroparen. Filbeskrivningar som returneras via en innehållsleverantör hanteras automatiskt baserat på filidentiteten.

###<a name="selective-wipe"></a>Selektiv rensning

Om en app registreras för ```WIPE_USER_DATA```-meddelanden får den inte fördelarna med SDK:s standardbeteende för selektiv rensning. För appar som kan hantera flera identiteter kan detta vara viktigare, eftersom en selektiv standardrensning med MAM endast rensar filer som matchar den identitet som ska rensas.

Om du skapar en app som kan hantera flera identiteter, kan du registrera dig för ```WIPE_USER_AUXILIARY_DATA```. Med det här meddelandet kan du utnyttja SDK:ns standardrensning. Det här meddelandet skickas omedelbart innan du utför SDK:ns selektiva standardrensning. Observera att en app aldrig bör registreras för både ```WIPE_USER_DATA``` och ```WIPE_USER_AUXILIARY_DATA```.

### <a name="known-platform-limitations"></a>Kända plattformsbegränsningar

#### <a name="file-size-limitations"></a>Filstorleksbegränsningar

I Android kan begränsningarna i formatet Dalvik för körbara filer bli ett problem för stora kodbaser som körs utan ProGuard. Mer specifikt kan följande begränsningar förekomma:

* Gräns på 65 000 för fält

* Gräns på 65 000 för metoder

När flera projekt ingår får varje `android:package` en kopia av R. Detta ökar kraftigt antalet fält när bibliotek läggs till. Följande rekommendationer kan hjälpa dig att undvika den här begränsningen:

* Om möjligt bör alla biblioteksprojekt dela samma `android:package`. Detta kommer inte att leda till sporadiska fel i fältet, eftersom det helt och hållet är ett problem som uppstår vid byggtiden. Dessutom bearbetar nyare versioner av Android SDK DEX-filer i förväg för att avlägsna viss redundans. Detta minskar avståndet från fälten ytterligare.

* Använd de senaste Android SDK-byggverktygen som är tillgängliga.

* Ta bort alla onödiga och oanvända bibliotek (t.ex. `android.support.v4`).

#### <a name="policy-enforcement-limitations"></a>Principtillämpningsgränser

**Skärmdump**: SDK:n kan inte framtvinga ett nytt värde för skärmdumpsinställningen i `Activity`-klasser som redan har gått igenom `Activity.onCreate`. Detta kan resultera i en viss tidsperiod då appen är konfigurerad att inaktivera skärmdumpar, men då skärmdumpar fortfarande kan tas.

**Innehållsmatchare**: Överförings- eller mottagningsprincipen kan blockera eller delvis blockera användningen av en innehållsmatchare för att få åtkomst till innehållsleverantören i en annan app. Detta innebär att `ContentResolver` metoder returnerar null eller genererar ett felvärde. (Till exempel kommer `openOutputStream` att utlösa `FileNotFoundException` om det är blockerat.) Appen kan göra det här anropet för att kontrollera om en princip orsakade (eller kan orsaka) att det inte går att skriva data via en innehållsmatchare:

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**Exporterade tjänster**: Den `AndroidManifest.xml`-fil som ingår i App-SDK Intune har `MAMNotificationReceiverService`. Detta måste vara en exporterad tjänst för att företagsportalappen ska kunna skicka meddelanden till en upplyst app. Tjänsten kontrollerar anroparen för att säkerställa att bara företagsportalappen har tillåtelse att skicka meddelanden.

### <a name="android-best-practices"></a>Metodtips för Android

Intune SDK använder kontraktet från Android-API:n, även om feltillstånd kan utlösas oftare på grund av principtillämpningen. Följande Android-rekommendationer minskar risken för fel:

* Android SDK-funktioner som kan returnera null har högre sannolikhet att vara null nu. Se till att null-kontrollerna finns på rätt plats för att minimera risken för problem.

* I funktioner som du kan kontrollera kan du använda deras SDK API:er när du kontrollerar dem.

* Eventuella härledda funktioner måste anropas via deras överordnade klassversioner.

* Undvik att använda API:er på ett tvetydigt sätt. Till exempel resulterar användning av `Activity.startActivityForResult/onActivityResult` utan att `requestCode` kontrolleras i ett onormalt beteende.

