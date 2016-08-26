---
title: "Utvecklarhandbok för Microsoft Intune App SDK för Android | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2915cca314b489bbcb590d01b03a0b38134fa619
ms.openlocfilehash: d2e4b6903d86b79edd9c758b2ce51733831e785a


---

# Utvecklarhandbok för Microsoft Intune App SDK för Android

> [!NOTE]
> Börja gärna med att läsa guiden [Översikt över Intune App SDK](intune-app-sdk.md). Den här översikten beskriver funktionerna i SDK samt hur du förbereder integreringen på de plattformar som stöds. 

# Vad innehåller SDK? 

Intune App SDK för Android är ett Android-standardbibliotek utan externa beroenden. SDK består av:  

* **`Microsoft.Intune MAM.SDK.jar`**: Gränssnitten som behövs för att aktivera MAM i en app, samt för att aktivera samverkan med Microsoft Intune-appen Företagsportal. Appar måste ange den som en Android-biblioteksreferens.

*  **`Microsoft.Intune.MAM.SDK.Support.v4.jar`**: Gränssnitten som behövs för att aktivera MAM i appar som använder Android v4-supportbiblioteket.  Appar som behöver den här typen av stöd måste referera till JAR-filen direkt. 

* **`Microsoft.Intune.MAM.SDK.Support.v7.jar`**: Gränssnitten som behövs för att aktivera MAM i appar som använder Android v7-supportbiblioteket.   Appar som behöver den här typen av stöd måste referera till JAR-filen direkt.

* **Resursbiblioteket**: De resurser (t.ex. strängar) som SDK behöver. 

* **`Microsoft.Intune.MAM.SDK.aar`**: SDK-komponenterna, med undantag av JAR-filerna Support.V4 och Support.V7. Den här filen kan användas i stället för de enskilda komponenterna om ditt system stöder AAR-filer.

* **`AndroidManifest.xml`**: De ytterligare startpunkterna och bibliotekskraven. 

* **`THIRDPARTYNOTICES.TXT`**: Information om tredjeparts- och/eller OSS-kod som ingår i appen. 

# Krav 

Intune App SDK kompileras som ett Android-projekt. Det betyder att det i hög grad är oberoende av versionen av Android som appen använder för sina minsta API-versioner eller mål-API-versioner. SDK stöder Android API 14 (Android 4.0+) till och med Android 24. 

# Hur Intune App SDK fungerar 

Intune App SDK kräver ändringar i appens källkod för att apphanteringsprinciper ska kunna användas. Detta görs genom att Android-basklasserna ersätts med motsvarande hanterade klasser, som i dokumentet har prefixet `MAM`. SDK-klasserna finns mellan Android-basklassen och appens egen härledda version av den klassen.  Om vi tar en aktivitet som exempel blir resultatet en arvshierarki som ser ut så här: `Activity ->MAMActivity->AppSpecificActivity`.

När `AppSpecificActivity` vill interagera med sitt överordnade objekt, t.ex. `super.onCreate())`, är `MAMActivity` den överordnade klassen trots att den finns i arvshierarkin och ersätter några metoder. Android-appar har ett enda läge och har åtkomst till hela systemet via Context-objektet.  Appar som implementerar Intune App SDK har däremot dubbla lägen. Apparna fortsätter att komma åt systemet via Context-objektet men, beroende på vilken basaktivitet som används, kommer Context-objektet antingen från Android eller så använder det intelligent multiplexering mellan en begränsad vy av systemet och Context-objektet från Android.

Intune App SDK för Android förutsätter att appen Företagsportal finns på enheten för att MAM-principer ska kunna aktiveras. Om appen Företagsportal inte finns förändras inte den MAM-aktiverade appens beteende, och den fungerar som vilken annan mobilapp som helst. När Företagsportal installeras och har en princip för användaren initieras SDK-startpunkterna asynkront. Initiering krävs endast om processen ursprungligen skapats av Android. Under initieringen upprättas en anslutning med appen Företagsportal och appbegränsningsprincipen hämtas.  

