---
title: "Säkerhetsprincipinställningar för mobila enheter"
description: "Använd Intune om du vill konfigurera ett flertal inställningar som du kan distribuera till hanterade enheter i organisationen."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 34da6fb95a6a2b292f8f2e1d787bef179fe2301b
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="mobile-device-security-policy-settings-in-microsoft-intune"></a>Säkerhetsprincipinställningar för mobila enheter i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

> [!IMPORTANT]
> I Microsoft Intune finns nu separata konfigurationsprinciper för varje enhetsplattform. Dessa principer innehåller de mest aktuella inställningarna som du kan använda. Du kan fortsätta att använda den mobila enhetens säkerhetsprincip. Alla befintliga distributioner kommer att fungera. Du bör planera att migrera till de nya konfigurationsprinciperna så snart som möjligt eftersom den mobila enhetens säkerhetsprincip kommer att tas bort i framtiden.

Du kan använda säkerhetsprinciper för mobila enheter i Intune om du vill konfigurera ett flertal inställningar som du kan distribuera till hanterade enheter i organisationen. De här inställningarna används för att kontrollera funktioner och säkerheten på dina enheter.

Du kan skapa och distribuera säkerhetsprinciper för mobila enheter för följande enhetstyper:

-   Windows RT 8.1 och registrerade Windows 8.1-enheter

-   Windows RT

-   Windows Phone 8 och Windows Phone 8.1

-   iOS

-   Android och Samsung KNOX Standard

> [!NOTE]
> Vissa inställningar gäller inte för vissa enheter. En fullständig lista över inställningar som du kan konfigurera finns i tabellen nedan.
> Från oktober 2016 upphör Microsoft Intunes stöd för Windows 8-företagsportalapparna. Microsoft Intunes stöd för Windows Phone 8- och WinRT-plattformarna upphör också. Det betyder att du inte kommer att kunna registrera eller uppdatera Windows Phone 8- eller WinRT-enheter. Men du kan fortsätta att hantera Windows Phone 8-, WinRT- och Windows 8-enheter som redan har registrerats. Uppdatera enheter med Windows Phone 8 och Windows 8 till Windows Phone 8.1 respektive Windows 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1. På så sätt kan du fortsätta att distribuera appar till dessa enheter utan avbrott.

## <a name="security-settings"></a>Säkerhetsinställningar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Nej|Nej|Ja|Ja|Ja|
|**Lösenordstyp krävs**<br /><br />Den här inställningen anger vilken typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt.|Ja|Ja|Ja|Ja|Nej|
|**Krävd lösenordstyp – minsta antal teckenuppsättningar**<br /><br />Det finns fyra teckenuppsättningar: gemener, versaler, siffror och symboler. Den här inställningen anger hur många olika teckenuppsättningar som lösenordet måste innehålla. För iOS-enheter specificerar detta dock det antal symboltecken som måste inkluderas i lösenordet.|Ja|Ja|Ja|Ja|Nej|
|**Minsta längd på lösenord**|Ja|Ja|Ja|Ja|Ja|
|**Tillåt enkla lösenord**<br /><br />Exempel på enkla lösenord är "0000" och "1234".|Nej|Nej|Ja|Ja|Nej|
|**Antal tillåtna, upprepade felinloggningar innan enheten rensas**|Ja|Ja|Ja|Ja|Ja|
|**Minuter av inaktivitet innan skärmen stängs av**<sup>1</sup>|Ja|Ja|Ja|Ja|Ja|
|**Lösenordets giltighetstid (i dagar)**|Ja|Ja|Ja|Ja|Ja|
|**Kom ihåg tidigare lösenord**|Ja|Ja|Ja|Ja|Ja|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Ja|Ja|Ja|Ja|Ja|
|**Lösenordskvalitet**|Nej|Nej|Nej|Nej|Ja|
|**Tillåt bildlösenord och PIN**|Ja|Ja|Nej|Nej|Nej|
|**Antal minuters inaktivitet innan lösenord krävs**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt fingeravtrycksupplåsning**|Nej|Nej|Nej|iOS 7 och senare|Nej|
<sup>1</sup> När du konfigurerar inställningarna **Minuter av inaktivitet innan skärmen stängs av** och **Minuter av inaktivitet innan lösenord måste anges** för iOS-enheter tillämpas de i följd. Om du t.ex. ställer in värdet för båda inställningarna till **5** minuter så stängs skärmen av automatiskt efter 5 minuter, och enheten låses efter ytterligare 5 minuter. Om användaren däremot stänger av skärmen manuellt så tillämpas den andra inställningen omedelbart. Efter det att användaren i det här exemplet har stängt av skärmen låses enheten 5 minuter senare.

Om du distribuerar en princip för lösenordslängd för enheter som kör Windows RT tvingas användarna att återställa sina lösenord, även om deras aktuella lösenord uppfyller principkraven.

