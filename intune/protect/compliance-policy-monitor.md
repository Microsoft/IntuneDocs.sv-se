---
title: Övervaka efterlevnadsprinciper för enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använd instrumentpanelen för enhetsefterlevnad för att övervaka övergripande enhetsefterlevnad, visa rapporter och visa enhetsefterlevnad per princip och per inställning.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 947472c5e589cb443c9a15d20a732c299cc48b44
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992980"
---
# <a name="monitor-intune-device-compliance-policies"></a>Övervaka efterlevnadsprinciper för Intune-enheter

Efterlevnadsrapporter hjälper dig att granska enhetsefterlevnad och felsöka efterlevnadsrelaterade problem i organisationen. Med hjälp av dessa rapporter kan du se information om följande:

- Övergripande efterlevnadsstatus för enheter
- Efterlevnadsstatus för en enskild inställning
- Efterlevnadsstatus för en enskild princip
- Se detaljer för enskilda enheter om du vill se specifika inställningar och principer som påverkar enheten

## <a name="open-the-compliance-dashboard"></a>Öppna instrumentpanelen för efterlevnad

Öppna **Intunes instrumentpanel för enhetsefterlevnad**:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Välj **Enhetsefterlevnad** > **Översikt**. **Instrumentpanelen för enhetsefterlevnad** öppnas.

> [!IMPORTANT]
> Enheter måste registreras i Intune för att kunna ta emot principer för enhetsefterlevnad.

## <a name="dashboard-overview"></a>Översikt över instrumentpanelen

När instrumentpanelen öppnas kan du få en översikt med alla efterlevnadsrapporter. I dessa rapporter kan du se och söka efter:

- Övergripande enhetsefterlevnad
- Enhetsefterlevnad per princip
- Enhetsefterlevnad per inställning
- Status för hotagent
- Enhetsskyddsstatus

![Bild av instrumentpanelen som visar instrumentpanelen för enhetsefterlevnad och olika rapporter](./media/compliance-policy-monitor/idc-1.png)

När du går in djupare i dessa rapporter kan du även se eventuella specifika efterlevnadsprinciper och inställningar som gäller för en viss enhet, inklusive efterlevnadsstatus för varje inställning.

### <a name="device-compliance-status"></a>Enhetens efterlevnadsstatus

Diagrammet **Status för enhetsefterlevnad** visar efterlevnadsstatusen för alla Intune-registrerade enheter. Kompatibilitetstillstånden finns i två olika databaser: Intune och Azure Active Directory.

