---
title: "Principinställningar för iOS-appskydd"
titlesuffix: Azure portal
description: "Det här ämnet beskriver inställningarna för appskyddsprinciper för iOS-enheter.”"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 268cd673ccb21dffcd8424cfc49c55c734312bff
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2018
---
#  <a name="ios-app-protection-policy-settings"></a>Principinställningar för iOS-appskydd
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

De principinställningar som beskrivs i det här avsnittet kan [konfigureras](app-protection-policies.md) för en appskyddsprincip på bladet **Inställningar** i Azure-portalen.

Det finns två kategorier för principinställningar: inställningar för dataflytt och åtkomst. I det här avsnittet används termen ***principhanterade appar*** för att hänvisa till appar som har konfigurerats med appskyddsprinciper.

##  <a name="data-relocation-settings"></a>Inställningar för dataflytt

| Inställningen | Använd så här | Standardvärde |
|------|------|------|
| **Förhindra säkerhetskopiering av iTunes och iCloud** | Välj **Ja** för att förhindra att den här appen säkerhetskopierar arbets- eller skoldata till iTunes och iCloud. Välj **Nej** för att tillåta att den här appen säkerhetskopierar arbets- eller skoldata till iTunes och iCloud.| Ja |
| **Tillåt att appen överför information till andra appar** | Ange vilka appar som kan ta emot data från den här appen: <ul><li> **Principhanterade appar**: Tillåt endast överföring till andra principhanterade appar.</li> <li>**Alla appar**: Tillåt överföring till alla appar. </li> <li>**Inga**: Tillåt inte dataöverföring till någon app, inklusive andra principhanterade appar.</li></ul> Om du anger det här alternativet till **Principhanterade appar** eller **Ingen** blockeras dessutom iOS 9-funktionen som gör att Spotlight-sökning kan söka efter data i appar. <br><br> Det finns vissa undantag för appar och tjänster som Intune kan tillåta dataöverföring till. En fullständig lista över appar och tjänster finns i avsnittet [undantag vid dataöverföring](#data-transfer-exemptions). | Alla appar |
| **Tillåt att appen hämtar data från andra appar** | Ange vilka appar som kan överföra data till den här appen: <ul><li>**Principhanterade appar**: Tillåt endast överföring från andra principhanterade appar.</li><li>**Alla appar**: Tillåt dataöverföring från alla appar.</li><li>**Ingen**: Tillåt inte dataöverföring från någon app, inklusive andra principhanterade appar.</li></ul> Det finns vissa undantag för appar och tjänster som Intune kan tillåta dataöverföring från. En fullständig lista över appar och tjänster finns i avsnittet [undantag vid dataöverföring](#data-transfer-exemptions). MAM-aktiverade program med flera identiteter på icke-registrerade iOS-enheter ignorerar den här principen och tillåter alla inkommande data. | Alla appar |
| **Förhindra "Spara som"** | Välj **Ja** om du vill inaktivera alternativet Spara som i den här appen. Välj **Nej** om du vill tillåta att Spara som används. | Nej |
| **Begränsa klipp ut, kopiera och klistra in med andra appar** | Ange när åtgärderna klippa ut, kopiera och klistra in kan användas med den här appen. Välj mellan: <ul><li>**Blockerad**: Tillåt inte åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra appar.</li><li>**Principhanterade appar**: Tillåt endast åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra principhanterade appar.</li><li>**Principhanterade appar med inklistring**: Tillåt klipp ut och kopiera mellan den här appen och andra principhanterade appar. Tillåt att data från en annan app klistras in i den här appen.</li><li>**Alla appar**: Inga begränsningar för klipp ut, kopiera och klistra in till och från den här appen. | Alla appar |
|**Begränsa webbinnehåll till visning i Managed Browser** | Välj **Ja** för att tvinga webblänkar i appen att öppnas i appen Managed Browser. <br><br> För enheter som inte har registrerats i Intune kan webblänkar i principhanterade appar endast öppnas i appen Managed Browser. <br><br> Om du använder Intune för att hantera dina enheter läser du [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](app-configuration-managed-browser.md). | Nej |
| **Kryptera appdata** | För principer för hanterade program krypteras data i viloläge med hjälp av krypteringsschemat på enhetsnivån som tillhandahålls av iOS. När en PIN-kod krävs krypteras data enligt inställningarna i appskyddsprincipen. <br><br> Gå till den officiella Apple-dokumentationen [här](https://support.apple.com/HT202739) för att se vilka iOS-krypteringsmoduler som är FIPS 140-2-certifierade eller väntar på FIPS 140-2-certifiering. <br><br> Ange när arbets- eller skoldata i den här appen ska krypteras. Välj mellan: <ul><li>**När enheten är låst**: Alla appdata som är associerade med den här principen krypteras när enheten är låst.</li><li>**När enheten är låst och det finns öppna filer**: Alla appdata som är associerade med den här principen krypteras när enheten är låst, utom data i filer som är öppna i appen.</li><li>**Efter omstart av enheten**: Alla appdata som är associerade med den här principen krypteras när enheten startas om, tills den första gången enheten låses upp.</li><li>**Använd enhetsinställningar**: Appdata krypteras baserat på standardinställningarna på enheten. </li></ul> När du aktiverar den här inställningen kanske användaren måste konfigurera och använda en PIN-kod för att komma åt sin enhet.  Om det inte finns någon PIN-kod för enheten och kryptering krävs startar inte apparna och användaren uppmanas att ange en PIN-kod. Ett meddelande visas som informerar användaren om att dennes organisation kräver att enheten har en PIN-kod för att det ska gå att komma åt appen.  | När enheten är låst |
| **Inaktivera synkronisering av kontakter** | Välj **Ja** att förhindra att appen sparar data i den interna appen Kontakter på enheten. Om du väljer **Nej** kan appen spara data i den interna appen Kontakter på enheten. <br><br>När du utför en selektiv rensning för att ta bort arbets- eller skoldata från appen kommer kontakter som har synkats direkt från appen till den inbyggda appen Kontakter att tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen. | Nej |
| **Inaktivera utskrift** | Välj **Ja** att förhindra att appen skriver ut arbets- eller skoldata. | Nej |
| **Välj med vilka lagringstjänster företagsdata ska sparas** | Användare kan spara de valda tjänsterna (OneDrive för företag, SharePoint och lokal lagring). Alla andra tjänster kommer att blockeras. | 0 valda |

> [!NOTE]
> Ingen av inställningarna för dataflytt styr den Apple-hanterade ”öppna med”-funktionen på iOS-enheter. Se [Hantera dataöverföring mellan iOS-appar med Microsoft Intune](data-transfer-between-apps-manage-ios.md) för hantering av ”öppna med”.

## <a name="data-transfer-exemptions"></a>Undantag vid dataöverföring

Det finns vissa undantag för appar och plattformstjänster som Intune-appskyddsprinciper kan tillåta dataöverföring till och från i vissa scenarion. Den här listan kan ändras och innehåller de tjänster och program som anses vara användbara för säker produktivitet.

| App-/tjänstnamn | Description |
| ---- | --- |
|<code>tel; telprompt</code> | Intern telefonapp |
| <code>skype</code> | Skype |
| <code>app-settings</code> | Enhetsinställningar |
| <code>itms; itmss; itms-apps; itms-appss; itms-services</code> | Appbutik |
| <code>calshow</code> | Intern kalender |




## <a name="access-settings"></a>Åtkomstinställningar

| Inställningen | Använd så här | Standardvärde |
|------|------|------|
| **Kräv PIN-kod för åtkomst** | Välj **Ja** för att kräva en PIN-kod för att använda den här appen. Användarna uppmanas att konfigurera denna PIN-kod första gången de kör appen i en arbets- eller skolkontext. PIN-koden tillämpas när du arbetar online eller offline. Standardvärde = **Ja**.<br><br> Konfigurera följande inställningar för PIN-styrka: <ul><li>**Välj typ**: Ange ett krav för PIN-koder av numerisk typ eller lösenordstyp innan du använder en app som appskyddsprinciper tillämpas för. Numeriska krav har endast siffror, medan ett lösenord kan definieras med minst en bokstav eller ett specialtecken. Standardvärde = **Numerisk**.</li><li>**Antal försök före återställning av PIN**: Ange antalet försök som användaren har att ange rätt PIN-kod innan den måste återställas. Standardvärde = **5**. <br> Det här principinställningsformatet stöder ett positivt heltal.</li><li> **Tillåt enkel PIN-kod:** Välj **Ja** du om du vill tillåta att användarna använder enkla PIN-kodssekvenser, till exempel 1234, 1111, absd eller aaaa. Välj **Nej** om du vill förhindra att de använder enkla sekvenser. Standardvärde = **Ja**. </li><li> **PIN-kodslängd**: Ange det minsta antalet siffror i en PIN-kodssekvens. Standardvärde = **4**. </li><li> **Kräv fingeravtryck istället för PIN (iOS 8.0+)**: Välj **Ja** om du vill kräva att [Touch-ID](https://support.apple.com/HT201371) används i stället för en PIN-kod för åtkomst till appen. Standardvärde = **Ja**.</li><li> **Tillåt ansiktsigenkänning istället för PIN-kod (iOS 11+)**: Välj **Ja** om du vill tillåta att [Face ID](https://support.apple.com/HT208109) används i stället för en PIN-kod för åtkomst till appen. Standardvärde = **Ja**. Användare uppmanas att tillhandahålla ansiktsidentifiering när de använder appen med sina arbetskonton.</li><li> **Inaktivera appens PIN-kod när enhetens PIN-kod hanteras**: Välj **Ja** om du vill inaktivera appens PIN-kod när ett enhetslås har identifierats på en registrerad enhet. <br> **Obs!** Appen måste ha Intune SDK-version 7.0.1 eller senare.</li></ul> På iOS-enheter kan du låta användaren bekräfta sin identitet med hjälp av [Touch-ID](https://support.apple.com/HT201371) eller [Face ID](https://support.apple.com/HT208109) i stället för en PIN-kod. Intune använder API:et [LocalAuthentication](https://developer.apple.com/documentation/localauthentication/) för att autentisera användare som använder Touch ID och Face ID. Läs mer om Touch ID och Face ID i [iOS Security Guide](https://www.apple.com/business/docs/iOS_Security_Guide.pdf) (iOS-säkerhetsguiden). När användarna försöker använda appen med ett arbets- eller skolkonto uppmanas de att lämna sitt fingeravtryck eller sin ansiktsidentitet i stället för att ange en PIN-kod. När den här inställningen är aktiverad kommer förhandsgranskningsbilden i appväxlaren att vara suddig när ett arbets- eller skolkonto används. </li></ul><!-- <br><br>You can require a PIN expiration for targeted iOS apps. You can configure the PIN requirement and expiration date in days through the Azure portal. When required, a user will be required to set and use a new PIN before getting access to an iOS app. Only iOS apps that have app protection enabled with the Intune App SDK will support this feature.-->| Kräv PIN-kod för åtkomst: Ja <br><br> Välj typ: Numerisk <br><br> PIN-återställningsförsök: 5 <br><br> Tillåt enkel PIN-kod: Ja <br><br> PIN-kodslängd: 4 <br><br> Tillåt fingeravtryck: Ja <br><br> Tillåt ansiktsigenkänning: Ja <br><br> Inaktivera PIN-kod för app: Nej |
| **Kräv företagets autentiseringsuppgifter för åtkomst** | Välj **Ja** om du vill kräva att användaren loggar in med sitt arbets- eller skolkonto i stället för att ange en PIN-kod för åtkomst till appen. Om du väljer **Ja** åsidosätts kraven på PIN-kod eller Touch ID.  | Nej |
| **Hindra hanterade appar från att köras på jailbrokade eller rotade enheter** |  Välj **Ja** om du vill förhindra att den här appen körs på jailbrokade eller rotade enheter. Användaren kan fortfarande använda apparna för personliga uppgifter, men måste använda en annan enhet för att komma åt arbets- eller skoldata i denna app. | Ja |
| **Kontrollera åtkomstbehörigheterna på nytt efter (minuter)** | Konfigurera följande inställningar: <ul><li>**Tidsgräns**: Det här är antalet minuter innan åtkomstkraven (definieras tidigare i principen) kontrolleras. En administratör kan till exempel aktivera PIN-kod i principen, så om en användare öppnar en Intune-hanterad app måste denne ange en PIN-kod. När du använder den här inställningen behöver användaren inte ange en PIN-kod i någon MAM-app under ytterligare **30 minuter** (standardvärde). <br><br>**Obs!** I iOS delas PIN-koden mellan alla Intune-hanterade appar från **samma utgivare**. PIN-timern för en viss PIN-kod återställs när appen lämnar enhetens förgrund. Användaren behöver inte ange en PIN-kod på någon Intune-hanterad app som delar sin PIN under perioden för den tidsgräns som anges i denna inställning. <br><br> Det här principinställningsformatet stöder ett positivt heltal.</li><li>**Offlinerespittid**: Det här är antalet minuter som MAM-appar kan köras offline, specificera tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen. Standardvärde = **720** minuter (12 timmar). När denna tid har gått ut kräver appen användarautentisering till AAD, så att appen kan fortsätta att köras.<br><br> Det här principinställningsformatet stöder ett positivt heltal.</li></ul>| Tidsgräns: 30 <br><br> Offline: 720 |
| **Offlineintervall innan appdata rensas (dagar)** | Efter detta antal dagar (definieras av administratören) med offlinekörning kräver appen att användaren ansluter till nätverket och autentiserar igen. Vid lyckad autentisering kan användaren fortsätta att få åtkomst till sina data och offlineintervallet återställs.  Om autentiseringen misslyckas utför appen en selektiv rensning av användarens konto och data.  Se [Hur du rensar endast företagsdata från Intune-hanterade appar](https://docs.microsoft.com/intune/apps-selective-wipe) om du vill ha mer information om vilka data som tas bort med en selektiv rensning. <br><br> Det här principinställningsformatet stöder ett positivt heltal. | 90 dagar |
| **Minimikrav på iOS-operativsystem** | Välj **Ja** för att ange ett minimikrav på det iOS-operativsystem som ska använda den här appen. Användaren kommer att blockeras från åtkomst om iOS-versionen på enheten inte uppfyller kraven. <br> **Obs!** Appen måste ha Intune SDK-version 7.0.1 eller senare. | Nej |
| **Minimikrav på iOS-operativsystem (endast varning)** | Välj **Ja** för att ange ett minimikrav på det iOS-operativsystem som ska använda den här appen. Användaren kommer att få ett meddelande om iOS-versionen på enheten inte uppfyller kraven. Det här meddelandet kan avvisas. <br> **Obs!** Appen måste ha Intune SDK-version 7.0.1 eller senare. | Nej |
| **Minimikrav på appversion** | Välj **Ja** för att ange ett minimikrav på appversionen för att använda appen. Användaren blockeras för åtkomst om appversionen på enheten inte uppfyller kravet.<br><br>Eftersom appar ofta har egna versionsscheman kan du skapa en princip med ett minimikrav på appversion riktat mot en specifik app (till exempel, ”Outlook versionsprincip”). <br><br> Det här principinställningsformatet stöder major.minor, major.minor.build, major.minor.build.revision. <br><br> **Obs!** Appen måste ha Intune SDK-version 7.0.1 eller senare. | Nej | 
| **Minimikrav på appversion (endast varning)** | Välj **Ja** för att rekommendera ett minimikrav på den appversion som ska använda den här appen. Användaren får ett meddelande om appversionen på enheten inte uppfyller kravet. Det här meddelandet kan avvisas.<br><br>Eftersom appar ofta har egna versionsscheman kan du skapa en princip med ett minimikrav på appversion riktat mot en specifik app (till exempel, ”Outlook versionsprincip”). <br><br> Det här principinställningsformatet stöder major.minor, major.minor.build, major.minor.build.revision. <br><br> **Obs!** Appen måste ha Intune SDK-version 7.0.1 eller senare. | Nej | 
| **Minimikrav på SDK-version för Intune-skyddsprincip** | Välj **Ja** för att ange ett minimkrav på SDK-version för Intune-skyddsprincip för den app som ska användas. Användaren kommer att blockeras från åtkomst om appens SDK-version för Intune-appskyddsprincipen inte uppfyller kravet. <br> <br> Läs mer om SDK-versionen för Intune-skyddsprincip i [Översikt över Intune App SDK](app-sdk.md). <br><br> Det här principinställningsformatet stöder major.minor, major.minor.build, major.minor.build.revision. <br><br> **Obs!** Appen måste ha Intune SDK-version 7.0.1 eller senare. | Nej |


##  <a name="add-ins-for-outlook-app"></a>Tillägg för Outlook-appen

Outlook införde nyligen iOS-tillägg i Outlook, så att du kan integrera populära appar med e-postklienten. Tillägg för Outlook är tillgängliga för Outlook på webben, Windows, Mac och Outlook för iOS. Eftersom tillägg hanteras via Microsoft Exchange kan användarna dela data och meddelanden via Outlook och ohanterade tilläggsprogram, såvida inte tilläggen har inaktiverats för användarna av Exchange.

Om du vill förhindra slutanvändarna från att få åtkomst till och kunna installera Outlook-tillägg (vilket påverkar alla Outlook-klienter) gör du följande rolländringar i Exchange-administrationscentret:

- Om du vill förhindra användare från att installera Office Store-tillägg tar du bort rollen Min Marketplace från dem.
- Om du vill förhindra användare från att läsa in tillägg separat tar du bort rollen Mina anpassade appar från dem.
- Om du vill förhindra användare från att installera alla tillägg tar du bort båda rollerna, Mina anpassade appar och Min Marketplace, från dem.

Dessa anvisningar gäller för Office 365, Exchange 2016, Exchange 2013 via Outlook på webben, Windows, Mac och mobilt.

- Lär dig mer om [tillägg för Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Lär dig mer om [hur du anger administratörer och användare som kan installera och hantera tillägg för Outlook-appen](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).
