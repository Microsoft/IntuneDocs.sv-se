---
title: macOS-enhetsinställningar i Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Lägg till, konfigurera eller skapa inställningar på macOS-enheter när du vill begränsa funktioner, till exempel lösenordskrav, kontrollera låst skärm, använda inbyggda appar, lägga till begränsade eller godkända appar, hantera bluetooth-enheter, ansluta till molnet för säkerhetskopiering och lagring, aktivera helskärmsläge, lägga till domäner och kontrollera hur användarna samverkar med Safari-webbläsaren i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a59c40a5f1095e832f84c4b21d553e3c5f11ed7
ms.sourcegitcommit: 464cf677e3746eaba46836dedfb94572a75032f9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58330427"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>macOS-enhetsinställningar för att tillåta eller begränsa funktioner med hjälp av Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de olika inställningar som du kan kontrollera på macOS-enheter. Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar för att tillåta eller inaktivera funktioner, ange lösenordsregler, tillåta eller begränsa specifika appar med mera.

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina macOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en profil för enhetskonfiguration begränsningar](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Allmänt

- **Blockdefinitionssökning**: **Blockera** förhindrar att användare markerar ett ord och sedan söka upp dess definition på enheten. **Inte konfigurerad** (standard) ger åtkomst till definitionssökningsfunktionen.
- **Blockera diktering**: **Blockera** förhindrar att användaren använder röstindata för att ange text. **Inte konfigurerat** (standard) tillåter användaren att använda röstindata.
- **Blockera innehållscachelagring**: Välj **inte konfigurerad** (standard) för att aktivera cachelagring av innehåll. Innehållscachelagring lagrar AppData, webbdata i webbläsaren, nedladdningar och mer lokalt på enheten. Välj **blockera** att förhindra att dessa data lagras i cacheminnet.

  Mer information om cachelagring av innehåll på macOS finns [hantera cachelagring av innehåll på Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (öppnas en annan webbplats).

  Den här funktionen gäller för:  
  - macOS 10.13 och senare

- **Skjuta upp programuppdateringar**: när **inte konfigurerad** (standard), programuppdateringar visas på enheten som Apple släpper dem.. Till exempel om en uppdatering av macOS hämtar släpps av Apple på ett specifikt datum, visas sedan uppdateringen naturligt på enheten runt lanseringsdatumet. Startvärdesklassen build uppdateringar tillåts utan fördröjning.

  **Aktivera** gör att du kan fördröja när programuppdateringar visas på enheter, från 0 – 90 dagar. Den här inställningen styr inte när uppdateringar är eller inte är installerade. 

  - **Fördröjning synligheten för programuppdateringar**: Ange ett värde mellan 0 – 90 dagar. När fördröjningen upphör får användarna ett meddelande om att uppdatera till den tidigaste versionen av OS som var tillgänglig när fördröjningen utlöstes.

    Exempel: om en macOS-uppdateringar är tillgängliga på **1 januari**, och **fördröjning synlighet** är inställd på **5 dagar**, och sedan uppdateringen inte visas som en tillgänglig uppdatering på enheter. På den **sjätte dagen** efter utgivningen att uppdateringen är tillgänglig och slutanvändare kan installera den.

    Den här funktionen gäller för:  
    - macOS 10.13.4 och senare

## <a name="password"></a>Lösenord

- **Lösenord**: **Kräv** att slutanvändaren måste ange ett lösenord för att få åtkomst till enheten. **Inte konfigurerad** (standard) inte kräver ett lösenord och inte framtvinga några begränsningar, till exempel blockerar enkla lösenord eller ange en minsta längd.
  - **Krav på lösenordstyp**: Ange om lösenordet kan bestå av endast numeriska tecken om det måste vara alfanumeriskt (innehålla bokstäver och siffror). Den här inställningen stöds endast i Mac OS X version 10.10.3 och senare.
  - **Antal icke-alfanumeriska tecken i lösenord**: Ange antalet avancerade tecken i lösenordet (**0** till **4**).<br>Ett avancerat tecken är en symbol, t.ex. ”**?**”.
  - **Minsta längd på lösenord**: Ange den minsta längd på lösenord som en användare måste konfigurera (mellan **4** och **16** tecken).
  - **Enkla lösenord**: Låt användarna skapa enkla lösenord, till exempel **0000** eller **1234**.
  - **Största antal minuter innan lösenord krävs efter det att skärmen låsts**: Ange hur länge datorn måste vara inaktiv innan ett lösenord krävs för att låsa upp den.
  - **Maximalt antal minuter av inaktivitet innan skärmen låses**: Anger hur lång tid datorn måste vara i viloläge innan skärmen låses.
  - **Lösenordets giltighetstid (i dagar)**: Ange efter hur många dagar användaren måste byta lösenord (**1** till **255** dagar).
  - **Förhindra återanvändning av tidigare lösenord**: Ange det antal tidigare lösenord som inte får återanvändas, från **1** till **24**.

- **Blockera användaren från att ändra lösenordet**: Välj **blockera** att stoppa lösenordet ändras, har lagts till eller har tagits bort. **Inte konfigurerad** (standard) tillåter att lösenord läggs till, ändras eller tas bort.
- **Blockera upplåsning med fingeravtryck**: Välj **Blockera** om du vill förhindra att fingeravtryck används för att låsa upp enheten. **Inte konfigurerad** (standard) tillåter att användare låser upp enheten med ett fingeravtryck.

- **Blockera automatisk ifyllning av lösenord**: Förhindra användningen av funktionen för automatisk ifyllning av lösenord i macOS genom att välja **Blockera**. Välja **blockera** har också följande påverkan:

  - Användarna ombeds inte att använda ett sparat lösenord i Safari eller i någon app.
  - Automatisk starka lösenord inaktiveras och starka lösenord föreslås inte för användare.

  **Inte konfigurerat** (standard) tillåter dessa funktioner.

- **Blockera förfrågningar om lösenordsnärhet**: Välj **Blockera** så att användarens enhet inte begär lösenord från enheter i närheten. **Inte konfigurerad** (standard) tillåter dessa lösenordsbegäranden.

- **Blockera lösenordsdelning**: **Blockera** förhindrar att lösenord delas mellan enheter med hjälp av AirDrop. **Inte konfigurerad** (standard) tillåter att lösenord delas.

## <a name="built-in-apps"></a>Inbyggda appar

- **Blockera Autofyll i Safari**: **Blockera** inaktiverar funktionen Autofyll i Safari på enheten. **Inte konfigurerad** (standard) tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren.
- **Blockera kamera**: Välj **Blockera** om du vill förhindra åtkomst till enhetens kamera. **Inte konfigurerad** (standard) ger åtkomst till enhetens kamera.
- **Blockera Apple Music**: **Blockera** återställer appen Apple Music till klassiskt läge och inaktiverar tjänsten Musik. **Inte konfigurerad** (standard) tillåter att Apple Music-appen används.
- **Blockera Spotlight-Internetresultat Search**: **blockera** stoppar Spotlight från att returnera alla resultat från en Internetsökning. **Inte konfigurerad** (standard) tillåter att Spotlight-sökningar ansluter till Internet för att visa sökresultat.
- **Blockera filöverföring med iTunes**: **blockera** inaktiverar application services för fildelning. Tillgänglig i macOS 10.13 och senare. **Inte konfigurerad** (standard) gör programmet tjänster för fildelning.

## <a name="restricted-apps"></a>Begränsade appar

Du kan konfigurera en av följande listor i listan med begränsade appar:

- Listan **Otillåtna appar**: Ange de appar som inte hanteras av Intune och som användarna inte får installera och köra. Användarna inte är inte installera en förbjuden app, men om de gör det rapporteras till administratören.
- Listan **Godkända appar**: Ange de appar som användare tillåts att installera. Användarna får inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt. Användarna inte är inte installera en app som inte finns med i listan över godkända. Men om de gör det rapporteras till administratören.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare, och appens samlings-ID (t.ex. *com.apple.calculator*).

## <a name="connected-devices"></a>Anslutna enheter

- **Blockera AirDrop**: **Blockera** förhindrar att AirDrop används på enheten. **Inte konfigurerad** (standard) tillåter att funktionen AirDrop används för att utbyta innehåll med enheter i närheten.
- **Blockera Apple Watch automatisk upplåsning**: **blockera** förhindrar användare från att låsa upp sina macOS-enheter med sin Apple Watch. **Inte konfigurerad** (standard) kan du låsa upp sina macOS-enheter med sin Apple Watch.

## <a name="cloud-and-storage"></a>Moln och lagring

- **Blockera synkronisering av iCloud-nyckelring**: Välj **Blockera** om du vill inaktivera synkronisering av autentiseringsuppgifter som lagras i nyckelringen till iCloud. **Inte konfigurerad** (standard) tillåter användare att synkronisera dessa autentiseringsuppgifter.
- **Blockera iCloud Dokumentsynkronisering**: **blockera** förhindrar att synkronisera dokument och data i iCloud. **Inte konfigurerad** (standard) tillåter synkronisering av dokument och nyckelvärden till ditt iCloud-lagringsutrymme.
- **Blockera iCloud-säkerhetskopiering för e-post**: **blockera** förhindrar att synkroniseras med e-postprogrammet macOS i iCloud. **Inte konfigurerad** (standard) tillåter e-postsynkronisering till iCloud.
- **Blockera iCloud-säkerhetskopiering Kontakta**: **blockera** förhindrar att iCloud synkronisering av kontakter för enheter. **Inte konfigurerad** (standard) tillåter synkronisering av kontakter med hjälp av iCloud.
- **Blockera iCloud-säkerhetskopiering kalender**: **blockera** förhindrar iCloud från att synkronisera med appen macOS kalender. **Inte konfigurerad** (standard) tillåter Kalendersynkronisering till iCloud.
- **Blockera iCloud-säkerhetskopiering påminnelse**: **blockera** förhindrar iCloud från att synkronisera med macOS påminnelser appen. **Inte konfigurerad** (standard) tillåter påminnelser synkronisering till iCloud.
- **Blockera iCloud-säkerhetskopiering bokmärke**: **blockera** förhindrar att synkronisera enheter bokmärken i iCloud. **Inte konfigurerad** (standard) tillåter bokmärke synkronisering till iCloud.
- **Blockera iCloud-säkerhetskopiering anteckningar**: **blockera** förhindrar att synkronisera enheter anteckningar i iCloud. **Inte konfigurerad** (standard) tillåter synkronisering av anteckningar till iCloud.

## <a name="domains"></a>Domains

- **Webbadress till e-postdomän**: Lägg till en eller flera webbadresser i listan. När slutanvändarna får ett e-postmeddelande från en annan domän än den du har konfigurerat, markeras e-postmeddelandet som ej betrott i MacOS-e-postappen.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också begränsa enhetens funktioner och inställningar på [iOS](device-restrictions-ios.md) enheter.
