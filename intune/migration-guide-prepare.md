---
title: Förbered Intune för hantering av mobila enheter
titleSuffix: Microsoft Intune
description: Utvärdera dina affärsspecifika och tekniska krav innan du migrerar till Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e527ed11e451ec0ef2f6d2fde42e0c8fd53408f3
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508369"
---
# <a name="phase-1-prepare-microsoft-intune-for-mobile-device-management-mdm"></a>Fas 1: Förbered Microsoft Intune för hantering av mobilenheter (MDM)

Innan du går in i detalj om hur Intune ska konfigureras, så låt oss titta på ditt företags krav på hur mobila enheter ska hanteras. Det kan vara bra att identifiera viktiga användargrupper genom att köra rapporter över aktiva användare i din aktuella MDM-provider. Sedan kan du gå igenom frågorna i avsnittet [Utvärdera MDM-krav ](migration-guide-prepare.md#assess-mdm-requirements).

## <a name="assess-mdm-requirements"></a>Utvärdera MDM-krav

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Vilka typer av enheter behöver hanteras?

-   Vilka [plattformar](supported-devices-browsers.md) krävs det stöd för?

-   Är de enheter som du behöver hantera företagsägda eller personliga enheter?

-   Vilken typ av anslutning använder du? Wi-Fi, mobiltelefon, VPN?

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>Vad måste användarna göra på hanterade enheter?

-   Behöver du tillhandahålla appar för slutanvändarna?

-   Använder du anpassade av verksamhetsspecifika appar? Eller bara behöver du bara offentliga Store-appar?

-   Måste du tillhandahålla e-postkonton?

### <a name="what-kinds-of-users"></a>Vilka typer av användare handlar det om?

-   Hur många användare kommer att använda samma enhet?

-   Vilka användningsvillkor behöver du?

    -   Var noga med att involvera företagets juridiska avdelning redan från början.
    -   Vilken typ av lokalisering krävs?

-   Är användarnas allmänna kunskaper om teknik och IT goda?

### <a name="what-is-your-device-security-policy"></a>Vilken är din säkerhetsprincip för enheter?

- Behöver du använda kryptering på enhetsnivå?

- Hur långa enhetslösenord/PIN-koder använder du nu?

- Måste du inaktivera enhetsfunktioner eller begränsa vissa enhetsbeteenden? Du kan styra olika plattformsspecifika inställningar med enhetskonfigurationsprofiler, till exempel:
    - Inaktivera kamera
    - Lås till enkelt appläge<br/>

- Vilka typer av autentisering måste du stödja? Om du behöver certifikatbaserad autentisering, vilka typer av certifikat krävs i så fall?
  - Intune kan tillhandahålla certifikat med resursåtkomstprofiler för registrerade enheter.
  -   Vilken typ av Public Key Infrastructure (PKI) behöver du stöd för?
  <br></br>
- Behöver du stöd för virtuella privata nätverk på enhets- eller appnivå?

  -   Intune kan tillhandahålla VPN-konfigurationer för VPN-tredjepartsleverantörer.
  <br/><br/>
- Går det att göra tillfälliga undantag för vissa krav om det skulle bidra till att undvika driftavbrott? Eller måste enheter med åtkomst alltid uppfylla alla säkerhetskrav?

## <a name="next-steps"></a>Nästa steg
Läs dessa [fallstudier](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune) från olika branschsektorer och se hur organisationer har utvärderat sina krav för hantering av mobila enheter.

Gå igenom [den grundläggande Intune-konfigurationen](migration-guide-setup.md).
