---
# required metadata

title: Säkerhetsprincipinställningar för mobila enheter i Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Säkerhetsprincipinställningar för mobila enheter i Microsoft Intune
> [!IMPORTANT]
> Microsoft Intune har nu separata konfigurationsprinciper för respektive enhetsplattform, och dessa principer innehåller de senaste uppdaterade inställningar som du kan använda. Du kan fortsätta att använda den mobila enhetens säkerhetsprincip och alla befintliga distributioner kommer att fungera. Du bör planera att migrera till de nya konfigurationaprinciperna så snart som möjligt eftersom den mobila enhetens säkerhetsprincip tas bort i framtiden.

Använd säkerhetsprinciper för mobila enheter i Intune om du vill konfigurera ett flertal inställningar som du kan distribuera till hanterade enheter i organisationen. De här inställningarna kan användas för att kontrollera funktioner och säkerheten på dina enheter.

Du kan skapa och distribuera säkerhetsprinciper för mobila enheter för följande enhetstyper:

-   Windows RT 8.1 och registrerade Windows 8.1-enheter

-   Windows RT

-   Windows Phone 8 och Windows Phone 8.1

-   iOS

-   Android och Samsung KNOX

> [!NOTE]
> Vissa inställningar gäller inte för vissa enheter. En fullständig lista över inställningar som du kan konfigurera finns i tabellen nedan.

## Säkerhetsinställningar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Nej|Nej|Ja|Ja|Ja|
|**Lösenordstyp krävs**<br /><br />(specificerar den typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt)|Ja|Ja|Ja|Ja|Nej|
|**Krävd lösenordstyp – minsta antal teckenuppsättningar**<br /><br />Det finns fyra teckenuppsättningar: gemena bokstäver, versala bokstäver, siffror och symboler. Den här inställningen anger hur många olika teckenuppsättningar som måste inkluderas i lösenordet. För iOS-enheter specificerar detta dock det antal symboltecken som måste inkluderas i lösenordet.|Ja|Ja|Ja|Ja|Nej|
|**Minsta längd på lösenord**|Ja|Ja|Ja|Ja|Ja|
|**Tillåt enkla lösenord**<br /><br />Exempel på enkla lösernord är "0000" och "1234"|Nej|Nej|Ja|Ja|Nej|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Ja|Ja|Ja|Ja|Ja|
|**Minuter av inaktivitet innan skärmen stängs av**<sup>1</sup>|Ja|Ja|Ja|Ja|Ja|
|**Lösenordets giltighetstid (i dagar)**|Ja|Ja|Ja|Ja|Ja|
|**Kom ihåg tidigare lösenord**|Ja|Ja|Ja|Ja|Ja|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Ja|Ja|Ja|Ja|Ja|
|**Lösenordskvalitet**|Nej|Nej|Nej|Nej|Ja|
|**Tillåt bildlösenord och PIN**|Ja|Ja|Nej|Nej|Nej|
|**Antal minuters inaktivitet innan lösenord krävs**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt fingeravtrycksupplåsning**|Nej|Nej|Nej|iOS 7 och senare|Nej|
När du konfigurerar inställningarna **Minuter av inaktivitet innan skärmen stängs av** och **Minuter av inaktivitet innan lösenord måste anges** för iOS-enheter tillämpas de i följd. Om du t.ex. ställer in värdet för båda inställningarna till **5** minuter så stängs skärmen av automatiskt efter 5 minuter, och enheten låses efter ytterligare 5 minuter. Om användaren däremot stänger av skärmen manuellt så tillämpas den andra inställningen omedelbart. Efter det att användaren i det här exemplet har stängt av skärmen låses enheten 5 minuter senare.

När du ställer in en princip för lösenordslängd för enheter som kör Windows RT tvingas användare att återställa sina lösenord, även om deras aktuella lösenord uppfyller principkraven.

## Krypteringsinställningar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kräv kryptering på den mobila enheten**<sup>1</sup><br /><br />För Windows Phone 8-enheter måste du ställa in denna på **Ja**.<br /><br />Om du vill möjliggöra kryptering på iOS-enheter måste du aktivera inställningen **Kräv lösenord för att låsa upp mobila enheter**.|Ja|Nej|Ja|Nej|Ja|
|**Kräv kryptering på minneskort**<br /><br />Gäller enheter som även hanteras av Exchange ActiveSync.|saknas|saknas|saknas (appar och associerade data krypteras automatiskt)|saknas|Ja|
Ytterligare information för enheter som kör Windows 8.1

