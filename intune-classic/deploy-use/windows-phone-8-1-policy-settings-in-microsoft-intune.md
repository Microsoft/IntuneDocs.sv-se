---
title: Principinställningar för Windows Phone 8.1
description: I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i Windows Phone 8.1-enheter. Du kan också ange OMA-URI-värden för att skapa anpassade inställningar som inte är tillgängliga från Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 83f7469c-272e-43f2-8139-b0d7bc34f43f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b44215e301bb712cc4d27722515d2e51b124101b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="windows-phone-81-policy-settings-in-microsoft-intune"></a>Principinställningar för Windows Phone 8.1 i Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i Windows Phone 8.1-enheter. Du kan också ange OMA-URI-värden (Open Mobile Alliance Uniform Resource Identifier) för att skapa anpassade inställningar som inte är tillgängliga från Intune.

## <a name="general-configuration-settings"></a>Allmänna konfigurationsinställningar

Använd Microsoft Intunes **Allmänna konfigurationsprincip för Windows Phone (Windows Phone 8.1 och senare)** om du vill konfigurera följande inställningar för Windows Phone 8.1-enheter:

-   **Säkerhetsinställningar för mobil enhet** – Välj i en lista fördefinierade inställningar med vilka du kan reglera många av enhetens egenskaper och funktioner.

-   **Kompatibla och inkompatibla appar** – Ange en lista över appar i företaget som är kompatibla eller inkompatibla. Windows Phone-enheter kan blockera eller tillåta installation av dessa appar.

### <a name="applicability-settings"></a>Tillämplighetsinställningar

|Inställningsnamn|Information|
|----------------|----------------------------------|
|**Tillämpa alla konfigurationer på Windows 10**|Gör att inställningar i den här principen tillämpas på Windows 10 Mobile-enheter utöver Windows Phone 8.1-enheter.|

### <a name="password-settings"></a>Inställningar för lösenord

|                                           Inställningsnamn                                            |                                                                                                                                    Information                                                                                                                                     |
|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                   <strong>Kräv ett lösenord för att låsa upp mobila enheter</strong>                    |                                                                                                     Anger om användarna måste ange ett lösenord för att få åtkomst till sina enheter.                                                                                                     |
|                              <strong>Lösenordstyp krävs</strong>                              |                                                                                          Anger vilken typ av lösenord som krävs, t.ex. enbart alfanumeriskt eller numeriskt.                                                                                           |
|            <strong>Krävd lösenordstyp – minsta antal teckenuppsättningar</strong>             | Anger hur många olika teckenuppsättningar som lösenordet måste innehålla. Det finns fyra teckenuppsättningar: gemena bokstäver, versala bokstäver, siffror och symboler. För iOS-enheter specificerar detta dock det antal symboler som måste inkluderas i lösenordet. |
|                             <strong>Minsta längd på lösenord</strong>                              |                                                                                                 Anger det minsta antalet tecken som lösenordet måste innehålla.                                                                                                  |
|                              <strong>Tillåt enkla lösenord</strong>                              |                                                                                                     Anger att enkla lösenord kan användas, till exempel "0000" och "1234".                                                                                                     |
|     <strong>Antal tillåtna, upprepade felinloggningar innan enheten rensas</strong>      |                                                                                         Anger hur många gånger ett felaktigt lösenord kan anges innan enheten rensas.                                                                                         |
|                <strong>Antal minuter av inaktivitet innan skärmen stängs av</strong>                 |                                                                                       Anger hur lång tid en enhet måste vara inaktiv innan skärmen låses automatiskt.                                                                                        |
|                            <strong>Lösenordets giltighetstid (i dagar)</strong>                            |                                                                                                    Anger antalet dagar innan lösenordet måste ändras.                                                                                                    |
|                            <strong>Kom ihåg tidigare lösenord</strong>                             |                                                                                     Anger om tidigare använda lösenord ska sparas så att användaren inte kan använda dem igen.                                                                                      |
| <strong>Spara lösenordshistorik</strong> – <strong>Förhindra återanvändning av tidigare lösenord</strong> |                                                                                                          Anger hur många tidigare använda lösenord som ska lagras.                                                                                                          |

