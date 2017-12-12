---
title: "Inställningar för enhetsbegränsningar för Android i Intune"
titlesuffix: Azure portal
description: "Läs vilka Intune-inställningar du kan använda för att kontrollera enhetsinställningar och funktioner på Android-enheter.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 97e125d768ca7b0cf58a2892d78675dfa42ef7ce
ms.sourcegitcommit: fa0f0402dfd25ec56a0df08c23708c7e2ad41120
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/29/2017
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Inställningar av begränsningar för Android- och Samsung KNOX Standard-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd de här inställningarna med en princip för begränsning av Android-enhet för att konfigurera enheter i din organisation.

>[!TIP]
>Om de önskade inställningarna inte är tillgängliga så kan du konfigurera dina enheter med hjälp av en [anpassad profil](custom-settings-android.md). 

## <a name="general"></a>Allmänt

- **Kamera** – Enhetens kamera kan användas.
- **Kopiera och klistra in (endast Samsung KNOX)** – Tillåter funktioner för att kopiera och klistra in på enheten.
- **Urklippsdelning mellan appar (endast Samsung KNOX)** – Tillåter användning av Urklipp vid funktionen Kopiera och klistra in mellan appar.
- **Sändning av diagnostikdata (endast Samsung KNOX)** – Hindrar användaren från att skicka diagnostikdata från enheten.
- **Fabriksåterställning (endast Samsung KNOX)** – Tillåter att användaren utför en fabriksåterställning på enheten.
- **Geoplats (endast Samsung KNOX)** – Tillåter att enheten använder platsinformation.
- **Avstängning (endast Samsung KNOX)** – Tillåter att användaren stänger av enheten.<br>Om det är inaktiverat så går det inte att ställa in **antal felaktiga inloggningar innan enheten rensas**.
- **Skärmdump (endast Samsung KNOX)** – Låter användaren fånga skärminnehållet som en bild.
- **Röstassistent (endast Samsung KNOX)** – Tillåter användning av röstassistentens programvara på enheten.
- **YouTube (endast Samsung KNOX)** – Tillåter användning av YouTube-appen på enheten.
- **Delade enheter (endast Samsung Knox)** – Konfigurera en hanterad Samsung KNOX Standard-enhet som delad. I det här läget så kan slutanvändare logga in och ut ur enheten med sina autentiseringsuppgifter för Azure AD. Enheten fortsätter att vara hanterad oavsett om den används eller inte.<br>När detta används tillsammans med en SCEP-certifikatprofil gör den här funktionen det möjligt för användarna att dela en enhet med samma uppsättning appar till alla användare, men med deras egna SCEP-certifikat för användare.  Alla appdata rensas när användaren loggar ut.  Den här funktionen är begränsad till endast LOB-appar.

## <a name="password"></a>Lösenord

- **Lösenord** – Kräver att användaren måste ange ett lösenord för att få åtkomst till enheten.|Ja|Ja|
- **Minsta längd på lösenord** – Ange den minsta längd på lösenord som en användare måste konfigurera (mellan 4 och 16 tecken).
- **Maximalt antal minuter av inaktivitet innan skärmen låses** – Anger antalet minuter av inaktivitet innan enheten låses automatiskt.
- **Antal felaktiga inloggningar innan enheten rensas** – Anger antalet tillåtna felinloggningar innan enheten rensas.
- **Lösenordets giltighetstid (dagar)** – Anger antal dagar innan lösenordet för enheten måste ändras.
-  **Krav på lösenordstyp** – Anger den komplexitetsnivå som krävs för lösenordet och om biometriska enheter kan användas. Välj mellan:
    - **Standard för enheten**
    - **Låg säkerhetsbiometri**
    - **Minst numeriskt**
    - **Numeriskt avancerat** – Upprepande eller efterföljande siffror som ”1111” eller ”1234” tillåts inte<sup>1</sup>
    - **Minst alfabetiskt**
    - **Minst alfanumeriskt**
    - **Minst alfanumeriskt med symboler**
- **Förhindra återanvändning av tidigare lösenord** – Hindrar slutanvändaren från att skapa ett lösenord som har använts tidigare.
- **Upplåsning med fingeravtryck (endast Samsung KNOX)** – Tillåter användning av fingeravtryck för att låsa upp enheter som stöds.
- **Smart Lock och andra betrodda agenter** – Innebär att du kan styra Smart Lock-funktionen på kompatibla Android-enheter (Samsung KNOX Standard 5.0 och senare). Den här telefonfunktionen, som ibland kallas förtroendeagent, låter dig inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten är på en betrodd plats. Det kan till exempel användas när enheten är ansluten till en specifik bluetooth-enhet eller när den är nära en NFC-tagg. Du kan använda den här inställningen för att förhindra att användare konfigurerar Smart Lock.
- **Kryptering** – Kräver att filer på enheten krypteras.

<sup>1</sup> Innan du tilldelar den här inställningen till enheter, kontrollerar du att företagsportalappen har uppdaterats till den senaste versionen på målenheterna.

