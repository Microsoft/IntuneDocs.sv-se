---
title: "Kom igång med grupper i förhandsversionen av Intune i Azure-portalen | Microsoft Docs"
description: "Läs mer om nyheterna med grupper i förhandsversionen av Intune i Azure-portalen"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 01/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 27a9c9d8269b302fa9735972056d38e7919f42b5


---

# <a name="get-started-with-groups"></a>Kom igång med grupper

[!INCLUDE[azure preview](../includes/azure_preview.md)]

Vi har hört er feedback och har därför gjort några ändringar i hur man arbetar med grupper i Microsoft Intune.
Om du använder Intune från Azure-portalen, har dina Intune-grupper migrerats till Azure Active Directory-säkerhetsgrupper.

Fördelen för dig är att du nu kan använda samma grupper för alla dina Enterprise Mobility + Security och Azure AD-appar. Dessutom kommer du att kunna använda PowerShell och Graph API för att utöka och anpassa den här nya funktionen.

Azure AD-säkerhetsgrupper stöder alla typer av Intune-distributioner för både användare och enheter. Du kan dessutom använda dynamiska grupper i Azure AD som automatiskt uppdateras baserat på de attribut som du anger. Du kan till exempel skapa en grupp av enheter som kör iOS 9. När en ny enhet som kör iOS 9 registreras läggs den automatiskt till den dynamiska gruppen.

## <a name="what-is-not-available"></a>Vad är inte tillgängligt?

Vissa av de funktioner för Intune-grupper som du tidigare kan ha använt är inte tillgängliga i Azure AD:

- Intune-grupperna **Användare utan grupp** och **Enheter utan grupp** är inte längre tillgängliga.
- Alternativet att **Exkludera vissa medlemmar** från en grupp finns inte i Azure-portalen. Du kan dock använda en Azure AD-säkerhetsgrupper med avancerade regler för att replikera dessa gruppers beteende. Du kan till exempel skapa en avancerad regel som inkluderar alla personer i din försäljningsavdelning i en säkerhetsgrupp, men inte de som har ordet "Assistent" i sina jobbtitlar med den här avancerade regeln: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- Gruppen **Alla hanterade enheter i Exchange ActiveSync** som är inbyggd i Intune-konsolen migrerades inte till Azure AD. Du kan emellertid fortfarande komma åt information om EAS-hanterade enheter från Azure Portal.


## <a name="how-to-get-started"></a>Hur kommer man igång?

- Läs följande Azure AD-avsnitt för mer information om Azure AD-säkerhetsgrupper och hur de fungerar:
    -  [Hantera åtkomst till resurser med Azure Active Directory-grupper](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
    -  [Hantera grupper i Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Använda attribut för att skapa avancerade regler](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
-  Kontrollera att alla administratörer som behöver skapa grupper läggs till i Azure AD-rollen **Administratör för Intune-tjänsten**. Notera att Azure AD-rollen Tjänstadministratör inte har behörighet att **hantera grupper**.
-  Överväg om du kan göra om grupper så att de inte använder undantag, eller om du kan använda avancerade regler i din Azure AD-fråga för att uppnå samma resultat om du använder grupper med alternativet **Exkludera särskilda medlemmar**.


## <a name="what-happened-to-intune-groups"></a>Vad hände med Intune-grupperna?

| Grupper i Intune|Grupper i Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Statisk användargrupp|Statisk Azure AD-säkerhetsgrupp|
|Dynamisk användargrupp|Statiska Azure AD-säkerhetsgrupper med hierarki för Azure AD-säkerhetsgrupper|
|Statisk enhetsgrupp|Statisk Azure AD-säkerhetsgrupp|
|Dynamisk enhetsgrupp|Dynamisk Azure AD-säkerhetsgrupp|
|En grupp med ett inkluderingsvillkor|Statisk Azure AD-säkerhetsgrupp som innehåller några statiska/dynamiska medlemmar från inkluderingsvillkoret i Intune|
|En grupp med ett exkluderingsvillkor|Migreras inte|
|De inbyggda grupperna **Alla användare**, **Uppdelade användare**, **Alla enheter**, **Uppdelade enheter**, **Alla datorer**, **Alla mobila enheter**, **All MDM managed devices** (Alla MDM-enheter), och **All EAS managed devices** (Alla EAS-hanterade enheter)|Azure AD-säkerhetsgrupper|

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

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>Vad händer med principer och appar som du tidigare har distribuerat?

Principer och appar fortsätter att distribueras till grupper precis som tidigare. Men du kan nu hantera dessa grupper från Azure Portal i stället för från den klassiska Intune-konsolen.



<!--HONumber=Feb17_HO1-->


