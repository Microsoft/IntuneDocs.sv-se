---
title: "Förbered Intune för hantering av mobila enheter"
description: "Syftet med den här artikeln är att hjälpa läsarna att kunna utvärdera sina verkamhetsrelaterade krav och tekniska krav innan migreringen till Intune görs."
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
ms.custom: intune-classic
ms.openlocfilehash: 65e3bb4b6a4e6e8dcfa1dd16738ae47758f4fb9b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="phase-1-prepare-intune-for-mobile-device-management-mdm"></a>Fas 1: Förbered Intune för hantering av mobila enheter (MDM)

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Innan du går in i detalj om hur Intune ska konfigureras, så låt oss titta på ditt företags krav på hur mobila enheter ska hanteras. Det kan vara bra att köra rapporter om aktiva användare i din aktuella MDM-provider så att du kan identifiera kritiska användargrupper. Sedan kan du börja adressera frågorna i avsnittet [Utvärdera MDM-krav](migration-guide-prepare.md#assess-mdm-requirements).

## <a name="assess-mdm-requirements"></a>Utvärdera MDM-krav

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Vilka typer av enheter behöver hanteras?

-   Vilka [plattformar](/intune-classic/get-started/supported-mobile-devices-and-computers) krävs det stöd för?

-   Är de enheter som du kräver stöd företagsägda enheter eller BYOD-enheter?

-   Vilken typ av anslutning används? Wi-Fi, mobiltelefon, VPN?

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

-   Enhetslösenord/PIN-kodslängd?

-   Måste du inaktivera enhetsfunktioner eller begränsa vissa enhetsbeteenden?

    -   Du kan styra flera plattformsspecifika inställningar med profiler för enhetskonfiguration, t.ex. inaktivering av kamera och låsning till enappsläge.
<br></br>
-   Vilka typer av autentisering måste du stödja?

    -   Om du behöver certifikatsbaserad autentisering, vilka typer av certifikat måste i så fall tillhandahållas?

        -   Intune kan tillhandahålla certifikat med resursåtkomstprofiler för registrerade enheter.
<br></br>
    -   Vilken typ av Public Key Infrastructure (PKI) behöver du stöd för?
<br></br>
-   Behöver du stöd för virtuella privata nätverk på enhets- eller appnivå?

    -   Intune kan tillhandahålla VPN-konfigurationer för VPN-tredjepartsleverantörer.
<br></br>
-   Går det att göra tillfälliga undantag för vissa krav om det skulle bidra till att undvika stillestånd? Eller måste enheter med åtkomst alltid uppfylla alla säkerhetskrav?

## <a name="additional-information"></a>Ytterligare information

-   Mer detaljerade exempel ges i dessa [fallstudier](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune) som kommer från olika branscher inom industrin. Där kan du se hur olika organisationer utvärderar sina krav på hantering av mobila enheter.

## <a name="next-steps"></a>Nästa steg

[Grundläggande konfiguration](migration-guide-setup.md)
