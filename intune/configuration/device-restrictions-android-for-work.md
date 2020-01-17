---
title: Enhetsinställningar för Android Enterprise i Microsoft Intune – Azure | Microsoft Docs
description: Du kan begränsa enhetsinställningarna för Android Enterprise eller Android for Work, inklusive inställningar för att kopiera och klistra in, visa aviseringar, appbehörigheter, dela data, lösenordslängd, inloggningsfel, använda fingeravtryck för upplåsning, återanvändning av lösenord och aktivering av Bluetooth-delning för arbetskontakter. Konfigurera enheter som en särskild enhet för att köra en eller flera appar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b6afd80517df3496e0c1402fc0c76f3fc24969fa
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206609"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Enhetsinställningarna för Android Enterprise tillåter eller begränsar funktioner med hjälp av Intune

Den här artikeln beskriver de olika inställningar som du kan styra på Android Enterprise-enheter. Som en del av MDM-lösningen (hantering av mobilenheter) använder du de här inställningarna för att tillåta eller inaktivera funktioner, köra appar på dedikerade enheter, kontrollera säkerhet och mer.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Endast enhetens ägare

Dessa inställningar gäller för Android Enterprise-registrerings typer där Intune styr hela enheten, till exempel Android Enterprise fullständigt hanterade eller dedikerade enheter.

### <a name="general-settings"></a>Allmänna inställningar

- **Skärmdump**: Välj **Blockera** för att förhindra skärmbilder eller skärmdumpar på enheten. Förhindrar också att innehållet visas på visningsenheter som inte har en säker videoutgång. **Inte konfigurerat** låter användaren fånga skärminnehållet som en bild.
- **Kamera**: Välj **Blockera** om du vill förhindra åtkomst till enhetens kamera. **Krävs inte** ger åtkomst till kameran på enheten.
- **Standardprincip för behörigheter**: Den här inställningen definierar standardbehörighetsprincipen vid begäranden om körningsbehörigheter. Möjliga värden är:
  - **Standard för enheten**: Använd enhetens standardinställning.
  - **Fråga**: Användaren uppmanas godkänna behörigheten.
  - **Bevilja automatiskt**: Behörigheter beviljas automatiskt.
  - **Neka automatiskt**: Behörigheter nekas automatiskt.
- **Datum- och tidsändringar**: Välj **Blockera** för att förhindra att användarna anger datum och tid manuellt. **Inte konfigurerad** tillåter användare att ange datum och tid på enheten.
- **Volym ändringar**: **blockera** förhindrar att användare ändrar enhetens volym och även stänger av huvud volymen. **Inte konfigurerad** tillåter volyminställningar på enheten.
- **Fabriksåterställning**: Välj **Blockera** för att förhindra att användarna använder alternativet för fabriksåterställning i enhetens inställningar. **Inte konfigurerad** tillåter användare att använda inställningen på enheten.
- **Säker start**: Välj **Blockera** för att förhindra att användarna startar om enheten i felsäkert läge. **Inte konfigurerad** tillåter användare att starta om enheten i felsäkert läge.
- **Statusfält**: Välj **Blockera** för att förhindra åtkomst till statusfältet, till exempel meddelanden och snabbinställningar. **Inte konfigurerad** ger användare åtkomst till statusfältet.
- **Dataroaming**: Välj **Blockera** om du vill förhindra dataroaming över det mobila nätverket. **Inte konfigurerad** tillåter dataroaming när enheten är i ett mobilnät.
- **Ändringar i Wi-Fi-inställning**: Välj **Blockera** för att förhindra att användarna ändrar Wi-Fi-inställningar som skapats av enhetsägaren. Användarna kan skapa sina egna Wi-Fi-konfigurationer. **Inte konfigurerad** tillåter användare att ändra Wi-Fi-inställningar på enheten.
- **Konfiguration av Wi-Fi-åtkomstpunkt**: Välj **Blockera** för att förhindra att användarna skapar eller ändrar Wi-Fi-konfigurationer. **Inte konfigurerad** tillåter användare att ändra Wi-Fi-inställningar på enheten.
- **Bluetooth-konfiguration**: Välj **Blockera** för att förhindra att användarna konfigurerar Bluetooth på enheten. **Inte konfigurerad** tillåter användning av Bluetooth på enheten.
- **Internetdelning och åtkomst till surfpunkter**: Välj **Blockera** för att förhindra Internetdelning och åtkomst till bärbara surfpunkter. **Inte konfigurerad** tillåter delning och åtkomst till bärbara surfzoner.
- **USB-lagring**: Välj **Tillåt** för åtkomst till USB-lagring på enheten. **Inte konfigurerad** förhindrar åtkomst till USB-lagring.
- **USB-filöverföring**: Välj **Blockera** för att förhindra överföring av filer via USB. **Inte konfigurerad** tillåter filöverföring.
- **Externa medier**: Välj **Blockera** för att förhindra användning av eller anslutning till externa medier på enheten. **Inte konfigurerad** tillåter extern media på enheten.
- **Överför data via NFC**: Välj **Blockera** för att förhindra användningen av NFC-teknik (Near Field Communication) vid överföring av data från appar. **Inte konfigurerad** tillåter NFC för att dela data mellan enheter.
- **Felsökningsfunktioner**: Välj **Tillåt** för att tillåta att användarna använder felsökningsfunktioner på enheten. **Inte konfigurerad** förhindrar användare från att använda felsökningsfunktioner på enheten.
- **Mikrofonjustering**: Välj **Blockera** för att förhindra att användarna slår på ljudet på mikrofonen och ändrar dess volym. **Inte konfigurerad** tillåter användaren att använda och justera mikrofonvolymen på enheten.
- **E-post för skydd mot fabriksåterställning**: Välj **E-postadresser för Google-konto**. Ange e-postadresserna för enhetsadministratörer som kan låsa upp enheten när den har rensats. Se till att avgränsa e-postadresser med semikolon, till exempel `admin1@gmail.com;admin2@gmail.com`. Om en e-postadress inte anges kan vem som helst låsa upp enheten efter den har återställts till fabriksinställningarna. De här e-postmeddelandena gäller endast när fabriks återställning från användare inte körs, till exempel att köra en fabriks återställning via återställnings menyn.
- **Nätverkshjälp**: Välj **Aktivera** för att tillåta att användarna aktiverar funktionen för nätverkshjälp. Om en nätverksanslutning inte skapats när enheten startas kommer nätverkshjälpen tillfälligt be om att ansluta till ett nätverk och uppdatera enhetsprincipen. När principen har tillämpats glöms det tillfälliga nätverket och starten av enheten fortsätter. Funktionen ansluter enheten till ett nätverk om:
  - Den förra principen saknar ett lämpligt nätverk.
  - Enheten startar i en app i låsläget.
  - Användaren inte kan nå enhetsinställningarna.

  **Inte konfigurerad** förhindrar användare från att aktivera funktionen nätverkshjälp på enheten.

