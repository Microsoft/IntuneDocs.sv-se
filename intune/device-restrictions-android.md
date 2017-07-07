---
title: "Inställningar för enhetsbegränsningar för Android i Intune"
titleSuffix: Intune on Azure
description: "Läs vilka Intune-inställningar du kan använda för att kontrollera enhetsinställningar och funktioner på Android-enheter.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 44d80e1c72b58eccd4e69b1d561c7d651f39b3c3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Inställningar av begränsningar för Android- och Samsung KNOX Standard-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd de här inställningarna med en princip för begränsning av Android-enhet för att konfigurera enheter i din organisation.

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
|**Avstängning**|Tillåter att användaren stänger av enheten.<br>Om det är inaktiverat så går det inte att ställa in **antal felaktiga inloggningar innan enheten rensas**.|Nej|Ja|
|**Skärmdump**|Låter användaren fånga skärminnehållet som en bild.|Nej|Ja|
|**Röstassistent**|Tillåter att röstassistentprogramvaran används på enheten.|Nej|Ja|
|**YouTube**|Tillåter att YouTube-appen används på enheten.|Nej|Ja|
|**Delade enheter**|Konfigurera en hanterad Samsung KNOX Standard-enhet som delad. I det här läget så kan slutanvändare logga in och ut ur enheten med sina autentiseringsuppgifter för Azure AD. Enheten fortsätter att vara hanterad oavsett om den används eller inte.<br>När slutanvändare loggar in så får de tillgång till appar och eventuella principer tillämpas på dem. Alla appdata rensas när användaren loggar ut.|Nej|Ja|

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
|**Smart Lock och andra betrodda agenter**|Innebär att du kan styra Smart Lock-funktionen på kompatibla Android-enheter (Samsung KNOX Standard 5.0 och senare). Den här telefonfunktionen, som ibland kallas förtroendeagent, låter dig inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten är på en betrodd plats. Det kan till exempel användas när enheten är ansluten till en specifik bluetooth-enhet eller när den är nära en NFC-tagg. Du kan använda den här inställningen för att förhindra att användare konfigurerar Smart Lock.|Ja (5.0 och senare)|Ja|
|**Kryptering**|Kräver att filer på enheten krypteras.|Ja|Ja|

<sup>1</sup> Innan du tilldelar den här inställningen till enheter, kontrollerar du att företagsportalappen har uppdaterats till den senaste versionen på målenheterna.

Om du konfigurerar inställningen **Numeriskt avancerad** och sedan tilldelar den till en enhet som kör en tidigare version av Android än 5.0, gäller följande.
- Om företagsportalappen kör en tidigare version än 1704 så kommer ingen PIN-kodsprincip att tillämpas på enheten och ett fel visas i Intune-portalen.
- Om företagsportalappen kör version 1704 eller senare, kan bara en enkel PIN-kod användas. Android-versioner som är tidigare än 5.0 har inte stöd för den här inställningen. Inget fel visas i Intune-portalen.


## <a name="google-play-store"></a>Google Play Store

|||||
|-|-|-|-|
|Inställningsnamn|Information|Android 4.0+|Samsung KNOX Standard|
|**Google Play Store**|Tillåter att användaren kommer åt Google Play Store på enheten|Nej|Ja|

## <a name="restricted-apps"></a>Begränsade appar

I listan över begränsade appar, kan du konfigurera någon av följande listor för både Android och Samsung KNOX Standard-enheter:

Listan **Otillåtna appar** – Ange de appar (som inte hanteras av Intune) som användarna inte får installera och köra.
Listan **Godkända appar** – Ange de appar som användare tillåts att installera. För att fortsätta vara kompatibla, får användare inte installera andra appar. Appar som hanteras av Intune tillåts automatiskt.
Enhetsprofiler som innehåller inställningar för begränsade appar måste tilldelas grupper av användare.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare samt webbadressen till appen i appbutiken.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Så här anger du webbadressen till appen i butiken

Gör så här om du vill ange en app-URL i listan över kompatibla och inkompatibla appar:

I [App-delen i Google Play](https://play.google.com/store/apps) söker du efter den app du vill använda.

Öppna installationssidan för appen och kopiera webbadressen till Urklipp. Nu kan du använda den URL:en i antingen listan över kompatibla eller inkompatibla appar.

Exempel: Sök på Google Play efter Microsoft Office Mobile. URL:en du ska använda är: **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

### <a name="additional-options"></a>Ytterligare alternativ

Du kan också klicka på **importera** för att hämta listan från en csv-fil. Använd formatet <*app-url*>, <*appnamn*>, <*appleverantör*> eller klicka på **Exportera** i csv-filen som innehåller listan med begränsade appar i samma format.      

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
|**Välj en hanterad app**|Välj något av följande alternativ för att lägga till en eller flera appar som kan köras när enheten är i helskärmsläge. Inga andra appar tillåts köra på enheten.<br><br>- **Lägg till appar efter paketnamn**<br>- **Lägg till appar efter URL**<br>- **Lägg till hanterade appar**|Nej|Ja|
|**Viloläge för skärm-knapp**|Aktiverar eller inaktiverar aktiveringsknappen på enhetens skärm.|Nej|Ja|
|**Volymknappar**|Aktiverar eller inaktiverar användningen av volymknapparna på enheten.|Nej|Ja|
