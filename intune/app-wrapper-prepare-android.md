---
title: Omsluta Android-appar med Intunes programhanteringsverktyg
description: Läs om hur du omsluter Android-appar utan att ändra koden i själva appen. Förbered apparna så att du kan använda hanteringsprinciper för mobilprogram.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/11/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64de72822ad8d2f8d9893e3428208ff1363d33e2
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566054"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Förbered Android-appar för appskyddsprinciper med Intunes programhanteringsverktyg

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Använd Microsoft Intunes programhanteringsverktyg för Android om du vill ändra funktionssättet för interna Android-appar genom att begränsa funktionerna i appen utan att ändra koden i själva appen.

Verktyget är ett kommandoradsprogram för Windows som körs i PowerShell och som skapar en omslutning runt Android-appen. När appen har omslutits kan du ändra appens funktioner genom att konfigurera [hanteringsprinciper för mobilprogram](app-protection-policies.md) i Intune.

Se [Säkerhetsaspekter vid körning av programhanteringsverktyget](#security-considerations-for-running-the-app-wrapping-tool) innan du kör verktyget. Om du vill ladda ned verktyget går du till [Microsoft Intunes programhanteringsverktyg för Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) på GitHub.

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Kontrollera att du uppfyller kraven för att använda programhanteringsverktyget

-   Du måste köra programhanteringsverktyget på en Windows-dator som kör Windows 7 eller senare.

-   Indataappen måste vara ett giltigt Android-programpaket med filtillägget .apk och:

    -   Den kan inte krypteras.
    -   Den får inte ha omslutits tidigare med Intunes programhanteringsverktyg.
    -   Den måste vara skriven för Android 4.0 eller senare.

-   Appen måste ha utvecklats av eller för ditt företag. Du kan inte använda verktyget på appar som har hämtats från Google Play-butiken.

-   För att kunna köra programhanteringsverktyget måste du installera den senaste versionen av [Java Runtime Environment](https://java.com/download/) och sedan kontrollera att Java-sökvägsvariabeln är inställd på C:\ProgramData\Oracle\Java\javapath i Windows-miljövariablerna. Mer hjälp finns i [Java-dokumentationen](https://java.com/download/help/).

    > [!NOTE]
    > I vissa fall kan 32-bitarsversionen av Java orsaka minnesproblem. Det är en bra idé att installera 64-bitarsversionen.

- Android kräver att alla appaket (.apk) signeras. Information om att **återanvända** befintliga certifikat och allmänna riktlinjer för signeringscertifikat finns i [Återanvända signeringscertifikat och omslutande appar](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps). Den körbara Java keytool.exe används för att generera **nya** autentiseringsuppgifter som krävs för att signera den omslutna utdataappen. Alla angivna lösenord måste vara säkra, men skriv ned dem eftersom de behövs för att köra programhanteringsverktyget.

    > [!NOTE]
    > Intunes programhanteringsverktyg har inte stöd för Googles signaturscheman v2 och v3 (kommande) för signering av appar. När du har omslutit .apk-filen med Intunes programhanteringsverktyg bör du använda [Googles Apksigner-verktyg]( https://developer.android.com/studio/command-line/apksigner). Då ser du till att appen kan startas enligt Android-standard när den skickats till slutanvändarnas enheter. 

- (Valfritt) Ibland kan en app uppnå storleksgränsen i Dalvik för körbara filer (DEX) på grund av de MAM SDK-klasser i Intune som läggs till vid omslutning. DEX-filer ingår i kompileringen av en Android-app. Intune App Wrapping-verktyget hanterar automatiskt DEX filen dataspill vid wrapping för appar med en minsta API-nivå av 21 eller högre (från och med [v. 1.0.2501.1](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android/releases)). För appar med en minsta API-nivå av < 21 bästa praxis är att öka det minsta värdet API-nivå med hjälp av omslutningen `-UseMinAPILevelForNativeMultiDex` flaggan. Följande DEX spill lösningar är tillgängliga för kunder som är det går inte att öka appens minsta API-nivå. I vissa organisationer kan du behöva kontakta den som kompilerar appen (dvs. apputvecklingsteamet):
* Använd ProGuard för att eliminera outnyttjade klassreferenser från appens primära DEX-fil.
* För kunder som använder v3.1.0 eller senare för Android Gradle-plugin-programmet, inaktivera den [D8 dexer](https://android-developers.googleblog.com/2018/04/android-studio-switching-to-d8-dexer.html).  

## <a name="install-the-app-wrapping-tool"></a>Installera App-Wrapping-verktyget

1.  Från [GitHub-databasen](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) hämtar du installationsfilen InstallAWT.exe för Intunes programhanteringsverktyg för Android till en Windows-dator. Öppna installationsfilen.

2.  Godkänn licensavtalet och slutför installationen.

Kom ihåg vilken mapp du installerade verktyget i. Standardplatsen är: C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>Kör App-Wrapping-verktyget

1. Öppna ett PowerShell-fönster på den Windows-dator där du installerade programhanteringsverktyget.

2. Från mappen där du installerade verktyget importerar du PowerShell-modulen för programhanteringsverktyget:

   ```PowerShell
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. Kör verktyget genom att använda kommandot **invoke-AppWrappingTool**, med följande användningssyntax:
   ```PowerShell
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
|**-UseMinAPILevelForNativeMultiDex**| (Valfritt) Använd den här flaggan för att öka källa Android appens minsta API-nivå 21. Den här flaggan uppmanas bekräfta som den kommer att begränsa vem som kan installera den här appen. Användare kan hoppa över dialogrutan genom att lägga till parametern ”-bekräfta: $false” till sina PowerShell-kommando. Flaggan bör endast användas av kunder på appar med min API < 21 som inte vill att omsluta har på grund av fel i DEX dataspill. | |
| **&lt;CommonParameters&gt;** | (Valfritt) Kommandot stöder vanliga PowerShell-parametrar som verbose och debug. |


- En lista med vanliga parametrar finns i [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx).

- Om du vill se detaljerad användningsinformation för verktyget anger du kommandot:

    ```PowerShell
    Help Invoke-AppWrappingTool
    ```

**Exempel:**

Importera PowerShell-modulen.
```PowerShell
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```
Kör programhanteringsverktyget på den interna appen HelloWorld.apk.
```PowerShell
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

-   Om utdataappen och verktyget finns på en UNC-sökväg (Universal Naming Convention) och du inte kör verktyget och indatafilerna på samma dator, konfigurerar du en säker miljö med hjälp av [IPsec (Internet Protocol Security)](https://wikipedia.org/wiki/IPsec) eller [signering med SMB (Server Message Block)](https://support.microsoft.com/kb/887429).

-   Kontrollera att programmet kommer från en betrodd källa.

-   Skydda utdatakatalogen som innehåller den omslutna appen. Fundera på att i stället använda en katalog på användarnivå för utdatan.

### <a name="see-also"></a>Se även
- [Förbereda appar för hantering av mobilprogram med Microsoft Intune](apps-prepare-mobile-application-management.md)

- [Utvecklarhandbok för Microsoft Intune App SDK för Android](app-sdk-android.md)