## <a name="encryption-settings"></a>Krypteringsinställningar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kräv kryptering på den mobila enheten**<sup>1</sup><br /><br />För Windows Phone 8-enheter måst du ställa in denna på **Ja**.<br /><br />Om du vill möjliggöra kryptering på iOS-enheter måste du aktivera inställningen **Kräv lösenord för att låsa upp mobila enheter**.|Ja|Nej|Ja|Nej|Ja|
|**Kräv kryptering på minneskort**<br /><br />Den här inställningen gäller enheter som även hanteras av Exchange ActiveSync.|saknas|saknas|saknas <br />Appar och associerade data krypteras automatiskt.|saknas|Ja|
<sup>1</sup> Här finns ytterligare information för enheter som kör Windows 8.1:

-   Om du vill framtvinga kryptering på enheter som kör Windows 8.1 måste du installera [December 2014 MDM-klientuppdateringen för Windows](http://support.microsoft.com/kb/3013816) på varje enhet.

-   Om du aktiverar den här inställningen för Windows 8.1-enheter måste alla användare av sådana enheter ha ett Microsoft-konto.

-   För att krypteringen ska fungera måste enheten uppfylla Microsofts [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) -maskinvarucertifieringskrav.

-   När du framtvingar kryptering på en enhet är återställningsnyckeln enbart tillgänglig från användarens Microsoft-konto, som nås från användarens OneDrive-konto. Du kan inte återställa denna nyckel för en användares räkning.

## <a name="malware-settings"></a>Inställningar för skadlig programvara

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kräv nätverksbrandvägg**|Ja|Nej|Nej|Nej|Nej|
|**Aktivera SmartScreen**|Ja|Nej|Nej|Nej|Nej|

## <a name="system-settings"></a>Systeminställningar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kräv automatiska uppdateringar**|Ja|Nej|Nej|Nej|Nej|
|**Kräv automatiska uppdateringar – Minsta nödvändiga klassificering för uppdateringar som ska installeras automatiskt**<br /><br />Välj den klassificering av uppdateringar som ska installeras automatiskt:<br /><br />- **Viktigt!** Installerar alla uppdateringar som klassificeras som viktiga.<br /><br />- **Rekommenderade**. Installerar alla uppdateringar som klassificeras som viktiga eller rekommenderade.|Ja|Nej|Nej|Nej|Nej|
|**Tillåt skärmbild**|Nej|Nej|Endast Windows Phone 8.1|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt kontrollcenter på låsskärm**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**Tillåt notisvy på låsskärm**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**Tillåt dagsvy på låsskärm**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**User Account Control**|Ja|Nej|Nej|Nej|Nej|
|**Tillåt sändning av diagnostikdata**|Ja|Nej|Endast Windows Phone 8.1|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt ej betrodda TLS-certifikat**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt personlig plånboksprogramvara när låst**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt fabriksåterställning**|Nej|Nej|Nej|Nej|Ja (endast Samsung KNOX Standard)|


## <a name="cloud-settings--documents-and-data"></a>Molninställningar – dokument och data

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt säkerhetskopiering till iCloud**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt dokumentsynkronisering till iCloud**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt bildströmssynkronisering till iCloud**|Nej|Nej|Nej|Ja|Nej|
|**Kräv krypterad säkerhetskopiering**|Nej|Nej|Nej|Ja|Nej|
|**URL till arbetsmappar**<br /><br />Den här inställningen anger arbetsmappens URL så att dokument kan synkroniseras mellan enheter.|Ja|Nej|Nej|Nej|Nej|
|**Tillåt Google-säkerhetskopiering**|Nej|Nej|Nej|Nej|Ja (endast Samsung KNOX Standard)|

## <a name="cloud-settings--accounts-and-synchronization"></a>Molninställningar – konton och synkronisering

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt Microsoft-konto**|Nej|Nej|Endast Windows Phone 8.1|Nej|Nej|
|**Tillåt autosynkronisering av Google-konto**|Nej|Nej|Nej|Nej|Ja (endast Samsung KNOX Standard)|

## <a name="email-settings"></a>E-postinställningar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt att användare hämtar bifogade filer i e-post**<sup>1</sup>|saknas|saknas|saknas|saknas|saknas|
|**E-postsynkroniseringsperiod** <br /><br />Den här inställningen gäller enheter som även hanteras av Exchange ActiveSync.|saknas|saknas|saknas|saknas|saknas|
|**Tillåt att mobilenheter som inte har fullständigt stöd för dessa inställningar synkroniseras med Exchange (Exchange ActiveSync)** <br /><br />Den här inställningen gäller enheter som även hanteras av Exchange ActiveSync.|saknas|saknas|saknas|saknas|saknas|
|**Gör Microsoft-kontot valfritt i Windows Mail-programmet**|Ja|Nej|Nej|Nej|Nej|
|**Tillåt anpassade e-postkonton**|Nej|Nej|Endast Windows Phone 8.1|Nej|Nej|

## <a name="application-settings---browser"></a>Programinställningar - webbläsare

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt webbläsare**|Nej|Nej|Endast Windows Phone 8.1|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt autofyll**|Ja|Nej|Nej|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt blockering av popup-fönster**|Ja|Nej|Nej|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt cookies**|Nej|Nej|Nej|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt insticksprogram**|Ja|Nej|Nej|Nej|Nej|
|**Tillåt Active scripting**|Ja|Nej|Nej|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt bedrägerivarning**|Ja|Nej|Nej|Ja|Nej|
|**Tillåt intranätplats för enstaka ord**<br /><br />(Med den här inställningen tillåts användning av ett enstaka ord för att dirigera Internet Explorer till en webbplats, t.ex. Bing.)|Ja|Nej|Nej|Nej|Nej|
|**Tillåt automatisk identifiering av intranätsnätverk**|Ja|Nej|Nej|Nej|Nej|
|**Säkerhetsnivå för Internet**|Ja|Nej|Nej|Nej|Nej|
|**Säkerhetsnivå för intranät**|Ja|Nej|Nej|Nej|Nej|
|**Säkerhetsnivå för betrodda platser**|Ja|Nej|Nej|Nej|Nej|
|**Säkerhetsnivå för ej betrodda platser**|Ja|Nej|Nej|Nej|Nej|
|**Skicka Do Not Track-huvud**|Ja|Nej|Nej|Nej|Nej|
|**Tillåt menyåtkomst till företagsläge**|Ja|Nej|Nej|Nej|Nej|
|**Listplats för Företagsläge-webbplats**|Ja|Nej|Nej|Nej|Nej|

## <a name="application-settings---apps"></a>Programinställningar - appar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt appbutik**|Nej|Nej|Endast Windows Phone 8.1|Ja|Ja (endast Samsung KNOX Standard)|
|**Kräv lösenord för åtkomst till appbutik**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt köp via app**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt hanterade dokument i andra ohanterade appar**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**Tillåt ohanterade dokument i andra hanterade appar**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**Tillåt videokonferens**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt innehåll för vuxna i mediebutik**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt appinstallation**|Nej|Nej|Nej|iOS 6 och senare|Nej|

## <a name="application-settings---gaming"></a>Programinställningar - spel

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt Game Center-vänner**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt spel för flera personer**|Nej|Nej|Nej|Ja|Nej|

## <a name="device-capabilities-settings---hardware"></a>Enhetskapacitetsinställningar - maskinvara

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt kamera**|Nej|Nej|Endast Windows Phone 8.1|Ja|Ja|
|**Tillåt flyttbara lagringsmedier**|Nej|Nej|Ja|Nej|Ja (endast Samsung KNOX Standard)|
|**Tillåt Wi-Fi**|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (endast Samsung KNOX Standard)|
|**Tillåt trådlös Internetdelning**|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (endast Samsung KNOX Standard)|
|**Tillåt automatisk anslutning till kostnadsfria trådlösa surfzoner**|Nej|Nej|Endast Windows Phone 8.1|Nej|Nej|
|**Tillåt rapportering om trådlösa surfzoner**<br /><br />Den här inställningen skickar information om Wi-Fi-anslutningar för att lättare upptäcka närliggande anslutningar.|Nej|Nej|Endast Windows Phone 8.1|Nej|Nej|
|**Tillåt geolokalisering**<br /><br />Med den här inställningen tillåts att enheten använder platsinformation.|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (endast Samsung KNOX Standard)|
|**Tillåt NFC**<br /><br />Med den här inställningen tillåts åtgärder som använder närfältskommunikation.|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (endast Samsung KNOX Standard)|
|**Tillåt Bluetooth**|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (endast Samsung KNOX Standard)|
|**Tillåt avstängning**<br>Om du inaktiverar den här inställningen så fungerar inte inställningen **Antal tillåtna upprepade felinloggningar innan enheten rensas** för Samsung KNOX Standard-enheter.|Nej|Nej|Nej|Nej|Ja (endast Samsung KNOX Standard)|

## <a name="device-capabilities-settings---cellular"></a>Enhetskapacitetsinställningar - mobil

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt röstnätverksväxling**|Nej|Nej|Nej|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt datanätverksväxling**|Ja|Nej|Nej|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt automatisk synkronisering under nätverksväxling**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt SMS-/MMS-meddelanden**|Nej|Nej|Nej|Nej|Ja (endast Samsung KNOX Standard)|

## <a name="device-capabilities-settings---features"></a>Enhetskapacitetsinställningar - funktioner

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt röstassistent**|Nej|Nej|Nej|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt röstassistent när enheten är låst**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt röstsamtal**|Nej|Nej|Nej|Ja|Ja (endast Samsung KNOX Standard)|
|**Tillåt kopiera och klistra in**|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (endast Samsung KNOX Standard)|
|**Tillåt delning av urklipp mellan program**|Nej|Nej|Nej|Nej|Ja (endast Samsung KNOX Standard)|
|**Tillåt YouTube**|Nej|Nej|Nej|Nej|Ja (endast Samsung KNOX Standard)|

### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
