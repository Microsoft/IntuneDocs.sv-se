---
title: "Principinställningar för Windows | Microsoft Intune"
description: "Använd Intunes allmänna konfigurationsprincip för Windows (Windows 8.1 och senare) om du vill konfigurera inställningar för registrerade Windows 8.1- och Windows 8-enheter."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7fdfe64a18fe359ee4b3b4507ef4108ad65ab573
ms.openlocfilehash: 3102e4637c61bbae002fb30947acd1f82204ac93


---

# Principinställningar för Windows i Microsoft Intune
Använd Microsoft Intunes **allmänna konfigurationsprincip för Windows (Windows 8.1 och senare)** om du vill konfigurera följande inställningar för registrerade Windows 8.1- och Windows 8-enheter:

## Tillämplighetsinställningar

|Inställningsnamn|Information|
|----------------|----------------------------------|
|**Tillämpa alla konfigurationer på Windows 10**|Gör att inställningar i den här principen tillämpas på Windows 10-enheter utöver Windows 8- och Windows 8.1-enheter.|

## Säkerhetsinställningar

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Lösenordstyp krävs**|Anger vilken typ av lösenord som krävs, t.ex. enbart alfanumeriskt eller numeriskt.|Ja|Ja|
|**Krävd lösenordstyp – minsta antal teckenuppsättningar**|Anger hur många olika teckenuppsättningar som lösenordet måste innehålla. Det finns fyra teckenuppsättningar: gemener, versaler, siffror och symboler. För iOS-enheter specificerar den här inställningen i stället det antal symboler som måste inkluderas i lösenordet.|Ja|Ja|
|**Minsta längd på lösenord**<sup>1</sup>|Konfigurerar den minsta tillåtna längden (i antal tecken) för lösenordet.|Ja|Ja|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Rensar enheten efter så här många misslyckade inloggningsförsök.|Ja|Ja|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Anger antalet minuter en enhet måste vara inaktiv innan det krävs ett lösenord för att låsa upp den.| Ja|Ja|
|**Lösenordets giltighetstid (i dagar)**|Anger antalet dagar innan lösenordet måste ändras.|Ja|Ja|
|**Kom ihåg tidigare lösenord**|Anger om användaren kan konfigurera tidigare använda lösenord.|Ja|Ja|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Anger antalet tidigare använda lösenord som enheten sparar.|Ja|Ja|
|**Tillåt bildlösenord och PIN**|Gör att det går att använda ett bildlösenord och en PIN-kod. Med ett bildlösenord kan användaren logga in med gester på en bild. Med en PIN-kod kan användaren snabbt logga in med en fyrsiffrig kod.|Ja|Ja|
<sup>1</sup> Om du distribuerar en princip för lösenordslängd för enheter som kör Windows RT tvingas användarna att återställa sina lösenord, även om deras aktuella lösenord uppfyller principkraven.

## Krypteringsinställningar

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Kräv kryptering på den mobila enheten**<sup>1</sup>|Kräver att filer på enheten krypteras.<br>För Windows Phone 8-enheter måst du ställa in denna på **Ja**.|Ja|Nej|
<sup>1</sup> Ytterligare information för enheter som kör Windows 8.1

