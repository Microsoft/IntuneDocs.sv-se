---
title: Principinställningar för Windows
description: Använd Intunes allmänna konfigurationsprincip för Windows (Windows 8.1 och senare) om du vill konfigurera inställningar för registrerade Windows 8.1- och Windows 8-enheter.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ccd5bd201de59537dbf99ea9e19d84dbf80c1a20
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="windows-policy-settings-in-microsoft-intune"></a>Principinställningar för Windows i Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Använd Microsoft Intunes **allmänna konfigurationsprincip för Windows (Windows 8.1 och senare)** om du vill konfigurera följande inställningar för registrerade Windows 8-, Windows 8.1-och Windows RT 8.1-enheter:

## <a name="applicability-settings"></a>Tillämplighetsinställningar

|Inställningsnamn|Information|
|----------------|----------------------------------|
|**Tillämpa alla konfigurationer på Windows 10**|Gör att inställningar i den här principen tillämpas på Windows 10-enheter utöver Windows 8- och Windows 8.1-enheter.|

## <a name="security-settings"></a>Säkerhetsinställningar

|Inställningsnamn|Information|
|----------------|------|
|**Lösenordstyp krävs**|Anger vilken typ av lösenord som krävs, t.ex. enbart alfanumeriskt eller numeriskt.|
|**Krävd lösenordstyp – minsta antal teckenuppsättningar**|Anger hur många olika teckenuppsättningar som lösenordet måste innehålla. Det finns fyra teckenuppsättningar: gemener, versaler, siffror och symboler. För iOS-enheter specificerar den här inställningen i stället det antal symboler som måste inkluderas i lösenordet.|
|**Minsta längd på lösenord**|Konfigurerar den minsta tillåtna längden (i antal tecken) för lösenordet.|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Rensar enheten efter så här många misslyckade inloggningsförsök.|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Anger antalet minuter en enhet måste vara inaktiv innan det krävs ett lösenord för att låsa upp den.|
|**Lösenordets giltighetstid (i dagar)**|Anger antalet dagar innan lösenordet måste ändras.|
|**Kom ihåg tidigare lösenord**|Anger om användaren kan konfigurera tidigare använda lösenord.|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Anger antalet tidigare använda lösenord som enheten sparar.|
|**Tillåt bildlösenord och PIN**|Gör att det går att använda ett bildlösenord och en PIN-kod. Med ett bildlösenord kan användaren logga in med gester på en bild. Med en PIN-kod kan användaren snabbt logga in med en fyrsiffrig kod.|

## <a name="encryption-settings"></a>Krypteringsinställningar

|                           Inställningsnamn                           |                     Information                      |
|------------------------------------------------------------------|--------------------------------------------------|
| <strong>Kräv kryptering på den mobila enheten</strong><sup>1</sup> | Kräver att filer på enheten krypteras. |

<sup>1</sup> Ytterligare information för enheter som kör Windows 8.1

