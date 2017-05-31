---
title: "Inställningar för enhetsbegränsningar för Android i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs om de Intune-inställningar du kan använda för att styra inställningar och funktioner på Android-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3627b28b60908c225ce1797968123ce854a70a8b
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Inställningar av begränsningar för Android- och Samsung KNOX Standard-enheter i Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="general"></a>Allmänt

|||||
|-|-|-|-|
|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|**Kamera**|Enhetens kamera får användas.|Ja|Ja|
|**Kopiera och Klistra in**|Tillåter funktioner för att kopiera och klistra in på enheten.|Nej|Ja|
|**Delning av urklipp mellan appar**|Tillåter att urklipp används för att kopiera och klistra in mellan appar.|Nej|Ja|
|**Sändning av diagnostikdata**|Hindrar användaren från att skicka diagnostikdata från enheten.|Nej|Ja|
|**Fabriksåterställning**|Tillåter att användaren utför en fabriksåterställning på enheten.|Nej|Ja|
|**Geolocation**|Tillåter att enheten använder platsinformation (endast Samsung KNOX Standard).|Nej|Ja|
|**Avstängning**|Tillåter att användaren stänger av enheten.<br>Om du inaktiverar den här inställningen kommer inte inställningen **Antal felaktiga inloggningar innan enheten rensas** att fungera för Samsung KNOX Standard-enheter.|Nej|Ja|
|**Skärmdump**|Låter användaren fånga skärminnehållet som en bild.|Nej|Ja|
|**Röstassistent**|Tillåter att röstassistentprogramvaran används på enheten.|Nej|Ja|
|**YouTube**|Tillåter att YouTube-appen används på enheten.|Nej|Ja|
|**Delade enheter**|Konfigurera en hanterad Samsung KNOX Standard-enhet som delad. I det här läget kan användarna logga in och ut från enheten med sina Azure AD-autentiseringsuppgifter, enheten hanteras centralt oavsett om den används eller inte.<br>När användarna loggar in får de tillgång till appar och dessutom verkställs eventuella principer som gäller för dem. Alla appdata rensas när användaren loggar ut.|Nej|Ja|

## <a name="password"></a>Lösenord

|||||
|-|-|-|-|
|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|**Lösenord**|Slutanvändaren måste ange ett lösenord för att få åtkomst till enheten.|Ja|Ja|
|**Minsta längd på lösenord**|Ange den minsta längden på lösenord som en användare måste konfigurera (mellan 4 och 16 tecken).|Ja|Ja|
|**Maximalt antal minuter av inaktivitet innan skärmen låses**|Anger antalet minuter av inaktivitet innan enheten låses automatiskt.|Ja|Ja|
|**Antal felaktiga inloggningar innan enheten rensas**|Anger antalet tillåtna felinloggningar innan enheten rensas.|Ja|Ja|
|**Lösenordets giltighetstid (i dagar)**|Anger antalet dagar innan lösenordet måste ändras.|Ja|Ja|
|**Lösenordstyp krävs**|Anger den komplexitetsnivå som krävs för lösenordet och om biometriska enheter kan användas. Välj mellan:<br><br>    -     **Standard för enheten**<br>-     **Låg säkerhetsbiometri**<br>    -     **Minst numeriskt**<br>    -     **Numeriskt avancerat komplexa** – (upprepande eller efterföljande siffror som ”1111” eller ”1234” tillåts inte)<sup>1</sup><br>    -     **Minst alfabetiskt**<br>    -     **Minst alfanumeriskt**<br>    -     **Minst alfanumeriskt med symboler**|Ja|Ja|
|**Förhindra återanvändning av tidigare lösenord**|Hindrar slutanvändaren från att skapa ett lösenord som har använts tidigare.|Ja|Ja|
|**Upplåsning med fingeravtryck**|Tillåter användning av fingeravtryck för att låsa upp enheter som stöds.|Nej|Ja|
|**Smart Lock och andra betrodda agenter**|Innebär att du kan styra Smart Lock-funktionen på kompatibla Android-enheter (Samsung KNOX Standard 5.0 och senare). Med den här telefonfunktionen, som ibland kallas förtroendeagent, kan du inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten är på en betrodd plats, till exempel när det är anslutet till en specifik bluetoothenhet eller när den är nära en NFC-tagg. Du kan använda den här inställningen för att förhindra att användare konfigurerar Smart Lock.|Ja (5.0 och senare)|Ja|
|**Kryptering**|Kräver att filer på enheten krypteras.|Ja|Ja|

<sup>1</sup>Innan du tilldelar den här inställningen till enheter, kontrollerar du att företagsportalappen har uppdaterats till den senaste versionen på målenheterna.

