---
title: Omsluta Android-appar med apphanteringsverktyget | Microsoft Intune
description: "Använd informationen i det här avsnittet för att lära dig hur du omsluter Android-appar utan att ändra koden i själva appen. Förbered apparna så att du kan använda hanteringsprinciper för mobilprogram."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fe3a9f2fd9ce9a3c3f776dcfd9ad3347a63d0fc1
ms.openlocfilehash: e623755cf926020bcb66d8a6d40e5cce9b46b0ae


---

# Förbereda Android-appar för hantering av mobilprogram med Intunes programhanteringsverktyg
Använd **Microsoft Intunes appomslutningsverktyg för Android** för att ändra funktionssättet för interna Android-appar genom att begränsa funktionerna i appen utan att ändra koden för själva appen.

Verktyget är ett kommandoradsprogram för Windows som körs i PowerShell och skapar en omslutning runt Android-appen. När appen har omslutits kan du ändra appens funktioner genom att konfigurera [hanteringsprinciper för mobilprogram](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) i Intune.


Se [Säkerhetsaspekter vid körning av programhanteringsverktyget](#security-considerations-for-running-the-app-wrapping-tool) innan du kör verktyget. Om du vill ladda ned verktyget går du till [Microsoft Intunes appomslutningsverktyg för Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) på GitHub.



## Steg 1 Uppfyll nödvändiga krav för att använda programhanteringsverktyget

-   Du måste köra app-wrapping-verktyget i en Windows-dator som kör Windows 7 eller senare.

-   Indataappen måste vara ett giltigt Android-programpaket med filtillägget **.apk** och:

    -   Går inte att kryptera

    -   Får inte redan ha omslutits med appomslutningsverktyget
    -   Måste vara skriven för Android 4.0 eller senare

-   Appen måste ha utvecklats av eller för ditt företag. Du kan inte använda verktyget på appar som har hämtats från Google Play-butiken.

-   För att kunna köra programhanteringsverktyget måste du installera den senaste versionen av [Java Runtime Environment](http://java.com/download/) och sedan kontrollera att Java-sökvägsvariabeln är inställd på **C:\ProgramData\Oracle\Java\javapath** i Windows-miljövariablerna. Mer hjälp finns i [Java-dokumentationen](http://java.com/download/help/).

    > [!NOTE]
    > I vissa fall kan 32-bitarsversionen av Java orsaka minnesproblem. Vi rekommenderar att du installerar 64-bitarsversionen istället.

- Android kräver att alla appaket (.apks) signeras. Använda Java-nyckeln för att generera autentiseringsuppgifter som krävs för att signera den omslutna utdataappen. Kommandot nedan använder till exempel den körbara Java-filen **keytool.exe** för att generera nycklar som kan användas av appomslutningsverktyget för att signera den omslutna utdataappen.

    ```
    keytool.exe -genkeypair -v -keystore mykeystorefile -alias mykeyalias -keyalg RSA -keysize 2048 -validity 50000
    ```
    Det här exemplet skapar ett nyckelpar (en offentlig nyckel och tillhörande privat nyckel med storleken 2048 bitar) med RSA-algoritmen, sedan omsluts den offentliga nyckeln till ett självsignerat X.509 v3-certifikat som lagras som en enda element i certifikatkedjan. Den här certifikatkedjan och den privata nyckeln lagras i en nyckellagerpost med namnet "mykeystorefile" och identifieras med alias "mykeyalias". Nyckellagerposten är giltig i 50 000 dagar.

    Kommandot uppmanar dig att ange lösenord för nyckellagret och nyckeln. Använd lösenord som är säkra och svåra att gissa, men kom ihåg dem, eftersom de behövs senare för att köra appomslutningsverktyget.

    Detaljerad dokumentation om [nyckelverktyget](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/keytool.html) i Java och [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) i Java finns på webbplatsen för Oracle-dokumentation.

## Steg 2 Installera programhanteringsverktyget

1.  Från [GitHub-databasen](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) hämtar och öppnar du installationsfilen **InstallAWT.exe** för Intunes appomslutningsverktyg för Android till en Windows-dator.

2.  Godkänn licensavtalet och slutför sedan installationen.

Kom ihåg vilken mapp du installerade verktyget i. Standardplatsen är: **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**.

## Steg 3 Kör programhanteringsverktyget

1.  På den Windows-dator där du installerade apphanteringsverktyget öppnar du ett PowerShell-fönster i administratörsläge.

2.  Från mappen där du installerade verktyget importerar du PowerShell-modulen för app-wrapping-verktyget:

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  Kör verktyget genom att använda kommandot **invoke-AppWrappingTool**, med följande användningssyntax:
    ```
    Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
    -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
    ```

 I följande tabell beskrivs egenskaperna för kommandot **invoke-AppWrappingTool**:

|Egenskap|Information|Exempel|
|-------------|--------------------|---------|
|**-InputPath**&lt;sträng&gt;|Sökvägen till käll-Android-appen (.apk).| |
|**-OutputPath**&lt;sträng&gt;|Sökväg till "utdata" Android-appen. Om det här är samma mapp-sökväg som för InputPath, så kommer paketeringen misslyckas.| |
|**-KeyStorePath**&lt;sträng&gt;|Sökväg till keystore-filen som innehåller det offentliga/privata nyckelparet för signering.|Nyckellagerfiler lagras som standard i "C:\Program Files (x86)\Java\jreX.X.X_XX\bin." |
|**-KeyStorePassword**&lt;säkerSträng&gt;|Lösenordet som används för att dekryptera keystore. Android kräver att alla appaket (.apk) signeras. Använd Java Key Tool för att generera KeyStorePassword. Läs mer om [nyckellagret](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) i Java här.| |
|**-KeyAlias**&lt;sträng&gt;|Namnet på nyckeln som ska användas för signering.| |
|**-KeyPassword**&lt;säkerSträng&gt;|Lösenordet som används för att dekryptera den privata nyckeln som ska användas för signering.| |
|**-SigAlg**&lt;säkerSträng&gt;| (Valfritt) Namnet på signaturalgoritmen som ska användas för signering. Algoritmen måste vara kompatibel med den privata nyckeln.|Exempel: SHA256withRSA, SHA1withRSA, MD5withRSA|
| **&lt;CommonParameters&gt;** | (Valfritt) Kommandot stöder vanliga PowerShell-parametrar som utförlig, felsökning osv. |


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
Kör appomslutningsverktyget i den interna appen **HelloWorld.apk**. 
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Du kommer sedan att uppmanas ange **KeyStorePassword** och **KeyPassword**. Ange de autentiseringsuppgifter som du använde för att skapa nyckellagerfilen.

Den omslutna appen skapas och sparas tillsammans med loggfilen i den sökväg för utdata som du har angett.

## Säkerhetsaspekter vid körning av app-wrapping-verktyget
För att förhindra eventuell förfalskning, avslöjande av information och privilegieangrepp:

-   Kontrollera att indata för affärsprogrammet (LOB), utdataappen och Java KeyStore finns på samma dator där appomslutningsverktyget körs.

-   Importera utdataappen till Intune-konsolen på samma dator där verktyget körs. Se [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) om du vill ha mer information om Java keytool.

-   Om utdataappen och verktyget finns på en UNC-sökväg (Universal Naming Convention) och du inte kör verktyget och indatafilerna på samma dator, konfigurerar du en säker miljö med hjälp av [IPsec (Internet Protocol Security)](http://en.wikipedia.org/wiki/IPsec) eller [signering med SMB (Server Message Block)](https://support.microsoft.com/en-us/kb/887429).

-   Kontrollera att programmet kommer från en betrodd källa.

-   Skydda den utdatakatalog som innehåller den omslutna appen. Fundera på att i stället använda en katalog på användarnivå för utdatan.



### Se även
- [Förbereda appar för hantering av mobilprogram med Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Aktivera hantering av mobilprogram i appar med SDK](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Oct16_HO2-->


