---
title: "Exchange-åtkomstregler för mobila enheter | Microsoft Intune"
description: "Exchange ActiveSync-åtkomstregler för att tillåta eller blockera enhetsanslutningar med EAS"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c49e19e8c478af252d7b59c380d5500a57b71db5
ms.openlocfilehash: 7714a338d02afedde2ac090964e4d18d4410a80e


---

# Exchange-åtkomstregler för mobila enheter
Exchange-åtkomstregler för mobila enheter avgör vilken åtkomstnivå dessa enheter har till Exchange ActiveSync. De här inställningarna påverkar alla mobila enheter, inklusive sådana som inte är registrerade i Microsoft Intune. Du kan börja med att definiera en **standardregel** som gäller för alla mobila enheter som inte har en anpassad regel som tillämpas. Följande tabell innehåller åtkomstnivåerna som hanteras av Exchange ActiveSync:

|Åtkomstnivå|Beskrivning|
|----------------|---------------|
|**Bevilja enheterna åtkomst till Exchange**|I läget *tillåt åtkomst* kan en mobil enhet synkronisera via Exchange ActiveSync och ansluta till Exchange-servern för att hämta e-post och hantera kalender, kontakter, uppgifter och anteckningar. Detta fortsätter så länge enheten överensstämmer med någon Exchange ActiveSync-postlådeprincip som du har konfigurerat i Exchange, om inte användaren eller den mobila enheten har blockerats av Exchange-administratören.|
|**Blockera enheterna från åtkomst till Exchange**|I läget *blockera åtkomst* är mobila enheter blockerade och tillåts inte att ansluta till Exchange-servern. Enheterna får felmeddelandet HTTP 403 Åtkomst nekas. Användaren får ett e-postmeddelande från Exchange-servern som anger att den mobila enheten har blockerats från att komma åt sin postlåda. Det här meddelandet får inte finnas på den blockerade mobila enheten. Du kan lägga till anpassad text i det här meddelandet för att ge instruktioner åt användare vars enheter har blockerats via aktiviteten **Ange användarmeddelande**.|
|**Sätt enheterna i karantän så att du kan tillåta eller blockera dem senare**|När en mobil enhet sätts i karantän tillåts den mobila enheten att ansluta till Exchange-servern. Men den har endast begränsad åtkomst till data. Användaren kan lägga till innehåll i kalendern, kontakter, aktiviteter och anteckningsmappar men servern tillåter inte att enheten hämtar innehåll från postlådan. Användaren får ett e-postmeddelande som anger att den mobila enheten har placerats i karantän. Det här meddelandet tas emot på enheten och i användarens postlåda. Du kan lägga till anpassad text i det här meddelandet för att ge instruktioner åt användare vars enheter finns i karantän via aktiviteten **Ange användarmeddelande** .|

En åtkomststrategi är en kombination av en **standardregel** och **plattformsundantag** som gäller för alla mobila enheter som är anslutna till Exchange. I tabellen nedan visas några exempel på åtkomststrategier.

|Åtkomststrategi|Beskrivning|
|-------------------|---------------|
|Lista över tillåtna|Du kan använda en *lista över tillåtna* för att bevilja åtkomst till en lista med kända enheter och begränsa åtkomsten för alla andra. Om du vill göra det måste du skapa anpassade regler för enhetsplattformar med tillgång till användarnas postlådor. När du skapar en sådan regel måste du ange standardregeln för åtkomst till att blockera eller sätta alla andra enheter i karantän. Om du vill lägga till en ny enhet i listan över tillåtna enheter kan du skapa en ny anpassad regel|
|Blockeringslista|Du kan använda en *blockeringslista* för att bevilja åtkomst till alla enheter som standard, men blockera åtkomsten för ett antal enheter som inte ska få åtkomst till organisationen. Skapa en blockeringslista genom att skapa anpassade regler som blockerar enhetsplattformar som du inte vill synkronisera med organisationens postlådor. Standardregeln ska anges till tillåt åtkomst till alla enheter som inte uttryckligen blockeras av befintliga regler. Om du vill lägga till en ny enhet eller uppsättning enheter i blockeringslistan skapar du en ny anpassad regel.|
|Blandat tillåt och blockera|Utöver att skapa listor över tillåtna och blockeringslistor kan du sätta nya mobila enheter i karantän när de kommer med i organisationen under tiden du utvärderar dem. Exempel: Om du har en blockeringslista för mobila enheter som inte tillåts i organisationen och en lista över tillåtna för mobila enheter som tillåts i organisationen kan du ange att standardregeln är att sätta i karantän. Alla andra enheter sätts i karantän automatiskt. Det gör att du kan identifiera nya enheter när de introduceras i organisationen och bestämma om du ska lägga till dem i listan över tillåtna eller i blockeringslistan.|
Följande procedur beskriver hur du skapar en anpassad regel.

## Skapa en standardregel för åtkomst

1.  I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) &gt; **Princip** &gt; **Exchange ActiveSync**.

2.  I listan **Standardregel** markerar du den åtkomstregel som du vill koppla till alla mobila enheter som inte omfattas av en regel eller personligt undantag. Välj **Spara**.

Följande procedur beskriver hur du skapar en anpassad regel.

## Skapa en anpassad åtkomstregel

1. I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) &gt; **Princip** &gt; **Exchange ActiveSync**.

2.  I listan **Plattformsundantag** väljer du **Lägg till regel** och skapar en anpassad regel. Välj **Spara**.



<!--HONumber=Aug16_HO1-->


