---
# required metadata

title: Inställningar för Android- och Samsung KNOX-konfigurationsprinciper | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inställningar för Android- och Samsung KNOX-principer i Microsoft Intune

## Allmän konfigurationsprincip

Använd Microsoft Intunes **allmänna konfigurationsprincip för Android** om du vill konfigurera inställningar för:

-   **Säkerhetsinställningar för mobil enhet** – Välj i en lista fördefinierade inställningar med vilka du kan reglera många av enhetens egenskaper och funktioner.

-   **Helskärmsläge** (enbart för Samsung KNOX-enheter) – Lås en enhet så att bara vissa funktioner fungerar. Du kan t.ex. tillåta att enheten endast ska kunna köra en hanterad app som du anger, eller så kan du inaktivera volymknapparna på en enhet. De här inställningarna kan användas på en demonstrationsmodell av en enhet, eller en enhet som bara används för att utföra en enda funktion, till exempel i en butikskassa.

-   **Kompatibla och inkompatibla appar** – Ange en lista över appar i företaget som är kompatibla eller inkompatibla. För Android- och iOS-enheter kan **Inkompatibilitetsrapporter för appar** användas för att visa om de appar du har angett i listan är kompatibla med appar som användare har installerat (men det inte går att blockera installationen av programmet).

> [!TIP]
> Du kan konfigurera villkor för användarna för att säkerställa att de är medvetna om att apparna på deras enheter, även personliga appar, kommer att utvärderas och inkompatibla appar antingen kommer att blockeras eller rapporteras som inkompatibla. Användarna måste acceptera dessa villkor innan de kan registrera sina enheter och använda företagsportalen för att hämta appar. Mer information om de allmänna villkoren finns i [Inställningar för användarvillkor i Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Om den inställning som du söker efter inte visas i det här avsnittet kan du skapa den med hjälp av en anpassad Android-princip med vilken du kan använda OMA-URI-inställningar för att styra enheten. Mer information finns i **Anpassade principinställningar** senare i det här avsnittet.

### Inställningar för lösenord

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX|
|----------------|-|----------------|----------------|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Kräv ett lösenord på enheter som stöds.|Ja|Ja|
|**Minsta längd på lösenord**|Minimilängd för lösenordet.|Ja|Ja|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|Rensar enheten om detta antal inloggningsförsök misslyckas.|Ja|Ja|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Ange antalet minuter innan enheten låses automatiskt.|Ja|Ja|
|**Lösenordets giltighetstid (i dagar)**|Antal dagar innan ett lösenord måste ändras.|Ja|Ja|
|**Kom ihåg tidigare lösenord**|Kom ihåg så här många lösenord som har använts tidigare.|Ja|Ja|
|**Spara lösenordshistorik** – **Förhindra återanvändning av tidigare lösenord**|Förhindrar återanvändning av lösenord som har använts tidigare.|Ja|Ja|
|**Lösenordskvalitet**|Välj den komplexitetsnivå som krävs för lösenordet och om biometriska enheter kan användas.|Ja|Ja|
|**Tillåt fingeravtrycksupplåsning**|Tillåt att enheten kan låsas upp med ett fingeravtryck.|Nej|Ja|

### Krypteringsinställningar

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Filkryptering på mobil enhet**|Kräver att filer på den mobila enheten krypteras.|Ja|Ja|
|**Kräv kryptering på minneskort**|Anger om enhetens minneskort måste vara krypterat.|Nej|Ja|

### Systeminställningar

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Tillåt skärmbild**|Låter användaren fånga skärminnehållet som en bild.|Nej|Ja|
|**Tillåt sändning av diagnostikdata**|Tillåter att enheten skickar diagnostikinformation till Google.|Nej|Ja|
|**Tillåt fabriksåterställning**|Tillåt att användaren utför en fabriksåterställning på enheten.|Nej|Ja|

### Molninställningar – dokument och data

|Inställningsnamn|Information|Android och Samsung KNOX|Android 4.0+|
|----------------|----------------------------|----------------|
|**Tillåt Google säkerhetskopiering**|Google-säkerhetskopiering får användas.|Nej|Ja|

### Molninställningar – konton och synkronisering

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Tillåt autosynkronisering av Google-konto**|Google-kontoinställningarna får synkroniseras automatiskt.|Nej|Ja|

### Programinställningar - webbläsare

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Tillåt webbläsare**|Anger om enhetens webbläsare får användas.|Nej|Ja|
|**Tillåt autofyll**|Tillåt att webbläsarens autofyllfunktion används.|Nej|Ja|
|**Tillåt blockering av popup-fönster**|Tillåter att blockering av popup-fönster används i webbläsaren.|Nej|Ja|
|**Tillåt cookies**|Tillåt att enhetens webbläsare använder cookies.|Nej|Ja|
|**Tillåt active scripting**|Tillåt att enhetens webbläsare använder aktiva skript.|Nej|Ja|

### Programinställningar - appar

|Inställningsnamn|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Tillåt Google Play-butik**|Tillåt att användaren kommer åt Google Play Store på enheten.|Nej|Ja|

### Enhetskapacitetsinställningar - maskinvara

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Tillåt kamera**|Enhetens kamera får användas.|Ja|Ja|
|**Tillåt flyttbara lagringsenheter**|Tillåter att enheten använder flyttbara lagringsenheter, t.ex. ett SD-kort.|Nej|Ja|
|**Tillåt Wi-Fi**|Tillåter att enhetens Wi-Fi-funktioner används.|Nej|Ja|
|**Tillåt Wi-Fi -delning**|Tillåter att Wi-Fi-delning används på enheten.|Nej|Ja|
|**Tillåt geolokalisering**|Tillåter att enheten använder platsinformation.|Nej|Ja|
|**Tillåt NFC**|Tillåter åtgärder som använder närfältskommunikation, om enheten har stöd för det.|Nej|Ja|
|**Tillåt Bluetooth**|Tillåter att Bluetooth används på enheten.|Nej|Ja|
|**Tillåt kraftavstängning**|Tillåter att användaren stänger av enheten.<br /><br />Om du inaktiverar den här inställningen så fungerar inte inställningen **Antal tillåtna upprepade felinloggningar innan enheten rensas** för Samsung KNOX-enheter.|Nej|Ja|

### Enhetskapacitetsinställningar - mobil

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Tillåt röstroaming**|Tillåt röstnätverksväxling när enheten befinner sig i ett mobilnät.|Nej|Ja|
|**Tillåt dataroaming**|Tillåt datanätverksväxling när enheten använder ett mobilnät.|Nej|Ja|
|**Tillåt SMS/MMS-meddelanden**|Tillåt att SMS och MMS används på enheten.|Nej|Ja|

### Enhetskapacitetsinställningar - funktioner

|Inställningsnamn|Information|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Tillåt röstassistent**|Tillåter att röstassistentprogramvaran används på enheten.|Nej|Ja|
|**Tillåt röstsamtal**|Aktiverar eller inaktiverar röstsamtalsfunktionen på enheten.|Nej|Ja|
|**Tillåt kopiera och klistra in**|Tillåt funktioner för att kopiera och klistra in på enheten.|Nej|Ja|
|**Tillåt delning av urklipp mellan program**|Använd urklipp för att kopiera och klistra in mellan appar.|Nej|Ja|
|**Tillåt YouTube**|Tillåt att YouTube används på enheten.|Nej|Ja|

### Inställningar för kompatibla och icke-kompatibla appar
I listan över **kompatibla och &amp;inkompatibla appar** skapar du en lista över kompatibla eller inkompatibla appar med hjälp av följande information:

> [!NOTE]
> En enda princip kan bara innehålla en lista över kompatibla eller en lista över inkompatibel appar. Du kan inte ange båda i samma princip.

|Inställningsnamn|Information|
|----------------|--------------------|
|**Rapportera inkompatibilitet när användare installerar apparna i listan**|Visar en lista med de appar som inte hanteras av Intune och som användarna inte får installera och köra.|
|**Rapportera inte inkompatibilitet när användare installerar apparna i listan**|Visar listan med de appar som användare tillåts att installera. För att fortsätta vara kompatibla får användarna inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt.|
|**Lägg till**|Lägger till en app i den markerade listan. Ange ett namn, eventuellt appens utgivare och webbadressen till appen i appbutiken.<br /><br />Mer hjälp finns i Så här anger du webbadresser till appbutiker senare i det här avsnittet.|
|**Importera appar**|Importerar en lista med appar som du har angett i en fil med kommaseparerade värden. Använd format, appnamn, utgivare och app-URL i filen.|
|**Redigera**|Du kan redigera namn, utgivare och webbadress för den valda appen.|
|**Ta bort**|Tar bort den markerade appen från listan.|

### Helskärmsinställningar
Ange följande inställningar för **Samsung KNOX-enheter**:

|Inställningsnamn|Information|
|----------------|--------------------|
|**Välj en hanterad app som ska kunna köras när enheten är i helskärmsläge**|Klicka på **Bläddra** och välj den hanterade app som kommer att tillåtas att köras när enheten är i helskärmsläge (appar som har angetts som en länk till butiken stöds inte för närvarande). Inga andra appar kommer att kunna köras på enheten.|
|**Tillåt volymknappar**|Aktiverar eller inaktiverar användningen av volymknapparna på enheten.|
|**Tillåt aktiveringsknapp på skärmen**|Aktiverar eller inaktiverar aktiveringsknappen på enhetens skärm.|

### Referensinformation för kompatibla och icke-kompatibla appar

#### Övervaka kompatibla och icke-kompatibla appar
Använd **Inkompatibilitetsrapporter för appar** för att visa kompatibiliteten för tillåtna och blockerade appar.

###### Så här kör du Inkompatibilitetsrapporter för appar

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) klickar du på **Rapporter** &gt; **Inkompatibilitetsrapport för appar**.

