---
title: "Fastställa målgrupper för distribution och tidsramar"
description: "Den här artikeln hjälper dig att bestämma vilka grupper som ska distribueras till Intune och vilka tidsramarna ska vara för dessa distributioner."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9dda530be47b5449a9c1ed610d8e409fd62148d7
ms.sourcegitcommit: ce363409d1206e4a3d669709863ccc9eb22b7d5f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2017
---
# Utveckla en distributionsplan
<a id="develop-a-rollout-plan" class="xliff"></a>

Din distributionsplan identifierar de målgrupper för Intune-distributionen som du vill ha i organisationen, vilka tidsramarna ska vara för distributionen för respektive grupp och vilka registreringsmetoder som du vill använda.

## Målgrupper och tidsramar
<a id="targeted-groups-and-timeframes" class="xliff"></a>

Granska först Intune-distributionens målgrupper som du identifierade i dina [användningsscenarier](planning-guide-scenarios.md).

Sedan bestämmer du tidsramen för respektive målgrupp. Den här uppgiften kräver normalt diskussioner mellan Intune-distributionsgruppen och målgrupperna, så att det kan fastställas vilken som är den bästa distributionstidsplanen för respektive grupp. Saker som bör tas upp i en sådan diskussion är:
* Gruppens förändringsvilja
* Antal användare och enheter
* Typer av enhetsplattformar
* Krav
* Geografisk plats
* Affärsrisk

## Distributionsfaser
<a id="rollout-phases" class="xliff"></a>
Organisationer väljer ofta att starta Intune-installationen med ett inledande pilottest som riktar in sig på en liten grupp användare på IT-avdelningen. Pilottestet kan utökas med ett större antal IT-användare och kan eventuellt även omfatta deltagare från andra organisationsgrupper.

### Pilot
<a id="pilot" class="xliff"></a>
Den första fasen i distributionen ska vara ämnad för pilotanvändare. Pilotanvändarna bör informeras om att de är de första användarna i en ny lösning. De måste vara villiga att ge feedback som kan bidra till att förbättra konfiguration, dokumentation och meddelanden, vilket underlättar för övriga användare i senare installationsfaser. Dessa användare får inte vara företagsledare eller VIP-användare.

Pilotdistributionen ger en bra möjlighet att testa nya [utmaningar](planning-guide-deployment-goals.md) och förfina de [krav](planning-guide-requirements.md) som du samlade in tidigare.

Utnyttja din [kommunikationsplan](planning-guide-communication-plan.md), [supportplan](planning-guide-support-plan.md) och [testning och verifiering](planning-guide-test-validation.md) så att du kan lösa eventuella problem medan effekterna för användarna fortfarande är förhållandevis begränsade.

### Produktionsdistribution
<a id="production-rollout" class="xliff"></a>
Efter en lyckad pilotdistribution är du redo att påbörja en fullständig driftssättning för resterande grupper i organisationen. Några exempel på distributionsgrupper och faser:

-   **Avdelningar** <br/>Varje avdelning kan vara en distributionsfas. Du har en hel avdelning i taget som mål. I den här typen av distribution tenderar alla användare på de olika avdelningarna att använda den mobila enheten på samma sätt och har åtkomst till samma program. Användarna har förmodligen samma typer av principer.

-   **Geografi** <br/>I den här alternativet sker distributionen till alla användare inom ett visst geografiskt område, t.ex. samma kontinent, land, region eller företagsbyggnad. Med den här typen av stegvis distribution kan du fokusera på den specifika användarplatsen. På så vis kan du använda en mer [assisterad](#user-assisted-enrollment) metod, eftersom antalet platser som distribuerar Intune samtidigt minskas. Eftersom det är möjligt att olika avdelningar eller användarfall befinner sig på samma plats kan olika användarfall distribueras samtidigt.

-   **Plattform** <br/>Den här distributionstypen innebär att distribuera liknande plattformar samtidigt. Ett exempel kan vara alla iOS-enheter den första månaden, följt av Android, följt av Windows. Den här typen av stegvis distribution förenklar supporten eftersom supportavdelningen bara behöver stödja en plattform i taget.

Följande är ett exempel på en Intune-distributionsplan som innehåller målgrupper och tidslinjer:

| **Distributionsfas** | **Juli** | **Augusti** | **September** | **Oktober** |
|:---:|:---:|:---:|:---:|:---:|
| Begränsat pilottest | IT (50 användare) |  |  |  |                                                         
| Utökat pilottest | IT (200 användare), IT-chefer (10 användare) |  |  |  |                                                         
| Produktionsdistributionsfas 1 |  | Försäljning och marknadsföring (2000 användare) |  |  |
| Produktionsdistributionsfas 2 |  |  | Återförsäljning (1000 användare) |  |
| Produktionsdistributionsfas 3 |  |  |  | Personalavdelning (50 användare), ekonomi (40 användare), chefer (30 användare) |

Du kan [ladda ned en mall för ovanstående tabell](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) och ange din organisations distributionsfaser.
## Matcha distributionsgrupper med registreringsmetoder
<a id="match-rollout-groups-to-enrollment-approaches" class="xliff"></a>

När du har fastställt målgrupper och tidsplaner för Intune-distributionen är nästa steg att välja den mest lämpliga Intune-registreringsmetoden för varje grupp. Du kan använda olika registreringsmetoder som t.ex.:
* Självbetjäning för användare
* Registrering med användarhjälp
* IT-teknikmässa

### Självbetjäning för användare
<a id="user-self-service" class="xliff"></a>

I det här fallet är det användarens ansvar att registrera sin egen enhet, vanligtvis enligt de registreringsanvisningar som IT-avdelningen tillhandahåller. Den här metoden används oftast i organisationer och är mer skalbar än registrering med användarhjälp.

### Användarstödd registrering
<a id="user-assisted-enrollment" class="xliff"></a>

Detta kallas för assisterad metod. En medlem i IT-teamet hjälper användaren genom registreringsprocessen, antingen personligen eller via Skype. Den här metoden används vanligtvis för chefer och andra grupper som kan behöva mer hjälp vid registreringen.

### IT-teknikmässa
<a id="it-tech-fair" class="xliff"></a>

Ett annat alternativ för Intune-användarregistrering är att ha en IT-teknikmässa. Vid ett sådant evenemang ställer IT-gruppen upp ett bås för hjälp med Intune-registrering, där användarna kan få information om Intune-registrering, ställa frågor och få hjälp med registreringsprocessen. Det här alternativet kan vara fördelaktigt både för IT-gruppen och användarna, särskilt under tidiga faser av Intune-distributionen.

Här följer ett uppdaterat exempel på ovanstående Intune-distributionsplan. Den omfattar följande registreringssätt:

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

## Nästa steg
<a id="next-steps" class="xliff"></a>

Nästa avsnitt innehåller råd om att [utveckla en kommunikationsplan för Intune-registreringen](planning-guide-communication-plan.md).
