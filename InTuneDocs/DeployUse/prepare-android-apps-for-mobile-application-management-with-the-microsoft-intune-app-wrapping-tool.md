---
title: Omsluta Android-appar med apphanteringsverktyget | Microsoft Intune
description: "Använd informationen i det här avsnittet för att lära dig hur du omsluter Android-appar utan att ändra koden i själva appen. Förbered apparna så att du kan använda hanteringsprinciper för mobilprogram."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: matgates
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: be1ebcdf2514e45d383dd49890e0e21acf6ede44
ms.openlocfilehash: 061bde9155c30bf8d7063d40478bbdf35fc7b53a


---

# Förbereda Android-appar för hantering av mobilprogram med Intunes programhanteringsverktyg
Använd **Microsoft Intunes programhanteringsverktyg för Android** för att ändra funktionssättet för interna Android-appar, så att du kan konfigurera funktionerna i appen utan att ändra koden för själva appen.

Verktyget är ett kommandoradsprogram för Windows som körs i PowerShell och skapar en omslutning runt en app. När appen har bearbetats kan du ändra appens funktioner med [hanteringsprinciper för mobilprogram](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) som du konfigurerar.

Om appen använder sig av Azure Active Directory Authentication Library (ADAL) måste du slutföra stegen i [Hur du omsluter appar som använder sig av Azure Active Directory Library](#how-to-wrap-apps-that-use-the-azure-active-directory-library) innan du omsluter appen. Om du är osäker på om din app använder det här biblioteket kan du kontakta apputvecklaren.

Se [Säkerhetsaspekter vid körning av programhanteringsverktyget](#security-considerations-for-running-the-app-wrapping-tool) innan du kör verktyget. För att ladda ned verktyget går du till [Microsoft Intunes apphanteringsverktyg för Android](https://www.microsoft.com/download/details.aspx?id=47267).

## Steg 1 Uppfyll nödvändiga krav för att använda programhanteringsverktyget

-   Du måste köra app-wrapping-verktyget i en Windows-dator som kör Windows 7 eller senare.

-   Din indataapp måste vara ett giltigt Android-programpaket med tillägget **.apk** och:

    -   Går inte att kryptera

    -   Måste redan ha omslutits med app-wrapping-verktyget

    -   Måste vara skriven för Android 4.0 eller senare

-   Appen måste ha utvecklats av eller för ditt företag. Du kan inte använda verktyget för att bearbeta appar som hämtats från Google Play-butiken.

-   För att kunna köra programhanteringsverktyget måste du installera den senaste versionen av [Java Runtime Environment](http://java.com/download/) och sedan kontrollera att Java-sökvägsvariabeln är inställd på **C:\ProgramData\Oracle\Java\javapath** i Windows-miljövariablerna. Mer hjälp finns i din [Java-dokumentation](http://java.com/download/help/).

    > [!NOTE]
    > I vissa fall kan 32-bitarsversionen av Java orsaka minnesproblem. Vi rekommenderar att du installerar 64-bitarsversionen istället.

## Steg 2 Installera programhanteringsverktyget

1.  Från Microsoft Download Center hämtar du och öppnar installationsfilen för app-wrapping-verktyget i en Windows-dator.

2.  Godkänn licensavtalet och slutför sedan installationen.

Kom ihåg vilken mapp du installerade verktyget i. Standardplatsen är: **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**.

## Steg 3 Kör programhanteringsverktyget

1.  På den Windows-dator där du installerade apphanteringsverktyget öppnar du ett PowerShell-fönster i administratörsläge.

2.  Från mappen där du installerade verktyget importerar du PowerShell-modulen för app-wrapping-verktyget:

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  Kör verktyget genom att använda kommandot **invoke-AppWrappingTool** tillsammans med följande parametrar. Parametrar som markerats som "valfritt" är för appar som använder sig av Azure Active Directory Library (ADAL). Mer information finns i [Hur du omsluter appar som använder sig av Azure Active Directory Library](#how-to-wrap-apps-that-use-the-azure-active-directory-library).

|Parameter|Mer information|Exempel|
|-------------|--------------------|---------|
|**-InputPath**&lt;sträng&gt;|Sökvägen till käll-Android-appen (.apk).| |
|**-OutputPath**&lt;sträng&gt;|Sökväg till "utdata" Android-appen. Om det här är samma mapp-sökväg som för InputPath, så kommer paketeringen misslyckas.| |
|**-KeyStorePath**&lt;sträng&gt;|Sökväg till keystore-filen som innehåller det offentliga/privata nyckelparet för signering.| |
|**-KeyStorePassword**&lt;säkerSträng&gt;|Lösenordet som används för att dekryptera keystore. Android kräver att alla appaket (.apk) signeras. Använd Java Key Tool för att generera KeyStorePassword enligt exemplet. Läs mer om [keystore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html).|keytool.exe -genkey -v -keystore keystorefile -alias ks -keyalg RSA -keysize 2048 -validity 50000 |
|**-KeyAlias**&lt;sträng&gt;|Namnet på nyckeln som ska användas för signering.| |
|**-KeyPassword**&lt;säkerSträng&gt;|Lösenordet som används för att dekryptera den privata nyckeln som ska användas för signering.| |
|**-SigAlg**&lt;säkerSträng&gt;|Namnet på signaturalgoritmen som ska användas för signering. Algoritmen måste vara kompatibel med den privata nyckeln.|Exempel: SHA256withRSA, SHA1withRSA, MD5withRSA|
|**-ClientID**&lt;GUID&gt;|Azure Active Directory klient-id för inkommande app (valfritt).| |
|**-AuthorityURI**&lt;URI&gt;|Azure Active Directory utfärdar-URI för inkommande app (valfritt).| |
|**-SkipBroker**&lt;boolesk&gt;|Anger om den inkommande appen stöder förhandlad enkel inloggning över hela enheten (valfritt). |**True** – indataappen stöder inte förhandlad enkel inloggning över hela enheten. Använd parametern NonBrokerRedirectURI. **False** – indataappen stöder förhandlad enkel inloggning över hela enheten.|
|**-NonBrokerRedirectURI**&lt;URI&gt;|Azure Active Directory omdirigerings-URI att använda om SkipBroker är true (valfritt).|  |


**&lt;CommonParameters&gt;**
    (valfri – stöder vanliga PowerShell-parametrar som t.ex. verbose, debug m.m.)

- En lista med vanliga parametrar finns i [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx).

- Om du behöver hjälp för verktyget anger du kommandot:

    ```
    Help Invoke-AppWrappingTool
    ```
- Mer information om Azure Active Directory-integration (AAD) finns i [Hur du omsluter appar som använder sig av Azure Active Directory Library](#how-to-wrap-apps-that-use-the-azure-active-directory-library).

**Exempel:**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app.wrapped\HelloWorld_wrapped2.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\keystorefile" -keyAlias ks -SigAlg SHA1withRSA -Verbose

Du kommer sedan att uppmanas ange **KeyStorePassword** och **KeyPassword**.

Den omslutna appen skapas och sparas tillsammans med loggfilen i den sökväg för utdata som du har angett.

## Säkerhetsaspekter vid körning av app-wrapping-verktyget
För att förhindra eventuell förfalskning, avslöjande av information och privilegieangrepp:

-   Kontrollera att indata för affärsprogrammet, utdataappen och Java KeyStore finns på samma dator där app-wrapping-verktyget körs.

-   Importera utdataappen till Intune-konsolen på samma dator där verktyget körs. Se [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) om du vill ha mer information om Java keytool.

-   Om utdataappen och verktyget finns på en UNC-sökväg (Universal Naming Convention) och du inte kör verktyget och indatafilerna på samma dator, konfigurerar du en säker miljö med hjälp av [IPsec (Internet Protocol Security)](http://en.wikipedia.org/wiki/IPsec) eller [signering med SMB (Server Message Block)](https://support.microsoft.com/en-us/kb/887429).

-   Kontrollera att programmet kommer från en betrodd källa, särskilt om du använder AAD (Azure Active Directory), vilket kan ge programmet åtkomst till AAD-token under körningen.

-   Skydda den utdatakatalog som innehåller den omslutna appen. Fundera på att i stället använda en katalog på användarnivå för utdatan.

## Hur du omsluter appar som använder sig av Azure Active Directory Library
Om din app använder sig av Azure Active Directory Authentication Library (ADAL), så måste du slutföra de här stegen innan du omsluter din app.

### Steg 1 Se till att du uppfyller kraven för ADAL
Följande villkor måste vara uppfyllda för appar som använder ADAL:

-   Appen måste innehålla ADAL version 1.0.2 eller högre

-   Utvecklaren måste ge sin app åtkomst till resursen för hantering av mobilprogram i Intune, enligt beskrivningen i [Steg 3 Konfigurera åtkomst till hantering av mobilprogram i AAD](#step-3-configure-access-to-mobile-app-management-in-aad).

### Steg 2 Granska de identifierare som du måste hämta när du registrerar appen
I nästa steg ska du använda Azures hanteringsportal för att registrera dina appar (som använder ADAL med Azure Active Directory (AAD)) för att hämta de unika identifierare som listas i följande tabell. Du ger sen identifierarna till utvecklaren när du integrerar ADAL med appen.

|Identifierare|Mer information|Standardvärde|
|--------------|--------------------|-----------------|
|**Klient-ID**|En unik GUID-identifierare som genereras för appen efter att den registrerats med AAD.<br /><br />Om du känner till appens klient-id, kan du ange det värdet. Annars använder du standardvärdet.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**Utfärdare-URI**|Utfärdarens enhetliga resursidentifierar(URI)-värde för AAD)-objekt (exempelvis användare och grupper).<br /><br />AuthorityURI-parametern är valfri för appomslutnings-verktyget. Om du inte använder parametern används standard-URI:n.||
|**SkipBroker**|Värdet anger om företagsportalen kommer användas som förhandlare.<br /><br />**True** – företagsportalen kommer inte att användas för ADAL-autentisering.<br /><br />**False** – företagsportalen kommer att användas för ADAL-autentisering. Företagsportalen använder den registrerade användaren för enkel inloggning.||
|**Icke-förhandlad omdirigerings-URI**|Inloggnings-URI som används när ADAL inte använder sig av förhandlings-appen (Intunes företagsportal).|urn:ietf:wg:oauth:2.0:oob|
|**Resurs-ID**|Pekar till appens AAD resurser.||

### Steg 3 Konfigurera åtkomst till hantering av mobilappar i AAD
Innan du kan använda en apps AAD-registreringsvärden i programhanteringsverktyget måste apputvecklaren bevilja den appen åtkomst till resursen för hantering av mobilprogram i Intune genom att följa de här stegen:

1.  Logga in på ett befintligt AAD-konto i Azures hanteringsportal.

2.  Välj **befintlig LOB-appregistrering**.

3.  I avsnittet **konfigurera** , väljer du **Konfigurera åtkomst till Web-API:er i andra applikationer**.

4.  I den första listrutan i avsnittet **Behörighet till andra program** väljer du **Hantering av mobilprogram i Intune**.

Du kan nu använda appens klient-ID i appomslutnings-verktyget. Du hittar klient-ID:t i hanteringsportalen för Azure Active Directory, enligt beskrivningen i tabellen i [Steg 2 Granska de identifierare som du måste hämta när du registrerar appen](#step-2-review-the-identifiers-you-need-to-get-when-you-register-the-app).

### Steg 4 Använd AAD-identifierarvärdena i programhanteringsverktyget
Använd de identifierarvärden du fick från registreringsprocessen och fyll i värdena som kommandorads-egenskaper i appomslutnings-verktyget. Du måste ange alla värdena i tabellen för att slutanvändare ska kunna autentisera appen. Om du inte anger ett värde används standardvärden.

|Identifierare|Parameter|
|--------------|-------------|
|Klient-ID|ClientID|
|Utfärdare-URI|Authority-URI|
|SkipBroker|SkipBroker|
|Icke-förhandlad omdirigerings-URI|NonBrokerRedirectURI|
|Resurs-ID|ResourceID|
Tänk på följande när du omsluter dina appar:

-   För att verifiera att autentiseringen lyckades, så hämtar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] den AAD-token som är associerad med resurs-ID:t för MAM. Den här token används dock inte för något anrop som i sin tur kunde varifiera tokens giltighet. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] läser bara UPN (User Principal Name) för den inloggade användaren för att fastställa appåtkomst. AAD-token används inte för ytterligare tjänstanrop.

-   Dubbla inloggningsprompter förhindras om du tillhandahåller din klientapplikations klient-ID och utfärdar-URI. Du behöver registrera klient-ID för att den ska kunna ha åtkomst till det publicerade [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM-resurs-ID:t i AAD-instrumentpanelen. Om du inte registrerar klient-ID:t, möts användarna av ett inloggningsfel när appen körs.


### Se även
- [Förbereda appar för hantering av mobilprogram med Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Aktivera hantering av mobilprogram i appar med SDK](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Jul16_HO5-->