-   Om du vill framtvinga kryptering på enheter som kör Windows 8.1 måste du installera [December 2014 MDM-klientuppdateringen för Windows](http://support.microsoft.com/kb/3013816) på varje enhet.

-   Om du aktiverar den här inställningen för Windows 8.1-enheter måste alla användare av sådana enheter ha ett Microsoft-konto.

-   För att krypteringen ska fungera måste enheten uppfylla Microsofts [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) -maskinvarucertifieringskrav.

-   När du framtvingar kryptering på en enhet är återställningsnyckeln enbart tillgänglig från användarens Microsoft-konto, som nås från användarens OneDrive-konto. Du kan inte återställa denna nyckel för en användares räkning.

## Inställningar för skadlig programvara

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Kräver brandvägg för nätverk**|Kräver att Windows-brandväggen är aktiverad.|Ja|Nej|
|**Aktivera SmartScreen**|Kräver användning av Windows SmartScreen.|Ja|Nej|

## Systeminställningar

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Kräver automatiska uppdateringar**|Aktiverar inställningen för automatiska uppdateringar på enheter.|Ja|Nej|
|**Kräver automatiska uppdateringar – Minimumklassificering för uppdateringar som ska installeras automatiskt**|Väljer den klassificering av uppdateringar som ska installeras automatiskt:<br /><br />-   **Viktiga** – Installerar alla uppdateringar som klassificeras som viktiga.<br />-   **Rekommenderade** – Installerar alla uppdateringar som klassificeras som viktiga eller rekommenderade.|Ja|Nej|
|**User Account Control**|Kräver användning av UAC (User Account Control) på enheter.|Ja|Nej|
|**Tillåt sändning av diagnostikdata**|Gör att enheten skickar diagnostikinformation till Microsoft.|Ja|Nej|


## Molninställningar – dokument och data

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**URL till arbetsmappar**|Ställer in arbetsmappens URL så att dokument kan synkroniseras mellan enheter.|Ja|Nej|

## E-postinställningar

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Gör Microsoft-kontot valfritt i Windows Mail-programmet**|Tillåter åtkomst till Windows Mail utan något Microsoft-konto.|Ja|Nej|

## Programinställningar - webbläsare

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Tillåt autofyll**|Gör att användarna kan ändra inställningarna för Komplettera automatiskt i webbläsaren.|Ja|Nej|
|**Tillåt blockering av popup-fönster**|Aktiverar eller inaktiverar webbläsarens blockering av popup-fönster.|Ja|Nej|
|**Tillåt insticksprogram**|Gör att användarna kan lägga till plugin-program i Internet Explorer.|Ja|Nej|
|**Tillåt active scripting**|Webbläsaren kan köra skript, till exempel ActiveX-skript.|Ja|Nej|
|**Tillåt bedrägerivarning**|Aktiverar eller inaktiverar varningar för webbplatser som kan vara bedrägliga.|Ja|Nej|
|**Tillåt intranätsplats för enstaka ord**|Gör att det går att använda ett enstaka ord för att dirigera Internet Explorer till en webbplats, t.ex. Bing.|Ja|Nej|
|**Tillåt automatisk identifiering av intranätsnätverk**|Hjälper till att konfigurera säkerheten för intranätsplatser i Internet Explorer.|Ja|Nej|
|**Säkerhetsnivå för Internet**|Anger säkerhetsnivån i Internet Explorer för webbplatser på Internet.|Ja|Nej|
|**Säkerhetsnivå för intranät**|Anger säkerhetsnivån i Internet Explorer för webbplatser på Internet.|Ja|Nej|
|**Säkerhetsnivå för betrodda platser**|Konfigurerar säkerhetsnivån för zonen Betrodda platser.|Ja|Nej|
|**Säkerhetsnivå för ej betrodda platser**|Konfigurerar säkerhetsnivån för zonen Ej betrodda platser.|Ja|Nej|
|**Skicka Spåra inte-rubrik**|Skickar ett Do Not Track-huvud till besökta webbplatser i Internet Explorer.|Ja|Nej|
|**Tillåt Företagsläge-menyåtkomst**|Låter användaren komma åt menyalternativen för företagsläge från Internet Explorer.<br>Om du väljer den här inställningen kan du även ange en **plats för loggningsrapport** som innehåller en URL till en rapport som visar webbplatser som användarna har aktiverat åtkomst till företagsläge för.|Ja|Nej|
|**Listplats för Företagsläge-webbplats**|Anger platsen där listan med webbplatser finns, som ska använda företagsläget när det är aktivt.|Ja|Nej|

## Enhetskapacitetsinställningar - mobil

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Tillåt dataroaming**|Gör att det går att använda dataroaming när enheten är i ett mobilnät.|Ja|Nej|



### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Aug16_HO3-->