### <a name="encryption-settings"></a>Krypteringsinställningar

|Inställningsnamn|Information|
|----------------|------|
|**Filkryptering på mobil enhet**|Kräver att data på mobila enheter som stöds krypteras.|

### <a name="system-settings"></a>Systeminställningar

|Inställningsnamn|Information|
|----------------|-----|
|**Tillåt skärmbild**|Låter användaren fånga innehållet på skärmen som en bildfil.|
|**Tillåt sändning av diagnostikdata**|Gör att enheten skickar diagnostikinformation till Microsoft.|

### <a name="cloud-settings--accounts-and-synchronization"></a>Molninställningar – konton och synkronisering

|Inställningsnamn|Information|
|----------------|------|
|**Tillåt Microsoft-konto**|Gör att ett Microsoft-konto kopplas till enheten.|

### <a name="email-settings"></a>E-postinställningar

|Inställningsnamn|Information|
|----------------|-----|
|**Tillåt anpassade e-postkonton**|Gör att enheten ansluter till andra e-postkonton än Microsoft-e-postkonton.|

### <a name="application-settings---browser"></a>Programinställningar - webbläsare

|Inställningsnamn|Information|
|----------------|-----|
|**Tillåt webbläsare**|Tillåter eller blockerar den inbyggda webbläsaren på enheter.|

### <a name="application-settings---apps"></a>Programinställningar - appar

|Inställningsnamn|Information|
|----------------|-----|
|**Tillåt appbutik**|Tillåter att användarna ansluter till appbutiken från enheten.|

### <a name="device-capabilities-settings---hardware"></a>Enhetskapacitetsinställningar - maskinvara

|Inställningsnamn|Information|
|----------------|-----|
|**Tillåt kamera**|Tillåter eller blockerar kameran på enheten.|
|**Tillåt flyttbara lagringsmedier**|Tillåter att enheten använder flyttbara lagringsenheter, till exempel SD-kort.|
|**Tillåt Wi-Fi**|Aktiverar eller inaktiverar Wi-Fi-funktioner på enheten.|
|**Tillåt trådlös Internetdelning**|Tillåter att Wi-Fi-delning används på enheten.|
|**Tillåt automatisk anslutning till kostnadsfria trådlösa surfzoner**|Gör att enheten ansluter automatiskt till kostnadsfria trådlösa surfzoner och att den automatiskt godkänner användningsvillkoren.|
|**Tillåt rapportering om trådlösa surfzoner**|Skickar information om Wi-Fi-anslutningar så att användaren lättare kan upptäcka närliggande anslutningar.|
|**Tillåt geolokalisering**|Gör att enheten använder platsinformation.|
|**Tillåt NFC**|Tillåter åtgärder som använder närfältskommunikation.|
|**Tillåt Bluetooth**|Aktiverar eller inaktiverar Bluetooth-funktionen på enheten.|

### <a name="device-capabilities-settings---features"></a>Enhetskapacitetsinställningar - funktioner

|Inställningsnamn|Information|
|----------------|----|
|**Tillåt kopiera och klistra in**|Tillåter kopierings- och inklistringsfunktioner på enheter.|

### <a name="settings-for-allowed-and-blocked-apps"></a>Inställningar för tillåtna och blockerade appar
I **Lista över tillåtna och blockerade appar** anger du en lista över appar som du vill tillåta eller blockera med hjälp av följande information:

> [!NOTE]
> En enskild princip kan bara innehålla en lista över tillåtna eller blockerade appar. Du kan inte ange båda i samma princip.