# Integrera med Intune App SDK
 
Som vi nämnt tidigare kräver SDK ändringar i appens källkod för att apphanteringsprinciper ska kunna användas. Här är de nödvändiga stegen för att aktivera MAM i en app: 

## Ersätt klasser, metoder och aktiviteter med deras MAM-motsvarighet (obligatoriskt) 

* Android-basklasser måste ersättas med deras MAM-motsvarighet. Du gör detta genom att leta upp alla instanser av klasserna som anges i tabellen nedan och ersätta dem med deras Intune App SDK-motsvarighet.  

    | Android-klass | Intune App SDK-motsvarighet |
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
    | android.app.PendingIntent | MAMPendingIntent |
    | android.app.Service | MAMService |
    | android.app.TabActivity | MAMTabActivity |
    | android.app.TaskStackBuilder | MAMTaskStackBuilder |
    | android.app.backup.BackupAgent | MAMBackupAgent |
    | android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
    | android.app.backup.FileBackupHelper | MAMFileBackupHelper |
    | android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
    | android.content.BroadcastReceiver | MAMBroadcastReceiver |
    | android.content.ContentProvider | MAMContentProvider |
    | android.os.Binder | MAMBinder* |
    | android.provider.DocumentsProvider | MAMDocumentsProvider |
    | android.preference.PreferenceActivity | MAMPreferenceActivity |

    *Du behöver bara ersätta Binder med MAMBinder om Binder inte genereras från ett AIDL-gränssnitt.

    **Microsoft.Intune.MAM.SDK.Suppeller till ent.v4.jar**:

    | Android-klass för Intune MAM | SDK-motsvarighet |
    |--|--|
    | android.support.v4.app.DialogFragment | MAMDialogFragment
    | android.support.v4.app.FragmentActivity | MAMFragmentActivity
    | android.support.v4.app.Fragment | MAMFragment
    | android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
    | android.support.v4.content.FileProvider | MAMFileProvider
    
    **Microsoft.Intune.MAM.SDK.Suppeller till ent.v7.jar**:

    |Android-klass | Intune MAM SDK-motsvarighet |
    |--|--|
    |android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


* Om du använder en Android-startpunkt som har åsidosatts av dess MAM-motsvarighet måste en alternativ version av startpunktens livscykel användas (med undantag av klassen `MAMApplication`).

    Om du härleder från `MAMActivity`, i stället för att åsidosätta `onCreate` och anropa `super.onCreate`, måste Activity åsidosätta `onMAMCreate` och anropa s`uper.onMAMCreate`. Detta gör att starten av Activity (bland andra) kan begränsas i vissa fall. 

# Aktivera funktioner som kräver appmedverkan 

Det finns vissa principer som SDK inte kan implementera själv. För att appen ska kunna kontrollera sitt beteende med dessa funktioner kan du använda flera API:er som du hittar i `AppPolicy` -gränssnittet som finns med nedan.  

    /**
     * External facing app policies.
     */
    public interface AppPolicy {
        /**
         * Restrict where an app can save personal data.
         * 
         * @return True if the app is allowed to save to personal data stores;
         *         false otherwise.
         */
        boolean getIsSaveToPersonalAllowed();
    
        /**
         * Check if policy prohibits saving to a content provider location.
         * 
         * @param location
         *            a content URI to check
         * @return True if location is not a content URI or if policy does not 
         *         prohibit saving to the content location.
         */
        boolean getIsSaveToLocationAllowed(android.net.Uri location); 
    
        /**
         * Whether the SDK PIN prompt is enlightened for the app.
         * 
         * @return True if the PIN is enabled. False otherwise.
         */
        boolean getIsPinRequired();
        /**
         * Whether the Intune Managed Browser is required to open web links.
         *
         * @return True if the Managed Browser is required, false otherwise
         */
        boolean getIsManagedBrowserRequired();
    }

