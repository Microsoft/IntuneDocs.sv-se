---
title: Exchange-åtkomstregler för mobila enheter
description: Exchange ActiveSync-åtkomstregler för att tillåta eller blockera enhetsanslutningar med EAS
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 93dece592ce5280b1650303484bd24169814465c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="exchange-access-rules-for-mobile-devices"></a>Exchange-åtkomstregler för mobila enheter

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Exchange-åtkomstregler för mobila enheter avgör vilken åtkomstnivå som dessa enheter har till Exchange ActiveSync. De här inställningarna påverkar alla mobila enheter, inklusive sådana som inte har registrerats i Microsoft Intune. Du kan börja med att definiera en **standardregel** som gäller för alla mobila enheter som inte har en anpassad regel som tillämpas.

Följande tabell innehåller åtkomstnivåerna som hanteras av Exchange ActiveSync:

|Åtkomstnivå|Beskrivning|
|----------------|---------------|
|**Bevilja enheterna åtkomst till Exchange**|I läget *tillåt åtkomst* kan en mobil enhet synkronisera via Exchange ActiveSync och ansluta till Exchange-servern för att hämta e-post och hantera kalender, kontakter, uppgifter och anteckningar. Detta fortsätter så länge enheten överensstämmer med någon Exchange ActiveSync-postlådeprincip som du har konfigurerat i Exchange, om inte användaren eller den mobila enheten har blockerats av Exchange-administratören.|
|**Blockera enheterna från åtkomst till Exchange**|I läget *blockera åtkomst* är mobila enheter blockerade och tillåts inte att ansluta till Exchange-servern. Enheterna får felmeddelandet HTTP 403 Åtkomst nekas. Användaren får ett e-postmeddelande från Exchange-servern som anger att den mobila enheten har blockerats från att komma åt sin postlåda. Det här meddelandet får inte finnas på den blockerade mobila enheten. Genom att använda **Ange användarmeddelande** kan du lägga till anpassad text i det här meddelandet som innehåller anvisningar för de användare vars enheter har blockerats. |
|**Sätt enheterna i karantän så att du kan tillåta eller blockera dem senare**|När en mobil enhet sätts i karantän tillåts den mobila enheten att ansluta till Exchange-servern. Men den har endast begränsad åtkomst till data. Användaren kan lägga till innehåll i kalendern, kontakter, aktiviteter och anteckningsmappar men servern tillåter inte att enheten hämtar innehåll från postlådan. Användaren får ett e-postmeddelande som anger att den mobila enheten har placerats i karantän. Det här meddelandet skickas till enheten och användarens postlåda. Genom att använda **Ange användarmeddelande** kan du lägga till anpassad text i det här meddelandet som innehåller anvisningar för de användare vars enheter har satts i karantän.|

En åtkomststrategi är en kombination av en **standardregel** och **plattformsundantag** som gäller för alla mobila enheter som är anslutna till Exchange. I följande tabell visas några exempel på åtkomststrategier.


|    Åtkomststrategi    |                                                                                                                                                                                                                                                                                       Beskrivning                                                                                                                                                                                                                                                                                        |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Lista över tillåtna       |                                                                                  Du kan använda en <em>lista över tillåtna</em> för att bevilja åtkomst till en lista med kända enheter och begränsa åtkomsten för alla andra enheter. Om du vill göra detta måste du skapa anpassade regler för enhetsplattformar med tillgång till användarnas postlådor. När du skapar en sådan regel måste du ange standardregeln för åtkomst till att blockera eller sätta alla andra enheter i karantän. Om du vill lägga till en ny enhet i listan över tillåtna enheter kan du skapa en ny anpassad regel.                                                                                  |
|      Blockeringslista       |                              Du kan använda en <em>blockeringslista</em> för att bevilja åtkomst till alla enheter som standard, men blockera åtkomsten för ett antal enheter som inte ska få åtkomst till organisationen. Skapa en blockeringslista genom att skapa anpassade regler som blockerar enhetsplattformar som du inte vill synkronisera med organisationens postlådor. Vi rekommenderar att du anger en standardregel som tillåter åtkomst till alla enheter som inte uttryckligen blockeras av befintliga regler. Om du vill lägga till en ny enhet eller uppsättning enheter i blockeringslistan skapar du en ny anpassad regel.                               |
| Blandat tillåt och blockera | Utöver att skapa listor över tillåtna och blockeringslistor kan du sätta nya mobila enheter i karantän när de kommer med i organisationen under tiden du utvärderar dem. Exempel: Om du har en blockeringslista för mobila enheter som inte tillåts i organisationen och en lista över tillåtna för mobila enheter som tillåts i organisationen kan du ange att standardregeln är att sätta i karantän. Alla andra enheter sätts automatiskt i karantän. Det gör att du kan identifiera nya enheter när de introduceras i organisationen och bestämma om du ska lägga till dem i listorna över tillåtna eller blockerade. |

Följande procedur beskriver hur du skapar en anpassad regel.

## <a name="create-a-default-access-rule"></a>Skapa en standardregel för åtkomst

1.  Välj **Princip** &gt; **Exchange ActiveSync** på [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com).

2.  Gå till listan **Standardregel** och markera den åtkomstregel som du vill koppla till alla mobila enheter som inte omfattas av en regel eller ett personligt undantag. Välj **Spara**.

Följande procedur beskriver hur du skapar en anpassad regel:

## <a name="create-a-custom-access-rule"></a>Skapa en anpassad åtkomstregel

1. Välj **Princip** &gt; **Exchange ActiveSync** på [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com).

2.  Välj **Lägg till regel** i listan **Plattformsundantag** och skapa sedan en anpassad regel. Välj **Spara**.
