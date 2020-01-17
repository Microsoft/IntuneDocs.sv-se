---
title: macOS-enhetsinställningar i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till, konfigurera eller skapa inställningar på macOS-enheter när du vill begränsa funktioner, till exempel lösenordskrav, kontrollera låst skärm, använda inbyggda appar, lägga till begränsade eller godkända appar, hantera bluetooth-enheter, ansluta till molnet för säkerhetskopiering och lagring, aktivera helskärmsläge, lägga till domäner och kontrollera hur användarna samverkar med Safari-webbläsaren i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6513c09f252d5a914ace4e57e5a593877a387172
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206558"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>macOS-enhetsinställningar för att tillåta eller begränsa funktioner med hjälp av Intune



I den här artikeln beskrivs de olika inställningar som du kan kontrollera på macOS-enheter. Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar för att tillåta eller inaktivera funktioner, ange lösenordsregler, tillåta eller begränsa specifika appar med mera.

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina macOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en konfigurationsprofil för enhetsbegränsningar](../device-restrictions-configure.md).

> [!NOTE]
> De här inställningarna gäller för olika registrerings typer. Mer information om de olika registrerings typerna finns i [MacOS-registrering](../macos-enroll.md).

## <a name="general"></a>Allmänt

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: enhets registrering och automatisk enhets registrering

