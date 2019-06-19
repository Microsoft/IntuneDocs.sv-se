---
title: Enhetsbegränsningsinställningar för Android i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista över alla Android-enhetsinställningar du kan kontrollera och begränsa i Microsoft Intune. Använd dessa inställningar för att styra lösenordet, komma åt Google Play-butiken, tillåta eller förbjuda appar, styra webbläsarinställningarna, blockera appar, säkerhetskopiera till Google Cloud och styra alternativen för meddelanden, röst, datanätverksväxling, Wi-Fi och Bluetooth-anslutning.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f13b78e05b9f0b94d98677004c7059f1acaa80f9
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67045718"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Inställningar av begränsningar för Android- och Samsung Knox Standard-enheter i Intune

I den här artikeln visas alla inställningar av enhetsbegränsningar som du kan konfigurera för enheter som kör Android.

>[!TIP]
>Om de önskade inställningarna inte är tillgängliga så kan du konfigurera dina enheter med hjälp av en [anpassad profil](custom-settings-android.md).

## <a name="general"></a>Allmänt

- **Kamera**: Välj **Blockera** för att förhindra åtkomst till kameran. **Inte konfigurerad** ger åtkomst till kameran på enheten.
- **Kopiera och klistra in (endast Samsung Knox)** : Välj **Blockera** för att förhindra kopiera och klistra in. **Inte konfigurerad** tillåter funktioner för att kopiera och klistra in på enheten.
- **Urklippsdelning mellan appar (endast Samsung Knox)** : Välj **Blockera** för att förhindra användning av Urklipp vid funktionen kopiera och klistra in mellan appar. **Inte konfigurerad** tillåter att urklipp används för att kopiera och klistra in mellan appar.
- **Sändning av diagnostikdata (endast Samsung Knox)** : Välj **Blockera** för att hindra användaren från att skicka diagnostikdata från enheten. **Inte konfigurerat** låter användaren skicka in data.
- **Rensning (endast Samsung Knox)** : Tillåter att användaren kör en [rensning](devices-wipe.md) på enheten.
- **Geoplats (endast Samsung Knox)** : Välj **Blockera** för att inaktivera användningen av platsinformation på enheten. **Inte konfigurerad** tillåter enheten att använda platsinformationen.
- **Avstängning (endast Samsung Knox)** : Välj **Blockera** för att förhindra användaren från att stänga av enheten. Om den här inställningen inaktiveras kan inte inställningen **Antal felaktiga inloggningar innan enheten rensas** ställas in och kommer inte att fungera. **Inte konfigurerad** låter användaren stänga av enheten.
- **Skärmdump (endast Samsung Knox)** : Välj **Blockera** för att förhindra skärmdumpar. **Inte konfigurerat** låter användaren fånga skärminnehållet som en bild.
- **Röstassistent (endast Samsung Knox)** : Välj **Blockera** för att inaktivera S Voice-tjänsten. **Inte konfigurerad** tillåter användning av S Voice-tjänsten och appen på enheten. Inställningen gäller inte för Bixby eller röstassistenten för hjälpmedel som läser upp skärmens innehåll.
- **YouTube (endast Samsung Knox)** : Välj **Blockera** för att förhindra användare från att använda YouTube-appen. **Inte konfigurerad** tillåter användning av YouTube-appen på enheten.
- **Delade enheter (endast Samsung Knox)** : Konfigurera en hanterad Samsung Knox Standard-enhet som delad. När det är satt på **Tillåt** så kan slutanvändare logga in och ut ur enheten med sina autentiseringsuppgifter för Azure AD. Enheten fortsätter att vara hanterad oavsett om den används eller inte.</br>När detta används med en SCEP-certifikatprofil gör den här funktionen det möjligt för slutanvändare att dela en enhet med samma appar för alla användare. Men varje användare har sina egna SCEP-användarcertifikat. Alla appdata rensas när användaren loggar ut. Den här funktionen är begränsad till endast LOB-appar. </br>**Inte konfigurerad** förhindrar att flera slutanvändare loggar in på företagsportalappen på enheten med sina autentiseringsuppgifter för Azure AD.
- **Blockera datum- och tidsändringar (Samsung Knox)** : Välj **Blockera** för att förhindra användaren från att ändra datum- och tidsinställningar på enheten. **Inte konfigurerad** låter användare ändra datum- och tidsinställningar.

