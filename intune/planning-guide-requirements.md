---
title: "Fastställa scenariokrav för användningsfall"
description: "Den här artikeln hjälper dig fastställa scenariokrav för Intunes användningsfall och underanvändningsfall vid en Microsoft Intune-implementering som sker enbart i molnet."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8806dc965653deaca5ab370c290403ae049e5c58
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="determine-use-case-scenario-requirements"></a>Fastställa scenariokrav för användningsfall

I det här avsnittet kommer att du fastställa kraven för varje organisationsgrupp inom varje användningsfall. Med den här processen kan du förbereda dig inför andra planeringsområden för Intune-distribution, t.ex. arkitektur och utformning, integration och distribution. Det kan också identifiera eventuella luckor och utmaningar gällande Intune-distributionsprojektet.

Du kan ha olika kravuppsättningar för vart och ett av användningsfallen/underanvändningsfallen och deras tillhörande organisationsgrupper och mobila enhetsplattformar. Företagets krav för användningsfall kan t.ex. kräva att enheter registreras i Intune med en mer restriktiv uppsättning enhetsinställningar, t.ex. en PIN-kod med 6 tecken eller inaktiverad molnsäkerhetskopiering. Ditt användningsfall för BYOD (Bring Your Own Device) kan vara mindre restriktivt och tillåta en PIN-kod på 4 tecken och molnsäkerhetskopiering.

Du kan också ha organisationsgrupper för företagets användningsfall som har olika kravuppsättningar (t.ex. PIN-inställningar, Wi-Fi- eller VPN-profil, distribuerade appar). Dina krav kan också fastställas med funktionerna i den mobila enhetsplattformen (exempelvis fingeravtrycksläsare eller e-postprofil).

Följande är några exempel på krav för användningsfall i en organisation, som visar olika kravuppsättningar för varje användningsfall/underanvändningsfall, organisationsgrupp och mobil enhetsplattform. Du kan också använda följande tabell för att ange organisationens krav för användningsfall:

| **Användningsfall** | **Underanvändningsfall** | **Grupper** | **Enhetsplattformar** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| Företag | Informationsarbetare | Personalavdelning, ekonomi | iOS | Säker e-post, enhetsinställningar, profiler, appar |                                                          
| Företag | Chefer | Personalavdelning, ekonomi | iOS | Säker e-post, enhetsinställningar, profiler, appar |                                                         
| Företag | Helskärmsläge | Återförsäljning | Android | Enhetsinställningar, profiler, appar |
| BYOD | Informationsarbetare | Marknadsföring, försäljning | iOS | Säker e-post, enhetsinställningar, profiler, appar |                                                         
| BYOD | Chefer | Marknadsföring, försäljning | iOS | Säker e-post, enhetsinställningar, profiler, appar |

Du kan [ladda ned en mall för ovanstående tabell](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) där du kan ange din organisations krav för användningsfall och underanvändningsfall.


## <a name="examples-of-requirements"></a>Exempel på krav

Här är några fler exempel som kan användas i kolumnen ”Krav”:

- **Säker e-post**
    - Villkorlig åtkomst för Exchange Online/lokalt
    - Appskyddsprinciper för Outlook

- **Enhetsinställningar**
    - PIN-inställning med fyra eller sex tecken
    - Begränsa molnsäkerhetskopiering

- **Profiler**
    - Wi-Fi
    - VPN
    - E-post (Windows 10 mobil)

- **Appar**
    - Office 365 med appskyddsprinciper
    - Branschspecifikt (LOB) med appskyddsprinciper

## <a name="next-section"></a>Nästa avsnitt

Nästa avsnitt innehåller råd om [att utveckla en plan för Intune-distributionen](planning-guide-rollout-plan.md).