2.  Välj de enhetsgrupper du vill kontrollera, om du vill söka efter kompatibla eller icke kompatibla appar och klicka sedan på **Visa rapport**.

#### Så här anger du webbadresser till appbutiker
Om du vill specificera en app-URL i listan över kompatibla och ej kompatibla appar ska du använda följande format:

I [App-delen i Google Play](https://play.google.com/store/apps) söker du efter den app du vill använda.

Öppna installationssidan för appen och kopiera webbadressen till Urklipp. Nu kan du använda denna som webbadress, i listan över kompatibla eller inkompatibla appar.

**Exempel**: Sök på Google Play efter Microsoft Office Mobile. Webbadressen du ska använda är **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## Anpassade principinställningar
Använd **Anpassad konfigurationsprincip för Android** i Microsoft Intune för att distribuera OMA-URI-inställningar (Open Mobile Alliance Uniform Resource Identifier) som kan användas till att styra funktioner på Android-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna distribuera Android-inställningar som inte går att konfigurera med Intune-principer. Information om vilka inställningar som du kan konfigurera med dessa principer finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

> [!NOTE]
> För närvarande stöder de anpassade Android-principerna enbart konfiguration av Wi-Fi-inställningar i Android-enheter som innehåller en i förväg delad nyckel. Mer information finns i Konfigurera en anpassad Wi-Fi-profil med en i förväg delad nyckel senare i det här avsnittet.

### Allmänna inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för den anpassade Android-principen som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en beskrivning med en översikt av den anpassade Android-principen och annan information som gör det enkelt att hitta den.|

### OMA-URI-inställningar

   |Inställningsnamn|Information|
    |--------|--------------------|
    |**Inställningsnamn**|Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.|
    |**Beskrivning av inställning**|Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.|
    |**Datatyp**|Ange den datumtyp med vilken du vill specificera den här OMA-URI-inställningen. Välj **sträng, sträng (XML), datum och tid, heltal, flyttal** eller **booleskt**.|
    |**OMA-URI (skiftlägeskänslig)**|Ange den OMA-URI som du vill tillhandahålla en inställning för.|
    |**Värde**|Ange det värde som ska associeras med den OMA-URI som du tidigare angav.|

### Exempel: Konfigurera en anpassad Wi-Fi-profil med en i förväg delad nyckel
Även om Intune stöder Wi-Fi-profiler för Android-enheter stöder den här funktionen för närvarande inte att en i förväg delad nyckel läggs till i konfigurationen. I det här exemplet lär du dig hur du skapar en anpassad Android-princip som i sin tur skapar en Wi-Fi-profil med en i förväg delad nyckel på Android-enheten.

#### Så här skapar du en Wi-Fi-profil med en i förväg delad nyckel

1.  Kontrollera att dina användare använder den senaste versionen av appen [Intune-företagsportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) för Android.

2.  Skapa en anpassad Android-princip och lägg till följande inställningar:

|Inställningsnamn|Information|
|----------------|--------------------|
|**Inställningsnamn**|Ange ett valfritt namn för inställningen.|
|**Beskrivning av inställning**|Ange en beskrivning av inställningen.|
|**Datatyp**|Välj **Sträng (XML)**.|
|**OMA-URI**|Ange följande: ./Vendor/MSFT/WiFi/Profile/*&lt;din Wi-Fi-profil&gt;*/Settings|

3.  Kopiera och klistra in följande XML-kod för **Värde**:

    ```
    <!--
    WEP Wifi Profile
                    <Name of wifi profile> = Name of profile 
                    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
                    <WEP password> = Password to connect to the network
    -->
    <WLANProfile 
    xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name><Name of wifi profile></name>
      <SSIDConfig>
        <SSID>
          <name><SSID of wifi profile></name>
        </SSID>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <MSM>
        <security>
          <authEncryption>
            <authentication>open</authentication>
            <encryption>WEP</encryption>
            <useOneX>false</useOneX>
          </authEncryption>
          <sharedKey>
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial><WEP password></keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>
    ```

4.  När du är klar sparar du principen och distribuerar den till de Android-enheter som behöver den. Den nya Wi-Fi-profilen visas i listan med anslutningar på enheten.

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO3-->


