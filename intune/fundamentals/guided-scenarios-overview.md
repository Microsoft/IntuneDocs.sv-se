---
title: Översikt över guidade scenarier
titleSuffix: Microsoft Intune
description: Lär dig mer om de guidade Intune-scenarier som finns i Microsoft 365-enhetshanteringsportalen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ebb17324355fff9631ef74a76388ef0ab797d437
ms.sourcegitcommit: 7cc45ef52dda08479bc6bdff7d11d2f6c0e7b93b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/06/2019
ms.locfileid: "74899131"
---
# <a name="intune-guided-scenarios-overview"></a>Översikt över guidade Intune-scenarier 

Ett guidat scenario är en anpassad serie med steg som handlar om ett visst användningsfall från slutpunkt till slutpunkt. Vanliga scenarier baseras på den roll som en administratör, användare eller enhet har i din organisation. Dessa regler kräver vanligtvis en samling noggrant samordnade profiler, inställningar, program och säkerhetskontroller för att ge bästa möjliga användarupplevelse och säkerhet.    

Om du inte är bekant med alla steg och resurser som behövs för att implementera ett visst Intune-scenario kan du använda guidade scenarier som utgångspunkt. Det guidade scenariot ordnar med principer, appar, tilldelningar och andra hanteringskonfigurationer automatiskt. Dessutom kan de guidade scenarierna avsiktligt utesluta vissa alternativ som inte är tillämpliga eller som är ovanliga för det aktuella scenariot. 

Guidade scenarier utgör inte ett annat hanteringsutrymme än de vanliga arbetsflödena i Intune. De här arbetsflödena är avsedda att användas tillsammans med de befintliga arbetsflödena för profiler, appar och principer i Intune. När ett guidat scenario har slutförts måste all framtida hantering av scenariot ske i de befintliga menyerna för principer, appar och profiler. Ett guidat scenario sparar inte resurstypen ”guidat scenario”, och spårar inte framtida ändringar som görs i resurserna. Varje resurs som skapas av ett guidat scenario visas i sin respektive arbetsbelastning. Alla alternativ, även sådana som utelämnas i det guidade scenariot, blir tillgängliga för redigering i de befintliga menyerna.  

## <a name="types-of-guided-scenarios"></a>Typer av guidade scenarier 

För enkelhetens skull utelämnar alla guidade scenarier komplexa omfångsfunktioner som omfångstaggar, uteslutningsgrupper och tilldelningar av virtuella grupper. Alla resurser som skapas av ett guidat scenario ärver varje omfångstagg från den administratör som slutför scenariot. Vissa scenarier erbjuder viss anpassningsbarhet för gemensamma inställningar i syfte att täcka nära relaterade scenarier. Dessa scenarier stöder endast grupptilldelning till inkluderingsgrupper. För andra guidade scenarier garanterar hela scenariot en konsekvent upplevelse genom att inte erbjuda någon anpassning och genererar automatiskt en ny grupp för att ta emot alla tilldelningar. När det guidade scenariot har slutförts kan du använda mer avancerade tilldelningar direkt via befintliga arbetsbelastningar för principer, appar och profiler.  

Följande scenarier är guidade: 
- Distribuera Microsoft Edge för mobil 
- Prova en molnhanterad dator
- Skydda Microsoft Office för mobil 

## <a name="guided-scenario-functionality"></a>Funktioner i guidat scenario 

Guidade scenarier erbjuder specifika funktioner. Följande information hjälper till att förklara vad du kan och inte kan göra när du följer ett guidat scenario.

### <a name="launching"></a>Starta  

Alla guidade scenarier är tillgängliga från **[Enhetshanteringsportalen](https://devicemanagement.microsoft.com)**  > **Felsökning + support** > **Guidade scenarier**. 

Det guidade scenariot börjar med en introduktion som förklarar syftet med scenariot och eventuella krav som krävs för att slutföra konfigurationen. I det här läget kontrolleras dina administratörsbehörigheter för att verifiera att du har alla nödvändiga behörigheter för att slutföra scenariot.  

När alla nödvändiga kontroller har godkänts erbjuder scenariot lämpliga inställningar för anpassning. Guidade scenarier strävar efter att endast kräva inmatning för ett minimalt antal inställningar och dölja ovanliga eller avancerade inställningar tills de behövs eller baserat på särskilda omständigheter. Varje guidat scenario innehåller länkar till dokumentation med ytterligare information. 

När alla obligatoriska inställningar har angetts visar det guidade scenariot en sammanfattning av de angivna inställningarna och de resurser som krävs för scenariot. I det här läget har inget sparats såvida inget annat uttryckligen anges.

Nästa steg är att distribuera scenariot. När ett scenario distribueras skapas och sparas alla nödvändiga resurser och valda inställningar. Hur lång tid det tar att slutföra en distribution beror på scenariot. När distributionen är klar visar det guidade scenariot en lista över de skapade resurserna med länkar till hanteringsläget för varje resurs, resursens normala arbetsbelastning samt dokumentationen. 

> [!IMPORTANT]
> Den lista som visas i slutet av det guidade scenariot sparas inte och kan endast visas när det guidade scenariot är öppet.  
Om det uppstår ett fel vid distribution av scenariot ångras alla ändringar. 

### <a name="editing"></a>Redigera 

Guidade scenarier kan inte användas för redigering av befintliga resurser. När de väl har skapats måste alla resurser, grupper och tilldelningar redigeras med hjälp av befintliga arbetsbelastningar.

### <a name="monitoring"></a>Övervakning 

Guidade scenarier kan inte användas för att övervaka befintliga resurser utöver den inledande skapandeprocessen. När de väl har skapats måste alla resurser, grupper och tilldelningar övervakas med hjälp av befintliga arbetsbelastningar. 

### <a name="retiring"></a>Ta ur bruk 

Guidade scenarier kan inte användas för att ta befintliga resurser ur bruk utöver den automatiserade rensningen under ett fel vid den inledande distributionen. När de väl har skapats måste alla resurser, grupper och tilldelningar tas ur bruk med hjälp av befintliga arbetsbelastningar. 

### <a name="updating"></a>Uppdatera

Allt eftersom tekniken utvecklas kan Intune ibland uppdatera ett guidat scenario för att förbättra användarupplevelsen, säkerheten eller andra aspekter av scenariot. Den här uppdateringen påverkar endast nya distributioner som görs i det guidade scenariot. Intune uppdaterar inte befintliga resurser som tidigare genererats av det guidade scenariot för att matcha ny bästa praxis eller nya rekommendationer.  

## <a name="next-steps"></a>Nästa steg

Kom igång snabbt med Microsoft Intune genom att gå igenom de guidade Intune-scenarierna. Om Intune är nytt för dig konfigurerar du din Intune-klientorganisation genom att följa [snabbstarten för kostnadsfri utvärderingsversion](free-trial-sign-up.md).
