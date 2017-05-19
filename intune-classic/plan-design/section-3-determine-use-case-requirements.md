---
title: "Fastställa krav för användningsfall i Intune | Microsoft Docs"
description: "Den här artikeln hjälper till att fastställa krav för Intune-användningsfall och underfall för en Microsoft Intune-molnimplementering."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: 91b25fe35c6a1f8a554d543ca005cc3b482f22d7
ms.lasthandoff: 12/30/2016


---

# <a name="determine-intune-use-case-scenario-requirements"></a>Fastställa krav för användningsfall i Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

I det här avsnittet kommer att du fastställa kraven för varje organisationsgrupp inom varje användningsfall. Genom att gå igenom den här processen kan du förbereda dig bättre för övriga planeringsområden gällande Intune-distribution, t.ex. arkitektur och utformning, onboarding och distribution. Det kan också identifiera eventuella luckor och utmaningar gällande Intune-distributionsprojektet.

Du kan ha olika kravuppsättningar för vart och ett av användningsfallen/underfallen och deras tillhörande organisationsgrupper och mobila enhetsplattformar. Företagets krav för användningsfall kan exempelvis kräva att enheter registreras i Intune med en mer restriktiv uppsättning enhetsinställningar (t.ex. PIN med 6 tecken, inaktivering av molnsäkerhetskopiering) jämfört med användningsfall med "Bring your own device" (BYOD), där mindre restriktiva inställningar krävs (t.ex. PIN med 4 tecken, molnsäkerhetskopiering tillåts).

Du kan också ha organisationsgrupper för företagets användningsfall som har olika kravuppsättningar (t.ex. PIN-inställningar, Wi-Fi- eller VPN-profil, distribuerade appar). Dessutom kan kraven fastställas genom funktionerna för den mobila enhetsplattformen (t.ex. fingeravtrycksläsare, e-postprofil).

Följande är några exempel på krav för användningsfall i en organisation, som visar olika kravuppsättningar för varje användningsfall/underfall, organisationsgrupp och mobil enhetsplattform. Du kan även använda tabellen nedan för att ange organisationens krav för användningsfall:

| **Användningsfall** | **Underanvändningsfall** | **Grupper** | **Enhetens OS-plattformar** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| Företag | Informationsarbetare | Personalavdelning, ekonomi | iOS | Säker e-post, enhetsinställningar, profiler, appar |                                                          
| Företag | Chefer | Personalavdelning, ekonomi | iOS | Säker e-post, enhetsinställningar, profiler, appar |                                                         
| Företag | Helskärmsläge | Återförsäljning | Android | Enhetsinställningar, profiler, appar |
| BYOD | Informationsarbetare | Marknadsföring, försäljning | iOS | Säker e-post, enhetsinställningar, profiler, appar |                                                         
| BYOD | Chefer | Marknadsföring, försäljning | iOS | Säker e-post, enhetsinställningar, profiler, appar |

## <a name="examples-of-requirements"></a>Exempel på krav

Följande är ytterligare exempel som kan användas i kolumnen "Krav" som hänvisas till i tabellen ovan:

- **Säker e-post**
    - Villkorlig åtkomst för Exchange Online/On-premises
    - Appskyddsprinciper för Outlook
<br></br>
- **Enhetsinställningar**
    - PIN-inställning med fyra eller sex tecken
    - Begränsa molnsäkerhetskopiering
<br></br>
- **Profiler**
    - Wi-Fi
    - VPN
    - E-post (Windows 10 mobil)
<br></br>
- **Appar**
    - Office 365 med appskyddsprinciper
    - Branschspecifikt (LOB) med appskyddsprinciper

## <a name="next-section"></a>Nästa avsnitt

Nästa avsnitt innehåller råd om [att utveckla en plan för Intune-distributionen](section-4-develop-a-rollout-plan.md).

