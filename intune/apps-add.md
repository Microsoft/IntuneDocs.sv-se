---
title: "Så här lägger du till appar i Microsoft Intune"
titlesuffix: Azure portal
description: "De här procedurerna hjälper dig att få in dina appar i Intune så att de är redo att tilldelas till användare och enheter. \""
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4c753ebfc48365d0d586773585552026ad17b6f6
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>Så här lägger du till appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Innan du kan tilldela, övervaka, konfigurera eller skydda appar måste du lägga till dem till Intune. Intune stöder en mängd olika apptyper. De tillgängliga alternativen skiljer sig åt för varje apptyp.

I Intune kan du lägga till och tilldela följande apptyper:
| Typ av app                                  | Installation                                                                  | Uppdateringar                       |
|------------------------------------------ |----------------------------------------------------------------------------   |---------------------------    |
| Appar på webben                           | Intune skapar en genväg till webbappen på enhetens startskärm          | Uppdateringar av appar sker automatiskt     |
| Appar om skrivits internt (verksamhetsspecifika)  | Intune installerar appen på enheten (du tillhandahåller installationsfilen)    | Du måste uppdatera appen       |
| Appar från butiken                       | Intune installerar apparna på enheten                                       | Uppdateringar av appar sker automatiskt     |
| Appar som är inbyggda                        | Intune installerar apparna på enheten                                       | Uppdateringar av appar sker automatiskt     |


Intune stöder följande specifika plattformar för Store-appar och LOB-appar:
- Store-appar
    - Android Store-appar
    - iOS Store-appar
    - Windows Phone 8.1 Store-appar
    - Windows Store-appar
    - Android for Work-appar
    - Office 365-appar för Windows
    - Office 365-appar för macOS
- Skapa din app – Line-of-business (LOB)
    - Verksamhetsspecifika appar för Android
    - Verksamhetsspecifika appar för iOS
    - Verksamhetsspecifika appar (LOB) för Windows Phone (.xap-filer)
    - Verksamhetsspecifika appar (LOB) för Windows (endast .xap-filer)
- Inbyggda appar    

>[!TIP]
> En verksamhetsspecifik app (LOB) är en app som du lägger till från en appinstallationsfil. För att exempelvis installera en iOS LOB-app lägger du till programmet genom att välja **Branschspecifik app** som **Apptyp** från bladet **Lägg till app**. Välj sedan appaketfilen (tillägget .ipa). Dessa typer av appar är vanligen skrivna internt.

## <a name="assess-application-requirements"></a>Utvärdera programvarukrav 
Som IT-administratör ska du inte bara bestämma vilka appar gruppen måste använda, utan du ska även bestämma vilka funktioner som behövs för varje grupp och undergrupp. För varje app måste du besluta vilka plattformar som behövs, vilka användargrupper som behöver appen, vilka konfigurationsprinciper som ska gälla för grupperna och vilka skyddsprinciper som ska gälla.  

Du måste dessutom bestämma om du behöver fokusera på focus Mobile Device Management (MDM) eller enbart Mobile Application Management (MAM). Det är praktiskt att använda Intune för att hantera enheten (Mobile Device Management) när:
- Användare behöver en WiFi- eller VPN-företagsanslutningsprofil för att vara produktiva.
- Användare behöver en uppsättning appar som ska push-överföras till deras enhet.
- Din organisation behöver uppfylla regler eller andra principer som ska beskriva MDM-kontroller (Mobile Device Management), som säkerhet eller kryptering.

Det är praktiskt att använda Intune för att hantera appar (hantering av mobilprogram) utan att hantera enheten när:
- Du vill att användare ska kunna använda sin egen enhet (BYOD).
- Du vill tillhandahålla enstaka popup-meddelanden för att informera användarna om att det finns MAM-skydd istället för kontinuerliga meddelanden på enhetsnivå.
- Du måste följa policyer som kräver mindre hanteringsfunktioner på personliga enheter. Du kanske till exempel vill hantera apparnas företagsdata istället för att hantera företagsdata för hela enheten.

