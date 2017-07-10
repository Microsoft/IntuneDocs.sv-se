---
title: "Principinställningar för Exchange ActiveSync"
description: "Använd Exchange ActiveSync-principen för att konfigurera inställningar som låter dig styra funktioner och funktionalitet på enheter som hanteras av Exchange ActiveSync."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6bbb0cd7ca87a3c6cc352cbdd6dd2b61a9c5e36c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="exchange-activesync-policy-settings-in-microsoft-intune"></a>Exchange ActiveSync-principinställningar i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Använd **Exchange ActiveSync**-principen i Microsoft Intune för att konfigurera inställningar som styr en mängd funktioner på enheter som hanteras av Exchange ActiveSync.


## <a name="password-settings"></a>Inställningar för lösenord

|Inställningsnamn|Information
|----------------|---|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Anger om enheter måste vara låsta med ett lösenord.<br>(gäller inte enheter som kör Windows RT).|
|**Lösenordstyp krävs**|Anger vilken typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt.|
|**Minsta längd på lösenord**|Anger det minsta antalet tecken som enhetslösenordet måste innehålla.|
|**Tillåt enkla lösenord**|Anger om du kan använda enkla lösenord, bland annat "0000" och "1234".|
|**Antal tillåtna, upprepade felinloggningar innan enheten rensas**|Anger antalet gånger som användaren kan ange ett felaktigt lösenord innan enheten rensas.|
|**Lösenordets giltighetstid (i dagar)**|Anger efter hur många dagar lösenordet måste ändras.
|**Kom ihåg tidigare lösenord**|Anger huruvida det är tillåtet att använda lösenord som har använts tidigare.|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Anger antalet lösenord som har använts tidigare som inte får användas igen.|
|**Antal minuters inaktivitet innan lösenord krävs**|Anger hur lång tid en enhet måste vara inaktiv innan skärmen låses.

## <a name="encryption-settings"></a>Krypteringsinställningar

|Inställningsnamn|Information|
|----------------|---|
|**Kräv kryptering på den mobila enheten**<sup>1</sup>|Kräver att data på en enhet krypteras när detta stöds.<br><br>För Windows Phone 8-enheter måst du ställa in denna på **Ja**.<br /><br />Om du vill möjliggöra kryptering på iOS-enheter måste du aktivera inställningen **Kräv lösenord för att låsa upp mobila enheter**.|
|**Kräv kryptering på minneskort**|Kräver att data som lagras på externa lagringsenheter, t.ex. ett SD-kort, ska krypteras (på enheter som stöds).
<sup>1</sup> Ytterligare information för enheter som kör Windows 8.1

-   Om du vill tillämpa kryptering på enheter som kör Windows 8.1 måste du installera [December 2014 MDM-klientuppdateringen för Windows](https://support.microsoft.com/kb/3013816) på varje enhet.

-   Om du aktiverar den här inställningen för Windows 8.1-enheter måste alla användare av sådana enheter ha ett Microsoft-konto.

-   Om du vill att krypteringen ska fungera för Windows 8.1-enheter måste enheten uppfylla Microsofts [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) -maskinvarucertifieringskrav.

-   Om du tillämpar kryptering på en Windows 8.1-enhet är återställningsnyckeln enbart tillgänglig från användarens Microsoft-konto, som nås från användarens OneDrive-konto. Du kan inte återställa denna nyckel för en användares räkning.

## <a name="email-settings"></a>E-postinställningar

|Inställningsnamn|Information
|----------------|---|
|**Tillåt användare att hämta e-postbilagor**|Anger om bifogade filer i e-postmeddelanden ska kunna hämtas till enheten.|
|**E-postsynkroniseringsperiod**|Anger hur många dagar med mottagen e-post som ska synkroniseras till enheten.
|**Tillåt mobila enheter som inte fullt ut stöder inställningarna i Exchange ActiveSync att synkroniseras med Exchange**|Anger om Exchange-åtkomst ska tillåtas på enheter som inte har stöd för en eller flera Exchange ActiveSync-inställningar.

## <a name="browser-settings"></a>Webbläsarinställningar

|Inställningsnamn|Information
|----------------|---|
|**Tillåt webbläsare**|Anger om webbläsaren på enheten får användas.<br>(Inte tillgängligt för Windows RT eller Windows Phone).

## <a name="hardware-settings"></a>Maskinvaruinställningar

|Inställningsnamn|Information
|----------------|---|
|**Tillåt kamera**|Anger om kameran på enheten får användas.<br>(Inte tillgängligt för Windows RT eller Windows Phone).



### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
