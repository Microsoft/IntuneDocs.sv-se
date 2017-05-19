---
title: "Fastställa inriktade grupper och tidsmål för Intune-distribution | Microsoft Docs"
description: "Den här artikeln hjälper till att fastställa inriktade grupper och tidsmål för distribution vid en Microsoft Intune-molnimplementering."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 2a970badf5ac18a05115a72dc267ee455ba4628d
ms.lasthandoff: 04/25/2017


---

# <a name="develop-an-intune-rollout-plan"></a>Utveckla en distributionsplan för Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Det här avsnittet hjälper dig att fastställa de organisationsgrupper som Intune-distributionen ska rikta in sig på, samt distributionstidsplanen för varje grupp och de registreringsmetoder som ska användas.

## <a name="determine-intune-rollout-targeted-groups-and-timeframes"></a>Fastställa inriktade grupper och tidsmål för Intune-distribution

Det är viktigt att först identifiera de grupper som Intune-distributionen ska rikta in sig på. Målgrupperna beskrevs tidigare i avsnittet om identifiering av Intune-användarscenarier i den här guiden.

För det andra måste du bestämma tidsplanen då varje grupp ska vara mål för Intune-distributionen. Detta kräver normalt diskussioner inom Intune-distributionsgruppen och med målgrupper för att fastställa den bästa distributionstidsplanen för varje grupp.

Intune-distributionsgruppen kan exempelvis diskutera sådana faktorer som målgruppens mottaglighet för förändringar, antal användare och enheter, typer av enhetsplattformar, krav, geografisk plats och affärsrisk för att fastställa distributionstidsplanen.

Organisationer väljer ofta att starta Intune-installationen med ett inledande pilottest som riktar in sig på en liten grupp användare på IT-avdelningen. Pilottestet kan sedan utökas med ett större antal IT-användare och deltagare från andra organisationsgrupper. Efter ett lyckat pilottest är organisationerna redo att inleda en fullständig distribution i produktionen, som riktar in sig på resten av organisationens grupper. Nedan följer några exempel på olika grupper och faser för distribution:

-   **Pilot:** Den första fasen i distributionen ska vara pilotanvändare. Pilotanvändarna bör förstå att de är de första användarna av en ny lösning och de bör vara villiga att lämna feedback för att förbättra konfiguration, dokumentation, meddelanden och underlätta för alla andra användare i senare installationsfaser. Dessa användare får inte vara företagsledare eller VIP-användare.

-   **Avdelningar:** Varje avdelning kan vara en distributionsfas. I det här scenariot kan du rikta in dig på en hel avdelning samtidigt. I den här typen av distribution använder varje fas troligen den mobila enheten på samma sätt och har åtkomst till samma program. Användarna har troligtvis även samma principtyper.

-   **Geografi:** Den här distributionstypen innebär att man distribuerar till alla användare inom ett visst geografiskt område, t.ex. samma kontinent, land, region eller företagsbyggnad. Den här typen av stegvis distribution gör det möjligt att fokusera på en specifik användarplats. Det kan möjliggöra en mer [assisterad](#user-assisted-enrollment) metod, eftersom antalet platser som distribuerar Intune samtidigt minskas. Eftersom det är möjligt att olika avdelningar eller användarfall befinner sig på samma plats kan olika användarfall distribueras samtidigt.

-   **Plattform:** Den här distributionstypen innebär att distribuera liknande plattformar samtidigt. Ett exempel kan vara alla iOS-enheter den första månaden, följt av Android, följt av Windows. Den här typen av stegvis distribution förenklar för supportavdelningen. Supportavdelningen behöver bara stödja en plattform i taget.

Följande är ett exempel på en Intune-distributionsplan som innehåller målgrupper och tidslinjer:

| **Distributionsfas** | **Juli** | **Augusti** | **September** | **Oktober** |
|:---:|:---:|:---:|:---:|:---:|
| Begränsat pilottest | IT (50 användare) |  |  |  |                                                         
| Utökat pilottest | IT (200 användare), IT-chefer (10 användare) |  |  |  |                                                         
| Produktionsdistributionsfas 1 |  | Försäljning och marknadsföring (2000 användare) |  |  |
| Produktionsdistributionsfas 2 |  |  | Återförsäljning (1000 användare) |  |
| Produktionsdistributionsfas 3 |  |  |  | Personalavdelning (50 användare), ekonomi (40 användare), chefer (30 användare) |

## <a name="determine-the-intune-enrollment-approach"></a>Fastställa metod för Intune-registrering

När du har fastställt målgrupper och tidsplaner för Intune-distributionen är nästa steg att välja den mest lämpliga Intune-registreringsmetoden för varje grupp. Det finns olika registreringsmetoder som organisationer kan använda för sina Intune-distributioner. Några vanliga registreringsmetoder är självbetjäning för användare, registrering med användarhjälp och IT-teknikmässa.

### <a name="user-self-service"></a>Självbetjäning för användare

Med den här metoden ansvarar användaren för att registrera sin egen enhet, vanligtvis enligt registreringsanvisningar som tillhandahålls av IT-organisationen. Den här metoden används oftast i organisationer och är mer skalbar än registrering med användarhjälp.

### <a name="user-assisted-enrollment"></a>Registrering med användarhjälp

Detta kallas en ”assisterad” metod, där en IT-gruppmedlem hjälper användaren genom registreringsprocessen, antingen personligen eller via Skype. Den här metoden används vanligtvis för chefer och andra grupper som kan behöva mer hjälp vid registreringen.

### <a name="it-tech-fair"></a>IT-teknikmässa

Ett annat alternativ för Intune-användarregistrering är att ha en IT-teknikmässa. Vid ett sådant evenemang ställer IT-gruppen upp ett bås för hjälp med Intune-registrering, där användarna kan få information om Intune-registrering, ställa frågor och få hjälp med registreringsprocessen. Det här alternativet kan vara fördelaktigt både för IT-gruppen och användaren, särskilt under tidiga faser av Intune-distributionen.

Följande är ett exempel på en Intune-distributionsplan med målgrupper, tidsplaner och registreringsmetoder:

| **Distributionsfas** | **Juli** | **Augusti** | **September** | **Oktober** |
|:---:|:---:|:---:|:---:|:---:|
| Begränsat pilottest |  |  |  |  |                                                         
| Självbetjäning | IT |  |  |  |
| Utökat pilottest |  |  |  |  |                                                         
| Självbetjäning | IT |  |  |  |
| Assisterad | IT-chefer |  |  |  |
| Produktionsdistributionsfas 1 |  | Försäljning, marknadsföring |  |  |
| Självbetjäning |  | Försäljning och marknadsföring |  |  |
| Produktionsdistributionsfas 2 |  |  | Återförsäljning |  |
| Självbetjäning |  |  |  |  |
| Produktionsdistributionsfas 3 |  |  | Återförsäljning |  |
| Självbetjäning |  |  |  | Personalavdelning, ekonomi |
| Assisterad |  |  |  | Chefer |

## <a name="next-section"></a>Nästa avsnitt

Nästa avsnitt innehåller råd om att [utveckla en kommunikationsplan för Intune-registreringen](section-5-develop-a-rollout-communication-plan.md).

