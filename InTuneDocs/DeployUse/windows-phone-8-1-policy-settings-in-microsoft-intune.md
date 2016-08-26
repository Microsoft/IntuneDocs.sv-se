---
title: "Principinställningar för Windows Phone 8.1 | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 83f7469c-272e-43f2-8139-b0d7bc34f43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a280fcbecf82e6ff27e40d2d53331b3988953ff7
ms.openlocfilehash: fe685da41bb5379526bdc28c2f9cceb6b7800703


---

# Principinställningar för Windows Phone 8.1 i Microsoft Intune

## Allmänna konfigurationsinställningar

Använd Microsoft Intunes **Allmänna konfigurationsprincip för Windows Phone (Windows Phone 8.1 och senare)** om du vill konfigurera följande inställningar för Windows Phone 8.1-enheter:

-   **Säkerhetsinställningar för mobil enhet** – Välj i en lista fördefinierade inställningar med vilka du kan reglera många av enhetens egenskaper och funktioner.

-   **Kompatibla och inkompatibla appar** – Ange en lista över appar i företaget som är kompatibla eller inkompatibla. Windows Phone-enheter kan blockera eller tillåta installation av dessa appar.

### Tillämplighetsinställningar

|Inställningsnamn|Information|
|----------------|----------------------------------|
|**Tillämpa alla konfigurationer på Windows 10**|Gör inställningar i den här principen ska tillämpas på Windows 10-enheter utöver Windows 8.1-enheter.|

### Inställningar för lösenord

|Inställningsnamn|Information|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Anger om användarna måste ange ett lösenord för att få åtkomst till sina enheter.|Ja|Ja|
|**Lösenordstyp krävs**|Anger vilken typ av lösenord som krävs, t.ex. enbart numeriskt eller alfanumeriskt.|Ja|Ja|
|**Krävd lösenordstyp – minsta antal teckenuppsättningar**|Det finns fyra teckenuppsättningar: gemena bokstäver, versala bokstäver, siffror och symboler. Den här inställningen anger hur många olika teckenuppsättningar som måste inkluderas i lösenordet. För iOS-enheter specificerar detta dock det antal symboltecken som måste inkluderas i lösenordet.|Ja|Ja|
|**Minsta längd på lösenord**|Anger det minsta antalet tecken som lösenordet måste innehålla.|Ja|Ja|
|**Tillåt enkla lösenord**|Exempel på enkla lösernord är "0000" och "1234"|Ja|Ja|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Anger hur många gånger ett felaktigt lösenord kan registreras innan enheten rensas.|Ja|Ja|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Anger hur lång tid en enhet måste vara inaktiv innan skärmen låses automatiskt.|Ja|Ja|
|**Lösenordets giltighetstid (i dagar)**|Anger antalet dagar innan lösenordet måste ändras.|Ja|Ja|
|**Kom ihåg tidigare lösenord**|Anger om tidigare använda lösenord ska sparas så att användaren inte kan använda dem igen.|Ja|Ja|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Anger hur många tidigare använda lösenord som ska lagras.|Ja|Ja|

### Krypteringsinställningar

|Inställningsnamn|Information|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Filkryptering på mobil enhet**|Kräver att data på mobila enheter som stöds krypteras.<br>För Windows Phone 8-enheter måst du ställa in denna på **Ja**.|Ja|Ja|

### Systeminställningar

|Inställningsnamn|Information|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Tillåt skärmbild**|Låter användaren fånga innehållet på skärmen som en bildfil.|Nej|Ja|
|**Tillåt sändning av diagnostikdata**|Tillåter att enheten skickar diagnostikinformation till Microsoft.|Nej|Ja|

### Molninställningar – konton och synkronisering

|Inställningsnamn|Information|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Tillåt Microsoft-konto**|Tillåter att ett Microsoft-konto kopplas till enheten.|Nej|Ja|

### E-postinställningar

|Inställningsnamn|Information|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Tillåt anpassade e-postkonton**|Tillåt att enheten ansluter till andra e-postkonton än Microsoft-e-postkonton.|Nej|Ja|

### Programinställningar - webbläsare

|Inställningsnamn|Information|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Tillåt webbläsare**|Tillåter eller blockerar den inbyggda webbläsaren på enheter.|Nej|Ja|

### Programinställningar - appar

|Inställningsnamn|Information|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Tillåt appbutik**|Tillåter att användarna ansluter till appbutiken från enheten.|Nej|Ja|

### Enhetskapacitetsinställningar - maskinvara

