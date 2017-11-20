---
title: "Principinställningar för Android-appskydd"
titlesuffix: Azure portal
description: "Det här ämnet beskriver inställningarna för appskyddsprinciper för Android-enheter.”"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9e9ef9f5-1215-4df1-b690-6b21a5a631f8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2383d41c52618710a1d42f0b2236d41d117b42be
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/08/2017
---
# <a name="android-app-protection-policy-settings"></a>Principinställningar för Android-appskydd
Principinställningarna som beskrivs i det här avsnittet kan [konfigureras](app-protection-policies.md) för en appskyddsprincip på bladet **Inställningar** i Azure-portalen.
Det finns två kategorier för principinställningar: inställningar för dataflytt och åtkomst. I det här avsnittet används termen *principhanterade appar* för att hänvisa till appar som har konfigurerats med appskyddsprinciper.

##  <a name="data-relocation-settings"></a>Inställningar för dataflytt

| Inställningar | Använd så här | Standardvärde(n) |
|------|------|------|
| **Förhindra Android-säkerhetskopieringar** | Välj **Ja** för att förhindra att den här appen säkerhetskopierar arbets- eller skoldata i [Android Backup Service](https://developer.android.com/google/backup/index.html) Välj **Nej** för att tillåta att den här appen säkerhetskopierar arbets- eller skoldata.| Ja |
| **Tillåt att appen överför information till andra appar** | Ange vilka appar som kan ta emot data från den här appen: <ul><li> **Principhanterade appar**: Tillåt endast överföring till andra principhanterade appar.</li> <li>**Alla appar**: Tillåt överföring till alla appar. </li> <li>**Inga**: Tillåt inte dataöverföring till någon app, inklusive andra principhanterade appar.</li></ul> <p>Det finns vissa undantag för appar och tjänster som Intune kan tillåta dataöverföring till. En fullständig lista över appar och tjänster finns i avsnittet [Undantag vid dataöverföring](#Data-transfer-exemptions).<p>**Obs!** Intune har för närvarande inte stöd för funktionen Android Instant Apps. Intune blockerar alla dataanslutningar till och från appen.  I dokumentationen för Android Developer finns mer information om [Android Instant Apps](https://developer.android.com/topic/instant-apps/index.html).</p>| Alla appar |
| **Tillåt att appen hämtar data från andra appar** | Ange vilka appar som kan överföra data till den här appen: <ul><li>**Principhanterade appar**: Tillåt endast överföring från andra principhanterade appar.</li><li>**Alla appar**: Tillåt dataöverföring från alla appar.</li><li>**Ingen**: Tillåt inte dataöverföring från någon app, inklusive andra principhanterade appar. </li></ul> <p>Det finns vissa undantag för appar och tjänster som Intune kan tillåta dataöverföring från. En fullständig lista över appar och tjänster finns i avsnittet [Undantag vid dataöverföring](#Data-transfer-exemptions). | Alla appar |
| **Förhindra "Spara som"** | Välj **Ja** om du vill inaktivera alternativet Spara som i den här appen. Välj **Nej** om du vill tillåta att Spara som används. <p><br>**Välj med vilka lagringstjänster företagsdata ska sparas** <br>Användare kan spara de valda tjänsterna (OneDrive för företag, SharePoint och lokal lagring). Alla andra tjänster kommer att blockeras.</p> | Nej <br><br> 0 valda |
| **Begränsa klipp ut, kopiera och klistra in med andra appar** | Ange när åtgärderna klippa ut, kopiera och klistra in kan användas med den här appen. Välj mellan: <ul><li>**Blockerad**: Tillåt inte åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra appar.</li><li>**Principhanterade appar**: Tillåt endast åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra principhanterade appar.</li><li>**Principhanterade appar med inklistring**: Tillåt klipp ut och kopiera mellan den här appen och andra principhanterade appar. Tillåt att data från en annan app klistras in i den här appen.</li><li>**Alla appar**: Inga begränsningar för klipp ut, kopiera och klistra in till och från den här appen. | Alla appar |
|**Begränsa webbinnehåll till visning i Managed Browser** | Välj **Ja** för att tvinga webblänkar i appen att öppnas i appen Managed Browser. <br><br> För enheter som inte har registrerats i Intune kan webblänkar i principhanterade appar endast öppnas i appen Managed Browser. <br><br> Om du använder Intune för att hantera dina enheter läser du [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](app-configuration-managed-browser.md). | Nej |
| **Kryptera appdata** | Välj **Ja** om du vill aktivera kryptering av arbets- eller skoldata i den här appen. Intune använder ett OpenSSL-baserat 128-bitars krypteringsschema tillsammans med Android Keystore-systemet för att kryptera appdata på ett säkert sätt. Data krypteras synkront under I/O-åtgärder. Innehållet i enhetens lagringsutrymme krypteras alltid. <br><br> Krypteringsmetoden är **inte** FIPS 140-2-certifierad.  | Ja |
| **Inaktivera appkryptering när enhetskryptering är aktiverat** | Välj **Ja** om du vill inaktivera appkryptering för intern applagring när enhetskryptering identifieras på en registrerad enhet. <br><br>**Obs!** Intune kan endast identifiera enhetsregistrering med Intune MDM. Extern applagring krypteras fortfarande för att säkerställa att data inte kan nås av ohanterade program. | Ja |
| **Inaktivera synkronisering av kontakter** | Välj **Ja** att förhindra att appen sparar data i den interna appen Kontakter på enheten. Om du väljer **Nej** kan appen spara data i den interna appen Kontakter på enheten. <br><br>När du utför en selektiv rensning för att ta bort arbets- eller skoldata från appen kommer kontakter som har synkats direkt från appen till den inbyggda appen Kontakter att tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen. | Nej |
| **Inaktivera utskrift** | Välj **Ja** att förhindra att appen skriver ut arbets- eller skoldata. | Nej |

  >[!NOTE]
  >Krypteringsmetoden för inställningen **Kryptera appdata** är **inte** FIPS 140-2-certifierad.

  ## <a name="data-transfer-exemptions"></a>Undantag vid dataöverföring

  Det finns vissa undantag för appar och plattformstjänster som Intune-appskyddsprinciper kan tillåta dataöverföring till och från. Till exempel måste alla Intune-medvetna appar för Android kunna överföra data till och från Googles ”text till tal”-funktion, så att text från mobilenhetens skärm kan läsa upp. Den här listan kan ändras och innehåller de tjänster och program som anses vara användbara för säker produktivitet.

  ### <a name="full-exemptions"></a>Fullständiga undantag

  Dessa appar och tjänster har full tillåtelse att överföra data till och från Intune-hanterade appar.

  |App-/tjänstnamn | Beskrivning |
  | ------ | ---- |
  | com.android.phone | Intern telefonapp
  | com.android.vending | Google Play Store |
  | com.android.documentsui | Android-dokumentväljare|
  | com.google.android.webview | [WebView](https://developer.android.com/reference/android/webkit/WebView.html), som krävs för många appar, däribland Outlook. |
  | com.android.webview |[Webview](https://developer.android.com/reference/android/webkit/WebView.html), som krävs för många appar, däribland Outlook.|
  | com.google.android.tts | Googles ”text till tal”-funktion |
  | com.android.providers.settings | Android-systeminställningar |
  | com.azure.authenticator | Azure Authenticator-appen, som krävs för autentisering i många scenarier. |
  | com.microsoft.windowsintune.companyportal | Intune Företagsportal|

  ### <a name="conditional-exemptions"></a>Villkorliga undantag
  Dessa appar och tjänster kan överföra data till och från Intune-appar under vissa omständigheter.

  |App-/tjänstnamn | Beskrivning | Villkor för undantag|
  | ------ | ---- | --- |
  | com.android.chrome | Webbläsaren Google Chrome | Chrome används för vissa WebView-komponenter i Android 7.0+ och är aldrig dolt. Dataflödet till och från appen är dock alltid begränsat.
  | com.skype.raider | Skype | Skype-appen tillåts endast för vissa åtgärder som resulterar i ett telefonsamtal. |
  | com.android.providers.media | Androids medieinnehållsprovider | Medieinnehållsprovidern tillåts endast för val av ringsignal. |
  | com.google.android.gms; com.google.android.gsf | Google Play Services-paket | Dessa paket tillåts för Google Cloud Messaging-åtgärder, till exempel push-meddelanden. |



##  <a name="access-settings"></a>Åtkomstinställningar

| Inställningar | Använd så här | Standardvärde(n) |
|------|------|------|
| **Kräv PIN-kod för åtkomst** | Välj **Ja** för att kräva en PIN-kod för att använda den här appen. Användarna uppmanas att konfigurera denna PIN-kod första gången de kör appen i en arbets- eller skolkontext. Standardvärde = **Ja**.<br><br> Konfigurera följande inställningar för PIN-styrka: <ul><li>**Antal försök före återställning av PIN**: Ange antalet försök som användaren har att ange rätt PIN-kod innan den måste återställas. Standardvärde = **5**.</li><li> **Tillåt enkel PIN-kod:** Välj **Ja** du om du vill tillåta att användarna använder enkla PIN-kodssekvenser, till exempel 1234 eller 1111. Välj **Nej** om du vill förhindra att de använder enkla sekvenser. Standardvärde = **Ja**. </li><li> **PIN-kodslängd**: Ange det minsta antalet siffror i en PIN-kodssekvens. Standardvärde = **4**. </li><li> **Kräv fingeravtryck istället för PIN (Android 6.0+)**: Välj **Ja** om du vill kräva att [autentisering med fingeravtryck](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) används i stället för en PIN-kod för åtkomst till appen. Standardvärde = **Ja**.</li></ul> På Android-enheter kan du låta användaren bekräfta sin identitet med hjälp av [Android-autentisering med fingeravtryck](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) i stället för en PIN-kod. När användarna försöker använda appen med ett arbets- eller skolkonto uppmanas de att lämna sitt fingeravtryck i stället för att ange en PIN-kod. </li></ul>| Kräv PIN-kod: Ja <br><br> PIN-återställningsförsök: 5 <br><br> Tillåt enkel PIN-kod: Ja <br><br> PIN-kodslängd: 4 <br><br> Tillåt fingeravtryck: Ja |
| **Kräv företagets autentiseringsuppgifter för åtkomst** | Välj **Ja** om du vill kräva att användaren loggar in med sitt arbets- eller skolkonto i stället för att ange en PIN-kod för åtkomst till appen. Om du väljer **Ja** åsidosätts kraven på PIN-kod eller Touch ID.  | Nej |
| **Hindra hanterade appar från att köras på jailbrokade eller rotade enheter** |Välj **Ja** om du vill förhindra att den här appen körs på jailbrokade eller rotade enheter. Användaren kan fortfarande använda apparna för personliga uppgifter, men måste använda en annan enhet för att komma åt arbets- eller skoldata i denna app. | Ja |
| **Kontrollera åtkomstbehörigheterna på nytt efter (minuter)** | Konfigurera följande inställningar: <ul><li>**Tidsgräns**: Det här är antalet minuter innan åtkomstkraven (definieras tidigare i principen) kontrolleras. En administratör kan till exempel aktivera PIN-kod i principen, så om en användare öppnar en MAM-app måste denne ange en PIN-kod. När du använder den här inställningen behöver användaren inte ange en PIN-kod i någon MAM-app under ytterligare **30 minuter** (standardvärde).</li><li>**Offlinerespittid**: Det här är antalet minuter som MAM-appar kan köras offline, specificera tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen. Standardvärde = **720** minuter (12 timmar). När denna tid har gått ut kräver appen användarautentisering till AAD, så att appen kan fortsätta att köras.</li></ul>| Tidsgräns: 30 <br><br> Offline: 720 |
| **Offlineintervall innan appdata rensas (dagar)** | Efter så här många dagars (definieras av administratören) offlinekörning kräver appen att användaren ansluter till nätverket och autentiserar igen. Vid lyckad autentisering kan användaren fortsätta att få åtkomst till sina data och offlineintervallet återställs.  Om autentiseringen misslyckas utför appen en selektiv rensning av användarens konto och data.  Se [Hur du rensar endast företagsdata från Intune-hanterade appar](https://docs.microsoft.com/en-us/intune/apps-selective-wipe) om du vill ha mer information om vilka data som tas bort med en selektiv rensning.<br><br> | 90 dagar |
| **Blockera skärmdump och Android Assistant (Android 6.0+)** | Välj **Ja** om du vill blockera funktionerna för skärmdumpar och **Android-assistenten** på enheten när appen används. Om du väljer **Ja** blir även förhandsgranskningsbilden i appväxlaren suddig när den här appen används med ett arbets- eller skolkonto. | Nej |
| **Inaktivera appens PIN-kod när enheten PIN-kod hanteras** | Välj **Ja** om du vill inaktivera appens PIN-kod när ett enhetslås har identifierats på en registrerad enhet. | Nej |
| **Minimikrav på Android-operativsystem** | Välj **Ja** för att ange ett minimikrav på det Android-operativsystem som ska använda appen. Användaren kommer att blockeras från åtkomst om Android-versionen på enheten inte uppfyller kravet. | Nej |
| **Minimikrav på Android-operativsystem (endast varning)** | Välj **Ja** för att ange ett minimikrav på det Android-operativsystem som ska använda appen. Användaren kommer att få ett meddelande ifall Android-versionen på enheten inte uppfyller kravet. Det här meddelandet kan avvisas. | Nej |
| **Minimikrav på appversion** | Välj **Ja** för att ange ett minimikrav på appversionen för att använda appen. Användaren kommer att blockeras från åtkomst om appversionen på enheten inte uppfyller kraven.<br><br>När du väljer vilka appar det ska gälla ska du lägga märke till att appar ofta har olika versionsscheman.<br><br> | Nej | 
| **Minimikrav på appversion (endast varning)** | Välj **Ja** för att rekommendera ett minimikrav på den appversion som ska använda den här appen. Användaren kommer att få ett meddelande om appversionen på enheten inte uppfyller kraven. Det här meddelandet kan avvisas.<br><br>När du väljer vilka appar det ska gälla ska du lägga märke till att appar ofta har olika versionsscheman.<br><br> | Nej | 
| **Kräv lägsta Android-uppdateringsversion** | Välj **Ja** om du vill kräva en lägsta Android-säkerhetsuppdatering som har publicerats av Google. Användaren kommer att blockeras från åtkomst om Android-säkerhetsuppdateringen på enheten inte uppfyller kravet. | Nej |
| **Kräv lägsta Android-uppdateringsversion (endast varning)** | Välj **Ja** om du vill kräva en lägsta Android-säkerhetsuppdatering som har publicerats av Google. Användaren kommer att få ett meddelande om Android-säkerhetsuppdateringen på enheten inte uppfyller kravet. Det här meddelandet kan avvisas. | Nej |