> [!IMPORTANT]
> Intune följer enhetens incheckningsschema för alla efterlevnadsutvärderingar på enheten. [Mer information om enhetens incheckningsschema](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Beskrivningar av statusar för enhetsefterlevnadsprinciper:

- **Kompatibel**: Enheten har tillämpat en eller flera principinställningar för enhetsefterlevnad.

- **Respitperiod:** En eller flera principinställningar för enhetsefterlevnad har riktats mot enheten. Användaren har dock inte tillämpat principerna än. Det innebär att enheten inte är kompatibel, men den är i respitperioden som angetts av administratören.

  - Läs mer om [åtgärder för inkompatibla enheter](actions-for-noncompliance.md).

- **Inte utvärderat**: Ett ursprungligt tillstånd för nyregistrerade enheter. Andra möjliga orsaker till detta tillstånd kan vara:

  - Enheter som inte har tilldelats någon efterlevnadsprincip och som saknar en utlösare för att kontrollera efterlevnaden
  - Enheter som inte har checkats in sedan efterlevnadsprincipen senast uppdaterades
  - Enheter som inte är associerade till en specifik användare, till exempel:
    - iOS-enheter som köpts via Apples program för enhetsregistrering (DEP) som inte har någon användartillhörighet
    - Dedikerade Android kiosk- eller Android Enterprise-enheter
  - Enheter som har registrerats med ett konto för enhetsregistreringshantering (DEM)

- **Inkompatibel:** Enheten kunde inte tillämpa en eller flera principinställningar för enhetsefterlevnad. Eller så har användaren inte efterlevt principerna.

- **Enheten har inte synkroniserats:** Enheten kunde inte rapportera sin status för enhetsefterlevnadsprincipen på grund av någon av följande orsaker:

  - **Okänd**: Enheten är offline eller kunde inte kommunicera med Intune eller Azure AD av andra orsaker.

  - **Fel**: Enheten kunde inte kommunicera med Intune eller Azure AD och tog emot ett felmeddelande som angav orsaken.

> [!IMPORTANT]
> Enheter som har registrerats i Intune men inte utgör mål för någon enhetsefterlevnadsprincip, inkluderas i den här rapporten under bucketen **Kompatibel**.

#### <a name="drill-down-for-more-details"></a>Öka detaljnivån om du vill ha mer information

I diagrammet **Kompatibilitetsstatus för enhet** väljer du en status. Välj till exempel statusen **Inte kompatibel**:

![Välj statusen inte kompatibel](./media/compliance-policy-monitor/select-not-compliant-status.png)

Den här åtgärden öppnar fönstret **Enhetsefterlevnad** och visar enheter i diagrammet **Enhetsstatus**. Diagrammet visar mer information om de enheter som har den här statusen, inklusive operativsystemplattform, datum för senaste incheckning med mera.
![Bilden av instrumentpanelen visar mer information på enheten med den specifika statusen](./media/compliance-policy-monitor/drill-down-details.png)

Om du vill se alla enheter som ägs av en specifik användare kan du även filtrera diagramrapporten genom att skriva in användarens e-postadress.

#### <a name="filter-and-columns"></a>Filter och kolumner

![Välj Filter och Kolumn om du vill ändra resultaten i diagrammet](./media/compliance-policy-monitor/filter-columns.png)

När du väljer knappen **Filtrera** visas fler alternativ, inklusive **efterlevnadsstatus**, **jailbrokade enheter** med mera. **Verkställ** filtret för att uppdatera resultatet.

Använd egenskapen **Kolumner** för att lägga till eller ta bort kolumner från diagrammets data. Till exempel kan **Användarens huvudnamn (UPN)** visa den e-postadress som är registrerad på enheten. **Verkställ** kolumnerna för att uppdatera resultatet.

#### <a name="device-details"></a>Information om enhet

I diagrammet **Enhetsinformation** väljer du en specifik enhet och väljer sedan **Enhetsefterlevnad**:

![Välj en specifik enhet och sedan Enhetsefterlevnad för att se de efterlevnadsprinciper som tillämpas](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Intune visar mer information om principinställningarna för enhetsefterlevnad som används på enheten. När du väljer en specifik princip visas alla inställningar i principen.

### <a name="devices-without-compliance"></a>Enheter utan efterlevnad

Bredvid diagrammet *Principefterlevnad* på sidan *Efterlevnadsstatus* kan du välja panelen **Enheter utan policy för efterlevnad** för att visa information om enheter som inte har några tilldelade efterlevnadsprinciper:

![Se enheter utan efterlevnadsprinciper](./media/compliance-policy-monitor/devices-without-policies.png)

När du väljer panelen visas alla enheter utan efterlevnadsprincip. Då visas även enhetens användare, principens distributionsstatus samt enhetsmodell.

#### <a name="what-you-need-to-know"></a>Vad du behöver veta

- Med säkerhetsinställningen **Markera enheter som saknar en policy för efterlevnad som** är det viktigt att identifiera enheter som inte har en efterlevnadsprincip. Du kan sedan tilldela minst en policy för efterlevnad till dem.

  Säkerhetsinställningen kan konfigureras i Intune-portalen. Gå till **Enheter** > **Efterlevnadsprinciper** > **Inställningar för policy för efterlevnad**. Ställ sedan in **Markera enheter som saknar en policy för efterlevnad som** på **Kompatibel** eller **Inte kompatibel**.

  Läs mer om denna [förbättrade säkerhet i Intune-tjänsten](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Användare som är tilldelade en efterlevnadsprincip av valfri typ visas inte i rapporten, oavsett enhetsplattform. Om du exempelvis har tilldelat en Windows-efterlevnadsprincip till en användare med en Android-enhet, visas enheten inte i rapporten. Intune anser emellertid att Android-enheten inte är kompatibel. För att undvika problem rekommenderar vi att du skapar principer för varje enhetsplattform och distribuerar dem till alla användare.

### <a name="per-policy-device-compliance"></a>Enhetsefterlevnad per princip

Diagrammet **Principefterlevnad** visar principerna och hur många enheter som är kompatibla och hur många som inte är det.

![Visa en lista över principen och hur många kompatibla och inte kompatibla enheter som finns för den principen](./media/compliance-policy-monitor/idc-8.png)

### <a name="setting-compliance"></a>Ställa in efterlevnad

Diagrammet **Inställningskompatibilitet** visar alla principinställningar för enhetsefterlevnad från alla efterlevnadsprinciper, de plattformar som principinställningarna används på, samt antalet ej kompatibla enheter.

![Visa en lista över alla inställningar i olika principer](./media/compliance-policy-monitor/idc-10.png)

## <a name="view-compliance-reports"></a>Visa efterlevnadsrapporter

Förutom att använda diagrammen i *Efterlevnadsstatus*kan du visa efterlevnadsrapporter på sidan *Övervakare* i administrationscentret.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Övervaka**och under **Efterlevnad** väljer du sedan den rapport du vill visa. Några av de tillgängliga efterlevnadsrapporterna är:

   - Efterlevnad för enhet
   - Icke-kompatibla enheter
   - Enheter utan policy för efterlevnad
   - Ställa in efterlevnad
   - Principefterlevnad
   - Hälsoattesteringsrapporter för Windows
   - Status för hotagent

Mer information om rapporter finns i [Intune-rapporter](../fundamentals/reports.md)

## <a name="view-status-of-device-policies"></a>Visa status för enhetsprinciper

Du kan kontrollera principernas olika statusar per plattform. Du kan till exempel ha en efterlevnadsprincip för macOS. Du vill se de enheter som påverkas av den här principen och se om det uppstår konflikter eller fel.

Den här funktionen ingår i statusrapporteringen för enheter:

1. Välj **Enheter** > **Efterlevnadsprinciper** > **Principer**. En lista över principer visas, inklusive plattformen, om principen har tilldelats, samt ytterligare information.
2. Välj en princip > **Översikt**. I den här vyn innehåller principtilldelningen följande statusar:

    - **Lyckades**: Principen tillämpas
    - **Fel**: Det gick inte att tillämpa principen. Detta meddelande visas vanligtvis med en felkod som länkar till en förklaring.
    - **Konflikt**: Två inställningar tillämpas på samma enhet och Intune kan inte lösa konflikten. En administratör bör granska.
    - **Väntar**: Enheten har inte checkats in i Intune ännu för att ta emot principen.
    - **Ej tillämpligt**: Enheten kan inte ta emot principen. Principen uppdaterar t.ex. en inställning som är specifik för iOS 11.1, men enheten använder iOS 10.

3. Om du vill visa information om de enheter som använder den här principen väljer du en av statusarna. Välj till exempel **Lyckades**. I nästa fönster visas specifik enhetsinformation, inklusive enhetsnamn och distributionsstatus.

## <a name="how-intune-resolves-policy-conflicts"></a>Så här löser Intune principkonflikter

Principkonflikter kan uppstå när flera Intune-principer används på en enhet. Om principinställningarna överlappar varandra löser Intune eventuella konflikter med hjälp av följande regler:

- Om de motstridiga inställningarna gäller en Intune-konfigurationsprincip och en efterlevnadsprincip, prioriteras inställningarna i efterlevnadsprincipen framför inställningarna i konfigurationsprincipen. Detta gäller även om inställningarna i konfigurationsprincipen är säkrare.

- Om du har distribuerat flera efterlevnadsprinciper använder Intune den säkraste av dessa principer.
