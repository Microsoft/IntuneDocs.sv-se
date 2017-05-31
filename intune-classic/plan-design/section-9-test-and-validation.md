---
title: Testning och validering av Intune | Microsoft Docs
description: "Den här artikeln hjälper dig med alla detaljer som ska övervägas vid testning och validering av Intune-molnlösningen i miljön."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: f3ba0c5a58132c9749fb8ad7e134d1323952a3de
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="intune-testing-and-validation"></a>Testning och validering av Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Testfasen bör vara under och efter implementeringsfasen, eftersom du måste testa konton, grupper och enheter för alla IT- (admin) och slutanvändarscenarier (användningsfall) som har identifierats tidigare.

Vi rekommenderar att IT-support-/supportavdelningspersonalen inkluderas i testfasen så att supportdokumentation skapas och IT-support-/supportavdelningspersonalen känner sig trygg med att tillhandahålla support för produkten. Om en komponent eller ett scenario inte fungerar baserat på användningsfallen ser du till att dokumentera de ändringar som krävs och inkludera orsaken till att en ändring har gjorts.

## <a name="before-you-begin"></a>Innan du börjar

Vi rekommenderar att du dokumenterar följande:

-   **Testkriterier:** Identifierar prestandamått att mäta mot.

-   **Utformningskomponenter:** Måste finnas i minst 1 testkriterium.

Om en utformningskomponent inte finns i minst 1 testkriterium som är anpassat till ett krav eller scenario kan du överväga om utformningskomponenten är nödvändig eller inte. Se även till att ha följande poster:

-   **Konton:** De konton som används vid testning bör vara testkonton som är licensierade för EMS och Office 365 för att testa alla användningsfall.

-   **Enheter:** De enheter som används vid den här tidpunkten ska vara testenheter som potentiellt kan rensas eller återställas till fabriksinställningarna.

-   **Integrationskomponenter:** Alla integrationskomponenter (Certificate Connector, Intune Service-to-Service Connector för värdbaserad Exchange och Intune lokal Exchange Connector) ska installeras och konfigureras vid behov.

Utformningsändringar kan behövas för att hantera oförutsedda problem. Dessutom bör alla ändringar dokumenteras fullständigt med orsaken för varje ändring. Här visas ett exempel som illustrerar vad en ändring kan vara:

-   Du kanske upptäcker att du inte uppfyller kraven för Network Device Enrollment Service (NDES) och du lär dig också att VPN- och Wi-Fi-profiler kan konfigureras med en rotcertifikatutfärdare som uppfyller samma krav utan en NDES-implementering.

Du kanske upplever utmaningar eller problem som kräver teknisk hjälp eller specialiserad felsökning under testnings- och valideringsprocessen. Vi rekommenderar att du begär hjälp via Microsofts supportkanaler.

-   [Så här får du support för Intune](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [Allmänna felsökningstips för Microsoft Intune](/intune-classic/troubleshoot/general-troubleshooting-tips-for-microsoft-intune).

-   [Lär dig hur du får support för Microsoft Intune.]/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [Kontakta telefonsupporten för Microsoft Intune](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)

## <a name="functional-validation-testing"></a>Funktionell valideringstestning

Funktionell validering består av testa varje komponent och konfiguration för att se om de fungerar korrekt. Ett exempel på valideringstestning visas i tabellen nedan.

![Avsnitt 9 tabell 1](../media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>Valideringstestning av användningsfall

Valideringstestning av användningsfall bör utföras för att verifiera att scenarierna är fullständiga och funktionella. Det finns två typer av användningsfall, IT-administratör och slutanvändare.

### <a name="it-admin"></a>IT-administratör

Valideringstestning för IT-administratörer utförs för att validera att administrativa åtgärder utförs på en enhet eller att användarfunktioner fungerar korrekt. Nedan visas ett exempel på ett valideringsscenario slutpunkt till slutpunkt för IT-administratörer.

![Avsnitt 9 tabell 2](../media/section-9-image-2-table.PNG)

### <a name="end-user"></a>Slutanvändare

Valideringstestning för slutanvändare bör utföras för att validera att slutanvändarupplevelsen är som förväntat och att den presenteras korrekt i all användarkommunikation. Det är viktigt att validera att slutanvändarupplevelsen är korrekt eftersom om detta inte valideras kan det leda till lägre införandefrekvens och fler samtal till supportavdelningen.

![Avsnitt 9 tabell 3](../media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>Nästa steg

Nu när du har testat och validerat Intunes funktionella scenarier och användningsfall är du redo för produktionsdistribution av Intune. Läs [Ytterligare resurser](additional-resources.md) om du vill ha mer information.

