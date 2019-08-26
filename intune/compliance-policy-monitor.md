---
title: Övervaka efterlevnadsprinciper för enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använd instrumentpanelen för enhetsefterlevnad för att övervaka övergripande enhetsefterlevnad, visa rapporter och visa enhetsefterlevnad per princip och per inställning.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f8560262d8c501af4127876eaafed293fbc4041
ms.sourcegitcommit: b1ddc7f4a3d520b7d6755c7a423a46d1e2548592
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69651199"
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
- Enhetsskyddsstatus
- Status för hotagent

![Bild av instrumentpanelen som visar instrumentpanelen för enhetsefterlevnad och olika rapporter](./media/compliance-policy-monitor/idc-1.png)

När du går in djupare i dessa rapporter kan du även se eventuella specifika efterlevnadsprinciper och inställningar som gäller för en viss enhet, inklusive efterlevnadsstatus för varje inställning.

### <a name="device-compliance-status-report"></a>Rapport för enhetens efterlevnadsstatus

Diagrammet visar efterlevnadsstatus för alla Intune-registrerade enheter. Kompatibilitetstillstånden finns i två olika databaser: Intune och Azure Active Directory. 

> [!IMPORTANT]
> Intune följer enhetens incheckningsschema för alla efterlevnadsutvärderingar på enheten. [Mer information om enhetens incheckningsschema](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

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

Den visar mer information om de enheter som har denna status, inklusive operativsystemplattform, datum för senaste incheckningen med mera. 

![Bild på instrumentpanelen visar mer information på enheten med den specifika statusen](./media/compliance-policy-monitor/drill-down-details.png)

Om du vill se alla enheter som ägs av en specifik användare kan du även filtrera diagramrapporten genom att skriva in användarens e-postadress.

#### <a name="filter-and-columns"></a>Filter och kolumner

![Välj Filter och Kolumn om du vill ändra resultaten i diagrammet](./media/compliance-policy-monitor/filter-columns.png)

När du väljer knappen **Filter** visas fler alternativ, inklusive efterlevnadsstatus, jailbrokade enheter med mera. **Verkställ** filtret för att uppdatera resultatet.

Använd egenskapen **Kolumner** för att lägga till eller ta bort kolumner från diagrammets data. Till exempel kan **Användarens huvudnamn (UPN)** visa den e-postadress som är registrerad på enheten. **Verkställ** kolumnerna för att uppdatera resultatet.

#### <a name="device-details"></a>Information om enhet

Välj en specifik enhet i diagrammet och välj sedan **Enhetsefterlevnad**:

![Välj en specifik enhet och sedan Enhetsefterlevnad för att se de efterlevnadsprinciper som tillämpas](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Där finns mer information om principinställningarna för enhetsefterlevnad som används på den enheten. När du väljer en specifik princip visas alla inställningar i principen.

### <a name="devices-without-compliance-policy"></a>Enheter utan policy för efterlevnad
I **Enhetsefterlevnad** > **Översikt** visar rapporten även enheter som inte har några tilldelade efterlevnadsprinciper:

![Se enheter utan efterlevnadsprinciper](./media/compliance-policy-monitor/devices-without-policies.png)

När du väljer panelen visas alla enheter utan efterlevnadsprincip. Då visas även enhetens användare, principens distributionsstatus samt enhetsmodell.

#### <a name="what-you-need-to-know"></a>Vad du behöver veta

- Med säkerhetsinställningen **Markera enheter som saknar en policy för efterlevnad som** är det viktigt att identifiera enheter som inte har en efterlevnadsprincip. Du kan sedan tilldela minst en policy för efterlevnad till dem.

  Säkerhetsinställningen kan konfigureras i Intune-portalen. Välj **Enhetsefterlevnad** > **Inställningar för efterlevnadsprinciper**. Ställ sedan in **Markera enheter som saknar en policy för efterlevnad som** på **Kompatibel** eller **Inte kompatibel**. 

  Läs mer om denna [förbättrade säkerhet i Intune-tjänsten](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Användare som är tilldelade en efterlevnadsprincip av valfri typ visas inte i rapporten, oavsett enhetsplattform. Om du exempelvis har tilldelat en Windows-efterlevnadsprincip till en användare med en Android-enhet, visas enheten inte i rapporten. Intune anser emellertid att Android-enheten inte är kompatibel. För att undvika problem rekommenderar vi att du skapar principer för varje enhetsplattform och distribuerar dem till alla användare.

### <a name="per-policy-device-compliance-report"></a>Rapport om enhetsefterlevnad per princip

Rapporten **Enhetsefterlevnad** > **Principefterlevnad** visar principerna, samt hur många enheter som är kompatibla och inte kompatibla. 

![Visa en lista över principen och hur många kompatibla och inte kompatibla enheter som finns för den principen](./media/compliance-policy-monitor/idc-8.png)

När du väljer en specifik princip kan du se **efterlevnadsstatus**, **användarens e-postalias**, **enhetsmodell** och **plats** för varje enhet som den efterlevnadsprincipen är inriktad på.

## <a name="setting-compliance-report"></a>Inställning av efterlevnadsrapport

Rapporten **Enhetsefterlevnad** > **Inställningskompatibilitet** visar det totala antalet enheter med respektive efterlevnadsstatus per efterlevnadsinställning. Den visar alla principinställningar för enhetsefterlevnad från alla efterlevnadsprinciper, de plattformar som principinställningarna används på, samt antalet ej kompatibla enheter.

![Visa en lista över alla inställningar i olika principer](./media/compliance-policy-monitor/idc-10.png)

När du väljer en specifik inställning kan du se **efterlevnadsstatus**, **användarens e-postalias**, **enhetsmodell** och **plats** för alla enheter som den inställningen är inriktad på.

> [!NOTE]
> En princip kan tilldelas en enhet och en användare på samma enhet. I vissa fall kan en enhet synkroniseras innan användaren loggar in, till exempel när enheten startas om. Efterlevnad kan utvärdera den här användaren och visa enheten som icke-kompatibel. Det här beteendet kan också visa systemkontot som en icke-kompatibel användare.
>
> Detta är ett känt problem med Windows 10-enheter med flera användare. Ändringar eller uppdateringar av det här beteendet presenteras i [under utveckling](in-development.md) och/eller [vad som är nytt](whats-new.md).

## <a name="view-status-of-device-policies"></a>Visa status för enhetsprinciper

Du kan kontrollera principernas olika statusar per plattform. Du kan till exempel ha en efterlevnadsprincip för macOS. Du vill se de enheter som påverkas av den här principen och se om det uppstår konflikter eller fel.

Den här funktionen ingår i statusrapporteringen för enheter:

1. Välj **Enhetsefterlevnad** > **Principer**. En lista över principer visas, inklusive plattformen, om principen har tilldelats, samt ytterligare information.
2. Välj en princip > **Översikt**. I den här vyn innehåller principtilldelningen följande statusar:

    - Lyckades: Principen tillämpas
    - Fel: Det gick inte att tillämpa principen. Detta meddelande visas vanligtvis med en felkod som länkar till en förklaring. 
    - Konflikt: Två inställningar tillämpas på samma enhet och Intune kan inte lösa konflikten. En administratör bör granska.
    - Väntar: Enheten har inte checkats in i Intune ännu för att ta emot principen. 
    - Inte tillämpligt: Enheten kan inte ta emot principen. Principen uppdaterar t.ex. en inställning som är specifik för iOS 11.1, men enheten använder iOS 10. 

3. Om du vill visa information om de enheter som använder den här principen väljer du en av statusarna. Välj till exempel **Lyckades**. I nästa fönster visas specifik enhetsinformation, inklusive enhetsnamn och distributionsstatus.

## <a name="how-intune-resolves-policy-conflicts"></a>Så här löser Intune principkonflikter
Principkonflikter kan uppstå när flera Intune-principer används på en enhet. Om principinställningarna överlappar varandra löser Intune eventuella konflikter med hjälp av följande regler:

- Om de motstridiga inställningarna gäller en Intune-konfigurationsprincip och en efterlevnadsprincip, prioriteras inställningarna i efterlevnadsprincipen framför inställningarna i konfigurationsprincipen. Detta gäller även om inställningarna i konfigurationsprincipen är säkrare.

- Om du har distribuerat flera efterlevnadsprinciper använder Intune den säkraste av dessa principer.
