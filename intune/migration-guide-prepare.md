---
title: "Förbered Intune för hantering av mobila enheter"
description: "Utvärdera dina affärsspecifika och tekniska krav innan du migrerar till Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 9e935531c785a1c907454d563550f237ebffdb13
ms.sourcegitcommit: fb17b59f4aa2b994b149fcc6d32520f74b0de6a5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/12/2017
---
# <a name="phase-1-prepare-intune-for-mobile-device-management-mdm"></a>Fas 1: Förbered Intune för hantering av mobila enheter (MDM)

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

-   Behöver du använda kryptering på enhetsnivå?

-   Hur långa enhetslösenord/PIN-koder använder du nu?

-   Måste du inaktivera enhetsfunktioner eller begränsa vissa enhetsbeteenden? Du kan styra olika plattformsspecifika inställningar med enhetskonfigurationsprofiler, till exempel:
      - Inaktivera kamera
      - Lås till enkelt appläge<br/>

-   Vilka typer av autentisering måste du stödja? Om du behöver certifikatbaserad autentisering, vilka typer av certifikat krävs i så fall?
  - Intune kan tillhandahålla certifikat med resursåtkomstprofiler för registrerade enheter.
    -   Vilken typ av Public Key Infrastructure (PKI) behöver du stöd för?
<br></br>
-   Behöver du stöd för virtuella privata nätverk på enhets- eller appnivå?

    -   Intune kan tillhandahålla VPN-konfigurationer för VPN-tredjepartsleverantörer.
<br/><br/>
-   Går det att göra tillfälliga undantag för vissa krav om det skulle bidra till att undvika driftavbrott? Eller måste enheter med åtkomst alltid uppfylla alla säkerhetskrav?

## <a name="next-steps"></a>Nästa steg
Läs dessa [fallstudier](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune) från olika branschsektorer och se hur organisationer har utvärderat sina krav för hantering av mobila enheter.

Gå igenom [den grundläggande Intune-konfigurationen](migration-guide-setup.md).