## <a name="password"></a>Lösenord

- **Lösenord**: **Kräv** att slutanvändaren måste ange ett lösenord för att få åtkomst till enheten. **Inte konfigurerad** låter användare komma åt enheten utan att ange ett lösenord.

    > [!NOTE]
    > Samsung Knox-enheter kräver automatiskt en fyrsiffrig PIN-kod under MDM-registreringen. Android-enheter kan automatiskt kräva att en PIN-kod är kompatibel med villkorsstyrd åtkomst.

- **Minsta längd på lösenord**: Ange den minsta längd på lösenord som en användare måste ange (mellan 4 och 16 tecken).
- **Maximalt antal minuter av inaktivitet innan skärmen låses**: Ange det maximala antal minuter av inaktivitet som ska tillåtas på enheten innan skärmen låses. En slutanvändare kan inte ange ett tidsvärde på en enhet som är större än den konfigurerade tiden i profilen. En slutanvändare kan dock ange ett lägre värde. Om profilen t.ex. är inställd på 15 minuter, kan en slutanvändare ange värdet till 5 minuter. En slutanvändare kan inte ange värdet till 30 minuter. 
- **Antal felaktiga inloggningar innan enheten rensas**: Ange antalet tillåtna felinloggningar innan enheten rensas.
- **Lösenordets giltighetstid (dagar)** : Ange antal dagar innan lösenordet för enheten måste ändras.
- **Krav på lösenordstyp**: Ange den komplexitetsnivå som krävs för lösenordet och om biometriska enheter kan användas. Alternativen är:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Minst numeriskt**
  - **Numeriskt avancerat**: Upprepade eller efterföljande siffror, till exempel ”1111” eller ”1234”, tillåts inte.<sup>1</sup>
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**
- **Förhindra återanvändning av tidigare lösenord**: Hindrar slutanvändaren från att skapa ett lösenord som har använts tidigare.
- **Upplåsning med fingeravtryck (endast Samsung Knox)** : Välj **Blockera** för att förhindra användning av fingeravtryck för att låsa upp enheten. **Inte konfigurerad** låter användare låsa upp enheten med ett fingeravtryck.
- **Smart Lock och andra betrodda agenter**: Välj **Blockera** för att förhindra Smart Lock och andra betrodda agenter från att justera låsskärmsinställningar (Samsung KNOX Standard 5.0+). Med den här telefonfunktionen, ibland även kallad förtroendeagent, kan du inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten finns på en betrodd plats. Funktionen kan till exempel användas när enheten är ansluten till en specifik Bluetooth-enhet eller när den är nära en NFC-tagg. Du kan använda den här inställningen för att förhindra att användare konfigurerar Smart Lock.
- **Kryptering**: Välj **Krävs** så att filer på enheten krypteras. Alla enheter stöder inte kryptering. Gör även så här för att använda funktionen: 
  1. Ställ in **Lösenord** till **Krävs**.
  2. Ställ in **Krav på lösenordstyp** till **Minst numeriskt**.
  3. Ställ in **Minsta lösenordslängd** till minst 4 för korrekt efterlevnadsrapportering för den här inställningen.

  > [!NOTE]
  > Om en krypteringsprincip tillämpas kräver Samsung Knox-enheter att användarna anger ett komplext sex tecken långt lösenord för enheten.

<sup>1</sup> Innan du tilldelar den här inställningen till enheter ska du se till att företagsportalappen har uppdaterats till den senaste versionen på målenheterna.

Om du ställer in **Krav på lösenordstyp** till **Numeriskt avancerad** och sedan tilldelar den till en enhet som kör en tidigare version av Android än 5.0, gäller följande:

- Om företagsportalappen kör en tidigare version än 1704 kommer ingen PIN-princip att tillämpas på enheten och ett fel visas i Azure-portalen.
- Om företagsportalappen kör version 1704 eller senare, kan bara en enkel PIN-kod användas. Android-versioner som är tidigare än 5.0 har inte stöd för den här inställningen. Inget fel visas i Azure-portalen.

