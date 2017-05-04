---
title: "iOS MAM-principinställningar | Microsoft Docs"
description: "I det här avsnittet beskrivs principinställningarna för hantering av mobilappar för iOS-enheter."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e96413a9f1398e7f025bbc2fbd66153c1c54c504
ms.openlocfilehash: 29fe0acf6c3724455d56b4657c79bc93fb258441
ms.lasthandoff: 04/24/2017


---

#  <a name="ios-mobile-app-protection-policy-settings"></a>Principinställningar för iOS-mobilappskydd

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

De principinställningar som beskrivs i det här avsnittet kan [konfigureras](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) för en appskyddsprincip på bladet **Alla inställningar** i Azure Portal.

Det finns två kategorier för principinställningar: inställningar för dataflytt och åtkomst. I det här avsnittet används termen _**principhanterade appar**_ för att hänvisa till appar som har konfigurerats med appskyddsprinciper.

##  <a name="data-relocation-settings"></a>Inställningar för dataflytt

| Inställningar | Använd så här | Standardvärde |
|------|------|------|
| **Förhindra säkerhetskopiering av iTunes och iCloud** | Välj **Ja** för att förhindra att den här appen säkerhetskopierar arbets- eller skoldata till iTunes och iCloud. Välj **Nej** för att tillåta att den här appen säkerhetskopierar arbets- eller skoldata till iTunes och iCloud.| Ja |
| **Tillåt att appen överför information till andra appar** | Ange vilka appar som kan ta emot data från den här appen: <ul><li> **Principhanterade appar**: Tillåt endast överföring till andra principhanterade appar.</li> <li>**Alla appar**: Tillåt överföring till alla appar. </li> <li>**Inga**: Tillåt inte dataöverföring till någon app, inklusive andra principhanterade appar.</li></ul> Om du anger det här alternativet till **Principhanterade appar** eller **Ingen** blockeras dessutom iOS 9-funktionen som gör att Spotlight-sökning kan söka efter data i appar. <br><br> Det finns vissa undantag för appar och tjänster som Intune kan tillåta dataöverföring till. En fullständig lista över appar och tjänster finns i avsnittet [Undantag vid dataöverföring](#Data-transfer-exemptions). | Alla appar |
| **Tillåt att appen hämtar data från andra appar** | Ange vilka appar som kan överföra data till den här appen: <ul><li>**Principhanterade appar**: Tillåt endast överföring från andra principhanterade appar.</li><li>**Alla appar**: Tillåt dataöverföring från alla appar.</li><li>**Ingen**: Tillåt inte dataöverföring från någon app, inklusive andra principhanterade appar.</li></ul> Det finns vissa undantag för appar och tjänster som Intune kan tillåta dataöverföring från. En fullständig lista över appar och tjänster finns i avsnittet [Undantag vid dataöverföring](#Data-transfer-exemptions).  | Alla appar |
| **Förhindra "Spara som"** | Välj **Ja** om du vill inaktivera alternativet Spara som i den här appen. Välj **Nej** om du vill tillåta att Spara som används. | Nej |
| **Begränsa klipp ut, kopiera och klistra in med andra appar** | Ange när åtgärderna klippa ut, kopiera och klistra in kan användas med den här appen. Välj mellan: <ul><li>**Blockerad**: Tillåt inte åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra appar.</li><li>**Principhanterade appar**: Tillåt endast åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra principhanterade appar.</li><li>**Principhanterade appar med inklistring**: Tillåt klipp ut och kopiera mellan den här appen och andra principhanterade appar. Tillåt att data från en annan app klistras in i den här appen.</li><li>**Alla appar**: Inga begränsningar för klipp ut, kopiera och klistra in till och från den här appen. | Alla appar |
|**Begränsa webbinnehåll till visning i Managed Browser** | Välj **Ja** för att tvinga webblänkar i appen att öppnas i appen Managed Browser. <br><br> För enheter som inte har registrerats i Intune kan webblänkar i principhanterade appar endast öppnas i appen Managed Browser. <br><br> Om du använder Intune för att hantera dina enheter läser du [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](manage-internet-access-using-managed-browser-policies.md). | Nej |
| **Kryptera appdata** | För principer för hanterade program krypteras data i viloläge med hjälp av krypteringsschemat på enhetsnivån som tillhandahålls av iOS. När en PIN-kod krävs krypteras data enligt inställningarna i appskyddsprincipen. <br><br> Gå till den officiella Apple-dokumentationen [här](https://support.apple.com/HT202739) för att se vilka iOS-krypteringsmoduler som är FIPS 140-2-certifierade eller väntar på FIPS 140-2-certifiering. <br><br> Ange när arbets- eller skoldata i den här appen ska krypteras. Välj mellan: <ul><li>**När enheten är låst**: Alla appdata som är associerade med den här principen krypteras när enheten är låst.</li><li>**När enheten är låst och det finns öppna filer**: Alla appdata som är associerade med den här principen krypteras när enheten är låst, utom data i filer som är öppna i appen.</li><li>**Efter omstart av enheten**: Alla appdata som är associerade med den här principen krypteras när enheten startas om, tills den första gången enheten låses upp.</li><li>**Använd enhetsinställningar**: Appdata krypteras baserat på standardinställningarna på enheten. När du aktiverar den här inställningen måste användaren konfigurera och använda en PIN-kod för att komma åt sin enhet.  Om det inte finns någon PIN-kod startar inte apparna och användaren uppmanas att ange en PIN-kod. Ett meddelande visas som informerar användaren om att dennes organisation kräver att enheten har en PIN-kod för att det ska gå att komma åt appen. </li></ul> | När enheten är låst |
| **Inaktivera synkronisering av kontakter** | Välj **Ja** att förhindra att appen sparar data i den interna appen Kontakter på enheten. Om du väljer **Nej** kan appen spara data i den interna appen Kontakter på enheten. <br><br>När du utför en selektiv rensning för att ta bort arbets- eller skoldata från appen kommer kontakter som har synkats direkt från appen till den inbyggda appen Kontakter att tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen. | Nej |
| **Inaktivera utskrift** | Välj **Ja** att förhindra att appen skriver ut arbets- eller skoldata. | Nej |
| **Välj med vilka lagringstjänster företagsdata ska sparas** | Användare kan spara de valda tjänsterna (OneDrive för företag, SharePoint och lokal lagring). Alla andra tjänster kommer att blockeras. | OneDrive för företag och SharePoint |

> [!NOTE]
> Ingen av inställningarna för dataflytt styr den Apple-hanterade ”öppna med”-funktionen på iOS-enheter. Se [Hantera dataöverföring mellan iOS-appar med Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md) för hantering av ”öppna med”.

## <a name="data-transfer-exemptions"></a>Undantag vid dataöverföring

Det finns vissa undantag för appar och plattformstjänster som Intune-appskyddsprinciper kan tillåta dataöverföring till och från i vissa scenarion. Den här listan kan ändras och innehåller de tjänster och program som anses vara användbara för säker produktivitet.

| App-/tjänstnamn | Beskrivning |
| ---- | --- |
|tel; telprompt | Intern telefonapp |
| skype | Skype |
| app-inställningar | Enhetsinställningar |
| itms; itmss; itms-apps; itms-appss; itms-services | Appbutik |
| calshow | Intern kalender |




## <a name="access-settings"></a>Åtkomstinställningar

| Inställningar | Använd så här | Standardvärde |
|------|------|------|
| **Kräv PIN-kod för åtkomst** | Välj **Ja** för att kräva en PIN-kod för att använda den här appen. Användarna uppmanas att konfigurera denna PIN-kod första gången de kör appen i en arbets- eller skolkontext. Standardvärde = **Ja**.<br><br> Konfigurera följande inställningar för PIN-styrka: <ul><li>**Antal försök före återställning av PIN**: Ange antalet försök som användaren har att ange rätt PIN-kod innan den måste återställas. Standardvärde = **5**.</li><li> **Tillåt enkel PIN-kod:** Välj **Ja** du om du vill tillåta att användarna använder enkla PIN-kodssekvenser, till exempel 1234 eller 1111. Välj **Nej** om du vill förhindra att de använder enkla sekvenser. Standardvärde = **Ja**. </li><li> **PIN-kodslängd**: Ange det minsta antalet siffror i en PIN-kodssekvens. Standardvärde = **4**. </li><li> **Kräv fingeravtryck istället för PIN (iOS 8.0+)**: Välj **Ja** om du vill kräva att [Touch-ID](https://support.apple.com/HT201371) används i stället för en PIN-kod för åtkomst till appen. Standardvärde = **Ja**</li></ul> På iOS-enheter kan du låta användaren bekräfta sin identitet med hjälp av [Touch-ID](https://support.apple.com/HT201371) i stället för en PIN-kod. När användarna försöker använda appen med ett arbets- eller skolkonto uppmanas de att lämna sitt fingeravtryck i stället för att ange en PIN-kod. När den här inställningen är aktiverad kommer förhandsgranskningsbilden i appväxlaren att vara suddig när ett arbets- eller skolkonto används. </li></ul>| Kräv PIN-kod: Ja <br><br> PIN-återställningsförsök: 5 <br><br> Tillåt enkel PIN-kod: Ja <br><br> PIN-kodslängd: 4 <br><br> Tillåt fingeravtryck: Ja |
| **Kräv företagets autentiseringsuppgifter för åtkomst** | Välj **Ja** om du vill kräva att användaren loggar in med sitt arbets- eller skolkonto i stället för att ange en PIN-kod för åtkomst till appen. Om du väljer **Ja** åsidosätts kraven på PIN-kod eller Touch ID.  | Nej |
| **Hindra hanterade appar från att köras på jailbrokade eller rotade enheter** |  Välj **Ja** om du vill förhindra att den här appen körs på jailbrokade eller rotade enheter. Användaren kan fortfarande använda apparna för personliga uppgifter, men måste använda en annan enhet för att komma åt arbets- eller skoldata i denna app. | Ja |
| **Kontrollera åtkomstbehörigheterna på nytt efter (minuter)** | Konfigurera följande inställningar: <ul><li>**Tidsgräns**: Det här är antalet minuter innan åtkomstkraven (definieras tidigare i principen) kontrolleras. En administratör kan till exempel aktivera PIN-kod i principen, så om en användare öppnar en MAM-app måste denne ange en PIN-kod. När du använder den här inställningen behöver användaren inte ange en PIN-kod i någon MAM-app under ytterligare **30 minuter** (standardvärde).</li><li>**Offlinerespittid**: Det här är antalet minuter som MAM-appar kan köras offline, specificera tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen. Standardvärde = **720** minuter (12 timmar). När denna tid har gått ut kräver appen användarautentisering till AAD, så att appen kan fortsätta att köras.</li></ul>| Tidsgräns: 30 <br><br> Offline: 720 |
| **Offlineintervall innan appdata rensas (dagar)** | Efter så här många dagar (anges av administratören) med användning offline genomför appen själv en selektiv rensning. Den här selektiva rensningen är samma rensning som kan startas av administratören i MAM-arbetsflödet för rensning. <br><br> | 90 dagar |
| **Inaktivera appens PIN-kod när enheten PIN-kod hanteras** | Välj **Ja** om du vill inaktivera appens PIN-kod när ett enhetslås har identifierats på en registrerad enhet. | Nej |

##  <a name="add-ins-for-outlook-app"></a>Tillägg för Outlook-appen

Outlook införde nyligen iOS-tillägg i Outlook, så att du kan integrera populära appar med e-postklienten. Tillägg för Outlook är tillgängliga för Outlook på webben, Windows, Mac och Outlook för iOS. Eftersom tillägg hanteras via Microsoft Exchange kan användarna dela data och meddelanden via Outlook och ohanterade tilläggsprogram, såvida inte tilläggen har inaktiverats för användarna av Exchange.

Om du vill förhindra slutanvändarna från att få åtkomst till och kunna installera Outlook-tillägg (vilket påverkar alla Outlook-klienter) gör du följande rolländringar i Exchange-administrationscentret:

- Om du vill förhindra användare från att installera Office Store-tillägg tar du bort rollen Min Marketplace från dem.
- Om du vill förhindra användare från att läsa in tillägg separat tar du bort rollen Mina anpassade appar från dem.
- Om du vill förhindra användare från att installera alla tillägg tar du bort båda rollerna, Mina anpassade appar och Min Marketplace, från dem.

Dessa anvisningar gäller för Office 365, Exchange 2016, Exchange 2013 via Outlook på webben, Windows, Mac och mobilt.

- Lär dig mer om [tillägg för Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Lär dig mer om [hur du anger administratörer och användare som kan installera och hantera tillägg för Outlook-appen](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).