|                          Inställningsnamn                          |                                                                                                      Information                                                                                                      |
|----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <strong>Blockera enheter från att öppna apparna i listan</strong>   |                                                        Visar en lista med de appar som inte hanteras av Intune och som användarna inte får installera och köra.                                                         |
| <strong>Tillåt endast att enheter får installera apparna i listan</strong> |                                 Visar listan med de appar som användare tillåts att installera. Användarna kan inte installera några andra appar. Appar som hanteras av Intune tillåts automatiskt.                                 |
|                      <strong>Lägg till</strong>                      | Lägger till en app i den markerade listan. Ange ett namn, webbadressen till appen i appbutiken och appens utgivare (valfritt). Mer hjälp finns i Så här anger du webbadresser till appbutiker senare i det här avsnittet. |
|                  <strong>Importera appar</strong>                  |                              Importerar en lista med appar som du har angett i en fil med kommaseparerade värden. Använd format, appnamn, utgivare och app-URL i filen.                               |
|                     <strong>Redigera</strong>                      |                                                                          Du kan redigera namn, utgivare och webbadress för den valda appen.                                                                          |
|                    <strong>Ta bort</strong>                     |                                                                                      Tar bort den markerade appen från listan.                                                                                      |

> [!IMPORTANT]
> Om du skapar en lista över tillåtna appar för Windows Phone 8.1-enheter måste du lägga till företagsportalappen i listan, annars blockeras den.


### <a name="reference-information-for-allowed-and-blocked-apps"></a>Referensinformation för tillåtna och blockerade appar

#### <a name="how-to-specify-urls-to-app-stores"></a>Så här anger du webbadresser till appbutiker
Om du vill ange en app-URL i listan över tillåtna och blockerade appar använder du följande format:

Gå till sidan [Appar+spel i Windows Phone appar och spel](http://www.windowsphone.com/store/overview) och sök efter den app du vill använda.

Öppna appens sida och kopiera webbadressen till Urklipp. Nu kan du använda den som webbadress i listan över tillåtna eller blockerade appar.

**Exempel:** Sök i butiken efter Skype-appen. Den URL som du använder är **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.

## <a name="custom-policy-settings"></a>Anpassade principinställningar
Använd **Anpassad konfigurationsprincip för Windows Phone** i Microsoft Intune för att distribuera OMA-URI-inställningar som kan användas till att styra funktioner på **Windows Phone 8.1-enheter**. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Med den här funktionen kan du distribuera Windows Phone-inställningar som inte kan konfigureras med en allmän Intune-konfigurationsprincip. Information om vilka inställningar som du kan konfigurera med dessa principer finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Mer information om hur du skapar OMA-URI-inställningar för Windows Phone-enheter finns i [dokumentationen för Windows Phone 8.1 MDM-protokollet](http://technet.microsoft.com/library/dn499787.aspx).

### <a name="general-settings"></a>Allmänna inställningar

|Inställningsnamn|Information|
|----------------|--------------------|
|**Namn**|Ange ett unikt namn för principen som hjälper dig att identifiera den i Intune-konsolen.|
|**Beskrivning**|Ange en lämplig beskrivning av principen och annan information som gör det enkelt att hitta den.|

### <a name="oma-uri-settings"></a>OMA-URI-inställningar

Gå till avsnittet **OMA-URI-inställningar** och lägg till en inställning genom att klicka på **Lägg till**. Du kan också redigera och ta bort en befintlig inställning.

I dialogrutan **Lägg till eller redigera OMA-URI-inställning** anger du följande information:

|Inställningsnamn|Information|
    |--------|--------------------|
    |**Namn**|Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.|
    |**Beskrivning av inställning**|Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.|
    |**Datatyp**|Ange den datumtyp med vilken du vill specificera den här OMA-URI-inställningen. Välj mellan:<br /><br />-   **Sträng**<br />-   **Sträng (XML)**<br />-   **Datum och tid**<br />-   **Heltal**<br />-   **Flyttal**<br />-   **Boolesk**|
    |**OMA-URI (skiftlägeskänslig)**|Ange den OMA-URI som du vill tillhandahålla en inställning för.|
    |**Värde**|Ange det värde som ska associeras med den OMA-URI som du tidigare angav.|

### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