-   Om du vill framtvinga kryptering på enheter som kör Windows 8.1 måste du installera [December 2014 MDM-klientuppdateringen för Windows](http://support.microsoft.com/kb/3013816) på varje enhet.

-   Om du aktiverar den här inställningen för Windows 8.1-enheter måste alla användare av sådana enheter ha ett Microsoft-konto.

-   För att krypteringen ska fungera måste enheten uppfylla Microsofts [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) -maskinvarucertifieringskrav.

-   När du framtvingar kryptering på en enhet är återställningsnyckeln enbart tillgänglig från användarens Microsoft-konto, som nås från användarens OneDrive-konto. Du kan inte återställa denna nyckel för en användares räkning.

## Inställningar för skadlig programvara

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kräver brandvägg för nätverk**|Ja|Nej|Nej|Nej|Nej|
|**Aktivera SmartScreen**|Ja|Nej|Nej|Nej|Nej|

## Systeminställningar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kräver automatiska uppdateringar**|Ja|Nej|Nej|Nej|Nej|
|**Kräver automatiska uppdateringar – Minimumklassificering för uppdateringar som ska installeras automatiskt**<br /><br />Välj den klassificering av uppdateringar som ska installeras automatiskt:<br /><br />**Viktiga** – Installerar alla uppdateringar som klassificeras som viktiga.<br /><br />**Rekommenderade** – Installerar alla uppdateringar som klassificeras som viktiga eller rekommenderade.|Ja|Nej|Nej|Nej|Nej|
|**Tillåt skärmbild**|Nej|Nej|Endast Windows Phone 8.1|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt Kontrollcenter på låsskärm**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**Tillåt notisvy på låsskärm**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**Tillåt dagsvy på låsskärm**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**User Account Control**|Ja|Nej|Nej|Nej|Nej|
|**Tillåt sändning av diagnostikdata**|Ja|Nej|Endast Windows Phone 8.1|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt ej betrodda TLS-certifikat**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt personlig plånboksprogramvara när låst**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt fabriksåterställning**|Nej|Nej|Nej|Nej|Ja (enbart Samsung KNOX)|


## Molninställningar – dokument och data

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt säkerhetskopiering till iCloud**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt dokumentsynkronisering till iCloud**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt bildströmssynkronisering till iCloud**|Nej|Nej|Nej|Ja|Nej|
|**Kräv krypterad säkerhetskopiering**|Nej|Nej|Nej|Ja|Nej|
|**URL till arbetsmappar**<br /><br />(ställer in arbetsmappens URL för att låta dokument synkroniseras mellan enheter)|Ja|Nej|Nej|Nej|Nej|
|**Tillåt Google säkerhetskopiering**|Nej|Nej|Nej|Nej|Ja (enbart Samsung KNOX)|

## Molninställningar – konton och synkronisering

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt Microsoft-konto**|Nej|Nej|Endast Windows Phone 8.1|Nej|Nej|
|**Tillåt autosynkronisering av Google-konto**|Nej|Nej|Nej|Nej|Ja (enbart Samsung KNOX)|

## E-postinställningar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt att användare hämtar bifogade filer i e-post**<sup>1</sup>|saknas|saknas|saknas|saknas|saknas|
|**Synkroniseringsperiod för e-post** Gäller enheter som även hanteras av Exchange ActiveSync.|saknas|saknas|saknas|saknas|saknas|
|**Tillåt att mobila enheter som inte har fullständigt stöd för dessa inställningar synkroniseras med Exchange (Exchange ActiveSync)** Gäller enheter som även hanteras av Exchange ActiveSync.|saknas|saknas|saknas|saknas|saknas|
|**Gör Microsoft-kontot valfritt i Windows Mail-programmet**|Ja|Nej|Nej|Nej|Nej|
|**Tillåt anpassade e-postkonton**|Nej|Nej|Endast Windows Phone 8.1|Nej|Nej|

## Programinställningar - webbläsare

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt webbläsare**|Nej|Nej|Endast Windows Phone 8.1|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt autofyll**|Ja|Nej|Nej|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt blockering av popup-fönster**|Ja|Nej|Nej|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt cookies**|Nej|Nej|Nej|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt insticksprogram**|Ja|Nej|Nej|Nej|Nej|
|**Tillåt active scripting**|Ja|Nej|Nej|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt bedrägerivarning**|Ja|Nej|Nej|Ja|Nej|
|**Tillåt intranätsplats för enstaka ord**<br /><br />(tillåter användning av enstaka ord för att rikta Internet Explorer till en webbplats, t.ex. Bing)|Ja|Nej|Nej|Nej|Nej|
|**Tillåt automatisk identifiering av intranätsnätverk**|Ja|Nej|Nej|Nej|Nej|
|**Säkerhetsnivå för Internet**|Ja|Nej|Nej|Nej|Nej|
|**Säkerhetsnivå för intranät**|Ja|Nej|Nej|Nej|Nej|
|**Säkerhetsnivå för betrodda platser**|Ja|Nej|Nej|Nej|Nej|
|**Säkerhetsnivå för ej betrodda platser**|Ja|Nej|Nej|Nej|Nej|
|**Skicka Spåra inte-rubrik**|Ja|Nej|Nej|Nej|Nej|
|**Tillåt Företagsläge-menyåtkomst**|Ja|Nej|Nej|Nej|Nej|
|**Listplats för Företagsläge-webbplats**|Ja|Nej|Nej|Nej|Nej|

## Programinställningar - appar

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt appbutik**|Nej|Nej|Endast Windows Phone 8.1|Ja|Ja (enbart Samsung KNOX)|
|**Kräv ett lösenord om du vill komma åt programbutiken.**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt köp via app**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt hanterade dokument i andra ohanterade appar**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**Tillåt ohanterade dokument i andra hanterade appar**|Nej|Nej|Nej|iOS 7 och senare|Nej|
|**Tillåt videokonferens**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt innehåll för vuxna i mediebutik**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt programinstallationer**|Nej|Nej|Nej|iOS 6 och senare|Nej|

## Programinställningar - spel

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt Game Center-vänner**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt spel för flera personer**|Nej|Nej|Nej|Ja|Nej|

## Enhetskapacitetsinställningar - maskinvara

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt kamera**|Nej|Nej|Endast Windows Phone 8.1|Ja|Ja|
|**Tillåt flyttbara lagringsenheter**|Nej|Nej|Ja|Nej|Ja (enbart Samsung KNOX)|
|**Tillåt Wi-Fi**|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (enbart Samsung KNOX)|
|**Tillåt Wi-Fi -delning**|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (enbart Samsung KNOX)|
|**Tillåt automatisk anslutning till kostnadsfria, trådlösa surfpunkter**|Nej|Nej|Endast Windows Phone 8.1|Nej|Nej|
|**Tillåt rapportering av trådlösa surfpunkter**<br /><br />(skicka information om Wi-Fi-anslutningar för att lättare upptäcka närliggande anslutningar)|Nej|Nej|Endast Windows Phone 8.1|Nej|Nej|
|**Tillåt geolokalisering**<br /><br />(tillåter enheten att använda platsinformation)|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (enbart Samsung KNOX)|
|**Tillåt NFC**<br /><br />(tillåter åtgärder som använder närfältskommunikation)|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (enbart Samsung KNOX)|
|**Tillåt Bluetooth**|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (enbart Samsung KNOX)|
|**Tillåt kraftavstängning**<br>Om den är inaktiverad fungerar inte inställningen **Antal inloggningsförsök innan enheten rensas** för Samsung KNOX-enheter.|Nej|Nej|Nej|Nej|Ja (enbart Samsung KNOX)|

## Enhetskapacitetsinställningar - mobil

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt röstroaming**|Nej|Nej|Nej|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt dataroaming**|Ja|Nej|Nej|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt automatisk synkronisering vid roaming**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt SMS/MMS-meddelanden**|Nej|Nej|Nej|Nej|Ja (enbart Samsung KNOX)|

## Enhetskapacitetsinställningar - funktioner

|Inställningsnamn|Windows 8.1 och Windows RT 8.1|Windows RT|Windows Phone 8 och Windows Phone 8.1|iOS|Android och Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Tillåt röstassistent**|Nej|Nej|Nej|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt röstassistent när enheten är låst**|Nej|Nej|Nej|Ja|Nej|
|**Tillåt röstsamtal**|Nej|Nej|Nej|Ja|Ja (enbart Samsung KNOX)|
|**Tillåt kopiera och klistra in**|Nej|Nej|Endast Windows Phone 8.1|Nej|Ja (enbart Samsung KNOX)|
|**Tillåt delning av urklipp mellan program**|Nej|Nej|Nej|Nej|Ja (enbart Samsung KNOX)|
|**Tillåt YouTube**|Nej|Nej|Nej|Nej|Ja (enbart Samsung KNOX)|

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


