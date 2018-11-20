---
title: Omsluta Android-appar med Intunes programhanteringsverktyg
description: Läs om hur du omsluter Android-appar utan att ändra koden i själva appen. Förbered apparna så att du kan använda hanteringsprinciper för mobilprogram.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 32ce1a71911c7a902f2790fef584ab1c3b86a293
ms.sourcegitcommit: 6ff5df63a2fff291d7ac5fed9c51417fe808650d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52167458"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Förbered Android-appar för appskyddsprinciper med Intunes programhanteringsverktyg

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Använd Microsoft Intunes programhanteringsverktyg för Android om du vill ändra funktionssättet för interna Android-appar genom att begränsa funktionerna i appen utan att ändra koden i själva appen.

Verktyget är ett kommandoradsprogram för Windows som körs i PowerShell och som skapar en omslutning runt Android-appen. När appen har omslutits kan du ändra appens funktioner genom att konfigurera [hanteringsprinciper för mobilprogram](/intune-classic/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) i Intune.


Se [Säkerhetsaspekter vid körning av programhanteringsverktyget](#security-considerations-for-running-the-app-wrapping-tool) innan du kör verktyget. Om du vill ladda ned verktyget går du till [Microsoft Intunes programhanteringsverktyg för Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) på GitHub.

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Kontrollera att du uppfyller kraven för att använda programhanteringsverktyget

-   Du måste köra programhanteringsverktyget på en Windows-dator som kör Windows 7 eller senare.

-   Indataappen måste vara ett giltigt Android-programpaket med filtillägget .apk och:

    -   Den kan inte krypteras.
    -   Den får inte ha omslutits tidigare med Intunes programhanteringsverktyg.
    -   Den måste vara skriven för Android 4.0 eller senare.

-   Appen måste ha utvecklats av eller för ditt företag. Du kan inte använda verktyget på appar som har hämtats från Google Play-butiken.

-   För att kunna köra programhanteringsverktyget måste du installera den senaste versionen av [Java Runtime Environment](http://java.com/download/) och sedan kontrollera att Java-sökvägsvariabeln är inställd på C:\ProgramData\Oracle\Java\javapath i Windows-miljövariablerna. Mer hjälp finns i [Java-dokumentationen](http://java.com/download/help/).

    > [!NOTE]
    > I vissa fall kan 32-bitarsversionen av Java orsaka minnesproblem. Det är en bra idé att installera 64-bitarsversionen.

- Android kräver att alla appaket (.apk) signeras. Information om att **återanvända** befintliga certifikat och allmänna riktlinjer för signeringscertifikat finns i [Återanvända signeringscertifikat och omslutande appar](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps). Den körbara Java keytool.exe används för att generera **nya** autentiseringsuppgifter som krävs för att signera den omslutna utdataappen. Alla angivna lösenord måste vara säkra, men skriv ned dem eftersom de behövs för att köra programhanteringsverktyget.

> [!NOTE]
> Intunes programhanteringsverktyg har inte stöd för Googles signaturscheman v2 och v3 (kommande) för signering av appar. När du har omslutit .apk-filen med Intunes programhanteringsverktyg bör du använda [Googles Apksigner-verktyg]( https://developer.android.com/studio/command-line/apksigner). Då ser du till att appen kan startas enligt Android-standard när den skickats till slutanvändarnas enheter. 

- (Valfritt) Aktivera Multidex i indataappen. Ibland kan en app uppnå storleksgränsen i Dalvik för körbara filer (DEX) på grund av de MAM SDK-klasser i Intune som läggs till vid omslutning. DEX-filer ingår i kompileringen av en Android-app. I det här scenariot är det bäst att aktivera Multidex i själva appen. I vissa organisationer kan du behöva kontakta den som kompilerar appen (t.ex. apputvecklaren). 

## <a name="install-the-app-wrapping-tool"></a>Installera App-Wrapping-verktyget

1.  Från [GitHub-databasen](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) hämtar du installationsfilen InstallAWT.exe för Intunes programhanteringsverktyg för Android till en Windows-dator. Öppna installationsfilen.

2.  Godkänn licensavtalet och slutför installationen.

Kom ihåg vilken mapp du installerade verktyget i. Standardplatsen är: C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>Kör App-Wrapping-verktyget

1. Öppna ett PowerShell-fönster på den Windows-dator där du installerade programhanteringsverktyget.

2. Från mappen där du installerade verktyget importerar du PowerShell-modulen för programhanteringsverktyget:

   ```
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. Kör verktyget genom att använda kommandot **invoke-AppWrappingTool**, med följande användningssyntax:
   ```
   Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
   -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
   ```

   I följande tabell beskrivs egenskaperna för kommandot **invoke-AppWrappingTool**:

|Egenskap|Information|Exempel|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Sökvägen till käll-Android-appen (.apk).| |
 |**-OutputPath**&lt;String&gt;|Sökväg till Android-utdataappen. Om det här är samma mapp-sökväg som för InputPath, så kommer paketeringen misslyckas.| |
|**-KeyStorePath**&lt;String&gt;|Sökväg till keystore-filen som innehåller det offentliga/privata nyckelparet för signering.|Keystore-filer lagras som standard i ”C:\Program (x86)\Java\jreX.X.X_XX\bin”. |
|**-KeyStorePassword**&lt;SecureString&gt;|Lösenordet som används för att dekryptera keystore. Android kräver att alla appaket (.apk) signeras. Använd Java Keytool för att generera KeyStorePassword. Läs mer om Java [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) här.| |
|**-KeyAlias**&lt;String&gt;|Namnet på nyckeln som ska användas för signering.| |
|**-KeyPassword**&lt;SecureString&gt;|Lösenordet som används för att dekryptera den privata nyckeln som ska användas för signering.| |
|**-SigAlg**&lt;SecureString&gt;| (Valfritt) Namnet på signaturalgoritmen som ska användas för signering. Algoritmen måste vara kompatibel med den privata nyckeln.|Exempel: SHA256withRSA, SHA1withRSA|
| **&lt;CommonParameters&gt;** | (Valfritt) Kommandot stöder vanliga PowerShell-parametrar som verbose och debug. |


- En lista med vanliga parametrar finns i [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx).

- Om du vill se detaljerad användningsinformation för verktyget anger du kommandot:

    ```
    Help Invoke-AppWrappingTool
    ```

**Exempel:**

Importera PowerShell-modulen.
```
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```
Kör programhanteringsverktyget på den interna appen HelloWorld.apk.
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Du uppmanas att ange **KeyStorePassword** och **KeyPassword**. Ange de autentiseringsuppgifter som du använde för att skapa nyckellagerfilen.

Den omslutna appen och en loggfil genereras och sparas på den utdatasökväg som du angett.

## <a name="how-often-should-i-rewrap-my-android-application-with-the-intune-app-wrapping-tool"></a>Hur ofta ska jag omsluta mitt Android-program på nytt med Intunes programhanteringsverktyg?
Huvudscenarierna när du måste omsluta dina program på nytt är följande:
* Programmet har publicerat en ny version. Den tidigare versionen av appen har omslutits och överförts till Intune-konsolen.
* Intunes programhanteringsverktyg för Android har publicerat en ny version som möjliggör viktiga felkorrigeringar, eller nya, specifika principfunktioner för skydd av Intune-program. Detta sker var sjätte till var åttonde vecka via GitHub-lagringsplatsen för [Microsoft Intunes programhanteringsverktyg för Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android).

Här är några metodtips för omslutning på nytt: 
* Information om hur du hanterar signeringscertifikat som använts under skapandeprocessen finns i [Återanvända signeringscertifikat och omslutande appar](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps)

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>Återanvända signeringscertifikat och omslutande appar
Android kräver att alla appar måste ha signerats av ett giltigt certifikat för att kunna installeras på Android-enheter.

Omslutna appar kan antingen signeras som en del av omslutningsprocessen eller *efter* omslutning med ditt befintliga signeringsverktyg (signering informationen i appen innan radbrytning tas bort). Om möjligt ska signeringsinformationen som redan användes när för byggprocessen användas vid omslutning. I vissa organisationer kan du behöva arbeta med den som äger keystore-informationen (t.ex. apputvecklare). 

Om tidigare signeringscertifikatet kan inte användas eller om appen har inte distribuerats innan kan du skapa ett nytt signeringscertifikat genom att följa anvisningarna i [Android Utvecklarhandboken](https://developer.android.com/studio/publish/app-signing.html#signing-manually).

Om appen har distribuerats tidigare med ett annat signeringscertifikat, kan appen inte överföras till Intune efter uppgraderingen. Appuppgraderingsscenarier kommer att brytas om appen har signerats med ett annat certifikat än det som appen har byggts med. Alla nya certifikat för tokensignering bör därför behållas för app-uppgraderingar. 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>Säkerhetsaspekter att tänka på när du kör programhanteringsverktyget
För att förhindra eventuell förfalskning, avslöjande av information och privilegieangrepp:

-   Kontrollera att indata för affärsprogrammet (LOB), utdataappen och Java KeyStore finns på samma dator där programhanteringsverktyget körs.

-   Importera utdataprogrammet till Intune på samma dator som där verktyget körs. Mer information om Java Keytool finns i [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html).

-   Om utdataappen och verktyget finns på en UNC-sökväg (Universal Naming Convention) och du inte kör verktyget och indatafilerna på samma dator, konfigurerar du en säker miljö med hjälp av [IPsec (Internet Protocol Security)](http://wikipedia.org/wiki/IPsec) eller [signering med SMB (Server Message Block)](https://support.microsoft.com/kb/887429).

-   Kontrollera att programmet kommer från en betrodd källa.

-   Skydda utdatakatalogen som innehåller den omslutna appen. Fundera på att i stället använda en katalog på användarnivå för utdatan.

## <a name="requiring-user-login-prompt-for-an-automatic-app-we-service-enrollment-requiring-intune-app-protection-policies-in-order-to-use-your-wrapped-android-lob-app-and-enabling-adal-sso-optional"></a>Kräva uppmaning om användarinloggning för en automatisk APP-WE-tjänstregistrering, kräva Intune-appskyddsprinciper för att kunna använda en omsluten Android LOB-app och aktivera ADAL SSO (valfritt)

Följande är vägledning för att kräva användaruppmaning vid start av appen för en automatisk APP-WE-tjänstregistrering (vi kallar detta **standardregistrering** i det här avsnittet), som kräver Intune-appskyddsprinciper för att endast tillåta att Intune-skyddade användare använder den omslutna Android LOB-appen. Det tar även upp hur du kan aktivera SSO för den omslutna Android LOB-appen. 

> [!NOTE] 
> Fördelarna med **standardregistrering** omfattar en förenklad metod för att hämta en princip från APP-WE-tjänsten för en app på enheten.

### <a name="general-requirements"></a>Allmänna krav
* Intune SDK-teamet kommer att kräva appens program-ID. Det går att hitta via [Azure Portal](https://portal.azure.com/), under **Alla program**, i kolumnen för **Program-ID**. Ett bra sätt att kontakta Intune SDK-teamet är att skicka e-post till msintuneappsdk@microsoft.com.
     
### <a name="working-with-the-intune-sdk"></a>Arbeta med Intune SDK
De här anvisningarna är specifika för alla Android- och Xamarin-appar som vill kräva Intune-appskyddsprinciper som ska användas på en slutanvändarenhet.

1. Konfigurera ADAL med hjälp av stegen som beskrivs i [handboken för Intune SDK för Android](https://docs.microsoft.com/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal).

> [!NOTE]
> Termen "klient-id" som är kopplad till din app är samma som termen "program-id" från Azure Portal som är kopplat till din app. 
> * Du behöver "Vanlig ADAL-konfiguration" nummer 2 för att aktivera SSO.

2. Aktivera standardregistrering genom att ange följande värde i manifestet: ```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
   > [!NOTE] 
   > Det får inte finnas några fler MAM-WE-integreringar i appen. Det kan uppstå konflikter om det finns några andra försök att anropa MAMEnrollmentManager API:er.

3. Aktivera MAM-principen som krävs genom att ange följande värde i manifestet: ```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
   > [!NOTE] 
   > Det gör att användaren måste ladda ned företagsportalen till enheten och slutföra flödet för standardregistrering före användning.

### <a name="see-also"></a>Se även
- [Förbereda appar för hantering av mobilprogram med Microsoft Intune](apps-prepare-mobile-application-management.md)

- [Utvecklarhandbok för Microsoft Intune App SDK för Android](app-sdk-android.md)