|Inställningsnamn|Information|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Tillåt kamera**|Tillåt eller blockera enhetens kamera.|Nej|Ja|
|**Tillåt flyttbara lagringsenheter**|Tillåter att enheten använder flyttbara lagringsenheter, till exempel SD-kort.|Ja|Ja|
|**Tillåt Wi-Fi**|Aktiverar eller inaktiverar Wi-Fi-funktioner på enheten.|Nej|Ja|
|**Tillåt Wi-Fi -delning**|Tillåt användning av Wi-Fi-delning på enheten.|Nej|Ja
|**Tillåt automatisk anslutning till kostnadsfria, trådlösa surfpunkter**|Tillåt att enheten ansluter automatiskt till kostnadsfria trådlösa surfzoner och att den automatiskt godkänner användningsvillkoren.|Nej|Ja|
|**Tillåt rapportering av trådlösa surfpunkter**|Skicka information om Wi-Fi-anslutningar för att lättare upptäcka närliggande anslutningar.|Nej|Ja|
|**Tillåt geolokalisering**|Tillåter att enheten använder platsinformation.|Nej|Ja|
|**Tillåt NFC**|Tillåter åtgärder som använder närfältskommunikation.|Nej|Ja|
|**Tillåt Bluetooth**|Aktiverar eller inaktiverar Bluetooth-funktionen på enheten.|Nej|Ja|

### Enhetskapacitetsinställningar - funktioner

|Inställningsnamn|Information|Windows Phone 8|Windows Phone 8.1|
|----------------|-----------------------------------------|
|**Tillåt kopiera och klistra in**|Tillåt kopierings- och inklistringsfunktioner på enheter.|Nej|Ja|

### Inställningar för kompatibla och icke-kompatibla appar
I listan över **kompatibla och &amp;inkompatibla appar** skapar du en lista över kompatibla eller inkompatibla appar med hjälp av följande information:

> [!NOTE]
> En enda princip kan bara innehålla en lista över kompatibla eller en lista över inkompatibel appar. Du kan inte ange båda i samma princip.

|Inställningsnamn|Information|
|----------------|--------------------|
|**Blockera enheter från att öppna apparna i listan**|Visar en lista med de appar som inte hanteras av Intune och som användarna inte får installera och köra.|
|**Tillåt endast att enheter får installera apparna i listan**|Visar listan med de appar som användare tillåts att installera. Användarna kan inte installera några andra appar. Appar som hanteras av Intune tillåts automatiskt.|
|**Lägg till**|Lägger till en app i den markerade listan. Ange ett namn, eventuellt appens utgivare och webbadressen till appen i appbutiken. Mer hjälp finns i Så här anger du webbadresser till appbutiker senare i det här avsnittet.
|**Importera appar**|Importerar en lista med appar som du har angett i en fil med kommaseparerade värden. Använd format, appnamn, utgivare och app-URL i filen.|
|**Redigera**|Du kan redigera namn, utgivare och webbadress för den valda appen.|
|**Ta bort**|Tar bort den markerade appen från listan.|
> [!IMPORTANT]
> Om du skapar en lista över tillåtna appar för Windows Phone 8.1-enheter måste du lägga till företagsportalappen i listan, annars blockeras den.


### Referensinformation för kompatibla och icke-kompatibla appar

#### Så här anger du webbadresser till appbutiker
Om du vill specificera en app-URL i listan över kompatibla och ej kompatibla appar ska du använda följande format:

Gå till sidan [Windows Phone appar och spel](http://www.windowsphone.com/en-us/store/overview) och sök efter den app du vill använda.

Öppna appens sida och kopiera webbadressen till Urklipp. Nu kan du använda denna som webbadress, i listan över kompatibla eller inkompatibla appar.

**Exempel:** Sök i butiken efter Skype-appen. Webbadressen som du använder är **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.

## Anpassade principinställningar 
Använd Microsoft Intunes **anpassade konfigurationsprincip för Windows Phone** om du vill distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på **Windows Phone 8.1-enheter**. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Med den här funktionen kan du distribuera Windows Phone-inställningar som inte kan konfigureras med en allmän Intune-konfigurationsprincip. Information om vilka inställningar som du kan konfigurera med dessa principer finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Mer information om hur du skapar OMA-URI-inställningar för Windows Phone-enheter finns i [dokumentationen för Windows Phone 8.1 MDM-protokollet](http://technet.microsoft.com/library/dn499787.aspx).

### Allmänna inställningar

|Inställningsnamn|Information|
|----------------|--------------------|
|**Namn**|Ange ett unikt namn för principen som hjälper dig att identifiera den i Intune-konsolen.|
|**Beskrivning**|Ange en lämplig beskrivning av principen och annan information som gör det enkelt att hitta den.|

### OMA-URI-inställningar

Gå till avsnittet **OMA-URI-inställningar** och lägg till en inställning genom att klicka på **Lägg till**. Du kan också redigera och ta bort en befintlig inställning.

I dialogrutan **Lägg till eller redigera OMA-URI-inställning** anger du följande information:

|Inställningsnamn|Information|
    |--------|--------------------|
    |**Inställningsnamn**|Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.|
    |**Beskrivning av inställning**|Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.|
    |**Datatyp**|Ange den datumtyp med vilken du vill specificera den här OMA-URI-inställningen. Välj mellan:<br /><br />-   **Sträng**<br />-   **Sträng (XML)**<br />-   **Datum och tid**<br />-   **Heltal**<br />-   **Flyttal**<br />-   **Boolesk**|
    |**OMA-URI (skiftlägeskänslig)**|Ange den OMA-URI som du vill tillhandahålla en inställning för.|
    |**Värde**|Ange det värde som ska associeras med den OMA-URI som du tidigare angav.|

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


