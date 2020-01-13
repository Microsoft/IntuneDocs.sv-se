---
title: Översikt över principer för appskydd
titleSuffix: Microsoft Intune
description: Läs mer om hur Microsoft Intune appskyddsprinciper hjälper till att skydda företagets data och förhindra dataförluster.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: f11ccb51e08e96595dfcb9118c1f479f1b0fc3de
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692130"
---
# <a name="app-protection-policies-overview"></a>Översikt över principer för appskydd

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Appskyddsprinciper (APP) är regler som säkerställer att organisationens data förblir säkra eller inkluderas i en hanterad app. En princip kan vara en regel som tillämpas när användaren försöker få åtkomst till eller flytta "företagsdata", eller en uppsättning åtgärder som är förbjudna eller övervakas när användaren är inne i appen. En hanterad app är en app som har tillämpade appskyddsprinciper och kan hanteras av Intune.

Med skyddsprinciper för hantering av mobila program (MAM) kan du hantera och skydda din organisations data i ett program. Med **MAM utan registrering** (MAM-WE), kan en arbets- eller skolrelaterad app som innehåller känsliga data hanteras på nästan alla [enheter](app-management.md#app-management-capabilities-by-platform), inklusive personliga enheter i **BYOD-scenarier** (Bring Your Own Device). Många produktivitetsappar, till exempel Microsoft Office-apparna, kan hanteras av Intune MAM. Se listan över officiella [MicrosoftIntune-skyddade appar](apps-supported-intune-apps.md) tillgängliga för allmänt bruk.

## <a name="how-you-can-protect-app-data"></a>Hur du kan skydda appdata
Dina anställda använder mobila enheter för både personliga och arbetsrelaterade uppgifter. Samtidigt som du vill se till att de anställda kan vara produktiva vill du förhindra dataförlust, både avsiktlig och oavsiktlig. Du vill även skydda företagsdata som nås från enheter som inte hanteras av dig.

Du kan använda Intunes appskyddsprinciper **oberoende av någon lösning för hantering av mobila enheter (MDM)** . Detta oberoende hjälper dig att skydda företagets data med eller utan registrering av enheter i en enhetshanteringslösning. Genom att implementera **principer på appnivå** kan du begränsa åtkomsten till företagsresurser och hålla data inom IT-avdelningens kontroll.

### <a name="app-protection-policies-on-devices"></a>Skyddsprinciper för appar på enheter

Appskyddsprinciper kan konfigureras för appar som körs på enheter som är:

- **Har registrerats i Microsoft Intune:** Dessa enheter är vanligtvis företagsägda.

- **Registrerade i en hanteringslösning för mobila enheter (MDM) från tredje part:** Dessa enheter är vanligtvis företagsägda.

  > [!NOTE]
  > Principer för mobilapphantering ska inte användas med tredje parts mobilapphantering eller säkra containerlösningar.

- **Har inte registrerats i någon lösning för hantering av mobila enheter:** Enheterna är vanligtvis personalägda enheter som inte hanteras eller som inte är registrerade i Intune eller andra MDM-lösningar.

> [!IMPORTANT]
> Du kan skapa hanteringsprinciper för mobila appar för Office-mobilappar som ansluter till Office 365-tjänster. Du kan även skydda åtkomsten till lokala Exchange-postlådor genom att skapa Intune-appskyddsprinciper för Outlook för iOS och Android där modern hybridautentisering är aktiverad. Innan du använder den här funktionen måste du se till att du uppfyller [kraven för Outlook för iOS och Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Appskyddsprinciper stöds inte för andra appar som ansluter till lokala Exchange- eller SharePoint-tjänster.

## <a name="benefits-of-using-app-protection-policies"></a>Fördelar med att använda appskyddsprinciper

De främsta fördelarna med att använda appskyddsprinciper är:

- **Skydda företagets data på appnivå.** Eftersom mobilappshantering inte kräver enhetshantering kan du skydda företagets data på både hanterade och ohanterade enheter. Eftersom hanteringen är uppbyggd kring användaridentiteten krävs ingen enhetshantering.

- **Slutanvändarens produktivitet påverkas inte och principerna tillämpas inte när appen används i en privat kontext.** Principerna tillämpas endast i arbetssammanhang, vilket ger dig möjlighet att skydda företagets data utan att röra personliga data.

- **Appskyddsprinciper säkerställer att det finns skydd på appnivå.** Du kan till exempel:
  - Kräv en PIN-kod för att öppna en app i arbetssammanhang 
  - Kontrollera delning av data mellan appar 
  - Förhindrar att företagsdata från appar sparas till en personlig lagringsplats

- **MDM, utöver MAM, ser till att enheten är skyddad**. Du kan till exempel behöva en PIN-kod för att få åtkomst till enheten, eller så kan du distribuera hanterade appar till enheten. Du kan också distribuera appar till enheter via MDM-lösningen, vilket ger dig större kontroll över apphanteringen.

Det finns ytterligare fördelar med att använda MDM med appskyddsprinciper. Företag kan använda appskyddsprinciper med och utan MDM på samma gång. Anta exempelvis att en anställd använder både en telefon som utfärdats av företaget och sina egna personliga surfplatta. Företagets telefon registreras i MDM och skyddas av appskyddsprinciper, medan den personliga enheten endast skyddas av appskyddsprinciper.

Om du tillämpar en MAM-princip för användaren utan att ange enhetens tillstånd kommer användaren att få MAM-principen på både BYOD-enheten och den Intune-hanterade enheten. Du kan också tillämpa en MAM-princip som baseras på det hanterade tillståndet. Så när du skapar en appskyddsprincip väljer du **Nej** bredvid **Rikta till alla typer av appar**. Gör sedan något av följande:
- Tillämpa en mindre strikt MAM-princip på Intune-hanterade enheter och tillämpa en mer begränsande MAM-princip på enheter som inte är MDM-registrerade.
- Tillämpa bara en MAM-princip på oregistrerade enheter.

## <a name="supported-platforms-for-app-protection-policies"></a>Plattformar som stöds för appskyddsprinciper

Intune erbjuder en mängd funktioner som hjälper dig att få de appar som du behöver, på de enheter som du önskar köra dem på. Mer information finns i [Apphanteringsfunktioner efter plattform](app-management.md#app-management-capabilities-by-platform).

Plattformsstödet för Intune-appskyddsprinciper är synkroniserat med plattformsstödet för Office-mobilprogram för Android- och iOS-enheter. Mer information finns i avsnittet **Mobilappar** i [Systemkrav för Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> Intunes företagsportal krävs på enheten för att kunna ta emot appskyddsprinciper på Android. Mer information finns i [Krav för åtkomst till appar i Intune-företagsportalen](../fundamentals/end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Hur appskyddsprinciper skyddar appdata

### <a name="apps-without-app-protection-policies"></a>Appar utan appskyddsprinciper

När appar används utan begränsningar kan företagsrelaterade och personliga data blandas. Företagsdata kan hamna på platser som personlig lagring eller överföras till appar som du inte har kontroll över, vilket leder till dataförlust. Pilarna i följande diagram visar hur data flyttas utan begränsningar mellan både företagsdata och personliga dataappar och till lagringsplatser.

![Konceptbild av dataförflyttning mellan appar utan befintliga principer](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>Dataskydd med appskyddsprinciper (APP)

Du kan använda appskyddsprinciper för att förhindra att företagets data sparas till enhetens lokala lagring (se nedanstående bild). Du kan även begränsa dataflytten till andra appar som inte skyddas av appskyddsprinciper. Principinställningar för appskydd inkluderar:
- Dataflyttningsprinciper såsom **Spara kopior av organisationsdata** och **Begränsa klipp ut, kopiera och klistra in**.
- Åtkomstprincipsinställningar som **Kräv enkel PIN för åtkomst** och **Blockera hanterade appar från att köras på jailbrokade eller rotade enheter**.

![Konceptbild som visar företagsdata som skyddas av principer](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>Dataskydd med APP på enheter som hanteras av en MDM-lösning

Nedanstående bild visar de skyddslager som MDM och appskyddsprinciper erbjuder tillsammans.

![Bild som visar hur appskyddsprinciper fungerar på BYOD-enheter](./media/app-protection-policy/app-protection-policies-with-mdm.png)

MDM-lösningen ger mervärde tack vare följande:

- Registrerar enheten
- Distribuerar appar till enheten
- Tillhandahåller fortlöpande enhetskompatibilitet och hantering

Appskyddsprinciper ger mervärde tack vare följande:

- Bidrar till att skydda företagsdata från att läckas till konsumentappar och tjänster
- Använda begränsningar som *Spara som*, *Urklipp* eller *PIN-kod* för klientappar
- Rensa företagsdata vid behov från appar utan att ta bort dessa appar från enheten

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>Dataskydd med APP för enheter utan registrering

Det följande diagrammet visar hur dataskyddsprinciper fungerar på appnivå utan MDM.

![Bild som visar hur appskyddsprinciper fungerar på enheter utan registrering (ej hanterade enheter)](./media/app-protection-policy/app-protection-policies-without-mdm.png)

För BYOD-enheter som inte har registrerats i någon MDM-lösning kan appskyddsprinciper skydda företagets data på appnivå.
Det finns dock vissa begränsningar som du bör känna till, t.ex.:

- Du kan inte distribuera appar till enheten. Slutanvändaren måste hämta apparna från butiken.
- Du kan inte etablera certifikatprofiler på enheterna.
- Du kan inte etablera företagets Wi-Fi- och VPN-inställningar på enheterna.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Appar som du kan hantera med appskyddsprinciper

Alla appar som har integrerats med [Intune App-SDK](../developer/app-sdk.md) eller inslutits av [Intunes programhanteringsverktyg](../developer/apps-prepare-mobile-application-management.md) kan hanteras med Intunes appskyddsprinciper. Se den officiella listan med [Microsoft Intune-skyddade appar](apps-supported-intune-apps.md) som har skapats med hjälp av dessa verktyg och är tillgängliga för offentligt bruk.

Intune SDK-utvecklingsteamet testar och underhåller aktivt stödet för appar som skapats med de ursprungliga Android-, iOS (Obj-C, Swift), Xamarin-, Xamarin.Forms- och Cordova-plattformarna. Även om vissa kunder har lyckats integrera Intune SDK med andra plattformar som React Native och NativeScript, tillhandahåller vi inte någon uttrycklig vägledning eller några plugin-program för apputvecklare som använder något annat än våra stödda plattformar.

[Intune APP SDK](../developer/app-sdk.md) använder vissa avancerade moderna autentiseringar från [Azure Active Directory-autentiseringsbibliotek](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) för SDK-versioner från såväl första som tredje part. Därför fungerar [Microsofts-autentiseringsbibliotek](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (MSAL) inte bra ihop med många av våra grundläggande scenarier, till exempel autentisering till tjänsten Intune-appskydd och villkorlig start. Eftersom den allmänna instruktionen från Microsoft Identity-teamet är att gå över till MSAL för alla Microsoft Office-appar kommer [Intune App SDK](../developer/app-sdk.md) så småningom att behöva stödja detta, men det finns inga planer på det idag.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>Slutanvändarkrav för att använda skyddsprinciper för appar

Följande lista innehåller kraven för att använda appskyddsprinciper på en Intune-hanterad app:

- Slutanvändare måste ha ett Azure Active Directory-konto (AAD). Se [Lägg till användare och ge administrativ behörighet till Intune](../fundamentals/users-add.md) för information om hur du skapar Intune-användare i Azure Active Directory.

- Slutanvändaren måste ha en licens för Microsoft Intune som tilldelats deras Azure Active Directory-konto. Se [Hantera Intune-licenser](../fundamentals/licenses-assign.md) för information om hur du tilldelar Intune-licenser till slutanvändare.

- Slutanvändaren måste tillhöra en säkerhetsgrupp som är målet för en appskyddsprincip. Samma appskyddsprincip måste ha den specifika app som används som mål. Appskyddsprinciper kan skapas och distribueras i Intune-konsolen i [Azure-portalen](https://portal.azure.com). Säkerhetsgrupper kan för närvarande skapas i [Microsoft 365-administrationscentret](https://admin.microsoft.com).

- Slutanvändaren måste logga in på appen med sitt AAD-konto.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Appskyddsprinciper för Microsoft Office-appar

Det finns några ytterligare krav som du bör vara medveten om när du använder appskyddsprinciper med Microsoft Office-appar.

### <a name="outlook-mobile-app"></a>Outlook-mobilapp
Ytterligare krav som ställs för användning av [Outlook-mobilappen](https://products.office.com/outlook) omfattar följande:

- Slutanvändaren måste ha Outlook-mobilappen installerad på sin enhet.
- Slutanvändaren måste ha en [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online)-postlåda och licens kopplad till sitt Azure Active Directory-konto.

  >[!NOTE]
  > Outlooks mobilapp har för närvarande endast stöd för Intune-appskydd för Microsoft Exchange Online och [Exchange Server med modern hybridautentisering](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) och saknar stöd för Exchange i Office 365 Dedicated.

### <a name="word-excel-and-powerpoint"></a>Word, Excel och PowerPoint
De ytterligare kraven för att använda [Word-, Excel- och PowerPoint](https://products.office.com/business/office)-apparna omfattar följande:

- Slutanvändaren måste ha en licens för [Office 365 Business eller Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) som länkats till deras Azure Active Directory-konto. Prenumerationen måste inkludera Office-apparna på mobila enheter och kan inkludera ett molnlagringskonto med [OneDrive för företag](https://onedrive.live.com/about/business/). Office 365-licenser kan tilldelas i [Microsoft 365-administrationscentret](https://admin.microsoft.com) med hjälp av följande [instruktioner](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- Slutanvändaren måste ha en hanterad plats som konfigurerats med detaljerade spara som-funktioner under inställningen för programskyddsprincipen ”Spara kopior av organisationsdata”. Om den hanterade platsen till exempel är OneDrive, ska [OneDrive](https://onedrive.live.com/about/)-appen vara konfigurerad i slutanvändarens Word-, Excel- eller PowerPoint-app.

- Om den hanterade platsen är OneDrive, måste appen vara mål för appskyddsprincipen som distribuerats till slutanvändaren.

  >[!NOTE]
  > Office mobilappar har för närvarande endast stöd för SharePoint Online och inte SharePoint på plats.

### <a name="managed-location-needed-for-office"></a>Hanterad plats krävs för Office
En hanterad plats krävs för Office (t.ex. OneDrive). Intune markerar all data i appen som ”företag” eller ”personligt”. Data anses som "företagets" när det kommer från en företagsplats. För Office-apparna betraktar Intune följande platser som företagets: e-post (Exchange) eller molnlagring (OneDrive-app med ett konto för OneDrive för företag).

### <a name="skype-for-business"></a>Skype för företag
Det finns ytterligare krav som ställs för användning av Skype för företag. Se licenskraven för [Skype för företag](https://products.office.com/skype-for-business/it-pros). Skype för företag (SfB) hybrid och lokala konfigurationer, se [Hybrid Modern autentisering för SfB och Exchange blir allmänt tillgängliga](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) och [Modern autentisering för SfB OnPrem med AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910), respektive.

## <a name="app-protection-global-policy"></a>Global princip för appskydd

Om en OneDrive-administratör går till **admin.office.com** och väljer **Enhetsåtkomst** kan de ange kontroller för **hantering av mobilprogram** för OneDrive- och SharePoint-klientappar. 

Inställningarna, som nås via OneDrive Admin-konsolen, konfigurerar en särskild Intune-appskyddsprincip som kallas **den Globala** principen. Den globala principen gäller för alla användare i din klient och kan inte styra riktad principtillämpning. 

När den har aktiverats skyddas OneDrive- och SharePoint-appar för iOS och Android med de valda inställningarna som standard. IT-personal kan ändra den här principen i Intune-konsolen för att lägga till fler riktade appar och ändra alla principinställningar. 

Som standard kan det endast finnas en **Global** princip per klient. Du kan dock använda [Intune Graph API:er](../developer/intune-graph-apis.md) för att skapa extra globala principer per klient men detta rekommenderas inte. Vi rekommendera att du inte skapar extra globala principer då detta kan komplicera en eventuell felsökning av implementeringen av principen.

Medan den **Globala** principen gäller för alla användare i din klient kommer standardprinciper för appskydd med Intune att åsidosätta dessa inställningar.

## <a name="app-protection-features"></a>Appskyddsfunktioner

### <a name="multi-identity"></a>Flera identiteter

Med stöd för flera identiteter kan en app stödja flera målgrupper. Dessa målgrupper är både ”företagsanvändare” och ”personliga” användare. Arbets- och skolkonton används av företagsgrupper medan personliga konton används för konsumentanvändare, t. ex. Microsoft Office-användare. En app som har stöd för flera identiteter kan publiceras offentligt, där appskyddsprinciperna endast tillämpas när appen används i arbets- och skolkontexten (”företag”). Stöd för flera identiteter är möjligheten för [Intune App SDK](../developer/app-sdk.md) att bara tillämpa appskyddsprinciper på arbets- eller skolkontot som använts för inloggning i appen. Om ett personligt konto är inloggat i appen ändras inga data.

För ett exempel på ”privat” kontext, anta att en användare som startar ett nytt dokument i Word, då anses detta vara privat kontext så Intune-appskyddsprinciper tillämpas inte. När dokumentet sparas på ”företagets” OneDrive-konto kommer det anses vara ”företagskontext” och Intune-appskyddsprinciperna tillämpas.

Anta som ett exempel på ett arbets- eller ”företagskontext” att en användare startar appen OneDrive med sitt arbetskonto. De kan inte flytta filerna till en personlig lagringsplats i ett arbetskontext. Om användaren senare använder OneDrive med ett personligt konto kan hen kopiera och flytta data från sin personliga OneDrive utan begränsningar.

Outlook har en kombinerad e-postvy med såväl ”personlig” som ”företags-e-post”. I det här fallet begär Outlook-appen Intune-PIN-koden vid start.

Mer information om flera identiteter i Intune finns i [MAM och flera identiteter](apps-supported-intune-apps.md).

### <a name="intune-app-pin"></a>Intune-appens PIN-kod

PIN-kod (Personal Identification Number) är ett lösenord som används för att verifiera att rätt användare har åtkomst till organisationens data i en app.

**PIN-fråga**<br>
Intune frågar endast efter användarens PIN-kod för appen när användaren ska få åtkomst till företagsdata. I appar för flera identiteter som till exempel Word, Excel eller PowerPoint uppmanas användarna att ange sina PIN-koder när de försöker öppna ett "företags"-dokument eller -fil. I appar för en identitet, till exempel branschspecifika appar som använder [Intunes apphanteringsverktyg](../developer/apps-prepare-mobile-application-management.md), efterfrågas PIN-koden redan vid start eftersom [Intune App SDK:n](../developer/app-sdk.md) vet att användarupplevelsen i appen alltid är företag.

**Fråga om PIN-kod eller behörighet för företaget, frekvens**<br>
IT-administratören kan definiera Intune-appskyddsprincipen **Kontrollera åtkomskraven igen efter (minuter)** i Intune-administratörskonsolen. Inställningen anger hur lång tid som ska passera innan åtkomstkraven kontrolleras på enheten och programmets PIN-skärm eller företagets behörighetsfråga visas igen. Detta är dock viktig information om PIN-koden som påverkar hur ofta användaren uppmanas:

- **PIN-koden delas mellan appar från samma utgivare för att förbättra användarvänligheten:**<br> I iOS delas en apps PIN-kod mellan alla appar **från samma apputgivare**. Alla Microsoft-appar har till exempel samma PIN-kod. På Android delas en app-PIN mellan alla appar.
- **Beteendet *Kontrollera åtkomstkraven igen efter (minuter)”* efter en omstart av enheten:**<br> En timer spårar antalet minuter av inaktivitet som avgör när Intune-appens PIN-kod eller företagets fråga om behörighet ska visas nästa gång. I iOS påverkas inte timern av att enheten startas om. Därför påverkar inte enhetsomstarten det antal minuter som användaren har varit inaktiv från en iOS-app med en riktad princip för Intune PIN (eller företagsautentisering). I Android återställs timern när enheten startas om. Därför är det troligt att Android-appar med Intune PIN (eller företagsautentisering) frågar efter appens PIN-kod eller företagets behörighet, oavsett värdet i inställningen ”Kontrollera åtkomstkraven igen efter (minuter)” **efter en omstart av enheten**.  
- **Den löpande funktionen för timern som är kopplad till PIN-koden:**<br> När en PIN-kod anges för att få åtkomst till en app (app A) och appen lämnar enhetens förgrund (huvudfokus) kommer timern att återställas för den PIN-koden. De appar (t.ex. app B) som delar denna PIN-kod kommer inte uppmana användaren att ange PIN-kod eftersom timern har återställts. Uppmaningen visas igen när värdet ”Kontrollera åtkomstkraven igen efter (minuter)” uppfylls igen.

För iOS-enheter visas meddelandet igen när värdet **Kontrollera åtkomstbehörigheterna på nytt efter (minuter)** uppfylls igen för den app som inte är huvudfokus, även om PIN-koden delas mellan appar från olika utgivare. En användare har till exempel appen _A_ från utgivare _X_ och appen _B_ från utgivare _Y_, och dessa två appar delar samma PIN-kod. Användaren fokuserar på app _A_ (förgrund) och app _B_ minimeras. När värdet **Kontrollera åtkomstbehörigheterna på nytt efter (minuter)** uppfylls och användaren växlar till app _B_ krävs PIN-koden.

  >[!NOTE]
  > För att verifiera användarens åtkomstkrav oftare (till exempel med en PIN-fråga), särskilt för appar som används ofta, rekommenderar vi att du minskar värdet för inställningen Kontrollera åtkomstkraven igen efter (minuter).

**Inbyggda app-PIN-koder för Outlook och OneDrive**<br>
Intune PIN-koden fungerar enligt en inaktivitetsbaserad timer (värdet för **Kontrollera åtkomstkraven igen efter (minuter)** ). Därför visas Intune PIN-uppmaningar oberoende av de inbyggda app-PIN-uppmaningarna för Outlook och OneDrive, som ofta är kopplade till appstart som standard. Om användaren får PIN-uppmaningarna samtidigt är det förväntade beteendet att Intune PIN-koden har företräde.

**Säkerhet för Intune-PIN**<br>
PIN-koden fungerar så att endast rätt användare får åtkomst till organisationens data i appen. Därför måste en slutanvändare logga in med sitt arbets- eller skolkonto innan de kan ställa in eller återställa Intune-appens PIN-kod. Den här autentiseringen hanteras av Azure Active Directory via utbyte av säker token och är inte transparent för [Intune App SDK](../developer/app-sdk.md). Ur ett säkerhetsperspektiv är bästa sättet att skydda data från arbete eller skola att kryptera den. Kryptering är inte relaterad till appens PIN-kod, utan en egen appskyddsprincip.

**Intune-PIN – skyddar mot nyckelsökningsattacker**<br>
Som en del av appens PIN-princip kan IT-administratören ange det maximala antalet gånger som en användare kan försöka att autentisera sin PIN-kod innan appen blir låst. När antalet försök har uppfyllts kan [Intune App SDK](../developer/app-sdk.md) rensa företagets data i appen.
  
**Ställer du in en PIN-kod två gånger på appar från samma utgivare?**<br>
MAM (på iOS) tillåter för tillfället PIN på programnivå med alfanumeriska tecken och specialtecken (kallas lösenord) som kräver medverkan av program (d.v.s. WXP, Outlook, hanterad webbläsare, Yammer) för att integrera [Intune APP SDK:n för iOS](../developer/app-sdk-ios.md). Utan detta tillämpas inställningar för lösenord inte korrekt för de aktuella programmen. Detta var en funktion som introducerades i Intune SDK för iOS v. 7.1.12.

För att stödja den här funktionen och säkerställa bakåtkompatibilitet med tidigare versioner av Intune SDK för iOS, hanteras alla PIN-koder (numeriska eller lösenord) i 7.1.12+ separat från den numeriska PIN-koden i tidigare versioner av SDK. Därför måste en enhet som har program med Intune SDK för iOS-versioner före 7.1.12 och efter 7.1.12 från samma utgivare, ställa in två PIN-koder. De två PIN-koderna (för varje app) är inte relaterade på något sätt, d.v.s. de måste följa den appskyddsprincip som tillämpas på appen. Därför kan användare konfigurera samma PIN-kod två gånger *endast* om apparna A och B har samma principer tillämpade (med avseende på PIN-kod). 

Det här beteendet är specifikt för PIN-koden på iOS-program som har aktiverats med Intune Mobile App Management. Med tiden när program inför senare versioner av Intune SDK för iOS, blir det inte ett så stort problem att behöva ange PIN-kod två gånger på appar från samma utgivare. Se avsnittet nedan för ett exempel.

  >[!NOTE]
  > Om t.ex. app A har skapats med en tidigare version än 7.1.12 och app B har byggts med en version som är högre än eller lika med 7.1.12 från samma utgivare, måste slutanvändaren ställa in PIN-koder separat för A och B om båda är installerade på en iOS-enhet.
  > Om en app C har SDK-version 7.1.9 installerad på enheten, delar den samma PIN-kod som app A. App D som har kompilerats med 7.1.14 kommer att dela samma PIN-kod som app B.  
  > Om bara apparna A och C är installerade på en enhet, behöver en PIN-kod anges. Detsamma gäller om bara apparna B och D är installerade på en enhet.

### <a name="app-data-encryption"></a>Appdatakryptering
IT-administratörer kan distribuera en appskyddsprincip som kräver att appdata krypteras. Som en del av principen kan IT-administratören även ange när innehållet krypteras.

**Hur fungerar datakrypteringsprocessen i Intune**<br> Se [Inställningar för Android-appskyddsprinciper](app-protection-policy-settings-android.md) och [Inställningar för iOS-appskyddsprinciper](app-protection-policy-settings-ios.md) för detaljerad information om inställning av appskyddprincip för kryptering.

**Data som är krypterade**<br>
Endast data som har markerats som "företagets" krypteras enligt IT-administratörens appskyddsprincip. Data anses som "företagets" när det kommer från en företagsplats. För Office-apparna beaktar Intune följande som företagsplatser:

- E-post (Exchange) 
- Molnlagring (OneDrive-app med ett OneDrive för företag-konto)

För branschspecifika appar som hanteras av [Intunes programhanteringsverktyg](../developer/apps-prepare-mobile-application-management.md), betraktas alla appdata som företag.

**Fjärrensa data**<br>
Intune kan rensa appdata på tre olika sätt: 
- Fullständig enhetsrensning
- Selektiv rensning för MDM 
- Selektiv rensning med MAM

Mer information om fjärrensning för MDM finns i [Ta bort enheter med rensning eller dra tillbaka](../remote-actions/devices-wipe.md). Om du vill ha mer information om selektiv rensning med hjälp av MAM kan du läsa om [åtgärden Dra tillbaka](../remote-actions/devices-wipe.md#retire) och [Hur du rensar endast företagsdata från appar](apps-selective-wipe.md).

[Rensning](../remote-actions/devices-wipe.md) tar bort all användardata och inställningar från **enheten** genom att återställa den till fabriksinställningarna. Enheten tas bort från Intune.

  >[!NOTE]
  > Rensning kan bara ske på enheter som registrerats med Intunes hantering av mobila enheter (MDM).

**Selektiv rensning för MDM**<br>
Se [Ta bort enheter – dra tillbaka](../remote-actions/devices-wipe.md#retire) för att läsa om hur du tar bort företagsdata.

**Selektiv rensning för MAM**<br>
Selektiv rensning för MAM tar helt enkelt bort företagsdata från en app. Begäran initieras med hjälp av Intune Azure-portalen. Information om hur du initierar en rensningsbegäran finns i [Så här rensar du endast företagsdata från appar](apps-selective-wipe.md).

Om användaren använder appen när selektiv rensning initieras söker [Intune App SDK](../developer/app-sdk.md) var 30:e minut efter en begäran om selektiv rensning från Intune MAM-tjänsten. Den söker även efter selektiv rensning när användaren startar appen för första gången och loggar in med sitt arbets- eller skolkonto.

**När tjänster på plats inte fungerar med Intunes appskydd**<br>
Intunes appskydd är beroende av att användarens identiteten är konsekvent mellan appen och [Intune App SDK](../developer/app-sdk.md). Det enda sättet att garantera detta är via modern autentisering. Det finns scenarier där appar kan fungera med en lokal konfiguration, men de är varken konsekventa eller garanterade.

**Ett säkert sätt att öppna webblänkar från hanterade appar**<br>
IT-administratören kan distribuera och ange appskyddsprincip för [Intune Managed Browser-appen](app-configuration-managed-browser.md), en webbläsare som har utvecklats av Microsoft Intune som enkelt kan hanteras med Intune. IT-administratören kan kräva att alla webblänkar i Intune-hanterade appar ska öppnas med Managed Browser-appen.

## <a name="examples-of-app-protection-policies"></a>Exempel på appskyddsprinciper

Se [Inställningar för Android-appskyddsprinciper](app-protection-policy-settings-android.md) och [Inställningar för iOS-appskyddsprinciper](app-protection-policy-settings-ios.md) för att läsa mer om respektive inställning av appskyddprincip och exempel på appskyddsprinciper.

## <a name="app-protection-experience-for-ios-devices"></a>Appskyddsupplevelse för iOS-enheter

### <a name="device-fingerprint-or-face-ids"></a>Fingeravtryck för enhet eller ansikts-ID 
Intunes appskyddsprinciper kan styra åtkomst till den Intune-licensierade användaren. Ett sätt att styra åtkomst till appen är att kräva antingen Apples Touch-ID eller ansikts-ID på enheter som stöds. Intune implementerar ett beteende där, om det förekommer ändringar till enhetens biometriska databas, Intune uppmanar användaren att ange en PIN-kod när nästa tidsgränsen för inaktivitet uppfylls. Ändringar av biometriska data inkluderar tillägg eller borttagning av ett fingeravtryck eller ansikte. Om Intune-användare inte har en PIN-kod, leds de till att ställa in en PIN-kod i Intune.
 
Syftet med detta är att fortsätta att hålla din organisations data i appen säkra och skyddade på appnivå. Den här funktionen är endast tillgänglig för iOS och kräver medverkan av program som integrerar Intune APP SDK för iOS, version 9.0.1 eller senare. Integrering av SDK krävs så att beteendet kan tillämpas på de berörda programmen. Den här integreringen händer på löpande bas, och är beroende av specifika programteam. Vissa appar som deltar omfattar WXP, Outlook, Managed Browser och Yammer.
  
### <a name="ios-share-extension"></a>Tillägg för iOS-resurs
Du kan använda iOS resurstillägg för att öppna arbets- eller skoldata i ohanterade appar, även om dataöverföringsprincipen är inställd på **Endast hanterade appar** eller **Inga appar**. Intunes appskyddsprincip kan inte styra iOS resurstillägg utan att hantera enheten. Därför krypterar Intune _**"företagets" data innan den delas utanför appen**_ . Du kan verifiera detta krypteringsbeteende genom att försöka öppna en "företags"-fil utanför den hanterade appen. Filen ska vara krypterad och inte kunna öppnas utanför den hanterade appen.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Flera åtkomstinställningar för Intune App Protection för samma uppsättning appar och användare
Appskyddsprinciper i Intune för åtkomst tillämpas i en viss ordning på slutanvändarenheter när de försöker få åtkomst till en riktad app från ett företagskonto. Vanligtvis får rensningar företräde, följt av blockeringar och därefter varningar som kan avfärdas. Exempel: Om det är tillämpligt för den specifika användaren/appen används en lägsta iOS-operativsysteminställning som varnar en användare för att göra en uppdatering av sin iOS-version efter den lägsta iOS-operativsysteminställningen som blockerar användarens åtkomst. I scenariot där en IT-administratör konfigurerar det äldsta iOS-operativsystemet till 11.0.0.0 och det äldsta iOS-operativsystemet (endast varning) till 11.1.0.0, medan enheten som försöker få åtkomst till appen hade iOS-version 10 blockeras slutanvändaren baserat på den mer restriktiva inställningen för den lägsta iOS-operativsystemversionen. Det leder till blockerad åtkomst.

När du hanterar olika typer av inställningar får ett krav på Intune App SDK-version företräde, följt av kravet på appversion, och därefter kravet på iOS-operativsystemets version. Sedan kontrolleras alla varningar för alla typer av inställningar i samma ordning. Vi rekommenderar att du endast konfigurerar Intune App SDK-versionskraven vid vägledning från Intune-produktteamet för väsentliga blockeringsscenarier.

## <a name="app-protection-experience-for-android-devices"></a>Appskyddsupplevelse för Android-enheter

### <a name="company-portal-app-and-intune-app-protection"></a>Företagsportalapp och Intune-appskydd
Många av appskyddets funktioner är inbyggda i företagsportalappen. Enhetsregistrering _krävs inte_, även om företagsportalappen alltid krävs. För mobilapphantering utan registrering (MAM-WE) behöver slutanvändaren bara ha företagsportalappen installerad på enheten.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Flera åtkomstinställningar för Intune App Protection för samma uppsättning appar och användare
Appskyddsprinciper i Intune för åtkomst tillämpas i en viss ordning på slutanvändarenheter när de försöker få åtkomst till en riktad app från ett företagskonto. Vanligtvis får en blockering företräde, och därefter en varning som kan avfärdas. Exempel: Om det är tillämpligt för den specifika användaren/appen används en lägsta inställning för Android-korrigeringsprogramversionen. Den varnar en användare för att göra en uppdatering efter den lägsta inställningen för Android-korrigeringsprogramversionen som blockerar användarens åtkomst. I scenariot där en IT-administratör konfigurerar den äldsta Android-korrigeringsprogramversionen till 2018-03-01 och den äldsta Android-korrigeringsprogramversionen (endast varning) till 2018-02-01, medan enheten som försöker få åtkomst till appen hade korrigeringsprogramversionen 2018-01-01, blockeras slutanvändaren baserat på den mer restriktiva inställningen för den lägsta Android-korrigeringsprogramversionen. Det leder till blockerad åtkomst. 

När du hanterar olika typer av inställningar får ett krav på appversion företräde, följt av kravet på Android-operativsystemets version och kravet på Android-korrigeringsprogrammets version. Sedan kontrolleras alla varningar för alla typer av inställningar i samma ordning.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Intune App Protection-principer och Googles SafetyNet-attestering för Android-enheter 
Intune-appskyddsprinciper ger administratörer möjligheten att kräva att slutanvändarenheter godkänns av Googles SafetyNet-attestering för Android-enheter. En ny Google Play-tjänstbestämmelse rapporteras till IT-administratören vid ett intervall som bestäms av Intune-tjänsten. Hur ofta tjänstanropet görs begränsas på grund av belastningen, vilket gör att det här värdet underhålls internt och inte kan konfigureras. Alla av IT-administratören konfigurerade åtgärder för inställningen för Googles SafetyNet-attestering vidtas baserat på det senast rapporterade resultatet till Intune-tjänsten vid tidpunkten för villkorsstyrd start. Om det inte finns några data tillåts åtkomst beroende på om inga andra kontroller för villkorsstyrd start misslyckas, och Google Play-tjänstens ”tur och retur” för att avgöra attesteringsresultat börjar i serverdelen och uppmanar användaren asynkront om enheten har misslyckats. Om det finns inaktuella data blockeras eller tillåts åtkomst beroende det senast rapporterade resultatet, och på ett liknande sätt startar Google Play-tjänstens ”tur och retur” för att avgöra attesteringsresultat och uppmanar användaren asynkront om enheten har misslyckats.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Intune App Protection-principer och Googles Verify Apps-API-attestering för Android-enheter
Intune-appskyddsprinciper ger administratörer möjligheten att kräva att slutanvändarenheter skickar signaler via Googles Verify Apps-API för Android-enheter. Anvisningar om hur du gör detta varierar något beroende på enheten. Den allmänna processen omfattar att gå till Google Play Store, klicka på **Mina appar och spel** och därefter klicka på resultatet av den senaste appgenomsökningen, vilket öppnar Play Protect-menyn. Se till att växlingsknappen för **Genomsök enheten efter säkerhetshot** växlas till på.

### <a name="googles-safetynet-attestation-api"></a>Googles SafetyNet attesterings-API 
Intune använder Google Play Protect SafetyNet-API:er som tillägg till våra befintliga rotidentifieringskontroller för oregistrerade enheter. Google har utvecklat och underhållit den här API-uppsättningen för införande i Android-appar om de inte vill att deras appar ska köras på rotade enheter. Det här har införts för till exempel Android Pay-appen. Google delar inte alla rotidentifieringskontroller som körs offentligt, men vi förväntar oss att de här API:erna identifierar användare som har rotat sina enheter. De här användarna kan sedan blockeras från åtkomst, eller så kan deras företagskonton rensas bort från principaktiverade appar. **Kontrollera grundläggande integritet** ger information om enhetens allmänna integritet. Rotade enheter, emulatorer, virtuella enheter och enheter med tecken på manipulation misslyckas med grundläggande integritet. **Kontrollera grundläggande integritet och certifierade enheter** ger information om enhetens kompatibilitet med Google-tjänster. Endast oförändrade enheter som har certifierats av Google kan godkännas av den här kontrollen. Enheter som misslyckas inbegriper följande:

- Enheter som misslyckas med grundläggande integritet
- Enheter med ett upplåst startprogram
- Enheter med en anpassad systemavbildning/ROM
- Enheter för vilka tillverkaren inte ansökte eller godkändes för Google-certifiering
- Enheter med en systemavbildning som skapats direkt från Android Open Source Program-källfilerna
- Enheter med en betaversion/utvecklarförhandsversion av systemavbildningen

Teknisk information finns i [Googles dokumentation om SafetyNet-attestering](https://developer.android.com/training/safetynet/attestation).

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>Inställningen ”SafetyNet-enhetsattestering” och inställningen ”jailbrokade/rotade enheter”
Google Play Protects SafetyNet-API-kontroller kräver att slutanvändaren är online, åtminstone under den tid då ”tur och retur” för att avgöra attesteringsresultat körs. Om användaren är offline kan IT-administratören fortfarande förvänta sig att ett resultat framtvingas från inställningen **jailbrokade/rotade enheter**. Om slutanvändaren har varit offline för länge kan dock värdet för **Offline-respitperioden** börja gälla, och all åtkomst till arbets- eller skoldata blockeras när det timervärdet uppnås tills nätverksåtkomst blir tillgänglig. Om båda inställningarna aktiveras ger det en metod med flera lager för att hålla slutanvändarenheter felfria, vilket är viktigt när slutanvändare kommer åt arbets- eller skoldata via mobilenheter.

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play Protect-API:er och Google Play-tjänster
De inställningar för appskyddsprincip som använder Google Play Protect-API:er kräver Google Play-tjänster för att kunna fungera. Båda inställningarna **SafetyNet-enhetsattestering** och **Hotgenomsökning på appar** kräver en Google-bestämd version av Google Play-tjänster för att fungera korrekt. Eftersom de här är inställningar som rör området säkerhet blockeras slutanvändaren om denne är föremål för de här inställningarna och inte uppfyller den lämpliga versionen av Google Play-tjänster eller inte har åtkomst till Google Play-tjänster.

## <a name="next-steps"></a>Nästa steg

[Skapa och distribuera appskyddsprinciper med Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Se även
Appar från tredje part, till exempel Salesforce-mobilappen fungerar med Intune på specifika sätt för att skydda företagsdata. Läs mer om hur Salesforce-appen i synnerhet fungerar med Intune (inklusive MDM-appkonfigurationsinställningar) i [Salesforce-appen och Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
