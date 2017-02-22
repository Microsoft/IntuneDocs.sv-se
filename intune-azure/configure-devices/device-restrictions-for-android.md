---
title: "Inställning av begränsningar i Intune-enheter för Android | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs om de Intune-inställningar du kan använda för att styra inställningar och funktioner på Android-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/23/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 74023866802eb4c13e7e9ff97e8048afe7d62409
ms.openlocfilehash: 40e04f1f8e7972bcd72cceae272d8295a496df7a


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-intune-azure-preview"></a>Inställning av begränsningar i förhandsversionen av Intune Azure-enheter för Android och Samsung KNOX Standard

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Allmänt
-   **Kamera** – Enhetens kamera kan användas.
-   **Kopiera och klistra in** – Tillåter funktioner för att kopiera och klistra in på enheten.
-   **Urklippsdelning mellan appar** – Tillåter användning av Urklipp vid funktionen Kopiera och klistra in mellan appar (endast Samsung KNOX Standard).
-   **Sändning av diagnostikdata** – Hindrar användaren från att skicka diagnostikdata från enheten.    
-   **Fabriksåterställning** – Tillåter att användaren utför en fabriksåterställning på enheten.
-   **Geoplats** – Tillåter att enheten använder platsinformation (endast Samsung KNOX Standard).
-   **Avstängning** – Tillåter att användaren stänger av enheten.<br>Om du inaktiverar den här inställningen kommer inte inställningen **Antal felaktiga inloggningar innan enheten rensas** att fungera för Samsung KNOX Standard-enheter.
-   **Skärmdump** – Låter användaren fånga skärminnehållet som en bild.
-   **Röstassistent** – Tillåter användning av röstassistentens programvara på enheten (endast Samsung KNOX Standard).
-   **YouTube** – Tillåter användning av YouTube-appen på enheten (endast Samsung KNOX Standard).

## <a name="password"></a>Lösenord
-   **Lösenord krävs** – Slutanvändaren måste ange ett lösenord för att få åtkomst till enheten.
-   **Minsta längd på lösenord** – Ange den minsta längd på lösenord som en användare måste konfigurera (mellan 4 och 16 tecken).
-   **Maximalt antal minuter av inaktivitet innan skärmen låses** – Anger antalet minuter av inaktivitet innan enheten låses automatiskt.
-   **Antal felaktiga inloggningar innan enheten rensas** – Anger antalet tillåtna felinloggningar innan enheten rensas.
-   **Lösenordets giltighetstid (dagar)** – Anger antal dagar innan lösenordet för enheten måste ändras.
-   **Krav på lösenordstyp** – Anger den komplexitetsnivå som krävs för lösenordet och om biometriska enheter kan användas.
-   **Förhindra återanvändning av tidigare lösenord** – Hindrar slutanvändaren från att skapa ett lösenord som har använts tidigare.
-   **Upplåsning med fingeravtryck** – Tillåter användning av fingeravtryck för att låsa upp enheter som stöds.
-   **Smart Lock och andra betrodda agenter** – Innebär att du kan styra Smart Lock-funktionen på kompatibla Android-enheter (Samsung KNOX Standard 5.0 och senare). Med den här telefonfunktionen, som ibland kallas förtroendeagent, kan du inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten är på en betrodd plats, till exempel när det är anslutet till en specifik bluetoothenhet eller när den är nära en NFC-tagg. Du kan använda den här inställningen för att förhindra att användare konfigurerar Smart Lock.
-   **Kryptering** – Kräver att filer på enheten krypteras.

## <a name="google-play-store"></a>Google Play Store

-   **Google Play Store** – Ger användaren åtkomst till Google Play Store på enheten (endast Samsung KNOX Standard).

## <a name="restricted-apps"></a>Begränsade appar

Du kan konfigurera en av följande listor i listan med begränsade appar:

Listan **Otillåtna appar** – Ange de appar (som inte hanteras av Intune) som användarna inte får installera och köra.
Listan **Godkända appar** – Ange de appar som användare tillåts att installera. För att fortsätta vara kompatibla får användarna inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt.
Enhetsprofiler som innehåller inställningar för begränsade appar måste distribueras till grupper av användare.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare samt webbadressen till appen i appbutiken.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Så här anger du webbadressen till appen i butiken

Gör så här om du vill ange en app-URL i listan över kompatibla och inkompatibla appar:

I [App-delen i Google Play](https://play.google.com/store/apps) söker du efter den app du vill använda.

Öppna installationssidan för appen och kopiera webbadressen till Urklipp. Nu kan du använda denna som webbadress, i listan över kompatibla eller inkompatibla appar.

Exempel: Sök på Google Play efter Microsoft Office Mobile. Webbadressen du ska använda är **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

### <a name="additional-options"></a>Ytterligare alternativ

Du kan också klicka på **Importera** för att fylla i listan från en csv-fil i formatet <*app-url*>, <*appnamn*>, <*appens utgivare*>, eller klicka på **Exportera** för att skapa en csv-fil med innehållet i listan över begränsade appar i samma format.      

## <a name="browser"></a>Webbläsare
-   **Webbläsare** – Anger om enhetens standardwebbläsare får användas.
-   **Autofyll** – Tillåter att webbläsarens autofyllfunktion används.
-   **Cookies** – Tillåter att enhetens webbläsare använder cookies.
-   **JavaScript** – Tillåter att enhetens webbläsare kör Java-skript.
-   **Popup-fönster** – Tillåter att blockering av popup-fönster används i webbläsaren.

## <a name="cloud-and-storage"></a>Moln och lagring
-   **Google-säkerhetskopiering** – Tillåter användning av Google-säkerhetskopiering.
-   **Automatisk synkronisering av Google-konto** – Tillåter att Google-kontoinställningarna får synkroniseras automatiskt.
-   **Flyttbara lagringsmedier** – Tillåter att enheten använder flyttbara lagringsmedier, som t.ex. SD-kort (endast Samsung KNOX Standard).
-   **Kryptering på minneskort** – Anger om enhetens minneskort måste vara krypterat.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning
-   **Datanätverksväxling** – Tillåter datanätverksväxling när enheten är i ett mobilnät (endast Samsung KNOX Standard).
-   **SMS och MMS** – Tillåter användning av SMS och MMS på enheten (endast Samsung KNOX Standard).
-   **Röstsamtal** – Aktiverar eller inaktiverar röstsamtal på enheten (endast Samsung KNOX Standard).
-   **Röstnätverksväxling** – Tillåter röstnätverksväxling när enheten är i ett mobilnät (endast Samsung KNOX Standard).
-   **Bluetooth** – Tillåter användning av Bluetooth på enheten (endast Samsung KNOX Standard).
-   **NFC** – Tillåter åtgärder som använder närfältskommunikation, om enheten har stöd för det (endast Samsung KNOX Standard).
-   **Trådlöst** – Tillåter trådlösa funktioner på enheten (endast Samsung KNOX Standard).
-   **Trådlös Internetdelning** – Tillåter användning av trådlös Internetdelning på enheten (endast Samsung KNOX Standard).

## <a name="kiosk"></a>Helskärmsläge
-   **Välj en hanterad app** – Bläddra till och välj en hanterad app som kan köras när enheten är i helskärmsläge (appar som har angetts som en länk till butiken stöds inte för närvarande). Inga andra appar kommer att kunna köras på enheten.
-   **Viloläge för skärmknapp** – Aktiverar eller inaktiverar knappen för viloläge på enheten.
-   **Volymknappar** – Aktiverar eller inaktiverar användningen av volymknapparna på enheten.



<!--HONumber=Feb17_HO1-->


