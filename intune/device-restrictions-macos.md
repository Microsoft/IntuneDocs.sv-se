---
title: macOS-enhetsinställningar i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
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
ms.openlocfilehash: 5feec66e791da4038bd069cdad69a7ba573f27f3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798385"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>macOS-enhetsinställningar för att tillåta eller begränsa funktioner med hjälp av Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de olika inställningar som du kan kontrollera på macOS-enheter. Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar för att tillåta eller inaktivera funktioner, ange lösenordsregler, tillåta eller begränsa specifika appar med mera.

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina macOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en konfigurationsprofil för enhetsbegränsningar](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Allmänt

- **Blockdefinitionssökning**: **Blockera** förhindrar att användare markerar ett ord och sedan söka upp dess definition på enheten. **Inte konfigurerad** (standard) ger åtkomst till definitionssökningsfunktionen.
- **Blockera diktering**: **Blockera** förhindrar att användaren använder röstindata för att ange text. **Inte konfigurerat** (standard) tillåter användaren att använda röstindata.
- **Blockera innehållscachelagring**: Välj **Inte konfigurerad** (standard) för att aktivera cachelagring av innehåll. Innehållscachelagring lagrar till exempel appdata, data i webbläsaren och nedladdningar lokalt på enheten. Välj **Blockera** om du vill förhindra att dessa data lagras i cacheminnet.

  Mer information om cachelagring av innehåll på macOS finns i [Hantera cachelagring av innehåll på Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (en annan webbplats öppnas).

  Den här funktionen gäller för:  
  - macOS 10.13 och senare

- **Skjut upp programuppdateringar**: När **Inte konfigurerad** (standard) används visas programuppdateringar på enheten när de ges ut av Apple. Om Apple exempelvis ger ut en macOS-uppdatering på ett specifikt datum, visas uppdateringen på enheten runt utgivningsdatumet. Startuppsättningar av versionsuppdateringar tillåts utan fördröjning.

  **Aktivera** gör att du kan skjuta upp visningen av programuppdateringar på enheter i 0–90 dagar. Den här inställningen styr inte när uppdateringar installeras eller inte. 

  - **Fördröj visning av programuppdateringar**: Ange ett värde mellan 0 och 90 dagar. När fördröjningen upphör får användarna ett meddelande om att uppdatera till den tidigaste versionen av OS som var tillgänglig när fördröjningen utlöstes.

    Exempel: Om en macOS-uppdatering är tillgänglig **den 1 januari** och **Fördröjd visning** är inställt på **5 dagar**, så visas inte uppdateringen som en tillgänglig uppdatering på enheter. På **den sjätte dagen** efter utgivningen är uppdateringen tillgänglig och slutanvändarna kan installera den.

    Den här funktionen gäller för:  
    - macOS 10.13.4 och senare

## <a name="password"></a>Lösenord

- **Lösenord**: **Kräv** att slutanvändaren måste ange ett lösenord för att få åtkomst till enheten. **Inte konfigurerad** (standard) kräver inget lösenord eller begränsningar, till exempel blockering av enkla lösenord eller konfiguration av en minsta längd.
  - **Krav på lösenordstyp**: Ange om lösenordet kan bestå av endast numeriska tecken om det måste vara alfanumeriskt (innehålla bokstäver och siffror). Den här inställningen stöds endast i Mac OS X version 10.10.3 och senare.
  - **Antal icke-alfanumeriska tecken i lösenord**: Ange antalet avancerade tecken i lösenordet (**0** till **4**).<br>Ett avancerat tecken är en symbol, t.ex. ”**?**”.
  - **Minsta längd på lösenord**: Ange den minsta längd på lösenord som en användare måste konfigurera (mellan **4** och **16** tecken).
  - **Enkla lösenord**: Låt användarna skapa enkla lösenord, till exempel **0000** eller **1234**.
  - **Största antal minuter innan lösenord krävs efter det att skärmen låsts**: Ange hur länge datorn måste vara inaktiv innan ett lösenord krävs för att låsa upp den.
  - **Maximalt antal minuter av inaktivitet innan skärmen låses**: Anger hur lång tid datorn måste vara i viloläge innan skärmen låses.
  - **Lösenordets giltighetstid (i dagar)**: Ange efter hur många dagar användaren måste byta lösenord (**1** till **255** dagar).
  - **Förhindra återanvändning av tidigare lösenord**: Ange det antal tidigare lösenord som inte får återanvändas, från **1** till **24**.

- **Block User from Modifying Passcode** (Förhindra att användare ändrar lösenord): Välj **Blockera** för att förhindra att lösenordet ändras, läggs till eller tas bort. **Inte konfigurerad** (standard) tillåter att lösenord läggs till, ändras eller tas bort.
- **Blockera upplåsning med fingeravtryck**: Välj **Blockera** om du vill förhindra att fingeravtryck används för att låsa upp enheten. **Inte konfigurerad** (standard) tillåter att användare låser upp enheten med ett fingeravtryck.

- **Blockera automatisk ifyllning av lösenord**: Förhindra användningen av funktionen för automatisk ifyllning av lösenord i macOS genom att välja **Blockera**. Inställningen **Blockera** har också följande effekt:

  - Användarna ombeds inte att använda ett sparat lösenord i Safari eller i någon app.
  - Automatisk starka lösenord inaktiveras och starka lösenord föreslås inte för användare.

  **Inte konfigurerat** (standard) tillåter dessa funktioner.

- **Blockera förfrågningar om lösenordsnärhet**: Välj **Blockera** så att användarens enhet inte begär lösenord från enheter i närheten. **Inte konfigurerad** (standard) tillåter dessa lösenordsbegäranden.

- **Blockera lösenordsdelning**: **Blockera** förhindrar att lösenord delas mellan enheter med hjälp av AirDrop. **Inte konfigurerad** (standard) tillåter att lösenord delas.

## <a name="built-in-apps"></a>Inbyggda appar

- **Blockera Autofyll i Safari**: **Blockera** inaktiverar funktionen Autofyll i Safari på enheten. **Inte konfigurerad** (standard) tillåter att användarna ändrar inställningarna för att komplettera automatiskt i webbläsaren.
- **Blockera kamera**: Välj **Blockera** om du vill förhindra åtkomst till enhetens kamera. **Inte konfigurerad** (standard) ger åtkomst till enhetens kamera.
- **Blockera Apple Music**: **Blockera** återställer appen Apple Music till klassiskt läge och inaktiverar tjänsten Musik. **Inte konfigurerad** (standard) tillåter att Apple Music-appen används.
- **Block Spotlight Internet Search Results** (Blockera resultat från Internetsökningar i Spotlight): **Blockera** hindrar Spotlight från att returnera resultat från en Internetsökning. **Inte konfigurerad** (standard) tillåter att Spotlight-sökningar ansluter till Internet för att visa sökresultat.
- **Block File Transfer using iTunes** (Blockera filöverföringar med iTunes): **Blockera** inaktiverar fildelningstjänster för program. Tillgängligt i macOS 10.13 och senare. **Inte konfigurerad** (standard) tillåter fildelningstjänster för program.

## <a name="restricted-apps"></a>Begränsade appar

Du kan konfigurera en av följande listor i listan med begränsade appar:

- Listan **Otillåtna appar**: Ange de appar som inte hanteras av Intune och som användarna inte får installera och köra. Användarna hindras inte från att installera en förbjuden app, men om de gör det rapporteras detta till administratören.
- Listan **Godkända appar**: Ange de appar som användare tillåts att installera. Användarna får inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt. Användarna hindras inte från att installera en app som inte finns med i listan över godkända appar. Men om de gör det rapporteras detta till administratören.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare, och appens samlings-ID (t.ex. *com.apple.calculator*).

## <a name="connected-devices"></a>Anslutna enheter

- **Blockera AirDrop**: **Blockera** förhindrar att AirDrop används på enheten. **Inte konfigurerad** (standard) tillåter att funktionen AirDrop används för att utbyta innehåll med enheter i närheten.
- **Block Apple Watch Auto Unlock** (Blockera automatisk upplåsning av Apple Watch): **Blockera** hindrar användaren från att låsa upp en macOS-enhet med Apple Watch. **Inte konfigurerad** (standard) tillåter att användaren låser upp en macOS-enhet med Apple Watch.

## <a name="cloud-and-storage"></a>Moln och lagring

- **Blockera synkronisering av iCloud-nyckelring**: Välj **Blockera** om du vill inaktivera synkronisering av autentiseringsuppgifter som lagras i nyckelringen till iCloud. **Inte konfigurerad** (standard) tillåter användare att synkronisera dessa autentiseringsuppgifter.
- **Block iCloud Document Sync** (Blockera dokumentsynkronisering med iCloud): **Blockera** förhindrar att iCloud synkroniserar dokument och data. **Inte konfigurerad** (standard) tillåter synkronisering av dokument och nyckelvärden till ditt iCloud-lagringsutrymme.
- **Block iCloud Mail Backup** (Blockera säkerhetskopiering av e-post med iCloud): **Blockera** förhindrar att iCloud synkroniseras med e-postprogrammet i macOS. **Inte konfigurerad** (standard) tillåter e-postsynkronisering med iCloud.
- **Block iCloud Contact Backup** (Blockera säkerhetskopiering av kontakter med iCloud): **Blockera** förhindrar att iCloud synkroniserar kontakter på enheten. **Inte konfigurerad** (standard) tillåter synkronisering av kontakter med iCloud.
- **Block iCloud Calendar Backup** (Blockera säkerhetskopiering av kalendern med iCloud): **Blockera** förhindrar att iCloud synkroniserar kalenderappen i macOS. **Inte konfigurerad** (standard) tillåter kalendersynkronisering med iCloud.
- **Block iCloud Reminder Backup** (Blockera säkerhetskopiering av påminnelser med iCloud): **Blockera** förhindrar att iCloud synkroniserar påminnelseappen i macOS. **Inte konfigurerad** (standard) tillåter synkronisering av påminnelser med iCloud.
- **Block iCloud Bookmark Backup** (Blockera säkerhetskopiering av bokmärken med iCloud): **Blockera** förhindrar att iCloud synkroniserar bokmärken på enheter. **Inte konfigurerad** (standard) tillåter synkronisering av bokmärken med iCloud.
- **Block iCloud Notes Backup** (Blockera säkerhetskopiering av anteckningar med iCloud): **Blockera** förhindrar att iCloud synkroniserar anteckningar på enheter. **Inte konfigurerad** (standard) tillåter synkronisering av anteckningar med iCloud.

## <a name="domains"></a>Domains

- **Webbadress till e-postdomän**: Lägg till en eller flera webbadresser i listan. När slutanvändarna får ett e-postmeddelande från en annan domän än den du har konfigurerat, markeras e-postmeddelandet som ej betrott i MacOS-e-postappen.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också begränsa enhetens funktioner och inställningar på [iOS](device-restrictions-ios.md)-enheter.
