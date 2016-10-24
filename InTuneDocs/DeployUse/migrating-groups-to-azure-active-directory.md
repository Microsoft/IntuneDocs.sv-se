---
title: Migrera till Azure Active Directory-grupper | Microsoft Intune
description: "Så kommer dina grupper att migrera från Intune till Azure AD"
keywords: 
author: nbigman
manager: angerobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
translationtype: Human Translation
ms.sourcegitcommit: d92c9ffe42b36770a32c28941de3c402aec9dd68
ms.openlocfilehash: 08bcc258f64e6385ae6fa648ddb8f2b5fe68942e


---

## Den nya gruppmiljön för administratörer
    
Efter att ha fått feedback om en enskild upplevelse för grupper och målgrupper i Enterprise Mobility & Security har vi gjort om Intune-grupper till Azure Active Directory-baserade säkerhetsgrupper. Det skapar en enhetlig grupphantering i Intune och Azure Active Directory (Azure AD). Det innebär att du undviker duplicerade grupper mellan tjänster och kan utöka med PowerShell och Graph. 

### Hur och när kommer jag att migrera till den nya upplevelsen?
Aktuella kunder kommer att migreras under en viss tidsperiod, som tidigast börjar i december 2016. Du kommer att få ett meddelande innan dina grupper migreras. Om du har några frågor angående migreringen kan du kontakta vårt migreringsteam på [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### Vilka nya funktioner kommer att vara tillgängliga för mig?
Här är de nya funktionerna som introduceras: 
 
-    Azure AD-säkerhetsgrupper stöds i Intune för alla typer av distributioner. 
-    Azure AD-säkerhetsgrupper stöder gruppering av enheter tillsammans med användare.
-    Azure AD-säkerhetsgrupper kommer att ha stöd för dynamiska grupper med Intune-enhetsattribut. Till exempel kommer du att kunna gruppera enheter dynamiskt baserat på plattform, till exempel iOS. När en ny iOS-enhet registreras i din organisation läggs den därmed automatiskt till i den dynamiska iOS-enhetsgruppen.
-    Delade administratörsupplevelser för grupphantering i Azure AD och Intune.
- *Intune-tjänstadministratörsrollen* kommer att läggas till i Azure AD så att tjänstadministratörer i Intune kan utföra grupphanteringsuppgifter i Azure AD.

 
### Vilka Intune-funktioner kommer inte att vara tillgängliga?
Grupphanteringen kommer att vara bättre, men vissa Intune-funktioner kommer inte att vara tillgängliga efter migreringen.

#### Funktionen Hantering av grupper

-   Du kommer inte att kunna undanta medlemmar eller grupper när du skapar en ny grupp. Men med dynamiska grupper i Azure AD kan du använda attribut för att skapa avancerade regler för att undanta medlemmar baserat på kriterier. Du kan till exempel skapa en avancerad regel som inkluderar alla personer i din försäljningsavdelning i en säkerhetsgrupp, men inte de som har ordet "Assistent" i sina jobbtitlar med den här avancerade regeln: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`. Se [Använda attribut för att skapa avancerade regler](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/) för mer information.
-   Det kommer inte att finnas stöd för grupperna **Användare utan grupp** och **Enheter utan grupp**. Dessa grupper migreras inte.

#### Gruppberoende funktioner

-   Rollen Tjänstadministratör kommer inte att ha behörighet att **hantera grupper**.
-   Du kommer inte att kunna gruppera Exchange ActiveSync-enheter.  Gruppen **Alla Exchange ActiveSync-hanterade enheter** kommer att konverteras från en grupp till en rapport.
-  Pivotering med grupper i rapporter kommer inte att vara tillgängligt.
-  Anpassade meddelanderegler för specifika grupper kommer inte att vara tillgängligt.

### Vad kan jag göra för att förbereda mig för den här ändringen?
 Vi har rekommendationer som underlättar övergången:
 
- Ta bort alla oönskade eller onödiga Intune-grupper före migreringen.
- Utvärdera din användning av undantag i grupper och fundera på hur du kan ändra dina grupper så att du inte behöver använda undantag, eller hur du kan göra för att använda avancerade regler för att uppnå samma ändamål.
-  Om det finns administratörer i organisationen som inte har behörighet att skapa grupper i Azure AD kan du be Azure AD-administratören att lägga till dem i rollen **Intune-tjänstadministratör** i Azure AD.

Du kan även lära dig mer om Azure AD-säkerhetsgrupper:
-  En översikt finns på sidan [Hantera åtkomst till resurser med Azure Active Directory-grupper](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
-  Se [Hantera grupper i Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/) för information om hur du skapar och hanterar Azure AD-grupper.
-  Se [Använda attribut för att skapa avancerade regler](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/) för mer information om avancerade regler för säkerhetsgrupper.

> [!NOTE]
Du kanske upptäcker att dokumentationen för Azure AD-säkerhetsgrupper inte nämner skapandet av grupper för enheter. Den funktionen kommer att finnas i Azure AD innan migreringen av Intune-grupper börjar.

## Information om migrering
Här följer information om hur Intune-grupper kommer att migreras till Azure AD-säkerhetsgrupper.

### Migrering av befintliga grupper

| Intune-grupper blir...|... Azure AD-säkerhetsgrupper|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Statiska användargrupper som är mål för Intune-principer|Statiska Azure AD-säkerhetsgrupper som innehåller samma användare|
|Dynamiska användargrupper som är mål för Intune-principer|Statiska Azure AD-säkerhetsgrupper med hierarki för Azure AD-säkerhetsgrupper|
|Statiska enhetsgrupper som är mål för Intune-principer|Statiska Azure AD-säkerhetsgrupper med enheter|
|Dynamiska enhetsgrupper med enhetsattribut som är mål för Intune-principer|Dynamiska Azure AD-säkerhetsgrupper med enhetsattribut|
|En grupp med ett inkluderingsvillkor|En separat statisk Azure AD-säkerhetsgrupp som innehåller en grupp + statiska/dynamiska medlemmar som inkluderingsvillkoret har tillåtit i Intune|
|En grupp med ett exkluderingsvillkor|...kommer inte att migreras. Exkluderingsvillkor stöds inte när du skapar statiska grupper i Azure AD. Ett exkluderingsvillkor kan användas när du skapar dynamiska grupper i Azure AD.|
|Standardgrupperna **Alla användare**, **Uppdelade användare**, **Alla enheter**, **Uppdelade enheter**, **Alla datorer**, **Alla mobila enheter**, **All MDM managed devices** (Alla MDM-enheter), och **All EAS managed devices** (Alla EAS-hanterade enheter), som du använder i Intune-principer  |Azure AD-säkerhetsgrupper. Standardgrupper som inte används måste skapas av kunden vid behov genom att använda dynamiska grupper.|

### Ändringar i hierarkiska vyer
Hierarkisk vy för grupper i Intune. Överordnade och underordnade relationer i Intune var supermängd-delmängd-relationer, men i Azure AD är det inte fallet. Underordnade kan ha medlemmar som inte är i den överordnade. Grupper kan också vara cykliska till sin natur i Azure AD – en överordnad grupp kan även vara en underordnad grupps underordnade.

### Attributkonvertering under migreringen
Attribut är enhetsegenskaper som kan användas för att definiera grupper. Den här tabellen beskriver hur dessa villkor kommer att migreras till Azure AD-säkerhetsgrupper.

| Intune-attribut|Azure AD-attribut|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Organisationsenhetsattribut för enhetsgrupper|Organisationsenhetsattribut för dynamiska grupper. Attributvärden görs tillgängliga för administratören som hör till klienten genom att de läggs till som klientkomponenter för visning.|
|Domännamnsattribut för enhetsgrupper|Domännamnsattribut för dynamiska grupper. Attributvärden görs tillgängliga för administratören som hör till klienten genom att de läggs till som klientkomponenter för visning|
|Säkerhetsgrupper som ett attribut för användargrupper|Grupper kan inte vara attribut i dynamiska frågor i Azure AD. Dynamiska grupper kan bara innehålla specifika attribut för användare eller enheter.|
|Chefsattribut för användargrupper|Avancerad regeln för *chefs*attribut i dynamiska grupper|
|Alla användare från den överordnade enhetsgruppen|Statisk grupp med den gruppen som en medlem|
|Alla mobila enheter från den överordnade enhetsgruppen|Statisk grupp med den gruppen som en medlem|
|Alla mobila enheter som hanteras av Microsoft Intune direkthantering|Hantera typsattribut med ‘MDM’ som värde för en dynamisk grupp|
|Alla mobila enheter som hanteras med EAS|EAS enheter kan inte grupperas i Azure AD. Gruppen **Alla Exchange ActiveSync-hanterade enheter** kommer att konverteras från en grupp till en rapport.|
|Kapslade grupper i statiska grupper |Kapslade grupper i statiska grupper|
|Kapslade grupper i dynamiska grupper|Dynamisk grupp med en kapslingsnivå|


## Principmigrering
Under tiden som migreringen av grupper sker kan du fortsätta att hantera dina principer i Intune-konsolen. Intune-konsolen kommer att ha en länk till Azure-hanteringskonsolen, där du kan hantera dina grupper. Dina principer kommer att fortsätta att distribueras till de migrerade Azure AD-säkerhetsgrupperna som är parallella till din gamla Intune-grupper.

När alla Intune-funktioner migrerats till Azure-hanteringsportalen (runt första kvartalet av 2017) kommer du att hantera principer och grupper där.

     
### Se även
[Hantera åtkomst till resurser med Azure Active Directory-grupper](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)

[Hantera grupper i Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)

[Använda attribut för att skapa avancerade regler](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)



<!--HONumber=Oct16_HO2-->