- **Slå upp definition**: **Blockera** förhindrar användare från att markera ett ord och sedan söka upp dess definition på enheten. **Inte konfigurerad** (standard) ger åtkomst till definitionssökningsfunktionen.
- **Diktering**: **Blockera** hindrar användaren från att använda röstindata för att ange text. **Inte konfigurerat** (standard) tillåter användaren att använda röstindata.
- **Cachelagring av innehåll**: Välj **Inte konfigurerad** (standard) för att aktivera cachelagring av innehåll. Innehållscachelagring lagrar till exempel appdata, data i webbläsaren och nedladdningar lokalt på enheten. Välj **Blockera** om du vill förhindra att dessa data lagras i cacheminnet.

  Mer information om cachelagring av innehåll på macOS finns i [Hantera cachelagring av innehåll på Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (en annan webbplats öppnas).

  Den här funktionen gäller för:  
  - macOS 10.13 och senare

- **Skjut upp programuppdateringar**: När **Inte konfigurerad** (standard) används visas programuppdateringar på enheten när de ges ut av Apple. Om Apple exempelvis ger ut en macOS-uppdatering på ett specifikt datum, visas uppdateringen på enheten runt utgivningsdatumet. Startuppsättningar av versionsuppdateringar tillåts utan fördröjning.

  **Aktivera** gör att du kan skjuta upp visningen av programuppdateringar på enheter i 0–90 dagar. Den här inställningen styr inte när uppdateringar installeras eller inte. 

  - **Fördröj visning av programuppdateringar**: Ange ett värde mellan 0–90 dagar. När fördröjningen upphör får användarna ett meddelande om att uppdatera till den tidigaste versionen av OS som var tillgänglig när fördröjningen utlöstes.

    Exempel: Om en macOS-uppdatering är tillgänglig **den 1 januari** och **Fördröjd visning** är inställt på **5 dagar**, så visas inte uppdateringen som en tillgänglig uppdatering. På **den sjätte dagen** efter utgivningen är uppdateringen tillgänglig och slutanvändarna kan installera den.

    Den här funktionen gäller för:  
    - macOS 10.13.4 och senare

- **Skärm bilder**: enheten måste vara registrerad i Apples automatiserad enhets registrering (DEP). När inställningen **blockeras**kan användarna inte spara en skärm bild av visningen. Det förhindrar också att klass rummets app styr fjärrskärmar. **Inte konfigurerad** (standard) gör att användare kan samla in skärm bilder och att appen klass rummet kan visa fjärrskärmar.

### <a name="settings-apply-to-automated-device-enrollment"></a>Inställningarna gäller för: automatisk enhets registrering

- **Fjärrstyrd skärm genom program klass**: **inaktivera** hindrar lärare från att använda klass rummets app för att se sina studenters skärmar. **Inte konfigurerad** (standard) låter lärare se sina studenters skärmar.

  Om du vill använda den här inställningen anger du **skärm** bilds inställningen till **inte konfigurerad** (skärm bilder tillåts).

- **Skärm visning utan uppmaning i program klass rummet**: **Tillåt** låter lärare se sina studenters skärmar utan att behöva enas om att komma över från studenten. **Inte konfigurerad** (standard) kräver att studenten samtycker till att läraren kan se skärmarna.

  Om du vill använda den här inställningen anger du **skärm** bilds inställningen till **inte konfigurerad** (skärm bilder tillåts).

- **Studenter måste begära behörighet att lämna klass rums klassen**: **kräver** tvingar studenter som är registrerade i en ohanterad klass rums kurs för att få ett godkännande för lärare att lämna kursen. **Inte konfigurerad** (standard) gör att student kan lämna kursen varje gång studenten väljer.

- **Lärare kan automatiskt låsa enheter eller appar i klass rums appen**: **Tillåt att** lärare låser en students enhet eller app utan student godkännande. **Inte konfigurerad** (standard) kräver att studenten samtycker till att läraren kan låsa enheten eller appen.

- **Studenter kan automatiskt ansluta klass rums klassen**: **Tillåt att** studenter ansluter till en klass utan att behöva lämna läraren. **Inte konfigurerad** (standard) kräver godkännande av lärare för att ansluta till en klass.

## <a name="password"></a>lösenordsinställning

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: enhets registrering och automatisk enhets registrering

- **Lösenord**: Slutanvändaren **måste** ange ett lösenord för att få åtkomst till enheten. **Inte konfigurerat** (standard) kräver inget lösen ord. Det gäller inte heller några begränsningar, till exempel att blockera enkla lösen ord eller att ange en minimal längd.
  - **Lösenordstyp som krävs**: Ange om lösenordet kan vara endast Numeriskt eller om det måste vara Alfanumeriskt (innehålla bokstäver och siffror).

    Den här funktionen gäller för:  
    - macOS 10.10.3 och senare

  - **Antal icke-alfanumeriska tecken i lösenord**: Ange det antal avancerade tecken som krävs i lösenordet (**0** till **4**).<br>Ett avancerat tecken är en symbol, t.ex. ” **?** ”.
  - **Minsta lösenordslängd**: Ange den minsta längden på lösenord som en användare måste konfigurera (mellan **4** och **16** tecken).
  - **Enkla lösenord**: Låt användarna skapa enkla lösenord som **0000** eller **1234**.
  - **Maximalt antal minuter efter skärmlås innan ett lösenord krävs**: Ange hur länge datorn måste vara inaktiv innan ett lösenord krävs för att låsa upp den.
  - **Maximalt antal minuter av inaktivitet innan skärmen låses**: Anger hur lång tid datorn måste vara i viloläge innan skärmen låses.
  - **Lösenordets giltighetstid (dagar)** : Ange efter hur många dagar användaren måste byta lösenord (**1** till **255** dagar).
  - **Förhindra återanvändning av tidigare lösenord**: Ange antal tidigare använda lösenord som inte får återanvändas, från **1** till **24**.

- **Blockera användare från att ändra lösenkod**: Välj **Blockera** om du vill förhindra att lösenkoden ändras, läggs till eller tas bort. **Inte konfigurerad** (standard) tillåter att lösenord läggs till, ändras eller tas bort.
- **Blockera upplåsning med fingeravtryck**: Välj **Blockera** om du vill förhindra att fingeravtryck används för att låsa upp enheten. **Inte konfigurerad** (standard) tillåter att användare låser upp enheten med ett fingeravtryck.

- **Blockera automatisk ifyllning av lösenord**: Förhindra användningen av funktionen för automatisk ifyllning av lösenord i macOS genom att välja **Blockera**. Inställningen **Blockera** har också följande effekt:

  - Användarna ombeds inte att använda ett sparat lösenord i Safari eller i någon app.
  - Automatisk starka lösenord inaktiveras och starka lösenord föreslås inte för användare.

  **Inte konfigurerat** (standard) tillåter dessa funktioner.

- **Blockera förfrågningar om lösenordsnärhet**: Välj **Blockera** så att användarens enhet inte begär lösenord från enheter i närheten. **Inte konfigurerad** (standard) tillåter dessa lösenordsbegäranden.

- **Blockera lösenordsdelning**: **Blockera** förhindrar att lösenord delas mellan enheter med hjälp av AirDrop. **Inte konfigurerad** (standard) tillåter att lösenord delas.

## <a name="built-in-apps"></a>Inbyggda appar

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: enhets registrering och automatisk enhets registrering

- **Blockera autofyll i Safari**: **Blockera** inaktiverar funktionen Autofyll i Safari på enheten. **Inte konfigurerad** (standard) tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren.
- **Blockera kamera**: Välj **Blockera** om du vill förhindra åtkomst till enhetens kamera. **Inte konfigurerad** (standard) ger åtkomst till enhetens kamera.
- **Blockera Apple Music**: **Blockera** återställer appen Apple Music till klassiskt läge och inaktiverar tjänsten Musik. **Inte konfigurerad** (standard) tillåter att Apple Music-appen används.
- **Blockera Internetsökresultat i Spotlight**: **Blockera** förhindrar Spotlight från att returnera resultat från sökningar på Internet. **Inte konfigurerad** (standard) tillåter att Spotlight-sökningar ansluter till Internet för att visa sökresultat.
- **Blockera filöverföring via iTunes**: **Blockera** inaktiverar fildelningstjänster för program. **Inte konfigurerad** (standard) tillåter fildelningstjänster för program.

  Den här funktionen gäller för:  
  - macOS 10.13 och senare

## <a name="restricted-apps"></a>Begränsade appar

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: enhets registrering och automatisk enhets registrering

- **Lista över typer av begränsade appar**: skapa en lista över appar som användarna inte får installera eller använda. Alternativen är:

  - **Inte konfigurerat** (standard): det finns inga begränsningar från Intune. Användare har åtkomst till appar som du tilldelar och inbyggda appar.
  - **Otillåtna appar**: Appar som inte hanteras av Intune som du inte vill ha installerade på enheten. Användare hindras inte från att installera en förbjuden app. Men om en användare installerar en app från den här listan, rapporteras den i Intune.
  - **Godkända appar**: Appar som användare tillåts att installera. Användarna får inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt. Användarna hindras inte från att installera en app som inte finns med i listan över godkända appar. Men om de gör det rapporteras de i Intune.
- **Appsamlings-ID**: Ange [appsamlings-ID](bundle-ids-built-in-ios-apps.md) för den app som du vill lägga till. Du kan visa eller dölja inbyggda appar och branschspecifika appar. På Apples webbplats finns en lista över [inbyggda Apple-appar](https://support.apple.com/HT208094).
- **Appnamn**: Ange namnet på den app som du vill lägga till. Du kan visa eller dölja inbyggda appar och branschspecifika appar. På Apples webbplats finns en lista över [inbyggda Apple-appar](https://support.apple.com/HT208094).
- **Utgivare**: Ange namnet på den utgivare som du vill lägga till.

Om du vill lägga till appar i listorna kan du:

- **Lägg till**: Välj om du vill skapa en lista över appar.
- **Importera** en CSV-fil med information om appen, inklusive webbadressen. Använd formatet `<app bundle ID>, <app name>, <app publisher>`. Eller **Exportera** för att skapa en lista över appar som du har lagt till i samma format.

## <a name="connected-devices"></a>Anslutna enheter

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: enhets registrering och automatisk enhets registrering

- **Blockera AirDrop**: **Blockera** förhindrar att du använder AirDrop på enheten. **Inte konfigurerad** (standard) tillåter att funktionen AirDrop används för att utbyta innehåll med enheter i närheten.
- **Blockera automatisk upplåsning av Apple Watch**: **Blockera** hindrar användaren från att låsa upp en macOS-enhet med Apple Watch. **Inte konfigurerad** (standard) tillåter att användaren låser upp en macOS-enhet med Apple Watch.

## <a name="cloud-and-storage"></a>Moln och lagring

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: enhets registrering och automatisk enhets registrering

- **Blockera synkronisering av iCloud-nyckelring**: Välj **Blockera** om du vill inaktivera synkronisering av autentiseringsuppgifter som lagras i nyckelringen till iCloud. **Inte konfigurerad** (standard) tillåter användare att synkronisera dessa autentiseringsuppgifter.
- **Blockera synkronisering av iCloud-dokument**: **Blockera** förhindrar iCloud från att synkronisera dokument och data. **Inte konfigurerad** (standard) tillåter synkronisering av dokument och nyckelvärden till ditt iCloud-lagringsutrymme.
- **Blockera säkerhetskopiering av Mail i iCloud**: **Blockera** förhindrar att iCloud synkroniseras med e-postprogrammet i macOS. **Inte konfigurerad** (standard) tillåter e-postsynkronisering med iCloud.
- **Blockera säkerhetskopiering av Kontakter i iCloud**: **Blockera** förhindrar att iCloud synkroniserar kontakter på enheten. **Inte konfigurerad** (standard) tillåter synkronisering av kontakter med iCloud.
- **Blockera säkerhetskopiering av Kalender i iCloud**: **Blockera** förhindrar att iCloud synkroniserar kalenderappen i macOS. **Inte konfigurerad** (standard) tillåter kalendersynkronisering med iCloud.
- **Blockera säkerhetskopiering av Påminnelser i iCloud**: **Blockera** förhindrar att iCloud synkroniserar påminnelseappen i macOS. **Inte konfigurerad** (standard) tillåter synkronisering av påminnelser med iCloud.
- **Blockera säkerhetskopiering av Bokmärken i iCloud**: **Blockera** förhindrar att iCloud synkroniserar bokmärken på enheter. **Inte konfigurerad** (standard) tillåter synkronisering av bokmärken med iCloud.
- **Blockera säkerhetskopiering av Anteckningar i iCloud**: **Blockera** förhindrar att iCloud synkroniserar anteckningar på enheter. **Inte konfigurerad** (standard) tillåter synkronisering av anteckningar med iCloud.
- **Blockera iCloud-bildbibliotek**: **block** inaktiverar iCloud-bildbibliotek och hindrar iCloud från att synkronisera enheternas foton. Alla bilder som inte har laddats ned till fullo från iCloud-bildbiblioteket tas bort från enhetens lokala lagringsutrymme. **Inte konfigurerad** (standard) tillåter synkronisering av foton mellan enheten och iCloud-bildbiblioteket.
- **Leverans**: **inte konfigurerat** (standard) gör att användare kan börja arbeta på en MacOS-enhet och sedan fortsätta att arbeta på en annan iOS-eller MacOS-enhet. **Blockera** förhindrar funktionen för leverans på enheten. 

  Den här funktionen gäller för:  
  - macOS 10.15 och senare

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Inställningarna gäller för: enhets registrering och automatisk enhets registrering

- **Webbadress till e-postdomän**: **Lägg till** en eller flera webbadresser i listan. När slutanvändarna får ett e-postmeddelande från en annan domän än den du har konfigurerat, markeras e-postmeddelandet som ej betrott i macOS-e-postappen.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

Du kan också begränsa enhetens funktioner och inställningar på [iOS](../device-restrictions-ios.md)-enheter.
