---
title: Fastställa distributionsmål, delmål och utmaningar
titleSuffix: Microsoft Intune
description: Den här artikeln hjälper till att fastställa distributionsmål, delmål och utmaningar för en Microsoft Intune-implementering endast i molnet.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8cc4a109aac22617f2785a74de701e4d1d7bdf09
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67885021"
---
# <a name="determine-deployment-goals-objectives-and-challenges"></a>Fastställa distributionsmål, delmål och utmaningar

När man vill skapa en bra distributionsplan måste man börja med att identifiera organisationens distributionsmål och delmål, tillsammans med tänkbara utmaningar. Vi ska diskutera varje område mer detaljerat.

## <a name="deployment-goals"></a>Distributionsmål

Distributionsmål är långsiktiga prestationer som du vill uppnå genom att distribuera Intune i din organisation. Nedan följer några exempel på sådana mål tillsammans med beskrivningar och affärsvärde för respektive mål.

- **Integrera med Office 365 och stöd användning av mobila Office-appar**

  - **Beskrivning:** Ger nära integrering med Office 365 och användningen av Office-mobilappar med appskydd.

  - **Affärsvärde:** Säker och förbättrad användarupplevelse genom att tillåta användarna att använda appar som de känner till och föredrar.

- **Aktivera åtkomst till interna företagstjänster på mobila enheter**

  - **Beskrivning:** Gör det möjligt för de anställda att vara produktiva oavsett var de behöver arbeta och med den enhet som passar dem bäst. Det här projektet bör sträva efter att möjliggöra mobil produktivitet och åtkomst till företagsdata på ett säkert sätt.

  - **Affärsvärde:** Gör det möjligt för medarbetarna att vara rörliga och arbeta där de behöver, vilket ger företaget större möjligheter att vara konkurrenskraftiga och tillhandahålla en mer tillfredsställande arbetsmiljö.

- **Tillhandahålla dataskydd på mobila enheter**

  - **Beskrivning:** Om data lagras på en mobil enhet bör de skyddas från skadlig och oavsiktlig förlust eller delning.

  - **Affärsvärde:** Dataskydd är viktigt för att säkerställa att vi fortsätter vara konkurrenskraftiga samt att vi behandlar våra kunder och deras data med största noggrannhet.

- **Minska kostnaderna**

  - **Beskrivning:** När så är möjligt sänker projektet kostnaderna för distribution och drift.

  - **Affärsvärde:** Effektiv användning av resurser gör det möjligt för företag att investera inom andra områden, konkurrera mer effektivt och ge kunderna bättre service.

## <a name="deployment-objectives"></a>Distributionsdelmål

Distributionsdelmål är de åtgärder din organisation kan vidta för att uppnå sina distributionsmål för Intune. Nedan visas några exempel på distributionsdelmål och hur de kan uppnås.

- **Minska antalet enhetshanteringslösningar**

  - **Implementering:** Konsolidera till en enda lösning för hantering av mobilenheter: Microsoft Intune för företagsdataskydd för appar och enheter.

- **Tillhandahålla säker åtkomst till Exchange och SharePoint Online**

  - **Implementering:** Tillämpa villkorlig åtkomst för Exchange och SharePoint Online.

- **Förhindra att företagsdata lagras eller vidarebefordras till tjänster på den mobila enheten som inte tillhör företaget**

  - **Implementering:** Tillämpa Intune-appskyddsprinciper för Microsoft Office-appar och verksamhetsspecifika appar.

- **Tillhandahålla möjlighet att rensa företagsdata från enheten**

  - **Implementering:** Registrera enheter till Intune. Detta ger dig möjlighet att utföra en fjärrensning av företagets data och resurser när så är lämpligt.

## <a name="deployment-challenges"></a>Distributionsutmaningar

Distributionsutmaningar är problem som är viktigast för en organisation och som kan ha en negativ inverkan på distributionen. De är ibland relaterade till äldre problem som man har upplevt med tidigare projekt och som du kanske vill undvika, eller nya problem som är relaterade till det aktuella distributionsarbetet. Nedan visas några exempel på en Intune-distributionsutmaningar tillsammans med möjliga lösningar.

- Supportberedskap och användarupplevelse ingår inte i den inledande projektomfattningen. Detta leder till dåligt anammande hos slutanvändarna, och till stora utmaningar för supportavdelningen.

  - **Lösning:** Lägg till supportutbildning. Verifiera slutanvändarnas erfarenhet av framgångsmått i din distributionsplan.

- Brist på tydligt definierade mål och framgångsmått leder till abstrakta resultat. Det kan också medföra att din organisation hamnar i reaktivt läge när problem uppstår.

  - **Lösning:** Definiera målen och framgångsmåtten tidigt i projektomfattningen, och använd dessa datapunkter för att bygga ut de andra distributionsfaserna. Kontrollera att målen är specifika, mätbara, uppnåeliga, realistiska och görs i rätt tid. Jämför med dina mål i varje enskild fas så att du kan säkerställa att distributionsprojektet ligger i fas.

- Anta att du inte skapar, verifierar eller offensivt delar ett tydligt värdeförslag som får respons i organisationen. Detta leder ofta till begränsat införande och utebliven avkastning.

  - **Lösning:** Du vill kanske sätta igång med projektet direkt, men se först till att det finns tydligt definierade mål och delmål. Ta med dessa i alla medvetenhets- och utbildningsaktiviteter för att säkerställa att användarna förstår varför organisationen har valt Intune.

## <a name="next-steps"></a>Nästa steg

Nu när du har identifierat distributionsmål, delmål och potentiella utmaningar går vi vidare till nästa avsnitt: [Identifiera scenarier för användningsfall](planning-guide-scenarios.md).