## <a name="google-play-store"></a>Google Play Store

- **Google Play Butik (endast Samsung Knox)** : Välj **Blockera** för att förhindra användare från att använda appen Google Play Butik. **Inte konfigurerat** tillåter att användaren kommer åt Google Play Butik på enheten.

## <a name="restricted-apps"></a>Begränsade appar

Använd inställningarna för att tillåta eller förhindra specifika appar på enheten. Funktionen stöds på Android- och Samsung Knox Standard-enheter:

- **Otillåtna appar**: En lista över appar som inte hanteras av Intune som du inte vill ha installerade på enheten. Om en användare installerar en app från den här listan kommer Intune att meddela dig.
- **Godkända appar**: En lista över de appar som användare tillåts att installera. Om användarna vill fortsätta följa standard får de inte installera andra appar. Appar som hanteras av Intune tillåts automatiskt.

Om du vill lägga till en app i listorna kan du:

- **Lägga till** webbadressen till den app du vill ha i Google Play Butik. Om du till exempel vill lägga till Microsoft Remote Desktop-appen för Android anger du `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`. Du hittar webbadressen till en app genom att öppna [Google Play Butik](https://play.google.com/store/apps) och söka efter appen. Du kan t.ex. söka efter `Microsoft Remote Desktop Play Store` eller `Microsoft Planner`. Välj appen och kopiera webbadressen.
- Importera en CSV-fil med information om appen, inklusive webbadressen. Använd formatet <*app-URL*>, <*appnamn*>, <*appens utgivare*>. Eller, **Exportera** en befintlig lista som innehåller listan över begränsade appar i samma format.

> [!IMPORTANT]
> Enhetsprofiler som använder inställningar för begränsade appar måste tilldelas grupper av användare.

## <a name="browser"></a>Webbläsare

- **Webbläsare (endast Samsung Knox)** : Välj **Blockera** för att förhindra att standardwebbläsaren används på enheten. **Inte konfigurerad** gör att enhetens standardwebbläsare används.
- **Autofyll (endast Samsung Knox)** : Välj **Blockera** för att förhindra autofyll av text i webbläsaren. **Inte konfigurerad** tillåter att webbläsarens autofyllfunktion används.
- **Cookies (endast Samsung Knox)** : Välj hur du vill hantera cookies från webbplatser på enheten. Alternativen är:
  - Tillåt
  - Blockera alla cookies
  - Tillåt cookies från besökta webbplatser
  - Tillåt cookies från aktuell webbplats
- **JavaScript (endast Samsung Knox)** : Välj **Blockera** för att förhindra att webbläsaren kör Java-skript. **Inte konfigurerad** tillåter att enhetens webbläsare kör Java-skript.
- **Popup-fönster (endast Samsung Knox)** : Välj **Blockera** för att förhindra popup-fönster i webbläsaren. **Inte konfigurerad** tillåter popup-fönster i webbläsaren.

## <a name="allow-or-block-apps"></a>Tillåt eller blockera program

Använd inställningarna för att tillåta, blockera eller dölja specifika appar på Samsung Knox Standard-enheter. Användare kan inte öppna eller köra appar som är dolda.

Alternativen är:

- **Appar som kan installeras (endast Samsung Knox Standard)**
- **Appar som blockeras från att starta (endast Samsung Knox Standard)**
- **Appar som döljs för användaren (endast Samsung Knox Standard)**

Lägg till en lista över appar för varje inställning. Alternativen är:

- **Lägg till appar efter paketnamn**: Används främst för verksamhetsspecifika program. Ange namnet på programmet och namnet på appaketet.
- **Lägg till appar efter URL**: Ange namnet på programmet och dess URL i Google Play Butik.
- **Lägg till butiksapp**: Välj en app från den befintliga listan med appar som du hanterar i Intune.

## <a name="cloud-and-storage"></a>Moln och lagring

- **Google-säkerhetskopiering (endast Samsung Knox)** : Välj **Blockera** för att förhindra att enheten synkroniserar med Google-säkerhetskopiering. **Inte konfigurerad** tillåter användning av Google-säkerhetskopiering.
- **Automatisk synkronisering av Google-konto (endast Samsung Knox)** : Välj **Blockera** för att hindra funktionen automatisk synkronisering av Google-konto på enheten. **Inte konfigurerad** låter Google-kontoinställningarna synkroniseras automatiskt.
- **Flyttbara lagringsenheter (endast Samsung Knox)** : Välj **Blockera** för att förhindra att enheten använder flyttbara lagringsenheter. **Inte konfigurerad** tillåter att enheten använder flyttbara lagringsenheter, t.ex. ett SD-kort.
- **Kryptering på minneskort (endast Samsung Knox)** : **Kräv** framtvingar att enhetens minneskort måste vara krypterat. **Inte konfigurerad** tillåter användning av okrypterade minneskort. Alla enheter stöder inte kryptering av minneskort. Bekräfta genom att kontrollera detta med enhetstillverkaren.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning

- **Datanätverksväxling (endast Samsung Knox)** : Välj **Blockera** för att förhindra datanätverksväxling över det mobila nätverket. **Inte konfigurerad** tillåter datanätverksväxling när enheten är i ett mobilnät.
- **SMS och MMS (endast Samsung Knox)** : Välj **Blockera** för att förhindra användning av textmeddelanden på enheten. **Inte konfigurerad** tillåter att SMS och MMS används på enheten.
- **Röstsamtal (endast Samsung Knox)** : Välj **Blockera** för att förhindra funktionen röstsamtal från att användas på enheten. **Inte konfigurerad** tillåter röstsamtal på enheten.
- **Röstnätverksväxling (endast Samsung Knox)** : Välj **Blockera** för att förhindra röstnätverksväxling över det mobila nätverket. **Inte konfigurerad** tillåter röstnätverksväxling när enheten är i ett mobilnät.
- **Bluetooth (endast Samsung Knox)** : Välj **Blockera** för att förhindra användningen av Bluetooth på enheten. **Inte konfigurerad** tillåter att Bluetooth används på enheten.
- **NFC (endast Samsung Knox)** : Välj **Blockera** för att stoppa NFC-teknik (Near Field Communication). **Inte konfigurerad** tillåter åtgärder som använder närfältskommunikation, om enheten har stöd för det.
- **Wi-Fi (endast Samsung Knox)** : Välj **Blockera** för att förhindra användningen av Wi-Fi på enheten. **Inte konfigurerad** tillåter användning av Wi-Fi-funktioner på enheten.
- **Trådlös internetdelning (endast Samsung Knox)** : Välj **Blockera** för att förhindra användningen av trådlös internetdelning på enheten. **Inte konfigurerad** tillåter att trådlös internetdelning används på enheten.

## <a name="kiosk"></a>Helskärmsläge

Inställningarna för helskärmsläget gäller endast för Samsung Knox Standard-enheter och enbart för program som du hanterar med Intune.

- Lägg till appar som du vill ska köras när enheten är i helskärmsläge. I helskärmsläge körs bara appar som du lägger till. Appar som inte har lagts till körs inte. Förinstallerade webbläsare körs inte som en app när enheten är i helskärmsläge. Om en webbläsare krävs ska du fundera på att använda den [hanterade webbläsaren](app-configuration-managed-browser.md).

  Alternativ för din app:

  - **Lägg till appar efter paketnamn**: Används främst för verksamhetsspecifika program. Ange namnet på programmet och namnet på appaketet.
  - **Lägg till appar efter URL**: Ange namnet på programmet och dess URL i Google Play Butik.
  - **Lägg till butiksapp**: Välj en app från den befintliga listan med appar som du hanterar i Intune.

- **Viloläge för skärmknapp**: Välj **Blockera** för att förhindra eller dölja viloläge för skärmknapp. **Inte konfigurerad** tillåter aktiveringsknappen på enheten.
- **Volymknappar**: Välj **Blockera** för att förhindra användaren från att ändra volymen genom att inaktivera volymknapparna. **Inte konfigurerad** tillåter användningen av volymknapparna på enheten.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa profiler för helskärmsläge för [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)- och [Windows 10](kiosk-settings.md)-enheter.
