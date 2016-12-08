---

title: "Inställningar för Android- och Samsung KNOX Standard-principer | Microsoft Intune"
description: "Skapa principer som styr inställningar och funktioner på Android-enheter som du hanterar med Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 08ec9963bf00d81f080c0cf4f26e23a3104763ea


---

# <a name="android-and-samsung-knox-standard-policy-settings-in-microsoft-intune"></a>Inställningar för Android- och Samsung KNOX Standard-principer i Microsoft Intune

I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i Android-enheter. Du kan också ange OMA-URI-värden (Open Mobile Alliance Uniform Resource Identifier) för att skapa anpassade inställningar som inte är tillgängliga från Intune.

## <a name="general-configuration-policy"></a>Allmän konfigurationsprincip

Använd Intunes **allmänna konfigurationsprincip för Android** för att konfigurera inställningarna för:

-   **Säkerhetsinställningar för mobil enhet** – Välj bland fördefinierade inställningar i en lista för att reglera många av enhetens egenskaper och funktioner.

-   **Helskärmsläge** (endast för Samsung KNOX Standard-enheter) – Lås en enhet så att bara vissa funktioner fungerar. Du kan t.ex. tillåta att enheten ska kunna köra endast en hanterad app som du anger, eller så kan du inaktivera volymknapparna på en enhet. De här inställningarna kan användas på en demonstrationsmodell av en enhet, eller en enhet som bara används för att utföra en enda funktion, till exempel i en butikskassa.

-   **Kompatibla och inkompatibla appar** – Ange en lista över appar i företaget som är kompatibla eller inkompatibla. För Android- och iOS-enheter kan **Inkompatibilitetsrapporter för appar** användas för att visa om de appar du har angett i listan är kompatibla med appar som användare har installerat. Rapporten kan inte blockera installationen av appen.

