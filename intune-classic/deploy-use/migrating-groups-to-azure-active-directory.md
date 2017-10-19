---
title: Migrera till Azure Active Directory-grupper
description: "Så kommer dina grupper att migrera från Intune till Azure AD"
keywords: 
author: arob98
ms.author: angrobe
manager: angerobe
ms.date: 12/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: 5eb6a72abd28b566b7588e56647787dc669706bc
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="a-new-way-of-using-groups-in-intune"></a>Ett nytt sätt att använda grupper i Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Vi har hört er feedback och gör därför några ändringar i hur du arbetar med grupper i Microsoft Intune.
Vi håller på att migrera alla våra kunders Intune-grupper till Azure Active Directory-säkerhetsgrupper.

Fördelen för dig är att du nu kan använda samma grupper för alla dina Enterprise Mobility + Security och Azure AD-appar. Dessutom kommer du att kunna använda PowerShell och Graph API för att utöka och anpassa den här nya funktionen.

Azure AD-säkerhetsgrupper stöder alla typer av Intune-distributioner för både användare och enheter. Du kan dessutom använda dynamiska grupper i Azure AD som automatiskt uppdateras baserat på de attribut som du anger. Du kan till exempel skapa en grupp av enheter som kör iOS 9. När en ny enhet som kör iOS 9 registreras läggs den automatiskt till den dynamiska gruppen.

## <a name="when-is-this-happening"></a>När kommer detta att ske?

Migreringen pågår just nu. Du kommer att meddelas innan migreringen utförs för dig.
Om du har redan har blivit migrerad kommer du att se ett meddelande som liknar det här när du försöker komma åt grupper från den klassiska Intune-konsolen:

![Meddelande för att visa att grupper har migrerats.](http://i.imgur.com/72KRaXj.png)

## <a name="what-wont-be-available"></a>Vad kommer inte att vara tillgängligt?

Vissa befintliga funktioner i Intune-grupper är inte tillgängliga i Azure AD:

- Intune-grupperna **Användare utan grupp** och **Enheter utan grupp** kommer inte att migreras.
- Alternativet **Exkludera vissa medlemmar** från en grupp som finns i Intune-konsolen finns inte i Azure Portal. Du kan dock använda en Azure AD-säkerhetsgrupper med avancerade regler för att replikera dessa gruppers beteende. Du kan till exempel skapa en avancerad regel som inkluderar alla personer i din försäljningsavdelning i en säkerhetsgrupp, men inte de som har ordet "Assistent" i sina jobbtitlar med den här avancerade regeln: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- Gruppen **Alla hanterade enheter i Exchange ActiveSync** som är inbyggd i Intune-konsolen kommer inte att migreras till Azure AD. Du kan emellertid fortfarande komma åt information om EAS-hanterade enheter från Azure Portal.
- Du kommer inte att kunna filtrera rapporter med grupper i den klassiska Intune-konsolen.
<!--- - Custom group targeting of notification rules will not be available. ROB I took this out as I couldn't replicate the behavior. --->

## <a name="how-to-get-ready"></a>Hur du förbereder dig

- Läs följande Azure AD-avsnitt för mer information om Azure AD-säkerhetsgrupper och hur de fungerar:
    -  [Hantera åtkomst till resurser med Azure Active Directory-grupper](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/).
    -  [Hantera grupper i Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Använda attribut för att skapa avancerade regler](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
- Överväg att ta bort de Intune-grupper som du inte längre använder innan du migrerar.
-  Kontrollera att alla administratörer som behöver skapa grupper läggs till i Azure AD-rollen **Administratör för Intune-tjänsten**. Notera att Azure AD-rollen Tjänstadministratör inte har behörighet att **hantera grupper**.
-  Överväg om du kan göra om grupper så att de inte använder undantag, eller om du kan använda avancerade regler i din Azure AD-fråga för att uppnå samma resultat om du använder grupper med alternativet **Exkludera särskilda medlemmar**.


## <a name="what-happens-to-intune-groups"></a>Vad händer med Intune-grupperna?

| Grupper i Intune|Grupper i Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Statisk användargrupp|Statisk Azure AD-säkerhetsgrupp|
|Dynamisk användargrupp|Statiska Azure AD-säkerhetsgrupper med hierarki för Azure AD-säkerhetsgrupper|
|Statisk enhetsgrupp|Statisk Azure AD-säkerhetsgrupp|
|Dynamisk enhetsgrupp|Dynamisk Azure AD-säkerhetsgrupp|
|En grupp med ett inkluderingsvillkor|Statisk Azure AD-säkerhetsgrupp som innehåller några statiska/dynamiska medlemmar från inkluderingsvillkoret i Intune.|
|En grupp med ett exkluderingsvillkor|Migreras inte|
|De inbyggda grupperna **Alla användare**, **Uppdelade användare**, **Alla enheter**, **Uppdelade enheter**, **Alla datorer**, **Alla mobila enheter**, **All MDM managed devices** (Alla MDM-enheter), och **All EAS managed devices** (Alla EAS-hanterade enheter)|Azure AD-säkerhetsgrupper.|

Alla grupper måste ha en överordnad grupp i Intune. Grupper kan endast innehålla medlemmar från den överordnade gruppen. Underordnade grupper i Azure AD kan innehålla medlemmar som inte är i den överordnade gruppen.

Attribut är enhetsegenskaper som kan användas för att definiera grupper. Den här tabellen beskriver hur dessa villkor kommer att migreras till Azure AD-säkerhetsgrupper.

| Attribut i Intune|Attribut i Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Organisationsenhetsattribut för enhetsgrupper|Organisationsenhetsattribut för dynamiska grupper.|
|Domännamnsattribut för enhetsgrupper|Domännamnsattribut för dynamiska grupper.|
|Säkerhetsgrupper som ett attribut för användargrupper|Grupper kan inte vara attribut i dynamiska frågor i Azure AD. Dynamiska grupper kan bara innehålla specifika attribut för användare eller enheter.|
|Chefsattribut för användargrupper|Avancerad regeln för *chefs*attribut i dynamiska grupper|
|Alla användare från den överordnade enhetsgruppen|Statisk grupp med den gruppen som en medlem|
|Alla mobila enheter från den överordnade enhetsgruppen|Statisk grupp med den gruppen som en medlem|
|Alla mobila enheter som hanteras med Intune|Hantera typsattribut med ‘MDM’ som värde för en dynamisk grupp|
|Kapslade grupper i statiska grupper |Kapslade grupper i statiska grupper|
|Kapslade grupper i dynamiska grupper|Dynamisk grupp med en kapslingsnivå|

## <a name="what-happens-to-policies-and-apps-youve-already-deployed"></a>Vad händer med principer och appar som du redan har distribuerat?

Principer och appar fortsätter att distribueras till grupper precis som tidigare. Men du kan nu hantera dessa grupper från Azure Portal i stället för från den klassiska Intune-konsolen.
 