Om du konfigurerar inställningen **Numeriskt avancerad** och sedan tilldelar den till en enhet som kör en tidigare version av Android än 5.0, gäller följande.
- Om företagsportalappen kör en version före 1704, kommer ingen PIN-kod-princip att tillämpas på enheten och ett fel visas i Intune-portalen.
- Om företagsportalappen har uppdaterats till 1704-versionen, tillämpas endast en enkel PIN-kod. Android-versioner som är tidigare än 5.0 har inte stöd för den här inställningen. Inget fel visas i Intune-portalen.


## <a name="google-play-store"></a>Google Play Store

|||||
|-|-|-|-|
|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|**Google Play Store**|Tillåter att användaren kommer åt Google Play Store på enheten|Nej|Ja|

## <a name="restricted-apps"></a>Begränsade appar

Du kan konfigurera en av följande listor i listan med begränsade appar:

Listan **Otillåtna appar** – Ange de appar (som inte hanteras av Intune) som användarna inte får installera och köra.
Listan **Godkända appar** – Ange de appar som användare tillåts att installera. För att fortsätta vara kompatibla får användarna inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt.
Enhetsprofiler som innehåller inställningar för begränsade appar måste tilldelas grupper av användare.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare samt webbadressen till appen i appbutiken.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Så här anger du webbadressen till appen i butiken

Gör så här om du vill ange en app-URL i listan över kompatibla och inkompatibla appar:

I [App-delen i Google Play](https://play.google.com/store/apps) söker du efter den app du vill använda.

Öppna installationssidan för appen och kopiera webbadressen till Urklipp. Nu kan du använda denna som webbadress, i listan över kompatibla eller inkompatibla appar.

Exempel: Sök på Google Play efter Microsoft Office Mobile. Webbadressen du ska använda är **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

### <a name="additional-options"></a>Ytterligare alternativ

Du kan också klicka på **Importera** för att fylla i listan från en csv-fil i formatet <*app-url*>, <*appnamn*>, <*appens utgivare*>, eller klicka på **Exportera** för att skapa en csv-fil med innehållet i listan över begränsade appar i samma format.        

## <a name="browser"></a>Webbläsare
|||||
|-|-|-|-|
|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|**Webbläsare**|Anger om enhetens standardwebbläsare får användas.|Nej|Ja|
|**Autofyll**|Tillåter att webbläsarens autofyllfunktion används.|Nej|Ja|
|**Cookies**|Tillåter att enhetens webbläsare använder cookies.|Nej|Ja|
|**Javascript**|Tillåter att enhetens webbläsare kör Java-skript.|Nej|Ja|
|**Popup-fönster**|Tillåter att blockering av popup-fönster används i webbläsaren.|Nej|Ja|

## <a name="cloud-and-storage"></a>Moln och lagring
|||||
|-|-|-|-|
|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|**Google-säkerhetskopiering**|Tillåter användning av Google-säkerhetskopiering.|Nej|Ja|
|**Automatisk synkronisering av Google-konto**|Google-kontoinställningarna får synkroniseras automatiskt.|Nej|Ja|
|**Flyttbart lagringsmedium**|Tillåter att enheten använder flyttbara lagringsenheter, t.ex. ett SD-kort.|Nej|Ja|
|**Kryptering på minneskort**|Anger om enhetens minneskort måste vara krypterat.|Nej|Ja|

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning
|||||
|-|-|-|-|
|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|**Datanätverksväxling**|Tillåter dataroaming när enheten är i ett mobilnät.|Nej|Ja|
|**SMS/MMS-meddelanden**|Tillåter att SMS och MMS används på enheten.|Nej|Ja|
|**Röstsamtal**|Aktiverar eller inaktiverar röstsamtalsfunktionen på enheten.|Nej|Ja|
|**Röstnätverksväxling**|Tillåter röstroaming när enheten är i ett mobilnät.|Nej|Ja|
|**Bluetooth**|Tillåter att Bluetooth används på enheten.|Nej|Ja|
|**NFC**|Tillåter åtgärder som använder närfältskommunikation, om enheten har stöd för det.|Nej|Ja|
|**Wi-Fi**|Tillåter att enhetens Wi-Fi-funktioner används.|Nej|Ja|
|**Trådlös Internetdelning**|Tillåter att Wi-Fi-delning används på enheten.|Nej|Ja|

## <a name="kiosk"></a>Helskärmsläge
|||||
|-|-|-|-|
|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|**Välj en hanterad app**|Bläddra till och välj en hanterad app som kan köras när enheten är i helskärmsläge (appar som har angetts som en länk till butiken stöds inte för närvarande). Inga andra appar kommer att kunna köras på enheten.|Nej|Ja|
|**Viloläge för skärm-knapp**|Aktiverar eller inaktiverar aktiveringsknappen på enhetens skärm.|Nej|Ja|
|**Volymknappar**|Aktiverar eller inaktiverar användningen av volymknapparna på enheten.|Nej|Ja|