## Ge IT-administratörer kontroll över hur appar sparar filer

Många appar implementerar funktioner som gör att slutanvändaren kan spara filer lokalt eller till en annan tjänst. Med Intune App SDK kan IT-administratörer skydda mot dataläckage genom att tillämpa principbegränsningar som passar behoven i deras organisation.  En av principerna som administratören kan kontrollera är om slutanvändaren kan spara filer i ett personligt datalager, till exempel på en lokal plats, på ett SD-kort eller till säkerhetskopieringstjänster. Appens medverkan krävs för att aktivera funktionen. Om din app tillåter att användaren sparar filer på personliga eller molnbaserade platser direkt från appen måste du implementera den här funktionen så att IT-administratören kan styra huruvida det går att spara eller inte på en viss plats. API:et nedan meddelar appen om den aktuella administratörsprincipen tillåter att filer sparas i ett personligt lager. Appen kan sedan framtvinga tillämpningen av principen eftersom den vet vilket personligt datalager som är tillgängligt för slutanvändaren via appen.  

Appen kan göra följande anrop för att avgöra om principen tillämpas: 

    MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();

**Obs!**MAMComponents.get(AppPolicy.class) returnerar alltid en apprincip som inte är null, även om enheten eller appen inte hanteras. 

## Tillåta att en app känner av om en PIN-princip krävs
 
 Det finns ytterligare principer då appen kanske vill inaktivera en del av sina funktioner för att inte duplicera funktioner i Intune App SDK. Om appen till exempel har en egen PIN-användarmiljö kanske den vill inaktivera den om SDK har konfigurerats så att slutanvändaren måste ange en PIN-kod. 

Appen kan göra följande anrop för att avgöra om PIN-principen har konfigurerats att kräva regelbunden PIN-inmatning: 

    MAMComponents.get(AppPolicy.class).getIsPinRequired();

## Registrera en app för meddelanden från SDK  

Med Intune App SDK har din app kontroll över beteendet när vissa principer, t.e.x en fjärrensningsprincip, används av IT-administratören. Detta kräver att du först registrerar appen för meddelanden från SDK genom att skapa en `MAMNotificationReceiver` -klass och registrera den med `MAMNotificationReceiverRegistry`. Det gör du genom att ange mottagaren och typen av meddelande som mottagaren vill få i  `App.onCreate`, som du ser i exemplet nedan:
 
    @Override
      public void onCreate() {
            super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class).registerReceiver(
    new ToastNotificationReceiver(), MAMNotificationType.WIPE_USER_DATA);
    }

`MAMNotificationReceiver` tar bara emot meddelanden. Vissa meddelanden hanteras av SDK direkt, andra kräver appens medverkan. En app måste returnera true eller false från ett meddelande. Den måste alltid returnera true förutom om en åtgärd som den försökte utföra till följd av meddelandet misslyckas. Den misslyckade åtgärden kan rapporteras till Intune-tjänsten, t.ex. för att ange att appen inte kunde rensa användardata. Det är säkert att blockera i `MAMNotificationReceiver.onReceive`; dess motanrop körs inte i UI-tråden. 

MAMNotificationReceiver-gränssnittet tas med nedan så som det definieras i SDK: 

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

Följande meddelanden skickas till appen och några av dem kan kräva appens medverkan: 

* **`WIPE_USER_DATA`-meddelande**: Det här meddelandet skickas i en `MAMUserNotification`-klass. När det här meddelandet tas emot ska appen radera alla data som associeras med identiteten som skickas med `MAMUserNotification`. För närvarande skickas det här meddelandet när Intune-tjänsten avregistreras. Användarens primära namn anges normalt under registreringen. Om du registrerar dig för det här meddelandet måste appen kontrollera att alla användardata har tagits bort. Om du inte registrerar dig för det här meddelandet utförs det fördefinierade beteendet för selektiv rensning. 