Om du konfigurerar inställningen **Numeriskt avancerad** och sedan tilldelar den till en enhet som kör en tidigare version av Android än 5.0, gäller följande.
- Om företagsportalappen kör en tidigare version än 1704 kommer ingen PIN-princip att tillämpas på enheten och ett fel visas i Azure-portalen.
- Om företagsportalappen kör version 1704 eller senare, kan bara en enkel PIN-kod användas. Android-versioner som är tidigare än 5.0 har inte stöd för den här inställningen. Inget fel visas i Azure-portalen.


## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (endast Samsung KNOX)** – Ger användaren åtkomst till Google Play Store på enheten.

## <a name="restricted-apps"></a>Begränsade appar

I listan över begränsade appar, kan du konfigurera någon av följande listor för både Android och Samsung KNOX Standard-enheter:

Listan **Otillåtna program** – Visar de program (som inte hanteras av Intune) som rapporteras om användarna installerar och kör dem.
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

- **Webbläsare (endast Samsung KNOX)** – Anger om enhetens standardwebbläsare får användas.
- **Autofyll (endast Samsung KNOX)** – Tillåter att webbläsarens autofyllfunktion används.
- **Cookies (endast Samsung KNOX)** – Tillåter att enhetens webbläsare använder cookies.
- **Javascript (endast Samsung KNOX)** – Tillåter att enhetens webbläsare använder Javascript.
- **Popup-fönster (endast Samsung KNOX)** – Tillåter att blockering av popup-fönster används i webbläsaren.

## <a name="allow-or-block-apps"></a>Tillåt eller blockera program

De här inställningarna kan användas för att ange program som kan installeras eller startas på enheter som endast kör Samsung KNOX Standard.
Dessutom kan du ange installerade program som ska vara dolda för enhetens användare. Användarna kan inte köra dessa program.

- **Appar som kan installeras (endast Samsung KNOX Standard)**
- **Appar som blockeras från att starta (endast Samsung KNOX Standard)**
- **Appar som döljs för användaren (endast Samsung KNOX Standard)**

För varje inställning konfigurerar du en lista med program med hjälp av något av följande:

- **Lägg till appar efter paketnamn** – Används främst för verksamhetsspecifika program. Ange namnet på programmet och namnet på appaketet. 
- **Lägg till appar efter URL** – Ange namnet på programmet och dess URL i Google Play Butik.
- **Lägg till hanterade appar** – I listan med program som du hanterar med Intune väljer du det program som du behöver.

## <a name="cloud-and-storage"></a>Moln och lagring

- **Google-säkerhetskopiering (endast Samsung KNOX)** – Tillåter användning av Google-säkerhetskopiering.
- **Automatisk synkronisering av Google-konto (endast Samsung KNOX)** – Tillåter att Google-kontoinställningarna får synkroniseras automatiskt.
- **Flyttbara lagringsmedier (endast Samsung KNOX)** – Tillåter att enheten använder flyttbara lagringsmedier, som t.ex. SD-kort.
- **Kryptering på minneskort (endast Samsung KNOX)** – Anger om enhetens minneskort måste vara krypterat.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning

- **Datanätverksväxling (endast Samsung KNOX)** – Tillåter datanätverksväxling när enheten är i ett mobilnät.
- **SMS och MMS (endast Samsung KNOX)** – Tillåter användning av SMS och MMS på enheten.
- **Röstsamtal (endast Samsung KNOX)** – Aktiverar eller inaktiverar röstsamtal på enheten.
- **Röstnätverksväxling (endast Samsung KNOX)** – Tillåter röstnätverksväxling när enheten är i ett mobilnät.
- **Bluetooth (endast Samsung KNOX)** – Tillåter att Bluetooth används på enheten.
- **NFC (endast Samsung KNOX)** – Tillåter åtgärder som använder närfältskommunikation, om enheten har stöd för det.
- **Trådlöst (endast Samsung KNOX)** – Tillåter trådlösa funktioner på enheten.
- **Trådlös Internetdelning (endast Samsung KNOX)** – Tillåter användning av trådlös Internetdelning på enheten.

## <a name="kiosk"></a>Helskärmsläge

Inställningarna för helskärmsläget gäller endast för Samsung KNOX Standard-enheter och enbart för program som du hanterar med Intune.

- **Välj en hanterad app** – Välj något av följande alternativ för att lägga till en eller flera hanterade program som kan köras när enheten är i helskärmsläge. Inga andra appar tillåts köra på enheten.
    - **Lägg till appar efter paketnamn**
    - **Lägg till appar efter URL**
    - **Lägg till hanterade appar**.
- **Viloläge för skärmknapp** – Aktiverar eller inaktiverar knappen för viloläge på enheten.
- **Volymknappar** – Aktiverar eller inaktiverar användningen av volymknapparna på enheten.


## <a name="next-steps"></a>Nästa steg

Fortsätt använda instruktionerna i [Så här konfigurerar du inställningar för enhetsbegränsning](device-restrictions-configure.md) för att skapa och sedan tilldela enhetsbegränsningsprofilen.