-   Om du vill framtvinga kryptering på enheter som kör Windows 8.1 måste du installera [December 2014 MDM-klientuppdateringen för Windows](http://support.microsoft.com/kb/3013816) på varje enhet.

-   Om du aktiverar den här inställningen för Windows 8.1-enheter måste alla användare av sådana enheter ha ett Microsoft-konto.

-   För att krypteringen ska fungera måste enheten uppfylla Microsofts [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) -maskinvarucertifieringskrav.

-   När du framtvingar kryptering på en enhet är återställningsnyckeln enbart tillgänglig från användarens Microsoft-konto, som nås från användarens OneDrive-konto. Du kan inte återställa denna nyckel för en användares räkning.

## <a name="malware-settings"></a>Inställningar för skadlig programvara

|Inställningsnamn|Information|
|----------------|-----|
|**Kräv nätverksbrandvägg**|Kräver att Windows-brandväggen är aktiverad.|
|**Aktivera SmartScreen**|Kräver användning av Windows SmartScreen.|

## <a name="system-settings"></a>Systeminställningar

|Inställningsnamn|Information|
|----------------|-------|
|**Kräv automatiska uppdateringar**|Aktiverar inställningen för automatiska uppdateringar på enheter.|
|**Kräv automatiska uppdateringar – Minsta nödvändiga klassificering för uppdateringar som ska installeras automatiskt**|Väljer den klassificering av uppdateringar som ska installeras automatiskt:<br /><br />-   **Viktiga** – Installerar alla uppdateringar som klassificeras som viktiga.<br />-   **Rekommenderade** – Installerar alla uppdateringar som klassificeras som viktiga eller rekommenderade.|
|**User Account Control**|Kräver användning av UAC (User Account Control) på enheter.|
|**Tillåt sändning av diagnostikdata**|Gör att enheten skickar diagnostikinformation till Microsoft.|


## <a name="cloud-settings--documents-and-data"></a>Molninställningar – dokument och data

|Inställningsnamn|Information|
|----------------|------|
|**URL till arbetsmappar**|Ställer in arbetsmappens URL så att dokument kan synkroniseras mellan enheter.|

## <a name="email-settings"></a>E-postinställningar

|Inställningsnamn|Information|
|----------------|-----|
|**Gör Microsoft-kontot valfritt i Windows Mail-programmet**|Tillåter åtkomst till Windows Mail utan något Microsoft-konto.|

## <a name="application-settings---browser"></a>Programinställningar - webbläsare

|Inställningsnamn|Information|
|----------------|-----|
|**Tillåt autofyll**|Gör att användarna kan ändra inställningarna för Komplettera automatiskt i webbläsaren.|
|**Tillåt blockering av popup-fönster**|Aktiverar eller inaktiverar webbläsarens blockering av popup-fönster.|
|**Tillåt insticksprogram**|Gör att användarna kan lägga till plugin-program i Internet Explorer.|
|**Tillåt Active scripting**|Webbläsaren kan köra skript, till exempel ActiveX-skript.|
|**Tillåt bedrägerivarning**|Aktiverar eller inaktiverar varningar för webbplatser som kan vara bedrägliga.|
|**Tillåt intranätplats för enstaka ord**|Gör att det går att använda ett enstaka ord för att dirigera Internet Explorer till en webbplats, t.ex. Bing.|
|**Tillåt automatisk identifiering av intranätsnätverk**|Hjälper till att konfigurera säkerheten för intranätsplatser i Internet Explorer.|
|**Säkerhetsnivå för Internet**|Anger säkerhetsnivån i Internet Explorer för webbplatser på Internet.|
|**Säkerhetsnivå för intranät**|Anger säkerhetsnivån i Internet Explorer för webbplatser på Internet.|
|**Säkerhetsnivå för betrodda platser**|Konfigurerar säkerhetsnivån för zonen Betrodda platser.|
|**Säkerhetsnivå för ej betrodda platser**|Konfigurerar säkerhetsnivån för zonen Ej betrodda platser.|
|**Skicka Do Not Track-huvud**|Skickar ett Do Not Track-huvud till besökta webbplatser i Internet Explorer.|
|**Tillåt menyåtkomst till företagsläge**|Låter användaren komma åt menyalternativen för företagsläge från Internet Explorer.<br>Om du väljer den här inställningen kan du även ange en **plats för loggningsrapport** som innehåller en URL till en rapport som visar webbplatser som användarna har aktiverat åtkomst till företagsläge för.|
|**Listplats för Företagsläge-webbplats**|Anger platsen där listan med webbplatser finns, som ska använda företagsläget när det är aktivt.|

## <a name="device-capabilities-settings---cellular"></a>Enhetskapacitetsinställningar - mobil

|Inställningsnamn|Information|
|----------------|----|
|**Tillåt datanätverksväxling**|Gör att det går att använda dataroaming när enheten är i ett mobilnät.|



### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