* **`WIPE_USER_AUXILIARY_DATA`-meddelande**: Appar kan registreras för det här meddelandet om Intune App SDK ska utföra standardrensningen, men apparna fortfarande ska ta bort vissa extra data när rensningen görs.  

* **`REFRESH_POLICY`-meddelande**: Det här meddelandet skickas i en MAMNotification utan ytterligare information. När det här meddelandet tas emot ska eventuella cachelagrade principer inte längre betraktas som inaktuella och ska därför kontrollera vad principen är. Detta hanteras vanligtvis av SDK, men ska hanteras av appen om principen används permanent. 

## Väntande avsikter och metoder 

Efter härledning från en av MAM-startpunkterna kan du använda Context som vanligt för att starta aktiviteter, med dess `PackageManager`osv.  `PendingIntents` är undantag till den här regeln. Du måste ändra klassnamnet när dessa klasser anropas. Till exempel måste `MAMPendingIntents.get*` användas i stället för `PendingIntent.get*`. 

I vissa fall har en metod som är tillgänglig i Android-klassen markerats som slutgiltig i MAM-ersättningsklassen. I så fall tillhandahåller MAM-ersättningsklassen en metod med liknande namn (vanligtvis med suffixet "MAM") som ska åsidosättas i stället. Exempelvis åsidosätter du `ContentProvider.query`i stället för `MAMContentProvider.queryMAM`. Java-kompilatorn ska framtvinga de slutliga begränsningarna för att förhindra oavsiktlig åsidosättning av den ursprungliga metoden i stället för motsvarande MAM. 

# Skydda säkerhetskopierade data 

