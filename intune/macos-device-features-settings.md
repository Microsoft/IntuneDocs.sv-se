---
title: Funktionsinställningar för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se inställningarna för att konfigurera macOS-enheter för AirPrint och anpassa inloggningsfönstret för att visa eller dölja strömknappar i Microsoft Intune. Se även anvisningar för att hämta IP-adress, sökväg och portinställningar för en AirPrint-server i nätverket. Använd dessa inställningar i en enhetskonfigurationsprofil när du konfigurerar funktioner för macOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1826498b3bfa2191900d7574f79051af8f758558
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041706"
---
# <a name="macos-device-feature-settings-in-intune"></a>Funktionsinställningar för macOS-enheter i Intune

I Intune finns vissa inbyggda inställningar för att anpassa funktioner i dina macOS-enheter. I den här artikeln visas inställningarna, tillsammans med en beskrivning av vad varje inställning gör. Här visas även anvisningar för att hämta IP-adress, sökväg och port för AirPrint-skrivare som använder Terminal-appen (emulator).

Den här funktionen gäller för:

- macOS

Du kan använda dessa inställningar som en del i din MDM-lösning (hantering av mobilenheter) för att till exempel skapa en banderoll, välja hur användarna ska logga in och lägga till en AirPrint-server.

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina macOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en macOS-enhetskonfigurationsprofil](device-features-configure.md).

## <a name="airprint"></a>AirPrint

