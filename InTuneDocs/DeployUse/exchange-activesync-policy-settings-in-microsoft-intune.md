---
# required metadata

title: Exchange ActiveSync-principinställningar | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Exchange ActiveSync-principinställningar i Microsoft Intune
Använd **Exchange ActiveSync**-principen i Microsoft Intune för att konfigurera inställningar som låter dig styra en mängd funktioner på enheter som hanteras av Exchange ActiveSync.


## Inställningar för lösenord

|Inställningsnamn|Information
|----------------|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Anger om enheter måste vara låsta med ett lösenord.<br>(gäller inte enheter som kör Windows RT)|
|**Lösenordstyp krävs**|Anger den typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt.|
|**Minsta längd på lösenord**|Anger det minsta antalet tecken som enhetslösenordet måste innehålla.|
|**Tillåt enkla lösenord**|Exempel på enkla lösenord är "0000" och "1234".|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Tillåt detta antal försök att ange ett korrekt lösenord innan enheten rensas.|
|**Lösenordets giltighetstid (i dagar)**|Anger efter hur många dagar lösenordet måste ändras.
|**Kom ihåg tidigare lösenord**|Anger huruvida det är tillåtet att använda lösenord som har använts tidigare.|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Anger antalet lösenord som har använts tidigare som inte får återanvändas.|
|**Antal minuters inaktivitet innan lösenord krävs**|Anger hur lång tid en enhet måste vara inaktiv innan skärmen låses.

## Krypteringsinställningar

|Inställningsnamn|Information|
|----------------|
|**Kräv kryptering på den mobila enheten**<sup>1</sup>|Kräver att data på enheten krypteras när detta stöds.<br>För Windows Phone 8-enheter måst du ställa in denna på **Ja**.<br /><br />Om du vill möjliggöra kryptering på iOS-enheter måste du aktivera inställningen **Kräv lösenord för att låsa upp mobila enheter**.|
|**Kräv kryptering på minneskort**|Kräver att data som lagras på externa lagringsenheter, t.ex. ett SD-kort, ska krypteras (på enheter som stöds).
<sup>1</sup> Ytterligare information för enheter som kör Windows 8.1

-   Om du vill framtvinga kryptering på enheter som kör Windows 8.1 måste du installera [December 2014 MDM-klientuppdateringen för Windows](http://support.microsoft.com/kb/3013816) på varje enhet.

-   Om du aktiverar den här inställningen för Windows 8.1-enheter måste alla användare av sådana enheter ha ett Microsoft-konto.

-   För att krypteringen ska fungera måste enheten uppfylla Microsofts [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) -maskinvarucertifieringskrav.

-   När du framtvingar kryptering på en enhet är återställningsnyckeln enbart tillgänglig från användarens Microsoft-konto, som nås från användarens OneDrive-konto. Du kan inte återställa denna nyckel för en användares räkning.

## E-postinställningar

|Inställningsnamn|Information
|----------------|
|**Tillåt användare att hämta e-postbilagor**|Anger om bifogade filer i e-postmeddelanden ska kunna hämtas till enheten.|
|**E-postsynkroniseringsperiod**|Välj hur många dagar med mottagen e-post som ska synkroniseras till enheten.
|**Tillåt mobila enheter som inte fullt ut stöder inställningarna i Exchange ActiveSync att synkroniseras med Exchange**|Anger om Exchange-åtkomst ska tillåtas på enheter som inte har stöd för en eller flera Exchange ActiveSync-inställningar.

## Webbläsarinställningar

|Inställningsnamn|Information
|----------------|-
|**Tillåt webbläsare**|Anger om webbläsaren på enheten får användas.<br>(inte tillgängligt för Windows RT eller Windows Phone).

## Maskinvaruinställningar

|Inställningsnamn|Information
|----------------|
|**Tillåt kamera**|Anger om kameran på enheten får användas.<br>(inte tillgängligt för Windows RT eller Windows Phone).



### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO2-->