- **Systemuppdatering**: Välj ett alternativ för att definiera hur enheten ska hantera trådlösa uppdateringar:
  - **Standard för enheten**: Använd enhetens standardinställning.
  - **Automatiskt**: Uppdateringar installeras automatiskt utan att användaren behöver göra något. Om du konfigurerar den här principen installeras väntande uppdateringar omedelbart.
  - **Uppskjuten**: Uppdateringar skjuts upp i 30 dagar. Mot slutet av 30-dagarsperioden uppmanar Android användaren att installera uppdateringen. Det är möjligt för enhetstillverkare eller operatörer att undanta viktiga säkerhetsuppdateringar från att skjutas upp. En undantagen uppdatering visar användaren ett systemmeddelande på enheten.
  - **Underhållsperiod**: Uppdateringar installeras automatiskt under en daglig underhållsperiod som du anger i Intune. Installationen gör ett försök dagligen under 30 dagar och kan misslyckas vid otillräckligt diskutrymme eller för låga batterinivåer. Efter 30 dagar uppmanar Android användaren att installera. Det här fönstret används också för att installera uppdateringar för Play-appar. Använd det här alternativet för dedikerade enheter såsom helskärmslägen, eftersom förgrundsappar för dedikerade enheter med enskild app kan uppdateras.

- **Meddelandefönster**: När **Inaktivera** har valts visas inte fönstermeddelanden, bland annat popup-fönster, inkommande samtal, utgående samtal, systemaviseringar och systemfel, på enheten. När **Inte konfigurerat** har valts används operativsystemets standardinställning, som kan vara att visa meddelanden.
- **Hoppa över första tipsen**: **Aktivera** gömmer eller hoppa över förslag från appar som går igenom självstudier eller tips när appen startar. När **Inte konfigurerat** har valts används operativsystemets standardinställning, som kan visa de här förslagen när appen startar.

### <a name="system-security-settings"></a>Inställningar för systemsäkerhet

- **Hotgenomsökning för appar**: Om du väljer **Kräv** (standard) kan Google Play Protect genomsöka appar före de installeras och efter de installerats. Om ett hot identifieras kan användaren varnas och uppmanas att ta bort appen från enheten. **Inte konfigurerad** innebär att Google Play Protect inte är aktiverat och inte söker igenom appar.

### <a name="dedicated-device-settings"></a>Inställningar för särskilda enheter

Använd dessa inställningar om du vill konfigurera en upplevelse i helskärmsformat i dina särskilda enheter. Du kan konfigurera en enhet för att köra en app eller flera appar. När en enhet är inställd på helskärmsläge är det bara de appar du lägger till som är tillgängliga. Dessa inställningar gäller för särskilda Android Enterprise-enheter. De gäller inte för fullständigt hanterade Android Enterprise-enheter.

**Helskärmsläge**: Välj om enheten ska köra en app eller flera appar.

- **Enstaka app**: Användarna har bara åtkomst till en enda app på enheten. Endast den specifika appen startar när enheten startar. Användarna förhindras att öppna nya appar eller ändra appen som körs.

  - **Välj en hanterad app**: Välj den hanterade Google Play-appen i listan.

    Om du inte har några appar som visas kan du [lägga till Android-appar](../apps/apps-add-android-for-work.md) till enheten. Se till att [tilldela appen till den enhetsgrupp som skapats för dina dedikerade enheter](../apps/apps-deploy.md).

  > [!IMPORTANT]
  > När du använder hel skärms läge för en enda app fungerar inte uppringnings-/telefon program korrekt. 
  