Mer information finns i [Jämför MDM och MAM](byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Bestämma vem som ska använda appen
När du har lagt till en app i Intune tilldelar du en grupp användare som kan använda appen. Du måste först bestämma en lämplig grupp som ska ha åtkomst till appen baserat på hur känsliga data appen innehåller. Du måste inkludera eller exkludera vissa typer av roller i organisationen. Till exempel kan endast vissa LOB-appar krävas för säljgruppen, medan personer som arbetar med ingenjörskonst, ekonomi, HR eller juridik kanske inte behöver använda LOB-apparna. Dessutom kanske säljgruppen behöver ytterligare dataskydd och åtkomst till interna företagstjänster på sina mobila enheter. Du måste bestämma hur den här gruppen ska ansluta till resurser med appen. Kommer de data som appen kommer åt finnas i molnet eller lokalt? Och hur kommer användarna att ansluta till resurser med appen? Med Intune kan du också aktivera åtkomst till mobilappar som kräver säker åtkomst till lokala data, t.ex. servrar för affärsappar. Den här typen av åtkomst görs normalt med [Intune-hanterade certifikat](certificates-configure.md) för åtkomstkontroll som kombineras med en VPN-gateway eller proxy av standardtyp i perimeternätverket, t.ex. Microsoft Azure Active Directory-programproxy. Intunes [programhanteringsverktyg och App SDK](apps-prepare-mobile-application-management.md) kan användas för att hålla kvar data i den verksamhetsspecifika appen, så att det inte går att vidareföra företagsdata till konsumentappar eller konsumenttjänster.

Använd [guiden för planering, utformning och implementering för distribution av Intune](planning-guide.md) och få hjälp med att bestämma hur du ska identifiera de organisatoriska grupper som är associerade med varje användningsfall och underanvändningsfall i appen. Mer information om hur du tilldelar appar till grupper finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md). 

### <a name="determine-the-type-of-app-for-your-solution"></a>Bestämma typ av app för en lösning
Du kan välja mellan följande apptyper:
- **Appar på webben** – En webbapp är ett klientserverprogram. Servern tillhandahåller webbappen, som innehåller användargränssnitt, innehåll och funktioner. Dessutom erbjuder moderna webbtjänstplattformar dessutom vanligen säkerhet, belastningsutjämning och andra förmåner. Den här typen av app underhålls separat på webben. Du använder Intune för att peka på den här apptypen. Du tilldelar också vilka användargrupper som ska kunna få åtkomst till den här appen. Observera att Android inte har stöd för webbappar.
- **Appar om skrivits internt (verksamhetsspecifika)** – Appar som skapats internt är verksamhetsspecifika appar (LOB). Funktionerna i den här apptypen har skapats för någon av plattformarna som stöds av Intune, som Windows, iOS eller Android. Din organisation skapar och förser dig med uppdateringar som en separat fil. Du ger användarna uppdateringar för appen genom att lägga till och distribuera uppdateringarna med Intune. 
- **Appar från Store** – En Store-app är en app som har laddats upp till antingen Windows Store, iOS Store eller Android Store. Store-appens provider underhåller och tillhandahåller uppdateringar för appen. Du väljer appen från Store-listan och lägger till den med hjälp av Intune som en app som är tillgänglig för användarna.

När du bestämmer vilka appar som krävs för din organisation bör du överväga hur apparna integrerar med molntjänster, vilka data apparna kan få åtkomst till, om apparna är tillgängliga för BYOD-användare och om apparna kräver internetåtkomst.

