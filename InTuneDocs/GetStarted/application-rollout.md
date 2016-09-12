---
title: Programdistribution | Microsoft Intune
description: "Rekommendationer för en stegvis distribution av appar i Microsoft Intune."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0fc32ed3-bcf4-472a-80e7-eb20986f78fa
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 83306c0847eaf98d499e649308669a33306aa97e


---

# Programdistribution
Det här avsnittet innehåller specifika rekommendationer för en stegvis distribution av appar i Microsoft Intune. Allmän information om distributionsfaser finns i [Distributionsfaser för distribution av Microsoft Intune](rollout-phases-for-microsoft-intune-deployment.md).

### Faser i appdistribution
Faserna i appdistributionen är:

-   Projektomfattning

-   Konceptbevis

-   Pilot

-   Företagsomfattande distribution

-   Åtgärder och underhåll

## Projektomfattning
Tänk på följande:

-   Den användaruppgift som appen är avsedd att möjliggöra.

-   Appens lämplighet för användarna och deras enheter (alla som sannolikt kommer att användas).

-   Kontrollera att installationsprogrammet för den app du väljer stöds av appdistribution i Intune, enligt beskrivningen i [Lägg till appar med Microsoft Intune](/intune/deploy-use/add-apps).

-   Se till att kraven för appdistributionen har installerats. <!---, as described in [Plan for app deployment in Microsoft Intune](plan-for-app-deployment-in-microsoft-intune.md).--->

-   Kontrollera att apptypen stöds av Intune.

-   Kontrollera att du har tillräckligt med ledigt lagringsutrymme i molnet för att hämta appen. Anvisningar för att köpa ytterligare lagringsutrymme finns i [Lägg till appar med Microsoft Intune](/intune/deploy-use/add-apps).

> [!NOTE]           
> Du kan hämta den här [planeringsmallen för mobilappar](https://gallery.technet.microsoft.com/Mobile-app-planning-18689d59) som hjälper dig med distributionen.

## Konceptbevis
Under fasen Konceptbevis testar du appdistributionen i en laboratoriemiljö på enheter och användare som du har konfigurerat endast i testsyfte.

-   Låt supportavdelningen delta i denna fas för att ta reda på vilka problem som kan uppstå under pilot- och produktionsdistribution. Information om felsökning finns i [Felsöka problem med appdistributionen i Microsoft Intune](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune).

-   Under den här delen av processen bör du ta fram kommunikationsplaner för pilot- och produktionsanvändare. Planen bör minst omfatta vilken app som distribueras, hur och när användare kan hämta den, affärssyftet med distributionen och vad användarna kan göra om de stöter på problem, både information för självhjälp och hur de kontaktar supportavdelningen.

## Pilot
Under pilottestet ska du distribuera appen till en liten grupp testanvändare och enheter. Tänk på följande:

-   Se till att testgruppen är representativ för användare och enheter som kommer att använda appen efter produktionsdistributionen.

-   Utbilda supportavdelningen om appdistributionen och se till att de är beredda att hjälpa användare i testgruppen.

-   Välj testanvändare som kommer att använda appen på normalt sätt och som på ett tillförlitligt sätt kommer att rapportera problem till pilotprojektets administratörer.

-   Aktivera kommunikationsplanen för pilotanvändare.

## Företagsomfattande distribution

-   Använd pilotresultaten för att anpassa den företagsomfattande distributionen.

-   Meddela supportavdelningen om schemat för appdistributionen. Ha funktioner redo för att besvara hjälpförfrågningar och anpassa distributionen efter behov.

-   Vad beredd att felsöka distributionen om problem uppstår.

-   Aktivera kommunikationsplanen för produktionsanvändare.

-   Använd en stegvis metod för att distribuera appen, genom att lägga till några grupper i taget för att se till att distributionen fungerar smidigt.

## Åtgärder och underhåll
**Åtgärder:** Övervaka Intune-konsolen för aviseringar och problem med användare eller enheter, och för att se till att programdistributionen fungerar enligt planen.

**Support:** Se till att supportavdelningen är medveten om eventuella ändringar i apptillgänglighet som kan leda till supportärenden.

### Se även
[Distribuera appar](/intune/deploy-use/deploy-apps)

[Felsöka problem med appdistributionen i Microsoft Intune](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)



<!--HONumber=Jul16_HO4-->