Från och med Android Marshmallow (API-23) kan en app säkerhetskopiera data på två sätt. Dessa alternativ är tillgängliga i din app och kräver olika steg för att säkerställa att MAM-dataskyddet tillämpas på rätt sätt. Tabellen nedan ger en snabb översikt över relevanta åtgärder som krävs för korrekt dataskydd.  Du kan också hitta mer information om säkerhetskopiering med Android i [säkerhetskopieringsguiden för Android-utvecklare](http://developer.android.com/guide/topics/data/backup.html.). 

## Automatisk fullständig säkerhetskopiering

I Android M började Android erbjuder automatiska fullständiga säkerhetskopieringar för appar oavsett mål-API när apparna körs på en Android M-enhet. Förutsatt att attributet `android:allowBackup` inte är false görs fullständiga, ofiltrerade säkerhetskopieringar för appen. Eftersom detta innebär en risk för dataläckage kräver SDK ändringarna som beskrivs i tabellen nedan för att säkerställa att data skyddas.  Det är viktigt att du följer riktlinjerna nedan för att skydda kundens data.  Om du ställer in `android:allowBackup=false` placeras din app aldrig i kö för säkerhetskopieringar av operativsystemet och det finns inga ytterligare åtgärder för MAM eftersom det finns inte någon säkerhetskopia.
 
 ## ”nyckel/värde”-säkerhetskopieringar

Det här alternativet är tillgängligt för alla API:er och använder `BackupAgent` och `BackupAgentHelper`. 

### Använda BackupAgentHelper

`BackupAgentHelper` är mycket enklare att implementera än `BackupAgent` , både vad gäller inbyggda Android-funktioner och MAM-integrering. `BackupAgentHelper` kan utvecklare registrera hela filer och delade inställningar antingen till en `FileBackupHelper` eller `SharedPreferencesBackupHelper`, som sedan läggs till i `BackupAgentHelper` när de skapas. 

### Använda BackupAgent

`BackupAgent` gör att du kan vara mycket mer explicit när det gäller vilka data som säkerhetskopieras. Det här alternativet innebär dock att du inte kan utnyttja ramverket för Android-säkerhetskopiering.  Eftersom du är ansvarig för implementeringen finns det fler steg som krävs för att säkerställa rätt dataskydd från MAM. Eftersom det mesta av arbetet läggs över på utvecklaren är MAM-integreringen något mer komplicerad. 

#### Appen har ingen säkerhetskopieringsagent
  
Utvecklaralternativen när `Android:allowbBackup =true`:

##### Fullständig säkerhetskopiering enligt en konfigurationsfil: 

Ange en resurs under metadatataggen `com.microsoft.intune.mam.FullBackupContent` i ditt manifest. Exempel:
    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

Lägg till följande attribut i taggen `<application>` : `android:fullBackupContent="@xml/my_scheme"`, där `my_scheme` är en XML-resurs i din app. 

##### Fullständig säkerhetskopiering utan undantag 

Ange en tagg i manifestet t.ex. `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
Lägg till följande attribut i taggen `<application>` :`android:fullBackupContent="true"`.

#### Appen har en säkerhetskopieringsagent

Följ rekommendationerna i avsnitten `BackupAgent` och `BackupAgentHelper` ovan. 

Överväg att byta till vår `MAMDefaultFullBackupAgent`, som tillhandahåller enkel säkerhetskopiering med Android M. 

### Innan du säkerhetskopierar

Innan du påbörjar säkerhetskopieringen måste du kontrollera att filerna eller databuffertarna som du planerar att säkerhetskopiera har tillstånd att säkerhetskopieras. Vi har lagt till en `isBackupAllowed` -funktion i `MAMFileProtectionManager` och `MAMDataProtectionManager` som du kan köra för att ta reda på det. Om filen eller bufferten inte får säkerhetskopieras bör du inte försöka använda den i säkerhetskopieringen.

Om du någon gång under säkerhetskopieringen vill säkerhetskopiera identiteterna för filerna som du markerade i steg 1 måste du anropa `backupMAMFileIdentity(BackupDataOutput data, File … files)` med de filer som du vill extrahera data från. När du gör det skapas automatiskt nya säkerhetskopieringsenheter som skrivs till `BackupDataOutput` . Dessa enheter används automatiskt vid en återställning. 

## Konfigurera Azure Directory Authentication Library (ADAL)  

SDK bygger på ADAL för autentisering och villkorsstyrda startscenarier som kräver att appar har vissa delar av Azure Active Directory-konfigurationen. Konfigurationsvärdena förmedlas till SDK via `AndroidManifest` -metadata. Om du vill konfigurera din app och aktivera lämplig autentisering lägger du till följande appnod i `AndroidManifest`. Vissa av de här konfigurationerna krävs endast om din app använder ADAL generellt för autentisering. I så fall behöver du de specifika värden som din app använder för att registrera sig med AAD. Avsikten med detta är att användaren inte ska uppmanas att autentisera sig två gånger på grund av att AAD upptäcker två separata registreringsvärden: en från appen och en från SDK. 

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

### Vanliga ADAL-konfigurationer 

Följande är exempel på vanliga konfigurationer för värdena som förklaras ovan. 

#### Appen integrerar inte ADAL

* Behörigheten måste konfigureras för önskad miljö där AAD-konton har konfigurerats.

* SkipBroker måste tilldelas värdet true.

#### Appen integrerar ADAL

* Behörigheten måste konfigureras för önskad miljö där AAD-konton har konfigurerats.

* Klient-ID:t måste anges till appens klient-ID.

* `NonBrokerRedirectURI` bör konfigureras med en giltig omdirigerings-URI för appen.
    * Or `urn:ietf:wg:oauth:2.0:oob` konfigureras som en giltig AAD-omdirigerings-URI.

* SkipBroker måste konfigureras som false (eller inte vara närvarande).

* AAD måste konfigureras att godkänna omdirigerings-URI:n för hanteraren.

#### Appen integrerar ADAL men har inte stöd för AAD-autentiseringsappen.

* Behörigheten måste konfigureras för önskad miljö där AAD-konton har konfigurerats.

* Klient-ID:t måste anges till appens klient-ID.

* `NonBrokerRedirectURI` måste konfigureras med en giltig omdirigerings-URI för appen.

    * Or `urn:ietf:wg:oauth:2.0:oob` konfigureras som en giltig AAD-omdirigerings-URI.

## Aktivera loggning i SDK 

Loggning görs via `java.util.logging` -ramverket. För att ta emot loggarna konfigurerar du globala loggning genom att följa anvisningarna i [Javas tekniska guide](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html). Beroende på appen är `App.onCreate` vanligtvis den bästa platsen för att initiera loggning. Observera att loggmeddelanden baseras på klassnamnet, som kan vara dolt.

# Kända plattformsbegränsningar 

## Filstorleksbegränsningar 

I Android kan begränsningarna i formatet Dalvik för körbara filer bli ett problem för stora kodbaser som körs utan ProGuard. Mer specifikt kan följande begränsningar förekomma: 

* Gräns på 65 K för fält.

* Gräns på 65 K för metoder.

När flera projekt är medtagna får varje android:package en kopia av R som kraftigt ökar antalet fält när bibliotek läggs till. Följande rekommendationer kan hjälpa dig att undvika den här begränsningen:
 
* Om möjligt bör alla biblioteksprojekt dela samma android:package. Detta kommer inte att leda till sporadiska fel i fältet eftersom det helt och hållet är ett problem som uppstår vid byggning.   Dessutom bearbetar nyare versioner av Android SDK DEX-filer i förväg för att avlägsna redundans. Detta minskar avståndet från fälten ytterligare.

* Använd de senaste Android SDK-byggverktygen som är tillgängliga.

* Ta bort alla onödiga och oanvända bibliotek (t.ex. `android.support.v4`)

## Principtillämpningsgränser

**Skärmdump**: SDK kan inte framtvinga ett nytt värde för skärmdumpsinställningen i aktiviteter som redan har gått igenom Activity.onCreate. Detta kan resultera i en viss tidsperiod då appen är konfigurerad att inaktivera skärmdumpar men då skärmdumpar fortfarande kan tas.

**Med hjälp av innehållsmatcharen*: Överförings- eller mottagningsprincipen kan blockera eller delvis blockera användningen av en innehållsmatchare för att komma åt innehållsleverantören i en annan app. Detta innebär att ContentResolver-metoder returnerar null eller genererar ett felvärde (t.ex. genererar `openOutputStream` `FileNotFoundException` om den blockeras). Appen kan avgöra om en misslyckad dataskrivning till en innehållsmatchare orsakades av en princip (eller kan orsakas av en princip) genom att göra anropet:

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**Exporterade tjänster**: Filen `AndroidManifest.xml` i Intune App SDK innehåller `MAMNotificationReceiverService`, som måste vara en exporterad tjänst för att Företagsportal ska kunna skicka meddelanden till en Intune App SDK-aktiverad app. Tjänsten kontrollerar anroparen för att säkerställa att bara Företagsportal har tillåtelse att skicka meddelanden. 

# Rekommenderade metoder för Android 

Intune SDK använder kontraktet som tillhandahålls av Android-API:et, även om feltillstånd kan utlösas oftare på grund av principtillämpning. Följande Android-rekommendationer minskar risken för fel: 

* Android SDK-funktioner som kan returnera null har högre sannolikhet att vara null nu.  Se till att null-kontrollerna körs på rätt plats för att minimera risken för problem.

* Funktioner som kan kontrolleras måste kontrolleras genom sina SDK-API:er.

* Eventuella härledda funktioner måste göra anrop upp till sina överordnade klassversioner.

* Undvik att använda API:er på ett tvetydigt sätt. Till exempel resulterar `Activity.startActivityForResult/onActivityResult` utan att requestCode kontrolleras i ett onormalt beteende.



<!--HONumber=Jun16_HO4-->


