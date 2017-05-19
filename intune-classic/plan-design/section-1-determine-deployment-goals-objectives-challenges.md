---
title: "Fastställa distributionsmål, delmål och utmaningar för Intune | Microsoft Docs"
description: "Den här artikeln hjälper till att fastställa distributionsmål, delmål och utmaningar för en Microsoft Intune-implementering endast i molnet."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d10906ee3fb69458738b31bb1d4252d632a9a0cf
ms.openlocfilehash: 6014527422ea3dae4d1333965ccd9e48e8216afb
ms.lasthandoff: 04/08/2017


---

# <a name="determine-intune-deployment-goals-objectives-and-challenges"></a>Fastställa distributionsmål, delmål och utmaningar för Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

När man vill skapa en bra distributionsplan måste man börja med att identifiera organisationens distributionsmål och delmål, tillsammans med tänkbara utmaningar. Varje organisation är unik och har sina egna distributionsmål, delmål och utmaningar. Vi ska diskutera varje område mer detaljerat.

## <a name="deployment-goals"></a>Distributionsmål

Distributionsmål är långsiktiga prestationer som uppnås genom att implementera Microsoft Intune i en organisation. Nedan följer några exempel på en organisations Intune-distributionsmål tillsammans med beskrivning och affärsvärde för varje.

-   **Integrera med Office 365 och stöd användning av mobila Office-appar**

    -   **Beskrivning:** Ger tät integrering med Office 365 och användning av mobila Office-program med programskydd.

    -   **Affärsvärde:** Säker och förbättrad användarupplevelse genom att tillåta att användarna använder appar de känner till och föredrar.

-   **Aktivera åtkomst till interna företagstjänster på mobila enheter**

    -   **Beskrivning:** Det är den strategiska riktningen för organisationen för att göra det möjligt för de anställda att vara produktiva oavsett var de behöver arbeta och med den enhet som passar dem bäst. Det här projektet bör sträva efter att möjliggöra mobil produktivitet och åtkomst till företagsdata på ett säkert sätt.

    -   **Affärsvärde:** Gör det möjligt för medarbetarna att vara rörliga och arbeta där de behöver, vilket ger företaget större möjligheter att vara konkurrenskraftiga och tillhandahålla en mer tillfredsställande arbetsmiljö.

-   **Tillhandahålla dataskydd på mobila enheter**

    -   **Beskrivning:** Om data lagras på en mobil enhet bör den skyddas från skadlig och oavsiktlig förlust eller delning.

    -   **Affärsvärde:** Dataskydd är viktigt för att säkerställa att vi fortsätter att vara konkurrenskraftiga och att vi behandlar våra kunder och deras data med största noggrannhet.

-   **Minska kostnaderna**

    -   **Beskrivning:** När så är möjligt sänker projektet distributions- och driftskostnaderna.

    -    **Affärsvärde:** Effektiv användning av resurser gör det möjligt för företag att investera inom andra områden, konkurrera mer effektivt och tillhandahålla bättre tjänster till kunderna.

## <a name="deployment-objectives"></a>Distributionsdelmål

Distributionsdelmål är de åtgärder en organisation kan vidta för att uppnå sina distributionsmål för Microsoft Intune. Nedan visas några exempel på en organisations distributionsdelmål och hur vart och ett kan uppnås.

-   **Minska antalet enhetshanteringslösningar**
<br>
    -   **Utförande:** Samla i en enda mobil enhetshanteringslösning, som Microsoft Intune för företagsdataskydd för appar och enheter.
<br></br>
-   **Tillhandahålla säker åtkomst till Exchange och SharePoint Online**
<br>
    -   **Utförande:** Implementera villkorlig åtkomst för Microsoft Intune för Exchange och SharePoint Online.
<br></br>
-   **Förhindra att företagsdata lagras eller vidarebefordras till tjänster på den mobila enheten som inte tillhör företaget**
<br>
    -   **Utförande:** Implementera appskyddsprinciper i Microsoft Intune för Microsoft Office- och LOB-appar.
<br></br>
-   **Tillhandahålla möjlighet att rensa företagsdata från enheten**
<br>
    -   **Utförande:** Registrera och hantera enheter med Microsoft Intune, vilket ger möjlighet att utföra en fjärrensning av företagsdata och resurser när så krävs.

## <a name="deployment-challenges"></a>Distributionsutmaningar

Distributionsutmaningar är problem som är viktigast för en organisation och som kan ha en negativ inverkan på distributionen. De är ibland relaterade till tidigare problem som man har upplevt med föregående projekt och som man vill undvika, eller nya problem som är relaterade till det aktuella distributionsarbetet. Nedan visas några exempel på en organisations distributionsutmaningar för Microsoft Intune tillsammans med möjliga lösningar.

-   Supportberedskap och användarupplevelse ingår inte i den inledande projektomfattningen.  Detta leder till begränsat slutanvändarinförande och det utmanar stödet för lösningen.
<br>
    -   **Lösning:** Införliva supportutbildning och bekräfta användarupplevelsen genom framgångsmått i distributionsplanen.
<br></br>
-   Brist på tydligt definierade mål och framgångsmått leder till abstrakta resultat, samt reaktivt läge när det uppstår problem.
<br>
    -   **Lösning:** Definiera målen och framgångsmåtten tidigt i projektomfattningen, och använd dessa datapunkter för att bygga ut de andra distributionsfaserna. Se till att målen är specifika, mätbara, uppnåeliga, realistiska och tidsenliga, och planera att mäta utifrån målen i varje fas och att säkerställa att distributionsprojektet ligger i fas.
<br></br>
-   Underlåtelse att skapa, verifiera och offensivt dela ett tydligt värdeförslag som får respons i organisationen leder ofta till begränsat införande och utebliven avkastning.
<br>
    -   **Lösning:** Du kanske vill sätta igång med projektet direkt, men se till att det finns tydligt definierade mål och delmål. Ta med dessa i alla medvetenhets- och utbildningsaktiviteter för att säkerställa att användarna förstår varför organisationen har valt Intune.

## <a name="next-steps"></a>Nästa steg

Nu när du har identifierat dina distributionsmål, delmål och potentiella utmaningar går vi vidare till nästa avsnitt: [Identifiera användningsscenarier](section-2-identify-use-case-scenarios.md).