- **IP-adress**: Ange skrivarens IPv4- eller IPv6-adress. Om du använder värdnamn till att identifiera skrivare, kan du hämta IP-adressen genom att pinga skrivaren i Terminal-appen. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
- **Sökväg**: Ange sökvägen till skrivaren. Sökvägen är vanligtvis `ipp/print` för skrivare i nätverket. Det finns mer information i [Hämta IP-adress och sökväg](#get-the-ip-address-and-path) (i den här artikeln).
- **Port** (iOS 11.0 och senare): Ange lyssningsporten för AirPrint-målet. Om du lämnar den här egenskapen tom, kommer AirPrint att använda standardporten.
- **TLS** (iOS 11.0 och senare): Välj **Aktivera** för att skydda AirPrint-anslutningar med TLS (Transport Layer Security).

**Lägg till** AirPrint-servern. Du kan lägga till flera AirPrint-servrar.

- **Importera** (valfritt): Du kan också **Importera** en kommaavgränsad fil (.csv) med en lista över AirPrint-skrivare. När du har lagt till AirPrint-skrivarna i Intune, kan du också **Exportera** listan.

Spara inställningarna genom att välja **OK**.

### <a name="get-the-ip-address-and-path"></a>Hämta IP-adress och sökväg

Om du vill lägga till AirPrinter-servrar, behöver du ha skrivarens IP-adress, resurssökväg och port. Följande steg visar hur du hämtar den här informationen.

1. Öppna **Terminal** (från **/Program/Verktyg**) på en Mac som är ansluten till samma lokala nätverk (undernät) som AirPrint-skrivarna.
2. I Terminal-appen skriver du `ippfind` och väljer Retur.

    Observera skrivarinformationen. Du kan exempelvis ange något i stil med `ipp://myprinter.local.:631/ipp/port1`. Den första delen är namnet på skrivaren. Den sista delen (`ipp/port1`) är resurssökvägen.

3. I Terminal skriver du `ping myprinter.local` och väljer Retur.

   Observera IP-adressen. Den visar något i stil med `PING myprinter.local (10.50.25.21)`.

4. Använd värdena för IP-adressen och resurssökvägen. I det här exemplet är IP-adressen `10.50.25.21` och resurssökvägen är `/ipp/port1`.

## <a name="login-window"></a>Inloggningsfönstret

### <a name="window-layout"></a>Fönsterlayout

- **Visa ytterligare information i menyfältet**: När du väljer tidsområdet på menyraden visas värdnamnet och macOS-versionen om **Tillåt** är valt. **Inte konfigurerad** (standard) innebär att den här informationen inte visas på menyraden.
- **Banderoll**: Ange ett meddelande som visas på inloggningsskärmen på enheten. Du kan till exempel ange organisationsinformation, ett välkomstmeddelande eller information för Upphittat.
- **Välj inloggningsformat**: Välj hur användare loggar in på enheten. Alternativen är:
  - **Fråga efter användarnamn och lösenord** (standard): Kräver att användarna anger ett användarnamn och lösenord.
  - **Lista alla användare, fråga efter lösenord**: Kräver att användarna väljer sitt användarnamn från en användarlista och sedan anger sitt lösenord. Konfigurera också:

    - **Lokala användare** : Om du väljer **Dölj** visas inte lokala användarkonton i användarlistan, som kan innehålla standardkonton och administratörskonton. Endast nätverks- och systemanvändarkonton visas. **Inte konfigurerad** (standard) visar de lokala användarkontona i användarlistan.
    - **Mobilkonton**: Om du väljer **Dölj** visas inte mobilkonton i användarlistan. **Inte konfigurerad** (standard) visar mobilkontona i användarlistan. Vissa mobilkonton kan visas som nätverksanvändare.
    - **Nätverksanvändare**: Välj **Visa** om du vill visa nätverksanvändare i användarlistan. **Inte konfigurerad** (standard) visar nätverksanvändarkontona i användarlistan.
    - **Administratörer**: Om du väljer **Dölj** visas inte administratörskonton i användarlistan. **Inte konfigurerad** (standard) visar administratörskontona i användarlistan.
    - **Andra användare**: Välj **Visa** om du vill visa **Andra...** användare i användarlistan. **Inte konfigurerad** (standard) visar konton för andra användare i användarlistan.

### <a name="login-screen-power-settings"></a>Strömsparinställningar på inloggningsskärmen

- **Stäng av**: Om du väljer **Dölj** visas inte avstängningsknappen på inloggningsskärmen. **Inte konfigurerad** (standard) visar avstängningsknappen.
- **Starta om**: Om du väljer **Dölj** visas inte omstartsknappen på inloggningsskärmen. **Inte konfigurerad** (standard) visar omstartsknappen.
- **Vila**: Om du väljer **Dölj** visas inte Vila-knappen på inloggningsskärmen. **Inte konfigurerad** (standard) visar Vila-knappen.

### <a name="other"></a>Andra

- **Inaktivera användarinloggning från konsol**: Om du väljer **Inaktivera** döljs macOS-kommandoraden som används för att logga in. Vanliga användare kan **inaktivera** den här inställningen. **Inte konfigurerad** (standard) gör att avancerade användare kan logga in med macOS-kommandoraden. För att gå till konsolläget anger användarna `>console` i fältet Användarnamn. Användarna måste sedan autentiseras i konsolfönstret.

### <a name="apple-menu"></a>Apple-menyn

När användarna loggar in på enheterna påverkar följande inställningar vad de kan göra.

- **Inaktivera Stäng av**: Om du väljer **Inaktivera** kan användarna inte använda alternativet **Stäng av** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Stäng av** på enheten.
- **Inaktivera omstart** : Om du väljer **Inaktivera** kan användarna inte välja alternativet **Starta om** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Starta om** på enheten.
- **Inaktivera Ström av**: Om du väljer **Inaktivera** kan användarna inte välja alternativet **Ström av** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Ström av** på enheten.
- **Inaktivera Logga ut** (macOS 10.13 och senare): Om du väljer **Inaktivera** kan användarna inte välja alternativet **Logga ut** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Logga ut** på enheten.
- **Inaktivera Lås skärm**  (macOS 10.13 och senare): Om du väljer **Inaktivera** kan användarna inte välja alternativet **Lås skärm** efter att de har loggat in. **Inte konfigurerad** (standard) tillåter användare att välja menyalternativet **Lås skärm** på enheten.

Spara inställningarna genom att välja **OK**.

## <a name="next-steps"></a>Nästa steg

- Visa alla inställningar för [iOS](ios-device-features-settings.md)-enheter.
- [Tilldela den här profilen](device-profile-assign.md) till dina grupper och [övervaka dess status](device-profile-monitor.md).
