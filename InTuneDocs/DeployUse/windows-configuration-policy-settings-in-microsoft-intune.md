---
# required metadata

title: Principinställningar för Windows | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Principinställningar för Windows i Microsoft Intune
Använd Microsoft Intunes **Allmänna konfigurationsprincip för Windows (Windows 8.1 och senare)** om du vill konfigurera inställningar för registrerade Windows 8.1- och Windows 8-enheter:

## Tillämplighetsinställningar

|Inställningsnamn|Information|
|----------------|----------------------------------|
|**Tillämpa alla konfigurationer på Windows 10**|Gör att inställningar i den här principen tillämpas på Windows 10-enheter utöver Windows 8- och Windows 8.1-enheter.|

## Säkerhetsinställningar

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Lösenordstyp krävs**|Anger vilken typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt.|Ja|Ja|
|**Krävd lösenordstyp – minsta antal teckenuppsättningar**|Det finns fyra teckenuppsättningar: gemena bokstäver, versala bokstäver, siffror och symboler. Den här inställningen anger hur många olika teckenuppsättningar som lösenordet måste innehålla. För iOS-enheter anger inställningen i stället antalet symboltecken som lösenordet måste innehålla.|Ja|Ja|
|**Minsta längd på lösenord**<sup>1</sup>|Konfigurerar den minsta tillåtna längden (i antal tecken) för lösenordet på enheter.|Ja|Ja|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Rensar enheten om inloggningen misslyckas angivet antal gånger.|Ja|Ja|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Välj hur många minuter som en enhet måste vara inaktiv innan ett lösenord krävs för att låsa upp den.| Ja|Ja|
|**Lösenordets giltighetstid (i dagar)**|Anger antalet dagar innan lösenordet måste ändras.|Ja|Ja|
|**Kom ihåg tidigare lösenord**|Anger om användaren kan konfigurera tidigare använda lösenord.|Ja|Ja|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Anger antalet tidigare använda lösenord som enheten sparar.|Ja|Ja|
|**Tillåt bildlösenord och PIN**|Tillåter användning av ett bildlösenord och en PIN-kod på enheten. Med ett bildlösenord kan användaren logga in med gester på en bild. Med en PIN-kod kan användaren snabbt logga in med en 4-siffrig kod.|Ja|Ja|
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
|**Kräver brandvägg för nätverk**|Kräv att Windows-brandväggen är aktiverad.|Ja|Nej|
|**Aktivera SmartScreen**|Kräv användning av Windows SmartScreen på enheter.|Ja|Nej|

## Systeminställningar

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Kräver automatiska uppdateringar**|Aktivera inställningen för automatiska uppdateringar på enheter.|Ja|Nej|
|**Kräver automatiska uppdateringar – Minimumklassificering för uppdateringar som ska installeras automatiskt**|Välj den klassificering av uppdateringar som ska installeras automatiskt:<br /><br />-   **Viktiga** – Installerar alla uppdateringar som klassificeras som viktiga.<br />-   **Rekommenderade** – Installerar alla uppdateringar som klassificeras som viktiga eller rekommenderade.|Ja|Nej|
|**User Account Control**|Kräv användning av UAC (User Account Control) på enheter.|Ja|Nej|
|**Tillåt sändning av diagnostikdata**|Tillåt att enheten skickar diagnostikinformation till Microsoft.|Ja|Nej|


## Molninställningar – dokument och data

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**URL till arbetsmappar**|Ställer in arbetsmappens URL så att dokument kan synkroniseras mellan enheter|Ja|Nej|

## E-postinställningar

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Gör Microsoft-kontot valfritt i Windows Mail-programmet**|Tillåter åtkomst till Windows Mail utan något Microsoft-konto.|Ja|Nej|

## Programinställningar - webbläsare

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Tillåt autofyll**|Användaren kan ändra inställningar för Komplettera automatiskt i webbläsaren.|Ja|Nej|
|**Tillåt blockering av popup-fönster**|Aktiverar eller inaktiverar webbläsarens blockering av popup-fönster.|Ja|Nej|
|**Tillåt insticksprogram**|Användaren kan lägga till plugin-program i Internet Explorer.|Ja|Nej|
|**Tillåt active scripting**|Webbläsaren kan köra skript, till exempel ActiveX-skript.|Ja|Nej|
|**Tillåt bedrägerivarning**|Aktivera eller inaktivera varningar för potentiella bedrägliga webbplatser.|Ja|Nej|
|**Tillåt intranätsplats för enstaka ord**|Tillåter användningen av ett enstaka ord för att dirigera Internet Explorer till en webbplats, t.ex. Bing.|Ja|Nej|
|**Tillåt automatisk identifiering av intranätsnätverk**|Hjälper till att konfigurera säkerheten för intranätsplatser i Internet Explorer.|Ja|Nej|
|**Säkerhetsnivå för Internet**|Ange säkerhetsnivån i Internet Explorer för webbplatser på Internet.|Ja|Nej|
|**Säkerhetsnivå för intranät**|Ange säkerhetsnivån i Internet Explorer för intranätsplatser.|Ja|Nej|
|**Säkerhetsnivå för betrodda platser**|Konfigurera säkerhetsnivån för zonen Betrodda platser.|Ja|Nej|
|**Säkerhetsnivå för ej betrodda platser**|Konfigurera säkerhetsnivån för zonen Ej betrodda platser.|Ja|Nej|
|**Skicka Spåra inte-rubrik**|Skicka ett Do Not Track-huvud till besökta webbplatser i Internet Explorer.|Ja|Nej|
|**Tillåt Företagsläge-menyåtkomst**|Låter användaren komma åt menyalternativen för företagsläge från Internet Explorer.<br>Om du väljer det här alternativet kan du även ange en **plats för loggningsrapport** som innehåller en URL till en rapport som visar webbplatser som användarna har aktiverat åtkomst till företagsläge för.|Ja|Nej|
|**Listplats för Företagsläge-webbplats**|Ange platsen där listan med webbplatser finns, som ska använda Enterprise-läget när det är aktivt.|Ja|Nej|

## Enhetskapacitetsinställningar - mobil

|Inställningsnamn|Information|Windows 8.1 och Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Tillåt dataroaming**|Tillåt datanätverksväxling när enheten använder ett mobilnät.|Ja|Nej|



### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO2-->