> [!TIP]
> Du kan konfigurera villkor för användarna för att säkerställa att de är medvetna om att alla appar på deras enheter, även personliga appar, kommer att utvärderas och att inkompatibla appar antingen kommer att blockeras eller rapporteras som inkompatibla. Användarna måste acceptera dessa villkor innan de kan registrera sina enheter och använda företagsportalen för att hämta appar. Mer information om de allmänna villkoren finns i [Inställningar för användarvillkor i Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Om den inställning som du söker efter inte visas i det här avsnittet kan du skapa den med hjälp av en anpassad Android-princip med vilken du kan använda OMA-URI-inställningar för att styra enheten. Mer information finns i [Anpassade principinställningar](#custom-policy-settings) senare i det här avsnittet.

### <a name="password-settings"></a>Inställningar för lösenord

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|-|----------------|----------------|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Anger om ett lösenord ska krävas på enheter som stöds.|Ja|Ja|
|**Minsta längd på lösenord**|Anger minimilängd för lösenordet.|Ja|Ja|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Anger antalet tillåtna felinloggningar innan enheten rensas.|Ja|Ja|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Anger antalet minuter av inaktivitet innan enheten låses automatiskt.|Ja|Ja|
|**Lösenordets giltighetstid (i dagar)**|Anger antal dagar innan ett lösenord måste ändras.|Ja|Ja|
|**Kom ihåg tidigare lösenord**|Anger antalet lösenord som har använts tidigare som ska sparas.|Ja|Ja|
|**Spara lösenordshistorik** - **Förhindra återanvändning av tidigare lösenord **|Förhindrar återanvändning av tidigare lösenord.|Ja|Ja|
|**Lösenordskvalitet**|Anger den komplexitetsnivå som krävs för lösenordet och om biometriska enheter kan användas.|Ja|Ja|
|**Tillåt fingeravtrycksupplåsning**|Tillåter att enheten kan låsas upp med ett fingeravtryck.|Nej|Ja|
|**Tillåt Smart Lock och andra betrodda agenter**<br>(Android 5 och senare)|Gör att du kan styra Smart Lock-funktionen i kompatibla Android-enheter. Med den här telefonfunktionen, som ibland kallas förtroendeagent, kan du inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten är på en betrodd plats, till exempel när det är anslutet till en specifik bluetoothenhet eller när den är nära en NFC-tagg. Du kan använda den här inställningen för att förhindra att användare konfigurerar Smart Lock.|Ja|Nej|

### <a name="encryption-settings"></a>Krypteringsinställningar

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Filkryptering på mobil enhet**|Kräver att filer på den mobila enheten krypteras.|Ja|Ja|
|**Kräv kryptering på minneskort**|Anger om enhetens minneskort måste vara krypterat.|Nej|Ja|

### <a name="system-settings"></a>Systeminställningar

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Tillåt skärmbild**|Låter användaren fånga skärminnehållet som en bild.|Nej|Ja|
|**Tillåt sändning av diagnostikdata**|Tillåter att enheten skickar diagnostikinformation till Google.|Nej|Ja|
|**Tillåt fabriksåterställning**|Tillåter att användaren utför en fabriksåterställning på enheten.|Nej|Ja|

### <a name="cloud-settings---documents-and-data"></a>Molninställningar – dokument och data

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------------------|----------------|
|**Tillåt Google-säkerhetskopiering**|Tillåter användning av Google-säkerhetskopiering.|Nej|Ja|

### <a name="cloud-settings---accounts-and-synchronization"></a>Molninställningar – konton och synkronisering

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Tillåt automatisk synkronisering av Google-konto**|Google-kontoinställningarna får synkroniseras automatiskt.|Nej|Ja|

### <a name="application-settings---browser"></a>Programinställningar - webbläsare

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Tillåt webbläsare**|Anger om enhetens standardwebbläsare får användas.|Nej|Ja|
|**Tillåt autofyll**|Tillåter att webbläsarens autofyllfunktion används.|Nej|Ja|
|**Tillåt blockering av popup-fönster**|Tillåter att blockering av popup-fönster används i webbläsaren.|Nej|Ja|
|**Tillåt cookies**|Tillåter att enhetens webbläsare använder cookies.|Nej|Ja|
|**Tillåt Active scripting**|Tillåter att enhetens webbläsare använder aktiva skript.|Nej|Ja|

### <a name="application-settings---apps"></a>Programinställningar - appar

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Tillåt Google Play-butik**|Tillåter att användaren kommer åt Google Play Store på enheten.|Nej|Ja|

### <a name="device-capabilities-settings---hardware"></a>Enhetskapacitetsinställningar - maskinvara

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Tillåt kamera**|Enhetens kamera får användas.|Ja|Ja|
|**Tillåt flyttbara lagringsenheter**|Tillåter att enheten använder flyttbara lagringsenheter, t.ex. ett SD-kort.|Nej|Ja|
|**Tillåt Wi-Fi**|Tillåter att enhetens Wi-Fi-funktioner används.|Nej|Ja|
|**Tillåt Wi-Fi -delning**|Tillåter att Wi-Fi-delning används på enheten.|Nej|Ja|
|**Tillåt geolokalisering**|Tillåter att enheten använder platsinformation.|Nej|Ja|
|**Tillåt NFC**|Tillåter åtgärder som använder närfältskommunikation, om enheten har stöd för det.|Nej|Ja|
|**Tillåt Bluetooth**|Tillåter att Bluetooth används på enheten.|Nej|Ja|
|**Tillåt avstängning**|Tillåter att användaren stänger av enheten.<br /><br />Om du inaktiverar den här inställningen så fungerar inte inställningen **Antal tillåtna upprepade felinloggningar innan enheten rensas** för Samsung KNOX Standard-enheter.|Nej|Ja|

### <a name="device-capabilities-settings---cellular"></a>Enhetskapacitetsinställningar - mobil

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Tillåt röstroaming**|Tillåter röstroaming när enheten är i ett mobilnät.|Nej|Ja|
|**Tillåt dataroaming**|Tillåter dataroaming när enheten är i ett mobilnät.|Nej|Ja|
|**Tillåt SMS/MMS-meddelanden**|Tillåter att SMS och MMS används på enheten.|Nej|Ja|

### <a name="device-capabilities-settings---features"></a>Enhetskapacitetsinställningar - funktioner

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Tillåt röstassistent**|Tillåter att röstassistentprogramvaran används på enheten.|Nej|Ja|
|**Tillåt röstsamtal**|Aktiverar eller inaktiverar röstsamtalsfunktionen på enheten.|Nej|Ja|
|**Tillåt kopiera och klistra in**|Tillåter funktioner för att kopiera och klistra in på enheten.|Nej|Ja|
|**Tillåt delning av urklipp mellan program**|Tillåter att urklipp används för att kopiera och klistra in mellan appar.|Nej|Ja|
|**Tillåt YouTube**|Tillåter användning av YouTube på enheten.|Nej|Ja|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>Inställningar för kompatibla och icke-kompatibla appar
I listan över **kompatibla och &amp;inkompatibla appar** skapar du en lista över kompatibla eller inkompatibla appar som använder följande information:

> [!NOTE]
> En enda princip kan innehålla endast en lista över kompatibla appar eller en lista över inkompatibla appar. Du kan inte ange båda i samma princip.

|Inställningsnamn|Information|
|----------------|--------------------|
|**Rapportera inkompatibilitet när användare installerar apparna i listan**|Visar en lista med de appar som inte hanteras av Intune och som du inte vill att användarna ska installera och köra. Om användarna installerar en av de här apparna skrivs det upp i en rapport över icke-kompatibla appar.|
|**Rapportera inte inkompatibilitet när användare installerar apparna i listan**|Visar de appar som du vill tillåta. För att fortsätta vara kompatibla får användarna inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt.|
|**Lägg till**|Lägger till en app i den markerade listan. Ange ett namn på appen, appens utgivare (valfritt) och webbadressen till appen i appbutiken.<br /><br />Mer information finns i [Ange webbadresser till appbutiker](#specify-urls-to-app-stores) senare i det här avsnittet.|
|**Importera appar**|Importerar en lista med appar som du har angett i en fil med kommaseparerade värden. Använd format, appnamn, utgivare och app-URL i filen.|
|**Redigera**|Du kan redigera namn, utgivare och webbadress för den valda appen.|
|**Ta bort**|Tar bort den markerade appen från listan.|

### <a name="kiosk-mode-settings"></a>Helskärmsinställningar
Ange följande inställningar för **Samsung KNOX Standard-enheter**:

|Inställningsnamn|Information|
|----------------|--------------------|
|**Välj en hanterad app som kan köras när enheten är i helskärmsläge**|Välj **Bläddra** och välj den hanterade app som kan köras när enheten är i helskärmsläge (appar som har angetts som en länk till butiken stöds inte för närvarande). Inga andra appar kommer att kunna köras på enheten.|
|**Tillåt volymknappar**|Aktiverar eller inaktiverar användningen av volymknapparna på enheten.|
|**Tillåt aktiveringsknapp på skärmen**|Aktiverar eller inaktiverar aktiveringsknappen på enhetens skärm.|

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Referensinformation för kompatibla och icke-kompatibla appar

#### <a name="monitor-compliant-and-noncompliant-apps"></a>Övervaka kompatibla och icke-kompatibla appar
Använd **Inkompatibilitetsrapporter för appar** för att visa kompatibiliteten för tillåtna och blockerade appar.

###### <a name="to-run-the-noncompliant-apps-report"></a>Så här kör du Inkompatibilitetsrapporter för appar

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Rapporter** &gt; **Inkompatibilitetsrapport för appar**.

2.  Välj de enhetsgrupper som du vill kontrollera. Välj sedan om du vill söka efter kompatibla appar, inkompatibla appar eller både och. Välj slutligen **Visa rapport**.

#### <a name="specify-urls-to-app-stores"></a>Ange webbadresser till appbutiker
Gör så här om du vill ange en app-URL i listan över kompatibla och inkompatibla appar:

I [App-delen i Google Play](https://play.google.com/store/apps) söker du efter den app du vill använda.

Öppna installationssidan för appen och kopiera webbadressen till Urklipp. Nu kan du använda denna som webbadress, i listan över kompatibla eller inkompatibla appar.

Exempel: Sök på Google Play efter Microsoft Office Mobile. Webbadressen du ska använda är **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## <a name="custom-policy-settings"></a>Anpassade principinställningar
Använd **Anpassad konfigurationsprincip för Android** i Microsoft Intune för att distribuera OMA-URI-inställningar som kan användas till att styra funktioner på Android-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna distribuera Android-inställningar som inte går att konfigurera med Intune-principer.

> [!NOTE]
> För närvarande stöder de anpassade Android-principerna enbart konfiguration av Wi-Fi-inställningar i Android-enheter som innehåller en i förväg delad nyckel.

### <a name="general-settings"></a>Allmänna inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för den anpassade Android-principen som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en beskrivning med en översikt av den anpassade Android-principen och annan information som gör det enkelt att hitta den.|

### <a name="oma-uri-settings"></a>OMA-URI-inställningar

   |Inställningsnamn|Information|
    |--------|--------------------|
    |**Inställningsnamn**|Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.|
    |**Beskrivning av inställning**|Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.|
    |**Datatyp**|Ange den datumtyp med vilken du vill specificera den här OMA-URI-inställningen. Välj **sträng, sträng (XML), datum och tid, heltal, flyttal** eller **booleskt**.|
    |**OMA-URI (skiftlägeskänslig)**|Ange den OMA-URI som du vill tillhandahålla en inställning för.|
    |**Värde**|Ange det värde som ska associeras med den OMA-URI som du tidigare angav.|

### <a name="examples"></a>Exempel

- [Skapa en Wi-Fi-profil med en i förväg delad nyckel](pre-shared-key-wi-fi-profile.md)
- [Använda en anpassad princip för att skapa en VPN-profil per app för Android-enheter](per-app-vpn-for-android-pulse-secure.md)
- [Använda anpassade principer för att tillåta och blockera appar för Samsung KNOX-enheter](custom-policy-to-allow-and-block-samsung-knox-apps.md)

### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Nov16_HO1-->