- **Flera appar**: Användarna har åtkomst till en begränsad uppsättning appar på enheten. Endast de appar du lägger till startar när enheten startar. Du kan också lägga till webblänkar som användare kan öppna. När principen används ser användarna ikoner för tillåtna appar på startskärmen.

  > [!IMPORTANT]
  > För dedikerade enheter för flera appar gäller att [appen Hanterade startskärmar](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) från Google Play **måste vara**:
  >   - [Tillagt som en klientapp](../apps/apps-add-android-for-work.md) i Intune
  >   - [Tilldelad till den enhetsgrupp](../apps/apps-deploy.md) som skapats för dina dedikerade enheter
  >
  > Appen **Hanterade startskärmar** måste inte finnas i konfigurationsprofilen, men den måste läggas till som klientapp. När appen **Hanterad startskärm** läggs till som en klientapp visas alla andra appar som du lägger till i konfigurationsprofilen som ikoner i **Hanterad startskärm**-appen.
  >
  > När du använder hel skärms läge för flera appar kanske inte uppringnings-/telefon program fungerar korrekt. 

  - **Lägg till**: Välj dina appar i listan.

    Om appen **Hanterad startskärm** inte visas kan du [lägga till den från Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Se till att [tilldela appen](../apps/apps-deploy.md) till den enhetsgrupp som skapats för dina dedikerade enheter.

    Du kan även lägga till andra [Android-appar](../apps/apps-add-android-for-work.md) och [webbappar](../apps/web-app.md) som skapats av din organisation till enheten. Se till att [tilldela appen till den enhetsgrupp som skapats för dina dedikerade enheter](../apps/apps-deploy.md).

  - **Virtuell Start knapp**: en knapp med mjuka nycklar som returnerar användare till den hanterade start skärmen så att användarna kan växla mellan appar. Alternativen är:

    - **Inte konfigurerad** (standard): en Start knapp visas inte. Användarna måste använda knappen bakåt för att växla mellan appar.
    - **Svep uppåt**: en Start knapp visar när en användare sveper upp på enheten.
    - **Flytande**: visar en beständigt, flytande Start knapp på enheten.

  - **Lämna helskärmsläge**: Välj **Aktivera** för att tillåta att administratörer tillfälligt kan pausa helskärmsläget för att uppdatera enheten. Om du vill använda den här funktionen kan administratören:
  
    1. Fortsätta att välja bakåtknappen tills knappen **Avsluta helskärmsläge** visas. 
    2. Väljer knappen **Avsluta helskärmsläge** och anger PIN-koden för **Kod för att lämna helskärmsläge**.
    3. När du är färdig väljer du appen **hanterad start** sida. Det här steget låser enheten i helskärmsläge för flera appar.

      När inställningen **inte är konfigurerad**kan administratörer inte pausa hel skärms läge. Om administratören fortsätter att välja bakåtknappen och väljer knappen **Avsluta helskärmsläge** visas ett meddelande om att ett lösenord krävs.

    - **Lämna kod för helskärmsläge**: Ange en numerisk PIN-kod på 4–6 siffror. Administratören använder den här PIN-koden för att tillfälligt pausa helskärmsläge.

  - **Ange anpassad URL-bakgrund**: Ange en URL för att anpassa bakgrundsskärmen på den dedikerade enheten.

    > [!NOTE]
    > I de flesta fall rekommenderar vi att du börjar med bilder med minst följande storlek:
    >
    > - Telefon: 1 080 x 1 920 bildpunkter
    > - Läsplatta: 1 920 x 1 080 bildpunkter
    >
    > För bästa möjliga upplevelse och detaljrikedom föreslår vi att du skapar bildresurser till enheternas respektive bildskärmsspecifikationer.
    >
    > Moderna bildskärmar har högre bildpunktsdensitet och kan visa bilder i 2K/4K.

  - **Wi-Fi-konfiguration**: **Aktivera** visar Wi-Fi-kontrollen på den hanterade start skärmen och gör att slutanvändarna kan ansluta enheten till olika WiFi-nätverk. Om du aktiverar den här funktionen aktiveras också enhetsplats. **Inte konfigurerad** (standard) visar inte Wi-Fi-kontrollen på den hanterade start skärmen. Den förhindrar användare från att ansluta till Wi-Fi-nätverk när den hanterade start skärmen används.

  - **Bluetooth-konfiguration**: **Aktivera** visar Bluetooth-kontrollen på den hanterade start skärmen och gör att slutanvändarna kan koppla enheter över Bluetooth. Om du aktiverar den här funktionen aktiveras också enhetsplats. **Inte konfigurerad** (standard) visar inte Bluetooth-kontrollen på den hanterade start skärmen. Den förhindrar användare från att konfigurera Bluetooth och para ihop enheter när den hanterade start skärmen används.

  - **Strålkastare Access**: **Enable** visar strålkastare-kontrollen på den hanterade start skärmen och gör att slutanvändarna kan aktivera eller inaktivera strålkastare. **Inte konfigurerad** (standard) visar inte kontrollen strålkastare på den hanterade start skärmen. Den förhindrar användare från att använda strålkastare när den hanterade start skärmen används.

  - **Medie volym kontroll**: **Aktivera** visar medie volym kontrollen på den hanterade start skärmen och gör att användarna kan justera enhetens medie volym med hjälp av ett skjutreglage. **Inte konfigurerad** (standard) visar inte medie volym kontrollen på den hanterade start skärmen. Det förhindrar att användare justerar enhetens medie volym på den hanterade start skärmen, om inte deras maskin varu knappar stöder det. 

  - **Skärmsläckare**: **Aktivera** visar en skärmsläckare på den hanterade start skärmen när enheten är låst eller tids gräns. **Inte konfigurerad** (standard) visar inte en skärmsläckare på den hanterade start skärmen.

    Konfigurera även när det är aktiverat:

    - **Ange avbildning av anpassad skärmsläckare**: Ange webb adressen till en anpassad png-, jpg-, JPEG-, GIF-, BMP-, WebP-eller ICOimage. Ange till exempel:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.webp`

      Om du inte anger en URL används enhetens Standard avbildning, om det finns en standard avbildning.
      
      > [!TIP]
      > Alla fil resurs-URL: er som kan omvandlas till en bitmapp stöds.

    - **Antal sekunder som enheten visar skärmsläckaren innan skärmen**stängs av: Välj hur länge enheten ska Visa skärmsläckaren. Ange ett värde mellan 0-9999999 sekunder. Standardvärdet är `0` sekunder. När värdet är tomt eller är inställt på noll (`0`) är skärmsläckaren aktiv tills en användare interagerar med enheten.
    - **Antal sekunder som enheten är inaktiv innan skärmsläckaren visas**: Välj hur länge enheten ska vara inaktiv innan skärmsläckaren visas. Ange ett värde mellan 1-9999999 sekunder. Standardvärdet är `30` sekunder. Du måste ange ett tal som är större än noll (`0`).
    - **Identifiera media innan**skärmsläckaren startas: **Aktivera** (standard) visar inte skärmsläckaren om ljud eller video spelas upp på enheten. **Inte konfigurerad** visar skärmsläckaren, även om ljud eller video spelas upp.

### <a name="device-password-settings"></a>Inställningar för enhetslösenord

- **Inaktivera Lås skärm**: Välj **Inaktivera** om du vill hindra användarna från att använda låsskärmsfunktionen Keyguard på enheten. **Inte konfigurerad** tillåter användaren att använda Keyguard-funktioner.
- **Inaktiverade låsskärmsfunktioner**: När keyguard har aktiverats på enheten väljer du vilka funktioner som ska inaktiveras. När **Säker kamera** är markerad är till exempel kamerafunktionen inaktiverad på enheten. Funktioner som inte är markerade är aktiverade på enheten.

  Dessa funktioner är tillgängliga för användarna när enheten är låst. Användarna kommer inte att se eller få åtkomst till de funktioner som är markerade.

- **Lösenordstyp som krävs**: Definiera typen av lösenord som krävs för enheten. Alternativen är:
  - **Standard för enheten**
  - **Lösenord krävs, inga begränsningar**
  - **Svag biometrik**: [Stark eller svag biometri](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (öppnar Androids webbplats)
  - **Numeriskt**: Lösenordet får bara innehålla siffror, till exempel `123456789`. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
  - **Numeriskt avancerat**: Upprepade eller efterföljande siffror, till exempel ”1111” eller ”1234”, tillåts inte. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
  - **Alfabetiskt**: Bokstäver i alfabetet måste anges. Siffror och symboler krävs inte. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
  - **Alfanumeriskt**: Innehåller versaler, gemener och numeriska tecken. Ange en **minsta längd på lösenord** som användaren måste ange (mellan 4 och 16 tecken).
  - **Alfanumeriskt med symboler**: Innehåller versaler, gemener, numeriska tecken, skiljetecken och symboler. Ange även:

    - **Minsta lösenordslängd**: Ange den minsta längd som lösenordet måste ha (mellan 4 och 16 tecken).
    - **Antal tecken som krävs**: Ange hur många tecken som lösenordet måste innehålla (mellan 0 och 16 tecken).
    - **Antal gemener som krävs**: Ange hur många gemener som lösenordet måste innehålla (mellan 0 och 16 tecken).
    - **Antal versaler som krävs**: Ange hur många versaler som lösenordet måste innehålla (mellan 0 och 16 tecken).
    - **Antal icke-bokstavstecken som krävs**: Ange hur många icke-bokstavstecken (bokstäver som inte ingår i alfabetet) som lösenordet måste innehålla (mellan 0 och 16 tecken).
    - **Antal numeriska tecken som krävs**: Ange hur många numeriska tecken (till exempel `1`, `2` eller `3`) som lösenordet måste innehålla (mellan 0 och 16 tecken).
    - **Antal symboltecken som krävs**: Ange hur många symboltecken (till exempel `&`, `#` eller `%`) som lösenordet måste innehålla (mellan 0 och 16 tecken).

- **Antal dagar tills lösenordet går ut**: Ange antal dagar innan lösenordet för enheten måste ändras (mellan 1 och 365). Exempel: Om du vill att lösenordet ska ändras om 60 dagar anger du `60`. När lösenordet upphör att gälla uppmanas användarna att skapa ett nytt lösenord.
- **Antal lösenord som krävs innan användaren kan återanvända ett lösenord**: Ange antalet senast använda lösenord som inte får återanvändas, mellan 1 och 24. Använd den här inställningen för att förhindra att användaren återanvänder tidigare använda lösenord.
- **Antal felaktiga inloggningar innan enheten rensas**: Anger antalet tillåtna felinloggningar, mellan 4 och 11, innan enheten rensas.

### <a name="power-settings"></a>Energiinställningar

- **Tid för att låsa skärmen**: Ange den längsta tid som en användare kan ange tills enheten låses. Om du till exempel ställer in den här inställningen på **10 minuter**kan användarna ange tiden från 15 sekunder upp till 10 minuter. När inställningen **inte är konfigurerad** , ändras inte Intune eller styrs av den här inställningen.

- **Skärmen är tänd när enheten är ansluten**: Välj vilka strömkällor som innebär att enhetens skärm är tänd när den är ansluten.

### <a name="users-and-accounts-settings"></a>Inställningar för användare och konton

- **Lägg till nya användare**: Välj **Blockera** för att förhindra att användarna lägger till nya användare. Varje användare har ett personligt utrymme på enheten för anpassade startskärmar, konton, appar och inställningar. **Inte konfigurerad** (standard) tillåter användare att lägga till andra användare på enheten.
- **Borttagning av användare**: Välj **Blockera** för att förhindra att användarna tar bort användare. **Inte konfigurerad** (standard) tillåter användare att ta bort andra användare från enheten.
- **Konto ändringar** (endast dedikerade enheter): Välj **blockera** för att förhindra att användare ändrar konton. **Inte konfigurerad** (standard) låter användare att uppdatera användarkonton på enheten.

  > [!NOTE]
  > Den här inställningen gäller inte för enhets ägarens (fullständigt hanterade) enheter. Om du konfigurerar den här inställningen ignoreras inställningen och har ingen effekt.

- **Användaren kan konfigurera autentiseringsuppgifter**: **blockera** förhindrar användare från att konfigurera certifikat som har tilldelats till enheter, även enheter som inte är associerade med ett användar konto. **Inte konfigurerad** kan göra det möjligt för användare att konfigurera eller ändra sina autentiseringsuppgifter när de ansluter till dem i nyckel arkivet. 
- **Personliga Google-konton**: **blockera** förhindrar att användare lägger till sina personliga Google-konton på enheten. **Inte konfigurerad** (standard) tillåter användare att lägga till sitt personliga Google-konto.

### <a name="applications"></a>Program

- **Tillåt installation från okända källor**: Välj **Tillåt** för att användarna ska kunna aktivera **Okända källor**. Den här inställningen gör att appar kan installeras från okända källor, inklusive andra källor än Google Play. **Inte konfigurerad** förhindrar användare från att aktivera **Okända källor**.
- **Tillåt åtkomst till alla appar i Google Play-butiken**: När **Tillåt** har valts får användarna åtkomst till alla appar i Google Play. De får inte åtkomst till de appar som har blockerats av administratören i [Klientappar](../apps/apps-add-android-for-work.md). **Inte konfigurerad** tvingar användare att endast använda appar som administratören gjort tillgängliga i Google Play, eller appar som krävs i [Klientappar](../apps/apps-add-android-for-work.md).
- **Automatiska appuppdateringar**: Välj när automatiska uppdateringar ska installeras. Alternativen är:
  - **Inte konfigurerat**
  - **Användarens val**
  - **Aldrig**
  - **Endast Wi-Fi**
  - **Alltid**

### <a name="connectivity"></a>Anslutningar

- **Konstant VPN-anslutning**: Välj **Aktivera** om du vill konfigurera en konstant VPN-klient som automatiskt ansluter och återansluter till VPN. VPN-anslutningar som alltid är aktiva är alltid anslutna eller ansluter direkt när användaren låser sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. 

  Välj **Inte konfigurerad** om du inte vill att VPN-anslutningarna alltid ska vara aktiva. Inställningen tillämpas på alla VPN-klienter.

  > [!IMPORTANT]
  > Var noga med att endast distribuera en princip för VPN som alltid är aktivt för en enskild enhet. Det går inte att distribuera flera principer av den här typen till en enskild enhet.

- **VPN-klient**: Välj en VPN-klient som har stöd för AlwaysOn. Alternativen är:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Anpassad
    - **Paket-ID**: Ange paket-ID:t för appen i Google Play Butik. Om URL:en för appen i Google Play Store exempelvis är `https://play.google.com/store/details?id=com.contosovpn.android.prod` är paket-ID:t `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Den VPN-klient som du väljer måste vara installerad på enheten och den måste ha stöd för ”per app-VPN” i arbetsprofiler. Annars uppstår ett fel. 
  > - Du måste godkänna VPN-klientappen i **den hanterade Google Play Store-butiken**, synkronisera appen till Intune och distribuera appen till enheten. När du har gjort det installeras appen i användarens arbetsprofil.
  > - Du måste fortfarande konfigurera VPN-klienten med en [VPN-profil](vpn-settings-android-enterprise.md)eller via en [konfigurations profil för appen](../apps/app-configuration-policies-use-android.md).
  > - Det kan finnas kända problem när du använder per app-VPN med F5-åtkomst för Android 3.0.4. Du hittar mer information i [Viktig F5-information för F5-åtkomst i Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Låst läge**: Välj **Aktivera** om du vill tvinga all nätverkstrafik att använda VPN-tunneln. Om en anslutning till VPN inte upprättas har inte enheten åtkomst till nätverket.

  Välj **Inte konfigurerad** om du vill tillåta att trafik flödar via VPN-tunneln eller det mobila nätverket.

- **Rekommenderad global proxy**: Välj **Aktivera** för att lägga till en global proxy till enheterna. När den är aktive rad kan HTTP-och HTTPS-trafik, inklusive vissa appar på enheten, använda den proxy som du anger. Den här proxyn är bara en rekommendation. Det är möjligt att vissa appar inte använder proxyn. **Inte konfigurerad** (standard) lägger inte till en rekommenderad global proxy.

  Mer information om den här funktionen finns i [setRecommendedGlobalProxy](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setRecommendedGlobalProxy(android.content.ComponentName,%20android.net.ProxyInfo)) (öppnar en Android-webbplats).

  När det är aktiverat anger du även **typen** av proxy. Alternativen är:

  - **Direkt**: Välj det här alternativet om du vill ange information om proxyservern manuellt, inklusive:
    - **Värd**: Ange värd namnet eller IP-adressen för proxyservern. Ange till exempel `proxy.contoso.com` eller `127.0.0.1`.
    - **Portnummer**: Ange TCP-portnumret som används av proxyservern. Ange till exempel `8080`.
    - **Exkluderade värdar**: Ange en lista över värdnamn eller IP-adresser som inte använder proxyn. Den här listan kan innehålla en asterisk (`*`) som jokertecken och flera värdar avgränsade med semikolon (`;`) utan blank steg. Ange till exempel `127.0.0.1;web.contoso.com;*.microsoft.com`.

  - Autokonfiguration av proxy: ange **PAC-URL** : en för skript för **Automatisk**proxykonfiguration. Ange till exempel `https://proxy.contoso.com/proxy.pac`.

    Mer information om PAC-filer finns i [PAC-fil (Proxy Auto-Configuration](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) ) (öppnar en webbplats som inte kommer från Microsoft).

## <a name="work-profile-only"></a>Endast arbetsprofil

Dessa inställningar gäller för Android Enterprise-registrerings typer där Intune bara styr arbets profilen, t. ex. Android företags arbets profil registrering på en personlig eller en egen enhet (BYOD).

### <a name="work-profile-settings"></a>Inställningar för arbetsprofil

#### <a name="general"></a>Allmänt

- **Kopiera och klistra in mellan arbetsprofiler och personliga profiler**: Välj **Blockera** för att förhindra funktionen att kopiera och klistra in mellan arbetsappar och personliga appar. **Inte konfigurerad** låter användare dela data med hjälp av kopiera och klistra in med appar i den personliga profilen 
- **Datadelning mellan arbetsprofiler och personliga profiler**: Välj om appar i arbetsprofilen ska kunna dela data med appar i den personliga profilen. Du kan till exempel styra delningsåtgärder i program, så som alternativet **Dela...** i Chrome-webbläsarappen. Den här inställningen gäller inte för kopierings- och inklistringsbeteendet i Urklipp. Delningsalternativ:
  - **Standard för enheten**: Detta är standardinställningen för delning av enheten, vilket varierar beroende på Android-version. Som standard tillåts delning från den personliga profilen till arbetsprofilen. Som standard är dessutom delning mellan arbetsprofilen och den personliga profilen blockerad. Den här inställningen förhindrar att arbetsdata delas till den personliga profilen. För enheter som kör version 6.0 och senare blockerar inte Google delning från den personliga profilen till arbetsprofilen.
  - **Appar i arbetsprofilen kan hantera delningsförfrågningar från den personliga profilen**: Aktiverar den inbyggda Android-funktionen som tillåter delning från den personliga profilen till arbetsprofilen. När detta är aktiverat, kan en delningsbegäran från en app i den personliga profilen dela med appar i arbetsprofilen. Det här är standardinställningen för Android-enheter som kör tidigare versioner än 6.0.
  - **Förhindra all delning över gränser**: förhindrar delning mellan arbets profiler och personliga profiler.
  - **Inga begränsningar vid delning**: aktiverar delning över arbets profilens gränser i båda riktningarna. När du väljer den här inställningen så kommer appar i arbetsprofilen att kunna dela data med omärkta appar i den personliga profilen. Med den här inställningen kan hanterade appar i arbetsprofilen dela med appar på den ohanterade delen av enheten. Använd därför den här inställningen med försiktighet.

- **Arbetsprofilmeddelanden när enheten är låst**: Styr om appar i arbetsprofilen får visa data i meddelanden när enheten är låst. **Blockera** visar inte data. **Inte konfigurerad** visar data.
- **Standardappbehörigheter**: Ange standardprincipen för behörighet för alla appar i arbetsprofilen. Från och med Android 6, måste användaren bevilja vissa behörigheter som krävs av appar när appen startas. Den här principinställningen låter dig välja om användare ombeds att bevilja behörigheter för alla appar i arbetsprofilen. Om du till exempel tilldelar en app i arbetsprofilen som kräver platsåtkomst. Normalt skulle den appen be användaren att godkänna eller neka platsåtkomst för appen. Använd den här principen för att automatiskt bevilja behörigheter utan att användaren tillfrågas, för att automatiskt neka behörigheter utan att användaren tillfrågas eller för att låta användaren bestämma. Välj mellan:
  - **Standard för enheten**
  - **Fråga**
  - **Bevilja automatiskt**
  - **Neka automatiskt**

  Du kan också använda en appkonfigurationsprincip för att bevilja behörigheter för enskilda appar (**Klientappar** > **Appkonfigurationsprinciper**).

- **Lägga till och ta bort konton**: Välj **Blockera** för att förhindra att slutanvändarna lägger till eller tar bort konton i arbetsprofilen manuellt. När du till exempel distribuerar Gmail-appen till en Android-arbetsprofil kan du hindra slutanvändare från att lägga till eller ta bort konton i arbetsprofilen. **Inte konfigurerad** tillåter att konton läggs till i arbetsprofilen.  

  > [!NOTE]
  > Google-konton kan inte läggas till i en arbets profil.

- **Kontaktdelning via Bluetooth**: Ger åtkomst till arbetskontakter från en annan enhet, till exempel en bil som har anslutits med Bluetooth. Den här inställningen konfigureras inte som standard och arbetsprofilens kontakter visas därför inte. Välj **Aktivera** för att tillåta denna delning och visa arbetsprofilens kontakter. Inställningen gäller för Androids arbetsprofilenheter i Android OS v6.0 och senare. När den här inställningen är aktiverad kan vissa Bluetooth-enheter tillåtas att cachelagra arbetskontakter vid den första anslutningen. Att inaktiverar den här principen efter en inledande länkning/synkronisering kanske inte kan ta bort arbetskontakter från en bluetooth-enhet.

- **Skärmdump**: Välj **Blockera** för att förhindra skärmbilder eller skärmdumpar på enheten i arbetsprofilen. Förhindrar också att innehållet visas på visningsenheter som inte har en säker videoutgång. **Inte konfigurerad** tillåter skärmbilder.

- **Visa arbetskontaktens nummerpresentation i en personlig profil**: När detta är aktiverat (**Inte konfigurerat**), visas arbetskontaktens nummerpresentation i den personliga profilen. När det är inställt på **Blockera** visas inte arbetskontaktens nummerpresentation i den personliga profilen. Gäller Android OS v6.0 och nyare versioner.

- **Sök arbetskontakter från en personlig profil**: Välj **Blockera** för att förhindra att användarna söker efter arbetskontakter i appar i den personliga profilen. **Krävs inte** tillåter sökningar efter arbetskontakter i den personliga profilen.

- **Kamera**: Välj **Blockera** för att förhindra åtkomst till kameran på enheten i arbetsprofilen. Kameran på den personliga sidan påverkas inte av inställningen. **Krävs inte** tillåter åtkomst till kameran i arbetsprofilen.

- **Tillåt widgetar från appar för arbets profil**: **Aktivera** tillåter att slutanvändare kan skicka widgetar som exponeras av appar på Start skärmen. **Inte konfigurerad** (standard) inaktiverar den här funktionen.

  Outlook är till exempel installerat i användarnas arbets profiler. När inställningen är **aktive**rad kan användarna lägga till Agenda-widgeten på enhetens start sida.

#### <a name="work-profile-password"></a>Lösenord för arbetsprofilen

- **Kräv lösenord för arbetsprofil**: Gäller för Android 7.0 och senare med arbetsprofil aktiverad. Välj **Kräv** för att ange en lösenordsprincip som endast gäller för apparna i arbetsprofilen. Användaren kan som standard välja att använda två separat definierade PIN-koder, eller välja att kombinera PIN-koderna till den starkaste av de två. **Inte konfigurerad** låter användaren använda arbetsappar utan att ange ett lösenord.
- **Minsta lösenordslängd**: Ange det minsta antal tecken som användarens lösenord måste innehålla, från **4**-**16**.
- **Maximalt antal minuter av inaktivitet innan arbetsprofilen låses**: Välj hur lång tid det ska ta innan arbetsprofilen låses. Därefter måste användaren ange sina autentiseringsuppgifter för att få åtkomst igen.
- **Antal felaktiga inloggningar innan enheten rensas**: Anger hur många gånger ett felaktigt lösenord kan anges innan arbetsprofilen rensas från enheten.
- **Lösenordets giltighetstid (dagar)** : Ange antal dagar innan slutanvändarens lösenord måste ändras (från **1**-**255**).
- **Lösenordstyp som krävs**: Välj den typ av lösenord som måste anges på enheten. Välj mellan:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Obligatoriskt**
  - **Minst numeriskt**
  - **Numeriskt avancerat**: Upprepande eller efterföljande siffror som ”1111” eller ”1234” tillåts inte
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**
- **Förhindra återanvändning av tidigare lösenord**: Ange hur många nya lösenord som måste ha använts innan ett gammalt kan återanvändas (från **1**-**24**).
- **Upplåsning med fingeravtryck**: Välj **Blockera** för att förhindra att slutanvändarna använder enhetens fingeravtrycksläsare till att låsa upp den. **Inte konfigurerad** låter användare låsa upp enheter med ett fingeravtryck i arbetsprofilen.
- **Smart Lock och andra betrodda agenter**: Välj **Blockera** för att förhindra Smart Lock och andra betrodda agenter från att ändra låsskärmsinställningar på kompatibla enheter. Med den här funktionen, även kallad förtroendeagent, kan du inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten finns på en betrodd plats. Du kan exempelvis kringgå lösenordet för arbetsprofilen när enheten är ansluten till en specifik Bluetooth-enhet eller när den är nära en NFC-tagg. Använd den här inställningen för att förhindra att användare konfigurerar Smart Lock.

### <a name="device-password"></a>Enhetslösenord

Lösenordsinställningarna gäller för personliga profiler på enheter som använder en arbetsprofil.

- **Minsta lösenordslängd**: Ange det minsta antal tecken som användarens lösenord måste innehålla, från **4**-**14**.
- **Maximalt antal minuter av inaktivitet innan skärmen låses**: Välj hur lång tid det tar innan en inaktiv enhet låses automatiskt
- **Antal felaktiga inloggningar innan enheten rensas**: Anger hur många gånger ett felaktigt lösenord kan anges innan alla data rensas från enheten
- **Lösenordets giltighetstid (dagar)** : Ange antal dagar innan slutanvändarens lösenord måste ändras (från **1**-**255**)
- **Lösenordstyp som krävs**: Välj den typ av lösenord som måste anges på enheten. Välj mellan:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Obligatoriskt**
  - **Minst numeriskt**
  - **Numeriskt avancerat**: Upprepande eller efterföljande siffror som ”1111” eller ”1234” tillåts inte
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**
- **Förhindra återanvändning av tidigare lösenord**: Ange hur många nya lösenord som måste ha använts innan ett gammalt kan återanvändas (från **1**-**24**).
- **Upplåsning med fingeravtryck**: Välj **Blockera** för att förhindra att slutanvändaren använder enhetens fingeravtrycksläsare till att låsa upp den. **Inte konfigurerad** låter användare låsa upp enheten med ett fingeravtryck.
- **Smart Lock och andra betrodda agenter**: Välj **Blockera** för att förhindra Smart Lock och andra betrodda agenter från att ändra låsskärmsinställningar på kompatibla enheter. Med den här funktionen, även kallad förtroendeagent, kan du inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten finns på en betrodd plats. Du kan exempelvis kringgå lösenordet för arbetsprofilen när enheten är ansluten till en specifik Bluetooth-enhet eller när den är nära en NFC-tagg. Använd den här inställningen för att förhindra att användare konfigurerar Smart Lock.

### <a name="system-security"></a>Systemsäkerhet

- **Hotgenomsökning för appar**: **Kräv** innebär att inställningen **Verifiera appar** är aktiverad för arbetsprofiler och personliga profiler.

   > [!Note]
   > Den här inställningen fungerar endast för Android 8 (Oreo)-enheter och senare.

- **Förhindra att appar installeras från okända källor i den personliga profilen**: efter design kan Android Enterprise Work Profile-enheter inte installera appar från andra källor än den Play Store. Av typ är arbets profil enheter avsedda att vara dubbla profiler:

  - En arbets profil som hanteras med MDM.
  - En personlig profil som är isolerad från MDM-hantering.

  Med den här inställningen kan administratörer styra applösenord från okända källor. **Inte konfigurerad** (standard) tillåter att app-installationer från okända källor i den personliga profilen används. **Blockera** förhindrar att program installationer från andra källor än Play Store i den personliga profilen.

### <a name="connectivity"></a>Anslutningar

- **Konstant VPN-anslutning**: Välj **Aktivera** om du vill konfigurera en konstant VPN-klient som automatiskt ansluter och återansluter till VPN. VPN-anslutningar som alltid är aktiva är alltid anslutna eller ansluter direkt när användaren låser sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. 

  Välj **Inte konfigurerad** om du inte vill att VPN-anslutningarna alltid ska vara aktiva. Inställningen tillämpas på alla VPN-klienter.

  > [!IMPORTANT]
  > Var noga med att endast distribuera en princip för VPN som alltid är aktivt för en enskild enhet. Det går inte att distribuera flera principer av den här typen till en enskild enhet.

- **VPN-klient**: Välj en VPN-klient som har stöd för AlwaysOn. Alternativen är:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Anpassad
    - **Paket-ID**: Ange paket-ID:t för appen i Google Play Butik. Om URL:en för appen i Google Play Store exempelvis är `https://play.google.com/store/details?id=com.contosovpn.android.prod` är paket-ID:t `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Den VPN-klient som du väljer måste vara installerad på enheten och den måste ha stöd för ”per app-VPN” i arbetsprofiler. Annars uppstår ett fel. 
  > - Du måste godkänna VPN-klientappen i **den hanterade Google Play Store-butiken**, synkronisera appen till Intune och distribuera appen till enheten. När du har gjort det installeras appen i användarens arbetsprofil.
  > - Det kan finnas kända problem när du använder per app-VPN med F5-åtkomst för Android 3.0.4. Du hittar mer information i [Viktig F5-information för F5-åtkomst i Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Låst läge**: Välj **Aktivera** om du vill tvinga all nätverkstrafik att använda VPN-tunneln. Om en anslutning till VPN inte upprättas har inte enheten åtkomst till nätverket.

  Välj **Inte konfigurerad** om du vill tillåta att trafik flödar via VPN-tunneln eller det mobila nätverket.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan även skapa helskärmslägesprofiler för dedikerade enheter för [Android](device-restrictions-android.md#kiosk)- och [Windows 10](kiosk-settings.md)-enheter.

## <a name="see-also"></a>Se även

[Konfigurera och felsöka Android-företagsenheter i Microsoft Intune](https://support.microsoft.com/help/4476974)