Mer information om att bestämma vilken typ av appar din organisation behöver finns i **Appar** i avsnittet **Funktionskrav** i [Skapa en design](planning-guide-design.md#feature-requirements).

### <a name="understanding-app-management-and-protection-policies"></a>Förstå principer för apphantering och skydd
Med Intune kan du ändra funktionen för appar som du distribuerar för att justera dem efter företagets principer för efterlevnad och säkerhet. Med den här kontrollen kan du också bestämma hur företagets data ska skyddas. Intune-hanterade appar har en omfattande uppsättning skyddsprinciper för mobila program som:

- Begränsning av funktionerna kopiera och klistra in och spara som
- Konfiguration av webblänkar som ska öppnas i appen Intune Managed Browser
- Aktivering av användning av flera identiteter och villkorlig åtkomst på appnivå

Intune-hanterade appar kan även aktivera appskydd utan att kräva registrering. På så sätt får du möjligheten att tillämpa principer för förebyggande av dataförlust utan att hantera användarens enhet. Dessutom kan du införliva hantering av mobilappar i dina mobila och verksamhetsspecifika appar med Intune App Software Development Kit (SDK) och apphanteringsverktyg. Mer information om verktygen finns i [Översikt över Intune App SDK](app-sdk.md).

### <a name="understanding-licensed-apps"></a>Förstå licensierade appar
Utöver webbappar, Store-appar och LOB-appar bör du också vara medveten om destinationen för appar för volymköpsprogram och licensierade appar som:     
- **Apples program för volyminköp för företag (iOS och MacOS)** – I iOS App Store kan du köpa flera licenser för en app som du vill använda i företaget. Om du köper flera exemplar så blir det lättare att effektivt hantera appar i ditt företag. Mer information finns i [Hantera volyminköpta iOS-appar](vpp-apps-ios.md).
- **Android for Work (Android)** – Du tilldelar appar till Android for Work-enheter på ett annat sätt än när du tilldelar dem till vanliga Android-enheter. Alla appar som du installerar för Android for Work kommer från Google Play for Work-butiken. Du kan logga in i butiken, bläddra efter de appar som du vill ha och godkänna dem. Programmet visas sedan i noden Licensierade appar i Azure-portalen. Härifrån kan du hantera tilldelningen av appen på samma sätt som du tilldelar andra appar.
- **Windows Store för företag (Windows 10)** – I Microsoft Store för företag kan du söka efter och köpa appar för din organisation, separat eller i volym. Genom att ansluta butiken till Microsoft Intune kan du hantera volyminköpta program från Azure-portalen. Mer information finns i [Hantera appar från Microsoft Store för företag](windows-store-for-business.md). 

## <a name="before-you-start"></a>Innan du börjar
Tänk på följande innan du börjar lägga till och tilldela appar.

- När du lägger till och tilldelar en app från en butik måste slutanvändare ha ett konto med den butiken för att kunna installera appen.
- Vissa appar eller objekt som du tilldelar kan vara beroende av inbyggda iOS-appar. Om du till exempel tilldelar en bok från iOS Store måste appen iBooks finnas på enheten. Om du har tagit bort den inbyggda iBooks-appen, kan du inte använda Intune för att återinföra den.

## <a name="cloud-storage-space"></a>Molnlagringsutrymme
Alla appar som du skapar med installationstypen Programinstallation (till exempel en verksamhetsspecifik app) måste paketeras och överföras till Microsoft Intunes molnlagring. En utvärderingsprenumeration på Intune inkluderar 2 GB molnbaserad lagring som används för att lagra hanterade appar och uppdateringar. 20 GB lagringsutrymme ingår i den fullständiga prenumerationen.

Du kan köpa ytterligare lagringsutrymme för Intune med din ursprungliga köpmetod.  Om du betalade via faktura eller med kreditkort besöker du [prenumerationshanteringsportalen](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  Annars kontaktar du din partner eller säljrepresentant.

Krav för lagringsutrymme i molnet:

-   Alla appinstallationsfiler måste finnas i samma mapp.
-   Den maximala filstorleken för en fil som du överför är 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Skapa och redigera kategorier för appar

Appkategorier kan användas för att sortera appar så att användarna lättare kan hitta dem i företagsportalen. Du kan tilldela en eller flera kategorier till en app, till exempel **Utvecklarprogram** eller **Kommunikationsappar**.
När du lägger till en app i Intune ges möjlighet att välja den kategori som du önskar. Använd de plattformsspecifika avsnitten för att lägga till en app och tilldela kategorier. Använd följande procedur för att skapa och redigera dina egna kategorier:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
4. Välj **Installation** > **Appkategorier** i arbetsbelastningen **Mobilappar**.
5. På bladet **Appkategorier** visas en lista över aktuella kategorier. Välj en av följande åtgärder:
    - **Skapa en kategori** – Välj **Lägg till** för att visa bladet **Skapa kategori** och lägg till ett namn på den nya kategorin. Namn kan bara anges på ett språk och översätts inte av Intune. Klicka på **Skapa** när du är klar.
    - **Redigera en kategori** – För valfri kategori i listan, välj ”**...** ”. Det här alternativet visar en popup-meny där du kan **fästa kategorin på instumentpanelen** eller **ta bort** den.

## <a name="apps-added-automatically-by-intune"></a>Appar som läggs till automatiskt av Intune

Tidigare innehöll Intune ett antal inbyggda appar för snabb tilldelning. Efter feedback från användarna har vi beslutat oss för att ta bort listan och dess inbyggda appar visas inte längre.
Om du har redan har tilldelat några inbyggda appar kommer dessa även i fortsättningen att finnas kvar i listan över appar. Du kan fortsätta att tilldela dessa appar vid behov.
I en senare version planerar vi att lägga till en enklare metod för att välja och tilldela inbyggda program från Azure-portalen.

## <a name="next-steps"></a>Nästa steg

Välj något av följande avsnitt för att ta reda på hur du lägger till appar för varje Intune-plattform:

- [Android Store-appar](store-apps-android.md)
- [Android LOB-appar](lob-apps-android.md)
- [iOS Store-appar](store-apps-ios.md)
- [iOS LOB-appar](lob-apps-ios.md)
- [Webbappar (för alla plattformar)](web-app.md)
- [Windows Phone 8.1 Store-appar](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB-appar](lob-apps-windows-phone.md)
- [Windows Store-appar](store-apps-windows.md)
- [Windows LOB-appar](lob-apps-windows.md)
- [Office 365-appar för Windows 10](apps-add-office365.md)
- [Inbyggda appar](apps-add-bulit-in.md)

